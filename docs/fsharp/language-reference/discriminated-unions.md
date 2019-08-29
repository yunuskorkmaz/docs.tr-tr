---
title: Ayrılmış Birleşimler
description: Ayırt edici birleşimler kullanmayı F# öğrenin.
ms.date: 05/16/2016
ms.openlocfilehash: fa4f011a8d5fd6725a44e030b423e79244a18734
ms.sourcegitcommit: 6f28b709592503d27077b16fff2e2eacca569992
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/28/2019
ms.locfileid: "70106765"
---
# <a name="discriminated-unions"></a><span data-ttu-id="c2fd9-103">Ayrılmış Birleşimler</span><span class="sxs-lookup"><span data-stu-id="c2fd9-103">Discriminated Unions</span></span>

<span data-ttu-id="c2fd9-104">Ayırt edici birleşimler, büyük olasılıkla her biri farklı değer ve türlere sahip olabilecek bir dizi adlandırılmış durum olabilen değerler için destek sağlar.</span><span class="sxs-lookup"><span data-stu-id="c2fd9-104">Discriminated unions provide support for values that can be one of a number of named cases, possibly each with different values and types.</span></span> <span data-ttu-id="c2fd9-105">Ayırt edici birleşimler heterojen veriler için yararlıdır; geçerli ve hata durumları dahil olmak üzere özel durumları olan veriler; tür olarak bir örnekten diğerine değişen veriler; küçük nesne hiyerarşileri için alternatif olarak.</span><span class="sxs-lookup"><span data-stu-id="c2fd9-105">Discriminated unions are useful for heterogeneous data; data that can have special cases, including valid and error cases; data that varies in type from one instance to another; and as an alternative for small object hierarchies.</span></span> <span data-ttu-id="c2fd9-106">Ayrıca, yinelemeli ayırt edici birleşimler ağaç veri yapılarını temsil etmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="c2fd9-106">In addition, recursive discriminated unions are used to represent tree data structures.</span></span>

## <a name="syntax"></a><span data-ttu-id="c2fd9-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c2fd9-107">Syntax</span></span>

```fsharp
[ attributes ]
type [accessibility-modifier] type-name =
    | case-identifier1 [of [ fieldname1 : ] type1 [ * [ fieldname2 : ] type2 ...]
    | case-identifier2 [of [fieldname3 : ]type3 [ * [ fieldname4 : ]type4 ...]

    [ member-list ]
```

## <a name="remarks"></a><span data-ttu-id="c2fd9-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c2fd9-108">Remarks</span></span>

<span data-ttu-id="c2fd9-109">Ayırt edici birleşimler diğer dillerdeki birleşim türlerine benzerdir, ancak farklılık vardır.</span><span class="sxs-lookup"><span data-stu-id="c2fd9-109">Discriminated unions are similar to union types in other languages, but there are differences.</span></span> <span data-ttu-id="c2fd9-110">İçindeki C++ bir birleşim türü veya Visual Basic değişken türünde olduğu gibi, değerde depolanan veriler düzeltilmez; Bu çeşitli seçeneklerden biri olabilir.</span><span class="sxs-lookup"><span data-stu-id="c2fd9-110">As with a union type in C++ or a variant type in Visual Basic, the data stored in the value is not fixed; it can be one of several distinct options.</span></span> <span data-ttu-id="c2fd9-111">Ancak, bu diğer dillerdeki birleşimlerin aksine, olası seçeneklerin her birine bir *Case tanımlayıcısı*verilir.</span><span class="sxs-lookup"><span data-stu-id="c2fd9-111">Unlike unions in these other languages, however, each of the possible options is given a *case identifier*.</span></span> <span data-ttu-id="c2fd9-112">Büyük/küçük harf tanımlayıcıları, bu türdeki nesnelerin olabilecek çeşitli olası değer türlerinin adlarıdır; değerler isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="c2fd9-112">The case identifiers are names for the various possible types of values that objects of this type could be; the values are optional.</span></span> <span data-ttu-id="c2fd9-113">Değerler yoksa, büyük/küçük harf bir numaralandırma durumuna eşdeğerdir.</span><span class="sxs-lookup"><span data-stu-id="c2fd9-113">If values are not present, the case is equivalent to an enumeration case.</span></span> <span data-ttu-id="c2fd9-114">Değerler mevcutsa, her değer belirtilen türde tek bir değer veya aynı ya da farklı türlerin birden fazla alanını toplayan bir tanımlama grubu olabilir.</span><span class="sxs-lookup"><span data-stu-id="c2fd9-114">If values are present, each value can either be a single value of a specified type, or a tuple that aggregates multiple fields of the same or different types.</span></span> <span data-ttu-id="c2fd9-115">Tek bir alana bir ad verebilirsiniz, ancak aynı durumda diğer alanlar adlandırılmış olsa bile ad isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="c2fd9-115">You can give an individual field a name, but the name is optional, even if other fields in the same case are named.</span></span>

