---
title: Çok Boyutlu Diziler (C# Programlama Kılavuzu)
ms.date: 07/20/2015
helpviewer_keywords:
- arrays [C#], multidimensional
- multidimensional arrays [C#]
ms.assetid: 020ce02e-7dff-4273-8e53-bf0b33747232
ms.openlocfilehash: a1d7a0a014c330682316e869f6727082fa3b31ef
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2018
ms.locfileid: "44039614"
---
# <a name="multidimensional-arrays-c-programming-guide"></a>Çok Boyutlu Diziler (C# Programlama Kılavuzu)

Diziler, birden fazla boyuta sahip olabilir. Örneğin, aşağıdaki bildirimi dört satır ve iki sütunlu iki boyutlu bir dizi oluşturur.  
  
 [!code-csharp[csProgGuideArrays#11](../../../csharp/programming-guide/arrays/codesnippet/CSharp/multidimensional-arrays_1.cs)]  
  
 Aşağıdaki bildirim üç bir dizi oluşturur boyutları, 4, 2 ve 3.  
  
 [!code-csharp[csProgGuideArrays#12](../../../csharp/programming-guide/arrays/codesnippet/CSharp/multidimensional-arrays_2.cs)]  
  
## <a name="array-initialization"></a>Dizi başlatma

 Aşağıdaki örnekte gösterildiği gibi dizi bildirimi üzerine başlatabilirsiniz.  
  
 [!code-csharp[csProgGuideArrays#13](../../../csharp/programming-guide/arrays/codesnippet/CSharp/multidimensional-arrays_3.cs)]  
  
 Dizi boyut belirtilmeden de başlatabilirsiniz.  
  
 [!code-csharp[csProgGuideArrays#14](../../../csharp/programming-guide/arrays/codesnippet/CSharp/multidimensional-arrays_4.cs)]  
  
 Bir dizi değişkeni başlatma olmadan belirtmek isterseniz, kullanmalısınız `new` dizi değişkenine atamak için işleç. Kullanımını `new` aşağıdaki örnekte gösterilmiştir.  
  
 [!code-csharp[csProgGuideArrays#15](../../../csharp/programming-guide/arrays/codesnippet/CSharp/multidimensional-arrays_5.cs)]  
  
 Aşağıdaki örnek, belirli bir dizi öğesine bir değer atar.  
  
 [!code-csharp[csProgGuideArrays#16](../../../csharp/programming-guide/arrays/codesnippet/CSharp/multidimensional-arrays_6.cs)]  
  
 Benzer şekilde, aşağıdaki örnekte belirli bir dizi öğenin değerini alır ve değişkenine atar `elementValue`.  
  
 [!code-csharp[csProgGuideArrays#42](../../../csharp/programming-guide/arrays/codesnippet/CSharp/multidimensional-arrays_7.cs)]  
  
 Aşağıdaki kod örneği, dizi öğeleri (hariç basit Diziler) varsayılan değerlerine başlatır.  
  
 [!code-csharp[csProgGuideArrays#17](../../../csharp/programming-guide/arrays/codesnippet/CSharp/multidimensional-arrays_8.cs)]  
  
## <a name="see-also"></a>Ayrıca Bkz.

- [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)  
- [Diziler](../../../csharp/programming-guide/arrays/index.md)  
- [Tek Boyutlu Diziler](../../../csharp/programming-guide/arrays/single-dimensional-arrays.md)  
- [Düzensiz Diziler](../../../csharp/programming-guide/arrays/jagged-arrays.md)
