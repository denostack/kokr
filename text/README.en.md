# @kokr/text <a href="https://github.com/denostack"><img src="https://raw.githubusercontent.com/denostack/images/main/logo.svg" width="160" align="right" /></a>

<p>
  <a href="https://github.com/denostack/kokr/actions"><img alt="Build" src="https://img.shields.io/github/actions/workflow/status/denostack/kokr/ci.yml?branch=main&logo=github&style=flat-square" /></a>
  <a href="https://codecov.io/gh/denostack/kokr"><img alt="Coverage" src="https://img.shields.io/codecov/c/gh/denostack/kokr?style=flat-square" /></a>
  <img alt="License" src="https://img.shields.io/npm/l/@kokr/text.svg?style=flat-square" />
  <img alt="Language Typescript" src="https://img.shields.io/badge/language-Typescript-007acc.svg?style=flat-square" />
  <br />
  <a href="https://jsr.io/@denostack/kokr"><img alt="JSR version" src="https://jsr.io/badges/@denostack/kokr?style=flat-square" /></a>
  <a href="https://www.npmjs.com/package/@kokr/text"><img alt="Version" src="https://img.shields.io/npm/v/@kokr/text.svg?style=flat-square&logo=npm" /></a>
  <a href="https://npmcharts.com/compare/@kokr/text?minimal=true"><img alt="Downloads" src="https://img.shields.io/npm/dt/@kokr/text.svg?style=flat-square" /></a>
</p>

[한국어](https://github.com/denostack/kokr/blob/main/text/README.md) | **English**

A utility that helps handle postpositions (josa) in Korean sentences, such as 은/는/이/가.

## Install

```bash
# Deno
deno add jsr:@denostack/kokr

# Node.js / Bun
npm install @kokr/text
```

```ts
// Deno
import { text } from "@denostack/kokr/text";

// Node.js / Bun
import { text } from "@kokr/text";
```

## Usage

### Postpositions (josa)

Automatically attaches the correct postposition (such as 은/는 or 이/가) via a template literal.

```typescript
import { text } from "@kokr/text";

let name1 = "사과";
let name2 = "코코넛";

// 은/는
console.log(text`${name1}는 코딩 합니다.`); // 사과는 코딩 합니다.
console.log(text`${name2}는 코딩 합니다.`); // 코코넛은 코딩 합니다.

// 이/가
console.log(text`${name1}가 코딩 했습니다.`); // 사과가 코딩 했습니다.
console.log(text`${name2}가 코딩 했습니다.`); // 코코넛이 코딩 했습니다.

// 을/를
console.log(text`${name1}을 가르쳤습니다.`); // 사과를 가르쳤습니다.
console.log(text`${name2}를 가르쳤습니다.`); // 코코넛을 가르쳤습니다.

// 로/으로 (with the ㄹ-final exception, e.g. 서울로)
console.log(text`${"대구"}으로 갑시다.`); // 대구로 갑시다.
console.log(text`${"부산"}로 갑시다.`); // 부산으로 갑시다.
console.log(text`${"서울"}으로 갑시다.`); // 서울로 갑시다.
```

Supported postpositions:

- 은/는
- 이/가
- 을/를
- 과/와
- 아/야 (ambiguous case, see below)
- 이나/나
- 이다/다
- 이든/든
- 이라/라
- 이란/란
- 이랑/랑
- 으로/로
- 이며/며
- 이셨/셨
- 이시/시
- 이야/야 (ambiguous case, see below)
- 이여/여
- 이었/였
- 이어요/여요
- 이에요/예요

**Ambiguous cases**

"아/야" and "이야/야" can be ambiguous. When a phrase ends with "야", the "이야/야" rule takes precedence. Use "이야" or
"아" explicitly for unambiguous results.

```typescript
// unambiguous
console.log(text`${"완두"}아!`); // "완두야!"
console.log(text`${"완삼"}아!`); // "완삼아!"

console.log(text`${"완두"}이야!`); // "완두야!"
console.log(text`${"완삼"}이야!`); // "완삼이야!"

// ambiguous
console.log(text`${"완두"}야!`); // "완두야!"
console.log(text`${"완삼"}야!`); // "완삼이야!" // "완삼아!" was intended, but the "이야/야" rule wins.
```

### Numbers and English words

Numbers are handled based on their Korean pronunciation.

```typescript
console.log(text`정답은 ${"100"}와 같다.`); // 정답은 100과 같다.
console.log(text`정답은 ${"72"}과 같다.`); // 정답은 72와 같다.
```

English words are also handled based on their Korean pronunciation.

```typescript
console.log(text`${"Apple"}는 코딩 합니다.`); // Apple은 코딩 합니다.
console.log(text`${"Banana"}은 코딩 합니다.`); // Banana는 코딩 합니다.
```

### Ignoring parentheses

When the value contains parentheses, the text inside them is ignored.

```typescript
console.log(text`${"코코넛(바나나)"}는 코딩 합니다.`); // 코코넛(바나나)은 코딩 합니다.
```

### Dedent

Removes leading indentation from multi-line strings.

```typescript
function printResult(winner: string, loser: string) {
  return text`
    결과는 다음과 같습니다.

    - 승: ${winner}
    - 패: ${loser}

    ${winner}님 축하드립니다!
  `;
}
```

### Bypassing postposition conversion

To output a postposition as-is without conversion:

```typescript
console.log(text`${name}는 가나다라..`); // '는' is converted by the 은/는 rule.

console.log(text`${name}{'는'} 가나다라..`); // '는' is printed as-is without conversion.
```

## API

[View API documentation](https://jsr.io/@denostack/kokr/doc)

## See also

- [Hangul.js](https://github.com/e-/Hangul.js) - a library that decomposes Korean sentences into consonants and vowels
- [inko](https://github.com/738/inko) - a library that converts English keystrokes to Korean and vice versa
- [josa-complete](https://github.com/rycont/josa-complete) - a library that extends String.prototype to attach
  postpositions cleanly