<span data-ttu-id="c2fd9-116">Ayırt edici birleşimler için erişilebilirlik varsayılan olarak `public`' dir.</span><span class="sxs-lookup"><span data-stu-id="c2fd9-116">Accessibility for discriminated unions defaults to `public`.</span></span>

<span data-ttu-id="c2fd9-117">Örneğin, bir şekil türünün Aşağıdaki bildirimini göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="c2fd9-117">For example, consider the following declaration of a Shape type.</span></span>

```fsharp
type Shape =
    | Rectangle of width : float * length : float
    | Circle of radius : float
    | Prism of width : float * float * height : float
```

<span data-ttu-id="c2fd9-118">Yukarıdaki kod, ayırt edici bir birleşim şekli bildirir ve bu üç durumda herhangi bir değer içerebilir: Dikdörtgen, daire ve Prizm.</span><span class="sxs-lookup"><span data-stu-id="c2fd9-118">The preceding code declares a discriminated union Shape, which can have values of any of three cases: Rectangle, Circle, and Prism.</span></span> <span data-ttu-id="c2fd9-119">Her durumda farklı bir alan kümesi vardır.</span><span class="sxs-lookup"><span data-stu-id="c2fd9-119">Each case has a different set of fields.</span></span> <span data-ttu-id="c2fd9-120">Dikdörtgen durumunun genişliği ve uzunluğu olan iki tür `float`alanı vardır.</span><span class="sxs-lookup"><span data-stu-id="c2fd9-120">The Rectangle case has two named fields, both of type `float`, that have the names width and length.</span></span> <span data-ttu-id="c2fd9-121">Daire durumunun yalnızca bir tane adlandırılmış alanı Radius vardır.</span><span class="sxs-lookup"><span data-stu-id="c2fd9-121">The Circle case has just one named field, radius.</span></span> <span data-ttu-id="c2fd9-122">Prronizme durumu üç alana sahiptir, ikisi de (genişlik ve yükseklik) olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="c2fd9-122">The Prism case has three fields, two of which (width and height) are named fields.</span></span> <span data-ttu-id="c2fd9-123">Adlandırılmamış alanlara anonim alanlar denir.</span><span class="sxs-lookup"><span data-stu-id="c2fd9-123">Unnamed fields are referred to as anonymous fields.</span></span>

<span data-ttu-id="c2fd9-124">Aşağıdaki örneklere göre adlandırılmış ve anonim alanlar için değerler sağlayarak nesneler oluşturursunuz.</span><span class="sxs-lookup"><span data-stu-id="c2fd9-124">You construct objects by providing values for the named and anonymous fields according to the following examples.</span></span>

```fsharp
let rect = Rectangle(length = 1.3, width = 10.0)
let circ = Circle (1.0)
let prism = Prism(5., 2.0, height = 3.0)
```

