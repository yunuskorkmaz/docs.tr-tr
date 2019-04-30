---
title: Etkin Desenler
description: Etkin desenler girdi verileri alt bölümlere adlandırılmış bölümler tanımlamak için kullanmayı öğrenin F# programlama dilidir.
ms.date: 05/16/2016
ms.openlocfilehash: 0f1f57de425836738201d2d8f84ab67a0df142ee
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61772759"
---
# <a name="active-patterns"></a><span data-ttu-id="35cd0-103">Etkin Desenler</span><span class="sxs-lookup"><span data-stu-id="35cd0-103">Active Patterns</span></span>

<span data-ttu-id="35cd0-104">*Etkin desenler* , bir desen eşleme ifadesinde için ayrılmış bir birleşim olduğu gibi bu adlar kullanabilirsiniz, böylece giriş verileri alt bölümlere adlandırılmış bölümler tanımlamanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="35cd0-104">*Active patterns* enable you to define named partitions that subdivide input data, so that you can use these names in a pattern matching expression just as you would for a discriminated union.</span></span> <span data-ttu-id="35cd0-105">Etkin desenler, her bölüm için özelleştirilmiş bir şekilde veri ayırmak için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="35cd0-105">You can use active patterns to decompose data in a customized manner for each partition.</span></span>

## <a name="syntax"></a><span data-ttu-id="35cd0-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="35cd0-106">Syntax</span></span>

```fsharp
// Complete active pattern definition.
let (|identifer1|identifier2|...|) [ arguments ] = expression
// Partial active pattern definition.
let (|identifier|_|) [ arguments ] = expression
```

## <a name="remarks"></a><span data-ttu-id="35cd0-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="35cd0-107">Remarks</span></span>

<span data-ttu-id="35cd0-108">Önceki sözdiziminde, bölümler tarafından temsil edilen giriş verileri için adları tanımlayıcılardır *bağımsız değişkenleri*, veya başka bir deyişle, bağımsız değişkenlerin tüm değerleri kümesi kümelerine adları.</span><span class="sxs-lookup"><span data-stu-id="35cd0-108">In the previous syntax, the identifiers are names for partitions of the input data that is represented by *arguments*, or, in other words, names for subsets of the set of all values of the arguments.</span></span> <span data-ttu-id="35cd0-109">Bir etkin düzeni tanımında en fazla yedi bölüm olabilir.</span><span class="sxs-lookup"><span data-stu-id="35cd0-109">There can be up to seven partitions in an active pattern definition.</span></span> <span data-ttu-id="35cd0-110">*İfade* , verileri ayırmak forma açıklar.</span><span class="sxs-lookup"><span data-stu-id="35cd0-110">The *expression* describes the form into which to decompose the data.</span></span> <span data-ttu-id="35cd0-111">Etkin desen tanımı, adlandırılmış bölüm ait bağımsız değişkenler olarak verilen değerlerden belirleyen kuralları tanımlamak için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="35cd0-111">You can use an active pattern definition to define the rules for determining which of the named partitions the values given as arguments belong to.</span></span> <span data-ttu-id="35cd0-112">(| Ve |) sembolleri denir *Muz klipleri* ve bu tür bir let bağlama tarafından oluşturulan işlev çağrılırsa bir *etkin tanıyıcı*.</span><span class="sxs-lookup"><span data-stu-id="35cd0-112">The (| and |) symbols are referred to as *banana clips* and the function created by this type of let binding is called an *active recognizer*.</span></span>

<span data-ttu-id="35cd0-113">Örneğin, bir bağımsız değişken ile aşağıdaki etkin düzeni göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="35cd0-113">As an example, consider the following active pattern with an argument.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet5001.fs)]

<span data-ttu-id="35cd0-114">Etkin desen bir desen eşleme ifadesinde, aşağıdaki örnekte olduğu gibi kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="35cd0-114">You can use the active pattern in a pattern matching expression, as in the following example.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet5002.fs)]

<span data-ttu-id="35cd0-115">Bu program çıktısı aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="35cd0-115">The output of this program is as follows:</span></span>

```
7 is odd
11 is odd
32 is even
```

