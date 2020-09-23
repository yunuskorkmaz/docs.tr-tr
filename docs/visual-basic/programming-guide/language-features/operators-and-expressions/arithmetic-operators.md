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
ms.openlocfilehash: 023e479736285aa2d04509e05f49fe930cb4721d
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91090085"
---
# <a name="arithmetic-operators-in-visual-basic"></a>Visual Basic'de Aritmetik İşleçler

Aritmetik işleçler, değişmez değerler, değişkenler, diğer ifadeler, işlev ve özellik çağrıları ve sabitler tarafından temsil edilen sayısal değerlerin hesaplanmasını içeren tanıdık aritmetik işlemlerin çoğunu gerçekleştirmek için kullanılır. Ayrıca, Aritmetik işleçlerle sınıflandırılan bit kaydırma işleçleridir. Bu, işlenen ayrı bitlerin düzeyine göre hareket ederler ve bit desenlerini sola veya sağa kaydıramalıdır.  
  
## <a name="arithmetic-operations"></a>Aritmetik Işlemler  

 Aşağıdaki örnekte gösterildiği gibi, bir ifadeye [+ işleciyle](../../../language-reference/operators/addition-operator.md)birlikte iki değer ekleyebilir veya [-işleci (Visual Basic)](../../../language-reference/operators/subtraction-operator.md)ile diğerine çıkarabilirsiniz.  
  
 [!code-vb[VbVbalrOperators#57](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#57)]  
  
 Değilleme Ayrıca, aşağıdaki örnekte gösterildiği gibi yalnızca bir işlenen ile [-işleci (Visual Basic)](../../../language-reference/operators/subtraction-operator.md)kullanır.  
  
 [!code-vb[VbVbalrOperators#58](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#58)]  
  
 Çarpma ve bölme, aşağıdaki örnekte gösterildiği gibi, sırasıyla [* işlecini](../../../language-reference/operators/multiplication-operator.md) ve [/işlecini (Visual Basic)](../../../language-reference/operators/floating-point-division-operator.md)kullanır.  
  
 [!code-vb[VbVbalrOperators#59](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#59)]  
  
 Üs, aşağıdaki örnekte gösterildiği gibi [^ işlecini](../../../language-reference/operators/exponentiation-operator.md)kullanır.  
  
 [!code-vb[VbVbalrOperators#60](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#60)]  
  
 Tamsayı bölme, [\ işleci (Visual Basic)](../../../language-reference/operators/integer-division-operator.md)kullanılarak yürütülür. Tamsayı bölme bölümü, diğer bir deyişle, bölen herhangi bir geri dönüş yapmadan bölünmeye bölüneceği sayı sayısını temsil eden tamsayıdır. Bölen ve bölünen öğelerinin her ikisi de `SByte` `Byte` `Short` `UShort` `Integer` `UInteger` `Long` `ULong` Bu operatör için tamsayı (,,,,,,, ve) türünde olmalıdır. Tüm diğer türler önce bir integral türüne dönüştürülmelidir. Aşağıdaki örnek, tamsayı bölümünü gösterir.  
  
 [!code-vb[VbVbalrOperators#61](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#61)]  
  
 Mod aritmetik, [Mod işleci](../../../language-reference/operators/mod-operator.md)kullanılarak gerçekleştirilir. Bu işleç, böleni bir integral sayısına bölündükten sonra kalanı döndürür. Hem bölen hem de bölünen tamsayı türlerdir, döndürülen değer integral olur. Bölen ve bölünen kayan nokta türüyorsa, döndürülen değer de kayan noktalı olur. Aşağıdaki örnek bu davranışı gösterir.  
  
 [!code-vb[VbVbalrOperators#62](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#62)]  
  
 [!code-vb[VbVbalrOperators#63](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#63)]  
  
### <a name="attempted-division-by-zero"></a>Sıfıra bölme denendi  

 Sıfıra bölme, dahil edilen veri türlerine bağlı olarak farklı sonuçlara sahiptir. İntegral bölümler (,,,,,,,,,,, `SByte` `Byte` `Short` `UShort` `Integer` `UInteger` `Long` `ULong` .NET Framework bir <xref:System.DivideByZeroException> özel durum oluşturur. `Decimal`Veya `Single` veri türündeki bölüm işlemlerinde, .NET Framework de bir <xref:System.DivideByZeroException> özel durum oluşturur.  
  
 Veri türünü içeren kayan nokta bölümleri içinde `Double` , hiçbir özel durum oluşturulmaz ve sonuç <xref:System.Double.NaN> , bölünme göre,, ya da temsil eden sınıf üyesidir <xref:System.Double.PositiveInfinity> <xref:System.Double.NegativeInfinity> . Aşağıdaki tabloda, bir değeri sıfıra bölme girişiminden oluşan çeşitli sonuçlar özetlenmektedir `Double` .  
  
|Bölünen veri türü|Bölen veri türü|Bölünen değer|Sonuç|  
|---|---|---|---|  
|`Double`|`Double`|0|<xref:System.Double.NaN> (matematik olarak tanımlanmış bir sayı değil)|  
|`Double`|`Double`|> 0|<xref:System.Double.PositiveInfinity>|  
|`Double`|`Double`|\< 0|<xref:System.Double.NegativeInfinity>|  
  
 Bir <xref:System.DivideByZeroException> özel durumu yakalarsanız, bunu işleyebilmeniz için üyelerini kullanabilirsiniz. Örneğin, <xref:System.Exception.Message%2A> özelliği özel durum için ileti metnini tutar. Daha fazla bilgi için bkz [. TRY... Yakala... Finally ekstresi](../../../language-reference/statements/try-catch-finally-statement.md).  
  
## <a name="bit-shift-operations"></a>Bit kaydırma Işlemleri  

 Bit kaydırma işlemi bir bit düzeninde aritmetik kaydırma gerçekleştirir. Model, sol taraftaki işlenende bulunur, ancak sağdaki işlenen, kalıbı kaydırmak için konumların sayısını belirtir. [>> işleçle](../../../language-reference/operators/right-shift-operator.md) veya [<< işleci](../../../language-reference/operators/left-shift-operator.md)ile sola doğru bir düzende kaydırma yapabilirsiniz.  
  
 Model işleneninin veri türü,,,, `SByte` `Byte` `Short` `UShort` `Integer` , `UInteger` , `Long` , veya olmalıdır `ULong` . Kaydırma tutarı işleneninin veri türü, olmalıdır veya ' `Integer` ye genişlemelidir `Integer` .  
  
 Aritmetik vardiyalar dairesel değildir, bu da sonucun bir sonunun dışına sürüklenen bitlerin diğer uçta yeniden tanıtılmadığını gösterir. Bir kaydırmaya göre belirlenen bit konumları aşağıdaki gibi ayarlanır:  
  
- Aritmetik sola kaydırma için 0  
  
- pozitif bir sayının aritmetik sağ kaydırması için 0  
  
- işaretsiz bir veri türünün aritmetik sağ kaydırması için 0 ( `Byte` ,,, `UShort` `UInteger` `ULong` )  
  
- negatif bir sayının ( `SByte` ,, `Short` `Integer` veya `Long` ) aritmetik sağ kaydırması için 1  
  
 Aşağıdaki örnek, bir `Integer` değeri hem sol hem de sağ kaydırır.  
  
 [!code-vb[VbVbalrOperators#64](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#64)]  
  
 Aritmetik vardiyalar hiçbir şekilde taşma özel durumu oluşturmaz.  
  
## <a name="bitwise-operations"></a>Bit düzeyinde Işlemler  

 Mantıksal işleçler olmanın yanı sıra,, `Not` , `Or` `And` ve `Xor` sayısal değerlerde kullanıldığında bit düzeyinde aritmetik de gerçekleştirir. Daha fazla bilgi için, [Visual Basic mantıksal ve bit düzeyinde işleçlerdeki](logical-and-bitwise-operators.md)"bit düzeyinde işlemler" konusuna bakın.  
  
## <a name="type-safety"></a>Tür güvenliği  

 İşlenenler normalde aynı türde olmalıdır. Örneğin, bir `Integer` değişkenle birlikte ekleme yapıyorsanız, bunu başka bir değişkene eklemeniz gerekir `Integer` ve sonucu da türünde bir değişkene atamanız gerekir `Integer` .  
  
 İyi tür açısından güvenli kodlama uygulaması sağlamanın bir yolu, [Strict deyimin seçeneğini](../../../language-reference/statements/option-strict-statement.md)kullanmaktır. Ayarlarsanız `Option Strict On` , Visual Basic otomatik olarak *tür kullanımı uyumlu* dönüşümler gerçekleştirir. Örneğin, bir değişkene bir değişken eklemeye `Integer` `Double` ve değeri bir değişkene atamaya çalışırsanız `Double` , bir `Integer` değer `Double` veri kaybı olmadan olarak dönüştürülebildiğinden, işlem normal olarak devam eder. Tür-güvenli olmayan dönüşümler, diğer yandan, ile bir derleyici hatasına neden olur `Option Strict On` . Örneğin, bir değişkene bir `Integer` değişken eklemeye `Double` ve değeri bir değişkene atamaya çalışırsanız, bir `Integer` `Double` değişken örtük olarak türüne dönüştürülemediğinden bir derleyici hatası oluşur `Integer` .  
  
 `Option Strict Off`Ancak ayarlarsanız Visual Basic örtük daraltma dönüştürmelerine izin verir, ancak beklenmedik veri veya duyarlık kaybına neden olabilirler. Bu nedenle, `Option Strict On` üretim kodu yazarken kullanmanızı öneririz. Daha fazla bilgi için bkz. [genişletme ve daraltma dönüştürmeleri](../data-types/widening-and-narrowing-conversions.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Aritmetik Işleçler](../../../language-reference/operators/arithmetic-operators.md)
- [Bit Kaydırma İşleçleri](../../../language-reference/operators/bit-shift-operators.md)
- [Visual Basic'de Karşılaştırma İşleçleri](comparison-operators.md)
- [Visual Basic'de Birleştirme İşleçleri](concatenation-operators.md)
- [Visual Basic'de Mantıksal ve Bit Düzeyinde İşleçler](logical-and-bitwise-operators.md)
- [İşleçlerin Etkili Bileşimi](efficient-combination-of-operators.md)
