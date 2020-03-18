---
title: Normal İfade Dili - Hızlı Başvuru
ms.date: 03/30/2017
ms.technology: dotnet-standard
f1_keywords:
- VS.RegularExpressionBuilder
helpviewer_keywords:
- regex cheat sheet
- parsing text with regular expressions, language elements
- searching with regular expressions, language elements
- pattern-matching with regular expressions, language elements
- regular expressions, language elements
- regular expressions [.NET Framework]
- cheat sheet
- .NET Framework regular expressions, language elements
ms.assetid: 930653a6-95d2-4697-9d5a-52d11bb6fd4c
ms.openlocfilehash: 8acf0886215c2d31f949e38401c4705ac9e2aef5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "77124318"
---
# <a name="regular-expression-language---quick-reference"></a>Normal İfade Dili - Hızlı Başvuru

Normal bir ifade, normal ifade motorunun giriş metninde eşleştirmeyi denediği bir desendir. Bir desen, bir veya daha çok karakter sabitinden, işleçlerden veya yapılardan oluşur. Kısa bir giriş için [bkz.](regular-expressions.md)

Bu hızlı başvurudaki her bölüm, normal ifadeleri tanımlamak için kullanabileceğiniz belirli bir karakter, işleç ve yapı kategorisini listeler.

Bu bilgileri, kolay başvuru için indirebileceğiniz ve yazdırabileceğiniz iki formatta da sağladık:

