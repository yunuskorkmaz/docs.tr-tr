---
title: Yöntemden sorgu döndürme
description: Sorgu döndürme yapma.
ms.date: 11/30/2016
ms.assetid: db220f79-c35b-41f2-886c-cd068672d42d
ms.openlocfilehash: 1c5fa534f3f39f8201d93b986e687d85bb303736
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43510793"
---
# <a name="how-to-return-a-query-from-a-method-c-programming-guide"></a><span data-ttu-id="d75c4-103">Nasıl yapılır: Yöntemden Sorgu Döndürme (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="d75c4-103">How to: Return a Query from a Method (C# Programming Guide)</span></span>
<span data-ttu-id="d75c4-104">Bu örnek ve dönüş değeri olarak bir yöntemden sorgu döndürme işlemini gösterir. bir `out` parametresi.</span><span class="sxs-lookup"><span data-stu-id="d75c4-104">This example shows how to return a query from a method as the return value and as an `out` parameter.</span></span>  
  
 <span data-ttu-id="d75c4-105">Sorgu nesneleri yöntemden sorgu döndürme, yani birleştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="d75c4-105">Query objects are composable, meaning that you can return a query from a method.</span></span> <span data-ttu-id="d75c4-106">Sorguları temsil eden nesneleri, sonuçta elde edilen koleksiyon, ancak gerektiğinde, istediğiniz sonuçları vermeyebilir adımları yerine depolamayın.</span><span class="sxs-lookup"><span data-stu-id="d75c4-106">Objects that represent queries do not store the resulting collection, but rather the steps to produce the results when needed.</span></span> <span data-ttu-id="d75c4-107">Sorgu nesneleri döndürme yöntemleri avantajı, bunların daha da oluşan değiştirilebilir veya emin olmanızdır.</span><span class="sxs-lookup"><span data-stu-id="d75c4-107">The advantage of returning query objects from methods is that they can be further composed or modified.</span></span> <span data-ttu-id="d75c4-108">Bu nedenle herhangi bir değer döndürür veya `out` bir sorgu döndüren bir yöntem parametresi türü de olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="d75c4-108">Therefore any return value or `out` parameter of a method that returns a query must also have that type.</span></span> <span data-ttu-id="d75c4-109">Bir yöntem içinde bir somut bir sorgu gerçekleştiren varsa <xref:System.Collections.Generic.List%601> veya <xref:System.Array> türü, bu olarak kabul sorgu sonuçları yerine sorguyu döndürüyor.</span><span class="sxs-lookup"><span data-stu-id="d75c4-109">If a method materializes a query into a concrete <xref:System.Collections.Generic.List%601> or <xref:System.Array> type, it is considered to be returning the query results instead of the query itself.</span></span> <span data-ttu-id="d75c4-110">Yöntemi tarafından döndürülen bir sorgu değişkeni yine de oluşur veya değiştirilemez.</span><span class="sxs-lookup"><span data-stu-id="d75c4-110">A query variable that is returned from a method can still be composed or modified.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d75c4-111">Örnek</span><span class="sxs-lookup"><span data-stu-id="d75c4-111">Example</span></span>  
 <span data-ttu-id="d75c4-112">Aşağıdaki örnekte, ilk yöntem dönüş değeri olarak bir sorgu döndürür ve ikinci yöntem döndüren bir sorgu olarak bir `out` parametresi.</span><span class="sxs-lookup"><span data-stu-id="d75c4-112">In the following example, the first method returns a query as a return value, and the second method returns a query as an `out` parameter.</span></span> <span data-ttu-id="d75c4-113">Her iki durumda da, sorgu sonuçları, döndürülen bir sorgu olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="d75c4-113">Note that in both cases it is a query that is  returned, not query results.</span></span>  
  
 [!code-csharp[csProgGuideLINQ#80](~/samples/snippets/csharp/concepts/linq/how-to-return-a-query-from-a-method_1.cs)]  

## <a name="see-also"></a><span data-ttu-id="d75c4-114">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="d75c4-114">See Also</span></span>

- [<span data-ttu-id="d75c4-115">Dil ile Tümleşik Sorgu (LINQ)</span><span class="sxs-lookup"><span data-stu-id="d75c4-115">Language Integrated Query (LINQ)</span></span>](index.md)
