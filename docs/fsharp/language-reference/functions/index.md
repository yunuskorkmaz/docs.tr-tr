---
title: İşlevler (F#)
description: 'F # ve nasıl F # ortak işlevsel programlama yapılarını destekler işlevleri hakkında bilgi edinin.'
ms.date: 05/16/2016
ms.openlocfilehash: c96dddb07ca671a9e823fb25f6f6c3788fe32fd2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33566411"
---
# <a name="functions"></a><span data-ttu-id="a3c54-103">İşlevler</span><span class="sxs-lookup"><span data-stu-id="a3c54-103">Functions</span></span>

<span data-ttu-id="a3c54-104">Temel birim herhangi bir programlama dili program yürütme işlevlerdir.</span><span class="sxs-lookup"><span data-stu-id="a3c54-104">Functions are the fundamental unit of program execution in any programming language.</span></span> <span data-ttu-id="a3c54-105">Diğer diller olduğu gibi bir F # işlevi bir ada sahip, parametreler ve bağımsız değişkenler Al olabilir ve gövde sahiptir.</span><span class="sxs-lookup"><span data-stu-id="a3c54-105">As in other languages, an F# function has a name, can have parameters and take arguments, and has a body.</span></span> <span data-ttu-id="a3c54-106">F # ayrıca değerleri olarak işlevler değerlendirmesini gibi işlevsel programlama yapıları adlandırılmamış işlevler ifadelerde, yeni işlevler, curried işlevleri ve kısmi yapmamanız işlevlerin örtük tanımı oluşturmak için işlevlerin oluşturulması kullanılmasını destekler işlev bağımsız değişkenleri uygulama.</span><span class="sxs-lookup"><span data-stu-id="a3c54-106">F# also supports functional programming constructs such as treating functions as values, using unnamed functions in expressions, composition of functions to form new functions, curried functions, and the implicit definition of functions by way of the partial application of function arguments.</span></span>

<span data-ttu-id="a3c54-107">İşlevleri kullanarak tanımladığınız `let` anahtar sözcüğü veya işlev özyinelemeli ise `let rec` anahtar sözcüğü birleşimi.</span><span class="sxs-lookup"><span data-stu-id="a3c54-107">You define functions by using the `let` keyword, or, if the function is recursive, the `let rec` keyword combination.</span></span>


## <a name="syntax"></a><span data-ttu-id="a3c54-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a3c54-108">Syntax</span></span>

```fsharp
// Non-recursive function definition.
let [inline] function-name parameter-list [ : return-type ] = function-body
// Recursive function definition.
let rec function-name parameter-list = recursive-function-body
```

## <a name="remarks"></a><span data-ttu-id="a3c54-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a3c54-109">Remarks</span></span>
<span data-ttu-id="a3c54-110">*İşlev adı* işlevi temsil eden bir tanımlayıcıdır.</span><span class="sxs-lookup"><span data-stu-id="a3c54-110">The *function-name* is an identifier that represents the function.</span></span> <span data-ttu-id="a3c54-111">*Parametre listesi* boşluklarla ayırarak art arda parametreleri oluşur.</span><span class="sxs-lookup"><span data-stu-id="a3c54-111">The *parameter-list* consists of successive parameters that are separated by spaces.</span></span> <span data-ttu-id="a3c54-112">Parametreler bölümünde açıklandığı gibi her parametre için bir açık tür belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a3c54-112">You can specify an explicit type for each parameter, as described in the Parameters section.</span></span> <span data-ttu-id="a3c54-113">Belirli bir bağımsız değişken türü belirtmezseniz, derleyici işlev gövdesi türünden Infer dener.</span><span class="sxs-lookup"><span data-stu-id="a3c54-113">If you do not specify a specific argument type, the compiler attempts to infer the type from the function body.</span></span> <span data-ttu-id="a3c54-114">*İşlev gövdesi* bir ifadenin oluşur.</span><span class="sxs-lookup"><span data-stu-id="a3c54-114">The *function-body* consists of an expression.</span></span> <span data-ttu-id="a3c54-115">İşlev gövdesi yapan genellikle dönen değer son bir ifadede culminate ifadeleri sayısı oluşan bileşik bir ifade ifadesidir.</span><span class="sxs-lookup"><span data-stu-id="a3c54-115">The expression that makes up the function body is typically a compound expression consisting of a number of expressions that culminate in a final expression that is the return value.</span></span> <span data-ttu-id="a3c54-116">*Dönüş türü* türüne göre üste ve isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="a3c54-116">The *return-type* is a colon followed by a type and is optional.</span></span> <span data-ttu-id="a3c54-117">Dönüş değeri türünü açıkça belirtmezseniz derleyici son deyim dönüş türü belirler.</span><span class="sxs-lookup"><span data-stu-id="a3c54-117">If you do not specify the type of the return value explicitly, the compiler determines the return type from the final expression.</span></span>

<span data-ttu-id="a3c54-118">Basit işlev tanımı aşağıdakine benzer:</span><span class="sxs-lookup"><span data-stu-id="a3c54-118">A simple function definition resembles the following:</span></span>

```fsharp
let f x = x + 1
```

<span data-ttu-id="a3c54-119">Önceki örnekte işlevi adıdır `f`, bağımsız değişken `x`, türüne sahip `int`, işlev gövdesi `x + 1`, ve dönüş değeri türü `int`.</span><span class="sxs-lookup"><span data-stu-id="a3c54-119">In the previous example, the function name is `f`, the argument is `x`, which has type `int`, the function body is `x + 1`, and the return value is of type `int`.</span></span>

<span data-ttu-id="a3c54-120">İşlevler işaretlenir `inline`.</span><span class="sxs-lookup"><span data-stu-id="a3c54-120">Functions can be marked `inline`.</span></span> <span data-ttu-id="a3c54-121">Hakkında bilgi için `inline`, bkz: [satır içi işlevler](../functions/inline-functions.md).</span><span class="sxs-lookup"><span data-stu-id="a3c54-121">For information about `inline`, see [Inline Functions](../functions/inline-functions.md).</span></span>


## <a name="scope"></a><span data-ttu-id="a3c54-122">Kapsam</span><span class="sxs-lookup"><span data-stu-id="a3c54-122">Scope</span></span>
<span data-ttu-id="a3c54-123">Tüm modül kapsamı dışında kapsam düzeyinde, bir değer veya işlev adı yeniden kullanmak için bir hata değildir.</span><span class="sxs-lookup"><span data-stu-id="a3c54-123">At any level of scope other than module scope, it is not an error to reuse a value or function name.</span></span> <span data-ttu-id="a3c54-124">Bir ad yeniden kullanırsanız, daha sonra bildirilen ad daha önce bildirilen ad shadows.</span><span class="sxs-lookup"><span data-stu-id="a3c54-124">If you reuse a name, the name declared later shadows the name declared earlier.</span></span> <span data-ttu-id="a3c54-125">Ancak, bir modüldeki en üst düzey kapsamında adlarının benzersiz olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="a3c54-125">However, at the top level scope in a module, names must be unique.</span></span> <span data-ttu-id="a3c54-126">Örneğin, aşağıdaki kod modülü kapsamda göründüğünde, ancak bir işlev içinde görüntülendiğinde değil, bir hata üretir:</span><span class="sxs-lookup"><span data-stu-id="a3c54-126">For example, the following code produces an error when it appears at module scope, but not when it appears inside a function:</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet101.fs)]

