---
title: Or İşleci
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
ms.openlocfilehash: f6cfd1073ada42aa2db8be9b14c81319bc0db294
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90874764"
---
# <a name="or-operator-visual-basic"></a>Or İşleci (Visual Basic)

İki ifadeye mantıksal bir ayırıcı `Boolean` ya da iki sayısal ifadeye bit düzeyinde ayırıcı uygular.  
  
## <a name="syntax"></a>Sözdizimi  
  
```vb  
result = expression1 Or expression2  
```  
  
## <a name="parts"></a>Bölümler  

 `result`  
 Gereklidir. Herhangi bir `Boolean` veya sayısal ifade. `Boolean`Karşılaştırma için `result` iki değerden oluşan kapsamlı mantıksal ayırıcı olur `Boolean` . Bit düzeyinde işlemler için `result` iki sayısal bit deseninin kapsamlı bit düzeyinde debirleşimin temsil eden sayısal bir değerdir.  
  
 `expression1`  
 Gereklidir. Herhangi bir `Boolean` veya sayısal ifade.  
  
 `expression2`  
 Gereklidir. Herhangi bir `Boolean` veya sayısal ifade.  
  
## <a name="remarks"></a>Açıklamalar  

 `Boolean`Karşılaştırma için `result` `False` ve yalnızca her ikisi de `expression1` `expression2` olarak değerlendirilir `False` . Aşağıdaki tabloda nasıl belirlendiği gösterilmektedir `result` .  
  
|İse `expression1`|Ve `expression2`|`result`Öğesinin değeri|  
|-------------------------|--------------------------|------------------------------|  
|`True`|`True`|`True`|  
|`True`|`False`|`True`|  
|`False`|`True`|`True`|  
|`False`|`False`|`False`|  
  
> [!NOTE]
> Bir `Boolean` karşılaştırmada, `Or` işleç her zaman her iki ifadeyi değerlendirir ve bu da yordam çağrıları yapmayı içerebilir. [OrElse işleci](orelse-operator.md) *kısa*devre uygular, yani `expression1` ise, `True` `expression2` hesaplanmaz.  
  
 Bit düzeyinde işlemler için, `Or` işleç iki sayısal ifadede aynı şekilde konumlandırılmış bitlerin bit düzeyinde karşılaştırmasını gerçekleştirir ve karşılık gelen biti `result` aşağıdaki tabloya göre ayarlar.  
  
|Eğer bit `expression1` ise|Ve bit `expression2` ,|`result`İçindeki bit|  
|--------------------------------|---------------------------------|----------------------------|  
|1|1|1|  
|1|0|1|  
|0|1|1|  
|0|0|0|  
  
> [!NOTE]
> Mantıksal ve bit düzeyinde işleçler diğer aritmetik ve ilişkisel işleçlerden daha düşük önceliğe sahip olduğundan, doğru yürütmeyi sağlamak için herhangi bir bit düzeyinde işlemin parantez içine alınması gerekir.  
  
## <a name="data-types"></a>Veri Türleri  

 İşlenenler bir `Boolean` ifadeden ve bir sayısal ifadeden oluşur Visual Basic, `Boolean` ifadeyi sayısal bir değere dönüştürür (– 1 `True` ve için 0 `False` ) ve bit düzeyinde bir işlem gerçekleştirir.  
  
 Bir `Boolean` karşılaştırma için sonucun veri türü olur `Boolean` . Bit düzeyinde karşılaştırma için, sonuç veri türü ve veri türleri için uygun sayısal bir türdür `expression1` `expression2` . [Işleç sonuçlarının veri türlerinde](data-types-of-operator-results.md)"Ilişkisel ve bit düzeyinde karşılaştırmalar" tablosuna bakın.  
  
## <a name="overloading"></a>Aşırı Yükleme  

 `Or`İşleç *aşırı*yüklenebilir, yani bir işlenen bu sınıf veya yapının türüne sahip olduğunda bir sınıf veya yapının davranışını yeniden tanımlayabileceği anlamına gelir. Kodunuz böyle bir sınıf veya yapıda bu işleci kullanıyorsa, yeniden tanımlanmış davranışını anladığınızdan emin olun. Daha fazla bilgi için bkz. [operatör yordamları](../../programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Örnek  

 Aşağıdaki örnek, `Or` iki ifadeye kapsamlı bir mantıksal ayırıcı gerçekleştirmek için işlecini kullanır. Sonuç, `Boolean` iki deyimden birinin olup olmadığını temsil eden bir değerdir `True` .  
  
 [!code-vb[VbVbalrOperators#35](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#35)]  
  
 Yukarıdaki örnek `True` sırasıyla,, ve sonuçlarını üretir `True` `False` .  
  
## <a name="example"></a>Örnek  

 Aşağıdaki örnek, `Or` iki sayısal ifadenin ayrı bitleri üzerinde kapsamlı mantıksal ayırıcı gerçekleştirmek için işlecini kullanır. Sonuç düzenindeki bit, işlenenlerde karşılık gelen bitlerin biri 1 olarak ayarlandıysa ayarlanır.  
  
 [!code-vb[VbVbalrOperators#36](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#36)]  
  
 Yukarıdaki örnek sırasıyla 10, 14 ve 14 sonuçlarını üretir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Mantıksal/Bit Düzeyinde İşleçler (Visual Basic)](logical-bitwise-operators.md)
- [Visual Basic'de İşleç Önceliği](operator-precedence.md)
- [İşlevselliğe Göre Listelenmiş İşleçler](operators-listed-by-functionality.md)
- [OrElse İşleci](orelse-operator.md)
- [Visual Basic'de Mantıksal ve Bit Düzeyinde İşleçler](../../programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
