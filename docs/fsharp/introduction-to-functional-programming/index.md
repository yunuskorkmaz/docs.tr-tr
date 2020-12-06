---
title: 'F # İşlevsel Programlamaya Giriş'
description: "F # ' da işlevsel programlama temellerini öğrenin."
ms.date: 10/29/2018
ms.openlocfilehash: fc2aebe80de16b92942c3557c0e03c198883dde1
ms.sourcegitcommit: ecd9e9bb2225eb76f819722ea8b24988fe46f34c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/05/2020
ms.locfileid: "96740334"
---
# <a name="introduction-to-functional-programming-in-f"></a><span data-ttu-id="99f79-103">F 'de Işlevsel programlamaya giriş\#</span><span class="sxs-lookup"><span data-stu-id="99f79-103">Introduction to Functional Programming in F\#</span></span>

<span data-ttu-id="99f79-104">Fonksiyonel programlama, işlevlerin ve değişmez verilerin kullanımını vurgulayarak programlama stilidir.</span><span class="sxs-lookup"><span data-stu-id="99f79-104">Functional programming is a style of programming that emphasizes the use of functions and immutable data.</span></span> <span data-ttu-id="99f79-105">Yazılan fonksiyonel programlama, fonksiyonel programlamanın, F # gibi statik türlerle birleştirilme biçimdedir.</span><span class="sxs-lookup"><span data-stu-id="99f79-105">Typed functional programming is when functional programming is combined with static types, such as with F#.</span></span> <span data-ttu-id="99f79-106">Genel olarak, aşağıdaki kavramlar işlevsel programlamada vurgulandı:</span><span class="sxs-lookup"><span data-stu-id="99f79-106">In general, the following concepts are emphasized in functional programming:</span></span>

* <span data-ttu-id="99f79-107">Kullandığınız birincil yapılar olarak işlevler</span><span class="sxs-lookup"><span data-stu-id="99f79-107">Functions as the primary constructs you use</span></span>
* <span data-ttu-id="99f79-108">Deyimler yerine ifadeler</span><span class="sxs-lookup"><span data-stu-id="99f79-108">Expressions instead of statements</span></span>
* <span data-ttu-id="99f79-109">Değişkenlerin üzerinde sabit değerler</span><span class="sxs-lookup"><span data-stu-id="99f79-109">Immutable values over variables</span></span>
* <span data-ttu-id="99f79-110">Kesinlik temelli programlama üzerinden bildirim temelli programlama</span><span class="sxs-lookup"><span data-stu-id="99f79-110">Declarative programming over imperative programming</span></span>

<span data-ttu-id="99f79-111">Bu serinin tamamında, F # kullanarak işlevsel programlamada kavramları ve desenleri keşfedebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="99f79-111">Throughout this series, you'll explore concepts and patterns in functional programming using F#.</span></span> <span data-ttu-id="99f79-112">Bu şekilde, bazı F # hakkında bilgi edineceksiniz.</span><span class="sxs-lookup"><span data-stu-id="99f79-112">Along the way, you'll learn some F# too.</span></span>

## <a name="terminology"></a><span data-ttu-id="99f79-113">Terminoloji</span><span class="sxs-lookup"><span data-stu-id="99f79-113">Terminology</span></span>

<span data-ttu-id="99f79-114">Diğer programlama paradigmalarına gibi işlevsel programlama, sonunda öğreneceği bir sözlük ile birlikte gelir.</span><span class="sxs-lookup"><span data-stu-id="99f79-114">Functional programming, like other programming paradigms, comes with a vocabulary that you will eventually need to learn.</span></span> <span data-ttu-id="99f79-115">Aşağıda, her zaman bir süre sonra göreceğiniz bazı yaygın terimler verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="99f79-115">Here are some common terms you'll see all of the time:</span></span>

