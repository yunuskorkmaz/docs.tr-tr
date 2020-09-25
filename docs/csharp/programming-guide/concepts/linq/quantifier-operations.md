---
title: Nicelik belirteci Işlemleri (C#)
description: Belirleyici işlemler hakkında bilgi edinin. Bu işlemler, bir dizideki bazı veya tüm öğelerin bir koşulu karşılayıp karşılamadığını belirten bir Boole değeri döndürür.
ms.date: 07/20/2015
ms.assetid: 84ac2ac2-7a63-4581-bc4c-14e34be1493b
ms.openlocfilehash: ffefe1715fd8a074692967e825e0f55673bb2b27
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91202545"
---
# <a name="quantifier-operations-c"></a><span data-ttu-id="d4f69-104">Nicelik belirteci Işlemleri (C#)</span><span class="sxs-lookup"><span data-stu-id="d4f69-104">Quantifier Operations (C#)</span></span>

<span data-ttu-id="d4f69-105">Nicelik belirteci işlemleri bir <xref:System.Boolean> dizideki öğelerin bazılarının veya tümünün bir koşulu karşılayıp karşılamadığını belirten bir değer döndürür.</span><span class="sxs-lookup"><span data-stu-id="d4f69-105">Quantifier operations return a <xref:System.Boolean> value that indicates whether some or all of the elements in a sequence satisfy a condition.</span></span>  
  
 <span data-ttu-id="d4f69-106">Aşağıdaki çizimde iki farklı kaynak dizisi üzerinde iki farklı belirleyici işlem gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="d4f69-106">The following illustration depicts two different quantifier operations on two different source sequences.</span></span> <span data-ttu-id="d4f69-107">İlk işlem, bir veya daha fazla öğenin ' A ' karakteri olup olmadığını sorar ve sonuç olur `true` .</span><span class="sxs-lookup"><span data-stu-id="d4f69-107">The first operation asks if one or more of the elements are the character 'A', and the result is `true`.</span></span> <span data-ttu-id="d4f69-108">İkinci işlem, tüm öğelerin ' A ' karakteri olup olmadığını ve sonucun olduğunu sorar `true` .</span><span class="sxs-lookup"><span data-stu-id="d4f69-108">The second operation asks if all the elements are the character 'A', and the result is `true`.</span></span>  
  
 ![LINQ nicelik belirteci Işlemleri](./media/quantifier-operations/linq-quantifier-operations.png)  
  
 <span data-ttu-id="d4f69-110">Belirleyici işlemler gerçekleştiren standart sorgu işleci yöntemleri aşağıdaki bölümde listelenmiştir.</span><span class="sxs-lookup"><span data-stu-id="d4f69-110">The standard query operator methods that perform quantifier operations are listed in the following section.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="d4f69-111">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="d4f69-111">Methods</span></span>  
  
|<span data-ttu-id="d4f69-112">Yöntem adı</span><span class="sxs-lookup"><span data-stu-id="d4f69-112">Method Name</span></span>|<span data-ttu-id="d4f69-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d4f69-113">Description</span></span>|<span data-ttu-id="d4f69-114">C# sorgu Ifadesi sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d4f69-114">C# Query Expression Syntax</span></span>|<span data-ttu-id="d4f69-115">Daha Fazla Bilgi</span><span class="sxs-lookup"><span data-stu-id="d4f69-115">More Information</span></span>|  
|-----------------|-----------------|---------------------------------|----------------------|  
|<span data-ttu-id="d4f69-116">Tümü</span><span class="sxs-lookup"><span data-stu-id="d4f69-116">All</span></span>|<span data-ttu-id="d4f69-117">Bir dizideki tüm öğelerin bir koşulu karşılayıp karşılamadığını belirler.</span><span class="sxs-lookup"><span data-stu-id="d4f69-117">Determines whether all the elements in a sequence satisfy a condition.</span></span>|<span data-ttu-id="d4f69-118">Geçerli değildir.</span><span class="sxs-lookup"><span data-stu-id="d4f69-118">Not applicable.</span></span>|<xref:System.Linq.Enumerable.All%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.All%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="d4f69-119">Herhangi biri</span><span class="sxs-lookup"><span data-stu-id="d4f69-119">Any</span></span>|<span data-ttu-id="d4f69-120">Bir dizideki herhangi bir öğenin bir koşulu karşılayıp karşılamadığını belirler.</span><span class="sxs-lookup"><span data-stu-id="d4f69-120">Determines whether any elements in a sequence satisfy a condition.</span></span>|<span data-ttu-id="d4f69-121">Geçerli değildir.</span><span class="sxs-lookup"><span data-stu-id="d4f69-121">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Any%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Any%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="d4f69-122">Contains</span><span class="sxs-lookup"><span data-stu-id="d4f69-122">Contains</span></span>|<span data-ttu-id="d4f69-123">Bir sıranın belirtilen bir öğeyi içerip içermediğini belirler.</span><span class="sxs-lookup"><span data-stu-id="d4f69-123">Determines whether a sequence contains a specified element.</span></span>|<span data-ttu-id="d4f69-124">Geçerli değildir.</span><span class="sxs-lookup"><span data-stu-id="d4f69-124">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Contains%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Contains%2A?displayProperty=nameWithType>|  

## <a name="query-expression-syntax-examples"></a><span data-ttu-id="d4f69-125">Sorgu Ifadesi söz dizimi örnekleri</span><span class="sxs-lookup"><span data-stu-id="d4f69-125">Query Expression Syntax Examples</span></span>  
  
### <a name="all"></a><span data-ttu-id="d4f69-126">Tümü</span><span class="sxs-lookup"><span data-stu-id="d4f69-126">All</span></span>  

<span data-ttu-id="d4f69-127">Aşağıdaki örnek, `All` tüm dizelerin belirli bir uzunlukta olduğunu denetlemek için öğesini kullanır.</span><span class="sxs-lookup"><span data-stu-id="d4f69-127">The following example uses the `All` to check that all strings are of a specific length.</span></span>
  
[!code-csharp[All](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQQuantifier/CS/Quantifier.cs#All)]  
  
### <a name="any"></a><span data-ttu-id="d4f69-128">Herhangi biri</span><span class="sxs-lookup"><span data-stu-id="d4f69-128">Any</span></span>  

<span data-ttu-id="d4f69-129">Aşağıdaki örnek `Any` ' o ' ile başlayan dizelerin olduğunu denetlemek için öğesini kullanır.</span><span class="sxs-lookup"><span data-stu-id="d4f69-129">The following example uses the `Any` to check that any strings are start with 'o'.</span></span>  
  
[!code-csharp[Any](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQQuantifier/CS/Quantifier.cs#Any)]  
  
### <a name="contains"></a><span data-ttu-id="d4f69-130">Contains</span><span class="sxs-lookup"><span data-stu-id="d4f69-130">Contains</span></span>  

<span data-ttu-id="d4f69-131">Aşağıdaki örnek, `Contains` bir diziyi denetlemek için öğesini kullanır, belirli bir öğesi.</span><span class="sxs-lookup"><span data-stu-id="d4f69-131">The following example uses the `Contains` to check an array have a specific element.</span></span>  
  
[!code-csharp[Contains](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQQuantifier/CS/Quantifier.cs#Contains)]  
  
## <a name="see-also"></a><span data-ttu-id="d4f69-132">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d4f69-132">See also</span></span>

- <xref:System.Linq>
- [<span data-ttu-id="d4f69-133">Standart sorgu Işleçlerine genel bakış (C#)</span><span class="sxs-lookup"><span data-stu-id="d4f69-133">Standard Query Operators Overview (C#)</span></span>](./standard-query-operators-overview.md)
- [<span data-ttu-id="d4f69-134">Çalışma zamanında koşul filtrelerini dinamik olarak belirtme</span><span class="sxs-lookup"><span data-stu-id="d4f69-134">Dynamically specify predicate filters at runtime</span></span>](../../../linq/dynamically-specify-predicate-filters-at-runtime.md)
- [<span data-ttu-id="d4f69-135">Belirli bir sözcük kümesini (LINQ) içeren cümleleri sorgulama (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="d4f69-135">How to query for sentences that contain a specified set of words (LINQ) (C#)</span></span>](./how-to-query-for-sentences-that-contain-a-specified-set-of-words-linq.md)
