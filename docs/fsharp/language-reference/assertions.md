---
title: Onaylamalar
description: F# Programlama dilindeki ifadeleri test etmek için hata ayıklama özelliği olarak ' onaylama ' ifadesini kullanmayı öğrenin.
ms.date: 05/16/2016
ms.openlocfilehash: b8b7e9662143b432d650f87515d4af31cced4149
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630029"
---
# <a name="assertions"></a>Onaylamalar

`assert` İfade, bir ifadeyi test etmek için kullanabileceğiniz bir hata ayıklama özelliğidir. Hata ayıklama modunda hata oluştuğunda bir onaylama işlemi bir sistem hatası iletişim kutusu oluşturur.

## <a name="syntax"></a>Sözdizimi

```fsharp
assert condition
```

## <a name="remarks"></a>Açıklamalar

`assert` İfadenin türü`bool -> unit`.

Önceki sözdiziminde, *koşul* test edilecek bir Boole ifadesini temsil eder. İfade olarak `true`değerlendirilirse, yürütme etkilenmeden devam eder. Değerlendiriliyorsa `false`, bir sistem hatası iletişim kutusu oluşturulur. Hata iletişim kutusu, dize **onaylama Işlemi başarısız**olan bir açıklamalı alt yazı içeriyor. İletişim kutusu, onaylama hatasının nerede oluştuğunu gösteren bir yığın izlemesi içerir.

Onaylama denetimi yalnızca hata ayıklama modunda derlerken etkinleştirilir; Bu, sabit `DEBUG` tanımlanmışsa. Proje sisteminde, varsayılan olarak, `DEBUG` sabit hata ayıklama yapılandırmasında tanımlanmıştır, ancak yayın yapılandırmasında belirlenir.

Onaylama hatası hatası özel durum işleme kullanılarak F# yakalanamıyor.

> [!NOTE]
> `assert` İşlevi olarak<xref:System.Diagnostics.Debug.Assert*?displayProperty=nameWithType>çözümlenir.

## <a name="example"></a>Örnek

Aşağıdaki kod örneği, `assert` ifadesinin kullanımını gösterir.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5401.fs)]

## <a name="see-also"></a>Ayrıca bkz.

- [F# Dili Başvurusu](index.md)
