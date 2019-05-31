---
title: Değer türleri tablosu - C# başvurusu
ms.custom: seodec18
ms.date: 08/24/2018
helpviewer_keywords:
- value types [C#], table
- types [C#], value types
- types [C#], suffixes
ms.assetid: 67d8f631-b6e3-4d83-9910-5ec497f8c5f3
ms.openlocfilehash: 959d4840344ba041ae1b01fd6d202f2b53936afc
ms.sourcegitcommit: 10986410e59ff29f2ec55c6759bde3eb4d1a00cb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/31/2019
ms.locfileid: "66422364"
---
# <a name="value-types-table-c-reference"></a>Değer türleri tablosu (C# Başvurusu)

Aşağıdaki tabloda C# değer türleri:

|Değer türü|Kategori|Tür soneki|
|----------------|--------------|-----------------|
|[bool](bool.md)|Boole değeri||
|[byte](byte.md)|İmzasız, sayısal, [tamsayı](integral-types-table.md)||
|[char](char.md)|İmzasız, sayısal, [tamsayı](integral-types-table.md)||
|[decimal](decimal.md)|Sayısal, [kayan nokta](floating-point-types-table.md)|M veya m|
|[double](double.md)|Sayısal, [kayan nokta](floating-point-types-table.md)|D veya d|
|[enum](enum.md)|Sabit Listesi||
|[float](float.md)|Sayısal, [kayan nokta](floating-point-types-table.md)|F veya f|
|[int](int.md)|İmzalı, sayısal, [tamsayı](integral-types-table.md)||
|[long](long.md)|İmzalı, sayısal, [tamsayı](integral-types-table.md)|M veya m|
|[sbyte](sbyte.md)|İmzalı, sayısal, [tamsayı](integral-types-table.md)||
|[short](short.md)|İmzalı, sayısal, [tamsayı](integral-types-table.md)||
|[struct](struct.md)|Kullanıcı tanımlı yapısı||
|[uint](uint.md)|İmzasız, sayısal, [tamsayı](integral-types-table.md)|U veya u|
|[ulong](ulong.md)|İmzasız, sayısal, [tamsayı](integral-types-table.md)|UL, Ul, uL, ul, LU, Lu, lU veya lu|
|[ushort](ushort.md)|İmzasız, sayısal, [tamsayı](integral-types-table.md)||

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
