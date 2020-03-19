---
title: Etkin Desenler
description: F# programlama dilinde giriş verilerini alt bölen adlandırılmış bölümleri tanımlamak için etkin desenleri nasıl kullanacağınızı öğrenin.
ms.date: 05/16/2016
ms.openlocfilehash: 898ef201369683bfd49d53e863e86f919f5837fe
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79187066"
---
# <a name="active-patterns"></a><span data-ttu-id="91009-103">Etkin Desenler</span><span class="sxs-lookup"><span data-stu-id="91009-103">Active Patterns</span></span>

<span data-ttu-id="91009-104">*Etkin desenler,* giriş verilerini alt bölen adlandırılmış bölümleri tanımlamanızı sağlar, böylece bu adları ayrımcı bir birliktelik için olduğu gibi eşleşen bir ifadede deseni kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="91009-104">*Active patterns* enable you to define named partitions that subdivide input data, so that you can use these names in a pattern matching expression just as you would for a discriminated union.</span></span> <span data-ttu-id="91009-105">Verileri her bölüm için özelleştirilmiş bir şekilde ayrıştırmak için etkin desenler kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="91009-105">You can use active patterns to decompose data in a customized manner for each partition.</span></span>

## <a name="syntax"></a><span data-ttu-id="91009-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="91009-106">Syntax</span></span>

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

## <a name="remarks"></a><span data-ttu-id="91009-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="91009-107">Remarks</span></span>

<span data-ttu-id="91009-108">Önceki sözdiziminde, *tanımlayıcılar, bağımsız değişkenler*tarafından temsil edilen giriş verilerinin bölümlerinin veya başka bir deyişle, bağımsız değişkenlerin tüm değer kümelerinin alt kümelerinin adlarıdır.</span><span class="sxs-lookup"><span data-stu-id="91009-108">In the previous syntax, the identifiers are names for partitions of the input data that is represented by *arguments*, or, in other words, names for subsets of the set of all values of the arguments.</span></span> <span data-ttu-id="91009-109">Etkin desen tanımında en fazla yedi bölüm olabilir.</span><span class="sxs-lookup"><span data-stu-id="91009-109">There can be up to seven partitions in an active pattern definition.</span></span> <span data-ttu-id="91009-110">*İfade,* verileri ayrıştırmak için hangi formu açıklar.</span><span class="sxs-lookup"><span data-stu-id="91009-110">The *expression* describes the form into which to decompose the data.</span></span> <span data-ttu-id="91009-111">Adlandırılmış bölümlerden hangisinin bağımsız değişken olarak verilen değerlerin ait olduğunu belirlemek için kuralları tanımlamak için etkin bir desen tanımı kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="91009-111">You can use an active pattern definition to define the rules for determining which of the named partitions the values given as arguments belong to.</span></span> <span data-ttu-id="91009-112">(| ve |) *sembolleri muz klipleri* olarak adlandırılır ve bu tür let bağlama tarafından oluşturulan işlev *etkin tanıyıcı*olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="91009-112">The (| and |) symbols are referred to as *banana clips* and the function created by this type of let binding is called an *active recognizer*.</span></span>

<span data-ttu-id="91009-113">Örnek olarak, bir bağımsız değişken ile aşağıdaki etkin desen düşünün.</span><span class="sxs-lookup"><span data-stu-id="91009-113">As an example, consider the following active pattern with an argument.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5001.fs)]

<span data-ttu-id="91009-114">Aşağıdaki örnekte olduğu gibi, etkin deseni desen eşleştirme ifadesinde kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="91009-114">You can use the active pattern in a pattern matching expression, as in the following example.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5002.fs)]

<span data-ttu-id="91009-115">Bu programın çıktısı aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="91009-115">The output of this program is as follows:</span></span>

```console
7 is odd
11 is odd
32 is even
```

