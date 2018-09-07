---
title: Statik Olarak Çözümlenmiş Tür Parametreleri (F#)
description: "Bir F #'ı kullanmayı öğrenin, derleme zamanında yerine çalışma zamanında gerçek türle değiştirilen statik olarak çözümlenmiş tür parametresi."
ms.date: 05/16/2016
ms.openlocfilehash: 747917fef2746dcbf363ef4b717ace5e47229800
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44080247"
---
# <a name="statically-resolved-type-parameters"></a>Statik Olarak Çözümlenmiş Tür Parametreleri

A *statik olarak çözümlenmiş tür parametresi* derleme zamanında yerine çalışma zamanında gerçek türle değiştirilen bir parametre türüdür. Bunlar, bir şapka (^) simgesi öncesinde olur.

## <a name="syntax"></a>Sözdizimi

```
ˆtype-parameter
```

## <a name="remarks"></a>Açıklamalar

F # dilinde iki farklı türden tür parametresi vardır. Standart genel tür parametresini ilk türüdür. Bu kesme işareti (') olarak gösterilen `'T` ve `'U`. Bunlar, diğer .NET Framework dillerinde genel tür parametreleri için eşdeğerdir. Diğer tür istatistiksel olarak çözümlenir ve gibi bir şapka karakteri ile belirtilir `^T` ve `^U`.

Statik çözülen tür parametrelerinin birlikte bir tür bağımsız değişkeni belirli bir üyeye veya belirli üyelere kullanılabilmesi için sahip olması gerektiğini belirtmenize izin veren kısıtlamalar olan üye kısıtlamalarıyla öncelikle yararlıdır. Normal genel tür parametre kullanarak bu tür bir kısıtlama oluşturmanın hiçbir yolu yoktur.

İki tür parametre çeşidi arasındaki benzerlikler ve aşağıdaki tabloda özetlenmiştir.

|Özellik|Genel|Statik olarak çözümlenmiş|
|-------|-------|-------------------|
|Sözdizimi|`'T`, `'U`|`^T`, `^U`|
|Çözümleme süresi|Çalışma zamanı|Derleme zamanı|
|Üye kısıtlamaları|Üye kısıtlamaları ile kullanılamaz.|Üye kısıtlamaları ile kullanılabilir.|
|Kod oluşturma|Standart genel türdeki parametrelere sahip bir türü (veya yöntem), bir tek genel tür veya yöntemin nesildeki sonuçlanır.|Türlerin ve yöntemlerin birden çok örnek oluşumu oluşturulur, biri her tür için gereklidir.|
|Türler ile kullanın|Türlerde kullanılabilir.|Türlerde kullanılamaz.|
|Satır içi işlevleri ile kullanın|Hayır. Satır içi işlev bir standart genel tür parametreyle parametreleştirilemez.|Evet. İşlevleri veya satır içi olmayan yöntemleri statik olarak çözümlenmiş tür parametreleri kullanılamaz.|

Çoğu F # çekirdek kitaplığı işlevinde, özellikle işleçlerde, statik olarak çözümlenmiş tür parametreleri. Bu işlevler ve işleçler satır içi ve sayısal hesaplamalar için etkili kod oluşturmayla sonuçlanır.

Satır içi yöntemler ve işleçleri kullanan ya da statik olarak çözümlenmiş tür parametreleri, diğer işlevleri kullanan işlevler statik çözülen tür parametrelerinin kendilerini de kullanabilirsiniz. Genellikle, tür çıkarımı, statik olarak çözümlenmiş tür parametreleri için gibi satır içi işlevleri çıkarır. Aşağıdaki örnek, statik olarak çözümlenmiş tür parametresi için ortaya çıkan bir işleç tanımını göstermektedir.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-3/snippet401.fs)]

Çözümlenen türünü `(+@)` kullanımına dayalı `(+)` ve `(*)`hem statik olarak çözülen tür parametreler üzerinde üye sınırlamalarını çıkarmak çıkarım neden olan. Çözümlenen tür F # yorumlayıcıda gösterildiği gibidir.

```fsharp
^a -> ^c -> ^d
when (^a or ^b) : (static member ( + ) : ^a * ^b -> ^d) and
(^a or ^c) : (static member ( * ) : ^a * ^c -> ^b)
```

Çıktı aşağıdaki gibidir:

```
2
1.500000
```

F # 4.1 ile başlayarak, somut tür adları statik olarak çözümlenen tür parametresi imzaları de belirtebilirsiniz.  Dilin önceki sürümlerinde, tür adı derleyici tarafından gerçekten çıkarılan, ancak gerçekte imzasında belirlenemedi.  F # 4.1 itibariyle, somut tür adları statik olarak çözümlenen tür parametresi imzaları de belirtebilirsiniz. Örnek buradadır:

```fsharp
let inline konst x _ = x

type CFunctor() = 
    static member inline fmap (f: ^a -> ^b, a: ^a list) = List.map f a
    static member inline fmap (f: ^a -> ^b, a: ^a option) =
        match a with
        | None -> None
        | Some x -> Some (f x)

    // default implementation of replace
    static member inline replace< ^a, ^b, ^c, ^d, ^e when ^a :> CFunctor and (^a or ^d): (static member fmap: (^b -> ^c) * ^d -> ^e) > (a, f) =
        ((^a or ^d) : (static member fmap : (^b -> ^c) * ^d -> ^e) (konst a, f))

    // call overridden replace if present
    static member inline replace< ^a, ^b, ^c when ^b: (static member replace: ^a * ^b -> ^c)>(a: ^a, f: ^b) =
        (^b : (static member replace: ^a * ^b -> ^c) (a, f))

let inline replace_instance< ^a, ^b, ^c, ^d when (^a or ^c): (static member replace: ^b * ^c -> ^d)> (a: ^b, f: ^c) =
        ((^a or ^c): (static member replace: ^b * ^c -> ^d) (a, f))

// Note the concrete type 'CFunctor' specified in the signature
let inline replace (a: ^a) (f: ^b): ^a0 when (CFunctor or  ^b): (static member replace: ^a *  ^b ->  ^a0) =
    replace_instance<CFunctor, _, _, _> (a, f)
```

## <a name="see-also"></a>Ayrıca bkz.

- [Genel Türler](index.md)
- [Tür Çıkarımı](../type-inference.md)
- [Otomatik Genelleştirme](automatic-generalization.md)
- [Kısıtlamalar](constraints.md)
- [Satır İçi İşlevler](../functions/inline-functions.md)
