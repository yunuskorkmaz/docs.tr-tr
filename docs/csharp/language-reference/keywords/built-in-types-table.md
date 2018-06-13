---
title: Yerleşik Türler Tablosu (C# Başvurusu)
ms.date: 07/20/2015
helpviewer_keywords:
- types [C#], built-in
- built-in C# types
ms.assetid: 54f901f2-bf2f-472c-ae8d-73e8ecfc57fe
ms.openlocfilehash: 120347e5bff7f0d6c7120af0cb250936ca39ea16
ms.sourcegitcommit: 89c93d05c2281b4c834f48f6c8df1047e1410980
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/15/2018
ms.locfileid: "34172272"
---
# <a name="built-in-types-table-c-reference"></a>Yerleşik Türler Tablosu (C# Başvurusu)
Anahtar sözcükler, önceden tanımlanmış türlerin diğer adları olan yerleşik C# türleri için aşağıdaki tabloda gösterilmektedir, <xref:System> ad alanı.  
  
|C# türü|.NET framework türü|  
|--------------|-------------------------|  
|[bool](../../../csharp/language-reference/keywords/bool.md)|`System.Boolean`|  
|[byte](../../../csharp/language-reference/keywords/byte.md)|`System.Byte`|  
|[sbyte](../../../csharp/language-reference/keywords/sbyte.md)|`System.SByte`|  
|[char](../../../csharp/language-reference/keywords/char.md)|`System.Char`|  
|[decimal](../../../csharp/language-reference/keywords/decimal.md)|`System.Decimal`|  
|[double](../../../csharp/language-reference/keywords/double.md)|`System.Double`|  
|[float](../../../csharp/language-reference/keywords/float.md)|`System.Single`|  
|[int](../../../csharp/language-reference/keywords/int.md)|`System.Int32`|  
|[uint](../../../csharp/language-reference/keywords/uint.md)|`System.UInt32`|  
|[long](../../../csharp/language-reference/keywords/long.md)|`System.Int64`|  
|[ulong](../../../csharp/language-reference/keywords/ulong.md)|`System.UInt64`|  
|[object](../../../csharp/language-reference/keywords/object.md)|`System.Object`|  
|[short](../../../csharp/language-reference/keywords/short.md)|`System.Int16`|  
|[ushort](../../../csharp/language-reference/keywords/ushort.md)|`System.UInt16`|  
|[string](../../../csharp/language-reference/keywords/string.md)|`System.String`|  
  
## <a name="remarks"></a>Açıklamalar  
 Tüm tablo türlerinde dışında `object` ve `string`, basit türleri olarak adlandırılır.  
  
 C# anahtar sözcükleri yazın ve benzersizse birbirinin yerine kullanılabilir. Örneğin, aşağıdaki bildirimlerini birini kullanarak bir tamsayı değişken bildirebilirsiniz:  
  
```csharp  
int x = 123;  
System.Int32 x = 123;  
```  
  
 Herhangi bir C# türü için fiili türü görüntülemek için sistem yöntemini kullanın `GetType()`. Örneğin, aşağıdaki deyim türünü temsil eden sistem diğer adı görüntüler `myVariable`:  
  
```csharp  
Console.WriteLine(myVariable.GetType());  
```  
  
 Aynı zamanda [typeof](../../../csharp/language-reference/keywords/typeof.md) işleci.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [C# başvurusu](../../../csharp/language-reference/index.md)  
 [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)  
 [C# Anahtar Sözcükleri](../../../csharp/language-reference/keywords/index.md)  
 [Değer Türleri](../../../csharp/language-reference/keywords/value-types.md)  
 [Varsayılan Değerler Tablosu](../../../csharp/language-reference/keywords/default-values-table.md)  
 [Sayısal Sonuçlar Tablosunu Biçimlendirme](../../../csharp/language-reference/keywords/formatting-numeric-results-table.md)  
 [dynamic](../../../csharp/language-reference/keywords/dynamic.md)  
 [Türler için Başvuru Tabloları](../../../csharp/language-reference/keywords/reference-tables-for-types.md)
