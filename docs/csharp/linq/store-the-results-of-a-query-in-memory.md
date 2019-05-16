---
title: Bellekte sorgunun sonuçlarını depolama
description: Sonuçları depolamayı öğrenin.
ms.date: 11/30/2016
ms.assetid: 5b863961-1750-4cf9-9607-acea5054d15a
ms.openlocfilehash: 66a7a95c74db4062e76c54d4339ccb7343f44067
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65633564"
---
# <a name="store-the-results-of-a-query-in-memory"></a><span data-ttu-id="c21bd-103">Bellekte sorgunun sonuçlarını depolama</span><span class="sxs-lookup"><span data-stu-id="c21bd-103">Store the results of a query in memory</span></span>

<span data-ttu-id="c21bd-104">Bir sorgu temel alabilir ve verileri düzenleme hakkında yönergeler kümesidir.</span><span class="sxs-lookup"><span data-stu-id="c21bd-104">A query is basically a set of instructions for how to retrieve and organize data.</span></span> <span data-ttu-id="c21bd-105">Sorgular, gevşek, sonraki her öğe sonucu, istenen şekilde yürütülür.</span><span class="sxs-lookup"><span data-stu-id="c21bd-105">Queries are executed lazily, as each subsequent item in the result is requested.</span></span> <span data-ttu-id="c21bd-106">Kullanırken `foreach` sonuçlarını yinelemek için öğeler erişilen olarak döndürülür.</span><span class="sxs-lookup"><span data-stu-id="c21bd-106">When you use `foreach` to iterate the results, items are returned as accessed.</span></span> <span data-ttu-id="c21bd-107">Bir sorguyu değerlendirmeye ve çalıştırmadan sonuçlarını depolamak için bir `foreach` döngüsünde, yalnızca aşağıdaki yöntemlerden birini sorgu değişkeni üzerinde çağırın:</span><span class="sxs-lookup"><span data-stu-id="c21bd-107">To evaluate a query and store its results without executing a `foreach` loop, just call one of the following methods on the query variable:</span></span>

- <xref:System.Linq.Enumerable.ToList%2A>

- <xref:System.Linq.Enumerable.ToArray%2A>

- <xref:System.Linq.Enumerable.ToDictionary%2A>

- <xref:System.Linq.Enumerable.ToLookup%2A>

 <span data-ttu-id="c21bd-108">Sorgu sonuçları depoladığınızda, döndürülen koleksiyon nesnesi için yeni bir değişken aşağıdaki örnekte gösterildiği gibi atamanızı öneririz:</span><span class="sxs-lookup"><span data-stu-id="c21bd-108">We recommend that when you store the query results, you assign the returned collection object to a new variable as shown in the following example:</span></span>

## <a name="example"></a><span data-ttu-id="c21bd-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="c21bd-109">Example</span></span>

[!code-csharp[csProgGuideLINQ#25](~/samples/snippets/csharp/concepts/linq/how-to-store-the-results-of-a-query-in-memory_1.cs)]

## <a name="see-also"></a><span data-ttu-id="c21bd-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c21bd-110">See also</span></span>

- [<span data-ttu-id="c21bd-111">Dil ile Tümleşik Sorgu (LINQ)</span><span class="sxs-lookup"><span data-stu-id="c21bd-111">Language Integrated Query (LINQ)</span></span>](index.md)
