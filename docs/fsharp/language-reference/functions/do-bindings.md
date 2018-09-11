---
title: do Bağlamaları (F#)
description: "F # 'bağlaması yapma' bir işlev veya değer tanımlamadan kod yürütmek için nasıl kullanıldığını öğrenin."
ms.date: 05/16/2016
ms.openlocfilehash: 78dbf8da0fe40b5af566ad98693df1109eede7e4
ms.sourcegitcommit: 8c2ece71e54f46aef9a2153540d0bda7e74b19a9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/11/2018
ms.locfileid: "44353102"
---
# <a name="do-bindings"></a>do Bağlamaları

A `do` bağlama, bir işlev veya değer tanımlamadan kod yürütmek için kullanılır. Ayrıca, bağlamaları olabilir misiniz sınıflarda kullanıldığında, bkz: [ `do` sınıflardaki bağlamaları](../members/do-bindings-in-classes.md).

## <a name="syntax"></a>Sözdizimi

```fsharp
[ attributes ]
[ do ]expression
```

## <a name="remarks"></a>Açıklamalar

Kullanım bir `do` bir işlev veya değer tanımı bağımsız olarak kod yürütmek istediğiniz zaman bağlama. İfade bir `do` bağlama döndürmelidir `unit`. En üst düzey bir kod `do` bağlama modülü başlatıldığında yürütülür. Anahtar sözcüğü `do` isteğe bağlıdır.

Öznitelikleri uygulanabilir için üst düzey `do` bağlama. Örneğin, programınız COM birlikte çalışma kullanıyorsa, uygulamak isteyebilirsiniz `STAThread` programınıza özniteliği. Bir öznitelik kullanarak bunu yapabilirsiniz bir `do` aşağıdaki kodda gösterildiği gibi bağlama.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet201.fs)]

## <a name="see-also"></a>Ayrıca bkz.

- [F# Dili Başvurusu](../index.md)
- [İşlevler](index.md)