<span data-ttu-id="91009-116">Etkin desenlerin başka bir kullanımı, aynı temel verilerin çeşitli olası gösterimleri olması gibi veri türlerini birden çok şekilde ayrıştırmaktır.</span><span class="sxs-lookup"><span data-stu-id="91009-116">Another use of active patterns is to decompose data types in multiple ways, such as when the same underlying data has various possible representations.</span></span> <span data-ttu-id="91009-117">Örneğin, bir `Color` nesne RGB gösterimi veya HSB gösterimi olarak ayrıştırılabilir.</span><span class="sxs-lookup"><span data-stu-id="91009-117">For example, a `Color` object could be decomposed into an RGB representation or an HSB representation.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5003.fs)]

<span data-ttu-id="91009-118">Yukarıdaki programın çıktısı aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="91009-118">The output of the above program is as follows:</span></span>

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

<span data-ttu-id="91009-119">Birlikte, etkin desenleri kullanmanın bu iki yolu, verileri yalnızca uygun biçimde bölmenize ve ayrıştırmanıza ve uygun veriler üzerinde uygun hesaplamaları hesaplama için en uygun biçimde gerçekleştirmenize olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="91009-119">In combination, these two ways of using active patterns enable you to partition and decompose data into just the appropriate form and perform the appropriate computations on the appropriate data in the form most convenient for the computation.</span></span>

<span data-ttu-id="91009-120">Ortaya çıkan desen eşleştirme ifadeleri, verilerin çok okunabilir bir şekilde yazılmasını sağlayarak karmaşık olabilecek dallanma ve veri çözümleme kodunu büyük ölçüde basitleştirir.</span><span class="sxs-lookup"><span data-stu-id="91009-120">The resulting pattern matching expressions enable data to be written in a convenient way that is very readable, greatly simplifying potentially complex branching and data analysis code.</span></span>

## <a name="partial-active-patterns"></a><span data-ttu-id="91009-121">Kısmi Aktif Desenler</span><span class="sxs-lookup"><span data-stu-id="91009-121">Partial Active Patterns</span></span>

<span data-ttu-id="91009-122">Bazen, giriş alanının yalnızca bir kısmını bölmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="91009-122">Sometimes, you need to partition only part of the input space.</span></span> <span data-ttu-id="91009-123">Bu durumda, her biri bazı girişler eşleşen ancak diğer girişleri eşleşemeyen kısmi desenler kümesi yazın.</span><span class="sxs-lookup"><span data-stu-id="91009-123">In that case, you write a set of partial patterns each of which match some inputs but fail to match other inputs.</span></span> <span data-ttu-id="91009-124">Her zaman bir değer üretmeyen *etkin desenlere kısmi etkin desenler*denir; opsiyon türüolan bir iade değerine sahiptirler.</span><span class="sxs-lookup"><span data-stu-id="91009-124">Active patterns that do not always produce a value are called *partial active patterns*; they have a return value that is an option type.</span></span> <span data-ttu-id="91009-125">Kısmi etkin bir desen tanımlamak için, muz\_kliplerinin içindeki desen listesinin sonunda bir joker karakter ( ) kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="91009-125">To define a partial active pattern, you use a wildcard character (\_) at the end of the list of patterns inside the banana clips.</span></span> <span data-ttu-id="91009-126">Aşağıdaki kod kısmi etkin bir desen kullanımını göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="91009-126">The following code illustrates the use of a partial active pattern.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5004.fs)]

<span data-ttu-id="91009-127">Önceki örneğin çıktısı aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="91009-127">The output of the previous example is as follows:</span></span>

```console
1.100000 : Floating point
0 : Integer
0.000000 : Floating point
10 : Integer
Something else : Not matched.
```

<span data-ttu-id="91009-128">Kısmi etkin desenler kullanırken, bazen bireysel seçimler ayrık veya birbirini dışlayan olabilir, ancak gerek yoktur.</span><span class="sxs-lookup"><span data-stu-id="91009-128">When using partial active patterns, sometimes the individual choices can be disjoint or mutually exclusive, but they need not be.</span></span> <span data-ttu-id="91009-129">Aşağıdaki örnekte, bazı sayılar 64 gibi kareler ve küpler olduğundan, desen Kare ve desen Küp ayrı değildir.</span><span class="sxs-lookup"><span data-stu-id="91009-129">In the following example, the pattern Square and the pattern Cube are not disjoint, because some numbers are both squares and cubes, such as 64.</span></span> <span data-ttu-id="91009-130">Aşağıdaki program Kare ve Küp desenleri birleştirmek için AND deseni kullanır.</span><span class="sxs-lookup"><span data-stu-id="91009-130">The following program uses the AND pattern to combine the Square and Cube patterns.</span></span> <span data-ttu-id="91009-131">Hem kareler hem de küpler olan 1000'e kadar olan tüm tamsaların yanı sıra yalnızca küp olan tüm tamsayıları yazdırır.</span><span class="sxs-lookup"><span data-stu-id="91009-131">It prints out all integers up to 1000 that are both squares and cubes, as well as those which are only cubes.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5005.fs)]

