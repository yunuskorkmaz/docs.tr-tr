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
ms.openlocfilehash: e8d3e38261a04c4d29faab351d24d6710413b09a
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/07/2019
ms.locfileid: "72004794"
---
# <a name="distinct-clause-visual-basic"></a><span data-ttu-id="f15b8-102">Distinct Tümcesi (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f15b8-102">Distinct Clause (Visual Basic)</span></span>
<span data-ttu-id="f15b8-103">Sonraki sorgu yan tümcelerinde yinelenen değerleri ortadan kaldırmak için geçerli aralık değişkeninin değerlerini kısıtlar.</span><span class="sxs-lookup"><span data-stu-id="f15b8-103">Restricts the values of the current range variable to eliminate duplicate values in subsequent query clauses.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f15b8-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f15b8-104">Syntax</span></span>  
  
```vb  
Distinct  
```  
  
## <a name="remarks"></a><span data-ttu-id="f15b8-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f15b8-105">Remarks</span></span>  
 <span data-ttu-id="f15b8-106">Benzersiz öğelerin bir listesini döndürmek için `Distinct` yan tümcesini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f15b8-106">You can use the `Distinct` clause to return a list of unique items.</span></span> <span data-ttu-id="f15b8-107">@No__t-0 yan tümcesi sorgunun yinelenen sorgu sonuçlarını yoksaymasına neden olur.</span><span class="sxs-lookup"><span data-stu-id="f15b8-107">The `Distinct` clause causes the query to ignore duplicate query results.</span></span> <span data-ttu-id="f15b8-108">@No__t-0 yan tümcesi, `Select` yan tümcesi tarafından belirtilen tüm dönüş alanları için yinelenen değerler için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="f15b8-108">The `Distinct` clause applies to duplicate values for all return fields specified by the `Select` clause.</span></span> <span data-ttu-id="f15b8-109">@No__t-0 yan tümcesi belirtilmemişse, `Distinct` yan tümcesi `From` yan tümcesinde tanımlanan sorgu için Aralık değişkenine uygulanır.</span><span class="sxs-lookup"><span data-stu-id="f15b8-109">If no `Select` clause is specified, the `Distinct` clause is applied to the range variable for the query identified in the `From` clause.</span></span> <span data-ttu-id="f15b8-110">Aralık değişkeni sabit bir tür değilse, sorgu Yalnızca türün tüm üyeleri var olan bir sorgu sonucuyla eşleşiyorsa sorgu sonucunu yoksayar.</span><span class="sxs-lookup"><span data-stu-id="f15b8-110">If the range variable is not an immutable type, the query will only ignore a query result if all members of the type match an existing query result.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f15b8-111">Örnek</span><span class="sxs-lookup"><span data-stu-id="f15b8-111">Example</span></span>  
 <span data-ttu-id="f15b8-112">Aşağıdaki sorgu ifadesi bir müşteri listesini ve müşteri siparişlerinin bir listesini birleştirir.</span><span class="sxs-lookup"><span data-stu-id="f15b8-112">The following query expression joins a list of customers and a list of customer orders.</span></span> <span data-ttu-id="f15b8-113">@No__t-0 yan tümcesi, benzersiz müşteri adları ve sipariş tarihlerinin listesini döndürmek için dahil edilmiştir.</span><span class="sxs-lookup"><span data-stu-id="f15b8-113">The `Distinct` clause is included to return a list of unique customer names and order dates.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#20](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#20)]  
  
## <a name="see-also"></a><span data-ttu-id="f15b8-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f15b8-114">See also</span></span>

- [<span data-ttu-id="f15b8-115">Visual Basic LINQ 'e giriş</span><span class="sxs-lookup"><span data-stu-id="f15b8-115">Introduction to LINQ in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [<span data-ttu-id="f15b8-116">Sorgular</span><span class="sxs-lookup"><span data-stu-id="f15b8-116">Queries</span></span>](../../../visual-basic/language-reference/queries/index.md)
- [<span data-ttu-id="f15b8-117">From Yan Tümcesi</span><span class="sxs-lookup"><span data-stu-id="f15b8-117">From Clause</span></span>](../../../visual-basic/language-reference/queries/from-clause.md)
- [<span data-ttu-id="f15b8-118">Select Yan Tümcesi</span><span class="sxs-lookup"><span data-stu-id="f15b8-118">Select Clause</span></span>](../../../visual-basic/language-reference/queries/select-clause.md)
- [<span data-ttu-id="f15b8-119">Where Yan Tümcesi</span><span class="sxs-lookup"><span data-stu-id="f15b8-119">Where Clause</span></span>](../../../visual-basic/language-reference/queries/where-clause.md)
