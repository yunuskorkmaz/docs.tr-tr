---
title: interface (C# Başvurusu)
ms.date: 07/20/2015
f1_keywords:
- interface_CSharpKeyword
helpviewer_keywords:
- interface keyword [C#]
ms.assetid: 7da38e81-4f99-4bc5-b07d-c986b687eeba
ms.openlocfilehash: 0320b1e287f8c7a3eb7751b68b40120f74e8f61c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33266548"
---
# <a name="interface-c-reference"></a>interface (C# Başvurusu)
Bir arabirim yalnızca imzalarını içerir [yöntemleri](../../../csharp/programming-guide/classes-and-structs/methods.md), [özellikleri](../../../csharp/programming-guide/classes-and-structs/properties.md), [olayları](../../../csharp/programming-guide/events/index.md) veya [dizin oluşturucular](../../../csharp/programming-guide/indexers/index.md). Ara birimi uygulayan bir sınıfın veya yapının, ara birim tanımında belirtilen ara birim üyelerini uygulaması gerekir. Aşağıdaki örnekte `ImplementationClass` sınıfının, parametresi olmayan ve `SampleMethod`'i döndüren `void` adlı bir yöntemi uygulaması gerekir.  
  
 Daha fazla bilgi ve örnekler için bkz: [arabirimleri](../../../csharp/programming-guide/interfaces/index.md).  
  
## <a name="example"></a>Örnek  
 [!code-csharp[csrefKeywordsTypes#14](../../../csharp/language-reference/keywords/codesnippet/CSharp/interface_1.cs)]  
  
 Ara birim, bir ad alanının veya bir sınıfın üyesi olabilir ve aşağıdaki üyelerin imzalarını içerebilir:  
  
-   [Yöntemler](../../../csharp/programming-guide/classes-and-structs/methods.md)  
  
-   [Özellikler](../../../csharp/programming-guide/classes-and-structs/using-properties.md)  
  
-   [Dizin Oluşturucular](../../../csharp/programming-guide/indexers/using-indexers.md)  
  
-   [Olaylar](../../../csharp/language-reference/keywords/event.md)  
  
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
 [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)  
 [C# Anahtar Sözcükleri](../../../csharp/language-reference/keywords/index.md)  
 [Başvuru Türleri](../../../csharp/language-reference/keywords/reference-types.md)  
 [Arabirimler](../../../csharp/programming-guide/interfaces/index.md)  
 [Özellikleri Kullanma](../../../csharp/programming-guide/classes-and-structs/using-properties.md)  
 [Dizin Oluşturucular Kullanma](../../../csharp/programming-guide/indexers/using-indexers.md)  
 [class](../../../csharp/language-reference/keywords/class.md)  
 [struct](../../../csharp/language-reference/keywords/struct.md)  
 [Arabirimler](../../../csharp/programming-guide/interfaces/index.md)
