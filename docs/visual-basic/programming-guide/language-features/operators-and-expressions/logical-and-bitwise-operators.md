---
title: Visual Basic'de Mantıksal ve Bit Düzeyinde İşleçler
ms.date: 07/20/2015
helpviewer_keywords:
- short-circuiting
- Boolean expressions
- logical operators [Visual Basic], Boolean expressions
- operators [Visual Basic], logical
- AndAlso operator [Visual Basic]
- Not operator [Visual Basic], Boolean expressions
- Xor operator [Visual Basic], Boolean expressions
- And operator [Visual Basic], logical operators
- logical operators [Visual Basic]
- expressions [Visual Basic], Boolean
- Or operator [Visual Basic], logical operators
- Visual Basic code, operators
- short-circuiting [Visual Basic], logical operators
- logical operators [Visual Basic], short-circuiting
- Visual Basic code, expressions
- logical operators [Visual Basic], binary
- OrElse operator [Visual Basic]
- logical operators [Visual Basic], unary
ms.assetid: ca474e13-567d-4b1d-a18b-301433705e57
ms.openlocfilehash: 371d28629b39fb2808ca018ea69da3306a31f50c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="logical-and-bitwise-operators-in-visual-basic"></a>Visual Basic'de Mantıksal ve Bit Düzeyinde İşleçler
Mantıksal işleçler karşılaştırmak `Boolean` ifadeleri ve return bir `Boolean` sonucu. `And`, `Or`, `AndAlso`, `OrElse`, Ve `Xor` işleçler *ikili* iki işlenen alır çünkü while `Not` işlecidir *birli* tek bir işlenen aldığından. Bu işleçlere bazıları tam sayı değerleri üzerinde bit tabanlı mantıksal işlemlerini de gerçekleştirebilirsiniz.  
  
