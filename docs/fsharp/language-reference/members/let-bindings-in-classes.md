---
title: Sınıflardaki let Bağlamaları (F#)
description: "Sınıf tanımı'nda 'let' bağlamaları kullanarak özel alanlar ve F # sınıfları için özel işlevler tanımlamak öğrenin."
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: dotnet-fsharp
ms.devlang: fsharp
ms.openlocfilehash: c4511a541403dde517acaf902e86de8d48f13781
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2018
---
# <a name="let-bindings-in-classes"></a>Sınıflardaki let Bağlamaları

Kullanarak özel alanlar ve F # sınıfları için özel işlevler tanımlayabilirsiniz `let` sınıf tanımında bağlar.


## <a name="syntax"></a>Sözdizimi

```fsharp
// Field.
[static] let [ mutable ] binding1 [ and ... binding-n ]

// Function.
[static] let [ rec ] binding1 [ and ... binding-n ]
```

## <a name="remarks"></a>Açıklamalar
Önceki sözdizimi sınıf başlık ve devralma bildirimleri sonra ancak herhangi bir üye tanımları önce görünür. Söz dizimi, gibi `let` sınıfları, ancak bir sınıf içinde tanımlanan adlar dışında bağlamaları sınıfa sınırlı bir kapsam vardır. A `let` özel alan veya verileri açığa işlevi; bağlama oluşturur veya işlevleri genel olarak, bildirme bir özellik ya da bir üye yöntemi.

A `let` bağlaması değil örneği statik olarak adlandırılan `let` bağlama. Örnek `let` bağlamaları nesneler oluşturulduğunda yürütün. Statik `let` bağlamaları statik Başlatıcı türü ilk kullanılmadan önce yürütülecek garanti sınıf için bir parçasıdır.

Örnek içindeki kod `let` bağlamaları birincil Oluşturucusu 's parametrelerini kullanabilirsiniz.

Öznitelikler ve erişilebilirlik değiştiricileri verilmez üzerinde `let` sınıflardaki bağlar.

Aşağıdaki kod örneğinde çeşitli türlerde göstermeye `let` sınıflardaki bağlar.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3001.fs)]

Çıktı aşağıdaki gibidir:

```
10 52 1 204
```

## <a name="alternative-ways-to-create-fields"></a>Alanları oluşturmak için alternatif yöntemler
Aynı zamanda `val` özel alanı oluşturmak için anahtar sözcüğü. Kullanırken `val` anahtar sözcüğü, alanın değil verilen bir değer nesnesi oluşturulur, ancak bunun yerine varsayılan bir değerle başlatılır. Daha fazla bilgi için bkz: [açık alanlar: val anahtar sözcüğü](explicit-fields-the-val-keyword.md).

Ayrıca özel alanlar bir sınıfta bir üye tanımı kullanılarak ve anahtar sözcüğü ekleyerek tanımlayabilirsiniz `private` tanımı. Bu üye erişilebilirliğini kodunuzu yeniden yazma işlemi değiştirmek bekliyorsanız yararlı olabilir. Daha fazla bilgi için bkz: [erişim denetimi](../access-control.md).

## <a name="see-also"></a>Ayrıca Bkz.
[Üyeler](index.md)

[`do` Sınıflardaki bağlamaları](do-bindings-in-classes.md)

[`let` Bağlamaları](../functions/let-bindings.md)
