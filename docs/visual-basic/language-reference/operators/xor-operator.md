---
title: Xor İşleci
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
ms.openlocfilehash: 999050314d674fa98833083d84796e471c22971d
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84406348"
---
# <a name="xor-operator-visual-basic"></a>Xor İşleci (Visual Basic)
İki ifadede bir mantıksal dışlama `Boolean` veya iki sayısal ifadede bit tabanlı dışlama gerçekleştirir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```vb  
result = expression1 Xor expression2  
```  
  
## <a name="parts"></a>Bölümler  
 `result`  
 Gereklidir. Herhangi bir `Boolean` veya sayısal değişken. Boolean karşılaştırma için `result` iki değerin mantıksal dışlamasıdır (dışlamalı mantıksal ayırıcı) `Boolean` . Bit düzeyinde işlemler için `result` iki sayısal bit deseninin bit düzeyinde dışlamasını (dışlayıcı bit düzeyinde ayırıcı) temsil eden sayısal bir değerdir.  
  
 `expression1`  
 Gereklidir. Herhangi bir `Boolean` veya sayısal ifade.  
  
 `expression2`  
 Gereklidir. Herhangi bir `Boolean` veya sayısal ifade.  
  
## <a name="remarks"></a>Açıklamalar  
 Boolean karşılaştırma için, `result` `True` ve yalnızca tam olarak bir tane olarak `expression1` `expression2` değerlendirilir `True` . Diğer bir deyişle, ve yalnızca Eğer `expression1` ve `expression2` ters değerler olarak değerlendirilir `Boolean` . Aşağıdaki tabloda nasıl belirlendiği gösterilmektedir `result` .  
  
|İse `expression1`|Ve `expression2`|`result`Öğesinin değeri|  
|-------------------------|--------------------------|------------------------------|  
|`True`|`True`|`False`|  
|`True`|`False`|`True`|  
|`False`|`True`|`True`|  
|`False`|`False`|`False`|  
  
> [!NOTE]
> Boole karşılaştırmasına, `Xor` işleç her zaman her iki ifadeyi değerlendirir ve bu da yordam çağrıları yapmayı içerebilir. Her `Xor` iki işlenenden de her zaman bağlı olduğundan, için bir kısa devre temelli karşılık yoktur. *Kısa* devre mantıksal işleçler için bkz. [AndAlso Işleci](andalso-operator.md) ve [orelsa işleci](orelse-operator.md).  
  
 Bit düzeyinde işlemler için, `Xor` işleç iki sayısal ifadede aynı şekilde konumlandırılmış bitlerin bit düzeyinde karşılaştırmasını gerçekleştirir ve karşılık gelen biti `result` aşağıdaki tabloya göre ayarlar.  
  
|Eğer bit `expression1` ise|Ve bit `expression2` ,|`result`İçindeki bit|  
|--------------------------------|---------------------------------|----------------------------|  
|1|1|0|  
|1|0|1|  
|0|1|1|  
|0|0|0|  
  
> [!NOTE]
> Mantıksal ve bit düzeyinde işleçler diğer aritmetik ve ilişkisel işleçlerden daha düşük önceliğe sahip olduğundan, doğru yürütmeyi sağlamak için herhangi bir bit düzeyinde işlemin parantez içine alınması gerekir.  
  
 Örneğin, 5 `Xor` 3, 6 ' dır. Bunun neden olduğunu görmek için, 5 ve 3 ' ü ikili gösterimlerine, 101 ve 011 dönüştürün. Ardından önceki tabloyu kullanarak 101 XOR 011 'in 6 ondalık sayının ikili temsili olan 110 olduğunu öğrenin.  
  
## <a name="data-types"></a>Veri Türleri  
 İşlenenler bir `Boolean` ifadeden ve bir sayısal ifadeden oluşur Visual Basic, `Boolean` ifadeyi sayısal bir değere dönüştürür (– 1 `True` ve için 0 `False` ) ve bit düzeyinde bir işlem gerçekleştirir.  
  
 Bir `Boolean` karşılaştırma için sonucun veri türü olur `Boolean` . Bit düzeyinde karşılaştırma için, sonuç veri türü ve veri türleri için uygun sayısal bir türdür `expression1` `expression2` . [Işleç sonuçlarının veri türlerinde](data-types-of-operator-results.md)"Ilişkisel ve bit düzeyinde karşılaştırmalar" tablosuna bakın.  
  
## <a name="overloading"></a>Aşırı Yükleme  
 `Xor`İşleç *aşırı*yüklenebilir, yani bir işlenen bu sınıf veya yapının türüne sahip olduğunda bir sınıf veya yapının davranışını yeniden tanımlayabileceği anlamına gelir. Kodunuz böyle bir sınıf veya yapıda bu işleci kullanıyorsa, yeniden tanımlanmış davranışını anladığınızdan emin olun. Daha fazla bilgi için bkz. [operatör yordamları](../../programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, `Xor` iki ifadeye mantıksal dışlama (dışlamalı mantıksal ayırıcı) gerçekleştirmek için işlecini kullanır. Sonuç, `Boolean` ifadelerden tam olarak bir tane olup olmadığını temsil eden bir değerdir `True` .  
  
 [!code-vb[VbVbalrOperators#40](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#40)]  
  
 Önceki örnek `False` sırasıyla,, ve sonuçlarını üretir `True` `False` .  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, `Xor` iki sayısal ifadenin ayrı bitleri üzerinde mantıksal dışlama (dışlamalı mantıksal ayırıcı) gerçekleştirmek için işlecini kullanır. Sonuç düzenindeki bit, işlenenlerde karşılık gelen bir bitlerin tam olarak 1 olarak ayarlanması halinde ayarlanır.  
  
 [!code-vb[VbVbalrOperators#41](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#41)]  
  
 Önceki örnek sırasıyla 2, 12 ve 14 sonuçlarını üretir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Mantıksal/Bit Düzeyinde İşleçler (Visual Basic)](logical-bitwise-operators.md)
- [Visual Basic'de İşleç Önceliği](operator-precedence.md)
- [İşlevselliğe Göre Listelenmiş İşleçler](operators-listed-by-functionality.md)
- [Visual Basic'de Mantıksal ve Bit Düzeyinde İşleçler](../../programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
