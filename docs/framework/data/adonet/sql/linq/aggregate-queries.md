---
title: Toplu Sorgular
ms.date: 03/30/2017
ms.assetid: 13ec5580-05ce-4a1f-9d3d-8660be7891a2
ms.openlocfilehash: 8dfe24a84c707b6d21afb7ccfc57ac7b0423942f
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91161548"
---
# <a name="aggregate-queries"></a><span data-ttu-id="0c37e-102">Toplu Sorgular</span><span class="sxs-lookup"><span data-stu-id="0c37e-102">Aggregate Queries</span></span>

[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="0c37e-103">,, `Average` , `Count` `Max` `Min` ve `Sum` toplama işleçlerini destekler.</span><span class="sxs-lookup"><span data-stu-id="0c37e-103">supports the `Average`, `Count`, `Max`, `Min`, and `Sum` aggregate operators.</span></span> <span data-ttu-id="0c37e-104">İçindeki toplama işleçleri aşağıdaki özelliklerine göz önünde edin [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] :</span><span class="sxs-lookup"><span data-stu-id="0c37e-104">Note the following characteristics of aggregate operators in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]:</span></span>  
  
- <span data-ttu-id="0c37e-105">Toplama sorguları hemen yürütülür.</span><span class="sxs-lookup"><span data-stu-id="0c37e-105">Aggregate queries are executed immediately.</span></span>  
  
     <span data-ttu-id="0c37e-106">Daha fazla bilgi için bkz. [LINQ Sorgularına Giriş (C#)](../../../../../csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md).</span><span class="sxs-lookup"><span data-stu-id="0c37e-106">For more information, see [Introduction to LINQ Queries (C#)](../../../../../csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md).</span></span>  
  
- <span data-ttu-id="0c37e-107">Toplama sorguları genellikle bir koleksiyon yerine bir sayı döndürür.</span><span class="sxs-lookup"><span data-stu-id="0c37e-107">Aggregate queries typically return a number instead of a collection.</span></span>  
  
     <span data-ttu-id="0c37e-108">Daha fazla bilgi için bkz. [toplama işlemleri](/previous-versions/visualstudio/visual-studio-2013/bb546138(v=vs.120)).</span><span class="sxs-lookup"><span data-stu-id="0c37e-108">For more information, see [Aggregation Operations](/previous-versions/visualstudio/visual-studio-2013/bb546138(v=vs.120)).</span></span>  
  
- <span data-ttu-id="0c37e-109">Anonim türlere karşı toplamalar çağrılamaz.</span><span class="sxs-lookup"><span data-stu-id="0c37e-109">You cannot call aggregates against anonymous types.</span></span>  
  
 <span data-ttu-id="0c37e-110">Aşağıdaki konulardaki örnekler Northwind örnek veritabanından türetilir.</span><span class="sxs-lookup"><span data-stu-id="0c37e-110">The examples in the following topics derive from the Northwind sample database.</span></span> <span data-ttu-id="0c37e-111">Daha fazla bilgi için bkz. [örnek veritabanlarını indirme](downloading-sample-databases.md).</span><span class="sxs-lookup"><span data-stu-id="0c37e-111">For more information, see [Downloading Sample Databases](downloading-sample-databases.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="0c37e-112">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="0c37e-112">In This Section</span></span>  

 [<span data-ttu-id="0c37e-113">Sayısal Diziden Ortalama Değer Döndürme</span><span class="sxs-lookup"><span data-stu-id="0c37e-113">Return the Average Value From a Numeric Sequence</span></span>](return-the-average-value-from-a-numeric-sequence.md)  
 <span data-ttu-id="0c37e-114">İşlecinin nasıl kullanılacağını gösterir <xref:System.Linq.Enumerable.Average%2A> .</span><span class="sxs-lookup"><span data-stu-id="0c37e-114">Demonstrates how to use the <xref:System.Linq.Enumerable.Average%2A> operator.</span></span>  
  
 [<span data-ttu-id="0c37e-115">Dizideki Öğe Sayısını Sayma</span><span class="sxs-lookup"><span data-stu-id="0c37e-115">Count the Number of Elements in a Sequence</span></span>](count-the-number-of-elements-in-a-sequence.md)  
 <span data-ttu-id="0c37e-116">İşlecinin nasıl kullanılacağını gösterir <xref:System.Linq.Enumerable.Count%2A> .</span><span class="sxs-lookup"><span data-stu-id="0c37e-116">Demonstrates how to use the <xref:System.Linq.Enumerable.Count%2A> operator.</span></span>  
  
 [<span data-ttu-id="0c37e-117">Sayısal Dizideki En Büyük Değeri Bulma</span><span class="sxs-lookup"><span data-stu-id="0c37e-117">Find the Maximum Value in a Numeric Sequence</span></span>](find-the-maximum-value-in-a-numeric-sequence.md)  
 <span data-ttu-id="0c37e-118">İşlecinin nasıl kullanılacağını gösterir <xref:System.Linq.Enumerable.Max%2A> .</span><span class="sxs-lookup"><span data-stu-id="0c37e-118">Demonstrates how to use the <xref:System.Linq.Enumerable.Max%2A> operator.</span></span>  
  
 [<span data-ttu-id="0c37e-119">Sayısal Dizideki En Küçük Değeri Bulma</span><span class="sxs-lookup"><span data-stu-id="0c37e-119">Find the Minimum Value in a Numeric Sequence</span></span>](find-the-minimum-value-in-a-numeric-sequence.md)  
 <span data-ttu-id="0c37e-120">İşlecinin nasıl kullanılacağını gösterir <xref:System.Linq.Enumerable.Min%2A> .</span><span class="sxs-lookup"><span data-stu-id="0c37e-120">Demonstrates how to use the <xref:System.Linq.Enumerable.Min%2A> operator.</span></span>  
  
 [<span data-ttu-id="0c37e-121">Sayısal Dizideki Değerlerin Toplamını Hesaplama</span><span class="sxs-lookup"><span data-stu-id="0c37e-121">Compute the Sum of Values in a Numeric Sequence</span></span>](compute-the-sum-of-values-in-a-numeric-sequence.md)  
 <span data-ttu-id="0c37e-122">İşlecinin nasıl kullanılacağını gösterir <xref:System.Linq.Enumerable.Sum%2A> .</span><span class="sxs-lookup"><span data-stu-id="0c37e-122">Demonstrates how to use the <xref:System.Linq.Enumerable.Sum%2A> operator.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="0c37e-123">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="0c37e-123">Related Sections</span></span>  

 [<span data-ttu-id="0c37e-124">Sorgu örnekleri</span><span class="sxs-lookup"><span data-stu-id="0c37e-124">Query Examples</span></span>](query-examples.md)  
 <span data-ttu-id="0c37e-125">[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]Visual Basic ve C# ' deki sorgulara bağlantılar sağlar.</span><span class="sxs-lookup"><span data-stu-id="0c37e-125">Provides links to [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] queries in Visual Basic and C#.</span></span>  
  
 [<span data-ttu-id="0c37e-126">Sorgu Kavramları</span><span class="sxs-lookup"><span data-stu-id="0c37e-126">Query Concepts</span></span>](query-concepts.md)  
 <span data-ttu-id="0c37e-127">İçinde LINQ sorguları tasarlamak için kavramları açıklayan konulara bağlantılar sağlar [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="0c37e-127">Provides links to topics that explain concepts for designing LINQ queries in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span>  
  
 [<span data-ttu-id="0c37e-128">LINQ Sorgularına Giriş (C#)</span><span class="sxs-lookup"><span data-stu-id="0c37e-128">Introduction to LINQ Queries (C#)</span></span>](../../../../../csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md)  
 <span data-ttu-id="0c37e-129">Sorguların LINQ 'te nasıl çalıştığını açıklar.</span><span class="sxs-lookup"><span data-stu-id="0c37e-129">Explains how queries work in LINQ.</span></span>
