---
title: Özel Durum Türleri
description: Tanımlama ve kullanma hakkında bilgi edinin F# özel durum türleri.
ms.date: 05/16/2016
ms.openlocfilehash: ed721dd0dc46a486fafeac2fa4c096800995ccb7
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61772729"
---
# <a name="exception-types"></a>Özel Durum Türleri

Özel durumları iki kategorisi vardır F#: .NET özel durum türlerini ve F# özel durum türleri. Bu konu nasıl tanımlanacağını ve kullanılacağını açıklar F# özel durum türleri.

## <a name="syntax"></a>Sözdizimi

```fsharp
exception exception-type of argument-type
```

## <a name="remarks"></a>Açıklamalar

Önceki sözdiziminde, *özel durum türü* yeni adı F# özel durum türü ve *bağımsız değişken türü* bu türde bir özel durum yükselttiğinizde sağlanabilir bir bağımsız değişken türünü temsil eder. Bir demet türü için'ı kullanarak birden çok bağımsız değişkeni belirtebilirsiniz *bağımsız değişken türü*.

Tipik bir tanımı için bir F# özel durum aşağıdakine benzer.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet5501.fs)]

Bu tür bir özel durum kullanarak oluşturabileceğiniz `raise` gibi işlev.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet5502.fs)]

Kullanabileceğiniz bir F# özel durum türünü doğrudan filtreleri bir `try...with` aşağıdaki örnekte gösterildiği gibi ifade.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet5503.fs)]

İle tanımladığınız özel durum türü `exception` anahtar sözcüğünü F# devralan yeni bir türdür `System.Exception`.

## <a name="see-also"></a>Ayrıca bkz.

- [Özel Durum İşleme](index.md)
- [Özel durumlar: `raise` işlevi](the-raise-function.md)
- [Özel durum hiyerarşisi](https://msdn.microsoft.com/library/z4c5tckx.aspx)