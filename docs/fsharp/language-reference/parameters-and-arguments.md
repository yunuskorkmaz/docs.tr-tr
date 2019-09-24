---
title: Parametreler ve Bağımsız Değişkenler
description: Parametreleri tanımlama F# ve işlevlere, yöntemlere ve özelliklere bağımsız değişkenleri geçirme için dil desteği hakkında bilgi edinin.
ms.date: 05/16/2016
ms.openlocfilehash: e8094ffbc55870b5de75acb740aa2736ec6590a5
ms.sourcegitcommit: 56f1d1203d0075a461a10a301459d3aa452f4f47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2019
ms.locfileid: "71216831"
---
# <a name="parameters-and-arguments"></a><span data-ttu-id="29e45-103">Parametreler ve Bağımsız Değişkenler</span><span class="sxs-lookup"><span data-stu-id="29e45-103">Parameters and Arguments</span></span>

<span data-ttu-id="29e45-104">Bu konuda, parametreleri tanımlama ve işlevlere, yöntemlere ve özelliklere bağımsız değişkenleri geçirme için dil desteği açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="29e45-104">This topic describes language support for defining parameters and passing arguments to functions, methods, and properties.</span></span> <span data-ttu-id="29e45-105">Başvuruya göre geçme ve değişken sayıda bağımsız değişken alan yöntemler tanımlama ve kullanma hakkında bilgi içerir.</span><span class="sxs-lookup"><span data-stu-id="29e45-105">It includes information about how to pass by reference, and how to define and use methods that can take a variable number of arguments.</span></span>

## <a name="parameters-and-arguments"></a><span data-ttu-id="29e45-106">Parametreler ve Bağımsız Değişkenler</span><span class="sxs-lookup"><span data-stu-id="29e45-106">Parameters and Arguments</span></span>

<span data-ttu-id="29e45-107">Terimi *parametresi* , sağlanması beklenen değerlerin adlarını anlatmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="29e45-107">The term *parameter* is used to describe the names for values that are expected to be supplied.</span></span> <span data-ttu-id="29e45-108">*Bağımsız değişkeni* , her bir parametre için belirtilen değerler için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="29e45-108">The term *argument* is used for the values provided for each parameter.</span></span>

<span data-ttu-id="29e45-109">Parametreler demet veya curried formunda ya da ikisinin bir birleşimi içinde belirtilebilir.</span><span class="sxs-lookup"><span data-stu-id="29e45-109">Parameters can be specified in tuple or curried form, or in some combination of the two.</span></span> <span data-ttu-id="29e45-110">Açık bir parametre adı kullanarak bağımsız değişkenler geçirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="29e45-110">You can pass arguments by using an explicit parameter name.</span></span> <span data-ttu-id="29e45-111">Yöntemlerin parametreleri isteğe bağlı olarak belirtilebilir ve varsayılan bir değer verilir.</span><span class="sxs-lookup"><span data-stu-id="29e45-111">Parameters of methods can be specified as optional and given a default value.</span></span>

## <a name="parameter-patterns"></a><span data-ttu-id="29e45-112">Parametre desenleri</span><span class="sxs-lookup"><span data-stu-id="29e45-112">Parameter Patterns</span></span>

<span data-ttu-id="29e45-113">İşlevlere ve yöntemlere sağlanan parametreler, genel olarak boşluklarla ayrılmış desenlerdir.</span><span class="sxs-lookup"><span data-stu-id="29e45-113">Parameters supplied to functions and methods are, in general, patterns separated by spaces.</span></span> <span data-ttu-id="29e45-114">Bu, ilke içinde, [eşleşme ifadelerinde](match-expressions.md) açıklanan desenlerin herhangi birinin bir işlev veya üye için parametre listesinde kullanılabileceği anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="29e45-114">This means that, in principle, any of the patterns described in [Match Expressions](match-expressions.md) can be used in a parameter list for a function or member.</span></span>

