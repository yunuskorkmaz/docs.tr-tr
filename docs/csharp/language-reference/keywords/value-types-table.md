---
title: Değer türleri tablosu - C# başvurusu
ms.custom: seodec18
ms.date: 08/24/2018
helpviewer_keywords:
- value types [C#], table
- types [C#], value types
- types [C#], suffixes
ms.assetid: 67d8f631-b6e3-4d83-9910-5ec497f8c5f3
ms.openlocfilehash: 98829f30c2c25c0710cf3fe044359d3c7538fe76
ms.sourcegitcommit: 9b1ac36b6c80176fd4e20eb5bfcbd9d56c3264cf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/28/2019
ms.locfileid: "67424049"
---
# <a name="value-types-table-c-reference"></a>Değer türleri tablosu (C# Başvurusu)

Aşağıdaki tabloda C# değer türleri:

|Değer türü|Kategori|Tür soneki|
|----------------|--------------|-----------------|
|[bool](bool.md)|Boole değeri||
|[byte](../builtin-types/integral-numeric-types.md)|İmzasız, sayısal, [tamsayı](../builtin-types/integral-numeric-types.md)||
|[char](char.md)|İmzasız, sayısal, [tamsayı](../builtin-types/integral-numeric-types.md)
)||
|[decimal](decimal.md)|Sayısal, [kayan nokta](floating-point-types-table.md)|M veya m|
|[double](double.md)|Sayısal, [kayan nokta](floating-point-types-table.md)|D veya d|
|[enum](enum.md)|Sabit Listesi||
|[float](float.md)|Sayısal, [kayan nokta](floating-point-types-table.md)|F veya f|
|[int](../builtin-types/integral-numeric-types.md)|İmzalı, sayısal, [tamsayı](../builtin-types/integral-numeric-types.md)||
|[long](../builtin-types/integral-numeric-types.md)|İmzalı, sayısal, [tamsayı](../builtin-types/integral-numeric-types.md)|M veya m|
|[sbyte](../builtin-types/integral-numeric-types.md)|İmzalı, sayısal, [tamsayı](../builtin-types/integral-numeric-types.md)||
|[short](../builtin-types/integral-numeric-types.md)|İmzalı, sayısal, [tamsayı](../builtin-types/integral-numeric-types.md)||
|[struct](struct.md)|Kullanıcı tanımlı yapısı||
|[uint](../builtin-types/integral-numeric-types.md)|İmzasız, sayısal, [tamsayı](../builtin-types/integral-numeric-types.md)|U veya u|
|[ulong](../builtin-types/integral-numeric-types.md)|İmzasız, sayısal, [tamsayı](../builtin-types/integral-numeric-types.md)|UL, Ul, uL, ul, LU, Lu, lU veya lu|
|[ushort](../builtin-types/integral-numeric-types.md)|İmzasız, sayısal, [tamsayı](../builtin-types/integral-numeric-types.md)||

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
