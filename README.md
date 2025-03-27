# Deterministic RSA JS

## Project Overview

Deterministic RSA JS is a lightweight JavaScript library that generates deterministic RSA key pairs using a seeded approach. Unlike traditional random key generation, this library allows you to create reproducible RSA keys based on a provided seed, which is useful for cryptographic applications requiring predictable key generation.

### Key Features
- 🔐 Deterministic RSA key generation
- 🧩 Fully compatible with JSON Web Key (JWK) format
- 🚀 Multithreaded prime number generation
- 🔢 Configurable key bit sizes
- 💻 Pure JavaScript implementation

### Use Cases
- Reproducible cryptographic key generation
- Blockchain and distributed systems
- Testing and simulation environments
- Cryptographic protocols requiring predictable keys

## Installation

Install the library using npm:

```bash
npm install deterministic-rsa-js
```

## API Reference

### `rsaGenKeys(bits, seed, [e])`

Generates a deterministic RSA key pair.

#### Parameters
- `bits` (number): Total number of bits for the RSA key. Must be:
  - A multiple of 32
  - At least 192 bits
- `seed` (Uint8Array): 32-byte seed for generating primes
- `e` (BigInt, optional): Public exponent, defaults to 65537

#### Returns
An object with two keys:
- `privateKey` (JsonWebKey): Complete private RSA key
- `publicKey` (JsonWebKey): Public RSA key

#### Example

```javascript
const { rsaGenKeys } = require('deterministic-rsa-js');

// Generate a 2048-bit RSA key with a specific seed
const seed = crypto.getRandomValues(new Uint8Array(32));
const { privateKey, publicKey } = await rsaGenKeys(2048, seed);
```

## Repository Structure

- `index.js`: Main library implementation
- `test.js`: Unit tests
- `package.json`: Project metadata and dependencies
- `LICENSE`: MIT License file

## Contributing

Contributions are welcome! Please follow these steps:

1. Fork the repository
2. Create a new branch (`git checkout -b feature/your-feature`)
3. Commit your changes (`git commit -m 'Add some feature'`)
4. Push to the branch (`git push origin feature/your-feature`)
5. Open a Pull Request

### Running Tests

```bash
npm test
```

## Performance and Limitations

- Prime generation is CPU-intensive
- Uses multithreading via `workerpool` for improved performance
- Seed quality directly impacts key generation consistency

## Dependencies

- `workerpool`: For multithreaded prime generation

## License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.

## Acknowledgements

Inspired by cryptographic techniques in blockchain and distributed systems.