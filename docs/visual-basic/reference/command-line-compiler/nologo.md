---
title: -nologo (Visual Basic)
ms.date: 03/13/2018
helpviewer_keywords:
- -nologo compiler option [Visual Basic]
- banners [Visual Basic], suppressing startup
- nologo compiler option [Visual Basic]
- /nologo compiler option [Visual Basic]
ms.assetid: 25ef54b6-d676-4639-a2d2-a747a158bc07
ms.openlocfilehash: 21c708ef632cc0ed923713cd49e22d44848b4db3
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53131150"
---
# <a name="-nologo-visual-basic"></a>-nologo (Visual Basic)
Derleme sırasında telif hakkı başlığının ve bilgi iletilerinin görüntülenmesini bastırır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
-nologo  
```  
  
## <a name="remarks"></a>Açıklamalar  
 Belirtirseniz `-nologo`, derleyici bir telif hakkı başlık göstermez. Varsayılan olarak, `-nologo` etkili değildir.  
  
> [!NOTE]
>  `-nologo` Seçeneği, Visual Studio geliştirme ortamında kullanılabilir değil; yalnızca komut satırından derleme yapılırken kullanılabilir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod derlenir `T2.vb` ve telif hakkı başlığını göstermez.  
  
```console
vbc -nologo t2.vb  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Visual Basic komut satırı derleyicisi](../../../visual-basic/reference/command-line-compiler/index.md)  
 [Örnek Derleme Komut Satırları](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
