# Compiler Projects – Summer of Code

We have a number of compiler projects available for interested participants. Please contact one of the mentors for
additional details and let us know what specifically interests you about this area of contribution. Together, we can tailor your project to best suit you. We are flexible and open to new ideas besides the ones listed below, but these should give a good overview of the kinds of ongoing projects in this area.

- **Escape analysis:**

  A classic problem in compiler analysis! We have recently introduced an [inter-procedural escape analysis pass](https://github.com/JuliaLang/julia/pull/42465). However, this pass is very new and there are still many possibilities for a project in this area --- some examples include improving the analysis itself, or working on optimization passes that utilize the newfound escape information. The schedule for the project would be as follows: first, you would start by writing some example programs that would benefit from escape information. Perhaps you've found an area where the current optimizations aren't doing all that they could, or you have an idea for a new optimization that utilizes knowledge of escapes. Next, you would identify what specific information is needed to required to optimize your program, and together we'll improve the existing framework to accurately compute that information. Finally, you'll get to the easy part: actually coding and putting those plans into practice. Along
  the way, you'll be mentored in submitting many smaller PRs to fix issues and make improvements you notice along the
  journey.

- **Optimization passes:**

  Another classic compiler challenge! We have some basic optimization passes (inlining, basic DCE,
  SROA), but currently many other interesting passes simply don't yet exist, or have a partial PR,
  but need significant effort to finish. There is of course overlap with the escape analysis project, but not that there are many areas for improvement completely outside of escape-related optimizations. For this proposal, we can work together to define which
  optimization to tackle next, and figure out if there is existing work to base our approach on.
  
- **Compiler plug-in project:**

- **Investigating OrcJIT v2 improvements:**

  The LLVM JIT has gained many new features. This project would involve finding out what they are
  and making use of them. Some examples include better resource tracking, parallel compilation, a
  new linker (which may need upstream work too), and fine-grained tracking of relocations.

- **Parser error messages (and other parts):**

  Error messages and infrastructure could use some work to track source locations more precisely.
  This may be a large project. Contact me and @c42f for more details if this interests you.

- **Macro hygiene re-implementation, to eliminate incorrect predictions inherent in current approach:**

  This may be a good project for someone that wants to learn lisp/scheme! Our current algorithm runs
  in multiple passes, which means sometimes we compute the wrong scope for a variable in the earlier
  pass than when we assign the actual scope to each value. See
  <https://github.com/JuliaLang/julia/labels/macros>, and particularly issues such as
  <https://github.com/JuliaLang/julia/issues/20241> and
  <https://github.com/JuliaLang/julia/issues/34164>.

- **Better debug information output for variables:**

  We have part of the infrastructure in place for representing DWARF information for our variables,
  but only from limited places. We could do much better since there are numerous opportunities for
  improvement!


**Recommended Skills**: Most of these projects involve algorithms work, requiring
a willingness and interest in seeing how to integrate with a large system.

**Mentors**: [Jameson Nash](https://github.com/vtjnash), [Ian Atol](https://github.com/ianatol)

## Improving test coverage

Code coverage reports very good coverage of all of the Julia Stdlib packages, but it's not complete.
Additionally, the coverage tools themselves (--track-coverage and
<https://github.com/JuliaCI/Coverage.jl>) could be further enhanced, such as to give better accuracy
of statement coverage, or more precision. A successful project may combine a bit of both building
code and finding faults in others' code.

Another related side-project might be to explore adding Type information to the coverage reports?

**Recommended Skills**: An eye for detail, a thrill for filing code issues, and the skill of breaking things.

**Contact:** [Jameson Nash](https://github.com/vtjnash)

## Multi-threading Improvement Projects

A few ideas to get you started, in brief:

- Make better use of threads for GC (and particularly, make the page-allocator multi-threaded)

- Improve granularity of codegen JIT for multi-threading

- Improve granularity of IO operations for multi-threading (and set up a worker thread for running
  the main libuv event loop)

- Measure and optimize the performance of the `partr` algorithm, and add the ability to dynamically
  scale it by workload size

- Automatic insertion of GC safe-points/regions, particularly around loops

- Work towards supporting a dynamic number of threads

Join the regularly scheduled multithreading call for discussion of any of these at [#multithreading
BoF calendar invite][threadcall] on the Julia Language Public Events calendar.

[threadcall]: https://calendar.google.com/event?action=TEMPLATE&tmeid=MzQ1MnZxMGNucGt2NGQwYW1zZjA4MzM5dGtfMjAyMTAyMTdUMTYzMDAwWiBqdWxpYWxhbmcub3JnX2tvbWF1YXFldDE0ZW9nOW9pdjNwNm83cG1nQGc&tmsrc=julialang.org_komauaqet14eog9oiv3p6o7pmg%40group.calendar.google.com&scp=ALL

**Recommended Skills**: Varies by project

**Contact:** [Jameson Nash](https://github.com/vtjnash)


## Automated performance measurements

The Nanosoldier.jl project (and related <https://github.com/JuliaCI/BaseBenchmarks.jl>) tests for
performance impacts of some changes. However, there remains many areas that are not covered (such as
compile time) while other areas are over-covered (greatly increasing the duration of the test for no
benefit) and some tests may not be configured appropriately for statistical power. Furthermore, the
current reports are very primitive and can only do a basic pair-wise comparison, while graphs and
other interactive tooling would be more valuable. Thus, there would be many great projects for a
summer participant to tackle here!

**Contact:** [Jameson Nash](https://github.com/vtjnash), [Tim Besard](https://github.com/maleadt)
