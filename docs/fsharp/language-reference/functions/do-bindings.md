---
title: do Bağlamaları
description: Bir işlev veya F# değer tanımlamadan kodu yürütmek için bir ' do ' bağlamasının nasıl kullanıldığını öğrenin.
ms.date: 05/16/2016
ms.openlocfilehash: f98f523296bfaceeda35d4861eafbfeaa5a60c32
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630533"
---
# <a name="do-bindings"></a>do Bağlamaları

Bir `do` bağlama, bir işlev veya değer tanımlamadan kodu yürütmek için kullanılır. Ayrıca, do bağlamaları sınıflarda kullanılabilir, bkz [ `do` . sınıflarda bağlamalar](../members/do-bindings-in-classes.md).

## <a name="syntax"></a>Sözdizimi

```fsharp
[ attributes ]
[ do ]expression
```

## <a name="remarks"></a>Açıklamalar

Kodu bir `do` işlevden veya değer tanımından bağımsız olarak yürütmek istediğinizde bir bağlama kullanın. Bir `do` bağlamadaki ifade döndürmelidir `unit`. Üst düzey `do` bağlamadaki kod, modül başlatıldığında yürütülür. Anahtar sözcüğü `do` isteğe bağlıdır.

Öznitelikler, üst düzey `do` bağlamaya uygulanabilir. Örneğin, programınız com birlikte çalışabilirliği kullanıyorsa, bu `STAThread` özniteliği programınıza uygulamak isteyebilirsiniz. Bunu, aşağıdaki kodda gösterildiği gibi `do` bağlamadaki bir özniteliği kullanarak yapabilirsiniz.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet201.fs)]

## <a name="see-also"></a>Ayrıca bkz.

- [F# Dili Başvurusu](../index.md)
- [İşlevler](index.md)
