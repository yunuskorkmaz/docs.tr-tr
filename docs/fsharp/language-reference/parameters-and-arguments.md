---
title: Parametreler ve Bağımsız Değişkenler (F#)
description: 'Parametreleri tanımlama ve bağımsız değişkenleri işlevleri, yöntemlere ve özelliklere geçirme için F # dil desteği hakkında bilgi edinin.'
ms.date: 05/16/2016
ms.openlocfilehash: a1e2a70ca560bbb09d2cd10f47485cbe5c5e029d
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/14/2018
ms.locfileid: "45591665"
---
# <a name="parameters-and-arguments"></a><span data-ttu-id="b146e-103">Parametreler ve Bağımsız Değişkenler</span><span class="sxs-lookup"><span data-stu-id="b146e-103">Parameters and Arguments</span></span>

<span data-ttu-id="b146e-104">Bu konuda tanımlayan parametreler ve bağımsız değişkenleri işlevleri, yöntemlere ve özelliklere geçirme için dil desteği açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="b146e-104">This topic describes language support for defining parameters and passing arguments to functions, methods, and properties.</span></span> <span data-ttu-id="b146e-105">Başvuruya göre nasıl ve tanımlayın ve değişken sayıda bağımsız değişken alabilir yöntemleri kullanma hakkında bilgiler içerir.</span><span class="sxs-lookup"><span data-stu-id="b146e-105">It includes information about how to pass by reference, and how to define and use methods that can take a variable number of arguments.</span></span>

## <a name="parameters-and-arguments"></a><span data-ttu-id="b146e-106">Parametreler ve Bağımsız Değişkenler</span><span class="sxs-lookup"><span data-stu-id="b146e-106">Parameters and Arguments</span></span>

<span data-ttu-id="b146e-107">Terim *parametre* sağlanacak beklenen değerleri adlarını tanımlamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="b146e-107">The term *parameter* is used to describe the names for values that are expected to be supplied.</span></span> <span data-ttu-id="b146e-108">Terim *bağımsız değişken* her parametre için sağlanan değerler için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="b146e-108">The term *argument* is used for the values provided for each parameter.</span></span>

<span data-ttu-id="b146e-109">Parametreleri, tanımlama grubu ya da curried form veya ikisinin birleşimi belirtilebilir.</span><span class="sxs-lookup"><span data-stu-id="b146e-109">Parameters can be specified in tuple or curried form, or in some combination of the two.</span></span> <span data-ttu-id="b146e-110">Bir açık parametre adını kullanarak, bağımsız değişkenler geçirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b146e-110">You can pass arguments by using an explicit parameter name.</span></span> <span data-ttu-id="b146e-111">Yöntemlerin parametreleri isteğe bağlı olarak belirtilebilir ve bir varsayılan değer verilir.</span><span class="sxs-lookup"><span data-stu-id="b146e-111">Parameters of methods can be specified as optional and given a default value.</span></span>

## <a name="parameter-patterns"></a><span data-ttu-id="b146e-112">Parametre desenleri</span><span class="sxs-lookup"><span data-stu-id="b146e-112">Parameter Patterns</span></span>

<span data-ttu-id="b146e-113">İşlevlere ve metotlara için sağlanan parametreler, genel olarak, boşluklarla ayırarak desenleri alır.</span><span class="sxs-lookup"><span data-stu-id="b146e-113">Parameters supplied to functions and methods are, in general, patterns separated by spaces.</span></span> <span data-ttu-id="b146e-114">İlkesi, herhangi bir kalıpla açıklanan, yani [eşleşme ifadeleri](match-expressions.md) bir işlevi veya üye için parametre listesinde kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="b146e-114">This means that, in principle, any of the patterns described in [Match Expressions](match-expressions.md) can be used in a parameter list for a function or member.</span></span>

<span data-ttu-id="b146e-115">Yöntemler, genellikle bağımsız değişkenleri geçirme demet biçimini kullanın.</span><span class="sxs-lookup"><span data-stu-id="b146e-115">Methods usually use the tuple form of passing arguments.</span></span> <span data-ttu-id="b146e-116">Kayıt formu .NET yöntemleri bağımsız değişkenler geçirilir şekilde eşleştiği için bu diğer .NET dilleri perspektifinden NET bir sonuç elde edilir.</span><span class="sxs-lookup"><span data-stu-id="b146e-116">This achieves a clearer result from the perspective of other .NET languages because the tuple form matches the way arguments are passed in .NET methods.</span></span>

<span data-ttu-id="b146e-117">Formun curried işlevleri kullanılarak oluşturulan ile en sık kullanılan `let` bağlar.</span><span class="sxs-lookup"><span data-stu-id="b146e-117">The curried form is most often used with functions created by using `let` bindings.</span></span>

<span data-ttu-id="b146e-118">Aşağıdaki sözde kod tanımlama grubu ve curried bağımsız örneklerini gösterir.</span><span class="sxs-lookup"><span data-stu-id="b146e-118">The following pseudocode shows examples of tuple and curried arguments.</span></span>

```fsharp
// Tuple form.
member this.SomeMethod(param1, param2) = ...
// Curried form.
let function1 param1 param2 = ...
```

<span data-ttu-id="b146e-119">Birleşik forms bazı bağımsız değişkenler de tanımlama gruplarına ve bazı değil mümkündür.</span><span class="sxs-lookup"><span data-stu-id="b146e-119">Combined forms are possible when some arguments are in tuples and some are not.</span></span>

```fsharp
let function2 param1 (param2a, param2b) param3 = ...
```

<span data-ttu-id="b146e-120">Diğer desenler içinde parametre listeleri de kullanılabilir, ancak parametre düzeni tüm olası girişleri eşleşmiyorsa olabilir bir tam eşleşme çalışma zamanında.</span><span class="sxs-lookup"><span data-stu-id="b146e-120">Other patterns can also be used in parameter lists, but if the parameter pattern does not match all possible inputs, there might be an incomplete match at run time.</span></span> <span data-ttu-id="b146e-121">Özel durum `MatchFailureException` bir bağımsız değişkenin değeri parametre listesinde belirtilen desenleri eşleşmediğinde oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="b146e-121">The exception `MatchFailureException` is generated when the value of an argument does not match the patterns specified in the parameter list.</span></span> <span data-ttu-id="b146e-122">Parametre düzeni için eksik eşleşmeler izin veriyorsa, derleyici bir uyarı verir.</span><span class="sxs-lookup"><span data-stu-id="b146e-122">The compiler issues a warning when a parameter pattern allows for incomplete matches.</span></span> <span data-ttu-id="b146e-123">Diğer düzen en az bir parametre listeleri için yaygın olarak kullanışlıdır ve joker karakter deseni.</span><span class="sxs-lookup"><span data-stu-id="b146e-123">At least one other pattern is commonly useful for parameter lists, and that is the wildcard pattern.</span></span> <span data-ttu-id="b146e-124">Yalnızca sağlanan herhangi bir bağımsız değişken yok saymak istediğinizde bir parametre listesinde joker karakter deseni kullanın.</span><span class="sxs-lookup"><span data-stu-id="b146e-124">You use the wildcard pattern in a parameter list when you simply want to ignore any arguments that are supplied.</span></span> <span data-ttu-id="b146e-125">Aşağıdaki kodu bir bağımsız değişken listesinde joker karakter deseni kullanımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="b146e-125">The following code illustrates the use of the wildcard pattern in an argument list.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/parameters-and-arguments-1/snippet3801.fs)]

