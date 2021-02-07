---
description: 'Daha fazla bilgi edinin: standart sorgu Işleci çevirisi'
title: Standart Sorgu İşleci Çevirisi
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: a60c30fa-1e68-45fe-b984-f6abb9ede40e
ms.openlocfilehash: e7e45e8f27f1e7d3c572f00ea014b4edb288b2b0
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99681532"
---
# <a name="standard-query-operator-translation"></a><span data-ttu-id="48110-103">Standart Sorgu İşleci Çevirisi</span><span class="sxs-lookup"><span data-stu-id="48110-103">Standard Query Operator Translation</span></span>

[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="48110-104">Standart sorgu Işleçlerini SQL komutlarına çevirir.</span><span class="sxs-lookup"><span data-stu-id="48110-104">translates Standard Query Operators to SQL commands.</span></span> <span data-ttu-id="48110-105">Veritabanının sorgu işlemcisi SQL çevirisi 'nin yürütme semantiğini belirler.</span><span class="sxs-lookup"><span data-stu-id="48110-105">The query processor of the database determines the execution semantics of SQL translation.</span></span>

<span data-ttu-id="48110-106">Standart sorgu Işleçleri *sıralara* göre tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="48110-106">Standard Query Operators are defined against *sequences*.</span></span> <span data-ttu-id="48110-107">Bir sıra *sıralanır* ve dizideki her öğe için başvuru kimliğini kullanır.</span><span class="sxs-lookup"><span data-stu-id="48110-107">A sequence is *ordered* and relies on reference identity for each element of the sequence.</span></span> <span data-ttu-id="48110-108">Daha fazla bilgi için bkz. [Standart sorgu Işleçlerine genel bakış (C#)](../../../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md) veya [Standart sorgu işleçlerine genel bakış (Visual Basic)](../../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md).</span><span class="sxs-lookup"><span data-stu-id="48110-108">For more information, see [Standard Query Operators Overview (C#)](../../../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md) or [Standard Query Operators Overview (Visual Basic)](../../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md).</span></span>

<span data-ttu-id="48110-109">SQL, birincil olarak *sırasız değer kümeleriyle anlaşmalar yapar*.</span><span class="sxs-lookup"><span data-stu-id="48110-109">SQL deals primarily with *unordered sets of values*.</span></span> <span data-ttu-id="48110-110">Sıralama genellikle, ara sonuçlar yerine bir sorgunun nihai sonucuna uygulanan, açıkça belirtilmiş, işleme sonrası bir işlemdir.</span><span class="sxs-lookup"><span data-stu-id="48110-110">Ordering is typically an explicitly stated, post-processing operation that is applied to the final result of a query rather than to intermediate results.</span></span> <span data-ttu-id="48110-111">Kimlik, değerler tarafından tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="48110-111">Identity is defined by values.</span></span> <span data-ttu-id="48110-112">Bu nedenle SQL sorguları, *kümeler* yerine çoklu kümeler (*bAdım*) ile uğraşmak üzere anlaşılmıştır.</span><span class="sxs-lookup"><span data-stu-id="48110-112">For this reason, SQL queries are understood to deal with multisets (*bags*) instead of *sets*.</span></span>

<span data-ttu-id="48110-113">Aşağıdaki paragraflarda, için SQL Server sağlayıcısı için standart sorgu Işleçleri ve SQL çevirisi arasındaki farklılıklar açıklanır [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="48110-113">The following paragraphs describe the differences between the Standard Query Operators and their SQL translation for the SQL Server provider for [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span>

## <a name="operator-support"></a><span data-ttu-id="48110-114">İşleç desteği</span><span class="sxs-lookup"><span data-stu-id="48110-114">Operator Support</span></span>

### <a name="concat"></a><span data-ttu-id="48110-115">Concat</span><span class="sxs-lookup"><span data-stu-id="48110-115">Concat</span></span>

<span data-ttu-id="48110-116"><xref:System.Linq.Enumerable.Concat%2A>Yöntemi, alıcı sırasının ve bağımsız değişkenin sırası aynı olduğu sıralı çoklu kümeler için tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="48110-116">The <xref:System.Linq.Enumerable.Concat%2A> method is defined for ordered multisets where the order of the receiver and the order of the argument are the same.</span></span> <span data-ttu-id="48110-117"><xref:System.Linq.Enumerable.Concat%2A>`UNION ALL`Çoklu kümeler üzerinde olduğu gibi çalışarak ortak sıra kullanılır.</span><span class="sxs-lookup"><span data-stu-id="48110-117"><xref:System.Linq.Enumerable.Concat%2A> works as `UNION ALL` over the multisets followed by the common order.</span></span>

<span data-ttu-id="48110-118">Son adım, sonuçlar üretilmadan önce SQL 'de sıralamaktır.</span><span class="sxs-lookup"><span data-stu-id="48110-118">The final step is ordering in SQL before results are produced.</span></span> <span data-ttu-id="48110-119"><xref:System.Linq.Enumerable.Concat%2A> bağımsız değişkenlerinin sırasını korumaz.</span><span class="sxs-lookup"><span data-stu-id="48110-119"><xref:System.Linq.Enumerable.Concat%2A> does not preserve the order of its arguments.</span></span> <span data-ttu-id="48110-120">Uygun sıralamayı sağlamak için, sonuçlarını açıkça sipariş etmeniz gerekir <xref:System.Linq.Enumerable.Concat%2A> .</span><span class="sxs-lookup"><span data-stu-id="48110-120">To ensure appropriate ordering, you must explicitly order the results of <xref:System.Linq.Enumerable.Concat%2A>.</span></span>

### <a name="intersect-except-union"></a><span data-ttu-id="48110-121">Intersect, Except, birleşim</span><span class="sxs-lookup"><span data-stu-id="48110-121">Intersect, Except, Union</span></span>

<span data-ttu-id="48110-122"><xref:System.Linq.Enumerable.Intersect%2A>Ve <xref:System.Linq.Enumerable.Except%2A> yöntemleri yalnızca kümeler üzerinde iyi tanımlanmış.</span><span class="sxs-lookup"><span data-stu-id="48110-122">The <xref:System.Linq.Enumerable.Intersect%2A> and <xref:System.Linq.Enumerable.Except%2A> methods are well defined only on sets.</span></span> <span data-ttu-id="48110-123">Multisets semantiği tanımsızdır.</span><span class="sxs-lookup"><span data-stu-id="48110-123">The semantics for multisets is undefined.</span></span>

<span data-ttu-id="48110-124">Yöntemi multisets 'ler <xref:System.Linq.Enumerable.Union%2A> için, birden çok küme için tanımlanır (SQL 'DEKI UNıON ALL yan tümcesinin sonucu etkin değildir).</span><span class="sxs-lookup"><span data-stu-id="48110-124">The <xref:System.Linq.Enumerable.Union%2A> method is defined for multisets as the unordered concatenation of the multisets (effectively the result of the UNION ALL clause in SQL).</span></span>

### <a name="take-skip"></a><span data-ttu-id="48110-125">Al, atla</span><span class="sxs-lookup"><span data-stu-id="48110-125">Take, Skip</span></span>

<span data-ttu-id="48110-126"><xref:System.Linq.Enumerable.Take%2A> ve <xref:System.Linq.Enumerable.Skip%2A> yöntemleri yalnızca *sıralı kümelere* karşı iyi tanımlanmış.</span><span class="sxs-lookup"><span data-stu-id="48110-126"><xref:System.Linq.Enumerable.Take%2A> and <xref:System.Linq.Enumerable.Skip%2A> methods are well defined only against *ordered sets*.</span></span> <span data-ttu-id="48110-127">Sıralanmamış kümeler veya birden çok küme semantiği tanımsızdır.</span><span class="sxs-lookup"><span data-stu-id="48110-127">The semantics for unordered sets or multisets are undefined.</span></span>

> [!NOTE]
> <span data-ttu-id="48110-128"><xref:System.Linq.Enumerable.Take%2A> ve <xref:System.Linq.Enumerable.Skip%2A> SQL Server 2000 ' de sorgularda kullanıldıkları bazı sınırlamalar vardır.</span><span class="sxs-lookup"><span data-stu-id="48110-128"><xref:System.Linq.Enumerable.Take%2A> and <xref:System.Linq.Enumerable.Skip%2A> have certain limitations when they are used in queries against SQL Server 2000.</span></span> <span data-ttu-id="48110-129">Daha fazla bilgi için bkz. [sorun giderme](troubleshooting.md)içindeki "SQL Server 2000 'de özel durumları atla ve al" girişi.</span><span class="sxs-lookup"><span data-stu-id="48110-129">For more information, see the "Skip and Take Exceptions in SQL Server 2000" entry in [Troubleshooting](troubleshooting.md).</span></span>

<span data-ttu-id="48110-130">SQL 'de sıralamaya yönelik sınırlamalar nedeniyle, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] Bu yöntemlerin bağımsız değişkeninin sıralamasını yöntemin sonucuna taşımaya çalışır.</span><span class="sxs-lookup"><span data-stu-id="48110-130">Because of limitations on ordering in SQL, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] tries to move the ordering of the argument of these methods to the result of the method.</span></span> <span data-ttu-id="48110-131">Örneğin, aşağıdaki sorguyu göz önünde bulundurun [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] :</span><span class="sxs-lookup"><span data-stu-id="48110-131">For example, consider the following [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] query:</span></span>

[!code-csharp[DLinqSQOTranslation#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSQOTranslation/cs/Program.cs#1)]
[!code-vb[DLinqSQOTranslation#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSQOTranslation/vb/Module1.vb#1)]

<span data-ttu-id="48110-132">Bu kod için oluşturulan SQL, aşağıdaki gibi sıralamayı sonuna taşıdır:</span><span class="sxs-lookup"><span data-stu-id="48110-132">The generated SQL for this code moves the ordering to the end, as follows:</span></span>

```sql
SELECT TOP 1 [t0].[CustomerID], [t0].[CompanyName],
FROM [Customers] AS [t0]
WHERE (NOT (EXISTS(
    SELECT NULL AS [EMPTY]
    FROM (
        SELECT TOP 1 [t1].[CustomerID]
        FROM [Customers] AS [t1]
        WHERE [t1].[City] = @p0
        ORDER BY [t1].[CustomerID]
        ) AS [t2]
    WHERE [t0].[CustomerID] = [t2].[CustomerID]
    ))) AND ([t0].[City] = @p1)
ORDER BY [t0].[CustomerID]
```

<span data-ttu-id="48110-133">Belirtilen tüm sıralama, <xref:System.Linq.Enumerable.Take%2A> ve birlikte zincirleme zaman tutarlı hale gelmelidir <xref:System.Linq.Enumerable.Skip%2A> .</span><span class="sxs-lookup"><span data-stu-id="48110-133">It becomes obvious that all the specified ordering must be consistent when <xref:System.Linq.Enumerable.Take%2A> and <xref:System.Linq.Enumerable.Skip%2A> are chained together.</span></span> <span data-ttu-id="48110-134">Aksi takdirde, sonuçlar tanımsızdır.</span><span class="sxs-lookup"><span data-stu-id="48110-134">Otherwise, the results are undefined.</span></span>

<span data-ttu-id="48110-135">Her ikisi de <xref:System.Linq.Enumerable.Take%2A> <xref:System.Linq.Enumerable.Skip%2A> , standart sorgu işleci belirtimine göre negatif olmayan, sabit tamsayı bağımsız değişkenleri için iyi tanımlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="48110-135">Both <xref:System.Linq.Enumerable.Take%2A> and <xref:System.Linq.Enumerable.Skip%2A> are well-defined for non-negative, constant integral arguments based on the Standard Query Operator specification.</span></span>

### <a name="operators-with-no-translation"></a><span data-ttu-id="48110-136">Çevirisi olmayan işleçler</span><span class="sxs-lookup"><span data-stu-id="48110-136">Operators with No Translation</span></span>

<span data-ttu-id="48110-137">Aşağıdaki yöntemler tarafından çevrilmez [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="48110-137">The following methods are not translated by [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span> <span data-ttu-id="48110-138">En yaygın neden, sıralanmamış çoklu kümeler ve diziler arasındaki farktır.</span><span class="sxs-lookup"><span data-stu-id="48110-138">The most common reason is the difference between unordered multisets and sequences.</span></span>

|<span data-ttu-id="48110-139">İşleçler</span><span class="sxs-lookup"><span data-stu-id="48110-139">Operators</span></span>|<span data-ttu-id="48110-140">Mantığı anladığınızdan</span><span class="sxs-lookup"><span data-stu-id="48110-140">Rationale</span></span>|
|---------------|---------------|
|<span data-ttu-id="48110-141"><xref:System.Linq.Enumerable.TakeWhile%2A>, <xref:System.Linq.Enumerable.SkipWhile%2A></span><span class="sxs-lookup"><span data-stu-id="48110-141"><xref:System.Linq.Enumerable.TakeWhile%2A>, <xref:System.Linq.Enumerable.SkipWhile%2A></span></span>|<span data-ttu-id="48110-142">SQL sorguları diziler üzerinde değil, çoklu kümeler üzerinde çalışır.</span><span class="sxs-lookup"><span data-stu-id="48110-142">SQL queries operate on multisets, not on sequences.</span></span> <span data-ttu-id="48110-143">`ORDER BY` sonuçlara uygulanan son yan tümce olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="48110-143">`ORDER BY` must be the last clause applied to the results.</span></span> <span data-ttu-id="48110-144">Bu nedenle, bu iki yöntem için genel amaçlı bir çeviri yoktur.</span><span class="sxs-lookup"><span data-stu-id="48110-144">For this reason, there is no general-purpose translation for these two methods.</span></span>|
|<xref:System.Linq.Enumerable.Reverse%2A>|<span data-ttu-id="48110-145">Bu yöntemin çevirisi, sıralı bir küme için mümkündür ancak şu anda tarafından çevrilmez [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="48110-145">Translation of this method is possible for an ordered set but is not currently translated by [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span>|
|<span data-ttu-id="48110-146"><xref:System.Linq.Enumerable.Last%2A>, <xref:System.Linq.Enumerable.LastOrDefault%2A></span><span class="sxs-lookup"><span data-stu-id="48110-146"><xref:System.Linq.Enumerable.Last%2A>, <xref:System.Linq.Enumerable.LastOrDefault%2A></span></span>|<span data-ttu-id="48110-147">Bu yöntemlerin çevirisi, sıralı bir küme için mümkündür ancak şu anda tarafından çevrilmez [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="48110-147">Translation of these methods is possible for an ordered set but is not currently translated by [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span>|
|<span data-ttu-id="48110-148"><xref:System.Linq.Enumerable.ElementAt%2A>, <xref:System.Linq.Enumerable.ElementAtOrDefault%2A></span><span class="sxs-lookup"><span data-stu-id="48110-148"><xref:System.Linq.Enumerable.ElementAt%2A>, <xref:System.Linq.Enumerable.ElementAtOrDefault%2A></span></span>|<span data-ttu-id="48110-149">SQL sorguları, dizine eklenebilir diziler üzerinde değil, çoklu kümeler üzerinde çalışır.</span><span class="sxs-lookup"><span data-stu-id="48110-149">SQL queries operate on multisets, not on indexable sequences.</span></span>|
|<span data-ttu-id="48110-150"><xref:System.Linq.Enumerable.DefaultIfEmpty%2A> (varsayılan bağımsız değişken ile aşırı yükleme)</span><span class="sxs-lookup"><span data-stu-id="48110-150"><xref:System.Linq.Enumerable.DefaultIfEmpty%2A> (overload with default arg)</span></span>|<span data-ttu-id="48110-151">Genel olarak, rastgele bir tanımlama grubu için varsayılan bir değer belirtilemez.</span><span class="sxs-lookup"><span data-stu-id="48110-151">In general, a default value cannot be specified for an arbitrary tuple.</span></span> <span data-ttu-id="48110-152">Dış birleştirmeler aracılığıyla bazı durumlarda, diziler için null değerler mümkündür.</span><span class="sxs-lookup"><span data-stu-id="48110-152">Null values for tuples are possible in some cases through outer joins.</span></span>|

## <a name="expression-translation"></a><span data-ttu-id="48110-153">İfade çevirisi</span><span class="sxs-lookup"><span data-stu-id="48110-153">Expression Translation</span></span>

### <a name="null-semantics"></a><span data-ttu-id="48110-154">Null semantiği</span><span class="sxs-lookup"><span data-stu-id="48110-154">Null semantics</span></span>

[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="48110-155">SQL 'de null karşılaştırma semantiğini uygulamaz.</span><span class="sxs-lookup"><span data-stu-id="48110-155">does not impose null comparison semantics on SQL.</span></span> <span data-ttu-id="48110-156">Karşılaştırma işleçleri, sözdizimsel olarak SQL eşdeğerlerine çevrilir.</span><span class="sxs-lookup"><span data-stu-id="48110-156">Comparison operators are syntactically translated to their SQL equivalents.</span></span> <span data-ttu-id="48110-157">Bu nedenle, semantik, sunucu veya bağlantı ayarları tarafından tanımlanan SQL semantiğini yansıtır.</span><span class="sxs-lookup"><span data-stu-id="48110-157">For this reason, the semantics reflect SQL semantics that are defined by server or connection settings.</span></span> <span data-ttu-id="48110-158">Örneğin, iki null değer varsayılan SQL Server ayarları altında eşit olarak değerlendirilir, ancak semantiğini değiştirmek için ayarları değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="48110-158">For example, two null values are considered unequal under default SQL Server settings, but you can change the settings to change the semantics.</span></span> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="48110-159">sorguları çevirdiğinde sunucu ayarlarını dikkate almaz.</span><span class="sxs-lookup"><span data-stu-id="48110-159">does not consider server settings when it translates queries.</span></span>

<span data-ttu-id="48110-160">Null değerli bir karşılaştırma, uygun SQL sürümüne ( `is null` veya `is not null` ) çevrilir.</span><span class="sxs-lookup"><span data-stu-id="48110-160">A comparison with the literal null is translated to the appropriate SQL version (`is null` or `is not null`).</span></span>

<span data-ttu-id="48110-161">`null`Harmanlama içindeki değeri SQL Server tarafından tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="48110-161">The value of `null` in collation is defined by SQL Server.</span></span> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="48110-162">harmanlamayı değiştirmez.</span><span class="sxs-lookup"><span data-stu-id="48110-162">does not change the collation.</span></span>

### <a name="aggregates"></a><span data-ttu-id="48110-163">Toplamalar</span><span class="sxs-lookup"><span data-stu-id="48110-163">Aggregates</span></span>

<span data-ttu-id="48110-164">Standart sorgu Işleci toplama yöntemi <xref:System.Linq.Enumerable.Sum%2A> boş bir sıra veya yalnızca null değer içeren bir sıra için sıfır olarak değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="48110-164">The Standard Query Operator aggregate method <xref:System.Linq.Enumerable.Sum%2A> evaluates to zero for an empty sequence or for a sequence that contains only nulls.</span></span> <span data-ttu-id="48110-165">[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]' De, SQL 'in semantiği değişmeden bırakılır ve boş bir <xref:System.Linq.Enumerable.Sum%2A> `null` sıra veya yalnızca null değerleri içeren bir sıra için sıfır yerine olarak değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="48110-165">In [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], the semantics of SQL are left unchanged, and <xref:System.Linq.Enumerable.Sum%2A> evaluates to `null` instead of zero for an empty sequence or for a sequence that contains only nulls.</span></span>

<span data-ttu-id="48110-166">Ara sonuçlarda SQL sınırlamaları, içindeki toplamalar için geçerlidir [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="48110-166">SQL limitations on intermediate results apply to aggregates in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span> <span data-ttu-id="48110-167"><xref:System.Linq.Enumerable.Sum%2A>32 bitlik tamsayı miktarları 64 bit sonuçlar kullanılarak hesaplanmaz.</span><span class="sxs-lookup"><span data-stu-id="48110-167">The <xref:System.Linq.Enumerable.Sum%2A> of 32-bit integer quantities is not computed by using 64-bit results.</span></span> <span data-ttu-id="48110-168">[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Linq.Enumerable.Sum%2A> Standart sorgu işleci uygulamasının karşılık gelen bellek içi dizide taşma olmasına neden olmasa bile, bir çevirisi için taşma gerçekleşebilir.</span><span class="sxs-lookup"><span data-stu-id="48110-168">Overflow might occur for a [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] translation of <xref:System.Linq.Enumerable.Sum%2A>, even if the Standard Query Operator implementation does not cause an overflow for the corresponding in-memory sequence.</span></span>

<span data-ttu-id="48110-169">Benzer şekilde, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Linq.Enumerable.Average%2A> tamsayı değerlerinin çevirisi bir olarak değil bir olarak hesaplanır `integer` `double` .</span><span class="sxs-lookup"><span data-stu-id="48110-169">Likewise, the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] translation of <xref:System.Linq.Enumerable.Average%2A> of integer values is computed as an `integer`, not as a `double`.</span></span>

### <a name="entity-arguments"></a><span data-ttu-id="48110-170">Varlık bağımsız değişkenleri</span><span class="sxs-lookup"><span data-stu-id="48110-170">Entity Arguments</span></span>

[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="48110-171">, ve yöntemlerinde varlık türlerinin kullanılmasını sağlar <xref:System.Linq.Enumerable.GroupBy%2A> <xref:System.Linq.Enumerable.OrderBy%2A> .</span><span class="sxs-lookup"><span data-stu-id="48110-171">enables entity types to be used in the <xref:System.Linq.Enumerable.GroupBy%2A> and <xref:System.Linq.Enumerable.OrderBy%2A> methods.</span></span> <span data-ttu-id="48110-172">Bu işleçlerin çevirisinde, bir türün bağımsız değişkeninin kullanımı, bu türün tüm üyelerini belirtmeye eşdeğer olarak kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="48110-172">In the translation of these operators, the use of an argument of a type is considered to be the equivalent to specifying all members of that type.</span></span> <span data-ttu-id="48110-173">Örneğin, aşağıdaki kod eşdeğerdir:</span><span class="sxs-lookup"><span data-stu-id="48110-173">For example, the following code is equivalent:</span></span>

[!code-csharp[DLinqSQOTranslation#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSQOTranslation/cs/Program.cs#2)]
[!code-vb[DLinqSQOTranslation#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSQOTranslation/vb/Module1.vb#2)]

### <a name="equatable--comparable-arguments"></a><span data-ttu-id="48110-174">Equatable/karşılaştırılabilir bağımsız değişkenler</span><span class="sxs-lookup"><span data-stu-id="48110-174">Equatable / Comparable Arguments</span></span>

<span data-ttu-id="48110-175">Aşağıdaki yöntemlerin uygulanmasında bağımsız değişkenlerin eşitliği gereklidir:</span><span class="sxs-lookup"><span data-stu-id="48110-175">Equality of arguments is required in the implementation of the following methods:</span></span>

- <xref:System.Linq.Enumerable.Contains%2A>

- <xref:System.Linq.Enumerable.Skip%2A>

- <xref:System.Linq.Enumerable.Union%2A>

- <xref:System.Linq.Enumerable.Intersect%2A>

- <xref:System.Linq.Enumerable.Except%2A>

[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="48110-176">*düz* bağımsız değişkenler için eşitlik ve karşılaştırmayı destekler, ancak dizileri olan veya içeren bağımsız değişkenler için değildir.</span><span class="sxs-lookup"><span data-stu-id="48110-176">supports equality and comparison for *flat* arguments, but not for arguments that are or contain sequences.</span></span> <span data-ttu-id="48110-177">Düz bir bağımsız değişken, bir SQL satırına eşlenebilir bir türdür.</span><span class="sxs-lookup"><span data-stu-id="48110-177">A flat argument is a type that can be mapped to a SQL row.</span></span> <span data-ttu-id="48110-178">Statik olarak belirlenebileceği bir veya daha fazla varlık türünün projeksiyonu düz bir bağımsız değişken olarak kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="48110-178">A projection of one or more entity types that can be statically determined not to contain a sequence is considered a flat argument.</span></span>

<span data-ttu-id="48110-179">Düz bağımsız değişkenlerin örnekleri aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="48110-179">The following are examples of flat arguments:</span></span>

[!code-csharp[DLinqSQOTranslation#3](~/samples/snippets/csharp/VS_Snippets_Data/DLinqSQOTranslation/cs/Program.cs#3)]
[!code-vb[DLinqSQOTranslation#3](~/samples/snippets/visualbasic/VS_Snippets_Data/DLinqSQOTranslation/vb/Module1.vb#3)]

<span data-ttu-id="48110-180">Aşağıda, düz olmayan (hiyerarşik) bağımsız değişkenlerin örnekleri verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="48110-180">The following are examples of non-flat (hierarchical) arguments:</span></span>

[!code-csharp[DLinqSQOTranslation#4](~/samples/snippets/csharp/VS_Snippets_Data/DLinqSQOTranslation/cs/Program.cs#4)]
[!code-vb[DLinqSQOTranslation#4](~/samples/snippets/visualbasic/VS_Snippets_Data/DLinqSQOTranslation/vb/Module1.vb#4)]

### <a name="visual-basic-function-translation"></a><span data-ttu-id="48110-181">Visual Basic Işlev çevirisi</span><span class="sxs-lookup"><span data-stu-id="48110-181">Visual Basic Function Translation</span></span>

<span data-ttu-id="48110-182">Visual Basic Derleyicisi tarafından kullanılan aşağıdaki yardımcı işlevler, karşılık gelen SQL işleçleri ve işlevlerine çevrilir:</span><span class="sxs-lookup"><span data-stu-id="48110-182">The following helper functions that are used by the Visual Basic compiler are translated to corresponding SQL operators and functions:</span></span>

- `CompareString`

- `DateTime.Compare`

- `Decimal.Compare`

- `IIf (in Microsoft.VisualBasic.Interaction)`

<span data-ttu-id="48110-183">Dönüştürme yöntemleri:</span><span class="sxs-lookup"><span data-stu-id="48110-183">Conversion methods:</span></span>

|||||
|-|-|-|-|
|<span data-ttu-id="48110-184">ToBoolean</span><span class="sxs-lookup"><span data-stu-id="48110-184">ToBoolean</span></span>|<span data-ttu-id="48110-185">ToSByte</span><span class="sxs-lookup"><span data-stu-id="48110-185">ToSByte</span></span>|<span data-ttu-id="48110-186">ToByte</span><span class="sxs-lookup"><span data-stu-id="48110-186">ToByte</span></span>|<span data-ttu-id="48110-187">ToChar</span><span class="sxs-lookup"><span data-stu-id="48110-187">ToChar</span></span>|
|<span data-ttu-id="48110-188">ToCharArrayRankOne</span><span class="sxs-lookup"><span data-stu-id="48110-188">ToCharArrayRankOne</span></span>|<span data-ttu-id="48110-189">ToDate</span><span class="sxs-lookup"><span data-stu-id="48110-189">ToDate</span></span>|<span data-ttu-id="48110-190">ToDecimal</span><span class="sxs-lookup"><span data-stu-id="48110-190">ToDecimal</span></span>|<span data-ttu-id="48110-191">ToDouble</span><span class="sxs-lookup"><span data-stu-id="48110-191">ToDouble</span></span>|
|<span data-ttu-id="48110-192">ToInteger</span><span class="sxs-lookup"><span data-stu-id="48110-192">ToInteger</span></span>|<span data-ttu-id="48110-193">ToUInteger</span><span class="sxs-lookup"><span data-stu-id="48110-193">ToUInteger</span></span>|<span data-ttu-id="48110-194">ToLong</span><span class="sxs-lookup"><span data-stu-id="48110-194">ToLong</span></span>|<span data-ttu-id="48110-195">ToULong</span><span class="sxs-lookup"><span data-stu-id="48110-195">ToULong</span></span>|
|<span data-ttu-id="48110-196">ToShort</span><span class="sxs-lookup"><span data-stu-id="48110-196">ToShort</span></span>|<span data-ttu-id="48110-197">ToUShort</span><span class="sxs-lookup"><span data-stu-id="48110-197">ToUShort</span></span>|<span data-ttu-id="48110-198">ToSingle</span><span class="sxs-lookup"><span data-stu-id="48110-198">ToSingle</span></span>|<span data-ttu-id="48110-199">ToString</span><span class="sxs-lookup"><span data-stu-id="48110-199">ToString</span></span>|

## <a name="inheritance-support"></a><span data-ttu-id="48110-200">Devralma Desteği</span><span class="sxs-lookup"><span data-stu-id="48110-200">Inheritance Support</span></span>

### <a name="inheritance-mapping-restrictions"></a><span data-ttu-id="48110-201">Devralma eşleme kısıtlamaları</span><span class="sxs-lookup"><span data-stu-id="48110-201">Inheritance Mapping Restrictions</span></span>

<span data-ttu-id="48110-202">Daha fazla bilgi için bkz. [nasıl yapılır: harita devralma hiyerarşileri](how-to-map-inheritance-hierarchies.md).</span><span class="sxs-lookup"><span data-stu-id="48110-202">For more information, see [How to: Map Inheritance Hierarchies](how-to-map-inheritance-hierarchies.md).</span></span>

### <a name="inheritance-in-queries"></a><span data-ttu-id="48110-203">Sorgularda devralma</span><span class="sxs-lookup"><span data-stu-id="48110-203">Inheritance in Queries</span></span>

<span data-ttu-id="48110-204">C# yayınları yalnızca projeksiyde desteklenir.</span><span class="sxs-lookup"><span data-stu-id="48110-204">C# casts are supported only in projection.</span></span> <span data-ttu-id="48110-205">Başka bir yerde kullanılan yayınlar çevrilmez ve yok sayılır.</span><span class="sxs-lookup"><span data-stu-id="48110-205">Casts that are used elsewhere are not translated and are ignored.</span></span> <span data-ttu-id="48110-206">SQL işlev adlarından de, SQL aslında yalnızca ortak dil çalışma zamanının (CLR) eşdeğerini uygular <xref:System.Convert> .</span><span class="sxs-lookup"><span data-stu-id="48110-206">Aside from SQL function names, SQL really only performs the equivalent of the common language runtime (CLR) <xref:System.Convert>.</span></span> <span data-ttu-id="48110-207">Diğer bir deyişle, SQL bir tür değerini başka bir türe değiştirebilir.</span><span class="sxs-lookup"><span data-stu-id="48110-207">That is, SQL can change the value of one type to another.</span></span> <span data-ttu-id="48110-208">Başka bir türden farklı bitleri yeniden yorumlama kavramı olmadığından, CLR cast ' ın eşdeğeri yoktur.</span><span class="sxs-lookup"><span data-stu-id="48110-208">There is no equivalent of CLR cast because there is no concept of reinterpreting the same bits as those of another type.</span></span> <span data-ttu-id="48110-209">Bunun nedeni, C# cast işlevinin yalnızca yerel olarak çalışmasına neden olur.</span><span class="sxs-lookup"><span data-stu-id="48110-209">That is why a C# cast works only locally.</span></span> <span data-ttu-id="48110-210">Bu uzak değildir.</span><span class="sxs-lookup"><span data-stu-id="48110-210">It is not remoted.</span></span>

<span data-ttu-id="48110-211">İşleçleri, `is` ve `as` ve yöntemi işleçle `GetType` kısıtlanmaz `Select` .</span><span class="sxs-lookup"><span data-stu-id="48110-211">The operators, `is` and `as`, and the `GetType` method are not restricted to the `Select` operator.</span></span> <span data-ttu-id="48110-212">Bunlar aynı zamanda diğer sorgu işleçleri içinde de kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="48110-212">They can be used in other query operators also.</span></span>

## <a name="sql-server-2008-support"></a><span data-ttu-id="48110-213">SQL Server 2008 desteği</span><span class="sxs-lookup"><span data-stu-id="48110-213">SQL Server 2008 Support</span></span>

<span data-ttu-id="48110-214">.NET Framework 3,5 SP1 ile başlayarak LINQ to SQL, SQL Server 2008 ile tanıtılan yeni tarih ve saat türleriyle eşlemeyi destekler.</span><span class="sxs-lookup"><span data-stu-id="48110-214">Starting with the .NET Framework 3.5 SP1, LINQ to SQL supports mapping to new date and time types introduced with SQL Server 2008.</span></span> <span data-ttu-id="48110-215">Ancak, bu yeni türlere eşlenen değerlere karşı çalışırken kullanabileceğiniz LINQ to SQL sorgu işleçleri için bazı sınırlamalar vardır.</span><span class="sxs-lookup"><span data-stu-id="48110-215">But, there are some limitations to the LINQ to SQL query operators that you can use when operating against values mapped to these new types.</span></span>

### <a name="unsupported-query-operators"></a><span data-ttu-id="48110-216">Desteklenmeyen sorgu Işleçleri</span><span class="sxs-lookup"><span data-stu-id="48110-216">Unsupported Query Operators</span></span>

<span data-ttu-id="48110-217">Aşağıdaki sorgu işleçleri, yeni SQL Server Tarih ve saat türleriyle eşlenen değerlerde desteklenmez: `DATETIME2` , `DATE` , `TIME` , ve `DATETIMEOFFSET` .</span><span class="sxs-lookup"><span data-stu-id="48110-217">The following query operators are not supported on values mapped to the new SQL Server date and time types: `DATETIME2`, `DATE`, `TIME`, and `DATETIMEOFFSET`.</span></span>

- `Aggregate`

- `Average`

- `LastOrDefault`

- `OfType`

- `Sum`

<span data-ttu-id="48110-218">Bu SQL Server Tarih ve saat türleriyle eşleştirme hakkında daha fazla bilgi için bkz. [SQL-CLR tür eşleme](sql-clr-type-mapping.md).</span><span class="sxs-lookup"><span data-stu-id="48110-218">For more information about mapping to these SQL Server date and time types, see [SQL-CLR Type Mapping](sql-clr-type-mapping.md).</span></span>

## <a name="sql-server-2005-support"></a><span data-ttu-id="48110-219">SQL Server 2005 desteği</span><span class="sxs-lookup"><span data-stu-id="48110-219">SQL Server 2005 Support</span></span>

[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="48110-220">, aşağıdaki SQL Server 2005 özelliklerini desteklemez:</span><span class="sxs-lookup"><span data-stu-id="48110-220">does not support the following SQL Server 2005 features:</span></span>

- <span data-ttu-id="48110-221">SQL CLR için yazılan saklı yordamlar.</span><span class="sxs-lookup"><span data-stu-id="48110-221">Stored procedures written for SQL CLR.</span></span>

- <span data-ttu-id="48110-222">Kullanıcı tanımlı tür.</span><span class="sxs-lookup"><span data-stu-id="48110-222">User-defined type.</span></span>

- <span data-ttu-id="48110-223">XML sorgu özellikleri.</span><span class="sxs-lookup"><span data-stu-id="48110-223">XML query features.</span></span>

## <a name="sql-server-2000-support"></a><span data-ttu-id="48110-224">SQL Server 2000 desteği</span><span class="sxs-lookup"><span data-stu-id="48110-224">SQL Server 2000 Support</span></span>

<span data-ttu-id="48110-225">Aşağıdaki SQL Server 2000 sınırlamaları (Microsoft SQL Server 2005 ile karşılaştırıldığında) desteği etkiler [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="48110-225">The following SQL Server 2000 limitations (compared to Microsoft SQL Server 2005) affect [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] support.</span></span>

### <a name="cross-apply-and-outer-apply-operators"></a><span data-ttu-id="48110-226">Çapraz uygulama ve dış uygulama Işleçleri</span><span class="sxs-lookup"><span data-stu-id="48110-226">Cross Apply and Outer Apply Operators</span></span>

<span data-ttu-id="48110-227">Bu işleçler SQL Server 2000 ' de kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="48110-227">These operators are not available in SQL Server 2000.</span></span> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="48110-228">uygun birleştirmelere göre değiştirmek için bir dizi yeniden yazmaya çalışır.</span><span class="sxs-lookup"><span data-stu-id="48110-228">tries a series of rewrites to replace them with appropriate joins.</span></span>

<span data-ttu-id="48110-229">`Cross Apply` ve `Outer Apply` ilişki gezginlerini için oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="48110-229">`Cross Apply` and `Outer Apply` are generated for relationship navigations.</span></span> <span data-ttu-id="48110-230">Bu tür yeniden yazar mümkün olan sorgu kümesi iyi tanımlanmamıştır.</span><span class="sxs-lookup"><span data-stu-id="48110-230">The set of queries for which such rewrites are possible is not well defined.</span></span> <span data-ttu-id="48110-231">Bu nedenle, SQL Server 2000 için desteklenen minimum sorgu kümesi ilişki gezintisi içermeyen bir kümesidir.</span><span class="sxs-lookup"><span data-stu-id="48110-231">For this reason, the minimal set of queries that is supported for SQL Server 2000 is the set that does not involve relationship navigation.</span></span>

### <a name="text--ntext"></a><span data-ttu-id="48110-232">Text/ntext</span><span class="sxs-lookup"><span data-stu-id="48110-232">text / ntext</span></span>

<span data-ttu-id="48110-233">Veri türleri `text`  /  `ntext` `varchar(max)`  /  `nvarchar(max)` , Microsoft SQL Server 2005 tarafından desteklenen belirli sorgu işlemlerinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="48110-233">Data types `text` / `ntext` cannot be used in certain query operations against `varchar(max)` / `nvarchar(max)`, which are supported by Microsoft SQL Server 2005.</span></span>

<span data-ttu-id="48110-234">Bu sınırlama için hiçbir çözüm yok.</span><span class="sxs-lookup"><span data-stu-id="48110-234">No resolution is available for this limitation.</span></span> <span data-ttu-id="48110-235">Özellikle, `Distinct()` veya sütunlarına eşlenen Üyeler içeren herhangi bir sonuç üzerinde kullanamazsınız `text` `ntext` .</span><span class="sxs-lookup"><span data-stu-id="48110-235">Specifically, you cannot use `Distinct()` on any result that contains members that are mapped to `text` or `ntext` columns.</span></span>

### <a name="behavior-triggered-by-nested-queries"></a><span data-ttu-id="48110-236">Iç Içe geçmiş sorgular tarafından tetiklenen davranış</span><span class="sxs-lookup"><span data-stu-id="48110-236">Behavior Triggered by Nested Queries</span></span>

<span data-ttu-id="48110-237">SQL Server 2000 (SP4) bağlayıcı, iç içe geçmiş sorgular tarafından tetiklenen bazı idosynyenilere sahiptir.</span><span class="sxs-lookup"><span data-stu-id="48110-237">SQL Server 2000 (through SP4) binder has some idiosyncrasies that are triggered by nested queries.</span></span> <span data-ttu-id="48110-238">Bu deyimi tetikleyen SQL sorguları kümesi iyi tanımlanmamıştır.</span><span class="sxs-lookup"><span data-stu-id="48110-238">The set of SQL queries that triggers these idiosyncrasies is not well defined.</span></span> <span data-ttu-id="48110-239">Bu nedenle, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] SQL Server özel durumlara neden olabilecek sorgu kümesini tanımlayamazsınız.</span><span class="sxs-lookup"><span data-stu-id="48110-239">For this reason, you cannot define the set of [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] queries that might cause SQL Server exceptions.</span></span>

### <a name="skip-and-take-operators"></a><span data-ttu-id="48110-240">Atla ve Al Işleçleri</span><span class="sxs-lookup"><span data-stu-id="48110-240">Skip and Take Operators</span></span>

<span data-ttu-id="48110-241"><xref:System.Linq.Enumerable.Take%2A> ve <xref:System.Linq.Enumerable.Skip%2A> SQL Server 2000 ' de sorgularda kullanıldıkları bazı sınırlamalar vardır.</span><span class="sxs-lookup"><span data-stu-id="48110-241"><xref:System.Linq.Enumerable.Take%2A> and <xref:System.Linq.Enumerable.Skip%2A> have certain limitations when they are used in queries against SQL Server 2000.</span></span> <span data-ttu-id="48110-242">Daha fazla bilgi için bkz. [sorun giderme](troubleshooting.md)içindeki "SQL Server 2000 'de özel durumları atla ve al" girişi.</span><span class="sxs-lookup"><span data-stu-id="48110-242">For more information, see the "Skip and Take Exceptions in SQL Server 2000" entry in [Troubleshooting](troubleshooting.md).</span></span>

## <a name="object-materialization"></a><span data-ttu-id="48110-243">Nesne Gerçekleştirme</span><span class="sxs-lookup"><span data-stu-id="48110-243">Object Materialization</span></span>

<span data-ttu-id="48110-244">Materialization bir veya daha fazla SQL sorgusu tarafından döndürülen satırlardan CLR nesneleri oluşturur.</span><span class="sxs-lookup"><span data-stu-id="48110-244">Materialization creates CLR objects from rows that are returned by one or more SQL queries.</span></span>

- <span data-ttu-id="48110-245">Aşağıdaki çağrılar, materialization 'ın bir parçası olarak *yerel olarak yürütülür* :</span><span class="sxs-lookup"><span data-stu-id="48110-245">The following calls are *executed locally* as a part of materialization:</span></span>

  - <span data-ttu-id="48110-246">Oluşturucular</span><span class="sxs-lookup"><span data-stu-id="48110-246">Constructors</span></span>

  - <span data-ttu-id="48110-247">`ToString` projeksiylerdeki Yöntemler</span><span class="sxs-lookup"><span data-stu-id="48110-247">`ToString` methods in projections</span></span>

  - <span data-ttu-id="48110-248">Yansıtmalarda tür atamaları</span><span class="sxs-lookup"><span data-stu-id="48110-248">Type casts in projections</span></span>

- <span data-ttu-id="48110-249">Yöntemi izleyen Yöntemler <xref:System.Linq.Enumerable.AsEnumerable%2A> *yerel olarak yürütülür*.</span><span class="sxs-lookup"><span data-stu-id="48110-249">Methods that follow the <xref:System.Linq.Enumerable.AsEnumerable%2A> method are *executed locally*.</span></span> <span data-ttu-id="48110-250">Bu yöntem, hemen yürütmeye neden olmaz.</span><span class="sxs-lookup"><span data-stu-id="48110-250">This method does not cause immediate execution.</span></span>

- <span data-ttu-id="48110-251">Bir `struct` Sorgu sonucunun dönüş türü olarak veya sonuç türünün üyesi olarak ' i kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="48110-251">You can use a `struct` as the return type of a query result or as a member of the result type.</span></span> <span data-ttu-id="48110-252">Varlıkların sınıflar olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="48110-252">Entities are required to be classes.</span></span> <span data-ttu-id="48110-253">Anonim türler sınıf örnekleri olarak gerçekleştirilir, ancak adlandırılmış yapılar (varlık olmayan) projeksiyonde kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="48110-253">Anonymous types are materialized as class instances, but named structs (non-entities) can be used in projection.</span></span>

- <span data-ttu-id="48110-254">Bir sorgu sonucunun dönüş türünün bir üyesi türünde olabilir <xref:System.Linq.IQueryable%601> .</span><span class="sxs-lookup"><span data-stu-id="48110-254">A member of the return type of a query result can be of type <xref:System.Linq.IQueryable%601>.</span></span> <span data-ttu-id="48110-255">Yerel bir koleksiyon olarak gerçekleştirilmiş olur.</span><span class="sxs-lookup"><span data-stu-id="48110-255">It is materialized as a local collection.</span></span>

- <span data-ttu-id="48110-256">Aşağıdaki yöntemler, yöntemlerin uygulandığı dizinin *hemen* bir şekilde oluşturulmasına neden olur:</span><span class="sxs-lookup"><span data-stu-id="48110-256">The following methods cause the *immediate materialization* of the sequence that the methods are applied to:</span></span>

  - <xref:System.Linq.Enumerable.ToList%2A>

  - <xref:System.Linq.Enumerable.ToDictionary%2A>

  - <xref:System.Linq.Enumerable.ToArray%2A>

## <a name="see-also"></a><span data-ttu-id="48110-257">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="48110-257">See also</span></span>

- [<span data-ttu-id="48110-258">Başvuru</span><span class="sxs-lookup"><span data-stu-id="48110-258">Reference</span></span>](reference.md)
- [<span data-ttu-id="48110-259">Dizideki Öğeleri Döndürme veya Atlama</span><span class="sxs-lookup"><span data-stu-id="48110-259">Return Or Skip Elements in a Sequence</span></span>](return-or-skip-elements-in-a-sequence.md)
- [<span data-ttu-id="48110-260">İki Diziyi Birleştirme</span><span class="sxs-lookup"><span data-stu-id="48110-260">Concatenate Two Sequences</span></span>](concatenate-two-sequences.md)
- [<span data-ttu-id="48110-261">İki Dizi Arasındaki Küme Farkını Döndürme</span><span class="sxs-lookup"><span data-stu-id="48110-261">Return the Set Difference Between Two Sequences</span></span>](return-the-set-difference-between-two-sequences.md)
- [<span data-ttu-id="48110-262">İki Dizinin Küme Kesişimini Döndürme</span><span class="sxs-lookup"><span data-stu-id="48110-262">Return the Set Intersection of Two Sequences</span></span>](return-the-set-intersection-of-two-sequences.md)
- [<span data-ttu-id="48110-263">İki Dizinin Küme Birleşimini Döndürme</span><span class="sxs-lookup"><span data-stu-id="48110-263">Return the Set Union of Two Sequences</span></span>](return-the-set-union-of-two-sequences.md)
