---
title: -nologo (Visual Basic)
ms.date: 03/13/2018
helpviewer_keywords:
- -nologo compiler option [Visual Basic]
- banners [Visual Basic], suppressing startup
- nologo compiler option [Visual Basic]
- /nologo compiler option [Visual Basic]
ms.assetid: 25ef54b6-d676-4639-a2d2-a747a158bc07
ms.openlocfilehash: c1824e4a086ecdd4b6a776bd6894f6e003d02867
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "58822563"
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
  
## <a name="see-also"></a>Ayrıca bkz.

- [Visual Basic komut satırı derleyicisi](../../../visual-basic/reference/command-line-compiler/index.md)
- [Örnek Derleme Komut Satırları](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
