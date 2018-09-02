---
title: -nostdlib (Visual Basic)
ms.date: 03/13/2018
helpviewer_keywords:
- nostdlib compiler option [Visual Basic]
- -nostdlib compiler option [Visual Basic]
- /nostdlib compiler option [Visual Basic]
ms.assetid: 140381b8-dc96-4ad5-ae11-792c9ed0be4d
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3764409f13a00f6d8a050bfbdd0f59e537a5ded3
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/01/2018
ms.locfileid: "43456298"
---
# <a name="-nostdlib-visual-basic"></a>-nostdlib (Visual Basic)
Standart kitaplıkları otomatik olarak başvuruda bulunmamaya derleyici neden olur.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
-nostdlib  
```  
  
## <a name="remarks"></a>Açıklamalar  
 `-nostdlib` Seçeneği System.dll derleme otomatik başvuruyu kaldırır ve derleyici nezahrnovat dosyayı okumasını önler. Yaygın olarak kullanılan Vbc.exe dosyasıyla aynı dizinde bulunan nezahrnovat dosyasını başvuran [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] derlemeler ve içeri aktarmalar `System` ve `Microsoft.VisualBasic` ad alanları.  
  
> [!NOTE]
>  Mscorlib.dll'nin ve Microsoft.VisualBasic.dll'nin derlemeler her zaman başvurulur.  
  
> [!NOTE]
>  `-nostdlib` Seçeneği, Visual Studio geliştirme ortamında kullanılabilir değil; yalnızca komut satırından derleme yapılırken kullanılabilir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod derlenir `T2.vb` standart kitaplıklarına başvuruda bulunan olmadan. Ayarlamalısınız `_MYTYPE` koşullu derleme sabiti'kaldırmak için "boş" dizeye `My` nesne.  
  
```console
vbc -nostdlib -define:_MYTYPE=\"Empty\" T2.vb  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [-noconfig](../../../visual-basic/reference/command-line-compiler/noconfig.md)  
 [Visual Basic komut satırı derleyicisi](../../../visual-basic/reference/command-line-compiler/index.md)  
 [Örnek Derleme Komut Satırları](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)  
 [My Özelliklerinde Hangi Nesnelerin Kullanılabilir Olduğunu Özelleştirme](../../../visual-basic/developing-apps/customizing-extending-my/customizing-which-objects-are-available-in-my.md)
