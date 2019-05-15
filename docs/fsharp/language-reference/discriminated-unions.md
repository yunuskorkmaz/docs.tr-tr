---
title: Ayrılmış Birleşimler
description: Nasıl kullanacağınızı öğrenin F# ayrılmış birleşimler.
ms.date: 05/16/2016
ms.openlocfilehash: 27fb9205f3f216adc435483fd1dcc839a6e13e03
ms.sourcegitcommit: 682c64df0322c7bda016f8bfea8954e9b31f1990
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/13/2019
ms.locfileid: "65557967"
---
# <a name="discriminated-unions"></a><span data-ttu-id="14a1b-103">Ayrılmış Birleşimler</span><span class="sxs-lookup"><span data-stu-id="14a1b-103">Discriminated Unions</span></span>

<span data-ttu-id="14a1b-104">Ayrılmış birleşimler, bir dizi adlandırılmış durumlarda, büyük olasılıkla her biri farklı değerde ve türde herhangi birini değerler için destek sağlar.</span><span class="sxs-lookup"><span data-stu-id="14a1b-104">Discriminated unions provide support for values that can be one of a number of named cases, possibly each with different values and types.</span></span> <span data-ttu-id="14a1b-105">Ayrılmış birleşimler heterojen veriler için kullanışlı; Geçerli dahil olmak üzere, özel durumlar ve hata durumları veri; bir örneği bir türden diğerine değişen verileri; ve küçük nesne hiyerarşileri için alternatif olarak.</span><span class="sxs-lookup"><span data-stu-id="14a1b-105">Discriminated unions are useful for heterogeneous data; data that can have special cases, including valid and error cases; data that varies in type from one instance to another; and as an alternative for small object hierarchies.</span></span> <span data-ttu-id="14a1b-106">Ayrıca, özyinelemeli ayırt edici birleşimler ağaç veri yapılarını temsil etmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="14a1b-106">In addition, recursive discriminated unions are used to represent tree data structures.</span></span>

## <a name="syntax"></a><span data-ttu-id="14a1b-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="14a1b-107">Syntax</span></span>

```fsharp
[ attributes ]
type [accessibility-modifier] type-name =
    | case-identifier1 [of [ fieldname1 : ] type1 [ * [ fieldname2 : ] type2 ...]
    | case-identifier2 [of [fieldname3 : ]type3 [ * [ fieldname4 : ]type4 ...]

    [ member-list ]
```

## <a name="remarks"></a><span data-ttu-id="14a1b-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="14a1b-108">Remarks</span></span>

<span data-ttu-id="14a1b-109">Ayrılmış birleşimler, diğer dillerdeki birleşim türleriyle benzerdir, ancak bazı farklılıklar vardır.</span><span class="sxs-lookup"><span data-stu-id="14a1b-109">Discriminated unions are similar to union types in other languages, but there are differences.</span></span> <span data-ttu-id="14a1b-110">Olarak C++ içindeki birleşim türünde veya Visual Basic içindeki değişken türünde değerde depolanan veriler sabit; ayrı ayrı birkaç seçenekten biri olabilir.</span><span class="sxs-lookup"><span data-stu-id="14a1b-110">As with a union type in C++ or a variant type in Visual Basic, the data stored in the value is not fixed; it can be one of several distinct options.</span></span> <span data-ttu-id="14a1b-111">Diğer bu dillerdeki birleşimlerden farklı olarak, Bununla birlikte, olası seçeneklerin her biri verilir bir *durum tanımlayıcı*.</span><span class="sxs-lookup"><span data-stu-id="14a1b-111">Unlike unions in these other languages, however, each of the possible options is given a *case identifier*.</span></span> <span data-ttu-id="14a1b-112">Durum tanımlayıcıları, bu tür nesneler olabilir değerleri çeşitli olası türleri adlarıdır; İsteğe bağlı değerler.</span><span class="sxs-lookup"><span data-stu-id="14a1b-112">The case identifiers are names for the various possible types of values that objects of this type could be; the values are optional.</span></span> <span data-ttu-id="14a1b-113">Değerler mevcut değilse, böyle bir numaralandırma vakasına eşdeğerdir.</span><span class="sxs-lookup"><span data-stu-id="14a1b-113">If values are not present, the case is equivalent to an enumeration case.</span></span> <span data-ttu-id="14a1b-114">Değerler varsa her değer ya da belirtilen bir türün ya da aynı ya da farklı türlerin birden çok alanını toplayan bir tanımlama grubu tek bir değer olabilir.</span><span class="sxs-lookup"><span data-stu-id="14a1b-114">If values are present, each value can either be a single value of a specified type, or a tuple that aggregates multiple fields of the same or different types.</span></span> <span data-ttu-id="14a1b-115">Ayrı ayrı alanlara bir ad verebilirsiniz ancak aynı durumdaki diğer alanlar adlandırılmış olsa dahi, isteğe bağlı adıdır.</span><span class="sxs-lookup"><span data-stu-id="14a1b-115">You can give an individual field a name, but the name is optional, even if other fields in the same case are named.</span></span>