<span data-ttu-id="29e45-115">Yöntemler genellikle bağımsız değişkenlerin geçirilerek demet biçimini kullanır.</span><span class="sxs-lookup"><span data-stu-id="29e45-115">Methods usually use the tuple form of passing arguments.</span></span> <span data-ttu-id="29e45-116">Bu, diğer .NET dillerinin perspektifinden daha net bir sonuca ulaşır çünkü demet formu, bağımsız değişkenlerin .NET yöntemlerine geçirilmesi ile eşleşir.</span><span class="sxs-lookup"><span data-stu-id="29e45-116">This achieves a clearer result from the perspective of other .NET languages because the tuple form matches the way arguments are passed in .NET methods.</span></span>

<span data-ttu-id="29e45-117">Curried form, genellikle bağlamalar kullanılarak `let` oluşturulan işlevlerle kullanılır.</span><span class="sxs-lookup"><span data-stu-id="29e45-117">The curried form is most often used with functions created by using `let` bindings.</span></span>

<span data-ttu-id="29e45-118">Aşağıdaki sözde kod, kayıt düzeni ve curried bağımsız değişkenlerinin örneklerini gösterir.</span><span class="sxs-lookup"><span data-stu-id="29e45-118">The following pseudocode shows examples of tuple and curried arguments.</span></span>

```fsharp
// Tuple form.
member this.SomeMethod(param1, param2) = ...
// Curried form.
let function1 param1 param2 = ...
```

<span data-ttu-id="29e45-119">Bazı bağımsız değişkenler diziler halinde olduğunda ve bazıları olmadığında birleştirilmiş formlar mümkündür.</span><span class="sxs-lookup"><span data-stu-id="29e45-119">Combined forms are possible when some arguments are in tuples and some are not.</span></span>

```fsharp
let function2 param1 (param2a, param2b) param3 = ...
```

<span data-ttu-id="29e45-120">Diğer desenler de parametre listelerinde kullanılabilir, ancak parametre deseni tüm olası girişlerle eşleşmezse, çalışma zamanında tamamlanmamış bir eşleşme olabilir.</span><span class="sxs-lookup"><span data-stu-id="29e45-120">Other patterns can also be used in parameter lists, but if the parameter pattern does not match all possible inputs, there might be an incomplete match at run time.</span></span> <span data-ttu-id="29e45-121">Bir bağımsız `MatchFailureException` değişkenin değeri, parametre listesinde belirtilen desenlerle eşleşmezse, bu özel durum oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="29e45-121">The exception `MatchFailureException` is generated when the value of an argument does not match the patterns specified in the parameter list.</span></span> <span data-ttu-id="29e45-122">Bir parametre deseninin tamamlanmamış eşleştirmelere izin verdiği durumlarda derleyici bir uyarı verir.</span><span class="sxs-lookup"><span data-stu-id="29e45-122">The compiler issues a warning when a parameter pattern allows for incomplete matches.</span></span> <span data-ttu-id="29e45-123">En az bir diğer model genellikle parametre listeleri için yararlıdır ve bu, joker karakter örüntü.</span><span class="sxs-lookup"><span data-stu-id="29e45-123">At least one other pattern is commonly useful for parameter lists, and that is the wildcard pattern.</span></span> <span data-ttu-id="29e45-124">Yalnızca sağlanan bağımsız değişkenleri yoksaymak istediğinizde joker karakter modelini bir parametre listesinde kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="29e45-124">You use the wildcard pattern in a parameter list when you simply want to ignore any arguments that are supplied.</span></span> <span data-ttu-id="29e45-125">Aşağıdaki kod, bir bağımsız değişken listesinde joker karakter deseninin kullanımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="29e45-125">The following code illustrates the use of the wildcard pattern in an argument list.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/parameters-and-arguments-1/snippet3801.fs)]

<span data-ttu-id="29e45-126">Joker karakter düzeni, aşağıdaki kodda olduğu gibi, normalde bir dize dizisi olarak sağlanan komut satırı bağımsız değişkenleri ile ilgilenmediğiniz zaman, bir programa yönelik ana giriş noktasında, örneğin, bir program için ana giriş noktasında, bir programın ana giriş noktasındaki bağımsız değişkenlere ihtiyaç duymadığınızda yararlı olabilir.</span><span class="sxs-lookup"><span data-stu-id="29e45-126">The wildcard pattern can be useful whenever you do not need the arguments passed in, such as in the main entry point to a program, when you are not interested in the command-line arguments that are normally supplied as a string array, as in the following code.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/parameters-and-arguments-1/snippet3802.fs)]

