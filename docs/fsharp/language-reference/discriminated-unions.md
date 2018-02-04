---
title: "Ayrılmış Birleşimler (F#)"
description: "F # kullanmayı öğrenin birleşimler."
keywords: "Visual f #, f # işlevsel programlama"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 16e2a011-c785-48c8-859f-79df7f3a0e29
ms.openlocfilehash: b7a02512ce4a63885e771be56f106bc66cc2743e
ms.sourcegitcommit: cf22b29db780e532e1090c6e755aa52d28273fa6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/01/2018
---
# <a name="discriminated-unions"></a><span data-ttu-id="3f44e-104">Ayrılmış Birleşimler</span><span class="sxs-lookup"><span data-stu-id="3f44e-104">Discriminated Unions</span></span>

<span data-ttu-id="3f44e-105">Ayrılmış birleşimler, bir dizi adlandırılmış durumlarda, büyük olasılıkla her farklı değerler ve türlerle biri olabilir değerler için destek sağlar.</span><span class="sxs-lookup"><span data-stu-id="3f44e-105">Discriminated unions provide support for values that can be one of a number of named cases, possibly each with different values and types.</span></span> <span data-ttu-id="3f44e-106">Ayrılmış birleşimler heterojen veriler için kullanışlı; Geçerli dahil olmak üzere özel durumlar ve hata durumları olabilir veri; bir örnek bir türden diğerine değişen verileri; ve küçük nesne Hiyerarşiler için alternatif olarak.</span><span class="sxs-lookup"><span data-stu-id="3f44e-106">Discriminated unions are useful for heterogeneous data; data that can have special cases, including valid and error cases; data that varies in type from one instance to another; and as an alternative for small object hierarchies.</span></span> <span data-ttu-id="3f44e-107">Ayrıca, özyinelemeli ayrılmış birleşimler ağaç veri yapıları temsil etmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="3f44e-107">In addition, recursive discriminated unions are used to represent tree data structures.</span></span>

## <a name="syntax"></a><span data-ttu-id="3f44e-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="3f44e-108">Syntax</span></span>

```fsharp
[ attributes ]
type type-name =
    | case-identifier1 [of [ fieldname1 : ] type1 [ * [ fieldname2 : ] type2 ...]
    | case-identifier2 [of [fieldname3 : ]type3 [ * [ fieldname4 : ]type4 ...]
...
```

## <a name="remarks"></a><span data-ttu-id="3f44e-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="3f44e-109">Remarks</span></span>
<span data-ttu-id="3f44e-110">Ayrılmış birleşimler diğer dillerde birleşim türlerini benzer ancak bazı farklılıklar vardır.</span><span class="sxs-lookup"><span data-stu-id="3f44e-110">Discriminated unions are similar to union types in other languages, but there are differences.</span></span> <span data-ttu-id="3f44e-111">Olarak bir birleşim türü c++ veya Visual Basic değişken türü değerinde depolanan verileri Düzeltilmemiş; Bu seçeneklerden biri veya birkaçı farklı olabilir.</span><span class="sxs-lookup"><span data-stu-id="3f44e-111">As with a union type in C++ or a variant type in Visual Basic, the data stored in the value is not fixed; it can be one of several distinct options.</span></span> <span data-ttu-id="3f44e-112">Bu diğer dillerdeki birleşimler, Bununla birlikte, her bir olası seçenek verilir bir *servis talebi tanımlayıcısı*.</span><span class="sxs-lookup"><span data-stu-id="3f44e-112">Unlike unions in these other languages, however, each of the possible options is given a *case identifier*.</span></span> <span data-ttu-id="3f44e-113">Bu tür nesneler olabilir değerleri çeşitli olası türleri için adları büyük/küçük harfe tanımlayıcılardır; değerleri isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="3f44e-113">The case identifiers are names for the various possible types of values that objects of this type could be; the values are optional.</span></span> <span data-ttu-id="3f44e-114">Değerler mevcut değilse, bir numaralandırma durumu eşdeğer bir durumdur.</span><span class="sxs-lookup"><span data-stu-id="3f44e-114">If values are not present, the case is equivalent to an enumeration case.</span></span> <span data-ttu-id="3f44e-115">Değerleri varsa, her değer ya da belirtilen bir tür ya da aynı veya farklı türdeki birden çok alan toplayan bir tanımlama grubu tek bir değer olabilir.</span><span class="sxs-lookup"><span data-stu-id="3f44e-115">If values are present, each value can either be a single value of a specified type, or a tuple that aggregates multiple fields of the same or different types.</span></span> <span data-ttu-id="3f44e-116">F # 3.1, itibariyle tek bir alanı bir ad verin, ancak diğer alanlar aynı durumda adlı olsa bile isteğe bağlı adıdır.</span><span class="sxs-lookup"><span data-stu-id="3f44e-116">As of F# 3.1, you can give an individual field a name, but the name is optional, even if other fields in the same case are named.</span></span>

