---
title: /noconfig
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- noconfig compiler option [Visual Basic]
- -noconfig compiler option [Visual Basic]
- /noconfig compiler option [Visual Basic]
ms.assetid: a7405067-bd21-4171-adf4-a126fa3ad6c3
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 94d13ccf0168027f4560b980c41e2a001ff503fd
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="noconfig"></a>/noconfig
Derleyici otomatik olarak yaygın olarak kullanılan başvuru vermemelisiniz olduğunu belirtir [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] derlemeler veya içeri aktarma `System` ve `Microsoft.VisualBasic` ad alanları.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
/noconfig  
```  
  
## <a name="remarks"></a>Açıklamalar  
 `/noconfig` Seçenek Vbc.exe dosya ile aynı dizinde bulunan Vbc.rsp dosyayla değil derlemeye derleyici söyler. Vbc.rsp dosya yaygın olarak kullanılan başvuran [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] derlemeler ve içeri aktarmalar `System` ve `Microsoft.VisualBasic` ad alanları. Derleyici örtük olarak sürece System.dll bütünleştirilmiş koduna başvuruyor `/nostdlib` seçeneği belirtildi. `/nostdlib` Seçeneği ile Vbc.rsp derleme veya otomatik olarak System.dll derleme başvurusu derleyici söyler.  
  
> [!NOTE]
>  Her zaman başvurulan Mscorlib.dll ve Microsoft.VisualBasic.dll içinde derlemeler.  
  
 Her Vbc.exe derlemede dahil edilmesi gereken ek derleyici seçeneklerini belirtmek için Vbc.rsp dosyasını değiştirebilirsiniz (belirtirken dışındaki `/noconfig` seçeneği). Daha fazla bilgi için bkz: [@ (yanıt dosyasını belirtin)](../../../visual-basic/reference/command-line-compiler/specify-response-file.md).  
  
 Derleyici geçirilen seçenekleri işler `vbc` son komutu. Bu nedenle, komut satırında herhangi bir seçenek Vbc.rsp dosyasındaki aynı seçeneği ayarını geçersiz kılar.  
  
> [!NOTE]
>  `/noconfig` Seçeneği Visual Studio geliştirme ortamında kullanılabilir değil; yalnızca komut satırından derlerken kullanılabilir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [/ nostdlib (Visual Basic)](../../../visual-basic/reference/command-line-compiler/nostdlib.md)  
 [Visual Basic komut satırı derleyicisi](../../../visual-basic/reference/command-line-compiler/index.md)  
 [@ (Yanıt dosyasını belirtin)](../../../visual-basic/reference/command-line-compiler/specify-response-file.md)  
 [/ Reference (Visual Basic)](../../../visual-basic/reference/command-line-compiler/reference.md)
