---
title: Değişmez Değerler
description: 'F # programlama dilindeki değişmez türler hakkında bilgi edinin.'
ms.date: 08/15/2020
ms.openlocfilehash: 15f73db3c36f7c60ab1eeba96c63a28ebc6d7f01
ms.sourcegitcommit: 8bfeb5930ca48b2ee6053f16082dcaf24d46d221
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/18/2020
ms.locfileid: "88559160"
---
# <a name="literals"></a>Değişmez Değerler

Bu makale, F # içinde bir sabit değerin türünü nasıl belirtmeyle ilgili bir tablo sağlar.

## <a name="literal-types"></a>Değişmez değer türleri

Aşağıdaki tabloda, F # içinde değişmez türler gösterilmektedir. Onaltılı gösterimdeki basamakları temsil eden karakterler büyük/küçük harfe duyarlı değildir; türü tanımlayan karakterler büyük/küçük harfe duyarlıdır.

|Tür|Açıklama|Sonek veya ön ek|Örnekler|
|----|-----------|----------------|--------|
|sbyte|imzalanan 8 bit tamsayı|y|`86y`<br /><br />`0b00000101y`|
|byte|işaretsiz 8 bit doğal sayı|uy|`86uy`<br /><br />`0b00000101uy`|
|Int16|imzalanan 16 bit tamsayı|s|`86s`|
|Int16|işaretsiz 16 bit doğal numara|ABD|`86us`|
|int<br /><br />Int32|imzalanan 32 bit tamsayı|l veya hiçbiri|`86`<br /><br />`86l`|
|uint<br /><br />Int32|işaretsiz 32 bit doğal numara|u veya UL|`86u`<br /><br />`86ul`|
|nativeint|doğal olarak imzalanan bir sayının yerel işaretçisi|n|`123n`|
|unativeint|işaretsiz doğal sayı olarak yerel işaretçi|alma|`0x00002D3Fun`|
|tutulamaz|imzalanan 64 bit tamsayı|L|`86L`|
|Int64|işaretsiz 64 bit doğal numara|UL|`86UL`|
|Single, float32|32-bit kayan noktalı sayı|F veya f|`4.14F` veya `4.14f`|
|||LF|`0x00000000lf`|
|float Çift|64-bit kayan noktalı sayı|yok|`4.14` or `2.3E+32` veya `2.3e+32`|
|||LF|`0x0000000000000000LF`|
|bigint|tamsayı, 64 bitlik gösterimiyle sınırlı değildir|I|`9999999999999999999999999999I`|
|decimal|sabit bir nokta veya Rational numarası olarak temsil edilen kesirli sayı|A veya d|`0.7833M` veya `0.7833m`|
|Char|Unicode karakter|yok|`'a'` veya `'\u0061'`|
|Dize|Unicode dizesi|yok|`"text\n"`<br /><br />veya<br /><br />`@"c:\filename"`<br /><br />veya<br /><br />`"""<book title="Paradise Lost">"""`<br /><br />veya<br /><br />`"string1" + "string2"`<br /><br />Ayrıca bkz. [dizeler](Strings.md).|
|byte|ASCII karakteri|B|`'a'B`|
|Byte []|ASCII dizesi|B|`"text"B`|
|Dize veya Byte []|Tam dize|@ ön eki|`@"\\server\share"` Kodlamaları<br /><br />`@"\\server\share"B` ASCII|

## <a name="named-literals"></a>Adlandırılmış sabit değerler

Sabitler olması amaçlanan değerler [değişmez değer](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-core-literalattribute.html) özniteliğiyle işaretlenebilir. Bu öznitelik, bir değerin bir sabit olarak derlenmesine neden olan etkiye sahiptir.

Desenler eşleşen ifadelerde, küçük harfli karakterlerle başlayan tanımlayıcılar her zaman değişmez değer yerine, her zaman bağlanacak değişkenler olarak değerlendirilir. bu nedenle, sabit değerleri tanımlarken genellikle ilk büyük harfleri kullanmanız gerekir.

```fsharp
[<Literal>]
let SomeJson = """{"numbers":[1,2,3,4,5]}"""

[<Literal>]
let Literal1 = "a" + "b"

[<Literal>]
let FileLocation =   __SOURCE_DIRECTORY__ + "/" + __SOURCE_FILE__

[<Literal>]
let Literal2 = 1 ||| 64

[<Literal>]
let Literal3 = System.IO.FileAccess.Read ||| System.IO.FileAccess.Write
```

## <a name="remarks"></a>Açıklamalar

Unicode dizeleri, ardından, `\u` `\U` herhangi bir Unicode kod noktasını temsil eden 32 bitlik bir onaltılık kod ile bunu kullanarak belirtebileceğiniz bir 16 bit onaltılı kod (0000-ffff) veya UTF-32 kodlamalarının ardından kullanarak belirtebileceğiniz açık kodlamalar içerebilir.

Dışındaki diğer bit düzeyinde işleçlerin kullanımına `|||` izin verilmez.

## <a name="integers-in-other-bases"></a>Diğer tabandaki tamsayılar

İmzalanan 32 bit tamsayılar Ayrıca `0x` , `0o` sırasıyla bir veya öneki kullanılarak onaltılık, sekizlik veya ikili olarak belirtilebilir `0b` .

```fsharp
let numbers = (0x9F, 0o77, 0b1010)
// Result: numbers : int * int * int = (159, 63, 10)
```

## <a name="underscores-in-numeric-literals"></a>Sayısal sabit değerlerde alt çizgiler

Rakamları alt çizgi karakteri () ile ayırabilirsiniz `_` .

```fsharp
let value = 0xDEAD_BEEF

let valueAsBits = 0b1101_1110_1010_1101_1011_1110_1110_1111

let exampleSSN = 123_456_7890
```
