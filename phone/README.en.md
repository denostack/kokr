# @kokr/phone <a href="https://github.com/denostack"><img src="https://raw.githubusercontent.com/denostack/images/main/logo.svg" width="160" align="right" /></a>

<p>
  <a href="https://github.com/denostack/kokr/actions"><img alt="Build" src="https://img.shields.io/github/actions/workflow/status/denostack/kokr/ci.yml?branch=main&logo=github&style=flat-square" /></a>
  <a href="https://codecov.io/gh/denostack/kokr"><img alt="Coverage" src="https://img.shields.io/codecov/c/gh/denostack/kokr?style=flat-square" /></a>
  <img alt="License" src="https://img.shields.io/npm/l/@kokr/phone.svg?style=flat-square" />
  <img alt="Language Typescript" src="https://img.shields.io/badge/language-Typescript-007acc.svg?style=flat-square" />
  <br />
  <a href="https://jsr.io/@denostack/kokr"><img alt="JSR version" src="https://jsr.io/badges/@denostack/kokr?style=flat-square" /></a>
  <a href="https://www.npmjs.com/package/@kokr/phone"><img alt="Version" src="https://img.shields.io/npm/v/@kokr/phone.svg?style=flat-square&logo=npm" /></a>
  <a href="https://npmcharts.com/compare/@kokr/phone?minimal=true"><img alt="Downloads" src="https://img.shields.io/npm/dt/@kokr/phone.svg?style=flat-square" /></a>
</p>

[한국어](https://github.com/denostack/kokr/blob/main/phone/README.md) | **English**

Provides utility functions for Korean phone numbers.

## Install

```bash
# Deno
deno add jsr:@denostack/kokr

# Node.js / Bun
npm install @kokr/phone
```

```ts
// Deno
import { format } from "@denostack/kokr/phone";

// Node.js / Bun
import { format } from "@kokr/phone";
```

## Usage

**Format a phone number**

```typescript
import { format } from "@kokr/phone";

format("0212341234"); // '02-1234-1234'
format("021231234"); // '02-123-1234'
format("16881234"); // '1688-1234'
```

Formatting with special characters (`#`, `*`) is also supported.

```typescript
format("02****####"); // '02-****-####'
```

## API

[View API documentation](https://jsr.io/@denostack/kokr/doc)
