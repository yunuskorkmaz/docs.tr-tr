---
title: Toplu Sorgular
ms.date: 03/30/2017
ms.assetid: 13ec5580-05ce-4a1f-9d3d-8660be7891a2
ms.openlocfilehash: 8defefb39974bea150fed84b0e7404b43882c41c
ms.sourcegitcommit: 7bc6887ab658550baa78f1520ea735838249345e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/03/2020
ms.locfileid: "75634748"
---
# <a name="aggregate-queries"></a><span data-ttu-id="1544b-102">Toplu Sorgular</span><span class="sxs-lookup"><span data-stu-id="1544b-102">Aggregate Queries</span></span>
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="1544b-103">, `Average`, `Count`, `Max`, `Min`ve `Sum` toplama işleçlerini destekler.</span><span class="sxs-lookup"><span data-stu-id="1544b-103">supports the `Average`, `Count`, `Max`, `Min`, and `Sum` aggregate operators.</span></span> <span data-ttu-id="1544b-104">[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]içindeki toplama işleçleri 'nin aşağıdaki özelliklerine göz önünde edin:</span><span class="sxs-lookup"><span data-stu-id="1544b-104">Note the following characteristics of aggregate operators in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]:</span></span>  
  
- <span data-ttu-id="1544b-105">Toplama sorguları hemen yürütülür.</span><span class="sxs-lookup"><span data-stu-id="1544b-105">Aggregate queries are executed immediately.</span></span>  
  
     <span data-ttu-id="1544b-106">Daha fazla bilgi için bkz. [LINQ Sorgularına Giriş (C#)](../../../../../csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md).</span><span class="sxs-lookup"><span data-stu-id="1544b-106">For more information, see [Introduction to LINQ Queries (C#)](../../../../../csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md).</span></span>  
  
- <span data-ttu-id="1544b-107">Toplama sorguları genellikle bir koleksiyon yerine bir sayı döndürür.</span><span class="sxs-lookup"><span data-stu-id="1544b-107">Aggregate queries typically return a number instead of a collection.</span></span>  
  
     <span data-ttu-id="1544b-108">Daha fazla bilgi için bkz. [toplama işlemleri](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/bb546138(v=vs.120)).</span><span class="sxs-lookup"><span data-stu-id="1544b-108">For more information, see [Aggregation Operations](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/bb546138(v=vs.120)).</span></span>  
  
- <span data-ttu-id="1544b-109">Anonim türlere karşı toplamalar çağrılamaz.</span><span class="sxs-lookup"><span data-stu-id="1544b-109">You cannot call aggregates against anonymous types.</span></span>  
  
 <span data-ttu-id="1544b-110">Aşağıdaki konulardaki örnekler Northwind örnek veritabanından türetilir.</span><span class="sxs-lookup"><span data-stu-id="1544b-110">The examples in the following topics derive from the Northwind sample database.</span></span> <span data-ttu-id="1544b-111">Daha fazla bilgi için bkz. [örnek veritabanlarını indirme](downloading-sample-databases.md).</span><span class="sxs-lookup"><span data-stu-id="1544b-111">For more information, see [Downloading Sample Databases](downloading-sample-databases.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="1544b-112">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="1544b-112">In This Section</span></span>  
 [<span data-ttu-id="1544b-113">Sayısal Diziden Ortalama Değer Döndürme</span><span class="sxs-lookup"><span data-stu-id="1544b-113">Return the Average Value From a Numeric Sequence</span></span>](return-the-average-value-from-a-numeric-sequence.md)  
 <span data-ttu-id="1544b-114"><xref:System.Linq.Enumerable.Average%2A> işlecinin nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="1544b-114">Demonstrates how to use the <xref:System.Linq.Enumerable.Average%2A> operator.</span></span>  
  
 [<span data-ttu-id="1544b-115">Dizideki Öğe Sayısını Sayma</span><span class="sxs-lookup"><span data-stu-id="1544b-115">Count the Number of Elements in a Sequence</span></span>](count-the-number-of-elements-in-a-sequence.md)  
 <span data-ttu-id="1544b-116"><xref:System.Linq.Enumerable.Count%2A> işlecinin nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="1544b-116">Demonstrates how to use the <xref:System.Linq.Enumerable.Count%2A> operator.</span></span>  
  
 [<span data-ttu-id="1544b-117">Sayısal Dizideki En Büyük Değeri Bulma</span><span class="sxs-lookup"><span data-stu-id="1544b-117">Find the Maximum Value in a Numeric Sequence</span></span>](find-the-maximum-value-in-a-numeric-sequence.md)  
 <span data-ttu-id="1544b-118"><xref:System.Linq.Enumerable.Max%2A> işlecinin nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="1544b-118">Demonstrates how to use the <xref:System.Linq.Enumerable.Max%2A> operator.</span></span>  
  
 [<span data-ttu-id="1544b-119">Sayısal Dizideki En Küçük Değeri Bulma</span><span class="sxs-lookup"><span data-stu-id="1544b-119">Find the Minimum Value in a Numeric Sequence</span></span>](find-the-minimum-value-in-a-numeric-sequence.md)  
 <span data-ttu-id="1544b-120"><xref:System.Linq.Enumerable.Min%2A> işlecinin nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="1544b-120">Demonstrates how to use the <xref:System.Linq.Enumerable.Min%2A> operator.</span></span>  
  
 [<span data-ttu-id="1544b-121">Sayısal Dizideki Değerlerin Toplamını Hesaplama</span><span class="sxs-lookup"><span data-stu-id="1544b-121">Compute the Sum of Values in a Numeric Sequence</span></span>](compute-the-sum-of-values-in-a-numeric-sequence.md)  
 <span data-ttu-id="1544b-122"><xref:System.Linq.Enumerable.Sum%2A> işlecinin nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="1544b-122">Demonstrates how to use the <xref:System.Linq.Enumerable.Sum%2A> operator.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="1544b-123">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="1544b-123">Related Sections</span></span>  
 [<span data-ttu-id="1544b-124">Sorgu Örnekleri</span><span class="sxs-lookup"><span data-stu-id="1544b-124">Query Examples</span></span>](query-examples.md)  
 <span data-ttu-id="1544b-125">Visual Basic ve C#' de [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] sorgularına bağlantılar sağlar.</span><span class="sxs-lookup"><span data-stu-id="1544b-125">Provides links to [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] queries in Visual Basic and C#.</span></span>  
  
 [<span data-ttu-id="1544b-126">Sorgu Kavramları</span><span class="sxs-lookup"><span data-stu-id="1544b-126">Query Concepts</span></span>](query-concepts.md)  
 <span data-ttu-id="1544b-127">[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]' de LINQ sorguları tasarlamak için kavramları açıklayan konuların bağlantılarını sağlar.</span><span class="sxs-lookup"><span data-stu-id="1544b-127">Provides links to topics that explain concepts for designing LINQ queries in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span>  
  
 [<span data-ttu-id="1544b-128">LINQ Sorgularına Giriş (C#)</span><span class="sxs-lookup"><span data-stu-id="1544b-128">Introduction to LINQ Queries (C#)</span></span>](../../../../../csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md)  
 <span data-ttu-id="1544b-129">Sorguların LINQ 'te nasıl çalıştığını açıklar.</span><span class="sxs-lookup"><span data-stu-id="1544b-129">Explains how queries work in LINQ.</span></span>
