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
ms.openlocfilehash: 0dddb411af1b4ee269e091c07553a94589d90b2c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33604035"
---
# <a name="take-clause-visual-basic"></a><span data-ttu-id="8f425-102">Take Tümcesi (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8f425-102">Take Clause (Visual Basic)</span></span>
<span data-ttu-id="8f425-103">Belirtilen sayıda bitişik öğeyi koleksiyonu başından döndürür.</span><span class="sxs-lookup"><span data-stu-id="8f425-103">Returns a specified number of contiguous elements from the start of a collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8f425-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="8f425-104">Syntax</span></span>  
  
```  
Take count  
```  
  
## <a name="parts"></a><span data-ttu-id="8f425-105">Bölümler</span><span class="sxs-lookup"><span data-stu-id="8f425-105">Parts</span></span>  
 `count`  
 <span data-ttu-id="8f425-106">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="8f425-106">Required.</span></span> <span data-ttu-id="8f425-107">Bir değer veya sıradaki döndürülecek sayısını veren ifade.</span><span class="sxs-lookup"><span data-stu-id="8f425-107">A value or an expression that evaluates to the number of elements of the sequence to return.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8f425-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="8f425-108">Remarks</span></span>  
 <span data-ttu-id="8f425-109">`Take` Yan tümcesinde belirtilen sayıda sonuç listesini başından bitişik öğeyi dahil etmek bir sorgu neden olur.</span><span class="sxs-lookup"><span data-stu-id="8f425-109">The `Take` clause causes a query to include a specified number of contiguous elements from the start of a results list.</span></span> <span data-ttu-id="8f425-110">Eklenecek öğe sayısı tarafından belirtilen `count` parametresi.</span><span class="sxs-lookup"><span data-stu-id="8f425-110">The number of elements to include is specified by the `count` parameter.</span></span>  
  
 <span data-ttu-id="8f425-111">Kullanabileceğiniz `Take` yan tümcesiyle birlikte `Skip` herhangi bir sorgu segment veri aralığını döndürülecek yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="8f425-111">You can use the `Take` clause with the `Skip` clause to return a range of data from any segment of a query.</span></span> <span data-ttu-id="8f425-112">Bunu yapmak için aralığın ilk öğenin dizini geçirmek `Skip` yan tümcesi ve aralığa boyutunu `Take` yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="8f425-112">To do this, pass the index of the first element of the range to the `Skip` clause and the size of the range to the `Take` clause.</span></span> <span data-ttu-id="8f425-113">Bu durumda, `Take` yan tümcesinde belirtilen, sonra `Skip` yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="8f425-113">In this case, the `Take` clause must be specified after the `Skip` clause.</span></span>  
  
 <span data-ttu-id="8f425-114">Kullandığınızda `Take` yan tümcesinin sorgudaki de ihtiyacınız olabilecek sonuçları etkinleştirecek bir sırada döndürüldüğünden emin olmak `Take` amaçlanan sonuçlara dahil etmek için yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="8f425-114">When you use the `Take` clause in a query, you may also need to ensure that the results are returned in an order that will enable the `Take` clause to include the intended results.</span></span> <span data-ttu-id="8f425-115">Sorgu sonuçlarını sıralama hakkında daha fazla bilgi için bkz: [Order By yan tümcesi](../../../visual-basic/language-reference/queries/order-by-clause.md).</span><span class="sxs-lookup"><span data-stu-id="8f425-115">For more information about ordering query results, see [Order By Clause](../../../visual-basic/language-reference/queries/order-by-clause.md).</span></span>  
  
 <span data-ttu-id="8f425-116">Kullanabileceğiniz `TakeWhile` yan tümcesini yalnızca belirli öğeler, sağlanan bir koşula göre döndürülmesi gerektiğini belirtin.</span><span class="sxs-lookup"><span data-stu-id="8f425-116">You can use the `TakeWhile` clause to specify that only certain elements be returned, depending on a supplied condition.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8f425-117">Örnek</span><span class="sxs-lookup"><span data-stu-id="8f425-117">Example</span></span>  
 <span data-ttu-id="8f425-118">Aşağıdaki kod örneğinde `Take` yan tümcesi ile birlikte `Skip` sayfaları sorguda veri döndürmek için yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="8f425-118">The following code example uses the `Take` clause together with the `Skip` clause to return data from a query in pages.</span></span> <span data-ttu-id="8f425-119">GetCustomers işlev kullanır `Skip` sağlanan başlangıç dizini kadar değeri ve kullandığı listesinde müşterileri atlamak için yan tümceyi `Take` yan tümcesi bu dizin değerden başlayan müşteriler, bir sayfaya dönün.</span><span class="sxs-lookup"><span data-stu-id="8f425-119">The GetCustomers function uses the `Skip` clause to bypass the customers in the list until the supplied starting index value, and uses the `Take` clause to return a page of customers starting from that index value.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#1](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/take-clause_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="8f425-120">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="8f425-120">See Also</span></span>  
 [<span data-ttu-id="8f425-121">Visual Basic'de LINQ'e giriş</span><span class="sxs-lookup"><span data-stu-id="8f425-121">Introduction to LINQ in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
 [<span data-ttu-id="8f425-122">Sorgular</span><span class="sxs-lookup"><span data-stu-id="8f425-122">Queries</span></span>](../../../visual-basic/language-reference/queries/queries.md)  
 [<span data-ttu-id="8f425-123">Select Yan Tümcesi</span><span class="sxs-lookup"><span data-stu-id="8f425-123">Select Clause</span></span>](../../../visual-basic/language-reference/queries/select-clause.md)  
 [<span data-ttu-id="8f425-124">From Yan Tümcesi</span><span class="sxs-lookup"><span data-stu-id="8f425-124">From Clause</span></span>](../../../visual-basic/language-reference/queries/from-clause.md)  
 [<span data-ttu-id="8f425-125">Order By Yan Tümcesi</span><span class="sxs-lookup"><span data-stu-id="8f425-125">Order By Clause</span></span>](../../../visual-basic/language-reference/queries/order-by-clause.md)  
 [<span data-ttu-id="8f425-126">Take While Yan Tümcesi</span><span class="sxs-lookup"><span data-stu-id="8f425-126">Take While Clause</span></span>](../../../visual-basic/language-reference/queries/take-while-clause.md)  
 [<span data-ttu-id="8f425-127">Skip Yan Tümcesi</span><span class="sxs-lookup"><span data-stu-id="8f425-127">Skip Clause</span></span>](../../../visual-basic/language-reference/queries/skip-clause.md)
