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
ms.openlocfilehash: 4b0ce12f6361d3dc6e5cc3601e96fc3a9bcf3841
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33603983"
---
# <a name="distinct-clause-visual-basic"></a><span data-ttu-id="04806-102">Distinct Tümcesi (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="04806-102">Distinct Clause (Visual Basic)</span></span>
<span data-ttu-id="04806-103">Yinelenen değerler sonraki sorgu yan tümcelerinde ortadan kaldırmak için geçerli aralık değişkeni değerlerini kısıtlar.</span><span class="sxs-lookup"><span data-stu-id="04806-103">Restricts the values of the current range variable to eliminate duplicate values in subsequent query clauses.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="04806-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="04806-104">Syntax</span></span>  
  
```  
Distinct  
```  
  
## <a name="remarks"></a><span data-ttu-id="04806-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="04806-105">Remarks</span></span>  
 <span data-ttu-id="04806-106">Kullanabileceğiniz `Distinct` benzersiz öğeleri listesini döndürmek için yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="04806-106">You can use the `Distinct` clause to return a list of unique items.</span></span> <span data-ttu-id="04806-107">`Distinct` Yan tümcesi yinelenen sorgu sonuçları yoksaymak sorgu neden olur.</span><span class="sxs-lookup"><span data-stu-id="04806-107">The `Distinct` clause causes the query to ignore duplicate query results.</span></span> <span data-ttu-id="04806-108">`Distinct` Yan tümcesi tüm tarafından belirtilen alanları dönmek için yinelenen değerler geçerlidir `Select` yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="04806-108">The `Distinct` clause applies to duplicate values for all return fields specified by the `Select` clause.</span></span> <span data-ttu-id="04806-109">Öyle değilse `Select` yan tümcesi belirtilirse, `Distinct` yan tümcesinin aralık değişkeni tanımlanan sorgu için uygulanan `From` yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="04806-109">If no `Select` clause is specified, the `Distinct` clause is applied to the range variable for the query identified in the `From` clause.</span></span> <span data-ttu-id="04806-110">Aralık değişkeni bir sabit türü değilse türdeki tüm üyelerin varolan bir sorgu sonuç eşleşiyorsa sorgu yalnızca bir sorgu sonucu göz ardı eder.</span><span class="sxs-lookup"><span data-stu-id="04806-110">If the range variable is not an immutable type, the query will only ignore a query result if all members of the type match an existing query result.</span></span>  
  
## <a name="example"></a><span data-ttu-id="04806-111">Örnek</span><span class="sxs-lookup"><span data-stu-id="04806-111">Example</span></span>  
 <span data-ttu-id="04806-112">Aşağıdaki sorgu ifadesi müşterilerin listesini ve müşteri siparişleri listesini birleştirir.</span><span class="sxs-lookup"><span data-stu-id="04806-112">The following query expression joins a list of customers and a list of customer orders.</span></span> <span data-ttu-id="04806-113">`Distinct` Benzersiz Müşteri adlarının bir listesini döndürür ve tarihleri sipariş yan tümcesi eklenmiştir.</span><span class="sxs-lookup"><span data-stu-id="04806-113">The `Distinct` clause is included to return a list of unique customer names and order dates.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#20](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/distinct-clause_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="04806-114">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="04806-114">See Also</span></span>  
 [<span data-ttu-id="04806-115">Visual Basic'de LINQ'e giriş</span><span class="sxs-lookup"><span data-stu-id="04806-115">Introduction to LINQ in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
 [<span data-ttu-id="04806-116">Sorgular</span><span class="sxs-lookup"><span data-stu-id="04806-116">Queries</span></span>](../../../visual-basic/language-reference/queries/queries.md)  
 [<span data-ttu-id="04806-117">From Yan Tümcesi</span><span class="sxs-lookup"><span data-stu-id="04806-117">From Clause</span></span>](../../../visual-basic/language-reference/queries/from-clause.md)  
 [<span data-ttu-id="04806-118">Select Yan Tümcesi</span><span class="sxs-lookup"><span data-stu-id="04806-118">Select Clause</span></span>](../../../visual-basic/language-reference/queries/select-clause.md)  
 [<span data-ttu-id="04806-119">Where Yan Tümcesi</span><span class="sxs-lookup"><span data-stu-id="04806-119">Where Clause</span></span>](../../../visual-basic/language-reference/queries/where-clause.md)
