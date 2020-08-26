---
title: Parametreler ve Bağımsız Değişkenler
description: 'Parametreleri tanımlama ve işlevlere, yöntemlere ve özelliklere bağımsız değişkenleri geçirme için F # dil desteği hakkında bilgi edinin.'
ms.date: 08/15/2020
ms.openlocfilehash: 6564fd31105427683af8fc6280672e638737e9b5
ms.sourcegitcommit: 9c45035b781caebc63ec8ecf912dc83fb6723b1f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/25/2020
ms.locfileid: "88811528"
---
# <a name="parameters-and-arguments"></a><span data-ttu-id="6904c-103">Parametreler ve Bağımsız Değişkenler</span><span class="sxs-lookup"><span data-stu-id="6904c-103">Parameters and Arguments</span></span>

<span data-ttu-id="6904c-104">Bu konuda, parametreleri tanımlama ve işlevlere, yöntemlere ve özelliklere bağımsız değişkenleri geçirme için dil desteği açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="6904c-104">This topic describes language support for defining parameters and passing arguments to functions, methods, and properties.</span></span> <span data-ttu-id="6904c-105">Başvuruya göre geçme ve değişken sayıda bağımsız değişken alan yöntemler tanımlama ve kullanma hakkında bilgi içerir.</span><span class="sxs-lookup"><span data-stu-id="6904c-105">It includes information about how to pass by reference, and how to define and use methods that can take a variable number of arguments.</span></span>

## <a name="parameters-and-arguments"></a><span data-ttu-id="6904c-106">Parametreler ve Bağımsız Değişkenler</span><span class="sxs-lookup"><span data-stu-id="6904c-106">Parameters and Arguments</span></span>

<span data-ttu-id="6904c-107">Terimi *parametresi* , sağlanması beklenen değerlerin adlarını anlatmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="6904c-107">The term *parameter* is used to describe the names for values that are expected to be supplied.</span></span> <span data-ttu-id="6904c-108">*Bağımsız değişkeni* , her bir parametre için belirtilen değerler için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="6904c-108">The term *argument* is used for the values provided for each parameter.</span></span>

<span data-ttu-id="6904c-109">Parametreler demet veya curried formunda ya da ikisinin bir birleşimi içinde belirtilebilir.</span><span class="sxs-lookup"><span data-stu-id="6904c-109">Parameters can be specified in tuple or curried form, or in some combination of the two.</span></span> <span data-ttu-id="6904c-110">Açık bir parametre adı kullanarak bağımsız değişkenler geçirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6904c-110">You can pass arguments by using an explicit parameter name.</span></span> <span data-ttu-id="6904c-111">Yöntemlerin parametreleri isteğe bağlı olarak belirtilebilir ve varsayılan bir değer verilir.</span><span class="sxs-lookup"><span data-stu-id="6904c-111">Parameters of methods can be specified as optional and given a default value.</span></span>

## <a name="parameter-patterns"></a><span data-ttu-id="6904c-112">Parametre desenleri</span><span class="sxs-lookup"><span data-stu-id="6904c-112">Parameter Patterns</span></span>

<span data-ttu-id="6904c-113">İşlevlere ve yöntemlere sağlanan parametreler, genel olarak boşluklarla ayrılmış desenlerdir.</span><span class="sxs-lookup"><span data-stu-id="6904c-113">Parameters supplied to functions and methods are, in general, patterns separated by spaces.</span></span> <span data-ttu-id="6904c-114">Bu, ilke içinde, [eşleşme ifadelerinde](match-expressions.md) açıklanan desenlerin herhangi birinin bir işlev veya üye için parametre listesinde kullanılabileceği anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="6904c-114">This means that, in principle, any of the patterns described in [Match Expressions](match-expressions.md) can be used in a parameter list for a function or member.</span></span>

<span data-ttu-id="6904c-115">Yöntemler genellikle bağımsız değişkenlerin geçirilerek demet biçimini kullanır.</span><span class="sxs-lookup"><span data-stu-id="6904c-115">Methods usually use the tuple form of passing arguments.</span></span> <span data-ttu-id="6904c-116">Bu, diğer .NET dillerinin perspektifinden daha net bir sonuca ulaşır çünkü demet formu, bağımsız değişkenlerin .NET yöntemlerine geçirilmesi ile eşleşir.</span><span class="sxs-lookup"><span data-stu-id="6904c-116">This achieves a clearer result from the perspective of other .NET languages because the tuple form matches the way arguments are passed in .NET methods.</span></span>

