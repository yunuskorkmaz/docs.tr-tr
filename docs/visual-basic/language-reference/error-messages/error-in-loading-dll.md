---
title: DLL yüklenirken hata (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vbrID48
ms.assetid: 4226cd1f-028c-477d-88a5-cb57f7e0cdc8
ms.openlocfilehash: 76a0a443fd9f8a6dec5ead24bc75c97d89d6c36b
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54518468"
---
# <a name="error-in-loading-dll-visual-basic"></a>DLL yüklenirken hata (Visual Basic)
Bir dinamik bağlantı kitaplığı (DLL) belirtilen bir kitaplıktır `Lib` yan tümcesi bir `Declare` deyimi. Bu hata için olası nedenler şunlardır:  
  
-   DLL yürütülebilir dosya değil.  
  
-   Dosya, Microsoft Windows DLL değil.  
  
-   DLL mevcut değilse başka bir DLL başvurusu.  
  
-   DLL veya başvurulan DLL belirtilen yolda bir dizin değil.  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
-   Dosya bir kaynak metin dosyası ve bu nedenle DLL çalıştırılabilir değil ise, derlenmiş ve gerekir DLL yürütülebilir dosya biçimine bağlı.  
  
-   Microsoft Windows DLL dosyası değil, eşdeğer Microsoft Windows edinin.  
  
-   DLL mevcut değilse başka bir DLL başvuruyorsa, başvurulan DLL edinin ve kullanılabilir hale getirmek.  
  
-   DLL veya başvurulan DLL yolu tarafından belirtilen bir dizinde değilse DLL başvurulan bir dizinine taşıyın.  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Declare Deyimi](../../../visual-basic/language-reference/statements/declare-statement.md)
