---
title: Normal İfade Dili - Hızlı Başvuru
description: Bu hızlı başvuru bölümünde, giriş metnini eşleştirmek için normal ifade desenleri kullanmayı öğrenin. Bir düzende bir veya daha fazla karakter sabit değeri, işleç veya yapı bulunur.
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
ms.openlocfilehash: a2fc2c56eeb29f5e89dc0b9f94636408ff10700f
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/05/2020
ms.locfileid: "84446372"
---
# <a name="regular-expression-language---quick-reference"></a>Normal İfade Dili - Hızlı Başvuru

Normal bir ifade, normal ifade motorunun giriş metninde eşleştirmeyi denediği bir desendir. Bir desen, bir veya daha çok karakter sabitinden, işleçlerden veya yapılardan oluşur. Kısa bir giriş için bkz. [.net normal ifadeler](regular-expressions.md).

Bu hızlı başvurudaki her bölüm normal ifadeleri tanımlamak için kullanabileceğiniz belirli bir karakter, işleç ve Yapı kategorisini listeler.

Ayrıca, bu bilgileri kolay başvuru için indirebileceğiniz ve yazdırabileceğiniz iki biçimde sunuyoruz:

- [Word (. docx) biçiminde indir](https://download.microsoft.com/download/D/2/4/D240EBF6-A9BA-4E4F-A63F-AEB6DA0B921C/Regular%20expressions%20quick%20reference.docx)
- [PDF (. PDF) biçiminde indir](https://download.microsoft.com/download/D/2/4/D240EBF6-A9BA-4E4F-A63F-AEB6DA0B921C/Regular%20expressions%20quick%20reference.pdf)

## <a name="character-escapes"></a>Karakter Çıkışları

Bir normal ifadede ters eğik çizgi karakteri ( \\ ), kendisini izleyen karakterin özel bir karakter olduğunu (aşağıdaki tabloda gösterildiği gibi) veya tam olarak yorumlanması gerektiğini gösterir. Daha fazla bilgi için bkz. [karakter kaçışları](character-escapes-in-regular-expressions.md).

|Kaçan karakter|Açıklama|Desen|Eşleşmeler|
|-----------------------|-----------------|-------------|-------------|
|`\a`|Bir bell karakterle eşleşir, \u0007.|`\a`|`"Error!" + '\u0007'` içinde `"\u0007"`|
|`\b`|Bir karakter sınıfında, geri al tuşuyla eşleşir, \u0008.|`[\b]{3,}`|`"\b\b\b\b"` içinde `"\b\b\b\b"`|
|`\t`|Bir sekmeyle eşleşir, \u0009.|`(\w+)\t`|`"item1\t"``"item2\t"`içinde,`"item1\titem2\t"`|
|`\r`|Bir satır başıyla eşleşir, \u000D. ( `\r` yeni satır karakteri ile eşdeğer değildir `\n` .)|`\r\n(\w+)`|`"\r\nThese are\ntwo lines."` içinde `"\r\nThese"`|
|`\v`|Bir dikey sekmeyle eşleşir, \u000B.|`[\v]{2,}`|`"\v\v\v"` içinde `"\v\v\v"`|
|`\f`|Form besleme ile eşleşir, \u000C.|`[\f]{2,}`|`"\f\f\f"` içinde `"\f\f\f"`|
|`\n`|Yeni bir satırla eşleşir, \u000A.|`\r\n(\w+)`|`"\r\nThese are\ntwo lines."` içinde `"\r\nThese"`|
|`\e`|Bir çıkışla eşleşir, \u001B.|`\e`|`"\x001B"` içinde `"\x001B"`|
|`\`*nnn*|Bir karakter belirtmek için sekizlik gösterim kullanır (*nnn* iki veya üç basamaktan oluşur).|`\w\040\w`|`"a b"``"c d"`içinde,`"a bc d"`|
|`\x`*nn*|Bir karakter belirtmek için onaltılık gösterim kullanır (*nn* tam olarak iki basamak içerir).|`\w\x20\w`|`"a b"``"c d"`içinde,`"a bc d"`|
|`\c` *X*<br /><br /> `\c` *x*|X *veya x tarafından BELIRTILEN* ASCII denetim karakteriyle *eşleşir; burada* *x* veya *x* , denetim karakterinin harfidir.|`\cC`|`"\x0003"`içinde `"\x0003"` (CTRL-C)|
|`\u`*nnnn*|Onaltılık gösterim kullanarak bir Unicode karakteriyle eşleşir ( *nnnn*ile gösterildiği gibi, tam olarak dört basamaklı).|`\w\u0020\w`|`"a b"``"c d"`içinde,`"a bc d"`|
|`\`|Bu konudaki bu ve diğer tablolarda kaçış karakteri olarak tanınmayan bir karakterden önce geldiğinde karakterle eşleşir. Örneğin, ile `\*` aynıdır `\x2A` ve ile `\.` aynıdır `\x2E` . Bu, normal ifade altyapısının dil öğelerini ( \* veya? gibi) ve karakter değişmez değerlerini (veya ile temsil edilen) belirsizliğini sağlar `\*` `\?` .|`\d+[\+-x\*]\d+`|`"(2+2) * 3*9"` içinde `"2+2"` ve `"3*9"`|

## <a name="character-classes"></a>Karakter Sınıfları

Bir karakter sınıfı, karakter kümelerinden herhangi biriyle eşleşir. Karakter sınıfları aşağıdaki tabloda listelenen dil öğelerini içerir: Daha fazla bilgi için bkz. [karakter sınıfları](character-classes-in-regular-expressions.md).

|Karakter sınıfı|Açıklama|Desen|Eşleşmeler|
|---------------------|-----------------|-------------|-------------|
|`[`*character_group*`]`|*Character_group*bir tek karakterle eşleşir. Varsayılan olarak, eşleşme büyük/küçük harf duyarlıdır.|`[ae]`|`"gray"` içinde `"a"`<br /><br /> `"a"``"e"`içinde,`"lane"`|
|`[^`*character_group*`]`|Değilleme: *character_group*olmayan herhangi bir tek karakterle eşleşir. Varsayılan olarak, *character_group* karakterler büyük/küçük harfe duyarlıdır.|`[^aei]`|`"r"`, `"g"` , `"n"` içinde`"reign"`|
|`[`*ilk* `-` *son*`]`|Karakter aralığı: *ilk* ve *en son*aralığındaki tek bir karakterle eşleşir.|`[A-Z]`|`"A"``"B"`içinde,`"AB123"`|
|`.`|Joker karakter: \n dışında herhangi bir tek karakterle eşleşir.<br /><br /> Bir sabit nokta karakteriyle (. ya da `\u002E` ), kaçış karakteriyle () önce gelmelidir `\.` .|`a.e`|`"nave"` içinde `"ave"`<br /><br /> `"water"` içinde `"ate"`|
|`\p{`*ad*`}`|Unicode Genel kategorisindeki veya *ada*göre belirtilen adlandırılmış bloktaki herhangi bir tek karakterle eşleşir.|`\p{Lu}`<br /><br /> `\p{IsCyrillic}`|`"C"``"L"`içinde,`"City Lights"`<br /><br /> `"Д"``"Ж"`içinde,`"ДЖem"`|
|`\P{`*ad*`}`|Unicode Genel kategorisinde veya *ada*göre belirtilen adlandırılmış blokta olmayan herhangi bir tek karakterle eşleşir.|`\P{Lu}`<br /><br /> `\P{IsCyrillic}`|`"i"`, `"t"` , `"y"` içinde`"City"`<br /><br /> `"e"``"m"`içinde,`"ДЖem"`|
|`\w`|Sözcük olan herhangi bir karakterle eşleşir.|`\w`|`"I"`,,, `"D"` `"A"` `"1"` , `"3"` içinde`"ID A1.3"`|
|`\W`|Sözcük olmayan herhangi bir karakterle eşleşir.|`\W`|`" "``"."`içinde,`"ID A1.3"`|
|`\s`|Boşluk olan herhangi bir karakterle eşleşir.|`\w\s`|`"ID A1.3"` içinde `"D "`|
|`\S`|Boşluk olmayan herhangi bir karakterle eşleşir.|`\s\S`|`"int __ctr"` içinde `" _"`|
|`\d`|Herhangi bir ondalık basamakla eşleşir.|`\d`|`"4 = IV"` içinde `"4"`|
|`\D`|Bir ondalık basamak dışında herhangi bir karakterle eşleşir.|`\D`|`" "`,,, `"="` `" "` `"I"` , `"V"` içinde`"4 = IV"`|

## <a name="anchors"></a>Tutturucular

Yer işaretleri veya atomik sıfır genişlik onayları, dizedeki geçerli konuma bağlı olarak eşleşmenin başarılı veya başarısız olmasına neden olurlar, ancak altyapının dize boyunca ilerlemesine veya karakterleri tüketmesine neden olmazlar. Aşağıdaki tabloda listelenen meta karakterler tutturuculardır. Daha fazla bilgi için bkz. [Tutturucular](anchors-in-regular-expressions.md).

|Onaylama işlemi|Açıklama|Desen|Eşleşmeler|
|---------------|-----------------|-------------|-------------|
|`^`|Varsayılan olarak, eşleşme dizenin başlangıcında başlatılmalıdır; çok satırlı modda, satırın başlangıcında başlamalıdır.|`^\d{3}`|`"901-333-"` içinde `"901"`|
|`$`|Varsayılan olarak, eşleşme dizenin sonunda veya dizenin sonundan önce gerçekleşmelidir `\n` ; çok satırlı modda, satırın sonundan önce veya satırın sonundaki öncesinde gerçekleşmelidir `\n` .|`-\d{3}$`|`"-901-333"` içinde `"-333"`|
|`\A`|Eşleşme dizenin başlangıcında gerçekleşmelidir.|`\A\d{3}`|`"901-333-"` içinde `"901"`|
|`\Z`|Eşleşme dizenin sonunda veya `\n` dizenin sonundaki önünde oluşmalıdır.|`-\d{3}\Z`|`"-901-333"` içinde `"-333"`|
|`\z`|Eşleşme dizenin sonunda gerçekleşmelidir.|`-\d{3}\z`|`"-901-333"` içinde `"-333"`|
|`\G`|Eşleşme önceki eşleşmenin sona erdiği noktada gerçekleşmelidir.|`\G\(\d\)`|`"(1)"`, `"(3)"` , `"(5)"` içinde`"(1)(3)(5)[7](9)"`|
|`\b`|Eşleşme, `\w` (alfasayısal) ve bir `\W` (alfasayısal olmayan) karakter arasındaki bir sınır üzerinde gerçekleşmelidir.|`\b\w+\s\w+\b`|`"them theme"``"them them"`içinde,`"them theme them them"`|
|`\B`|Eşleşme bir sınırda gerçekleşmemelidir `\b` .|`\Bend\w*\b`|`"ends"``"ender"`içinde,`"end sends endure lender"`|

## <a name="grouping-constructs"></a>Gruplandırma Yapıları

Yapıları gruplandırma, normal bir ifadenin alt ifadelerini açıklar ve tipik olarak bir giriş dizesinin alt dizelerini yakalar. Yapıları gruplandırma aşağıdaki tabloda listelenen dil öğelerini içerir. Daha fazla bilgi için bkz. [yapıları gruplandırma](grouping-constructs-in-regular-expressions.md).

|Yapıyı gruplandırma|Açıklama|Desen|Eşleşmeler|
|------------------------|-----------------|-------------|-------------|
|`(`alt *ifade*`)`|Eşleşen alt ifadeyi yakalar ve buna bir tabanlı bir sıra numarası atar.|`(\w)\1`|`"deep"` içinde `"ee"`|
|`(?<`*ad* `>` alt *ifade*`)`|Eşleşen alt ifadeyi adlandırılmış bir gruba yakalar.|`(?<double>\w)\k<double>`|`"deep"` içinde `"ee"`|
|`(?<`*name1* `-` *AD2* `>` alt *ifade*`)`|Bir dengeleme grubu tanımını tanımlar. Daha fazla bilgi için, [gruplandırma yapıları](grouping-constructs-in-regular-expressions.md)Içindeki "Grup tanımı Dengeleme" bölümüne bakın.|`(((?'Open'\()[^\(\)]*)+((?'Close-Open'\))[^\(\)]*)+)*(?(Open)(?!))$`|`"3+2^((1-3)*(3-1))"` içinde `"((1-3)*(3-1))"`|
|`(?:`alt *ifade*`)`|Yakalama yapmayan grubu tanımlar.|`Write(?:Line)?`|`"Console.WriteLine()"` içinde `"WriteLine"`<br /><br /> `"Console.Write(value)"` içinde `"Write"`|
|`(?imnsx-imnsx:`alt *ifade*`)`|Alt *ifade*içinde belirtilen seçenekleri uygular veya devre dışı bırakır. Daha fazla bilgi için bkz. [normal Ifade seçenekleri](regular-expression-options.md).|`A\d{2}(?i:\w+)\b`|`"A12xl"``"A12XL"`içinde,`"A12xl A12XL a12xl"`|
|`(?=`alt *ifade*`)`|Sıfır genişlik pozitif ileriye yönelik onaylar.|`\w+(?=\.)`|`"is"`, `"ran"` , ve `"out"` içinde`"He is. The dog ran. The sun is out."`|
|`(?!`alt *ifade*`)`|Sıfır genişlik negatif ileriye yönelik onaylar.|`\b(?!un)\w+\b`|`"sure"``"used"`içinde,`"unsure sure unity used"`|
|`(?<=`alt *ifade*`)`|Sıfır genişlik pozitif geriye yönelik onaylar.|`(?<=19)\d{2}\b`|`"99"`, `"50"` , `"05"` içinde`"1851 1999 1950 1905 2003"`|
|`(?<!`alt *ifade*`)`|Sıfır genişlik negatif geriye yönelik onaylar.|`(?<!19)\d{2}\b`|`"51"``"03"`içinde,`"1851 1999 1950 1905 2003"`|
|`(?>`alt *ifade*`)`|Atomik grup.|`[13579](?>A+B+)`|`"1ABB"`, `"3ABB"` , ve `"5AB"` içinde`"1ABB 3ABBC 5AB 5AC"`|

## <a name="quantifiers"></a>Miktar Niceleyiciler

Niceleyici, önceki öğenin (karakter, grup veya karakter sınıfı olabilir) kaç örneğinin oluşacak eşleme için giriş dizesinde mevcut olması gerektiğini belirtir. Miktar niceleyiciler aşağıdaki tabloda listelenen dil öğelerini içerir. Daha fazla bilgi için bkz. [nicelik belirteçleri](quantifiers-in-regular-expressions.md).

|Miktar Niceleyici|Açıklama|Desen|Eşleşmeler|
|----------------|-----------------|-------------|-------------|
|`*`|Önceki öğeyle sıfır kez veya daha fazla eşleşir.|`\d*\.\d`|`".0"`, `"19.9"`, `"219.9"`|
|`+`|Önceki öğeyle bir kez veya daha fazla eşleşir.|`"be+"`|`"bee"`içinde `"been"` , `"be"` içinde`"bent"`|
|`?`|Önceki öğeyle sıfır veya bir kez eşleşir.|`"rai?n"`|`"ran"`, `"rain"`|
|`{`*n*`}`|Önceki öğeyle tam olarak *n* kez eşleşir.|`",\d{3}"`|`",043"``"1,043.6"`,, `",876"` , `",543"` ve `",210"` içinde`"9,876,543,210"`|
|`{`*n*`,}`|Önceki öğeyle en az *n* kez eşleşir.|`"\d{2,}"`|`"166"`, `"29"`, `"1930"`|
|`{`*n* `,` *e*`}`|Önceki öğeyle en az *n* kez eşleşir, ancak hiç *8 kez eşleşmez* .|`"\d{3,5}"`|`"166"`, `"17668"`<br /><br /> `"193024"` içinde `"19302"`|
|`*?`|Önceki öğeyle sıfır kez veya daha fazla ancak mümkün olduğunca az eşleşir.|`\d*?\.\d`|`".0"`, `"19.9"`, `"219.9"`|
|`+?`|Önceki öğeyle bir kez veya daha fazla ancak mümkün olduğunca az eşleşir.|`"be+?"`|`"be"`içinde `"been"` , `"be"` içinde`"bent"`|
|`??`|Önceki öğeyle sıfır veya bir kez ancak mümkün olduğunca az eşleşir.|`"rai??n"`|`"ran"`, `"rain"`|
|`{`*n*`}?`|Önceki öğeyle tam olarak *n* kez eşleşir.|`",\d{3}?"`|`",043"``"1,043.6"`,, `",876"` , `",543"` ve `",210"` içinde`"9,876,543,210"`|
|`{`*n*`,}?`|Önceki öğeyle en az *n* kez, ancak mümkün olduğunca az eşleşir.|`"\d{2,}?"`|`"166"`, `"29"`, `"1930"`|
|`{`*n* `,` *e*`}?`|Önceki öğeyle *n* ila *5 kez ve* mümkün olduğunca az eşleşir.|`"\d{3,5}?"`|`"166"`, `"17668"`<br /><br /> `"193"``"024"`içinde,`"193024"`|

## <a name="backreference-constructs"></a>Yeniden Başvuru Yapıları

Yeniden başvuru, aynı normal ifadede daha sonra tanımlanabilecek alt ifadeyle daha önce eşleşmesine olanak sağlar. Aşağıdaki tabloda, .NET 'teki normal ifadeler tarafından desteklenen geri başvuru yapıları listelenmektedir. Daha fazla bilgi için bkz. [Backreference yapıları](backreference-constructs-in-regular-expressions.md).

|Yeniden başvuru yapısı|Açıklama|Desen|Eşleşmeler|
|-----------------------------|-----------------|-------------|-------------|
|`\`*sayı*|Yeniden başvuru. Numaralandırılmış ifadenin değeriyle eşleşir.|`(\w)\1`|`"seek"` içinde `"ee"`|
|`\k<`*ad*`>`|Adlandırılan yeniden başvuru. Adlandırılmış ifadenin değeriyle eşleşir.|`(?<char>\w)\k<char>`|`"seek"` içinde `"ee"`|

## <a name="alternation-constructs"></a>Değişim Yapıları

Değişim yapıları, ve/veya eşleştirmeyi etkinleştirmek üzere bir normal ifadeyi değiştirir. Bu yapılar aşağıdaki tabloda listelenen dil öğelerini içerir. Daha fazla bilgi için bkz. [değişim yapıları](alternation-constructs-in-regular-expressions.md).

|Değişim yapısı|Açıklama|Desen|Eşleşmeler|
|---------------------------|-----------------|-------------|-------------|
|<code>&#124;</code>|Dikey çubuk () karakteriyle ayrılmış herhangi bir öğeyle eşleşir <code>&#124;</code> .|<code>th(e&#124;is&#124;at)</code>|`"the"``"this"`içinde,`"this is the day."`|
|`(?(`*ifade* `)` *Evet* <code>&#124;</code> *Hayır*`)`|*Expression* ile belirlenen normal ifade deseninin eşleşiyorsa *Evet* ile eşleşir; Aksi takdirde, isteğe bağlı *hiçbir* bölüm ile eşleşir. *ifade* sıfır genişlikli bir onaylama olarak yorumlanır.|<code>(?(A)A\d{2}\b&#124;\b\d{3}\b)</code>|`"A10"``"910"`içinde,`"A10 C103 910"`|
|`(?(`*ad* `)` *Evet* <code>&#124;</code> *Hayır*`)`|*Ad*, adlandırılmış veya numaralandırılmış yakalama grubu, eşleşme içeriyorsa *Evet* ile eşleşir; Aksi takdirde, isteğe bağlı *No*ile eşleşir.|<code>(?&lt;quoted&gt;&quot;)?(?(quoted).+?&quot;&#124;\S+\s)</code>|`"Dogs.jpg "``"\"Yiska playing.jpg\""`içinde,`"Dogs.jpg \"Yiska playing.jpg\""`|

## <a name="substitutions"></a>Değişimler

Değişimler değiştirme desenlerinde desteklenen normal ifade dil öğeleridir. Daha fazla bilgi için bkz. [alternatifler](substitutions-in-regular-expressions.md). Aşağıdaki tabloda listelenen meta karakterler atomik sıfır genişlik onaylarıdır.

|Karakter|Açıklama|Desen|Değiştirme deseni|Giriş dizesi|Sonuç Dizesi|
|---------------|-----------------|-------------|-------------------------|------------------|-------------------|
|`$`*sayı*|Grup *numarasıyla*eşleşen alt dizeyi değiştirir.|`\b(\w+)(\s)(\w+)\b`|`$3$2$1`|`"one two"`|`"two one"`|
|`${`*ad*`}`|Adlandırılmış grup *adıyla*eşleştirilen alt dizeyi değiştirir.|`\b(?<word1>\w+)(\s)(?<word2>\w+)\b`|`${word2} ${word1}`|`"one two"`|`"two one"`|
|`$$`|Değişmez değerli bir "$" işaretinin yerini alır.|`\b(\d+)\s?USD`|`$$$1`|`"103 USD"`|`"$103"`|
|`$&`|Tam eşleşmenin bir kopyasının yerini alır.|`\$?\d*\.?\d+`|`**$&**`|`"$1.30"`|`"**$1.30**"`|
|``$` ``|Eşleşmeden önce giriş dizesi metninin tamamının yerini alır.|`B+`|``$` ``|`"AABBCC"`|`"AAAACC"`|
|`$'`|Eşleşmeden sonra giriş dizesi metninin tamamının yerini alır.|`B+`|`$'`|`"AABBCC"`|`"AACCCC"`|
|`$+`|Yakalanan son grubun yerini alır.|`B+(C+)`|`$+`|`"AABBCCDD"`|`"AACCDD"`|
|`$_`|Giriş dizesinin tamamının yerini alır.|`B+`|`$_`|`"AABBCC"`|`"AAAABBCCCC"`|

## <a name="regular-expression-options"></a>Normal İfade Seçenekleri

Normal ifade sisteminin normal ifade modellerini nasıl denetleyeceğiyle ilgili seçenekler belirtebilirsiniz. Bu seçeneklerin çoğu satır içi (normal ifade düzeninde) veya bir veya daha fazla sabit olarak belirtilebilir <xref:System.Text.RegularExpressions.RegexOptions> . Bu hızlı başvuru yalnızca satır içi seçeneklerini listeler. Satır içi ve seçenekler hakkında daha fazla bilgi için <xref:System.Text.RegularExpressions.RegexOptions> bkz. [normal ifade seçenekleri](regular-expression-options.md)makalesi.

Satır içi seçeneği iki şekilde belirtebilirsiniz:

- Bir [miscellaneous construct](miscellaneous-constructs-in-regular-expressions.md) `(?imnsx-imnsx)` seçenek veya seçenek kümesinden önce gelen eksi işareti (-), bu seçenekleri devre dışı bırakır. Örneğin, `(?i-mn)` büyük/küçük harf duyarsız eşleştirmeyi ( `i` ) açar, çok satırlı modu ( `m` ) kapatır ve adsız grup yakalamalarını ( `n` ) kapatır. Seçenek, seçeneğin tanımlandığı noktadan itibaren normal ifade deseni için geçerlidir ve desenin sonuna kadar ya da bir başka yapının seçeneği tersine çevirdiği noktaya kadar etkilidir.
- [Gruplandırma yapısı](grouping-constructs-in-regular-expressions.md)alt ifadesini kullanarak `(?imnsx-imnsx:` *subexpression* `)` , yalnızca belirtilen grup için seçenekleri tanımlar.

.NET normal ifade motoru aşağıdaki satır içi seçenekleri destekler:

|Seçenek|Açıklama|Desen|Eşleşmeler|
|------------|-----------------|-------------|-------------|
|`i`|Büyük küçük harf duyarlı eşleme kullanın.|`\b(?i)a(?-i)a\w+\b`|`"aardvark"``"aaaAuto"`içinde,`"aardvark AAAuto aaaAuto Adam breakfast"`|
|`m`|Çok satırlı modunu kullanın. `^`ve `$` bir dizenin başlangıcı ve bitişi yerine bir satırın başlangıcını ve bitişini eşleştirin.|Bir örnek için, [normal Ifade seçeneklerinde](regular-expression-options.md)"çok satırlı mod" bölümüne bakın.||
|`n`|Adsız grupları yakalamayın.|Bir örnek için, [normal Ifade seçeneklerinde](regular-expression-options.md)"yalnızca belirtik yakalama" bölümüne bakın.||
|`s`|Tek satır modunu kullanın.|Bir örnek için, [normal Ifade seçeneklerinde](regular-expression-options.md)"tek satır modu" bölümüne bakın.||
|`x`|Normal ifade deseninde kaçışsız boşluğu yoksay.|`\b(?x) \d+ \s \w+`|`"1 aardvark"``"2 cats"`içinde,`"1 aardvark 2 cats IV centurions"`|

## <a name="miscellaneous-constructs"></a>Çeşitli Yapılar

Çeşitli yapılar, bir normal ifade desenini değiştirir veya bununla ilgili bilgi sağlar. Aşağıdaki tabloda .NET tarafından desteklenen çeşitli yapılar listelenmektedir. Daha fazla bilgi için bkz. [çeşitli yapılar](miscellaneous-constructs-in-regular-expressions.md).

|Oluştur|Tanım|Örnek|
|---------------|----------------|-------------|
|`(?imnsx-imnsx)`|Bir düzenin ortasında büyük/küçük harf duyarlı gibi seçenekleri ayarlar veya devre dışı bırakır. Daha fazla bilgi için bkz. [normal Ifade seçenekleri](regular-expression-options.md).|`\bA(?i)b\w+\b``"ABA"`içindeki eşleşmeler `"Able"``"ABA Able Act"`|
|`(?#`*Açıklama*`)`|Satır içi açıklama. Açıklama ilk kapanış parantezinde sona erer.|`\bA(?#Matches words starting with A)\w+\b`|
|`#`[satır sonuna kadar]|X-mode yorumu. Yorum, kaçışsız başlar `#` ve satırın sonuna kadar devam eder.|`(?x)\bA\w+\b#Matches words starting with A`|

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Text.RegularExpressions?displayProperty=nameWithType>
- <xref:System.Text.RegularExpressions.Regex?displayProperty=nameWithType>
- [Normal Ifadeler](regular-expressions.md)
- [Normal Ifade sınıfları](the-regular-expression-object-model.md)
- [Normal Ifadeler-hızlı başvuru (Word biçiminde indir)](https://download.microsoft.com/download/D/2/4/D240EBF6-A9BA-4E4F-A63F-AEB6DA0B921C/Regular%20expressions%20quick%20reference.docx)
- [Normal Ifadeler-hızlı başvuru (PDF biçiminde indir)](https://download.microsoft.com/download/D/2/4/D240EBF6-A9BA-4E4F-A63F-AEB6DA0B921C/Regular%20expressions%20quick%20reference.pdf)
