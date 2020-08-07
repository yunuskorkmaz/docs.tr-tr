---
title: Kod Tırnak İşaretleri
description: 'Programlama yoluyla F # kod ifadeleri oluşturup bunlarla çalışmanıza olanak tanıyan bir dil özelliği olan F # kod teklifleri hakkında bilgi edinin.'
ms.date: 05/16/2016
ms.openlocfilehash: bb5c03edd180c42667731bb90d7a1f624ed2e522
ms.sourcegitcommit: c37e8d4642fef647ebab0e1c618ecc29ddfe2a0f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/06/2020
ms.locfileid: "87855405"
---
# <a name="code-quotations"></a>Kod teklifleri

Bu makalede, programlama yoluyla F # kod ifadelerini oluşturup birlikte çalışmanıza olanak tanıyan bir dil özelliği olan *kod teklifleri*açıklanmaktadır. Bu özellik, F # kodunu temsil eden bir soyut sözdizimi ağacı oluşturmanıza olanak sağlar. Soyut sözdizimi ağacı, uygulamanızın gereksinimlerine göre çapraz ve işlenebilir. Örneğin, ağacı kullanarak F # kodu oluşturabilir veya başka bir dilde kod oluşturabilirsiniz.

> [!NOTE]
> F # için docs.microsoft.com API başvurusu tamamlanmadı. Bozuk bağlantılarla karşılaşırsanız, bunun yerine [F # Çekirdek Kitaplığı belgelerine](https://fsharp.github.io/fsharp-core-docs/) başvurun.

## <a name="quoted-expressions"></a>Tırnak işareti Ifadesi

*Tırnak içine alınmış bir ifade* , kodunuzda, programınızın bir parçası olarak derlenmediği, ancak bunun yerine bir f # ifadesini temsil eden bir nesneye derlenen bir f # deyimidir. Tırnak içine alınmış bir ifadeyi iki şekilde işaretleyebilirsiniz: tür bilgisi veya tür bilgisi olmadan. Tür bilgilerini eklemek istiyorsanız, sembolleri kullanır `<@` ve `@>` tırnak içine alınmış ifadeyi sınırlandırın. Tür bilgilerine ihtiyacınız yoksa, ve simgelerini kullanırsınız `<@@` `@@>` . Aşağıdaki kod, yazılan ve türsüz teklifleri gösterir.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-3/snippet501.fs)]

Tür bilgilerini eklemezseniz büyük bir ifade ağacına geçiş yapmak daha hızlıdır. Türü belirlenmiş simgelerle tırnak içine alınmış bir ifadenin sonuç türü, `Expr<'T>` tür parametresinin F # derleyicisinin tür çıkarımı algoritması tarafından belirlendiği şekilde ifadenin türüne sahip olduğu yerdir. Kod tekliflerini tür bilgisi olmadan kullandığınızda, tırnak [işareti türü genel olmayan ifadedir.](https://msdn.microsoft.com/library/ed6a2caf-69d4-45c2-ab97-e9b3be9bce65) [Raw](https://msdn.microsoft.com/library/47fb94f1-e77f-4c68-aabc-2b0ba40d59c2) `Expr` Türsüz nesneyi elde etmek için, yazılan sınıfta ham özelliğini çağırabilirsiniz `Expr` .

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

## <a name="expr-type"></a>Expr türü

Türün bir örneği `Expr` bir F # ifadesini temsil eder. Hem genel hem de genel olmayan `Expr` türler F # kitaplığı belgelerinde belgelenmiştir. Daha fazla bilgi için bkz. [Microsoft. FSharp. Quotations ad alanı](https://msdn.microsoft.com/visualfsharpdocs/conceptual/microsoft.fsharp.quotations-namespace-%5bfsharp%5d) ve [Quotations. Expr sınıfı](https://msdn.microsoft.com/visualfsharpdocs/conceptual/quotations.expr-class-%5bfsharp%5d).

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

### <a name="description"></a>Açıklama

