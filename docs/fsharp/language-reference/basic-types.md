---
title: Temel Türler
description: 'F # dilinde kullanılan temel temel türleri bulur.'
ms.date: 08/15/2020
ms.openlocfilehash: 659ac8424c62985affcca1741e1b2a74c9c3ee8d
ms.sourcegitcommit: 8bfeb5930ca48b2ee6053f16082dcaf24d46d221
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/18/2020
ms.locfileid: "88557704"
---
# <a name="basic-types"></a>Temel türler

Bu konu, F # dilinde tanımlanan temel türleri listeler. Bu türler, neredeyse her F # programının temelini oluşturan F # ' da en temel programdır. Bunlar .NET temel türlerinin bir üst kümesidir.

|Tür|.NET türü|Açıklama|Örnek|
|----|---------|-----------|-------|
|`bool`|<xref:System.Boolean>|Olası değerler şunlardır `true` `false` .|`true`/`false`|
|`byte`|<xref:System.Byte>|0 ile 255 arasında değerler.|`1uy`|
|`sbyte`|<xref:System.SByte>|-128 ile 127 arasındaki değerler.|`1y`|
|`int16`|<xref:System.Int16>|-32768 ile 32767 arasındaki değerler.|`1s`|
|`uint16`|<xref:System.UInt16>|0 ile 65535 arasında değerler.|`1us`|
|`int`|<xref:System.Int32>|-2.147.483.648 ile 2.147.483.647 arasındaki değerler.|`1`|
|`uint`|<xref:System.UInt32>|0 ile 4.294.967.295 arasında değerler.|`1u`|
|`int64`|<xref:System.Int64>|-9223372036854775808-9.223.372.036.854.775.807 arası değerler.|`1L`|
|`uint64`|<xref:System.UInt64>|0 ile 18446744073709551615 arasında değerler.|`1UL`|
|`nativeint`|<xref:System.IntPtr>|İşaretli tamsayı olarak yerel bir işaretçi.|`nativeint 1`|
|`unativeint`|<xref:System.UIntPtr>|İşaretsiz tamsayı olarak yerel bir işaretçi.|`unativeint 1`|
|`decimal`|<xref:System.Decimal>|En az 28 önemli basamağa sahip bir kayan nokta veri türü.|`1.0`|
|`float`, `double`|<xref:System.Double>|64 bitlik kayan nokta türü.|`1.0`|
|`float32`, `single`|<xref:System.Single>|32 bitlik kayan nokta türü.|`1.0f`|
|`char`|<xref:System.Char>|Unicode karakter değerleri.|`'c'`|
|`string`|<xref:System.String>|Unicode metin.|`"str"`|
|`unit`|uygulanamaz|Gerçek değerin yokluğunu gösterir. Türün yalnızca bir biçimsel değeri vardır ve bu değer gösterilir `()` . Birim değeri, `()` genellikle bir değerin gerekli olduğu ancak gerçek bir değer kullanılabilir olmayan bir yer tutucu olarak kullanılır veya anlamlı olur.|`()`|

> [!NOTE]
> [Tamsayı türü kullanılarak](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-core-bigint.html) 64 bitlik tamsayı türü için çok büyük tamsayılar içeren hesaplamalar yapabilirsiniz. `bigint` temel tür olarak kabul edilmez; için bir kısaltmadır `System.Numerics.BigInteger` .

## <a name="see-also"></a>Ayrıca bkz.

- [F # dil başvurusu](index.md)
