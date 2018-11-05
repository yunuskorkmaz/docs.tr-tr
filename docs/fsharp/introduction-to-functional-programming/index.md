---
title: 'F # İşlevsel Programlamaya Giriş'
description: İşlevsel programlamaya temellerini öğrenin F#.
ms.date: 10/29/2018
ms.openlocfilehash: d4a9bb0cd826b41aca96e12e2bcb5aab80c18eb4
ms.sourcegitcommit: db8b83057d052c1f9f249d128b08d4423af0f7c2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/02/2018
ms.locfileid: "25863842"
---
# <a name="introduction-to-functional-programming-in-f"></a><span data-ttu-id="cf5e3-103">F # İşlevsel Programlamaya Giriş</span><span class="sxs-lookup"><span data-stu-id="cf5e3-103">Introduction to Functional Programming in F#</span></span> #

<span data-ttu-id="cf5e3-104">İşlevsel programlama, İşlevler ve sabit veri kullanımını vurgulamaktadır programlama stilidir.</span><span class="sxs-lookup"><span data-stu-id="cf5e3-104">Functional programming is a style of programming that emphasizes the use of functions and immutable data.</span></span> <span data-ttu-id="cf5e3-105">Türü belirlenmiş işlevsel programlama, işlevsel programlama statik türler ile gibi ile birleştirildiğinde F#.</span><span class="sxs-lookup"><span data-stu-id="cf5e3-105">Typed functional programming is when functional programming is combined with static types, such as with F#.</span></span> <span data-ttu-id="cf5e3-106">Genel olarak, aşağıdaki kavramları işlevsel programlamaya vurgulanır:</span><span class="sxs-lookup"><span data-stu-id="cf5e3-106">In general, the following concepts are emphasized in functional programming:</span></span>

* <span data-ttu-id="cf5e3-107">Kullandığınız yönelik birincil yapılar işlevleri</span><span class="sxs-lookup"><span data-stu-id="cf5e3-107">Functions as the primary constructs you use</span></span>
* <span data-ttu-id="cf5e3-108">İfadeler yerine deyimleri</span><span class="sxs-lookup"><span data-stu-id="cf5e3-108">Expressions instead of statements</span></span>
* <span data-ttu-id="cf5e3-109">Değişkenler üzerinde değişmez değerleri</span><span class="sxs-lookup"><span data-stu-id="cf5e3-109">Immutable values over variables</span></span>
* <span data-ttu-id="cf5e3-110">Bildirim temelli üzerinden zorunlu programlama</span><span class="sxs-lookup"><span data-stu-id="cf5e3-110">Declarative programming over imperative programming</span></span>

<span data-ttu-id="cf5e3-111">Bu seri boyunca kavramları ve desenler işlevsel programlama kullanarak keşfedeceksiniz F#.</span><span class="sxs-lookup"><span data-stu-id="cf5e3-111">Throughout this series, you'll explore concepts and patterns in functional programming using F#.</span></span> <span data-ttu-id="cf5e3-112">Bu doğrultuda, bazı öğreneceksiniz F# çok.</span><span class="sxs-lookup"><span data-stu-id="cf5e3-112">Along the way, you'll learn some F# too.</span></span>

## <a name="terminology"></a><span data-ttu-id="cf5e3-113">Terminoloji</span><span class="sxs-lookup"><span data-stu-id="cf5e3-113">Terminology</span></span>

<span data-ttu-id="cf5e3-114">Diğer programlama paradigmalarını gibi fonksiyonel programlama sonunda öğrenmek için ihtiyacınız olacak bir sözlük ile birlikte gelir.</span><span class="sxs-lookup"><span data-stu-id="cf5e3-114">Functional programming, like other programming paradigms, comes with a vocabulary that you will eventually need to learn.</span></span> <span data-ttu-id="cf5e3-115">Her zaman göreceğiniz bazı ortak şartları şunlardır:</span><span class="sxs-lookup"><span data-stu-id="cf5e3-115">Here are some common terms you'll see all of the time:</span></span>

