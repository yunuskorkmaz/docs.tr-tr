---
title: Parametreler ve Bağımsız Değişkenler
description: Parametreleri tanımlamak ve bağımsız değişkenleri işlevlere, yöntemlere ve özelliklere geçirmek için F# dil desteği hakkında bilgi edinin.
ms.date: 12/04/2019
ms.openlocfilehash: b234ef939128e7cf09d35f9580d4d5010d7dc639
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79400199"
---
# <a name="parameters-and-arguments"></a><span data-ttu-id="3095e-103">Parametreler ve Bağımsız Değişkenler</span><span class="sxs-lookup"><span data-stu-id="3095e-103">Parameters and Arguments</span></span>

<span data-ttu-id="3095e-104">Bu konu, parametreleri tanımlamak ve bağımsız değişkenleri işlevlere, yöntemlere ve özelliklere geçirmek için dil desteğini açıklar.</span><span class="sxs-lookup"><span data-stu-id="3095e-104">This topic describes language support for defining parameters and passing arguments to functions, methods, and properties.</span></span> <span data-ttu-id="3095e-105">Başvuruya göre nasıl geçirilebileceği ve değişken sayıda bağımsız değişken alabilecek yöntemlerin nasıl tanımlanabileceği ve kullanılacağı hakkında bilgiler içerir.</span><span class="sxs-lookup"><span data-stu-id="3095e-105">It includes information about how to pass by reference, and how to define and use methods that can take a variable number of arguments.</span></span>

## <a name="parameters-and-arguments"></a><span data-ttu-id="3095e-106">Parametreler ve Bağımsız Değişkenler</span><span class="sxs-lookup"><span data-stu-id="3095e-106">Parameters and Arguments</span></span>

<span data-ttu-id="3095e-107">Terim *parametresi,* sağlanmalıdır beklenen değerlerin adlarını açıklamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="3095e-107">The term *parameter* is used to describe the names for values that are expected to be supplied.</span></span> <span data-ttu-id="3095e-108">Terim *bağımsız değişkeni,* her parametre için sağlanan değerler için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="3095e-108">The term *argument* is used for the values provided for each parameter.</span></span>

<span data-ttu-id="3095e-109">Parametreler tuple veya curried şeklinde veya ikisinin bir kombinasyonunda belirtilebilir.</span><span class="sxs-lookup"><span data-stu-id="3095e-109">Parameters can be specified in tuple or curried form, or in some combination of the two.</span></span> <span data-ttu-id="3095e-110">Açık bir parametre adı kullanarak bağımsız değişkenleri geçirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3095e-110">You can pass arguments by using an explicit parameter name.</span></span> <span data-ttu-id="3095e-111">Yöntemlerin parametreleri isteğe bağlı olarak belirtilebilir ve varsayılan değer verilebilir.</span><span class="sxs-lookup"><span data-stu-id="3095e-111">Parameters of methods can be specified as optional and given a default value.</span></span>

## <a name="parameter-patterns"></a><span data-ttu-id="3095e-112">Parametre Desenleri</span><span class="sxs-lookup"><span data-stu-id="3095e-112">Parameter Patterns</span></span>

