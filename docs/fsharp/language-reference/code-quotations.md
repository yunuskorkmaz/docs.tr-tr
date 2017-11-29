---
title: "Kod Tırnak İşaretleri (F#)"
description: "F # kod teklifleri hakkında oluşturmak ve F # kodu ifadelerle programlı olarak çalışmanıza olanak sağlayan bir dil özellik öğrenin."
keywords: "Visual f #, f # işlevsel programlama"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 4559e659-2b04-48bd-8a0b-8527920eec95
ms.openlocfilehash: f7a08013bc6487b570a62576bb01ca2dd65ce8b1
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="code-quotations"></a><span data-ttu-id="25216-104">Kod Tırnak İşaretleri</span><span class="sxs-lookup"><span data-stu-id="25216-104">Code Quotations</span></span>

> [!NOTE]
<span data-ttu-id="25216-105">API başvuru bağlantısı sizi MSDN'ye götürür.</span><span class="sxs-lookup"><span data-stu-id="25216-105">The API reference link will take you to MSDN.</span></span>  <span data-ttu-id="25216-106">Docs.microsoft.com API Başvurusu tamamlanmadı.</span><span class="sxs-lookup"><span data-stu-id="25216-106">The docs.microsoft.com API reference is not complete.</span></span>

<span data-ttu-id="25216-107">Bu konuda açıklanmaktadır *kod tırnak işaretleri*, oluşturmak ve F # kodu ifadelerle programlı olarak çalışmanıza olanak sağlayan bir dil özellik.</span><span class="sxs-lookup"><span data-stu-id="25216-107">This topic describes *code quotations*, a language feature that enables you to generate and work with F# code expressions programmatically.</span></span> <span data-ttu-id="25216-108">Bu özellik F # kodunu temsil eden bir soyut söz dizimi ağaç oluşturmanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="25216-108">This feature lets you generate an abstract syntax tree that represents F# code.</span></span> <span data-ttu-id="25216-109">Soyut söz dizimi ağaç geçiş ve uygulamanızın gereksinimlerine göre işlenir.</span><span class="sxs-lookup"><span data-stu-id="25216-109">The abstract syntax tree can then be traversed and processed according to the needs of your application.</span></span> <span data-ttu-id="25216-110">Örneğin, F # kodu oluşturmak veya başka bir dilde içinde kodu oluşturmak için ağaç kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="25216-110">For example, you can use the tree to generate F# code or generate code in some other language.</span></span>


## <a name="quoted-expressions"></a><span data-ttu-id="25216-111">Tırnak işaretli ifadeleri</span><span class="sxs-lookup"><span data-stu-id="25216-111">Quoted Expressions</span></span>
<span data-ttu-id="25216-112">A *ifade tırnak içine alınmış* kodunuzda bu programınızı bir parçası olarak derlenmemiş olduğunu şekilde ayrılmış, ancak bunun yerine bir F # ifade temsil eden bir nesneye derlenmiş F # ifade.</span><span class="sxs-lookup"><span data-stu-id="25216-112">A *quoted expression* is an F# expression in your code that is delimited in such a way that it is not compiled as part of your program, but instead is compiled into an object that represents an F# expression.</span></span> <span data-ttu-id="25216-113">Tırnak içine alınmış bir ifade iki yoldan biriyle işaretleyebilirsiniz: türü bilgilerle veya tür bilgileri olmadan.</span><span class="sxs-lookup"><span data-stu-id="25216-113">You can mark a quoted expression in one of two ways: either with type information or without type information.</span></span> <span data-ttu-id="25216-114">Tür bilgileri dahil etmek istiyorsanız, simgeleri kullanın `<@` ve `@>` tırnak işaretli ifade sınırlandırmak için.</span><span class="sxs-lookup"><span data-stu-id="25216-114">If you want to include type information, you use the symbols `<@` and `@>` to delimit the quoted expression.</span></span> <span data-ttu-id="25216-115">Tür bilgileri gerekmiyorsa simgeleri kullanın `<@@` ve `@@>`.</span><span class="sxs-lookup"><span data-stu-id="25216-115">If you do not need type information, you use the symbols `<@@` and `@@>`.</span></span> <span data-ttu-id="25216-116">Aşağıdaki kod yazılan ve türsüz teklifleri gösterir.</span><span class="sxs-lookup"><span data-stu-id="25216-116">The following code shows typed and untyped quotations.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-3/snippet501.fs)]

