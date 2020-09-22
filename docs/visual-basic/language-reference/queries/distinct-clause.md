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
ms.openlocfilehash: 49eaab2e6a8c48d61518ea51ef2f644b6eb48314
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90875285"
---
# <a name="distinct-clause-visual-basic"></a><span data-ttu-id="b629a-102">Distinct Tümcesi (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b629a-102">Distinct Clause (Visual Basic)</span></span>

<span data-ttu-id="b629a-103">Sonraki sorgu yan tümcelerinde yinelenen değerleri ortadan kaldırmak için geçerli aralık değişkeninin değerlerini kısıtlar.</span><span class="sxs-lookup"><span data-stu-id="b629a-103">Restricts the values of the current range variable to eliminate duplicate values in subsequent query clauses.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b629a-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b629a-104">Syntax</span></span>  
  
```vb  
Distinct  
```  
  
## <a name="remarks"></a><span data-ttu-id="b629a-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b629a-105">Remarks</span></span>  

 <span data-ttu-id="b629a-106">`Distinct`Yan tümcesini kullanarak benzersiz öğelerin bir listesini döndürebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b629a-106">You can use the `Distinct` clause to return a list of unique items.</span></span> <span data-ttu-id="b629a-107">`Distinct`Yan tümce sorgunun yinelenen sorgu sonuçlarını yoksaymasına neden olur.</span><span class="sxs-lookup"><span data-stu-id="b629a-107">The `Distinct` clause causes the query to ignore duplicate query results.</span></span> <span data-ttu-id="b629a-108">`Distinct`Yan tümcesi, yan tümcesi tarafından belirtilen tüm dönüş alanları için yinelenen değerler için geçerlidir `Select` .</span><span class="sxs-lookup"><span data-stu-id="b629a-108">The `Distinct` clause applies to duplicate values for all return fields specified by the `Select` clause.</span></span> <span data-ttu-id="b629a-109">Hiçbir `Select` yan tümce belirtilmemişse yan tümce, `Distinct` yan tümcesinde tanımlanan sorgu için Aralık değişkenine uygulanır `From` .</span><span class="sxs-lookup"><span data-stu-id="b629a-109">If no `Select` clause is specified, the `Distinct` clause is applied to the range variable for the query identified in the `From` clause.</span></span> <span data-ttu-id="b629a-110">Aralık değişkeni sabit bir tür değilse, sorgu Yalnızca türün tüm üyeleri var olan bir sorgu sonucuyla eşleşiyorsa sorgu sonucunu yoksayar.</span><span class="sxs-lookup"><span data-stu-id="b629a-110">If the range variable is not an immutable type, the query will only ignore a query result if all members of the type match an existing query result.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b629a-111">Örnek</span><span class="sxs-lookup"><span data-stu-id="b629a-111">Example</span></span>  

 <span data-ttu-id="b629a-112">Aşağıdaki sorgu ifadesi bir müşteri listesini ve müşteri siparişlerinin bir listesini birleştirir.</span><span class="sxs-lookup"><span data-stu-id="b629a-112">The following query expression joins a list of customers and a list of customer orders.</span></span> <span data-ttu-id="b629a-113">`Distinct`Yan tümcesi, benzersiz müşteri adları ve sipariş tarihlerinin listesini döndürmek için dahil edilmiştir.</span><span class="sxs-lookup"><span data-stu-id="b629a-113">The `Distinct` clause is included to return a list of unique customer names and order dates.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#20](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#20)]  
  
## <a name="see-also"></a><span data-ttu-id="b629a-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b629a-114">See also</span></span>

- [<span data-ttu-id="b629a-115">Visual Basic'de LINQ'e Giriş</span><span class="sxs-lookup"><span data-stu-id="b629a-115">Introduction to LINQ in Visual Basic</span></span>](../../programming-guide/language-features/linq/introduction-to-linq.md)
- [<span data-ttu-id="b629a-116">Sorgular</span><span class="sxs-lookup"><span data-stu-id="b629a-116">Queries</span></span>](index.md)
- [<span data-ttu-id="b629a-117">From yan tümcesi</span><span class="sxs-lookup"><span data-stu-id="b629a-117">From Clause</span></span>](from-clause.md)
- [<span data-ttu-id="b629a-118">Select yan tümcesi</span><span class="sxs-lookup"><span data-stu-id="b629a-118">Select Clause</span></span>](select-clause.md)
- [<span data-ttu-id="b629a-119">WHERE yan tümcesi</span><span class="sxs-lookup"><span data-stu-id="b629a-119">Where Clause</span></span>](where-clause.md)
