# Spring Autowire example

The easiest way to autowire a bean is by using the @Autowire annotation, to avoid the xml configuration. It can be used to autowire a bean on the setter method, on a constructor or a field.

Using this as a starting point
https://examples.javacodegeeks.com/enterprise-java/spring/beans-spring/spring-autowire-example/

## Auto-Wiring using applicationContext.xml

**Color.java** will be the **bean** that we will use to **autowire** in all possible ways. It is a class that represents the color of an animal. It has two attributes, the **baseColor** and **textureColoe**.

* Auto-Wiring ‘no’ : It is the **default mode** that includes no autowiring. Bean references must be defined via a **ref element**.
````xml
    <bean id="cat" class="Cat">
        <property name="name" value="cat"/>
        <property name="color" ref="color"/>
    </bean>
````
* Auto-Wiring ‘byName’ : Autowiring by **property name**. Spring looks for a bean with the same name as the property that needs to be autowired. 
````xml
    <bean id="dog" class="Dog" autowire="byName">
        <property name="name" value="dog" />
    </bean>
````
  * In this case the class Dog has a private declaration of "Color".
````java
    private Color color;
````
* Auto-Wiring ‘byType’ : Allows a property to be autowired.
```xml
    <bean id="elephant" class="Elephant" autowire="byType">
        <property name="name" value="elephant" />
    </bean>
```
  * So the same line of code, in a different class, is used to do the auto-wiring?
````java
    private Color color;
````
* Auto-Wiring ‘constructor’ : Analogous to byType, but applies to constructor arguments. 
````xml
    <bean id="frog" class="Frog" autowire="constructor">
        <property name="name" value="frog" />
    </bean>
````
  * The ctor
  ````java
    public Frog(Color color){
        this.color= color;
    }
````
## Auto-Wiring with @Autowired annotation

Had to add default ctor to Tiger class.

* Setter method
````java
    @Autowired
    public void setColor(Color color) {
        this.color = color;
    }
````
* Constructor
````java
    @Autowired
    public Tiger(Color color) {
        this.color = color;
    }
````
* Field
````java
    @Autowired
    private Color color;
````
* Dependency checking
By default, the @Autowired annotation will perform the dependency checking to make sure the property has been wired properly. But if there is no matching bean to wire, Spring will throw an exception. To avoid this exception we can disable this checking feature by setting the required attribute of @Autowired to false. In that case, if Spring does not find a matching bean, it will leave the property unset.
````java
	@Autowired(required=false)
	private Color color;
````
* @Qualifier annotation


