---
title: Normal İfadelerdeki Karakter Sınıfları
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- character classes
- regular expressions, character classes
- characters, matching syntax
- .NET Framework regular expressions, character classes
ms.assetid: 0f8bffab-ee0d-4e0e-9a96-2b4a252bb7e4
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 241bc9756118cd2db15356dcc2c724a24c84d0fc
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="character-classes-in-regular-expressions"></a>Normal İfadelerdeki Karakter Sınıfları
<a name="Top"></a> Karakter sınıfı herhangi biri başarılı olması bir eşleştirme için giriş dizesi içinde oluşabilir karakter kümesini tanımlar. .NET normal ifade dilde şu karakter sınıflarından destekler:  
  
-   Pozitif karakter grupları. Giriş dizesindeki bir karakter, belirli bir karakter kümesindekindeki karakterlerden biriyle eşleşmelidir. Daha fazla bilgi için bkz: [pozitif karakter grubu](#PositiveGroup).  
  
-   Negatif karakter grupları. Giriş dizesindeki bir karakter, belirli bir karakter kümesindekindeki karakterlerden biriyle eşleşmemelidir. Daha fazla bilgi için bkz: [negatif karakter grubu](#NegativeGroup).  
  
-   Herhangi bir karakter. `.` (Nokta veya dönemi) karakterdir normal ifadede dışında herhangi bir karakter ile eşleşen bir joker karakter `\n`. Daha fazla bilgi için bkz: [herhangi bir karakter](#AnyCharacter).  
  
-   Genel bir Unicode kategorisi veya adlandırılmış blok. Giriş dizesindeki bir karakter, eşleşmenin başarılı olması için belirli bir Unicode kategorisinin üyesi veya bir bitişik Unicode karakterleri aralığında olmalıdır. Daha fazla bilgi için bkz: [Unicode kategori veya Unicode blok](#CategoryOrBlock).  
  
-   Negatif bir Unicode kategorisi veya adlandırılmış blok. Giriş dizesindeki bir karakter, eşleşmenin başarılı olması için belirli bir Unicode kategorisinin üyesi veya bir bitişik Unicode karakterleri aralığında olmamalıdır. Daha fazla bilgi için bkz: [negatif Unicode kategori veya Unicode blok](#NegativeCategoryOrBlock).  
  
-   Bir sözcük karakteri. Giriş dizesindeki bir karakter, sözcüklerdeki karakterler için uygun olan herhangi bir Unicode kategorisine ait olabilir. Daha fazla bilgi için bkz: [sözcük karakteriyle](#WordCharacter).  
  
-   Sözcük olmayan karakter. Giriş dizesindeki bir karakter, sözcük karakteri olmayan herhangi bir Unicode kategorisine ait olabilir. Daha fazla bilgi için bkz: [olmayan sözcük karakteriyle](#NonWordCharacter).  
  
-   Boşluk karakteri. Giriş dizesindeki bir karakter herhangi bir Unicode ayıraç karakteri veya herhangi bir denetim karakteri olabilir. Daha fazla bilgi için bkz: [boşluk karakteri](#WhitespaceCharacter).  
  
-   Boşluk olmayan karakter. Giriş dizesindeki bir karakter boşluk karakteri olmayan herhangi bir karakter olabilir. Daha fazla bilgi için bkz: [boşluk olmayan karakter](#NonWhitespaceCharacter).  
  
-   Ondalık basamak. Giriş dizesindeki bir karakter Unicode ondalık basamakları olarak sınıflandırılan karakterlerden biri olabilir. Daha fazla bilgi için bkz: [ondalık basamak karakter](#DigitCharacter).  
  
-   Ondalık olmayan basamak. Giriş dizesindeki bir karakter, bir Unicode basamak karakteri dışındaki herhangi bir karakter olabilir. Daha fazla bilgi için bkz: [ondalık basamak karakter](#NonDigitCharacter).  
  
 .NET karakter sınıfı çıkarma ifadeleri, başka bir karakter sınıftan bir karakter sınıfı hariç sonucu olarak bir karakter kümesi tanımlamanıza olanak sağlayan destekler. Daha fazla bilgi için bkz: [karakter sınıfı çıkarma](#CharacterClassSubtraction).  
  
> [!NOTE]
>  Karakter karakterlerle kategoriye göre gibi eşleşen sınıfları [\w](#WordCharacter) word karakteri eşleştirmek için veya [\p{} ](#CategoryOrBlock) Unicode kategorisine eşleşecek şekilde Bel <xref:System.Globalization.CharUnicodeInfo> bilgi sağlamak için sınıfı karakter kategorileri hakkında.  İle başlayarak [!INCLUDE[net_v462](../../../includes/net-v462-md.md)], karakter kategorileri temel [Unicode standart, sürüm 8.0.0](https://www.unicode.org/versions/Unicode8.0.0/). İçinde [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)] aracılığıyla [!INCLUDE[net_v461](../../../includes/net-v461-md.md)], esas alan [Unicode standart, sürüm 6.3.0](https://www.unicode.org/versions/Unicode6.3.0/).  
  
<a name="PositiveGroup"></a>   
## <a name="positive-character-group--"></a>Pozitif Karakter Grubu: [ ]  
 Bir pozitif karakter grubu, eşleşme olabilmesi için giriş dizesinde bulunabilecek karakterlerin listesini belirtir. Bu karakterler tek tek, bir aralık olarak veya her iki şekilde de belirtilebilir.  
  
 Karakterlerin tek tek bulunduğu bir listeyi belirtmek için kullanılan söz dizimi aşağıdaki gibidir:  
  
 [*character_group*]  
  
 Burada *character_group* başarılı olması bir eşleştirme için giriş dizesi görünebilir karakterleri tek tek bir listesi verilmiştir. *character_group* bir veya daha fazla sabit karakterleri, herhangi bir birleşimini içerebilir [kaçış karakterleri](../../../docs/standard/base-types/character-escapes-in-regular-expressions.md), ya da karakter sınıfları.  
  
 Bir karakter aralığı belirtmek için kullanılan söz dizimi aşağıdaki gibidir:  
  
```  
[firstCharacter-lastCharacter]  
```  
  
 Burada *firstCharacter* aralığı başlar karakterdir ve *lastCharacter* aralığın bittiği karakterdir. Bir karakter aralığı serideki ilk karakter, tire işareti (-) ve ardından serideki son karakterle belirtilen bitişik karakter dizisidir. İki karakter, eğer bitişik Unicode kod noktaları var ise bitişiktir.  
  
 Pozitif karakter sınıflarını içeren bazı sık kullanılan normal ifade desenleri aşağıdaki tabloda listelenmiştir.  
  
|Desen|Açıklama|  
|-------------|-----------------|  
|`[aeiou]`|Tüm sesli harflerle eşleş.|  
|`[\p{P}\d]`|Tüm noktalama işaretleriyle ve ondalık basamak işaretleriyle eşleş.|  
|`[\s\p{P}]`|Tüm boşluk veya noktalama eşleşmesi.|  
  
 Aşağıdaki örnek "a" ve "e" karakterlerini içerek bir pozitif karakterler grubu tanımlar ve eşleşmenin gerçekleşmesi için giriş dizesinde "grey" veya "gray" sözcüklerinin ardından bir sözcük daha bulunmasını gerektirir.  
  
 [!code-csharp[Conceptual.RegEx.Language.CharacterClasses#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.characterclasses/cs/positivecharclasses.cs#1)]
 [!code-vb[Conceptual.RegEx.Language.CharacterClasses#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.characterclasses/vb/positivecharclasses.vb#1)]  
  
 Normal ifade `gr[ae]y\s\S+?[\s|\p{P}]` şu şekilde tanımlanır:  
  
|Desen|Açıklama|  
|-------------|-----------------|  
|`gr`|"gr" sabit karakterleriyle eşleş.|  
|`[ae]`|Bir "a" veya "e" ile eşleş.|  
|`y\s`|"y" sabit karakteri ve ardından bir boşluk karakteriyle eşleş.|  
|`\S+?`|Bir veya daha fazla boşluk olmayan karakterle, ama olabildiğince az sayıda olanla eşleş.|  
|`[\s\p{P}]`|Bir boşluk karakteri veya noktalama işaretiyle eşleş.|  
  
 Aşağıdaki örnek büyük harf ile başlayan sözcüklerle eşleşir. Alt kullanan `[A-Z]` büyük harf aralığını A'dan Z'ye temsil etmek için.  
  
 [!code-csharp[Conceptual.RegEx.Language.CharacterClasses#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.characterclasses/cs/range.cs#3)]
 [!code-vb[Conceptual.RegEx.Language.CharacterClasses#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.characterclasses/vb/range.vb#3)]  
  
 Normal ifade `\b[A-Z]\w*\b` aşağıdaki tabloda gösterildiği gibi tanımlanır.  
  
|Desen|Açıklama|  
|-------------|-----------------|  
|`\b`|Bir sözcük sınırında başla.|  
|`[A-Z]`|A'dan Z'ye herhangi bir büyük harf karakterle eşleş.|  
|`\w*`|Sıfır veya daha fazla sözcük karakteriyle eşleş.|  
|`\b`|Bir sözcük sınırıyla eşleş.|  
  
 [Başa dön](#Top)  
  
<a name="NegativeGroup"></a>   
## <a name="negative-character-group-"></a>Negatif Karakter Grubu: [^]  
 Bir negatif karakter grubu, eşleşmenin gerçekleşmesi için giriş dizesinde bulunmaması gereken karakterlerin listesini belirtir. Karakter listesi tek tek, bir aralık olarak veya her iki şekilde de belirtilebilir.  
  
 Karakterlerin tek tek bulunduğu bir listeyi belirtmek için kullanılan söz dizimi aşağıdaki gibidir:  
  
 [*^ character_group*]  
  
 Burada *character_group* başarılı olması bir eşleştirme için giriş dizesi görünemez karakterleri tek tek bir listesi verilmiştir. *character_group* bir veya daha fazla sabit karakterleri, herhangi bir birleşimini içerebilir [kaçış karakterleri](../../../docs/standard/base-types/character-escapes-in-regular-expressions.md), ya da karakter sınıfları.  
  
 Bir karakter aralığı belirtmek için kullanılan söz dizimi aşağıdaki gibidir:  
  
 [^*firstCharacter*-*lastCharacter*]  
  
 Burada *firstCharacter* aralığı başlar karakterdir ve *lastCharacter* aralığın bittiği karakterdir. Bir karakter aralığı serideki ilk karakter, tire işareti (-) ve ardından serideki son karakterle belirtilen bitişik karakter dizisidir. İki karakter, eğer bitişik Unicode kod noktaları var ise bitişiktir.  
  
 İki veya daha fazla karakter aralığı birleştirilebilir. Örneğin, "9", küçük harf ile "f", "a" aralığı üzerinden "0" arasında ondalık basamak aralığını ve "A" ile "F" büyük harfler aralığını belirtmek için kullanın `[0-9a-fA-F]`.  
  
 Önde gelen ayar karakter (`^`) sıfırdan küçük bir karakter grubu zorunludur ve karakter grubu pozitif karakter grubu yerine bir negatif karakter grubu gösterir.  
  
> [!IMPORTANT]
>  Büyük bir normal ifade deseninde bulunan bir negatif karakter grubu, sıfır genişlikli onay değildir. Yani, normal ifade motoru negatif karakter grubunu değerlendirdikten sonra giriş dizesinde bir karakter ilerler.  
  
 Negatif karakter gruplarını içeren bazı sık kullanılan normal ifade desenleri aşağıdaki tabloda listelenmiştir.  
  
|Desen|Açıklama|  
|-------------|-----------------|  
|`[^aeiou]`|Sesli harfler dışındaki tüm karakterlerle eşleş.|  
|`[^\p{P}\d]`|Noktalama işaretleri ve ondalık basamak karakterleri dışındaki tüm karakterlerle eşleş.|  
  
 Aşağıdaki örnek "th" ile başlayan ve "o" ile devam etmeyen tüm karakterlerle eşleşir.  
  
 [!code-csharp[Conceptual.RegEx.Language.CharacterClasses#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.characterclasses/cs/negativecharclasses.cs#2)]
 [!code-vb[Conceptual.RegEx.Language.CharacterClasses#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.characterclasses/vb/negativecharclasses.vb#2)]  
  
 Normal ifade `\bth[^o]\w+\b` aşağıdaki tabloda gösterildiği gibi tanımlanır.  
  
|Desen|Açıklama|  
|-------------|-----------------|  
|`\b`|Bir sözcük sınırında başla.|  
|`th`|"th" sabit karakterleriyle eşleş.|  
|`[^o]`|"o" olmayan herhangi bir karakterle eşleş.|  
|`\w+`|Bir veya daha fazla sözcük karakteri eşleştir.|  
|`\b`|Bir sözcük sınırında bit.|  
  
 [Başa dön](#Top)  
  
<a name="AnyCharacter"></a>   
## <a name="any-character-"></a>Herhangi Bir Karakter: .  
 Nokta karakteri (.) dışında herhangi bir karakterle eşleşir `\n` (yeni satır karakteri, \u000A) aşağıdaki iki nitelikleri ile:  
  
-   Normal ifade deseni tarafından değiştirilirse <xref:System.Text.RegularExpressions.RegexOptions.Singleline?displayProperty=nameWithType> seçeneğini veya desen kısmı, içeriyorsa `.` tarafından karakter sınıfı değiştirilmiş `s` seçeneği, `.` herhangi bir karakterle eşleşir. Daha fazla bilgi için bkz: [normal ifade seçenekleri](../../../docs/standard/base-types/regular-expression-options.md).  
  
     Aşağıdaki örnekte, farklı davranışını gösterilmektedir `.` varsayılan ve ile sınıfı karakter <xref:System.Text.RegularExpressions.RegexOptions.Singleline?displayProperty=nameWithType> seçeneği. Normal ifade `^.+` dizenin başında başlar ve her bir karakterle eşleşir. Varsayılan olarak, ilk satırın sonuna eşleşme sonlandırır; Normal ifade deseni ile eşleşen satır başı karakteri `\r` veya \u000D, ancak eşleşmiyor `\n`. Çünkü <xref:System.Text.RegularExpressions.RegexOptions.Singleline?displayProperty=nameWithType> seçeneği yorumlar tek bir satır olarak tüm giriş dizesi, giriş dizesi içinde her karakterle eşleşir dahil olmak üzere `\n`.  
  
     [!code-csharp[Conceptual.Regex.Language.CharacterClasses#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.characterclasses/cs/any2.cs#5)]
     [!code-vb[Conceptual.Regex.Language.CharacterClasses#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.characterclasses/vb/any2.vb#5)]  
  
> [!NOTE]
>  Dışında herhangi bir karakter eşleştiğinden `\n`, `.` karakter sınıfı ayrıca eşleşir `\r` (satır başı karakteri, \u000D).  
  
-   Bir pozitif veya negatif karakter grubunda, nokta bir karakter sınıfı yerine sabit karakter olarak kabul edilir. Daha fazla bilgi için bkz: [pozitif karakter grubu](#PositiveGroup) ve [negatif karakter grubu](#NegativeGroup) bu konuda daha önce. Aşağıdaki örnek bir çizim nokta karakterini içeren bir normal ifade tanımlayarak sağlar (`.`) hem de bir karakter sınıfını pozitif karakter grubunun bir üyesi olarak. Normal ifade `\b.*[.?!;:](\s|\z)` word sınırında başlar, bir süre dahil olmak üzere dört noktalama işaretleri birini bulduğu kadar herhangi bir karakterle eşleşir ve ardından bir boşluk karakteri veya dize sonu ile eşleşir.  
  
     [!code-csharp[Conceptual.RegEx.Language.CharacterClasses#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.characterclasses/cs/any1.cs#4)]
     [!code-vb[Conceptual.RegEx.Language.CharacterClasses#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.characterclasses/vb/any1.vb#4)]  
  
> [!NOTE]
>  Herhangi bir karakter eşleştiğinden `.` bir normal ifade deseni birden çok kez herhangi bir karakteri eşleştirmek çalışırsa language öğesi ile yavaş niceleyici genellikle kullanılır. Daha fazla bilgi için bkz: [nicelik](../../../docs/standard/base-types/quantifiers-in-regular-expressions.md).  
  
 [Başa dön](#Top)  
  
<a name="CategoryOrBlock"></a>   
## <a name="unicode-category-or-unicode-block-p"></a>Unicode kategori veya Unicode blok: \p{}  
 Unicode standardı her karakteri genel bir kategoriye atar. Örneğin, belirli bir karakterin büyük harfe olabilir (tarafından temsil edilen `Lu` kategori), ondalık bir sayı ( `Nd` kategori), bir matematik simge ( `Sm` kategori), veya bir paragraf ayırıcı ( `Zl` kategori). Unicode standardındaki belirli karakter kümeleri ayrıca birbirini izleyen kod noktalarının belirli bir aralığını veya bloğunu kaplar. Örneğin, temel Latin karakter kümesi \u0000 ile \u007F arasındayken, Arapça karakter kümesi \u0600 ile \u06FF arasındadır.  
  
 Normal ifade yapısı  
  
 `\p{` *Adı* `}`  
  
 bir Unicode genel kategorisine veya adlandırılmış blok ait herhangi bir karakterle eşleşir nerede *adı* kategori kısaltması veya adlandırılmış blok adıdır. Kategori kısaltmalar listesi için bkz: [desteklenen Unicode genel kategorileri](#SupportedUnicodeGeneralCategories) bu konunun ilerleyen bölümlerinde. Adlandırılmış blokları listesi için bkz: [adlı blokları desteklenen](#SupportedNamedBlocks) bu konunun ilerleyen bölümlerinde.  
  
 Aşağıdaki örnek kullanır `\p{` *adı* `}` hem bir Unicode genel kategori eşleştirmek için yapı (Bu durumda, `Pd`, veya noktalama işaretleri, tire kategori) ve adlandırılmış bir blok ( `IsGreek` ve `IsBasicLatin` blokları adlı).  
  
 [!code-csharp[Conceptual.RegEx.Language.CharacterClasses#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.characterclasses/cs/category1.cs#6)]
 [!code-vb[Conceptual.RegEx.Language.CharacterClasses#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.characterclasses/vb/category1.vb#6)]  
  
 Normal ifade `\b(\p{IsGreek}+(\s)?)+\p{Pd}\s(\p{IsBasicLatin}+(\s)?)+` aşağıdaki tabloda gösterildiği gibi tanımlanır.  
  
|Desen|Açıklama|  
|-------------|-----------------|  
|`\b`|Bir sözcük sınırında başla.|  
|`\p{IsGreek}+`|Bir veya daha fazla Yunan karakterle eşleş.|  
|`(\s)?`|Sıfır veya bir beyaz boşluk karakterini eşleştirin.|  
|`(\p{IsGreek}+(\s)?)+`|Bir veya birden çok Yunanca karakter desenini, ardından sıfır veya bir beyaz alan karakteri bir veya birden çok kez gelecek şekilde eşleştirin.|  
|`\p{Pd}`|Bir Punctuation, Dash karakteriyle eşleş.|  
|`\s`|Bir boşluk karakteri ile eşleştirin.|  
|`\p{IsBasicLatin}+`|Bir veya daha fazla temel Latin karakteriyle eşleş.|  
|`(\s)?`|Sıfır veya bir beyaz boşluk karakterini eşleştirin.|  
|`(\p{IsBasicLatin}+(\s)?)+`|Bir veya daha fazla kere, bir veya daha fazla temel Latin karakterinin ardından sıfır veya bir boşluk karakteri deseniyle eşleş.|  
  
 [Başa dön](#Top)  
  
<a name="NegativeCategoryOrBlock"></a>   
## <a name="negative-unicode-category-or-unicode-block-p"></a>Negatif Unicode kategori veya Unicode blok: \P{}  
 Unicode standardı her karakteri genel bir kategoriye atar. Örneğin, belirli bir karakterin büyük harfe olabilir (tarafından temsil edilen `Lu` kategori), ondalık bir sayı ( `Nd` kategori), bir matematik simge ( `Sm` kategori), veya bir paragraf ayırıcı ( `Zl` kategori). Unicode standardındaki belirli karakter kümeleri ayrıca birbirini izleyen kod noktalarının belirli bir aralığını veya bloğunu kaplar. Örneğin, temel Latin karakter kümesi \u0000 ile \u007F arasındayken, Arapça karakter kümesi \u0600 ile \u06FF arasındadır.  
  
 Normal ifade yapısı  
  
 `\P{` *Adı* `}`  
  
 bir Unicode genel kategori veya adlandırılmış blok ait olmayan herhangi bir karakterle eşleşir nerede *adı* kategori kısaltması veya adlandırılmış blok adıdır. Kategori kısaltmalar listesi için bkz: [desteklenen Unicode genel kategorileri](#SupportedUnicodeGeneralCategories) bu konunun ilerleyen bölümlerinde. Adlandırılmış blokları listesi için bkz: [adlı blokları desteklenen](#SupportedNamedBlocks) bu konunun ilerleyen bölümlerinde.  
  
 Aşağıdaki örnek kullanır `\P{` *adı* `}` hiçbir para birimi simgesini kaldırmak için yapı (Bu durumda, `Sc`, veya sembol, para birimi kategori) sayısal dizelerden.  
  
 [!code-csharp[Conceptual.RegEx.Language.CharacterClasses#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.characterclasses/cs/notcategory1.cs#7)]
 [!code-vb[Conceptual.RegEx.Language.CharacterClasses#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.characterclasses/vb/notcategory1.vb#7)]  
  
 Normal ifade deseni `(\P{Sc})+` eşleşen bir veya daha fazla karakter para birimi simgeleri olmayan; etkili bir şekilde sonuç dizesini herhangi para birimi simgesini kaldırır.  
  
 [Başa dön](#Top)  
  
<a name="WordCharacter"></a>   
## <a name="word-character-w"></a>Sözcük Karakteri: \w  
 `\w` herhangi bir sözcük karakterle eşleşir. Bir sözcük karakteri, aşağıdaki tabloda listelenen Unicode kategorilerinin herhangi birinin üyesidir.  
  
|Kategori|Açıklama|  
|--------------|-----------------|  
|Ll|Harf, Küçük Harf|  
|Lu|Harf, Büyük Harf|  
|Lt|Harf, Başlık Düzeni|  
|Lo|Harf, Diğer|  
|Lm|Harf, Değiştirici|  
|Sütun|İşaret, Boşluksuz|  
|Nd|Sayı, Ondalık Basamak|  
|Pc|Noktalama, Bağlayıcı. Bu kategori on karakter içerir ve bu karakterlerin en sık kullanılanı alt çizgi karakteridir (_), u+005F.|  
  
 ECMAScript uyumlu davranış belirtilirse, `\w` eşdeğerdir `[a-zA-Z_0-9]`. "ECMAScript eşleşen davranışı" bölümünde ECMAScript normal ifadeler hakkında daha fazla bilgi için bkz: [normal ifade seçenekleri](../../../docs/standard/base-types/regular-expression-options.md).  
  
> [!NOTE]
>  Herhangi bir sözcük karakteri eşleştiğinden `\w` bir normal ifade deseni birden çok kez herhangi bir sözcük karakteri eşleştirmek belirli word karakterin ardından çalışırsa language öğesi ile yavaş niceleyici genellikle kullanılır. Daha fazla bilgi için bkz: [nicelik](../../../docs/standard/base-types/quantifiers-in-regular-expressions.md).  
  
 Aşağıdaki örnek kullanır `\w` language öğesi bir sözcük yinelenen karakteri eşleştirmek için. Örnek bir normal ifade deseni tanımlayan `(\w)\1`, hangi yorumlayabilir gibi.  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|(\w)|Bir sözcük karakteriyle eşleş. Bu ilk yakalama grubudur.|  
|\1|İlk yakalamanın değeriyle eşleş.|  
  
 [!code-csharp[Conceptual.RegEx.Language.CharacterClasses#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.characterclasses/cs/wordchar1.cs#8)]
 [!code-vb[Conceptual.RegEx.Language.CharacterClasses#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.characterclasses/vb/wordchar1.vb#8)]  
  
 [Başa dön](#Top)  
  
<a name="NonWordCharacter"></a>   
## <a name="non-word-character-w"></a>Sözcük Olmayan Karakter: \W  
 `\W` herhangi bir sözcük dışı karakterle eşleşir. \W dil öğesi aşağıdaki karakter sınıfıyla eşdeğerdir:  
  
```  
[^\p{Ll}\p{Lu}\p{Lt}\p{Lo}\p{Nd}\p{Pc}\p{Lm}]  
```  
  
 Diğer bir deyişle, aşağıdaki tabloda listelenen Unicode kategorilerindeki olanlar dışında herhangi bir karakterle eşleşir.  
  
|Kategori|Açıklama|  
|--------------|-----------------|  
|Ll|Harf, Küçük Harf|  
|Lu|Harf, Büyük Harf|  
|Lt|Harf, Başlık Düzeni|  
|Lo|Harf, Diğer|  
|Lm|Harf, Değiştirici|  
|Sütun|İşaret, Boşluksuz|  
|Nd|Sayı, Ondalık Basamak|  
|Pc|Noktalama, Bağlayıcı. Bu kategori on karakter içerir ve bu karakterlerin en sık kullanılanı alt çizgi karakteridir (_), u+005F.|  
  
 ECMAScript uyumlu davranış belirtilirse, `\W` eşdeğerdir `[^a-zA-Z_0-9]`. "ECMAScript eşleşen davranışı" bölümünde ECMAScript normal ifadeler hakkında daha fazla bilgi için bkz: [normal ifade seçenekleri](../../../docs/standard/base-types/regular-expression-options.md).  
  
> [!NOTE]
>  Herhangi bir sözcük olmayan karakteri eşleştiğinden `\W` bir normal ifade deseni birden çok kez belirli bir sözcük olmayan karakterin ardından herhangi bir sözcük olmayan karakteri eşleştirmek çalışırsa language öğesi ile yavaş niceleyici genellikle kullanılır. Daha fazla bilgi için bkz: [nicelik](../../../docs/standard/base-types/quantifiers-in-regular-expressions.md).  
  
 Aşağıdaki örnek gösterilmektedir `\W` karakter sınıfı.  Normal ifade deseni tanımlayan `\b(\w+)(\W){1,2}`, bir veya iki word olmayan karakter, boşluk veya noktalama gibi arkasından bir sözcük eşleşir. Normal ifade aşağıdaki tabloda gösterildiği gibi yorumlanır.  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|\b|Bir sözcük sınırında eşleşmeye başla.|  
|(\w+)|Bir veya daha fazla sözcük karakteri eşleştir. Bu ilk yakalama grubudur.|  
|(\W){1,2}|Sözcük olmayan bir karakteri bir veya iki kez eşleştir. Bu ikinci yakalama grubudur.|  
  
 [!code-csharp[Conceptual.RegEx.Language.CharacterClasses#9](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.characterclasses/cs/nonwordchar1.cs#9)]
 [!code-vb[Conceptual.RegEx.Language.CharacterClasses#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.characterclasses/vb/nonwordchar1.vb#9)]  
  
 Çünkü <xref:System.Text.RegularExpressions.Group> ikinci yakalama grubu için nesne içeren tek bir sözcük olmayan karakter yakalanan yalnızca, tüm yakalanan word olmayan karakterler örnek alır <xref:System.Text.RegularExpressions.CaptureCollection> tarafından döndürülen nesne <xref:System.Text.RegularExpressions.Group.Captures%2A?displayProperty=nameWithType> özelliği.  
  
 [Başa dön](#Top)  
  
<a name="WhitespaceCharacter"></a>   
## <a name="white-space-character-s"></a>Boşluk Karakteri: \s  
 `\s` herhangi bir boşluk karakteri ile eşleşir. Aşağıdaki tabloda listelenen kaçış dizileri ve Unicode kategorileriyle eşdeğerdir.  
  
|Kategori|Açıklama|  
|--------------|-----------------|  
|`\f`|Sonraki sayfaya geçme karakteri, \u000C.|  
|`\n`|Yeni satır karakteri, \u000A.|  
|`\r`|Satır başı karakteri, \u000D.|  
|`\t`|Sekme karakteri, \u0009.|  
|`\v`|Dikey sekme karakteri, \u000B.|  
|`\x85`|Üç nokta veya sonraki satır (NEL) karakteri (...), \u0085.|  
|`\p{Z}`|Herhangi bir ayıraç karakterle eşleşir.|  
  
 ECMAScript uyumlu davranış belirtilirse, `\s` eşdeğerdir `[ \f\n\r\t\v]`. "ECMAScript eşleşen davranışı" bölümünde ECMAScript normal ifadeler hakkında daha fazla bilgi için bkz: [normal ifade seçenekleri](../../../docs/standard/base-types/regular-expression-options.md).  
  
 Aşağıdaki örnek gösterilmektedir `\s` karakter sınıfı. Normal ifade deseni tanımlayan `\b\w+(e)?s(\s|$)`, "s" veya "es ardından bir boşluk karakteri veya giriş dizesi sonuna" biten bir sözcük eşleşir. Normal ifade aşağıdaki tabloda gösterildiği gibi yorumlanır.  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|\b|Bir sözcük sınırında eşleşmeye başla.|  
|\w+|Bir veya daha fazla sözcük karakteri eşleştir.|  
|(e)?|Sıfır veya bir kez "e" ile eşleş.|  
|s|Bir "s" ile eşleş.|  
|(\s&#124;$)|Eşleşen bir boşluk karakteri veya giriş dize sonu.|  
  
 [!code-csharp[Conceptual.RegEx.Language.CharacterClasses#10](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.characterclasses/cs/whitespace1.cs#10)]
 [!code-vb[Conceptual.RegEx.Language.CharacterClasses#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.characterclasses/vb/whitespace1.vb#10)]  
  
 [Başa dön](#Top)  
  
<a name="NonWhitespaceCharacter"></a>   
## <a name="non-white-space-character-s"></a>Boşluk Olmayan Karakter: \S  
 `\S` herhangi bir boşluk olmayan karakterle eşleşir. Eşdeğer olan `[^\f\n\r\t\v\x85\p{Z}]` normal ifade deseni ya da eşdeğer olan normal ifade deseni karşıtı `\s`, boşluk karakterleri eşleştirir. Daha fazla bilgi için bkz: [boşluk karakteri: \s](#WhitespaceCharacter).  
  
 ECMAScript uyumlu davranış belirtilirse, `\S` eşdeğerdir `[^ \f\n\r\t\v]`. "ECMAScript eşleşen davranışı" bölümünde ECMAScript normal ifadeler hakkında daha fazla bilgi için bkz: [normal ifade seçenekleri](../../../docs/standard/base-types/regular-expression-options.md).  
  
 Aşağıdaki örnek gösterilmektedir `\S` language öğesi. Normal ifade deseni `\b(\S+)\s?` boşluk karakterleriyle sınırlandırılır dizelerle eşleşir. Eşleşme'nın ikinci öğe <xref:System.Text.RegularExpressions.GroupCollection> nesne eşleşen dize içeriyor. Normal ifade aşağıdaki tabloda gösterildiği gibi yorumlanabilir.  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|`\b`|Bir sözcük sınırında eşleşmeye başla.|  
|`(\S+)`|Bir veya daha fazla boşluk olmayan karakterle eşleş. Bu ilk yakalama grubudur.|  
|`\s?`|Sıfır veya bir beyaz boşluk karakterini eşleştirin.|  
  
 [!code-csharp[Conceptual.RegEx.Language.CharacterClasses#11](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.characterclasses/cs/nonwhitespace1.cs#11)]
 [!code-vb[Conceptual.RegEx.Language.CharacterClasses#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.characterclasses/vb/nonwhitespace1.vb#11)]  
  
 [Başa dön](#Top)  
  
<a name="DigitCharacter"></a>   
## <a name="decimal-digit-character-d"></a>Ondalık Basamak Karakteri: \d  
 `\d` herhangi bir ondalık basamak eşleşir. Eşdeğer olan `\p{Nd}` standart ondalık basamak 0-9 ve bunun yanı sıra diğer karakter kümesi sayısı, ondalık basamak içeren normal ifade deseni.  
  
 ECMAScript uyumlu davranış belirtilirse, `\d` eşdeğerdir `[0-9]`. "ECMAScript eşleşen davranışı" bölümünde ECMAScript normal ifadeler hakkında daha fazla bilgi için bkz: [normal ifade seçenekleri](../../../docs/standard/base-types/regular-expression-options.md).  
  
 Aşağıdaki örnek gösterilmektedir `\d` language öğesi. Bir giriş dizesinin Amerika Birleşik Devletleri ve Kanada'da geçerli bir telefon numarası olup olmadığını test eder. Normal ifade deseni `^(\(?\d{3}\)?[\s-])?\d{3}-\d{4}$` aşağıdaki tabloda gösterildiği gibi tanımlanır.  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|`^`|Giriş dizesinin başında eşleşmeye başla.|  
|`\(?`|Sıfır veya bir sabit "(" karakteriyle eşleş.|  
|`\d{3}`|Üç ondalık basamakla eşleş.|  
|`\)?`|Sıfır veya bir sabit ")" karakteriyle eşleş.|  
|`[\s-]`|Bir tire veya boşluk karakteriyle eşleş.|  
|`(\(?\d{3}\)?[\s-])?`|İsteğe bağlı olarak bir açma parantezi, üç ondalık basamak ve bir kapatma parantezi; ardından da sıfır veya bir kere bir boşluk karakteri veya tire ile eşleş. Bu ilk yakalama grubudur.|  
|`\d{3}-\d{4}`|Üç ondalık basamak, ardından bir tire ve sonra dört tane daha ondalık basamak ile eşleş.|  
|`$`|Giriş dizesinin sonuyla eşleş.|  
  
 [!code-csharp[Conceptual.RegEx.Language.CharacterClasses#12](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.characterclasses/cs/digit1.cs#12)]
 [!code-vb[Conceptual.RegEx.Language.CharacterClasses#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.characterclasses/vb/digit1.vb#12)]  
  
 [Başa dön](#Top)  
  
<a name="NonDigitCharacter"></a>   
## <a name="non-digit-character-d"></a>Rakam Olmayan Karakter: \D  
 `\D` herhangi bir rakam olmayan karakterle eşleşir. Eşdeğer olan `\P{Nd}` normal ifade deseni.  
  
 ECMAScript uyumlu davranış belirtilirse, `\D` eşdeğerdir `[^0-9]`. "ECMAScript eşleşen davranışı" bölümünde ECMAScript normal ifadeler hakkında daha fazla bilgi için bkz: [normal ifade seçenekleri](../../../docs/standard/base-types/regular-expression-options.md).  
  
 Aşağıdaki örnek, \D dil öğesini gösterir. Parça numarası gibi bir dizenin doğru ondalık ve ondalık olmayan karakter birleşimini içerip içermediğini test eder. Normal ifade deseni `^\D\d{1,5}\D*$` aşağıdaki tabloda gösterildiği gibi tanımlanır.  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|`^`|Giriş dizesinin başında eşleşmeye başla.|  
|`\D`|Basamak olmayan bir karakterle eşleş.|  
|`\d{1,5}`|Bir ile beş tane arasında ondalık basamakla eşleş.|  
|`\D*`|Sıfır, bir veya daha fazla ondalık olmayan karakter eşleşmesi.|  
|`$`|Giriş dizesinin sonuyla eşleş.|  
  
 [!code-csharp[Conceptual.RegEx.Language.CharacterClasses#13](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.characterclasses/cs/nondigit1.cs#13)]
 [!code-vb[Conceptual.RegEx.Language.CharacterClasses#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.characterclasses/vb/nondigit1.vb#13)]  
  
 [Başa dön](#Top)  
  
<a name="SupportedUnicodeGeneralCategories"></a>   
## <a name="supported-unicode-general-categories"></a>Desteklenen Unicode Genel Kategorileri  
 Unicode aşağıdaki tabloda listelenen genel kategorileri tanımlar. Konumundaki "UCD dosya biçimi" ve "Genel kategori değerler" konuları daha fazla bilgi için bkz: [Unicode karakter veritabanı](https://www.unicode.org/reports/tr44/).  
  
|Kategori|Açıklama|  
|--------------|-----------------|  
|`Lu`|Harf, Büyük Harf|  
|`Ll`|Harf, Küçük Harf|  
|`Lt`|Harf, Başlık Düzeni|  
|`Lm`|Harf, Değiştirici|  
|`Lo`|Harf, Diğer|  
|`L`|Tüm harf karakterler. Bu içerir `Lu`, `Ll`, `Lt`, `Lm`, ve `Lo` karakter.|  
|`Mn`|İşaret, Boşluksuz|  
|`Mc`|İşaret, Boşluklu Birleşik|  
|`Me`|İşaret, Çevreleyen|  
|`M`|Tüm aksan işaretleri. Bu içerir `Mn`, `Mc`, ve `Me` kategoriler.|  
|`Nd`|Sayı, Ondalık Basamak|  
|`Nl`|Sayı, Harf|  
|`No`|Sayı, Diğer|  
|`N`|Tüm sayılar. Bu içerir `Nd`, `Nl`, ve `No` kategoriler.|  
|`Pc`|Noktalama, Bağlayıcı|  
|`Pd`|Noktalama, Tire|  
|`Ps`|Noktalama, Açık|  
|`Pe`|Noktalama, Kapalı|  
|`Pi`|Noktalama, Açılış tırnağı (kullanıma göre Ps veya Pe gibi davranabilir)|  
|`Pf`|Noktalama, Kapanış tırnağı (kullanıma göre Ps veya Pe gibi davranabilir)|  
|`Po`|Noktalama, Diğer|  
|`P`|Tüm noktalama işaretleri. Bu içerir `Pc`, `Pd`, `Ps`, `Pe`, `Pi`, `Pf`, ve `Po` kategoriler.|  
|`Sm`|Sembol, Matematik|  
|`Sc`|Sembol, Para Birimi|  
|`Sk`|Sembol, Değiştirici|  
|`So`|Sembol, Diğer|  
|`S`|Tüm semboller. Bu içerir `Sm`, `Sc`, `Sk`, ve `So` kategoriler.|  
|`Zs`|Ayırıcı, Boşluk|  
|`Zl`|Ayırıcı, Satır|  
|`Zp`|Ayırıcı, Paragraf|  
|`Z`|Tüm ayırıcı karakterlerler. Bu içerir `Zs`, `Zl`, ve `Zp` kategoriler.|  
|`Cc`|Diğer, Denetim|  
|`Cf`|Diğer, Biçim|  
|`Cs`|Diğer, Yedek Karakter|  
|`Co`|Diğer, Özel Kullanım|  
|`Cn`|Diğer, Atanmamış (hiçbir karakter bu özelliğe sahip değildir)|  
|`C`|Tüm denetim karakterleri. Bu içerir `Cc`, `Cf`, `Cs`, `Co`, ve `Cn` kategoriler.|  
  
 Bu karakteri geçirerek herhangi bir karakterin Unicode kategorisi belirleyebilirsiniz <xref:System.Char.GetUnicodeCategory%2A> yöntemi. Aşağıdaki örnek kullanır <xref:System.Char.GetUnicodeCategory%2A> seçili Latin karakterler içeren bir dizi her bir öğesinde kategorisini belirlemek amacıyla yöntemi.  
  
 [!code-csharp[Conceptual.RegEx.Language.CharacterClasses#14](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.characterclasses/cs/getunicodecategory1.cs#14)]
 [!code-vb[Conceptual.RegEx.Language.CharacterClasses#14](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.characterclasses/vb/getunicodecategory1.vb#14)]  
  
 [Başa dön](#Top)  
  
<a name="SupportedNamedBlocks"></a>   
## <a name="supported-named-blocks"></a>Desteklenen Adlandırılmış Bloklar  
 .NET aşağıdaki tabloda listelenen adlandırılmış blokları sağlar. Desteklenen adlandırılmış bloklar kümesi Unicode 4.0 ve Perl 5.6'yı temel alır.  
  
|Kod noktası aralığı|Blok adı|  
|----------------------|----------------|  
|0000 - 007F|`IsBasicLatin`|  
|0080 - 00FF|`IsLatin-1Supplement`|  
|0100 - 017F|`IsLatinExtended-A`|  
|0180 - 024F|`IsLatinExtended-B`|  
|0250 - 02AF|`IsIPAExtensions`|  
|02B0 - 02FF|`IsSpacingModifierLetters`|  
|0300 - 036F|`IsCombiningDiacriticalMarks`|  
|0370 - 03FF|`IsGreek`<br /><br /> -veya-<br /><br /> `IsGreekandCoptic`|  
|0400 - 04FF|`IsCyrillic`|  
|0500 - 052F|`IsCyrillicSupplement`|  
|0530 - 058F|`IsArmenian`|  
|0590 - 05FF|`IsHebrew`|  
|0600 - 06FF|`IsArabic`|  
|0700 - 074F|`IsSyriac`|  
|0780 - 07BF|`IsThaana`|  
|0900 - 097F|`IsDevanagari`|  
|0980 - 09FF|`IsBengali`|  
|0A00 - 0A7F|`IsGurmukhi`|  
|0A80 - 0AFF|`IsGujarati`|  
|0B00 - 0B7F|`IsOriya`|  
|0B80 - 0BFF|`IsTamil`|  
|0C00 - 0C7F|`IsTelugu`|  
|0C80 - 0CFF|`IsKannada`|  
|0D00 - 0D7F|`IsMalayalam`|  
|0D80 - 0DFF|`IsSinhala`|  
|0E00 - 0E7F|`IsThai`|  
|0E80 - 0EFF|`IsLao`|  
|0F00 - 0FFF|`IsTibetan`|  
|1000 - 109F|`IsMyanmar`|  
|10A0 - 10FF|`IsGeorgian`|  
|1100 - 11FF|`IsHangulJamo`|  
|1200 - 137F|`IsEthiopic`|  
|13A0 - 13FF|`IsCherokee`|  
|1400 - 167F|`IsUnifiedCanadianAboriginalSyllabics`|  
|1680 - 169F|`IsOgham`|  
|16A0 - 16FF|`IsRunic`|  
|1700 - 171F|`IsTagalog`|  
|1720 - 173F|`IsHanunoo`|  
|1740 - 175F|`IsBuhid`|  
|1760 - 177F|`IsTagbanwa`|  
|1780 - 17FF|`IsKhmer`|  
|1800 - 18AF|`IsMongolian`|  
|1900 - 194F|`IsLimbu`|  
|1950 - 197F|`IsTaiLe`|  
|19E0 - 19FF|`IsKhmerSymbols`|  
|1D00 - 1D7F|`IsPhoneticExtensions`|  
|1E00 - 1EFF|`IsLatinExtendedAdditional`|  
|1F00 - 1FFF|`IsGreekExtended`|  
|2000 - 206F|`IsGeneralPunctuation`|  
|2070 - 209F|`IsSuperscriptsandSubscripts`|  
|20A0 - 20CF|`IsCurrencySymbols`|  
|20D0 - 20FF|`IsCombiningDiacriticalMarksforSymbols`<br /><br /> -veya-<br /><br /> `IsCombiningMarksforSymbols`|  
|2100 - 214F|`IsLetterlikeSymbols`|  
|2150 - 218F|`IsNumberForms`|  
|2190 - 21FF|`IsArrows`|  
|2200 - 22FF|`IsMathematicalOperators`|  
|2300 - 23FF|`IsMiscellaneousTechnical`|  
|2400 - 243F|`IsControlPictures`|  
|2440 - 245F|`IsOpticalCharacterRecognition`|  
|2460 - 24FF|`IsEnclosedAlphanumerics`|  
|2500 - 257F|`IsBoxDrawing`|  
|2580 - 259F|`IsBlockElements`|  
|25A0 - 25FF|`IsGeometricShapes`|  
|2600 - 26FF|`IsMiscellaneousSymbols`|  
|2700 - 27BF|`IsDingbats`|  
|27C0 - 27EF|`IsMiscellaneousMathematicalSymbols-A`|  
|27F0 - 27FF|`IsSupplementalArrows-A`|  
|2800 - 28FF|`IsBraillePatterns`|  
|2900 - 297F|`IsSupplementalArrows-B`|  
|2980 - 29FF|`IsMiscellaneousMathematicalSymbols-B`|  
|2A00 - 2AFF|`IsSupplementalMathematicalOperators`|  
|2B00 - 2BFF|`IsMiscellaneousSymbolsandArrows`|  
|2E80 - 2EFF|`IsCJKRadicalsSupplement`|  
|2F00 - 2FDF|`IsKangxiRadicals`|  
|2FF0 - 2FFF|`IsIdeographicDescriptionCharacters`|  
|3000 - 303F|`IsCJKSymbolsandPunctuation`|  
|3040 - 309F|`IsHiragana`|  
|30A0 - 30FF|`IsKatakana`|  
|3100 - 312F|`IsBopomofo`|  
|3130 - 318F|`IsHangulCompatibilityJamo`|  
|3190 - 319F|`IsKanbun`|  
|31A0 - 31BF|`IsBopomofoExtended`|  
|31F0 - 31FF|`IsKatakanaPhoneticExtensions`|  
|3200 - 32FF|`IsEnclosedCJKLettersandMonths`|  
|3300 - 33FF|`IsCJKCompatibility`|  
|3400 - 4DBF|`IsCJKUnifiedIdeographsExtensionA`|  
|4DC0 - 4DFF|`IsYijingHexagramSymbols`|  
|4E00 - 9FFF|`IsCJKUnifiedIdeographs`|  
|A000 - A48F|`IsYiSyllables`|  
|A490 - A4CF|`IsYiRadicals`|  
|AC00 - D7AF|`IsHangulSyllables`|  
|D800 - DB7F|`IsHighSurrogates`|  
|DB80 - DBFF|`IsHighPrivateUseSurrogates`|  
|DC00 - DFFF|`IsLowSurrogates`|  
|E000 - F8FF|`IsPrivateUse` Veya `IsPrivateUseArea`|  
|F900 - FAFF|`IsCJKCompatibilityIdeographs`|  
|FB00 - FB4F|`IsAlphabeticPresentationForms`|  
|FB50 - FDFF|`IsArabicPresentationForms-A`|  
|FE00 - FE0F|`IsVariationSelectors`|  
|FE20 - FE2F|`IsCombiningHalfMarks`|  
|FE30 - FE4F|`IsCJKCompatibilityForms`|  
|FE50 - FE6F|`IsSmallFormVariants`|  
|FE70 - FEFF|`IsArabicPresentationForms-B`|  
|FF00 - FFEF|`IsHalfwidthandFullwidthForms`|  
|FFF0 - FFFF|`IsSpecials`|  
  
 [Başa dön](#Top)  
  
<a name="CharacterClassSubtraction"></a>   
## <a name="character-class-subtraction-basegroup---excludedgroup"></a>Karakter Sınıfı Çıkarma: [base_group - [excluded_group]]  
 Bir karakter sınıfı bir karakter kümesini tanımlar. Karakter sınıfı çıkarma, bir karakter sınıfındaki karakterlerin başka bir karakter sınıfından dışlanmasının sonucu olan bir karakter kümesi döndürür.  
  
 Bir karakter sınıfı çıkarma ifadesi aşağıdaki biçime sahiptir:  
  
 `[` *base_group* `-[` *excluded_group* `]]`  
  
 Köşeli ayraç (`[]`) ve tire (`-`) zorunludur. *Base_group* olan bir [pozitif karakter grubu](#PositiveGroup) veya [negatif karakter grubu](#NegativeGroup). *Excluded_group* bileşenidir başka bir olumlu veya olumsuz karakter grubu ya da başka bir karakter sınıfı çıkarma ifade (diğer bir deyişle, karakter sınıfı çıkarma ifadeleri geçirebilmenize).  
  
 Örneğin, "a" - "z" karakter aralığından oluşan bir temel grubunuz olduğunu varsayalım. "M" karakter dışında temel grubundan oluşur karakter kümesini tanımlamak için `[a-z-[m]]`. Karakter "d", "j" ve "p" kümesi dışında temel grubundan oluşur karakter kümesini tanımlamak için `[a-z-[djp]]`. "P" ile "m" karakter aralıktan hariç temel grubundan oluşur karakter kümesini tanımlamak için `[a-z-[m-p]]`.  
  
 İç içe karakter sınıfı çıkarma ifade göz önünde bulundurun `[a-z-[d-w-[m-o]]]`. İfade en içteki karakter aralığından dışa doğru değerlendirilir. İlk önce, "m" - "o" karakter aralığı "d" - "w" karakter aralığından çıkarılır ve bunun sonucunda "d" ile "l" ve "p" ile "w" arasındaki karakterlerin kümesi oluşur. Set sonra "a" karakter aralığından gelen "karakter kümesini veren Z'den", çıkartıldığını `[abcmnoxyz]`.  
  
 Karakter sınıfı çıkarma işleminden herhangi bir karakter sınıfını kullanabilirsiniz. Boşluk karakterleri dışında \uFFFF aracılığıyla \u0000 tüm Unicode karakterler içeren karakter kümesini tanımlamak için (`\s`), noktalama genel kategori karakterleri (`\p{P}`), karakter `IsGreek` adlı blok (`\p{IsGreek}`), ve Unicode sonraki SATIRA denetim karakteri (\x85) `[\u0000-\uFFFF-[\s\p{P}\p{IsGreek}\x85]]`.  
  
 Karakter sınıflarını yararlı sonuçlar verecek bir karakter sınıfı çıkarma ifadesi için seçin. Hiçbir şeyle eşleşmeyen boş bir karakter kümesi oluşturan veya orijinal temel gruba eşdeğer olan ifadelerden kaçının. Örneğin, boş küme ifadesi sonucudur `[\p{IsBasicLatin}-[\x00-\x7F]]`, içindeki tüm karakterleri çıkarır `IsBasicLatin` karakter aralığından `IsBasicLatin` genel kategorisi. Benzer şekilde, özgün temel Grup ifadesi sonucudur `[a-z-[0-9]]`.  Bunun sebebi, "a" - "z" arasındaki karakterleri içeren temel grubun, "0" - "9" arasındaki ondalık basamakları içeren çıkarılan gruptaki hiçbir karakteri içermemesidir.  
  
 Aşağıdaki örnek, normal bir ifade tanımlar `^[0-9-[2468]]+$`, sıfır ile eşleşen ve tek basamak giriş dizesi içinde.  Normal ifade aşağıdaki tabloda gösterildiği gibi yorumlanır.  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|^|Giriş dizesinin başında eşleşmeyi başlat.|  
|`[0-9-[2468]]+`|0 ile 9 arasında; 2, 4, 6 ve 8 dışındaki herhangi bir karakter bir veya daha fazla bulunduğunda eşleş. Başka bir deyişle, sıfır veya bir tek basamakla eşleş.|  
|$|Giriş dizesinin sonunda eşleşmeyi bitir.|  
  
 [!code-csharp[Conceptual.RegEx.Language.CharacterClasses#15](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.characterclasses/cs/classsubtraction1.cs#15)]
 [!code-vb[Conceptual.RegEx.Language.CharacterClasses#15](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.characterclasses/vb/classsubtraction1.vb#15)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Char.GetUnicodeCategory%2A>  
 [Normal İfade Dili - Hızlı Başvuru](../../../docs/standard/base-types/regular-expression-language-quick-reference.md)  
 [Normal İfade Seçenekleri](../../../docs/standard/base-types/regular-expression-options.md)