* <span data-ttu-id="cf5e3-116">**İşlev** -bir işlev bir giriş verildiğinde bir çıktı oluşturacak bir yapıdır.</span><span class="sxs-lookup"><span data-stu-id="cf5e3-116">**Function** - A function is a construct that will produce an output when given an input.</span></span> <span data-ttu-id="cf5e3-117">Daha fazla izlerse, _eşler_ birinden bir öğe için başka bir grubu ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="cf5e3-117">More formally, it _maps_ an item from one set to another set.</span></span> <span data-ttu-id="cf5e3-118">Bu formalism özellikle çalışan işlevler koleksiyon veri kullanılırken, pek çok yolla somut içine kaldırılır.</span><span class="sxs-lookup"><span data-stu-id="cf5e3-118">This formalism is lifted into the concrete in many ways, especially when using functions that operate on collections of data.</span></span> <span data-ttu-id="cf5e3-119">Bu, en temel (ve önemli) kavram olarak fonksiyonel programlama olur.</span><span class="sxs-lookup"><span data-stu-id="cf5e3-119">It is the most basic (and important) concept in functional programming.</span></span> 
* <span data-ttu-id="cf5e3-120">**İfade** -bir ifade bir değer üreten kodda bir yapıdır.</span><span class="sxs-lookup"><span data-stu-id="cf5e3-120">**Expression** - An expression is a construct in code that produces a value.</span></span> <span data-ttu-id="cf5e3-121">İçinde F#, bu değer bağlı veya açıkça yoksayıldı.</span><span class="sxs-lookup"><span data-stu-id="cf5e3-121">In F#, this value must be bound or explicitly ignored.</span></span> <span data-ttu-id="cf5e3-122">Bir ifade, basit bir şekilde işlev çağrısına göre değiştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="cf5e3-122">An expression can be trivially replaced by a function call.</span></span>
* <span data-ttu-id="cf5e3-123">**Saflığa** -Saflığa olduğu bir özelliği bir işlevin dönüş değeri her zaman aynı bağımsız değişkenleri aynı olduğundan emin ve kendi değerlendirme yan etkileri vardır.</span><span class="sxs-lookup"><span data-stu-id="cf5e3-123">**Purity** - Purity is a property of a function such that its return value is always the same for the same arguments, and that its evaluation has no side effects.</span></span> <span data-ttu-id="cf5e3-124">Saf işlev tamamen bağımsız değişkenlerini bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="cf5e3-124">A pure function depends entirely on its arguments.</span></span>
* <span data-ttu-id="cf5e3-125">**Başvuru saydamlık** -başvuru saydamlık çıktılarını ile bunlar değiştirilebilir bir programın davranışını etkilemeden, ifadelerin bir özelliği olan.</span><span class="sxs-lookup"><span data-stu-id="cf5e3-125">**Referential Transparency** - Referential Transparency is a property of expressions such that they can be replaced with their output without affecting a program's behavior.</span></span>
* <span data-ttu-id="cf5e3-126">**Değiştirilemezlik** -değiştirilen yerinde bir değer olamaz Değiştirilemezlik anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="cf5e3-126">**Immutability** - Immutability means that a value cannot be changed in-place.</span></span> <span data-ttu-id="cf5e3-127">Yerinde değiştirebileceğiniz değişkenler kullanılmasının budur.</span><span class="sxs-lookup"><span data-stu-id="cf5e3-127">This is in contrast with variables, which can change in place.</span></span>

## <a name="examples"></a><span data-ttu-id="cf5e3-128">Örnekler</span><span class="sxs-lookup"><span data-stu-id="cf5e3-128">Examples</span></span>

<span data-ttu-id="cf5e3-129">Aşağıdaki örnekler, bu kavramları göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="cf5e3-129">The following examples demonstrate these core concepts.</span></span>

### <a name="functions"></a><span data-ttu-id="cf5e3-130">İşlevler</span><span class="sxs-lookup"><span data-stu-id="cf5e3-130">Functions</span></span>

<span data-ttu-id="cf5e3-131">En yaygın ve temel işlevsel programlama yapısında işlevdir.</span><span class="sxs-lookup"><span data-stu-id="cf5e3-131">The most common and fundamental construct in functional programming is the function.</span></span> <span data-ttu-id="cf5e3-132">Tamsayıya 1 ekler, basit bir işlevi şu şekildedir:</span><span class="sxs-lookup"><span data-stu-id="cf5e3-132">Here's a simple function that adds 1 to an integer:</span></span>

```fsharp
let addOne x = x + 1
```

<span data-ttu-id="cf5e3-133">Tür imzası aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="cf5e3-133">Its type signature is as follows:</span></span>

```fsharp
val addOne: x:int -> int
```

<span data-ttu-id="cf5e3-134">İmza, okunabilir "`addOne` kabul eden bir `int` adlı `x` ve oluşturacak bir `int`".</span><span class="sxs-lookup"><span data-stu-id="cf5e3-134">The signature can be read as, "`addOne` accepts an `int` named `x` and will produce an `int`".</span></span> <span data-ttu-id="cf5e3-135">Daha eski adıyla `addOne` olduğu _eşleme_ tamsayılar kümesi ile tamsayılar kümesi arasında bir değer.</span><span class="sxs-lookup"><span data-stu-id="cf5e3-135">More formally, `addOne` is _mapping_ a value from the set of integers to the set of integers.</span></span> <span data-ttu-id="cf5e3-136">`->` Belirteci bu eşlemeyi gösterir.</span><span class="sxs-lookup"><span data-stu-id="cf5e3-136">The `->` token signifies this mapping.</span></span> <span data-ttu-id="cf5e3-137">İçinde F#, ne yaptığını fikir işlev imzası genellikle bakabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="cf5e3-137">In F#, you can usually look at the function signature to get a sense for what it does.</span></span>

