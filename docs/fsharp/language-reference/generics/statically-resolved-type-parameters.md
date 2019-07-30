---
title: Statik Olarak Çözümlenmiş Tür Parametreleri
description: Statik olarak çözümlenen bir F# tür parametresini nasıl kullanacağınızı öğrenin. Bu, çalışma zamanı yerine derleme sırasında gerçek bir tür ile değiştirilmiştir.
ms.date: 05/16/2016
ms.openlocfilehash: 43ed79b6e5f43a499a27b05e26472b021c455e44
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630589"
---
# <a name="statically-resolved-type-parameters"></a>Statik Olarak Çözümlenmiş Tür Parametreleri

*Statik olarak çözümlenen tür parametresi* , çalışma zamanı yerine derleme sırasında gerçek tür ile değiştirilmiş bir tür parametresidir. Önünde bir şapka (^) simgesi gelir.

## <a name="syntax"></a>Sözdizimi

```
ˆtype-parameter
```

## <a name="remarks"></a>Açıklamalar

F# Dilde iki farklı türde tür parametresi vardır. İlk tür standart genel tür parametresidir. Bunlar, ve `'T` `'U`' de olduğu gibi bir kesme işareti (') ile gösterilir. Bunlar, diğer .NET Framework dillerdeki genel tür parametrelerine eşdeğerdir. Diğer tür statik olarak çözümlenir ve ve `^T` `^U`' de olduğu gibi bir giriş işareti simgesiyle belirtilir.

Statik olarak çözümlenen tür parametreleri, genellikle bir tür bağımsız değişkeninin kullanılabilmesi için belirli bir üyeye veya üyelere sahip olması gerektiğini belirtmenize imkan tanıyan kısıtlamalar olan üye kısıtlamalarıyla birlikte faydalıdır. Normal genel tür parametresi kullanarak bu tür bir kısıtlamayı oluşturmanın bir yolu yoktur.

Aşağıdaki tabloda, iki tür parametre türüyle benzerlik ve farklar özetlenmektedir.

|Özellik|Genel|Statik olarak çözümlendi|
|-------|-------|-------------------|
|Sözdizimi|`'T`, `'U`|`^T`, `^U`|
|Çözümleme süresi|Çalışma zamanı|Derleme zamanı|
|Üye kısıtlamaları|Üye kısıtlamalarıyla kullanılamaz.|, Üye kısıtlamalarıyla kullanılabilir.|
|Kod oluşturma|Standart genel tür parametrelerine sahip bir tür (veya yöntem), tek bir genel tür veya yöntemin oluşturulmasına neden olur.|Her bir tür için bir tane olmak üzere tür ve yöntemlerin birden çok örneği oluşturulur.|
|Türlerle kullanma|Türleri üzerinde kullanılabilir.|Türler üzerinde kullanılamaz.|
|Satır içi işlevlerle kullanma|Hayır. Bir satır içi işlev standart bir genel tür parametresiyle parametreleştirilemez.|Evet. Statik olarak çözümlenen tür parametreleri, satır içi olmayan işlevlerde veya metotlarda kullanılamaz.|

Birçok F# Çekirdek Kitaplığı işlevi, özellikle işleçler, statik olarak çözümlenen tür parametrelerine sahiptir. Bu işlevler ve işleçler satır içine alınır ve sayısal hesaplamalar için verimli kod oluşturulmasına neden olur.

Ve statik olarak çözümlenen tür parametrelerine sahip diğer işlevleri kullanan satır içi Yöntemler ve işlevler, statik olarak çözümlenen tür parametrelerinin kendisini de kullanabilir. Genellikle, tür çıkarımı statik olarak çözümlenen tür parametrelerine sahip olan satır içi işlevleri tür çıkarıcılar. Aşağıdaki örnek, statik olarak çözümlenen bir tür parametresine sahip olacak şekilde gösterilen bir işleç tanımını gösterir.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-3/snippet401.fs)]

Çözümlenme türü `(+@)` , hem hem de `(*)`' nin, her `(+)` ikisi de statik olarak çözümlenen tür parametrelerinde üye kısıtlamalarını çıkarmasına neden olan tür çıkarımı ' nın kullanımını temel alır. Çözülen tür, yorumlayıcıda F# gösterildiği gibi aşağıdaki gibidir.

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

4,1 ile F# başlayarak statik olarak çözümlenen tür parametre imzaları içinde somut tür adları da belirtebilirsiniz.  Dilin önceki sürümlerinde tür adı aslında derleyici tarafından çıkarsanamıyor, ancak İmzada belirtilenemez.  F# 4,1 itibariyle statik olarak çözümlenen tür parametre imzaları içinde somut tür adları da belirtebilirsiniz. Örnek buradadır:

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
