---
title: Nesneler koleksiyonunu sorgula (C#'da LINQ)
description: C#'da LINQ kullanarak sorgu koleksiyonlarının nasıl olduğunu öğrenin.
ms.date: 11/30/2016
ms.assetid: 87a76f8a-0b58-4791-90ea-2fe0a30416c9
ms.openlocfilehash: 9b2f5dd09c540800e9a2498d48883357f58c0116
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "61659819"
---
# <a name="query-a-collection-of-objects"></a><span data-ttu-id="5d747-103">Nesneler koleksiyonunu sorgulama</span><span class="sxs-lookup"><span data-stu-id="5d747-103">Query a collection of objects</span></span>

<span data-ttu-id="5d747-104">Bu örnek, `Student` nesneler listesi üzerinde basit bir sorgunun nasıl gerçekleştirildirilebildiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="5d747-104">This example shows how to perform a simple query over a list of `Student` objects.</span></span> <span data-ttu-id="5d747-105">Her `Student` nesne, öğrenci hakkında bazı temel bilgiler ve dört sınavda öğrencinin puanlarını temsil eden bir liste içerir.</span><span class="sxs-lookup"><span data-stu-id="5d747-105">Each `Student` object contains some basic information about the student, and a list that represents the student's scores on four examinations.</span></span>  
  
<span data-ttu-id="5d747-106">Bu uygulama, aynı `students` veri kaynağını kullanan bu bölümdeki diğer birçok örnek için bir çerçeve görevi görehizmet eder.</span><span class="sxs-lookup"><span data-stu-id="5d747-106">This application serves as the framework for many other examples in this section that use the same `students` data source.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5d747-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="5d747-107">Example</span></span>

<span data-ttu-id="5d747-108">Aşağıdaki sorgu, ilk sınavda 90 veya daha fazla puan alan öğrencileri döndürür.</span><span class="sxs-lookup"><span data-stu-id="5d747-108">The following query returns the students who received a score of 90 or greater on their first exam.</span></span>  
  
[!code-csharp[csProgGuideLINQ#15](~/samples/snippets/csharp/concepts/linq/how-to-query-a-collection-of-objects_1.cs)]  
  
<span data-ttu-id="5d747-109">Bu sorgu deneme etkinleştirmek için kasıtlı olarak basittir.</span><span class="sxs-lookup"><span data-stu-id="5d747-109">This query is intentionally simple to enable you to experiment.</span></span> <span data-ttu-id="5d747-110">Örneğin, `where` yan tümcede daha fazla koşul `orderby` deneyebilir veya sonuçları sıralamak için bir yan tümce kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5d747-110">For example, you can try more conditions in the `where` clause, or use an `orderby` clause to sort the results.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5d747-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5d747-111">See also</span></span>

- [<span data-ttu-id="5d747-112">Dil ile Tümleşik Sorgu (LINQ)</span><span class="sxs-lookup"><span data-stu-id="5d747-112">Language Integrated Query (LINQ)</span></span>](index.md)
- [<span data-ttu-id="5d747-113">Dize ilişkilendirme</span><span class="sxs-lookup"><span data-stu-id="5d747-113">String interpolation</span></span>](../language-reference/tokens/interpolated.md)
