---
title: Normal İfadelerdeki Tutturucular
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- atomic zero-width assertions
- regular expressions, anchors
- regular expressions, atomic zero-width assertions
- anchors, in regular expressions
- metacharacters, atomic zero-width assertions
- metacharacters, anchors
- .NET Framework regular expressions, anchors
- .NET Framework regular expressions, atomic zero-width assertions
ms.assetid: 336391f6-2614-499b-8b1b-07a6837108a7
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2cbf0ceb7d5f8e56955f8989e5eb4efba99540bc
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="anchors-in-regular-expressions"></a>Normal İfadelerdeki Tutturucular
<a name="top"></a> Bağlayıcılarını veya atomik Sıfır Genişlik onayları bir eşleşme gerçekleştiği gerekir bir dizedeki belirtin. Arama ifadenizde bir yer işareti kullandığınızda, normal ifade motoru dize veya harcama karakterleri boyunca ilerlemez; sadece belirtilen konumda bir eşleşme arar. Örneğin `^` , eşleşmenin bir satır veya dize başında başlaması gerektiğini belirtir. Bu nedenle `^http:` normal ifadesi, sadece bir satırın başında gerçekleştiğinde "http:" ile eşleşir. Aşağıdaki tabloda .NET normal ifadelerde tarafından desteklenen bağlayıcıları listeler.  
  
