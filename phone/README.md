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

**한국어** | [English](https://github.com/denostack/kokr/blob/main/phone/README.en.md)

전화번호와 관련된 유틸리티 함수를 제공합니다.

## 설치

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

## 사용법

**전화번호 포매팅**

전화번호를 포매팅합니다.

```typescript
import { format } from "@kokr/phone";

format("0212341234"); // '02-1234-1234'
format("021231234"); // '02-123-1234'
format("16881234"); // '1688-1234'
```

특수문자(`#`, `*`)를 포함한 포매팅도 가능합니다.

```typescript
format("02****####"); // '02-****-####'
```

## API

[API 문서 보기](https://jsr.io/@denostack/kokr/doc)
