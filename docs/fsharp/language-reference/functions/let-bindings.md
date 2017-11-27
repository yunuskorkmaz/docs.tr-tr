---
title: "let Bağlamaları (F#)"
description: "F # 'bir değer veya işlevi bir tanımlayıcı ilişkilendirir bağlama let' kullanmayı öğrenin."
keywords: "Visual f #, f # işlevsel programlama"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: bee69edc-d5ae-46bd-8b56-f02d97725d0d
ms.openlocfilehash: a57c5572e4bb5a3777c928dd572b7a84d4f0a334
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="let-bindings"></a>let Bağlamaları

A *bağlama* bir değer veya işlevi bir tanımlayıcı ilişkilendirir. Kullandığınız `let` bir değer veya işlevi için bir ad bağlamak için anahtar sözcüğü.

## <a name="syntax"></a>Sözdizimi

```fsharp
// Binding a value:
let identifier-or-pattern [: type] =expressionbody-expression
// Binding a function value:
let identifier parameter-list [: return-type ] =expressionbody-expression
```

## <a name="remarks"></a>Açıklamalar

`let` Anahtar sözcüğü değerleri veya bir veya daha fazla adları için işlevi değerleri tanımlamak için ifadeleri bağlama kullanılır. En basit biçimi `let` ifadesi bir ad gibi basit bir değere bağlar.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet1101.fs)]

Yeni bir satır kullanarak tanımlayıcı ifadesinden ayırmak, her satırın aşağıdaki kodu olduğu gibi ifadesinin girinti gerekir.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet1102.fs)]

Yalnızca bir adı yerine, adlarını içeren bir desen belirtilebilir, aşağıdaki kodda gösterildiği gibi bir tanımlama grubu,.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet1103.fs)]

*Gövde ifade* adları kullanılır ifadesidir. Gövde ifade ilk karakteri ile tam olarak yukarı satırına girintili kendi satırında görünen `let` anahtar sözcüğü:

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet1104.fs)]

A `let` bağlama görünebilir modülü düzeyinde bir sınıf türü tanımını veya yerel kapsamlar, işlev tanımının olduğu gibi. A `let` bağlama en üst düzeydeki bir modüle ya da bir sınıf türü bir gövde ifadesi olması gerekmez, ancak diğer kapsam düzeylerde gövde ifade gereklidir. Bağımlı adları, tanımının, ancak önce herhangi bir noktada değil noktadan sonra kullanılabilir `let` aşağıdaki kodda gösterildiği gibi bağlama görüntülenir.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet1105.fs)]
    
## <a name="function-bindings"></a>İşlev bağlamaları

Aşağıdaki kodda gösterildiği gibi işlev bağlamaları işlev adı ve parametreleri dahil dışında işlev bağlamaları değeri bağlamaları için kuralları izleyin.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet1106.fs)]

Genel olarak, bir demet deseni gibi düzenleri Parametreler şunlardır:

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet1107.fs)]

A `let` ifade bağlama son deyim değerine değerlendirir. Bu nedenle, aşağıdaki kod örneğinde, değeri içinde `result` gelen hesaplanan `100 * function3 (1, 2)`, hesaplar için `300`.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet1109.fs)]

Daha fazla bilgi için bkz: [işlevler](index.md).

## <a name="type-annotations"></a>Tür ek açıklamaları

Parantez içinde tüm iliştirilmiş bir tür adı ve ardından iki nokta (:) dahil ederek parametreler için türlerini belirtebilirsiniz. Dönüş değeri türü iki nokta üst üste ve türünü sonra son parametre ekleyerek de belirtebilirsiniz. Tam tür ek açıklamaları için `function1`, parametre türleri olarak tamsayılar ile aşağıdaki gibi olur.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet1108.fs)]

Açık tür parametre bulunmadığında tür çıkarımı işlevlerin parametre türlerini belirlemek için kullanılır. Bu, otomatik olarak genel olarak bir parametrenin türü genelleme içerebilir.

