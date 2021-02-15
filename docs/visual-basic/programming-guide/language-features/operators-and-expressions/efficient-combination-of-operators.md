---
description: 'Hakkında daha fazla bilgi edinin: etkin Işleçler birleşimi (Visual Basic)'
title: İşleçlerin Etkili Bileşimi
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
ms.openlocfilehash: a4d2d0c1caeea95dd8d34b2033a398d26bcf63ef
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100476273"
---
# <a name="efficient-combination-of-operators-visual-basic"></a>İşleçlerin Etkili Bileşimi (Visual Basic)

Karmaşık ifadelerde birçok farklı işleç bulunabilir. Aşağıdaki örnek bunu göstermektedir.  
  
 `x = (45 * (y + z)) ^ (2 / 85) * 5 + z`  
  
 Önceki örnekteki gibi karmaşık ifadelerin oluşturulması, işleç önceliği kurallarının eksiksiz bir şekilde anlaşılmasına gerek duyar. Daha fazla bilgi için [Visual Basic operatör önceliği](../../../language-reference/operators/operator-precedence.md)bölümüne bakın.  
  
## <a name="parenthetical-expressions"></a>Parantez içinde Ifadeler  

 Genellikle işlemlerin operatör önceliğine göre belirlenen şekilde farklı bir sırada devam etmesini istiyorsunuz. Aşağıdaki örneği inceleyin.  
  
 `x = z * y + 4`  
  
 Önceki örnek ile çarpar `z` `y` , sonra sonucunu öğesine ekler `4` . Ancak `y` `4` , sonucu çarpmadan önce eklemek istiyorsanız `z` , parantez kullanarak normal operatör önceliğini geçersiz kılabilirsiniz. Bir ifadeyi parantez içine alarak, işleç önceliği ne olursa olsun, bu ifadenin ilk olarak değerlendirilmesini zorlarsınız. Önceki örneği öncelikle eklemeyi zorlamak için, aşağıdaki örnekte olduğu gibi yeniden yazabilirsiniz.  
  
 `x = z * (y + 4)`  
  
 Yukarıdaki örnek, `y` ve `4` sonra bu toplamı ile çarpar `z` .  
  
### <a name="nested-parenthetical-expressions"></a>İç içe geçmiş parantez Ifadeleri  

 Daha da fazla öncelik vermek için ifadeleri birden çok parantez düzeyinde iç içe yerleştirebilirsiniz. Parantez içinde en derin iç içe yerleştirilmiş ifadeler önce değerlendirilir, ardından sonraki en derin iç içe geçmiş ve bu, en az derin iç içe, son olarak da parantez dışında ifadeler. Aşağıdaki örnek bunu göstermektedir.  
  
 `x = (z * 4) ^ (y * (z + 2))`  
  
 Önceki örnekte, `z + 2` önce değerlendirilir, sonra diğer parantez içinde ifadeler. Normalde ekleme veya çarpmayla daha yüksek önceliğe sahip olan üs, bu örnekte en son değerlendirilir çünkü diğer ifadeler parantez içine alınmıştır.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Visual Basic'de Aritmetik İşleçler](arithmetic-operators.md)
- [Visual Basic'de Karşılaştırma İşleçleri](comparison-operators.md)
- [Visual Basic'de Mantıksal ve Bit Düzeyinde İşleçler](logical-and-bitwise-operators.md)
- [Mantıksal/Bit Düzeyinde İşleçler (Visual Basic)](../../../language-reference/operators/logical-bitwise-operators.md)
- [Boole Ifadeleri](boolean-expressions.md)
- [Değer Karşılaştırmaları](value-comparisons.md)
- [Nasıl yapılır: Sayısal Değerleri Hesaplama](how-to-calculate-numeric-values.md)
- [Visual Basic'de İşleç Önceliği](../../../language-reference/operators/operator-precedence.md)
