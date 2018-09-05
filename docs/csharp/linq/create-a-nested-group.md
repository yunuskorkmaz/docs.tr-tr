---
title: (C# üzerinde LINQ) bir iç içe geçmiş grup oluşturma
description: C# LINQ sorgu ifadesinde iç içe geçmiş grup oluşturmayı öğrenin.
ms.date: 12/1/2016
ms.assetid: e9f00708-362e-4d13-98c5-d77549347ba0
ms.openlocfilehash: 82b07c303215200fa974ce614a2d5a77882dcf4c
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43509974"
---
# <a name="create-a-nested-group"></a><span data-ttu-id="376d0-103">İç içe geçmiş grup oluşturma</span><span class="sxs-lookup"><span data-stu-id="376d0-103">Create a nested group</span></span>

<span data-ttu-id="376d0-104">Aşağıdaki örnek, bir LINQ sorgu ifadesinde iç içe geçmiş gruplar oluşturma işlemi gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="376d0-104">The following example shows how to create nested groups in a LINQ query expression.</span></span> <span data-ttu-id="376d0-105">Öğrenci yıl veya sınıf düzeyine göre oluşturulan her grup ardından bireylerin adlarına göre gruplara ek bölünmüştür.</span><span class="sxs-lookup"><span data-stu-id="376d0-105">Each group that is created according to student year or grade level is then further subdivided into groups based on the individuals' names.</span></span>

## <a name="example"></a><span data-ttu-id="376d0-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="376d0-106">Example</span></span>

> [!NOTE]
> <span data-ttu-id="376d0-107">Bu örnekte örnek koda tanımlanan nesneleri başvuruları içeren [nesneler koleksiyonunu sorgulama](query-a-collection-of-objects.md).</span><span class="sxs-lookup"><span data-stu-id="376d0-107">This example contains references to objects that are defined in the sample code in [Query a collection of objects](query-a-collection-of-objects.md).</span></span>

[!code-csharp[csProgGuideLINQ#24](~/samples/snippets/csharp/concepts/linq/how-to-create-a-nested-group_1.cs)]

<span data-ttu-id="376d0-108">Üç iç içe geçmiş Not `foreach` iç içe geçmiş Grup iç öğeleri üzerinde yinelemek için döngüleri gereklidir.</span><span class="sxs-lookup"><span data-stu-id="376d0-108">Note that three nested `foreach` loops are required to iterate over the inner elements of a nested group.</span></span>

## <a name="see-also"></a><span data-ttu-id="376d0-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="376d0-109">See also</span></span>

- [<span data-ttu-id="376d0-110">Dil ile Tümleşik Sorgu (LINQ)</span><span class="sxs-lookup"><span data-stu-id="376d0-110">Language Integrated Query (LINQ)</span></span>](index.md)
