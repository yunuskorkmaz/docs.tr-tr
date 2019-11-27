---
title: 'Nasıl yapılır: Bir İşleç Yordamı Çağırma'
ms.date: 07/20/2015
helpviewer_keywords:
- operator procedures [Visual Basic], calling
- procedures [Visual Basic], operator
- procedure calls [Visual Basic], operator overloading
- syntax [Visual Basic], Operator procedures
- operators [Visual Basic], overloading
- return values [Visual Basic], Operator procedures
- overloaded operators [Visual Basic], calling
- operator overloading
ms.assetid: 0dce42cc-f0b0-4c14-9f62-018b21f33497
ms.openlocfilehash: a685be7cc3b346b271413e2c29faae5a839313f4
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74340238"
---
# <a name="how-to-call-an-operator-procedure-visual-basic"></a>Nasıl yapılır: Bir İşleç Yordamı Çağırma (Visual Basic)
Bir ifadede işleç sembolünü kullanarak bir işleç yordamı çağırın. Bir dönüştürme işleci söz konusu olduğunda, bir değeri bir veri türünden diğerine dönüştürmek için [CType işlevini](../../../../visual-basic/language-reference/functions/ctype-function.md) çağırın.  
  
 Operatör yordamlarını açıkça çağırmayın. Yalnızca işlecini veya `CType` işlevini, bir atama deyiminde veya bir ifadede, normalde bir işleci kullandığınız şekilde kullanırsınız. Visual Basic işleç yordamına çağrı yapar.  
  
 Bir sınıf veya yapı üzerinde işleç tanımlamak, işleci *aşırı yükleme* olarak da adlandırılır.  
  
### <a name="to-call-an-operator-procedure"></a>Bir işleç yordamını çağırmak için  
  
1. Bir ifadede işleç sembolünü normal şekilde kullanın.  
  
2. İşlenenlerin veri türlerinin operatör için uygun olduğundan ve doğru sırada olduğundan emin olun.  
  
3. İşleci, ifadenin değerine beklenen şekilde katkıda bulunur.  
  
### <a name="to-call-a-conversion-operator-procedure"></a>Bir dönüştürme işleci yordamını çağırmak için  
  
1. `CType` bir ifadenin içinde kullanın.  
  
2. İşlenenlerin veri türlerinin dönüştürme için uygun olduğundan ve doğru sırada olduğundan emin olun.  
  
3. `CType` dönüştürme işleci yordamını çağırır ve dönüştürülen değeri döndürür.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek iki <xref:System.TimeSpan> yapısı oluşturur, bunları birlikte ekler ve sonucu üçüncü bir <xref:System.TimeSpan> yapısında depolar. <xref:System.TimeSpan> yapısı, birkaç standart işlecin aşırı yüklenmesine yönelik operatör yordamlarını tanımlar.  
  
 [!code-vb[VbVbcnProcedures#29](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#29)]  
  
 <xref:System.TimeSpan> standart `+` işlecini aşırı yüklediğinden, önceki örnek `combinedSpan`değerini hesaplarken bir işleç yordamını çağırır.  
  
 Bir konuşma işleci yordamı çağırma örneği için bkz. [nasıl yapılır: Işleçleri tanımlayan bir sınıf kullanma](./how-to-use-a-class-that-defines-operators.md).  
  
## <a name="compiling-the-code"></a>Kod Derleme  
 Kullandığınız sınıf veya yapının kullanmak istediğiniz işleci tanımladığından emin olun.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [İşleç Yordamları](./operator-procedures.md)
- [Nasıl yapılır: İşleç Tanımlama](./how-to-define-an-operator.md)
- [Nasıl yapılır: Dönüştürme İşleci Tanımlama](./how-to-define-a-conversion-operator.md)
- [Operator Deyimi](../../../../visual-basic/language-reference/statements/operator-statement.md)
- [Widening](../../../../visual-basic/language-reference/modifiers/widening.md)
- [Narrowing](../../../../visual-basic/language-reference/modifiers/narrowing.md)
- [Structure Deyimi](../../../../visual-basic/language-reference/statements/structure-statement.md)
- [Nasıl yapılır: Bir Yapıyı Bildirme](../../../../visual-basic/programming-guide/language-features/data-types/how-to-declare-a-structure.md)
- [Örtük ve Açık Dönüştürmeler](../../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
- [Genişletme ve Daraltma Dönüştürmeleri](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
