---
description: ': Take tümcesi hakkında daha fazla bilgi edinin (Visual Basic)'
title: Take Yan Tümcesi
ms.date: 07/20/2015
f1_keywords:
- vb.QueryTake
helpviewer_keywords:
- Take statement [Visual Basic]
- queries [Visual Basic], Take
- Take clause [Visual Basic]
ms.assetid: 77bf87b2-1476-4456-957f-fee922fbad8c
ms.openlocfilehash: 6542d262490d9d4acff893b2a99ffb60dd1446a2
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99653543"
---
# <a name="take-clause-visual-basic"></a><span data-ttu-id="9a457-103">Take Tümcesi (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9a457-103">Take Clause (Visual Basic)</span></span>

<span data-ttu-id="9a457-104">Bir koleksiyonun başından itibaren belirtilen sayıda bitişik öğeyi döndürür.</span><span class="sxs-lookup"><span data-stu-id="9a457-104">Returns a specified number of contiguous elements from the start of a collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9a457-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="9a457-105">Syntax</span></span>  
  
```vb  
Take count  
```  
  
## <a name="parts"></a><span data-ttu-id="9a457-106">Bölümler</span><span class="sxs-lookup"><span data-stu-id="9a457-106">Parts</span></span>  

 `count`  
 <span data-ttu-id="9a457-107">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="9a457-107">Required.</span></span> <span data-ttu-id="9a457-108">Döndürülecek dizi öğe sayısını değerlendiren bir değer veya ifade.</span><span class="sxs-lookup"><span data-stu-id="9a457-108">A value or an expression that evaluates to the number of elements of the sequence to return.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9a457-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="9a457-109">Remarks</span></span>  

 <span data-ttu-id="9a457-110">`Take`Yan tümce bir sorgunun bir sonuç listesinin başından itibaren belirtilen sayıda bitişik öğe içermesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="9a457-110">The `Take` clause causes a query to include a specified number of contiguous elements from the start of a results list.</span></span> <span data-ttu-id="9a457-111">Dahil edilecek öğe sayısı parametresi tarafından belirtilir `count` .</span><span class="sxs-lookup"><span data-stu-id="9a457-111">The number of elements to include is specified by the `count` parameter.</span></span>  
  
 <span data-ttu-id="9a457-112">`Take` `Skip` Bir sorgunun herhangi bir segmentinden bir veri aralığı döndürmek için yan tümcesini kullanın.</span><span class="sxs-lookup"><span data-stu-id="9a457-112">You can use the `Take` clause with the `Skip` clause to return a range of data from any segment of a query.</span></span> <span data-ttu-id="9a457-113">Bunu yapmak için aralığın ilk öğesinin dizinini `Skip` yan tümcesine ve aralığın boyutunu `Take` yan tümcesine geçirin.</span><span class="sxs-lookup"><span data-stu-id="9a457-113">To do this, pass the index of the first element of the range to the `Skip` clause and the size of the range to the `Take` clause.</span></span> <span data-ttu-id="9a457-114">Bu durumda yan tümce, yan `Take` tümcesinden sonra belirtilmelidir `Skip` .</span><span class="sxs-lookup"><span data-stu-id="9a457-114">In this case, the `Take` clause must be specified after the `Skip` clause.</span></span>  
  
 <span data-ttu-id="9a457-115">`Take`Bir sorguda yan tümcesini kullandığınızda, sonuçların `Take` amaçlanan sonuçları dahil etmek için yan tümce sağlayacak bir sırada döndürüldüğünden de emin olmanız gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="9a457-115">When you use the `Take` clause in a query, you may also need to ensure that the results are returned in an order that will enable the `Take` clause to include the intended results.</span></span> <span data-ttu-id="9a457-116">Sorgu sonuçlarını sıralama hakkında daha fazla bilgi için bkz. [order by yan tümcesi](order-by-clause.md).</span><span class="sxs-lookup"><span data-stu-id="9a457-116">For more information about ordering query results, see [Order By Clause](order-by-clause.md).</span></span>  
  
 <span data-ttu-id="9a457-117">`TakeWhile`Belirtilen koşula bağlı olarak yalnızca belirli öğelerin döndürüleceğini belirtmek için yan tümcesini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9a457-117">You can use the `TakeWhile` clause to specify that only certain elements be returned, depending on a supplied condition.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9a457-118">Örnek</span><span class="sxs-lookup"><span data-stu-id="9a457-118">Example</span></span>  

 <span data-ttu-id="9a457-119">Aşağıdaki kod örneği, yan tümcesini, `Take` `Skip` sayfalardaki bir sorgudan veri döndürmek için yan tümcesiyle birlikte kullanır.</span><span class="sxs-lookup"><span data-stu-id="9a457-119">The following code example uses the `Take` clause together with the `Skip` clause to return data from a query in pages.</span></span> <span data-ttu-id="9a457-120">GetCustomers işlevi, `Skip` sağlanan başlangıç dizini değerine kadar listedeki müşterileri atlamak için yan tümcesini kullanır ve `Take` Bu dizin değerinden başlayan müşterilerin bir sayfasını döndürmek için yan tümcesini kullanır.</span><span class="sxs-lookup"><span data-stu-id="9a457-120">The GetCustomers function uses the `Skip` clause to bypass the customers in the list until the supplied starting index value, and uses the `Take` clause to return a page of customers starting from that index value.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="9a457-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9a457-121">See also</span></span>

- [<span data-ttu-id="9a457-122">Visual Basic'de LINQ'e Giriş</span><span class="sxs-lookup"><span data-stu-id="9a457-122">Introduction to LINQ in Visual Basic</span></span>](../../programming-guide/language-features/linq/introduction-to-linq.md)
- [<span data-ttu-id="9a457-123">Sorgular</span><span class="sxs-lookup"><span data-stu-id="9a457-123">Queries</span></span>](index.md)
- [<span data-ttu-id="9a457-124">Select yan tümcesi</span><span class="sxs-lookup"><span data-stu-id="9a457-124">Select Clause</span></span>](select-clause.md)
- [<span data-ttu-id="9a457-125">From yan tümcesi</span><span class="sxs-lookup"><span data-stu-id="9a457-125">From Clause</span></span>](from-clause.md)
- [<span data-ttu-id="9a457-126">Order by yan tümcesi</span><span class="sxs-lookup"><span data-stu-id="9a457-126">Order By Clause</span></span>](order-by-clause.md)
- [<span data-ttu-id="9a457-127">Take While Yan Tümcesi</span><span class="sxs-lookup"><span data-stu-id="9a457-127">Take While Clause</span></span>](take-while-clause.md)
- [<span data-ttu-id="9a457-128">Skip Yan Tümcesi</span><span class="sxs-lookup"><span data-stu-id="9a457-128">Skip Clause</span></span>](skip-clause.md)
