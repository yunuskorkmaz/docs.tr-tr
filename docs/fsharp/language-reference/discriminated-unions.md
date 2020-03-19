---
title: Ayrılmış Birleşimler
description: F# ayrımcı birliş nasıl kullanılacağını öğrenin.
ms.date: 05/16/2016
ms.openlocfilehash: 539e2843c0bbc8c5ac9c0597ffc5443f8cd127f8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79400220"
---
# <a name="discriminated-unions"></a><span data-ttu-id="f1591-103">Ayrılmış Birleşimler</span><span class="sxs-lookup"><span data-stu-id="f1591-103">Discriminated Unions</span></span>

<span data-ttu-id="f1591-104">Ayrımcı sendikalar, her biri farklı değerlere ve türlere sahip, adlandırılmış birkaç servis örneğinden biri olabilecek değerler için destek sağlar.</span><span class="sxs-lookup"><span data-stu-id="f1591-104">Discriminated unions provide support for values that can be one of a number of named cases, possibly each with different values and types.</span></span> <span data-ttu-id="f1591-105">Ayrımcı sendikalar heterojen veriler için yararlıdır; geçerli ve hata durumları da dahil olmak üzere özel durumlara sahip olabilecek veriler; türünde bir örnekten diğerine değişen veriler; ve küçük nesne hiyerarşileri için bir alternatif olarak.</span><span class="sxs-lookup"><span data-stu-id="f1591-105">Discriminated unions are useful for heterogeneous data; data that can have special cases, including valid and error cases; data that varies in type from one instance to another; and as an alternative for small object hierarchies.</span></span> <span data-ttu-id="f1591-106">Buna ek olarak, özyinelemeli ayrımcı sendikalar ağaç veri yapılarını temsil etmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="f1591-106">In addition, recursive discriminated unions are used to represent tree data structures.</span></span>

## <a name="syntax"></a><span data-ttu-id="f1591-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f1591-107">Syntax</span></span>

```fsharp
[ attributes ]
type [accessibility-modifier] type-name =
    | case-identifier1 [of [ fieldname1 : ] type1 [ * [ fieldname2 : ] type2 ...]
    | case-identifier2 [of [fieldname3 : ]type3 [ * [ fieldname4 : ]type4 ...]

    [ member-list ]
```

## <a name="remarks"></a><span data-ttu-id="f1591-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f1591-108">Remarks</span></span>

<span data-ttu-id="f1591-109">Ayrımcı sendikalar diğer dillerdeki birlik türlerine benzer, ancak farklılıklar vardır.</span><span class="sxs-lookup"><span data-stu-id="f1591-109">Discriminated unions are similar to union types in other languages, but there are differences.</span></span> <span data-ttu-id="f1591-110">C++'daki birleşim türünde veya Visual Basic'te bir varyant türünde olduğu gibi, değerde depolanan veriler sabit değildir; birkaç farklı seçenekten biri olabilir.</span><span class="sxs-lookup"><span data-stu-id="f1591-110">As with a union type in C++ or a variant type in Visual Basic, the data stored in the value is not fixed; it can be one of several distinct options.</span></span> <span data-ttu-id="f1591-111">Ancak, bu diğer dillerdeki birlişlerden farklı olarak, olası seçeneklerin her birine bir *servis talebi tanımlayıcısı*verilir.</span><span class="sxs-lookup"><span data-stu-id="f1591-111">Unlike unions in these other languages, however, each of the possible options is given a *case identifier*.</span></span> <span data-ttu-id="f1591-112">Servis talebi tanımlayıcıları, bu tür nesnelerin olabileceği çeşitli olası değer türlerinin adlarıdır; değerler isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="f1591-112">The case identifiers are names for the various possible types of values that objects of this type could be; the values are optional.</span></span> <span data-ttu-id="f1591-113">Değerler yoksa, durum numaralandırma örneğine eşdeğerdir.</span><span class="sxs-lookup"><span data-stu-id="f1591-113">If values are not present, the case is equivalent to an enumeration case.</span></span> <span data-ttu-id="f1591-114">Değerler varsa, her değer belirtilen bir türün tek bir değeri veya aynı veya farklı türdeki birden çok alanı biraraya getiren bir tuple olabilir.</span><span class="sxs-lookup"><span data-stu-id="f1591-114">If values are present, each value can either be a single value of a specified type, or a tuple that aggregates multiple fields of the same or different types.</span></span> <span data-ttu-id="f1591-115">Tek bir alana bir ad verebilirsiniz, ancak aynı durumda diğer alanlar adlandırılmış olsa bile ad isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="f1591-115">You can give an individual field a name, but the name is optional, even if other fields in the same case are named.</span></span>

