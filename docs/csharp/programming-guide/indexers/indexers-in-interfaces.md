---
title: Arabirimlerde Dizin oluşturucular- C# Programlama Kılavuzu
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- indexers [C#], in interfaces
- accessors [C#], indexers
ms.assetid: e16b54bd-4a83-4f52-bd75-65819fca79e8
ms.openlocfilehash: cea8d157e89597ddf4633cf7f7d3df7044db9ec7
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69589446"
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
  
```  
string ISomeInterface.this[int index]   
{   
}   
```  
  
 Ancak, tam adı yalnızca, sınıf aynı Dizin Oluşturucu imzasına sahip birden fazla arabirim uygularken karışıklığı önlemek için gereklidir. Örneğin, bir `Employee` sınıf iki `ICitizen` arabirim `IEmployee`uygusa ve her iki arabirimde de aynı Dizin Oluşturucu imzası varsa, açık arabirim üye uygulaması gereklidir. Diğer bir deyişle, aşağıdaki Dizin Oluşturucu bildirimi:  
  
```  
string IEmployee.this[int index]   
{   
}   
```  
  
 `IEmployee` arabirim üzerinde dizin oluşturucuyu uygular, aşağıdaki bildirim:  
  
```  
string ICitizen.this[int index]
{   
}   
```  
  
 `ICitizen` arabirimindeki Dizin oluşturucuyu uygular.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../index.md)
- [Dizin Oluşturucular](./index.md)
- [Özellikler](../classes-and-structs/properties.md)
- [Arabirimler](../interfaces/index.md)
