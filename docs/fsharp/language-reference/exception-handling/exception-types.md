---
title: Özel Durum Türleri (F#)
description: 'Tanımlama ve F # özel durum türlerini kullanma hakkında bilgi edinin.'
ms.date: 05/16/2016
ms.openlocfilehash: b8d648a3649153a3604856deb61ce41db8c40bf2
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2018
ms.locfileid: "43858827"
---
# <a name="exception-types"></a>Özel Durum Türleri

F # dilinde özel durumlar iki kategorisi vardır: .NET özel durum türlerini ve F # özel durum türleri. Bu konuda, tanımlamak ve F # özel durum türlerini kullanın açıklar.

## <a name="syntax"></a>Sözdizimi

```fsharp
exception exception-type of argument-type
```

## <a name="remarks"></a>Açıklamalar

Önceki sözdiziminde, *özel durum türü* yeni F # özel durum türü adıdır ve *bağımsız değişken türü* bu türde bir özel durum yükselttiğinizde sağlanabilir bir bağımsız değişken türünü temsil eder. Bir demet türü için'ı kullanarak birden çok bağımsız değişkeni belirtebilirsiniz *bağımsız değişken türü*.

Bir F # özel durum için tipik bir tanım aşağıdakine benzer.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet5501.fs)]

Bu tür bir özel durum kullanarak oluşturabileceğiniz `raise` gibi işlev.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet5502.fs)]

Bir F # özel durum türü, doğrudan, filtreleri kullanabilirsiniz bir `try...with` aşağıdaki örnekte gösterildiği gibi ifade.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet5503.fs)]

İle tanımladığınız özel durum türü `exception` sözcüktür F #'de devraldığı yeni bir tür `System.Exception`.

## <a name="see-also"></a>Ayrıca bkz.

- [Özel Durum İşleme](index.md)
- [Özel durumlar: `raise` işlevi](the-raise-function.md)
- [Özel durum hiyerarşisi](https://msdn.microsoft.com/library/z4c5tckx.aspx)
