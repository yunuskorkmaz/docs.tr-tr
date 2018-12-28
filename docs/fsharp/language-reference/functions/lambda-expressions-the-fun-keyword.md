---
title: 'Lambda ifadeleri: Fun anahtar sözcüğü'
description: Nasıl kullanacağınızı öğrenin F# 'eğlenceli' anahtar sözcüğü, anonim bir işlevdir bir lambda ifadesi tanımlayacaksınız.
ms.date: 05/16/2016
ms.openlocfilehash: 6ad15173bb8643bff330e3ca3823cba5d43ad445
ms.sourcegitcommit: fa38fe76abdc8972e37138fcb4dfdb3502ac5394
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/19/2018
ms.locfileid: "53614473"
---
# <a name="lambda-expressions-the-fun-keyword-f"></a>Lambda ifadeleri: Fun anahtar sözcüğü (F#)

`fun` Anahtar sözcüğü, bir lambda ifadesi, başka bir deyişle, anonim bir işlev tanımlamak için kullanılır.

## <a name="syntax"></a>Sözdizimi

```fsharp
fun parameter-list -> expression
```

## <a name="remarks"></a>Açıklamalar

*Parametre-listesi* genellikle adları ve parametre türleri, isteğe bağlı olarak oluşur. Daha genel *parametre-listesi* herhangi birini oluşturulması F# desenleri. Olası desenleri tam bir listesi için bkz. [desen eşleştirme](../pattern-matching.md). Geçerli parametrelerin bir listesi aşağıdaki örnekleri içerir.

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

Lambda ifadeleri, özellikle bir liste veya diğer toplama işlemleri ve bir işlevi tanımlayan kaynaklanan ek yükten kaçınmak istiyorsanız istediğinizde kullanışlıdır. Birçok F# kitaplığı işlevler bağımsız değişkenler olarak işlev değerleri alır ve bir lambda ifadesi bu gibi durumlarda kullanılacak özellikle kullanışlı olabilir. Aşağıdaki kod bir lambda ifadesi bir liste öğelerine uygulanır. Bu durumda, anonim işlev listesini her öğeye 1 ekler.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet302.fs)]

## <a name="see-also"></a>Ayrıca bkz.

- [İşlevler](index.md)