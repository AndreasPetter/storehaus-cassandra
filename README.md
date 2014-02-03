storehaus-cassandra
===================

A storehaus-wrapper for hector/Cassandra.
This was my first Scala project so it probably can be done 
a lot more "the functional way"

Changes required to the original storehaus branch
-------------------------------------------------

Steps to build:
- Clone http://github.com/twitter/storehaus
- Copy this stuff into the folder as a subproject "storehaus-cassandra"
- Change Build.scala and add somewhere (e.g. on line 223):
  lazy val storehausCassandra= module("cassandra").settings(
    libraryDependencies ++= Seq(
      "com.twitter" %% "algebird-core" % algebirdVersion,
      "com.twitter" %% "bijection-core" % bijectionVersion,
      "org.hectorclient" % "hector-core" % "1.1-4"
    ),
    parallelExecution in Test := false
  ).dependsOn(storehausAlgebra % "test->test;compile->compile")
- Add "storehausCassandra" to the list of submodules (e.g. on line 141)

Optional - for Scala-IDE support:
- Change /project/plugins.sbt and add:
addSbtPlugin("com.typesafe.sbteclipse" % "sbteclipse-plugin" % "2.4.0")

