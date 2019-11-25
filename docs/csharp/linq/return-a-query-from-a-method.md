---
title: Yöntemden sorgu döndürme
description: Sorgu döndürme.
ms.date: 11/30/2016
ms.assetid: db220f79-c35b-41f2-886c-cd068672d42d
ms.openlocfilehash: 1df533770f76301432b104d6f8398f1687750cce
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/12/2019
ms.locfileid: "73972520"
---
# <a name="how-to-return-a-query-from-a-method-c-programming-guide"></a><span data-ttu-id="c23ab-103">Yöntemden bir sorgu döndürme (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="c23ab-103">How to return a query from a method (C# Programming Guide)</span></span>
<span data-ttu-id="c23ab-104">Bu örnek, bir yöntemden dönüş değeri olarak ve `out` parametresi olarak bir sorgunun nasıl döndürülyapılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="c23ab-104">This example shows how to return a query from a method as the return value and as an `out` parameter.</span></span>  
  
 <span data-ttu-id="c23ab-105">Sorgu nesneleri birleştirilebilir, bu da bir yöntemden sorgu döndürebilmeniz anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="c23ab-105">Query objects are composable, meaning that you can return a query from a method.</span></span> <span data-ttu-id="c23ab-106">Sorguları temsil eden nesneler, sonuçta elde edilen koleksiyonu depolamaz, ancak gerektiğinde sonuçları oluşturmak için gerekli adımları uygulayın.</span><span class="sxs-lookup"><span data-stu-id="c23ab-106">Objects that represent queries do not store the resulting collection, but rather the steps to produce the results when needed.</span></span> <span data-ttu-id="c23ab-107">Yöntemlerin sorgu nesnelerini döndürmesinin avantajı, daha fazla oluşturulabilir veya değiştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="c23ab-107">The advantage of returning query objects from methods is that they can be further composed or modified.</span></span> <span data-ttu-id="c23ab-108">Bu nedenle, bir sorgu döndüren bir yöntemin dönüş değeri veya `out` parametresi de aynı türde olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="c23ab-108">Therefore any return value or `out` parameter of a method that returns a query must also have that type.</span></span> <span data-ttu-id="c23ab-109">Bir yöntem bir sorguyu somut bir <xref:System.Collections.Generic.List%601> veya <xref:System.Array> türüne alıyorsa, sorgunun kendisi yerine sorgu sonuçlarının döndürülmesi kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="c23ab-109">If a method materializes a query into a concrete <xref:System.Collections.Generic.List%601> or <xref:System.Array> type, it is considered to be returning the query results instead of the query itself.</span></span> <span data-ttu-id="c23ab-110">Bir yöntemden döndürülen bir sorgu değişkeni hala oluşturulabilir veya değiştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="c23ab-110">A query variable that is returned from a method can still be composed or modified.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c23ab-111">Örnek</span><span class="sxs-lookup"><span data-stu-id="c23ab-111">Example</span></span>  
 <span data-ttu-id="c23ab-112">Aşağıdaki örnekte, ilk yöntem bir sorgu dönüş değeri olarak döndürür ve ikinci yöntem `out` parametresi olarak bir sorgu döndürür.</span><span class="sxs-lookup"><span data-stu-id="c23ab-112">In the following example, the first method returns a query as a return value, and the second method returns a query as an `out` parameter.</span></span> <span data-ttu-id="c23ab-113">Her iki durumda da, sorgu sonuçlarının değil, döndürülen bir sorgu olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="c23ab-113">Note that in both cases it is a query that is  returned, not query results.</span></span>  
  
 [!code-csharp[csProgGuideLINQ#80](~/samples/snippets/csharp/concepts/linq/how-to-return-a-query-from-a-method_1.cs)]  

## <a name="see-also"></a><span data-ttu-id="c23ab-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c23ab-114">See also</span></span>

- [<span data-ttu-id="c23ab-115">Dil ile Tümleşik Sorgu (LINQ)</span><span class="sxs-lookup"><span data-stu-id="c23ab-115">Language Integrated Query (LINQ)</span></span>](index.md)
