---
title: Dizileri bağımsız değişkenler olarak - geçirme C# Programlama Kılavuzu
ms.custom: seodec18
ms.date: 07/05/2018
helpviewer_keywords:
- arrays [C#], passing as arguments
ms.assetid: f3a0971e-c87c-4a1f-8262-bc0a3b712772
ms.openlocfilehash: 6e11020491c36349f035abb333aa3396c246dd68
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/11/2018
ms.locfileid: "53245619"
---
# <a name="passing-arrays-as-arguments-c-programming-guide"></a>Dizileri bağımsız değişkenler (C# programlama Kılavuzu) olarak geçirme

Dizileri bağımsız değişkenler olarak yöntemi parametrelerine geçirilebilir. Yöntemi, diziler, başvuru türleri olduğundan, öğelerin değerini değiştirebilirsiniz.

## <a name="passing-single-dimensional-arrays-as-arguments"></a>Tek boyutlu dizileri bağımsız değişkenler olarak geçirme

Başlatılmış bir tek boyutlu dizi için bir yöntem geçirebilirsiniz. Örneğin, aşağıdaki deyim, yazdırma bir yönteme bir dizi gönderir.

[!code-csharp[csProgGuideArrays#34](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#34)]

Aşağıdaki kod, yazdırma yöntemin kısmi bir uygulamasını gösterir.

[!code-csharp[csProgGuideArrays#33](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#33)]

Başlatın ve aşağıdaki örnekte gösterildiği gibi bir adım, yeni bir dizi geçirin.

[!code-csharp[CsProgGuideArrays#35](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#35)]

### <a name="example"></a>Örnek

Aşağıdaki örnekte, dize dizisi başlatılır ve bağımsız değişken olarak geçirilen bir `DisplayArray` dizeler için yöntemi. Yöntemi, dizinin öğeleri görüntüler. Ardından, `ChangeArray` yöntemi, dizi öğelerinin tersine çevirir ve ardından `ChangeArrayElements` yöntemi, dizinin ilk üç öğeleri değiştirir. Her yöntemin dönüşünün ardından `DisplayArray` yöntemi bir dizi değere göre geçirme değişiklikleri dizi öğelerine engellemez olduğunu gösterir.

[!code-csharp[csProgGuideArrays#30](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/ArrayExample.cs)]

## <a name="passing-multidimensional-arrays-as-arguments"></a>Çok boyutlu diziler bağımsız değişken olarak geçirme

Başlatılmış bir çok boyutlu dizi tek boyutlu dizi geçirdiğiniz aynı şekilde bir yönteme geçirin.

[!code-csharp[csProgGuideArrays#41](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#41)]

Aşağıdaki kod iki boyutlu bir dizi bağımsız değişken olarak kabul eden bir yazdırma yöntemin kısmi bir bildirimi gösterir.

[!code-csharp[csProgGuideArrays#36](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#36)]

Başlatın ve aşağıdaki örnekte gösterildiği gibi bir adım, yeni bir dizi geçirin:

[!code-csharp[csProgGuideArrays#32](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#32)]

### <a name="example"></a>Örnek

Aşağıdaki örnekte, iki boyutlu bir tamsayı dizisi başlatılır ve geçirilen `Print2DArray` yöntemi. Yöntemi, dizinin öğeleri görüntüler.

[!code-csharp[csProgGuideArrays#31](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#31)]

## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../index.md)  
- [Diziler](index.md)  
- [Tek Boyutlu Diziler](single-dimensional-arrays.md)  
- [Çok Boyutlu Diziler](multidimensional-arrays.md)  
- [Düzensiz Diziler](jagged-arrays.md)  