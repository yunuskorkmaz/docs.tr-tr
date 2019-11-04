---
title: Nicelik belirteci IşlemleriC#()
ms.date: 07/20/2015
ms.assetid: 84ac2ac2-7a63-4581-bc4c-14e34be1493b
ms.openlocfilehash: 5899af79799d5b8404e60027d7ba1b005c4b1b79
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73423359"
---
# <a name="quantifier-operations-c"></a><span data-ttu-id="19d43-102">Nicelik belirteci IşlemleriC#()</span><span class="sxs-lookup"><span data-stu-id="19d43-102">Quantifier Operations (C#)</span></span>
<span data-ttu-id="19d43-103">Nicelik belirteci işlemleri bir dizideki öğelerin bazılarının veya tümünün bir koşulu karşılayıp karşılamadığını belirten <xref:System.Boolean> bir değer döndürür.</span><span class="sxs-lookup"><span data-stu-id="19d43-103">Quantifier operations return a <xref:System.Boolean> value that indicates whether some or all of the elements in a sequence satisfy a condition.</span></span>  
  
 <span data-ttu-id="19d43-104">Aşağıdaki çizimde iki farklı kaynak dizisi üzerinde iki farklı belirleyici işlem gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="19d43-104">The following illustration depicts two different quantifier operations on two different source sequences.</span></span> <span data-ttu-id="19d43-105">İlk işlem, bir veya daha fazla öğenin ' A ' karakteri olup olmadığını sorar ve sonuç `true`.</span><span class="sxs-lookup"><span data-stu-id="19d43-105">The first operation asks if one or more of the elements are the character 'A', and the result is `true`.</span></span> <span data-ttu-id="19d43-106">İkinci işlem, tüm öğelerin ' A ' karakteri olup olmadığını sorar ve sonuç `true`.</span><span class="sxs-lookup"><span data-stu-id="19d43-106">The second operation asks if all the elements are the character 'A', and the result is `true`.</span></span>  
  
 ![LINQ nicelik belirteci Işlemleri](./media/quantifier-operations/linq-quantifier-operations.png)  
  
 <span data-ttu-id="19d43-108">Belirleyici işlemler gerçekleştiren standart sorgu işleci yöntemleri aşağıdaki bölümde listelenmiştir.</span><span class="sxs-lookup"><span data-stu-id="19d43-108">The standard query operator methods that perform quantifier operations are listed in the following section.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="19d43-109">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="19d43-109">Methods</span></span>  
  
|<span data-ttu-id="19d43-110">Yöntem adı</span><span class="sxs-lookup"><span data-stu-id="19d43-110">Method Name</span></span>|<span data-ttu-id="19d43-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="19d43-111">Description</span></span>|<span data-ttu-id="19d43-112">C#Sorgu Ifadesi söz dizimi</span><span class="sxs-lookup"><span data-stu-id="19d43-112">C# Query Expression Syntax</span></span>|<span data-ttu-id="19d43-113">Daha fazla bilgi</span><span class="sxs-lookup"><span data-stu-id="19d43-113">More Information</span></span>|  
|-----------------|-----------------|---------------------------------|----------------------|  
|<span data-ttu-id="19d43-114">Tümü</span><span class="sxs-lookup"><span data-stu-id="19d43-114">All</span></span>|<span data-ttu-id="19d43-115">Bir dizideki tüm öğelerin bir koşulu karşılayıp karşılamadığını belirler.</span><span class="sxs-lookup"><span data-stu-id="19d43-115">Determines whether all the elements in a sequence satisfy a condition.</span></span>|<span data-ttu-id="19d43-116">Yok.</span><span class="sxs-lookup"><span data-stu-id="19d43-116">Not applicable.</span></span>|<xref:System.Linq.Enumerable.All%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.All%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="19d43-117">Kaydedilmemiş</span><span class="sxs-lookup"><span data-stu-id="19d43-117">Any</span></span>|<span data-ttu-id="19d43-118">Bir dizideki herhangi bir öğenin bir koşulu karşılayıp karşılamadığını belirler.</span><span class="sxs-lookup"><span data-stu-id="19d43-118">Determines whether any elements in a sequence satisfy a condition.</span></span>|<span data-ttu-id="19d43-119">Yok.</span><span class="sxs-lookup"><span data-stu-id="19d43-119">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Any%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Any%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="19d43-120">İçerir</span><span class="sxs-lookup"><span data-stu-id="19d43-120">Contains</span></span>|<span data-ttu-id="19d43-121">Bir sıranın belirtilen bir öğeyi içerip içermediğini belirler.</span><span class="sxs-lookup"><span data-stu-id="19d43-121">Determines whether a sequence contains a specified element.</span></span>|<span data-ttu-id="19d43-122">Yok.</span><span class="sxs-lookup"><span data-stu-id="19d43-122">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Contains%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Contains%2A?displayProperty=nameWithType>|  
  
## <a name="see-also"></a><span data-ttu-id="19d43-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="19d43-123">See also</span></span>

- <xref:System.Linq>
- [<span data-ttu-id="19d43-124">Standart sorgu Işleçlerine genelC#bakış ()</span><span class="sxs-lookup"><span data-stu-id="19d43-124">Standard Query Operators Overview (C#)</span></span>](./standard-query-operators-overview.md)
- [<span data-ttu-id="19d43-125">Nasıl yapılır: çalışma zamanında koşul filtrelerini dinamik olarak belirtme</span><span class="sxs-lookup"><span data-stu-id="19d43-125">How to: Dynamically Specify Predicate Filters at Runtime</span></span>](../../../linq/dynamically-specify-predicate-filters-at-runtime.md)
- [<span data-ttu-id="19d43-126">Nasıl yapılır: belirli bir sözcükler kümesini içeren cümleleri sorgulama (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="19d43-126">How to: Query for Sentences that Contain a Specified Set of Words (LINQ) (C#)</span></span>](./how-to-query-for-sentences-that-contain-a-specified-set-of-words-linq.md)
