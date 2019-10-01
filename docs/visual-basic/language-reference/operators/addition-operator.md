---
title: + İşleç (Visual Basic)
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
ms.openlocfilehash: 3187551afb7d25470f48dad894188766a811bb0a
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/01/2019
ms.locfileid: "71701004"
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
|`expression2`|@No__t-0 işleci negatif bir değer hesaplanmadığı için gereklidir. Herhangi bir sayısal veya dize ifadesi.|  
  
## <a name="result"></a>Sonuç  
 @No__t-0 ve `expression2` her ikisi de sayısal ise, sonuç Aritmetik toplamdır.  
  
 @No__t-0 yoksa, `+` işleci bir ifadenin değiştirilmemiş değeri için *birli* kimlik işleçtir. Bu anlamda, işlem `expression1` ' ın işaretini korur, bu nedenle `expression1` negatifse sonuç negatif olur.  
  
 @No__t-0 ve `expression2` her iki dizise sonuç, değerlerinin birleştirilmesiyle sonuçlanır.  
  
 @No__t-0 ve `expression2` karma türdaysa, uygulanan eylem türlerine, içeriklerine ve [seçenek katı deyimin](../../../visual-basic/language-reference/statements/option-strict-statement.md)ayarına bağlıdır. Daha fazla bilgi için "Notlar" içindeki tablolara bakın.  
  
## <a name="supported-types"></a>Desteklenen türler  
 İşaretsiz ve kayan nokta türleri ve `Decimal` ve `String` dahil tüm sayısal türler.  
  
## <a name="remarks"></a>Açıklamalar  
 Genellikle `+`, mümkün olduğunda aritmetik ekleme gerçekleştirir ve yalnızca her iki ifade de dizeler olduğunda art arda ekler.  
  
 Hiçbir ifade bir `Object` değilse, Visual Basic aşağıdaki eylemleri gerçekleştirir.  
  
|İfadelerin veri türleri|Derleyiciye göre eylem|  
|---|---|  
|Her iki ifade de sayısal veri türleridir (`SByte`, `Byte`, `Short`, `UShort`, `Integer`, `UInteger`, `Long`, `ULong`, `Decimal`, `Single` ya da 0)|Ekleyemiyorum. Sonuç veri türü, `expression1` ve `expression2` veri türleri için uygun bir sayısal türdür. [Işleç sonuçlarının veri türlerinde](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md)"tamsayı aritmetiği" tablolarına bakın.|  
|Her iki ifade @no__t türündedir-0|Karakter.|  
|Bir ifade sayısal bir veri türü ve diğeri bir dizedir|@No__t-0 ise-1 @no__t ve ardından bir derleyici hatası oluşturur.<br /><br /> @No__t-0 `Off` ise, `String` ' yi örtülü olarak `Double` ' e dönüştürün ve ekleyin.<br /><br /> @No__t-0 ' ı `Double` ' e dönüştürülemiyorsa, <xref:System.InvalidCastException> özel durumu oluşturun.|  
|Bir ifade sayısal bir veri türüdür ve diğeri [Nothing](../../../visual-basic/language-reference/nothing.md) değildir|@No__t-0 değeri sıfır olarak değer ile ekleyin.|  
|Bir ifade bir dizedir ve diğeri `Nothing` ' dır|Birleştir, `Nothing` ile "" olarak değerlendirilir.|  
  
 Bir ifade `Object` ifadesiyse Visual Basic aşağıdaki eylemleri gerçekleştirir.  
  
