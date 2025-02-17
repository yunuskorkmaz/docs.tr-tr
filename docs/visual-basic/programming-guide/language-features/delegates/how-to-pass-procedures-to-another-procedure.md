---
description: 'Daha fazla bilgi edinin: nasıl yapılır: yordamları Visual Basic başka bir yordama geçirme'
title: "Nasıl yapılır: Visual Basic'de Başka Bir Yordama Yordam Geçirme"
ms.date: 07/20/2015
helpviewer_keywords:
- AddressOf operator [Visual Basic]
- delegates [Visual Basic], passing procedures
ms.assetid: 5adbba15-5a1d-413f-ab3e-3ff6cc0a4669
ms.openlocfilehash: dfd75d1f58519365bfb6ac59892238b5322743f3
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100434452"
---
# <a name="how-to-pass-procedures-to-another-procedure-in-visual-basic"></a>Nasıl yapılır: Visual Basic'de Başka Bir Yordama Yordam Geçirme

Bu örnek, bir yordamın başka bir yordama iletilmesi için temsilcilerin nasıl kullanılacağını gösterir.  
  
 Temsilci, Visual Basic diğer herhangi bir tür gibi kullanabileceğiniz bir türdür. `AddressOf`İşleci bir yordam adına uygulandığında bir temsilci nesnesi döndürür.  
  
 Bu örnek, işleç ile elde edilen başka bir yordama başvuru alan bir temsilci parametresi olan bir yordama sahiptir `AddressOf` .  
  
### <a name="create-the-delegate-and-matching-procedures"></a>Temsilci ve eşleştirme yordamlarını oluşturma  
  
1. Adlı bir temsilci oluşturun `MathOperator` .  
  
     [!code-vb[VbVbalrDelegates#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDelegates/VB/Class1.vb#1)]  
  
2. `AddNumbers`İmzaların eşleşmesi için parametreleriyle eşleşen parametre ve dönüş değeri ile adlı bir yordam oluşturun `MathOperator` .  
  
     [!code-vb[VbVbalrDelegates#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDelegates/VB/Class1.vb#2)]  
  
3. İle eşleşen imzaya sahip adlı bir yordam oluşturun `SubtractNumbers` `MathOperator` .  
  
     [!code-vb[VbVbalrDelegates#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDelegates/VB/Class1.vb#3)]  
  
4. Bir `DelegateTest` temsilciyi parametre olarak alan adlı bir yordam oluşturun.  
  
     `AddNumbers` `SubtractNumbers` İmzaları imzayla eşleştiğinden, bu yordam veya için bir başvuruyu kabul edebilir `MathOperator` .  
  
     [!code-vb[VbVbalrDelegates#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDelegates/VB/Class1.vb#4)]  
  
5. `Test`Parametresi olarak bir kez çağıran adlı bir yordam oluşturun `DelegateTest` ve bir `AddNumbers` parametre olarak için temsilciyle yeniden `SubtractNumbers` .  
  
     [!code-vb[VbVbalrDelegates#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDelegates/VB/Class1.vb#5)]  
  
     `Test`Çağrıldığında, ilk olarak, `AddNumbers` `5` 8 olan ve üzerinde işlem sonucunu görüntüler `3` . Daha sonra `SubtractNumbers` `9` , ve üzerinde işlem sonucu `3` , 6 ' da görüntülenir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Temsilciler](index.md)
- [AddressOf İşleci](../../../language-reference/operators/addressof-operator.md)
- [Delegate Deyimi](../../../language-reference/statements/delegate-statement.md)
- [Nasıl yapılır: Temsilci Yöntemi Çağırma](how-to-invoke-a-delegate-method.md)
