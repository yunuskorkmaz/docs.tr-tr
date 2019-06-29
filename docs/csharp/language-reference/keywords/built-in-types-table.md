---
title: Yerleşik türler tablosu - C# başvurusu
ms.custom: seodec18
description: Yerleşik C# türleri için anahtar sözcükler
ms.date: 08/17/2018
helpviewer_keywords:
- types [C#], built-in
- built-in C# types
ms.assetid: 54f901f2-bf2f-472c-ae8d-73e8ecfc57fe
ms.openlocfilehash: 4a54059f288a432cbaf904626cabf4f7bcba7209
ms.sourcegitcommit: 9b1ac36b6c80176fd4e20eb5bfcbd9d56c3264cf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/28/2019
ms.locfileid: "67424381"
---
# <a name="built-in-types-table-c-reference"></a>Yerleşik türler tablosu (C# Başvurusu)

Önceden tanımlanmış tür diğer adları olan yerleşik C# türü için anahtar sözcükleri aşağıdaki tabloda gösterilmektedir, <xref:System> ad alanı.  
  
|C# türü|.NET türü|  
|--------------|-------------------------|  
|[bool](bool.md)|<xref:System.Boolean?displayProperty=nameWithType>|  
|[byte](../builtin-types/integral-numeric-types.md)|<xref:System.Byte?displayProperty=nameWithType>|  
|[sbyte](../builtin-types/integral-numeric-types.md)|<xref:System.SByte?displayProperty=nameWithType>|  
|[char](char.md)|<xref:System.Char?displayProperty=nameWithType>|  
|[decimal](decimal.md)|<xref:System.Decimal?displayProperty=nameWithType>|  
|[double](double.md)|<xref:System.Double?displayProperty=nameWithType>|  
|[float](float.md)|<xref:System.Single?displayProperty=nameWithType>|  
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
