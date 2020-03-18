---
title: Yöntemden sorgu döndürme
description: Sorgu nasıl döndürülecek.
ms.date: 11/30/2016
ms.assetid: db220f79-c35b-41f2-886c-cd068672d42d
ms.openlocfilehash: 1df533770f76301432b104d6f8398f1687750cce
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "73972520"
---
# <a name="how-to-return-a-query-from-a-method-c-programming-guide"></a><span data-ttu-id="0b0ab-103">Bir yöntemden sorgu nasıl döndürülür (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="0b0ab-103">How to return a query from a method (C# Programming Guide)</span></span>
<span data-ttu-id="0b0ab-104">Bu örnek, bir yöntemden bir sorgunun iade değeri `out` olarak ve parametre olarak nasıl döndürüleceklerini gösterir.</span><span class="sxs-lookup"><span data-stu-id="0b0ab-104">This example shows how to return a query from a method as the return value and as an `out` parameter.</span></span>  
  
 <span data-ttu-id="0b0ab-105">Sorgu nesneleri birleştirilebilir, yani bir yöntemden sorgu döndürebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0b0ab-105">Query objects are composable, meaning that you can return a query from a method.</span></span> <span data-ttu-id="0b0ab-106">Sorguları temsil eden nesneler, ortaya çıkan koleksiyonu değil, gerektiğinde sonuçları üreten adımları depolar.</span><span class="sxs-lookup"><span data-stu-id="0b0ab-106">Objects that represent queries do not store the resulting collection, but rather the steps to produce the results when needed.</span></span> <span data-ttu-id="0b0ab-107">Sorgu nesnelerini yöntemlerden döndürmenin avantajı, bunların daha fazla oluşturulabiliyor veya değiştirilebiliyor olmasıdır.</span><span class="sxs-lookup"><span data-stu-id="0b0ab-107">The advantage of returning query objects from methods is that they can be further composed or modified.</span></span> <span data-ttu-id="0b0ab-108">Bu nedenle, `out` sorgu döndüren bir yöntemin herhangi bir dönüş değeri veya parametresi de bu türolmalıdır.</span><span class="sxs-lookup"><span data-stu-id="0b0ab-108">Therefore any return value or `out` parameter of a method that returns a query must also have that type.</span></span> <span data-ttu-id="0b0ab-109">Bir yöntem bir sorguyu somut <xref:System.Collections.Generic.List%601> veya <xref:System.Array> türe somutlaştırırsa, sorgunun kendisi yerine sorgu sonuçlarını döndürülür olarak kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="0b0ab-109">If a method materializes a query into a concrete <xref:System.Collections.Generic.List%601> or <xref:System.Array> type, it is considered to be returning the query results instead of the query itself.</span></span> <span data-ttu-id="0b0ab-110">Yöntemden döndürülen bir sorgu değişkeni yine de oluşturulabilir veya değiştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="0b0ab-110">A query variable that is returned from a method can still be composed or modified.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0b0ab-111">Örnek</span><span class="sxs-lookup"><span data-stu-id="0b0ab-111">Example</span></span>  
 <span data-ttu-id="0b0ab-112">Aşağıdaki örnekte, ilk yöntem bir sorguyu iade değeri olarak döndürür `out` ve ikinci yöntem bir sorguyu parametre olarak döndürür.</span><span class="sxs-lookup"><span data-stu-id="0b0ab-112">In the following example, the first method returns a query as a return value, and the second method returns a query as an `out` parameter.</span></span> <span data-ttu-id="0b0ab-113">Her iki durumda da sorgu sonuçları değil, döndürülen bir sorgu olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="0b0ab-113">Note that in both cases it is a query that is  returned, not query results.</span></span>  
  
 [!code-csharp[csProgGuideLINQ#80](~/samples/snippets/csharp/concepts/linq/how-to-return-a-query-from-a-method_1.cs)]  

## <a name="see-also"></a><span data-ttu-id="0b0ab-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0b0ab-114">See also</span></span>

- [<span data-ttu-id="0b0ab-115">Dil ile Tümleşik Sorgu (LINQ)</span><span class="sxs-lookup"><span data-stu-id="0b0ab-115">Language Integrated Query (LINQ)</span></span>](index.md)
