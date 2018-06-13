---
title: Niceleyici işlemleri (C#)
ms.date: 07/20/2015
ms.assetid: 84ac2ac2-7a63-4581-bc4c-14e34be1493b
ms.openlocfilehash: dac5ca7349a45f5fc37cff0cb83bd6b2e1292568
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33339871"
---
# <a name="quantifier-operations-c"></a><span data-ttu-id="35b94-102">Niceleyici işlemleri (C#)</span><span class="sxs-lookup"><span data-stu-id="35b94-102">Quantifier Operations (C#)</span></span>
<span data-ttu-id="35b94-103">Niceleyici işlemleri dönüş bir <xref:System.Boolean> bazı veya tüm öğeleri bir sırada bir koşulu karşılıyor olup olmadığını belirten değer.</span><span class="sxs-lookup"><span data-stu-id="35b94-103">Quantifier operations return a <xref:System.Boolean> value that indicates whether some or all of the elements in a sequence satisfy a condition.</span></span>  
  
 <span data-ttu-id="35b94-104">Aşağıdaki çizimde, iki farklı kaynak sıraları üzerinde iki farklı niceleyici işlemleri gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="35b94-104">The following illustration depicts two different quantifier operations on two different source sequences.</span></span> <span data-ttu-id="35b94-105">İlk işlemi bir veya daha fazla öğe karakter 'A' olan ve sonucu olup olmadığını soran `true`.</span><span class="sxs-lookup"><span data-stu-id="35b94-105">The first operation asks if one or more of the elements are the character 'A', and the result is `true`.</span></span> <span data-ttu-id="35b94-106">İkinci bir işlem tüm öğeleri karakter 'A' olan ve sonucu olup olmadığını soran `true`.</span><span class="sxs-lookup"><span data-stu-id="35b94-106">The second operation asks if all the elements are the character 'A', and the result is `true`.</span></span>  
  
 <span data-ttu-id="35b94-107">![LINQ Niceleyici işlemleri](../../../../csharp/programming-guide/concepts/linq/media/linq_quantifier.png "LINQ_Quantifier")</span><span class="sxs-lookup"><span data-stu-id="35b94-107">![LINQ Quantifier Operations](../../../../csharp/programming-guide/concepts/linq/media/linq_quantifier.png "LINQ_Quantifier")</span></span>  
  
 <span data-ttu-id="35b94-108">Niceleyici işlemleri gerçekleştiren standart sorgu işleci yöntemleri aşağıdaki bölümde listelenmektedir.</span><span class="sxs-lookup"><span data-stu-id="35b94-108">The standard query operator methods that perform quantifier operations are listed in the following section.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="35b94-109">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="35b94-109">Methods</span></span>  
  
|<span data-ttu-id="35b94-110">Yöntem adı</span><span class="sxs-lookup"><span data-stu-id="35b94-110">Method Name</span></span>|<span data-ttu-id="35b94-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="35b94-111">Description</span></span>|<span data-ttu-id="35b94-112">C# sorgu ifade sözdizimi</span><span class="sxs-lookup"><span data-stu-id="35b94-112">C# Query Expression Syntax</span></span>|<span data-ttu-id="35b94-113">Daha fazla bilgi</span><span class="sxs-lookup"><span data-stu-id="35b94-113">More Information</span></span>|  
|-----------------|-----------------|---------------------------------|----------------------|  
|<span data-ttu-id="35b94-114">Tümü</span><span class="sxs-lookup"><span data-stu-id="35b94-114">All</span></span>|<span data-ttu-id="35b94-115">Bir dizi tüm öğeler bir koşulu karşılıyor olup olmadığını belirler.</span><span class="sxs-lookup"><span data-stu-id="35b94-115">Determines whether all the elements in a sequence satisfy a condition.</span></span>|<span data-ttu-id="35b94-116">Yok.</span><span class="sxs-lookup"><span data-stu-id="35b94-116">Not applicable.</span></span>|<xref:System.Linq.Enumerable.All%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.All%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="35b94-117">tüm</span><span class="sxs-lookup"><span data-stu-id="35b94-117">Any</span></span>|<span data-ttu-id="35b94-118">Bir dizisinde herhangi bir öğenin bir koşulu karşılıyor olup olmadığını belirler.</span><span class="sxs-lookup"><span data-stu-id="35b94-118">Determines whether any elements in a sequence satisfy a condition.</span></span>|<span data-ttu-id="35b94-119">Yok.</span><span class="sxs-lookup"><span data-stu-id="35b94-119">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Any%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Any%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="35b94-120">İçerir</span><span class="sxs-lookup"><span data-stu-id="35b94-120">Contains</span></span>|<span data-ttu-id="35b94-121">Bir dizi belirtilen öğeyi içerip içermediğini belirler.</span><span class="sxs-lookup"><span data-stu-id="35b94-121">Determines whether a sequence contains a specified element.</span></span>|<span data-ttu-id="35b94-122">Yok.</span><span class="sxs-lookup"><span data-stu-id="35b94-122">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Contains%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Contains%2A?displayProperty=nameWithType>|  
  
## <a name="see-also"></a><span data-ttu-id="35b94-123">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="35b94-123">See Also</span></span>  
 <xref:System.Linq>  
 [<span data-ttu-id="35b94-124">Standart sorgu işleçlerine genel bakış (C#)</span><span class="sxs-lookup"><span data-stu-id="35b94-124">Standard Query Operators Overview (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)  
 [<span data-ttu-id="35b94-125">Nasıl yapılır: çalışma zamanında koşul filtrelerini dinamik olarak belirtme</span><span class="sxs-lookup"><span data-stu-id="35b94-125">How to: Dynamically Specify Predicate Filters at Runtime</span></span>](../../../../csharp/programming-guide/linq-query-expressions/how-to-dynamically-specify-predicate-filters-at-runtime.md)  
 [<span data-ttu-id="35b94-126">Nasıl yapılır: sözcükleri (LINQ) (C#) belirtilen bir kümesini içeren cümleleri sorgulama</span><span class="sxs-lookup"><span data-stu-id="35b94-126">How to: Query for Sentences that Contain a Specified Set of Words (LINQ) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-query-for-sentences-that-contain-a-specified-set-of-words-linq.md)
