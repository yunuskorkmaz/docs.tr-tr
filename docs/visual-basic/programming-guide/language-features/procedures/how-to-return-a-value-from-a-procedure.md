---
title: 'Nasıl yapılır: Bir Yordamdan Değer Döndürme (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- Visual Basic code, procedures
- procedures [Visual Basic], returning from
- procedures [Visual Basic], returning a value
ms.assetid: 4bcc4724-2b4e-4df8-9b4b-16054607f87d
ms.openlocfilehash: 62e8a52e488247d4dfcde2a560920447abe1c182
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-return-a-value-from-a-procedure-visual-basic"></a>Nasıl yapılır: Bir Yordamdan Değer Döndürme (Visual Basic)
A `Function` yordamı değeri döndürür çağıran kodu çalıştırarak ya da bir `Return` deyimi veya karşılaşmadan bir `Exit Function` veya `End Function` deyimi.  
  
### <a name="to-return-a-value-using-the-return-statement"></a>Return deyimi kullanarak bir değer döndürmek için  
  
1.  PUT bir `Return` yordam görev tamamlandı burada noktada deyimi.  
  
2.  İzleyin `Return` dönüş çağıran kodu istediğiniz anahtar sözcüğü ile değer döndüren bir ifade.  
  
3.  Birden fazla sahip `Return` aynı yordamı deyiminde.  
  
     Aşağıdaki `Function` yordamı uzun yan veya sağ üçgen hipotenüsü hesaplar ve arama kodu döndürür.  
  
     [!code-vb[VbVbcnProcedures#1](./codesnippet/VisualBasic/how-to-return-a-value-from-a-procedure_1.vb)]  
  
     Aşağıdaki örnek tipik bir çağrı gösterilmektedir `hypotenuse`, döndürülen değer depolar.  
  
     [!code-vb[VbVbcnProcedures#6](./codesnippet/VisualBasic/how-to-return-a-value-from-a-procedure_2.vb)]  
  
### <a name="to-return-a-value-using-exit-function-or-end-function"></a>Exit işlevi veya End işlevi kullanarak bir değer döndürmek için  
  
1.  En az bir yerinde `Function` yordamı, Ata bir değer yordamın adı.  
  
2.  Çalıştırdığınızda bir `Exit Function` veya `End Function` deyimi, Visual Basic en son yordam adına atanmış değeri döndürür.  
  
3.  Birden fazla sahip `Exit Function` aynı yordamı ve deyiminde karışık `Return` ve `Exit Function` aynı yordamı deyimlerinde.  
  
4.  Yalnızca bir bulunabilir `End Function` deyiminde bir `Function` yordamı.  
  
     Daha fazla bilgi ve bir örnek için "Dönüş değeri" bölümüne bakın [Function deyimi](../../../../visual-basic/language-reference/statements/function-statement.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Yordamlar](./index.md)  
 [Alt Yordamlar](./sub-procedures.md)  
 [Özellik Yordamları](./property-procedures.md)  
 [İşleç Yordamları](./operator-procedures.md)  
 [Yordam Parametreleri ve Bağımsız Değişkenleri](./procedure-parameters-and-arguments.md)  
 [Function Deyimi](../../../../visual-basic/language-reference/statements/function-statement.md)  
 [Return Deyimi](../../../../visual-basic/language-reference/statements/return-statement.md)  
 [Nasıl yapılır: Değer Döndüren Bir Yordam Oluşturma](./how-to-create-a-procedure-that-returns-a-value.md)  
 [Nasıl yapılır: Değer Döndüren Bir Yordam Çağırma](./how-to-call-a-procedure-that-returns-a-value.md)
