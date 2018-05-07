---
title: Visual Basic'de Aritmetik İşleçler
ms.date: 07/20/2015
helpviewer_keywords:
- type safety
- operators [Visual Basic], bitwise
- operators [Visual Basic], bit-shift
- bitwise operators [Visual Basic]
- bit-shift operators [Visual Basic]
- zero, division by zero
- operators [Visual Basic], arithmetic
- division [Visual Basic], by zero
- Visual Basic code, operators
- arithmetic operators [Visual Basic], about arithmetic operators
ms.assetid: 325dac7a-ea4f-41d5-8b48-f6e904211569
ms.openlocfilehash: cd66d08eba973a796472fcbd40a6a84edbbb62ae
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="arithmetic-operators-in-visual-basic"></a>Visual Basic'de Aritmetik İşleçler
Aritmetik işleçler değişmez değerleri, değişkenleri, diğer ifadeler, işlevi ve özellik çağrılarını ve sabitler tarafından temsil edilen sayısal değerleri hesaplama ile ilgili bilinen aritmetik işlemler çoğunu gerçekleştirmek için kullanılır. Ayrıca aritmetik sınıflandırılmış işlenenler tek tek bit düzeyinde hareket ve bunların bit şekillerine sola veya sağa kaydırma bit kaydırma işleçleri var.  
  
