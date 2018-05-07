---
title: Daraltma (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.narrowing
helpviewer_keywords:
- conversions [Visual Basic], type
- type conversion [Visual Basic]
- conversions [Visual Basic], data type
- Narrowing keyword [Visual Basic]
- data type conversion [Visual Basic]
ms.assetid: a207ee91-aca4-4771-b4e2-713f029bf2bb
ms.openlocfilehash: 54a18d0cc10e42829b48b0ef75bb77ab0d47b45f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="narrowing-visual-basic"></a>Daraltma (Visual Basic)
Belirten bir dönüşüm işleci (`CType`) bir sınıf veya yapı bazı özgün sınıf veya yapı olası değerlerini tutabilecek özellikte olmayabilecek türüne dönüştürür.  
  
## <a name="converting-with-the-narrowing-keyword"></a>Daraltma anahtar sözcüğü ile dönüştürme  
 Dönüştürme yordamı belirtmelisiniz `Public Shared` ek olarak `Narrowing`.  
  
 Daraltma dönüşümleri her zaman çalışma zamanında başarılı ve başarısız veya veri kaybına neden. Örnekler `Long` için `Integer`, `String` için `Date`ve türetilmiş bir tür için bir taban türü. Temel türü türetilen türdeki tüm üyelerin içerebilir ve dolayısıyla türetilen tür örneği olmadığından bu son dönüştürme daraltma.  
  
 Varsa `Option Strict` olan `On`, kod tüketen kullanmalıdır `CType` tüm daraltma dönüşümleri için.  
  
 `Narrowing` Anahtar sözcüğü bu bağlamda kullanılabilir:  
  
 [Operator Deyimi](../../../visual-basic/language-reference/statements/operator-statement.md)  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Operator Deyimi](../../../visual-basic/language-reference/statements/operator-statement.md)  
 [Widening](../../../visual-basic/language-reference/modifiers/widening.md)  
 [Genişletme ve Daraltma Dönüştürmeleri](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)  
 [Nasıl yapılır: İşleç Tanımlama](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-an-operator.md)  
 [CType İşlevi](../../../visual-basic/language-reference/functions/ctype-function.md)  
 [Option Strict Deyimi](../../../visual-basic/language-reference/statements/option-strict-statement.md)
