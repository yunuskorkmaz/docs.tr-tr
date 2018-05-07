---
title: Dizilerle foreach kullanma (C# Programlama Kılavuzu)
ms.date: 07/20/2015
helpviewer_keywords:
- arrays [C#], foreach
- foreach statement [C#], using with arrays
ms.assetid: 5f2da2a9-1f56-4de5-94cc-e07f4f7a0244
ms.openlocfilehash: 8511d9dd3b7155d2f6bca229f264071b54ed173b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="using-foreach-with-arrays-c-programming-guide"></a>Dizilerle foreach kullanma (C# Programlama Kılavuzu)
C# ayrıca sağlar [foreach](../../../csharp/language-reference/keywords/foreach-in.md) deyimi. Bu deyim, bir dizinin veya herhangi bir sıralanabilir koleksiyonun öğeleri arasında yineleme yapmak için basit ve temiz bir yol sağlar. `foreach` Deyimini öğeleri, genellikle 0 öğesinden son dizi ya da koleksiyon tür numaralandırıcı tarafından döndürülen sırayla işler. Örneğin, aşağıdaki kod olarak adlandırılan bir dizi oluşturur `numbers` ve onunla dolaşır `foreach` deyimi:  
  
 [!code-csharp[csProgGuideArrays#28](../../../csharp/programming-guide/arrays/codesnippet/CSharp/using-foreach-with-arrays_1.cs)]  
  
 Çok boyutlu dizilerle, öğeler boyunca yineleme yapmak için aynı yöntemi kullanabilirsiniz, örneğin:  
  
 [!code-csharp[csProgGuideArrays#29](../../../csharp/programming-guide/arrays/codesnippet/CSharp/using-foreach-with-arrays_2.cs)]  
  
 Ancak, çok boyutlu diziler ile iç içe bir kullanarak [için](../../../csharp/language-reference/keywords/for.md) döngü dizi öğeleri üzerinde daha fazla denetim sağlar.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Array>  
 [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)  
 [Diziler](../../../csharp/programming-guide/arrays/index.md)  
 [Tek Boyutlu Diziler](../../../csharp/programming-guide/arrays/single-dimensional-arrays.md)  
 [Çok Boyutlu Diziler](../../../csharp/programming-guide/arrays/multidimensional-arrays.md)  
 [Düzensiz Diziler](../../../csharp/programming-guide/arrays/jagged-arrays.md)
