# protocol-buffer

### Tags

- Tags numbered from `1 to 15` use `1 byte` in space, so use them for frequently populated fields
- Tags numbered from `16 to 2047` use `2 byte`

### Repeated Fields

- To make a "list" or an "array", you can use the concept of repeated fields
- The list can take any number (0 or more) of elements you want
- The opposite of repeated is "singular"(we don't write it)

### Comments

- It is possible to embed comments in your .proto file
- It is actually recommended to use comments as form of documentation for your schemas

```java
// this is comment
/*
 * This is comment
 * with multiline
 */
```

### Default Value for Fields

- All fields, if not specified or unknown, will take a default value

| Type               | Value            |
|--------------------|------------------|
| bool               | false            |
| number(int32, etc) | 0                |
| string             | empty string     |
| bytes              | empty byte       |
| enum               | first enum value |
| repeated           | empty list       |

### Enums

- If you know all the values a field can take in advance, you can leverage the `Enum` type
- The first value of an Enum is the default value
- Enum must start by the tag 0(which is the default value)

### Nesting Types

- It is possible to define types within types
- The reason could be
    - avoid naming conflicts
    - Enforcing some level of "locality" for that type
- You can nest types as deeply as you want

### Importing Types

- You can also have different types in different `.proto` files
- This is useful if you want to re-use code and import other
  `.proto` files created by people in your team

### Packages

- It is very important to define the packages in which your protocol buffer messages live
    - when your code gets compiled, it will be placed at the package you indicated
    - it also helps to prevent name conflicts between messages (my.package.Person)
- Packages will help all the different languages compile correctly from `.proto` files(Java, C#, Python, Go, etc..)