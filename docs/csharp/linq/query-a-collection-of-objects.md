---
title: Nesneler koleksiyonunu sorgulama
description: Koleksiyonları nasıl sorgu.
ms.date: 11/30/2016
ms.assetid: 87a76f8a-0b58-4791-90ea-2fe0a30416c9
ms.openlocfilehash: c690da2ae59d2a9b34a5bd403bc54797c4e95fa0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33282398"
---
# <a name="query-a-collection-of-objects"></a><span data-ttu-id="2e550-103">Nesneler koleksiyonunu sorgulama</span><span class="sxs-lookup"><span data-stu-id="2e550-103">Query a collection of objects</span></span>
<span data-ttu-id="2e550-104">Bu örnek listesini basit bir sorgu gerçekleştirme gösterir `Student` nesneleri.</span><span class="sxs-lookup"><span data-stu-id="2e550-104">This example shows how to perform a simple query over a list of `Student` objects.</span></span> <span data-ttu-id="2e550-105">Her `Student` nesnesi Öğrenci ve dört incelemelerde öğrencinin başarı gösteren liste hakkında bazı temel bilgileri içerir.</span><span class="sxs-lookup"><span data-stu-id="2e550-105">Each `Student` object contains some basic information about the student, and a list that represents the student's scores on four examinations.</span></span>  
  
 <span data-ttu-id="2e550-106">Aynı kullanan çok sayıda diğer örnekler için bu bölümdeki framework olarak bu uygulamaya hizmet `students` veri kaynağı.</span><span class="sxs-lookup"><span data-stu-id="2e550-106">This application serves as the framework for many other examples in this section that use the same `students` data source.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2e550-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="2e550-107">Example</span></span>  
 <span data-ttu-id="2e550-108">Aşağıdaki sorgu 90 veya kendi ilk incelemesi üzerinde daha büyük bir puan alınan Öğrenciler döndürür.</span><span class="sxs-lookup"><span data-stu-id="2e550-108">The following query returns the students who received a score of 90 or greater on their first exam.</span></span>  
  
 [!code-csharp[csProgGuideLINQ#15](../../../samples/snippets/csharp/concepts/linq/how-to-query-a-collection-of-objects_1.cs)]  
  
 <span data-ttu-id="2e550-109">Bu sorgu, deneme etkinleştirmek kasıtlı olarak basit bir işlemdir.</span><span class="sxs-lookup"><span data-stu-id="2e550-109">This query is intentionally simple to enable you to experiment.</span></span> <span data-ttu-id="2e550-110">Örneğin, daha fazla koşullarında deneyebilirsiniz `where` yan tümcesi ya da kullanım bir `orderby` sonuçları sıralamak için yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="2e550-110">For example, you can try more conditions in the `where` clause, or use an `orderby` clause to sort the results.</span></span>  
  

## <a name="see-also"></a><span data-ttu-id="2e550-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2e550-111">See also</span></span>  
 [<span data-ttu-id="2e550-112">LINQ Sorgu ifadeleri</span><span class="sxs-lookup"><span data-stu-id="2e550-112">LINQ Query Expressions</span></span>](index.md)  
 [<span data-ttu-id="2e550-113">Dize ilişkilendirme</span><span class="sxs-lookup"><span data-stu-id="2e550-113">String interpolation</span></span>](../language-reference/tokens/interpolated.md)
