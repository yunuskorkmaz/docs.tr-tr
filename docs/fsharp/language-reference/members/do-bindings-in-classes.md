---
title: Sınıflardaki do Bağlamaları (F#)
description: "F # 'nesne oluşturulduğunda veya türü ilk defa kullanıldığında eylemler gerçekleştiren bir sınıf tanımı bağlaması yapma' kullanmayı öğrenin."
ms.date: 05/16/2016
ms.openlocfilehash: e54a5bde52bf6973cc338c929ba99e6fd5b53127
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2018
ms.locfileid: "43801547"
---
# <a name="do-bindings-in-classes"></a>Sınıflardaki do Bağlamaları

A `do` nesne oluşturulduğunda veya statik bir sınıf tanımı bağlamasında eylemleri gerçekleştirir `do` bağlamayı türü ilk kez kullanıldığında.

## <a name="syntax"></a>Sözdizimi

```fsharp
[static] do expression
```

## <a name="remarks"></a>Açıklamalar

A `do` bağlama ile birlikte veya sonra görünür `let` bağlamaları, ancak bir sınıf tanımının üye tanımlarında önce. Ancak `do` anahtar sözcüğü için isteğe bağlı `do` bağlamaları Modül düzeyinde bu için isteğe bağlı değil `do` bağlamaları bir sınıf tanımı.

Türü, statik olmayan her nesne herhangi oluşumu için verilen `do` bağlamaları ve statik olmayan `let` bağlamaları, sınıf tanımında göründükleri sırayla yürütülür. Birden çok `do` bağlamaları bir türüne meydana gelebilir. Statik olmayan `let` bağlamaları ve statik olmayan `do` bağlamaları birincil oluşturucusunun gövdesi olur. Statik olmayan kodda `do` bağlamalar bölümü birincil Oluşturucu parametreler ve değerler veya tanımlanan işlevleri başvurabilir `let` bağlamalar bölümü.

Statik olmayan `do` bağlamaları, sınıfın üyelerine erişebilir, sınıf tarafından tanımlanan bir kendi kendini tanımlayıcısı olduğu sürece bir `as` başlık ve bu üyelerin tüm kullanımları sınıfı için kendi kendine tanımlayıcısı ile tam olarak uzun sınıfı anahtar sözcüğü.

Çünkü `let` bağlamaları başlatmak özel alanlar genellikle üyeleri beklendiği gibi davranmaya garanti etmek gerekli olan, bir sınıfın `do` bağlamaları sonra genellikle isimlerine `let` kod, bu nedenle bağlamaları `do` bağlama can tam olarak başlatılmış bir nesneyle yürütün. Kodunuzu başlatılması tamamlanmadan önce bir üyesini kullanın çalışırsa, bir InvalidOperationException ortaya çıkar.

Statik `do` bağlamaları statik üyeleri başvurabilir veya kapsayan alan sınıfının ancak örnek üye veya alan değil. Statik `do` bağlamaları sınıfı ilk kez kullanılmadan önce yürütülecek garanti sınıfı için statik Başlatıcı bir parçası haline gelir.

Öznitelikler için yoksayıldı `do` türlerinde bağlar. Bir öznitelik için yürütülen kodu gerekli olup olmadığını bir `do` bağlama, bunun birincil oluşturucuya uygulanması gerekir.

Aşağıdaki kodda, statik sınıfında `do` bağlama ve statik olmayan `do` bağlama. Nesne iki parametreye sahip bir oluşturucuya sahip `a` ve `b`, ve iki özel alan tanımlanmış `let` bağlamaları sınıfı. İki özellik de tanımlanır. Tüm bunların statik olmayan kapsamda bulunan `do` bağlamalar bölümü, tüm bu değerlere yazdırır çizgiyle gösterildiği gibi.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3101.fs)]

Çıktı aşağıdaki gibidir:

```console
Initializing MyType.
Initializing object 1 2 2 4 8 16
```

## <a name="see-also"></a>Ayrıca bkz.

- [Üyeler](index.md)
- [Sınıflar](../classes.md)
- [Oluşturucular](constructors.md)
- [`let` Sınıflardaki bağlamaları](let-bindings-in-classes.md)
- [`do` Bağlamaları](../functions/do-Bindings.md)