<span data-ttu-id="29e45-127">Bazen bağımsız değişkenlerde kullanılan diğer desenler, `as` düzen ve ayrılmış birleşimler ve etkin desenlerle ilişkili tanımlayıcı desenlerdir.</span><span class="sxs-lookup"><span data-stu-id="29e45-127">Other patterns that are sometimes used in arguments are the `as` pattern, and identifier patterns associated with discriminated unions and active patterns.</span></span> <span data-ttu-id="29e45-128">Tek durum ayrılmış birleşim modelini aşağıdaki gibi kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="29e45-128">You can use the single-case discriminated union pattern as follows.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/parameters-and-arguments-1/snippet3803.fs)]

<span data-ttu-id="29e45-129">Çıktı aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="29e45-129">The output is as follows.</span></span>

```console
Data begins at 0 and ends at 4 in string Et tu, Brute?
Et tu
```

<span data-ttu-id="29e45-130">Etkin desenler, aşağıdaki örnekte olduğu gibi, bir bağımsız değişken istenen biçime dönüştürülürken parametre olarak yararlı olabilir:</span><span class="sxs-lookup"><span data-stu-id="29e45-130">Active patterns can be useful as parameters, for example, when transforming an argument into a desired format, as in the following example:</span></span>

```fsharp
type Point = { x : float; y : float }

let (| Polar |) { x = x; y = y} =
    ( sqrt (x*x + y*y), System.Math.Atan (y/ x) )

let radius (Polar(r, _)) = r
let angle (Polar(_, theta)) = theta
```

<span data-ttu-id="29e45-131">Aşağıdaki kod satırında gösterildiği `as` gibi, eşleşen bir değeri yerel bir değer olarak depolamak için, bu kalıbı kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="29e45-131">You can use the `as` pattern to store a matched value as a local value, as is shown in the following line of code.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/parameters-and-arguments-1/snippet3805.fs)]

<span data-ttu-id="29e45-132">Bazen kullanılan başka bir model, işlevin gövdesi olarak, örtük bağımsız değişkende bir model eşleşmesi yapan bir lambda ifadesi sağlayarak adlandırılmamış en son bağımsız değişkeni bir işlev olarak bırakır.</span><span class="sxs-lookup"><span data-stu-id="29e45-132">Another pattern that is used occasionally is a function that leaves the last argument unnamed by providing, as the body of the function, a lambda expression that immediately performs a pattern match on the implicit argument.</span></span> <span data-ttu-id="29e45-133">Aşağıdaki kod satırı buna bir örnektir.</span><span class="sxs-lookup"><span data-stu-id="29e45-133">An example of this is the following line of code.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/parameters-and-arguments-1/snippet3804.fs)]

<span data-ttu-id="29e45-134">Bu kod, genel liste alan ve liste boşsa ve `true` `false` Aksi takdirde döndüren bir işlevi tanımlar.</span><span class="sxs-lookup"><span data-stu-id="29e45-134">This code defines a function that takes a generic list and returns `true` if the list is empty, and `false` otherwise.</span></span> <span data-ttu-id="29e45-135">Bu tür tekniklerin kullanımı, kodun okunmasını zorlaştırabilir.</span><span class="sxs-lookup"><span data-stu-id="29e45-135">The use of such techniques can make code more difficult to read.</span></span>

<span data-ttu-id="29e45-136">Bazen, tamamlanmamış eşleşmeleri içeren desenler yararlı olur, örneğin, programınızdaki listelerin yalnızca üç öğesi olduğunu biliyorsanız, aşağıdaki gibi bir deseni parametre listesinde kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="29e45-136">Occasionally, patterns that involve incomplete matches are useful, for example, if you know that the lists in your program have only three elements, you might use a pattern like the following in a parameter list.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/parameters-and-arguments-1/snippet3806.fs)]

