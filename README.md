# What
This is an example that shows you how to corporate you ant build within maven.

Assume you have an old legacy code that purely use ant, and now you need put it into maven to leverage the functionality of maven and/or other build system.

# How
Put all your legacy ant build into the `ant-project` module. 
1. Edit the `build.xml` to meet your needs
2. Put all your source code into `ant-build` folder
3. If your ant outputs several apps/jars, you might want to output/copy java classes into different maven modules, e.g. proj1, proj2 and etc.
4. Hock up the ant-run in `pom.xml`

When maven build, 
1. It uses ant that works on the `ant-project`, to generate java .class files, then it directly or copys to the individual maven module (proj1, proj2 and etc).
2. For individual modules, it would pickup the java classes from the ant build and follows the maven way.
   
For you configuration/properties files, it is recommended to put them into maven module's configure location, e.g. `proj1/src/main/resources`

You can use following command to build, package your app(s) in maven
```
mvn compile
mvn package
```
   
