---
title: 'Nasıl yapılır: Değer Döndüren Bir Yordam Oluşturma (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- procedures [Visual Basic], defining
- Visual Basic code, procedures
- procedures [Visual Basic], returning a value
ms.assetid: 8ee19f95-a9ef-4033-963b-d224dca207c4
ms.openlocfilehash: 472f55173a4897a23a82812a2b24bf1646c1a6ed
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33648443"
---
# <a name="how-to-create-a-procedure-that-returns-a-value-visual-basic"></a>Nasıl yapılır: Değer Döndüren Bir Yordam Oluşturma (Visual Basic)
Kullandığınız bir `Function` yordamı çağıran kodu için bir değer döndürür.  
  
### <a name="to-create-a-procedure-that-returns-a-value"></a>Bir değer döndüren bir yordam oluşturmak için  
  
1.  Diğer herhangi bir yordam dışında kullanmak bir `Function` deyimi, arkasından bir `End Function` deyimi.  
  
2.  İçinde `Function` deyimi, izleyin `Function` adını yordamı ve parantez içinde parametre listesi olan anahtar sözcük.  
  
3.  Parantezler ile izleyin bir `As` yan tümcesini döndürülen değerin veri türü belirtin.  
  
4.  Yordam kod deyimleri arasında yerleştirin `Function` ve `End Function` deyimleri.  
  
5.  Kullanım bir `Return` deyimi çağıran kodu değerini döndürür.  
  
     Aşağıdaki `Function` yordamı en uzun taraf veya diğer iki kenara için değerlerine göre bir sağ üçgen hipotenüsü hesaplar.  
  
     [!code-vb[VbVbcnProcedures#1](./codesnippet/VisualBasic/how-to-create-a-procedure-that-returns-a-value_1.vb)]  
  
     Aşağıdaki örnek tipik bir çağrı gösterilmektedir `hypotenuse`.  
  
     [!code-vb[VbVbcnProcedures#6](./codesnippet/VisualBasic/how-to-create-a-procedure-that-returns-a-value_2.vb)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Yordamlar](./index.md)  
 [Alt Yordamlar](./sub-procedures.md)  
 [Özellik Yordamları](./property-procedures.md)  
 [İşleç Yordamları](./operator-procedures.md)  
 [Yordam Parametreleri ve Bağımsız Değişkenleri](./procedure-parameters-and-arguments.md)  
 [Function Deyimi](../../../../visual-basic/language-reference/statements/function-statement.md)  
 [Nasıl yapılır: Bir Yordamdan Değer Döndürme](./how-to-return-a-value-from-a-procedure.md)  
 [Nasıl yapılır: Değer Döndüren Bir Yordam Çağırma](./how-to-call-a-procedure-that-returns-a-value.md)
