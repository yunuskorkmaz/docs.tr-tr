---
title: 'Nasıl yapılır: İki nesnenin aynı (Visual Basic) olup olmadığını belirleme'
ms.date: 07/20/2015
helpviewer_keywords:
- testing [Visual Basic], objects
- objects [Visual Basic], comparing
- object variables [Visual Basic], determining identity
ms.assetid: 7829f817-0d1f-4749-a707-de0b95e0cf5c
ms.openlocfilehash: aae053ae0473ed6ced0f28da3d5e5afc0be629df
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59295048"
---
# <a name="how-to-determine-whether-two-objects-are-identical-visual-basic"></a>Nasıl yapılır: İki nesnenin aynı (Visual Basic) olup olmadığını belirleme
Visual Basic'te, her iki değişken için aynı sınıf örneği bellekte gelirseniz iki değişken başvuruları kendi işaretçileri aynıysa, diğer bir deyişle, aynı kabul edilir. Örneğin, bir Windows Forms uygulamasında belirlemek için bir karşılaştırma yapmak isteyebileceğiniz olup olmadığını geçerli örneğini (`Me`) belirli bir örneği aynı olduğu gibi `Form2`.  
  
 Visual Basic işaretçileri karşılaştırmak için iki işleçleri sağlar. [İşleci olan](../../../../visual-basic/language-reference/operators/is-operator.md) döndürür `True` nesneleri aynıysa ve [IsNot işleci](../../../../visual-basic/language-reference/operators/isnot-operator.md) döndürür `True` yoksa.  
  
## <a name="determining-if-two-objects-are-identical"></a>İki nesnenin aynı olup olmadığını belirleme  
  
#### <a name="to-determine-if-two-objects-are-identical"></a>İki nesnenin aynı olup olmadığını belirlemek için  
  
1. Ayarlanmış bir `Boolean` iki nesne test etmek için ifade.  
  
2. Test ifadesinde kullanmak `Is` işlenen olarak iki nesne işleci.  
  
     `Is` döndürür `True` için aynı sınıf örneği nesnelerini noktası.  
  
## <a name="determining-if-two-objects-are-not-identical"></a>İki nesnenin aynı olup olmadığını belirleme  
 İki nesnenin aynı değildir ve birleştirmek garip olabilir bir eylem gerçekleştirmek istediğiniz bazen `Not` ve `Is`, örneğin `If Not obj1 Is obj2`. Böyle bir durumda kullanabileceğiniz `IsNot` işleci.  
  
#### <a name="to-determine-if-two-objects-are-not-identical"></a>İki nesnenin aynı olup olmadığını belirlemek için  
  
1. Ayarlanmış bir `Boolean` iki nesne test etmek için ifade.  
  
2. Test ifadesinde kullanmak `IsNot` işlenen olarak iki nesne işleci.  
  
     `IsNot` döndürür `True` nesneleri aynı sınıf örneğine işaret etmiyorsa.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek çiftlerini testleri `Object` aynı sınıf örneğine işaret görmek için değişkenleri.  
  
 [!code-vb[VbVbalrKeywords#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/class7.vb#14)]  
  
 Yukarıdaki örnek aşağıdaki çıkışı görüntüler.  
  
 `objA different from objB? True`  
  
 `objA identical to objC? True`  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Object Veri Türü](../../../../visual-basic/language-reference/data-types/object-data-type.md)
- [Nesne Değişkenleri](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)
- [Nesne Değişkeni Değerleri](../../../../visual-basic/programming-guide/language-features/variables/object-variable-values.md)
- [Is İşleci](../../../../visual-basic/language-reference/operators/is-operator.md)
- [IsNot İşleci](../../../../visual-basic/language-reference/operators/isnot-operator.md)
- [Nasıl yapılır: İki nesnenin ilgili olup olmadığını belirleme](../../../../visual-basic/programming-guide/language-features/variables/how-to-determine-whether-two-objects-are-related.md)
- [Me, My, MyBase ve MyClass](../../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)
