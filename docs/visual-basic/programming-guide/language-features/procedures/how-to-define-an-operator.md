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
ms.openlocfilehash: 3a09657ee7a79b7f590adba0e4fb0c04a8e89043
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58843649"
---
# <a name="how-to-define-an-operator-visual-basic"></a>Nasıl yapılır: (Visual Basic) bir işleci tanımlama
Bir sınıf veya yapı tanımladıysanız, standart bir işleç davranışını tanımlayın (gibi `*`, `<>`, veya `And`) bir veya iki işlenenden olduğunda sınıf veya yapı türü.  
  
 Standart işleci, sınıf veya yapı içinde bir işleç yordamı olarak tanımlayın. İşleç yordamları tüm olmalıdır `Public` `Shared`.  
  
 Bir sınıf ya da yapı üzerinde operatör tanımlama olarak da adlandırılır *aşırı yükleme* işleci.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek tanımlar `+` işleci bir yapı için adlı `height`. Yapı ayak ve inç cinsinden yüksekliklerini kullanır. Bir *inç* 2,54 santimetre ve bir *altbilgi* 12 inçtir. Normalleştirilmiş değerleri (inç < 12.0) sağlamak için oluşturucu gerçekleştirir *modül* aritmetik 12. `+` İşleci normalleştirilmiş değerler oluşturmak için oluşturucu kullanır.  
  
 [!code-vb[VbVbcnProcedures#25](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#25)]  
  
 Yapıyı test edebilirsiniz `height` aşağıdaki kod ile.  
  
 [!code-vb[VbVbcnProcedures#26](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#26)]  
  
  
## <a name="see-also"></a>Ayrıca bkz.

- [İşleç Yordamları](./operator-procedures.md)
- [Nasıl yapılır: Bir dönüşüm işleci tanımlama](./how-to-define-a-conversion-operator.md)
- [Nasıl yapılır: Bir işleç yordamı çağırma](./how-to-call-an-operator-procedure.md)
- [Nasıl yapılır: İşleçleri tanımlayan bir sınıf kullanma](./how-to-use-a-class-that-defines-operators.md)
- [Operator Deyimi](../../../../visual-basic/language-reference/statements/operator-statement.md)
- [Structure Deyimi](../../../../visual-basic/language-reference/statements/structure-statement.md)
- [Nasıl yapılır: Yapıyı Bildirme](../../../../visual-basic/programming-guide/language-features/data-types/how-to-declare-a-structure.md)
- [Mod İşleci](../../../../visual-basic/language-reference/operators/mod-operator.md)