<span data-ttu-id="3095e-113">Fonksiyonlara ve yöntemlere verilen parametreler, genel olarak boşluklara göre ayrılmış desenlerdir.</span><span class="sxs-lookup"><span data-stu-id="3095e-113">Parameters supplied to functions and methods are, in general, patterns separated by spaces.</span></span> <span data-ttu-id="3095e-114">Bu, ilke olarak, [Eşler İfadeleri'nde](match-expressions.md) açıklanan desenlerden herhangi birinin bir işlev veya üye için parametre listesinde kullanılabileceğini zedebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3095e-114">This means that, in principle, any of the patterns described in [Match Expressions](match-expressions.md) can be used in a parameter list for a function or member.</span></span>

<span data-ttu-id="3095e-115">Yöntemler genellikle geçen bağımsız değişkenlerin tuple biçimini kullanır.</span><span class="sxs-lookup"><span data-stu-id="3095e-115">Methods usually use the tuple form of passing arguments.</span></span> <span data-ttu-id="3095e-116">Bu, diğer .NET dillerinin perspektifinden daha net bir sonuç elde eder, çünkü tuple formu .NET yöntemlerinde bağımsız değişkenlerin geçirildiği şekilde eşleşir.</span><span class="sxs-lookup"><span data-stu-id="3095e-116">This achieves a clearer result from the perspective of other .NET languages because the tuple form matches the way arguments are passed in .NET methods.</span></span>

<span data-ttu-id="3095e-117">Körili form en sık bağlamalar kullanılarak `let` oluşturulan işlevlerle kullanılır.</span><span class="sxs-lookup"><span data-stu-id="3095e-117">The curried form is most often used with functions created by using `let` bindings.</span></span>

<span data-ttu-id="3095e-118">Aşağıdaki pseudocode tuple ve curried bağımsız değişkenörnekleri gösterir.</span><span class="sxs-lookup"><span data-stu-id="3095e-118">The following pseudocode shows examples of tuple and curried arguments.</span></span>

```fsharp
// Tuple form.
member this.SomeMethod(param1, param2) = ...
// Curried form.
let function1 param1 param2 = ...
```

<span data-ttu-id="3095e-119">Bazı bağımsız değişkenler tuples ve bazı değildir kombine formlar mümkündür.</span><span class="sxs-lookup"><span data-stu-id="3095e-119">Combined forms are possible when some arguments are in tuples and some are not.</span></span>

```fsharp
let function2 param1 (param2a, param2b) param3 = ...
```

<span data-ttu-id="3095e-120">Diğer desenler de parametre listelerinde kullanılabilir, ancak parametre deseni tüm olası girişler le eşleşmiyorsa, çalışma zamanında eksik bir eşleşme olabilir.</span><span class="sxs-lookup"><span data-stu-id="3095e-120">Other patterns can also be used in parameter lists, but if the parameter pattern does not match all possible inputs, there might be an incomplete match at run time.</span></span> <span data-ttu-id="3095e-121">Bir `MatchFailureException` bağımsız değişkenin değeri parametre listesinde belirtilen desenlerle eşleşmediğinde özel durum oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="3095e-121">The exception `MatchFailureException` is generated when the value of an argument does not match the patterns specified in the parameter list.</span></span> <span data-ttu-id="3095e-122">Derleyici, parametre deseni eksik eşleşmeler için izin verdiğinde bir uyarı verir.</span><span class="sxs-lookup"><span data-stu-id="3095e-122">The compiler issues a warning when a parameter pattern allows for incomplete matches.</span></span> <span data-ttu-id="3095e-123">Parametre listeleri için en az bir desen daha yararlıdır ve bu joker karakter desenidir.</span><span class="sxs-lookup"><span data-stu-id="3095e-123">At least one other pattern is commonly useful for parameter lists, and that is the wildcard pattern.</span></span> <span data-ttu-id="3095e-124">Sağlanan bağımsız değişkenleri yok saymak istediğinizde, bir parametre listesinde joker karakter deseni kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="3095e-124">You use the wildcard pattern in a parameter list when you simply want to ignore any arguments that are supplied.</span></span> <span data-ttu-id="3095e-125">Aşağıdaki kod, bağımsız değişken listesinde joker karakter deseninin kullanımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="3095e-125">The following code illustrates the use of the wildcard pattern in an argument list.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/parameters-and-arguments-1/snippet3801.fs)]

<span data-ttu-id="3095e-126">Joker karakter deseni, aşağıdaki kodda olduğu gibi normalde bir dize dizisi olarak sağlanan komut satırı bağımsız değişkenleriyle ilgilenmediğiniz bir programa ana giriş noktası gibi bağımsız değişkenlere gerek kalmadığında yararlı olabilir.</span><span class="sxs-lookup"><span data-stu-id="3095e-126">The wildcard pattern can be useful whenever you do not need the arguments passed in, such as in the main entry point to a program, when you are not interested in the command-line arguments that are normally supplied as a string array, as in the following code.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/parameters-and-arguments-1/snippet3802.fs)]

<span data-ttu-id="3095e-127">Bazen bağımsız değişkenlerde kullanılan diğer `as` desenler desen ve ayrımcı sendikalar ve etkin desenler ile ilişkili tanımlayıcı desenleri vardır.</span><span class="sxs-lookup"><span data-stu-id="3095e-127">Other patterns that are sometimes used in arguments are the `as` pattern, and identifier patterns associated with discriminated unions and active patterns.</span></span> <span data-ttu-id="3095e-128">Tek harfli ayrımlı birleşim modelini aşağıdaki gibi kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3095e-128">You can use the single-case discriminated union pattern as follows.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/parameters-and-arguments-1/snippet3803.fs)]

