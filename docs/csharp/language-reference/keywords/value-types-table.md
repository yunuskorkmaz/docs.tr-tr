---
title: Değer türleri tablosu - C# başvurusu
ms.custom: seodec18
ms.date: 08/24/2018
helpviewer_keywords:
- value types [C#], table
- types [C#], value types
- types [C#], suffixes
ms.assetid: 67d8f631-b6e3-4d83-9910-5ec497f8c5f3
ms.openlocfilehash: 81f85ce60f423cad8aecccad8f97e90897ba86db
ms.sourcegitcommit: d6e27023aeaffc4b5a3cb4b88685018d6284ada4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/09/2019
ms.locfileid: "67661595"
---
# <a name="value-types-table-c-reference"></a>Değer türleri tablosu (C# Başvurusu)

Aşağıdaki tabloda C# değer türleri:

|Değer türü|Kategori|Tür soneki|
|----------------|--------------|-----------------|
|[bool](bool.md)|Boole değeri||
|`byte`|İmzasız, sayısal, [tamsayı](../builtin-types/integral-numeric-types.md)||
|[char](char.md)|İmzasız, sayısal, [tamsayı](../builtin-types/integral-numeric-types.md)
)||
|`decimal`|Sayısal, [kayan nokta](../builtin-types/floating-point-numeric-types.md)|M veya m|
|`double`|Sayısal, [kayan nokta](../builtin-types/floating-point-numeric-types.md)|D veya d|
|[enum](enum.md)|Sabit Listesi||
|`float`|Sayısal, [kayan nokta](../builtin-types/floating-point-numeric-types.md)|F veya f|
|`int`|İmzalı, sayısal, [tamsayı](../builtin-types/integral-numeric-types.md)||
|`long`|İmzalı, sayısal, [tamsayı](../builtin-types/integral-numeric-types.md)|M veya m|
|`sbyte`|İmzalı, sayısal, [tamsayı](../builtin-types/integral-numeric-types.md)||
|`short`|İmzalı, sayısal, [tamsayı](../builtin-types/integral-numeric-types.md)||
|[struct](struct.md)|Kullanıcı tanımlı yapısı||
|`uint`|İmzasız, sayısal, [tamsayı](../builtin-types/integral-numeric-types.md)|U veya u|
|`ulong`|İmzasız, sayısal, [tamsayı](../builtin-types/integral-numeric-types.md)|UL, Ul, uL, ul, LU, Lu, lU veya lu|
|`ushort`|İmzasız, sayısal, [tamsayı](../builtin-types/integral-numeric-types.md)||

## <a name="remarks"></a>Açıklamalar

Bir sayısal değişmez değer türü belirtmek için kullanın. Örneğin:

```csharp
decimal a = 0.1M;
```

Varsa bir [tamsayı sayısal sabit değer](~/_csharplang/spec/lexical-structure.md#integer-literals) hiçbir soneki olan ilk hangi değeri gösterilebileceği aşağıdaki türleri içeriyor: `int`, `uint`, `long`, `ulong`.

Varsa bir [gerçek sayısal sabit değer](~/_csharplang/spec/lexical-structure.md#real-literals) hiçbir soneki olan türü `double`.

## <a name="see-also"></a>Ayrıca bkz.

- [C# başvurusu](../index.md)
- [C# Programlama Kılavuzu](../../programming-guide/index.md)
- [Varsayılan değerler tablosu](default-values-table.md)
- [Değer türleri](value-types.md)
- [Sayısal sonuçlar tablosunu biçimlendirme](formatting-numeric-results-table.md)
