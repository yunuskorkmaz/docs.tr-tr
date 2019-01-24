---
title: Niceleyici işlemleri (C#)
ms.date: 07/20/2015
ms.assetid: 84ac2ac2-7a63-4581-bc4c-14e34be1493b
ms.openlocfilehash: 22d7b86a5935c7721b7ab13eea1252231d6ac095
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54509226"
---
# <a name="quantifier-operations-c"></a><span data-ttu-id="a413e-102">Niceleyici işlemleri (C#)</span><span class="sxs-lookup"><span data-stu-id="a413e-102">Quantifier Operations (C#)</span></span>
<span data-ttu-id="a413e-103">Niceleyici işlemleri dönüş bir <xref:System.Boolean> bazılarını veya tümünü bir dizideki öğelerin bir koşulu karşılayan olup olmadığını gösteren değer.</span><span class="sxs-lookup"><span data-stu-id="a413e-103">Quantifier operations return a <xref:System.Boolean> value that indicates whether some or all of the elements in a sequence satisfy a condition.</span></span>  
  
 <span data-ttu-id="a413e-104">Aşağıdaki çizimde, iki farklı kaynak diziler üzerinde iki farklı niceleyici işlemleri gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="a413e-104">The following illustration depicts two different quantifier operations on two different source sequences.</span></span> <span data-ttu-id="a413e-105">İlk işlem bir veya daha fazla öğe olan karakter 'A' ve sonucu olup olmadığını soran `true`.</span><span class="sxs-lookup"><span data-stu-id="a413e-105">The first operation asks if one or more of the elements are the character 'A', and the result is `true`.</span></span> <span data-ttu-id="a413e-106">İkinci işlem tüm öğeleri karakter 'A' olan ve sonucu olup olmadığını soran `true`.</span><span class="sxs-lookup"><span data-stu-id="a413e-106">The second operation asks if all the elements are the character 'A', and the result is `true`.</span></span>  
  
 <span data-ttu-id="a413e-107">![LINQ Niceleyici işlemleri](../../../../csharp/programming-guide/concepts/linq/media/linq_quantifier.png "LINQ_Quantifier")</span><span class="sxs-lookup"><span data-stu-id="a413e-107">![LINQ Quantifier Operations](../../../../csharp/programming-guide/concepts/linq/media/linq_quantifier.png "LINQ_Quantifier")</span></span>  
  
 <span data-ttu-id="a413e-108">Niceleyici işlemleri gerçekleştiren standart sorgu işleci yöntemleri aşağıdaki bölümünde listelenir.</span><span class="sxs-lookup"><span data-stu-id="a413e-108">The standard query operator methods that perform quantifier operations are listed in the following section.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="a413e-109">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="a413e-109">Methods</span></span>  
  
|<span data-ttu-id="a413e-110">Yöntem adı</span><span class="sxs-lookup"><span data-stu-id="a413e-110">Method Name</span></span>|<span data-ttu-id="a413e-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a413e-111">Description</span></span>|<span data-ttu-id="a413e-112">C# sorgu ifade sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a413e-112">C# Query Expression Syntax</span></span>|<span data-ttu-id="a413e-113">Daha fazla bilgi</span><span class="sxs-lookup"><span data-stu-id="a413e-113">More Information</span></span>|  
|-----------------|-----------------|---------------------------------|----------------------|  
|<span data-ttu-id="a413e-114">Tümü</span><span class="sxs-lookup"><span data-stu-id="a413e-114">All</span></span>|<span data-ttu-id="a413e-115">Bir dizideki tüm öğeler bir koşulu karşılayan olup olmadığını belirler.</span><span class="sxs-lookup"><span data-stu-id="a413e-115">Determines whether all the elements in a sequence satisfy a condition.</span></span>|<span data-ttu-id="a413e-116">Uygulanamaz.</span><span class="sxs-lookup"><span data-stu-id="a413e-116">Not applicable.</span></span>|<xref:System.Linq.Enumerable.All%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.All%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="a413e-117">Tüm</span><span class="sxs-lookup"><span data-stu-id="a413e-117">Any</span></span>|<span data-ttu-id="a413e-118">Bir dizideki herhangi bir öğe bir koşulu karşılayan olup olmadığını belirler.</span><span class="sxs-lookup"><span data-stu-id="a413e-118">Determines whether any elements in a sequence satisfy a condition.</span></span>|<span data-ttu-id="a413e-119">Uygulanamaz.</span><span class="sxs-lookup"><span data-stu-id="a413e-119">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Any%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Any%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="a413e-120">İçerir</span><span class="sxs-lookup"><span data-stu-id="a413e-120">Contains</span></span>|<span data-ttu-id="a413e-121">Bir dizi belirtilen öğeyi içerip içermediğini belirler.</span><span class="sxs-lookup"><span data-stu-id="a413e-121">Determines whether a sequence contains a specified element.</span></span>|<span data-ttu-id="a413e-122">Uygulanamaz.</span><span class="sxs-lookup"><span data-stu-id="a413e-122">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Contains%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Contains%2A?displayProperty=nameWithType>|  
  
## <a name="see-also"></a><span data-ttu-id="a413e-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a413e-123">See also</span></span>

- <xref:System.Linq>
- [<span data-ttu-id="a413e-124">Standart sorgu işleçlerine genel bakış (C#)</span><span class="sxs-lookup"><span data-stu-id="a413e-124">Standard Query Operators Overview (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [<span data-ttu-id="a413e-125">Nasıl yapılır: Çalışma zamanında koşul filtrelerini dinamik olarak belirtme</span><span class="sxs-lookup"><span data-stu-id="a413e-125">How to: Dynamically Specify Predicate Filters at Runtime</span></span>](../../../../csharp/programming-guide/linq-query-expressions/how-to-dynamically-specify-predicate-filters-at-runtime.md)
- [<span data-ttu-id="a413e-126">Nasıl yapılır: Belirli bir sözcükler (LINQ) kümesini içeren cümleleri sorgulama (C#)</span><span class="sxs-lookup"><span data-stu-id="a413e-126">How to: Query for Sentences that Contain a Specified Set of Words (LINQ) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-query-for-sentences-that-contain-a-specified-set-of-words-linq.md)
