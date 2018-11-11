---
title: let Bağlamaları (F#)
description: F# 'let bir değer ya da işlevin tanımlayıcı ilişkilendiren bir bağlama' kullanmayı öğrenin.
ms.date: 05/16/2016
ms.openlocfilehash: 1a35b5a39f2768a18665b5c7fe768af0e7714577
ms.sourcegitcommit: db8b83057d052c1f9f249d128b08d4423af0f7c2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/02/2018
ms.locfileid: "43777476"
---
# <a name="let-bindings"></a>let Bağlamaları

A *bağlama* bir değer ya da işlevin tanımlayıcı ilişkilendirir. Kullandığınız `let` bir değer veya işlevi için bir ad bağlamak için anahtar sözcüğü.

## <a name="syntax"></a>Sözdizimi

```fsharp
// Binding a value:
let identifier-or-pattern [: type] =expressionbody-expression
// Binding a function value:
let identifier parameter-list [: return-type ] =expressionbody-expression
```

## <a name="remarks"></a>Açıklamalar

`let` Anahtar sözcüğü, bağlama ifadeleri değerleri veya bir veya daha çok işlevi değerlerini tanımlamak için kullanılır. En basit biçimi `let` ifade bir ad gibi basit bir değere bağlar.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet1101.fs)]

Yeni bir satır kullanarak tanımlayıcı ifadesinden ayırarak, aşağıdaki kodda gösterildiği gibi ifadesinin her satırı girintile gerekir.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet1102.fs)]

Bir ad yerine yalnızca, adları içeren bir desen belirtilebilir, aşağıdaki kodda gösterildiği gibi bir tanımlama.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet1103.fs)]

*Gövde ifadesi* ifade adları kullanılır. Gövde ifadesi ilk karakteri ile tam olarak ayarlamak için satır girintili kendi satırında görünür `let` anahtar sözcüğü:

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet1104.fs)]

A `let` bağlama görünebilir Modül düzeyinde bir sınıf türünün tanımında veya yerel kapsamlar, bir işlev tanımı gibi. A `let` bağlama en üst düzeyinde bir modül veya sınıf türünde bir gövde ifadesi olması gerekmez, ancak diğer kapsam düzeylerinde gövde ifadesi gereklidir. Bağımlı adlar, tanımı, ancak önce herhangi bir noktada değil noktadan sonra kullanılabilir `let` aşağıdaki kodda gösterildiği gibi bağlama görünür.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet1105.fs)]

## <a name="function-bindings"></a>İşlev bağlamaları

Aşağıdaki kodda gösterildiği gibi işlev bağlamaları işlev adı ve parametreler dahil dışında işlev bağlamaları değeri bağlamaları için kuralları izleyin.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet1106.fs)]

Genel olarak, bir kayıt düzeni deseni gibi kalıplar Parametreler şunlardır:

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet1107.fs)]

A `let` ifade bağlama değeri son ifade olarak değerlendirir. Bu nedenle, aşağıdaki kod örneği, değeri içinde `result` gelen hesaplanan `100 * function3 (1, 2)`, hangi değerlendirir `300`.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet1109.fs)]

Daha fazla bilgi için [işlevleri](index.md).

## <a name="type-annotations"></a>Tür ek açıklamaları

Tür parametreleri için parantez içinde tüm kapalı bir tür adını ardından bir iki nokta üst üste (:) dahil ederek belirtebilirsiniz. Dönüş değerinin türü iki nokta üst üste ve türdeki sonra son parametre ekleyerek de belirtebilirsiniz. İçin tam bir tür ek açıklamalar `function1`, parametre türleri olarak tamsayı ile şu şekilde olacaktır.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet1108.fs)]

Açık tür parametre bulunmadığında tür çıkarımı işlevlerin parametre türlerini belirlemek için kullanılır. Bu, otomatik olarak genel bir parametre türü genelleştiriliyor içerebilir.

