---
title: Distinct Yan Tümcesi
ms.date: 07/20/2015
f1_keywords:
- vb.QueryDistinct
helpviewer_keywords:
- Distinct clause [Visual Basic]
- Distinct statement [Visual Basic]
- queries [Visual Basic], Distinct
ms.assetid: 86f42614-0d8f-4ffc-b888-ce8a37a8d36a
ms.openlocfilehash: 5aecffbce036500d294d03a925798d51f1269af6
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84401400"
---
# <a name="distinct-clause-visual-basic"></a><span data-ttu-id="d3fd1-102">Distinct Tümcesi (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d3fd1-102">Distinct Clause (Visual Basic)</span></span>
<span data-ttu-id="d3fd1-103">Sonraki sorgu yan tümcelerinde yinelenen değerleri ortadan kaldırmak için geçerli aralık değişkeninin değerlerini kısıtlar.</span><span class="sxs-lookup"><span data-stu-id="d3fd1-103">Restricts the values of the current range variable to eliminate duplicate values in subsequent query clauses.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d3fd1-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d3fd1-104">Syntax</span></span>  
  
```vb  
Distinct  
```  
  
## <a name="remarks"></a><span data-ttu-id="d3fd1-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d3fd1-105">Remarks</span></span>  
 <span data-ttu-id="d3fd1-106">`Distinct`Yan tümcesini kullanarak benzersiz öğelerin bir listesini döndürebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d3fd1-106">You can use the `Distinct` clause to return a list of unique items.</span></span> <span data-ttu-id="d3fd1-107">`Distinct`Yan tümce sorgunun yinelenen sorgu sonuçlarını yoksaymasına neden olur.</span><span class="sxs-lookup"><span data-stu-id="d3fd1-107">The `Distinct` clause causes the query to ignore duplicate query results.</span></span> <span data-ttu-id="d3fd1-108">`Distinct`Yan tümcesi, yan tümcesi tarafından belirtilen tüm dönüş alanları için yinelenen değerler için geçerlidir `Select` .</span><span class="sxs-lookup"><span data-stu-id="d3fd1-108">The `Distinct` clause applies to duplicate values for all return fields specified by the `Select` clause.</span></span> <span data-ttu-id="d3fd1-109">Hiçbir `Select` yan tümce belirtilmemişse yan tümce, `Distinct` yan tümcesinde tanımlanan sorgu için Aralık değişkenine uygulanır `From` .</span><span class="sxs-lookup"><span data-stu-id="d3fd1-109">If no `Select` clause is specified, the `Distinct` clause is applied to the range variable for the query identified in the `From` clause.</span></span> <span data-ttu-id="d3fd1-110">Aralık değişkeni sabit bir tür değilse, sorgu Yalnızca türün tüm üyeleri var olan bir sorgu sonucuyla eşleşiyorsa sorgu sonucunu yoksayar.</span><span class="sxs-lookup"><span data-stu-id="d3fd1-110">If the range variable is not an immutable type, the query will only ignore a query result if all members of the type match an existing query result.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d3fd1-111">Örnek</span><span class="sxs-lookup"><span data-stu-id="d3fd1-111">Example</span></span>  
 <span data-ttu-id="d3fd1-112">Aşağıdaki sorgu ifadesi bir müşteri listesini ve müşteri siparişlerinin bir listesini birleştirir.</span><span class="sxs-lookup"><span data-stu-id="d3fd1-112">The following query expression joins a list of customers and a list of customer orders.</span></span> <span data-ttu-id="d3fd1-113">`Distinct`Yan tümcesi, benzersiz müşteri adları ve sipariş tarihlerinin listesini döndürmek için dahil edilmiştir.</span><span class="sxs-lookup"><span data-stu-id="d3fd1-113">The `Distinct` clause is included to return a list of unique customer names and order dates.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#20](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#20)]  
  
## <a name="see-also"></a><span data-ttu-id="d3fd1-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d3fd1-114">See also</span></span>

- [<span data-ttu-id="d3fd1-115">Visual Basic'de LINQ'e Giriş</span><span class="sxs-lookup"><span data-stu-id="d3fd1-115">Introduction to LINQ in Visual Basic</span></span>](../../programming-guide/language-features/linq/introduction-to-linq.md)
- [<span data-ttu-id="d3fd1-116">Sorgular</span><span class="sxs-lookup"><span data-stu-id="d3fd1-116">Queries</span></span>](index.md)
- [<span data-ttu-id="d3fd1-117">From yan tümcesi</span><span class="sxs-lookup"><span data-stu-id="d3fd1-117">From Clause</span></span>](from-clause.md)
- [<span data-ttu-id="d3fd1-118">Select yan tümcesi</span><span class="sxs-lookup"><span data-stu-id="d3fd1-118">Select Clause</span></span>](select-clause.md)
- [<span data-ttu-id="d3fd1-119">WHERE yan tümcesi</span><span class="sxs-lookup"><span data-stu-id="d3fd1-119">Where Clause</span></span>](where-clause.md)
