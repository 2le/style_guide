From [ISO/IEC 11179](http://standards.iso.org/ittf/PubliclyAvailableStandards/c035347_ISO_IEC_11179-5_2005(E).zip)

4.1 Requirements A data definition shall:
a) be stated in the singular
b) state what the concept is, not only what it is not
c) be stated as a descriptive phrase or sentence(s)
d) contain only commonly understood abbreviations
e) be expressed without embedding definitions of other data or underlying concepts
4.2 Recommendations A data definition should:
a) state the essential meaning of the concept
b) be precise and unambiguous
c) be concise
d) be able to stand alone
e) be expressed without embedding rationale, functional usage, or procedural information
f) avoid circular reasoning
g) use the same terminology and consistent logical structure for related definitions
h) be appropriate for the type of metadata item being defined

* **Object class**: an object class is a set of ideas, abstractions or things in the real world that are identified with explicit boundaries and meaning, and whose properties and behaviour follow the same rules.

In the data element names "Employee Last Name", "Cost Budget Period Total Amount", "Tree Height Measure" and "Member Last Name", the terms `Employee`, `Cost`, `Tree`, and `Member` are object class terms.

a Property is a characteristic common to all members of an object class. Each property has a name. The registration of properties in a registry is optional, but if used, the set of actual and potential property names provides a taxonomy of property terms.
the terms `Last Name`, `Total Amount`, and `Height` are properties.


A representation term may be a part of an administered item name that describes the form of representation of an administered item that includes representation: data elements and value domains.

Using the above rules, a data element describing a measurement of the height of a tree would have the data element name Tree Height Measure. The word Measure is the data element's representation term. However, a data element that describes the last name of a person would have the data element name of Person Last Name Name. The second word Name is the data element's representation term. However, to promote clarity, one occurrence of the redundant word is removed.

Amount      	Monetary value with units of currency.
BinaryObject	Set of finite-length sequences of binary octets used to represent sound, images and other structures.
Code        	An enumerated list of all allowable values. Each enumerated value is a string that for brevity represents a specific meaning. For example for a PersonGenderCode the valid values might be "male", "female" or "unknown".
Date        	An ISO 8601 date usually in the format YYYY-MM-DD
DateTime    	An ISO 8601 date (in the format YYYY-MM-DD) AND time structure. Note: Do not use unless BOTH the date AND time are REQUIRED fields. If one OR the other is optional always specify the data elements as separate date and time elements.
Graphic     	Used to store images. Secondary to Binary Object.
ID          	Abbreviation for Identifier
Identifier  	A language-independent label, sign or token used to establish identity of, and uniquely distinguish one instance of an object within an identification scheme.
Indicator   	Boolean, exactly two mutually exclusive values (true or false). A precise definition must be given for the meaning of a true value.
Measure     	Numeric value determined by measurement with units. Typically used with items such as height or weight. if the unit of measure is not clear it should be specified.
Name        	A textual label used as identification of an object. A name is usually meaningful in some language, and is the primary means of identification of objects for humans. Unlike an identifier, a name is not necessarily unique.
Number      	Assigned or determined by calculation.
Percent     	A type of Numeric that traditionally is the results of a ratio calculation that ranges from values of 0 to 1 for values of 0% to 100%.
Quantity    	Non-monetary numeric value or count with units.
Rate        	A type of Numeric
Text        	Character string generally in the form of words.
Time        	An ISO 8601 time structure.
Value       	A type of Numeric.
Year        	An ISO 8601 Year

(ISO/IEC 11179 Metadata Registry)

Qualifier terms may be attached to object class terms, property terms, and representation terms if necessary to distinguish one data element concept, conceptual domain, data element, or data value domain from another. These qualifier terms may be derived from structure sets specific to a context. In the rules for a naming convention, a restriction in the number of qualifier terms is recommended.
For example, in the data element name "Cost Budget Period Total Amount", the term `Budget Period` is a qualifier term.


Object classes represent things of interest in a universe of discourse that may, for instance, be found in a model of that universe. (ex: `Cost`). Exactly one object class term shall be present.
Property terms shall be derived from the property system structure set and represent a characteristic of the object class (ex: `Total Amount`). Exactly one property term shall be present.
The combination of object class term and property term forms the names for data element concepts.
Qualifiers may be derived as determined by the subject area authority and will be added as needed to make the name unique within a specified context (ex: `Budget Period`). The order of the qualifier terms is not significant. Qualifier terms are optional.
The representation of the valid value set of a data element or value domain is described by the representation term.
Exactly one representation term shall be present (ex: `Amount`). Representation terms, usually with added qualifiers, form value domain names.

Syntactic rules:
a) The object class term shall occupy the first (leftmost) position in the name.
b) Qualifier terms shall preceed the part qualified. The order of qualifiers shall not be used to differentiate names.
c) The property term shall occupy the next position.
d) The representation term shall occupy the last position. If any word in the representation term is redundant with any word in the property term, one occurrence will be deleted.
EXAMPLE Cost Budget Period Total Amount

Lexical rules:
a) Nouns are used in singular form only. Verbs (if any) are in the present tense.
b) Name parts and words in multi-word terms are separated by spaces. No special characters are allowed.
c) All words in the name are in mixed case. The rules of “mixed case” are defined by the RA. These rules may by different for different parts of the administered item name (object class, property, representation class).
d) Abbreviations, acronyms, and initialisms are allowed.
EXAMPLE Cost Budget Period Total Amount
Uniqueness rule:
All names in each language shall be unique within this context.


http://www5.opengroup.org/udef/htm/en_objects.htm

[UDEF Full Property Tree](http://www5.opengroup.org/udefinfo/htm/en_properties.htm)

 1 Amount - A number of monetary units specified in a currency
  2 Graphic - a diagram, graph, mathematical curve or similar representation (a type of binary object)
  3 Picture - a visual representation of a person, object, or scene (a type of binary object)
  4 Code - a character string used to replace a definitive value
  5 Date-Time - a particular point in the progression of time
  6 Date - A day within a particular calendar year (a type of date time)
  7 Indicator - a list of two and only two possible values (synonym for Boolean)
  8 Identifier - A character string used to identify and distinguish uniquely
  9 Percent - a rate expressed in hundredths between two values with same UoM (a type of numeric)
  10 Name - a word or phrase that distinctively designates a person, place, etc. (a type of text)
  11 Quantity - a counted number of non-monetary units (a type of numeric)
  12 Rate - a quantity or amount measured with respect to another quantity or amount (a type of numeric)
  13 Measure - a numeric value that is determined by measuring an object. Measures are specified with a unit of measure.
  14 Text - a character string generally in the form of words of a language
  15 Time - the time within a (not specified) day (a type of date time)
  16 Value - numeric information that is assigned or determined by calculation, counting, or sequencing (a type of numeric)
  17 Sound - a binary object that is capable of creating audio (a type of binary object)
  18 Video - a binary object that is capable of creating motion pictures/graphics (a type of binary object)
 

 


