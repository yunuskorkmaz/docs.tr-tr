---
title: Parametreler ve Bağımsız Değişkenler (F#)
description: 'Parametreleri tanımlama ve bağımsız değişkenleri işlevleri, yöntemlere ve özelliklere geçirme için F # dil desteği hakkında bilgi edinin.'
ms.date: 05/16/2016
ms.openlocfilehash: 9744339110314e4e6b3c3cf8d49b1c988bc25e3c
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2018
ms.locfileid: "43471987"
---
# <a name="parameters-and-arguments"></a><span data-ttu-id="8ebde-103">Parametreler ve Bağımsız Değişkenler</span><span class="sxs-lookup"><span data-stu-id="8ebde-103">Parameters and Arguments</span></span>

<span data-ttu-id="8ebde-104">Bu konuda tanımlayan parametreler ve bağımsız değişkenleri işlevleri, yöntemlere ve özelliklere geçirme için dil desteği açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="8ebde-104">This topic describes language support for defining parameters and passing arguments to functions, methods, and properties.</span></span> <span data-ttu-id="8ebde-105">Başvuruya göre nasıl ve tanımlayın ve değişken sayıda bağımsız değişken alabilir yöntemleri kullanma hakkında bilgiler içerir.</span><span class="sxs-lookup"><span data-stu-id="8ebde-105">It includes information about how to pass by reference, and how to define and use methods that can take a variable number of arguments.</span></span>


## <a name="parameters-and-arguments"></a><span data-ttu-id="8ebde-106">Parametreler ve Bağımsız Değişkenler</span><span class="sxs-lookup"><span data-stu-id="8ebde-106">Parameters and Arguments</span></span>
<span data-ttu-id="8ebde-107">Terim *parametre* sağlanacak beklenen değerleri adlarını tanımlamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="8ebde-107">The term *parameter* is used to describe the names for values that are expected to be supplied.</span></span> <span data-ttu-id="8ebde-108">Terim *bağımsız değişken* her parametre için sağlanan değerler için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="8ebde-108">The term *argument* is used for the values provided for each parameter.</span></span>

<span data-ttu-id="8ebde-109">Parametreleri, tanımlama grubu ya da curried form veya ikisinin birleşimi belirtilebilir.</span><span class="sxs-lookup"><span data-stu-id="8ebde-109">Parameters can be specified in tuple or curried form, or in some combination of the two.</span></span> <span data-ttu-id="8ebde-110">Bir açık parametre adını kullanarak, bağımsız değişkenler geçirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8ebde-110">You can pass arguments by using an explicit parameter name.</span></span> <span data-ttu-id="8ebde-111">Yöntemlerin parametreleri isteğe bağlı olarak belirtilebilir ve bir varsayılan değer verilir.</span><span class="sxs-lookup"><span data-stu-id="8ebde-111">Parameters of methods can be specified as optional and given a default value.</span></span>


## <a name="parameter-patterns"></a><span data-ttu-id="8ebde-112">Parametre desenleri</span><span class="sxs-lookup"><span data-stu-id="8ebde-112">Parameter Patterns</span></span>
<span data-ttu-id="8ebde-113">İşlevlere ve metotlara için sağlanan parametreler, genel olarak, boşluklarla ayırarak desenleri alır.</span><span class="sxs-lookup"><span data-stu-id="8ebde-113">Parameters supplied to functions and methods are, in general, patterns separated by spaces.</span></span> <span data-ttu-id="8ebde-114">İlkesi, herhangi bir kalıpla açıklanan, yani [eşleşme ifadeleri](match-expressions.md) bir işlevi veya üye için parametre listesinde kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="8ebde-114">This means that, in principle, any of the patterns described in [Match Expressions](match-expressions.md) can be used in a parameter list for a function or member.</span></span>

<span data-ttu-id="8ebde-115">Yöntemler, genellikle bağımsız değişkenleri geçirme demet biçimini kullanın.</span><span class="sxs-lookup"><span data-stu-id="8ebde-115">Methods usually use the tuple form of passing arguments.</span></span> <span data-ttu-id="8ebde-116">Kayıt formu .NET yöntemleri bağımsız değişkenler geçirilir şekilde eşleştiği için bu diğer .NET dilleri perspektifinden NET bir sonuç elde edilir.</span><span class="sxs-lookup"><span data-stu-id="8ebde-116">This achieves a clearer result from the perspective of other .NET languages because the tuple form matches the way arguments are passed in .NET methods.</span></span>

<span data-ttu-id="8ebde-117">Formun curried işlevleri kullanılarak oluşturulan ile en sık kullanılan `let` bağlar.</span><span class="sxs-lookup"><span data-stu-id="8ebde-117">The curried form is most often used with functions created by using `let` bindings.</span></span>

<span data-ttu-id="8ebde-118">Aşağıdaki sözde kod tanımlama grubu ve curried bağımsız örneklerini gösterir.</span><span class="sxs-lookup"><span data-stu-id="8ebde-118">The following pseudocode shows examples of tuple and curried arguments.</span></span>

```fsharp
// Tuple form.
member this.SomeMethod(param1, param2) = ...
// Curried form.
let function1 param1 param2 = ...
```

<span data-ttu-id="8ebde-119">Birleşik forms bazı bağımsız değişkenler de tanımlama gruplarına ve bazı değil mümkündür.</span><span class="sxs-lookup"><span data-stu-id="8ebde-119">Combined forms are possible when some arguments are in tuples and some are not.</span></span>

```fsharp
let function2 param1 (param2a, param2b) param3 = ...
```

<span data-ttu-id="8ebde-120">Diğer desenler içinde parametre listeleri de kullanılabilir, ancak parametre düzeni tüm olası girişleri eşleşmiyorsa olabilir bir tam eşleşme çalışma zamanında.</span><span class="sxs-lookup"><span data-stu-id="8ebde-120">Other patterns can also be used in parameter lists, but if the parameter pattern does not match all possible inputs, there might be an incomplete match at run time.</span></span> <span data-ttu-id="8ebde-121">Özel durum `MatchFailureException` bir bağımsız değişkenin değeri parametre listesinde belirtilen desenleri eşleşmediğinde oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="8ebde-121">The exception `MatchFailureException` is generated when the value of an argument does not match the patterns specified in the parameter list.</span></span> <span data-ttu-id="8ebde-122">Parametre düzeni için eksik eşleşmeler izin veriyorsa, derleyici bir uyarı verir.</span><span class="sxs-lookup"><span data-stu-id="8ebde-122">The compiler issues a warning when a parameter pattern allows for incomplete matches.</span></span> <span data-ttu-id="8ebde-123">Diğer düzen en az bir parametre listeleri için yaygın olarak kullanışlıdır ve joker karakter deseni.</span><span class="sxs-lookup"><span data-stu-id="8ebde-123">At least one other pattern is commonly useful for parameter lists, and that is the wildcard pattern.</span></span> <span data-ttu-id="8ebde-124">Yalnızca sağlanan herhangi bir bağımsız değişken yok saymak istediğinizde bir parametre listesinde joker karakter deseni kullanın.</span><span class="sxs-lookup"><span data-stu-id="8ebde-124">You use the wildcard pattern in a parameter list when you simply want to ignore any arguments that are supplied.</span></span> <span data-ttu-id="8ebde-125">Aşağıdaki kodu bir bağımsız değişken listesinde joker karakter deseni kullanımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="8ebde-125">The following code illustrates the use of the wildcard pattern in an argument list.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/parameters-and-arguments-1/snippet3801.fs)]

