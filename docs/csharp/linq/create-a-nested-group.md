---
title: "İç içe geçmiş grup oluşturma"
description: "İç içe geçmiş grup oluşturma"
keywords: .NET, .NET core, C#
author: BillWagner
manager: wpickett
ms.author: wiwagn
ms.date: 12/1/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.assetid: e9f00708-362e-4d13-98c5-d77549347ba0
ms.openlocfilehash: 232aa46d975d7c338bbc776e3867f2e566601fde
ms.sourcegitcommit: 7e99f66ef09d2903e22c789c67ff5a10aa953b2f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/18/2017
---
# <a name="create-a-nested-group"></a><span data-ttu-id="b39d4-104">İç içe geçmiş grup oluşturma</span><span class="sxs-lookup"><span data-stu-id="b39d4-104">Create a nested group</span></span>

<span data-ttu-id="b39d4-105">Aşağıdaki örnekte bir LINQ sorgu ifadesinde iç içe grupları oluşturmayı gösterir.</span><span class="sxs-lookup"><span data-stu-id="b39d4-105">The following example shows how to create nested groups in a LINQ query expression.</span></span> <span data-ttu-id="b39d4-106">Öğrenci yıl veya notu düzeyine göre oluşturulan her bir grup sonra başka kişiler adlarına göre gruplara bölünmüştür.</span><span class="sxs-lookup"><span data-stu-id="b39d4-106">Each group that is created according to student year or grade level is then further subdivided into groups based on the individuals' names.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b39d4-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="b39d4-107">Example</span></span>

 > [!NOTE]
 > <span data-ttu-id="b39d4-108">Bu örnek, örnek kodda tanımlanan nesnelere başvurular içerir [nesneler koleksiyonunu sorgulama](query-a-collection-of-objects.md).</span><span class="sxs-lookup"><span data-stu-id="b39d4-108">This example contains references to objects that are defined in the sample code in [Query a collection of objects](query-a-collection-of-objects.md).</span></span> 

 [!code-csharp[csProgGuideLINQ#24](../../../samples/snippets/csharp/concepts/linq/how-to-create-a-nested-group_1.cs)]  
  
 <span data-ttu-id="b39d4-109">Üç iç içe geçmiş Not `foreach` döngüler, iç içe geçmiş Grup iç öğeleri yineleme için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="b39d4-109">Note that three nested `foreach` loops are required to iterate over the inner elements of a nested group.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b39d4-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b39d4-110">See also</span></span>  
 [<span data-ttu-id="b39d4-111">LINQ Sorgu ifadeleri</span><span class="sxs-lookup"><span data-stu-id="b39d4-111">LINQ Query Expressions</span></span>](index.md)
