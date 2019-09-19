---
title: Etkin Desenler
description: F# Programlama dilinde giriş verilerini bölümlendirilen adlandırılmış bölümleri tanımlamak için etkin desenleri nasıl kullanacağınızı öğrenin.
ms.date: 05/16/2016
ms.openlocfilehash: 0c1315f2386b3cea2def698f4725e4c1cf030609
ms.sourcegitcommit: a2d0e1f66367367065bc8dc0dde488ab536da73f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/18/2019
ms.locfileid: "71083075"
---
# <a name="active-patterns"></a><span data-ttu-id="55161-103">Etkin Desenler</span><span class="sxs-lookup"><span data-stu-id="55161-103">Active Patterns</span></span>

<span data-ttu-id="55161-104">*Etkin desenler* , bu adları ayrılmış bir birleşim için yaptığınız gibi bir desen eşleştirme ifadesinde kullanabilmeniz için, giriş verilerini bölümlendirilen adlandırılmış bölümler tanımlamanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="55161-104">*Active patterns* enable you to define named partitions that subdivide input data, so that you can use these names in a pattern matching expression just as you would for a discriminated union.</span></span> <span data-ttu-id="55161-105">Her bölüm için özelleştirilmiş bir şekilde verileri ayırmak için etkin desenleri kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="55161-105">You can use active patterns to decompose data in a customized manner for each partition.</span></span>

## <a name="syntax"></a><span data-ttu-id="55161-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="55161-106">Syntax</span></span>

```fsharp
// Active pattern of one choice.
let (|identifier|) [arguments] valueToMatch= expression

// Active Pattern with multiple choices.
// Uses a FSharp.Core.Choice<_,...,_> based on the number of case names. In F#, the limitation n <= 7 applies.
let (|identifer1|identifier2|...|) valueToMatch = expression

// Partial active pattern definition.
// Uses a FSharp.Core.option<_> to represent if the type is satisfied at the call site.
let (|identifier|_|) [arguments ] valueToMatch = expression
```

## <a name="remarks"></a><span data-ttu-id="55161-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="55161-107">Remarks</span></span>

<span data-ttu-id="55161-108">Önceki sözdiziminde, tanımlayıcılar *bağımsız değişkenlerle*temsil edilen giriş verilerinin bölümlerinin adlarıdır veya diğer bir deyişle, bağımsız değişkenlerin tüm değerleri kümesinin alt kümelerine yönelik adlar.</span><span class="sxs-lookup"><span data-stu-id="55161-108">In the previous syntax, the identifiers are names for partitions of the input data that is represented by *arguments*, or, in other words, names for subsets of the set of all values of the arguments.</span></span> <span data-ttu-id="55161-109">Etkin bir model tanımında en fazla yedi bölüm olabilir.</span><span class="sxs-lookup"><span data-stu-id="55161-109">There can be up to seven partitions in an active pattern definition.</span></span> <span data-ttu-id="55161-110">*İfade* , verilerin parçalara çıkarılması için kullanılacak formu açıklar.</span><span class="sxs-lookup"><span data-stu-id="55161-110">The *expression* describes the form into which to decompose the data.</span></span> <span data-ttu-id="55161-111">Adlandırılmış bölümlerin bağımsız değişken olarak verilen değerlerin hangisinin dahil olduğunu belirlemek için kuralları tanımlamak üzere etkin bir model tanımı kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="55161-111">You can use an active pattern definition to define the rules for determining which of the named partitions the values given as arguments belong to.</span></span> <span data-ttu-id="55161-112">(| Ve |) sembolleri, *muz klip* olarak adlandırılır ve bu tür Let bağlamasıyla oluşturulan işleve *etkin bir tanıyıcı*denir.</span><span class="sxs-lookup"><span data-stu-id="55161-112">The (| and |) symbols are referred to as *banana clips* and the function created by this type of let binding is called an *active recognizer*.</span></span>

<span data-ttu-id="55161-113">Örnek olarak, aşağıdaki etkin düzene bir bağımsız değişkenle göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="55161-113">As an example, consider the following active pattern with an argument.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5001.fs)]

<span data-ttu-id="55161-114">Aşağıdaki örnekte olduğu gibi, bir model eşleştirme ifadesinde etkin bir model kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="55161-114">You can use the active pattern in a pattern matching expression, as in the following example.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5002.fs)]

<span data-ttu-id="55161-115">Bu programın çıktısı aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="55161-115">The output of this program is as follows:</span></span>

```console
7 is odd
11 is odd
32 is even
```

