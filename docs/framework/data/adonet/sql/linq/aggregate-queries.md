---
title: Toplu sorgular
ms.date: 03/30/2017
ms.assetid: 13ec5580-05ce-4a1f-9d3d-8660be7891a2
ms.openlocfilehash: 1c8f6191cfb832a71bd32c60db492eafb8ca22ca
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2018
ms.locfileid: "43464159"
---
# <a name="aggregate-queries"></a><span data-ttu-id="11115-102">Toplu sorgular</span><span class="sxs-lookup"><span data-stu-id="11115-102">Aggregate Queries</span></span>
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="11115-103"> destekleyen `Average`, `Count`, `Max`, `Min`, ve `Sum` toplama işleçleri.</span><span class="sxs-lookup"><span data-stu-id="11115-103"> supports the `Average`, `Count`, `Max`, `Min`, and `Sum` aggregate operators.</span></span> <span data-ttu-id="11115-104">Toplama işleçleri aşağıdaki özellikleri Not [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]:</span><span class="sxs-lookup"><span data-stu-id="11115-104">Note the following characteristics of aggregate operators in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]:</span></span>  
  
-   <span data-ttu-id="11115-105">Toplam değer sorguları hemen çalıştırılır.</span><span class="sxs-lookup"><span data-stu-id="11115-105">Aggregate queries are executed immediately.</span></span>  
  
     <span data-ttu-id="11115-106">Daha fazla bilgi için [(C#) LINQ sorgularına giriş](~/docs/csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md).</span><span class="sxs-lookup"><span data-stu-id="11115-106">For more information, see [Introduction to LINQ Queries (C#)](~/docs/csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md).</span></span>  
  
-   <span data-ttu-id="11115-107">Toplam değer sorguları genellikle bir koleksiyon yerine bir sayı döndürür.</span><span class="sxs-lookup"><span data-stu-id="11115-107">Aggregate queries typically return a number instead of a collection.</span></span>  
  
     <span data-ttu-id="11115-108">Daha fazla bilgi için [toplama işlemleri](https://msdn.microsoft.com/library/36d97c83-5de5-457d-971d-10a69365e7c4).</span><span class="sxs-lookup"><span data-stu-id="11115-108">For more information, see [Aggregation Operations](https://msdn.microsoft.com/library/36d97c83-5de5-457d-971d-10a69365e7c4).</span></span>  
  
-   <span data-ttu-id="11115-109">Anonim türler karşı toplamalar çağrılamıyor.</span><span class="sxs-lookup"><span data-stu-id="11115-109">You cannot call aggregates against anonymous types.</span></span>  
  
 <span data-ttu-id="11115-110">Aşağıdaki konulardaki örnekleri, Northwind örnek veritabanından türetilir.</span><span class="sxs-lookup"><span data-stu-id="11115-110">The examples in the following topics derive from the Northwind sample database.</span></span> <span data-ttu-id="11115-111">Daha fazla bilgi için [Downloading Sample Databases](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md).</span><span class="sxs-lookup"><span data-stu-id="11115-111">For more information, see [Downloading Sample Databases](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="11115-112">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="11115-112">In This Section</span></span>  
 [<span data-ttu-id="11115-113">Sayısal Diziden Ortalama Değer Döndürme</span><span class="sxs-lookup"><span data-stu-id="11115-113">Return the Average Value From a Numeric Sequence</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/return-the-average-value-from-a-numeric-sequence.md)  
 <span data-ttu-id="11115-114">Nasıl kullanılacağını gösteren <xref:System.Linq.Enumerable.Average%2A> işleci.</span><span class="sxs-lookup"><span data-stu-id="11115-114">Demonstrates how to use the <xref:System.Linq.Enumerable.Average%2A> operator.</span></span>  
  
 [<span data-ttu-id="11115-115">Dizideki Öğe Sayısını Sayma</span><span class="sxs-lookup"><span data-stu-id="11115-115">Count the Number of Elements in a Sequence</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/count-the-number-of-elements-in-a-sequence.md)  
 <span data-ttu-id="11115-116">Nasıl kullanılacağını gösteren <xref:System.Linq.Enumerable.Count%2A> işleci.</span><span class="sxs-lookup"><span data-stu-id="11115-116">Demonstrates how to use the <xref:System.Linq.Enumerable.Count%2A> operator.</span></span>  
  
 [<span data-ttu-id="11115-117">Sayısal Dizideki En Büyük Değeri Bulma</span><span class="sxs-lookup"><span data-stu-id="11115-117">Find the Maximum Value in a Numeric Sequence</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/find-the-maximum-value-in-a-numeric-sequence.md)  
 <span data-ttu-id="11115-118">Nasıl kullanılacağını gösteren <xref:System.Linq.Enumerable.Max%2A> işleci.</span><span class="sxs-lookup"><span data-stu-id="11115-118">Demonstrates how to use the <xref:System.Linq.Enumerable.Max%2A> operator.</span></span>  
  
 [<span data-ttu-id="11115-119">Sayısal Dizideki En Küçük Değeri Bulma</span><span class="sxs-lookup"><span data-stu-id="11115-119">Find the Minimum Value in a Numeric Sequence</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/find-the-minimum-value-in-a-numeric-sequence.md)  
 <span data-ttu-id="11115-120">Nasıl kullanılacağını gösteren <xref:System.Linq.Enumerable.Min%2A> işleci.</span><span class="sxs-lookup"><span data-stu-id="11115-120">Demonstrates how to use the <xref:System.Linq.Enumerable.Min%2A> operator.</span></span>  
  
 [<span data-ttu-id="11115-121">Sayısal Dizideki Değerlerin Toplamını Hesaplama</span><span class="sxs-lookup"><span data-stu-id="11115-121">Compute the Sum of Values in a Numeric Sequence</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/compute-the-sum-of-values-in-a-numeric-sequence.md)  
 <span data-ttu-id="11115-122">Nasıl kullanılacağını gösteren <xref:System.Linq.Enumerable.Sum%2A> işleci.</span><span class="sxs-lookup"><span data-stu-id="11115-122">Demonstrates how to use the <xref:System.Linq.Enumerable.Sum%2A> operator.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="11115-123">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="11115-123">Related Sections</span></span>  
 [<span data-ttu-id="11115-124">Sorgu Örnekleri</span><span class="sxs-lookup"><span data-stu-id="11115-124">Query Examples</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/query-examples.md)  
 <span data-ttu-id="11115-125">Bağlantılar sağlar [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] Visual Basic ve C# sorgular.</span><span class="sxs-lookup"><span data-stu-id="11115-125">Provides links to [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] queries in Visual Basic and C#.</span></span>  
  
 [<span data-ttu-id="11115-126">Sorgu Kavramları</span><span class="sxs-lookup"><span data-stu-id="11115-126">Query Concepts</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/query-concepts.md)  
 <span data-ttu-id="11115-127">Tasarım kavramları açıklayan konulara bağlantılar sağlar [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)] sorgulara [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="11115-127">Provides links to topics that explain concepts for designing [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)] queries in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span>  
  
 [<span data-ttu-id="11115-128">LINQ sorguları (C#) giriş</span><span class="sxs-lookup"><span data-stu-id="11115-128">Introduction to LINQ Queries (C#)</span></span>](~/docs/csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md)  
 <span data-ttu-id="11115-129">Sorguları nasıl çalıştığı açıklanır [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="11115-129">Explains how queries work in [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)].</span></span>