* <span data-ttu-id="99f79-116">**Function** -bir işlev, bir giriş verildiğinde çıkış oluşturacak bir yapıdır.</span><span class="sxs-lookup"><span data-stu-id="99f79-116">**Function** - A function is a construct that will produce an output when given an input.</span></span> <span data-ttu-id="99f79-117">Daha resmi bir öğeyi bir kümeden başka bir küme ile _eşleştirir_ .</span><span class="sxs-lookup"><span data-stu-id="99f79-117">More formally, it _maps_ an item from one set to another set.</span></span> <span data-ttu-id="99f79-118">Bu formalroni, özellikle veri koleksiyonlarında çalışan işlevler kullanılırken birçok şekilde somut yükseltilmemiş.</span><span class="sxs-lookup"><span data-stu-id="99f79-118">This formalism is lifted into the concrete in many ways, especially when using functions that operate on collections of data.</span></span> <span data-ttu-id="99f79-119">Fonksiyonel programlamada en temel (ve önemli) kavramdır.</span><span class="sxs-lookup"><span data-stu-id="99f79-119">It is the most basic (and important) concept in functional programming.</span></span>
* <span data-ttu-id="99f79-120">**İfade** -bir ifade, bir değer üreten bir kod yapısıdır.</span><span class="sxs-lookup"><span data-stu-id="99f79-120">**Expression** - An expression is a construct in code that produces a value.</span></span> <span data-ttu-id="99f79-121">F # ' da, bu değerin bağlanması veya açıkça yoksayılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="99f79-121">In F#, this value must be bound or explicitly ignored.</span></span> <span data-ttu-id="99f79-122">Bir ifade, bir işlev çağrısıyla daha fazla değiştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="99f79-122">An expression can be trivially replaced by a function call.</span></span>
* <span data-ttu-id="99f79-123">**Purity** Bu, bir işlevin özelliği olan dönüş değeri aynı bağımsız değişkenler için her zaman aynı ve değerlendirmesinin bir yan etkisi yoktur.</span><span class="sxs-lookup"><span data-stu-id="99f79-123">**Purity** - Purity is a property of a function such that its return value is always the same for the same arguments, and that its evaluation has no side effects.</span></span> <span data-ttu-id="99f79-124">Saf işlev tamamen bağımsız değişkenlerine bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="99f79-124">A pure function depends entirely on its arguments.</span></span>
* <span data-ttu-id="99f79-125">**Bilgi saydamlığı** -başvurusal saydamlık, bir programın davranışını etkilemeden kendi çıktılarıyla değiştirilmeleri için ifadelerin bir özelliğidir.</span><span class="sxs-lookup"><span data-stu-id="99f79-125">**Referential Transparency** - Referential Transparency is a property of expressions such that they can be replaced with their output without affecting a program's behavior.</span></span>
* <span data-ttu-id="99f79-126">**Imlebilirlik kullanılabilirliği** -değişiklik, bir değerin yerinde değiştirilememe anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="99f79-126">**Immutability** - Immutability means that a value cannot be changed in-place.</span></span> <span data-ttu-id="99f79-127">Bu, yerinde değişiklik olabilen değişkenlerle aynıdır.</span><span class="sxs-lookup"><span data-stu-id="99f79-127">This is in contrast with variables, which can change in place.</span></span>

## <a name="examples"></a><span data-ttu-id="99f79-128">Örnekler</span><span class="sxs-lookup"><span data-stu-id="99f79-128">Examples</span></span>

<span data-ttu-id="99f79-129">Aşağıdaki örneklerde bu temel kavramlar gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="99f79-129">The following examples demonstrate these core concepts.</span></span>

### <a name="functions"></a><span data-ttu-id="99f79-130">İşlevler</span><span class="sxs-lookup"><span data-stu-id="99f79-130">Functions</span></span>

<span data-ttu-id="99f79-131">Fonksiyonel programlamada en yaygın ve temel yapı işlevdir.</span><span class="sxs-lookup"><span data-stu-id="99f79-131">The most common and fundamental construct in functional programming is the function.</span></span> <span data-ttu-id="99f79-132">İşte 1 tamsayı ekleyen basit bir işlev:</span><span class="sxs-lookup"><span data-stu-id="99f79-132">Here's a simple function that adds 1 to an integer:</span></span>

