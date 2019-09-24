---
title: Sınıflardaki let Bağlamaları
description: Sınıf tanımındaki ' Let ' bağlamalarını kullanarak sınıflar için F# özel alanları ve özel işlevleri tanımlamayı öğrenin.
ms.date: 05/16/2016
ms.openlocfilehash: 1366ab8f1f4f606fe5947a8fc4df10de49346b3e
ms.sourcegitcommit: 56f1d1203d0075a461a10a301459d3aa452f4f47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2019
ms.locfileid: "71216522"
---
# <a name="let-bindings-in-classes"></a>Sınıflardaki let Bağlamaları

Sınıf tanımındaki bağlamaları kullanarak F# `let` sınıflar için özel alanlar ve özel işlevler tanımlayabilirsiniz.

## <a name="syntax"></a>Sözdizimi

```fsharp
// Field.
[static] let [ mutable ] binding1 [ and ... binding-n ]

// Function.
[static] let [ rec ] binding1 [ and ... binding-n ]
```

## <a name="remarks"></a>Açıklamalar

Önceki sözdizimi, sınıf başlığı ve devralma bildirimlerinden sonra, tüm üye tanımlarından önce görüntülenir. Söz dizimi sınıfların dışındaki `let` bağlamalardan gibidir, ancak bir sınıfta tanımlanan adların, sınıfıyla sınırlı bir kapsamı vardır. `let` Bağlama, verileri veya işlevleri herkese açık bir şekilde göstermek için bir özel alan veya işlev oluşturur; bir özellik veya bir üye yöntemi bildirir.

Statik `let` olmayan bir bağlama örnek `let` bağlama olarak adlandırılır. Nesneler `let` oluşturulduğunda örnek bağlamaları yürütülür. Statik `let` bağlamalar, türü ilk kullanılmadan önce yürütülmesi garanti edilen, sınıfının statik başlatıcısının bir parçasıdır.

Örnek `let` bağlamaların içindeki kod, birincil oluşturucunun parametrelerini kullanabilir.

Sınıflardaki bağlamalarda `let` özniteliklere ve erişilebilirlik değiştiricilerine izin verilmez.

Aşağıdaki kod örnekleri sınıflardaki çeşitli `let` bağlama türlerini gösterir.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet3001.fs)]

Çıktı aşağıdaki gibidir:

```console
10 52 1 204
```

## <a name="alternative-ways-to-create-fields"></a>Alan oluşturmak için alternatif yollar

Özel bir alan oluşturmak için `val` anahtar sözcüğünü de kullanabilirsiniz. `val` Anahtar sözcüğü kullanılırken, nesne oluşturulduğunda alana bir değer verilmez, bunun yerine varsayılan bir değerle başlatılır. Daha fazla bilgi için bkz [. açık alanlar: Val anahtar sözcüğü](explicit-fields-the-val-keyword.md).

Ayrıca, bir üye tanımı kullanarak ve tanımına anahtar sözcüğünü `private` ekleyerek bir sınıfta özel alanlar tanımlayabilirsiniz. Bu, kodunuzu yeniden yazmadan bir üyenin erişilebilirliğini değiştirmeniz beklendiğinde yararlı olabilir. Daha fazla bilgi için bkz. [Access Control](../access-control.md).

## <a name="see-also"></a>Ayrıca bkz.

- [Üyeler](index.md)
- [`do`Sınıflarda bağlamalar](do-bindings-in-classes.md)
- [`let`Lara](../functions/let-bindings.md)
