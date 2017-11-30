---
title: "Parametreler ve Bağımsız Değişkenler (F#)"
description: "Parametreleri tanımlama ve bağımsız değişkenleri işlevleri, yöntemlere ve özelliklere geçirme için F # dil desteği hakkında bilgi edinin."
keywords: "Visual f #, f # işlevsel programlama"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 9b37a5c4-9263-4513-822a-fbb0d1004254
ms.openlocfilehash: 50f54bacd9ba7ec20a7151794734f93200df9f2d
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="parameters-and-arguments"></a><span data-ttu-id="5a2a9-104">Parametreler ve Bağımsız Değişkenler</span><span class="sxs-lookup"><span data-stu-id="5a2a9-104">Parameters and Arguments</span></span>

<span data-ttu-id="5a2a9-105">Bu konuda parametreleri tanımlama ve bağımsız değişkenleri işlevleri, yöntemlere ve özelliklere geçirme için dil desteği açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="5a2a9-105">This topic describes language support for defining parameters and passing arguments to functions, methods, and properties.</span></span> <span data-ttu-id="5a2a9-106">Nasıl başvuruya göre geçirme ve tanımlayın ve değişken sayıda bağımsız değişken sürebilir yöntemleri kullanma hakkında bilgi içerir.</span><span class="sxs-lookup"><span data-stu-id="5a2a9-106">It includes information about how to pass by reference, and how to define and use methods that can take a variable number of arguments.</span></span>


## <a name="parameters-and-arguments"></a><span data-ttu-id="5a2a9-107">Parametreler ve Bağımsız Değişkenler</span><span class="sxs-lookup"><span data-stu-id="5a2a9-107">Parameters and Arguments</span></span>
<span data-ttu-id="5a2a9-108">Terim *parametresi* sağlanacak beklenen değerler adlarını tanımlamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="5a2a9-108">The term *parameter* is used to describe the names for values that are expected to be supplied.</span></span> <span data-ttu-id="5a2a9-109">Terim *bağımsız değişkeni* her parametre için sağlanan değerler için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="5a2a9-109">The term *argument* is used for the values provided for each parameter.</span></span>

<span data-ttu-id="5a2a9-110">Parametre tanımlama grubu ya da curried form veya bazı ikisinin birleşimini belirtilebilir.</span><span class="sxs-lookup"><span data-stu-id="5a2a9-110">Parameters can be specified in tuple or curried form, or in some combination of the two.</span></span> <span data-ttu-id="5a2a9-111">Bir açık parametre adını kullanarak bağımsız değişkenler geçirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5a2a9-111">You can pass arguments by using an explicit parameter name.</span></span> <span data-ttu-id="5a2a9-112">Yöntem parametreleri isteğe bağlı olarak belirtilen ve varsayılan bir değer verilir.</span><span class="sxs-lookup"><span data-stu-id="5a2a9-112">Parameters of methods can be specified as optional and given a default value.</span></span>


## <a name="parameter-patterns"></a><span data-ttu-id="5a2a9-113">Parametre desenleri</span><span class="sxs-lookup"><span data-stu-id="5a2a9-113">Parameter Patterns</span></span>
<span data-ttu-id="5a2a9-114">İşlevler ve yöntemleri için sağlanan parametreler genel olarak, boşluklarla ayırarak desenleri alır.</span><span class="sxs-lookup"><span data-stu-id="5a2a9-114">Parameters supplied to functions and methods are, in general, patterns separated by spaces.</span></span> <span data-ttu-id="5a2a9-115">Temelde desenleri hiçbirini açıklanan, yani [eşleşme ifadeleri](match-expressions.md) parametre listesinde bir işlevi veya üye için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="5a2a9-115">This means that, in principle, any of the patterns described in [Match Expressions](match-expressions.md) can be used in a parameter list for a function or member.</span></span>