<span data-ttu-id="91009-132">Çıktı aşağıdaki şekilde olacaktır:</span><span class="sxs-lookup"><span data-stu-id="91009-132">The output is as follows:</span></span>

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

## <a name="parameterized-active-patterns"></a><span data-ttu-id="91009-133">Parametreli Etkin Desenler</span><span class="sxs-lookup"><span data-stu-id="91009-133">Parameterized Active Patterns</span></span>

<span data-ttu-id="91009-134">Etkin desenler her zaman eşleşen öğe için en az bir bağımsız değişken alır, ancak ek bağımsız değişkenler de alabilir, bu durumda ad *parametreli etkin desen* geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="91009-134">Active patterns always take at least one argument for the item being matched, but they may take additional arguments as well, in which case the name *parameterized active pattern* applies.</span></span> <span data-ttu-id="91009-135">Ek bağımsız değişkenler genel bir desen özel leştirilmiş olmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="91009-135">Additional arguments allow a general pattern to be specialized.</span></span> <span data-ttu-id="91009-136">Örneğin, dizeleri ayrıştırmak için normal ifadeler kullanan etkin desenler genellikle önceki kod örneğinde tanımlanan kısmi etkin desen `Integer` kullanan aşağıdaki kodda olduğu gibi, ek bir parametre olarak normal ifadeyi içerir.</span><span class="sxs-lookup"><span data-stu-id="91009-136">For example, active patterns that use regular expressions to parse strings often include the regular expression as an extra parameter, as in the following code, which also uses the partial active pattern `Integer` defined in the previous code example.</span></span> <span data-ttu-id="91009-137">Bu örnekte, genel ParseRegex etkin deseni özelleştirmek için çeşitli tarih biçimleri için normal ifadeler kullanan dizeleri verilir.</span><span class="sxs-lookup"><span data-stu-id="91009-137">In this example, strings that use regular expressions for various date formats are given to customize the general ParseRegex active pattern.</span></span> <span data-ttu-id="91009-138">Karşıcı etkin desen, eşleşen dizeleri DateTime oluşturucusuna geçirilebilen bir aralığa dönüştürmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="91009-138">The Integer active pattern is used to convert the matched strings into integers that can be passed to the DateTime constructor.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5006.fs)]

<span data-ttu-id="91009-139">Önceki kodun çıktısı aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="91009-139">The output of the previous code is as follows:</span></span>

```console
12/22/2008 12:00:00 AM 1/1/2009 12:00:00 AM 1/15/2008 12:00:00 AM 12/28/1995 12:00:00 AM
```

<span data-ttu-id="91009-140">Etkin desenler yalnızca desen eşleştirme ifadeleriyle sınırlı değildir, bunları izin bağlamalarında da kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="91009-140">Active patterns are not restricted only to pattern matching expressions, you can also use them on let-bindings.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5007.fs)]

<span data-ttu-id="91009-141">Önceki kodun çıktısı aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="91009-141">The output of the previous code is as follows:</span></span>

```console
Hello, random citizen!
Hello, George!
```

## <a name="see-also"></a><span data-ttu-id="91009-142">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="91009-142">See also</span></span>

- [<span data-ttu-id="91009-143">F# Dil Referansı</span><span class="sxs-lookup"><span data-stu-id="91009-143">F# Language Reference</span></span>](index.md)
- [<span data-ttu-id="91009-144">Eşleşme İfadeleri</span><span class="sxs-lookup"><span data-stu-id="91009-144">Match Expressions</span></span>](match-expressions.md)