<span data-ttu-id="a3c54-127">Ancak herhangi bir kapsam düzeyinde aşağıdaki kodu kabul edilebilir:</span><span class="sxs-lookup"><span data-stu-id="a3c54-127">But the following code is acceptable at any level of scope:</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet102.fs)]
    
#### <a name="parameters"></a><span data-ttu-id="a3c54-128">Parametreler</span><span class="sxs-lookup"><span data-stu-id="a3c54-128">Parameters</span></span>
<span data-ttu-id="a3c54-129">Parametre adları sonra işlevi adı listelenir.</span><span class="sxs-lookup"><span data-stu-id="a3c54-129">Names of parameters are listed after the function name.</span></span> <span data-ttu-id="a3c54-130">Aşağıdaki örnekte gösterildiği gibi bir parametrenin türünü belirtebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="a3c54-130">You can specify a type for a parameter, as shown in the following example:</span></span>

```fsharp
let f (x : int) = x + 1
```

<span data-ttu-id="a3c54-131">Bir tür belirtirseniz, parametrenin adı izler ve adından virgülle ayrılmış.</span><span class="sxs-lookup"><span data-stu-id="a3c54-131">If you specify a type, it follows the name of the parameter and is separated from the name by a colon.</span></span> <span data-ttu-id="a3c54-132">Parametresinin türü atlarsanız, parametre türü derleyici tarafından algılanır.</span><span class="sxs-lookup"><span data-stu-id="a3c54-132">If you omit the type for the parameter, the parameter type is inferred by the compiler.</span></span> <span data-ttu-id="a3c54-133">Örneğin, aşağıdaki işlev tanımında, bağımsız değişkeni `x` türünde olması olayla `int` 1 türünde olduğundan `int`.</span><span class="sxs-lookup"><span data-stu-id="a3c54-133">For example, in the following function definition, the argument `x` is inferred to be of type `int` because 1 is of type `int`.</span></span>

