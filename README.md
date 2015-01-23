
==================


Bitmerchant &mdash; A free, self-hostable Bitcoin payment processor.
==========


Bitmerchant is a full [Bitcoinj](https://github.com/bitcoinj/bitcoinj)-based merchant-services platform. It lets you accept bitcoin payments or donations on your site, without having to go through an intermediary service like coinbase or bitpay; the purchases or donations go directly into a wallet that **you control**. 

For more information, head over to
TODO bitmerchant.github.io.

## Installation

To install Bitmerchant, make sure you have both java 8, and maven installed. Then run the following commands:
```
git clone https://github.com/tchoulihan/bitmerchant
cd bitmerchant
./install.sh
```


To run Bitmerchant
<pre>
java -jar target/bitmerchant.jar -params
parameters:
-testnet : run on the bitcoin testnet3
-deleteDB : delete the local database before starting

</pre>


It was inspired by [ActiveRecord ORM](https://github.com/rails/rails/tree/master/activerecord) from Ruby on Rails.

## Features include
* A fully-functioning bitcoin wallet, in a slick bootstrap-based WEBGUI. 
* Should be very easy to work with
* Should reduce amount of code to a minimum
* No configuration, just conventions
* Some conventions are overridable in code
* No need to learn another language
* No need to learn another QL &mdash; SQL is sufficient
* Code must be lightweight and intuitive, should read like English
* No sessions, no "attaching, re-attaching"
* No persistence managers
* No classes outside your own models
* Models are lightweight, no transient fields
* No proxying. What you write is what you get (WYSIWYG:))
* Should have the least possible resistance to startup a project
* No useless getters and setters (they just pollute code). You can still write them if you like.
* No DAOs and DTOs &mdash; this is mostly junk code anyway

## Simple example

For a simple example we will use a table called `people` created with this MySQL DDL:

<pre>
CREATE TABLE people (
  id  int(11) NOT NULL auto_increment PRIMARY KEY, 
  name VARCHAR(56) NOT NULL, 
  last_name VARCHAR(56), 
  dob DATE, 
  graduation_date DATE, 
  created_at DATETIME, 
  updated_at DATETIME
);
</pre>

ActiveJDBC infers DB schema parameters from a database. This means you do not have to provide it in code, the simplest example model looks like this:

```java
public class Person extends Model {}
```

Despite the fact that there is no code in it, it is fully functional and will map to a table called `people` automatically.

Here is a simple query how to use the `Person` model:
 
```Java
List<Person> people = Person.where("name = 'John'");
Person aJohn =  people.get(0);
String johnsLastName = aJohn.get("last_name");
```

As you can see, the amount of code is reduced to a level when it is actually readable. Finder methods can also be parametrized like this:

```Java
List<Person> people = Person.where("name = ?", "John");
Person aJohn =  people.get(0);
String johnsLastName = aJohn.get("last_name");
```

## Documentation

For more information, follow here: http://javalite.io