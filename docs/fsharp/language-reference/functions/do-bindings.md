---
title: do Bağlamaları (F#)
description: "F # 'bağlaması yapma' bir işlevi veya değer tanımlamadan kod yürütmek için nasıl kullanıldığı hakkında bilgi edinin."
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: dotnet-fsharp
ms.devlang: fsharp
ms.openlocfilehash: 4c63da0c5e2f4130d59f9efa6bc54a55e5fe9fd8
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2018
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

