---
title: .NET normal Ifadelerinde karakter sınıfları
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
author: rpetrusha
ms.author: ronpet
ms.custom: seodec18
ms.openlocfilehash: 53dcbcfdcc9a8d04840bc91a563b6514153b9577
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69963426"
---
# <a name="character-classes-in-regular-expressions"></a>Normal ifadelerde karakter sınıfları

Bir karakter sınıfı, bir eşleşmenin başarılı olması için giriş dizesinde bulunabilecek karakterleri içeren bir karakter kümesi tanımlar. .NET 'teki normal ifade dili aşağıdaki karakter sınıflarını destekler:  
  
- Pozitif karakter grupları. Giriş dizesindeki bir karakter, belirli bir karakter kümesindekindeki karakterlerden biriyle eşleşmelidir. Daha fazla bilgi için bkz. [pozitif karakter grubu](#PositiveGroup).  
  
- Negatif karakter grupları. Giriş dizesindeki bir karakter, belirli bir karakter kümesindekindeki karakterlerden biriyle eşleşmemelidir. Daha fazla bilgi için bkz. [negatif karakter grubu](#NegativeGroup).  
  
- Herhangi bir karakter. Normal bir ifadede bulunan `\n` (noktaveyanokta)karakter,dışındaherhangibirkarakterleeşleşenbirjokerkarakterdir.`.` Daha fazla bilgi için, bkz. [herhangi bir karakter](#AnyCharacter).  
  
- Genel bir Unicode kategorisi veya adlandırılmış blok. Giriş dizesindeki bir karakter, eşleşmenin başarılı olması için belirli bir Unicode kategorisinin üyesi veya bir bitişik Unicode karakterleri aralığında olmalıdır. Daha fazla bilgi için bkz. [Unicode kategorisi veya Unicode bloğu](#CategoryOrBlock).  
  
- Negatif bir Unicode kategorisi veya adlandırılmış blok. Giriş dizesindeki bir karakter, eşleşmenin başarılı olması için belirli bir Unicode kategorisinin üyesi veya bir bitişik Unicode karakterleri aralığında olmamalıdır. Daha fazla bilgi için bkz. [negatif Unicode kategorisi veya Unicode bloğu](#NegativeCategoryOrBlock).  
  
- Bir sözcük karakteri. Giriş dizesindeki bir karakter, sözcüklerdeki karakterler için uygun olan herhangi bir Unicode kategorisine ait olabilir. Daha fazla bilgi için bkz. [sözcük karakteri](#WordCharacter).  
  
- Sözcük olmayan karakter. Giriş dizesindeki bir karakter, sözcük karakteri olmayan herhangi bir Unicode kategorisine ait olabilir. Daha fazla bilgi için, bkz. [sözcük olmayan karakter](#NonWordCharacter).  
  
- Boşluk karakteri. Giriş dizesindeki bir karakter herhangi bir Unicode ayıraç karakteri veya herhangi bir denetim karakteri olabilir. Daha fazla bilgi için bkz. boşluk [karakteri](#WhitespaceCharacter).  
  
- Boşluk olmayan karakter. Giriş dizesindeki bir karakter boşluk karakteri olmayan herhangi bir karakter olabilir. Daha fazla bilgi için bkz. [boşluk olmayan karakter](#NonWhitespaceCharacter).  
  
- Ondalık basamak. Giriş dizesindeki bir karakter Unicode ondalık basamakları olarak sınıflandırılan karakterlerden biri olabilir. Daha fazla bilgi için bkz. [ondalık basamak karakteri](#DigitCharacter).  
  
- Ondalık olmayan basamak. Giriş dizesindeki bir karakter, bir Unicode basamak karakteri dışındaki herhangi bir karakter olabilir. Daha fazla bilgi için bkz. [ondalık basamak karakteri](#NonDigitCharacter).  
  
 .NET, bir karakter sınıfının başka bir karakter sınıfından dışlanması sonucu olarak bir karakter kümesi tanımlamanızı sağlayan karakter sınıfı çıkarma ifadelerini destekler. Daha fazla bilgi için bkz. [karakter sınıfı çıkarma](#CharacterClassSubtraction).  
  
> [!NOTE]
> Bir<xref:System.Globalization.CharUnicodeInfo> Unicode kategorisiyle eşleşmesi için sözcük karakterleriyle veya [{} \p](#CategoryOrBlock) ile eşleşecek [\w](#WordCharacter) gibi karakter sınıfları, karakter kategorileri hakkında bilgi sağlamak için sınıfına bağımlıdır.  .NET Framework 4.6.2 başlayarak, karakter kategorileri [Unicode standardı, sürüm 8.0.0](https://www.unicode.org/versions/Unicode8.0.0/)' i temel alır. .NET Framework 4.6.1 aracılığıyla .NET Framework 4 ' te, [Unicode standardı, sürüm 6.3.0](https://www.unicode.org/versions/Unicode6.3.0/)tabanlıdır.  
  
<a name="PositiveGroup"></a>   
## <a name="positive-character-group--"></a>Pozitif karakter grubu: []  
 Bir pozitif karakter grubu, eşleşme olabilmesi için giriş dizesinde bulunabilecek karakterlerin listesini belirtir. Bu karakterler tek tek, bir aralık olarak veya her iki şekilde de belirtilebilir.  
  
 Karakterlerin tek tek bulunduğu bir listeyi belirtmek için kullanılan söz dizimi aşağıdaki gibidir:  

```  
[*character_group*]  
```

 Burada *character_group* , bir eşleşmenin başarılı olması için giriş dizesinde görünebilen tek tek karakterlerin bir listesidir. *character_group* , bir veya daha fazla değişmez karakter, [kaçış karakteri](../../../docs/standard/base-types/character-escapes-in-regular-expressions.md)veya karakter sınıfı herhangi bir birleşimini içerebilir.  
  
 Bir karakter aralığı belirtmek için kullanılan söz dizimi aşağıdaki gibidir:  
  
```  
[firstCharacter-lastCharacter]  
```  
  
 Burada *Firstcharacter* aralığı Başlatan karakter ve *lastcharacter* aralığı sonlandıran karakterdir. Bir karakter aralığı serideki ilk karakter, tire işareti (-) ve ardından serideki son karakterle belirtilen bitişik karakter dizisidir. İki karakter, eğer bitişik Unicode kod noktaları var ise bitişiktir. *Firstcharacter* , alt kod noktası olan karakter olmalıdır ve *lastcharacter* , daha yüksek kod noktası olan karakter olmalıdır.

> [!NOTE]
> Pozitif bir karakter grubu hem bir karakter kümesi hem de bir karakter aralığı içerebildiğinden, grubun ilk veya son karakteri`-`olmadığı sürece bir tire karakteri () her zaman Aralık ayırıcısı olarak yorumlanır.

Pozitif karakter sınıflarını içeren bazı sık kullanılan normal ifade desenleri aşağıdaki tabloda listelenmiştir.  
  
|Desen|Açıklama|  
|-------------|-----------------|  
|`[aeiou]`|Tüm sesli harflerle eşleş.|  
|`[\p{P}\d]`|Tüm noktalama işaretleriyle ve ondalık basamak işaretleriyle eşleş.|  
|`[\s\p{P}]`|Tüm boşluk ve noktalama işaretlerini eşleştirin.|  
  
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
  
 Aşağıdaki örnek büyük harf ile başlayan sözcüklerle eşleşir. A 'dan Z 'ye `[A-Z]` kadar büyük harflerin aralığını temsil etmek için alt ifadeyi kullanır.  
  
 [!code-csharp[Conceptual.RegEx.Language.CharacterClasses#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.characterclasses/cs/range.cs#3)]
 [!code-vb[Conceptual.RegEx.Language.CharacterClasses#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.characterclasses/vb/range.vb#3)]  
  
 Normal ifade `\b[A-Z]\w*\b` aşağıdaki tabloda gösterildiği gibi tanımlanmıştır.  
  
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

```
[*^character_group*]  
```

 Burada *character_group* , bir eşleşmenin başarılı olması için giriş dizesinde görünmeyen tek karakterlerin bir listesidir. *character_group* , bir veya daha fazla değişmez karakter, [kaçış karakteri](../../../docs/standard/base-types/character-escapes-in-regular-expressions.md)veya karakter sınıfı herhangi bir birleşimini içerebilir.  
  
 Bir karakter aralığı belirtmek için kullanılan söz dizimi aşağıdaki gibidir:  

```
[^*firstCharacter*-*lastCharacter*]  
```

Burada *Firstcharacter* aralığı Başlatan karakter ve *lastcharacter* aralığı sonlandıran karakterdir. Bir karakter aralığı serideki ilk karakter, tire işareti (-) ve ardından serideki son karakterle belirtilen bitişik karakter dizisidir. İki karakter, eğer bitişik Unicode kod noktaları var ise bitişiktir. *Firstcharacter* , alt kod noktası olan karakter olmalıdır ve *lastcharacter* , daha yüksek kod noktası olan karakter olmalıdır.

> [!NOTE]
> Negatif bir karakter grubu hem bir karakter kümesi hem de bir karakter aralığı içerebildiğinden, grubun ilk veya son karakteri`-`olmadığı sürece bir tire karakteri () her zaman Aralık ayırıcısı olarak yorumlanır.
  
 İki veya daha fazla karakter aralığı birleştirilebilir. Örneğin, "0" ile "9" arasındaki ondalık basamak aralığını, "a" ile "f" arasındaki küçük harflerin aralığını ve "A" ile "F" arasındaki büyük harflerin aralığını belirtmek için öğesini kullanın `[0-9a-fA-F]`.  
  
 Negatif bir karakter grubundaki baştaki simgeyi seçtiğinizde karakteri (`^`) zorunludur ve karakter grubu pozitif karakter grubu yerine negatif bir karakter grubu olduğunu gösterir.  
  
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
  
 Normal ifade `\bth[^o]\w+\b` aşağıdaki tabloda gösterildiği gibi tanımlanmıştır.  
  
|Desen|Açıklama|  
|-------------|-----------------|  
|`\b`|Bir sözcük sınırında başla.|  
|`th`|"th" sabit karakterleriyle eşleş.|  
|`[^o]`|"o" olmayan herhangi bir karakterle eşleş.|  
|`\w+`|Bir veya daha fazla sözcük karakteri eşleştir.|  
|`\b`|Bir sözcük sınırında bit.|  
  
<a name="AnyCharacter"></a>   
## <a name="any-character-"></a>Herhangi bir karakter:.  
 Nokta karakteri (.), aşağıdaki iki nitelikle `\n` , (yeni satır karakteri, \u000A) dışında herhangi bir karakterle eşleşir:  
  
- Bir <xref:System.Text.RegularExpressions.RegexOptions.Singleline?displayProperty=nameWithType> normal ifade deseninin seçeneği tarafından değiştirilirse veya bir `.` karakter `s` sınıfını içeren deseninin bölümü seçeneği tarafından `.` değiştirilirse, herhangi bir karakterle eşleşir. Daha fazla bilgi için bkz. [Normal İfade Seçenekleri](../../../docs/standard/base-types/regular-expression-options.md).  
  
     Aşağıdaki örnek, varsayılan olarak ve `.` <xref:System.Text.RegularExpressions.RegexOptions.Singleline?displayProperty=nameWithType> seçeneğiyle karakter sınıfının farklı davranışını gösterir. Normal ifade `^.+` dizenin başlangıcında başlar ve her karakterle eşleşir. Varsayılan olarak eşleştirme, ilk satırın sonunda biter; normal ifade deseninin satır dönüş karakteriyle `\r` veya \u000D ile eşleşmesi, ancak eşleşmez. `\n` Seçeneği giriş dizesinin tamamını tek bir satır olarak yorumladığından, dahil olmak üzere `\n`giriş dizesindeki her karakterle eşleşir. <xref:System.Text.RegularExpressions.RegexOptions.Singleline?displayProperty=nameWithType>  
  
     [!code-csharp[Conceptual.Regex.Language.CharacterClasses#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.characterclasses/cs/any2.cs#5)]
     [!code-vb[Conceptual.Regex.Language.CharacterClasses#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.characterclasses/vb/any2.vb#5)]  
  
> [!NOTE]
> Dışındaki `\n`bir karakterle eşleştiğinden `.` , karakter sınıfı da eşleşir `\r` (satır başı karakteri, \u000D).  
  
- Bir pozitif veya negatif karakter grubunda, nokta bir karakter sınıfı yerine sabit karakter olarak kabul edilir. Daha fazla bilgi için bu konunun önceki kısımlarında yer alarak [pozitif karakter grubu](#PositiveGroup) ve [negatif karakter grubu](#NegativeGroup) konularına bakın. Aşağıdaki örnek, nokta karakterini (`.`) hem karakter sınıfı hem de pozitif bir karakter grubunun üyesi olarak içeren bir normal ifade tanımlayarak bir çizim sağlar. Normal ifade `\b.*[.?!;:](\s|\z)` bir sözcük sınırında başlar, bir nokta dahil olmak üzere beş noktalama işaretinden biriyle karşılaşana kadar herhangi bir karakterle eşleşir ve sonra bir boşluk karakteri veya dizenin sonuyla eşleşir.  
  
     [!code-csharp[Conceptual.RegEx.Language.CharacterClasses#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.characterclasses/cs/any1.cs#4)]
     [!code-vb[Conceptual.RegEx.Language.CharacterClasses#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.characterclasses/vb/any1.vb#4)]  
  
> [!NOTE]
> Herhangi bir karakterle eşleştiğinden, bir normal `.` ifade deseninin herhangi bir karakteri birden çok kez eşleştirmeye çalışırsa, dil öğesi genellikle bir yavaş nicelik değeriyle kullanılır. Daha fazla bilgi için bkz [Miktar Belirleyiciler](../../../docs/standard/base-types/quantifiers-in-regular-expressions.md).  
  
<a name="CategoryOrBlock"></a>   
## <a name="unicode-category-or-unicode-block-p"></a>Unicode kategorisi veya Unicode bloğu: \p{}  
 Unicode standardı her karakteri genel bir kategoriye atar. Örneğin, belirli bir karakter `Lu` büyük harf (Kategori tarafından temsil edilir), ondalık basamak `Nd` (kategori), matematik simgesi ( `Sm` kategori `Zl` ) veya paragraf ayırıcı (kategori) olabilir. Unicode standardındaki belirli karakter kümeleri ayrıca birbirini izleyen kod noktalarının belirli bir aralığını veya bloğunu kaplar. Örneğin, temel Latin karakter kümesi \u0000 ile \u007F arasındayken, Arapça karakter kümesi \u0600 ile \u06FF arasındadır.  
  
 Normal ifade yapısı  
  
 `\p{`*ad*`}`  
  
 bir Unicode genel kategorisine veya adlandırılmış bloğa ait olan herhangi bir karakterle eşleşir; burada *ad* kategori kısaltması veya adlandırılmış blok adıdır. Kategori kısaltmalarının listesi için, bu konunun ilerleyen kısımlarında [desteklenen Unicode genel kategorileri](#SupportedUnicodeGeneralCategories) bölümüne bakın. Adlandırılmış blokların listesi için, bu konunun ilerleyen kısımlarında [desteklenen adlandırılmış bloklar](#SupportedNamedBlocks) bölümüne bakın.  
  
 Aşağıdaki örnek, bir Unicode `\p{`genel `Pd`kategorisini (Bu durumda, veya noktalama işareti `IsGreek` , Dash kategorisi) ve adlandırılmış bir bloğu (ve `IsBasicLatin` adlı) eşleştirmek için *ad* `}` yapısını kullanır. bloklar).  
  
 [!code-csharp[Conceptual.RegEx.Language.CharacterClasses#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.characterclasses/cs/category1.cs#6)]
 [!code-vb[Conceptual.RegEx.Language.CharacterClasses#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.characterclasses/vb/category1.vb#6)]  
  
 Normal ifade `\b(\p{IsGreek}+(\s)?)+\p{Pd}\s(\p{IsBasicLatin}+(\s)?)+` aşağıdaki tabloda gösterildiği gibi tanımlanmıştır.  
  
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
## <a name="negative-unicode-category-or-unicode-block-p"></a>Negatif Unicode kategorisi veya Unicode bloğu: \p{}  
 Unicode standardı her karakteri genel bir kategoriye atar. Örneğin, belirli bir karakter `Lu` büyük harf (Kategori tarafından temsil edilir), ondalık basamak `Nd` (kategori), matematik simgesi ( `Sm` kategori `Zl` ) veya paragraf ayırıcı (kategori) olabilir. Unicode standardındaki belirli karakter kümeleri ayrıca birbirini izleyen kod noktalarının belirli bir aralığını veya bloğunu kaplar. Örneğin, temel Latin karakter kümesi \u0000 ile \u007F arasındayken, Arapça karakter kümesi \u0600 ile \u06FF arasındadır.  
  
 Normal ifade yapısı  
  
 `\P{`*ad*`}`  
  
 bir Unicode genel kategorisine veya adlandırılmış bloğa ait olmayan herhangi bir karakterle eşleşir; burada *ad* kategori kısaltması veya adlandırılmış blok adıdır. Kategori kısaltmalarının listesi için, bu konunun ilerleyen kısımlarında [desteklenen Unicode genel kategorileri](#SupportedUnicodeGeneralCategories) bölümüne bakın. Adlandırılmış blokların listesi için, bu konunun ilerleyen kısımlarında [desteklenen adlandırılmış bloklar](#SupportedNamedBlocks) bölümüne bakın.  
  
 Aşağıdaki örnek, sayısal dizelerdeki herhangi bir para `\P{`birimi `Sc`simgesini (Bu durumda, veya symbol, para birimi kategorisi) kaldırmak için *ad* `}` yapısını kullanır.  
  
 [!code-csharp[Conceptual.RegEx.Language.CharacterClasses#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.characterclasses/cs/notcategory1.cs#7)]
 [!code-vb[Conceptual.RegEx.Language.CharacterClasses#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.characterclasses/vb/notcategory1.vb#7)]  
  
 Normal ifade deseninin `(\P{Sc})+` para birimi sembolleri olmayan bir veya daha fazla karakterle eşleşmesi; sonuç dizesinden herhangi bir para birimi sembolünü etkin bir şekilde şeritleri.  
  
<a name="WordCharacter"></a>   
## <a name="word-character-w"></a>Sözcük karakteri: \w  
 `\w`herhangi bir kelime karakteriyle eşleşir. Bir sözcük karakteri, aşağıdaki tabloda listelenen Unicode kategorilerinin herhangi birinin üyesidir.  
  
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
  
 ECMAScript uyumlu davranış belirtilmişse, `\w` değerine `[a-zA-Z_0-9]`eşdeğerdir. ECMAScript normal ifadeleri hakkında daha fazla bilgi için [normal Ifade seçeneklerinde](../../../docs/standard/base-types/regular-expression-options.md)"ECMAScript eşleştirme davranışı" bölümüne bakın.  
  
> [!NOTE]
> Herhangi bir kelime karakteriyle eşleştiği için, `\w` bir normal ifade deseninin her bir sözcük karakterini birden çok kez eşleştirmeye çalışırsa ve ardından belirli bir sözcük karakteriyle karşılaşarak, dil öğesi genellikle bir yavaş nicelik değeriyle kullanılır. Daha fazla bilgi için bkz [Miktar Belirleyiciler](../../../docs/standard/base-types/quantifiers-in-regular-expressions.md).  
  
 Aşağıdaki örnek, bir sözcükteki yinelenen karakterleri eşleştirmek için `\w` Language öğesini kullanır. Örnek, aşağıdaki gibi yorumlanabilen bir normal `(\w)\1`ifade deseninin tanımlar.  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|(\w)|Bir sözcük karakteriyle eşleş. Bu ilk yakalama grubudur.|  
|\1|İlk yakalamanın değeriyle eşleş.|  
  
 [!code-csharp[Conceptual.RegEx.Language.CharacterClasses#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.characterclasses/cs/wordchar1.cs#8)]
 [!code-vb[Conceptual.RegEx.Language.CharacterClasses#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.characterclasses/vb/wordchar1.vb#8)]  
  
<a name="NonWordCharacter"></a>   
## <a name="non-word-character-w"></a>Sözcük olmayan karakter: \w  
 `\W`sözcük olmayan herhangi bir karakterle eşleşir. \W dil öğesi aşağıdaki karakter sınıfıyla eşdeğerdir:  
  
```  
[^\p{Ll}\p{Lu}\p{Lt}\p{Lo}\p{Nd}\p{Pc}\p{Lm}]  
```  
  
 Diğer bir deyişle, aşağıdaki tabloda listelenen Unicode kategorilerindekiler dışında herhangi bir karakterle eşleşir.  
  
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
  
 ECMAScript uyumlu davranış belirtilmişse, `\W` değerine `[^a-zA-Z_0-9]`eşdeğerdir. ECMAScript normal ifadeleri hakkında daha fazla bilgi için [normal Ifade seçeneklerinde](../../../docs/standard/base-types/regular-expression-options.md)"ECMAScript eşleştirme davranışı" bölümüne bakın.  
  
> [!NOTE]
> Sözcük olmayan herhangi bir karakterle eşleştiğinden, bir normal ifade `\W` deseninin sözcük olmayan bir karakterle birden çok kez ve ardından belirli bir sözcük olmayan karakterle eşleşmesi deneniyorsa, dil öğesi genellikle bir yavaş nicelik değeriyle kullanılır. Daha fazla bilgi için bkz [Miktar Belirleyiciler](../../../docs/standard/base-types/quantifiers-in-regular-expressions.md).  
  
 Aşağıdaki örnek, `\W` karakter sınıfını göstermektedir.  Bir sözcüğe ve ardından boşluk veya noktalama `\b(\w+)(\W){1,2}`gibi bir veya iki sözcük olmayan karakterle eşleşen bir normal ifade deseninin tanımlar. Normal ifade aşağıdaki tabloda gösterildiği gibi yorumlanır.  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|\b|Bir sözcük sınırında eşleşmeye başla.|  
|(\w+)|Bir veya daha fazla sözcük karakteri eşleştir. Bu ilk yakalama grubudur.|  
|\W{1,2}|Sözcük olmayan bir karakteri bir veya iki kez eşleştir. Bu ikinci yakalama grubudur.|  
  
 [!code-csharp[Conceptual.RegEx.Language.CharacterClasses#9](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.characterclasses/cs/nonwordchar1.cs#9)]
 [!code-vb[Conceptual.RegEx.Language.CharacterClasses#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.characterclasses/vb/nonwordchar1.vb#9)]  
  
 İkinci yakalama grubuna yönelik <xref:System.Text.RegularExpressions.CaptureCollection> <xref:System.Text.RegularExpressions.Group.Captures%2A?displayProperty=nameWithType> nesne yalnızca tek bir yakalanan sözcük olmayan karakter içerdiğinden, örnek, tüm yakalanan sözcük olmayan karakterleri özelliği tarafından döndürülen nesneden alır. <xref:System.Text.RegularExpressions.Group>  
  
<a name="WhitespaceCharacter"></a>   
## <a name="whitespace-character-s"></a>Boşluk karakteri: \s  
 `\s`herhangi bir boşluk karakteriyle eşleşir. Aşağıdaki tabloda listelenen kaçış dizileri ve Unicode kategorileriyle eşdeğerdir.  
  
|Kategori|Açıklama|  
|--------------|-----------------|  
|`\f`|Sonraki sayfaya geçme karakteri, \u000C.|  
|`\n`|Yeni satır karakteri, \u000A.|  
|`\r`|Satır başı karakteri, \u000D.|  
|`\t`|Sekme karakteri, \u0009.|  
|`\v`|Dikey sekme karakteri, \u000B.|  
|`\x85`|Üç nokta veya sonraki satır (NEL) karakteri (...), \u0085.|  
|`\p{Z}`|Herhangi bir ayıraç karakterle eşleşir.|  
  
 ECMAScript uyumlu davranış belirtilmişse, `\s` değerine `[ \f\n\r\t\v]`eşdeğerdir. ECMAScript normal ifadeleri hakkında daha fazla bilgi için [normal Ifade seçeneklerinde](../../../docs/standard/base-types/regular-expression-options.md)"ECMAScript eşleştirme davranışı" bölümüne bakın.  
  
 Aşağıdaki örnek, `\s` karakter sınıfını göstermektedir. "S" veya "es" `\b\w+(e)?s(\s|$)`ile biten bir sözcükle, ardından bir boşluk karakteri veya giriş dizesinin sonu ile eşleşen bir normal ifade deseninin tanımlar. Normal ifade aşağıdaki tabloda gösterildiği gibi yorumlanır.  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|\b|Bir sözcük sınırında eşleşmeye başla.|  
|\w+|Bir veya daha fazla sözcük karakteri eşleştir.|  
|(e)?|Sıfır veya bir kez "e" ile eşleş.|  
|s|Bir "s" ile eşleş.|  
|(\s&#124;$)|Boşluk karakteri veya giriş dizesinin sonuyla eşleştirin.|  
  
 [!code-csharp[Conceptual.RegEx.Language.CharacterClasses#10](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.characterclasses/cs/whitespace1.cs#10)]
 [!code-vb[Conceptual.RegEx.Language.CharacterClasses#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.characterclasses/vb/whitespace1.vb#10)]  
  
<a name="NonWhitespaceCharacter"></a>   
## <a name="non-whitespace-character-s"></a>Boşluk olmayan karakter: \s  
 `\S`boşluk olmayan herhangi bir karakterle eşleşir. Bu, `[^\f\n\r\t\v\x85\p{Z}]` normal ifade deseninin veya `\s`eşdeğer olan normal ifade deseninin ters, boşluk karakterleriyle eşleşen, ile eşdeğerdir. Daha fazla bilgi için bkz. boşluk [karakteri: \s](#WhitespaceCharacter).  
  
 ECMAScript uyumlu davranış belirtilmişse, `\S` değerine `[^ \f\n\r\t\v]`eşdeğerdir. ECMAScript normal ifadeleri hakkında daha fazla bilgi için [normal Ifade seçeneklerinde](../../../docs/standard/base-types/regular-expression-options.md)"ECMAScript eşleştirme davranışı" bölümüne bakın.  
  
 Aşağıdaki örnek, `\S` Language öğesini göstermektedir. Normal ifade deseninin `\b(\S+)\s?` boşluk karakterleri ile ayrılmış dizeler eşleşir. Eşleşmenin <xref:System.Text.RegularExpressions.GroupCollection> nesnesindeki ikinci öğe eşleşen dizeyi içeriyor. Normal ifade aşağıdaki tabloda gösterildiği gibi yorumlanabilir.  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|`\b`|Bir sözcük sınırında eşleşmeye başla.|  
|`(\S+)`|Bir veya daha fazla boşluk olmayan karakterle eşleş. Bu ilk yakalama grubudur.|  
|`\s?`|Sıfır veya bir beyaz boşluk karakterini eşleştirin.|  
  
 [!code-csharp[Conceptual.RegEx.Language.CharacterClasses#11](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.characterclasses/cs/nonwhitespace1.cs#11)]
 [!code-vb[Conceptual.RegEx.Language.CharacterClasses#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.characterclasses/vb/nonwhitespace1.vb#11)]  
  
<a name="DigitCharacter"></a>   
## <a name="decimal-digit-character-d"></a>Ondalık basamak karakteri: \d  
 `\d`herhangi bir ondalık basamakla eşleşir. Standart ondalık basamakları 0-9, `\p{Nd}` diğer karakter kümelerinin ondalık basamakları de dahil olmak üzere, normal ifade deseninin eşdeğeridir.  
  
 ECMAScript uyumlu davranış belirtilmişse, `\d` değerine `[0-9]`eşdeğerdir. ECMAScript normal ifadeleri hakkında daha fazla bilgi için [normal Ifade seçeneklerinde](../../../docs/standard/base-types/regular-expression-options.md)"ECMAScript eşleştirme davranışı" bölümüne bakın.  
  
 Aşağıdaki örnek, `\d` Language öğesini göstermektedir. Bir giriş dizesinin Amerika Birleşik Devletleri ve Kanada'da geçerli bir telefon numarası olup olmadığını test eder. Normal ifade deseninin `^(\(?\d{3}\)?[\s-])?\d{3}-\d{4}$` , aşağıdaki tabloda gösterildiği gibi tanımlanmıştır.  
  
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
## <a name="non-digit-character-d"></a>Basamak olmayan karakter: \d  
 `\D`rakam olmayan herhangi bir karakterle eşleşir. `\P{Nd}` Normal ifade deseninin eşdeğeridir.  
  
 ECMAScript uyumlu davranış belirtilmişse, `\D` değerine `[^0-9]`eşdeğerdir. ECMAScript normal ifadeleri hakkında daha fazla bilgi için [normal Ifade seçeneklerinde](../../../docs/standard/base-types/regular-expression-options.md)"ECMAScript eşleştirme davranışı" bölümüne bakın.  
  
 Aşağıdaki örnek, \D dil öğesini gösterir. Parça numarası gibi bir dizenin doğru ondalık ve ondalık olmayan karakter birleşimini içerip içermediğini test eder. Normal ifade deseninin `^\D\d{1,5}\D*$` , aşağıdaki tabloda gösterildiği gibi tanımlanmıştır.  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|`^`|Giriş dizesinin başında eşleşmeye başla.|  
|`\D`|Basamak olmayan bir karakterle eşleş.|  
|`\d{1,5}`|Bir ile beş tane arasında ondalık basamakla eşleş.|  
|`\D*`|Sıfır, bir veya daha fazla ondalık olmayan karakteri eşleştirin.|  
|`$`|Giriş dizesinin sonuyla eşleş.|  
  
 [!code-csharp[Conceptual.RegEx.Language.CharacterClasses#13](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.characterclasses/cs/nondigit1.cs#13)]
 [!code-vb[Conceptual.RegEx.Language.CharacterClasses#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.characterclasses/vb/nondigit1.vb#13)]  
  
<a name="SupportedUnicodeGeneralCategories"></a>   
## <a name="supported-unicode-general-categories"></a>Desteklenen Unicode genel kategorileri  
 Unicode aşağıdaki tabloda listelenen genel kategorileri tanımlar. Daha fazla bilgi için, [Unicode karakter veritabanında](https://www.unicode.org/reports/tr44/)"UCD dosya biçimi" ve "genel kategori değerleri" alt konuları bölümüne bakın.  
  
|Kategori|Açıklama|  
|--------------|-----------------|  
|`Lu`|Harf, Büyük Harf|  
|`Ll`|Harf, Küçük Harf|  
|`Lt`|Harf, Başlık Düzeni|  
|`Lm`|Harf, Değiştirici|  
|`Lo`|Harf, Diğer|  
|`L`|Tüm harf karakterler. Bu,, `Lu`, `Ll`, ve `Lm` `Lt` karakterleriniiçerir`Lo` .|  
|`Mn`|İşaret, Boşluksuz|  
|`Mc`|İşaret, Boşluklu Birleşik|  
|`Me`|İşaret, Çevreleyen|  
|`M`|Tüm aksan işaretleri. Bu,, `Mn`ve `Mc` `Me` kategorilerini içerir.|  
|`Nd`|Sayı, Ondalık Basamak|  
|`Nl`|Sayı, Harf|  
|`No`|Sayı, Diğer|  
|`N`|Tüm sayılar. Bu,, `Nd`ve `Nl` `No` kategorilerini içerir.|  
|`Pc`|Noktalama, Bağlayıcı|  
|`Pd`|Noktalama, Tire|  
|`Ps`|Noktalama, Açık|  
|`Pe`|Noktalama, Kapalı|  
|`Pi`|Noktalama, Açılış tırnağı (kullanıma göre Ps veya Pe gibi davranabilir)|  
|`Pf`|Noktalama, Kapanış tırnağı (kullanıma göre Ps veya Pe gibi davranabilir)|  
|`Po`|Noktalama, Diğer|  
|`P`|Tüm noktalama işaretleri. Bu,, `Pc`,, `Ps`, `Pe`, `Pi` `Pd`ve `Pf`kategorilerini içerir.`Po`|  
|`Sm`|Sembol, Matematik|  
|`Sc`|Sembol, Para Birimi|  
|`Sk`|Sembol, Değiştirici|  
|`So`|Sembol, Diğer|  
|`S`|Tüm semboller. Bu,, `Sm`, `Sc`ve `Sk` kategorileriniiçerir`So` .|  
|`Zs`|Ayırıcı, Boşluk|  
|`Zl`|Ayırıcı, Satır|  
|`Zp`|Ayırıcı, Paragraf|  
|`Z`|Tüm ayırıcı karakterlerler. Bu,, `Zs`ve `Zl` `Zp` kategorilerini içerir.|  
|`Cc`|Diğer, Denetim|  
|`Cf`|Diğer, Biçim|  
|`Cs`|Diğer, Yedek Karakter|  
|`Co`|Diğer, Özel Kullanım|  
|`Cn`|Diğer, Atanmamış (hiçbir karakter bu özelliğe sahip değildir)|  
|`C`|Tüm denetim karakterleri. Bu,, `Cc`, `Cf`, ve `Co` `Cs` kategorileriniiçerir`Cn` .|  
  
 Söz konusu karakteri <xref:System.Char.GetUnicodeCategory%2A> yöntemine geçirerek belirli bir karakterin Unicode kategorisini belirleyebilirsiniz. Aşağıdaki örnek, seçili Latin <xref:System.Char.GetUnicodeCategory%2A> karakterlerini içeren bir dizideki her öğenin kategorisini belirlemede yöntemini kullanır.  
  
 [!code-csharp[Conceptual.RegEx.Language.CharacterClasses#14](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.characterclasses/cs/getunicodecategory1.cs#14)]
 [!code-vb[Conceptual.RegEx.Language.CharacterClasses#14](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.characterclasses/vb/getunicodecategory1.vb#14)]  
  
<a name="SupportedNamedBlocks"></a>   
## <a name="supported-named-blocks"></a>Desteklenen adlandırılmış bloklar

.NET, aşağıdaki tabloda listelenen adlandırılmış blokları sağlar. Desteklenen adlandırılmış bloklar kümesi Unicode 4.0 ve Perl 5.6'yı temel alır. Adlandırılmış blokları kullanan bir normal ifade için bkz. [Unicode kategorisi veya Unicode \\bloğu: p{} ](#unicode-category-or-unicode-block-p) bölümü.  
  
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
## <a name="character-class-subtraction-base_group---excluded_group"></a>Karakter sınıfı çıkarma: [Base_group-[excluded_group]]  
 Bir karakter sınıfı bir karakter kümesini tanımlar. Karakter sınıfı çıkarma, bir karakter sınıfındaki karakterlerin başka bir karakter sınıfından dışlanmasının sonucu olan bir karakter kümesi döndürür.  
  
 Bir karakter sınıfı çıkarma ifadesi aşağıdaki biçime sahiptir:  
  
 `[`*Base_group* `-[` *excluded_group*`]]`  
  
 Köşeli parantezler (`[]`) ve kısa çizgi (`-`) zorunludur. *Base_group* bir [pozitif karakter grubu](#PositiveGroup) veya [negatif karakter grubudur](#NegativeGroup). *Excluded_group* bileşeni başka bir pozitif veya negatif karakter grubu ya da başka bir karakter sınıfı çıkarma ifadesi (yani, karakter sınıfı çıkarma ifadelerini iç içe geçirebilirsiniz).  
  
 Örneğin, "a" - "z" karakter aralığından oluşan bir temel grubunuz olduğunu varsayalım. "E" karakteri dışında temel gruptan oluşan karakter kümesini tanımlamak için kullanın `[a-z-[m]]`. "D", "j" ve "p" karakter kümesi hariç temel gruptan oluşan karakter kümesini tanımlamak için öğesini kullanın `[a-z-[djp]]`. "M" ile "p" arasında karakter aralığı dışında temel gruptan oluşan karakter kümesini tanımlamak için kullanın `[a-z-[m-p]]`.  
  
 İç içe geçmiş karakter sınıfı çıkarma ifadesini `[a-z-[d-w-[m-o]]]`göz önünde bulundurun. İfade en içteki karakter aralığından dışa doğru değerlendirilir. İlk önce, "m" - "o" karakter aralığı "d" - "w" karakter aralığından çıkarılır ve bunun sonucunda "d" ile "l" ve "p" ile "w" arasındaki karakterlerin kümesi oluşur. Bu küme daha sonra, karakter kümesini `[abcmnoxyz]`veren "a"-"z" karakter aralığından çıkarılır.  
  
 Karakter sınıfı çıkarma işleminden herhangi bir karakter sınıfını kullanabilirsiniz. Boşluk karakterleri hariç \u0000 ile \uFFFF arasındaki tüm Unicode karakterlerinden oluşan karakter kümesini tanımlamak için (`\s`), noktalama işaretleri Genel kategorisindeki (`\p{P}`) `IsGreek` , adındaki karakterler Block (`\p{IsGreek}`) ve Unicode sonraki satır denetim karakteri (\x85), kullanın `[\u0000-\uFFFF-[\s\p{P}\p{IsGreek}\x85]]`.  
  
 Karakter sınıflarını yararlı sonuçlar verecek bir karakter sınıfı çıkarma ifadesi için seçin. Hiçbir şeyle eşleşmeyen boş bir karakter kümesi oluşturan veya orijinal temel gruba eşdeğer olan ifadelerden kaçının. Örneğin, boş küme ifadenin `[\p{IsBasicLatin}-[\x00-\x7F]]`sonucudur ve bu, `IsBasicLatin` karakter aralığındaki `IsBasicLatin` tüm karakterleri Genel kategorisinden çıkartır. Benzer şekilde, özgün temel Grup, ifadenin `[a-z-[0-9]]`sonucudur.  Bunun sebebi, "a" - "z" arasındaki karakterleri içeren temel grubun, "0" - "9" arasındaki ondalık basamakları içeren çıkarılan gruptaki hiçbir karakteri içermemesidir.  
  
 Aşağıdaki örnek, bir giriş dizesindeki sıfır ve `^[0-9-[2468]]+$`tek basamakla eşleşen normal bir ifade tanımlar.  Normal ifade aşağıdaki tabloda gösterildiği gibi yorumlanır.  
  
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