<span data-ttu-id="cf5e3-138">Bu nedenle, neden imza önemlidir?</span><span class="sxs-lookup"><span data-stu-id="cf5e3-138">So, why is the signature important?</span></span> <span data-ttu-id="cf5e3-139">Türü belirlenmiş işlevsel programlama, bir işlev uygulaması genellikle küçük gerçek tür imzası daha önemlidir!</span><span class="sxs-lookup"><span data-stu-id="cf5e3-139">In typed functional programming, the implementation of a function is often less important than the actual type signature!</span></span> <span data-ttu-id="cf5e3-140">Olgu, `addOne` çalışma zamanında, ilgi çekici bir tamsayı değerine 1 ekler ancak zaman, oluşturmak bir program kabul edip döndürür olgu bir `int` olduğundan bu işlev gerçekte nasıl kullanacağını ne bildirir.</span><span class="sxs-lookup"><span data-stu-id="cf5e3-140">The fact that `addOne` adds the value 1 to an integer is interesting at runtime, but when you are constructing a program, the fact that it accepts and returns an `int` is what informs how you will actually use this function.</span></span> <span data-ttu-id="cf5e3-141">Bu işlev doğru (göre türü imzası) kullandığınızda, ayrıca, herhangi bir sorunu tanılamada gövdesi içinde yalnızca yapılabilir `addOne` işlevi.</span><span class="sxs-lookup"><span data-stu-id="cf5e3-141">Furthermore, once you use this function correctly (with respect to its type signature), diagnosing any problems can be done only within the body of the `addOne` function.</span></span> <span data-ttu-id="cf5e3-142">Arkasında yazılı işlevsel programlama impetus budur.</span><span class="sxs-lookup"><span data-stu-id="cf5e3-142">This is the impetus behind typed functional programming.</span></span>

### <a name="expressions"></a><span data-ttu-id="cf5e3-143">İfadeler</span><span class="sxs-lookup"><span data-stu-id="cf5e3-143">Expressions</span></span>

<span data-ttu-id="cf5e3-144">İfade bir değer olarak değerlendirilmesi yapılarıdır.</span><span class="sxs-lookup"><span data-stu-id="cf5e3-144">Expressions are constructs that evaluate to a value.</span></span> <span data-ttu-id="cf5e3-145">Bir eylem gerçekleştirmek, deyimleri aksine, geri bir değer veren bir eylem gerçekleştirmek ifadeleri düşünülebilir.</span><span class="sxs-lookup"><span data-stu-id="cf5e3-145">In contrast to statements, which perform an action, expressions can be thought of performing an action that gives back a value.</span></span> <span data-ttu-id="cf5e3-146">İfadeler, neredeyse her zaman işlevsel programlama deyimlerinde yerine kullanılır.</span><span class="sxs-lookup"><span data-stu-id="cf5e3-146">Expressions are almost always used in favor of statements in functional programming.</span></span>

<span data-ttu-id="cf5e3-147">Önceki işlevi `addOne`.</span><span class="sxs-lookup"><span data-stu-id="cf5e3-147">Consider the previous function, `addOne`.</span></span> <span data-ttu-id="cf5e3-148">Gövdesi `addOne` ifade:</span><span class="sxs-lookup"><span data-stu-id="cf5e3-148">The body of `addOne` is an expression:</span></span>

```fsharp
// 'x + 1' is an expression!
let addOne x = x + 1
```

<span data-ttu-id="cf5e3-149">Bu ifadenin sonuç türü tanımlayan sonucudur `addOne` işlevi.</span><span class="sxs-lookup"><span data-stu-id="cf5e3-149">It is the result of this expression that defines the result type of the `addOne` function.</span></span> <span data-ttu-id="cf5e3-150">Örneğin, bu işlevi oluşturan ifade gibi farklı bir tür olarak değiştirilemedi bir `string`:</span><span class="sxs-lookup"><span data-stu-id="cf5e3-150">For example, the expression that makes up this function could be changed to be a different type, such as a `string`:</span></span>

```fsharp
let addOne x = x.ToString() + "1"
```

<span data-ttu-id="cf5e3-151">İşlev imzası sunulmuştur:</span><span class="sxs-lookup"><span data-stu-id="cf5e3-151">The signature of the function is now:</span></span>

```fsharp
val addOne: x:'a -> string
```