## <a name="arithmetic-operations"></a>Aritmetik işlemler  
 İki değer ile birlikte bir ifadede ekleyebileceğiniz [+ işleci](../../../../visual-basic/language-reference/operators/addition-operator.md), veya başka bir çıkarma [-işleci (Visual Basic)](../../../../visual-basic/language-reference/operators/subtraction-operator.md), aşağıdaki örnekte gösterilmiştir.  
  
 [!code-vb[VbVbalrOperators#57](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/arithmetic-operators_1.vb)]  
  
 Değilleme de kullanır [-işleci (Visual Basic)](../../../../visual-basic/language-reference/operators/subtraction-operator.md), ancak yalnızca bir terimiyle aşağıdaki örnek olarak gösterilmiştir.  
  
 [!code-vb[VbVbalrOperators#58](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/arithmetic-operators_2.vb)]  
  
 Çarpma ve bölme kullanım [* işleci](../../../../visual-basic/language-reference/operators/multiplication-operator.md) ve [/ işleci (Visual Basic)](../../../../visual-basic/language-reference/operators/floating-point-division-operator.md), sırasıyla gibi aşağıdaki örnekte gösterilmiştir.  
  
 [!code-vb[VbVbalrOperators#59](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/arithmetic-operators_3.vb)]  
  
 Üs kullanan [^ işleci](../../../../visual-basic/language-reference/operators/exponentiation-operator.md), aşağıdaki örnekte gösterilmiştir.  
  
 [!code-vb[VbVbalrOperators#60](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/arithmetic-operators_4.vb)]  
  
 Tamsayı bölme gerçekleştirilir kullanarak [\ işleci (Visual Basic)](../../../../visual-basic/language-reference/operators/integer-division-operator.md). Sayının tamsayı bölme döndürür, diğer bir deyişle, sayısını temsil eden tamsayıyı bölen göz önünde bulundurarak herhangi kalanın olmadan bölünen bölebilirsiniz. Tam sayı türleri bölen ve bölünen olmalıdır (`SByte`, `Byte`, `Short`, `UShort`, `Integer`, `UInteger`, `Long`, ve `ULong`) bu işleç. Tüm diğer türleri tamsayı türü için öncelikle dönüştürülmesi gerekir. Aşağıdaki örnek, Tamsayı bölme gösterir.  
  
 [!code-vb[VbVbalrOperators#61](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/arithmetic-operators_5.vb)]  
  
 Modulus aritmetik kullanarak gerçekleştirilir [Mod işleci](../../../../visual-basic/language-reference/operators/mod-operator.md). Bu işleç kalanı bölen bölünen bölerek sonra sayısı bir tamsayı döndürür. Bölen ve bölünen tam sayı türleri ise, döndürülen değerin tam sayı. Bölen bölünen kayan nokta türleri ise, döndürülen değer de kayan nokta olur. Aşağıdaki örnek, bu davranış gösterir.  
  
 [!code-vb[VbVbalrOperators#62](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/arithmetic-operators_6.vb)]  
  
 [!code-vb[VbVbalrOperators#63](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/arithmetic-operators_7.vb)]  
  
### <a name="attempted-division-by-zero"></a>Denenen sıfıra  
 Sıfıra bölme söz konusu veri türlerine bağlı olarak farklı sonuçlar vardır. Tam sayı bölümler içinde (`SByte`, `Byte`, `Short`, `UShort`, `Integer`, `UInteger`, `Long`, `ULong`), [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] oluşturur bir <xref:System.DivideByZeroException> özel durum. Üzerinde bölme işlemlerinde `Decimal` veya `Single` veri türü, [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] de oluşturur bir <xref:System.DivideByZeroException> özel durum.  
  
 Kayan nokta bölümler ilgili olarak `Double` veri türü, hiçbir özel durum oluşur ve sonucu temsil eden sınıf üyesi olan <xref:System.Double.NaN>, <xref:System.Double.PositiveInfinity>, veya <xref:System.Double.NegativeInfinity>bölünen bağlı olarak. Aşağıdaki tabloda çeşitli bölmek çalışılıyor sonuçlarını özetler bir `Double` değeri sıfıra.  
  
|Bölünen veri türü|Bölen veri türü|Bölünen değeri|Sonuç|  
|---|---|---|---|  
|`Double`|`Double`|0|<xref:System.Double.NaN> (matematiksel olarak tanımlanan sayı değil)|  
|`Double`|`Double`|> 0|<xref:System.Double.PositiveInfinity>|  
|`Double`|`Double`|\< 0|<xref:System.Double.NegativeInfinity>|  
  
 Catch ne zaman bir <xref:System.DivideByZeroException> özel durum, bu işleme yardımcı olmak için üyeleri kullanabilirsiniz. Örneğin, <xref:System.Exception.Message%2A> özelliği, özel durum için ileti metni içerir. Daha fazla bilgi için bkz: [deneyin... Catch... Finally ifadesi](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).  
  
## <a name="bit-shift-operations"></a>Bit kaydırma işlemleri  
 Bit kaydırma işlemi bir bit desenine aritmetik kaydırma uygular. Sağdaki işlenen düzeni kaydırılacak konumlar sayısını belirtir sırada düzeni sol işleneni bulunur. Soldan sağa düzeni shift [>> işleci](../../../../visual-basic/language-reference/operators/right-shift-operator.md) veya sol [<< işleci](../../../../visual-basic/language-reference/operators/left-shift-operator.md).  
  
 Desen işlenen veri türünde olmalıdır `SByte`, `Byte`, `Short`, `UShort`, `Integer`, `UInteger`, `Long`, veya `ULong`. Shift tutar işlenen veri türünde olmalıdır `Integer` veya genişletmek gerekir `Integer`.  
  
 Aritmetik kaydırmalar sonucu ucunu gölgeye BITS diğer sonunda yeniden girmesini olmayan başka bir deyişle, döngüsel, değil. Bir kaydırma tarafından vacated bit konumları aşağıdaki gibi ayarlayın:  
  
-   aritmetik sola kaydırma için 0  
  
-   aritmetik sağa kaydırma pozitif bir sayı, 0  
  
-   İmzasız veri türünün aritmetik sağa kaydırma için 0 (`Byte`, `UShort`, `UInteger`, `ULong`)  
  
-   negatif bir sayı, aritmetik sağa kaydırma için 1 (`SByte`, `Short`, `Integer`, veya `Long`)  
  
 Aşağıdaki örnek kaydırır bir `Integer` sol ve sağ değer.  
  
 [!code-vb[VbVbalrOperators#64](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/arithmetic-operators_8.vb)]  
  
 Aritmetik kaydırmalar hiçbir zaman taşma özel durumları oluşturur.  
  
## <a name="bitwise-operations"></a>Bit düzeyinde işlemler  
 Mantıksal işleçler olan yanı sıra `Not`, `Or`, `And`, ve `Xor` de sayısal değerleri kullanıldığında Bitsel aritmetik gerçekleştirin. Daha fazla bilgi için bkz: "Bit düzeyinde işlemler" [mantıksal ve bit düzeyinde işleçler Visual Basic'te](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md).  
  
## <a name="type-safety"></a>Tür güvenliği  
 İşlenen normalde aynı türde olmalıdır. Örneğin, eklenmesiyle yapıyorsanız bir `Integer` değişken, onu diğerine eklemeniz `Integer` değişkeni ve atama sonucu türünde bir değişken `Integer` de.  
  
 Tek yönlü iyi tür kullanımı uyumlu emin olmak için yöntem kodlama kullanmaktır [Option Strict deyimi](../../../../visual-basic/language-reference/statements/option-strict-statement.md). Ayarlarsanız `Option Strict On`, Visual Basic otomatik olarak gerçekleştirir *tür kullanımı uyumlu* dönüşümler. Eklemeye çalışırsanız, örneğin, bir `Integer` için değişken bir `Double` değişkeni ve değer atadığınız bir `Double` değişken, işlemi normal olarak, çünkü devam eder bir `Integer` değer dönüştürülebilir `Double` veri kaybı olmadan. Türü güvensiz dönüştürme, diğer yandan derleyici hatası ile neden `Option Strict On`. Eklemeye çalışırsanız, örneğin, bir `Integer` için değişken bir `Double` değişkeni ve değer atadığınız bir `Integer` değişken, bir derleyici hatası, çünkü sonuçları bir `Double` değişkeni örtük olarak dönüştürülemiyor yazmak için `Integer`.  
  
 Ayarlarsanız `Option Strict Off`, beklenmeyen veri veya duyarlık kaybına neden olabilir ancak bununla birlikte, Visual Basic, gerçekleşmesi örtük daraltma dönüşümleri izin verir. Bu nedenle, kullanmanızı öneririz `Option Strict On` üretim kodu yazarken. Daha fazla bilgi için bkz: [Widening ve daraltma dönüşümleri](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Aritmetik İşleçler](../../../../visual-basic/language-reference/operators/arithmetic-operators.md)  
 [Bit Kaydırma İşleçleri](../../../../visual-basic/language-reference/operators/bit-shift-operators.md)  
 [Visual Basic'de Karşılaştırma işleçleri](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)  
 [Visual Basic'de birleştirme işleçleri](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/concatenation-operators.md)  
 [Visual Basic'de mantıksal ve bit düzeyinde işleçler](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)  
 [İşleçlerin Etkili Bileşimi](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/efficient-combination-of-operators.md)
