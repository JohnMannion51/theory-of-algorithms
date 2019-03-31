## The Theory of Algorithms
## Student: G00340314
## Lecturer: Dr. Ian McLoughlin


The secure hash algorithm or SHA is a set of cryptographic hash functions. A hash function is a type of mathematical function which turns data into a fingerprint of that data called a hash. It’s like a formula or algorithm which takes the input data and turns it into an output of a fixed length, which represents the fingerprint of the data. The algorithm can be used to encrypt data so that the resulting output will be completely indistinguishable from the original data. This makes it very difficult to determine the input even if you know the output.
 

A message or data is processed by blocks of 512 = 16 × 32 bits, each block requiring 64 rounds.

## Specifications
This program was created on a google cloud virtual machine running Debian GNU/Linux 9 operating system with the Vi text editor installed.

## How the program works
1. Compile the program using the command. ( gcc -o sha256 sha256.c )
2. Run the program using the command. ( ./sha256 < name-of-file-here > e.g. (./sha256 test ))
    
The output should look like this for test file containing the string:
"This is a test file for the secure hash algorithm 256"
Hash value of file is:
b71ce26e 92d898de 7bb543a4 1a6256bf e93f4d9a c8e101c2 a6dfea9c 84a99c99
