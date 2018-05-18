---
title: struct (C# Başvurusu)
ms.date: 07/20/2015
f1_keywords:
- struct_CSharpKeyword
helpviewer_keywords:
- struct keyword [C#]
- structs [C#], struct keyword
ms.assetid: ff3dd9b7-dc93-4720-8855-ef5558f65c7c
ms.openlocfilehash: ddea59e76835ccccd07c299f819796336cddada8
ms.sourcegitcommit: 89c93d05c2281b4c834f48f6c8df1047e1410980
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/15/2018
---
# <a name="struct-c-reference"></a>struct (C# Başvurusu)
A `struct` türüdür genellikle bir dikdörtgen koordinatlarını veya öğeyi bir stok özelliklerini gibi ilgili değişkenlerin küçük gruplar kapsüllemek için kullanılan bir değer türü. Aşağıdaki örnek, bir basit yapı bildirimi gösterir:  
  
```csharp  
public struct Book  
{  
    public decimal price;  
    public string title;  
    public string author;  
}  
```  
  
## <a name="remarks"></a>Açıklamalar  
 Yapılar de içerebilir [oluşturucular](../../../csharp/programming-guide/classes-and-structs/constructors.md), [sabitleri](../../../csharp/programming-guide/classes-and-structs/constants.md), [alanları](../../../csharp/programming-guide/classes-and-structs/fields.md), [yöntemleri](../../../csharp/programming-guide/classes-and-structs/methods.md), [özellikleri](../../../csharp/programming-guide/classes-and-structs/properties.md), [dizin oluşturucular](../../../csharp/programming-guide/indexers/index.md), [işleçleri](../../../csharp/programming-guide/statements-expressions-operators/operators.md), [olayları](../../../csharp/programming-guide/events/index.md), ve [türleri iç içe geçmiş](../../../csharp/programming-guide/classes-and-structs/nested-types.md), ancak bu tür üyeler, gerekirse, Bunun yerine, türü bir sınıf yapma göz önünde bulundurmalısınız.  
  
 Örnekler için bkz: [kullanarak yapılar](../../../csharp/programming-guide/classes-and-structs/using-structs.md).  
  
 Yapılar bir arabirimi uygulayabilirsiniz, ancak başka bir yapı devralınan olamaz. Bu nedenle, Yapı üyeleri olarak bildirilemez `protected`.  
  
 Daha fazla bilgi için bkz: [yapılar](../../../csharp/programming-guide/classes-and-structs/structs.md).  
  
## <a name="examples"></a>Örnekler  
 Örnekler ve daha fazla bilgi için bkz: [kullanarak yapılar](../../../csharp/programming-guide/classes-and-structs/using-structs.md).  
  
## <a name="c-language-specification"></a>C# Dil Belirtimi  
 Örnekler için bkz: [kullanarak yapılar](../../../csharp/programming-guide/classes-and-structs/using-structs.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [C# başvurusu](../../../csharp/language-reference/index.md)  
 [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)  
 [C# Anahtar Sözcükleri](../../../csharp/language-reference/keywords/index.md)  
 [Varsayılan Değerler Tablosu](../../../csharp/language-reference/keywords/default-values-table.md)  
 [Yerleşik Türler Tablosu](../../../csharp/language-reference/keywords/built-in-types-table.md)  
 [Türler](../../../csharp/language-reference/keywords/types.md)  
 [Değer Türleri](../../../csharp/language-reference/keywords/value-types.md)  
 [class](../../../csharp/language-reference/keywords/class.md)  
 [interface](../../../csharp/language-reference/keywords/interface.md)  
 [Sınıflar ve Yapılar](../../../csharp/programming-guide/classes-and-structs/index.md)