```fsharp
let addOne x = x + 1
```

<span data-ttu-id="99f79-133">Tür imzası aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="99f79-133">Its type signature is as follows:</span></span>

```fsharp
val addOne: x:int -> int
```

<span data-ttu-id="99f79-134">İmza, " `addOne` adlandırılmış bir adı kabul eder `int` `x` ve bir" oluşturur "olarak okunabilir `int` .</span><span class="sxs-lookup"><span data-stu-id="99f79-134">The signature can be read as, "`addOne` accepts an `int` named `x` and will produce an `int`".</span></span> <span data-ttu-id="99f79-135">Daha resmi olarak, `addOne` tamsayıların kümesinden bir değeri tamsayılar kümesine _eşliyorlar_ .</span><span class="sxs-lookup"><span data-stu-id="99f79-135">More formally, `addOne` is _mapping_ a value from the set of integers to the set of integers.</span></span> <span data-ttu-id="99f79-136">`->`Belirteç bu eşlemeyi belirtir.</span><span class="sxs-lookup"><span data-stu-id="99f79-136">The `->` token signifies this mapping.</span></span> <span data-ttu-id="99f79-137">F # ' da genellikle işlev imzasına bakarak ne yapacaklarınız hakkında bir fikir edinebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="99f79-137">In F#, you can usually look at the function signature to get a sense for what it does.</span></span>

<span data-ttu-id="99f79-138">Bu nedenle imza neden önemlidir?</span><span class="sxs-lookup"><span data-stu-id="99f79-138">So, why is the signature important?</span></span> <span data-ttu-id="99f79-139">Yazılan işlevsel programlamada, bir işlevin uygulanması genellikle gerçek tür imzasına göre daha az önemlidir!</span><span class="sxs-lookup"><span data-stu-id="99f79-139">In typed functional programming, the implementation of a function is often less important than the actual type signature!</span></span> <span data-ttu-id="99f79-140">`addOne`1 değerini bir tamsayıya ekleyen olgu, çalışma zamanında ilgi çekici, ancak bir program oluştururken, kabul ettiği ve döndüren olgu, `int` Bu işlevi gerçekten nasıl kullanacağınızı bildirir.</span><span class="sxs-lookup"><span data-stu-id="99f79-140">The fact that `addOne` adds the value 1 to an integer is interesting at runtime, but when you are constructing a program, the fact that it accepts and returns an `int` is what informs how you will actually use this function.</span></span> <span data-ttu-id="99f79-141">Ayrıca, bu işlevi doğru bir şekilde (tür imzasına göre) kullandığınızda, herhangi bir sorunu tanılamak yalnızca işlevin gövdesinde yapılabilir `addOne` .</span><span class="sxs-lookup"><span data-stu-id="99f79-141">Furthermore, once you use this function correctly (with respect to its type signature), diagnosing any problems can be done only within the body of the `addOne` function.</span></span> <span data-ttu-id="99f79-142">Bu, yazılı işlevsel programlamanın arkasındaki aksaklýmdır.</span><span class="sxs-lookup"><span data-stu-id="99f79-142">This is the impetus behind typed functional programming.</span></span>

### <a name="expressions"></a><span data-ttu-id="99f79-143">İfadeler</span><span class="sxs-lookup"><span data-stu-id="99f79-143">Expressions</span></span>

<span data-ttu-id="99f79-144">İfadeler bir değeri değerlendiren yapılardır.</span><span class="sxs-lookup"><span data-stu-id="99f79-144">Expressions are constructs that evaluate to a value.</span></span> <span data-ttu-id="99f79-145">Bir eylem gerçekleştiren deyimlerin aksine, ifadeler bir değeri geri veren bir eylem gerçekleştirmeye düşünülebilir.</span><span class="sxs-lookup"><span data-stu-id="99f79-145">In contrast to statements, which perform an action, expressions can be thought of performing an action that gives back a value.</span></span> <span data-ttu-id="99f79-146">İfadeler, işlevsel programlamada deyimler için neredeyse her zaman kullanılır.</span><span class="sxs-lookup"><span data-stu-id="99f79-146">Expressions are almost always used in favor of statements in functional programming.</span></span>

