---
title: AndAlso İşleci (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.AndAlso
- AndAlso
helpviewer_keywords:
- short-circuiting
- AndAlso operator [Visual Basic]
- operators [Visual Basic], short-circuiting
- operators [Visual Basic], conjunction
- short-circuit evaluation
ms.assetid: bbc15191-b374-495b-9b8f-7b8c2f4388eb
ms.openlocfilehash: 549d14cc35d285ac2e4a02a37dd201cc669c5627
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="andalso-operator-visual-basic"></a>AndAlso İşleci (Visual Basic)
Mantıksal ve işlecini iki ifadeye kısa devre gerçekleştirir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
result = expression1 AndAlso expression2  
```  
  
## <a name="parts"></a>Bölümler  
  
|Terim|Tanım|  
|---|---|  
|`result`|Gerekli. Tüm `Boolean` ifade. Sonuç `Boolean` iki ifadeye karşılaştırması sonucu.|  
|`expression1`|Gerekli. Tüm `Boolean` ifade.|  
|`expression2`|Gerekli. Tüm `Boolean` ifade.|  
  
## <a name="remarks"></a>Açıklamalar  
 Mantıksal bir işlem olarak kabul edilir *kısa devre* derlenmiş kod başka bir ifade sonucuna bağlı olarak bir ifade değerlendirme devre dışı bırakabilir. İlk ifade Hesaplandı sonucunu işleminin son sonucu belirlerse, ikinci ifade değerlendirmek için gerek yoktur nihai sonucu değiştiremediğinizden. Kısa devre atlandığında ifade karmaşıksa veya yordam çağrıları içeriyorsa performansı artırabilir.  
  
 İçin her iki ifade değerlendirin varsa `True`, `result` olan `True`. Aşağıdaki tabloda gösterilmektedir nasıl `result` belirlenir.  
  
|Varsa `expression1` olduğu|Ve `expression2` olduğu|Değeri `result` olduğu|  
|---|---|---|  
|`True`|`True`|`True`|  
|`True`|`False`|`False`|  
|`False`|(Değerlendirilmedi)|`False`|  
  
## <a name="data-types"></a>Veri Türleri  
 `AndAlso` İşleci yalnızca için tanımlanmış [Boole veri türü](../../../visual-basic/language-reference/data-types/boolean-data-type.md). Visual Basic dönüştürür için gereken her işlenen `Boolean` ve tamamen işlemi gerçekleştirir `Boolean`. Sayısal bir tür sonucu atarsanız, Visual Basic ondan dönüştürür `Boolean` bu türü. Bu, beklenmeyen davranışları üretebilir. Örneğin, `5 AndAlso 12` sonuçlanır `–1` için dönüştürüldüğünde `Integer`.  
  
## <a name="overloading"></a>Aşırı Yükleme  
 [Ve işleç](../../../visual-basic/language-reference/operators/and-operator.md) ve [IsFalse işleci](../../../visual-basic/language-reference/operators/isfalse-operator.md) olabilir *aşırı*, yani işleneni, türüne sahip olduğunda bir sınıf veya yapı davranışlarını tanımlayabilirsiniz, sınıf veya yapı. Aşırı yükleme `And` ve `IsFalse` işleçleri davranışını etkileyen `AndAlso` işleci. Kodunuzu kullanıyorsa `AndAlso` bir sınıf veya overloads yapısı `And` ve `IsFalse`, yeniden tanımlanan davranışlarını anladığınızdan emin olun. Daha fazla bilgi için bkz: [işleç yordamları](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek kullanır `AndAlso` iki ifadeleri mantıksal ve işlecini gerçekleştirmek için işleci. Sonuç bir `Boolean` tüm ifade conjoined olup olmadığını gösteren bir değer doğrudur. İlk ifade ise `False`, ikinci değerlendirilmez.  
  
 [!code-vb[VbVbalrOperators#24](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/andalso-operator_1.vb)]  
  
 Önceki örnekte sonuçlarını üreten `True`, `False`, ve `False`sırasıyla. Hesaplanmasına `secondCheck`, ilk zaten olduğundan ikinci ifade değerlendirilmez `False`. Ancak, ikinci ifade hesaplaması olarak değerlendirilir `thirdCheck`.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte gösterildiği bir `Function` verilen değer bir dizi öğeleri arasında arar yordamı. Dizi boş ise veya dizi uzunluğu aşıldı ise, `While` deyimi dizi öğesi arama değeri karşı test değil.  
  
 [!code-vb[VbVbalrOperators#25](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/andalso-operator_2.vb)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Mantıksal ve bit düzeyinde işleçler (Visual Basic)](../../../visual-basic/language-reference/operators/logical-bitwise-operators.md)  
 [Visual Basic'de İşleç önceliği](../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [İşlevselliğe Göre Listelenmiş İşleçler](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)  
 [And İşleci](../../../visual-basic/language-reference/operators/and-operator.md)  
 [IsFalse İşleci](../../../visual-basic/language-reference/operators/isfalse-operator.md)  
 [Visual Basic'de mantıksal ve bit düzeyinde işleçler](../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
