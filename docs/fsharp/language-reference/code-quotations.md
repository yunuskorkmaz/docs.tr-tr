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
# <a name="code-quotations"></a>Kod teklifleri

Bu makalede, programlama yoluyla F # kod ifadelerini oluşturup birlikte çalışmanıza olanak tanıyan bir dil özelliği olan *kod teklifleri* açıklanmaktadır. Bu özellik, F # kodunu temsil eden bir soyut sözdizimi ağacı oluşturmanıza olanak sağlar. Soyut sözdizimi ağacı, uygulamanızın gereksinimlerine göre çapraz ve işlenebilir. Örneğin, ağacı kullanarak F # kodu oluşturabilir veya başka bir dilde kod oluşturabilirsiniz.

## <a name="quoted-expressions"></a>Tırnak işareti Ifadesi

*Tırnak içine alınmış bir ifade* , kodunuzda, programınızın bir parçası olarak derlenmediği, ancak bunun yerine bir f # ifadesini temsil eden bir nesneye derlenen bir f # deyimidir. Tırnak içine alınmış bir ifadeyi iki şekilde işaretleyebilirsiniz: tür bilgisi veya tür bilgisi olmadan. Tür bilgilerini eklemek istiyorsanız, sembolleri kullanır `<@` ve `@>` tırnak içine alınmış ifadeyi sınırlandırın. Tür bilgilerine ihtiyacınız yoksa, ve simgelerini kullanırsınız `<@@` `@@>` . Aşağıdaki kod, yazılan ve türsüz teklifleri gösterir.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-3/snippet501.fs)]

Tür bilgilerini eklemezseniz büyük bir ifade ağacına geçiş yapmak daha hızlıdır. Türü belirlenmiş simgelerle tırnak içine alınmış bir ifadenin sonuç türü, `Expr<'T>` tür parametresinin F # derleyicisinin tür çıkarımı algoritması tarafından belirlendiği şekilde ifadenin türüne sahip olduğu yerdir. Kod tekliflerini tür bilgisi olmadan kullandığınızda, tırnak [işareti türü genel olmayan ifadedir.](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-quotations-fsharpexpr.html) [Raw](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-quotations-fsharpexpr-1.html#Raw) `Expr` Türsüz nesneyi elde etmek için, yazılan sınıfta ham özelliğini çağırabilirsiniz `Expr` .

Tırnak içine alınmış ifadeler kullanmadan, sınıfında programlama yoluyla F # ifade nesneleri oluşturmanıza izin veren çeşitli statik yöntemler vardır `Expr` .

Bir kod teklifinin bir bütün ifadeyi içermesi gerektiğini unutmayın. `let`Örneğin, bir bağlama için, hem ilişkili ad tanımının hem de bağlamayı kullanan ek bir ifadenin olması gerekir. Ayrıntılı söz diziminde, bu anahtar sözcüğünü izleyen bir ifadedir `in` . Modüldeki en üst düzey bu, modüldeki yalnızca bir sonraki ifadedir, ancak bir teklifte, açıkça gereklidir.

Bu nedenle, aşağıdaki ifade geçerli değildir.

```fsharp
// Not valid:
// <@ let f x = x + 1 @>
```

Ancak aşağıdaki ifadeler geçerlidir.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-3/snippet502.fs)]

F # tekliflerini değerlendirmek için [f # teklif Değerlendiricisi](https://github.com/fsprojects/FSharp.Quotations.Evaluator)kullanmanız gerekir. F # ifade nesnelerini değerlendirmek ve yürütmek için destek sağlar.

F # teklifleri de tür kısıtlaması bilgilerini korur. Aşağıdaki örneği inceleyin:

```fsharp
open FSharp.Linq.RuntimeHelpers

let eval q = LeafExpressionConverter.EvaluateQuotation q

let inline negate x = -x
// val inline negate: x: ^a ->  ^a when  ^a : (static member ( ~- ) :  ^a ->  ^a)

<@ negate 1.0 @>  |> eval
```

İşlev tarafından oluşturulan kısıtlama `inline` , kod kullanımı içinde tutulur. `negate`İşlevin alıntı yapılabilir formu artık değerlendirilebilirler.

## <a name="expr-type"></a>Expr türü

Türün bir örneği `Expr` bir F # ifadesini temsil eder. Hem genel hem de genel olmayan `Expr` türler F # kitaplığı belgelerinde belgelenmiştir. Daha fazla bilgi için bkz. [FSharp. Quotations ad alanı](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-quotations.html) ve [Quotations. Expr sınıfı](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-quotations-fsharpexpr.html).

## <a name="splicing-operators"></a>Splicing Işleçleri

