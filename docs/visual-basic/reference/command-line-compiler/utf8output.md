---
title: -utf8output (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- -utf8output compiler option [Visual Basic]
- utf8output compiler option [Visual Basic]
- /utf8output compiler option [Visual Basic]
ms.assetid: 8ab36b1e-027a-49ac-85b4-f48997d9e4d6
ms.openlocfilehash: adcb518cbe8397549c3ae3b3a8ca9f0ecf9dc38e
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/07/2019
ms.locfileid: "72004660"
---
# <a name="-utf8output-visual-basic"></a>-utf8output (Visual Basic)
UTF-8 kodlamasını kullanarak derleyici çıkışını görüntüler.  
  
## <a name="syntax"></a>Sözdizimi  
  
```console  
-utf8output[+ | -]  
```  
  
## <a name="arguments"></a>Arguments  
 `+` &#124; `-`  
 İsteğe bağlı. Bu seçenek için varsayılan değer `-utf8output-` ' dır. Bu, derleyici çıkışının UTF-8 kodlaması kullanmaz anlamına gelir. @No__t-0 belirtildiğinde `-utf8output+` belirtilerek aynı olur.  
  
## <a name="remarks"></a>Açıklamalar  
 Bazı uluslararası yapılandırmalarda, Derleyici çıktısı konsolunda doğru şekilde görüntülenemez. Bu gibi durumlarda, `-utf8output` ' ı kullanın ve derleyici çıkışını bir dosyaya yeniden yönlendirin.  
  
> [!NOTE]
> @No__t-0 seçeneği, Visual Studio geliştirme ortamı içinden kullanılamaz; yalnızca komut satırından derlenirken kullanılabilir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod `In.vb` derler ve derleyiciyi UTF-8 kodlaması kullanarak çıktıyı görüntüleyecek şekilde yönlendirir.  
  
```console  
vbc -utf8output in.vb  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Visual Basic komut satırı derleyicisi](../../../visual-basic/reference/command-line-compiler/index.md)
- [Örnek Derleme Komut Satırları](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
