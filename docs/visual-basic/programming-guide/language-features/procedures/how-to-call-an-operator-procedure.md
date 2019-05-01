---
title: 'Nasıl yapılır: (Visual Basic) bir işleç yordamı çağırma'
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
ms.openlocfilehash: d68781aa12ab7c1c717031ca252c5f3120649edc
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61863941"
---
# <a name="how-to-call-an-operator-procedure-visual-basic"></a>Nasıl yapılır: (Visual Basic) bir işleç yordamı çağırma
Bir ifadede operatör sembolünü kullanarak, bir işleç yordamı çağırma. Bir dönüştürme operatörünün söz konusu olduğunda, çağrı [CType işlevi](../../../../visual-basic/language-reference/functions/ctype-function.md) bir değeri bir veri türünden dönüştürme.  
  
 İşleç yordamları açıkça çağırmayın. İşleci, yalnızca kullandığınız ya da `CType` işlevi, atama deyiminin veya bir ifade, operatörün normalde kullandığınız gibi. Visual Basic işleç yordamı çağrıda bulunur.  
  
 Bir sınıf ya da yapı üzerinde operatör tanımlama olarak da adlandırılır *aşırı yükleme* işleci.  
  
### <a name="to-call-an-operator-procedure"></a>Bir işleç yordamı çağırma için  
  
1. İşlecin bir ifadede normal şekilde kullanın.  
  
2. İşlenen veri türlerini işleci için ve doğru sırada uygun olduğundan emin olun.  
  
3. İşleci, beklenen şekilde ifadesinin değerine katkıda bulunur.  
  
### <a name="to-call-a-conversion-operator-procedure"></a>Bir dönüştürme işleci yordam çağırmak için  
  
1. Kullanım `CType` içinde bir ifade.  
  
2. İşlenen veri türlerini dönüştürme ve doğru sırada uygun olduğundan emin olun.  
  
3. `CType` dönüştürme işleci yordam çağrıları ve dönüştürülen değeri döndürür.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek iki oluşturur <xref:System.TimeSpan> yapıları, bunları bir araya getirir ve sonucu bir üçüncü depolar <xref:System.TimeSpan> yapısı. <xref:System.TimeSpan> Birkaç standart İşleç aşırı yüklemeyi işleç yordamları yapısını tanımlar.  
  
 [!code-vb[VbVbcnProcedures#29](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#29)]  
  
 Çünkü <xref:System.TimeSpan> Standart aşırı `+` işleci, önceki örnekte çağıran bir işleç yordamı değerini hesaplarken `combinedSpan`.  
  
 Konuşma bir işleç yordamı çağırma örneği için bkz: [nasıl yapılır: İşleçleri tanımlayan bir sınıf kullanma](./how-to-use-a-class-that-defines-operators.md).  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Kullanmak istediğiniz işleci tanımlar, sınıfın veya yapının kullanmakta olduğunuz emin olun.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [İşleç Yordamları](./operator-procedures.md)
- [Nasıl yapılır: Bir işleci tanımlama](./how-to-define-an-operator.md)
- [Nasıl yapılır: Bir dönüşüm işleci tanımlama](./how-to-define-a-conversion-operator.md)
- [Operator Deyimi](../../../../visual-basic/language-reference/statements/operator-statement.md)
- [Widening](../../../../visual-basic/language-reference/modifiers/widening.md)
- [Narrowing](../../../../visual-basic/language-reference/modifiers/narrowing.md)
- [Structure Deyimi](../../../../visual-basic/language-reference/statements/structure-statement.md)
- [Nasıl yapılır: Yapıyı Bildirme](../../../../visual-basic/programming-guide/language-features/data-types/how-to-declare-a-structure.md)
- [Örtük ve Açık Dönüştürmeler](../../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
- [Genişletme ve Daraltma Dönüştürmeleri](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
