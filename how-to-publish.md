## Summary
1. Install gpg
2. Edit the plugins.sbt file
3. Get next version identifier

## From Jonathan's Notes
### install gpg 
~/.sbt/sonatype.sbt
import com.typesafe.sbt.pgp._

pgpPassphrase := Some("".toArray)

credentials += Credentials("Sonatype Nexus Repository Manager", 
                           "oss.sonatype.org", 
                           "jenkinss142",
                           "xxxx")

### edit the plugins sbt file
~/.sbt/plugins/build.sbt
```
resolvers += Resolver.url("scalasbt", new URL("http://scalasbt.artifactoryonline.com/scalasbt/sbt-plugin-releases")) (Resolver.ivyStylePatterns)

addSbtPlugin("com.typesafe.sbt" % "sbt-pgp" % "0.8")
```
----
sbt passphrase

pgp-cmd key-gen

// don't use passphrase

// may have to publish your key ???

### get next version identifier 
From: http://central.maven.org/maven2/edu/berkeley/cs/chisel_2.10/
```
cd ~/bar/chisel
edit ~/bar/chisel/project/build.scala and put in version number
sbt publish-signed
```
--
### Enable distribution on sonatype.org
go to https://oss.sonatype.org/
```
login with jenkins142 account (from .sbt/....)
click on staging repositories
hit refresh
select corresponding chisel jar file
hit close
hit refresh 
wait for release button to appear
hit release
```
---
incorporate git has
tag git repo with version number