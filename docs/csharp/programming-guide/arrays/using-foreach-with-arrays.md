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
# <a name="using-foreach-with-arrays-c-programming-guide"></a><span data-ttu-id="9aaf4-102">Foreach'i dizilerle kullanma (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="9aaf4-102">Using foreach with arrays (C# Programming Guide)</span></span>

<span data-ttu-id="9aaf4-103">[Foreach](../../language-reference/keywords/foreach-in.md) deyimi, bir dizinin öğeleri aracılığıyla yinelemek için basit ve temiz bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="9aaf4-103">The [foreach](../../language-reference/keywords/foreach-in.md) statement provides a simple, clean way to iterate through the elements of an array.</span></span>

<span data-ttu-id="9aaf4-104">Tek boyutlu diziler için `foreach` deyim öğeleri, dizin 0 ile başlayan ve `Length - 1`dizinle biten, indeks sırasını artırarak işler:</span><span class="sxs-lookup"><span data-stu-id="9aaf4-104">For single-dimensional arrays, the `foreach` statement processes elements in increasing index order, starting with index 0 and ending with index `Length - 1`:</span></span>

 [!code-csharp[csProgGuideArrays#28](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#28)]

<span data-ttu-id="9aaf4-105">Çok boyutlu diziler için, elemanlar önce en sağdaki boyutun indeksleri, sonra bir sonraki sol boyut ve sola doğru artırılacak şekilde geçiş yapılır:</span><span class="sxs-lookup"><span data-stu-id="9aaf4-105">For multi-dimensional arrays, elements are traversed such that the indices of the rightmost dimension are increased first, then the next left dimension, and so on to the left:</span></span>

 [!code-csharp[csProgGuideArrays#29](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#29)]

<span data-ttu-id="9aaf4-106">Ancak, çok boyutlu dizilerle, iç içe [doğru](../../language-reference/keywords/for.md) bir döngü kullanmak, dizi öğelerini işleme sırası üzerinde daha fazla denetim sağlar.</span><span class="sxs-lookup"><span data-stu-id="9aaf4-106">However, with multidimensional arrays, using a nested [for](../../language-reference/keywords/for.md) loop gives you more control over the order in which to process the array elements.</span></span>

## <a name="see-also"></a><span data-ttu-id="9aaf4-107">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9aaf4-107">See also</span></span>

- <xref:System.Array>
- [<span data-ttu-id="9aaf4-108">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="9aaf4-108">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="9aaf4-109">Diziler</span><span class="sxs-lookup"><span data-stu-id="9aaf4-109">Arrays</span></span>](index.md)
- [<span data-ttu-id="9aaf4-110">Tek Boyutlu Diziler</span><span class="sxs-lookup"><span data-stu-id="9aaf4-110">Single-Dimensional Arrays</span></span>](single-dimensional-arrays.md)
- [<span data-ttu-id="9aaf4-111">Çok Boyutlu Diziler</span><span class="sxs-lookup"><span data-stu-id="9aaf4-111">Multidimensional Arrays</span></span>](multidimensional-arrays.md)
- [<span data-ttu-id="9aaf4-112">Basit Diziler</span><span class="sxs-lookup"><span data-stu-id="9aaf4-112">Jagged Arrays</span></span>](jagged-arrays.md)