<span data-ttu-id="3095e-129">Çıktı aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="3095e-129">The output is as follows.</span></span>

```console
Data begins at 0 and ends at 4 in string Et tu, Brute?
Et tu
```

<span data-ttu-id="3095e-130">Etkin desenler, örneğin aşağıdaki örnekte olduğu gibi, bir bağımsız değişkeni istenilen biçime dönüştürürken parametreler olarak yararlı olabilir:</span><span class="sxs-lookup"><span data-stu-id="3095e-130">Active patterns can be useful as parameters, for example, when transforming an argument into a desired format, as in the following example:</span></span>

```fsharp
type Point = { x : float; y : float }

let (| Polar |) { x = x; y = y} =
    ( sqrt (x*x + y*y), System.Math.Atan (y/ x) )

let radius (Polar(r, _)) = r
let angle (Polar(_, theta)) = theta
```

<span data-ttu-id="3095e-131">`as` Aşağıdaki kod satırında gösterildiği gibi, eşleşen bir değeri yerel bir değer olarak depolamak için deseni kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3095e-131">You can use the `as` pattern to store a matched value as a local value, as is shown in the following line of code.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/parameters-and-arguments-1/snippet3805.fs)]

<span data-ttu-id="3095e-132">Bazen kullanılan başka bir desen, işlevin gövdesi olarak, örtük bağımsız değişken üzerinde hemen bir desen eşleşmesi gerçekleştiren bir lambda ifadesi sağlayarak, son bağımsız değişkeni isimsiz bırakan bir işlevdir.</span><span class="sxs-lookup"><span data-stu-id="3095e-132">Another pattern that is used occasionally is a function that leaves the last argument unnamed by providing, as the body of the function, a lambda expression that immediately performs a pattern match on the implicit argument.</span></span> <span data-ttu-id="3095e-133">Bunun bir örneği aşağıdaki kod satırıdır.</span><span class="sxs-lookup"><span data-stu-id="3095e-133">An example of this is the following line of code.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/parameters-and-arguments-1/snippet3804.fs)]

<span data-ttu-id="3095e-134">Bu kod, genel bir liste alan `true` ve liste boşsa `false` ve başka türlü döndüren bir işlev tanımlar.</span><span class="sxs-lookup"><span data-stu-id="3095e-134">This code defines a function that takes a generic list and returns `true` if the list is empty, and `false` otherwise.</span></span> <span data-ttu-id="3095e-135">Bu tür tekniklerin kullanımı kodun okunmasını zorlaştırabilir.</span><span class="sxs-lookup"><span data-stu-id="3095e-135">The use of such techniques can make code more difficult to read.</span></span>

<span data-ttu-id="3095e-136">Bazen, tamamlanmamış eşleşmeler içeren desenler yararlıdır, örneğin, programınızdaki listelerin yalnızca üç öğesi olduğunu biliyorsanız, parametre listesinde aşağıdaki gibi bir desen kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3095e-136">Occasionally, patterns that involve incomplete matches are useful, for example, if you know that the lists in your program have only three elements, you might use a pattern like the following in a parameter list.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/parameters-and-arguments-1/snippet3806.fs)]

<span data-ttu-id="3095e-137">Eksik eşleşmeleri olan desenlerin kullanımı en iyi hızlı prototipleme ve diğer geçici kullanımlar için ayrılmıştır.</span><span class="sxs-lookup"><span data-stu-id="3095e-137">The use of patterns that have incomplete matches is best reserved for quick prototyping and other temporary uses.</span></span> <span data-ttu-id="3095e-138">Derleyici bu tür kod için bir uyarı yayımlar.</span><span class="sxs-lookup"><span data-stu-id="3095e-138">The compiler will issue a warning for such code.</span></span> <span data-ttu-id="3095e-139">Bu tür desenler tüm olası girdilerin genel durumunu kapsayamaz ve bu nedenle bileşen API'leri için uygun değildir.</span><span class="sxs-lookup"><span data-stu-id="3095e-139">Such patterns cannot cover the general case of all possible inputs and therefore are not suitable for component APIs.</span></span>

