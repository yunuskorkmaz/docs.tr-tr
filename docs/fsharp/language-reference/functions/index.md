---
title: İşlevler
description: İçindeki F# işlevleri hakkında bilgi edinin ve F# ortak fonksiyonel programlama yapılarını nasıl destekler.
ms.date: 05/16/2016
ms.openlocfilehash: c6b8307f51ffcdc77fe4352b2305fca1f247ccbb
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73423948"
---
# <a name="functions"></a><span data-ttu-id="1db00-103">İşlevler</span><span class="sxs-lookup"><span data-stu-id="1db00-103">Functions</span></span>

<span data-ttu-id="1db00-104">İşlevler, herhangi bir programlama dilinde program yürütmenin temel birimidir.</span><span class="sxs-lookup"><span data-stu-id="1db00-104">Functions are the fundamental unit of program execution in any programming language.</span></span> <span data-ttu-id="1db00-105">Diğer dillerde olduğu gibi, bir F# işlevin adı vardır, parametreleri olabilir ve bağımsız değişkenler alabilir ve bir gövdeye sahip olabilir.</span><span class="sxs-lookup"><span data-stu-id="1db00-105">As in other languages, an F# function has a name, can have parameters and take arguments, and has a body.</span></span> <span data-ttu-id="1db00-106">F#Ayrıca, işlevleri değer olarak davranma, ifadelerde adlandırılmamış işlevleri kullanma, yeni işlevler, curried işlevleri ve kısmi olarak işlevlerin örtük tanımına göre işlev oluşturma gibi işlev programlama yapılarını destekler. işlev bağımsız değişkenlerinin uygulaması.</span><span class="sxs-lookup"><span data-stu-id="1db00-106">F# also supports functional programming constructs such as treating functions as values, using unnamed functions in expressions, composition of functions to form new functions, curried functions, and the implicit definition of functions by way of the partial application of function arguments.</span></span>

<span data-ttu-id="1db00-107">`let` anahtar sözcüğünü kullanarak işlevler tanımlarsınız veya işlev özyinelemeli ise `let rec` anahtar sözcük birleşimi.</span><span class="sxs-lookup"><span data-stu-id="1db00-107">You define functions by using the `let` keyword, or, if the function is recursive, the `let rec` keyword combination.</span></span>

## <a name="syntax"></a><span data-ttu-id="1db00-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="1db00-108">Syntax</span></span>

```fsharp
// Non-recursive function definition.
let [inline] function-name parameter-list [ : return-type ] = function-body
// Recursive function definition.
let rec function-name parameter-list = recursive-function-body
```

## <a name="remarks"></a><span data-ttu-id="1db00-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="1db00-109">Remarks</span></span>

<span data-ttu-id="1db00-110">*İşlev adı* , işlevini temsil eden bir tanıtıcıdır.</span><span class="sxs-lookup"><span data-stu-id="1db00-110">The *function-name* is an identifier that represents the function.</span></span> <span data-ttu-id="1db00-111">*Parametre-listesi* , boşluklarla ayrılmış ardışık parametrelerden oluşur.</span><span class="sxs-lookup"><span data-stu-id="1db00-111">The *parameter-list* consists of successive parameters that are separated by spaces.</span></span> <span data-ttu-id="1db00-112">Parametreler bölümünde açıklandığı gibi her bir parametre için açık bir tür belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1db00-112">You can specify an explicit type for each parameter, as described in the Parameters section.</span></span> <span data-ttu-id="1db00-113">Belirli bir bağımsız değişken türü belirtmezseniz, derleyici türü işlev gövdesinden çıkarması için çalışır.</span><span class="sxs-lookup"><span data-stu-id="1db00-113">If you do not specify a specific argument type, the compiler attempts to infer the type from the function body.</span></span> <span data-ttu-id="1db00-114">*İşlev gövdesi* bir ifadeden oluşur.</span><span class="sxs-lookup"><span data-stu-id="1db00-114">The *function-body* consists of an expression.</span></span> <span data-ttu-id="1db00-115">İşlev gövdesini oluşturan ifade, genellikle dönüş değeri olan bir son ifadede yer alan bir dizi ifadeden oluşan bir bileşik ifadedir.</span><span class="sxs-lookup"><span data-stu-id="1db00-115">The expression that makes up the function body is typically a compound expression consisting of a number of expressions that culminate in a final expression that is the return value.</span></span> <span data-ttu-id="1db00-116">*Dönüş türü* , ardından bir tür ve isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="1db00-116">The *return-type* is a colon followed by a type and is optional.</span></span> <span data-ttu-id="1db00-117">Dönüş değerinin türünü açıkça belirtmezseniz, derleyici son ifadeden dönüş türünü belirler.</span><span class="sxs-lookup"><span data-stu-id="1db00-117">If you do not specify the type of the return value explicitly, the compiler determines the return type from the final expression.</span></span>

