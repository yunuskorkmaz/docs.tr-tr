---
title: "Bellekte sorgunun sonuçlarını depolama"
description: "Sonuçları deposunu yapma."
keywords: .NET, .NET core, C#
author: BillWagner
manager: wpickett
ms.author: wiwagn
ms.date: 11/30/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.assetid: 5b863961-1750-4cf9-9607-acea5054d15a
ms.openlocfilehash: 86a9c2d464eac83cabb5faa68987ad580fc31248
ms.sourcegitcommit: 7e99f66ef09d2903e22c789c67ff5a10aa953b2f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/18/2017
---
# <a name="store-the-results-of-a-query-in-memory"></a><span data-ttu-id="6f037-104">Bellekte sorgunun sonuçlarını depolama</span><span class="sxs-lookup"><span data-stu-id="6f037-104">Store the results of a query in memory</span></span>

<span data-ttu-id="6f037-105">Bir sorguyu temel alabilir ve verileri düzenlemek hakkında yönergeler kümesidir.</span><span class="sxs-lookup"><span data-stu-id="6f037-105">A query is basically a set of instructions for how to retrieve and organize data.</span></span> <span data-ttu-id="6f037-106">İstenen sonuç sonraki her öğe olarak sorguları gevşek, yürütülür.</span><span class="sxs-lookup"><span data-stu-id="6f037-106">Queries are executed lazily, as each subsequent item in the result is requested.</span></span> <span data-ttu-id="6f037-107">Kullandığınızda `foreach` sonuçları yinelemek için öğeler erişilen olarak döndürülür.</span><span class="sxs-lookup"><span data-stu-id="6f037-107">When you use `foreach` to iterate the results, items are returned as accessed.</span></span> <span data-ttu-id="6f037-108">Bir sorguyu değerlendirmek ve sonuçlarını çalıştırmadan depolamak için bir `foreach` döngü, yalnızca aşağıdaki yöntemlerden birini sorgu değişkeni üzerine çağırırsınız:</span><span class="sxs-lookup"><span data-stu-id="6f037-108">To evaluate a query and store its results without executing a `foreach` loop, just call one of the following methods on the query variable:</span></span>  
  
-   <xref:System.Linq.Enumerable.ToList%2A>  
  
-   <xref:System.Linq.Enumerable.ToArray%2A>  
  
-   <xref:System.Linq.Enumerable.ToDictionary%2A>  
  
-   <xref:System.Linq.Enumerable.ToLookup%2A>  
  
 <span data-ttu-id="6f037-109">Sorgu sonuçları depoladığınızda, döndürülen koleksiyon nesnesi için yeni bir değişken aşağıdaki örnekte gösterildiği gibi atamanızı öneririz:</span><span class="sxs-lookup"><span data-stu-id="6f037-109">We recommend that when you store the query results, you assign the returned collection object to a new variable as shown in the following example:</span></span>  
  
## <a name="example"></a><span data-ttu-id="6f037-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="6f037-110">Example</span></span>  
 [!code-csharp[csProgGuideLINQ#25](../../../samples/snippets/csharp/concepts/linq/how-to-store-the-results-of-a-query-in-memory_1.cs)]  
  

## <a name="see-also"></a><span data-ttu-id="6f037-111">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="6f037-111">See Also</span></span>  
 [<span data-ttu-id="6f037-112">LINQ Sorgu ifadeleri</span><span class="sxs-lookup"><span data-stu-id="6f037-112">LINQ Query Expressions</span></span>](index.md)
