---
title: Xor İşleci (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Xor
helpviewer_keywords:
- exclusive OR operator [Visual Basic]
- logical exclusion
- operators [Visual Basic], exclusive or
- exclusion operator [Visual Basic]
- operators [Visual Basic], bitwise
- bitwise operators [Visual Basic], XOR operator
- Xor operator [Visual Basic]
- Xor keyword [Visual Basic]
- bitwise comparison [Visual Basic]
ms.assetid: 036000a9-3934-4e7f-a9d0-a816de3d84a6
ms.openlocfilehash: af6589206232f01b572cd2b965ba1a0f36d462e1
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54527126"
---
# <a name="xor-operator-visual-basic"></a>Xor İşleci (Visual Basic)
İki mantıksal dışlama gerçekleştirir `Boolean` deyimlerde ya da iki sayısal ifadeye bit tabanlı dışlama.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
result = expression1 Xor expression2  
```  
  
## <a name="parts"></a>Bölümler  
 `result`  
 Gerekli. Tüm `Boolean` veya sayısal bir değişken. Boole karşılaştırma `result` (özel mantıksal veya işlecini) iki mantıksal dışlama `Boolean` değerleri. Bit düzeyinde işlemler için `result` iki sayısal bit desenlerinin (özel bit tabanlı veya işlecini) bit tabanlı dışlama temsil eden sayısal bir değerdir.  
  
 `expression1`  
 Gerekli. Tüm `Boolean` veya sayısal ifade.  
  
 `expression2`  
 Gerekli. Tüm `Boolean` veya sayısal ifade.  
  
## <a name="remarks"></a>Açıklamalar  
 Boole karşılaştırma `result` olduğu `True` ve yalnızca, tam olarak birine `expression1` ve `expression2` değerlendiren `True`. Diğer bir deyişle, ve yalnızca, `expression1` ve `expression2` değerlendirmek için ters `Boolean` değerleri. Aşağıdaki tabloda gösterilmiştir nasıl `result` belirlenir.  
  
|Varsa `expression1` olduğu|Ve `expression2` olduğu|Değerini `result` olduğu|  
|-------------------------|--------------------------|------------------------------|  
|`True`|`True`|`False`|  
|`True`|`False`|`True`|  
|`False`|`True`|`True`|  
|`False`|`False`|`False`|  
  
> [!NOTE]
>  Bir Boolean karşılaştırmaya `Xor` işleci yordam çağrıları yapma içerebilir her iki ifade her zaman değerlendirilir. İçin hiçbir short-circuiting karşılığı yoktur `Xor`, sonucu her zaman her iki işlenen üzerinde de bağlıdır. İçin *kısa devre* mantıksal işleçler bkz [AndAlso işleci](../../../visual-basic/language-reference/operators/andalso-operator.md) ve [OrElse işleci](../../../visual-basic/language-reference/operators/orelse-operator.md).  
  
 Bit düzeyinde işlemler için `Xor` işleci iki sayısal ifadeye bit düzeyinde bir karşılaştırma aynı şekilde konumlandırılmış bit gerçekleştirir ve karşılık gelen, bit ayarlar `result` aşağıdaki tabloya göre.  
  
|Varsa, bit `expression1` olduğu|Ve içindeki bit `expression2` olduğu|Bit `result` olduğu|  
|--------------------------------|---------------------------------|----------------------------|  
|1.|1|0|  
|1.|0|1.|  
|0|1.|1|  
|0|0|0|  
  
> [!NOTE]
>  Mantıksal ve bit düzeyinde işleçler diğer aritmetik ve ilişkisel işleçler düşük önceliğe sahip olduğundan, herhangi bir bit düzeyinde işlemler doğru yürütme emin olmak için parantez içine alınmalıdır.  
  
 Örneğin, 5 `Xor` 3, 6. Bu neden olduğunu görmek için bu nedenle, 5. ve 3, ikili gösterimler için 101 ve 011 Dönüştür. Ardından, ondalık sayı 6 ikili gösterimini olduğu 101 Xor 011 110, olduğunu belirlemek için önceki tabloyu kullanın.  
  
## <a name="data-types"></a>Veri Türleri  
 İşlenenler biri oluşuyorsa `Boolean` ifadesi ve bir sayısal ifade, Visual Basic dönüştürür `Boolean` ifadesi bir sayısal değere (– 1 için `True` ve 0 `False`) ve bir bit düzeyinde işlem gerçekleştirir.  
  
 İçin bir `Boolean` karşılaştırma, sonuç veri türü olan `Boolean`. Bit düzeyinde bir karşılaştırması için sonuç veri türü bir sayısal veri türleri için uygun türüdür `expression1` ve `expression2`. "İlişkisel ve bit düzeyinde karşılaştırmaları" tablosuna bakın [işleci sonuçlarını veri türleri](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md).  
  
## <a name="overloading"></a>Aşırı Yükleme  
 `Xor` İşleci olabilir *aşırı*, işleneni, sınıf veya yapı türüne sahip olduğunda bir sınıf veya yapı davranışını tanımlayabilirsiniz, anlamına gelir. Kodunuz bu tür bir sınıf veya yapı üzerinde bu işleç kullanıyorsa, yeniden tanımlanan davranışını anladığınızdan emin olun. Daha fazla bilgi için [işleç yordamları](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte `Xor` iki ifadelerini temel (özel mantıksal veya işlecini) mantıksal dışlama gerçekleştirmek için işleci. Sonuç bir `Boolean` tam olarak bir ifade olup olmadığını gösteren bir değer `True`.  
  
 [!code-vb[VbVbalrOperators#40](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xor-operator_1.vb)]  
  
 Önceki örnekte sonuçlarını üretir `False`, `True`, ve `False`sırasıyla.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte `Xor` mantıksal dışlama (özel mantıksal veya işlecini) bireysel iki sayısal ifadeye bit üzerinde gerçekleştirmek için işleci. Tek bir işlenen karşılık gelen bitleri 1 olarak ayarlarsanız sonucu deseninde bir bit ayarlanır.  
  
 [!code-vb[VbVbalrOperators#41](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xor-operator_2.vb)]  
  
 Önceki örnekte sırasıyla 2, 12 ve 14, sonuçlar üretir.  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Mantıksal/bit düzeyinde işleçler (Visual Basic)](../../../visual-basic/language-reference/operators/logical-bitwise-operators.md)
- [Visual Basic'de İşleç önceliği](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [İşlevselliğe Göre Listelenmiş İşleçler](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [Visual Basic'de mantıksal ve bit düzeyinde işleçler](../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
