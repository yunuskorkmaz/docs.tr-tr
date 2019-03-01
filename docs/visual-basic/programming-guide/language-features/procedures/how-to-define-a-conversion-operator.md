---
title: 'Nasıl yapılır: Bir dönüşüm işleci (Visual Basic) tanımlama'
ms.date: 07/20/2015
helpviewer_keywords:
- procedures [Visual Basic], defining
- operators [Visual Basic], defining
- procedures [Visual Basic], operator
- operators [Visual Basic], overloading
- return values [Visual Basic], Operator procedures
- operator overloading
ms.assetid: 54203dfa-c24b-463f-9942-d5153e89e762
ms.openlocfilehash: fe5c314fe4e39c8a06803037da29b51148188e14
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/28/2019
ms.locfileid: "56974646"
---
# <a name="how-to-define-a-conversion-operator-visual-basic"></a>Nasıl yapılır: Bir dönüşüm işleci (Visual Basic) tanımlama
Bir sınıf veya yapı tanımladıysanız, bir sınıf veya yapı türü ve başka bir veri türü arasında tür dönüştürme işleci tanımlama (gibi `Integer`, `Double`, veya `String`).  
  
 Tür dönüştürme olarak tanımlayan bir [CType işlevi](../../../../visual-basic/language-reference/functions/ctype-function.md) yordam sınıf veya yapı içinde. Tüm dönüştürme yordamları olmalıdır `Public Shared`, ve her biri belirtmeli [Widening](../../../../visual-basic/language-reference/modifiers/widening.md) veya [Narrowing](../../../../visual-basic/language-reference/modifiers/narrowing.md).  
  
 Bir sınıf ya da yapı üzerinde operatör tanımlama olarak da adlandırılır *aşırı yükleme* işleci.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek adlı bir yapıyı arasında dönüştürme işleçleri tanımlar `digit` ve `Byte`.  
  
 [!code-vb[VbVbcnProcedures#27](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#27)]  
  
 Yapıyı test edebilirsiniz `digit` aşağıdaki kod ile.  
  
 [!code-vb[VbVbcnProcedures#28](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#28)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- [İşleç Yordamları](./operator-procedures.md)
- [Nasıl yapılır: Bir işleci tanımlama](./how-to-define-an-operator.md)
- [Nasıl yapılır: Bir işleç yordamı çağırma](./how-to-call-an-operator-procedure.md)
- [Nasıl yapılır: İşleçleri tanımlayan bir sınıf kullanma](./how-to-use-a-class-that-defines-operators.md)
- [Operator Deyimi](../../../../visual-basic/language-reference/statements/operator-statement.md)
- [Structure Deyimi](../../../../visual-basic/language-reference/statements/structure-statement.md)
- [Nasıl yapılır: Yapıyı Bildirme](../../../../visual-basic/programming-guide/language-features/data-types/how-to-declare-a-structure.md)
- [Örtük ve Açık Dönüştürmeler](../../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
- [Genişletme ve Daraltma Dönüştürmeleri](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
