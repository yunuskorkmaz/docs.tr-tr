---
title: + İşleç
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
ms.openlocfilehash: 12c14b3be0562a31470ddbd2d5489ccdbdf3b62b
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74350286"
---
# <a name="-operator-visual-basic"></a>+ İşleci (Visual Basic)
İki sayı ekler veya sayısal bir ifadenin pozitif değerini döndürür. , İki dize ifadesini birleştirmek için de kullanılabilir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```vb
expression1 + expression2
```
  
veya

```vb  
+expression1  
```  
  
## <a name="parts"></a>Bölümler  
  
|Terim|Tanım|  
|---|---|  
|`expression1`|Gerekli. Herhangi bir sayısal veya dize ifadesi.|  
|`expression2`|`+` işleci negatif bir değer hesaplanmadığı için gereklidir. Herhangi bir sayısal veya dize ifadesi.|  
  
## <a name="result"></a>Sonuç  
 `expression1` ve `expression2` her ikisi de sayısal ise, sonuç Aritmetik toplamdır.  
  
 `expression2` yoksa, `+` işleci bir ifadenin değiştirilmemiş değeri için *birli* kimlik işleçtir. Bu anlamda, işlem `expression1`işaretini korur, bu nedenle `expression1` negatifse sonuç negatif olur.  
  
 `expression1` ve `expression2` her iki dizise sonuç, değerlerinin birleştirilmesiyle sonuçlanır.  
  
 `expression1` ve `expression2` karışık türlerdir, uygulanan eylem türlerine, içeriğine ve [katı deyimin seçeneğine](../../../visual-basic/language-reference/statements/option-strict-statement.md)bağlıdır. Daha fazla bilgi için "Notlar" içindeki tablolara bakın.  
  
## <a name="supported-types"></a>Desteklenen türler  
 İşaretsiz ve kayan nokta türleri ve `Decimal`ve `String`dahil olmak üzere tüm sayısal türler.  
  
## <a name="remarks"></a>Açıklamalar  
 Genellikle `+`, mümkün olduğunda aritmetik ekleme gerçekleştirir ve yalnızca her iki ifade de dizeler olduğunda art arda ekler.  
  
 Hiçbir ifade bir `Object`değilse, Visual Basic aşağıdaki eylemleri gerçekleştirir.  
  
|İfadelerin veri türleri|Derleyiciye göre eylem|  
|---|---|  
|Her iki ifade de sayısal veri türleridir (`SByte`, `Byte`, `Short`, `UShort`, `Integer`, `UInteger`, `Long`, `ULong`, `Decimal`, `Single`veya `Double`)|Ekleyemiyorum. Sonuç veri türü, `expression1` ve `expression2`veri türleri için uygun bir sayısal türdür. [Işleç sonuçlarının veri türlerinde](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md)"tamsayı aritmetiği" tablolarına bakın.|  
|Her iki ifade de `String` türündedir|Karakter.|  
|Bir ifade sayısal bir veri türü ve diğeri bir dizedir|`Option Strict` `On`ve ardından bir derleyici hatası oluşturun.<br /><br /> `Option Strict` `Off`, `String` örtülü olarak `Double` ve Ekle ' ye dönüştürün.<br /><br /> `String` `Double`olarak dönüştürülemiyorsa, bir <xref:System.InvalidCastException> özel durumu oluşturun.|  
|Bir ifade sayısal bir veri türüdür ve diğeri [Nothing](../../../visual-basic/language-reference/nothing.md) değildir|`Nothing`, sıfır olarak değerli bir değer ekleyin.|  
|Bir ifade bir dizedir ve diğeri `Nothing`|Birleştirme, `Nothing` "" olarak değerlendirilir.|  
  
 Bir ifade `Object` ifadesiyse Visual Basic aşağıdaki eylemleri gerçekleştirir.  
  
