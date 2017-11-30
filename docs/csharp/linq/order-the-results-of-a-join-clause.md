---
title: "Join tümcesinin sonuçlarını sıralama"
description: "Join tümcesinin sonuçlarını sıralama yapma."
keywords: .NET, .NET core, C#
author: BillWagner
manager: wpickett
ms.author: wiwagn
ms.date: 12/1/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.assetid: a7458901-1201-4c25-b8d9-c04ca52e0eb9
ms.openlocfilehash: f948c18fb16a4f3ac02945b4a63583f1b01cad40
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="order-the-results-of-a-join-clause"></a><span data-ttu-id="70a7e-104">Join tümcesinin sonuçlarını sıralama</span><span class="sxs-lookup"><span data-stu-id="70a7e-104">Order the results of a join clause</span></span>
<span data-ttu-id="70a7e-105">Bu örnek, bir birleştirme işlemi sonuçlarını sıralama gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="70a7e-105">This example shows how to order the results of a join operation.</span></span> <span data-ttu-id="70a7e-106">Sıralama birleştirme sonrasında gerçekleştirildiğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="70a7e-106">Note that the ordering is performed after the join.</span></span> <span data-ttu-id="70a7e-107">Kullanabilirsiniz ancak bir `orderby` yan tümcesi bir veya daha fazla kaynak ile dizilerinin birleştirme öncesinde, genellikle bunu önermiyoruz.</span><span class="sxs-lookup"><span data-stu-id="70a7e-107">Although you can use an `orderby` clause with one or more of the source sequences before the join, generally we do not recommend it.</span></span> <span data-ttu-id="70a7e-108">Bazı LINQ sağlayıcıları bu birleştirme sonrasında sıralama koruyabilir değil.</span><span class="sxs-lookup"><span data-stu-id="70a7e-108">Some LINQ providers might not preserve that ordering after the join.</span></span>  
  
## <a name="example"></a><span data-ttu-id="70a7e-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="70a7e-109">Example</span></span>  
 <span data-ttu-id="70a7e-110">Bu sorgu, bir grup birleşim oluşturur ve hala kapsam içi kategori öğesi temelinde grupları sıralar.</span><span class="sxs-lookup"><span data-stu-id="70a7e-110">This query creates a group join, and then sorts the groups based on the category element, which is still in scope.</span></span> <span data-ttu-id="70a7e-111">Anonim tür başlatıcısı bir alt sorgu ürünleri serisinden eşleşen tüm öğeleri sıralar.</span><span class="sxs-lookup"><span data-stu-id="70a7e-111">Inside the anonymous type initializer, a sub-query orders all the matching elements from the products sequence.</span></span>  
  
 [!code-csharp[csProgGuideLINQ#81](../../../samples/snippets/csharp/concepts/linq/how-to-order-the-results-of-a-join-clause_1.cs)]  
 
## <a name="see-also"></a><span data-ttu-id="70a7e-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="70a7e-112">See also</span></span>  
 [<span data-ttu-id="70a7e-113">LINQ Sorgu ifadeleri</span><span class="sxs-lookup"><span data-stu-id="70a7e-113">LINQ query expressions</span></span>](index.md)  
 [<span data-ttu-id="70a7e-114">OrderBy yan tümcesi</span><span class="sxs-lookup"><span data-stu-id="70a7e-114">orderby clause</span></span>](../language-reference/keywords/orderby-clause.md)  
 [<span data-ttu-id="70a7e-115">Join tümcesi</span><span class="sxs-lookup"><span data-stu-id="70a7e-115">join clause</span></span>](../language-reference/keywords/join-clause.md) 
