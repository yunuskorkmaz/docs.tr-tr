---
title: 'Nasıl yapılır: Değer Döndüren Bir Yordam Oluşturma'
ms.date: 07/20/2015
helpviewer_keywords:
- procedures [Visual Basic], defining
- Visual Basic code, procedures
- procedures [Visual Basic], returning a value
ms.assetid: 8ee19f95-a9ef-4033-963b-d224dca207c4
ms.openlocfilehash: 218dbb52abc0100724d38d10be91ef24252d5226
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74349715"
---
# <a name="how-to-create-a-procedure-that-returns-a-value-visual-basic"></a>Nasıl yapılır: Değer Döndüren Bir Yordam Oluşturma (Visual Basic)
Çağırma koduna bir değer döndürmek için `Function` yordamını kullanın.  
  
### <a name="to-create-a-procedure-that-returns-a-value"></a>Bir değer döndüren bir yordam oluşturmak için  
  
1. Diğer herhangi bir yordamın dışında, bir `Function` ifadesini ve ardından bir `End Function` bildirisini kullanın.  
  
2. `Function` bildiriminde, yordamın adı ile `Function` anahtar sözcüğünü ve ardından parantez içindeki parametre listesini izleyin.  
  
3. Döndürülen değerin veri türünü belirtmek için bir `As` yan tümcesiyle ayraçları izleyin.  
  
4. Yordamın kod deyimlerini `Function` ve `End Function` deyimleri arasına yerleştirin.  
  
5. Değeri çağırma koduna döndürmek için bir `Return` ifadesini kullanın.  
  
     Aşağıdaki `Function` yordam, iki tarafa ait değerler verildiğinde, doğru bir üçgenin en uzun tarafını veya hipotenüsü değerini hesaplar.  
  
     [!code-vb[VbVbcnProcedures#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#1)]  
  
     Aşağıdaki örnek `hypotenuse`tipik bir çağrısını gösterir.  
  
     [!code-vb[VbVbcnProcedures#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#6)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Yordamlar](./index.md)
- [Alt Yordamlar](./sub-procedures.md)
- [Özellik Yordamları](./property-procedures.md)
- [İşleç Yordamları](./operator-procedures.md)
- [Yordam Parametreleri ve Bağımsız Değişkenleri](./procedure-parameters-and-arguments.md)
- [Function Deyimi](../../../../visual-basic/language-reference/statements/function-statement.md)
- [Nasıl yapılır: Bir Yordamdan Değer Döndürme](./how-to-return-a-value-from-a-procedure.md)
- [Nasıl yapılır: Değer Döndüren Bir Yordam Çağırma](./how-to-call-a-procedure-that-returns-a-value.md)
