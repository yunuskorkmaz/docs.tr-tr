---
title: Kod Tırnak İşaretleri
description: 'Programlama yoluyla F # kod ifadeleri oluşturup bunlarla çalışmanıza olanak tanıyan bir dil özelliği olan F # kod teklifleri hakkında bilgi edinin.'
ms.date: 08/13/2020
ms.openlocfilehash: dc37fdbd6cd29e5ee94e5c0186dfe2bfeb666f32
ms.sourcegitcommit: f99115e12a5eb75638abe45072e023a3ce3351ac
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/12/2020
ms.locfileid: "94557200"
---
# <a name="code-quotations"></a><span data-ttu-id="fa833-103">Kod teklifleri</span><span class="sxs-lookup"><span data-stu-id="fa833-103">Code quotations</span></span>

<span data-ttu-id="fa833-104">Bu makalede, programlama yoluyla F # kod ifadelerini oluşturup birlikte çalışmanıza olanak tanıyan bir dil özelliği olan *kod teklifleri* açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="fa833-104">This article describes *code quotations* , a language feature that enables you to generate and work with F# code expressions programmatically.</span></span> <span data-ttu-id="fa833-105">Bu özellik, F # kodunu temsil eden bir soyut sözdizimi ağacı oluşturmanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="fa833-105">This feature lets you generate an abstract syntax tree that represents F# code.</span></span> <span data-ttu-id="fa833-106">Soyut sözdizimi ağacı, uygulamanızın gereksinimlerine göre çapraz ve işlenebilir.</span><span class="sxs-lookup"><span data-stu-id="fa833-106">The abstract syntax tree can then be traversed and processed according to the needs of your application.</span></span> <span data-ttu-id="fa833-107">Örneğin, ağacı kullanarak F # kodu oluşturabilir veya başka bir dilde kod oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fa833-107">For example, you can use the tree to generate F# code or generate code in some other language.</span></span>

## <a name="quoted-expressions"></a><span data-ttu-id="fa833-108">Tırnak işareti Ifadesi</span><span class="sxs-lookup"><span data-stu-id="fa833-108">Quoted Expressions</span></span>

<span data-ttu-id="fa833-109">*Tırnak içine alınmış bir ifade* , kodunuzda, programınızın bir parçası olarak derlenmediği, ancak bunun yerine bir f # ifadesini temsil eden bir nesneye derlenen bir f # deyimidir.</span><span class="sxs-lookup"><span data-stu-id="fa833-109">A *quoted expression* is an F# expression in your code that is delimited in such a way that it is not compiled as part of your program, but instead is compiled into an object that represents an F# expression.</span></span> <span data-ttu-id="fa833-110">Tırnak içine alınmış bir ifadeyi iki şekilde işaretleyebilirsiniz: tür bilgisi veya tür bilgisi olmadan.</span><span class="sxs-lookup"><span data-stu-id="fa833-110">You can mark a quoted expression in one of two ways: either with type information or without type information.</span></span> <span data-ttu-id="fa833-111">Tür bilgilerini eklemek istiyorsanız, sembolleri kullanır `<@` ve `@>` tırnak içine alınmış ifadeyi sınırlandırın.</span><span class="sxs-lookup"><span data-stu-id="fa833-111">If you want to include type information, you use the symbols `<@` and `@>` to delimit the quoted expression.</span></span> <span data-ttu-id="fa833-112">Tür bilgilerine ihtiyacınız yoksa, ve simgelerini kullanırsınız `<@@` `@@>` .</span><span class="sxs-lookup"><span data-stu-id="fa833-112">If you do not need type information, you use the symbols `<@@` and `@@>`.</span></span> <span data-ttu-id="fa833-113">Aşağıdaki kod, yazılan ve türsüz teklifleri gösterir.</span><span class="sxs-lookup"><span data-stu-id="fa833-113">The following code shows typed and untyped quotations.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-3/snippet501.fs)]

