---
title: do Bağlamaları
description: Bilgi nasıl bir F# 'do binding' bir işlev veya değer tanımlamadan kod yürütmek için kullanılır.
ms.date: 05/16/2016
ms.openlocfilehash: d29f8557fda06097d2e85748ab6286f0415730b3
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61683385"
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