```fsharp
let f x = x + 1
```

<span data-ttu-id="a3c54-134">Ancak, derleyici işlevi olabildiğince genel kurmayı dener.</span><span class="sxs-lookup"><span data-stu-id="a3c54-134">However, the compiler will attempt to make the function as generic as possible.</span></span> <span data-ttu-id="a3c54-135">Örneğin, aşağıdaki kodu not edin:</span><span class="sxs-lookup"><span data-stu-id="a3c54-135">For example, note the following code:</span></span>

```fsharp
let f x = (x, x)
```

<span data-ttu-id="a3c54-136">İşlev herhangi bir türde bir bağımsız değişkende bir tanımlama grubu oluşturur.</span><span class="sxs-lookup"><span data-stu-id="a3c54-136">The function creates a tuple from one argument of any type.</span></span> <span data-ttu-id="a3c54-137">Türü belirtilmediğinden, bu işlev ile herhangi bir bağımsız değişken türü kullanılır.</span><span class="sxs-lookup"><span data-stu-id="a3c54-137">Because the type is not specified, the function can be used with any argument type.</span></span> <span data-ttu-id="a3c54-138">Daha fazla bilgi için bkz: [otomatik Genelleştirme](../generics/automatic-generalization.md).</span><span class="sxs-lookup"><span data-stu-id="a3c54-138">For more information, see [Automatic Generalization](../generics/automatic-generalization.md).</span></span>


## <a name="function-bodies"></a><span data-ttu-id="a3c54-139">İşlev Gövdeleri</span><span class="sxs-lookup"><span data-stu-id="a3c54-139">Function Bodies</span></span>
<span data-ttu-id="a3c54-140">İşlev gövdesi, yerel değişkenleri ve işlevleri tanımları içerebilir.</span><span class="sxs-lookup"><span data-stu-id="a3c54-140">A function body can contain definitions of local variables and functions.</span></span> <span data-ttu-id="a3c54-141">Bu tür değişkenleri ve işlevleri gövdesi geçerli işlevi dışında bu kapsamda ' dir.</span><span class="sxs-lookup"><span data-stu-id="a3c54-141">Such variables and functions are in scope in the body of the current function but not outside it.</span></span> <span data-ttu-id="a3c54-142">Basit sözdizimi seçeneği etkin olduğunda, aşağıdaki örnekte gösterildiği gibi bir tanımı bir işlev gövdesine olduğunu belirtmek için girinti kullanmanız gerekir:</span><span class="sxs-lookup"><span data-stu-id="a3c54-142">When you have the lightweight syntax option enabled, you must use indentation to indicate that a definition is in a function body, as shown in the following example:</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet103.fs)]

<span data-ttu-id="a3c54-143">Daha fazla bilgi için bkz: [kod biçimlendirme yönergeleri](../code-formatting-guidelines.md) ve [ayrıntılı sözdizimi](../verbose-syntax.md).</span><span class="sxs-lookup"><span data-stu-id="a3c54-143">For more information, see [Code Formatting Guidelines](../code-formatting-guidelines.md) and [Verbose Syntax](../verbose-syntax.md).</span></span>


