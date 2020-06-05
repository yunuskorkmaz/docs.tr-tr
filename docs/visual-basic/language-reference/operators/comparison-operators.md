---
title: Karşılaştırma İşleçleri
ms.date: 07/20/2015
f1_keywords:
- vb.<>
- vb.>=
- vb.<=
- vb.>
- vb.<
helpviewer_keywords:
- greater than or equal to operator [Visual Basic]
- '>= operator [Visual Basic]'
- = operator [Visual Basic]
- < operator [Visual Basic]
- less than operator [Visual Basic]
- relational operators [Visual Basic], syntax
- Like operator [Visual Basic]
- <> operator [Visual Basic]
- '> operator [Visual Basic]'
- equal operator [Visual Basic]
- less than or equal to operator [Visual Basic]
- symbols, operators
- greater than operator [Visual Basic]
- comparing values [Visual Basic]
- operators [Visual Basic], relational
- string comparison [Visual Basic]
- not equal to comparison operator [Visual Basic]
- <= operator [Visual Basic]
- operators [Visual Basic], comparison
- Is operator [Visual Basic]
- comparison operators [Visual Basic], Visual Basic
ms.assetid: d6cb12a8-e52e-46a7-8aaf-f804d634a825
ms.openlocfilehash: bcd51d70c5c7bd08991c7433e244316a82daa9da
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84371797"
---
# <a name="comparison-operators-visual-basic"></a>Karşılaştırma İşleçleri (Visual Basic)
Aşağıda, Visual Basic tanımlanan karşılaştırma işleçleri verilmiştir.

 `<`işlecinde

 `<=`işlecinde

 `>`işlecinde

 `>=`işlecinde

 `=`işlecinde

 `<>`işlecinde

 [Is İşleci](is-operator.md)

 [IsNot İşleci](isnot-operator.md)

 [Like İşleci](like-operator.md)

 Bu işleçler, eşit olup olmadığını ve değilse ne farklılık olduğunu anlamak için iki ifadeyi karşılaştırır. `Is`, `IsNot` ve `Like` ayrı Yardım sayfalarında ayrıntılı olarak ele alınmıştır. İlişkisel karşılaştırma işleçleri bu sayfada ayrıntılı olarak ele alınmıştır.

## <a name="syntax"></a>Sözdizimi
  
```vb
result = expression1 comparisonoperator expression2  
result = object1 [Is | IsNot] object2  
result = string Like pattern  
```  
  
## <a name="parts"></a>Bölümler
 `result`  
 Gereklidir. `Boolean`Karşılaştırmanın sonucunu temsil eden bir değer.

 `expression1`, `expression2`  
 Gereklidir. Herhangi bir ifade.

 `comparisonoperator`  
 Gereklidir. Herhangi bir ilişkisel karşılaştırma işleci.

 `object1`, `object2`  
 Gereklidir. Herhangi bir başvuru nesnesi adı.

 `string`  
 Gereklidir. Herhangi bir `String` ifade.

 `pattern`  
 Gereklidir. Herhangi bir `String` ifade veya karakter aralığı.

## <a name="remarks"></a>Açıklamalar
 Aşağıdaki tabloda, ilişkisel karşılaştırma işleçleri ve olup olmadığını belirleme koşulları yer almaktadır `result` `True` `False` .

|Operatör|`True`kullandıysanız|`False`kullandıysanız|
|--------------|---------------|----------------|
|`<`(Küçüktür)|`expression1` < `expression2`|`expression1` >= `expression2`|
|`<=`(Küçüktür veya eşittir)|`expression1` <= `expression2`|`expression1` > `expression2`|
|`>`(Büyüktür)|`expression1` > `expression2`|`expression1` <= `expression2`|
|`>=`(Büyüktür veya eşittir)|`expression1` >= `expression2`|`expression1` < `expression2`|
|`=`(Eşittir)|`expression1` = `expression2`|`expression1` <> `expression2`|
|`<>`(Eşit değildir)|`expression1` <> `expression2`|`expression1` = `expression2`|

