---
title: -noconfig
ms.date: 03/13/2018
helpviewer_keywords:
- noconfig compiler option [Visual Basic]
- -noconfig compiler option [Visual Basic]
- /noconfig compiler option [Visual Basic]
ms.assetid: a7405067-bd21-4171-adf4-a126fa3ad6c3
ms.openlocfilehash: bce2d98a8915e80cdecd7b67029b0c872cf70140
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33650848"
---
# <a name="-noconfig"></a>-noconfig
Derleyici otomatik olarak yaygın olarak kullanılan başvuru vermemelisiniz olduğunu belirtir [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] derlemeler veya içeri aktarma `System` ve `Microsoft.VisualBasic` ad alanları.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
-noconfig  
```  
  
## <a name="remarks"></a>Açıklamalar  
 `-noconfig` Seçenek Vbc.exe dosya ile aynı dizinde bulunan Vbc.rsp dosyayla değil derlemeye derleyici söyler. Vbc.rsp dosya yaygın olarak kullanılan başvuran [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] derlemeler ve içeri aktarmalar `System` ve `Microsoft.VisualBasic` ad alanları. Derleyici örtük olarak sürece System.dll bütünleştirilmiş koduna başvuruyor `-nostdlib` seçeneği belirtildi. `-nostdlib` Seçeneği ile Vbc.rsp derleme veya otomatik olarak System.dll derleme başvurusu derleyici söyler.  
  
> [!NOTE]
>  Her zaman başvurulan Mscorlib.dll ve Microsoft.VisualBasic.dll içinde derlemeler.  
  
 Her Vbc.exe derlemede dahil edilmesi gereken ek derleyici seçeneklerini belirtmek için Vbc.rsp dosyasını değiştirebilirsiniz (belirtirken dışındaki `-noconfig` seçeneği). Daha fazla bilgi için bkz: [@ (yanıt dosyasını belirtin)](../../../visual-basic/reference/command-line-compiler/specify-response-file.md).  
  
 Derleyici geçirilen seçenekleri işler `vbc` son komutu. Bu nedenle, komut satırında herhangi bir seçenek Vbc.rsp dosyasındaki aynı seçeneği ayarını geçersiz kılar.  
  
> [!NOTE]
>  `-noconfig` Seçeneği Visual Studio geliştirme ortamında kullanılabilir değil; yalnızca komut satırından derlerken kullanılabilir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [-nostdlib (Visual Basic)](../../../visual-basic/reference/command-line-compiler/nostdlib.md)  
 [Visual Basic komut satırı derleyicisi](../../../visual-basic/reference/command-line-compiler/index.md)  
 [@ (Yanıt Dosyasını Belirtin)](../../../visual-basic/reference/command-line-compiler/specify-response-file.md)  
 [-başvuru (Visual Basic)](../../../visual-basic/reference/command-line-compiler/reference.md)