## <a name="unary-logical-operator"></a>Birli mantıksal işleç  
 [Not işleci](../../../../visual-basic/language-reference/operators/not-operator.md) mantıksal gerçekleştirir *değilleme* üzerinde bir `Boolean` ifade. Kendi işleneni mantıksal karşıtı verir. İfade değerlendirilirse `True`, ardından `Not` döndürür `False`; ifade değerlendirilirse `False`, ardından `Not` döndürür `True`. Aşağıdaki örnek bunu göstermektedir.  
  
 [!code-vb[VbVbalrOperators#77](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/logical-and-bitwise-operators_1.vb)]  
  
## <a name="binary-logical-operators"></a>İkili mantıksal işleçler  
 [Ve işleç](../../../../visual-basic/language-reference/operators/and-operator.md) mantıksal gerçekleştirir *birlikte* iki üzerinde `Boolean` ifadeler. İçin her iki ifade değerlendirin varsa `True`, ardından `And` döndürür `True`. En az bir ifadenin değerlendirilirse `False`, ardından `And` döndürür `False`.  
  
 [Veya işleci](../../../../visual-basic/language-reference/operators/or-operator.md) mantıksal gerçekleştirir *ayrım* veya *ekleme* iki üzerinde `Boolean` ifadeler. Ya da ifade değerlendirilirse `True`, veya her ikisi için değerlendirin `True`, ardından `Or` döndürür `True`. Hiçbiri ifade değerlendirilirse `True`, `Or` döndürür `False`.  
  
 [Xor işleci](../../../../visual-basic/language-reference/operators/xor-operator.md) mantıksal gerçekleştirir *dışlama* iki üzerinde `Boolean` ifadeler. Tam olarak bir ifade değerlendirilirse `True`, ancak ikisini, `Xor` döndürür `True`. İçin her iki ifade değerlendirin varsa `True` veya her ikisi için değerlendirin `False`, `Xor` döndürür `False`.  
  
 Aşağıdaki örnek gösterilmektedir `And`, `Or`, ve `Xor` işleçler.  
  
 [!code-vb[VbVbalrOperators#78](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/logical-and-bitwise-operators_2.vb)]  
  
## <a name="short-circuiting-logical-operations"></a>Kısa devre mantıksal işlemleri  
 [AndAlso işleci](../../../../visual-basic/language-reference/operators/andalso-operator.md) çok benzer `And` işleci, ayrıca mantıksal ve işlecini iki gerçekleştirir, `Boolean` ifadeler. İkisi arasındaki temel fark `AndAlso` sergiler *kısa devre* davranışı. İlk ifadesinde bir `AndAlso` ifadeyi hesaplar için `False`, sonra da nihai sonucu değiştirilemiyor çünkü ikinci ifade değerlendirilmez ve `AndAlso` döndürür `False`.  
  
 Benzer şekilde, [OrElse işleci](../../../../visual-basic/language-reference/operators/orelse-operator.md) kısa devre mantıksal veya işlecini iki gerçekleştirir `Boolean` ifadeler. İlk ifadesinde bir `OrElse` ifadeyi hesaplar için `True`, sonra da nihai sonucu değiştirilemiyor çünkü ikinci ifade değerlendirilmez ve `OrElse` döndürür `True`.  
  
### <a name="short-circuiting-trade-offs"></a>Dengelemeler kısa devre  
 Kısa devre mantıksal işleminin sonucu değiştirilemiyor bir ifade değerlendirerek değil performansını iyileştirebilir. Ancak, bu deyim ek eylemler gerçekleştiriyorsa, bu eylemleri bir kısa devre atlar. İfade için bir çağrı içeriyorsa, örneğin, bir `Function` yordamı, yordam ifade kısa devre yapılma ise ve herhangi bir ek kod bulunan çağrılmaz `Function` çalışmaz. Bu nedenle, işlevi yalnızca bazı durumlarda çalışabilir ve doğru bir şekilde test edilmelidir değil. Veya program mantığı kodda bağlı `Function`.  
  
 Aşağıdaki örnek arasındaki fark gösterilmektedir `And`, `Or`ve short-circuiting'dekiler.  
  
 [!code-vb[VbVbalrOperators#81](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/logical-and-bitwise-operators_3.vb)]  
  
 [!code-vb[VbVbalrOperators#80](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/logical-and-bitwise-operators_4.vb)]  
  
 [!code-vb[VbVbalrOperators#79](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/logical-and-bitwise-operators_5.vb)]  
  
 Önceki örnekte unutmayın bazı önemli kod içinde `checkIfValid()` çağrı kısa devre yapılma olduğunda çalışmaz. İlk `If` deyimi çağrıları `checkIfValid()` olsa bile `12 > 45` döndürür `False`, çünkü `And` değil kısa devre oluşturur. İkinci `If` deyimi çağırmaz `checkIfValid()`, çünkü zaman `12 > 45` döndürür `False`, `AndAlso` ikinci ifade short-circuits. Üçüncü `If` deyimi çağrıları `checkIfValid()` olsa bile `12 < 45` döndürür `True`, çünkü `Or` değil kısa devre oluşturur. Dördüncü `If` deyimi çağırmaz `checkIfValid()`, çünkü zaman `12 < 45` döndürür `True`, `OrElse` ikinci ifade short-circuits.  
  
## <a name="bitwise-operations"></a>Bit düzeyinde işlemler  
 Bit düzeyinde işlemler ikili (2 tabanı) formunda iki tamsayı değerleri değerlendirin. Bunlar, karşılık gelen konumlarda BITS karşılaştırın ve karşılaştırma üzerine dayalı değerler atayın. Aşağıdaki örnek gösterilmektedir `And` işleci.  
  
 [!code-vb[VbVbalrConcepts#2](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/codesnippet/VisualBasic/logical-and-bitwise-operators_6.vb)]  
  
 Önceki örnekte değerini ayarlar `x` 1. Bu şu nedenlerden dolayı gerçekleşir:  
  
-   Değerleri, binary olarak kabul edilir:  
  
     ikili biçimde 3 011 =  
  
     ikili biçimde 5 101 =  
  
-   `And` İşleci ikili temsili bir ikili konum (bit) aynı anda karşılaştırır. Verilen konumda bitlerin her ikisi de 1 ise, 1, bu konumda sonucu yerleştirilir. Her iki bit 0 ise, 0, bu konumda sonucu yerleştirilir. Önceki örnekte bu gibi üretir:  
  
     011 (3 ikili biçimde)  
  
     101 (5 ikili biçimde)  
  
     001 (ikili formunda, sonuç)  
  
-   Sonuç ondalık olarak kabul edilir. Değerin 001 ikili 1, bu nedenle gösterimidir `x` = 1.  
  
 Bit düzeyinde `Or` işlem olduğunu benzer, birini veya ikisini karşılaştırılan BITS 1 ise 1 sonuç bit atanan dışında. `Xor` Karşılaştırılan BITS (ikisini) tam olarak birine 1 ise 1 sonuç bit atar. `Not` tek bir işlenen alır ve oturum bit dahil olmak üzere tüm BITS tersine çevirir ve bu değeri sonuca atar. Bu için pozitif sayılar imzalı anlamına gelir `Not` her zaman negatif bir değer döndürür ve negatif sayıları için `Not` her zaman bir pozitif veya sıfır değerini döndürür.  
  
 `AndAlso` Ve `OrElse` işleçler bit düzeyinde işlemler desteklemez.  
  
> [!NOTE]
>  Bit düzeyinde işlemler yalnızca tam sayı türleri üzerinde gerçekleştirilebilir. Bit düzeyinde işlemi devam etmeden önce kayan nokta değerlerine tam sayı türleri dönüştürülmesi gerekir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Mantıksal ve bit düzeyinde işleçler (Visual Basic)](../../../../visual-basic/language-reference/operators/logical-bitwise-operators.md)  
 [Boole İfadeleri](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/boolean-expressions.md)  
 [Visual Basic'de aritmetik işleçler](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)  
 [Visual Basic'de Karşılaştırma işleçleri](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)  
 [Visual Basic'de birleştirme işleçleri](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/concatenation-operators.md)  
 [İşleçlerin Etkili Bileşimi](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/efficient-combination-of-operators.md)
