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
ms.openlocfilehash: 3761f6d6ba97e7f1a824b70b18a50dae820c7e51
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54710046"
---
# <a name="distinct-clause-visual-basic"></a><span data-ttu-id="3a8eb-102">Distinct Tümcesi (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3a8eb-102">Distinct Clause (Visual Basic)</span></span>
<span data-ttu-id="3a8eb-103">Sonraki sorgu yan tümceleri içinde yinelenen değerleri ortadan kaldırmak için geçerli aralık değişkeni değerlerini sınırlandırır.</span><span class="sxs-lookup"><span data-stu-id="3a8eb-103">Restricts the values of the current range variable to eliminate duplicate values in subsequent query clauses.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3a8eb-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="3a8eb-104">Syntax</span></span>  
  
```  
Distinct  
```  
  
## <a name="remarks"></a><span data-ttu-id="3a8eb-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="3a8eb-105">Remarks</span></span>  
 <span data-ttu-id="3a8eb-106">Kullanabileceğiniz `Distinct` yan benzersiz öğelerin listesini döndürür.</span><span class="sxs-lookup"><span data-stu-id="3a8eb-106">You can use the `Distinct` clause to return a list of unique items.</span></span> <span data-ttu-id="3a8eb-107">`Distinct` Yan tümcesi yinelenen sorgu sonuçlarını yok saymak sorgu neden olur.</span><span class="sxs-lookup"><span data-stu-id="3a8eb-107">The `Distinct` clause causes the query to ignore duplicate query results.</span></span> <span data-ttu-id="3a8eb-108">`Distinct` Yan tümcesi tüm alanlar tarafından belirtilen döndürmek için yinelenen değerlere uygulanan `Select` yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="3a8eb-108">The `Distinct` clause applies to duplicate values for all return fields specified by the `Select` clause.</span></span> <span data-ttu-id="3a8eb-109">Hayır ise `Select` yan tümcesi belirtildiğinde, `Distinct` yan tümcesinin aralık değişkeni içinde belirtilen sorgu için uygulanan `From` yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="3a8eb-109">If no `Select` clause is specified, the `Distinct` clause is applied to the range variable for the query identified in the `From` clause.</span></span> <span data-ttu-id="3a8eb-110">Aralık değişkeni bir sabit türü değilse, türün tüm üyeleri varolan bir sorgu sonucu eşleşiyorsa sorgu yalnızca bir sorgu sonucunu yoksayar.</span><span class="sxs-lookup"><span data-stu-id="3a8eb-110">If the range variable is not an immutable type, the query will only ignore a query result if all members of the type match an existing query result.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3a8eb-111">Örnek</span><span class="sxs-lookup"><span data-stu-id="3a8eb-111">Example</span></span>  
 <span data-ttu-id="3a8eb-112">Aşağıdaki sorgu ifadesi, müşterilerin listesini ve müşteri siparişlerinin listesi birleştirir.</span><span class="sxs-lookup"><span data-stu-id="3a8eb-112">The following query expression joins a list of customers and a list of customer orders.</span></span> <span data-ttu-id="3a8eb-113">`Distinct` Benzersiz Müşteri adlarının bir listesini döndürür ve sipariş tarihlerini yan tümcesi dahildir.</span><span class="sxs-lookup"><span data-stu-id="3a8eb-113">The `Distinct` clause is included to return a list of unique customer names and order dates.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#20](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/distinct-clause_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="3a8eb-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3a8eb-114">See also</span></span>
- [<span data-ttu-id="3a8eb-115">Visual Basic'de LINQ'e giriş</span><span class="sxs-lookup"><span data-stu-id="3a8eb-115">Introduction to LINQ in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [<span data-ttu-id="3a8eb-116">Sorgular</span><span class="sxs-lookup"><span data-stu-id="3a8eb-116">Queries</span></span>](../../../visual-basic/language-reference/queries/index.md)
- [<span data-ttu-id="3a8eb-117">From Yan Tümcesi</span><span class="sxs-lookup"><span data-stu-id="3a8eb-117">From Clause</span></span>](../../../visual-basic/language-reference/queries/from-clause.md)
- [<span data-ttu-id="3a8eb-118">Select Yan Tümcesi</span><span class="sxs-lookup"><span data-stu-id="3a8eb-118">Select Clause</span></span>](../../../visual-basic/language-reference/queries/select-clause.md)
- [<span data-ttu-id="3a8eb-119">Where Yan Tümcesi</span><span class="sxs-lookup"><span data-stu-id="3a8eb-119">Where Clause</span></span>](../../../visual-basic/language-reference/queries/where-clause.md)
