---
title: 'Nasıl yapılır: İki Nesnenin Aynı Olup Olmadığını Belirleme'
ms.date: 07/20/2015
helpviewer_keywords:
- testing [Visual Basic], objects
- objects [Visual Basic], comparing
- object variables [Visual Basic], determining identity
ms.assetid: 7829f817-0d1f-4749-a707-de0b95e0cf5c
ms.openlocfilehash: 5deebd4ffc5b277c94f5ae36c00fd6e5010a1551
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74348605"
---
# <a name="how-to-determine-whether-two-objects-are-identical-visual-basic"></a>Nasıl yapılır: İki Nesnenin Aynı Olup Olmadığını Belirleme (Visual Basic)
Visual Basic, işaretçilerin aynısı varsa, iki değişken başvurusu özdeş kabul edilir, yani her iki değişken de bellekteki aynı sınıf örneğini işaret ediyor. Örneğin, Windows Forms bir uygulamada, geçerli örneğin (`Me`) `Form2`gibi belirli bir örnekle aynı olup olmadığını belirlemede bir karşılaştırma yapmak isteyebilirsiniz.  
  
 Visual Basic işaretçileri karşılaştırmak için iki işleç sağlar. İf [işleci](../../../../visual-basic/language-reference/operators/is-operator.md) , nesneler aynıysa `True` döndürür ve [ınot işleci](../../../../visual-basic/language-reference/operators/isnot-operator.md) yoksa `True` döndürür.  
  
## <a name="determining-if-two-objects-are-identical"></a>Iki nesnenin aynı olup olmadığını belirleme  
  
#### <a name="to-determine-if-two-objects-are-identical"></a>İki nesnenin aynı olup olmadığını belirleme  
  
1. İki nesneyi test etmek için bir `Boolean` ifadesi ayarlayın.  
  
2. Test ifadenizde, iki nesne işlenen olarak `Is` işlecini kullanın.  
  
     `Is`, nesneler aynı sınıf örneğine işaret ettikten sonra `True` döndürür.  
  
## <a name="determining-if-two-objects-are-not-identical"></a>Iki nesnenin aynı olup olmadığını belirleme  
 Bazen iki nesne özdeş değilse bir eylem gerçekleştirmek istiyor ve bu, örneğin `If Not obj1 Is obj2``Not` ve `Is`birleştirmek için de kullanılabilir. Böyle bir durumda `IsNot` işlecini kullanabilirsiniz.  
  
#### <a name="to-determine-if-two-objects-are-not-identical"></a>İki nesnenin aynı olup olmadığını belirleme  
  
1. İki nesneyi test etmek için bir `Boolean` ifadesi ayarlayın.  
  
2. Test ifadenizde, iki nesne işlenen olarak `IsNot` işlecini kullanın.  
  
     nesneler aynı sınıf örneğini işaret etmez `IsNot` `True` döndürür.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, aynı sınıf örneğine işaret edip ettikleri görmek için `Object` değişkenlerinin çiftlerini sınar.  
  
 [!code-vb[VbVbalrKeywords#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/class7.vb#14)]  
  
 Yukarıdaki örnek aşağıdaki çıktıyı görüntüler.  
  
 `objA different from objB? True`  
  
 `objA identical to objC? True`  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Object Veri Türü](../../../../visual-basic/language-reference/data-types/object-data-type.md)
- [Nesne Değişkenleri](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)
- [Nesne Değişkeni Değerleri](../../../../visual-basic/programming-guide/language-features/variables/object-variable-values.md)
- [Is İşleci](../../../../visual-basic/language-reference/operators/is-operator.md)
- [IsNot İşleci](../../../../visual-basic/language-reference/operators/isnot-operator.md)
- [Nasıl yapılır: İki Nesnenin İlgili Olup Olmadığını Belirleme](../../../../visual-basic/programming-guide/language-features/variables/how-to-determine-whether-two-objects-are-related.md)
- [Me, My, MyBase ve MyClass](../../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)
