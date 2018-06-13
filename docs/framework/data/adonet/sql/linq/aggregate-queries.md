---
title: Toplama sorguları
ms.date: 03/30/2017
ms.assetid: 13ec5580-05ce-4a1f-9d3d-8660be7891a2
ms.openlocfilehash: e4d5e0a9dc1ffb0bf1857fee788d46947f3901d4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33358849"
---
# <a name="aggregate-queries"></a><span data-ttu-id="eb47d-102">Toplama sorguları</span><span class="sxs-lookup"><span data-stu-id="eb47d-102">Aggregate Queries</span></span>
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="eb47d-103"> destekleyen `Average`, `Count`, `Max`, `Min`, ve `Sum` toplama işleçleri.</span><span class="sxs-lookup"><span data-stu-id="eb47d-103"> supports the `Average`, `Count`, `Max`, `Min`, and `Sum` aggregate operators.</span></span> <span data-ttu-id="eb47d-104">İçinde toplama işleçleri aşağıdaki özelliklere dikkat edin [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]:</span><span class="sxs-lookup"><span data-stu-id="eb47d-104">Note the following characteristics of aggregate operators in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]:</span></span>  
  
-   <span data-ttu-id="eb47d-105">Toplama sorguları hemen çalıştırılır.</span><span class="sxs-lookup"><span data-stu-id="eb47d-105">Aggregate queries are executed immediately.</span></span>  
  
     <span data-ttu-id="eb47d-106">Daha fazla bilgi için bkz: [LINQ sorgularını (C#) giriş](~/docs/csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md).</span><span class="sxs-lookup"><span data-stu-id="eb47d-106">For more information, see [Introduction to LINQ Queries (C#)](~/docs/csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md).</span></span>  
  
-   <span data-ttu-id="eb47d-107">Toplama sorguları genellikle bir koleksiyon yerine bir sayı döndürür.</span><span class="sxs-lookup"><span data-stu-id="eb47d-107">Aggregate queries typically return a number instead of a collection.</span></span>  
  
     <span data-ttu-id="eb47d-108">Daha fazla bilgi için bkz: [toplama işlemleri](http://msdn.microsoft.com/library/36d97c83-5de5-457d-971d-10a69365e7c4).</span><span class="sxs-lookup"><span data-stu-id="eb47d-108">For more information, see [Aggregation Operations](http://msdn.microsoft.com/library/36d97c83-5de5-457d-971d-10a69365e7c4).</span></span>  
  
-   <span data-ttu-id="eb47d-109">Anonim türler karşı toplamalar çağrılamaz.</span><span class="sxs-lookup"><span data-stu-id="eb47d-109">You cannot call aggregates against anonymous types.</span></span>  
  
 <span data-ttu-id="eb47d-110">Aşağıdaki konulardaki örnekleri Northwind örnek veritabanından alınabilir.</span><span class="sxs-lookup"><span data-stu-id="eb47d-110">The examples in the following topics derive from the Northwind sample database.</span></span> <span data-ttu-id="eb47d-111">Daha fazla bilgi için bkz: [örnek veritabanları yükleme](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md).</span><span class="sxs-lookup"><span data-stu-id="eb47d-111">For more information, see [Downloading Sample Databases](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="eb47d-112">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="eb47d-112">In This Section</span></span>  
 [<span data-ttu-id="eb47d-113">Sayısal Diziden Ortalama Değer Döndürme</span><span class="sxs-lookup"><span data-stu-id="eb47d-113">Return the Average Value From a Numeric Sequence</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/return-the-average-value-from-a-numeric-sequence.md)  
 <span data-ttu-id="eb47d-114">Nasıl kullanılacağı ortaya <xref:System.Linq.Enumerable.Average%2A> işleci.</span><span class="sxs-lookup"><span data-stu-id="eb47d-114">Demonstrates how to use the <xref:System.Linq.Enumerable.Average%2A> operator.</span></span>  
  
 [<span data-ttu-id="eb47d-115">Dizideki Öğe Sayısını Sayma</span><span class="sxs-lookup"><span data-stu-id="eb47d-115">Count the Number of Elements in a Sequence</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/count-the-number-of-elements-in-a-sequence.md)  
 <span data-ttu-id="eb47d-116">Nasıl kullanılacağı ortaya <xref:System.Linq.Enumerable.Count%2A> işleci.</span><span class="sxs-lookup"><span data-stu-id="eb47d-116">Demonstrates how to use the <xref:System.Linq.Enumerable.Count%2A> operator.</span></span>  
  
 [<span data-ttu-id="eb47d-117">Sayısal Dizideki En Büyük Değeri Bulma</span><span class="sxs-lookup"><span data-stu-id="eb47d-117">Find the Maximum Value in a Numeric Sequence</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/find-the-maximum-value-in-a-numeric-sequence.md)  
 <span data-ttu-id="eb47d-118">Nasıl kullanılacağı ortaya <xref:System.Linq.Enumerable.Max%2A> işleci.</span><span class="sxs-lookup"><span data-stu-id="eb47d-118">Demonstrates how to use the <xref:System.Linq.Enumerable.Max%2A> operator.</span></span>  
  
 [<span data-ttu-id="eb47d-119">Sayısal Dizideki En Küçük Değeri Bulma</span><span class="sxs-lookup"><span data-stu-id="eb47d-119">Find the Minimum Value in a Numeric Sequence</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/find-the-minimum-value-in-a-numeric-sequence.md)  
 <span data-ttu-id="eb47d-120">Nasıl kullanılacağı ortaya <xref:System.Linq.Enumerable.Min%2A> işleci.</span><span class="sxs-lookup"><span data-stu-id="eb47d-120">Demonstrates how to use the <xref:System.Linq.Enumerable.Min%2A> operator.</span></span>  
  
 [<span data-ttu-id="eb47d-121">Sayısal Dizideki Değerlerin Toplamını Hesaplama</span><span class="sxs-lookup"><span data-stu-id="eb47d-121">Compute the Sum of Values in a Numeric Sequence</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/compute-the-sum-of-values-in-a-numeric-sequence.md)  
 <span data-ttu-id="eb47d-122">Nasıl kullanılacağı ortaya <xref:System.Linq.Enumerable.Sum%2A> işleci.</span><span class="sxs-lookup"><span data-stu-id="eb47d-122">Demonstrates how to use the <xref:System.Linq.Enumerable.Sum%2A> operator.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="eb47d-123">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="eb47d-123">Related Sections</span></span>  
 [<span data-ttu-id="eb47d-124">Sorgu Örnekleri</span><span class="sxs-lookup"><span data-stu-id="eb47d-124">Query Examples</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/query-examples.md)  
 <span data-ttu-id="eb47d-125">Bağlantılar sağlar [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] Visual Basic ve C# sorgular.</span><span class="sxs-lookup"><span data-stu-id="eb47d-125">Provides links to [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] queries in Visual Basic and C#.</span></span>  
  
 [<span data-ttu-id="eb47d-126">Sorgu Kavramları</span><span class="sxs-lookup"><span data-stu-id="eb47d-126">Query Concepts</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/query-concepts.md)  
 <span data-ttu-id="eb47d-127">Tasarım kavramları açıklamak konulara bağlantılar sağlanır [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)] sorgular [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="eb47d-127">Provides links to topics that explain concepts for designing [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)] queries in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span>  
  
 [<span data-ttu-id="eb47d-128">Giriş LINQ sorgularını (C#)</span><span class="sxs-lookup"><span data-stu-id="eb47d-128">Introduction to LINQ Queries (C#)</span></span>](~/docs/csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md)  
 <span data-ttu-id="eb47d-129">Sorguları nasıl çalıştığı açıklanmaktadır [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="eb47d-129">Explains how queries work in [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)].</span></span>