Daha fazla bilgi için [otomatik Genelleştirme](../generics/automatic-generalization.md) ve [tür çıkarımı](../type-inference.md).

## <a name="let-bindings-in-classes"></a>Sınıflardaki let Bağlamaları

A `let` bağlama, sınıf türünde ancak yapısı veya kayıt türü görünebilir. Sınıfı, bir sınıf türünde bağlama bir let kullanmak için bir birincil oluşturucuya sahip olmalıdır. Oluşturucu parametresi, sınıf tanımında tür adından sonra yer almalıdır. A `let` özel alanlar ve üyeleri sınıf türüne ve ile birlikte bir sınıf türü bağlamasında tanımlar `do` türündeki bağlama türü için birincil Oluşturucu için kod oluşturur. Aşağıdaki kod örnekleri, bir sınıf Göster `MyClass` özel alanlara sahip `field1` ve `field2`.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet1110.fs)]

Kapsamlar `field1` ve `field2` içinde bildirilen türü sınırlıdır. Daha fazla bilgi için [ `let` sınıflardaki bağlamaları](../members/let-bindings-in-classes.md) ve [sınıfları](../classes.md).

## <a name="type-parameters-in-let-bindings"></a>Tür parametrelerinde let bağlamaları

A `let` bağlama Modül düzeyinde bir türü veya bir hesaplama ifadesi açık tür parametrelerine sahip olabilir. Bir işlev tanımı içinde bağlama gibi bir ifadede bir let Tür parametrelerine sahip olamaz. Daha fazla bilgi için [genel türler](../generics/index.md).

## <a name="attributes-on-let-bindings"></a>Özniteliklerinde let bağlamaları

Öznitelikleri uygulanabilir çok en üst düzey `let` bağlamaları aşağıdaki kodda gösterildiği gibi bir modülde.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet1111.fs)]

## <a name="scope-and-accessibility-of-let-bindings"></a>Kapsamı ve erişilebilirliğini Let bağlamaları

Let bağlama ile bildirilen bir varlığa kapsamını içeren kısmı sınırlıdır kapsamını (bir işlev, modül, dosya veya sınıf gibi) bağlama göründükten sonra. Bu nedenle, let bağlama bir kapsamın içine bir ad tanıtır söylenebilir. Let bağlamaları modülünde modülünün genel işlevlere derlenmiş modülü erişilebilir olduğu sürece bir modülde let ilişkili değer veya işlevi bir modül istemcilere erişilebilir. Aksine, sınıfa bir sınıfta let bağlamaları özeldir.

Normalde, modüllerdeki İşlevler, istemci kodu tarafından kullanıldığında modülünün adı ile nitelenmelidir. Örneğin, bir modül, `Module1` bir işlev `function1`, kullanıcıların belirtirsiniz `Module1.function1` işleve başvurmak için.

Bir modülün kullanıcılar, içeri aktarma bildirimi, modül adı tarafından yetkili olmadan bu modülündeki işlevleri kullanmak için kullanılabilir hale getirmek için kullanabilir. Yalnızca bahsedilen örnekte, modülün kullanıcılar bu durumda modül içeri aktarma bildirimi açık kullanarak açabilirsiniz `Module1` ve bundan sonra başvurmak `function1` doğrudan.

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

Bazı modüller özniteliğine sahip [RequireQualifiedAccess](https://msdn.microsoft.com/library/8b9b6ade-0471-4413-ac5d-638cd0de5f15), yani ortaya işlevleri modül adı ile nitelenmelidir. Örneğin, F# List Modülü, bu öznitelik vardır.

Modüller ve erişim denetimi hakkında daha fazla bilgi için bkz. [modülleri](../modules.md) ve [erişim denetimi](../access-control.md).

## <a name="see-also"></a>Ayrıca bkz.

- [İşlevler](index.md)
- [`let` Sınıflardaki bağlamaları](../members/let-bindings-in-classes.md)
