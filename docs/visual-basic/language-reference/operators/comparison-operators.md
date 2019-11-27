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
ms.openlocfilehash: ea7604626ede66da818e4bc22fe4922bc752dc2c
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74336080"
---
# <a name="comparison-operators-visual-basic"></a>Karşılaştırma İşleçleri (Visual Basic)
Aşağıda, Visual Basic tanımlanan karşılaştırma işleçleri verilmiştir.

 `<` işleci

 `<=` işleci

 `>` işleci

 `>=` işleci

 `=` işleci

 `<>` işleci

 [Is İşleci](../../../visual-basic/language-reference/operators/is-operator.md)

 [IsNot İşleci](../../../visual-basic/language-reference/operators/isnot-operator.md)

 [Like İşleci](../../../visual-basic/language-reference/operators/like-operator.md)

 Bu işleçler, eşit olup olmadığını ve değilse ne farklılık olduğunu anlamak için iki ifadeyi karşılaştırır. `Is`, `IsNot`ve `Like` ayrı Yardım sayfalarında ayrıntılı olarak ele alınmıştır. İlişkisel karşılaştırma işleçleri bu sayfada ayrıntılı olarak ele alınmıştır.

## <a name="syntax"></a>Sözdizimi
  
```vb
result = expression1 comparisonoperator expression2  
result = object1 [Is | IsNot] object2  
result = string Like pattern  
```  
  
## <a name="parts"></a>Bölümler
 `result`  
 Gerekli. Karşılaştırmanın sonucunu temsil eden bir `Boolean` değeri.

 `expression1`, `expression2`  
 Gerekli. Herhangi bir ifade.

 `comparisonoperator`  
 Gerekli. Herhangi bir ilişkisel karşılaştırma işleci.

 `object1`, `object2`  
 Gerekli. Herhangi bir başvuru nesnesi adı.

 `string`  
 Gerekli. Herhangi bir `String` ifadesi.

 `pattern`  
 Gerekli. Herhangi bir `String` ifadesi veya karakter aralığı.

## <a name="remarks"></a>Açıklamalar
 Aşağıdaki tabloda, ilişkisel karşılaştırma işleçleri listesi ve `result` `True` veya `False`olup olmadığını belirleme koşulları yer almaktadır.

|İşleç|`True`|`False`|
|--------------|---------------|----------------|
|`<` (küçüktür)|`expression1` < `expression2`|`expression1` >= `expression2`|
|`<=` (küçüktür veya eşittir)|`expression1` <= `expression2`|`expression1` > `expression2`|
|`>` (büyüktür)|`expression1` > `expression2`|`expression1` <= `expression2`|
|`>=` (büyüktür veya eşittir)|`expression1` >= `expression2`|`expression1` < `expression2`|
|`=` (eşittir)|`expression1` = `expression2`|`expression1` <> `expression2`|
|`<>` (eşit değildir)|`expression1` <> `expression2`|`expression1` = `expression2`|

> [!NOTE]
> [= İşleci](../../../visual-basic/language-reference/operators/assignment-operator.md) atama işleci olarak da kullanılır.

 `Is` işleci, `IsNot` işleci ve `Like` işleci, önceki tablodaki işleçlerden farklı olan özel karşılaştırma işlevlerine sahiptir.

## <a name="comparing-numbers"></a>Sayıları karşılaştırma
 `Single` türündeki bir ifadeyi `Double`türünden birine karşılaştırdığınızda, `Single` ifadesi `Double`'ye dönüştürülür. Bu davranış, Visual Basic 6 ' da bulunan davranışın tersidir.

 Benzer şekilde, `Decimal` bir ifadesini `Single` veya `Double`türünde bir ifadeyle karşılaştırdığınızda `Decimal` ifadesi `Single` veya `Double`olarak dönüştürülür. `Decimal` ifadelerde, 1E-28 ' den küçük olan herhangi bir kesirli değer kaybolmuş olabilir. Bu tür kesirli değer kaybı, iki değerin, olmadıkları zaman eşit olarak karşılaştırılmasını sağlayabilir. Bu nedenle, iki kayan nokta değişkenini karşılaştırmak için eşitlik (`=`) kullanırken dikkatli olmanız gerekir. İki sayı arasındaki farkın mutlak değerinin, kabul edilebilir küçük bir toleranstan daha az olup olmadığını test etmek daha güvenlidir.

### <a name="floating-point-imprecision"></a>Kayan nokta noktasında kesinlik eksikliği
 Kayan noktalı sayılarla çalışırken her zaman bellekte kesin bir gösterimine sahip olmadıkları göz önünde bulundurun. Bu, değer karşılaştırması ve [Mod işleci](../../../visual-basic/language-reference/operators/mod-operator.md)gibi belirli işlemlerden beklenmedik sonuçlara neden olabilir. Daha fazla bilgi için bkz. [sorun giderme veri türleri](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md).

