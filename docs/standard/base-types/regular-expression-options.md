---
title: Normal İfade Seçenekleri
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- regular expressions, options
- constructs, options
- .NET Framework regular expressions, options
- inline option constructs
- options parameter
ms.assetid: c82dc689-7e82-4767-a18d-cd24ce5f05e9
ms.openlocfilehash: bf352d6494a823d4f7b24eb2876d9bffa5877b2b
ms.sourcegitcommit: 7980a91f90ae5eca859db7e6bfa03e23e76a1a50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/13/2020
ms.locfileid: "81242783"
---
# <a name="regular-expression-options"></a>Normal İfade Seçenekleri

Varsayılan olarak, bir giriş dizesinin normal bir ifade desenindeki herhangi bir gerçek karakterle karşılaştırılması büyük/küçük harf duyarlıdır, normal ifade desenindeki beyaz boşluk gerçek beyaz alan karakterleri olarak yorumlanır ve normal bir ifadedeki yakalama grupları örtülü olarak ve açıkça adlandırılır. Bu ve varsayılan normal ifade davranışının diğer birkaç yönünü düzenli ifade seçenekleri belirterek değiştirebilirsiniz. Aşağıdaki tabloda listelenen bu seçenekler, normal ifade deseninin bir <xref:System.Text.RegularExpressions.Regex?displayProperty=nameWithType> parçası olarak satır içinde eklenebilir veya bir sınıf oluşturucuya <xref:System.Text.RegularExpressions.RegexOptions?displayProperty=nameWithType> veya statik desen eşleştirme yöntemine numaralandırma değeri olarak sağlanabilir.

