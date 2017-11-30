---
title: "Nasıl yapılır: İki Nesnenin Aynı Olup Olmadığını Belirleme (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- testing [Visual Basic], objects
- objects [Visual Basic], comparing
- object variables [Visual Basic], determining identity
ms.assetid: 7829f817-0d1f-4749-a707-de0b95e0cf5c
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 02083a93e63fe799f529776f777ca877d2d138b1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-determine-whether-two-objects-are-identical-visual-basic"></a>Nasıl yapılır: İki Nesnenin Aynı Olup Olmadığını Belirleme (Visual Basic)
İçinde [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)], her iki değişken aynı sınıfı örneğini bellekte noktası iki değişken başvuruları kendi işaretçileri, diğer bir deyişle, aynıysa aynı değerlendirilir. Örneğin, bir Windows Forms uygulamasında, belirlemek için bir karşılaştırma yapmak isteyebilirsiniz olup olmadığını geçerli örneğini (`Me`) belirli bir örneği ile aynı olduğu gibi `Form2`.  
  
 [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]iki işleç işaretçilerini karşılaştırmanızı sağlar. [Is işlecini](../../../../visual-basic/language-reference/operators/is-operator.md) döndürür `True` nesneleri özdeş ise ve [IsNot işleci](../../../../visual-basic/language-reference/operators/isnot-operator.md) döndürür `True` değillerse.  
  
## <a name="determining-if-two-objects-are-identical"></a>İki nesnenin aynı olup olmadığını belirleme  
  
#### <a name="to-determine-if-two-objects-are-identical"></a>İki nesnenin aynı olup olmadığını belirlemek için  
  
1.  Ayarlanmış bir `Boolean` iki nesne test etmek için ifade.  
  
2.  Sınama İfadenizde kullanmak `Is` işlenen olarak iki nesnenin işleç.  
  
     `Is`döndürür `True` nesneleri aynı sınıf örneğine noktası.  
  
## <a name="determining-if-two-objects-are-not-identical"></a>İki nesnenin aynı olup olmadığını belirleme  
 İki nesnenin aynı değilseniz ve birleştirmek garip olabilir bir eylem gerçekleştirmek istediğiniz bazen `Not` ve `Is`, örneğin `If Not obj1 Is obj2`. Böyle bir durumda kullandığınız `IsNot` işleci.  
  
#### <a name="to-determine-if-two-objects-are-not-identical"></a>İki nesnenin aynı olup olmadığını belirlemek için  
  
1.  Ayarlanmış bir `Boolean` iki nesne test etmek için ifade.  
  
2.  Sınama İfadenizde kullanmak `IsNot` işlenen olarak iki nesnenin işleç.  
  
     `IsNot`döndürür `True` nesneleri aynı sınıfı örneğini işaret etmiyorsa.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek çiftlerini testleri `Object` aynı sınıf örneğine noktası görmek için değişkenleri.  
  
 [!code-vb[VbVbalrKeywords#14](../../../../visual-basic/language-reference/codesnippet/VisualBasic/how-to-determine-whether-two-objects-are-identical_1.vb)]  
  
 Önceki örnekte, aşağıdaki çıkış görüntüler.  
  
 `objA different from objB? True`  
  
 `objA identical to objC? True`  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Nesne veri türü](../../../../visual-basic/language-reference/data-types/object-data-type.md)  
 [Nesne değişkenleri](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)  
 [Nesne değişkeni değerleri](../../../../visual-basic/programming-guide/language-features/variables/object-variable-values.md)  
 [Is işleci](../../../../visual-basic/language-reference/operators/is-operator.md)  
 [IsNot işleci](../../../../visual-basic/language-reference/operators/isnot-operator.md)  
 [Nasıl yapılır: iki nesnenin ilgili olup olmadığını belirleme](../../../../visual-basic/programming-guide/language-features/variables/how-to-determine-whether-two-objects-are-related.md)  
 [Me, My, MyBase ve MyClass](../../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)
