---
title: /nostdlib (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- nostdlib compiler option [Visual Basic]
- -nostdlib compiler option [Visual Basic]
- /nostdlib compiler option [Visual Basic]
ms.assetid: 140381b8-dc96-4ad5-ae11-792c9ed0be4d
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: a9d76563a5b3d439495899e07ce2df59c0acd75e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="nostdlib-visual-basic"></a>/nostdlib (Visual Basic)
Otomatik olarak standart kitaplıkları değil, başvuru için derleyici neden olur.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
/nostdlib  
```  
  
## <a name="remarks"></a>Açıklamalar  
 `/nostdlib` Seçeneği otomatik System.dll derleme başvurusu kaldırır ve derleyici Vbc.rsp dosyayı okumasını önler. Vbc.rsp dosya — Vbc.exe dosya ile aynı dizinde bulunan — yaygın olarak kullanılan başvuran [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] derlemeler ve içeri aktarmalar `System` ve `Microsoft.VisualBasic` ad alanları.  
  
> [!NOTE]
>  Her zaman başvurulan Mscorlib.dll ve Microsoft.VisualBasic.dll içinde derlemeler.  
  
> [!NOTE]
>  `/nostdlib` Seçeneği Visual Studio geliştirme ortamında kullanılabilir değil; yalnızca komut satırından derlerken kullanılabilir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod derlerken `T2.vb` standart kitaplıkları başvuran olmadan. Ayarlamalısınız `_MYTYPE` koşullu derleme sabiti kaldırmak için "boş" dizeye `My` nesnesi.  
  
```  
vbc /nostdlib /define:_MYTYPE=\"Empty\" T2.vb  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [/ noconfig](../../../visual-basic/reference/command-line-compiler/noconfig.md)  
 [Visual Basic komut satırı derleyicisi](../../../visual-basic/reference/command-line-compiler/index.md)  
 [Örnek derleme komut satırları](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)  
 [Özelleştirme hangi nesnelerin kullanılabilir olduğunu My](../../../visual-basic/developing-apps/customizing-extending-my/customizing-which-objects-are-available-in-my.md)
