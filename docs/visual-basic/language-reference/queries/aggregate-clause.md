---
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
ms.openlocfilehash: be2e401c7931b2637c14a3ea3b742a2c09917939
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90869992"
---
# <a name="aggregate-clause-visual-basic"></a><span data-ttu-id="cf66d-102">Aggregate Tümcesi (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="cf66d-102">Aggregate Clause (Visual Basic)</span></span>

<span data-ttu-id="cf66d-103">Bir koleksiyona bir veya daha fazla toplama işlevi uygular.</span><span class="sxs-lookup"><span data-stu-id="cf66d-103">Applies one or more aggregate functions to a collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cf66d-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="cf66d-104">Syntax</span></span>  
  
```vb  
Aggregate element [As type] In collection _  
  [, element2 [As type2] In collection2, [...]]  
  [ clause ]  
  Into expressionList  
```  
  
## <a name="parts"></a><span data-ttu-id="cf66d-105">Bölümler</span><span class="sxs-lookup"><span data-stu-id="cf66d-105">Parts</span></span>  
  
|<span data-ttu-id="cf66d-106">Terim</span><span class="sxs-lookup"><span data-stu-id="cf66d-106">Term</span></span>|<span data-ttu-id="cf66d-107">Tanım</span><span class="sxs-lookup"><span data-stu-id="cf66d-107">Definition</span></span>|  
|---|---|  
|`element`|<span data-ttu-id="cf66d-108">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="cf66d-108">Required.</span></span> <span data-ttu-id="cf66d-109">Koleksiyon öğeleri boyunca yinelemek için kullanılan değişken.</span><span class="sxs-lookup"><span data-stu-id="cf66d-109">Variable used to iterate through the elements of the collection.</span></span>|  
|`type`|<span data-ttu-id="cf66d-110">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="cf66d-110">Optional.</span></span> <span data-ttu-id="cf66d-111">Türü `element` .</span><span class="sxs-lookup"><span data-stu-id="cf66d-111">The type of `element`.</span></span> <span data-ttu-id="cf66d-112">Hiçbir tür belirtilmemişse, türü `element` öğesinden çıkarsanamıyor `collection` .</span><span class="sxs-lookup"><span data-stu-id="cf66d-112">If no type is specified, the type of `element` is inferred from `collection`.</span></span>|  
|`collection`|<span data-ttu-id="cf66d-113">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="cf66d-113">Required.</span></span> <span data-ttu-id="cf66d-114">Üzerinde çalışılacak koleksiyona başvurur.</span><span class="sxs-lookup"><span data-stu-id="cf66d-114">Refers to the collection to operate on.</span></span>|  
|`clause`|<span data-ttu-id="cf66d-115">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="cf66d-115">Optional.</span></span> <span data-ttu-id="cf66d-116">`Where`Toplama yan tümcesini veya yan tümceleri uygulamak üzere sorgu sonucunu daraltmak için bir yan tümce gibi bir veya daha fazla sorgu yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="cf66d-116">One or more query clauses, such as a `Where` clause, to refine the query result to apply the aggregate clause or clauses to.</span></span>|  
|`expressionList`|<span data-ttu-id="cf66d-117">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="cf66d-117">Required.</span></span> <span data-ttu-id="cf66d-118">Koleksiyona uygulanacak bir toplama işlevini tanımlayan bir veya daha fazla virgülle ayrılmış ifade.</span><span class="sxs-lookup"><span data-stu-id="cf66d-118">One or more comma-delimited expressions that identify an aggregate function to apply to the collection.</span></span> <span data-ttu-id="cf66d-119">Sorgu sonucu için bir üye adı belirtmek üzere bir toplama işlevine bir diğer ad uygulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="cf66d-119">You can apply an alias to an aggregate function to specify a member name for the query result.</span></span> <span data-ttu-id="cf66d-120">Diğer ad sağlanmazsa, toplama işlevinin adı kullanılır.</span><span class="sxs-lookup"><span data-stu-id="cf66d-120">If no alias is supplied, the name of the aggregate function is used.</span></span> <span data-ttu-id="cf66d-121">Örnekler için, bu konunun ilerleyen kısımlarında bulunan toplama işlevleri hakkında bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="cf66d-121">For examples, see the section about aggregate functions later in this topic.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="cf66d-122">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="cf66d-122">Remarks</span></span>  

 <span data-ttu-id="cf66d-123">`Aggregate`Yan tümce, Sorgularınızdaki toplama işlevlerini dahil etmek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="cf66d-123">The `Aggregate` clause can be used to include aggregate functions in your queries.</span></span> <span data-ttu-id="cf66d-124">Toplama işlevleri, bir değerler kümesi üzerinde denetim ve hesaplamalar gerçekleştirir ve tek bir değer döndürür.</span><span class="sxs-lookup"><span data-stu-id="cf66d-124">Aggregate functions perform checks and computations over a set of values and return a single value.</span></span> <span data-ttu-id="cf66d-125">Sorgu sonuç türünün bir üyesini kullanarak hesaplanan değere erişebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="cf66d-125">You can access the computed value by using a member of the query result type.</span></span> <span data-ttu-id="cf66d-126">Kullanabileceğiniz standart toplama işlevleri,,,,,, `All` `Any` `Average` `Count` `LongCount` `Max` `Min` , ve `Sum` işlevleridir.</span><span class="sxs-lookup"><span data-stu-id="cf66d-126">The standard aggregate functions that you can use are the `All`, `Any`, `Average`, `Count`, `LongCount`, `Max`, `Min`, and `Sum` functions.</span></span> <span data-ttu-id="cf66d-127">Bu işlevler, SQL 'deki toplamalara alışkın olan geliştiricilere tanıdık gelecektir.</span><span class="sxs-lookup"><span data-stu-id="cf66d-127">These functions are familiar to developers who are familiar with aggregates in SQL.</span></span> <span data-ttu-id="cf66d-128">Bunlar, bu konunun aşağıdaki bölümünde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="cf66d-128">They are described in the following section of this topic.</span></span>  
  
 <span data-ttu-id="cf66d-129">Toplama işlevinin sonucu sorgu sonuç türünün bir alanı olarak sorgu sonucuna dahil edilir.</span><span class="sxs-lookup"><span data-stu-id="cf66d-129">The result of an aggregate function is included in the query result as a field of the query result type.</span></span> <span data-ttu-id="cf66d-130">Toplama işlevi sonucu için, toplam değeri tutacak sorgu sonuç türü üyesinin adını belirtmek üzere bir diğer ad sağlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="cf66d-130">You can supply an alias for the aggregate function result to specify the name of the member of the query result type that will hold the aggregate value.</span></span> <span data-ttu-id="cf66d-131">Diğer ad sağlanmazsa, toplama işlevinin adı kullanılır.</span><span class="sxs-lookup"><span data-stu-id="cf66d-131">If no alias is supplied, the name of the aggregate function is used.</span></span>  
  
 <span data-ttu-id="cf66d-132">`Aggregate`Yan tümce bir sorgu başlatabilir veya bir sorguya ek bir yan tümce olarak eklenebilir.</span><span class="sxs-lookup"><span data-stu-id="cf66d-132">The `Aggregate` clause can begin a query, or it can be included as an additional clause in a query.</span></span> <span data-ttu-id="cf66d-133">`Aggregate`Yan tümce bir sorgu başlıyorsa, sonuç, yan tümcesinde belirtilen toplama işlevinin sonucu olan tek bir değerdir `Into` .</span><span class="sxs-lookup"><span data-stu-id="cf66d-133">If the `Aggregate` clause begins a query, the result is a single value that is the result of the aggregate function specified in the `Into` clause.</span></span> <span data-ttu-id="cf66d-134">Yan tümcesinde birden fazla toplama işlevi belirtilmişse `Into` , sorgu, yan tümcesindeki her toplama işlevinin sonucuna başvurmak için ayrı bir özelliği olan tek bir tür döndürür `Into` .</span><span class="sxs-lookup"><span data-stu-id="cf66d-134">If more than one aggregate function is specified in the `Into` clause, the query returns a single type with a separate property to reference the result of each aggregate function in the `Into` clause.</span></span> <span data-ttu-id="cf66d-135">`Aggregate`Yan tümce bir sorguya ek bir yan tümce olarak dahil edildiğinde, sorgu koleksiyonunda döndürülen tür, yan tümcesindeki her toplama işlevinin sonucuna başvuracak ayrı bir özelliğe sahip olur `Into` .</span><span class="sxs-lookup"><span data-stu-id="cf66d-135">If the `Aggregate` clause is included as an additional clause in a query, the type returned in the query collection will have a separate property to reference the result of each aggregate function in the `Into` clause.</span></span>  
  
