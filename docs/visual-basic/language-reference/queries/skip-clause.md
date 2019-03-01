---
title: Skip Tümcesi (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.QuerySkip
helpviewer_keywords:
- queries [Visual Basic], Skip
- Skip statement [Visual Basic]
- Skip clause [Visual Basic]
ms.assetid: f00eb172-3907-4c43-9745-d8546ab86234
ms.openlocfilehash: 8441e619cdbd18545be72fd701c2cc9b1cf495d9
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/28/2019
ms.locfileid: "56971243"
---
# <a name="skip-clause-visual-basic"></a><span data-ttu-id="c25aa-102">Skip Tümcesi (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c25aa-102">Skip Clause (Visual Basic)</span></span>
<span data-ttu-id="c25aa-103">Belirtilen sayıda bir koleksiyondaki öğeleri atlar ve kalan öğeleri döndürür.</span><span class="sxs-lookup"><span data-stu-id="c25aa-103">Bypasses a specified number of elements in a collection and then returns the remaining elements.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c25aa-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c25aa-104">Syntax</span></span>  
  
```  
Skip count  
```  
  
## <a name="parts"></a><span data-ttu-id="c25aa-105">Bölümler</span><span class="sxs-lookup"><span data-stu-id="c25aa-105">Parts</span></span>  
 `count`  
 <span data-ttu-id="c25aa-106">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="c25aa-106">Required.</span></span> <span data-ttu-id="c25aa-107">Bir değer veya atlamak için dizisinin öğe sayısı için değerlendirilen bir ifade.</span><span class="sxs-lookup"><span data-stu-id="c25aa-107">A value or an expression that evaluates to the number of elements of the sequence to skip.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c25aa-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c25aa-108">Remarks</span></span>  
 <span data-ttu-id="c25aa-109">`Skip` Yan tümcesi bir sorgu sonuç listesini başındaki öğeleri atlamak ve kalan öğeleri döndürmek neden olur.</span><span class="sxs-lookup"><span data-stu-id="c25aa-109">The `Skip` clause causes a query to bypass elements at the beginning of a results list and return the remaining elements.</span></span> <span data-ttu-id="c25aa-110">Geçilecek öğelerin sayısı tarafından tanımlanan `count` parametresi.</span><span class="sxs-lookup"><span data-stu-id="c25aa-110">The number of elements to skip is identified by the `count` parameter.</span></span>  
  
 <span data-ttu-id="c25aa-111">Kullanabileceğiniz `Skip` yan tümcesiyle `Take` yan tümcesi bir sorgu herhangi bir segmentten veri aralığı döndürülecek.</span><span class="sxs-lookup"><span data-stu-id="c25aa-111">You can use the `Skip` clause with the `Take` clause to return a range of data from any segment of a query.</span></span> <span data-ttu-id="c25aa-112">Bunu yapmak için dizini aralığın ilk öğesine geçirmek `Skip` yan tümcesi ve aralık için boyutunu `Take` yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="c25aa-112">To do this, pass the index of the first element of the range to the `Skip` clause and the size of the range to the `Take` clause.</span></span>  
  
 <span data-ttu-id="c25aa-113">Kullanırken `Skip` sorgu yan tümcesi, aynı zamanda gerekebilir sonuçları olanak sağlayacak bir sırada döndürüldüğünden emin olunması `Skip` hedeflenen sonuçları atlamak için yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="c25aa-113">When you use the `Skip` clause in a query, you may also need to ensure that the results are returned in an order that will enable the `Skip` clause to bypass the intended results.</span></span> <span data-ttu-id="c25aa-114">Sorgu sonuçlarını sıralama hakkında daha fazla bilgi için bkz. [Order By yan tümcesi](../../../visual-basic/language-reference/queries/order-by-clause.md).</span><span class="sxs-lookup"><span data-stu-id="c25aa-114">For more information about ordering query results, see [Order By Clause](../../../visual-basic/language-reference/queries/order-by-clause.md).</span></span>  
  
 <span data-ttu-id="c25aa-115">Kullanabileceğiniz `SkipWhile` yan tümcesi yalnızca belirli öğeleri, belirtilen bir koşula bağlı olarak göz ardı edilir olduğunu belirtmek için.</span><span class="sxs-lookup"><span data-stu-id="c25aa-115">You can use the `SkipWhile` clause to specify that only certain elements are ignored, depending on a supplied condition.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c25aa-116">Örnek</span><span class="sxs-lookup"><span data-stu-id="c25aa-116">Example</span></span>  
 <span data-ttu-id="c25aa-117">Aşağıdaki kod örneğinde `Skip` yan tümcesi ile birlikte `Take` veri sayfalarında sorgudan döndürülecek yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="c25aa-117">The following code example uses the `Skip` clause together with the `Take` clause to return data from a query in pages.</span></span> <span data-ttu-id="c25aa-118">`GetCustomers` İşlevini kullanan `Skip` sağlanan başlangıç dizini kadar değer ve kullanımlar listesinde müşterileri atlamak için yan tümcesi `Take` yan tümcesi bu dizin değerden başlayan müşteriler bir sayfaya dönün.</span><span class="sxs-lookup"><span data-stu-id="c25aa-118">The `GetCustomers` function uses the `Skip` clause to bypass the customers in the list until the supplied starting index value, and uses the `Take` clause to return a page of customers starting from that index value.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="c25aa-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c25aa-119">See also</span></span>
- [<span data-ttu-id="c25aa-120">Visual Basic'de LINQ'e giriş</span><span class="sxs-lookup"><span data-stu-id="c25aa-120">Introduction to LINQ in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [<span data-ttu-id="c25aa-121">Sorgular</span><span class="sxs-lookup"><span data-stu-id="c25aa-121">Queries</span></span>](../../../visual-basic/language-reference/queries/index.md)
- [<span data-ttu-id="c25aa-122">Select Yan Tümcesi</span><span class="sxs-lookup"><span data-stu-id="c25aa-122">Select Clause</span></span>](../../../visual-basic/language-reference/queries/select-clause.md)
- [<span data-ttu-id="c25aa-123">From Yan Tümcesi</span><span class="sxs-lookup"><span data-stu-id="c25aa-123">From Clause</span></span>](../../../visual-basic/language-reference/queries/from-clause.md)
- [<span data-ttu-id="c25aa-124">Order By Yan Tümcesi</span><span class="sxs-lookup"><span data-stu-id="c25aa-124">Order By Clause</span></span>](../../../visual-basic/language-reference/queries/order-by-clause.md)
- [<span data-ttu-id="c25aa-125">Skip While Yan Tümcesi</span><span class="sxs-lookup"><span data-stu-id="c25aa-125">Skip While Clause</span></span>](../../../visual-basic/language-reference/queries/skip-while-clause.md)
- [<span data-ttu-id="c25aa-126">Take Yan Tümcesi</span><span class="sxs-lookup"><span data-stu-id="c25aa-126">Take Clause</span></span>](../../../visual-basic/language-reference/queries/take-clause.md)