<span data-ttu-id="6904c-117">Curried form, genellikle bağlamalar kullanılarak oluşturulan işlevlerle kullanılır `let` .</span><span class="sxs-lookup"><span data-stu-id="6904c-117">The curried form is most often used with functions created by using `let` bindings.</span></span>

<span data-ttu-id="6904c-118">Aşağıdaki sözde kod, kayıt düzeni ve curried bağımsız değişkenlerinin örneklerini gösterir.</span><span class="sxs-lookup"><span data-stu-id="6904c-118">The following pseudocode shows examples of tuple and curried arguments.</span></span>

```fsharp
// Tuple form.
member this.SomeMethod(param1, param2) = ...
// Curried form.
let function1 param1 param2 = ...
```

<span data-ttu-id="6904c-119">Bazı bağımsız değişkenler diziler halinde olduğunda ve bazıları olmadığında birleştirilmiş formlar mümkündür.</span><span class="sxs-lookup"><span data-stu-id="6904c-119">Combined forms are possible when some arguments are in tuples and some are not.</span></span>

```fsharp
let function2 param1 (param2a, param2b) param3 = ...
```

<span data-ttu-id="6904c-120">Diğer desenler de parametre listelerinde kullanılabilir, ancak parametre deseni tüm olası girişlerle eşleşmezse, çalışma zamanında tamamlanmamış bir eşleşme olabilir.</span><span class="sxs-lookup"><span data-stu-id="6904c-120">Other patterns can also be used in parameter lists, but if the parameter pattern does not match all possible inputs, there might be an incomplete match at run time.</span></span> <span data-ttu-id="6904c-121">`MatchFailureException`Bir bağımsız değişkenin değeri, parametre listesinde belirtilen desenlerle eşleşmezse, bu özel durum oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="6904c-121">The exception `MatchFailureException` is generated when the value of an argument does not match the patterns specified in the parameter list.</span></span> <span data-ttu-id="6904c-122">Bir parametre deseninin tamamlanmamış eşleştirmelere izin verdiği durumlarda derleyici bir uyarı verir.</span><span class="sxs-lookup"><span data-stu-id="6904c-122">The compiler issues a warning when a parameter pattern allows for incomplete matches.</span></span> <span data-ttu-id="6904c-123">En az bir diğer model genellikle parametre listeleri için yararlıdır ve bu, joker karakter örüntü.</span><span class="sxs-lookup"><span data-stu-id="6904c-123">At least one other pattern is commonly useful for parameter lists, and that is the wildcard pattern.</span></span> <span data-ttu-id="6904c-124">Yalnızca sağlanan bağımsız değişkenleri yoksaymak istediğinizde joker karakter modelini bir parametre listesinde kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="6904c-124">You use the wildcard pattern in a parameter list when you simply want to ignore any arguments that are supplied.</span></span> <span data-ttu-id="6904c-125">Aşağıdaki kod, bir bağımsız değişken listesinde joker karakter deseninin kullanımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="6904c-125">The following code illustrates the use of the wildcard pattern in an argument list.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/parameters-and-arguments-1/snippet3801.fs)]

<span data-ttu-id="6904c-126">Joker karakter düzeni, aşağıdaki kodda olduğu gibi, normalde bir dize dizisi olarak sağlanan komut satırı bağımsız değişkenleri ile ilgilenmediğiniz zaman, bir programa yönelik ana giriş noktasında, örneğin, bir program için ana giriş noktasında, bir programın ana giriş noktasındaki bağımsız değişkenlere ihtiyaç duymadığınızda yararlı olabilir.</span><span class="sxs-lookup"><span data-stu-id="6904c-126">The wildcard pattern can be useful whenever you do not need the arguments passed in, such as in the main entry point to a program, when you are not interested in the command-line arguments that are normally supplied as a string array, as in the following code.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/parameters-and-arguments-1/snippet3802.fs)]

