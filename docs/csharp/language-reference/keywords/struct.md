---
title: struct (C# Başvurusu)
ms.date: 07/20/2015
f1_keywords:
- struct_CSharpKeyword
helpviewer_keywords:
- struct keyword [C#]
- structs [C#], struct keyword
ms.assetid: ff3dd9b7-dc93-4720-8855-ef5558f65c7c
ms.openlocfilehash: 7931da2e5f5c493b54eb1f33a1d6f57b38592f6e
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43530198"
---
# <a name="struct-c-reference"></a>struct (C# Başvurusu)
A `struct` türü, genelde küçük bir dikdörtgen koordinatlarını veya bir öğe bir stok özelliklerini gibi ilişkili değişken grupları kapsüllemek için kullanılan bir değer türüdür. Aşağıdaki örnek, bir basit yapı bildirimi gösterilmektedir:  
  
```csharp  
public struct Book  
{  
    public decimal price;  
    public string title;  
    public string author;  
}  
```  
  
## <a name="remarks"></a>Açıklamalar  
 Yapılar içerebilir [oluşturucular](../../../csharp/programming-guide/classes-and-structs/constructors.md), [sabitleri](../../../csharp/programming-guide/classes-and-structs/constants.md), [alanları](../../../csharp/programming-guide/classes-and-structs/fields.md), [yöntemleri](../../../csharp/programming-guide/classes-and-structs/methods.md), [özellikleri](../../../csharp/programming-guide/classes-and-structs/properties.md), [dizin oluşturucular](../../../csharp/programming-guide/indexers/index.md), [işleçleri](../../../csharp/programming-guide/statements-expressions-operators/operators.md), [olayları](../../../csharp/programming-guide/events/index.md), ve [türlerin](../../../csharp/programming-guide/classes-and-structs/nested-types.md), ancak birçok üye gerekliyse, türünüz bunun yerine bir sınıf yapma dikkate almanız gerekir.  
  
 Örnekler için bkz [yapılar kullanarak](../../../csharp/programming-guide/classes-and-structs/using-structs.md).  
  
 Yapı birimleri arabirim uygulayabilir, ancak bunlar başka bir yapı devralamaz. Bu nedenle, Yapı üyeleri olarak bildirilemez `protected`.  
  
 Daha fazla bilgi için [yapılar](../../../csharp/programming-guide/classes-and-structs/structs.md).  
  
## <a name="examples"></a>Örnekler  
 Örnekler ve daha fazla bilgi için bkz. [yapılar kullanarak](../../../csharp/programming-guide/classes-and-structs/using-structs.md).  
  
## <a name="c-language-specification"></a>C# Dil Belirtimi  
 Örnekler için bkz [yapılar kullanarak](../../../csharp/programming-guide/classes-and-structs/using-structs.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.

- [C# başvurusu](../../../csharp/language-reference/index.md)  
- [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)  
- [C# Anahtar Sözcükleri](../../../csharp/language-reference/keywords/index.md)  
- [Varsayılan Değerler Tablosu](../../../csharp/language-reference/keywords/default-values-table.md)  
- [Yerleşik Türler Tablosu](../../../csharp/language-reference/keywords/built-in-types-table.md)  
- [Türler](../../../csharp/language-reference/keywords/types.md)  
- [Değer Türleri](../../../csharp/language-reference/keywords/value-types.md)  
- [class](../../../csharp/language-reference/keywords/class.md)  
- [interface](../../../csharp/language-reference/keywords/interface.md)  
- [Sınıflar ve Yapılar](../../../csharp/programming-guide/classes-and-structs/index.md)
