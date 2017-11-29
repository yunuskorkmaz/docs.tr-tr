---
title: "Özyinelemeli İşlevler: rec Anahtar Sözcüğü (F#)"
description: "F # 'rec' anahtar sözcüğü özyinelemeli bir işlev tanımlamak için 'let' anahtar sözcüğü ile nasıl kullanıldığı hakkında bilgi edinin."
keywords: "Visual f #, f # işlevsel programlama"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 1a95639f-9bfe-4f1d-a5e2-246d1d37776e
ms.openlocfilehash: b837d2c0f8e2b1d28980620103097ccc8345c098
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="recursive-functions-the-rec-keyword"></a>Özyinelemeli İşlevler: rec Anahtar Sözcüğü

`rec` Anahtar sözcüğü ile birlikte kullanıldığında `let` özyinelemeli bir işlev tanımlamak için anahtar sözcüğü.


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
Özyinelemeli İşlevler, kendileri arama işlevleri açıkça F # dilinde tanımlanır. Bu tanımlanıyorsa tanımlayıcı işlevi kapsamında kullanılabilmesini sağlar.

Aşağıdaki kod hesaplar bir özyinelemeli işlev gösterir  *n* th Fibonacci numarası.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet4001.fs)]

>[!NOTE]
Önceden hesaplanan değerler recomputation içerdiğinden, gibi Yukarıdaki kod bellek ve işlemci süresini kayıp uygulamadır.


Örtük olarak özyinelemeli türü içinde yöntemleridir; eklemeye gerek yoktur `rec` anahtar sözcüğü. Sınıflardaki let bağlamaları örtülü olarak özyinelemeli değildir.


## <a name="mutually-recursive-functions"></a>Karşılıklı özyinelemeli İşlevler
Bazen işlevlerdir *karşılıklı özyinelemeli*, çağrıları burada bir işlevi çağırır sırayla çağrıları herhangi bir sayı ile ilk çağıran başka arasında bir daire form anlamına gelir. Bu tür işlevler bir araya tanımlamalısınız `let` kullanarak binding `and` birbirine bağlamak için anahtar sözcüğü.

Aşağıdaki örnekte iki birbirini gösterir özyinelemeli işlevler.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet4002.fs)]

## <a name="see-also"></a>Ayrıca Bkz.
[İşlevler](index.md)