<span data-ttu-id="99f79-147">Önceki işlevi göz önünde bulundurun `addOne` .</span><span class="sxs-lookup"><span data-stu-id="99f79-147">Consider the previous function, `addOne`.</span></span> <span data-ttu-id="99f79-148">Gövdesi `addOne` bir ifadedir:</span><span class="sxs-lookup"><span data-stu-id="99f79-148">The body of `addOne` is an expression:</span></span>

```fsharp
// 'x + 1' is an expression!
let addOne x = x + 1
```

<span data-ttu-id="99f79-149">İşlevin sonuç türünü tanımlayan bu ifadenin sonucudur `addOne` .</span><span class="sxs-lookup"><span data-stu-id="99f79-149">It is the result of this expression that defines the result type of the `addOne` function.</span></span> <span data-ttu-id="99f79-150">Örneğin, bu işlevi oluşturan ifade, gibi farklı bir tür olacak şekilde değiştirilebilir `string` :</span><span class="sxs-lookup"><span data-stu-id="99f79-150">For example, the expression that makes up this function could be changed to be a different type, such as a `string`:</span></span>

```fsharp
let addOne x = x.ToString() + "1"
```

<span data-ttu-id="99f79-151">İşlevin imzası artık şu şekilde olur:</span><span class="sxs-lookup"><span data-stu-id="99f79-151">The signature of the function is now:</span></span>

```fsharp
val addOne: x:'a -> string
```

<span data-ttu-id="99f79-152">F # ' deki herhangi bir tür `ToString()` üzerinde çağrılabilecek olduğundan, türü `x` genel yapıldı ( [Otomatik Genelleştirme](../language-reference/generics/automatic-generalization.md)adı verilir) ve sonuç türü bir olur `string` .</span><span class="sxs-lookup"><span data-stu-id="99f79-152">Since any type in F# can have `ToString()` called on it, the type of `x` has been made generic (called [Automatic Generalization](../language-reference/generics/automatic-generalization.md)), and the resultant type is a `string`.</span></span>

<span data-ttu-id="99f79-153">İfadeler yalnızca işlevlerin gövdeleridir.</span><span class="sxs-lookup"><span data-stu-id="99f79-153">Expressions are not just the bodies of functions.</span></span> <span data-ttu-id="99f79-154">Başka bir yerde kullandığınız bir değer üreten deyimleriniz olabilir.</span><span class="sxs-lookup"><span data-stu-id="99f79-154">You can have expressions that produce a value you use elsewhere.</span></span> <span data-ttu-id="99f79-155">Yaygın bir tane şunlardır `if` :</span><span class="sxs-lookup"><span data-stu-id="99f79-155">A common one is `if`:</span></span>

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

<span data-ttu-id="99f79-156">`if`İfade adlı bir değer oluşturur `result` .</span><span class="sxs-lookup"><span data-stu-id="99f79-156">The `if` expression produces a value called `result`.</span></span> <span data-ttu-id="99f79-157">Tamamen yok saymayacağınızı ve `result` `if` ifadeyi işlevin gövdesinde yapmayı unutmayın `addOneIfOdd` .</span><span class="sxs-lookup"><span data-stu-id="99f79-157">Note that you could omit `result` entirely, making the `if` expression the body of the `addOneIfOdd` function.</span></span> <span data-ttu-id="99f79-158">İfadeler hakkında hatırlamanız gereken önemli şey bir değer üretmeleridir.</span><span class="sxs-lookup"><span data-stu-id="99f79-158">The key thing to remember about expressions is that they produce a value.</span></span>