<span data-ttu-id="fa833-114">Tür bilgilerini eklemezseniz büyük bir ifade ağacına geçiş yapmak daha hızlıdır.</span><span class="sxs-lookup"><span data-stu-id="fa833-114">Traversing a large expression tree is faster if you do not include type information.</span></span> <span data-ttu-id="fa833-115">Türü belirlenmiş simgelerle tırnak içine alınmış bir ifadenin sonuç türü, `Expr<'T>` tür parametresinin F # derleyicisinin tür çıkarımı algoritması tarafından belirlendiği şekilde ifadenin türüne sahip olduğu yerdir.</span><span class="sxs-lookup"><span data-stu-id="fa833-115">The resulting type of an expression quoted with the typed symbols is `Expr<'T>`, where the type parameter has the type of the expression as determined by the F# compiler's type inference algorithm.</span></span> <span data-ttu-id="fa833-116">Kod tekliflerini tür bilgisi olmadan kullandığınızda, tırnak [işareti türü genel olmayan ifadedir.](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-quotations-fsharpexpr.html)</span><span class="sxs-lookup"><span data-stu-id="fa833-116">When you use code quotations without type information, the type of the quoted expression is the non-generic type [Expr](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-quotations-fsharpexpr.html).</span></span> <span data-ttu-id="fa833-117">[Raw](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-quotations-fsharpexpr-1.html#Raw) `Expr` Türsüz nesneyi elde etmek için, yazılan sınıfta ham özelliğini çağırabilirsiniz `Expr` .</span><span class="sxs-lookup"><span data-stu-id="fa833-117">You can call the [Raw](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-quotations-fsharpexpr-1.html#Raw) property on the typed `Expr` class to obtain the untyped `Expr` object.</span></span>

<span data-ttu-id="fa833-118">Tırnak içine alınmış ifadeler kullanmadan, sınıfında programlama yoluyla F # ifade nesneleri oluşturmanıza izin veren çeşitli statik yöntemler vardır `Expr` .</span><span class="sxs-lookup"><span data-stu-id="fa833-118">There are a variety of static methods that allow you to generate F# expression objects programmatically in the `Expr` class without using quoted expressions.</span></span>

<span data-ttu-id="fa833-119">Bir kod teklifinin bir bütün ifadeyi içermesi gerektiğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="fa833-119">Note that a code quotation must include a complete expression.</span></span> <span data-ttu-id="fa833-120">`let`Örneğin, bir bağlama için, hem ilişkili ad tanımının hem de bağlamayı kullanan ek bir ifadenin olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="fa833-120">For a `let` binding, for example, you need both the definition of the bound name and an additional expression that uses the binding.</span></span> <span data-ttu-id="fa833-121">Ayrıntılı söz diziminde, bu anahtar sözcüğünü izleyen bir ifadedir `in` .</span><span class="sxs-lookup"><span data-stu-id="fa833-121">In verbose syntax, this is an expression that follows the `in` keyword.</span></span> <span data-ttu-id="fa833-122">Modüldeki en üst düzey bu, modüldeki yalnızca bir sonraki ifadedir, ancak bir teklifte, açıkça gereklidir.</span><span class="sxs-lookup"><span data-stu-id="fa833-122">At the top-level in a module, this is just the next expression in the module, but in a quotation, it is explicitly required.</span></span>

<span data-ttu-id="fa833-123">Bu nedenle, aşağıdaki ifade geçerli değildir.</span><span class="sxs-lookup"><span data-stu-id="fa833-123">Therefore, the following expression is not valid.</span></span>

```fsharp
// Not valid:
// <@ let f x = x + 1 @>
```

<span data-ttu-id="fa833-124">Ancak aşağıdaki ifadeler geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="fa833-124">But the following expressions are valid.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-3/snippet502.fs)]

<span data-ttu-id="fa833-125">F # tekliflerini değerlendirmek için [f # teklif Değerlendiricisi](https://github.com/fsprojects/FSharp.Quotations.Evaluator)kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="fa833-125">To evaluate F# quotations, you must use the [F# Quotation Evaluator](https://github.com/fsprojects/FSharp.Quotations.Evaluator).</span></span> <span data-ttu-id="fa833-126">F # ifade nesnelerini değerlendirmek ve yürütmek için destek sağlar.</span><span class="sxs-lookup"><span data-stu-id="fa833-126">It provides support for evaluating and executing F# expression objects.</span></span>

<span data-ttu-id="fa833-127">F # teklifleri de tür kısıtlaması bilgilerini korur.</span><span class="sxs-lookup"><span data-stu-id="fa833-127">F# quotations also retain type constraint information.</span></span> <span data-ttu-id="fa833-128">Aşağıdaki örneği inceleyin:</span><span class="sxs-lookup"><span data-stu-id="fa833-128">Consider the following example:</span></span>

```fsharp
open FSharp.Linq.RuntimeHelpers

let eval q = LeafExpressionConverter.EvaluateQuotation q

let inline negate x = -x
// val inline negate: x: ^a ->  ^a when  ^a : (static member ( ~- ) :  ^a ->  ^a)

<@ negate 1.0 @>  |> eval
```

