---
title: -rootnamespace
ms.date: 03/13/2018
f1_keywords:
- /rootnamespace
- rootnamespace
helpviewer_keywords:
- /rootnamespace compiler option [Visual Basic]
- -rootnamespace compiler option [Visual Basic]
- rootnamespace compiler option [Visual Basic]
ms.assetid: e9245edf-6bef-420d-a7c7-324117752783
ms.openlocfilehash: 4df4e74fc13c922f51f5b74c3c152bdea28b4431
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/07/2019
ms.locfileid: "72005202"
---
# <a name="-rootnamespace"></a>-rootnamespace
Tüm tür bildirimleri için bir ad alanı belirtir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```console  
-rootnamespace:namespace  
```  
  
## <a name="arguments"></a>Bağımsız Değişkenler  
  
|Sözleşme Dönemi|Tanım|  
|---|---|  
|`namespace`|Geçerli proje için tüm tür bildirimlerinin içine alınacağı ad alanının adı.|  
  
## <a name="remarks"></a>Açıklamalar  
 Visual Studio tümleşik geliştirme ortamında oluşturulan bir projeyi derlemek için Visual Studio yürütülebilir dosyası (devenv. exe) kullanırsanız, `-rootnamespace` <xref:VSLangProj80.VBProjectProperties3.RootNamespace%2A> özelliğinin değerini belirtmek için kullanın. Daha fazla bilgi için bkz. [Devenv komut satırı anahtarları](/visualstudio/ide/reference/devenv-command-line-switches) .  
  
 Çıkış dosyanızdaki ad alanı adlarını görüntülemek için ortak dil`Ildasm.exe`çalışma zamanı MSIL Disassembler () kullanın.  
  
|Visual Studio tümleşik geliştirme ortamında Set-RootNamespace|  
|---|  
|1. **Çözüm Gezgini**bir proje seçili olmalıdır. **Proje** menüsünde **Özellikler**' e tıklayın. <br />2. **uygulama** sekmesine tıklayın.<br />3. **kök ad alanı** kutusundaki değeri değiştirin.|  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod, ad `In.vb` alanındaki `mynamespace`tüm tür bildirimlerini derler ve içine alır.  
  
```console
vbc -rootnamespace:mynamespace in.vb  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Visual Basic komut satırı derleyicisi](../../../visual-basic/reference/command-line-compiler/index.md)
- [Ildadsm. exe (Il ayırıcı)](../../../framework/tools/ildasm-exe-il-disassembler.md)
- [Örnek Derleme Komut Satırları](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