Splicing, sabit kod tekliflerini programlı bir şekilde veya başka bir kod teklifinden oluşturduğunuz ifadelerle birleştirmenizi sağlar. `%`Ve `%%` işleçleri, bir kod teklifine bir F # ifade nesnesi eklemenizi sağlar. Türü belirlenmiş bir `%` teklife yazılmış bir ifade nesnesi eklemek için işlecini kullanırsınız; türsüz bir `%%` ifade nesnesini türsüz bir teklife eklemek için işlecini kullanırsınız. Her iki işleç de birli önek işleçleridir. Bu nedenle `expr` , türünde türsüz bir ifade varsa `Expr` , aşağıdaki kod geçerli olur.

```fsharp
<@@ 1 + %%expr @@>
```

`expr`Türü belirlenmiş bir tırnak ise `Expr<int>` , aşağıdaki kod geçerli olur.

```fsharp
<@ 1 + %expr @>
```

## <a name="example"></a>Örnek

### <a name="description"></a>Description

Aşağıdaki örnek, F # kodunu bir ifade nesnesine koymak için kod tekliflerinin kullanımını gösterir ve ardından ifadeyi temsil eden F # kodunu yazdırır. Kolay bir `println` `print` biçimde bir F # ifade nesnesi (türünde) görüntüleyen özyinelemeli bir işlev içeren bir işlev tanımlanmıştır `Expr` . [FSharp. Quotations. Patterns](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-quotations-patternsmodule.html) ve [FSharp. Quotations. DerivedPatterns](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-quotations-derivedpatternsmodule.html) modüllerinde ifade nesnelerini çözümlemek için kullanılabilen çeşitli etkin desenler vardır. Bu örnek, bir F # ifadesinde görünebilen tüm olası desenleri içermez. Tüm tanınmayan desenler joker karakter düzeniyle () bir eşleşme `_` tetikleyip, türü kullanılarak işlenir ve `ToString` Bu da tür üzerinde, `Expr` eşleştirme ifadenizde eklemek üzere etkin olan kalıbı bilmenizi sağlar.

### <a name="code"></a>Kod

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-3/snippet601.fs)]

### <a name="output"></a>Çıkış

```fsharp
fun (x:System.Int32) -> x + 1
a + 1
let f = fun (x:System.Int32) -> x + 10 in f 10
```

## <a name="example"></a>Örnek

### <a name="description"></a>Description

Ayrıca, daha az etkin desenle ifade ağaçlarına çapraz geçiş yapmak için [ExprShape modülünde](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-quotations-exprshapemodule.html) üç etkin deseni de kullanabilirsiniz. Bu etkin desenler, bir ağaca geçiş yapmak istediğinizde yararlı olabilir ancak düğümlerin çoğunda tüm bilgilere ihtiyacınız yoktur. Bu desenleri kullandığınızda herhangi bir F # ifadesi şu üç desenden biriyle eşleşir: `ShapeVar` ifade bir değişkense, `ShapeLambda` ifade bir lambda ifadesiyse veya `ShapeCombination` ifade başka bir şeydir. Önceki kod örneğinde olduğu gibi etkin desenleri kullanarak bir ifade ağacında çapraz geçiş yaparsanız, tüm olası F # ifade türlerini işlemek için çok daha fazla desen kullanmanız gerekir ve kodunuz daha karmaşık olacaktır. Daha fazla bilgi için bkz. [ExprShape. ShapeVar&#124;ShapeLambda&#124;Shapekombinasyon etkin model](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-quotations-exprshapemodule.html#(%20|ShapeVar|ShapeLambda|ShapeCombination|%20)).

Aşağıdaki kod örneği, daha karmaşık traversals için temel olarak kullanılabilir. Bu kodda, bir işlev çağrısını içeren bir ifade için bir ifade ağacı oluşturulur `add` . İfade ağacında yapılan herhangi bir çağrıyı algılamak için [SpecificCall](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-quotations-derivedpatternsmodule.html#(%20|SpecificCall|_|%20)) etkin deseninin kullanılması `add` . Bu etkin model, çağrının bağımsız değişkenlerini `exprList` değerine atar. Bu durumda, yalnızca ikisi vardır, bu nedenle bunlar kullanıma alınır ve işlev bağımsız değişkenlerde yinelemeli olarak çağırılır. Sonuçlar, `mul` splice işleci () kullanılarak yapılan çağrıyı temsil eden bir kod teklifine eklenir `%%` . `println`Önceki örnekteki işlev, sonuçları göstermek için kullanılır.

Diğer etkin model dallarındaki kod yalnızca aynı ifade ağacını yeniden oluşturur, bu nedenle sonuç ifadesindeki tek değişiklik, ' dan ' a değişir `add` `mul` .

### <a name="code"></a>Kod

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-3/snippet701.fs)]

### <a name="output"></a>Çıkış

```fsharp
1 + Module1.add(2,Module1.add(3,4))
1 + Module1.mul(2,Module1.mul(3,4))
```

## <a name="see-also"></a>Ayrıca bkz.

- [F # dil başvurusu](index.md)
