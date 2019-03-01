---
title: Aggregate Tümcesi (Visual Basic)
ms.date: 08/28/2018
f1_keywords:
- vb.QueryAggregateIn
- vb.QueryAggregate
- vb.QueryAggregateInto
helpviewer_keywords:
- Aggregate clause [Visual Basic]
- Aggregate statement [Visual Basic]
- queries [Visual Basic], Aggregate
ms.assetid: 1315a814-5db6-4077-b34b-b141e11cc0eb
ms.openlocfilehash: 21781db637c71abbbe9366bc95b6ee4c89ac2246
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/28/2019
ms.locfileid: "56981965"
---
# <a name="aggregate-clause-visual-basic"></a><span data-ttu-id="4d643-102">Aggregate Tümcesi (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4d643-102">Aggregate Clause (Visual Basic)</span></span>
<span data-ttu-id="4d643-103">Bir veya daha fazla toplama işlevleri, bir koleksiyon için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="4d643-103">Applies one or more aggregate functions to a collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4d643-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="4d643-104">Syntax</span></span>  
  
```  
Aggregate element [As type] In collection _  
  [, element2 [As type2] In collection2, [...]]  
  [ clause ]  
  Into expressionList  
```  
  
## <a name="parts"></a><span data-ttu-id="4d643-105">Bölümler</span><span class="sxs-lookup"><span data-stu-id="4d643-105">Parts</span></span>  
  
