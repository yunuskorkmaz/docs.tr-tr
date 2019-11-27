---
title: DLL dosyasını yüklemede hata
ms.date: 07/20/2015
f1_keywords:
- vbrID48
ms.assetid: 4226cd1f-028c-477d-88a5-cb57f7e0cdc8
ms.openlocfilehash: 36452cc6ff03042939cd4066aef76129b5bb8f0a
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74329554"
---
# <a name="error-in-loading-dll-visual-basic"></a>DLL yüklenirken hata (Visual Basic)
Dinamik bağlantı kitaplığı (DLL), bir `Declare` deyimin `Lib` yan tümcesinde belirtilen bir kitaplıktır. Bu hatanın olası nedenleri şunlardır:  
  
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

- [Declare Deyimi](../../../visual-basic/language-reference/statements/declare-statement.md)
