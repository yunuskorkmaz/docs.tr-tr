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
ms.openlocfilehash: 59f27b92996e1506be5967de88c22fb88e06f5b7
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69965854"
---
# <a name="xor-operator-visual-basic"></a>Xor İşleci (Visual Basic)
İki `Boolean` ifadede bir mantıksal dışlama veya iki sayısal ifadede bit tabanlı dışlama gerçekleştirir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
result = expression1 Xor expression2  
```  
  
## <a name="parts"></a>Bölümler  
 `result`  
 Gerekli. Herhangi `Boolean` bir veya sayısal değişken. Boolean karşılaştırma `result` için iki `Boolean` değerin mantıksal dışlamasıdır (dışlamalı mantıksal ayırıcı). Bit düzeyinde işlemler `result` için iki sayısal bit deseninin bit düzeyinde dışlamasını (dışlayıcı bit düzeyinde ayırıcı) temsil eden sayısal bir değerdir.  
  
 `expression1`  
 Gerekli. Herhangi `Boolean` bir veya sayısal ifade.  
  
 `expression2`  
 Gerekli. Herhangi `Boolean` bir veya sayısal ifade.  
  
## <a name="remarks"></a>Açıklamalar  
 Boolean karşılaştırma için, `result` `True` ve `expression1` yalnızca tam `expression2` olarak`True`bir tane olarak değerlendirilir. Diğer bir deyişle, ve yalnızca Eğer `expression1` ve `expression2` ters `Boolean` değerler olarak değerlendirilir. Aşağıdaki tabloda nasıl `result` belirlendiği gösterilmektedir.  
  
|`expression1` İse|Ve `expression2`|Öğesinin `result` değeri|  
|-------------------------|--------------------------|------------------------------|  
|`True`|`True`|`False`|  
|`True`|`False`|`True`|  
|`False`|`True`|`True`|  
|`False`|`False`|`False`|  
  
> [!NOTE]
> Boole karşılaştırmasına, `Xor` işleç her zaman her iki ifadeyi değerlendirir ve bu da yordam çağrıları yapmayı içerebilir. Her iki işlenenden de her zaman bağlı olduğundan `Xor`, için bir kısa devre temelli karşılık yoktur. *Kısa* devre mantıksal işleçler için bkz. [AndAlso Işleci](../../../visual-basic/language-reference/operators/andalso-operator.md) ve [orelsa işleci](../../../visual-basic/language-reference/operators/orelse-operator.md).  
  
 Bit düzeyinde işlemler için, `Xor` işleç iki sayısal ifadede aynı şekilde `result` konumlandırılmış bitlerin bit düzeyinde karşılaştırmasını gerçekleştirir ve karşılık gelen biti aşağıdaki tabloya göre ayarlar.  
  
|Eğer bit `expression1` ise|Ve bit `expression2` ,|İçindeki `result` bit|  
|--------------------------------|---------------------------------|----------------------------|  
|1\.|1|0|  
|1\.|0|1\.|  
|0|1\.|1|  
|0|0|0|  
  
> [!NOTE]
> Mantıksal ve bit düzeyinde işleçler diğer aritmetik ve ilişkisel işleçlerden daha düşük önceliğe sahip olduğundan, doğru yürütmeyi sağlamak için herhangi bir bit düzeyinde işlemin parantez içine alınması gerekir.  
  
 Örneğin, 5 `Xor` 3, 6 ' dır. Bunun neden olduğunu görmek için, 5 ve 3 ' ü ikili gösterimlerine, 101 ve 011 dönüştürün. Ardından önceki tabloyu kullanarak 101 XOR 011 'in 6 ondalık sayının ikili temsili olan 110 olduğunu öğrenin.  
  
## <a name="data-types"></a>Veri Türleri  
 İşlenenler bir `Boolean` ifadeden ve bir sayısal ifadeden oluşur Visual Basic, `Boolean` ifadeyi sayısal bir `True` değere dönüştürür (– `False`1 ve için 0) ve bit düzeyinde bir işlem gerçekleştirir.  
  
 Bir `Boolean` karşılaştırma için sonucun veri türü olur `Boolean`. Bit düzeyinde karşılaştırma için, sonuç veri türü `expression1` ve `expression2`veri türleri için uygun sayısal bir türdür. [Işleç sonuçlarının veri türlerinde](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md)"Ilişkisel ve bit düzeyinde karşılaştırmalar" tablosuna bakın.  
  
## <a name="overloading"></a>Aşırı Yükleme  
 İşleç aşırı yüklenebilir, yani bir işlenen bu sınıf veya yapının türüne sahip olduğunda bir sınıf veya yapının davranışını yeniden tanımlayabileceği anlamına gelir. `Xor` Kodunuz böyle bir sınıf veya yapıda bu işleci kullanıyorsa, yeniden tanımlanmış davranışını anladığınızdan emin olun. Daha fazla bilgi için bkz. [operatör yordamları](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, iki ifadeye `Xor` mantıksal dışlama (dışlamalı mantıksal ayırıcı) gerçekleştirmek için işlecini kullanır. Sonuç, `Boolean` `True`ifadelerden tam olarak bir tane olup olmadığını temsil eden bir değerdir.  
  
 [!code-vb[VbVbalrOperators#40](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#40)]  
  
 Önceki örnek sırasıyla `False`, `True`, ve `False`sonuçlarını üretir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, iki sayısal `Xor` ifadenin ayrı bitleri üzerinde mantıksal dışlama (dışlamalı mantıksal ayırıcı) gerçekleştirmek için işlecini kullanır. Sonuç düzenindeki bit, işlenenlerde karşılık gelen bir bitlerin tam olarak 1 olarak ayarlanması halinde ayarlanır.  
  
 [!code-vb[VbVbalrOperators#41](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#41)]  
  
 Önceki örnek sırasıyla 2, 12 ve 14 sonuçlarını üretir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Mantıksal/bit düzeyinde Işleçler (Visual Basic)](../../../visual-basic/language-reference/operators/logical-bitwise-operators.md)
- [Visual Basic operatör önceliği](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [İşlevselliğe Göre Listelenmiş İşleçler](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [Visual Basic mantıksal ve bit düzeyinde Işleçler](../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
