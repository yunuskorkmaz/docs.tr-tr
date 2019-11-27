---
title: Aritmetik İşleçler
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
ms.openlocfilehash: 8ded8d7111bd37cf8762a202b728e814aa5a082b
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74352654"
---
# <a name="arithmetic-operators-in-visual-basic"></a>Visual Basic'de Aritmetik İşleçler
Aritmetik işleçler, değişmez değerler, değişkenler, diğer ifadeler, işlev ve özellik çağrıları ve sabitler tarafından temsil edilen sayısal değerlerin hesaplanmasını içeren tanıdık aritmetik işlemlerin çoğunu gerçekleştirmek için kullanılır. Ayrıca, Aritmetik işleçlerle sınıflandırılan bit kaydırma işleçleridir. Bu, işlenen ayrı bitlerin düzeyine göre hareket ederler ve bit desenlerini sola veya sağa kaydıramalıdır.  
  
## <a name="arithmetic-operations"></a>Aritmetik Işlemler  
 Aşağıdaki örnekte gösterildiği gibi, bir ifadeye [+ işleciyle](../../../../visual-basic/language-reference/operators/addition-operator.md)birlikte iki değer ekleyebilir veya [-işleci (Visual Basic)](../../../../visual-basic/language-reference/operators/subtraction-operator.md)ile diğerine çıkarabilirsiniz.  
  
 [!code-vb[VbVbalrOperators#57](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#57)]  
  
 Değilleme Ayrıca, aşağıdaki örnekte gösterildiği gibi yalnızca bir işlenen ile [-işleci (Visual Basic)](../../../../visual-basic/language-reference/operators/subtraction-operator.md)kullanır.  
  
 [!code-vb[VbVbalrOperators#58](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#58)]  
  
 Çarpma ve bölme, aşağıdaki örnekte gösterildiği gibi, sırasıyla [* işlecini](../../../../visual-basic/language-reference/operators/multiplication-operator.md) ve [/işlecini (Visual Basic)](../../../../visual-basic/language-reference/operators/floating-point-division-operator.md)kullanır.  
  
 [!code-vb[VbVbalrOperators#59](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#59)]  
  
 Üs, aşağıdaki örnekte gösterildiği gibi [^ işlecini](../../../../visual-basic/language-reference/operators/exponentiation-operator.md)kullanır.  
  
 [!code-vb[VbVbalrOperators#60](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#60)]  
  
 Tamsayı bölme, [\ işleci (Visual Basic)](../../../../visual-basic/language-reference/operators/integer-division-operator.md)kullanılarak yürütülür. Tamsayı bölme bölümü, diğer bir deyişle, bölen herhangi bir geri dönüş yapmadan bölünmeye bölüneceği sayı sayısını temsil eden tamsayıdır. Bölen ve bölünen öğelerinin her ikisi de bu operatör için tamsayı türleri (`SByte`, `Byte`, `Short`, `UShort`, `Integer`, `UInteger`, `Long`ve `ULong`) olmalıdır. Tüm diğer türler önce bir integral türüne dönüştürülmelidir. Aşağıdaki örnek, tamsayı bölümünü gösterir.  
  
 [!code-vb[VbVbalrOperators#61](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#61)]  
  
 Mod aritmetik, [Mod işleci](../../../../visual-basic/language-reference/operators/mod-operator.md)kullanılarak gerçekleştirilir. Bu işleç, böleni bir integral sayısına bölündükten sonra kalanı döndürür. Hem bölen hem de bölünen tamsayı türlerdir, döndürülen değer integral olur. Bölen ve bölünen kayan nokta türüyorsa, döndürülen değer de kayan noktalı olur. Aşağıdaki örnek bu davranışı gösterir.  
  
 [!code-vb[VbVbalrOperators#62](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#62)]  
  
 [!code-vb[VbVbalrOperators#63](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#63)]  
  
### <a name="attempted-division-by-zero"></a>Sıfıra bölme denendi  
 Sıfıra bölme, dahil edilen veri türlerine bağlı olarak farklı sonuçlara sahiptir. Tam sayı bölümleri (`SByte`, `Byte`, `Short`, `UShort`, `Integer`, `UInteger`, `Long`, `ULong`), .NET Framework bir <xref:System.DivideByZeroException> özel durumu oluşturur. `Decimal` veya `Single` veri türünde bölüm işlemlerinde .NET Framework Ayrıca bir <xref:System.DivideByZeroException> özel durumu oluşturur.  
  
 `Double` veri türünü içeren kayan nokta bölümleri içinde, hiçbir özel durum oluşturulmaz ve sonuç, bölünme göre <xref:System.Double.NaN>, <xref:System.Double.PositiveInfinity>veya <xref:System.Double.NegativeInfinity>temsil eden sınıf üyesidir. Aşağıdaki tabloda `Double` değeri sıfıra bölme girişimi çeşitli sonuçları özetlenmektedir.  
  
|Bölünen veri türü|Bölen veri türü|Bölünen değer|Sonuç|  
|---|---|---|---|  
|`Double`|`Double`|0|<xref:System.Double.NaN> (matematik yoluyla tanımlanmış bir sayı değil)|  
|`Double`|`Double`|> 0|<xref:System.Double.PositiveInfinity>|  
|`Double`|`Double`|\< 0|<xref:System.Double.NegativeInfinity>|  
  
 <xref:System.DivideByZeroException> bir özel durumu yakalarsanız, kendi üyelerini kullanarak bu uygulamayı işleyebilmeniz için kullanabilirsiniz. Örneğin, <xref:System.Exception.Message%2A> özelliği özel durum için ileti metnini barındırır. Daha fazla bilgi için bkz [. TRY... Yakala... Finally ekstresi](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).  
  
## <a name="bit-shift-operations"></a>Bit kaydırma Işlemleri  
 Bit kaydırma işlemi bir bit düzeninde aritmetik kaydırma gerçekleştirir. Model, sol taraftaki işlenende bulunur, ancak sağdaki işlenen, kalıbı kaydırmak için konumların sayısını belirtir. [> > işleci](../../../../visual-basic/language-reference/operators/right-shift-operator.md) veya [< < işleci](../../../../visual-basic/language-reference/operators/left-shift-operator.md)ile sola doğru bir düzende kaydırma yapabilirsiniz.  
  
 Düzenin işlenen veri türü `SByte`, `Byte`, `Short`, `UShort`, `Integer`, `UInteger`, `Long`veya `ULong`olmalıdır. SHIFT amount işlenenin veri türü `Integer` olmalı veya `Integer`olarak genişlemelidir.  
  
 Aritmetik vardiyalar dairesel değildir, bu da sonucun bir sonunun dışına sürüklenen bitlerin diğer uçta yeniden tanıtılmadığını gösterir. Bir kaydırmaya göre belirlenen bit konumları aşağıdaki gibi ayarlanır:  
  
- Aritmetik sola kaydırma için 0  
  
- pozitif bir sayının aritmetik sağ kaydırması için 0  
  
- işaretsiz bir veri türünün aritmetik sağ kaydırması için 0 (`Byte`, `UShort`, `UInteger`, `ULong`)  
  
- 1 negatif bir sayının aritmetik sağa kaydırılması (`SByte`, `Short`, `Integer`veya `Long`)  
  
 Aşağıdaki örnek, bir `Integer` değerini hem sol hem de sağ kaydırır.  
  
 [!code-vb[VbVbalrOperators#64](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#64)]  
  
 Aritmetik vardiyalar hiçbir şekilde taşma özel durumu oluşturmaz.  
  
## <a name="bitwise-operations"></a>Bit düzeyinde Işlemler  
 Mantıksal işleçler olmanın yanı sıra `Not`, `Or`, `And`ve `Xor` sayısal değerlerde kullanıldığında bit düzeyinde aritmetik da gerçekleştirir. Daha fazla bilgi için, [Visual Basic mantıksal ve bit düzeyinde işleçlerdeki](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)"bit düzeyinde işlemler" konusuna bakın.  
  
## <a name="type-safety"></a>Tür güvenliği  
 İşlenenler normalde aynı türde olmalıdır. Örneğin, bir `Integer` değişkenle birlikte ekleme yapıyorsanız, bunu başka bir `Integer` değişkenine eklemeniz gerekir ve sonucu da `Integer` türünde bir değişkene atamanız gerekir.  
  
 İyi tür açısından güvenli kodlama uygulaması sağlamanın bir yolu, [Strict deyimin seçeneğini](../../../../visual-basic/language-reference/statements/option-strict-statement.md)kullanmaktır. `Option Strict On`ayarlarsanız, Visual Basic otomatik olarak *tür kullanımı uyumlu* dönüşümler gerçekleştirir. Örneğin, bir `Double` değişkenine `Integer` değişken eklemeye ve değeri bir `Double` değişkenine atamaya çalışırsanız, bir `Integer` değeri veri kaybı olmadan `Double` olarak dönüştürülebildiğinden, işlem normal olarak devam eder. Tür-güvenli olmayan dönüşümler, diğer yandan `Option Strict On`bir derleyici hatasına neden olur. Örneğin, bir `Double` değişkenine `Integer` değişken eklemeye ve değeri bir `Integer` değişkenine atamaya çalışırsanız, bir `Double` değişkeni örtük olarak `Integer`türüne dönüştürülemediğinden bir derleyici hatası oluşur.  
  
 Ancak `Option Strict Off`ayarlarsanız, Visual Basic örtülü daraltma dönüştürmelerine izin verir, ancak beklenmedik veri veya duyarlık kaybına neden olabilirler. Bu nedenle, üretim kodu yazarken `Option Strict On` kullanmanızı öneririz. Daha fazla bilgi için bkz. [genişletme ve daraltma dönüştürmeleri](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Aritmetik İşleçler](../../../../visual-basic/language-reference/operators/arithmetic-operators.md)
- [Bit Kaydırma İşleçleri](../../../../visual-basic/language-reference/operators/bit-shift-operators.md)
- [Visual Basic karşılaştırma Işleçleri](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)
- [Visual Basic birleştirme Işleçleri](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/concatenation-operators.md)
- [Visual Basic mantıksal ve bit düzeyinde Işleçler](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
- [İşleçlerin Etkili Bileşimi](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/efficient-combination-of-operators.md)
