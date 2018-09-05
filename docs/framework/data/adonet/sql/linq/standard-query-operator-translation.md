---
title: Standart sorgu işleci çevirisi
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: a60c30fa-1e68-45fe-b984-f6abb9ede40e
ms.openlocfilehash: fb4910e48af58463c5c851173f8e3caf4594cc3a
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43672781"
---
# <a name="standard-query-operator-translation"></a><span data-ttu-id="97a82-102">Standart sorgu işleci çevirisi</span><span class="sxs-lookup"><span data-stu-id="97a82-102">Standard Query Operator Translation</span></span>
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="97a82-103"> Standart sorgu işleçleri SQL komutlara çevirir.</span><span class="sxs-lookup"><span data-stu-id="97a82-103"> translates Standard Query Operators to SQL commands.</span></span> <span data-ttu-id="97a82-104">Sorgu işlemcisi veritabanının SQL çeviri yürütme semantikleri belirler.</span><span class="sxs-lookup"><span data-stu-id="97a82-104">The query processor of the database determines the execution semantics of SQL translation.</span></span>  
  
 <span data-ttu-id="97a82-105">Standart sorgu işleçleri karşı tanımlanmış *dizileri*.</span><span class="sxs-lookup"><span data-stu-id="97a82-105">Standard Query Operators are defined against *sequences*.</span></span> <span data-ttu-id="97a82-106">Bir sıra *sıralı* ve dizinin her öğesi için başvuru kimliği kullanır.</span><span class="sxs-lookup"><span data-stu-id="97a82-106">A sequence is *ordered* and relies on reference identity for each element of the sequence.</span></span> <span data-ttu-id="97a82-107">Daha fazla bilgi için [standart sorgu işleçlerine genel bakış](https://msdn.microsoft.com/library/24cda21e-8af8-4632-b519-c404a839b9b2).</span><span class="sxs-lookup"><span data-stu-id="97a82-107">For more information, see [Standard Query Operators Overview](https://msdn.microsoft.com/library/24cda21e-8af8-4632-b519-c404a839b9b2).</span></span>  
  
 <span data-ttu-id="97a82-108">SQL ilgilenen öncelikli olarak *değer kümeleri sıralanmamış*.</span><span class="sxs-lookup"><span data-stu-id="97a82-108">SQL deals primarily with *unordered sets of values*.</span></span> <span data-ttu-id="97a82-109">Sıralamadır genellikle bir açıkça belirtilen, bir sorgu sonucunu yerine Ara sonuçlar uygulanan sonrası işlem.</span><span class="sxs-lookup"><span data-stu-id="97a82-109">Ordering is typically an explicitly stated, post-processing operation that is applied to the final result of a query rather than to intermediate results.</span></span> <span data-ttu-id="97a82-110">Kimlik değerleri tarafından tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="97a82-110">Identity is defined by values.</span></span> <span data-ttu-id="97a82-111">Bu nedenle SQL sorguları multisets ile dağıtılacak anlaşılabilir (*paketleri*) yerine *ayarlar*.</span><span class="sxs-lookup"><span data-stu-id="97a82-111">For this reason, SQL queries are understood to deal with multisets (*bags*) instead of *sets*.</span></span>  
  
 <span data-ttu-id="97a82-112">Standart sorgu işleçleri ve kendi SQL çeviri için SQL Server sağlayıcısı arasındaki farklar aşağıdaki paragraflara açıklayan [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="97a82-112">The following paragraphs describe the differences between the Standard Query Operators and their SQL translation for the SQL Server provider for [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span>  
  
## <a name="operator-support"></a><span data-ttu-id="97a82-113">İşleç desteği</span><span class="sxs-lookup"><span data-stu-id="97a82-113">Operator Support</span></span>  
  
### <a name="concat"></a><span data-ttu-id="97a82-114">concat</span><span class="sxs-lookup"><span data-stu-id="97a82-114">Concat</span></span>  
 <span data-ttu-id="97a82-115"><xref:System.Linq.Enumerable.Concat%2A> Yöntemi alıcı sırası ve bağımsız değişken sırası olduğu aynı sıralı multisets için tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="97a82-115">The <xref:System.Linq.Enumerable.Concat%2A> method is defined for ordered multisets where the order of the receiver and the order of the argument are the same.</span></span> <span data-ttu-id="97a82-116"><xref:System.Linq.Enumerable.Concat%2A> gibi çalışır `UNION ALL` genel sıraya göre ve ardından multisets üzerinden.</span><span class="sxs-lookup"><span data-stu-id="97a82-116"><xref:System.Linq.Enumerable.Concat%2A> works as `UNION ALL` over the multisets followed by the common order.</span></span>  
  
 <span data-ttu-id="97a82-117">Son adım, sonuçları üretti önce SQL sıralaması.</span><span class="sxs-lookup"><span data-stu-id="97a82-117">The final step is ordering in SQL before results are produced.</span></span> <span data-ttu-id="97a82-118"><xref:System.Linq.Enumerable.Concat%2A> bağımsız değişkenlerinin sırası korumaz.</span><span class="sxs-lookup"><span data-stu-id="97a82-118"><xref:System.Linq.Enumerable.Concat%2A> does not preserve the order of its arguments.</span></span> <span data-ttu-id="97a82-119">Uygun sıralama emin olmak için açıkça sonuçlarını sıralamanız gerekir <xref:System.Linq.Enumerable.Concat%2A>.</span><span class="sxs-lookup"><span data-stu-id="97a82-119">To ensure appropriate ordering, you must explicitly order the results of <xref:System.Linq.Enumerable.Concat%2A>.</span></span>  
  
### <a name="intersect-except-union"></a><span data-ttu-id="97a82-120">INTERSECT, birleşim dışında</span><span class="sxs-lookup"><span data-stu-id="97a82-120">Intersect, Except, Union</span></span>  
 <span data-ttu-id="97a82-121"><xref:System.Linq.Enumerable.Intersect%2A> Ve <xref:System.Linq.Enumerable.Except%2A> yöntemlerdir kümelerinde yalnızca iyi tanımlanmış.</span><span class="sxs-lookup"><span data-stu-id="97a82-121">The <xref:System.Linq.Enumerable.Intersect%2A> and <xref:System.Linq.Enumerable.Except%2A> methods are well defined only on sets.</span></span> <span data-ttu-id="97a82-122">Semantiği multisets için tanımlı değil.</span><span class="sxs-lookup"><span data-stu-id="97a82-122">The semantics for multisets is undefined.</span></span>  
  
 <span data-ttu-id="97a82-123"><xref:System.Linq.Enumerable.Union%2A> Yöntemi multisets için (etkili bir şekilde SQL UNION ALL yan tümcesinin sonucu) multisets sırasız birleşimi olarak tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="97a82-123">The <xref:System.Linq.Enumerable.Union%2A> method is defined for multisets as the unordered concatenation of the multisets (effectively the result of the UNION ALL clause in SQL).</span></span>  
  
### <a name="take-skip"></a><span data-ttu-id="97a82-124">Sınav zamanı, Atla</span><span class="sxs-lookup"><span data-stu-id="97a82-124">Take, Skip</span></span>  
 <span data-ttu-id="97a82-125"><xref:System.Linq.Enumerable.Take%2A> ve <xref:System.Linq.Enumerable.Skip%2A> yöntemlerdir karşı yalnızca iyi tanımlanmış *kümeleri sıralı*.</span><span class="sxs-lookup"><span data-stu-id="97a82-125"><xref:System.Linq.Enumerable.Take%2A> and <xref:System.Linq.Enumerable.Skip%2A> methods are well defined only against *ordered sets*.</span></span> <span data-ttu-id="97a82-126">Sırasız kümeleri veya multisets semantiği tanımsızdır.</span><span class="sxs-lookup"><span data-stu-id="97a82-126">The semantics for unordered sets or multisets are undefined.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="97a82-127"><xref:System.Linq.Enumerable.Take%2A> ve <xref:System.Linq.Enumerable.Skip%2A> SQL Server 2000 sorguları içinde kullanıldığında belirli sınırlamaları vardır.</span><span class="sxs-lookup"><span data-stu-id="97a82-127"><xref:System.Linq.Enumerable.Take%2A> and <xref:System.Linq.Enumerable.Skip%2A> have certain limitations when they are used in queries against SQL Server 2000.</span></span> <span data-ttu-id="97a82-128">"Atla ve SQL Server 2000'de özel durumlar'ı Al" girdisinde daha fazla bilgi için bkz. [sorun giderme](../../../../../../docs/framework/data/adonet/sql/linq/troubleshooting.md).</span><span class="sxs-lookup"><span data-stu-id="97a82-128">For more information, see the "Skip and Take Exceptions in SQL Server 2000" entry in [Troubleshooting](../../../../../../docs/framework/data/adonet/sql/linq/troubleshooting.md).</span></span>  
  
 <span data-ttu-id="97a82-129">SQL'de sıralama sınırlamaları nedeniyle [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] bağımsız değişkeni yöntemin sonucu için bu yöntemlerin sıralama taşımak çalışır.</span><span class="sxs-lookup"><span data-stu-id="97a82-129">Because of limitations on ordering in SQL, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] tries to move the ordering of the argument of these methods to the result of the method.</span></span> <span data-ttu-id="97a82-130">Örneğin, aşağıdakileri dikkate alın [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] sorgu:</span><span class="sxs-lookup"><span data-stu-id="97a82-130">For example, consider the following [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] query:</span></span>  
  
 [!code-csharp[DLinqSQOTranslation#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSQOTranslation/cs/Program.cs#1)]
 [!code-vb[DLinqSQOTranslation#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSQOTranslation/vb/Module1.vb#1)]  
  
 <span data-ttu-id="97a82-131">Bu kod için oluşturulan SQL gibi sonuna sıralama taşır:</span><span class="sxs-lookup"><span data-stu-id="97a82-131">The generated SQL for this code moves the ordering to the end, as follows:</span></span>  
  
```  
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
  
 <span data-ttu-id="97a82-132">Tüm belirtilen sıralama ne zaman tutarlı olmasını belirgin hale gelir <xref:System.Linq.Enumerable.Take%2A> ve <xref:System.Linq.Enumerable.Skip%2A> birbirine zincirlenmiş.</span><span class="sxs-lookup"><span data-stu-id="97a82-132">It becomes obvious that all the specified ordering must be consistent when <xref:System.Linq.Enumerable.Take%2A> and <xref:System.Linq.Enumerable.Skip%2A> are chained together.</span></span> <span data-ttu-id="97a82-133">Aksi takdirde, sonuçlar tanımsızdır.</span><span class="sxs-lookup"><span data-stu-id="97a82-133">Otherwise, the results are undefined.</span></span>  
  
 <span data-ttu-id="97a82-134">Her ikisi de <xref:System.Linq.Enumerable.Take%2A> ve <xref:System.Linq.Enumerable.Skip%2A> standart sorgu işleci belirtimine göre negatif olmayan, sabit tamsayı bağımsız değişkenler için iyi tanımlanmış olması.</span><span class="sxs-lookup"><span data-stu-id="97a82-134">Both <xref:System.Linq.Enumerable.Take%2A> and <xref:System.Linq.Enumerable.Skip%2A> are well-defined for non-negative, constant integral arguments based on the Standard Query Operator specification.</span></span>  
  
### <a name="operators-with-no-translation"></a><span data-ttu-id="97a82-135">Çeviri sahip işleçler</span><span class="sxs-lookup"><span data-stu-id="97a82-135">Operators with No Translation</span></span>  
 <span data-ttu-id="97a82-136">Aşağıdaki yöntemleri tarafından bunların çevirisi yapılmaz [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="97a82-136">The following methods are not translated by [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span> <span data-ttu-id="97a82-137">En yaygın nedeni, sırasız multisets dizileri arasındaki farktır.</span><span class="sxs-lookup"><span data-stu-id="97a82-137">The most common reason is the difference between unordered multisets and sequences.</span></span>  
  
|<span data-ttu-id="97a82-138">İşleçler</span><span class="sxs-lookup"><span data-stu-id="97a82-138">Operators</span></span>|<span data-ttu-id="97a82-139">Stratejinin</span><span class="sxs-lookup"><span data-stu-id="97a82-139">Rationale</span></span>|  
|---------------|---------------|  
|<span data-ttu-id="97a82-140"><xref:System.Linq.Enumerable.TakeWhile%2A>, <xref:System.Linq.Enumerable.SkipWhile%2A></span><span class="sxs-lookup"><span data-stu-id="97a82-140"><xref:System.Linq.Enumerable.TakeWhile%2A>, <xref:System.Linq.Enumerable.SkipWhile%2A></span></span>|<span data-ttu-id="97a82-141">Diziler üzerinde değil, multisets üzerinde SQL sorguları çalışır.</span><span class="sxs-lookup"><span data-stu-id="97a82-141">SQL queries operate on multisets, not on sequences.</span></span> <span data-ttu-id="97a82-142">`ORDER BY` Son yan tümce sonuçları uygulanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="97a82-142">`ORDER BY` must be the last clause applied to the results.</span></span> <span data-ttu-id="97a82-143">Bu nedenle, bu iki yöntem için genel amaçlı çeviri yoktur.</span><span class="sxs-lookup"><span data-stu-id="97a82-143">For this reason, there is no general-purpose translation for these two methods.</span></span>|  
|<xref:System.Linq.Enumerable.Reverse%2A>|<span data-ttu-id="97a82-144">Bu yöntemin çeviri sıralı bir küme için mümkündür, ancak şu anda tarafından çevrilmez [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="97a82-144">Translation of this method is possible for an ordered set but is not currently translated by [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span>|  
|<span data-ttu-id="97a82-145"><xref:System.Linq.Enumerable.Last%2A>, <xref:System.Linq.Enumerable.LastOrDefault%2A></span><span class="sxs-lookup"><span data-stu-id="97a82-145"><xref:System.Linq.Enumerable.Last%2A>, <xref:System.Linq.Enumerable.LastOrDefault%2A></span></span>|<span data-ttu-id="97a82-146">Bu yöntemlerin çeviri sıralı bir küme için mümkündür, ancak şu anda tarafından çevrilmez [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="97a82-146">Translation of these methods is possible for an ordered set but is not currently translated by [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span>|  
|<span data-ttu-id="97a82-147"><xref:System.Linq.Enumerable.ElementAt%2A>, <xref:System.Linq.Enumerable.ElementAtOrDefault%2A></span><span class="sxs-lookup"><span data-stu-id="97a82-147"><xref:System.Linq.Enumerable.ElementAt%2A>, <xref:System.Linq.Enumerable.ElementAtOrDefault%2A></span></span>|<span data-ttu-id="97a82-148">SQL sorguları dizinlenebilir dizileri göre değil, multisets üzerinde çalışır.</span><span class="sxs-lookup"><span data-stu-id="97a82-148">SQL queries operate on multisets, not on indexable sequences.</span></span>|  
|<span data-ttu-id="97a82-149"><xref:System.Linq.Enumerable.DefaultIfEmpty%2A> (varsayılan bağımsız değişken ile aşırı yükleme)</span><span class="sxs-lookup"><span data-stu-id="97a82-149"><xref:System.Linq.Enumerable.DefaultIfEmpty%2A> (overload with default arg)</span></span>|<span data-ttu-id="97a82-150">Genel olarak, rastgele bir demet için bir varsayılan değer belirtilemez.</span><span class="sxs-lookup"><span data-stu-id="97a82-150">In general, a default value cannot be specified for an arbitrary tuple.</span></span> <span data-ttu-id="97a82-151">Diziler için null değerler, bazı durumlarda dış birleştirmeler ile mümkündür.</span><span class="sxs-lookup"><span data-stu-id="97a82-151">Null values for tuples are possible in some cases through outer joins.</span></span>|  
  
## <a name="expression-translation"></a><span data-ttu-id="97a82-152">İfade çevirisi</span><span class="sxs-lookup"><span data-stu-id="97a82-152">Expression Translation</span></span>  
  
### <a name="null-semantics"></a><span data-ttu-id="97a82-153">Null semantikler</span><span class="sxs-lookup"><span data-stu-id="97a82-153">Null semantics</span></span>  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="97a82-154"> SQL null karşılaştırma semantiği uygulamaz.</span><span class="sxs-lookup"><span data-stu-id="97a82-154"> does not impose null comparison semantics on SQL.</span></span> <span data-ttu-id="97a82-155">Karşılaştırma işleçleri sözdizimsel olarak SQL eşdeğerlerine dönüştürülür.</span><span class="sxs-lookup"><span data-stu-id="97a82-155">Comparison operators are syntactically translated to their SQL equivalents.</span></span> <span data-ttu-id="97a82-156">Bu nedenle, sunucu veya bağlantı ayarları tarafından tanımlanan SQL semantiği semantiği yansıtır.</span><span class="sxs-lookup"><span data-stu-id="97a82-156">For this reason, the semantics reflect SQL semantics that are defined by server or connection settings.</span></span> <span data-ttu-id="97a82-157">Örneğin, iki null değerler varsayılan SQL Server Ayarları altında eşit olarak kabul edilir, ancak semantiği değiştirmek için ayarları değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="97a82-157">For example, two null values are considered unequal under default SQL Server settings, but you can change the settings to change the semantics.</span></span> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="97a82-158"> sorguları dönüştürdüğünde sunucu ayarlarını dikkate almaz.</span><span class="sxs-lookup"><span data-stu-id="97a82-158"> does not consider server settings when it translates queries.</span></span>  
  
 <span data-ttu-id="97a82-159">Değişmez değeri null ile bir karşılaştırması için uygun SQL sürümü çevrilir (`is null` veya `is not null`).</span><span class="sxs-lookup"><span data-stu-id="97a82-159">A comparison with the literal null is translated to the appropriate SQL version (`is null` or `is not null`).</span></span>  
  
 <span data-ttu-id="97a82-160">Değerini `null` harmanlamasında SQL Server tarafından tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="97a82-160">The value of `null` in collation is defined by SQL Server.</span></span> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="97a82-161"> harmanlama değiştirmez.</span><span class="sxs-lookup"><span data-stu-id="97a82-161"> does not change the collation.</span></span>  
  
### <a name="aggregates"></a><span data-ttu-id="97a82-162">Toplamlar</span><span class="sxs-lookup"><span data-stu-id="97a82-162">Aggregates</span></span>  
 <span data-ttu-id="97a82-163">Standart sorgu işleci toplama yöntemi <xref:System.Linq.Enumerable.Sum%2A> sıfıra yalnızca null içeren bir dizi veya boş bir dizi için değerlendirir.</span><span class="sxs-lookup"><span data-stu-id="97a82-163">The Standard Query Operator aggregate method <xref:System.Linq.Enumerable.Sum%2A> evaluates to zero for an empty sequence or for a sequence that contains only nulls.</span></span> <span data-ttu-id="97a82-164">İçinde [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], SQL semantiği sol değiştirmeden, ve <xref:System.Linq.Enumerable.Sum%2A> değerlendiren `null` yerine yalnızca null içeren bir dizi veya boş bir dizi için sıfır.</span><span class="sxs-lookup"><span data-stu-id="97a82-164">In [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], the semantics of SQL are left unchanged, and <xref:System.Linq.Enumerable.Sum%2A> evaluates to `null` instead of zero for an empty sequence or for a sequence that contains only nulls.</span></span>  
  
 <span data-ttu-id="97a82-165">Toplamalar Ara sonuçlar SQL sınırlamalar uygulanır [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="97a82-165">SQL limitations on intermediate results apply to aggregates in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span> <span data-ttu-id="97a82-166"><xref:System.Linq.Enumerable.Sum%2A> 32-bit tamsayı miktarlar hesaplanan 64-bit sonuçları kullanarak.</span><span class="sxs-lookup"><span data-stu-id="97a82-166">The <xref:System.Linq.Enumerable.Sum%2A> of 32-bit integer quantities is not computed by using 64-bit results.</span></span> <span data-ttu-id="97a82-167">Taşma için oluşabilir bir [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] çevirisi <xref:System.Linq.Enumerable.Sum%2A>bile standart sorgu işleci uygulaması karşılık gelen bir bellek içi dizisi taşmaya neden olmaz.</span><span class="sxs-lookup"><span data-stu-id="97a82-167">Overflow might occur for a [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] translation of <xref:System.Linq.Enumerable.Sum%2A>, even if the Standard Query Operator implementation does not cause an overflow for the corresponding in-memory sequence.</span></span>  
  
 <span data-ttu-id="97a82-168">Benzer şekilde, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] çevirisi <xref:System.Linq.Enumerable.Average%2A> tamsayı değerleri olarak hesaplanır bir `integer`, olarak değil bir `double`.</span><span class="sxs-lookup"><span data-stu-id="97a82-168">Likewise, the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] translation of <xref:System.Linq.Enumerable.Average%2A> of integer values is computed as an `integer`, not as a `double`.</span></span>  
  
### <a name="entity-arguments"></a><span data-ttu-id="97a82-169">Varlık bağımsız değişkenleri</span><span class="sxs-lookup"><span data-stu-id="97a82-169">Entity Arguments</span></span>  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="97a82-170"> varlık türleri kullanılmak üzere etkinleştirir <xref:System.Linq.Enumerable.GroupBy%2A> ve <xref:System.Linq.Enumerable.OrderBy%2A> yöntemleri.</span><span class="sxs-lookup"><span data-stu-id="97a82-170"> enables entity types to be used in the <xref:System.Linq.Enumerable.GroupBy%2A> and <xref:System.Linq.Enumerable.OrderBy%2A> methods.</span></span> <span data-ttu-id="97a82-171">Bu işleçler çeviriyi türünde bir bağımsız değişken kullanımı belirterek bu türün tüm üyeleri için eşdeğer olarak kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="97a82-171">In the translation of these operators, the use of an argument of a type is considered to be the equivalent to specifying all members of that type.</span></span> <span data-ttu-id="97a82-172">Örneğin, aşağıdaki kod eşdeğerdir:</span><span class="sxs-lookup"><span data-stu-id="97a82-172">For example, the following code is equivalent:</span></span>  
  
 [!code-csharp[DLinqSQOTranslation#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSQOTranslation/cs/Program.cs#2)]
 [!code-vb[DLinqSQOTranslation#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSQOTranslation/vb/Module1.vb#2)]  
  
### <a name="equatable--comparable-arguments"></a><span data-ttu-id="97a82-173">Equatable / karşılaştırılabilir bağımsız değişkenleri</span><span class="sxs-lookup"><span data-stu-id="97a82-173">Equatable / Comparable Arguments</span></span>  
 <span data-ttu-id="97a82-174">Aşağıdaki yöntemlerden birini uygulamasında eşitlik bağımsız değişkenleri gereklidir:</span><span class="sxs-lookup"><span data-stu-id="97a82-174">Equality of arguments is required in the implementation of the following methods:</span></span>  
  
 <xref:System.Linq.Enumerable.Contains%2A>  
  
 <xref:System.Linq.Enumerable.Skip%2A>  
  
 <xref:System.Linq.Enumerable.Union%2A>  
  
 <xref:System.Linq.Enumerable.Intersect%2A>  
  
 <xref:System.Linq.Enumerable.Except%2A>  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="97a82-175"> Eşitlik ve karşılaştırma için destekleyen *düz* bağımsız değişkenler, ancak veya dizileri içeren olmayan bağımsız değişkenler için.</span><span class="sxs-lookup"><span data-stu-id="97a82-175"> supports equality and comparison for *flat* arguments, but not for arguments that are or contain sequences.</span></span> <span data-ttu-id="97a82-176">Düz bir bağımsız değişken için bir SQL satırını eşlenmiş bir türdür.</span><span class="sxs-lookup"><span data-stu-id="97a82-176">A flat argument is a type that can be mapped to a SQL row.</span></span> <span data-ttu-id="97a82-177">Bir projeksiyon bir dizisini içermez statik olarak belirlenebilir bir veya daha fazla varlık türleri, düz bir bağımsız değişken olarak kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="97a82-177">A projection of one or more entity types that can be statically determined not to contain a sequence is considered a flat argument.</span></span>  
  
 <span data-ttu-id="97a82-178">Düz bağımsız değişkenleri örnekleri aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="97a82-178">Following are examples of flat arguments:</span></span>  
  
 [!code-csharp[DLinqSQOTranslation#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSQOTranslation/cs/Program.cs#3)]
 [!code-vb[DLinqSQOTranslation#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSQOTranslation/vb/Module1.vb#3)]  
  
 <span data-ttu-id="97a82-179">Olmayan-düz (hiyerarşik) bağımsız örnekleri aşağıda verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="97a82-179">The following are examples of non-flat (hierarchical) arguments.</span></span>  
  
 [!code-csharp[DLinqSQOTranslation#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSQOTranslation/cs/Program.cs#4)]
 [!code-vb[DLinqSQOTranslation#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSQOTranslation/vb/Module1.vb#4)]  
  
### <a name="visual-basic-function-translation"></a><span data-ttu-id="97a82-180">Visual Basic işlevi çeviri</span><span class="sxs-lookup"><span data-stu-id="97a82-180">Visual Basic Function Translation</span></span>  
 <span data-ttu-id="97a82-181">Visual Basic derleyici tarafından kullanılan aşağıdaki yardımcı İşlevler, karşılık gelen SQL işleç ve işlevlerini için çevrilir:</span><span class="sxs-lookup"><span data-stu-id="97a82-181">The following helper functions that are used by the Visual Basic compiler are translated to corresponding SQL operators and functions:</span></span>  
  
 `CompareString`  
  
 `DateTime.Compare`  
  
 `Decimal.Compare`  
  
 `IIf (in Microsoft.VisualBasic.Interaction)`  
  
 <span data-ttu-id="97a82-182">Dönüştürme yöntemleri:</span><span class="sxs-lookup"><span data-stu-id="97a82-182">Conversion methods:</span></span>  
  
|||||  
|-|-|-|-|  
|<span data-ttu-id="97a82-183">ToBoolean</span><span class="sxs-lookup"><span data-stu-id="97a82-183">ToBoolean</span></span>|<span data-ttu-id="97a82-184">ToSByte</span><span class="sxs-lookup"><span data-stu-id="97a82-184">ToSByte</span></span>|<span data-ttu-id="97a82-185">ToByte</span><span class="sxs-lookup"><span data-stu-id="97a82-185">ToByte</span></span>|<span data-ttu-id="97a82-186">ToChar</span><span class="sxs-lookup"><span data-stu-id="97a82-186">ToChar</span></span>|  
|<span data-ttu-id="97a82-187">ToCharArrayRankOne</span><span class="sxs-lookup"><span data-stu-id="97a82-187">ToCharArrayRankOne</span></span>|<span data-ttu-id="97a82-188">ToDate</span><span class="sxs-lookup"><span data-stu-id="97a82-188">ToDate</span></span>|<span data-ttu-id="97a82-189">ToDecimal</span><span class="sxs-lookup"><span data-stu-id="97a82-189">ToDecimal</span></span>|<span data-ttu-id="97a82-190">ToDouble</span><span class="sxs-lookup"><span data-stu-id="97a82-190">ToDouble</span></span>|  
|<span data-ttu-id="97a82-191">ToInteger</span><span class="sxs-lookup"><span data-stu-id="97a82-191">ToInteger</span></span>|<span data-ttu-id="97a82-192">ToUInteger</span><span class="sxs-lookup"><span data-stu-id="97a82-192">ToUInteger</span></span>|<span data-ttu-id="97a82-193">ToLong</span><span class="sxs-lookup"><span data-stu-id="97a82-193">ToLong</span></span>|<span data-ttu-id="97a82-194">ToULong</span><span class="sxs-lookup"><span data-stu-id="97a82-194">ToULong</span></span>|  
|<span data-ttu-id="97a82-195">ToShort</span><span class="sxs-lookup"><span data-stu-id="97a82-195">ToShort</span></span>|<span data-ttu-id="97a82-196">ToUShort</span><span class="sxs-lookup"><span data-stu-id="97a82-196">ToUShort</span></span>|<span data-ttu-id="97a82-197">ToSingle</span><span class="sxs-lookup"><span data-stu-id="97a82-197">ToSingle</span></span>|<span data-ttu-id="97a82-198">ToString</span><span class="sxs-lookup"><span data-stu-id="97a82-198">ToString</span></span>|  
  
## <a name="inheritance-support"></a><span data-ttu-id="97a82-199">Devralma desteği</span><span class="sxs-lookup"><span data-stu-id="97a82-199">Inheritance Support</span></span>  
  
### <a name="inheritance-mapping-restrictions"></a><span data-ttu-id="97a82-200">Devralma eşleme kısıtlamaları</span><span class="sxs-lookup"><span data-stu-id="97a82-200">Inheritance Mapping Restrictions</span></span>  
 <span data-ttu-id="97a82-201">Daha fazla bilgi için [nasıl yapılır: devralma hiyerarşilerini eşleme](../../../../../../docs/framework/data/adonet/sql/linq/how-to-map-inheritance-hierarchies.md).</span><span class="sxs-lookup"><span data-stu-id="97a82-201">For more information, see [How to: Map Inheritance Hierarchies](../../../../../../docs/framework/data/adonet/sql/linq/how-to-map-inheritance-hierarchies.md).</span></span>  
  
### <a name="inheritance-in-queries"></a><span data-ttu-id="97a82-202">Sorgularda devralma</span><span class="sxs-lookup"><span data-stu-id="97a82-202">Inheritance in Queries</span></span>  
 <span data-ttu-id="97a82-203">C# atamalar yalnızca yansıtma içinde desteklenir.</span><span class="sxs-lookup"><span data-stu-id="97a82-203">C# casts are supported only in projection.</span></span> <span data-ttu-id="97a82-204">Başka bir yerde kullanılan atamaları değil çevrilir ve göz ardı edilir.</span><span class="sxs-lookup"><span data-stu-id="97a82-204">Casts that are used elsewhere are not translated and are ignored.</span></span> <span data-ttu-id="97a82-205">SQL yanı sıra işlev adlarını, SQL gerçekten yalnızca ortak dil çalışma zamanı (CLR) eşdeğerini gerçekleştirir <xref:System.Convert>.</span><span class="sxs-lookup"><span data-stu-id="97a82-205">Aside from SQL function names, SQL really only performs the equivalent of the common language runtime (CLR) <xref:System.Convert>.</span></span> <span data-ttu-id="97a82-206">Diğer bir deyişle, SQL, bir tür değeri diğerine değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="97a82-206">That is, SQL can change the value of one type to another.</span></span> <span data-ttu-id="97a82-207">Başka bir tür olarak aynı bitleri yeniden yorumlamak güvenli olmayabilecek bir kavram yoktur çünkü cast CLR eşdeğeri yoktur.</span><span class="sxs-lookup"><span data-stu-id="97a82-207">There is no equivalent of CLR cast because there is no concept of reinterpreting the same bits as those of another type.</span></span> <span data-ttu-id="97a82-208">Bir C# dönüştürme works neden yalnızca yerel olarak olmasıdır.</span><span class="sxs-lookup"><span data-stu-id="97a82-208">That is why a C# cast works only locally.</span></span> <span data-ttu-id="97a82-209">Düğümlerde değil.</span><span class="sxs-lookup"><span data-stu-id="97a82-209">It is not remoted.</span></span>  
  
 <span data-ttu-id="97a82-210">İşleçler `is` ve `as`ve `GetType` yöntemi sınırlı olmayan `Select` işleci.</span><span class="sxs-lookup"><span data-stu-id="97a82-210">The operators, `is` and `as`, and the `GetType` method are not restricted to the `Select` operator.</span></span> <span data-ttu-id="97a82-211">Bunlar ayrıca diğer sorgu işleçleri kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="97a82-211">They can be used in other query operators also.</span></span>  
  
## <a name="sql-server-2008-support"></a><span data-ttu-id="97a82-212">SQL Server 2008 desteği</span><span class="sxs-lookup"><span data-stu-id="97a82-212">SQL Server 2008 Support</span></span>  
 <span data-ttu-id="97a82-213">.NET Framework 3.5 SP1 ile başlayarak, LINQ to SQL eşlemesi yeni tarih ve saat türleri SQL Server 2008 ile sunulan destekler.</span><span class="sxs-lookup"><span data-stu-id="97a82-213">Starting with the .NET Framework 3.5 SP1, LINQ to SQL supports mapping to new date and time types introduced with SQL Server 2008.</span></span> <span data-ttu-id="97a82-214">Ancak, bu yeni türleri için eşlenen değerleri karşı çalışırken kullanabileceğiniz SQL sorgu işleçleri için LINQ için bazı sınırlamalar vardır.</span><span class="sxs-lookup"><span data-stu-id="97a82-214">But, there are some limitations to the LINQ to SQL query operators that you can use when operating against values mapped to these new types.</span></span>  
  
### <a name="unsupported-query-operators"></a><span data-ttu-id="97a82-215">Desteklenmeyen sorgu işleçleri</span><span class="sxs-lookup"><span data-stu-id="97a82-215">Unsupported Query Operators</span></span>  
 <span data-ttu-id="97a82-216">Yeni SQL Server tarih ve saat türlerinin eşlenen değerleri aşağıdaki sorgu işleçleri desteklenmez: `DATETIME2`, `DATE`, `TIME`, ve `DATETIMEOFFSET`.</span><span class="sxs-lookup"><span data-stu-id="97a82-216">The following query operators are not supported on values mapped to the new SQL Server date and time types: `DATETIME2`, `DATE`, `TIME`, and `DATETIMEOFFSET`.</span></span>  
  
-   `Aggregate`  
  
-   `Average`  
  
-   `LastOrDefault`  
  
-   `OfType`  
  
-   `Sum`  
  
 <span data-ttu-id="97a82-217">Bu SQL Server tarih ve saat türlerinin eşleme hakkında daha fazla bilgi için bkz. [SQL-CLR tür eşlemesi](../../../../../../docs/framework/data/adonet/sql/linq/sql-clr-type-mapping.md).</span><span class="sxs-lookup"><span data-stu-id="97a82-217">For more information about mapping to these SQL Server date and time types, see [SQL-CLR Type Mapping](../../../../../../docs/framework/data/adonet/sql/linq/sql-clr-type-mapping.md).</span></span>  
  
## <a name="sql-server-2005-support"></a><span data-ttu-id="97a82-218">SQL Server 2005 desteği</span><span class="sxs-lookup"><span data-stu-id="97a82-218">SQL Server 2005 Support</span></span>  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="97a82-219"> Aşağıdaki SQL Server 2005 özellikleri desteklemez:</span><span class="sxs-lookup"><span data-stu-id="97a82-219"> does not support the following SQL Server 2005 features:</span></span>  
  
-   <span data-ttu-id="97a82-220">Saklı yordamlar SQL CLR için yazılır.</span><span class="sxs-lookup"><span data-stu-id="97a82-220">Stored procedures written for SQL CLR.</span></span>  
  
-   <span data-ttu-id="97a82-221">Kullanıcı tanımlı tür.</span><span class="sxs-lookup"><span data-stu-id="97a82-221">User-defined type.</span></span>  
  
-   <span data-ttu-id="97a82-222">XML sorgu özellikleri.</span><span class="sxs-lookup"><span data-stu-id="97a82-222">XML query features.</span></span>  
  
## <a name="sql-server-2000-support"></a><span data-ttu-id="97a82-223">SQL Server 2000 desteği</span><span class="sxs-lookup"><span data-stu-id="97a82-223">SQL Server 2000 Support</span></span>  
 <span data-ttu-id="97a82-224">Aşağıdaki [!INCLUDE[ss2k](../../../../../../includes/ss2k-md.md)] sınırlamaları (karşılaştırıldığında [!INCLUDE[sqprsqext](../../../../../../includes/sqprsqext-md.md)]) etkileyen [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] destekler.</span><span class="sxs-lookup"><span data-stu-id="97a82-224">The following [!INCLUDE[ss2k](../../../../../../includes/ss2k-md.md)] limitations (compared to [!INCLUDE[sqprsqext](../../../../../../includes/sqprsqext-md.md)]) affect [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] support.</span></span>  
  
### <a name="cross-apply-and-outer-apply-operators"></a><span data-ttu-id="97a82-225">Çapraz Uygula ve dış işleçleri Uygula</span><span class="sxs-lookup"><span data-stu-id="97a82-225">Cross Apply and Outer Apply Operators</span></span>  
 <span data-ttu-id="97a82-226">Bu işleçler kullanılamaz [!INCLUDE[ss2k](../../../../../../includes/ss2k-md.md)].</span><span class="sxs-lookup"><span data-stu-id="97a82-226">These operators are not available in [!INCLUDE[ss2k](../../../../../../includes/ss2k-md.md)].</span></span> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="97a82-227"> bir dizi uygun birleştirmelerle değiştirilecek yeniden dener.</span><span class="sxs-lookup"><span data-stu-id="97a82-227"> tries a series of rewrites to replace them with appropriate joins.</span></span>  
  
 <span data-ttu-id="97a82-228">`Cross Apply` ve `Outer Apply` ilişki gezintiler için oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="97a82-228">`Cross Apply` and `Outer Apply` are generated for relationship navigations.</span></span> <span data-ttu-id="97a82-229">Bu tür yeniden olası sorgu kümesi iyi tanımlı değil.</span><span class="sxs-lookup"><span data-stu-id="97a82-229">The set of queries for which such rewrites are possible is not well defined.</span></span> <span data-ttu-id="97a82-230">Bu nedenle, en küçük grup için desteklenen sorgu [!INCLUDE[ss2k](../../../../../../includes/ss2k-md.md)] ilişki Gezinti içermeyen kümesidir.</span><span class="sxs-lookup"><span data-stu-id="97a82-230">For this reason, the minimal set of queries that is supported for [!INCLUDE[ss2k](../../../../../../includes/ss2k-md.md)] is the set that does not involve relationship navigation.</span></span>  
  
### <a name="text--ntext"></a><span data-ttu-id="97a82-231">Text / ntext</span><span class="sxs-lookup"><span data-stu-id="97a82-231">text / ntext</span></span>  
 <span data-ttu-id="97a82-232">Veri türleri `text`  /  `ntext` karşı belirli sorgu işlemleri kullanılamaz `varchar(max)`  /  `nvarchar(max)`, tarafından hangi desteklendiği [!INCLUDE[sqprsqext](../../../../../../includes/sqprsqext-md.md)].</span><span class="sxs-lookup"><span data-stu-id="97a82-232">Data types `text` / `ntext` cannot be used in certain query operations against `varchar(max)` / `nvarchar(max)`, which are supported by [!INCLUDE[sqprsqext](../../../../../../includes/sqprsqext-md.md)].</span></span>  
  
 <span data-ttu-id="97a82-233">Bu sınırlama için herhangi bir çözüm kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="97a82-233">No resolution is available for this limitation.</span></span> <span data-ttu-id="97a82-234">Özellikle, kullanamazsınız `Distinct()` eşlendiğine üyeleri içeren herhangi bir sonuç üzerinde `text` veya `ntext` sütunları.</span><span class="sxs-lookup"><span data-stu-id="97a82-234">Specifically, you cannot use `Distinct()` on any result that contains members that are mapped to `text` or `ntext` columns.</span></span>  
  
### <a name="behavior-triggered-by-nested-queries"></a><span data-ttu-id="97a82-235">İç içe geçmiş sorgular tarafından tetiklenen davranışı</span><span class="sxs-lookup"><span data-stu-id="97a82-235">Behavior Triggered by Nested Queries</span></span>  
 [!INCLUDE[ss2k](../../../../../../includes/ss2k-md.md)]<span data-ttu-id="97a82-236"> (SP4), bağlayıcı iç içe geçmiş sorgular tarafından tetiklenen olmasını sağlayan bazı özelliklere sahiptir.</span><span class="sxs-lookup"><span data-stu-id="97a82-236"> (through SP4) binder has some idiosyncrasies that are triggered by nested queries.</span></span> <span data-ttu-id="97a82-237">Bu idiosyncrasies tetikleyen SQL sorguları kümesini, iyi tanımlanmış değil.</span><span class="sxs-lookup"><span data-stu-id="97a82-237">The set of SQL queries that triggers these idiosyncrasies is not well defined.</span></span> <span data-ttu-id="97a82-238">Bu nedenle, bir dizi tanımlanamaz [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] sorguları SQL Server özel durumlarına neden.</span><span class="sxs-lookup"><span data-stu-id="97a82-238">For this reason, you cannot define the set of [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] queries that might cause SQL Server exceptions.</span></span>  
  
### <a name="skip-and-take-operators"></a><span data-ttu-id="97a82-239">Skip ve Take işleçleri</span><span class="sxs-lookup"><span data-stu-id="97a82-239">Skip and Take Operators</span></span>  
 <span data-ttu-id="97a82-240"><xref:System.Linq.Enumerable.Take%2A> ve <xref:System.Linq.Enumerable.Skip%2A> sorguları içinde kullanıldığında belirli sınırlamaları vardır [!INCLUDE[ss2k](../../../../../../includes/ss2k-md.md)].</span><span class="sxs-lookup"><span data-stu-id="97a82-240"><xref:System.Linq.Enumerable.Take%2A> and <xref:System.Linq.Enumerable.Skip%2A> have certain limitations when they are used in queries against [!INCLUDE[ss2k](../../../../../../includes/ss2k-md.md)].</span></span> <span data-ttu-id="97a82-241">"Atla ve SQL Server 2000'de özel durumlar'ı Al" girdisinde daha fazla bilgi için bkz. [sorun giderme](../../../../../../docs/framework/data/adonet/sql/linq/troubleshooting.md).</span><span class="sxs-lookup"><span data-stu-id="97a82-241">For more information, see the "Skip and Take Exceptions in SQL Server 2000" entry in [Troubleshooting](../../../../../../docs/framework/data/adonet/sql/linq/troubleshooting.md).</span></span>  
  
## <a name="object-materialization"></a><span data-ttu-id="97a82-242">Nesne gerçekleştirme</span><span class="sxs-lookup"><span data-stu-id="97a82-242">Object Materialization</span></span>  
 <span data-ttu-id="97a82-243">Materialization bir veya daha fazla SQL sorguları tarafından döndürülen satırlar CLR nesnesi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="97a82-243">Materialization creates CLR objects from rows that are returned by one or more SQL queries.</span></span>  
  
-   <span data-ttu-id="97a82-244">Aşağıdaki çağrıları *yerel olarak yürütüldüğü* materialization bir parçası olarak:</span><span class="sxs-lookup"><span data-stu-id="97a82-244">The following calls are *executed locally* as a part of materialization:</span></span>  
  
    -   <span data-ttu-id="97a82-245">Oluşturucular</span><span class="sxs-lookup"><span data-stu-id="97a82-245">Constructors</span></span>  
  
    -   <span data-ttu-id="97a82-246">`ToString` projeksiyonlar yöntemleri</span><span class="sxs-lookup"><span data-stu-id="97a82-246">`ToString` methods in projections</span></span>  
  
    -   <span data-ttu-id="97a82-247">Projeksiyonlar içinde tür atamaları</span><span class="sxs-lookup"><span data-stu-id="97a82-247">Type casts in projections</span></span>  
  
-   <span data-ttu-id="97a82-248">Aşağıdaki yöntemleri <xref:System.Linq.Enumerable.AsEnumerable%2A> yöntemdir *yerel olarak yürütüldüğü*.</span><span class="sxs-lookup"><span data-stu-id="97a82-248">Methods that follow the <xref:System.Linq.Enumerable.AsEnumerable%2A> method are *executed locally*.</span></span> <span data-ttu-id="97a82-249">Bu yöntem, anında yürütülmesine neden olmaz.</span><span class="sxs-lookup"><span data-stu-id="97a82-249">This method does not cause immediate execution.</span></span>  
  
-   <span data-ttu-id="97a82-250">Kullanabileceğiniz bir `struct` dönüş türü bir sorgu sonucunun veya sonuç türünün bir üyesi olarak.</span><span class="sxs-lookup"><span data-stu-id="97a82-250">You can use a `struct` as the return type of a query result or as a member of the result type.</span></span> <span data-ttu-id="97a82-251">Varlık sınıfları için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="97a82-251">Entities are required to be classes.</span></span> <span data-ttu-id="97a82-252">Anonim türler sınıf örneklerinin gerçekleştirilmiş ancak projeksiyonda adlandırılmış yapıları (varlıklar olmayan) kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="97a82-252">Anonymous types are materialized as class instances, but named structs (non-entities) can be used in projection.</span></span>  
  
-   <span data-ttu-id="97a82-253">Dönüş türü bir sorgu sonucunun üyesi türünde olabilir <xref:System.Linq.IQueryable%601>.</span><span class="sxs-lookup"><span data-stu-id="97a82-253">A member of the return type of a query result can be of type <xref:System.Linq.IQueryable%601>.</span></span> <span data-ttu-id="97a82-254">Yerel koleksiyon olarak gerçekleştirilip.</span><span class="sxs-lookup"><span data-stu-id="97a82-254">It is materialized as a local collection.</span></span>  
  
-   <span data-ttu-id="97a82-255">Aşağıdaki yöntemlerden neden *hemen materialization* yöntemleri uygulanan dizisi:</span><span class="sxs-lookup"><span data-stu-id="97a82-255">The following methods cause the *immediate materialization* of the sequence that the methods are applied to:</span></span>  
  
    -   <xref:System.Linq.Enumerable.ToList%2A>  
  
    -   <xref:System.Linq.Enumerable.ToDictionary%2A>  
  
    -   <xref:System.Linq.Enumerable.ToArray%2A>  
  
## <a name="see-also"></a><span data-ttu-id="97a82-256">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="97a82-256">See Also</span></span>  
 [<span data-ttu-id="97a82-257">Başvuru</span><span class="sxs-lookup"><span data-stu-id="97a82-257">Reference</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/reference.md)  
 [<span data-ttu-id="97a82-258">Dizideki Öğeleri Döndürme veya Atlama</span><span class="sxs-lookup"><span data-stu-id="97a82-258">Return Or Skip Elements in a Sequence</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/return-or-skip-elements-in-a-sequence.md)  
 [<span data-ttu-id="97a82-259">İki Diziyi Birleştirme</span><span class="sxs-lookup"><span data-stu-id="97a82-259">Concatenate Two Sequences</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/concatenate-two-sequences.md)  
 [<span data-ttu-id="97a82-260">İki Dizi Arasındaki Küme Farkını Döndürme</span><span class="sxs-lookup"><span data-stu-id="97a82-260">Return the Set Difference Between Two Sequences</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/return-the-set-difference-between-two-sequences.md)  
 [<span data-ttu-id="97a82-261">İki Dizinin Küme Kesişimini Döndürme</span><span class="sxs-lookup"><span data-stu-id="97a82-261">Return the Set Intersection of Two Sequences</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/return-the-set-intersection-of-two-sequences.md)  
 [<span data-ttu-id="97a82-262">İki Dizinin Küme Birleşimini Döndürme</span><span class="sxs-lookup"><span data-stu-id="97a82-262">Return the Set Union of Two Sequences</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/return-the-set-union-of-two-sequences.md)
