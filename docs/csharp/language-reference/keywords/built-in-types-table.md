---
title: Yerleşik türler tablosu - C# başvurusu
ms.custom: seodec18
description: Yerleşik C# türleri için anahtar sözcükler
ms.date: 08/17/2018
helpviewer_keywords:
- types [C#], built-in
- built-in C# types
ms.assetid: 54f901f2-bf2f-472c-ae8d-73e8ecfc57fe
ms.openlocfilehash: fae0cedfe8bf675dceb9cb9d5835d923cae8b4ab
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/11/2018
ms.locfileid: "53235637"
---
# <a name="built-in-types-table-c-reference"></a>Yerleşik türler tablosu (C# Başvurusu)

Önceden tanımlanmış tür diğer adları olan yerleşik C# türü için anahtar sözcükleri aşağıdaki tabloda gösterilmektedir, <xref:System> ad alanı.  
  
|C# türü|.NET türü|  
|--------------|-------------------------|  
|[bool](bool.md)|<xref:System.Boolean?displayProperty=nameWithType>|  
|[byte](byte.md)|<xref:System.Byte?displayProperty=nameWithType>|  
|[sbyte](sbyte.md)|<xref:System.SByte?displayProperty=nameWithType>|  
|[char](char.md)|<xref:System.Char?displayProperty=nameWithType>|  
|[decimal](decimal.md)|<xref:System.Decimal?displayProperty=nameWithType>|  
|[double](double.md)|<xref:System.Double?displayProperty=nameWithType>|  
|[float](float.md)|<xref:System.Single?displayProperty=nameWithType>|  
|[int](int.md)|<xref:System.Int32?displayProperty=nameWithType>|  
|[uint](uint.md)|<xref:System.UInt32?displayProperty=nameWithType>|  
|[long](long.md)|<xref:System.Int64?displayProperty=nameWithType>|  
|[ulong](ulong.md)|<xref:System.UInt64?displayProperty=nameWithType>|  
|[object](object.md)|<xref:System.Object?displayProperty=nameWithType>|  
|[short](short.md)|<xref:System.Int16?displayProperty=nameWithType>|  
|[ushort](ushort.md)|<xref:System.UInt16?displayProperty=nameWithType>|  
|[string](string.md)|<xref:System.String?displayProperty=nameWithType>|  
  
## <a name="remarks"></a>Açıklamalar

Tüm türleri tabloda dışında `object` ve `string`, basit türler olarak adlandırılır.  
  
C# anahtar sözcükleri yazın ve diğer adlarını birbirinin yerine kullanılabilir. Örneğin, aşağıdaki bildirimleri birini kullanarak bir tam sayı değişkeni bildirebilirsiniz:  

```csharp
int x = 123;
System.Int32 y = 123;
```

Kullanım [typeof](typeof.md) almak için işleci <xref:System.Type?displayProperty=nameWithType> belirtilen türünü temsil eden örneği:

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
- [Türler için başvuru tabloları](reference-tables-for-types.md)
- [Değer türleri](value-types.md)
- [Başvuru türleri](reference-types.md)
- [Varsayılan değerler tablosu](default-values-table.md)
- [dynamic](dynamic.md)
