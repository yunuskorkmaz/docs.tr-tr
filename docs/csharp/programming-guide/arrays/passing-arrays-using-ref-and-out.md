---
title: ref ve out Kullanarak Dizileri Geçirme (C# Programlama Kılavuzu)
ms.date: 07/20/2015
helpviewer_keywords:
- arrays [C#], passing using ref and out
ms.assetid: 6a2b261e-a1cc-49a6-b4f0-6cacae385a1e
ms.openlocfilehash: 8da3bf9f8eede72a7bc3cf8380eab66ca2b56e86
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43526771"
---
# <a name="passing-arrays-using-ref-and-out-c-programming-guide"></a>ref ve out Kullanarak Dizileri Geçirme (C# Programlama Kılavuzu)

Tüm [kullanıma](../../../csharp/language-reference/keywords/out-parameter-modifier.md) parametreleri bir `out` kullanılmadan önce bir dizi türünde bir parametresi atanmalıdır; yani, aranan tarafından atanmalıdır. Örneğin:  
  
 [!code-csharp[csProgGuideArrays#39](../../../csharp/programming-guide/arrays/codesnippet/CSharp/passing-arrays-using-ref-and-out_1.cs)]  
  
 Tüm [ref](../../../csharp/language-reference/keywords/ref.md) parametreleri bir `ref` bir dizi türünde bir parametresi arayan tarafından kesinlikle da atanmalıdır. Bu nedenle, kesinlikle Aranan tarafından atanmasına gerek yoktur. A `ref` bir dizi türünde bir parametresi çağrının bir sonucu olarak değiştirilebilir. Örneğin, bir dizi atanabilir [null](../../../csharp/language-reference/keywords/null.md) değer veya farklı bir dizi olarak başlatılabilir. Örneğin:  
  
 [!code-csharp[csProgGuideArrays#40](../../../csharp/programming-guide/arrays/codesnippet/CSharp/passing-arrays-using-ref-and-out_2.cs)]  
  
 Aşağıdaki iki örnek arasındaki farkı göstermek `out` ve `ref` dizileri yöntemlere geçirirken kullanıldığında.  
  
## <a name="example"></a>Örnek

 Bu örnekte, dizi `theArray` arayanda ( `Main` yöntemi) ve içinde başlatılan `FillArray` yöntemi. Sonra, dizi öğeleri arayana döndürülür ve görüntülenir.  
  
 [!code-csharp[csProgGuideArrays#37](../../../csharp/programming-guide/arrays/codesnippet/CSharp/passing-arrays-using-ref-and-out_3.cs)]

## <a name="example"></a>Örnek

 Bu örnekte, dizi `theArray` arayanda başlatılır ( `Main` yöntemi) ve geçirilen `FillArray` yöntemi kullanarak `ref` parametresi. Bazı dizi öğeleri güncellenir `FillArray` yöntemi. Sonra, dizi öğeleri arayana döndürülür ve görüntülenir.  
  
 [!code-csharp[csProgGuideArrays#38](../../../csharp/programming-guide/arrays/codesnippet/CSharp/passing-arrays-using-ref-and-out_4.cs)]  
  
## <a name="see-also"></a>Ayrıca Bkz.

- [ref](../../../csharp/language-reference/keywords/ref.md)  
- [out parametresi değiştiricisi](../../../csharp/language-reference/keywords/out-parameter-modifier.md)  
- [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)  
- [Diziler](../../../csharp/programming-guide/arrays/index.md)  
- [Tek Boyutlu Diziler](../../../csharp/programming-guide/arrays/single-dimensional-arrays.md)  
- [Çok Boyutlu Diziler](../../../csharp/programming-guide/arrays/multidimensional-arrays.md)  
- [Düzensiz Diziler](../../../csharp/programming-guide/arrays/jagged-arrays.md)