## <a name="named-arguments"></a><span data-ttu-id="3095e-140">Adlandırılmış Bağımsız Değişkenler</span><span class="sxs-lookup"><span data-stu-id="3095e-140">Named Arguments</span></span>

<span data-ttu-id="3095e-141">Yöntemler için bağımsız değişkenler virgülle ayrılmış bir bağımsız değişken listesindeki konuma göre belirtilebilir veya ad sağlanarak, ardından eşit bir işaret ve geçirilecek değer sağlanarak bir yönteme geçirilebilir.</span><span class="sxs-lookup"><span data-stu-id="3095e-141">Arguments for methods can be specified by position in a comma-separated argument list, or they can be passed to a method explicitly by providing the name, followed by an equal sign and the value to be passed in.</span></span> <span data-ttu-id="3095e-142">Ad belirtilerek belirtilirse, bildirimde kullanılandan farklı bir sırada görünebilirler.</span><span class="sxs-lookup"><span data-stu-id="3095e-142">If specified by providing the name, they can appear in a different order from that used in the declaration.</span></span>

<span data-ttu-id="3095e-143">Adlandırılmış bağımsız değişkenler, kodu yöntem parametrelerinin yeniden sıralanması gibi API'deki belirli değişiklik türlerine daha kolay ve daha uyarlanabilir hale getirebilir.</span><span class="sxs-lookup"><span data-stu-id="3095e-143">Named arguments can make code more readable and more adaptable to certain types of changes in the API, such as a reordering of method parameters.</span></span>

<span data-ttu-id="3095e-144">Adlandırılmış bağımsız değişkenlere yalnızca `let`bağlı işlevler, işlev değerleri veya lambda ifadeleri için değil, yöntemler için izin verilir.</span><span class="sxs-lookup"><span data-stu-id="3095e-144">Named arguments are allowed only for methods, not for `let`-bound functions, function values, or lambda expressions.</span></span>

<span data-ttu-id="3095e-145">Aşağıdaki kod örneği, adlandırılmış bağımsız değişkenlerin kullanımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="3095e-145">The following code example demonstrates the use of named arguments.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/parameters-and-arguments-1/snippet3807.fs)]

<span data-ttu-id="3095e-146">Bir sınıf oluşturucuya yapılan bir çağrıda, adlandırılmış bağımsız değişkenlere benzer bir sözdizimi kullanarak sınıfın özelliklerinin değerlerini ayarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3095e-146">In a call to a class constructor, you can set the values of properties of the class by using a syntax similar to that of named arguments.</span></span> <span data-ttu-id="3095e-147">Aşağıdaki örnekte bu sözdizimi gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="3095e-147">The following example shows this syntax.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet3506.fs)]

