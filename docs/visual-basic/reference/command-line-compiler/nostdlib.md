---
title: -nostdlib (Visual Basic)
ms.date: 03/13/2018
ms.prod: .net
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- nostdlib compiler option [Visual Basic]
- -nostdlib compiler option [Visual Basic]
- /nostdlib compiler option [Visual Basic]
ms.assetid: 140381b8-dc96-4ad5-ae11-792c9ed0be4d
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 14361c01d13238db8f820b43889716e2528097f5
ms.sourcegitcommit: 498799639937c89de777361aab74261efe7b79ea
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/22/2018
---
# <a name="-nostdlib-visual-basic"></a>-nostdlib (Visual Basic)
Otomatik olarak standart kitaplıkları değil, başvuru için derleyici neden olur.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
-nostdlib  
```  
  
## <a name="remarks"></a>Açıklamalar  
 `-nostdlib` Seçeneği otomatik System.dll derleme başvurusu kaldırır ve derleyici Vbc.rsp dosyayı okumasını önler. Vbc.exe dosya ile aynı dizinde bulunan Vbc.rsp dosyasını yaygın olarak kullanılan başvuran [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] derlemeler ve içeri aktarmalar `System` ve `Microsoft.VisualBasic` ad alanları.  
  
> [!NOTE]
>  Her zaman başvurulan Mscorlib.dll ve Microsoft.VisualBasic.dll içinde derlemeler.  
  
> [!NOTE]
>  `-nostdlib` Seçeneği Visual Studio geliştirme ortamında kullanılabilir değil; yalnızca komut satırından derlerken kullanılabilir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod derlerken `T2.vb` standart kitaplıkları başvuran olmadan. Ayarlamalısınız `_MYTYPE` koşullu derleme sabiti kaldırmak için "boş" dizeye `My` nesnesi.  
  
```console
vbc -nostdlib -define:_MYTYPE=\"Empty\" T2.vb  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [-noconfig](../../../visual-basic/reference/command-line-compiler/noconfig.md)  
 [Visual Basic komut satırı derleyicisi](../../../visual-basic/reference/command-line-compiler/index.md)  
 [Örnek Derleme Komut Satırları](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)  
 [My Özelliklerinde Hangi Nesnelerin Kullanılabilir Olduğunu Özelleştirme](../../../visual-basic/developing-apps/customizing-extending-my/customizing-which-objects-are-available-in-my.md)
