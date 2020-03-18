---
title: .NET Normal İfadelerde Karakter Sınıfları
description: .NET normal ifadelerinde bir karakter kümesini temsil etmek için karakter sınıflarını nasıl kullanacağınızı öğrenin.
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
ms.openlocfilehash: 07bd63c90bc8d78c9831e2007695a232a85111b1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "78159344"
---
# <a name="character-classes-in-regular-expressions"></a>Normal ifadelerdeki karakter sınıfları

Bir karakter sınıfı, bir eşleşmenin başarılı olması için giriş dizesinde bulunabilecek karakterleri içeren bir karakter kümesi tanımlar. .NET'teki normal ifade dili aşağıdaki karakter sınıflarını destekler:  
  
- Pozitif karakter grupları. Giriş dizesindeki bir karakter, belirli bir karakter kümesindekindeki karakterlerden biriyle eşleşmelidir. Daha fazla bilgi için [Pozitif Karakter Grubu'na](#PositiveGroup)bakın.  
  
- Negatif karakter grupları. Giriş dizesindeki bir karakter, belirli bir karakter kümesindekindeki karakterlerden biriyle eşleşmemelidir. Daha fazla bilgi için [Negatif Karakter Grubu'na](#NegativeGroup)bakın.  
  
- Herhangi bir karakter. Normal `.` bir ifadedeki (nokta veya nokta) karakter, `\n`hariç herhangi bir karakterle eşleşen bir joker karakterdir. Daha fazla bilgi için [Herhangi Bir Karakter'e](#AnyCharacter)bakın.  
  
- Genel bir Unicode kategorisi veya adlandırılmış blok. Giriş dizesindeki bir karakter, eşleşmenin başarılı olması için belirli bir Unicode kategorisinin üyesi veya bir bitişik Unicode karakterleri aralığında olmalıdır. Daha fazla bilgi için [Unicode Kategorisi veya Unicode Bloğu'na](#CategoryOrBlock)bakın.  
  
- Negatif bir Unicode kategorisi veya adlandırılmış blok. Giriş dizesindeki bir karakter, eşleşmenin başarılı olması için belirli bir Unicode kategorisinin üyesi veya bir bitişik Unicode karakterleri aralığında olmamalıdır. Daha fazla bilgi için [Negatif Unicode Kategorisi veya Unicode Bloğu'na](#NegativeCategoryOrBlock)bakın.  
  
- Bir sözcük karakteri. Giriş dizesindeki bir karakter, sözcüklerdeki karakterler için uygun olan herhangi bir Unicode kategorisine ait olabilir. Daha fazla bilgi için [Word Karakteri'ne](#WordCharacter)bakın.  
  
- Sözcük olmayan karakter. Giriş dizesindeki bir karakter, sözcük karakteri olmayan herhangi bir Unicode kategorisine ait olabilir. Daha fazla bilgi için Word [Olmayan Karakter'e](#NonWordCharacter)bakın.  
  
- Boşluk karakteri. Giriş dizesindeki bir karakter herhangi bir Unicode ayıraç karakteri veya herhangi bir denetim karakteri olabilir. Daha fazla bilgi için [Beyaz Boşluk Karakteri'ne](#WhitespaceCharacter)bakın.  
  
- Boşluk olmayan karakter. Giriş dizesindeki bir karakter boşluk karakteri olmayan herhangi bir karakter olabilir. Daha fazla bilgi için Beyaz [Olmayan Boşluk Karakteri'ne](#NonWhitespaceCharacter)bakın.  
  
- Ondalık basamak. Giriş dizesindeki bir karakter Unicode ondalık basamakları olarak sınıflandırılan karakterlerden biri olabilir. Daha fazla bilgi için bkz: [Ondalık Basamak Karakteri.](#DigitCharacter)  
  
- Ondalık olmayan basamak. Giriş dizesindeki bir karakter, bir Unicode basamak karakteri dışındaki herhangi bir karakter olabilir. Daha fazla bilgi için bkz: [Ondalık Basamak Karakteri.](#NonDigitCharacter)  
  
 .NET, bir karakter sınıfını başka bir karakter sınıfından dışlamanın sonucu olarak bir karakter kümesi tanımlamanızı sağlayan karakter sınıfı çıkarma ifadelerini destekler. Daha fazla bilgi için [Bkz. Karakter Sınıfı Çıkarma.](#CharacterClassSubtraction)  
  
> [!NOTE]
> Karakter kategorilerine göre eşleşen karakter sınıfları [,sözcük](#WordCharacter) karakterlerini eşleştirmek için \w veya Unicode kategorisiyle eşleşecek [{} \p,](#CategoryOrBlock) karakter kategorileri hakkında bilgi sağlamak için <xref:System.Globalization.CharUnicodeInfo> sınıfa güvenir.  .NET Framework 4.6.2 ile başlayarak, karakter [kategorileri Unicode Standardı, Sürüm 8.0.0'a](https://www.unicode.org/versions/Unicode8.0.0/)göre dir. .NET Framework 4.6.1 ile .NET Framework 4'te, [Unicode Standardı, Sürüm 6.3.0'a](https://www.unicode.org/versions/Unicode6.3.0/)dayanmaktadır.  
  
<a name="PositiveGroup"></a>
## <a name="positive-character-group--"></a>Pozitif karakter grubu: [ ]  
 Bir pozitif karakter grubu, eşleşme olabilmesi için giriş dizesinde bulunabilecek karakterlerin listesini belirtir. Bu karakterler tek tek, bir aralık olarak veya her iki şekilde de belirtilebilir.  
  
 Karakterlerin tek tek bulunduğu bir listeyi belirtmek için kullanılan söz dizimi aşağıdaki gibidir:  

`[*character_group*]`

 *character_group* bir eşleşmenin başarılı olması için giriş dizesinde görünebilecek tek tek karakterlerin listesidir. *character_group* bir veya daha fazla edebi karakter, [kaçış karakterleri](../../../docs/standard/base-types/character-escapes-in-regular-expressions.md)veya karakter sınıfları herhangi bir kombinasyonu oluşabilir.  
  
 Bir karakter aralığı belirtmek için kullanılan söz dizimi aşağıdaki gibidir:  
  
`[firstCharacter-lastCharacter]`  
  
 *burada firstCharacter* aralığı başlatan karakter ve *lastCharacter* aralığı sona erdileyen karakterdir. Bir karakter aralığı serideki ilk karakter, tire işareti (-) ve ardından serideki son karakterle belirtilen bitişik karakter dizisidir. İki karakter, eğer bitişik Unicode kod noktaları var ise bitişiktir. *firstCharacter* alt kod noktasına sahip karakter olmalı ve *lastCharacter* daha yüksek kod noktasına sahip karakter olmalıdır.

> [!NOTE]
> Pozitif karakter grubu hem bir karakter kümesini hem de karakter aralığını`-`içerebildiği için, tire karakteri ( ) grubun ilk veya son karakteri olmadığı sürece her zaman aralık ayırıcısı olarak yorumlanır.

Pozitif karakter sınıflarını içeren bazı sık kullanılan normal ifade desenleri aşağıdaki tabloda listelenmiştir.  
  
|Desen|Açıklama|  
|-------------|-----------------|  
|`[aeiou]`|Tüm sesli harflerle eşleş.|  
|`[\p{P}\d]`|Tüm noktalama işaretleriyle ve ondalık basamak işaretleriyle eşleş.|  
|`[\s\p{P}]`|Tüm beyaz boşluk ve noktalama maç.|  
  
 Aşağıdaki örnek "a" ve "e" karakterlerini içerek bir pozitif karakterler grubu tanımlar ve eşleşmenin gerçekleşmesi için giriş dizesinde "grey" veya "gray" sözcüklerinin ardından bir sözcük daha bulunmasını gerektirir.  
  
 [!code-csharp[Conceptual.RegEx.Language.CharacterClasses#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.characterclasses/cs/positivecharclasses.cs#1)]
 [!code-vb[Conceptual.RegEx.Language.CharacterClasses#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.characterclasses/vb/positivecharclasses.vb#1)]  
  
 Normal ifade `gr[ae]y\s\S+?[\s|\p{P}]` aşağıdaki gibi tanımlanır:  
  
|Desen|Açıklama|  
|-------------|-----------------|  
|`gr`|"gr" sabit karakterleriyle eşleş.|  
|`[ae]`|Bir "a" veya "e" ile eşleş.|  
|`y\s`|"y" sabit karakteri ve ardından bir boşluk karakteriyle eşleş.|  
|`\S+?`|Bir veya daha fazla boşluk olmayan karakterle, ama olabildiğince az sayıda olanla eşleş.|  
|`[\s\p{P}]`|Bir boşluk karakteri veya noktalama işaretiyle eşleş.|  
  
 Aşağıdaki örnek büyük harf ile başlayan sözcüklerle eşleşir. A'dan Z'ye büyük harf aralığını temsil etmek için alt ifadeyi `[A-Z]` kullanır.  
  
 [!code-csharp[Conceptual.RegEx.Language.CharacterClasses#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.characterclasses/cs/range.cs#3)]
 [!code-vb[Conceptual.RegEx.Language.CharacterClasses#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.characterclasses/vb/range.vb#3)]  
  
 Normal ifade `\b[A-Z]\w*\b` aşağıdaki tabloda gösterildiği gibi tanımlanır.  
  
|Desen|Açıklama|  
|-------------|-----------------|  
|`\b`|Bir sözcük sınırında başla.|  
|`[A-Z]`|A'dan Z'ye herhangi bir büyük harf karakterle eşleş.|  
|`\w*`|Sıfır veya daha fazla sözcük karakteriyle eşleş.|  
|`\b`|Bir sözcük sınırıyla eşleş.|  
  
<a name="NegativeGroup"></a>
## <a name="negative-character-group-"></a>Negatif karakter grubu: [^]  
 Bir negatif karakter grubu, eşleşmenin gerçekleşmesi için giriş dizesinde bulunmaması gereken karakterlerin listesini belirtir. Karakter listesi tek tek, bir aralık olarak veya her iki şekilde de belirtilebilir.  
  
Karakterlerin tek tek bulunduğu bir listeyi belirtmek için kullanılan söz dizimi aşağıdaki gibidir:  

`[*^character_group*]`

 *character_group,* bir eşleşmenin başarılı olması için giriş dizesinde görünemeyen tek tek karakterlerin listesidir. *character_group* bir veya daha fazla edebi karakter, [kaçış karakterleri](../../../docs/standard/base-types/character-escapes-in-regular-expressions.md)veya karakter sınıfları herhangi bir kombinasyonu oluşabilir.  
  
 Bir karakter aralığı belirtmek için kullanılan söz dizimi aşağıdaki gibidir:  

`[^*firstCharacter*-*lastCharacter*]`

*burada firstCharacter* aralığı başlatan karakter ve *lastCharacter* aralığı sona erdileyen karakterdir. Bir karakter aralığı serideki ilk karakter, tire işareti (-) ve ardından serideki son karakterle belirtilen bitişik karakter dizisidir. İki karakter, eğer bitişik Unicode kod noktaları var ise bitişiktir. *firstCharacter* alt kod noktasına sahip karakter olmalı ve *lastCharacter* daha yüksek kod noktasına sahip karakter olmalıdır.

> [!NOTE]
> Negatif karakter grubu hem bir karakter kümesini hem de karakter aralığını`-`içerebildiği için, tire karakteri ( ) grubun ilk veya son karakteri olmadığı sürece her zaman aralık ayırıcısı olarak yorumlanır.
  
 İki veya daha fazla karakter aralığı birleştirilebilir. Örneğin, ondalık basamak aralığını belirtmek için "0" ile "9" arasında, "a"dan "f"e kadar küçük harflerin aralığı nı ve "A"dan "F"e kadar olan büyük harflerin aralığını kullanın. `[0-9a-fA-F]`  
  
 Negatif karakter grubundaki`^`önde gelen caret karakteri ( ) zorunludur ve karakter grubunun pozitif karakter grubu yerine negatif karakter grubu olduğunu gösterir.  
  
> [!IMPORTANT]
> Büyük bir normal ifade deseninde bulunan bir negatif karakter grubu, sıfır genişlikli onay değildir. Yani, normal ifade motoru negatif karakter grubunu değerlendirdikten sonra giriş dizesinde bir karakter ilerler.  
  
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
  
<a name="AnyCharacter"></a>
## <a name="any-character-"></a>Herhangi bir karakter: .  
 Dönem karakteri (.) aşağıdaki `\n` iki nitelik le (yeni çizgi karakteri, \u000A) dışında herhangi bir karakterle eşleşir:  
  
- Normal bir ifade deseni <xref:System.Text.RegularExpressions.RegexOptions.Singleline?displayProperty=nameWithType> seçenek tarafından değiştirilirse veya `.` karakter sınıfını içeren desen `s` bölümü `.` seçenek tarafından değiştirilirse, herhangi bir karakterle eşleşir. Daha fazla bilgi için [Düzenli İfade Seçenekleri'ne](../../../docs/standard/base-types/regular-expression-options.md)bakın.  
  
     Aşağıdaki örnekte, varsayılan olarak `.` ve seçenekle karakter <xref:System.Text.RegularExpressions.RegexOptions.Singleline?displayProperty=nameWithType> sınıfının farklı davranışını gösterin. Normal ifade `^.+` dize başında başlar ve her karakter eşleşir. Varsayılan olarak, eşleşme ilk satırın sonunda sona erer; normal ifade deseni satır başı `\r` karakteriyle veya \u000D `\n`ile eşleşir, ancak bu durum . <xref:System.Text.RegularExpressions.RegexOptions.Singleline?displayProperty=nameWithType> Seçenek tüm giriş dizesini tek bir satır olarak yorumladığı için, giriş dizesindeki her karakterle `\n`eşleşir.  
  
     [!code-csharp[Conceptual.Regex.Language.CharacterClasses#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.characterclasses/cs/any2.cs#5)]
     [!code-vb[Conceptual.Regex.Language.CharacterClasses#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.characterclasses/vb/any2.vb#5)]  
  
> [!NOTE]
> Dışında herhangi bir `\n`karakter `.` eşleştiğinden, `\r` karakter sınıfı da eşleşir (satır başı karakteri, \u000D).  
  
- Bir pozitif veya negatif karakter grubunda, nokta bir karakter sınıfı yerine sabit karakter olarak kabul edilir. Daha fazla bilgi için bu konunun başında [Pozitif Karakter Grubu](#PositiveGroup) ve Negatif Karakter [Grubu'na](#NegativeGroup) bakın. Aşağıdaki örnek, hem karakter sınıfı hem de pozitif karakter`.`grubunun bir üyesi olarak dönem karakterini içeren normal bir ifade tanımlayarak bir illüstrasyon sağlar. Normal ifade `\b.*[.?!;:](\s|\z)` bir sözcük sınırında başlar, bir noktalama işaretinden biriyle karşılaşAna kadar herhangi bir karakterle eşleşir ve sonra bir beyaz boşluk karakteriyle veya dize sonuyla eşleşir.  
  
     [!code-csharp[Conceptual.RegEx.Language.CharacterClasses#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.characterclasses/cs/any1.cs#4)]
     [!code-vb[Conceptual.RegEx.Language.CharacterClasses#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.characterclasses/vb/any1.vb#4)]  
  
> [!NOTE]
> Herhangi bir karakterle `.` eşleştiğinden, normal bir ifade deseni herhangi bir karakteri birden çok kez eşleştirmeye çalışırsa, dil öğesi genellikle tembel bir niceleme ile kullanılır. Daha fazla bilgi için, [bkz.](../../../docs/standard/base-types/quantifiers-in-regular-expressions.md)  
  
<a name="CategoryOrBlock"></a>
## <a name="unicode-category-or-unicode-block-p"></a>Unicode kategori veya Unicode blok: \p{}  
 Unicode standardı her karakteri genel bir kategoriye atar. Örneğin, belirli bir karakter büyük `Lu` harf (kategoriye göre temsil edilir), ondalık basamak `Nd` (kategori), `Sm` matematik sembolü (kategori) `Zl` veya paragraf ayırıcısı (kategori) olabilir. Unicode standardındaki belirli karakter kümeleri ayrıca birbirini izleyen kod noktalarının belirli bir aralığını veya bloğunu kaplar. Örneğin, temel Latin karakter kümesi \u0000 ile \u007F arasındayken, Arapça karakter kümesi \u0600 ile \u06FF arasındadır.  
  
 Normal ifade yapısı  
  
 `\p{`*isim*`}`  
  
 ad kategori kısaltması veya adlandırılmış blok adı *olan* Unicode genel kategorisine veya adlandırılmış bloğa ait herhangi bir karakterle eşleşir. Kategori kısaltmaları listesi için, bu konunun ilerleyen bölümlerinde [desteklenen Unicode Genel Kategoriler](#SupportedUnicodeGeneralCategories) bölümüne bakın. Adlandırılmış blokların listesi için, bu konunun ilerleyen bölümlerinde [desteklenen Adlandırılmış Bloklar](#SupportedNamedBlocks) bölümüne bakın.  
  
 Aşağıdaki örnek, `\p{`hem Unicode genel kategorisi (bu `Pd`durumda, veya Noktalama, Tire kategorisi) hem de adlandırılmış `IsGreek` `IsBasicLatin` bir bloğu (ve adlı blokları) eşleştirmek için *ad* `}` yapısını kullanır.  
  
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
  
<a name="NegativeCategoryOrBlock"></a>
## <a name="negative-unicode-category-or-unicode-block-p"></a>Negatif Unicode kategorisi veya Unicode bloğu: \P{}  
 Unicode standardı her karakteri genel bir kategoriye atar. Örneğin, belirli bir karakter büyük `Lu` harf (kategoriye göre temsil edilir), ondalık basamak `Nd` (kategori), `Sm` matematik sembolü (kategori) `Zl` veya paragraf ayırıcısı (kategori) olabilir. Unicode standardındaki belirli karakter kümeleri ayrıca birbirini izleyen kod noktalarının belirli bir aralığını veya bloğunu kaplar. Örneğin, temel Latin karakter kümesi \u0000 ile \u007F arasındayken, Arapça karakter kümesi \u0600 ile \u06FF arasındadır.  
  
 Normal ifade yapısı  
  
 `\P{`*isim*`}`  
  
 ad kategori kısaltması veya adlandırılmış blok adı *olan* Unicode genel kategorisine veya adlandırılmış bloğa ait olmayan herhangi bir karakterle eşleşir. Kategori kısaltmaları listesi için, bu konunun ilerleyen bölümlerinde [desteklenen Unicode Genel Kategoriler](#SupportedUnicodeGeneralCategories) bölümüne bakın. Adlandırılmış blokların listesi için, bu konunun ilerleyen bölümlerinde [desteklenen Adlandırılmış Bloklar](#SupportedNamedBlocks) bölümüne bakın.  
  
 Aşağıdaki örnek, `\P{`sayısal dizelerden herhangi bir para birimi `Sc`simgesini (bu durumda, , veya Sembol, Para Birimi kategorisi) kaldırmak için *ad* `}` yapısını kullanır.  
  
 [!code-csharp[Conceptual.RegEx.Language.CharacterClasses#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.characterclasses/cs/notcategory1.cs#7)]
 [!code-vb[Conceptual.RegEx.Language.CharacterClasses#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.characterclasses/vb/notcategory1.vb#7)]  
  
 Normal ifade `(\P{Sc})+` deseni, para birimi sembolü olmayan bir veya daha fazla karakterle eşleşir; herhangi bir para birimi simgesini sonuç dizesinden etkili bir şekilde sıyırıyor.  
  
<a name="WordCharacter"></a>
## <a name="word-character-w"></a>Kelime karakteri: \w  
 `\w`herhangi bir kelime karakteri yle eşleşir. Bir sözcük karakteri, aşağıdaki tabloda listelenen Unicode kategorilerinin herhangi birinin üyesidir.  
  
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
  
 ECMAScript uyumlu davranış belirtilirse, `\w` `[a-zA-Z_0-9]`'ye eşdeğerdir. ECMAScript normal ifadeleri hakkında bilgi [için, Normal İfade Seçenekleri'ndeki](../../../docs/standard/base-types/regular-expression-options.md)"ECMAScript Eşleştirme Davranışı" bölümüne bakın.  
  
> [!NOTE]
> Herhangi bir sözcük karakteriyle eşleştiğinden, normal bir ifade deseni herhangi bir sözcük karakterini birden çok kez eşleştirmeye çalışırsa ve ardından belirli bir sözcük karakteri yle birlikte `\w` dil öğesi genellikle tembel bir niceleme ile kullanılır. Daha fazla bilgi için, [bkz.](../../../docs/standard/base-types/quantifiers-in-regular-expressions.md)  
  
 Aşağıdaki örnek, `\w` sözcükteki yinelenen karakterleri eşleştirmek için dil öğesini kullanır. Örnek, `(\w)\1`aşağıdaki gibi yorumlanabilecek normal bir ifade deseni tanımlar.  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|(\w)|Bir sözcük karakteriyle eşleş. Bu ilk yakalama grubudur.|  
|\1|İlk yakalamanın değeriyle eşleş.|  
  
 [!code-csharp[Conceptual.RegEx.Language.CharacterClasses#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.characterclasses/cs/wordchar1.cs#8)]
 [!code-vb[Conceptual.RegEx.Language.CharacterClasses#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.characterclasses/vb/wordchar1.vb#8)]  
  
<a name="NonWordCharacter"></a>
## <a name="non-word-character-w"></a>Sözcük dışı karakter: \W  
 `\W`sözcük içermeyen karakterlerle eşleşir. \W dil öğesi aşağıdaki karakter sınıfıyla eşdeğerdir:  
  
`[^\p{Ll}\p{Lu}\p{Lt}\p{Lo}\p{Nd}\p{Pc}\p{Lm}]`  
  
 Başka bir deyişle, aşağıdaki tabloda listelenen Unicode kategorilerinde olanlar dışında herhangi bir karakter eşleşir.  
  
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
  
 ECMAScript uyumlu davranış belirtilirse, `\W` `[^a-zA-Z_0-9]`'ye eşdeğerdir. ECMAScript normal ifadeleri hakkında bilgi [için, Normal İfade Seçenekleri'ndeki](../../../docs/standard/base-types/regular-expression-options.md)"ECMAScript Eşleştirme Davranışı" bölümüne bakın.  
  
> [!NOTE]
> Sözcük dışı herhangi bir karakterle eşleştiğinden, normal bir ifade deseni sözcük olmayan herhangi bir karakteri birden çok kez eşleştirmeye çalışırsa, `\W` dil öğesi genellikle tembel bir nicelemeile kullanılır ve ardından belirli bir sözcük dışı karakter kullanılır. Daha fazla bilgi için, [bkz.](../../../docs/standard/base-types/quantifiers-in-regular-expressions.md)  
  
 Aşağıdaki örnek, karakter `\W` sınıfını göstermektedir.  Normal bir ifade deseni `\b(\w+)(\W){1,2}`tanımlar, beyaz boşluk veya noktalama gibi bir veya iki sözcük olmayan karakter, ardından bir sözcük eşleşen. Normal ifade aşağıdaki tabloda gösterildiği gibi yorumlanır.  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|\b|Bir sözcük sınırında eşleşmeye başla.|  
|(\w+)|Bir veya daha fazla sözcük karakteri eşleştir. Bu ilk yakalama grubudur.|  
|(\W){1,2}|Sözcük olmayan bir karakteri bir veya iki kez eşleştir. Bu ikinci yakalama grubudur.|  
  
 [!code-csharp[Conceptual.RegEx.Language.CharacterClasses#9](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.characterclasses/cs/nonwordchar1.cs#9)]
 [!code-vb[Conceptual.RegEx.Language.CharacterClasses#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.characterclasses/vb/nonwordchar1.vb#9)]  
  
 İkinci <xref:System.Text.RegularExpressions.Group> yakalama grubunun nesnesi yalnızca tek bir yakalanan sözcük olmayan karakter içerdiğinden, örnek, <xref:System.Text.RegularExpressions.CaptureCollection> <xref:System.Text.RegularExpressions.Group.Captures%2A?displayProperty=nameWithType> yakalanan tüm sözcük olmayan karakterleri özellik tarafından döndürülen nesneden alır.  
  
<a name="WhitespaceCharacter"></a>
## <a name="whitespace-character-s"></a>Beyaz boşluk karakteri: \s  
 `\s`herhangi bir whitespace karakteriyle eşleşir. Aşağıdaki tabloda listelenen kaçış dizileri ve Unicode kategorileriyle eşdeğerdir.  
  
|Kategori|Açıklama|  
|--------------|-----------------|  
|`\f`|Sonraki sayfaya geçme karakteri, \u000C.|  
|`\n`|Yeni satır karakteri, \u000A.|  
|`\r`|Satır başı karakteri, \u000D.|  
|`\t`|Sekme karakteri, \u0009.|  
|`\v`|Dikey sekme karakteri, \u000B.|  
|`\x85`|Üç nokta veya sonraki satır (NEL) karakteri (...), \u0085.|  
|`\p{Z}`|Herhangi bir ayıraç karakterle eşleşir.|  
  
 ECMAScript uyumlu davranış belirtilirse, `\s` `[ \f\n\r\t\v]`'ye eşdeğerdir. ECMAScript normal ifadeleri hakkında bilgi [için, Normal İfade Seçenekleri'ndeki](../../../docs/standard/base-types/regular-expression-options.md)"ECMAScript Eşleştirme Davranışı" bölümüne bakın.  
  
 Aşağıdaki örnek, karakter `\s` sınıfını göstermektedir. "s" veya "es" ile biten bir sözcüğü nsonucu beyaz boşluk karakteri veya giriş dizesinin sonu ile eşleşen normal bir ifade deseni `\b\w+(e)?s(\s|$)`tanımlar. Normal ifade aşağıdaki tabloda gösterildiği gibi yorumlanır.  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|\b|Bir sözcük sınırında eşleşmeye başla.|  
|\w+|Bir veya daha fazla sözcük karakteri eşleştir.|  
|(e)?|Sıfır veya bir kez "e" ile eşleş.|  
|s|Bir "s" ile eşleş.|  
|(\s&#124;$)|Bir beyaz boşluk karakterini veya giriş dizesinin sonunu eşleştirin.|  
  
 [!code-csharp[Conceptual.RegEx.Language.CharacterClasses#10](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.characterclasses/cs/whitespace1.cs#10)]
 [!code-vb[Conceptual.RegEx.Language.CharacterClasses#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.characterclasses/vb/whitespace1.vb#10)]  
  
<a name="NonWhitespaceCharacter"></a>
## <a name="non-whitespace-character-s"></a>Beyazolmayan karakter: \S  
 `\S`herhangi bir beyaz boşluk olmayan karakter eşleşir. `[^\f\n\r\t\v\x85\p{Z}]` Normal ifade desenine veya beyaz alan karakterleriyle eşleşen normal `\s`ifade desenine eşdeğerdir. Daha fazla bilgi için [Bkz. Beyaz Boşluk Karakteri: \s.](#WhitespaceCharacter)  
  
 ECMAScript uyumlu davranış belirtilirse, `\S` `[^ \f\n\r\t\v]`'ye eşdeğerdir. ECMAScript normal ifadeleri hakkında bilgi [için, Normal İfade Seçenekleri'ndeki](../../../docs/standard/base-types/regular-expression-options.md)"ECMAScript Eşleştirme Davranışı" bölümüne bakın.  
  
 Aşağıdaki örnekte `\S` dil öğesi gösterilmektedir. Normal ifade `\b(\S+)\s?` deseni, beyaz alan karakterleri ile sınırlandırılmış dizeleri eşleşir. Eşleşmenin <xref:System.Text.RegularExpressions.GroupCollection> nesnesindeki ikinci öğe eşleşen dizeyi içerir. Normal ifade aşağıdaki tabloda gösterildiği gibi yorumlanabilir.  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|`\b`|Bir sözcük sınırında eşleşmeye başla.|  
|`(\S+)`|Bir veya daha fazla boşluk olmayan karakterle eşleş. Bu ilk yakalama grubudur.|  
|`\s?`|Sıfır veya bir beyaz boşluk karakterini eşleştirin.|  
  
 [!code-csharp[Conceptual.RegEx.Language.CharacterClasses#11](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.characterclasses/cs/nonwhitespace1.cs#11)]
 [!code-vb[Conceptual.RegEx.Language.CharacterClasses#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.characterclasses/vb/nonwhitespace1.vb#11)]  
  
<a name="DigitCharacter"></a>
## <a name="decimal-digit-character-d"></a>Ondalık basamak karakteri: \d  
 `\d`herhangi bir ondalık basamakla eşleşir. Standart ondalık `\p{Nd}` basamak 0-9'un yanı sıra diğer karakter kümelerinin ondalık basamaklarını içeren normal ifade desenine eşdeğerdir.  
  
 ECMAScript uyumlu davranış belirtilirse, `\d` `[0-9]`'ye eşdeğerdir. ECMAScript normal ifadeleri hakkında bilgi [için, Normal İfade Seçenekleri'ndeki](../../../docs/standard/base-types/regular-expression-options.md)"ECMAScript Eşleştirme Davranışı" bölümüne bakın.  
  
 Aşağıdaki örnekte `\d` dil öğesi gösterilmektedir. Bir giriş dizesinin Amerika Birleşik Devletleri ve Kanada'da geçerli bir telefon numarası olup olmadığını test eder. Normal ifade `^(\(?\d{3}\)?[\s-])?\d{3}-\d{4}$` deseni aşağıdaki tabloda gösterildiği gibi tanımlanır.  
  
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
  
<a name="NonDigitCharacter"></a>
## <a name="non-digit-character-d"></a>Basamaksız karakter: \D  
 `\D`herhangi bir rakamsız karakter eşleşir. Normal ifade desenine `\P{Nd}` eşdeğerdir.  
  
 ECMAScript uyumlu davranış belirtilirse, `\D` `[^0-9]`'ye eşdeğerdir. ECMAScript normal ifadeleri hakkında bilgi [için, Normal İfade Seçenekleri'ndeki](../../../docs/standard/base-types/regular-expression-options.md)"ECMAScript Eşleştirme Davranışı" bölümüne bakın.  
  
 Aşağıdaki örnek, \D dil öğesini gösterir. Parça numarası gibi bir dizenin doğru ondalık ve ondalık olmayan karakter birleşimini içerip içermediğini test eder. Normal ifade `^\D\d{1,5}\D*$` deseni aşağıdaki tabloda gösterildiği gibi tanımlanır.  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|`^`|Giriş dizesinin başında eşleşmeye başla.|  
|`\D`|Basamak olmayan bir karakterle eşleş.|  
|`\d{1,5}`|Bir ile beş tane arasında ondalık basamakla eşleş.|  
|`\D*`|Sıfır, bir veya daha fazla ondalık olmayan karakterleri eşleştirin.|  
|`$`|Giriş dizesinin sonuyla eşleş.|  
  
 [!code-csharp[Conceptual.RegEx.Language.CharacterClasses#13](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.characterclasses/cs/nondigit1.cs#13)]
 [!code-vb[Conceptual.RegEx.Language.CharacterClasses#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.characterclasses/vb/nondigit1.vb#13)]  
  
<a name="SupportedUnicodeGeneralCategories"></a>
## <a name="supported-unicode-general-categories"></a>Desteklenen Unicode genel kategorileri  
 Unicode aşağıdaki tabloda listelenen genel kategorileri tanımlar. Daha fazla bilgi için [Unicode Karakter Veritabanı'ndaki](https://www.unicode.org/reports/tr44/)"UCD Dosya Biçimi" ve "Genel Kategori Değerleri" alt başlıklarına bakın.  
  
|Kategori|Açıklama|  
|--------------|-----------------|  
|`Lu`|Harf, Büyük Harf|  
|`Ll`|Harf, Küçük Harf|  
|`Lt`|Harf, Başlık Düzeni|  
|`Lm`|Harf, Değiştirici|  
|`Lo`|Harf, Diğer|  
|`L`|Tüm harf karakterler. `Lu`Bu, , `Ll` `Lt`, `Lm`, `Lo` ve karakterleri içerir.|  
|`Mn`|İşaret, Boşluksuz|  
|`Mc`|İşaret, Boşluklu Birleşik|  
|`Me`|İşaret, Çevreleyen|  
|`M`|Tüm aksan işaretleri. Bu `Mn`, `Mc`ve `Me` kategorileriçerir.|  
|`Nd`|Sayı, Ondalık Basamak|  
|`Nl`|Sayı, Harf|  
|`No`|Sayı, Diğer|  
|`N`|Tüm sayılar. Bu `Nd`, `Nl`ve `No` kategorileriçerir.|  
|`Pc`|Noktalama, Bağlayıcı|  
|`Pd`|Noktalama, Tire|  
|`Ps`|Noktalama, Açık|  
|`Pe`|Noktalama, Kapalı|  
|`Pi`|Noktalama, Açılış tırnağı (kullanıma göre Ps veya Pe gibi davranabilir)|  
|`Pf`|Noktalama, Kapanış tırnağı (kullanıma göre Ps veya Pe gibi davranabilir)|  
|`Po`|Noktalama, Diğer|  
|`P`|Tüm noktalama işaretleri. `Pc`Bu, , `Pd` `Ps`, `Pe` `Pi`, `Pf`, `Po` , ve kategorileri içerir.|  
|`Sm`|Sembol, Matematik|  
|`Sc`|Sembol, Para Birimi|  
|`Sk`|Sembol, Değiştirici|  
|`So`|Sembol, Diğer|  
|`S`|Tüm semboller. `Sm`Bu, , `Sc` `Sk`, `So` ve kategorileri içerir.|  
|`Zs`|Ayırıcı, Boşluk|  
|`Zl`|Ayırıcı, Satır|  
|`Zp`|Ayırıcı, Paragraf|  
|`Z`|Tüm ayırıcı karakterlerler. Bu `Zs`, `Zl`ve `Zp` kategorileriçerir.|  
|`Cc`|Diğer, Denetim|  
|`Cf`|Diğer, Biçim|  
|`Cs`|Diğer, Yedek Karakter|  
|`Co`|Diğer, Özel Kullanım|  
|`Cn`|Diğer, Atanmamış (hiçbir karakter bu özelliğe sahip değildir)|  
|`C`|Tüm denetim karakterleri. `Cc`Bu, , `Cf` `Cs`, `Co`, `Cn` ve kategorileri içerir.|  
  
 Belirli bir karakterin Unicode kategorisini, <xref:System.Char.GetUnicodeCategory%2A> bu karakteri yönteme geçirerek belirleyebilirsiniz. Aşağıdaki örnek, <xref:System.Char.GetUnicodeCategory%2A> seçili Latin karakterleri içeren bir dizideki her öğenin kategorisini belirlemek için yöntemi kullanır.  
  
 [!code-csharp[Conceptual.RegEx.Language.CharacterClasses#14](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.characterclasses/cs/getunicodecategory1.cs#14)]
 [!code-vb[Conceptual.RegEx.Language.CharacterClasses#14](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.characterclasses/vb/getunicodecategory1.vb#14)]  
  
<a name="SupportedNamedBlocks"></a>
## <a name="supported-named-blocks"></a>Desteklenen adlandırılmış bloklar

.NET aşağıdaki tabloda listelenen adlandırılmış blokları sağlar. Desteklenen adlandırılmış bloklar kümesi Unicode 4.0 ve Perl 5.6'yı temel alır. Adlandırılmış blokları kullanan normal bir ifade için [Unicode kategorisine \\{} veya Unicode bloğuna bakın: p](#unicode-category-or-unicode-block-p) bölümü.  
  
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
|E000 - F8FF|`IsPrivateUse` veya `IsPrivateUseArea`|  
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
  
<a name="CharacterClassSubtraction"></a>
## <a name="character-class-subtraction-base_group---excluded_group"></a>Karakter sınıfı çıkarma: [base_group - [excluded_group]]  
 Bir karakter sınıfı bir karakter kümesini tanımlar. Karakter sınıfı çıkarma, bir karakter sınıfındaki karakterlerin başka bir karakter sınıfından dışlanmasının sonucu olan bir karakter kümesi döndürür.  
  
 Bir karakter sınıfı çıkarma ifadesi aşağıdaki biçime sahiptir:  
  
 `[`*base_group* `-[` *excluded_group*`]]`  
  
 Kare parantez (`[]`) ve`-`tire ( ) zorunludur. *base_group* [pozitif](#PositiveGroup) karakter grubu veya negatif [karakter grubudur.](#NegativeGroup) *excluded_group* bileşeni başka bir pozitif veya negatif karakter grubu veya başka bir karakter sınıfı çıkarma ifadesidir (diğer bir şekilde karakter sınıfı çıkarma ifadelerini iç içe bulabilirsiniz).  
  
 Örneğin, "a" - "z" karakter aralığından oluşan bir temel grubunuz olduğunu varsayalım. "m" karakteri dışında taban gruptan oluşan karakter kümesini tanımlamak için `[a-z-[m]]`. "d", "j" ve "p" karakterleri kümesi dışında taban gruptan oluşan karakter kümesini tanımlamak `[a-z-[djp]]`için. "m" ile "p" arasında değişen karakter aralığı dışında temel gruptan oluşan karakter `[a-z-[m-p]]`kümesini tanımlamak için.  
  
 İç içe karakter sınıfı çıkarma `[a-z-[d-w-[m-o]]]`ifadesini göz önünde bulundurun. İfade en içteki karakter aralığından dışa doğru değerlendirilir. İlk önce, "m" - "o" karakter aralığı "d" - "w" karakter aralığından çıkarılır ve bunun sonucunda "d" ile "l" ve "p" ile "w" arasındaki karakterlerin kümesi oluşur. Bu küme daha sonra karakter aralığından "a" ile "z" arasında çıkarılır ve `[abcmnoxyz]`bu da karakter kümesini verir.  
  
 Karakter sınıfı çıkarma işleminden herhangi bir karakter sınıfını kullanabilirsiniz. \u0000'den \uFFFF'ye kadar tüm Unicode karakterlerinden oluşan karakter kümesini tanımlamak`\s`için beyaz boşluk karakterleri hariç (`\p{P}`), noktalama işaretleri `IsGreek` genel`\p{IsGreek}`kategorisindeki karakterler ( ), adlandırılmış bloktaki karakterler `[\u0000-\uFFFF-[\s\p{P}\p{IsGreek}\x85]]`( ), ve Unicode NEXT LINE denetim karakteri (\x85), kullanın .  
  
 Karakter sınıflarını yararlı sonuçlar verecek bir karakter sınıfı çıkarma ifadesi için seçin. Hiçbir şeyle eşleşmeyen boş bir karakter kümesi oluşturan veya orijinal temel gruba eşdeğer olan ifadelerden kaçının. Örneğin, boş küme, `[\p{IsBasicLatin}-[\x00-\x7F]]` `IsBasicLatin` karakter aralığındaki tüm karakterleri genel kategoriden çıkaran ifadenin `IsBasicLatin` sonucudur. Benzer şekilde, özgün temel grup ifadenin `[a-z-[0-9]]`sonucudur.  Bunun sebebi, "a" - "z" arasındaki karakterleri içeren temel grubun, "0" - "9" arasındaki ondalık basamakları içeren çıkarılan gruptaki hiçbir karakteri içermemesidir.  
  
 Aşağıdaki örnek, `^[0-9-[2468]]+$`giriş dizesinde sıfır ve tek basamaklarla eşleşen normal bir ifade tanımlar.  Normal ifade aşağıdaki tabloda gösterildiği gibi yorumlanır.  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|^|Giriş dizesinin başında eşleşmeyi başlat.|  
|`[0-9-[2468]]+`|0 ile 9 arasında; 2, 4, 6 ve 8 dışındaki herhangi bir karakter bir veya daha fazla bulunduğunda eşleş. Başka bir deyişle, sıfır veya bir tek basamakla eşleş.|  
|$|Giriş dizesinin sonunda eşleşmeyi bitir.|  
  
 [!code-csharp[Conceptual.RegEx.Language.CharacterClasses#15](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.characterclasses/cs/classsubtraction1.cs#15)]
 [!code-vb[Conceptual.RegEx.Language.CharacterClasses#15](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.characterclasses/vb/classsubtraction1.vb#15)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Char.GetUnicodeCategory%2A>
- [Normal İfade Dili - Hızlı Başvuru](../../../docs/standard/base-types/regular-expression-language-quick-reference.md)
- [Normal İfade Seçenekleri](../../../docs/standard/base-types/regular-expression-options.md)