## <a name="aggregate-functions"></a><span data-ttu-id="cf66d-136">Toplama İşlevleri</span><span class="sxs-lookup"><span data-stu-id="cf66d-136">Aggregate Functions</span></span>

<span data-ttu-id="cf66d-137">Aşağıdaki, yan tümcesiyle kullanılabilen standart toplama işlevleridir `Aggregate` .</span><span class="sxs-lookup"><span data-stu-id="cf66d-137">The following are the standard aggregate functions that can be used with the `Aggregate` clause.</span></span>  
  
### <a name="all"></a><span data-ttu-id="cf66d-138">Tümü</span><span class="sxs-lookup"><span data-stu-id="cf66d-138">All</span></span>

<span data-ttu-id="cf66d-139">`true`Koleksiyondaki tüm öğelerin belirtilen koşulu karşılayıp karşılamadığını döndürür; Aksi takdirde döndürür `false` .</span><span class="sxs-lookup"><span data-stu-id="cf66d-139">Returns `true` if all elements in the collection satisfy a specified condition; otherwise returns `false`.</span></span> <span data-ttu-id="cf66d-140">Aşağıda bir örnek verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="cf66d-140">The following is an example:</span></span>

 [!code-vb[VbSimpleQuerySamples#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#5)]

### <a name="any"></a><span data-ttu-id="cf66d-141">Herhangi biri</span><span class="sxs-lookup"><span data-stu-id="cf66d-141">Any</span></span>

<span data-ttu-id="cf66d-142">`true`Koleksiyondaki herhangi bir öğenin belirtilen koşulu karşılayıp karşılamadığını döndürür; Aksi takdirde döndürür `false` .</span><span class="sxs-lookup"><span data-stu-id="cf66d-142">Returns `true` if any element in the collection satisfies a specified condition; otherwise returns `false`.</span></span> <span data-ttu-id="cf66d-143">Aşağıda bir örnek verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="cf66d-143">The following is an example:</span></span>

 [!code-vb[VbSimpleQuerySamples#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#6)]

### <a name="average"></a><span data-ttu-id="cf66d-144">Ortalama</span><span class="sxs-lookup"><span data-stu-id="cf66d-144">Average</span></span>

<span data-ttu-id="cf66d-145">Koleksiyondaki tüm öğelerin ortalamasını hesaplar veya koleksiyondaki tüm öğeler için sağlanan bir ifadeyi hesaplar.</span><span class="sxs-lookup"><span data-stu-id="cf66d-145">Computes the average of all elements in the collection, or computes a supplied expression for all elements in the collection.</span></span> <span data-ttu-id="cf66d-146">Aşağıda bir örnek verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="cf66d-146">The following is an example:</span></span>

 [!code-vb[VbSimpleQuerySamples#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#7)]

### <a name="count"></a><span data-ttu-id="cf66d-147">Count</span><span class="sxs-lookup"><span data-stu-id="cf66d-147">Count</span></span>

<span data-ttu-id="cf66d-148">Koleksiyondaki öğelerin sayısını sayar.</span><span class="sxs-lookup"><span data-stu-id="cf66d-148">Counts the number of elements in the collection.</span></span> <span data-ttu-id="cf66d-149">`Boolean`Koleksiyonda yalnızca bir koşulu karşılayan öğelerin sayısını saymak için isteğe bağlı bir ifade sağlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="cf66d-149">You can supply an optional `Boolean` expression to count only the number of elements in the collection that satisfy a condition.</span></span> <span data-ttu-id="cf66d-150">Aşağıda bir örnek verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="cf66d-150">The following is an example:</span></span>

 [!code-vb[VbSimpleQuerySamples#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#8)]

### <a name="group"></a><span data-ttu-id="cf66d-151">Grup</span><span class="sxs-lookup"><span data-stu-id="cf66d-151">Group</span></span>

<span data-ttu-id="cf66d-152">, `Group By` Veya yan tümcesinin sonucu olarak gruplandırılan sorgu sonuçlarının başvurduğu anlamına gelir `Group Join` .</span><span class="sxs-lookup"><span data-stu-id="cf66d-152">Refers to query results that are grouped as a result of a `Group By` or `Group Join` clause.</span></span> <span data-ttu-id="cf66d-153">`Group`İşlev yalnızca `Into` `Group By` OR yan tümcesinde geçerlidir `Group Join` .</span><span class="sxs-lookup"><span data-stu-id="cf66d-153">The `Group` function is valid only in the `Into` clause of a `Group By` or `Group Join` clause.</span></span> <span data-ttu-id="cf66d-154">Daha fazla bilgi ve örnek için bkz. [Group by yan tümcesi](group-by-clause.md) ve [Group JOIN yan tümcesi](group-join-clause.md).</span><span class="sxs-lookup"><span data-stu-id="cf66d-154">For more information and examples, see [Group By Clause](group-by-clause.md) and [Group Join Clause](group-join-clause.md).</span></span>

### <a name="longcount"></a><span data-ttu-id="cf66d-155">LongCount</span><span class="sxs-lookup"><span data-stu-id="cf66d-155">LongCount</span></span>

<span data-ttu-id="cf66d-156">Koleksiyondaki öğelerin sayısını sayar.</span><span class="sxs-lookup"><span data-stu-id="cf66d-156">Counts the number of elements in the collection.</span></span> <span data-ttu-id="cf66d-157">`Boolean`Koleksiyonda yalnızca bir koşulu karşılayan öğelerin sayısını saymak için isteğe bağlı bir ifade sağlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="cf66d-157">You can supply an optional `Boolean` expression to count only the number of elements in the collection that satisfy a condition.</span></span> <span data-ttu-id="cf66d-158">Sonucu bir olarak döndürür `Long` .</span><span class="sxs-lookup"><span data-stu-id="cf66d-158">Returns the result as a `Long`.</span></span> <span data-ttu-id="cf66d-159">Bir örnek için bkz `Count` . toplama işlevi.</span><span class="sxs-lookup"><span data-stu-id="cf66d-159">For an example, see the `Count` aggregate function.</span></span>

### <a name="max"></a><span data-ttu-id="cf66d-160">En yüksek değer</span><span class="sxs-lookup"><span data-stu-id="cf66d-160">Max</span></span>

<span data-ttu-id="cf66d-161">Koleksiyondaki maksimum değeri hesaplar veya koleksiyondaki tüm öğeler için sağlanan bir ifadeyi hesaplar.</span><span class="sxs-lookup"><span data-stu-id="cf66d-161">Computes the maximum value from the collection, or computes a supplied expression for all elements in the collection.</span></span> <span data-ttu-id="cf66d-162">Aşağıda bir örnek verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="cf66d-162">The following is an example:</span></span>

 [!code-vb[VbSimpleQuerySamples#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#9)]

### <a name="min"></a><span data-ttu-id="cf66d-163">Min</span><span class="sxs-lookup"><span data-stu-id="cf66d-163">Min</span></span>

<span data-ttu-id="cf66d-164">Koleksiyondaki en küçük değeri hesaplar veya koleksiyondaki tüm öğeler için sağlanan bir ifadeyi hesaplar.</span><span class="sxs-lookup"><span data-stu-id="cf66d-164">Computes the minimum value from the collection, or computes a supplied expression for all elements in the collection.</span></span> <span data-ttu-id="cf66d-165">Aşağıda bir örnek verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="cf66d-165">The following is an example:</span></span>

 [!code-vb[VbSimpleQuerySamples#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#10)]

### <a name="sum"></a><span data-ttu-id="cf66d-166">Toplam</span><span class="sxs-lookup"><span data-stu-id="cf66d-166">Sum</span></span>

<span data-ttu-id="cf66d-167">Koleksiyondaki tüm öğelerin toplamını hesaplar veya koleksiyondaki tüm öğeler için sağlanan bir ifadeyi hesaplar.</span><span class="sxs-lookup"><span data-stu-id="cf66d-167">Computes the sum of all elements in the collection, or computes a supplied expression for all elements in the collection.</span></span> <span data-ttu-id="cf66d-168">Aşağıda bir örnek verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="cf66d-168">The following is an example:</span></span>

 [!code-vb[VbSimpleQuerySamples#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#15)]

## <a name="example"></a><span data-ttu-id="cf66d-169">Örnek</span><span class="sxs-lookup"><span data-stu-id="cf66d-169">Example</span></span>  

<span data-ttu-id="cf66d-170">Aşağıdaki örnek, `Aggregate` bir sorgu sonucuna toplama işlevleri uygulamak için yan tümcesinin nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="cf66d-170">The following example shows how to use the `Aggregate` clause to apply aggregate functions to a query result.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#4)]  
  
## <a name="creating-user-defined-aggregate-functions"></a><span data-ttu-id="cf66d-171">Kullanıcı tanımlı toplama Işlevleri oluşturma</span><span class="sxs-lookup"><span data-stu-id="cf66d-171">Creating User-Defined Aggregate Functions</span></span>

 <span data-ttu-id="cf66d-172">Türe uzantı yöntemleri ekleyerek kendi özel toplama işlevlerinizi bir sorgu ifadesine dahil edebilirsiniz <xref:System.Collections.Generic.IEnumerable%601> .</span><span class="sxs-lookup"><span data-stu-id="cf66d-172">You can include your own custom aggregate functions in a query expression by adding extension methods to the <xref:System.Collections.Generic.IEnumerable%601> type.</span></span> <span data-ttu-id="cf66d-173">Özel yönteminiz, toplama işlevinizin başvurduğu sıralanabilir koleksiyonda bir hesaplama veya işlem gerçekleştirebilir.</span><span class="sxs-lookup"><span data-stu-id="cf66d-173">Your custom method can then perform a calculation or operation on the enumerable collection that has referenced your aggregate function.</span></span> <span data-ttu-id="cf66d-174">Uzantı yöntemleri hakkında daha fazla bilgi için bkz. [Uzantı yöntemleri](../../programming-guide/language-features/procedures/extension-methods.md).</span><span class="sxs-lookup"><span data-stu-id="cf66d-174">For more information about extension methods, see [Extension Methods](../../programming-guide/language-features/procedures/extension-methods.md).</span></span>  
  
 <span data-ttu-id="cf66d-175">Örneğin, aşağıdaki örnek bir sayı koleksiyonunun ortanca değerini hesaplayan özel bir toplama işlevi gösterir.</span><span class="sxs-lookup"><span data-stu-id="cf66d-175">For example, the following example shows a custom aggregate function that calculates the median value of a collection of numbers.</span></span> <span data-ttu-id="cf66d-176">Uzantı yönteminin iki aşırı yüklemesi vardır `Median` .</span><span class="sxs-lookup"><span data-stu-id="cf66d-176">There are two overloads of the `Median` extension method.</span></span> <span data-ttu-id="cf66d-177">İlk aşırı yükleme giriş olarak bir tür koleksiyonu kabul eder `IEnumerable(Of Double)` .</span><span class="sxs-lookup"><span data-stu-id="cf66d-177">The first overload accepts, as input, a collection of type `IEnumerable(Of Double)`.</span></span> <span data-ttu-id="cf66d-178">`Median`Toplama işlevi, türünde bir sorgu alanı için çağrılırsa `Double` , bu yöntem çağrılır.</span><span class="sxs-lookup"><span data-stu-id="cf66d-178">If the `Median` aggregate function is called for a query field of type `Double`, this method will be called.</span></span> <span data-ttu-id="cf66d-179">Metodun ikinci aşırı yüklemesi `Median` herhangi bir genel tür geçirilebilir.</span><span class="sxs-lookup"><span data-stu-id="cf66d-179">The second overload of the `Median` method can be passed any generic type.</span></span> <span data-ttu-id="cf66d-180">Yönteminin genel aşırı yüklemesi, `Median` `Func(Of T, Double)` bir tür için değeri (bir koleksiyondan), karşılık gelen türü olarak proje için lambda ifadesine başvuran ikinci bir parametre alır `Double` .</span><span class="sxs-lookup"><span data-stu-id="cf66d-180">The generic overload of the `Median` method takes a second parameter that references the `Func(Of T, Double)` lambda expression to project a value for a type (from a collection) as the corresponding value of type `Double`.</span></span> <span data-ttu-id="cf66d-181">Daha sonra ortanca değer hesaplamasını metodun diğer aşırı yüküne devreder `Median` .</span><span class="sxs-lookup"><span data-stu-id="cf66d-181">It then delegates the calculation of the median value to the other overload of the `Median` method.</span></span> <span data-ttu-id="cf66d-182">Lambda ifadeleri hakkında daha fazla bilgi için bkz. [lambda ifadeleri](../../programming-guide/language-features/procedures/lambda-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="cf66d-182">For more information about lambda expressions, see [Lambda Expressions](../../programming-guide/language-features/procedures/lambda-expressions.md).</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#18](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/UserDefinedAggregates.vb#18)]  
  
 <span data-ttu-id="cf66d-183">Aşağıdaki örnek `Median` , bir türü koleksiyonda toplama işlevini çağıran örnek sorguları `Integer` ve türünde bir koleksiyonu gösterir `Double` .</span><span class="sxs-lookup"><span data-stu-id="cf66d-183">The following example shows sample queries that call the `Median` aggregate function on a collection of type `Integer`, and a collection of type `Double`.</span></span> <span data-ttu-id="cf66d-184">`Median`Türü koleksiyonundaki toplama işlevini çağıran sorgu, `Double` `Median` türü bir koleksiyon olarak kabul eden metodun aşırı yüklemesini çağırır `Double` .</span><span class="sxs-lookup"><span data-stu-id="cf66d-184">The query that calls the `Median` aggregate function on the collection of type `Double` calls the overload of the `Median` method that accepts, as input, a collection of type `Double`.</span></span> <span data-ttu-id="cf66d-185">`Median`Türü koleksiyonundaki toplama işlevini çağıran sorgu, `Integer` yönteminin genel aşırı yüklemesini çağırır `Median` .</span><span class="sxs-lookup"><span data-stu-id="cf66d-185">The query that calls the `Median` aggregate function on the collection of type `Integer` calls the generic overload of the `Median` method.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#19](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/UserDefinedAggregates.vb#19)]  
  
## <a name="see-also"></a><span data-ttu-id="cf66d-186">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="cf66d-186">See also</span></span>

- [<span data-ttu-id="cf66d-187">Visual Basic'de LINQ'e Giriş</span><span class="sxs-lookup"><span data-stu-id="cf66d-187">Introduction to LINQ in Visual Basic</span></span>](../../programming-guide/language-features/linq/introduction-to-linq.md)
- [<span data-ttu-id="cf66d-188">Sorgular</span><span class="sxs-lookup"><span data-stu-id="cf66d-188">Queries</span></span>](index.md)
- [<span data-ttu-id="cf66d-189">Select yan tümcesi</span><span class="sxs-lookup"><span data-stu-id="cf66d-189">Select Clause</span></span>](select-clause.md)
- [<span data-ttu-id="cf66d-190">From yan tümcesi</span><span class="sxs-lookup"><span data-stu-id="cf66d-190">From Clause</span></span>](from-clause.md)
- [<span data-ttu-id="cf66d-191">WHERE yan tümcesi</span><span class="sxs-lookup"><span data-stu-id="cf66d-191">Where Clause</span></span>](where-clause.md)
- [<span data-ttu-id="cf66d-192">Group By Yan Tümcesi</span><span class="sxs-lookup"><span data-stu-id="cf66d-192">Group By Clause</span></span>](group-by-clause.md)
