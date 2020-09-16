---
title: Özel Durum Türleri
description: 'F # özel durum türlerini tanımlama ve kullanma hakkında bilgi edinin.'
ms.date: 05/16/2016
ms.openlocfilehash: 8b4ceec31a2d68abbcd025812ffeeefc0c090efb
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90557235"
---
# <a name="exception-types"></a>Özel Durum Türleri

F #: .NET özel durum türlerinde ve F # özel durum türlerinde iki özel durum kategorisi vardır. Bu konu başlığı altında, F # özel durum türlerinin nasıl tanımlanacağı ve kullanılacağı açıklanmaktadır.

## <a name="syntax"></a>Syntax

```fsharp
exception exception-type of argument-type
```

## <a name="remarks"></a>Açıklamalar

Önceki sözdiziminde, *özel durum türü* yeni bir F # özel durum türünün adıdır ve *bağımsız değişken türü* , bu türde bir özel durum oluştururken sağlanabilecek bir bağımsız değişkenin türünü temsil eder. *Bağımsız değişken*türü için bir demet türü kullanarak birden çok bağımsız değişken belirtebilirsiniz.

F # özel durumu için tipik bir tanım aşağıdakine benzer.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5501.fs)]

Aşağıdaki gibi, işlevini kullanarak bu türde bir özel durum oluşturabilirsiniz `raise` .

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5502.fs)]

Aşağıdaki örnekte gösterildiği gibi, bir ifadedeki doğrudan filtrelerde bir F # özel durum türü kullanabilirsiniz `try...with` .

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5503.fs)]

`exception`F # içindeki anahtar sözcükle tanımladığınız özel durum türü, öğesinden devralan yeni bir türdür `System.Exception` .

## <a name="see-also"></a>Ayrıca bkz.

- [Özel Durum İşleme](index.md)
- [Özel durumlar: `raise` işlev](the-raise-function.md)
- [Özel durum hiyerarşisi](../../../standard/exceptions/index.md)
