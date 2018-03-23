---
title: -utf8output (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- -utf8output compiler option [Visual Basic]
- utf8output compiler option [Visual Basic]
- /utf8output compiler option [Visual Basic]
ms.assetid: 8ab36b1e-027a-49ac-85b4-f48997d9e4d6
caps.latest.revision: ''
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 97f90b39046aebe0cd15c7e033d8e588045491f7
ms.sourcegitcommit: 498799639937c89de777361aab74261efe7b79ea
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/22/2018
---
# <a name="-utf8output-visual-basic"></a>-utf8output (Visual Basic)
UTF-8 kodlaması kullanarak derleyici çıkışı görüntülenir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
-utf8output[+ | -]  
```  
  
## <a name="arguments"></a>Arguments  
 `+` &#124; `-`  
 İsteğe bağlı. Bu seçenek için varsayılan değer `-utf8output-`, yani Derleyici çıktısı UTF-8 kodlaması kullanmaz. Belirtme `-utf8output` belirtme aynı `-utf8output+`.  
  
## <a name="remarks"></a>Açıklamalar  
 Uluslararası bazı yapılandırmalarda Derleyici çıktısı doğru konsolda görüntülenemiyor. Bu gibi durumlarda kullanmak `-utf8output` ve Derleyici çıktısı bir dosyaya yönlendirin.  
  
> [!NOTE]
>  `-utf8output` Seçeneği Visual Studio geliştirme ortamında kullanılabilir değil; yalnızca komut satırından derlerken kullanılabilir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod derlerken `In.vb` ve görüntülemek için derleyici yönlendirir UTF-8 kodlaması kullanarak çıktı.  
  
```console  
vbc -utf8output in.vb  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Visual Basic komut satırı derleyicisi](../../../visual-basic/reference/command-line-compiler/index.md)  
 [Örnek Derleme Komut Satırları](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
