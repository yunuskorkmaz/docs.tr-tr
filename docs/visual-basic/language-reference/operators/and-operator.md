---
title: And İşleci
ms.date: 07/20/2015
f1_keywords:
- vb.And
helpviewer_keywords:
- operators [Visual Basic], bitwise
- logical conjunction
- bitwise AND operator [Visual Basic]
- conjunction operator [Visual Basic]
- And operator [Visual Basic]
- bitwise operators [Visual Basic], AND operator
- operators [Visual Basic], conjunction
- bitwise comparison [Visual Basic]
ms.assetid: 2ea711f3-439a-4c7c-9e3a-1ffe3b0d6046
ms.openlocfilehash: b4d6d08cca2907befeab2e31c6804b69849c9e38
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90874866"
---
# <a name="and-operator-visual-basic"></a>And İşleci (Visual Basic)

İki ifadeye bir mantıksal birlikte `Boolean` veya iki sayısal ifadeye bit tabanlı bir birlikte uygular.  
  
## <a name="syntax"></a>Sözdizimi  
  
```vb  
result = expression1 And expression2  
```  
  
## <a name="parts"></a>Bölümler  

 `result`  
 Gereklidir. Herhangi bir `Boolean` veya sayısal ifade. Boolean karşılaştırma için `result` iki değerden oluşan mantıksal bir değer `Boolean` . Bit düzeyinde işlemler için, `result` iki sayısal bit deseninin bit düzeyinde birlikte temsil eden sayısal bir değerdir.  
  
 `expression1`  
 Gereklidir. Herhangi bir `Boolean` veya sayısal ifade.  
  
 `expression2`  
 Gereklidir. Herhangi bir `Boolean` veya sayısal ifade.  
  
## <a name="remarks"></a>Açıklamalar  

 Boolean karşılaştırma için `result` `True` ve yalnızca her ikisi de `expression1` `expression2` olarak değerlendirilir `True` . Aşağıdaki tabloda nasıl belirlendiği gösterilmektedir `result` .  
  
|İse `expression1`|Ve `expression2`|`result`Öğesinin değeri|  
|-------------------------|--------------------------|------------------------------|  
|`True`|`True`|`True`|  
|`True`|`False`|`False`|  
|`False`|`True`|`False`|  
|`False`|`False`|`False`|  
  
> [!NOTE]
> Boole karşılaştırmasına, `And` işleç her zaman her iki ifadeyi değerlendirir ve bu da yordam çağrıları yapmayı içerebilir. [AndAlso işleci de](andalso-operator.md) *kısa*devre uygular, yani varsa `expression1` `False` , `expression2` değerlendirilmez.  
  
 Sayısal değerlere uygulandığında `And` operatör iki sayısal ifadede aynı şekilde konumlandırılmış bitlerin bit düzeyinde karşılaştırmasını gerçekleştirir ve karşılık gelen biti `result` aşağıdaki tabloya göre ayarlar.  
  
|Eğer bit `expression1` ise|Ve bit `expression2` ,|`result`İçindeki bit|  
|--------------------------------|---------------------------------|----------------------------|  
|1|1|1|  
|1|0|0|  
|0|1|0|  
|0|0|0|  
  
> [!NOTE]
> Mantıksal ve bit düzeyinde işleçler diğer aritmetik ve ilişkisel işleçlerden daha düşük önceliğe sahip olduğundan, doğru sonuçları sağlamak için herhangi bir bit düzeyinde işlemin parantez içine alınması gerekir.  
  
## <a name="data-types"></a>Veri Türleri  

 İşlenenler bir `Boolean` ifadeden ve bir sayısal ifadeden oluşur Visual Basic, `Boolean` ifadeyi sayısal bir değere dönüştürür (– 1 `True` ve için 0 `False` ) ve bit düzeyinde bir işlem gerçekleştirir.  
  
 Boolean karşılaştırma için sonucun veri türü olur `Boolean` . Bit düzeyinde karşılaştırma için, sonuç veri türü ve veri türleri için uygun sayısal bir türdür `expression1` `expression2` . [Işleç sonuçlarının veri türlerinde](data-types-of-operator-results.md)"Ilişkisel ve bit düzeyinde karşılaştırmalar" tablosuna bakın.  
  
> [!NOTE]
> `And`İşleç *aşırı*yüklenebilir, yani bir işlenen bu sınıf veya yapının türüne sahip olduğunda bir sınıf veya yapının davranışını yeniden tanımlayabileceği anlamına gelir. Kodunuz böyle bir sınıf veya yapıda bu işleci kullanıyorsa, yeniden tanımlanmış davranışını anladığınızdan emin olun. Daha fazla bilgi için bkz. [operatör yordamları](../../programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Örnek  

 Aşağıdaki örnek, `And` iki ifadeye mantıksal bir birlikte gerçekleştirmek için işlecini kullanır. Sonuç, `Boolean` ifadelerin her ikisinin de olup olmadığını temsil eden bir değerdir `True` .  
  
 [!code-vb[VbVbalrOperators#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#22)]  
  
 Yukarıdaki örnek `True` sırasıyla ve, sonuçları üretir `False` .  
  
## <a name="example"></a>Örnek  

 Aşağıdaki örnek, `And` iki sayısal ifadenin ayrı bitleri üzerinde mantıksal bir işlem gerçekleştirmek için işlecini kullanır. Sonuç düzenindeki bit, işlenenlerde karşılık gelen bitlerin her ikisi de 1 olarak ayarlandıysa ayarlanır.  
  
 [!code-vb[VbVbalrOperators#23](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#23)]  
  
 Yukarıdaki örnek sırasıyla 8, 2 ve 0 sonuçlarını üretir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Mantıksal/Bit Düzeyinde İşleçler (Visual Basic)](logical-bitwise-operators.md)
- [Visual Basic'de İşleç Önceliği](operator-precedence.md)
- [İşlevselliğe Göre Listelenmiş İşleçler](operators-listed-by-functionality.md)
- [AndAlso İşleci](andalso-operator.md)
- [Visual Basic'de Mantıksal ve Bit Düzeyinde İşleçler](../../programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
