# Maven Import Java Libraries (Jars)

With this course, come two Java libraries (`tegels.jar`, `verkiezingen.jar`). They are NOT available 
through a Maven repository. So they need to be imported manually to the local Maven repository.

The Maven configuration file `pom.xml`, in this directory, is set up for installing these jars,
in the local Maven repository.

Use the following Maven commands to do so.

__WARNING:__ Run them separate, not both profiles combined.

	mvn  -P install-tegels  initialize  
	mvn  -P install-verkiezingen  initialize  


## Background

Normally almost all Java dependencies, will come from some central Maven repository, or some organisation
specific ones. So importing Maven libraries manually, is extreme rare! In cases where the jars are not available
through one of the external repositories, they can be installed manually. Below follow some details, how to do so.

[Maven - Guide to installing 3rd party JARs](https://maven.apache.org/guides/mini/guide-3rd-party-jars-local.html)

	mvn  install:install-file
	-Dfile=<path-to-file>
	-DgroupId=<group-id>
	-DartifactId=<artifact-id>
	-Dversion=<version>
	-Dpackaging=<packaging>
	-DgeneratePom=true
	
	Where: <path-to-file>  the path to the file to load
	   <group-id>      the group that the file should be registered under
	   <artifact-id>   the artifact name for the file
	   <version>       the version of the file
	   <packaging>     the packaging of the file e.g. jar

	mvn  install:install-file  -Dfile=lib/tegels.jar  -DgroupId=nl.ou.oo-java  -DartifactId=tegels  -Dversion=1.0.0  -Dpackaging=jar  -DgeneratePom=true

	mvn  install:install-file  -Dfile=lib/tegels.jar  -DgroupId=nl.ou.oo-java  -DartifactId=verkiezingen  -Dversion=1.0.0  -Dpackaging=jar  -DgeneratePom=true
