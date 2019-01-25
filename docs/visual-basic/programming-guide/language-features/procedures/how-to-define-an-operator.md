---
title: 'Nasıl yapılır: (Visual Basic) bir işleci tanımlama'
ms.date: 07/20/2015
helpviewer_keywords:
- procedures [Visual Basic], defining
- Visual Basic code, procedures
- operators [Visual Basic], defining
- procedures [Visual Basic], operator
- Visual Basic code, operators
- syntax [Visual Basic], Operator procedures
- operators [Visual Basic], overloading
- operator procedures [Visual Basic], about operator procedures
- return values [Visual Basic], Operator procedures
- operator overloading
ms.assetid: d4b0e253-092a-4e6e-9fe2-01f562140a29
ms.openlocfilehash: fb150298562c1ec91f73f3c8075f4f8a4fc20b27
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54679532"
---
# <a name="how-to-define-an-operator-visual-basic"></a>Nasıl yapılır: (Visual Basic) bir işleci tanımlama
Bir sınıf veya yapı tanımladıysanız, standart bir işleç davranışını tanımlayın (gibi `*`, `<>`, veya `And`) bir veya iki işlenenden olduğunda sınıf veya yapı türü.  
  
 Standart işleci, sınıf veya yapı içinde bir işleç yordamı olarak tanımlayın. İşleç yordamları tüm olmalıdır `Public` `Shared`.  
  
 Bir sınıf ya da yapı üzerinde operatör tanımlama olarak da adlandırılır *aşırı yükleme* işleci.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek tanımlar `+` işleci bir yapı için adlı `height`. Yapı ayak ve inç cinsinden yüksekliklerini kullanır. Bir *inç* 2,54 santimetre ve bir *altbilgi* 12 inçtir. Normalleştirilmiş değerleri (inç < 12.0) sağlamak için oluşturucu gerçekleştirir *modül* aritmetik 12. `+` İşleci normalleştirilmiş değerler oluşturmak için oluşturucu kullanır.  
  
 [!code-vb[VbVbcnProcedures#25](./codesnippet/VisualBasic/how-to-define-an-operator_1.vb)]  
  
 Yapıyı test edebilirsiniz `height` aşağıdaki kod ile.  
  
 [!code-vb[VbVbcnProcedures#26](./codesnippet/VisualBasic/how-to-define-an-operator_2.vb)]  
  
 Daha fazla bilgi ve örnekler için bkz. [işleci aşırı yüklemesi Visual Basic 2005](https://msdn.microsoft.com/library/ms379613(v=vs.80).aspx).  
  
## <a name="see-also"></a>Ayrıca bkz.
- [İşleç Yordamları](./operator-procedures.md)
- [Nasıl yapılır: Bir dönüşüm işleci tanımlama](./how-to-define-a-conversion-operator.md)
- [Nasıl yapılır: Bir işleç yordamı çağırma](./how-to-call-an-operator-procedure.md)
- [Nasıl yapılır: İşleçleri tanımlayan bir sınıf kullanma](./how-to-use-a-class-that-defines-operators.md)
- [Operator Deyimi](../../../../visual-basic/language-reference/statements/operator-statement.md)
- [Structure Deyimi](../../../../visual-basic/language-reference/statements/structure-statement.md)
- [Nasıl yapılır: Yapıyı Bildirme](../../../../visual-basic/programming-guide/language-features/data-types/how-to-declare-a-structure.md)
- [Mod İşleci](../../../../visual-basic/language-reference/operators/mod-operator.md)
