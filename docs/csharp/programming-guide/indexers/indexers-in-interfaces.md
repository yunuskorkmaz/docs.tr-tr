---
title: Arabirimlerdeki Dizin Oluşturucular (C# Programlama Kılavuzu)
ms.date: 07/20/2015
helpviewer_keywords:
- indexers [C#], in interfaces
- accessors [C#], indexers
ms.assetid: e16b54bd-4a83-4f52-bd75-65819fca79e8
ms.openlocfilehash: c3ddb48590087d49402482e8cbf3760027da1a2a
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43673468"
---
# <a name="indexers-in-interfaces-c-programming-guide"></a>Arabirimlerdeki Dizin Oluşturucular (C# Programlama Kılavuzu)
Dizin oluşturucular bildirilebilir bir [arabirimi](../../../csharp/language-reference/keywords/interface.md). Arabirim dizin oluşturucuları erişicilerini erişicilerini farklı [sınıfı](../../../csharp/language-reference/keywords/class.md) dizin oluşturucuları aşağıdaki yollarla:  
  
-   Arabirimi erişimcileri değiştiriciler kullanmayın.  
  
-   Bir arabirim erişimcisini bir gövde yok.  
  
 Bu nedenle, amacı erişimci, dizin oluşturucu salt okunur, salt okunur veya sadece yazılabilir olup olmadığını belirtmektir.  
  
 Arabirim dizin oluşturucu erişimci örneği verilmiştir:  
  
 [!code-csharp[csProgGuideIndexers#3](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/indexers-in-interfaces_1.cs)]  
  
 Bir dizin oluşturucu imzasının aynı arabirimde bildirilen tüm diğer dizin imzalarını farklı olmalıdır.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, arabirim dizin oluşturucuları uygulamak gösterilmektedir.  
  
 [!code-csharp[csProgGuideIndexers#4](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/indexers-in-interfaces_2.cs)]  
  
 Önceki örnekte, arabirim üyesini tam olarak nitelenmiş adını kullanarak açık arabirim üyesi uygulaması kullanabilirsiniz. Örneğin:  
  
```  
string ISomeInterface.this[int index]   
{   
}   
```  
  
 Ancak tam nitelikli ad, yalnızca aynı dizin oluşturucu imzaya sahip birden fazla arabirim sınıfı uygulanırken belirsizlik önlemek için gereklidir. Örneğin, bir `Employee` sınıf iki arabirim uygulama `ICitizen` ve `IEmployee`, ve her iki arabirimde aynı dizin oluşturucu imzası, açık arabirim üyesi uygulaması gereklidir. Diğer bir deyişle, aşağıdaki dizin oluşturucu bildirimi:  
  
```  
string IEmployee.this[int index]   
{   
}   
```  
  
 Dizin Oluşturucu üzerinde uygulayan `IEmployee` arabirimi, aşağıdaki bildirim yandan:  
  
```  
string ICitizen.this[int index]
{   
}   
```  
  
 Dizin Oluşturucu üzerinde uygulayan `ICitizen` arabirimi.  
  
## <a name="see-also"></a>Ayrıca Bkz.

- [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)  
- [Dizin Oluşturucular](../../../csharp/programming-guide/indexers/index.md)  
- [Özellikler](../../../csharp/programming-guide/classes-and-structs/properties.md)  
- [Arabirimler](../../../csharp/programming-guide/interfaces/index.md)
