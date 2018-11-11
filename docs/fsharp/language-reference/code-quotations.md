---
title: Kod Tırnak İşaretleri (F#)
description: F# kod teklifleri hakkında oluşturmak ve F# kodu ifadeleri ile programlı bir şekilde çalışmanıza olanak sağlayan bir dil özelliği hakkında bilgi edinin.
ms.date: 05/16/2016
ms.openlocfilehash: 27e9cf1d99e2b5955cc6359653fc87bdbe824cc7
ms.sourcegitcommit: db8b83057d052c1f9f249d128b08d4423af0f7c2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/02/2018
ms.locfileid: "47397208"
---
# <a name="code-quotations"></a>Kod Tırnak İşaretleri

> [!NOTE]
MSDN için API başvuru bağlantısı sizi yönlendirir.  Docs.microsoft.com API başvuru tamamlanmadı.

Bu konu başlığı altında açıklanır *kod tırnak işaretleri*, oluşturmak ve F# kodu ifadeleri ile programlı bir şekilde çalışmanıza olanak sağlayan bir dil özelliği. Bu özellik F# kodu temsil eden bir soyut sözdizimi ağacını oluşturmanıza olanak sağlar. Soyut sözdizimi ağacını geçiş ve uygulamanızın gereksinimlerine göre işlenir. Örneğin, ağaç F# kodu oluşturabilir veya bazı başka bir dilde kod oluşturmak için kullanabilirsiniz.

## <a name="quoted-expressions"></a>Tırnak işaretli ifadeleri

A *ifade alıntılanmış* bir F# ifadesi kodunuzda programınızın parçası derlenmedi şekilde ayrılır, ancak bunun yerine bir F# ifadeyi temsil eden bir nesneye derlenir. Tırnak içine alınmış bir ifade iki yoldan biriyle işaretleyebilirsiniz: türü bilgilerini ile veya olmadan türü bilgileri. Tür bilgilerini dahil etmek istiyorsanız, semboller kullanın `<@` ve `@>` tırnak içine alınmış deyim sınırlandırmak için. Tür bilgilerini gerekmiyorsa, semboller kullanın `<@@` ve `@@>`. Aşağıdaki kod, yazılan ve yazılmayan teklifleri gösterir.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-3/snippet501.fs)]

Tür bilgilerini eklemezseniz büyük ifade ağacının çapraz geçişi hızlıdır. Elde edilen türü belirlenmiş simgeleri ile alıntılanmış bir ifadenin `Expr<'T>`, burada F# derleyicinin tür çıkarımı algoritması tarafından belirlenen şekilde bir ifadenin türü tür parametresi yok. Kod tırnak işaretleri türü bilgisi olmadan kullandığınızda, genel olmayan tür tırnak işaretli ifadenin türü olan [Expr](https://msdn.microsoft.com/library/ed6a2caf-69d4-45c2-ab97-e9b3be9bce65). Çağırabilirsiniz [ham](https://msdn.microsoft.com/library/47fb94f1-e77f-4c68-aabc-2b0ba40d59c2) özelliği belirlenmiş `Expr` yazılmamış almak için sınıf `Expr` nesne.

F# ifade nesneleri program oluşturmanıza olanak sağlayan statik yöntemleri birçok `Expr` kullanmadan sınıf ifadeleri tırnak işareti.

Kod tırnak eksiksiz bir ifade içermelidir unutmayın. İçin bir `let` bağlama, örneğin, tanımı ilişkili adı ve bağlama kullanan bir ek bir ifade ihtiyacınız. Ayrıntılı sözdizimi bu izleyen bir ifadedir `in` anahtar sözcüğü. Üst düzey bir modülde modülü yalnızca sonraki ifade budur ancak bir teklifte kesinlikle gerekli olmadığı.

Bu nedenle, aşağıdaki ifade geçerli değil.

```fsharp
// Not valid:
// <@ let f x = x + 1 @>
```

Ancak, aşağıdaki ifadeler geçerlidir.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-3/snippet502.fs)]

