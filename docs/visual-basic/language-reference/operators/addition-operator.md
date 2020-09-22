---
title: + Operatör
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
ms.openlocfilehash: bc31e4c66c64d891e3fffd809b7ae99b9c9a0520
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90873453"
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
|`expression1`|Gereklidir. Herhangi bir sayısal veya dize ifadesi.|  
|`expression2`|`+`İşleç negatif bir değer hesaplanmadığı için gereklidir. Herhangi bir sayısal veya dize ifadesi.|  
  
## <a name="result"></a>Sonuç  

 `expression1`Ve `expression2` her ikisi de ise, sonuç Aritmetik toplamdır.  
  
 Yoksa `expression2` , `+` işleci bir ifadenin değiştirilmemiş değeri için *birli* kimlik işleçtir. Bu anlamda, işlem işaretini korur `expression1` , bu nedenle sonuç negatifse negatif olur `expression1` .  
  
 `expression1`Ve `expression2` her iki dizise sonuç, değerlerinin birleştirilmesiyle sonuçlanır.  
  
 `expression1`Ve `expression2` karışık türlerdir, uygulanan eylem türlerine, Içeriğine ve [katı deyimin seçeneğine](../statements/option-strict-statement.md)göre değişir. Daha fazla bilgi için "Notlar" içindeki tablolara bakın.  
  
## <a name="supported-types"></a>Desteklenen türler  

 İşaretsiz ve kayan nokta türleri ve ve dahil olmak üzere tüm sayısal türler `Decimal` `String` .  
  
## <a name="remarks"></a>Açıklamalar  

 Genel olarak, `+` mümkün olduğunda aritmetik ekleme gerçekleştirir ve yalnızca her iki ifade de dizeler olduğunda art arda ekler.  
  
 Ne ifade yoksa `Object` Visual Basic aşağıdaki eylemleri gerçekleştirir.  
  
|İfadelerin veri türleri|Derleyiciye göre eylem|  
|---|---|  
|Her iki ifade de sayısal veri türleridir ( `SByte` , `Byte` ,, `Short` `UShort` , `Integer` , `UInteger` , `Long` , `ULong` , `Decimal` , `Single` veya `Double` )|Ekle. Sonuç veri türü ve veri türleri için uygun bir sayısal türdür `expression1` `expression2` . [Işleç sonuçlarının veri türlerinde](data-types-of-operator-results.md)"tamsayı aritmetiği" tablolarına bakın.|  
|Her iki ifade de tür `String`|Karakter.|  
|Bir ifade sayısal bir veri türü ve diğeri bir dizedir|`Option Strict`İse `On` , bir derleyici hatası oluşturur.<br /><br /> İse, öğesini `Option Strict` `Off` örtülü olarak öğesine dönüştürün `String` `Double` ve ekleyin.<br /><br /> `String`Öğesine dönüştürülemiyorsa `Double` , bir <xref:System.InvalidCastException> özel durum oluşturun.|  
|Bir ifade sayısal bir veri türüdür ve diğeri [Nothing](../nothing.md) değildir|`Nothing`Değerini, sıfıra kadar değerli şekilde ekleyin.|  
|Bir ifade bir dizedir ve diğeri `Nothing`|"" İle birlikte Birleştir `Nothing` .|  
  
 Bir ifade bir `Object` ifadesiyse, Visual Basic aşağıdaki eylemleri gerçekleştirir.  
  
|İfadelerin veri türleri|Derleyiciye göre eylem|  
|---|---|  
|`Object` ifade sayısal bir değer ve diğeri ise sayısal bir veri türü tutar|`Option Strict`İse `On` , bir derleyici hatası oluşturur.<br /><br /> `Option Strict`İse `Off` , ekleyin.|  
|`Object` ifade bir sayısal değer ve diğeri tür `String`|`Option Strict`İse `On` , bir derleyici hatası oluşturur.<br /><br /> İse, öğesini `Option Strict` `Off` örtülü olarak öğesine dönüştürün `String` `Double` ve ekleyin.<br /><br /> `String`Öğesine dönüştürülemiyorsa `Double` , bir <xref:System.InvalidCastException> özel durum oluşturun.|  
|`Object` ifade bir dize tutar ve diğeri sayısal bir veri türü|`Option Strict`İse `On` , bir derleyici hatası oluşturur.<br /><br /> `Option Strict`İse `Off` , dizeyi örtük olarak `Object` öğesine dönüştürün `Double` ve ekleyin.<br /><br /> Dize `Object` öğesine dönüştürülemiyorsa `Double` , bir <xref:System.InvalidCastException> özel durum oluşturun.|  
|`Object` ifade bir dizeyi ve diğeri türü tutar `String`|`Option Strict`İse `On` , bir derleyici hatası oluşturur.<br /><br /> `Option Strict`İse `Off` , örtülü olarak Dönüştür `Object` `String` ve birleştir.|  
  
 Her iki ifade de `Object` ifadeleridir, Visual Basic aşağıdaki eylemleri alır ( `Option Strict Off` yalnızca).  
  
