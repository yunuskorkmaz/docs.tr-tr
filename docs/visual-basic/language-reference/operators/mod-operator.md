---
title: Mod İşleci (Visual Basic)
ms.date: 04/24/2018
f1_keywords:
- vb.Mod
helpviewer_keywords:
- remainder (Mod operator)
- division operator [Visual Basic], Mod operator
- modulus operator [Visual Basic], Visual Basic
- Mod operator [Visual Basic]
- operators [Visual Basic], division
- arithmetic operators [Visual Basic], Mod
- math operators [Visual Basic]
ms.assetid: 6ff7e40e-cec8-4c77-bff6-8ddd2791c25b
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5120823f4e001fc3aff71f267176311e2465597a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="mod-operator-visual-basic"></a>Mod işleci (Visual Basic)
İki sayıyı böler ve yalnızca kalanı döndürür.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
number1 Mod number2  
```  
  
## <a name="parts"></a>Bölümler  
 `number1`  
 Gerekli. Herhangi bir sayısal ifade.  
  
 `number2`  
 Gerekli. Herhangi bir sayısal ifade.  
  
## <a name="supported-types"></a>Desteklenen türler  
 Tüm sayısal türler. Bu imzasız ve kayan nokta türleri içerir ve `Decimal`.  
  
## <a name="result"></a>Sonuç

Sonra geri kalan sonucudur `number1` bölünür `number2`. Örneğin, ifade `14 Mod 4` 2 olarak değerlendirir.  

> [!NOTE]
> Arasında bir fark *kalan* ve *modulus* negatif sayılar için farklı sonuçlarla matematik içinde. `Mod` Visual Basic'te .NET Framework işleci `op_Modulus` işleci ve temel alınan [rem]<xref:System.Reflection.Emit.OpCodes.Rem> IL yönerge tüm kalan işlemi gerçekleştirin.

Sonucunu bir `Mod` işlemi korur bölünen oturum `number1`, ve olumlu veya olumsuz olabilir. Sonucu her zaman aralığı içinde değil (-`number2`, `number2`), özel. Örneğin:

```vb
Public Module Example
   Public Sub Main()
      Console.WriteLine($" 8 Mod  3 = {8 Mod 3}")
      Console.WriteLine($"-8 Mod  3 = {-8 Mod 3}")
      Console.WriteLine($" 8 Mod -3 = {8 Mod -3}")
      Console.WriteLine($"-8 Mod -3 = {-8 Mod -3}")
   End Sub
End Module
' The example displays the following output:
'       8 Mod  3 = 2
'      -8 Mod  3 = -2
'       8 Mod -3 = 2
'      -8 Mod -3 = -2
```

## <a name="remarks"></a>Açıklamalar  
 Her iki `number1` veya `number2` bir kayan nokta bölme kayan nokta kalanı döndürülen değerdir. Sonuç veri türü veri türlerini bölme kaynaklanan tüm olası değerler tutabileceği en küçük veri türüdür `number1` ve `number2`.  
  
 Varsa `number1` veya `number2` değerlendiren [hiçbir şey](../../../visual-basic/language-reference/nothing.md), sıfır olarak kabul edilir.  
  
 İlgili işleçleri aşağıdakileri içerir:  
  
-   [\ İşleci (Visual Basic)](../../../visual-basic/language-reference/operators/integer-division-operator.md) bir bölümünün tamsayı bölümü döndürür. Örneğin, ifade `14 \ 4` 3 olarak değerlendirir.  
  
-   [/ İşleci (Visual Basic)](../../../visual-basic/language-reference/operators/floating-point-division-operator.md) bir kayan noktalı sayı olarak kalan dahil olmak üzere tam sayının döndürür. Örneğin, ifade `14 / 4` 3.5 değerlendirir.  
  
## <a name="attempted-division-by-zero"></a>Denenen sıfıra  
 Varsa `number2` sıfır olarak davranışını değerlendirir `Mod` işleci işlenen veri türüne bağlıdır. Tamsayı bölme oluşturur bir <xref:System.DivideByZeroException> özel durum. Kayan nokta bölme döndürür <xref:System.Double.NaN>.  
  
## <a name="equivalent-formula"></a>Eşdeğer formülü  
 İfade `a Mod b` da aşağıdaki formüller eşdeğerdir:  
  
 `a - (b * (a \ b))`  
  
 `a - (b * Fix(a / b))`  
  
## <a name="floating-point-imprecision"></a>Kayan nokta imprecision  
 Kayan nokta sayıları ile çalışırken, bunlar her zaman kesin bir ondalık gösterimi belleğe sahip olmadığını unutmayın. Değer karşılaştırması gibi bazı işlemleri alanından bu beklenmeyen sonuçlara neden olabilir ve `Mod` işleci. Daha fazla bilgi için bkz: [veri türleri sorunlarını giderme](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md).  
  
## <a name="overloading"></a>Aşırı Yükleme  
 `Mod` İşleci olabilir *aşırı*, yani bir sınıf veya yapı davranışını tanımlayabilirsiniz. Kodunuzu geçerliyse `Mod` bir sınıf ya da böyle bir aşırı içerir yapısı bir örneğine yeniden tanımlanan davranışını anladığınızdan emin olun. Daha fazla bilgi için bkz: [işleç yordamları](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek kullanır `Mod` işleci iki sayı bölme ve yalnızca kalanı döndürür. Her iki sayı kayan noktalı sayı ise kalan temsil eden bir kayan noktalı sayı sonucudur.  
  
 [!code-vb[VbVbalrOperators#31](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/mod-operator_1.vb)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, kayan nokta işlenenleri imprecision olası gösterir. İşlenen ilk deyiminde olan `Double`, ve 0.2 sonsuz yinelenen bir ikili Kesir 0.20000000000000001 depolanan değeri. İkinci deyiminde sabit değer türü karakteri `D` her iki işlenen zorlar `Decimal`, ve 0.2 kesin bir gösterimi.  
  
 [!code-vb[VbVbalrOperators#32](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/mod-operator_2.vb)]  
  
## <a name="see-also"></a>Ayrıca bkz.  
 <xref:Microsoft.VisualBasic.Conversion.Int%2A>  
 <xref:Microsoft.VisualBasic.Conversion.Fix%2A>  
 [Aritmetik İşleçler](../../../visual-basic/language-reference/operators/arithmetic-operators.md)  
 [Visual Basic'de İşleç önceliği](../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [İşlevselliğe Göre Listelenmiş İşleçler](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)  
 [Veri Türü Sorunlarını Giderme](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)  
 [Visual Basic'de aritmetik işleçler](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)  
 [\ İşleci (Visual Basic)](../../../visual-basic/language-reference/operators/integer-division-operator.md)