<span data-ttu-id="8ebde-126">Aşağıdaki kodda gösterildiği gibi bir dize dizisi olarak normal olarak sağlanan komut satırı bağımsız değişkenleri ilginizi olmadığında yararlı geçirilen bağımsız değişkenlerdeki ihtiyacınız olduğunda, bir programa ana girdi noktası olduğu gibi joker karakter deseni olabilir.</span><span class="sxs-lookup"><span data-stu-id="8ebde-126">The wildcard pattern can be useful whenever you do not need the arguments passed in, such as in the main entry point to a program, when you are not interested in the command-line arguments that are normally supplied as a string array, as in the following code.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/parameters-and-arguments-1/snippet3802.fs)]

<span data-ttu-id="8ebde-127">Bağımsız değişkenler bazen kullanılan diğer desenler `as` deseni ve ayrılmış birleşimler ve Etkin desenler ilişkili tanımlayıcı desenler.</span><span class="sxs-lookup"><span data-stu-id="8ebde-127">Other patterns that are sometimes used in arguments are the `as` pattern, and identifier patterns associated with discriminated unions and active patterns.</span></span> <span data-ttu-id="8ebde-128">Tek örneği ayrılmış birleşim deseni şu şekilde kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8ebde-128">You can use the single-case discriminated union pattern as follows.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/parameters-and-arguments-1/snippet3803.fs)]

