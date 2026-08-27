# @kokr/id <a href="https://github.com/denostack"><img src="https://raw.githubusercontent.com/denostack/images/main/logo.svg" width="160" align="right" /></a>

<p>
  <a href="https://github.com/denostack/kokr/actions"><img alt="Build" src="https://img.shields.io/github/actions/workflow/status/denostack/kokr/ci.yml?branch=main&logo=github&style=flat-square" /></a>
  <a href="https://codecov.io/gh/denostack/kokr"><img alt="Coverage" src="https://img.shields.io/codecov/c/gh/denostack/kokr?style=flat-square" /></a>
  <img alt="License" src="https://img.shields.io/npm/l/@kokr/id.svg?style=flat-square" />
  <img alt="Language Typescript" src="https://img.shields.io/badge/language-Typescript-007acc.svg?style=flat-square" />
  <br />
  <a href="https://jsr.io/@denostack/kokr"><img alt="JSR version" src="https://jsr.io/badges/@denostack/kokr?style=flat-square" /></a>
  <a href="https://www.npmjs.com/package/@kokr/id"><img alt="Version" src="https://img.shields.io/npm/v/@kokr/id.svg?style=flat-square&logo=npm" /></a>
  <a href="https://npmcharts.com/compare/@kokr/id?minimal=true"><img alt="Downloads" src="https://img.shields.io/npm/dt/@kokr/id.svg?style=flat-square" /></a>
</p>

[한국어](https://github.com/denostack/kokr/blob/main/id/README.md) | **English**

Provides utilities for Korean resident registration numbers (RRN).

## Install

```bash
# Deno
deno add jsr:@denostack/kokr

# Node.js / Bun
npm install @kokr/id
```

```ts
// Deno
import { analyze } from "@denostack/kokr/id";

// Node.js / Bun
import { analyze } from "@kokr/id";
```

## Usage

> The registration numbers used in tests were created by entering arbitrary digits and computing the check code - they
> do not belong to real people.

**Analyze a resident/foreigner registration number**

Analyzes a resident or foreigner registration number to determine its validity, gender, foreigner status, birth date,
and age. All non-digit characters are stripped before analysis, so it works with or without hyphens ('-').

```typescript
import { analyze } from "@kokr/id";

analyze("000101-1000002");
/*
{
  valid: true, // whether the number is valid
  parity: 2, // the check digit at the end
  gender: 'M', // gender
  foreigner: false, // whether it is a foreigner registration number
  birth: '1900-01-01', // birth date (null for non-existent dates like 2003-02-29)
  age: 121, // international age
  krAge: 122, // Korean age
}
*/
```

Ages are calculated based on today's date. To calculate against a different date, use the `now` option.

```typescript
analyze("000101-1000002", { now: "2021-06-01" });
```

**Validate a registration number**

Validates a resident or foreigner registration number and returns a `boolean`. To validate only resident registration
numbers (excluding foreigner registration numbers), use the `disableForeigner` option.

```typescript
import { validate } from "@kokr/id";

validate("010101-0010101");

// resident registration numbers only (foreigner numbers rejected)
validate("010101-5010105", { disableForeigner: true }); // false
```

**Format a registration number**

Formats a resident or foreigner registration number as a `string`. All non-digit characters are removed and a hyphen
('-') is inserted.

```typescript
import { format } from "@kokr/id";

format("0101010010101"); // 010101-0010101
```

Invalid numbers are not formatted by default - `null` is returned instead.

```typescript
format("01234"); // null
```

To format numbers with a different length or invalid values anyway, use the `ignoreInvalid` option.

```typescript
format("010101", { ignoreInvalid: true }); // 010101
format("0101010", { ignoreInvalid: true }); // 010101-0
format("01010100101019", { ignoreInvalid: true }); // 010101-00101019
```

## Data structure

**AnalyzeResult**

| Property    | Type                     | Description                                      |
| ----------- | ------------------------ | ------------------------------------------------ |
| `valid`     | `boolean`                | Whether the given number is valid                |
| `parity`    | `number` \| `null`       | Parity (check) digit; `null` for invalid numbers |
| `gender`    | `"M"` \| `"F"` \| `null` | Gender - M for male, F for female                |
| `foreigner` | `boolean` \| `null`      | Whether it is a foreigner registration number    |
| `birth`     | `string` \| `null`       | Birth date                                       |
| `age`       | `number` \| `null`       | International age                                |
| `krAge`     | `number` \| `null`       | Korean age                                       |

## API

[View API documentation](https://jsr.io/@denostack/kokr/doc)
