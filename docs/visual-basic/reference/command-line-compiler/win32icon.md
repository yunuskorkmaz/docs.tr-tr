---
title: -win32icon
ms.date: 03/13/2018
helpviewer_keywords:
- win32icon compiler option [Visual Basic]
- -win32icon compiler option [Visual Basic]
- /win32icon compiler option [Visual Basic]
ms.assetid: aecaab01-9353-46c5-941c-6edabd4eff92
ms.openlocfilehash: e36e9187ab8c9c2b4950a66ff8ff3fc93adbd9c4
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61774835"
---
# <a name="-win32icon"></a>-win32icon
Çıktı dosyasına bir .ico simge dosyası ekler. Bu .ico dosyasını temsil eder çıkış dosyasında **dosya Gezgini**.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
-win32icon:filename  
```  
  
## <a name="arguments"></a>Arguments  
  
|Terim|Tanım|  
|---|---|  
|`filename`|Çıkış dosyanızı eklemek için .ico dosyası. Dosya adı tırnak içine alın ("") bir boşluk içeriyorsa.|  
  
## <a name="remarks"></a>Açıklamalar  
 Microsoft Windows Kaynak derleyicisi (RC) olan bir .ico simge dosyası oluşturabilirsiniz. Kaynak derleyicisi, bir Visual C++ programını derlerken çağrılır; .rc dosyasından bir .ico simge dosyası oluşturulur. `-win32icon` Ve `-win32resource` seçenekleri karşılıklı olarak birbirini dışlar.  
  
 Bkz: [- linkresource (Visual Basic)](../../../visual-basic/reference/command-line-compiler/linkresource.md) başvurmak için bir [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] kaynak dosyası veya [-kaynak (Visual Basic)](../../../visual-basic/reference/command-line-compiler/resource.md) eklemek için bir [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] kaynak dosyası. Bkz: [-win32resource](../../../visual-basic/reference/command-line-compiler/win32resource.md) bir .res dosyası içeri aktarmak için.  
  
|Ayarlanacak - Visual Studio IDE'de win32icon|  
|---|  
|1.  Seçili bir projeyi **Çözüm Gezgini**. Üzerinde **proje** menüsünü tıklatın **özellikleri**. <br />2.  Tıklayın **uygulama** sekmesi.<br />3.  Değer değiştirme **simgesi** kutusu.|  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod derlenir `In.vb` ve bir .ico simge dosyası ekler `Rf.ico`.  
  
```console
vbc -win32icon:rf.ico in.vb  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Visual Basic komut satırı derleyicisi](../../../visual-basic/reference/command-line-compiler/index.md)
- [Örnek Derleme Komut Satırları](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