<span data-ttu-id="cf5e3-152">Herhangi bir türü beri F# olabilir `ToString()` bunun üzerinde türü adlı `x` genel yapılan (adlı [otomatik Genelleştirme](../language-reference/generics/automatic-generalization.md)), ve sonuç türü bir `string`.</span><span class="sxs-lookup"><span data-stu-id="cf5e3-152">Since any type in F# can have `ToString()` called on it, the type of `x` has been made generic (called [Automatic Generalization](../language-reference/generics/automatic-generalization.md)), and the resultant type is a `string`.</span></span>

<span data-ttu-id="cf5e3-153">İfadeleri yalnızca işlev gövdeleri değildir.</span><span class="sxs-lookup"><span data-stu-id="cf5e3-153">Expressions are not just the bodies of functions.</span></span> <span data-ttu-id="cf5e3-154">Başka bir yerde kullanmak için bir değer üreten ifadeleri olabilir.</span><span class="sxs-lookup"><span data-stu-id="cf5e3-154">You can have expressions that produce a value you use elsewhere.</span></span> <span data-ttu-id="cf5e3-155">Bir ortak biridir `if`:</span><span class="sxs-lookup"><span data-stu-id="cf5e3-155">A common one is `if`:</span></span>

```fsharp
// Checks if 'x' is odd by using the mod operator
let isOdd x = x % 2 <> 0

let addOneIfOdd input =
    let result =
        if isOdd input then
            input + 1
        else
            input

    result
```

<span data-ttu-id="cf5e3-156">`if` İfade olarak adlandırılan bir değer oluşturuyor `result`.</span><span class="sxs-lookup"><span data-stu-id="cf5e3-156">The `if` expression produces a value called `result`.</span></span> <span data-ttu-id="cf5e3-157">Atlarsanız Not `result` tamamen yapmadan `if` ifade gövdesi, `addOneIfOdd` işlevi.</span><span class="sxs-lookup"><span data-stu-id="cf5e3-157">Note that you could omit `result` entirely, making the `if` expression the body of the `addOneIfOdd` function.</span></span> <span data-ttu-id="cf5e3-158">Deyimler hakkında hatırlamak anahtar değer üretme şeydir.</span><span class="sxs-lookup"><span data-stu-id="cf5e3-158">The key thing to remember about expressions is that they produce a value.</span></span>

<span data-ttu-id="cf5e3-159">Özel bir tür `unit`, olduğunda döndürülecek bir şey kullanılır.</span><span class="sxs-lookup"><span data-stu-id="cf5e3-159">There is a special type, `unit`, that is used when there is nothing to return.</span></span> <span data-ttu-id="cf5e3-160">Örneğin, bu basit işlev göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="cf5e3-160">For example, consider this simple function:</span></span>

```fsharp
let printString (str: string) =
    printfn "String is: %s" s
```

<span data-ttu-id="cf5e3-161">İmza şöyle görünür:</span><span class="sxs-lookup"><span data-stu-id="cf5e3-161">The signature looks like this:</span></span>

```fsharp
val printString: str:string -> unit
```

<span data-ttu-id="cf5e3-162">`unit` Türü, döndürülen gerçek değer olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="cf5e3-162">The `unit` type indicates that there is no actual value being returned.</span></span> <span data-ttu-id="cf5e3-163">Gereken bir yordamı olması gerektiğinde bu faydalıdır "İş" Bu çalışma sonucunda döndürülecek değer sahip olmasına rağmen.</span><span class="sxs-lookup"><span data-stu-id="cf5e3-163">This is useful when you have a routine that must "do work" despite having no value to return as a result of that work.</span></span>

<span data-ttu-id="cf5e3-164">Kesin programlama sharp Karşıtlık budur burada eşdeğer `if` yapıdır bir deyim ve değerleri üreten genellikle yapılır değişkenleri diziyi ile.</span><span class="sxs-lookup"><span data-stu-id="cf5e3-164">This is in sharp contrast to imperative programming, where the equivalent `if` construct is a statement, and producing values is often done with mutating variables.</span></span> <span data-ttu-id="cf5e3-165">Örneğin, C#, kod şu şekilde yazılmış olabilir:</span><span class="sxs-lookup"><span data-stu-id="cf5e3-165">For example, in C#, the code might be written like this:</span></span>

```csharp
bool IsOdd(int x) => x % 2 != 0;

int AddOneIfOdd(int input)
{
    var result = input;

    if (IsOdd(input))
    {
        result = input + 1;
    }

    return result;
}
```

<span data-ttu-id="cf5e3-166">Hatalarının ayıklanabileceğini belirtmekte yarar C# ve diğer C stili dillerin desteği [Üçlü ifade](../../csharp/language-reference/operators/conditional-operator.md), ifade tabanlı koşullu programlama için izin verir.</span><span class="sxs-lookup"><span data-stu-id="cf5e3-166">It's worth noting that C# and other C-style languages do support the [ternary expression](../../csharp/language-reference/operators/conditional-operator.md), which allows for expression-based conditional programming.</span></span>