<span data-ttu-id="c2fd9-125">Bu kod, başlatma içindeki adlandırılmış alanları kullanabilir ya da bildirimdeki alanların sıralamasını temel alabilir ve yalnızca her bir alan için değerleri de sağlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c2fd9-125">This code shows that you can either use the named fields in the initialization, or you can rely on the ordering of the fields in the declaration and just provide the values for each field in turn.</span></span> <span data-ttu-id="c2fd9-126">Önceki kodda için `rect` Oluşturucu çağrısı, adlandırılmış alanları kullanır, ancak için `circ` Oluşturucu çağrısı sıralamayı kullanır.</span><span class="sxs-lookup"><span data-stu-id="c2fd9-126">The constructor call for `rect` in the previous code uses the named fields, but the constructor call for `circ` uses the ordering.</span></span> <span data-ttu-id="c2fd9-127">İçinde olduğu gibi sıralı alanları ve adlandırılmış alanları karıştırabilirsiniz `prism`.</span><span class="sxs-lookup"><span data-stu-id="c2fd9-127">You can mix the ordered fields and named fields, as in the construction of `prism`.</span></span>

<span data-ttu-id="c2fd9-128">Tür, F# çekirdek kitaplığındaki basit bir ayırt edici birleşimdir. `option`</span><span class="sxs-lookup"><span data-stu-id="c2fd9-128">The `option` type is a simple discriminated union in the F# core library.</span></span> <span data-ttu-id="c2fd9-129">`option` Tür aşağıdaki şekilde bildirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="c2fd9-129">The `option` type is declared as follows.</span></span>

```fsharp
// The option type is a discriminated union.
type Option<'a> =
    | Some of 'a
    | None
```

<span data-ttu-id="c2fd9-130">Önceki kod, türün `Option` iki `Some` durum ve ile `None`ayırt edici bir bileşim olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="c2fd9-130">The previous code specifies that the type `Option` is a discriminated union that has two cases, `Some` and `None`.</span></span> <span data-ttu-id="c2fd9-131">Örnekte, türü tür parametresiyle `'a`temsil edilen bir anonim alandan oluşan ilişkili bir değer vardır. `Some`</span><span class="sxs-lookup"><span data-stu-id="c2fd9-131">The `Some` case has an associated value that consists of one anonymous field whose type is represented by the type parameter `'a`.</span></span> <span data-ttu-id="c2fd9-132">`None` Büyük/küçük harf ilişkili bir değere sahip değil.</span><span class="sxs-lookup"><span data-stu-id="c2fd9-132">The `None` case has no associated value.</span></span> <span data-ttu-id="c2fd9-133">Bu nedenle `option` tür, bir tür değeri veya değeri olmayan bir genel türü belirtir.</span><span class="sxs-lookup"><span data-stu-id="c2fd9-133">Thus the `option` type specifies a generic type that either has a value of some type or no value.</span></span> <span data-ttu-id="c2fd9-134">Türün `Option` Ayrıca, daha yaygın olarak kullanılan küçük harfli `option`bir tür diğer adı vardır.</span><span class="sxs-lookup"><span data-stu-id="c2fd9-134">The type `Option` also has a lowercase type alias, `option`, that is more commonly used.</span></span>

<span data-ttu-id="c2fd9-135">Büyük/küçük harf tanımlayıcıları, ayırt edici birleşim türü için oluşturucular olarak kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="c2fd9-135">The case identifiers can be used as constructors for the discriminated union type.</span></span> <span data-ttu-id="c2fd9-136">Örneğin, aşağıdaki kod, `option` türünün değerlerini oluşturmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="c2fd9-136">For example, the following code is used to create values of the `option` type.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2001.fs)]