> [!NOTE]
> [= İşleci](assignment-operator.md) atama işleci olarak da kullanılır.

 İşleci `Is` , `IsNot` işleci ve `Like` işleci, önceki tablodaki işleçlerden farklı olan özel karşılaştırma işlevlerine sahiptir.

## <a name="comparing-numbers"></a>Sayıları karşılaştırma
 Türünde bir ifadeyi türünden birine karşılaştırdığınızda `Single` `Double` , `Single` ifadesi öğesine dönüştürülür `Double` . Bu davranış, Visual Basic 6 ' da bulunan davranışın tersidir.

 Benzer şekilde, türü bir ifadesini `Decimal` veya türünde bir ifadeye karşılaştırdığınızda `Single` `Double` , ifade veya ' a `Decimal` dönüştürülür `Single` `Double` . `Decimal`İfadeler için, 1E-28 ' den küçük herhangi bir kesirli değer kaybolmuş olabilir. Bu tür kesirli değer kaybı, iki değerin, olmadıkları zaman eşit olarak karşılaştırılmasını sağlayabilir. Bu nedenle, `=` iki kayan nokta değişkenini karşılaştırmak için eşitlik () kullanırken dikkatli olmanız gerekir. İki sayı arasındaki farkın mutlak değerinin, kabul edilebilir küçük bir toleranstan daha az olup olmadığını test etmek daha güvenlidir.

### <a name="floating-point-imprecision"></a>Kayan nokta noktasında kesinlik eksikliği
 Kayan noktalı sayılarla çalışırken her zaman bellekte kesin bir gösterimine sahip olmadıkları göz önünde bulundurun. Bu, değer karşılaştırması ve [Mod işleci](mod-operator.md)gibi belirli işlemlerden beklenmedik sonuçlara neden olabilir. Daha fazla bilgi için bkz. [sorun giderme veri türleri](../../programming-guide/language-features/data-types/troubleshooting-data-types.md).

## <a name="comparing-strings"></a>Dizeleri Karşılaştırma
 Dizeleri karşılaştırdığınızda, dize ifadeleri alfabetik sıralama sıralamasına göre değerlendirilir ve bu `Option Compare` ayar değişir.

 `Option Compare Binary`, karakterlerin iç ikili gösterimlerine göre türetilmiş bir sıralama düzeninde dize karşılaştırmaları dayandırır. Sıralama düzeni kod sayfası tarafından belirlenir. Aşağıdaki örnek tipik bir ikili sıralama düzeni gösterir.

 `A < B < E < Z < a < b < e < z < À < Ê < Ø < à < ê < ø`

 `Option Compare Text`, uygulamanızın yerel ayarı tarafından belirlenen büyük/küçük harf duyarsız, metinsel sıralama düzeninde dize karşılaştırmaları dayandırır. `Option Compare Text`Önceki örnekteki karakterleri ayarlayıp sıraladığınızda aşağıdaki metin sıralama düzeni geçerlidir:

 `(A=a) < (À= à) < (B=b) < (E=e) < (Ê= ê) < (Ø = ø) < (Z=z)`

### <a name="locale-dependence"></a>Yerel ayar bağımlılığını
 Ayarladığınızda `Option Compare Text` , bir dize karşılaştırmasının sonucu uygulamanın çalıştığı yerel ayara bağlı olabilir. İki karakter, bir yerel ayarda eşit olarak karşılaştırılabilir ancak başka bir şekilde karşılaştırılabilir. Oturum açma denemesinin kabul edilip edilmeyeceğini kabul etmeksizin, önemli kararlar almak için bir dize karşılaştırması kullanıyorsanız, yerel ayar duyarlılığı için uyarı almanız gerekir. `Option Compare Binary`Yerel ayarı hesabına alan öğesini ayarlamayı veya çağırmayı düşünün <xref:Microsoft.VisualBasic.Strings.StrComp%2A> .