<span data-ttu-id="25216-117">Büyük ifade ağacına geçiş türü bilgileri eklemezseniz hızlıdır.</span><span class="sxs-lookup"><span data-stu-id="25216-117">Traversing a large expression tree is faster if you do not include type information.</span></span> <span data-ttu-id="25216-118">Yazılı sembolleriyle tırnak içine alınmış bir ifade sonuç türü `Expr<'T>`, burada tür parametresi F # derleyicinin türü çıkarımı algoritması tarafından belirlenen ifade türü.</span><span class="sxs-lookup"><span data-stu-id="25216-118">The resulting type of an expression quoted with the typed symbols is `Expr<'T>`, where the type parameter has the type of the expression as determined by the F# compiler's type inference algorithm.</span></span> <span data-ttu-id="25216-119">Kod tırnak işaretleri türü bilgileri olmadan kullandığınızda, teklif edilen ifadenin genel olmayan tür türüdür [Expr](https://msdn.microsoft.com/library/ed6a2caf-69d4-45c2-ab97-e9b3be9bce65).</span><span class="sxs-lookup"><span data-stu-id="25216-119">When you use code quotations without type information, the type of the quoted expression is the non-generic type [Expr](https://msdn.microsoft.com/library/ed6a2caf-69d4-45c2-ab97-e9b3be9bce65).</span></span> <span data-ttu-id="25216-120">Çağırabilirsiniz [Raw](https://msdn.microsoft.com/library/47fb94f1-e77f-4c68-aabc-2b0ba40d59c2) özelliği belirtilmiş `Expr` türsüz elde etmek için sınıf `Expr` nesnesi.</span><span class="sxs-lookup"><span data-stu-id="25216-120">You can call the [Raw](https://msdn.microsoft.com/library/47fb94f1-e77f-4c68-aabc-2b0ba40d59c2) property on the typed `Expr` class to obtain the untyped `Expr` object.</span></span>

<span data-ttu-id="25216-121">Çeşitli F # ifade nesnelerini program aracılığıyla da oluşturmak izin statik yöntemler vardır `Expr` kullanmadan sınıfı, ifadeleri tırnak içine alınmış.</span><span class="sxs-lookup"><span data-stu-id="25216-121">There are a variety of static methods that allow you to generate F# expression objects programmatically in the `Expr` class without using quoted expressions.</span></span>

<span data-ttu-id="25216-122">Kod tırnak tam bir ifade içermelidir unutmayın.</span><span class="sxs-lookup"><span data-stu-id="25216-122">Note that a code quotation must include a complete expression.</span></span> <span data-ttu-id="25216-123">İçin bir `let` bağlama, örneğin, tanımı ilişkili adı ve bağlama kullanan bir ek ifade gerekir.</span><span class="sxs-lookup"><span data-stu-id="25216-123">For a `let` binding, for example, you need both the definition of the bound name and an additional expression that uses the binding.</span></span> <span data-ttu-id="25216-124">Ayrıntılı sözdizimi bu izleyen bir ifadesidir `in` anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="25216-124">In verbose syntax, this is an expression that follows the `in` keyword.</span></span> <span data-ttu-id="25216-125">Üst düzey bir modüldeki modülü yalnızca sonraki ifadesinde budur ancak bir teklife, açıkça gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="25216-125">At the top-level in a module, this is just the next expression in the module, but in a quotation, it is explicitly required.</span></span>

<span data-ttu-id="25216-126">Bu nedenle, aşağıdaki ifade geçerli değil.</span><span class="sxs-lookup"><span data-stu-id="25216-126">Therefore, the following expression is not valid.</span></span>

```fsharp
// Not valid:
// <@ let f x = x + 1 @>
```

<span data-ttu-id="25216-127">Ancak aşağıdaki ifadeler geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="25216-127">But the following expressions are valid.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-3/snippet502.fs)]

