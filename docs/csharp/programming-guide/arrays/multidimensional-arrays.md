---
title: Çok Boyutlu Diziler - C# Programlama Kılavuzu
ms.date: 07/20/2015
helpviewer_keywords:
- arrays [C#], multidimensional
- multidimensional arrays [C#]
ms.assetid: 020ce02e-7dff-4273-8e53-bf0b33747232
ms.openlocfilehash: ee5fae36ff844fadad7e1b6a766020319b67a83c
ms.sourcegitcommit: 348bb052d5cef109a61a3d5253faa5d7167d55ac
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/22/2020
ms.locfileid: "82021749"
---
# <a name="multidimensional-arrays-c-programming-guide"></a>Çok Boyutlu Diziler (C# Programlama Kılavuzu)

Dizilerin birden fazla boyutu olabilir. Örneğin, aşağıdaki bildirim dört satır ve iki sütundan oluşan iki boyutlu bir dizi oluşturur.  
  
 [!code-csharp[csProgGuideArrays#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#11)]  
  
 Aşağıdaki bildirim, 4, 2 ve 3 olmak üzere üç boyutlu bir dizi oluşturur.  
  
 [!code-csharp[csProgGuideArrays#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#12)]  
  
## <a name="array-initialization"></a>Dizi Başlatma

 Aşağıdaki örnekte gösterildiği gibi, diziyi bildirim üzerine başlatma yapabilirsiniz.  
  
 [!code-csharp[csProgGuideArrays#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#13)]  
  
 Sıralamayı belirtmeden diziyi de başharfe alabilirsiniz.  
  
 [!code-csharp[csProgGuideArrays#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#14)]  
  
 Bir dizi değişkenini başlatma olmadan bildirmeyi seçerseniz, değişkene bir dizi atamak için `new` işleci kullanmanız gerekir. Kullanımı `new` aşağıdaki örnekte gösterilmiştir.  
  
 [!code-csharp[csProgGuideArrays#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#15)]  
  
 Aşağıdaki örnek, belirli bir dizi öğesine bir değer atar.  
  
 [!code-csharp[csProgGuideArrays#16](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#16)]  
  
 Benzer şekilde, aşağıdaki örnek belirli bir dizi öğesinin değerini `elementValue`alır ve değişkene atar.  
  
 [!code-csharp[csProgGuideArrays#42](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#42)]  
  
 Aşağıdaki kod örneği, dizi öğelerini varsayılan değerlere (pürüzlü diziler hariç) başlarar.  
  
 [!code-csharp[csProgGuideArrays#17](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#17)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../index.md)
- [Diziler](./index.md)
- [Tek Boyutlu Diziler](./single-dimensional-arrays.md)
- [Düzensiz Diziler](./jagged-arrays.md)