<span data-ttu-id="99f79-159">Döndürülecek bir şey olmadığında kullanılan özel bir tür vardır `unit` .</span><span class="sxs-lookup"><span data-stu-id="99f79-159">There is a special type, `unit`, that is used when there is nothing to return.</span></span> <span data-ttu-id="99f79-160">Örneğin, şu basit işlevi göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="99f79-160">For example, consider this simple function:</span></span>

```fsharp
let printString (str: string) =
    printfn $"String is: {str}"
```

<span data-ttu-id="99f79-161">İmza şöyle görünür:</span><span class="sxs-lookup"><span data-stu-id="99f79-161">The signature looks like this:</span></span>

```fsharp
val printString: str:string -> unit
```

<span data-ttu-id="99f79-162">`unit`Türü, döndürülmekte olan gerçek değer olmadığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="99f79-162">The `unit` type indicates that there is no actual value being returned.</span></span> <span data-ttu-id="99f79-163">Bu, işin sonucu olarak döndürülecek bir değer olmamasına rağmen "iş yap" gerektiren bir yordamınız olduğunda faydalıdır.</span><span class="sxs-lookup"><span data-stu-id="99f79-163">This is useful when you have a routine that must "do work" despite having no value to return as a result of that work.</span></span>

<span data-ttu-id="99f79-164">Bu, eşdeğer `if` yapının bir ifade olduğu ve değer oluşturmanın genellikle değişkenlerle birlikte yapılması gereken, kesin programlamaya yönelik keskin karşıtlığa sahiptir.</span><span class="sxs-lookup"><span data-stu-id="99f79-164">This is in sharp contrast to imperative programming, where the equivalent `if` construct is a statement, and producing values is often done with mutating variables.</span></span> <span data-ttu-id="99f79-165">Örneğin, C# ' de kod şöyle yazılmış olabilir:</span><span class="sxs-lookup"><span data-stu-id="99f79-165">For example, in C#, the code might be written like this:</span></span>

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

<span data-ttu-id="99f79-166">C# ve diğer C stili dillerin, ifade tabanlı koşullu programlamaya izin veren [Üçlü ifadeyi](../../csharp/language-reference/operators/conditional-operator.md)desteklediğini belirtmekte de dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="99f79-166">It's worth noting that C# and other C-style languages do support the [ternary expression](../../csharp/language-reference/operators/conditional-operator.md), which allows for expression-based conditional programming.</span></span>

<span data-ttu-id="99f79-167">Fonksiyonel programlamada, deyimleri olan değerleri bulunmamalıdır olarak ifade edilir.</span><span class="sxs-lookup"><span data-stu-id="99f79-167">In functional programming, it is rare to mutate values with statements.</span></span> <span data-ttu-id="99f79-168">Bazı işlevsel diller deyimleri ve mutasyonlarını desteklese de, bu kavramların işlevsel programlamada kullanılması yaygın değildir.</span><span class="sxs-lookup"><span data-stu-id="99f79-168">Although some functional languages support statements and mutation, it is not common to use these concepts in functional programming.</span></span>

### <a name="pure-functions"></a><span data-ttu-id="99f79-169">Saf işlevler</span><span class="sxs-lookup"><span data-stu-id="99f79-169">Pure functions</span></span>

<span data-ttu-id="99f79-170">Daha önce belirtildiği gibi, saf işlevler şu şekilde çalışır:</span><span class="sxs-lookup"><span data-stu-id="99f79-170">As previously mentioned, pure functions are functions that:</span></span>

* <span data-ttu-id="99f79-171">Aynı giriş için her zaman aynı değere değerlendirin.</span><span class="sxs-lookup"><span data-stu-id="99f79-171">Always evaluate to the same value for the same input.</span></span>
* <span data-ttu-id="99f79-172">Yan etkileri yoktur.</span><span class="sxs-lookup"><span data-stu-id="99f79-172">Have no side effects.</span></span>