<span data-ttu-id="1db00-118">Basit bir işlev tanımı aşağıdakine benzer:</span><span class="sxs-lookup"><span data-stu-id="1db00-118">A simple function definition resembles the following:</span></span>

```fsharp
let f x = x + 1
```

<span data-ttu-id="1db00-119">Önceki örnekte, işlev adı `f`, bağımsız değişken türü `int`olan `x`, işlev gövdesi `x + 1`ve dönüş değeri `int`türündedir.</span><span class="sxs-lookup"><span data-stu-id="1db00-119">In the previous example, the function name is `f`, the argument is `x`, which has type `int`, the function body is `x + 1`, and the return value is of type `int`.</span></span>

<span data-ttu-id="1db00-120">İşlevler, `inline`olarak işaretlenebilir.</span><span class="sxs-lookup"><span data-stu-id="1db00-120">Functions can be marked `inline`.</span></span> <span data-ttu-id="1db00-121">`inline`hakkında bilgi için bkz. [Inline Functions](../functions/inline-functions.md).</span><span class="sxs-lookup"><span data-stu-id="1db00-121">For information about `inline`, see [Inline Functions](../functions/inline-functions.md).</span></span>

## <a name="scope"></a><span data-ttu-id="1db00-122">Kapsam</span><span class="sxs-lookup"><span data-stu-id="1db00-122">Scope</span></span>

<span data-ttu-id="1db00-123">Modül kapsamı dışında herhangi bir kapsam düzeyinde bir değer veya işlev adını yeniden kullanmak bir hata değildir.</span><span class="sxs-lookup"><span data-stu-id="1db00-123">At any level of scope other than module scope, it is not an error to reuse a value or function name.</span></span> <span data-ttu-id="1db00-124">Bir adı yeniden kullanırsanız daha sonra belirtilen ad daha önce belirtilen adı gölgeliyor.</span><span class="sxs-lookup"><span data-stu-id="1db00-124">If you reuse a name, the name declared later shadows the name declared earlier.</span></span> <span data-ttu-id="1db00-125">Ancak, modüldeki en üst düzey kapsamda adların benzersiz olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="1db00-125">However, at the top level scope in a module, names must be unique.</span></span> <span data-ttu-id="1db00-126">Örneğin, aşağıdaki kod modül kapsamında göründüğünde bir hata üretir, ancak bir işlev içinde göründüğünde değil:</span><span class="sxs-lookup"><span data-stu-id="1db00-126">For example, the following code produces an error when it appears at module scope, but not when it appears inside a function:</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet101.fs)]

<span data-ttu-id="1db00-127">Ancak aşağıdaki kod herhangi bir kapsam düzeyinde kabul edilebilir:</span><span class="sxs-lookup"><span data-stu-id="1db00-127">But the following code is acceptable at any level of scope:</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet102.fs)]

### <a name="parameters"></a><span data-ttu-id="1db00-128">Parametreler</span><span class="sxs-lookup"><span data-stu-id="1db00-128">Parameters</span></span>

<span data-ttu-id="1db00-129">Parametrelerin adları, işlev adından sonra listelenir.</span><span class="sxs-lookup"><span data-stu-id="1db00-129">Names of parameters are listed after the function name.</span></span> <span data-ttu-id="1db00-130">Bir parametre için aşağıdaki örnekte gösterildiği gibi bir tür belirtebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="1db00-130">You can specify a type for a parameter, as shown in the following example:</span></span>

```fsharp
let f (x : int) = x + 1
```

