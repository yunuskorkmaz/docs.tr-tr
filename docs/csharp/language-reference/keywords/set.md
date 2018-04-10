---
title: set (C# Başvurusu)
ms.date: 03/10/2017
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- set
- set_CSharpKeyword
helpviewer_keywords:
- set keyword [C#]
ms.assetid: 30d7e4e5-cc2e-4635-a597-14a724879619
caps.latest.revision: 14
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: b810280724dcf608859bfa455947a75ce64b7abe
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="set-c-reference"></a>set (C# Başvurusu)
`set` Anahtar sözcüğü tanımlayan bir *erişimci* yöntemi bir özellik ya da özellik veya dizin oluşturucu öğesi için bir değer atar dizin oluşturucu. Daha fazla bilgi ve örnekler için bkz: [özellikleri](../../../csharp/programming-guide/classes-and-structs/properties.md), [Auto-Implemented özellikleri](../../../csharp/programming-guide/classes-and-structs/auto-implemented-properties.md), ve [dizin oluşturucular](../../../csharp/programming-guide/indexers/index.md).  
  
Aşağıdaki örnek, her ikisi de tanımlar bir `get` ve `set` adlı bir özellik için erişimci `Seconds`. Adlı özel bir alan kullanan `_seconds` özellik değeri yedeklenir.  
 
 [!code-csharp[set#1](../../../../samples/snippets/csharp/language-reference/keywords/get/get-1.cs)]  

Genellikle, `set` erişimci önceki örnekte olduğu gibi bir değer döndüren tek bir deyimde oluşur. C# 7 ile başlayan, uygulayabileceğiniz `set` bir ifade bodied üye olarak erişimcisi. Aşağıdaki örnek hem de uygulayan `get` ve `set` erişimciler ifade bodied üye olarak.

 [!code-csharp[set#3](../../../../samples/snippets/csharp/language-reference/keywords/get/get-3.cs)]   
    
Basit durumlarda için bir özelliğin `get` ve `set` erişimciler ayarlama veya özel yedekleme alanını değerinde alma daha diğer işlemi gerçekleştirmek, otomatik uygulanan özellikler için C# Derleyici 's desteğinin avantajından yararlanabilirsiniz. Aşağıdaki örnek uygulayan `Hours` otomatik uygulanan bir özellik olarak. 
  
 [!code-csharp[set#2](../../../../samples/snippets/csharp/language-reference/keywords/get/get-2.cs)]  
    
## <a name="c-language-specification"></a>C# Dil Belirtimi  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [C# başvurusu](../../../csharp/language-reference/index.md)  
 [C# programlama kılavuzu](../../../csharp/programming-guide/index.md)  
 [C# anahtar sözcükleri](../../../csharp/language-reference/keywords/index.md)  
 [Özellikleri](../../../csharp/programming-guide/classes-and-structs/properties.md)