## <a name="typeless-programming-with-relational-comparison-operators"></a>Ilişkisel karşılaştırma Işleçleri ile Türsüz programlama
 İçinde deyimlerle ilişkisel karşılaştırma işleçleri kullanımına `Object` izin verilmez `Option Strict On` . Olduğunda `Option Strict` `Off` ve ya da `expression1` `expression2` bir ifade olduğunda `Object` , çalışma zamanı türleri nasıl karşılaştırıldığını tespit edilir. Aşağıdaki tabloda, işlenenlerinin çalışma zamanı türüne bağlı olarak ifadelerin karşılaştırılacağı ve Karşılaştırmanın sonucu gösterilmektedir.

|İşlenenler|Karşılaştırma|
|---------------------|-------------------|
|İs`String`|Dize sıralama özelliklerine göre karşılaştırmayı sıralayın.|
|Her iki sayısal|' A dönüştürülen nesneler `Double` , sayısal karşılaştırmaya.|
|Bir sayısal ve bir`String`|, `String` Bir değerine dönüştürülür `Double` ve sayısal bir karşılaştırmaya yapılır. `String`Öğesine dönüştürülemiyorsa `Double` , bir <xref:System.InvalidCastException> atılır.|
|Ya da her ikisi birden dışında başvuru türleridir`String`|Bir oluşturulur <xref:System.InvalidCastException> .|

 Sayısal karşılaştırmalar `Nothing` 0 olarak değerlendirilir. Dize karşılaştırmaları `Nothing` `""` (boş bir dize) olarak değerlendirilir.

## <a name="overloading"></a>Aşırı Yükleme
 İlişkisel karşılaştırma işleçleri ( `<` . `<=`,,, `>` `>=` `=` , `<>` ) *aşırı*yüklenebilir, yani bir işlenen bu sınıf veya yapının türüne sahip olduğunda bir sınıf veya yapının davranışlarını yeniden tanımlayabileceği anlamına gelir. Kodunuz böyle bir sınıf veya yapıda bu işleçlerden herhangi birini kullanıyorsa, yeniden tanımlanan davranışı anladığınızdan emin olun. Daha fazla bilgi için bkz. [operatör yordamları](../../programming-guide/language-features/procedures/operator-procedures.md).

 [= İşlecinin](assignment-operator.md) , atama işleci olarak değil, yalnızca ilişkisel karşılaştırma operatörü olarak aşırı yüklenebilir olduğuna dikkat edin.

## <a name="example"></a>Örnek
 Aşağıdaki örnek, ifadeleri karşılaştırmak için kullandığınız, ilişkisel karşılaştırma işleçlerinin çeşitli kullanımlarını gösterir. İlişkisel karşılaştırma işleçleri `Boolean` , belirtilen ifadenin olarak değerlendirilip değerlendirilmediğini temsil eden bir sonuç döndürür `True` . `>`Ve `<` işleçlerini dizelere uyguladığınızda, karşılaştırma, dizelerin normal alfabetik sıralama düzeni kullanılarak yapılır. Bu sipariş, yerel ayara bağlı olabilir. Sıralamanın büyük/küçük harfe duyarlı olup olmadığı veya [Seçenek karşılaştırma](../statements/option-compare-statement.md) ayarına bağlı olup olmadığı.

 [!code-vb[VbVbalrOperators#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#1)]

 Önceki örnekte, ilk karşılaştırma döndürülür `False` ve kalan karşılaştırmalar döndürülür `True` .

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.InvalidCastException>
- [= İşleci](assignment-operator.md)
- [Visual Basic'de İşleç Önceliği](operator-precedence.md)
- [İşlevselliğe Göre Listelenmiş İşleçler](operators-listed-by-functionality.md)
- [Veri Türü Sorunlarını Giderme](../../programming-guide/language-features/data-types/troubleshooting-data-types.md)
- [Visual Basic'de Karşılaştırma İşleçleri](../../programming-guide/language-features/operators-and-expressions/comparison-operators.md)
