---
title: LINQ'i Destekleyen C# Özellikleri
ms.date: 07/20/2015
helpviewer_keywords:
- LINQ [C#], features supporting LINQ
ms.assetid: 524b0078-ebfd-45a7-b390-f2ceb9d84797
ms.openlocfilehash: 32ba8f5e60b3ed2efd813a8ae32e5f4009eb790d
ms.sourcegitcommit: 71b8f5a2108a0f1a4ef1d8d75c5b3e129ec5ca1e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/29/2020
ms.locfileid: "84202403"
---
# <a name="c-features-that-support-linq"></a><span data-ttu-id="91bf0-102">LINQ'i Destekleyen C# Özellikleri</span><span class="sxs-lookup"><span data-stu-id="91bf0-102">C# Features That Support LINQ</span></span>

<span data-ttu-id="91bf0-103">Aşağıdaki bölümde C# 3,0 ' de tanıtılan yeni dil yapıları tanıtılmaktadır.</span><span class="sxs-lookup"><span data-stu-id="91bf0-103">The following section introduces new language constructs introduced in C# 3.0.</span></span> <span data-ttu-id="91bf0-104">Bu yeni özelliklerin tümü LINQ sorgularıyla bir dereceye kadar kullanılsa da, LINQ ile sınırlı değildir ve yararlı bulduğunuz herhangi bir bağlamda kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="91bf0-104">Although these new features are all used to a degree with LINQ queries, they are not limited to LINQ and can be used in any context where you find them useful.</span></span>

## <a name="query-expressions"></a><span data-ttu-id="91bf0-105">Sorgu İfadeleri</span><span class="sxs-lookup"><span data-stu-id="91bf0-105">Query Expressions</span></span>

<span data-ttu-id="91bf0-106">Sorgu ifadeleri, IEnumerable koleksiyonlarını sorgulamak için SQL veya XQuery ile benzer bir bildirime dayalı sözdizimi kullanır.</span><span class="sxs-lookup"><span data-stu-id="91bf0-106">Query expressions use a declarative syntax similar to SQL or XQuery to query over IEnumerable collections.</span></span> <span data-ttu-id="91bf0-107">Derleme zamanı sorgu söz dizimi, bir LINQ sağlayıcısının standart sorgu işleci genişletme yöntemlerinin uygulamasına yönelik yöntem çağrılarına dönüştürülür.</span><span class="sxs-lookup"><span data-stu-id="91bf0-107">At compile time query syntax is converted to method calls to a LINQ provider's implementation of the standard query operator extension methods.</span></span> <span data-ttu-id="91bf0-108">Uygulamalar, uygun ad alanını bir yönergeyle belirterek kapsamdaki standart sorgu işleçlerini denetler `using` .</span><span class="sxs-lookup"><span data-stu-id="91bf0-108">Applications control the standard query operators that are in scope by specifying the appropriate namespace with a `using` directive.</span></span> <span data-ttu-id="91bf0-109">Aşağıdaki sorgu ifadesi bir dize dizisi alır, bunları dizedeki ilk karaktere göre gruplandırır ve grupları sıralar.</span><span class="sxs-lookup"><span data-stu-id="91bf0-109">The following query expression takes an array of strings, groups them according to the first character in the string, and orders the groups.</span></span>

```csharp
var query = from str in stringArray
            group str by str[0] into stringGroup
            orderby stringGroup.Key
            select stringGroup;
```

<span data-ttu-id="91bf0-110">Daha fazla bilgi için bkz. [LINQ sorgu ifadeleri](../../../linq/index.md).</span><span class="sxs-lookup"><span data-stu-id="91bf0-110">For more information, see [LINQ Query Expressions](../../../linq/index.md).</span></span>

## <a name="implicitly-typed-variables-var"></a><span data-ttu-id="91bf0-111">Örtük olarak yazılan değişkenler (var)</span><span class="sxs-lookup"><span data-stu-id="91bf0-111">Implicitly Typed Variables (var)</span></span>

<span data-ttu-id="91bf0-112">Bir değişkeni bildirdiğinizde ve başlattığınızda açıkça bir tür belirtmek yerine, derleyicinin türü çıkarması ve atamasını bildirmek için, burada gösterildiği gibi [var](../../../language-reference/keywords/var.md) değiştiricisini kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="91bf0-112">Instead of explicitly specifying a type when you declare and initialize a variable, you can use the [var](../../../language-reference/keywords/var.md) modifier to instruct the compiler to infer and assign the type, as shown here:</span></span>

```csharp
var number = 5;
var name = "Virginia";
var query = from str in stringArray
            where str[0] == 'm'
            select str;
```

<span data-ttu-id="91bf0-113">Olarak belirtilen değişkenler `var` , türü açıkça belirttiğiniz değişkenler olarak kesin şekilde türdedir.</span><span class="sxs-lookup"><span data-stu-id="91bf0-113">Variables declared as `var` are just as strongly typed as variables whose type you specify explicitly.</span></span> <span data-ttu-id="91bf0-114">Öğesinin kullanımı `var` anonim türler oluşturmayı mümkün kılar, ancak yalnızca yerel değişkenler için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="91bf0-114">The use of `var` makes it possible to create anonymous types, but it can be used only for local variables.</span></span> <span data-ttu-id="91bf0-115">Diziler, örtük yazma ile de bildirilemez.</span><span class="sxs-lookup"><span data-stu-id="91bf0-115">Arrays can also be declared with implicit typing.</span></span>

<span data-ttu-id="91bf0-116">Daha fazla bilgi için bkz. [örtülü olarak yazılan yerel değişkenler](../../classes-and-structs/implicitly-typed-local-variables.md).</span><span class="sxs-lookup"><span data-stu-id="91bf0-116">For more information, see [Implicitly Typed Local Variables](../../classes-and-structs/implicitly-typed-local-variables.md).</span></span>

## <a name="object-and-collection-initializers"></a><span data-ttu-id="91bf0-117">Nesne ve Koleksiyon Başlatıcıları</span><span class="sxs-lookup"><span data-stu-id="91bf0-117">Object and Collection Initializers</span></span>

<span data-ttu-id="91bf0-118">Nesne ve koleksiyon başlatıcıları nesne için bir oluşturucu açıkça çağrılmadan nesneleri başlatmayı mümkün hale getirir.</span><span class="sxs-lookup"><span data-stu-id="91bf0-118">Object and collection initializers make it possible to initialize objects without explicitly calling a constructor for the object.</span></span> <span data-ttu-id="91bf0-119">Başlatıcılar, genellikle, kaynak verileri yeni bir veri türüne proje yaparken sorgu ifadelerinde kullanılır.</span><span class="sxs-lookup"><span data-stu-id="91bf0-119">Initializers are typically used in query expressions when they project the source data into a new data type.</span></span> <span data-ttu-id="91bf0-120">Public ve Properties ile adlandırılmış bir sınıf varsayıldığında `Customer` `Name` `Phone` , nesne Başlatıcısı aşağıdaki kodda olduğu gibi kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="91bf0-120">Assuming a class named `Customer` with public `Name` and `Phone` properties, the object initializer can be used as in the following code:</span></span>

```csharp
var cust = new Customer { Name = "Mike", Phone = "555-1212" };
```

<span data-ttu-id="91bf0-121">Sınıfımızla devam ederek, `Customer` adlı bir veri kaynağı olduğunu `IncomingOrders` ve her sıra büyük bir sipariş için bu `OrderSize` sırada yeni bir temel oluşturmak istiyoruz `Customer` .</span><span class="sxs-lookup"><span data-stu-id="91bf0-121">Continuing with our `Customer` class, assume that there is a data source called `IncomingOrders`, and that for each order with a large `OrderSize`, we would like to create a new `Customer` based off of that order.</span></span> <span data-ttu-id="91bf0-122">Bir LINQ sorgusu bu veri kaynağında yürütülebilir ve bir koleksiyonu doldurarak nesne başlatma işlemi kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="91bf0-122">A LINQ query can be executed on this data source and use object initialization to fill a collection:</span></span>

```csharp
var newLargeOrderCustomers = from o in IncomingOrders
                            where o.OrderSize > 5
                            select new Customer { Name = o.Name, Phone = o.Phone };
```

<span data-ttu-id="91bf0-123">Veri kaynağı, gibi bir sınıftan çok daha fazla özelliğe sahip olabilir `Customer` `OrderSize` , ancak nesne başlatma ile sorgudan döndürülen veriler istenen veri türüne kopyalanır; sınıfımızla ilgili verileri seçiyoruz.</span><span class="sxs-lookup"><span data-stu-id="91bf0-123">The data source may have more properties lying under the hood than the `Customer` class such as `OrderSize`, but with object initialization, the data returned from the query is molded into the desired data type; we choose the data that is relevant to our class.</span></span> <span data-ttu-id="91bf0-124">Sonuç olarak, şimdi `IEnumerable` `Customer` yaptığımız yeni s 'leri doldurduk.</span><span class="sxs-lookup"><span data-stu-id="91bf0-124">As a result, we now have an `IEnumerable` filled with the new `Customer`s we wanted.</span></span> <span data-ttu-id="91bf0-125">Yukarıdaki, LINQ yöntem sözdiziminde de yazılabilir:</span><span class="sxs-lookup"><span data-stu-id="91bf0-125">The above can also be written in LINQ's method syntax:</span></span>

```csharp
var newLargeOrderCustomers = IncomingOrders.Where(x => x.OrderSize > 5).Select(y => new Customer { Name = y.Name, Phone = y.Phone });
```

<span data-ttu-id="91bf0-126">Daha fazla bilgi için bkz.</span><span class="sxs-lookup"><span data-stu-id="91bf0-126">For more information, see:</span></span>

- [<span data-ttu-id="91bf0-127">Nesne ve Koleksiyon Başlatıcıları</span><span class="sxs-lookup"><span data-stu-id="91bf0-127">Object and Collection Initializers</span></span>](../../classes-and-structs/object-and-collection-initializers.md)

- [<span data-ttu-id="91bf0-128">Standart Sorgu İşleçleri için Sorgu İfade Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="91bf0-128">Query Expression Syntax for Standard Query Operators</span></span>](./query-expression-syntax-for-standard-query-operators.md)

## <a name="anonymous-types"></a><span data-ttu-id="91bf0-129">Anonim Türler</span><span class="sxs-lookup"><span data-stu-id="91bf0-129">Anonymous Types</span></span>

<span data-ttu-id="91bf0-130">Anonim bir tür derleyici tarafından oluşturulur ve tür adı yalnızca derleyici tarafından kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="91bf0-130">An anonymous type is constructed by the compiler and the type name is only available to the compiler.</span></span> <span data-ttu-id="91bf0-131">Anonim türler, farklı bir adlandırılmış tür tanımlamak zorunda kalmadan bir özellik kümesini geçici olarak bir sorgu sonucuyla gruplamak için kullanışlı bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="91bf0-131">Anonymous types provide a convenient way to group a set of properties temporarily in a query result without having to define a separate named type.</span></span> <span data-ttu-id="91bf0-132">Anonim türler aşağıda gösterildiği gibi yeni bir ifadeyle ve bir nesne başlatıcısıyla başlatılır:</span><span class="sxs-lookup"><span data-stu-id="91bf0-132">Anonymous types are initialized with a new expression and an object initializer, as shown here:</span></span>

```csharp
select new {name = cust.Name, phone = cust.Phone};
```

<span data-ttu-id="91bf0-133">Daha fazla bilgi için bkz. [anonim türler](../../classes-and-structs/anonymous-types.md).</span><span class="sxs-lookup"><span data-stu-id="91bf0-133">For more information, see [Anonymous Types](../../classes-and-structs/anonymous-types.md).</span></span>

## <a name="extension-methods"></a><span data-ttu-id="91bf0-134">Uzantı Metotları</span><span class="sxs-lookup"><span data-stu-id="91bf0-134">Extension Methods</span></span>

<span data-ttu-id="91bf0-135">Uzantı yöntemi, bir tür ile ilişkilendirilebilen statik bir yöntemdir ve bu sayede tür üzerinde bir örnek yöntemi gibi çağrılabilir.</span><span class="sxs-lookup"><span data-stu-id="91bf0-135">An extension method is a static method that can be associated with a type, so that it can be called as if it were an instance method on the type.</span></span> <span data-ttu-id="91bf0-136">Bu özellik, etkin bir şekilde, var olan türlere "Ekle" gibi yeni yöntemler eklemenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="91bf0-136">This feature enables you to, in effect, "add" new methods to existing types without actually modifying them.</span></span> <span data-ttu-id="91bf0-137">Standart sorgu işleçleri, uygulayan herhangi bir tür için LINQ sorgu işlevselliği sağlayan bir genişletme yöntemleri kümesidir <xref:System.Collections.Generic.IEnumerable%601> .</span><span class="sxs-lookup"><span data-stu-id="91bf0-137">The standard query operators are a set of extension methods that provide LINQ query functionality for any type that implements <xref:System.Collections.Generic.IEnumerable%601>.</span></span>

<span data-ttu-id="91bf0-138">Daha fazla bilgi için bkz. [Uzantı yöntemleri](../../classes-and-structs/extension-methods.md).</span><span class="sxs-lookup"><span data-stu-id="91bf0-138">For more information, see [Extension Methods](../../classes-and-structs/extension-methods.md).</span></span>

## <a name="lambda-expressions"></a><span data-ttu-id="91bf0-139">Lambda İfadeleri</span><span class="sxs-lookup"><span data-stu-id="91bf0-139">Lambda Expressions</span></span>

<span data-ttu-id="91bf0-140">Lambda ifadesi, işlev gövdesinden giriş parametrelerini ayırmak için => işlecini kullanan ve derleme zamanında bir temsilciye veya bir ifade ağacına dönüştürülebilen bir satır içi işlevdir.</span><span class="sxs-lookup"><span data-stu-id="91bf0-140">A lambda expression is an inline function that uses the => operator to separate input parameters from the function body and can be converted at compile time to a delegate or an expression tree.</span></span> <span data-ttu-id="91bf0-141">LINQ programlamada, standart sorgu işleçleri için doğrudan Yöntem çağrıları yaptığınızda lambda ifadeleriyle karşılaşacaksınız.</span><span class="sxs-lookup"><span data-stu-id="91bf0-141">In LINQ programming, you will encounter lambda expressions when you make direct method calls to the standard query operators.</span></span>

<span data-ttu-id="91bf0-142">Daha fazla bilgi için bkz.</span><span class="sxs-lookup"><span data-stu-id="91bf0-142">For more information, see:</span></span>

- [<span data-ttu-id="91bf0-143">Anonim Işlevler</span><span class="sxs-lookup"><span data-stu-id="91bf0-143">Anonymous Functions</span></span>](../../statements-expressions-operators/anonymous-functions.md)

- [<span data-ttu-id="91bf0-144">Lambda Ifadeleri</span><span class="sxs-lookup"><span data-stu-id="91bf0-144">Lambda Expressions</span></span>](../../statements-expressions-operators/lambda-expressions.md)

- [<span data-ttu-id="91bf0-145">İfade ağaçları (C#)</span><span class="sxs-lookup"><span data-stu-id="91bf0-145">Expression Trees (C#)</span></span>](../expression-trees/index.md)

## <a name="see-also"></a><span data-ttu-id="91bf0-146">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="91bf0-146">See also</span></span>

- [<span data-ttu-id="91bf0-147">Dil ile tümleşik sorgu (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="91bf0-147">Language-Integrated Query (LINQ) (C#)</span></span>](./index.md)
