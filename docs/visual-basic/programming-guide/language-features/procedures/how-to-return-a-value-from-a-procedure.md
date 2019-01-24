---
title: 'Nasıl yapılır: Bir değer döndüren bir yordam (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- Visual Basic code, procedures
- procedures [Visual Basic], returning from
- procedures [Visual Basic], returning a value
ms.assetid: 4bcc4724-2b4e-4df8-9b4b-16054607f87d
ms.openlocfilehash: 38b0673f5725077eec9253021eec4216e66504a2
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54615263"
---
# <a name="how-to-return-a-value-from-a-procedure-visual-basic"></a>Nasıl yapılır: Bir değer döndüren bir yordam (Visual Basic)
A `Function` yordamı değeri döndürür çağırma kodu yürüterek ya da bir `Return` deyimi veya karşılaşıldığında bir `Exit Function` veya `End Function` deyimi.  
  
### <a name="to-return-a-value-using-the-return-statement"></a>Return deyimi kullanarak bir değer döndürmek için  
  
1.  PUT bir `Return` burada yordam görev tamamlandığında bir noktada deyimi.  
  
2.  İzleyin `Return` çağrıldığı koda döndürmek istediğiniz anahtar sözcüğü ile değer döndüren bir ifade.  
  
3.  Birden fazla aboneliğiniz `Return` aynı yordamındaki.  
  
     Aşağıdaki `Function` yordam en uzun kenar veya, dik üçgenin, hipotenüsü hesaplar ve çağıran koda döndürür.  
  
     [!code-vb[VbVbcnProcedures#1](./codesnippet/VisualBasic/how-to-return-a-value-from-a-procedure_1.vb)]  
  
     Aşağıdaki örnek, tipik bir çağrı gösterir `hypotenuse`, döndürülen değer depolar.  
  
     [!code-vb[VbVbcnProcedures#6](./codesnippet/VisualBasic/how-to-return-a-value-from-a-procedure_2.vb)]  
  
### <a name="to-return-a-value-using-exit-function-or-end-function"></a>Exit işlevine veya End işlevi kullanarak bir değer döndürmek için  
  
1.  En az bir yerinde `Function` yordamı, bir yordam adı için bir değer atayın.  
  
2.  Çalıştırdığınızda bir `Exit Function` veya `End Function` deyimi, Visual Basic, en son yordam adı için atanan değer döndürür.  
  
3.  Birden fazla aboneliğiniz `Exit Function` aynı yordamı ve deyiminde karıştırmak `Return` ve `Exit Function` deyimleri aynı yordam içinde.  
  
4.  Tek sahip `End Function` deyiminde bir `Function` yordamı.  
  
     Daha fazla bilgi ve örnek için "Dönüş değerini" bölümüne bakın [Function deyimi](../../../../visual-basic/language-reference/statements/function-statement.md).  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Yordamlar](./index.md)
- [Alt Yordamlar](./sub-procedures.md)
- [Özellik Yordamları](./property-procedures.md)
- [İşleç Yordamları](./operator-procedures.md)
- [Yordam Parametreleri ve Bağımsız Değişkenleri](./procedure-parameters-and-arguments.md)
- [Function Deyimi](../../../../visual-basic/language-reference/statements/function-statement.md)
- [Return Deyimi](../../../../visual-basic/language-reference/statements/return-statement.md)
- [Nasıl yapılır: Bir değer döndüren bir yordam oluşturma](./how-to-create-a-procedure-that-returns-a-value.md)
- [Nasıl yapılır: Bir değer döndüren bir yordam çağırma](./how-to-call-a-procedure-that-returns-a-value.md)
