---
title: Diziler ile foreach kullanma- C# Programlama Kılavuzu
ms.date: 05/23/2018
helpviewer_keywords:
- arrays [C#], foreach
- foreach statement [C#], using with arrays
ms.assetid: 5f2da2a9-1f56-4de5-94cc-e07f4f7a0244
ms.openlocfilehash: bb121b0f5d990ef6e596b34a45606e2abde6811a
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75705684"
---
# <a name="using-foreach-with-arrays-c-programming-guide"></a>Dizilerle foreach kullanma (C# Programlama Kılavuzu)

[Foreach](../../language-reference/keywords/foreach-in.md) ifadesi bir dizinin öğeleri boyunca yinelemek için basit ve temiz bir yol sağlar.

Tek boyutlu diziler için `foreach` bildiri, dizin 0 ' dan başlayıp Dizin `Length - 1`ile sona ermek üzere, öğeleri artan dizin sırasında işler:

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
