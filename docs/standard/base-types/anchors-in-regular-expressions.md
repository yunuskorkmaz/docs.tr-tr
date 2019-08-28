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
author: rpetrusha
ms.author: ronpet
ms.custom: seodec18
ms.openlocfilehash: 5f722977928604e5876e52a7329eef5c933bf2a7
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/27/2019
ms.locfileid: "70046466"
---
# <a name="anchors-in-regular-expressions"></a>Normal İfadelerdeki Tutturucular
<a name="top"></a>Tutturucular veya atomik sıfır Genişlik onayları, bir eşleşmenin gerçekleşmesi gereken dizede bir konum belirtin. Arama ifadenizde bir yer işareti kullandığınızda, normal ifade motoru dize veya harcama karakterleri boyunca ilerlemez; sadece belirtilen konumda bir eşleşme arar. Örneğin `^` , eşleşmenin bir satır veya dize başında başlaması gerektiğini belirtir. Bu nedenle `^http:` normal ifadesi, sadece bir satırın başında gerçekleştiğinde "http:" ile eşleşir. Aşağıdaki tabloda, .NET 'teki normal ifadeler tarafından desteklenen bağlantılar listelenmektedir.  
  
|Yer işareti|Açıklama|  
|------------|-----------------|  
|`^`|Varsayılan olarak, eşleşme dizenin başlangıcında gerçekleşmelidir; çok satırlı modda, satırın başlangıcında gerçekleşmelidir. Daha fazla bilgi için bkz. [dize veya satır başlangıcı](#Start).|  
|`$`|Varsayılan olarak, eşleşme dizenin sonunda veya dizenin sonundan önce `\n` gerçekleşmelidir; çok satırlı modda, satırın sonunda `\n` veya satırın sonunda yer almalıdır olması gerekir. Daha fazla bilgi için bkz. [dize veya satır sonu](#End).|  
|`\A`|Eşleşme yalnızca dizenin başında gerçekleşmelidir (çok satır desteği yok). Daha fazla bilgi için bkz. [yalnızca dize başlangıcı](#StartOnly).|  
|`\Z`|Eşleşme, dizenin sonunda veya dizenin sonundaki önünde `\n` oluşmalıdır. Daha fazla bilgi için bkz. [dize sonu veya yeni satır](#EndOrNOnly)sonu.|  
|`\z`|Eşleşme sadece dizenin sonunda gerçekleşmelidir. Daha fazla bilgi için bkz. [yalnızca dize sonu](#EndOnly).|  
|`\G`|Eşleşme önceki eşleşmenin sona erdiği konumda başlamalıdır. Daha fazla bilgi için bkz. [bitişik eşleşmeler](#Contiguous).|  
|`\b`|Eşleşme bir kelime sınırında gerçekleşmemelidir. Daha fazla bilgi için bkz. [sözcük sınırı](#WordBoundary).|  
|`\B`|Eşleşme bir sözcük sınırında gerçekleşmemelidir. Daha fazla bilgi için bkz. [sözcük olmayan sınır](#NonwordBoundary).|  
  
<a name="Start"></a>   
## <a name="start-of-string-or-line-"></a>Dize veya Satır Başlangıcı: ^  
 Varsayılan olarak, `^` tutturucu aşağıdaki düzenin dizenin ilk karakter konumunda başlaması gerektiğini belirtir. Seçeneğiyle<xref:System.Text.RegularExpressions.RegexOptions.Multiline?displayProperty=nameWithType> kullanıyorsanız `^` (bkz. [normal ifade seçenekleri](../../../docs/standard/base-types/regular-expression-options.md)), eşleşme her satırın başlangıcında gerçekleşmelidir.  
  
 Aşağıdaki örnek, bazı profesyonel beysbol takımlarının var olduğu yıllar hakkındaki bilgiyi ayıklayan normal bir ifadedeki `^` yer işaretini kullanır. Örnek, <xref:System.Text.RegularExpressions.Regex.Matches%2A?displayProperty=nameWithType> yönteminin iki aşırı yüklemesini çağırır:  
  
- <xref:System.Text.RegularExpressions.Regex.Matches%28System.String%2CSystem.String%29> aşırı yüklemesine olan çağrı, yalnızca normal ifade deseni ile eşleşen girdi dizesindeki ilk alt dizeyi bulur.  
  
- <xref:System.Text.RegularExpressions.Regex.Matches%28System.String%2CSystem.String%2CSystem.Text.RegularExpressions.RegexOptions%29> öğesine ayarlı `options` parametresiyle birlikte <xref:System.Text.RegularExpressions.RegexOptions.Multiline?displayProperty=nameWithType> aşırı yüklemesine olan çağrı beş alt dizenin tümünü bulur.  
  
 [!code-csharp[Conceptual.RegEx.Language.Assertions#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.assertions/cs/startofstring1.cs#1)]
 [!code-vb[Conceptual.RegEx.Language.Assertions#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.assertions/vb/startofstring1.vb#1)]  
  
 Normal ifade deseninin `^((\w+(\s?)){2,}),\s(\w+\s\w+),(\s\d{4}(-(\d{4}|present))?,?)+` , aşağıdaki tabloda gösterildiği gibi tanımlanmıştır.  
  
|Desen|Açıklama|  
|-------------|-----------------|  
|`^`|Giriş dizesinin başında eşleşmeye başlayın (eğer yöntem <xref:System.Text.RegularExpressions.RegexOptions.Multiline?displayProperty=nameWithType> seçeneği ile çağrılırsa satırın başında).|  
|`((\w+(\s?)){2,}`|Bir ya da daha fazla sözcük karakterini, sıfıra veya en az iki kez bir boşluk ile eşleştirin. Bu ilk yakalama grubudur. Bu ifade Ayrıca ikinci ve üçüncü bir yakalama grubunu tanımlar: İkincisi yakalanan sözcükten oluşur ve üçüncü, yakalanan boşluk bilgisinden oluşur.|  
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
 Tutturucu, önceki düzenin giriş dizesinin sonunda veya giriş dizesinin sonundan önce `\n` gerçekleşmesi gerektiğini belirtir. `$`  
  
 Eğer `$` öğesini <xref:System.Text.RegularExpressions.RegexOptions.Multiline?displayProperty=nameWithType> seçeneği ile birlikte kullanıyorsanız eşleşme aynı zamanda satırın sonunda da oluşabilir. `$` Bununla eşleşir `\n` ancak eşleşmez`\r\n` (satır başı ve yeni satır karakterlerinin veya CR/LF birleşimi). CR/LF karakter birleşimini eşleştirmek için normal ifade düzenine `\r?$` dahil edin.  
  
 Aşağıdaki örnek, `$` bağlayıcıyı [dize veya satır başlangıcı](#Start) bölümündeki örnekte kullanılan normal ifade düzenine ekler. Beş satırlık metin içeren özgün giriş dizesi ile kullanıldığında <xref:System.Text.RegularExpressions.Regex.Matches%28System.String%2CSystem.String%29?displayProperty=nameWithType> yöntemi bir eşleşme bulamaz, çünkü ilk satırın sonu `$` deseni ile eşleşmez. Özgün giriş dizesi bir dize dizisine bölündüğünde <xref:System.Text.RegularExpressions.Regex.Matches%28System.String%2CSystem.String%29?displayProperty=nameWithType> yöntemi beş satırının her birini eşlemede başarılı olur. <xref:System.Text.RegularExpressions.Regex.Matches%28System.String%2CSystem.String%2CSystem.Text.RegularExpressions.RegexOptions%29?displayProperty=nameWithType> yöntemi, `options` öğesine ayarlanmış <xref:System.Text.RegularExpressions.RegexOptions.Multiline?displayProperty=nameWithType> parametresi ile çağrıldığında hiçbir eşleşme bulunmaz, çünkü normal ifade deseni satır başı öğesini (\u+000D) hesaba katmaz. Ancak, normal ifade `$` deseninin ile `\r?$`değiştirilerek değiştirildiği zaman, <xref:System.Text.RegularExpressions.Regex.Matches%28System.String%2CSystem.String%2CSystem.Text.RegularExpressions.RegexOptions%29?displayProperty=nameWithType> `options` parametre ayarlanmış <xref:System.Text.RegularExpressions.RegexOptions.Multiline?displayProperty=nameWithType> olarak parametresi, beş eşleşme bulur.  
  
 [!code-csharp[Conceptual.RegEx.Language.Assertions#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.assertions/cs/endofstring1.cs#2)]
 [!code-vb[Conceptual.RegEx.Language.Assertions#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.assertions/vb/endofstring1.vb#2)]  
  
 [Başa dön](#top)  
  
<a name="StartOnly"></a>   
## <a name="start-of-string-only-a"></a>Yalnızca Dize Başlangıcı: \A  
 `\A` Tutturucu, giriş dizesinin başlangıcında bir eşleşmenin gerçekleşmesi gerektiğini belirtir. Bu, `^` bağlantı noktası ile aynıdır, `\A` ancak <xref:System.Text.RegularExpressions.RegexOptions.Multiline?displayProperty=nameWithType> seçeneği yok sayılır. Bu nedenle, çok satırlı bir girdi dizesinde yalnızca ilk satırın başı ile eşleşebilir.  
  
 Aşağıdaki örnek, `^` ve `$` yer işaretlerine ait örnekler ile benzerdir. Bu, `\A` bir normal ifadede yer alan ve bazı profesyonel bebete ekiplerinin varolduğu yıllar hakkında bilgi çıkaran bir ifade kullanır. Giriş dizesi beş satır içerir. <xref:System.Text.RegularExpressions.Regex.Matches%28System.String%2CSystem.String%2CSystem.Text.RegularExpressions.RegexOptions%29?displayProperty=nameWithType> yöntemine yönelik çağrı yalnızca normal ifade deseni ile eşleşen girdi dizesindeki ilk alt dizeyi bulur. Örnekte gösterildiği gibi <xref:System.Text.RegularExpressions.RegexOptions.Multiline> seçeneğinin etkisi yoktur.  
  
 [!code-csharp[Conceptual.RegEx.Language.Assertions#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.assertions/cs/startofstring2.cs#3)]
 [!code-vb[Conceptual.RegEx.Language.Assertions#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.assertions/vb/startofstring2.vb#3)]  
  
 [Başa dön](#top)  
  
<a name="EndOrNOnly"></a>   
## <a name="end-of-string-or-before-ending-newline-z"></a>Dize Sonu veya Yeni Satır Sonlandırmadan Önce: \z  
 Tutturucu, giriş dizesinin sonunda `\n` veya giriş dizesinin sonundaki bir eşleşmenin gerçekleşmesi gerektiğini belirtir. `\Z` Bu, `$` bağlantı noktası ile aynıdır, `\Z` ancak <xref:System.Text.RegularExpressions.RegexOptions.Multiline?displayProperty=nameWithType> seçeneği yok sayılır. Bu nedenle, çok satırlı bir dizede, yalnızca son satırın sonu veya önceki `\n`son satır ile eşleşemez.  
  
 `\Z` Bununla eşleşir `\n` ancak eşleşmez`\r\n` (CR/LF karakter birleşimi). CR/LF ile eşleştirmek için normal `\r?\Z` ifade düzenine dahil edin.  
  
 Aşağıdaki örnek, bazı profesyonel `\Z` bebete ekiplerinin varolduğu yıllar hakkında bilgi çıkaran, [dize veya satır başlangıcı](#Start) bölümündeki örneğe benzer bir normal ifadede yer alan bağlayıcıyı kullanır. Normal ifadedeki `\r?\Z` `^((\w+(\s?)){2,}),\s(\w+\s\w+),(\s\d{4}(-(\d{4}|present))?,?)+\r?\Z` alt ifade bir dizenin sonuyla eşleşir ve ayrıca veya `\r\n`ile `\n` biten bir dizeyle eşleşir. Sonuç olarak, dizideki her bir öğe normal ifade deseni ile eşleşir.  
  
 [!code-csharp[Conceptual.RegEx.Language.Assertions#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.assertions/cs/endofstring2.cs#4)]
 [!code-vb[Conceptual.RegEx.Language.Assertions#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.assertions/vb/endofstring2.vb#4)]  
  
 [Başa dön](#top)  
  
<a name="EndOnly"></a>   
## <a name="end-of-string-only-z"></a>Yalnızca Dize Sonu: \z  
 `\z` Tutturucu, giriş dizesinin sonunda bir eşleşmenin gerçekleşmesi gerektiğini belirtir. Language öğesi gibi, `\z` <xref:System.Text.RegularExpressions.RegexOptions.Multiline?displayProperty=nameWithType> seçeneğini yoksayar. `$` Language öğesinden farklı olarak, `\z` bir dizenin sonundaki `\n` karakterle eşleşmez. `\Z` Bu nedenle, yalnızca giriş dizesinin son satırı ile eşleşebilir.  
  
 Aşağıdaki örnek, bir önceki `\z` bölümde yer alan Örneğin, bazı profesyonel bebete ekiplerinin varolduğu yıllar hakkında bilgi çıkaran bir normal ifadede yer alan bağlayıcıyı kullanır. Örnek, bir dize dizisindeki beş öğenin her birini normal ifade düzeniyle `^((\w+(\s?)){2,}),\s(\w+\s\w+),(\s\d{4}(-(\d{4}|present))?,?)+\r?\z`eşleştirmeye çalışır. Dizelerden ikisi satır başı ve satır besleme karakteri ile, bir tanesi satır besleme karakteri ile, iki tanesi ise ne satır başı ne de satır besleme karakteri ile biter. Çıktıda gösterildiği gibi yalnızca bir satır başı veya satır besleme karakteri olmayan dizeler desen ile eşleşir.  
  
 [!code-csharp[Conceptual.RegEx.Language.Assertions#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.assertions/cs/endofstring3.cs#5)]
 [!code-vb[Conceptual.RegEx.Language.Assertions#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.assertions/vb/endofstring3.vb#5)]  
  
 [Başa dön](#top)  
  
<a name="Contiguous"></a>   
## <a name="contiguous-matches-g"></a>Bitişik Eşleştirmeler: \G  
 `\G` Tutturucu, bir eşleşmenin önceki eşleşmenin sona erdiği noktada gerçekleşmesi gerektiğini belirtir. Bu yer işaretini <xref:System.Text.RegularExpressions.Regex.Matches%2A?displayProperty=nameWithType> veya <xref:System.Text.RegularExpressions.Match.NextMatch%2A?displayProperty=nameWithType> yöntemi ile kullandığınızda tüm eşleşmelerin bitişik olmasını sağlar.  
  
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
 Tutturucu, eşleşmenin bir sözcük karakteri `\w` (dil öğesi) ile bir sözcük olmayan karakter ( `\W` dil öğesi) arasındaki bir sınır üzerinde gerçekleşmesi gerektiğini belirtir. `\b` Sözcük karakteri alfasayısal karakterler ve alt çizgilerden oluşur; sözcük olmayan bir karakter ise alfasayısal veya bir alt çizgi olmayan herhangi bir karakterdir. (Daha fazla bilgi için bkz. [karakter sınıfları](../../../docs/standard/base-types/character-classes-in-regular-expressions.md).) Eşleşme aynı zamanda dizenin başı veya sonundaki bir sözcük sınırında da oluşabilir.  
  
 `\b` yer işareti genellikle bir alt ifadenin, bir sözcüğün yalnızca başlangıcı ya da bitişi yerine tüm sözcük ile eşleştiğinden emin olmak için kullanılır. Aşağıdaki örnekteki normal `\bare\w*\b` ifade bu kullanımı göstermektedir. "Olan" alt dizesi ile başlayan herhangi bir sözcüğü eşleştirir. Örneğin çıktısı ayrıca `\b` öğesinin, giriş dizesinin başlangıcı ve sonuyla eşleştiğini gösterir.  
  
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
 `\B` Tutturucu, eşleşmenin bir sözcük sınırında gerçekleşmemelidir. Bu, `\b` yer işaretinin tersidir.  
  
 Aşağıdaki örnek, bir sözcükteki "qu" alt dize oluşumlarını bulmak için `\B` bağlayıcıyı kullanır. Normal ifade deseninin `\Bqu\w+` , bir kelime başlatmayan ve sözcüğün sonuna kadar devam eden bir "qu" ile başlayan bir alt dizeyle eşleşir.  
  
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
