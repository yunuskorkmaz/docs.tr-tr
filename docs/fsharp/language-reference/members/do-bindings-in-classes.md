---
title: Sınıflardaki do Bağlamaları
description: Nesne oluşturulduğunda veya tür ilk F# kullanıldığında eylemler gerçekleştiren bir sınıf tanımında ' do ' bağlamayı nasıl kullanacağınızı öğrenin.
ms.date: 05/16/2016
ms.openlocfilehash: ced4f1bb17d9e23bf51cc79b5a275cc334cca013
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68627579"
---
# <a name="do-bindings-in-classes"></a>Sınıflardaki do Bağlamaları

Bir sınıf tanımındaki `do` bağlama,nesneoluşturulduğundaveyabirstatikbağlamaiçintürilk`do` kullanıldığında eylemler gerçekleştirir.

## <a name="syntax"></a>Sözdizimi

```fsharp
[static] do expression
```

## <a name="remarks"></a>Açıklamalar

Bağlama bağlamalarla birlikte veya sonra `let` , ancak bir sınıf tanımındaki üye tanımlarından önce görüntülenir. `do` Anahtar sözcüğü, modül düzeyindeki bağlamalar `do` için isteğe bağlı olsa da, bir sınıf tanımındaki bağlamalar için `do` isteğe bağlı değildir. `do`

Verili herhangi bir türdeki her nesnenin oluşturulması için, statik `do` olmayan bağlamalar ve statik `let` olmayan bağlamalar, sınıf tanımında göründükleri sırada yürütülür. Tek `do` bir türde birden çok bağlama meydana gelebilir. Statik `let` olmayan bağlamalar ve statik `do` olmayan bağlamalar, birincil oluşturucunun gövdesi olur. Statik `do` olmayan bağlamalar bölümündeki kod, birincil Oluşturucu parametrelerine ve `let` bağlamalar bölümünde tanımlanan herhangi bir değere veya işleve başvurabilir.

Statik `do` olmayan bağlamalar, sınıf başlığında bir `as` anahtar sözcük tarafından tanımlanan bir kendine tanımlayıcı olduğu sürece ve bu üyelerin tüm kullanımları sınıf için kendi kendine tanımlayıcı ile nitelendirilse de, sınıfın üyelerine erişebilir.

Bağlamalar, genellikle üyelerin `do` beklenen `let` şekilde davranmasını güvence altına almak için gerekli olan bir sınıfın özel alanlarını başlatırken, bağlamaların bağlamadaki `do`kodun `let` tamamen başlatılmış bir nesneyle yürütün. Kodunuz, başlatma tamamlanmadan önce bir üye kullanmayı denerse, bir InvalidOperationException oluşturulur.

Statik `do` bağlamalar, kapsayan sınıfın statik üyelerine veya alanlarına başvurabilir ancak örnek üye veya alanlar değildir. Statik `do` bağlamalar, sınıfının ilk kullanılmadan önce yürütülmesi garanti edilen, sınıfının statik başlatıcısının bir parçası haline gelir.

Türler içindeki bağlamalar için `do` öznitelikler yok sayılır. Bir `do` bağlamada yürütülen kod için bir öznitelik gerekliyse, birincil oluşturucuya uygulanmalıdır.

Aşağıdaki kodda, bir sınıfta statik `do` bağlama ve statik `do` olmayan bağlama bulunur. Nesnesi iki parametreye `a` sahip bir oluşturucuya sahiptir ve `b`ve iki özel `let` alan, sınıf bağlamalarında tanımlanmıştır. İki özellik de tanımlanmıştır. Bunların hepsi, statik `do` olmayan bağlamalar bölümünde, tüm bu değerleri yazdıran satıra göre gösterildiği gibi kapsamdadır.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet3101.fs)]

Çıktı aşağıdaki gibidir:

```console
Initializing MyType.
Initializing object 1 2 2 4 8 16
```

## <a name="see-also"></a>Ayrıca bkz.

- [Üyeler](index.md)
- [Sınıflar](../classes.md)
- [Oluşturucular](constructors.md)
- [`let`Sınıflarda bağlamalar](let-bindings-in-classes.md)
- [`do`Lara](../functions/do-Bindings.md)