<span data-ttu-id="5a2a9-116">Yöntemleri genellikle argümanları tanımlama grubu formu kullanın.</span><span class="sxs-lookup"><span data-stu-id="5a2a9-116">Methods usually use the tuple form of passing arguments.</span></span> <span data-ttu-id="5a2a9-117">Tuple formun bağımsız değişkenler .NET yöntemlerinde geçirilir şekilde eşleştiğinden bunu diğer .NET dilleri perspektifinden daha anlaşılır bir sonuç uygular.</span><span class="sxs-lookup"><span data-stu-id="5a2a9-117">This achieves a clearer result from the perspective of other .NET languages because the tuple form matches the way arguments are passed in .NET methods.</span></span>

<span data-ttu-id="5a2a9-118">Curried form çoğunlukla kullanılarak oluşturulan işlevleri ile kullanılır `let` bağlar.</span><span class="sxs-lookup"><span data-stu-id="5a2a9-118">The curried form is most often used with functions created by using `let` bindings.</span></span>

<span data-ttu-id="5a2a9-119">Aşağıdaki yarı kodu tanımlama grubu ve curried bağımsız örnekleri gösterilir.</span><span class="sxs-lookup"><span data-stu-id="5a2a9-119">The following pseudocode shows examples of tuple and curried arguments.</span></span>

```fsharp
// Tuple form.
member this.SomeMethod(param1, param2) = ...
// Curried form.
let function1 param1 param2 = ...
```

<span data-ttu-id="5a2a9-120">Birleşik forms bazı bağımsız değişkenler tanımlama grupları ve bazı değil mümkündür.</span><span class="sxs-lookup"><span data-stu-id="5a2a9-120">Combined forms are possible when some arguments are in tuples and some are not.</span></span>

```fsharp
let function2 param1 (param2a, param2b) param3 = ...
```

<span data-ttu-id="5a2a9-121">Diğer desenleri parametre listelerinde de kullanılabilir, ancak parametre düzeni tüm olası girişleri eşleşmiyorsa olabilir tamamlanmamış bir eşleşme çalışma zamanında.</span><span class="sxs-lookup"><span data-stu-id="5a2a9-121">Other patterns can also be used in parameter lists, but if the parameter pattern does not match all possible inputs, there might be an incomplete match at run time.</span></span> <span data-ttu-id="5a2a9-122">Özel durum `MatchFailureException` bağımsız değişken değeri parametre listesinde belirtilen desenleri eşleşmediğinde oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="5a2a9-122">The exception `MatchFailureException` is generated when the value of an argument does not match the patterns specified in the parameter list.</span></span> <span data-ttu-id="5a2a9-123">Bir parametre düzeni için tam eşleşme izin veriyorsa derleyici bir uyarı verir.</span><span class="sxs-lookup"><span data-stu-id="5a2a9-123">The compiler issues a warning when a parameter pattern allows for incomplete matches.</span></span> <span data-ttu-id="5a2a9-124">En az bir desen parametre listeleri için yaygın olarak yararlıdır ve joker karakter deseni olmasıdır.</span><span class="sxs-lookup"><span data-stu-id="5a2a9-124">At least one other pattern is commonly useful for parameter lists, and that is the wildcard pattern.</span></span> <span data-ttu-id="5a2a9-125">Yalnızca sağlanan herhangi bir bağımsız değişken yok saymak istediğinizde bir parametre listesinde joker karakter deseni kullanın.</span><span class="sxs-lookup"><span data-stu-id="5a2a9-125">You use the wildcard pattern in a parameter list when you simply want to ignore any arguments that are supplied.</span></span> <span data-ttu-id="5a2a9-126">Aşağıdaki kodu bir bağımsız değişken listesinde joker karakter deseni kullanımını göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="5a2a9-126">The following code illustrates the use of the wildcard pattern in an argument list.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/parameters-and-arguments-1/snippet3801.fs)]