|İfadelerin veri türleri|Derleyiciye göre eylem|  
|---|---|  
|`Object` ifadesi sayısal bir değer ve diğeri ise sayısal bir veri türüdür|@No__t-0 ise-1 @no__t ve ardından bir derleyici hatası oluşturur.<br /><br /> @No__t-0 `Off` ise ekleyin.|  
|`Object` ifadesi sayısal bir değer ve diğeri tür `String` ' i barındırır|@No__t-0 ise-1 @no__t ve ardından bir derleyici hatası oluşturur.<br /><br /> @No__t-0 `Off` ise, `String` ' yi örtülü olarak `Double` ' e dönüştürün ve ekleyin.<br /><br /> @No__t-0 ' ı `Double` ' e dönüştürülemiyorsa, <xref:System.InvalidCastException> özel durumu oluşturun.|  
|`Object` ifadesi bir dize ve diğeri ise sayısal bir veri türüdür|@No__t-0 ise-1 @no__t ve ardından bir derleyici hatası oluşturur.<br /><br /> @No__t-0 `Off` ise, `Object` dizesini örtülü olarak `Double` ' e dönüştürün ve ekleyin.<br /><br /> @No__t-0 dizesi `Double` ' e dönüştürülemiyorsa, <xref:System.InvalidCastException> özel durumu oluşturun.|  
|`Object` ifadesi bir dize ve diğeri tür `String` ' i barındırır|@No__t-0 ise-1 @no__t ve ardından bir derleyici hatası oluşturur.<br /><br /> @No__t-0 `Off` ise, örtük olarak `Object` ' ye `String` ' e dönüştürün ve birleştirme.|  
  
 Her iki ifade `Object` ifadeleridir, Visual Basic aşağıdaki eylemleri gerçekleştirir (yalnızca `Option Strict Off`).  
  
|İfadelerin veri türleri|Derleyiciye göre eylem|  
|---|---|  
|@No__t-0 ifadeleri sayısal değerleri tutar|Ekleyemiyorum.|  
|@No__t-0 ifadesi her ikisi de `String` türündedir|Karakter.|  
|Bir `Object` ifadesi sayısal bir değer ve diğeri bir dize tutar|@No__t-0 dizesini örtük olarak `Double` ' e dönüştürün ve ekleyin.<br /><br /> @No__t-0 dizesi sayısal bir değere dönüştürülemiyorsa, bir <xref:System.InvalidCastException> özel durumu oluşturun.|  
  
 @No__t-0 ifadesi [Nothing](../../../visual-basic/language-reference/nothing.md) veya <xref:System.DBNull> olarak değerlendirilirse, `+` işleci bunu "" değeriyle `String` olarak değerlendirir.  
  
> [!NOTE]
> @No__t-0 işlecini kullandığınızda, ekleme veya dize birleştirme işleminin yapılıp yapılmayacağını belirleyemeyebilirsiniz. Belirsizliği ortadan kaldırmak ve kendi kendine belgeleme kodu sağlamak için, birleştirmek üzere `&` işlecini kullanın.  
  
## <a name="overloading"></a>Aşırı Yükleme  
 @No__t-0 işleci *aşırı*yüklenebilir, yani bir işlenen bu sınıf veya yapının türüne sahip olduğunda bir sınıf veya yapının davranışını yeniden tanımlayabileceği anlamına gelir. Kodunuz böyle bir sınıf veya yapıda bu işleci kullanıyorsa, yeniden tanımlanmış davranışını anladığınızdan emin olun. Daha fazla bilgi için bkz. [operatör yordamları](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, sayı eklemek için `+` işlecini kullanır. İşlenenler her ikisi de sayısal ise, Visual Basic aritmetik sonucu hesaplar. Aritmetik sonuç, iki işlenenin toplamını temsil eder.  
  
 [!code-vb[VbVbalrOperators#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#6)]  
  
 Dizeleri birleştirmek için `+` işlecini de kullanabilirsiniz. İşlenenler her iki dizise, Visual Basic bunları birleştirir. Birleştirme sonucu, iki işleneninin içeriğinden oluşan tek bir dizeyi temsil eder.  
  
 İşlenenler karışık türlerinise, sonuç, [Option Strict deyimin](../../../visual-basic/language-reference/statements/option-strict-statement.md)ayarına bağlıdır. Aşağıdaki örnekte `Option Strict` `On` olduğunda sonuç gösterilmektedir.  
  
 [!code-vb[VbVbalrOperators#53](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class3.vb#53)]  
  
 [!code-vb[VbVbalrOperators#50](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class2.vb#50)]  
[!code-vb[VbVbalrOperators#51](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class2.vb#51)]  
  
 Aşağıdaki örnekte `Option Strict` `Off` olduğunda sonuç gösterilmektedir.  
  
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
