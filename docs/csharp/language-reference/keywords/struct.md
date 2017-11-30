---
title: "struct (C# Başvurusu)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: struct_CSharpKeyword
helpviewer_keywords:
- struct keyword [C#]
- structs [C#], struct keyword
ms.assetid: ff3dd9b7-dc93-4720-8855-ef5558f65c7c
caps.latest.revision: "23"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: e8a848d5543291ef335e72cb7806158827e865dd
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="struct-c-reference"></a>struct (C# Başvurusu)
A `struct` türüdür genellikle bir dikdörtgen koordinatlarını veya öğeyi bir stok özelliklerini gibi ilgili değişkenlerin küçük gruplar kapsüllemek için kullanılan bir değer türü. Aşağıdaki örnek, bir basit yapı bildirimi gösterir:  
  
```  
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
 [C# programlama kılavuzu](../../../csharp/programming-guide/index.md)  
 [C# anahtar sözcükleri](../../../csharp/language-reference/keywords/index.md)  
 [Varsayılan değerler tablosu](../../../csharp/language-reference/keywords/default-values-table.md)  
 [Yerleşik türler tablosu](../../../csharp/language-reference/keywords/built-in-types-table.md)  
 [Türler](../../../csharp/language-reference/keywords/types.md)  
 [Değer türleri](../../../csharp/language-reference/keywords/value-types.md)  
 [sınıfı](../../../csharp/language-reference/keywords/class.md)  
 [arabirimi](../../../csharp/language-reference/keywords/interface.md)  
 [Sınıflar ve yapılar](../../../csharp/programming-guide/classes-and-structs/index.md)