|İfadelerin veri türleri|Derleyiciye göre eylem|  
|---|---|  
|`Object` ifade sayısal bir değer ve diğeri ise sayısal bir veri türüdür|`Option Strict` `On`ve ardından bir derleyici hatası oluşturun.<br /><br /> `Option Strict` `Off`ise ekleyin.|  
|`Object` ifade sayısal bir değer ve diğeri tür `String` tutar|`Option Strict` `On`ve ardından bir derleyici hatası oluşturun.<br /><br /> `Option Strict` `Off`, `String` örtülü olarak `Double` ve Ekle ' ye dönüştürün.<br /><br /> `String` `Double`olarak dönüştürülemiyorsa, bir <xref:System.InvalidCastException> özel durumu oluşturun.|  
|`Object` ifade bir dize ve diğeri ise sayısal bir veri türüdür|`Option Strict` `On`ve ardından bir derleyici hatası oluşturun.<br /><br /> `Option Strict` `Off`, `Object` dizeyi örtük olarak `Double` ve Ekle ' ye dönüştürün.<br /><br /> `Object` dize `Double`dönüştürülemiyorsa, bir <xref:System.InvalidCastException> özel durumu oluşturun.|  
|`Object` ifade bir dizeyi ve diğeri tür `String` içerir|`Option Strict` `On`ve ardından bir derleyici hatası oluşturun.<br /><br /> `Option Strict` `Off`, `Object` örtülü olarak `String` ve Birleştir 'e dönüştürün.|  
  
 Her iki ifade de `Object` ifadeleridir Visual Basic aşağıdaki eylemleri alır (yalnızca`Option Strict Off`).  
  
|İfadelerin veri türleri|Derleyiciye göre eylem|  
|---|---|  
|Her iki `Object` ifadesi de sayısal değerleri tutar|Ekleyemiyorum.|  
|Her iki `Object` ifadesi de tür `String`|Karakter.|  
|Bir `Object` ifadesi sayısal bir değer ve diğeri bir dize tutar|`Object` dize `Double` ve Ekle ' ye örtük olarak dönüştürün.<br /><br /> `Object` dize sayısal bir değere dönüştürülemiyorsa, bir <xref:System.InvalidCastException> özel durumu oluşturun.|  
  
 `Object` ifadesi [Nothing](../../../visual-basic/language-reference/nothing.md) veya <xref:System.DBNull>olarak değerlendirilirse, `+` işleci bunu "" değerine sahip bir `String` olarak değerlendirir.  
  
> [!NOTE]
> `+` işlecini kullandığınızda, ekleme veya dize birleştirme işleminin yapılıp yapılmayacağını belirleyemeyebilirsiniz. Belirsizliği ortadan kaldırmak ve kendi kendine belgeleme kodu sağlamak için, birleştirme için `&` işlecini kullanın.  
  
## <a name="overloading"></a>Aşırı Yükleme  
 `+` işleci *aşırı*yüklenebilir, yani bir işlenen bu sınıf veya yapının türüne sahip olduğunda bir sınıf veya yapının davranışını yeniden tanımlayabileceği anlamına gelir. Kodunuz böyle bir sınıf veya yapıda bu işleci kullanıyorsa, yeniden tanımlanmış davranışını anladığınızdan emin olun. Daha fazla bilgi için bkz. [operatör yordamları](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, sayı eklemek için `+` işlecini kullanır. İşlenenler her ikisi de sayısal ise, Visual Basic aritmetik sonucu hesaplar. Aritmetik sonuç, iki işlenenin toplamını temsil eder.  
  
 [!code-vb[VbVbalrOperators#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#6)]  
  
 Dizeleri birleştirmek için `+` işlecini de kullanabilirsiniz. İşlenenler her iki dizise, Visual Basic bunları birleştirir. Birleştirme sonucu, iki işleneninin içeriğinden oluşan tek bir dizeyi temsil eder.  
  
 İşlenenler karışık türlerinise, sonuç, [Option Strict deyimin](../../../visual-basic/language-reference/statements/option-strict-statement.md)ayarına bağlıdır. Aşağıdaki örnek `Option Strict` `On`sonucunu gösterir.  
  
 [!code-vb[VbVbalrOperators#53](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class3.vb#53)]  
  
 [!code-vb[VbVbalrOperators#50](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class2.vb#50)]  
[!code-vb[VbVbalrOperators#51](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class2.vb#51)]  
  
 Aşağıdaki örnek `Option Strict` `Off`sonucunu gösterir.  
  
 [!code-vb[VbVbalrOperators#54](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class2.vb#54)]  
  
 [!code-vb[VbVbalrOperators#50](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class2.vb#50)]  
[!code-vb[VbVbalrOperators#52](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class2.vb#52)]  
  
 Belirsizliği ortadan kaldırmak için, birleştirme için `+` yerine `&` işlecini kullanmanız gerekir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [& İşleci](../../../visual-basic/language-reference/operators/concatenation-operator.md)
- [Birleştirme İşleçleri](../../../visual-basic/language-reference/operators/concatenation-operators.md)
- [Aritmetik İşleçler](../../../visual-basic/language-reference/operators/arithmetic-operators.md)
- [İşlevselliğe Göre Listelenmiş İşleçler](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [Visual Basic operatör önceliği](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [Visual Basic aritmetik Işleçler](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
- [Option Strict Deyimi](../../../visual-basic/language-reference/statements/option-strict-statement.md)
