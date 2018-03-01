---
title: "Take Tümcesi (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.QueryTake
helpviewer_keywords:
- Take statement [Visual Basic]
- queries [Visual Basic], Take
- Take clause [Visual Basic]
ms.assetid: 77bf87b2-1476-4456-957f-fee922fbad8c
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: ee289a24c15226126a526af116ed53b4a9055b35
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="take-clause-visual-basic"></a><span data-ttu-id="d95e1-102">Take Tümcesi (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d95e1-102">Take Clause (Visual Basic)</span></span>
<span data-ttu-id="d95e1-103">Belirtilen sayıda bitişik öğeyi koleksiyonu başından döndürür.</span><span class="sxs-lookup"><span data-stu-id="d95e1-103">Returns a specified number of contiguous elements from the start of a collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d95e1-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d95e1-104">Syntax</span></span>  
  
```  
Take count  
```  
  
## <a name="parts"></a><span data-ttu-id="d95e1-105">Bölümler</span><span class="sxs-lookup"><span data-stu-id="d95e1-105">Parts</span></span>  
 `count`  
 <span data-ttu-id="d95e1-106">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="d95e1-106">Required.</span></span> <span data-ttu-id="d95e1-107">Bir değer veya sıradaki döndürülecek sayısını veren ifade.</span><span class="sxs-lookup"><span data-stu-id="d95e1-107">A value or an expression that evaluates to the number of elements of the sequence to return.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d95e1-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d95e1-108">Remarks</span></span>  
 <span data-ttu-id="d95e1-109">`Take` Yan tümcesinde belirtilen sayıda sonuç listesini başından bitişik öğeyi dahil etmek bir sorgu neden olur.</span><span class="sxs-lookup"><span data-stu-id="d95e1-109">The `Take` clause causes a query to include a specified number of contiguous elements from the start of a results list.</span></span> <span data-ttu-id="d95e1-110">Eklenecek öğe sayısı tarafından belirtilen `count` parametresi.</span><span class="sxs-lookup"><span data-stu-id="d95e1-110">The number of elements to include is specified by the `count` parameter.</span></span>  
  
 <span data-ttu-id="d95e1-111">Kullanabileceğiniz `Take` yan tümcesiyle birlikte `Skip` herhangi bir sorgu segment veri aralığını döndürülecek yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="d95e1-111">You can use the `Take` clause with the `Skip` clause to return a range of data from any segment of a query.</span></span> <span data-ttu-id="d95e1-112">Bunu yapmak için aralığın ilk öğenin dizini geçirmek `Skip` yan tümcesi ve aralığa boyutunu `Take` yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="d95e1-112">To do this, pass the index of the first element of the range to the `Skip` clause and the size of the range to the `Take` clause.</span></span> <span data-ttu-id="d95e1-113">Bu durumda, `Take` yan tümcesinde belirtilen, sonra `Skip` yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="d95e1-113">In this case, the `Take` clause must be specified after the `Skip` clause.</span></span>  
  
 <span data-ttu-id="d95e1-114">Kullandığınızda `Take` yan tümcesinin sorgudaki de ihtiyacınız olabilecek sonuçları etkinleştirecek bir sırada döndürüldüğünden emin olmak `Take` amaçlanan sonuçlara dahil etmek için yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="d95e1-114">When you use the `Take` clause in a query, you may also need to ensure that the results are returned in an order that will enable the `Take` clause to include the intended results.</span></span> <span data-ttu-id="d95e1-115">Sorgu sonuçlarını sıralama hakkında daha fazla bilgi için bkz: [Order By yan tümcesi](../../../visual-basic/language-reference/queries/order-by-clause.md).</span><span class="sxs-lookup"><span data-stu-id="d95e1-115">For more information about ordering query results, see [Order By Clause](../../../visual-basic/language-reference/queries/order-by-clause.md).</span></span>  
  
 <span data-ttu-id="d95e1-116">Kullanabileceğiniz `TakeWhile` yan tümcesini yalnızca belirli öğeler, sağlanan bir koşula göre döndürülmesi gerektiğini belirtin.</span><span class="sxs-lookup"><span data-stu-id="d95e1-116">You can use the `TakeWhile` clause to specify that only certain elements be returned, depending on a supplied condition.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d95e1-117">Örnek</span><span class="sxs-lookup"><span data-stu-id="d95e1-117">Example</span></span>  
 <span data-ttu-id="d95e1-118">Aşağıdaki kod örneğinde `Take` yan tümcesi ile birlikte `Skip` sayfaları sorguda veri döndürmek için yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="d95e1-118">The following code example uses the `Take` clause together with the `Skip` clause to return data from a query in pages.</span></span> <span data-ttu-id="d95e1-119">GetCustomers işlev kullanır `Skip` sağlanan başlangıç dizini kadar değeri ve kullandığı listesinde müşterileri atlamak için yan tümceyi `Take` yan tümcesi bu dizin değerden başlayan müşteriler, bir sayfaya dönün.</span><span class="sxs-lookup"><span data-stu-id="d95e1-119">The GetCustomers function uses the `Skip` clause to bypass the customers in the list until the supplied starting index value, and uses the `Take` clause to return a page of customers starting from that index value.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#1](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/take-clause_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="d95e1-120">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="d95e1-120">See Also</span></span>  
 [<span data-ttu-id="d95e1-121">Visual Basic'de LINQ'e giriş</span><span class="sxs-lookup"><span data-stu-id="d95e1-121">Introduction to LINQ in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
 [<span data-ttu-id="d95e1-122">Sorguları</span><span class="sxs-lookup"><span data-stu-id="d95e1-122">Queries</span></span>](../../../visual-basic/language-reference/queries/queries.md)  
 [<span data-ttu-id="d95e1-123">Select tümcesi</span><span class="sxs-lookup"><span data-stu-id="d95e1-123">Select Clause</span></span>](../../../visual-basic/language-reference/queries/select-clause.md)  
 [<span data-ttu-id="d95e1-124">From yan tümcesi</span><span class="sxs-lookup"><span data-stu-id="d95e1-124">From Clause</span></span>](../../../visual-basic/language-reference/queries/from-clause.md)  
 [<span data-ttu-id="d95e1-125">Order By tümcesi</span><span class="sxs-lookup"><span data-stu-id="d95e1-125">Order By Clause</span></span>](../../../visual-basic/language-reference/queries/order-by-clause.md)  
 [<span data-ttu-id="d95e1-126">Take While tümcesi</span><span class="sxs-lookup"><span data-stu-id="d95e1-126">Take While Clause</span></span>](../../../visual-basic/language-reference/queries/take-while-clause.md)  
 [<span data-ttu-id="d95e1-127">Skip tümcesi</span><span class="sxs-lookup"><span data-stu-id="d95e1-127">Skip Clause</span></span>](../../../visual-basic/language-reference/queries/skip-clause.md)