|<span data-ttu-id="4d643-106">Terim</span><span class="sxs-lookup"><span data-stu-id="4d643-106">Term</span></span>|<span data-ttu-id="4d643-107">Tanım</span><span class="sxs-lookup"><span data-stu-id="4d643-107">Definition</span></span>|  
|---|---|  
|`element`|<span data-ttu-id="4d643-108">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="4d643-108">Required.</span></span> <span data-ttu-id="4d643-109">Değişken koleksiyonu öğelerinde yineleme yapmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="4d643-109">Variable used to iterate through the elements of the collection.</span></span>|  
|`type`|<span data-ttu-id="4d643-110">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="4d643-110">Optional.</span></span> <span data-ttu-id="4d643-111">Türünü `element`.</span><span class="sxs-lookup"><span data-stu-id="4d643-111">The type of `element`.</span></span> <span data-ttu-id="4d643-112">Tür yok belirtilirse, türü `element` içinden gösterilen `collection`.</span><span class="sxs-lookup"><span data-stu-id="4d643-112">If no type is specified, the type of `element` is inferred from `collection`.</span></span>|  
|`collection`|<span data-ttu-id="4d643-113">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="4d643-113">Required.</span></span> <span data-ttu-id="4d643-114">Üzerinde çalışılacak koleksiyonuna başvuruyor.</span><span class="sxs-lookup"><span data-stu-id="4d643-114">Refers to the collection to operate on.</span></span>|  
|`clause`|<span data-ttu-id="4d643-115">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="4d643-115">Optional.</span></span> <span data-ttu-id="4d643-116">Bir veya daha fazla yan tümcesi gibi sorgu bir `Where` aggregate yan tümcesi veya yan tümceyi uygulamak için sorgu sonucu iyileştirmek için yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="4d643-116">One or more query clauses, such as a `Where` clause, to refine the query result to apply the aggregate clause or clauses to.</span></span>|  
|`expressionList`|<span data-ttu-id="4d643-117">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="4d643-117">Required.</span></span> <span data-ttu-id="4d643-118">Koleksiyona uygulamak için bir toplama işlevi tanımlayan bir veya daha fazla virgülle ayrılmış ifadeler.</span><span class="sxs-lookup"><span data-stu-id="4d643-118">One or more comma-delimited expressions that identify an aggregate function to apply to the collection.</span></span> <span data-ttu-id="4d643-119">Sorgu sonucu için bir üye adı belirtmek için bir toplama işlevi için bir diğer ad uygulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4d643-119">You can apply an alias to an aggregate function to specify a member name for the query result.</span></span> <span data-ttu-id="4d643-120">Takma ad sağlanmazsa, toplama işlevinin adı kullanılır.</span><span class="sxs-lookup"><span data-stu-id="4d643-120">If no alias is supplied, the name of the aggregate function is used.</span></span> <span data-ttu-id="4d643-121">Örnekler için bu konunun ilerleyen bölümlerinde toplama işlevleri hakkındaki bölüme bakın.</span><span class="sxs-lookup"><span data-stu-id="4d643-121">For examples, see the section about aggregate functions later in this topic.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4d643-122">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="4d643-122">Remarks</span></span>  
 <span data-ttu-id="4d643-123">`Aggregate` Yan tümcesi, sorgularınızdaki toplama işlevleri eklemek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="4d643-123">The `Aggregate` clause can be used to include aggregate functions in your queries.</span></span> <span data-ttu-id="4d643-124">Toplama işlevleri, bir dizi üzerinde denetimleri ve hesaplamalar gerçekleştirmek ve tek bir değer döndürür.</span><span class="sxs-lookup"><span data-stu-id="4d643-124">Aggregate functions perform checks and computations over a set of values and return a single value.</span></span> <span data-ttu-id="4d643-125">Sorgu sonuç türü üyesi'ı kullanarak hesaplanan değer erişebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4d643-125">You can access the computed value by using a member of the query result type.</span></span> <span data-ttu-id="4d643-126">Kullanabileceğiniz standart toplama işlevleri `All`, `Any`, `Average`, `Count`, `LongCount`, `Max`, `Min`, ve `Sum` işlevleri.</span><span class="sxs-lookup"><span data-stu-id="4d643-126">The standard aggregate functions that you can use are the `All`, `Any`, `Average`, `Count`, `LongCount`, `Max`, `Min`, and `Sum` functions.</span></span> <span data-ttu-id="4d643-127">Bu işlevler, toplamlar SQL bilginiz geliştiriciler sahibisiniz.</span><span class="sxs-lookup"><span data-stu-id="4d643-127">These functions are familiar to developers who are familiar with aggregates in SQL.</span></span> <span data-ttu-id="4d643-128">Bunlar, bu konunun aşağıdaki bölümde açıklanmıştır.</span><span class="sxs-lookup"><span data-stu-id="4d643-128">They are described in the following section of this topic.</span></span>  
  
 <span data-ttu-id="4d643-129">Bir toplama işlevi sonucu sorgu sonucu bir sorgu sonuç türünü alan olarak dahil edilir.</span><span class="sxs-lookup"><span data-stu-id="4d643-129">The result of an aggregate function is included in the query result as a field of the query result type.</span></span> <span data-ttu-id="4d643-130">Toplam değer tutacak sorgu sonuç türü üyesi adını belirtmek toplama işlevi sonucu için bir diğer ad sağlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4d643-130">You can supply an alias for the aggregate function result to specify the name of the member of the query result type that will hold the aggregate value.</span></span> <span data-ttu-id="4d643-131">Takma ad sağlanmazsa, toplama işlevinin adı kullanılır.</span><span class="sxs-lookup"><span data-stu-id="4d643-131">If no alias is supplied, the name of the aggregate function is used.</span></span>  
  
 <span data-ttu-id="4d643-132">`Aggregate` Yan tümcesi bir sorgu başlayabilir veya başka bir yan tümce sorgu olarak dahil edilebilir.</span><span class="sxs-lookup"><span data-stu-id="4d643-132">The `Aggregate` clause can begin a query, or it can be included as an additional clause in a query.</span></span> <span data-ttu-id="4d643-133">Varsa `Aggregate` yan tümcesi bir sorgu başlar, belirtilen toplama işlevinin sonucu tek bir değer sonuç `Into` yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="4d643-133">If the `Aggregate` clause begins a query, the result is a single value that is the result of the aggregate function specified in the `Into` clause.</span></span> <span data-ttu-id="4d643-134">Birden fazla toplama işlevi belirtilmişse `Into` yan tümcesi, sorgunun döndürdüğü her bir toplama işlevinde sonucunu başvurmak için ayrı bir özellik ile tek bir türü `Into` yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="4d643-134">If more than one aggregate function is specified in the `Into` clause, the query returns a single type with a separate property to reference the result of each aggregate function in the `Into` clause.</span></span> <span data-ttu-id="4d643-135">Varsa `Aggregate` yan tümcesi bir sorgu içinde başka bir yan tümce olarak dahil, sorgu koleksiyonda döndürülen tür her bir toplama işlevinde sonucunu başvurmak için ayrı bir özelliğe sahiptir `Into` yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="4d643-135">If the `Aggregate` clause is included as an additional clause in a query, the type returned in the query collection will have a separate property to reference the result of each aggregate function in the `Into` clause.</span></span>  
  
