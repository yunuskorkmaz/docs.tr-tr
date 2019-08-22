---
title: Karşılaştırma İşleçleri (Visual Basic)
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
ms.openlocfilehash: 10558563b528ce0bae3f77f31a97a217018f455f
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/21/2019
ms.locfileid: "69666832"
---
# <a name="comparison-operators-visual-basic"></a>Karşılaştırma İşleçleri (Visual Basic)
Aşağıda, Visual Basic tanımlanan karşılaştırma işleçleri verilmiştir.

 `<`işlecinde

 `<=`işlecinde

 `>`işlecinde

 `>=`işlecinde

 `=`işlecinde

 `<>`işlecinde

 [Is İşleci](../../../visual-basic/language-reference/operators/is-operator.md)

 [IsNot İşleci](../../../visual-basic/language-reference/operators/isnot-operator.md)

 [Like İşleci](../../../visual-basic/language-reference/operators/like-operator.md)

 Bu işleçler, eşit olup olmadığını ve değilse ne farklılık olduğunu anlamak için iki ifadeyi karşılaştırır. `Is`, `IsNot` ve`Like` ayrı Yardım sayfalarında ayrıntılı olarak ele alınmıştır. İlişkisel karşılaştırma işleçleri bu sayfada ayrıntılı olarak ele alınmıştır.

## <a name="syntax"></a>Sözdizimi
  
```vb
result = expression1 comparisonoperator expression2  
result = object1 [Is | IsNot] object2  
result = string Like pattern  
```  
  
## <a name="parts"></a>Bölümler
 `result`  
 Gerekli. Karşılaştırmanın `Boolean` sonucunu temsil eden bir değer.

 `expression1`, `expression2`  
 Gerekli. Herhangi bir ifade.

 `comparisonoperator`  
 Gerekli. Herhangi bir ilişkisel karşılaştırma işleci.

 `object1`, `object2`  
 Gerekli. Herhangi bir başvuru nesnesi adı.

 `string`  
 Gerekli. Herhangi `String` bir ifade.

 `pattern`  
 Gerekli. Herhangi `String` bir ifade veya karakter aralığı.

## <a name="remarks"></a>Açıklamalar
 Aşağıdaki tabloda, ilişkisel karşılaştırma işleçleri ve olup olmadığını `result` `True` `False`belirleme koşulları yer almaktadır.

|İşleç|`True`kullandıysanız|`False`kullandıysanız|
|--------------|---------------|----------------|
|`<`(Küçüktür)|`expression1` < `expression2`|`expression1` >= `expression2`|
|`<=`(Küçüktür veya eşittir)|`expression1` <= `expression2`|`expression1` > `expression2`|
|`>`(Büyüktür)|`expression1` > `expression2`|`expression1` <= `expression2`|
|`>=`(Büyüktür veya eşittir)|`expression1` >= `expression2`|`expression1` < `expression2`|
|`=`(Eşittir)|`expression1` = `expression2`|`expression1` <> `expression2`|
|`<>`(Eşit değildir)|`expression1` <> `expression2`|`expression1` = `expression2`|

> [!NOTE]
>  [= İşleci](../../../visual-basic/language-reference/operators/assignment-operator.md) atama işleci olarak da kullanılır.

 İşleci, işleci ve`Like` işleci, önceki tablodaki işleçlerden farklı olan özel karşılaştırma işlevlerine sahiptir. `IsNot` `Is`

## <a name="comparing-numbers"></a>Sayıları karşılaştırma
 Türünde `Single` bir ifadeyi türünden `Double`birine karşılaştırdığınızda, `Single` ifadesi öğesine `Double`dönüştürülür. Bu davranış, Visual Basic 6 ' da bulunan davranışın tersidir.

 Benzer şekilde, türü `Decimal` bir ifadesini veya `Double`türünde `Single` bir ifadeye karşılaştırdığınızda, `Decimal` ifade `Single` veya `Double`' a dönüştürülür. İfadeler `Decimal` için, 1E-28 ' den küçük herhangi bir kesirli değer kaybolmuş olabilir. Bu tür kesirli değer kaybı, iki değerin, olmadıkları zaman eşit olarak karşılaştırılmasını sağlayabilir. Bu nedenle, iki kayan nokta değişkenini karşılaştırmak için eşitlik (`=`) kullanırken dikkatli olmanız gerekir. İki sayı arasındaki farkın mutlak değerinin, kabul edilebilir küçük bir toleranstan daha az olup olmadığını test etmek daha güvenlidir.

### <a name="floating-point-imprecision"></a>Kayan nokta noktasında kesinlik eksikliği
 Kayan noktalı sayılarla çalışırken her zaman bellekte kesin bir gösterimine sahip olmadıkları göz önünde bulundurun. Bu, değer karşılaştırması ve [Mod işleci](../../../visual-basic/language-reference/operators/mod-operator.md)gibi belirli işlemlerden beklenmedik sonuçlara neden olabilir. Daha fazla bilgi için bkz. [sorun giderme veri türleri](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md).

