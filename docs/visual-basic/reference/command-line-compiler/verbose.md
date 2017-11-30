---
title: /verbose
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- verbose compiler option [Visual Basic]
- -verbose compiler option [Visual Basic]
- /verbose compiler option [Visual Basic]
ms.assetid: d1aec0c1-0261-421d-9adc-5b13756100be
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 5480f828fa1f0b6d71fa649bf44513ce806bb440
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="verbose"></a>/verbose
Ayrıntılı durum ve hata iletilerine neden derleyicinin neden olur.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
/verbose[+ | -]  
```  
  
## <a name="arguments"></a>Arguments  
 `+` &#124; `-`  
 İsteğe bağlı. Belirtme `/verbose` belirtme aynı `/verbose+`, ayrıntılı iletiler yaymak üzere derleyici neden olur. Bu seçenek için varsayılan değer `/verbose-`.  
  
## <a name="remarks"></a>Açıklamalar  
 `/verbose` Seçeneği derleyici tarafından verilen hatalarının toplam sayısını hakkında bilgi, bir modül tarafından hangi derlemelerin yüklenen raporları ve hangi dosyaların şu anda derlenmiş görüntüler.  
  
> [!NOTE]
>  `/verbose` Seçeneği Visual Studio geliştirme ortamında kullanılabilir değil; yalnızca komut satırından derlerken kullanılabilir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod derlerken `In.vb` ve ayrıntılı durum bilgilerini görüntülemek için derleyici yönlendirir.  
  
```  
vbc /verbose in.vb  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Visual Basic komut satırı derleyicisi](../../../visual-basic/reference/command-line-compiler/index.md)  
 [Örnek derleme komut satırları](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