<span data-ttu-id="5a2a9-127">Aşağıdaki kod olduğu gibi bir dize dizisi olarak normal olarak sağlanan komut satırı bağımsız değişkenleri ilginizi olmadığında Joker karakter deseni geçirilen bağımsız değişken gerekmez olduğunca yararlı, örn. bir program için ana giriş noktası olabilir.</span><span class="sxs-lookup"><span data-stu-id="5a2a9-127">The wildcard pattern can be useful whenever you do not need the arguments passed in, such as in the main entry point to a program, when you are not interested in the command-line arguments that are normally supplied as a string array, as in the following code.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/parameters-and-arguments-1/snippet3802.fs)]

<span data-ttu-id="5a2a9-128">Bazen değişkenlerinde kullanılan diğer desenleri olan `as` düzeni ve ayrılmış birleşimler ve Etkin desenler ilişkili tanımlayıcı desenleri.</span><span class="sxs-lookup"><span data-stu-id="5a2a9-128">Other patterns that are sometimes used in arguments are the `as` pattern, and identifier patterns associated with discriminated unions and active patterns.</span></span> <span data-ttu-id="5a2a9-129">Tek durumda ayrılmış birleşim deseni gibi kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5a2a9-129">You can use the single-case discriminated union pattern as follows.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/parameters-and-arguments-1/snippet3803.fs)]

<span data-ttu-id="5a2a9-130">Çıktı aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="5a2a9-130">The output is as follows.</span></span>

```
Data begins at 0 and ends at 4 in string Et tu, Brute?
Et tu
```

<span data-ttu-id="5a2a9-131">Etkin desenler aşağıdaki örnekteki gibi istenen bir biçime dönüştürme bağımsız değişken olarak parametreler, örneğin, kullanışlı olabilir:</span><span class="sxs-lookup"><span data-stu-id="5a2a9-131">Active patterns can be useful as parameters, for example, when transforming an argument into a desired format, as in the following example:</span></span>

```fsharp
type Point = { x : float; y : float }

let (| Polar |) { x = x; y = y} =
    ( sqrt (x*x + y*y), System.Math.Atan (y/ x) )

let radius (Polar(r, _)) = r
let angle (Polar(_, theta)) = theta
```

<span data-ttu-id="5a2a9-132">Kullanabileceğiniz `as` aşağıdaki kod satırını gösterildiği gibi bir yerel değer olarak eşleşen bir değeri depolamak için desen.</span><span class="sxs-lookup"><span data-stu-id="5a2a9-132">You can use the `as` pattern to store a matched value as a local value, as is shown in the following line of code.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/parameters-and-arguments-1/snippet3805.fs)]

<span data-ttu-id="5a2a9-133">Bazen kullanılan başka bir düzen, işlev gövdesi olarak sağlayarak adlandırılmamış son bağımsız değişken ayrıldığında bir işlev, hemen örtük bağımsız bir desen eşleştirme gerçekleştiren bir lambda ifadesi yöneliktir.</span><span class="sxs-lookup"><span data-stu-id="5a2a9-133">Another pattern that is used occasionally is a function that leaves the last argument unnamed by providing, as the body of the function, a lambda expression that immediately performs a pattern match on the implicit argument.</span></span> <span data-ttu-id="5a2a9-134">Bu aşağıdaki satırlık bir kod örneğidir.</span><span class="sxs-lookup"><span data-stu-id="5a2a9-134">An example of this is the following line of code.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/parameters-and-arguments-1/snippet3804.fs)]

<span data-ttu-id="5a2a9-135">Bu kod, genel bir liste alır ve döndüren bir işlev tanımlar `true` liste boşsa ve `false` Aksi takdirde.</span><span class="sxs-lookup"><span data-stu-id="5a2a9-135">This code defines a function that takes a generic list and returns `true` if the list is empty, and `false` otherwise.</span></span> <span data-ttu-id="5a2a9-136">Bu tür teknikler kullanımını kod okumak daha zor hale getirebilir.</span><span class="sxs-lookup"><span data-stu-id="5a2a9-136">The use of such techniques can make code more difficult to read.</span></span>

