---
title: interface (C# Başvurusu)
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- interface_CSharpKeyword
helpviewer_keywords:
- interface keyword [C#]
ms.assetid: 7da38e81-4f99-4bc5-b07d-c986b687eeba
caps.latest.revision: 29
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: aba9ee66a90216066a47f22e251182caad465818
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="interface-c-reference"></a>interface (C# Başvurusu)
Bir arabirim yalnızca imzalarını içerir [yöntemleri](../../../csharp/programming-guide/classes-and-structs/methods.md), [özellikleri](../../../csharp/programming-guide/classes-and-structs/properties.md), [olayları](../../../csharp/programming-guide/events/index.md) veya [dizin oluşturucular](../../../csharp/programming-guide/indexers/index.md). Ara birimi uygulayan bir sınıfın veya yapının, ara birim tanımında belirtilen ara birim üyelerini uygulaması gerekir. Aşağıdaki örnekte `ImplementationClass` sınıfının, parametresi olmayan ve `SampleMethod`'i döndüren `void` adlı bir yöntemi uygulaması gerekir.  
  
 Daha fazla bilgi ve örnekler için bkz: [arabirimleri](../../../csharp/programming-guide/interfaces/index.md).  
  
## <a name="example"></a>Örnek  
 [!code-csharp[csrefKeywordsTypes#14](../../../csharp/language-reference/keywords/codesnippet/CSharp/interface_1.cs)]  
  
 Ara birim, bir ad alanının veya bir sınıfın üyesi olabilir ve aşağıdaki üyelerin imzalarını içerebilir:  
  
-   [Yöntemleri](../../../csharp/programming-guide/classes-and-structs/methods.md)  
  
-   [Özellikleri](../../../csharp/programming-guide/classes-and-structs/using-properties.md)  
  
-   [Dizin oluşturucular](../../../csharp/programming-guide/indexers/using-indexers.md)  
  
-   [Olayları](../../../csharp/language-reference/keywords/event.md)  
  
 Bir ara birim, bir veya daha fazla temel ara birimden devralınabilir.  
  
 Bir temel tür listesi temel bir sınıfı ve ara birimleri içerdiğinde, temel sınıfın listede ilk sırada olması gerekir.  
  
 Bir ara birimi uygulayan bir sınıf, o ara birimin üyelerini açıkça uygulayabilir. Açıkça uygulanan bir üyeye, bir sınıfın örneği üzerinden erişilemez, yalnızca ara birimin bir örneği üzerinden erişilebilir.  
  
 Daha fazla ayrıntı ve açık arabirim uygulaması üzerinde kod örnekleri için bkz: [açık arabirim uygulaması](../../../csharp/programming-guide/interfaces/explicit-interface-implementation.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, ara birim uygulamasını gösterir. Bu örnekte, ara birim özellik bildirimini, sınıf ise uygulamayı içerir. `IPoint` öğesini uygulayan bir sınıfın herhangi bir örneği `x` ve `y` tamsayı özelliklerine sahiptir.  
  
 [!code-csharp[csrefKeywordsTypes#15](../../../csharp/language-reference/keywords/codesnippet/CSharp/interface_2.cs)]  
  
## <a name="c-language-specification"></a>C# Dil Belirtimi  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [C# başvurusu](../../../csharp/language-reference/index.md)  
 [C# programlama kılavuzu](../../../csharp/programming-guide/index.md)  
 [C# anahtar sözcükleri](../../../csharp/language-reference/keywords/index.md)  
 [Başvuru türleri](../../../csharp/language-reference/keywords/reference-types.md)  
 [Arabirimleri](../../../csharp/programming-guide/interfaces/index.md)  
 [Özellikleri kullanma](../../../csharp/programming-guide/classes-and-structs/using-properties.md)  
 [Dizin oluşturucular kullanma](../../../csharp/programming-guide/indexers/using-indexers.md)  
 [sınıfı](../../../csharp/language-reference/keywords/class.md)  
 [yapısı](../../../csharp/language-reference/keywords/struct.md)  
 [Arabirimleri](../../../csharp/programming-guide/interfaces/index.md)