<span data-ttu-id="3f44e-117">Örneğin, bir şekil türü aşağıdaki bildirimi göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="3f44e-117">For example, consider the following declaration of a Shape type.</span></span>

```fsharp
type Shape =
    | Rectangle of width : float * length : float
    | Circle of radius : float
    | Prism of width : float * float * height : float
```

<span data-ttu-id="3f44e-118">Önceki kod ayrılmış birleşim herhangi üç durumda değerlere sahip olabilir şekli bildirir: dikdörtgen, daire ve Prizma.</span><span class="sxs-lookup"><span data-stu-id="3f44e-118">The preceding code declares a discriminated union Shape, which can have values of any of three cases: Rectangle, Circle, and Prism.</span></span> <span data-ttu-id="3f44e-119">Her durumda, farklı bir alan kümesi vardır.</span><span class="sxs-lookup"><span data-stu-id="3f44e-119">Each case has a different set of fields.</span></span> <span data-ttu-id="3f44e-120">Durumda olması adlı iki dikdörtgen alanları, her iki tür `float`, adları genişlik ve uzunluk sahip.</span><span class="sxs-lookup"><span data-stu-id="3f44e-120">The Rectangle case has two named fields, both of type `float`, that have the names width and length.</span></span> <span data-ttu-id="3f44e-121">Yalnızca bir adlandırılmış alan daire durumda olması RADIUS.</span><span class="sxs-lookup"><span data-stu-id="3f44e-121">The Circle case has just one named field, radius.</span></span> <span data-ttu-id="3f44e-122">Üç alanları Prizma durumu olan alanları adlı iki hangi (genişlik ve yükseklik).</span><span class="sxs-lookup"><span data-stu-id="3f44e-122">The Prism case has three fields, two of which (width and height) are named fields.</span></span> <span data-ttu-id="3f44e-123">Adlandırılmamış alanları anonim alanlar olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="3f44e-123">Unnamed fields are referred to as anonymous fields.</span></span>

<span data-ttu-id="3f44e-124">Aşağıdaki örnekler göre adlandırılmış ve anonim alanların değerlerini sağlayarak nesneleri oluşturur.</span><span class="sxs-lookup"><span data-stu-id="3f44e-124">You construct objects by providing values for the named and anonymous fields according to the following examples.</span></span>

```fsharp
let rect = Rectangle(length = 1.3, width = 10.0)
let circ = Circle (1.0)
let prism = Prism(5., 2.0, height = 3.0)
```

<span data-ttu-id="3f44e-125">Bu kod başlatma adlandırılmış alanları ya da kullanabilirsiniz, veya sırasını bildiriminde alanlarının kullanır ve yalnızca değerleri için her bir alan sırayla belirtin gösterir.</span><span class="sxs-lookup"><span data-stu-id="3f44e-125">This code shows that you can either use the named fields in the initialization, or you can rely on the ordering of the fields in the declaration and just provide the values for each field in turn.</span></span> <span data-ttu-id="3f44e-126">İçin oluşturucu çağrısı `rect` önceki kodda adlandırılmış alanlar, ancak Oluşturucusu çağrısı için kullandığı `circ` sıralama kullanır.</span><span class="sxs-lookup"><span data-stu-id="3f44e-126">The constructor call for `rect` in the previous code uses the named fields, but the constructor call for `circ` uses the ordering.</span></span> <span data-ttu-id="3f44e-127">Sıralı alanları karıştırabilirsiniz ve yapımı olduğu gibi alanları adlı `prism`.</span><span class="sxs-lookup"><span data-stu-id="3f44e-127">You can mix the ordered fields and named fields, as in the construction of `prism`.</span></span>

