---
title: -noconfig
ms.date: 03/13/2018
helpviewer_keywords:
- noconfig compiler option [Visual Basic]
- -noconfig compiler option [Visual Basic]
- /noconfig compiler option [Visual Basic]
ms.assetid: a7405067-bd21-4171-adf4-a126fa3ad6c3
ms.openlocfilehash: bce2d98a8915e80cdecd7b67029b0c872cf70140
ms.sourcegitcommit: 60645077dc4b62178403145f8ef691b13ffec28e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2018
ms.locfileid: "37959585"
---
# <a name="-noconfig"></a>-noconfig
Derleyicinin otomatik olarak yaygın olarak kullanılan başvurmamalıdır olduğunu belirtir [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] derlemeleri veya içeri aktarma `System` ve `Microsoft.VisualBasic` ad alanları.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
-noconfig  
```  
  
## <a name="remarks"></a>Açıklamalar  
 `-noconfig` Vbc.exe dosyasıyla aynı dizinde bulunan nezahrnovat dosyası derleme değil derleyici seçeneği söyler. Nezahrnovat dosya yaygın olarak kullanılan başvuran [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] derlemeler ve içeri aktarmalar `System` ve `Microsoft.VisualBasic` ad alanları. Derleyici örtük olarak sürece System.dll derlemeye başvuran `-nostdlib` seçeneği belirtildi. `-nostdlib` Seçeneği söyler derleyicinin nezahrnovat ile derleyin veya otomatik olarak System.dll derleme başvurusu değil.  
  
> [!NOTE]
>  Mscorlib.dll'nin ve Microsoft.VisualBasic.dll'nin derlemeler her zaman başvurulur.  
  
 Her Vbc.exe derlemede dahil edilmesi gereken ek derleyici seçeneklerini belirtmek için nezahrnovat dosyasını değiştirebilirsiniz (belirtirken dışındaki `-noconfig` seçeneği). Daha fazla bilgi için [@ (yanıt dosyası belirtme)](../../../visual-basic/reference/command-line-compiler/specify-response-file.md).  
  
 Derleyici geçirilecek seçeneklerini işler `vbc` son komutu. Bu nedenle, komut satırında herhangi bir seçenek nezahrnovat dosyasında aynı seçeneğinin ayarını geçersiz kılar.  
  
> [!NOTE]
>  `-noconfig` Seçeneği, Visual Studio geliştirme ortamında kullanılabilir değil; yalnızca komut satırından derleme yapılırken kullanılabilir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [-nostdlib (Visual Basic)](../../../visual-basic/reference/command-line-compiler/nostdlib.md)  
 [Visual Basic komut satırı derleyicisi](../../../visual-basic/reference/command-line-compiler/index.md)  
 [@ (Yanıt Dosyasını Belirtin)](../../../visual-basic/reference/command-line-compiler/specify-response-file.md)  
 [-başvuru (Visual Basic)](../../../visual-basic/reference/command-line-compiler/reference.md)
