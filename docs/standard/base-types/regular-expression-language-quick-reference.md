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
ms.openlocfilehash: b41161d1511f7dce975ac5ad916750734972fa3c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="regular-expression-language---quick-reference"></a>Normal İfade Dili - Hızlı Başvuru
<a name="top"></a> Normal bir ifade normal ifade altyapısı giriş metni eşleştirmeyi dener bir desen ' dir. Bir desen, bir veya daha çok karakter sabitinden, işleçlerden veya yapılardan oluşur.  Kısa bir giriş için bkz [.NET normal ifadeler](../../../docs/standard/base-types/regular-expressions.md).  
  
 Bu hızlı başvurudaki her bölüm normal ifadeleri tanımlamak üzere kullanabileceğiniz belirli bir karakter, işleç ve yapı kategorisini listeler:  
  
 [Karakter çıkışları](#character_escapes)  
 [Karakter sınıfları](#character_classes)  
 [Yer İşaretleri](#atomic_zerowidth_assertions)  
 [Gruplandırma yapıları](#grouping_constructs)  
 [Belirleyiciler](#quantifiers)  
 [Yeniden başvuru yapıları](#backreference_constructs)  
 [Değişim yapıları](#alternation_constructs)  
 [Değişimler](#substitutions)  
 [Normal ifade seçenekleri](#options)  
 [Çeşitli yapılar](#miscellaneous_constructs)  
  
 Ayrıca kolay başvuru için karşıdan yüklemek ve yazdırma iki biçimlerde bu bilgiler sunulmuştur:  
  
 [Word (.docx) biçiminde indirin](https://download.microsoft.com/download/D/2/4/D240EBF6-A9BA-4E4F-A63F-AEB6DA0B921C/Regular%20expressions%20quick%20reference.docx)  
 [PDF (.pdf) biçiminde indirin](https://download.microsoft.com/download/D/2/4/D240EBF6-A9BA-4E4F-A63F-AEB6DA0B921C/Regular%20expressions%20quick%20reference.pdf)  
  
<a name="character_escapes"></a>   
## <a name="character-escapes"></a>Karakter Çıkışları  
 Ters eğik çizgi karakteri (\\) normal ifadede ya da izleyen karakterin (aşağıdaki tabloda gösterildiği gibi) bir özel karakter gösterir ya da tam anlamıyla yorumlanıp. Daha fazla bilgi için bkz: [karakter çıkışları](../../../docs/standard/base-types/character-escapes-in-regular-expressions.md).  
  
|Kaçan karakter|Açıklama|Desen|Eşleşmeler|  
|-----------------------|-----------------|-------------|-------------|  
|`\a`|Bir bell karakterle eşleşir, \u0007.|`\a`|"Error!" içinde "\u0007" + '\u0007'|  
|`\b`|Bir karakter sınıfında, geri al tuşuyla eşleşir, \u0008.|`[\b]{3,}`|"\b\b\b\b" içinde "\b\b\b\b"|  
|`\t`|Bir sekmeyle eşleşir, \u0009.|`(\w+)\t`|"item1\titem2\t" içinde "item1\t", "item2\t"|  
|`\r`|Bir satır başıyla eşleşir, \u000D. (`\r` yeni satır karakteri için eşdeğer olmayan `\n`.)|`\r\n(\w+)`|"\r\nThese are\ntwo lines" içinde "\r\nThese"|  
|`\v`|Bir dikey sekmeyle eşleşir, \u000B.|`[\v]{2,}`|"\v\v\v" içinde "\v\v\v"|  
|`\f`|Form besleme ile eşleşir, \u000C.|`[\f]{2,}`|"\f\f\f" içinde "\f\f\f"|  
|`\n`|Yeni bir satırla eşleşir, \u000A.|`\r\n(\w+)`|"\r\nThese are\ntwo lines" içinde "\r\nThese"|  
|`\e`|Bir çıkışla eşleşir, \u001B.|`\e`|"\x001B" içinde "\x001B"|  
|`\` *nnn*|Bir karakter belirtmek için sekizli gösterimini kullanır (*nnn* iki veya üç rakamı oluşur).|`\w\040\w`|Şunun içinde "a b", "c d" :<br /><br /> "a bc d"|  
|`\x` *nn*|Bir karakter belirtmek için onaltılık gösterimini kullanır (*nn* tam olarak iki sayılardan oluşur).|`\w\x20\w`|Şunun içinde "a b", "c d" :<br /><br /> "a bc d"|  
|`\c` *X*<br /><br /> `\c` *X*|Tarafından belirtilen ASCII denetim karakterle eşleşir *X* veya *x*, burada *X* veya *x* denetim karakteri harfi.|`\cC`|"\x0003" içinde "\x0003" (Ctrl-C)|  
|`\u` *nnnn*|Onaltılık gösterim kullanılarak bir Unicode karakteri ile eşleşir (tarafından belirtildiği şekilde tam olarak dört basamak *nnnn*).|`\w\u0020\w`|Şunun içinde "a b", "c d" :<br /><br /> "a bc d"|  
|`\`|Bu konudaki bu ve diğer tablolarda kaçış karakteri olarak tanınmayan bir karakterden önce geldiğinde karakterle eşleşir. Örneğin, `\*` aynı `\x2A`, ve `\.` aynı `\x2E`. Bu dil öğeleri belirsizliğini ortadan kaldırmak normal ifade altyapısı sağlar (gibi \* veya?) ve karakter değişmez değerleri (tarafından temsil edilen `\*` veya `\?`).|`\d+[\+-x\*]\d+`|"2 + 2" ve "3\*9" "(2+2) \* 3\*9"|  
  
 [Başa dön](#top)  
  
<a name="character_classes"></a>   
## <a name="character-classes"></a>Karakter Sınıfları  
 Bir karakter sınıfı, karakter kümelerinden herhangi biriyle eşleşir. Karakter sınıfları aşağıdaki tabloda listelenen dil öğelerini içerir: Daha fazla bilgi için bkz: [karakter sınıfları](../../../docs/standard/base-types/character-classes-in-regular-expressions.md).  
  
|Karakter sınıfı|Açıklama|Desen|Eşleşmeler|  
|---------------------|-----------------|-------------|-------------|  
|`[` *character_group* `]`|Herhangi bir tek karakterle eşleşir *character_group*. Varsayılan olarak, eşleşme büyük/küçük harf duyarlıdır.|`[ae]`|"gray" içinde "a"<br /><br /> "lane" içinde "a", "e"|  
|`[^` *character_group* `]`|Değilleme: olmayan herhangi bir tek karakterle eşleşir *character_group*. İçinde varsayılan olarak, karakterleri *character_group* büyük küçük harfe duyarlıdır.|`[^aei]`|"reign" içinde "r", "g", "n"|  
|`[` *İlk* `-` *son* `]`|Karakter aralığı: aralığında herhangi bir tek karakterle eşleşir *ilk* için *son*.|`[A-Z]`|"AB123" içinde "A", "B"|  
|`.`|Joker karakter: \n dışında herhangi bir tek karakterle eşleşir.<br /><br /> Değişmez değer nokta karakteri eşleştirmek için (. veya `\u002E`), kaçış karakteriyle gelmelidir (`\.`).|`a.e`|"nave" içinde "ave"<br /><br /> "water" içinde "ate"|  
|`\p{` *Adı* `}`|Unicode genel kategorisine veya adlandırılmış blok tarafından belirtilen herhangi bir tek karakterle eşleşir *adı*.|`\p{Lu}`<br /><br /> `\p{IsCyrillic}`|"City Lights" içinde "C", "L"<br /><br /> "ДЖem" içinde "Д", "Ж"|  
|`\P{` *Adı* `}`|Unicode genel kategorisine veya adlandırılmış blok tarafından belirtilen olmayan herhangi bir tek karakterle eşleşir *adı*.|`\P{Lu}`<br /><br /> `\P{IsCyrillic}`|"City" içinde "i", "t", "y"<br /><br /> "ДЖem" içinde "e", "m"|  
|`\w`|Sözcük olan herhangi bir karakterle eşleşir.|`\w`|"ID A1.3" içinde "I", "D", "A", "1", "3"|  
|`\W`|Sözcük olmayan herhangi bir karakterle eşleşir.|`\W`|"ID A1.3" içinde " ", "."|  
|`\s`|Boşluk olan herhangi bir karakterle eşleşir.|`\w\s`|"ID A1.3" içinde "D "|  
|`\S`|Boşluk olmayan herhangi bir karakterle eşleşir.|`\s\S`|"_" "int \__ctr"|  
|`\d`|Herhangi bir ondalık basamakla eşleşir.|`\d`|"4 = IV" içinde "4"|  
|`\D`|Bir ondalık basamak dışında herhangi bir karakterle eşleşir.|`\D`|"4 = IV" içinde " ", "=", " ", "I", "V"|  
  
 [Başa dön](#top)  
  
<a name="atomic_zerowidth_assertions"></a>   
## <a name="anchors"></a>Tutturucular  
 Yer işaretleri veya atomik sıfır genişlik onayları, dizedeki geçerli konuma bağlı olarak eşleşmenin başarılı veya başarısız olmasına neden olurlar, ancak altyapının dize boyunca ilerlemesine veya karakterleri tüketmesine neden olmazlar. Aşağıdaki tabloda listelenen meta karakterler tutturuculardır. Daha fazla bilgi için bkz: [bağlayıcılarını](../../../docs/standard/base-types/anchors-in-regular-expressions.md).  
  
|Onaylama işlemi|Açıklama|Desen|Eşleşmeler|  
|---------------|-----------------|-------------|-------------|  
|`^`|Eşleşme dizenin veya satırın başlangıcında başlamalıdır.|`^\d{3}`|"901" içinde<br /><br /> "901-333-"|  
|`$`|Eşleşme dizenin veya önce sonunda gerçekleşmelidir `\n` satırı veya dize sonunda.|`-\d{3}$`|"-333"<br /><br /> "-901-333"|  
|`\A`|Eşleşme dizenin başlangıcında gerçekleşmelidir.|`\A\d{3}`|"901" içinde<br /><br /> "901-333-"|  
|`\Z`|Eşleşme dizenin veya önce sonunda gerçekleşmelidir `\n` dizesi sonunda.|`-\d{3}\Z`|"-333"<br /><br /> "-901-333"|  
|`\z`|Eşleşme dizenin sonunda gerçekleşmelidir.|`-\d{3}\z`|"-333"<br /><br /> "-901-333"|  
|`\G`|Eşleşme önceki eşleşmenin sona erdiği noktada gerçekleşmelidir.|`\G\(\d\)`|"(1)", "(3)", "(5)" içindeki "(1) (3) (5) [7] (9\)"|  
|`\b`|Eşleşme arasında bir sınır oluşması gereken bir `\w` (alfasayısal) ve bir `\W` (alfasayısal olmayan) karakter.|`\b\w+\s\w+\b`|"them theme them them" içinde "them theme", "them them"|  
|`\B`|Eşleşme üzerinde oluşamaz bir `\b` sınır.|`\Bend\w*\b`|"end sends endure lender" içinde "ends", "ender"|  
  
 [Başa dön](#top)  
  
<a name="grouping_constructs"></a>   
## <a name="grouping-constructs"></a>Gruplandırma Yapıları  
 Yapıları gruplandırma, normal bir ifadenin alt ifadelerini açıklar ve tipik olarak bir giriş dizesinin alt dizelerini yakalar. Yapıları gruplandırma aşağıdaki tabloda listelenen dil öğelerini içerir. Daha fazla bilgi için bkz: [gruplandırma yapıları](grouping-constructs-in-regular-expressions.md).  
  
|Yapıyı gruplandırma|Açıklama|Desen|Eşleşmeler|  
|------------------------|-----------------|-------------|-------------|  
|`(` *alt* `)`|Eşleşen alt ifadeyi yakalar ve buna bir tabanlı bir sıra numarası atar.|`(\w)\1`|"deep" içinde "ee"|  
|`(?<` *ad* `>` *alt* `)`|Eşleşen alt ifadeyi adlandırılmış bir gruba yakalar.|`(?<double>\w)\k<double>`|"deep" içinde "ee"|  
|`(?<` *Ad1* `-` *ad2* `>` *alt* `)`|Bir dengeleme grubu tanımını tanımlar. Daha fazla bilgi için "Grup tanımı Dengeleme" bölümüne bakın [gruplandırma yapıları](grouping-constructs-in-regular-expressions.md).|`(((?'Open'\()[^\(\)]*)+((?'Close-Open'\))[^\(\)]*)+)*(?(Open)(?!))$`|"((1-3)\*(3-1))" içindeki "3+2^((1-3)\*(3-1))"|  
|`(?:` *alt* `)`|Yakalama yapmayan grubu tanımlar.|`Write(?:Line)?`|"Console.WriteLine()" içinde "WriteLine"<br /><br /> "Console.Write(value)" içinde "Yaz"|  
|`(?imnsx-imnsx:` *alt* `)`|İçinde belirtilen seçeneklerini devre dışı bırakır veya uygular *alt*. Daha fazla bilgi için bkz: [normal ifade seçenekleri](regular-expression-options.md).|`A\d{2}(?i:\w+)\b`|"A12xl A12XL a12xl" içinde "A12xl", "A12XL"|  
|`(?=` *alt* `)`|Sıfır genişlik pozitif ileriye yönelik onaylar.|`\w+(?=\.)`|"He is. içinde "is", "ran" ve "out" Köpek çalıştı. Güneş çıktı."|  
|`(?!` *alt* `)`|Sıfır genişlik negatif ileriye yönelik onaylar.|`\b(?!un)\w+\b`|"unsure sure unity used" içinde "sure", "used"|  
|`(?<=` *alt* `)`|Sıfır genişlik pozitif geriye yönelik onaylar.|`(?<=19)\d{2}\b`|"1851 1999 1950 1905 2003" içinde "99", "50", "05"|  
|`(?<!` *alt* `)`|Sıfır genişlik negatif geriye yönelik onaylar.|`(?<!19)\d{2}\b`|"1851 1999 1950 1905 2003" içinde "51", "03"|  
|`(?>` *alt* `)`|Geri dönüşlü olmayan (veya "greedy") alt ifade.|`[13579](?>A+B+)`|"1ABB 3ABBC 5AB 5AC" içinde "1ABB", "3ABB" ve "5AB"|  
  
 [Başa dön](#top)  
  
<a name="quantifiers"></a>   
## <a name="quantifiers"></a>Miktar Belirleyiciler  
 Niceleyici, önceki öğenin (karakter, grup veya karakter sınıfı olabilir) kaç örneğinin oluşacak eşleme için giriş dizesinde mevcut olması gerektiğini belirtir. Miktar belirleyiciler aşağıdaki tabloda listelenen dil öğelerini içerir. Daha fazla bilgi için bkz: [nicelik](quantifiers-in-regular-expressions.md).  
  
|Miktar Belirleyici|Açıklama|Desen|Eşleşmeler|  
|----------------|-----------------|-------------|-------------|  
|`*`|Önceki öğeyle sıfır kez veya daha fazla eşleşir.|`\d*\.\d`|".0", "19.9", "219.9"|  
|`+`|Önceki öğeyle bir kez veya daha fazla eşleşir.|`"be+"`|"been" içinde "bee", "bent" içinde "be"|  
|`?`|Önceki öğeyle sıfır veya bir kez eşleşir.|`"rai?n"`|"ran", "rain"|  
|`{` *N* `}`|Önceki öğesi tam olarak eşleşen *n* kez.|`",\d{3}"`|"1,043.6" içinde ",043", "9,876,543,210" içinde ",876", ",543" ve ",210"|  
|`{` *N* `,}`|Önceki öğesi en az eşleşen *n* kez.|`"\d{2,}"`|"166", "29", "1930"|  
|`{` *n* `,` *m* `}`|Önceki öğesi en az eşleşen *n* kez ancak hiçbir birden fazla *m* kez.|`"\d{3,5}"`|"166", "17668"<br /><br /> "193024" içinde "19302"|  
|`*?`|Önceki öğeyle sıfır kez veya daha fazla ancak mümkün olduğunca az eşleşir.|`\d*?\.\d`|".0", "19.9", "219.9"|  
|`+?`|Önceki öğeyle bir kez veya daha fazla ancak mümkün olduğunca az eşleşir.|`"be+?"`|"been" içinde "be", "bent" içinde "be"|  
|`??`|Önceki öğeyle sıfır veya bir kez ancak mümkün olduğunca az eşleşir.|`"rai??n"`|"ran", "rain"|  
|`{` *N* `}?`|Önceki öğesi tam olarak eşleşen *n* kez.|`",\d{3}?"`|"1,043.6" içinde ",043", "9,876,543,210" içinde ",876", ",543" ve ",210"|  
|`{` *N* `,}?`|Önceki öğesi en az eşleşen *n* kez ancak mümkün olduğunca birkaç kez.|`"\d{2,}?"`|"166", "29", "1930"|  
|`{` *n* `,` *m* `}?`|Önceki öğesi arasında eşleşen *n* ve *m* kez ancak mümkün olduğunca birkaç kez.|`"\d{3,5}?"`|"166", "17668"<br /><br /> "193024" içinde "193", "024"|  
  
 [Başa dön](#top)  
  
<a name="backreference_constructs"></a>   
## <a name="backreference-constructs"></a>Yeniden Başvuru Yapıları  
 Yeniden başvuru, aynı normal ifadede daha sonra tanımlanabilecek alt ifadeyle daha önce eşleşmesine olanak sağlar. Aşağıdaki tabloda .NET normal ifadelerde tarafından desteklenen yeniden başvuru yapıları listelenmektedir. Daha fazla bilgi için bkz: [yeniden başvuru yapıları](backreference-constructs-in-regular-expressions.md).  
  
|Yeniden başvuru yapısı|Açıklama|Desen|Eşleşmeler|  
|-----------------------------|-----------------|-------------|-------------|  
|`\` *Sayı*|Yeniden başvuru. Numaralandırılmış ifadenin değeriyle eşleşir.|`(\w)\1`|"seek" içinde "ee"|  
|`\k<` *Adı* `>`|Adlandırılan yeniden başvuru. Adlandırılmış ifadenin değeriyle eşleşir.|`(?<char>\w)\k<char>`|"seek" içinde "ee"|  
  
 [Başa dön](#top)  
  
<a name="alternation_constructs"></a>   
## <a name="alternation-constructs"></a>Değişim Yapıları  
 Değişim yapıları, ve/veya eşleştirmeyi etkinleştirmek üzere bir normal ifadeyi değiştirir. Bu yapılar aşağıdaki tabloda listelenen dil öğelerini içerir. Daha fazla bilgi için bkz: [değişim yapıları](alternation-constructs-in-regular-expressions.md).  
  
|Değişim yapısı|Açıklama|Desen|Eşleşmeler|  
|---------------------------|-----------------|-------------|-------------|  
|<code>&#124;</code>|Dikey çubukla ayrılan herhangi bir öğesiyle eşleştiğinden (&#124;) karakter.|<code>th(e&#124;is&#124;at)</code>|"this is the day" içinde "the", "this" "|  
|`(?(` *ifade* `)` *Evet* <code>&#124;</code> *yok* `)`|Eşleşen *Evet* normal ifade deseni olarak belirlendiyse *ifade* eşleşen; Aksi halde, isteğe bağlı eşleşen *hiçbir* bölümü. *ifade* Sıfır Genişlik onaylama yorumlanır.|<code>(?(A)A\d{2}\b&#124;\b\d{3}\b)</code>|"A10 C103 910" içinde "A10", "910"|  
|`(?(` *ad* `)` *Evet* <code>&#124;</code> *yok* `)`|Eşleşen *Evet* varsa *adı*, adlandırılmış ya da numaralı grup, yakalama bir eşleşmeye sahip; Aksi halde, isteğe bağlı eşleşen *hiçbir*.|<code>(?&lt;quoted&gt;&quot;)?(?(quoted).+?&quot;&#124;\S+\s)</code>|"Dogs.jpg "Yiska playing.jpg" içeriğindeki "Dogs.jpg, "Yiska playing.jpg"|  
  
 [Başa dön](#top)  
  
<a name="substitutions"></a>   
## <a name="substitutions"></a>Değişimler  
 Değişimler değiştirme desenlerinde desteklenen normal ifade dil öğeleridir. Daha fazla bilgi için bkz: [değişimler](substitutions-in-regular-expressions.md). Aşağıdaki tabloda listelenen meta karakterler atomik sıfır genişlik onaylarıdır.  
  
|Karakter|Açıklama|Desen|Değiştirme deseni|Giriş dizesi|Sonuç Dizesi|  
|---------------|-----------------|-------------|-------------------------|------------------|-------------------|  
|`$` *Sayı*|Gruplandırma ölçütü eşleşen alt dizeyi değiştirir *numarası*.|`\b(\w+)(\s)(\w+)\b`|`$3$2$1`|"one two"|"two one"|  
|`${` *Adı* `}`|Adlandırılmış grupla eşleşen alt dizeyi değiştirir *adı*.|`\b(?<word1>\w+)(\s)(?<word2>\w+)\b`|`${word2} ${word1}`|"one two"|"two one"|  
|`$$`|Değişmez değerli bir "$" işaretinin yerini alır.|`\b(\d+)\s?USD`|`$$$1`|"103 USD"|"$103"|  
|`$&`|Tam eşleşmenin bir kopyasının yerini alır.|`\$?\d*\.?\d+`|`**$&**`|"$1.30"|"\*\*$1.30\*\*"|  
|<code>$`</code>|Eşleşmeden önce giriş dizesi metninin tamamının yerini alır.|`B+`|<code>$`</code>|"AABBCC"|"AAAACC"|  
|`$'`|Eşleşmeden sonra giriş dizesi metninin tamamının yerini alır.|`B+`|`$'`|"AABBCC"|"AACCCC"|  
|`$+`|Yakalanan son grubun yerini alır.|`B+(C+)`|`$+`|"AABBCCDD"|AACCDD|  
|`$_`|Giriş dizesinin tamamının yerini alır.|`B+`|`$_`|"AABBCC"|"AAAABBCCCC"|  
  
 [Başa dön](#top)  
  
<a name="options"></a>   
## <a name="regular-expression-options"></a>Normal İfade Seçenekleri  
 Normal ifade sisteminin normal ifade modellerini nasıl denetleyeceğiyle ilgili seçenekler belirtebilirsiniz. Bu seçeneklerden çoğu olabilir ya da satır (normal ifade deseni içinde) belirtilen veya bir veya daha fazla olarak <xref:System.Text.RegularExpressions.RegexOptions> sabitleri. Bu hızlı başvuru yalnızca satır içi seçeneklerini listeler. Satır içi hakkında daha fazla bilgi ve <xref:System.Text.RegularExpressions.RegexOptions> seçenekleri başlıklı makaleye bakın [normal ifade seçenekleri](regular-expression-options.md).  
  
 Satır içi seçeneği iki şekilde belirtebilirsiniz:  
  
-   Kullanarak [çeşitli yapı](miscellaneous-constructs-in-regular-expressions.md) `(?imnsx-imnsx)`, burada bir seçenek veya seçenek kümesi önce eksi işareti (-) bu seçenekleri devre dışı bırakır. Örneğin, `(?i-mn)` büyük küçük harf duyarsız eşleşen kapatır (`i`), çok satırlı moda kapatır (`m`) kapalı ve kapatır Grup yakalamaları adlandırılmamış (`n`) devre dışı. Seçenek, seçeneğin tanımlandığı noktadan itibaren normal ifade deseni için geçerlidir ve desenin sonuna kadar ya da bir başka yapının seçeneği tersine çevirdiği noktaya kadar etkilidir.  
  
-   Kullanarak [yapı gruplandırma](grouping-constructs-in-regular-expressions.md)`(?imnsx-imnsx:`*alt*`)`, sadece belirtilen grubun seçeneklerini tanımlar.  
  
 .NET normal ifade altyapısı aşağıdaki satır içi seçeneklerini destekler.  
  
|Seçenek|Açıklama|Desen|Eşleşmeler|  
|------------|-----------------|-------------|-------------|  
|`i`|Büyük küçük harf duyarlı eşleme kullanın.|`\b(?i)a(?-i)a\w+\b`|"aardvark AAAuto aaaAuto Adam breakfast" içinde "aardvark", "aaaAuto"|  
|`m`|Çok satırlı modunu kullanın. `^` ve `$` başlangıcını ve bitişini başlangıcını ve bitişini dizenin yerine bir çizginin eşleşmesi.|Örneğin, "Çok satırlı modu" bölümüne bakın [normal ifade seçenekleri](regular-expression-options.md).||  
|`n`|Adsız grupları yakalamayın.|Örneğin, "Açık yakalar yalnızca" bölümüne bakın [normal ifade seçenekleri](regular-expression-options.md).||  
|`s`|Tek satır modunu kullanın.|Örneğin, "tek satırlı moda" bölümüne bakın [normal ifade seçenekleri](regular-expression-options.md).||  
|`x`|Normal ifade deseninde kaçışsız boşluğu yoksay.|`\b(?x) \d+ \s \w+`|"1 aardvark 2 cats IV centurions" içinde "1 aardvark", "2 cats"|  
  
 [Başa dön](#top)  
  
<a name="miscellaneous_constructs"></a>   
## <a name="miscellaneous-constructs"></a>Çeşitli Yapılar  
 Çeşitli yapılar, bir normal ifade desenini değiştirir veya bununla ilgili bilgi sağlar. Aşağıdaki tabloda .NET tarafından desteklenen çeşitli yapılar listeler. Daha fazla bilgi için bkz: [çeşitli yapıları](miscellaneous-constructs-in-regular-expressions.md).  
  
|Oluştur|Tanım|Örnek|  
|---------------|----------------|-------------|  
|`(?imnsx-imnsx)`|Büyük/küçük harfe bir desen ortasında gibi seçenekleri devre dışı bırakır veya ayarlar. Daha fazla bilgi için bkz: [normal ifade seçenekleri](regular-expression-options.md).|`\bA(?i)b\w+\b` "ABA", "ABA mümkün Act" "mümkün" ile eşleşir|  
|`(?#` *Açıklama* `)`|Satır içi açıklama. Açıklama ilk kapanış parantezinde sona erer.|`\bA(?#Matches words starting with A)\w+\b`|  
|`#` [için satır sonu]|X-mode yorumu. Açıklama atlanmayan başlatır `#` ve satırın sonuna kadar devam eder.|`(?x)\bA\w+\b#Matches words starting with A`|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Text.RegularExpressions?displayProperty=nameWithType>  
 <xref:System.Text.RegularExpressions.Regex>  
 [Normal ifadeler](regular-expressions.md)  
 [Normal ifade sınıfları](the-regular-expression-object-model.md)  
 [Normal İfade Örnekleri](regular-expression-examples.md)  
 [Normal ifadeler - hızlı başvuru (Word biçiminde de indirilebilir)](https://download.microsoft.com/download/D/2/4/D240EBF6-A9BA-4E4F-A63F-AEB6DA0B921C/Regular%20expressions%20quick%20reference.docx)  
 [Normal ifadeler - hızlı başvuru (PDF biçimli indirme)](https://download.microsoft.com/download/D/2/4/D240EBF6-A9BA-4E4F-A63F-AEB6DA0B921C/Regular%20expressions%20quick%20reference.pdf)
