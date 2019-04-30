---
title: -Dizilerle foreach kullanma C# Programlama Kılavuzu
ms.custom: seodec18
ms.date: 05/23/2018
helpviewer_keywords:
- arrays [C#], foreach
- foreach statement [C#], using with arrays
ms.assetid: 5f2da2a9-1f56-4de5-94cc-e07f4f7a0244
ms.openlocfilehash: a22cb939370b38780881eca0d9585a14002c8250
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61683723"
---
# <a name="using-foreach-with-arrays-c-programming-guide"></a><span data-ttu-id="1b344-102">Dizilerle foreach kullanma (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="1b344-102">Using foreach with arrays (C# Programming Guide)</span></span>

<span data-ttu-id="1b344-103">[Foreach](../../language-reference/keywords/foreach-in.md) deyimi bir dizi öğelerinde yineleme yapmak için basit ve temiz bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="1b344-103">The [foreach](../../language-reference/keywords/foreach-in.md) statement provides a simple, clean way to iterate through the elements of an array.</span></span>

<span data-ttu-id="1b344-104">Tek boyutlu diziler için `foreach` deyimi, artan dizin sırasıyla dizini 0'ile başlayıp diziniyle öğeleri işler `Length - 1`:</span><span class="sxs-lookup"><span data-stu-id="1b344-104">For single-dimensional arrays, the `foreach` statement processes elements in increasing index order, starting with index 0 and ending with index `Length - 1`:</span></span>

 [!code-csharp[csProgGuideArrays#28](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#28)]

<span data-ttu-id="1b344-105">En sağdaki boyutu dizinleri artan ilk sonra sonraki sol boyut vb. için sol olduğuna gibi çok boyutlu diziler için öğeleri geçirilir:</span><span class="sxs-lookup"><span data-stu-id="1b344-105">For multi-dimensional arrays, elements are traversed such that the indices of the rightmost dimension are increased first, then the next left dimension, and so on to the left:</span></span>

 [!code-csharp[csProgGuideArrays#29](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#29)]

<span data-ttu-id="1b344-106">Ancak, çok boyutlu dizilerle, iç içe bir kullanarak [için](../../language-reference/keywords/for.md) döngü, dizi öğeleri işlemek sırada üzerinde daha fazla denetim sağlar.</span><span class="sxs-lookup"><span data-stu-id="1b344-106">However, with multidimensional arrays, using a nested [for](../../language-reference/keywords/for.md) loop gives you more control over the order in which to process the array elements.</span></span>

## <a name="see-also"></a><span data-ttu-id="1b344-107">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1b344-107">See also</span></span>

- <xref:System.Array>
- [<span data-ttu-id="1b344-108">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="1b344-108">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="1b344-109">Diziler</span><span class="sxs-lookup"><span data-stu-id="1b344-109">Arrays</span></span>](index.md)
- [<span data-ttu-id="1b344-110">Tek Boyutlu Diziler</span><span class="sxs-lookup"><span data-stu-id="1b344-110">Single-Dimensional Arrays</span></span>](single-dimensional-arrays.md)
- [<span data-ttu-id="1b344-111">Çok Boyutlu Diziler</span><span class="sxs-lookup"><span data-stu-id="1b344-111">Multidimensional Arrays</span></span>](multidimensional-arrays.md)
- [<span data-ttu-id="1b344-112">Düzensiz Diziler</span><span class="sxs-lookup"><span data-stu-id="1b344-112">Jagged Arrays</span></span>](jagged-arrays.md)