Daha fazla bilgi için bkz: [otomatik Genelleştirme](../generics/automatic-generalization.md) ve [tür çıkarımı](../type-inference.md).

## <a name="let-bindings-in-classes"></a>Sınıflardaki let Bağlamaları

A `let` bağlama, sınıf türü ancak yapısı veya kayıt türü görünebilir. Bir sınıf türü bağlama let kullanmak için sınıfı birincil bir oluşturucuya sahip olmalıdır. Oluşturucu parametreleri sınıf tanımında tür adından sonra görünmesi gerekir. A `let` bir sınıf türü bağlamasında tanımlar özel alanlar ve üyeleri bu sınıf türü için ve ile birlikte `do` türü bağlama türü için birincil Oluşturucu için kod oluşturur. Bir sınıfa aşağıdaki kodu örnekler `MyClass` özel alanlarla `field1` ve `field2`.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet1110.fs)]

Kapsamların `field1` ve `field2` bunlar bildirilen türü sınırlıdır. Daha fazla bilgi için bkz: [ `let` sınıflardaki bağlamaları](../members/let-bindings-in-classes.md) ve [sınıfları](../classes.md).

## <a name="type-parameters-in-let-bindings"></a>Tür parametrelerinde let bağlamaları

A `let` bağlama düzeyinde modülü, bir tür ya da bir hesaplama ifadesi açık türü parametrelerine sahip olabilir. Bir işlev tanımı içinde gibi bir ifadede bağlama let tür parametreleri olamaz. Daha fazla bilgi için bkz: [genel türler](../generics/index.md).

## <a name="attributes-on-let-bindings"></a>Özniteliklerde let bağlamaları

Öznitelikleri uygulanabilir çok üst düzey `let` aşağıdaki kodda gösterildiği gibi bir modüldeki bağlar.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet1111.fs)]
    
## <a name="scope-and-accessibility-of-let-bindings"></a>Kapsam ve Let bağlamaları erişilebilirliğini

Let bağlama ile bildirilen varlık kapsamı içeren bölümüne sınırlıdır kapsam (bir işlev, modül, dosya veya sınıf gibi) bağlama göründükten sonra. Bu nedenle, bir let bağlama kapsam içine bir ad tanıtır söylenebilir. Bir modül let bağlamaları modülünün genel işlevlerini derlenen beri modülü erişilebilen sürece bir modüldeki bir let ilişkili değer veya işlevi bir modül istemcilere erişilebilir. Bunun aksine, bir sınıf let bağlamaları sınıfına özeldir.

Normalde, modüllerdeki işlevlerin istemci kodu tarafından kullanıldığında, modülün adıyla nitelenmelidir. Örneğin, bir modül, `Module1` bir işlev `function1`, kullanıcıların belirtirsiniz `Module1.function1` işlevine başvurmak için.

Kullanıcılar bir modülün modül adı tarafından yetkili olmadan bu modül içinde işlevleri kullanmak için kullanılabilir hale getirmek alma bildirimi kullanabilir. Yalnızca belirtilen örnekte modülü kullanıcılarının bu durumda modül alma bildirimi açık kullanarak açabilirsiniz `Module1` ve bundan sonra başvurulacak `function1` doğrudan.

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

Bazı modüller özniteliğine sahip [RequireQualifiedAccess](https://msdn.microsoft.com/library/8b9b6ade-0471-4413-ac5d-638cd0de5f15), yani ortaya işlevleri modülünün adıyla nitelendirilmesi gerekir. Örneğin, F # List Modülü bu özniteliği vardır.

Modülleri ve erişim denetimi hakkında daha fazla bilgi için bkz: [modülleri](../modules.md) ve [erişim denetimi](../access-control.md).

## <a name="see-also"></a>Ayrıca Bkz.

[İşlevler](index.md)

[`let`Sınıflardaki bağlamaları](../members/let-bindings-in-classes.md)