<span data-ttu-id="14a1b-116">Ayrılmış birleşimler için erişilebilirlik varsayılanları `public`.</span><span class="sxs-lookup"><span data-stu-id="14a1b-116">Accessibility for discriminated unions defaults to `public`.</span></span>

<span data-ttu-id="14a1b-117">Örneğin, bir şekil türünün aşağıdaki bildirimini düşünün.</span><span class="sxs-lookup"><span data-stu-id="14a1b-117">For example, consider the following declaration of a Shape type.</span></span>

```fsharp
type Shape =
    | Rectangle of width : float * length : float
    | Circle of radius : float
    | Prism of width : float * float * height : float
```

<span data-ttu-id="14a1b-118">Yukarıdaki kod, ayrılmış bir birleşim herhangi birinin üç durum değerleri olan şekil bildirir: Dikdörtgen, daire ve Prizma.</span><span class="sxs-lookup"><span data-stu-id="14a1b-118">The preceding code declares a discriminated union Shape, which can have values of any of three cases: Rectangle, Circle, and Prism.</span></span> <span data-ttu-id="14a1b-119">Her durumda, farklı bir alan kümesi vardır.</span><span class="sxs-lookup"><span data-stu-id="14a1b-119">Each case has a different set of fields.</span></span> <span data-ttu-id="14a1b-120">Dikdörtgenin çalışması sahip iki adlı alanları, iki tür `float`, genişlik ve uzunluk adlarına sahip.</span><span class="sxs-lookup"><span data-stu-id="14a1b-120">The Rectangle case has two named fields, both of type `float`, that have the names width and length.</span></span> <span data-ttu-id="14a1b-121">Circle durumu yalnızca bir adlandırılmış alana sahiptir RADIUS.</span><span class="sxs-lookup"><span data-stu-id="14a1b-121">The Circle case has just one named field, radius.</span></span> <span data-ttu-id="14a1b-122">Prism durumunun üç alanı vardır alanları adlı iki hangi (genişlik ve yükseklik).</span><span class="sxs-lookup"><span data-stu-id="14a1b-122">The Prism case has three fields, two of which (width and height) are named fields.</span></span> <span data-ttu-id="14a1b-123">Adlandırılmamış anonim alan olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="14a1b-123">Unnamed fields are referred to as anonymous fields.</span></span>

<span data-ttu-id="14a1b-124">Aşağıdaki örnekler göre adlandırılmış ve anonim alanlar için değerleri sağlayarak nesneleri oluşturmak.</span><span class="sxs-lookup"><span data-stu-id="14a1b-124">You construct objects by providing values for the named and anonymous fields according to the following examples.</span></span>

```fsharp
let rect = Rectangle(length = 1.3, width = 10.0)
let circ = Circle (1.0)
let prism = Prism(5., 2.0, height = 3.0)
```

<span data-ttu-id="14a1b-125">Bu kod, başlatma işlemindeki adlandırılmış alanları kullanabilirsiniz, veya bildirimdeki alanların sıralamasını üzerinde kullanır ve her alan için değerleri'yalnızca sırayla sağlayın gösterir.</span><span class="sxs-lookup"><span data-stu-id="14a1b-125">This code shows that you can either use the named fields in the initialization, or you can rely on the ordering of the fields in the declaration and just provide the values for each field in turn.</span></span> <span data-ttu-id="14a1b-126">İçin oluşturucu çağrısı `rect` önceki kod içinde adlandırılmış alanları, ancak için oluşturucu çağrısı kullanır `circ` sıralamayı kullanır.</span><span class="sxs-lookup"><span data-stu-id="14a1b-126">The constructor call for `rect` in the previous code uses the named fields, but the constructor call for `circ` uses the ordering.</span></span> <span data-ttu-id="14a1b-127">Sıralı alanları karıştırabilirsiniz ve alanları, oluşumunu olduğu gibi adlı `prism`.</span><span class="sxs-lookup"><span data-stu-id="14a1b-127">You can mix the ordered fields and named fields, as in the construction of `prism`.</span></span>