<span data-ttu-id="5a2a9-137">Bazen, tamamlanmamış eşleşmeleri içeren desenleri faydalıdır, programınızı listelerinde yalnızca üç öğe olduğunu biliyorsanız, örneğin, aşağıdaki gibi bir desen parametre listesini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5a2a9-137">Occasionally, patterns that involve incomplete matches are useful, for example, if you know that the lists in your program have only three elements, you might use a pattern like the following in a parameter list.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/parameters-and-arguments-1/snippet3806.fs)]

<span data-ttu-id="5a2a9-138">Tamamlanmamış eşleşmeleri sahip desenleri kullanımını en iyi hızlı prototipi oluşturulurken ve diğer geçici kullanım için ayrılmıştır.</span><span class="sxs-lookup"><span data-stu-id="5a2a9-138">The use of patterns that have incomplete matches is best reserved for quick prototyping and other temporary uses.</span></span> <span data-ttu-id="5a2a9-139">Derleyici, bu tür kodu için bir uyarı verecek.</span><span class="sxs-lookup"><span data-stu-id="5a2a9-139">The compiler will issue a warning for such code.</span></span> <span data-ttu-id="5a2a9-140">Desenler tüm olası girdi genel durum kapak olamaz ve API bileşeni için uygun değildir.</span><span class="sxs-lookup"><span data-stu-id="5a2a9-140">Such patterns cannot cover the general case of all possible inputs and therefore are not suitable for component APIs.</span></span>

## <a name="named-arguments"></a><span data-ttu-id="5a2a9-141">Adlandırılmış bağımsız değişkenler</span><span class="sxs-lookup"><span data-stu-id="5a2a9-141">Named Arguments</span></span>
<span data-ttu-id="5a2a9-142">Yöntemleri için bağımsız bir virgülle ayrılmış bağımsız değişken listesinde konuma göre belirtilebilir veya bunların bir yönteme açıkça eşittir işareti ve geçirilmesi değeri adından, sağlayarak geçirilebilir.</span><span class="sxs-lookup"><span data-stu-id="5a2a9-142">Arguments for methods can be specified by position in a comma-separated argument list, or they can be passed to a method explicitly by providing the name, followed by an equal sign and the value to be passed in.</span></span> <span data-ttu-id="5a2a9-143">Adı sağlayarak belirtilmişse bildiriminde kullanılan ile farklı bir sırada yer alabilir.</span><span class="sxs-lookup"><span data-stu-id="5a2a9-143">If specified by providing the name, they can appear in a different order from that used in the declaration.</span></span>

<span data-ttu-id="5a2a9-144">Adlandırılmış bağımsız değişkenler kodunu daha okunabilir ve daha uyarlanabilir belirli türde bir yöntem parametreleri, sipariş API'sindeki değişiklikleri yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5a2a9-144">Named arguments can make code more readable and more adaptable to certain types of changes in the API, such as a reordering of method parameters.</span></span>

<span data-ttu-id="5a2a9-145">Adlandırılmış bağımsız değişkenler için değil yalnızca yöntemleri için verilir `let`-bağlı İşlevler, işlevi değerleri veya lambda ifadeleri.</span><span class="sxs-lookup"><span data-stu-id="5a2a9-145">Named arguments are allowed only for methods, not for `let`-bound functions, function values, or lambda expressions.</span></span>

<span data-ttu-id="5a2a9-146">Aşağıdaki kod örneğinde adlandırılmış bağımsız değişkenler kullanımını göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="5a2a9-146">The following code example demonstrates the use of named arguments.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/parameters-and-arguments-1/snippet3807.fs)]

<span data-ttu-id="5a2a9-147">Bir sınıf oluşturucu için bir çağrı adlandırılmış bağımsız değişkenler için benzer bir söz dizimi kullanarak sınıfın özelliklerinin değerlerini ayarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5a2a9-147">In a call to a class constructor, you can set the values of properties of the class by using a syntax similar to that of named arguments.</span></span> <span data-ttu-id="5a2a9-148">Aşağıdaki örnekte bu söz dizimini gösterir.</span><span class="sxs-lookup"><span data-stu-id="5a2a9-148">The following example shows this syntax.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet3506.fs)]

