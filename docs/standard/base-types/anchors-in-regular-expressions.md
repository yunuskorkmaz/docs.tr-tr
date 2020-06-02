---
title: .NET normal Ifadelerinde tutturucular
description: Normal ifade desenlerinde Tutturucuların nasıl kullanılacağını öğrenin.
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
ms.openlocfilehash: e86bae8a687e89acba9a0b713630b43809f081d1
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84290635"
---
# <a name="anchors-in-regular-expressions"></a>Normal İfadelerdeki Tutturucular
Tutturucular veya atomik sıfır Genişlik onayları, bir eşleşmenin gerçekleşmesi gereken dizede bir konum belirtin. Arama ifadenizde bir yer işareti kullandığınızda, normal ifade motoru dize veya harcama karakterleri boyunca ilerlemez; sadece belirtilen konumda bir eşleşme arar. Örneğin `^` , eşleşmenin bir satır veya dize başında başlaması gerektiğini belirtir. Bu nedenle `^http:` normal ifadesi, sadece bir satırın başında gerçekleştiğinde "http:" ile eşleşir. Aşağıdaki tabloda, .NET 'teki normal ifadeler tarafından desteklenen bağlantılar listelenmektedir.  
  
|Yer işareti|Description|  
|------------|-----------------|  
|`^`|Varsayılan olarak, eşleşme dizenin başlangıcında gerçekleşmelidir; çok satırlı modda, satırın başlangıcında gerçekleşmelidir. Daha fazla bilgi için bkz. [dize veya satır başlangıcı](#start-of-string-or-line-).|  
|`$`|Varsayılan olarak, eşleşme dizenin sonunda veya dizenin sonundan önce gerçekleşmelidir `\n` ; çok satırlı modda, satırın sonunda veya satırın sonunda yer almalıdır olması gerekir `\n` . Daha fazla bilgi için bkz. [dize veya satır sonu](#end-of-string-or-line-).|  
|`\A`|Eşleşme yalnızca dizenin başında gerçekleşmelidir (çok satır desteği yok). Daha fazla bilgi için bkz. [yalnızca dize başlangıcı](#start-of-string-only-a).|  
|`\Z`|Eşleşme, dizenin sonunda veya `\n` dizenin sonundaki önünde oluşmalıdır. Daha fazla bilgi için bkz. [dize sonu veya yeni satır](#end-of-string-or-before-ending-newline-z)sonu.|  
|`\z`|Eşleşme sadece dizenin sonunda gerçekleşmelidir. Daha fazla bilgi için bkz. [yalnızca dize sonu](#end-of-string-only-z).|  
|`\G`|Eşleşme önceki eşleşmenin sona erdiği konumda başlamalıdır. Daha fazla bilgi için bkz. [bitişik eşleşmeler](#contiguous-matches-g).|  
|`\b`|Eşleşme bir kelime sınırında gerçekleşmemelidir. Daha fazla bilgi için bkz. [sözcük sınırı](#word-boundary-b).|  
|`\B`|Eşleşme bir sözcük sınırında gerçekleşmemelidir. Daha fazla bilgi için bkz. [sözcük olmayan sınır](#non-word-boundary-b).|  

## <a name="start-of-string-or-line-"></a>Dize veya Satır Başlangıcı: ^  
 Varsayılan olarak, `^` tutturucu aşağıdaki düzenin dizenin ilk karakter konumunda başlaması gerektiğini belirtir. `^` <xref:System.Text.RegularExpressions.RegexOptions.Multiline?displayProperty=nameWithType> Seçeneğiyle kullanıyorsanız (bkz. [normal ifade seçenekleri](regular-expression-options.md)), eşleşme her satırın başlangıcında gerçekleşmelidir.  
  
 Aşağıdaki örnek, bazı profesyonel beysbol takımlarının var olduğu yıllar hakkındaki bilgiyi ayıklayan normal bir ifadedeki `^` yer işaretini kullanır. Örnek, <xref:System.Text.RegularExpressions.Regex.Matches%2A?displayProperty=nameWithType> yönteminin iki aşırı yüklemesini çağırır:  
  
- <xref:System.Text.RegularExpressions.Regex.Matches%28System.String%2CSystem.String%29> aşırı yüklemesine olan çağrı, yalnızca normal ifade deseni ile eşleşen girdi dizesindeki ilk alt dizeyi bulur.  
  
- <xref:System.Text.RegularExpressions.Regex.Matches%28System.String%2CSystem.String%2CSystem.Text.RegularExpressions.RegexOptions%29> öğesine ayarlı `options` parametresiyle birlikte <xref:System.Text.RegularExpressions.RegexOptions.Multiline?displayProperty=nameWithType> aşırı yüklemesine olan çağrı beş alt dizenin tümünü bulur.  
  
 [!code-csharp[Conceptual.RegEx.Language.Assertions#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.assertions/cs/startofstring1.cs#1)]
 [!code-vb[Conceptual.RegEx.Language.Assertions#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.assertions/vb/startofstring1.vb#1)]  
  
 Normal ifade deseninin, `^((\w+(\s?)){2,}),\s(\w+\s\w+),(\s\d{4}(-(\d{4}|present))?,?)+` Aşağıdaki tabloda gösterildiği gibi tanımlanmıştır.  
  
|Desen|Description|  
|-------------|-----------------|  
|`^`|Giriş dizesinin başında eşleşmeye başlayın (eğer yöntem <xref:System.Text.RegularExpressions.RegexOptions.Multiline?displayProperty=nameWithType> seçeneği ile çağrılırsa satırın başında).|  
|`((\w+(\s?)){2,}`|Bir ya da daha fazla sözcük karakterini, sıfıra veya en az iki kez bir boşluk ile eşleştirin. Bu ilk yakalama grubudur. Bu ifade Ayrıca ikinci ve üçüncü bir yakalama grubunu tanımlar: ikincisi yakalanan sözcükten oluşur ve üçüncü, yakalanan boşluk bilgisinden oluşur.|  
|`,\s`|Ardından bir boşluk karakteri gelen bir virgülü eşleştirin.|  
|`(\w+\s\w+)`|Ardından bir boşluk gelen ve ardından bir veya daha fazla sözcük karakteri gelen bir veya daha fazla sözcük karakterini eşleştirin. Bu dördüncü yakalama grubudur.|  
|`,`|Bir virgülü eşleştirin.|  
|`\s\d{4}`|Ardından dört ondalık basamak gelen bir boşluğu eşleştirin.|  
|<code>(-(\d{4}&#124;present))?</code>|Ardından dört ondalık basamak veya "var" dizesi gelen bir tirenin sıfır veya bir oluşumunu eşleştirin. Bu altıncı yakalama grubudur. Ayrıca yedinci bir yakalama grubunu içerir.|  
|`,?`|Bir virgülün sıfır veya bir oluşumunu eşleştirin.|  
|<code>(\s\d{4}(-(\d{4}&#124;present))?,?)+</code>|Aşağıdakilerin bir veya daha fazla oluşumunu eşleştirin: bir boşluk, dört ondalık basamak, ardından dört ondalık basamak veya "var" dizesi gelen bir tirenin sıfır veya bir oluşumu ve sıfır veya bir virgül. Bu beşinci yakalama grubudur.|

## <a name="end-of-string-or-line-"></a>Dize veya Satır Sonu: $  
 `$`Tutturucu, önceki düzenin giriş dizesinin sonunda veya giriş dizesinin sonundan önce gerçekleşmesi gerektiğini belirtir `\n` .  
  
 Eğer `$` öğesini <xref:System.Text.RegularExpressions.RegexOptions.Multiline?displayProperty=nameWithType> seçeneği ile birlikte kullanıyorsanız eşleşme aynı zamanda satırın sonunda da oluşabilir. `$` `\n` Bununla eşleşir ancak eşleşmez `\r\n` (satır başı ve yeni satır karakterlerinin veya CR/LF birleşimi). CR/LF karakter birleşimini eşleştirmek için `\r?$` normal ifade düzenine dahil edin.  
  
 Aşağıdaki örnek, `$` bağlayıcıyı [dize veya satır başlangıcı](#start-of-string-or-line-) bölümündeki örnekte kullanılan normal ifade düzenine ekler. Beş satırlık metin içeren özgün giriş dizesi ile kullanıldığında <xref:System.Text.RegularExpressions.Regex.Matches%28System.String%2CSystem.String%29?displayProperty=nameWithType> yöntemi bir eşleşme bulamaz, çünkü ilk satırın sonu `$` deseni ile eşleşmez. Özgün giriş dizesi bir dize dizisine bölündüğünde <xref:System.Text.RegularExpressions.Regex.Matches%28System.String%2CSystem.String%29?displayProperty=nameWithType> yöntemi beş satırının her birini eşlemede başarılı olur. <xref:System.Text.RegularExpressions.Regex.Matches%28System.String%2CSystem.String%2CSystem.Text.RegularExpressions.RegexOptions%29?displayProperty=nameWithType> yöntemi, `options` öğesine ayarlanmış <xref:System.Text.RegularExpressions.RegexOptions.Multiline?displayProperty=nameWithType> parametresi ile çağrıldığında hiçbir eşleşme bulunmaz, çünkü normal ifade deseni satır başı öğesini (\u+000D) hesaba katmaz. Ancak, normal ifade deseninin ile değiştirilerek değiştirildiği zaman `$` `\r?$` , <xref:System.Text.RegularExpressions.Regex.Matches%28System.String%2CSystem.String%2CSystem.Text.RegularExpressions.RegexOptions%29?displayProperty=nameWithType> `options` parametre ayarlanmış olarak parametresi, <xref:System.Text.RegularExpressions.RegexOptions.Multiline?displayProperty=nameWithType> beş eşleşme bulur.  
  
 [!code-csharp[Conceptual.RegEx.Language.Assertions#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.assertions/cs/endofstring1.cs#2)]
 [!code-vb[Conceptual.RegEx.Language.Assertions#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.assertions/vb/endofstring1.vb#2)]

## <a name="start-of-string-only-a"></a>Yalnızca Dize Başlangıcı: \A  
 `\A`Tutturucu, giriş dizesinin başlangıcında bir eşleşmenin gerçekleşmesi gerektiğini belirtir. Bu, bağlantı noktası ile aynıdır `^` , ancak `\A` seçeneği yok sayılır <xref:System.Text.RegularExpressions.RegexOptions.Multiline?displayProperty=nameWithType> . Bu nedenle, çok satırlı bir girdi dizesinde yalnızca ilk satırın başı ile eşleşebilir.  
  
 Aşağıdaki örnek, `^` ve `$` yer işaretlerine ait örnekler ile benzerdir. Bu, `\A` bir normal ifadede yer alan ve bazı profesyonel bebete ekiplerinin varolduğu yıllar hakkında bilgi çıkaran bir ifade kullanır. Giriş dizesi beş satır içerir. <xref:System.Text.RegularExpressions.Regex.Matches%28System.String%2CSystem.String%2CSystem.Text.RegularExpressions.RegexOptions%29?displayProperty=nameWithType> yöntemine yönelik çağrı yalnızca normal ifade deseni ile eşleşen girdi dizesindeki ilk alt dizeyi bulur. Örnekte gösterildiği gibi <xref:System.Text.RegularExpressions.RegexOptions.Multiline> seçeneğinin etkisi yoktur.  
  
 [!code-csharp[Conceptual.RegEx.Language.Assertions#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.assertions/cs/startofstring2.cs#3)]
 [!code-vb[Conceptual.RegEx.Language.Assertions#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.assertions/vb/startofstring2.vb#3)]

## <a name="end-of-string-or-before-ending-newline-z"></a>Dize Sonu veya Yeni Satır Sonlandırmadan Önce: \z  
 `\Z`Tutturucu, giriş dizesinin sonunda veya giriş dizesinin sonundaki bir eşleşmenin gerçekleşmesi gerektiğini belirtir `\n` . Bu, bağlantı noktası ile aynıdır `$` , ancak `\Z` seçeneği yok sayılır <xref:System.Text.RegularExpressions.RegexOptions.Multiline?displayProperty=nameWithType> . Bu nedenle, çok satırlı bir dizede, yalnızca son satırın sonu veya önceki son satır ile eşleşemez `\n` .  
  
 `\Z` `\n` Bununla eşleşir ancak EŞLEŞMEZ `\r\n` (CR/LF karakter birleşimi). CR/LF ile eşleştirmek için `\r?\Z` normal ifade düzenine dahil edin.  
  
 Aşağıdaki örnek, bazı profesyonel bebete `\Z` ekiplerinin varolduğu yıllar hakkında bilgi çıkaran, [dize veya satır başlangıcı](#start-of-string-or-line-) bölümündeki örneğe benzer bir normal ifadede yer alan bağlayıcıyı kullanır. `\r?\Z`Normal ifadedeki alt ifade `^((\w+(\s?)){2,}),\s(\w+\s\w+),(\s\d{4}(-(\d{4}|present))?,?)+\r?\Z` bir dizenin sonuyla eşleşir ve ayrıca veya ile biten bir dizeyle eşleşir `\n` `\r\n` . Sonuç olarak, dizideki her bir öğe normal ifade deseni ile eşleşir.  
  
 [!code-csharp[Conceptual.RegEx.Language.Assertions#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.assertions/cs/endofstring2.cs#4)]
 [!code-vb[Conceptual.RegEx.Language.Assertions#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.assertions/vb/endofstring2.vb#4)]

## <a name="end-of-string-only-z"></a>Yalnızca Dize Sonu: \z  
 `\z`Tutturucu, giriş dizesinin sonunda bir eşleşmenin gerçekleşmesi gerektiğini belirtir. `$`Language öğesi gibi, `\z` <xref:System.Text.RegularExpressions.RegexOptions.Multiline?displayProperty=nameWithType> seçeneğini yoksayar. `\Z`Language öğesinden farklı olarak, `\z` `\n` bir dizenin sonundaki karakterle eşleşmez. Bu nedenle, yalnızca giriş dizesinin son satırı ile eşleşebilir.  
  
 Aşağıdaki örnek, `\z` bir önceki bölümde yer alan Örneğin, bazı profesyonel bebete ekiplerinin varolduğu yıllar hakkında bilgi çıkaran bir normal ifadede yer alan bağlayıcıyı kullanır. Örnek, bir dize dizisindeki beş öğenin her birini normal ifade düzeniyle eşleştirmeye çalışır `^((\w+(\s?)){2,}),\s(\w+\s\w+),(\s\d{4}(-(\d{4}|present))?,?)+\r?\z` . Dizelerden ikisi satır başı ve satır besleme karakteri ile, bir tanesi satır besleme karakteri ile, iki tanesi ise ne satır başı ne de satır besleme karakteri ile biter. Çıktıda gösterildiği gibi yalnızca bir satır başı veya satır besleme karakteri olmayan dizeler desen ile eşleşir.  
  
 [!code-csharp[Conceptual.RegEx.Language.Assertions#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.assertions/cs/endofstring3.cs#5)]
 [!code-vb[Conceptual.RegEx.Language.Assertions#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.assertions/vb/endofstring3.vb#5)]

## <a name="contiguous-matches-g"></a>Bitişik Eşleştirmeler: \G  
 `\G`Tutturucu, bir eşleşmenin önceki eşleşmenin sona erdiği noktada gerçekleşmesi gerektiğini belirtir. Bu yer işaretini <xref:System.Text.RegularExpressions.Regex.Matches%2A?displayProperty=nameWithType> veya <xref:System.Text.RegularExpressions.Match.NextMatch%2A?displayProperty=nameWithType> yöntemi ile kullandığınızda tüm eşleşmelerin bitişik olmasını sağlar.  
  
 Aşağıdaki örnek rodent türlerinin adlarını virgülle ayrılmış dizeden çıkartmak için normal bir ifade kullanır.  
  
 [!code-csharp[Conceptual.RegEx.Language.Assertions#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.assertions/cs/contiguous1.cs#6)]
 [!code-vb[Conceptual.RegEx.Language.Assertions#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.assertions/vb/contiguous1.vb#6)]  
  
 Normal ifade `\G(\w+\s?\w*),?` Aşağıdaki tabloda gösterildiği gibi yorumlanır.  
  
|Desen|Description|  
|-------------|-----------------|  
|`\G`|Son eşleşmenin sona erdiği yerden başlayın.|  
|`\w+`|Bir veya daha fazla sözcük karakteri eşleştir.|  
|`\s?`|Sıfır veya bir boşluğu eşleştirin.|  
|`\w*`|Sıfır veya daha fazla sözcük karakteriyle eşleş.|  
|`(\w+\s?\w*)`|Ardından sıfır veya bir boşluk gelen ve ardından sıfır veya daha fazla sözcük karakteri gelen bir veya daha fazla sözcük karakterini eşleştirin. Bu ilk yakalama grubudur.|  
|`,?`|Sabit bir virgül karakterinin sıfır veya bir oluşumunu eşleştirin.|

## <a name="word-boundary-b"></a>Sözcük Sınırı: \b  
 `\b`Tutturucu, eşleşmenin bir sözcük karakteri ( `\w` Dil öğesi) ile bir sözcük olmayan karakter (dil öğesi) arasındaki bir sınır üzerinde gerçekleşmesi gerektiğini belirtir `\W` . Sözcük karakteri alfasayısal karakterler ve alt çizgilerden oluşur; sözcük olmayan bir karakter ise alfasayısal veya bir alt çizgi olmayan herhangi bir karakterdir. (Daha fazla bilgi için bkz. [karakter sınıfları](character-classes-in-regular-expressions.md).) Eşleşme, dizenin başındaki veya sonundaki bir sözcük sınırında de gerçekleşebilir.  
  
 `\b` yer işareti genellikle bir alt ifadenin, bir sözcüğün yalnızca başlangıcı ya da bitişi yerine tüm sözcük ile eşleştiğinden emin olmak için kullanılır. `\bare\w*\b`Aşağıdaki örnekteki normal ifade bu kullanımı göstermektedir. "Olan" alt dizesi ile başlayan herhangi bir sözcüğü eşleştirir. Örneğin çıktısı ayrıca `\b` öğesinin, giriş dizesinin başlangıcı ve sonuyla eşleştiğini gösterir.  
  
 [!code-csharp[Conceptual.RegEx.Language.Assertions#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.assertions/cs/word1.cs#7)]
 [!code-vb[Conceptual.RegEx.Language.Assertions#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.assertions/vb/word1.vb#7)]  
  
 Normal ifade deseni aşağıdaki tabloda gösterildiği gibi yorumlanır.  
  
|Desen|Description|  
|-------------|-----------------|  
|`\b`|Bir sözcük sınırında eşleşmeye başla.|  
|`are`|"Olan" alt dizesini eşleştirin.|  
|`\w*`|Sıfır veya daha fazla sözcük karakteriyle eşleş.|  
|`\b`|Eşlemeyi bir sözcük sınırında sonlandır.|  

## <a name="non-word-boundary-b"></a>Sözcük Olmayan Sınır: \B  
 `\B`Tutturucu, eşleşmenin bir sözcük sınırında gerçekleşmemelidir. Bu, `\b` yer işaretinin tersidir.  
  
 Aşağıdaki örnek, `\B` bir sözcükteki "qu" alt dize oluşumlarını bulmak için bağlayıcıyı kullanır. Normal ifade deseninin, bir `\Bqu\w+` kelime başlatmayan ve sözcüğün sonuna kadar devam eden bir "qu" ile başlayan bir alt dizeyle eşleşir.  
  
 [!code-csharp[Conceptual.RegEx.Language.Assertions#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.assertions/cs/nonword1.cs#8)]
 [!code-vb[Conceptual.RegEx.Language.Assertions#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.assertions/vb/nonword1.vb#8)]  
  
 Normal ifade deseni aşağıdaki tabloda gösterildiği gibi yorumlanır.  
  
|Desen|Description|  
|-------------|-----------------|  
|`\B`|Eşlemeyi bir sözcük sınırında başlatmayın.|  
|`qu`|"qu" alt dizesini eşleştirin.|  
|`\w+`|Bir veya daha fazla sözcük karakteri eşleştir.|  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Normal İfade Dili - Hızlı Başvuru](regular-expression-language-quick-reference.md)
- [Normal Ifade seçenekleri](regular-expression-options.md)
