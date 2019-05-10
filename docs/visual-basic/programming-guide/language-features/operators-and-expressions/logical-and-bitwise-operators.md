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
ms.openlocfilehash: 23f3758527b787551ad83cbd4e19076b788c9dd8
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64649688"
---
# <a name="logical-and-bitwise-operators-in-visual-basic"></a>Visual Basic'de Mantıksal ve Bit Düzeyinde İşleçler
Mantıksal işleçler karşılaştırma `Boolean` ifadeleri ve dönüş bir `Boolean` sonucu. `And`, `Or`, `AndAlso`, `OrElse`, Ve `Xor` işleçleri *ikili* bunlar iki işlenenden tuttuğundan, while `Not` işleci *birli* tek bir işlenen aldığından. Bu işleçlerden bazıları, tam sayı değerleri üzerinde bit düzeyinde mantıksal işlemleri de yapabilirsiniz.  
  
## <a name="unary-logical-operator"></a>Birli mantıksal işleç  
 [Not işleci](../../../../visual-basic/language-reference/operators/not-operator.md) mantıksal gerçekleştirir *olumsuzlama* üzerinde bir `Boolean` ifade. Bu mantıksal tersidir işlenenin verir. İfade değerlendirme sonucu `True`, ardından `Not` döndürür `False`; ifadenin değerlendirdiği `False`, ardından `Not` döndürür `True`. Aşağıdaki örnek bunu göstermektedir.  
  
 [!code-vb[VbVbalrOperators#77](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#77)]  
  
## <a name="binary-logical-operators"></a>İkili mantıksal işleçler  
 [And işlecini](../../../../visual-basic/language-reference/operators/and-operator.md) mantıksal gerçekleştirir *birlikte* iki `Boolean` ifadeler. Her iki ifade sonucunu verirse `True`, ardından `And` döndürür `True`. En az bir ifade değerlendirme sonucu `False`, ardından `And` döndürür `False`.  
  
 [Veya işleci](../../../../visual-basic/language-reference/operators/or-operator.md) mantıksal gerçekleştirir *ayrım* veya *ekleme* iki `Boolean` ifadeler. Her iki ifade değerlendirilirse `True`, veya her ikisi de olarak değerlendirilmesi `True`, ardından `Or` döndürür `True`. Her iki ifade değerlendirilirse `True`, `Or` döndürür `False`.  
  
 [Xor işleci](../../../../visual-basic/language-reference/operators/xor-operator.md) mantıksal gerçekleştirir *dışlama* iki `Boolean` ifadeler. Tam olarak bir ifade değerlendirme sonucu `True`, iki değil, `Xor` döndürür `True`. Her iki ifade sonucunu verirse `True` veya her ikisi de olarak değerlendirilmesi `False`, `Xor` döndürür `False`.  
  
 Aşağıdaki örnekte gösterilmiştir `And`, `Or`, ve `Xor` işleçleri.  
  
 [!code-vb[VbVbalrOperators#78](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#78)]  
  
## <a name="short-circuiting-logical-operations"></a>Kısa devre mantıksal işlemleri  
 [AndAlso işleci](../../../../visual-basic/language-reference/operators/andalso-operator.md) çok benzer `And` işleci, ayrıca mantıksal ve işlecini iki gerçekleştirdiği, `Boolean` ifadeler. İkisi arasındaki temel fark `AndAlso` sergiler *kısa devre* davranışı. İlk ifadesinde bir `AndAlso` ifadeyi hesaplar için `False`, sonra da nihai sonucu değiştirilemiyor çünkü ikinci ifade değerlendirilmez ve `AndAlso` döndürür `False`.  
  
 Benzer şekilde, [OrElse işleci](../../../../visual-basic/language-reference/operators/orelse-operator.md) kısa devre mantıksal veya işlecini iki gerçekleştirir `Boolean` ifadeler. İlk ifadesinde bir `OrElse` ifadeyi hesaplar için `True`, sonra da nihai sonucu değiştirilemiyor çünkü ikinci ifade değerlendirilmez ve `OrElse` döndürür `True`.  
  
### <a name="short-circuiting-trade-offs"></a>Denge kısa devre  
 Kısa devre mantıksal işleminin sonucu değiştirilemez bir ifade değerlendirerek değil performansını iyileştirebilir. Ancak, bu ifade ek eylemler gerçekleştiriyorsa bu eylemlerin bir kısa devre atlar. Örneğin, ifade için bir çağrı içeriyorsa bir `Function` yordamı, yordam varsa ifade kısa devre yapılma ve herhangi ek bir kod içindeki çağrılmaz `Function` çalışmaz. Bu nedenle, işlev nadiren çalışabilir ve doğru bir şekilde test edilecek değil. Veya bir programın mantığı kodda bağımlı olabileceği `Function`.  
  
 Arasındaki fark aşağıdaki örnekte `And`, `Or`ve short-circuiting karşılıkları.  
  
 [!code-vb[VbVbalrOperators#81](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#81)]  
  
 [!code-vb[VbVbalrOperators#80](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#80)]  
  
 [!code-vb[VbVbalrOperators#79](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#79)]  
  
 Unutmayın önceki örnekte, bazı önemli kod içinde `checkIfValid()` çağrı kısa devre yapılma olduğunda çalışmaz. İlk `If` deyim aramaları `checkIfValid()` olsa bile `12 > 45` döndürür `False`, çünkü `And` değil kısa devre oluşturur. İkinci `If` deyimi çağırmaz `checkIfValid()`, çünkü zaman `12 > 45` döndürür `False`, `AndAlso` short-circuits ikinci ifade. Üçüncü `If` deyim aramaları `checkIfValid()` olsa bile `12 < 45` döndürür `True`, çünkü `Or` değil kısa devre oluşturur. Dördüncü `If` deyimi çağırmaz `checkIfValid()`, çünkü zaman `12 < 45` döndürür `True`, `OrElse` short-circuits ikinci ifade.  
  
## <a name="bitwise-operations"></a>Bit düzeyinde işlemler  
 Bit düzeyinde işlemler (taban 2) ikili biçimde iki tamsayı değerlerini değerlendirin. Bunlar, karşılık gelen konumlarda BITS karşılaştırın ve karşılaştırma üzerine dayalı değerler atayın. Aşağıdaki örnekte gösterilmiştir `And` işleci.  
  
 [!code-vb[VbVbalrConcepts#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrConcepts/VB/Class1.vb#2)]  
  
 Yukarıdaki örnekte ayarlar `x` 1. Bu, aşağıdaki nedenlerden dolayı gerçekleşir:  
  
- Değerleri, ikili olarak kabul edilir:  
  
     3. ikili biçimini 011 =  
  
     5'te ikili biçimini 101 =  
  
- `And` İşleci, ikili temsili bir ikili konum (bit) aynı anda karşılaştırır. Verilen konumda bitlerin her ikisi de 1, 1 sonuç o konuma yerleştirilir. Her iki bit 0 ise, 0 sonuç o konuma yerleştirilir. Önceki örnekte bu gibi işe:  
  
     011 (ikili biçimde 3)  
  
     101 (ikili biçimde 5)  
  
     001 (ikili biçimde sonuç)  
  
- Sonucun ondalık olarak kabul edilir. 001 değeri ikili 1, bu nedenle gösterimidir `x` = 1.  
  
 Bit düzeyinde `Or` veya her ikisini karşılaştırılan bitleri 1 ise 1 sonuç bite atanır dışında işlemi benzer. `Xor` Karşılaştırılan BITS (hem değil) tam olarak birine 1 ise 1 sonuç bite atar. `Not` tek bir işlenen alan, imza biti dahil olmak üzere tüm bitleri tersine çevirir ve sonucu bu değeri atar. Yani için pozitif bir sayı, imzalı `Not` her zaman negatif bir değer döndürür ve negatif sayılar için `Not` her zaman bir pozitif veya sıfır değeri döndürür.  
  
 `AndAlso` Ve `OrElse` işleçler bit düzeyinde işlemler desteklemez.  
  
> [!NOTE]
>  Yalnızca integral türleri üzerinde bit düzeyinde işlemler gerçekleştirilebilir. Bit düzeyinde işlem devam etmeden önce kayan nokta değerleri integral türlerine dönüştürülmesi gerekir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Mantıksal/bit düzeyinde işleçler (Visual Basic)](../../../../visual-basic/language-reference/operators/logical-bitwise-operators.md)
- [Boole İfadeleri](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/boolean-expressions.md)
- [Visual Basic'de aritmetik işleçler](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
- [Visual Basic'de Karşılaştırma işleçleri](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)
- [Visual Basic'de birleştirme işleçleri](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/concatenation-operators.md)
- [İşleçlerin Etkili Bileşimi](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/efficient-combination-of-operators.md)
