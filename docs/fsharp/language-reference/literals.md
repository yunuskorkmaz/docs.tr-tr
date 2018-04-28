---
title: Değişmez Değerler (F#)
description: 'F # programlama dili değişmez değer türleri hakkında bilgi edinin.'
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: dotnet-fsharp
ms.devlang: fsharp
ms.openlocfilehash: 961d6a10122c5d5c691d394efa8d2b7b31a80453
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2018
---
# <a name="literals"></a>Sabit değerler

> [!NOTE]
Bu makalede API başvuru bağlantılar (şimdilik) için MSDN sürer.

Bu konu, bir hazır değer türü F #'ta belirtme gösteren bir tablo sağlar.

## <a name="literal-types"></a>Değişmez değer türleri
Değişmez değer türleri aşağıdaki tabloda F #'de gösterilmektedir. Onaltılık gösterimde basamağı temsil karakterleri büyük küçük harfe duyarlı değildir; tür belirleme karakterleri büyük/küçük harfe duyarlıdır.

|Tür|Açıklama|Sonek veya öneki|Örnekler|
|----|-----------|----------------|--------|
|sbyte|İşaretli 8 bit tam sayı|y|`86y`<br /><br />`0b00000101y`|
|byte|İmzasız 8 bit doğal sayı|Uy|`86uy`<br /><br />`0b00000101uy`|
|Int16|İşaretli 16 bit tam sayı|s|`86s`|
|uint16|İmzasız 16 bit doğal sayı|Bize|`86us`|
|int<br /><br />Int32|işaretli 32 bit tam sayı|m veya hiçbiri|`86`<br /><br />`86l`|
|uint<br /><br />uint32|İmzasız 32-bit doğal sayı|u veya ul|`86u`<br /><br />`86ul`|
|unativeint|işaretsiz doğal sayı olarak yerel işaretçiden|kaldırma|`0x00002D3Fun`|
|Int64|işaretli 64 bit tam sayı|L|`86L`|
|uint64|İmzasız 64-bit doğal sayı|UL|`86UL`|
|tek float32|32 bit kayan nokta sayısı|F veya f|`4.14F` Veya `4.14f`|
|||LF|`0x00000000lf`|
|float; çift|64-bit kayan nokta sayısı|yok|`4.14` veya `2.3E+32` veya `2.3e+32`|
|||LF|`0x0000000000000000LF`|
|bigint|64-bit gösterimine bunlarla sınırlı olmamak tamsayı|I|`9999999999999999999999999999I`|
|decimal|bir sabit bir nokta ya da rasyonel sayı olarak temsil kesirli numarası|M veya m|`0.7833M` Veya `0.7833m`|
|Char|Unicode karakter|yok|`'a'`|
|Dize|UNICODE dizesi|yok|`"text\n"`<br /><br />veya<br /><br />`@"c:\filename"`<br /><br />veya<br /><br />`"""<book title="Paradise Lost">"""`<br /><br />veya<br /><br />`"string1" + "string2"`<br /><br />Ayrıca bkz. [dizeleri](Strings.md).|
|byte|ASCII karakter|B|`'a'B`|
|Byte]|ASCII dizesi|B|`"text"B`|
|String veya byte]|harfi harfine dize|@ öneki|`@"\\server\share"` (Unicode)<br /><br />`@"\\server\share"B` (ASCII)|

## <a name="remarks"></a>Açıklamalar
Unicode dizelerini kullanarak belirtebilirsiniz açık Kodlamalar içerebilir `\u` bir 16 bit onaltılık kodu veya kullanarak belirtebilirsiniz UTF-32 kodlamaları arkasından `\U` bir Unicode temsil eden bir 32 bit onaltılık kodla ve ardından yedek çifti.

F # 3.1 itibariyle, kullandığınız `+` dize değişmez değerleri birleştirmek oturum açın. Bit düzeyinde kullanabilirsiniz veya (`|||`) enum bayrakları birleştirmek için işleci. Örneğin, aşağıdaki kodu F # 3.1 uygundur:

```fsharp
[<Literal>]
let Literal1 = "a" + "b"

[<Literal>]
let FileLocation =   __SOURCE_DIRECTORY__ + "/" + __SOURCE_FILE__

[<Literal>]
let Literal2 = 1 ||| 64

[<Literal>]
let Literal3 = System.IO.FileAccess.Read ||| System.IO.FileAccess.Write
```

Diğer bit düzeyinde işleçler kullanılmasına izin verilmiyor.


## <a name="named-literals"></a>Adlandırılmış değişmez değerleri
Sabitler yönelik değerleri işaretlenir ile [değişmez değer](https://msdn.microsoft.com/library/465f36ce-d146-41c0-b425-679c509cd285) özniteliği. Bu öznitelik, bir sabit değer olarak derlenmesi için bir değer neden etkisi vardır.

Eşleşen düzeninde küçük harf karakterler ile başlayan tanımlayıcıları her zaman bağlı olmasını değişkenleri olarak davranılır yerine değişmez değerler tanımlarken değişmez değerler, bu nedenle genellikle ilk harfler büyük harf kullanmanız gerekir.

## <a name="integers-in-other-bases"></a>Diğer tabanları tamsayılar

İmzalı 32-bit tamsayı de belirtilebilir onaltılı, sekizli veya ikili kullanarak bir `0x`, `0o` veya `0b` sırasıyla önek.

```fsharp
let Numbers = (0x9F, 0o77, 0b1010)
// Result: Numbers : int * int * int = (159, 63, 10)
```

## <a name="underscores-in-numeric-literals"></a>Sayısal değişmez değerlerinde alt çizgiler

F # 4.1 ile başlayarak, basamak alt çizgi karakteriyle ayırabilirsiniz (`_`).

```fsharp
let DeadBeef = 0xDEAD_BEEF

let DeadBeefAsBits = 0b1101_1110_1010_1101_1011_1110_1110_1111

let ExampleSSN = 123_456_7890
```

## <a name="see-also"></a>Ayrıca Bkz.

[Core.LiteralAttribute sınıfı](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.literalattribute-class-%5bfsharp%5d)
