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
ms.openlocfilehash: ff4b1729f1b9fb1d698b4b5b1e3711ce3d27b4db
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61639041"
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
