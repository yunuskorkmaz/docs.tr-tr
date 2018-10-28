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
ms.openlocfilehash: 4ecac4ffe665d724d625aaeb7cc1e008eb13ca54
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/27/2018
ms.locfileid: "50186089"
---
# <a name="-win32resource"></a>-win32resource
Bir Win32 kaynak dosyası çıkış dosyasına ekler.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
-win32resource:filename  
```  
  
## <a name="arguments"></a>Arguments  
 `filename`  
 Çıkış dosyanızı eklemek için kaynak dosyanın adı. Dosya adı tırnak içine alın ("") bir boşluk içeriyorsa.  
  
## <a name="remarks"></a>Açıklamalar  
 Microsoft Windows Kaynak derleyicisi (RC) ile bir Win32 kaynak dosyası oluşturabilirsiniz.  
  
 Bir Win32 kaynağı sürümü içerebilir veya yardımcı olan bit eşlem (simge) bilgileri, uygulamanızda tanımlamak **dosya Gezgini**. Siz belirtmezseniz `-win32resource`, derleyici derleme sürümünü temel alan sürüm bilgisi oluşturur. `-win32resource` Ve `-win32icon` seçenekleri karşılıklı olarak birbirini dışlar.  
  
 Bkz: [- linkresource (Visual Basic)](../../../visual-basic/reference/command-line-compiler/linkresource.md) başvurmak için bir [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] kaynak dosyası veya [-kaynak (Visual Basic)](../../../visual-basic/reference/command-line-compiler/resource.md) eklemek için bir [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] kaynak dosyası.  
  
> [!NOTE]
>  `-win32resource` Seçeneği, Visual Studio geliştirme ortamında kullanılabilir değil; yalnızca komut satırından derleme yapılırken kullanılabilir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod derlenir `In.vb` ve bir Win32 kaynak dosyası ekler `Rf.res`:  
  
```console  
vbc -win32resource:rf.res in.vb  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Visual Basic komut satırı derleyicisi](../../../visual-basic/reference/command-line-compiler/index.md)  
 [Örnek Derleme Komut Satırları](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
