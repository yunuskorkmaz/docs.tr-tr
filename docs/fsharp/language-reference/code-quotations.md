---
title: Kod Tırnak İşaretleri (F#)
description: 'F # kod teklifleri hakkında oluşturmak ve F # kodu ifadelerle programlı olarak çalışmanıza olanak sağlayan bir dil özellik öğrenin.'
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: dotnet-fsharp
ms.devlang: fsharp
ms.openlocfilehash: cfa2e4b9a4ad1776315dfa8ea82fb8fc3f13a552
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2018
---
# <a name="code-quotations"></a>Kod Tırnak İşaretleri

> [!NOTE]
API başvuru bağlantısı sizi MSDN'ye götürür.  Docs.microsoft.com API Başvurusu tamamlanmadı.

Bu konuda açıklanmaktadır *kod tırnak işaretleri*, oluşturmak ve F # kodu ifadelerle programlı olarak çalışmanıza olanak sağlayan bir dil özellik. Bu özellik F # kodunu temsil eden bir soyut söz dizimi ağaç oluşturmanıza olanak sağlar. Soyut söz dizimi ağaç geçiş ve uygulamanızın gereksinimlerine göre işlenir. Örneğin, F # kodu oluşturmak veya başka bir dilde içinde kodu oluşturmak için ağaç kullanabilirsiniz.


## <a name="quoted-expressions"></a>Tırnak işaretli ifadeleri
A *ifade tırnak içine alınmış* kodunuzda bu programınızı bir parçası olarak derlenmemiş olduğunu şekilde ayrılmış, ancak bunun yerine bir F # ifade temsil eden bir nesneye derlenmiş F # ifade. Tırnak içine alınmış bir ifade iki yoldan biriyle işaretleyebilirsiniz: türü bilgilerle veya tür bilgileri olmadan. Tür bilgileri dahil etmek istiyorsanız, simgeleri kullanın `<@` ve `@>` tırnak işaretli ifade sınırlandırmak için. Tür bilgileri gerekmiyorsa simgeleri kullanın `<@@` ve `@@>`. Aşağıdaki kod yazılan ve türsüz teklifleri gösterir.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-3/snippet501.fs)]

Büyük ifade ağacına geçiş türü bilgileri eklemezseniz hızlıdır. Yazılı sembolleriyle tırnak içine alınmış bir ifade sonuç türü `Expr<'T>`, burada tür parametresi F # derleyicinin türü çıkarımı algoritması tarafından belirlenen ifade türü. Kod tırnak işaretleri türü bilgileri olmadan kullandığınızda, teklif edilen ifadenin genel olmayan tür türüdür [Expr](https://msdn.microsoft.com/library/ed6a2caf-69d4-45c2-ab97-e9b3be9bce65). Çağırabilirsiniz [Raw](https://msdn.microsoft.com/library/47fb94f1-e77f-4c68-aabc-2b0ba40d59c2) özelliği belirtilmiş `Expr` türsüz elde etmek için sınıf `Expr` nesnesi.

Çeşitli F # ifade nesnelerini program aracılığıyla da oluşturmak izin statik yöntemler vardır `Expr` kullanmadan sınıfı, ifadeleri tırnak içine alınmış.

Kod tırnak tam bir ifade içermelidir unutmayın. İçin bir `let` bağlama, örneğin, tanımı ilişkili adı ve bağlama kullanan bir ek ifade gerekir. Ayrıntılı sözdizimi bu izleyen bir ifadesidir `in` anahtar sözcüğü. Üst düzey bir modüldeki modülü yalnızca sonraki ifadesinde budur ancak bir teklife, açıkça gerekli değildir.

Bu nedenle, aşağıdaki ifade geçerli değil.

```fsharp
// Not valid:
// <@ let f x = x + 1 @>
```

Ancak aşağıdaki ifadeler geçerlidir.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-3/snippet502.fs)]

