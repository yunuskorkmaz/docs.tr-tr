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
ms.openlocfilehash: 8f5dd6c56b3e4576b9d798e0e5e10b2996f558dc
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61864665"
---
# <a name="efficient-combination-of-operators-visual-basic"></a>İşleçlerin Etkili Bileşimi (Visual Basic)
Birçok farklı işleçleri karmaşık ifadeleri içerebilir. Aşağıdaki örnek bunu göstermektedir.  
  
 `x = (45 * (y + z)) ^ (2 / 85) * 5 + z`  
  
 Bir önceki örnekte gibi karmaşık ifadeler oluşturmak için işleç önceliği kurallarına Azure'un gerekir. Daha fazla bilgi için [Visual Basic'de İşleç önceliği](../../../../visual-basic/language-reference/operators/operator-precedence.md).  
  
## <a name="parenthetical-expressions"></a>Parantez içinde ifadeler  
 Çoğu zaman İşleç önceliği tarafından belirlenen olanlardan farklı bir düzende devam etmek için işlem ister. Aşağıdaki örnek göz önünde bulundurun.  
  
 `x = z * y + 4`  
  
 Yukarıdaki örnekte çarpar `z` tarafından `y`, ardından sonuca ekler `4`. Ancak eklemek istiyorsanız `y` ve `4` sonucu çarpmadan önce `z`, parantezler kullanarak normal İşleç önceliği geçersiz kılabilirsiniz. Bir ifadeyi parantez içine alarak, ilk olarak, İşleç önceliği bağımsız olarak değerlendirilecek ifade zorlar. Ayrıca ilk yapmak için önceki örnekte zorlamak için aşağıdaki örnekte olduğu gibi yeniden yazabilirsiniz.  
  
 `x = z * (y + 4)`  
  
 Yukarıdaki örnekte ekler `y` ve `4`, ardından toplamı ile çarpar `z`.  
  
### <a name="nested-parenthetical-expressions"></a>Parantez içinde iç içe geçmiş ifadeler  
 Daha da önceliği geçersiz kılmak için parantez, birden çok düzeyi ifadelerini iç içe yerleştirebilirsiniz. Parantez içine en derin yuvalanmış ifadeleri en, vb. az derin şekilde iç içe geçmiş ve son olarak parantez dışında ifadeleri iç içe girmiş sonraki ardından ilk olarak değerlendirilir. Aşağıdaki örnek bunu göstermektedir.  
  
 `x = (z * 4) ^ (y * (z + 2))`  
  
 Önceki örnekte `z + 2` değerlendirilen ilk sonra parantez içinde bir ifade. Diğer ifadeler ayraç içindeki çünkü normalde toplama veya çarpma daha yüksek bir önceliğe sahiptir, üs olarak gösterme Bu örnekte son değerlendirilir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Visual Basic'de aritmetik işleçler](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
- [Visual Basic'de Karşılaştırma işleçleri](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)
- [Visual Basic'de mantıksal ve bit düzeyinde işleçler](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
- [Mantıksal/bit düzeyinde işleçler (Visual Basic)](../../../../visual-basic/language-reference/operators/logical-bitwise-operators.md)
- [Boole İfadeleri](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/boolean-expressions.md)
- [Değer Karşılaştırmaları](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/value-comparisons.md)
- [Nasıl yapılır: Sayısal değerleri hesaplama](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/how-to-calculate-numeric-values.md)
- [Visual Basic'de İşleç önceliği](../../../../visual-basic/language-reference/operators/operator-precedence.md)
