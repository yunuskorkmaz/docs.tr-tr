---
title: Bir sorgu döndürme
description: Bir sorgu iade etme.
ms.date: 11/30/2016
ms.assetid: db220f79-c35b-41f2-886c-cd068672d42d
ms.openlocfilehash: 6a1d581c46c7b0b2062859fd60701dd25ea54eea
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33274956"
---
# <a name="how-to-return-a-query-from-a-method-c-programming-guide"></a><span data-ttu-id="0ac40-103">Nasıl yapılır: Yöntemden Sorgu Döndürme (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="0ac40-103">How to: Return a Query from a Method (C# Programming Guide)</span></span>
<span data-ttu-id="0ac40-104">Bu örnek bir sorgu ve dönüş değeri olarak döndürme gösterilmektedir bir `out` parametresi.</span><span class="sxs-lookup"><span data-stu-id="0ac40-104">This example shows how to return a query from a method as the return value and as an `out` parameter.</span></span>  
  
 <span data-ttu-id="0ac40-105">Sorgu nesneleri birleştirilebilir bir yöntemden sorgu döndürebilir anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="0ac40-105">Query objects are composable, meaning that you can return a query from a method.</span></span> <span data-ttu-id="0ac40-106">Sorguları temsil eden nesneler, sonuçta elde edilen koleksiyonu, ancak gerektiğinde sonuçlar yerine adımlarını depolamayın.</span><span class="sxs-lookup"><span data-stu-id="0ac40-106">Objects that represent queries do not store the resulting collection, but rather the steps to produce the results when needed.</span></span> <span data-ttu-id="0ac40-107">Yöntemleri sorgu nesneleri döndürme avantajı, bunların daha oluşan değiştirilebilir veya olduğunu olmasıdır.</span><span class="sxs-lookup"><span data-stu-id="0ac40-107">The advantage of returning query objects from methods is that they can be further composed or modified.</span></span> <span data-ttu-id="0ac40-108">Bu nedenle herhangi bir değeri döndürme veya `out` bir sorgu döndüren bir yöntem parametresinin türü de olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="0ac40-108">Therefore any return value or `out` parameter of a method that returns a query must also have that type.</span></span> <span data-ttu-id="0ac40-109">Bir yöntem somut bir sorgu gerçeğe varsa <xref:System.Collections.Generic.List%601> veya <xref:System.Array> türü, onu olarak kabul sorgu yerine sorgu sonuçları döndürüyor.</span><span class="sxs-lookup"><span data-stu-id="0ac40-109">If a method materializes a query into a concrete <xref:System.Collections.Generic.List%601> or <xref:System.Array> type, it is considered to be returning the query results instead of the query itself.</span></span> <span data-ttu-id="0ac40-110">Bir yöntemin döndürdüğü bir sorgu değişkeni hala oluşur veya değiştirilemez.</span><span class="sxs-lookup"><span data-stu-id="0ac40-110">A query variable that is returned from a method can still be composed or modified.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0ac40-111">Örnek</span><span class="sxs-lookup"><span data-stu-id="0ac40-111">Example</span></span>  
 <span data-ttu-id="0ac40-112">Aşağıdaki örnekte, ilk yöntem sorgu dönüş değeri olarak döndürür ve bir sorgu olarak ikinci yöntem bir `out` parametresi.</span><span class="sxs-lookup"><span data-stu-id="0ac40-112">In the following example, the first method returns a query as a return value, and the second method returns a query as an `out` parameter.</span></span> <span data-ttu-id="0ac40-113">Her iki durumda da, sorgu sonuçları döndüren bir sorgu olduğuna dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="0ac40-113">Note that in both cases it is a query that is  returned, not query results.</span></span>  
  
 [!code-csharp[csProgGuideLINQ#80](../../../samples/snippets/csharp/concepts/linq/how-to-return-a-query-from-a-method_1.cs)]  

## <a name="see-also"></a><span data-ttu-id="0ac40-114">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="0ac40-114">See Also</span></span>  
 [<span data-ttu-id="0ac40-115">LINQ Sorgu ifadeleri</span><span class="sxs-lookup"><span data-stu-id="0ac40-115">LINQ Query Expressions</span></span>](index.md)