<span data-ttu-id="fa833-129">İşlev tarafından oluşturulan kısıtlama `inline` , kod kullanımı içinde tutulur.</span><span class="sxs-lookup"><span data-stu-id="fa833-129">The constraint generated by the `inline` function is retained in the code qutoation.</span></span> <span data-ttu-id="fa833-130">`negate`İşlevin alıntı yapılabilir formu artık değerlendirilebilirler.</span><span class="sxs-lookup"><span data-stu-id="fa833-130">The `negate` function's quotated form can now be evaluated.</span></span>

## <a name="expr-type"></a><span data-ttu-id="fa833-131">Expr türü</span><span class="sxs-lookup"><span data-stu-id="fa833-131">Expr Type</span></span>

<span data-ttu-id="fa833-132">Türün bir örneği `Expr` bir F # ifadesini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="fa833-132">An instance of the `Expr` type represents an F# expression.</span></span> <span data-ttu-id="fa833-133">Hem genel hem de genel olmayan `Expr` türler F # kitaplığı belgelerinde belgelenmiştir.</span><span class="sxs-lookup"><span data-stu-id="fa833-133">Both the generic and the non-generic `Expr` types are documented in the F# library documentation.</span></span> <span data-ttu-id="fa833-134">Daha fazla bilgi için bkz. [FSharp. Quotations ad alanı](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-quotations.html) ve [Quotations. Expr sınıfı](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-quotations-fsharpexpr.html).</span><span class="sxs-lookup"><span data-stu-id="fa833-134">For more information, see [FSharp.Quotations Namespace](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-quotations.html) and [Quotations.Expr Class](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-quotations-fsharpexpr.html).</span></span>

## <a name="splicing-operators"></a><span data-ttu-id="fa833-135">Splicing Işleçleri</span><span class="sxs-lookup"><span data-stu-id="fa833-135">Splicing Operators</span></span>

<span data-ttu-id="fa833-136">Splicing, sabit kod tekliflerini programlı bir şekilde veya başka bir kod teklifinden oluşturduğunuz ifadelerle birleştirmenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="fa833-136">Splicing enables you to combine literal code quotations with expressions that you have created programmatically or from another code quotation.</span></span> <span data-ttu-id="fa833-137">`%`Ve `%%` işleçleri, bir kod teklifine bir F # ifade nesnesi eklemenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="fa833-137">The `%` and `%%` operators enable you to add an F# expression object into a code quotation.</span></span> <span data-ttu-id="fa833-138">Türü belirlenmiş bir `%` teklife yazılmış bir ifade nesnesi eklemek için işlecini kullanırsınız; türsüz bir `%%` ifade nesnesini türsüz bir teklife eklemek için işlecini kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="fa833-138">You use the `%` operator to insert a typed expression object into a typed quotation; you use the `%%` operator to insert an untyped expression object into an untyped quotation.</span></span> <span data-ttu-id="fa833-139">Her iki işleç de birli önek işleçleridir.</span><span class="sxs-lookup"><span data-stu-id="fa833-139">Both operators are unary prefix operators.</span></span> <span data-ttu-id="fa833-140">Bu nedenle `expr` , türünde türsüz bir ifade varsa `Expr` , aşağıdaki kod geçerli olur.</span><span class="sxs-lookup"><span data-stu-id="fa833-140">Thus if `expr` is an untyped expression of type `Expr`, the following code is valid.</span></span>

```fsharp
<@@ 1 + %%expr @@>
```

<span data-ttu-id="fa833-141">`expr`Türü belirlenmiş bir tırnak ise `Expr<int>` , aşağıdaki kod geçerli olur.</span><span class="sxs-lookup"><span data-stu-id="fa833-141">And if `expr` is a typed quotation of type `Expr<int>`, the following code is valid.</span></span>

```fsharp
<@ 1 + %expr @>
```

## <a name="example"></a><span data-ttu-id="fa833-142">Örnek</span><span class="sxs-lookup"><span data-stu-id="fa833-142">Example</span></span>

### <a name="description"></a><span data-ttu-id="fa833-143">Description</span><span class="sxs-lookup"><span data-stu-id="fa833-143">Description</span></span>

