---
title: do Bağlamaları (F#)
description: "F # 'bağlaması yapma' bir işlevi veya değer tanımlamadan kod yürütmek için nasıl kullanıldığı hakkında bilgi edinin."
ms.date: 05/16/2016
ms.openlocfilehash: 6fd084090a204beab0da1c2deb5b5ae2a86281c8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33562342"
---
# <a name="do-bindings"></a>do Bağlamaları

A `do` bağlama bir işlevi veya değer tanımlamadan kod yürütmek için kullanılır. Ayrıca, bağlamaları olabilir yapmak sınıflarda kullanıldığında, bkz: [ `do` sınıflardaki bağlamaları](../members/do-bindings-in-classes.md).


## <a name="syntax"></a>Sözdizimi

```fsharp
[ attributes ]
[ do ]expression
```

## <a name="remarks"></a>Açıklamalar
Kullanım bir `do` bir işlevi veya değer tanımı bağımsız olarak kod yürütmek istediğinizde bağlama. İfade bir `do` bağlama döndürmelidir `unit`. Kodda bir üst düzey `do` bağlama modül başlatıldığında gerçekleştirilir. Anahtar sözcüğü `do` isteğe bağlıdır.

Öznitelikleri uygulanabilir için üst düzey `do` bağlama. Örneğin, programınızı COM birlikte çalışma kullanıyorsa, uygulamak isteyebilirsiniz `STAThread` programınıza özniteliği. Bir öznitelik kullanarak bunu yapabilirsiniz bir `do` aşağıdaki kodda gösterildiği gibi bağlama.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet201.fs)]
    
## <a name="see-also"></a>Ayrıca Bkz.
[F# Dili Başvurusu](../index.md)

[İşlevler](index.md)

