---
title: "Nasıl yapılır: Visual Basic'de başka bir yordama yordam geçirin"
ms.date: 07/20/2015
helpviewer_keywords:
- AddressOf operator [Visual Basic]
- delegates [Visual Basic], passing procedures
ms.assetid: 5adbba15-5a1d-413f-ab3e-3ff6cc0a4669
ms.openlocfilehash: 312c0e0f100e85256ad4ca856ccf7f35dbaa36dc
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61973296"
---
# <a name="how-to-pass-procedures-to-another-procedure-in-visual-basic"></a>Nasıl yapılır: Visual Basic'de başka bir yordama yordam geçirin
Bu örnek, temsilciler başka bir yordama yordam geçirme için nasıl kullanılacağını gösterir.  
  
 Bir temsilci, herhangi bir türü Visual Basic'te gibi kullanabileceğiniz bir türdür. `AddressOf` İşleci bir yordam adına uygulandığında bir temsilci nesnesini döndürür.  
  
 Bu örnek ile elde ettiğiniz başka bir yordama başvuru sürebilir bir temsilci parametresi içeren bir yordamı sahip `AddressOf` işleci.  
  
### <a name="create-the-delegate-and-matching-procedures"></a>Temsilci ve eşleşen yordamlar oluşturma  
  
1. Adlı bir temsilci oluşturmak `MathOperator`.  
  
     [!code-vb[VbVbalrDelegates#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDelegates/VB/Class1.vb#1)]  
  
2. Adlı bir yordam oluşturma `AddNumbers` parametreleri ve eşleşen dönüş değeri ile `MathOperator`, böylece imzalar.  
  
     [!code-vb[VbVbalrDelegates#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDelegates/VB/Class1.vb#2)]  
  
3. Adlı bir yordam oluşturma `SubtractNumbers` imzayla eşleşen `MathOperator`.  
  
     [!code-vb[VbVbalrDelegates#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDelegates/VB/Class1.vb#3)]  
  
4. Adlı bir yordam oluşturma `DelegateTest` , temsilci bir parametre olarak alır.  
  
     Bu yordam bir başvuru kabul edebilir `AddNumbers` veya `SubtractNumbers`, bunların imzalarını eşleştiğinden `MathOperator` imzası.  
  
     [!code-vb[VbVbalrDelegates#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDelegates/VB/Class1.vb#4)]  
  
5. Adlı bir yordam oluşturma `Test` çağrılarının `DelegateTest` temsilcisi ile bir kez `AddNumbers` bir parametre olarak ve yeniden temsilcisi ile `SubtractNumbers` bir parametre olarak.  
  
     [!code-vb[VbVbalrDelegates#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDelegates/VB/Class1.vb#5)]  
  
     Zaman `Test` olan çağrılır, ilk sonucunu görüntüler `AddNumbers` üzerinde yürüten `5` ve `3`, 8 olduğu. Ardından sonucunu `SubtractNumbers` üzerinde çalışan `9` ve `3` görüntülenir, 6.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Temsilciler](../../../../visual-basic/programming-guide/language-features/delegates/index.md)
- [AddressOf İşleci](../../../../visual-basic/language-reference/operators/addressof-operator.md)
- [Delegate Deyimi](../../../../visual-basic/language-reference/statements/delegate-statement.md)
- [Nasıl yapılır: Bir temsilci yöntemi çağırma](../../../../visual-basic/programming-guide/language-features/delegates/how-to-invoke-a-delegate-method.md)
