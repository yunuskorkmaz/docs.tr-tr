---
title: Kod Tırnak İşaretleri
description: Programlama yoluyla F# kod ifadeleri oluşturmanıza ve bunlarla F# çalışmanıza olanak tanıyan bir dil özelliği olan kod teklifleri hakkında bilgi edinin.
ms.date: 05/16/2016
ms.openlocfilehash: c6ec0078c685a6452f49edd289b01491dd62e3db
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630421"
---
# <a name="code-quotations"></a>Kod Tırnak İşaretleri

> [!NOTE]
> API başvuru bağlantısı sizi MSDN 'ye götürür.  Docs.microsoft.com API başvurusu tamamlanmadı.

Bu konu, kod ifadelerini programlama yoluyla oluşturmanıza ve bunlarla F# çalışmanıza olanak tanıyan bir dil özelliği olan *kod tekliflerini*açıklar. Bu özellik, kodu temsil F# eden bir soyut sözdizimi ağacı oluşturmanıza olanak sağlar. Soyut sözdizimi ağacı, uygulamanızın gereksinimlerine göre çapraz ve işlenebilir. Örneğin, ağacı kod oluşturmak F# veya başka bir dilde kod oluşturmak için kullanabilirsiniz.

## <a name="quoted-expressions"></a>Tırnak işareti Ifadesi

*Tırnak içine alınmış* bir ifade F# , kodunuzda, programınızın bir parçası olarak derlenmediği, ancak bunun yerine bir F# ifadeyi temsil eden bir nesneye derlenmiş şekilde sınırlanmış bir ifadedir. Tırnak içine alınmış bir ifadeyi iki şekilde işaretleyebilirsiniz: tür bilgisi veya tür bilgisi olmadan. Tür bilgilerini eklemek istiyorsanız, sembolleri `<@` kullanır ve `@>` tırnak içine alınmış ifadeyi sınırlandırın. Tür bilgilerine ihtiyacınız yoksa, ve `<@@` `@@>`simgelerini kullanırsınız. Aşağıdaki kod, yazılan ve türsüz teklifleri gösterir.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-3/snippet501.fs)]

Tür bilgilerini eklemezseniz büyük bir ifade ağacına geçiş yapmak daha hızlıdır. Türü belirlenmiş simgelerle tırnak içine alınmış bir ifadenin sonuç türü, tür `Expr<'T>`parametresi F# derleyicinin tür çıkarımı algoritması tarafından belirlendiği şekilde ifadenin türüne sahip olur. Kod tekliflerini tür bilgisi olmadan kullandığınızda, tırnak işareti türü genel olmayan [ifadedir.](https://msdn.microsoft.com/library/ed6a2caf-69d4-45c2-ab97-e9b3be9bce65) Türsüz [](https://msdn.microsoft.com/library/47fb94f1-e77f-4c68-aabc-2b0ba40d59c2) `Expr` nesneyieldeetmekiçin,yazılansınıftahamözelliğini`Expr` çağırabilirsiniz.

Tırnak içine alınmış ifadeler kullanmadan F# `Expr` sınıfında program aracılığıyla ifade nesneleri oluşturmanıza imkan tanıyan çeşitli statik yöntemler vardır.

Bir kod teklifinin bir bütün ifadeyi içermesi gerektiğini unutmayın. Örneğin, `let` bir bağlama için, hem ilişkili ad tanımının hem de bağlamayı kullanan ek bir ifadenin olması gerekir. Ayrıntılı söz diziminde, bu `in` anahtar sözcüğünü izleyen bir ifadedir. Modüldeki en üst düzey bu, modüldeki yalnızca bir sonraki ifadedir, ancak bir teklifte, açıkça gereklidir.

Bu nedenle, aşağıdaki ifade geçerli değildir.

```fsharp
// Not valid:
// <@ let f x = x + 1 @>
```

Ancak aşağıdaki ifadeler geçerlidir.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-3/snippet502.fs)]

Teklifleri değerlendirmek F# için, [ F# teklif değerlendirici](https://github.com/fsprojects/FSharp.Quotations.Evaluator)' ni kullanmanız gerekir. İfade nesnelerini değerlendirmek ve yürütmek F# için destek sağlar.

## <a name="expr-type"></a>Expr türü

`Expr` Türün bir örneği bir F# ifadeyi temsil eder. Hem genel hem de genel `Expr` olmayan türler F# kitaplık belgelerinde belgelenmiştir. Daha fazla bilgi için bkz. [Microsoft. FSharp. Quotations ad alanı](https://msdn.microsoft.com/visualfsharpdocs/conceptual/microsoft.fsharp.quotations-namespace-%5bfsharp%5d) ve [Quotations. Expr sınıfı](https://msdn.microsoft.com/visualfsharpdocs/conceptual/quotations.expr-class-%5bfsharp%5d).

## <a name="splicing-operators"></a>Splicing Işleçleri

