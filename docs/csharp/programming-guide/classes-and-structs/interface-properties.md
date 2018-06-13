---
title: Arabirim Özellikleri (C# Programlama Kılavuzu)
ms.date: 07/20/2015
helpviewer_keywords:
- properties [C#], on interfaces
- interfaces [C#], properties
ms.assetid: 6503e9ed-33d7-44ec-b4c1-cc16c084b795
ms.openlocfilehash: bfa03c7ebe82f3f6a03666d908a5fa9d4e386172
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33325415"
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
 [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)  
 [Özellikler](../../../csharp/programming-guide/classes-and-structs/properties.md)  
 [Özellikleri Kullanma](../../../csharp/programming-guide/classes-and-structs/using-properties.md)  
 [Özellikler ve Dizin Oluşturucular Arasında Karşılaştırma](../../../csharp/programming-guide/indexers/comparison-between-properties-and-indexers.md)  
 [Dizin Oluşturucular](../../../csharp/programming-guide/indexers/index.md)  
 [Arabirimler](../../../csharp/programming-guide/interfaces/index.md)