<span data-ttu-id="3f44e-128">`option` Basit bir ayrılmış birleşim F # core kitaplık içinde türüdür.</span><span class="sxs-lookup"><span data-stu-id="3f44e-128">The `option` type is a simple discriminated union in the F# core library.</span></span> <span data-ttu-id="3f44e-129">`option` Türü gibi bildirilmedi.</span><span class="sxs-lookup"><span data-stu-id="3f44e-129">The `option` type is declared as follows.</span></span>

```fsharp
// The option type is a discriminated union.
type Option<'a> =
    | Some of 'a
    | None
```

<span data-ttu-id="3f44e-130">Önceki kod belirleyen türü `Option` iki durumda sahip ayrılmış bir birleşimdir `Some` ve `None`.</span><span class="sxs-lookup"><span data-stu-id="3f44e-130">The previous code specifies that the type `Option` is a discriminated union that has two cases, `Some` and `None`.</span></span> <span data-ttu-id="3f44e-131">`Some` Durumu, türü tür parametresi tarafından gösterilen bir anonim alanından oluşur ilişkili bir değere sahip `'a`.</span><span class="sxs-lookup"><span data-stu-id="3f44e-131">The `Some` case has an associated value that consists of one anonymous field whose type is represented by the type parameter `'a`.</span></span> <span data-ttu-id="3f44e-132">`None` Durumda olması ilişkili değer.</span><span class="sxs-lookup"><span data-stu-id="3f44e-132">The `None` case has no associated value.</span></span> <span data-ttu-id="3f44e-133">Bu nedenle `option` ya da bazı türü veya herhangi bir değer değerine sahip genel bir tür türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="3f44e-133">Thus the `option` type specifies a generic type that either has a value of some type or no value.</span></span> <span data-ttu-id="3f44e-134">Türü `Option` ayrıca bir küçük harf türü diğer adı olan `option`, yani daha sık kullanılan.</span><span class="sxs-lookup"><span data-stu-id="3f44e-134">The type `Option` also has a lowercase type alias, `option`, that is more commonly used.</span></span>

<span data-ttu-id="3f44e-135">Servis talebi tanımlayıcıları oluşturucular ayrılmış birleşim türü için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="3f44e-135">The case identifiers can be used as constructors for the discriminated union type.</span></span> <span data-ttu-id="3f44e-136">Örneğin, aşağıdaki kod değerlerini oluşturmak için kullanılan `option` türü.</span><span class="sxs-lookup"><span data-stu-id="3f44e-136">For example, the following code is used to create values of the `option` type.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2001.fs)]

<span data-ttu-id="3f44e-137">Servis talebi tanımlayıcıları da eşleşen modelinde kullanılır.</span><span class="sxs-lookup"><span data-stu-id="3f44e-137">The case identifiers are also used in pattern matching expressions.</span></span> <span data-ttu-id="3f44e-138">İfade ile eşleşen bir deseni tanımlayıcıları tek tek durumları ile ilişkili değerleri için sağlanır.</span><span class="sxs-lookup"><span data-stu-id="3f44e-138">In a pattern matching expression, identifiers are provided for the values associated with the individual cases.</span></span> <span data-ttu-id="3f44e-139">Örneğin, aşağıdaki kodda, `x` tanımlayıcısı ile ilişkili değer verilen `Some` durumu `option` türü.</span><span class="sxs-lookup"><span data-stu-id="3f44e-139">For example, in the following code, `x` is the identifier given the value that is associated with the `Some` case of the `option` type.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2002.fs)]

<span data-ttu-id="3f44e-140">Eşleşen desende adlandırılmış alanlar ayrılmış birleşim eşleşmeleri belirtmek için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3f44e-140">In pattern matching expressions, you can use named fields to specify discriminated union matches.</span></span> <span data-ttu-id="3f44e-141">Alanların değerlerini ayıklamak için aşağıdaki kodda gösterildiği gibi daha önce bildirildi Şekil türü için adlandırılmış alanlar kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3f44e-141">For the Shape type that was declared previously, you can use the named fields as the following code shows to extract the values of the fields.</span></span>

