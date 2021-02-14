---
description: Hakkında daha fazla bilgi edinin:-nologo (Visual Basic)
title: -nologo
ms.date: 03/13/2018
helpviewer_keywords:
- -nologo compiler option [Visual Basic]
- banners [Visual Basic], suppressing startup
- nologo compiler option [Visual Basic]
- /nologo compiler option [Visual Basic]
ms.assetid: 25ef54b6-d676-4639-a2d2-a747a158bc07
ms.openlocfilehash: 370889fbd5d4e499ba27ff8bee4adc16a7a71876
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100434894"
---
# <a name="-nologo-visual-basic"></a>-nologo (Visual Basic)

Derleme sırasında telif hakkı başlığının ve bilgilendirici mesajların görüntülenmesini önler.  
  
## <a name="syntax"></a>Syntax  
  
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

- [Visual Basic Command-Line derleyicisi](index.md)
- [Örnek Derleme Komut Satırları](sample-compilation-command-lines.md)
