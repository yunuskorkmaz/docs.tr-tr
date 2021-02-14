---
title: Çalışma zamanı durumuna göre sorgulama (C#)
description: Kodunuzun, bu yöntemlere geçirilen LINQ Yöntem çağrılarını veya ifade ağaçlarını değiştirerek çalışma zamanı durumuna göre dinamik olarak sorgulamak için kullanabileceği çeşitli teknikler açıklanmaktadır.
ms.date: 02/11/2021
ms.assetid: 52cd44dd-a3ec-441e-b93a-4eca388119c7
ms.openlocfilehash: 0dcf1696ca323ac4823c80c7993fef7873fd8ed5
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100433789"
---
# <a name="querying-based-on-runtime-state-c"></a><span data-ttu-id="9dfd2-103">Çalışma zamanı durumuna göre sorgulama (C#)</span><span class="sxs-lookup"><span data-stu-id="9dfd2-103">Querying based on runtime state (C#)</span></span>

<span data-ttu-id="9dfd2-104">Bir <xref:System.Linq.IQueryable> veri kaynağına karşı bir veya bir [IQueryable \<T> ](<xref:System.Linq.IQueryable%601>) tanımlayan kodu düşünün:</span><span class="sxs-lookup"><span data-stu-id="9dfd2-104">Consider code that defines an <xref:System.Linq.IQueryable> or an [IQueryable\<T>](<xref:System.Linq.IQueryable%601>) against a data source:</span></span>

:::code language="csharp" source="../../../../../samples/snippets/csharp/programming-guide/dynamic-linq-expression-trees/Program.cs" id="Initialize":::

<span data-ttu-id="9dfd2-105">Bu kodu her çalıştırdığınızda, aynı tam sorgu yürütülür.</span><span class="sxs-lookup"><span data-stu-id="9dfd2-105">Every time you run this code, the same exact query will be executed.</span></span> <span data-ttu-id="9dfd2-106">Bu, kodunuzun çalışma zamanında koşullara bağlı olarak farklı sorgular yürütmesini isteyebileceğiniz için genellikle çok yararlı değildir.</span><span class="sxs-lookup"><span data-stu-id="9dfd2-106">This is frequently not very useful, as you may want your code to execute different queries depending on conditions at runtime.</span></span> <span data-ttu-id="9dfd2-107">Bu makalede, çalışma zamanı durumuna göre farklı bir sorguyu nasıl yürütebileceğinizi açıklar.</span><span class="sxs-lookup"><span data-stu-id="9dfd2-107">This article describes how you can execute a different query based on runtime state.</span></span>

## <a name="iqueryable--iqueryablet-and-expression-trees"></a><span data-ttu-id="9dfd2-108">IQueryable/IQueryable \<T> ve ifade ağaçları</span><span class="sxs-lookup"><span data-stu-id="9dfd2-108">IQueryable / IQueryable\<T> and expression trees</span></span>

<span data-ttu-id="9dfd2-109">Temelde <xref:System.Linq.IQueryable> iki bileşeni vardır:</span><span class="sxs-lookup"><span data-stu-id="9dfd2-109">Fundamentally, an <xref:System.Linq.IQueryable> has two components:</span></span>

* <span data-ttu-id="9dfd2-110"><xref:System.Linq.IQueryable.Expression>&mdash;bir ifade ağacı biçiminde geçerli sorgu bileşenlerinin dil ve veri kaynağı belirsiz temsili.</span><span class="sxs-lookup"><span data-stu-id="9dfd2-110"><xref:System.Linq.IQueryable.Expression>&mdash;a language- and datasource-agnostic representation of the current query's components, in the form of an expression tree.</span></span>
* <span data-ttu-id="9dfd2-111"><xref:System.Linq.IQueryable.Provider>&mdash;bir LINQ sağlayıcısı örneği, geçerli sorguyu bir değere veya bir değer kümesine nasıl bir şekilde bir değere veya değer kümesine nasıl bir şekilde bir değere göre nasıl bir</span><span class="sxs-lookup"><span data-stu-id="9dfd2-111"><xref:System.Linq.IQueryable.Provider>&mdash;an instance of a LINQ provider, which knows how to materialize the current query into a value or set of values.</span></span>

<span data-ttu-id="9dfd2-112">Dinamik sorgulama bağlamında, sağlayıcı genellikle aynı kalır; sorgunun ifade ağacı sorgudan sorguya farklı olacak.</span><span class="sxs-lookup"><span data-stu-id="9dfd2-112">In the context of dynamic querying, the provider will usually remain the same; the expression tree of the query will differ from query to query.</span></span>

<span data-ttu-id="9dfd2-113">İfade ağaçları sabittir; farklı bir ifade ağacı &mdash; ve bu nedenle farklı bir sorgu istiyorsanız &mdash; , var olan ifade ağacını yeni birine ve bu nedenle de yeni bir sorguya çevirmeniz gerekir <xref:System.Linq.IQueryable> .</span><span class="sxs-lookup"><span data-stu-id="9dfd2-113">Expression trees are immutable; if you want a different expression tree&mdash;and thus a different query&mdash;you'll need to translate the existing expression tree to a new one, and thus to a new <xref:System.Linq.IQueryable>.</span></span>

<span data-ttu-id="9dfd2-114">Aşağıdaki bölümlerde, çalışma zamanı durumuna yanıt olarak farklı sorgulama için özel teknikler açıklanır:</span><span class="sxs-lookup"><span data-stu-id="9dfd2-114">The following sections describe specific techniques for querying differently in response to runtime state:</span></span>

- <span data-ttu-id="9dfd2-115">Çalışma zamanı durumunu ifade ağacı içinden kullanın</span><span class="sxs-lookup"><span data-stu-id="9dfd2-115">Use runtime state from within the expression tree</span></span>
- <span data-ttu-id="9dfd2-116">Ek LINQ yöntemlerini çağırın</span><span class="sxs-lookup"><span data-stu-id="9dfd2-116">Call additional LINQ methods</span></span>
- <span data-ttu-id="9dfd2-117">LINQ yöntemlerine geçirilen ifade ağacını farklılık gösterir</span><span class="sxs-lookup"><span data-stu-id="9dfd2-117">Vary the expression tree passed into the LINQ methods</span></span>
- <span data-ttu-id="9dfd2-118">Üzerinde Fabrika yöntemlerini kullanarak bir [ifade \<TDelegate> ](xref:System.Linq.Expressions.Expression%601) ifadesi ağacı oluşturun<xref:System.Linq.Expressions.Expression></span><span class="sxs-lookup"><span data-stu-id="9dfd2-118">Construct an [Expression\<TDelegate>](xref:System.Linq.Expressions.Expression%601) expression tree using the factory methods at <xref:System.Linq.Expressions.Expression></span></span>
- <span data-ttu-id="9dfd2-119">Yöntem çağrı düğümlerini bir <xref:System.Linq.IQueryable> ifade ağacına ekleme</span><span class="sxs-lookup"><span data-stu-id="9dfd2-119">Adding method call nodes to an <xref:System.Linq.IQueryable>'s expression tree</span></span>
- <span data-ttu-id="9dfd2-120">Dizeler oluşturun ve [dınamık LINQ kitaplığını](https://dynamic-linq.net/) kullanın</span><span class="sxs-lookup"><span data-stu-id="9dfd2-120">Construct strings, and use the [Dynamic LINQ library](https://dynamic-linq.net/)</span></span>

## <a name="use-runtime-state-from-within-the-expression-tree"></a><span data-ttu-id="9dfd2-121">Çalışma zamanı durumunu ifade ağacı içinden kullanın</span><span class="sxs-lookup"><span data-stu-id="9dfd2-121">Use runtime state from within the expression tree</span></span>

<span data-ttu-id="9dfd2-122">LINQ sağlayıcısı 'nın onu desteklediğine göre, dinamik olarak sorgu oluşturmanın en kolay yolu, aşağıdaki kod örneğinde olduğu gibi, doğrudan sorgudaki bir kapalı değişken aracılığıyla çalışma zamanı durumuna başvurmalıdır `length` :</span><span class="sxs-lookup"><span data-stu-id="9dfd2-122">Assuming the LINQ provider supports it, the simplest way to query dynamically is to reference the runtime state directly in the query via a closed-over variable, such as `length` in the following code example:</span></span>

:::code language="csharp" source="../../../../../samples/snippets/csharp/programming-guide/dynamic-linq-expression-trees/Program.cs" id="Runtime_state_from_within_expression_tree":::

<span data-ttu-id="9dfd2-123">İç ifade ağacı &mdash; ve bu nedenle sorgu &mdash; değiştirilmedi; sorgu yalnızca değeri değiştiği için farklı değerler döndürüyor `length` .</span><span class="sxs-lookup"><span data-stu-id="9dfd2-123">The internal expression tree&mdash;and thus the query&mdash;haven't been modified; the query returns different values only because the value of `length` has been changed.</span></span>

## <a name="call-additional-linq-methods"></a><span data-ttu-id="9dfd2-124">Ek LINQ yöntemlerini çağırın</span><span class="sxs-lookup"><span data-stu-id="9dfd2-124">Call additional LINQ methods</span></span>

<span data-ttu-id="9dfd2-125">Genellikle, [YERLEŞIK LINQ yöntemleri](https://github.com/dotnet/runtime/blob/master/src/libraries/System.Linq.Queryable/src/System/Linq/Queryable.cs) <xref:System.Linq.Queryable> iki adım gerçekleştirir:</span><span class="sxs-lookup"><span data-stu-id="9dfd2-125">Generally, the [built-in LINQ methods](https://github.com/dotnet/runtime/blob/master/src/libraries/System.Linq.Queryable/src/System/Linq/Queryable.cs) at <xref:System.Linq.Queryable> perform two steps:</span></span>

* <span data-ttu-id="9dfd2-126">Yöntem çağrısını temsil eden içinde geçerli ifade ağacını sarın <xref:System.Linq.Expressions.MethodCallExpression> .</span><span class="sxs-lookup"><span data-stu-id="9dfd2-126">Wrap the current expression tree in a <xref:System.Linq.Expressions.MethodCallExpression> representing the method call.</span></span>
* <span data-ttu-id="9dfd2-127">Sarmalanan ifade ağacını sağlayıcıya geri geçirin; Örneğin, sağlayıcının yöntemi aracılığıyla bir değer döndürün <xref:System.Linq.IQueryProvider.Execute%2A?displayProperty=nameWithType> ya da yöntemi aracılığıyla çevrilmiş bir sorgu nesnesi döndürün <xref:System.Linq.IQueryProvider.CreateQuery%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="9dfd2-127">Pass the wrapped expression tree back to the provider, either to return a value via the provider's <xref:System.Linq.IQueryProvider.Execute%2A?displayProperty=nameWithType> method; or to return a translated query object via the <xref:System.Linq.IQueryProvider.CreateQuery%2A?displayProperty=nameWithType> method.</span></span>

<span data-ttu-id="9dfd2-128">Yeni bir sorgu almak için özgün sorguyu bir [IQueryable \<T> ](xref:System.Linq.IQueryable%601)döndüren metodun sonucuyla değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9dfd2-128">You can replace the original query with the result of an [IQueryable\<T>](xref:System.Linq.IQueryable%601)-returning method, to get a new query.</span></span> <span data-ttu-id="9dfd2-129">Bunu, aşağıdaki örnekte olduğu gibi çalışma zamanı durumuna göre yapabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="9dfd2-129">You can do this based on runtime state, as in the following example:</span></span>

:::code language="csharp" source="../../../../../samples/snippets/csharp/programming-guide/dynamic-linq-expression-trees/Program.cs" id="Added_method_calls":::

## <a name="vary-the-expression-tree-passed-into-the-linq-methods"></a><span data-ttu-id="9dfd2-130">LINQ yöntemlerine geçirilen ifade ağacını farklılık gösterir</span><span class="sxs-lookup"><span data-stu-id="9dfd2-130">Vary the expression tree passed into the LINQ methods</span></span>

<span data-ttu-id="9dfd2-131">Çalışma zamanı durumuna bağlı olarak LINQ yöntemlerine farklı ifadeler geçirebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="9dfd2-131">You can pass in different expressions to the LINQ methods, depending on runtime state:</span></span>

:::code language="csharp" source="../../../../../samples/snippets/csharp/programming-guide/dynamic-linq-expression-trees/Program.cs" id="Varying_expressions":::

<span data-ttu-id="9dfd2-132">Ayrıca, [Linqkit](http://www.albahari.com/nutshell/linqkit.aspx)'In [predicatebuilder](http://www.albahari.com/nutshell/predicatebuilder.aspx)gibi üçüncü taraf bir kitaplık kullanarak çeşitli alt ifadeler oluşturmak isteyebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="9dfd2-132">You might also want to compose the various sub-expressions using a third-party library such as [LinqKit](http://www.albahari.com/nutshell/linqkit.aspx)'s [PredicateBuilder](http://www.albahari.com/nutshell/predicatebuilder.aspx):</span></span>

:::code language="csharp" source="../../../../../samples/snippets/csharp/programming-guide/dynamic-linq-expression-trees/Program.cs" id="Compose_expressions":::

## <a name="construct-expression-trees-and-queries-using-factory-methods"></a><span data-ttu-id="9dfd2-133">Fabrika yöntemlerini kullanarak ifade ağaçları ve sorgular oluşturun</span><span class="sxs-lookup"><span data-stu-id="9dfd2-133">Construct expression trees and queries using factory methods</span></span>

<span data-ttu-id="9dfd2-134">Bu noktaya kadar olan tüm örneklerde, derleme zamanında öğe türü &mdash; `string` &mdash; ve bu nedenle sorgu türü bilinirdi &mdash; `IQueryable<string>` .</span><span class="sxs-lookup"><span data-stu-id="9dfd2-134">In all the examples up to this point, we've known the element type at compile time&mdash;`string`&mdash;and thus the type of the query&mdash;`IQueryable<string>`.</span></span> <span data-ttu-id="9dfd2-135">Herhangi bir öğe türünün sorgusuna bileşen eklemeniz gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="9dfd2-135">You may need to add components to a query of any element type.</span></span> <span data-ttu-id="9dfd2-136">Öğe türüne bağlı olarak farklı bileşenler eklemeniz gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="9dfd2-136">You may need to add different components, depending on the element type.</span></span> <span data-ttu-id="9dfd2-137">' Deki fabrika yöntemlerini kullanarak baştan sona ifade ağaçları oluşturabilir <xref:System.Linq.Expressions.Expression?displayProperty=fullName> ve bu sayede ifadeyi belirli bir öğe türüne uyarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9dfd2-137">You can create expression trees from the ground up, using the factory methods at <xref:System.Linq.Expressions.Expression?displayProperty=fullName>, and thus tailor the expression to a specific element type.</span></span>

### <a name="constructing-an-expressiontdelegate"></a><span data-ttu-id="9dfd2-138">[İfade \<TDelegate> ](xref:System.Linq.Expressions.Expression%601) oluşturma</span><span class="sxs-lookup"><span data-stu-id="9dfd2-138">Constructing an [Expression\<TDelegate>](xref:System.Linq.Expressions.Expression%601)</span></span>

<span data-ttu-id="9dfd2-139">LINQ metotlarından birine geçirilecek bir ifade oluşturduğunuzda, aslında bir [ifade \<TDelegate> ](xref:System.Linq.Expressions.Expression%601)örneği oluşturursunuz; burada,, `TDelegate` `Func<string, bool>` `Action` veya özel bir temsilci türü gibi bir temsilci türüdür.</span><span class="sxs-lookup"><span data-stu-id="9dfd2-139">When you construct an expression to pass into one of the LINQ methods, you're actually constructing an instance of [Expression\<TDelegate>](xref:System.Linq.Expressions.Expression%601), where `TDelegate` is some delegate type such as `Func<string, bool>`, `Action`, or a custom delegate type.</span></span>

<span data-ttu-id="9dfd2-140">[İfade \<TDelegate> ](xref:System.Linq.Expressions.Expression%601) <xref:System.Linq.Expressions.LambdaExpression>, aşağıdaki gibi bir bütün lambda ifadesini temsil eden öğesinden devralır:</span><span class="sxs-lookup"><span data-stu-id="9dfd2-140">[Expression\<TDelegate>](xref:System.Linq.Expressions.Expression%601) inherits from <xref:System.Linq.Expressions.LambdaExpression>, which represents a complete lambda expression like the following:</span></span>

```csharp
Expression<Func<string, bool>> expr = x => x.StartsWith("a");
```

<span data-ttu-id="9dfd2-141"><xref:System.Linq.Expressions.LambdaExpression>, İki bileşene sahiptir:</span><span class="sxs-lookup"><span data-stu-id="9dfd2-141">A <xref:System.Linq.Expressions.LambdaExpression> has two components:</span></span>

* <span data-ttu-id="9dfd2-142">&mdash; `(string x)` &mdash; özelliği tarafından temsil edilen bir parametre <xref:System.Linq.Expressions.LambdaExpression.Parameters> listesi</span><span class="sxs-lookup"><span data-stu-id="9dfd2-142">a parameter list&mdash;`(string x)`&mdash;represented by the <xref:System.Linq.Expressions.LambdaExpression.Parameters> property</span></span>
* <span data-ttu-id="9dfd2-143">&mdash; `x.StartsWith("a")` &mdash; özelliği tarafından temsil edilen bir gövde <xref:System.Linq.Expressions.LambdaExpression.Body> .</span><span class="sxs-lookup"><span data-stu-id="9dfd2-143">a body&mdash;`x.StartsWith("a")`&mdash;represented by the <xref:System.Linq.Expressions.LambdaExpression.Body> property.</span></span>

<span data-ttu-id="9dfd2-144">Bir [ifade \<TDelegate> ](xref:System.Linq.Expressions.Expression%601) oluşturmak için temel adımlar aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="9dfd2-144">The basic steps in constructing an [Expression\<TDelegate>](xref:System.Linq.Expressions.Expression%601) are as follows:</span></span>

* <span data-ttu-id="9dfd2-145"><xref:System.Linq.Expressions.ParameterExpression>Lambda ifadesindeki her bir parametre (varsa) için nesneleri, <xref:System.Linq.Expressions.Expression.Parameter%2A> Factory yöntemini kullanarak tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="9dfd2-145">Define <xref:System.Linq.Expressions.ParameterExpression> objects for each of the parameters (if any) in the lambda expression, using the <xref:System.Linq.Expressions.Expression.Parameter%2A> factory method.</span></span>

    ```csharp
    ParameterExpression x = Parameter(typeof(string), "x");
    ```

* <span data-ttu-id="9dfd2-146"><xref:System.Linq.Expressions.LambdaExpression>Tanımladığınız öğesini kullanarak, gövdesini oluşturun <xref:System.Linq.Expressions.ParameterExpression> .</span><span class="sxs-lookup"><span data-stu-id="9dfd2-146">Construct the body of your <xref:System.Linq.Expressions.LambdaExpression>, using the <xref:System.Linq.Expressions.ParameterExpression> you've defined.</span></span> <span data-ttu-id="9dfd2-147">Örneğin, temsil eden bir ifade şöyle `x.StartsWith("a")` oluşturulabilir:</span><span class="sxs-lookup"><span data-stu-id="9dfd2-147">For instance, an expression representing `x.StartsWith("a")` could be constructed like this:</span></span>

    ```csharp
    Expression body = Call(
        x,
        typeof(string).GetMethod("StartsWith", new [] {typeof(string)}),
        Constant("a")
    );
    ```

* <span data-ttu-id="9dfd2-148">Parametreleri ve gövdesi, uygun fabrika yöntemi aşırı yüklemesini kullanarak, derleme zamanı türü belirlenmiş bir [ifadede \<TDelegate> ](xref:System.Linq.Expressions.Expression%601)sarın <xref:System.Linq.Expressions.Expression.Lambda%2A> :</span><span class="sxs-lookup"><span data-stu-id="9dfd2-148">Wrap the parameters and body in a compile-time-typed [Expression\<TDelegate>](xref:System.Linq.Expressions.Expression%601), using the appropriate <xref:System.Linq.Expressions.Expression.Lambda%2A> factory method overload:</span></span>

    ```csharp
    Expression<Func<string, bool>> expr = Lambda<Func<string, bool>>(body, prm);
    ```

<span data-ttu-id="9dfd2-149">Aşağıdaki bölümlerde, bir LINQ yöntemine geçirilecek bir [ifade \<TDelegate> ](xref:System.Linq.Expressions.Expression%601) oluşturmak isteyebileceğiniz ve Fabrika yöntemlerini kullanarak nasıl yapılacağını gösteren bir örnek sağlayan bir senaryo açıklanır.</span><span class="sxs-lookup"><span data-stu-id="9dfd2-149">The following sections describe a scenario in which you might want to construct an [Expression\<TDelegate>](xref:System.Linq.Expressions.Expression%601) to pass into a LINQ method, and provide a complete example of how to do so using the factory methods.</span></span>

### <a name="scenario"></a><span data-ttu-id="9dfd2-150">Senaryo</span><span class="sxs-lookup"><span data-stu-id="9dfd2-150">Scenario</span></span>

<span data-ttu-id="9dfd2-151">Birden çok varlık türü olduğunu varsayalım:</span><span class="sxs-lookup"><span data-stu-id="9dfd2-151">Let's say you have multiple entity types:</span></span>

```csharp
record Person(string LastName, string FirstName, DateTime DateOfBirth);
record Car(string Model, int Year);
```

<span data-ttu-id="9dfd2-152">Bu varlık türlerinin herhangi biri için, yalnızca kendi alanlarından birinde belirli bir metne sahip olan varlıkları filtrelemek ve döndürmek istersiniz `string` .</span><span class="sxs-lookup"><span data-stu-id="9dfd2-152">For any of these entity types, you want to filter and return only those entities that have a given text inside one of their `string` fields.</span></span> <span data-ttu-id="9dfd2-153">İçin, `Person` `FirstName` ve özelliklerini aramak istersiniz `LastName` :</span><span class="sxs-lookup"><span data-stu-id="9dfd2-153">For `Person`, you'd want to search the `FirstName` and `LastName` properties:</span></span>

```csharp
string term = /* ... */;
var personsQry = new List<Person>()
    .AsQueryable()
    .Where(x => x.FirstName.Contains(term) || x.LastName.Contains(term));
```

<span data-ttu-id="9dfd2-154">Ancak `Car` , için yalnızca özelliğini aramak istersiniz `Model` :</span><span class="sxs-lookup"><span data-stu-id="9dfd2-154">but for `Car`, you'd want to search only the `Model` property:</span></span>

```csharp
string term = /* ... */;
var carsQry = new List<Car>()
    .AsQueryable()
    .Where(x => x.Model.Contains(term));
```

<span data-ttu-id="9dfd2-155">İçin bir özel işlev ve diğeri için yazabilirken `IQueryable<Person>` `IQueryable<Car>` , aşağıdaki işlev bu filtrelemeyi, belirli öğe türünden bağımsız olarak varolan herhangi bir sorguya ekler.</span><span class="sxs-lookup"><span data-stu-id="9dfd2-155">While you could write one custom function for `IQueryable<Person>` and another for `IQueryable<Car>`, the following function adds this filtering to any existing query, irrespective of the specific element type.</span></span>

### <a name="example"></a><span data-ttu-id="9dfd2-156">Örnek</span><span class="sxs-lookup"><span data-stu-id="9dfd2-156">Example</span></span>

:::code language="csharp" source="../../../../../samples/snippets/csharp/programming-guide/dynamic-linq-expression-trees/Program.cs" id="Factory_methods_expression_of_tdelegate":::

<span data-ttu-id="9dfd2-157">`TextFilter`İşlev bir [IQueryable \<T> ](xref:System.Linq.IQueryable%601) (ve yalnızca bir) alıp döndürdüğünden <xref:System.Linq.IQueryable> , metin filtresinden sonra, derleme zamanı türü belirtilmiş sorgu öğeleri ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9dfd2-157">Because the `TextFilter` function takes and returns an [IQueryable\<T>](xref:System.Linq.IQueryable%601) (and not just an <xref:System.Linq.IQueryable>), you can add further compile-time-typed query elements after the text filter.</span></span>

:::code language="csharp" source="../../../../../samples/snippets/csharp/programming-guide/dynamic-linq-expression-trees/Program.cs" id="Factory_methods_expression_of_tdelegate_usage":::

## <a name="adding-method-call-nodes-to-the-xrefsystemlinqiqueryables-expression-tree"></a><span data-ttu-id="9dfd2-158">Yöntem çağrı düğümleri, <xref:System.Linq.IQueryable> ifade ağacına ekleniyor</span><span class="sxs-lookup"><span data-stu-id="9dfd2-158">Adding method call nodes to the <xref:System.Linq.IQueryable>'s expression tree</span></span>

<span data-ttu-id="9dfd2-159">Bir <xref:System.Linq.IQueryable> [IQueryable \<T> ](xref:System.Linq.IQueryable%601)yerıne sahipseniz, genel LINQ yöntemlerini doğrudan çağrılamaz.</span><span class="sxs-lookup"><span data-stu-id="9dfd2-159">If you have an <xref:System.Linq.IQueryable> instead of an [IQueryable\<T>](xref:System.Linq.IQueryable%601), you can't directly call the generic LINQ methods.</span></span> <span data-ttu-id="9dfd2-160">Diğer bir seçenek de, yukarıdaki gibi iç ifade ağacını derlemek ve ifade ağacına geçiş yaparken uygun LINQ metodunu çağırmak için yansıma kullanmaktır.</span><span class="sxs-lookup"><span data-stu-id="9dfd2-160">One alternative is to build the inner expression tree as above, and use reflection to invoke the appropriate LINQ method while passing in the expression tree.</span></span>

<span data-ttu-id="9dfd2-161">LINQ yönteminin işlevini, LINQ yöntemine yapılan çağrıyı temsil eden ' de tüm ağacı sarmalayarak da çoğaltabilirsiniz <xref:System.Linq.Expressions.MethodCallExpression> .</span><span class="sxs-lookup"><span data-stu-id="9dfd2-161">You could also duplicate the LINQ method's functionality, by wrapping the entire tree in a <xref:System.Linq.Expressions.MethodCallExpression> which represents a call to the LINQ method:</span></span>

:::code language="csharp" source="../../../../../samples/snippets/csharp/programming-guide/dynamic-linq-expression-trees/Program.cs" id="Factory_methods_lambdaexpression":::

<span data-ttu-id="9dfd2-162">Bu durumda, bir derleme zamanı `T` genel yer tutucusu olmadığından, <xref:System.Linq.Expressions.Expression.Lambda%2A> derleme zamanı türü bilgileri gerektirmeyen ve bir <xref:System.Linq.Expressions.LambdaExpression> Ifade yerine bir [ \<TDelegate> ifadesi](xref:System.Linq.Expressions.Expression%601)üreten aşırı yüklemeyi kullanacaksınız.</span><span class="sxs-lookup"><span data-stu-id="9dfd2-162">Note that in this case you don't have a compile-time `T` generic placeholder, so you'll use the <xref:System.Linq.Expressions.Expression.Lambda%2A> overload which doesn't require compile-time type information, and which produces a <xref:System.Linq.Expressions.LambdaExpression> instead of an an [Expression\<TDelegate>](xref:System.Linq.Expressions.Expression%601).</span></span>

## <a name="the-dynamic-linq-library"></a><span data-ttu-id="9dfd2-163">Dinamik LINQ kitaplığı</span><span class="sxs-lookup"><span data-stu-id="9dfd2-163">The Dynamic LINQ library</span></span>

<span data-ttu-id="9dfd2-164">Fabrika yöntemlerini kullanarak ifade ağaçları oluşturmak nispeten karmaşıktır; dizeleri oluşturmak daha kolaydır.</span><span class="sxs-lookup"><span data-stu-id="9dfd2-164">Constructing expression trees using factory methods is relatively complex; it is easier to compose strings.</span></span> <span data-ttu-id="9dfd2-165">[Dınamık LINQ kitaplığı](https://dynamic-linq.net/) , IÇINDEKI <xref:System.Linq.IQueryable> standart LINQ yöntemlerine karşılık gelen <xref:System.Linq.Queryable> ve ifade ağaçları yerine [özel bir sözdiziminde](https://dynamic-linq.net/expression-language) dizeleri kabul eden bir genişletme yöntemleri kümesi sunar.</span><span class="sxs-lookup"><span data-stu-id="9dfd2-165">The [Dynamic LINQ library](https://dynamic-linq.net/) exposes a set of extension methods on <xref:System.Linq.IQueryable> corresponding to the standard LINQ methods at <xref:System.Linq.Queryable>, and which accept strings in a [special syntax](https://dynamic-linq.net/expression-language) instead of expression trees.</span></span> <span data-ttu-id="9dfd2-166">Kitaplık, dizeden uygun ifade ağacını oluşturur ve elde edilen çevrilen sonuçları döndürebilir <xref:System.Linq.IQueryable> .</span><span class="sxs-lookup"><span data-stu-id="9dfd2-166">The library generates the appropriate expression tree from the string, and can return the resultant translated <xref:System.Linq.IQueryable>.</span></span>

<span data-ttu-id="9dfd2-167">Örneğin, önceki örnek aşağıdaki şekilde yeniden yazılabilir:</span><span class="sxs-lookup"><span data-stu-id="9dfd2-167">For instance, the previous example could be rewritten as follows:</span></span>

:::code language="csharp" source="../../../../../samples/snippets/csharp/programming-guide/dynamic-linq-expression-trees/Program.cs" id="Dynamic_linq":::

## <a name="see-also"></a><span data-ttu-id="9dfd2-168">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9dfd2-168">See also</span></span>

- [<span data-ttu-id="9dfd2-169">İfade ağaçları (C#)</span><span class="sxs-lookup"><span data-stu-id="9dfd2-169">Expression Trees (C#)</span></span>](./index.md)
- [<span data-ttu-id="9dfd2-170">İfade ağaçlarını yürütme (C#)</span><span class="sxs-lookup"><span data-stu-id="9dfd2-170">How to execute expression trees (C#)</span></span>](./how-to-execute-expression-trees.md)
- [<span data-ttu-id="9dfd2-171">Çalışma zamanında koşul filtrelerini dinamik olarak belirtme</span><span class="sxs-lookup"><span data-stu-id="9dfd2-171">Dynamically specify predicate filters at runtime</span></span>](../../../linq/dynamically-specify-predicate-filters-at-runtime.md)
