---
title: Distinct Tümcesi (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.QueryDistinct
helpviewer_keywords:
- Distinct clause [Visual Basic]
- Distinct statement [Visual Basic]
- queries [Visual Basic], Distinct
ms.assetid: 86f42614-0d8f-4ffc-b888-ce8a37a8d36a
ms.openlocfilehash: 18d09d8018303aab6a69801c84c7ec9c6ea19ca9
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2018
ms.locfileid: "43788629"
---
# <a name="distinct-clause-visual-basic"></a><span data-ttu-id="bb5b2-102">Distinct Tümcesi (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="bb5b2-102">Distinct Clause (Visual Basic)</span></span>
<span data-ttu-id="bb5b2-103">Sonraki sorgu yan tümceleri içinde yinelenen değerleri ortadan kaldırmak için geçerli aralık değişkeni değerlerini sınırlandırır.</span><span class="sxs-lookup"><span data-stu-id="bb5b2-103">Restricts the values of the current range variable to eliminate duplicate values in subsequent query clauses.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bb5b2-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="bb5b2-104">Syntax</span></span>  
  
```  
Distinct  
```  
  
## <a name="remarks"></a><span data-ttu-id="bb5b2-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="bb5b2-105">Remarks</span></span>  
 <span data-ttu-id="bb5b2-106">Kullanabileceğiniz `Distinct` yan benzersiz öğelerin listesini döndürür.</span><span class="sxs-lookup"><span data-stu-id="bb5b2-106">You can use the `Distinct` clause to return a list of unique items.</span></span> <span data-ttu-id="bb5b2-107">`Distinct` Yan tümcesi yinelenen sorgu sonuçlarını yok saymak sorgu neden olur.</span><span class="sxs-lookup"><span data-stu-id="bb5b2-107">The `Distinct` clause causes the query to ignore duplicate query results.</span></span> <span data-ttu-id="bb5b2-108">`Distinct` Yan tümcesi tüm alanlar tarafından belirtilen döndürmek için yinelenen değerlere uygulanan `Select` yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="bb5b2-108">The `Distinct` clause applies to duplicate values for all return fields specified by the `Select` clause.</span></span> <span data-ttu-id="bb5b2-109">Hayır ise `Select` yan tümcesi belirtildiğinde, `Distinct` yan tümcesinin aralık değişkeni içinde belirtilen sorgu için uygulanan `From` yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="bb5b2-109">If no `Select` clause is specified, the `Distinct` clause is applied to the range variable for the query identified in the `From` clause.</span></span> <span data-ttu-id="bb5b2-110">Aralık değişkeni bir sabit türü değilse, türün tüm üyeleri varolan bir sorgu sonucu eşleşiyorsa sorgu yalnızca bir sorgu sonucunu yoksayar.</span><span class="sxs-lookup"><span data-stu-id="bb5b2-110">If the range variable is not an immutable type, the query will only ignore a query result if all members of the type match an existing query result.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bb5b2-111">Örnek</span><span class="sxs-lookup"><span data-stu-id="bb5b2-111">Example</span></span>  
 <span data-ttu-id="bb5b2-112">Aşağıdaki sorgu ifadesi, müşterilerin listesini ve müşteri siparişlerinin listesi birleştirir.</span><span class="sxs-lookup"><span data-stu-id="bb5b2-112">The following query expression joins a list of customers and a list of customer orders.</span></span> <span data-ttu-id="bb5b2-113">`Distinct` Benzersiz Müşteri adlarının bir listesini döndürür ve sipariş tarihlerini yan tümcesi dahildir.</span><span class="sxs-lookup"><span data-stu-id="bb5b2-113">The `Distinct` clause is included to return a list of unique customer names and order dates.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#20](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/distinct-clause_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="bb5b2-114">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="bb5b2-114">See Also</span></span>  
 [<span data-ttu-id="bb5b2-115">Visual Basic'de LINQ'e giriş</span><span class="sxs-lookup"><span data-stu-id="bb5b2-115">Introduction to LINQ in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
 [<span data-ttu-id="bb5b2-116">Sorgular</span><span class="sxs-lookup"><span data-stu-id="bb5b2-116">Queries</span></span>](../../../visual-basic/language-reference/queries/index.md)  
 [<span data-ttu-id="bb5b2-117">From Yan Tümcesi</span><span class="sxs-lookup"><span data-stu-id="bb5b2-117">From Clause</span></span>](../../../visual-basic/language-reference/queries/from-clause.md)  
 [<span data-ttu-id="bb5b2-118">Select Yan Tümcesi</span><span class="sxs-lookup"><span data-stu-id="bb5b2-118">Select Clause</span></span>](../../../visual-basic/language-reference/queries/select-clause.md)  
 [<span data-ttu-id="bb5b2-119">Where Yan Tümcesi</span><span class="sxs-lookup"><span data-stu-id="bb5b2-119">Where Clause</span></span>](../../../visual-basic/language-reference/queries/where-clause.md)
