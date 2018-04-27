---
title: Varsayılan değerler tablosu (C# Başvurusu)
descripton: Learn what are the default values of value types returned by the default constructors.
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
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
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: e249dd2f352fe6177f3afbfd089fc4dc9b1b7798
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/26/2018
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
|[bool](bool.md)|`false`|
|[byte](byte.md)|0|
|[char](char.md)|'\0'|
|[decimal](decimal.md)|0M|
|[double](double.md)|0,0 D|
|[enum](enum.md)|Burada E enum tanımlayıcısıdır (E) 0, deyim tarafından üretilen değeri.|
|[float](float.md)|0.0F|
|[int](int.md)|0|
|[long](long.md)|0 M|
|[sbyte](sbyte.md)|0|
|[short](short.md)|0|
|[struct](struct.md)|Değer üretilen tüm değer tür alanları varsayılan değerlerine ve tüm başvuru türü alanlarına ayarlanarak `null`.|
|[uint](uint.md)|0|
|[ulong](ulong.md)|0|
|[ushort](ushort.md)|0|

## <a name="see-also"></a>Ayrıca bkz.
 [C# başvurusu](../index.md)  
 [C# Programlama Kılavuzu](../../programming-guide/index.md)  
 [Değer Türleri Tablosu](value-types-table.md)  
 [Değer Türleri](value-types.md)  
 [Yerleşik Türler Tablosu](built-in-types-table.md)  
 [Türler için Başvuru Tabloları](reference-tables-for-types.md)
