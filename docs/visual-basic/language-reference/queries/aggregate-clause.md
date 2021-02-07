---
description: 'Daha fazla bilgi edinin: toplama tümcesi (Visual Basic)'
title: Aggregate Yan Tümcesi
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
ms.openlocfilehash: 404cb4091bc11132450cf0d8d001ce426439ece7
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99700669"
---
# <a name="aggregate-clause-visual-basic"></a><span data-ttu-id="e1dbf-103">Aggregate Tümcesi (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e1dbf-103">Aggregate Clause (Visual Basic)</span></span>

<span data-ttu-id="e1dbf-104">Bir koleksiyona bir veya daha fazla toplama işlevi uygular.</span><span class="sxs-lookup"><span data-stu-id="e1dbf-104">Applies one or more aggregate functions to a collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e1dbf-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="e1dbf-105">Syntax</span></span>  
  
```vb  
Aggregate element [As type] In collection _  
  [, element2 [As type2] In collection2, [...]]  
  [ clause ]  
  Into expressionList  
```  
  
## <a name="parts"></a><span data-ttu-id="e1dbf-106">Bölümler</span><span class="sxs-lookup"><span data-stu-id="e1dbf-106">Parts</span></span>  
  
|<span data-ttu-id="e1dbf-107">Süre</span><span class="sxs-lookup"><span data-stu-id="e1dbf-107">Term</span></span>|<span data-ttu-id="e1dbf-108">Tanım</span><span class="sxs-lookup"><span data-stu-id="e1dbf-108">Definition</span></span>|  
|---|---|  
|`element`|<span data-ttu-id="e1dbf-109">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="e1dbf-109">Required.</span></span> <span data-ttu-id="e1dbf-110">Koleksiyon öğeleri boyunca yinelemek için kullanılan değişken.</span><span class="sxs-lookup"><span data-stu-id="e1dbf-110">Variable used to iterate through the elements of the collection.</span></span>|  
|`type`|<span data-ttu-id="e1dbf-111">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="e1dbf-111">Optional.</span></span> <span data-ttu-id="e1dbf-112">Türü `element` .</span><span class="sxs-lookup"><span data-stu-id="e1dbf-112">The type of `element`.</span></span> <span data-ttu-id="e1dbf-113">Hiçbir tür belirtilmemişse, türü `element` öğesinden çıkarsanamıyor `collection` .</span><span class="sxs-lookup"><span data-stu-id="e1dbf-113">If no type is specified, the type of `element` is inferred from `collection`.</span></span>|  
|`collection`|<span data-ttu-id="e1dbf-114">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="e1dbf-114">Required.</span></span> <span data-ttu-id="e1dbf-115">Üzerinde çalışılacak koleksiyona başvurur.</span><span class="sxs-lookup"><span data-stu-id="e1dbf-115">Refers to the collection to operate on.</span></span>|  
|`clause`|<span data-ttu-id="e1dbf-116">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="e1dbf-116">Optional.</span></span> <span data-ttu-id="e1dbf-117">`Where`Toplama yan tümcesini veya yan tümceleri uygulamak üzere sorgu sonucunu daraltmak için bir yan tümce gibi bir veya daha fazla sorgu yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="e1dbf-117">One or more query clauses, such as a `Where` clause, to refine the query result to apply the aggregate clause or clauses to.</span></span>|  
|`expressionList`|<span data-ttu-id="e1dbf-118">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="e1dbf-118">Required.</span></span> <span data-ttu-id="e1dbf-119">Koleksiyona uygulanacak bir toplama işlevini tanımlayan bir veya daha fazla virgülle ayrılmış ifade.</span><span class="sxs-lookup"><span data-stu-id="e1dbf-119">One or more comma-delimited expressions that identify an aggregate function to apply to the collection.</span></span> <span data-ttu-id="e1dbf-120">Sorgu sonucu için bir üye adı belirtmek üzere bir toplama işlevine bir diğer ad uygulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e1dbf-120">You can apply an alias to an aggregate function to specify a member name for the query result.</span></span> <span data-ttu-id="e1dbf-121">Diğer ad sağlanmazsa, toplama işlevinin adı kullanılır.</span><span class="sxs-lookup"><span data-stu-id="e1dbf-121">If no alias is supplied, the name of the aggregate function is used.</span></span> <span data-ttu-id="e1dbf-122">Örnekler için, bu konunun ilerleyen kısımlarında bulunan toplama işlevleri hakkında bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="e1dbf-122">For examples, see the section about aggregate functions later in this topic.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e1dbf-123">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e1dbf-123">Remarks</span></span>  

 <span data-ttu-id="e1dbf-124">`Aggregate`Yan tümce, Sorgularınızdaki toplama işlevlerini dahil etmek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="e1dbf-124">The `Aggregate` clause can be used to include aggregate functions in your queries.</span></span> <span data-ttu-id="e1dbf-125">Toplama işlevleri, bir değerler kümesi üzerinde denetim ve hesaplamalar gerçekleştirir ve tek bir değer döndürür.</span><span class="sxs-lookup"><span data-stu-id="e1dbf-125">Aggregate functions perform checks and computations over a set of values and return a single value.</span></span> <span data-ttu-id="e1dbf-126">Sorgu sonuç türünün bir üyesini kullanarak hesaplanan değere erişebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e1dbf-126">You can access the computed value by using a member of the query result type.</span></span> <span data-ttu-id="e1dbf-127">Kullanabileceğiniz standart toplama işlevleri,,,,,, `All` `Any` `Average` `Count` `LongCount` `Max` `Min` , ve `Sum` işlevleridir.</span><span class="sxs-lookup"><span data-stu-id="e1dbf-127">The standard aggregate functions that you can use are the `All`, `Any`, `Average`, `Count`, `LongCount`, `Max`, `Min`, and `Sum` functions.</span></span> <span data-ttu-id="e1dbf-128">Bu işlevler, SQL 'deki toplamalara alışkın olan geliştiricilere tanıdık gelecektir.</span><span class="sxs-lookup"><span data-stu-id="e1dbf-128">These functions are familiar to developers who are familiar with aggregates in SQL.</span></span> <span data-ttu-id="e1dbf-129">Bunlar, bu konunun aşağıdaki bölümünde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="e1dbf-129">They are described in the following section of this topic.</span></span>  
  
 <span data-ttu-id="e1dbf-130">Toplama işlevinin sonucu sorgu sonuç türünün bir alanı olarak sorgu sonucuna dahil edilir.</span><span class="sxs-lookup"><span data-stu-id="e1dbf-130">The result of an aggregate function is included in the query result as a field of the query result type.</span></span> <span data-ttu-id="e1dbf-131">Toplama işlevi sonucu için, toplam değeri tutacak sorgu sonuç türü üyesinin adını belirtmek üzere bir diğer ad sağlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e1dbf-131">You can supply an alias for the aggregate function result to specify the name of the member of the query result type that will hold the aggregate value.</span></span> <span data-ttu-id="e1dbf-132">Diğer ad sağlanmazsa, toplama işlevinin adı kullanılır.</span><span class="sxs-lookup"><span data-stu-id="e1dbf-132">If no alias is supplied, the name of the aggregate function is used.</span></span>  
  
 <span data-ttu-id="e1dbf-133">`Aggregate`Yan tümce bir sorgu başlatabilir veya bir sorguya ek bir yan tümce olarak eklenebilir.</span><span class="sxs-lookup"><span data-stu-id="e1dbf-133">The `Aggregate` clause can begin a query, or it can be included as an additional clause in a query.</span></span> <span data-ttu-id="e1dbf-134">`Aggregate`Yan tümce bir sorgu başlıyorsa, sonuç, yan tümcesinde belirtilen toplama işlevinin sonucu olan tek bir değerdir `Into` .</span><span class="sxs-lookup"><span data-stu-id="e1dbf-134">If the `Aggregate` clause begins a query, the result is a single value that is the result of the aggregate function specified in the `Into` clause.</span></span> <span data-ttu-id="e1dbf-135">Yan tümcesinde birden fazla toplama işlevi belirtilmişse `Into` , sorgu, yan tümcesindeki her toplama işlevinin sonucuna başvurmak için ayrı bir özelliği olan tek bir tür döndürür `Into` .</span><span class="sxs-lookup"><span data-stu-id="e1dbf-135">If more than one aggregate function is specified in the `Into` clause, the query returns a single type with a separate property to reference the result of each aggregate function in the `Into` clause.</span></span> <span data-ttu-id="e1dbf-136">`Aggregate`Yan tümce bir sorguya ek bir yan tümce olarak dahil edildiğinde, sorgu koleksiyonunda döndürülen tür, yan tümcesindeki her toplama işlevinin sonucuna başvuracak ayrı bir özelliğe sahip olur `Into` .</span><span class="sxs-lookup"><span data-stu-id="e1dbf-136">If the `Aggregate` clause is included as an additional clause in a query, the type returned in the query collection will have a separate property to reference the result of each aggregate function in the `Into` clause.</span></span>  
  
