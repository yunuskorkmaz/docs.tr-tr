---
title: -utf8output (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- -utf8output compiler option [Visual Basic]
- utf8output compiler option [Visual Basic]
- /utf8output compiler option [Visual Basic]
ms.assetid: 8ab36b1e-027a-49ac-85b4-f48997d9e4d6
ms.openlocfilehash: 753c92cdf2124ee7fb1b471c7bc543b6db6f3daa
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
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
