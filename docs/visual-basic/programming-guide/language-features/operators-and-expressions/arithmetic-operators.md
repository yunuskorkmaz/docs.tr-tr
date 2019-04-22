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
ms.openlocfilehash: 635c791f81107a1800e2ef381f6bea78cbc18e18
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "58820782"
---
# <a name="arithmetic-operators-in-visual-basic"></a>Visual Basic'de Aritmetik İşleçler
Aritmetik işleçler değişmez değerleri, değişkenleri, diğer ifadeler, işlevi ve özellik çağrılarını ve sabitleri tarafından temsil edilen sayısal değerleri hesaplama ilgili alışık olduğunuz aritmetik işlemleri çoğunu gerçekleştirmek için kullanılır. Ayrıca aritmetik sınıflandırılmış işlenenden tek bit düzeyinde işlem ve bunların bit düzenleri sola veya sağa kaydırma bit kaydırma işleçleri şunlardır.  
  
## <a name="arithmetic-operations"></a>Aritmetik işlemler  
 İki değer ile birlikte bir ifadede ekleyebileceğiniz [+ işleci](../../../../visual-basic/language-reference/operators/addition-operator.md), ya da başka birinden çıkarma [-işleci (Visual Basic)](../../../../visual-basic/language-reference/operators/subtraction-operator.md), aşağıdaki örnekte de gösterildiği gibi.  
  
 [!code-vb[VbVbalrOperators#57](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#57)]  
  
 Değilleme de kullanır [-işleci (Visual Basic)](../../../../visual-basic/language-reference/operators/subtraction-operator.md), ancak yalnızca bir işlenen, aşağıdaki örnek gösterir.  
  
 [!code-vb[VbVbalrOperators#58](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#58)]  
  
 Çarpma ve bölme kullanım [* işleci](../../../../visual-basic/language-reference/operators/multiplication-operator.md) ve [/ işleci (Visual Basic)](../../../../visual-basic/language-reference/operators/floating-point-division-operator.md), sırasıyla aşağıdaki örnekte de gösterildiği gibi.  
  
 [!code-vb[VbVbalrOperators#59](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#59)]  
  
 Üs kullanır [^ işleci](../../../../visual-basic/language-reference/operators/exponentiation-operator.md), aşağıdaki örnekte de gösterildiği gibi.  
  
 [!code-vb[VbVbalrOperators#60](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#60)]  
  
 Tamsayı bölme yazımının kullanarak [\ işleci (Visual Basic)](../../../../visual-basic/language-reference/operators/integer-division-operator.md). Sayının tamsayı bölme döndürür, diğer bir deyişle, sayısını temsil eden tamsayı bölen bir hatırlatıcı göz önüne alarak olmadan bölünen bölebilirsiniz. Bölen hem de Tamsayı türünde olması gerekir (`SByte`, `Byte`, `Short`, `UShort`, `Integer`, `UInteger`, `Long`, ve `ULong`) için bu işleci. Diğer tüm türlerin bir integral türe önce dönüştürülmelidir. Aşağıdaki örnek, Tamsayı bölme gösterir.  
  
 [!code-vb[VbVbalrOperators#61](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#61)]  
  
 Modulus aritmetik kullanarak gerçekleştirilir [Mod işleci](../../../../visual-basic/language-reference/operators/mod-operator.md). Bu işleç kalanı bölen bölünen bölme işleminden sayısı bir tamsayı döndürür. Bölen hem bölünen integral türleri ise, döndürülen değer tam sayı. Bölen ve bölünen kayan nokta türleri ise, döndürülen değer aynı zamanda kayan nokta. Aşağıdaki örnek, bu davranış gösterir.  
  
 [!code-vb[VbVbalrOperators#62](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#62)]  
  
 [!code-vb[VbVbalrOperators#63](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#63)]  
  
### <a name="attempted-division-by-zero"></a>Denenen sıfıra bölme  
 Sıfıra bölme, söz konusu veri türlerine bağlı olarak farklı sonuçlar sahiptir. İntegral bulunduğu (`SByte`, `Byte`, `Short`, `UShort`, `Integer`, `UInteger`, `Long`, `ULong`), [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] oluşturur bir <xref:System.DivideByZeroException> özel durum. Bölme işlemleri, `Decimal` veya `Single` veri türü [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] ayrıca oluşturur bir <xref:System.DivideByZeroException> özel durum.  
  
 Kayan nokta bölümler ilgili olarak `Double` veri türü, hiçbir özel durum ve sonucu temsil eden sınıf üyesidir <xref:System.Double.NaN>, <xref:System.Double.PositiveInfinity>, veya <xref:System.Double.NegativeInfinity>bölünen bağlı olarak. Aşağıdaki tabloda özetlenmiştir bölmek çalışılırken çeşitli sonuçlarını bir `Double` sıfır değeri.  
  
|Bölünen veri türü|Bölen veri türü|Bölünen değer|Sonuç|  
|---|---|---|---|  
|`Double`|`Double`|0|<xref:System.Double.NaN> (matematiksel olarak tanımlanmış bir sayı değil)|  
|`Double`|`Double`|> 0|<xref:System.Double.PositiveInfinity>|  
|`Double`|`Double`|\< 0|<xref:System.Double.NegativeInfinity>|  
  
 Catch ne zaman bir <xref:System.DivideByZeroException> özel durum, bu işleme yardımcı olacak üyeleri kullanabilirsiniz. Örneğin, <xref:System.Exception.Message%2A> özelliği, özel durum için ileti metni içerir. Daha fazla bilgi için [deneyin... Catch... Finally deyimini](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).  
  
## <a name="bit-shift-operations"></a>Bit kaydırma işleçlerini  
 Bit kaydırma işlemi bir bit desenine aritmetik kaydırma uygular. Sağ işlenen deseni kaydırmak için konum sayısına belirtirken deseni sol işlenende yer alır. Soldan sağa düzen kaydırma [>> işleci](../../../../visual-basic/language-reference/operators/right-shift-operator.md) veya sol [<< işleci](../../../../visual-basic/language-reference/operators/left-shift-operator.md).  
  
 Desen işlenen veri türünde olmalıdır `SByte`, `Byte`, `Short`, `UShort`, `Integer`, `UInteger`, `Long`, veya `ULong`. Kaydırma miktarı işlenen veri türünde olmalıdır `Integer` veya genişlemesi gerekir `Integer`.  
  
 Sonucu ucunu kaydırılacak bitlerin diğer sonunda yeniden girmesini yok anlamına gelir özelliği aritmetik kaydırmalar döngüsel, değildir. Bir kaydırma işleci boşaltılmış bit konumları gibi ayarlayın:  
  
-   aritmetik sola kaydırma için 0  
  
-   0 için bir pozitif sayı aritmetik sağa kaydırma  
  
-   İmzasız veri türü aritmetik sağa kaydırma için 0 (`Byte`, `UShort`, `UInteger`, `ULong`)  
  
-   aritmetik sağa kaydırma, negatif bir sayı 1 (`SByte`, `Short`, `Integer`, veya `Long`)  
  
 Aşağıdaki örnek kaydırır bir `Integer` sağa ve sola değeri.  
  
 [!code-vb[VbVbalrOperators#64](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#64)]  
  
 Aritmetik kaydırmalar hiçbir zaman taşması özel durumları oluşturur.  
  
## <a name="bitwise-operations"></a>Bit düzeyinde işlemler  
 Mantıksal işleçler olan yanı sıra `Not`, `Or`, `And`, ve `Xor` de sayısal değerleri üzerinde kullanıldığında bit düzeyinde aritmetik işlemleri. Daha fazla bilgi için bkz: "Bit düzeyinde işlemler" [mantıksal ve bit düzeyinde işleçler Visual Basic'te](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md).  
  
## <a name="type-safety"></a>Tür güvenliği  
 İşlenenler, normalde aynı türde olmalıdır. Örneğin eklenmesiyle yapıyorsanız, bir `Integer` değişken, onu diğerine eklemeniz `Integer` değişkeni ve ata sonucu türünde bir değişkene `Integer` de.  
  
 Tek yönlü iyi tür kullanımı uyumlu olmak için kodlama yöntemi kullanmaktır [Option Strict deyimi](../../../../visual-basic/language-reference/statements/option-strict-statement.md). Ayarlarsanız `Option Strict On`, Visual Basic otomatik olarak gerçekleştirir *tür kullanımı uyumlu* dönüşümler. Eklemeyi denerseniz, örneğin, bir `Integer` değişkenini bir `Double` değişkeni ve değer atayın bir `Double` değişken, işlem normalde, çünkü devam ettiği bir `Integer` değer dönüştürülebilir `Double` veri kaybı olmadan. Güvenli olmayan tür dönüştürme, diğer yandan, bir derleyici hatası ile neden `Option Strict On`. Eklemeyi denerseniz, örneğin, bir `Integer` değişkenini bir `Double` değişkeni ve değer atayın bir `Integer` değişken, bir derleyici hatası, çünkü sonuçları bir `Double` değişkeni örtük olarak dönüştürülemez yazın `Integer`.  
  
 Ayarlarsanız `Option Strict Off`, ancak beklenmeyen veri veya duyarlık kaybına neden olabilir, ancak Visual Basic, gerçekleşmesi örtük daraltma dönüştürmelerini tanır. Bu nedenle, kullandığınız olan öneririz `Option Strict On` üretim kodu yazarken. Daha fazla bilgi için [Widening ve daraltma dönüşümleri](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Aritmetik İşleçler](../../../../visual-basic/language-reference/operators/arithmetic-operators.md)
- [Bit Kaydırma İşleçleri](../../../../visual-basic/language-reference/operators/bit-shift-operators.md)
- [Visual Basic'de Karşılaştırma işleçleri](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)
- [Visual Basic'de birleştirme işleçleri](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/concatenation-operators.md)
- [Visual Basic'de mantıksal ve bit düzeyinde işleçler](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
- [İşleçlerin Etkili Bileşimi](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/efficient-combination-of-operators.md)
