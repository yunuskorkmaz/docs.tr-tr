---
title: Xor İşleci (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
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
caps.latest.revision: 17
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: b14f11f2df2df9c29e88e9188390cfe245d2cb58
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="xor-operator-visual-basic"></a>Xor İşleci (Visual Basic)
Mantıksal dışlama iki gerçekleştirir `Boolean` ifadeler veya iki sayısal ifadeye bit tabanlı bir dışlama.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
result = expression1 Xor expression2  
```  
  
## <a name="parts"></a>Bölümler  
 `result`  
 Gerekli. Tüm `Boolean` veya sayısal değişkeni. Boole karşılaştırma için `result` iki mantıksal dışlama (özel mantıksal ayrım) işlemi `Boolean` değerleri. Bit düzeyinde işlemler için `result` iki sayısal bit desenleri Bitsel dışlama (özel Bitsel ayrım) temsil eden sayısal bir değerdir.  
  
 `expression1`  
 Gerekli. Tüm `Boolean` veya sayısal ifade.  
  
 `expression2`  
 Gerekli. Tüm `Boolean` veya sayısal ifade.  
  
## <a name="remarks"></a>Açıklamalar  
 Boole karşılaştırma için `result` olan `True` ve yalnızca, tam olarak birine `expression1` ve `expression2` değerlendiren `True`. Diğer bir deyişle, yalnızca ve yalnızca, `expression1` ve `expression2` değerlendirmek için ters `Boolean` değerleri. Aşağıdaki tabloda gösterilmektedir nasıl `result` belirlenir.  
  
|Varsa `expression1` olduğu|Ve `expression2` olduğu|Değeri `result` olduğu|  
|-------------------------|--------------------------|------------------------------|  
|`True`|`True`|`False`|  
|`True`|`False`|`True`|  
|`False`|`True`|`True`|  
|`False`|`False`|`False`|  
  
> [!NOTE]
>  Boole karşılaştırmaya `Xor` işleci her zaman yordam çağrıları yapma dahil olabilir hem ifadeleri değerlendirir. Hiçbir short-circuiting karşılığı vardır `Xor`, sonucu her zaman iki işlenen üzerinde bağlıdır. İçin *kısa devre* mantıksal işleçler bkz [AndAlso işleci](../../../visual-basic/language-reference/operators/andalso-operator.md) ve [OrElse işleci](../../../visual-basic/language-reference/operators/orelse-operator.md).  
  
 Bit düzeyinde işlemler için `Xor` işleci içinde iki sayısal ifadeye bit tabanlı karşılaştırma aynı konumlandırılmış bit gerçekleştirir ve buna karşılık gelen içinde bit ayarlar `result` aşağıdaki tabloya göre.  
  
|Varsa, bit `expression1` olduğu|Ve içinde bit `expression2` olduğu|Bit `result` olduğu|  
|--------------------------------|---------------------------------|----------------------------|  
|1.|1.|0|  
|1.|0|1.|  
|0|1.|1.|  
|0|0|0|  
  
> [!NOTE]
>  Mantıksal ve bit düzeyinde işleçler diğer aritmetik ve ilişkisel işleçleri düşük önceliğe sahip olduğundan, tüm bit düzeyinde işlemler doğru yürütme emin olmak için parantez içine alınmış.  
  
 Örneğin, 5 `Xor` 3, 6. Bu neden olduğunu görmek için bu nedenle, kendi ikili gösterimler için 101 ve 011 5 ve 3 dönüştürün. Ardından, ondalık sayı 6 ikili gösterimidir 101 Xor 011 110, olduğunu belirlemek için önceki tabloyu kullanın.  
  
## <a name="data-types"></a>Veri Türleri  
 İşlenen birini oluşması durumunda `Boolean` ifadesi ve tek bir sayısal ifade, Visual Basic dönüştürür `Boolean` ifade sayısal bir değere (– 1 için `True` ve 0 `False`) ve bit tabanlı işlemi gerçekleştirir.  
  
 İçin bir `Boolean` karşılaştırma, sonuç veri türünde `Boolean`. Bit tabanlı karşılaştırma için sonuç veri türü veri türleri için uygun sayısal bir tür değil. `expression1` ve `expression2`. "İlişkisel ve Bitsel karşılaştırmaları" tablosunda görmek [işleci sonuçlarını veri türleri](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md).  
  
## <a name="overloading"></a>Aşırı Yükleme  
 `Xor` İşleci olabilir *aşırı*, işleneni, sınıf veya yapı türüne sahip olduğunda bir sınıf veya yapı davranışını tanımlayabilirsiniz, anlamına gelir. Bu tür bir sınıf veya yapı üzerinde kodunuzu bu işleç kullanıyorsa, yeniden tanımlanan davranışını anladığınızdan emin olun. Daha fazla bilgi için bkz: [işleç yordamları](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek kullanır `Xor` iki ifadeleri mantıksal dışlama (özel mantıksal ayrım) gerçekleştirmek için işleci. Sonuç bir `Boolean` ifadeleri tam olarak birine olup olmadığını gösteren bir değer `True`.  
  
 [!code-vb[VbVbalrOperators#40](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xor-operator_1.vb)]  
  
 Önceki örnekte sonuçlarını üreten `False`, `True`, ve `False`sırasıyla.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek kullanır `Xor` iki sayısal ifadeye tek tek bitleri mantıksal dışlama (özel mantıksal ayrım) gerçekleştirmek için işleci. İşlenen karşılık gelen bitleri tam olarak birine 1 olarak ayarlanırsa sonuç düzeninde bit ayarlanır.  
  
 [!code-vb[VbVbalrOperators#41](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xor-operator_2.vb)]  
  
 Önceki örnek 2, 12 ve 14, sonuçları sırasıyla üretir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Mantıksal ve bit düzeyinde işleçler (Visual Basic)](../../../visual-basic/language-reference/operators/logical-bitwise-operators.md)  
 [Visual Basic'de İşleç önceliği](../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [İşlevselliğe göre listelenmiş işleçler](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)  
 [Visual Basic'de mantıksal ve bit düzeyinde işleçler](../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