```fsharp
let getShapeHeight shape =
    match shape with
    | Rectangle(height = h) -> h
    | Circle(radius = r) -> 2. * r
    | Prism(height = h) -> h
```

<span data-ttu-id="3f44e-142">Normalde, servis talebi tanımlayıcıları UNION adıyla niteleme olmadan kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="3f44e-142">Normally, the case identifiers can be used without qualifying them with the name of the union.</span></span> <span data-ttu-id="3f44e-143">Her zaman UNION adıyla nitelendirilmesi adı istiyorsanız uygulayabilirsiniz [RequireQualifiedAccess](https://msdn.microsoft.com/library/8b9b6ade-0471-4413-ac5d-638cd0de5f15) özniteliğin birleşim türü tanımı.</span><span class="sxs-lookup"><span data-stu-id="3f44e-143">If you want the name to always be qualified with the name of the union, you can apply the [RequireQualifiedAccess](https://msdn.microsoft.com/library/8b9b6ade-0471-4413-ac5d-638cd0de5f15) attribute to the union type definition.</span></span>

### <a name="unwrapping-discriminated-unions"></a><span data-ttu-id="3f44e-144">Açma ayrılmış birleşimler</span><span class="sxs-lookup"><span data-stu-id="3f44e-144">Unwrapping Discriminated Unions</span></span>

<span data-ttu-id="3f44e-145">F # ayrılmış birleşimler genellikle etki alanı-modelleme tek bir türü kaydırma için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="3f44e-145">In F# Discriminated Unions are often used in domain-modeling for wrapping a single type.</span></span> <span data-ttu-id="3f44e-146">Desen eşleştirme de aracılığıyla alttaki değerini ayıklayın kolaydır.</span><span class="sxs-lookup"><span data-stu-id="3f44e-146">It's easy to extract the underlying value via pattern matching as well.</span></span> <span data-ttu-id="3f44e-147">Bir eşleşme ifadesi için tek bir kasada kullanmanız gerekmez:</span><span class="sxs-lookup"><span data-stu-id="3f44e-147">You don't need to use a match expression for a single case:</span></span>
```fsharp
let ([UnionCaseName] [values]) = [UnionValue]
```

<span data-ttu-id="3f44e-148">Aşağıdaki örnekte bu gösterir:</span><span class="sxs-lookup"><span data-stu-id="3f44e-148">The following example demonstrates this:</span></span>

```fsharp
type ShaderProgram = | ShaderProgram of id:int

let someMethodUsingShaderProgram shaderProgram =
    let (ShaderProgram id) = shaderProgram
    // Use the unwrapped value
    ..
```

## <a name="struct-discriminated-unions"></a><span data-ttu-id="3f44e-149">Yapı birleşimler</span><span class="sxs-lookup"><span data-stu-id="3f44e-149">Struct Discriminated Unions</span></span>

<span data-ttu-id="3f44e-150">F # 4.1 ile başlayarak, ayrılmış birleşimler yapılar da gösterebilir.</span><span class="sxs-lookup"><span data-stu-id="3f44e-150">Starting with F# 4.1, you can also represent Discriminated Unions as structs.</span></span>  <span data-ttu-id="3f44e-151">Bu gerçekleştirilir `[<Struct>]` özniteliği.</span><span class="sxs-lookup"><span data-stu-id="3f44e-151">This is done with the `[<Struct>]` attribute.</span></span>

```fsharp
[<Struct>]
type SingleCase = Case of string

[<Struct>]
type Multicase =
    | Case1 of Case1 : string
    | Case2 of Case2 : int
    | Case3 of Case3 : double
```

<span data-ttu-id="3f44e-152">Bu değer türleri ve başvuru türlerini değil çünkü vardır ek başvuru ile karşılaştırıldığında konuları ayrılmış birleşimler:</span><span class="sxs-lookup"><span data-stu-id="3f44e-152">Because these are value types and not reference types, there are extra considerations compared with reference discriminated unions:</span></span>

1. <span data-ttu-id="3f44e-153">Bunlar, değer türleri kopyalanır ve değer türü anlamları vardır.</span><span class="sxs-lookup"><span data-stu-id="3f44e-153">They are copied as value types and have value type semantics.</span></span>
2. <span data-ttu-id="3f44e-154">Bir özyinelemeli tür tanımı multicase yapı Discriminated birleşimi ile kullanamazsınız.</span><span class="sxs-lookup"><span data-stu-id="3f44e-154">You cannot use a recursive type definition with a multicase struct Discriminated Union.</span></span>
3. <span data-ttu-id="3f44e-155">Multicase yapı Discriminated birleşimi benzersiz servis talebi adlar sağlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="3f44e-155">You must provide unique case names for a multicase struct Discriminated Union.</span></span>

## <a name="using-discriminated-unions-instead-of-object-hierarchies"></a><span data-ttu-id="3f44e-156">Ayrılmış birleşimler yerine nesne hiyerarşileri kullanma</span><span class="sxs-lookup"><span data-stu-id="3f44e-156">Using Discriminated Unions Instead of Object Hierarchies</span></span>
<span data-ttu-id="3f44e-157">Küçük nesne hiyerarşisi daha basit bir alternatif olarak, ayrılmış bir birleşim genellikle kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3f44e-157">You can often use a discriminated union as a simpler alternative to a small object hierarchy.</span></span> <span data-ttu-id="3f44e-158">Örneğin, aşağıdaki ayrılmış birleşim yerine kullanılabilecek bir `Shape` temel daire, türlerinde türetilmiş kare, vb. sınıfı.</span><span class="sxs-lookup"><span data-stu-id="3f44e-158">For example, the following discriminated union could be used instead of a `Shape` base class that has derived types for circle, square, and so on.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2003.fs)]

<span data-ttu-id="3f44e-159">Bunun yerine bir alanı veya çevre hesaplamak için sanal yöntemi gibi nesne yönelimli uygulama kullanır, bu miktarlar işlem için uygun formüller dala eşleşen kalıbı kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3f44e-159">Instead of a virtual method to compute an area or perimeter, as you would use in an object-oriented implementation, you can use pattern matching to branch to appropriate formulas to compute these quantities.</span></span> <span data-ttu-id="3f44e-160">Aşağıdaki örnekte, farklı formüller şekli bağlı olarak alan hesaplamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="3f44e-160">In the following example, different formulas are used to compute the area, depending on the shape.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2004.fs)]

<span data-ttu-id="3f44e-161">Çıktı aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="3f44e-161">The output is as follows:</span></span>

```
Area of circle that has radius 15.000000: 706.858347
Area of square that has side 10.000000: 100.000000
Area of rectangle that has height 5.000000 and width 10.000000 is 50.000000
```

## <a name="using-discriminated-unions-for-tree-data-structures"></a><span data-ttu-id="3f44e-162">Ayrılmış birleşimler ağaç veri yapıları için kullanma</span><span class="sxs-lookup"><span data-stu-id="3f44e-162">Using Discriminated Unions for Tree Data Structures</span></span>
<span data-ttu-id="3f44e-163">Ayrılmış birleşimler birleşim türünde bir veya daha fazla örneklerinin eklenebilir anlamı özyinelemeli olabilir.</span><span class="sxs-lookup"><span data-stu-id="3f44e-163">Discriminated unions can be recursive, meaning that the union itself can be included in the type of one or more cases.</span></span> <span data-ttu-id="3f44e-164">Özyinelemeli ayrılmış birleşimler programlama dilleri, model ifadeleri için kullanılan ağaç yapıları oluşturmak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="3f44e-164">Recursive discriminated unions can be used to create tree structures, which are used to model expressions in programming languages.</span></span> <span data-ttu-id="3f44e-165">Aşağıdaki kodda bir özyinelemeli ayrılmış birleşim bir ikili ağacı veri yapısı oluşturmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="3f44e-165">In the following code, a recursive discriminated union is used to create a binary tree data structure.</span></span> <span data-ttu-id="3f44e-166">İki örneklerini UNION oluşur `Node`, bir tamsayı değeri ve sol ve sağ alt ağaçta, bir düğümü olduğu ve `Tip`, ağaç sonlandırır.</span><span class="sxs-lookup"><span data-stu-id="3f44e-166">The union consists of two cases, `Node`, which is a node with an integer value and left and right subtrees, and `Tip`, which terminates the tree.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2005.fs)]

