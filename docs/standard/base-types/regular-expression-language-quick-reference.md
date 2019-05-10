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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 053df7eeba10938f1d1d749e856f64d179d471d4
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64664672"
---
# <a name="regular-expression-language---quick-reference"></a>Normal İfade Dili - Hızlı Başvuru
 Normal bir ifade, normal ifade motorunun giriş metninde eşleştirmeyi denediği bir desendir. Bir desen, bir veya daha çok karakter sabitinden, işleçlerden veya yapılardan oluşur.  Kısa bir giriş için bkz. [.NET normal ifadeler](../../../docs/standard/base-types/regular-expressions.md).  
  
 Bu hızlı başvurudaki her bölüm, belirli bir kategori karakter, işleç ve normal ifadeler tanımlamak için kullanabileceğiniz yapıları listeler.  
  
 Bu bilgileri indirip yazdırma iki biçim de kolayca başvurmak için sunulmuştur:  
  
 [Word (.docx) biçiminde indir](https://download.microsoft.com/download/D/2/4/D240EBF6-A9BA-4E4F-A63F-AEB6DA0B921C/Regular%20expressions%20quick%20reference.docx)  
 [PDF (.pdf) biçiminde indir](https://download.microsoft.com/download/D/2/4/D240EBF6-A9BA-4E4F-A63F-AEB6DA0B921C/Regular%20expressions%20quick%20reference.pdf)  
  
## <a name="character-escapes"></a>Karakter Çıkışları  
 Ters eğik çizgi karakteri (\\) normal bir ifadede ya da izleyen karakterin özel bir karakter (aşağıdaki tabloda gösterildiği gibi) gösterir veya genel anlamıyla yorumlanması. Daha fazla bilgi için [karakter çıkışları](../../../docs/standard/base-types/character-escapes-in-regular-expressions.md).  
  
|Kaçan karakter|Açıklama|Desen|Eşleşmeler|  
|-----------------------|-----------------|-------------|-------------|  
|`\a`|Bir bell karakterle eşleşir, \u0007.|`\a`|`"\u0007"` İçinde `"Error!" + '\u0007'`|  
|`\b`|Bir karakter sınıfında, geri al tuşuyla eşleşir, \u0008.|`[\b]{3,}`|`"\b\b\b\b"` İçinde `"\b\b\b\b"`|  
|`\t`|Bir sekmeyle eşleşir, \u0009.|`(\w+)\t`|`"item1\t"`, `"item2\t"` içinde `"item1\titem2\t"`|  
|`\r`|Bir satır başıyla eşleşir, \u000D. (`\r` yeni satır karakteri eşdeğer değildir `\n`.)|`\r\n(\w+)`|`"\r\nThese"` İçinde `"\r\nThese are\ntwo lines."`|  
|`\v`|Bir dikey sekmeyle eşleşir, \u000B.|`[\v]{2,}`|`"\v\v\v"` İçinde `"\v\v\v"`|  
|`\f`|Form besleme ile eşleşir, \u000C.|`[\f]{2,}`|`"\f\f\f"` İçinde `"\f\f\f"`|  
|`\n`|Yeni bir satırla eşleşir, \u000A.|`\r\n(\w+)`|`"\r\nThese"` İçinde `"\r\nThese are\ntwo lines."`|  
|`\e`|Bir çıkışla eşleşir, \u001B.|`\e`|`"\x001B"` İçinde `"\x001B"`|  
|`\` *nnn*|Bir karakter belirtmek için sekizlik gösterim kullanır (*nnn* iki veya üç basamak içerir).|`\w\040\w`|`"a b"`, `"c d"` içinde `"a bc d"`|  
|`\x` *nn*|Bir karakter belirtmek için onaltılık gösterim kullanır (*nn* tam olarak iki basamak içerir).|`\w\x20\w`|`"a b"`, `"c d"` içinde `"a bc d"`|  
|`\c` *X*<br /><br /> `\c` *x*|Tarafından belirtilen ASCII denetim karakteriyle eşleşir *X* veya *x*burada *X* veya *x* harfinin denetim karakteri.|`\cC`|`"\x0003"` içinde `"\x0003"` (Ctrl-C)|  
|`\u` *nnnn*|Onaltılık gösterim kullanılarak bir Unicode karakter ile eşleşir (tam olarak dört basamak tarafından temsil edilen *nnnn*).|`\w\u0020\w`|`"a b"`, `"c d"` içinde `"a bc d"`|  
|`\`|Bu konudaki bu ve diğer tablolarda kaçış karakteri olarak tanınmayan bir karakterden önce geldiğinde karakterle eşleşir. Örneğin, `\*` aynı `\x2A`, ve `\.` aynı `\x2E`. Bu normal ifade altyapısının dil öğelerinin belirsizliğinin ortadan kaldırılmasını sağlar (gibi \* veya?) ve karakter değişmez değerleri (tarafından temsil edilen `\*` veya `\?`).|`\d+[\+-x\*]\d+`|`"2+2"` ve `"3*9"` içinde `"(2+2) * 3*9"`|  
  
 [Başa dön](#top)  
  
## <a name="character-classes"></a>Karakter Sınıfları  
 Bir karakter sınıfı, karakter kümelerinden herhangi biriyle eşleşir. Karakter sınıfları aşağıdaki tabloda listelenen dil öğelerini içerir: Daha fazla bilgi için bkz.[Karakter Sınıfları](../../../docs/standard/base-types/character-classes-in-regular-expressions.md).  
  
|Karakter sınıfı|Açıklama|Desen|Eşleşmeler|  
|---------------------|-----------------|-------------|-------------|  
|`[` *character_group* `]`|Herhangi bir tek karakterle eşleşir *character_group*. Varsayılan olarak, eşleşme büyük/küçük harf duyarlıdır.|`[ae]`|`"a"` İçinde `"gray"`<br /><br /> `"a"`, `"e"` içinde `"lane"`|  
|`[^` *character_group* `]`|Olumsuzlama: Kullanımda olmayan herhangi bir tek karakterle eşleşir *character_group*. Varsayılan olarak, içindeki karakterler *character_group* büyük küçük harfe duyarlıdır.|`[^aei]`|`"r"`, `"g"`, `"n"` içinde `"reign"`|  
|`[` *İlk* `-` *son* `]`|Karakter aralığı: Aralığındaki herhangi tek karakterle eşleşir *ilk* için *son*.|`[A-Z]`|`"A"`, `"B"` içinde `"AB123"`|  
|`.`|Joker karakter: \N dışında herhangi bir tek karakterle eşleşir.<br /><br /> Bir değişmez nokta değeriyle eşleştirmek için (. veya `\u002E`), kaçış karakteriyle gelmelidir (`\.`).|`a.e`|`"ave"` İçinde `"nave"`<br /><br /> `"ate"` İçinde `"water"`|  
|`\p{` *Adı* `}`|Unicode Genel kategorisinde veya tarafından belirtilen adlandırılmış bloktaki herhangi bir tek karakterle eşleşir *adı*.|`\p{Lu}`<br /><br /> `\p{IsCyrillic}`|`"C"`, `"L"` içinde `"City Lights"`<br /><br /> `"Д"`, `"Ж"` içinde `"ДЖem"`|  
|`\P{` *Adı* `}`|Unicode Genel kategorisinde veya tarafından belirtilen adlandırılmış blokta olmayan herhangi bir tek karakterle eşleşir *adı*.|`\P{Lu}`<br /><br /> `\P{IsCyrillic}`|`"i"`, `"t"`, `"y"` içinde `"City"`<br /><br /> `"e"`, `"m"` içinde `"ДЖem"`|  
|`\w`|Sözcük olan herhangi bir karakterle eşleşir.|`\w`|`"I"`, `"D"`, `"A"`, `"1"`, `"3"` içinde `"ID A1.3"`|  
|`\W`|Sözcük olmayan herhangi bir karakterle eşleşir.|`\W`|`" "`, `"."` içinde `"ID A1.3"`|  
|`\s`|Boşluk olan herhangi bir karakterle eşleşir.|`\w\s`|`"D "` İçinde `"ID A1.3"`|  
|`\S`|Boşluk olmayan herhangi bir karakterle eşleşir.|`\s\S`|`" _"` İçinde `"int __ctr"`|  
|`\d`|Herhangi bir ondalık basamakla eşleşir.|`\d`|`"4"` İçinde `"4 = IV"`|  
|`\D`|Bir ondalık basamak dışında herhangi bir karakterle eşleşir.|`\D`|`" "`, `"="`, `" "`, `"I"`, `"V"` içinde `"4 = IV"`|  
  
 [Başa dön](#top)  
  
## <a name="anchors"></a>Tutturucular  
 Bağlayıcılar veya atomik sıfır genişlik onayları, dizedeki geçerli konuma bağlı olarak eşleşmenin başarılı veya başarısız olmasına neden olurlar, ancak altyapının dize boyunca ilerlemesine veya karakterleri tüketmesine neden olmazlar. Aşağıdaki tabloda listelenen meta karakterler bağlayıcılardır. Daha fazla bilgi için bkz. [bağlayıcılar](../../../docs/standard/base-types/anchors-in-regular-expressions.md).  
  
|Onaylama işlemi|Açıklama|Desen|Eşleşmeler|  
|---------------|-----------------|-------------|-------------|  
|`^`|Varsayılan olarak, eşleşme dizenin başlangıcında başlamalıdır; çok satırlı modu satırın başlangıcında başlamalıdır.|`^\d{3}`|`"901"` İçinde `"901-333-"`|  
|`$`|Varsayılan olarak, eşleşme önce ya da dizenin sonunda gerçekleşmelidir `\n` sonunda dize; çok satırlı modu, çizgi veya önce bitmeden önce gerçekleşmelidir `\n` satırın sonunda.|`-\d{3}$`|`"-333"` İçinde `"-901-333"`|  
|`\A`|Eşleşme dizenin başlangıcında gerçekleşmelidir.|`\A\d{3}`|`"901"` İçinde `"901-333-"`|  
|`\Z`|Eşleşme dizenin sonunda veya önce sonunda gerçekleşmelidir `\n` dizenin sonunda.|`-\d{3}\Z`|`"-333"` İçinde `"-901-333"`|  
|`\z`|Eşleşme dizenin sonunda gerçekleşmelidir.|`-\d{3}\z`|`"-333"` İçinde `"-901-333"`|  
|`\G`|Eşleşme önceki eşleşmenin sona erdiği noktada gerçekleşmelidir.|`\G\(\d\)`|`"(1)"`, `"(3)"`, `"(5)"` içinde `"(1)(3)(5)[7](9)"`|  
|`\b`|Eşleşme arasındaki sınırda gerçekleşmemelidir bir `\w` (alfasayısal) ve bir `\W` (alfasayısal olmayan) karakter.|`\b\w+\s\w+\b`|`"them theme"`, `"them them"` içinde `"them theme them them"`|  
|`\B`|Eşleşme gerçekleşmemelidir bir `\b` sınır.|`\Bend\w*\b`|`"ends"`, `"ender"` içinde `"end sends endure lender"`|  
  
 [Başa dön](#top)  
  
## <a name="grouping-constructs"></a>Gruplandırma Yapıları  
 Yapıları gruplandırma, normal bir ifadenin alt ifadelerini açıklar ve tipik olarak bir giriş dizesinin alt dizelerini yakalar. Yapıları gruplandırma aşağıdaki tabloda listelenen dil öğelerini içerir. Daha fazla bilgi için bkz. [Gruplandırma Yapıları](grouping-constructs-in-regular-expressions.md).  
  
|Yapıyı gruplandırma|Açıklama|Desen|Eşleşmeler|  
|------------------------|-----------------|-------------|-------------|  
|`(` *Alt ifade* `)`|Eşleşen alt ifadeyi yakalar ve buna bir tabanlı bir sıra numarası atar.|`(\w)\1`|`"ee"` İçinde `"deep"`|  
|`(?<` *adı* `>` *alt ifade* `)`|Eşleşen alt ifadeyi adlandırılmış bir gruba yakalar.|`(?<double>\w)\k<double>`|`"ee"` İçinde `"deep"`|  
|`(?<` *name1* `-` *name2* `>` *alt ifade* `)`|Bir dengeleme grubu tanımını tanımlar. Daha fazla bilgi için [Gruplandırma Yapıları](grouping-constructs-in-regular-expressions.md) içindeki "Dengeleme Grubu Tanımı" bölümüne bakın.|`(((?'Open'\()[^\(\)]*)+((?'Close-Open'\))[^\(\)]*)+)*(?(Open)(?!))$`|`"((1-3)*(3-1))"` İçinde `"3+2^((1-3)*(3-1))"`|  
|`(?:` *Alt ifade* `)`|Yakalama yapmayan grubu tanımlar.|`Write(?:Line)?`|`"WriteLine"` İçinde `"Console.WriteLine()"`<br /><br /> `"Write"` İçinde `"Console.Write(value)"`|  
|`(?imnsx-imnsx:` *Alt ifade* `)`|*Alt ifade* dahilinde belirlenen seçenekleri uygular veya devre dışı bırakır. Daha fazla bilgi için bkz. [Normal İfade Seçenekleri](regular-expression-options.md).|`A\d{2}(?i:\w+)\b`|`"A12xl"`, `"A12XL"` içinde `"A12xl A12XL a12xl"`|  
|`(?=` *Alt ifade* `)`|Sıfır genişlik pozitif ileriye yönelik onaylar.|`\w+(?=\.)`|`"is"`, `"ran"`, ve `"out"` içinde `"He is. The dog ran. The sun is out."`|  
|`(?!` *Alt ifade* `)`|Sıfır genişlik negatif ileriye yönelik onaylar.|`\b(?!un)\w+\b`|`"sure"`, `"used"` içinde `"unsure sure unity used"`|  
|`(?<=` *Alt ifade* `)`|Sıfır genişlik pozitif geriye yönelik onaylar.|`(?<=19)\d{2}\b`|`"99"`, `"50"`, `"05"` içinde `"1851 1999 1950 1905 2003"`|  
|`(?<!` *Alt ifade* `)`|Sıfır genişlik negatif geriye yönelik onaylar.|`(?<!19)\d{2}\b`|`"51"`, `"03"` içinde `"1851 1999 1950 1905 2003"`|  
|`(?>` *Alt ifade* `)`|Geri dönüşlü olmayan (veya "greedy") alt ifade.|`[13579](?>A+B+)`|`"1ABB"`, `"3ABB"`, ve `"5AB"` içinde `"1ABB 3ABBC 5AB 5AC"`|  
  
 [Başa dön](#top)  
  
## <a name="quantifiers"></a>Miktar Niceleyiciler  
 Niceleyici, önceki öğenin (karakter, grup veya karakter sınıfı olabilir) kaç örneğinin oluşacak eşleme için giriş dizesinde mevcut olması gerektiğini belirtir. Miktar niceleyiciler aşağıdaki tabloda listelenen dil öğelerini içerir. Daha fazla bilgi için bkz [Miktar Belirleyiciler](quantifiers-in-regular-expressions.md).  
  
|Miktar Niteleyici|Açıklama|Desen|Eşleşmeler|  
|----------------|-----------------|-------------|-------------|  
|`*`|Önceki öğeyle sıfır kez veya daha fazla eşleşir.|`\d*\.\d`|`".0"`, `"19.9"`, `"219.9"`|  
|`+`|Önceki öğeyle bir kez veya daha fazla eşleşir.|`"be+"`|`"bee"` içinde `"been"`, `"be"` içinde `"bent"`|  
|`?`|Önceki öğeyle sıfır veya bir kez eşleşir.|`"rai?n"`|`"ran"`, `"rain"`|  
|`{` *n* `}`|Önceki öğeyle tam olarak eşleşir *n* kez.|`",\d{3}"`|`",043"` içinde `"1,043.6"`, `",876"`, `",543"`, ve `",210"` içinde `"9,876,543,210"`|  
|`{` *n* `,}`|Önceki öğeyle en az eşleşir *n* kez.|`"\d{2,}"`|`"166"`, `"29"`, `"1930"`|  
|`{` *n* `,` *m* `}`|Önceki öğeyle en az eşleşir *n* süreleri, ancak Hayır birden fazla *m* kez.|`"\d{3,5}"`|`"166"`, `"17668"`<br /><br /> `"19302"` İçinde `"193024"`|  
|`*?`|Önceki öğeyle sıfır kez veya daha fazla ancak mümkün olduğunca az eşleşir.|`\d*?\.\d`|`".0"`, `"19.9"`, `"219.9"`|  
|`+?`|Önceki öğeyle bir kez veya daha fazla ancak mümkün olduğunca az eşleşir.|`"be+?"`|`"be"` içinde `"been"`, `"be"` içinde `"bent"`|  
|`??`|Önceki öğeyle sıfır veya bir kez ancak mümkün olduğunca az eşleşir.|`"rai??n"`|`"ran"`, `"rain"`|  
|`{` *n* `}?`|Önceki öğeyle tam olarak eşleşen *n* kez.|`",\d{3}?"`|`",043"` içinde `"1,043.6"`, `",876"`, `",543"`, ve `",210"` içinde `"9,876,543,210"`|  
|`{` *n* `,}?`|Önceki öğeyle en az eşleşir *n* kez ancak mümkün olduğunca.|`"\d{2,}?"`|`"166"`, `"29"`, `"1930"`|  
|`{` *n* `,` *m* `}?`|Önceki öğeyle eşleşen *n* ve *m* kez ancak mümkün olduğunca.|`"\d{3,5}?"`|`"166"`, `"17668"`<br /><br /> `"193"`, `"024"` içinde `"193024"`|  
  
 [Başa dön](#top)  
  
## <a name="backreference-constructs"></a>Yeniden Başvuru Yapıları  
 Yeniden başvuru, daha önceden eşleşen bir alt ifadenin, aynı normal ifadede daha sonra tanımlanabilmesine olanak sağlar. Aşağıdaki tablo, .NET içindeki düzenli ifadelerle desteklenen yeniden başvuru yapılarını listeler. Daha fazla bilgi için bkz. [Yeniden Başvuru Yapıları](backreference-constructs-in-regular-expressions.md).  
  
|Yeniden başvuru yapısı|Açıklama|Desen|Eşleşmeler|  
|-----------------------------|-----------------|-------------|-------------|  
|`\` *Sayı*|Yeniden başvuru. Numaralandırılmış ifadenin değeriyle eşleşir.|`(\w)\1`|`"ee"` İçinde `"seek"`|  
|`\k<` *Adı* `>`|Adlandırılan yeniden başvuru. Adlandırılmış ifadenin değeriyle eşleşir.|`(?<char>\w)\k<char>`|`"ee"` İçinde `"seek"`|  
  
 [Başa dön](#top)  
  
## <a name="alternation-constructs"></a>Değişim Yapıları  
 Değişim yapıları, ve/veya eşleştirmesini etkinleştirmek üzere bir normal ifadeyi değiştirir. Bu yapılar aşağıdaki tabloda listelenen dil öğelerini içerir. Daha fazla bilgi için bkz. [Değişim Yapıları](alternation-constructs-in-regular-expressions.md).  
  
|Değişim yapısı|Açıklama|Desen|Eşleşmeler|  
|---------------------------|-----------------|-------------|-------------|  
|<code>&#124;</code>|Bir çubukla ayrılan herhangi bir öğeyle eşleşir (<code>&#124;</code>) karakter.|<code>th(e&#124;is&#124;at)</code>|`"the"`, `"this"` içinde `"this is the day."`|  
|`(?(` *ifade* `)` *Evet* <code>&#124;</code> *yok* `)`|Eşleşen *Evet* ile belirlenen normal ifade deseni eşleşiyorsa *ifade* eşleşir; Aksi halde isteğe bağlı eşleşen *hiçbir* bölümü. *ifade* Sıfır genişlikli onaylama olarak yorumlanır.|<code>(?(A)A\d{2}\b&#124;\b\d{3}\b)</code>|`"A10"`, `"910"` içinde `"A10 C103 910"`|  
|`(?(` *adı* `)` *Evet* <code>&#124;</code> *yok* `)`|Eşleşen *Evet* varsa *adı*, adlandırışmış veya numaralandırılmış yakalama grubu bir eşleşmeye sahip; Aksi halde isteğe bağlı eşleşen *hiçbir*.|<code>(?&lt;quoted&gt;&quot;)?(?(quoted).+?&quot;&#124;\S+\s)</code>|`"Dogs.jpg "`, `"\"Yiska playing.jpg\""` içinde `"Dogs.jpg \"Yiska playing.jpg\""`|  
  
 [Başa dön](#top)  
  
## <a name="substitutions"></a>Değişimler  
 Değişimler, değiştirme desenlerinde desteklenen normal ifade dil öğeleridir. Daha fazla bilgi için bkz. [Değişimler](substitutions-in-regular-expressions.md). Aşağıdaki tabloda listelenen meta karakterler atomik sıfır genişlik onaylarıdır.  
  
|Karakter|Açıklama|Desen|Değiştirme deseni|Giriş dizesi|Sonuç Dizesi|  
|---------------|-----------------|-------------|-------------------------|------------------|-------------------|  
|`$` *Sayı*|Grubuyla eşleştirilen alt dizenin yerini alır *numarası*.|`\b(\w+)(\s)(\w+)\b`|`$3$2$1`|`"one two"`|`"two one"`|  
|`${` *Adı* `}`|Adlandırılmış grubuyla eşleştirilen alt dizenin yerini alır *adı*.|`\b(?<word1>\w+)(\s)(?<word2>\w+)\b`|`${word2} ${word1}`|`"one two"`|`"two one"`|  
|`$$`|Değişmez değerli bir "$" işaretinin yerini alır.|`\b(\d+)\s?USD`|`$$$1`|`"103 USD"`|`"$103"`|  
|`$&`|Tam eşleşmenin bir kopyasının yerini alır.|`\$?\d*\.?\d+`|`**$&**`|`"$1.30"`|`"**$1.30**"`|  
|``$` ``| Önce eşleşmenin Giriş dizesinin tüm metnini değiştirir. |`B+`|``$` ``|`"AABBCC"`|`"AAAACC"`|  
|`$'`|Eşleşmeden sonra giriş dizesi metninin tamamının yerini alır.|`B+`|`$'`|`"AABBCC"`|`"AACCCC"`|  
|`$+`|Yakalanan son grubun yerini alır.|`B+(C+)`|`$+`|`"AABBCCDD"`|`"AACCDD"`|  
|`$_`|Giriş dizesinin tamamının yerini alır.|`B+`|`$_`|`"AABBCC"`|`"AAAABBCCCC"`|  
  
 [Başa dön](#top)  
  
## <a name="regular-expression-options"></a>Normal İfade Seçenekleri  
 Normal ifade sisteminin, normal ifade desenlerini nasıl denetleyeceğiyle ilgili seçenekler belirtebilirsiniz. Bu seçeneklerin çoğu, satır içi olarak (normal ifade deseninde) ya da bir veya daha fazla <xref:System.Text.RegularExpressions.RegexOptions> sabiti olarak belirtilebilir. Bu hızlı başvuru yalnızca satır içi seçenekleri listeler. Satır içi ve <xref:System.Text.RegularExpressions.RegexOptions> seçenekleri hakkında daha fazla bilgi için [Normal İfade Seçenekleri](regular-expression-options.md) başlıklı makaleye bakın.  
  
 Satır içi seçeneği iki şekilde belirtebilirsiniz:  
  
- Kullanarak [muhtelif yapı](miscellaneous-constructs-in-regular-expressions.md) `(?imnsx-imnsx)`, bir seçenek veya seçenek kümesinden önce bir eksi işareti (-) o seçenekleri kapattığı. Örneğin, `(?i-mn)` büyük küçük harf duyarsız eşleştirmeyi (`i`) açar, çok satırlı modunu (`m`) kapatır ve adsız Grup yakalamalarını (`n`) devre dışı. Seçenek, seçeneğin tanımlandığı noktadan itibaren normal ifade deseni için geçerlidir ve desenin sonuna kadar ya da bir başka yapının seçeneği tersine çevirdiği noktaya kadar etkilidir.  
  
- Kullanarak [yapıyı gruplandırma](grouping-constructs-in-regular-expressions.md)`(?imnsx-imnsx:`*subexpression*`)`, yalnızca belirtilen grup için seçenekleri tanımlar.  
  
 .NET normal ifade motoru aşağıdaki satır içi seçeneklerini destekler.  
  
|Seçenek|Açıklama|Desen|Eşleşmeler|  
|------------|-----------------|-------------|-------------|  
|`i`|Büyük küçük harf duyarlı eşleme kullanın.|`\b(?i)a(?-i)a\w+\b`|`"aardvark"`, `"aaaAuto"` içinde `"aardvark AAAuto aaaAuto Adam breakfast"`|  
|`m`|Çok satırlı modunu kullanın. `^` ve `$`, bir dizenin başlangıcı ve bitişi yerine bir satırın başlangıcı ve bitişini eşler.|Bir örnek için [Normal İfade Seçenekleri](regular-expression-options.md) altındaki "Çok satırlı modu" bölümüne bakın.||  
|`n`|Adsız grupları yakalamayın.|Bir örnek için [Normal İfade Seçenekleri](regular-expression-options.md) altındaki "Yalnızca Açık Yakalama" bölümüne bakın.||  
|`s`|Tek satır modunu kullanın.|Bir örnek için [Normal İfade Seçenekleri](regular-expression-options.md) altındaki "Tek Satır Modu" bölümüne bakın.||  
|`x`|Normal ifade deseninde kaçışsız boşluğu yoksay.|`\b(?x) \d+ \s \w+`|`"1 aardvark"`, `"2 cats"` içinde `"1 aardvark 2 cats IV centurions"`|  
  
 [Başa dön](#top)  
  
## <a name="miscellaneous-constructs"></a>Çeşitli Yapılar  
 Çeşitli yapılar, bir normal ifade desenini değiştirir veya bununla ilgili bilgi sağlar. Aşağıdaki tablo, .NET tarafından desteklenen çeşitli yapıları listeler. Daha fazla bilgi için bkz. [Çeşitli Yapılar](miscellaneous-constructs-in-regular-expressions.md).  
  
|Oluştur|Tanım|Örnek|  
|---------------|----------------|-------------|  
|`(?imnsx-imnsx)`|Ayarlar veya bir desenin ortasındaki büyük/küçük harf duyarsızlığı gibi seçenekleri devre dışı bırakır. Daha fazla bilgi için bkz. [Normal İfade Seçenekleri](regular-expression-options.md).|`\bA(?i)b\w+\b` eşleşen `"ABA"`, `"Able"` içinde `"ABA Able Act"`|  
|`(?#` *Açıklama* `)`|Satır içi açıklama. Açıklama ilk kapanış parantezinde sona erer.|`\bA(?#Matches words starting with A)\w+\b`|  
|`#` [satır sonuna için]|X-mode yorumu. Yorum kaçışsız başlar `#` ve satırın sonuna dek devam eder.|`(?x)\bA\w+\b#Matches words starting with A`|  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Text.RegularExpressions?displayProperty=nameWithType>
- <xref:System.Text.RegularExpressions.Regex?displayProperty=nameWithType>
- [Normal İfadeler](regular-expressions.md)
- [Normal ifade sınıfları](the-regular-expression-object-model.md)
- [Normal İfade Örnekleri](regular-expression-examples.md)
- [Normal ifadeler - hızlı başvuru (indirme, Word biçiminde)](https://download.microsoft.com/download/D/2/4/D240EBF6-A9BA-4E4F-A63F-AEB6DA0B921C/Regular%20expressions%20quick%20reference.docx)
- [Normal ifadeler - hızlı başvuru (PDF biçimindeki indirme)](https://download.microsoft.com/download/D/2/4/D240EBF6-A9BA-4E4F-A63F-AEB6DA0B921C/Regular%20expressions%20quick%20reference.pdf)