<span data-ttu-id="b146e-126">Aşağıdaki kodda gösterildiği gibi bir dize dizisi olarak normal olarak sağlanan komut satırı bağımsız değişkenleri ilginizi olmadığında yararlı geçirilen bağımsız değişkenlerdeki ihtiyacınız olduğunda, bir programa ana girdi noktası olduğu gibi joker karakter deseni olabilir.</span><span class="sxs-lookup"><span data-stu-id="b146e-126">The wildcard pattern can be useful whenever you do not need the arguments passed in, such as in the main entry point to a program, when you are not interested in the command-line arguments that are normally supplied as a string array, as in the following code.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/parameters-and-arguments-1/snippet3802.fs)]

<span data-ttu-id="b146e-127">Bağımsız değişkenler bazen kullanılan diğer desenler `as` deseni ve ayrılmış birleşimler ve Etkin desenler ilişkili tanımlayıcı desenler.</span><span class="sxs-lookup"><span data-stu-id="b146e-127">Other patterns that are sometimes used in arguments are the `as` pattern, and identifier patterns associated with discriminated unions and active patterns.</span></span> <span data-ttu-id="b146e-128">Tek örneği ayrılmış birleşim deseni şu şekilde kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b146e-128">You can use the single-case discriminated union pattern as follows.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/parameters-and-arguments-1/snippet3803.fs)]

