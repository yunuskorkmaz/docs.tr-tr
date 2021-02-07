---
description: 'Daha fazla bilgi edinin: toplama sorguları'
title: Toplu Sorgular
ms.date: 03/30/2017
ms.assetid: 13ec5580-05ce-4a1f-9d3d-8660be7891a2
ms.openlocfilehash: 2b9b71440c804740e2f04d5b2dc8c2cd111634b7
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99712837"
---
# <a name="aggregate-queries"></a><span data-ttu-id="ca88b-103">Toplu Sorgular</span><span class="sxs-lookup"><span data-stu-id="ca88b-103">Aggregate Queries</span></span>

[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="ca88b-104">,, `Average` , `Count` `Max` `Min` ve `Sum` toplama işleçlerini destekler.</span><span class="sxs-lookup"><span data-stu-id="ca88b-104">supports the `Average`, `Count`, `Max`, `Min`, and `Sum` aggregate operators.</span></span> <span data-ttu-id="ca88b-105">İçindeki toplama işleçleri aşağıdaki özelliklerine göz önünde edin [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] :</span><span class="sxs-lookup"><span data-stu-id="ca88b-105">Note the following characteristics of aggregate operators in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]:</span></span>  
  
- <span data-ttu-id="ca88b-106">Toplama sorguları hemen yürütülür.</span><span class="sxs-lookup"><span data-stu-id="ca88b-106">Aggregate queries are executed immediately.</span></span>  
  
     <span data-ttu-id="ca88b-107">Daha fazla bilgi için bkz. [LINQ Sorgularına Giriş (C#)](../../../../../csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md).</span><span class="sxs-lookup"><span data-stu-id="ca88b-107">For more information, see [Introduction to LINQ Queries (C#)](../../../../../csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md).</span></span>  
  
- <span data-ttu-id="ca88b-108">Toplama sorguları genellikle bir koleksiyon yerine bir sayı döndürür.</span><span class="sxs-lookup"><span data-stu-id="ca88b-108">Aggregate queries typically return a number instead of a collection.</span></span>  
  
     <span data-ttu-id="ca88b-109">Daha fazla bilgi için bkz. [toplama işlemleri](/previous-versions/visualstudio/visual-studio-2013/bb546138(v=vs.120)).</span><span class="sxs-lookup"><span data-stu-id="ca88b-109">For more information, see [Aggregation Operations](/previous-versions/visualstudio/visual-studio-2013/bb546138(v=vs.120)).</span></span>  
  
- <span data-ttu-id="ca88b-110">Anonim türlere karşı toplamalar çağrılamaz.</span><span class="sxs-lookup"><span data-stu-id="ca88b-110">You cannot call aggregates against anonymous types.</span></span>  
  
 <span data-ttu-id="ca88b-111">Aşağıdaki konulardaki örnekler Northwind örnek veritabanından türetilir.</span><span class="sxs-lookup"><span data-stu-id="ca88b-111">The examples in the following topics derive from the Northwind sample database.</span></span> <span data-ttu-id="ca88b-112">Daha fazla bilgi için bkz. [örnek veritabanlarını indirme](downloading-sample-databases.md).</span><span class="sxs-lookup"><span data-stu-id="ca88b-112">For more information, see [Downloading Sample Databases](downloading-sample-databases.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="ca88b-113">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="ca88b-113">In This Section</span></span>  

 [<span data-ttu-id="ca88b-114">Sayısal Diziden Ortalama Değer Döndürme</span><span class="sxs-lookup"><span data-stu-id="ca88b-114">Return the Average Value From a Numeric Sequence</span></span>](return-the-average-value-from-a-numeric-sequence.md)  
 <span data-ttu-id="ca88b-115">İşlecinin nasıl kullanılacağını gösterir <xref:System.Linq.Enumerable.Average%2A> .</span><span class="sxs-lookup"><span data-stu-id="ca88b-115">Demonstrates how to use the <xref:System.Linq.Enumerable.Average%2A> operator.</span></span>  
  
 [<span data-ttu-id="ca88b-116">Dizideki Öğe Sayısını Sayma</span><span class="sxs-lookup"><span data-stu-id="ca88b-116">Count the Number of Elements in a Sequence</span></span>](count-the-number-of-elements-in-a-sequence.md)  
 <span data-ttu-id="ca88b-117">İşlecinin nasıl kullanılacağını gösterir <xref:System.Linq.Enumerable.Count%2A> .</span><span class="sxs-lookup"><span data-stu-id="ca88b-117">Demonstrates how to use the <xref:System.Linq.Enumerable.Count%2A> operator.</span></span>  
  
 [<span data-ttu-id="ca88b-118">Sayısal Dizideki En Büyük Değeri Bulma</span><span class="sxs-lookup"><span data-stu-id="ca88b-118">Find the Maximum Value in a Numeric Sequence</span></span>](find-the-maximum-value-in-a-numeric-sequence.md)  
 <span data-ttu-id="ca88b-119">İşlecinin nasıl kullanılacağını gösterir <xref:System.Linq.Enumerable.Max%2A> .</span><span class="sxs-lookup"><span data-stu-id="ca88b-119">Demonstrates how to use the <xref:System.Linq.Enumerable.Max%2A> operator.</span></span>  
  
 [<span data-ttu-id="ca88b-120">Sayısal Dizideki En Küçük Değeri Bulma</span><span class="sxs-lookup"><span data-stu-id="ca88b-120">Find the Minimum Value in a Numeric Sequence</span></span>](find-the-minimum-value-in-a-numeric-sequence.md)  
 <span data-ttu-id="ca88b-121">İşlecinin nasıl kullanılacağını gösterir <xref:System.Linq.Enumerable.Min%2A> .</span><span class="sxs-lookup"><span data-stu-id="ca88b-121">Demonstrates how to use the <xref:System.Linq.Enumerable.Min%2A> operator.</span></span>  
  
 [<span data-ttu-id="ca88b-122">Sayısal Dizideki Değerlerin Toplamını Hesaplama</span><span class="sxs-lookup"><span data-stu-id="ca88b-122">Compute the Sum of Values in a Numeric Sequence</span></span>](compute-the-sum-of-values-in-a-numeric-sequence.md)  
 <span data-ttu-id="ca88b-123">İşlecinin nasıl kullanılacağını gösterir <xref:System.Linq.Enumerable.Sum%2A> .</span><span class="sxs-lookup"><span data-stu-id="ca88b-123">Demonstrates how to use the <xref:System.Linq.Enumerable.Sum%2A> operator.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="ca88b-124">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="ca88b-124">Related Sections</span></span>  

 [<span data-ttu-id="ca88b-125">Sorgu örnekleri</span><span class="sxs-lookup"><span data-stu-id="ca88b-125">Query Examples</span></span>](query-examples.md)  
 <span data-ttu-id="ca88b-126">[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]Visual Basic ve C# ' deki sorgulara bağlantılar sağlar.</span><span class="sxs-lookup"><span data-stu-id="ca88b-126">Provides links to [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] queries in Visual Basic and C#.</span></span>  
  
 [<span data-ttu-id="ca88b-127">Sorgu Kavramları</span><span class="sxs-lookup"><span data-stu-id="ca88b-127">Query Concepts</span></span>](query-concepts.md)  
 <span data-ttu-id="ca88b-128">İçinde LINQ sorguları tasarlamak için kavramları açıklayan konulara bağlantılar sağlar [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="ca88b-128">Provides links to topics that explain concepts for designing LINQ queries in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span>  
  
 [<span data-ttu-id="ca88b-129">LINQ Sorgularına Giriş (C#)</span><span class="sxs-lookup"><span data-stu-id="ca88b-129">Introduction to LINQ Queries (C#)</span></span>](../../../../../csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md)  
 <span data-ttu-id="ca88b-130">Sorguların LINQ 'te nasıl çalıştığını açıklar.</span><span class="sxs-lookup"><span data-stu-id="ca88b-130">Explains how queries work in LINQ.</span></span>