## <a name="return-values"></a><span data-ttu-id="a3c54-144">Dönüş Değerleri</span><span class="sxs-lookup"><span data-stu-id="a3c54-144">Return Values</span></span>
<span data-ttu-id="a3c54-145">Derleyici son deyim dönüş değeri ve türü belirlemek için bir işlev gövdesine kullanır.</span><span class="sxs-lookup"><span data-stu-id="a3c54-145">The compiler uses the final expression in a function body to determine the return value and type.</span></span> <span data-ttu-id="a3c54-146">Derleyici önceki ifadeleri son ifadesinden türünü Infer.</span><span class="sxs-lookup"><span data-stu-id="a3c54-146">The compiler might infer the type of the final expression from previous expressions.</span></span> <span data-ttu-id="a3c54-147">İşlevinde `cylinderVolume`türünü önceki bölümde gösterilen `pi` sabit türünden belirlenir `3.14159` olmasını `float`.</span><span class="sxs-lookup"><span data-stu-id="a3c54-147">In the function `cylinderVolume`, shown in the previous section, the type of `pi` is determined from the type of the literal `3.14159` to be `float`.</span></span> <span data-ttu-id="a3c54-148">Derleyici türünü kullanan `pi` ifade türünü belirlemek için `h * pi * r * r` olmasını `float`.</span><span class="sxs-lookup"><span data-stu-id="a3c54-148">The compiler uses the type of `pi` to determine the type of the expression `h * pi * r * r` to be `float`.</span></span> <span data-ttu-id="a3c54-149">Bu nedenle, işlevinin genel dönüş türü olan `float`.</span><span class="sxs-lookup"><span data-stu-id="a3c54-149">Therefore, the overall return type of the function is `float`.</span></span>

<span data-ttu-id="a3c54-150">Dönüş değeri açıkça belirtmek için bir kod aşağıdaki gibi yazın:</span><span class="sxs-lookup"><span data-stu-id="a3c54-150">To specify the return value explicitly, write the code as follows:</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet105.fs)]

<span data-ttu-id="a3c54-151">Kod yukarıda yazıldığı şekilde derleyici geçerlidir **float** de parametre türleri uygulamak ortalama, tüm işleve; aşağıdaki kodu kullanın:</span><span class="sxs-lookup"><span data-stu-id="a3c54-151">As the code is written above, the compiler applies **float** to the entire function; if you mean to apply it to the parameter types as well, use the following code:</span></span>

```fsharp
let cylinderVolume (radius : float) (length : float) : float
```

## <a name="calling-a-function"></a><span data-ttu-id="a3c54-152">İşlev Çağırma</span><span class="sxs-lookup"><span data-stu-id="a3c54-152">Calling a Function</span></span>
<span data-ttu-id="a3c54-153">İşlev adı bir boşluk bırakarak ve boşluklarla ayırarak sonra herhangi bir bağımsız değişken belirterek işlevlerini çağırın.</span><span class="sxs-lookup"><span data-stu-id="a3c54-153">You call functions by specifying the function name followed by a space and then any arguments separated by spaces.</span></span> <span data-ttu-id="a3c54-154">Örneğin, bir işlevi çağırmak için **cylinderVolume** ve sonuç değeri atayın **sesi**, aşağıdaki kodu yazın:</span><span class="sxs-lookup"><span data-stu-id="a3c54-154">For example, to call the function **cylinderVolume** and assign the result to the value **vol**, you write the following code:</span></span>

```fsharp
let vol = cylinderVolume 2.0 3.0
```

## <a name="partial-application-of-arguments"></a><span data-ttu-id="a3c54-155">Bağımsız Değişkenlerin Kısmi Uygulanması</span><span class="sxs-lookup"><span data-stu-id="a3c54-155">Partial Application of Arguments</span></span>
<span data-ttu-id="a3c54-156">Belirtilen bağımsız değişkenler sayısından az sağlarsanız, kalan bağımsız değişkenleri bekler yeni bir işlev oluşturun.</span><span class="sxs-lookup"><span data-stu-id="a3c54-156">If you supply fewer than the specified number of arguments, you create a new function that expects the remaining arguments.</span></span> <span data-ttu-id="a3c54-157">Bu yöntem bağımsız değişkenleri işleme olarak adlandırılır *currying* ve F # işlevsel programlama dilleri özelliğidir.</span><span class="sxs-lookup"><span data-stu-id="a3c54-157">This method of handling arguments is referred to as *currying* and is a characteristic of functional programming languages like F#.</span></span> <span data-ttu-id="a3c54-158">Örneğin, iki kanal boyutlarıyla çalıştığınız varsayalım: bir yarıçapı varsa **2.0** ve diğer bir yarıçapı sahip **3.0**.</span><span class="sxs-lookup"><span data-stu-id="a3c54-158">For example, suppose you are working with two sizes of pipe: one has a radius of **2.0** and the other has a radius of **3.0**.</span></span> <span data-ttu-id="a3c54-159">Kanal hacmi gibi belirlemek işlevleri oluşturabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="a3c54-159">You could create functions that determine the volume of pipe as follows:</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet106.fs)]

