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
ms.openlocfilehash: ab18a7137a31ed8e616f465e7d617305c96d7b10
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69943019"
---
# <a name="-operator-visual-basic"></a>+ İşleci (Visual Basic)
İki sayı ekler veya sayısal bir ifadenin pozitif değerini döndürür. , İki dize ifadesini birleştirmek için de kullanılabilir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```vb
expression1 + expression2  
- or -  
+ expression1  
```  
  
## <a name="parts"></a>Bölümler  
  
|Terim|Tanım|  
|---|---|  
|`expression1`|Gerekli. Herhangi bir sayısal veya dize ifadesi.|  
|`expression2`|İşleç negatif bir `+` değer hesaplanmadığı için gereklidir. Herhangi bir sayısal veya dize ifadesi.|  
  
## <a name="result"></a>Sonuç  
 `expression1` Ve`expression2` her ikisi de ise, sonuç Aritmetik toplamdır.  
  
 Yoksa `expression2` , işleci bir ifadenin değiştirilmemiş değeri için birli kimlik işleçtir. `+` Bu anlamda, işlem işaretini `expression1`korur, bu nedenle sonuç negatifse `expression1` negatif olur.  
  
 `expression1` Ve`expression2` her iki dizise sonuç, değerlerinin birleştirilmesiyle sonuçlanır.  
  
 Ve karışık türlerdir, uygulanan eylem türlerine, içeriğine ve [katı deyimin seçeneğine](../../../visual-basic/language-reference/statements/option-strict-statement.md)göre değişir. `expression2` `expression1` Daha fazla bilgi için "Notlar" içindeki tablolara bakın.  
  
## <a name="supported-types"></a>Desteklenen türler  
 İşaretsiz ve kayan nokta türleri ve `Decimal`ve `String`dahil olmak üzere tüm sayısal türler.  
  
## <a name="remarks"></a>Açıklamalar  
 Genel olarak, `+` mümkün olduğunda aritmetik ekleme gerçekleştirir ve yalnızca her iki ifade de dizeler olduğunda art arda ekler.  
  
 Ne ifade `Object`yoksa Visual Basic aşağıdaki eylemleri gerçekleştirir.  
  
|İfadelerin veri türleri|Derleyiciye göre eylem|  
|---|---|  
|Her iki ifade de sayısal veri türleridir`SByte`( `Byte`, `Short`, `UShort`, `Integer`, `UInteger`, `Long`, `ULong`, ,`Decimal` ,`Single`veya )`Double`|Ekleyemiyorum. Sonuç veri türü `expression1` ve `expression2`veri türleri için uygun bir sayısal türdür. [Işleç sonuçlarının veri türlerinde](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md)"tamsayı aritmetiği" tablolarına bakın.|  
|Her iki ifade de tür`String`|Karakter.|  
|Bir ifade sayısal bir veri türü ve diğeri bir dizedir|`Option Strict` İse`On`, bir derleyici hatası oluşturur.<br /><br /> İse, öğesini `String` örtülü olarak öğesine `Double` dönüştürün ve ekleyin. `Off` `Option Strict`<br /><br /> Öğesine dönüştürülemiyorsa, bir <xref:System.InvalidCastException> özel durum oluşturun. `Double` `String`|  
|Bir ifade sayısal bir veri türüdür ve diğeri [Nothing](../../../visual-basic/language-reference/nothing.md) değildir|Değerini, `Nothing` sıfıra kadar değerli şekilde ekleyin.|  
|Bir ifade bir dizedir ve diğeri`Nothing`|"" İle `Nothing` birlikte birleştir.|  
  
 Bir ifade bir `Object` ifadesiyse, Visual Basic aşağıdaki eylemleri gerçekleştirir.  
  
|İfadelerin veri türleri|Derleyiciye göre eylem|  
|---|---|  
|`Object`ifade sayısal bir değer ve diğeri ise sayısal bir veri türü tutar|`Option Strict` İse`On`, bir derleyici hatası oluşturur.<br /><br /> `Option Strict` İse`Off`, ekleyin.|  
|`Object`ifade bir sayısal değer ve diğeri tür`String`|`Option Strict` İse`On`, bir derleyici hatası oluşturur.<br /><br /> İse, öğesini `String` örtülü olarak öğesine `Double` dönüştürün ve ekleyin. `Off` `Option Strict`<br /><br /> Öğesine dönüştürülemiyorsa, bir <xref:System.InvalidCastException> özel durum oluşturun. `Double` `String`|  
|`Object`ifade bir dize tutar ve diğeri sayısal bir veri türü|`Option Strict` İse`On`, bir derleyici hatası oluşturur.<br /><br /> `Option Strict` İse ,`Off` dizeyi`Object` örtük olarak öğesine`Double` dönüştürün ve ekleyin.<br /><br /> Dize `Object` <xref:System.InvalidCastException> öğesine `Double`dönüştürülemiyorsa, bir özel durum oluşturun.|  
|`Object`ifade bir dizeyi ve diğeri türü tutar`String`|`Option Strict` İse`On`, bir derleyici hatası oluşturur.<br /><br /> `Option Strict` `Object` İse`String` , örtülüolarak`Off`Dönüştür ve birleştir.|  
  
 Her iki ifade de `Object` ifadeleridir, Visual Basic aşağıdaki eylemleri alır (`Option Strict Off` yalnızca).  
  
