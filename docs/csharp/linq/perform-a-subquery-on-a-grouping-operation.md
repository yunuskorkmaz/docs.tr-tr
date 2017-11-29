---
title: "Gruplandırma işleminde alt sorgu gerçekleştirme"
description: "Gruplandırma işleminde alt sorgu gerçekleştirme yapma."
keywords: .NET, .NET core, C#
author: BillWagner
manager: wpickett
ms.author: wiwagn
ms.date: 12/1/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.assetid: d75a588e-9b6f-4f37-b195-f99ec8503855
ms.openlocfilehash: f638b8a679a15891d04e02f1597d6bf7934a9e74
ms.sourcegitcommit: 7e99f66ef09d2903e22c789c67ff5a10aa953b2f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/18/2017
---
# <a name="perform-a-subquery-on-a-grouping-operation"></a><span data-ttu-id="d7033-104">Gruplandırma işleminde alt sorgu gerçekleştirme</span><span class="sxs-lookup"><span data-stu-id="d7033-104">Perform a subquery on a grouping operation</span></span>

<span data-ttu-id="d7033-105">Bu konuda, gruplar halinde veri kaynağını sıralar ve ardından bir alt sorgu her grubu ayrı ayrı gerçekleştiren bir sorgu oluşturmak için iki farklı yolu gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="d7033-105">This topic shows two different ways to create a query that orders the source data into groups, and then performs a subquery over each group individually.</span></span> <span data-ttu-id="d7033-106">Temel her örnekte kullanarak kaynağı öğeleri gruplandırmak için tekniktir bir *devamlılık* adlı `newGroup`, yeni bir alt sorgu karşı oluşturmasını `newGroup`.</span><span class="sxs-lookup"><span data-stu-id="d7033-106">The basic technique in each example is to group the source elements by using a *continuation* named `newGroup`, and then generating a new subquery against `newGroup`.</span></span> <span data-ttu-id="d7033-107">Bu alt sorgu dış sorgu tarafından oluşturulan her yeni Grup karşı çalıştırılır.</span><span class="sxs-lookup"><span data-stu-id="d7033-107">This subquery is run against each new group that is created by the outer query.</span></span> <span data-ttu-id="d7033-108">Bu örnekte son çıkışı değildir bir grup, ancak anonim türler düz bir dizi olduğuna dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="d7033-108">Note that in this particular example the final output is not a group, but a flat sequence of anonymous types.</span></span>  
  
 <span data-ttu-id="d7033-109">Gruba hakkında daha fazla bilgi için bkz: [group yan tümcesi](../language-reference/keywords/group-clause.md).</span><span class="sxs-lookup"><span data-stu-id="d7033-109">For more information about how to group, see [group clause](../language-reference/keywords/group-clause.md).</span></span>  
  
 <span data-ttu-id="d7033-110">Devamlılıklar hakkında daha fazla bilgi için bkz: [içine](../language-reference/keywords/into.md).</span><span class="sxs-lookup"><span data-stu-id="d7033-110">For more information about continuations, see [into](../language-reference/keywords/into.md).</span></span> <span data-ttu-id="d7033-111">Aşağıdaki örnek, veri kaynağı olarak bir bellek içi veri yapısı kullanır, ancak aynı ilkeler LINQ veri kaynağı herhangi bir tür için uygulanır.</span><span class="sxs-lookup"><span data-stu-id="d7033-111">The following example uses an in-memory data structure as the data source, but the same principles apply for any kind of LINQ data source.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d7033-112">Örnek</span><span class="sxs-lookup"><span data-stu-id="d7033-112">Example</span></span> 

 > [!NOTE]
 > <span data-ttu-id="d7033-113">Bu örnek, örnek kodda tanımlanan nesnelere başvurular içerir [nesneler koleksiyonunu sorgulama](query-a-collection-of-objects.md).</span><span class="sxs-lookup"><span data-stu-id="d7033-113">This example contains references to objects that are defined in the sample code in [Query a collection of objects](query-a-collection-of-objects.md).</span></span>

 [!code-csharp[csProgGuideLINQ#23](../../../samples/snippets/csharp/concepts/linq/how-to-perform-a-subquery-on-a-grouping-operation_1.cs)]  
   
## <a name="see-also"></a><span data-ttu-id="d7033-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d7033-114">See also</span></span>  
 [<span data-ttu-id="d7033-115">LINQ Sorgu ifadeleri</span><span class="sxs-lookup"><span data-stu-id="d7033-115">LINQ Query Expressions</span></span>](index.md)
