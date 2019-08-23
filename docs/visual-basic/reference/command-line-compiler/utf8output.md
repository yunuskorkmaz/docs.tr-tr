---
title: -utf8output (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- -utf8output compiler option [Visual Basic]
- utf8output compiler option [Visual Basic]
- /utf8output compiler option [Visual Basic]
ms.assetid: 8ab36b1e-027a-49ac-85b4-f48997d9e4d6
ms.openlocfilehash: 789df84bb4011d1ad128c50a9c689d1217be6694
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69937272"
---
# <a name="-utf8output-visual-basic"></a>-utf8output (Visual Basic)
UTF-8 kodlamasını kullanarak derleyici çıkışını görüntüler.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
-utf8output[+ | -]  
```  
  
## <a name="arguments"></a>Arguments  
 `+` &#124; `-`  
 İsteğe bağlı. Bu seçenek `-utf8output-`için varsayılan değer, derleyici çıkışının UTF-8 kodlamasını kullanmayacağı anlamına gelir. Belirtmek `-utf8output` , belirtilerek `-utf8output+`aynı olur.  
  
## <a name="remarks"></a>Açıklamalar  
 Bazı uluslararası yapılandırmalarda, Derleyici çıktısı konsolunda doğru şekilde görüntülenemez. Bu gibi durumlarda, derleyici `-utf8output` çıkışını kullanın ve bir dosyaya yeniden yönlendirin.  
  
> [!NOTE]
> Bu `-utf8output` seçenek, Visual Studio geliştirme ortamı içinden kullanılamaz; yalnızca komut satırından derlenirken kullanılabilir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod derlenir `In.vb` ve derleyicinin UTF-8 kodlamasını kullanarak çıktıyı görüntülemesini sağlar.  
  
```console  
vbc -utf8output in.vb  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Visual Basic komut satırı derleyicisi](../../../visual-basic/reference/command-line-compiler/index.md)
- [Örnek Derleme Komut Satırları](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
