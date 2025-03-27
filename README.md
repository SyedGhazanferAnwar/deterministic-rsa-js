# Deterministic RSA JS

**WARNING: This project has not yet been verified to be cryptographically secure. USE AT YOUR OWN RISK!**

## Project Overview

`deterministic-rsa-js` is a high-performance JavaScript library for generating deterministic RSA key pairs using a seed-based approach. This library is designed to:

- Generate RSA keys reproducibly from a provided seed
- Leverage native JavaScript BigInt for improved performance
- Utilize multithreading for efficient prime number generation
- Provide compatibility with JSON Web Key (JWK) standard

### Key Features

- **Deterministic Key Generation**: Generate the same RSA key pair from an identical seed
- **High Performance**: ~3x faster than alternative implementations
- **Multithreaded Prime Generation**: Uses `workerpool` for parallel prime generation
- **Native BigInt Support**: Avoids slow byte array shims
- **Optimized Memory Behavior**: Reduces garbage collection overhead
- **JWK Compatibility**: Returns keys in JSON Web Key format

## Installation

Install via npm:

```bash
npm install deterministic-rsa-js
```

### Prerequisites

- Node.js v14.0.0 or higher (with native BigInt support)
- Recommended: Node.js v16+ for best performance

## API Reference

### Key Generation Function

```javascript
async function rsaGenKeys(
  bits: number, 
  seed: Uint8Array, 
  e?: BigInt = 65537n
): Promise<{
  privateKey: JsonWebKey, 
  publicKey: JsonWebKey
}>
```

#### Parameters
- `bits`: Number of bits for RSA modulus (must be multiple of 32, minimum 192)
- `seed`: 32-byte Uint8Array for seeding prime generation
- `e` (optional): Public encryption exponent, defaults to 65537

#### Returns
An object containing:
- `privateKey`: Complete RSA private key in JWK format
- `publicKey`: RSA public key in JWK format

#### Example Usage

```javascript
const { rsaGenKeys } = require('deterministic-rsa-js');

async function generateKeys() {
  const seed = crypto.randomBytes(32);
  const { privateKey, publicKey } = await rsaGenKeys(2048, seed);
  console.log(privateKey, publicKey);
}
```

## Repository Structure

- `index.js`: Main library implementation
- `test.js`: Library test suite
- `package.json`: Project metadata and dependencies
- `LICENSE`: MIT license file

## Contributing

Contributions are welcome! Please follow these steps:

1. Fork the repository
2. Create a new branch for your feature
3. Implement your changes
4. Write or update tests
5. Run tests with `node test`
6. Submit a pull request

### Current TODO Items

- Add optimized prime checking implementation
- Integrate native Node.js crypto module for prime checking
- Explore alternative Pseudo-Random Number Generation (PRNG) methods

## Performance Optimization Techniques

- Native BigInt usage
- Multithreaded prime generation
- Efficient random number generation
- Preallocated buffers
- Minimized type coercion

## License

This project is licensed under the MIT License. See the `LICENSE` file for details.