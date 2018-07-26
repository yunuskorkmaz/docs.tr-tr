---
title: (C# üzerinde LINQ) join tümcesinin sonuçlarını sıralama
description: C# LINQ join tümcesinin sonuçlarını sıralama öğrenin.
ms.date: 12/1/2016
ms.assetid: a7458901-1201-4c25-b8d9-c04ca52e0eb9
ms.openlocfilehash: e4a12b6f9b4a99decb1f64524ebe67a196084a04
ms.sourcegitcommit: 4c158beee818c408d45a9609bfc06f209a523e22
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/03/2018
ms.locfileid: "37404742"
---
# <a name="order-the-results-of-a-join-clause"></a><span data-ttu-id="8aae7-103">Join tümcesinin sonuçlarını sıralama</span><span class="sxs-lookup"><span data-stu-id="8aae7-103">Order the results of a join clause</span></span>

<span data-ttu-id="8aae7-104">Bu örnek, bir birleştirme işleminin sonuçlarını sıralama gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="8aae7-104">This example shows how to order the results of a join operation.</span></span> <span data-ttu-id="8aae7-105">Sıralama alanına katılım işleminden gerçekleştirildiğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="8aae7-105">Note that the ordering is performed after the join.</span></span> <span data-ttu-id="8aae7-106">Hizmetini kullanıyor olsanız da bir `orderby` yan tümcesi bir veya daha fazla kaynak ile birleştirme öncesinde dizilerinin, genellikle bunu önermiyoruz.</span><span class="sxs-lookup"><span data-stu-id="8aae7-106">Although you can use an `orderby` clause with one or more of the source sequences before the join, generally we do not recommend it.</span></span> <span data-ttu-id="8aae7-107">Bazı LINQ sağlayıcıları sıralama alanına katılım işleminden koruyabilir değil.</span><span class="sxs-lookup"><span data-stu-id="8aae7-107">Some LINQ providers might not preserve that ordering after the join.</span></span>

## <a name="example"></a><span data-ttu-id="8aae7-108">Örnek</span><span class="sxs-lookup"><span data-stu-id="8aae7-108">Example</span></span>

<span data-ttu-id="8aae7-109">Bu sorgu, bir grup birleştirme oluşturur ve sonra hala kapsamındaki kategori öğesi temelinde grupları sıralar.</span><span class="sxs-lookup"><span data-stu-id="8aae7-109">This query creates a group join, and then sorts the groups based on the category element, which is still in scope.</span></span> <span data-ttu-id="8aae7-110">Anonim tür başlatıcı içinde alt sorguda ürünleri serisinden eşleşen tüm öğeleri sıralar.</span><span class="sxs-lookup"><span data-stu-id="8aae7-110">Inside the anonymous type initializer, a sub-query orders all the matching elements from the products sequence.</span></span>

[!code-csharp[csProgGuideLINQ#81](~/samples/snippets/csharp/concepts/linq/how-to-order-the-results-of-a-join-clause_1.cs)]

## <a name="see-also"></a><span data-ttu-id="8aae7-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8aae7-111">See also</span></span>

[<span data-ttu-id="8aae7-112">Dil ile Tümleşik Sorgu (LINQ)</span><span class="sxs-lookup"><span data-stu-id="8aae7-112">Language Integrated Query (LINQ)</span></span>](index.md)  
[<span data-ttu-id="8aae7-113">orderby yan tümcesi</span><span class="sxs-lookup"><span data-stu-id="8aae7-113">orderby clause</span></span>](../language-reference/keywords/orderby-clause.md)  
[<span data-ttu-id="8aae7-114">join yan tümcesi</span><span class="sxs-lookup"><span data-stu-id="8aae7-114">join clause</span></span>](../language-reference/keywords/join-clause.md)  