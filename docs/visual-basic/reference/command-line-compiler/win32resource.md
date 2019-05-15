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
ms.openlocfilehash: d8f9c9aac87fd71b61a5413386582ae660efd903
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/14/2019
ms.locfileid: "65593079"
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
  
 Bkz: [- linkresource (Visual Basic)](../../../visual-basic/reference/command-line-compiler/linkresource.md) bir .NET Framework kaynak dosyası başvurmak veya [-kaynak (Visual Basic)](../../../visual-basic/reference/command-line-compiler/resource.md) bir .NET Framework kaynak dosyası eklemek için.  
  
> [!NOTE]
>  `-win32resource` Seçeneği, Visual Studio geliştirme ortamında kullanılabilir değil; yalnızca komut satırından derleme yapılırken kullanılabilir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod derlenir `In.vb` ve bir Win32 kaynak dosyası ekler `Rf.res`:  
  
```console  
vbc -win32resource:rf.res in.vb  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Visual Basic komut satırı derleyicisi](../../../visual-basic/reference/command-line-compiler/index.md)
- [Örnek Derleme Komut Satırları](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
