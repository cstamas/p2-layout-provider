# P2 Maven Resolver

This project is a Maven plugin to allow basic resolution of artifacts from a p2 (Eclipse-style) repository.

## Use

To use this plugin, add it to the `<build>` section of your project's Pom with `<extensions>true</extensions>`. Then, add a repository with `<layout>p2</layout>` pointing at a location containing an "artifacts.jar" file and a "plugins" directory. Once that is set up, you can refer to p2-hosted artifacts with a `groupId` matching the `id` of the repository you add.

```xml
<project xmlns="http://maven.apache.org/POM/4.0.0" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
	xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 https://maven.apache.org/xsd/maven-4.0.0.xsd">
	<modelVersion>4.0.0</modelVersion>
	<groupId>com.example</groupId>
	<artifactId>p2-resolution.example</artifactId>
	<version>0.0.1-SNAPSHOT</version>

	<repositories>
		<repository>
			<id>org.eclipse.p2.repo</id>
			<url>http://download.eclipse.org/releases/2019-12/201912181000</url>
			<layout>p2</layout>
		</repository>
	</repositories>

	<dependencies>
		<dependency>
			<groupId>org.eclipse.p2.repo</groupId>
			<artifactId>ch.qos.logback.slf4j</artifactId>
			<version>1.1.2.v20160301-0943</version>
		</dependency>
	</dependencies>

	<build>
		<plugins>
			<plugin>
				<groupId>org.openntf.maven</groupId>
				<artifactId>p2-layout-resolver</artifactId>
				<version>1.0.0-SNAPSHOT</version>
				<extensions>true</extensions>
			</plugin>
		</plugins>
	</build>
</project>
```