<span data-ttu-id="fa833-144">Aşağıdaki örnek, F # kodunu bir ifade nesnesine koymak için kod tekliflerinin kullanımını gösterir ve ardından ifadeyi temsil eden F # kodunu yazdırır.</span><span class="sxs-lookup"><span data-stu-id="fa833-144">The following example illustrates the use of code quotations to put F# code into an expression object and then print the F# code that represents the expression.</span></span> <span data-ttu-id="fa833-145">Kolay bir `println` `print` biçimde bir F # ifade nesnesi (türünde) görüntüleyen özyinelemeli bir işlev içeren bir işlev tanımlanmıştır `Expr` .</span><span class="sxs-lookup"><span data-stu-id="fa833-145">A function `println` is defined that contains a recursive function `print` that displays an F# expression object (of type `Expr`) in a friendly format.</span></span> <span data-ttu-id="fa833-146">[FSharp. Quotations. Patterns](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-quotations-patternsmodule.html) ve [FSharp. Quotations. DerivedPatterns](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-quotations-derivedpatternsmodule.html) modüllerinde ifade nesnelerini çözümlemek için kullanılabilen çeşitli etkin desenler vardır.</span><span class="sxs-lookup"><span data-stu-id="fa833-146">There are several active patterns in the [FSharp.Quotations.Patterns](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-quotations-patternsmodule.html) and [FSharp.Quotations.DerivedPatterns](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-quotations-derivedpatternsmodule.html) modules that can be used to analyze expression objects.</span></span> <span data-ttu-id="fa833-147">Bu örnek, bir F # ifadesinde görünebilen tüm olası desenleri içermez.</span><span class="sxs-lookup"><span data-stu-id="fa833-147">This example does not include all the possible patterns that might appear in an F# expression.</span></span> <span data-ttu-id="fa833-148">Tüm tanınmayan desenler joker karakter düzeniyle () bir eşleşme `_` tetikleyip, türü kullanılarak işlenir ve `ToString` Bu da tür üzerinde, `Expr` eşleştirme ifadenizde eklemek üzere etkin olan kalıbı bilmenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="fa833-148">Any unrecognized pattern triggers a match to the wildcard pattern (`_`) and is rendered by using the `ToString` method, which, on the `Expr` type, lets you know the active pattern to add to your match expression.</span></span>

### <a name="code"></a><span data-ttu-id="fa833-149">Kod</span><span class="sxs-lookup"><span data-stu-id="fa833-149">Code</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-3/snippet601.fs)]

### <a name="output"></a><span data-ttu-id="fa833-150">Çıkış</span><span class="sxs-lookup"><span data-stu-id="fa833-150">Output</span></span>

```fsharp
fun (x:System.Int32) -> x + 1
a + 1
let f = fun (x:System.Int32) -> x + 10 in f 10
```

## <a name="example"></a><span data-ttu-id="fa833-151">Örnek</span><span class="sxs-lookup"><span data-stu-id="fa833-151">Example</span></span>

### <a name="description"></a><span data-ttu-id="fa833-152">Description</span><span class="sxs-lookup"><span data-stu-id="fa833-152">Description</span></span>

<span data-ttu-id="fa833-153">Ayrıca, daha az etkin desenle ifade ağaçlarına çapraz geçiş yapmak için [ExprShape modülünde](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-quotations-exprshapemodule.html) üç etkin deseni de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fa833-153">You can also use the three active patterns in the [ExprShape module](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-quotations-exprshapemodule.html) to traverse expression trees with fewer active patterns.</span></span> <span data-ttu-id="fa833-154">Bu etkin desenler, bir ağaca geçiş yapmak istediğinizde yararlı olabilir ancak düğümlerin çoğunda tüm bilgilere ihtiyacınız yoktur.</span><span class="sxs-lookup"><span data-stu-id="fa833-154">These active patterns can be useful when you want to traverse a tree but you do not need all the information in most of the nodes.</span></span> <span data-ttu-id="fa833-155">Bu desenleri kullandığınızda herhangi bir F # ifadesi şu üç desenden biriyle eşleşir: `ShapeVar` ifade bir değişkense, `ShapeLambda` ifade bir lambda ifadesiyse veya `ShapeCombination` ifade başka bir şeydir.</span><span class="sxs-lookup"><span data-stu-id="fa833-155">When you use these patterns, any F# expression matches one of the following three patterns: `ShapeVar` if the expression is a variable, `ShapeLambda` if the expression is a lambda expression, or `ShapeCombination` if the expression is anything else.</span></span> <span data-ttu-id="fa833-156">Önceki kod örneğinde olduğu gibi etkin desenleri kullanarak bir ifade ağacında çapraz geçiş yaparsanız, tüm olası F # ifade türlerini işlemek için çok daha fazla desen kullanmanız gerekir ve kodunuz daha karmaşık olacaktır.</span><span class="sxs-lookup"><span data-stu-id="fa833-156">If you traverse an expression tree by using the active patterns as in the previous code example, you have to use many more patterns to handle all possible F# expression types, and your code will be more complex.</span></span> <span data-ttu-id="fa833-157">Daha fazla bilgi için bkz. [ExprShape. ShapeVar&#124;ShapeLambda&#124;Shapekombinasyon etkin model](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-quotations-exprshapemodule.html#(%20|ShapeVar|ShapeLambda|ShapeCombination|%20)).</span><span class="sxs-lookup"><span data-stu-id="fa833-157">For more information, see [ExprShape.ShapeVar&#124;ShapeLambda&#124;ShapeCombination Active Pattern](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-quotations-exprshapemodule.html#(%20|ShapeVar|ShapeLambda|ShapeCombination|%20)).</span></span>