<span data-ttu-id="c2fd9-137">Büyük/küçük harf tanımlayıcıları aynı zamanda desenler eşleştirme ifadelerinde de kullanılır.</span><span class="sxs-lookup"><span data-stu-id="c2fd9-137">The case identifiers are also used in pattern matching expressions.</span></span> <span data-ttu-id="c2fd9-138">Bir model eşleştirme ifadesinde, tanımlayıcılar, bireysel durumlar ile ilişkili değerler için sağlanır.</span><span class="sxs-lookup"><span data-stu-id="c2fd9-138">In a pattern matching expression, identifiers are provided for the values associated with the individual cases.</span></span> <span data-ttu-id="c2fd9-139">Örneğin, aşağıdaki kodda, `x` `option` tür `Some` durumuyla ilişkili değer verilen tanıtıcıdır.</span><span class="sxs-lookup"><span data-stu-id="c2fd9-139">For example, in the following code, `x` is the identifier given the value that is associated with the `Some` case of the `option` type.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2002.fs)]

<span data-ttu-id="c2fd9-140">Desenler eşleştirme ifadelerinde, ayırt edici birleşim eşleşmelerini belirtmek için adlandırılmış alanları kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c2fd9-140">In pattern matching expressions, you can use named fields to specify discriminated union matches.</span></span> <span data-ttu-id="c2fd9-141">Daha önce tanımlanan şekil türü için, alanların değerlerini ayıklamak üzere aşağıdaki kodda gösterildiği gibi, adlandırılmış alanları kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c2fd9-141">For the Shape type that was declared previously, you can use the named fields as the following code shows to extract the values of the fields.</span></span>

```fsharp
let getShapeHeight shape =
    match shape with
    | Rectangle(height = h) -> h
    | Circle(radius = r) -> 2. * r
    | Prism(height = h) -> h
```

<span data-ttu-id="c2fd9-142">Genellikle, büyük/küçük harf tanımlayıcıları birleşim adıyla nitelemeden kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="c2fd9-142">Normally, the case identifiers can be used without qualifying them with the name of the union.</span></span> <span data-ttu-id="c2fd9-143">Adın her zaman birleşimin adı ile nitelenmiş olmasını istiyorsanız, [RequireQualifiedAccess](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.requirequalifiedaccessattribute-class-[fsharp]) özniteliğini birleşim türü tanımına uygulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c2fd9-143">If you want the name to always be qualified with the name of the union, you can apply the [RequireQualifiedAccess](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.requirequalifiedaccessattribute-class-[fsharp]) attribute to the union type definition.</span></span>

### <a name="unwrapping-discriminated-unions"></a><span data-ttu-id="c2fd9-144">Ayrılmış birleşimler sarmalama</span><span class="sxs-lookup"><span data-stu-id="c2fd9-144">Unwrapping Discriminated Unions</span></span>

<span data-ttu-id="c2fd9-145">F# Ayırt edici birleşimler, genellikle tek bir tür sarmalama için etki alanı modellemesinde kullanılır.</span><span class="sxs-lookup"><span data-stu-id="c2fd9-145">In F# Discriminated Unions are often used in domain-modeling for wrapping a single type.</span></span> <span data-ttu-id="c2fd9-146">Temel alınan değeri, aynı zamanda kalıp eşleştirme aracılığıyla ayıklamak çok kolaydır.</span><span class="sxs-lookup"><span data-stu-id="c2fd9-146">It's easy to extract the underlying value via pattern matching as well.</span></span> <span data-ttu-id="c2fd9-147">Tek bir durum için eşleşme ifadesi kullanmanız gerekmez:</span><span class="sxs-lookup"><span data-stu-id="c2fd9-147">You don't need to use a match expression for a single case:</span></span>

```fsharp
let ([UnionCaseName] [values]) = [UnionValue]
```

<span data-ttu-id="c2fd9-148">Aşağıdaki örnek şunu gösterir:</span><span class="sxs-lookup"><span data-stu-id="c2fd9-148">The following example demonstrates this:</span></span>

```fsharp
type ShaderProgram = | ShaderProgram of id:int

let someFunctionUsingShaderProgram shaderProgram =
    let (ShaderProgram id) = shaderProgram
    // Use the unwrapped value
    ...
```

