---
title: Nicelik belirteci IşlemleriC#()
ms.date: 07/20/2015
ms.assetid: 84ac2ac2-7a63-4581-bc4c-14e34be1493b
ms.openlocfilehash: 5c931e0971a2ae7970415905be8772a64a82ee39
ms.sourcegitcommit: 7bc6887ab658550baa78f1520ea735838249345e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/03/2020
ms.locfileid: "75635489"
---
# <a name="quantifier-operations-c"></a><span data-ttu-id="41817-102">Nicelik belirteci IşlemleriC#()</span><span class="sxs-lookup"><span data-stu-id="41817-102">Quantifier Operations (C#)</span></span>
<span data-ttu-id="41817-103">Nicelik belirteci işlemleri bir dizideki öğelerin bazılarının veya tümünün bir koşulu karşılayıp karşılamadığını belirten <xref:System.Boolean> bir değer döndürür.</span><span class="sxs-lookup"><span data-stu-id="41817-103">Quantifier operations return a <xref:System.Boolean> value that indicates whether some or all of the elements in a sequence satisfy a condition.</span></span>  
  
 <span data-ttu-id="41817-104">Aşağıdaki çizimde iki farklı kaynak dizisi üzerinde iki farklı belirleyici işlem gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="41817-104">The following illustration depicts two different quantifier operations on two different source sequences.</span></span> <span data-ttu-id="41817-105">İlk işlem, bir veya daha fazla öğenin ' A ' karakteri olup olmadığını sorar ve sonuç `true`.</span><span class="sxs-lookup"><span data-stu-id="41817-105">The first operation asks if one or more of the elements are the character 'A', and the result is `true`.</span></span> <span data-ttu-id="41817-106">İkinci işlem, tüm öğelerin ' A ' karakteri olup olmadığını sorar ve sonuç `true`.</span><span class="sxs-lookup"><span data-stu-id="41817-106">The second operation asks if all the elements are the character 'A', and the result is `true`.</span></span>  
  
 ![LINQ nicelik belirteci Işlemleri](./media/quantifier-operations/linq-quantifier-operations.png)  
  
 <span data-ttu-id="41817-108">Belirleyici işlemler gerçekleştiren standart sorgu işleci yöntemleri aşağıdaki bölümde listelenmiştir.</span><span class="sxs-lookup"><span data-stu-id="41817-108">The standard query operator methods that perform quantifier operations are listed in the following section.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="41817-109">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="41817-109">Methods</span></span>  
  
|<span data-ttu-id="41817-110">Yöntem adı</span><span class="sxs-lookup"><span data-stu-id="41817-110">Method Name</span></span>|<span data-ttu-id="41817-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="41817-111">Description</span></span>|<span data-ttu-id="41817-112">C#Sorgu Ifadesi söz dizimi</span><span class="sxs-lookup"><span data-stu-id="41817-112">C# Query Expression Syntax</span></span>|<span data-ttu-id="41817-113">Daha fazla bilgi</span><span class="sxs-lookup"><span data-stu-id="41817-113">More Information</span></span>|  
|-----------------|-----------------|---------------------------------|----------------------|  
|<span data-ttu-id="41817-114">Tümü</span><span class="sxs-lookup"><span data-stu-id="41817-114">All</span></span>|<span data-ttu-id="41817-115">Bir dizideki tüm öğelerin bir koşulu karşılayıp karşılamadığını belirler.</span><span class="sxs-lookup"><span data-stu-id="41817-115">Determines whether all the elements in a sequence satisfy a condition.</span></span>|<span data-ttu-id="41817-116">Yok.</span><span class="sxs-lookup"><span data-stu-id="41817-116">Not applicable.</span></span>|<xref:System.Linq.Enumerable.All%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.All%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="41817-117">Tümü</span><span class="sxs-lookup"><span data-stu-id="41817-117">Any</span></span>|<span data-ttu-id="41817-118">Bir dizideki herhangi bir öğenin bir koşulu karşılayıp karşılamadığını belirler.</span><span class="sxs-lookup"><span data-stu-id="41817-118">Determines whether any elements in a sequence satisfy a condition.</span></span>|<span data-ttu-id="41817-119">Yok.</span><span class="sxs-lookup"><span data-stu-id="41817-119">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Any%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Any%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="41817-120">İçerir</span><span class="sxs-lookup"><span data-stu-id="41817-120">Contains</span></span>|<span data-ttu-id="41817-121">Bir sıranın belirtilen bir öğeyi içerip içermediğini belirler.</span><span class="sxs-lookup"><span data-stu-id="41817-121">Determines whether a sequence contains a specified element.</span></span>|<span data-ttu-id="41817-122">Yok.</span><span class="sxs-lookup"><span data-stu-id="41817-122">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Contains%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Contains%2A?displayProperty=nameWithType>|  

