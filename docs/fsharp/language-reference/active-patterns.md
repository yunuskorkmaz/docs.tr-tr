---
title: Etkin Desenler (F#)
description: "Etkin desenler F # programlama dili giriş verisi ayırabilir adlandırılmış bölümleri tanımlamak için nasıl kullanılacağını öğrenin."
keywords: "Visual f #, f # işlevsel programlama"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 11a724ff-f9ff-4056-b5e0-87e9ed986f4a
ms.openlocfilehash: 845184e6150cf0b93393038ca3d39f0e6d898a2e
ms.sourcegitcommit: a53799f81351ad9afb3007cd68846ce6aeeb10cb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/15/2017
---
# <a name="active-patterns"></a><span data-ttu-id="2644c-104">Etkin Desenler</span><span class="sxs-lookup"><span data-stu-id="2644c-104">Active Patterns</span></span>

<span data-ttu-id="2644c-105">*Etkin desenler* , bu adları için ayrılmış bir birleşim gibi ifadeyle eşleşen bir düzende kullanabilmesi için giriş verileri ayırabilir adlandırılmış bölümleri tanımlamayı sağlar.</span><span class="sxs-lookup"><span data-stu-id="2644c-105">*Active patterns* enable you to define named partitions that subdivide input data, so that you can use these names in a pattern matching expression just as you would for a discriminated union.</span></span> <span data-ttu-id="2644c-106">Etkin desenler her bölüm için özelleştirilmiş bir şekilde veri parçalayın için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2644c-106">You can use active patterns to decompose data in a customized manner for each partition.</span></span>


## <a name="syntax"></a><span data-ttu-id="2644c-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="2644c-107">Syntax</span></span>

```fsharp
// Complete active pattern definition.
let (|identifer1|identifier2|...|) [ arguments ] = expression
// Partial active pattern definition.
let (|identifier|_|) [ arguments ] = expression
```

## <a name="remarks"></a><span data-ttu-id="2644c-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="2644c-108">Remarks</span></span>
<span data-ttu-id="2644c-109">Önceki sözdiziminde tarafından temsil edilen giriş verileri bölümlerini adlarını tanımlayıcılardır *bağımsız değişkenleri*, veya, diğer bir deyişle, değişkenlerin tüm değerleri kümesi kümelerine adları.</span><span class="sxs-lookup"><span data-stu-id="2644c-109">In the previous syntax, the identifiers are names for partitions of the input data that is represented by *arguments*, or, in other words, names for subsets of the set of all values of the arguments.</span></span> <span data-ttu-id="2644c-110">Bir etkin desen tanımında en çok yedi bölüm olabilir.</span><span class="sxs-lookup"><span data-stu-id="2644c-110">There can be up to seven partitions in an active pattern definition.</span></span> <span data-ttu-id="2644c-111">*İfade* olduğu veri parçalayın forma açıklar.</span><span class="sxs-lookup"><span data-stu-id="2644c-111">The *expression* describes the form into which to decompose the data.</span></span> <span data-ttu-id="2644c-112">Adlandırılmış bölüm hangisinin ait bağımsız değişkenler olarak verilen değerleri belirlemek için kurallar tanımlamak için bir etkin desen tanımı kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2644c-112">You can use an active pattern definition to define the rules for determining which of the named partitions the values given as arguments belong to.</span></span> <span data-ttu-id="2644c-113">(| Ve |) simgeleri denir *Muz klipleri* ve bu tür let bağlama tarafından oluşturulan işlev çağrılır bir *etkin tanıyıcı*.</span><span class="sxs-lookup"><span data-stu-id="2644c-113">The (| and |) symbols are referred to as *banana clips* and the function created by this type of let binding is called an *active recognizer*.</span></span>

<span data-ttu-id="2644c-114">Örnek olarak, bağımsız değişkeni aşağıdaki etkin desen göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="2644c-114">As an example, consider the following active pattern with an argument.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet5001.fs)]

<span data-ttu-id="2644c-115">Aşağıdaki örnekte olduğu gibi ifade ile eşleşen bir deseni etkin desen kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2644c-115">You can use the active pattern in a pattern matching expression, as in the following example.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet5002.fs)]

<span data-ttu-id="2644c-116">Bu programın çıkışı aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="2644c-116">The output of this program is as follows:</span></span>

```
7 is odd
11 is odd
32 is even
```