<span data-ttu-id="14a1b-128">`option` Türüdür, basit bir birleşimdir F# çekirdek kitaplığı.</span><span class="sxs-lookup"><span data-stu-id="14a1b-128">The `option` type is a simple discriminated union in the F# core library.</span></span> <span data-ttu-id="14a1b-129">`option` Türü gibi bildirilir.</span><span class="sxs-lookup"><span data-stu-id="14a1b-129">The `option` type is declared as follows.</span></span>

```fsharp
// The option type is a discriminated union.
type Option<'a> =
    | Some of 'a
    | None
```

<span data-ttu-id="14a1b-130">Önceki kod belirten türü `Option` iki duruma sahip ayrılmış bir birleşim olduğunu `Some` ve `None`.</span><span class="sxs-lookup"><span data-stu-id="14a1b-130">The previous code specifies that the type `Option` is a discriminated union that has two cases, `Some` and `None`.</span></span> <span data-ttu-id="14a1b-131">`Some` Çalışması türü tür parametresi ile temsil edilir bir anonim alan içeren ilişkili değeri var `'a`.</span><span class="sxs-lookup"><span data-stu-id="14a1b-131">The `Some` case has an associated value that consists of one anonymous field whose type is represented by the type parameter `'a`.</span></span> <span data-ttu-id="14a1b-132">`None` Çalışması ilişkili değere sahip.</span><span class="sxs-lookup"><span data-stu-id="14a1b-132">The `None` case has no associated value.</span></span> <span data-ttu-id="14a1b-133">Bu nedenle `option` türü veya tür veya değer değeri olan bir genel tür belirtir.</span><span class="sxs-lookup"><span data-stu-id="14a1b-133">Thus the `option` type specifies a generic type that either has a value of some type or no value.</span></span> <span data-ttu-id="14a1b-134">Türü `Option` ayrıca bir küçük harf tür diğer adı olan `option`, yani daha sık kullanılan.</span><span class="sxs-lookup"><span data-stu-id="14a1b-134">The type `Option` also has a lowercase type alias, `option`, that is more commonly used.</span></span>

<span data-ttu-id="14a1b-135">Durum tanımlayıcıları, ayrılmış birleşim türü için oluşturucu kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="14a1b-135">The case identifiers can be used as constructors for the discriminated union type.</span></span> <span data-ttu-id="14a1b-136">Örneğin, aşağıdaki kod değerler oluşturmak için kullanılan `option` türü.</span><span class="sxs-lookup"><span data-stu-id="14a1b-136">For example, the following code is used to create values of the `option` type.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2001.fs)]

<span data-ttu-id="14a1b-137">Durum tanımlayıcıları da Desen eşleştirme ifadelerinde kullanılır.</span><span class="sxs-lookup"><span data-stu-id="14a1b-137">The case identifiers are also used in pattern matching expressions.</span></span> <span data-ttu-id="14a1b-138">Bir desen eşleme ifadesinde tanımlayıcılar tek tek durumlarla ilişkili değerler için sağlanır.</span><span class="sxs-lookup"><span data-stu-id="14a1b-138">In a pattern matching expression, identifiers are provided for the values associated with the individual cases.</span></span> <span data-ttu-id="14a1b-139">Örneğin, aşağıdaki kodda, `x` tanımlayıcısı ile ilişkili değer verilen `Some` durumu `option` türü.</span><span class="sxs-lookup"><span data-stu-id="14a1b-139">For example, in the following code, `x` is the identifier given the value that is associated with the `Some` case of the `option` type.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2002.fs)]

<span data-ttu-id="14a1b-140">Desen eşleştirme ifadelerinde, ayrılmış birleşim eşleşmelerini belirtmek için adlandırılmış alanları kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="14a1b-140">In pattern matching expressions, you can use named fields to specify discriminated union matches.</span></span> <span data-ttu-id="14a1b-141">Alanların değerlerini ayıklamak için aşağıdaki kodda gösterildiği gibi daha önceden bildirilen Şekil türü için adlandırılmış alanları kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="14a1b-141">For the Shape type that was declared previously, you can use the named fields as the following code shows to extract the values of the fields.</span></span>

