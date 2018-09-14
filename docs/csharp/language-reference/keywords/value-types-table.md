---
title: Değer türleri tablosu (C# Başvurusu)
ms.date: 08/24/2018
helpviewer_keywords:
- value types [C#], table
- types [C#], value types
- types [C#], suffixes
ms.assetid: 67d8f631-b6e3-4d83-9910-5ec497f8c5f3
ms.openlocfilehash: bc7143b9f006af20b0bb91203d3093410d4ac0bf
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/14/2018
ms.locfileid: "45609729"
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

Varsa bir [tamsayı sayısal sabit değer](/dotnet/csharp/language-reference/language-specification/lexical-structure#integer-literals) hiçbir soneki olan ilk hangi değeri gösterilebileceği aşağıdaki türleri içeriyor: `int`, `uint`, `long`, `ulong`.

Varsa bir [gerçek sayısal sabit değer](/dotnet/csharp/language-reference/language-specification/lexical-structure#real-literals) hiçbir soneki olan türü `double`.

## <a name="see-also"></a>Ayrıca bkz.

- [C# başvurusu](../index.md)
- [C# Programlama Kılavuzu](../../programming-guide/index.md)
- [Türler için başvuru tabloları](reference-tables-for-types.md)
- [Varsayılan değerler tablosu](default-values-table.md)
- [Değer türleri](value-types.md)
- [Sayısal sonuçlar tablosunu biçimlendirme](formatting-numeric-results-table.md)