<span data-ttu-id="1db00-131">Bir tür belirtirseniz, parametrenin adını izler ve iki nokta üst üste ile birbirinden ayrılır.</span><span class="sxs-lookup"><span data-stu-id="1db00-131">If you specify a type, it follows the name of the parameter and is separated from the name by a colon.</span></span> <span data-ttu-id="1db00-132">Parametresinin türünü atlarsanız, parametre türü derleyici tarafından algılanır.</span><span class="sxs-lookup"><span data-stu-id="1db00-132">If you omit the type for the parameter, the parameter type is inferred by the compiler.</span></span> <span data-ttu-id="1db00-133">Örneğin, aşağıdaki işlev tanımında `x` bağımsız değişkeni, 1 `int`türünde olduğu için `int` türü olarak algılanır.</span><span class="sxs-lookup"><span data-stu-id="1db00-133">For example, in the following function definition, the argument `x` is inferred to be of type `int` because 1 is of type `int`.</span></span>

```fsharp
let f x = x + 1
```

<span data-ttu-id="1db00-134">Ancak derleyici, işlevi mümkün olduğunca genel olarak yapmayı dener.</span><span class="sxs-lookup"><span data-stu-id="1db00-134">However, the compiler will attempt to make the function as generic as possible.</span></span> <span data-ttu-id="1db00-135">Örneğin, aşağıdaki koda göz önünde yer verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="1db00-135">For example, note the following code:</span></span>

```fsharp
let f x = (x, x)
```

<span data-ttu-id="1db00-136">İşlevi herhangi bir türden bağımsız değişkenden bir tanımlama grubu oluşturur.</span><span class="sxs-lookup"><span data-stu-id="1db00-136">The function creates a tuple from one argument of any type.</span></span> <span data-ttu-id="1db00-137">Tür belirtilmediğinden, işlev herhangi bir bağımsız değişken türüyle kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="1db00-137">Because the type is not specified, the function can be used with any argument type.</span></span> <span data-ttu-id="1db00-138">Daha fazla bilgi için bkz. [Otomatik Genelleştirme](../generics/automatic-generalization.md).</span><span class="sxs-lookup"><span data-stu-id="1db00-138">For more information, see [Automatic Generalization](../generics/automatic-generalization.md).</span></span>

## <a name="function-bodies"></a><span data-ttu-id="1db00-139">İşlev Gövdeleri</span><span class="sxs-lookup"><span data-stu-id="1db00-139">Function Bodies</span></span>

<span data-ttu-id="1db00-140">Bir işlev gövdesi, yerel değişkenlerin ve işlevlerin tanımlarını içerebilir.</span><span class="sxs-lookup"><span data-stu-id="1db00-140">A function body can contain definitions of local variables and functions.</span></span> <span data-ttu-id="1db00-141">Bu tür değişkenler ve işlevler, geçerli işlevin gövdesinde kapsam içinde ve dışında değil.</span><span class="sxs-lookup"><span data-stu-id="1db00-141">Such variables and functions are in scope in the body of the current function but not outside it.</span></span> <span data-ttu-id="1db00-142">Hafif sözdizimi seçeneğini etkinleştirdiğinizde, aşağıdaki örnekte gösterildiği gibi bir tanımın bir işlev gövdesinde olduğunu göstermek için girinti kullanmanız gerekir:</span><span class="sxs-lookup"><span data-stu-id="1db00-142">When you have the lightweight syntax option enabled, you must use indentation to indicate that a definition is in a function body, as shown in the following example:</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet103.fs)]

<span data-ttu-id="1db00-143">Daha fazla bilgi için bkz. [kod biçimlendirme yönergeleri](../../style-guide/formatting.md) ve [ayrıntılı sözdizimi](../verbose-syntax.md).</span><span class="sxs-lookup"><span data-stu-id="1db00-143">For more information, see [Code Formatting Guidelines](../../style-guide/formatting.md) and [Verbose Syntax](../verbose-syntax.md).</span></span>

## <a name="return-values"></a><span data-ttu-id="1db00-144">Dönüş Değerleri</span><span class="sxs-lookup"><span data-stu-id="1db00-144">Return Values</span></span>