<span data-ttu-id="3f44e-167">Önceki kod `resultSumTree` 10 değerine sahiptir.</span><span class="sxs-lookup"><span data-stu-id="3f44e-167">In the previous code, `resultSumTree` has the value 10.</span></span> <span data-ttu-id="3f44e-168">Aşağıdaki çizim için ağaç yapısını gösterir `myTree`.</span><span class="sxs-lookup"><span data-stu-id="3f44e-168">The following illustration shows the tree structure for `myTree`.</span></span>

![MyTree için ağaç yapısı](../media/TreeStructureDiagram.png)

<span data-ttu-id="3f44e-170">Ayrılmış birleşimler ağacında düğümlerin heterojen iyi çalışır.</span><span class="sxs-lookup"><span data-stu-id="3f44e-170">Discriminated unions work well if the nodes in the tree are heterogeneous.</span></span> <span data-ttu-id="3f44e-171">Aşağıdaki kodda, türü `Expression` eklenmesini destekler basit bir programlama dili ifade soyut söz dizimi ağaç ve çarpma numaraları ve değişkenlerin temsil eder.</span><span class="sxs-lookup"><span data-stu-id="3f44e-171">In the following code, the type `Expression` represents the abstract syntax tree of an expression in a simple programming language that supports addition and multiplication of numbers and variables.</span></span> <span data-ttu-id="3f44e-172">Birleşim durumları bazıları özyinelemeli olmayan ve her iki sayılar temsil eder (`Number`) veya değişkenleri (`Variable`).</span><span class="sxs-lookup"><span data-stu-id="3f44e-172">Some of the union cases are not recursive and represent either numbers (`Number`) or variables (`Variable`).</span></span> <span data-ttu-id="3f44e-173">Diğer durumlarda özyinelemeli ve işlemleri temsil eder (`Add` ve `Multiply`), işlenen ifadeler de nerede.</span><span class="sxs-lookup"><span data-stu-id="3f44e-173">Other cases are recursive, and represent operations (`Add` and `Multiply`), where the operands are also expressions.</span></span> <span data-ttu-id="3f44e-174">`Evaluate` İşlevi bir eşleşme ifadesi özyinelemeli olarak işlem sözdizimi ağacı için kullanır.</span><span class="sxs-lookup"><span data-stu-id="3f44e-174">The `Evaluate` function uses a match expression to recursively process the syntax tree.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2006.fs)]

