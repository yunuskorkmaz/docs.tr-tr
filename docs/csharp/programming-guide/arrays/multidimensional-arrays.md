---
title: Çok boyutlu diziler-C# Programlama Kılavuzu
description: C# içindeki diziler birden fazla boyuta sahip olabilir. Bu örnek bildirim dört satırlık ve iki sütundan oluşan iki boyutlu bir dizi oluşturur.
ms.date: 07/20/2015
helpviewer_keywords:
- arrays [C#], multidimensional
- multidimensional arrays [C#]
ms.assetid: 020ce02e-7dff-4273-8e53-bf0b33747232
ms.openlocfilehash: a2f204c0866672b317569fbc620aa8af60829ffd
ms.sourcegitcommit: cf5a800a33de64d0aad6d115ffcc935f32375164
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/20/2020
ms.locfileid: "86475014"
---
# <a name="multidimensional-arrays-c-programming-guide"></a>Çok Boyutlu Diziler (C# Programlama Kılavuzu)

Diziler birden fazla boyuta sahip olabilir. Örneğin, aşağıdaki bildirim dört satırlık ve iki sütundan oluşan iki boyutlu bir dizi oluşturur.  
  
 [!code-csharp[csProgGuideArrays#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#11)]  
  
 Aşağıdaki bildirim üç boyutlu bir dizi oluşturur, 4, 2 ve 3.  
  
 [!code-csharp[csProgGuideArrays#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#12)]  
  
## <a name="array-initialization"></a>Dizi başlatma

 Aşağıdaki örnekte gösterildiği gibi, bildirimi üzerinde diziyi başlatabilirsiniz.  
  
 [!code-csharp[csProgGuideArrays#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#13)]  
  
 Ayrıca, sırası belirtmeden diziyi de başlatabilirsiniz.  
  
 [!code-csharp[csProgGuideArrays#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#14)]  
  
 Başlatma olmadan bir dizi değişkeni tanımlamayı seçerseniz, `new` değişkenine bir dizi atamak için işlecini kullanmanız gerekir. Öğesinin kullanımı `new` Aşağıdaki örnekte gösterilmiştir.  
  
 [!code-csharp[csProgGuideArrays#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#15)]  
  
 Aşağıdaki örnek, belirli bir dizi öğesine bir değer atar.  
  
 [!code-csharp[csProgGuideArrays#16](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#16)]  
  
 Benzer şekilde, aşağıdaki örnek, belirli bir dizi öğesinin değerini alır ve bunu değişkenine atar `elementValue` .  
  
 [!code-csharp[csProgGuideArrays#42](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#42)]  
  
 Aşağıdaki kod örneği, dizi öğelerini varsayılan değerlere (pürüzlü Diziler hariç) başlatır.  
  
 [!code-csharp[csProgGuideArrays#17](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#17)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../index.md)
- [Diziler](./index.md)
- [Tek Boyutlu Diziler](./single-dimensional-arrays.md)
- [Düzensiz Diziler](./jagged-arrays.md)
