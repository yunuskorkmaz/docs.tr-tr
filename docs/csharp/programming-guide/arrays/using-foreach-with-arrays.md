---
title: Dizilerle foreach kullanma (C# Programlama Kılavuzu)
ms.date: 05/23/2018
helpviewer_keywords:
- arrays [C#], foreach
- foreach statement [C#], using with arrays
ms.assetid: 5f2da2a9-1f56-4de5-94cc-e07f4f7a0244
ms.openlocfilehash: 298ee915bbe11313f3b33ea7dae9353ef956a231
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43509541"
---
# <a name="using-foreach-with-arrays-c-programming-guide"></a><span data-ttu-id="2bf16-102">Dizilerle foreach kullanma (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="2bf16-102">Using foreach with Arrays (C# Programming Guide)</span></span>

<span data-ttu-id="2bf16-103">[Foreach](../../language-reference/keywords/foreach-in.md) deyimi bir dizi öğelerinde yineleme yapmak için basit ve temiz bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="2bf16-103">The [foreach](../../language-reference/keywords/foreach-in.md) statement provides a simple, clean way to iterate through the elements of an array.</span></span>

<span data-ttu-id="2bf16-104">Tek boyutlu diziler için `foreach` deyimi, artan dizin sırasıyla dizini 0'ile başlayıp diziniyle öğeleri işler `Length - 1`:</span><span class="sxs-lookup"><span data-stu-id="2bf16-104">For single-dimensional arrays, the `foreach` statement processes elements in increasing index order, starting with index 0 and ending with index `Length - 1`:</span></span>

[!code-csharp[csProgGuideArrays#28](./codesnippet/CSharp/using-foreach-with-arrays_1.cs)]

<span data-ttu-id="2bf16-105">En sağdaki boyutu dizinleri artan ilk sonra sonraki sol boyut vb. için sol olduğuna gibi çok boyutlu diziler için öğeleri geçirilir:</span><span class="sxs-lookup"><span data-stu-id="2bf16-105">For multi-dimensional arrays, elements are traversed such that the indices of the rightmost dimension are increased first, then the next left dimension, and so on to the left:</span></span>

[!code-csharp[csProgGuideArrays#29](./codesnippet/CSharp/using-foreach-with-arrays_2.cs)]

<span data-ttu-id="2bf16-106">Ancak, çok boyutlu dizilerle, iç içe bir kullanarak [için](../../language-reference/keywords/for.md) döngü, dizi öğeleri işlemek sırada üzerinde daha fazla denetim sağlar.</span><span class="sxs-lookup"><span data-stu-id="2bf16-106">However, with multidimensional arrays, using a nested [for](../../language-reference/keywords/for.md) loop gives you more control over the order in which to process the array elements.</span></span>

## <a name="see-also"></a><span data-ttu-id="2bf16-107">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="2bf16-107">See Also</span></span>

- <xref:System.Array>  
- [<span data-ttu-id="2bf16-108">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="2bf16-108">C# Programming Guide</span></span>](../index.md)  
- [<span data-ttu-id="2bf16-109">Diziler</span><span class="sxs-lookup"><span data-stu-id="2bf16-109">Arrays</span></span>](index.md)  
- [<span data-ttu-id="2bf16-110">Tek Boyutlu Diziler</span><span class="sxs-lookup"><span data-stu-id="2bf16-110">Single-Dimensional Arrays</span></span>](single-dimensional-arrays.md)  
- [<span data-ttu-id="2bf16-111">Çok Boyutlu Diziler</span><span class="sxs-lookup"><span data-stu-id="2bf16-111">Multidimensional Arrays</span></span>](multidimensional-arrays.md)  
- [<span data-ttu-id="2bf16-112">Düzensiz Diziler</span><span class="sxs-lookup"><span data-stu-id="2bf16-112">Jagged Arrays</span></span>](jagged-arrays.md)
