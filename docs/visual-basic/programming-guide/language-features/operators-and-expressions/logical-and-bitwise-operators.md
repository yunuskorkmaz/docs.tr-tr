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
ms.openlocfilehash: 40076b2ad6606b4c565bcd39dbeea9e55da47211
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69963311"
---
# <a name="logical-and-bitwise-operators-in-visual-basic"></a>Visual Basic'de Mantıksal ve Bit Düzeyinde İşleçler
Mantıksal işleçler ifadeleri `Boolean` karşılaştırır ve bir `Boolean` sonuç döndürür. `And` ,`OrElse` ,,`Not` Ve işleçleri iki işlenen kullandığından, tek bir işlenen aldığı için işleç tekil olduğu için ikili bir dosyaysa. `Xor` `Or` `AndAlso` Bu işleçlerden bazıları, tam sayı değerlerinde bit düzeyinde mantıksal işlemler de gerçekleştirebilir.  
  
## <a name="unary-logical-operator"></a>Birli mantıksal Işleç  
 [Not işleci](../../../../visual-basic/language-reference/operators/not-operator.md) bir `Boolean` ifadede mantıksal *değilleme* gerçekleştirir. İşleneni, işleneninin mantıksal tersini verir. İfade `True`olarak değerlendirilirse `Not` `Not` , `False`, ifadesi olarak `False`değerlendirilirse, öğesinidöndürür.`True` Aşağıdaki örnek bunu göstermektedir.  
  
 [!code-vb[VbVbalrOperators#77](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#77)]  
  
## <a name="binary-logical-operators"></a>İkili mantıksal Işleçler  
 [And işleci](../../../../visual-basic/language-reference/operators/and-operator.md) iki `Boolean` ifade üzerinde mantıksal bir *birlikte* gerçekleştirir. Her iki ifade olarak `True`değerlendirilir `And` , öğesini döndürür `True`. Deyimlerden en az biri olarak `False`değerlendirilirse `And` , öğesini döndürür `False`.  
  
 [OR işleci](../../../../visual-basic/language-reference/operators/or-operator.md) , mantıksal *ayırıcı* veya iki `Boolean` ifadeye *dahil* etme işlemini gerçekleştirir. İki ifade olarak `True`değerlendirilirse veya her ikisi de `Or` olarak `True`değerlendirilirse, öğesini döndürür `True`. Hiçbir ifadenin olarak `True`değerlendiriliyorsa, `Or` döndürür `False`.  
  
 [Xor işleci](../../../../visual-basic/language-reference/operators/xor-operator.md) iki `Boolean` ifadeye mantıksal *dışlama* gerçekleştirir. Tam olarak bir ifade olarak değerlendirilir `True`, ancak `Xor` her ikisini de değil `True`, döndürür. Her iki ifade de olarak `True` değerlendirilir veya her ikisini `False`de `Xor` olarak `False`değerlendirir, döndürür.  
  
 Aşağıdaki örnekte `And`, `Or`, ve `Xor` işleçleri gösterilmektedir.  
  
 [!code-vb[VbVbalrOperators#78](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#78)]  
  
## <a name="short-circuiting-logical-operations"></a>Kısa devre mantıksal Işlemler yürütülüyor  
 [AndAlso işleci](../../../../visual-basic/language-reference/operators/andalso-operator.md) , `And` işleçle çok benzerdir, bu da iki `Boolean` ifadeye de mantıksal bir işlem yapar. İkisi arasındaki temel fark, *kısa* devre uygulayan `AndAlso` davranışı gösteriyor. Bir `AndAlso` ifadedeki ilk ifade olarak değerlendirilirse, ikinci ifade `False`nihai sonucu değiştirmediği ve `AndAlso` döndürdüğü `False`için değerlendirilmez.  
  
 Benzer şekilde, [OrElse işleci](../../../../visual-basic/language-reference/operators/orelse-operator.md) iki `Boolean` ifadeye kısa devre uygulayan mantıksal bir birleşim uygular. Bir `OrElse` ifadedeki ilk ifade olarak değerlendirilirse, ikinci ifade `True`nihai sonucu değiştirmediği ve `OrElse` döndürdüğü `True`için değerlendirilmez.  
  
### <a name="short-circuiting-trade-offs"></a>Kısa süreli bir denge  
 Kısa devre uygulayan, mantıksal işlemin sonucunu değiştirebilecek bir ifadeyi değerlendirmeden performansı iyileştirebilir. Ancak, bu ifade ek eylemler gerçekleştirdiğinde, kısa devre uygulayan bu eylemleri atlar. Örneğin, ifade bir `Function` yordama çağrı içeriyorsa, ifade kısa devre dışı ise ve `Function` içinde yer alan ek kodlar çalıştırılsa, bu yordam çağrılmaz. Bu nedenle, işlev yalnızca belirli bir zaman çalışabilir ve doğru şekilde sınanmayabilir. Ya da program mantığı içindeki `Function`koda bağlı olabilirler.  
  
 Aşağıdaki örnek, `Or`, ve bunların kısa `And`devre dışı karşılıkları arasındaki farkı gösterir.  
  
 [!code-vb[VbVbalrOperators#81](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#81)]  
  
 [!code-vb[VbVbalrOperators#80](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#80)]  
  
 [!code-vb[VbVbalrOperators#79](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#79)]  
  
 Yukarıdaki örnekte, çağrı kısa devre dışı olduğunda, içindeki `checkIfValid()` bazı önemli kodların çalıştırılmadığını unutmayın. `If` İlk ifade çağrı `checkIfValid()` yapmaz `12 > 45` ,`And`ancak kısa devre dışı değildir. `False` İkinci `If` deyim çağırmaz `checkIfValid()` ,çünkü`12 > 45` döndürür `False`, kısadevrelerikinciifadedir.`AndAlso` Kısa devre `If` olmadığından, `checkIfValid()` `12 < 45` Üçüncüifade`True`çağrıları döndürür. `Or` Dördüncü `If` deyim çağrı `checkIfValid()`yapmaz `12 < 45` ,çünkü`True`döndürür, kısadevrelerikinciifadedir.`OrElse`  
  
## <a name="bitwise-operations"></a>Bit düzeyinde Işlemler  
 Bit düzeyinde işlemler ikili (taban 2) formda iki integral değeri değerlendirir. Bunlara karşılık gelen konumlarda bitleri karşılaştırırlar ve sonra karşılaştırmaya göre değerler atar. Aşağıdaki örnekte `And` işleç gösterilmektedir.  
  
 [!code-vb[VbVbalrConcepts#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrConcepts/VB/Class1.vb#2)]  
  
 Önceki örnek değerini `x` 1 olarak ayarlar. Bu durum aşağıdaki nedenlerden dolayı gerçekleşir:  
  
- Değerler ikili olarak değerlendirilir:  
  
     3 ikili biçiminde 3 = 011  
  
     5 ikili biçimi = 101  
  
- `And` İşleci, tek seferde bir ikili konum (bit) ikili gösterimlerini karşılaştırır. Belirli bir konumdaki bitlerin her ikisi de 1 ise, sonuçta bu konuma bir 1 konur. Her iki bit de 0 ise, sonuçta bu konuma 0 yerleştirilir. Yukarıdaki örnekte bu, aşağıdaki gibi çalışmaktadır:  
  
     011 (ikili biçimde 3)  
  
     101 (ikili biçimde 5)  
  
     001 (sonuç, ikili biçimde)  
  
- Sonuç ondalık olarak değerlendirilir. 001 değeri 1, bu nedenle `x` = 1 ' in ikili gösterimidir.  
  
 Bit düzeyinde `Or` işlem benzerdir, ancak karşılaştırılan bitlerin biri veya her ikisi 1 ise sonuç bitine 1 atanır. `Xor`karşılaştırılan bitlerin (her ikisi de değil) tam olarak biri 1 ise, sonuç bitini 1 atar. `Not`tek bir işlenen alır ve işaret biti dahil olmak üzere tüm bitleri ters çevirir ve bu değeri sonuca atar. Bu, `Not` işaretli pozitif sayıların her zaman negatif bir değer döndüğü ve negatif `Not` sayıların her zaman pozitif veya sıfır değer döndürdüğü anlamına gelir.  
  
 `AndAlso` Ve`OrElse` işleçleri bit düzeyinde işlemleri desteklemez.  
  
> [!NOTE]
> Bit düzeyinde işlemler yalnızca integral türlerinde gerçekleştirilebilir. Bit düzeyinde işlemin devam edebilmesi için kayan nokta değerlerinin tamsayı türlerine dönüştürülmesi gerekir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Mantıksal/bit düzeyinde Işleçler (Visual Basic)](../../../../visual-basic/language-reference/operators/logical-bitwise-operators.md)
- [Boole İfadeleri](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/boolean-expressions.md)
- [Visual Basic aritmetik Işleçler](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
- [Visual Basic karşılaştırma Işleçleri](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)
- [Visual Basic birleştirme Işleçleri](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/concatenation-operators.md)
- [İşleçlerin Etkili Bileşimi](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/efficient-combination-of-operators.md)
