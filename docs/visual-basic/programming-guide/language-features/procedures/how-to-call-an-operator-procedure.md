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
ms.openlocfilehash: fa2bc5417b8b917ff48502a5bd0a4daa21fab67e
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84388575"
---
# <a name="how-to-call-an-operator-procedure-visual-basic"></a>Nasıl yapılır: Bir İşleç Yordamı Çağırma (Visual Basic)
Bir ifadede işleç sembolünü kullanarak bir işleç yordamı çağırın. Bir dönüştürme işleci söz konusu olduğunda, bir değeri bir veri türünden diğerine dönüştürmek için [CType işlevini](../../../language-reference/functions/ctype-function.md) çağırın.  
  
 Operatör yordamlarını açıkça çağırmayın. Yalnızca işlecini veya bir deyimi, bir `CType` atama deyiminde veya bir ifadede, normalde bir işleci kullandığınız şekilde kullanırsınız. Visual Basic işleç yordamına çağrı yapar.  
  
 Bir sınıf veya yapı üzerinde işleç tanımlamak, işleci *aşırı yükleme* olarak da adlandırılır.  
  
### <a name="to-call-an-operator-procedure"></a>Bir işleç yordamını çağırmak için  
  
1. Bir ifadede işleç sembolünü normal şekilde kullanın.  
  
2. İşlenenlerin veri türlerinin operatör için uygun olduğundan ve doğru sırada olduğundan emin olun.  
  
3. İşleci, ifadenin değerine beklenen şekilde katkıda bulunur.  
  
### <a name="to-call-a-conversion-operator-procedure"></a>Bir dönüştürme işleci yordamını çağırmak için  
  
1. `CType`Bir ifadenin içinde kullanın.  
  
2. İşlenenlerin veri türlerinin dönüştürme için uygun olduğundan ve doğru sırada olduğundan emin olun.  
  
3. `CType`dönüştürme işleci yordamını çağırır ve dönüştürülen değeri döndürür.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek iki yapı oluşturur <xref:System.TimeSpan> , bunları birlikte ekler ve sonucu üçüncü bir <xref:System.TimeSpan> yapıda depolar. <xref:System.TimeSpan>Yapı, birkaç standart işlecin aşırı yüklenmesine yönelik operatör yordamlarını tanımlar.  
  
 [!code-vb[VbVbcnProcedures#29](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#29)]  
  
 <xref:System.TimeSpan>Standart `+` işleci aşırı yüklediğinden, önceki örnek değerini hesaplarken bir işleç yordamını çağırır `combinedSpan` .  
  
 Bir konuşma işleci yordamı çağırma örneği için bkz. [nasıl yapılır: Işleçleri tanımlayan bir sınıf kullanma](./how-to-use-a-class-that-defines-operators.md).  
  
## <a name="compile-the-code"></a>Kodu derle  
 Kullandığınız sınıf veya yapının kullanmak istediğiniz işleci tanımladığından emin olun.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [İşleç Yordamları](./operator-procedures.md)
- [Nasıl yapılır: İşleç Tanımlama](./how-to-define-an-operator.md)
- [Nasıl yapılır: Dönüştürme İşleci Tanımlama](./how-to-define-a-conversion-operator.md)
- [Operator Deyimi](../../../language-reference/statements/operator-statement.md)
- [Genişletme](../../../language-reference/modifiers/widening.md)
- [Narrowing](../../../language-reference/modifiers/narrowing.md)
- [Structure Yapısı](../../../language-reference/statements/structure-statement.md)
- [Nasıl yapılır: Yapıyı Bildirme](../data-types/how-to-declare-a-structure.md)
- [Örtük ve Açık Dönüştürmeler](../data-types/implicit-and-explicit-conversions.md)
- [Genişletme ve Daraltma Dönüşümleri](../data-types/widening-and-narrowing-conversions.md)