<span data-ttu-id="2644c-117">Başka bir Etkin desenler veri türleri aynı temel alınan verilerin çeşitli olası sunularını olduğunda gibi birden çok yolla parçalayın için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="2644c-117">Another use of active patterns is to decompose data types in multiple ways, such as when the same underlying data has various possible representations.</span></span> <span data-ttu-id="2644c-118">Örneğin, bir `Color` nesne ayrılmış bir RGB temsili veya HSB gösterimi.</span><span class="sxs-lookup"><span data-stu-id="2644c-118">For example, a `Color` object could be decomposed into an RGB representation or an HSB representation.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet5003.fs)]

<span data-ttu-id="2644c-119">Yukarıdaki programın çıkışı aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="2644c-119">The output of the above program is as follows:</span></span>

```
Red
 Red: 255 Green: 0 Blue: 0
 Hue: 360.000000 Saturation: 1.000000 Brightness: 0.500000
Black
 Red: 0 Green: 0 Blue: 0
 Hue: 0.000000 Saturation: 0.000000 Brightness: 0.000000
White
 Red: 255 Green: 255 Blue: 255
 Hue: 0.000000 Saturation: 0.000000 Brightness: 1.000000
Gray
 Red: 128 Green: 128 Blue: 128
 Hue: 0.000000 Saturation: 0.000000 Brightness: 0.501961
BlanchedAlmond
 Red: 255 Green: 235 Blue: 205
 Hue: 36.000000 Saturation: 1.000000 Brightness: 0.901961
```

<span data-ttu-id="2644c-120">Birlikte, Etkin desenler kullanarak bu iki yolu bölüme etkinleştirin ve yalnızca uygun forma veri parçalayın ve hesaplama için en uygun biçimde uygun veri uygun hesaplamalar gerçekleştirin.</span><span class="sxs-lookup"><span data-stu-id="2644c-120">In combination, these two ways of using active patterns enable you to partition and decompose data into just the appropriate form and perform the appropriate computations on the appropriate data in the form most convenient for the computation.</span></span>

<span data-ttu-id="2644c-121">Sonuçta elde edilen desen eşleştirme ifadeleri çok okunabilir, büyük ölçüde basitleştirme potansiyel olarak karmaşık dallanma ve veri analizi kodu uygun şekilde yazılacak veriler etkinleştirin.</span><span class="sxs-lookup"><span data-stu-id="2644c-121">The resulting pattern matching expressions enable data to be written in a convenient way that is very readable, greatly simplifying potentially complex branching and data analysis code.</span></span>


## <a name="partial-active-patterns"></a><span data-ttu-id="2644c-122">Kısmi Etkin desenler</span><span class="sxs-lookup"><span data-stu-id="2644c-122">Partial Active Patterns</span></span>
<span data-ttu-id="2644c-123">Bazı durumlarda, yalnızca giriş alanı parçası bölüm gerekir.</span><span class="sxs-lookup"><span data-stu-id="2644c-123">Sometimes, you need to partition only part of the input space.</span></span> <span data-ttu-id="2644c-124">Bu durumda, kısmi desenleri de, bazı girişler eşleşen ancak diğer girişleri eşleşecek şekilde başarısız yazma.</span><span class="sxs-lookup"><span data-stu-id="2644c-124">In that case, you write a set of partial patterns each of which match some inputs but fail to match other inputs.</span></span> <span data-ttu-id="2644c-125">Her zaman bir değer üretmez Etkin desenler çağrılır *kısmi Etkin desenler*; bir seçenek türü bir dönüş değerine sahip.</span><span class="sxs-lookup"><span data-stu-id="2644c-125">Active patterns that do not always produce a value are called *partial active patterns*; they have a return value that is an option type.</span></span> <span data-ttu-id="2644c-126">Kısmi bir etkin düzeni tanımlamak için Muz klipleri içinde desenleri listesi sonunda joker karakteri (_) kullanın.</span><span class="sxs-lookup"><span data-stu-id="2644c-126">To define a partial active pattern, you use a wildcard character (_) at the end of the list of patterns inside the banana clips.</span></span> <span data-ttu-id="2644c-127">Aşağıdaki kod, kısmi bir etkin desen kullanımını göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="2644c-127">The following code illustrates the use of a partial active pattern.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet5004.fs)]

<span data-ttu-id="2644c-128">Önceki örnekte çıktısı şu şekildedir:</span><span class="sxs-lookup"><span data-stu-id="2644c-128">The output of the previous example is as follows:</span></span>

```
1.100000 : Floating point
0 : Integer
0.000000 : Floating point
10 : Integer
Something else : Not matched.
```

