---
title: Nicelik belirteci IşlemleriC#()
ms.date: 07/20/2015
ms.assetid: 84ac2ac2-7a63-4581-bc4c-14e34be1493b
ms.openlocfilehash: 4a0f5b2c90d4b71a945dee02a32cbe897818c538
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69591469"
---
# <a name="quantifier-operations-c"></a><span data-ttu-id="d2f3d-102">Nicelik belirteci IşlemleriC#()</span><span class="sxs-lookup"><span data-stu-id="d2f3d-102">Quantifier Operations (C#)</span></span>
<span data-ttu-id="d2f3d-103">Nicelik belirteci işlemleri bir <xref:System.Boolean> dizideki öğelerin bazılarının veya tümünün bir koşulu karşılayıp karşılamadığını belirten bir değer döndürür.</span><span class="sxs-lookup"><span data-stu-id="d2f3d-103">Quantifier operations return a <xref:System.Boolean> value that indicates whether some or all of the elements in a sequence satisfy a condition.</span></span>  
  
 <span data-ttu-id="d2f3d-104">Aşağıdaki çizimde iki farklı kaynak dizisi üzerinde iki farklı belirleyici işlem gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="d2f3d-104">The following illustration depicts two different quantifier operations on two different source sequences.</span></span> <span data-ttu-id="d2f3d-105">İlk işlem, bir veya daha fazla öğenin ' A ' karakteri olup olmadığını sorar ve sonuç olur `true`.</span><span class="sxs-lookup"><span data-stu-id="d2f3d-105">The first operation asks if one or more of the elements are the character 'A', and the result is `true`.</span></span> <span data-ttu-id="d2f3d-106">İkinci işlem, tüm öğelerin ' A ' karakteri olup olmadığını ve sonucun olduğunu `true`sorar.</span><span class="sxs-lookup"><span data-stu-id="d2f3d-106">The second operation asks if all the elements are the character 'A', and the result is `true`.</span></span>  
  
 ![LINQ nicelik belirteci Işlemleri](./media/quantifier-operations/linq-quantifier-operations.png)  
  
 <span data-ttu-id="d2f3d-108">Belirleyici işlemler gerçekleştiren standart sorgu işleci yöntemleri aşağıdaki bölümde listelenmiştir.</span><span class="sxs-lookup"><span data-stu-id="d2f3d-108">The standard query operator methods that perform quantifier operations are listed in the following section.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="d2f3d-109">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="d2f3d-109">Methods</span></span>  
  
|<span data-ttu-id="d2f3d-110">Yöntem adı</span><span class="sxs-lookup"><span data-stu-id="d2f3d-110">Method Name</span></span>|<span data-ttu-id="d2f3d-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d2f3d-111">Description</span></span>|<span data-ttu-id="d2f3d-112">C#Sorgu Ifadesi söz dizimi</span><span class="sxs-lookup"><span data-stu-id="d2f3d-112">C# Query Expression Syntax</span></span>|<span data-ttu-id="d2f3d-113">Daha fazla bilgi</span><span class="sxs-lookup"><span data-stu-id="d2f3d-113">More Information</span></span>|  
|-----------------|-----------------|---------------------------------|----------------------|  
|<span data-ttu-id="d2f3d-114">Tümü</span><span class="sxs-lookup"><span data-stu-id="d2f3d-114">All</span></span>|<span data-ttu-id="d2f3d-115">Bir dizideki tüm öğelerin bir koşulu karşılayıp karşılamadığını belirler.</span><span class="sxs-lookup"><span data-stu-id="d2f3d-115">Determines whether all the elements in a sequence satisfy a condition.</span></span>|<span data-ttu-id="d2f3d-116">Geçerli değildir.</span><span class="sxs-lookup"><span data-stu-id="d2f3d-116">Not applicable.</span></span>|<xref:System.Linq.Enumerable.All%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.All%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="d2f3d-117">Any</span><span class="sxs-lookup"><span data-stu-id="d2f3d-117">Any</span></span>|<span data-ttu-id="d2f3d-118">Bir dizideki herhangi bir öğenin bir koşulu karşılayıp karşılamadığını belirler.</span><span class="sxs-lookup"><span data-stu-id="d2f3d-118">Determines whether any elements in a sequence satisfy a condition.</span></span>|<span data-ttu-id="d2f3d-119">Geçerli değildir.</span><span class="sxs-lookup"><span data-stu-id="d2f3d-119">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Any%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Any%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="d2f3d-120">İçerir</span><span class="sxs-lookup"><span data-stu-id="d2f3d-120">Contains</span></span>|<span data-ttu-id="d2f3d-121">Bir sıranın belirtilen bir öğeyi içerip içermediğini belirler.</span><span class="sxs-lookup"><span data-stu-id="d2f3d-121">Determines whether a sequence contains a specified element.</span></span>|<span data-ttu-id="d2f3d-122">Geçerli değildir.</span><span class="sxs-lookup"><span data-stu-id="d2f3d-122">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Contains%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Contains%2A?displayProperty=nameWithType>|  
  
## <a name="see-also"></a><span data-ttu-id="d2f3d-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d2f3d-123">See also</span></span>

- <xref:System.Linq>
- [<span data-ttu-id="d2f3d-124">Standart sorgu Işleçlerine genelC#bakış ()</span><span class="sxs-lookup"><span data-stu-id="d2f3d-124">Standard Query Operators Overview (C#)</span></span>](./standard-query-operators-overview.md)
- [<span data-ttu-id="d2f3d-125">Nasıl yapılır: Çalışma zamanında koşul filtrelerini dinamik olarak belirtme</span><span class="sxs-lookup"><span data-stu-id="d2f3d-125">How to: Dynamically Specify Predicate Filters at Runtime</span></span>](../../linq-query-expressions/how-to-dynamically-specify-predicate-filters-at-runtime.md)
- [<span data-ttu-id="d2f3d-126">Nasıl yapılır: Belirli bir sözcük kümesini (LINQ) içeren cümleleri sorgulama (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="d2f3d-126">How to: Query for Sentences that Contain a Specified Set of Words (LINQ) (C#)</span></span>](./how-to-query-for-sentences-that-contain-a-specified-set-of-words-linq.md)