## <a name="aggregate-functions"></a><span data-ttu-id="4d643-136">Toplama İşlevleri</span><span class="sxs-lookup"><span data-stu-id="4d643-136">Aggregate Functions</span></span>

<span data-ttu-id="4d643-137">Kullanılabilir standart toplama işlevleri şunlardır `Aggregate` yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="4d643-137">The following are the standard aggregate functions that can be used with the `Aggregate` clause.</span></span>  
  
### <a name="all"></a><span data-ttu-id="4d643-138">Tümü</span><span class="sxs-lookup"><span data-stu-id="4d643-138">All</span></span>

<span data-ttu-id="4d643-139">Döndürür `true` koleksiyondaki tüm öğeler belirtilen bir koşulu; karşılıyorsanız, döndürür, aksi takdirde `false`.</span><span class="sxs-lookup"><span data-stu-id="4d643-139">Returns `true` if all elements in the collection satisfy a specified condition; otherwise returns `false`.</span></span> <span data-ttu-id="4d643-140">Bir örnek verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="4d643-140">The following is an example:</span></span>

 [!code-vb[VbSimpleQuerySamples#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#5)]

### <a name="any"></a><span data-ttu-id="4d643-141">Tüm</span><span class="sxs-lookup"><span data-stu-id="4d643-141">Any</span></span>

<span data-ttu-id="4d643-142">Döndürür `true` koleksiyondaki herhangi bir öğeyi; belirtilen bir koşulu karşılıyorsa döndürür, aksi takdirde `false`.</span><span class="sxs-lookup"><span data-stu-id="4d643-142">Returns `true` if any element in the collection satisfies a specified condition; otherwise returns `false`.</span></span> <span data-ttu-id="4d643-143">Bir örnek verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="4d643-143">The following is an example:</span></span>

 [!code-vb[VbSimpleQuerySamples#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#6)]

### <a name="average"></a><span data-ttu-id="4d643-144">Ortalama</span><span class="sxs-lookup"><span data-stu-id="4d643-144">Average</span></span>

<span data-ttu-id="4d643-145">Koleksiyondaki tüm öğelerin ortalamasını hesaplar veya koleksiyondaki tüm öğeler için sağlanan bir ifade sonucunu hesaplar.</span><span class="sxs-lookup"><span data-stu-id="4d643-145">Computes the average of all elements in the collection, or computes a supplied expression for all elements in the collection.</span></span> <span data-ttu-id="4d643-146">Bir örnek verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="4d643-146">The following is an example:</span></span>

 [!code-vb[VbSimpleQuerySamples#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#7)]

### <a name="count"></a><span data-ttu-id="4d643-147">Sayı</span><span class="sxs-lookup"><span data-stu-id="4d643-147">Count</span></span>

<span data-ttu-id="4d643-148">Koleksiyondaki öğe sayısını sayar.</span><span class="sxs-lookup"><span data-stu-id="4d643-148">Counts the number of elements in the collection.</span></span> <span data-ttu-id="4d643-149">İsteğe bağlı bir tedarik `Boolean` ifade yalnızca bir koşulu karşılayan koleksiyondaki öğe sayısı.</span><span class="sxs-lookup"><span data-stu-id="4d643-149">You can supply an optional `Boolean` expression to count only the number of elements in the collection that satisfy a condition.</span></span> <span data-ttu-id="4d643-150">Bir örnek verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="4d643-150">The following is an example:</span></span>

 [!code-vb[VbSimpleQuerySamples#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#8)]

### <a name="group"></a><span data-ttu-id="4d643-151">Grup</span><span class="sxs-lookup"><span data-stu-id="4d643-151">Group</span></span>

<span data-ttu-id="4d643-152">Sonucu olarak gruplandırılır sorgu sonuçları başvurduğu bir `Group By` veya `Group Join` yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="4d643-152">Refers to query results that are grouped as a result of a `Group By` or `Group Join` clause.</span></span> <span data-ttu-id="4d643-153">`Group` İşlev, yalnızca geçerli `Into` yan tümcesi bir `Group By` veya `Group Join` yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="4d643-153">The `Group` function is valid only in the `Into` clause of a `Group By` or `Group Join` clause.</span></span> <span data-ttu-id="4d643-154">Daha fazla bilgi ve örnekler için bkz. [Group yan tümcesi tarafından](../../../visual-basic/language-reference/queries/group-by-clause.md) ve [Group JOIN yan tümcesi](../../../visual-basic/language-reference/queries/group-join-clause.md).</span><span class="sxs-lookup"><span data-stu-id="4d643-154">For more information and examples, see [Group By Clause](../../../visual-basic/language-reference/queries/group-by-clause.md) and [Group Join Clause](../../../visual-basic/language-reference/queries/group-join-clause.md).</span></span>

### <a name="longcount"></a><span data-ttu-id="4d643-155">LongCount</span><span class="sxs-lookup"><span data-stu-id="4d643-155">LongCount</span></span>

<span data-ttu-id="4d643-156">Koleksiyondaki öğe sayısını sayar.</span><span class="sxs-lookup"><span data-stu-id="4d643-156">Counts the number of elements in the collection.</span></span> <span data-ttu-id="4d643-157">İsteğe bağlı bir tedarik `Boolean` ifade yalnızca bir koşulu karşılayan koleksiyondaki öğe sayısı.</span><span class="sxs-lookup"><span data-stu-id="4d643-157">You can supply an optional `Boolean` expression to count only the number of elements in the collection that satisfy a condition.</span></span> <span data-ttu-id="4d643-158">Sonuç olarak döndüren bir `Long`.</span><span class="sxs-lookup"><span data-stu-id="4d643-158">Returns the result as a `Long`.</span></span> <span data-ttu-id="4d643-159">Bir örnek için bkz `Count` toplama işlevi.</span><span class="sxs-lookup"><span data-stu-id="4d643-159">For an example, see the `Count` aggregate function.</span></span>

### <a name="max"></a><span data-ttu-id="4d643-160">Maks.</span><span class="sxs-lookup"><span data-stu-id="4d643-160">Max</span></span>

<span data-ttu-id="4d643-161">Koleksiyondan maksimum değeri hesaplar ve koleksiyondaki tüm öğeler için sağlanan bir ifadeyi hesaplar.</span><span class="sxs-lookup"><span data-stu-id="4d643-161">Computes the maximum value from the collection, or computes a supplied expression for all elements in the collection.</span></span> <span data-ttu-id="4d643-162">Bir örnek verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="4d643-162">The following is an example:</span></span>

 [!code-vb[VbSimpleQuerySamples#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#9)]

### <a name="min"></a><span data-ttu-id="4d643-163">Min.</span><span class="sxs-lookup"><span data-stu-id="4d643-163">Min</span></span>

<span data-ttu-id="4d643-164">Koleksiyondan minimum değeri hesaplar ve koleksiyondaki tüm öğeler için sağlanan bir ifadeyi hesaplar.</span><span class="sxs-lookup"><span data-stu-id="4d643-164">Computes the minimum value from the collection, or computes a supplied expression for all elements in the collection.</span></span> <span data-ttu-id="4d643-165">Bir örnek verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="4d643-165">The following is an example:</span></span>

 [!code-vb[VbSimpleQuerySamples#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#10)]

### <a name="sum"></a><span data-ttu-id="4d643-166">Toplam</span><span class="sxs-lookup"><span data-stu-id="4d643-166">Sum</span></span>

<span data-ttu-id="4d643-167">Koleksiyondaki tüm öğelerin toplamını hesaplar ve koleksiyondaki tüm öğeler için sağlanan bir ifadeyi hesaplar.</span><span class="sxs-lookup"><span data-stu-id="4d643-167">Computes the sum of all elements in the collection, or computes a supplied expression for all elements in the collection.</span></span> <span data-ttu-id="4d643-168">Bir örnek verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="4d643-168">The following is an example:</span></span>

 [!code-vb[VbSimpleQuerySamples#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#15)]

## <a name="example"></a><span data-ttu-id="4d643-169">Örnek</span><span class="sxs-lookup"><span data-stu-id="4d643-169">Example</span></span>  

<span data-ttu-id="4d643-170">Aşağıdaki örnek nasıl kullanılacağını gösterir `Aggregate` yan tümcesi bir sorgu sonucuna toplama işlevleri uygulamak için.</span><span class="sxs-lookup"><span data-stu-id="4d643-170">The following example shows how to use the `Aggregate` clause to apply aggregate functions to a query result.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#4)]  
  
## <a name="creating-user-defined-aggregate-functions"></a><span data-ttu-id="4d643-171">Kullanıcı tanımlı toplama işlevleri oluşturma</span><span class="sxs-lookup"><span data-stu-id="4d643-171">Creating User-Defined Aggregate Functions</span></span>

 <span data-ttu-id="4d643-172">Kendi özel toplama işlevleri için genişletme yöntemleri ekleyerek bir sorgu ifadesine dahil edebileceğiniz <xref:System.Collections.Generic.IEnumerable%601> türü.</span><span class="sxs-lookup"><span data-stu-id="4d643-172">You can include your own custom aggregate functions in a query expression by adding extension methods to the <xref:System.Collections.Generic.IEnumerable%601> type.</span></span> <span data-ttu-id="4d643-173">Özel yönteminiz, ardından bir hesaplama veya toplama işlevinizi başvurmuş sıralanabilir koleksiyonun işlemi gerçekleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4d643-173">Your custom method can then perform a calculation or operation on the enumerable collection that has referenced your aggregate function.</span></span> <span data-ttu-id="4d643-174">Uzantı yöntemleri hakkında daha fazla bilgi için bkz. [genişletme yöntemleri](../../../visual-basic/programming-guide/language-features/procedures/extension-methods.md).</span><span class="sxs-lookup"><span data-stu-id="4d643-174">For more information about extension methods, see [Extension Methods](../../../visual-basic/programming-guide/language-features/procedures/extension-methods.md).</span></span>  
  
 <span data-ttu-id="4d643-175">Örneğin, aşağıdaki örnek, sayıdan oluşan bir koleksiyon ORTANCA değerini hesaplar. özel bir toplama işlevi gösterir.</span><span class="sxs-lookup"><span data-stu-id="4d643-175">For example, the following example shows a custom aggregate function that calculates the median value of a collection of numbers.</span></span> <span data-ttu-id="4d643-176">İki aşırı yükleme `Median` genişletme yöntemi.</span><span class="sxs-lookup"><span data-stu-id="4d643-176">There are two overloads of the `Median` extension method.</span></span> <span data-ttu-id="4d643-177">İlk aşırı yükleme, giriş olarak bir koleksiyon türü kabul eden `IEnumerable(Of Double)`.</span><span class="sxs-lookup"><span data-stu-id="4d643-177">The first overload accepts, as input, a collection of type `IEnumerable(Of Double)`.</span></span> <span data-ttu-id="4d643-178">Varsa `Median` toplama işlevi türü için bir sorgu alanını adlı `Double`, bu yöntem çağrılır.</span><span class="sxs-lookup"><span data-stu-id="4d643-178">If the `Median` aggregate function is called for a query field of type `Double`, this method will be called.</span></span> <span data-ttu-id="4d643-179">İkinci aşırı yüklemesi `Median` yöntemi herhangi bir genel tür geçirilebilir.</span><span class="sxs-lookup"><span data-stu-id="4d643-179">The second overload of the `Median` method can be passed any generic type.</span></span> <span data-ttu-id="4d643-180">Genel aşırı yüklemesini `Median` yöntemi başvuran ikinci bir parametre alır `Func(Of T, Double)` lambda ifadesi (bir koleksiyondan) bir tür için bir değer türüne karşılık gelen değeri olarak projeye `Double`.</span><span class="sxs-lookup"><span data-stu-id="4d643-180">The generic overload of the `Median` method takes a second parameter that references the `Func(Of T, Double)` lambda expression to project a value for a type (from a collection) as the corresponding value of type `Double`.</span></span> <span data-ttu-id="4d643-181">Ardından bir aşırı yüklemesini ORTANCA değeri hesaplama Temsilciler `Median` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="4d643-181">It then delegates the calculation of the median value to the other overload of the `Median` method.</span></span> <span data-ttu-id="4d643-182">Lambda ifadeleri hakkında daha fazla bilgi için bkz. [Lambda ifadeleri](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="4d643-182">For more information about lambda expressions, see [Lambda Expressions](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md).</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#18](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/UserDefinedAggregates.vb#18)]  
  
 <span data-ttu-id="4d643-183">Aşağıdaki örnek, çağıran örnek sorgular gösterir `Median` toplama türü koleksiyonunda işlevi `Integer`ve bir koleksiyon türü `Double`.</span><span class="sxs-lookup"><span data-stu-id="4d643-183">The following example shows sample queries that call the `Median` aggregate function on a collection of type `Integer`, and a collection of type `Double`.</span></span> <span data-ttu-id="4d643-184">Çağıran bir sorgu `Median` toplama türü koleksiyonunu işlevi `Double` aşırı yüklemesini çağırır `Median` türünde bir girdi olarak kabul eden yöntemi `Double`.</span><span class="sxs-lookup"><span data-stu-id="4d643-184">The query that calls the `Median` aggregate function on the collection of type `Double` calls the overload of the `Median` method that accepts, as input, a collection of type `Double`.</span></span> <span data-ttu-id="4d643-185">Çağıran bir sorgu `Median` toplama türü koleksiyonunu işlevi `Integer` genel aşırı yüklemesini çağırır `Median` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="4d643-185">The query that calls the `Median` aggregate function on the collection of type `Integer` calls the generic overload of the `Median` method.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#19](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/UserDefinedAggregates.vb#19)]  
  
## <a name="see-also"></a><span data-ttu-id="4d643-186">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4d643-186">See also</span></span>

- [<span data-ttu-id="4d643-187">Visual Basic'de LINQ'e giriş</span><span class="sxs-lookup"><span data-stu-id="4d643-187">Introduction to LINQ in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [<span data-ttu-id="4d643-188">Sorgular</span><span class="sxs-lookup"><span data-stu-id="4d643-188">Queries</span></span>](../../../visual-basic/language-reference/queries/index.md)
- [<span data-ttu-id="4d643-189">Select Yan Tümcesi</span><span class="sxs-lookup"><span data-stu-id="4d643-189">Select Clause</span></span>](../../../visual-basic/language-reference/queries/select-clause.md)
- [<span data-ttu-id="4d643-190">From Yan Tümcesi</span><span class="sxs-lookup"><span data-stu-id="4d643-190">From Clause</span></span>](../../../visual-basic/language-reference/queries/from-clause.md)
- [<span data-ttu-id="4d643-191">Where Yan Tümcesi</span><span class="sxs-lookup"><span data-stu-id="4d643-191">Where Clause</span></span>](../../../visual-basic/language-reference/queries/where-clause.md)
- [<span data-ttu-id="4d643-192">Group By Yan Tümcesi</span><span class="sxs-lookup"><span data-stu-id="4d643-192">Group By Clause</span></span>](../../../visual-basic/language-reference/queries/group-by-clause.md)
