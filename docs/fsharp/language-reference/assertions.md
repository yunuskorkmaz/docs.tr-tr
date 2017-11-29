---
title: Onaylamalar (F#)
description: "'Onay' ifadesi ifadeleri F # programlama dili test etmek için hata ayıklama bir özellik olarak kullanmayı öğrenin."
keywords: "Visual f #, f # işlevsel programlama"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 2badaad7-f086-47e7-99c1-91f35117da83
ms.openlocfilehash: 56891769602afaa765ebfe7e7822a179c7a22968
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="assertions"></a>Onaylamalar

`assert` İfadesidir bir ifade test etmek için kullanabileceğiniz bir hata ayıklama özelliği. Hata ayıklama modunda başarısızlık durumunda, bir onaylama sistem hata iletişim kutusu oluşturur.

## <a name="syntax"></a>Sözdizimi

```fsharp
assert condition
```

## <a name="remarks"></a>Açıklamalar

`assert` İfade türüne sahip `bool -> unit`.

Önceki sözdiziminde *koşulu* test edilmesi için bir Boole ifadesini temsil eder. İfade değerlendirilirse `true`, yürütülmeye etkilenmez. Değerlendirilirse `false`, bir sistem hatası iletişim kutusu oluşturulur. Hata iletişim kutusu dizeyi içeren bir resim yazısını **onaylama başarısız**. İletişim kutusu onaylama hatası nerede oluştuğunu gösteren bir yığın izlemeyi içerir.

Yalnızca hata ayıklama modunda derlediğinizde, onaylama işlemi denetimi etkinleştirilir; diğer bir deyişle, sabit `DEBUG` tanımlanır. Varsayılan olarak, proje sisteminde `DEBUG` sabiti hata ayıklama yapılandırmasını ancak sürüm yapılandırmasında tanımlanır.

F # özel durum işleme kullanarak onaylama hata yakalandı olamaz.

>[!NOTE]
`assert` İşlevi çözümler için <xref:System.Diagnostics.Debug.Assert*?displayProperty=nameWithType>.

## <a name="example"></a>Örnek

Aşağıdaki kod örneğinde kullanımını göstermektedir `assert` ifade.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet5401.fs)]
    
## <a name="see-also"></a>Ayrıca Bkz.

[F # dili başvurusu](index.md)
