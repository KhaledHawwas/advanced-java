# Annotations 
Java annotations are a way of adding metadata to Java code to add functionality .<br>
It can be added to classes, methods, parameters, variables, constructors, and other annotations. <br>
There are built-in annotations in Java like:
* `@Override` to notify the compiler that the next method is Overrided.
* `@Deprecated` to indicate that the method has been replaced and is no longer recommended.
* `@SuppressWarnings` removes a compiler warning.<br>
It starts with `@` symbol, then the parameter list `()` (if needed). example:
``` Java      
@SuppressWarnings("unused")
Cat cat =new Cat("Stella")
```
### How to add your own annotations.

You can define your own annotations exactly like defining a new interface but add `@` symbol before interface keyword.<br>

then add [@Target](https://docs.oracle.com/javase/8/docs/api/java/lang/annotation/Target.html) and 

[@Retention](https://docs.oracle.com/javase/8/docs/api/java/lang/annotation/Retention.html) annotations to it .For example:

```Java
@Target(ElementType.FIELD)
@Retention(RetentionPolicy.RUNTIME) 
public @interface VeryImportant{

}

```
---
the `@Target` takes [ElementType](https://docs.oracle.com/javase/8/docs/api/java/lang/annotation/ElementType.html) 
list which tells what your annotation can be added to. <br>
Notice that if you want to add a list of parameters you should put them between `{}` brackets. For example:
```Java
@Target({ElementType.TYPE,ElmentType.FIELD})

```

---

The `@Retention` takes one `RetentionPolicy` parameter which describes the retention of the annotation:
* `RetentionPolicy.CLASS` the annotation will be removed after linking.
* `RetentionPolicy.RUNTIME`the annotation can be read by the VM at runtime and by Combiler.
* `RetentionPolicy.SOURCE` the annotation will not be read by combiler.

### Inside the annotation body

To add a variable to an annotation, define it like this:
```Java
@Target(ElementType.FIELD)
@Retention(RetentionPolicy.RUNTIME) 
public @interface VeryImportant{
int id();
}

```
and to put the default value
```Java
int id() default 0;
```
Only data types, enums, and strings are vaild .You can't use a user-defined type.

---
Resources:
* [Coding with John](https://www.youtube.com/watch?v=DkZr7_c9ry8)
* [Naresh i Technologies](https://www.youtube.com/watch?v=2t22AjtbyEY)
