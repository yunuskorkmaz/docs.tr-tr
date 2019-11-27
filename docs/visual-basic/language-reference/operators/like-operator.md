---
title: Like İşleci
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
ms.openlocfilehash: 5db9488bbec716156a3ab464042c0853241a82b1
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74350941"
---
# <a name="like-operator-visual-basic"></a>Like İşleci (Visual Basic)
Bir dizeyi bir düzene göre karşılaştırır.  

> [!IMPORTANT]
> `Like` işleci Şu anda .NET Core ve .NET Standard projelerinde desteklenmez.

## <a name="syntax"></a>Sözdizimi  
  
```vb  
result = string Like pattern  
```  
  
## <a name="parts"></a>Bölümler  
 `result`  
 Gerekli. Herhangi bir `Boolean` değişken. Sonuç, `string` `pattern`karşılayıp karşılamadığını belirten `Boolean` bir değerdir.  
  
 `string`  
 Gerekli. Herhangi bir `String` ifadesi.  
  
 `pattern`  
 Gerekli. "Açıklamalar" bölümünde açıklanan desenler ile eşleşen kurallara uyan herhangi bir `String` ifadesi.  
  
## <a name="remarks"></a>Açıklamalar  
 `string` değeri `pattern`bulunan kalıbı karşılıyorsa `result` `True`. Dize, `False``result`. Hem `string` hem de `pattern` boş dizelerdir, sonuç `True`olur.  
  
## <a name="comparison-method"></a>Karşılaştırma yöntemi  
 `Like` işlecinin davranışı [Seçenek karşılaştırma bildirimine](../../../visual-basic/language-reference/statements/option-compare-statement.md)bağlıdır. Her kaynak dosya için varsayılan dize karşılaştırma yöntemi `Option Compare Binary`.  
  
## <a name="pattern-options"></a>Model seçenekleri  
 Yerleşik model eşleştirme, dize karşılaştırmaları için çok yönlü bir araç sağlar. Desenler ile eşleşen özellikler, `string` her bir karakteri belirli bir karakter, joker karakter, bir karakter listesi veya bir karakter aralığı ile eşleştirmesini sağlar. Aşağıdaki tabloda `pattern` ' de izin verilen karakterler ve bunların eşleştikleri gösterilmektedir.  
  
|`pattern` karakterler|`string` eşleşiyor|  
|-----------------------------|-------------------------|  
|`?`|Herhangi bir tek karakter|  
|`*`|Sıfır veya daha fazla karakter|  
|`#`|Herhangi bir tek basamak (0 – 9)|  
|`[charlist]`|`charlist` bir tek karakter|  
|`[!charlist]`|`charlist` olmayan bir tek karakter|  
  
## <a name="character-lists"></a>Karakter listeleri  
 Köşeli ayraçlar (`[ ]`) içindeki bir veya daha fazla karakter (`charlist`) grubu, `string` tek bir karakterle eşleştirmek için kullanılabilir ve rakamlar dahil neredeyse tüm karakter kodlarını içerebilir.  
  
 `charlist` başındaki bir ünlem işareti (`!`), `charlist` karakterler dışında herhangi bir karakter `string`içinde bulunursa bir eşleşmenin yapıldığı anlamına gelir. Köşeli ayraçlar dışında kullanıldığında, ünlem işareti kendisiyle eşleşir.  
  
## <a name="special-characters"></a>Özel Karakterler  
 Sol köşeli ayraç (`[`), soru işareti (`?`), numara işareti (`#`) ve yıldız işareti (`*`) ile eşleştirmek için bunları köşeli ayraç içine alın. Sağ köşeli ayraç (`]`), bir grup içinde kendisiyle eşleşmek için kullanılamaz, ancak tek bir karakter olarak bir grup dışında kullanılabilir.  
  
 `[]` karakter sırası sıfır uzunluklu bir dize (`""`) olarak kabul edilir. Ancak, köşeli ayraç içine alınmış bir karakter listesinin parçası olamaz. `string` bir konumun bir karakter grubundan birini mi yoksa herhangi bir karakteri mi içerdiğini denetlemek istiyorsanız, `Like` iki kez kullanabilirsiniz. Bir örnek için bkz. [nasıl yapılır: bir dizeyi bir düzene göre eşleştirme](../../../visual-basic/programming-guide/language-features/operators-and-expressions/how-to-match-a-string-against-a-pattern.md).  
  
