---
title: "A Survey of Static Methods to Prevent Temporal Memory Errors"
document: TODO
date: 2023-02-24
audience: EWG, SG23
author:
  - name: TODO
    email: TODO
toc: true
toc-depth: 4
---

\pagebreak

# Revision History

# Introduction

Memory errors are responsible for about 70% of the vulnerabilities in most software products according to Microsoft [@MSFTMEM], Google [@GOOGMEM] and Mozilla [@MOZMEM].
These memory errors include data races, use-after-free errors and buffer overruns. These errors can be categorized into spatial memory errors (like buffer overruns),
and temporal memory errors (like use-after-free errors). Spatial memory errors are often caught using bounds checked data structures. This is the approach followed by
many modern languages including Rust. Moreover, there are proposals to introduce bound checks into STL and create tools to rewrite unsafe code to use bound checked 
alternatives [@BOUNDC]. There are some approaches to combine static analysis and dynamic checks to prevent spatial error related vulnerabilities, like Checked C
[@CHECKEDC], but those are not wide spread. Using dynamic checks have negligible overhead for most workloads due to the efficiency of branch predictors in modern
architectures. On the other hand, we do not have efficient ways to catch temporal memory errors at runtime. Some methods like the address sanitizer can catch
certain temporal memory errors but they incur significant runtime overhead [@ASANOVERHEAD] that makes them impractical to deploy in production. Moreover, Android
developers did not see a major shift in the number of vulnerabilities after deploying mitigations, but they noticed a major shift after they started to deploy
memory safe languages more widely [@ANDROVULN]. Garbage collection
is another alternative to prevent this class of errors; this method cannot be deployed in low-latency applications. Rust popularized a type system that can prevent
temporal memory errors at compilation time. Is it possible to achieve something similar for C++? This paper surveys some of the existing models that aim to prevent
or mitigate temporal memory errors. The goal is to provide an objective comparison and evaluate their compatibility with the language features that exist in C++
today.


---
references:
  - id: MSFTMEM
    citation-label: MSFTMEM
    title: "Trends, Challenges, and Strategic Shifts in the Software Vulnerability Mitigation Landscape"
    author:
      - family: Miller
        given: M.
    URL: https://www.zdnet.com/article/microsoft-70-percent-of-all-security-bugs-are-memory-safety-issues
  - id: GOOGMEM
    citation-label: GOOGMEM
    title: "Chromium memory safety report"
    URL: https://www.chromium.org/Home/chromium-security/memory-safety
  - id: MOZMEM
    citation-label: MOZMEM
    title: "Implications of rewriting a browser component in Rust"
    author:
      - family: Hosfelt
        given: D.
    URL: https://hacks.mozilla.org/2019/02/rewriting-a-browser-component-in-rust/ 
  - id: BOUNDC
    citation-label: BOUNDC
    title: "C++ Buffer Hardening"
    URL: https://discourse.llvm.org/t/rfc-c-buffer-hardening/65734
  - id: CHECKEDC
    citation-label: CHECKEDC
    title: "Checked C: Making C Safe by Extension"
    author:
      - family: Elliott
        given: Archibald Samuel
      - family: et al.
    URL: https://www.microsoft.com/en-us/research/uploads/prod/2018/09/checkedc-secdev2018-preprint.pdf
  - id: ASANOVERHEAD
    citation-label: ASANOVERHEAD
    title: "Debloating Address Sanitizer"
    author:
      - family: Zhang
        given: Yuchen
      - family: et al.
    URL: https://www.usenix.org/system/files/sec22summer_zhang-yuchen.pdf
  - id: ANDROVULN
    citation-label: ANDROVULN
    title: "Memory Safe Languages in Android 13"
    author:
      - family: Stoep
        given: Jeffrey Vander
    URL: https://security.googleblog.com/2022/12/memory-safe-languages-in-android-13.html
---