# Avro compiler for avro4k

This is a generator for avro4k compatible kotlin source files. The generator is based on 
the avro java compiler.

Unsupported features:
- Protocol generation
- Union types other than a Union with null

Additional features:
- Kotlin data classes may have a different name than avro records.

## Maven plugin usage:
```xml
<build>
    <plugins>
        <plugin>
            <groupId>com.github.thake.avro4k</groupId>
            <artifactId>avro4k-maven-plugin</artifactId>
            <version>0.0.1</version>
            <configuration>
                <sourceDirectory>${avro.schema.directory}</sourceDirectory>
                <outputDirectory>${project.build.directory}/generated-sources</outputDirectory>
                <renamedClasses>
                    <renamedClass>
                        <regex>my.namespace.(\w+)Record</regex>
                        <replacement>other.namespace.$1</replacement>
                    </renamedClass>
                </renamedClasses>
            </configuration>            				        
        </plugin>
        ...
    </plugins>
</build>
```