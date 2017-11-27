---
title: "Arabirimlerdeki Dizin Oluşturucular (C# Programlama Kılavuzu)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- indexers [C#], in interfaces
- accessors [C#], indexers
ms.assetid: e16b54bd-4a83-4f52-bd75-65819fca79e8
caps.latest.revision: "18"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 304f2e037d8df025376d06f229ddd1584f8713b6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="indexers-in-interfaces-c-programming-guide"></a>Arabirimlerdeki Dizin Oluşturucular (C# Programlama Kılavuzu)
Dizin oluşturucular bildirilebilir bir [arabirimi](../../../csharp/language-reference/keywords/interface.md). Arabirim Dizinleyicileri erişimciler erişimci farklı [sınıfı](../../../csharp/language-reference/keywords/class.md) dizin oluşturucular aşağıdaki yollarla:  
  
-   Arabirim erişimciler değiştiricileri kullanmayın.  
  
-   Arabirim erişimci gövde yok.  
  
 Bu nedenle, dizin oluşturucu okuma-yazma, salt okunur veya sadece yazılabilir olduğunu belirtmek için erişimci amacı budur.  
  
 Arabirim dizin oluşturucu erişimci örneği verilmiştir:  
  
 [!code-csharp[csProgGuideIndexers#3](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/indexers-in-interfaces_1.cs)]  
  
 Bir dizin oluşturucu imza aynı arabirimde bildirilen tüm diğer dizin oluşturucular imzalarını farklı olmalıdır.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, arabirim Dizinleyicileri uygulamak gösterilmiştir.  
  
 [!code-csharp[csProgGuideIndexers#4](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/indexers-in-interfaces_2.cs)]  
  
 Önceki örnekte, arabirim üyesini tam adını kullanarak açık arabirim üye uygulaması kullanabilirsiniz. Örneğin:  
  
```  
public string ISomeInterface.this   
{   
}   
```  
  
 Ancak, tam adı, yalnızca sınıf aynı dizin oluşturucu imzaya sahip birden fazla arabirimi uygularken Karışıklığı önlemek için gereklidir. Örneğin, bir `Employee` sınıfı iki arabirim uygulama `ICitizen` ve `IEmployee`, ve her iki arabirimde aynı dizin oluşturucu imza açık arabirim üye uygulaması gereklidir. Diğer bir deyişle, aşağıdaki dizin oluşturucu bildirimi:  
  
```  
public string IEmployee.this   
{   
}   
```  
  
 üzerine dizinleyici uygulayan `IEmployee` arabirimi, aşağıdaki bildirimi sırasında:  
  
```  
public string ICitizen.this   
{   
}   
```  
  
 üzerine dizinleyici uygulayan `ICitizen` arabirimi.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [C# programlama kılavuzu](../../../csharp/programming-guide/index.md)  
 [Dizin oluşturucular](../../../csharp/programming-guide/indexers/index.md)  
 [Özellikleri](../../../csharp/programming-guide/classes-and-structs/properties.md)  
 [Arabirimleri](../../../csharp/programming-guide/interfaces/index.md)