```fsharp
let getShapeHeight shape =
    match shape with
    | Rectangle(height = h) -> h
    | Circle(radius = r) -> 2. * r
    | Prism(height = h) -> h
```

<span data-ttu-id="14a1b-142">Normalde, büyük/küçük harf tanımlayıcıları, birleşim adıyla nitelemeden kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="14a1b-142">Normally, the case identifiers can be used without qualifying them with the name of the union.</span></span> <span data-ttu-id="14a1b-143">Her zaman için birleşim adıyla nitelendirilmesi adını isterseniz uygulayabilirsiniz [RequireQualifiedAccess](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.requirequalifiedaccessattribute-class-[fsharp]) özniteliğini birleşim türü tanımına.</span><span class="sxs-lookup"><span data-stu-id="14a1b-143">If you want the name to always be qualified with the name of the union, you can apply the [RequireQualifiedAccess](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.requirequalifiedaccessattribute-class-[fsharp]) attribute to the union type definition.</span></span>

### <a name="unwrapping-discriminated-unions"></a><span data-ttu-id="14a1b-144">Açma ayrılmış birleşimler</span><span class="sxs-lookup"><span data-stu-id="14a1b-144">Unwrapping Discriminated Unions</span></span>

<span data-ttu-id="14a1b-145">İçinde F# ayırt edici birleşimler sık kullanılan etki alanı modelleme, tek bir tür sarmalama için.</span><span class="sxs-lookup"><span data-stu-id="14a1b-145">In F# Discriminated Unions are often used in domain-modeling for wrapping a single type.</span></span> <span data-ttu-id="14a1b-146">Temeldeki değeri de desen eşleştirme aracılığıyla ayıklamak kolay bir işlemdir.</span><span class="sxs-lookup"><span data-stu-id="14a1b-146">It's easy to extract the underlying value via pattern matching as well.</span></span> <span data-ttu-id="14a1b-147">Bir eşleme ifadesi için tek bir kasada kullanmanız gerekmez:</span><span class="sxs-lookup"><span data-stu-id="14a1b-147">You don't need to use a match expression for a single case:</span></span>

```fsharp
let ([UnionCaseName] [values]) = [UnionValue]
```

<span data-ttu-id="14a1b-148">Aşağıdaki örnek bunu gösterir:</span><span class="sxs-lookup"><span data-stu-id="14a1b-148">The following example demonstrates this:</span></span>

```fsharp
type ShaderProgram = | ShaderProgram of id:int

let someFunctionUsingShaderProgram shaderProgram =
    let (ShaderProgram id) = shaderProgram
    // Use the unwrapped value
    ...
```

<span data-ttu-id="14a1b-149">Burada tek bir kasada sarmalamadan çıkarma için desen eşleştirme doğrudan işlev parametrelerinde da izin verilir:</span><span class="sxs-lookup"><span data-stu-id="14a1b-149">Pattern matching is also allowed directly in function parameters, so you can unwrap a single case there:</span></span>

```fsharp
let someFunctionUsingShaderProgram (ShaderProgram id) =
    // Use the unwrapped value
    ...
```

## <a name="struct-discriminated-unions"></a><span data-ttu-id="14a1b-150">Ayrılmış birleşimler yapısı</span><span class="sxs-lookup"><span data-stu-id="14a1b-150">Struct Discriminated Unions</span></span>

<span data-ttu-id="14a1b-151">İle başlayarak F# 4.1, ayırt edici birleşimler yapı birimleri olarak da temsil edebilir.</span><span class="sxs-lookup"><span data-stu-id="14a1b-151">Starting with F# 4.1, you can also represent Discriminated Unions as structs.</span></span>  <span data-ttu-id="14a1b-152">Bunun `[<Struct>]` özniteliği.</span><span class="sxs-lookup"><span data-stu-id="14a1b-152">This is done with the `[<Struct>]` attribute.</span></span>

```fsharp
[<Struct>]
type SingleCase = Case of string

[<Struct>]
type Multicase =
    | Case1 of Case1 : string
    | Case2 of Case2 : int
    | Case3 of Case3 : double
```

