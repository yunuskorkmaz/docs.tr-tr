---
title: Take Tümcesi (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.QueryTake
helpviewer_keywords:
- Take statement [Visual Basic]
- queries [Visual Basic], Take
- Take clause [Visual Basic]
ms.assetid: 77bf87b2-1476-4456-957f-fee922fbad8c
ms.openlocfilehash: cb109eaf43fee19b77ac690492b85919c9d78301
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58816960"
---
# <a name="take-clause-visual-basic"></a><span data-ttu-id="ef0f9-102">Take Tümcesi (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ef0f9-102">Take Clause (Visual Basic)</span></span>
<span data-ttu-id="ef0f9-103">Bir koleksiyon başlangıcından belirtilen bir bitişik öğelerin sayısını döndürür.</span><span class="sxs-lookup"><span data-stu-id="ef0f9-103">Returns a specified number of contiguous elements from the start of a collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ef0f9-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ef0f9-104">Syntax</span></span>  
  
```  
Take count  
```  
  
## <a name="parts"></a><span data-ttu-id="ef0f9-105">Bölümler</span><span class="sxs-lookup"><span data-stu-id="ef0f9-105">Parts</span></span>  
 `count`  
 <span data-ttu-id="ef0f9-106">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="ef0f9-106">Required.</span></span> <span data-ttu-id="ef0f9-107">Bir değer veya döndürülecek dizisinin öğe sayısı için değerlendirilen bir ifade.</span><span class="sxs-lookup"><span data-stu-id="ef0f9-107">A value or an expression that evaluates to the number of elements of the sequence to return.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ef0f9-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ef0f9-108">Remarks</span></span>  
 <span data-ttu-id="ef0f9-109">`Take` Yan tümcesi bir sorgu sonuç listesini başlangıcından bitişik öğelerin belirtilen bir sayı içerecek şekilde neden olur.</span><span class="sxs-lookup"><span data-stu-id="ef0f9-109">The `Take` clause causes a query to include a specified number of contiguous elements from the start of a results list.</span></span> <span data-ttu-id="ef0f9-110">Eklenecek öğe sayısı tarafından belirtilen `count` parametresi.</span><span class="sxs-lookup"><span data-stu-id="ef0f9-110">The number of elements to include is specified by the `count` parameter.</span></span>  
  
 <span data-ttu-id="ef0f9-111">Kullanabileceğiniz `Take` yan tümcesiyle `Skip` yan tümcesi bir sorgu herhangi bir segmentten veri aralığı döndürülecek.</span><span class="sxs-lookup"><span data-stu-id="ef0f9-111">You can use the `Take` clause with the `Skip` clause to return a range of data from any segment of a query.</span></span> <span data-ttu-id="ef0f9-112">Bunu yapmak için dizini aralığın ilk öğesine geçirmek `Skip` yan tümcesi ve aralık için boyutunu `Take` yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="ef0f9-112">To do this, pass the index of the first element of the range to the `Skip` clause and the size of the range to the `Take` clause.</span></span> <span data-ttu-id="ef0f9-113">Bu durumda, `Take` yan belirtilen, sonra `Skip` yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="ef0f9-113">In this case, the `Take` clause must be specified after the `Skip` clause.</span></span>  
  
 <span data-ttu-id="ef0f9-114">Kullanırken `Take` sorgu yan tümcesi, aynı zamanda gerekebilir sonuçları olanak sağlayacak bir sırada döndürüldüğünden emin olunması `Take` hedeflenen sonuçları içerecek şekilde yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="ef0f9-114">When you use the `Take` clause in a query, you may also need to ensure that the results are returned in an order that will enable the `Take` clause to include the intended results.</span></span> <span data-ttu-id="ef0f9-115">Sorgu sonuçlarını sıralama hakkında daha fazla bilgi için bkz. [Order By yan tümcesi](../../../visual-basic/language-reference/queries/order-by-clause.md).</span><span class="sxs-lookup"><span data-stu-id="ef0f9-115">For more information about ordering query results, see [Order By Clause](../../../visual-basic/language-reference/queries/order-by-clause.md).</span></span>  
  
 <span data-ttu-id="ef0f9-116">Kullanabileceğiniz `TakeWhile` yan tümcesini yalnızca belirli öğeleri, belirtilen bir koşula bağlı olarak verilmesini belirtin.</span><span class="sxs-lookup"><span data-stu-id="ef0f9-116">You can use the `TakeWhile` clause to specify that only certain elements be returned, depending on a supplied condition.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ef0f9-117">Örnek</span><span class="sxs-lookup"><span data-stu-id="ef0f9-117">Example</span></span>  
 <span data-ttu-id="ef0f9-118">Aşağıdaki kod örneğinde `Take` yan tümcesi ile birlikte `Skip` veri sayfalarında sorgudan döndürülecek yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="ef0f9-118">The following code example uses the `Take` clause together with the `Skip` clause to return data from a query in pages.</span></span> <span data-ttu-id="ef0f9-119">GetCustomers işlevini kullanan `Skip` sağlanan başlangıç dizini kadar değer ve kullanımlar listesinde müşterileri atlamak için yan tümcesi `Take` yan tümcesi bu dizin değerden başlayan müşteriler bir sayfaya dönün.</span><span class="sxs-lookup"><span data-stu-id="ef0f9-119">The GetCustomers function uses the `Skip` clause to bypass the customers in the list until the supplied starting index value, and uses the `Take` clause to return a page of customers starting from that index value.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="ef0f9-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ef0f9-120">See also</span></span>

- [<span data-ttu-id="ef0f9-121">Visual Basic'de LINQ'e giriş</span><span class="sxs-lookup"><span data-stu-id="ef0f9-121">Introduction to LINQ in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [<span data-ttu-id="ef0f9-122">Sorgular</span><span class="sxs-lookup"><span data-stu-id="ef0f9-122">Queries</span></span>](../../../visual-basic/language-reference/queries/index.md)
- [<span data-ttu-id="ef0f9-123">Select Yan Tümcesi</span><span class="sxs-lookup"><span data-stu-id="ef0f9-123">Select Clause</span></span>](../../../visual-basic/language-reference/queries/select-clause.md)
- [<span data-ttu-id="ef0f9-124">From Yan Tümcesi</span><span class="sxs-lookup"><span data-stu-id="ef0f9-124">From Clause</span></span>](../../../visual-basic/language-reference/queries/from-clause.md)
- [<span data-ttu-id="ef0f9-125">Order By Yan Tümcesi</span><span class="sxs-lookup"><span data-stu-id="ef0f9-125">Order By Clause</span></span>](../../../visual-basic/language-reference/queries/order-by-clause.md)
- [<span data-ttu-id="ef0f9-126">Take While Yan Tümcesi</span><span class="sxs-lookup"><span data-stu-id="ef0f9-126">Take While Clause</span></span>](../../../visual-basic/language-reference/queries/take-while-clause.md)
- [<span data-ttu-id="ef0f9-127">Skip Yan Tümcesi</span><span class="sxs-lookup"><span data-stu-id="ef0f9-127">Skip Clause</span></span>](../../../visual-basic/language-reference/queries/skip-clause.md)
