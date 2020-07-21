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
# <a name="using-foreach-with-arrays-c-programming-guide"></a><span data-ttu-id="8d584-104">Dizilerle foreach kullanma (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="8d584-104">Using foreach with arrays (C# Programming Guide)</span></span>

<span data-ttu-id="8d584-105">[Foreach](../../language-reference/keywords/foreach-in.md) ifadesi bir dizinin öğeleri boyunca yinelemek için basit ve temiz bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="8d584-105">The [foreach](../../language-reference/keywords/foreach-in.md) statement provides a simple, clean way to iterate through the elements of an array.</span></span>

<span data-ttu-id="8d584-106">Tek boyutlu diziler için, `foreach` ifade 0 dizininden başlayıp dizin ile sona ermek üzere öğeleri artan dizin sırasında işler `Length - 1` :</span><span class="sxs-lookup"><span data-stu-id="8d584-106">For single-dimensional arrays, the `foreach` statement processes elements in increasing index order, starting with index 0 and ending with index `Length - 1`:</span></span>

 [!code-csharp[csProgGuideArrays#28](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#28)]

<span data-ttu-id="8d584-107">Çok boyutlu diziler için öğelere, en sağdaki boyutun dizinlerinin önce artması, sonra bir sonraki sol boyut ve bu şekilde sola doğru bir şekilde geçmesi gerekir:</span><span class="sxs-lookup"><span data-stu-id="8d584-107">For multi-dimensional arrays, elements are traversed such that the indices of the rightmost dimension are increased first, then the next left dimension, and so on to the left:</span></span>

 [!code-csharp[csProgGuideArrays#29](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#29)]

<span data-ttu-id="8d584-108">Ancak, çok boyutlu diziler ile, iç içe geçmiş bir [for](../../language-reference/keywords/for.md) döngüsü kullanılması, dizi öğelerinin işlenmesi sırasında daha fazla denetim sağlar.</span><span class="sxs-lookup"><span data-stu-id="8d584-108">However, with multidimensional arrays, using a nested [for](../../language-reference/keywords/for.md) loop gives you more control over the order in which to process the array elements.</span></span>

## <a name="see-also"></a><span data-ttu-id="8d584-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8d584-109">See also</span></span>

- <xref:System.Array>
- [<span data-ttu-id="8d584-110">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="8d584-110">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="8d584-111">Diziler</span><span class="sxs-lookup"><span data-stu-id="8d584-111">Arrays</span></span>](index.md)
- [<span data-ttu-id="8d584-112">Tek Boyutlu Diziler</span><span class="sxs-lookup"><span data-stu-id="8d584-112">Single-Dimensional Arrays</span></span>](single-dimensional-arrays.md)
- [<span data-ttu-id="8d584-113">Çok Boyutlu Diziler</span><span class="sxs-lookup"><span data-stu-id="8d584-113">Multidimensional Arrays</span></span>](multidimensional-arrays.md)
- [<span data-ttu-id="8d584-114">Düzensiz Diziler</span><span class="sxs-lookup"><span data-stu-id="8d584-114">Jagged Arrays</span></span>](jagged-arrays.md)
