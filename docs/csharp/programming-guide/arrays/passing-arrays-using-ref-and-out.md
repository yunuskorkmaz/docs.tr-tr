---
title: "ref ve out Kullanarak Dizileri Geçirme (C# Programlama Kılavuzu)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
helpviewer_keywords:
- arrays [C#], passing using ref and out
ms.assetid: 6a2b261e-a1cc-49a6-b4f0-6cacae385a1e
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 7f2d4e613491b26e82523d230398af3ec34b4d0c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="passing-arrays-using-ref-and-out-c-programming-guide"></a>ref ve out Kullanarak Dizileri Geçirme (C# Programlama Kılavuzu)
Tüm [çıkışı](../../../csharp/language-reference/keywords/out.md) parametreleri, bir `out` kullanılmadan önce bir dizi türü parametresinin atanmalıdır; diğer bir deyişle, aranan tarafından atanmalıdır. Örneğin:  
  
 [!code-csharp[csProgGuideArrays#39](../../../csharp/programming-guide/arrays/codesnippet/CSharp/passing-arrays-using-ref-and-out_1.cs)]  
  
 Tüm [ref](../../../csharp/language-reference/keywords/ref.md) parametreleri, bir `ref` parametresi bir dizi türü, çağıran tarafından kesinlikle da atanmalıdır. Bu nedenle, kesinlikle Aranan tarafından atanmasına gerek yoktur. A `ref` parametresi bir dizi türü, çağrı sonucu olarak değiştirilebilir. Örneğin, dizi atanabilir [null](../../../csharp/language-reference/keywords/null.md) değer veya farklı bir dizi başlatılabilir. Örneğin:  
  
 [!code-csharp[csProgGuideArrays#40](../../../csharp/programming-guide/arrays/codesnippet/CSharp/passing-arrays-using-ref-and-out_2.cs)]  
  
 Aşağıdaki iki örnek arasındaki farkı göstermek `out` ve `ref` yöntemlerine dizileri geçirme içinde kullanıldığında.  
  
## <a name="example"></a>Örnek  
 Bu örnekte, dizi `theArray` çağrı yapan bildirilmiş ( `Main` yöntemi) ve içinde başlatılmış `FillArray` yöntemi. Sonra, dizi öğeleri arayana döndürülür ve görüntülenir.  
  
 [!code-csharp[csProgGuideArrays#37](../../../csharp/programming-guide/arrays/codesnippet/CSharp/passing-arrays-using-ref-and-out_3.cs)]  
  
## <a name="example"></a>Örnek  
 Bu örnekte, dizi `theArray` çağrı yapan başlatıldı ( `Main` yöntemi) ve geçirilen `FillArray` yöntemi kullanarak `ref` parametresi. Dizi öğeleri bazıları uygulamasında güncelleştirilir `FillArray` yöntemi. Sonra, dizi öğeleri arayana döndürülür ve görüntülenir.  
  
 [!code-csharp[csProgGuideArrays#38](../../../csharp/programming-guide/arrays/codesnippet/CSharp/passing-arrays-using-ref-and-out_4.cs)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Ref](../../../csharp/language-reference/keywords/ref.md)  
 [out parametresi değiştiricisi](../../../csharp/language-reference/keywords/out-parameter-modifier.md)  
 [C# programlama kılavuzu](../../../csharp/programming-guide/index.md)  
 [Diziler](../../../csharp/programming-guide/arrays/index.md)  
 [Tek boyutlu diziler](../../../csharp/programming-guide/arrays/single-dimensional-arrays.md)  
 [Çok boyutlu diziler](../../../csharp/programming-guide/arrays/multidimensional-arrays.md)  
 [Basit diziler](../../../csharp/programming-guide/arrays/jagged-arrays.md)
