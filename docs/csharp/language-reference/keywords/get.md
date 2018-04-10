---
title: get (C# Başvurusu)
ms.date: 03/10/2017
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- get_CSharpKeyword
- get
helpviewer_keywords:
- get keyword [C#]
ms.assetid: a52de048-fbe0-41b0-82ec-8e4ac04d3a71
caps.latest.revision: 11
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: a2e8426e5c5be16be0114b5ccc66f30793ce7dda
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="get-c-reference"></a>get (C# Başvurusu)

`get` Anahtar sözcüğü tanımlayan bir *erişimci* yöntemi bir özellik ya da özellik değeri veya dizin oluşturucu öğesi döndürür. dizin oluşturucu. Daha fazla bilgi için bkz: [özellikleri](../../../csharp/programming-guide/classes-and-structs/properties.md), [Auto-Implemented özellikleri](../../../csharp/programming-guide/classes-and-structs/auto-implemented-properties.md) ve [dizin oluşturucular](../../../csharp/programming-guide/indexers/index.md).  
  
Aşağıdaki örnek, her ikisi de tanımlar bir `get` ve `set` adlı bir özellik için erişimci `Seconds`. Adlı özel bir alan kullanan `_seconds` özellik değeri yedeklenir.  
 
 [!code-csharp[get#1](../../../../samples/snippets/csharp/language-reference/keywords/get/get-1.cs)]  
  
Genellikle, `get` erişimci önceki örnekte olduğu gibi bir değer döndüren tek bir deyimde oluşur. C# 7 ile başlayan, uygulayabileceğiniz `get` bir ifade bodied üye olarak erişimcisi. Aşağıdaki örnek hem de uygulayan `get` ve `set` ifade bodied üye olarak erişimcisi.

 [!code-csharp[get#3](../../../../samples/snippets/csharp/language-reference/keywords/get/get-3.cs)]   
 
Basit durumlarda için bir özelliğin `get` ve `set` erişimciler ayarlama veya özel yedekleme alanını değerinde alma daha diğer işlemi gerçekleştirmek, otomatik uygulanan özellikler için C# Derleyici 's desteğinin avantajından yararlanabilirsiniz. Aşağıdaki örnek uygulayan `Hours` otomatik uygulanan bir özellik olarak. 
  
 [!code-csharp[get#2](../../../../samples/snippets/csharp/language-reference/keywords/get/get-2.cs)]  
  
## <a name="c-language-specification"></a>C# Dil Belirtimi

 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [C# başvurusu](../../../csharp/language-reference/index.md)  
 [C# programlama kılavuzu](../../../csharp/programming-guide/index.md)  
 [C# anahtar sözcükleri](../../../csharp/language-reference/keywords/index.md) [özellikleri](../../../csharp/programming-guide/classes-and-structs/properties.md)
