# Integer Value Object

## Setup (Before you meet the Assessee) 

Start with two blank files. One for the test and one for the implementation.

## Explain The Assessment

### Reassurance and Reasoning

This is not a test.
 
You cannot fail this. 

We want to understand were we can help you to be a better software developer. 

If you do not understand anything that I say please do not worry about asking a question. There is no mark from this 
assessment the only outcome will be suggested reading, tutorials or additional training.

### The Task
    
The task is to create an Integer class that can be used as a value object.

This should type hinting or return types only function is_*() and get_type() can be used

**Do you know what the difference between a class and an object is?**

A class is a template for defining objects.
 
It specifies the names and types of variables that can exist in an object, as well as methods for operating on those variables.
 
An Object is an instance of that class that can hold values and be operated upon.

**Do you know what a Value Object Is?**

a value object is a small object that represents a simple entity whose equality is not based on identity: i.e. two value 
objects are equal when they have the same value, not necessarily being the same object.

**Do you know what an Integer is?**

a number which is not a fraction; a whole number

## Code

*Please note*: that the test function has been named to enable you to question the naming of functions in the Integer 
class. **Do not** change the test function names.

### Is should instantiated with an integer given

```php
public function testObjectCanBeCreated()
{
	$this->assertInstanceOf(Integer::class, new Integer(1));
}
```

### It should be able to returns it value as an integer
```php
public function testWeCanGetTheObjectsNumber()
{
	$one = new Integer(1);

	$this->assertEquals(1, $one->getValue());
}
```
**What should we name the variable holding the value?**

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
	$smallerInteger = new Integer(1);
	$largerInteger = new Integer(2);

	$this->assertTrue($largerInteger->greaterThan($smallerInteger));
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
	$this->setExpectedExceptionMessage(
“Divideing 5 by 2 does not create a whole number”
	);
	
	$five = new Integer(5);
	$two = new Integer(2);

	$five->divideBy($two);
}
```