<span data-ttu-id="35cd0-116">Başka bir Etkin desenler veri türleri aynı temel alınan verilerin çeşitli olası gösterimleri olduğunda gibi birden çok yolla ayırmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="35cd0-116">Another use of active patterns is to decompose data types in multiple ways, such as when the same underlying data has various possible representations.</span></span> <span data-ttu-id="35cd0-117">Örneğin, bir `Color` nesne ayrılmış bir RGB temsili ya da bir HSB temsili.</span><span class="sxs-lookup"><span data-stu-id="35cd0-117">For example, a `Color` object could be decomposed into an RGB representation or an HSB representation.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5003.fs)]

<span data-ttu-id="35cd0-118">Yukarıdaki program çıktısı aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="35cd0-118">The output of the above program is as follows:</span></span>

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

<span data-ttu-id="35cd0-119">Birlikte, Etkin desenler kullanarak bu iki yolu bölüme etkinleştirin ve yalnızca uygun biçime verileri parçalayın ve hesaplama için en uygun biçimde uygun veri uygun hesaplamalar gerçekleştirin.</span><span class="sxs-lookup"><span data-stu-id="35cd0-119">In combination, these two ways of using active patterns enable you to partition and decompose data into just the appropriate form and perform the appropriate computations on the appropriate data in the form most convenient for the computation.</span></span>

<span data-ttu-id="35cd0-120">Sonuçta elde edilen desen eşleştirme ifadeleri çok okunabilir, büyük ölçüde basitleştirme bulunabilecek karmaşık dallanma ve veri analizi kodu uygun şekilde yazılacak veriler etkinleştirin.</span><span class="sxs-lookup"><span data-stu-id="35cd0-120">The resulting pattern matching expressions enable data to be written in a convenient way that is very readable, greatly simplifying potentially complex branching and data analysis code.</span></span>

## <a name="partial-active-patterns"></a><span data-ttu-id="35cd0-121">Kısmi Etkin desenler</span><span class="sxs-lookup"><span data-stu-id="35cd0-121">Partial Active Patterns</span></span>

<span data-ttu-id="35cd0-122">Bazen, giriş alanı yalnızca bir kısmını bölümlemek gerekir.</span><span class="sxs-lookup"><span data-stu-id="35cd0-122">Sometimes, you need to partition only part of the input space.</span></span> <span data-ttu-id="35cd0-123">Bu durumda, kısmi desenleri, bazı girişler eşleşen ancak diğer girişler eşleştirilecek başarısız yazın.</span><span class="sxs-lookup"><span data-stu-id="35cd0-123">In that case, you write a set of partial patterns each of which match some inputs but fail to match other inputs.</span></span> <span data-ttu-id="35cd0-124">Her zaman bir değer üretmez Etkin desenler çağrılır *kısmi Etkin desenler*; bunlar seçeneği türünde bir dönüş değerine sahip.</span><span class="sxs-lookup"><span data-stu-id="35cd0-124">Active patterns that do not always produce a value are called *partial active patterns*; they have a return value that is an option type.</span></span> <span data-ttu-id="35cd0-125">Kısmi bir etkin düzeni tanımlamak için bir joker karakter kullanın. (\_) Muz klipleri içinde Desen listesinin sonunda.</span><span class="sxs-lookup"><span data-stu-id="35cd0-125">To define a partial active pattern, you use a wildcard character (\_) at the end of the list of patterns inside the banana clips.</span></span> <span data-ttu-id="35cd0-126">Aşağıdaki kodu kısmi bir etkin desen kullanımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="35cd0-126">The following code illustrates the use of a partial active pattern.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5004.fs)]

<span data-ttu-id="35cd0-127">Önceki örnek çıktısı aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="35cd0-127">The output of the previous example is as follows:</span></span>

```
1.100000 : Floating point
0 : Integer
0.000000 : Floating point
10 : Integer
Something else : Not matched.
```

<span data-ttu-id="35cd0-128">Kısmi Etkin desenler kullanırken bazen tek tek seçimler ayrık veya birbirini dışlayan olabilir, ancak bunlar olmaması.</span><span class="sxs-lookup"><span data-stu-id="35cd0-128">When using partial active patterns, sometimes the individual choices can be disjoint or mutually exclusive, but they need not be.</span></span> <span data-ttu-id="35cd0-129">Bazı sayılar kareler hem 64 gibi küpler olduğundan aşağıdaki örnekte, deseni kare ve küp deseni ayrık, değildir.</span><span class="sxs-lookup"><span data-stu-id="35cd0-129">In the following example, the pattern Square and the pattern Cube are not disjoint, because some numbers are both squares and cubes, such as 64.</span></span> <span data-ttu-id="35cd0-130">Aşağıdaki program, kare ve küp desenleri birleştirmek ve deseni kullanır.</span><span class="sxs-lookup"><span data-stu-id="35cd0-130">The following program uses the AND pattern to combine the Square and Cube patterns.</span></span> <span data-ttu-id="35cd0-131">Yazdırabilirsiniz hem kareler ve küpleri, hem de hangi yalnızca küpleri olan 1000'e kadar tüm tamsayıları.</span><span class="sxs-lookup"><span data-stu-id="35cd0-131">It print out all integers up to 1000 that are both squares and cubes, as well as those which are only cubes.</span></span> 

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5005.fs)]

