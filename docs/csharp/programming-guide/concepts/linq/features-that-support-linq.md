---
title: LINQ'i Destekleyen C# Özellikleri
ms.date: 07/20/2015
helpviewer_keywords:
- LINQ [C#], features supporting LINQ
ms.assetid: 524b0078-ebfd-45a7-b390-f2ceb9d84797
ms.openlocfilehash: 9fc8adaa49d02f8b69c2db6e94a28b9fab36b3b0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75635801"
---
# <a name="c-features-that-support-linq"></a><span data-ttu-id="5bb87-102">LINQ'i Destekleyen C# Özellikleri</span><span class="sxs-lookup"><span data-stu-id="5bb87-102">C# Features That Support LINQ</span></span>

<span data-ttu-id="5bb87-103">Aşağıdaki bölümde C# 3.0'da tanıtılan yeni dil yapıları tanıtılır.</span><span class="sxs-lookup"><span data-stu-id="5bb87-103">The following section introduces new language constructs introduced in C# 3.0.</span></span> <span data-ttu-id="5bb87-104">Bu yeni özelliklerin tümü LINQ sorgularında bir dereceye kadar kullanılsa da, linq ile sınırlı değildir ve bunları yararlı bulduğunuz herhangi bir bağlamda kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="5bb87-104">Although these new features are all used to a degree with LINQ queries, they are not limited to LINQ and can be used in any context where you find them useful.</span></span>

## <a name="query-expressions"></a><span data-ttu-id="5bb87-105">Sorgu İfadeleri</span><span class="sxs-lookup"><span data-stu-id="5bb87-105">Query Expressions</span></span>

<span data-ttu-id="5bb87-106">Sorgu ifadeleri, Tamamlanamayan koleksiyonlar üzerinde sorgulamak için SQL veya XQuery'ye benzer bir bildirim sözdizimi kullanır.</span><span class="sxs-lookup"><span data-stu-id="5bb87-106">Query expressions use a declarative syntax similar to SQL or XQuery to query over IEnumerable collections.</span></span> <span data-ttu-id="5bb87-107">Derleme zaman sorgu sözdizimi, bir LINQ sağlayıcısının standart sorgu işleci uzantısı yöntemlerini uygulamasına yöntem çağrılarına dönüştürülür.</span><span class="sxs-lookup"><span data-stu-id="5bb87-107">At compile time query syntax is converted to method calls to a LINQ provider's implementation of the standard query operator extension methods.</span></span> <span data-ttu-id="5bb87-108">Uygulamalar, bir `using` yönergeyle uygun ad alanını belirterek kapsamda olan standart sorgu işleçlerini denetler.</span><span class="sxs-lookup"><span data-stu-id="5bb87-108">Applications control the standard query operators that are in scope by specifying the appropriate namespace with a `using` directive.</span></span> <span data-ttu-id="5bb87-109">Aşağıdaki sorgu ifadesi bir dizi dize alır, dizedeki ilk karaktere göre gruplanır ve grupları emreder.</span><span class="sxs-lookup"><span data-stu-id="5bb87-109">The following query expression takes an array of strings, groups them according to the first character in the string, and orders the groups.</span></span>

```csharp
var query = from str in stringArray
            group str by str[0] into stringGroup
            orderby stringGroup.Key
            select stringGroup;
```

<span data-ttu-id="5bb87-110">Daha fazla bilgi için [LINQ Sorgu İfadeleri'ne](../../../linq/index.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="5bb87-110">For more information, see [LINQ Query Expressions](../../../linq/index.md).</span></span>

## <a name="implicitly-typed-variables-var"></a><span data-ttu-id="5bb87-111">Örtülü Olarak Yazılan Değişkenler (var)</span><span class="sxs-lookup"><span data-stu-id="5bb87-111">Implicitly Typed Variables (var)</span></span>

<span data-ttu-id="5bb87-112">Bir değişkeni beyan ve başharfe çevirirken bir türü açıkça belirtmek yerine, burada gösterildiği gibi derleyiciye türü çıkartmasını ve atamasını bildirmek için [var](../../../language-reference/keywords/var.md) değiştiricisini kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="5bb87-112">Instead of explicitly specifying a type when you declare and initialize a variable, you can use the [var](../../../language-reference/keywords/var.md) modifier to instruct the compiler to infer and assign the type, as shown here:</span></span>

```csharp
var number = 5;
var name = "Virginia";
var query = from str in stringArray
            where str[0] == 'm'
            select str;
```

<span data-ttu-id="5bb87-113">Olarak `var` bildirilen değişkenler, türünü açıkça belirttiğiniz değişkenler kadar güçlü bir şekilde yazılır.</span><span class="sxs-lookup"><span data-stu-id="5bb87-113">Variables declared as `var` are just as strongly-typed as variables whose type you specify explicitly.</span></span> <span data-ttu-id="5bb87-114">Kullanımı, `var` anonim türleri oluşturmayı mümkün kılar, ancak yalnızca yerel değişkenler için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="5bb87-114">The use of `var` makes it possible to create anonymous types, but it can be used only for local variables.</span></span> <span data-ttu-id="5bb87-115">Diziler de örtülü yazarak ilan edilebilir.</span><span class="sxs-lookup"><span data-stu-id="5bb87-115">Arrays can also be declared with implicit typing.</span></span>

<span data-ttu-id="5bb87-116">Daha fazla bilgi için [bkz.](../../classes-and-structs/implicitly-typed-local-variables.md)</span><span class="sxs-lookup"><span data-stu-id="5bb87-116">For more information, see [Implicitly Typed Local Variables](../../classes-and-structs/implicitly-typed-local-variables.md).</span></span>

## <a name="object-and-collection-initializers"></a><span data-ttu-id="5bb87-117">Nesne ve Koleksiyon Başlatıcıları</span><span class="sxs-lookup"><span data-stu-id="5bb87-117">Object and Collection Initializers</span></span>

<span data-ttu-id="5bb87-118">Nesne ve koleksiyon başharfleri, nesne için açıkça bir oluşturucu çağırmadan nesneleri başlatmayı mümkün kılar.</span><span class="sxs-lookup"><span data-stu-id="5bb87-118">Object and collection initializers make it possible to initialize objects without explicitly calling a constructor for the object.</span></span> <span data-ttu-id="5bb87-119">Başlangıç layıcılar genellikle kaynak verileri yeni bir veri türüne yansıttığında sorgu ifadelerinde kullanılır.</span><span class="sxs-lookup"><span data-stu-id="5bb87-119">Initializers are typically used in query expressions when they project the source data into a new data type.</span></span> <span data-ttu-id="5bb87-120">Ortak `Name` ve `Phone` `Customer` özellikleri ile adlı bir sınıf varsayarsak, nesne baş harfizer aşağıdaki kod olarak kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="5bb87-120">Assuming a class named `Customer` with public `Name` and `Phone` properties, the object initializer can be used as in the following code:</span></span>

```csharp
var cust = new Customer { Name = "Mike", Phone = "555-1212" };
```

<span data-ttu-id="5bb87-121">Sınıfımıza `Customer` devam ederek, "büyük" adlı `IncomingOrders`bir veri kaynağı olduğunu ve `OrderSize`her sipariş için bu `Customer` siparişten yeni bir tabanlı oluşturmak istediğimizi varsayalım.</span><span class="sxs-lookup"><span data-stu-id="5bb87-121">Continuing with our `Customer` class, assume that there is a data source called `IncomingOrders`, and that for each order with a large `OrderSize`, we would like to create a new `Customer` based off of that order.</span></span> <span data-ttu-id="5bb87-122">Bir LINQ sorgusu bu veri kaynağında yürütülebilir ve bir koleksiyonu doldurmak için nesne başlatmayı kullanabilir:</span><span class="sxs-lookup"><span data-stu-id="5bb87-122">A LINQ query can be executed on this data source and use object initialization to fill a collection:</span></span>

```csharp
var newLargeOrderCustomers = from o in IncomingOrders
                            where o.OrderSize > 5
                            select new Customer { Name = o.Name, Phone = o.Phone };
```

<span data-ttu-id="5bb87-123">Veri kaynağı, başlık `Customer` altında sınıf , `OrderSize`ancak nesne başlatma ile, sorgudan döndürülen veri istenilen veri türüne kalıplanmış daha fazla özelliklere sahip olabilir; sınıfımızla ilgili verileri seçeriz.</span><span class="sxs-lookup"><span data-stu-id="5bb87-123">The data source may have more properties lying under the hood than the `Customer` class such as `OrderSize`, but with object initialization, the data returned from the query is molded into the desired data type; we choose the data that is relevant to our class.</span></span> <span data-ttu-id="5bb87-124">Sonuç olarak, şimdi istediğimiz `IEnumerable` yeni `Customer`s ile dolu bir var.</span><span class="sxs-lookup"><span data-stu-id="5bb87-124">As a result, we now have an `IEnumerable` filled with the new `Customer`s we wanted.</span></span> <span data-ttu-id="5bb87-125">Yukarıdaki ler LINQ'nin yöntem sözdiziminde de yazılabilir:</span><span class="sxs-lookup"><span data-stu-id="5bb87-125">The above can also be written in LINQ's method syntax:</span></span>

```csharp
var newLargeOrderCustomers = IncomingOrders.Where(x => x.OrderSize > 5).Select(y => new Customer { Name = y.Name, Phone = y.Phone });
```

<span data-ttu-id="5bb87-126">Daha fazla bilgi için bkz.</span><span class="sxs-lookup"><span data-stu-id="5bb87-126">For more information, see:</span></span>

- [<span data-ttu-id="5bb87-127">Nesne ve Koleksiyon Başlatıcıları</span><span class="sxs-lookup"><span data-stu-id="5bb87-127">Object and Collection Initializers</span></span>](../../classes-and-structs/object-and-collection-initializers.md)

- [<span data-ttu-id="5bb87-128">Standart Sorgu İşleçleri için Sorgu İfade Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5bb87-128">Query Expression Syntax for Standard Query Operators</span></span>](./query-expression-syntax-for-standard-query-operators.md)

## <a name="anonymous-types"></a><span data-ttu-id="5bb87-129">Anonim Türler</span><span class="sxs-lookup"><span data-stu-id="5bb87-129">Anonymous Types</span></span>

<span data-ttu-id="5bb87-130">Anonim bir tür derleyici tarafından oluşturulur ve tür adı yalnızca derleyici için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="5bb87-130">An anonymous type is constructed by the compiler and the type name is only available to the compiler.</span></span> <span data-ttu-id="5bb87-131">Adsız türler, ayrı bir adlandırılmış tür tanımlamak zorunda kalmadan, bir dizi özelliği geçici olarak sorgu sonucuna gruplandırmak için kullanışlı bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="5bb87-131">Anonymous types provide a convenient way to group a set of properties temporarily in a query result without having to define a separate named type.</span></span> <span data-ttu-id="5bb87-132">Anonim türleri burada gösterildiği gibi, yeni bir ifade ve bir nesne baş harfi ile baş harfe</span><span class="sxs-lookup"><span data-stu-id="5bb87-132">Anonymous types are initialized with a new expression and an object initializer, as shown here:</span></span>

```csharp
select new {name = cust.Name, phone = cust.Phone};
```

<span data-ttu-id="5bb87-133">Daha fazla bilgi için [Bkz. Anonim Türler.](../../classes-and-structs/anonymous-types.md)</span><span class="sxs-lookup"><span data-stu-id="5bb87-133">For more information, see [Anonymous Types](../../classes-and-structs/anonymous-types.md).</span></span>

## <a name="extension-methods"></a><span data-ttu-id="5bb87-134">Genişletme Yöntemleri</span><span class="sxs-lookup"><span data-stu-id="5bb87-134">Extension Methods</span></span>

<span data-ttu-id="5bb87-135">Uzantı yöntemi, bir türle ilişkilendirilebilen statik bir yöntemdir, böylece türüzerinde bir örnek yöntemi yatılabilir.</span><span class="sxs-lookup"><span data-stu-id="5bb87-135">An extension method is a static method that can be associated with a type, so that it can be called as if it were an instance method on the type.</span></span> <span data-ttu-id="5bb87-136">Bu özellik, gerçekte, gerçekte bunları değiştirmeden varolan türlere yeni yöntemler "eklemek" sağlar.</span><span class="sxs-lookup"><span data-stu-id="5bb87-136">This feature enables you to, in effect, "add" new methods to existing types without actually modifying them.</span></span> <span data-ttu-id="5bb87-137">Standart sorgu işleçleri, linq sorgusu işlevselliği sağlayan bir uzantı yöntemi kümesidir. <xref:System.Collections.Generic.IEnumerable%601></span><span class="sxs-lookup"><span data-stu-id="5bb87-137">The standard query operators are a set of extension methods that provide LINQ query functionality for any type that implements <xref:System.Collections.Generic.IEnumerable%601>.</span></span>

<span data-ttu-id="5bb87-138">Daha fazla bilgi için [Uzantı Yöntemleri'ne](../../classes-and-structs/extension-methods.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="5bb87-138">For more information, see [Extension Methods](../../classes-and-structs/extension-methods.md).</span></span>

## <a name="lambda-expressions"></a><span data-ttu-id="5bb87-139">Lambda İfadeleri</span><span class="sxs-lookup"><span data-stu-id="5bb87-139">Lambda Expressions</span></span>

<span data-ttu-id="5bb87-140">Lambda ifadesi, giriş parametrelerini işlev gövdesinden ayırmak için => işleci kullanan ve derleme zamanında bir temsilciye veya bir ifade ağacına dönüştürülebilen bir satır dışı işlevdir.</span><span class="sxs-lookup"><span data-stu-id="5bb87-140">A lambda expression is an inline function that uses the => operator to separate input parameters from the function body and can be converted at compile time to a delegate or an expression tree.</span></span> <span data-ttu-id="5bb87-141">LINQ programlamada, standart sorgu işleçlerine doğrudan yöntem aramaları yaptığınızda lambda ifadelerle karşılaşırsınız.</span><span class="sxs-lookup"><span data-stu-id="5bb87-141">In LINQ programming, you will encounter lambda expressions when you make direct method calls to the standard query operators.</span></span>

<span data-ttu-id="5bb87-142">Daha fazla bilgi için bkz.</span><span class="sxs-lookup"><span data-stu-id="5bb87-142">For more information, see:</span></span>

- [<span data-ttu-id="5bb87-143">Anonim Fonksiyonlar</span><span class="sxs-lookup"><span data-stu-id="5bb87-143">Anonymous Functions</span></span>](../../statements-expressions-operators/anonymous-functions.md)

- [<span data-ttu-id="5bb87-144">Lambda İfadeler</span><span class="sxs-lookup"><span data-stu-id="5bb87-144">Lambda Expressions</span></span>](../../statements-expressions-operators/lambda-expressions.md)

- [<span data-ttu-id="5bb87-145">İfade Ağaçları (C#)</span><span class="sxs-lookup"><span data-stu-id="5bb87-145">Expression Trees (C#)</span></span>](../expression-trees/index.md)

## <a name="see-also"></a><span data-ttu-id="5bb87-146">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5bb87-146">See also</span></span>

- [<span data-ttu-id="5bb87-147">Dil-Tümleşik Sorgu (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="5bb87-147">Language-Integrated Query (LINQ) (C#)</span></span>](./index.md)
