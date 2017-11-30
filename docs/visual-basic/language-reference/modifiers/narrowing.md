---
title: Daraltma (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.narrowing
helpviewer_keywords:
- conversions [Visual Basic], type
- type conversion [Visual Basic]
- conversions [Visual Basic], data type
- Narrowing keyword [Visual Basic]
- data type conversion [Visual Basic]
ms.assetid: a207ee91-aca4-4771-b4e2-713f029bf2bb
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 50116c6212e919d4b9b35fc933d80dee14bd4ecf
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="narrowing-visual-basic"></a>Daraltma (Visual Basic)
Belirten bir dönüşüm işleci (`CType`) bir sınıf veya yapı bazı özgün sınıf veya yapı olası değerlerini tutabilecek özellikte olmayabilecek türüne dönüştürür.  
  
## <a name="converting-with-the-narrowing-keyword"></a>Daraltma anahtar sözcüğü ile dönüştürme  
 Dönüştürme yordamı belirtmelisiniz `Public Shared` ek olarak `Narrowing`.  
  
 Daraltma dönüşümleri her zaman çalışma zamanında başarılı ve başarısız veya veri kaybına neden. Örnekler `Long` için `Integer`, `String` için `Date`ve türetilmiş bir tür için bir taban türü. Temel türü türetilen türdeki tüm üyelerin içerebilir ve dolayısıyla türetilen tür örneği olmadığından bu son dönüştürme daraltma.  
  
 Varsa `Option Strict` olan `On`, kod tüketen kullanmalıdır `CType` tüm daraltma dönüşümleri için.  
  
 `Narrowing` Anahtar sözcüğü bu bağlamda kullanılabilir:  
  
 [Operator deyimi](../../../visual-basic/language-reference/statements/operator-statement.md)  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Operator deyimi](../../../visual-basic/language-reference/statements/operator-statement.md)  
 [Genişletme](../../../visual-basic/language-reference/modifiers/widening.md)  
 [Genişletme ve daraltma dönüşümleri](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)  
 [Nasıl yapılır: bir işleci tanımlama](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-an-operator.md)  
 [CType işlevi](../../../visual-basic/language-reference/functions/ctype-function.md)  
 [Option Strict deyimi](../../../visual-basic/language-reference/statements/option-strict-statement.md)