|İfadelerin veri türleri|Derleyiciye göre eylem|  
|---|---|  
|Her iki `Object` ifade de sayısal değerleri tutar|Ekle.|  
|Her iki `Object` ifade de tür `String`|Karakter.|  
|Bir `Object` ifade sayısal bir değer ve diğeri bir dize tutar|Dizeyi örtük olarak `Object` öğesine dönüştürün `Double` ve ekleyin.<br /><br /> Dize `Object` sayısal bir değere dönüştürülemiyorsa, bir <xref:System.InvalidCastException> özel durum oluşturun.|  
  
 Her iki `Object` ifade de [Nothing](../nothing.md) olarak değerlendirilirse <xref:System.DBNull> , `+` işleci bunu `String` "" değeri ile bir olarak değerlendirir.  
  
> [!NOTE]
> `+`İşlecini kullandığınızda, ekleme veya dize birleştirme işleminin yapılıp yapılmayacağını belirleyemeyebilirsiniz. `&`Belirsizliği ortadan kaldırmak ve kendi kendine belgeleme kodu sağlamak için birleştirme işlecini kullanın.  
  
## <a name="overloading"></a>Aşırı Yükleme  

 `+`İşleç *aşırı*yüklenebilir, yani bir işlenen bu sınıf veya yapının türüne sahip olduğunda bir sınıf veya yapının davranışını yeniden tanımlayabileceği anlamına gelir. Kodunuz böyle bir sınıf veya yapıda bu işleci kullanıyorsa, yeniden tanımlanmış davranışını anladığınızdan emin olun. Daha fazla bilgi için bkz. [operatör yordamları](../../programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Örnek  

 Aşağıdaki örnek, `+` sayı eklemek için işlecini kullanır. İşlenenler her ikisi de sayısal ise, Visual Basic aritmetik sonucu hesaplar. Aritmetik sonuç, iki işlenenin toplamını temsil eder.  
  
 [!code-vb[VbVbalrOperators#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#6)]  
  
 Ayrıca, `+` dizeleri birleştirmek için işlecini de kullanabilirsiniz. İşlenenler her iki dizise, Visual Basic bunları birleştirir. Birleştirme sonucu, iki işleneninin içeriğinden oluşan tek bir dizeyi temsil eder.  
  
 İşlenenler karışık türlerinise, sonuç, [Option Strict deyimin](../statements/option-strict-statement.md)ayarına bağlıdır. Aşağıdaki örnek, olduğu zaman sonucunu gösterir `Option Strict` `On` .  
  
 [!code-vb[VbVbalrOperators#53](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class3.vb#53)]  
  
 [!code-vb[VbVbalrOperators#50](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class2.vb#50)]  
[!code-vb[VbVbalrOperators#51](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class2.vb#51)]  
  
 Aşağıdaki örnek, olduğu zaman sonucunu gösterir `Option Strict` `Off` .  
  
 [!code-vb[VbVbalrOperators#54](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class2.vb#54)]  
  
 [!code-vb[VbVbalrOperators#50](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class2.vb#50)]  
[!code-vb[VbVbalrOperators#52](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class2.vb#52)]  
  
 Belirsizliği ortadan kaldırmak için, `&` birleştirmek yerine işlecini kullanmanız gerekir `+` .  
  
## <a name="see-also"></a>Ayrıca bkz.

- [& Işleci](concatenation-operator.md)
- [Birleştirme İşleçleri](concatenation-operators.md)
- [Aritmetik Işleçler](arithmetic-operators.md)
- [İşlevselliğe Göre Listelenmiş İşleçler](operators-listed-by-functionality.md)
- [Visual Basic'de İşleç Önceliği](operator-precedence.md)
- [Visual Basic'de Aritmetik İşleçler](../../programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
- [Option Strict Deyimi](../statements/option-strict-statement.md)
