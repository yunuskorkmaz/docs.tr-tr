---
title: Yerleşik türler tablosu - C# başvurusu
ms.custom: seodec18
description: Yerleşik C# türleri için anahtar sözcükler
ms.date: 08/17/2018
helpviewer_keywords:
- types [C#], built-in
- built-in C# types
ms.assetid: 54f901f2-bf2f-472c-ae8d-73e8ecfc57fe
ms.openlocfilehash: e770c305afe098e633700b039efb51770c77ada7
ms.sourcegitcommit: d6e27023aeaffc4b5a3cb4b88685018d6284ada4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/09/2019
ms.locfileid: "67661442"
---
# <a name="built-in-types-table-c-reference"></a>Yerleşik türler tablosu (C# Başvurusu)

Önceden tanımlanmış tür diğer adları olan yerleşik C# türü için anahtar sözcükleri aşağıdaki tabloda gösterilmektedir, <xref:System> ad alanı.  
  
|C# türü|.NET türü|  
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

Tüm türleri tabloda dışında `object` ve `string`, basit türler olarak adlandırılır.  
  
C# anahtar sözcükleri yazın ve diğer adlarını birbirinin yerine kullanılabilir. Örneğin, aşağıdaki bildirimleri birini kullanarak bir tam sayı değişkeni bildirebilirsiniz:  

```csharp
int x = 123;
System.Int32 y = 123;
```

Kullanım [typeof](../operators/type-testing-and-conversion-operators.md#typeof-operator) almak için işleci <xref:System.Type?displayProperty=nameWithType> belirtilen türünü temsil eden örneği:

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

- [C# başvurusu](../../../csharp/language-reference/index.md)
- [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)
- [C# Anahtar Sözcükleri](index.md)
- [Değer türleri](value-types.md)
- [Başvuru türleri](reference-types.md)
- [Varsayılan değerler tablosu](default-values-table.md)
- [dynamic](dynamic.md)
