---
title: -win32icon
ms.date: 03/13/2018
ms.prod: .net
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- win32icon compiler option [Visual Basic]
- -win32icon compiler option [Visual Basic]
- /win32icon compiler option [Visual Basic]
ms.assetid: aecaab01-9353-46c5-941c-6edabd4eff92
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 95b2e2b4542f2e396a136f6a3d9baeb3e0c037a3
ms.sourcegitcommit: 498799639937c89de777361aab74261efe7b79ea
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/22/2018
---
# <a name="-win32icon"></a>-win32icon
Bir .ico dosyasını çıktı dosyasına ekler. Çıktı dosyasında bu .ico dosyasını temsil eden **dosya Gezgini**.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
-win32icon:filename  
```  
  
## <a name="arguments"></a>Arguments  
  
|Terim|Tanım|  
|---|---|  
|`filename`|Çıkış dosyanızın eklemek için .ico dosyasını. Dosya adını tırnak işaretleri içine alın ("") boşluk içeriyorsa.|  
  
## <a name="remarks"></a>Açıklamalar  
 Microsoft Windows Kaynak Derleyici (RC) ile bir .ico dosyasını oluşturabilirsiniz. Kaynak derleyicisi bir Visual C++ programını derleme yaparken çağrılır; .rc dosyasından bir .ico dosyası oluşturulur. `-win32icon` Ve `-win32resource` seçenekleri karşılıklı olarak birbirini dışlar.  
  
 Bkz: [- linkresource (Visual Basic)](../../../visual-basic/reference/command-line-compiler/linkresource.md) başvurusu için bir [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] kaynak dosyası veya [-kaynak (Visual Basic)](../../../visual-basic/reference/command-line-compiler/resource.md) eklemek için bir [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] kaynak dosyası. Bkz: [-win32resource](../../../visual-basic/reference/command-line-compiler/win32resource.md) .res dosyasını içeri aktarmak için.  
  
|Ayarlanacak - win32icon Visual Studio IDE içinde|  
|---|  
|1.  Seçili bir projeyi **Çözüm Gezgini**. Üzerinde **proje** menüsünde tıklatın **özellikleri**. <br />2.  Tıklatın **uygulama** sekmesi.<br />3.  Değer değiştirme **simgesi** kutusu.|  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod derlerken `In.vb` ve bir .ico dosyasını ekler `Rf.ico`.  
  
```console
vbc -win32icon:rf.ico in.vb  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Visual Basic komut satırı derleyicisi](../../../visual-basic/reference/command-line-compiler/index.md)  
 [Örnek Derleme Komut Satırları](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
