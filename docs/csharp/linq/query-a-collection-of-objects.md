---
title: (C# üzerinde LINQ) nesneler koleksiyonunu sorgulama
description: Bilgi koleksiyonları LINQ C# kullanarak nasıl sorgulama.
ms.date: 11/30/2016
ms.assetid: 87a76f8a-0b58-4791-90ea-2fe0a30416c9
ms.openlocfilehash: 9b2f5dd09c540800e9a2498d48883357f58c0116
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54734509"
---
# <a name="query-a-collection-of-objects"></a><span data-ttu-id="51ac3-103">Nesneler koleksiyonunu sorgulama</span><span class="sxs-lookup"><span data-stu-id="51ac3-103">Query a collection of objects</span></span>

<span data-ttu-id="51ac3-104">Bu örnek bir listesi basit bir sorgu gerçekleştirmek nasıl gösterir `Student` nesneleri.</span><span class="sxs-lookup"><span data-stu-id="51ac3-104">This example shows how to perform a simple query over a list of `Student` objects.</span></span> <span data-ttu-id="51ac3-105">Her `Student` nesnesi Öğrenci ve öğrencinin puanları üzerindeki dört incelemelerde temsil eden bir liste hakkında bazı temel bilgileri içerir.</span><span class="sxs-lookup"><span data-stu-id="51ac3-105">Each `Student` object contains some basic information about the student, and a list that represents the student's scores on four examinations.</span></span>  
  
<span data-ttu-id="51ac3-106">Bu uygulama, aynı kullanan çok sayıda diğer örnekler için bu bölümdeki framework görür `students` veri kaynağı.</span><span class="sxs-lookup"><span data-stu-id="51ac3-106">This application serves as the framework for many other examples in this section that use the same `students` data source.</span></span>  
  
## <a name="example"></a><span data-ttu-id="51ac3-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="51ac3-107">Example</span></span>

<span data-ttu-id="51ac3-108">Aşağıdaki sorgu bir puana 90 ya da kendi ilk sınavı büyük öğrencilere döndürür.</span><span class="sxs-lookup"><span data-stu-id="51ac3-108">The following query returns the students who received a score of 90 or greater on their first exam.</span></span>  
  
[!code-csharp[csProgGuideLINQ#15](~/samples/snippets/csharp/concepts/linq/how-to-query-a-collection-of-objects_1.cs)]  
  
<span data-ttu-id="51ac3-109">Bu sorgu, denemenizi etkinleştirmek kasıtlı olarak basit bir işlemdir.</span><span class="sxs-lookup"><span data-stu-id="51ac3-109">This query is intentionally simple to enable you to experiment.</span></span> <span data-ttu-id="51ac3-110">Örneğin, daha fazla koşullarında deneyebilirsiniz `where` yan tümcesi veya kullanımı bir `orderby` sonuçları sıralamak için yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="51ac3-110">For example, you can try more conditions in the `where` clause, or use an `orderby` clause to sort the results.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="51ac3-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="51ac3-111">See also</span></span>

- [<span data-ttu-id="51ac3-112">Dil ile Tümleşik Sorgu (LINQ)</span><span class="sxs-lookup"><span data-stu-id="51ac3-112">Language Integrated Query (LINQ)</span></span>](index.md)
- [<span data-ttu-id="51ac3-113">Dize ilişkilendirme</span><span class="sxs-lookup"><span data-stu-id="51ac3-113">String interpolation</span></span>](../language-reference/tokens/interpolated.md)