<span data-ttu-id="a3c54-160">Ardından, çeşitli iki farklı boyutlarda kanal uzunluk için gerektiğinde ek bağımsız değişken sağlayın:</span><span class="sxs-lookup"><span data-stu-id="a3c54-160">You would then supply the additional argument as needed for various lengths of pipe of the two different sizes:</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet107.fs)]
    
## <a name="recursive-functions"></a><span data-ttu-id="a3c54-161">Özyinelemeli İşlevler</span><span class="sxs-lookup"><span data-stu-id="a3c54-161">Recursive Functions</span></span>
<span data-ttu-id="a3c54-162">*Özyinelemeli işlevler* kendisini çağıran işlev.</span><span class="sxs-lookup"><span data-stu-id="a3c54-162">*Recursive functions* are functions that call themselves.</span></span> <span data-ttu-id="a3c54-163">Bunlar, belirttiğiniz gerektirir **rec** anahtar sözcüğünü aşağıdaki **izin** anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="a3c54-163">They require that you specify the **rec** keyword following the **let** keyword.</span></span> <span data-ttu-id="a3c54-164">Hiçbir işlev çağrısı çağırma işlevinin gövdesi içinde özyinelemeli işlevinden çağırır.</span><span class="sxs-lookup"><span data-stu-id="a3c54-164">Invoke the recursive function from within the body of the function just as you would invoke any function call.</span></span> <span data-ttu-id="a3c54-165">Aşağıdaki özyinelemeli işlev hesaplar *n*th Fibonacci numarası.</span><span class="sxs-lookup"><span data-stu-id="a3c54-165">The following recursive function computes the *n*th Fibonacci number.</span></span> <span data-ttu-id="a3c54-166">Fibonacci numarası dizisi antiquity bu yana bilinen ve her ardışık sayı dizisinin önceki iki sayı toplamı olacak bir dizidir.</span><span class="sxs-lookup"><span data-stu-id="a3c54-166">The Fibonacci number sequence has been known since antiquity and is a sequence in which each successive number is the sum of the previous two numbers in the sequence.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet108.fs)]

<span data-ttu-id="a3c54-167">Bazı özyinelemeli işlevler program yığın taşması olabilir ya da bunları Bakım ve accumulators ve devamlılıklar kullanımı gibi özel teknikleri hakkında farkındalık ile yazdığınız değil inefficiently gerçekleştirin.</span><span class="sxs-lookup"><span data-stu-id="a3c54-167">Some recursive functions might overflow the program stack or perform inefficiently if you do not write them with care and with awareness of special techniques, such as the use of accumulators and continuations.</span></span>


## <a name="function-values"></a><span data-ttu-id="a3c54-168">İşlev Değerleri</span><span class="sxs-lookup"><span data-stu-id="a3c54-168">Function Values</span></span>
<span data-ttu-id="a3c54-169">F #'ta tüm işlevleri değerleri olarak kabul edilir; olarak aslında, bilinen *işlev değerleri*.</span><span class="sxs-lookup"><span data-stu-id="a3c54-169">In F#, all functions are considered values; in fact, they are known as *function values*.</span></span> <span data-ttu-id="a3c54-170">İşlevleri değerleri olduğundan, bunlar diğer işlevleri veya diğer bağlamlarda bağımsız değişken değerleri kullanıldığı kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="a3c54-170">Because functions are values, they can be used as arguments to other functions or in other contexts where values are used.</span></span> <span data-ttu-id="a3c54-171">Bağımsız değişken olarak bir işlev değer isteyen bir işlevi örneği aşağıdadır:</span><span class="sxs-lookup"><span data-stu-id="a3c54-171">Following is an example of a function that takes a function value as an argument:</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet109.fs)]