Kod tırnak işaretleri kullanmak için bir içeri aktarma bildirimi ekleyin (kullanarak `open` anahtar sözcüğü) açılır [Microsoft.FSharp.Quotations](https://msdn.microsoft.com/library/e9ce8a3a-e00c-4190-bad5-cce52ee089b2) ad alanı.

F # PowerPack değerlendirmek ve F # ifade nesnelerini çalıştırmak için destek sağlar.


## <a name="expr-type"></a>İfade türü
Örneği `Expr` türünü F # ifade temsil eder. Hem genel hem de genel olmayan `Expr` türleri, F # kitaplığı belgelerinde belgelenmiştir. Daha fazla bilgi için bkz: [Microsoft.FSharp.Quotations Namespace](https://msdn.microsoft.com/visualfsharpdocs/conceptual/microsoft.fsharp.quotations-namespace-%5bfsharp%5d) ve [Quotations.Expr sınıfı](https://msdn.microsoft.com/visualfsharpdocs/conceptual/quotations.expr-class-%5bfsharp%5d).


## <a name="splicing-operators"></a>Boşluklarına ayıran işleçleri
Boşluklarına ayıran değişmez değer kod tırnak işaretleri programlı olarak veya başka bir kod tırnak oluşturulan ifadelerle birleştirmek etkinleştirir. `%` Ve `%%` işleçleri F # ifade nesne kodu tırnak ekleme olanak tanır. Kullandığınız `%` ; kullanmanıza yazılan tırnak yazılan ifade nesne eklemeye işleci `%%` türsüz ifade nesne türü belirsiz bir tırnak eklemek için işleci. Her iki işleçleri birli önek işleçler şunlardır. Bu nedenle, `expr` türsüz ifade türü olan `Expr`, aşağıdaki kodu geçerlidir.

```fsharp
<@@ 1 + %%expr @@>
```

Ve `expr` yazılmış bir teklif türü `Expr<int>`, aşağıdaki kodu geçerlidir.

```fsharp
<@ 1 + %expr @>
```

## <a name="example"></a>Örnek

### <a name="description"></a>Açıklama
Aşağıdaki örnek bir ifade nesnesine F # kodu koyun ve ifadeyi temsil eden F # kodu yazdırmak için kod tırnak işaretleri kullanımını göstermektedir. Bir işlev `println` tanımlanan özyinelemeli işlev içeren `print` bir F # ifade nesnesi görüntüleyen (türünde `Expr`) kolay bir biçimde. Çeşitli Etkin desenler vardır [Microsoft.FSharp.Quotations.Patterns](https://msdn.microsoft.com/library/093944a9-c752-403a-8983-5fcd5dbf92a4) ve [Microsoft.FSharp.Quotations.DerivedPatterns](https://msdn.microsoft.com/library/d2434a6e-ae7b-4f3d-b567-c162938bc9cd) ifade nesnelerini çözümlemek için kullanılan modül. Bu örnek, F # deyimde ortaya çıkabilecek olası desenleri içermez. Herhangi bir desen tetikler joker karakter deseni bir eşleşme tanınmayan (`_`) ve kullanarak işlenen `ToString` yöntemi, üzerinde `Expr` türü, eşleşme İfadenizde eklemek için etkin desen bildiğiniz sağlar.


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
Üç Etkin desenler içinde de kullanabilirsiniz [ExprShape Modülü](https://msdn.microsoft.com/library/7685150e-2432-4d39-9338-57292eff18de) ifade ağaçları daha az Etkin desenler ile geçiş yapmak için. Bu Etkin desenler bir ağacı gezme istiyor ancak çoğu düğümlerinin tüm bilgileri gerekmez kullanışlı olabilir. Bu düzenleri kullandığınızda, herhangi bir F # ifade aşağıdaki üç desenleri biriyle eşleşen: `ShapeVar` ifade bir değişken ise `ShapeLambda` ifade bir lambda ifadesi ise veya `ShapeCombination` ifade başka bir şey olması durumunda. Etkin desenler önceki kod örneğinde olduğu gibi kullanarak bir ifade ağacına gezme, olası tüm F # ifade türleri işlemek için çok daha fazla desenleri kullanmak zorunda ve kodunuzu daha karmaşık olacaktır. Daha fazla bilgi için bkz: [ExprShape.ShapeVar&#124;ShapeLambda&#124;ShapeCombination etkin düzeni](https://msdn.microsoft.com/visualfsharpdocs/conceptual/exprshape.shapevarhshapelambdahshapecombination-active-pattern-%5bfsharp%5d).

Aşağıdaki kod örneği için daha karmaşık çapraz geçişlerine temeli olarak kullanılabilir. Bu kod, bir işlev çağrısı içeren bir ifadenin bir ifade ağacına oluşturulur `add`. [SpecificCall](https://msdn.microsoft.com/library/05a77b21-20fe-4b9a-8e07-aa999538198d) etkin desen herhangi çağrısına algılamak için kullanılan `add` ifade ağacında. Bu etkin desen çağrısı bağımsız atar `exprList` değeri. Bu durumda, vardır yalnızca iki, böylece bunlar çekilen ve işlev bağımsız değişkenler üzerinde yinelemeli olarak adlandırılır. Sonuçları bir çağrı temsil eden bir kod tırnak içine eklenen `mul` splice işlecini kullanarak (`%%`). `println` İşlevi önceki örnekten sonuçları görüntülemek için kullanılır.

Elde edilen ifadesi yalnızca değişikliği farklıdır şekilde diğer etkin desen dalları kodda yalnızca aynı ifade ağacına oluşturur `add` için `mul`.


### <a name="code"></a>Kod
[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-3/snippet701.fs)]
    
### <a name="output"></a>Çıkış

```fsharp
1 + Module1.add(2,Module1.add(3,4))
1 + Module1.mul(2,Module1.mul(3,4))
```

## <a name="see-also"></a>Ayrıca Bkz.
[F# Dili Başvurusu](index.md)