<span data-ttu-id="cf5e3-167">İşlevsel programlama, bu deyimleri değerlerle kesilecek nadir olarak rastlanıyor.</span><span class="sxs-lookup"><span data-stu-id="cf5e3-167">In functional programming, it is rare to mutate values with statements.</span></span> <span data-ttu-id="cf5e3-168">Bazı işlevsel dillerin deyimleri ve Mutasyon desteklese de, bu kavramları işlevsel programlamaya kullanmak yaygın değildir.</span><span class="sxs-lookup"><span data-stu-id="cf5e3-168">Although some functional languages support statements and mutation, it is not common to use these concepts in functional programming.</span></span>

### <a name="pure-functions"></a><span data-ttu-id="cf5e3-169">Saf İşlevler</span><span class="sxs-lookup"><span data-stu-id="cf5e3-169">Pure functions</span></span>

<span data-ttu-id="cf5e3-170">Daha önce belirtildiği gibi saf İşlevler, işlev:</span><span class="sxs-lookup"><span data-stu-id="cf5e3-170">As previously mentioned, pure functions are functions that:</span></span>

* <span data-ttu-id="cf5e3-171">Aynı değere aynı giriş için her zaman değerlendirin.</span><span class="sxs-lookup"><span data-stu-id="cf5e3-171">Always evaluate to the same value for the same input.</span></span>
* <span data-ttu-id="cf5e3-172">Hiçbir yan etkisi yoktur.</span><span class="sxs-lookup"><span data-stu-id="cf5e3-172">Have no side effects.</span></span>

<span data-ttu-id="cf5e3-173">Matematik işlevleri bu bağlamda düşünmek faydalıdır.</span><span class="sxs-lookup"><span data-stu-id="cf5e3-173">It is helpful to think of mathematical functions in this context.</span></span> <span data-ttu-id="cf5e3-174">Matematik, işlevleri yalnızca kendi bağımsız değişkenlerine göre değişir ve tüm yan etkileri izniniz yok.</span><span class="sxs-lookup"><span data-stu-id="cf5e3-174">In mathematics, functions depend only on their arguments and do not have any side effects.</span></span> <span data-ttu-id="cf5e3-175">Matematik işlevindeki `f(x) = x + 1`, değerini `f(x)` yalnızca değerine bağlıdır `x`.</span><span class="sxs-lookup"><span data-stu-id="cf5e3-175">In the mathematical function `f(x) = x + 1`, the value of `f(x)` depends only on the value of `x`.</span></span> <span data-ttu-id="cf5e3-176">Saf işlevsel programlama, aynı şekilde işlevlerdir.</span><span class="sxs-lookup"><span data-stu-id="cf5e3-176">Pure functions in functional programming are the same way.</span></span>

<span data-ttu-id="cf5e3-177">Saf işlev yazarken işlevi bağımsız değişkenlerinden yalnızca üzerinde bağlıdır ve sonuçları bir yan etkisi herhangi bir eylem gerçekleştirmenize gerekir.</span><span class="sxs-lookup"><span data-stu-id="cf5e3-177">When writing a pure function, the function must depend only on its arguments and not perform any action that results in a side effect.</span></span>

<span data-ttu-id="cf5e3-178">Aşağıda, genel, kesilebilir durumuna bağlıdır çünkü saf olmayan işlev örneği verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="cf5e3-178">Here is an example of a non-pure function because it depends on global, mutable state:</span></span>

```fsharp
let mutable value = 1

let addOneToValue x = x + value
```

<span data-ttu-id="cf5e3-179">`addOneToValue` İşlevi açıkça Hanuka çünkü `value` 1'den farklı bir değere sahip için herhangi bir zamanda değiştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="cf5e3-179">The `addOneToValue` function is clearly impure, because `value` could be changed at any time to have a different value than 1.</span></span> <span data-ttu-id="cf5e3-180">Bu, genel bir değerde bağlı olarak, işlevsel programlama kaçınılması modelidir.</span><span class="sxs-lookup"><span data-stu-id="cf5e3-180">This pattern of depending on a global value is to be avoided in functional programming.</span></span>

<span data-ttu-id="cf5e3-181">Bir yan etkisi gerçekleştirdiğinden, saf olmayan bir işlevin başka bir örnek aşağıdadır:</span><span class="sxs-lookup"><span data-stu-id="cf5e3-181">Here is another example of a non-pure function, because it performs a side effect:</span></span>

```fsharp
let addOneToValue x = 
    printfn "x is %d" x
    x + 1
```

