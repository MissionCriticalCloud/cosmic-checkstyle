# Checkstyle

The checkstyle repository is a placeholder for our code conventions.

# Using the Checkstyle project

The project artifacts can be easily installed. In order to do so, please add the following Plugin Repository Dependency to your pom.xml file.

```
  <pluginRepositories>
    <pluginRepository>
      <id>check-style-maven-repo</id>
      <name>MCC Maven Repo</name>
      <url>https://github.com/MissionCriticalCloud/maven-repo/raw/checkstyle/</url>
      <releases>
        <enabled>true</enabled>
        <updatePolicy>always</updatePolicy>
      </releases>
      <snapshots>
        <enabled>true</enabled>
        <updatePolicy>always</updatePolicy>
      </snapshots>
    </pluginRepository>
  </pluginRepositories>
```

Now that the dependency was added, we have to add the Maven Checkstyle Plugin. Please, add the xml snippet below to your pom.cml.

```
      <plugin>
        <groupId>org.apache.maven.plugins</groupId>
        <artifactId>maven-checkstyle-plugin</artifactId>
        <version>2.17</version>
        <dependencies>
          <dependency>
            <groupId>com.puppycrawl.tools</groupId>
            <artifactId>checkstyle</artifactId>
            <version>6.11.2</version>
          </dependency>
          <dependency>
            <groupId>mcc.checkstyle</groupId>
            <artifactId>checkstyle</artifactId>
            <version>1.0-SNAPSHOT</version>
          </dependency>
        </dependencies>
        <executions>
          <execution>
            <id>checkstyle</id>
            <phase>compile</phase>
            <configuration>
              <configLocation>google-checkstyle/checkstyle.xml</configLocation>
              <headerLocation>LICENSE</headerLocation>
              <encoding>UTF-8</encoding>
              <consoleOutput>true</consoleOutput>
              <failsOnError>true</failsOnError>
            </configuration>
            <goals>
              <goal>checkstyle</goal>
            </goals>
          </execution>
        </executions>
      </plugin>
```

# Importing Eclipse specific settings

The Checkstyle project also contains Eclipse specific configuration files for Fromatter, Clean-up and Organise Import actions. The xml files can be found under the following directory:

* checkstyle/configuration/eclipse/formatter.xml
* checkstyle/configuration/eclipse/cleanup.xml
* checkstyle/configuration/eclipse/imports.xml

Those files can be imported into Eclipse preferences settings.

# Integrating Maven Checkstyle with Eclipse Checkstyle

The latest M2E-Code-Quality Plugin is not working properly with Eclipse Mars.1. In order to get the integrtion done, we have to use the plugin availbale in this project.

The Jar file is available under ```checkstyle/lib/com.basistech.m2e.code.quality.checkstyle-1.0.0-SNAPSHOT.jar```. In order to get the plugin installed, please copy the file under the plugins folder of your Eclipse installation. 

We will apply the fix to the M2E Code Quality Plugin and make it availbale via the Eclipse Market Place.

# Prerequisites

* Eclipse Mars.1
* Eclipse Checkstyle Plugin
* Eclipse M2E-Code-Quality Plugin
