---
title: + İşleci (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.+
helpviewer_keywords:
- arithmetic operators [Visual Basic], addition
- + operator
- concatenation operators [Visual Basic], syntax
- strings [Visual Basic], concatenating
- sum operator [Visual Basic]
ms.assetid: 5694778f-0a2c-4539-8009-f66f318fb46d
ms.openlocfilehash: ccf79c700cf852c0febb9c3f3464cbacdd39296e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="-operator-visual-basic"></a>+ İşleci (Visual Basic)
İki sayı ekleyen ya da pozitif sayısal ifadenin değerini döndürür. Ayrıca iki dize ifadeleri birleştirmek için kullanılabilir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
      expression1 + expression2  
- or -  
+ expression1  
```  
  
## <a name="parts"></a>Bölümler  
  
|Terim|Tanım|  
|---|---|  
|`expression1`|Gerekli. Tüm sayısal veya dize ifadesi.|  
|`expression2`|Sürece gerekli `+` işleci negatif bir değer hesaplıyor. Tüm sayısal veya dize ifadesi.|  
  
## <a name="result"></a>Sonuç  
 Varsa `expression1` ve `expression2` hem de sayısal sonucudur kendi aritmetik toplam olması.  
  
 Varsa `expression2` yoksa, `+` işlecidir *birli* değişmez değeri ifade kimlik işleci. İşaretini korur işlem bu anlamda oluşur `expression1`sonucu negatif gelir, `expression1` negatiftir.  
  
 Varsa `expression1` ve `expression2` hem dizelerdir değerlerine birleşimini sonucudur.  
  
 Varsa `expression1` ve `expression2` olan karma türleri, gerçekleştirilecek eylem türlerini, içeriklerini ve ayarını bağlıdır [Option Strict deyimi](../../../visual-basic/language-reference/statements/option-strict-statement.md). Daha fazla bilgi için bkz: "Açıklamalar" ın tabloları  
  
## <a name="supported-types"></a>Desteklenen türler  
 İmzasız ve kayan nokta türleri dahil olmak üzere tüm sayısal türler ve `Decimal`, ve `String`.  
  
## <a name="remarks"></a>Açıklamalar  
 Genel olarak, `+` aritmetik toplama mümkün olduğunda gerçekleştirir ve yalnızca her iki ifade dizeleri olduğunda art arda ekler.  
  
 Hiçbiri ifade ise bir `Object`, Visual Basic aşağıdaki eylemleri gerçekleştirir.  
  
|İfade veri türleri|Derleyici tarafından eylemi|  
|---|---|  
|Her iki ifadelerini sayısal veri türleri (`SByte`, `Byte`, `Short`, `UShort`, `Integer`, `UInteger`, `Long`, `ULong`, `Decimal`, `Single`, veya `Double`)|Ekleyin. Sonuç veri türü sayısal bir tür veri türleri için uygun değil `expression1` ve `expression2`. "Tamsayı aritmetiğini" tablolarda bkz [işleci sonuçlarını veri türleri](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md).|  
|Her iki ifadelerini türü `String`|Art arda ekler.|  
|Bir ifade sayısal veri türüne ve diğer bir dizedir|Varsa `Option Strict` olan `On`, derleyici hatası oluşturur.<br /><br /> Varsa `Option Strict` olan `Off`, örtük dönüştürme `String` için `Double` ve ekleyin.<br /><br /> Varsa `String` dönüştürülemiyor `Double`, ardından throw bir <xref:System.InvalidCastException> özel durum.|  
|Bir ifade sayısal veri türüne ve diğer [hiçbir şey](../../../visual-basic/language-reference/nothing.md)|Ekleme, ile `Nothing` sıfır olarak değerli.|  
|Bir ifadenin bir dize ve diğer `Nothing`|Birleştir ile `Nothing` değerli olarak "".|  
  
 Bir ifade olması durumunda bir `Object` ifadesi, Visual Basic, aşağıdaki eylemleri gerçekleştirir.  
  
|İfade veri türleri|Derleyici tarafından eylemi|  
|---|---|  
|`Object` ifade sayısal bir değer içerir ve diğeri sayısal veri türüne|Varsa `Option Strict` olan `On`, derleyici hatası oluşturur.<br /><br /> Varsa `Option Strict` olan `Off`, sonra ekleyin.|  
|`Object` sayısal bir değer ifadesi tutar ve diğer türüdür `String`|Varsa `Option Strict` olan `On`, derleyici hatası oluşturur.<br /><br /> Varsa `Option Strict` olan `Off`, örtük dönüştürme `String` için `Double` ve ekleyin.<br /><br /> Varsa `String` dönüştürülemiyor `Double`, ardından throw bir <xref:System.InvalidCastException> özel durum.|  
|`Object` bir dize ifadesi tutar ve diğer sayısal veri türü|Varsa `Option Strict` olan `On`, derleyici hatası oluşturur.<br /><br /> Varsa `Option Strict` olan `Off`, dize örtük dönüştürme `Object` için `Double` ve ekleyin.<br /><br /> Varsa dize `Object` dönüştürülemiyor `Double`, ardından throw bir <xref:System.InvalidCastException> özel durum.|  
|`Object` bir dize ifadesi tutar ve diğer türüdür `String`|Varsa `Option Strict` olan `On`, derleyici hatası oluşturur.<br /><br /> Varsa `Option Strict` olan `Off`, örtük dönüştürme `Object` için `String` ve art arda ekler.|  
  
 Her iki ifadeler `Object` ifadeleri, Visual Basic, aşağıdaki eylemleri gerçekleştirir (`Option Strict Off` yalnızca).  
  
|İfade veri türleri|Derleyici tarafından eylemi|  
|---|---|  
|Her ikisi de `Object` ifadeleri sayısal değerleri tutun|Ekleyin.|  
|Her ikisi de `Object` ifadelerini türü `String`|Art arda ekler.|  
|Bir `Object` ifade sayısal bir değer tutar ve diğer bir dize tutar|Örtük olarak dize dönüştürme `Object` için `Double` ve ekleyin.<br /><br /> Varsa dize `Object` sayısal bir değere dönüştürülemez sonra throw bir <xref:System.InvalidCastException> özel durum.|  
  
 Her iki `Object` ifadeyi hesaplar için [hiçbir şey](../../../visual-basic/language-reference/nothing.md) veya <xref:System.DBNull>, `+` işleci da işler bir `String` değerini "".  
  
> [!NOTE]
>  Kullandığınızda `+` işleci, eklenmesi veya dize birleştirme oluşacaktır olup olmadığını belirlemek kuramıyor olabilir. Kullanım `&` belirsizliği ortadan kaldırmak ve kendi kendine belgelendirme kod sağlamak için birleştirme için işleci.  
  
## <a name="overloading"></a>Aşırı Yükleme  
 `+` İşleci olabilir *aşırı*, işleneni, sınıf veya yapı türüne sahip olduğunda bir sınıf veya yapı davranışını tanımlayabilirsiniz, anlamına gelir. Bu tür bir sınıf veya yapı üzerinde kodunuzu bu işleç kullanıyorsa, yeniden tanımlanan davranışını anladığınızdan emin olun. Daha fazla bilgi için bkz: [işleç yordamları](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek kullanır `+` sayıları işleci. İşlenen her ikisi de sayısal olursa, Visual Basic Aritmetik sonuç hesaplar. Aritmetik sonuç iki işlenen toplamını temsil eder.  
  
 [!code-vb[VbVbalrOperators#6](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/addition-operator_1.vb)]  
  
 Aynı zamanda `+` dizeyi birleştirmek için işleci. Visual Basic bunları işlenen iki dize olursa, art arda ekler. Birleştirme sonucu art arda iki işlenen bir içeriğini oluşan tek bir dize temsil eder.  
  
 İşlenen karma türlerini olursa, sonuç olarak ayarına bağlıdır [Option Strict deyimi](../../../visual-basic/language-reference/statements/option-strict-statement.md). Aşağıdaki örnek sonucu gösterilmektedir, `Option Strict` olan `On`.  
  
 [!code-vb[VbVbalrOperators#53](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/addition-operator_2.vb)]  
  
 [!code-vb[VbVbalrOperators#50](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/addition-operator_3.vb)]  
[!code-vb[VbVbalrOperators#51](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/addition-operator_4.vb)]  
  
 Aşağıdaki örnek sonucu gösterilmektedir, `Option Strict` olan `Off`.  
  
 [!code-vb[VbVbalrOperators#54](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/addition-operator_5.vb)]  
  
 [!code-vb[VbVbalrOperators#50](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/addition-operator_3.vb)]  
[!code-vb[VbVbalrOperators#52](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/addition-operator_6.vb)]  
  
 Belirsizliği ortadan kaldırmak için kullanmanız `&` operatörü yerine `+` birleştirme için.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [& İşleci](../../../visual-basic/language-reference/operators/concatenation-operator.md)  
 [Birleştirme İşleçleri](../../../visual-basic/language-reference/operators/concatenation-operators.md)  
 [Aritmetik İşleçler](../../../visual-basic/language-reference/operators/arithmetic-operators.md)  
 [İşlevselliğe Göre Listelenmiş İşleçler](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)  
 [Visual Basic'de İşleç önceliği](../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [Visual Basic'de aritmetik işleçler](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)  
 [Option Strict Deyimi](../../../visual-basic/language-reference/statements/option-strict-statement.md)