## <a name="query-expression-syntax-examples"></a><span data-ttu-id="41817-123">Sorgu Ifadesi söz dizimi örnekleri</span><span class="sxs-lookup"><span data-stu-id="41817-123">Query Expression Syntax Examples</span></span>  
  
### <a name="all"></a><span data-ttu-id="41817-124">Tümü</span><span class="sxs-lookup"><span data-stu-id="41817-124">All</span></span>  
<span data-ttu-id="41817-125">Aşağıdaki örnek, tüm dizelerin belirli bir uzunlukta olduğunu denetlemek için `All` kullanır.</span><span class="sxs-lookup"><span data-stu-id="41817-125">The following example uses the `All` to check that all strings are of a specific length.</span></span>
  
[!code-csharp[All](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQQuantifier/CS/Quantifier.cs#All)]  
  
### <a name="any"></a><span data-ttu-id="41817-126">Tümü</span><span class="sxs-lookup"><span data-stu-id="41817-126">Any</span></span>  
<span data-ttu-id="41817-127">Aşağıdaki örnek, tüm dizelerin ' o ' ile başlayıp başlamamı kontrol etmek için `Any` kullanır.</span><span class="sxs-lookup"><span data-stu-id="41817-127">The following example uses the `Any` to check that any strings are start with 'o'.</span></span>  
  
[!code-csharp[Any](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQQuantifier/CS/Quantifier.cs#Any)]  
  
### <a name="contains"></a><span data-ttu-id="41817-128">İçerir</span><span class="sxs-lookup"><span data-stu-id="41817-128">Contains</span></span>  
<span data-ttu-id="41817-129">Aşağıdaki örnek, bir dizinin belirli bir öğeye sahip olup olmadığını denetlemek için `Contains` kullanır.</span><span class="sxs-lookup"><span data-stu-id="41817-129">The following example uses the `Contains` to check an array have a specific element.</span></span>  
  
[!code-csharp[Contains](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQQuantifier/CS/Quantifier.cs#Contains)]  
  
## <a name="see-also"></a><span data-ttu-id="41817-130">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="41817-130">See also</span></span>

- <xref:System.Linq>
- [<span data-ttu-id="41817-131">Standart sorgu Işleçlerine genelC#bakış ()</span><span class="sxs-lookup"><span data-stu-id="41817-131">Standard Query Operators Overview (C#)</span></span>](./standard-query-operators-overview.md)
- [<span data-ttu-id="41817-132">Çalışma zamanında koşul filtrelerini dinamik olarak belirtme</span><span class="sxs-lookup"><span data-stu-id="41817-132">Dynamically specify predicate filters at runtime</span></span>](../../../linq/dynamically-specify-predicate-filters-at-runtime.md)
- [<span data-ttu-id="41817-133">Belirli bir sözcük kümesini (LINQ) içeren cümleleri sorgulama (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="41817-133">How to query for sentences that contain a specified set of words (LINQ) (C#)</span></span>](./how-to-query-for-sentences-that-contain-a-specified-set-of-words-linq.md)