<span data-ttu-id="8ebde-129">Çıktı aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="8ebde-129">The output is as follows.</span></span>

```
Data begins at 0 and ends at 4 in string Et tu, Brute?
Et tu
```

<span data-ttu-id="8ebde-130">Etkin desenler, bağımsız değişken aşağıdaki örnekte olduğu gibi istediğiniz bir biçime dönüştürme, parametre olarak, örneğin, yararlı olabilir:</span><span class="sxs-lookup"><span data-stu-id="8ebde-130">Active patterns can be useful as parameters, for example, when transforming an argument into a desired format, as in the following example:</span></span>

```fsharp
type Point = { x : float; y : float }

let (| Polar |) { x = x; y = y} =
    ( sqrt (x*x + y*y), System.Math.Atan (y/ x) )

let radius (Polar(r, _)) = r
let angle (Polar(_, theta)) = theta
```

<span data-ttu-id="8ebde-131">Kullanabileceğiniz `as` kod aşağıdaki satırda gösterildiği gibi yerel bir değer olarak, eşleşen bir değeri depolamak için desen.</span><span class="sxs-lookup"><span data-stu-id="8ebde-131">You can use the `as` pattern to store a matched value as a local value, as is shown in the following line of code.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/parameters-and-arguments-1/snippet3805.fs)]

<span data-ttu-id="8ebde-132">Nadiren kullanılan başka bir desendir son bağımsız değişken, işlev gövdesi olarak sağlayarak adlandırılmamış ayrıldığında bir işlev, bir lambda ifadesi hemen örtük bağımsız değişken bir desen eşleştirmesi gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="8ebde-132">Another pattern that is used occasionally is a function that leaves the last argument unnamed by providing, as the body of the function, a lambda expression that immediately performs a pattern match on the implicit argument.</span></span> <span data-ttu-id="8ebde-133">Buna örnek olarak aşağıdaki kod satırını ' dir.</span><span class="sxs-lookup"><span data-stu-id="8ebde-133">An example of this is the following line of code.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/parameters-and-arguments-1/snippet3804.fs)]

<span data-ttu-id="8ebde-134">Bu kod, genel bir liste alan ve döndüren bir işlev tanımlar `true` liste boşsa ve `false` Aksi takdirde.</span><span class="sxs-lookup"><span data-stu-id="8ebde-134">This code defines a function that takes a generic list and returns `true` if the list is empty, and `false` otherwise.</span></span> <span data-ttu-id="8ebde-135">Bu tür teknikler kullanımını kod okumak daha zor hale getirebilir.</span><span class="sxs-lookup"><span data-stu-id="8ebde-135">The use of such techniques can make code more difficult to read.</span></span>

<span data-ttu-id="8ebde-136">Bazen, eksik eşleşmeler içeren desenleri kullanışlıdır, programınızdaki listeleri yalnızca üç öğe olduğunu biliyorsanız, örneğin, bir desen aşağıdaki gibi bir parametre listesinde kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8ebde-136">Occasionally, patterns that involve incomplete matches are useful, for example, if you know that the lists in your program have only three elements, you might use a pattern like the following in a parameter list.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/parameters-and-arguments-1/snippet3806.fs)]

