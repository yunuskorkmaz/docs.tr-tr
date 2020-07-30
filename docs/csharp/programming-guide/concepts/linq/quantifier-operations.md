---
title: Nicelik belirteci Işlemleri (C#)
description: Belirleyici işlemler hakkında bilgi edinin. Bu işlemler, bir dizideki bazı veya tüm öğelerin bir koşulu karşılayıp karşılamadığını belirten bir Boole değeri döndürür.
ms.date: 07/20/2015
ms.assetid: 84ac2ac2-7a63-4581-bc4c-14e34be1493b
ms.openlocfilehash: ce06f887d3ad7b10cbdedf9e33072df2c0819ef1
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/28/2020
ms.locfileid: "87299155"
---
# <a name="quantifier-operations-c"></a><span data-ttu-id="8f828-104">Nicelik belirteci Işlemleri (C#)</span><span class="sxs-lookup"><span data-stu-id="8f828-104">Quantifier Operations (C#)</span></span>
<span data-ttu-id="8f828-105">Nicelik belirteci işlemleri bir <xref:System.Boolean> dizideki öğelerin bazılarının veya tümünün bir koşulu karşılayıp karşılamadığını belirten bir değer döndürür.</span><span class="sxs-lookup"><span data-stu-id="8f828-105">Quantifier operations return a <xref:System.Boolean> value that indicates whether some or all of the elements in a sequence satisfy a condition.</span></span>  
  
 <span data-ttu-id="8f828-106">Aşağıdaki çizimde iki farklı kaynak dizisi üzerinde iki farklı belirleyici işlem gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="8f828-106">The following illustration depicts two different quantifier operations on two different source sequences.</span></span> <span data-ttu-id="8f828-107">İlk işlem, bir veya daha fazla öğenin ' A ' karakteri olup olmadığını sorar ve sonuç olur `true` .</span><span class="sxs-lookup"><span data-stu-id="8f828-107">The first operation asks if one or more of the elements are the character 'A', and the result is `true`.</span></span> <span data-ttu-id="8f828-108">İkinci işlem, tüm öğelerin ' A ' karakteri olup olmadığını ve sonucun olduğunu sorar `true` .</span><span class="sxs-lookup"><span data-stu-id="8f828-108">The second operation asks if all the elements are the character 'A', and the result is `true`.</span></span>  
  
 ![LINQ nicelik belirteci Işlemleri](./media/quantifier-operations/linq-quantifier-operations.png)  
  
 <span data-ttu-id="8f828-110">Belirleyici işlemler gerçekleştiren standart sorgu işleci yöntemleri aşağıdaki bölümde listelenmiştir.</span><span class="sxs-lookup"><span data-stu-id="8f828-110">The standard query operator methods that perform quantifier operations are listed in the following section.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="8f828-111">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="8f828-111">Methods</span></span>  
  
|<span data-ttu-id="8f828-112">Yöntem adı</span><span class="sxs-lookup"><span data-stu-id="8f828-112">Method Name</span></span>|<span data-ttu-id="8f828-113">Description</span><span class="sxs-lookup"><span data-stu-id="8f828-113">Description</span></span>|<span data-ttu-id="8f828-114">C# sorgu Ifadesi sözdizimi</span><span class="sxs-lookup"><span data-stu-id="8f828-114">C# Query Expression Syntax</span></span>|<span data-ttu-id="8f828-115">Daha Fazla Bilgi</span><span class="sxs-lookup"><span data-stu-id="8f828-115">More Information</span></span>|  
|-----------------|-----------------|---------------------------------|----------------------|  
|<span data-ttu-id="8f828-116">Tümü</span><span class="sxs-lookup"><span data-stu-id="8f828-116">All</span></span>|<span data-ttu-id="8f828-117">Bir dizideki tüm öğelerin bir koşulu karşılayıp karşılamadığını belirler.</span><span class="sxs-lookup"><span data-stu-id="8f828-117">Determines whether all the elements in a sequence satisfy a condition.</span></span>|<span data-ttu-id="8f828-118">Geçerli değildir.</span><span class="sxs-lookup"><span data-stu-id="8f828-118">Not applicable.</span></span>|<xref:System.Linq.Enumerable.All%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.All%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="8f828-119">Herhangi bir</span><span class="sxs-lookup"><span data-stu-id="8f828-119">Any</span></span>|<span data-ttu-id="8f828-120">Bir dizideki herhangi bir öğenin bir koşulu karşılayıp karşılamadığını belirler.</span><span class="sxs-lookup"><span data-stu-id="8f828-120">Determines whether any elements in a sequence satisfy a condition.</span></span>|<span data-ttu-id="8f828-121">Geçerli değildir.</span><span class="sxs-lookup"><span data-stu-id="8f828-121">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Any%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Any%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="8f828-122">Contains</span><span class="sxs-lookup"><span data-stu-id="8f828-122">Contains</span></span>|<span data-ttu-id="8f828-123">Bir sıranın belirtilen bir öğeyi içerip içermediğini belirler.</span><span class="sxs-lookup"><span data-stu-id="8f828-123">Determines whether a sequence contains a specified element.</span></span>|<span data-ttu-id="8f828-124">Geçerli değildir.</span><span class="sxs-lookup"><span data-stu-id="8f828-124">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Contains%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Contains%2A?displayProperty=nameWithType>|  

## <a name="query-expression-syntax-examples"></a><span data-ttu-id="8f828-125">Sorgu Ifadesi söz dizimi örnekleri</span><span class="sxs-lookup"><span data-stu-id="8f828-125">Query Expression Syntax Examples</span></span>  
  
### <a name="all"></a><span data-ttu-id="8f828-126">Tümü</span><span class="sxs-lookup"><span data-stu-id="8f828-126">All</span></span>  
<span data-ttu-id="8f828-127">Aşağıdaki örnek, `All` tüm dizelerin belirli bir uzunlukta olduğunu denetlemek için öğesini kullanır.</span><span class="sxs-lookup"><span data-stu-id="8f828-127">The following example uses the `All` to check that all strings are of a specific length.</span></span>
  
[!code-csharp[All](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQQuantifier/CS/Quantifier.cs#All)]  
  
### <a name="any"></a><span data-ttu-id="8f828-128">Herhangi bir</span><span class="sxs-lookup"><span data-stu-id="8f828-128">Any</span></span>  
<span data-ttu-id="8f828-129">Aşağıdaki örnek `Any` ' o ' ile başlayan dizelerin olduğunu denetlemek için öğesini kullanır.</span><span class="sxs-lookup"><span data-stu-id="8f828-129">The following example uses the `Any` to check that any strings are start with 'o'.</span></span>  
  
[!code-csharp[Any](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQQuantifier/CS/Quantifier.cs#Any)]  
  
### <a name="contains"></a><span data-ttu-id="8f828-130">Contains</span><span class="sxs-lookup"><span data-stu-id="8f828-130">Contains</span></span>  
<span data-ttu-id="8f828-131">Aşağıdaki örnek, `Contains` bir diziyi denetlemek için öğesini kullanır, belirli bir öğesi.</span><span class="sxs-lookup"><span data-stu-id="8f828-131">The following example uses the `Contains` to check an array have a specific element.</span></span>  
  
[!code-csharp[Contains](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQQuantifier/CS/Quantifier.cs#Contains)]  
  
## <a name="see-also"></a><span data-ttu-id="8f828-132">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8f828-132">See also</span></span>

- <xref:System.Linq>
- [<span data-ttu-id="8f828-133">Standart sorgu Işleçlerine genel bakış (C#)</span><span class="sxs-lookup"><span data-stu-id="8f828-133">Standard Query Operators Overview (C#)</span></span>](./standard-query-operators-overview.md)
- [<span data-ttu-id="8f828-134">Çalışma zamanında koşul filtrelerini dinamik olarak belirtme</span><span class="sxs-lookup"><span data-stu-id="8f828-134">Dynamically specify predicate filters at runtime</span></span>](../../../linq/dynamically-specify-predicate-filters-at-runtime.md)
- [<span data-ttu-id="8f828-135">Belirli bir sözcük kümesini (LINQ) içeren cümleleri sorgulama (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="8f828-135">How to query for sentences that contain a specified set of words (LINQ) (C#)</span></span>](./how-to-query-for-sentences-that-contain-a-specified-set-of-words-linq.md)
