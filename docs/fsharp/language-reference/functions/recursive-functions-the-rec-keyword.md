---
title: 'Özyinelemeli Işlevler: REC anahtar sözcüğü'
description: "' Rec ' F# anahtar sözcüğünün özyinelemeli bir işlev tanımlamak için ' Let ' anahtar sözcüğüyle nasıl kullanıldığını öğrenin."
ms.date: 05/16/2016
ms.openlocfilehash: 7edaa7206b2109c7b1a405624b9b2330968f9c52
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630655"
---
# <a name="recursive-functions-the-rec-keyword"></a>Özyinelemeli Işlevler: REC anahtar sözcüğü

Anahtar sözcüğü özyinelemeli bir işlev tanımlamak için `let` anahtar sözcüğüyle birlikte kullanılır. `rec`

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

Kendini çağıran işlevler, açıkça F# dilde tanımlanır. Bu, tanımlanmakta olan tanımlayıcıların işlevin kapsamında kullanılabilir olmasını sağlar.

Aşağıdaki kod, *n*<sup>.</sup> fibonaccı numarasını hesaplayan özyinelemeli bir işlevi gösterir.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet4001.fs)]

> [!NOTE]
> Uygulamada, yukarıda yer alan kod, daha önce hesaplanmış değerlerin yeniden hesaplanmasını içerdiğinden, bellek ve işlemci süresinin boşa harcanmasından kaynaklanır.

Yöntemler tür içinde örtük olarak özyinelemeli; `rec` anahtar sözcüğü eklemeye gerek yoktur. Sınıfların içindeki bağlamaların örtülü olarak özyinelemeli olmadığından izin verin.

## <a name="mutually-recursive-functions"></a>Birbirini karşılıklı özyinelemeli Işlevler

Bazen işlevler *birbirini yinelemelidir*, yani bir işlevin bir kez çağrı yaptığı, aralarında herhangi bir sayıda çağrıya sahip olan diğeri çağıran bir daire oluşturur. Bu tür işlevleri bir `let` bağlamada birlikte tanımlamanız gerekir, `and` anahtar sözcüğünü kullanarak birbirine bağlayabilirsiniz.

Aşağıdaki örnekte birbirini dışlayan iki özyinelemeli işlev gösterilmektedir.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet4002.fs)]

## <a name="see-also"></a>Ayrıca bkz.

- [İşlevler](index.md)
