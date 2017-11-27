---
title: "Karşılaştırma İşleçleri (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
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
- comparison operators [Visual Basic], Visual Basicl
ms.assetid: d6cb12a8-e52e-46a7-8aaf-f804d634a825
caps.latest.revision: "20"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: aa450f7978f46196663c7534b31597b04d80482a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="comparison-operators-visual-basic"></a>Karşılaştırma İşleçleri (Visual Basic)
Visual Basic'te tanımlanan Karşılaştırma işleçleri verilmiştir.  
  
 `<`işleci  
  
 `<=`işleci  
  
 `>`işleci  
  
 `>=`işleci  
  
 `=`işleci  
  
 `<>`işleci  
  
 [Is işleci](../../../visual-basic/language-reference/operators/is-operator.md)  
  
 [IsNot işleci](../../../visual-basic/language-reference/operators/isnot-operator.md)  
  
 [Like işleci](../../../visual-basic/language-reference/operators/like-operator.md)  
  
 Bu işleçlere eşit değilse, bunların nasıl farklı olup olmadığını belirlemek için iki ifadeye karşılaştırın. `Is`, `IsNot`, ve `Like` ayrı Yardım sayfalarına ayrıntılı olarak ele alınmıştır. İlişkisel Karşılaştırma işleçleri bu sayfada ayrıntılı olarak ele alınmıştır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
      result = expression1 comparisonoperator expression2  