<span data-ttu-id="3095e-148">Daha fazla bilgi için [Constructors (F#)](https://msdn.microsoft.com/library/2cd0ed07-d214-4125-8317-4f288af99f05)bakın.</span><span class="sxs-lookup"><span data-stu-id="3095e-148">For more information, see [Constructors (F#)](https://msdn.microsoft.com/library/2cd0ed07-d214-4125-8317-4f288af99f05).</span></span>

## <a name="optional-parameters"></a><span data-ttu-id="3095e-149">İsteğe Bağlı Parametreler</span><span class="sxs-lookup"><span data-stu-id="3095e-149">Optional Parameters</span></span>

<span data-ttu-id="3095e-150">Parametre adının önünde bir soru işareti kullanarak bir yöntem için isteğe bağlı bir parametre belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3095e-150">You can specify an optional parameter for a method by using a question mark in front of the parameter name.</span></span> <span data-ttu-id="3095e-151">İsteğe bağlı parametreler F# seçeneği türü olarak yorumlanır, böylece seçenek türlerinin sorgulanacağı normal `match` şekilde `Some` `None`sorgulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3095e-151">Optional parameters are interpreted as the F# option type, so you can query them in the regular way that option types are queried, by using a `match` expression with `Some` and `None`.</span></span> <span data-ttu-id="3095e-152">İsteğe bağlı parametrelere yalnızca üyelere izin `let` verilir, bağlamalar kullanılarak oluşturulan işlevlerde değil.</span><span class="sxs-lookup"><span data-stu-id="3095e-152">Optional parameters are permitted only on members, not on functions created by using `let` bindings.</span></span>

<span data-ttu-id="3095e-153">Varolan isteğe bağlı değerleri parametre adı `?arg=None` ile `?arg=Some(3)` `?arg=arg`yönteme geçirebilirsiniz, örneğin veya .</span><span class="sxs-lookup"><span data-stu-id="3095e-153">You can pass existing optional values to method by parameter name, such as `?arg=None` or `?arg=Some(3)` or `?arg=arg`.</span></span> <span data-ttu-id="3095e-154">Bu, isteğe bağlı bağımsız değişkenleri başka bir yönteme geçen bir yöntem yaparken yararlı olabilir.</span><span class="sxs-lookup"><span data-stu-id="3095e-154">This can be useful when building a method that passes optional arguments to another method.</span></span>

<span data-ttu-id="3095e-155">İsteğe bağlı bir `defaultArg`bağımsız değişkenin varsayılan değerini belirleyen bir işlev de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3095e-155">You can also use a function `defaultArg`, which sets a default value of an optional argument.</span></span> <span data-ttu-id="3095e-156">İşlev, `defaultArg` isteğe bağlı parametreyi ilk bağımsız değişken olarak, varsayılan değeri ise ikinci olarak alır.</span><span class="sxs-lookup"><span data-stu-id="3095e-156">The `defaultArg` function takes the optional parameter as the first argument and the default value as the second.</span></span>

<span data-ttu-id="3095e-157">Aşağıdaki örnekte isteğe bağlı parametrelerin kullanımı gösteriş verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="3095e-157">The following example illustrates the use of optional parameters.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/parameters-and-arguments-1/snippet3808.fs)]

<span data-ttu-id="3095e-158">Çıktı aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="3095e-158">The output is as follows.</span></span>

```console
Baud Rate: 9600 Duplex: Full Parity: false
Baud Rate: 4800 Duplex: Half Parity: false
Baud Rate: 300 Duplex: Half Parity: true
Baud Rate: 9600 Duplex: Full Parity: false
Baud Rate: 9600 Duplex: Full Parity: false
Baud Rate: 4800 Duplex: Half Parity: false
```

<span data-ttu-id="3095e-159">C# ve Visual Basic interop amaçları için `[<Optional; DefaultParameterValue<(...)>]` F# özniteliklerini kullanabilirsiniz, böylece arayanlar isteğe bağlı olarak bir argüman göreceksiniz.</span><span class="sxs-lookup"><span data-stu-id="3095e-159">For the purposes of C# and Visual Basic interop you can use the attributes `[<Optional; DefaultParameterValue<(...)>]` in F#, so that callers will see an argument as optional.</span></span> <span data-ttu-id="3095e-160">Bu, bağımsız değişkeni C#'da isteğe `MyMethod(int i = 3)`bağlı olarak tanımlamaya eşdeğerdir.</span><span class="sxs-lookup"><span data-stu-id="3095e-160">This is equivalent to defining the argument as optional in C# as in `MyMethod(int i = 3)`.</span></span>

```fsharp
open System
open System.Runtime.InteropServices
type C =
    static member Foo([<Optional; DefaultParameterValue("Hello world")>] message) =
        printfn "%s" message
```

<span data-ttu-id="3095e-161">Varsayılan parametre değeri olarak yeni bir nesne de belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3095e-161">You can also specify a new object as a default parameter value.</span></span> <span data-ttu-id="3095e-162">Örneğin, `Foo` üye nin giriş `CancellationToken` olarak isteğe bağlı bir girişi olabilir:</span><span class="sxs-lookup"><span data-stu-id="3095e-162">For example, the `Foo` member could have an optional `CancellationToken` as input instead:</span></span>

```fsharp
open System.Threading
open System.Runtime.InteropServices
type C =
    static member Foo([<Optional; DefaultParameterValue(CancellationToken())>] ct: CancellationToken) =
        printfn "%A" ct
```

