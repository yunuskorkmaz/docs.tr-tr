---
title: -define
ms.date: 03/10/2018
helpviewer_keywords:
- -d compiler option [Visual Basic]
- /d compiler option [Visual Basic]
- -define compiler option [Visual Basic]
- d compiler option [Visual Basic]
- /define compiler option [Visual Basic]
- define compiler option [Visual Basic]
ms.assetid: f735c57d-1cf9-4f2f-a26f-0de630fd4077
ms.openlocfilehash: 5035466de4aa17c374824e1b0f02ed594731a9d3
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75716805"
---
# <a name="-define-visual-basic"></a>-tanımla (Visual Basic)
Koşullu derleyici sabitlerini tanımlar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```console  
-define:["]symbol[=value][,symbol[=value]]["]  
```

or

```console  
-d:["]symbol[=value][,symbol[=value]]["]  
```  
  
## <a name="arguments"></a>Bağımsız Değişkenler  
  
|Sözleşme Dönemi|Tanım|  
|---|---|  
|`symbol`|Gereklidir. Tanımlanacak simge.|  
|`value`|İsteğe bağlı. Atanacak `symbol`değer. `value` Bir dizeyse, tırnak işaretleri yerine ters eğik çizgi/tırnak işareti dizileri (\\") arasına alınmalıdır. Hiçbir değer belirtilmemişse, true olarak alınır.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bu `-define` seçenek, kaynak dosyanızda ön `#Const` işlemci yönergesini kullanmayla benzer bir etkiye sahiptir, ancak ile `-define` tanımlanmış sabitler ortak olur ve projedeki tüm dosyalar için geçerlidir.  
  
 Bu seçenek tarafından oluşturulan sembolleri `#If`... ile kullanabilirsiniz. `Then`... `#Else` kaynak dosyaları koşullu olarak derlemek için yönerge.  
  
 `-d`, öğesinin `-define`kısa biçimidir.  
  
 Sembol tanımlarını ayırmak için virgül kullanarak `-define` birden çok sembol tanımlayabilirsiniz.  
  
|Visual Studio tümleşik geliştirme ortamında ayarlamak için|  
|---|  
|1. **Çözüm Gezgini**bir proje seçili olmalıdır. **Proje** menüsünde **Özellikler**' e tıklayın. <br />2. **Derle** sekmesine tıklayın.<br />3. **Gelişmiş**'e tıklayın.<br />4. **Özel sabitler** kutusundaki değeri değiştirin.|  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod, iki koşullu derleyici sabiti tanımlar ve kullanır.  
  
 [!code-vb[VbVbalrCompiler#45](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCompiler/VB/Class1.vb#45)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Visual Basic komut satırı derleyicisi](../../../visual-basic/reference/command-line-compiler/index.md)
- [#If... Sonra... #Else yönergeler](../../../visual-basic/language-reference/directives/if-then-else-directives.md)
- [#Const Yönergesi](../../../visual-basic/language-reference/directives/const-directive.md)
- [Örnek Derleme Komut Satırları](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
