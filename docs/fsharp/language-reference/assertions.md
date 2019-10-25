---
title: Onaylamalar
description: F# Programlama dilindeki ifadeleri test etmek için hata ayıklama özelliği olarak ' onaylama ' ifadesini kullanmayı öğrenin.
ms.date: 10/22/2019
ms.openlocfilehash: 430db20e5ca307ba43a72e678a0424e03b0ac381
ms.sourcegitcommit: 9bd1c09128e012b6e34bdcbdf3576379f58f3137
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2019
ms.locfileid: "72799067"
---
# <a name="assertions"></a>Onaylamalar

`assert` ifadesi bir ifadeyi test etmek için kullanabileceğiniz bir hata ayıklama özelliğidir. Hata ayıklama modunda hata oluştuğunda bir onaylama işlemi bir sistem hatası iletişim kutusu oluşturur.

## <a name="syntax"></a>Sözdizimi

```fsharp
assert condition
```

## <a name="remarks"></a>Açıklamalar

`assert` ifadesi tür `bool -> unit`.

`assert` işlevi <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType>olarak çözümlenir. Bu, davranışının <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType> doğrudan çağırmasına benzer şekilde olduğu anlamına gelir.

Onaylama denetimi yalnızca hata ayıklama modunda derlerken etkinleştirilir; diğer bir deyişle, sabit `DEBUG` tanımlanmışsa. Proje sisteminde, varsayılan olarak `DEBUG` sabiti, sürüm yapılandırmasında değil, hata ayıklama yapılandırmasında tanımlanmıştır.

Onaylama hatası hatası özel durum işleme kullanılarak F# yakalanamıyor.

## <a name="example"></a>Örnek

Aşağıdaki kod örneği `assert` ifadesinin kullanımını gösterir.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5401.fs)]

## <a name="see-also"></a>Ayrıca bkz.

- [F# Dili Başvurusu](index.md)