<span data-ttu-id="14a1b-153">Bu değer türleri ve başvuru türleri değil çünkü vardır ek konuları başvuru ile karşılaştırıldığında ayırt edici birleşimler:</span><span class="sxs-lookup"><span data-stu-id="14a1b-153">Because these are value types and not reference types, there are extra considerations compared with reference discriminated unions:</span></span>

1. <span data-ttu-id="14a1b-154">Bunlar, değer türleri kopyalanır ve değer türü anlamları vardır.</span><span class="sxs-lookup"><span data-stu-id="14a1b-154">They are copied as value types and have value type semantics.</span></span>
2. <span data-ttu-id="14a1b-155">Bir özyinelemeli tür tanımı Discriminated birleşim multicase yapı ile kullanamazsınız.</span><span class="sxs-lookup"><span data-stu-id="14a1b-155">You cannot use a recursive type definition with a multicase struct Discriminated Union.</span></span>
3. <span data-ttu-id="14a1b-156">Multicase yapı Discriminated birleşim büyük/küçük harf benzersiz adlar sağlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="14a1b-156">You must provide unique case names for a multicase struct Discriminated Union.</span></span>

## <a name="using-discriminated-unions-instead-of-object-hierarchies"></a><span data-ttu-id="14a1b-157">Nesne hiyerarşileri yerine ayrılmış birleşimler kullanma</span><span class="sxs-lookup"><span data-stu-id="14a1b-157">Using Discriminated Unions Instead of Object Hierarchies</span></span>

<span data-ttu-id="14a1b-158">Küçük nesne hiyerarşisi için basit bir alternatif olarak, ayrılmış bir birleşim genellikle kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="14a1b-158">You can often use a discriminated union as a simpler alternative to a small object hierarchy.</span></span> <span data-ttu-id="14a1b-159">Örneğin, aşağıdaki ayrılmış bileşim yerine kullanılabilecek bir `Shape` temel türleri daire, türetilmiş kare vb. sınıfı.</span><span class="sxs-lookup"><span data-stu-id="14a1b-159">For example, the following discriminated union could be used instead of a `Shape` base class that has derived types for circle, square, and so on.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2003.fs)]

<span data-ttu-id="14a1b-160">Bunun yerine bir alan veya çevre hesaplamak için sanal bir yöntem, nesne yönelimli bir uygulamada kullanmanız gerekir, bu miktarları hesaplamak için uygun formüllere eşleşen kalıbı kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="14a1b-160">Instead of a virtual method to compute an area or perimeter, as you would use in an object-oriented implementation, you can use pattern matching to branch to appropriate formulas to compute these quantities.</span></span> <span data-ttu-id="14a1b-161">Aşağıdaki örnekte, şekile bağlı olarak alan hesaplamak için farklı formüller kullanılır.</span><span class="sxs-lookup"><span data-stu-id="14a1b-161">In the following example, different formulas are used to compute the area, depending on the shape.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2004.fs)]

<span data-ttu-id="14a1b-162">Çıktı aşağıdaki şekilde olacaktır:</span><span class="sxs-lookup"><span data-stu-id="14a1b-162">The output is as follows:</span></span>

```
Area of circle that has radius 15.000000: 706.858347
Area of square that has side 10.000000: 100.000000
Area of rectangle that has height 5.000000 and width 10.000000 is 50.000000
```

## <a name="using-discriminated-unions-for-tree-data-structures"></a><span data-ttu-id="14a1b-163">Ayrılmış birleşimler ağaç veri yapıları için kullanma</span><span class="sxs-lookup"><span data-stu-id="14a1b-163">Using Discriminated Unions for Tree Data Structures</span></span>

