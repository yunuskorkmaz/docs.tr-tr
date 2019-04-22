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
ms.openlocfilehash: b127c50f3319d4fe7c4890fc3bffb295baa37466
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "58840178"
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
 Tüm sayısal türler. Bu imzalanmamış ve kayan nokta türlerini içerir ve `Decimal`.  
  
## <a name="result"></a>Sonuç

Sonra kalan sonucudur `number1` bölünür `number2`. Örneğin, ifade `14 Mod 4` 2 olarak değerlendirilir.  

> [!NOTE]
> Arasında bir fark *kalan* ve *modulus* negatif sayılar için farklı sonuçlarla Matematikte. `Mod` İşleci Visual Basic'te .NET Framework `op_Modulus` işleci ve arka plandaki [rem](<xref:System.Reflection.Emit.OpCodes.Rem>) IL yönergesinin tüm kalan işlemi gerçekleştirin.

Sonucu bir `Mod` işlemi korur bölünen sayının işaretini `number1`, ve pozitif veya negatif olabilir. Her zaman aralığında sonucudur (-`number2`, `number2`), özel. Örneğin:

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
 Ya da `number1` veya `number2` bir kayan nokta kayan nokta bölme kalanını döndürülen değerdir. Sonuç veri türü, veri türlerini bölme kaynaklanan tüm olası değerlerini tutabilecek en küçük veri türüdür `number1` ve `number2`.  
  
 Varsa `number1` veya `number2` değerlendiren [hiçbir şey](../../../visual-basic/language-reference/nothing.md), sıfır olarak kabul edilir.  
  
 İlgili işleçler şunlardır:  
  
-   [\ İşleci (Visual Basic)](../../../visual-basic/language-reference/operators/integer-division-operator.md) bölme işleminin tamsayı bölümünü döndürür. Örneğin, ifade `14 \ 4` 3 olarak değerlendirir.  
  
-   [/ İşleci (Visual Basic)](../../../visual-basic/language-reference/operators/floating-point-division-operator.md) bir kayan noktalı sayı olarak kalan dahil olmak üzere tam kalanını döndürür. Örneğin, ifade `14 / 4` 3.5 için değerlendirir.  
  
## <a name="attempted-division-by-zero"></a>Denenen sıfıra bölme  
 Varsa `number2` sıfır olarak davranışını değerlendirilen `Mod` işleci, işlenen veri türüne bağlıdır. Bir tamsayı bölme oluşturur bir <xref:System.DivideByZeroException> özel durum. Kayan nokta bölme döndürür <xref:System.Double.NaN>.  
  
## <a name="equivalent-formula"></a>Eşdeğer formülü  
 İfade `a Mod b` şu formüllerden birini eşdeğerdir:  
  
 `a - (b * (a \ b))`  
  
 `a - (b * Fix(a / b))`  
  
## <a name="floating-point-imprecision"></a>Kayan nokta kesinlik eksikliği  
 Kayan noktalı sayı ile çalıştığınızda, bunlar her zaman kesin bir ondalık gösterim bellekte olmadığını unutmayın. Bu değer karşılaştırması gibi bazı işlemleri öğesinden beklenmeyen sonuçlara açabilir ve `Mod` işleci. Daha fazla bilgi için [veri türleri sorunlarını giderme](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md).  
  
## <a name="overloading"></a>Aşırı Yükleme  
 `Mod` İşleci olabilir *aşırı*, yani bir sınıf veya yapı davranışını tanımlayabilirsiniz. Kodunuzu geçerliyse `Mod` bir sınıf veya yapı gibi bir aşırı yüklemeyi içeren bir örneği için yeniden tanımlanan davranışını anladığınızdan emin olun. Daha fazla bilgi için [işleç yordamları](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte `Mod` işleci iki sayı bölme ve yalnızca kalanı döndürür. Ya da bir kayan noktalı sayı olan, kalan temsil eden bir kayan noktalı sayı sonucudur.  
  
 [!code-vb[VbVbalrOperators#31](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#31)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, kayan nokta işlenenler kesinlik eksikliği olası gösterir. İlk ifade, işlenenin olduğu `Double`, ve 0.2 sonsuz yinelenen bir ikili Kesir 0.20000000000000001 depolanan değerine sahip. İkinci ifadede, değişmez değer türü karakteri `D` iki işlenen de zorlar `Decimal`, ve 0.2 kesin bir gösterimi.  
  
 [!code-vb[VbVbalrOperators#32](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#32)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualBasic.Conversion.Int%2A>
- <xref:Microsoft.VisualBasic.Conversion.Fix%2A>
- [Aritmetik İşleçler](../../../visual-basic/language-reference/operators/arithmetic-operators.md)
- [Visual Basic'de İşleç önceliği](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [İşlevselliğe Göre Listelenmiş İşleçler](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [Veri Türü Sorunlarını Giderme](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)
- [Visual Basic'de aritmetik işleçler](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
- [\ İşleci (Visual Basic)](../../../visual-basic/language-reference/operators/integer-division-operator.md)
