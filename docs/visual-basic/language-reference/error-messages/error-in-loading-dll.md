---
description: 'Hakkında daha fazla bilgi edinin: DLL yüklenirken hata (Visual Basic)'
title: DLL dosyasını yüklemede hata
ms.date: 07/20/2015
f1_keywords:
- vbrID48
ms.assetid: 4226cd1f-028c-477d-88a5-cb57f7e0cdc8
ms.openlocfilehash: 098d05e93d328f3667000bd81290f4b77cf7949e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99796515"
---
# <a name="error-in-loading-dll-visual-basic"></a>DLL yüklenirken hata (Visual Basic)

Dinamik bağlantı kitaplığı (DLL), `Lib` bir deyimin yan tümcesinde belirtilen bir kitaplıktır `Declare` . Bu hatanın olası nedenleri şunlardır:  
  
- Dosya DLL yürütülebilir dosyası değil.  
  
- Dosya bir Microsoft Windows DLL 'i değil.  
  
- DLL, mevcut olmayan başka bir DLL 'ye başvuruyor.  
  
- DLL veya başvurulan DLL, yolda belirtilen bir dizin içinde değil.  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
- Dosya bir kaynak-metin dosyasıdır ve bu nedenle DLL yürütülebilir dosyası değilse, derlenmesi ve DLL yürütülebilir bir formla ilişkilendirilmesi gerekir.  
  
- Dosya bir Microsoft Windows DLL değilse, Microsoft Windows eşdeğerini edinin.  
  
- DLL, mevcut olmayan başka bir DLL 'ye başvuruyorsa, başvurulan DLL 'yi edinin ve kullanılabilir hale getirin.  
  
- DLL veya başvurulan DLL, yol tarafından belirtilen bir dizinde değilse, DLL 'yi başvurulan bir dizine taşıyın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Declare Deyimi](../statements/declare-statement.md)
