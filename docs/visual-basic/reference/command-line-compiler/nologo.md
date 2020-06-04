---
title: -nologo
ms.date: 03/13/2018
helpviewer_keywords:
- -nologo compiler option [Visual Basic]
- banners [Visual Basic], suppressing startup
- nologo compiler option [Visual Basic]
- /nologo compiler option [Visual Basic]
ms.assetid: 25ef54b6-d676-4639-a2d2-a747a158bc07
ms.openlocfilehash: d1307603ebc06b4eb4c3786f1cd2fb432c0cf636
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84360468"
---
# <a name="-nologo-visual-basic"></a>-nologo (Visual Basic)
Derleme sırasında telif hakkı başlığının ve bilgilendirici mesajların görüntülenmesini önler.  
  
## <a name="syntax"></a>Sözdizimi  
  
```console  
-nologo  
```  
  
## <a name="remarks"></a>Açıklamalar  
 Belirtirseniz `-nologo` , derleyici bir telif hakkı başlığını görüntülemez. Varsayılan olarak `-nologo` etkin değildir.  
  
> [!NOTE]
> `-nologo`Bu seçenek, Visual Studio geliştirme ortamı içinden kullanılamaz; yalnızca komut satırından derlenirken kullanılabilir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod, `T2.vb` bir telif hakkı başlığını derler ve göstermez.  
  
```console
vbc -nologo t2.vb  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Visual Basic komut satırı derleyicisi](index.md)
- [Örnek Derleme Komut Satırları](sample-compilation-command-lines.md)
