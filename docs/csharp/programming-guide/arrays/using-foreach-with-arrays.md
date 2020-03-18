---
title: Foreach'i dizilerle kullanma - C# Programlama Kılavuzu
ms.date: 05/23/2018
helpviewer_keywords:
- arrays [C#], foreach
- foreach statement [C#], using with arrays
ms.assetid: 5f2da2a9-1f56-4de5-94cc-e07f4f7a0244
ms.openlocfilehash: bb121b0f5d990ef6e596b34a45606e2abde6811a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75705684"
---
# <a name="using-foreach-with-arrays-c-programming-guide"></a>Foreach'i dizilerle kullanma (C# Programlama Kılavuzu)

[Foreach](../../language-reference/keywords/foreach-in.md) deyimi, bir dizinin öğeleri aracılığıyla yinelemek için basit ve temiz bir yol sağlar.

Tek boyutlu diziler için `foreach` deyim öğeleri, dizin 0 ile başlayan ve `Length - 1`dizinle biten, indeks sırasını artırarak işler:

 [!code-csharp[csProgGuideArrays#28](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#28)]

Çok boyutlu diziler için, elemanlar önce en sağdaki boyutun indeksleri, sonra bir sonraki sol boyut ve sola doğru artırılacak şekilde geçiş yapılır:

 [!code-csharp[csProgGuideArrays#29](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#29)]

Ancak, çok boyutlu dizilerle, iç içe [doğru](../../language-reference/keywords/for.md) bir döngü kullanmak, dizi öğelerini işleme sırası üzerinde daha fazla denetim sağlar.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Array>
- [C# Programlama Kılavuzu](../index.md)
- [Diziler](index.md)
- [Tek Boyutlu Diziler](single-dimensional-arrays.md)
- [Çok Boyutlu Diziler](multidimensional-arrays.md)
- [Basit Diziler](jagged-arrays.md)