<span data-ttu-id="f1591-116">Ayrımcı sendikalar için erişilebilirlik `public`varsayılan olarak .</span><span class="sxs-lookup"><span data-stu-id="f1591-116">Accessibility for discriminated unions defaults to `public`.</span></span>

<span data-ttu-id="f1591-117">Örneğin, şekil türünün aşağıdaki bildirimini göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="f1591-117">For example, consider the following declaration of a Shape type.</span></span>

```fsharp
type Shape =
    | Rectangle of width : float * length : float
    | Circle of radius : float
    | Prism of width : float * float * height : float
```

<span data-ttu-id="f1591-118">Önceki kod, dikdörtgen, Daire ve Prizma olmak üzere üç durumdan herhangi birinin değerlerine sahip olabilecek ayrımcı bir birlik Şekli bildirir.</span><span class="sxs-lookup"><span data-stu-id="f1591-118">The preceding code declares a discriminated union Shape, which can have values of any of three cases: Rectangle, Circle, and Prism.</span></span> <span data-ttu-id="f1591-119">Her servis talebinin farklı bir alan kümesi vardır.</span><span class="sxs-lookup"><span data-stu-id="f1591-119">Each case has a different set of fields.</span></span> <span data-ttu-id="f1591-120">Dikdörtgen durumda iki adlandırılmış alanları, her `float`ikisi de türü , adları genişlik ve uzunluk var.</span><span class="sxs-lookup"><span data-stu-id="f1591-120">The Rectangle case has two named fields, both of type `float`, that have the names width and length.</span></span> <span data-ttu-id="f1591-121">Circle davasının sadece bir adı var, yarıçapı.</span><span class="sxs-lookup"><span data-stu-id="f1591-121">The Circle case has just one named field, radius.</span></span> <span data-ttu-id="f1591-122">Prizma durumda iki (genişlik ve yükseklik) alanları adlı üç alan vardır.</span><span class="sxs-lookup"><span data-stu-id="f1591-122">The Prism case has three fields, two of which (width and height) are named fields.</span></span> <span data-ttu-id="f1591-123">Adsız alanlar anonim alanlar olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="f1591-123">Unnamed fields are referred to as anonymous fields.</span></span>

<span data-ttu-id="f1591-124">Aşağıdaki örneklere göre adlandırılmış ve anonim alanlar için değerler sağlayarak nesneleri oluşturmak.</span><span class="sxs-lookup"><span data-stu-id="f1591-124">You construct objects by providing values for the named and anonymous fields according to the following examples.</span></span>

```fsharp
let rect = Rectangle(length = 1.3, width = 10.0)
let circ = Circle (1.0)
let prism = Prism(5., 2.0, height = 3.0)
```

<span data-ttu-id="f1591-125">Bu kod, başlatmada adlandırılmış alanları kullanabileceğinizi veya bildirimdeki alanların sıralanmasına güvenebileceğinizi ve sırayla her alan için değerleri sağlayabileceğinizi gösterir.</span><span class="sxs-lookup"><span data-stu-id="f1591-125">This code shows that you can either use the named fields in the initialization, or you can rely on the ordering of the fields in the declaration and just provide the values for each field in turn.</span></span> <span data-ttu-id="f1591-126">Önceki kodda `rect` kurucu çağrısı adlandırılmış alanları kullanır, ancak kurucu `circ` çağrı sıralama kullanır.</span><span class="sxs-lookup"><span data-stu-id="f1591-126">The constructor call for `rect` in the previous code uses the named fields, but the constructor call for `circ` uses the ordering.</span></span> <span data-ttu-id="f1591-127">Sipariş edilen alanları ve adlandırılmış alanları, inşaatta `prism`olduğu gibi karıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f1591-127">You can mix the ordered fields and named fields, as in the construction of `prism`.</span></span>

