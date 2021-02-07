---
description: 'Daha fazla bilgi edinin: DISTINCT tümcesi (Visual Basic)'
title: Distinct Yan Tümcesi
ms.date: 07/20/2015
f1_keywords:
- vb.QueryDistinct
helpviewer_keywords:
- Distinct clause [Visual Basic]
- Distinct statement [Visual Basic]
- queries [Visual Basic], Distinct
ms.assetid: 86f42614-0d8f-4ffc-b888-ce8a37a8d36a
ms.openlocfilehash: df1cdc58f7af406533e67a396a958a26b0c79635
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99700656"
---
# <a name="distinct-clause-visual-basic"></a><span data-ttu-id="1261e-103">Distinct Tümcesi (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1261e-103">Distinct Clause (Visual Basic)</span></span>

<span data-ttu-id="1261e-104">Sonraki sorgu yan tümcelerinde yinelenen değerleri ortadan kaldırmak için geçerli aralık değişkeninin değerlerini kısıtlar.</span><span class="sxs-lookup"><span data-stu-id="1261e-104">Restricts the values of the current range variable to eliminate duplicate values in subsequent query clauses.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1261e-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="1261e-105">Syntax</span></span>  
  
```vb  
Distinct  
```  
  
## <a name="remarks"></a><span data-ttu-id="1261e-106">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="1261e-106">Remarks</span></span>  

 <span data-ttu-id="1261e-107">`Distinct`Yan tümcesini kullanarak benzersiz öğelerin bir listesini döndürebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1261e-107">You can use the `Distinct` clause to return a list of unique items.</span></span> <span data-ttu-id="1261e-108">`Distinct`Yan tümce sorgunun yinelenen sorgu sonuçlarını yoksaymasına neden olur.</span><span class="sxs-lookup"><span data-stu-id="1261e-108">The `Distinct` clause causes the query to ignore duplicate query results.</span></span> <span data-ttu-id="1261e-109">`Distinct`Yan tümcesi, yan tümcesi tarafından belirtilen tüm dönüş alanları için yinelenen değerler için geçerlidir `Select` .</span><span class="sxs-lookup"><span data-stu-id="1261e-109">The `Distinct` clause applies to duplicate values for all return fields specified by the `Select` clause.</span></span> <span data-ttu-id="1261e-110">Hiçbir `Select` yan tümce belirtilmemişse yan tümce, `Distinct` yan tümcesinde tanımlanan sorgu için Aralık değişkenine uygulanır `From` .</span><span class="sxs-lookup"><span data-stu-id="1261e-110">If no `Select` clause is specified, the `Distinct` clause is applied to the range variable for the query identified in the `From` clause.</span></span> <span data-ttu-id="1261e-111">Aralık değişkeni sabit bir tür değilse, sorgu Yalnızca türün tüm üyeleri var olan bir sorgu sonucuyla eşleşiyorsa sorgu sonucunu yoksayar.</span><span class="sxs-lookup"><span data-stu-id="1261e-111">If the range variable is not an immutable type, the query will only ignore a query result if all members of the type match an existing query result.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1261e-112">Örnek</span><span class="sxs-lookup"><span data-stu-id="1261e-112">Example</span></span>  

 <span data-ttu-id="1261e-113">Aşağıdaki sorgu ifadesi bir müşteri listesini ve müşteri siparişlerinin bir listesini birleştirir.</span><span class="sxs-lookup"><span data-stu-id="1261e-113">The following query expression joins a list of customers and a list of customer orders.</span></span> <span data-ttu-id="1261e-114">`Distinct`Yan tümcesi, benzersiz müşteri adları ve sipariş tarihlerinin listesini döndürmek için dahil edilmiştir.</span><span class="sxs-lookup"><span data-stu-id="1261e-114">The `Distinct` clause is included to return a list of unique customer names and order dates.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#20](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#20)]  
  
## <a name="see-also"></a><span data-ttu-id="1261e-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1261e-115">See also</span></span>

- [<span data-ttu-id="1261e-116">Visual Basic'de LINQ'e Giriş</span><span class="sxs-lookup"><span data-stu-id="1261e-116">Introduction to LINQ in Visual Basic</span></span>](../../programming-guide/language-features/linq/introduction-to-linq.md)
- [<span data-ttu-id="1261e-117">Sorgular</span><span class="sxs-lookup"><span data-stu-id="1261e-117">Queries</span></span>](index.md)
- [<span data-ttu-id="1261e-118">From yan tümcesi</span><span class="sxs-lookup"><span data-stu-id="1261e-118">From Clause</span></span>](from-clause.md)
- [<span data-ttu-id="1261e-119">Select yan tümcesi</span><span class="sxs-lookup"><span data-stu-id="1261e-119">Select Clause</span></span>](select-clause.md)
- [<span data-ttu-id="1261e-120">WHERE yan tümcesi</span><span class="sxs-lookup"><span data-stu-id="1261e-120">Where Clause</span></span>](where-clause.md)