<span data-ttu-id="6904c-127">Bazen bağımsız değişkenlerde kullanılan diğer desenler `as` , düzen ve ayrılmış birleşimler ve etkin desenlerle ilişkili tanımlayıcı desenlerdir.</span><span class="sxs-lookup"><span data-stu-id="6904c-127">Other patterns that are sometimes used in arguments are the `as` pattern, and identifier patterns associated with discriminated unions and active patterns.</span></span> <span data-ttu-id="6904c-128">Tek durum ayrılmış birleşim modelini aşağıdaki gibi kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6904c-128">You can use the single-case discriminated union pattern as follows.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/parameters-and-arguments-1/snippet3803.fs)]

<span data-ttu-id="6904c-129">Çıktı aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="6904c-129">The output is as follows.</span></span>

```console
Data begins at 0 and ends at 4 in string Et tu, Brute?
Et tu
```

<span data-ttu-id="6904c-130">Etkin desenler, aşağıdaki örnekte olduğu gibi, bir bağımsız değişken istenen biçime dönüştürülürken parametre olarak yararlı olabilir:</span><span class="sxs-lookup"><span data-stu-id="6904c-130">Active patterns can be useful as parameters, for example, when transforming an argument into a desired format, as in the following example:</span></span>

```fsharp
type Point = { x : float; y : float }

let (| Polar |) { x = x; y = y} =
    ( sqrt (x*x + y*y), System.Math.Atan (y/ x) )

let radius (Polar(r, _)) = r
let angle (Polar(_, theta)) = theta
```

<span data-ttu-id="6904c-131">`as`Aşağıdaki kod satırında gösterildiği gibi, eşleşen bir değeri yerel bir değer olarak depolamak için, bu kalıbı kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6904c-131">You can use the `as` pattern to store a matched value as a local value, as is shown in the following line of code.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/parameters-and-arguments-1/snippet3805.fs)]

<span data-ttu-id="6904c-132">Bazen kullanılan başka bir model, işlevin gövdesi olarak, örtük bağımsız değişkende bir model eşleşmesi yapan bir lambda ifadesi sağlayarak adlandırılmamış en son bağımsız değişkeni bir işlev olarak bırakır.</span><span class="sxs-lookup"><span data-stu-id="6904c-132">Another pattern that is used occasionally is a function that leaves the last argument unnamed by providing, as the body of the function, a lambda expression that immediately performs a pattern match on the implicit argument.</span></span> <span data-ttu-id="6904c-133">Aşağıdaki kod satırı buna bir örnektir.</span><span class="sxs-lookup"><span data-stu-id="6904c-133">An example of this is the following line of code.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/parameters-and-arguments-1/snippet3804.fs)]

<span data-ttu-id="6904c-134">Bu kod, genel liste alan ve `true` Liste boşsa ve aksi takdirde döndüren bir işlevi tanımlar `false` .</span><span class="sxs-lookup"><span data-stu-id="6904c-134">This code defines a function that takes a generic list and returns `true` if the list is empty, and `false` otherwise.</span></span> <span data-ttu-id="6904c-135">Bu tür tekniklerin kullanımı, kodun okunmasını zorlaştırabilir.</span><span class="sxs-lookup"><span data-stu-id="6904c-135">The use of such techniques can make code more difficult to read.</span></span>

<span data-ttu-id="6904c-136">Bazen, tamamlanmamış eşleşmeleri içeren desenler yararlı olur, örneğin, programınızdaki listelerin yalnızca üç öğesi olduğunu biliyorsanız, aşağıdaki gibi bir deseni parametre listesinde kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6904c-136">Occasionally, patterns that involve incomplete matches are useful, for example, if you know that the lists in your program have only three elements, you might use a pattern like the following in a parameter list.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/parameters-and-arguments-1/snippet3806.fs)]

<span data-ttu-id="6904c-137">Tamamlanmamış eşleşmelerin kullanıldığı desenlerin kullanımı, Hızlı Prototipleme ve diğer geçici kullanımlar için en iyi ayırmıştır.</span><span class="sxs-lookup"><span data-stu-id="6904c-137">The use of patterns that have incomplete matches is best reserved for quick prototyping and other temporary uses.</span></span> <span data-ttu-id="6904c-138">Derleyici bu tür kodlar için bir uyarı verebilir.</span><span class="sxs-lookup"><span data-stu-id="6904c-138">The compiler will issue a warning for such code.</span></span> <span data-ttu-id="6904c-139">Bu tür desenler tüm olası girdilerin genel durumunu kapsamaz ve bu nedenle bileşen API 'Leri için uygun değildir.</span><span class="sxs-lookup"><span data-stu-id="6904c-139">Such patterns cannot cover the general case of all possible inputs and therefore are not suitable for component APIs.</span></span>

