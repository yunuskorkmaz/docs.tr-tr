---
title: -tanımla (Visual Basic)
ms.date: 03/10/2018
helpviewer_keywords:
- -d compiler option [Visual Basic]
- /d compiler option [Visual Basic]
- -define compiler option [Visual Basic]
- d compiler option [Visual Basic]
- /define compiler option [Visual Basic]
- define compiler option [Visual Basic]
ms.assetid: f735c57d-1cf9-4f2f-a26f-0de630fd4077
ms.openlocfilehash: 5b2c0173416418f67446c5441a93e5b06e93dc12
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/07/2019
ms.locfileid: "72002375"
---
# <a name="-define-visual-basic"></a>-tanımla (Visual Basic)
Koşullu derleyici sabitlerini tanımlar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```console  
-define:["]symbol[=value][,symbol[=value]]["]  
```

veya

```console  
-d:["]symbol[=value][,symbol[=value]]["]  
```  
  
## <a name="arguments"></a>Arguments  
  
|Terim|Tanım|  
|---|---|  
|`symbol`|Gerekli. Tanımlanacak simge.|  
|`value`|İsteğe bağlı. @No__t atanacak değer-0. @No__t-0 bir dizeyse, tırnak işaretleri yerine ters eğik çizgi/tırnak işareti dizileri (\\ ") arasına alınmalıdır. Hiçbir değer belirtilmemişse, true olarak alınır.|  
  
## <a name="remarks"></a>Açıklamalar  
 @No__t-0 seçeneği, kaynak dosyanızda `#Const` önişlemcisi yönergesini kullanmayla benzer bir etkiye sahiptir, ancak `-define` ile tanımlanmış sabitler ortak olur ve projedeki tüm dosyalar için geçerlidir.  
  
 Bu seçenek tarafından oluşturulan sembolleri, kaynak dosyaları koşullu olarak derlemek için `#If`... `Then`... `#Else` yönergesi ile kullanabilirsiniz.  
  
 `-d`, `-define` ' in kısa biçimidir.  
  
 Sembol tanımlarını ayırmak için virgül kullanarak, `-define` ile birden çok sembol tanımlayabilirsiniz.  
  
|Visual Studio tümleşik geliştirme ortamında/define ayarlamak için|  
|---|  
|1. **Çözüm Gezgini**bir proje seçili olmalıdır. **Proje** menüsünde **Özellikler**' e tıklayın. <br />2. **Derle** sekmesine tıklayın.<br />3. **Gelişmiş**'e tıklayın.<br />4. **Özel sabitler** kutusundaki değeri değiştirin.|  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod, iki koşullu derleyici sabiti tanımlar ve kullanır.  
  
 [!code-vb[VbVbalrCompiler#45](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCompiler/VB/Class1.vb#45)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Visual Basic komut satırı derleyicisi](../../../visual-basic/reference/command-line-compiler/index.md)
- [#If...Then...#Else Yönergesi](../../../visual-basic/language-reference/directives/if-then-else-directives.md)
- [#Const Yönergesi](../../../visual-basic/language-reference/directives/const-directive.md)
- [Örnek Derleme Komut Satırları](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