<span data-ttu-id="f1591-128">Tür, `option` F# çekirdek kitaplığında basit bir ayrımcı birleşimdir.</span><span class="sxs-lookup"><span data-stu-id="f1591-128">The `option` type is a simple discriminated union in the F# core library.</span></span> <span data-ttu-id="f1591-129">Türü `option` aşağıdaki gibi bildirilir.</span><span class="sxs-lookup"><span data-stu-id="f1591-129">The `option` type is declared as follows.</span></span>

```fsharp
// The option type is a discriminated union.
type Option<'a> =
    | Some of 'a
    | None
```

<span data-ttu-id="f1591-130">Önceki kod, türün `Option` iki servis nedeni olan ayrımlı `Some` bir `None`birleşim olduğunu belirtir ve .</span><span class="sxs-lookup"><span data-stu-id="f1591-130">The previous code specifies that the type `Option` is a discriminated union that has two cases, `Some` and `None`.</span></span> <span data-ttu-id="f1591-131">Servis `Some` talebi, türü tür parametresi `'a`ile temsil edilen anonim bir alandan oluşan ilişkili bir değere sahiptir.</span><span class="sxs-lookup"><span data-stu-id="f1591-131">The `Some` case has an associated value that consists of one anonymous field whose type is represented by the type parameter `'a`.</span></span> <span data-ttu-id="f1591-132">Servis `None` talebinin ilişkili bir değeri yoktur.</span><span class="sxs-lookup"><span data-stu-id="f1591-132">The `None` case has no associated value.</span></span> <span data-ttu-id="f1591-133">Böylece `option` tür, bazı türde bir değere sahip veya değeri olmayan genel bir türü belirtir.</span><span class="sxs-lookup"><span data-stu-id="f1591-133">Thus the `option` type specifies a generic type that either has a value of some type or no value.</span></span> <span data-ttu-id="f1591-134">Türü `Option` de daha yaygın olarak kullanılan `option`bir küçük tür takma vardır.</span><span class="sxs-lookup"><span data-stu-id="f1591-134">The type `Option` also has a lowercase type alias, `option`, that is more commonly used.</span></span>

<span data-ttu-id="f1591-135">Vaka tanımlayıcıları, ayrımcı birlik türü için yapıcı olarak kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="f1591-135">The case identifiers can be used as constructors for the discriminated union type.</span></span> <span data-ttu-id="f1591-136">Örneğin, tür değerlerini `option` oluşturmak için aşağıdaki kod kullanılır.</span><span class="sxs-lookup"><span data-stu-id="f1591-136">For example, the following code is used to create values of the `option` type.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2001.fs)]

<span data-ttu-id="f1591-137">Örnek tanımlayıcılar desen eşleştirme ifadelerinde de kullanılır.</span><span class="sxs-lookup"><span data-stu-id="f1591-137">The case identifiers are also used in pattern matching expressions.</span></span> <span data-ttu-id="f1591-138">Desen eşleştirme ifadesinde, tek tek servis talepleriyle ilişkili değerler için tanımlayıcılar sağlanır.</span><span class="sxs-lookup"><span data-stu-id="f1591-138">In a pattern matching expression, identifiers are provided for the values associated with the individual cases.</span></span> <span data-ttu-id="f1591-139">Örneğin, aşağıdaki kodda, `x` `Some` `option` tür örneği ile ilişkili değer verilen tanımlayıcıdır.</span><span class="sxs-lookup"><span data-stu-id="f1591-139">For example, in the following code, `x` is the identifier given the value that is associated with the `Some` case of the `option` type.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2002.fs)]

<span data-ttu-id="f1591-140">Desen eşleştirme ifadelerinde, ayrımcı birleşim eşleşmelerini belirtmek için adlandırılmış alanları kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f1591-140">In pattern matching expressions, you can use named fields to specify discriminated union matches.</span></span> <span data-ttu-id="f1591-141">Daha önce bildirilen Şekil türü için, alanların değerlerini ayıklamak için aşağıdaki kodun gösterdiği gibi adlandırılmış alanları kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f1591-141">For the Shape type that was declared previously, you can use the named fields as the following code shows to extract the values of the fields.</span></span>

```fsharp
let getShapeWidth shape =
    match shape with
    | Rectangle(width = w) -> w
    | Circle(radius = r) -> 2. * r
    | Prism(width = w) -> w
```