## <a name="named-arguments"></a><span data-ttu-id="6904c-140">Adlandırılmış bağımsız değişkenler</span><span class="sxs-lookup"><span data-stu-id="6904c-140">Named Arguments</span></span>

<span data-ttu-id="6904c-141">Yöntemler için bağımsız değişkenler, virgülle ayrılmış bir bağımsız değişken listesindeki konuma göre belirtilebilir veya ad ve ardından bir eşittir işareti ve geçirilecek değer tarafından açıkça bir yönteme geçirilebilir.</span><span class="sxs-lookup"><span data-stu-id="6904c-141">Arguments for methods can be specified by position in a comma-separated argument list, or they can be passed to a method explicitly by providing the name, followed by an equal sign and the value to be passed in.</span></span> <span data-ttu-id="6904c-142">Ad sağlanarak belirtilmişse bildirimde kullanılan farklı bir sırada görünebilirler.</span><span class="sxs-lookup"><span data-stu-id="6904c-142">If specified by providing the name, they can appear in a different order from that used in the declaration.</span></span>

<span data-ttu-id="6904c-143">Adlandırılmış bağımsız değişkenler, API 'de yöntem parametrelerinin yeniden sıralanması gibi belirli değişiklik türlerine kod daha okunabilir ve daha uyumlu hale getirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6904c-143">Named arguments can make code more readable and more adaptable to certain types of changes in the API, such as a reordering of method parameters.</span></span>

<span data-ttu-id="6904c-144">Adlandırılmış bağımsız değişkenlere yalnızca, for `let` -bağlanmadı işlevleri, işlev değerleri veya lambda ifadeleri için izin verilir.</span><span class="sxs-lookup"><span data-stu-id="6904c-144">Named arguments are allowed only for methods, not for `let`-bound functions, function values, or lambda expressions.</span></span>

<span data-ttu-id="6904c-145">Aşağıdaki kod örneği adlandırılmış bağımsız değişkenlerin kullanımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="6904c-145">The following code example demonstrates the use of named arguments.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/parameters-and-arguments-1/snippet3807.fs)]

<span data-ttu-id="6904c-146">Bir sınıf oluşturucusuna yapılan çağrıda, adlandırılmış bağımsız değişkenlerden benzer bir sözdizimi kullanarak sınıfının özelliklerinin değerlerini ayarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6904c-146">In a call to a class constructor, you can set the values of properties of the class by using a syntax similar to that of named arguments.</span></span> <span data-ttu-id="6904c-147">Aşağıdaki örnek bu söz dizimini gösterir.</span><span class="sxs-lookup"><span data-stu-id="6904c-147">The following example shows this syntax.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet3506.fs)]

