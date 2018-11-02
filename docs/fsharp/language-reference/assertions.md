---
title: Onaylamalar (F#)
description: "'Onay' ifadesi, ifadeler F # programlama dilinin test etmek için bir hata ayıklama özelliği olarak kullanmayı öğrenin."
ms.date: 05/16/2016
ms.openlocfilehash: 85b1e839bfd19bada48b7f1821d15ddd8fa77754
ms.sourcegitcommit: db8b83057d052c1f9f249d128b08d4423af0f7c2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/02/2018
ms.locfileid: "48842482"
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

F # özel durum işlemeyi kullanarak, onaylama işlemi hatası yakalanamıyor.

>[!NOTE]
`assert` İşlevi çözümler için <xref:System.Diagnostics.Debug.Assert*?displayProperty=nameWithType>.

## <a name="example"></a>Örnek

Aşağıdaki kod örneği kullanışını `assert` ifade.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet5401.fs)]

## <a name="see-also"></a>Ayrıca bkz.

- [F# Dili Başvurusu](index.md)
