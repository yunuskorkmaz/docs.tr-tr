---
title: "İşleçlerin Etkili Bileşimi (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- expressions [Visual Basic], parentheses
- operators [Visual Basic], associativity
- expressions [Visual Basic], operators
- operators [Visual Basic], precedence
- Visual Basic code, operators
- Visual Basic code, expressions
- operators [Visual Basic], complex expressions
- expressions [Visual Basic], complex
- parentheses [Visual Basic], complex expressions
- numeric expressions
ms.assetid: bd22340e-b5be-458b-8772-3916c02309a4
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 4b0f1d637bc1757515cf271a8c70d62effab0843
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="efficient-combination-of-operators-visual-basic"></a>İşleçlerin Etkili Bileşimi (Visual Basic)
Karmaşık ifadeler birçok farklı işleçleri içerebilir. Aşağıdaki örnek bunu göstermektedir.  
  
 `x = (45 * (y + z)) ^ (2 / 85) * 5 + z`  
  
 Bir önceki örnekte gibi karmaşık ifadeler oluşturma İşleç önceliği kuralları kapsamlı olarak anlamayı gerektirir. Daha fazla bilgi için bkz: [Visual Basic'de İşleç önceliği](../../../../visual-basic/language-reference/operators/operator-precedence.md).  
  
## <a name="parenthetical-expressions"></a>Parantez içinde ifadeler  
 Genellikle operations İşleç önceliği tarafından belirlenen ile farklı sırada devam etmek istiyorsunuz. Aşağıdaki örnek göz önünde bulundurun.  
  
 `x = z * y + 4`  
  
 Önceki örnekte çarpar `z` tarafından `y`, sonuca ekler `4`. Ancak eklemek istiyorsanız `y` ve `4` sonucu çarparak önce `z`, parantez kullanarak normal İşleç önceliği geçersiz kılabilirsiniz. Bir ifade parantez içinde kapsayan tarafından ilk olarak, İşleç önceliği bağımsız olarak değerlendirilecek ifade zorlar. Ayrıca ilk yapmak için önceki örnekte zorlamak için aşağıdaki örnekte olduğu gibi yeniden yazabilirsiniz.  
  
 `x = z * (y + 4)`  
  
 Önceki örnekte ekler `y` ve `4`, toplamı tarafından çarpar `z`.  
  
### <a name="nested-parenthetical-expressions"></a>İç içe geçmiş parantez içinde ifadeler  
 Parantez daha önceliği geçersiz kılmak için birden çok düzeyi ifadelerinde yerleştirebilirsiniz. En fazla parantez içinde iç içe ifadeler, ilk olarak, en fazla, vb. az iç içe ve son olarak parantez dışında ifadeleri iç içe sonraki arkasından değerlendirilir. Aşağıdaki örnek bunu göstermektedir.  
  
 `x = (z * 4) ^ (y * (z + 2))`  
  
 Önceki örnekte `z + 2` değerlendirilen ilk sonra parantez içinde bir ifade değil. Diğer ifadeler parantez içine alınmış olduğundan normalde toplama veya çarpma daha yüksek önceliğe sahiptir, üs son Bu örnekte değerlendirilir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Visual Basic'de aritmetik işleçler](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)  
 [Visual Basic'de Karşılaştırma işleçleri](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)  
 [Visual Basic'de mantıksal ve bit düzeyinde işleçler](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)  
 [Mantıksal ve bit düzeyinde işleçler (Visual Basic)](../../../../visual-basic/language-reference/operators/logical-bitwise-operators.md)  
 [Boole ifadeleri](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/boolean-expressions.md)  
 [Değer karşılaştırmaları](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/value-comparisons.md)  
 [Nasıl yapılır: sayısal değerleri hesaplama](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/how-to-calculate-numeric-values.md)  
 [Visual Basic'de İşleç önceliği](../../../../visual-basic/language-reference/operators/operator-precedence.md)
