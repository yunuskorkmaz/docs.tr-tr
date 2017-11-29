---
title: "Özel Durum Türleri (F#)"
description: "F # özel durum türlerini tanımlamak ve nasıl kullanılacağını öğrenin."
keywords: "Visual f #, f # işlevsel programlama"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: e850205a-b8da-459e-8f6d-cb3510f8f173
ms.openlocfilehash: a0864218841396c0ebdf26c7585e0e5bb778f83e
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="exception-types"></a>Özel Durum Türleri

F # özel durumların iki kategorisi vardır: .NET özel durum türleri ve F # özel durum türleri. Bu konu F # özel durum türlerini tanımlamak ve nasıl kullanılacağını açıklar.


## <a name="syntax"></a>Sözdizimi

```fsharp
exception exception-type of argument-type
```

## <a name="remarks"></a>Açıklamalar
Önceki sözdiziminde *özel durum türü* yeni F # özel durum türü, adı ve *bağımsız değişken türü* bu türünde bir özel durum yükselttiğinizde sağlanabilir bir bağımsız değişken türünü temsil eder. İçin bir tanımlama grubu türü kullanarak birden fazla bağımsız değişkenini belirtebilirsiniz *bağımsız değişken türü*.

F # özel durumu için tipik bir tanım aşağıdakine benzer.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet5501.fs)]

Bu tür bir özel durum kullanarak oluşturabileceğiniz `raise` gibi işlev.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet5502.fs)]

F # özel durum türü doğrudan filtreleri kullanabileceğiniz bir `try...with` aşağıdaki örnekte gösterildiği gibi ifade.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet5503.fs)]

İle tanımladığınız özel durum türü `exception` sözcüktür F # devraldığı yeni bir tür `System.Exception`.


## <a name="see-also"></a>Ayrıca Bkz.
[Özel durum işleme](index.md)

[Özel durumlar: `raise` işlevi](the-raise-function.md)

[Özel durum hiyerarşisi](https://msdn.microsoft.com/library/z4c5tckx.aspx)
