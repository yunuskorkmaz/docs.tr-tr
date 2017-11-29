---
title: "Parametreleri Geçirme (C# Programlama Kılavuzu)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- parameters [C#], passing
- passing parameters [C#]
- arguments [C#]
- methods [C#], passing parameters
- C# language, method parameters
ms.assetid: a5c3003f-7441-4710-b8b1-c79de77e0b77
caps.latest.revision: "17"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: d9e0e06d67f9da39c6b55f91e35d4a75b43353f3
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="passing-parameters-c-programming-guide"></a>Parametreleri Geçirme (C# Programlama Kılavuzu)
C# ' ta bağımsız değişken parametreleri değere veya başvuruya göre geçirilebilir. Başvuruya göre geçirme etkinleştirir işlevi üyeleri, yöntemler, özellikler, dizin oluşturucular, işleçler ve parametre değerini değiştirin ve bu değişikliği oluşturucular arama ortamda kalır. Başvuruya göre bir parametre geçirmek için kullanmak `ref` veya `out` anahtar sözcüğü. Basitlik, yalnızca için `ref` anahtar sözcüğü, bu konudaki örnekler kullanılıyor. Arasındaki farklar hakkında daha fazla bilgi için `ref` ve `out`, bkz: [ref](../../../csharp/language-reference/keywords/ref.md), [çıkışı](../../../csharp/language-reference/keywords/out.md), ve [kullanarak dizileri geçirme ref ve çıkış](../../../csharp/programming-guide/arrays/passing-arrays-using-ref-and-out.md).  
  
 Aşağıdaki örnek, değer ve başvuru parametreleri arasındaki fark gösterilmektedir.  
  
 [!code-csharp[csProgGuideParameters#10](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/passing-parameters_1.cs)]  
  
 Daha fazla bilgi için aşağıdaki konulara bakın:  
  
-   [Değer türü parametrelerini geçirme](../../../csharp/programming-guide/classes-and-structs/passing-value-type-parameters.md)  
  
-   [Başvuru türü parametreleri geçirme](../../../csharp/programming-guide/classes-and-structs/passing-reference-type-parameters.md)  
  
## <a name="c-language-specification"></a>C# Dil Belirtimi  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [C# programlama kılavuzu](../../../csharp/programming-guide/index.md)  
 [Yöntemleri](../../../csharp/programming-guide/classes-and-structs/methods.md)
