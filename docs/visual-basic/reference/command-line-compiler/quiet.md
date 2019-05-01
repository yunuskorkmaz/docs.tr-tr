---
title: -quiet
ms.date: 07/20/2015
f1_keywords:
- -quiet
- quiet
helpviewer_keywords:
- -quiet compiler option [Visual Basic]
- /quiet compiler option [Visual Basic]
- quiet compiler option [Visual Basic]
ms.assetid: 5d77fa23-4c50-4708-8535-649912b098e8
ms.openlocfilehash: a22773e2e37eb60ab6f1e88305266f41764311e7
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61788854"
---
# <a name="-quiet"></a>-quiet

Derleyici, kod söz dizimi ile ilgili hatalar ve Uyarılar için görüntülenmesini engeller.

## <a name="syntax"></a>Sözdizimi

```
-quiet
```

## <a name="remarks"></a>Açıklamalar

Varsayılan olarak, `-quiet` etkili değildir. Derleyici bir söz dizimi ile ilgili hata veya uyarı bildirdiğinde, ayrıca kaynak kod satırından çıkarır. Derleyici çıkışı çözümlenemedi uygulamalar için derleyicinin yalnızca metin tanı çıktısını almak daha kullanışlı olabilir.

Aşağıdaki örnekte, `Module1` olmadan derlendiğinde kaynak kodu içeren bir hata verir `-quiet`.

```vb
Module Module1
    Sub Main()
        x()
    End Sub
End Module
```

Çıktı:

```console
C:\projects\vb2.vb(3) : error BC30451: 'x' is not declared. It may be inaccessible due to its protection level.

        x()
        ~
```

İle derlenmiş `-quiet`, yalnızca aşağıdaki derleyici çıkışı:

```
E:\test\t2.vb(3) : error BC30451: Name 'x' is not declared.
```

> [!NOTE]
> `-quiet` Seçeneği, Visual Studio geliştirme ortamında kullanılabilir değil; yalnızca komut satırından derleme yapılırken kullanılabilir.

## <a name="example"></a>Örnek

Aşağıdaki kod derlenir `T2.vb` ve ilgili söz dizimleri derleyici tanılaması için kod görüntülemez:

```
vbc -quiet t2.vb
```

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Basic komut satırı derleyicisi](../../../visual-basic/reference/command-line-compiler/index.md)
- [Örnek Derleme Komut Satırları](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