## <a name="aggregate-functions"></a><span data-ttu-id="e1dbf-137">Toplama İşlevleri</span><span class="sxs-lookup"><span data-stu-id="e1dbf-137">Aggregate Functions</span></span>

<span data-ttu-id="e1dbf-138">Aşağıdaki, yan tümcesiyle kullanılabilen standart toplama işlevleridir `Aggregate` .</span><span class="sxs-lookup"><span data-stu-id="e1dbf-138">The following are the standard aggregate functions that can be used with the `Aggregate` clause.</span></span>  
  
### <a name="all"></a><span data-ttu-id="e1dbf-139">Tümü</span><span class="sxs-lookup"><span data-stu-id="e1dbf-139">All</span></span>

<span data-ttu-id="e1dbf-140">`true`Koleksiyondaki tüm öğelerin belirtilen koşulu karşılayıp karşılamadığını döndürür; Aksi takdirde döndürür `false` .</span><span class="sxs-lookup"><span data-stu-id="e1dbf-140">Returns `true` if all elements in the collection satisfy a specified condition; otherwise returns `false`.</span></span> <span data-ttu-id="e1dbf-141">Aşağıda bir örnek verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="e1dbf-141">The following is an example:</span></span>

 [!code-vb[VbSimpleQuerySamples#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#5)]

### <a name="any"></a><span data-ttu-id="e1dbf-142">Herhangi bir</span><span class="sxs-lookup"><span data-stu-id="e1dbf-142">Any</span></span>

<span data-ttu-id="e1dbf-143">`true`Koleksiyondaki herhangi bir öğenin belirtilen koşulu karşılayıp karşılamadığını döndürür; Aksi takdirde döndürür `false` .</span><span class="sxs-lookup"><span data-stu-id="e1dbf-143">Returns `true` if any element in the collection satisfies a specified condition; otherwise returns `false`.</span></span> <span data-ttu-id="e1dbf-144">Aşağıda bir örnek verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="e1dbf-144">The following is an example:</span></span>

 [!code-vb[VbSimpleQuerySamples#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#6)]

### <a name="average"></a><span data-ttu-id="e1dbf-145">Ortalama</span><span class="sxs-lookup"><span data-stu-id="e1dbf-145">Average</span></span>

<span data-ttu-id="e1dbf-146">Koleksiyondaki tüm öğelerin ortalamasını hesaplar veya koleksiyondaki tüm öğeler için sağlanan bir ifadeyi hesaplar.</span><span class="sxs-lookup"><span data-stu-id="e1dbf-146">Computes the average of all elements in the collection, or computes a supplied expression for all elements in the collection.</span></span> <span data-ttu-id="e1dbf-147">Aşağıda bir örnek verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="e1dbf-147">The following is an example:</span></span>

 [!code-vb[VbSimpleQuerySamples#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#7)]

### <a name="count"></a><span data-ttu-id="e1dbf-148">Count</span><span class="sxs-lookup"><span data-stu-id="e1dbf-148">Count</span></span>

<span data-ttu-id="e1dbf-149">Koleksiyondaki öğelerin sayısını sayar.</span><span class="sxs-lookup"><span data-stu-id="e1dbf-149">Counts the number of elements in the collection.</span></span> <span data-ttu-id="e1dbf-150">`Boolean`Koleksiyonda yalnızca bir koşulu karşılayan öğelerin sayısını saymak için isteğe bağlı bir ifade sağlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e1dbf-150">You can supply an optional `Boolean` expression to count only the number of elements in the collection that satisfy a condition.</span></span> <span data-ttu-id="e1dbf-151">Aşağıda bir örnek verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="e1dbf-151">The following is an example:</span></span>

 [!code-vb[VbSimpleQuerySamples#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#8)]

### <a name="group"></a><span data-ttu-id="e1dbf-152">Grup</span><span class="sxs-lookup"><span data-stu-id="e1dbf-152">Group</span></span>

<span data-ttu-id="e1dbf-153">, `Group By` Veya yan tümcesinin sonucu olarak gruplandırılan sorgu sonuçlarının başvurduğu anlamına gelir `Group Join` .</span><span class="sxs-lookup"><span data-stu-id="e1dbf-153">Refers to query results that are grouped as a result of a `Group By` or `Group Join` clause.</span></span> <span data-ttu-id="e1dbf-154">`Group`İşlev yalnızca `Into` `Group By` OR yan tümcesinde geçerlidir `Group Join` .</span><span class="sxs-lookup"><span data-stu-id="e1dbf-154">The `Group` function is valid only in the `Into` clause of a `Group By` or `Group Join` clause.</span></span> <span data-ttu-id="e1dbf-155">Daha fazla bilgi ve örnek için bkz. [Group by yan tümcesi](group-by-clause.md) ve [Group JOIN yan tümcesi](group-join-clause.md).</span><span class="sxs-lookup"><span data-stu-id="e1dbf-155">For more information and examples, see [Group By Clause](group-by-clause.md) and [Group Join Clause](group-join-clause.md).</span></span>

### <a name="longcount"></a><span data-ttu-id="e1dbf-156">LongCount</span><span class="sxs-lookup"><span data-stu-id="e1dbf-156">LongCount</span></span>

<span data-ttu-id="e1dbf-157">Koleksiyondaki öğelerin sayısını sayar.</span><span class="sxs-lookup"><span data-stu-id="e1dbf-157">Counts the number of elements in the collection.</span></span> <span data-ttu-id="e1dbf-158">`Boolean`Koleksiyonda yalnızca bir koşulu karşılayan öğelerin sayısını saymak için isteğe bağlı bir ifade sağlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e1dbf-158">You can supply an optional `Boolean` expression to count only the number of elements in the collection that satisfy a condition.</span></span> <span data-ttu-id="e1dbf-159">Sonucu bir olarak döndürür `Long` .</span><span class="sxs-lookup"><span data-stu-id="e1dbf-159">Returns the result as a `Long`.</span></span> <span data-ttu-id="e1dbf-160">Bir örnek için bkz `Count` . toplama işlevi.</span><span class="sxs-lookup"><span data-stu-id="e1dbf-160">For an example, see the `Count` aggregate function.</span></span>

### <a name="max"></a><span data-ttu-id="e1dbf-161">En yüksek değer</span><span class="sxs-lookup"><span data-stu-id="e1dbf-161">Max</span></span>

<span data-ttu-id="e1dbf-162">Koleksiyondaki maksimum değeri hesaplar veya koleksiyondaki tüm öğeler için sağlanan bir ifadeyi hesaplar.</span><span class="sxs-lookup"><span data-stu-id="e1dbf-162">Computes the maximum value from the collection, or computes a supplied expression for all elements in the collection.</span></span> <span data-ttu-id="e1dbf-163">Aşağıda bir örnek verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="e1dbf-163">The following is an example:</span></span>

 [!code-vb[VbSimpleQuerySamples#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#9)]

### <a name="min"></a><span data-ttu-id="e1dbf-164">Min</span><span class="sxs-lookup"><span data-stu-id="e1dbf-164">Min</span></span>

<span data-ttu-id="e1dbf-165">Koleksiyondaki en küçük değeri hesaplar veya koleksiyondaki tüm öğeler için sağlanan bir ifadeyi hesaplar.</span><span class="sxs-lookup"><span data-stu-id="e1dbf-165">Computes the minimum value from the collection, or computes a supplied expression for all elements in the collection.</span></span> <span data-ttu-id="e1dbf-166">Aşağıda bir örnek verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="e1dbf-166">The following is an example:</span></span>

 [!code-vb[VbSimpleQuerySamples#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#10)]

### <a name="sum"></a><span data-ttu-id="e1dbf-167">Sum</span><span class="sxs-lookup"><span data-stu-id="e1dbf-167">Sum</span></span>

<span data-ttu-id="e1dbf-168">Koleksiyondaki tüm öğelerin toplamını hesaplar veya koleksiyondaki tüm öğeler için sağlanan bir ifadeyi hesaplar.</span><span class="sxs-lookup"><span data-stu-id="e1dbf-168">Computes the sum of all elements in the collection, or computes a supplied expression for all elements in the collection.</span></span> <span data-ttu-id="e1dbf-169">Aşağıda bir örnek verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="e1dbf-169">The following is an example:</span></span>

 [!code-vb[VbSimpleQuerySamples#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#15)]

## <a name="example"></a><span data-ttu-id="e1dbf-170">Örnek</span><span class="sxs-lookup"><span data-stu-id="e1dbf-170">Example</span></span>  

<span data-ttu-id="e1dbf-171">Aşağıdaki örnek, `Aggregate` bir sorgu sonucuna toplama işlevleri uygulamak için yan tümcesinin nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="e1dbf-171">The following example shows how to use the `Aggregate` clause to apply aggregate functions to a query result.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#4)]  
  
## <a name="creating-user-defined-aggregate-functions"></a><span data-ttu-id="e1dbf-172">User-Defined toplama Işlevleri oluşturma</span><span class="sxs-lookup"><span data-stu-id="e1dbf-172">Creating User-Defined Aggregate Functions</span></span>

 <span data-ttu-id="e1dbf-173">Türe uzantı yöntemleri ekleyerek kendi özel toplama işlevlerinizi bir sorgu ifadesine dahil edebilirsiniz <xref:System.Collections.Generic.IEnumerable%601> .</span><span class="sxs-lookup"><span data-stu-id="e1dbf-173">You can include your own custom aggregate functions in a query expression by adding extension methods to the <xref:System.Collections.Generic.IEnumerable%601> type.</span></span> <span data-ttu-id="e1dbf-174">Özel yönteminiz, toplama işlevinizin başvurduğu sıralanabilir koleksiyonda bir hesaplama veya işlem gerçekleştirebilir.</span><span class="sxs-lookup"><span data-stu-id="e1dbf-174">Your custom method can then perform a calculation or operation on the enumerable collection that has referenced your aggregate function.</span></span> <span data-ttu-id="e1dbf-175">Uzantı yöntemleri hakkında daha fazla bilgi için bkz. [Uzantı yöntemleri](../../programming-guide/language-features/procedures/extension-methods.md).</span><span class="sxs-lookup"><span data-stu-id="e1dbf-175">For more information about extension methods, see [Extension Methods](../../programming-guide/language-features/procedures/extension-methods.md).</span></span>  
  
 <span data-ttu-id="e1dbf-176">Örneğin, aşağıdaki örnek bir sayı koleksiyonunun ortanca değerini hesaplayan özel bir toplama işlevi gösterir.</span><span class="sxs-lookup"><span data-stu-id="e1dbf-176">For example, the following example shows a custom aggregate function that calculates the median value of a collection of numbers.</span></span> <span data-ttu-id="e1dbf-177">Uzantı yönteminin iki aşırı yüklemesi vardır `Median` .</span><span class="sxs-lookup"><span data-stu-id="e1dbf-177">There are two overloads of the `Median` extension method.</span></span> <span data-ttu-id="e1dbf-178">İlk aşırı yükleme giriş olarak bir tür koleksiyonu kabul eder `IEnumerable(Of Double)` .</span><span class="sxs-lookup"><span data-stu-id="e1dbf-178">The first overload accepts, as input, a collection of type `IEnumerable(Of Double)`.</span></span> <span data-ttu-id="e1dbf-179">`Median`Toplama işlevi, türünde bir sorgu alanı için çağrılırsa `Double` , bu yöntem çağrılır.</span><span class="sxs-lookup"><span data-stu-id="e1dbf-179">If the `Median` aggregate function is called for a query field of type `Double`, this method will be called.</span></span> <span data-ttu-id="e1dbf-180">Metodun ikinci aşırı yüklemesi `Median` herhangi bir genel tür geçirilebilir.</span><span class="sxs-lookup"><span data-stu-id="e1dbf-180">The second overload of the `Median` method can be passed any generic type.</span></span> <span data-ttu-id="e1dbf-181">Yönteminin genel aşırı yüklemesi, `Median` `Func(Of T, Double)` bir tür için değeri (bir koleksiyondan), karşılık gelen türü olarak proje için lambda ifadesine başvuran ikinci bir parametre alır `Double` .</span><span class="sxs-lookup"><span data-stu-id="e1dbf-181">The generic overload of the `Median` method takes a second parameter that references the `Func(Of T, Double)` lambda expression to project a value for a type (from a collection) as the corresponding value of type `Double`.</span></span> <span data-ttu-id="e1dbf-182">Daha sonra ortanca değer hesaplamasını metodun diğer aşırı yüküne devreder `Median` .</span><span class="sxs-lookup"><span data-stu-id="e1dbf-182">It then delegates the calculation of the median value to the other overload of the `Median` method.</span></span> <span data-ttu-id="e1dbf-183">Lambda ifadeleri hakkında daha fazla bilgi için bkz. [lambda ifadeleri](../../programming-guide/language-features/procedures/lambda-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="e1dbf-183">For more information about lambda expressions, see [Lambda Expressions](../../programming-guide/language-features/procedures/lambda-expressions.md).</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#18](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/UserDefinedAggregates.vb#18)]  
  
 <span data-ttu-id="e1dbf-184">Aşağıdaki örnek `Median` , bir türü koleksiyonda toplama işlevini çağıran örnek sorguları `Integer` ve türünde bir koleksiyonu gösterir `Double` .</span><span class="sxs-lookup"><span data-stu-id="e1dbf-184">The following example shows sample queries that call the `Median` aggregate function on a collection of type `Integer`, and a collection of type `Double`.</span></span> <span data-ttu-id="e1dbf-185">`Median`Türü koleksiyonundaki toplama işlevini çağıran sorgu, `Double` `Median` türü bir koleksiyon olarak kabul eden metodun aşırı yüklemesini çağırır `Double` .</span><span class="sxs-lookup"><span data-stu-id="e1dbf-185">The query that calls the `Median` aggregate function on the collection of type `Double` calls the overload of the `Median` method that accepts, as input, a collection of type `Double`.</span></span> <span data-ttu-id="e1dbf-186">`Median`Türü koleksiyonundaki toplama işlevini çağıran sorgu, `Integer` yönteminin genel aşırı yüklemesini çağırır `Median` .</span><span class="sxs-lookup"><span data-stu-id="e1dbf-186">The query that calls the `Median` aggregate function on the collection of type `Integer` calls the generic overload of the `Median` method.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#19](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/UserDefinedAggregates.vb#19)]  
  
## <a name="see-also"></a><span data-ttu-id="e1dbf-187">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e1dbf-187">See also</span></span>

- [<span data-ttu-id="e1dbf-188">Visual Basic'de LINQ'e Giriş</span><span class="sxs-lookup"><span data-stu-id="e1dbf-188">Introduction to LINQ in Visual Basic</span></span>](../../programming-guide/language-features/linq/introduction-to-linq.md)
- [<span data-ttu-id="e1dbf-189">Sorgular</span><span class="sxs-lookup"><span data-stu-id="e1dbf-189">Queries</span></span>](index.md)
- [<span data-ttu-id="e1dbf-190">Select yan tümcesi</span><span class="sxs-lookup"><span data-stu-id="e1dbf-190">Select Clause</span></span>](select-clause.md)
- [<span data-ttu-id="e1dbf-191">From yan tümcesi</span><span class="sxs-lookup"><span data-stu-id="e1dbf-191">From Clause</span></span>](from-clause.md)
- [<span data-ttu-id="e1dbf-192">WHERE yan tümcesi</span><span class="sxs-lookup"><span data-stu-id="e1dbf-192">Where Clause</span></span>](where-clause.md)
- [<span data-ttu-id="e1dbf-193">Group by yan tümcesi</span><span class="sxs-lookup"><span data-stu-id="e1dbf-193">Group By Clause</span></span>](group-by-clause.md)
