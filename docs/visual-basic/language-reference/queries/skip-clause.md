---
title: "Skip Tümcesi (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.QuerySkip
helpviewer_keywords:
- queries [Visual Basic], Skip
- Skip statement [Visual Basic]
- Skip clause [Visual Basic]
ms.assetid: f00eb172-3907-4c43-9745-d8546ab86234
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 508f3c094df4c834305bcb4a78223c1cee82b1c8
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="skip-clause-visual-basic"></a><span data-ttu-id="7518a-102">Skip Tümcesi (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7518a-102">Skip Clause (Visual Basic)</span></span>
<span data-ttu-id="7518a-103">Belirtilen bir koleksiyondaki öğelerin sayısı atlar ve kalan öğeleri döndürür.</span><span class="sxs-lookup"><span data-stu-id="7518a-103">Bypasses a specified number of elements in a collection and then returns the remaining elements.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7518a-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="7518a-104">Syntax</span></span>  
  
```  
Skip count  
```  
  
## <a name="parts"></a><span data-ttu-id="7518a-105">Bölümler</span><span class="sxs-lookup"><span data-stu-id="7518a-105">Parts</span></span>  
 `count`  
 <span data-ttu-id="7518a-106">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="7518a-106">Required.</span></span> <span data-ttu-id="7518a-107">Bir değer veya atlamak için sıradaki sayısını veren ifade.</span><span class="sxs-lookup"><span data-stu-id="7518a-107">A value or an expression that evaluates to the number of elements of the sequence to skip.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7518a-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="7518a-108">Remarks</span></span>  
 <span data-ttu-id="7518a-109">`Skip` Yan tümcesi sonuçları listesinin başında öğeleri atlamak ve kalan öğeleri döndürmek bir sorgu neden olur.</span><span class="sxs-lookup"><span data-stu-id="7518a-109">The `Skip` clause causes a query to bypass elements at the beginning of a results list and return the remaining elements.</span></span> <span data-ttu-id="7518a-110">Atlamayı öğelerin sayısı tarafından tanımlanan `count` parametresi.</span><span class="sxs-lookup"><span data-stu-id="7518a-110">The number of elements to skip is identified by the `count` parameter.</span></span>  
  
 <span data-ttu-id="7518a-111">Kullanabileceğiniz `Skip` yan tümcesiyle birlikte `Take` herhangi bir sorgu segment veri aralığını döndürülecek yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="7518a-111">You can use the `Skip` clause with the `Take` clause to return a range of data from any segment of a query.</span></span> <span data-ttu-id="7518a-112">Bunu yapmak için aralığın ilk öğenin dizini geçirmek `Skip` yan tümcesi ve aralığa boyutunu `Take` yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="7518a-112">To do this, pass the index of the first element of the range to the `Skip` clause and the size of the range to the `Take` clause.</span></span>  
  
 <span data-ttu-id="7518a-113">Kullandığınızda `Skip` yan tümcesinin sorgudaki de ihtiyacınız olabilecek sonuçları etkinleştirecek bir sırada döndürüldüğünden emin olmak `Skip` hedeflenen sonuçları atlamak için yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="7518a-113">When you use the `Skip` clause in a query, you may also need to ensure that the results are returned in an order that will enable the `Skip` clause to bypass the intended results.</span></span> <span data-ttu-id="7518a-114">Sorgu sonuçlarını sıralama hakkında daha fazla bilgi için bkz: [Order By yan tümcesi](../../../visual-basic/language-reference/queries/order-by-clause.md).</span><span class="sxs-lookup"><span data-stu-id="7518a-114">For more information about ordering query results, see [Order By Clause](../../../visual-basic/language-reference/queries/order-by-clause.md).</span></span>  
  
 <span data-ttu-id="7518a-115">Kullanabileceğiniz `SkipWhile` yan tümcesi yalnızca belirli öğeler, sağlanan bir koşula göre göz ardı edilir olduğunu belirtmek için.</span><span class="sxs-lookup"><span data-stu-id="7518a-115">You can use the `SkipWhile` clause to specify that only certain elements are ignored, depending on a supplied condition.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7518a-116">Örnek</span><span class="sxs-lookup"><span data-stu-id="7518a-116">Example</span></span>  
 <span data-ttu-id="7518a-117">Aşağıdaki kod örneğinde `Skip` yan tümcesi ile birlikte `Take` sayfaları sorguda veri döndürmek için yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="7518a-117">The following code example uses the `Skip` clause together with the `Take` clause to return data from a query in pages.</span></span> <span data-ttu-id="7518a-118">`GetCustomers` İşlev kullanır `Skip` sağlanan başlangıç dizini kadar değeri ve kullandığı listesinde müşterileri atlamak için yan tümceyi `Take` yan tümcesi bu dizin değerden başlayan müşteriler, bir sayfaya dönün.</span><span class="sxs-lookup"><span data-stu-id="7518a-118">The `GetCustomers` function uses the `Skip` clause to bypass the customers in the list until the supplied starting index value, and uses the `Take` clause to return a page of customers starting from that index value.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#1](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/skip-clause_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="7518a-119">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="7518a-119">See Also</span></span>  
 [<span data-ttu-id="7518a-120">Visual Basic'de LINQ'e giriş</span><span class="sxs-lookup"><span data-stu-id="7518a-120">Introduction to LINQ in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
 [<span data-ttu-id="7518a-121">Sorguları</span><span class="sxs-lookup"><span data-stu-id="7518a-121">Queries</span></span>](../../../visual-basic/language-reference/queries/queries.md)  
 [<span data-ttu-id="7518a-122">Select tümcesi</span><span class="sxs-lookup"><span data-stu-id="7518a-122">Select Clause</span></span>](../../../visual-basic/language-reference/queries/select-clause.md)  
 [<span data-ttu-id="7518a-123">From yan tümcesi</span><span class="sxs-lookup"><span data-stu-id="7518a-123">From Clause</span></span>](../../../visual-basic/language-reference/queries/from-clause.md)  
 [<span data-ttu-id="7518a-124">Order By tümcesi</span><span class="sxs-lookup"><span data-stu-id="7518a-124">Order By Clause</span></span>](../../../visual-basic/language-reference/queries/order-by-clause.md)  
 [<span data-ttu-id="7518a-125">Skip While tümcesi</span><span class="sxs-lookup"><span data-stu-id="7518a-125">Skip While Clause</span></span>](../../../visual-basic/language-reference/queries/skip-while-clause.md)  
 [<span data-ttu-id="7518a-126">Take tümcesi</span><span class="sxs-lookup"><span data-stu-id="7518a-126">Take Clause</span></span>](../../../visual-basic/language-reference/queries/take-clause.md)