<span data-ttu-id="c2fd9-149">Ayrıca, doğrudan işlev parametrelerinde de model eşleştirmeye izin verilir, bu nedenle tek bir büyük/küçük harf sarmasını geri alabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="c2fd9-149">Pattern matching is also allowed directly in function parameters, so you can unwrap a single case there:</span></span>

```fsharp
let someFunctionUsingShaderProgram (ShaderProgram id) =
    // Use the unwrapped value
    ...
```

## <a name="struct-discriminated-unions"></a><span data-ttu-id="c2fd9-150">Yapı ayırt edici birleşimler</span><span class="sxs-lookup"><span data-stu-id="c2fd9-150">Struct Discriminated Unions</span></span>

<span data-ttu-id="c2fd9-151">Ayırt edici birleşimleri yapı olarak da temsil edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c2fd9-151">You can also represent Discriminated Unions as structs.</span></span>  <span data-ttu-id="c2fd9-152">Bu, `[<Struct>]` özniteliğiyle yapılır.</span><span class="sxs-lookup"><span data-stu-id="c2fd9-152">This is done with the `[<Struct>]` attribute.</span></span>

```fsharp
[<Struct>]
type SingleCase = Case of string

[<Struct>]
type Multicase =
    | Case1 of Case1 : string
    | Case2 of Case2 : int
    | Case3 of Case3 : double
```

<span data-ttu-id="c2fd9-153">Bunlar değer türleri ve başvuru türleri olduklarından, başvuru ayrılmış birleşimlerle karşılaştırıldığında ek hususlar vardır:</span><span class="sxs-lookup"><span data-stu-id="c2fd9-153">Because these are value types and not reference types, there are extra considerations compared with reference discriminated unions:</span></span>

1. <span data-ttu-id="c2fd9-154">Değer türleri olarak kopyalanırlar ve değer türü semantiği vardır.</span><span class="sxs-lookup"><span data-stu-id="c2fd9-154">They are copied as value types and have value type semantics.</span></span>
2. <span data-ttu-id="c2fd9-155">Bir özyinelemeli tür tanımını, Multicase yapısına ayrılmış birleşim ile kullanamazsınız.</span><span class="sxs-lookup"><span data-stu-id="c2fd9-155">You cannot use a recursive type definition with a multicase struct Discriminated Union.</span></span>
3. <span data-ttu-id="c2fd9-156">Çok büyük harf yapısına ayrılmış bir birleşim için benzersiz bir durum adı sağlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="c2fd9-156">You must provide unique case names for a multicase struct Discriminated Union.</span></span>

## <a name="using-discriminated-unions-instead-of-object-hierarchies"></a><span data-ttu-id="c2fd9-157">Nesne hiyerarşileri yerine ayrılmış birleşimler kullanma</span><span class="sxs-lookup"><span data-stu-id="c2fd9-157">Using Discriminated Unions Instead of Object Hierarchies</span></span>

<span data-ttu-id="c2fd9-158">Ayrılmış bir birleşimi genellikle küçük bir nesne hiyerarşisinin daha basit bir alternatifi olarak kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c2fd9-158">You can often use a discriminated union as a simpler alternative to a small object hierarchy.</span></span> <span data-ttu-id="c2fd9-159">Örneğin, aşağıdaki ayrılmış birleşim, daire, kare ve benzeri türetilmiş türler içeren `Shape` bir temel sınıf yerine kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="c2fd9-159">For example, the following discriminated union could be used instead of a `Shape` base class that has derived types for circle, square, and so on.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2003.fs)]