- [Word (.docx) formatında indirin](https://download.microsoft.com/download/D/2/4/D240EBF6-A9BA-4E4F-A63F-AEB6DA0B921C/Regular%20expressions%20quick%20reference.docx)
- [PDF (.pdf) formatında indirin](https://download.microsoft.com/download/D/2/4/D240EBF6-A9BA-4E4F-A63F-AEB6DA0B921C/Regular%20expressions%20quick%20reference.pdf)

## <a name="character-escapes"></a>Karakter Çıkışları

Normal bir ifadedeki ters eğik çizgi karakteri (\\) onu izleyen karakterin özel bir karakter olduğunu (aşağıdaki tabloda gösterildiği gibi) veya tam anlamıyla yorumlanması gerektiğini belirtir. Daha fazla bilgi için [Karakter Kaçışları'na](character-escapes-in-regular-expressions.md)bakın.

|Kaçan karakter|Açıklama|Desen|Eşleşmeler|
|-----------------------|-----------------|-------------|-------------|
|`\a`|Bir bell karakterle eşleşir, \u0007.|`\a`|`"Error!" + '\u0007'` içinde `"\u0007"`|
|`\b`|Bir karakter sınıfında, geri al tuşuyla eşleşir, \u0008.|`[\b]{3,}`|`"\b\b\b\b"` içinde `"\b\b\b\b"`|
|`\t`|Bir sekmeyle eşleşir, \u0009.|`(\w+)\t`|`"item1\t"`, `"item2\t"` içinde`"item1\titem2\t"`|
|`\r`|Bir satır başıyla eşleşir, \u000D. (`\r` yeni çizgi karakterine eşdeğer `\n`değildir,.)|`\r\n(\w+)`|`"\r\nThese are\ntwo lines."` içinde `"\r\nThese"`|
|`\v`|Bir dikey sekmeyle eşleşir, \u000B.|`[\v]{2,}`|`"\v\v\v"` içinde `"\v\v\v"`|
|`\f`|Form besleme ile eşleşir, \u000C.|`[\f]{2,}`|`"\f\f\f"` içinde `"\f\f\f"`|
|`\n`|Yeni bir satırla eşleşir, \u000A.|`\r\n(\w+)`|`"\r\nThese are\ntwo lines."` içinde `"\r\nThese"`|
|`\e`|Bir çıkışla eşleşir, \u001B.|`\e`|`"\x001B"` içinde `"\x001B"`|
|`\`*nnnn*|Bir karakter belirtmek için sekizli gösterimi kullanır *(nnn* iki veya üç basamaktan oluşur).|`\w\040\w`|`"a b"`, `"c d"` içinde`"a bc d"`|
|`\x`*nn*|Bir karakter belirtmek için hexadecimal gösterimi kullanır *(nn* tam olarak iki basamaktan oluşur).|`\w\x20\w`|`"a b"`, `"c d"` içinde`"a bc d"`|
|`\c` *X*<br /><br /> `\c`*x*|*X* veya *x'in* kontrol karakterinin harfi *olduğu* X veya *x*tarafından belirtilen ASCII kontrol karakteriyle eşleşir.|`\cC`|`"\x0003"`içinde `"\x0003"` (Ctrl-C)|
|`\u`*nnnnn*|Hexadecimal gösterimi *(nnnn*tarafından temsil edildiği gibi tam dört basamak) kullanarak unicode karakteri yle eşleşir.|`\w\u0020\w`|`"a b"`, `"c d"` içinde`"a bc d"`|
|`\`|Bu konudaki bu ve diğer tablolarda kaçış karakteri olarak tanınmayan bir karakterden önce geldiğinde karakterle eşleşir. Örneğin, `\*` `\x2A`aynı ' ve `\.` `\x2E`aynıdır . Bu normal ifade altyapısı dil öğeleri (gibi \* veya ?) ve karakter literals (tarafından temsil `\*` veya) `\?`disambiguate sağlar.|`\d+[\+-x\*]\d+`|`"(2+2) * 3*9"` içinde `"2+2"` ve `"3*9"`|

## <a name="character-classes"></a>Karakter Sınıfları

Bir karakter sınıfı, karakter kümelerinden herhangi biriyle eşleşir. Karakter sınıfları aşağıdaki tabloda listelenen dil öğelerini içerir: Daha fazla bilgi için [Karakter Sınıfları'na](character-classes-in-regular-expressions.md)bakın.

|Karakter sınıfı|Açıklama|Desen|Eşleşmeler|
|---------------------|-----------------|-------------|-------------|
|`[`*character_group*`]`|*character_group'daki*herhangi bir karakterle eşleşir. Varsayılan olarak, eşleşme büyük/küçük harf duyarlıdır.|`[ae]`|`"gray"` içinde `"a"`<br /><br /> `"a"`, `"e"` içinde`"lane"`|
|`[^`*character_group*`]`|Olumsuzlama: *character_group*olmayan herhangi bir tek karakterle eşleşir. Varsayılan olarak, *character_group'daki* karakterler büyük/küçük harf duyarlıdır.|`[^aei]`|`"r"`, `"g"` `"n"` içinde`"reign"`|
|`[`*ilk* `-` *son*`]`|Karakter aralığı: *Birinciden* *sona*kadar olan aralıktaki herhangi bir tek karakterle eşleşir.|`[A-Z]`|`"A"`, `"B"` içinde`"AB123"`|
|`.`|Joker karakter: \n dışında herhangi bir tek karakterle eşleşir.<br /><br /> Bir edebi dönem karakteri eşleştirmek için (. veya `\u002E`), kaçış karakteri ile önce`\.`gerekir ( ).|`a.e`|`"nave"` içinde `"ave"`<br /><br /> `"water"` içinde `"ate"`|
|`\p{`*isim*`}`|Unicode genel kategorisindeki veya *adla*belirtilen ad bloğundaki herhangi bir karakteri eşler.|`\p{Lu}`<br /><br /> `\p{IsCyrillic}`|`"C"`, `"L"` içinde`"City Lights"`<br /><br /> `"Д"`, `"Ж"` içinde`"ДЖem"`|
|`\P{`*isim*`}`|Unicode genel kategorisinde olmayan veya *adla*belirtilen blok adlı herhangi bir tek karakterle eşleşir.|`\P{Lu}`<br /><br /> `\P{IsCyrillic}`|`"i"`, `"t"` `"y"` içinde`"City"`<br /><br /> `"e"`, `"m"` içinde`"ДЖem"`|
|`\w`|Sözcük olan herhangi bir karakterle eşleşir.|`\w`|`"I"`, `"D"` `"A"`, `"1"` `"3"` , içinde`"ID A1.3"`|
|`\W`|Sözcük olmayan herhangi bir karakterle eşleşir.|`\W`|`" "`, `"."` içinde`"ID A1.3"`|
|`\s`|Boşluk olan herhangi bir karakterle eşleşir.|`\w\s`|`"ID A1.3"` içinde `"D "`|
|`\S`|Boşluk olmayan herhangi bir karakterle eşleşir.|`\s\S`|`"int __ctr"` içinde `" _"`|
|`\d`|Herhangi bir ondalık basamakla eşleşir.|`\d`|`"4 = IV"` içinde `"4"`|
|`\D`|Bir ondalık basamak dışında herhangi bir karakterle eşleşir.|`\D`|`" "`, `"="` `" "`, `"I"` `"V"` , içinde`"4 = IV"`|

## <a name="anchors"></a>Tutturucular

Yer işaretleri veya atomik sıfır genişlik onayları, dizedeki geçerli konuma bağlı olarak eşleşmenin başarılı veya başarısız olmasına neden olurlar, ancak altyapının dize boyunca ilerlemesine veya karakterleri tüketmesine neden olmazlar. Aşağıdaki tabloda listelenen meta karakterler tutturuculardır. Daha fazla bilgi için [Bkz. Çapalar.](anchors-in-regular-expressions.md)

|Onaylama işlemi|Açıklama|Desen|Eşleşmeler|
|---------------|-----------------|-------------|-------------|
|`^`|Varsayılan olarak, eşleşme dize başında başlamalıdır; çok satırlı modda, satırın başında başlamalıdır.|`^\d{3}`|`"901-333-"` içinde `"901"`|
|`$`|Varsayılan olarak, eşleşme dize sonunda veya dize sonunda önce `\n` oluşmalıdır; çok satırlı modda, satırın sonundan önce `\n` veya satırın sonundan önce gerçekleşmelidir.|`-\d{3}$`|`"-901-333"` içinde `"-333"`|
|`\A`|Eşleşme dizenin başlangıcında gerçekleşmelidir.|`\A\d{3}`|`"901-333-"` içinde `"901"`|
|`\Z`|Eşleşme, dize sonunda veya dize `\n` sonunda önce oluşmalıdır.|`-\d{3}\Z`|`"-901-333"` içinde `"-333"`|
|`\z`|Eşleşme dizenin sonunda gerçekleşmelidir.|`-\d{3}\z`|`"-901-333"` içinde `"-333"`|
|`\G`|Eşleşme önceki eşleşmenin sona erdiği noktada gerçekleşmelidir.|`\G\(\d\)`|`"(1)"`, `"(3)"` `"(5)"` içinde`"(1)(3)(5)[7](9)"`|
|`\b`|Eşleşme, bir `\w` (alfanümerik) ve (alfasayısal `\W` olmayan) karakter arasındaki bir sınırda gerçekleşmelidir.|`\b\w+\s\w+\b`|`"them theme"`, `"them them"` içinde`"them theme them them"`|
|`\B`|Eşleşme bir `\b` sınırda oluşmamalıdır.|`\Bend\w*\b`|`"ends"`, `"ender"` içinde`"end sends endure lender"`|

## <a name="grouping-constructs"></a>Gruplandırma Yapıları

Yapıları gruplandırma, normal bir ifadenin alt ifadelerini açıklar ve tipik olarak bir giriş dizesinin alt dizelerini yakalar. Yapıları gruplandırma aşağıdaki tabloda listelenen dil öğelerini içerir. Daha fazla bilgi için [yapıyı gruplandırma](grouping-constructs-in-regular-expressions.md)ya da gruplandırma'ya bakın.

|Yapıyı gruplandırma|Açıklama|Desen|Eşleşmeler|
|------------------------|-----------------|-------------|-------------|
|`(`*alt ifade*`)`|Eşleşen alt ifadeyi yakalar ve buna bir tabanlı bir sıra numarası atar.|`(\w)\1`|`"deep"` içinde `"ee"`|
|`(?<`*ad* `>` *alt ifadesi*`)`|Eşleşen alt ifadeyi adlandırılmış bir gruba yakalar.|`(?<double>\w)\k<double>`|`"deep"` içinde `"ee"`|
|`(?<`*name1* `-` *name2* `>` *alt ifade*`)`|Bir dengeleme grubu tanımını tanımlar. Daha fazla bilgi için, [Yapı gruplandırmabölümündeki](grouping-constructs-in-regular-expressions.md)"Dengeleme Grubu Tanımı" bölümüne bakın.|`(((?'Open'\()[^\(\)]*)+((?'Close-Open'\))[^\(\)]*)+)*(?(Open)(?!))$`|`"3+2^((1-3)*(3-1))"` içinde `"((1-3)*(3-1))"`|
|`(?:`*alt ifade*`)`|Yakalama yapmayan grubu tanımlar.|`Write(?:Line)?`|`"Console.WriteLine()"` içinde `"WriteLine"`<br /><br /> `"Console.Write(value)"` içinde `"Write"`|
|`(?imnsx-imnsx:`*alt ifade*`)`|*Alt ifade*de belirtilen seçenekleri uygular veya devre dışı kılabilir. Daha fazla bilgi için [Düzenli İfade Seçenekleri'ne](regular-expression-options.md)bakın.|`A\d{2}(?i:\w+)\b`|`"A12xl"`, `"A12XL"` içinde`"A12xl A12XL a12xl"`|
|`(?=`*alt ifade*`)`|Sıfır genişlik pozitif ileriye yönelik onaylar.|`\w+(?=\.)`|`"is"`, `"ran"`ve `"out"` içinde`"He is. The dog ran. The sun is out."`|
|`(?!`*alt ifade*`)`|Sıfır genişlik negatif ileriye yönelik onaylar.|`\b(?!un)\w+\b`|`"sure"`, `"used"` içinde`"unsure sure unity used"`|
|`(?<=`*alt ifade*`)`|Sıfır genişlik pozitif geriye yönelik onaylar.|`(?<=19)\d{2}\b`|`"99"`, `"50"` `"05"` içinde`"1851 1999 1950 1905 2003"`|
|`(?<!`*alt ifade*`)`|Sıfır genişlik negatif geriye yönelik onaylar.|`(?<!19)\d{2}\b`|`"51"`, `"03"` içinde`"1851 1999 1950 1905 2003"`|
|`(?>`*alt ifade*`)`|Atomik grup.|`[13579](?>A+B+)`|`"1ABB"`, `"3ABB"`ve `"5AB"` içinde`"1ABB 3ABBC 5AB 5AC"`|

## <a name="quantifiers"></a>Miktar Niceleyiciler

Niceleyici, önceki öğenin (karakter, grup veya karakter sınıfı olabilir) kaç örneğinin oluşacak eşleme için giriş dizesinde mevcut olması gerektiğini belirtir. Miktar niceleyiciler aşağıdaki tabloda listelenen dil öğelerini içerir. Daha fazla bilgi için, [bkz.](quantifiers-in-regular-expressions.md)

|Miktar Niceleyici|Açıklama|Desen|Eşleşmeler|
|----------------|-----------------|-------------|-------------|
|`*`|Önceki öğeyle sıfır kez veya daha fazla eşleşir.|`\d*\.\d`|`".0"`, `"19.9"`, `"219.9"`|
|`+`|Önceki öğeyle bir kez veya daha fazla eşleşir.|`"be+"`|`"bee"`in `"been"` `"be"` , in`"bent"`|
|`?`|Önceki öğeyle sıfır veya bir kez eşleşir.|`"rai?n"`|`"ran"`, `"rain"`|
|`{`*n*`}`|Önceki öğeyi tam olarak *n* kez eşleşir.|`",\d{3}"`|`",043"`içinde `"1,043.6"` `",876"`, `",543"`, `",210"` ve içinde`"9,876,543,210"`|
|`{`*n*`,}`|Önceki öğeyle en az *n* kez eşleşir.|`"\d{2,}"`|`"166"`, `"29"`, `"1930"`|
|`{`*n* `,` *m*`}`|Önceki öğeyi en az *n* kez eşler, ancak *m* kereden fazla değil.|`"\d{3,5}"`|`"166"`, `"17668"`<br /><br /> `"193024"` içinde `"19302"`|
|`*?`|Önceki öğeyle sıfır kez veya daha fazla ancak mümkün olduğunca az eşleşir.|`\d*?\.\d`|`".0"`, `"19.9"`, `"219.9"`|
|`+?`|Önceki öğeyle bir kez veya daha fazla ancak mümkün olduğunca az eşleşir.|`"be+?"`|`"be"`in `"been"` `"be"` , in`"bent"`|
|`??`|Önceki öğeyle sıfır veya bir kez ancak mümkün olduğunca az eşleşir.|`"rai??n"`|`"ran"`, `"rain"`|
|`{`*n*`}?`|Önceki öğeyi tam olarak *n* kez eşleşir.|`",\d{3}?"`|`",043"`içinde `"1,043.6"` `",876"`, `",543"`, `",210"` ve içinde`"9,876,543,210"`|
|`{`*n*`,}?`|Önceki öğeyi en az *n* kez, ancak mümkün olduğunca az kez eşleşir.|`"\d{2,}?"`|`"166"`, `"29"`, `"1930"`|
|`{`*n* `,` *m*`}?`|*N* ve *m* saatleri arasındaki önceki öğeyle eşleşir, ancak mümkün olduğunca az kez.|`"\d{3,5}?"`|`"166"`, `"17668"`<br /><br /> `"193"`, `"024"` içinde`"193024"`|

## <a name="backreference-constructs"></a>Yeniden Başvuru Yapıları

Yeniden başvuru, aynı normal ifadede daha sonra tanımlanabilecek alt ifadeyle daha önce eşleşmesine olanak sağlar. Aşağıdaki tabloda .NET'te normal ifadelerle desteklenen geri başvuru yapıları listelenir. Daha fazla bilgi için [Bkz. Backreference Yapıları.](backreference-constructs-in-regular-expressions.md)

|Yeniden başvuru yapısı|Açıklama|Desen|Eşleşmeler|
|-----------------------------|-----------------|-------------|-------------|
|`\` *number*|Yeniden başvuru. Numaralandırılmış ifadenin değeriyle eşleşir.|`(\w)\1`|`"seek"` içinde `"ee"`|
|`\k<`*isim*`>`|Adlandırılan yeniden başvuru. Adlandırılmış ifadenin değeriyle eşleşir.|`(?<char>\w)\k<char>`|`"seek"` içinde `"ee"`|

## <a name="alternation-constructs"></a>Değişim Yapıları

Değişim yapıları, ve/veya eşleştirmeyi etkinleştirmek üzere bir normal ifadeyi değiştirir. Bu yapılar aşağıdaki tabloda listelenen dil öğelerini içerir. Daha fazla bilgi için [alternation Constructs'a](alternation-constructs-in-regular-expressions.md)bakın.

|Değişim yapısı|Açıklama|Desen|Eşleşmeler|
|---------------------------|-----------------|-------------|-------------|
|<code>&#124;</code>|Dikey çubuk (<code>&#124;</code>) karakteriyle ayrılmış herhangi bir öğeyle eşleşir.|<code>th(e&#124;is&#124;at)</code>|`"the"`, `"this"` içinde`"this is the day."`|
|`(?(`*ifade* `)` *evet* <code>&#124;</code> *hayır*`)`|*İfade* yle belirlenen normal ifade deseni eşleşirse *evet* eşleşir; aksi takdirde, isteğe bağlı *hiçbir* bölümü eşleşir. *ifade* sıfır genişlikte bir iddia olarak yorumlanır.|<code>(?(A)A\d{2}\b&#124;\b\d{3}\b)</code>|`"A10"`, `"910"` içinde`"A10 C103 910"`|
|`(?(`*isim* `)` *evet* <code>&#124;</code> *hayır*`)`|Ad *,* adlandırılmış veya numaralandırılmış yakalama grubu, bir eşleşme varsa *evet* eşleşir; aksi takdirde, isteğe bağlı *hayır*eşleşir.|<code>(?&lt;quoted&gt;&quot;)?(?(quoted).+?&quot;&#124;\S+\s)</code>|`"Dogs.jpg "`, `"\"Yiska playing.jpg\""` içinde`"Dogs.jpg \"Yiska playing.jpg\""`|

## <a name="substitutions"></a>Değişimler

Değişimler değiştirme desenlerinde desteklenen normal ifade dil öğeleridir. Daha fazla bilgi için [Bkz.](substitutions-in-regular-expressions.md) Aşağıdaki tabloda listelenen meta karakterler atomik sıfır genişlik onaylarıdır.

|Karakter|Açıklama|Desen|Değiştirme deseni|Giriş dizesi|Sonuç Dizesi|
|---------------|-----------------|-------------|-------------------------|------------------|-------------------|
|`$` *number*|Grup *numarasıyla*eşleşen alt dizeyi yerine alır.|`\b(\w+)(\s)(\w+)\b`|`$3$2$1`|`"one two"`|`"two one"`|
|`${`*isim*`}`|Adlandırılmış grup *adı*ile eşleşen alt dize yerine.|`\b(?<word1>\w+)(\s)(?<word2>\w+)\b`|`${word2} ${word1}`|`"one two"`|`"two one"`|
|`$$`|Değişmez değerli bir "$" işaretinin yerini alır.|`\b(\d+)\s?USD`|`$$$1`|`"103 USD"`|`"$103"`|
|`$&`|Tam eşleşmenin bir kopyasının yerini alır.|`\$?\d*\.?\d+`|`**$&**`|`"$1.30"`|`"**$1.30**"`|
|``$` ``|Eşleşmeden önce giriş dizesi metninin tamamının yerini alır.|`B+`|``$` ``|`"AABBCC"`|`"AAAACC"`|
|`$'`|Eşleşmeden sonra giriş dizesi metninin tamamının yerini alır.|`B+`|`$'`|`"AABBCC"`|`"AACCCC"`|
|`$+`|Yakalanan son grubun yerini alır.|`B+(C+)`|`$+`|`"AABBCCDD"`|`"AACCDD"`|
|`$_`|Giriş dizesinin tamamının yerini alır.|`B+`|`$_`|`"AABBCC"`|`"AAAABBCCCC"`|

## <a name="regular-expression-options"></a>Normal İfade Seçenekleri

Normal ifade sisteminin normal ifade modellerini nasıl denetleyeceğiyle ilgili seçenekler belirtebilirsiniz. Bu seçeneklerin çoğu satır içinde (normal ifade deseni) veya <xref:System.Text.RegularExpressions.RegexOptions> bir veya daha fazla sabit olarak belirtilebilir. Bu hızlı başvuru yalnızca satır içi seçeneklerini listeler. Satır çizgisi ve <xref:System.Text.RegularExpressions.RegexOptions> seçenekler hakkında daha fazla bilgi için Düzenli İfade [Seçenekleri](regular-expression-options.md)makalesine bakın.

Satır içi seçeneği iki şekilde belirtebilirsiniz:

- Bir seçenek veya seçenek kümesi bu seçenekleri kapatmadan önce eksi işareti (-) çeşitli [yapı](miscellaneous-constructs-in-regular-expressions.md) `(?imnsx-imnsx)`kullanarak. Örneğin, `(?i-mn)` büyük/küçük harf duyarsız`i`eşlemi ( )`m`açar, çok satırlı modu`n`( ) kapatır ve adsız grup yakalamalarını ( ) kapatır. Seçenek, seçeneğin tanımlandığı noktadan itibaren normal ifade deseni için geçerlidir ve desenin sonuna kadar ya da bir başka yapının seçeneği tersine çevirdiği noktaya kadar etkilidir.
- Yalnızca belirtilen grup için seçenekleri tanımlayan yapı*alt ifadesini*`)` [gruplandırma](grouping-constructs-in-regular-expressions.md)`(?imnsx-imnsx:`yı kullanarak.

.NET normal ifade altyapısı aşağıdaki satır satır seçeneklerini destekler:

|Seçenek|Açıklama|Desen|Eşleşmeler|
|------------|-----------------|-------------|-------------|
|`i`|Büyük küçük harf duyarlı eşleme kullanın.|`\b(?i)a(?-i)a\w+\b`|`"aardvark"`, `"aaaAuto"` içinde`"aardvark AAAuto aaaAuto Adam breakfast"`|
|`m`|Çok satırlı modunu kullanın. `^`ve `$` bir dize başlangıcı ve sonu yerine bir satırın başlangıcı ve sonu maç.|Örneğin, [Normal İfade Seçenekleri'ndeki](regular-expression-options.md)"Çok Satırlı Mod" bölümüne bakın.||
|`n`|Adsız grupları yakalamayın.|Örneğin, [Normal İfade Seçenekleri'ndeki](regular-expression-options.md)"Yalnızca Açık Yakalamalar" bölümüne bakın.||
|`s`|Tek satır modunu kullanın.|Örneğin, [Normal İfade Seçenekleri'ndeki](regular-expression-options.md)"Tek Satırlı Mod" bölümüne bakın.||
|`x`|Normal ifade deseninde kaçışsız boşluğu yoksay.|`\b(?x) \d+ \s \w+`|`"1 aardvark"`, `"2 cats"` içinde`"1 aardvark 2 cats IV centurions"`|

## <a name="miscellaneous-constructs"></a>Çeşitli Yapılar

Çeşitli yapılar, bir normal ifade desenini değiştirir veya bununla ilgili bilgi sağlar. Aşağıdaki tabloda .NET tarafından desteklenen çeşitli yapılar listelenir. Daha fazla bilgi için [bkz.](miscellaneous-constructs-in-regular-expressions.md)

|Oluştur|Tanım|Örnek|
|---------------|----------------|-------------|
|`(?imnsx-imnsx)`|Desen ortasında büyük/küçük harf duyarsızlığı gibi seçenekleri ayarlar veya devre dışı kayırır. Daha fazla bilgi için [Düzenli İfade Seçenekleri'ne](regular-expression-options.md)bakın.|`\bA(?i)b\w+\b`maçlar `"ABA"` `"Able"` , içinde`"ABA Able Act"`|
|`(?#`*yorum yapın*`)`|Satır içi açıklama. Açıklama ilk kapanış parantezinde sona erer.|`\bA(?#Matches words starting with A)\w+\b`|
|`#`[satır sonuna kadar]|X-mode yorumu. Yorum bir unescape `#` başlar ve satırSonuna kadar devam ediyor.|`(?x)\bA\w+\b#Matches words starting with A`|

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Text.RegularExpressions?displayProperty=nameWithType>
- <xref:System.Text.RegularExpressions.Regex?displayProperty=nameWithType>
- [Düzenli İfadeler](regular-expressions.md)
- [Normal İfade Sınıfları](the-regular-expression-object-model.md)
- [Normal İfade Örnekleri](regular-expression-examples.md)
- [Normal İfadeler - Hızlı Başvuru (Word formatında indir)](https://download.microsoft.com/download/D/2/4/D240EBF6-A9BA-4E4F-A63F-AEB6DA0B921C/Regular%20expressions%20quick%20reference.docx)
- [Normal İfadeler - Hızlı Başvuru (PDF formatında indir)](https://download.microsoft.com/download/D/2/4/D240EBF6-A9BA-4E4F-A63F-AEB6DA0B921C/Regular%20expressions%20quick%20reference.pdf)