<span data-ttu-id="b146e-129">Çıktı aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="b146e-129">The output is as follows.</span></span>

```
Data begins at 0 and ends at 4 in string Et tu, Brute?
Et tu
```

<span data-ttu-id="b146e-130">Etkin desenler, bağımsız değişken aşağıdaki örnekte olduğu gibi istediğiniz bir biçime dönüştürme, parametre olarak, örneğin, yararlı olabilir:</span><span class="sxs-lookup"><span data-stu-id="b146e-130">Active patterns can be useful as parameters, for example, when transforming an argument into a desired format, as in the following example:</span></span>

```fsharp
type Point = { x : float; y : float }

let (| Polar |) { x = x; y = y} =
    ( sqrt (x*x + y*y), System.Math.Atan (y/ x) )

let radius (Polar(r, _)) = r
let angle (Polar(_, theta)) = theta
```

<span data-ttu-id="b146e-131">Kullanabileceğiniz `as` kod aşağıdaki satırda gösterildiği gibi yerel bir değer olarak, eşleşen bir değeri depolamak için desen.</span><span class="sxs-lookup"><span data-stu-id="b146e-131">You can use the `as` pattern to store a matched value as a local value, as is shown in the following line of code.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/parameters-and-arguments-1/snippet3805.fs)]

<span data-ttu-id="b146e-132">Nadiren kullanılan başka bir desendir son bağımsız değişken, işlev gövdesi olarak sağlayarak adlandırılmamış ayrıldığında bir işlev, bir lambda ifadesi hemen örtük bağımsız değişken bir desen eşleştirmesi gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="b146e-132">Another pattern that is used occasionally is a function that leaves the last argument unnamed by providing, as the body of the function, a lambda expression that immediately performs a pattern match on the implicit argument.</span></span> <span data-ttu-id="b146e-133">Buna örnek olarak aşağıdaki kod satırını ' dir.</span><span class="sxs-lookup"><span data-stu-id="b146e-133">An example of this is the following line of code.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/parameters-and-arguments-1/snippet3804.fs)]

<span data-ttu-id="b146e-134">Bu kod, genel bir liste alan ve döndüren bir işlev tanımlar `true` liste boşsa ve `false` Aksi takdirde.</span><span class="sxs-lookup"><span data-stu-id="b146e-134">This code defines a function that takes a generic list and returns `true` if the list is empty, and `false` otherwise.</span></span> <span data-ttu-id="b146e-135">Bu tür teknikler kullanımını kod okumak daha zor hale getirebilir.</span><span class="sxs-lookup"><span data-stu-id="b146e-135">The use of such techniques can make code more difficult to read.</span></span>

<span data-ttu-id="b146e-136">Bazen, eksik eşleşmeler içeren desenleri kullanışlıdır, programınızdaki listeleri yalnızca üç öğe olduğunu biliyorsanız, örneğin, bir desen aşağıdaki gibi bir parametre listesinde kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b146e-136">Occasionally, patterns that involve incomplete matches are useful, for example, if you know that the lists in your program have only three elements, you might use a pattern like the following in a parameter list.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/parameters-and-arguments-1/snippet3806.fs)]

<span data-ttu-id="b146e-137">Tam eşleşme sahip desenleri kullanımını en iyi hızlı prototip oluşturma ve geçici diğer kullanımlar için ayrılmıştır.</span><span class="sxs-lookup"><span data-stu-id="b146e-137">The use of patterns that have incomplete matches is best reserved for quick prototyping and other temporary uses.</span></span> <span data-ttu-id="b146e-138">Derleyici bu tür kod için bir uyarı verir.</span><span class="sxs-lookup"><span data-stu-id="b146e-138">The compiler will issue a warning for such code.</span></span> <span data-ttu-id="b146e-139">Desenler, tüm olası girişleri genel durumunun kapsamamaktadır ve bileşen API'leri için uygun değildir.</span><span class="sxs-lookup"><span data-stu-id="b146e-139">Such patterns cannot cover the general case of all possible inputs and therefore are not suitable for component APIs.</span></span>