<span data-ttu-id="14a1b-164">Ayrılmış birleşimler, yani birleşim kendi başına bir veya daha fazla türünü eklenebilir, özyinelemeli olabilir.</span><span class="sxs-lookup"><span data-stu-id="14a1b-164">Discriminated unions can be recursive, meaning that the union itself can be included in the type of one or more cases.</span></span> <span data-ttu-id="14a1b-165">Özyinelemeli ayrılmış birleşimler, programlama dillerindeki ifadeleri için kullanılan ağaç yapıları oluşturmak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="14a1b-165">Recursive discriminated unions can be used to create tree structures, which are used to model expressions in programming languages.</span></span> <span data-ttu-id="14a1b-166">Aşağıdaki kodda bir özyinelemeli ayrılmış birleşim bir ikili ağaç veri yapısı oluşturmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="14a1b-166">In the following code, a recursive discriminated union is used to create a binary tree data structure.</span></span> <span data-ttu-id="14a1b-167">Birleşim iki durumdan oluşur `Node`, bir tamsayı değeri ile sol ve sağ alt ağaçlara sahip bir düğüm ve `Tip`, ve ağacı sonlandıran.</span><span class="sxs-lookup"><span data-stu-id="14a1b-167">The union consists of two cases, `Node`, which is a node with an integer value and left and right subtrees, and `Tip`, which terminates the tree.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2005.fs)]

<span data-ttu-id="14a1b-168">Önceki kodda, `resultSumTree` 10 değerine sahiptir.</span><span class="sxs-lookup"><span data-stu-id="14a1b-168">In the previous code, `resultSumTree` has the value 10.</span></span> <span data-ttu-id="14a1b-169">Ağaç yapısı için aşağıdaki çizimde `myTree`.</span><span class="sxs-lookup"><span data-stu-id="14a1b-169">The following illustration shows the tree structure for `myTree`.</span></span>

![MyTree için ağaç yapısı gösteren diyagram.](../media/discriminated-unions/tree-structure-mytree.png)

<span data-ttu-id="14a1b-171">Ayrılmış birleşimler Ağaçtaki düğümler heterojen iyi çalışır.</span><span class="sxs-lookup"><span data-stu-id="14a1b-171">Discriminated unions work well if the nodes in the tree are heterogeneous.</span></span> <span data-ttu-id="14a1b-172">Aşağıdaki kodda, türü `Expression` toplanmasını ve çarpılmasını sayıların ve değişkenlerin destekler basit bir programlama dili, bir ifadenin soyut sözdizimi ağacını temsil eder.</span><span class="sxs-lookup"><span data-stu-id="14a1b-172">In the following code, the type `Expression` represents the abstract syntax tree of an expression in a simple programming language that supports addition and multiplication of numbers and variables.</span></span> <span data-ttu-id="14a1b-173">Bazı birleşim durumları özyinelemeli değildir ve sayıları temsil eder (`Number`) veya değişkenler (`Variable`).</span><span class="sxs-lookup"><span data-stu-id="14a1b-173">Some of the union cases are not recursive and represent either numbers (`Number`) or variables (`Variable`).</span></span> <span data-ttu-id="14a1b-174">Diğer durumlarda özyinelemelidir ve işlemleri temsil etmekte (`Add` ve `Multiply`), işlenenlerin de ifadeleri olduğu.</span><span class="sxs-lookup"><span data-stu-id="14a1b-174">Other cases are recursive, and represent operations (`Add` and `Multiply`), where the operands are also expressions.</span></span> <span data-ttu-id="14a1b-175">`Evaluate` İşlevi sözdizimi ağacını yinelemeli olarak işlemek için bir eşleme ifadesi kullanılır.</span><span class="sxs-lookup"><span data-stu-id="14a1b-175">The `Evaluate` function uses a match expression to recursively process the syntax tree.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2006.fs)]

<span data-ttu-id="14a1b-176">Bu kod zaman yürütülür, değerini `result` 5'tir.</span><span class="sxs-lookup"><span data-stu-id="14a1b-176">When this code is executed, the value of `result` is 5.</span></span>

## <a name="common-attributes"></a><span data-ttu-id="14a1b-177">Ortak Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="14a1b-177">Common Attributes</span></span>

<span data-ttu-id="14a1b-178">Aşağıdaki öznitelikler de ayrılmış birleşimler yaygın olarak görülür:</span><span class="sxs-lookup"><span data-stu-id="14a1b-178">The following attributes are commonly seen in discriminated unions:</span></span>

* `[RequireQualifiedAccess]`
* `[NoEquality]`
* `[NoComparison]`
* `[Struct]`

## <a name="see-also"></a><span data-ttu-id="14a1b-179">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="14a1b-179">See also</span></span>

- [<span data-ttu-id="14a1b-180">F# Dili Başvurusu</span><span class="sxs-lookup"><span data-stu-id="14a1b-180">F# Language Reference</span></span>](index.md)