<span data-ttu-id="c2fd9-160">Bir alanı veya birimi hesaplamak için bir sanal yöntem yerine, nesne odaklı bir uygulamada kullandığınız gibi, bu miktarları hesaplamak için uygun formüllere dalla bir şekilde eşleşen model eşleştirmeyi kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c2fd9-160">Instead of a virtual method to compute an area or perimeter, as you would use in an object-oriented implementation, you can use pattern matching to branch to appropriate formulas to compute these quantities.</span></span> <span data-ttu-id="c2fd9-161">Aşağıdaki örnekte, şekle bağlı olarak alanı hesaplamak için farklı formüller kullanılır.</span><span class="sxs-lookup"><span data-stu-id="c2fd9-161">In the following example, different formulas are used to compute the area, depending on the shape.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2004.fs)]

<span data-ttu-id="c2fd9-162">Çıktı aşağıdaki şekilde olacaktır:</span><span class="sxs-lookup"><span data-stu-id="c2fd9-162">The output is as follows:</span></span>

```
Area of circle that has radius 15.000000: 706.858347
Area of square that has side 10.000000: 100.000000
Area of rectangle that has height 5.000000 and width 10.000000 is 50.000000
```

## <a name="using-discriminated-unions-for-tree-data-structures"></a><span data-ttu-id="c2fd9-163">Ağaç veri yapıları için ayrılmış birleşimler kullanma</span><span class="sxs-lookup"><span data-stu-id="c2fd9-163">Using Discriminated Unions for Tree Data Structures</span></span>

<span data-ttu-id="c2fd9-164">Ayırt edici birleşimler özyinelemeli olabilir; yani birleşim bir veya daha fazla durum türüne dahil edilebilir.</span><span class="sxs-lookup"><span data-stu-id="c2fd9-164">Discriminated unions can be recursive, meaning that the union itself can be included in the type of one or more cases.</span></span> <span data-ttu-id="c2fd9-165">Yinelemeli ayırt edici birleşimler, programlama dillerinde ifadeleri modellemek için kullanılan ağaç yapıları oluşturmak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="c2fd9-165">Recursive discriminated unions can be used to create tree structures, which are used to model expressions in programming languages.</span></span> <span data-ttu-id="c2fd9-166">Aşağıdaki kodda, bir ikili ağaç veri yapısı oluşturmak için özyinelemeli bir ayırt edici birleşim kullanılır.</span><span class="sxs-lookup"><span data-stu-id="c2fd9-166">In the following code, a recursive discriminated union is used to create a binary tree data structure.</span></span> <span data-ttu-id="c2fd9-167">Birleşim, bir tamsayı değeri ve sol `Node`ve sağ alt ağaçlar olan ve `Tip`ağacı sonlandıran bir düğüm olan iki durum oluşur.</span><span class="sxs-lookup"><span data-stu-id="c2fd9-167">The union consists of two cases, `Node`, which is a node with an integer value and left and right subtrees, and `Tip`, which terminates the tree.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2005.fs)]

<span data-ttu-id="c2fd9-168">Önceki kodda `resultSumTree` 10 değerine sahiptir.</span><span class="sxs-lookup"><span data-stu-id="c2fd9-168">In the previous code, `resultSumTree` has the value 10.</span></span> <span data-ttu-id="c2fd9-169">Aşağıdaki çizimde için `myTree`ağaç yapısı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="c2fd9-169">The following illustration shows the tree structure for `myTree`.</span></span>

![MyTree için ağaç yapısını gösteren diyagram.](../media/discriminated-unions/tree-structure-mytree.png)

