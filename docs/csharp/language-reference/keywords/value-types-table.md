---
title: Değer türleri tablosu - C# başvurusu
ms.custom: seodec18
ms.date: 08/24/2018
helpviewer_keywords:
- value types [C#], table
- types [C#], value types
- types [C#], suffixes
ms.assetid: 67d8f631-b6e3-4d83-9910-5ec497f8c5f3
ms.openlocfilehash: d651350f46c0ec1947be9f4f586c341514356fd2
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/11/2018
ms.locfileid: "53244160"
---
# <a name="value-types-table-c-reference"></a>Değer türleri tablosu (C# Başvurusu)

Aşağıdaki tabloda, C# değer türleri gösterilmektedir.  
  
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
- [Türler için başvuru tabloları](reference-tables-for-types.md)
- [Varsayılan değerler tablosu](default-values-table.md)
- [Değer türleri](value-types.md)
- [Sayısal sonuçlar tablosunu biçimlendirme](formatting-numeric-results-table.md)
