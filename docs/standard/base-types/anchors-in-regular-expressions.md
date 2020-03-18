---
title: .NET Düzenli İfadelerde Çapalar
description: Çapaları normal ifade desenlerinde nasıl kullanacağınızı öğrenin.
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
ms.openlocfilehash: c4853a6854f5da1a3217c976a03ddbde3b528560
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "78159669"
---
# <a name="anchors-in-regular-expressions"></a>Normal İfadelerdeki Tutturucular
Çapalar veya atomik sıfır genişlik iddiaları, bir eşleşmenin oluşması gereken dizedeki konumu belirtin. Arama ifadenizde bir yer işareti kullandığınızda, normal ifade motoru dize veya harcama karakterleri boyunca ilerlemez; sadece belirtilen konumda bir eşleşme arar. Örneğin `^` , eşleşmenin bir satır veya dize başında başlaması gerektiğini belirtir. Bu nedenle `^http:` normal ifadesi, sadece bir satırın başında gerçekleştiğinde "http:" ile eşleşir. Aşağıdaki tabloda .NET'teki normal ifadeler tarafından desteklenen çapalar listelenir.  
  
|Yer işareti|Açıklama|  
|------------|-----------------|  
|`^`|Varsayılan olarak, eşleşme dize başında oluşmalıdır; çok satırlı modda, satırın başında meydana gelmelidir. Daha fazla bilgi için [String veya Line'ın Başlangıcı'na](#start-of-string-or-line-)bakın.|  
|`$`|Varsayılan olarak, eşleşme dize sonunda veya dize sonunda önce `\n` oluşmalıdır; çok satırlı modda, satırın sonunda veya `\n` satırın sonunda önce meydana gelmelidir. Daha fazla bilgi için String [veya Satır Sonu'na](#end-of-string-or-line-)bakın.|  
|`\A`|Eşleşme yalnızca dizenin başında gerçekleşmelidir (çok satır desteği yok). Daha fazla bilgi için Yalnızca [String'in Başlangıcı'na](#start-of-string-only-a)bakın.|  
|`\Z`|Eşleşme, dize sonunda veya dize `\n` sonunda önce oluşmalıdır. Daha fazla bilgi için [String'in Sonu veya Yeni Satırı Sona Erdirmeden Önce](#end-of-string-or-before-ending-newline-z)bölümüne bakın.|  
|`\z`|Eşleşme sadece dizenin sonunda gerçekleşmelidir. Daha fazla bilgi için yalnızca [String'in Sonu'na](#end-of-string-only-z)bakın.|  
|`\G`|Eşleşme önceki eşleşmenin sona erdiği konumda başlamalıdır. Daha fazla bilgi için [Bitişik Eşleşmeler'e](#contiguous-matches-g)bakın.|  
|`\b`|Eşleşme bir kelime sınırında gerçekleşmemelidir. Daha fazla bilgi için [Sözcük Sınırı'na](#word-boundary-b)bakın.|  
|`\B`|Eşleşme bir sözcük sınırında gerçekleşmemelidir. Daha fazla bilgi için Word [Olmayan Sınır'a](#non-word-boundary-b)bakın.|  

## <a name="start-of-string-or-line-"></a>Dize veya Satır Başlangıcı: ^  
 Varsayılan olarak, `^` bağlantı noktası aşağıdaki desenin dizeilk karakter konumunda başlaması gerektiğini belirtir. Seçeneği yle `^` kullanıyorsanız [(Bkz. Normal İfade Seçenekleri),](../../../docs/standard/base-types/regular-expression-options.md)eşleşme her satırın başında gerçekleşmelidir. <xref:System.Text.RegularExpressions.RegexOptions.Multiline?displayProperty=nameWithType>  
  
 Aşağıdaki örnek, bazı profesyonel beysbol takımlarının var olduğu yıllar hakkındaki bilgiyi ayıklayan normal bir ifadedeki `^` yer işaretini kullanır. Örnek, <xref:System.Text.RegularExpressions.Regex.Matches%2A?displayProperty=nameWithType> yönteminin iki aşırı yüklemesini çağırır:  
  
- <xref:System.Text.RegularExpressions.Regex.Matches%28System.String%2CSystem.String%29> aşırı yüklemesine olan çağrı, yalnızca normal ifade deseni ile eşleşen girdi dizesindeki ilk alt dizeyi bulur.  
  
- <xref:System.Text.RegularExpressions.Regex.Matches%28System.String%2CSystem.String%2CSystem.Text.RegularExpressions.RegexOptions%29> öğesine ayarlı `options` parametresiyle birlikte <xref:System.Text.RegularExpressions.RegexOptions.Multiline?displayProperty=nameWithType> aşırı yüklemesine olan çağrı beş alt dizenin tümünü bulur.  
  
 [!code-csharp[Conceptual.RegEx.Language.Assertions#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.assertions/cs/startofstring1.cs#1)]
 [!code-vb[Conceptual.RegEx.Language.Assertions#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.assertions/vb/startofstring1.vb#1)]  
  
 Normal ifade `^((\w+(\s?)){2,}),\s(\w+\s\w+),(\s\d{4}(-(\d{4}|present))?,?)+` deseni aşağıdaki tabloda gösterildiği gibi tanımlanır.  
  
|Desen|Açıklama|  
|-------------|-----------------|  
|`^`|Giriş dizesinin başında eşleşmeye başlayın (eğer yöntem <xref:System.Text.RegularExpressions.RegexOptions.Multiline?displayProperty=nameWithType> seçeneği ile çağrılırsa satırın başında).|  
|`((\w+(\s?)){2,}`|Bir veya daha fazla sözcük karakterini sıfır veya bir boşluk la en az iki kez eşleştirin. Bu ilk yakalama grubudur. Bu ifade aynı zamanda ikinci ve üçüncü yakalama grubunu da tanımlar: İkinci yakalanan sözcükten oluşur ve üçüncüsü yakalanan beyaz boşluktan oluşur.|  
|`,\s`|Ardından bir boşluk karakteri gelen bir virgülü eşleştirin.|  
|`(\w+\s\w+)`|Ardından bir boşluk gelen ve ardından bir veya daha fazla sözcük karakteri gelen bir veya daha fazla sözcük karakterini eşleştirin. Bu dördüncü yakalama grubudur.|  
|`,`|Bir virgülü eşleştirin.|  
|`\s\d{4}`|Ardından dört ondalık basamak gelen bir boşluğu eşleştirin.|  
|<code>(-(\d{4}&#124;present))?</code>|Ardından dört ondalık basamak veya "var" dizesi gelen bir tirenin sıfır veya bir oluşumunu eşleştirin. Bu altıncı yakalama grubudur. Ayrıca yedinci bir yakalama grubunu içerir.|  
|`,?`|Bir virgülün sıfır veya bir oluşumunu eşleştirin.|  
|<code>(\s\d{4}(-(\d{4}&#124;present))?,?)+</code>|Aşağıdakilerin bir veya daha fazla oluşumunu eşleştirin: bir boşluk, dört ondalık basamak, ardından dört ondalık basamak veya "var" dizesi gelen bir tirenin sıfır veya bir oluşumu ve sıfır veya bir virgül. Bu beşinci yakalama grubudur.|

## <a name="end-of-string-or-line-"></a>Dize veya Satır Sonu: $  
 Bağlantı, `$` önceki desenin giriş dizesinin sonunda veya `\n` giriş dizesinin sonunda oluşması gerektiğini belirtir.  
  
 Eğer `$` öğesini <xref:System.Text.RegularExpressions.RegexOptions.Multiline?displayProperty=nameWithType> seçeneği ile birlikte kullanıyorsanız eşleşme aynı zamanda satırın sonunda da oluşabilir. `$` Eşleştiğini `\n` ancak eşleşmediğini `\r\n` unutmayın (satır başı ve yeni satır karakterleri veya CR/LF kombinasyonu). CR/LF karakter birleşimiile eşleştirmek için normal ifade desenine ekleyin. `\r?$`  
  
 Aşağıdaki örnek, `$` [dize veya Satır ın Başlangıcı](#start-of-string-or-line-) bölümünde örnekte kullanılan normal ifade deseni için çapa ekler. Beş satırlık metin içeren özgün giriş dizesi ile kullanıldığında <xref:System.Text.RegularExpressions.Regex.Matches%28System.String%2CSystem.String%29?displayProperty=nameWithType> yöntemi bir eşleşme bulamaz, çünkü ilk satırın sonu `$` deseni ile eşleşmez. Özgün giriş dizesi bir dize dizisine bölündüğünde <xref:System.Text.RegularExpressions.Regex.Matches%28System.String%2CSystem.String%29?displayProperty=nameWithType> yöntemi beş satırının her birini eşlemede başarılı olur. <xref:System.Text.RegularExpressions.Regex.Matches%28System.String%2CSystem.String%2CSystem.Text.RegularExpressions.RegexOptions%29?displayProperty=nameWithType> yöntemi, `options` öğesine ayarlanmış <xref:System.Text.RegularExpressions.RegexOptions.Multiline?displayProperty=nameWithType> parametresi ile çağrıldığında hiçbir eşleşme bulunmaz, çünkü normal ifade deseni satır başı öğesini (\u+000D) hesaba katmaz. Ancak, normal ifade deseni değiştirilerek `$` `\r?$`değiştirildiğinde, <xref:System.Text.RegularExpressions.Regex.Matches%28System.String%2CSystem.String%2CSystem.Text.RegularExpressions.RegexOptions%29?displayProperty=nameWithType> yöntemi `options` parametre ile <xref:System.Text.RegularExpressions.RegexOptions.Multiline?displayProperty=nameWithType> yeniden ayarlayarak beş eşleşme bulur.  
  
 [!code-csharp[Conceptual.RegEx.Language.Assertions#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.assertions/cs/endofstring1.cs#2)]
 [!code-vb[Conceptual.RegEx.Language.Assertions#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.assertions/vb/endofstring1.vb#2)]

## <a name="start-of-string-only-a"></a>Yalnızca Dize Başlangıcı: \A  
 Bağlantı, `\A` giriş dizesinin başında bir eşleşmenin oluşması gerektiğini belirtir. Seçeneği yok sayan `^` `\A` <xref:System.Text.RegularExpressions.RegexOptions.Multiline?displayProperty=nameWithType> sunucu dışında, çapa ile aynıdır. Bu nedenle, çok satırlı bir girdi dizesinde yalnızca ilk satırın başı ile eşleşebilir.  
  
 Aşağıdaki örnek, `^` ve `$` yer işaretlerine ait örnekler ile benzerdir. Bazı profesyonel `\A` beyzbol takımları var olduğu yıllar hakkında bilgi ayıklar düzenli bir ifade çapa kullanır. Giriş dizesi beş satır içerir. <xref:System.Text.RegularExpressions.Regex.Matches%28System.String%2CSystem.String%2CSystem.Text.RegularExpressions.RegexOptions%29?displayProperty=nameWithType> yöntemine yönelik çağrı yalnızca normal ifade deseni ile eşleşen girdi dizesindeki ilk alt dizeyi bulur. Örnekte gösterildiği gibi <xref:System.Text.RegularExpressions.RegexOptions.Multiline> seçeneğinin etkisi yoktur.  
  
 [!code-csharp[Conceptual.RegEx.Language.Assertions#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.assertions/cs/startofstring2.cs#3)]
 [!code-vb[Conceptual.RegEx.Language.Assertions#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.assertions/vb/startofstring2.vb#3)]

## <a name="end-of-string-or-before-ending-newline-z"></a>Dize Sonu veya Yeni Satır Sonlandırmadan Önce: \z  
 Bağlantı, `\Z` giriş dizesinin sonunda veya `\n` giriş dizesinin sonunda bir eşleşmenin oluşması gerektiğini belirtir. Seçeneği yok sayan `$` `\Z` <xref:System.Text.RegularExpressions.RegexOptions.Multiline?displayProperty=nameWithType> sunucu dışında, çapa ile aynıdır. Bu nedenle, çok satırlı bir dize, yalnızca son satırın sonu `\n`veya önceki son satır maç olabilir.  
  
 `\Z` Eşleştiğini `\n` ancak eşleşmediğini `\r\n` unutmayın (CR/LF karakter birleşimi). CR/LF ile eşleştirmek için normal ifade desenine ekleyin. `\r?\Z`  
  
 Aşağıdaki örnek, `\Z` bazı profesyonel beyzbol takımlarının var olduğu yıllar hakkında bilgi ayıklayan [Dize veya Satır Başlangıcı](#start-of-string-or-line-) bölümündeki örneğe benzer normal bir ifadede çapa kullanır. `\r?\Z` Normal ifadedeki `^((\w+(\s?)){2,}),\s(\w+\s\w+),(\s\d{4}(-(\d{4}|present))?,?)+\r?\Z` alt ifade, bir dize sonuyla eşleşir ve `\n` `\r\n`ayrıca bitiş isiyle veya . Sonuç olarak, dizideki her bir öğe normal ifade deseni ile eşleşir.  
  
 [!code-csharp[Conceptual.RegEx.Language.Assertions#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.assertions/cs/endofstring2.cs#4)]
 [!code-vb[Conceptual.RegEx.Language.Assertions#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.assertions/vb/endofstring2.vb#4)]

## <a name="end-of-string-only-z"></a>Yalnızca Dize Sonu: \z  
 Bağlantı, `\z` giriş dizesinin sonunda bir eşleşme nin oluşması gerektiğini belirtir. `$` Dil öğesi gibi, `\z` <xref:System.Text.RegularExpressions.RegexOptions.Multiline?displayProperty=nameWithType> seçeneği yok sayar. Dil `\Z` öğesinin `\z` aksine, bir `\n` dize sonundaki bir karakterle eşleşmez. Bu nedenle, yalnızca giriş dizesinin son satırı ile eşleşebilir.  
  
 Aşağıdaki örnek, `\z` çapayı, bazı profesyonel beyzbol takımlarının var olduğu yıllar hakkında bilgi ayıklayan önceki bölümdeki örnekle aynı olan normal bir ifadede kullanır. Örnek, bir dize dizisindeki beş öğenin her `^((\w+(\s?)){2,}),\s(\w+\s\w+),(\s\d{4}(-(\d{4}|present))?,?)+\r?\z`birini normal ifade deseniyle eşleştirmeye çalışır. Dizelerden ikisi satır başı ve satır besleme karakteri ile, bir tanesi satır besleme karakteri ile, iki tanesi ise ne satır başı ne de satır besleme karakteri ile biter. Çıktıda gösterildiği gibi yalnızca bir satır başı veya satır besleme karakteri olmayan dizeler desen ile eşleşir.  
  
 [!code-csharp[Conceptual.RegEx.Language.Assertions#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.assertions/cs/endofstring3.cs#5)]
 [!code-vb[Conceptual.RegEx.Language.Assertions#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.assertions/vb/endofstring3.vb#5)]

## <a name="contiguous-matches-g"></a>Bitişik Eşleştirmeler: \G  
 Bağlantı, `\G` bir eşleşmenin önceki eşleşmenin sona erdiği noktada gerçekleşmesi gerektiğini belirtir. Bu yer işaretini <xref:System.Text.RegularExpressions.Regex.Matches%2A?displayProperty=nameWithType> veya <xref:System.Text.RegularExpressions.Match.NextMatch%2A?displayProperty=nameWithType> yöntemi ile kullandığınızda tüm eşleşmelerin bitişik olmasını sağlar.  
  
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

## <a name="word-boundary-b"></a>Sözcük Sınırı: \b  
 Bağlantı, `\b` eşleşmenin bir sözcük karakteri `\w` (dil öğesi) ile sözcük dışı karakter `\W` (dil öğesi) arasındaki bir sınırda oluşması gerektiğini belirtir. Sözcük karakteri alfasayısal karakterler ve alt çizgilerden oluşur; sözcük olmayan bir karakter ise alfasayısal veya bir alt çizgi olmayan herhangi bir karakterdir. (Daha fazla bilgi için [Karakter Sınıfları'na](../../../docs/standard/base-types/character-classes-in-regular-expressions.md)bakın.) Eşleşme, dize başında veya sonunda bir sözcük sınırında da oluşabilir.  
  
 `\b` yer işareti genellikle bir alt ifadenin, bir sözcüğün yalnızca başlangıcı ya da bitişi yerine tüm sözcük ile eşleştiğinden emin olmak için kullanılır. Aşağıdaki örnekteki normal ifade `\bare\w*\b` bu kullanımı göstermektedir. "Olan" alt dizesi ile başlayan herhangi bir sözcüğü eşleştirir. Örneğin çıktısı ayrıca `\b` öğesinin, giriş dizesinin başlangıcı ve sonuyla eşleştiğini gösterir.  
  
 [!code-csharp[Conceptual.RegEx.Language.Assertions#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.assertions/cs/word1.cs#7)]
 [!code-vb[Conceptual.RegEx.Language.Assertions#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.assertions/vb/word1.vb#7)]  
  
 Normal ifade deseni aşağıdaki tabloda gösterildiği gibi yorumlanır.  
  
|Desen|Açıklama|  
|-------------|-----------------|  
|`\b`|Bir sözcük sınırında eşleşmeye başla.|  
|`are`|"Olan" alt dizesini eşleştirin.|  
|`\w*`|Sıfır veya daha fazla sözcük karakteriyle eşleş.|  
|`\b`|Eşlemeyi bir sözcük sınırında sonlandır.|  

## <a name="non-word-boundary-b"></a>Sözcük Olmayan Sınır: \B  
 Bağlantı, `\B` eşleşmenin sözcük sınırında oluşmaması gerektiğini belirtir. Bu, `\b` yer işaretinin tersidir.  
  
 Aşağıdaki örnekte, `\B` bir sözcükteki "qu" alt dizesinin oluşumlarını bulmak için çapa kullanır. Normal ifade `\Bqu\w+` deseni, bir sözcüğü başlatmayan ve sözcüğün sonuna kadar devam eden bir "qu" ile başlayan bir alt dizeyle eşleşir.  
  
 [!code-csharp[Conceptual.RegEx.Language.Assertions#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.assertions/cs/nonword1.cs#8)]
 [!code-vb[Conceptual.RegEx.Language.Assertions#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.assertions/vb/nonword1.vb#8)]  
  
 Normal ifade deseni aşağıdaki tabloda gösterildiği gibi yorumlanır.  
  
|Desen|Açıklama|  
|-------------|-----------------|  
|`\B`|Eşlemeyi bir sözcük sınırında başlatmayın.|  
|`qu`|"qu" alt dizesini eşleştirin.|  
|`\w+`|Bir veya daha fazla sözcük karakteri eşleştir.|  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Normal İfade Dili - Hızlı Başvuru](../../../docs/standard/base-types/regular-expression-language-quick-reference.md)
- [Normal İfade Seçenekleri](../../../docs/standard/base-types/regular-expression-options.md)