<span data-ttu-id="8ebde-137">Tam eşleşme sahip desenleri kullanımını en iyi hızlı prototip oluşturma ve geçici diğer kullanımlar için ayrılmıştır.</span><span class="sxs-lookup"><span data-stu-id="8ebde-137">The use of patterns that have incomplete matches is best reserved for quick prototyping and other temporary uses.</span></span> <span data-ttu-id="8ebde-138">Derleyici bu tür kod için bir uyarı verir.</span><span class="sxs-lookup"><span data-stu-id="8ebde-138">The compiler will issue a warning for such code.</span></span> <span data-ttu-id="8ebde-139">Desenler, tüm olası girişleri genel durumunun kapsamamaktadır ve bileşen API'leri için uygun değildir.</span><span class="sxs-lookup"><span data-stu-id="8ebde-139">Such patterns cannot cover the general case of all possible inputs and therefore are not suitable for component APIs.</span></span>

## <a name="named-arguments"></a><span data-ttu-id="8ebde-140">Adlandırılmış bağımsız değişkenler</span><span class="sxs-lookup"><span data-stu-id="8ebde-140">Named Arguments</span></span>
<span data-ttu-id="8ebde-141">Bağımsız değişkenler yöntemleri için bir virgülle ayrılmış bağımsız değişken listesindeki konumu ile belirtilebilir veya bunlar bir yönteme açıkça ardından bir eşittir işareti ve geçirilmesi değer adı sağlayarak geçirilebilir.</span><span class="sxs-lookup"><span data-stu-id="8ebde-141">Arguments for methods can be specified by position in a comma-separated argument list, or they can be passed to a method explicitly by providing the name, followed by an equal sign and the value to be passed in.</span></span> <span data-ttu-id="8ebde-142">Belirtilen ad sağlayarak, bildirimde kullanılan ile farklı bir sırada görünebilir.</span><span class="sxs-lookup"><span data-stu-id="8ebde-142">If specified by providing the name, they can appear in a different order from that used in the declaration.</span></span>

<span data-ttu-id="8ebde-143">Adlandırılmış bağımsız değişkenler kod daha okunabilir ve uyarlanabilir daha belirli türde bir yöntem parametreleri, yeniden sıralama API'sindeki değişiklikler yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8ebde-143">Named arguments can make code more readable and more adaptable to certain types of changes in the API, such as a reordering of method parameters.</span></span>

<span data-ttu-id="8ebde-144">Adlandırılmış bağımsız değişkenler için değil yalnızca yöntemleri için verilir `let`-bağlı İşlevler, işlev değerleri veya lambda ifadeleri.</span><span class="sxs-lookup"><span data-stu-id="8ebde-144">Named arguments are allowed only for methods, not for `let`-bound functions, function values, or lambda expressions.</span></span>

<span data-ttu-id="8ebde-145">Aşağıdaki kod örneği, adlandırılmış bağımsız değişkenler kullanımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="8ebde-145">The following code example demonstrates the use of named arguments.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/parameters-and-arguments-1/snippet3807.fs)]

<span data-ttu-id="8ebde-146">Bir sınıf oluşturucusuna bir çağrı adlandırılmış bağımsız değişkenler için benzer bir sözdizimi kullanarak sınıfın özelliklerinin değerlerini ayarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8ebde-146">In a call to a class constructor, you can set the values of properties of the class by using a syntax similar to that of named arguments.</span></span> <span data-ttu-id="8ebde-147">Aşağıdaki örnek bu söz dizimini gösterir.</span><span class="sxs-lookup"><span data-stu-id="8ebde-147">The following example shows this syntax.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet3506.fs)]