<span data-ttu-id="3095e-163">Bağımsız değişken olarak `DefaultParameterValue` verilen değer, parametrenin türüyle eşleşmelidir.</span><span class="sxs-lookup"><span data-stu-id="3095e-163">The value given as argument to `DefaultParameterValue` must match the type of the parameter.</span></span> <span data-ttu-id="3095e-164">Örneğin, aşağıdakiler izin verilmez:</span><span class="sxs-lookup"><span data-stu-id="3095e-164">For example, the following is not allowed:</span></span>

```fsharp
type C =
    static member Wrong([<Optional; DefaultParameterValue("string")>] i:int) = ()
```

<span data-ttu-id="3095e-165">Bu durumda, derleyici bir uyarı oluşturur ve her iki öznitelikleri tamamen yoksayacaktır.</span><span class="sxs-lookup"><span data-stu-id="3095e-165">In this case, the compiler generates a warning and will ignore both attributes altogether.</span></span> <span data-ttu-id="3095e-166">Varsayılan değerin `null` tür açıklamalı olması gerektiğini unutmayın, aksi takdirde derleyici yanlış türü çıkar, `[<Optional; DefaultParameterValue(null:obj)>] o:obj`yani.</span><span class="sxs-lookup"><span data-stu-id="3095e-166">Note that the default value `null` needs to be type-annotated, as otherwise the compiler infers the wrong type, i.e. `[<Optional; DefaultParameterValue(null:obj)>] o:obj`.</span></span>

## <a name="passing-by-reference"></a><span data-ttu-id="3095e-167">Başvuruya Göre Geçiş</span><span class="sxs-lookup"><span data-stu-id="3095e-167">Passing by Reference</span></span>

<span data-ttu-id="3095e-168">F# değerini referansla geçmek, yönetilen işaretçi türlerini içeren [byrefs](byrefs.md)içerir.</span><span class="sxs-lookup"><span data-stu-id="3095e-168">Passing an F# value by reference involves [byrefs](byrefs.md), which are managed pointer types.</span></span> <span data-ttu-id="3095e-169">Hangi türde kullanılacağı nayönelik yönerge aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="3095e-169">Guidance for which type to use is as follows:</span></span>

- <span data-ttu-id="3095e-170">Yalnızca `inref<'T>` işaretçiyi okumanız gerekiyorsa kullanın.</span><span class="sxs-lookup"><span data-stu-id="3095e-170">Use `inref<'T>` if you only need to read the pointer.</span></span>
- <span data-ttu-id="3095e-171">Yalnızca `outref<'T>` işaretçiye yazmanız gerekiyorsa kullanın.</span><span class="sxs-lookup"><span data-stu-id="3095e-171">Use `outref<'T>` if you only need to write to the pointer.</span></span>
- <span data-ttu-id="3095e-172">Hem `byref<'T>` okumanız hem de işaretçiye yazmanız gerekiyorsa kullanın.</span><span class="sxs-lookup"><span data-stu-id="3095e-172">Use `byref<'T>` if you need to both read from and write to the pointer.</span></span>

```fsharp
let example1 (x: inref<int>) = printfn "It's %d" x

let example2 (x: outref<int>) = x <- x + 1

let example3 (x: byref<int>) =
    printfn "It'd %d" x
    x <- x + 1

let test () =
    // No need to make it mutable, since it's read-only
    let x = 1
    example1 &x

    // Needs to be mutable, since we write to it
    let mutable y = 2
    example2 &y
    example3 &y // Now 'y' is 3
```

<span data-ttu-id="3095e-173">Parametre bir işaretçi ve değer değişken olduğundan, işlev in yürütülmesinden sonra değerdeki tüm değişiklikler korunur.</span><span class="sxs-lookup"><span data-stu-id="3095e-173">Because the parameter is a pointer and the value is mutable, any changes to the value are retained after the execution of the function.</span></span>

<span data-ttu-id="3095e-174">Herhangi `out` bir parametreyi .NET kitaplık yöntemlerinde depolamak için bir tuple'ı iade değeri olarak kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3095e-174">You can use a tuple as a return value to store any `out` parameters in .NET library methods.</span></span> <span data-ttu-id="3095e-175">Alternatif olarak, parametreyi `out` bir `byref` parametre olarak değerlendirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3095e-175">Alternatively, you can treat the `out` parameter as a `byref` parameter.</span></span> <span data-ttu-id="3095e-176">Aşağıdaki kod örneği her iki yolu da göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="3095e-176">The following code example illustrates both ways.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/parameters-and-arguments-1/snippet3810.fs)]

