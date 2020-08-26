---
title: let Bağlamaları
description: "Bir tanıtıcıyı bir değer veya işlevle ilişkilendiren F # ' Let ' bağlamasını nasıl kullanacağınızı öğrenin."
ms.date: 05/16/2016
ms.openlocfilehash: 6f2396f480c5e6c631d0022f4732419ee5b07db6
ms.sourcegitcommit: 9c45035b781caebc63ec8ecf912dc83fb6723b1f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/25/2020
ms.locfileid: "88812230"
---
# <a name="let-bindings"></a>let Bağlamaları

*Bağlama* bir tanımlayıcıyı bir değer veya işlevle ilişkilendirir. Bir `let` adı bir değere veya işleve bağlamak için anahtar sözcüğünü kullanırsınız.

## <a name="syntax"></a>Syntax

```fsharp
// Binding a value:
let identifier-or-pattern [: type] =expressionbody-expression
// Binding a function value:
let identifier parameter-list [: return-type ] =expressionbody-expression
```

## <a name="remarks"></a>Açıklamalar

`let`Anahtar sözcüğü, bir veya daha fazla ad için değerleri ya da işlev değerlerini tanımlamak üzere deyimlerde kullanılır. İfadenin en basit formu `let` , bir adı aşağıdaki gibi basit bir değere bağlar.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1101.fs)]

İfadeyi yeni bir satır kullanarak tanımlayıcıdan ayırdıysanız, aşağıdaki kodda olduğu gibi, ifadenin her satırını girintileyebilirsiniz.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1102.fs)]

Yalnızca bir ad yerine, aşağıdaki kodda gösterildiği gibi, adları içeren bir model, örneğin bir tanımlama grubu belirtilebilir.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1103.fs)]

*Body ifadesi* , adların kullanıldığı ifadedir. Gövde ifadesi kendi satırında görünür, bu, anahtar kelimesinin ilk karakteriyle tam olarak çizgiye kadar girintilenir `let` :

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1104.fs)]

Bir `let` bağlama modül düzeyinde, bir sınıf türünün tanımında veya bir işlev tanımında olduğu gibi yerel kapsamlarda görünebilir. `let`Bir modülde veya bir sınıf türünde en üst düzeydeki bir bağlamanın gövde ifadesi olması gerekmez, ancak diğer kapsam düzeylerinde gövde ifadesi gereklidir. Aşağıdaki kodda gösterildiği gibi, ilişkili adlar, tanım noktası sonrasında kullanılabilir, ancak bağlama görüntülenmeden önce herhangi bir noktada kullanılamaz `let` .

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1105.fs)]

## <a name="function-bindings"></a>İşlev bağlamaları

İşlev bağlamaları, aşağıdaki kodda gösterildiği gibi işlev bağlamaları işlev adını ve parametreleri içermesi dışında değer bağlamaları kurallarını izler.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1106.fs)]

Genel olarak parametreler, demet deseni gibi desenlerdir:

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1107.fs)]

`let`Bağlama ifadesi, son ifadenin değerini değerlendirir. Bu nedenle, aşağıdaki kod örneğinde değeri, `result` `100 * function3 (1, 2)` olarak değerlendirilen ' den hesaplanır `300` .

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1109.fs)]

Daha fazla bilgi için bkz. [işlevler](index.md).

## <a name="type-annotations"></a>Tür ek açıklamaları

Parametre türlerini, iki nokta üst üste ekleyerek belirtebilirsiniz (:) sonra parantez içine alınmış bir tür adı. Ayrıca, iki nokta üst üste ekleyerek ve son parametreden sonra yazarak dönüş değerinin türünü de belirtebilirsiniz. Tam tür ek açıklamalarını `function1` parametre türleri olarak tamsayılar ile aşağıdaki gibi olacaktır.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1108.fs)]

Açık tür parametreleri olmadığında, işlevlerin parametre türlerini belirlemekte tür çıkarımı kullanılır. Bu, genel olacak bir parametre türünün otomatik olarak genelleştirilmesi dahil olabilir.

