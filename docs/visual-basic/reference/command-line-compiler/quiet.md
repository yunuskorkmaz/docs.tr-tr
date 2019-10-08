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
ms.openlocfilehash: 6e773c60469e8426956c92a5aa377741ba5af4d3
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/07/2019
ms.locfileid: "72005284"
---
# <a name="-quiet"></a>-quiet

Derleyicinin sözdizimiyle ilgili hatalar ve uyarılar için kod görüntülemesini engeller.

## <a name="syntax"></a>Sözdizimi

```console
-quiet
```

## <a name="remarks"></a>Açıklamalar

Varsayılan olarak, `-quiet` geçerli değildir. Derleyici söz dizimi ile ilgili bir hata veya uyarı bildirdiğinde, satır kaynak kodundan de çıkış olur. Derleyici çıkışını ayrıştırmaya yönelik uygulamalar için derleyicinin yalnızca Tanılamanın metnini çıktısının daha kullanışlı olabilir.

Aşağıdaki örnekte, `Module1` `-quiet` olmadan derlendiğinde kaynak kodu içeren bir hata verir.

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

@No__t-0 ile derlenirse, derleyici yalnızca şunları verir:

```console
E:\test\t2.vb(3) : error BC30451: Name 'x' is not declared.
```

> [!NOTE]
> @No__t-0 seçeneği, Visual Studio geliştirme ortamı içinden kullanılamaz; yalnızca komut satırından derlenirken kullanılabilir.

## <a name="example"></a>Örnek

Aşağıdaki kod `T2.vb` derler ve söz dizimi ile ilgili derleyici tanılamaları için kod görüntülemez:

```console
vbc -quiet t2.vb
```

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Basic komut satırı derleyicisi](../../../visual-basic/reference/command-line-compiler/index.md)
- [Örnek Derleme Komut Satırları](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
