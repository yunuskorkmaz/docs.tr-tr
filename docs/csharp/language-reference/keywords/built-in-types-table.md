---
title: Yerleşik türler tablo- C# başvuru
ms.custom: seodec18
description: Yerleşik C# türler için anahtar sözcükler
ms.date: 08/17/2018
helpviewer_keywords:
- types [C#], built-in
- built-in C# types
ms.assetid: 54f901f2-bf2f-472c-ae8d-73e8ecfc57fe
ms.openlocfilehash: 77a927a7735d565390c8a5560312ee36b9e48925
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74428550"
---
# <a name="built-in-types-table-c-reference"></a>Yerleşik türler tablosu (C# başvuru)

Aşağıdaki tabloda, <xref:System> ad alanında önceden tanımlanmış türlerin diğer C# adları olan yerleşik türler için anahtar sözcükler gösterilmektedir:

|C#türüyle|.NET türü|  
|--------------|-------------------------|  
|[bool](bool.md)|<xref:System.Boolean?displayProperty=nameWithType>|  
|[byte](../builtin-types/integral-numeric-types.md)|<xref:System.Byte?displayProperty=nameWithType>|  
|[sbyte](../builtin-types/integral-numeric-types.md)|<xref:System.SByte?displayProperty=nameWithType>|  
|[char](../builtin-types/char.md)|<xref:System.Char?displayProperty=nameWithType>|  
|[decimal](../builtin-types/floating-point-numeric-types.md)|<xref:System.Decimal?displayProperty=nameWithType>|  
|[double](../builtin-types/floating-point-numeric-types.md)|<xref:System.Double?displayProperty=nameWithType>|  
|[float](../builtin-types/floating-point-numeric-types.md)|<xref:System.Single?displayProperty=nameWithType>|  
|[int](../builtin-types/integral-numeric-types.md)|<xref:System.Int32?displayProperty=nameWithType>|  
|[uint](../builtin-types/integral-numeric-types.md)|<xref:System.UInt32?displayProperty=nameWithType>|  
|[long](../builtin-types/integral-numeric-types.md)|<xref:System.Int64?displayProperty=nameWithType>|  
|[ulong](../builtin-types/integral-numeric-types.md)|<xref:System.UInt64?displayProperty=nameWithType>|  
|[object](../builtin-types/reference-types.md)|<xref:System.Object?displayProperty=nameWithType>|  
|[short](../builtin-types/integral-numeric-types.md)|<xref:System.Int16?displayProperty=nameWithType>|  
|[ushort](../builtin-types/integral-numeric-types.md)|<xref:System.UInt16?displayProperty=nameWithType>|  
|[string](../builtin-types/reference-types.md)|<xref:System.String?displayProperty=nameWithType>|  
  
## <a name="remarks"></a>Açıklamalar

Tablodaki tüm türler, `object` ve `string`hariç, basit türler olarak adlandırılır.

.NET türleri ve bunların C# tür anahtar sözcük diğer adları değiştirilebilir. Örneğin, aşağıdaki bildirimlerden birini kullanarak bir tamsayı değişkeni bildirebilirsiniz:

```csharp
int x = 123;
System.Int32 y = 123;
```

Belirtilen türü temsil eden <xref:System.Type?displayProperty=nameWithType> örneğini almak için [typeof](../operators/type-testing-and-cast.md#typeof-operator) işlecini kullanın:

```csharp
Type stringType = typeof(string);
Console.WriteLine(stringType.FullName);

Type doubleType = typeof(System.Double);
Console.WriteLine(doubleType.FullName);

// Output:
// System.String
// System.Double
```

## <a name="see-also"></a>Ayrıca bkz.

- [C#Başvurunun](../index.md)
- [C# Programlama Kılavuzu](../../programming-guide/index.md)
- [C# Anahtar Sözcükleri](index.md)
- [Değer türleri](value-types.md)
- [Başvuru türleri](reference-types.md)
- [Varsayılan değerler tablosu](default-values-table.md)
- [dynamic](../builtin-types/reference-types.md)