|Yer işareti|Açıklama|  
|------------|-----------------|  
|`^`|Eşleşme dizenin veya satırın başlangıcında gerçekleşmelidir. Daha fazla bilgi için bkz: [Başlat, dize veya satır](#Start).|  
|`$`|Eşleşme dize veya satırının ya da önce sonunda gerçekleşmelidir `\n` dize veya satırının sonunda. Daha fazla bilgi için bkz: [son, dize veya satır](#End).|  
|`\A`|Eşleşme yalnızca dizenin başında gerçekleşmelidir (çok satır desteği yok). Daha fazla bilgi için bkz: [Başlat, dize yalnızca](#StartOnly).|  
|`\Z`|Eşleşme dizesinin ya da önce sonunda gerçekleşmelidir `\n` dizesi sonunda. Daha fazla bilgi için bkz: [son, dize ya da önce bitiş yeni satır](#EndOrNOnly).|  
|`\z`|Eşleşme sadece dizenin sonunda gerçekleşmelidir. Daha fazla bilgi için bkz: [son, dize yalnızca](#EndOnly).|  
|`\G`|Eşleşme önceki eşleşmenin sona erdiği konumda başlamalıdır. Daha fazla bilgi için bkz: [bitişik eşleşmeleri](#Contiguous).|  
|`\b`|Eşleşme bir kelime sınırında gerçekleşmemelidir. Daha fazla bilgi için bkz: [Word sınır](#WordBoundary).|  
|`\B`|Eşleşme bir sözcük sınırında gerçekleşmemelidir. Daha fazla bilgi için bkz: [olmayan Word sınır](#NonwordBoundary).|  
  
<a name="Start"></a>   
## <a name="start-of-string-or-line-"></a>Dize veya Satır Başlangıcı: ^  
 `^` yer işareti, aşağıdaki desenin dizenin ilk karakter konumunda başlaması gerektiğini belirtir. Kullanırsanız `^` ile <xref:System.Text.RegularExpressions.RegexOptions.Multiline?displayProperty=nameWithType> seçeneği (bkz [normal ifade seçenekleri](../../../docs/standard/base-types/regular-expression-options.md)), her satırın başındaki eşleşme olmalıdır.  
  
 Aşağıdaki örnek, bazı profesyonel beysbol takımlarının var olduğu yıllar hakkındaki bilgiyi ayıklayan normal bir ifadedeki `^` yer işaretini kullanır. Örnek, <xref:System.Text.RegularExpressions.Regex.Matches%2A?displayProperty=nameWithType> yönteminin iki aşırı yüklemesini çağırır:  
  
-   <xref:System.Text.RegularExpressions.Regex.Matches%28System.String%2CSystem.String%29> aşırı yüklemesine olan çağrı, yalnızca normal ifade deseni ile eşleşen girdi dizesindeki ilk alt dizeyi bulur.  
  
-   <xref:System.Text.RegularExpressions.Regex.Matches%28System.String%2CSystem.String%2CSystem.Text.RegularExpressions.RegexOptions%29> öğesine ayarlı `options` parametresiyle birlikte <xref:System.Text.RegularExpressions.RegexOptions.Multiline?displayProperty=nameWithType> aşırı yüklemesine olan çağrı beş alt dizenin tümünü bulur.  
  
 [!code-csharp[Conceptual.RegEx.Language.Assertions#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.assertions/cs/startofstring1.cs#1)]
 [!code-vb[Conceptual.RegEx.Language.Assertions#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.assertions/vb/startofstring1.vb#1)]  
  
 Normal ifade deseni `^((\w+(\s?)){2,}),\s(\w+\s\w+),(\s\d{4}(-(\d{4}|present))?,?)+` aşağıdaki tabloda gösterildiği gibi tanımlanır.  
  
|Desen|Açıklama|  
|-------------|-----------------|  
|`^`|Giriş dizesinin başında eşleşmeye başlayın (eğer yöntem <xref:System.Text.RegularExpressions.RegexOptions.Multiline?displayProperty=nameWithType> seçeneği ile çağrılırsa satırın başında).|  
|`((\w+(\s?)){2,}`|Tam olarak iki kez ardından sıfır veya bir boşluk gelen bir veya daha fazla sözcük karakterini eşleştirin. Bu ilk yakalama grubudur. Bu ifade aynı zamanda ikinci ve üçüncü bir yakalama grubunu tanımlar: İkinci grup yakalanan sözcükten, üçüncü grup ise yakalanan boşluktan oluşur.|  
|`,\s`|Ardından bir boşluk karakteri gelen bir virgülü eşleştirin.|  
|`(\w+\s\w+)`|Ardından bir boşluk gelen ve ardından bir veya daha fazla sözcük karakteri gelen bir veya daha fazla sözcük karakterini eşleştirin. Bu dördüncü yakalama grubudur.|  
|`,`|Bir virgülü eşleştirin.|  
|`\s\d{4}`|Ardından dört ondalık basamak gelen bir boşluğu eşleştirin.|  
|<code>(-(\d{4}&#124;present))?</code>|Ardından dört ondalık basamak veya "var" dizesi gelen bir tirenin sıfır veya bir oluşumunu eşleştirin. Bu altıncı yakalama grubudur. Ayrıca yedinci bir yakalama grubunu içerir.|  
|`,?`|Bir virgülün sıfır veya bir oluşumunu eşleştirin.|  
|<code>(\s\d{4}(-(\d{4}&#124;present))?,?)+</code>|Aşağıdakilerin bir veya daha fazla oluşumunu eşleştirin: bir boşluk, dört ondalık basamak, ardından dört ondalık basamak veya "var" dizesi gelen bir tirenin sıfır veya bir oluşumu ve sıfır veya bir virgül. Bu beşinci yakalama grubudur.|  
  
 [Başa dön](#top)  
  
<a name="End"></a>   
## <a name="end-of-string-or-line-"></a>Dize veya Satır Sonu: $  
 `$` Bağlantısı belirtir. önceki düzeni Giriş dizesinin ya da önce sonunda gerçekleşmelidir `\n` giriş dizesi sonunda.  
  
 Eğer `$` öğesini <xref:System.Text.RegularExpressions.RegexOptions.Multiline?displayProperty=nameWithType> seçeneği ile birlikte kullanıyorsanız eşleşme aynı zamanda satırın sonunda da oluşabilir. Unutmayın `$` eşleşen `\n` ancak eşleşmiyor `\r\n` (satır başı ve yeni satır karakterlerini veya CR/LF birlikte). CR/LF karakter bileşimi eşleşecek şekilde dahil `\r?$` normal ifade deseni içinde.  
  
 Aşağıdaki örnek, `$` örnekte kullanılan normal ifade deseni bağlantı [Başlat, dize veya satır](#Start) bölümü. Beş satırlık metin içeren özgün giriş dizesi ile kullanıldığında <xref:System.Text.RegularExpressions.Regex.Matches%28System.String%2CSystem.String%29?displayProperty=nameWithType> yöntemi bir eşleşme bulamaz, çünkü ilk satırın sonu `$` deseni ile eşleşmez. Özgün giriş dizesi bir dize dizisine bölündüğünde <xref:System.Text.RegularExpressions.Regex.Matches%28System.String%2CSystem.String%29?displayProperty=nameWithType> yöntemi beş satırının her birini eşlemede başarılı olur. <xref:System.Text.RegularExpressions.Regex.Matches%28System.String%2CSystem.String%2CSystem.Text.RegularExpressions.RegexOptions%29?displayProperty=nameWithType> yöntemi, `options` öğesine ayarlanmış <xref:System.Text.RegularExpressions.RegexOptions.Multiline?displayProperty=nameWithType> parametresi ile çağrıldığında hiçbir eşleşme bulunmaz, çünkü normal ifade deseni satır başı öğesini (\u+000D) hesaba katmaz. Bununla birlikte, normal ifade deseni değiştirildiği değiştirerek `$` ile `\r?$`, arama <xref:System.Text.RegularExpressions.Regex.Matches%28System.String%2CSystem.String%2CSystem.Text.RegularExpressions.RegexOptions%29?displayProperty=nameWithType> yöntemiyle `options` parametre kümesine <xref:System.Text.RegularExpressions.RegexOptions.Multiline?displayProperty=nameWithType> yeniden beş eşleştiğini bulur.  
  
 [!code-csharp[Conceptual.RegEx.Language.Assertions#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.assertions/cs/endofstring1.cs#2)]
 [!code-vb[Conceptual.RegEx.Language.Assertions#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.assertions/vb/endofstring1.vb#2)]  
  
 [Başa dön](#top)  
  
<a name="StartOnly"></a>   
## <a name="start-of-string-only-a"></a>Yalnızca Dize Başlangıcı: \A  
 `\A` Bağlantısı belirtir. bir eşleşme giriş dizesi başında olmalıdır. Aynı `^` , durumlar dışında bağlantı `\A` yoksayar <xref:System.Text.RegularExpressions.RegexOptions.Multiline?displayProperty=nameWithType> seçeneği. Bu nedenle, çok satırlı bir girdi dizesinde yalnızca ilk satırın başı ile eşleşebilir.  
  
 Aşağıdaki örnek, `^` ve `$` yer işaretlerine ait örnekler ile benzerdir. Kullandığı `\A` bağlantı kurulduğu bazı profesyonel Beyzbol ekipler var yıl hakkında bilgi ayıklar normal bir ifade. Giriş dizesi beş satır içerir. <xref:System.Text.RegularExpressions.Regex.Matches%28System.String%2CSystem.String%2CSystem.Text.RegularExpressions.RegexOptions%29?displayProperty=nameWithType> yöntemine yönelik çağrı yalnızca normal ifade deseni ile eşleşen girdi dizesindeki ilk alt dizeyi bulur. Örnekte gösterildiği gibi <xref:System.Text.RegularExpressions.RegexOptions.Multiline> seçeneğinin etkisi yoktur.  
  
 [!code-csharp[Conceptual.RegEx.Language.Assertions#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.assertions/cs/startofstring2.cs#3)]
 [!code-vb[Conceptual.RegEx.Language.Assertions#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.assertions/vb/startofstring2.vb#3)]  
  
 [Başa dön](#top)  
  
<a name="EndOrNOnly"></a>   
## <a name="end-of-string-or-before-ending-newline-z"></a>Dize Sonu veya Yeni Satır Sonlandırmadan Önce: \z  
 `\Z` Bağlantısı belirtir. bir eşleşme Giriş dizesinin ya da önce sonunda gerçekleşmelidir `\n` giriş dizesi sonunda. Aynı `$` , durumlar dışında bağlantı `\Z` yoksayar <xref:System.Text.RegularExpressions.RegexOptions.Multiline?displayProperty=nameWithType> seçeneği. Bu nedenle, çok satırlı bir dize, yalnızca son satırı veya önce son satır sonu eşleştirebilirsiniz `\n`.  
  
 Unutmayın `\Z` eşleşen `\n` ancak eşleşmiyor `\r\n` (CR/LF karakter birlikte). CR/LF eşleşecek şekilde dahil `\r?\Z` normal ifade deseni içinde.  
  
 Aşağıdaki örnek kullanır `\Z` örneğe benzer bir normal ifade bulunan yer işaretine [Başlat, dize veya satır](#Start) hangi bazı profesyonel Beyzbol sırasında yıl hakkında bilgi ayıklar bölümü Takımlar vardı. Alt `\r?\Z` normal ifadede `^((\w+(\s?)){2,}),\s(\w+\s\w+),(\s\d{4}(-(\d{4}|present))?,?)+\r?\Z` bir dize sonu eşleştiğinden ve ayrıca ile biten bir dizeyle eşleşir `\n` veya `\r\n`. Sonuç olarak, dizideki her bir öğe normal ifade deseni ile eşleşir.  
  
 [!code-csharp[Conceptual.RegEx.Language.Assertions#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.assertions/cs/endofstring2.cs#4)]
 [!code-vb[Conceptual.RegEx.Language.Assertions#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.assertions/vb/endofstring2.vb#4)]  
  
 [Başa dön](#top)  
  
<a name="EndOnly"></a>   
## <a name="end-of-string-only-z"></a>Yalnızca Dize Sonu: \z  
 `\z` Bağlantısı belirtir. bir eşleşme giriş dizesi sonunda gerçekleşmelidir. Gibi `$` language öğesi `\z` yoksayar <xref:System.Text.RegularExpressions.RegexOptions.Multiline?displayProperty=nameWithType> seçeneği. Aksine `\Z` language öğesi `\z` eşleşmeyen bir `\n` bir dizenin sonunda karakter. Bu nedenle, yalnızca giriş dizesinin son satırı ile eşleşebilir.  
  
 Aşağıdaki örnek kullanır `\z` bağlantı kurulduğu bazı profesyonel Beyzbol ekipler var yıl hakkında bilgi ayıklar önceki bölümdeki örnek aksi aynıdır normal bir ifade. Örneğin bir dize dizisinde normal ifade deseni ile beş öğelerin her birini eşleştirmeyi dener `^((\w+(\s?)){2,}),\s(\w+\s\w+),(\s\d{4}(-(\d{4}|present))?,?)+\r?\z`. Dizelerden ikisi satır başı ve satır besleme karakteri ile, bir tanesi satır besleme karakteri ile, iki tanesi ise ne satır başı ne de satır besleme karakteri ile biter. Çıktıda gösterildiği gibi yalnızca bir satır başı veya satır besleme karakteri olmayan dizeler desen ile eşleşir.  
  
 [!code-csharp[Conceptual.RegEx.Language.Assertions#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.assertions/cs/endofstring3.cs#5)]
 [!code-vb[Conceptual.RegEx.Language.Assertions#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.assertions/vb/endofstring3.vb#5)]  
  
 [Başa dön](#top)  
  
<a name="Contiguous"></a>   
## <a name="contiguous-matches-g"></a>Bitişik Eşleştirmeler: \G  
 `\G` Bağlantısı belirtir. burada önceki eşleşmeye sona erdi noktada bir eşleşme olmalıdır. Bu yer işaretini <xref:System.Text.RegularExpressions.Regex.Matches%2A?displayProperty=nameWithType> veya <xref:System.Text.RegularExpressions.Match.NextMatch%2A?displayProperty=nameWithType> yöntemi ile kullandığınızda tüm eşleşmelerin bitişik olmasını sağlar.  
  
 Aşağıdaki örnek rodent türlerinin adlarını virgülle ayrılmış dizeden çıkartmak için normal bir ifade kullanır.  
  
 [!code-csharp[Conceptual.RegEx.Language.Assertions#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.assertions/cs/contiguous1.cs#6)]
 [!code-vb[Conceptual.RegEx.Language.Assertions#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.assertions/vb/contiguous1.vb#6)]  
  
 Normal ifade `\G(\w+\s?\w*),?` aşağıdaki tabloda gösterildiği gibi yorumlanır.  
  
|Desen|Açıklama|  
|-------------|-----------------|  
|`\G`|Son eşleşmenin sona erdiği yerden başlayın.|  
|`\w+`|Bir veya daha fazla sözcük karakteri eşleştir.|  
|`\s?`|Sıfır veya bir boşluğu eşleştirin.|  
|`\w*`|Sıfır veya daha fazla sözcük karakteriyle eşleş.|  
|`(\w+\s?\w*)`|Ardından sıfır veya bir boşluk gelen ve ardından sıfır veya daha fazla sözcük karakteri gelen bir veya daha fazla sözcük karakterini eşleştirin. Bu ilk yakalama grubudur.|  
|`,?`|Sabit bir virgül karakterinin sıfır veya bir oluşumunu eşleştirin.|  
  
 [Başa dön](#top)  
  
<a name="WordBoundary"></a>   
## <a name="word-boundary-b"></a>Sözcük Sınırı: \b  
 `\b` Bağlantısı belirtir. eşleşen bir sözcük karakteriyle arasında bir sınır gerçekleşmelidir ( `\w` language öğesi) ve bir word olmayan karakter ( `\W` language öğesi). Sözcük karakteri alfasayısal karakterler ve alt çizgilerden oluşur; sözcük olmayan bir karakter ise alfasayısal veya bir alt çizgi olmayan herhangi bir karakterdir. (Daha fazla bilgi için bkz: [karakter sınıfları](../../../docs/standard/base-types/character-classes-in-regular-expressions.md).) Eşleşme aynı zamanda dizenin başı veya sonundaki bir sözcük sınırında da oluşabilir.  
  
 `\b` yer işareti genellikle bir alt ifadenin, bir sözcüğün yalnızca başlangıcı ya da bitişi yerine tüm sözcük ile eşleştiğinden emin olmak için kullanılır. Normal ifade `\bare\w*\b` aşağıdaki örnekte bu kullanımını gösterir. "Olan" alt dizesi ile başlayan herhangi bir sözcüğü eşleştirir. Örneğin çıktısı ayrıca `\b` öğesinin, giriş dizesinin başlangıcı ve sonuyla eşleştiğini gösterir.  
  
 [!code-csharp[Conceptual.RegEx.Language.Assertions#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.assertions/cs/word1.cs#7)]
 [!code-vb[Conceptual.RegEx.Language.Assertions#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.assertions/vb/word1.vb#7)]  
  
 Normal ifade deseni aşağıdaki tabloda gösterildiği gibi yorumlanır.  
  
|Desen|Açıklama|  
|-------------|-----------------|  
|`\b`|Bir sözcük sınırında eşleşmeye başla.|  
|`are`|"Olan" alt dizesini eşleştirin.|  
|`\w*`|Sıfır veya daha fazla sözcük karakteriyle eşleş.|  
|`\b`|Eşlemeyi bir sözcük sınırında sonlandır.|  
  
 [Başa dön](#top)  
  
<a name="NonwordBoundary"></a>   
## <a name="non-word-boundary-b"></a>Sözcük Olmayan Sınır: \B  
 `\B` Bağlantısı belirtir. eşleşen bir word sınırında oluşamaz. Bu, `\b` yer işaretinin tersidir.  
  
 Aşağıdaki örnek kullanır `\B` "Pro" substring oluşumları word bulmak için bağlayıcı. Normal ifade deseni `\Bqu\w+` "sözcüğün sonuna kadar devam eder ve bir sözcük başlamıyor bir Pro" ile başlayan bir altdizgi eşleştirmesi.  
  
 [!code-csharp[Conceptual.RegEx.Language.Assertions#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.assertions/cs/nonword1.cs#8)]
 [!code-vb[Conceptual.RegEx.Language.Assertions#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.assertions/vb/nonword1.vb#8)]  
  
 Normal ifade deseni aşağıdaki tabloda gösterildiği gibi yorumlanır.  
  
|Desen|Açıklama|  
|-------------|-----------------|  
|`\B`|Eşlemeyi bir sözcük sınırında başlatmayın.|  
|`qu`|"qu" alt dizesini eşleştirin.|  
|`\w+`|Bir veya daha fazla sözcük karakteri eşleştir.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Normal İfade Dili - Hızlı Başvuru](../../../docs/standard/base-types/regular-expression-language-quick-reference.md)  
 [Normal İfade Seçenekleri](../../../docs/standard/base-types/regular-expression-options.md)
