tycho-karaf-bridge
==================

kar-packager: The kar-packager is a small Maven Plugin to create [Apache Karaf](http://karaf.apache.org/manual/latest-2.2.x/users-guide/kar.html) Archives (.kar) from a given folder. Everything the folder needs to contain are the bundles to make up the archive.

The reason this plugin was created is simple. When you come from the Eclipse-OSGi world you are familiar with [p2](http://eclipse.org/equinox/p2/). When you come form the Apache-OSGi world you are familiar with Maven. When you want to use an [Eclipse Tycho](http://eclipse.org/tycho/) build to produce a Karaf Archive without giving up the Eclipse way you are completely lost! The purpose of this plugin is to bridge the gap between the two worlds, at least for creating Karaf Archives ;).

Usage
-----
In your parent pom enable the plugin:

```xml
<build>
  <plugins>
    ...
    <plugin>
      <groupId>com.eclipsesource.tycho.karaf.bridge</groupId>
      <artifactId>kar-packager</artifactId>
      <version>0.2.0</version>
      <extensions>true</extensions>
    </plugin>
    ...
  </plugins>
</build>
```

In the module you want to create the kar archive create a pom with the packaging typ kar as followed:

```xml
...
<packaging>kar</packaging>
<build>
  <plugins>
    <plugin>
      <groupId>com.eclipsesource.tycho.karaf.bridge</groupId>
      <artifactId>kar-packager</artifactId>
      <version>0.2.0</version>
      <configuration>
        <bundlesFolder>${PATH_TO_A_FOLDER_CONTAINING_BUNDLES}</bundlesFolder>
        <karName>${NAME_OF_THE_KAR_ARCHIVE_WITHOUT_.kar}</karName>
      </configuration>
    </plugin>
  </plugins>
</build>
...
```
As you can see the plugin needs to be configured with two properties. The first is the location of the folder which contains all bundles. The second is the name of the Apache Karaf Archive without the .kar extension.

Installation
------------

Available in Maven Central.

License
-------

All code in com.eclipsesource.* packages is published under the terms of the [Eclipse Public License, version 1.0](http://www.eclipse.org/legal/epl-v10.html).
All code in com.crsn.maven.* packages is published under the terms of the GPL3 and was taken and modified from the [maven-osgi-repo Google Code Project](http://code.google.com/p/maven-osgi-repo/). 