<span data-ttu-id="35cd0-132">Çıktı aşağıdaki şekilde olacaktır:</span><span class="sxs-lookup"><span data-stu-id="35cd0-132">The output is as follows:</span></span>

```
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

## <a name="parameterized-active-patterns"></a><span data-ttu-id="35cd0-133">Parametreli Etkin desenler</span><span class="sxs-lookup"><span data-stu-id="35cd0-133">Parameterized Active Patterns</span></span>

<span data-ttu-id="35cd0-134">Etkin desenler, eşleştirilen öğesi için en az bir bağımsız değişkeni her zaman alır ancak adı bu durumda da, ek bağımsız değişken alabilir *parametreli etkin desen* uygular.</span><span class="sxs-lookup"><span data-stu-id="35cd0-134">Active patterns always take at least one argument for the item being matched, but they may take additional arguments as well, in which case the name *parameterized active pattern* applies.</span></span> <span data-ttu-id="35cd0-135">Ek bağımsız değişkenler özelleştirilmesi için genel bir desen sağlar.</span><span class="sxs-lookup"><span data-stu-id="35cd0-135">Additional arguments allow a general pattern to be specialized.</span></span> <span data-ttu-id="35cd0-136">Örneğin, normal ifade ayrıca kısmi etkin deseni kullanan aşağıdaki kod, olduğu gibi ek bir parametre olarak dizeler genellikle ayrıştırmak için normal ifadeleri kullanma Etkin desenler dahil `Integer` önceki kod örneğinde tanımlanan.</span><span class="sxs-lookup"><span data-stu-id="35cd0-136">For example, active patterns that use regular expressions to parse strings often include the regular expression as an extra parameter, as in the following code, which also uses the partial active pattern `Integer` defined in the previous code example.</span></span> <span data-ttu-id="35cd0-137">Bu örnekte, çeşitli tarih biçimleri için normal ifadeleri kullanma dizeleri genel ParseRegex etkin düzeni özelleştirildiği verilir.</span><span class="sxs-lookup"><span data-stu-id="35cd0-137">In this example, strings that use regular expressions for various date formats are given to customize the general ParseRegex active pattern.</span></span> <span data-ttu-id="35cd0-138">Tamsayı etkin deseni, eşleşen dizeleri DateTime oluşturucuya geçirilen tamsayı dönüştürmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="35cd0-138">The Integer active pattern is used to convert the matched strings into integers that can be passed to the DateTime constructor.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5006.fs)]

<span data-ttu-id="35cd0-139">Önceki kodun çıktısı aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="35cd0-139">The output of the previous code is as follows:</span></span>

```
12/22/2008 12:00:00 AM 1/1/2009 12:00:00 AM 1/15/2008 12:00:00 AM 12/28/1995 12:00:00 AM
```

<span data-ttu-id="35cd0-140">Etkin desenler yalnızca eşleşen bir ifade deseni için sınırlı değildir, ayrıca bunları let bağlamaları üzerinde kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="35cd0-140">Active patterns are not restricted only to pattern matching expressions, you can also use them on let-bindings.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5007.fs)]

<span data-ttu-id="35cd0-141">Önceki kodun çıktısı aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="35cd0-141">The output of the previous code is as follows:</span></span>

```
Hello, random citizen!
Hello, George!
```

## <a name="see-also"></a><span data-ttu-id="35cd0-142">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="35cd0-142">See also</span></span>

- [<span data-ttu-id="35cd0-143">F# Dili Başvurusu</span><span class="sxs-lookup"><span data-stu-id="35cd0-143">F# Language Reference</span></span>](index.md)
- [<span data-ttu-id="35cd0-144">Eşleşme İfadeleri</span><span class="sxs-lookup"><span data-stu-id="35cd0-144">Match Expressions</span></span>](match-expressions.md)