<span data-ttu-id="8ebde-148">Daha fazla bilgi için [oluşturucular (F #)](https://msdn.microsoft.com/library/2cd0ed07-d214-4125-8317-4f288af99f05).</span><span class="sxs-lookup"><span data-stu-id="8ebde-148">For more information, see [Constructors (F#)](https://msdn.microsoft.com/library/2cd0ed07-d214-4125-8317-4f288af99f05).</span></span>

## <a name="optional-parameters"></a><span data-ttu-id="8ebde-149">İsteğe Bağlı Parametreler</span><span class="sxs-lookup"><span data-stu-id="8ebde-149">Optional Parameters</span></span>
<span data-ttu-id="8ebde-150">İsteğe bağlı parametresi bir yöntem için parametre adının önüne bir soru işareti kullanarak belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8ebde-150">You can specify an optional parameter for a method by using a question mark in front of the parameter name.</span></span> <span data-ttu-id="8ebde-151">İsteğe bağlı parametreler, F # seçeneği türü olarak yorumlanır, seçenek türleri, kullanarak sorgulanır, normal şekilde sorgulayabilmesi bir `match` ifadesiyle `Some` ve `None`.</span><span class="sxs-lookup"><span data-stu-id="8ebde-151">Optional parameters are interpreted as the F# option type, so you can query them in the regular way that option types are queried, by using a `match` expression with `Some` and `None`.</span></span> <span data-ttu-id="8ebde-152">İsteğe bağlı parametreler kullanılarak oluşturulan işlevleri, üye üzerinde yalnızca verilen `let` bağlar.</span><span class="sxs-lookup"><span data-stu-id="8ebde-152">Optional parameters are permitted only on members, not on functions created by using `let` bindings.</span></span>

<span data-ttu-id="8ebde-153">Bir işlev de kullanabilirsiniz `defaultArg`, isteğe bağlı varsayılan değerini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="8ebde-153">You can also use a function `defaultArg`, which sets a default value of an optional argument.</span></span> <span data-ttu-id="8ebde-154">`defaultArg` İşlevi isteğe bağlı parametre olarak ilk bağımsız değişken ve varsayılan değer olarak saniye alır.</span><span class="sxs-lookup"><span data-stu-id="8ebde-154">The `defaultArg` function takes the optional parameter as the first argument and the default value as the second.</span></span>

<span data-ttu-id="8ebde-155">Aşağıdaki örnek, isteğe bağlı parametreler kullanımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="8ebde-155">The following example illustrates the use of optional parameters.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/parameters-and-arguments-1/snippet3808.fs)]

<span data-ttu-id="8ebde-156">Çıktı aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="8ebde-156">The output is as follows.</span></span>

```
Baud Rate: 9600 Duplex: Full Parity: false
Baud Rate: 4800 Duplex: Half Parity: false
Baud Rate: 300 Duplex: Half Parity: true
```

## <a name="passing-by-reference"></a><span data-ttu-id="8ebde-157">Başvuruya göre geçirme</span><span class="sxs-lookup"><span data-stu-id="8ebde-157">Passing by Reference</span></span>
<span data-ttu-id="8ebde-158">Bir F # değere Başvuruya göre geçirme içerir `byref` anahtar sözcüğü parametresi başvuruya göre geçirilen değere gerçekten bir işaretçi olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="8ebde-158">Passing an F# value by reference involves the `byref` keyword, which specifies that the parameter is actually a pointer to the value being passed by reference.</span></span> <span data-ttu-id="8ebde-159">Herhangi bir değer geçirildi yöntemi ile bir `byref` bağımsız değişken olarak `mutable`.</span><span class="sxs-lookup"><span data-stu-id="8ebde-159">Any value passed into a method with a `byref` as the argument must be `mutable`.</span></span>

<span data-ttu-id="8ebde-160">Parametre bir işaretçi ve değer değişebilir olduğundan, işlevi yürütme sonrasında değeri herhangi bir değişiklik korunur.</span><span class="sxs-lookup"><span data-stu-id="8ebde-160">Because the parameter is a pointer and the value is mutable, any changes to the value are retained after the execution of the function.</span></span>

