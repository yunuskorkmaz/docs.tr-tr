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
ms.openlocfilehash: c5b26bd1d3ebae5136718833c124e3c6e575e9b7
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/01/2018
ms.locfileid: "43452709"
---
# <a name="like-operator-visual-basic"></a>Like İşleci (Visual Basic)
Bir dizeyi bir desene göre karşılaştırır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
result = string Like pattern  
```  
  
## <a name="parts"></a>Bölümler  
 `result`  
 Gerekli. Tüm `Boolean` değişkeni. Sonuç bir `Boolean` belirten değer olup olmadığını `string` karşılayan `pattern`.  
  
 `string`  
 Gerekli. Tüm `String` ifade.  
  
 `pattern`  
 Gerekli. Tüm `String` ifade "Açıklamalar" içinde tanımlanan desen eşleştirme kuralları uyumludur  
  
## <a name="remarks"></a>Açıklamalar  
 Varsa değerini `string` bulunan deseni karşılayan `pattern`, `result` olduğu `True`. Dizeyi bir desen karşılamaz, `result` olduğu `False`. Her iki `string` ve `pattern` boş dizeleri olan sonuç `True`.  
  
## <a name="comparison-method"></a>Karşılaştırma yöntemi  
 Davranışını `Like` işleci bağlıdır [seçenek karşılaştırma ifadesini](../../../visual-basic/language-reference/statements/option-compare-statement.md). Her kaynak dosyası için varsayılan dize karşılaştırma yöntemi: `Option Compare Binary`.  
  
## <a name="pattern-options"></a>Düzen Seçenekleri  
 Yerleşik bir desenle eşleşen dize karşılaştırmaları için çok yönlü bir araç sağlar. Desen eşleştirme özellikleri, her bir karakterle Eşleştir imkan tanır `string` belirli bir karakter, bir joker karakter, karakter listesini ya da bir karakter aralığı. Aşağıdaki tablo, izin verilen karakter gösterir `pattern` ve bunların eşleşmesi.  
  
|Karakter `pattern`|Eşleştirme `string`|  
|-----------------------------|-------------------------|  
|`?`|Herhangi bir tek karakter|  
|`*`|Sıfır veya daha fazla karakter|  
|`#`|Herhangi bir tek basamak (0 – 9)|  
|`[charlist]`|Herhangi bir tek karakterle `charlist`|  
|`[!charlist]`|Herhangi bir tek karakterle içinde değil `charlist`|  
  
## <a name="character-lists"></a>Karakter listeler  
 Bir veya daha fazla karakter grubu (`charlist`) parantezleri içine alınan (`[ ]`) herhangi bir tek karakterle eşleştirmek için kullanılan `string` basamak dahil olmak üzere neredeyse her karakter kodu içerebilir.  
  
 Ünlem işareti (`!`) başında `charlist` karakterler dışında herhangi bir karakterin varsa bir eşleşme yapılan anlamına gelir `charlist` bulunur `string`. Köşeli ayraç içine kullanıldığında, ünlem kendisi ile eşleşir.  
  
## <a name="special-characters"></a>Özel Karakterler  
 Özel karakterleri sol köşeli ayraç eşleştirmek için (`[`), soru işareti (`?`), numara işareti (`#`) ve yıldız işareti (`*`), bunları köşeli ayraç içine alın. Sağ köşeli ayraç (`]`) içindeki bir grubun kendisi eşleştirmek için kullanılamaz ancak tek bir karakter olarak bir grubun dışına kullanılabilir.  
  
 Karakter dizisi `[]` sıfır uzunlukta bir dize olarak kabul edilir (`""`). Ancak, ayraç içine bir karakter listesinin bir parçası olamaz. Bir konumda olup olmadığını denetlemek istiyorsanız `string` birini içeren karakter veya hiçbir karakter grubu kullandığınız `Like` iki kez. Bir örnek için bkz. [nasıl yapılır: bir dizeyi belirli bir desene göre eşleştirme](../../../visual-basic/programming-guide/language-features/operators-and-expressions/how-to-match-a-string-against-a-pattern.md).  
  
