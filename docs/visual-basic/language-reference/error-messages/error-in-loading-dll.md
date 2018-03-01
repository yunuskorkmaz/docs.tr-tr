---
title: "DLL yüklenirken hata (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbrID48
ms.assetid: 4226cd1f-028c-477d-88a5-cb57f7e0cdc8
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: cc557dcc6709178b6519adb56f31debcbd1d1c39
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
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
 [Declare deyimi](../../../visual-basic/language-reference/statements/declare-statement.md)