## <a name="comparing-strings"></a>Dizeleri Karşılaştırma
 Dizeleri karşılaştırdığınızda, dize ifadeleri alfabetik sıralama sıralamasına göre değerlendirilir ve bu, `Option Compare` ayarına bağlıdır.

 `Option Compare Binary`, karakterlerin iç ikili gösterimlerine göre türetilmiş bir sıralama düzeninde dize karşılaştırmaları dayandırır. Sıralama düzeni kod sayfası tarafından belirlenir. Aşağıdaki örnek tipik bir ikili sıralama düzeni gösterir.

 `A < B < E < Z < a < b < e < z < À < Ê < Ø < à < ê < ø`

 `Option Compare Text`, uygulamanızın yerel ayarı tarafından belirlenen büyük/küçük harf duyarsız, metinsel sıralama düzeninde dize karşılaştırmaları dayandırır. `Option Compare Text` ayarlayıp önceki örnekteki karakterleri sıraladığınızda aşağıdaki metin sıralama düzeni geçerlidir:

 `(A=a) < (À= à) < (B=b) < (E=e) < (Ê= ê) < (Ø = ø) < (Z=z)`

### <a name="locale-dependence"></a>Yerel ayar bağımlılığını
 `Option Compare Text`ayarladığınızda, bir dize karşılaştırmasının sonucu uygulamanın çalıştığı yerel ayara bağlı olabilir. İki karakter, bir yerel ayarda eşit olarak karşılaştırılabilir ancak başka bir şekilde karşılaştırılabilir. Oturum açma denemesinin kabul edilip edilmeyeceğini kabul etmeksizin, önemli kararlar almak için bir dize karşılaştırması kullanıyorsanız, yerel ayar duyarlılığı için uyarı almanız gerekir. Yerel ayarı hesaba alan `Option Compare Binary` veya <xref:Microsoft.VisualBasic.Strings.StrComp%2A>çağırmayı düşünün.

## <a name="typeless-programming-with-relational-comparison-operators"></a>Ilişkisel karşılaştırma Işleçleri ile Türsüz programlama
 `Option Strict On`altında `Object` ifadelerle ilişkisel karşılaştırma işleçleri kullanımına izin verilmez. `Option Strict` `Off`ve `expression1` ya da `expression2` bir `Object` ifadesi olduğunda, çalışma zamanı türleri nasıl karşılaştırılacağını belirlenir. Aşağıdaki tabloda, işlenenlerinin çalışma zamanı türüne bağlı olarak ifadelerin karşılaştırılacağı ve Karşılaştırmanın sonucu gösterilmektedir.

|İşlenenler|Karşılaştırma|
|---------------------|-------------------|
|Her iki `String`|Dize sıralama özelliklerine göre karşılaştırmayı sıralayın.|
|Her iki sayısal|`Double`, sayısal karşılaştırmaya dönüştürülen nesneler.|
|Bir sayısal ve bir `String`|`String` bir `Double` dönüştürülür ve sayısal karşılaştırma gerçekleştirilir. `String` `Double`olarak dönüştürülemiyorsa bir <xref:System.InvalidCastException> oluşturulur.|
|Ya da her ikisi de `String` dışındaki başvuru türleridir|Bir <xref:System.InvalidCastException> oluşturulur.|

 Sayısal karşılaştırmalar `Nothing` 0 olarak değerlendirir. Dize karşılaştırmaları `Nothing` `""` (boş bir dize) olarak değerlendirir.

## <a name="overloading"></a>Aşırı Yükleme
 İlişkisel karşılaştırma işleçleri (`<`. `<=`, `>`, `>=`, `=`, `<>`) *aşırı yüklenmiş*olabilir, bu da bir işlenen bu sınıf veya yapının türüne sahip olduğunda bir sınıf veya yapının davranışlarını yeniden tanımlayabileceği anlamına gelir. Kodunuz böyle bir sınıf veya yapıda bu işleçlerden herhangi birini kullanıyorsa, yeniden tanımlanan davranışı anladığınızdan emin olun. Daha fazla bilgi için bkz. [operatör yordamları](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).

 [= İşlecinin](../../../visual-basic/language-reference/operators/assignment-operator.md) , atama işleci olarak değil, yalnızca ilişkisel karşılaştırma operatörü olarak aşırı yüklenebilir olduğuna dikkat edin.

## <a name="example"></a>Örnek
 Aşağıdaki örnek, ifadeleri karşılaştırmak için kullandığınız, ilişkisel karşılaştırma işleçlerinin çeşitli kullanımlarını gösterir. İlişkisel karşılaştırma işleçleri, belirtilen ifadenin `True`olarak değerlendirilip değerlendirilmediğini temsil eden `Boolean` bir sonuç döndürür. Dizelere `>` ve `<` işleçlerini uyguladığınızda, karşılaştırma, dizelerin normal alfabetik sıralama düzeni kullanılarak yapılır. Bu sipariş, yerel ayara bağlı olabilir. Sıralamanın büyük/küçük harfe duyarlı olup olmadığı veya [Seçenek karşılaştırma](../../../visual-basic/language-reference/statements/option-compare-statement.md) ayarına bağlı olup olmadığı.

 [!code-vb[VbVbalrOperators#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#1)]

 Yukarıdaki örnekte, ilk karşılaştırma `False` döndürür ve kalan karşılaştırmalar `True`döndürür.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.InvalidCastException>
- [= İşleci](../../../visual-basic/language-reference/operators/assignment-operator.md)
- [Visual Basic operatör önceliği](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [İşlevselliğe Göre Listelenmiş İşleçler](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [Veri Türü Sorunlarını Giderme](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)
- [Visual Basic karşılaştırma Işleçleri](../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)
