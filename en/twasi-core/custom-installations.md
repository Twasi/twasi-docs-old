# Custom installations
In order to test your plugins before you submit them, or if you want to
run your own instance, you can install Twasi-Core in any of your environments.

## Installing MongoDB
Twasi needs connection to a MongoDB server. Please refer to the MongoDB docs
to find out how to install a MongoDB server on your target machine: https://docs.mongodb.com/manual/installation/

Please note that if you only use your application for local testing, you do
not have to configure any of MongoDB's security features. Per default, the server will
be bound to localhost which means that only the machine itself is allowed
to access.

## Installing Java
As Twasi-Core is a Java application, you should install an applicable version of
Java. Twasi-Core was developed and tested using Java 8 (JDK 1.8). However, it
should also work on newer versions. https://www.java.com/en/download/help/download_options.xml

## Installing other dependencies
You also need the following Dependencies installed:
- Maven (https://maven.apache.org/install.html)
- Git (https://git-scm.com/book/en/v2/Getting-Started-Installing-Git)

## Cloning the repository, obtaining the source code
Currently, there is no .jar file provided. That means that you have to build
one yourself.

Start of by cloning Twasi-Core to your machine:
`git clone https://github.com/Twasi/twasi-core`

Change dir to the freshly cloned directory:
`cd twasi-core`

Build the Jar file using maven:
`mvn clean compile assembly:single`

After that, the file `target/TwasiCore-{Version}-jar-with-dependencies.jar` should be created.

Copy that file to where you want to install Twasi and execute
`java -jar TwasiCore-{Version}-jar-with-dependencies.jar` to run the file.
