---
layout: page
---


# Maven Repository

Maven repository top level directory is [here](maven-repo/).

To use software from this repository in your Maven projects, add the following
configuration to the appropriate section in either your project's `pom.xml`
file or your Maven global `settings.xml` file.


    <repositories>
        <repository>
            <id>inesc-id-esw-repository</id>
            <url>http://inesc-id-esw.github.com/maven-repo/</url>
        </repository>
    </repositories>



# Available Downloads

## Atomic Annotation

Put this in your maven project to use the Atomic Annotation library:

    <dependencies>
        <dependency>
            <groupId>pt.ist.esw</groupId>
            <artifactId>atomic-annotation</artifactId>
            <version>1.0</version>
        </dependency>
    </dependencies>
    
Alternative you can browse the files in the repository and directly download
the latest JAR file available.

To effectively use this library, your compiled code that makes use of the
@Atomic annotation needs to be post-processed using the
`pt.ist.esw.atomicannotation.ProcessAtomicAnnotations` program.  It takes as
parameter a directory containing class files to process.  In Maven just add
the following, or equivalent, to the `<plugins>` section in your POM:

    <!-- ProcessAtomicAnnotations immediatly after compiling -->
    <plugin>
        <groupId>org.codehaus.mojo</groupId>
        <artifactId>exec-maven-plugin</artifactId>
        <version>1.2.1</version>
        <executions>
            <execution>
                <phase>process-classes</phase>
                <goals>
                    <goal>java</goal>
                </goals>
            </execution>
        </executions>
        <configuration>
            <mainClass>pt.ist.esw.atomicannotation.ProcessAtomicAnnotations</mainClass>
            <arguments>
                <argument>${project.build.outputDirectory}</argument>
            </arguments>
        </configuration>
    </plugin>



# Contact

You can contact us via email at: esw_AT_inesc-id_DOT_ist_DOT_utl_DOT_pt.