<span data-ttu-id="5a2a9-149">Daha fazla bilgi için bkz: [oluşturucular (F #)](https://msdn.microsoft.com/library/2cd0ed07-d214-4125-8317-4f288af99f05).</span><span class="sxs-lookup"><span data-stu-id="5a2a9-149">For more information, see [Constructors (F#)](https://msdn.microsoft.com/library/2cd0ed07-d214-4125-8317-4f288af99f05).</span></span>

## <a name="optional-parameters"></a><span data-ttu-id="5a2a9-150">İsteğe Bağlı Parametreler</span><span class="sxs-lookup"><span data-stu-id="5a2a9-150">Optional Parameters</span></span>
<span data-ttu-id="5a2a9-151">İsteğe bağlı parametresi bir yöntem için parametre adı önünde soru işareti kullanarak belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5a2a9-151">You can specify an optional parameter for a method by using a question mark in front of the parameter name.</span></span> <span data-ttu-id="5a2a9-152">İsteğe bağlı parametreler, F # seçeneği türü olarak yorumlanır, seçenek türleri, kullanarak seçmeleri istenir, normal şekilde sorgulayabilirsiniz şekilde bir `match` ifadesiyle `Some` ve `None`.</span><span class="sxs-lookup"><span data-stu-id="5a2a9-152">Optional parameters are interpreted as the F# option type, so you can query them in the regular way that option types are queried, by using a `match` expression with `Some` and `None`.</span></span> <span data-ttu-id="5a2a9-153">İsteğe bağlı parametreler kullanılarak oluşturulan işlevlerde üyeleri yalnızca üzerinde verilen `let` bağlar.</span><span class="sxs-lookup"><span data-stu-id="5a2a9-153">Optional parameters are permitted only on members, not on functions created by using `let` bindings.</span></span>

<span data-ttu-id="5a2a9-154">Bir işlev de kullanabilirsiniz `defaultArg`, isteğe bağlı bir bağımsız değişken varsayılan değerini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="5a2a9-154">You can also use a function `defaultArg`, which sets a default value of an optional argument.</span></span> <span data-ttu-id="5a2a9-155">`defaultArg` İşlev, ilk bağımsız değişken olarak isteğe bağlı bir parametre ve ikinci olarak varsayılan değerini alır.</span><span class="sxs-lookup"><span data-stu-id="5a2a9-155">The `defaultArg` function takes the optional parameter as the first argument and the default value as the second.</span></span>

<span data-ttu-id="5a2a9-156">Aşağıdaki örnek, isteğe bağlı parametreler kullanımını göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="5a2a9-156">The following example illustrates the use of optional parameters.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/parameters-and-arguments-1/snippet3808.fs)]

<span data-ttu-id="5a2a9-157">Çıktı aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="5a2a9-157">The output is as follows.</span></span>

```
Baud Rate: 9600 Duplex: Full Parity: false
Baud Rate: 4800 Duplex: Half Parity: false
Baud Rate: 300 Duplex: Half Parity: true
```

## <a name="passing-by-reference"></a><span data-ttu-id="5a2a9-158">Başvuruya göre geçirme</span><span class="sxs-lookup"><span data-stu-id="5a2a9-158">Passing by Reference</span></span>
<span data-ttu-id="5a2a9-159">F # destekler `byref` anahtar sözcüğü bir parametre başvuruya göre geçirilir belirtir.</span><span class="sxs-lookup"><span data-stu-id="5a2a9-159">F# supports the `byref` keyword, which specifies that a parameter is passed by reference.</span></span> <span data-ttu-id="5a2a9-160">Bu değer herhangi bir değişiklik işlevi yürütme sonrasında korunur anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="5a2a9-160">This means that any changes to the value are retained after the execution of the function.</span></span> <span data-ttu-id="5a2a9-161">İçin sağlanan değerlerden bir `byref` parametresi değişebilir olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="5a2a9-161">Values provided to a `byref` parameter must be mutable.</span></span> <span data-ttu-id="5a2a9-162">Alternatif olarak, uygun bir tür başvuru hücreleri geçirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5a2a9-162">Alternatively, you can pass reference cells of the appropriate type.</span></span>

