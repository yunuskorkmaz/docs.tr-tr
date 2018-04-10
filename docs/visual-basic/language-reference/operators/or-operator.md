---
title: Or İşleci (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Or
helpviewer_keywords:
- Or operator [Visual Basic]
- operators [Visual Basic], bitwise
- inclusive Or operator [Visual Basic]
- bitwise operators [Visual Basic], OR operator
- Or keyword [Visual Basic]
- operators [Visual Basic], inclusive or
- operators [Visual Basic], disjunction
- bitwise comparison [Visual Basic]
- logical disjunction
- disjunction operator [Visual Basic]
ms.assetid: 41ed6905-bf3d-468a-9e3b-03c10d461891
caps.latest.revision: 12
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 4c9429eb2bdeb86bfa73786433231fdc22a230d9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="or-operator-visual-basic"></a>Or İşleci (Visual Basic)
Mantıksal ayrım iki gerçekleştirir `Boolean` ifadeler veya iki sayısal ifadeye bit tabanlı bir ayrım.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
result = expression1 Or expression2  
```  
  
## <a name="parts"></a>Bölümler  
 `result`  
 Gerekli. Tüm `Boolean` veya sayısal ifade. İçin `Boolean` karşılaştırma, `result` iki dahil mantıksal ayrım olduğu `Boolean` değerleri. Bit düzeyinde işlemler için `result` iki sayısal bit desenleri dahil Bitsel ayrım temsil eden bir sayısal değer.  
  
 `expression1`  
 Gerekli. Tüm `Boolean` veya sayısal ifade.  
  
 `expression2`  
 Gerekli. Tüm `Boolean` veya sayısal ifade.  
  
## <a name="remarks"></a>Açıklamalar  
 İçin `Boolean` karşılaştırma, `result` olan `False` varsa ve yalnızca her iki `expression1` ve `expression2` için değerlendirin `False`. Aşağıdaki tabloda gösterilmektedir nasıl `result` belirlenir.  
  
|Varsa `expression1` olduğu|Ve `expression2` olduğu|Değeri `result` olduğu|  
|-------------------------|--------------------------|------------------------------|  
|`True`|`True`|`True`|  
|`True`|`False`|`True`|  
|`False`|`True`|`True`|  
|`False`|`False`|`False`|  
  
> [!NOTE]
>  İçinde bir `Boolean` karşılaştırma, `Or` işleci her zaman yordam çağrıları yapma dahil olabilir hem ifadeleri değerlendirir. [OrElse işleci](../../../visual-basic/language-reference/operators/orelse-operator.md) gerçekleştirir *kısa devre*, başka bir deyişle, olması durumunda `expression1` olan `True`, ardından `expression2` değerlendirilmez.  
  
 Bit düzeyinde işlemler için `Or` işleci içinde iki sayısal ifadeye bit tabanlı karşılaştırma aynı konumlandırılmış bit gerçekleştirir ve buna karşılık gelen içinde bit ayarlar `result` aşağıdaki tabloya göre.  
  
|Varsa, bit `expression1` olduğu|Ve içinde bit `expression2` olduğu|Bit `result` olduğu|  
|--------------------------------|---------------------------------|----------------------------|  
|1.|1.|1.|  
|1.|0|1.|  
|0|1.|1.|  
|0|0|0|  
  
> [!NOTE]
>  Mantıksal ve bit düzeyinde işleçler diğer aritmetik ve ilişkisel işleçleri düşük önceliğe sahip olduğundan, tüm bit düzeyinde işlemler doğru yürütme emin olmak için parantez içine alınmış.  
  
## <a name="data-types"></a>Veri Türleri  
 İşlenen birini oluşması durumunda `Boolean` ifadesi ve tek bir sayısal ifade, Visual Basic dönüştürür `Boolean` ifade sayısal bir değere (– 1 için `True` ve 0 `False`) ve bit tabanlı işlemi gerçekleştirir.  
  
 İçin bir `Boolean` karşılaştırma, sonuç veri türünde `Boolean`. Bit tabanlı karşılaştırma için sonuç veri türü veri türleri için uygun sayısal bir tür değil. `expression1` ve `expression2`. "İlişkisel ve Bitsel karşılaştırmaları" tablosunda görmek [işleci sonuçlarını veri türleri](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md).  
  
## <a name="overloading"></a>Aşırı Yükleme  
 `Or` İşleci olabilir *aşırı*, işleneni, sınıf veya yapı türüne sahip olduğunda bir sınıf veya yapı davranışını tanımlayabilirsiniz, anlamına gelir. Bu tür bir sınıf veya yapı üzerinde kodunuzu bu işleç kullanıyorsa, yeniden tanımlanan davranışını anladığınızdan emin olun. Daha fazla bilgi için bkz: [işleç yordamları](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek kullanır `Or` iki ifadeleri (bunlar dahil) bir mantıksal ayrım gerçekleştirmek için işleci. Sonuç bir `Boolean` gösteren bir değer ya da iki ifadeye olup olmadığını `True`.  
  
 [!code-vb[VbVbalrOperators#35](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/or-operator_1.vb)]  
  
 Önceki örnekte sonuçlarını üreten `True`, `True`, ve `False`sırasıyla.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek kullanır `Or` iki sayısal ifadeye tek tek bitleri dahil mantıksal ayrım gerçekleştirmek için işleci. İşlenen karşılık gelen bitleri ya da ayarlanmış 1 sonuç düzeninde bit ayarlanır.  
  
 [!code-vb[VbVbalrOperators#36](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/or-operator_2.vb)]  
  
 Önceki örnekte, 10, 14 ve 14, sonuçları sırasıyla üretir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Mantıksal ve bit düzeyinde işleçler (Visual Basic)](../../../visual-basic/language-reference/operators/logical-bitwise-operators.md)  
 [Visual Basic'de İşleç önceliği](../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [İşlevselliğe göre listelenmiş işleçler](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)  
 [OrElse işleci](../../../visual-basic/language-reference/operators/orelse-operator.md)  
 [Visual Basic'de mantıksal ve bit düzeyinde işleçler](../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