<span data-ttu-id="1db00-145">Derleyici, dönüş değerini ve türünü belirleyebilmek için bir işlev gövdesinde son ifadeyi kullanır.</span><span class="sxs-lookup"><span data-stu-id="1db00-145">The compiler uses the final expression in a function body to determine the return value and type.</span></span> <span data-ttu-id="1db00-146">Derleyici, önceki ifadelerden son ifadenin türünü çıkarmayabilir.</span><span class="sxs-lookup"><span data-stu-id="1db00-146">The compiler might infer the type of the final expression from previous expressions.</span></span> <span data-ttu-id="1db00-147">Önceki bölümde gösterilen `cylinderVolume`işlevinde, `pi` türü, sabit değer `3.14159` `float`olacak şekilde belirlenir.</span><span class="sxs-lookup"><span data-stu-id="1db00-147">In the function `cylinderVolume`, shown in the previous section, the type of `pi` is determined from the type of the literal `3.14159` to be `float`.</span></span> <span data-ttu-id="1db00-148">Derleyici, `float`olacak `h * pi * r * r` ifade türünü belirleyebilmek için `pi` türünü kullanır.</span><span class="sxs-lookup"><span data-stu-id="1db00-148">The compiler uses the type of `pi` to determine the type of the expression `h * pi * r * r` to be `float`.</span></span> <span data-ttu-id="1db00-149">Bu nedenle, işlevin genel dönüş türü `float`.</span><span class="sxs-lookup"><span data-stu-id="1db00-149">Therefore, the overall return type of the function is `float`.</span></span>

<span data-ttu-id="1db00-150">Dönüş değerini açık olarak belirtmek için, kodu aşağıdaki gibi yazın:</span><span class="sxs-lookup"><span data-stu-id="1db00-150">To specify the return value explicitly, write the code as follows:</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet105.fs)]

<span data-ttu-id="1db00-151">Kod yukarıda yazıldığı için, derleyici tüm işleve **float** uygular; parametresi parametre türlerine de uygulamak için aşağıdaki kodu kullanın:</span><span class="sxs-lookup"><span data-stu-id="1db00-151">As the code is written above, the compiler applies **float** to the entire function; if you mean to apply it to the parameter types as well, use the following code:</span></span>

```fsharp
let cylinderVolume (radius : float) (length : float) : float
```

## <a name="calling-a-function"></a><span data-ttu-id="1db00-152">İşlev Çağırma</span><span class="sxs-lookup"><span data-stu-id="1db00-152">Calling a Function</span></span>

<span data-ttu-id="1db00-153">İşlev adını ve ardından boşluk ile ayrılmış bağımsız değişkenleri belirterek işlevleri çağırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1db00-153">You call functions by specifying the function name followed by a space and then any arguments separated by spaces.</span></span> <span data-ttu-id="1db00-154">Örneğin, **silindir Dervolume** işlevini çağırmak ve sonucu değer **Ses**'e atamak için aşağıdaki kodu yazarsınız:</span><span class="sxs-lookup"><span data-stu-id="1db00-154">For example, to call the function **cylinderVolume** and assign the result to the value **vol**, you write the following code:</span></span>

```fsharp
let vol = cylinderVolume 2.0 3.0
```

## <a name="partial-application-of-arguments"></a><span data-ttu-id="1db00-155">Bağımsız Değişkenlerin Kısmi Uygulanması</span><span class="sxs-lookup"><span data-stu-id="1db00-155">Partial Application of Arguments</span></span>

<span data-ttu-id="1db00-156">Belirtilen sayıda bağımsız değişkene daha az bir değer sağlarsanız, kalan bağımsız değişkenleri bekleyen yeni bir işlev oluşturursunuz.</span><span class="sxs-lookup"><span data-stu-id="1db00-156">If you supply fewer than the specified number of arguments, you create a new function that expects the remaining arguments.</span></span> <span data-ttu-id="1db00-157">Bu bağımsız değişken işleme yöntemi, gibi F#işlevsel programlama dillerinin bir *özelliğidir ve olarak* adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="1db00-157">This method of handling arguments is referred to as *currying* and is a characteristic of functional programming languages like F#.</span></span> <span data-ttu-id="1db00-158">Örneğin, iki kanal boyutu ile çalıştığınızı varsayalım: biri **2,0** radius ve diğeri ise **3,0**yarıçapı vardır.</span><span class="sxs-lookup"><span data-stu-id="1db00-158">For example, suppose you are working with two sizes of pipe: one has a radius of **2.0** and the other has a radius of **3.0**.</span></span> <span data-ttu-id="1db00-159">Aşağıdaki gibi kanal hacmini tespit eden işlevler oluşturabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="1db00-159">You could create functions that determine the volume of pipe as follows:</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet106.fs)]

