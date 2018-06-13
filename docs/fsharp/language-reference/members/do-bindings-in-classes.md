---
title: Sınıflardaki do Bağlamaları (F#)
description: "F # 'nesne oluşturulduğunda veya türü ilk kullanıldığında eylemler gerçekleştiren bir sınıf tanımı bağlamasında do' kullanmayı öğrenin."
ms.date: 05/16/2016
ms.openlocfilehash: 779b33c44b1518135f4c7f270173ec8124fec101
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33565197"
---
# <a name="do-bindings-in-classes"></a>Sınıflardaki do Bağlamaları

A `do` sınıf tanımında bağlama nesnesi oluşturulduğunda veya bir statik eylemleri gerçekleştirir `do` bağlama, türü ilk kullanıldığında.


## <a name="syntax"></a>Sözdizimi

```fsharp
[static] do expression
```

## <a name="remarks"></a>Açıklamalar
A `do` bağlama görünür ile birlikte veya sonra `let` bağlamaları ancak bir sınıf tanımı üye tanımlarında önce. Ancak `do` anahtar sözcüğü için isteğe bağlı `do` bağlamaları Modül düzeyinde onu için isteğe bağlı değil `do` bir sınıf tanımı bağlama.

Her nesne herhangi yapımı için belirtilen tür, statik olmayan `do` bağlamalar ve statik olmayan `let` bağlamaları sınıf tanımında göründükleri sırada çalıştırılır. Birden çok `do` bağlamaları bir türüne meydana gelebilir. Statik olmayan `let` bağlamalar ve statik olmayan `do` bağlamaları birincil Oluşturucusu gövdesi haline gelir. Statik olmayan kodda `do` bağlamaları bölümü başvuru birincil Oluşturucusu parametreler ve değerler veya tanımlanan işlevler `let` bağlamaları bölümü.

Statik olmayan `do` bağlamaları, sınıf üyeleri erişebilir, sınıf tarafından tanımlanan bir kendi kendini tanımlayıcısı olduğu sürece bir `as` başlık ve tüm bu üyeler kullanımlarını sınıfı için kendi kendine tanımlayıcısı ile tam olarak uzun sınıfı anahtar sözcük.

Çünkü `let` bağlamaları başlatma özel alanları genellikle üyeleri beklendiği gibi davranır güvence altına almak gerekli olan, bir sınıfın `do` bağlamaları sonra genellikle konur `let` kod, böylece bağlamaları `do` bağlama can tamamen başlatılmış bir nesneyle yürütün. Kodunuzu başlatılması tamamlanmadan önce bir üyesini kullanmaya çalışırsa, bir InvalidOperationException tetiklenir.

Statik `do` bağlamaları statik üyeler başvuru veya kapsayan alanların sınıf ancak üyeleri veya alanlar örneği değil. Statik `do` bağlamaları statik Başlatıcı sınıfı ilk kullanılmadan önce yürütülecek garanti sınıfının bir parçası haline gelir.

Öznitelikler için yoksayılır `do` türlerinde bağlar. Bir öznitelik olarak yürütülen kodu için gerekli olup olmadığını bir `do` bağlama, bunun birincil oluşturucuya uygulanması gerekir.

Aşağıdaki kodda bir sınıf statik sahip `do` bağlama ve statik olmayan `do` bağlama. Nesne iki parametreye sahip bir kurucusunun `a` ve `b`, ve iki özel alan tanımlanmış `let` sınıfı için bağlamalar. İki özellik de tanımlanabilir. Bu statik olmayan kapsamda tümü `do` bağlamaları bölümünde, bu değerleri yazdırır satırı ile gösterildiği gibi.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3101.fs)]

Çıktı aşağıdaki gibidir:

```console
Initializing MyType.
Initializing object 1 2 2 4 8 16
```

## <a name="see-also"></a>Ayrıca Bkz.
[Üyeler](index.md)

[Sınıflar](../classes.md)

[Oluşturucular](constructors.md)

[`let` Sınıflardaki bağlamaları](let-bindings-in-classes.md)

[`do` Bağlamaları](../functions/do-Bindings.md)
