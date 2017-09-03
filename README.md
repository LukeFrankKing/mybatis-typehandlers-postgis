# MyBatis Type Handlers for PostGIS

The MyBatis type handlers supporting geometry types introduced in PostGIS: JDBC Geometry API

## Configuration

* If you are using MyBatis alone, add the type handlers to your `mybatis-config.xml` as follow:

```xml
<typeHandlers>
  <!-- ... -->
  <typeHandler handler="com.eyougo.mybatis.postgis.type.PointTypeHandler" />
  <typeHandler handler="com.eyougo.mybatis.postgis.type.PolygonTypeHandler" />
</typeHandlers>
```
* If you are using MyBatis with **Spring**, add the type handlers package to the Spring configuration as follow:

With XML Configuration 

```xml
<bean id="sqlSessionFactory" class="org.mybatis.spring.SqlSessionFactoryBean">
    <!-- ... -->
    <property name="typeAliasesPackage" value="com.eyougo.mybatis.postgis.type" />
</bean>
```
Or with Java configuration

```java
@Bean
public SqlSessionFactory sqlSessionFactory(Configuration config) {
    SqlSessionFactoryBean factory = new SqlSessionFactoryBean();
    // ...
    factory.setTypeHandlersPackage("com.eyougo.mybatis.postgis.type");
    return factory.getObject();
}
```
* If you are using MyBatis with **Spring Boot**, add the type handlers package to the configuration file as follow: 

`application.properties`

```properties
mybatis.type-handlers-package = com.eyougo.mybatis.postgis.type
```
Or `application.yml`

```yaml
mybatis:
    type-handlers-package: com.eyougo.mybatis.postgis.type

```

## Supported types

The following type handlers are supported:

| Type handler |  PostGIS Geometry API type | JDBC types | Available version |
| ------------ | ----------------------- | ---------- | :------------------: | 
| `PointTypeHandler` | `org.postgis.Point` | `OTHER` |  1.0-SNAPSHOT |
| `PolygonTypeHandler` | `org.postgis.Polygon` | `OTHER` |  1.0-SNAPSHOT |


> **Note:**
> For more details of type handler, please refer to "[MyBatis 3 REFERENCE DOCUMENTATION](http://www.mybatis.org/mybatis-3/configuration.html#typeHandlers)".