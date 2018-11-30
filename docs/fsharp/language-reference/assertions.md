---
title: Onaylamalar (F#)
description: İfadeleri test etmek için bir hata ayıklama özelliği olarak 'onay' ifadesi kullanmayı öğrenirsiniz F# programlama dilidir.
ms.date: 05/16/2016
ms.openlocfilehash: fbaf038f08cfc74e6cb262c110322dc586813c0c
ms.sourcegitcommit: 7f7664837d35320a0bad3f7e4ecd68d6624633b2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/30/2018
ms.locfileid: "52671932"
---
# <a name="assertions"></a>Onaylamalar

`assert` Bir ifade test etmek için kullanabileceğiniz bir hata ayıklama özelliği ifadesidir. Hata ayıklama modunda başarısızlık durumunda, bir sistem hatası iletişim kutusu bir onay oluşturur.

## <a name="syntax"></a>Sözdizimi

```fsharp
assert condition
```

## <a name="remarks"></a>Açıklamalar

`assert` İfade türüne sahip `bool -> unit`.

Önceki sözdiziminde, *koşul* test edilecek bir Boole ifadesi temsil eder. İfade değerlendirme sonucu `true`, yürütme devam eder etkilenmez. Değerlendirilirse `false`, sistem hatası iletişim kutusu oluşturulur. Hata iletişim kutusu dize içeren bir başlığa sahip **onaylama işlemi başarısız oldu**. İletişim kutusu, onaylama işlemi hatası nerede oluştuğunu gösteren bir yığın izlemesi içerir.

Yalnızca, hata ayıklama modunda derleme yaptığınızda, onaylama işlemi denetimi etkinleştirilir; diğer bir deyişle, sabiti `DEBUG` tanımlanır. Varsayılan olarak, proje sistemi içindeki `DEBUG` sabiti, hata ayıklama yapılandırmasında ancak sürüm yapılandırmasını içinde tanımlanır.

Onaylama işlemi hatası kullanarak yakalanamaz F# özel durum işleme.

> [!NOTE]
> `assert` İşlevi çözümler için <xref:System.Diagnostics.Debug.Assert*?displayProperty=nameWithType>.

## <a name="example"></a>Örnek

Aşağıdaki kod örneği kullanışını `assert` ifade.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet5401.fs)]

## <a name="see-also"></a>Ayrıca bkz.

- [F# Dili Başvurusu](index.md)
