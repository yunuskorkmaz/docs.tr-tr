---
title: 'Özyinelemeli İşlevler: Rec anahtar sözcüğü'
description: Bilgi nasıl F# 'rec' anahtar sözcüğü, bir özyinelemeli işlev tanımlamak için 'let' anahtar sözcüğü ile kullanılır.
ms.date: 05/16/2016
ms.openlocfilehash: 9f9c7e1a4468de9551b3852d0e7b4381025b2699
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61941017"
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