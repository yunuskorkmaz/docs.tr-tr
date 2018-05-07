---
title: DLL yüklenirken hata (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vbrID48
ms.assetid: 4226cd1f-028c-477d-88a5-cb57f7e0cdc8
ms.openlocfilehash: ac21c4d52b248025ee26bac3e511bb5b0a0b668e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="error-in-loading-dll-visual-basic"></a>DLL yüklenirken hata (Visual Basic)
Dinamik bağlantı kitaplığı (DLL) içinde belirtilen bir kitaplıktır `Lib` yan tümcesinde bir `Declare` deyimi. Bu hatanın olası nedenleri şunlardır:  
  
-   Dosya DLL yürütülebilir değil.  
  
-   Dosya bir Microsoft Windows dll dosyası değil.  
  
-   DLL mevcut değil başka bir DLL başvurur.  
  
-   DLL veya başvurulan DLL yolunda belirtilen bir dizin değil.  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
-   Dosya bir kaynak metin dosyası ve bu nedenle değil DLL yürütülebilir ise derlenmiş ve gerekir DLL yürütülebilir dosya biçimine bağlı.  
  
-   Dosya bir Microsoft Windows DLL değilse, Microsoft Windows eşdeğer edinin.  
  
-   DLL mevcut değil başka bir DLL başvuruyorsa, başvurulan DLL edinmek ve kullanılabilir yapın.  
  
-   DLL veya başvurulan DLL yolu tarafından belirtilen bir dizinde değilse, DLL başvurulan bir dizinine taşıyın.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Declare Deyimi](../../../visual-basic/language-reference/statements/declare-statement.md)
