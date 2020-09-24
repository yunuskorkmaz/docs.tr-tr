---
title: Sorgu Örnekleri
ms.date: 03/30/2017
ms.assetid: 137f8677-494c-4d49-95ce-c17742f2d01f
ms.openlocfilehash: f3f135850fb5f40b3b8882f72f5cc24512f21084
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91147560"
---
# <a name="query-examples"></a><span data-ttu-id="918e3-102">Sorgu Örnekleri</span><span class="sxs-lookup"><span data-stu-id="918e3-102">Query Examples</span></span>

<span data-ttu-id="918e3-103">Bu bölümde, tipik sorgulara yönelik Visual Basic ve C# örnekleri verilmiştir [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="918e3-103">This section provides Visual Basic and C# examples of typical [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] queries.</span></span> <span data-ttu-id="918e3-104">Visual Studio kullanan geliştiriciler, örnekler bölümünde bulunan örnek bir çözümde birçok örnek bulabilir.</span><span class="sxs-lookup"><span data-stu-id="918e3-104">Developers using Visual Studio can find many more examples in a sample solution available in the Samples section.</span></span> <span data-ttu-id="918e3-105">Daha fazla bilgi için bkz. [örnekler](samples.md).</span><span class="sxs-lookup"><span data-stu-id="918e3-105">For more information, see [Samples](samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="918e3-106">*veritabanı* , genellikle belgelerdeki kod örneklerinde kullanılır [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="918e3-106">*db* is often used in code examples in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] documentation.</span></span> <span data-ttu-id="918e3-107">*DB* 'Nin devralan *Northwind* sınıfının bir örneği olduğu varsayılır <xref:System.Data.Linq.DataContext> .</span><span class="sxs-lookup"><span data-stu-id="918e3-107">*db* is assumed to be an instance of a *Northwind* class, which inherits from <xref:System.Data.Linq.DataContext>.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="918e3-108">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="918e3-108">In This Section</span></span>  

 [<span data-ttu-id="918e3-109">Toplu Sorgular</span><span class="sxs-lookup"><span data-stu-id="918e3-109">Aggregate Queries</span></span>](aggregate-queries.md)  
 <span data-ttu-id="918e3-110">, Ve ' nin nasıl kullanılacağını açıklar <xref:System.Linq.Enumerable.Average%2A> <xref:System.Linq.Enumerable.Count%2A> .</span><span class="sxs-lookup"><span data-stu-id="918e3-110">Describes how to use <xref:System.Linq.Enumerable.Average%2A>, <xref:System.Linq.Enumerable.Count%2A>, and so forth.</span></span>  
  
 [<span data-ttu-id="918e3-111">Dizideki İlk Öğeyi Döndürme</span><span class="sxs-lookup"><span data-stu-id="918e3-111">Return the First Element in a Sequence</span></span>](return-the-first-element-in-a-sequence.md)  
 <span data-ttu-id="918e3-112">, Kullanma örnekleri sağlar <xref:System.Linq.Enumerable.First%2A> .</span><span class="sxs-lookup"><span data-stu-id="918e3-112">Provides examples of using <xref:System.Linq.Enumerable.First%2A>.</span></span>  
  
 [<span data-ttu-id="918e3-113">Dizideki Öğeleri Döndürme veya Atlama</span><span class="sxs-lookup"><span data-stu-id="918e3-113">Return Or Skip Elements in a Sequence</span></span>](return-or-skip-elements-in-a-sequence.md)  
 <span data-ttu-id="918e3-114">, Ve kullanımına örnekler <xref:System.Linq.Enumerable.Take%2A> sağlar <xref:System.Linq.Enumerable.Skip%2A> .</span><span class="sxs-lookup"><span data-stu-id="918e3-114">Provides examples of using <xref:System.Linq.Enumerable.Take%2A> and <xref:System.Linq.Enumerable.Skip%2A>.</span></span>  
  
 [<span data-ttu-id="918e3-115">Dizideki Öğeleri Sıralama</span><span class="sxs-lookup"><span data-stu-id="918e3-115">Sort Elements in a Sequence</span></span>](sort-elements-in-a-sequence.md)  
 <span data-ttu-id="918e3-116">, Kullanma örnekleri sağlar <xref:System.Linq.Enumerable.OrderBy%2A> .</span><span class="sxs-lookup"><span data-stu-id="918e3-116">Provides examples of using <xref:System.Linq.Enumerable.OrderBy%2A>.</span></span>  
  
 [<span data-ttu-id="918e3-117">Dizideki Öğeleri Gruplama</span><span class="sxs-lookup"><span data-stu-id="918e3-117">Group Elements in a Sequence</span></span>](group-elements-in-a-sequence.md)  
 <span data-ttu-id="918e3-118">, Kullanma örnekleri sağlar <xref:System.Linq.Enumerable.GroupBy%2A> .</span><span class="sxs-lookup"><span data-stu-id="918e3-118">Provides examples of using <xref:System.Linq.Enumerable.GroupBy%2A>.</span></span>  
  
 [<span data-ttu-id="918e3-119">Dizideki Yinelenen Öğeleri Kaldırma</span><span class="sxs-lookup"><span data-stu-id="918e3-119">Eliminate Duplicate Elements from a Sequence</span></span>](eliminate-duplicate-elements-from-a-sequence.md)  
 <span data-ttu-id="918e3-120">, Kullanma örnekleri sağlar <xref:System.Linq.Enumerable.Distinct%2A> .</span><span class="sxs-lookup"><span data-stu-id="918e3-120">Provides examples of using <xref:System.Linq.Enumerable.Distinct%2A>.</span></span>  
  
 [<span data-ttu-id="918e3-121">Dizideki Öğelerin Herhangi Birinin veya Tümünün Bir Koşulu Karşılayıp Karşılamadığını Belirleme</span><span class="sxs-lookup"><span data-stu-id="918e3-121">Determine if Any or All Elements in a Sequence Satisfy a Condition</span></span>](determine-if-any-or-all-elements-in-a-sequence-satisfy-a-condition.md)  
 <span data-ttu-id="918e3-122">, Ve kullanımına örnekler <xref:System.Linq.Enumerable.All%2A> sağlar <xref:System.Linq.Enumerable.Any%2A> .</span><span class="sxs-lookup"><span data-stu-id="918e3-122">Provides examples of using <xref:System.Linq.Enumerable.All%2A> and <xref:System.Linq.Enumerable.Any%2A>.</span></span>  
  
 [<span data-ttu-id="918e3-123">İki Diziyi Birleştirme</span><span class="sxs-lookup"><span data-stu-id="918e3-123">Concatenate Two Sequences</span></span>](concatenate-two-sequences.md)  
 <span data-ttu-id="918e3-124">, Kullanma örnekleri sağlar <xref:System.Linq.Enumerable.Concat%2A> .</span><span class="sxs-lookup"><span data-stu-id="918e3-124">Provides examples of using <xref:System.Linq.Enumerable.Concat%2A>.</span></span>  
  
 [<span data-ttu-id="918e3-125">İki Dizi Arasındaki Küme Farkını Döndürme</span><span class="sxs-lookup"><span data-stu-id="918e3-125">Return the Set Difference Between Two Sequences</span></span>](return-the-set-difference-between-two-sequences.md)  
 <span data-ttu-id="918e3-126">, Kullanma örnekleri sağlar <xref:System.Linq.Enumerable.Except%2A> .</span><span class="sxs-lookup"><span data-stu-id="918e3-126">Provides examples of using <xref:System.Linq.Enumerable.Except%2A>.</span></span>  
  
 [<span data-ttu-id="918e3-127">İki Dizinin Küme Kesişimini Döndürme</span><span class="sxs-lookup"><span data-stu-id="918e3-127">Return the Set Intersection of Two Sequences</span></span>](return-the-set-intersection-of-two-sequences.md)  
 <span data-ttu-id="918e3-128">, Kullanma örnekleri sağlar <xref:System.Linq.Enumerable.Intersect%2A> .</span><span class="sxs-lookup"><span data-stu-id="918e3-128">Provides examples of using <xref:System.Linq.Enumerable.Intersect%2A>.</span></span>  
  
 [<span data-ttu-id="918e3-129">İki Dizinin Küme Birleşimini Döndürme</span><span class="sxs-lookup"><span data-stu-id="918e3-129">Return the Set Union of Two Sequences</span></span>](return-the-set-union-of-two-sequences.md)  
 <span data-ttu-id="918e3-130">, Kullanma örnekleri sağlar <xref:System.Linq.Enumerable.Union%2A> .</span><span class="sxs-lookup"><span data-stu-id="918e3-130">Provides examples of using <xref:System.Linq.Enumerable.Union%2A>.</span></span>  
  
 [<span data-ttu-id="918e3-131">Diziyi (Sequence) Diziye (Array) Dönüştürme</span><span class="sxs-lookup"><span data-stu-id="918e3-131">Convert a Sequence to an Array</span></span>](convert-a-sequence-to-an-array.md)  
 <span data-ttu-id="918e3-132">, Kullanma örnekleri sağlar <xref:System.Linq.Enumerable.ToArray%2A> .</span><span class="sxs-lookup"><span data-stu-id="918e3-132">Provides examples of using <xref:System.Linq.Enumerable.ToArray%2A>.</span></span>  
  
 [<span data-ttu-id="918e3-133">Diziyi Genel Listeye Dönüştürme</span><span class="sxs-lookup"><span data-stu-id="918e3-133">Convert a Sequence to a Generic List</span></span>](convert-a-sequence-to-a-generic-list.md)  
 <span data-ttu-id="918e3-134">, Kullanma örnekleri sağlar <xref:System.Linq.Enumerable.ToList%2A> .</span><span class="sxs-lookup"><span data-stu-id="918e3-134">Provides examples of using <xref:System.Linq.Enumerable.ToList%2A>.</span></span>  
  
 [<span data-ttu-id="918e3-135">Türü Genel IEnumerable Öğesine Dönüştürme</span><span class="sxs-lookup"><span data-stu-id="918e3-135">Convert a Type to a Generic IEnumerable</span></span>](convert-a-type-to-a-generic-ienumerable.md)  
 <span data-ttu-id="918e3-136">, Kullanma örnekleri sağlar <xref:System.Linq.Enumerable.AsEnumerable%2A> .</span><span class="sxs-lookup"><span data-stu-id="918e3-136">Provides examples of using <xref:System.Linq.Enumerable.AsEnumerable%2A>.</span></span>  
  
 [<span data-ttu-id="918e3-137">Birleşimler ve Çapraz Ürün Sorguları Düzenleme</span><span class="sxs-lookup"><span data-stu-id="918e3-137">Formulate Joins and Cross-Product Queries</span></span>](formulate-joins-and-cross-product-queries.md)  
 <span data-ttu-id="918e3-138">`from`, `where` , Ve `select` yan tümcelerinde yabancı anahtar gezintisini kullanma örnekleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="918e3-138">Provides examples of using foreign-key navigation in the `from`, `where`, and `select` clauses.</span></span>  
  
 [<span data-ttu-id="918e3-139">Projeksiyonlar Düzenleme</span><span class="sxs-lookup"><span data-stu-id="918e3-139">Formulate Projections</span></span>](formulate-projections.md)  
 <span data-ttu-id="918e3-140">`select`Sorgu projeksiyonlarını biçimlendirmek için diğer özelliklerle birleştirme örnekleri sağlar (örneğin, *anonim türler*).</span><span class="sxs-lookup"><span data-stu-id="918e3-140">Provides examples of combining `select` with other features (for example, *anonymous types*) to form query projections.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="918e3-141">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="918e3-141">Related Sections</span></span>  

 [<span data-ttu-id="918e3-142">Standart sorgu Işleçlerine genel bakış (C#)</span><span class="sxs-lookup"><span data-stu-id="918e3-142">Standard Query Operators Overview (C#)</span></span>](../../../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)  
 <span data-ttu-id="918e3-143">C# kullanan standart sorgu işleçleri kavramını açıklar.</span><span class="sxs-lookup"><span data-stu-id="918e3-143">Explains the concept of standard query operators using C#.</span></span>  
  
 [<span data-ttu-id="918e3-144">Standart sorgu Işleçlerine genel bakış (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="918e3-144">Standard Query Operators Overview (Visual Basic)</span></span>](../../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)  
 <span data-ttu-id="918e3-145">Visual Basic kullanan standart sorgu işleçleri kavramını açıklar.</span><span class="sxs-lookup"><span data-stu-id="918e3-145">Explains the concept of standard query operators using Visual Basic.</span></span>  
  
 [<span data-ttu-id="918e3-146">Sorgu Kavramları</span><span class="sxs-lookup"><span data-stu-id="918e3-146">Query Concepts</span></span>](query-concepts.md)  
 <span data-ttu-id="918e3-147">[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]Sorgular için uygulanan kavramların nasıl kullandığını açıklar.</span><span class="sxs-lookup"><span data-stu-id="918e3-147">Explains how [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] uses concepts that apply to queries.</span></span>  
  
 [<span data-ttu-id="918e3-148">Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="918e3-148">Programming Guide</span></span>](programming-guide.md)  
 <span data-ttu-id="918e3-149">İle ilgili programlama kavramlarını açıklayan konularda bir portal sağlar [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="918e3-149">Provides a portal to topics that explain programming concepts related to [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span>
