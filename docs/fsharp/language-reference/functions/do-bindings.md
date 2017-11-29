---
title: "do Bağlamaları (F#)"
description: "F # 'bağlaması yapma' bir işlevi veya değer tanımlamadan kod yürütmek için nasıl kullanıldığı hakkında bilgi edinin."
keywords: "Visual f #, f # işlevsel programlama"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 4c1057a3-3aa1-4b64-b46a-25ffe33f0be9
ms.openlocfilehash: f2563d384b67c005c96c2ff487c786476d385e70
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
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
[F # dili başvurusu](../index.md)

[İşlevler](index.md)

