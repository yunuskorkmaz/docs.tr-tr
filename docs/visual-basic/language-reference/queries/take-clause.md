---
title: Take Yan Tümcesi
ms.date: 07/20/2015
f1_keywords:
- vb.QueryTake
helpviewer_keywords:
- Take statement [Visual Basic]
- queries [Visual Basic], Take
- Take clause [Visual Basic]
ms.assetid: 77bf87b2-1476-4456-957f-fee922fbad8c
ms.openlocfilehash: f2377d8d1635912885a310b2b0429a6a00083b47
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90869671"
---
# <a name="take-clause-visual-basic"></a><span data-ttu-id="93579-102">Take Tümcesi (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="93579-102">Take Clause (Visual Basic)</span></span>

<span data-ttu-id="93579-103">Bir koleksiyonun başından itibaren belirtilen sayıda bitişik öğeyi döndürür.</span><span class="sxs-lookup"><span data-stu-id="93579-103">Returns a specified number of contiguous elements from the start of a collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="93579-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="93579-104">Syntax</span></span>  
  
```vb  
Take count  
```  
  
## <a name="parts"></a><span data-ttu-id="93579-105">Bölümler</span><span class="sxs-lookup"><span data-stu-id="93579-105">Parts</span></span>  

 `count`  
 <span data-ttu-id="93579-106">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="93579-106">Required.</span></span> <span data-ttu-id="93579-107">Döndürülecek dizi öğe sayısını değerlendiren bir değer veya ifade.</span><span class="sxs-lookup"><span data-stu-id="93579-107">A value or an expression that evaluates to the number of elements of the sequence to return.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="93579-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="93579-108">Remarks</span></span>  

 <span data-ttu-id="93579-109">`Take`Yan tümce bir sorgunun bir sonuç listesinin başından itibaren belirtilen sayıda bitişik öğe içermesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="93579-109">The `Take` clause causes a query to include a specified number of contiguous elements from the start of a results list.</span></span> <span data-ttu-id="93579-110">Dahil edilecek öğe sayısı parametresi tarafından belirtilir `count` .</span><span class="sxs-lookup"><span data-stu-id="93579-110">The number of elements to include is specified by the `count` parameter.</span></span>  
  
 <span data-ttu-id="93579-111">`Take` `Skip` Bir sorgunun herhangi bir segmentinden bir veri aralığı döndürmek için yan tümcesini kullanın.</span><span class="sxs-lookup"><span data-stu-id="93579-111">You can use the `Take` clause with the `Skip` clause to return a range of data from any segment of a query.</span></span> <span data-ttu-id="93579-112">Bunu yapmak için aralığın ilk öğesinin dizinini `Skip` yan tümcesine ve aralığın boyutunu `Take` yan tümcesine geçirin.</span><span class="sxs-lookup"><span data-stu-id="93579-112">To do this, pass the index of the first element of the range to the `Skip` clause and the size of the range to the `Take` clause.</span></span> <span data-ttu-id="93579-113">Bu durumda yan tümce, yan `Take` tümcesinden sonra belirtilmelidir `Skip` .</span><span class="sxs-lookup"><span data-stu-id="93579-113">In this case, the `Take` clause must be specified after the `Skip` clause.</span></span>  
  
 <span data-ttu-id="93579-114">`Take`Bir sorguda yan tümcesini kullandığınızda, sonuçların `Take` amaçlanan sonuçları dahil etmek için yan tümce sağlayacak bir sırada döndürüldüğünden de emin olmanız gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="93579-114">When you use the `Take` clause in a query, you may also need to ensure that the results are returned in an order that will enable the `Take` clause to include the intended results.</span></span> <span data-ttu-id="93579-115">Sorgu sonuçlarını sıralama hakkında daha fazla bilgi için bkz. [order by yan tümcesi](order-by-clause.md).</span><span class="sxs-lookup"><span data-stu-id="93579-115">For more information about ordering query results, see [Order By Clause](order-by-clause.md).</span></span>  
  
 <span data-ttu-id="93579-116">`TakeWhile`Belirtilen koşula bağlı olarak yalnızca belirli öğelerin döndürüleceğini belirtmek için yan tümcesini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="93579-116">You can use the `TakeWhile` clause to specify that only certain elements be returned, depending on a supplied condition.</span></span>  
  
## <a name="example"></a><span data-ttu-id="93579-117">Örnek</span><span class="sxs-lookup"><span data-stu-id="93579-117">Example</span></span>  

 <span data-ttu-id="93579-118">Aşağıdaki kod örneği, yan tümcesini, `Take` `Skip` sayfalardaki bir sorgudan veri döndürmek için yan tümcesiyle birlikte kullanır.</span><span class="sxs-lookup"><span data-stu-id="93579-118">The following code example uses the `Take` clause together with the `Skip` clause to return data from a query in pages.</span></span> <span data-ttu-id="93579-119">GetCustomers işlevi, `Skip` sağlanan başlangıç dizini değerine kadar listedeki müşterileri atlamak için yan tümcesini kullanır ve `Take` Bu dizin değerinden başlayan müşterilerin bir sayfasını döndürmek için yan tümcesini kullanır.</span><span class="sxs-lookup"><span data-stu-id="93579-119">The GetCustomers function uses the `Skip` clause to bypass the customers in the list until the supplied starting index value, and uses the `Take` clause to return a page of customers starting from that index value.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="93579-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="93579-120">See also</span></span>

- [<span data-ttu-id="93579-121">Visual Basic'de LINQ'e Giriş</span><span class="sxs-lookup"><span data-stu-id="93579-121">Introduction to LINQ in Visual Basic</span></span>](../../programming-guide/language-features/linq/introduction-to-linq.md)
- [<span data-ttu-id="93579-122">Sorgular</span><span class="sxs-lookup"><span data-stu-id="93579-122">Queries</span></span>](index.md)
- [<span data-ttu-id="93579-123">Select yan tümcesi</span><span class="sxs-lookup"><span data-stu-id="93579-123">Select Clause</span></span>](select-clause.md)
- [<span data-ttu-id="93579-124">From yan tümcesi</span><span class="sxs-lookup"><span data-stu-id="93579-124">From Clause</span></span>](from-clause.md)
- [<span data-ttu-id="93579-125">Order by yan tümcesi</span><span class="sxs-lookup"><span data-stu-id="93579-125">Order By Clause</span></span>](order-by-clause.md)
- [<span data-ttu-id="93579-126">Take While Yan Tümcesi</span><span class="sxs-lookup"><span data-stu-id="93579-126">Take While Clause</span></span>](take-while-clause.md)
- [<span data-ttu-id="93579-127">Skip Yan Tümcesi</span><span class="sxs-lookup"><span data-stu-id="93579-127">Skip Clause</span></span>](skip-clause.md)
