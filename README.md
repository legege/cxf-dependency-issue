# cxf-dependency-issue

## Maven

* Command to run: `mvn dependency:tree`

Output:

```
[INFO] --- maven-dependency-plugin:2.8:tree (default-cli) @ cxf-dependency-issue ---
[INFO] com.legege.test:cxf-dependency-issue:jar:1.0.0
[INFO] \- org.apache.cxf:cxf-rt-frontend-jaxws:jar:3.3.6:compile
[INFO]    +- xml-resolver:xml-resolver:jar:1.2:compile
[INFO]    +- org.ow2.asm:asm:jar:7.1:compile
[INFO]    +- org.apache.cxf:cxf-core:jar:3.3.6:compile
[INFO]    |  +- org.glassfish.jaxb:jaxb-runtime:jar:2.3.2:compile
[INFO]    |  |  +- org.glassfish.jaxb:txw2:jar:2.3.2:compile
[INFO]    |  |  +- com.sun.istack:istack-commons-runtime:jar:3.0.8:compile
[INFO]    |  |  +- com.sun.xml.fastinfoset:FastInfoset:jar:1.2.16:compile
[INFO]    |  |  \- jakarta.activation:jakarta.activation-api:jar:1.2.1:compile
[INFO]    |  +- com.fasterxml.woodstox:woodstox-core:jar:5.0.3:compile
[INFO]    |  |  \- org.codehaus.woodstox:stax2-api:jar:3.1.4:compile
[INFO]    |  +- org.apache.ws.xmlschema:xmlschema-core:jar:2.2.5:compile
[INFO]    |  \- jakarta.xml.bind:jakarta.xml.bind-api:jar:2.3.2:compile
[INFO]    +- org.apache.cxf:cxf-rt-bindings-soap:jar:3.3.6:compile
[INFO]    |  +- org.apache.cxf:cxf-rt-wsdl:jar:3.3.6:compile
[INFO]    |  |  \- wsdl4j:wsdl4j:jar:1.6.3:compile
[INFO]    |  \- org.apache.cxf:cxf-rt-databinding-jaxb:jar:3.3.6:compile
[INFO]    +- org.apache.cxf:cxf-rt-bindings-xml:jar:3.3.6:compile
[INFO]    +- org.apache.cxf:cxf-rt-frontend-simple:jar:3.3.6:compile
[INFO]    +- org.apache.cxf:cxf-rt-ws-addr:jar:3.3.6:compile
[INFO]    |  \- org.apache.cxf:cxf-rt-ws-policy:jar:3.3.6:compile
[INFO]    |     \- org.apache.neethi:neethi:jar:3.1.1:compile
[INFO]    +- javax.annotation:javax.annotation-api:jar:1.3.2:compile
[INFO]    +- javax.xml.ws:jaxws-api:jar:2.3.1:compile
[INFO]    |  \- javax.xml.soap:javax.xml.soap-api:jar:1.4.0:compile
[INFO]    +- com.sun.activation:javax.activation:jar:1.2.0:compile
[INFO]    +- org.apache.geronimo.specs:geronimo-ws-metadata_2.0_spec:jar:1.1.3:compile
[INFO]    +- com.sun.xml.messaging.saaj:saaj-impl:jar:1.4.0-b03:compile
[INFO]    |  +- org.jvnet.mimepull:mimepull:jar:1.9.7:compile
[INFO]    |  \- org.jvnet.staxex:stax-ex:jar:1.7.8:compile
[INFO]    |     \- javax.activation:activation:jar:1.1:compile
[INFO]    +- org.jacorb:jacorb-omgapi:jar:3.9:compile
[INFO]    +- org.apache.geronimo.specs:geronimo-jta_1.1_spec:jar:1.1.1:compile
[INFO]    \- org.jboss.spec.javax.rmi:jboss-rmi-api_1.0_spec:jar:1.0.6.Final:compile
```

We find here the library `com.sun.activation:javax.activation` coming directly from `org.apache.cxf:cxf-rt-frontend-jaxws` dependency.

## Gradle

* Command to run: `mvn dependency:tree`

Output:

```
compileClasspath - Compile classpath for source set 'main'.
\--- org.apache.cxf:cxf-rt-frontend-jaxws:3.3.6
     +--- xml-resolver:xml-resolver:1.2
     +--- org.ow2.asm:asm:7.1
     +--- org.apache.cxf:cxf-core:3.3.6
     |    +--- org.glassfish.jaxb:jaxb-runtime:2.3.2
     |    |    +--- jakarta.xml.bind:jakarta.xml.bind-api:2.3.2
     |    |    |    \--- jakarta.activation:jakarta.activation-api:1.2.1
     |    |    +--- org.glassfish.jaxb:txw2:2.3.2
     |    |    +--- com.sun.istack:istack-commons-runtime:3.0.8
     |    |    |    \--- jakarta.activation:jakarta.activation-api:1.2.1
     |    |    +--- org.jvnet.staxex:stax-ex:1.8.1
     |    |    |    +--- jakarta.activation:jakarta.activation-api:1.2.1
     |    |    |    \--- jakarta.xml.bind:jakarta.xml.bind-api:2.3.2 (*)
     |    |    +--- com.sun.xml.fastinfoset:FastInfoset:1.2.16
     |    |    \--- jakarta.activation:jakarta.activation-api:1.2.1
     |    +--- com.fasterxml.woodstox:woodstox-core:5.0.3
     |    |    \--- org.codehaus.woodstox:stax2-api:3.1.4
     |    +--- org.apache.ws.xmlschema:xmlschema-core:2.2.5
     |    \--- jakarta.xml.bind:jakarta.xml.bind-api:2.3.2 (*)
     +--- org.apache.cxf:cxf-rt-bindings-soap:3.3.6
     |    +--- org.apache.cxf:cxf-core:3.3.6 (*)
     |    +--- org.apache.cxf:cxf-rt-wsdl:3.3.6
     |    |    +--- org.apache.cxf:cxf-core:3.3.6 (*)
     |    |    +--- wsdl4j:wsdl4j:1.6.3
     |    |    \--- org.ow2.asm:asm:7.1
     |    \--- org.apache.cxf:cxf-rt-databinding-jaxb:3.3.6
     |         +--- org.apache.cxf:cxf-core:3.3.6 (*)
     |         \--- org.apache.cxf:cxf-rt-wsdl:3.3.6 (*)
     +--- org.apache.cxf:cxf-rt-bindings-xml:3.3.6
     |    \--- org.apache.cxf:cxf-core:3.3.6 (*)
     +--- org.apache.cxf:cxf-rt-frontend-simple:3.3.6
     |    +--- org.apache.cxf:cxf-core:3.3.6 (*)
     |    +--- org.apache.cxf:cxf-rt-bindings-soap:3.3.6 (*)
     |    \--- org.apache.cxf:cxf-rt-wsdl:3.3.6 (*)
     \--- org.apache.cxf:cxf-rt-ws-addr:3.3.6
          +--- org.apache.cxf:cxf-core:3.3.6 (*)
          +--- org.apache.cxf:cxf-rt-bindings-soap:3.3.6 (*)
          \--- org.apache.cxf:cxf-rt-ws-policy:3.3.6
               +--- wsdl4j:wsdl4j:1.6.3
               +--- org.apache.cxf:cxf-core:3.3.6 (*)
               \--- org.apache.neethi:neethi:3.1.1
```

The library `com.sun.activation:javax.activation` cannot be found.
