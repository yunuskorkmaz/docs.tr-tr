---
title: -quiet
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- -quiet
- quiet
helpviewer_keywords:
- -quiet compiler option [Visual Basic]
- /quiet compiler option [Visual Basic]
- quiet compiler option [Visual Basic]
ms.assetid: 5d77fa23-4c50-4708-8535-649912b098e8
caps.latest.revision: ''
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: a0ed08e013f088f512ae915daa9aeb2fa6b249b0
ms.sourcegitcommit: 498799639937c89de777361aab74261efe7b79ea
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/22/2018
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
