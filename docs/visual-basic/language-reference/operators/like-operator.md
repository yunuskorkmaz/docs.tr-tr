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
ms.openlocfilehash: 795ecc2e80d57af29ccd50c50d2dd209c6425e40
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/01/2019
ms.locfileid: "71701129"
---
# <a name="like-operator-visual-basic"></a>Like İşleci (Visual Basic)
Bir dizeyi bir düzene göre karşılaştırır.  

> [!IMPORTANT]
> @No__t-0 işleci Şu anda .NET Core ve .NET Standard projelerinde desteklenmez.

## <a name="syntax"></a>Sözdizimi  
  
```vb  
result = string Like pattern  
```  
  
## <a name="parts"></a>Bölümler  
 `result`  
 Gerekli. Herhangi bir `Boolean` değişkeni. Sonuç, `string` ' in `pattern` ' y i karşılayıp karşılamadığını belirten `Boolean` değeridir.  
  
 `string`  
 Gerekli. Herhangi bir `String` ifadesi.  
  
 `pattern`  
 Gerekli. "Açıklamalar" bölümünde açıklanan desenler ile eşleşen kurallara uyan herhangi bir `String` ifadesi.  
  
## <a name="remarks"></a>Açıklamalar  
 @No__t-0 ' daki değer `pattern` ' de bulunan bir düzene uygunsa, `result` `True` ' dir. Dize, kalıbı karşılamaz `result` `False` ' dir. Hem `string` hem de `pattern` dizeler boşsa, sonuç `True` olur.  
  
## <a name="comparison-method"></a>Karşılaştırma yöntemi  
 @No__t-0 işlecinin davranışı [Seçenek karşılaştırma bildirimine](../../../visual-basic/language-reference/statements/option-compare-statement.md)bağlıdır. Her kaynak dosya için varsayılan dize karşılaştırma yöntemi `Option Compare Binary` ' dır.  
  
## <a name="pattern-options"></a>Model seçenekleri  
 Yerleşik model eşleştirme, dize karşılaştırmaları için çok yönlü bir araç sağlar. Desenler ile eşleşen özellikler, `string` ' daki her karakteri belirli bir karakter, joker karakter, bir karakter listesi veya karakter aralığı ile eşleştirirken izin verir. Aşağıdaki tabloda `pattern` ' da izin verilen karakterler ve bunların eşleştikleri gösterilmektedir.  
  
|@No__t karakterler-0|@No__t eşleşme-0|  
|-----------------------------|-------------------------|  
|`?`|Herhangi bir tek karakter|  
|`*`|Sıfır veya daha fazla karakter|  
|`#`|Herhangi bir tek basamak (0 – 9)|  
|`[charlist]`|@No__t-0 ' da herhangi bir tek karakter|  
|`[!charlist]`|@No__t olmayan tek bir karakter-0|  
  
## <a name="character-lists"></a>Karakter listeleri  
 Köşeli ayraçlar (`[ ]`) içinde bir veya daha fazla karakter (`charlist`) grubu, `string` ' deki herhangi bir karakteri eşleştirmek için kullanılabilir ve rakamlar dahil neredeyse tüm karakter kodlarını içerebilir.  
  
 @No__t-1 ' in başındaki bir ünlem işareti (`!`), `string` ' te `charlist` ' deki karakterler dışında herhangi bir karakter bulunursa bir eşleşme yapıldığı anlamına gelir. Köşeli ayraçlar dışında kullanıldığında, ünlem işareti kendisiyle eşleşir.  
  
## <a name="special-characters"></a>Özel Karakterler  
 Sol köşeli ayraç (`[`), soru işareti (`?`), sayı işareti (`#`) ve yıldız işareti (`*`) eşleştirmek için, bu karakterleri köşeli ayraç içine alın. Sağ köşeli ayraç (`]`), bir grup içinde kendisiyle eşleşecek şekilde kullanılamaz, ancak tek bir karakter olarak bir grup dışında kullanılabilir.  
  
 @No__t-0 karakter sırası sıfır uzunluklu bir dize (`""`) olarak kabul edilir. Ancak, köşeli ayraç içine alınmış bir karakter listesinin parçası olamaz. @No__t-0 ' daki bir konumun bir karakter grubundan birini mi yoksa herhangi bir karakteri mi içerdiğini denetlemek istiyorsanız, `Like` ' i iki kez kullanabilirsiniz. Bir örnek için bkz. [nasıl yapılır: bir dizeyi bir düzene göre eşleştirme](../../../visual-basic/programming-guide/language-features/operators-and-expressions/how-to-match-a-string-against-a-pattern.md).  
  