<span data-ttu-id="a3c54-172">Kullanarak bir işlev değer türü belirtmek `->` belirteci.</span><span class="sxs-lookup"><span data-stu-id="a3c54-172">You specify the type of a function value by using the `->` token.</span></span> <span data-ttu-id="a3c54-173">Bu belirteç sol tarafındaki bağımsız değişken türü, ve sağ tarafta dönüş değeri.</span><span class="sxs-lookup"><span data-stu-id="a3c54-173">On the left side of this token is the type of the argument, and on the right side is the return value.</span></span> <span data-ttu-id="a3c54-174">Önceki örnekte, `apply1` bir işlev alır bir işlevi olduğunu `transform` bir bağımsız değişken olarak burada `transform` tamsayı alan ve başka bir tamsayı döndüren bir işlev değil.</span><span class="sxs-lookup"><span data-stu-id="a3c54-174">In the previous example, `apply1` is a function that takes a function `transform` as an argument, where `transform` is a function that takes an integer and returns another integer.</span></span> <span data-ttu-id="a3c54-175">Aşağıdaki kodu nasıl kullanılacağını gösterir `apply1`:</span><span class="sxs-lookup"><span data-stu-id="a3c54-175">The following code shows how to use `apply1`:</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet110.fs)]

<span data-ttu-id="a3c54-176">Değeri `result` önceki kod çalıştıktan sonra 101 olacaktır.</span><span class="sxs-lookup"><span data-stu-id="a3c54-176">The value of `result` will be 101 after the previous code runs.</span></span>

<span data-ttu-id="a3c54-177">Birden çok bağımsız değişkenleri art arda tarafından ayrılmış olan `->` belirteçler, aşağıdaki örnekte gösterildiği gibi:</span><span class="sxs-lookup"><span data-stu-id="a3c54-177">Multiple arguments are separated by successive `->` tokens, as shown in the following example:</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet111.fs)]

<span data-ttu-id="a3c54-178">200 sonucudur.</span><span class="sxs-lookup"><span data-stu-id="a3c54-178">The result is 200.</span></span>


## <a name="lambda-expressions"></a><span data-ttu-id="a3c54-179">Lambda İfadeleri</span><span class="sxs-lookup"><span data-stu-id="a3c54-179">Lambda Expressions</span></span>
<span data-ttu-id="a3c54-180">A *lambda ifadesi* adlandırılmamış bir işlevdir.</span><span class="sxs-lookup"><span data-stu-id="a3c54-180">A *lambda expression* is an unnamed function.</span></span> <span data-ttu-id="a3c54-181">Önceki örneklerde işlevleri adlı tanımlama yerine **artırma** ve **mul**, lambda ifadeleri şu şekilde kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="a3c54-181">In the previous examples, instead of defining named functions **increment** and **mul**, you could use lambda expressions as follows:</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet112.fs)]

<span data-ttu-id="a3c54-182">Lambda ifadeleri kullanarak tanımladığınız `fun` anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="a3c54-182">You define lambda expressions by using the `fun` keyword.</span></span> <span data-ttu-id="a3c54-183">Lambda ifadesi, yerine dışında bir işlev tanımı benzer `=` belirteç, `->` belirteci bağımsız değişken listesi işlevi gövdesinden ayırmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="a3c54-183">A lambda expression resembles a function definition, except that instead of the `=` token, the `->` token is used to separate the argument list from the function body.</span></span> <span data-ttu-id="a3c54-184">Normal işlev tanımı olduğu gibi bağımsız değişken türleri yapılandırılacağını veya açıkça belirtilen ve lambda ifadesi dönüş türü gövdesi son ifadesinde tür çıkarımı yapılan.</span><span class="sxs-lookup"><span data-stu-id="a3c54-184">As in a regular function definition, the argument types can be inferred or specified explicitly, and the return type of the lambda expression is inferred from the type of the last expression in the body.</span></span> <span data-ttu-id="a3c54-185">Daha fazla bilgi için bkz: [Lambda ifadeleri: `fun` anahtar sözcüğü](../functions/lambda-expressions-the-fun-keyword.md).</span><span class="sxs-lookup"><span data-stu-id="a3c54-185">For more information, see [Lambda Expressions: The `fun` Keyword](../functions/lambda-expressions-the-fun-keyword.md).</span></span>


## <a name="function-composition-and-pipelining"></a><span data-ttu-id="a3c54-186">İşlev Bileşimi ve Ardışık Düzen Oluşturma</span><span class="sxs-lookup"><span data-stu-id="a3c54-186">Function Composition and Pipelining</span></span>
<span data-ttu-id="a3c54-187">F # işlevleri diğer işlevleri birleştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="a3c54-187">Functions in F# can be composed from other functions.</span></span> <span data-ttu-id="a3c54-188">İki işlevlerin oluşturulması **function1** ve **function2** , uygulamanın gösteren başka bir işlevi olan **function1** Uygulamaveardından**function2**:</span><span class="sxs-lookup"><span data-stu-id="a3c54-188">The composition of two functions **function1** and **function2** is another function that represents the application of **function1** followed the application of **function2**:</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet113.fs)]

