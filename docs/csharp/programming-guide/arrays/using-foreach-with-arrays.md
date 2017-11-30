---
title: "Dizilerle foreach kullanma (C# Programlama Kılavuzu)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- arrays [C#], foreach
- foreach statement [C#], using with arrays
ms.assetid: 5f2da2a9-1f56-4de5-94cc-e07f4f7a0244
caps.latest.revision: "14"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 797cb9a63a5e1009b170b2afda8634bd21a50035
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="using-foreach-with-arrays-c-programming-guide"></a>Dizilerle foreach kullanma (C# Programlama Kılavuzu)
C# ayrıca sağlar [foreach](../../../csharp/language-reference/keywords/foreach-in.md) deyimi. Bu deyim, bir dizinin veya herhangi bir sıralanabilir koleksiyonun öğeleri arasında yineleme yapmak için basit ve temiz bir yol sağlar. `foreach` Deyimini öğeleri, genellikle 0 öğesinden son dizi ya da koleksiyon tür numaralandırıcı tarafından döndürülen sırayla işler. Örneğin, aşağıdaki kod olarak adlandırılan bir dizi oluşturur `numbers` ve onunla dolaşır `foreach` deyimi:  
  
 [!code-csharp[csProgGuideArrays#28](../../../csharp/programming-guide/arrays/codesnippet/CSharp/using-foreach-with-arrays_1.cs)]  
  
 Çok boyutlu dizilerle, öğeler boyunca yineleme yapmak için aynı yöntemi kullanabilirsiniz, örneğin:  
  
 [!code-csharp[csProgGuideArrays#29](../../../csharp/programming-guide/arrays/codesnippet/CSharp/using-foreach-with-arrays_2.cs)]  
  
 Ancak, çok boyutlu diziler ile iç içe bir kullanarak [için](../../../csharp/language-reference/keywords/for.md) döngü dizi öğeleri üzerinde daha fazla denetim sağlar.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Array>  
 [C# programlama kılavuzu](../../../csharp/programming-guide/index.md)  
 [Diziler](../../../csharp/programming-guide/arrays/index.md)  
 [Tek boyutlu diziler](../../../csharp/programming-guide/arrays/single-dimensional-arrays.md)  
 [Çok boyutlu diziler](../../../csharp/programming-guide/arrays/multidimensional-arrays.md)  
 [Basit diziler](../../../csharp/programming-guide/arrays/jagged-arrays.md)