|RegexOptions üyesi|Satır çizgisi karakteri|Etki|
|-------------------------|----------------------|------------|
|<xref:System.Text.RegularExpressions.RegexOptions.None>|Kullanılamaz|Varsayılan davranışı kullanın. Daha fazla bilgi için [Varsayılan Seçenekler'e](#default-options)bakın.|
|<xref:System.Text.RegularExpressions.RegexOptions.IgnoreCase>|`i`|Büyük küçük harf duyarlı eşleme kullanın. Daha fazla bilgi için [bkz.](#case-insensitive-matching)|
|<xref:System.Text.RegularExpressions.RegexOptions.Multiline>|`m`|Her satırın başlangıç `^` `$` ve sonunu (giriş dizesinin başı ve sonu yerine) eşleştirin ve çok satırlı modu kullanın. Daha fazla bilgi için [Çoklu Satır Modu'na](#multiline-mode)bakın.|
|<xref:System.Text.RegularExpressions.RegexOptions.Singleline>|`s`|Dönem (.) her karakterle eşleştiği tek satırlı modu `\n`kullanın (hariç her karakter yerine). Daha fazla bilgi için [Tek Satırlı Mod'a](#single-line-mode)bakın.|
|<xref:System.Text.RegularExpressions.RegexOptions.ExplicitCapture>|`n`|Adsız grupları yakalamayın. Yalnızca geçerli yakalamalar, `(?<`form *adı* `>` alt *ifadesinin*`)`açık adlandırılmış veya numaralandırılmış gruplarıdır. Daha fazla bilgi için [bkz.](#explicit-captures-only)|
|<xref:System.Text.RegularExpressions.RegexOptions.Compiled>|Kullanılamaz|Normal ifadeyi derlemeye derle. Daha fazla bilgi için [Derlenmiş Düzenli İfadeler'e](#compiled-regular-expressions)bakın.|
|<xref:System.Text.RegularExpressions.RegexOptions.IgnorePatternWhitespace>|`x`|Kamışsız beyaz alanı deseniniçin hariç tutve`#`bir sayı işaretinden sonra açıklamaları etkinleştirin ( ). Daha fazla bilgi için [bkz.](#ignore-white-space)|
|<xref:System.Text.RegularExpressions.RegexOptions.RightToLeft>|Kullanılamaz|Arama yönünü değiştirin. Arama soldan sağa değil, sağdan sola doğru hareket eder. Daha fazla bilgi için [sağdan sola modu'na](#right-to-left-mode)bakın.|
|<xref:System.Text.RegularExpressions.RegexOptions.ECMAScript>|Kullanılamaz|İfade için ECMAScript uyumlu davranışı etkinleştirin. Daha fazla bilgi için [ECMAScript Eşleştirme Davranışı'na](#ecmascript-matching-behavior)bakın.|
|<xref:System.Text.RegularExpressions.RegexOptions.CultureInvariant>|Kullanılamaz|Dildeki kültürel farklılıkları göz ardı edin. Daha fazla bilgi için Değişmez [Kültürü Kullanarak Karşılaştırma'ya](#comparison-using-the-invariant-culture)bakın.|

## <a name="specifying-the-options"></a>Seçenekleri Belirtme

Normal ifadeler için seçenekleri üç şekilde belirtebilirsiniz:

- Bir `options` <xref:System.Text.RegularExpressions.Regex?displayProperty=nameWithType> sınıf oluşturucu veya statik parametre`Shared` (Visual Basic) desen eşleştirme <xref:System.Text.RegularExpressions.Regex.%23ctor%28System.String%2CSystem.Text.RegularExpressions.RegexOptions%29> <xref:System.Text.RegularExpressions.Regex.Match%28System.String%2CSystem.String%2CSystem.Text.RegularExpressions.RegexOptions%29?displayProperty=nameWithType>yöntemi, gibi veya . `options` Parametre, numaralandırılmış değerlerin bitwise VEYA birleşimidir. <xref:System.Text.RegularExpressions.RegexOptions?displayProperty=nameWithType>

  Bir sınıf oluşturucu <xref:System.Text.RegularExpressions.Regex> parametresi `options` kullanılarak bir örneğe seçenekler sağlandığında, <xref:System.Text.RegularExpressions.RegexOptions?displayProperty=nameWithType> seçenekler özelliğe atanır. Ancak, <xref:System.Text.RegularExpressions.RegexOptions?displayProperty=nameWithType> özellik normal ifade deseni kendisi satır satır seçeneklerini yansıtmaz.

  Aşağıdaki örnek, bir gösterim sağlar. Büyük/küçük `options` harf duyarsız <xref:System.Text.RegularExpressions.Regex.Match%28System.String%2CSystem.String%2CSystem.Text.RegularExpressions.RegexOptions%29?displayProperty=nameWithType> eşleştirmeyi etkinleştirmek ve "d" harfiyle başlayan sözcükleri tanımlarken desen beyaz alanı yok saymak için yöntemin parametresini kullanır.

  [!code-csharp[Conceptual.Regex.Language.Options#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.options/cs/example1.cs#6)]
  [!code-vb[Conceptual.Regex.Language.Options#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.options/vb/example1.vb#6)]

- Sözdizimi `(?imnsx-imnsx)`ile normal bir ifade deseni satır içinde seçenekleri uygulayarak. Seçenek, seçeneğin tanımlandığı noktadan desenin sonuna veya seçeneğin başka bir satır altı seçeneği yle tanımlanmamış olduğu noktaya uygulanır. Bir <xref:System.Text.RegularExpressions.Regex> örneğin <xref:System.Text.RegularExpressions.RegexOptions?displayProperty=nameWithType> özelliğinin bu satır satır seçeneklerini yansıtmadığını unutmayın. Daha fazla bilgi [için, Çeşitli Yapılar konusuna](../../../docs/standard/base-types/miscellaneous-constructs-in-regular-expressions.md) bakın.

  Aşağıdaki örnek, bir gösterim sağlar. Büyük/küçük harf duyarsız eşleştirmeyi etkinleştirmek ve "d" harfiyle başlayan sözcükleri tanımlarken desen beyaz alanı yok saymak için satır içi seçenekleri kullanır.

  [!code-csharp[Conceptual.Regex.Language.Options#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.options/cs/example1.cs#7)]
  [!code-vb[Conceptual.Regex.Language.Options#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.options/vb/example1.vb#7)]

- Sözdizimi `(?imnsx-imnsx:` *alt ifadesi*`)`ile normal bir ifade deseni belirli bir gruplandırma yapısında satır başı seçenekleri uygulayarak. Bir dizi seçenek seti açmadan önce hiçbir işaret yok; bir dizi seçenek ayarlıyı kapatmadan önce eksi işareti. (`?` dil yapısının sözdiziminin seçenekler etkin veya devre dışı bırakılmış olması gereken sabit bir parçasıdır.) Bu seçenek yalnızca bu grup için geçerlidir. Daha fazla bilgi için [yapıyı gruplandırma](../../../docs/standard/base-types/grouping-constructs-in-regular-expressions.md)ya da gruplandırma'ya bakın.

  Aşağıdaki örnek, bir gösterim sağlar. Büyük/küçük harf duyarsız eşleştirmeyi etkinleştirmek ve "d" harfiyle başlayan sözcükleri tanımlarken desen beyaz alanı yok saymak için gruplandırma yapısında satır içi seçenekleri kullanır.

  [!code-csharp[Conceptual.Regex.Language.Options#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.options/cs/example1.cs#8)]
  [!code-vb[Conceptual.Regex.Language.Options#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.options/vb/example1.vb#8)]

Seçenekler satır satırda belirtilirse,`-`bir seçenek veya seçenek kümesi bu seçenekleri kapatmadan önce eksi işareti ( ) Örneğin, satır ara `(?ix-ms)` yapısı ve <xref:System.Text.RegularExpressions.RegexOptions.IgnoreCase?displayProperty=nameWithType> <xref:System.Text.RegularExpressions.RegexOptions.IgnorePatternWhitespace?displayProperty=nameWithType> seçenekleri açar ve <xref:System.Text.RegularExpressions.RegexOptions.Multiline?displayProperty=nameWithType> <xref:System.Text.RegularExpressions.RegexOptions.Singleline?displayProperty=nameWithType> seçenekleri kapatır ve seçenekleri kapatır. Tüm normal ifade seçenekleri varsayılan olarak kapatılır.

> [!NOTE]
> Bir oluşturucu veya yöntem `options` inline normal bir ifade deseni belirtilen seçenekleri ile çakışması parametre belirtilen normal ifade seçenekleri, satır ara seçenekleri kullanılır.

Aşağıdaki beş normal ifade seçeneği hem seçenekler parametresi hem de satır altı ile ayarlanabilir:

- <xref:System.Text.RegularExpressions.RegexOptions.IgnoreCase?displayProperty=nameWithType>

- <xref:System.Text.RegularExpressions.RegexOptions.Multiline?displayProperty=nameWithType>

- <xref:System.Text.RegularExpressions.RegexOptions.Singleline?displayProperty=nameWithType>

- <xref:System.Text.RegularExpressions.RegexOptions.ExplicitCapture?displayProperty=nameWithType>

- <xref:System.Text.RegularExpressions.RegexOptions.IgnorePatternWhitespace?displayProperty=nameWithType>

Aşağıdaki beş normal ifade seçeneği `options` parametre kullanılarak ayarlanabilir, ancak satır satıra ayarlanamaz:

- <xref:System.Text.RegularExpressions.RegexOptions.None?displayProperty=nameWithType>

- <xref:System.Text.RegularExpressions.RegexOptions.Compiled?displayProperty=nameWithType>

- <xref:System.Text.RegularExpressions.RegexOptions.RightToLeft?displayProperty=nameWithType>

- <xref:System.Text.RegularExpressions.RegexOptions.CultureInvariant?displayProperty=nameWithType>

- <xref:System.Text.RegularExpressions.RegexOptions.ECMAScript?displayProperty=nameWithType>

## <a name="determining-the-options"></a>Seçenekleri Belirleme

Salt <xref:System.Text.RegularExpressions.Regex.Options%2A?displayProperty=nameWithType> okunur özelliğin değerini <xref:System.Text.RegularExpressions.Regex> alarak bir nesneye anında hangi seçeneklerin sağlandığını belirleyebilirsiniz. Bu özellik, <xref:System.Text.RegularExpressions.Regex.CompileToAssembly%2A?displayProperty=nameWithType> özellikle yöntem tarafından oluşturulan derlenmiş normal ifade için tanımlanan seçenekleri belirlemek için yararlıdır.

Dışında <xref:System.Text.RegularExpressions.RegexOptions.None?displayProperty=nameWithType>herhangi bir seçeneğin varlığını test etmek için, <xref:System.Text.RegularExpressions.Regex.Options%2A?displayProperty=nameWithType> özelliğin değeri <xref:System.Text.RegularExpressions.RegexOptions> ve ilgilendiğiniz değeri ile bir AND işlemi gerçekleştirin. Ardından, sonucun bu <xref:System.Text.RegularExpressions.RegexOptions> değere eşit olup olmadığını test edin. Aşağıdaki örnek, seçeneğin <xref:System.Text.RegularExpressions.RegexOptions.IgnoreCase?displayProperty=nameWithType> ayarlanıp ayarlandığını test edin.

[!code-csharp[Conceptual.Regex.Language.Options#19](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.options/cs/determine1.cs#19)]
[!code-vb[Conceptual.Regex.Language.Options#19](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.options/vb/determine1.vb#19)]

Test etmek <xref:System.Text.RegularExpressions.RegexOptions.None?displayProperty=nameWithType>için, aşağıdaki örnekte gösterildiği <xref:System.Text.RegularExpressions.Regex.Options%2A?displayProperty=nameWithType> <xref:System.Text.RegularExpressions.RegexOptions.None?displayProperty=nameWithType>gibi, özelliğin değerinin eşit olup olmadığını belirleyin.

[!code-csharp[Conceptual.Regex.Language.Options#20](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.options/cs/determine1.cs#20)]
[!code-vb[Conceptual.Regex.Language.Options#20](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.options/vb/determine1.vb#20)]

Aşağıdaki bölümlerde .NET'te normal ifadeyle desteklenen seçenekler listelenir.

## <a name="default-options"></a>Varsayılan Seçenekler

Seçenek, <xref:System.Text.RegularExpressions.RegexOptions.None?displayProperty=nameWithType> hiçbir seçeneğin belirtildiğini ve normal ifade altyapısının varsayılan davranışını kullandığını gösterir. Bu, aşağıdakileri içerir:

- Desen, ECMAScript normal ifadesi yerine kanonik olarak yorumlanır.

- Normal ifade deseni, giriş dizesinde soldan sağa eşleşir.

- Karşılaştırmalar büyük/küçük harf duyarlıdır.

- `^` Ve `$` dil öğeleri giriş dizesinin başı ve sonuyla eşleşir.

- Dil `.` öğesi hariç `\n`her karakterle eşleşir.

- Normal ifade desenindeki herhangi bir beyaz boşluk gerçek bir boşluk karakteri olarak yorumlanır.

- Desen giriş dizesini karşılaştırırken geçerli kültürün kuralları kullanılır.

- Normal ifade desenindeki yakalama grupları örtük olduğu kadar açık da vardır.

> [!NOTE]
> Seçeneğin <xref:System.Text.RegularExpressions.RegexOptions.None?displayProperty=nameWithType> satır eşdeğeri yoktur. Sıralı normal ifade seçenekleri uygulandığında, varsayılan davranış belirli bir seçeneği kapatarak seçenek bazında geri yüklenir. Örneğin, `(?i)` büyük/küçük harf duyarlı karşılaştırmayı açar ve `(?-i)` varsayılan büyük/küçük harf duyarlı karşılaştırmayı geri yükler.

<xref:System.Text.RegularExpressions.RegexOptions.None?displayProperty=nameWithType> Seçenek normal ifade altyapısının varsayılan davranışını temsil ettiği için, yöntem çağrısında nadiren açıkça belirtilir. Bunun yerine parametre içermeyen bir `options` yapı oluşturucu veya statik desen eşleştirme yöntemi çağrılır.

## <a name="case-insensitive-matching"></a>Büyük/Küçük Harf-Duyarsız Eşleştirme

Seçenek <xref:System.Text.RegularExpressions.RegexOptions.IgnoreCase> veya `i` satır içi seçenek, büyük/küçük harf duyarsız eşleştirme sağlar. Varsayılan olarak, geçerli kültürün kasa kuralları kullanılır.

Aşağıdaki örnek, `\bthe\w*\b`"the" ile başlayan tüm sözcükleri eşleştiren normal bir ifade deseni tanımlar. <xref:System.Text.RegularExpressions.Regex.Match%2A> Yönteme ilk çağrı varsayılan büyük/küçük harf duyarlı karşılaştırma kullandığından, çıktı cümleyi başlatan "The" dizesinin eşleşmediğini gösterir. Yöntem ' e <xref:System.Text.RegularExpressions.Regex.Match%2A> ayarlanmış seçeneklerle çağrıldığında <xref:System.Text.RegularExpressions.RegexOptions.IgnoreCase>eşleşir.

[!code-csharp[Conceptual.Regex.Language.Options#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.options/cs/case1.cs#1)]
[!code-vb[Conceptual.Regex.Language.Options#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.options/vb/case1.vb#1)]

Aşağıdaki örnek, önceki örnekteki normal ifade deseni, `options` büyük/küçük harf duyarsız karşılaştırması sağlamak için parametre yerine satır içi seçenekleri kullanmak üzere değiştirir. İlk desen, gruplandırma yapısında yalnızca "the" dizesindeki "t" harfine uygulanan büyük/küçük harf duyarsız seçeneğini tanımlar. Seçenek yapısı desenin başında oluştuğundan, ikinci desen tüm normal ifadeye büyük/küçük harf duyarsız seçeneğini uygular.

[!code-csharp[Conceptual.Regex.Language.Options#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.options/cs/case2.cs#2)]
[!code-vb[Conceptual.Regex.Language.Options#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.options/vb/case2.vb#2)]

## <a name="multiline-mode"></a>Çoklu Çizgi Modu

Seçenek <xref:System.Text.RegularExpressions.RegexOptions.Multiline?displayProperty=nameWithType> veya `m` satır çizgisi seçeneği, normal ifade altyapısının birden çok satırdan oluşan bir giriş dizesini işlemesini sağlar. Giriş dizesinin `^` başı `$` ve sonu yerine bir satırın başlangıcı ve sonuyla eşleşecek şekilde ve dil öğelerinin yorumlanmasını değiştirir.

Varsayılan olarak, `$` yalnızca giriş dizesinin sonuyla eşleşir. <xref:System.Text.RegularExpressions.RegexOptions.Multiline?displayProperty=nameWithType> Seçeneği belirtirseniz, yeni satır karakteriyle (`\n`) veya giriş dizesinin sonuyla eşleşir. Ancak, satır başı/satır besleme karakteri birleşimi ile eşleşmez. Bunları başarıyla eşleştirmek için, `\r?$` alt `$`ifadeyi sadece .

Aşağıdaki örnek bowlers'ın adlarını ve puanlarını <xref:System.Collections.Generic.SortedList%602> ayıklar ve bunları azalan sırada sıralayan bir koleksiyona ekler. Yöntem <xref:System.Text.RegularExpressions.Regex.Matches%2A> iki kez çağrılır. İlk yöntem çağrısında, normal ifade `^(\w+)\s(\d+)$` ve hiçbir seçenek ayarlanır. Çıktının gösterdiği gibi, normal ifade altyapısı giriş dizesinin başı ve sonuyla birlikte giriş deseniyle eşleşemediğinden, eşleşme bulunamadı. İkinci yöntem çağrısında, normal ifade değiştirilir `^(\w+)\s(\d+)\r?$` ve seçenekler <xref:System.Text.RegularExpressions.RegexOptions.Multiline?displayProperty=nameWithType>. Çıktının gösterdiği gibi, adlar ve skorlar başarıyla eşlenir ve puanlar azalan sırada görüntülenir.

[!code-csharp[Conceptual.Regex.Language.Options#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.options/cs/multiline1.cs#3)]
[!code-vb[Conceptual.Regex.Language.Options#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.options/vb/multiline1.vb#3)]

Normal ifade `^(\w+)\s(\d+)\r*$` deseni aşağıdaki tabloda gösterildiği gibi tanımlanır.

|Desen|Açıklama|
|-------------|-----------------|
|`^`|Sıranın başında başla.|
|`(\w+)`|Bir veya daha fazla sözcük karakteri eşleştir. Bu ilk yakalama grubudur.|
|`\s`|Bir boşluk karakteri ile eşleştirin.|
|`(\d+)`|Bir veya daha fazla ondalık basamağı eşleştirin. Bu ikinci yakalama grubudur.|
|`\r?`|Sıfır veya bir taşıma dönüş karakterini eşleştirin.|
|`$`|Hattın sonunda bit.|

Aşağıdaki örnek, çok satırlı seçeneği `(?m)` ayarlamak için satır satır seçeneğini kullanması dışında, öncekine eşdeğerdir.

[!code-csharp[Conceptual.Regex.Language.Options#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.options/cs/multiline2.cs#4)]
[!code-vb[Conceptual.Regex.Language.Options#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.options/vb/multiline2.vb#4)]

## <a name="single-line-mode"></a>Tek Satırlı Mod

Seçenek <xref:System.Text.RegularExpressions.RegexOptions.Singleline?displayProperty=nameWithType> veya satır `s` çizgisi seçeneği, normal ifade altyapısının giriş dizesini tek bir satırdan oluşuyormuş gibi ele almasına neden olur. Bunu, yeni çizgi karakteri`.` `\n` veya \u000A dışındaki her karakterle eşleşip her karakterle eşleşebilecek şekilde dönemin ( ) dil öğesinin davranışını değiştirerek yapar.

Aşağıdaki örnek, `.` <xref:System.Text.RegularExpressions.RegexOptions.Singleline?displayProperty=nameWithType> seçeneği kullandığınızda dil öğesinin davranışının nasıl değiştiğini göstermektedir. Normal ifade `^.+` dize başında başlar ve her karakter eşleşir. Varsayılan olarak, eşleşme ilk satırın sonunda sona erer; normal ifade deseni satır başı `\r` karakteriyle veya \u000D `\n`ile eşleşir, ancak bu durum . <xref:System.Text.RegularExpressions.RegexOptions.Singleline?displayProperty=nameWithType> Seçenek tüm giriş dizesini tek bir satır olarak yorumladığı için, giriş dizesindeki her karakterle `\n`eşleşir.

[!code-csharp[Conceptual.Regex.Language.CharacterClasses#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.characterclasses/cs/any2.cs#5)]
[!code-vb[Conceptual.Regex.Language.CharacterClasses#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.characterclasses/vb/any2.vb#5)]

Aşağıdaki örnek, tek satırlı modu etkinleştirmek için satır `(?s)` içi seçeneği kullanması dışında, öncekine eşdeğerdir.

[!code-csharp[Conceptual.Regex.Language.Options#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.options/cs/singleline1.cs#5)]
[!code-vb[Conceptual.Regex.Language.Options#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.options/vb/singleline1.vb#5)]

## <a name="explicit-captures-only"></a>Yalnızca Açık Yakalar

Varsayılan olarak, yakalama grupları normal ifade deseninde parantez kullanımı ile tanımlanır. Adlandırılmış gruplara `(?<` *ad*`>`*alt ifade* `)` dili seçeneğiyle bir ad veya sayı atanırken, adsız gruplara dizin tarafından erişilebilir. Nesnede, <xref:System.Text.RegularExpressions.GroupCollection> adlandırılmış gruplar adlandırılmış gruplardan önce gelir.

Gruplandırma yapıları genellikle yalnızca birden çok dil öğesine niceleyiciuygulamak için kullanılır ve yakalanan alt dizeleri ilgi çekici değildir. Örneğin, aşağıdaki normal ifade:

`\b\(?((\w+),?\s?)+[\.!?]\)?`

yalnızca bir belgeden bir dönem, ünlem işareti veya soru işaretiyle biten cümleleri ayıklamak için tasarlanmıştır, <xref:System.Text.RegularExpressions.Match> yalnızca ortaya çıkan tümce (nesne tarafından temsil edilir) ilgi çekicidir. Koleksiyondaki tek tek sözcükler değildir.

Normal ifade altyapısı hem toplama nesnelerini doldurması <xref:System.Text.RegularExpressions.GroupCollection> <xref:System.Text.RegularExpressions.CaptureCollection> gerektiğinden, daha sonra kullanılmayan grupları yakalama pahalı olabilir. Alternatif olarak, yalnızca geçerli <xref:System.Text.RegularExpressions.RegexOptions.ExplicitCapture?displayProperty=nameWithType> yakalamaların `n` `(?<` *ad* `>` *alt ifade* `)` yapısı tarafından atanan açık adlandırılmış veya numaralandırılmış gruplar olduğunu belirtmek için seçeneği veya satır satır daki seçeneği kullanabilirsiniz.

Aşağıdaki örnekte, `\b\(?((\w+),?\s?)+[\.!?]\)?` <xref:System.Text.RegularExpressions.Regex.Match%2A> yöntem <xref:System.Text.RegularExpressions.RegexOptions.ExplicitCapture?displayProperty=nameWithType> seçeneği ile ve seçenek olmadan çağrıldığında normal ifade deseni tarafından döndürülen eşleşmeler hakkında bilgi görüntülenir. İlk yöntem çağrısından çıktının gösterdiği gibi, normal ifade <xref:System.Text.RegularExpressions.GroupCollection> <xref:System.Text.RegularExpressions.CaptureCollection> altyapısı yakalanan alt dizeleri hakkında bilgi içeren ve toplama nesnelerini tam olarak doldurur. İkinci yöntem set ile `options` çağrıldığı için, <xref:System.Text.RegularExpressions.RegexOptions.ExplicitCapture?displayProperty=nameWithType>gruplar hakkında bilgi yakalamaz.

[!code-csharp[Conceptual.Regex.Language.Options#9](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.options/cs/explicit1.cs#9)]
[!code-vb[Conceptual.Regex.Language.Options#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.options/vb/explicit1.vb#9)]

Normal ifade`\b\(?((?>\w+),?\s?)+[\.!?]\)?` deseni aşağıdaki tabloda gösterildiği gibi tanımlanır.

|Desen|Açıklama|
|-------------|-----------------|
|`\b`|Bir sözcük sınırında niçin başlayın.|
|`\(?`|Açılış parantezinin sıfır veya bir olaylarını eşleştirin ("(").|
|`(?>\w+),?`|Bir veya daha fazla sözcük karakterini eşleştirin ve ardından sıfır veya bir virgül le eşleştirin. Sözcük karakterlerini eşleştirirken geri izlemeyin.|
|`\s?`|Sıfır veya bir beyaz boşluk karakterini eşleştirin.|
|`((\w+),?\s?)+`|Bir veya daha fazla sözcük karakteri, sıfır veya bir virgül ve sıfır veya bir beyaz boşluk karakterlerinin bir veya daha fazla kez birleşimini eşleştirin.|
|`[\.!?]\)?`|Üç noktalama işareti sembollerinden herhangi birini eşleştirin ve ardından sıfır veya bir kapanış parantezi (")") gelir.|

`(?n)` Otomatik yakalamaları bastırmak için satır içi öğeyi de kullanabilirsiniz. Aşağıdaki örnek, `(?n)` <xref:System.Text.RegularExpressions.RegexOptions.ExplicitCapture?displayProperty=nameWithType> seçenek yerine satır satır öğesini kullanmak için önceki normal ifade deseni değiştirir.

[!code-csharp[Conceptual.Regex.Language.Options#10](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.options/cs/explicit2.cs#10)]
[!code-vb[Conceptual.Regex.Language.Options#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.options/vb/explicit2.vb#10)]

Son olarak, otomatik yakalamaları `(?n:)` grup bazında bastırmak için satır içi grup öğesini kullanabilirsiniz. Aşağıdaki örnek, dış gruptaki adsız yakalamaları bastırmak için `((?>\w+),?\s?)`önceki deseni değiştirir. Bunun iç gruptaki isimsiz yakalamaları da bastırdığını unutmayın.

[!code-csharp[Conceptual.Regex.Language.Options#11](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.options/cs/explicit3.cs#11)]
[!code-vb[Conceptual.Regex.Language.Options#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.options/vb/explicit3.vb#11)]

## <a name="compiled-regular-expressions"></a>Derlenmiş Düzenli İfadeler

Varsayılan olarak, .NET'teki normal ifadeler yorumlanır. Bir <xref:System.Text.RegularExpressions.Regex> nesne anında veya statik <xref:System.Text.RegularExpressions.Regex> bir yöntem çağrıldığında, normal ifade deseni özel opcodes kümesine ayrıştırılır ve bir yorumlayıcı normal ifadeyi çalıştırmak için bu opcodes kullanır. Bu bir tradeoff içerir: Normal ifade altyapısı nın başlatılmasının maliyeti çalışma süresi performansı pahasına en aza indirilir.

Bu <xref:System.Text.RegularExpressions.RegexOptions.Compiled?displayProperty=nameWithType> seçeneği kullanarak, yorumlanmış normal ifadeler yerine derlenmiş ifadeleri kullanabilirsiniz. Bu durumda, bir desen normal ifade altyapısına geçirildiğinde, bir opcodes kümesine ayrıştırılır ve daha sonra doğrudan ortak dil çalışma süresine geçirilebilen Microsoft ara diline (MSIL) dönüştürülür. Derlenen düzenli ifadeler, başlatma zamanı pahasına çalışma zamanı performansını en üst düzeye çıkarır.

> [!NOTE]
> Normal bir ifade yalnızca bir <xref:System.Text.RegularExpressions.RegexOptions.Compiled?displayProperty=nameWithType> `options` <xref:System.Text.RegularExpressions.Regex> sınıf oluşturucu parametresi veya statik desen eşleştirme yöntemi nin parametresine değer sağlayarak derlenebilir. Satır satır seçeneği olarak kullanılamaz.

Derlenmiş normal ifadeleri hem statik hem de örnek normal ifadelere yapılan çağrılarda kullanabilirsiniz. Statik normal ifadelerde, <xref:System.Text.RegularExpressions.RegexOptions.Compiled?displayProperty=nameWithType> seçenek normal `options` ifade deseni eşleştirme yönteminin parametresine aktarılır. Örneğin normal ifadeler, `options` <xref:System.Text.RegularExpressions.Regex> sınıf oluşturucu parametregeçirilir. Her iki durumda da, gelişmiş performans ile sonuçlanır.

Ancak, performanstaki bu iyileşme yalnızca aşağıdaki koşullar altında gerçekleşir:

- Belirli <xref:System.Text.RegularExpressions.Regex> bir normal ifadeyi temsil eden bir nesne, normal ifade deseni eşleştirme yöntemlerine birden çok çağrıda kullanılır.

- Nesnenin <xref:System.Text.RegularExpressions.Regex> kapsam dışına çıkmasına izin verilmez, bu nedenle yeniden kullanılabilir.

- Statik bir normal ifade, normal ifade deseni eşleştirme yöntemlerine birden çok çağrıda kullanılır. (Statik yöntem çağrılarında kullanılan normal ifadeler normal ifade altyapısı tarafından önbelleğe alındırDığından performans geliştirme mümkündür.)

> [!NOTE]
> Seçenek, <xref:System.Text.RegularExpressions.RegexOptions.Compiled?displayProperty=nameWithType> önceden tanımlanmış <xref:System.Text.RegularExpressions.Regex.CompileToAssembly%2A?displayProperty=nameWithType> derlenmiş düzenli ifadeler içeren özel amaçlı bir derleme oluşturan yöntemle ilgisizdir.

## <a name="ignore-white-space"></a>Beyaz Uzayı Yoksay

Varsayılan olarak, normal bir ifade desenindeki beyaz boşluk önemlidir; normal ifade motorini giriş dizesindeki bir beyaz boşluk karakteriyle eşleşmeye zorlar. Bu nedenle, ""`\b\w+\s`ve "`\b\w+` " normal ifadeleri kabaca eşdeğerdir. Buna ek olarak, sayı işareti (#) normal bir ifade deseni ile karşılaşıldığında, eşlenecek gerçek bir karakter olarak yorumlanır.

Seçenek <xref:System.Text.RegularExpressions.RegexOptions.IgnorePatternWhitespace?displayProperty=nameWithType> veya satır `x` satırlı seçenek, bu varsayılan davranışı aşağıdaki gibi değiştirir:

- Normal ifade deseninde kaçamayan beyaz boşluk yoksayılır. Normal bir ifade deseninin parçası olmak için, beyaz boşluk karakterlerinin`\` (örneğin, " gibi veya " ") `\s` kaçması gerekir.

- Sayı işareti (#) gerçek bir karakter olarak değil, bir yorumun başlangıcı olarak yorumlanır. # karakterinden dize sonuna kadar normal ifade desenindeki tüm metin bir yorum olarak yorumlanır.

Ancak, aşağıdaki durumlarda, <xref:System.Text.RegularExpressions.RegexOptions.IgnorePatternWhitespace?displayProperty=nameWithType> seçeneği kullansanız bile normal bir ifadedeki beyaz boşluk karakterleri göz ardı edilmez:

- Karakter sınıfı içindeki beyaz boşluk her zaman tam anlamıyla yorumlanır. Örneğin, normal ifade `[ .,;:]` deseni herhangi bir beyaz boşluk karakteri, nokta, virgül, semicolon veya iki nokta eşleşir.

- `{`N , *n*`}` `{` *n*`,}` `{`ve *n*`,`*m*`}`gibi parantez li bir niceleme içinde beyaz alana izin verilmez. Örneğin, normal ifade `\d{1, 3}` deseni, bir beyaz boşluk karakteri içerdiğinden, bir ile üç basamak arasında herhangi bir basamak dizisini eşleştirmiyor.

- Bir dil öğesini tanıtan bir karakter dizisi içinde beyaz uzaya izin verilmez. Örneğin:

  - Dil öğesi `(?:` *alt ifadesi* `)` yakalamayan bir grubu `(?:` temsil eder ve öğenin bir bölümü katıştırılmış boşluklara sahip olamaz. Normal `(? :`ifade altyapısı deseni ayrışdıramadığı ve desen <xref:System.ArgumentException> `( ?:`alt ifadesi alt`)` *ifadeyle* `)` eşleşmediği için *subexpression*desen *alt ifadesi* çalışma zamanında bir atar.

  - Unicode `\p{`kategorisini veya adlandırılmış bloğu temsil eden dil öğesi *adı,*`}`öğenin bölümüne `\p{` katıştırılmış boşluklar içeremez. Beyaz bir boşluk eklerseniz, öğe çalışma <xref:System.ArgumentException> zamanında bir atar.

Bu seçeneği etkinleştirmek, ayrıştırması ve anlaşılması genellikle zor olan normal ifadeleri basitleştirmeye yardımcı olur. Okunabilirliği artırır ve düzenli bir ifadeyi belgeleyebilmeyi mümkün kılar.

Aşağıdaki örnekte aşağıdaki normal ifade deseni tanımlanır:

`\b \(? ( (?>\w+) ,?\s? )+  [\.!?] \)? # Matches an entire sentence.`

Bu desen, desen beyaz alanı [Explicit Captures Only](#explicit-captures-only) yoksayma <xref:System.Text.RegularExpressions.RegexOptions.IgnorePatternWhitespace?displayProperty=nameWithType> seçeneğini kullanması dışında, Yalnızca Açık Yakalar bölümünde tanımlanan desene benzer.

[!code-csharp[Conceptual.Regex.Language.Options#12](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.options/cs/whitespace1.cs#12)]
[!code-vb[Conceptual.Regex.Language.Options#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.options/vb/whitespace1.vb#12)]

Aşağıdaki örnek, desen beyaz `(?x)` alanı yoksaymak için satır içinde seçeneği kullanır.

[!code-csharp[Conceptual.Regex.Language.Options#13](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.options/cs/whitespace2.cs#13)]
[!code-vb[Conceptual.Regex.Language.Options#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.options/vb/whitespace2.vb#13)]

## <a name="right-to-left-mode"></a>Sağdan Sola Mod

Varsayılan olarak, normal ifade altyapısı soldan sağa arama. <xref:System.Text.RegularExpressions.RegexOptions.RightToLeft?displayProperty=nameWithType> Seçeneği kullanarak arama yönünü tersine çevirebilirsiniz. Arama otomatik olarak dize son karakter konumunda başlar. Başlangıç konumu parametresi gibi <xref:System.Text.RegularExpressions.Regex.Match%28System.String%2CSystem.Int32%29?displayProperty=nameWithType>bir başlangıç konumu parametresi içeren desen eşleştirme yöntemleri için, başlangıç konumu, aramanın başlayacağı en doğru karakter konumunun dizinidir.

> [!NOTE]
> Sağdan sola desen modu, <xref:System.Text.RegularExpressions.RegexOptions.RightToLeft?displayProperty=nameWithType> yalnızca bir `options` <xref:System.Text.RegularExpressions.Regex> sınıf oluşturucuveya statik desen eşleştirme yönteminin parametresine değer sağlayarak kullanılabilir. Satır satır seçeneği olarak kullanılamaz.

Seçenek <xref:System.Text.RegularExpressions.RegexOptions.RightToLeft?displayProperty=nameWithType> yalnızca arama yönünü değiştirir; normal ifade deseni sağdan sola yorumlamaz. Örneğin, normal ifade `\bb\w+\s` "b" harfiyle başlayan sözcüklerle eşleşir ve ardından beyaz boşluk karakteri gelir. Aşağıdaki örnekte, giriş dizesi bir veya daha fazla "b" karakterini içeren üç sözcükten oluşur. İlk sözcük "b" ile başlar, ikincisi "b" ile biter ve üçüncü sözcüğün ortasında iki "b" karakteri içerir. Örnekteki çıktının gösterdiği gibi, yalnızca ilk sözcük normal ifade deseniyle eşleşir.

[!code-csharp[Conceptual.Regex.Language.Options#17](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.options/cs/righttoleft1.cs#17)]
[!code-vb[Conceptual.Regex.Language.Options#17](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.options/vb/righttoleft1.vb#17)]

Ayrıca, ileriye dönük öneetme `(?=` *(alt ifade* `)` dili öğesi) ve `(?<=`lookbehind assertion *(alt ifade* `)` dili öğesi) yönünü değiştirmez unutmayın. İleriye dönük iddialar sağa bakar; iddiaların arkasındaki bakışlar sola bakar. Örneğin, normal ifade, `(?<=\d{1,2}\s)\w+,?\s\d{4}` bir ay adından önceki bir tarihi sınamak için lookbehind iddiasını kullanır. Normal ifade daha sonra ay ve yıl eşleşir. İleriye dönük ve ileriye dönük iddialar hakkında bilgi için, [Gruplandırma Yapıları'na](../../../docs/standard/base-types/grouping-constructs-in-regular-expressions.md)bakın.

[!code-csharp[Conceptual.Regex.Language.Options#18](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.options/cs/righttoleft2.cs#18)]
[!code-vb[Conceptual.Regex.Language.Options#18](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.options/vb/righttoleft2.vb#18)]

Normal ifade deseni aşağıdaki tabloda gösterildiği gibi tanımlanır.

|Desen|Açıklama|
|-------------|-----------------|
|`(?<=\d{1,2}\s)`|Maçın başında bir veya iki ondalık basamak ve ardından bir boşluk olmalıdır.|
|`\w+`|Bir veya daha fazla sözcük karakteri eşleştir.|
|`,?`|Sıfır veya bir virgül karakterlerini eşleştirin.|
|`\s`|Bir boşluk karakteri ile eşleştirin.|
|`\d{4}`|Dört ondalık basamakeşleştirin.|

## <a name="ecmascript-matching-behavior"></a>ECMAScript Eşleştirme Davranışı

Varsayılan olarak, normal ifade altyapısı, giriş metniyle normal bir ifade deseni eşleştirirken kanonik davranış kullanır. Ancak, normal ifade altyapısına <xref:System.Text.RegularExpressions.RegexOptions.ECMAScript?displayProperty=nameWithType> seçeneği belirterek ECMAScript eşleştirme davranışını kullanmasını talimatı verebilirsiniz.

> [!NOTE]
> ECMAScript uyumlu davranış, yalnızca bir <xref:System.Text.RegularExpressions.RegexOptions.ECMAScript?displayProperty=nameWithType> `options` <xref:System.Text.RegularExpressions.Regex> sınıf oluşturucuveya statik desen eşleştirme yönteminin parametresine değer sağlayarak kullanılabilir. Satır satır seçeneği olarak kullanılamaz.

Seçenek <xref:System.Text.RegularExpressions.RegexOptions.ECMAScript?displayProperty=nameWithType> yalnızca ve <xref:System.Text.RegularExpressions.RegexOptions.IgnoreCase?displayProperty=nameWithType> <xref:System.Text.RegularExpressions.RegexOptions.Multiline?displayProperty=nameWithType> seçenekleri ile kombine edilebilir. Normal bir ifadede başka bir seçeneğin <xref:System.ArgumentOutOfRangeException>kullanılması ,

ECMAScript ve kanonik normal ifadelerin davranışı üç alanda farklılık gösterir: karakter sınıfı sözdizimi, kendi kendine başvuran yakalama grupları ve sekize karşı backreference yorumu.

- Karakter sınıfı sözdizimi. Kanonik normal ifadeler Unicode'u desteklediğinden, ECMAScript'teki karakter sınıflarının daha sınırlı bir sözdizimi vardır ve bazı karakter sınıfı dil öğelerinin farklı bir anlamı vardır. Örneğin, ECMAScript Unicode kategorisi veya blok öğeleri `\p` ve . `\P` Benzer şekilde, `\w` bir sözcük karakteriyle eşleşen öğe, ECMAScript kullanırken `[\p{Ll}\p{Lu}\p{Lt}\p{Lo}\p{Nd}\p{Pc}\p{Lm}]` ve kanonik davranış kullanırken `[a-zA-Z_0-9]` karakter sınıfına eşdeğerdir. Daha fazla bilgi için [Karakter Sınıfları'na](../../../docs/standard/base-types/character-classes-in-regular-expressions.md)bakın.

  Aşağıdaki örnek, kanonik ve ECMAScript desen eşleştirme arasındaki farkı göstermektedir. Normal bir ifade tanımlar, `\b(\w+\s*)+`beyaz boşluk karakterleri tarafından takip edilen sözcüklerle eşleşir. Giriş, biri Latin karakter kümesini, diğeri kiril karakter kümesini kullanan iki dizeden oluşur. Çıktının gösterdiği gibi, ECMAScript eşlemeyi kullanan <xref:System.Text.RegularExpressions.Regex.IsMatch%28System.String%2CSystem.String%2CSystem.Text.RegularExpressions.RegexOptions%29?displayProperty=nameWithType> yönteme yapılan çağrı Kiril sözcüklerle eşleşmezken, kanonik eşleştirme kullanan yöntem çağrısı bu sözcüklerle eşleşir.

  [!code-csharp[Conceptual.Regex.Language.Options#16](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.options/cs/ecmascript1.cs#16)]
  [!code-vb[Conceptual.Regex.Language.Options#16](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.options/vb/ecmascript1.vb#16)]

- Yakalama gruplarının kendi kendine başvurması. Kendisine bir geri başvuru ile normal bir ifade yakalama sınıfı her yakalama yineleme ile güncelleştirilmelidir. Aşağıdaki örnekte de görüldüğü gibi, bu `((a+)(\1) ?)+` özellik, ECMAScript kullanırken " aa aaaa aaaaaa " giriş dizesini eşleştirmek için normal ifadeyi sağlar, ancak standart eşleme kullanırken değil.

  [!code-csharp[Conceptual.Regex.Language.Options#21](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.options/cs/ecmascript2.cs#21)]
  [!code-vb[Conceptual.Regex.Language.Options#21](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.options/vb/ecmascript2.vb#21)]

  Normal ifade aşağıdaki tabloda gösterildiği gibi tanımlanır.

  |Desen|Açıklama|
  |-------------|-----------------|
  |(a+)|"A" harfini bir veya daha fazla kez eşleştirin. Bu ikinci yakalama grubudur.|
  |(\1)|İlk yakalama grubu tarafından yakalanan alt dize eşleştirin. Bu, üçüncü yakalama grubudur.|
  |?|Sıfır veya bir boşluk karakterlerini eşleştirin.|
  |((a+)(\1) ?) +|Bir veya daha fazla "a" karakterinin deseniyle eşleşin ve ardından ilk yakalama grubuyla eşleşen ve ardından sıfır veya bir boşluk karakteriyle bir veya daha fazla kez eşleşen bir dize eşleştirin. Bu ilk yakalama grubudur.|

- Sekizli kaçışlar ve geri dönüşler arasındaki belirsizliklerin çözümü. Aşağıdaki tabloda, kanonik ve ECMAScript düzenli ifadeleri ile sekizli ve backreference yorumlama daki farklılıkları özetleyebiliriz.

  |Normal ifade|Kanonik davranış|ECMAScript davranışı|
  |------------------------|------------------------|-------------------------|
  |`\0`0-2 okta basamağı takip|Oksal olarak yorumla. Örneğin, `\044` her zaman bir oksal değer olarak yorumlanır ve "$" anlamına gelir.|Aynı davranış.|
  |`\`1'den 9'a kadar bir basamak, ardından ek ondalık basamaklar,|Bir backreference olarak yorumlayın. Örneğin, `\9` dokuzuncu yakalama grubu olmasa bile, her zaman geri başvuru 9 anlamına gelir. Yakalama grubu yoksa, normal ifade parıcısı bir <xref:System.ArgumentException>.|Tek bir ondalık basamak yakalama grubu varsa, bu rakama geri başvurun. Aksi takdirde, değeri gerçek olarak yorumlayın.|
  |`\`ardından 1'den 9'a kadar bir basamak, ardından ek ondalık basamaklar|Basamakları ondalık değer olarak yorumlayın. Bu yakalama grubu varsa, ifadeyi bir geri başvuru olarak yorumlayın.<br /><br /> Aksi takdirde, octal 377 kadar önde gelen sekizli basamakları yorumlamak; diğer bir şey, değerin yalnızca düşük 8 bitini göz önünde bulundurun. Kalan basamakları gerçek olarak yorumlayın. Örneğin, "300 grubunu yakalama" ifadesinde, `\3000`geri başvuru 300 olarak yorumlayın; yakalama grubu 300 yoksa, okt 300 ve ardından 0 olarak yorumlayın.|Bir yakalama yada bir ondalık değer mümkün olduğunca çok sayıda basamak dönüştürerek bir backreference olarak yorumlayın. Hiçbir basamak dönüştürülemezse, 377'ye kadar olan önde gelen sekizli basamakları kullanarak sekizli olarak yorumlayın; kalan basamakları gerçek olarak yorumlayın.|

## <a name="comparison-using-the-invariant-culture"></a>Değişmez Kültürü Kullanarak Karşılaştırma

Varsayılan olarak, normal ifade altyapısı büyük/küçük harf li karşılaştırmalar yaptığında, eşdeğer büyük harf ve küçük harfleri belirlemek için geçerli kültürün kasa kurallarını kullanır.

Ancak, bu davranış, özellikle kullanıcı girişini parolalar, dosyalar veya URL'ler gibi sistem kaynaklarının adlarıyla karşılaştırırken, bazı karşılaştırma türleri için istenmeyen bir durumdur. Aşağıdaki örnekte senaryo gibi gösteriş. Kod, URL'si **FILE://** ile önceden karşılanmış olan herhangi bir kaynağa erişimi engellemek için tasarlanmıştır. Normal ifade, normal ifadeyi `$FILE://`kullanarak dize ile duyarsız bir eşleşme dener. Ancak mevcut sistem kültürü TR-TR (Türk-Türkiye) olduğunda "i" büyük harf karşılığı değildir. Sonuç olarak, <xref:System.Text.RegularExpressions.Regex.IsMatch%2A?displayProperty=nameWithType> yönteme çağrı `false`döndürür ve dosyaya erişime izin verilir.

[!code-csharp[Conceptual.Regex.Language.Options#14](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.options/cs/culture1.cs#14)]
[!code-vb[Conceptual.Regex.Language.Options#14](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.options/vb/culture1.vb#14)]

> [!NOTE]
> Büyük/küçük harf duyarlı ve değişmez kültürü kullanan dize karşılaştırmaları hakkında daha fazla bilgi [için, Dizeleri Kullanmak için En İyi Uygulamalar'a](../../../docs/standard/base-types/best-practices-strings.md)bakın.

Geçerli kültürün karşıt lık karşılaştırmalarını kullanmak yerine, dildeki <xref:System.Text.RegularExpressions.RegexOptions.CultureInvariant?displayProperty=nameWithType> kültürel farklılıkları yoksayma ve değişmez kültürün kurallarını kullanma seçeneğini belirtebilirsiniz.

> [!NOTE]
> Değişmez kültür kullanılarak karşılaştırma yalnızca bir <xref:System.Text.RegularExpressions.RegexOptions.CultureInvariant?displayProperty=nameWithType> `options` <xref:System.Text.RegularExpressions.Regex> sınıf oluşturucu veya statik desen eşleştirme yönteminin parametredeğeri sağlayarak kullanılabilir. Satır satır seçeneği olarak kullanılamaz.

Aşağıdaki örnek, statik <xref:System.Text.RegularExpressions.Regex.IsMatch%28System.String%2CSystem.String%2CSystem.Text.RegularExpressions.RegexOptions%29?displayProperty=nameWithType> yöntemin . <xref:System.Text.RegularExpressions.RegexOptions.CultureInvariant?displayProperty=nameWithType> Geçerli kültür Türkçe (Türkiye) olarak ayarlandığında bile, normal ifade altyapısı "FILE" ve "file"yi başarıyla eşleştirebiliyor ve dosya kaynağına erişimi engelleyebilir.

[!code-csharp[Conceptual.Regex.Language.Options#15](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.options/cs/culture1.cs#15)]
[!code-vb[Conceptual.Regex.Language.Options#15](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.options/vb/culture1.vb#15)]

## <a name="see-also"></a>Ayrıca bkz.

- [Normal İfade Dili - Hızlı Başvuru](../../../docs/standard/base-types/regular-expression-language-quick-reference.md)
