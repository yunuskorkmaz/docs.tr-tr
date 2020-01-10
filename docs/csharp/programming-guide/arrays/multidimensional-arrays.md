---
title: Çok boyutlu diziler C# -Programlama Kılavuzu
ms.date: 07/20/2015
helpviewer_keywords:
- arrays [C#], multidimensional
- multidimensional arrays [C#]
ms.assetid: 020ce02e-7dff-4273-8e53-bf0b33747232
ms.openlocfilehash: eb49f4386b6106328f1613b5ec70794ac26fc9b7
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75715047"
---
# <a name="multidimensional-arrays-c-programming-guide"></a>Çok Boyutlu Diziler (C# Programlama Kılavuzu)

Diziler birden fazla boyuta sahip olabilir. Örneğin, aşağıdaki bildirim dört satırlık ve iki sütundan oluşan iki boyutlu bir dizi oluşturur.  
  
 [!code-csharp[csProgGuideArrays#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#11)]  
  
 Aşağıdaki bildirim üç boyutlu bir dizi oluşturur, 4, 2 ve 3.  
  
 [!code-csharp[csProgGuideArrays#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#12)]  
  
## <a name="array-initialization"></a>Dizi başlatma

 Aşağıdaki örnekte gösterildiği gibi, bildirimi üzerinde diziyi başlatabilirsiniz.  
  
 [!code-csharp[csProgGuideArrays#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#13)]  
  
 Ayrıca, sırası belirtmeden diziyi başlatabilirsiniz.  
  
 [!code-csharp[csProgGuideArrays#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#14)]  
  
 Başlatma olmadan bir dizi değişkeni tanımlamayı seçerseniz, değişkenine bir dizi atamak için `new` işlecini kullanmanız gerekir. `new` kullanımı aşağıdaki örnekte gösterilmiştir.  
  
 [!code-csharp[csProgGuideArrays#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#15)]  
  
 Aşağıdaki örnek, belirli bir dizi öğesine bir değer atar.  
  
 [!code-csharp[csProgGuideArrays#16](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#16)]  
  
 Benzer şekilde, aşağıdaki örnek, belirli bir dizi öğesinin değerini alır ve onu `elementValue`değişkenine atar.  
  
 [!code-csharp[csProgGuideArrays#42](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#42)]  
  
 Aşağıdaki kod örneği, dizi öğelerini varsayılan değerlere (pürüzlü Diziler hariç) başlatır.  
  
 [!code-csharp[csProgGuideArrays#17](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#17)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../index.md)
- [Diziler](./index.md)
- [Tek Boyutlu Diziler](./single-dimensional-arrays.md)
- [Düzensiz Diziler](./jagged-arrays.md)
