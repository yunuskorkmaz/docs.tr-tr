---
title: "Distinct Tümcesi (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.QueryDistinct
helpviewer_keywords:
- Distinct clause [Visual Basic]
- Distinct statement [Visual Basic]
- queries [Visual Basic], Distinct
ms.assetid: 86f42614-0d8f-4ffc-b888-ce8a37a8d36a
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 6ed92d5d601c1ec329728346ac881c4fa2bad8aa
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="distinct-clause-visual-basic"></a><span data-ttu-id="01fb7-102">Distinct Tümcesi (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="01fb7-102">Distinct Clause (Visual Basic)</span></span>
<span data-ttu-id="01fb7-103">Yinelenen değerler sonraki sorgu yan tümcelerinde ortadan kaldırmak için geçerli aralık değişkeni değerlerini kısıtlar.</span><span class="sxs-lookup"><span data-stu-id="01fb7-103">Restricts the values of the current range variable to eliminate duplicate values in subsequent query clauses.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="01fb7-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="01fb7-104">Syntax</span></span>  
  
```  
Distinct  
```  
  
## <a name="remarks"></a><span data-ttu-id="01fb7-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="01fb7-105">Remarks</span></span>  
 <span data-ttu-id="01fb7-106">Kullanabileceğiniz `Distinct` benzersiz öğeleri listesini döndürmek için yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="01fb7-106">You can use the `Distinct` clause to return a list of unique items.</span></span> <span data-ttu-id="01fb7-107">`Distinct` Yan tümcesi yinelenen sorgu sonuçları yoksaymak sorgu neden olur.</span><span class="sxs-lookup"><span data-stu-id="01fb7-107">The `Distinct` clause causes the query to ignore duplicate query results.</span></span> <span data-ttu-id="01fb7-108">`Distinct` Yan tümcesi tüm tarafından belirtilen alanları dönmek için yinelenen değerler geçerlidir `Select` yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="01fb7-108">The `Distinct` clause applies to duplicate values for all return fields specified by the `Select` clause.</span></span> <span data-ttu-id="01fb7-109">Öyle değilse `Select` yan tümcesi belirtilirse, `Distinct` yan tümcesinin aralık değişkeni tanımlanan sorgu için uygulanan `From` yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="01fb7-109">If no `Select` clause is specified, the `Distinct` clause is applied to the range variable for the query identified in the `From` clause.</span></span> <span data-ttu-id="01fb7-110">Aralık değişkeni bir sabit türü değilse türdeki tüm üyelerin varolan bir sorgu sonuç eşleşiyorsa sorgu yalnızca bir sorgu sonucu göz ardı eder.</span><span class="sxs-lookup"><span data-stu-id="01fb7-110">If the range variable is not an immutable type, the query will only ignore a query result if all members of the type match an existing query result.</span></span>  
  
## <a name="example"></a><span data-ttu-id="01fb7-111">Örnek</span><span class="sxs-lookup"><span data-stu-id="01fb7-111">Example</span></span>  
 <span data-ttu-id="01fb7-112">Aşağıdaki sorgu ifadesi müşterilerin listesini ve müşteri siparişleri listesini birleştirir.</span><span class="sxs-lookup"><span data-stu-id="01fb7-112">The following query expression joins a list of customers and a list of customer orders.</span></span> <span data-ttu-id="01fb7-113">`Distinct` Benzersiz Müşteri adlarının bir listesini döndürür ve tarihleri sipariş yan tümcesi eklenmiştir.</span><span class="sxs-lookup"><span data-stu-id="01fb7-113">The `Distinct` clause is included to return a list of unique customer names and order dates.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#20](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/distinct-clause_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="01fb7-114">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="01fb7-114">See Also</span></span>  
 [<span data-ttu-id="01fb7-115">Visual Basic'de LINQ'e giriş</span><span class="sxs-lookup"><span data-stu-id="01fb7-115">Introduction to LINQ in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
 [<span data-ttu-id="01fb7-116">Sorguları</span><span class="sxs-lookup"><span data-stu-id="01fb7-116">Queries</span></span>](../../../visual-basic/language-reference/queries/queries.md)  
 [<span data-ttu-id="01fb7-117">From yan tümcesi</span><span class="sxs-lookup"><span data-stu-id="01fb7-117">From Clause</span></span>](../../../visual-basic/language-reference/queries/from-clause.md)  
 [<span data-ttu-id="01fb7-118">Select tümcesi</span><span class="sxs-lookup"><span data-stu-id="01fb7-118">Select Clause</span></span>](../../../visual-basic/language-reference/queries/select-clause.md)  
 [<span data-ttu-id="01fb7-119">Burada yan tümcesi</span><span class="sxs-lookup"><span data-stu-id="01fb7-119">Where Clause</span></span>](../../../visual-basic/language-reference/queries/where-clause.md)
