# The Theory of Algorithms
### Student: G00340314
### Lecturer: Dr. Ian McLoughlin


The secure hash algorithm or SHA is a set of cryptographic hash functions. A hash function is a type of mathematical function which turns data into a fingerprint of that data called a hash. It’s like a formula or algorithm which takes the input data and turns it into an output of a fixed length, which represents the fingerprint of the data. The algorithm can be used to encrypt data so that the resulting output will be completely indistinguishable from the original data. This makes it very difficult to determine the input even if you know the output.
 

A message or data is processed by blocks of 512 = 16 × 32 bits, each block requiring 64 rounds.

### Specifications
This program was created on a [google cloud](https://cloud.google.com/) virtual machine running [Debian GNU/Linux 9](https://www.debian.org/) operating system with the [Vi text editor](https://www.vim.org/download.php) installed.

### Basic operations
* Boolean operations AND, XOR and OR, denoted by ^,  and _, respectively.
* Bitwise complement, denoted by ¯.
* Integer addition modulo 2^32, denoted by A + B.

Each of them operates on 32-bit words. For the last operation, binary words are interpreted as
integers written in base 2.

* RotR(A, n) denotes the circular right shift of n bits of the binary word A.
* ShR(A, n) denotes the right shift of n bits of the binary word A.
* A||B denotes the concatenation of the binary words A and B.

### Functions and constants
The algorithm uses the functions:
* Ch(X, Y,Z) 
* Maj(X, Y,Z)
* SIG0(X)
* SIG1(X)
* sig0(X)
* sig1(X)
* Constant H
uint32_t H[8] = {
      0x6a09e667, 0xbb67ae85
    , 0x3c6ef372, 0xa54ff53a
    , 0x510e527f, 0x9b05688c
    , 0x1f83d9ab, 0x5be0cd19
  };


and the 64 binary words Ki given by the 32 first bits of the fractional parts of the cube roots of the first
64 prime numbers:
* Constant K
uint32_t K[] = {
 
    0x428a2f98, 0x71374491, 0xb5c0fbcf, 0xe9b5dba5,
    0x3956c25b, 0x59f111f1, 0x923f82a4, 0xab1c5ed5,
    0xd807aa98, 0x12835b01, 0x243185be, 0x550c7dc3,
    0x72be5d74, 0x80deb1fe, 0x9bdc06a7, 0xc19bf174,
    0xe49b69c1, 0xefbe4786, 0x0fc19dc6, 0x240ca1cc,
    0x2de92c6f, 0x4a7484aa, 0x5cb0a9dc, 0x76f988da,
    0x983e5152, 0xa831c66d, 0xb00327c8, 0xbf597fc7,
    0xc6e00bf3, 0xd5a79147, 0x06ca6351, 0x14292967,
    0x27b70a85, 0x2e1b2138, 0x4d2c6dfc, 0x53380d13,
    0x650a7354, 0x766a0abb, 0x81c2c92e, 0x92722c85,
    0xa2bfe8a1, 0xa81a664b, 0xc24b8b70, 0xc76c51a3,
    0xd192e819, 0xd6990624, 0xf40e3585, 0x106aa070,
    0x19a4c116, 0x1e376c08, 0x2748774c, 0x34b0bcb5,
    0x391c0cb3, 0x4ed8aa4a, 0x5b9cca4f, 0x682e6ff3,
    0x748f82ee, 0x78a5636f, 0x84c87814, 0x8cc70208,
    0x90befffa, 0xa4506ceb, 0xbef9a3f7, 0xc67178f2
  
  };

We call the hashing function using a message block so that we can pad the file when needed.

union msgblock {
  uint8_t* e[64];
  uint32_t t[16];
  uint64_t s[8];
  };

  
Use emuns to store the state of the padding
* enum status {READ , PAD0, PAD1, FINISH};
SHA 256 works by reading message block of size 512, with the last 64 bits of the block left to denote the size of the original message. When the program reads in the file, it takes the bits of all the data and adds it up. It then add a one and pads the message block out with zeros to 448 bits. 512 - 64 = 448.

A message of 3 characters with 8 bits each, 3 X 8 = 24
A one is then added to the message 24 + 1 = 25
The program will pad the message out with 423 zeros 448 - 25 = 423
Leaving the last 64 bits so that a number representing the bits in the original message can be added to the block.
If a message message contains more than 512 bit then multiple blocks of 512 are used
If a message is 765 bits in size, the first block will take the first 512 bits
The second block then takes the remaining 253 bits 756 - 512 = 253
A one is then added to the message 253 + 1 = 254
The program will pad the message out with 194 zeros 448 - 254 = 194
Leaving the last 64 bits so that a number representing the bits in the original message can be added to the block

### Running the program
* Compile the program using the command. ( gcc -o sha256 sha256.c )
* Run the program using the command. ( ./sha256 < name-of-file-here > e.g. (./sha256 test ))
    
The output should look like this for test file containing the string. 

"This is a test file for the secure hash algorithm 256". 

Hash value of file is:

b71ce26e 92d898de 7bb543a4 1a6256bf e93f4d9a c8e101c2 a6dfea9c 84a99c99

### Resources 
Many thanks to Dr. Ian McLoughlin for his videos on how to create this project.
[sha256](https://codeshare.co.uk/blog/sha-256-and-sha-512-hash-examples/)
[java example](https://www.geeksforgeeks.org/sha-256-hash-in-java/)