<span data-ttu-id="cf5e3-182">Bu işlev üzerinde genel bir değerde benzemez olsa da, bu değeri Yazar `x` programın çıkışı için.</span><span class="sxs-lookup"><span data-stu-id="cf5e3-182">Although this function does not depend on a global value, it writes the value of `x` to the output of the program.</span></span> <span data-ttu-id="cf5e3-183">Olmasa da Bunun yapılması doğal olarak yanlış bir şey, işlevin saf değil anlamına gelmez.</span><span class="sxs-lookup"><span data-stu-id="cf5e3-183">Although there is nothing inherently wrong with doing this, it does mean that the function is not pure.</span></span>

<span data-ttu-id="cf5e3-184">Kaldırma `printfn` deyimi finally yapar işlevin saf:</span><span class="sxs-lookup"><span data-stu-id="cf5e3-184">Removing the `printfn` statement finally makes the function pure:</span></span>

```fsharp
let addOneToValue x = x + 1
```

<span data-ttu-id="cf5e3-185">Bu işlev bir kendiliğinden olmasa da _daha iyi_ daha önceki sürümüyle `printfn` deyimi, bunu garanti bu işlev yaptığı olduğundan, bir değer döndürür.</span><span class="sxs-lookup"><span data-stu-id="cf5e3-185">Although this function is not inherently _better_ than the previous version with the `printfn` statement, it does guarantee that all this function does is return a value.</span></span> <span data-ttu-id="cf5e3-186">Bunu çağıran bir kez işlev ya da 1 milyardan fazla kez aynı şeyi hala neden olur: yalnızca bir değer üretir.</span><span class="sxs-lookup"><span data-stu-id="cf5e3-186">Calling this function once or 1 billion times will still result in the same thing: just producing a value.</span></span> <span data-ttu-id="cf5e3-187">Bu tahmin edilebilirliğini işlevsel programlama, değerli aynıdır tüm saf işlev referentially saydam olduğu anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="cf5e3-187">This predictability is valuable in functional programming, as it means that any pure function is referentially transparent.</span></span>

### <a name="referential-transparency"></a><span data-ttu-id="cf5e3-188">Başvuru saydamlık</span><span class="sxs-lookup"><span data-stu-id="cf5e3-188">Referential Transparency</span></span>

<span data-ttu-id="cf5e3-189">Başvuru saydamlık, ifadeler ve İşlevler için kullanılan bir özelliktir.</span><span class="sxs-lookup"><span data-stu-id="cf5e3-189">Referential transparency is a property of expressions and functions.</span></span> <span data-ttu-id="cf5e3-190">Bir ifade referentially saydam olacak şekilde, programın davranışını değiştirmeden elde edilen değeriyle değiştirilmesi mümkün olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="cf5e3-190">For an expression to be referentially transparent, it must be able to be replaced with its resulting value without changing the program's behavior.</span></span> <span data-ttu-id="cf5e3-191">Tüm saf işlevler referentially saydamdır.</span><span class="sxs-lookup"><span data-stu-id="cf5e3-191">All pure functions are referentially transparent.</span></span>

<span data-ttu-id="cf5e3-192">Saf işlevler gibi ile başvuru saydamlık matematik açısından düşünmek yararlı olabilir.</span><span class="sxs-lookup"><span data-stu-id="cf5e3-192">As with pure functions, it can be helpful to think of referential transparency from a mathematical perspective.</span></span> <span data-ttu-id="cf5e3-193">Matematik ifadesindeki `y = f(x)`, `f(x)` işlevin sonucu tarafından değiştirilebilir ve yine de eşit olacaktır `y`.</span><span class="sxs-lookup"><span data-stu-id="cf5e3-193">In the mathematical expression `y = f(x)`, `f(x)` can be replaced by the result of the function and it will still be equal to `y`.</span></span> <span data-ttu-id="cf5e3-194">Bu başvuru saydamlık fonksiyonel programlama için eşit oranda geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="cf5e3-194">This is equally true for referential transparency in functional programming.</span></span>

<span data-ttu-id="cf5e3-195">Önceden tanımlanmış çağırmayı düşünün `addOneIfOdd` iki kez çalışması:</span><span class="sxs-lookup"><span data-stu-id="cf5e3-195">Consider calling the previously defined `addOneIfOdd` function twice:</span></span>

```fsharp
// Checks if 'x' is odd by using the mod operator
let isOdd x = x % 2 <> 0

let addOneIfOdd input =
    let result =
        if isOdd input then
            input + 1
        else
            input

    result

let res1 = addOneIffOdd 1 // Produces 2
let res2 = addOneIffOdd 2 // Produces 2
```

<span data-ttu-id="cf5e3-196">Biz bağımsız değişkenini değiştirerek işlev gövdesi ile her işlev çağrısının değiştirebilirsiniz `input` her değeri:</span><span class="sxs-lookup"><span data-stu-id="cf5e3-196">We can replace each function call with the function body, substituting the argument `input` with each value:</span></span>