Splicing, sabit kod tekliflerini programlı bir şekilde veya başka bir kod teklifinden oluşturduğunuz ifadelerle birleştirmenizi sağlar. Ve `%` işleçleri`%%` , bir kod teklifine bir F# ifade nesnesi eklemenizi sağlar. Türü belirlenmiş bir `%` teklife yazılmış bir ifade nesnesi eklemek için işlecini kullanırsınız; türsüz bir ifade nesnesini `%%` türsüz bir teklife eklemek için işlecini kullanırsınız. Her iki işleç de birli önek işleçleridir. Bu nedenle `expr` , türünde `Expr`türsüz bir ifade varsa, aşağıdaki kod geçerli olur.

```fsharp
<@@ 1 + %%expr @@>
```

`expr` Türü`Expr<int>`belirlenmiş bir tırnak ise, aşağıdaki kod geçerli olur.

```fsharp
<@ 1 + %expr @>
```

## <a name="example"></a>Örnek

### <a name="description"></a>Açıklama

Aşağıdaki örnek, kod tekliflerinin bir ifade nesnesine kod koymak F# ve sonra ifadeyi temsil eden F# kodu yazdırmak için kullanımını gösterir. Bir işlev `println` , F# bir ifade nesnesini (türünde `Expr`) kolay bir biçimde görüntüleyen özyinelemeli bir işlev `print` içeren tanımlanır. [Microsoft. FSharp. Quotations. Patterns](https://msdn.microsoft.com/library/093944a9-c752-403a-8983-5fcd5dbf92a4) ve [Microsoft. FSharp. Quotations. DerivedPatterns](https://msdn.microsoft.com/library/d2434a6e-ae7b-4f3d-b567-c162938bc9cd) modüllerinde ifade nesnelerini çözümlemek için kullanılabilen çeşitli etkin desenler vardır. Bu örnek, bir F# ifadede görünebilen tüm olası desenleri içermez. Tüm tanınmayan desenler joker karakter düzeniyle (`_`) bir eşleşme tetikleyip, `Expr` türü `ToString` kullanılarak işlenir ve bu da tür üzerinde, eşleştirme ifadenizde eklemek üzere etkin olan kalıbı bilmenizi sağlar.

### <a name="code"></a>Kod

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-3/snippet601.fs)]

### <a name="output"></a>Çıkış

```fsharp
fun (x:System.Int32) -> x + 1
a + 1
let f = fun (x:System.Int32) -> x + 10 in f 10
```

## <a name="example"></a>Örnek

### <a name="description"></a>Açıklama

Ayrıca, daha az etkin desenle ifade ağaçlarına çapraz geçiş yapmak için [ExprShape modülünde](https://msdn.microsoft.com/library/7685150e-2432-4d39-9338-57292eff18de) üç etkin deseni de kullanabilirsiniz. Bu etkin desenler, bir ağaca geçiş yapmak istediğinizde yararlı olabilir ancak düğümlerin çoğunda tüm bilgilere ihtiyacınız yoktur. Bu desenleri F# kullandığınızda, herhangi bir ifade aşağıdaki üç desenden biriyle eşleşir: `ShapeVar` ifade bir değişkense, `ShapeLambda` ifade bir lambda ifadesiyse veya `ShapeCombination` ifade başka bir şeydir. Önceki kod örneğinde olduğu gibi etkin desenleri kullanarak bir ifade ağacında çapraz geçiş yaparsanız, olası F# tüm ifade türlerini işlemek için çok daha fazla desen kullanmanız gerekir ve kodunuz daha karmaşık olacaktır. Daha fazla bilgi için bkz. [ExprShape. ShapeVar&#124;ShapeLambda&#124;shapebirleşimi etkin model](https://msdn.microsoft.com/visualfsharpdocs/conceptual/exprshape.shapevarhshapelambdahshapecombination-active-pattern-%5bfsharp%5d).

Aşağıdaki kod örneği, daha karmaşık traversals için temel olarak kullanılabilir. Bu kodda, bir işlev çağrısını `add`içeren bir ifade için bir ifade ağacı oluşturulur. İfade ağacında yapılan `add` herhangi bir çağrıyı algılamak için [SpecificCall](https://msdn.microsoft.com/library/05a77b21-20fe-4b9a-8e07-aa999538198d) etkin deseninin kullanılması. Bu etkin model, çağrının `exprList` bağımsız değişkenlerini değerine atar. Bu durumda, yalnızca ikisi vardır, bu nedenle bunlar kullanıma alınır ve işlev bağımsız değişkenlerde yinelemeli olarak çağırılır. Sonuçlar, splice işleci ( `mul` `%%`) kullanılarak yapılan çağrıyı temsil eden bir kod teklifine eklenir. Önceki `println` örnekteki işlev, sonuçları göstermek için kullanılır.

Diğer etkin model dallarındaki kod yalnızca aynı ifade ağacını yeniden oluşturur, bu nedenle sonuç ifadesindeki tek değişiklik, ' dan `add` `mul`' a değişir.

### <a name="code"></a>Kod

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-3/snippet701.fs)]

### <a name="output"></a>Çıkış

```fsharp
1 + Module1.add(2,Module1.add(3,4))
1 + Module1.mul(2,Module1.mul(3,4))
```

## <a name="see-also"></a>Ayrıca bkz.

- [F# Dili Başvurusu](index.md)
