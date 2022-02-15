Program specs
* 3 args:
  - argv[1] : number of fraction bits (n) between 2 and 10 to be used in the representation
      - 

  - argv[2] : number of exponent bits (k) betweeen 3 and 5 to be used in the representation
      - calculate the bias as 2^(argv[2]-1)-1

  - argv [3] : hexadecimal representation of the number you want to parse assuming the settings given in the first two args
      -make sure this is within the bounds allowed

======
|s|eeee|mmmmm| for input fp_parse 5 4 0xFF

Formula: Given s (sign bit 0 or 1),
         mantissa M (0...0 to 1...1)
         biased exponent E

         Value = (-1)^s * 1.M x 2^(E-127)
======
User validation:
o argv[1] must be between 2 and 10 (exponent bits)
o argv[2] must be between 3 and 5 (exponent bits)
o argv[3] must be a hex representation of a number
    -the number of bits to represent arg[3] must be
     1 + argv[2] + argv[1]
======
Special Values:
- NaN
  - exp is all ones with a zero sign bit, mantissa not zero
- infinity
  -exp all ones and mantissa all zeroes
- 0
  -exp and mantissa all zeroes
======
The Algorithm 
  Given int frc = argv[1],int exp = argv[2],
  ul bitfield = argv[3]
o int bias = (2 E-1) - 1
o int totalbits = frc + exp + 1;
o if(1<<totalbits &1) print '-'
o 