<span data-ttu-id="f1591-142">Normalde, durum tanımlayıcıları sendika adı ile niteleme den önce kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="f1591-142">Normally, the case identifiers can be used without qualifying them with the name of the union.</span></span> <span data-ttu-id="f1591-143">Adın her zaman birliğin adı ile nitelikli olmasını istiyorsanız, Birleşim türü tanımına [RequireQualifiedAccess](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.requirequalifiedaccessattribute-class-[fsharp]) özniteliğini uygulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f1591-143">If you want the name to always be qualified with the name of the union, you can apply the [RequireQualifiedAccess](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.requirequalifiedaccessattribute-class-[fsharp]) attribute to the union type definition.</span></span>

### <a name="unwrapping-discriminated-unions"></a><span data-ttu-id="f1591-144">Ayrımcı Sendikaların Ambalajını Açma</span><span class="sxs-lookup"><span data-stu-id="f1591-144">Unwrapping Discriminated Unions</span></span>

<span data-ttu-id="f1591-145">F# Ayrımcı Sendikalar genellikle tek bir türü sarma için etki alanı modelleme kullanılır.</span><span class="sxs-lookup"><span data-stu-id="f1591-145">In F# Discriminated Unions are often used in domain-modeling for wrapping a single type.</span></span> <span data-ttu-id="f1591-146">Desen eşleştirme yoluyla da temel değeri ayıklamak kolaydır.</span><span class="sxs-lookup"><span data-stu-id="f1591-146">It's easy to extract the underlying value via pattern matching as well.</span></span> <span data-ttu-id="f1591-147">Tek bir servis talebi için eşeşleştirme ifadesi kullanmanız gerekmez:</span><span class="sxs-lookup"><span data-stu-id="f1591-147">You don't need to use a match expression for a single case:</span></span>

```fsharp
let ([UnionCaseIdentifier] [values]) = [UnionValue]
```

<span data-ttu-id="f1591-148">Aşağıdaki örnek bunu göstermektedir:</span><span class="sxs-lookup"><span data-stu-id="f1591-148">The following example demonstrates this:</span></span>

```fsharp
type ShaderProgram = | ShaderProgram of id:int

let someFunctionUsingShaderProgram shaderProgram =
    let (ShaderProgram id) = shaderProgram
    // Use the unwrapped value
    ...
```

<span data-ttu-id="f1591-149">Desen eşleştirmede doğrudan işlev parametrelerine de izin verilir, böylece tek bir servis talebinin paketlemesine orada da izin verebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="f1591-149">Pattern matching is also allowed directly in function parameters, so you can unwrap a single case there:</span></span>

```fsharp
let someFunctionUsingShaderProgram (ShaderProgram id) =
    // Use the unwrapped value
    ...
```

## <a name="struct-discriminated-unions"></a><span data-ttu-id="f1591-150">Struct Ayrımcı Sendikalar</span><span class="sxs-lookup"><span data-stu-id="f1591-150">Struct Discriminated Unions</span></span>

<span data-ttu-id="f1591-151">Ayrıca, Ayrımcı Birliş'leri yapı olarak temsil edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f1591-151">You can also represent Discriminated Unions as structs.</span></span>  <span data-ttu-id="f1591-152">Bu öznitelik `[<Struct>]` ile yapılır.</span><span class="sxs-lookup"><span data-stu-id="f1591-152">This is done with the `[<Struct>]` attribute.</span></span>

```fsharp
[<Struct>]
type SingleCase = Case of string

[<Struct>]
type Multicase =
    | Case1 of Case1 : string
    | Case2 of Case2 : int
    | Case3 of Case3 : double
```

<span data-ttu-id="f1591-153">Bunlar referans türleri değil, değer türleri olduğundan, başvuru ayrımı yapan birbiriyle karşılaştırıldığında ek hususlar vardır:</span><span class="sxs-lookup"><span data-stu-id="f1591-153">Because these are value types and not reference types, there are extra considerations compared with reference discriminated unions:</span></span>