<span data-ttu-id="99f79-173">Matematik işlevlerini bu bağlamda düşünmek yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="99f79-173">It is helpful to think of mathematical functions in this context.</span></span> <span data-ttu-id="99f79-174">Matematik olarak işlevler yalnızca bağımsız değişkenlerine bağımlıdır ve herhangi bir yan etkisi yoktur.</span><span class="sxs-lookup"><span data-stu-id="99f79-174">In mathematics, functions depend only on their arguments and do not have any side effects.</span></span> <span data-ttu-id="99f79-175">Matematik işlevinde `f(x) = x + 1` , değeri `f(x)` yalnızca değerine göre değişir `x` .</span><span class="sxs-lookup"><span data-stu-id="99f79-175">In the mathematical function `f(x) = x + 1`, the value of `f(x)` depends only on the value of `x`.</span></span> <span data-ttu-id="99f79-176">İşlevsel programlamada saf işlevler aynı şekilde yapılır.</span><span class="sxs-lookup"><span data-stu-id="99f79-176">Pure functions in functional programming are the same way.</span></span>

<span data-ttu-id="99f79-177">Saf bir işlev yazarken, işlev yalnızca bağımsız değişkenlerine bağlı olmalıdır ve yan etkisi olan herhangi bir eylem gerçekleştirmez.</span><span class="sxs-lookup"><span data-stu-id="99f79-177">When writing a pure function, the function must depend only on its arguments and not perform any action that results in a side effect.</span></span>

<span data-ttu-id="99f79-178">Genel, kesilebilir duruma bağlı olduğundan, saf olmayan bir işleve bir örnek aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="99f79-178">Here is an example of a non-pure function because it depends on global, mutable state:</span></span>

```fsharp
let mutable value = 1

let addOneToValue x = x + value
```

<span data-ttu-id="99f79-179">`addOneToValue`İşlev, `value` herhangi bir zamanda 1 ' den farklı bir değere sahip olacak şekilde değiştirilebildiğinden, açıkça kesin bir şekilde belirlenir.</span><span class="sxs-lookup"><span data-stu-id="99f79-179">The `addOneToValue` function is clearly impure, because `value` could be changed at any time to have a different value than 1.</span></span> <span data-ttu-id="99f79-180">Genel değere bağlı olarak bu düzenin işlevsel programlamada kaçınılmaz.</span><span class="sxs-lookup"><span data-stu-id="99f79-180">This pattern of depending on a global value is to be avoided in functional programming.</span></span>

<span data-ttu-id="99f79-181">Bir yan etkisi gerçekleştirdiğinden, saf olmayan bir işlevin başka bir örneği aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="99f79-181">Here is another example of a non-pure function, because it performs a side effect:</span></span>

```fsharp
let addOneToValue x =
    printfn $"x is %d{x}"
    x + 1
```

<span data-ttu-id="99f79-182">Bu işlev genel bir değere bağımlı olmasa da, değerini `x` programın çıktısına yazar.</span><span class="sxs-lookup"><span data-stu-id="99f79-182">Although this function does not depend on a global value, it writes the value of `x` to the output of the program.</span></span> <span data-ttu-id="99f79-183">Bunu yaparken doğal olarak yanlış bir şey olmasa da, işlevin saf olmadığı anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="99f79-183">Although there is nothing inherently wrong with doing this, it does mean that the function is not pure.</span></span> <span data-ttu-id="99f79-184">Programınızın başka bir bölümü, çıkış arabelleği gibi programa ait bir şeye bağımlıysa, bu işlevi çağırmak programınızın diğer bölümünü etkileyebilir.</span><span class="sxs-lookup"><span data-stu-id="99f79-184">If another part of your program depends on something external to the program, such as the output buffer, then calling this function can affect that other part of your program.</span></span>

<span data-ttu-id="99f79-185">Deyimin kaldırılması `printfn` işlevi saf hale getirir:</span><span class="sxs-lookup"><span data-stu-id="99f79-185">Removing the `printfn` statement makes the function pure:</span></span>

