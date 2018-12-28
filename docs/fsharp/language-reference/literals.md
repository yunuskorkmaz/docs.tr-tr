---
title: Sabit değerler
description: Değişmez değer türleri hakkında bilgi edinin F# programlama dilidir.
ms.date: 05/16/2016
ms.openlocfilehash: dfc02f0ff8ac3ad8600be5f3b6c9359f02bd25be
ms.sourcegitcommit: fa38fe76abdc8972e37138fcb4dfdb3502ac5394
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/19/2018
ms.locfileid: "53612458"
---
# <a name="literals"></a>Sabit değerler

> [!NOTE]
> Bu makaledeki API başvuru bağlantıları için MSDN (şimdilik) sürer.

Bu konu, bir sabit listesinde değişmez değerin türünü gösteren bir tablo sağlar F#.

## <a name="literal-types"></a>Değişmez değer türleri

Aşağıdaki tabloda, değişmez değer türleri gösterilmektedir F#. Onaltılık gösterimdeki basamakları temsil eden karakterler büyük küçük harfe duyarlı değildir; türü tanımlayan karakterler büyük/küçük harfe duyarlıdır.

|Tür|Açıklama|Sonek veya önek|Örnekler|
|----|-----------|----------------|--------|
|sbyte|İşaretli 8 bit tam sayı|y|`86y`<br /><br />`0b00000101y`|
|byte|imzalanmamış 8 bit doğal sayı|Uy|`86uy`<br /><br />`0b00000101uy`|
|Int16|İşaretli 16 bit tam sayı|s|`86s`|
|uint16|İmzasız 16-bit doğal sayı|ABD|`86us`|
|int<br /><br />Int32|İşaretli 32 bit tam sayı|l ya da yok|`86`<br /><br />`86l`|
|uint<br /><br />uint32|işaretsiz 32-bit doğal sayı|u veya ul|`86u`<br /><br />`86ul`|
|unativeint|işeritsiz doğal sayı olarak yerel işaretçi|Geri Al|`0x00002D3Fun`|
|Int64|İşaretli 64 bit tam sayı|L|`86L`|
|uint64|işaretsiz 64-bit doğal sayı|UL|`86UL`|
|tek, float32|32 bit kayan nokta sayısı|F veya f|`4.14F` veya `4.14f`|
|||LF|`0x00000000lf`|
|kayan nokta; çift|64-bit kayan nokta sayısı|yok|`4.14` veya `2.3E+32` veya `2.3e+32`|
|||LF|`0x0000000000000000LF`|
|bigint|64 bit gösterimle sınırlı olmayan tamsayı|I|`9999999999999999999999999999I`|
|decimal|Sabit nokta veya rasyonel sayı olarak temsil edilen kesirli sayı|M veya m|`0.7833M` veya `0.7833m`|
|Char|Unicode karakter|yok|`'a'`|
|Dize|Unicode dizesi|yok|`"text\n"`<br /><br />veya<br /><br />`@"c:\filename"`<br /><br />veya<br /><br />`"""<book title="Paradise Lost">"""`<br /><br />veya<br /><br />`"string1" + "string2"`<br /><br />Ayrıca bkz: [dizeleri](Strings.md).|
|byte|ASCII karakteri|B|`'a'B`|
|bayt]|ASCII dizesi|B|`"text"B`|
|Dize veya bayt]|Verbatim dizesi|@ ön ek|`@"\\server\share"` (Unicode)<br /><br />`@"\\server\share"B` (ASCII)|

## <a name="remarks"></a>Açıklamalar

Unicode dizelerini kullanarak belirttiğiniz açık Kodlamalar içerebilir `\u` bir 16 bitlik onaltılık kod ya da kullanarak belirtebilirsiniz UTF-32 kodlamalarına ardından `\U` bir Unicode temsil eden bir 32 bit onaltılık kodla ve ardından vekil çifti.

Sürümünden itibaren F# kullanabileceğiniz 3.1, `+` dize değişmez değerlerini birleştirmek için oturum açın. Bit düzeyinde kullanabilirsiniz veya (`|||`) numaralandırma bayraklarını birleştirmek istiyorsanız işleci. Örneğin, aşağıdaki yasal kodudur F# 3.1:

```fsharp
[<Literal>]
let literal1 = "a" + "b"

[<Literal>]
let fileLocation =   __SOURCE_DIRECTORY__ + "/" + __SOURCE_FILE__

[<Literal>]
let literal2 = 1 ||| 64

[<Literal>]
let literal3 = System.IO.FileAccess.Read ||| System.IO.FileAccess.Write
```

Bit düzeyindeki diğer işleçlerin kullanımına izin verilmiyor.

## <a name="named-literals"></a>Adlandırılmış değişmez değerler

Sabit olması amaçlanır değerler ile işaretlenebilir [değişmez değer](https://msdn.microsoft.com/library/465f36ce-d146-41c0-b425-679c509cd285) özniteliği. Bu öznitelik değeri bir sabit olarak derlenmesine neden etkisi vardır.

Eşleştirme ifadesi deseninde, küçük harfle başlayan tanımlayıcılar her zaman bağlı değişkenleri olarak kabul edilir yerine sabit değerleri tanımlarken değişmez değer olarak, bu nedenle genellikle ilk harfleri büyük kullanmanız gerekir.

## <a name="integers-in-other-bases"></a>Diğer Tabanlara tamsayılar

İşaretli 32 bit tam sayılar da belirtilebilir onaltılık, sekizlik veya ikili kullanarak bir `0x`, `0o` veya `0b` sırasıyla önek.

```fsharp
let Numbers = (0x9F, 0o77, 0b1010)
// Result: Numbers : int * int * int = (159, 63, 10)
```

## <a name="underscores-in-numeric-literals"></a>Sayısal sabit değerlerde alt çizgiler

İle başlayarak F# 4.1, basamak alt çizgi karakteriyle ayırın (`_`).

```fsharp
let value = 0xDEAD_BEEF

let valueAsBits = 0b1101_1110_1010_1101_1011_1110_1110_1111

let exampleSSN = 123_456_7890
```

## <a name="see-also"></a>Ayrıca bkz.

- [Core.LiteralAttribute sınıfı](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.literalattribute-class-%5bfsharp%5d)