Kod tırnak işaretleri kullanmak için içeri aktarma bildirimi ekleyin (kullanarak `open` anahtar sözcüğü) açılır [Microsoft.FSharp.Quotations](https://msdn.microsoft.com/library/e9ce8a3a-e00c-4190-bad5-cce52ee089b2) ad alanı.

F# PowerPack, değerlendirme ve F# ifadesi nesnelerini çalıştırmak için destek sağlar.

## <a name="expr-type"></a>İfade türü

Örneği `Expr` türünü temsil eden bir F# ifadesi. Hem genel hem de genel olmayan `Expr` türleri, F# kitaplığı belgelerinde belgelenmiştir. Daha fazla bilgi için [Microsoft.FSharp.Quotations Namespace](https://msdn.microsoft.com/visualfsharpdocs/conceptual/microsoft.fsharp.quotations-namespace-%5bfsharp%5d) ve [Quotations.Expr sınıfı](https://msdn.microsoft.com/visualfsharpdocs/conceptual/quotations.expr-class-%5bfsharp%5d).

## <a name="splicing-operators"></a>İşleçler ekleniyor

Boşluklarına ayıran, sabit kod tırnak işaretleri ile programlama yoluyla veya başka bir kod tırnak oluşturulmuş ifadeler birleştirmenize olanak sağlar. `%` Ve `%%` işleçleri bir kod tırnak F# ifadesi nesne eklemek etkinleştirin. Kullandığınız `%` işleci belirlenmiş ifade nesne türü belirtilmiş bir tırnak eklemek için; kullanmanıza `%%` yazılmamış bir tırnak yazılmamış ifade nesne eklemek için işleci. Her iki işleçleri birli önek işleçleridir. Bu nedenle, `expr` türünde yazılmamış bir ifadedir `Expr`, aşağıdaki kod geçerlidir.

```fsharp
<@@ 1 + %%expr @@>
```

Ve `expr` türü belirlenmiş bir teklif `Expr<int>`, aşağıdaki kod geçerlidir.

```fsharp
<@ 1 + %expr @>
```

## <a name="example"></a>Örnek

### <a name="description"></a>Açıklama

Aşağıdaki örnek bir ifade nesnesine F# kodu yerleştirin ve ardından ifadeyi temsil eden F# kodu yazdırmak için kod tırnak işaretleri kullanımını gösterir. Bir işlev `println` tanımlanan özyinelemeli işlev içeren `print` görüntüleyen bir F# ifadesi nesnesi (tür `Expr`) kolay bir biçimde. Etkin desenlerinde vardır [Microsoft.FSharp.Quotations.Patterns](https://msdn.microsoft.com/library/093944a9-c752-403a-8983-5fcd5dbf92a4) ve [Microsoft.FSharp.Quotations.DerivedPatterns](https://msdn.microsoft.com/library/d2434a6e-ae7b-4f3d-b567-c162938bc9cd) ifade nesnelerini çözümlemek için kullanılan modül. Bu örnek, bir F# ifadesi ortaya çıkabilecek olası desenleri içermez. Herhangi bir joker karakter deseni eşleşme deseni tetikler tanınmayan (`_`) ve kullanılarak işlenir `ToString` yöntemi, üzerinde `Expr` yazın, eşleşme ifadeniz eklemek için etkin desen bildiğiniz sağlar.

### <a name="code"></a>Kod

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-3/snippet601.fs)]

### <a name="output"></a>Çıkış

```fsharp
fun (x:System.Int32) -> x + 1
a + 1
let f = fun (x:System.Int32) -> x + 10 in f 10
```

## <a name="example"></a>Örnek

### <a name="description"></a>Açıklama

Üç Etkin desenler içinde kullanabilirsiniz [ExprShape Modülü](https://msdn.microsoft.com/library/7685150e-2432-4d39-9338-57292eff18de) daha az etkin desen ile ifade ağaçları geçirilecek. Ağacı gezme istiyor ancak düğümlerinin çoğunda tüm bilgilere ihtiyacınız yoksa, bu Etkin desenler yararlı olabilir. Bu desenleri kullandığınızda, aşağıdaki üç desenlerden birini tüm F# ifadeyle eşleşiyor: `ShapeVar` ifade bir değişken ise `ShapeLambda` ifade bir lambda ifadesi ise veya `ShapeCombination` ifade başka bir şey ise. Etkin desenler bir önceki kod örneğinde olduğu gibi kullanarak bir ifade ağacı gezme, olası tüm F# ifadesi türleri işlemek için çok sayıda diğer desenler kullanmak zorunda ve kodunuzu daha karmaşık olacaktır. Daha fazla bilgi için [ExprShape.ShapeVar&#124;ShapeLambda&#124;ShapeCombination etkin düzeni](https://msdn.microsoft.com/visualfsharpdocs/conceptual/exprshape.shapevarhshapelambdahshapecombination-active-pattern-%5bfsharp%5d).

Aşağıdaki kod örneği, daha karmaşık çapraz geçişleri için temel olarak kullanılabilir. Bu kod içinde bir ifade ağacı bir işlev çağrısı içeren bir ifade için oluşturulan `add`. [SpecificCall](https://msdn.microsoft.com/library/05a77b21-20fe-4b9a-8e07-aa999538198d) yapılan tüm çağrıların algılamak için kullanılan etkin desen `add` ifade ağacında. Çağrı bağımsız değişkenleri bu etkin desen atar `exprList` değeri. Bu durumda, var. yalnızca iki bunlar çekilen ve işlev yinelemeli olarak bağımsız değişkenler üzerinde çağrılır Sonuçları bir çağrı temsil eden bir kod tırnak içine eklenen `mul` splice işleci kullanarak (`%%`). `println` Önceki örnekten gelen işlevi sonuçları görüntülemek için kullanılır.

Etkin desen bir dala kodda değişiklik elde edilen ifade tek değişiklik, bu nedenle yalnızca aynı ifade ağacı oluşturur. `add` için `mul`.

### <a name="code"></a>Kod

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-3/snippet701.fs)]

### <a name="output"></a>Çıkış

```fsharp
1 + Module1.add(2,Module1.add(3,4))
1 + Module1.mul(2,Module1.mul(3,4))
```

## <a name="see-also"></a>Ayrıca bkz.

- [F# Dili Başvurusu](index.md)
