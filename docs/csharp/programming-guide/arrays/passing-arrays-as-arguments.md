---
title: Dizileri bağımsız değişken olarak geçirme - C# Programlama Kılavuzu
ms.date: 07/05/2018
helpviewer_keywords:
- arrays [C#], passing as arguments
ms.assetid: f3a0971e-c87c-4a1f-8262-bc0a3b712772
ms.openlocfilehash: 2e53008910a9062ada25680eb4b8e54a225fd226
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75705697"
---
# <a name="passing-arrays-as-arguments-c-programming-guide"></a>Dizileri bağımsız değişken olarak geçirme (C# Programlama Kılavuzu)

Diziler yöntem parametrelerine bağımsız değişken olarak geçirilebilir. Diziler başvuru türleri olduğundan, yöntem öğelerin değerini değiştirebilir.

## <a name="passing-single-dimensional-arrays-as-arguments"></a>Tek boyutlu dizileri bağımsız değişken olarak geçirme

Başharfe bıyılan tek boyutlu bir diziyi bir yönteme geçirebilirsiniz. Örneğin, aşağıdaki deyim bir diziyi yazdırma yöntemine gönderir.

[!code-csharp[csProgGuideArrays#34](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#34)]

Aşağıdaki kod yazdırma yönteminin kısmi bir uygulamasını gösterir.

[!code-csharp[csProgGuideArrays#33](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#33)]

Aşağıdaki örnekte gösterildiği gibi, yeni bir diziyi tek adımda başolarak açabilir ve geçirebilirsiniz.

[!code-csharp[CsProgGuideArrays#35](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#35)]

### <a name="example"></a>Örnek

Aşağıdaki örnekte, dizeleri bir dizi baş harfe ve `DisplayArray` dizeleri için bir yöntemiçin bir bağımsız değişken olarak geçirilir. Yöntem, dizinin öğelerini görüntüler. Daha sonra, `ChangeArray` yöntem dizi öğelerini tersine `ChangeArrayElements` çevirir ve ardından yöntem dizinin ilk üç öğesini değiştirir. Her yöntem döndükten `DisplayArray` sonra, yöntem bir diziyi değere aktarmanın dizi öğelerinde değişiklikleri engellemediğini gösterir.

[!code-csharp[csProgGuideArrays#30](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/ArrayExample.cs)]

## <a name="passing-multidimensional-arrays-as-arguments"></a>Çok boyutlu dizileri bağımsız değişken olarak geçirme

Başharfli çok boyutlu bir diziyi, tek boyutlu bir diziyi geçtiğin gibi bir yönteme geçirirsiniz.

[!code-csharp[csProgGuideArrays#41](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#41)]

Aşağıdaki kod, iki boyutlu bir diziyi bağımsız değişken olarak kabul eden bir yazdırma yönteminin kısmi bildirimini gösterir.

[!code-csharp[csProgGuideArrays#36](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#36)]

Aşağıdaki örnekte gösterildiği gibi, yeni bir diziyi tek adımda başolarak açabilir ve geçirebilirsiniz:

[!code-csharp[csProgGuideArrays#32](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#32)]

### <a name="example"></a>Örnek

Aşağıdaki örnekte, iki boyutlu bir tamsayı dizisi baş harfe `Print2DArray` getirilmiş ve yönteme geçirilir. Yöntem, dizinin öğelerini görüntüler.

[!code-csharp[csProgGuideArrays#31](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#31)]

## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../index.md)
- [Diziler](index.md)
- [Tek Boyutlu Diziler](single-dimensional-arrays.md)
- [Çok Boyutlu Diziler](multidimensional-arrays.md)
- [Basit Diziler](jagged-arrays.md)