<span data-ttu-id="2644c-129">Kısmi Etkin desenler kullanırken, bazen tek tek seçimler ayrık veya birbirini dışlayan olabilir, ancak bunlar olmaması.</span><span class="sxs-lookup"><span data-stu-id="2644c-129">When using partial active patterns, sometimes the individual choices can be disjoint or mutually exclusive, but they need not be.</span></span> <span data-ttu-id="2644c-130">Kare ve küpleri 64 gibi bazı numaralarıdır aşağıdaki örnekte, düzeni kare ve küp düzeni ayrık, değildir.</span><span class="sxs-lookup"><span data-stu-id="2644c-130">In the following example, the pattern Square and the pattern Cube are not disjoint, because some numbers are both squares and cubes, such as 64.</span></span> <span data-ttu-id="2644c-131">Aşağıdaki programı tüm tamsayılar kadar kareler ve küpleri 1000000 yazdırır.</span><span class="sxs-lookup"><span data-stu-id="2644c-131">The following program prints out all integers up to 1000000 that are both squares and cubes.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet5005.fs)]

<span data-ttu-id="2644c-132">Çıktı aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="2644c-132">The output is as follows:</span></span>

```
1
64
729
4096
15625
46656
117649
262144
531441
1000000
```

## <a name="parameterized-active-patterns"></a><span data-ttu-id="2644c-133">Parametreli Etkin desenler</span><span class="sxs-lookup"><span data-stu-id="2644c-133">Parameterized Active Patterns</span></span>
<span data-ttu-id="2644c-134">Etkin desenler her zaman en az bir değişken eşleşen öğe için etkinleştirilir, ancak adı durumda ek bağımsız değişkenler de sürebilir *parametreli etkin desen* uygular.</span><span class="sxs-lookup"><span data-stu-id="2644c-134">Active patterns always take at least one argument for the item being matched, but they may take additional arguments as well, in which case the name *parameterized active pattern* applies.</span></span> <span data-ttu-id="2644c-135">Ek bağımsız değişkenler özelleştirilmesi için genel bir desen sağlar.</span><span class="sxs-lookup"><span data-stu-id="2644c-135">Additional arguments allow a general pattern to be specialized.</span></span> <span data-ttu-id="2644c-136">Örneğin, normal ifade de kısmi etkin desen kullanan aşağıdaki kod, olduğu gibi ek bir parametre olarak dizeler genellikle ayrıştırmak için normal ifadeleri kullanma Etkin desenler dahil `Integer` önceki kod örneğinde tanımlanan.</span><span class="sxs-lookup"><span data-stu-id="2644c-136">For example, active patterns that use regular expressions to parse strings often include the regular expression as an extra parameter, as in the following code, which also uses the partial active pattern `Integer` defined in the previous code example.</span></span> <span data-ttu-id="2644c-137">Bu örnekte, genel ParseRegex etkin desen özelleştirmek için çeşitli tarih biçimleri için normal ifadeler kullanan dizeleri verilir.</span><span class="sxs-lookup"><span data-stu-id="2644c-137">In this example, strings that use regular expressions for various date formats are given to customize the general ParseRegex active pattern.</span></span> <span data-ttu-id="2644c-138">Tamsayı etkin desen DateTime oluşturucuya geçirilen tamsayılar eşleşen dizeleri dönüştürmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="2644c-138">The Integer active pattern is used to convert the matched strings into integers that can be passed to the DateTime constructor.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet5006.fs)]

<span data-ttu-id="2644c-139">Önceki kod çıkışı aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="2644c-139">The output of the previous code is as follows:</span></span>

```
12/22/2008 12:00:00 AM 1/1/2009 12:00:00 AM 1/15/2008 12:00:00 AM 12/28/1995 12:00:00 AM
```

<span data-ttu-id="2644c-140">Etkin desenler yalnızca eşleşen ifadeleri desen sınırlı değildir, ayrıca bunları let bağlamaları üzerinde kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2644c-140">Active patterns are not restricted only to pattern matching expressions, you can also use them on let-bindings.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet5007.fs)]

<span data-ttu-id="2644c-141">Önceki kod çıkışı aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="2644c-141">The output of the previous code is as follows:</span></span>

```
Hello, random citizen!
Hello, George!
```

## <a name="see-also"></a><span data-ttu-id="2644c-142">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="2644c-142">See Also</span></span>
[<span data-ttu-id="2644c-143">F # dili başvurusu</span><span class="sxs-lookup"><span data-stu-id="2644c-143">F# Language Reference</span></span>](index.md)

[<span data-ttu-id="2644c-144">Eşleşme ifadeleri</span><span class="sxs-lookup"><span data-stu-id="2644c-144">Match Expressions</span></span>](match-expressions.md)

