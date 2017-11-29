---
title: "Yerleşik Türler Tablosu (C# Başvurusu)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- types [C#], built-in
- built-in C# types
ms.assetid: 54f901f2-bf2f-472c-ae8d-73e8ecfc57fe
caps.latest.revision: "12"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: d9d1e4945526a862074e73e608185696328946be
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="built-in-types-table-c-reference"></a>Yerleşik Türler Tablosu (C# Başvurusu)
Anahtar sözcükler, önceden tanımlanmış türlerin diğer adları olan yerleşik C# türleri için aşağıdaki tabloda gösterilmektedir, <xref:System> ad alanı.  
  
|C# türü|.NET framework türü|  
|--------------|-------------------------|  
|[bool](../../../csharp/language-reference/keywords/bool.md)|`System.Boolean`|  
|[bayt](../../../csharp/language-reference/keywords/byte.md)|`System.Byte`|  
|[sbyte](../../../csharp/language-reference/keywords/sbyte.md)|`System.SByte`|  
|[char](../../../csharp/language-reference/keywords/char.md)|`System.Char`|  
|[ondalık](../../../csharp/language-reference/keywords/decimal.md)|`System.Decimal`|  
|[çift](../../../csharp/language-reference/keywords/double.md)|`System.Double`|  
|[kayan nokta](../../../csharp/language-reference/keywords/float.md)|`System.Single`|  
|[int](../../../csharp/language-reference/keywords/int.md)|`System.Int32`|  
|[uint](../../../csharp/language-reference/keywords/uint.md)|`System.UInt32`|  
|[uzun](../../../csharp/language-reference/keywords/long.md)|`System.Int64`|  
|[ulong](../../../csharp/language-reference/keywords/ulong.md)|`System.UInt64`|  
|[Nesne](../../../csharp/language-reference/keywords/object.md)|`System.Object`|  
|[kısa](../../../csharp/language-reference/keywords/short.md)|`System.Int16`|  
|[ushort](../../../csharp/language-reference/keywords/ushort.md)|`System.UInt16`|  
|[dize](../../../csharp/language-reference/keywords/string.md)|`System.String`|  
  
## <a name="remarks"></a>Açıklamalar  
 Tüm tablo türlerinde dışında `object` ve `string`, basit türleri olarak adlandırılır.  
  
 C# anahtar sözcükleri yazın ve benzersizse birbirinin yerine kullanılabilir. Örneğin, aşağıdaki bildirimlerini birini kullanarak bir tamsayı değişken bildirebilirsiniz:  
  
```  
int x = 123;  
System.Int32 x = 123;  
```  
  
 Herhangi bir C# türü için fiili türü görüntülemek için sistem yöntemini kullanın `GetType()`. Örneğin, aşağıdaki deyim türünü temsil eden sistem diğer adı görüntüler `myVariable`:  
  
```  
Console.WriteLine(myVariable.GetType());  
```  
  
 Aynı zamanda [typeof](../../../csharp/language-reference/keywords/typeof.md) işleci.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [C# başvurusu](../../../csharp/language-reference/index.md)  
 [C# programlama kılavuzu](../../../csharp/programming-guide/index.md)  
 [C# anahtar sözcükleri](../../../csharp/language-reference/keywords/index.md)  
 [Değer türleri](../../../csharp/language-reference/keywords/value-types.md)  
 [Varsayılan değerler tablosu](../../../csharp/language-reference/keywords/default-values-table.md)  
 [Sayısal sonuçlar tablosunu biçimlendirme](../../../csharp/language-reference/keywords/formatting-numeric-results-table.md)  
 [dinamik](../../../csharp/language-reference/keywords/dynamic.md)  
 [Türler için başvuru tabloları](../../../csharp/language-reference/keywords/reference-tables-for-types.md)