```fsharp
// Checks if 'x' is odd by using the mod operator
let isOdd x = x % 2 <> 0

let addOneIfOdd input =
    let result =
        if isOdd input then
            input + 1
        else
            input

    result

let res1 =
    let result =
        if isOdd 1 then
            1 + 1
        else
            1

    result
let res2 =
    let result =
        if isOdd 2 then
            2 + 1
        else
            2

    result
```

<span data-ttu-id="cf5e3-197">Her ikisi de `res1` ve `res2` gösteren işlev çağrıldı sanki aynı değere sahip `addOneIfOdd` referentially saydamdır!</span><span class="sxs-lookup"><span data-stu-id="cf5e3-197">Both `res1` and `res2` have the same value as if the function was called, indicating that `addOneIfOdd` is referentially transparent!</span></span>

<span data-ttu-id="cf5e3-198">Ayrıca, bir işlev de referentially saydam olarak saf olmak zorunda değildir.</span><span class="sxs-lookup"><span data-stu-id="cf5e3-198">Additionally, a function doesn't have to be pure to also be referentially transparent.</span></span> <span data-ttu-id="cf5e3-199">Bir önceki tanımını dikkate `addOneTovalue`:</span><span class="sxs-lookup"><span data-stu-id="cf5e3-199">Consider a previous definition of  `addOneTovalue`:</span></span>

```fsharp
let addOneToValue x = 
    printfn "x is %d" x
    x + 1
```

<span data-ttu-id="cf5e3-200">Bu işlev için herhangi bir çağrı, gövdesinde tarafından değiştirilebilir ve her şeyi gerçekleşir:</span><span class="sxs-lookup"><span data-stu-id="cf5e3-200">Any call to this function can also be replaced by its body and the same things will happen each time:</span></span>

* <span data-ttu-id="cf5e3-201">Çıktı, eklenmeden önce değeri yazdırılır</span><span class="sxs-lookup"><span data-stu-id="cf5e3-201">The value, prior to being added to, is printed to the output</span></span>
* <span data-ttu-id="cf5e3-202">Eklenmiş 1 değerine sahip</span><span class="sxs-lookup"><span data-stu-id="cf5e3-202">The value has 1 added to it</span></span>

<span data-ttu-id="cf5e3-203">Programlama yaparken F#, genellikle saflığa yerine hedefi olan başvuru saydamlık olur.</span><span class="sxs-lookup"><span data-stu-id="cf5e3-203">When programming in F#, it is often referential transparency that is the goal, rather than purity.</span></span> <span data-ttu-id="cf5e3-204">Ancak, mümkün olduğunda, saf işlevler yazma yine de iyi bir uygulamadır.</span><span class="sxs-lookup"><span data-stu-id="cf5e3-204">However, it is still good practice to write pure functions when you can.</span></span>

### <a name="immutability"></a><span data-ttu-id="cf5e3-205">Değiştirilemezlik</span><span class="sxs-lookup"><span data-stu-id="cf5e3-205">Immutability</span></span>

<span data-ttu-id="cf5e3-206">Son olarak, en temel kavramlarını yazılmış işlevsel programlama değiştirilemezlik biridir.</span><span class="sxs-lookup"><span data-stu-id="cf5e3-206">Finally, one of the most fundamental concepts of typed functional programming is immutability.</span></span> <span data-ttu-id="cf5e3-207">İçinde F#, varsayılan olarak tüm değerler sabittir.</span><span class="sxs-lookup"><span data-stu-id="cf5e3-207">In F#, all values are immutable by default.</span></span> <span data-ttu-id="cf5e3-208">Bu, açıkça değişebilir olarak işaretlerken sürece yerinde olamaz anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="cf5e3-208">That means they cannot be mutated in-place unless you explicitly mark them as mutable.</span></span>

<span data-ttu-id="cf5e3-209">Uygulamada, değişmez değerleri ile çalışma "Bir şeyle değiştirmek istiyorum," programlamaya yaklaşımınızı değiştirmek, için "yeni bir değer oluşturmak istiyorum" gösterir.</span><span class="sxs-lookup"><span data-stu-id="cf5e3-209">In practice, working with immutable values means that you change your approach to programming from, "I need to change something", to "I need to produce a new value".</span></span>

<span data-ttu-id="cf5e3-210">Örneğin, bir değer eklemeyi 1 var olan bir diziyi değil, yeni bir değer üreten anlamına gelir:</span><span class="sxs-lookup"><span data-stu-id="cf5e3-210">For example, adding 1 to a value means producing a new value, not mutating the existing one:</span></span>

```fsharp
let value = 1
let secondValue = value + 1
```

<span data-ttu-id="cf5e3-211">İçinde F#, aşağıdaki kod mu **değil** bulunmamalıdır `value` işlev; bunun yerine, bunu bir eşitlik denetimi gerçekleştirir:</span><span class="sxs-lookup"><span data-stu-id="cf5e3-211">In F#, the following code does **not** mutate the `value` function; instead, it performs an equality check:</span></span>

