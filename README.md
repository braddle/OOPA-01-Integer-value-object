# Integer Value Object

This is the first in a set of assessments to gage another developers understaning of Object Orientated Programming (OOP).
The assessments make use of Test Driven Development (TDD) and Pair Programming practises. During the assessment the 
assessor should write all the code. Whilst discussing how to test and implement the functionality.

The assessment is scripted out in the rest of this document. 

I have added links to recommended reading and tutorials throughout the assessment script. These are to be given to the 
person being assessed at the end of the assessment. If you have other suggestions please submit a pull request.

The script slowly builds up the complexity of the features. If the person you are assessing is struggling it should be 
possible to end the assessment at any point rather than having someone struggle through the remaining tasks.

## Setup

Please ensure you read through the entire script before you start assessing.

 - Checkout this Repo
 - Open `src/Integer.php` This should only contain the open php tag and the namespace line.
 - Open `test/IntegerTest.php` This should be an empty IntegerTest class that extends TestCase.
 - Have the two files split vertically in you IDE. It should always be possible to see both files.
 - Open us the terminal in your IDE ready to run the tests.
 
 Ensure you have done to above setup before you start meet with the person being assessed.

## Explain The Assessment

This task should take around an hour.

### Reassurance and Reasoning

This is not a test.
 
You cannot fail this. 

We want to understand were we can help you to be a better software developer. 

If you do not understand anything that I say please do not worry about asking any questions. There is no mark from this. 
The assessments only outcome will be suggested reading, tutorials or additional training.

### The Task
    
The task is to create an Integer class that can be used as a value object.

This implementation cannot use type hinting or return types. The only functions available are is_*() and get_type().

**Do you understand what Mutable and Immutable value of an Object are**
A mutable object is an object whose state can be modified after it is created. An immutable object is an object whose 
state cannot be modified after it is created.

_Suggested Reading_ ???

**Do you know what the difference between a class and an object is?**

A class is a template for defining objects.
 
It specifies the names and types of variables that can exist in an object, as well as methods for operating on those variables.
 
An Object is an instance of that class that can hold values and be operated upon.

_Suggested Reading_ ???

**Do you know what a Value Object Is?**

A value object is a small object that represents a simple entity whose equality is not based on identity: i.e. two value 
objects are equal when they have the same value, not necessarily being the same object.

_Suggested Reading_ ???

**Do you know what an Integer is?**

a number which is not a fraction. A whole number.

## Code

*Please note*: that the test functions have been named to enable you to question the naming of functions in the Integer 
class. **Do not** change the test function names. I know some of them may be a bit odd.

### Is should instantiated with an integer given

```php
public function testIntgerObjectCanBeCreated()
{
	$this->assertInstanceOf(Integer::class, new Integer(1));
}
```
**What is the term used for creating an object?** Instatiate 

### It should be able to returns it value as an integer
```php
public function testWeCanGetTheObjectsNumber()
{
	$one = new Integer(1);

	$this->assertEquals(1, $one->getValue());
}
```
**What shall we call the variable in the test?**
**What should we name the variable holding the value?**
**What word to we use to referer to basic types** Scalar

### It should know if it is equal to another integer object
```php
public function testWeCanCheckTheValuesAreTheSame()
{
	$oneA = new Integer(1);
	$oneB = new Integer(1);

	$this->assertTrue($oneA->equals($oneB));
}
```
**What should we call the function that checks the values are the same?**

### It should know if it is not equal to another integer object
```php
public function testItRecognisesIfItsHasDifferentValueToAnotherIntegerObject()
{
	$firstInteger = new Integer(1);
	$secondInteger = new Integer(2);

	$this->assertFalse($firstInteger->equals($secondInteger));

}
```

### It should know if its value is larger than another integer objects value
```php
public function testItRecognisesItsValueIsLargerThanAnotherValue()
{
	$one = new Integer(1);
	$two = new Integer(2);

	$this->assertTrue($two->greaterThan($one));
}
```
**What should the function that recognises the value is larger than another be called?**

### It should know if its value is not larger than another integer objects value
```php
public function testItRecognisesItsValueIsNotLargerThanAnotherValue()
{
	$one = new Integer(1);
	$two = new Integer(2);

	$this->assertFalse($one>greaterThan($two));
}
```

### It should know if it is less than another integer object.
```php
public function testItRecognisesItsValueIsSmallerThanAnotherValue()
{
	$one = new Integer(1);
	$two = new Integer(2);

	$this->assertTrue($smallerInteger>lessThan($largerInteger));
}
```
**What should we call the test function**
**What should the function that recognises the value is smaller than another be called?**


### It should throw an exception when instantiated with a string?
```php
public function testItDoesNotAcceptStringsOnConstruction
{
	$this->setExpectedException(\Exception::class);
	$this->setExpectedExceptionMessage(“Integer class cannot be instantiated with a string”);

	New Integer(“one”);
}

```
**What a string is?**

a string is traditionally a sequence of characters, either as a literal constant or as some kind of variable.

**What is an Exception?**

Exception handling is the process of responding to the occurrence, during computation, of exceptions – anomalous or 
exceptional conditions requiring special processing – often changing the normal flow of program execution.

### It should throw an exception when given a boolean?
```php
public function testItDoesNotAcceptBooleansOnConstruction()
{
	$this->setExpectedException(\Exception::class);
	$this->setExpectedExceptionMessage(“Integer class cannot be instantiated with a boolean”);

	New Integer(true);	
}

```
**What is a boolean?**

a Boolean data type is a data type with only two possible values: true or false.

### It should throw an exception when instantiated with a float?
```php
Public function testItDoesNotAcceptFloatsOnConstruction()
{
	$this->setExpectedException(\Exception::class);
	$this->setExpectedExceptionMessage(“Integer class cannot be instantiated with a float”);

	New Integer(1.3);	
}
```
**What is a Float?**

floating point is the formulaic representation that approximates a real number so as to support a trade-off between 
range and precision.

### It should be able to add it value to another integer
```php
public function testItCanAddTheValueOfAnotherInterger()
{
	$one   = new Integer(1);
	$two   = new Integer(2);
	$three = $one->add($two);

	$this->assertInstanceOf(Integer::class, $three);
	$this->assertEquals(1, $one->getValue());
	$this->assertEquals(2, $two->getValue());
	$this->assertEquals(3, $three->getValue());
}

```

### It should be able to subtract it value to another integer
```php
public function testItCanSubtractheValueOfAnotherInterger()
{
	$three = new Integer(3);
	$one   = new Integer(1);
	$two   = $three->subtract($one);

	$this->assertInstanceOf(Integer::class, $two);
	$this->assertEquals(1, $one->getValue());
	$this->assertEquals(2, $two->getValue());
	$this->assertEquals(3, $three->getValue());
}
```

### It should be able to divide it value to another integer
```php
public function testItCanDividetheValueOfAnotherInterger()
{
	$twelve = new Integer(12);
	$two    = new Integer(2);
	$six    = $twelve->divide($two);

	$this->assertInstanceOf(Integer::class, $six);
	$this->assertEquals(12, $twelve->getValue());
	$this->assertEquals(2, $two->getValue());
	$this->assertEquals(6, $six->getValue());
}
```

### It should throw an exception if it cannot divide to an integer
```php
Public function testItDoesNotAllowDivitionIfItCannotPreduceAnInteger()
{
	$this->setExpectedException(\Exception::class);
	$this->setExpectedExceptionMessage(“Divideing 5 by 2 does not create a whole number”);
	
	$five = new Integer(5);
	$two = new Integer(2);

	$five->divideBy($two);
}
```