<span data-ttu-id="29e45-137">Tamamlanmamış eşleşmelerin kullanıldığı desenlerin kullanımı, Hızlı Prototipleme ve diğer geçici kullanımlar için en iyi ayırmıştır.</span><span class="sxs-lookup"><span data-stu-id="29e45-137">The use of patterns that have incomplete matches is best reserved for quick prototyping and other temporary uses.</span></span> <span data-ttu-id="29e45-138">Derleyici bu tür kodlar için bir uyarı verebilir.</span><span class="sxs-lookup"><span data-stu-id="29e45-138">The compiler will issue a warning for such code.</span></span> <span data-ttu-id="29e45-139">Bu tür desenler tüm olası girdilerin genel durumunu kapsamaz ve bu nedenle bileşen API 'Leri için uygun değildir.</span><span class="sxs-lookup"><span data-stu-id="29e45-139">Such patterns cannot cover the general case of all possible inputs and therefore are not suitable for component APIs.</span></span>

## <a name="named-arguments"></a><span data-ttu-id="29e45-140">Adlandırılmış bağımsız değişkenler</span><span class="sxs-lookup"><span data-stu-id="29e45-140">Named Arguments</span></span>

<span data-ttu-id="29e45-141">Yöntemler için bağımsız değişkenler, virgülle ayrılmış bir bağımsız değişken listesindeki konuma göre belirtilebilir veya ad ve ardından bir eşittir işareti ve geçirilecek değer tarafından açıkça bir yönteme geçirilebilir.</span><span class="sxs-lookup"><span data-stu-id="29e45-141">Arguments for methods can be specified by position in a comma-separated argument list, or they can be passed to a method explicitly by providing the name, followed by an equal sign and the value to be passed in.</span></span> <span data-ttu-id="29e45-142">Ad sağlanarak belirtilmişse bildirimde kullanılan farklı bir sırada görünebilirler.</span><span class="sxs-lookup"><span data-stu-id="29e45-142">If specified by providing the name, they can appear in a different order from that used in the declaration.</span></span>

<span data-ttu-id="29e45-143">Adlandırılmış bağımsız değişkenler, API 'de yöntem parametrelerinin yeniden sıralanması gibi belirli değişiklik türlerine kod daha okunabilir ve daha uyumlu hale getirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="29e45-143">Named arguments can make code more readable and more adaptable to certain types of changes in the API, such as a reordering of method parameters.</span></span>

<span data-ttu-id="29e45-144">Adlandırılmış bağımsız değişkenlere yalnızca, for `let`-bağlanmadı işlevleri, işlev değerleri veya lambda ifadeleri için izin verilir.</span><span class="sxs-lookup"><span data-stu-id="29e45-144">Named arguments are allowed only for methods, not for `let`-bound functions, function values, or lambda expressions.</span></span>

<span data-ttu-id="29e45-145">Aşağıdaki kod örneği adlandırılmış bağımsız değişkenlerin kullanımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="29e45-145">The following code example demonstrates the use of named arguments.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/parameters-and-arguments-1/snippet3807.fs)]

<span data-ttu-id="29e45-146">Bir sınıf oluşturucusuna yapılan çağrıda, adlandırılmış bağımsız değişkenlerden benzer bir sözdizimi kullanarak sınıfının özelliklerinin değerlerini ayarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="29e45-146">In a call to a class constructor, you can set the values of properties of the class by using a syntax similar to that of named arguments.</span></span> <span data-ttu-id="29e45-147">Aşağıdaki örnek bu söz dizimini gösterir.</span><span class="sxs-lookup"><span data-stu-id="29e45-147">The following example shows this syntax.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet3506.fs)]

