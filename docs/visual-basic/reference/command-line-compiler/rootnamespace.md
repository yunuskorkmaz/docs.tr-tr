---
description: :-RootNamespace hakkında daha fazla bilgi edinin
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
ms.openlocfilehash: 0e034999a65bf5294e63c8f9cec1a4ce4de39a4b
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100474089"
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
|1. **Çözüm Gezgini** bir proje seçili olmalıdır. **Proje** menüsünde **Özellikler**' e tıklayın. <br />2. **uygulama** sekmesine tıklayın.<br />3. **kök ad alanı** kutusundaki değeri değiştirin.|  
  
## <a name="example"></a>Örnek  

 Aşağıdaki kod, `In.vb` ad alanındaki tüm tür bildirimlerini derler ve içine alır `mynamespace` .  
  
```console
vbc -rootnamespace:mynamespace in.vb  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Visual Basic Command-Line derleyicisi](index.md)
- [Ildasm.exe (Il ayırıcı)](../../../framework/tools/ildasm-exe-il-disassembler.md)
- [Örnek Derleme Komut Satırları](sample-compilation-command-lines.md)
