# java

## transform Object into JSON

```JAVA
Object dataToConvert; // not to use in code, it's your Object you want to convert
ObjectMapper mapper = new ObjectMapper();
    
//JSON from file to Object
String convertedString = mapper.writeValueAsString(dataToConvert);
// Generally get this in debug and calculate it via expressions tab
```