|İfadelerin veri türleri|Derleyiciye göre eylem|  
|---|---|  
|Her `Object` iki ifade de sayısal değerleri tutar|Ekleyemiyorum.|  
|Her `Object` iki ifade de tür`String`|Karakter.|  
|Bir `Object` ifade sayısal bir değer ve diğeri bir dize tutar|Dizeyi `Object` örtük olarak öğesine `Double` dönüştürün ve ekleyin.<br /><br /> Dize `Object` sayısal bir değere dönüştürülemiyorsa, bir <xref:System.InvalidCastException> özel durum oluşturun.|  
  
 Her iki `Object` ifade de [Nothing](../../../visual-basic/language-reference/nothing.md) <xref:System.DBNull>olarak değerlendirilirse, `+` işleci bunu "" değeri ile `String` bir olarak değerlendirir.  
  
> [!NOTE]
> `+` İşlecini kullandığınızda, ekleme veya dize birleştirme işleminin yapılıp yapılmayacağını belirleyemeyebilirsiniz. Belirsizliği ortadan kaldırmak ve kendi kendine belgeleme kodu sağlamak için birleştirme işlecinikullanın.`&`  
  
## <a name="overloading"></a>Aşırı Yükleme  
 İşleç aşırı yüklenebilir, yani bir işlenen bu sınıf veya yapının türüne sahip olduğunda bir sınıf veya yapının davranışını yeniden tanımlayabileceği anlamına gelir. `+` Kodunuz böyle bir sınıf veya yapıda bu işleci kullanıyorsa, yeniden tanımlanmış davranışını anladığınızdan emin olun. Daha fazla bilgi için bkz. [operatör yordamları](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, sayı eklemek `+` için işlecini kullanır. İşlenenler her ikisi de sayısal ise, Visual Basic aritmetik sonucu hesaplar. Aritmetik sonuç, iki işlenenin toplamını temsil eder.  
  
 [!code-vb[VbVbalrOperators#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#6)]  
  
 Ayrıca, `+` dizeleri birleştirmek için işlecini de kullanabilirsiniz. İşlenenler her iki dizise, Visual Basic bunları birleştirir. Birleştirme sonucu, iki işleneninin içeriğinden oluşan tek bir dizeyi temsil eder.  
  
 İşlenenler karışık türlerinise, sonuç, [Option Strict deyimin](../../../visual-basic/language-reference/statements/option-strict-statement.md)ayarına bağlıdır. Aşağıdaki örnek, olduğu `Option Strict` `On`zaman sonucunu gösterir.  
  
 [!code-vb[VbVbalrOperators#53](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class3.vb#53)]  
  
 [!code-vb[VbVbalrOperators#50](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class2.vb#50)]  
[!code-vb[VbVbalrOperators#51](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class2.vb#51)]  
  
 Aşağıdaki örnek, olduğu `Option Strict` `Off`zaman sonucunu gösterir.  
  
 [!code-vb[VbVbalrOperators#54](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class2.vb#54)]  
  
 [!code-vb[VbVbalrOperators#50](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class2.vb#50)]  
[!code-vb[VbVbalrOperators#52](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class2.vb#52)]  
  
 Belirsizliği ortadan kaldırmak için, birleştirmek `&` `+` yerine işlecini kullanmanız gerekir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [& İşleci](../../../visual-basic/language-reference/operators/concatenation-operator.md)
- [Birleştirme İşleçleri](../../../visual-basic/language-reference/operators/concatenation-operators.md)
- [Aritmetik İşleçler](../../../visual-basic/language-reference/operators/arithmetic-operators.md)
- [İşlevselliğe Göre Listelenmiş İşleçler](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [Visual Basic operatör önceliği](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [Visual Basic aritmetik Işleçler](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
- [Option Strict Deyimi](../../../visual-basic/language-reference/statements/option-strict-statement.md)
