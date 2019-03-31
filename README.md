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

and the 64 binary words Ki given by the 32 first bits of the fractional parts of the cube roots of the first
64 prime numbers:

0x428a2f98 0x71374491 0xb5c0fbcf 0xe9b5dba5 0x3956c25b 0x59f111f1 0x923f82a4 0xab1c5ed5
0xd807aa98 0x12835b01 0x243185be 0x550c7dc3 0x72be5d74 0x80deb1fe 0x9bdc06a7 0xc19bf174
0xe49b69c1 0xefbe4786 0x0fc19dc6 0x240ca1cc 0x2de92c6f 0x4a7484aa 0x5cb0a9dc 0x76f988da
0x983e5152 0xa831c66d 0xb00327c8 0xbf597fc7 0xc6e00bf3 0xd5a79147 0x06ca6351 0x14292967
0x27b70a85 0x2e1b2138 0x4d2c6dfc 0x53380d13 0x650a7354 0x766a0abb 0x81c2c92e 0x92722c85
0xa2bfe8a1 0xa81a664b 0xc24b8b70 0xc76c51a3 0xd192e819 0xd6990624 0xf40e3585 0x106aa070
0x19a4c116 0x1e376c08 0x2748774c 0x34b0bcb5 0x391c0cb3 0x4ed8aa4a 0x5b9cca4f 0x682e6ff3
0x748f82ee 0x78a5636f 0x84c87814 0x8cc70208 0x90befffa 0xa4506ceb 0xbef9a3f7 0xc67178f2


### Running the program
* Compile the program using the command. ( gcc -o sha256 sha256.c )
* Run the program using the command. ( ./sha256 < name-of-file-here > e.g. (./sha256 test ))
    
The output should look like this for test file containing the string. 

"This is a test file for the secure hash algorithm 256". 

Hash value of file is: 
b71ce26e 92d898de 7bb543a4 1a6256bf e93f4d9a c8e101c2 a6dfea9c 84a99c99