<span data-ttu-id="1db00-160">Daha sonra, iki farklı boyuttan oluşan çeşitli uzunluklar için gereken ek bağımsız değişkeni sağlamanız gerekir:</span><span class="sxs-lookup"><span data-stu-id="1db00-160">You would then supply the additional argument as needed for various lengths of pipe of the two different sizes:</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet107.fs)]

## <a name="recursive-functions"></a><span data-ttu-id="1db00-161">Özyinelemeli İşlevler</span><span class="sxs-lookup"><span data-stu-id="1db00-161">Recursive Functions</span></span>

<span data-ttu-id="1db00-162">*Özyinelemeli işlevler* kendilerini çağıran işlevlerdir.</span><span class="sxs-lookup"><span data-stu-id="1db00-162">*Recursive functions* are functions that call themselves.</span></span> <span data-ttu-id="1db00-163">**Let** anahtar sözcüğünü takip eden **REC** anahtar sözcüğünü belirtmenizi gerektirir.</span><span class="sxs-lookup"><span data-stu-id="1db00-163">They require that you specify the **rec** keyword following the **let** keyword.</span></span> <span data-ttu-id="1db00-164">Herhangi bir işlev çağrısını çağırırın olduğu gibi, işlev gövdesinin içinden özyinelemeli işlevi çağırın.</span><span class="sxs-lookup"><span data-stu-id="1db00-164">Invoke the recursive function from within the body of the function just as you would invoke any function call.</span></span> <span data-ttu-id="1db00-165">Aşağıdaki özyinelemeli işlev *n*<sup>.</sup> fibonaccı numarasını hesaplar.</span><span class="sxs-lookup"><span data-stu-id="1db00-165">The following recursive function computes the *n*<sup>th</sup> Fibonacci number.</span></span> <span data-ttu-id="1db00-166">Fibonaccı numara sırası, Antiquity 'in bilindiği ve ardışık her sayının dizideki önceki iki sayının toplamı olduğu bir sıralamadır.</span><span class="sxs-lookup"><span data-stu-id="1db00-166">The Fibonacci number sequence has been known since antiquity and is a sequence in which each successive number is the sum of the previous two numbers in the sequence.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet108.fs)]

<span data-ttu-id="1db00-167">Bazı Özyinelemeli işlevler program yığınını taşımayabilir veya işlevindeki biriktiricileri ve devamlılık kullanımı gibi özel tekniklerin farkında olmak üzere, bunları dikkatli bir şekilde yazmayabilir.</span><span class="sxs-lookup"><span data-stu-id="1db00-167">Some recursive functions might overflow the program stack or perform inefficiently if you do not write them with care and with awareness of special techniques, such as the use of accumulators and continuations.</span></span>

## <a name="function-values"></a><span data-ttu-id="1db00-168">İşlev Değerleri</span><span class="sxs-lookup"><span data-stu-id="1db00-168">Function Values</span></span>

<span data-ttu-id="1db00-169">' F#De, tüm işlevler değer olarak değerlendirilir; Aslında, *işlev değerleri*olarak bilinir.</span><span class="sxs-lookup"><span data-stu-id="1db00-169">In F#, all functions are considered values; in fact, they are known as *function values*.</span></span> <span data-ttu-id="1db00-170">İşlevler değerler olduğundan, diğer işlevlerde veya değerlerin kullanıldığı diğer bağlamlarda bağımsız değişkenler olarak kullanılabilirler.</span><span class="sxs-lookup"><span data-stu-id="1db00-170">Because functions are values, they can be used as arguments to other functions or in other contexts where values are used.</span></span> <span data-ttu-id="1db00-171">Bağımsız değişken olarak bir işlev değeri alan bir işlev örneği aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="1db00-171">Following is an example of a function that takes a function value as an argument:</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet109.fs)]

