---
title: Gruplandırma işleminde alt sorgu gerçekleştirme
description: Gruplandırma işleminde alt sorgu gerçekleştirme yapma.
ms.date: 12/1/2016
ms.assetid: d75a588e-9b6f-4f37-b195-f99ec8503855
ms.openlocfilehash: 209d05c2fe8719fa9116061d199272366146f465
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33277335"
---
# <a name="perform-a-subquery-on-a-grouping-operation"></a><span data-ttu-id="86efe-103">Gruplandırma işleminde alt sorgu gerçekleştirme</span><span class="sxs-lookup"><span data-stu-id="86efe-103">Perform a subquery on a grouping operation</span></span>

<span data-ttu-id="86efe-104">Bu konuda, gruplar halinde veri kaynağını sıralar ve ardından bir alt sorgu her grubu ayrı ayrı gerçekleştiren bir sorgu oluşturmak için iki farklı yolu gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="86efe-104">This topic shows two different ways to create a query that orders the source data into groups, and then performs a subquery over each group individually.</span></span> <span data-ttu-id="86efe-105">Temel her örnekte kullanarak kaynağı öğeleri gruplandırmak için tekniktir bir *devamlılık* adlı `newGroup`, yeni bir alt sorgu karşı oluşturmasını `newGroup`.</span><span class="sxs-lookup"><span data-stu-id="86efe-105">The basic technique in each example is to group the source elements by using a *continuation* named `newGroup`, and then generating a new subquery against `newGroup`.</span></span> <span data-ttu-id="86efe-106">Bu alt sorgu dış sorgu tarafından oluşturulan her yeni Grup karşı çalıştırılır.</span><span class="sxs-lookup"><span data-stu-id="86efe-106">This subquery is run against each new group that is created by the outer query.</span></span> <span data-ttu-id="86efe-107">Bu örnekte son çıkışı değildir bir grup, ancak anonim türler düz bir dizi olduğuna dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="86efe-107">Note that in this particular example the final output is not a group, but a flat sequence of anonymous types.</span></span>  
  
 <span data-ttu-id="86efe-108">Gruba hakkında daha fazla bilgi için bkz: [group yan tümcesi](../language-reference/keywords/group-clause.md).</span><span class="sxs-lookup"><span data-stu-id="86efe-108">For more information about how to group, see [group clause](../language-reference/keywords/group-clause.md).</span></span>  
  
 <span data-ttu-id="86efe-109">Devamlılıklar hakkında daha fazla bilgi için bkz: [içine](../language-reference/keywords/into.md).</span><span class="sxs-lookup"><span data-stu-id="86efe-109">For more information about continuations, see [into](../language-reference/keywords/into.md).</span></span> <span data-ttu-id="86efe-110">Aşağıdaki örnek, veri kaynağı olarak bir bellek içi veri yapısı kullanır, ancak aynı ilkeler LINQ veri kaynağı herhangi bir tür için uygulanır.</span><span class="sxs-lookup"><span data-stu-id="86efe-110">The following example uses an in-memory data structure as the data source, but the same principles apply for any kind of LINQ data source.</span></span>  
  
## <a name="example"></a><span data-ttu-id="86efe-111">Örnek</span><span class="sxs-lookup"><span data-stu-id="86efe-111">Example</span></span> 

 > [!NOTE]
 > <span data-ttu-id="86efe-112">Bu örnek, örnek kodda tanımlanan nesnelere başvurular içerir [nesneler koleksiyonunu sorgulama](query-a-collection-of-objects.md).</span><span class="sxs-lookup"><span data-stu-id="86efe-112">This example contains references to objects that are defined in the sample code in [Query a collection of objects](query-a-collection-of-objects.md).</span></span>

 [!code-csharp[csProgGuideLINQ#23](../../../samples/snippets/csharp/concepts/linq/how-to-perform-a-subquery-on-a-grouping-operation_1.cs)]  
   
## <a name="see-also"></a><span data-ttu-id="86efe-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="86efe-113">See also</span></span>  
 [<span data-ttu-id="86efe-114">LINQ Sorgu ifadeleri</span><span class="sxs-lookup"><span data-stu-id="86efe-114">LINQ Query Expressions</span></span>](index.md)
