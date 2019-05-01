---
title: Or İşleci (Visual Basic)
ms.date: 07/20/2015
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
ms.openlocfilehash: 0277b6f24e62ed5f0cad3dae225c86fffc4c09b9
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62013523"
---
# <a name="or-operator-visual-basic"></a>Or İşleci (Visual Basic)
İkisini de bir mantıksal veya işlecini gerçekleştirir `Boolean` deyimlerde ya da bir iki sayısal ifadeye bit tabanlı veya işlecini.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
result = expression1 Or expression2  
```  
  
## <a name="parts"></a>Bölümler  
 `result`  
 Gerekli. Tüm `Boolean` veya sayısal ifade. İçin `Boolean` karşılaştırması, `result` iki kapsamlı mantıksal veya işlecini olan `Boolean` değerleri. Bit düzeyinde işlemler için `result` iki sayısal bit desenlerinin kapsamlı bit tabanlı veya işlecini temsil eden sayısal bir değerdir.  
  
 `expression1`  
 Gerekli. Tüm `Boolean` veya sayısal ifade.  
  
 `expression2`  
 Gerekli. Tüm `Boolean` veya sayısal ifade.  
  
## <a name="remarks"></a>Açıklamalar  
 İçin `Boolean` karşılaştırması, `result` olduğu `False` varsa ve yalnızca her iki `expression1` ve `expression2` vermesi `False`. Aşağıdaki tabloda gösterilmiştir nasıl `result` belirlenir.  
  
|Varsa `expression1` olduğu|Ve `expression2` olduğu|Değerini `result` olduğu|  
|-------------------------|--------------------------|------------------------------|  
|`True`|`True`|`True`|  
|`True`|`False`|`True`|  
|`False`|`True`|`True`|  
|`False`|`False`|`False`|  
  
> [!NOTE]
>  İçinde bir `Boolean` karşılaştırması, `Or` işleci yordam çağrıları yapma içerebilir her iki ifade her zaman değerlendirilir. [OrElse işleci](../../../visual-basic/language-reference/operators/orelse-operator.md) gerçekleştirir *kısa devre*, olması durumunda anlamına gelir `expression1` olduğu `True`, ardından `expression2` değerlendirilmez.  
  
 Bit düzeyinde işlemler için `Or` işleci iki sayısal ifadeye bit düzeyinde bir karşılaştırma aynı şekilde konumlandırılmış bit gerçekleştirir ve karşılık gelen, bit ayarlar `result` aşağıdaki tabloya göre.  
  
|Varsa, bit `expression1` olduğu|Ve içindeki bit `expression2` olduğu|Bit `result` olduğu|  
|--------------------------------|---------------------------------|----------------------------|  
|1.|1.|1.|  
|1|0|1.|  
|0|1.|1|  
|0|0|0|  
  
> [!NOTE]
>  Mantıksal ve bit düzeyinde işleçler diğer aritmetik ve ilişkisel işleçler düşük önceliğe sahip olduğundan, herhangi bir bit düzeyinde işlemler doğru yürütme emin olmak için parantez içine alınmalıdır.  
  
## <a name="data-types"></a>Veri Türleri  
 İşlenenler biri oluşuyorsa `Boolean` ifadesi ve bir sayısal ifade, Visual Basic dönüştürür `Boolean` ifadesi bir sayısal değere (– 1 için `True` ve 0 `False`) ve bir bit düzeyinde işlem gerçekleştirir.  
  
 İçin bir `Boolean` karşılaştırma, sonuç veri türü olan `Boolean`. Bit düzeyinde bir karşılaştırması için sonuç veri türü bir sayısal veri türleri için uygun türüdür `expression1` ve `expression2`. "İlişkisel ve bit düzeyinde karşılaştırmaları" tablosuna bakın [işleci sonuçlarını veri türleri](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md).  
  
## <a name="overloading"></a>Aşırı Yükleme  
 `Or` İşleci olabilir *aşırı*, işleneni, sınıf veya yapı türüne sahip olduğunda bir sınıf veya yapı davranışını tanımlayabilirsiniz, anlamına gelir. Kodunuz bu tür bir sınıf veya yapı üzerinde bu işleç kullanıyorsa, yeniden tanımlanan davranışını anladığınızdan emin olun. Daha fazla bilgi için [işleç yordamları](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte `Or` kapsamlı mantıksal veya işlecini iki ifadelerini gerçekleştirmek için işleci. Sonuç bir `Boolean` gösteren bir değer iki ifadeden birini olup olmadığını `True`.  
  
 [!code-vb[VbVbalrOperators#35](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#35)]  
  
 Yukarıdaki örnekte sonuçlarını üretir `True`, `True`, ve `False`sırasıyla.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte `Or` kapsamlı mantıksal veya işlecini bireysel iki sayısal ifadeye bit üzerinde gerçekleştirmek için işleci. Sonuç deseninde bit işlenenler karşılık gelen bitleri ya da ayarlanmış ise 1 olarak ayarlanır.  
  
 [!code-vb[VbVbalrOperators#36](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#36)]  
  
 Yukarıdaki örnekte sırasıyla 10, 14 ve 14, sonuçlar üretir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Mantıksal/bit düzeyinde işleçler (Visual Basic)](../../../visual-basic/language-reference/operators/logical-bitwise-operators.md)
- [Visual Basic'de İşleç önceliği](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [İşlevselliğe Göre Listelenmiş İşleçler](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [OrElse İşleci](../../../visual-basic/language-reference/operators/orelse-operator.md)
- [Visual Basic'de mantıksal ve bit düzeyinde işleçler](../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
