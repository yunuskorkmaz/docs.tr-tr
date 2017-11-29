---
title: "Nasıl yapılır: Değer Döndüren Bir Yordam Oluşturma (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- procedures [Visual Basic], defining
- Visual Basic code, procedures
- procedures [Visual Basic], returning a value
ms.assetid: 8ee19f95-a9ef-4033-963b-d224dca207c4
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 787eddc1fd1cdb9dd6b655a8556b75044b2a49dc
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
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
 [Yordamları](./index.md)  
 [Alt yordamlar](./sub-procedures.md)  
 [Özellik yordamları](./property-procedures.md)  
 [İşleç yordamları](./operator-procedures.md)  
 [Parametreler ve bağımsız değişkenler](./procedure-parameters-and-arguments.md)  
 [Function deyimi](../../../../visual-basic/language-reference/statements/function-statement.md)  
 [Nasıl yapılır: bir yordamdan değer döndürme](./how-to-return-a-value-from-a-procedure.md)  
 [Nasıl yapılır: değer döndüren bir yordam çağırma](./how-to-call-a-procedure-that-returns-a-value.md)