<span data-ttu-id="1db00-172">`->` belirtecini kullanarak bir işlev değeri türünü belirtirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1db00-172">You specify the type of a function value by using the `->` token.</span></span> <span data-ttu-id="1db00-173">Bu belirtecin sol tarafında, bağımsız değişkenin türü ve sağ tarafta ise dönüş değeri bulunur.</span><span class="sxs-lookup"><span data-stu-id="1db00-173">On the left side of this token is the type of the argument, and on the right side is the return value.</span></span> <span data-ttu-id="1db00-174">Önceki örnekte `apply1`, bir bağımsız değişken olarak bir işlev `transform` alan, `transform` bir tamsayı alan ve başka bir tamsayı döndüren bir işlevdir.</span><span class="sxs-lookup"><span data-stu-id="1db00-174">In the previous example, `apply1` is a function that takes a function `transform` as an argument, where `transform` is a function that takes an integer and returns another integer.</span></span> <span data-ttu-id="1db00-175">Aşağıdaki kod `apply1`nasıl kullanacağınızı gösterir:</span><span class="sxs-lookup"><span data-stu-id="1db00-175">The following code shows how to use `apply1`:</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet110.fs)]

<span data-ttu-id="1db00-176">`result` değeri, önceki kod çalıştıktan sonra 101 olacaktır.</span><span class="sxs-lookup"><span data-stu-id="1db00-176">The value of `result` will be 101 after the previous code runs.</span></span>

<span data-ttu-id="1db00-177">Aşağıdaki örnekte gösterildiği gibi, birden çok bağımsız değişken birbirini izleyen `->` belirteçleriyle ayrılır:</span><span class="sxs-lookup"><span data-stu-id="1db00-177">Multiple arguments are separated by successive `->` tokens, as shown in the following example:</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet111.fs)]

<span data-ttu-id="1db00-178">Sonuç 200 ' dir.</span><span class="sxs-lookup"><span data-stu-id="1db00-178">The result is 200.</span></span>

## <a name="lambda-expressions"></a><span data-ttu-id="1db00-179">Lambda İfadeleri</span><span class="sxs-lookup"><span data-stu-id="1db00-179">Lambda Expressions</span></span>

<span data-ttu-id="1db00-180">*Lambda ifadesi* adlandırılmamış bir işlevdir.</span><span class="sxs-lookup"><span data-stu-id="1db00-180">A *lambda expression* is an unnamed function.</span></span> <span data-ttu-id="1db00-181">Önceki örneklerde, adlandırılmış işlevleri **artırma** ve **MUL**tanımlamak yerine Lambda ifadelerini aşağıdaki şekilde kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="1db00-181">In the previous examples, instead of defining named functions **increment** and **mul**, you could use lambda expressions as follows:</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet112.fs)]

<span data-ttu-id="1db00-182">Lambda ifadelerini `fun` anahtar sözcüğünü kullanarak tanımlarsınız.</span><span class="sxs-lookup"><span data-stu-id="1db00-182">You define lambda expressions by using the `fun` keyword.</span></span> <span data-ttu-id="1db00-183">Lambda ifadesi bir işlev tanımına benzer, ancak `=` belirteci yerine, bağımsız değişken listesini işlev gövdesinden ayırmak için `->` belirteci kullanılır.</span><span class="sxs-lookup"><span data-stu-id="1db00-183">A lambda expression resembles a function definition, except that instead of the `=` token, the `->` token is used to separate the argument list from the function body.</span></span> <span data-ttu-id="1db00-184">Normal bir işlev tanımında olduğu gibi, bağımsız değişken türleri açıkça çıkarsanamıyor veya belirlenebilir ve lambda ifadesinin dönüş türü, gövdedeki son ifadenin türünden çıkarsanamıyor.</span><span class="sxs-lookup"><span data-stu-id="1db00-184">As in a regular function definition, the argument types can be inferred or specified explicitly, and the return type of the lambda expression is inferred from the type of the last expression in the body.</span></span> <span data-ttu-id="1db00-185">Daha fazla bilgi için bkz. [lambda ifadeleri: `fun` anahtar sözcüğü](../functions/lambda-expressions-the-fun-keyword.md).</span><span class="sxs-lookup"><span data-stu-id="1db00-185">For more information, see [Lambda Expressions: The `fun` Keyword](../functions/lambda-expressions-the-fun-keyword.md).</span></span>

