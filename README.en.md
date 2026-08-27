# kokr <a href="https://github.com/denostack"><img src="https://raw.githubusercontent.com/denostack/images/main/logo.svg" width="160" align="right" /></a>

<p>
  <a href="https://github.com/denostack/kokr/actions"><img alt="Build" src="https://img.shields.io/github/actions/workflow/status/denostack/kokr/ci.yml?branch=main&logo=github&style=flat-square" /></a>
  <a href="https://codecov.io/gh/denostack/kokr"><img alt="Coverage" src="https://img.shields.io/codecov/c/gh/denostack/kokr?style=flat-square" /></a>
  <img alt="License" src="https://img.shields.io/github/license/denostack/kokr?style=flat-square" />
  <img alt="Language Typescript" src="https://img.shields.io/badge/language-Typescript-007acc.svg?style=flat-square" />
  <br />
  <a href="https://jsr.io/@denostack/kokr"><img alt="JSR version" src="https://jsr.io/badges/@denostack/kokr?style=flat-square" /></a>
</p>

[한국어](https://github.com/denostack/kokr/blob/main/README.md) | **English**

kokr is a collection of utilities for the Korean language (ko) and Korea (KR), written in TypeScript. It is available on
both Deno (JSR) and Node.js (NPM).

## Packages

The currently available packages are listed below. More features will be added as needed.

- [@kokr/date](./date): Provides utilities for Korean dates - holidays, solar terms, and seasonal days, with
  business-day calculations.
- [@kokr/id](./id): Provides tools to analyze Korean resident registration numbers - extract birth date and gender, and
  validate the number.
- [@kokr/phone](./phone): Provides a phone number formatting tool that converts phone numbers into a consistent format.
- [@kokr/text](./text): A utility that handles Korean postpositions (josa) such as 은/는/이/가 automatically.

## Install

```bash
# Deno
deno add jsr:@denostack/kokr

# Node.js / Bun - one package per module
npm install @kokr/text
```

```ts
// Deno
import { text } from "@denostack/kokr/text";

// Node.js / Bun
import { text } from "@kokr/text";
```

## Documentation

The code makes extensive use of jsdoc, so full API documentation is available on the JSR page. See each package's README
for detailed usage and examples.

[View all documentation](https://jsr.io/@denostack/kokr/doc)

## Contributing

Contributions are welcome! Feel free to open an issue or send a pull request for new features and bug fixes. Improving
documentation and adding test cases are also great ways to contribute.