<span data-ttu-id="55161-116">Farklı bir etkin model kullanımı, veri türlerini birden çok şekilde oluşturmak, örneğin aynı temeldeki verilerin çeşitli olası temsiller olması olabilir.</span><span class="sxs-lookup"><span data-stu-id="55161-116">Another use of active patterns is to decompose data types in multiple ways, such as when the same underlying data has various possible representations.</span></span> <span data-ttu-id="55161-117">Örneğin, bir `Color` nesne bir rgb gösterimine veya bir HSB gösterimine parçalanamadı.</span><span class="sxs-lookup"><span data-stu-id="55161-117">For example, a `Color` object could be decomposed into an RGB representation or an HSB representation.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5003.fs)]

<span data-ttu-id="55161-118">Yukarıdaki programın çıktısı aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="55161-118">The output of the above program is as follows:</span></span>

```console
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

<span data-ttu-id="55161-119">Bunun yanında, etkin desenleri kullanmanın bu iki yolu, verileri yalnızca uygun biçimde bölümleyip oluştururın ve uygun hesaplamaları hesaplama için en kullanışlı biçimde gerçekleştirmenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="55161-119">In combination, these two ways of using active patterns enable you to partition and decompose data into just the appropriate form and perform the appropriate computations on the appropriate data in the form most convenient for the computation.</span></span>

<span data-ttu-id="55161-120">Sonuç olarak eşleşen desenler, verilerin çok okunaklı, büyük olasılıkla karmaşık dallara ve veri analizi koduna büyük ölçüde basitleşerek kolay bir şekilde yazılmasına olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="55161-120">The resulting pattern matching expressions enable data to be written in a convenient way that is very readable, greatly simplifying potentially complex branching and data analysis code.</span></span>

## <a name="partial-active-patterns"></a><span data-ttu-id="55161-121">Kısmi etkin desenler</span><span class="sxs-lookup"><span data-stu-id="55161-121">Partial Active Patterns</span></span>

<span data-ttu-id="55161-122">Bazen, giriş alanının yalnızca bir kısmını bölümleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="55161-122">Sometimes, you need to partition only part of the input space.</span></span> <span data-ttu-id="55161-123">Bu durumda, her biri bazı girdilerle eşleşen, ancak diğer girişlerle eşleşmeyecek bir kısmi desenler kümesi yazarsınız.</span><span class="sxs-lookup"><span data-stu-id="55161-123">In that case, you write a set of partial patterns each of which match some inputs but fail to match other inputs.</span></span> <span data-ttu-id="55161-124">Her zaman bir değer üretmeyen etkin desenler *kısmen etkin desenler*olarak adlandırılır; Bunlar bir seçenek türü olan bir dönüş değerine sahiptir.</span><span class="sxs-lookup"><span data-stu-id="55161-124">Active patterns that do not always produce a value are called *partial active patterns*; they have a return value that is an option type.</span></span> <span data-ttu-id="55161-125">Kısmi bir etkin düzen tanımlamak için, muz kliplerin içindeki desenler listesinin\_sonunda bir joker karakteri () kullanın.</span><span class="sxs-lookup"><span data-stu-id="55161-125">To define a partial active pattern, you use a wildcard character (\_) at the end of the list of patterns inside the banana clips.</span></span> <span data-ttu-id="55161-126">Aşağıdaki kod, kısmen etkin bir düzenin kullanımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="55161-126">The following code illustrates the use of a partial active pattern.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5004.fs)]

<span data-ttu-id="55161-127">Önceki örneğin çıktısı aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="55161-127">The output of the previous example is as follows:</span></span>

```console
1.100000 : Floating point
0 : Integer
0.000000 : Floating point
10 : Integer
Something else : Not matched.
```

<span data-ttu-id="55161-128">Kısmi etkin desenler kullanılırken, bazen bağımsız seçimler ayrık veya birbirini dışlamalı olabilir, ancak bunların olmaması gerekir.</span><span class="sxs-lookup"><span data-stu-id="55161-128">When using partial active patterns, sometimes the individual choices can be disjoint or mutually exclusive, but they need not be.</span></span> <span data-ttu-id="55161-129">Aşağıdaki örnekte, model karesi ve model küpü ayrık değildir, çünkü bazı sayılar hem kareler hem de küplerdir (örneğin, 64).</span><span class="sxs-lookup"><span data-stu-id="55161-129">In the following example, the pattern Square and the pattern Cube are not disjoint, because some numbers are both squares and cubes, such as 64.</span></span> <span data-ttu-id="55161-130">Aşağıdaki program kare ve küp desenlerini birleştirmek için ve desenini kullanır.</span><span class="sxs-lookup"><span data-stu-id="55161-130">The following program uses the AND pattern to combine the Square and Cube patterns.</span></span> <span data-ttu-id="55161-131">Hem kareler hem de küpler olan ve yalnızca küplerden oluşan tüm tamsayıları 1000 'e kadar yazdırır.</span><span class="sxs-lookup"><span data-stu-id="55161-131">It print out all integers up to 1000 that are both squares and cubes, as well as those which are only cubes.</span></span> 

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5005.fs)]

<span data-ttu-id="55161-132">Çıktı aşağıdaki şekilde olacaktır:</span><span class="sxs-lookup"><span data-stu-id="55161-132">The output is as follows:</span></span>

```console
1 is a cube and a square
8 is a cube
27 is a cube
64 is a cube and a square
125 is a cube
216 is a cube
343 is a cube
512 is a cube
729 is a cube and a square
1000 is a cube
```

## <a name="parameterized-active-patterns"></a><span data-ttu-id="55161-133">Parametreli etkin desenler</span><span class="sxs-lookup"><span data-stu-id="55161-133">Parameterized Active Patterns</span></span>

<span data-ttu-id="55161-134">Etkin desenler, eşleşen öğe için her zaman en az bir bağımsız değişken alır, ancak bu durumda, ad *Parametreli etkin düzeni* geçerli olacak şekilde ek bağımsız değişkenler de olabilir.</span><span class="sxs-lookup"><span data-stu-id="55161-134">Active patterns always take at least one argument for the item being matched, but they may take additional arguments as well, in which case the name *parameterized active pattern* applies.</span></span> <span data-ttu-id="55161-135">Ek bağımsız değişkenler, genel bir düzenin özelleştireklenmesine izin verir.</span><span class="sxs-lookup"><span data-stu-id="55161-135">Additional arguments allow a general pattern to be specialized.</span></span> <span data-ttu-id="55161-136">Örneğin, dizeleri ayrıştırmak için normal ifadeler kullanan etkin desenler, bir önceki kod örneğinde tanımlanan kısmi etkin deseni `Integer` de kullanan aşağıdaki kodda olduğu gibi normal ifadeyi ek bir parametre olarak içerir.</span><span class="sxs-lookup"><span data-stu-id="55161-136">For example, active patterns that use regular expressions to parse strings often include the regular expression as an extra parameter, as in the following code, which also uses the partial active pattern `Integer` defined in the previous code example.</span></span> <span data-ttu-id="55161-137">Bu örnekte, çeşitli tarih biçimleri için normal ifadeler kullanan dizeler, genel ParseRegex etkin modelini özelleştirmek için verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="55161-137">In this example, strings that use regular expressions for various date formats are given to customize the general ParseRegex active pattern.</span></span> <span data-ttu-id="55161-138">Tamsayı etkin stili, eşleşen dizeleri DateTime oluşturucusuna geçirilebilecek tamsayılara dönüştürmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="55161-138">The Integer active pattern is used to convert the matched strings into integers that can be passed to the DateTime constructor.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5006.fs)]

<span data-ttu-id="55161-139">Önceki kodun çıktısı aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="55161-139">The output of the previous code is as follows:</span></span>

```console
12/22/2008 12:00:00 AM 1/1/2009 12:00:00 AM 1/15/2008 12:00:00 AM 12/28/1995 12:00:00 AM
```

<span data-ttu-id="55161-140">Etkin desenler yalnızca desen eşleştirme ifadelerine kısıtlanmaz, bunları Let bağlamaları üzerinde de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="55161-140">Active patterns are not restricted only to pattern matching expressions, you can also use them on let-bindings.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5007.fs)]

<span data-ttu-id="55161-141">Önceki kodun çıktısı aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="55161-141">The output of the previous code is as follows:</span></span>

```console
Hello, random citizen!
Hello, George!
```

## <a name="see-also"></a><span data-ttu-id="55161-142">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="55161-142">See also</span></span>

- [<span data-ttu-id="55161-143">F# Dili Başvurusu</span><span class="sxs-lookup"><span data-stu-id="55161-143">F# Language Reference</span></span>](index.md)
- [<span data-ttu-id="55161-144">Eşleşme İfadeleri</span><span class="sxs-lookup"><span data-stu-id="55161-144">Match Expressions</span></span>](match-expressions.md)