Aşağıdaki örnek, F # kodunu bir ifade nesnesine koymak için kod tekliflerinin kullanımını gösterir ve ardından ifadeyi temsil eden F # kodunu yazdırır. Kolay bir `println` `print` biçimde bir F # ifade nesnesi (türünde) görüntüleyen özyinelemeli bir işlev içeren bir işlev tanımlanmıştır `Expr` . [Microsoft. FSharp. Quotations. Patterns](https://msdn.microsoft.com/library/093944a9-c752-403a-8983-5fcd5dbf92a4) ve [Microsoft. FSharp. Quotations. DerivedPatterns](https://msdn.microsoft.com/library/d2434a6e-ae7b-4f3d-b567-c162938bc9cd) modüllerinde ifade nesnelerini çözümlemek için kullanılabilen çeşitli etkin desenler vardır. Bu örnek, bir F # ifadesinde görünebilen tüm olası desenleri içermez. Tüm tanınmayan desenler joker karakter düzeniyle () bir eşleşme `_` tetikleyip, türü kullanılarak işlenir ve `ToString` Bu da tür üzerinde, `Expr` eşleştirme ifadenizde eklemek üzere etkin olan kalıbı bilmenizi sağlar.

### <a name="code"></a>Kod

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-3/snippet601.fs)]

### <a name="output"></a>Çıktı

```fsharp
fun (x:System.Int32) -> x + 1
a + 1
let f = fun (x:System.Int32) -> x + 10 in f 10
```

## <a name="example"></a>Örnek

### <a name="description"></a>Açıklama

Ayrıca, daha az etkin desenle ifade ağaçlarına çapraz geçiş yapmak için [ExprShape modülünde](https://msdn.microsoft.com/library/7685150e-2432-4d39-9338-57292eff18de) üç etkin deseni de kullanabilirsiniz. Bu etkin desenler, bir ağaca geçiş yapmak istediğinizde yararlı olabilir ancak düğümlerin çoğunda tüm bilgilere ihtiyacınız yoktur. Bu desenleri kullandığınızda herhangi bir F # ifadesi şu üç desenden biriyle eşleşir: `ShapeVar` ifade bir değişkense, `ShapeLambda` ifade bir lambda ifadesiyse veya `ShapeCombination` ifade başka bir şeydir. Önceki kod örneğinde olduğu gibi etkin desenleri kullanarak bir ifade ağacında çapraz geçiş yaparsanız, tüm olası F # ifade türlerini işlemek için çok daha fazla desen kullanmanız gerekir ve kodunuz daha karmaşık olacaktır. Daha fazla bilgi için bkz. [ExprShape. ShapeVar&#124;ShapeLambda&#124;Shapekombinasyon etkin model](https://msdn.microsoft.com/visualfsharpdocs/conceptual/exprshape.shapevarhshapelambdahshapecombination-active-pattern-%5bfsharp%5d).

Aşağıdaki kod örneği, daha karmaşık traversals için temel olarak kullanılabilir. Bu kodda, bir işlev çağrısını içeren bir ifade için bir ifade ağacı oluşturulur `add` . İfade ağacında yapılan herhangi bir çağrıyı algılamak için [SpecificCall](https://msdn.microsoft.com/library/05a77b21-20fe-4b9a-8e07-aa999538198d) etkin deseninin kullanılması `add` . Bu etkin model, çağrının bağımsız değişkenlerini `exprList` değerine atar. Bu durumda, yalnızca ikisi vardır, bu nedenle bunlar kullanıma alınır ve işlev bağımsız değişkenlerde yinelemeli olarak çağırılır. Sonuçlar, `mul` splice işleci () kullanılarak yapılan çağrıyı temsil eden bir kod teklifine eklenir `%%` . `println`Önceki örnekteki işlev, sonuçları göstermek için kullanılır.

Diğer etkin model dallarındaki kod yalnızca aynı ifade ağacını yeniden oluşturur, bu nedenle sonuç ifadesindeki tek değişiklik, ' dan ' a değişir `add` `mul` .

### <a name="code"></a>Kod

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-3/snippet701.fs)]

### <a name="output"></a>Çıktı

```fsharp
1 + Module1.add(2,Module1.add(3,4))
1 + Module1.mul(2,Module1.mul(3,4))
```

## <a name="see-also"></a>Ayrıca bkz.

- [F # dil başvurusu](index.md)
