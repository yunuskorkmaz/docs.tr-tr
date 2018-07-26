---
title: -win32icon
ms.date: 03/13/2018
helpviewer_keywords:
- win32icon compiler option [Visual Basic]
- -win32icon compiler option [Visual Basic]
- /win32icon compiler option [Visual Basic]
ms.assetid: aecaab01-9353-46c5-941c-6edabd4eff92
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 045e621f0104c4c958d77d2443c1524b33410b7a
ms.sourcegitcommit: f6343b070f3c66877338a05c8bfb0be9985255e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/24/2018
ms.locfileid: "39221029"
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
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Visual Basic komut satırı derleyicisi](../../../visual-basic/reference/command-line-compiler/index.md)  
 [Örnek Derleme Komut Satırları](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
