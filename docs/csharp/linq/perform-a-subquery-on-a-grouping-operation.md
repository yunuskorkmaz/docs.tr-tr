---
title: Gruplandırma işleminde bir alt sorgu gerçekleştirin (C#'da LINQ)
description: C#'da LINQ kullanarak gruplandırma işleminde bir alt sorgu nasıl gerçekleştirililir?
ms.date: 12/01/2016
ms.assetid: d75a588e-9b6f-4f37-b195-f99ec8503855
ms.openlocfilehash: fd26f87ad7d5b4892f086bf8c7a34cf19a7f9e02
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79173373"
---
# <a name="perform-a-subquery-on-a-grouping-operation"></a><span data-ttu-id="997f0-103">Gruplandırma işleminde alt sorgu gerçekleştirme</span><span class="sxs-lookup"><span data-stu-id="997f0-103">Perform a subquery on a grouping operation</span></span>

<span data-ttu-id="997f0-104">Bu makalede, kaynak verileri gruplara ayıran bir sorgu oluşturmanın iki farklı yolu gösterilmektedir ve sonra her grup üzerinde ayrı ayrı bir alt sorgu gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="997f0-104">This article shows two different ways to create a query that orders the source data into groups, and then performs a subquery over each group individually.</span></span> <span data-ttu-id="997f0-105">Her örnekte temel teknik, kaynak öğeleri adlı *continuation* `newGroup`bir devamı kullanarak gruplandırmak ve `newGroup`daha sonra karşı yeni bir alt sorgu oluşturmaktır.</span><span class="sxs-lookup"><span data-stu-id="997f0-105">The basic technique in each example is to group the source elements by using a *continuation* named `newGroup`, and then generating a new subquery against `newGroup`.</span></span> <span data-ttu-id="997f0-106">Bu alt sorgu, dış sorgu tarafından oluşturulan her yeni gruba karşı çalıştırılır.</span><span class="sxs-lookup"><span data-stu-id="997f0-106">This subquery is run against each new group that is created by the outer query.</span></span> <span data-ttu-id="997f0-107">Bu özel örnekte son çıktının bir grup değil, anonim türlerin düz bir sırası olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="997f0-107">Note that in this particular example the final output is not a group, but a flat sequence of anonymous types.</span></span>  
  
<span data-ttu-id="997f0-108">Gruplandırma hakkında daha fazla bilgi için [grup yan tümcesine](../language-reference/keywords/group-clause.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="997f0-108">For more information about how to group, see [group clause](../language-reference/keywords/group-clause.md).</span></span>  
  
<span data-ttu-id="997f0-109">Devamı hakkında daha fazla bilgi için [bkz.](../language-reference/keywords/into.md)</span><span class="sxs-lookup"><span data-stu-id="997f0-109">For more information about continuations, see [into](../language-reference/keywords/into.md).</span></span> <span data-ttu-id="997f0-110">Aşağıdaki örnek, veri kaynağı olarak bellek içi bir veri yapısı kullanır, ancak her tür LINQ veri kaynağı için aynı ilkeler geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="997f0-110">The following example uses an in-memory data structure as the data source, but the same principles apply for any kind of LINQ data source.</span></span>  
  
## <a name="example"></a><span data-ttu-id="997f0-111">Örnek</span><span class="sxs-lookup"><span data-stu-id="997f0-111">Example</span></span>

> [!NOTE]
> <span data-ttu-id="997f0-112">Bu örnek, sorgulayan [nesneler koleksiyonunda](query-a-collection-of-objects.md)örnek kodda tanımlanan nesnelere başvurular içerir.</span><span class="sxs-lookup"><span data-stu-id="997f0-112">This example contains references to objects that are defined in the sample code in [Query a collection of objects](query-a-collection-of-objects.md).</span></span>

[!code-csharp[csProgGuideLINQ#23](~/samples/snippets/csharp/concepts/linq/how-to-perform-a-subquery-on-a-grouping-operation_1.cs)]

<span data-ttu-id="997f0-113">Yukarıdaki parçacıktaki sorgu yöntem sözdizimi kullanılarak da yazılabilir.</span><span class="sxs-lookup"><span data-stu-id="997f0-113">The query in the snippet above can also be written using method syntax.</span></span> <span data-ttu-id="997f0-114">Aşağıdaki kod snippet yöntem sözdizimi kullanılarak yazılmış bir semantically eşdeğer sorgu vardır.</span><span class="sxs-lookup"><span data-stu-id="997f0-114">The following code snippet has a semantically equivalent query written using method syntax.</span></span>

[!code-csharp[csProgGuideLINQ#86](~/samples/snippets/csharp/concepts/linq/how-to-perform-a-subquery-on-a-grouping-operation_2.cs)]

## <a name="see-also"></a><span data-ttu-id="997f0-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="997f0-115">See also</span></span>

- [<span data-ttu-id="997f0-116">Dil ile Tümleşik Sorgu (LINQ)</span><span class="sxs-lookup"><span data-stu-id="997f0-116">Language Integrated Query (LINQ)</span></span>](index.md)
