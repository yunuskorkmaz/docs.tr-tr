---
title: 'Nasıl yapılır: başka bir yordama yordam geçirme'
ms.date: 07/20/2015
helpviewer_keywords:
- AddressOf operator [Visual Basic]
- delegates [Visual Basic], passing procedures
ms.assetid: 5adbba15-5a1d-413f-ab3e-3ff6cc0a4669
ms.openlocfilehash: 300489935ce54d78b989d09211a7f6ba95c2f514
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74345241"
---
# <a name="how-to-pass-procedures-to-another-procedure-in-visual-basic"></a>Nasıl yapılır: Visual Basic'de Başka Bir Yordama Yordam Geçirme
Bu örnek, bir yordamın başka bir yordama iletilmesi için temsilcilerin nasıl kullanılacağını gösterir.  
  
 Temsilci, Visual Basic diğer herhangi bir tür gibi kullanabileceğiniz bir türdür. `AddressOf` işleci bir yordam adına uygulandığında bir temsilci nesnesi döndürür.  
  
 Bu örnek, `AddressOf` işleci ile elde edilen başka bir yordama başvuru alan bir temsilci parametresi olan bir yordama sahiptir.  
  
### <a name="create-the-delegate-and-matching-procedures"></a>Temsilci ve eşleştirme yordamlarını oluşturma  
  
1. `MathOperator`adlı bir temsilci oluşturun.  
  
     [!code-vb[VbVbalrDelegates#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDelegates/VB/Class1.vb#1)]  
  
2. İmzaların eşleşmesi için `MathOperator`eşleşen parametrelere ve dönüş değerine sahip `AddNumbers` adlı bir yordam oluşturun.  
  
     [!code-vb[VbVbalrDelegates#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDelegates/VB/Class1.vb#2)]  
  
3. `MathOperator`eşleşen bir imzayla `SubtractNumbers` adlı bir yordam oluşturun.  
  
     [!code-vb[VbVbalrDelegates#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDelegates/VB/Class1.vb#3)]  
  
4. Bir temsilciyi parametre olarak alan `DelegateTest` adlı bir yordam oluşturun.  
  
     İmzaları `MathOperator` imzasıyla eşleştiğinden, bu yordam `AddNumbers` veya `SubtractNumbers`bir başvuruyu kabul edebilir.  
  
     [!code-vb[VbVbalrDelegates#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDelegates/VB/Class1.vb#4)]  
  
5. Bir parametre olarak `AddNumbers` temsilcisinden bir kez `DelegateTest` çağıran `Test` adlı bir yordam oluşturun ve bir parametre olarak `SubtractNumbers` için temsilciyle yeniden.  
  
     [!code-vb[VbVbalrDelegates#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDelegates/VB/Class1.vb#5)]  
  
     `Test` çağrıldığında, önce `5` ve `3`üzerinde işlem yapan `AddNumbers` sonucunu görüntüler, bu 8 ' dir. Sonra, `9` ve `3` işlem `SubtractNumbers` sonucu 6 ' da görüntülenir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Temsilciler](../../../../visual-basic/programming-guide/language-features/delegates/index.md)
- [AddressOf İşleci](../../../../visual-basic/language-reference/operators/addressof-operator.md)
- [Delegate Deyimi](../../../../visual-basic/language-reference/statements/delegate-statement.md)
- [Nasıl yapılır: Temsilci Yöntemi Çağırma](../../../../visual-basic/programming-guide/language-features/delegates/how-to-invoke-a-delegate-method.md)
