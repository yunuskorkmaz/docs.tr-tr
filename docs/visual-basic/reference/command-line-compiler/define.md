---
title: /define (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- -d compiler option [Visual Basic]
- /d compiler option [Visual Basic]
- -define compiler option [Visual Basic]
- d compiler option [Visual Basic]
- /define compiler option [Visual Basic]
- define compiler option [Visual Basic]
ms.assetid: f735c57d-1cf9-4f2f-a26f-0de630fd4077
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 8bc3056c3e2d7a4aad469d3bf2c404f5f5248384
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="define-visual-basic"></a>/define (Visual Basic)
Koşullu derleme sabitleri tanımlar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
/define:["]symbol[=value][,symbol[=value]]["]  
' -or-  
/d:["]symbol[=value][,symbol[=value]]["]  
```  
  
## <a name="arguments"></a>Arguments  
  
|Terim|Tanım|  
|---|---|  
|`symbol`|Gerekli. Tanımlamak için simge.|  
|`value`|İsteğe bağlı. Atanacak değer `symbol`. Varsa `value` bir dizedir ters eğik çizgi /-tırnağından sıraları ile alınmalıdır (\\") tırnak işareti yerine. Değer belirtilmedi sonra olması için geçen True.|  
  
## <a name="remarks"></a>Açıklamalar  
 `/define` Seçeneği bir etkisi kullanmaya benzer bir `#Const` ile tanımlanmış bu sabitleri dışında kaynak dosyanızdaki önişlemci yönergesi `/define` ortak ve projedeki tüm dosyalar için geçerlidir.  
  
 Bu seçenek ile tarafından oluşturulan simgeleri kullanabilirsiniz `#If`... `Then`... `#Else` kaynak dosyaları koşullu derleme yönergesi.  
  
 `/d`kısa biçimi olan `/define`.  
  
 Birden çok sembolleriyle tanımlayabilirsiniz `/define` simge tanımlarını ayırmak için virgül kullanarak.  
  
|Ayarlamak için Visual Studio tümleşik geliştirme ortamında tanımlayın|  
|---|  
|1.  Seçili bir projeyi **Çözüm Gezgini**. Üzerinde **proje** menüsünde tıklatın **özellikleri**. Daha fazla bilgi için bkz: [Proje Tasarımcısı giriş](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7).<br />2.  Tıklatın **derleme** sekmesi.<br />3.  **Gelişmiş**'e tıklayın.<br />4.  Değer değiştirme **özel sabitleri** kutusu.|  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod tanımlar ve iki koşullu derleyici sabitleri kullanır.  
  
 [!code-vb[VbVbalrCompiler#45](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/define_1.vb)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Visual Basic komut satırı derleyicisi](../../../visual-basic/reference/command-line-compiler/index.md)  
 [#If... Then... #Else yönergeleri](../../../visual-basic/language-reference/directives/if-then-else-directives.md)  
 [#Const yönergesi](../../../visual-basic/language-reference/directives/const-directive.md)  
 [Örnek derleme komut satırları](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