```fsharp
let addOneToValue x = x + 1
```

<span data-ttu-id="99f79-186">Bu işlev doğal olarak önceki sürümden _daha iyi_ olmasa da `printfn` , tüm bu işlevin bir değer döndürdiğinin garantisi vardır.</span><span class="sxs-lookup"><span data-stu-id="99f79-186">Although this function is not inherently _better_ than the previous version with the `printfn` statement, it does guarantee that all this function does is return a value.</span></span> <span data-ttu-id="99f79-187">Bu işlevi çağırmak, herhangi bir sayıda kez aynı sonucu üretir: yalnızca bir değer oluşturur.</span><span class="sxs-lookup"><span data-stu-id="99f79-187">Calling this function any number of times produces the same result: it just produces a value.</span></span> <span data-ttu-id="99f79-188">Öngörüler tarafından verilen öngörülebilirlik, birçok işlevsel programcı için çaba göstermesidir.</span><span class="sxs-lookup"><span data-stu-id="99f79-188">The predictability given by purity is something many functional programmers strive for.</span></span>

### <a name="immutability"></a><span data-ttu-id="99f79-189">Değiştirilemezlik</span><span class="sxs-lookup"><span data-stu-id="99f79-189">Immutability</span></span>

<span data-ttu-id="99f79-190">Son olarak, yazılan fonksiyonel programlama için en temel kavramlardan biri imlebilirlik olarak belirlenir.</span><span class="sxs-lookup"><span data-stu-id="99f79-190">Finally, one of the most fundamental concepts of typed functional programming is immutability.</span></span> <span data-ttu-id="99f79-191">F # ' da, tüm değerler varsayılan olarak sabittir.</span><span class="sxs-lookup"><span data-stu-id="99f79-191">In F#, all values are immutable by default.</span></span> <span data-ttu-id="99f79-192">Diğer bir deyişle, bunları açıkça değişebilir olarak işaretlemediğiniz sürece bu, yerinde değiştirilemez.</span><span class="sxs-lookup"><span data-stu-id="99f79-192">That means they cannot be mutated in-place unless you explicitly mark them as mutable.</span></span>

<span data-ttu-id="99f79-193">Uygulamada, değişmez değerlerle çalışmak, programlama yaklaşımınızı "bir şeyi değiştirmem", "yeni bir değer üretmem gerekiyor" olarak değiştirdiğiniz anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="99f79-193">In practice, working with immutable values means that you change your approach to programming from, "I need to change something", to "I need to produce a new value".</span></span>

<span data-ttu-id="99f79-194">Örneğin, bir değere 1 eklemek, var olan bir değer üretilmeden yeni bir değer üretilmesinin anlamına gelir:</span><span class="sxs-lookup"><span data-stu-id="99f79-194">For example, adding 1 to a value means producing a new value, not mutating the existing one:</span></span>

```fsharp
let value = 1
let secondValue = value + 1
```

<span data-ttu-id="99f79-195">F # ' da, aşağıdaki kod işlevi **göstermez** `value` ; bunun yerine bir eşitlik denetimi gerçekleştirir:</span><span class="sxs-lookup"><span data-stu-id="99f79-195">In F#, the following code does **not** mutate the `value` function; instead, it performs an equality check:</span></span>

```fsharp
let value = 1
value = value + 1 // Produces a 'bool' value!
```

<span data-ttu-id="99f79-196">Bazı işlevsel programlama dilleri hiç birini desteklemez.</span><span class="sxs-lookup"><span data-stu-id="99f79-196">Some functional programming languages do not support mutation at all.</span></span> <span data-ttu-id="99f79-197">F # içinde desteklenir, ancak değerler için varsayılan davranış değildir.</span><span class="sxs-lookup"><span data-stu-id="99f79-197">In F#, it is supported, but it is not the default behavior for values.</span></span>

