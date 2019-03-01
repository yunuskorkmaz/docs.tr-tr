---
title: 'Nasıl yapılır: İşleçler (Visual Basic) tanımlayan bir sınıf kullanma'
ms.date: 07/20/2015
helpviewer_keywords:
- operator procedures [Visual Basic], calling
- procedures [Visual Basic], operator
- procedures [Visual Basic], calling
- examples [Visual Basic], CType
- syntax [Visual Basic], Operator procedures
- operators [Visual Basic], overloading
- return values [Visual Basic], Operator procedures
- operator overloading
ms.assetid: 7ccce94a-6ca0-47d1-9f3f-13385d34f5d5
ms.openlocfilehash: 358e81904f48ad844351a20a448b615a0fef8f89
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/28/2019
ms.locfileid: "56972527"
---
# <a name="how-to-use-a-class-that-defines-operators-visual-basic"></a>Nasıl yapılır: İşleçler (Visual Basic) tanımlayan bir sınıf kullanma
Bir sınıf veya kendi işleçleri tanımlayan bir yapı kullanıyorsanız, bu işleçler Visual Basic'ten erişebilirsiniz.  
  
 Bir sınıf ya da yapı üzerinde operatör tanımlama olarak da adlandırılır *aşırı yükleme* işleci.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek SQL yapısı erişen <xref:System.Data.SqlTypes.SqlString>, dönüştürme işleçlerini tanımlar ([CType işlevi](../../../../visual-basic/language-reference/functions/ctype-function.md)) SQL dizesi ve bir Visual Basic dize arasında iki yönlü. Kullanım `CType(` *SQL dize ifadesi*, `String)` SQL dizesi bir Visual Basic dizeye dönüştürmek için ve `CType(` *Visual Basic dize ifadesinin*, <xref:System.Data.SqlTypes.SqlString> `)` diğer yönde dönüştürülecek.  
  
 [!code-vb[VbVbcnProcedures#30](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#30)]  
  
 [!code-vb[VbVbcnProcedures#31](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#31)]  
  
 <xref:System.Data.SqlTypes.SqlString> Yapısını tanımlayan bir dönüştürme operatörünün ([CType işlevi](../../../../visual-basic/language-reference/functions/ctype-function.md)) öğesinden `String` için <xref:System.Data.SqlTypes.SqlString> ve başka bir uygulamadan <xref:System.Data.SqlTypes.SqlString> için `String`. Atayan deyimi `title` için `jobTitle` ilk işlecini kullanır ve <xref:Microsoft.VisualBasic.Interaction.MsgBox%2A> ikinci işlev çağrısı kullanır.  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Kullanmak istediğiniz işleci tanımlar, sınıfın veya yapının kullanmakta olduğunuz emin olun. Sınıfın veya yapının her işleci aşırı yükleme için kullanılabilir tanımladığı varsaymayın. Kullanılabilir işleçlerin bir listesi için bkz. [Operator deyimi](../../../../visual-basic/language-reference/statements/operator-statement.md).  
  
 Uygun dahil `Imports` kaynak dosyasının başında SQL dizesi deyimi (Bu durumda <xref:System.Data.SqlTypes>).  
  
 Proje başvuruları System.Data ve System.XML olması gerekir.  
  
## <a name="see-also"></a>Ayrıca bkz.
- [İşleç Yordamları](./operator-procedures.md)
- [Nasıl yapılır: Bir işleci tanımlama](./how-to-define-an-operator.md)
- [Nasıl yapılır: Bir dönüşüm işleci tanımlama](./how-to-define-a-conversion-operator.md)
- [Nasıl yapılır: Bir işleç yordamı çağırma](./how-to-call-an-operator-procedure.md)
- [Widening](../../../../visual-basic/language-reference/modifiers/widening.md)
- [Narrowing](../../../../visual-basic/language-reference/modifiers/narrowing.md)
- [Structure Deyimi](../../../../visual-basic/language-reference/statements/structure-statement.md)
- [Nasıl yapılır: Yapıyı Bildirme](../../../../visual-basic/programming-guide/language-features/data-types/how-to-declare-a-structure.md)
- [Örtük ve Açık Dönüştürmeler](../../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
- [Genişletme ve Daraltma Dönüştürmeleri](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
