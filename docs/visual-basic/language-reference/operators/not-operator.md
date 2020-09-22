---
title: Not İşleci
ms.date: 07/20/2015
f1_keywords:
- vb.Not
helpviewer_keywords:
- Boolean expressions, negating
- operators [Visual Basic], bitwise
- negation operator [Visual Basic]
- inverse bit values in variables [Visual Basic]
- bitwise operators [Visual Basic], NOT operator
- bitwise comparison [Visual Basic]
- Not operator [Visual Basic]
- logical negation
- operators [Visual Basic], negation
ms.assetid: 8f2ea83c-d2ed-480a-a474-3042a1cad9b5
ms.openlocfilehash: 7d0beea16a2ac00be090c6a241f9790a0ba33390
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90874798"
---
# <a name="not-operator-visual-basic"></a>Not İşleci (Visual Basic)

Bir ifadede mantıksal Olumsuzlaştırma `Boolean` veya sayısal ifadede bit tabanlı Olumsuzlaştırma gerçekleştirir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```vb  
result = Not expression  
```  
  
## <a name="parts"></a>Bölümler  

 `result`  
 Gereklidir. Herhangi bir `Boolean` veya sayısal ifade.  
  
 `expression`  
 Gereklidir. Herhangi bir `Boolean` veya sayısal ifade.  
  
## <a name="remarks"></a>Açıklamalar  

 `Boolean`İfadeler için aşağıdaki tabloda nasıl `result` belirlendiği gösterilmektedir.  
  
|İse `expression`|`result`Öğesinin değeri|  
|------------------------|------------------------------|  
|`True`|`False`|  
|`False`|`True`|  
  
 Sayısal ifadeler için işleç, `Not` herhangi bir sayısal ifadenin bit değerlerini tersine çevirir ve karşılık gelen biti `result` aşağıdaki tabloya göre ayarlar.  
  
|Eğer bit `expression` ise|`result`İçindeki bit|  
|-------------------------------|----------------------------|  
|1|0|  
|0|1|  
  
> [!NOTE]
> Mantıksal ve bit düzeyinde işleçler diğer aritmetik ve ilişkisel işleçlerden daha düşük önceliğe sahip olduğundan, doğru yürütmeyi sağlamak için herhangi bir bit düzeyinde işlemin parantez içine alınması gerekir.  
  
## <a name="data-types"></a>Veri Türleri  

 Boolean Olumsuzlaştırma için sonucun veri türü olur `Boolean` . Bit düzeyinde olumsuzlama için sonuç veri türü, ile aynıdır `expression` . Ancak, ifadesi ise `Decimal` sonuç olur `Long` .  
  
## <a name="overloading"></a>Aşırı Yükleme  

 `Not`İşleç *aşırı*yüklenebilir, yani işleneni Bu sınıf veya yapının türüne sahip olduğunda bir sınıf veya yapının davranışını yeniden tanımlayabileceği anlamına gelir. Kodunuz böyle bir sınıf veya yapıda bu işleci kullanıyorsa, yeniden tanımlanmış davranışını anladığınızdan emin olun. Daha fazla bilgi için bkz. [operatör yordamları](../../programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Örnek  

 Aşağıdaki örnek, `Not` bir ifadede mantıksal olumsuzlama gerçekleştirmek için işlecini kullanır `Boolean` . Sonuç, `Boolean` ifadenin değerinin ters çevrilme değerini temsil eden bir değerdir.  
  
 [!code-vb[VbVbalrOperators#33](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#33)]  
  
 Yukarıdaki örnek `False` sırasıyla ve, sonuçları üretir `True` .  
  
## <a name="example"></a>Örnek  

 Aşağıdaki örnek, `Not` bir sayısal ifadenin ayrı bitlerinin mantıksal olumsuzunu gerçekleştirmek için işlecini kullanır. Sonuç deseninin biti, işaret biti dahil olmak üzere işlenen deseninin karşılık gelen bitin ters olarak ayarlanır.  
  
 [!code-vb[VbVbalrOperators#34](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#34)]  
  
 Yukarıdaki örnek sırasıyla – 11, – 9 ve – 7 sonuçlarını üretir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Mantıksal/Bit Düzeyinde İşleçler (Visual Basic)](logical-bitwise-operators.md)
- [Visual Basic'de İşleç Önceliği](operator-precedence.md)
- [İşlevselliğe Göre Listelenmiş İşleçler](operators-listed-by-functionality.md)
- [Visual Basic'de Mantıksal ve Bit Düzeyinde İşleçler](../../programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
