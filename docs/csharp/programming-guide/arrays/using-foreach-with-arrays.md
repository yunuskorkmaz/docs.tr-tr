---
title: Arrays ile foreach kullanma-C# Programlama Kılavuzu
description: C# ' deki foreach ifadesi bir dizinin öğeleri boyunca yinelenir. Tek boyutlu diziler için foreach, öğeleri artan dizin sırasında işler.
ms.date: 05/23/2018
helpviewer_keywords:
- arrays [C#], foreach
- foreach statement [C#], using with arrays
ms.assetid: 5f2da2a9-1f56-4de5-94cc-e07f4f7a0244
ms.openlocfilehash: d924a3ef3351cbb30b809a1542f35314ee721852
ms.sourcegitcommit: cf5a800a33de64d0aad6d115ffcc935f32375164
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/20/2020
ms.locfileid: "86474546"
---
# <a name="using-foreach-with-arrays-c-programming-guide"></a>Dizilerle foreach kullanma (C# Programlama Kılavuzu)

[Foreach](../../language-reference/keywords/foreach-in.md) ifadesi bir dizinin öğeleri boyunca yinelemek için basit ve temiz bir yol sağlar.

Tek boyutlu diziler için, `foreach` ifade 0 dizininden başlayıp dizin ile sona ermek üzere öğeleri artan dizin sırasında işler `Length - 1` :

 [!code-csharp[csProgGuideArrays#28](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#28)]

Çok boyutlu diziler için öğelere, en sağdaki boyutun dizinlerinin önce artması, sonra bir sonraki sol boyut ve bu şekilde sola doğru bir şekilde geçmesi gerekir:

 [!code-csharp[csProgGuideArrays#29](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#29)]

Ancak, çok boyutlu diziler ile, iç içe geçmiş bir [for](../../language-reference/keywords/for.md) döngüsü kullanılması, dizi öğelerinin işlenmesi sırasında daha fazla denetim sağlar.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Array>
- [C# Programlama Kılavuzu](../index.md)
- [Diziler](index.md)
- [Tek Boyutlu Diziler](single-dimensional-arrays.md)
- [Çok Boyutlu Diziler](multidimensional-arrays.md)
- [Düzensiz Diziler](jagged-arrays.md)