## <a name="named-arguments"></a><span data-ttu-id="b146e-140">Adlandırılmış bağımsız değişkenler</span><span class="sxs-lookup"><span data-stu-id="b146e-140">Named Arguments</span></span>

<span data-ttu-id="b146e-141">Bağımsız değişkenler yöntemleri için bir virgülle ayrılmış bağımsız değişken listesindeki konumu ile belirtilebilir veya bunlar bir yönteme açıkça ardından bir eşittir işareti ve geçirilmesi değer adı sağlayarak geçirilebilir.</span><span class="sxs-lookup"><span data-stu-id="b146e-141">Arguments for methods can be specified by position in a comma-separated argument list, or they can be passed to a method explicitly by providing the name, followed by an equal sign and the value to be passed in.</span></span> <span data-ttu-id="b146e-142">Belirtilen ad sağlayarak, bildirimde kullanılan ile farklı bir sırada görünebilir.</span><span class="sxs-lookup"><span data-stu-id="b146e-142">If specified by providing the name, they can appear in a different order from that used in the declaration.</span></span>

<span data-ttu-id="b146e-143">Adlandırılmış bağımsız değişkenler kod daha okunabilir ve uyarlanabilir daha belirli türde bir yöntem parametreleri, yeniden sıralama API'sindeki değişiklikler yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b146e-143">Named arguments can make code more readable and more adaptable to certain types of changes in the API, such as a reordering of method parameters.</span></span>

<span data-ttu-id="b146e-144">Adlandırılmış bağımsız değişkenler için değil yalnızca yöntemleri için verilir `let`-bağlı İşlevler, işlev değerleri veya lambda ifadeleri.</span><span class="sxs-lookup"><span data-stu-id="b146e-144">Named arguments are allowed only for methods, not for `let`-bound functions, function values, or lambda expressions.</span></span>

<span data-ttu-id="b146e-145">Aşağıdaki kod örneği, adlandırılmış bağımsız değişkenler kullanımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="b146e-145">The following code example demonstrates the use of named arguments.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/parameters-and-arguments-1/snippet3807.fs)]

<span data-ttu-id="b146e-146">Bir sınıf oluşturucusuna bir çağrı adlandırılmış bağımsız değişkenler için benzer bir sözdizimi kullanarak sınıfın özelliklerinin değerlerini ayarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b146e-146">In a call to a class constructor, you can set the values of properties of the class by using a syntax similar to that of named arguments.</span></span> <span data-ttu-id="b146e-147">Aşağıdaki örnek bu söz dizimini gösterir.</span><span class="sxs-lookup"><span data-stu-id="b146e-147">The following example shows this syntax.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet3506.fs)]

<span data-ttu-id="b146e-148">Daha fazla bilgi için [oluşturucular (F #)](https://msdn.microsoft.com/library/2cd0ed07-d214-4125-8317-4f288af99f05).</span><span class="sxs-lookup"><span data-stu-id="b146e-148">For more information, see [Constructors (F#)](https://msdn.microsoft.com/library/2cd0ed07-d214-4125-8317-4f288af99f05).</span></span>

## <a name="optional-parameters"></a><span data-ttu-id="b146e-149">İsteğe Bağlı Parametreler</span><span class="sxs-lookup"><span data-stu-id="b146e-149">Optional Parameters</span></span>

<span data-ttu-id="b146e-150">İsteğe bağlı parametresi bir yöntem için parametre adının önüne bir soru işareti kullanarak belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b146e-150">You can specify an optional parameter for a method by using a question mark in front of the parameter name.</span></span> <span data-ttu-id="b146e-151">İsteğe bağlı parametreler, F # seçeneği türü olarak yorumlanır, seçenek türleri, kullanarak sorgulanır, normal şekilde sorgulayabilmesi bir `match` ifadesiyle `Some` ve `None`.</span><span class="sxs-lookup"><span data-stu-id="b146e-151">Optional parameters are interpreted as the F# option type, so you can query them in the regular way that option types are queried, by using a `match` expression with `Some` and `None`.</span></span> <span data-ttu-id="b146e-152">İsteğe bağlı parametreler kullanılarak oluşturulan işlevleri, üye üzerinde yalnızca verilen `let` bağlar.</span><span class="sxs-lookup"><span data-stu-id="b146e-152">Optional parameters are permitted only on members, not on functions created by using `let` bindings.</span></span>

<span data-ttu-id="b146e-153">Bir işlev de kullanabilirsiniz `defaultArg`, isteğe bağlı varsayılan değerini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="b146e-153">You can also use a function `defaultArg`, which sets a default value of an optional argument.</span></span> <span data-ttu-id="b146e-154">`defaultArg` İşlevi isteğe bağlı parametre olarak ilk bağımsız değişken ve varsayılan değer olarak saniye alır.</span><span class="sxs-lookup"><span data-stu-id="b146e-154">The `defaultArg` function takes the optional parameter as the first argument and the default value as the second.</span></span>

<span data-ttu-id="b146e-155">Aşağıdaki örnek, isteğe bağlı parametreler kullanımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="b146e-155">The following example illustrates the use of optional parameters.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/parameters-and-arguments-1/snippet3808.fs)]

