# Validator

Validator is Java library makes data validation  very easy in your application. This library was inspired by the Laravel framework's Validator.

### Why use Validator?
- Easy to use.
- Not dependent on any libraries.
- Readable and declarative validation rules.


## Features
- Function isNumber(number: string)
- Function isDouble(double: string)
- Function isInteger(integer: string)
- Function isSuperiorOf(value: string, max: number, isString: boolean)
- Function isInferiorOf(value: string, min: number, isString: boolean)
- Function validate(value: string, validators: string)

## Installation
Gradle:
```gradle
repositories {
    flatDir {
        dirs '../build/libs' // Path to the jar lib
    }
}

dependencies {
    compile name: 'validator'
}
```

## Usage

Don't forget to import the library when you need to use Validator:
```java
import validator;
```

Function **validate()**
```java
// Types
Validator.validate("20", "numeric"); // return true
Validator.validate("20.23", "numeric"); // return true
Validator.validate("dije", "numeric");  // return false

Validator.validate("20", "double");  // return true
Validator.validate("dezf", "double");  // return false

Validator.validate("20", "integer");  // return true
Validator.validate("20.23", "integer");  // return false

// Max
Validator.validate("-2", "numeric|max:20"); // return true
Validator.validate("20", "numeric|max:20"); // return true
Validator.validate("21", "numeric|max:20"); // return false

// Min
Validator.validate("-20", "numeric|min:20"); // return false
Validator.validate("20", "numeric|min:20"); //  return true
Validator.validate("21", "numeric|min:20"); //  return true

// Required
Validator.validate("", "required"); // return false
Validator.validate(null, "required"); // return false
Validator.validate("TOTO", "required"); // return true

// Advanced
Validator.validate("12", "required|numeric|max:20|min:0"); // return true
```

Function **isDouble()**
```java
Validator.isDouble("20.2"); // return 'true'
Validator.isDouble("20"); // return 'true'
Validator.isDouble("-20"); // return 'true'
Validator.isDouble("20n")); // return 'false'
Validator.isDouble("defrglk"); // return 'false'
```

Function **isInteger()**
```java
Validator.isInteger("20.2"); // return 'false'
Validator.isInteger("20"); // return 'true'
Validator.isInteger("-20"); // return 'true'
Validator.isInteger("20n")); // return 'false'
Validator.isInteger("defrglk"); // return 'false'
```

Function **isNumeric()**
```java
Validator.isNumeric("-20.2"); // return 'true
Validator.isNumeric("20.2"); // return 'true'
Validator.isNumeric("20"); // return 'true'
Validator.isNumeric("20n")); // return 'false'
Validator.isNumeric("defrglk"); // return 'false'
```

Function **isSuperiorOf()**
```java
Validator.isSuperiorOf("tot", 4, true); // return 'false'
Validator.isSuperiorOf("toto", 4, true); // return 'false'
Validator.isSuperiorOf("totol", 4, true); // return 'true'
Validator.isSuperiorOf("24", 4, false); // return 'true'
Validator.isSuperiorOf("2", 4, false); // return 'false'
```

Function **isInferiorOf()**
```java
Validator.isSuperiorOf("tot", 4, true); // return 'true'
Validator.isSuperiorOf("toto", 4, true); // return 'false'
Validator.isSuperiorOf("totol", 4, true); // return 'false'
Validator.isSuperiorOf("24", 4, false); // return 'false'
Validator.isSuperiorOf("2", 4, false); // return 'true'
```


## Contributing


Pull requests are welcome. For major changes, please open an issue first to discuss what you would like to change.

Please make sure to update tests as appropriate.

## License

[GPL3](https://choosealicense.com/licenses/gpl-3.0/)