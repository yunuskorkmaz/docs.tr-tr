---
title: "Standart sorgu işleci çevirisi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: a60c30fa-1e68-45fe-b984-f6abb9ede40e
caps.latest.revision: "2"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: fc99fea9b722f6c3395f6bade625a09c6e97eb08
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/17/2018
---
# <a name="standard-query-operator-translation"></a><span data-ttu-id="cedba-102">Standart sorgu işleci çevirisi</span><span class="sxs-lookup"><span data-stu-id="cedba-102">Standard Query Operator Translation</span></span>
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="cedba-103">Standart sorgu işleçleri için SQL komutlarını çevirir.</span><span class="sxs-lookup"><span data-stu-id="cedba-103"> translates Standard Query Operators to SQL commands.</span></span> <span data-ttu-id="cedba-104">Sorgu işlemcisi veritabanının SQL çeviri yürütme semantiği belirler.</span><span class="sxs-lookup"><span data-stu-id="cedba-104">The query processor of the database determines the execution semantics of SQL translation.</span></span>  
  
 <span data-ttu-id="cedba-105">Standart sorgu işleçleri karşı tanımlanmış *sıraları*.</span><span class="sxs-lookup"><span data-stu-id="cedba-105">Standard Query Operators are defined against *sequences*.</span></span> <span data-ttu-id="cedba-106">Bir sıra *sıralı* ve dizideki her öğe için başvuru kimliği dayanır.</span><span class="sxs-lookup"><span data-stu-id="cedba-106">A sequence is *ordered* and relies on reference identity for each element of the sequence.</span></span> <span data-ttu-id="cedba-107">Daha fazla bilgi için bkz: [standart sorgu işleçlerine genel bakış](http://msdn.microsoft.com/library/24cda21e-8af8-4632-b519-c404a839b9b2).</span><span class="sxs-lookup"><span data-stu-id="cedba-107">For more information, see [Standard Query Operators Overview](http://msdn.microsoft.com/library/24cda21e-8af8-4632-b519-c404a839b9b2).</span></span>  
  
 <span data-ttu-id="cedba-108">SQL ilgilenir öncelikli olarak *değerlerin kümeleri sıralanmamış*.</span><span class="sxs-lookup"><span data-stu-id="cedba-108">SQL deals primarily with *unordered sets of values*.</span></span> <span data-ttu-id="cedba-109">Sıralama olan genellikle bir açıkça belirtilen, bir sorgu sonucunu yerine Ara sonuçların uygulanan sonrası işlem.</span><span class="sxs-lookup"><span data-stu-id="cedba-109">Ordering is typically an explicitly stated, post-processing operation that is applied to the final result of a query rather than to intermediate results.</span></span> <span data-ttu-id="cedba-110">Kimlik değerleri tarafından tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="cedba-110">Identity is defined by values.</span></span> <span data-ttu-id="cedba-111">Bu nedenle, multisets ile mücadele etmek için SQL sorguları anlaşılır (*paketler*) yerine *ayarlar*.</span><span class="sxs-lookup"><span data-stu-id="cedba-111">For this reason, SQL queries are understood to deal with multisets (*bags*) instead of *sets*.</span></span>  
  
 <span data-ttu-id="cedba-112">Standart sorgu işleçleri ve SQL Server sağlayıcısı için kendi SQL çevirisi arasındaki farklar aşağıdaki paragraflara açıklamak [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="cedba-112">The following paragraphs describe the differences between the Standard Query Operators and their SQL translation for the SQL Server provider for [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span>  
  
## <a name="operator-support"></a><span data-ttu-id="cedba-113">İşleç desteği</span><span class="sxs-lookup"><span data-stu-id="cedba-113">Operator Support</span></span>  
  
### <a name="concat"></a><span data-ttu-id="cedba-114">concat</span><span class="sxs-lookup"><span data-stu-id="cedba-114">Concat</span></span>  
 <span data-ttu-id="cedba-115"><xref:System.Linq.Enumerable.Concat%2A> Yöntemi alıcı sırasını ve bağımsız değişkeni sırasını nerede aynı sıralı multisets için tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="cedba-115">The <xref:System.Linq.Enumerable.Concat%2A> method is defined for ordered multisets where the order of the receiver and the order of the argument are the same.</span></span> <span data-ttu-id="cedba-116"><xref:System.Linq.Enumerable.Concat%2A>olarak çalışır `UNION ALL` genel sıraya göre ve ardından multisets üzerinden.</span><span class="sxs-lookup"><span data-stu-id="cedba-116"><xref:System.Linq.Enumerable.Concat%2A> works as `UNION ALL` over the multisets followed by the common order.</span></span>  
  
 <span data-ttu-id="cedba-117">Sonuçları üretilen önce son adım SQL'de sıralama.</span><span class="sxs-lookup"><span data-stu-id="cedba-117">The final step is ordering in SQL before results are produced.</span></span> <span data-ttu-id="cedba-118"><xref:System.Linq.Enumerable.Concat%2A>bağımsız değişkenlerini sırasını korumaz.</span><span class="sxs-lookup"><span data-stu-id="cedba-118"><xref:System.Linq.Enumerable.Concat%2A> does not preserve the order of its arguments.</span></span> <span data-ttu-id="cedba-119">Uygun sıralama emin olmak için açıkça sonuçlarını sıralama gerekir <xref:System.Linq.Enumerable.Concat%2A>.</span><span class="sxs-lookup"><span data-stu-id="cedba-119">To ensure appropriate ordering, you must explicitly order the results of <xref:System.Linq.Enumerable.Concat%2A>.</span></span>  
  
### <a name="intersect-except-union"></a><span data-ttu-id="cedba-120">Dışında UNION, INTERSECT</span><span class="sxs-lookup"><span data-stu-id="cedba-120">Intersect, Except, Union</span></span>  
 <span data-ttu-id="cedba-121"><xref:System.Linq.Enumerable.Intersect%2A> Ve <xref:System.Linq.Enumerable.Except%2A> yöntemleri yalnızca kümeleri üzerinde iyi tanımlanmış.</span><span class="sxs-lookup"><span data-stu-id="cedba-121">The <xref:System.Linq.Enumerable.Intersect%2A> and <xref:System.Linq.Enumerable.Except%2A> methods are well defined only on sets.</span></span> <span data-ttu-id="cedba-122">Multisets anlamları tanımlanmamıştır.</span><span class="sxs-lookup"><span data-stu-id="cedba-122">The semantics for multisets is undefined.</span></span>  
  
 <span data-ttu-id="cedba-123"><xref:System.Linq.Enumerable.Union%2A> Yöntemi multisets için (etkili bir şekilde UNION ALL yan tümcesi SQL sonuç) multisets sırasız birleşimini olarak tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="cedba-123">The <xref:System.Linq.Enumerable.Union%2A> method is defined for multisets as the unordered concatenation of the multisets (effectively the result of the UNION ALL clause in SQL).</span></span>  
  
### <a name="take-skip"></a><span data-ttu-id="cedba-124">Al, Atla</span><span class="sxs-lookup"><span data-stu-id="cedba-124">Take, Skip</span></span>  
 <span data-ttu-id="cedba-125"><xref:System.Linq.Enumerable.Take%2A>ve <xref:System.Linq.Enumerable.Skip%2A> yöntemleri yalnızca karşı iyi tanımlanmış *kümeleri sıralı*.</span><span class="sxs-lookup"><span data-stu-id="cedba-125"><xref:System.Linq.Enumerable.Take%2A> and <xref:System.Linq.Enumerable.Skip%2A> methods are well defined only against *ordered sets*.</span></span> <span data-ttu-id="cedba-126">Sırasız kümeleri veya multisets anlamları tanımlanmamış.</span><span class="sxs-lookup"><span data-stu-id="cedba-126">The semantics for unordered sets or multisets are undefined.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="cedba-127"><xref:System.Linq.Enumerable.Take%2A>ve <xref:System.Linq.Enumerable.Skip%2A> SQL Server 2000 karşı sorgularda kullanıldığında belirli sınırlamaları vardır.</span><span class="sxs-lookup"><span data-stu-id="cedba-127"><xref:System.Linq.Enumerable.Take%2A> and <xref:System.Linq.Enumerable.Skip%2A> have certain limitations when they are used in queries against SQL Server 2000.</span></span> <span data-ttu-id="cedba-128">Daha fazla bilgi için "Atlayın ve SQL Server 2000'de özel durumlar alın" girdisinde bkz [sorun giderme](../../../../../../docs/framework/data/adonet/sql/linq/troubleshooting.md).</span><span class="sxs-lookup"><span data-stu-id="cedba-128">For more information, see the "Skip and Take Exceptions in SQL Server 2000" entry in [Troubleshooting](../../../../../../docs/framework/data/adonet/sql/linq/troubleshooting.md).</span></span>  
  
 <span data-ttu-id="cedba-129">SQL'de sıralama sınırlamalar nedeniyle [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] yöntemi için bu yöntemlerin bağımsız değişkeni sıralama taşımayı dener.</span><span class="sxs-lookup"><span data-stu-id="cedba-129">Because of limitations on ordering in SQL, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] tries to move the ordering of the argument of these methods to the result of the method.</span></span> <span data-ttu-id="cedba-130">Örneğin, aşağıdakileri göz önünde bulundurun [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] sorgu:</span><span class="sxs-lookup"><span data-stu-id="cedba-130">For example, consider the following [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] query:</span></span>  
  
 [!code-csharp[DLinqSQOTranslation#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSQOTranslation/cs/Program.cs#1)]
 [!code-vb[DLinqSQOTranslation#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSQOTranslation/vb/Module1.vb#1)]  
  
 <span data-ttu-id="cedba-131">Bu kodun oluşturulan SQL gibi sonuna sıralama taşır:</span><span class="sxs-lookup"><span data-stu-id="cedba-131">The generated SQL for this code moves the ordering to the end, as follows:</span></span>  
  
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
  
 <span data-ttu-id="cedba-132">Tüm belirtilen sıralama ne zaman tutarlı olması gerektiğini belirgin hale <xref:System.Linq.Enumerable.Take%2A> ve <xref:System.Linq.Enumerable.Skip%2A> birbirine zincirlenmiş.</span><span class="sxs-lookup"><span data-stu-id="cedba-132">It becomes obvious that all the specified ordering must be consistent when <xref:System.Linq.Enumerable.Take%2A> and <xref:System.Linq.Enumerable.Skip%2A> are chained together.</span></span> <span data-ttu-id="cedba-133">Aksi takdirde, sonuçları tanımlanmamış.</span><span class="sxs-lookup"><span data-stu-id="cedba-133">Otherwise, the results are undefined.</span></span>  
  
 <span data-ttu-id="cedba-134">Her ikisi de <xref:System.Linq.Enumerable.Take%2A> ve <xref:System.Linq.Enumerable.Skip%2A> standart sorgu işleci belirtimine dayalı negatif olmayan, sabit tamsayı bağımsız değişkenler için iyi tanımlanmış olması.</span><span class="sxs-lookup"><span data-stu-id="cedba-134">Both <xref:System.Linq.Enumerable.Take%2A> and <xref:System.Linq.Enumerable.Skip%2A> are well-defined for non-negative, constant integral arguments based on the Standard Query Operator specification.</span></span>  
  
### <a name="operators-with-no-translation"></a><span data-ttu-id="cedba-135">Çeviri işleçleri</span><span class="sxs-lookup"><span data-stu-id="cedba-135">Operators with No Translation</span></span>  
 <span data-ttu-id="cedba-136">Aşağıdaki yöntemlerden tarafından çevrilmesi değil [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="cedba-136">The following methods are not translated by [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span> <span data-ttu-id="cedba-137">En yaygın nedeni, sırasız multisets ve dizilerinin arasındaki farktır.</span><span class="sxs-lookup"><span data-stu-id="cedba-137">The most common reason is the difference between unordered multisets and sequences.</span></span>  
  
|<span data-ttu-id="cedba-138">İşleçler</span><span class="sxs-lookup"><span data-stu-id="cedba-138">Operators</span></span>|<span data-ttu-id="cedba-139">Stratejinin</span><span class="sxs-lookup"><span data-stu-id="cedba-139">Rationale</span></span>|  
|---------------|---------------|  
|<span data-ttu-id="cedba-140"><xref:System.Linq.Enumerable.TakeWhile%2A>, <xref:System.Linq.Enumerable.SkipWhile%2A></span><span class="sxs-lookup"><span data-stu-id="cedba-140"><xref:System.Linq.Enumerable.TakeWhile%2A>, <xref:System.Linq.Enumerable.SkipWhile%2A></span></span>|<span data-ttu-id="cedba-141">SQL sorguları sıraları üzerinde multisets çalışmayabilir.</span><span class="sxs-lookup"><span data-stu-id="cedba-141">SQL queries operate on multisets, not on sequences.</span></span> <span data-ttu-id="cedba-142">`ORDER BY`Son yan tümce sonuçları uygulanmış olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="cedba-142">`ORDER BY` must be the last clause applied to the results.</span></span> <span data-ttu-id="cedba-143">Bu nedenle, bu iki yöntem için genel amaçlı çeviri yok.</span><span class="sxs-lookup"><span data-stu-id="cedba-143">For this reason, there is no general-purpose translation for these two methods.</span></span>|  
|<xref:System.Linq.Enumerable.Reverse%2A>|<span data-ttu-id="cedba-144">Bu yöntemin çeviri sıralanmış bir küme için mümkün olmakla birlikte tarafından şu anda çevrilmemiştir [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="cedba-144">Translation of this method is possible for an ordered set but is not currently translated by [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span>|  
|<span data-ttu-id="cedba-145"><xref:System.Linq.Enumerable.Last%2A>, <xref:System.Linq.Enumerable.LastOrDefault%2A></span><span class="sxs-lookup"><span data-stu-id="cedba-145"><xref:System.Linq.Enumerable.Last%2A>, <xref:System.Linq.Enumerable.LastOrDefault%2A></span></span>|<span data-ttu-id="cedba-146">Bu yöntemlerin çeviri sıralanmış bir küme için mümkün olmakla birlikte tarafından şu anda çevrilmemiştir [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="cedba-146">Translation of these methods is possible for an ordered set but is not currently translated by [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span>|  
|<span data-ttu-id="cedba-147"><xref:System.Linq.Enumerable.ElementAt%2A>, <xref:System.Linq.Enumerable.ElementAtOrDefault%2A></span><span class="sxs-lookup"><span data-stu-id="cedba-147"><xref:System.Linq.Enumerable.ElementAt%2A>, <xref:System.Linq.Enumerable.ElementAtOrDefault%2A></span></span>|<span data-ttu-id="cedba-148">SQL sorguları dizine sıraları üzerinde multisets çalışmayabilir.</span><span class="sxs-lookup"><span data-stu-id="cedba-148">SQL queries operate on multisets, not on indexable sequences.</span></span>|  
|<span data-ttu-id="cedba-149"><xref:System.Linq.Enumerable.DefaultIfEmpty%2A>(varsayılan arg ile aşırı yükleme)</span><span class="sxs-lookup"><span data-stu-id="cedba-149"><xref:System.Linq.Enumerable.DefaultIfEmpty%2A> (overload with default arg)</span></span>|<span data-ttu-id="cedba-150">Genel olarak, varsayılan bir değer için rasgele bir tanımlama grubu belirtilemez.</span><span class="sxs-lookup"><span data-stu-id="cedba-150">In general, a default value cannot be specified for an arbitrary tuple.</span></span> <span data-ttu-id="cedba-151">Diziler için null değerler dış birleştirmeler aracılığıyla bazı durumlarda mümkün olabilir.</span><span class="sxs-lookup"><span data-stu-id="cedba-151">Null values for tuples are possible in some cases through outer joins.</span></span>|  
  
## <a name="expression-translation"></a><span data-ttu-id="cedba-152">İfade çevirisi</span><span class="sxs-lookup"><span data-stu-id="cedba-152">Expression Translation</span></span>  
  
### <a name="null-semantics"></a><span data-ttu-id="cedba-153">Null semantiği</span><span class="sxs-lookup"><span data-stu-id="cedba-153">Null semantics</span></span>  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="cedba-154">SQL'de null karşılaştırma semantiği getirmez.</span><span class="sxs-lookup"><span data-stu-id="cedba-154"> does not impose null comparison semantics on SQL.</span></span> <span data-ttu-id="cedba-155">Karşılaştırma işleçleri sözdizimsel olarak SQL eşdeğerlerine çevrilir.</span><span class="sxs-lookup"><span data-stu-id="cedba-155">Comparison operators are syntactically translated to their SQL equivalents.</span></span> <span data-ttu-id="cedba-156">Bu nedenle, sunucu veya bağlantı ayarları tarafından tanımlanan SQL semantiği semantiğini yansıtır.</span><span class="sxs-lookup"><span data-stu-id="cedba-156">For this reason, the semantics reflect SQL semantics that are defined by server or connection settings.</span></span> <span data-ttu-id="cedba-157">Örneğin, iki null değerler varsayılan SQL Server Ayarları altında eşit olarak kabul edilir, ancak semantiğini değiştirmek için ayarları değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="cedba-157">For example, two null values are considered unequal under default SQL Server settings, but you can change the settings to change the semantics.</span></span> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="cedba-158">sorguları dönüştürdüğünde sunucu ayarlarını dikkate almaz.</span><span class="sxs-lookup"><span data-stu-id="cedba-158"> does not consider server settings when it translates queries.</span></span>  
  
 <span data-ttu-id="cedba-159">Değişmez değer null ile bir karşılaştırması için uygun SQL sürümü çevrilir (`is null` veya `is not null`).</span><span class="sxs-lookup"><span data-stu-id="cedba-159">A comparison with the literal null is translated to the appropriate SQL version (`is null` or `is not null`).</span></span>  
  
 <span data-ttu-id="cedba-160">Değeri `null` harmanlamasında SQL Server tarafından tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="cedba-160">The value of `null` in collation is defined by SQL Server.</span></span> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="cedba-161">harmanlama değiştirmez.</span><span class="sxs-lookup"><span data-stu-id="cedba-161"> does not change the collation.</span></span>  
  
### <a name="aggregates"></a><span data-ttu-id="cedba-162">Toplamlar</span><span class="sxs-lookup"><span data-stu-id="cedba-162">Aggregates</span></span>  
 <span data-ttu-id="cedba-163">Standart sorgu işleci toplama yöntemi <xref:System.Linq.Enumerable.Sum%2A> sıfır yalnızca null içeren bir dizi veya boş bir dizi için değerlendirir.</span><span class="sxs-lookup"><span data-stu-id="cedba-163">The Standard Query Operator aggregate method <xref:System.Linq.Enumerable.Sum%2A> evaluates to zero for an empty sequence or for a sequence that contains only nulls.</span></span> <span data-ttu-id="cedba-164">İçinde [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], SQL semantiği sol değiştirmeden, ve <xref:System.Linq.Enumerable.Sum%2A> değerlendiren `null` sıfır boş bir dizi veya yalnızca null içeren bir dizi yerine.</span><span class="sxs-lookup"><span data-stu-id="cedba-164">In [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], the semantics of SQL are left unchanged, and <xref:System.Linq.Enumerable.Sum%2A> evaluates to `null` instead of zero for an empty sequence or for a sequence that contains only nulls.</span></span>  
  
 <span data-ttu-id="cedba-165">Ara sonuçların SQL sınırlamalar uygulanır Toplamaların [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="cedba-165">SQL limitations on intermediate results apply to aggregates in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span> <span data-ttu-id="cedba-166"><xref:System.Linq.Enumerable.Sum%2A> 32 bit tamsayı miktarları hesaplanan 64-bit sonuçları kullanarak.</span><span class="sxs-lookup"><span data-stu-id="cedba-166">The <xref:System.Linq.Enumerable.Sum%2A> of 32-bit integer quantities is not computed by using 64-bit results.</span></span> <span data-ttu-id="cedba-167">Taşma için oluşabilir bir [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] çevrilmesi <xref:System.Linq.Enumerable.Sum%2A>standart sorgu işleci uygulama karşılık gelen bellek içi dizisi taşma neden olmaz olsa bile.</span><span class="sxs-lookup"><span data-stu-id="cedba-167">Overflow might occur for a [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] translation of <xref:System.Linq.Enumerable.Sum%2A>, even if the Standard Query Operator implementation does not cause an overflow for the corresponding in-memory sequence.</span></span>  
  
 <span data-ttu-id="cedba-168">Benzer şekilde, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] çevrilmesi <xref:System.Linq.Enumerable.Average%2A> değerler tamsayı hesaplanan olarak bir `integer`, olarak değil bir `double`.</span><span class="sxs-lookup"><span data-stu-id="cedba-168">Likewise, the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] translation of <xref:System.Linq.Enumerable.Average%2A> of integer values is computed as an `integer`, not as a `double`.</span></span>  
  
### <a name="entity-arguments"></a><span data-ttu-id="cedba-169">Varlık bağımsız değişkenler</span><span class="sxs-lookup"><span data-stu-id="cedba-169">Entity Arguments</span></span>  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="cedba-170">varlık türleri kullanılmak üzere etkinleştirir <xref:System.Linq.Enumerable.GroupBy%2A> ve <xref:System.Linq.Enumerable.OrderBy%2A> yöntemleri.</span><span class="sxs-lookup"><span data-stu-id="cedba-170"> enables entity types to be used in the <xref:System.Linq.Enumerable.GroupBy%2A> and <xref:System.Linq.Enumerable.OrderBy%2A> methods.</span></span> <span data-ttu-id="cedba-171">Bu işleçlere çeviriyi türünde bir bağımsız değişken kullanımını bu türdeki tüm üyelerin belirtmek için eşdeğer olarak kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="cedba-171">In the translation of these operators, the use of an argument of a type is considered to be the equivalent to specifying all members of that type.</span></span> <span data-ttu-id="cedba-172">Örneğin, aşağıdaki kodu eşdeğerdir:</span><span class="sxs-lookup"><span data-stu-id="cedba-172">For example, the following code is equivalent:</span></span>  
  
 [!code-csharp[DLinqSQOTranslation#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSQOTranslation/cs/Program.cs#2)]
 [!code-vb[DLinqSQOTranslation#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSQOTranslation/vb/Module1.vb#2)]  
  
### <a name="equatable--comparable-arguments"></a><span data-ttu-id="cedba-173">Equatable / karşılaştırılabilir bağımsız değişkenler</span><span class="sxs-lookup"><span data-stu-id="cedba-173">Equatable / Comparable Arguments</span></span>  
 <span data-ttu-id="cedba-174">Bağımsız değişkenleri eşitlik için aşağıdaki yöntemlerden birini uygulamasında gereklidir:</span><span class="sxs-lookup"><span data-stu-id="cedba-174">Equality of arguments is required in the implementation of the following methods:</span></span>  
  
 <xref:System.Linq.Enumerable.Contains%2A>  
  
 <xref:System.Linq.Enumerable.Skip%2A>  
  
 <xref:System.Linq.Enumerable.Union%2A>  
  
 <xref:System.Linq.Enumerable.Intersect%2A>  
  
 <xref:System.Linq.Enumerable.Except%2A>  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="cedba-175">Eşitlik ve karşılaştırma için destekleyen *düz* bağımsız değişkenleri, ancak değil veya sıraları içeriyor bağımsız.</span><span class="sxs-lookup"><span data-stu-id="cedba-175"> supports equality and comparison for *flat* arguments, but not for arguments that are or contain sequences.</span></span> <span data-ttu-id="cedba-176">Düz bir bağımsız değişken için bir SQL satır eşlenebilir. bir türüdür.</span><span class="sxs-lookup"><span data-stu-id="cedba-176">A flat argument is a type that can be mapped to a SQL row.</span></span> <span data-ttu-id="cedba-177">Statik olarak bir dizi içermemesi belirlenebilir bir veya daha fazla varlık türlerinin bir yansıtma düz bir bağımsız değişken olarak kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="cedba-177">A projection of one or more entity types that can be statically determined not to contain a sequence is considered a flat argument.</span></span>  
  
 <span data-ttu-id="cedba-178">Düz bağımsız değişkenleri örnekleri şunlardır:</span><span class="sxs-lookup"><span data-stu-id="cedba-178">Following are examples of flat arguments:</span></span>  
  
 [!code-csharp[DLinqSQOTranslation#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSQOTranslation/cs/Program.cs#3)]
 [!code-vb[DLinqSQOTranslation#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSQOTranslation/vb/Module1.vb#3)]  
  
 <span data-ttu-id="cedba-179">Olmayan-düz (hiyerarşik) bağımsız değişkenleri örnekleri verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="cedba-179">The following are examples of non-flat (hierarchical) arguments.</span></span>  
  
 [!code-csharp[DLinqSQOTranslation#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSQOTranslation/cs/Program.cs#4)]
 [!code-vb[DLinqSQOTranslation#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSQOTranslation/vb/Module1.vb#4)]  
  
### <a name="visual-basic-function-translation"></a><span data-ttu-id="cedba-180">Visual Basic işlevi çevirisi</span><span class="sxs-lookup"><span data-stu-id="cedba-180">Visual Basic Function Translation</span></span>  
 <span data-ttu-id="cedba-181">Visual Basic derleyici tarafından kullanılan aşağıdaki yardımcı işlevleri karşılık gelen SQL işleçler ve işlevleri dönüştürülür:</span><span class="sxs-lookup"><span data-stu-id="cedba-181">The following helper functions that are used by the Visual Basic compiler are translated to corresponding SQL operators and functions:</span></span>  
  
 `CompareString`  
  
 `DateTime.Compare`  
  
 `Decimal.Compare`  
  
 `IIf (in Microsoft.VisualBasic.Interaction)`  
  
 <span data-ttu-id="cedba-182">Dönüştürme yöntemleri:</span><span class="sxs-lookup"><span data-stu-id="cedba-182">Conversion methods:</span></span>  
  
|||||  
|-|-|-|-|  
|<span data-ttu-id="cedba-183">ToBoolean</span><span class="sxs-lookup"><span data-stu-id="cedba-183">ToBoolean</span></span>|<span data-ttu-id="cedba-184">ToSByte</span><span class="sxs-lookup"><span data-stu-id="cedba-184">ToSByte</span></span>|<span data-ttu-id="cedba-185">ToByte</span><span class="sxs-lookup"><span data-stu-id="cedba-185">ToByte</span></span>|<span data-ttu-id="cedba-186">ToChar</span><span class="sxs-lookup"><span data-stu-id="cedba-186">ToChar</span></span>|  
|<span data-ttu-id="cedba-187">ToCharArrayRankOne</span><span class="sxs-lookup"><span data-stu-id="cedba-187">ToCharArrayRankOne</span></span>|<span data-ttu-id="cedba-188">ToDate</span><span class="sxs-lookup"><span data-stu-id="cedba-188">ToDate</span></span>|<span data-ttu-id="cedba-189">ToDecimal</span><span class="sxs-lookup"><span data-stu-id="cedba-189">ToDecimal</span></span>|<span data-ttu-id="cedba-190">ToDouble</span><span class="sxs-lookup"><span data-stu-id="cedba-190">ToDouble</span></span>|  
|<span data-ttu-id="cedba-191">ToInteger</span><span class="sxs-lookup"><span data-stu-id="cedba-191">ToInteger</span></span>|<span data-ttu-id="cedba-192">ToUInteger</span><span class="sxs-lookup"><span data-stu-id="cedba-192">ToUInteger</span></span>|<span data-ttu-id="cedba-193">ToLong</span><span class="sxs-lookup"><span data-stu-id="cedba-193">ToLong</span></span>|<span data-ttu-id="cedba-194">ToULong</span><span class="sxs-lookup"><span data-stu-id="cedba-194">ToULong</span></span>|  
|<span data-ttu-id="cedba-195">ToShort</span><span class="sxs-lookup"><span data-stu-id="cedba-195">ToShort</span></span>|<span data-ttu-id="cedba-196">ToUShort</span><span class="sxs-lookup"><span data-stu-id="cedba-196">ToUShort</span></span>|<span data-ttu-id="cedba-197">ToSingle</span><span class="sxs-lookup"><span data-stu-id="cedba-197">ToSingle</span></span>|<span data-ttu-id="cedba-198">ToString</span><span class="sxs-lookup"><span data-stu-id="cedba-198">ToString</span></span>|  
  
## <a name="inheritance-support"></a><span data-ttu-id="cedba-199">Devralma desteği</span><span class="sxs-lookup"><span data-stu-id="cedba-199">Inheritance Support</span></span>  
  
### <a name="inheritance-mapping-restrictions"></a><span data-ttu-id="cedba-200">Devralma eşleme kısıtlamaları</span><span class="sxs-lookup"><span data-stu-id="cedba-200">Inheritance Mapping Restrictions</span></span>  
 <span data-ttu-id="cedba-201">Daha fazla bilgi için bkz: [nasıl yapılır: eşleme devralma hiyerarşileri](../../../../../../docs/framework/data/adonet/sql/linq/how-to-map-inheritance-hierarchies.md).</span><span class="sxs-lookup"><span data-stu-id="cedba-201">For more information, see [How to: Map Inheritance Hierarchies](../../../../../../docs/framework/data/adonet/sql/linq/how-to-map-inheritance-hierarchies.md).</span></span>  
  
### <a name="inheritance-in-queries"></a><span data-ttu-id="cedba-202">Sorgularda devralma</span><span class="sxs-lookup"><span data-stu-id="cedba-202">Inheritance in Queries</span></span>  
 <span data-ttu-id="cedba-203">C# atamalar yalnızca projeksiyon desteklenir.</span><span class="sxs-lookup"><span data-stu-id="cedba-203">C# casts are supported only in projection.</span></span> <span data-ttu-id="cedba-204">Başka bir yerde kullanılan atamalar dönüştürülmez ve göz ardı edilir.</span><span class="sxs-lookup"><span data-stu-id="cedba-204">Casts that are used elsewhere are not translated and are ignored.</span></span> <span data-ttu-id="cedba-205">SQL yanı sıra işlev adları, SQL gerçekten yalnızca ortak dil çalışma zamanı (CLR) denk gerçekleştirir <xref:System.Convert>.</span><span class="sxs-lookup"><span data-stu-id="cedba-205">Aside from SQL function names, SQL really only performs the equivalent of the common language runtime (CLR) <xref:System.Convert>.</span></span> <span data-ttu-id="cedba-206">Diğer bir deyişle, SQL bir türü değeri diğerine değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="cedba-206">That is, SQL can change the value of one type to another.</span></span> <span data-ttu-id="cedba-207">Başka bir tür olarak aynı BITS reinterpreting hiçbir kavramı olduğundan cast CLR'ın eşdeğeri yoktur.</span><span class="sxs-lookup"><span data-stu-id="cedba-207">There is no equivalent of CLR cast because there is no concept of reinterpreting the same bits as those of another type.</span></span> <span data-ttu-id="cedba-208">C# cast works neden yalnızca yerel olarak olmasıdır.</span><span class="sxs-lookup"><span data-stu-id="cedba-208">That is why a C# cast works only locally.</span></span> <span data-ttu-id="cedba-209">Düğümlerde değil.</span><span class="sxs-lookup"><span data-stu-id="cedba-209">It is not remoted.</span></span>  
  
 <span data-ttu-id="cedba-210">İşleçler `is` ve `as`ve `GetType` yöntem sınırlı değildir `Select` işleci.</span><span class="sxs-lookup"><span data-stu-id="cedba-210">The operators, `is` and `as`, and the `GetType` method are not restricted to the `Select` operator.</span></span> <span data-ttu-id="cedba-211">Bunlar ayrıca diğer sorgu işleçleri kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="cedba-211">They can be used in other query operators also.</span></span>  
  
## <a name="sql-server-2008-support"></a><span data-ttu-id="cedba-212">SQL Server 2008 Support</span><span class="sxs-lookup"><span data-stu-id="cedba-212">SQL Server 2008 Support</span></span>  
 <span data-ttu-id="cedba-213">LINQ-SQL, .NET Framework 3.5 SP1 ile başlayarak, yeni bir tarih ve saat türleri SQL Server 2008 ile sunulan eşleme destekler.</span><span class="sxs-lookup"><span data-stu-id="cedba-213">Starting with the .NET Framework 3.5 SP1, LINQ to SQL supports mapping to new date and time types introduced with SQL Server 2008.</span></span> <span data-ttu-id="cedba-214">Ancak, bu yeni tür eşlenen değerleri karşı çalışırken kullanabileceğiniz SQL sorgu işleçleri için LINQ için bazı kısıtlamalar vardır.</span><span class="sxs-lookup"><span data-stu-id="cedba-214">But, there are some limitations to the LINQ to SQL query operators that you can use when operating against values mapped to these new types.</span></span>  
  
### <a name="unsupported-query-operators"></a><span data-ttu-id="cedba-215">Desteklenmeyen sorgu işleçleri</span><span class="sxs-lookup"><span data-stu-id="cedba-215">Unsupported Query Operators</span></span>  
 <span data-ttu-id="cedba-216">Aşağıdaki sorgu işleçleri yeni SQL Server tarih ve saat türleri eşlenen değerler desteklenmez: `DATETIME2`, `DATE`, `TIME`, ve `DATETIMEOFFSET`.</span><span class="sxs-lookup"><span data-stu-id="cedba-216">The following query operators are not supported on values mapped to the new SQL Server date and time types: `DATETIME2`, `DATE`, `TIME`, and `DATETIMEOFFSET`.</span></span>  
  
-   `Aggregate`  
  
-   `Average`  
  
-   `LastOrDefault`  
  
-   `OfType`  
  
-   `Sum`  
  
 <span data-ttu-id="cedba-217">Bu SQL Server tarih ve saat türler için eşleme hakkında daha fazla bilgi için bkz: [SQL CLR türü eşlemesi](../../../../../../docs/framework/data/adonet/sql/linq/sql-clr-type-mapping.md).</span><span class="sxs-lookup"><span data-stu-id="cedba-217">For more information about mapping to these SQL Server date and time types, see [SQL-CLR Type Mapping](../../../../../../docs/framework/data/adonet/sql/linq/sql-clr-type-mapping.md).</span></span>  
  
## <a name="sql-server-2005-support"></a><span data-ttu-id="cedba-218">SQL Server 2005 desteği</span><span class="sxs-lookup"><span data-stu-id="cedba-218">SQL Server 2005 Support</span></span>  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="cedba-219">Aşağıdaki SQL Server 2005 özellikleri desteklemez:</span><span class="sxs-lookup"><span data-stu-id="cedba-219"> does not support the following SQL Server 2005 features:</span></span>  
  
-   <span data-ttu-id="cedba-220">Saklı yordamlar SQL CLR yazılır.</span><span class="sxs-lookup"><span data-stu-id="cedba-220">Stored procedures written for SQL CLR.</span></span>  
  
-   <span data-ttu-id="cedba-221">Kullanıcı tanımlı tür.</span><span class="sxs-lookup"><span data-stu-id="cedba-221">User-defined type.</span></span>  
  
-   <span data-ttu-id="cedba-222">XML sorgu özellikleri.</span><span class="sxs-lookup"><span data-stu-id="cedba-222">XML query features.</span></span>  
  
## <a name="sql-server-2000-support"></a><span data-ttu-id="cedba-223">SQL Server 2000 desteği</span><span class="sxs-lookup"><span data-stu-id="cedba-223">SQL Server 2000 Support</span></span>  
 <span data-ttu-id="cedba-224">Aşağıdaki [!INCLUDE[ss2k](../../../../../../includes/ss2k-md.md)] sınırlamaları (karşılaştırılan [!INCLUDE[sqprsqext](../../../../../../includes/sqprsqext-md.md)]) etkileyen [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] destekler.</span><span class="sxs-lookup"><span data-stu-id="cedba-224">The following [!INCLUDE[ss2k](../../../../../../includes/ss2k-md.md)] limitations (compared to [!INCLUDE[sqprsqext](../../../../../../includes/sqprsqext-md.md)]) affect [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] support.</span></span>  
  
### <a name="cross-apply-and-outer-apply-operators"></a><span data-ttu-id="cedba-225">Çapraz uygulama ve dış işleçleri Uygula</span><span class="sxs-lookup"><span data-stu-id="cedba-225">Cross Apply and Outer Apply Operators</span></span>  
 <span data-ttu-id="cedba-226">Bu işleçlere kullanılamayan [!INCLUDE[ss2k](../../../../../../includes/ss2k-md.md)].</span><span class="sxs-lookup"><span data-stu-id="cedba-226">These operators are not available in [!INCLUDE[ss2k](../../../../../../includes/ss2k-md.md)].</span></span> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="cedba-227">bir dizi bunları uygun birleştirmeler ile değiştirmek için yeniden çalışır.</span><span class="sxs-lookup"><span data-stu-id="cedba-227"> tries a series of rewrites to replace them with appropriate joins.</span></span>  
  
 <span data-ttu-id="cedba-228">`Cross Apply`ve `Outer Apply` ilişki gezintilerini için oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="cedba-228">`Cross Apply` and `Outer Apply` are generated for relationship navigations.</span></span> <span data-ttu-id="cedba-229">Bu tür yeniden yazdırmaya olası sorgu kümesini iyi tanımlanmış değil.</span><span class="sxs-lookup"><span data-stu-id="cedba-229">The set of queries for which such rewrites are possible is not well defined.</span></span> <span data-ttu-id="cedba-230">Bu nedenle, desteklenen sorguları en az sayıda [!INCLUDE[ss2k](../../../../../../includes/ss2k-md.md)] ilişki Gezinti içermeyen kümesidir.</span><span class="sxs-lookup"><span data-stu-id="cedba-230">For this reason, the minimal set of queries that is supported for [!INCLUDE[ss2k](../../../../../../includes/ss2k-md.md)] is the set that does not involve relationship navigation.</span></span>  
  
### <a name="text--ntext"></a><span data-ttu-id="cedba-231">Text / ntext</span><span class="sxs-lookup"><span data-stu-id="cedba-231">text / ntext</span></span>  
 <span data-ttu-id="cedba-232">Veri türleri `text`  /  `ntext` belirli sorgu işlemleri karşı kullanılamaz `varchar(max)`  /  `nvarchar(max)`, tarafından desteklenen [!INCLUDE[sqprsqext](../../../../../../includes/sqprsqext-md.md)].</span><span class="sxs-lookup"><span data-stu-id="cedba-232">Data types `text` / `ntext` cannot be used in certain query operations against `varchar(max)` / `nvarchar(max)`, which are supported by [!INCLUDE[sqprsqext](../../../../../../includes/sqprsqext-md.md)].</span></span>  
  
 <span data-ttu-id="cedba-233">Herhangi bir çözüm, bu sınırlamaya için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="cedba-233">No resolution is available for this limitation.</span></span> <span data-ttu-id="cedba-234">Özellikle, kullanamazsınız `Distinct()` eşlendiği üyeleri içeren sonuç üzerinde `text` veya `ntext` sütun.</span><span class="sxs-lookup"><span data-stu-id="cedba-234">Specifically, you cannot use `Distinct()` on any result that contains members that are mapped to `text` or `ntext` columns.</span></span>  
  
### <a name="behavior-triggered-by-nested-queries"></a><span data-ttu-id="cedba-235">İç içe geçmiş sorgular tarafından tetiklenen davranışı</span><span class="sxs-lookup"><span data-stu-id="cedba-235">Behavior Triggered by Nested Queries</span></span>  
 [!INCLUDE[ss2k](../../../../../../includes/ss2k-md.md)]<span data-ttu-id="cedba-236">(SP4) bağlayıcı iç içe geçmiş sorgular tarafından tetiklenen olmasını sağlayan bazı özelliklere sahiptir.</span><span class="sxs-lookup"><span data-stu-id="cedba-236"> (through SP4) binder has some idiosyncrasies that are triggered by nested queries.</span></span> <span data-ttu-id="cedba-237">Bu idiosyncrasies tetikler SQL sorguları kümesini iyi tanımlanmış değil.</span><span class="sxs-lookup"><span data-stu-id="cedba-237">The set of SQL queries that triggers these idiosyncrasies is not well defined.</span></span> <span data-ttu-id="cedba-238">Bu nedenle, kümesini tanımlayamazsınız [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] sorguları SQL Server özel durumlara neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="cedba-238">For this reason, you cannot define the set of [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] queries that might cause SQL Server exceptions.</span></span>  
  
### <a name="skip-and-take-operators"></a><span data-ttu-id="cedba-239">Atla ve Al işleçleri</span><span class="sxs-lookup"><span data-stu-id="cedba-239">Skip and Take Operators</span></span>  
 <span data-ttu-id="cedba-240"><xref:System.Linq.Enumerable.Take%2A>ve <xref:System.Linq.Enumerable.Skip%2A> karşı sorgularda kullanıldığında belirli sınırlamaları vardır [!INCLUDE[ss2k](../../../../../../includes/ss2k-md.md)].</span><span class="sxs-lookup"><span data-stu-id="cedba-240"><xref:System.Linq.Enumerable.Take%2A> and <xref:System.Linq.Enumerable.Skip%2A> have certain limitations when they are used in queries against [!INCLUDE[ss2k](../../../../../../includes/ss2k-md.md)].</span></span> <span data-ttu-id="cedba-241">Daha fazla bilgi için "Atlayın ve SQL Server 2000'de özel durumlar alın" girdisinde bkz [sorun giderme](../../../../../../docs/framework/data/adonet/sql/linq/troubleshooting.md).</span><span class="sxs-lookup"><span data-stu-id="cedba-241">For more information, see the "Skip and Take Exceptions in SQL Server 2000" entry in [Troubleshooting](../../../../../../docs/framework/data/adonet/sql/linq/troubleshooting.md).</span></span>  
  
## <a name="object-materialization"></a><span data-ttu-id="cedba-242">Nesne Materialization</span><span class="sxs-lookup"><span data-stu-id="cedba-242">Object Materialization</span></span>  
 <span data-ttu-id="cedba-243">Materialization bir veya daha fazla SQL sorguları tarafından döndürülen satır CLR nesneleri oluşturur.</span><span class="sxs-lookup"><span data-stu-id="cedba-243">Materialization creates CLR objects from rows that are returned by one or more SQL queries.</span></span>  
  
-   <span data-ttu-id="cedba-244">Aşağıdaki çağrıları *yerel olarak yürütülen* materialization bir parçası olarak:</span><span class="sxs-lookup"><span data-stu-id="cedba-244">The following calls are *executed locally* as a part of materialization:</span></span>  
  
    -   <span data-ttu-id="cedba-245">Oluşturucular</span><span class="sxs-lookup"><span data-stu-id="cedba-245">Constructors</span></span>  
  
    -   <span data-ttu-id="cedba-246">`ToString`projeksiyonlar yöntemleri</span><span class="sxs-lookup"><span data-stu-id="cedba-246">`ToString` methods in projections</span></span>  
  
    -   <span data-ttu-id="cedba-247">Projeksiyonlar tür atamaları</span><span class="sxs-lookup"><span data-stu-id="cedba-247">Type casts in projections</span></span>  
  
-   <span data-ttu-id="cedba-248">İzleyin yöntemleri <xref:System.Linq.Enumerable.AsEnumerable%2A> yönteminin *yerel olarak çalıştırılan*.</span><span class="sxs-lookup"><span data-stu-id="cedba-248">Methods that follow the <xref:System.Linq.Enumerable.AsEnumerable%2A> method are *executed locally*.</span></span> <span data-ttu-id="cedba-249">Bu yöntem, hemen yürütülmesine neden olmaz.</span><span class="sxs-lookup"><span data-stu-id="cedba-249">This method does not cause immediate execution.</span></span>  
  
-   <span data-ttu-id="cedba-250">Kullanabileceğiniz bir `struct` sonuç türünün bir üyesi olarak veya bir sorgu sonucunun dönüş türü.</span><span class="sxs-lookup"><span data-stu-id="cedba-250">You can use a `struct` as the return type of a query result or as a member of the result type.</span></span> <span data-ttu-id="cedba-251">Varlıkları sınıfları olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="cedba-251">Entities are required to be classes.</span></span> <span data-ttu-id="cedba-252">Anonim türler sınıf örnekleri gerçekleştirilip ancak projeksiyon adlandırılmış yapılar (varlıklar olmayan) kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="cedba-252">Anonymous types are materialized as class instances, but named structs (non-entities) can be used in projection.</span></span>  
  
-   <span data-ttu-id="cedba-253">Dönüş türü bir sorgu sonucunun üyesi türde olabilir <xref:System.Linq.IQueryable%601>.</span><span class="sxs-lookup"><span data-stu-id="cedba-253">A member of the return type of a query result can be of type <xref:System.Linq.IQueryable%601>.</span></span> <span data-ttu-id="cedba-254">Yerel bir koleksiyon olarak gerçekleştirildiği.</span><span class="sxs-lookup"><span data-stu-id="cedba-254">It is materialized as a local collection.</span></span>  
  
-   <span data-ttu-id="cedba-255">Aşağıdaki yöntemlerden neden *hemen materialization* yöntemleri uygulanır dizisi:</span><span class="sxs-lookup"><span data-stu-id="cedba-255">The following methods cause the *immediate materialization* of the sequence that the methods are applied to:</span></span>  
  
    -   <xref:System.Linq.Enumerable.ToList%2A>  
  
    -   <xref:System.Linq.Enumerable.ToDictionary%2A>  
  
    -   <xref:System.Linq.Enumerable.ToArray%2A>  
  
## <a name="see-also"></a><span data-ttu-id="cedba-256">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="cedba-256">See Also</span></span>  
 [<span data-ttu-id="cedba-257">Başvuru</span><span class="sxs-lookup"><span data-stu-id="cedba-257">Reference</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/reference.md)  
 [<span data-ttu-id="cedba-258">Dizideki Öğeleri Döndürme veya Atlama</span><span class="sxs-lookup"><span data-stu-id="cedba-258">Return Or Skip Elements in a Sequence</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/return-or-skip-elements-in-a-sequence.md)  
 [<span data-ttu-id="cedba-259">İki Diziyi Birleştirme</span><span class="sxs-lookup"><span data-stu-id="cedba-259">Concatenate Two Sequences</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/concatenate-two-sequences.md)  
 [<span data-ttu-id="cedba-260">İki Dizi Arasındaki Küme Farkını Döndürme</span><span class="sxs-lookup"><span data-stu-id="cedba-260">Return the Set Difference Between Two Sequences</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/return-the-set-difference-between-two-sequences.md)  
 [<span data-ttu-id="cedba-261">İki Dizinin Küme Kesişimini Döndürme</span><span class="sxs-lookup"><span data-stu-id="cedba-261">Return the Set Intersection of Two Sequences</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/return-the-set-intersection-of-two-sequences.md)  
 [<span data-ttu-id="cedba-262">İki Dizinin Küme Birleşimini Döndürme</span><span class="sxs-lookup"><span data-stu-id="cedba-262">Return the Set Union of Two Sequences</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/return-the-set-union-of-two-sequences.md)
