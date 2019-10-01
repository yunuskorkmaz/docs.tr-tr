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
ms.openlocfilehash: d82018a3018e2cf4362b9904ed127c20f56f6f0c
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/01/2019
ms.locfileid: "71701278"
---
# <a name="xor-operator-visual-basic"></a>Xor İşleci (Visual Basic)
İki `Boolean` ifadelerinde mantıksal dışlama veya iki sayısal ifadede bit tabanlı dışlama gerçekleştirir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```vb  
result = expression1 Xor expression2  
```  
  
## <a name="parts"></a>Bölümler  
 `result`  
 Gerekli. Herhangi bir `Boolean` veya sayısal değişken. Boolean karşılaştırma için, `result` iki `Boolean` değerin mantıksal dışlamasıdır (dışlamalı mantıksal ayırıcı). Bit düzeyinde işlemler için `result`, iki sayısal bit deseninin bit tabanlı dışlamasını (dışlayıcı bit düzeyinde ayırıcı) temsil eden sayısal bir değerdir.  
  
 `expression1`  
 Gerekli. Herhangi bir `Boolean` veya sayısal ifade.  
  
 `expression2`  
 Gerekli. Herhangi bir `Boolean` veya sayısal ifade.  
  
## <a name="remarks"></a>Açıklamalar  
 Boolean karşılaştırma için `result` ' dır ve yalnızca `expression1` ve `expression2` ' ten yalnızca biri `True` ' e değerlendirilirse `True` ' dir. Diğer bir deyişle, yalnızca `expression1` ve `expression2`, ters `Boolean` değerlerine göre değerlendirilir. Aşağıdaki tabloda `result` ' ın nasıl belirlendiği gösterilmektedir.  
  
|@No__t-0 ise|Ve `expression2`|@No__t-0 değeri|  
|-------------------------|--------------------------|------------------------------|  
|`True`|`True`|`False`|  
|`True`|`False`|`True`|  
|`False`|`True`|`True`|  
|`False`|`False`|`False`|  
  
> [!NOTE]
> Boole karşılaştırmasına `Xor` işleci her zaman her iki ifadeyi değerlendirir ve bu da yordam çağrıları yapmayı içerebilir. @No__t-0 ' a yönelik kısa devre temelli bir değer yoktur, çünkü sonuç her iki işlenenden de bağlıdır. *Kısa* devre mantıksal işleçler için bkz. [AndAlso Işleci](../../../visual-basic/language-reference/operators/andalso-operator.md) ve [orelsa işleci](../../../visual-basic/language-reference/operators/orelse-operator.md).  
  
 Bit düzeyinde işlemler için `Xor` işleci iki sayısal ifadede aynı şekilde konumlandırılmış bitlerin bit düzeyinde karşılaştırmasını gerçekleştirir ve `result` ' de karşılık gelen biti aşağıdaki tabloya göre ayarlar.  
  
|Bit `expression1` ise|Ve bit `expression2` ' dır|@No__t-0 ' daki bit|  
|--------------------------------|---------------------------------|----------------------------|  
|1\.|1\.|0|  
|1\.|0|1\.|  
|0|1\.|1\.|  
|0|0|0|  
  
> [!NOTE]
> Mantıksal ve bit düzeyinde işleçler diğer aritmetik ve ilişkisel işleçlerden daha düşük önceliğe sahip olduğundan, doğru yürütmeyi sağlamak için herhangi bir bit düzeyinde işlemin parantez içine alınması gerekir.  
  
 Örneğin, 5 `Xor` 3 6 ' dır. Bunun neden olduğunu görmek için, 5 ve 3 ' ü ikili gösterimlerine, 101 ve 011 dönüştürün. Ardından önceki tabloyu kullanarak 101 XOR 011 'in 6 ondalık sayının ikili temsili olan 110 olduğunu öğrenin.  
  
## <a name="data-types"></a>Veri Türleri  
 İşlenenler bir `Boolean` ifadesinde ve bir sayısal ifadeden oluşur Visual Basic, `Boolean` ifadesini sayısal bir değere dönüştürür (-1 `True` ve `False` için 0) ve bit düzeyinde bir işlem gerçekleştirir.  
  
 @No__t 0 karşılaştırması için sonucun veri türü `Boolean` ' dir. Bit düzeyinde karşılaştırma için sonuç veri türü, `expression1` ve `expression2` veri türleri için uygun sayısal bir türdür. [Işleç sonuçlarının veri türlerinde](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md)"Ilişkisel ve bit düzeyinde karşılaştırmalar" tablosuna bakın.  
  
## <a name="overloading"></a>Aşırı Yükleme  
 @No__t-0 işleci *aşırı*yüklenebilir, yani bir işlenen bu sınıf veya yapının türüne sahip olduğunda bir sınıf veya yapının davranışını yeniden tanımlayabileceği anlamına gelir. Kodunuz böyle bir sınıf veya yapıda bu işleci kullanıyorsa, yeniden tanımlanmış davranışını anladığınızdan emin olun. Daha fazla bilgi için bkz. [operatör yordamları](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, iki ifadeye mantıksal dışlama (dışlamalı mantıksal ayırıcı) gerçekleştirmek için `Xor` işlecini kullanır. Sonuç, ifadelerden tam olarak bir tane `True` olup olmadığını temsil eden bir `Boolean` değeridir.  
  
 [!code-vb[VbVbalrOperators#40](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#40)]  
  
 Önceki örnek sırasıyla `False`, `True` ve `False` sonuçları üretir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, iki sayısal ifadenin ayrı bitleri üzerinde mantıksal dışlama (dışlamalı mantıksal ayırıcı) gerçekleştirmek için `Xor` işlecini kullanır. Sonuç düzenindeki bit, işlenenlerde karşılık gelen bir bitlerin tam olarak 1 olarak ayarlanması halinde ayarlanır.  
  
 [!code-vb[VbVbalrOperators#41](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#41)]  
  
 Önceki örnek sırasıyla 2, 12 ve 14 sonuçlarını üretir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Mantıksal/bit düzeyinde Işleçler (Visual Basic)](../../../visual-basic/language-reference/operators/logical-bitwise-operators.md)
- [Visual Basic operatör önceliği](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [İşlevselliğe Göre Listelenmiş İşleçler](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [Visual Basic mantıksal ve bit düzeyinde Işleçler](../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
