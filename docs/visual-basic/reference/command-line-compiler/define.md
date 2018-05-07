---
title: -tanımlama (Visual Basic)
ms.date: 03/10/2018
helpviewer_keywords:
- -d compiler option [Visual Basic]
- /d compiler option [Visual Basic]
- -define compiler option [Visual Basic]
- d compiler option [Visual Basic]
- /define compiler option [Visual Basic]
- define compiler option [Visual Basic]
ms.assetid: f735c57d-1cf9-4f2f-a26f-0de630fd4077
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4de37c58543aed9ed13be8b0d2bcec9830ca9082
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="-define-visual-basic"></a>-tanımlama (Visual Basic)
Koşullu derleme sabitleri tanımlar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
-define:["]symbol[=value][,symbol[=value]]["]  
' -or-  
-d:["]symbol[=value][,symbol[=value]]["]  
```  
  
## <a name="arguments"></a>Arguments  
  
|Terim|Tanım|  
|---|---|  
|`symbol`|Gerekli. Tanımlamak için simge.|  
|`value`|İsteğe bağlı. Atanacak değer `symbol`. Varsa `value` bir dizedir ters eğik çizgi /-tırnağından sıraları ile alınmalıdır (\\") tırnak işareti yerine. Değer belirtilmedi sonra olması için geçen True.|  
  
## <a name="remarks"></a>Açıklamalar  
 `-define` Seçeneği bir etkisi kullanmaya benzer bir `#Const` ile tanımlanmış bu sabitleri dışında kaynak dosyanızdaki önişlemci yönergesi `-define` ortak ve projedeki tüm dosyalar için geçerlidir.  
  
 Bu seçenek ile tarafından oluşturulan simgeleri kullanabilirsiniz `#If`... `Then`... `#Else` kaynak dosyaları koşullu derleme yönergesi.  
  
 `-d` kısa biçimi olan `-define`.  
  
 Birden çok sembolleriyle tanımlayabilirsiniz `-define` simge tanımlarını ayırmak için virgül kullanarak.  
  
|Ayarlamak için Visual Studio tümleşik geliştirme ortamında tanımlayın|  
|---|  
|1.  Seçili bir projeyi **Çözüm Gezgini**. Üzerinde **proje** menüsünde tıklatın **özellikleri**. <br />2.  Tıklatın **derleme** sekmesi.<br />3.  **Gelişmiş**'e tıklayın.<br />4.  Değer değiştirme **özel sabitleri** kutusu.|  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod tanımlar ve iki koşullu derleyici sabitleri kullanır.  
  
 [!code-vb[VbVbalrCompiler#45](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/define_1.vb)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Visual Basic komut satırı derleyicisi](../../../visual-basic/reference/command-line-compiler/index.md)  
 [#If...Then...#Else Yönergesi](../../../visual-basic/language-reference/directives/if-then-else-directives.md)  
 [#Const Yönergesi](../../../visual-basic/language-reference/directives/const-directive.md)  
 [Örnek Derleme Komut Satırları](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
