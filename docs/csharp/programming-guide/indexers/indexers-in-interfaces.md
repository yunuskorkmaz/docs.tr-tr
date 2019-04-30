---
title: Arabirimlerdeki dizin - C# Programlama Kılavuzu
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- indexers [C#], in interfaces
- accessors [C#], indexers
ms.assetid: e16b54bd-4a83-4f52-bd75-65819fca79e8
ms.openlocfilehash: c56369b28f8e1bab1ca8e8c13ebd9710c8f1d9fb
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61679836"
---
# <a name="indexers-in-interfaces-c-programming-guide"></a>Arabirimlerdeki Dizin Oluşturucular (C# Programlama Kılavuzu)
Dizin oluşturucular bildirilebilir bir [arabirimi](../../../csharp/language-reference/keywords/interface.md). Arabirim dizin oluşturucuları erişicilerini erişicilerini farklı [sınıfı](../../../csharp/language-reference/keywords/class.md) dizin oluşturucuları aşağıdaki yollarla:  
  
- Arabirimi erişimcileri değiştiriciler kullanmayın.  
  
- Bir arabirim erişimcisini bir gövde yok.  
  
 Bu nedenle, amacı erişimci, dizin oluşturucu salt okunur, salt okunur veya sadece yazılabilir olup olmadığını belirtmektir.  
  
 Arabirim dizin oluşturucu erişimci örneği verilmiştir:  
  
 [!code-csharp[csProgGuideIndexers#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideIndexers/CS/Indexers.cs#3)]  
  
 Bir dizin oluşturucu imzasının aynı arabirimde bildirilen tüm diğer dizin imzalarını farklı olmalıdır.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, arabirim dizin oluşturucuları uygulamak gösterilmektedir.  
  
 [!code-csharp[csProgGuideIndexers#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideIndexers/CS/Indexers.cs#4)]  
  
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
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)
- [Dizin Oluşturucular](../../../csharp/programming-guide/indexers/index.md)
- [Özellikler](../../../csharp/programming-guide/classes-and-structs/properties.md)
- [Arabirimler](../../../csharp/programming-guide/interfaces/index.md)
