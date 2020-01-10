---
title: Arabirimlerde Dizin oluşturucular- C# Programlama Kılavuzu
ms.date: 07/20/2015
helpviewer_keywords:
- indexers [C#], in interfaces
- accessors [C#], indexers
ms.assetid: e16b54bd-4a83-4f52-bd75-65819fca79e8
ms.openlocfilehash: 4ac51589ed1680f8484fde797c045d15beed3af9
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75712123"
---
# <a name="indexers-in-interfaces-c-programming-guide"></a>Arabirimlerdeki Dizin Oluşturucular (C# Programlama Kılavuzu)
Dizin oluşturucular bir [arabirimde](../../language-reference/keywords/interface.md)bildirilemez. Arabirim dizin oluşturucularının erişimcileri, [sınıf](../../language-reference/keywords/class.md) dizin oluşturucularının erişimcilerine aşağıdaki yollarla göre farklılık gösterir:  
  
- Arabirim erişimcileri değiştiriciler kullanmaz.  
  
- Arabirim erişimcisinin gövdesi yok.  
  
 Bu nedenle, erişimcinin amacı, dizin oluşturucunun okuma-yazma, salt okunurdur veya salt yazılır olduğunu belirtsağlamaktır.  
  
 Arabirim dizin oluşturucu erişimcisine bir örnek aşağıda verilmiştir:  
  
 [!code-csharp[csProgGuideIndexers#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideIndexers/CS/Indexers.cs#3)]  
  
 Bir dizin oluşturucunun imzası aynı arabirimde belirtilen diğer tüm dizin oluşturucularının imzalarından farklı olmalıdır.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, arabirim dizin oluşturucularının nasıl uygulanacağını gösterir.  
  
 [!code-csharp[csProgGuideIndexers#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideIndexers/CS/Indexers.cs#4)]  
  
 Yukarıdaki örnekte, arabirim üyesinin tam adını kullanarak açık arabirim üye uygulamasını kullanabilirsiniz. Örneğin:  
  
```csharp  
string ISomeInterface.this[int index]   
{   
}   
```  
  
 Ancak, tam adı yalnızca, sınıf aynı Dizin Oluşturucu imzasına sahip birden fazla arabirim uygularken karışıklığı önlemek için gereklidir. Örneğin, bir `Employee` sınıfı iki arabirim uygusa, `ICitizen` ve `IEmployee`ve her iki arabirimde de aynı Dizin Oluşturucu imzası varsa, açık arabirim üye uygulaması gereklidir. Diğer bir deyişle, aşağıdaki Dizin Oluşturucu bildirimi:  
  
```csharp  
string IEmployee.this[int index]   
{   
}   
```  
  
 , aşağıdaki bildirim sırasında `IEmployee` arabiriminde Dizin oluşturucuyu uygular:  
  
```csharp  
string ICitizen.this[int index]
{   
}   
```  
  
 `ICitizen` arabirimindeki Dizin oluşturucuyu uygular.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../index.md)
- [Dizin Oluşturucular](./index.md)
- [Veri Erişimi](../classes-and-structs/properties.md)
- [Arabirimler](../interfaces/index.md)
