---
title: Like İşleci (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- Like
- vb.Like
helpviewer_keywords:
- similar to
- pattern matching
- Like operator [Visual Basic]
- '? symbol, wildcard character'
- string comparison [Visual Basic], Like operator
- strings [Visual Basic], comparing
- comparison operators [Visual Basic]
- symbols, wildcard
- wildcards, Like operator
- strings [Visual Basic], matching
- string comparison [Visual Basic], sorting data
- data [Visual Basic], sorting
- text [Visual Basic], comparing
- operators [Visual Basic], pattern-matching
- data [Visual Basic], string comparisons
- string comparison [Visual Basic], Like operators
ms.assetid: 966283ec-80e2-4294-baa8-c75baff804f9
ms.openlocfilehash: a9c672a397510c69c9ee67358689feff80d8831a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="like-operator-visual-basic"></a>Like İşleci (Visual Basic)
Bir dizeyi belirli bir desene göre karşılaştırır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
result = string Like pattern  
```  
  
## <a name="parts"></a>Bölümler  
 `result`  
 Gerekli. Tüm `Boolean` değişkeni. Sonuç bir `Boolean` belirten değer desteklemediğini `string` karşılayan `pattern`.  
  
 `string`  
 Gerekli. Tüm `String` ifade.  
  
 `pattern`  
 Gerekli. Tüm `String` "Açıklamalar" açıklanan desen eşleştirme kurallarına uyan ifade  
  
## <a name="remarks"></a>Açıklamalar  
 Varsa değeri `string` içinde yer alan düzeni karşılayan `pattern`, `result` olan `True`. Dize desenini karşılamadığı varsa `result` olan `False`. Her iki `string` ve `pattern` boş dizeler şunlardır: sonuç `True`.  
  
## <a name="comparison-method"></a>Karşılaştırma yöntemi  
 Davranışını `Like` işleci bağımlı [Option Compare deyimi](../../../visual-basic/language-reference/statements/option-compare-statement.md). Her kaynak dosya için varsayılan dize karşılaştırma yöntemi `Option Compare Binary`.  
  
## <a name="pattern-options"></a>Desen seçenekleri  
 Yerleşik desen eşleştirme dize karşılaştırmaları için çok yönlü bir araç sağlar. Desen eşleştirme özellikleri her karakteri eşleştirmek izin `string` karşı belirli bir karakter, bir joker karakter, karakter listesini veya bir karakter aralığı. Aşağıdaki tabloda, izin verilen karakter gösterilmektedir `pattern` ve bunların eşleşmesi.  
  
|Karakter `pattern`|İçinde eşleşir `string`|  
|-----------------------------|-------------------------|  
|`?`|Herhangi bir tek karakteri|  
|`*`|Sıfır veya daha fazla karakter|  
|`#`|Tek bir rakam (0-9)|  
|`[charlist]`|Herhangi bir tek karakteri `charlist`|  
|`[!charlist]`|Herhangi bir tek karakteri değil `charlist`|  
  
## <a name="character-lists"></a>Karakter listeler  
 Bir veya daha fazla karakter grubu (`charlist`) ayraç (`[ ]`) herhangi bir tek karakteri eşleştirmek için kullanılan `string` ve basamak dahil olmak üzere, neredeyse her bir karakter kodu içerebilir.  
  
 Ünlem işareti (`!`) başındaki `charlist` karakterleri dışında herhangi bir karakterin varsa bir eşleşme yapılan anlamına gelir `charlist` içinde bulunan `string`. Köşeli ayraç içine kullanıldığında, ünlem kendisi ile eşleşir.  
  
## <a name="special-characters"></a>Özel Karakterler  
 Özel karakterler sol ayraç eşleşecek şekilde (`[`), soru işareti (`?`), numara işareti (`#`) ve yıldız işareti (`*`), köşeli ayraç içine alın. Sağ köşeli ayraç (`]`) içindeki bir grubun kendisi eşleşecek şekilde kullanılamaz ancak tek bir karakter olarak bir grubun dışında kullanılabilir.  
  
 Karakter dizisi `[]` sıfır uzunlukta bir dize olarak kabul edilir (`""`). Ancak, ayraç karakter listesinin bir parçası olamaz. Bir konumda olup olmadığını denetlemek istiyorsanız `string` birini içeren bir Grubu'nun karakterleri veya hiç bir karakter, kullandığınız `Like` iki kez. Bir örnek için bkz: [nasıl yapılır: bir dizeyi belirli bir desene göre eşleştirme](../../../visual-basic/programming-guide/language-features/operators-and-expressions/how-to-match-a-string-against-a-pattern.md).  
  
## <a name="character-ranges"></a>Karakter aralıkları  
 Bir tire kullanarak (`–`) alt ve üst sınır, ayırmak için `charlist` karakter aralığı belirtebilirsiniz. Örneğin, `[A–Z]` karşılık gelen karakter yerleştirin varsa bir eşleşme sonuçları `string` aralık içinde herhangi bir karakter içeriyor `A`–`Z`, ve `[!H–L]` karşılık gelen karakter konumunu varsa bir eşleşme sonuçları izin verilen aralığın dışında herhangi bir karakter içeriyor `H`–`L`.  
  
 Karakter aralığı belirttiğinizde, diğer bir deyişle, en yüksek düzeye düşükten artan sıralama görünmelidir. Bu nedenle, `[A–Z]` geçerli bir düzen ancak `[Z–A]` değil.  
  
### <a name="multiple-character-ranges"></a>Birden çok karakter aralığı  
 Aynı karakterin için birden çok aralık belirtmek için bunları sınırlayıcıları olmadan aynı parantez içine yerleştirin. Örneğin, `[A–CX–Z]` karşılık gelen karakter yerleştirin varsa bir eşleşme sonuçları `string` ya da aralık içinde herhangi bir karakter içeriyor `A`–`C` veya aralık `X`–`Z`.  
  
### <a name="usage-of-the-hyphen"></a>Tire kullanımı  
 Bir tire (`–`) (sonra bir ünlem işareti varsa) başında veya sonunda görünebilir `charlist` kendisini eşlemek üzere. Diğer herhangi bir yere içinde tire tire her iki tarafında karaktere göre ayrılmış karakter aralığı tanımlar.  
  
## <a name="collating-sequence"></a>Harmanlama sırası  
 Belirli bir aralık anlamını tarafından belirlendiği şekilde, çalışma zamanında sıralama karakter bağlıdır `Option``Compare` ve sistem yerel ayarı kodu çalıştırma. İle `Option``Compare``Binary`, aralığın `[A–E]` eşleşen `A`, `B`, `C`, `D`, ve `E`. İle `Option``Compare``Text`, `[A–E]` eşleşen `A`, `a`, `À`, `à`, `B`, `b`, `C`, `c`, `D`, `d`, `E`, ve `e`. Aralığın eşleşmiyor `Ê` veya `ê` sıralama düzeni olarak karakter sonra vurgulu karakterlerin collate olduğundan.  
  
## <a name="digraph-characters"></a>Digraph karakterleri  
 Bazı dillerde, iki ayrı karakteri temsil alfabetik karakterler vardır. Örneğin, çeşitli diller karakterini kullanın `æ` karakterleri temsil etmek için `a` ve `e` birlikte görüntülendiğinde. `Like` İşleci tanıdığı tek digraph karakter ve iki ayrı karakter eşdeğer.  
  
 Bir digraph karakter kullanan bir dil ayarlarına yerel ayar belirtildiğinde, bir oluşumu ya da tek digraph karakterinin `pattern` veya `string` eşdeğer bir dize iki karakter dizisi eşleşir. Benzer şekilde, bir digraph karakter `pattern` ayraç (tek başına, liste veya aralık) eşdeğer iki karakter dizisi eşleşen `string`.  
  
## <a name="overloading"></a>Aşırı Yükleme  
 `Like` İşleci olabilir *aşırı*, işleneni, sınıf veya yapı türüne sahip olduğunda bir sınıf veya yapı davranışını tanımlayabilirsiniz, anlamına gelir. Bu tür bir sınıf veya yapı üzerinde kodunuzu bu işleç kullanıyorsa, yeniden tanımlanan davranışını anladığınızdan emin olun. Daha fazla bilgi için bkz: [işleç yordamları](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Örnek  
 Bu örnekte `Like` çeşitli desenlerini dizeleri karşılaştırmak için işleci. Sonuçları yerleştirilmesini bir `Boolean` her dize desenini karşılayıp karşılamadığını belirten değişkeni.  
  
 [!code-vb[VbVbalrOperators#30](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/like-operator_1.vb)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:Microsoft.VisualBasic.Strings.InStr%2A>  
 <xref:Microsoft.VisualBasic.Strings.StrComp%2A>  
 [Karşılaştırma İşleçleri](../../../visual-basic/language-reference/operators/comparison-operators.md)  
 [Visual Basic'de İşleç önceliği](../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [İşlevselliğe Göre Listelenmiş İşleçler](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)  
 [Option Compare Deyimi](../../../visual-basic/language-reference/statements/option-compare-statement.md)  
 [İşleçler ve İfadeler](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)  
 [Nasıl yapılır: Bir Dizeyi Belirli Bir Desene Göre Eşleştirme](../../../visual-basic/programming-guide/language-features/operators-and-expressions/how-to-match-a-string-against-a-pattern.md)
