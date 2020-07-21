---
title: Dizileri bağımsız değişkenler olarak geçirme-C# Programlama Kılavuzu
description: C# içindeki diziler, yöntem parametrelerine bağımsız değişken olarak geçirilebilir. Diziler başvuru türleri olduğundan, yöntemi öğelerinin değerini değiştirebilir.
ms.date: 07/05/2018
helpviewer_keywords:
- arrays [C#], passing as arguments
ms.assetid: f3a0971e-c87c-4a1f-8262-bc0a3b712772
ms.openlocfilehash: 68f174421e56e2cf082fe670f93c4f6627d7c17b
ms.sourcegitcommit: cf5a800a33de64d0aad6d115ffcc935f32375164
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/20/2020
ms.locfileid: "86474637"
---
# <a name="passing-arrays-as-arguments-c-programming-guide"></a>Dizileri bağımsız değişkenler olarak geçirme (C# Programlama Kılavuzu)

Diziler, yöntem parametrelerine bağımsız değişken olarak geçirilebilir. Diziler başvuru türleri olduğundan, yöntemi öğelerinin değerini değiştirebilir.

## <a name="passing-single-dimensional-arrays-as-arguments"></a>Tek boyutlu dizileri bağımsız değişkenler olarak geçirme

Başlatılmış bir tek boyutlu diziyi bir yönteme geçirebilirsiniz. Örneğin, aşağıdaki ifade bir PRINT yöntemine bir dizi gönderir.

[!code-csharp[csProgGuideArrays#34](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#34)]

Aşağıdaki kod, Print yönteminin kısmi bir uygulamasını gösterir.

[!code-csharp[csProgGuideArrays#33](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#33)]

Aşağıdaki örnekte gösterildiği gibi, yeni bir diziyi tek bir adımda başlatabilir ve geçirebilirsiniz.

[!code-csharp[CsProgGuideArrays#35](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#35)]

### <a name="example"></a>Örnek

Aşağıdaki örnekte, dizeler dizisi başlatılır ve dizeler için bir yönteme bağımsız değişken olarak geçirilir `DisplayArray` . Yöntemi, dizinin öğelerini görüntüler. Sonra, `ChangeArray` yöntemi dizi öğelerini tersine çevirir ve sonra `ChangeArrayElements` yöntemin ilk üç öğesini değiştirir. Her yöntemin döndürdüğü `DisplayArray` Yöntem, bir diziyi değere göre geçirmenin dizi öğelerinde değişiklik yapılmasını önleyemediğini gösterir.

[!code-csharp[csProgGuideArrays#30](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/ArrayExample.cs)]

## <a name="passing-multidimensional-arrays-as-arguments"></a>Çok boyutlu dizileri bağımsız değişken olarak geçirme

Başlatılmış bir çok boyutlu diziyi, tek boyutlu bir diziyi geçirdiğiniz şekilde bir yönteme geçirirsiniz.

[!code-csharp[csProgGuideArrays#41](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#41)]

Aşağıdaki kod, bağımsız değişkeni olarak iki boyutlu bir diziyi kabul eden bir Print yönteminin kısmi bildirimini gösterir.

[!code-csharp[csProgGuideArrays#36](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#36)]

Aşağıdaki örnekte gösterildiği gibi, yeni bir diziyi tek bir adımda başlatabilir ve geçirebilirsiniz:

[!code-csharp[csProgGuideArrays#32](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#32)]

### <a name="example"></a>Örnek

Aşağıdaki örnekte, iki boyutlu bir tamsayılar dizisi başlatılır ve `Print2DArray` yöntemine geçirilir. Yöntemi, dizinin öğelerini görüntüler.

[!code-csharp[csProgGuideArrays#31](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#31)]

## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../index.md)
- [Diziler](index.md)
- [Tek Boyutlu Diziler](single-dimensional-arrays.md)
- [Çok Boyutlu Diziler](multidimensional-arrays.md)
- [Düzensiz Diziler](jagged-arrays.md)
