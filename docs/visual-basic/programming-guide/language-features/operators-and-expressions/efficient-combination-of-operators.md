---
title: İşleçlerin Etkili Bileşimi (Visual Basic)
ms.date: 07/20/2015
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
ms.openlocfilehash: 8ced464cb0cc8e1bec3c3449dccb827575599905
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33648924"
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
 [Boole İfadeleri](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/boolean-expressions.md)  
 [Değer Karşılaştırmaları](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/value-comparisons.md)  
 [Nasıl yapılır: Sayısal Değerleri Hesaplama](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/how-to-calculate-numeric-values.md)  
 [Visual Basic'de İşleç önceliği](../../../../visual-basic/language-reference/operators/operator-precedence.md)