## <a name="character-ranges"></a>Karakter aralıkları  
 Aralığın alt ve üst sınırlarını ayırmak için kısa çizgi (`–`) kullanarak `charlist` bir karakter aralığı belirtebilir. Örneğin, `string` karşılık gelen karakter konumu `A`–`Z`aralığı içinde herhangi bir karakter içeriyorsa ve `[!H–L]`, karşılık gelen karakter konumu Aralık dışında herhangi bir karakter içeriyorsa, bir eşleşme ile sonuçlanır `[A–Z]`.`H``L`  
  
 Bir karakter aralığı belirttiğinizde, bu karakterlerin artan sıralama düzeninde görünmesi gerekir, yani en küçükten en büyüğe. Bu nedenle, `[A–Z]` geçerli bir örüntü, ancak `[Z–A]` değildir.  
  
### <a name="multiple-character-ranges"></a>Birden çok karakter aralığı  
 Aynı karakter konumu için birden çok Aralık belirtmek için, bunları sınırlayıcılar olmadan aynı köşeli ayraç içine alın. Örneğin, `string` karşılık gelen karakter konumu `A`–`C` veya `X`–`Z`aralığında herhangi bir karakter içeriyorsa, `[A–CX–Z]` bir eşleştirmeye neden olur.  
  
### <a name="usage-of-the-hyphen"></a>Kısa çizgi kullanımı  
 Kısa çizgi (`–`), başında (ünlem işaretiyle, varsa) veya `charlist` sonunda ile eşleşmek için görünebilir. Diğer herhangi bir konumda, tire, tirein her iki tarafındaki karakterlerle sınırlandırılmış bir karakter aralığı tanımlar.  
  
## <a name="collating-sequence"></a>Harmanlama sırası  
 Belirtilen bir aralığın anlamı, `Option Compare` tarafından belirlendiği şekilde, çalışma zamanında karakter sıralamasına ve kodun üzerinde çalıştığı sistemin yerel ayar ayarına göre değişir. `Option Compare Binary`, Aralık `[A–E]` `A`, `B`, `C`, `D`ve `E`eşleşir. `Option Compare Text`, `[A–E]` `A`, `a`, `À`, `à`, `B`, `b`, `C`, `c`, `D`, `d`, `E`ve `e`eşleşir. Aralık `Ê` veya `ê` eşleşmiyor çünkü aksanlı karakterler sıralama düzeninde vurgusuz sonra harmanlandıktan sonra harmanlama.  
  
## <a name="digraph-characters"></a>Digraf karakterleri  
 Bazı dillerde, iki ayrı karakteri temsil eden alfabetik karakterler vardır. Örneğin, birkaç dil, `a` karakterleri göstermek için `æ` karakter kullanır ve birlikte görüntülendiklerinde `e`. `Like` işleci, tek bir digraf karakterinin ve iki ayrı karakterin eşdeğer olduğunu algılar.  
  
 Sistem yerel ayarları 'nda bir digraf karakteri kullanan bir dil belirtildiğinde, `pattern` veya `string` tek bir digraf karakterinin bir oluşumu, diğer dizedeki eşdeğer iki karakterli dizi ile eşleşir. Benzer şekilde, köşeli ayraçlar içinde `pattern` bir digraf karakteri (bir listede veya bir Aralık içinde), `string`denk iki karakterlik sırayla eşleşir.  
  
## <a name="overloading"></a>Aşırı Yükleme  
 `Like` işleci *aşırı*yüklenebilir, yani bir işlenen bu sınıf veya yapının türüne sahip olduğunda bir sınıf veya yapının davranışını yeniden tanımlayabileceği anlamına gelir. Kodunuz böyle bir sınıf veya yapıda bu işleci kullanıyorsa, yeniden tanımlanmış davranışını anladığınızdan emin olun. Daha fazla bilgi için bkz. [operatör yordamları](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Örnek  
 Bu örnek, dizeleri çeşitli desenlerle karşılaştırmak için `Like` işlecini kullanır. Sonuçlar, her bir dizenin düzene uygun olup olmadığını gösteren bir `Boolean` değişkenine gider.  
  
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