```fsharp
let value = 1
value = value + 1 // Produces a 'bool' value!
```

<span data-ttu-id="cf5e3-212">Bazı işlevsel programlama dilleri Mutasyon hiç desteklemez.</span><span class="sxs-lookup"><span data-stu-id="cf5e3-212">Some functional programming languages do not support mutation at all.</span></span> <span data-ttu-id="cf5e3-213">İçinde F#desteklenir, ancak bu değerler için varsayılan davranış değildir.</span><span class="sxs-lookup"><span data-stu-id="cf5e3-213">In F#, it is supported, but it is not the default behavior for values.</span></span>

<span data-ttu-id="cf5e3-214">Bu kavram, hatta veri yapıları daha fazla sınırlandıramazsınız genişletir.</span><span class="sxs-lookup"><span data-stu-id="cf5e3-214">This concept extends even further to data structures.</span></span> <span data-ttu-id="cf5e3-215">Başlangıçta olabilir daha kümeleri (ve çok daha fazlası) farklı bir uygulama gibi işlevsel programlama, sabit veri yapılarını bekler.</span><span class="sxs-lookup"><span data-stu-id="cf5e3-215">In functional programming, immutable data structures such as sets (and many more) have a different implementation than you might initially expect.</span></span> <span data-ttu-id="cf5e3-216">Kavramsal olarak, bir şey bir kümeye bir öğe eklemeye kümesi değişmez gibi ürettiği bir _yeni_ değer ile ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="cf5e3-216">Conceptually, something like adding an item to a set does not change the set, it produces a _new_ set with the added value.</span></span> <span data-ttu-id="cf5e3-217">Arka planda, bu genellikle sağlar ve böylece verilerin uygun gösterimi sonucunda verilebilir verimli bir şekilde bir değer izlemek için farklı veri yapısı tarafından gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="cf5e3-217">Under the covers, this is often accomplished by a different data structure that allows for efficiently tracking a value so that the appropriate representation of the data can be given as a result.</span></span>

<span data-ttu-id="cf5e3-218">Bu şey yeni bir sürümü oluşturursa gibi bir şey değiştirir herhangi bir işlem davranmaya zorlar gibi bu stil, değerleri ve veri yapıları ile çalışma önemlidir.</span><span class="sxs-lookup"><span data-stu-id="cf5e3-218">This style of working with values and data structures is critical, as it forces you to treat any operation that modifies something as if it creates a new version of that thing.</span></span> <span data-ttu-id="cf5e3-219">Bu eşitlik ve comparability gibi şeyleri programlarınızda tutarlı olmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="cf5e3-219">This allows for things like equality and comparability to be consistent in your programs.</span></span>

## <a name="next-steps"></a><span data-ttu-id="cf5e3-220">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="cf5e3-220">Next steps</span></span>

<span data-ttu-id="cf5e3-221">Sonraki bölümde işlevsel programlamaya kullanabileceğiniz farklı yolları keşfetmeye işlevleri, kapsamlı olarak ele alınacaktır.</span><span class="sxs-lookup"><span data-stu-id="cf5e3-221">The next section will thoroughly cover functions, exploring different ways you can use them in functional programming.</span></span>

<span data-ttu-id="cf5e3-222">[Birinci sınıf işlevler](first-class-functions.md) işlevleri çeşitli bağlamlarda bunları kullanabileceğinizi gösteren derin bir şekilde, keşfediyor.</span><span class="sxs-lookup"><span data-stu-id="cf5e3-222">[First-class functions](first-class-functions.md) explores functions deeply, showing how you can use them in various contexts.</span></span>

## <a name="further-reading"></a><span data-ttu-id="cf5e3-223">Daha fazla bilgi</span><span class="sxs-lookup"><span data-stu-id="cf5e3-223">Further reading</span></span>

<span data-ttu-id="cf5e3-224">[İşlevsel olarak düşünmek](https://fsharpforfunandprofit.com/posts/thinking-functionally-intro/) serisi, işlevsel programlama ile ilgili bilgi edinmek için başka bir harika kaynak F#.</span><span class="sxs-lookup"><span data-stu-id="cf5e3-224">The [Thinking Functionally](https://fsharpforfunandprofit.com/posts/thinking-functionally-intro/) series is another great resource to learn about functional programming with F#.</span></span> <span data-ttu-id="cf5e3-225">Pragmatik ve kolay okunur bir biçimde işlevsel programlamanın temellerini kapsayan kullanarak F# kavramları göstermek için özellikleri.</span><span class="sxs-lookup"><span data-stu-id="cf5e3-225">It covers fundamentals of functional programming in a pragmatic and easy-to-read way, using F# features to illustrate the concepts.</span></span>