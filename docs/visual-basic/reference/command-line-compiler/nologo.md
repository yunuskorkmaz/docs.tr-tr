---
title: -nologo
ms.date: 03/13/2018
helpviewer_keywords:
- -nologo compiler option [Visual Basic]
- banners [Visual Basic], suppressing startup
- nologo compiler option [Visual Basic]
- /nologo compiler option [Visual Basic]
ms.assetid: 25ef54b6-d676-4639-a2d2-a747a158bc07
ms.openlocfilehash: 03dc98c45a894304a67765c3e49cd19bbb089c8c
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74335429"
---
# <a name="-nologo-visual-basic"></a>-nologo (Visual Basic)
Derleme sırasında telif hakkı başlığının ve bilgilendirici mesajların görüntülenmesini önler.  
  
## <a name="syntax"></a>Sözdizimi  
  
```console  
-nologo  
```  
  
## <a name="remarks"></a>Açıklamalar  
 Belirtirseniz `-nologo`, derleyici bir telif hakkı başlığını görüntülemez. Varsayılan `-nologo` olarak etkin değildir.  
  
> [!NOTE]
> Bu `-nologo` seçenek, Visual Studio geliştirme ortamı içinden kullanılamaz; yalnızca komut satırından derlenirken kullanılabilir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod, bir `T2.vb` telif hakkı başlığını derler ve göstermez.  
  
```console
vbc -nologo t2.vb  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Visual Basic komut satırı derleyicisi](../../../visual-basic/reference/command-line-compiler/index.md)
- [Örnek Derleme Komut Satırları](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
