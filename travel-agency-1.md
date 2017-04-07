Scala and SBT

One of my responsibilities on a medium-sized Scala team was managing the builds.  Naturally, this meant learning the
wonderful world of SBT.  SBT is the "Simple Build Tool", but it's misnamed; in a way, I think SBT is the quintessential 
Scala program:
* SBT features its own DSL (Scala is, after all, the Scalable Language), which also includes infuriating operators such 
as "<++="
* There's a affinity towards elegance at the expense of basic understandability.  A good example to illustrate this is 
the design of SBT is recursive; that is, your SBT build is an SBT program that must be built before your program is 
built.  Then you may write a meta-SBT-build program to build your SBT build, and so on.  I'm very sure SBT developers 
are quite proud of this architecture, but my team members universally thought this was pointless and confusing.
* It's slow, and trying to speed it up is an engineering spike in and of itself.
* As Scala doesn't bother to maintain binary compatibility across point releases, the SBT and plugin ecosystem has to
use an older version of Scala.  So now your SBT plugin code is probably using a different compiler than your 
Scala application code.
* In exchange for the steep learning curve, you are rewarded with a powerful feature set that was definitely 
innovative: incremental, parallel, and continuous builds, a REPL, a great SBT plugin community, etc.

After Make, Maven, and now Gradle, I have mainly learned one lesson: never write a build system.