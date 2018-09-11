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
ms.openlocfilehash: 91806c204c313956b292eb9c9be078991f733b4e
ms.sourcegitcommit: 4b6490b2529707627ad77c3a43fbe64120397175
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/10/2018
ms.locfileid: "44276010"
---
# <a name="-operator-visual-basic"></a>+ İşleci (Visual Basic)
İki sayı ekleyen veya sayısal bir ifadenin pozitif değerini döndürür. Ayrıca iki dize ifadeleri birleştirmek için kullanılabilir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```vb
expression1 + expression2  
- or -  
+ expression1  
```  
  
## <a name="parts"></a>Bölümler  
  
|Terim|Tanım|  
|---|---|  
|`expression1`|Gerekli. Bir sayı veya dize ifadesi.|  
|`expression2`|Sürece gerekli `+` işleci, negatif bir değer hesaplıyor. Bir sayı veya dize ifadesi.|  
  
## <a name="result"></a>Sonuç  
 Varsa `expression1` ve `expression2` hem de sayısal sonucudur aritmetik toplamları olması.  
  
 Varsa `expression2` eksik, `+` işleci *birli* kimlik işleci değişmez değerini bir ifade. Bu anlamda işlemi işaretini korur oluşur `expression1`, sonuç negatif olur, `expression1` negatiftir.  
  
 Varsa `expression1` ve `expression2` hem dizelerdir değerleri birleşimi sonucudur.  
  
 Varsa `expression1` ve `expression2` olan karışık türde gerçekleştirilecek eylemi türleri, içerikleri ve ayarına bağlıdır [Option Strict deyimi](../../../visual-basic/language-reference/statements/option-strict-statement.md). Daha fazla bilgi için "Açıklamalar" tablolarında bakın  
  
## <a name="supported-types"></a>Desteklenen türler  
 İmzasız ve kayan nokta türleri dahil olmak üzere tüm sayısal türlerin ve `Decimal`, ve `String`.  
  
## <a name="remarks"></a>Açıklamalar  
 Genel olarak, `+` aritmetik ek mümkün olduğunda gerçekleştirir ve yalnızca her iki ifade de dizeleri olduğunda art arda ekler.  
  
 Her iki ifade ise bir `Object`, Visual Basic, aşağıdaki eylemleri gerçekleştirir.  
  
|İfade veri türleri|Derleyici tarafından eylemi|  
|---|---|  
|Her iki ifade de sayısal veri türleri: (`SByte`, `Byte`, `Short`, `UShort`, `Integer`, `UInteger`, `Long`, `ULong`, `Decimal`, `Single`, veya `Double`)|Ekleyin. Sonuç veri türü olan veri türleri için uygun bir sayısal tür `expression1` ve `expression2`. "Tamsayı aritmetik" tablolarında bkz [işleci sonuçlarını veri türleri](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md).|  
|Her iki ifade de türüdür `String`|Art arda ekler.|  
|Bir ifade bir sayısal veri türü ve diğer bir dizedir|Varsa `Option Strict` olduğu `On`, ardından bir derleyici hatası oluşturur.<br /><br /> Varsa `Option Strict` olduğu `Off`, örtük dönüştürme `String` için `Double` ve ekleyin.<br /><br /> Varsa `String` dönüştürülemez `Double`, ardından throw bir <xref:System.InvalidCastException> özel durum.|  
|Bir ifade olan bir sayısal veri türü ve diğeri [hiçbir şey](../../../visual-basic/language-reference/nothing.md)|Ekleme, ile `Nothing` sıfır değerli.|  
|Bir ifade bir dizedir ve diğeri ise `Nothing`|İle Birleştir `Nothing` değerli olarak "".|  
  
 Bir ifade ise bir `Object` ifade, Visual Basic, aşağıdaki eylemleri gerçekleştirir.  
  
|İfade veri türleri|Derleyici tarafından eylemi|  
|---|---|  
|`Object` sayısal bir değeri bir ifade tutan ve diğer bir sayısal veri türü|Varsa `Option Strict` olduğu `On`, ardından bir derleyici hatası oluşturur.<br /><br /> Varsa `Option Strict` olduğu `Off`, sonra ekleyin.|  
|`Object` sayısal bir değeri bir ifade tutan ve diğer türüdür `String`|Varsa `Option Strict` olduğu `On`, ardından bir derleyici hatası oluşturur.<br /><br /> Varsa `Option Strict` olduğu `Off`, örtük dönüştürme `String` için `Double` ve ekleyin.<br /><br /> Varsa `String` dönüştürülemez `Double`, ardından throw bir <xref:System.InvalidCastException> özel durum.|  
|`Object` bir ifade tutan bir dize ve diğer bir sayısal veri türü|Varsa `Option Strict` olduğu `On`, ardından bir derleyici hatası oluşturur.<br /><br /> Varsa `Option Strict` olduğu `Off`, dizeyi örtük dönüştürme `Object` için `Double` ve ekleyin.<br /><br /> Dize `Object` dönüştürülemez `Double`, ardından throw bir <xref:System.InvalidCastException> özel durum.|  
|`Object` bir ifade tutan bir dize ve diğer türüdür `String`|Varsa `Option Strict` olduğu `On`, ardından bir derleyici hatası oluşturur.<br /><br /> Varsa `Option Strict` olduğu `Off`, örtük dönüştürme `Object` için `String` ve birleştirin.|  
  
 Her iki ifade ise `Object` ifadeleri, Visual Basic, aşağıdaki eylemleri gerçekleştirir (`Option Strict Off` yalnızca).  
  
