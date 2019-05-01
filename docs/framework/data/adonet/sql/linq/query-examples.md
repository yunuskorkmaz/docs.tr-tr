---
title: Sorgu Örnekleri
ms.date: 03/30/2017
ms.assetid: 137f8677-494c-4d49-95ce-c17742f2d01f
ms.openlocfilehash: 74664dd98ac067153894edc934c8f15eec407261
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61783116"
---
# <a name="query-examples"></a><span data-ttu-id="204e6-102">Sorgu Örnekleri</span><span class="sxs-lookup"><span data-stu-id="204e6-102">Query Examples</span></span>
<span data-ttu-id="204e6-103">Bu bölümde Visual Basic ve C# örnekleri tipik [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] sorgular.</span><span class="sxs-lookup"><span data-stu-id="204e6-103">This section provides Visual Basic and C# examples of typical [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] queries.</span></span> <span data-ttu-id="204e6-104">Visual Studio kullanan geliştiricilerin çok daha fazla örnek, bir örnek çözüm kullanılabilir örnekleri bölümünde bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="204e6-104">Developers using Visual Studio can find many more examples in a sample solution available in the Samples section.</span></span> <span data-ttu-id="204e6-105">Daha fazla bilgi için [örnekleri](../../../../../../docs/framework/data/adonet/sql/linq/samples.md).</span><span class="sxs-lookup"><span data-stu-id="204e6-105">For more information, see [Samples](../../../../../../docs/framework/data/adonet/sql/linq/samples.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="204e6-106">*DB* kod örneklerinde sık kullanılan [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] belgeleri.</span><span class="sxs-lookup"><span data-stu-id="204e6-106">*db* is often used in code examples in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] documentation.</span></span> <span data-ttu-id="204e6-107">*DB* örneği varsayılır bir *Northwind* öğesinden devralan sınıf <xref:System.Data.Linq.DataContext>.</span><span class="sxs-lookup"><span data-stu-id="204e6-107">*db* is assumed to be an instance of a *Northwind* class, which inherits from <xref:System.Data.Linq.DataContext>.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="204e6-108">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="204e6-108">In This Section</span></span>  
 [<span data-ttu-id="204e6-109">Toplu Sorgular</span><span class="sxs-lookup"><span data-stu-id="204e6-109">Aggregate Queries</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/aggregate-queries.md)  
 <span data-ttu-id="204e6-110">Nasıl kullanılacağını açıklar <xref:System.Linq.Enumerable.Average%2A>, <xref:System.Linq.Enumerable.Count%2A>ve böyle devam eder.</span><span class="sxs-lookup"><span data-stu-id="204e6-110">Describes how to use <xref:System.Linq.Enumerable.Average%2A>, <xref:System.Linq.Enumerable.Count%2A>, and so forth.</span></span>  
  
 [<span data-ttu-id="204e6-111">Dizideki İlk Öğeyi Döndürme</span><span class="sxs-lookup"><span data-stu-id="204e6-111">Return the First Element in a Sequence</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/return-the-first-element-in-a-sequence.md)  
 <span data-ttu-id="204e6-112">Kullanım örnekleri sağlar <xref:System.Linq.Enumerable.First%2A>.</span><span class="sxs-lookup"><span data-stu-id="204e6-112">Provides examples of using <xref:System.Linq.Enumerable.First%2A>.</span></span>  
  
 [<span data-ttu-id="204e6-113">Dizideki Öğeleri Döndürme veya Atlama</span><span class="sxs-lookup"><span data-stu-id="204e6-113">Return Or Skip Elements in a Sequence</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/return-or-skip-elements-in-a-sequence.md)  
 <span data-ttu-id="204e6-114">Kullanım örnekleri sağlar <xref:System.Linq.Enumerable.Take%2A> ve <xref:System.Linq.Enumerable.Skip%2A>.</span><span class="sxs-lookup"><span data-stu-id="204e6-114">Provides examples of using <xref:System.Linq.Enumerable.Take%2A> and <xref:System.Linq.Enumerable.Skip%2A>.</span></span>  
  
 [<span data-ttu-id="204e6-115">Dizideki Öğeleri Sıralama</span><span class="sxs-lookup"><span data-stu-id="204e6-115">Sort Elements in a Sequence</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/sort-elements-in-a-sequence.md)  
 <span data-ttu-id="204e6-116">Kullanım örnekleri sağlar <xref:System.Linq.Enumerable.OrderBy%2A>.</span><span class="sxs-lookup"><span data-stu-id="204e6-116">Provides examples of using <xref:System.Linq.Enumerable.OrderBy%2A>.</span></span>  
  
 [<span data-ttu-id="204e6-117">Dizideki Öğeleri Gruplama</span><span class="sxs-lookup"><span data-stu-id="204e6-117">Group Elements in a Sequence</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/group-elements-in-a-sequence.md)  
 <span data-ttu-id="204e6-118">Kullanım örnekleri sağlar <xref:System.Linq.Enumerable.GroupBy%2A>.</span><span class="sxs-lookup"><span data-stu-id="204e6-118">Provides examples of using <xref:System.Linq.Enumerable.GroupBy%2A>.</span></span>  
  
 [<span data-ttu-id="204e6-119">Dizideki Yinelenen Öğeleri Kaldırma</span><span class="sxs-lookup"><span data-stu-id="204e6-119">Eliminate Duplicate Elements from a Sequence</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/eliminate-duplicate-elements-from-a-sequence.md)  
 <span data-ttu-id="204e6-120">Kullanım örnekleri sağlar <xref:System.Linq.Enumerable.Distinct%2A>.</span><span class="sxs-lookup"><span data-stu-id="204e6-120">Provides examples of using <xref:System.Linq.Enumerable.Distinct%2A>.</span></span>  
  
 [<span data-ttu-id="204e6-121">Dizideki Öğelerin Herhangi Birinin veya Tümünün Bir Koşulu Karşılayıp Karşılamadığını Belirleme</span><span class="sxs-lookup"><span data-stu-id="204e6-121">Determine if Any or All Elements in a Sequence Satisfy a Condition</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/determine-if-any-or-all-elements-in-a-sequence-satisfy-a-condition.md)  
 <span data-ttu-id="204e6-122">Kullanım örnekleri sağlar <xref:System.Linq.Enumerable.All%2A> ve <xref:System.Linq.Enumerable.Any%2A>.</span><span class="sxs-lookup"><span data-stu-id="204e6-122">Provides examples of using <xref:System.Linq.Enumerable.All%2A> and <xref:System.Linq.Enumerable.Any%2A>.</span></span>  
  
 [<span data-ttu-id="204e6-123">İki Diziyi Birleştirme</span><span class="sxs-lookup"><span data-stu-id="204e6-123">Concatenate Two Sequences</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/concatenate-two-sequences.md)  
 <span data-ttu-id="204e6-124">Kullanım örnekleri sağlar <xref:System.Linq.Enumerable.Concat%2A>.</span><span class="sxs-lookup"><span data-stu-id="204e6-124">Provides examples of using <xref:System.Linq.Enumerable.Concat%2A>.</span></span>  
  
 [<span data-ttu-id="204e6-125">İki Dizi Arasındaki Küme Farkını Döndürme</span><span class="sxs-lookup"><span data-stu-id="204e6-125">Return the Set Difference Between Two Sequences</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/return-the-set-difference-between-two-sequences.md)  
 <span data-ttu-id="204e6-126">Kullanım örnekleri sağlar <xref:System.Linq.Enumerable.Except%2A>.</span><span class="sxs-lookup"><span data-stu-id="204e6-126">Provides examples of using <xref:System.Linq.Enumerable.Except%2A>.</span></span>  
  
 [<span data-ttu-id="204e6-127">İki Dizinin Küme Kesişimini Döndürme</span><span class="sxs-lookup"><span data-stu-id="204e6-127">Return the Set Intersection of Two Sequences</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/return-the-set-intersection-of-two-sequences.md)  
 <span data-ttu-id="204e6-128">Kullanım örnekleri sağlar <xref:System.Linq.Enumerable.Intersect%2A>.</span><span class="sxs-lookup"><span data-stu-id="204e6-128">Provides examples of using <xref:System.Linq.Enumerable.Intersect%2A>.</span></span>  
  
 [<span data-ttu-id="204e6-129">İki Dizinin Küme Birleşimini Döndürme</span><span class="sxs-lookup"><span data-stu-id="204e6-129">Return the Set Union of Two Sequences</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/return-the-set-union-of-two-sequences.md)  
 <span data-ttu-id="204e6-130">Kullanım örnekleri sağlar <xref:System.Linq.Enumerable.Union%2A>.</span><span class="sxs-lookup"><span data-stu-id="204e6-130">Provides examples of using <xref:System.Linq.Enumerable.Union%2A>.</span></span>  
  
 [<span data-ttu-id="204e6-131">Diziyi (Sequence) Diziye (Array) Dönüştürme</span><span class="sxs-lookup"><span data-stu-id="204e6-131">Convert a Sequence to an Array</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/convert-a-sequence-to-an-array.md)  
 <span data-ttu-id="204e6-132">Kullanım örnekleri sağlar <xref:System.Linq.Enumerable.ToArray%2A>.</span><span class="sxs-lookup"><span data-stu-id="204e6-132">Provides examples of using <xref:System.Linq.Enumerable.ToArray%2A>.</span></span>  
  
 [<span data-ttu-id="204e6-133">Diziyi Genel Listeye Dönüştürme</span><span class="sxs-lookup"><span data-stu-id="204e6-133">Convert a Sequence to a Generic List</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/convert-a-sequence-to-a-generic-list.md)  
 <span data-ttu-id="204e6-134">Kullanım örnekleri sağlar <xref:System.Linq.Enumerable.ToList%2A>.</span><span class="sxs-lookup"><span data-stu-id="204e6-134">Provides examples of using <xref:System.Linq.Enumerable.ToList%2A>.</span></span>  
  
 [<span data-ttu-id="204e6-135">Türü Genel IEnumerable Öğesine Dönüştürme</span><span class="sxs-lookup"><span data-stu-id="204e6-135">Convert a Type to a Generic IEnumerable</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/convert-a-type-to-a-generic-ienumerable.md)  
 <span data-ttu-id="204e6-136">Kullanım örnekleri sağlar <xref:System.Linq.Enumerable.AsEnumerable%2A>.</span><span class="sxs-lookup"><span data-stu-id="204e6-136">Provides examples of using <xref:System.Linq.Enumerable.AsEnumerable%2A>.</span></span>  
  
 [<span data-ttu-id="204e6-137">Birleşimler ve Çapraz Ürün Sorguları Düzenleme</span><span class="sxs-lookup"><span data-stu-id="204e6-137">Formulate Joins and Cross-Product Queries</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/formulate-joins-and-cross-product-queries.md)  
 <span data-ttu-id="204e6-138">Yabancı anahtar Gezinti kullanma örnekleri sağlar `from`, `where`, ve `select` yan tümceleri.</span><span class="sxs-lookup"><span data-stu-id="204e6-138">Provides examples of using foreign-key navigation in the `from`, `where`, and `select` clauses.</span></span>  
  
 [<span data-ttu-id="204e6-139">Projeksiyonlar Düzenleme</span><span class="sxs-lookup"><span data-stu-id="204e6-139">Formulate Projections</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/formulate-projections.md)  
 <span data-ttu-id="204e6-140">Birleştirme örnekleri sağlar `select` diğer özelliklerle (örneğin, *anonim türler*) form sorgu projeksiyonları için.</span><span class="sxs-lookup"><span data-stu-id="204e6-140">Provides examples of combining `select` with other features (for example, *anonymous types*) to form query projections.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="204e6-141">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="204e6-141">Related Sections</span></span>  
 [<span data-ttu-id="204e6-142">Standart sorgu işleçlerine genel bakış (C#)</span><span class="sxs-lookup"><span data-stu-id="204e6-142">Standard Query Operators Overview (C#)</span></span>](../../../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)  
 <span data-ttu-id="204e6-143">Standart sorgu işleçleri kullanarak kavramını açıklar C#.</span><span class="sxs-lookup"><span data-stu-id="204e6-143">Explains the concept of standard query operators using C#.</span></span>  
  
 [<span data-ttu-id="204e6-144">Standart sorgu işleçlerine genel bakış (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="204e6-144">Standard Query Operators Overview (Visual Basic)</span></span>](../../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)  
 <span data-ttu-id="204e6-145">Visual Basic kullanarak standart sorgu işleçleri kavramını açıklar.</span><span class="sxs-lookup"><span data-stu-id="204e6-145">Explains the concept of standard query operators using Visual Basic.</span></span>  
  
 [<span data-ttu-id="204e6-146">Sorgu Kavramları</span><span class="sxs-lookup"><span data-stu-id="204e6-146">Query Concepts</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/query-concepts.md)  
 <span data-ttu-id="204e6-147">Açıklayan nasıl [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] sorguları için geçerlidir kavramları kullanır.</span><span class="sxs-lookup"><span data-stu-id="204e6-147">Explains how [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] uses concepts that apply to queries.</span></span>  
  
 [<span data-ttu-id="204e6-148">Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="204e6-148">Programming Guide</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/programming-guide.md)  
 <span data-ttu-id="204e6-149">İlgili programlama kavramları açıklayan konulara bir portal sağlar [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="204e6-149">Provides a portal to topics that explain programming concepts related to [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span>
