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
ms.openlocfilehash: 4279d90c74c80403146448a8ba5a6051ec9d12f6
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84401568"
---
# <a name="like-operator-visual-basic"></a>Like İşleci (Visual Basic)
Bir dizeyi bir düzene göre karşılaştırır.  

> [!IMPORTANT]
> `Like`İşleç Şu anda .NET Core ve .NET Standard projelerinde desteklenmez.

## <a name="syntax"></a>Sözdizimi  
  
```vb  
result = string Like pattern  
```  
  
## <a name="parts"></a>Bölümler  
 `result`  
 Gereklidir. Herhangi bir `Boolean` değişken. Sonuç, `Boolean` karşılayıp karşılamadığını gösteren bir değerdir `string` `pattern` .  
  
 `string`  
 Gereklidir. Herhangi bir `String` ifade.  
  
 `pattern`  
 Gereklidir. `String`"Açıklamalar" bölümünde açıklanan desenler ile eşleşen kurallara uyan ifadeler.  
  
## <a name="remarks"></a>Açıklamalar  
 İçindeki değeri `string` içinde bulunan bir kalıbı karşılıyorsa,, `pattern` `result` olur `True` . Dize, bu kalıbı karşılamaz `result` `False` . Hem hem `string` de `pattern` boş dizeler varsa, sonuç olur `True` .  
  
## <a name="comparison-method"></a>Karşılaştırma yöntemi  
 `Like`İşlecin davranışı [Seçenek karşılaştırma bildirimine](../statements/option-compare-statement.md)bağlıdır. Her kaynak dosya için varsayılan dize karşılaştırma yöntemi `Option Compare Binary` .  
  
## <a name="pattern-options"></a>Model seçenekleri  
 Yerleşik model eşleştirme, dize karşılaştırmaları için çok yönlü bir araç sağlar. Desenler ile eşleşen özellikler, içindeki her karakteri `string` belirli bir karakter, joker karakter, bir karakter listesi veya karakter aralığı ile eşleştirirken izin verir. Aşağıdaki tabloda ' da izin verilen karakterler `pattern` ve bunların eşleştiği özellikler gösterilmektedir.  
  
|İçindeki karakterler`pattern`|İçindeki eşleşmeler`string`|  
|-----------------------------|-------------------------|  
|`?`|Herhangi bir tek karakter|  
|`*`|Sıfır veya daha fazla karakter|  
|`#`|Herhangi bir tek basamak (0 – 9)|  
|`[charlist]`|İçinde herhangi bir tek karakter`charlist`|  
|`[!charlist]`|Herhangi bir tek karakter`charlist`|  
  
## <a name="character-lists"></a>Karakter listeleri  
 Parantez dahil bir veya daha fazla karakter () içeren bir grup () `charlist` `[ ]` , içindeki herhangi bir karakteri eşleştirmek için kullanılabilir `string` ve rakamlar dahil neredeyse tüm karakter kodlarını içerebilir.  
  
 Öğesinin başındaki bir ünlem işareti ( `!` ), içinde `charlist` karakterler dışında herhangi bir karakter içinde bulunursa eşleşme yapılır anlamına gelir `charlist` `string` . Köşeli ayraçlar dışında kullanıldığında, ünlem işareti kendisiyle eşleşir.  
  
## <a name="special-characters"></a>Özel Karakterler  
 Sol köşeli ayraç ( `[` ), soru işareti ( `?` ), sayı işareti ( `#` ) ve yıldız işareti () gibi özel karakterleri eşleştirmek için `*` bunları köşeli ayraç içine alın. Sağ köşeli ayraç ( `]` ) bir grup içinde kendisiyle eşleşecek şekilde kullanılamaz, ancak tek bir karakter olarak bir grup dışında kullanılabilir.  
  
 Karakter sırası `[]` sıfır uzunluklu bir dize () olarak kabul edilir `""` . Ancak, köşeli ayraç içine alınmış bir karakter listesinin parçası olamaz. İçindeki bir konumun bir `string` karakter grubundan birini mi yoksa herhangi bir karakteri mi içerdiğini denetlemek isterseniz `Like` iki kez kullanabilirsiniz. Bir örnek için bkz. [nasıl yapılır: bir dizeyi bir düzene göre eşleştirme](../../programming-guide/language-features/operators-and-expressions/how-to-match-a-string-against-a-pattern.md).  
  