result = object1 [Is | IsNot] object2  
result = string Like pattern  
```  
  
## <a name="parts"></a>Bölümler  
 `result`  
 Gerekli. A `Boolean` karşılaştırma sonucunu temsil eden değer.  
  
 `expression`  
 Gerekli. Herhangi bir ifade.  
  
 `comparisonoperator`  
 Gerekli. Herhangi bir ilişkisel karşılaştırma işleci.  
  
 `object1`, `object2`  
 Gerekli. Herhangi bir nesne adlarını başvuru.  
  
 `string`  
 Gerekli. Tüm `String` ifade.  
  
 `pattern`  
 Gerekli. Tüm `String` ifadesi veya karakter aralığı.  
  
## <a name="remarks"></a>Açıklamalar  
 Aşağıdaki tabloda ilişkisel Karşılaştırma işleçleri ve belirleyen koşulları listesini içeren olup olmadığını `result` olan `True` veya `False`.  
  
|İşleç|`True`Eğer|`False`Eğer|  
|--------------|---------------|----------------|  
|`<`(Küçüktür)|`expression1` < `expression2`|`expression1` >= `expression2`|  
|`<=`(Küçük veya eşittir)|`expression1` <= `expression2`|`expression1` > `expression2`|  
|`>`(Büyük)|`expression1` > `expression2`|`expression1` <= `expression2`|  
|`>=`(Büyük veya eşittir)|`expression1` >= `expression2`|`expression1` < `expression2`|  
|`=`(Eşit)|`expression1` = `expression2`|`expression1` <> `expression2`|  
|`<>`(Eşit değildir)|`expression1` <> `expression2`|`expression1` = `expression2`|  
  
> [!NOTE]
>  [= İşleci](../../../visual-basic/language-reference/operators/assignment-operator.md) atama işleci da kullanılır.  
  
 `Is` İşleci, `IsNot` işleci ve `Like` işleci işleçleri önceki tabloda farklı belirli karşılaştırma işlevler sahip.  
  
## <a name="comparing-numbers"></a>Sayı karşılaştırma  
 Türünde bir ifadenin karşılaştırmak zaman `Single` türü birine `Double`, `Single` ifade için dönüştürülür `Double`. Bu Visual Basic 6'bulunan davranışı ters yönde bir davranıştır.  
  
 Benzer şekilde, ne zaman, karşılaştırma türü bir ifadenin `Decimal` türünde bir ifadenin için `Single` veya `Double`, `Decimal` ifade için dönüştürülür `Single` veya `Double`. İçin `Decimal` ifadeleri, herhangi bir kesir değerini 1E-28 kaybolabilir. Böyle bir kesir değerini kaybı olmadıkları zaman eşit karşılaştırmak iki değer neden olabilir. Bu nedenle, eşitlik kullanırken dikkatli (`=`) iki kayan nokta değişkenleri karşılaştırmak için. İki sayı arasındaki farkı mutlak değerini küçük kabul edilebilir tolerans değerinden olup olmadığını sınamak daha güvenlidir.  
  
### <a name="floating-point-imprecision"></a>Kayan nokta Imprecision  
 Kayan nokta sayıları ile çalışırken, her zaman kesin gösterimi bellekte olmadığı olduğunu aklınızda bulundurun. Değer karşılaştırması gibi bazı işlemleri alanından bu beklenmeyen sonuçlara neden ve [Mod işleci](../../../visual-basic/language-reference/operators/mod-operator.md). Daha fazla bilgi için bkz: [veri türleri sorunlarını giderme](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md).  
  
## <a name="comparing-strings"></a>Dizeleri Karşılaştırma  
 Dizeleri karşılaştırmak, dize ifadeler bağlıdır alfabetik sıralama düzenlerine göre değerlendirilir `Option Compare` ayarı.  
  
 `Option Compare Binary`tabanları iç ikili gösterimlerini karakterleri türetilmiş bir sıralama düzeni üzerinde karşılaştırmalarına dize. Sıralama düzenini kod sayfası tarafından belirlenir. Aşağıdaki örnek, tipik bir ikili sıralama gösterir.  
  
 `A < B < E < Z < a < b < e < z < À < Ê < Ø < à < ê < ø`  
  
 `Option Compare Text`tabanları uygulamanızın bölgeye göre belirlenir büyük küçük harf duyarsız, metinsel sıralama düzeni üzerinde karşılaştırmalarına dize. Ayarladığınızda `Option Compare Text` ve önceki örnekte karakterleri sıralamak için aşağıdaki metni sıralama düzeni uygular:  
  
 `(A=a) < (À= à) < (B=b) < (E=e) < (Ê= ê) < (Ø = ø) < (Z=z)`  
  
### <a name="locale-dependence"></a>Yerel ayar bağımlılığı  
 Ayarladığınızda `Option Compare Text`, dize karşılaştırmasının sonucu uygulamanın çalıştığı yerel ayara bağlı olabilir. İki karakter, bir yerel ancak başka eşit olarak karşılaştırın. Oturum girişimi kabul edilip edilmeyeceğini gibi önemli kararları yapmak için bir dize karşılaştırma kullanıyorsanız, yerel ayar duyarlılık uyarısını olmalıdır. Her iki ayar göz önünde bulundurun `Option Compare Binary` veya arama <xref:Microsoft.VisualBasic.Strings.StrComp%2A>, hesaba yerel alır.  
  
## <a name="typeless-programming-with-relational-comparison-operators"></a>İlişkisel Karşılaştırma işleçleri ile yazısız programlama  
 İlişkisel Karşılaştırma işleçleri ile kullanımını `Object` ifadeleri altında izin verilmeyen `Option Strict On`. Zaman `Option Strict` olan `Off`ve her iki `expression1` veya `expression2` olan bir `Object` ifadesi nasıl karşılaştırılır çalışma zamanı türlerini belirleyin. Aşağıdaki tablo ifadeleri nasıl karşılaştırılır ve işlenen çalışma zamanı türüne bağlı olarak karşılaştırma sonucundan gösterir.  
  
|İşlenen olursa|Karşılaştırma|  
|---------------------|-------------------|  
|Her ikisi`String`|Özellikleri sıralama dizesine dayalı karşılaştırma sıralayın.|  
|Her iki sayısal|Nesneleri dönüştürülür `Double`, sayısal karşılaştırma.|  
|Bir sayısal ve bir`String`|`String` Dönüştürülür bir `Double` ve sayısal karşılaştırma gerçekleştirilir. Varsa `String` dönüştürülemiyor `Double`, bir <xref:System.InvalidCastException> oluşturulur.|  
|Ya da her ikisini de dışında başvuru türleri:`String`|Bir <xref:System.InvalidCastException> oluşturulur.|  
  
 Sayısal karşılaştırmaları kabul `Nothing` 0 olarak. Dize karşılaştırmaları kabul `Nothing` olarak `""` (boş bir dize).  
  
## <a name="overloading"></a>Aşırı Yükleme  
 İlişkisel Karşılaştırma işleçleri (`<`. `<=``>`, `>=`, `=`, `<>`) olabilir *aşırı*, işleneni, sınıf veya yapı türüne sahip olduğunda bir sınıf veya yapı davranışlarını tanımlayabilirsiniz, anlamına gelir. Bu tür bir sınıf veya yapı üzerinde kodunuzu bu işleçlere hiçbirini kullanıyorsa, yeniden tanımlanan davranışı anladığınızdan emin olun. Daha fazla bilgi için bkz: [işleç yordamları](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
 Dikkat [= işleci](../../../visual-basic/language-reference/operators/assignment-operator.md) aşırı yüklenmiş olabilir yalnızca bir ilişkisel karşılaştırma işleci olarak değil olarak atama işleci.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek ifadeler karşılaştırmak için kullandığınız ilişkisel Karşılaştırma işleçleri çeşitli kullanımları gösterir. İlişkisel Karşılaştırma işleçleri dönüş bir `Boolean` için belirtilen ifadeyi hesaplar olup olmadığına bakılmaksızın temsil eden sonuç `True`. Uyguladığınızda `>` ve `<` işleçleri dizeleri için Karşılaştırma yapıldığında dizelerin normal alfabetik sıralama düzenini kullanarak. Bu sırada, yerel ayara bağlı olabilir. Sıralama büyük küçük harfe duyarlı olup olmamasına bağlıdır [seçeneği karşılaştırmak](../../../visual-basic/language-reference/statements/option-compare-statement.md) ayarı.  
  
 [!code-vb[VbVbalrOperators#1](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/comparison-operators_1.vb)]  
  
 Önceki örnekte, ilk karşılaştırma döndürür `False` ve kalan karşılaştırmaları dönmek `True`.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.InvalidCastException>  
 [= İşleci](../../../visual-basic/language-reference/operators/assignment-operator.md)  
 [Visual Basic'de İşleç önceliği](../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [İşlevselliğe göre listelenmiş işleçler](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)  
 [Veri türleri sorunlarını giderme](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)  
 [Visual Basic'de Karşılaştırma işleçleri](../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)