<span data-ttu-id="a3c54-189">202 sonucudur.</span><span class="sxs-lookup"><span data-stu-id="a3c54-189">The result is 202.</span></span>

<span data-ttu-id="a3c54-190">Art arda işlemleri olarak birbirine zincirlenmesi için ardışık düzen etkinleştirir işlevi çağırır.</span><span class="sxs-lookup"><span data-stu-id="a3c54-190">Pipelining enables function calls to be chained together as successive operations.</span></span> <span data-ttu-id="a3c54-191">Works gibi ardışık düzen oluşturma:</span><span class="sxs-lookup"><span data-stu-id="a3c54-191">Pipelining works as follows:</span></span>

```fsharp
let result = 100 |> function1 |> function2
```

<span data-ttu-id="a3c54-192">Yeniden 202 sonucudur.</span><span class="sxs-lookup"><span data-stu-id="a3c54-192">The result is again 202.</span></span>

<span data-ttu-id="a3c54-193">Birleşim operatörleri iki işlevleri alır ve bir işlev döndürür; Bunun aksine, ardışık düzen operatörleri bir işlev ve bağımsız değişken alır ve bir değer döndürür.</span><span class="sxs-lookup"><span data-stu-id="a3c54-193">The composition operators take two functions and return a function; by contrast, the pipeline operators take a function and an argument and return a value.</span></span> <span data-ttu-id="a3c54-194">Aşağıdaki kod örneğinde işlevi imzalar ve kullanım farklılıkları göstererek ardışık düzen ve birleşim işleçleri arasındaki farkı gösterir.</span><span class="sxs-lookup"><span data-stu-id="a3c54-194">The following code example shows the difference between the pipeline and composition operators by showing the differences in the function signatures and usage.</span></span>

```fsharp
// Function composition and pipeline operators compared.

let addOne x = x + 1
let timesTwo x = 2 * x

// Composition operator
// ( >> ) : ('T1 -> 'T2) -> ('T2 -> 'T3) -> 'T1 -> 'T3
let Compose2 = addOne >> timesTwo

// Backward composition operator
// ( << ) : ('T2 -> 'T3) -> ('T1 -> 'T2) -> 'T1 -> 'T3
let Compose1 = addOne << timesTwo

// Result is 5
let result1 = Compose1 2

// Result is 6
let result2 = Compose2 2

// Pipelining
// Pipeline operator
// ( |> ) : 'T1 -> ('T1 -> 'U) -> 'U
let Pipeline2 x = addOne x |> timesTwo

// Backward pipeline operator
// ( <| ) : ('T -> 'U) -> 'T -> 'U
let Pipeline1 x = addOne <| timesTwo x

// Result is 5
let result3 = Pipeline1 2

// Result is 6
let result4 = Pipeline2 2
```

## <a name="overloading-functions"></a><span data-ttu-id="a3c54-195">Aşırı Yükleme İşlevleri</span><span class="sxs-lookup"><span data-stu-id="a3c54-195">Overloading Functions</span></span>
<span data-ttu-id="a3c54-196">Bir tür ancak değil işlevleri yöntemlerini aşırı yüklenebilir.</span><span class="sxs-lookup"><span data-stu-id="a3c54-196">You can overload methods of a type but not functions.</span></span> <span data-ttu-id="a3c54-197">Daha fazla bilgi için bkz: [yöntemleri](../members/methods.md).</span><span class="sxs-lookup"><span data-stu-id="a3c54-197">For more information, see [Methods](../members/methods.md).</span></span>


## <a name="see-also"></a><span data-ttu-id="a3c54-198">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="a3c54-198">See Also</span></span>
[<span data-ttu-id="a3c54-199">Değerler</span><span class="sxs-lookup"><span data-stu-id="a3c54-199">Values</span></span>](../values/index.md)

[<span data-ttu-id="a3c54-200">F# Dili Başvurusu</span><span class="sxs-lookup"><span data-stu-id="a3c54-200">F# Language Reference</span></span>](../index.md)
