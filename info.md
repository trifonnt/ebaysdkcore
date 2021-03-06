# Info
   - https://mvnrepository.com/artifact/com.ebay/ebaysdkcore/939

 - https://github.com/tonicsoft/ebaysdkcore
   - https://mvnrepository.com/artifact/org.tonicsoft.ebay/ebaysdkcore/981.0.0

 - https://github.com/linus87/ebaysdk
   - https://mvnrepository.com/artifact/io.github.linus87/ebaysdk/1065

 - https://github.com/lespaul361/eBaySDK939
 - https://github.com/lespaul361/eBaySDK1027


# Steps when new version of eBay SDK is released
+01) Get last version
```shell
$ cd ebay-origin
$ wget https://developer.ebay.com/devzone/codebase/javasdk-jaxb/ebaysdkjava1131.zip -- TODO
$ unzip ./ebaysdkjava1131.zip --TODO

-$ wget https://developer.ebay.com/devzone/codebase/javasdk-jaxb/ebaysdkjava1113.zip
-$ unzip ./ebaysdkjava1113.zip
```


+02) Copy source files
```shell
$ cd 01_jhipster/ebaysdkcore
$ rm -rf ./src/main/java
$ mkdir -p ./src/main/java


$ cd 01_jhipster/ebaysdkcore/ebay-origin

$ cp -r ./source/core/src/com ../src/main/java
$ rm -rf ../src/main/java/src/com/ebay/soap

$ cp -r ./source/apiCalls/src/com ../src/main/java
-$ cp -r ./source/attributesLib/src/com ../src/main/java
$ cp -r ./source/helper/src/com ../src/main/java
$ cp ./source/wsdl/ebaySvc.wsdl ../src/main/resources/com/ebay/sdk/
-$ cp ./build/custom-binding.xml ../
-$ cp ./build/jaxb-binding.xjb ../
```


+03) Ensure Maven has enough memory to run the SDK build
```shell
$ set MAVEN_OPTS=-Xmx512m
```

+04) Execute Maven command
```shell
$ ./mvnw -e clean package
```
If the build is successful, the jar file will be built to 'target' folder.


-05) Release to Central Maven Repository
???


Notes:
1. The Maven build will call wsimport ant task to generate proxy from eBay wsdl,
for details, please refer to pom.xml file.
2. The build was tested with following configuration-
- Java 1.8.0_171
- Maven 3.6.0
- Linux (Ubuntu)


### Publish new version to JitPack

 - Create new Release in GitHub

 - Open below URL in order to start JitPack build process

```shell
https://jitpack.io/com/github/trifonnt/ebaysdkcore/1113.0.3
```

### Get this project into your Maven build(pom.xml)
```xml
	...
	<repositories>
		<repository>
		    <id>jitpack.io</id>
		    <url>https://jitpack.io</url>
		</repository>
	</repositories>
 	...
 	...
 	<dependency>
	    <groupId>com.github.trifonnt</groupId>
	    <artifactId>ebaysdkcore</artifactId>
	    <version>1113.0.3</version>
	</dependency>
	...
```
