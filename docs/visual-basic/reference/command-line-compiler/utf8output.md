---
title: -utf8output
ms.date: 07/20/2015
helpviewer_keywords:
- -utf8output compiler option [Visual Basic]
- utf8output compiler option [Visual Basic]
- /utf8output compiler option [Visual Basic]
ms.assetid: 8ab36b1e-027a-49ac-85b4-f48997d9e4d6
ms.openlocfilehash: 5cdc60888cd872940afc1b03febd879bb6d87c2e
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74350831"
---
# <a name="-utf8output-visual-basic"></a>-utf8output (Visual Basic)
UTF-8 kodlamasını kullanarak derleyici çıkışını görüntüler.  
  
## <a name="syntax"></a>Sözdizimi  
  
```console  
-utf8output[+ | -]  
```  
  
## <a name="arguments"></a>Bağımsız Değişkenler  
 `+` &#124; `-`  
 İsteğe bağlı. Bu seçenek için varsayılan değer `-utf8output-`, bu, derleyici çıkışının UTF-8 kodlamasını kullanmayacağı anlamına gelir. `-utf8output` belirtmek `-utf8output+`belirtirken de aynıdır.  
  
## <a name="remarks"></a>Açıklamalar  
 Bazı uluslararası yapılandırmalarda, Derleyici çıktısı konsolunda doğru şekilde görüntülenemez. Bu gibi durumlarda `-utf8output` kullanın ve derleyici çıkışını bir dosyaya yeniden yönlendirin.  
  
> [!NOTE]
> `-utf8output` seçeneği, Visual Studio geliştirme ortamı içinden kullanılamaz; yalnızca komut satırından derlenirken kullanılabilir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod `In.vb` derler ve derleyiciyi UTF-8 kodlaması kullanarak çıktıyı görüntüleyecek şekilde yönlendirir.  
  
```console  
vbc -utf8output in.vb  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Visual Basic komut satırı derleyicisi](../../../visual-basic/reference/command-line-compiler/index.md)
- [Örnek Derleme Komut Satırları](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
