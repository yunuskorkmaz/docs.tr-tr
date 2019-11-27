---
title: Take Tümcesi
ms.date: 07/20/2015
f1_keywords:
- vb.QueryTake
helpviewer_keywords:
- Take statement [Visual Basic]
- queries [Visual Basic], Take
- Take clause [Visual Basic]
ms.assetid: 77bf87b2-1476-4456-957f-fee922fbad8c
ms.openlocfilehash: 3082954ef84560ccb70f7a47cd3532f622829392
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74349641"
---
# <a name="take-clause-visual-basic"></a><span data-ttu-id="d88cd-102">Take Tümcesi (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d88cd-102">Take Clause (Visual Basic)</span></span>
<span data-ttu-id="d88cd-103">Bir koleksiyonun başından itibaren belirtilen sayıda bitişik öğeyi döndürür.</span><span class="sxs-lookup"><span data-stu-id="d88cd-103">Returns a specified number of contiguous elements from the start of a collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d88cd-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d88cd-104">Syntax</span></span>  
  
```vb  
Take count  
```  
  
## <a name="parts"></a><span data-ttu-id="d88cd-105">Bölümler</span><span class="sxs-lookup"><span data-stu-id="d88cd-105">Parts</span></span>  
 `count`  
 <span data-ttu-id="d88cd-106">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="d88cd-106">Required.</span></span> <span data-ttu-id="d88cd-107">Döndürülecek dizi öğe sayısını değerlendiren bir değer veya ifade.</span><span class="sxs-lookup"><span data-stu-id="d88cd-107">A value or an expression that evaluates to the number of elements of the sequence to return.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d88cd-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d88cd-108">Remarks</span></span>  
 <span data-ttu-id="d88cd-109">`Take` yan tümcesi, bir sorgunun bir sonuç listesinin başından itibaren belirtilen sayıda bitişik öğe içermesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="d88cd-109">The `Take` clause causes a query to include a specified number of contiguous elements from the start of a results list.</span></span> <span data-ttu-id="d88cd-110">Eklenecek öğe sayısı `count` parametresi tarafından belirtilir.</span><span class="sxs-lookup"><span data-stu-id="d88cd-110">The number of elements to include is specified by the `count` parameter.</span></span>  
  
 <span data-ttu-id="d88cd-111">Sorgunun herhangi bir segmentinden bir veri aralığı döndürmek için `Skip` yan tümcesiyle `Take` yan tümcesini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d88cd-111">You can use the `Take` clause with the `Skip` clause to return a range of data from any segment of a query.</span></span> <span data-ttu-id="d88cd-112">Bunu yapmak için aralığın ilk öğesinin dizinini `Skip` yan tümcesine ve aralığın boyutunu `Take` yan tümcesine geçirin.</span><span class="sxs-lookup"><span data-stu-id="d88cd-112">To do this, pass the index of the first element of the range to the `Skip` clause and the size of the range to the `Take` clause.</span></span> <span data-ttu-id="d88cd-113">Bu durumda, `Take` yan tümcesinin `Skip` yan tümcesinden sonra belirtilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="d88cd-113">In this case, the `Take` clause must be specified after the `Skip` clause.</span></span>  
  
 <span data-ttu-id="d88cd-114">Bir sorguda `Take` yan tümcesini kullandığınızda, sonuçların, `Take` yan tümcesinin amaçlanan sonuçları içermesini sağlayacak bir sırada döndürüldüğünden emin olmanız da gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="d88cd-114">When you use the `Take` clause in a query, you may also need to ensure that the results are returned in an order that will enable the `Take` clause to include the intended results.</span></span> <span data-ttu-id="d88cd-115">Sorgu sonuçlarını sıralama hakkında daha fazla bilgi için bkz. [order by yan tümcesi](../../../visual-basic/language-reference/queries/order-by-clause.md).</span><span class="sxs-lookup"><span data-stu-id="d88cd-115">For more information about ordering query results, see [Order By Clause](../../../visual-basic/language-reference/queries/order-by-clause.md).</span></span>  
  
 <span data-ttu-id="d88cd-116">Belirtilen koşula bağlı olarak yalnızca belirli öğelerin döndürüleceğini belirtmek için `TakeWhile` yan tümcesini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d88cd-116">You can use the `TakeWhile` clause to specify that only certain elements be returned, depending on a supplied condition.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d88cd-117">Örnek</span><span class="sxs-lookup"><span data-stu-id="d88cd-117">Example</span></span>  
 <span data-ttu-id="d88cd-118">Aşağıdaki kod örneği, sayfalardaki bir sorgudan veri döndürmek için `Skip` yan tümcesiyle birlikte `Take` yan tümcesini kullanır.</span><span class="sxs-lookup"><span data-stu-id="d88cd-118">The following code example uses the `Take` clause together with the `Skip` clause to return data from a query in pages.</span></span> <span data-ttu-id="d88cd-119">GetCustomers işlevi, sağlanan başlangıç dizini değerine kadar listedeki müşterileri atlamak için `Skip` yan tümcesini kullanır ve bu dizin değerinden başlayan müşterilerin bir sayfasını döndürmek için `Take` yan tümcesini kullanır.</span><span class="sxs-lookup"><span data-stu-id="d88cd-119">The GetCustomers function uses the `Skip` clause to bypass the customers in the list until the supplied starting index value, and uses the `Take` clause to return a page of customers starting from that index value.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="d88cd-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d88cd-120">See also</span></span>

- [<span data-ttu-id="d88cd-121">Visual Basic LINQ 'e giriş</span><span class="sxs-lookup"><span data-stu-id="d88cd-121">Introduction to LINQ in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [<span data-ttu-id="d88cd-122">Sorgular</span><span class="sxs-lookup"><span data-stu-id="d88cd-122">Queries</span></span>](../../../visual-basic/language-reference/queries/index.md)
- [<span data-ttu-id="d88cd-123">Select Yan Tümcesi</span><span class="sxs-lookup"><span data-stu-id="d88cd-123">Select Clause</span></span>](../../../visual-basic/language-reference/queries/select-clause.md)
- [<span data-ttu-id="d88cd-124">From Yan Tümcesi</span><span class="sxs-lookup"><span data-stu-id="d88cd-124">From Clause</span></span>](../../../visual-basic/language-reference/queries/from-clause.md)
- [<span data-ttu-id="d88cd-125">Order By Yan Tümcesi</span><span class="sxs-lookup"><span data-stu-id="d88cd-125">Order By Clause</span></span>](../../../visual-basic/language-reference/queries/order-by-clause.md)
- [<span data-ttu-id="d88cd-126">Take While Yan Tümcesi</span><span class="sxs-lookup"><span data-stu-id="d88cd-126">Take While Clause</span></span>](../../../visual-basic/language-reference/queries/take-while-clause.md)
- [<span data-ttu-id="d88cd-127">Skip Yan Tümcesi</span><span class="sxs-lookup"><span data-stu-id="d88cd-127">Skip Clause</span></span>](../../../visual-basic/language-reference/queries/skip-clause.md)
