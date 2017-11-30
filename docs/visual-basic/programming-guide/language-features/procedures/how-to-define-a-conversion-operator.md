---
title: "Nasıl yapılır: Bir Dönüşüm İşleci Tanımlama (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- procedures [Visual Basic], defining
- operators [Visual Basic], defining
- procedures [Visual Basic], operator
- operators [Visual Basic], overloading
- return values [Visual Basic], Operator procedures
- operator overloading
ms.assetid: 54203dfa-c24b-463f-9942-d5153e89e762
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: b0f9e63ba039a48226186fa4ce118d3e47b5673e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-define-a-conversion-operator-visual-basic"></a>Nasıl yapılır: Bir Dönüşüm İşleci Tanımlama (Visual Basic)
Bir sınıf veya yapı tanımladıysanız, sınıf veya yapı türüne ve başka bir veri türü arasında tür dönüştürme işleci tanımlayabilirsiniz (gibi `Integer`, `Double`, veya `String`).  
  
 Tür dönüştürme olarak tanımlayan bir [CType işlevi](../../../../visual-basic/language-reference/functions/ctype-function.md) yordam sınıf veya yapı içinde. Tüm dönüştürme yordamları olmalıdır `Public Shared`, ve her biri ya da belirtmeniz gerekir [Widening](../../../../visual-basic/language-reference/modifiers/widening.md) veya [Narrowing](../../../../visual-basic/language-reference/modifiers/narrowing.md).  
  
 Bir sınıf veya yapı bir işleci tanımlama olarak da adlandırılır *aşırı* işleci.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek olarak adlandırılan bir yapıyı arasında dönüştürme işleçleri tanımlayan `digit` ve `Byte`.  
  
 [!code-vb[VbVbcnProcedures#27](./codesnippet/VisualBasic/how-to-define-a-conversion-operator_1.vb)]  
  
 Yapıyı test `digit` aşağıdaki kod ile.  
  
 [!code-vb[VbVbcnProcedures#28](./codesnippet/VisualBasic/how-to-define-a-conversion-operator_2.vb)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [İşleç yordamları](./operator-procedures.md)  
 [Nasıl yapılır: bir işleci tanımlama](./how-to-define-an-operator.md)  
 [Nasıl yapılır: bir işleç yordamı çağırma](./how-to-call-an-operator-procedure.md)  
 [Nasıl yapılır: işleçleri tanımlayan bir sınıf kullanma](./how-to-use-a-class-that-defines-operators.md)  
 [Operator deyimi](../../../../visual-basic/language-reference/statements/operator-statement.md)  
 [Structure deyimi](../../../../visual-basic/language-reference/statements/structure-statement.md)  
 [Nasıl yapılır: bir yapıyı bildirme](../../../../visual-basic/programming-guide/language-features/data-types/how-to-declare-a-structure.md)  
 [Örtük ve açık dönüştürmeler](../../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)  
 [Genişletme ve daraltma dönüşümleri](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