<span data-ttu-id="5a2a9-163">Bir işlevden birden fazla değer döndürmek için bir yol olarak gelişen .NET dillerinde başvuruya göre geçirme.</span><span class="sxs-lookup"><span data-stu-id="5a2a9-163">Passing by reference in .NET languages evolved as a way to return more than one value from a function.</span></span> <span data-ttu-id="5a2a9-164">F #'ta yapabilir bu amaç için bir tanımlama grubu döndürür veya kesilebilir başvuru hücresi parametre olarak kullanın.</span><span class="sxs-lookup"><span data-stu-id="5a2a9-164">In F#, you can return a tuple for this purpose, or use a mutable reference cell as a parameter.</span></span> <span data-ttu-id="5a2a9-165">`byref` Parametresi .NET kitaplıkları ile birlikte çalışabilirlik için temel olarak sağlanır.</span><span class="sxs-lookup"><span data-stu-id="5a2a9-165">The `byref` parameter is mainly provided for interoperability with .NET libraries.</span></span>

<span data-ttu-id="5a2a9-166">Aşağıdaki örnekler kullanımını göstermek `byref` anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="5a2a9-166">The following examples illustrate the use of the `byref` keyword.</span></span> <span data-ttu-id="5a2a9-167">Parametre olarak bir başvuru hücresi kullandığınızda, gerekir adlandırılmış değeri olarak başvuru hücresi oluşturur ve parametre olarak kullanan, yalnızca eklemek dikkat edin `ref` yapılan ilk çağrıda gösterildiği gibi işleci `Increment` aşağıdaki kodda.</span><span class="sxs-lookup"><span data-stu-id="5a2a9-167">Note that when you use a reference cell as a parameter, you must create a reference cell as a named value and use that as the parameter, not just add the `ref` operator as shown in the first call to `Increment` in the following code.</span></span> <span data-ttu-id="5a2a9-168">Bir başvuru hücre oluşturma temel alan değeri bir kopyasını oluşturduğundan ilk çağrı yalnızca geçici bir değeri artırır.</span><span class="sxs-lookup"><span data-stu-id="5a2a9-168">Because creating a reference cell creates a copy of the underlying value, the first call just increments a temporary value.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/parameters-and-arguments-1/snippet3809.fs)]

<span data-ttu-id="5a2a9-169">Herhangi bir depolamak için dönüş değeri olarak bir tanımlama grubu kullanabilirsiniz `out` .NET kitaplığı yöntem parametreleri.</span><span class="sxs-lookup"><span data-stu-id="5a2a9-169">You can use a tuple as a return value to store any `out` parameters in .NET library methods.</span></span> <span data-ttu-id="5a2a9-170">Alternatif olarak, davranabilirsiniz `out` parametre olarak bir `byref` parametresi.</span><span class="sxs-lookup"><span data-stu-id="5a2a9-170">Alternatively, you can treat the `out` parameter as a `byref` parameter.</span></span> <span data-ttu-id="5a2a9-171">Aşağıdaki kod örneği, her iki yolu gösterir.</span><span class="sxs-lookup"><span data-stu-id="5a2a9-171">The following code example illustrates both ways.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/parameters-and-arguments-1/snippet3810.fs)]

