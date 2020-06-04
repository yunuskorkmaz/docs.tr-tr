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
ms.openlocfilehash: fe15e976e6a5469f2a9d1b3521a70a3e1860fdd3
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84414356"
---
# <a name="how-to-use-a-class-that-defines-operators-visual-basic"></a>Nasıl yapılır: İşleçleri Tanımlayan Bir Sınıf Kullanma (Visual Basic)
Kendi işleçlerini tanımlayan bir sınıf veya yapı kullanıyorsanız, bu işleçlere Visual Basic erişebilirsiniz.  
  
 Bir sınıf veya yapı üzerinde işleç tanımlamak, işleci *aşırı yükleme* olarak da adlandırılır.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, <xref:System.Data.SqlTypes.SqlString> BIR SQL dizesi ve bir Visual Basic dizesi arasında her iki yönde de dönüştürme işleçlerini ([CType işlevi](../../../language-reference/functions/ctype-function.md)) tanımlayan SQL yapısına erişir. SQL dize `CType(` *ifadesini*, `String)` bir SQL dizesini bir Visual Basic dizesine dönüştürmek için ve `CType(` *Visual Basic dize ifadesini*kullanarak <xref:System.Data.SqlTypes.SqlString> `)` diğer yönde dönüştürün.  
  
 [!code-vb[VbVbcnProcedures#30](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#30)]  
  
 [!code-vb[VbVbcnProcedures#31](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#31)]  
  
 <xref:System.Data.SqlTypes.SqlString>Yapı, öğesinden ve öğesinden öğesinden öğesine bir dönüştürme işleci ([CType işlevi](../../../language-reference/functions/ctype-function.md)) tanımlar `String` <xref:System.Data.SqlTypes.SqlString> <xref:System.Data.SqlTypes.SqlString> `String` . Öğesine atayan ifade `title` `jobTitle` , ilk işleci kullanır ve <xref:Microsoft.VisualBasic.Interaction.MsgBox%2A> işlev çağrısı ikincisini kullanır.  
  
## <a name="compile-the-code"></a>Kodu derle  
 Kullandığınız sınıf veya yapının kullanmak istediğiniz işleci tanımladığından emin olun. Sınıf veya yapının, aşırı yükleme için kullanılabilen her işleci tanımladığını varsayın. Kullanılabilir operatörlerin bir listesi için bkz. [operator deyimleri](../../../language-reference/statements/operator-statement.md).  
  
 `Imports`Kaynak dosyanızın başına (Bu durumda) SQL dizesi için uygun bir ifade ekleyin <xref:System.Data.SqlTypes> .  
  
 Projenizin System. Data ve System. XML öğesine başvuruları olmalıdır.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [İşleç Yordamları](./operator-procedures.md)
- [Nasıl yapılır: İşleç Tanımlama](./how-to-define-an-operator.md)
- [Nasıl yapılır: Dönüştürme İşleci Tanımlama](./how-to-define-a-conversion-operator.md)
- [Nasıl yapılır: Bir İşleç Yordamı Çağırma](./how-to-call-an-operator-procedure.md)
- [Genişletme](../../../language-reference/modifiers/widening.md)
- [Narrowing](../../../language-reference/modifiers/narrowing.md)
- [Structure Yapısı](../../../language-reference/statements/structure-statement.md)
- [Nasıl yapılır: Yapıyı Bildirme](../data-types/how-to-declare-a-structure.md)
- [Örtük ve Açık Dönüştürmeler](../data-types/implicit-and-explicit-conversions.md)
- [Genişletme ve Daraltma Dönüşümleri](../data-types/widening-and-narrowing-conversions.md)
