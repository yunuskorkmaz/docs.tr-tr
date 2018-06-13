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
ms.openlocfilehash: e67fe05507c8cb3edd7f46cad19211ba11e3b054
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33652402"
---
# <a name="-quiet"></a>-quiet
Derleyici sözdizimi ile ilgili hatalar ve Uyarılar için kod görüntülenmesini engeller.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
-quiet  
```  
  
## <a name="remarks"></a>Açıklamalar  
 Varsayılan olarak, `-quiet` etkili değildir. Derleyici bir sözdizimi ile ilgili hata veya uyarı bildirdiğinde, ayrıca kaynak kod satırından çıkarır. Derleyici çıktı ayrıştırma uygulamalar için yalnızca Tanı metin çıktısı derleyici için daha kullanışlı olabilir.  
  
 Aşağıdaki örnekte, `Module1` olmadan derlendiğinde kaynak kodu içeren hata çıkarır `-quiet`.  
  
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
 Derlenmiş ile `-quiet`, yalnızca aşağıdaki derleyici çıkarır:  
  
 `E:\test\t2.vb(3) : error BC30451: Name 'x' is not declared.`  
  
> [!NOTE]
>  `-quiet` Seçeneği Visual Studio geliştirme ortamında kullanılabilir değil; yalnızca komut satırından derlerken kullanılabilir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod derlerken `T2.vb` ve derleyici sözdizimi ile ilgili tanılama kodunu görüntülemez:  
  
```  
vbc -quiet t2.vb  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Visual Basic komut satırı derleyicisi](../../../visual-basic/reference/command-line-compiler/index.md)  
 [Örnek Derleme Komut Satırları](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
