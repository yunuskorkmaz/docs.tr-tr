---
title: Join tümcesinin sonuçlarını sıralama
description: Join tümcesinin sonuçlarını sıralama yapma.
ms.date: 12/1/2016
ms.assetid: a7458901-1201-4c25-b8d9-c04ca52e0eb9
ms.openlocfilehash: f426152e614ed9a9c4aa41d7ba7cb8ddf1cd3063
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33269706"
---
# <a name="order-the-results-of-a-join-clause"></a><span data-ttu-id="e08db-103">Join tümcesinin sonuçlarını sıralama</span><span class="sxs-lookup"><span data-stu-id="e08db-103">Order the results of a join clause</span></span>
<span data-ttu-id="e08db-104">Bu örnek, bir birleştirme işlemi sonuçlarını sıralama gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="e08db-104">This example shows how to order the results of a join operation.</span></span> <span data-ttu-id="e08db-105">Sıralama birleştirme sonrasında gerçekleştirildiğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="e08db-105">Note that the ordering is performed after the join.</span></span> <span data-ttu-id="e08db-106">Kullanabilirsiniz ancak bir `orderby` yan tümcesi bir veya daha fazla kaynak ile dizilerinin birleştirme öncesinde, genellikle bunu önermiyoruz.</span><span class="sxs-lookup"><span data-stu-id="e08db-106">Although you can use an `orderby` clause with one or more of the source sequences before the join, generally we do not recommend it.</span></span> <span data-ttu-id="e08db-107">Bazı LINQ sağlayıcıları bu birleştirme sonrasında sıralama koruyabilir değil.</span><span class="sxs-lookup"><span data-stu-id="e08db-107">Some LINQ providers might not preserve that ordering after the join.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e08db-108">Örnek</span><span class="sxs-lookup"><span data-stu-id="e08db-108">Example</span></span>  
 <span data-ttu-id="e08db-109">Bu sorgu, bir grup birleşim oluşturur ve hala kapsam içi kategori öğesi temelinde grupları sıralar.</span><span class="sxs-lookup"><span data-stu-id="e08db-109">This query creates a group join, and then sorts the groups based on the category element, which is still in scope.</span></span> <span data-ttu-id="e08db-110">Anonim tür başlatıcısı bir alt sorgu ürünleri serisinden eşleşen tüm öğeleri sıralar.</span><span class="sxs-lookup"><span data-stu-id="e08db-110">Inside the anonymous type initializer, a sub-query orders all the matching elements from the products sequence.</span></span>  
  
 [!code-csharp[csProgGuideLINQ#81](../../../samples/snippets/csharp/concepts/linq/how-to-order-the-results-of-a-join-clause_1.cs)]  
 
## <a name="see-also"></a><span data-ttu-id="e08db-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e08db-111">See also</span></span>  
 [<span data-ttu-id="e08db-112">LINQ Sorgu ifadeleri</span><span class="sxs-lookup"><span data-stu-id="e08db-112">LINQ query expressions</span></span>](index.md)  
 [<span data-ttu-id="e08db-113">orderby yan tümcesi</span><span class="sxs-lookup"><span data-stu-id="e08db-113">orderby clause</span></span>](../language-reference/keywords/orderby-clause.md)  
 [<span data-ttu-id="e08db-114">join yan tümcesi</span><span class="sxs-lookup"><span data-stu-id="e08db-114">join clause</span></span>](../language-reference/keywords/join-clause.md) 
