---
title: Niceleyici İşlemleri (C#)
ms.date: 07/20/2015
ms.assetid: 84ac2ac2-7a63-4581-bc4c-14e34be1493b
ms.openlocfilehash: 5c931e0971a2ae7970415905be8772a64a82ee39
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75635489"
---
# <a name="quantifier-operations-c"></a><span data-ttu-id="25e32-102">Niceleyici İşlemleri (C#)</span><span class="sxs-lookup"><span data-stu-id="25e32-102">Quantifier Operations (C#)</span></span>
<span data-ttu-id="25e32-103">Niceleyici işlemleri, bir <xref:System.Boolean> dizideki öğelerden bazılarının veya tümünün bir koşulu karşılayıp karşıladığını gösteren bir değer döndürer.</span><span class="sxs-lookup"><span data-stu-id="25e32-103">Quantifier operations return a <xref:System.Boolean> value that indicates whether some or all of the elements in a sequence satisfy a condition.</span></span>  
  
 <span data-ttu-id="25e32-104">Aşağıdaki resimde, iki farklı kaynak dizisinde iki farklı niceleme işlemi gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="25e32-104">The following illustration depicts two different quantifier operations on two different source sequences.</span></span> <span data-ttu-id="25e32-105">İlk işlem, öğelerden birinin veya daha fazlasının 'A' karakteri `true`olup olmadığını sorar ve sonuç .</span><span class="sxs-lookup"><span data-stu-id="25e32-105">The first operation asks if one or more of the elements are the character 'A', and the result is `true`.</span></span> <span data-ttu-id="25e32-106">İkinci işlem tüm öğelerin 'A' karakteri olup olmadığını `true`sorar ve sonuç .</span><span class="sxs-lookup"><span data-stu-id="25e32-106">The second operation asks if all the elements are the character 'A', and the result is `true`.</span></span>  
  
 ![LINQ Niceleme İşlemleri](./media/quantifier-operations/linq-quantifier-operations.png)  
  
 <span data-ttu-id="25e32-108">Niceleyici işlemleri gerçekleştiren standart sorgu işleci yöntemleri aşağıdaki bölümde listelenmiştir.</span><span class="sxs-lookup"><span data-stu-id="25e32-108">The standard query operator methods that perform quantifier operations are listed in the following section.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="25e32-109">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="25e32-109">Methods</span></span>  
  
|<span data-ttu-id="25e32-110">Yöntem Adı</span><span class="sxs-lookup"><span data-stu-id="25e32-110">Method Name</span></span>|<span data-ttu-id="25e32-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="25e32-111">Description</span></span>|<span data-ttu-id="25e32-112">C# Sorgu İfade Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="25e32-112">C# Query Expression Syntax</span></span>|<span data-ttu-id="25e32-113">Daha Fazla Bilgi</span><span class="sxs-lookup"><span data-stu-id="25e32-113">More Information</span></span>|  
|-----------------|-----------------|---------------------------------|----------------------|  
|<span data-ttu-id="25e32-114">Tümü</span><span class="sxs-lookup"><span data-stu-id="25e32-114">All</span></span>|<span data-ttu-id="25e32-115">Bir dizideki tüm öğelerin bir koşulu karşılayıp karşılamadığını belirler.</span><span class="sxs-lookup"><span data-stu-id="25e32-115">Determines whether all the elements in a sequence satisfy a condition.</span></span>|<span data-ttu-id="25e32-116">Geçerli değildir.</span><span class="sxs-lookup"><span data-stu-id="25e32-116">Not applicable.</span></span>|<xref:System.Linq.Enumerable.All%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.All%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="25e32-117">Herhangi biri</span><span class="sxs-lookup"><span data-stu-id="25e32-117">Any</span></span>|<span data-ttu-id="25e32-118">Bir dizideki öğelerin bir durumu karşılayıp karşılamadığını belirler.</span><span class="sxs-lookup"><span data-stu-id="25e32-118">Determines whether any elements in a sequence satisfy a condition.</span></span>|<span data-ttu-id="25e32-119">Geçerli değildir.</span><span class="sxs-lookup"><span data-stu-id="25e32-119">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Any%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Any%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="25e32-120">Contains</span><span class="sxs-lookup"><span data-stu-id="25e32-120">Contains</span></span>|<span data-ttu-id="25e32-121">Bir dizinin belirli bir öğe yi içerip içermediğini belirler.</span><span class="sxs-lookup"><span data-stu-id="25e32-121">Determines whether a sequence contains a specified element.</span></span>|<span data-ttu-id="25e32-122">Geçerli değildir.</span><span class="sxs-lookup"><span data-stu-id="25e32-122">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Contains%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Contains%2A?displayProperty=nameWithType>|  

## <a name="query-expression-syntax-examples"></a><span data-ttu-id="25e32-123">Sorgu İfadesözdizimi Örnekleri</span><span class="sxs-lookup"><span data-stu-id="25e32-123">Query Expression Syntax Examples</span></span>  
  
### <a name="all"></a><span data-ttu-id="25e32-124">Tümü</span><span class="sxs-lookup"><span data-stu-id="25e32-124">All</span></span>  
<span data-ttu-id="25e32-125">Aşağıdaki örnek, `All` tüm dizeleri belirli bir uzunlukta olup olmadığını denetlemek için kullanır.</span><span class="sxs-lookup"><span data-stu-id="25e32-125">The following example uses the `All` to check that all strings are of a specific length.</span></span>
  
[!code-csharp[All](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQQuantifier/CS/Quantifier.cs#All)]  
  
### <a name="any"></a><span data-ttu-id="25e32-126">Herhangi biri</span><span class="sxs-lookup"><span data-stu-id="25e32-126">Any</span></span>  
<span data-ttu-id="25e32-127">Aşağıdaki örnekte, `Any` dizeleri 'o' ile başlatılır olup olmadığını kontrol etmek için kullanır.</span><span class="sxs-lookup"><span data-stu-id="25e32-127">The following example uses the `Any` to check that any strings are start with 'o'.</span></span>  
  
[!code-csharp[Any](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQQuantifier/CS/Quantifier.cs#Any)]  
  
### <a name="contains"></a><span data-ttu-id="25e32-128">Contains</span><span class="sxs-lookup"><span data-stu-id="25e32-128">Contains</span></span>  
<span data-ttu-id="25e32-129">Aşağıdaki örnekte `Contains` belirli bir öğeye sahip bir dizi kontrol etmek için kullanır.</span><span class="sxs-lookup"><span data-stu-id="25e32-129">The following example uses the `Contains` to check an array have a specific element.</span></span>  
  
[!code-csharp[Contains](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQQuantifier/CS/Quantifier.cs#Contains)]  
  
## <a name="see-also"></a><span data-ttu-id="25e32-130">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="25e32-130">See also</span></span>

- <xref:System.Linq>
- [<span data-ttu-id="25e32-131">Standart Sorgu Operatörlerine Genel Bakış (C#)</span><span class="sxs-lookup"><span data-stu-id="25e32-131">Standard Query Operators Overview (C#)</span></span>](./standard-query-operators-overview.md)
- [<span data-ttu-id="25e32-132">Çalışma zamanında koşul filtrelerini dinamik olarak belirtme</span><span class="sxs-lookup"><span data-stu-id="25e32-132">Dynamically specify predicate filters at runtime</span></span>](../../../linq/dynamically-specify-predicate-filters-at-runtime.md)
- [<span data-ttu-id="25e32-133">Belirli bir sözcük kümesi (LINQ) (C#) içeren cümleler için sorgulama</span><span class="sxs-lookup"><span data-stu-id="25e32-133">How to query for sentences that contain a specified set of words (LINQ) (C#)</span></span>](./how-to-query-for-sentences-that-contain-a-specified-set-of-words-linq.md)
