# Message Mixer

## Overview
*Message Mixer* is a message-encryption service designed to transform input text using various ciphers. It allows users to encrypt messages through different methods and displays the encrypted output to the console. The service offers three encryption methods to customise how messages are transformed.

## Project Structure
This Codecademy Intermediate JavaScript project is built using a modular approach, featuring three files: `message-mixer.js`, `encryptors.js`, and `super-encoder.js`. The encryption functions are defined in `encryptors.js` and are imported into both `message-mixer.js` and `super-encoder.js`. This structure enables easier maintenance and reuse of the encryption logic.

## Requirements

### `encryptors.js` Module
Contains the encryption functions used by `message-mixer.js` and `super-encoder.js`.

#### Functions:
- **`caesarCipher(str, amount)`**: Shifts each character of `str` alphabetically by `amount`.
- **`symbolCipher(str)`**: Replaces select characters in `str` with visually similar symbols.
- **`reverseCipher(str)`**: Reverses each word in `str` in place.

### `message-mixer.js` Script
Handles user input, imports functions from `encryptors.js`, and displays the encrypted output.

#### Functionality:
- Accepts user commands to specify which encryption method to use and the shift amount (if applicable).
- Reads the user input for the message to be encrypted.
- Applies the chosen encryption method.
- Displays the encrypted message to the console.

### `super-encoder.js` Script
Enhances the encryption process by combining multiple encryption methods.

#### Functionality:
- **Encoding**: Uses a combination of the Caesar cipher (with a fixed shift of 6), Symbol cipher, and Reverse cipher to encrypt messages.
- **Decoding**: Reverses the encoding process, using the same combination of ciphers in reverse order.

#### Sample Code:
```javascript
// Import the encryptors functions here.
const encryptors = require('./encryptors.js');
const {caesarCipher, symbolCipher, reverseCipher} = encryptors;

const encodeMessage = (str) => {
  // Use the encryptor functions here.
  return reverseCipher(symbolCipher(caesarCipher(str, 6)));
}

const decodeMessage = (str) => {
  // Use the encryptor functions here.
  return caesarCipher(symbolCipher(reverseCipher(str)), -6);
}

// User input / output.

const handleInput = (userInput) => {
  const str = userInput.toString().trim();
  let output;
  if (process.argv[2] === 'encode') {
    output = encodeMessage(str);
  } 
  if (process.argv[2] === 'decode') {
    output = decodeMessage(str);
  } 
  
  process.stdout.write(output + '\n');
  process.exit();
}

// Run the program.
process.stdout.write('Enter the message you would like to encrypt...\n> ');
process.stdin.on('data', handleInput);


## Usage
To run the encryption service, execute the following command in the terminal:

```bash
node message-mixer.js ['caesar'|'symbol'|'reverse'] [amount]
```

To use the super encoder, run:

```
node super-encoder.js [encode|decode]
``` 

## Examples

### Caesar Cipher:

```
$ node message-mixer.js caesar 4
Enter the message you would like to encrypt...
> hello world

Here is your encrypted message:
> lipps asvph
```

### Reverse Cipher:

```
$ node message-mixer.js reverse
Enter the message you would like to encrypt...
> hello world

Here is your encrypted message:
> olleh dlrow
```

### Super Encoder (Encoding):

```
$ node super-encoder.js encode
Enter the message you would like to encrypt...
> codecademy

Here is your encoded message:
> kfgggkgrgu
```

### Super Encoder (Decoding):

```
$ node super-encoder.js decode
Enter the message you would like to decrypt...
> kfgggkgrgu

Here is your decoded message:
> codecademy
```

## Example Output
Create an instance of the Caesar cipher with a shift amount to see how the encryption alters the text:

```
$ node message-mixer.js caesar 3
Enter the message you would like to encrypt...
> codecademy
Here is your encrypted message:
> frghfdghpb
```

In this example, each character is shifted forward by 3 places in the alphabet.

## Conclusion
This project demonstrated the process of breaking down a programme into separate modules to enhance code reusability and maintainability. By isolating encryption functions into `encryptors.js` and using them in `message-mixer.js` and `super-encoder.js`, the project is better organised and more accessible for other developers who wish to implement similar encryption methods in their applications.