<span data-ttu-id="6904c-148">Daha fazla bilgi için bkz. [oluşturucular (F #)](members/constructors.md).</span><span class="sxs-lookup"><span data-stu-id="6904c-148">For more information, see [Constructors (F#)](members/constructors.md).</span></span>

## <a name="optional-parameters"></a><span data-ttu-id="6904c-149">İsteğe Bağlı Parametreler</span><span class="sxs-lookup"><span data-stu-id="6904c-149">Optional Parameters</span></span>

<span data-ttu-id="6904c-150">Parametre adının önünde bir soru işareti kullanarak, bir yöntem için isteğe bağlı bir parametre belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6904c-150">You can specify an optional parameter for a method by using a question mark in front of the parameter name.</span></span> <span data-ttu-id="6904c-151">İsteğe bağlı parametreler F # seçenek türü olarak yorumlanır. bu nedenle, ve ile bir ifade kullanarak bunları seçenek türlerinin sorgulandığı normal şekilde sorgulayabilirsiniz `match` `Some` `None` .</span><span class="sxs-lookup"><span data-stu-id="6904c-151">Optional parameters are interpreted as the F# option type, so you can query them in the regular way that option types are queried, by using a `match` expression with `Some` and `None`.</span></span> <span data-ttu-id="6904c-152">İsteğe bağlı parametrelere, bağlamalar kullanılarak oluşturulan işlevlerde değil, yalnızca üyelerde izin verilir `let` .</span><span class="sxs-lookup"><span data-stu-id="6904c-152">Optional parameters are permitted only on members, not on functions created by using `let` bindings.</span></span>

<span data-ttu-id="6904c-153">İsteğe bağlı değerleri, veya gibi parametre adına göre yönteme geçirebilirsiniz `?arg=None` `?arg=Some(3)` `?arg=arg` .</span><span class="sxs-lookup"><span data-stu-id="6904c-153">You can pass existing optional values to method by parameter name, such as `?arg=None` or `?arg=Some(3)` or `?arg=arg`.</span></span> <span data-ttu-id="6904c-154">Bu, isteğe bağlı bağımsız değişkenleri başka bir yönteme geçiren bir yöntem oluştururken yararlı olabilir.</span><span class="sxs-lookup"><span data-stu-id="6904c-154">This can be useful when building a method that passes optional arguments to another method.</span></span>

<span data-ttu-id="6904c-155">`defaultArg`İsteğe bağlı bir bağımsız değişkenin varsayılan değerini ayarlayan bir işlevi de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6904c-155">You can also use a function `defaultArg`, which sets a default value of an optional argument.</span></span> <span data-ttu-id="6904c-156">`defaultArg`İşlevi, isteğe bağlı parametreyi ilk bağımsız değişken olarak ve varsayılan değeri ikinci olarak alır.</span><span class="sxs-lookup"><span data-stu-id="6904c-156">The `defaultArg` function takes the optional parameter as the first argument and the default value as the second.</span></span>

<span data-ttu-id="6904c-157">Aşağıdaki örnek, isteğe bağlı parametrelerin kullanımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="6904c-157">The following example illustrates the use of optional parameters.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/parameters-and-arguments-1/snippet3808.fs)]

<span data-ttu-id="6904c-158">Çıktı aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="6904c-158">The output is as follows.</span></span>

```console
Baud Rate: 9600 Duplex: Full Parity: false
Baud Rate: 4800 Duplex: Half Parity: false
Baud Rate: 300 Duplex: Half Parity: true
Baud Rate: 9600 Duplex: Full Parity: false
Baud Rate: 9600 Duplex: Full Parity: false
Baud Rate: 4800 Duplex: Half Parity: false
```

<span data-ttu-id="6904c-159">C# ve Visual Basic birlikte çalışabilirliğine yönelik `[<Optional; DefaultParameterValue<(...)>]` olarak, F # içindeki öznitelikleri kullanarak çağıranların isteğe bağlı olarak bir bağımsız değişken görmesini sağlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6904c-159">For the purposes of C# and Visual Basic interop you can use the attributes `[<Optional; DefaultParameterValue<(...)>]` in F#, so that callers will see an argument as optional.</span></span> <span data-ttu-id="6904c-160">Bu, bağımsız değişkeni C# ' de olduğu gibi isteğe bağlı olarak tanımlamaya eşdeğerdir `MyMethod(int i = 3)` .</span><span class="sxs-lookup"><span data-stu-id="6904c-160">This is equivalent to defining the argument as optional in C# as in `MyMethod(int i = 3)`.</span></span>

```fsharp
open System
open System.Runtime.InteropServices
type C =
    static member Foo([<Optional; DefaultParameterValue("Hello world")>] message) =
        printfn "%s" message
```

<span data-ttu-id="6904c-161">Ayrıca, varsayılan parametre değeri olarak yeni bir nesne belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6904c-161">You can also specify a new object as a default parameter value.</span></span> <span data-ttu-id="6904c-162">Örneğin, `Foo` üyenin `CancellationToken` bunun yerine giriş olarak isteğe bağlı olması olabilir:</span><span class="sxs-lookup"><span data-stu-id="6904c-162">For example, the `Foo` member could have an optional `CancellationToken` as input instead:</span></span>

```fsharp
open System.Threading
open System.Runtime.InteropServices
type C =
    static member Foo([<Optional; DefaultParameterValue(CancellationToken())>] ct: CancellationToken) =
        printfn "%A" ct
```