|İfade veri türleri|Derleyici tarafından eylemi|  
|---|---|  
|Her ikisi de `Object` ifadeleri sayısal değerleri tutun|Ekleyin.|  
|Her ikisi de `Object` ifadeleri, tür `String`|Art arda ekler.|  
|Bir `Object` ifade tutan bir sayısal değer ve başka bir dize içerir|Dizeyi örtük dönüştürme `Object` için `Double` ve ekleyin.<br /><br /> Dize `Object` sayısal bir değere dönüştürülemez ve throw bir <xref:System.InvalidCastException> özel durum.|  
  
 Ya da `Object` ifadeyi hesaplar için [hiçbir şey](../../../visual-basic/language-reference/nothing.md) veya <xref:System.DBNull>, `+` işleci olarak bunu değerlendirir bir `String` değerine sahip "".  
  
> [!NOTE]
>  Kullanırken `+` işleci, yükleyemeyebilir eklenmesi veya dize birleştirme gerçekleşip gerçekleşmeyeceğini belirlemek. Kullanım `&` birleştirme için işleç belirsizliği ortadan kaldırmak ve kendi kendine belgelendirme kodu sağlayabilir.  
  
## <a name="overloading"></a>Aşırı Yükleme  
 `+` İşleci olabilir *aşırı*, işleneni, sınıf veya yapı türüne sahip olduğunda bir sınıf veya yapı davranışını tanımlayabilirsiniz, anlamına gelir. Kodunuz bu tür bir sınıf veya yapı üzerinde bu işleç kullanıyorsa, yeniden tanımlanan davranışını anladığınızdan emin olun. Daha fazla bilgi için [işleç yordamları](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte `+` numaralarını eklemek için işleci. İşlenenler, her ikisi de sayısal olduğunda, Visual Basic aritmetik sonucu hesaplar. Aritmetik sonucu iki işlenenden toplamını temsil eder.  
  
 [!code-vb[VbVbalrOperators#6](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/addition-operator_1.vb)]  
  
 Ayrıca `+` dizeyi birleştirmek için işleci. Visual Basic bunları işlenen her iki dize olursa art arda ekler. Birleştirme sonucu art arda iki işlenenden biri içeriğini oluşan tek bir dize temsil eder.  
  
 İşlenen karma türde ise, sonuç ayarına bağlıdır [Option Strict deyimi](../../../visual-basic/language-reference/statements/option-strict-statement.md). Sonuç aşağıdaki örnekte, `Option Strict` olduğu `On`.  
  
 [!code-vb[VbVbalrOperators#53](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/addition-operator_2.vb)]  
  
 [!code-vb[VbVbalrOperators#50](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/addition-operator_3.vb)]  
[!code-vb[VbVbalrOperators#51](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/addition-operator_4.vb)]  
  
 Sonuç aşağıdaki örnekte, `Option Strict` olduğu `Off`.  
  
 [!code-vb[VbVbalrOperators#54](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/addition-operator_5.vb)]  
  
 [!code-vb[VbVbalrOperators#50](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/addition-operator_3.vb)]  
[!code-vb[VbVbalrOperators#52](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/addition-operator_6.vb)]  
  
 Belirsizliği ortadan kaldırmak için kullanmanız `&` yerine işleci `+` birleştirme için.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [& İşleci](../../../visual-basic/language-reference/operators/concatenation-operator.md)  
 [Birleştirme İşleçleri](../../../visual-basic/language-reference/operators/concatenation-operators.md)  
 [Aritmetik İşleçler](../../../visual-basic/language-reference/operators/arithmetic-operators.md)  
 [İşlevselliğe Göre Listelenmiş İşleçler](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)  
 [Visual Basic'de İşleç önceliği](../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [Visual Basic'de aritmetik işleçler](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)  
 [Option Strict Deyimi](../../../visual-basic/language-reference/statements/option-strict-statement.md)
