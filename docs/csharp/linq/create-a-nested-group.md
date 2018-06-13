---
title: İç içe geçmiş grup oluşturma
description: İç içe geçmiş grup oluşturma
ms.date: 12/1/2016
ms.assetid: e9f00708-362e-4d13-98c5-d77549347ba0
ms.openlocfilehash: dd1158bfa1456342fe8967aed5e02ecebae591c1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33273149"
---
# <a name="create-a-nested-group"></a><span data-ttu-id="6d3b0-103">İç içe geçmiş grup oluşturma</span><span class="sxs-lookup"><span data-stu-id="6d3b0-103">Create a nested group</span></span>

<span data-ttu-id="6d3b0-104">Aşağıdaki örnekte bir LINQ sorgu ifadesinde iç içe grupları oluşturmayı gösterir.</span><span class="sxs-lookup"><span data-stu-id="6d3b0-104">The following example shows how to create nested groups in a LINQ query expression.</span></span> <span data-ttu-id="6d3b0-105">Öğrenci yıl veya notu düzeyine göre oluşturulan her bir grup sonra başka kişiler adlarına göre gruplara bölünmüştür.</span><span class="sxs-lookup"><span data-stu-id="6d3b0-105">Each group that is created according to student year or grade level is then further subdivided into groups based on the individuals' names.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6d3b0-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="6d3b0-106">Example</span></span>

 > [!NOTE]
 > <span data-ttu-id="6d3b0-107">Bu örnek, örnek kodda tanımlanan nesnelere başvurular içerir [nesneler koleksiyonunu sorgulama](query-a-collection-of-objects.md).</span><span class="sxs-lookup"><span data-stu-id="6d3b0-107">This example contains references to objects that are defined in the sample code in [Query a collection of objects](query-a-collection-of-objects.md).</span></span> 

 [!code-csharp[csProgGuideLINQ#24](../../../samples/snippets/csharp/concepts/linq/how-to-create-a-nested-group_1.cs)]  
  
 <span data-ttu-id="6d3b0-108">Üç iç içe geçmiş Not `foreach` döngüler, iç içe geçmiş Grup iç öğeleri yineleme için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="6d3b0-108">Note that three nested `foreach` loops are required to iterate over the inner elements of a nested group.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6d3b0-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6d3b0-109">See also</span></span>  
 [<span data-ttu-id="6d3b0-110">LINQ Sorgu ifadeleri</span><span class="sxs-lookup"><span data-stu-id="6d3b0-110">LINQ Query Expressions</span></span>](index.md)
