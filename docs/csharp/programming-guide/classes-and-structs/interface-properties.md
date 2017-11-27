---
title: "Arabirim Özellikleri (C# Programlama Kılavuzu)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- properties [C#], on interfaces
- interfaces [C#], properties
ms.assetid: 6503e9ed-33d7-44ec-b4c1-cc16c084b795
caps.latest.revision: "13"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 1da48adf73cccb28d9cff641948db52b40b8c1bb
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="interface-properties-c-programming-guide"></a>Arabirim Özellikleri (C# Programlama Kılavuzu)
Özellikler bildirilebilir bir [arabirimi](../../../csharp/language-reference/keywords/interface.md). Arabirim dizin oluşturucu erişimci örneği verilmiştir:  
  
 [!code-csharp[csProgGuideProperties#14](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/interface-properties_1.cs)]  
  
 Bir arabirim özelliği erişimcisi gövde yok. Bu nedenle, özelliğin okuma-yazma, salt okunur veya sadece yazılabilir olup olmadığını belirtmek için erişimciler amacı budur.  
  
## <a name="example"></a>Örnek  
 Bu örnekte, arabirim `IEmployee` bir okuma-yazma özelliği var. `Name`ve salt okunur bir özellik `Counter`. Sınıf `Employee` uygulayan `IEmployee` arabirim ve bu iki özellik kullanır. Programın adını yeni bir çalışan ve çalışanların geçerli sayısını okur ve çalışan adını ve hesaplanan çalışan numarasını görüntüler.  
  
 Üye bildirilmedi arabirimi başvuran özelliği tam adını kullanabilirsiniz. Örneğin:  
  
 [!code-csharp[csProgGuideProperties#16](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/interface-properties_2.cs)]  
  
 Bu adlı [açık arabirim uygulaması](../../../csharp/programming-guide/interfaces/explicit-interface-implementation.md). Örneğin, varsa sınıfı `Employee` iki arabirimler uygulama `ICitizen` ve `IEmployee` ve her iki arabirimde `Name` özelliği, açık arabirim üye uygulaması gerekli olacak. Diğer bir deyişle, aşağıdaki özellik bildirimi:  
  
 [!code-csharp[csProgGuideProperties#16](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/interface-properties_2.cs)]  
  
 uygulayan `Name` özellikte `IEmployee` arabirimi, aşağıdaki bildirimi sırasında:  
  
 [!code-csharp[csProgGuideProperties#17](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/interface-properties_3.cs)]  
  
 uygulayan `Name` özellikte `ICitizen` arabirimi.  
  
 [!code-csharp[csProgGuideProperties#15](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/interface-properties_4.cs)]  
  
  **`210 Hazem Abolrous`**    
## <a name="sample-output"></a>Örnek Çıktı  
 `Enter number of employees: 210`  
  
 `Enter the name of the new employee: Hazem Abolrous`  
  
 `The employee information:`  
  
 `Employee number: 211`  
  
 `Employee name: Hazem Abolrous`  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [C# programlama kılavuzu](../../../csharp/programming-guide/index.md)  
 [Özellikleri](../../../csharp/programming-guide/classes-and-structs/properties.md)  
 [Özellikleri kullanma](../../../csharp/programming-guide/classes-and-structs/using-properties.md)  
 [Özellikler ve dizin oluşturucular arasında karşılaştırma](../../../csharp/programming-guide/indexers/comparison-between-properties-and-indexers.md)  
 [Dizin oluşturucular](../../../csharp/programming-guide/indexers/index.md)  
 [Arabirimleri](../../../csharp/programming-guide/interfaces/index.md)