<span data-ttu-id="b146e-156">Çıktı aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="b146e-156">The output is as follows.</span></span>

```
Baud Rate: 9600 Duplex: Full Parity: false
Baud Rate: 4800 Duplex: Half Parity: false
Baud Rate: 300 Duplex: Half Parity: true
```

## <a name="passing-by-reference"></a><span data-ttu-id="b146e-157">Başvuruya göre geçirme</span><span class="sxs-lookup"><span data-stu-id="b146e-157">Passing by Reference</span></span>

<span data-ttu-id="b146e-158">Bir F # değere Başvuruya göre geçirme içerir [zkratka](byrefs.md), Yönetilen işaretçi türleri olduğu.</span><span class="sxs-lookup"><span data-stu-id="b146e-158">Passing an F# value by reference involves [byrefs](byrefs.md), which are managed pointer types.</span></span> <span data-ttu-id="b146e-159">Kılavuz, hangi tür kullanmak aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="b146e-159">Guidance for which type to use is as follows:</span></span>

* <span data-ttu-id="b146e-160">Kullanım `inref<'T>` yalnızca işaretçi okumak gerekiyorsa.</span><span class="sxs-lookup"><span data-stu-id="b146e-160">Use `inref<'T>` if you only need to read the pointer.</span></span>
* <span data-ttu-id="b146e-161">Kullanım `outref<'T>` yalnızca işaretçi yazmak gerekiyorsa.</span><span class="sxs-lookup"><span data-stu-id="b146e-161">Use `outref<'T>` if you only need to write to the pointer.</span></span>
* <span data-ttu-id="b146e-162">Kullanım `byref<'T>` hem okuma hem de yazma işaretçisi gerekiyorsa.</span><span class="sxs-lookup"><span data-stu-id="b146e-162">Use `byref<'T>` if you need to both read from and write to the pointer.</span></span>

```fsharp
let example1 (x: inref<int>) = printfn "It's %d" x

let example2 (x: outref<int>) = x <- x + 1

let example3 (x: byref<int>) =
    printfn "It'd %d" x
    x <- x + 1

// No need to make it mutable, since it's read-only
let x = 1
example1 &x

// Needs to be mutable, since we write to it
let mutable y = 2
example2 &y
example3 &y // Now 'y' is 3
```

<span data-ttu-id="b146e-163">Parametre bir işaretçi ve değer değişebilir olduğundan, işlevi yürütme sonrasında değeri herhangi bir değişiklik korunur.</span><span class="sxs-lookup"><span data-stu-id="b146e-163">Because the parameter is a pointer and the value is mutable, any changes to the value are retained after the execution of the function.</span></span>

<span data-ttu-id="b146e-164">Tüm depolamak için bir dönüş değeri olarak bir tanımlama grubu kullanabilirsiniz `out` .NET kitaplığı yöntem parametreleri.</span><span class="sxs-lookup"><span data-stu-id="b146e-164">You can use a tuple as a return value to store any `out` parameters in .NET library methods.</span></span> <span data-ttu-id="b146e-165">Alternatif olarak davranabileceğiniz `out` parametre olarak bir `byref` parametresi.</span><span class="sxs-lookup"><span data-stu-id="b146e-165">Alternatively, you can treat the `out` parameter as a `byref` parameter.</span></span> <span data-ttu-id="b146e-166">Aşağıdaki kod örneği iki yolunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="b146e-166">The following code example illustrates both ways.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/parameters-and-arguments-1/snippet3810.fs)]

