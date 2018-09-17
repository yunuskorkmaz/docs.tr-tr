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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 13bce09ca9fd1ae9ebb919a9245d8ccf87fbde1d
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/17/2018
ms.locfileid: "45692690"
---
# <a name="-rootnamespace"></a>-rootnamespace
Tüm tür bildirimleri için bir ad alanını belirtir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
-rootnamespace:namespace  
```  
  
## <a name="arguments"></a>Arguments  
  
|Terim|Tanım|  
|---|---|  
|`namespace`|Geçerli proje için tüm tür bildirimleri içine almak, ad alanının adı.|  
  
## <a name="remarks"></a>Açıklamalar  
 Visual Studio yürütülebilir dosyası (Devenv.exe) oluşturulmuş bir projeyi derlemek için Visual Studio tümleşik geliştirme ortamında kullanım kullanırsanız `-rootnamespace` değerini belirtmek için <xref:VSLangProj80.VBProjectProperties3.RootNamespace%2A> özelliği. Bkz: [Devenv komut satırı anahtarları](/visualstudio/ide/reference/devenv-command-line-switches) daha fazla bilgi için.  
  
 Ortak dil çalışma zamanı MSIL Disassembler kullanın (`Ildasm.exe`), çıkış dosyasında ad alanı adları görüntülemek için.  
  
|-Rootnamespace Visual Studio tümleşik geliştirme ortamında ayarlamak için|  
|---|  
|1.  Seçili bir projeyi **Çözüm Gezgini**. Üzerinde **proje** menüsünü tıklatın **özellikleri**. <br />2.  Tıklayın **uygulama** sekmesi.<br />3.  Değer değiştirme **kök Namespace** kutusu.|  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod derlenir `In.vb` ve ad alanındaki tüm tür bildirimleri kapsayan `mynamespace`.  
  
```console
vbc -rootnamespace:mynamespace in.vb  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Visual Basic komut satırı derleyicisi](../../../visual-basic/reference/command-line-compiler/index.md)  
- [Ildasm.exe (IL Ayrıştırıcı)](../../../framework/tools/ildasm-exe-il-disassembler.md)  
- [Örnek Derleme Komut Satırları](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
