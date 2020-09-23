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
ms.openlocfilehash: cb56e727479fd249cb0d7e5e7c3c50d5b68b3a72
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91072021"
---
# <a name="-define-visual-basic"></a>-tanımla (Visual Basic)

Koşullu derleyici sabitlerini tanımlar.  
  
## <a name="syntax"></a>Syntax  
  
```console  
-define:["]symbol[=value][,symbol[=value]]["]  
```

veya

```console  
-d:["]symbol[=value][,symbol[=value]]["]  
```  
  
## <a name="arguments"></a>Bağımsız değişkenler  
  
|Terim|Tanım|  
|---|---|  
|`symbol`|Gereklidir. Tanımlanacak simge.|  
|`value`|İsteğe bağlı. Atanacak değer `symbol` . `value`Bir dizeyse, tırnak işaretleri yerine ters eğik çizgi/tırnak işareti dizileri ( \\ ") arasına alınmalıdır. Hiçbir değer belirtilmemişse, true olarak alınır.|  
  
## <a name="remarks"></a>Açıklamalar  

 `-define`Bu seçenek, kaynak dosyanızda ön işlemci yönergesini kullanmayla benzer bir etkiye sahiptir `#Const` , ancak ile tanımlanmış sabitler `-define` ortak olur ve projedeki tüm dosyalar için geçerlidir.  
  
 Bu seçenek tarafından oluşturulan sembolleri `#If` .. `Then` . ile kullanabilirsiniz. ...`#Else` kaynak dosyaları koşullu olarak derlemek için yönerge.  
  
 `-d` , öğesinin kısa biçimidir `-define` .  
  
 `-define`Sembol tanımlarını ayırmak için virgül kullanarak birden çok sembol tanımlayabilirsiniz.  
  
|Visual Studio tümleşik geliştirme ortamında ayarlamak için|  
|---|  
|1. **Çözüm Gezgini**bir proje seçili olmalıdır. **Proje** menüsünde **Özellikler**' e tıklayın. <br />2. **Derle** sekmesine tıklayın.<br />3. **Gelişmiş**'e tıklayın.<br />4. **Özel sabitler** kutusundaki değeri değiştirin.|  
  
## <a name="example"></a>Örnek  

 Aşağıdaki kod, iki koşullu derleyici sabiti tanımlar ve kullanır.  
  
 [!code-vb[VbVbalrCompiler#45](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCompiler/VB/Class1.vb#45)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Visual Basic komut satırı derleyicisi](index.md)
- [#If... Sonra... #Else yönergeler](../../language-reference/directives/if-then-else-directives.md)
- [#Const Yönergesi](../../language-reference/directives/const-directive.md)
- [Örnek Derleme Komut Satırları](sample-compilation-command-lines.md)
