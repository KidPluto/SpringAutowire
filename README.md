=== Spring Autowire example ===

https://examples.javacodegeeks.com/enterprise-java/spring/beans-spring/spring-autowire-example/

* Auto-Wiring ‘no’ : It is the **default mode** that includes no autowiring. Bean references must be defined via a ref element. Changing the default setting is not recommended for larger deployments, because specifying collaborators explicitly gives greater control and clarity. To some extent, it documents the structure of a system.
* Auto-Wiring ‘byName’ : Autowiring by **property name**. Spring looks for a bean with the same name as the property that needs to be autowired. For example, if a bean definition is set to autowire by name, and it contains a master property (that is, it has a setMaster(..) method), Spring looks for a bean definition named master, and uses it to set the property.
* Auto-Wiring ‘byType’ : Allows a property to be autowired if exactly **one bean of the property type exists in the container**. If more than one exists, a fatal exception is thrown, which indicates that you may not use byType autowiring for that bean. If there are no matching beans, nothing happens; the property is not set.
* Auto-Wiring ‘constructor’ : Analogous to byType, but applies to constructor arguments. If there is not exactly one bean of the constructor argument type in the container, a fatal error is raised.

**Color.java** will be the **bean** that we will use to **autowire** in all possible ways. It is a class that represents the color of an animal. It has two attributes, the **baseColor** that is the base color of an animal’s skin and the **textureColor** that is the texture color of an animal’s skin.

