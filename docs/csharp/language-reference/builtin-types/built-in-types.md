---
title: Yerleşik türler-C# başvurusu
description: C# yerleşik değer ve başvuru türleri hakkında bilgi edinin
ms.date: 03/15/2021
helpviewer_keywords:
- types [C#], built-in
- built-in C# types
ms.openlocfilehash: 4b92add8189c6205408ec78c281eaacf04173047
ms.sourcegitcommit: 05d0087dfca85aac9ca2960f86c5efd218bf833f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/27/2021
ms.locfileid: "105637071"
---
# <a name="built-in-types-c-reference"></a>Yerleşik türler (C# Başvurusu)

Aşağıdaki tabloda C# yerleşik [değer](value-types.md) türleri listelenmektedir:

|C# Type anahtar sözcüğü|.NET türü|
|--------------|-------------------------|
|[`bool`](bool.md)|<xref:System.Boolean?displayProperty=nameWithType>|
|[`byte`](integral-numeric-types.md)|<xref:System.Byte?displayProperty=nameWithType>|
|[`sbyte`](integral-numeric-types.md)|<xref:System.SByte?displayProperty=nameWithType>|
|[`char`](char.md)|<xref:System.Char?displayProperty=nameWithType>|
|[`decimal`](floating-point-numeric-types.md)|<xref:System.Decimal?displayProperty=nameWithType>|
|[`double`](floating-point-numeric-types.md)|<xref:System.Double?displayProperty=nameWithType>|
|[`float`](floating-point-numeric-types.md)|<xref:System.Single?displayProperty=nameWithType>|
|[`int`](integral-numeric-types.md)|<xref:System.Int32?displayProperty=nameWithType>|
|[`uint`](integral-numeric-types.md)|<xref:System.UInt32?displayProperty=nameWithType>|
|[`nint`](nint-nuint.md)|<xref:System.IntPtr?displayProperty=nameWithType>|
|[`nuint`](nint-nuint.md)|<xref:System.UIntPtr?displayProperty=nameWithType>|
|[`long`](integral-numeric-types.md)|<xref:System.Int64?displayProperty=nameWithType>|
|[`ulong`](integral-numeric-types.md)|<xref:System.UInt64?displayProperty=nameWithType>|
|[`short`](integral-numeric-types.md)|<xref:System.Int16?displayProperty=nameWithType>|
|[`ushort`](integral-numeric-types.md)|<xref:System.UInt16?displayProperty=nameWithType>|

Aşağıdaki tabloda C# yerleşik [başvuru](../keywords/reference-types.md) türleri listelenmektedir:

|C# Type anahtar sözcüğü|.NET türü|
|--------------|-------------------------|
|[`object`](reference-types.md#the-object-type)|<xref:System.Object?displayProperty=nameWithType>|
|[`string`](reference-types.md#the-string-type)|<xref:System.String?displayProperty=nameWithType>|
|[`dynamic`](reference-types.md#the-dynamic-type)|<xref:System.Object?displayProperty=nameWithType>|

Yukarıdaki tablolarda, sol sütundan ( [nint ve nint](nint-nuint.md) ve [Dynamic](reference-types.md#the-dynamic-type)dışında) her C# tür anahtar sözcüğü, karşılık gelen .NET türü için bir diğer addır. Bunlar arasında değiştirilebilir. Örneğin, aşağıdaki bildirimler aynı türdeki değişkenleri bildirir:

```csharp
int a = 123;
System.Int32 b = 123;
```

`nint` `nuint` İlk tablonun son iki satırında ve türleri yerel boyutlu tamsayılardır. Bunlar, belirtilen .NET türleri tarafından dahili olarak temsil edilir, ancak her durumda anahtar sözcüğü ve .NET türü birbirini değiştirmez. Derleyici, `nint` ve için ve `nuint` işaretçi türleri için sağlamayan tamsayı türleri olarak işlemler ve dönüştürmeler sağlar `System.IntPtr` `System.UIntPtr` . Daha fazla bilgi için bkz. [ `nint` ve `nuint` türleri](nint-nuint.md).

[`void`](void.md)Anahtar sözcüğü bir türün yokluğunu temsil eder. Değer döndürmeyen bir yöntemin dönüş türü olarak kullanabilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.

- [C# başvurusu](../index.md)
- [C# türlerinin varsayılan değerleri](default-values.md)