Daha fazla bilgi için bkz. [Otomatik Genelleştirme](../generics/automatic-generalization.md) ve [tür çıkarımı](../type-inference.md).

## <a name="let-bindings-in-classes"></a>Sınıflardaki let Bağlamaları

`let`Bağlama bir yapı veya kayıt türünde değil, sınıf türünde görünebilir. Sınıf türünde bir Let bağlaması kullanmak için, sınıfın bir birincil oluşturucusu olmalıdır. Oluşturucu parametreleri, sınıf tanımındaki tür adından sonra gelmelidir. `let`Bir sınıf türündeki bağlama, bu sınıf türü için özel alanları ve üyeleri tanımlar ve `do` türdeki bağlamalarla birlikte, türün birincil oluşturucusunun kodunu oluşturur. Aşağıdaki kod örneklerinde `MyClass` özel alanlar ve içeren bir sınıf gösterilmektedir `field1` `field2` .

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1110.fs)]

Ve kapsamları, `field1` `field2` bildirildiği türle sınırlıdır. Daha fazla bilgi için bkz. [ `let` sınıflarda](../members/let-bindings-in-classes.md) ve [sınıflarda](../classes.md)bağlamalar.

## <a name="type-parameters-in-let-bindings"></a>Let bağlamalarında tür parametreleri

`let`Modül düzeyinde bir tür veya bir hesaplama ifadesinde bir bağlama açık tür parametrelerine sahip olabilir. Bir ifadede, işlev tanımı içindeki gibi bir bağlamanın tür parametreleri olamaz. Daha fazla bilgi için bkz. [Genel türler](../generics/index.md).

## <a name="attributes-on-let-bindings"></a>Let bağlamalarında öznitelikler

Öznitelikler `let` , aşağıdaki kodda gösterildiği gibi, bir modüldeki en üst düzey bağlamalar için uygulanabilir.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1111.fs)]

## <a name="scope-and-accessibility-of-let-bindings"></a>Let bağlamalarının kapsamı ve erişilebilirliği

Bir Let bağlaması ile belirtilen bir varlığın kapsamı, bağlama göründükten sonra kapsayan kapsamın (bir işlev, modül, dosya veya sınıf gibi) bölümüyle sınırlıdır. Bu nedenle, bağlamanın bir ada bir ad sunmasına izin ver. Bir modülde, bir modüldeki izin bağlamaları modülün ortak işlevlerine derlendiğinden, bir modüle izin ver değeri veya işlevi modülün istemcileri tarafından erişilebilirdir. Buna karşılık, bir sınıftaki bağlamaların sınıfına özel olması gerekir.

Normalde, modüller içindeki işlevler, istemci kodu tarafından kullanıldığında modülün adı ile nitelenmelidir. Örneğin, bir modülün işlevi varsa `Module1` `function1` , kullanıcılar `Module1.function1` işlevine başvurmak için belirtecekti.

Modül kullanıcıları modül adı tarafından nitelendirilmeden Bu modüldeki işlevlerin kullanılabilmesini sağlamak için içeri aktarma bildirimi kullanabilir. Yalnızca bahsedilen örnekte, modülün kullanıcıları bu durumda içeri aktarma bildirimini aç ' ı kullanarak modülü açabilir `Module1` ve bundan sonra doğrudan öğesine başvurabilirler `function1` .

```fsharp
module Module1 =
    let function1 x = x + 1.0

module Module2 =
    let function2 x =
        Module1.function1 x

open Module1

let function3 x =
    function1 x
```

Bazı modüllerin [RequireQualifiedAccess](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-core-requirequalifiedaccessattribute.html)özniteliği vardır. Bu, sergiledikleri işlevlerin modülün adı ile nitelendirilmeleri gerektiği anlamına gelir. Örneğin, F # liste modülünün bu özniteliği vardır.

Modüller ve erişim denetimi hakkında daha fazla bilgi için bkz. [modüller](../modules.md) ve [Access Control](../access-control.md).

## <a name="see-also"></a>Ayrıca bkz.

- [İşlevler](index.md)
- [`let` Sınıflarda bağlamalar](../members/let-bindings-in-classes.md)
