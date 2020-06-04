---
title: DLL dosyasını yüklemede hata
ms.date: 07/20/2015
f1_keywords:
- vbrID48
ms.assetid: 4226cd1f-028c-477d-88a5-cb57f7e0cdc8
ms.openlocfilehash: fd2e425f2dd3f4127cd777d4a1f7ab9809de9d45
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84409639"
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