## <a name="parameter-arrays"></a><span data-ttu-id="b146e-167">Parametre Dizileri</span><span class="sxs-lookup"><span data-stu-id="b146e-167">Parameter Arrays</span></span>

<span data-ttu-id="b146e-168">Bazen tercihe bağlı sayıda heterojen türünde parametre alan bir işlev tanımlamak gereklidir.</span><span class="sxs-lookup"><span data-stu-id="b146e-168">Occasionally it is necessary to define a function that takes an arbitrary number of parameters of heterogeneous type.</span></span> <span data-ttu-id="b146e-169">Kullanılabilen tüm türleri için hesap için tüm olası aşırı yüklenmiş yöntemler oluşturmak pratik olmaz.</span><span class="sxs-lookup"><span data-stu-id="b146e-169">It would not be practical to create all the possible overloaded methods to account for all the types that could be used.</span></span> <span data-ttu-id="b146e-170">.NET uygulamaları için parametre dizisi özelliği aracılığıyla bu tür yöntemler için destek sağlar.</span><span class="sxs-lookup"><span data-stu-id="b146e-170">The .NET implementations provide support for such methods through the parameter array feature.</span></span> <span data-ttu-id="b146e-171">Bir parametre dizisi içinde imzasını alan bir yöntem rastgele sayıda parametre ile sağlanabilir.</span><span class="sxs-lookup"><span data-stu-id="b146e-171">A method that takes a parameter array in its signature can be provided with an arbitrary number of parameters.</span></span> <span data-ttu-id="b146e-172">Parametreler, bir dizi içine yerleştirilir.</span><span class="sxs-lookup"><span data-stu-id="b146e-172">The parameters are put into an array.</span></span> <span data-ttu-id="b146e-173">Dizi öğelerinin türü, işleve geçirilen parametre türleri belirler.</span><span class="sxs-lookup"><span data-stu-id="b146e-173">The type of the array elements determines the parameter types that can be passed to the function.</span></span> <span data-ttu-id="b146e-174">Parametre dizisi ile tanımlarsanız `System.Object` öğe türü istemci kodu her türden değer geçirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b146e-174">If you define the parameter array with `System.Object` as the element type, then client code can pass values of any type.</span></span>

<span data-ttu-id="b146e-175">F #'ta parametre dizileri, yalnızca yöntemlerdeki tanımlanabilir.</span><span class="sxs-lookup"><span data-stu-id="b146e-175">In F#, parameter arrays can only be defined in methods.</span></span> <span data-ttu-id="b146e-176">Tek başına işlevleri veya modül içinde tanımlanan işlevleri kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="b146e-176">They cannot be used in standalone functions or functions that are defined in modules.</span></span>

<span data-ttu-id="b146e-177">Bir parametre dizisi kullanarak tanımladığınız `ParamArray` özniteliği.</span><span class="sxs-lookup"><span data-stu-id="b146e-177">You define a parameter array by using the `ParamArray` attribute.</span></span> <span data-ttu-id="b146e-178">`ParamArray` Özniteliği yalnızca en son parametreye uygulanabilir.</span><span class="sxs-lookup"><span data-stu-id="b146e-178">The `ParamArray` attribute can only be applied to the last parameter.</span></span>

<span data-ttu-id="b146e-179">Aşağıdaki kod, her iki arama alan bir parametre dizisi ve bir tür tanımını içeren bir parametre dizisi alan bir yöntem içinde F # .NET yöntemi gösterir.</span><span class="sxs-lookup"><span data-stu-id="b146e-179">The following code illustrates both calling a .NET method that takes a parameter array and the definition of a type in F# that has a method that takes a parameter array.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/parameters-and-arguments-2/snippet3811.fs)]

<span data-ttu-id="b146e-180">Bir projeyi çalıştırdığınızda, önceki kodun çıktısı aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="b146e-180">When run in a project, the output of the previous code is as follows:</span></span>

```console
a 1 10 Hello world 1 True
"a"
1
10.0
"Hello world"
1u
true
```

## <a name="see-also"></a><span data-ttu-id="b146e-181">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b146e-181">See also</span></span>

- [<span data-ttu-id="b146e-182">Üyeler</span><span class="sxs-lookup"><span data-stu-id="b146e-182">Members</span></span>](members/index.md)
