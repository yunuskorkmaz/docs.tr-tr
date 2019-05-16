---
title: Sınıflardaki let Bağlamaları
description: Özel alanlar ve özel işlevler için tanımlamayı öğrenin F# kullanarak sınıfları 'let' sınıf tanımında bağlar.
ms.date: 05/16/2016
ms.openlocfilehash: 29f843e3e065837a53fd5eb26c79088bc0778c76
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65645181"
---
# <a name="let-bindings-in-classes"></a>Sınıflardaki let Bağlamaları

Özel alanlar ve özel işlevler için tanımlayabileceğiniz F# sınıfları kullanarak `let` sınıf tanımında bağlar.

## <a name="syntax"></a>Sözdizimi

```fsharp
// Field.
[static] let [ mutable ] binding1 [ and ... binding-n ]

// Function.
[static] let [ rec ] binding1 [ and ... binding-n ]
```

## <a name="remarks"></a>Açıklamalar

Önceki sözdizimini, başlık ve devralma sınıf bildirimleri sonra ancak herhangi bir üye tanımı önce görünür. Söz dizimi şu şekildedir gibi `let` bağlamaları sınıfları, ancak bir sınıfta tanımlanan adlar dışında sınıfa sınırlı kapsamı vardır. A `let` bağlama, bir özel alan veya verileri ortaya çıkarmak için işlev; oluşturur veya işlevleri genel olarak, bir özellik veya bir üye yöntem bildirin.

A `let` bağlama değil örneği statik olarak adlandırılan `let` bağlama. Örnek `let` bağlamaları yürütmek nesneler oluşturulduğunda. Statik `let` bağlamaları türü ilk kez kullanılmadan önce yürütülecek garanti sınıfı için statik Başlatıcı bir parçasıdır.

Kod örneği içinde `let` bağlamaları birincil oluşturucunun parametreleri kullanabilirsiniz.

Öznitelikler ve erişilebilirlik değiştiricileri verilmez üzerinde `let` sınıflardaki bağlar.

Aşağıdaki kod örnekleri birkaç türde göstermek `let` sınıflardaki bağlar.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3001.fs)]

Çıktı aşağıdaki gibidir:

```
10 52 1 204
```

## <a name="alternative-ways-to-create-fields"></a>Alanları oluşturmak için alternatif yollar

Ayrıca `val` özel bir alan oluşturmak için anahtar sözcüğü. Kullanırken `val` anahtar sözcüğü, alan verilmemiş bir değer nesnesi oluşturulur, ancak bunun yerine varsayılan bir değerle başlatılır. Daha fazla bilgi için [açık alanlar: Val anahtar sözcüğü](explicit-fields-the-val-keyword.md).

Ayrıca özel alanlar bir sınıfta bir üye tanımı kullanarak ve anahtar sözcüğü ekleyerek tanımlayabilirsiniz `private` tanımına. Bu, kodunuzu yeniden yazma olmadan bir üyenin erişilebilirliğini değiştirmek bekliyorsanız yararlı olabilir. Daha fazla bilgi için [erişim denetimi](../access-control.md).

## <a name="see-also"></a>Ayrıca bkz.

- [Üyeler](index.md)
- [`do` Sınıflardaki bağlamaları](do-bindings-in-classes.md)
- [`let` Bağlamaları](../functions/let-bindings.md)
