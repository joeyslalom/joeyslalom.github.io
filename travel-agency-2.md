AWS Pipeline
* You might think this stuff would work together easily.  Maybe it's a skill / knowledge barrier, but this difference
is ridiculous
* aws is not easy to use, its interface is quite bad
* first omen: copy and paste example hello world program doesn't work
  * You must implement an interface that isn't mentioned!
* create lambda user. pip install and configure aws cli tool.
* get thing to build. turns out, must chmod? then countless iterations of broken yaml. then changing build image. then changing output target.

Java vs NodeJS

* Decision to use JavaScript does not appear to be made on a technical / objective basis, so it's hard for me to
make an effective argument.  Seems to me the argument is more about potential opportunity?
* This is why I want to understand what are the constraints that are important to you and what things you are 
concerned about.  We've all been in the game long enough to realize engineering is all about trade-offs.
* So when I hear my architects are willing to change their tech stack in a week, personally I don't see that as
being against Java or honestly even loving JavaScript, but it signals to me there's still a bit of flexibility in
how things are built.  Which is good!  Don't leave stuff off the table.
* Let me say my biases clearly so you can understand them.  I have been pretty successful in building for maintainability
  * This is why I prefer Java, in nearly any metric that's important to you, (TIOBE, StackOverflow, GitHub, Monster)
  Java, Java articles, resources, frameworks and libraries have excellent representation.
  * I will avoid hacks or bad solutions.  Even if the correct way takes longer, it is worth it.
* But instead of switching tech stacks - which I want to be very clear - will have impacts on velocity and quality -
consider other solution frameworks, or even cloud provider.
* As an example, the team thinks Lambda is magical fairy dust.  Here's my opinion:
  * Lambda does have advantages, mainly in that there's a free tier
  * On the flip side, there's no price ceiling.  So for consistent high demand it's not a good trade-off.
  * Also, as they are provisioned on demand, must be careful about latency, rejected requests
  * They also force a certain programming model, namely they are stateless.
* So immediately Lambda's aren't a fit for the Wild Stallion solution.
  * If you want to force it, we can use something like AWS Dynamo DB.  But if things like vendor lock-in were important to you,
  I would say you're a hard lock to AWS.
* Maybe the Scorpio solution can be, but I have concerns:
  * Because there are integrations, now you are paying the setup/teardown cost per request (remember your SLA)
  * This will also increase the running time and memory size of the lambda which results in higher lambda cost
  

AWS Lambda, API Gateway
* These things have some awareness of each other, but naturally this makes things quite confusing
* For instance, the Lambda "test event" is json.  This will go to your method as you may expect
* However, the API Gateway "request body" is also json, but this will become an element named "body" in a large object
* Also, even though these input and output objects are basic java objects, you may NOT use AutoValue for them, AWS freaks out

Spring Booty

* In stark comparison to the dumpster fire that is AWS Lambda and API Gateway (which, in the their defense, I don't know
and don't particularly care about) day one of building an app server, I got Spring Boot and added swagger support.
Ryan setup Jenkins on EC2 and connecting that through github was done.
* Day 2, I added docker integration.  BOOOM!