## <a name="parameter-arrays"></a><span data-ttu-id="3095e-177">Parametre Dizileri</span><span class="sxs-lookup"><span data-stu-id="3095e-177">Parameter Arrays</span></span>

<span data-ttu-id="3095e-178">Bazen heterojen tip parametrelerin rasgele bir sayı alan bir işlev tanımlamak için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="3095e-178">Occasionally it is necessary to define a function that takes an arbitrary number of parameters of heterogeneous type.</span></span> <span data-ttu-id="3095e-179">Kullanılabilecek tüm türleri hesaba katmak için tüm olası aşırı yükleme yöntemlerini oluşturmak pratik olmaz.</span><span class="sxs-lookup"><span data-stu-id="3095e-179">It would not be practical to create all the possible overloaded methods to account for all the types that could be used.</span></span> <span data-ttu-id="3095e-180">.NET uygulamaları, parametre diziözelliği aracılığıyla bu tür yöntemler için destek sağlar.</span><span class="sxs-lookup"><span data-stu-id="3095e-180">The .NET implementations provide support for such methods through the parameter array feature.</span></span> <span data-ttu-id="3095e-181">İmzasında parametre dizisini alan bir yöntem, rasgele bir parametre sayısıyla sağlanabilir.</span><span class="sxs-lookup"><span data-stu-id="3095e-181">A method that takes a parameter array in its signature can be provided with an arbitrary number of parameters.</span></span> <span data-ttu-id="3095e-182">Parametreler bir diziye konur.</span><span class="sxs-lookup"><span data-stu-id="3095e-182">The parameters are put into an array.</span></span> <span data-ttu-id="3095e-183">Dizi öğelerinin türü, işleve geçirilebilen parametre türlerini belirler.</span><span class="sxs-lookup"><span data-stu-id="3095e-183">The type of the array elements determines the parameter types that can be passed to the function.</span></span> <span data-ttu-id="3095e-184">Öğe türü `System.Object` ile parametre dizisini tanımlarsanız, istemci kodu herhangi bir türdeki değerleri geçirebilir.</span><span class="sxs-lookup"><span data-stu-id="3095e-184">If you define the parameter array with `System.Object` as the element type, then client code can pass values of any type.</span></span>

<span data-ttu-id="3095e-185">F#'da parametre dizileri yalnızca yöntemlerle tanımlanabilir.</span><span class="sxs-lookup"><span data-stu-id="3095e-185">In F#, parameter arrays can only be defined in methods.</span></span> <span data-ttu-id="3095e-186">Bağımsız işlevlerde veya modüllerde tanımlanan işlevlerde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="3095e-186">They cannot be used in standalone functions or functions that are defined in modules.</span></span>

<span data-ttu-id="3095e-187">Özniteliği kullanarak bir parametre `ParamArray` dizisini tanımlarsınız.</span><span class="sxs-lookup"><span data-stu-id="3095e-187">You define a parameter array by using the `ParamArray` attribute.</span></span> <span data-ttu-id="3095e-188">Öznitelik `ParamArray` yalnızca son parametreye uygulanabilir.</span><span class="sxs-lookup"><span data-stu-id="3095e-188">The `ParamArray` attribute can only be applied to the last parameter.</span></span>

<span data-ttu-id="3095e-189">Aşağıdaki kod, hem parametre dizisini alan bir .NET yöntemini hem de parametre dizisini alan bir metodu olan F# türü tanımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="3095e-189">The following code illustrates both calling a .NET method that takes a parameter array and the definition of a type in F# that has a method that takes a parameter array.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/parameters-and-arguments-2/snippet3811.fs)]

<span data-ttu-id="3095e-190">Bir projede çalıştırıldığında, önceki kodun çıktısı aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="3095e-190">When run in a project, the output of the previous code is as follows:</span></span>

```console
a 1 10 Hello world 1 True
"a"
1
10.0
"Hello world"
1u
true
```

## <a name="see-also"></a><span data-ttu-id="3095e-191">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3095e-191">See also</span></span>

- [<span data-ttu-id="3095e-192">Üyeler</span><span class="sxs-lookup"><span data-stu-id="3095e-192">Members</span></span>](./members/index.md)
