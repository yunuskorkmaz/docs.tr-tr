---
title: "Varsayılan değerler tablosu (C# Başvurusu)"
descripton: Learn what are the default values of value types returned by the default constructors.
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- constructors [C#], return values
- keywords [C#], new
- default constructor [C#]
- defaults [C#]
- value types [C#], initializing
- variables [C#], value types
- constructors [C#], default constructor
- types [C#], default constructor return values
ms.assetid: 4af2c1df-9e3a-48c1-83ac-b192986fc5bc
caps.latest.revision: "12"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: d034c1daf495c50e299fec4c5bf399652dad08ce
ms.sourcegitcommit: 425524461530f020f9747492b42f8cd72b011ae7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/25/2017
---
# <a name="default-values-table-c-reference"></a>Varsayılan değerler tablosu (C# Başvurusu)
Aşağıdaki tabloda, varsayılan oluşturucular tarafından döndürülen değer türlerinin varsayılan değerleri gösterir. Varsayılan Oluşturucu çağrılır kullanarak `new` şekilde işleci:

```csharp
int myInt = new int();
```

Önceki deyimi aşağıdaki ifadeyi aynı etkiye sahiptir:

```csharp
int myInt = 0;
```

Başlatılmamış değişkenleri C# kullanarak verilmez unutmayın.

|Değer türü|Varsayılan değer|
|----------------|-------------------|
|[bool](../../../csharp/language-reference/keywords/bool.md)|`false`|
|[bayt](../../../csharp/language-reference/keywords/byte.md)|0|
|[char](../../../csharp/language-reference/keywords/char.md)|'\0'|
|[ondalık](../../../csharp/language-reference/keywords/decimal.md)|0M|
|[çift](../../../csharp/language-reference/keywords/double.md)|0,0 D|
|[Enum](../../../csharp/language-reference/keywords/enum.md)|Burada E enum tanımlayıcısıdır (E) 0, deyim tarafından üretilen değeri.|
|[kayan nokta](../../../csharp/language-reference/keywords/float.md)|0.0F|
|[int](../../../csharp/language-reference/keywords/int.md)|0|
|[uzun](../../../csharp/language-reference/keywords/long.md)|0 M|
|[sbyte](../../../csharp/language-reference/keywords/sbyte.md)|0|
|[kısa](../../../csharp/language-reference/keywords/short.md)|0|
|[yapısı](../../../csharp/language-reference/keywords/struct.md)|Değer üretilen tüm değer tür alanları varsayılan değerlerine ve tüm başvuru türü alanlarına ayarlanarak `null`.|
|[uint](../../../csharp/language-reference/keywords/uint.md)|0|
|[ulong](../../../csharp/language-reference/keywords/ulong.md)|0|
|[ushort](../../../csharp/language-reference/keywords/ushort.md)|0|

## <a name="see-also"></a>Ayrıca bkz.
 [C# başvurusu](../../../csharp/language-reference/index.md)  
 [C# programlama kılavuzu](../../../csharp/programming-guide/index.md)  
 [Değer türleri tablosu](../../../csharp/language-reference/keywords/value-types-table.md)  
 [Değer türleri](../../../csharp/language-reference/keywords/value-types.md)  
 [Yerleşik türler tablosu](../../../csharp/language-reference/keywords/built-in-types-table.md)  
 [Türler için başvuru tabloları](../../../csharp/language-reference/keywords/reference-tables-for-types.md)