<span data-ttu-id="6904c-163">Bağımsız değişkeni olarak verilen değerin `DefaultParameterValue` parametrenin türüyle eşleşmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="6904c-163">The value given as argument to `DefaultParameterValue` must match the type of the parameter.</span></span> <span data-ttu-id="6904c-164">Örneğin, aşağıdakilere izin verilmez:</span><span class="sxs-lookup"><span data-stu-id="6904c-164">For example, the following is not allowed:</span></span>

```fsharp
type C =
    static member Wrong([<Optional; DefaultParameterValue("string")>] i:int) = ()
```

<span data-ttu-id="6904c-165">Bu durumda, derleyici bir uyarı oluşturur ve iki özniteliği de tamamen yoksayar.</span><span class="sxs-lookup"><span data-stu-id="6904c-165">In this case, the compiler generates a warning and will ignore both attributes altogether.</span></span> <span data-ttu-id="6904c-166">Diğer bir deyişle, `null` derleyici yanlış türü (ör.), aksi takdirde, varsayılan değerin tür-açıklama olması gerektiğini unutmayın `[<Optional; DefaultParameterValue(null:obj)>] o:obj` .</span><span class="sxs-lookup"><span data-stu-id="6904c-166">Note that the default value `null` needs to be type-annotated, as otherwise the compiler infers the wrong type, i.e. `[<Optional; DefaultParameterValue(null:obj)>] o:obj`.</span></span>

## <a name="passing-by-reference"></a><span data-ttu-id="6904c-167">Başvuruya göre geçirme</span><span class="sxs-lookup"><span data-stu-id="6904c-167">Passing by Reference</span></span>

<span data-ttu-id="6904c-168">Bir F # değerinin başvuruya geçirilmesi, yönetilen işaretçi türleri olan [ByRef](byrefs.md)'ler ile ilgilidir.</span><span class="sxs-lookup"><span data-stu-id="6904c-168">Passing an F# value by reference involves [byrefs](byrefs.md), which are managed pointer types.</span></span> <span data-ttu-id="6904c-169">Kullanılacak tür ile ilgili kılavuz aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="6904c-169">Guidance for which type to use is as follows:</span></span>

- <span data-ttu-id="6904c-170">`inref<'T>`Yalnızca işaretçiyi okumanız gerekiyorsa kullanın.</span><span class="sxs-lookup"><span data-stu-id="6904c-170">Use `inref<'T>` if you only need to read the pointer.</span></span>
- <span data-ttu-id="6904c-171">`outref<'T>`Yalnızca işaretçiye yazmanız gerekiyorsa kullanın.</span><span class="sxs-lookup"><span data-stu-id="6904c-171">Use `outref<'T>` if you only need to write to the pointer.</span></span>
- <span data-ttu-id="6904c-172">`byref<'T>`Hem okuma hem de işaretçiye yazma gerekiyorsa kullanın.</span><span class="sxs-lookup"><span data-stu-id="6904c-172">Use `byref<'T>` if you need to both read from and write to the pointer.</span></span>

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

<span data-ttu-id="6904c-173">Parametresi bir işaretçi olduğundan ve değer değişebilir olduğundan, değer üzerinde yapılan tüm değişiklikler işlevin yürütülmesinden sonra tutulur.</span><span class="sxs-lookup"><span data-stu-id="6904c-173">Because the parameter is a pointer and the value is mutable, any changes to the value are retained after the execution of the function.</span></span>

<span data-ttu-id="6904c-174">.NET kitaplığı yöntemlerinde herhangi bir parametreyi depolamak için bir kayıt düzeni değerini dönüş değeri olarak kullanabilirsiniz `out` .</span><span class="sxs-lookup"><span data-stu-id="6904c-174">You can use a tuple as a return value to store any `out` parameters in .NET library methods.</span></span> <span data-ttu-id="6904c-175">Alternatif olarak, `out` parametresini bir parametre olarak kabul edebilirsiniz `byref` .</span><span class="sxs-lookup"><span data-stu-id="6904c-175">Alternatively, you can treat the `out` parameter as a `byref` parameter.</span></span> <span data-ttu-id="6904c-176">Aşağıdaki kod örneğinde her iki yol da gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="6904c-176">The following code example illustrates both ways.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/parameters-and-arguments-1/snippet3810.fs)]