<span data-ttu-id="29e45-148">Daha fazla bilgi için bkz. [oluşturucularF#()](https://msdn.microsoft.com/library/2cd0ed07-d214-4125-8317-4f288af99f05).</span><span class="sxs-lookup"><span data-stu-id="29e45-148">For more information, see [Constructors (F#)](https://msdn.microsoft.com/library/2cd0ed07-d214-4125-8317-4f288af99f05).</span></span>

## <a name="optional-parameters"></a><span data-ttu-id="29e45-149">İsteğe Bağlı Parametreler</span><span class="sxs-lookup"><span data-stu-id="29e45-149">Optional Parameters</span></span>

<span data-ttu-id="29e45-150">Parametre adının önünde bir soru işareti kullanarak, bir yöntem için isteğe bağlı bir parametre belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="29e45-150">You can specify an optional parameter for a method by using a question mark in front of the parameter name.</span></span> <span data-ttu-id="29e45-151">F# İsteğe bağlı parametreler seçenek türü olarak yorumlanır. bu nedenle, `match` ve `None`ile `Some` bir ifade kullanarak bunları seçenek türlerinin sorgulandığı düzenli bir şekilde sorgulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="29e45-151">Optional parameters are interpreted as the F# option type, so you can query them in the regular way that option types are queried, by using a `match` expression with `Some` and `None`.</span></span> <span data-ttu-id="29e45-152">İsteğe bağlı parametrelere, bağlamalar kullanılarak `let` oluşturulan işlevlerde değil, yalnızca üyelerde izin verilir.</span><span class="sxs-lookup"><span data-stu-id="29e45-152">Optional parameters are permitted only on members, not on functions created by using `let` bindings.</span></span>

<span data-ttu-id="29e45-153">İsteğe bağlı değerleri, `?arg=None` `?arg=Some(3)` veya gibi parametre adına göre yönteme geçirebilirsiniz. `?arg=arg`</span><span class="sxs-lookup"><span data-stu-id="29e45-153">You can pass existing optional values to method by parameter name, such as `?arg=None` or `?arg=Some(3)` or `?arg=arg`.</span></span> <span data-ttu-id="29e45-154">Bu, isteğe bağlı bağımsız değişkenleri başka bir yönteme geçiren bir yöntem oluştururken yararlı olabilir.</span><span class="sxs-lookup"><span data-stu-id="29e45-154">This can be useful when building a method that passes optional arguments to another method.</span></span>

<span data-ttu-id="29e45-155">İsteğe bağlı bir bağımsız değişkenin varsayılan `defaultArg`değerini ayarlayan bir işlevi de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="29e45-155">You can also use a function `defaultArg`, which sets a default value of an optional argument.</span></span> <span data-ttu-id="29e45-156">`defaultArg` İşlevi, isteğe bağlı parametreyi ilk bağımsız değişken olarak ve varsayılan değeri ikinci olarak alır.</span><span class="sxs-lookup"><span data-stu-id="29e45-156">The `defaultArg` function takes the optional parameter as the first argument and the default value as the second.</span></span>

<span data-ttu-id="29e45-157">Aşağıdaki örnek, isteğe bağlı parametrelerin kullanımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="29e45-157">The following example illustrates the use of optional parameters.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/parameters-and-arguments-1/snippet3808.fs)]

<span data-ttu-id="29e45-158">Çıktı aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="29e45-158">The output is as follows.</span></span>

```console
Baud Rate: 9600 Duplex: Full Parity: false
Baud Rate: 4800 Duplex: Half Parity: false
Baud Rate: 300 Duplex: Half Parity: true
Baud Rate: 9600 Duplex: Full Parity: false
Baud Rate: 9600 Duplex: Full Parity: false
Baud Rate: 4800 Duplex: Half Parity: false
```

<span data-ttu-id="29e45-159">Ve Visual Basic birlikte çalışabilirliğine sahip olmak için, içindeki C# `[<Optional; DefaultParameterValue<(...)>]` F#özniteliklerini kullanarak çağıranların isteğe bağlı olarak bir bağımsız değişken görmesini sağlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="29e45-159">For the purposes of C# and Visual Basic interop you can use the attributes `[<Optional; DefaultParameterValue<(...)>]` in F#, so that callers will see an argument as optional.</span></span> <span data-ttu-id="29e45-160">Bu, bağımsız değişkeninin ' de C# `MyMethod(int i = 3)`olduğu gibi isteğe bağlı olarak tanımlanması ile eşdeğerdir.</span><span class="sxs-lookup"><span data-stu-id="29e45-160">This is equivalent to defining the argument as optional in C# as in `MyMethod(int i = 3)`.</span></span>

```fsharp
open System
open System.Runtime.InteropServices
type C =
    static member Foo([<Optional; DefaultParameterValue("Hello world")>] message) =
        printfn "%s" message
```

<span data-ttu-id="29e45-161">Ayrıca, varsayılan parametre değeri olarak yeni bir nesne belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="29e45-161">You can also specify a new object as a default parameter value.</span></span> <span data-ttu-id="29e45-162">Örneğin, `Foo` üyenin bunun yerine giriş olarak isteğe bağlı `CancellationToken` olması olabilir:</span><span class="sxs-lookup"><span data-stu-id="29e45-162">For example, the `Foo` member could have an optional `CancellationToken` as input instead:</span></span>