1. <span data-ttu-id="f1591-154">Bunlar değer türleri olarak kopyalanır ve değer türü semantiği vardır.</span><span class="sxs-lookup"><span data-stu-id="f1591-154">They are copied as value types and have value type semantics.</span></span>
2. <span data-ttu-id="f1591-155">Çok harfli yapı lı Ayrımcılık Birliği ile özyinelemeli bir tür tanımı kullanamazsınız.</span><span class="sxs-lookup"><span data-stu-id="f1591-155">You cannot use a recursive type definition with a multicase struct Discriminated Union.</span></span>
3. <span data-ttu-id="f1591-156">Çok harfli yapı Ayrımlı Birlik için benzersiz örnek adları sağlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="f1591-156">You must provide unique case names for a multicase struct Discriminated Union.</span></span>

## <a name="using-discriminated-unions-instead-of-object-hierarchies"></a><span data-ttu-id="f1591-157">Nesne Hiyerarşileri Yerine Ayrımcı Birliş Kullanma</span><span class="sxs-lookup"><span data-stu-id="f1591-157">Using Discriminated Unions Instead of Object Hierarchies</span></span>

<span data-ttu-id="f1591-158">Küçük nesne hiyerarşisine daha basit bir alternatif olarak genellikle ayrımcı bir birleşim kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f1591-158">You can often use a discriminated union as a simpler alternative to a small object hierarchy.</span></span> <span data-ttu-id="f1591-159">Örneğin, daire, kare ve benzeri türleri `Shape` türemiş bir taban sınıf yerine aşağıdaki ayrımcı birleşim kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="f1591-159">For example, the following discriminated union could be used instead of a `Shape` base class that has derived types for circle, square, and so on.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2003.fs)]

<span data-ttu-id="f1591-160">Nesne yönelimli bir uygulamada kullanacağınız gibi, bir alanı veya çevreyi hesaplamak için sanal bir yöntem yerine, bu miktarları hesaplamak için dalla eşleşen deseni uygun formüllerle kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f1591-160">Instead of a virtual method to compute an area or perimeter, as you would use in an object-oriented implementation, you can use pattern matching to branch to appropriate formulas to compute these quantities.</span></span> <span data-ttu-id="f1591-161">Aşağıdaki örnekte, şekle bağlı olarak alanı hesaplamak için farklı formüller kullanılır.</span><span class="sxs-lookup"><span data-stu-id="f1591-161">In the following example, different formulas are used to compute the area, depending on the shape.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2004.fs)]

<span data-ttu-id="f1591-162">Çıktı aşağıdaki şekilde olacaktır:</span><span class="sxs-lookup"><span data-stu-id="f1591-162">The output is as follows:</span></span>

```console
Area of circle that has radius 15.000000: 706.858347
Area of square that has side 10.000000: 100.000000
Area of rectangle that has height 5.000000 and width 10.000000 is 50.000000
```

## <a name="using-discriminated-unions-for-tree-data-structures"></a><span data-ttu-id="f1591-163">Ağaç Veri Yapıları için Ayrımcı Birliş Kullanma</span><span class="sxs-lookup"><span data-stu-id="f1591-163">Using Discriminated Unions for Tree Data Structures</span></span>

<span data-ttu-id="f1591-164">Ayrımcı sendikalar özyinelemeli olabilir, bu da birliğin kendisinin bir veya daha fazla vaka türüne dahil edilebildiği anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="f1591-164">Discriminated unions can be recursive, meaning that the union itself can be included in the type of one or more cases.</span></span> <span data-ttu-id="f1591-165">Özyinelemeli ayrımcı birliş, programlama dillerinde ifadeleri modellemek için kullanılan ağaç yapıları oluşturmak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="f1591-165">Recursive discriminated unions can be used to create tree structures, which are used to model expressions in programming languages.</span></span> <span data-ttu-id="f1591-166">Aşağıdaki kodda, ikili ağaç veri yapısı oluşturmak için özyinelemeli bir ayrımcılık birliği kullanılır.</span><span class="sxs-lookup"><span data-stu-id="f1591-166">In the following code, a recursive discriminated union is used to create a binary tree data structure.</span></span> <span data-ttu-id="f1591-167">Birleşim, `Node`tamsayı değeri ve sol ve sağ alt ağaçları olan bir düğüm `Tip`olan ve ağacı sonlandıran iki durumdan oluşur.</span><span class="sxs-lookup"><span data-stu-id="f1591-167">The union consists of two cases, `Node`, which is a node with an integer value and left and right subtrees, and `Tip`, which terminates the tree.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2005.fs)]

