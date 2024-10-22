# Message Mixer

## Overview
*Message Mixer* is a message-encryption service designed to transform input text using various ciphers. It allows users to encrypt messages through different methods and displays the encrypted output to the console. The service offers three encryption methods to customize how messages are transformed.

## Project Structure
This Codecademy Intermediate JavaScript project is built using a modular approach, featuring two files: `message-mixer.js` and `encryptors.js`. The encryption functions are defined in `encryptors.js` and are imported into `message-mixer.js` for use. This structure enables easier maintenance and reuse of the encryption logic.

## Requirements

### `encryptors.js` Module
Contains the encryption functions used by `message-mixer.js`.

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

## Usage
To run the encryption service, execute the following command in the terminal:

```bash
node message-mixer.js ['caesar'|'symbol'|'reverse'] [amount]
```