## <a name="character-ranges"></a>Karakter aralıkları  
 Aralığın alt ve üst sınırlarını ayırmak için kısa çizgi (`–`) kullanarak, `charlist` bir karakter aralığı belirtebilir. Örneğin, `string` ' deki karşılık gelen karakter konumu, `A` – `Z` aralığında herhangi bir karakter içeriyorsa ve `[!H–L]`, karşılık gelen karakter konumu dışında herhangi bir karakter içeriyorsa, `[A–Z]` eşleşme ile sonuçlanır. Aralık `H` – `L`.  
  
 Bir karakter aralığı belirttiğinizde, bu karakterlerin artan sıralama düzeninde görünmesi gerekir, yani en küçükten en büyüğe. Bu nedenle, `[A–Z]` geçerli bir örüntü, ancak `[Z–A]` değildir.  
  
### <a name="multiple-character-ranges"></a>Birden çok karakter aralığı  
 Aynı karakter konumu için birden çok Aralık belirtmek için, bunları sınırlayıcılar olmadan aynı köşeli ayraç içine alın. Örneğin, `string` ' deki karşılık gelen karakter konumu `A` – `C` aralığında ya da `X` – `Z` aralığında herhangi bir karakter içeriyorsa `[A–CX–Z]` bir eşleşme ile sonuçlanır.  
  
### <a name="usage-of-the-hyphen"></a>Kısa çizgi kullanımı  
 Bir tire (`–`) başlangıcında (bir ünlem işaretiyle, varsa) veya `charlist` ' in sonuna ile eşleşmek üzere görünebilir. Diğer herhangi bir konumda, tire, tirein her iki tarafındaki karakterlerle sınırlandırılmış bir karakter aralığı tanımlar.  
  
## <a name="collating-sequence"></a>Harmanlama sırası  
 Belirtilen bir aralığın anlamı, `Option Compare` ve kodun üzerinde çalıştığı sistemin yerel ayar ayarı tarafından belirlendiği şekilde, çalışma zamanında karakter sıralamasına bağlıdır. @No__t-0 ile `[A–E]` aralığı `A`, `B`, `C`, `D` ve `E` ile eşleşir. @No__t-0 ile `[A–E]` ile `A`, `a`, `À`, `à`, `B`, `b`, `C`, `c`, 0, 1, 2 ve 3 arasında eşleşir. @No__t-0 veya `ê` ile eşleşmiyor çünkü aksanlı karakterler sıralama düzeninde vurgusuz sonra harmanlandıktan sonra harmanlama.  
  
## <a name="digraph-characters"></a>Digraf karakterleri  
 Bazı dillerde, iki ayrı karakteri temsil eden alfabetik karakterler vardır. Örneğin, birkaç dil `æ` karakterini `a` ve `e` karakterlerini göstermek için kullanır. @No__t-0 işleci, tek bir digraf karakterinin ve iki ayrı karakterin eşdeğer olduğunu algılar.  
  
 Sistem yerel ayarları 'nda bir digraf karakteri kullanan bir dil belirtildiğinde, `pattern` veya `string` ' de tek bir digraf karakterinin bir oluşumu, diğer dizedeki eşdeğer iki karakterli sırayla eşleşir. Benzer şekilde, köşeli ayraçlar içinde `pattern` ' daki bir digraf karakteri (bir listede veya bir aralıkta), `string` ' deki eşdeğer iki karakterlik sırayla eşleşir.  
  
## <a name="overloading"></a>Aşırı Yükleme  
 @No__t-0 işleci *aşırı*yüklenebilir, yani bir işlenen bu sınıf veya yapının türüne sahip olduğunda bir sınıf veya yapının davranışını yeniden tanımlayabileceği anlamına gelir. Kodunuz böyle bir sınıf veya yapıda bu işleci kullanıyorsa, yeniden tanımlanmış davranışını anladığınızdan emin olun. Daha fazla bilgi için bkz. [operatör yordamları](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Örnek  
 Bu örnek, dizeleri çeşitli desenlerle karşılaştırmak için `Like` işlecini kullanır. Sonuçlar, her bir dizenin bu kalıbı karşılayıp karşılamadığını belirten `Boolean` değişkenine gider.  
  
 [!code-vb[VbVbalrOperators#30](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#30)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualBasic.Strings.InStr%2A>
- <xref:Microsoft.VisualBasic.Strings.StrComp%2A>
- [Karşılaştırma İşleçleri](../../../visual-basic/language-reference/operators/comparison-operators.md)
- [Visual Basic operatör önceliği](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [İşlevselliğe Göre Listelenmiş İşleçler](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [Option Compare Deyimi](../../../visual-basic/language-reference/statements/option-compare-statement.md)
- [İşleçler ve İfadeler](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)
- [Nasıl yapılır: Bir Dizeyi Belirli Bir Desene Göre Eşleştirme](../../../visual-basic/programming-guide/language-features/operators-and-expressions/how-to-match-a-string-against-a-pattern.md)
