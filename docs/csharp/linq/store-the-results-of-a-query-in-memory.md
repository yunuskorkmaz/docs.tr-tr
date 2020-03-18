---
title: Bellekte sorgunun sonuçlarını depolama
description: Sonuçları depolamak için nasıl.
ms.date: 11/30/2016
ms.assetid: 5b863961-1750-4cf9-9607-acea5054d15a
ms.openlocfilehash: 66a7a95c74db4062e76c54d4339ccb7343f44067
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "65633564"
---
# <a name="store-the-results-of-a-query-in-memory"></a><span data-ttu-id="0dc55-103">Bellekte sorgunun sonuçlarını depolama</span><span class="sxs-lookup"><span data-stu-id="0dc55-103">Store the results of a query in memory</span></span>

<span data-ttu-id="0dc55-104">Sorgu, temelde verilerin nasıl alınacağına ve düzenlenene yönelik bir yönerge ler kümesidir.</span><span class="sxs-lookup"><span data-stu-id="0dc55-104">A query is basically a set of instructions for how to retrieve and organize data.</span></span> <span data-ttu-id="0dc55-105">Sorgular, sonuçtaki her sonraki öğe istendiği için tembelce yürütülür.</span><span class="sxs-lookup"><span data-stu-id="0dc55-105">Queries are executed lazily, as each subsequent item in the result is requested.</span></span> <span data-ttu-id="0dc55-106">Sonuçları doğrulamak `foreach` için kullandığınızda, öğeler erişilmiş olarak döndürülür.</span><span class="sxs-lookup"><span data-stu-id="0dc55-106">When you use `foreach` to iterate the results, items are returned as accessed.</span></span> <span data-ttu-id="0dc55-107">Bir sorguyu değerlendirmek ve bir `foreach` döngü yürütmeden sonuçlarını depolamak için sorgu değişkeninde aşağıdaki yöntemlerden birini aramaniz yeterlidir:</span><span class="sxs-lookup"><span data-stu-id="0dc55-107">To evaluate a query and store its results without executing a `foreach` loop, just call one of the following methods on the query variable:</span></span>

- <xref:System.Linq.Enumerable.ToList%2A>

- <xref:System.Linq.Enumerable.ToArray%2A>

- <xref:System.Linq.Enumerable.ToDictionary%2A>

- <xref:System.Linq.Enumerable.ToLookup%2A>

 <span data-ttu-id="0dc55-108">Sorgu sonuçlarını depolarken, döndürülen koleksiyon nesnesini aşağıdaki örnekte gösterildiği gibi yeni bir değişkene atamanızı öneririz:</span><span class="sxs-lookup"><span data-stu-id="0dc55-108">We recommend that when you store the query results, you assign the returned collection object to a new variable as shown in the following example:</span></span>

## <a name="example"></a><span data-ttu-id="0dc55-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="0dc55-109">Example</span></span>

[!code-csharp[csProgGuideLINQ#25](~/samples/snippets/csharp/concepts/linq/how-to-store-the-results-of-a-query-in-memory_1.cs)]

## <a name="see-also"></a><span data-ttu-id="0dc55-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0dc55-110">See also</span></span>

- [<span data-ttu-id="0dc55-111">Dil ile Tümleşik Sorgu (LINQ)</span><span class="sxs-lookup"><span data-stu-id="0dc55-111">Language Integrated Query (LINQ)</span></span>](index.md)
