---
title: "Nasıl yapılır: Visual Basic'de Başka Bir Yordama Yordam Geçirme"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- AddressOf operator [Visual Basic]
- delegates [Visual Basic], passing procedures
ms.assetid: 5adbba15-5a1d-413f-ab3e-3ff6cc0a4669
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 4e8e205f5238aab39aa92574bc5c680e68cc8a81
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-pass-procedures-to-another-procedure-in-visual-basic"></a>Nasıl yapılır: Visual Basic'de Başka Bir Yordama Yordam Geçirme
Bu örnek temsilciler başka bir yordama yordam geçirmek için nasıl kullanılacağını gösterir.  
  
 Bir temsilci gibi herhangi bir türü kullanabileceğiniz bir türüdür [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]. `AddressOf` İşleci bir yordam adı uygulandığında bir temsilci nesnesini döndürür.  
  
 Bu örnek bir yordamı ile elde başka bir yordam için bir başvuru yapabileceği bir temsilci parametresiyle sahip `AddressOf` işleci.  
  
### <a name="create-the-delegate-and-matching-procedures"></a>Temsilci oluşturup eşleşen yordamları  
  
1.  Adlı bir temsilci oluşturma `MathOperator`.  
  
     [!code-vb[VbVbalrDelegates#1](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-pass-procedures-to-another-procedure_1.vb)]  
  
2.  Adlı bir yordam oluşturma `AddNumbers` parametreleri ve eşleşen dönüş değeri ile `MathOperator`, imzaları eşleşmesi.  
  
     [!code-vb[VbVbalrDelegates#2](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-pass-procedures-to-another-procedure_2.vb)]  
  
3.  Adlı bir yordam oluşturma `SubtractNumbers` eşleşen imzayla `MathOperator`.  
  
     [!code-vb[VbVbalrDelegates#3](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-pass-procedures-to-another-procedure_3.vb)]  
  
4.  Adlı bir yordam oluşturma `DelegateTest` temsilci bir parametre olarak alır.  
  
     Bu yordam bir başvuru kabul edebilir `AddNumbers` veya `SubtractNumbers`, kendi imzaları eşleştiğinden `MathOperator` imza.  
  
     [!code-vb[VbVbalrDelegates#4](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-pass-procedures-to-another-procedure_4.vb)]  
  
5.  Adlı bir yordam oluşturma `Test` çağrısı `DelegateTest` için temsilci ile bir kez `AddNumbers` bir parametre olarak ve yeniden için temsilci ile `SubtractNumbers` bir parametre olarak.  
  
     [!code-vb[VbVbalrDelegates#5](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-pass-procedures-to-another-procedure_5.vb)]  
  
     Zaman `Test` olan çağrılmadan önce sonucunu gösterir `AddNumbers` üzerinde görevi `5` ve `3`, 8 olduğu. Ardından sonucunu `SubtractNumbers` üzerinde hareket `9` ve `3` görüntülenir, 6.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Temsilciler](../../../../visual-basic/programming-guide/language-features/delegates/index.md)  
 [AddressOf işleci](../../../../visual-basic/language-reference/operators/addressof-operator.md)  
 [Delegate deyimi](../../../../visual-basic/language-reference/statements/delegate-statement.md)  
 [Nasıl yapılır: temsilci yöntemi çağırma](../../../../visual-basic/programming-guide/language-features/delegates/how-to-invoke-a-delegate-method.md)
