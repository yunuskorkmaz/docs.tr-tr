---
title: 'Nasıl yapılır: İşleçleri Tanımlayan Bir Sınıf Kullanma'
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
ms.openlocfilehash: 455c839702b90738ec5aea37c1b09d72eba42ff4
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75347886"
---
# <a name="how-to-use-a-class-that-defines-operators-visual-basic"></a>Nasıl yapılır: İşleçleri Tanımlayan Bir Sınıf Kullanma (Visual Basic)
Kendi işleçlerini tanımlayan bir sınıf veya yapı kullanıyorsanız, bu işleçlere Visual Basic erişebilirsiniz.  
  
 Bir sınıf veya yapı üzerinde işleç tanımlamak, işleci *aşırı yükleme* olarak da adlandırılır.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, bir SQL dizesi ve bir Visual Basic dizesi arasında her iki yönde de dönüştürme işleçlerini ([CType işlevi](../../../../visual-basic/language-reference/functions/ctype-function.md)) tanımlayan SQL yapısına erişir <xref:System.Data.SqlTypes.SqlString>. `CType(`*SQL dize ifadesi*kullanın, bir sql dizesini Visual Basic bir dizeye dönüştürmek için `String)` ve `CType(`*Visual Basic dize ifadesi*, <xref:System.Data.SqlTypes.SqlString>`)` diğer yönde dönüştürmek için.  
  
 [!code-vb[VbVbcnProcedures#30](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#30)]  
  
 [!code-vb[VbVbcnProcedures#31](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#31)]  
  
 <xref:System.Data.SqlTypes.SqlString> yapısı, `String` bir dönüştürme işlecini ([CType işlevi](../../../../visual-basic/language-reference/functions/ctype-function.md)) <xref:System.Data.SqlTypes.SqlString> ve <xref:System.Data.SqlTypes.SqlString> arasında bir `String`tanımlar. `jobTitle` `title` atayan ifade, ilk işleci kullanır ve <xref:Microsoft.VisualBasic.Interaction.MsgBox%2A> işlev çağrısı ikincisini kullanır.  
  
## <a name="compile-the-code"></a>Kod derleme  
 Kullandığınız sınıf veya yapının kullanmak istediğiniz işleci tanımladığından emin olun. Sınıf veya yapının, aşırı yükleme için kullanılabilen her işleci tanımladığını varsayın. Kullanılabilir operatörlerin bir listesi için bkz. [operator deyimleri](../../../../visual-basic/language-reference/statements/operator-statement.md).  
  
 Kaynak dosyanızın başlangıcında SQL dizesi için uygun `Imports` ifadesini ekleyin (Bu durumda <xref:System.Data.SqlTypes>).  
  
 Projenizin System. Data ve System. XML öğesine başvuruları olmalıdır.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [İşleç Yordamları](./operator-procedures.md)
- [Nasıl yapılır: İşleç Tanımlama](./how-to-define-an-operator.md)
- [Nasıl yapılır: Dönüştürme İşleci Tanımlama](./how-to-define-a-conversion-operator.md)
- [Nasıl yapılır: Bir İşleç Yordamı Çağırma](./how-to-call-an-operator-procedure.md)
- [Widening](../../../../visual-basic/language-reference/modifiers/widening.md)
- [Narrowing](../../../../visual-basic/language-reference/modifiers/narrowing.md)
- [Structure Deyimi](../../../../visual-basic/language-reference/statements/structure-statement.md)
- [Nasıl yapılır: Bir Yapıyı Bildirme](../../../../visual-basic/programming-guide/language-features/data-types/how-to-declare-a-structure.md)
- [Örtük ve Açık Dönüştürmeler](../../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
- [Genişletme ve Daraltma Dönüştürmeleri](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
