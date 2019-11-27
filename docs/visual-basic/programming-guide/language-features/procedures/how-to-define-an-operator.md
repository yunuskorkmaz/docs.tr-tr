---
title: 'Nasıl yapılır: Bir İşleci Tanımlama'
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
ms.openlocfilehash: b99af8ff4d5428f1749bfc1a4c51a136f12405ee
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74344871"
---
# <a name="how-to-define-an-operator-visual-basic"></a>Nasıl yapılır: Bir İşleci Tanımlama (Visual Basic)
Bir sınıf veya yapı tanımladıysanız, işlenenleri bir veya her ikisi de sınıfınızın veya yapınızın türü olduğunda standart bir işlecin (`*`, `<>`veya `And`) davranışını tanımlayabilirsiniz.  
  
 Standart işleci sınıf veya yapı içinde operatör yordamı olarak tanımlayın. Tüm operatör yordamları `Public` `Shared`olmalıdır.  
  
 Bir sınıf veya yapı üzerinde işleç tanımlamak, işleci *aşırı yükleme* olarak da adlandırılır.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, `height`adlı bir yapı için `+` işlecini tanımlar. Yapı, fit ve inç cinsinden ölçülen yükseklikleri kullanır. Bir *inç* 2,54 santimetre, bir *Foot* ise 12 inç 'tir. Normalleştirilmiş değerler (inç < 12,0) sağlamak için, Oluşturucu *Modül* 12 aritmetik işlemini gerçekleştirir. `+` işleci, normalleştirilmiş değerler oluşturmak için oluşturucuyu kullanır.  
  
 [!code-vb[VbVbcnProcedures#25](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#25)]  
  
 Aşağıdaki kodla yapıyı `height` test edebilirsiniz.  
  
 [!code-vb[VbVbcnProcedures#26](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#26)]  

## <a name="see-also"></a>Ayrıca bkz.

- [İşleç Yordamları](./operator-procedures.md)
- [Nasıl yapılır: Dönüştürme İşleci Tanımlama](./how-to-define-a-conversion-operator.md)
- [Nasıl yapılır: Bir İşleç Yordamı Çağırma](./how-to-call-an-operator-procedure.md)
- [Nasıl yapılır: İşleçleri Tanımlayan Bir Sınıf Kullanma](./how-to-use-a-class-that-defines-operators.md)
- [Operator Deyimi](../../../../visual-basic/language-reference/statements/operator-statement.md)
- [Structure Deyimi](../../../../visual-basic/language-reference/statements/structure-statement.md)
- [Nasıl yapılır: Bir Yapıyı Bildirme](../../../../visual-basic/programming-guide/language-features/data-types/how-to-declare-a-structure.md)
- [Mod İşleci](../../../../visual-basic/language-reference/operators/mod-operator.md)
