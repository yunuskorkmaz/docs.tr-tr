---
title: Sorgu Örnekleri
ms.date: 03/30/2017
ms.assetid: 137f8677-494c-4d49-95ce-c17742f2d01f
ms.openlocfilehash: 8f86c4aa94dcc70ce79526b0f4a3685cfef3f389
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70781140"
---
# <a name="query-examples"></a><span data-ttu-id="44ae5-102">Sorgu Örnekleri</span><span class="sxs-lookup"><span data-stu-id="44ae5-102">Query Examples</span></span>
<span data-ttu-id="44ae5-103">Bu bölümde tipik [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] sorguların Visual Basic C# ve örnekleri verilmektedir.</span><span class="sxs-lookup"><span data-stu-id="44ae5-103">This section provides Visual Basic and C# examples of typical [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] queries.</span></span> <span data-ttu-id="44ae5-104">Visual Studio kullanan geliştiriciler, örnekler bölümünde bulunan örnek bir çözümde birçok örnek bulabilir.</span><span class="sxs-lookup"><span data-stu-id="44ae5-104">Developers using Visual Studio can find many more examples in a sample solution available in the Samples section.</span></span> <span data-ttu-id="44ae5-105">Daha fazla bilgi için bkz. [örnekler](samples.md).</span><span class="sxs-lookup"><span data-stu-id="44ae5-105">For more information, see [Samples](samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="44ae5-106">*veritabanı* , genellikle [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] belgelerdeki kod örneklerinde kullanılır.</span><span class="sxs-lookup"><span data-stu-id="44ae5-106">*db* is often used in code examples in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] documentation.</span></span> <span data-ttu-id="44ae5-107">*DB* 'Nin devralan <xref:System.Data.Linq.DataContext> *Northwind* sınıfının bir örneği olduğu varsayılır.</span><span class="sxs-lookup"><span data-stu-id="44ae5-107">*db* is assumed to be an instance of a *Northwind* class, which inherits from <xref:System.Data.Linq.DataContext>.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="44ae5-108">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="44ae5-108">In This Section</span></span>  
 [<span data-ttu-id="44ae5-109">Toplu Sorgular</span><span class="sxs-lookup"><span data-stu-id="44ae5-109">Aggregate Queries</span></span>](aggregate-queries.md)  
 <span data-ttu-id="44ae5-110"><xref:System.Linq.Enumerable.Average%2A> ,<xref:System.Linq.Enumerable.Count%2A>Ve ' nin nasıl kullanılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="44ae5-110">Describes how to use <xref:System.Linq.Enumerable.Average%2A>, <xref:System.Linq.Enumerable.Count%2A>, and so forth.</span></span>  
  
 [<span data-ttu-id="44ae5-111">Dizideki İlk Öğeyi Döndürme</span><span class="sxs-lookup"><span data-stu-id="44ae5-111">Return the First Element in a Sequence</span></span>](return-the-first-element-in-a-sequence.md)  
 <span data-ttu-id="44ae5-112">, Kullanma <xref:System.Linq.Enumerable.First%2A>örnekleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="44ae5-112">Provides examples of using <xref:System.Linq.Enumerable.First%2A>.</span></span>  
  
 [<span data-ttu-id="44ae5-113">Dizideki Öğeleri Döndürme veya Atlama</span><span class="sxs-lookup"><span data-stu-id="44ae5-113">Return Or Skip Elements in a Sequence</span></span>](return-or-skip-elements-in-a-sequence.md)  
 <span data-ttu-id="44ae5-114">, Ve <xref:System.Linq.Enumerable.Take%2A> <xref:System.Linq.Enumerable.Skip%2A>kullanımına örnekler sağlar.</span><span class="sxs-lookup"><span data-stu-id="44ae5-114">Provides examples of using <xref:System.Linq.Enumerable.Take%2A> and <xref:System.Linq.Enumerable.Skip%2A>.</span></span>  
  
 [<span data-ttu-id="44ae5-115">Dizideki Öğeleri Sıralama</span><span class="sxs-lookup"><span data-stu-id="44ae5-115">Sort Elements in a Sequence</span></span>](sort-elements-in-a-sequence.md)  
 <span data-ttu-id="44ae5-116">, Kullanma <xref:System.Linq.Enumerable.OrderBy%2A>örnekleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="44ae5-116">Provides examples of using <xref:System.Linq.Enumerable.OrderBy%2A>.</span></span>  
  
 [<span data-ttu-id="44ae5-117">Dizideki Öğeleri Gruplama</span><span class="sxs-lookup"><span data-stu-id="44ae5-117">Group Elements in a Sequence</span></span>](group-elements-in-a-sequence.md)  
 <span data-ttu-id="44ae5-118">, Kullanma <xref:System.Linq.Enumerable.GroupBy%2A>örnekleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="44ae5-118">Provides examples of using <xref:System.Linq.Enumerable.GroupBy%2A>.</span></span>  
  
 [<span data-ttu-id="44ae5-119">Dizideki Yinelenen Öğeleri Kaldırma</span><span class="sxs-lookup"><span data-stu-id="44ae5-119">Eliminate Duplicate Elements from a Sequence</span></span>](eliminate-duplicate-elements-from-a-sequence.md)  
 <span data-ttu-id="44ae5-120">, Kullanma <xref:System.Linq.Enumerable.Distinct%2A>örnekleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="44ae5-120">Provides examples of using <xref:System.Linq.Enumerable.Distinct%2A>.</span></span>  
  
 [<span data-ttu-id="44ae5-121">Dizideki Öğelerin Herhangi Birinin veya Tümünün Bir Koşulu Karşılayıp Karşılamadığını Belirleme</span><span class="sxs-lookup"><span data-stu-id="44ae5-121">Determine if Any or All Elements in a Sequence Satisfy a Condition</span></span>](determine-if-any-or-all-elements-in-a-sequence-satisfy-a-condition.md)  
 <span data-ttu-id="44ae5-122">, Ve <xref:System.Linq.Enumerable.All%2A> <xref:System.Linq.Enumerable.Any%2A>kullanımına örnekler sağlar.</span><span class="sxs-lookup"><span data-stu-id="44ae5-122">Provides examples of using <xref:System.Linq.Enumerable.All%2A> and <xref:System.Linq.Enumerable.Any%2A>.</span></span>  
  
 [<span data-ttu-id="44ae5-123">İki Diziyi Birleştirme</span><span class="sxs-lookup"><span data-stu-id="44ae5-123">Concatenate Two Sequences</span></span>](concatenate-two-sequences.md)  
 <span data-ttu-id="44ae5-124">, Kullanma <xref:System.Linq.Enumerable.Concat%2A>örnekleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="44ae5-124">Provides examples of using <xref:System.Linq.Enumerable.Concat%2A>.</span></span>  
  
 [<span data-ttu-id="44ae5-125">İki Dizi Arasındaki Küme Farkını Döndürme</span><span class="sxs-lookup"><span data-stu-id="44ae5-125">Return the Set Difference Between Two Sequences</span></span>](return-the-set-difference-between-two-sequences.md)  
 <span data-ttu-id="44ae5-126">, Kullanma <xref:System.Linq.Enumerable.Except%2A>örnekleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="44ae5-126">Provides examples of using <xref:System.Linq.Enumerable.Except%2A>.</span></span>  
  
 [<span data-ttu-id="44ae5-127">İki Dizinin Küme Kesişimini Döndürme</span><span class="sxs-lookup"><span data-stu-id="44ae5-127">Return the Set Intersection of Two Sequences</span></span>](return-the-set-intersection-of-two-sequences.md)  
 <span data-ttu-id="44ae5-128">, Kullanma <xref:System.Linq.Enumerable.Intersect%2A>örnekleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="44ae5-128">Provides examples of using <xref:System.Linq.Enumerable.Intersect%2A>.</span></span>  
  
 [<span data-ttu-id="44ae5-129">İki Dizinin Küme Birleşimini Döndürme</span><span class="sxs-lookup"><span data-stu-id="44ae5-129">Return the Set Union of Two Sequences</span></span>](return-the-set-union-of-two-sequences.md)  
 <span data-ttu-id="44ae5-130">, Kullanma <xref:System.Linq.Enumerable.Union%2A>örnekleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="44ae5-130">Provides examples of using <xref:System.Linq.Enumerable.Union%2A>.</span></span>  
  
 [<span data-ttu-id="44ae5-131">Diziyi (Sequence) Diziye (Array) Dönüştürme</span><span class="sxs-lookup"><span data-stu-id="44ae5-131">Convert a Sequence to an Array</span></span>](convert-a-sequence-to-an-array.md)  
 <span data-ttu-id="44ae5-132">, Kullanma <xref:System.Linq.Enumerable.ToArray%2A>örnekleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="44ae5-132">Provides examples of using <xref:System.Linq.Enumerable.ToArray%2A>.</span></span>  
  
 [<span data-ttu-id="44ae5-133">Diziyi Genel Listeye Dönüştürme</span><span class="sxs-lookup"><span data-stu-id="44ae5-133">Convert a Sequence to a Generic List</span></span>](convert-a-sequence-to-a-generic-list.md)  
 <span data-ttu-id="44ae5-134">, Kullanma <xref:System.Linq.Enumerable.ToList%2A>örnekleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="44ae5-134">Provides examples of using <xref:System.Linq.Enumerable.ToList%2A>.</span></span>  
  
 [<span data-ttu-id="44ae5-135">Türü Genel IEnumerable Öğesine Dönüştürme</span><span class="sxs-lookup"><span data-stu-id="44ae5-135">Convert a Type to a Generic IEnumerable</span></span>](convert-a-type-to-a-generic-ienumerable.md)  
 <span data-ttu-id="44ae5-136">, Kullanma <xref:System.Linq.Enumerable.AsEnumerable%2A>örnekleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="44ae5-136">Provides examples of using <xref:System.Linq.Enumerable.AsEnumerable%2A>.</span></span>  
  
 [<span data-ttu-id="44ae5-137">Birleşimler ve Çapraz Ürün Sorguları Düzenleme</span><span class="sxs-lookup"><span data-stu-id="44ae5-137">Formulate Joins and Cross-Product Queries</span></span>](formulate-joins-and-cross-product-queries.md)  
 <span data-ttu-id="44ae5-138">`from` ,`where`, Ve`select` yan tümcelerinde yabancı anahtar gezintisini kullanma örnekleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="44ae5-138">Provides examples of using foreign-key navigation in the `from`, `where`, and `select` clauses.</span></span>  
  
 [<span data-ttu-id="44ae5-139">Projeksiyonlar Düzenleme</span><span class="sxs-lookup"><span data-stu-id="44ae5-139">Formulate Projections</span></span>](formulate-projections.md)  
 <span data-ttu-id="44ae5-140">Sorgu projeksiyonlarını `select` biçimlendirmek için diğer özelliklerle birleştirme örnekleri sağlar (örneğin, *anonim türler*).</span><span class="sxs-lookup"><span data-stu-id="44ae5-140">Provides examples of combining `select` with other features (for example, *anonymous types*) to form query projections.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="44ae5-141">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="44ae5-141">Related Sections</span></span>  
 [<span data-ttu-id="44ae5-142">Standart sorgu Işleçlerine genelC#bakış ()</span><span class="sxs-lookup"><span data-stu-id="44ae5-142">Standard Query Operators Overview (C#)</span></span>](../../../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)  
 <span data-ttu-id="44ae5-143">Kullanılarak C#standart sorgu işleçleri kavramını açıklar.</span><span class="sxs-lookup"><span data-stu-id="44ae5-143">Explains the concept of standard query operators using C#.</span></span>  
  
 [<span data-ttu-id="44ae5-144">Standart sorgu Işleçlerine genel bakış (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="44ae5-144">Standard Query Operators Overview (Visual Basic)</span></span>](../../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)  
 <span data-ttu-id="44ae5-145">Visual Basic kullanan standart sorgu işleçleri kavramını açıklar.</span><span class="sxs-lookup"><span data-stu-id="44ae5-145">Explains the concept of standard query operators using Visual Basic.</span></span>  
  
 [<span data-ttu-id="44ae5-146">Sorgu Kavramları</span><span class="sxs-lookup"><span data-stu-id="44ae5-146">Query Concepts</span></span>](query-concepts.md)  
 <span data-ttu-id="44ae5-147">Sorgular için [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] uygulanan kavramların nasıl kullandığını açıklar.</span><span class="sxs-lookup"><span data-stu-id="44ae5-147">Explains how [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] uses concepts that apply to queries.</span></span>  
  
 [<span data-ttu-id="44ae5-148">Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="44ae5-148">Programming Guide</span></span>](programming-guide.md)  
 <span data-ttu-id="44ae5-149">İle [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]ilgili programlama kavramlarını açıklayan konularda bir portal sağlar.</span><span class="sxs-lookup"><span data-stu-id="44ae5-149">Provides a portal to topics that explain programming concepts related to [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span>
