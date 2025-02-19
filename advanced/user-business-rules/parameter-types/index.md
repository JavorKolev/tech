# Parameter types

Parameter types specify how to obtain a parameter value:

- **Constant** - indicates the value for this param type would be a constant whenever the rule is activated;
- **Attribute** -  the value of the system or user-defined attribute;
- **Reference** -  link to another object, typically used with _Attribute_ as a second parameter. <br> The attributes would be attributes of the referenced object - not of the current repository;
- **ChildList** - detailed objects related to the current master object;
- **[FormattedString](https://docs.erp.net/tech/advanced/user-business-rules/parameter-types/formattedstring.html)** - Text which supports multi-line, variable interpolation, and variable formatting.