## <a name="comparing-strings"></a>Dizeleri Karşılaştırma
 Dizeleri karşılaştırdığınızda, dize ifadeleri alfabetik sıralama sıralamasına göre değerlendirilir ve bu `Option Compare` ayar değişir.

 `Option Compare Binary`, karakterlerin iç ikili gösterimlerine göre türetilmiş bir sıralama düzeninde dize karşılaştırmaları dayandırır. Sıralama düzeni kod sayfası tarafından belirlenir. Aşağıdaki örnek tipik bir ikili sıralama düzeni gösterir.

 `A < B < E < Z < a < b < e < z < À < Ê < Ø < à < ê < ø`

 `Option Compare Text`, uygulamanızın yerel ayarı tarafından belirlenen büyük/küçük harf duyarsız, metinsel sıralama düzeninde dize karşılaştırmaları dayandırır. Önceki örnekteki karakterleri `Option Compare Text` ayarlayıp sıraladığınızda aşağıdaki metin sıralama düzeni geçerlidir:

 `(A=a) < (À= à) < (B=b) < (E=e) < (Ê= ê) < (Ø = ø) < (Z=z)`

### <a name="locale-dependence"></a>Yerel ayar bağımlılığını
 Ayarladığınızda `Option Compare Text`, bir dize karşılaştırmasının sonucu uygulamanın çalıştığı yerel ayara bağlı olabilir. İki karakter, bir yerel ayarda eşit olarak karşılaştırılabilir ancak başka bir şekilde karşılaştırılabilir. Oturum açma denemesinin kabul edilip edilmeyeceğini kabul etmeksizin, önemli kararlar almak için bir dize karşılaştırması kullanıyorsanız, yerel ayar duyarlılığı için uyarı almanız gerekir. Yerel ayarı hesabına `Option Compare Binary` alan <xref:Microsoft.VisualBasic.Strings.StrComp%2A>öğesini ayarlamayı veya çağırmayı düşünün.

## <a name="typeless-programming-with-relational-comparison-operators"></a>Ilişkisel karşılaştırma Işleçleri ile Türsüz programlama
 İçinde deyimlerle `Object` ilişkisel karşılaştırma işleçleri kullanımına `Option Strict On`izin verilmez. Olduğundave`Option Strict` ya da `expression1` bir`Object`ifade olduğunda, çalışma zamanı türleri nasıl karşılaştırıldığını tespit edilir. `expression2` `Off` Aşağıdaki tabloda, işlenenlerinin çalışma zamanı türüne bağlı olarak ifadelerin karşılaştırılacağı ve Karşılaştırmanın sonucu gösterilmektedir.

|İşlenenler|Karşılaştırma|
|---------------------|-------------------|
|İs`String`|Dize sıralama özelliklerine göre karşılaştırmayı sıralayın.|
|Her iki sayısal|`Double`' A dönüştürülen nesneler, sayısal karşılaştırmaya.|
|Bir sayısal ve bir`String`|, `String` Bir değerine dönüştürülür ve `Double` sayısal bir karşılaştırmaya yapılır. Öğesine dönüştürülemiyorsa, bir <xref:System.InvalidCastException> atılır. `Double` `String`|
|Ya da her ikisi birden dışında başvuru türleridir`String`|Bir <xref:System.InvalidCastException> oluşturulur.|

 Sayısal karşılaştırmalar 0 `Nothing` olarak değerlendirilir. Dize karşılaştırmaları ( `Nothing` boş `""` bir dize) olarak değerlendirilir.

## <a name="overloading"></a>Aşırı Yükleme
 İlişkisel karşılaştırma işleçleri (`<`. `<=``>`,, ,`<>`,) aşırı yüklenebilir, yani bir işlenen bu sınıf veya yapının türüne sahip olduğunda bir sınıf veya yapının davranışlarını yeniden tanımlayabileceği anlamına gelir. `=` `>=` Kodunuz böyle bir sınıf veya yapıda bu işleçlerden herhangi birini kullanıyorsa, yeniden tanımlanan davranışı anladığınızdan emin olun. Daha fazla bilgi için bkz. [operatör yordamları](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).

 [= İşlecinin](../../../visual-basic/language-reference/operators/assignment-operator.md) , atama işleci olarak değil, yalnızca ilişkisel karşılaştırma operatörü olarak aşırı yüklenebilir olduğuna dikkat edin.

## <a name="example"></a>Örnek
 Aşağıdaki örnek, ifadeleri karşılaştırmak için kullandığınız, ilişkisel karşılaştırma işleçlerinin çeşitli kullanımlarını gösterir. İlişkisel karşılaştırma işleçleri, belirtilen `Boolean` ifadenin olarak `True`değerlendirilip değerlendirilmediğini temsil eden bir sonuç döndürür. `>` Ve`<` işleçlerini dizelere uyguladığınızda, karşılaştırma, dizelerin normal alfabetik sıralama düzeni kullanılarak yapılır. Bu sipariş, yerel ayara bağlı olabilir. Sıralamanın büyük/küçük harfe duyarlı olup olmadığı veya [Seçenek karşılaştırma](../../../visual-basic/language-reference/statements/option-compare-statement.md) ayarına bağlı olup olmadığı.

 [!code-vb[VbVbalrOperators#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#1)]

 Önceki örnekte, ilk karşılaştırma döndürülür `False` ve kalan `True`karşılaştırmalar döndürülür.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.InvalidCastException>
- [= İşleci](../../../visual-basic/language-reference/operators/assignment-operator.md)
- [Visual Basic operatör önceliği](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [İşlevselliğe Göre Listelenmiş İşleçler](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [Veri Türü Sorunlarını Giderme](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)
- [Visual Basic karşılaştırma Işleçleri](../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)
