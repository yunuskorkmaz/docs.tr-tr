---
title: Sabit değerler
description: F# Programlama dilindeki değişmez türler hakkında bilgi edinin.
ms.date: 06/28/2019
ms.openlocfilehash: 9792a24ac28eb402e35e78574cd6a2bf9526734d
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/29/2019
ms.locfileid: "73041039"
---
# <a name="literals"></a>Sabit değerler

> [!NOTE]
> Bu makaledeki API başvuru bağlantıları sizi MSDN 'ye götürecektir (şimdilik).

Bu konu, içinde F#bir sabit değerin türünü nasıl belirtmeyle ilgili bir tablo sağlar.

## <a name="literal-types"></a>Değişmez değer türleri

Aşağıdaki tabloda, içindeki F#değişmez türler gösterilmektedir. Onaltılı gösterimdeki basamakları temsil eden karakterler büyük/küçük harfe duyarlı değildir; türü tanımlayan karakterler büyük/küçük harfe duyarlıdır.

|Tür|Açıklama|Sonek veya ön ek|Örnekler|
|----|-----------|----------------|--------|
|sbyte|İmzalanan 8 bit tamsayı|y|`86y`<br /><br />`0b00000101y`|
|byte|işaretsiz 8 bit doğal sayı|uy|`86uy`<br /><br />`0b00000101uy`|
|Int16|İmzalanan 16 bit tamsayı|s|`86s`|
|Int16|işaretsiz 16 bit doğal numara|ABD|`86us`|
|int<br /><br />Int32|İmzalanan 32 bit tamsayı|l veya hiçbiri|`86`<br /><br />`86l`|
|uint<br /><br />Int32|işaretsiz 32 bit doğal numara|u veya UL|`86u`<br /><br />`86ul`|
|nativeint|doğal olarak imzalanan bir sayının yerel işaretçisi|n|`123n`|
|unativeint|işaretsiz doğal sayı olarak yerel işaretçi|alma|`0x00002D3Fun`|
|Tutulamaz|İmzalanan 64 bit tamsayı|L|`86L`|
|Int64|işaretsiz 64 bit doğal numara|UL|`86UL`|
|Single, float32|32-bit kayan noktalı sayı|F veya f|`4.14F` veya `4.14f`|
|||LF|`0x00000000lf`|
|float Çift|64-bit kayan noktalı sayı|yok|`4.14` veya `2.3E+32` veya `2.3e+32`|
|||LF|`0x0000000000000000LF`|
|bigint|tamsayı, 64 bitlik gösterimiyle sınırlı değildir|I|`9999999999999999999999999999I`|
|decimal|sabit bir nokta veya Rational numarası olarak temsil edilen kesirli sayı|A veya d|`0.7833M` veya `0.7833m`|
|Char|Unicode karakter|yok|`'a'` veya `'\u0061'`|
|Dize|Unicode dizesi|yok|`"text\n"`<br /><br />veya<br /><br />`@"c:\filename"`<br /><br />veya<br /><br />`"""<book title="Paradise Lost">"""`<br /><br />veya<br /><br />`"string1" + "string2"`<br /><br />Ayrıca bkz. [dizeler](Strings.md).|
|byte|ASCII karakteri|B|`'a'B`|
|Byte []|ASCII dizesi|B|`"text"B`|
|Dize veya Byte []|Tam dize|@ ön eki|`@"\\server\share"` (Unicode)<br /><br />`@"\\server\share"B` (ASCII)|

## <a name="named-literals"></a>Adlandırılmış sabit değerler

Sabitler olması amaçlanan değerler [değişmez değer](https://msdn.microsoft.com/library/465f36ce-d146-41c0-b425-679c509cd285) özniteliğiyle işaretlenebilir. Bu öznitelik, bir değerin bir sabit olarak derlenmesine neden olan etkiye sahiptir.

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

Unicode dizeleri, `\u` ve ardından bir 16 bit onaltılı kod (0000-FFFF) veya UTF-32 kodlamalarının ardından, herhangi bir Unicode 'U temsil eden 32 bitlik bir onaltılık kod tarafından ve `\U` kullanarak belirtebileceğiniz açık kodlamalar içerebilir kod noktası (00000000-0010FFFF).

`|||` dışındaki diğer bit düzeyinde işleçlerin kullanımına izin verilmez.

## <a name="integers-in-other-bases"></a>Diğer tabandaki tamsayılar

İmzalı 32 bitlik tamsayılar, sırasıyla `0x``0o` veya `0b` ön eki kullanılarak onaltılık, sekizlik veya ikili düzende de belirtilebilir.

```fsharp
let numbers = (0x9F, 0o77, 0b1010)
// Result: numbers : int * int * int = (159, 63, 10)
```

## <a name="underscores-in-numeric-literals"></a>Sayısal sabit değerlerde alt çizgiler

Rakamları alt çizgi karakteri (`_`) ile ayırabilirsiniz.

```fsharp
let value = 0xDEAD_BEEF

let valueAsBits = 0b1101_1110_1010_1101_1011_1110_1110_1111

let exampleSSN = 123_456_7890
```

## <a name="see-also"></a>Ayrıca bkz.

- [Core. LiteralAttribute sınıfı](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.literalattribute-class-%5bfsharp%5d)
