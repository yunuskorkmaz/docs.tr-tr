---
title: -Dizilerle foreach kullanma C# Programlama Kılavuzu
ms.custom: seodec18
ms.date: 05/23/2018
helpviewer_keywords:
- arrays [C#], foreach
- foreach statement [C#], using with arrays
ms.assetid: 5f2da2a9-1f56-4de5-94cc-e07f4f7a0244
ms.openlocfilehash: a290cd709dd6491981658f467fa0163011290128
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/11/2018
ms.locfileid: "53238474"
---
# <a name="using-foreach-with-arrays-c-programming-guide"></a><span data-ttu-id="2c53d-102">Dizilerle foreach kullanma (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="2c53d-102">Using foreach with arrays (C# Programming Guide)</span></span>

<span data-ttu-id="2c53d-103">[Foreach](../../language-reference/keywords/foreach-in.md) deyimi bir dizi öğelerinde yineleme yapmak için basit ve temiz bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="2c53d-103">The [foreach](../../language-reference/keywords/foreach-in.md) statement provides a simple, clean way to iterate through the elements of an array.</span></span>

<span data-ttu-id="2c53d-104">Tek boyutlu diziler için `foreach` deyimi, artan dizin sırasıyla dizini 0'ile başlayıp diziniyle öğeleri işler `Length - 1`:</span><span class="sxs-lookup"><span data-stu-id="2c53d-104">For single-dimensional arrays, the `foreach` statement processes elements in increasing index order, starting with index 0 and ending with index `Length - 1`:</span></span>

[!code-csharp[csProgGuideArrays#28](./codesnippet/CSharp/using-foreach-with-arrays_1.cs)]

<span data-ttu-id="2c53d-105">En sağdaki boyutu dizinleri artan ilk sonra sonraki sol boyut vb. için sol olduğuna gibi çok boyutlu diziler için öğeleri geçirilir:</span><span class="sxs-lookup"><span data-stu-id="2c53d-105">For multi-dimensional arrays, elements are traversed such that the indices of the rightmost dimension are increased first, then the next left dimension, and so on to the left:</span></span>

[!code-csharp[csProgGuideArrays#29](./codesnippet/CSharp/using-foreach-with-arrays_2.cs)]

<span data-ttu-id="2c53d-106">Ancak, çok boyutlu dizilerle, iç içe bir kullanarak [için](../../language-reference/keywords/for.md) döngü, dizi öğeleri işlemek sırada üzerinde daha fazla denetim sağlar.</span><span class="sxs-lookup"><span data-stu-id="2c53d-106">However, with multidimensional arrays, using a nested [for](../../language-reference/keywords/for.md) loop gives you more control over the order in which to process the array elements.</span></span>

## <a name="see-also"></a><span data-ttu-id="2c53d-107">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="2c53d-107">See Also</span></span>

- <xref:System.Array>  
- [<span data-ttu-id="2c53d-108">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="2c53d-108">C# Programming Guide</span></span>](../index.md)  
- [<span data-ttu-id="2c53d-109">Diziler</span><span class="sxs-lookup"><span data-stu-id="2c53d-109">Arrays</span></span>](index.md)  
- [<span data-ttu-id="2c53d-110">Tek Boyutlu Diziler</span><span class="sxs-lookup"><span data-stu-id="2c53d-110">Single-Dimensional Arrays</span></span>](single-dimensional-arrays.md)  
- [<span data-ttu-id="2c53d-111">Çok Boyutlu Diziler</span><span class="sxs-lookup"><span data-stu-id="2c53d-111">Multidimensional Arrays</span></span>](multidimensional-arrays.md)  
- [<span data-ttu-id="2c53d-112">Düzensiz Diziler</span><span class="sxs-lookup"><span data-stu-id="2c53d-112">Jagged Arrays</span></span>](jagged-arrays.md)
