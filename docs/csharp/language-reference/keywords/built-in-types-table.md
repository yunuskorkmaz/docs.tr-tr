---
title: Yerleşik türler tablo- C# başvuru
ms.custom: seodec18
description: Yerleşik C# türler için anahtar sözcükler
ms.date: 08/17/2018
helpviewer_keywords:
- types [C#], built-in
- built-in C# types
ms.assetid: 54f901f2-bf2f-472c-ae8d-73e8ecfc57fe
ms.openlocfilehash: 61701cc38c38b5e7235fbadb6d2a86e0e66b09ac
ms.sourcegitcommit: 29a9b29d8b7d07b9c59d46628da754a8bff57fa4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/17/2019
ms.locfileid: "69566366"
---
# <a name="built-in-types-table-c-reference"></a>Yerleşik türler tablosu (C# başvuru)

Aşağıdaki tabloda, <xref:System> ad alanındaki önceden tanımlanmış türlerin diğer adları C# olan yerleşik türler için anahtar sözcükler gösterilmektedir.  
  
|C#türüyle|.NET türü|  
|--------------|-------------------------|  
|[bool](bool.md)|<xref:System.Boolean?displayProperty=nameWithType>|  
|[byte](../builtin-types/integral-numeric-types.md)|<xref:System.Byte?displayProperty=nameWithType>|  
|[sbyte](../builtin-types/integral-numeric-types.md)|<xref:System.SByte?displayProperty=nameWithType>|  
|[char](char.md)|<xref:System.Char?displayProperty=nameWithType>|  
|[decimal](../builtin-types/floating-point-numeric-types.md)|<xref:System.Decimal?displayProperty=nameWithType>|  
|[double](../builtin-types/floating-point-numeric-types.md)|<xref:System.Double?displayProperty=nameWithType>|  
|[float](../builtin-types/floating-point-numeric-types.md)|<xref:System.Single?displayProperty=nameWithType>|  
|[int](../builtin-types/integral-numeric-types.md)|<xref:System.Int32?displayProperty=nameWithType>|  
|[uint](../builtin-types/integral-numeric-types.md)|<xref:System.UInt32?displayProperty=nameWithType>|  
|[long](../builtin-types/integral-numeric-types.md)|<xref:System.Int64?displayProperty=nameWithType>|  
|[ulong](../builtin-types/integral-numeric-types.md)|<xref:System.UInt64?displayProperty=nameWithType>|  
|[object](object.md)|<xref:System.Object?displayProperty=nameWithType>|  
|[short](../builtin-types/integral-numeric-types.md)|<xref:System.Int16?displayProperty=nameWithType>|  
|[ushort](../builtin-types/integral-numeric-types.md)|<xref:System.UInt16?displayProperty=nameWithType>|  
|[string](string.md)|<xref:System.String?displayProperty=nameWithType>|  
  
## <a name="remarks"></a>Açıklamalar

`object` Ve`string`hariç olmak üzere tablodaki tüm türler basit türler olarak adlandırılır.  
  
.NET türleri ve bunların C# tür anahtar sözcük diğer adları değiştirilebilir. Örneğin, aşağıdaki bildirimlerden birini kullanarak bir tamsayı değişkeni bildirebilirsiniz:  

```csharp
int x = 123;
System.Int32 y = 123;
```

Belirtilen türü [](../operators/type-testing-and-cast.md#typeof-operator) temsil eden <xref:System.Type?displayProperty=nameWithType> örneği almak için typeof işlecini kullanın:

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

- [C#Başvurunun](../../../csharp/language-reference/index.md)
- [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)
- [C# Anahtar Sözcükleri](index.md)
- [Değer türleri](value-types.md)
- [Başvuru türleri](reference-types.md)
- [Varsayılan değerler tablosu](default-values-table.md)
- [dynamic](dynamic.md)
