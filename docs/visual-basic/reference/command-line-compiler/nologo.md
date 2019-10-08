---
title: -nologo (Visual Basic)
ms.date: 03/13/2018
helpviewer_keywords:
- -nologo compiler option [Visual Basic]
- banners [Visual Basic], suppressing startup
- nologo compiler option [Visual Basic]
- /nologo compiler option [Visual Basic]
ms.assetid: 25ef54b6-d676-4639-a2d2-a747a158bc07
ms.openlocfilehash: bb64a468f67745b80b47b42c4fac18852279035d
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/07/2019
ms.locfileid: "72005429"
---
# <a name="-nologo-visual-basic"></a>-nologo (Visual Basic)
Derleme sırasında telif hakkı başlığının ve bilgilendirici mesajların görüntülenmesini önler.  
  
## <a name="syntax"></a>Sözdizimi  
  
```console  
-nologo  
```  
  
## <a name="remarks"></a>Açıklamalar  
 @No__t-0 belirtirseniz, derleyici bir telif hakkı başlığını görüntülemez. Varsayılan olarak, `-nologo` geçerli değildir.  
  
> [!NOTE]
> @No__t-0 seçeneği, Visual Studio geliştirme ortamı içinden kullanılamaz; yalnızca komut satırından derlenirken kullanılabilir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod `T2.vb` derler ve bir telif hakkı başlığını görüntülemez.  
  
```console
vbc -nologo t2.vb  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Visual Basic komut satırı derleyicisi](../../../visual-basic/reference/command-line-compiler/index.md)
- [Örnek Derleme Komut Satırları](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
