---
title: -verbose
ms.date: 03/13/2018
ms.prod: .net
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- verbose compiler option [Visual Basic]
- -verbose compiler option [Visual Basic]
- /verbose compiler option [Visual Basic]
ms.assetid: d1aec0c1-0261-421d-9adc-5b13756100be
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f0523409e53a8c7ea34de7dcc24b1bce2885a183
ms.sourcegitcommit: 498799639937c89de777361aab74261efe7b79ea
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/22/2018
---
# <a name="-verbose"></a>-verbose
Ayrıntılı durum ve hata iletilerine neden derleyicinin neden olur.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
-verbose[+ | -]  
```  
  
## <a name="arguments"></a>Arguments  
 `+` &#124; `-`  
 İsteğe bağlı. Belirtme `-verbose` belirtme aynı `-verbose+`, ayrıntılı iletiler yaymak üzere derleyici neden olur. Bu seçenek için varsayılan değer `-verbose-`.  
  
## <a name="remarks"></a>Açıklamalar  
 `-verbose` Seçeneği derleyici tarafından verilen hatalarının toplam sayısını hakkında bilgi, bir modül tarafından hangi derlemelerin yüklenen raporları ve hangi dosyaların şu anda derlenmiş görüntüler.  
  
> [!NOTE]
>  `-verbose` Seçeneği Visual Studio geliştirme ortamında kullanılabilir değil; yalnızca komut satırından derlerken kullanılabilir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod derlerken `In.vb` ve ayrıntılı durum bilgilerini görüntülemek için derleyici yönlendirir.  
  
```console  
vbc -verbose in.vb  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Visual Basic komut satırı derleyicisi](../../../visual-basic/reference/command-line-compiler/index.md)  
 [Örnek Derleme Komut Satırları](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
