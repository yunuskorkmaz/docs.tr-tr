---
title: -noconfig
ms.date: 03/13/2018
helpviewer_keywords:
- noconfig compiler option [Visual Basic]
- -noconfig compiler option [Visual Basic]
- /noconfig compiler option [Visual Basic]
ms.assetid: a7405067-bd21-4171-adf4-a126fa3ad6c3
ms.openlocfilehash: b707899c845b6b08e008fe229497f682c930044a
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/14/2019
ms.locfileid: "65588852"
---
# <a name="-noconfig"></a>-noconfig
Derleyicinin otomatik olarak yaygın olarak kullanılan .NET Framework derlemelerine veya içeri aktarma belirtir `System` ve `Microsoft.VisualBasic` ad alanları.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
-noconfig  
```  
  
## <a name="remarks"></a>Açıklamalar  
 `-noconfig` Vbc.exe dosyasıyla aynı dizinde bulunan nezahrnovat dosyası derleme değil derleyici seçeneği söyler. Nezahrnovat dosya yaygın olarak kullanılan .NET Framework derlemeleri atıfta bulunan ve içeri aktarır `System` ve `Microsoft.VisualBasic` ad alanları. Derleyici örtük olarak sürece System.dll derlemeye başvuran `-nostdlib` seçeneği belirtildi. `-nostdlib` Seçeneği söyler derleyicinin nezahrnovat ile derleyin veya otomatik olarak System.dll derleme başvurusu değil.  
  
> [!NOTE]
>  Mscorlib.dll'nin ve Microsoft.VisualBasic.dll'nin derlemeler her zaman başvurulur.  
  
 Her Vbc.exe derlemede dahil edilmesi gereken ek derleyici seçeneklerini belirtmek için nezahrnovat dosyasını değiştirebilirsiniz (belirtirken dışındaki `-noconfig` seçeneği). Daha fazla bilgi için [@ (yanıt dosyası belirtme)](../../../visual-basic/reference/command-line-compiler/specify-response-file.md).  
  
 Derleyici geçirilecek seçeneklerini işler `vbc` son komutu. Bu nedenle, komut satırında herhangi bir seçenek nezahrnovat dosyasında aynı seçeneğinin ayarını geçersiz kılar.  
  
> [!NOTE]
>  `-noconfig` Seçeneği, Visual Studio geliştirme ortamında kullanılabilir değil; yalnızca komut satırından derleme yapılırken kullanılabilir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [-nostdlib (Visual Basic)](../../../visual-basic/reference/command-line-compiler/nostdlib.md)
- [Visual Basic komut satırı derleyicisi](../../../visual-basic/reference/command-line-compiler/index.md)
- [@ (Yanıt Dosyasını Belirtin)](../../../visual-basic/reference/command-line-compiler/specify-response-file.md)
- [-başvuru (Visual Basic)](../../../visual-basic/reference/command-line-compiler/reference.md)
