---
title: Birleştirme yan tümcesinin sonuçlarını sipariş edin (C#'da LINQ)
description: C#'daki LINQ birleştirme yan tümcesinin sonuçlarını nasıl sipariş edebilirsiniz öğrenin.
ms.date: 12/01/2016
ms.assetid: a7458901-1201-4c25-b8d9-c04ca52e0eb9
ms.openlocfilehash: f60000b83bf378dd8740b7255d421dd4335614c4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "61659871"
---
# <a name="order-the-results-of-a-join-clause"></a><span data-ttu-id="7806a-103">Join yan tümcesinin sonuçlarını sıralama</span><span class="sxs-lookup"><span data-stu-id="7806a-103">Order the results of a join clause</span></span>

<span data-ttu-id="7806a-104">Bu örnek, birbirle işleminin sonuçlarının nasıl sıralanın gösteriş olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="7806a-104">This example shows how to order the results of a join operation.</span></span> <span data-ttu-id="7806a-105">Sıralamanın birleştirmeden sonra gerçekleştirildiğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="7806a-105">Note that the ordering is performed after the join.</span></span> <span data-ttu-id="7806a-106">Birleştirmeden önce `orderby` kaynak dizilerinden bir veya daha fazlasına sahip bir yan tümce yi kullanabilirsiniz, ancak genellikle bunu önermiyoruz.</span><span class="sxs-lookup"><span data-stu-id="7806a-106">Although you can use an `orderby` clause with one or more of the source sequences before the join, generally we do not recommend it.</span></span> <span data-ttu-id="7806a-107">Bazı LINQ sağlayıcıları birleştirmeden sonra bu siparişi koruyamayabilir.</span><span class="sxs-lookup"><span data-stu-id="7806a-107">Some LINQ providers might not preserve that ordering after the join.</span></span>

## <a name="example"></a><span data-ttu-id="7806a-108">Örnek</span><span class="sxs-lookup"><span data-stu-id="7806a-108">Example</span></span>

<span data-ttu-id="7806a-109">Bu sorgu bir grup birleştirme oluşturur ve sonra hala kapsam içinde olan kategori öğesine göre grupları sıralar.</span><span class="sxs-lookup"><span data-stu-id="7806a-109">This query creates a group join, and then sorts the groups based on the category element, which is still in scope.</span></span> <span data-ttu-id="7806a-110">Anonim tür baş harfinin içinde, bir alt sorgu ürün dizisindeki tüm eşleşen öğeleri sıralar.</span><span class="sxs-lookup"><span data-stu-id="7806a-110">Inside the anonymous type initializer, a sub-query orders all the matching elements from the products sequence.</span></span>

[!code-csharp[csProgGuideLINQ#81](~/samples/snippets/csharp/concepts/linq/how-to-order-the-results-of-a-join-clause_1.cs)]

## <a name="see-also"></a><span data-ttu-id="7806a-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7806a-111">See also</span></span>

- [<span data-ttu-id="7806a-112">Dil ile Tümleşik Sorgu (LINQ)</span><span class="sxs-lookup"><span data-stu-id="7806a-112">Language Integrated Query (LINQ)</span></span>](index.md)
- [<span data-ttu-id="7806a-113">orderby yan tümcesi</span><span class="sxs-lookup"><span data-stu-id="7806a-113">orderby clause</span></span>](../language-reference/keywords/orderby-clause.md)
- [<span data-ttu-id="7806a-114">birleştirme yan tümcesi</span><span class="sxs-lookup"><span data-stu-id="7806a-114">join clause</span></span>](../language-reference/keywords/join-clause.md)
