---
title: -utf8output (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- -utf8output compiler option [Visual Basic]
- utf8output compiler option [Visual Basic]
- /utf8output compiler option [Visual Basic]
ms.assetid: 8ab36b1e-027a-49ac-85b4-f48997d9e4d6
ms.openlocfilehash: 75369c3bcb19afbf98bfb80bc3e439f996d2a9d0
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61796084"
---
# <a name="-utf8output-visual-basic"></a>-utf8output (Visual Basic)
UTF-8 kodlaması kullanarak derleyici çıkışı görüntüler.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
-utf8output[+ | -]  
```  
  
## <a name="arguments"></a>Arguments  
 `+` &#124; `-`  
 İsteğe bağlı. Bu seçenek için varsayılan değer `-utf8output-`, derleyici çıkışını UTF-8 kodlamasını kullanmayan anlamına gelir. Belirtme `-utf8output` belirtmekle aynı `-utf8output+`.  
  
## <a name="remarks"></a>Açıklamalar  
 Bazı uluslararası yapılandırmalarında, derleyici çıkışını konsolunda doğru şekilde görüntülenemiyor. Böyle durumlarda `-utf8output` ve derleyici çıkışı bir dosyaya yönlendirin.  
  
> [!NOTE]
>  `-utf8output` Seçeneği, Visual Studio geliştirme ortamında kullanılabilir değil; yalnızca komut satırından derleme yapılırken kullanılabilir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod derlenir `In.vb` ve görüntülemek için derleyicinin yönlendirir UTF-8 kodlaması kullanarak çıktı.  
  
```console  
vbc -utf8output in.vb  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Visual Basic komut satırı derleyicisi](../../../visual-basic/reference/command-line-compiler/index.md)
- [Örnek Derleme Komut Satırları](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
