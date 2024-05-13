# The Caesar and Vigenère Ciphers
In this tutorial we will write two programs for implementing the Caesar and Vigenère Ciphers in Python. Let's begin.

## Program 1: The Caesar Cipher
The Caesar Cipher is a simple and widely known encryption technique where each letter in the plaintext is shifted
a certain number of places down or up the alphabet. For example, with a shift of 3, A would be replaced by D,
B would become E, and so on.

Let's write the program:
```python runnable
# Define a word:
word = "HELLO"

# Create a variable called shift, which can be negative or positive:
shift = 3

# Create a function to encode input and return the result:
def Caesar(word, shift):
    encoded = ""
    for char in word:
        # The integer '97' is the ordinal value in Unicode Point Code that represents the character "a".
        encoded += chr(((ord(char) - 97 + shift) % 26) + 97)
    # Check the case of the word, and match the case for the encoding.
    if word.isupper():
        return encoded.upper()
    else:
        return encoded

print(Caesar(word, shift))
```
The result of this code will be: "EBIIL".

## Program 2: The Vigenère Cipher
The Vigenère cipher is a method of encrypting alphabetic text where each letter of the plaintext is encoded with
a different Caesar cipher, whose increment is determined by the corresponding letter of another text, the key.

Let's write the program:
```python runnable
# Define a word:
word = "HELLO"

# Create a variable called key:
key = "THREE"

# Extend the length of keyword until it is greater-than or equal to word.
while len(key) < len(word):
    key+=key

key = key[:len(word)] # Trim the key to the length of the word. We are using a "splice" here.

# Define a function that encodes a word using a keyword and returns the result.
def Vigenère(word, key):
    encoded_word = ""
    for i, char in enumerate(word):
        key_char = key[i % len(key)]  # Use modulo to repeat the key if it's shorter than the word
        encoded_char = chr(((ord(char) - 65 + ord(key_char) - 65) % 26) + 65)  # Apply Vigenère cipher logic
        encoded_word += encoded_char
    return encoded_word

print(Vigenère(word, key))
```
The result of this code will be: "ALCPS"

### Conclusion
There we go. We have two programs for the Caesar and Vigenère Ciphers.

If you'd like to read up some information on the Ciphers, I have added some links below:

https://en.wikipedia.org/wiki/Caesar_cipher

https://en.wikipedia.org/wiki/Vigenère_cipher

Feel free to use this code.

Happy Coding,
@Code-Parser