<span data-ttu-id="8ebde-161">Aynı işlemi gerçekleştirebilirsiniz [başvuru hücreleri](reference-cells.md), ancak dikkat etmeniz önemlidir **başvuru hücreleri ve `byref`s aynı şey değildir**.</span><span class="sxs-lookup"><span data-stu-id="8ebde-161">You can accomplish the same thing with [Reference Cells](reference-cells.md), but it's important to note that **reference cells and `byref`s are not the same thing**.</span></span> <span data-ttu-id="8ebde-162">Bir başvuru hücresi inceleyin ve içeriğini değiştirme, ancak bu değer yığın üzerinde yaşadığı ve içerdiği değiştirilebilir bir değer ile kayıt olmakla eşdeğerdir bir değer için bir kapsayıcıdır.</span><span class="sxs-lookup"><span data-stu-id="8ebde-162">A reference cell is a container for a value that you can inspect and change the contents of, but this value lives on the heap and is equivalent to having a record with a mutable value contained within it.</span></span> <span data-ttu-id="8ebde-163">A `byref` farklı temel alınan semantiği ve (hangi oldukça kısıtlayıcı olabilir) kullanım kuralları, bu nedenle, gerçek bir işaretçi olduğu.</span><span class="sxs-lookup"><span data-stu-id="8ebde-163">A `byref` is an actual pointer, so it is different underlying semantics and usage rules (which can be quite restrictive).</span></span>

<span data-ttu-id="8ebde-164">Aşağıdaki örnekler, kullanımını gösterir `byref` anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="8ebde-164">The following examples illustrate the use of the `byref` keyword.</span></span> <span data-ttu-id="8ebde-165">Parametre olarak bir başvuru hücresi kullanmanız, size gerekir adlandırılmış değeri olarak başvuru hücresini oluşturmak ve parametre olarak kullanan, yalnızca ekleme dikkat edin `ref` yapılan ilk çağrıda gösterildiği bir işleç `Increment` aşağıdaki kodda.</span><span class="sxs-lookup"><span data-stu-id="8ebde-165">Note that when you use a reference cell as a parameter, you must create a reference cell as a named value and use that as the parameter, not just add the `ref` operator as shown in the first call to `Increment` in the following code.</span></span> <span data-ttu-id="8ebde-166">Temel alınan değerinin bir kopyasıdır oluşturduğu bir başvuru hücresi oluşturmak için ilk çağrı yalnızca geçici bir değeri artırır.</span><span class="sxs-lookup"><span data-stu-id="8ebde-166">Because creating a reference cell creates a copy of the underlying value, the first call just increments a temporary value.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/parameters-and-arguments-1/snippet3809.fs)]

<span data-ttu-id="8ebde-167">Tüm depolamak için bir dönüş değeri olarak bir tanımlama grubu kullanabilirsiniz `out` .NET kitaplığı yöntem parametreleri.</span><span class="sxs-lookup"><span data-stu-id="8ebde-167">You can use a tuple as a return value to store any `out` parameters in .NET library methods.</span></span> <span data-ttu-id="8ebde-168">Alternatif olarak davranabileceğiniz `out` parametre olarak bir `byref` parametresi.</span><span class="sxs-lookup"><span data-stu-id="8ebde-168">Alternatively, you can treat the `out` parameter as a `byref` parameter.</span></span> <span data-ttu-id="8ebde-169">Aşağıdaki kod örneği iki yolunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="8ebde-169">The following code example illustrates both ways.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/parameters-and-arguments-1/snippet3810.fs)]

