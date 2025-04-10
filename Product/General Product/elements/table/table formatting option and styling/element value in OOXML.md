# table formatting option and styling
## objectives
I will teach you the meaning of the value of `w:val` attribute (which determines the behaviour of table formatting option and styling).
## meaning of value
value of `w:val` attribute should be a hexadecimal number.

Xml preprocessor of Office Word uses bitmask to configure the behaviour of table formatting option and styling.

Step 1:

1. convert the value of `w:val` attribute from hexadecimal number to binary number (as bitmask operation only available on binary number)

2. Step 2:

3. find all bits that is set to 1 in the converted binary number.

4. Step 3:

5. look at option code for [table formatting option and styling](https://github.com/40843245/Microsoft_Office/blob/main/Product/General%20Product/elements/table/table%20formatting%20option%20and%20styling/option%20code.md)

6. Then you can know how the table will be formatted.

### examples
#### example 1
For example,

`<w:tblLook w:val="04A0"/>`

Its value of the attribute `w:val` is `04A0`.

Step 1:

`0x04A0` = `0b 0000 0100 1010 0000`

Step 2:

The 5th bit (counting from LST, zero-based) (`0b 0000 0000 0010 0000`) is set to 1.

The 7th bit (counting from LST, zero-based) (`0b 0000 0000 1000 0000`) is set to 1.

The 10th bit (counting from LST, zero-based) (`0b 0000 0100 0000 0000`) is set to 1.

Step 3:

Look at mapping table about option code.

`0b 0000 0000 0010 0000` => Apply first row for conditional formatting.

`0b 0000 0000 1000 0000` => Apply first column for conditional formatting.

`0b 0000 0100 0000 0000` => Don't apply column banding for conditional formatting.

Thus, we can know the table will

+ Apply first row for conditional formatting.
+ Apply first column for conditional formatting.
+ Don't apply column banding for conditional formatting.
