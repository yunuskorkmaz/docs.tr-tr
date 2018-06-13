---
title: 'Lambda İfadeleri: fun Anahtar Sözcüğü (F#)'
description: "F # 'eğlenceli' anahtar sözcüğü adsız bir işlev bir lambda ifadesi tanımlamak için nasıl kullanılacağını öğrenin."
ms.date: 05/16/2016
ms.openlocfilehash: 433451fb9bf89bfabdcd8e71560105317771d251
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33563856"
---
# <a name="lambda-expressions-the-fun-keyword-f"></a>Lambda İfadeleri: fun Anahtar Sözcüğü (F#)

`fun` Anahtar sözcüğü bir lambda ifadesi, başka bir deyişle, adsız bir işlev tanımlamak için kullanılır.


## <a name="syntax"></a>Sözdizimi

```fsharp
fun parameter-list -> expression
```

## <a name="remarks"></a>Açıklamalar
*Parametre listesi* genellikle adları ve parametre türlerini, isteğe bağlı olarak, oluşur. Daha fazla genel olarak, *parametre listesi* herhangi F # desenlerini oluşturulabilir. Olası desenleri tam bir listesi için bkz: [desen eşleştirme](../pattern-matching.md). Geçerli parametreler listesi örnek olarak şunlar gösterilebilir.

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

*İfade* gövdesi işlevinin biri son deyim dönüş değeri oluşturur. Geçerli lambda ifadeleri örnekleri şunlardır:

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet301.fs)]
    
## <a name="using-lambda-expressions"></a>Lambda İfadeleri kullanma
Lambda ifadeleri bir liste veya diğer koleksiyon üzerinde işlem gerçekleştirmek ve bir işlev tanımlamanın ek iş önlemek istiyorsanız istediğinizde özellikle yararlıdır. Birçok F # kitaplığı işlevi bağımsız değişken olarak işlevi değerleri alır ve bir lambda ifadesi bu gibi durumlarda kullanılacak özellikle kullanışlı olabilir. Aşağıdaki kod bir lambda ifadesi bir liste öğelerine uygulanır. Bu durumda, anonim işlevi listesini her öğeye 1 ekler.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet302.fs)]
    
## <a name="see-also"></a>Ayrıca Bkz.
[İşlevler](index.md)
