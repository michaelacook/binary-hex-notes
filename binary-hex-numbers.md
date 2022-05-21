# Binary and Hexadecimal Numbers
- binary and hexadecimal are ways of encoding numbers in ways that are useful when programming or hacking electronics
- Assembly programs are binary numbers
- Hexadecimal numbers are ways of encoding numbers that makes it easy for humans to read and write data that's meant to be interpreted as binary by a computer 
- primary tool for rom hacking is a hex editor - make changes to binary rom files without parsing millions of 1s and 0s

## Binary
- unlike base-10 numbers which are based on powers of 10, binary numbers have 2 digits (1 and 0) and are based on powers of 2
- to convert a binary number to base-10, moving from right to left each number is multiplied by an incrementing power of 2
- eg: 1001 = 1 x 2<sup>0</sup> + 0 x 2<sup>1</sup> + 0 x 2<sup>2</sup> + 1 x 2<sup>3</sup>
  - then remove terms multiplied by 0 since they evaluate to 0: 
    - 1 x 2<sup>0</sup> + 1 x 2<sup>3</sup> = 1 + 8 = 9 

- TypeScript function to convert binary to base-10:

```ts
function binaryToBase10(bin: number): number {
  const numArr = bin.toString().split('').map(Number).reverse()

  return numArr.reduce((acc, curr, i) => {
    acc += curr * Math.pow(2, i)
    return acc
  })
}
```

- why do computers use binary instead of base-10 numbers?
  - computers are physical machines and calculate by manipulating physical states 
  - using just two physical states - on or off - is far simpler than using ten physical states
---

## Hexadecimal
- base-16 numbers
- reading binary numbers is very hard for humans
  - human brains are great at distinguishing complex and varied symbols 
  - but 1s and 0s are too simple - great for computers, hard to distinguish for humans
- hexadecimal is much easier for humans to read, but easily converted to binary
- hexadecimal has 16 numbers: `0 1 2 3 4 5 6 7 8 9 A B C D E F`
  - A - F represent 10 - 15
- To convert a hexadecimal number to base-10, moving from right to left each number is multiplied by an incrementing power of 16. It is the same algorithm used to convert binary to base-10 except that powers of 16 are used instead
- e.g: B8 = 8 x 16<sup>0</sup> + 11 x 16<sup>1</sup>
  - = 8 x 1 + 11 x 16 
  - = 8 + 176
  - = 184

### Hex to Binary
- each digit of a hexadecimal number can be perfectly represented by four binary digits or bits:

    |0|1|2|3|4|5|6|7|
    |-|-|-|-|-|-|-|-|
    |0000|0001|0010|0011|0100|0101|0110|0111|

    |8|9|A|B|C|D|E|F|
    |-|-|-|-|-|-|-|-|
    |1000|1001|1010|1011|1100|1101|1110|1111|

- conversion to binary is easy because each digit only needs to be converted to a simple binary number one at a time
- binary is also easy to convert to hexadecimal using the table
- ASCII is a character encoding system that represents characters with 8-bit numbers (ie 52, B4, 4E)
- ASCII character code table: 

    |41|42|43|44|45|46|47|48|49|4A|4B|4C|4D|
    |-|-|-|-|-|-|-|-|-|-|-|-|-|
    |A|B|C|D|E|F|G|H|I|J|K|L|M|

    |4E|4F|50|51|52|53|54|55|56|57|58|59|5A|
    |-|-|-|-|-|-|-|-|-|-|-|-|-|
    |N|O|P|Q|R|S|T|U|V|W|X|Y|Z|