---
description: Hakkında daha fazla bilgi edinin:-utf8output (Visual Basic)
title: -utf8output
ms.date: 07/20/2015
helpviewer_keywords:
- -utf8output compiler option [Visual Basic]
- utf8output compiler option [Visual Basic]
- /utf8output compiler option [Visual Basic]
ms.assetid: 8ab36b1e-027a-49ac-85b4-f48997d9e4d6
ms.openlocfilehash: 317c1be3f18150ae88bb8e95927d9f5faf0e4f3c
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100461898"
---
# <a name="-utf8output-visual-basic"></a>-utf8output (Visual Basic)

UTF-8 kodlamasını kullanarak derleyici çıkışını görüntüler.  
  
## <a name="syntax"></a>Söz dizimi  
  
```console  
-utf8output[+ | -]  
```  
  
## <a name="arguments"></a>Bağımsız değişkenler  

 `+` &#124; `-`  
 İsteğe bağlı. Bu seçenek için varsayılan değer, `-utf8output-` derleyici ÇıKıŞıNıN UTF-8 kodlamasını kullanmayacağı anlamına gelir. Belirtmek, `-utf8output` belirtilerek aynı olur `-utf8output+` .  
  
## <a name="remarks"></a>Açıklamalar  

 Bazı uluslararası yapılandırmalarda, Derleyici çıktısı konsolunda doğru şekilde görüntülenemez. Bu gibi durumlarda, `-utf8output` derleyici çıkışını kullanın ve bir dosyaya yeniden yönlendirin.  
  
> [!NOTE]
> `-utf8output`Bu seçenek, Visual Studio geliştirme ortamı içinden kullanılamaz; yalnızca komut satırından derlenirken kullanılabilir.  
  
## <a name="example"></a>Örnek  

 Aşağıdaki kod derlenir `In.vb` ve DERLEYICININ UTF-8 kodlamasını kullanarak çıktıyı görüntülemesini sağlar.  
  
```console  
vbc -utf8output in.vb  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Visual Basic Command-Line derleyicisi](index.md)
- [Örnek Derleme Komut Satırları](sample-compilation-command-lines.md)
