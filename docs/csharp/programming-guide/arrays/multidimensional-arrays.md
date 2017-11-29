---
title: "Çok Boyutlu Diziler (C# Programlama Kılavuzu)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- arrays [C#], multidimensional
- multidimensional arrays [C#]
ms.assetid: 020ce02e-7dff-4273-8e53-bf0b33747232
caps.latest.revision: "16"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: ab3a93c21ddb9541a6149967605b851ea5a50a3c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="multidimensional-arrays-c-programming-guide"></a>Çok Boyutlu Diziler (C# Programlama Kılavuzu)
Diziler, birden fazla boyuta sahip olabilir. Örneğin, aşağıdaki bildirimi dört satır ve iki sütun iki boyutlu bir dizi oluşturur.  
  
 [!code-csharp[csProgGuideArrays#11](../../../csharp/programming-guide/arrays/codesnippet/CSharp/multidimensional-arrays_1.cs)]  
  
 Üç dizisi şu bildirimi oluşturur boyutları, 4, 2 ve 3.  
  
 [!code-csharp[csProgGuideArrays#12](../../../csharp/programming-guide/arrays/codesnippet/CSharp/multidimensional-arrays_2.cs)]  
  
## <a name="array-initialization"></a>Dizi başlatma  
 Aşağıdaki örnekte gösterildiği gibi bildirimi bağlı dizi başlatabilirsiniz.  
  
 [!code-csharp[csProgGuideArrays#13](../../../csharp/programming-guide/arrays/codesnippet/CSharp/multidimensional-arrays_3.cs)]  
  
 Dizi derecesini belirtmeden de başlatabilirsiniz.  
  
 [!code-csharp[csProgGuideArrays#14](../../../csharp/programming-guide/arrays/codesnippet/CSharp/multidimensional-arrays_4.cs)]  
  
 Bir dizi değişkeni başlatma olmadan bildirmek isterseniz, kullanmalısınız `new` bir dizi değişkenine atamak için işleci. Kullanımını `new` aşağıdaki örnekte gösterilir.  
  
 [!code-csharp[csProgGuideArrays#15](../../../csharp/programming-guide/arrays/codesnippet/CSharp/multidimensional-arrays_5.cs)]  
  
 Aşağıdaki örnek bir değer belirli bir dizi öğesine atar.  
  
 [!code-csharp[csProgGuideArrays#16](../../../csharp/programming-guide/arrays/codesnippet/CSharp/multidimensional-arrays_6.cs)]  
  
 Benzer şekilde, aşağıdaki örnekte belirli bir dizi öğenin değerini alır ve değişkenine atar `elementValue`.  
  
 [!code-csharp[csProgGuideArrays#42](../../../csharp/programming-guide/arrays/codesnippet/CSharp/multidimensional-arrays_7.cs)]  
  
 Aşağıdaki kod örneğinde dizi öğeleri (dışında basit Diziler) varsayılan değerlerine başlatır.  
  
 [!code-csharp[csProgGuideArrays#17](../../../csharp/programming-guide/arrays/codesnippet/CSharp/multidimensional-arrays_8.cs)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [C# programlama kılavuzu](../../../csharp/programming-guide/index.md)  
 [Diziler](../../../csharp/programming-guide/arrays/index.md)  
 [Tek boyutlu diziler](../../../csharp/programming-guide/arrays/single-dimensional-arrays.md)  
 [Basit diziler](../../../csharp/programming-guide/arrays/jagged-arrays.md)
