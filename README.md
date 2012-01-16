ABON
====
[Official Site: under construction](under construction)

What is ABON?
-------------
* Lightweight data-interchange format
 Compared to XML or JSON
* Simple format
 Easy for humans to read and write
 Easy for machines to parse and generate
* ABON is a text format
 Programming language independent
 Uses conventions that are familiar to programmers of the C-family of languages, including C, C++, C#, Java, JavaScript, Perl, Python

Why Use ABON over XML or JSON
-----------------------------
* Lighter and faster than XML or JSON as on-the-wire data format
* ABON objects are typed while XML data is typeless
 ABON types: string, number, array, boolean   and symbol
 XML data are all string
* Native data form for Java  1.3 code
 Data is readily accessible as ABON objects in your Java code vs. XML data needed to be parsed and assigned to variables through tedious DOM APIs
 Retrieving values is as easy as reading from an objectproperty in your Java code

Where is ABON Used?
-------------------
* Represent configuration information
* Implement communication protocols

ABON Structures
---------------
* A collection of name/value pairs using keyname or just name
 In various languages, this is realized as an object, record, struct, dictionary, hash table, keyed list, or associative array
* An ordered list of values
 In most languages, this is realized as an array, vector, list, or sequence
* These are universal data structures supported by most modern programming languages

ABON Object Notation
--------------------
* An ABON object is an unordered set of name/value pairs
* An ABON object begins with \[ (open bracket) and ends with \] (close bracket)
* Each name is followed by : (colon) and after that is the value that closed by / (forward slash) and followed by ] (close bracket)

ABON and Java
-------------
* ABON is a subset of the object literal notation of Java 1.3
 ABON can be used in the Java language with no muss or fuss

### Example: ABON Object
	String myABONString = 
	"[items1:" +
	  "[item11:one one/]" +
		"[item12:
			"[item12a: one two a/]" +
			"[item12b:one two b/]" +
			"[item12c :" +
				"[item12ca: one two c a/]" +
			"]" +
		"]" +
		"[item13:one three/]" +
	"];
	ABONReader  abonReader = new ABONReader(myABONString.getBytes());

> Or from InputStream
	
	int size = inputStream.available();
	byte[] dataBytes = new byte[size];
	inputStream.read(dataBytes, 0, size);
	ABONReader abonReader = new ABONReader(dataBytes);


* In this example, an ABON Java object is created containing a single member `items1`, which contains an array containing 5 valued objects, each members represented by keyname or unique node name.
* Members can be retrieved using keyname or node name if name is unique

### Example: To retrieve ABON Object
Step-by-step method:

> Get document from ABON reader

	Document document = abonReader.getDocument();
	
> than get node from the document

	Node item11Node = document.getNode(“items1.item11”);
	Node item12caNode = document.getNode(“items1.item12.item12c.item12ca”);
	
> Or if no duplicated keyname

	Node item11Node = document.getNode(“item11”);
	Node item11Node = document.getNode(“items12ca”);
	
> finally

	String items11Name = Item11Node.getName();
	String items11Value = Item11Node.getValue();
	
	String items12caName = Item12caNode.getName();
	String items12caValue = Item12caNode.getValue();