<span data-ttu-id="c2fd9-171">Ağaç içindeki düğümler heterojen ise, ayırt edici birleşimler iyi çalışır.</span><span class="sxs-lookup"><span data-stu-id="c2fd9-171">Discriminated unions work well if the nodes in the tree are heterogeneous.</span></span> <span data-ttu-id="c2fd9-172">Aşağıdaki kodda, türü `Expression` , sayıların ve değişkenlerin eklenmesini ve çarpimlerini destekleyen basit bir programlama dilinde bir ifadenin soyut sözdizimi ağacını temsil eder.</span><span class="sxs-lookup"><span data-stu-id="c2fd9-172">In the following code, the type `Expression` represents the abstract syntax tree of an expression in a simple programming language that supports addition and multiplication of numbers and variables.</span></span> <span data-ttu-id="c2fd9-173">Birleşim durumlarının bazıları özyinelemeli değildir ve sayılar (`Number`) ya da değişkenler (`Variable`) temsil eder.</span><span class="sxs-lookup"><span data-stu-id="c2fd9-173">Some of the union cases are not recursive and represent either numbers (`Number`) or variables (`Variable`).</span></span> <span data-ttu-id="c2fd9-174">Diğer durumlar özyinelemeli olarak işlenir ve işlenen işlemleri (`Add` ve `Multiply`) temsil eder; burada işlenenler de deyimlerdir.</span><span class="sxs-lookup"><span data-stu-id="c2fd9-174">Other cases are recursive, and represent operations (`Add` and `Multiply`), where the operands are also expressions.</span></span> <span data-ttu-id="c2fd9-175">`Evaluate` İşlevi, sözdizimi ağacını yinelemeli olarak işlemek için bir Match ifadesi kullanır.</span><span class="sxs-lookup"><span data-stu-id="c2fd9-175">The `Evaluate` function uses a match expression to recursively process the syntax tree.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2006.fs)]

<span data-ttu-id="c2fd9-176">Bu kod yürütüldüğünde değeri `result` 5 ' tir.</span><span class="sxs-lookup"><span data-stu-id="c2fd9-176">When this code is executed, the value of `result` is 5.</span></span>

## <a name="members"></a><span data-ttu-id="c2fd9-177">Üyeler</span><span class="sxs-lookup"><span data-stu-id="c2fd9-177">Members</span></span>

<span data-ttu-id="c2fd9-178">Ayrılmış birleşimlerde Üyeler tanımlamak mümkündür.</span><span class="sxs-lookup"><span data-stu-id="c2fd9-178">It is possible to define members on discriminated unions.</span></span> <span data-ttu-id="c2fd9-179">Aşağıdaki örnek, bir özelliğin nasıl tanımlanacağını ve bir arabirimin nasıl uygulanacağını gösterir:</span><span class="sxs-lookup"><span data-stu-id="c2fd9-179">The following example shows how to define a property and implement an interface:</span></span>

```fsharp
open System

type IPrintable =
    abstract Print: unit -> unit

type Shape =
    | Circle of float
    | EquilateralTriangle of float
    | Square of float
    | Rectangle of float * float

    member this.Area =
        match this with
        | Circle r -> 2.0 * Math.PI * r
        | EquilateralTriangle s -> s * s * sqrt 3.0 / 4.0
        | Square s -> s * s
        | Rectangle(l, w) -> l * w

    interface IPrintable with
        member this.Print () =
            match this with
            | Circle r -> printfn "Circle with radius %f" r
            | EquilateralTriangle s -> printfn "Equilateral Triangle of side %f" s
            | Square s -> printfn "Square with side %f" s
            | Rectangle(l, w) -> printfn "Rectangle with length %f and width %f" l w
```

## <a name="common-attributes"></a><span data-ttu-id="c2fd9-180">Ortak öznitelikler</span><span class="sxs-lookup"><span data-stu-id="c2fd9-180">Common attributes</span></span>

<span data-ttu-id="c2fd9-181">Aşağıdaki öznitelikler yaygın olarak ayrılmış birleşimlerde görülür:</span><span class="sxs-lookup"><span data-stu-id="c2fd9-181">The following attributes are commonly seen in discriminated unions:</span></span>

- `[<RequireQualifiedAccess>]`
- `[<NoEquality>]`
- `[<NoComparison>]`
- `[<Struct>]`

## <a name="see-also"></a><span data-ttu-id="c2fd9-182">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c2fd9-182">See also</span></span>

- [<span data-ttu-id="c2fd9-183">F# Dili Başvurusu</span><span class="sxs-lookup"><span data-stu-id="c2fd9-183">F# Language Reference</span></span>](index.md)
