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
ms.openlocfilehash: 9014cac5e2f3933b27411dfe5681fc16f4cdde30
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62013588"
---
# <a name="comparison-operators-visual-basic"></a>Karşılaştırma İşleçleri (Visual Basic)
Visual Basic içinde tanımlanan Karşılaştırma işleçleri şunlardır:  
  
 `<` İşleci  
  
 `<=` İşleci  
  
 `>` İşleci  
  
 `>=` İşleci  
  
 `=` İşleci  
  
 `<>` İşleci  
  
 [Is İşleci](../../../visual-basic/language-reference/operators/is-operator.md)  
  
 [IsNot İşleci](../../../visual-basic/language-reference/operators/isnot-operator.md)  
  
 [Like İşleci](../../../visual-basic/language-reference/operators/like-operator.md)  
  
 Bu işleçler, eşit oldukları ve aksi durumda, bunlar farklılıklar olup olmadığını belirlemek için iki deyim karşılaştırın. `Is`, `IsNot`, ve `Like` ayrı Yardım sayfalarında ayrıntılı olarak ele alınmıştır. İlişkisel Karşılaştırma işleçleri, bu sayfada ayrıntılı olarak ele alınmıştır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
      result = expression1 comparisonoperator expression2  
result = object1 [Is | IsNot] object2  
result = string Like pattern  
```  
  
## <a name="parts"></a>Bölümler  
 `result`  
 Gerekli. A `Boolean` Karşılaştırmanın sonucu temsil eden değer.  
  
 `expression`  
 Gerekli. Herhangi bir ifade.  
  
 `comparisonoperator`  
 Gerekli. Herhangi bir ilişkisel karşılaştırma işleci.  
  
 `object1`, `object2`  
 Gerekli. Tüm başvuru nesne adları.  
  
 `string`  
 Gerekli. Tüm `String` ifade.  
  
 `pattern`  
 Gerekli. Tüm `String` ifadesi veya karakter aralığı.  
  
## <a name="remarks"></a>Açıklamalar  
 Aşağıdaki tabloda ilişkisel Karşılaştırma işleçleri ve belirleyen koşulları listesini içeren olmadığını `result` olduğu `True` veya `False`.  
  
|İşleç|`True` Eğer|`False` Eğer|  
|--------------|---------------|----------------|  
|`<` (Küçüktür)|`expression1` < `expression2`|`expression1` >= `expression2`|  
|`<=` (Küçüktür veya eşittir)|`expression1` <= `expression2`|`expression1` > `expression2`|  
|`>` (Büyüktür)|`expression1` > `expression2`|`expression1` <= `expression2`|  
|`>=` (Büyüktür veya eşittir)|`expression1` >= `expression2`|`expression1` < `expression2`|  
|`=` (Eşittir)|`expression1` = `expression2`|`expression1` <> `expression2`|  
|`<>` (Eşit değildir)|`expression1` <> `expression2`|`expression1` = `expression2`|  
  
> [!NOTE]
>  [= İşleci](../../../visual-basic/language-reference/operators/assignment-operator.md) bir atama işleci da kullanılır.  
  
 `Is` İşleci `IsNot` işleci ve `Like` operatörü sahip işleçler yukarıdaki tabloda, farklı belirli karşılaştırma işlevleri.  
  
## <a name="comparing-numbers"></a>Sayı karşılaştırma  
 Türündeki bir ifade karşılaştığınızda `Single` türü birine `Double`, `Single` ifade dönüştürülür `Double`. Bu davranış, Visual Basic 6'da bulunan ters yönde, davranıştır.  
  
 Benzer şekilde, bir ifade türü karşılaştığınızda `Decimal` türündeki bir ifadeye `Single` veya `Double`, `Decimal` ifade dönüştürülür `Single` veya `Double`. İçin `Decimal` ifadeleri herhangi bir kesirli değer 1E-28 kesilmiş olabilir. Böyle bir kesirli değer kaybı olmadıkları zaman eşit karşılaştırmak iki değeri neden olabilir. Bu nedenle, eşitlik kullanırken dikkatli (`=`) iki kayan nokta değişkeni karşılaştırmak için. İki sayı arasındaki farkı mutlak değerini küçük kabul edilebilir tolerans'dan küçük olup olmadığını test etmek daha güvenlidir.  
  
### <a name="floating-point-imprecision"></a>Kayan nokta kesinlik eksikliği  
 Kayan noktalı sayı ile çalıştığınızda, bunlar her zaman kesin bir gösterimi bellekte olmadığını aklınızda bulundurun. Değer karşılaştırması gibi bazı işlemleri öğesinden bu beklenmeyen sonuçlara neden olabilir ve [Mod işleci](../../../visual-basic/language-reference/operators/mod-operator.md). Daha fazla bilgi için [veri türleri sorunlarını giderme](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md).  
  
## <a name="comparing-strings"></a>Dizeleri Karşılaştırma  
 Dizeleri karşılaştırırken dize ifadeleri bağlıdır alfabetik sıralama düzenlerine göre değerlendirilir `Option Compare` ayarı.  
  
 `Option Compare Binary` tabanları karakterlerin dahili ikili gösterimi türetilmiş bir sıralama düzeni üzerindeki dize. Sıralama düzenini kod sayfası tarafından belirlenir. Aşağıdaki örnek, tipik ikili sıralama düzeninde gösterir.  
  
 `A < B < E < Z < a < b < e < z < À < Ê < Ø < à < ê < ø`  
  
 `Option Compare Text` tabanları, uygulamanızın yerel ayarı tarafından belirlenen büyük küçük harf duyarsız, metin sıralama düzeni üzerindeki dize. Ayarladığınızda `Option Compare Text` ve önceki örnekte karakterleri sıralamak için aşağıdaki metin sıralama düzeni uygular:  
  
 `(A=a) < (À= à) < (B=b) < (E=e) < (Ê= ê) < (Ø = ø) < (Z=z)`  
  
### <a name="locale-dependence"></a>Yerel ayar bağımlılığı  
 Ayarladığınızda `Option Compare Text`, bir dize karşılaştırmasının sonucunu uygulamasının çalıştığı yerel ayarına göre değişebilir. İki karakteri, eşittir, ancak, başka bir yerel ayardaki karşılaştırın. Oturum girişimi kabul edilip edilmeyeceğini gibi önemli kararları yapmak için bir dize karşılaştırmasının kullanıyorsanız, yerel ayar duyarlılık uyarı olmalıdır. Her iki ayarlamayı düşünün `Option Compare Binary` veya çağıran <xref:Microsoft.VisualBasic.Strings.StrComp%2A>, hesaba yerel alır.  
  
## <a name="typeless-programming-with-relational-comparison-operators"></a>Yazısız programlama ilişkisel Karşılaştırma işleçleri  
 İlişkisel Karşılaştırma işleçleri ile kullanımını `Object` altında ifadeleri verilmez `Option Strict On`. Zaman `Option Strict` olduğu `Off`ve her iki `expression1` veya `expression2` olduğu bir `Object` ifade nasıl kıyasla çalışma zamanı türlerini belirleyin. Aşağıdaki tabloda, ifadelerin nasıl karşılaştırılır ve işlenenleri çalışma zamanı türüne bağlı olarak, karşılaştırma sonucu gösterir.  
  
|İşlenen|Karşılaştırma|  
|---------------------|-------------------|  
|Her ikisi de `String`|Karşılaştırma özelliklerini sıralama dizesine dayalı sıralayın.|  
|Her iki sayısal|Nesneleri dönüştürülen `Double`, sayısal karşılaştırma.|  
|Bir sayısal ve bir `String`|`String` Dönüştürülür bir `Double` ve sayısal karşılaştırma gerçekleştirilir. Varsa `String` dönüştürülemez `Double`e <xref:System.InvalidCastException> oluşturulur.|  
|Veya ikisini birden fazla başvuru türleri olan `String`|Bir <xref:System.InvalidCastException> oluşturulur.|  
  
 Sayısal karşılaştırma kabul `Nothing` 0 olarak. Dize karşılaştırmaları kabul `Nothing` olarak `""` (boş bir dize).  
  
## <a name="overloading"></a>Aşırı Yükleme  
 İlişkisel Karşılaştırma işleçleri (`<`. `<=``>`, `>=`, `=`, `<>`) olabilir *aşırı*, işleneni, sınıf veya yapı türüne sahip olduğunda bir sınıf veya yapı davranışlarını tanımlayabilirsiniz, anlamına gelir. Bu tür bir sınıf veya yapı üzerinde kodunuzu bu işleçler birini kullanıyorsa, yeniden tanımlanan davranışını anladığınızdan emin olun. Daha fazla bilgi için [işleç yordamları](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
 Dikkat [= işleci](../../../visual-basic/language-reference/operators/assignment-operator.md) aşırı yüklenmiş olabilir yalnızca ilişkisel karşılaştırma işleci olarak, bir atama işleci olarak değil.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, çeşitli kullanımları ifadeleri karşılaştırmak için kullanılan ilişkisel karşılaştırma işleçlerini gösterir. İlişkisel Karşılaştırma işleçleri dönüş bir `Boolean` belirtilen ifadenin değerlendirdiği olup olmadığını gösteren bir sonuç `True`. Uyguladığınızda `>` ve `<` işleçleri için dizeleri Karşılaştırma yapıldığında dizelerin normal alfabetik sıralama düzenini kullanarak. Bu sırada, yerel ayara bağlı olabilir. Sıralama büyük küçük harfe duyarlı olup olmamasına bağlıdır [Option Compare](../../../visual-basic/language-reference/statements/option-compare-statement.md) ayarı.  
  
 [!code-vb[VbVbalrOperators#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#1)]  
  
 Önceki örnekte, ilk karşılaştırma döndürür `False` ve kalan karşılaştırmalar dönüş `True`.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.InvalidCastException>
- [= İşleci](../../../visual-basic/language-reference/operators/assignment-operator.md)
- [Visual Basic'de İşleç önceliği](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [İşlevselliğe Göre Listelenmiş İşleçler](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [Veri Türü Sorunlarını Giderme](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)
- [Visual Basic'de Karşılaştırma işleçleri](../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)