## <a name="function-composition-and-pipelining"></a><span data-ttu-id="1db00-186">İşlev Bileşimi ve Ardışık Düzen Oluşturma</span><span class="sxs-lookup"><span data-stu-id="1db00-186">Function Composition and Pipelining</span></span>

<span data-ttu-id="1db00-187">İçindeki F# işlevler diğer işlevlerden oluşabilir.</span><span class="sxs-lookup"><span data-stu-id="1db00-187">Functions in F# can be composed from other functions.</span></span> <span data-ttu-id="1db00-188">İki işlev **işlev1** ve **function2** bileşimi, **işlev1** uygulamasının **function2**uygulamasını temsil eden başka bir işlevdir:</span><span class="sxs-lookup"><span data-stu-id="1db00-188">The composition of two functions **function1** and **function2** is another function that represents the application of **function1** followed the application of **function2**:</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet113.fs)]

<span data-ttu-id="1db00-189">Sonuç 202 ' dir.</span><span class="sxs-lookup"><span data-stu-id="1db00-189">The result is 202.</span></span>

<span data-ttu-id="1db00-190">Ardışık düzen oluşturma, işlev çağrılarının ardışık işlemler olarak birlikte zincirde olmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="1db00-190">Pipelining enables function calls to be chained together as successive operations.</span></span> <span data-ttu-id="1db00-191">Ardışık düzen oluşturma aşağıdaki gibi çalışmaktadır:</span><span class="sxs-lookup"><span data-stu-id="1db00-191">Pipelining works as follows:</span></span>

```fsharp
let result = 100 |> function1 |> function2
```

<span data-ttu-id="1db00-192">Sonuç yeniden 202 ' dir.</span><span class="sxs-lookup"><span data-stu-id="1db00-192">The result is again 202.</span></span>

<span data-ttu-id="1db00-193">Kompozisyon işleçleri iki işlev alır ve bir işlev döndürür; Buna karşılık, işlem hattı işleçleri bir işlevi ve bir bağımsız değişkeni alır ve bir değer döndürür.</span><span class="sxs-lookup"><span data-stu-id="1db00-193">The composition operators take two functions and return a function; by contrast, the pipeline operators take a function and an argument and return a value.</span></span> <span data-ttu-id="1db00-194">Aşağıdaki kod örneği, işlev imzalarındaki ve kullanımındaki farklılıkları göstererek işlem hattı ve bileşim işleçleri arasındaki farkı gösterir.</span><span class="sxs-lookup"><span data-stu-id="1db00-194">The following code example shows the difference between the pipeline and composition operators by showing the differences in the function signatures and usage.</span></span>

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

## <a name="overloading-functions"></a><span data-ttu-id="1db00-195">Aşırı Yükleme İşlevleri</span><span class="sxs-lookup"><span data-stu-id="1db00-195">Overloading Functions</span></span>

<span data-ttu-id="1db00-196">Bir türün yöntemlerini aşırı yükleyebilirsiniz ancak işlevleri kullanamazsınız.</span><span class="sxs-lookup"><span data-stu-id="1db00-196">You can overload methods of a type but not functions.</span></span> <span data-ttu-id="1db00-197">Daha fazla bilgi için bkz. [Yöntemler](../members/methods.md).</span><span class="sxs-lookup"><span data-stu-id="1db00-197">For more information, see [Methods](../members/methods.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="1db00-198">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1db00-198">See also</span></span>

- [<span data-ttu-id="1db00-199">Değerler</span><span class="sxs-lookup"><span data-stu-id="1db00-199">Values</span></span>](../values/index.md)
- [<span data-ttu-id="1db00-200">F# Dili Başvurusu</span><span class="sxs-lookup"><span data-stu-id="1db00-200">F# Language Reference</span></span>](../index.md)
