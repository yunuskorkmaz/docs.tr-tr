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
ms.openlocfilehash: eb5f021371291483b8eb2a13727a9fda94540638
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "58838857"
---
# <a name="narrowing-visual-basic"></a>Daraltma (Visual Basic)
Bildiren bir dönüştürme operatörünün (`CType`) bir sınıf veya yapı, bazı özgün sınıf veya yapıda olası değerlerini tutabilecek özellikte olmayabilecek bir türe dönüştürür.  
  
## <a name="converting-with-the-narrowing-keyword"></a>Daraltma anahtar sözcüğü ile dönüştürme  
 Dönüştürme yordamı belirtmelisiniz `Public Shared` ek olarak `Narrowing`.  
  
 Daraltma dönüştürmeleri her zaman çalışma zamanında başarılı ve başarısız veya veri kaybına neden. Örnekler `Long` için `Integer`, `String` için `Date`ve türetilmiş bir tür için bir taban türü. Temel tür türetilmiş bir türde tüm üyelerini içermeyebilir ve bu nedenle türetilmiş bir tür örneği olmadığından bu son dönüştürme belirlemektir.  
  
 Varsa `Option Strict` olduğu `On`, kod tüketen kullanmalıdır `CType` tüm daraltma dönüştürmeleri için.  
  
 `Narrowing` Anahtar sözcüğü bu bağlamda kullanılabilir:  
  
 [Operator Deyimi](../../../visual-basic/language-reference/statements/operator-statement.md)  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Operator Deyimi](../../../visual-basic/language-reference/statements/operator-statement.md)
- [Widening](../../../visual-basic/language-reference/modifiers/widening.md)
- [Genişletme ve Daraltma Dönüştürmeleri](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
- [Nasıl yapılır: Bir işleci tanımlama](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-an-operator.md)
- [CType İşlevi](../../../visual-basic/language-reference/functions/ctype-function.md)
- [Option Strict Deyimi](../../../visual-basic/language-reference/statements/option-strict-statement.md)
