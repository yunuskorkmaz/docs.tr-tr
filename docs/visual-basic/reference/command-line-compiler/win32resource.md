---
title: -win32resource
ms.date: 03/13/2018
f1_keywords:
- -win32resource
- win32resource
helpviewer_keywords:
- /win32resource compiler option [Visual Basic]
- -win32resource compiler option [Visual Basic]
- win32resource compiler option [Visual Basic]
ms.assetid: e226946d-19ce-4cc9-91f5-aed24f77aa2b
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ac495e10be2ec1534dc9d9081aef369773d93e17
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33649880"
---
# <a name="-win32resource"></a>-win32resource
Win32 kaynak dosyasını çıktı dosyasına ekler.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
-win32resource:filename  
```  
  
## <a name="arguments"></a>Arguments  
 `filename`  
 Çıkış dosyanızın eklemek için kaynak dosyanın adı. Dosya adını tırnak işaretleri içine alın ("") boşluk içeriyorsa.  
  
## <a name="remarks"></a>Açıklamalar  
 Microsoft Windows Kaynak Derleyici (RC) ile Win32 kaynak dosyasını oluşturabilirsiniz.  
  
 Win32 kaynak sürüm içerebilir veya yardım eden bir bit eşlem (simgesi) bilgi tanımlamak, uygulamanızda **dosya Gezgini**. Belirtmezseniz, `-win32resource`, derleyici derleme sürümünü temel alan sürüm bilgisi oluşturur. `-win32resource` Ve `-win32icon` seçenekleri karşılıklı olarak birbirini dışlar.  
  
 Bkz: [- linkresource (Visual Basic)](../../../visual-basic/reference/command-line-compiler/linkresource.md) başvurusu için bir [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] kaynak dosyası veya [-kaynak (Visual Basic)](../../../visual-basic/reference/command-line-compiler/resource.md) eklemek için bir [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] kaynak dosyası.  
  
> [!NOTE]
>  `-win32resource` Seçeneği Visual Studio geliştirme ortamında kullanılabilir değil; yalnızca komut satırından derlerken kullanılabilir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod derlerken `In.vb` ve Win32 kaynak dosyasını, iliştirir `Rf.res`:  
  
```console  
vbc -win32resource:rf.res in.vb  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Visual Basic komut satırı derleyicisi](../../../visual-basic/reference/command-line-compiler/index.md)  
 [Örnek Derleme Komut Satırları](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
