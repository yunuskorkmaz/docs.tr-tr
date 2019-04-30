---
title: Çok boyutlu diziler - C# Programlama Kılavuzu
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- arrays [C#], multidimensional
- multidimensional arrays [C#]
ms.assetid: 020ce02e-7dff-4273-8e53-bf0b33747232
ms.openlocfilehash: df9063d0616b72ad15c9c48fa4459a6dc98b77c1
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61683931"
---
# <a name="multidimensional-arrays-c-programming-guide"></a>Çok Boyutlu Diziler (C# Programlama Kılavuzu)

Diziler, birden fazla boyuta sahip olabilir. Örneğin, aşağıdaki bildirimi dört satır ve iki sütunlu iki boyutlu bir dizi oluşturur.  
  
 [!code-csharp[csProgGuideArrays#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#11)]  
  
 Aşağıdaki bildirim üç bir dizi oluşturur boyutları, 4, 2 ve 3.  
  
 [!code-csharp[csProgGuideArrays#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#12)]  
  
## <a name="array-initialization"></a>Dizi başlatma

 Aşağıdaki örnekte gösterildiği gibi dizi bildirimi üzerine başlatabilirsiniz.  
  
 [!code-csharp[csProgGuideArrays#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#13)]  
  
 Dizi boyut belirtilmeden de başlatabilirsiniz.  
  
 [!code-csharp[csProgGuideArrays#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#14)]  
  
 Bir dizi değişkeni başlatma olmadan belirtmek isterseniz, kullanmalısınız `new` dizi değişkenine atamak için işleç. Kullanımını `new` aşağıdaki örnekte gösterilmiştir.  
  
 [!code-csharp[csProgGuideArrays#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#15)]  
  
 Aşağıdaki örnek, belirli bir dizi öğesine bir değer atar.  
  
 [!code-csharp[csProgGuideArrays#16](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#16)]  
  
 Benzer şekilde, aşağıdaki örnekte belirli bir dizi öğenin değerini alır ve değişkenine atar `elementValue`.  
  
 [!code-csharp[csProgGuideArrays#42](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#42)]  
  
 Aşağıdaki kod örneği, dizi öğeleri (hariç basit Diziler) varsayılan değerlerine başlatır.  
  
 [!code-csharp[csProgGuideArrays#17](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#17)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)
- [Diziler](../../../csharp/programming-guide/arrays/index.md)
- [Tek Boyutlu Diziler](../../../csharp/programming-guide/arrays/single-dimensional-arrays.md)
- [Düzensiz Diziler](../../../csharp/programming-guide/arrays/jagged-arrays.md)
