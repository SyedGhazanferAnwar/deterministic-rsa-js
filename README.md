# Deterministic RSA JS

## Project Overview

**Deterministic RSA JS** is a lightweight JavaScript library for generating reproducible RSA key pairs from deterministic seeds. This library provides a unique approach to RSA key generation that allows developers to create consistent, predictable public and private key pairs using a provided seed.

### Key Features
- 🔑 Deterministic RSA key generation
- 🌐 Compatible with JSON Web Key (JWK) format
- 🚀 Multithreaded prime generation using `workerpool`
- 🔒 Supports configurable key bit sizes
- 💻 Pure JavaScript implementation
- 🧮 Implements advanced cryptographic algorithms like Miller-Rabin primality testing

### Use Cases
- Reproducible key generation for cryptographic applications
- Blockchain and distributed systems
- Testing and simulation environments
- Scenarios requiring predictable key generation

## Installation

Install the library using npm:

```bash
npm install deterministic-rsa-js
```

### Prerequisites
- Node.js (v12.0.0 or higher)
- ES6 BigInt support

## API Reference

### `rsaGenKeys(bits, seed[, e])`

Generates a deterministic RSA key pair.

#### Parameters
- `bits` (number): Total number of bits for the RSA key modulus (must be a multiple of 32, minimum 192)
- `seed` (Uint8Array): 32-byte seed for deterministic key generation
- `e` (BigInt, optional): Public encryption exponent (default: 65537n)

#### Returns
An object with two keys:
- `privateKey` (JsonWebKey): Complete private RSA key
- `publicKey` (JsonWebKey): Public RSA key

#### Example
```javascript
const { rsaGenKeys } = require('deterministic-rsa-js');

const seed = new Uint8Array(32); // Your 32-byte seed
const keyPair = await rsaGenKeys(2048, seed);

console.log(keyPair.publicKey);  // Public key in JWK format
console.log(keyPair.privateKey); // Private key in JWK format
```

## Repository Structure

- `index.js`: Main library implementation
- `test.js`: Unit tests and examples
- `package.json`: Project metadata and dependencies
- `LICENSE`: MIT license details

## Contributing

Contributions are welcome! Here's how you can help:

1. Fork the repository
2. Create a new branch (`git checkout -b feature/improvement`)
3. Commit your changes (`git commit -m 'Add some feature'`)
4. Push to the branch (`git push origin feature/improvement`)
5. Open a Pull Request

### Running Tests
```bash
npm test
```

## Performance Considerations

- The library uses multithreading for prime generation
- Implements efficient Miller-Rabin primality testing
- Uses custom random number generation (xoshiro128ss)

## License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.

## Disclaimer

This library is in beta. Use in production environments with caution and proper security review.