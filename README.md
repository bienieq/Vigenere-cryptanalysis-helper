# Vigenere-cryptanalysis-helper

University project - Vigenere cryptanalysyis helper application with web interface 

## Features

There are 2 aviable options:

**Search for key length using Kasiski's test**

- Option for unknown key length.

First, the program finds the n-grams (lenght: 3 and 4) and the biggest distance between their consequent apperances int the ciphertext.
After that, we are provided with common divisors (representing the length of the key, here the limited value is 24 characters so the list contains range from 2 to 24) and the count of n-grams distances divisible by them. The most probable key length values are the divisors with most hit counts (without considering the really small values, like 2 or 3 since a key of that length would be trivially easy to break, so it's best to consider the larger ones first).

Our prediction on the key lenght can be verified by the second option.

**Find the key - chi-squared statistics**

- Option for known key length.

Here, the application will try to find the most probable key letters based on [Chi squared statistics](http://www.practicalcryptography.com/cryptanalysis/stochastic-searching/cryptanalysis-vigenere-cipher/#finding-the-key) and decrypt provided ciphertext with the found key. Based on the output we can verify if the found key is correct.

<img width="573" alt="site" src="https://user-images.githubusercontent.com/127363211/225180874-fe57c39c-a486-4186-b731-d71b298d1403.png">

## Example

Plaintext:
One morning, when Gregor Samsa woke from troubled dreams, he found himself transformed in his bed into a horrible vermin.

(text source: [Franz Kafka - Metamorphosis](https://www.gutenberg.org/files/5200/5200-h/5200-h.htm))

Key:
VIGENERE

Ciphertext:
Jvk qbvemio, clrr Xvzouv Fedwv euor jish bxshfciy lxinqj, lz nuyah ymhakps xieialseqvh dv nmf fvh dvzs n lfvmqhpr zvvhqt.

<img width="893" alt="example01" src="https://user-images.githubusercontent.com/127363211/225180364-b4ef6572-cb52-4393-ae2d-7cc2b72490a4.png">

### Limitations and issues

This tool uses statistical-based analysis, and errors may occur due to the text and key properties. For best results, longer texts are recommended.

## Application structure

The application was built on a docker container image based on NGINX and Alpine Linux using Python and Flask to create the web page. The logic of cryptanalysis was written in C++. Please note that the main focus of this project was to write the analysis/decryption program. Therefore, the setting up of the web application was less important at the time of creating the project. As a result, this part contains a lot of makeshift code and is not as polished as I would have liked.

## Helpful sources

- [practical cryptography - vigenere and gronsfeld cipher](http://www.practicalcryptography.com/ciphers/classical-era/vigenere-gronsfeld-and-autokey/)

- [crypto corner - kasiski analysis, breaking the code](https://crypto.interactive-maths.com/kasiski-analysis-breaking-the-code.html#intro)