<span data-ttu-id="25216-128">Kod tırnak işaretleri kullanmak için bir içeri aktarma bildirimi ekleyin (kullanarak `open` anahtar sözcüğü) açılır [Microsoft.FSharp.Quotations](https://msdn.microsoft.com/library/e9ce8a3a-e00c-4190-bad5-cce52ee089b2) ad alanı.</span><span class="sxs-lookup"><span data-stu-id="25216-128">To use code quotations, you must add an import declaration (by using the `open` keyword) that opens the [Microsoft.FSharp.Quotations](https://msdn.microsoft.com/library/e9ce8a3a-e00c-4190-bad5-cce52ee089b2) namespace.</span></span>

<span data-ttu-id="25216-129">F # PowerPack değerlendirmek ve F # ifade nesnelerini çalıştırmak için destek sağlar.</span><span class="sxs-lookup"><span data-stu-id="25216-129">The F# PowerPack provides support for evaluating and executing F# expression objects.</span></span>


## <a name="expr-type"></a><span data-ttu-id="25216-130">İfade türü</span><span class="sxs-lookup"><span data-stu-id="25216-130">Expr Type</span></span>
<span data-ttu-id="25216-131">Örneği `Expr` türünü F # ifade temsil eder.</span><span class="sxs-lookup"><span data-stu-id="25216-131">An instance of the `Expr` type represents an F# expression.</span></span> <span data-ttu-id="25216-132">Hem genel hem de genel olmayan `Expr` türleri, F # kitaplığı belgelerinde belgelenmiştir.</span><span class="sxs-lookup"><span data-stu-id="25216-132">Both the generic and the non-generic `Expr` types are documented in the F# library documentation.</span></span> <span data-ttu-id="25216-133">Daha fazla bilgi için bkz: [Microsoft.FSharp.Quotations Namespace](https://msdn.microsoft.com/visualfsharpdocs/conceptual/microsoft.fsharp.quotations-namespace-%5bfsharp%5d) ve [Quotations.Expr sınıfı](https://msdn.microsoft.com/visualfsharpdocs/conceptual/quotations.expr-class-%5bfsharp%5d).</span><span class="sxs-lookup"><span data-stu-id="25216-133">For more information, see [Microsoft.FSharp.Quotations Namespace](https://msdn.microsoft.com/visualfsharpdocs/conceptual/microsoft.fsharp.quotations-namespace-%5bfsharp%5d) and [Quotations.Expr Class](https://msdn.microsoft.com/visualfsharpdocs/conceptual/quotations.expr-class-%5bfsharp%5d).</span></span>


## <a name="splicing-operators"></a><span data-ttu-id="25216-134">Boşluklarına ayıran işleçleri</span><span class="sxs-lookup"><span data-stu-id="25216-134">Splicing Operators</span></span>
<span data-ttu-id="25216-135">Boşluklarına ayıran değişmez değer kod tırnak işaretleri programlı olarak veya başka bir kod tırnak oluşturulan ifadelerle birleştirmek etkinleştirir.</span><span class="sxs-lookup"><span data-stu-id="25216-135">Splicing enables you to combine literal code quotations with expressions that you have created programmatically or from another code quotation.</span></span> <span data-ttu-id="25216-136">`%` Ve `%%` işleçleri F # ifade nesne kodu tırnak ekleme olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="25216-136">The `%` and `%%` operators enable you to add an F# expression object into a code quotation.</span></span> <span data-ttu-id="25216-137">Kullandığınız `%` ; kullanmanıza yazılan tırnak yazılan ifade nesne eklemeye işleci `%%` türsüz ifade nesne türü belirsiz bir tırnak eklemek için işleci.</span><span class="sxs-lookup"><span data-stu-id="25216-137">You use the `%` operator to insert a typed expression object into a typed quotation; you use the `%%` operator to insert an untyped expression object into an untyped quotation.</span></span> <span data-ttu-id="25216-138">Her iki işleçleri birli önek işleçler şunlardır.</span><span class="sxs-lookup"><span data-stu-id="25216-138">Both operators are unary prefix operators.</span></span> <span data-ttu-id="25216-139">Bu nedenle, `expr` türsüz ifade türü olan `Expr`, aşağıdaki kodu geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="25216-139">Thus if `expr` is an untyped expression of type `Expr`, the following code is valid.</span></span>

```fsharp
<@@ 1 + %%expr @@>
```

<span data-ttu-id="25216-140">Ve `expr` yazılmış bir teklif türü `Expr<int>`, aşağıdaki kodu geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="25216-140">And if `expr` is a typed quotation of type `Expr<int>`, the following code is valid.</span></span>

```fsharp
<@ 1 + %expr @>
```

## <a name="example"></a><span data-ttu-id="25216-141">Örnek</span><span class="sxs-lookup"><span data-stu-id="25216-141">Example</span></span>

### <a name="description"></a><span data-ttu-id="25216-142">Açıklama</span><span class="sxs-lookup"><span data-stu-id="25216-142">Description</span></span>
<span data-ttu-id="25216-143">Aşağıdaki örnek bir ifade nesnesine F # kodu koyun ve ifadeyi temsil eden F # kodu yazdırmak için kod tırnak işaretleri kullanımını göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="25216-143">The following example illustrates the use of code quotations to put F# code into an expression object and then print the F# code that represents the expression.</span></span> <span data-ttu-id="25216-144">Bir işlev `println` tanımlanan özyinelemeli işlev içeren `print` bir F # ifade nesnesi görüntüleyen (türünde `Expr`) kolay bir biçimde.</span><span class="sxs-lookup"><span data-stu-id="25216-144">A function `println` is defined that contains a recursive function `print` that displays an F# expression object (of type `Expr`) in a friendly format.</span></span> <span data-ttu-id="25216-145">Çeşitli Etkin desenler vardır [Microsoft.FSharp.Quotations.Patterns](https://msdn.microsoft.com/library/093944a9-c752-403a-8983-5fcd5dbf92a4) ve [Microsoft.FSharp.Quotations.DerivedPatterns](https://msdn.microsoft.com/library/d2434a6e-ae7b-4f3d-b567-c162938bc9cd) ifade nesnelerini çözümlemek için kullanılan modül.</span><span class="sxs-lookup"><span data-stu-id="25216-145">There are several active patterns in the [Microsoft.FSharp.Quotations.Patterns](https://msdn.microsoft.com/library/093944a9-c752-403a-8983-5fcd5dbf92a4) and [Microsoft.FSharp.Quotations.DerivedPatterns](https://msdn.microsoft.com/library/d2434a6e-ae7b-4f3d-b567-c162938bc9cd) modules that can be used to analyze expression objects.</span></span> <span data-ttu-id="25216-146">Bu örnek, F # deyimde ortaya çıkabilecek olası desenleri içermez.</span><span class="sxs-lookup"><span data-stu-id="25216-146">This example does not include all the possible patterns that might appear in an F# expression.</span></span> <span data-ttu-id="25216-147">Herhangi bir desen tetikler joker karakter deseni bir eşleşme tanınmayan (`_`) ve kullanarak işlenen `ToString` yöntemi, üzerinde `Expr` türü, eşleşme İfadenizde eklemek için etkin desen bildiğiniz sağlar.</span><span class="sxs-lookup"><span data-stu-id="25216-147">Any unrecognized pattern triggers a match to the wildcard pattern (`_`) and is rendered by using the `ToString` method, which, on the `Expr` type, lets you know the active pattern to add to your match expression.</span></span>


### <a name="code"></a><span data-ttu-id="25216-148">Kod</span><span class="sxs-lookup"><span data-stu-id="25216-148">Code</span></span>
[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-3/snippet601.fs)]
    