## <a name="parameter-arrays"></a><span data-ttu-id="5a2a9-172">Parametre Dizileri</span><span class="sxs-lookup"><span data-stu-id="5a2a9-172">Parameter Arrays</span></span>
<span data-ttu-id="5a2a9-173">Bazen rastgele sayıda heterojen türü parametre isteyen bir işlev tanımlamak gereklidir.</span><span class="sxs-lookup"><span data-stu-id="5a2a9-173">Occasionally it is necessary to define a function that takes an arbitrary number of parameters of heterogeneous type.</span></span> <span data-ttu-id="5a2a9-174">Kullanılabilir tüm türleri için hesap için tüm olası aşırı yüklenmiş yöntemler oluşturmak mümkün olmayacaktır.</span><span class="sxs-lookup"><span data-stu-id="5a2a9-174">It would not be practical to create all the possible overloaded methods to account for all the types that could be used.</span></span> <span data-ttu-id="5a2a9-175">.NET uygulamaları için parametre dizisi özelliği aracılığıyla böyle yöntemleri için destek sağlar.</span><span class="sxs-lookup"><span data-stu-id="5a2a9-175">The .NET implementations provide support for such methods through the parameter array feature.</span></span> <span data-ttu-id="5a2a9-176">Bir parametre dizisi kendi İmzada gereken bir yöntem rastgele sayıda parametre ile sağlanabilir.</span><span class="sxs-lookup"><span data-stu-id="5a2a9-176">A method that takes a parameter array in its signature can be provided with an arbitrary number of parameters.</span></span> <span data-ttu-id="5a2a9-177">Parametreleri bir diziye yerleştirilir.</span><span class="sxs-lookup"><span data-stu-id="5a2a9-177">The parameters are put into an array.</span></span> <span data-ttu-id="5a2a9-178">Dizi öğelerin türü işlevine geçirilen parametre türleri belirler.</span><span class="sxs-lookup"><span data-stu-id="5a2a9-178">The type of the array elements determines the parameter types that can be passed to the function.</span></span> <span data-ttu-id="5a2a9-179">Parametre dizisi ile tanımlarsanız `System.Object` öğe türü olarak istemci kodu herhangi bir tür değerleri geçirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5a2a9-179">If you define the parameter array with `System.Object` as the element type, then client code can pass values of any type.</span></span>

<span data-ttu-id="5a2a9-180">F #'ta parametre dizileri, yalnızca yöntemleri tanımlanabilir.</span><span class="sxs-lookup"><span data-stu-id="5a2a9-180">In F#, parameter arrays can only be defined in methods.</span></span> <span data-ttu-id="5a2a9-181">Tek başına işlevlerde veya modüllerde tanımlı işlevler kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="5a2a9-181">They cannot be used in standalone functions or functions that are defined in modules.</span></span>

<span data-ttu-id="5a2a9-182">Bir parametre dizisi kullanarak tanımladığınız `ParamArray` özniteliği.</span><span class="sxs-lookup"><span data-stu-id="5a2a9-182">You define a parameter array by using the `ParamArray` attribute.</span></span> <span data-ttu-id="5a2a9-183">`ParamArray` Özniteliği yalnızca son parametre uygulanabilir.</span><span class="sxs-lookup"><span data-stu-id="5a2a9-183">The `ParamArray` attribute can only be applied to the last parameter.</span></span>

<span data-ttu-id="5a2a9-184">Aşağıdaki kod, her iki çağırma F bir parametre dizisi alan yöntemi olan #'de bir parametre dizisi ve bir tür tanımını alır .NET yöntemi gösterir.</span><span class="sxs-lookup"><span data-stu-id="5a2a9-184">The following code illustrates both calling a .NET method that takes a parameter array and the definition of a type in F# that has a method that takes a parameter array.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/parameters-and-arguments-2/snippet3811.fs)]

<span data-ttu-id="5a2a9-185">Bir proje ile çalıştırdığınızda, önceki kod çıkışı aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="5a2a9-185">When run in a project, the output of the previous code is as follows:</span></span>

```
a 1 10 Hello world 1 True
"a"
1
10.0
"Hello world"
1u
true
```

## <a name="see-also"></a><span data-ttu-id="5a2a9-186">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="5a2a9-186">See Also</span></span>
[<span data-ttu-id="5a2a9-187">Üyeleri</span><span class="sxs-lookup"><span data-stu-id="5a2a9-187">Members</span></span>](members/index.md)
