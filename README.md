
# `object`

## About `object`

* We know that objects are instantiated from classes
* We can also create an `object`, a single `object`, without a class
* This is called an `object`
* **IMPORTANT** An object is a singleton. There is only one
* It is how we avoid static methods

## **Lab:** Trying out the object

**Step 1:** Here we will create a single object


```scala
object MyObject
```


    Intitializing Scala interpreter ...



    Spark Web UI available at http://fb98a64ea0b9:4043
    SparkContext available as 'sc' (version = 2.4.3, master = local[*], app id = local-1562361769053)
    SparkSession available as 'spark'
    





    defined object MyObject
    



**Step 2:** Verify that it is truly a singleton, by assigning `MyObject` to a val `a` and `b`

**Step 3:** Determine that they are the same reference, by using `eq` which returns `true` if two references are pointing to the same object

**Step 4:** Determine if they are the same with object value by using either `a.equals(b)` or `a == b`

**NOTE** In scala, `==` is the same as `.equals()` as Java. `.equals()` is also available in Scala, but rarely used`

## How we avoid static

* We can add values, or variables, and methods to an object
* When we invoke those values, variable, and methods it looks and feels like invoking something static

## An example object with a def

* You can have `val`, `var`, `class`, `object`, `trait` in an object
* Here is `MyObject` which is an object with a method foo


```scala
object MyObject {
   def foo(x:Int, y:Int) = x + y
}
```




    defined object MyObject
    



This can be invoked using:


```scala
MyObject.foo(4, 2)
```




    res1: Int = 6
    



This has a look and feel of Java static method

## When do you need `object`?

* For Classes
  * Need to define a template to create multiple instances
  * Every instance has a state
* For Objects
  * You need a singleton
  * You need a factory pattern, which defined as: Creating families of related or dependent objects without specifying or hiding their concrete classes.
  * You need to implement pattern matching logic
  * You need create a utility that doesn’t require and instance or a state.
  * You have some default values or constants

## The `main` method

The main method in Java requires all of this so that we can execute it as an application
```
public static void main(String[] args) {
   System.out.println("Hello, Scala")
}
```

The same elements apply in Scala although the components are different
* `object` instead of `static`
* `Unit` instead of `void`
* Everything is `public` by default
* `Array[String]` instead of `String[]`

Therefore the `main` method in Scala looks like:


```scala
object Runner { //Call it whatever you want
  def main(args:Array[String]):Unit = println("Hello, Scala")
}
```




    defined object Runner
    



## Alternative `main` method

As seen already You can also create a main method doing the following:


```scala
object Runner extends App {
   println("Hello, Scala")
}
```




    defined object Runner
    



# `object` Conclusion

* Objects are Singletons
* Objects are Scala’s replacement for `static`
* Objects are typically meant for factories, utilities, defining pattern matching, defining defaults, and `main` methods
* `main` methods are inside of objects…​always
* You can forgo the main method declaration have the object extend `App`.