### <a name="output"></a><span data-ttu-id="25216-149">Çıkış</span><span class="sxs-lookup"><span data-stu-id="25216-149">Output</span></span>

```fsharp
fun (x:System.Int32) -> x + 1
a + 1
let f = fun (x:System.Int32) -> x + 10 in f 10
```

## <a name="example"></a><span data-ttu-id="25216-150">Örnek</span><span class="sxs-lookup"><span data-stu-id="25216-150">Example</span></span>

### <a name="description"></a><span data-ttu-id="25216-151">Açıklama</span><span class="sxs-lookup"><span data-stu-id="25216-151">Description</span></span>
<span data-ttu-id="25216-152">Üç Etkin desenler içinde de kullanabilirsiniz [ExprShape Modülü](https://msdn.microsoft.com/library/7685150e-2432-4d39-9338-57292eff18de) ifade ağaçları daha az Etkin desenler ile geçiş yapmak için.</span><span class="sxs-lookup"><span data-stu-id="25216-152">You can also use the three active patterns in the [ExprShape module](https://msdn.microsoft.com/library/7685150e-2432-4d39-9338-57292eff18de) to traverse expression trees with fewer active patterns.</span></span> <span data-ttu-id="25216-153">Bu Etkin desenler bir ağacı gezme istiyor ancak çoğu düğümlerinin tüm bilgileri gerekmez kullanışlı olabilir.</span><span class="sxs-lookup"><span data-stu-id="25216-153">These active patterns can be useful when you want to traverse a tree but you do not need all the information in most of the nodes.</span></span> <span data-ttu-id="25216-154">Bu düzenleri kullandığınızda, herhangi bir F # ifade aşağıdaki üç desenleri biriyle eşleşen: `ShapeVar` ifade bir değişken ise `ShapeLambda` ifade bir lambda ifadesi ise veya `ShapeCombination` ifade başka bir şey olması durumunda.</span><span class="sxs-lookup"><span data-stu-id="25216-154">When you use these patterns, any F# expression matches one of the following three patterns: `ShapeVar` if the expression is a variable, `ShapeLambda` if the expression is a lambda expression, or `ShapeCombination` if the expression is anything else.</span></span> <span data-ttu-id="25216-155">Etkin desenler önceki kod örneğinde olduğu gibi kullanarak bir ifade ağacına gezme, olası tüm F # ifade türleri işlemek için çok daha fazla desenleri kullanmak zorunda ve kodunuzu daha karmaşık olacaktır.</span><span class="sxs-lookup"><span data-stu-id="25216-155">If you traverse an expression tree by using the active patterns as in the previous code example, you have to use many more patterns to handle all possible F# expression types, and your code will be more complex.</span></span> <span data-ttu-id="25216-156">Daha fazla bilgi için bkz: [ExprShape.ShapeVar &#124; ShapeLambda &#124; ShapeCombination etkin düzeni](https://msdn.microsoft.com/visualfsharpdocs/conceptual/exprshape.shapevarhshapelambdahshapecombination-active-pattern-%5bfsharp%5d).</span><span class="sxs-lookup"><span data-stu-id="25216-156">For more information, see [ExprShape.ShapeVar&#124;ShapeLambda&#124;ShapeCombination Active Pattern](https://msdn.microsoft.com/visualfsharpdocs/conceptual/exprshape.shapevarhshapelambdahshapecombination-active-pattern-%5bfsharp%5d).</span></span>

<span data-ttu-id="25216-157">Aşağıdaki kod örneği için daha karmaşık çapraz geçişlerine temeli olarak kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="25216-157">The following code example can be used as a basis for more complex traversals.</span></span> <span data-ttu-id="25216-158">Bu kod, bir işlev çağrısı içeren bir ifadenin bir ifade ağacına oluşturulur `add`.</span><span class="sxs-lookup"><span data-stu-id="25216-158">In this code, an expression tree is created for an expression that involves a function call, `add`.</span></span> <span data-ttu-id="25216-159">[SpecificCall](https://msdn.microsoft.com/library/05a77b21-20fe-4b9a-8e07-aa999538198d) etkin desen herhangi çağrısına algılamak için kullanılan `add` ifade ağacında.</span><span class="sxs-lookup"><span data-stu-id="25216-159">The [SpecificCall](https://msdn.microsoft.com/library/05a77b21-20fe-4b9a-8e07-aa999538198d) active pattern is used to detect any call to `add` in the expression tree.</span></span> <span data-ttu-id="25216-160">Bu etkin desen çağrısı bağımsız atar `exprList` değeri.</span><span class="sxs-lookup"><span data-stu-id="25216-160">This active pattern assigns the arguments of the call to the `exprList` value.</span></span> <span data-ttu-id="25216-161">Bu durumda, vardır yalnızca iki, böylece bunlar çekilen ve işlev bağımsız değişkenler üzerinde yinelemeli olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="25216-161">In this case, there are only two, so these are pulled out and the function is called recursively on the arguments.</span></span> <span data-ttu-id="25216-162">Sonuçları bir çağrı temsil eden bir kod tırnak içine eklenen `mul` splice işlecini kullanarak (`%%`).</span><span class="sxs-lookup"><span data-stu-id="25216-162">The results are inserted into a code quotation that represents a call to `mul` by using the splice operator (`%%`).</span></span> <span data-ttu-id="25216-163">`println` İşlevi önceki örnekten sonuçları görüntülemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="25216-163">The `println` function from the previous example is used to display the results.</span></span>

<span data-ttu-id="25216-164">Elde edilen ifadesi yalnızca değişikliği farklıdır şekilde diğer etkin desen dalları kodda yalnızca aynı ifade ağacına oluşturur `add` için `mul`.</span><span class="sxs-lookup"><span data-stu-id="25216-164">The code in the other active pattern branches just regenerates the same expression tree, so the only change in the resulting expression is the change from `add` to `mul`.</span></span>


### <a name="code"></a><span data-ttu-id="25216-165">Kod</span><span class="sxs-lookup"><span data-stu-id="25216-165">Code</span></span>
[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-3/snippet701.fs)]
    
### <a name="output"></a><span data-ttu-id="25216-166">Çıkış</span><span class="sxs-lookup"><span data-stu-id="25216-166">Output</span></span>

```fsharp
1 + Module1.add(2,Module1.add(3,4))
1 + Module1.mul(2,Module1.mul(3,4))
```

## <a name="see-also"></a><span data-ttu-id="25216-167">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="25216-167">See Also</span></span>
[<span data-ttu-id="25216-168">F # dili başvurusu</span><span class="sxs-lookup"><span data-stu-id="25216-168">F# Language Reference</span></span>](index.md)