## <a name="parameter-arrays"></a><span data-ttu-id="8ebde-170">Parametre Dizileri</span><span class="sxs-lookup"><span data-stu-id="8ebde-170">Parameter Arrays</span></span>
<span data-ttu-id="8ebde-171">Bazen tercihe bağlı sayıda heterojen türünde parametre alan bir işlev tanımlamak gereklidir.</span><span class="sxs-lookup"><span data-stu-id="8ebde-171">Occasionally it is necessary to define a function that takes an arbitrary number of parameters of heterogeneous type.</span></span> <span data-ttu-id="8ebde-172">Kullanılabilen tüm türleri için hesap için tüm olası aşırı yüklenmiş yöntemler oluşturmak pratik olmaz.</span><span class="sxs-lookup"><span data-stu-id="8ebde-172">It would not be practical to create all the possible overloaded methods to account for all the types that could be used.</span></span> <span data-ttu-id="8ebde-173">.NET uygulamaları için parametre dizisi özelliği aracılığıyla bu tür yöntemler için destek sağlar.</span><span class="sxs-lookup"><span data-stu-id="8ebde-173">The .NET implementations provide support for such methods through the parameter array feature.</span></span> <span data-ttu-id="8ebde-174">Bir parametre dizisi içinde imzasını alan bir yöntem rastgele sayıda parametre ile sağlanabilir.</span><span class="sxs-lookup"><span data-stu-id="8ebde-174">A method that takes a parameter array in its signature can be provided with an arbitrary number of parameters.</span></span> <span data-ttu-id="8ebde-175">Parametreler, bir dizi içine yerleştirilir.</span><span class="sxs-lookup"><span data-stu-id="8ebde-175">The parameters are put into an array.</span></span> <span data-ttu-id="8ebde-176">Dizi öğelerinin türü, işleve geçirilen parametre türleri belirler.</span><span class="sxs-lookup"><span data-stu-id="8ebde-176">The type of the array elements determines the parameter types that can be passed to the function.</span></span> <span data-ttu-id="8ebde-177">Parametre dizisi ile tanımlarsanız `System.Object` öğe türü istemci kodu her türden değer geçirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8ebde-177">If you define the parameter array with `System.Object` as the element type, then client code can pass values of any type.</span></span>

<span data-ttu-id="8ebde-178">F #'ta parametre dizileri, yalnızca yöntemlerdeki tanımlanabilir.</span><span class="sxs-lookup"><span data-stu-id="8ebde-178">In F#, parameter arrays can only be defined in methods.</span></span> <span data-ttu-id="8ebde-179">Tek başına işlevleri veya modül içinde tanımlanan işlevleri kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="8ebde-179">They cannot be used in standalone functions or functions that are defined in modules.</span></span>

<span data-ttu-id="8ebde-180">Bir parametre dizisi kullanarak tanımladığınız `ParamArray` özniteliği.</span><span class="sxs-lookup"><span data-stu-id="8ebde-180">You define a parameter array by using the `ParamArray` attribute.</span></span> <span data-ttu-id="8ebde-181">`ParamArray` Özniteliği yalnızca en son parametreye uygulanabilir.</span><span class="sxs-lookup"><span data-stu-id="8ebde-181">The `ParamArray` attribute can only be applied to the last parameter.</span></span>

<span data-ttu-id="8ebde-182">Aşağıdaki kod, her iki arama alan bir parametre dizisi ve bir tür tanımını içeren bir parametre dizisi alan bir yöntem içinde F # .NET yöntemi gösterir.</span><span class="sxs-lookup"><span data-stu-id="8ebde-182">The following code illustrates both calling a .NET method that takes a parameter array and the definition of a type in F# that has a method that takes a parameter array.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/parameters-and-arguments-2/snippet3811.fs)]

<span data-ttu-id="8ebde-183">Bir projeyi çalıştırdığınızda, önceki kodun çıktısı aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="8ebde-183">When run in a project, the output of the previous code is as follows:</span></span>

```
a 1 10 Hello world 1 True
"a"
1
10.0
"Hello world"
1u
true
```

## <a name="see-also"></a><span data-ttu-id="8ebde-184">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="8ebde-184">See Also</span></span>
[<span data-ttu-id="8ebde-185">Üyeler</span><span class="sxs-lookup"><span data-stu-id="8ebde-185">Members</span></span>](members/index.md)
