---
title: "Bir sorgu döndürme"
description: Bir sorgu iade etme.
keywords: .NET, .NET core, C#
author: BillWagner
manager: wpickett
ms.author: wiwagn
ms.date: 11/30/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.assetid: db220f79-c35b-41f2-886c-cd068672d42d
ms.openlocfilehash: c1b69e3f5f0cd2c50ae80d2454e6b7f13dc30344
ms.sourcegitcommit: 7e99f66ef09d2903e22c789c67ff5a10aa953b2f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/18/2017
---
# <a name="how-to-return-a-query-from-a-method-c-programming-guide"></a><span data-ttu-id="a261d-104">Nasıl yapılır: Yöntemden Sorgu Döndürme (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="a261d-104">How to: Return a Query from a Method (C# Programming Guide)</span></span>
<span data-ttu-id="a261d-105">Bu örnek bir sorgu ve dönüş değeri olarak döndürme gösterilmektedir bir `out` parametresi.</span><span class="sxs-lookup"><span data-stu-id="a261d-105">This example shows how to return a query from a method as the return value and as an `out` parameter.</span></span>  
  
 <span data-ttu-id="a261d-106">Sorgu nesneleri birleştirilebilir bir yöntemden sorgu döndürebilir anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="a261d-106">Query objects are composable, meaning that you can return a query from a method.</span></span> <span data-ttu-id="a261d-107">Sorguları temsil eden nesneler, sonuçta elde edilen koleksiyonu, ancak gerektiğinde sonuçlar yerine adımlarını depolamayın.</span><span class="sxs-lookup"><span data-stu-id="a261d-107">Objects that represent queries do not store the resulting collection, but rather the steps to produce the results when needed.</span></span> <span data-ttu-id="a261d-108">Yöntemleri sorgu nesneleri döndürme avantajı, bunların daha oluşan değiştirilebilir veya olduğunu olmasıdır.</span><span class="sxs-lookup"><span data-stu-id="a261d-108">The advantage of returning query objects from methods is that they can be further composed or modified.</span></span> <span data-ttu-id="a261d-109">Bu nedenle herhangi bir değeri döndürme veya `out` bir sorgu döndüren bir yöntem parametresinin türü de olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="a261d-109">Therefore any return value or `out` parameter of a method that returns a query must also have that type.</span></span> <span data-ttu-id="a261d-110">Bir yöntem somut bir sorgu gerçeğe varsa <xref:System.Collections.Generic.List%601> veya <xref:System.Array> türü, onu olarak kabul sorgu yerine sorgu sonuçları döndürüyor.</span><span class="sxs-lookup"><span data-stu-id="a261d-110">If a method materializes a query into a concrete <xref:System.Collections.Generic.List%601> or <xref:System.Array> type, it is considered to be returning the query results instead of the query itself.</span></span> <span data-ttu-id="a261d-111">Bir yöntemin döndürdüğü bir sorgu değişkeni hala oluşur veya değiştirilemez.</span><span class="sxs-lookup"><span data-stu-id="a261d-111">A query variable that is returned from a method can still be composed or modified.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a261d-112">Örnek</span><span class="sxs-lookup"><span data-stu-id="a261d-112">Example</span></span>  
 <span data-ttu-id="a261d-113">Aşağıdaki örnekte, ilk yöntem sorgu dönüş değeri olarak döndürür ve bir sorgu olarak ikinci yöntem bir `out` parametresi.</span><span class="sxs-lookup"><span data-stu-id="a261d-113">In the following example, the first method returns a query as a return value, and the second method returns a query as an `out` parameter.</span></span> <span data-ttu-id="a261d-114">Her iki durumda da, sorgu sonuçları döndüren bir sorgu olduğuna dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="a261d-114">Note that in both cases it is a query that is  returned, not query results.</span></span>  
  
 [!code-csharp[csProgGuideLINQ#80](../../../samples/snippets/csharp/concepts/linq/how-to-return-a-query-from-a-method_1.cs)]  

## <a name="see-also"></a><span data-ttu-id="a261d-115">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="a261d-115">See Also</span></span>  
 [<span data-ttu-id="a261d-116">LINQ Sorgu ifadeleri</span><span class="sxs-lookup"><span data-stu-id="a261d-116">LINQ Query Expressions</span></span>](index.md)
