---
title: 'Lambda Ifadeleri: Eğlenceli anahtar sözcüğü'
description: Anonim bir işlev olan bir F# lambda ifadesi tanımlamak için ' Fun ' anahtar sözcüğünü nasıl kullanacağınızı öğrenin.
ms.date: 05/16/2016
ms.openlocfilehash: 9818724686dd83a7e352fb36819289fa19b002df
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630669"
---
# <a name="lambda-expressions-the-fun-keyword-f"></a>Lambda Ifadeleri: Fun anahtar sözcüğü (F#)

`fun` Anahtar sözcüğü bir lambda ifadesi, yani anonim bir işlev tanımlamak için kullanılır.

## <a name="syntax"></a>Sözdizimi

```fsharp
fun parameter-list -> expression
```

## <a name="remarks"></a>Açıklamalar

*Parametre listesi* genellikle ad ve isteğe bağlı olarak parametre türlerinden oluşur. Daha genel olarak, *parametre listesi* herhangi bir F# desenden oluşabilir. Olası desenlerin tam listesi için bkz. [desen eşleştirme](../pattern-matching.md). Geçerli parametrelerin listeleri aşağıdaki örnekleri içerir.

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

*İfade* , bir dönüş değeri üreten son ifadesi olan işlevinin gövdesidir. Geçerli lambda ifadesi örnekleri şunları içerir:

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet301.fs)]

## <a name="using-lambda-expressions"></a>Lambda İfadeleri kullanma

Lambda ifadeleri özellikle bir liste veya başka bir koleksiyon üzerinde işlemler gerçekleştirmek istediğinizde ve bir işlev tanımlamayı önlemek istediğinizde faydalıdır. Birçok F# kitaplık işlevi işlev değerlerini bağımsız değişken olarak alır ve özellikle bu durumlarda bir lambda ifadesi kullanmak kullanışlı olabilir. Aşağıdaki kod, bir listenin öğelerine bir lambda ifadesi uygular. Bu durumda, anonim işlev bir listenin her öğesine 1 ekler.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet302.fs)]

## <a name="see-also"></a>Ayrıca bkz.

- [İşlevler](index.md)