<span data-ttu-id="3f44e-175">Bu kod, ne zaman yürütülür, değeri `result` 5'tir.</span><span class="sxs-lookup"><span data-stu-id="3f44e-175">When this code is executed, the value of `result` is 5.</span></span>

## <a name="common-attributes"></a><span data-ttu-id="3f44e-176">Ortak Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="3f44e-176">Common Attributes</span></span>

<span data-ttu-id="3f44e-177">Aşağıdaki öznitelikler içinde ayrılmış birleşimler sık görülür:</span><span class="sxs-lookup"><span data-stu-id="3f44e-177">The following attributes are commonly seen in discriminated unions:</span></span>

* `[RequireQualifiedAccess]`
* `[NoEquality]`
* `[NoComparison]`
* <span data-ttu-id="3f44e-178">`[Struct]`(F # 4.1 ve üzeri)</span><span class="sxs-lookup"><span data-stu-id="3f44e-178">`[Struct]` (F# 4.1 and higher)</span></span>

## <a name="see-also"></a><span data-ttu-id="3f44e-179">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="3f44e-179">See Also</span></span>
[<span data-ttu-id="3f44e-180">F# Dili Başvurusu</span><span class="sxs-lookup"><span data-stu-id="3f44e-180">F# Language Reference</span></span>](index.md)
