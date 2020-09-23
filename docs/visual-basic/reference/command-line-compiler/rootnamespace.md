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
ms.openlocfilehash: d9388ace03f654458eb955e989673b7441e72f23
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91085145"
---
# <a name="-rootnamespace"></a>-rootnamespace

Tüm tür bildirimleri için bir ad alanı belirtir.  
  
## <a name="syntax"></a>Söz dizimi  
  
```console  
-rootnamespace:namespace  
```  
  
## <a name="arguments"></a>Bağımsız değişkenler  
  
|Terim|Tanım|  
|---|---|  
|`namespace`|Geçerli proje için tüm tür bildirimlerinin içine alınacağı ad alanının adı.|  
  
## <a name="remarks"></a>Açıklamalar  

 Visual Studio tümleşik geliştirme ortamında oluşturulan bir projeyi derlemek için Visual Studio çalıştırılabilir dosyasını (Devenv.exe) kullanıyorsanız, `-rootnamespace` özelliğin değerini belirtmek için kullanın <xref:VSLangProj80.VBProjectProperties3.RootNamespace%2A> . Daha fazla bilgi için bkz. [Devenv komut satırı anahtarları](/visualstudio/ide/reference/devenv-command-line-switches) .  
  
 `Ildasm.exe`Çıkış dosyanızdaki ad alanı adlarını görüntülemek için ortak dil çalışma zamanı MSIL Disassembler () kullanın.  
  
|Visual Studio tümleşik geliştirme ortamında Set-RootNamespace|  
|---|  
|1. **Çözüm Gezgini**bir proje seçili olmalıdır. **Proje** menüsünde **Özellikler**' e tıklayın. <br />2. **uygulama** sekmesine tıklayın.<br />3. **kök ad alanı** kutusundaki değeri değiştirin.|  
  
## <a name="example"></a>Örnek  

 Aşağıdaki kod, `In.vb` ad alanındaki tüm tür bildirimlerini derler ve içine alır `mynamespace` .  
  
```console
vbc -rootnamespace:mynamespace in.vb  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Visual Basic komut satırı derleyicisi](index.md)
- [Ildasm.exe (Il ayırıcı)](../../../framework/tools/ildasm-exe-il-disassembler.md)
- [Örnek Derleme Komut Satırları](sample-compilation-command-lines.md)
