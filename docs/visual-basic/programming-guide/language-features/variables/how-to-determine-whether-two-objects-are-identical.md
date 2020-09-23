---
title: 'Nasıl yapılır: İki Nesnenin Aynı Olup Olmadığını Belirleme'
ms.date: 07/20/2015
helpviewer_keywords:
- testing [Visual Basic], objects
- objects [Visual Basic], comparing
- object variables [Visual Basic], determining identity
ms.assetid: 7829f817-0d1f-4749-a707-de0b95e0cf5c
ms.openlocfilehash: 1bbc8083fcfb6f5ff0f4328c32b83a2e7218ecd6
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91072281"
---
# <a name="how-to-determine-whether-two-objects-are-identical-visual-basic"></a>Nasıl yapılır: İki Nesnenin Aynı Olup Olmadığını Belirleme (Visual Basic)

Visual Basic, işaretçilerin aynısı varsa, iki değişken başvurusu özdeş kabul edilir, yani her iki değişken de bellekteki aynı sınıf örneğini işaret ediyor. Örneğin, Windows Forms bir uygulamada, geçerli örneğin ( `Me` ) belirli bir örnekle aynı olup olmadığını (gibi) belirlemede bir karşılaştırma yapmak isteyebilirsiniz `Form2` .  
  
 Visual Basic işaretçileri karşılaştırmak için iki işleç sağlar. [,](../../../language-reference/operators/is-operator.md) `True` Nesneleri özdeş Ise ve [ınot işleci](../../../language-reference/operators/isnot-operator.md) değilse, işleç döndürür `True` .  
  
## <a name="determining-if-two-objects-are-identical"></a>Iki nesnenin aynı olup olmadığını belirleme  
  
#### <a name="to-determine-if-two-objects-are-identical"></a>İki nesnenin aynı olup olmadığını belirleme  
  
1. `Boolean`İki nesneyi test etmek için bir ifade ayarlayın.  
  
2. Test ifadesiyse `Is` işleci iki nesne ile işlenen olarak kullanın.  
  
     `Is``True`nesneler aynı sınıf örneğine işaret ettikten sonra döndürür.  
  
## <a name="determining-if-two-objects-are-not-identical"></a>Iki nesnenin aynı olup olmadığını belirleme  

 Bazen iki nesne özdeş değilse bir eylem gerçekleştirmek istersiniz ve bu, örneğin, birleştirmek için de olabilir `Not` `Is` `If Not obj1 Is obj2` . Böyle bir durumda, `IsNot` işlecini kullanabilirsiniz.  
  
#### <a name="to-determine-if-two-objects-are-not-identical"></a>İki nesnenin aynı olup olmadığını belirleme  
  
1. `Boolean`İki nesneyi test etmek için bir ifade ayarlayın.  
  
2. Test ifadesiyse `IsNot` işleci iki nesne ile işlenen olarak kullanın.  
  
     `IsNot``True`nesnelerin aynı sınıf örneğini işaret edip etmez döndürür.  
  
## <a name="example"></a>Örnek  

 Aşağıdaki örnek, `Object` aynı sınıf örneğine işaret edip ettikleri anlamak için değişken çiftlerini sınar.  
  
 [!code-vb[VbVbalrKeywords#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/class7.vb#14)]  
  
 Yukarıdaki örnek aşağıdaki çıktıyı görüntüler.  
  
 `objA different from objB? True`  
  
 `objA identical to objC? True`  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Nesne Veri Türü](../../../language-reference/data-types/object-data-type.md)
- [Nesne Değişkenleri](object-variables.md)
- [Nesne Değişkeni Değerleri](object-variable-values.md)
- [Is İşleci](../../../language-reference/operators/is-operator.md)
- [IsNot İşleci](../../../language-reference/operators/isnot-operator.md)
- [Nasıl yapılır: İki Nesnenin İlgili Olup Olmadığını Belirleme](how-to-determine-whether-two-objects-are-related.md)
- [Me, My, MyBase ve MyClass](../../program-structure/me-my-mybase-and-myclass.md)
