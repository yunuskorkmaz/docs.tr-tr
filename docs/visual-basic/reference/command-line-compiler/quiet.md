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
ms.openlocfilehash: f894ed6a778e026ffd3976a63fe3b677eb6a9557
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84400532"
---
# <a name="-quiet"></a>-quiet

Derleyicinin sözdizimiyle ilgili hatalar ve uyarılar için kod görüntülemesini engeller.

## <a name="syntax"></a>Sözdizimi

```console
-quiet
```

## <a name="remarks"></a>Açıklamalar

Varsayılan olarak `-quiet` etkin değildir. Derleyici söz dizimi ile ilgili bir hata veya uyarı bildirdiğinde, satır kaynak kodundan de çıkış olur. Derleyici çıkışını ayrıştırmaya yönelik uygulamalar için derleyicinin yalnızca Tanılamanın metnini çıktısının daha kullanışlı olabilir.

Aşağıdaki örnekte, `Module1` olmadan derlendiğinde kaynak kodu içeren bir hata verir `-quiet` .

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

İle derlenirse `-quiet` , derleyici yalnızca aşağıdakilerin çıktısını verir:

```console
E:\test\t2.vb(3) : error BC30451: Name 'x' is not declared.
```

> [!NOTE]
> `-quiet`Bu seçenek, Visual Studio geliştirme ortamı içinden kullanılamaz; yalnızca komut satırından derlenirken kullanılabilir.

## <a name="example"></a>Örnek

Aşağıdaki kod, `T2.vb` sözdizimi ile ilgili derleyici tanılamaları için kodu derler ve görüntülemez:

```console
vbc -quiet t2.vb
```

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Basic komut satırı derleyicisi](index.md)
- [Örnek Derleme Komut Satırları](sample-compilation-command-lines.md)