```fsharp
open System.Threading
open System.Runtime.InteropServices
type C =
    static member Foo([<Optional; DefaultParameterValue(CancellationToken())>] ct: CancellationToken) =
        printfn "%A" ct
```

<span data-ttu-id="29e45-163">Bağımsız değişkeni `DefaultParameterValue` olarak verilen değerin parametrenin türüyle eşleşmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="29e45-163">The value given as argument to `DefaultParameterValue` must match the type of the parameter.</span></span> <span data-ttu-id="29e45-164">Örneğin, aşağıdakilere izin verilmez:</span><span class="sxs-lookup"><span data-stu-id="29e45-164">For example, the following is not allowed:</span></span>

```fsharp
type C =
    static member Wrong([<Optional; DefaultParameterValue("string")>] i:int) = ()
```

<span data-ttu-id="29e45-165">Bu durumda, derleyici bir uyarı oluşturur ve iki özniteliği de tamamen yoksayar.</span><span class="sxs-lookup"><span data-stu-id="29e45-165">In this case, the compiler generates a warning and will ignore both attributes altogether.</span></span> <span data-ttu-id="29e45-166">Diğer bir deyişle, derleyici `null` yanlış türü (ör. `[<Optional; DefaultParameterValue(null:obj)>] o:obj`), aksi takdirde, varsayılan değerin tür-açıklama olması gerektiğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="29e45-166">Note that the default value `null` needs to be type-annotated, as otherwise the compiler infers the wrong type, i.e. `[<Optional; DefaultParameterValue(null:obj)>] o:obj`.</span></span>

## <a name="passing-by-reference"></a><span data-ttu-id="29e45-167">Başvuruya göre geçirme</span><span class="sxs-lookup"><span data-stu-id="29e45-167">Passing by Reference</span></span>

<span data-ttu-id="29e45-168">Bir F# değerin başvuruya göre geçirilmesi, yönetilen işaretçi türleri olan [ByRef 'ler](byrefs.md)içerir.</span><span class="sxs-lookup"><span data-stu-id="29e45-168">Passing an F# value by reference involves [byrefs](byrefs.md), which are managed pointer types.</span></span> <span data-ttu-id="29e45-169">Kullanılacak tür ile ilgili kılavuz aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="29e45-169">Guidance for which type to use is as follows:</span></span>

- <span data-ttu-id="29e45-170">Yalnızca `inref<'T>` işaretçiyi okumanız gerekiyorsa kullanın.</span><span class="sxs-lookup"><span data-stu-id="29e45-170">Use `inref<'T>` if you only need to read the pointer.</span></span>
- <span data-ttu-id="29e45-171">Yalnızca `outref<'T>` işaretçiye yazmanız gerekiyorsa kullanın.</span><span class="sxs-lookup"><span data-stu-id="29e45-171">Use `outref<'T>` if you only need to write to the pointer.</span></span>
- <span data-ttu-id="29e45-172">Hem `byref<'T>` okuma hem de işaretçiye yazma gerekiyorsa kullanın.</span><span class="sxs-lookup"><span data-stu-id="29e45-172">Use `byref<'T>` if you need to both read from and write to the pointer.</span></span>

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

<span data-ttu-id="29e45-173">Parametresi bir işaretçi olduğundan ve değer değişebilir olduğundan, değer üzerinde yapılan tüm değişiklikler işlevin yürütülmesinden sonra tutulur.</span><span class="sxs-lookup"><span data-stu-id="29e45-173">Because the parameter is a pointer and the value is mutable, any changes to the value are retained after the execution of the function.</span></span>

<span data-ttu-id="29e45-174">.NET kitaplığı yöntemlerinde herhangi `out` bir parametreyi depolamak için bir kayıt düzeni değerini dönüş değeri olarak kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="29e45-174">You can use a tuple as a return value to store any `out` parameters in .NET library methods.</span></span> <span data-ttu-id="29e45-175">Alternatif olarak, `out` parametresini bir `byref` parametre olarak kabul edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="29e45-175">Alternatively, you can treat the `out` parameter as a `byref` parameter.</span></span> <span data-ttu-id="29e45-176">Aşağıdaki kod örneğinde her iki yol da gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="29e45-176">The following code example illustrates both ways.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/parameters-and-arguments-1/snippet3810.fs)]

