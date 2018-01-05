---
title: "Toplama sorguları"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 13ec5580-05ce-4a1f-9d3d-8660be7891a2
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 0f76178d6b10e8253fd135c35504389e03d8acae
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="aggregate-queries"></a><span data-ttu-id="3e4e8-102">Toplama sorguları</span><span class="sxs-lookup"><span data-stu-id="3e4e8-102">Aggregate Queries</span></span>
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="3e4e8-103">destekleyen `Average`, `Count`, `Max`, `Min`, ve `Sum` toplama işleçleri.</span><span class="sxs-lookup"><span data-stu-id="3e4e8-103"> supports the `Average`, `Count`, `Max`, `Min`, and `Sum` aggregate operators.</span></span> <span data-ttu-id="3e4e8-104">İçinde toplama işleçleri aşağıdaki özelliklere dikkat edin [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]:</span><span class="sxs-lookup"><span data-stu-id="3e4e8-104">Note the following characteristics of aggregate operators in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]:</span></span>  
  
-   <span data-ttu-id="3e4e8-105">Toplama sorguları hemen çalıştırılır.</span><span class="sxs-lookup"><span data-stu-id="3e4e8-105">Aggregate queries are executed immediately.</span></span>  
  
     <span data-ttu-id="3e4e8-106">Daha fazla bilgi için bkz: [LINQ sorgularını (C#) giriş](~/docs/csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md).</span><span class="sxs-lookup"><span data-stu-id="3e4e8-106">For more information, see [Introduction to LINQ Queries (C#)](~/docs/csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md).</span></span>  
  
-   <span data-ttu-id="3e4e8-107">Toplama sorguları genellikle bir koleksiyon yerine bir sayı döndürür.</span><span class="sxs-lookup"><span data-stu-id="3e4e8-107">Aggregate queries typically return a number instead of a collection.</span></span>  
  
     <span data-ttu-id="3e4e8-108">Daha fazla bilgi için bkz: [toplama işlemleri](http://msdn.microsoft.com/library/36d97c83-5de5-457d-971d-10a69365e7c4).</span><span class="sxs-lookup"><span data-stu-id="3e4e8-108">For more information, see [Aggregation Operations](http://msdn.microsoft.com/library/36d97c83-5de5-457d-971d-10a69365e7c4).</span></span>  
  
-   <span data-ttu-id="3e4e8-109">Anonim türler karşı toplamalar çağrılamaz.</span><span class="sxs-lookup"><span data-stu-id="3e4e8-109">You cannot call aggregates against anonymous types.</span></span>  
  
 <span data-ttu-id="3e4e8-110">Aşağıdaki konulardaki örnekleri Northwind örnek veritabanından alınabilir.</span><span class="sxs-lookup"><span data-stu-id="3e4e8-110">The examples in the following topics derive from the Northwind sample database.</span></span> <span data-ttu-id="3e4e8-111">Daha fazla bilgi için bkz: [örnek veritabanları yükleme](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md).</span><span class="sxs-lookup"><span data-stu-id="3e4e8-111">For more information, see [Downloading Sample Databases](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="3e4e8-112">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="3e4e8-112">In This Section</span></span>  
 [<span data-ttu-id="3e4e8-113">Sayısal Diziden Ortalama Değer Döndürme</span><span class="sxs-lookup"><span data-stu-id="3e4e8-113">Return the Average Value From a Numeric Sequence</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/return-the-average-value-from-a-numeric-sequence.md)  
 <span data-ttu-id="3e4e8-114">Nasıl kullanılacağı ortaya <xref:System.Linq.Enumerable.Average%2A> işleci.</span><span class="sxs-lookup"><span data-stu-id="3e4e8-114">Demonstrates how to use the <xref:System.Linq.Enumerable.Average%2A> operator.</span></span>  
  
 [<span data-ttu-id="3e4e8-115">Dizideki Öğe Sayısını Sayma</span><span class="sxs-lookup"><span data-stu-id="3e4e8-115">Count the Number of Elements in a Sequence</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/count-the-number-of-elements-in-a-sequence.md)  
 <span data-ttu-id="3e4e8-116">Nasıl kullanılacağı ortaya <xref:System.Linq.Enumerable.Count%2A> işleci.</span><span class="sxs-lookup"><span data-stu-id="3e4e8-116">Demonstrates how to use the <xref:System.Linq.Enumerable.Count%2A> operator.</span></span>  
  
 [<span data-ttu-id="3e4e8-117">Sayısal Dizideki En Büyük Değeri Bulma</span><span class="sxs-lookup"><span data-stu-id="3e4e8-117">Find the Maximum Value in a Numeric Sequence</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/find-the-maximum-value-in-a-numeric-sequence.md)  
 <span data-ttu-id="3e4e8-118">Nasıl kullanılacağı ortaya <xref:System.Linq.Enumerable.Max%2A> işleci.</span><span class="sxs-lookup"><span data-stu-id="3e4e8-118">Demonstrates how to use the <xref:System.Linq.Enumerable.Max%2A> operator.</span></span>  
  
 [<span data-ttu-id="3e4e8-119">Sayısal Dizideki En Küçük Değeri Bulma</span><span class="sxs-lookup"><span data-stu-id="3e4e8-119">Find the Minimum Value in a Numeric Sequence</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/find-the-minimum-value-in-a-numeric-sequence.md)  
 <span data-ttu-id="3e4e8-120">Nasıl kullanılacağı ortaya <xref:System.Linq.Enumerable.Min%2A> işleci.</span><span class="sxs-lookup"><span data-stu-id="3e4e8-120">Demonstrates how to use the <xref:System.Linq.Enumerable.Min%2A> operator.</span></span>  
  
 [<span data-ttu-id="3e4e8-121">Sayısal Dizideki Değerlerin Toplamını Hesaplama</span><span class="sxs-lookup"><span data-stu-id="3e4e8-121">Compute the Sum of Values in a Numeric Sequence</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/compute-the-sum-of-values-in-a-numeric-sequence.md)  
 <span data-ttu-id="3e4e8-122">Nasıl kullanılacağı ortaya <xref:System.Linq.Enumerable.Sum%2A> işleci.</span><span class="sxs-lookup"><span data-stu-id="3e4e8-122">Demonstrates how to use the <xref:System.Linq.Enumerable.Sum%2A> operator.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="3e4e8-123">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="3e4e8-123">Related Sections</span></span>  
 [<span data-ttu-id="3e4e8-124">Sorgu Örnekleri</span><span class="sxs-lookup"><span data-stu-id="3e4e8-124">Query Examples</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/query-examples.md)  
 <span data-ttu-id="3e4e8-125">Bağlantılar sağlar [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] Visual Basic ve C# sorgular.</span><span class="sxs-lookup"><span data-stu-id="3e4e8-125">Provides links to [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] queries in Visual Basic and C#.</span></span>  
  
 [<span data-ttu-id="3e4e8-126">Sorgu Kavramları</span><span class="sxs-lookup"><span data-stu-id="3e4e8-126">Query Concepts</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/query-concepts.md)  
 <span data-ttu-id="3e4e8-127">Tasarım kavramları açıklamak konulara bağlantılar sağlanır [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)] sorgular [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="3e4e8-127">Provides links to topics that explain concepts for designing [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)] queries in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span>  
  
 [<span data-ttu-id="3e4e8-128">Giriş LINQ sorgularını (C#)</span><span class="sxs-lookup"><span data-stu-id="3e4e8-128">Introduction to LINQ Queries (C#)</span></span>](~/docs/csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md)  
 <span data-ttu-id="3e4e8-129">Sorguları nasıl çalıştığı açıklanmaktadır [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="3e4e8-129">Explains how queries work in [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)].</span></span>
