---
title: Sorgu örnekleri
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-ado
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 137f8677-494c-4d49-95ce-c17742f2d01f
caps.latest.revision: 2
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload:
- dotnet
ms.openlocfilehash: 5b1681f609d8715167defcb1df57cc270b61e53a
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/26/2018
---
# <a name="query-examples"></a><span data-ttu-id="69011-102">Sorgu örnekleri</span><span class="sxs-lookup"><span data-stu-id="69011-102">Query Examples</span></span>
<span data-ttu-id="69011-103">Bu bölümde Visual Basic ve C# örnekleri tipik [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] sorgular.</span><span class="sxs-lookup"><span data-stu-id="69011-103">This section provides Visual Basic and C# examples of typical [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] queries.</span></span> <span data-ttu-id="69011-104">Geliştiriciler Visual Studio kullanarak, pek çok daha fazla örnek örnek bir çözüm içinde kullanılabilir örnekleri bölümünde bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="69011-104">Developers using Visual Studio can find many more examples in a sample solution available in the Samples section.</span></span> <span data-ttu-id="69011-105">Daha fazla bilgi için bkz: [örnekleri](../../../../../../docs/framework/data/adonet/sql/linq/samples.md).</span><span class="sxs-lookup"><span data-stu-id="69011-105">For more information, see [Samples](../../../../../../docs/framework/data/adonet/sql/linq/samples.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="69011-106">*DB* kod örneklerinde sık kullanılan [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] belgeleri.</span><span class="sxs-lookup"><span data-stu-id="69011-106">*db* is often used in code examples in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] documentation.</span></span> <span data-ttu-id="69011-107">*DB* örneği varsayılır bir *Northwind* devraldığı sınıfı <xref:System.Data.Linq.DataContext>.</span><span class="sxs-lookup"><span data-stu-id="69011-107">*db* is assumed to be an instance of a *Northwind* class, which inherits from <xref:System.Data.Linq.DataContext>.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="69011-108">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="69011-108">In This Section</span></span>  
 [<span data-ttu-id="69011-109">Toplu Sorgular</span><span class="sxs-lookup"><span data-stu-id="69011-109">Aggregate Queries</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/aggregate-queries.md)  
 <span data-ttu-id="69011-110">Nasıl kullanılacağını açıklar <xref:System.Linq.Enumerable.Average%2A>, <xref:System.Linq.Enumerable.Count%2A>, vb.</span><span class="sxs-lookup"><span data-stu-id="69011-110">Describes how to use <xref:System.Linq.Enumerable.Average%2A>, <xref:System.Linq.Enumerable.Count%2A>, and so forth.</span></span>  
  
 [<span data-ttu-id="69011-111">Dizideki İlk Öğeyi Döndürme</span><span class="sxs-lookup"><span data-stu-id="69011-111">Return the First Element in a Sequence</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/return-the-first-element-in-a-sequence.md)  
 <span data-ttu-id="69011-112">Kullanım örnekleri sağlar <xref:System.Linq.Enumerable.First%2A>.</span><span class="sxs-lookup"><span data-stu-id="69011-112">Provides examples of using <xref:System.Linq.Enumerable.First%2A>.</span></span>  
  
 [<span data-ttu-id="69011-113">Dizideki Öğeleri Döndürme veya Atlama</span><span class="sxs-lookup"><span data-stu-id="69011-113">Return Or Skip Elements in a Sequence</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/return-or-skip-elements-in-a-sequence.md)  
 <span data-ttu-id="69011-114">Kullanım örnekleri sağlar <xref:System.Linq.Enumerable.Take%2A> ve <xref:System.Linq.Enumerable.Skip%2A>.</span><span class="sxs-lookup"><span data-stu-id="69011-114">Provides examples of using <xref:System.Linq.Enumerable.Take%2A> and <xref:System.Linq.Enumerable.Skip%2A>.</span></span>  
  
 [<span data-ttu-id="69011-115">Dizideki Öğeleri Sıralama</span><span class="sxs-lookup"><span data-stu-id="69011-115">Sort Elements in a Sequence</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/sort-elements-in-a-sequence.md)  
 <span data-ttu-id="69011-116">Kullanım örnekleri sağlar <xref:System.Linq.Enumerable.OrderBy%2A>.</span><span class="sxs-lookup"><span data-stu-id="69011-116">Provides examples of using <xref:System.Linq.Enumerable.OrderBy%2A>.</span></span>  
  
 [<span data-ttu-id="69011-117">Dizideki Öğeleri Gruplama</span><span class="sxs-lookup"><span data-stu-id="69011-117">Group Elements in a Sequence</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/group-elements-in-a-sequence.md)  
 <span data-ttu-id="69011-118">Kullanım örnekleri sağlar <xref:System.Linq.Enumerable.GroupBy%2A>.</span><span class="sxs-lookup"><span data-stu-id="69011-118">Provides examples of using <xref:System.Linq.Enumerable.GroupBy%2A>.</span></span>  
  
 [<span data-ttu-id="69011-119">Dizideki Yinelenen Öğeleri Kaldırma</span><span class="sxs-lookup"><span data-stu-id="69011-119">Eliminate Duplicate Elements from a Sequence</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/eliminate-duplicate-elements-from-a-sequence.md)  
 <span data-ttu-id="69011-120">Kullanım örnekleri sağlar <xref:System.Linq.Enumerable.Distinct%2A>.</span><span class="sxs-lookup"><span data-stu-id="69011-120">Provides examples of using <xref:System.Linq.Enumerable.Distinct%2A>.</span></span>  
  
 [<span data-ttu-id="69011-121">Dizideki Öğelerin Herhangi Birinin veya Tümünün Bir Koşulu Karşılayıp Karşılamadığını Belirleme</span><span class="sxs-lookup"><span data-stu-id="69011-121">Determine if Any or All Elements in a Sequence Satisfy a Condition</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/determine-if-any-or-all-elements-in-a-sequence-satisfy-a-condition.md)  
 <span data-ttu-id="69011-122">Kullanım örnekleri sağlar <xref:System.Linq.Enumerable.All%2A> ve <xref:System.Linq.Enumerable.Any%2A>.</span><span class="sxs-lookup"><span data-stu-id="69011-122">Provides examples of using <xref:System.Linq.Enumerable.All%2A> and <xref:System.Linq.Enumerable.Any%2A>.</span></span>  
  
 [<span data-ttu-id="69011-123">İki Diziyi Birleştirme</span><span class="sxs-lookup"><span data-stu-id="69011-123">Concatenate Two Sequences</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/concatenate-two-sequences.md)  
 <span data-ttu-id="69011-124">Kullanım örnekleri sağlar <xref:System.Linq.Enumerable.Concat%2A>.</span><span class="sxs-lookup"><span data-stu-id="69011-124">Provides examples of using <xref:System.Linq.Enumerable.Concat%2A>.</span></span>  
  
 [<span data-ttu-id="69011-125">İki Dizi Arasındaki Küme Farkını Döndürme</span><span class="sxs-lookup"><span data-stu-id="69011-125">Return the Set Difference Between Two Sequences</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/return-the-set-difference-between-two-sequences.md)  
 <span data-ttu-id="69011-126">Kullanım örnekleri sağlar <xref:System.Linq.Enumerable.Except%2A>.</span><span class="sxs-lookup"><span data-stu-id="69011-126">Provides examples of using <xref:System.Linq.Enumerable.Except%2A>.</span></span>  
  
 [<span data-ttu-id="69011-127">İki Dizinin Küme Kesişimini Döndürme</span><span class="sxs-lookup"><span data-stu-id="69011-127">Return the Set Intersection of Two Sequences</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/return-the-set-intersection-of-two-sequences.md)  
 <span data-ttu-id="69011-128">Kullanım örnekleri sağlar <xref:System.Linq.Enumerable.Intersect%2A>.</span><span class="sxs-lookup"><span data-stu-id="69011-128">Provides examples of using <xref:System.Linq.Enumerable.Intersect%2A>.</span></span>  
  
 [<span data-ttu-id="69011-129">İki Dizinin Küme Birleşimini Döndürme</span><span class="sxs-lookup"><span data-stu-id="69011-129">Return the Set Union of Two Sequences</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/return-the-set-union-of-two-sequences.md)  
 <span data-ttu-id="69011-130">Kullanım örnekleri sağlar <xref:System.Linq.Enumerable.Union%2A>.</span><span class="sxs-lookup"><span data-stu-id="69011-130">Provides examples of using <xref:System.Linq.Enumerable.Union%2A>.</span></span>  
  
 [<span data-ttu-id="69011-131">Diziyi (Sequence) Diziye (Array) Dönüştürme</span><span class="sxs-lookup"><span data-stu-id="69011-131">Convert a Sequence to an Array</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/convert-a-sequence-to-an-array.md)  
 <span data-ttu-id="69011-132">Kullanım örnekleri sağlar <xref:System.Linq.Enumerable.ToArray%2A>.</span><span class="sxs-lookup"><span data-stu-id="69011-132">Provides examples of using <xref:System.Linq.Enumerable.ToArray%2A>.</span></span>  
  
 [<span data-ttu-id="69011-133">Diziyi Genel Listeye Dönüştürme</span><span class="sxs-lookup"><span data-stu-id="69011-133">Convert a Sequence to a Generic List</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/convert-a-sequence-to-a-generic-list.md)  
 <span data-ttu-id="69011-134">Kullanım örnekleri sağlar <xref:System.Linq.Enumerable.ToList%2A>.</span><span class="sxs-lookup"><span data-stu-id="69011-134">Provides examples of using <xref:System.Linq.Enumerable.ToList%2A>.</span></span>  
  
 [<span data-ttu-id="69011-135">Türü Genel IEnumerable Öğesine Dönüştürme</span><span class="sxs-lookup"><span data-stu-id="69011-135">Convert a Type to a Generic IEnumerable</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/convert-a-type-to-a-generic-ienumerable.md)  
 <span data-ttu-id="69011-136">Kullanım örnekleri sağlar <xref:System.Linq.Enumerable.AsEnumerable%2A>.</span><span class="sxs-lookup"><span data-stu-id="69011-136">Provides examples of using <xref:System.Linq.Enumerable.AsEnumerable%2A>.</span></span>  
  
 [<span data-ttu-id="69011-137">Birleşimler ve Çapraz Ürün Sorguları Düzenleme</span><span class="sxs-lookup"><span data-stu-id="69011-137">Formulate Joins and Cross-Product Queries</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/formulate-joins-and-cross-product-queries.md)  
 <span data-ttu-id="69011-138">Yabancı anahtar Gezinti bölmesinde kullanma örnekleri sağlar `from`, `where`, ve `select` yan tümceleri.</span><span class="sxs-lookup"><span data-stu-id="69011-138">Provides examples of using foreign-key navigation in the `from`, `where`, and `select` clauses.</span></span>  
  
 [<span data-ttu-id="69011-139">Projeksiyonlar Düzenleme</span><span class="sxs-lookup"><span data-stu-id="69011-139">Formulate Projections</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/formulate-projections.md)  
 <span data-ttu-id="69011-140">Birleştirme örnekleri sağlar `select` diğer özelliklerle (örneğin, *anonim türler*) form sorgu tahminleri için.</span><span class="sxs-lookup"><span data-stu-id="69011-140">Provides examples of combining `select` with other features (for example, *anonymous types*) to form query projections.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="69011-141">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="69011-141">Related Sections</span></span>  
 [<span data-ttu-id="69011-142">Standart Sorgu İşleçlerine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="69011-142">Standard Query Operators Overview</span></span>](http://msdn.microsoft.com/library/24cda21e-8af8-4632-b519-c404a839b9b2)  
 <span data-ttu-id="69011-143">Standart sorgu işleçleri kavramını açıklar.</span><span class="sxs-lookup"><span data-stu-id="69011-143">Explains the concept of standard query operators.</span></span>  
  
 [<span data-ttu-id="69011-144">Sorgu Kavramları</span><span class="sxs-lookup"><span data-stu-id="69011-144">Query Concepts</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/query-concepts.md)  
 <span data-ttu-id="69011-145">Açıklar nasıl [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] sorguları için geçerlidir kavramları kullanır.</span><span class="sxs-lookup"><span data-stu-id="69011-145">Explains how [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] uses concepts that apply to queries.</span></span>  
  
 [<span data-ttu-id="69011-146">Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="69011-146">Programming Guide</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/programming-guide.md)  
 <span data-ttu-id="69011-147">Programlama Kavramları ilgili açıklayan konulara bir portal sağlar [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="69011-147">Provides a portal to topics that explain programming concepts related to [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span>