## <a name="character-ranges"></a>Karakter aralığı  
 Kullanarak bir tire (`–`) alt ve üst sınırları aralığını ayırmak için `charlist` da karakter aralığını belirtebilirsiniz. Örneğin, `[A–Z]` karaktere karşılık gelen yerleştirin, sonuçları bir eşleşme `string` aralığındaki herhangi bir karakter içeren `A`–`Z`, ve `[!H–L]` karaktere karşılık gelen konum, içinde bir eşleşme sonuçları izin verilen aralığın dışında herhangi bir karakter içeren `H`–`L`.  
  
 Karakter aralığı belirttiğinizde, en düşükten en yükseğe yüksek için sıralama düzeni, diğer bir deyişle, artan sırada görünmelidir. Bu nedenle, `[A–Z]` geçerli bir düzen olduğunu ancak `[Z–A]` değil.  
  
### <a name="multiple-character-ranges"></a>Birden çok karakter aralıkları  
 Aynı karakterin konumu için birden çok aralık belirtmek için sınırlayıcılar aynı ayraçlar içine yerleştirin. Örneğin, `[A–CX–Z]` karaktere karşılık gelen yerleştirin, sonuçları bir eşleşme `string` ya da aralıktaki herhangi bir karakter içeren `A`–`C` veya aralığını `X`–`Z`.  
  
### <a name="usage-of-the-hyphen"></a>Kısa çizgi kullanımı  
 Bir tire (`–`) (sonra bir ünlem işareti varsa) başında veya sonunda görünebilir `charlist` kendisini eşleştirilecek. Herhangi diğer konumda kısa çizgi, kısa çizgi her iki tarafındaki karakterleri tarafından ayrılmış karakter aralığı tanımlar.  
  
## <a name="collating-sequence"></a>Harmanlama sırası  
 Belirtilen bir aralıktaki anlamını tarafından belirlenen şekilde çalışma zamanında sıralama karakter bağlıdır `Option Compare` ve sistemin yerel ayarı kodu çalışıyor. İle `Option Compare Binary`, aralığın `[A–E]` eşleşen `A`, `B`, `C`, `D`, ve `E`. İle `Option Compare Text`, `[A–E]` eşleşen `A`, `a`, `À`, `à`, `B`, `b`, `C`, `c`, `D`, `d`, `E`, ve `e`. Aralığın eşleşmiyor `Ê` veya `ê` sıralama düzeninde vurgulanmamış karakterden sonra vurgulu karakterlerin collate olduğundan.  
  
## <a name="digraph-characters"></a>Digraph karakter  
 Bazı dillerde, iki ayrı karakterleri temsil alfabetik karakterler vardır. Örneğin, çeşitli diller karakter kullanın `æ` karakterleri temsil etmek için `a` ve `e` birlikte görüntülendiğinde. `Like` İşleci tek digraph karakter ve karakterlerin tek tek iki eşdeğer olduğunu algılar.  
  
 Sistem yerel ayarları digraph karakter kullanan bir dil belirtildiğinde, bir olayın ya da tek digraph karakterinin `pattern` veya `string` diğer dizede eşdeğer iki karakter dizisiyle eşleşir. Benzer şekilde, bir digraph karakter `pattern` parantezleri içine alınan (tek başına bir liste veya bir aralıktaki) eşdeğer iki karakter dizisi ile eşleşen `string`.  
  
## <a name="overloading"></a>Aşırı Yükleme  
 `Like` İşleci olabilir *aşırı*, işleneni, sınıf veya yapı türüne sahip olduğunda bir sınıf veya yapı davranışını tanımlayabilirsiniz, anlamına gelir. Kodunuz bu tür bir sınıf veya yapı üzerinde bu işleç kullanıyorsa, yeniden tanımlanan davranışını anladığınızdan emin olun. Daha fazla bilgi için [işleç yordamları](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Örnek  
 Bu örnekte `Like` çeşitli desenleri için dizeleri karşılaştırmak için işleci. Tarihinden itibaren bu sonuçları bir `Boolean` her dize deseni karşılayıp karşılamadığını belirten değişkeni.  
  
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