## <a name="parameter-arrays"></a><span data-ttu-id="29e45-177">Parametre Dizileri</span><span class="sxs-lookup"><span data-stu-id="29e45-177">Parameter Arrays</span></span>

<span data-ttu-id="29e45-178">Bazen heterojen türden rastgele sayıda parametre alan bir işlev tanımlanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="29e45-178">Occasionally it is necessary to define a function that takes an arbitrary number of parameters of heterogeneous type.</span></span> <span data-ttu-id="29e45-179">Tüm olası aşırı yüklenmiş yöntemlerin, kullanılabilecek tüm türlere yönelik olarak oluşturulması pratik değildir.</span><span class="sxs-lookup"><span data-stu-id="29e45-179">It would not be practical to create all the possible overloaded methods to account for all the types that could be used.</span></span> <span data-ttu-id="29e45-180">.NET uygulamaları, parametre dizisi özelliği aracılığıyla bu tür yöntemler için destek sağlar.</span><span class="sxs-lookup"><span data-stu-id="29e45-180">The .NET implementations provide support for such methods through the parameter array feature.</span></span> <span data-ttu-id="29e45-181">İmzasında parametre dizisi alan bir yöntem, rastgele sayıda parametre ile birlikte etkinleştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="29e45-181">A method that takes a parameter array in its signature can be provided with an arbitrary number of parameters.</span></span> <span data-ttu-id="29e45-182">Parametreler bir diziye konur.</span><span class="sxs-lookup"><span data-stu-id="29e45-182">The parameters are put into an array.</span></span> <span data-ttu-id="29e45-183">Dizi öğelerinin türü, işleve geçirilebilecek parametre türlerini belirler.</span><span class="sxs-lookup"><span data-stu-id="29e45-183">The type of the array elements determines the parameter types that can be passed to the function.</span></span> <span data-ttu-id="29e45-184">Parametre dizisini `System.Object` öğesi türü olarak tanımlarsanız, istemci kodu herhangi bir türdeki değerleri geçirebilir.</span><span class="sxs-lookup"><span data-stu-id="29e45-184">If you define the parameter array with `System.Object` as the element type, then client code can pass values of any type.</span></span>

<span data-ttu-id="29e45-185">İçinde F#, parametre dizileri yalnızca yöntemlerde tanımlanabilir.</span><span class="sxs-lookup"><span data-stu-id="29e45-185">In F#, parameter arrays can only be defined in methods.</span></span> <span data-ttu-id="29e45-186">Bunlar tek başına işlevlerde veya modüllerde tanımlanmış işlevlerde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="29e45-186">They cannot be used in standalone functions or functions that are defined in modules.</span></span>

<span data-ttu-id="29e45-187">`ParamArray` Özniteliğini kullanarak bir parametre dizisi tanımlarsınız.</span><span class="sxs-lookup"><span data-stu-id="29e45-187">You define a parameter array by using the `ParamArray` attribute.</span></span> <span data-ttu-id="29e45-188">`ParamArray` Özniteliği yalnızca son parametreye uygulanabilir.</span><span class="sxs-lookup"><span data-stu-id="29e45-188">The `ParamArray` attribute can only be applied to the last parameter.</span></span>

<span data-ttu-id="29e45-189">Aşağıdaki kod, her ikisi de bir parametre dizisi alan ve içindeki F# bir tür tanımı bir parametre dizisi alan bir .net yönteminin çağrılmasını göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="29e45-189">The following code illustrates both calling a .NET method that takes a parameter array and the definition of a type in F# that has a method that takes a parameter array.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/parameters-and-arguments-2/snippet3811.fs)]

<span data-ttu-id="29e45-190">Bir projede çalıştırıldığında, önceki kodun çıktısı aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="29e45-190">When run in a project, the output of the previous code is as follows:</span></span>

```console
a 1 10 Hello world 1 True
"a"
1
10.0
"Hello world"
1u
true
```

## <a name="see-also"></a><span data-ttu-id="29e45-191">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="29e45-191">See also</span></span>

- [<span data-ttu-id="29e45-192">Üyeler</span><span class="sxs-lookup"><span data-stu-id="29e45-192">Members</span></span>](./members/index.md)
