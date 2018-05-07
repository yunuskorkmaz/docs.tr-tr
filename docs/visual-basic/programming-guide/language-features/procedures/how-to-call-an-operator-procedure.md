---
title: 'Nasıl yapılır: Bir İşleç Yordamı Çağırma (Visual Basic)'
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
ms.openlocfilehash: b1dc4477daa4ceb9dfc6a9a6ab3f041e68011acd
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-call-an-operator-procedure-visual-basic"></a>Nasıl yapılır: Bir İşleç Yordamı Çağırma (Visual Basic)
Bir ifadeyi işleç simgesi kullanarak bir işleç yordamı çağırma. Bir dönüşüm işleci söz konusu olduğunda, çağrı [CType işlevi](../../../../visual-basic/language-reference/functions/ctype-function.md) bir değer bir veri türünden dönüştürmek için.  
  
 İşleç yordamları açıkça çağırmayın. Yalnızca işlecini kullanın veya `CType` bir atama ifadesi veya bir ifade, bir işleç normalde kullandığınız gibi işlev. Visual Basic işleç yordamı çağrıda bulunur.  
  
 Bir sınıf veya yapı bir işleci tanımlama olarak da adlandırılır *aşırı* işleci.  
  
### <a name="to-call-an-operator-procedure"></a>Bir işleç yordamı çağırma için  
  
1.  İşleç simgesi bir ifadede normal şekilde kullanın.  
  
2.  İşlenen veri türlerini operatöre ve doğru sırada uygun olduğundan emin olun.  
  
3.  İşleci, beklendiği gibi ifadenin değerini katkıda bulunur.  
  
### <a name="to-call-a-conversion-operator-procedure"></a>Bir dönüştürme işleç yordamı çağırma için  
  
1.  Kullanım `CType` içinde bir ifade.  
  
2.  İşlenen veri türlerini dönüştürme işlemi için ve doğru sırada uygun olduğundan emin olun.  
  
3.  `CType` dönüştürme işleci yordam çağrıları ve dönüştürülen değeri döndürür.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte iki oluşturur <xref:System.TimeSpan> yapıları, bunları bir araya getirir ve üçüncü bir sonucu depolar <xref:System.TimeSpan> yapısı. <xref:System.TimeSpan> Yapısı birkaç standart işleci aşırı yüklemeyi işleç yordamları tanımlar.  
  
 [!code-vb[VbVbcnProcedures#29](./codesnippet/VisualBasic/how-to-call-an-operator-procedure_1.vb)]  
  
 Çünkü <xref:System.TimeSpan> standart overloads `+` işleci, önceki örnekte çağıran bir işleç yordamı değeri hesaplarken `combinedSpan`.  
  
 Konuşma işleç yordamı çağırma örneği için bkz: [nasıl yapılır: bir sınıf tanımlar, işleçler kullanma](./how-to-use-a-class-that-defines-operators.md).  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Sınıf veya yapı kullanmakta olduğunuz kullanmak istediğiniz işleci tanımlar emin olun.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [İşleç Yordamları](./operator-procedures.md)  
 [Nasıl yapılır: İşleç Tanımlama](./how-to-define-an-operator.md)  
 [Nasıl yapılır: Dönüştürme İşleci Tanımlama](./how-to-define-a-conversion-operator.md)  
 [Operator Deyimi](../../../../visual-basic/language-reference/statements/operator-statement.md)  
 [Widening](../../../../visual-basic/language-reference/modifiers/widening.md)  
 [Narrowing](../../../../visual-basic/language-reference/modifiers/narrowing.md)  
 [Structure Deyimi](../../../../visual-basic/language-reference/statements/structure-statement.md)  
 [Nasıl yapılır: Bir Yapıyı Bildirme](../../../../visual-basic/programming-guide/language-features/data-types/how-to-declare-a-structure.md)  
 [Örtük ve Açık Dönüştürmeler](../../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)  
 [Genişletme ve Daraltma Dönüştürmeleri](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
