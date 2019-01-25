---
title: 'Nasıl yapılır: (Visual Basic) bir değer döndüren bir yordam oluşturma'
ms.date: 07/20/2015
helpviewer_keywords:
- procedures [Visual Basic], defining
- Visual Basic code, procedures
- procedures [Visual Basic], returning a value
ms.assetid: 8ee19f95-a9ef-4033-963b-d224dca207c4
ms.openlocfilehash: 18becfe05da27e538c5c294b26e0bb7aa19cad2b
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54506426"
---
# <a name="how-to-create-a-procedure-that-returns-a-value-visual-basic"></a>Nasıl yapılır: (Visual Basic) bir değer döndüren bir yordam oluşturma
Kullandığınız bir `Function` yordamın çağrıldığı koda bir değer döndürür.  
  
### <a name="to-create-a-procedure-that-returns-a-value"></a>Bir değer döndüren bir yordam oluşturmak için  
  
1.  Diğer herhangi bir yordam dışında kullanmak bir `Function` deyimi, arkasından bir `End Function` deyimi.  
  
2.  İçinde `Function` deyimi izleyin `Function` adını yordamı ve parantez içinde parametre listesi ile anahtar sözcüğü.  
  
3.  Parantezler ile izleyin bir `As` yan tümcesi, döndürülen değerin veri türü belirtmek için.  
  
4.  Yordam kod deyimlerini arasında yerleştirin `Function` ve `End Function` deyimleri.  
  
5.  Kullanım bir `Return` deyimini çağrıldığı koda bir değer döndürür.  
  
     Aşağıdaki `Function` yordamı, en uzun kenar veya, diğer iki yüz için değerlerine dik üçgenin, hipotenüsü hesaplar.  
  
     [!code-vb[VbVbcnProcedures#1](./codesnippet/VisualBasic/how-to-create-a-procedure-that-returns-a-value_1.vb)]  
  
     Aşağıdaki örnek, tipik bir çağrı gösterir `hypotenuse`.  
  
     [!code-vb[VbVbcnProcedures#6](./codesnippet/VisualBasic/how-to-create-a-procedure-that-returns-a-value_2.vb)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Yordamlar](./index.md)
- [Alt Yordamlar](./sub-procedures.md)
- [Özellik Yordamları](./property-procedures.md)
- [İşleç Yordamları](./operator-procedures.md)
- [Yordam Parametreleri ve Bağımsız Değişkenleri](./procedure-parameters-and-arguments.md)
- [Function Deyimi](../../../../visual-basic/language-reference/statements/function-statement.md)
- [Nasıl yapılır: Bir yordamdan değer döndürme](./how-to-return-a-value-from-a-procedure.md)
- [Nasıl yapılır: Bir değer döndüren bir yordam çağırma](./how-to-call-a-procedure-that-returns-a-value.md)
