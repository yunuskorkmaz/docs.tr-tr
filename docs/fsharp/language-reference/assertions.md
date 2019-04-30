---
title: Onaylamalar
description: İfadeleri test etmek için bir hata ayıklama özelliği olarak 'onay' ifadesi kullanmayı öğrenirsiniz F# programlama dilidir.
ms.date: 05/16/2016
ms.openlocfilehash: c2d97386e87e9b915da490a78fff9aedb9def616
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61703224"
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