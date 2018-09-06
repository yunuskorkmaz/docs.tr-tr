---
title: 'Lambda İfadeleri: fun Anahtar Sözcüğü (F#)'
description: "Anonim bir işlevdir bir lambda ifadesi tanımlamak için F # 'eğlenceli' anahtar sözcüğünü kullanmayı öğrenin."
ms.date: 05/16/2016
ms.openlocfilehash: a37757f6b7328cd348bbf13f058a6dbc881769cf
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2018
ms.locfileid: "43744294"
---
# <a name="lambda-expressions-the-fun-keyword-f"></a>Lambda İfadeleri: fun Anahtar Sözcüğü (F#)

`fun` Anahtar sözcüğü, bir lambda ifadesi, başka bir deyişle, anonim bir işlev tanımlamak için kullanılır.

## <a name="syntax"></a>Sözdizimi

```fsharp
fun parameter-list -> expression
```

## <a name="remarks"></a>Açıklamalar

*Parametre-listesi* genellikle adları ve parametre türleri, isteğe bağlı olarak oluşur. Daha genel *parametre-listesi* tüm F # desenlerini oluşabilir. Olası desenleri tam bir listesi için bkz. [desen eşleştirme](../pattern-matching.md). Geçerli parametrelerin bir listesi aşağıdaki örnekleri içerir.

```fsharp
// Lambda expressions with parameter lists.
fun a b c -> ...
fun (a: int) b c -> ...
fun (a : int) (b : string) (c:float) -> ...

// A lambda expression with a tuple pattern.
fun (a, b) -> …

// A lambda expression with a list pattern.
fun head :: tail -> …
```

*İfade* biri son deyim dönüş değeri oluşturur işlev gövdesidir. Geçerli lambda ifadeleri örnekleri şunları içerir:

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet301.fs)]

## <a name="using-lambda-expressions"></a>Lambda İfadeleri kullanma

Lambda ifadeleri, özellikle bir liste veya diğer toplama işlemleri ve bir işlevi tanımlayan kaynaklanan ek yükten kaçınmak istiyorsanız istediğinizde kullanışlıdır. İşlev değerleri olarak bağımsız değişkenler çoğu F # kitaplığı işlevleri yararlanın ve bir lambda ifadesi bu gibi durumlarda kullanılacak özellikle kullanışlı olabilir. Aşağıdaki kod bir lambda ifadesi bir liste öğelerine uygulanır. Bu durumda, anonim işlev listesini her öğeye 1 ekler.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet302.fs)]

## <a name="see-also"></a>Ayrıca bkz.

- [İşlevler](index.md)
