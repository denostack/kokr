# @kokr/date <a href="https://github.com/denostack"><img src="https://raw.githubusercontent.com/denostack/images/main/logo.svg" width="160" align="right" /></a>

<p>
  <a href="https://github.com/denostack/kokr/actions"><img alt="Build" src="https://img.shields.io/github/actions/workflow/status/denostack/kokr/ci.yml?branch=main&logo=github&style=flat-square" /></a>
  <a href="https://codecov.io/gh/denostack/kokr"><img alt="Coverage" src="https://img.shields.io/codecov/c/gh/denostack/kokr?style=flat-square" /></a>
  <img alt="License" src="https://img.shields.io/npm/l/@kokr/date.svg?style=flat-square" />
  <img alt="Language Typescript" src="https://img.shields.io/badge/language-Typescript-007acc.svg?style=flat-square" />
  <br />
  <a href="https://jsr.io/@denostack/kokr"><img alt="JSR version" src="https://jsr.io/badges/@denostack/kokr?style=flat-square" /></a>
  <a href="https://www.npmjs.com/package/@kokr/date"><img alt="Version" src="https://img.shields.io/npm/v/@kokr/date.svg?style=flat-square&logo=npm" /></a>
  <a href="https://npmcharts.com/compare/@kokr/date?minimal=true"><img alt="Downloads" src="https://img.shields.io/npm/dt/@kokr/date.svg?style=flat-square" /></a>
</p>

[한국어](https://github.com/denostack/kokr/blob/main/date/README.md) | **English**

Provides Korean public holidays, anniversaries, the 24 solar terms, and seasonal days. Holiday data is fetched from an
external API, so it stays up to date without library updates. It also caches results daily via the Web Storage API (with
[shim-webstore](https://github.com/denostack/node-shim-webstore) on Node.js), making repeated lookups very fast.

@kokr/date uses holiday data from [distbe/holidays](https://github.com/distbe/holidays), which in turn is based on the
holiday data from the Korean public data portal.

## Install

```bash
# Deno
deno add jsr:@denostack/kokr

# Node.js / Bun
npm install @kokr/date
```

```ts
// Deno
import { getHolidays } from "@denostack/kokr/date";

// Node.js / Bun
import { getHolidays } from "@kokr/date";
```

## Usage

**Get holidays**

Given a year, returns all holidays, anniversaries, solar terms, and seasonal days for that year. See the data structure
section above for details.

```typescript
import { getHolidays } from "@kokr/date";

const dates = await getHolidays(2022);
```

**Business day calculation**

Calculates business days, excluding holidays (Saturdays, Sundays, and public holidays).

```typescript
import { getNextBusinessDay } from "@kokr/date";

const date = await getNextBusinessDay("2022-01-01", 10);
```

**Holiday check**

Returns `true` when the given date is a holiday (Saturday, Sunday, or a public holiday).

```typescript
import { isHoliday } from "@kokr/date";

const holiday = await isHoliday("2022-01-01"); // true
```

## Data structure

**DateInfo**

| Property | Type               | Description                                                             |
| -------- | ------------------ | ----------------------------------------------------------------------- |
| date     | `string`           | Date of the holiday (YYYY-MM-DD)                                        |
| name     | `string`           | Name of the holiday                                                     |
| holiday  | `boolean`          | Whether the date is a public holiday                                    |
| remarks  | `string` \| `null` | Extra description provided by the API, when available                   |
| kind     | `DateKind`         | Whether it is a holiday, anniversary, or solar term - see the enum      |
| time     | `string` \| `null` | Exact standard time (HH:mm), returned for `DateKind.SolarTerms`         |
| sunLng   | `number` \| `null` | Ecliptic longitude of the sun (deg), returned for `DateKind.SolarTerms` |

**DateKind**

| Value         | Description    | Examples                                           |
| ------------- | -------------- | -------------------------------------------------- |
| `Holiday`     | Public holiday | Seollal, election days, Chuseok (substitute), etc. |
| `Anniversary` | Anniversary    | Teachers' Day, Armed Forces Day, etc.              |
| `SolarTerms`  | 24 solar terms | Ipchun, Gyeongchip, etc.                           |
| `Sundry`      | Seasonal days  | Jeongwol Daeboreum, Chobok, Jungbok, etc.          |

## API

[View API documentation](https://jsr.io/@denostack/kokr/doc)