<span data-ttu-id="fa833-158">Aşağıdaki kod örneği, daha karmaşık traversals için temel olarak kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="fa833-158">The following code example can be used as a basis for more complex traversals.</span></span> <span data-ttu-id="fa833-159">Bu kodda, bir işlev çağrısını içeren bir ifade için bir ifade ağacı oluşturulur `add` .</span><span class="sxs-lookup"><span data-stu-id="fa833-159">In this code, an expression tree is created for an expression that involves a function call, `add`.</span></span> <span data-ttu-id="fa833-160">İfade ağacında yapılan herhangi bir çağrıyı algılamak için [SpecificCall](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-quotations-derivedpatternsmodule.html#(%20|SpecificCall|_|%20)) etkin deseninin kullanılması `add` .</span><span class="sxs-lookup"><span data-stu-id="fa833-160">The [SpecificCall](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-quotations-derivedpatternsmodule.html#(%20|SpecificCall|_|%20)) active pattern is used to detect any call to `add` in the expression tree.</span></span> <span data-ttu-id="fa833-161">Bu etkin model, çağrının bağımsız değişkenlerini `exprList` değerine atar.</span><span class="sxs-lookup"><span data-stu-id="fa833-161">This active pattern assigns the arguments of the call to the `exprList` value.</span></span> <span data-ttu-id="fa833-162">Bu durumda, yalnızca ikisi vardır, bu nedenle bunlar kullanıma alınır ve işlev bağımsız değişkenlerde yinelemeli olarak çağırılır.</span><span class="sxs-lookup"><span data-stu-id="fa833-162">In this case, there are only two, so these are pulled out and the function is called recursively on the arguments.</span></span> <span data-ttu-id="fa833-163">Sonuçlar, `mul` splice işleci () kullanılarak yapılan çağrıyı temsil eden bir kod teklifine eklenir `%%` .</span><span class="sxs-lookup"><span data-stu-id="fa833-163">The results are inserted into a code quotation that represents a call to `mul` by using the splice operator (`%%`).</span></span> <span data-ttu-id="fa833-164">`println`Önceki örnekteki işlev, sonuçları göstermek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="fa833-164">The `println` function from the previous example is used to display the results.</span></span>

<span data-ttu-id="fa833-165">Diğer etkin model dallarındaki kod yalnızca aynı ifade ağacını yeniden oluşturur, bu nedenle sonuç ifadesindeki tek değişiklik, ' dan ' a değişir `add` `mul` .</span><span class="sxs-lookup"><span data-stu-id="fa833-165">The code in the other active pattern branches just regenerates the same expression tree, so the only change in the resulting expression is the change from `add` to `mul`.</span></span>

### <a name="code"></a><span data-ttu-id="fa833-166">Kod</span><span class="sxs-lookup"><span data-stu-id="fa833-166">Code</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-3/snippet701.fs)]

### <a name="output"></a><span data-ttu-id="fa833-167">Çıkış</span><span class="sxs-lookup"><span data-stu-id="fa833-167">Output</span></span>

```fsharp
1 + Module1.add(2,Module1.add(3,4))
1 + Module1.mul(2,Module1.mul(3,4))
```

## <a name="see-also"></a><span data-ttu-id="fa833-168">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fa833-168">See also</span></span>

- [<span data-ttu-id="fa833-169">F # dil başvurusu</span><span class="sxs-lookup"><span data-stu-id="fa833-169">F# Language Reference</span></span>](index.md)
