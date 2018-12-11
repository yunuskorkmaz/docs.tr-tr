---
title: 'Özyinelemeli İşlevler: Rec anahtar sözcüğü (F#)'
description: Bilgi nasıl F# 'rec' anahtar sözcüğü, bir özyinelemeli işlev tanımlamak için 'let' anahtar sözcüğü ile kullanılır.
ms.date: 05/16/2016
ms.openlocfilehash: 0db3ed7f85a1380654f2827b4773985b661589c7
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53127738"
---
# <a name="recursive-functions-the-rec-keyword"></a>Özyinelemeli İşlevler: Rec anahtar sözcüğü

`rec` Anahtar sözcüğü ile birlikte kullanılır `let` özyinelemeli işlev tanımlamak için anahtar sözcüğü.

## <a name="syntax"></a>Sözdizimi

```fsharp
// Recursive function:
let rec function-nameparameter-list =
function-body

// Mutually recursive functions:
let rec function1-nameparameter-list =
function1-body
and function2-nameparameter-list =
function2-body
...
```

## <a name="remarks"></a>Açıklamalar

Özyinelemeli İşlevler, kendileri çağıran işlevler açıkça tanımlanır F# dili. Bu tanımlanıyorsa tanımlayıcısı işlev kapsamında kullanılabilmesini sağlar.

Aşağıdaki kod hesaplar bir özyinelemeli işlev göstermektedir *n*<sup>th</sup> Fibonacci sayı.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet4001.fs)]

> [!NOTE]
> Yeniden hesaplama yapmayı daha önce hesaplanan değerler içerdiğinden, yukarıdaki kod bellek ve işlemci zamanı kısıp uygulamadır.

Yöntem türü içinde dolaylı olarak özyinelemelidir; eklemenize gerek yoktur `rec` anahtar sözcüğü. Sınıflardaki let bağlamaları örtülü olarak özyinelemeli değildir.

## <a name="mutually-recursive-functions"></a>Karşılıklı özyinelemeli İşlevler

Bazen işlevlerdir *karşılıklı özyinelemeli*, çağrıları burada bir işlevi çağırır sırayla çağrıları herhangi bir sayıda ile ilk çağıran başka arasında bir daire, form anlamına gelir. Bu tür işlevleri bir araya tanımlamalısınız `let` kullanarak binding `and` birbirine bağlamak için anahtar sözcüğü.

Aşağıdaki örnek iki birbirini gösterir özyinelemeli işlevler.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet4002.fs)]

## <a name="see-also"></a>Ayrıca bkz.

- [İşlevler](index.md)