<span data-ttu-id="99f79-198">Bu kavram, veri yapılarını daha da artırır.</span><span class="sxs-lookup"><span data-stu-id="99f79-198">This concept extends even further to data structures.</span></span> <span data-ttu-id="99f79-199">İşlevsel programlamada, kümeler (ve çok daha fazlası) gibi değişmez veri yapıları, başlangıçta bekleneceğiniz farklı bir uygulamaya sahiptir.</span><span class="sxs-lookup"><span data-stu-id="99f79-199">In functional programming, immutable data structures such as sets (and many more) have a different implementation than you might initially expect.</span></span> <span data-ttu-id="99f79-200">Kavramsal olarak, bir küme için bir öğe eklemeye benzer şekilde küme değişmez; eklenen değere sahip _Yeni_ bir küme oluşturur.</span><span class="sxs-lookup"><span data-stu-id="99f79-200">Conceptually, something like adding an item to a set does not change the set, it produces a _new_ set with the added value.</span></span> <span data-ttu-id="99f79-201">Bu, genellikle bir değeri etkin bir şekilde izlemeye izin veren farklı bir veri yapısı tarafından gerçekleştirilir. böylece, verilerin uygun gösterimi sonuç olarak verilebilir.</span><span class="sxs-lookup"><span data-stu-id="99f79-201">Under the covers, this is often accomplished by a different data structure that allows for efficiently tracking a value so that the appropriate representation of the data can be given as a result.</span></span>

<span data-ttu-id="99f79-202">Değerler ve veri yapıları ile çalışmanın bu stili, bu işlemin yeni bir sürümünü oluşturuyor gibi bir şeyi değiştiren herhangi bir işlemi bildirmeye zorlarsa kritik öneme sahiptir.</span><span class="sxs-lookup"><span data-stu-id="99f79-202">This style of working with values and data structures is critical, as it forces you to treat any operation that modifies something as if it creates a new version of that thing.</span></span> <span data-ttu-id="99f79-203">Bu, eşitlik ve karşılaştırıcı gibi öğelerin programlarınızda tutarlı olmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="99f79-203">This allows for things like equality and comparability to be consistent in your programs.</span></span>

## <a name="next-steps"></a><span data-ttu-id="99f79-204">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="99f79-204">Next steps</span></span>

<span data-ttu-id="99f79-205">Sonraki bölümde işlevleri kapsamlı olarak ele alınmaktadır ve bunları işlevsel programlamada kullanabileceğiniz farklı şekillerde bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="99f79-205">The next section will thoroughly cover functions, exploring different ways you can use them in functional programming.</span></span>

<span data-ttu-id="99f79-206">[Birinci sınıf işlevler](first-class-functions.md) , işlevleri çeşitli bağlamlarda nasıl kullanabileceğinizi gösteren daha derin bir şekilde araştırır.</span><span class="sxs-lookup"><span data-stu-id="99f79-206">[First-class functions](first-class-functions.md) explores functions deeply, showing how you can use them in various contexts.</span></span>

## <a name="further-reading"></a><span data-ttu-id="99f79-207">Daha fazla bilgi</span><span class="sxs-lookup"><span data-stu-id="99f79-207">Further reading</span></span>

<span data-ttu-id="99f79-208">[Düşünce](https://fsharpforfunandprofit.com/posts/thinking-functionally-intro/) işlevi serisi, F # ile işlevsel programlama hakkında bilgi edinmek için harika bir kaynaktır.</span><span class="sxs-lookup"><span data-stu-id="99f79-208">The [Thinking Functionally](https://fsharpforfunandprofit.com/posts/thinking-functionally-intro/) series is another great resource to learn about functional programming with F#.</span></span> <span data-ttu-id="99f79-209">Kavramları göstermek için F # özelliklerini kullanarak, işlevsel programlama temellerini kolay ve kolay okunabilir bir şekilde ele alır.</span><span class="sxs-lookup"><span data-stu-id="99f79-209">It covers fundamentals of functional programming in a pragmatic and easy-to-read way, using F# features to illustrate the concepts.</span></span>
