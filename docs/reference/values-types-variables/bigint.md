---
sidebar_label: bigint型
title: bigint型(長整数型)
---

JavaScriptのbigint型は、number型よりも大きな整数を扱えるプリミティブ型です。

## bigint型リテラル

JavaScriptのbigint型のリテラルは整数値の末尾に`n`をつけて書きます。

```ts twoslash
const x = 100n;
```

bigintリテラルをTypeScriptで用いるには、コンパイラーオプションのtargetをes2020以上にする必要があります。

## bigint型の型注釈

TypeScriptでbigint型を型注釈するには、`bigint`を用います。

```ts twoslash
const x: bigint = 100n;
```

## BigInt関数

bigint型はBigInt関数を使って作ることができます。BigInt関数は第1引数に数値もしくは文字列を渡します。

```ts twoslash
const x = BigInt(100);
const y = BigInt("9007199254740991");
```

TypeScriptでBigInt関数を用いるには、コンパイラーオプションのlibをes2020以上にする必要があります。

## bigint型をnumber型と計算する

bigint型とnumber型はそのままでは一緒に演算をすることはできません。どちらかに型を合わせる必要があります。

```ts twoslash
// @errors: 2365
2n + 3;
```

number型が小数部を持っていない限り、より表現幅の広いbigint型に合わせる方が無難です。

```ts twoslash
const i = 2n + BigInt(3);
console.log(i);
// @log: 5n
```

## bigint型を使う上での注意点

bigint型を直接`JSON.stringify()`に渡すと、TypeErrorが発生します。

```ts twoslash
JSON.stringify(12n);
// @error: TypeError: Do not know how to serialize a BigInt
```

また、bigint型を含むオブジェクトを`JSON.stringify()`に渡しても、TypeErrorが発生します。

```ts twoslash
JSON.stringify({ x: 12n });
// @error: TypeError: Do not know how to serialize a BigInt
```
