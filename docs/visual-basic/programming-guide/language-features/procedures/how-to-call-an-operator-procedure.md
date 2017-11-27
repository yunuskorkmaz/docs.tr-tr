---
title: "Nasıl yapılır: Bir İşleç Yordamı Çağırma (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
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
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 0abff0a81ebcdacb59b69d0c307bb4aa219906c3
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-call-an-operator-procedure-visual-basic"></a>Nasıl yapılır: Bir İşleç Yordamı Çağırma (Visual Basic)
Bir ifadeyi işleç simgesi kullanarak bir işleç yordamı çağırma. Bir dönüşüm işleci söz konusu olduğunda, çağrı [CType işlevi](../../../../visual-basic/language-reference/functions/ctype-function.md) bir değer bir veri türünden dönüştürmek için.  
  
 İşleç yordamları açıkça çağırmayın. Yalnızca işlecini kullanın veya `CType` bir atama ifadesi veya bir ifade, bir işleç normalde kullandığınız gibi işlev. [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]işleç yordamı çağrıda bulunur.  
  
 Bir sınıf veya yapı bir işleci tanımlama olarak da adlandırılır *aşırı* işleci.  
  
### <a name="to-call-an-operator-procedure"></a>Bir işleç yordamı çağırma için  
  
1.  İşleç simgesi bir ifadede normal şekilde kullanın.  
  
2.  İşlenen veri türlerini operatöre ve doğru sırada uygun olduğundan emin olun.  
  
3.  İşleci, beklendiği gibi ifadenin değerini katkıda bulunur.  
  
### <a name="to-call-a-conversion-operator-procedure"></a>Bir dönüştürme işleç yordamı çağırma için  
  
1.  Kullanım `CType` içinde bir ifade.  
  
2.  İşlenen veri türlerini dönüştürme işlemi için ve doğru sırada uygun olduğundan emin olun.  
  
3.  `CType`dönüştürme işleci yordam çağrıları ve dönüştürülen değeri döndürür.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte iki oluşturur <xref:System.TimeSpan> yapıları, bunları bir araya getirir ve üçüncü bir sonucu depolar <xref:System.TimeSpan> yapısı. <xref:System.TimeSpan> Yapısı birkaç standart işleci aşırı yüklemeyi işleç yordamları tanımlar.  
  
 [!code-vb[VbVbcnProcedures#29](./codesnippet/VisualBasic/how-to-call-an-operator-procedure_1.vb)]  
  
 Çünkü <xref:System.TimeSpan> standart overloads `+` işleci, önceki örnekte çağıran bir işleç yordamı değeri hesaplarken `combinedSpan`.  
  
 Konuşma işleç yordamı çağırma örneği için bkz: [nasıl yapılır: bir sınıf tanımlar, işleçler kullanma](./how-to-use-a-class-that-defines-operators.md).  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Sınıf veya yapı kullanmakta olduğunuz kullanmak istediğiniz işleci tanımlar emin olun.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [İşleç yordamları](./operator-procedures.md)  
 [Nasıl yapılır: bir işleci tanımlama](./how-to-define-an-operator.md)  
 [Nasıl yapılır: bir dönüşüm işleci tanımlama](./how-to-define-a-conversion-operator.md)  
 [Operator deyimi](../../../../visual-basic/language-reference/statements/operator-statement.md)  
 [Genişletme](../../../../visual-basic/language-reference/modifiers/widening.md)  
 [Daraltma](../../../../visual-basic/language-reference/modifiers/narrowing.md)  
 [Structure deyimi](../../../../visual-basic/language-reference/statements/structure-statement.md)  
 [Nasıl yapılır: bir yapıyı bildirme](../../../../visual-basic/programming-guide/language-features/data-types/how-to-declare-a-structure.md)  
 [Örtük ve açık dönüştürmeler](../../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)  
 [Genişletme ve daraltma dönüşümleri](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
