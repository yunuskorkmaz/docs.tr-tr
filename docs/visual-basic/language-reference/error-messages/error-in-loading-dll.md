---
title: DLL yüklenirken hata (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vbrID48
ms.assetid: 4226cd1f-028c-477d-88a5-cb57f7e0cdc8
ms.openlocfilehash: c3f88a5a3c37c89d23055aa413957b2add38ed67
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "58816908"
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
