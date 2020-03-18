---
title: İç içe bir grup oluşturma (C#'da LINQ)
description: C#'daki LINQ sorgu ifadesinde iç içe bir grup oluşturmayı öğrenin.
ms.date: 12/01/2016
ms.assetid: e9f00708-362e-4d13-98c5-d77549347ba0
ms.openlocfilehash: 7d056c9e215ccc7ca24d621b64e2328bed79f22e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "61688624"
---
# <a name="create-a-nested-group"></a><span data-ttu-id="8d7b1-103">İç içe geçmiş grup oluşturma</span><span class="sxs-lookup"><span data-stu-id="8d7b1-103">Create a nested group</span></span>

<span data-ttu-id="8d7b1-104">Aşağıdaki örnekte, BIR LINQ sorgu ifadesinde iç içe gruplar nasıl oluşturulacak gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="8d7b1-104">The following example shows how to create nested groups in a LINQ query expression.</span></span> <span data-ttu-id="8d7b1-105">Öğrenci yılı veya not düzeyine göre oluşturulan her grup daha sonra bireylerin adlarına göre gruplara ayrılır.</span><span class="sxs-lookup"><span data-stu-id="8d7b1-105">Each group that is created according to student year or grade level is then further subdivided into groups based on the individuals' names.</span></span>

## <a name="example"></a><span data-ttu-id="8d7b1-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="8d7b1-106">Example</span></span>

> [!NOTE]
> <span data-ttu-id="8d7b1-107">Bu örnek, sorgulayan [nesneler koleksiyonunda](query-a-collection-of-objects.md)örnek kodda tanımlanan nesnelere başvurular içerir.</span><span class="sxs-lookup"><span data-stu-id="8d7b1-107">This example contains references to objects that are defined in the sample code in [Query a collection of objects](query-a-collection-of-objects.md).</span></span>

[!code-csharp[csProgGuideLINQ#24](~/samples/snippets/csharp/concepts/linq/how-to-create-a-nested-group_1.cs)]

<span data-ttu-id="8d7b1-108">İç içe bir `foreach` grubun iç öğeleri üzerinde üç iç içe döngünün yeniden kaydedilmesi gerektiğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="8d7b1-108">Note that three nested `foreach` loops are required to iterate over the inner elements of a nested group.</span></span>

## <a name="see-also"></a><span data-ttu-id="8d7b1-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8d7b1-109">See also</span></span>

- [<span data-ttu-id="8d7b1-110">Dil ile Tümleşik Sorgu (LINQ)</span><span class="sxs-lookup"><span data-stu-id="8d7b1-110">Language Integrated Query (LINQ)</span></span>](index.md)
