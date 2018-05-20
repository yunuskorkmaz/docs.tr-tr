---
title: Statik Olarak Çözümlenmiş Tür Parametreleri (F#)
description: 'F # kullanmayı öğrenin gerçek bir türüyle derleme zamanında yerine çalışma zamanında değiştirilir statik olarak çözümlenmiş tür parametresi.'
ms.date: 05/16/2016
ms.openlocfilehash: 12c2af4d9df7ae1e5e77efc9413eb8777459a83c
ms.sourcegitcommit: 22c3c8f74eaa138dbbbb02eb7d720fce87fc30a9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/17/2018
---
# <a name="statically-resolved-type-parameters"></a>Statik Olarak Çözümlenmiş Tür Parametreleri

A *statik olarak çözümlenmiş tür parametresi* gerçek bir türüyle derleme zamanında yerine çalışma zamanında değiştirilir bir tür parametresidir. Bunlar, bir şapka (^) simgesi öncesinde olur.


## <a name="syntax"></a>Sözdizimi

```
ˆtype-parameter
```

## <a name="remarks"></a>Açıklamalar
F # dili, tür parametreleri iki farklı tür vardır. İlk standart genel tür parametresi türüdür. Bunlar kesme işareti (') olarak gösterilen `'T` ve `'U`. Bunlar, diğer .NET Framework dillerde genel tür parametreleri için eşdeğerdir. Diğer türü statik olarak çözümlenmiş ve düzeltme işareti sembolü tarafından olarak belirtilen `^T` ve `^U`.

Statik olarak çözümlenmiş tür parametreleri, tür bağımsız değişkeni belirli bir üye veya üyeleri kullanılması için sahip gerektiğini belirtmenize olanak veren sınırlamalardır üye kısıtlamaları birlikte öncelikle faydalıdır. Normal genel tür parametresi kullanarak bu tür bir kısıtlama oluşturmak için bir yolu yoktur.

Aşağıdaki tabloda benzerlikler ve tür parametreleri iki türleri arasındaki farklar özetlenmektedir.

|Özellik|Genel|Statik olarak çözümlenmiş|
|-------|-------|-------------------|
|Sözdizimi|`'T`, `'U`|`^T`, `^U`|
|Çözümleme süresi|Çalışma zamanı|Derleme zamanı|
|Üye kısıtlamaları|Üye kısıtlamalarıyla kullanılamaz.|Üye kısıtlamaları ile kullanılabilir.|
|Kod oluşturma|Tek genel türü veya yöntemi oluşturma bir türü (veya yöntem) standart genel tür parametreleri ile sonuçlanır.|Birden çok örneklemesi türleri ve yöntemleri üretilir, biri her türü için gereklidir.|
|Türleriyle kullanın|Türlerinde kullanılabilir.|Türleri üzerinde kullanılamaz.|
|Satır içi işlevlerle kullanın|Hayır. Satır içi işlev standart genel tür parametresi ile parametreli olamaz.|Evet. Statik olarak çözümlenmiş tür parametreleri işlevleri veya satır içi olmayan yöntemleri kullanılamaz.|

Birçok F # core kitaplık işlevleri, özellikle de operatörler statik olarak çözümlenmiş tür parametreleri. Bu işlevler ve işleçler satır içi ve verimli kod oluşturma sayısal hesaplamalar için sonuçlanır.

Satır içi yöntemleri ve işleçleri veya statik olarak çözümlenmiş tür parametreleri, diğer işlevleri kullanın işlevleri statik olarak çözümlenmiş tür parametreleri kendileri de kullanabilirsiniz. Genellikle, tür çıkarımı statik olarak çözümlenmiş tür parametreleri gibi satır içi işlevler oluşturur. Aşağıdaki örnek, bir statik olarak çözümlenmiş tür parametreye sahip çıkarımı yapılan bir işleç tanımı gösterilmektedir.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-3/snippet401.fs)]

Çözümlenen türü `(+@)` ikisinin kullanım dayanarak `(+)` ve `(*)`, her iki hangi tür çıkarımı üye statik olarak çözümlenmiş tür parametrelerindeki kısıtlamalar Infer neden olarak. Çözümlenmiş tür F # Yorumlayıcı, gösterildiği gibi gibidir.

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

F # 4.1 ile başlayarak, somut tür adları statik olarak çözümlenmiş tür parametresi imzalarında de belirtebilirsiniz.  Dil önceki sürümlerinde, tür adı derleyici tarafından gerçekten çıkarsanamadı, ancak gerçekte imzası belirlenemedi.  F # 4.1 itibariyle, somut tür adları statik olarak çözümlenmiş tür parametresi imzalarında de belirtebilir. Örnek buradadır:

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

## <a name="see-also"></a>Ayrıca Bkz.
[Genel Türler](index.md)

[Tür Çıkarımı](../type-inference.md)

[Otomatik Genelleştirme](automatic-generalization.md)

[Kısıtlamalar](constraints.md)

[Satır İçi İşlevler](../functions/inline-functions.md)
