---
title: Özel Durum Türleri
description: Özel durum türlerini tanımlama ve kullanma F# hakkında bilgi edinin.
ms.date: 05/16/2016
ms.openlocfilehash: 8545fab50ff6338d1f1621710a838a200f9ac705
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630318"
---
# <a name="exception-types"></a>Özel Durum Türleri

İçinde F#iki özel durum kategorisi vardır: .NET özel durum türleri ve F# özel durum türleri. Bu konu, F# özel durum türlerinin nasıl tanımlanacağını ve kullanılacağını açıklar.

## <a name="syntax"></a>Sözdizimi

```fsharp
exception exception-type of argument-type
```

## <a name="remarks"></a>Açıklamalar

Önceki sözdiziminde, *özel* durum türü yeni F# bir özel durum türünün adıdır ve *bağımsız değişken türü* , bu türde bir özel durum oluştururken sağlanabilecek bir bağımsız değişkenin türünü temsil eder. *Bağımsız değişken*türü için bir demet türü kullanarak birden çok bağımsız değişken belirtebilirsiniz.

Bir F# özel durum için tipik bir tanım aşağıdakine benzer.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5501.fs)]

Aşağıdaki gibi, `raise` işlevini kullanarak bu türde bir özel durum oluşturabilirsiniz.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5502.fs)]

Aşağıdaki örnekte gösterildiği gibi F# , bir `try...with` ifadede doğrudan filtrelerde bir özel durum türü kullanabilirsiniz.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5503.fs)]

İçindeki `exception` F# anahtar sözcüğüyle tanımladığınız özel durum türü, öğesinden `System.Exception`devralan yeni bir türdür.

## <a name="see-also"></a>Ayrıca bkz.

- [Özel Durum İşleme](index.md)
- [Özel durumlar: `raise` işlev](the-raise-function.md)
- [Özel durum hiyerarşisi](https://msdn.microsoft.com/library/z4c5tckx.aspx)