## <a name="character-ranges"></a>Karakter aralıkları  
 `–`Aralığın alt ve üst sınırlarını ayırmak için kısa çizgi () kullanarak `charlist` bir karakter aralığı belirtebilirsiniz. Örneğin, `[A–Z]` içindeki karşılık gelen karakter konumu, `string` Aralık içinde herhangi bir karakter içeriyorsa `A` `Z` ve `[!H–L]` karşılık gelen karakter konumu Aralık dışında herhangi bir karakter içeriyorsa bir `H` `L` eşleşme ile sonuçlanır.  
  
 Bir karakter aralığı belirttiğinizde, bu karakterlerin artan sıralama düzeninde görünmesi gerekir, yani en küçükten en büyüğe. Bu nedenle, `[A–Z]` geçerli bir örüntü, ancak `[Z–A]` değildir.  
  
### <a name="multiple-character-ranges"></a>Birden çok karakter aralığı  
 Aynı karakter konumu için birden çok Aralık belirtmek için, bunları sınırlayıcılar olmadan aynı köşeli ayraç içine alın. Örneğin, `[A–CX–Z]` içindeki karşılık gelen karakter konumu, `string` Aralık içinde herhangi bir karakter `A` `C` veya-aralığı içinde herhangi bir karakter içeriyorsa, bir eşleşme ile sonuçlanır `X` `Z` .  
  
### <a name="usage-of-the-hyphen"></a>Kısa çizgi kullanımı  
 Kısa çizgi ( `–` ), başında (ünlem işaretiyle, varsa) veya sonuna kadar bir nokta () görünebilir `charlist` . Diğer herhangi bir konumda, tire, tirein her iki tarafındaki karakterlerle sınırlandırılmış bir karakter aralığı tanımlar.  
  
## <a name="collating-sequence"></a>Harmanlama sırası  
 Belirtilen bir aralığın anlamı, tarafından belirlendiği şekilde çalışma zamanında karakter sıralamasına `Option Compare` ve kodun üzerinde çalıştığı sistemin yerel ayar ayarına bağlıdır. İle, aralığı,,, `Option Compare Binary` `[A–E]` ve ile eşleşir `A` `B` `C` `D` `E` . ,,,,,,,,,,,,, `Option Compare Text` `[A–E]` Ve ile eşleşir `A` `a` `À` `à` `B` `b` `C` `c` `D` `d` `E` `e` . Aralık eşleşmiyor `Ê` veya aksanlı `ê` karakterler sıralama düzeninde vurgusuz olmayan karakterlerden sonra harmanlanmıyor.  
  
## <a name="digraph-characters"></a>Digraf karakterleri  
 Bazı dillerde, iki ayrı karakteri temsil eden alfabetik karakterler vardır. Örneğin, birkaç dil, `æ` karakterleri temsil eden karakteri `a` ve `e` birlikte görüntülendikleri karakteri kullanır. `Like`İşleci, tek bir digraf karakterinin ve iki ayrı karakterin eşdeğer olduğunu algılar.  
  
 Sistem yerel ayarlarında bir digraf karakteri kullanan bir dil belirtildiğinde, ya da içinde tek bir digraf karakterinin bir oluşumu `pattern` `string` diğer dizedeki eşdeğer iki karakterli dizi ile eşleşir. Benzer şekilde, parantez içine alınmış bir dime karakteri `pattern` (kendisiyle, bir listede veya bir aralığa göre), içindeki eşdeğer iki karakterli sırayla eşleşir `string` .  
  
## <a name="overloading"></a>Aşırı Yükleme  
 `Like`İşleç *aşırı*yüklenebilir, yani bir işlenen bu sınıf veya yapının türüne sahip olduğunda bir sınıf veya yapının davranışını yeniden tanımlayabileceği anlamına gelir. Kodunuz böyle bir sınıf veya yapıda bu işleci kullanıyorsa, yeniden tanımlanmış davranışını anladığınızdan emin olun. Daha fazla bilgi için bkz. [operatör yordamları](../../programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Örnek  
 Bu örnek, `Like` dizeleri çeşitli desenlerle karşılaştırmak için işlecini kullanır. Sonuçlar, `Boolean` her bir dizenin düzene uygun olup olmadığını gösteren bir değişkene gider.  
  
 [!code-vb[VbVbalrOperators#30](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#30)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualBasic.Strings.InStr%2A>
- <xref:Microsoft.VisualBasic.Strings.StrComp%2A>
- [Karşılaştırma Işleçleri](comparison-operators.md)
- [Visual Basic'de İşleç Önceliği](operator-precedence.md)
- [İşlevselliğe Göre Listelenmiş İşleçler](operators-listed-by-functionality.md)
- [Option Compare Deyimi](../statements/option-compare-statement.md)
- [İşleçler ve Ifadeler](../../programming-guide/language-features/operators-and-expressions/index.md)
- [Nasıl yapılır: Bir Dizeyi Belirli Bir Desene Göre Eşleştirme](../../programming-guide/language-features/operators-and-expressions/how-to-match-a-string-against-a-pattern.md)
