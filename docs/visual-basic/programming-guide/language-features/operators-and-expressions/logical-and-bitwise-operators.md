---
title: Mantıksal ve Bit Düzeyinde İşleçler
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
ms.openlocfilehash: 55a246c0d56501a409ebbc7d0d0aa39ae9fa1770
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74343600"
---
# <a name="logical-and-bitwise-operators-in-visual-basic"></a>Visual Basic'de Mantıksal ve Bit Düzeyinde İşleçler
Mantıksal işleçler `Boolean` ifadelerini karşılaştırır ve `Boolean` sonucunu döndürür. `And`, `Or`, `AndAlso`, `OrElse`ve `Xor` işleçleri *ikili bir dosya* olsa da, tek bir işlenen aldığı için `Not` işleci *birli* olur. Bu işleçlerden bazıları, tam sayı değerlerinde bit düzeyinde mantıksal işlemler de gerçekleştirebilir.  
  
## <a name="unary-logical-operator"></a>Birli mantıksal Işleç  
 [Not işleci](../../../../visual-basic/language-reference/operators/not-operator.md) `Boolean` ifadesinde mantıksal *değilleme* gerçekleştirir. İşleneni, işleneninin mantıksal tersini verir. İfade `True`olarak değerlendirilirse `Not` `False`döndürür; ifade `False`olarak değerlendirilirse `Not` `True`döndürür. Aşağıdaki örnek bunu göstermektedir.  
  
 [!code-vb[VbVbalrOperators#77](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#77)]  
  
## <a name="binary-logical-operators"></a>İkili mantıksal Işleçler  
 [And işleci](../../../../visual-basic/language-reference/operators/and-operator.md) iki `Boolean` ifadelerinde mantıksal bir *birlikte* gerçekleştirir. Her iki ifade de `True`olarak değerlendirilir `And` `True`döndürür. Deyimlerden en az biri `False`değerlendirilirse `And` `False`döndürür.  
  
 [OR işleci](../../../../visual-basic/language-reference/operators/or-operator.md) , mantıksal *ayırıcı* veya iki `Boolean` ifadeye *dahil* etme işlemini gerçekleştirir. Her iki ifade de `True`olarak değerlendirilir veya `True`her ikisi de `Or` `True`döndürür. Hiçbir ifadenin `True`olarak değerlendiriliyorsa `Or` `False`döndürür.  
  
 [Xor işleci](../../../../visual-basic/language-reference/operators/xor-operator.md) iki `Boolean` ifadelerinde mantıksal *dışlama* gerçekleştirir. Tam olarak bir ifade `True`olarak değerlendirilir, ancak her ikisini birden değil `Xor` `True`döndürür. Her iki ifade de `True` veya her ikisi de `False`olarak değerlendirilir `Xor` `False`döndürür.  
  
 Aşağıdaki örnekte `And`, `Or`ve `Xor` işleçleri gösterilmektedir.  
  
 [!code-vb[VbVbalrOperators#78](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#78)]  
  
## <a name="short-circuiting-logical-operations"></a>Kısa devre mantıksal Işlemler yürütülüyor  
 [AndAlso işleci](../../../../visual-basic/language-reference/operators/andalso-operator.md) `And` işlecine çok benzer ve ayrıca iki `Boolean` ifadesi üzerinde mantıksal bir işlem gerçekleştirir. İkisi arasındaki temel fark, `AndAlso` *kısa* devre davranýþý davranışını gösteriyor. `AndAlso` ifadesindeki ilk ifade `False`olarak değerlendirilirse, ikinci ifade, nihai sonucu değiştirmediği ve `AndAlso` `False`döndürdüğü için değerlendirilmez.  
  
 Benzer şekilde, [OrElse işleci](../../../../visual-basic/language-reference/operators/orelse-operator.md) iki `Boolean` ifadeye kısa devre uygulayan mantıksal bir birleşim gerçekleştirir. `OrElse` ifadesindeki ilk ifade `True`olarak değerlendirilirse, ikinci ifade, nihai sonucu değiştirmediği ve `OrElse` `True`döndürdüğü için değerlendirilmez.  
  
### <a name="short-circuiting-trade-offs"></a>Kısa süreli bir denge  
 Kısa devre uygulayan, mantıksal işlemin sonucunu değiştirebilecek bir ifadeyi değerlendirmeden performansı iyileştirebilir. Ancak, bu ifade ek eylemler gerçekleştirdiğinde, kısa devre uygulayan bu eylemleri atlar. Örneğin, ifade bir `Function` yordamına çağrı içeriyorsa, ifade kısa devre dışı ise ve `Function` dahil olan ek kodlar çalıştırılmadığından Bu yordam çağrılmaz. Bu nedenle, işlev yalnızca belirli bir zaman çalışabilir ve doğru şekilde sınanmayabilir. Ya da program mantığı `Function`koda bağlı olarak değişebilir.  
  
 Aşağıdaki örnek, `And`, `Or`ve bunların kısa devre dışı karşılıkları arasındaki farkı gösterir.  
  
 [!code-vb[VbVbalrOperators#81](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#81)]  
  
 [!code-vb[VbVbalrOperators#80](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#80)]  
  
 [!code-vb[VbVbalrOperators#79](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#79)]  
  
 Yukarıdaki örnekte, çağrı kısa devre dışı olduğunda `checkIfValid()` içindeki bazı önemli kodun çalıştırılmadığını unutmayın. İlk `If` ifade, `And` kısa devre olmadığından `12 > 45` `False`döndürse bile `checkIfValid()` çağırır. İkinci `If` deyimi `checkIfValid()`çağırmaz; çünkü `12 > 45` `False`döndürdüğünde, `AndAlso` kısa devreler ikinci ifadedir. `Or` kısa devre olmadığından, üçüncü `If` ifade `12 < 45` `True`döndürse bile `checkIfValid()` çağırır. Dördüncü `If` deyimi, `12 < 45` `True`döndürdüğünde, `OrElse` kısa devreden ikinci ifadeye `checkIfValid()`çağırmaz.  
  
## <a name="bitwise-operations"></a>Bit düzeyinde Işlemler  
 Bit düzeyinde işlemler ikili (taban 2) formda iki integral değeri değerlendirir. Bunlara karşılık gelen konumlarda bitleri karşılaştırırlar ve sonra karşılaştırmaya göre değerler atar. Aşağıdaki örnekte `And` işleci gösterilmektedir.  
  
 [!code-vb[VbVbalrConcepts#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrConcepts/VB/Class1.vb#2)]  
  
 Yukarıdaki örnek `x` değerini 1 olarak ayarlar. Bu durum aşağıdaki nedenlerden dolayı gerçekleşir:  
  
- Değerler ikili olarak değerlendirilir:  
  
     3 ikili biçiminde 3 = 011  
  
     5 ikili biçimi = 101  
  
- `And` işleci, tek seferde bir ikili konum (bit) ikili gösterimlerini karşılaştırır. Belirli bir konumdaki bitlerin her ikisi de 1 ise, sonuçta bu konuma bir 1 konur. Her iki bit de 0 ise, sonuçta bu konuma 0 yerleştirilir. Yukarıdaki örnekte bu, aşağıdaki gibi çalışmaktadır:  
  
     011 (ikili biçimde 3)  
  
     101 (ikili biçimde 5)  
  
     001 (sonuç, ikili biçimde)  
  
- Sonuç ondalık olarak değerlendirilir. 001 değeri 1 ' in ikili gösterimidir, bu nedenle `x` = 1 ' dir.  
  
 Bit düzeyinde `Or` işlem benzerdir, ancak karşılaştırılan bitlerin biri veya her ikisi 1 ise sonuç bitine 1 atanır. `Xor`, karşılaştırılan bitlerin (her ikisi de değil) tam olarak biri 1 olduğunda sonuç bitini 1 atar. `Not` tek bir işlenen alır ve işaret biti dahil olmak üzere tüm bitleri ters çevirir ve bu değeri sonuca atar. Bu, `Not` her zaman negatif bir değer döndüren ve negatif sayılar için `Not` her zaman pozitif veya sıfır değeri döndüren anlamına gelir.  
  
 `AndAlso` ve `OrElse` işleçleri bit düzeyinde işlemleri desteklemez.  
  
> [!NOTE]
> Bit düzeyinde işlemler yalnızca integral türlerinde gerçekleştirilebilir. Bit düzeyinde işlemin devam edebilmesi için kayan nokta değerlerinin tamsayı türlerine dönüştürülmesi gerekir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Mantıksal/bit düzeyinde Işleçler (Visual Basic)](../../../../visual-basic/language-reference/operators/logical-bitwise-operators.md)
- [Boole İfadeleri](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/boolean-expressions.md)
- [Visual Basic aritmetik Işleçler](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
- [Visual Basic karşılaştırma Işleçleri](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)
- [Visual Basic birleştirme Işleçleri](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/concatenation-operators.md)
- [İşleçlerin Etkili Bileşimi](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/efficient-combination-of-operators.md)
