---
title: Bellekte sorgunun sonuçlarını depolama
description: Sonuçları deposunu yapma.
ms.date: 11/30/2016
ms.assetid: 5b863961-1750-4cf9-9607-acea5054d15a
ms.openlocfilehash: c125d134d7c1db98363844c12fc8abd3faa9c868
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33279639"
---
# <a name="store-the-results-of-a-query-in-memory"></a><span data-ttu-id="2735b-103">Bellekte sorgunun sonuçlarını depolama</span><span class="sxs-lookup"><span data-stu-id="2735b-103">Store the results of a query in memory</span></span>

<span data-ttu-id="2735b-104">Bir sorguyu temel alabilir ve verileri düzenlemek hakkında yönergeler kümesidir.</span><span class="sxs-lookup"><span data-stu-id="2735b-104">A query is basically a set of instructions for how to retrieve and organize data.</span></span> <span data-ttu-id="2735b-105">İstenen sonuç sonraki her öğe olarak sorguları gevşek, yürütülür.</span><span class="sxs-lookup"><span data-stu-id="2735b-105">Queries are executed lazily, as each subsequent item in the result is requested.</span></span> <span data-ttu-id="2735b-106">Kullandığınızda `foreach` sonuçları yinelemek için öğeler erişilen olarak döndürülür.</span><span class="sxs-lookup"><span data-stu-id="2735b-106">When you use `foreach` to iterate the results, items are returned as accessed.</span></span> <span data-ttu-id="2735b-107">Bir sorguyu değerlendirmek ve sonuçlarını çalıştırmadan depolamak için bir `foreach` döngü, yalnızca aşağıdaki yöntemlerden birini sorgu değişkeni üzerine çağırırsınız:</span><span class="sxs-lookup"><span data-stu-id="2735b-107">To evaluate a query and store its results without executing a `foreach` loop, just call one of the following methods on the query variable:</span></span>  
  
-   <xref:System.Linq.Enumerable.ToList%2A>  
  
-   <xref:System.Linq.Enumerable.ToArray%2A>  
  
-   <xref:System.Linq.Enumerable.ToDictionary%2A>  
  
-   <xref:System.Linq.Enumerable.ToLookup%2A>  
  
 <span data-ttu-id="2735b-108">Sorgu sonuçları depoladığınızda, döndürülen koleksiyon nesnesi için yeni bir değişken aşağıdaki örnekte gösterildiği gibi atamanızı öneririz:</span><span class="sxs-lookup"><span data-stu-id="2735b-108">We recommend that when you store the query results, you assign the returned collection object to a new variable as shown in the following example:</span></span>  
  
## <a name="example"></a><span data-ttu-id="2735b-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="2735b-109">Example</span></span>  
 [!code-csharp[csProgGuideLINQ#25](../../../samples/snippets/csharp/concepts/linq/how-to-store-the-results-of-a-query-in-memory_1.cs)]  
  

## <a name="see-also"></a><span data-ttu-id="2735b-110">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="2735b-110">See Also</span></span>  
 [<span data-ttu-id="2735b-111">LINQ Sorgu ifadeleri</span><span class="sxs-lookup"><span data-stu-id="2735b-111">LINQ Query Expressions</span></span>](index.md)