## <a name="parameter-arrays"></a><span data-ttu-id="6904c-177">Parametre Dizileri</span><span class="sxs-lookup"><span data-stu-id="6904c-177">Parameter Arrays</span></span>

<span data-ttu-id="6904c-178">Bazen heterojen türden rastgele sayıda parametre alan bir işlev tanımlanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="6904c-178">Occasionally it is necessary to define a function that takes an arbitrary number of parameters of heterogeneous type.</span></span> <span data-ttu-id="6904c-179">Tüm olası aşırı yüklenmiş yöntemlerin, kullanılabilecek tüm türlere yönelik olarak oluşturulması pratik değildir.</span><span class="sxs-lookup"><span data-stu-id="6904c-179">It would not be practical to create all the possible overloaded methods to account for all the types that could be used.</span></span> <span data-ttu-id="6904c-180">.NET uygulamaları, parametre dizisi özelliği aracılığıyla bu tür yöntemler için destek sağlar.</span><span class="sxs-lookup"><span data-stu-id="6904c-180">The .NET implementations provide support for such methods through the parameter array feature.</span></span> <span data-ttu-id="6904c-181">İmzasında parametre dizisi alan bir yöntem, rastgele sayıda parametre ile birlikte etkinleştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="6904c-181">A method that takes a parameter array in its signature can be provided with an arbitrary number of parameters.</span></span> <span data-ttu-id="6904c-182">Parametreler bir diziye konur.</span><span class="sxs-lookup"><span data-stu-id="6904c-182">The parameters are put into an array.</span></span> <span data-ttu-id="6904c-183">Dizi öğelerinin türü, işleve geçirilebilecek parametre türlerini belirler.</span><span class="sxs-lookup"><span data-stu-id="6904c-183">The type of the array elements determines the parameter types that can be passed to the function.</span></span> <span data-ttu-id="6904c-184">Parametre dizisini `System.Object` öğesi türü olarak tanımlarsanız, istemci kodu herhangi bir türdeki değerleri geçirebilir.</span><span class="sxs-lookup"><span data-stu-id="6904c-184">If you define the parameter array with `System.Object` as the element type, then client code can pass values of any type.</span></span>

<span data-ttu-id="6904c-185">F # içinde parametre dizileri yalnızca yöntemlerde tanımlanabilir.</span><span class="sxs-lookup"><span data-stu-id="6904c-185">In F#, parameter arrays can only be defined in methods.</span></span> <span data-ttu-id="6904c-186">Bunlar tek başına işlevlerde veya modüllerde tanımlanmış işlevlerde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="6904c-186">They cannot be used in standalone functions or functions that are defined in modules.</span></span>

<span data-ttu-id="6904c-187">Özniteliğini kullanarak bir parametre dizisi tanımlarsınız `ParamArray` .</span><span class="sxs-lookup"><span data-stu-id="6904c-187">You define a parameter array by using the `ParamArray` attribute.</span></span> <span data-ttu-id="6904c-188">`ParamArray`Özniteliği yalnızca son parametreye uygulanabilir.</span><span class="sxs-lookup"><span data-stu-id="6904c-188">The `ParamArray` attribute can only be applied to the last parameter.</span></span>

<span data-ttu-id="6904c-189">Aşağıdaki kod, bir parametre dizisi alan bir .NET yöntemi ve bir parametre dizisi alan bir yöntemi olan F # içindeki bir tür tanımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="6904c-189">The following code illustrates both calling a .NET method that takes a parameter array and the definition of a type in F# that has a method that takes a parameter array.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/parameters-and-arguments-2/snippet3811.fs)]

<span data-ttu-id="6904c-190">Bir projede çalıştırıldığında, önceki kodun çıktısı aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="6904c-190">When run in a project, the output of the previous code is as follows:</span></span>

```console
a 1 10 Hello world 1 True
"a"
1
10.0
"Hello world"
1u
true
```

## <a name="see-also"></a><span data-ttu-id="6904c-191">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6904c-191">See also</span></span>

- [<span data-ttu-id="6904c-192">Üyeler</span><span class="sxs-lookup"><span data-stu-id="6904c-192">Members</span></span>](./members/index.md)