<span data-ttu-id="f1591-168">Önceki kodda `resultSumTree` 10 değeri vardır.</span><span class="sxs-lookup"><span data-stu-id="f1591-168">In the previous code, `resultSumTree` has the value 10.</span></span> <span data-ttu-id="f1591-169">Aşağıdaki resimde ağaç yapısı `myTree`.</span><span class="sxs-lookup"><span data-stu-id="f1591-169">The following illustration shows the tree structure for `myTree`.</span></span>

![myTree için ağaç yapısını gösteren diyagram.](../media/discriminated-unions/tree-structure-mytree.png)

<span data-ttu-id="f1591-171">Ağaçtaki düğümler heterojen sayılsa, ayrımcı sendikalar iyi çalışır.</span><span class="sxs-lookup"><span data-stu-id="f1591-171">Discriminated unions work well if the nodes in the tree are heterogeneous.</span></span> <span data-ttu-id="f1591-172">Aşağıdaki kodda, tür, `Expression` sayıların ve değişkenlerin eklenmesini ve çoğalmasını destekleyen basit bir programlama dilinde bir ifadenin soyut sözdizimi ağacını temsil eder.</span><span class="sxs-lookup"><span data-stu-id="f1591-172">In the following code, the type `Expression` represents the abstract syntax tree of an expression in a simple programming language that supports addition and multiplication of numbers and variables.</span></span> <span data-ttu-id="f1591-173">Bazı birleşim durumları özyinelemeli değildir ve sayılar`Number`( )`Variable`veya değişkenleri ( ) temsil eder.</span><span class="sxs-lookup"><span data-stu-id="f1591-173">Some of the union cases are not recursive and represent either numbers (`Number`) or variables (`Variable`).</span></span> <span data-ttu-id="f1591-174">Diğer durumlarda özyinelemeli ve operands `Multiply`da ifadeler olduğu işlemleri temsil eder.`Add`</span><span class="sxs-lookup"><span data-stu-id="f1591-174">Other cases are recursive, and represent operations (`Add` and `Multiply`), where the operands are also expressions.</span></span> <span data-ttu-id="f1591-175">İşlev `Evaluate` sözdizimi ağacını özyinelemeli olarak işlemek için bir eşleşme ifadesi kullanır.</span><span class="sxs-lookup"><span data-stu-id="f1591-175">The `Evaluate` function uses a match expression to recursively process the syntax tree.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2006.fs)]

<span data-ttu-id="f1591-176">Bu kod yürütüldüğünde, `result` değeri 5'tir.</span><span class="sxs-lookup"><span data-stu-id="f1591-176">When this code is executed, the value of `result` is 5.</span></span>

## <a name="members"></a><span data-ttu-id="f1591-177">Üyeler</span><span class="sxs-lookup"><span data-stu-id="f1591-177">Members</span></span>

<span data-ttu-id="f1591-178">Ayrımcılık yapılan sendikalarda üye tanımlamak mümkündür.</span><span class="sxs-lookup"><span data-stu-id="f1591-178">It is possible to define members on discriminated unions.</span></span> <span data-ttu-id="f1591-179">Aşağıdaki örnek, bir özelliğin nasıl tanımlanacağını ve arabirimi nasıl uygulayacağını gösterir:</span><span class="sxs-lookup"><span data-stu-id="f1591-179">The following example shows how to define a property and implement an interface:</span></span>

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

## <a name="common-attributes"></a><span data-ttu-id="f1591-180">Ortak öznitelikler</span><span class="sxs-lookup"><span data-stu-id="f1591-180">Common attributes</span></span>

<span data-ttu-id="f1591-181">Aşağıdaki öznitelikler genellikle ayrımcı sendikalarda görülür:</span><span class="sxs-lookup"><span data-stu-id="f1591-181">The following attributes are commonly seen in discriminated unions:</span></span>

- `[<RequireQualifiedAccess>]`
- `[<NoEquality>]`
- `[<NoComparison>]`
- `[<Struct>]`

## <a name="see-also"></a><span data-ttu-id="f1591-182">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f1591-182">See also</span></span>

- [<span data-ttu-id="f1591-183">F# Dil Referansı</span><span class="sxs-lookup"><span data-stu-id="f1591-183">F# Language Reference</span></span>](index.md)
