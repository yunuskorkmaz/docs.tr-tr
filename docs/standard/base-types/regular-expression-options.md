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
ms.openlocfilehash: 8c742c855234bfd9653bb57036c41e7ccce66295
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84289297"
---
# <a name="regular-expression-options"></a>Normal İfade Seçenekleri

Varsayılan olarak, bir giriş dizesinin normal ifade deseninin herhangi bir sabit karakter ile karşılaştırılması büyük/küçük harfe duyarlıdır, bir normal ifade deseninin boşluk değeri değişmez boşluk karakterleri olarak yorumlanır ve normal bir ifadede yakalama grupları örtük olarak ve açıkça adlandırılmaktadır. Normal ifade seçeneklerini belirterek, varsayılan normal ifade davranışının bu ve diğer birçok yönlerini değiştirebilirsiniz. Aşağıdaki tabloda listelenen bu seçenekler, normal ifade deseninin bir parçası olarak satır içi olarak dahil edilebilir veya bir <xref:System.Text.RegularExpressions.Regex?displayProperty=nameWithType> sınıf oluşturucusuna veya statik model eşleştirme yöntemine bir <xref:System.Text.RegularExpressions.RegexOptions?displayProperty=nameWithType> numaralandırma değeri olarak sağlanabilir.

|RegexOptions üyesi|Satır içi karakter|Etki|
|-------------------------|----------------------|------------|
|<xref:System.Text.RegularExpressions.RegexOptions.None>|Kullanılamaz|Varsayılan davranışı kullanın. Daha fazla bilgi için bkz. [varsayılan seçenekler](#default-options).|
|<xref:System.Text.RegularExpressions.RegexOptions.IgnoreCase>|`i`|Büyük küçük harf duyarlı eşleme kullanın. Daha fazla bilgi için bkz. [büyük/küçük harfe duyarsız eşleşme](#case-insensitive-matching).|
|<xref:System.Text.RegularExpressions.RegexOptions.Multiline>|`m`|Her satırın başlangıcını ve bitişini `^` `$` (giriş dizesinin başı ve sonu yerine) ve sonuna kadar çok satırlı modunu kullanın. Daha fazla bilgi için bkz. [çok satırlı mod](#multiline-mode).|
|<xref:System.Text.RegularExpressions.RegexOptions.Singleline>|`s`|Tek satır modunu kullanın; burada nokta (.) her karakterle eşleşir (hariç her karakter yerine `\n` ). Daha fazla bilgi için bkz. [tek satırlık mod](#single-line-mode).|
|<xref:System.Text.RegularExpressions.RegexOptions.ExplicitCapture>|`n`|Adsız grupları yakalamayın. Yalnızca geçerli yakalamalar, form adı alt ifadesinin açıkça adlandırılmış veya numaralandırılmış gruplarıdır `(?<` *name* `>` *subexpression* `)` . Daha fazla bilgi için [yalnızca açık yakalamalar](#explicit-captures-only)bölümüne bakın.|
|<xref:System.Text.RegularExpressions.RegexOptions.Compiled>|Kullanılamaz|Normal ifadeyi bir derleme için derleyin. Daha fazla bilgi için bkz. [derlenmiş normal ifadeler](#compiled-regular-expressions).|
|<xref:System.Text.RegularExpressions.RegexOptions.IgnorePatternWhitespace>|`x`|Kaçışsız boşluğu düzeninden hariç tutun ve bir sayı işaretinden () sonra açıklamaları etkinleştirin `#` . Daha fazla bilgi için bkz. boşluğu [Yoksay](#ignore-white-space).|
|<xref:System.Text.RegularExpressions.RegexOptions.RightToLeft>|Kullanılamaz|Arama yönünü değiştirin. Arama, soldan sağa yerine sağdan sola gider. Daha fazla bilgi için bkz. [sağdan sola mod](#right-to-left-mode).|
|<xref:System.Text.RegularExpressions.RegexOptions.ECMAScript>|Kullanılamaz|İfade için ECMAScript uyumlu davranışı etkinleştirin. Daha fazla bilgi için bkz. [ECMAScript eşleştirme davranışı](#ecmascript-matching-behavior).|
|<xref:System.Text.RegularExpressions.RegexOptions.CultureInvariant>|Kullanılamaz|Dildeki kültürel farklarını yoksayın. Daha fazla bilgi için bkz. [sabit kültür kullanılarak karşılaştırma](#comparison-using-the-invariant-culture).|

## <a name="specifying-the-options"></a>Seçenekleri belirtme

Normal ifadeler için seçenekleri üç şekilde belirtebilirsiniz:

- `options`Bir sınıf oluşturucusunun parametresinde veya bir <xref:System.Text.RegularExpressions.Regex?displayProperty=nameWithType> statik ( `Shared` Visual Basic), veya gibi bir model eşleme yöntemi <xref:System.Text.RegularExpressions.Regex.%23ctor%28System.String%2CSystem.Text.RegularExpressions.RegexOptions%29> <xref:System.Text.RegularExpressions.Regex.Match%28System.String%2CSystem.String%2CSystem.Text.RegularExpressions.RegexOptions%29?displayProperty=nameWithType> . `options`Parametresi, numaralandırılmış değerlerin bit SEVIYESINDE veya birleşimidir <xref:System.Text.RegularExpressions.RegexOptions?displayProperty=nameWithType> .

  Bir <xref:System.Text.RegularExpressions.Regex> sınıf oluşturucusunun parametresi kullanılarak bir örneğe seçenekler sağlandığında `options` , Seçenekler <xref:System.Text.RegularExpressions.RegexOptions?displayProperty=nameWithType> özelliğine atanır. Ancak, <xref:System.Text.RegularExpressions.RegexOptions?displayProperty=nameWithType> özelliği normal ifade deseninin kendi satır içi seçeneklerini yansıtmaz.

  Aşağıdaki örnek, bir gösterim sağlar. `options` <xref:System.Text.RegularExpressions.Regex.Match%28System.String%2CSystem.String%2CSystem.Text.RegularExpressions.RegexOptions%29?displayProperty=nameWithType> Büyük/küçük harfe duyarsız eşleştirmeyi etkinleştirmek için yönteminin parametresini kullanır ve "d" harfiyle başlayan sözcükleri tanımlarken kalıp uzayını yok saymaya dönüştürür.

  [!code-csharp[Conceptual.Regex.Language.Options#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.options/cs/example1.cs#6)]
  [!code-vb[Conceptual.Regex.Language.Options#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.options/vb/example1.vb#6)]

- Bir normal ifade deseninin sözdizimi ile satır içi seçenekler uygulayarak `(?imnsx-imnsx)` . Seçeneği, seçeneğinin düzenin sonuna kadar veya başka bir satır içi seçenek tarafından tanımsız olan nokta için geçerli olan nokta için geçerlidir. <xref:System.Text.RegularExpressions.RegexOptions?displayProperty=nameWithType> <xref:System.Text.RegularExpressions.Regex> Örneğin özelliğinin bu satır içi seçenekleri yansıtmadığını unutmayın. Daha fazla bilgi için bkz. [çeşitli yapılar](miscellaneous-constructs-in-regular-expressions.md) konusu.

  Aşağıdaki örnek, bir gösterim sağlar. Büyük/küçük harfe duyarsız eşleştirmeyi etkinleştirmek ve "d" harfiyle başlayan sözcükleri tanımlarken kalıp boşluk yoksaymak için satır içi seçenekleri kullanır.

  [!code-csharp[Conceptual.Regex.Language.Options#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.options/cs/example1.cs#7)]
  [!code-vb[Conceptual.Regex.Language.Options#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.options/vb/example1.vb#7)]

- Belirli bir gruplama yapısına, sözdizimi alt ifadesi ile bir normal ifade düzeninde satır içi seçenekler uygulayarak `(?imnsx-imnsx:` *subexpression* `)` . Bir seçenek kümesinden önce hiçbir işaret, kümeyi açmadan önce hiçbir işaret yoktur; bir seçenek kümesinden önceki bir eksi işareti, kümeyi devre dışı bırakır. ( `?` seçeneklerin etkin veya devre dışı bırakılmış olması gereken dil yapısı sözdiziminin sabit bir parçasıdır.) Seçeneği yalnızca bu grup için geçerlidir. Daha fazla bilgi için bkz. [yapıları gruplandırma](grouping-constructs-in-regular-expressions.md).

  Aşağıdaki örnek, bir gösterim sağlar. Büyük/küçük harfe duyarsız eşleştirmeyi etkinleştirmek ve "d" harfiyle başlayan sözcükleri tanımlarken kalıp boşluk yoksaymak için bir gruplama yapısında satır içi seçenekleri kullanır.

  [!code-csharp[Conceptual.Regex.Language.Options#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.options/cs/example1.cs#8)]
  [!code-vb[Conceptual.Regex.Language.Options#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.options/vb/example1.vb#8)]

Seçenekler satır içi belirtilirse, `-` bir seçenek veya seçenek kümesinden önce bir eksi işareti (), bu seçenekleri devre dışı bırakır. Örneğin, satır içi yapı `(?ix-ms)` ve seçeneklerini etkinleştirir ve <xref:System.Text.RegularExpressions.RegexOptions.IgnoreCase?displayProperty=nameWithType> <xref:System.Text.RegularExpressions.RegexOptions.IgnorePatternWhitespace?displayProperty=nameWithType> ve seçeneklerini devre dışı bırakır <xref:System.Text.RegularExpressions.RegexOptions.Multiline?displayProperty=nameWithType> <xref:System.Text.RegularExpressions.RegexOptions.Singleline?displayProperty=nameWithType> . Tüm normal ifade seçenekleri varsayılan olarak kapalıdır.

> [!NOTE]
> `options`Bir oluşturucunun veya yöntem çağrısının parametresinde belirtilen normal ifade seçenekleri bir normal ifade düzeninde satır içi belirtilen seçeneklerle çakışırsa, satır içi seçenekler kullanılır.

Aşağıdaki beş normal ifade seçeneği, hem Options parametresiyle hem de satır içi olarak ayarlanabilir:

- <xref:System.Text.RegularExpressions.RegexOptions.IgnoreCase?displayProperty=nameWithType>

- <xref:System.Text.RegularExpressions.RegexOptions.Multiline?displayProperty=nameWithType>

- <xref:System.Text.RegularExpressions.RegexOptions.Singleline?displayProperty=nameWithType>

- <xref:System.Text.RegularExpressions.RegexOptions.ExplicitCapture?displayProperty=nameWithType>

- <xref:System.Text.RegularExpressions.RegexOptions.IgnorePatternWhitespace?displayProperty=nameWithType>

Aşağıdaki beş normal ifade seçeneği parametresi kullanılarak ayarlanabilir, `options` ancak satır içi ayarlanamaz:

- <xref:System.Text.RegularExpressions.RegexOptions.None?displayProperty=nameWithType>

- <xref:System.Text.RegularExpressions.RegexOptions.Compiled?displayProperty=nameWithType>

- <xref:System.Text.RegularExpressions.RegexOptions.RightToLeft?displayProperty=nameWithType>

- <xref:System.Text.RegularExpressions.RegexOptions.CultureInvariant?displayProperty=nameWithType>

- <xref:System.Text.RegularExpressions.RegexOptions.ECMAScript?displayProperty=nameWithType>

## <a name="determining-the-options"></a>Seçenekleri belirleme

<xref:System.Text.RegularExpressions.Regex>Salt okunurdur özelliğinin değeri alınırken, bir nesneye hangi seçeneklerin sağlandığını belirleyebilirsiniz <xref:System.Text.RegularExpressions.Regex.Options%2A?displayProperty=nameWithType> . Bu özellik özellikle yöntemi tarafından oluşturulan derlenmiş bir normal ifade için tanımlanan seçenekleri belirlemek için yararlıdır <xref:System.Text.RegularExpressions.Regex.CompileToAssembly%2A?displayProperty=nameWithType> .

Dışında herhangi bir seçeneğin varlığını test etmek için <xref:System.Text.RegularExpressions.RegexOptions.None?displayProperty=nameWithType> , <xref:System.Text.RegularExpressions.Regex.Options%2A?displayProperty=nameWithType> özelliğinin değeri ve ilgilendiğiniz değer Ile bir ve işlemi gerçekleştirin <xref:System.Text.RegularExpressions.RegexOptions> . Sonra sonucun bu değere eşit olup olmadığını test edin <xref:System.Text.RegularExpressions.RegexOptions> . Aşağıdaki örnek, seçeneğinin ayarlanmış olup olmadığını sınar <xref:System.Text.RegularExpressions.RegexOptions.IgnoreCase?displayProperty=nameWithType> .

[!code-csharp[Conceptual.Regex.Language.Options#19](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.options/cs/determine1.cs#19)]
[!code-vb[Conceptual.Regex.Language.Options#19](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.options/vb/determine1.vb#19)]

Test etmek için, <xref:System.Text.RegularExpressions.RegexOptions.None?displayProperty=nameWithType> <xref:System.Text.RegularExpressions.Regex.Options%2A?displayProperty=nameWithType> Aşağıdaki örnekte gösterildiği gibi, özelliğin değerinin değerine eşit olup olmadığını saptayın <xref:System.Text.RegularExpressions.RegexOptions.None?displayProperty=nameWithType> .

[!code-csharp[Conceptual.Regex.Language.Options#20](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.options/cs/determine1.cs#20)]
[!code-vb[Conceptual.Regex.Language.Options#20](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.options/vb/determine1.vb#20)]

Aşağıdaki bölümlerde, .NET içindeki normal ifade tarafından desteklenen seçenekler listelenmektedir.

## <a name="default-options"></a>Varsayılan Seçenekler

<xref:System.Text.RegularExpressions.RegexOptions.None?displayProperty=nameWithType>Seçeneği hiçbir seçeneğin belirtilmediğini ve normal ifade altyapısının varsayılan davranışını kullandığını gösterir. Bu, aşağıdakileri içerir:

- Desenler, ECMAScript normal ifadesi yerine kurallı olarak yorumlanır.

- Normal ifade deseninin giriş dizesinde soldan sağa eşleşmesi vardır.

- Karşılaştırmalar büyük/küçük harfe duyarlıdır.

- `^`Ve `$` Language öğeleri giriş dizesinin başlangıcı ve sonu ile eşleşir.

- `.`Language öğesi, hariç her karakterle eşleşir `\n` .

- Normal ifade düzenindeki herhangi bir boşluk, sabit bir boşluk karakteri olarak yorumlanır.

- Geçerli kültürün kuralları, model giriş dizesiyle karşılaştırılırken kullanılır.

- Normal ifade düzeninde yakalama grupları örtük ve açık olarak açıktır.

> [!NOTE]
> <xref:System.Text.RegularExpressions.RegexOptions.None?displayProperty=nameWithType>Seçeneğin satır içi eşdeğeri yoktur. Normal ifade seçenekleri satır içi uygulandığında, özel bir seçenek devre dışı bırakarak varsayılan davranış bir seçenek temelinde geri yüklenir. Örneğin, `(?i)` büyük/küçük harfe duyarsız karşılaştırmayı açar ve `(?-i)` varsayılan büyük/küçük harfe duyarlı karşılaştırmayı geri yükler.

Seçeneği, <xref:System.Text.RegularExpressions.RegexOptions.None?displayProperty=nameWithType> normal ifade altyapısının varsayılan davranışını temsil ettiğinden, yöntem çağrısında nadiren açıkça belirtilir. Yerine parametresi olmayan bir Oluşturucu veya statik bir model eşleştirme yöntemi `options` çağırılır.

## <a name="case-insensitive-matching"></a>Büyük/küçük harfe duyarsız eşleşme

<xref:System.Text.RegularExpressions.RegexOptions.IgnoreCase>Seçeneği veya `i` satır içi seçeneği, büyük/küçük harfe duyarsız eşleşme sağlar. Varsayılan olarak, geçerli kültürün büyük/küçük harf kuralları kullanılır.

Aşağıdaki örnek, `\bthe\w*\b` "The" ile başlayan tüm sözcüklerle eşleşen bir normal ifade deseninin tanımlar. Yönteme ilk çağrı <xref:System.Text.RegularExpressions.Regex.Match%2A> varsayılan büyük/küçük harfe duyarlı karşılaştırmayı kullandığından, çıkış, tümceyi Başlatan "The" dizesinin eşleştirilmediğini belirtir. <xref:System.Text.RegularExpressions.Regex.Match%2A>Yöntemi, olarak ayarlanan seçenekler ile çağrıldığında eşleşir <xref:System.Text.RegularExpressions.RegexOptions.IgnoreCase> .

[!code-csharp[Conceptual.Regex.Language.Options#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.options/cs/case1.cs#1)]
[!code-vb[Conceptual.Regex.Language.Options#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.options/vb/case1.vb#1)]

Aşağıdaki örnek, önceki örnekteki normal ifade deseninin, `options` büyük/küçük harfe duyarsız karşılaştırma sağlamak için parametresi yerine satır içi seçenekler kullanması için değiştirir. İlk model, yalnızca "The" dizesinde "t" harfine uygulanan bir gruplama yapısında büyük/küçük harf duyarsız seçeneğini tanımlar. Seçenek yapısı deseninin başlangıcında gerçekleştiğinden, ikinci model büyük/küçük harf duyarsız seçeneğini normal ifadeye uygular.

[!code-csharp[Conceptual.Regex.Language.Options#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.options/cs/case2.cs#2)]
[!code-vb[Conceptual.Regex.Language.Options#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.options/vb/case2.vb#2)]

## <a name="multiline-mode"></a>Çok satırlı mod

<xref:System.Text.RegularExpressions.RegexOptions.Multiline?displayProperty=nameWithType>Seçeneği veya `m` satır içi seçeneği, normal ifade altyapısının birden çok satırdan oluşan bir giriş dizesini işlemesini sağlar. `^`Ve `$` dili öğelerinin yorumu, giriş dizesinin başı ve sonu yerine bir satırın başlangıcıyla ve sonuyla eşleşecek şekilde değişir.

Varsayılan olarak, `$` yalnızca giriş dizesinin sonu ile eşleşir. <xref:System.Text.RegularExpressions.RegexOptions.Multiline?displayProperty=nameWithType>Seçeneğini belirtirseniz, bu, yeni satır karakteriyle ( `\n` ) veya giriş dizesinin sonuyla eşleşir. Ancak, satır başı/satır besleme karakteri bileşimiyle eşleşmez. Bunları başarıyla eşleştirmek için, yalnızca yerine alt ifadeyi kullanın `\r?$` `$` .

Aşağıdaki örnek Bowler adlarını ve puanlarını ayıklar ve bunları <xref:System.Collections.Generic.SortedList%602> azalan sırada sıralayan bir koleksiyona ekler. <xref:System.Text.RegularExpressions.Regex.Matches%2A>Yöntemi iki kez çağrılır. İlk yöntem çağrısında, normal ifade değildir `^(\w+)\s(\d+)$` ve hiçbir seçenek ayarlanmadı. Çıktının gösterdiği gibi, normal ifade altyapısı giriş deseninin yanı sıra giriş dizesinin başlangıcı ve sonuyla eşleşeceğinden, hiçbir eşleşme bulunamamıştır. İkinci yöntem çağrısında, normal ifade olarak değiştirilir `^(\w+)\s(\d+)\r?$` ve seçenekler olarak ayarlanır <xref:System.Text.RegularExpressions.RegexOptions.Multiline?displayProperty=nameWithType> . Çıktıda gösterildiği gibi, adlar ve puanlar başarıyla eşleştirilir ve puanlar azalan sırada görüntülenir.

[!code-csharp[Conceptual.Regex.Language.Options#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.options/cs/multiline1.cs#3)]
[!code-vb[Conceptual.Regex.Language.Options#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.options/vb/multiline1.vb#3)]

Normal ifade deseninin, `^(\w+)\s(\d+)\r*$` Aşağıdaki tabloda gösterildiği gibi tanımlanmıştır.

|Desen|Description|
|-------------|-----------------|
|`^`|Satırın başlangıcında başlayın.|
|`(\w+)`|Bir veya daha fazla sözcük karakteri eşleştir. Bu ilk yakalama grubudur.|
|`\s`|Bir boşluk karakteri ile eşleştirin.|
|`(\d+)`|Bir veya daha fazla ondalık basamağı eşleştirin. Bu ikinci yakalama grubudur.|
|`\r?`|Sıfır veya bir satır başı karakteri eşleştirin.|
|`$`|Satırın sonunda biter.|

Aşağıdaki örnek, tek `(?m)` satırlı seçeneğini ayarlamak için satır içi seçeneğini kullanması dışında, öncekiyle eşdeğerdir.

[!code-csharp[Conceptual.Regex.Language.Options#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.options/cs/multiline2.cs#4)]
[!code-vb[Conceptual.Regex.Language.Options#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.options/vb/multiline2.vb#4)]

## <a name="single-line-mode"></a>Tek satırlık mod

<xref:System.Text.RegularExpressions.RegexOptions.Singleline?displayProperty=nameWithType>Seçeneği veya `s` satır içi seçeneği, normal ifade altyapısının giriş dizesini tek bir satırdan oluşan gibi işleme almasına neden olur. Bu, nokta ( `.` ) dil öğesinin davranışını, yeni satır karakteri `\n` veya \u000ahariç her karakteri eşleştirmek yerine her karakterle eşleşecek şekilde değiştirerek yapar.

Aşağıdaki örnek, `.` seçeneğini kullandığınızda Language öğesi davranışının nasıl değiştiği gösterilmektedir <xref:System.Text.RegularExpressions.RegexOptions.Singleline?displayProperty=nameWithType> . Normal ifade `^.+` dizenin başlangıcında başlar ve her karakterle eşleşir. Varsayılan olarak eşleştirme, ilk satırın sonunda biter; normal ifade deseninin satır dönüş karakteriyle `\r` veya \u000D ile eşleşmesi, ancak eşleşmez `\n` . <xref:System.Text.RegularExpressions.RegexOptions.Singleline?displayProperty=nameWithType>Seçeneği giriş dizesinin tamamını tek bir satır olarak yorumladığından, dahil olmak üzere giriş dizesindeki her karakterle eşleşir `\n` .

[!code-csharp[Conceptual.Regex.Language.CharacterClasses#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.characterclasses/cs/any2.cs#5)]
[!code-vb[Conceptual.Regex.Language.CharacterClasses#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.characterclasses/vb/any2.vb#5)]

Aşağıdaki örnek, `(?s)` tek satır modunu etkinleştirmek için satır içi seçeneğini kullanması dışında, önceki bir ile eşdeğerdir.

[!code-csharp[Conceptual.Regex.Language.Options#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.options/cs/singleline1.cs#5)]
[!code-vb[Conceptual.Regex.Language.Options#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.options/vb/singleline1.vb#5)]

## <a name="explicit-captures-only"></a>Yalnızca açık yakalamalar

Varsayılan olarak, yakalama grupları, normal ifade deseninin parantez kullanılarak tanımlanır. Adlandırılmış gruplara ad alt ifade dili seçeneği tarafından ad veya sayı atanır `(?<` *name* `>` *subexpression* `)` , ancak adlandırılmamış gruplar dizin tarafından erişilebilir. <xref:System.Text.RegularExpressions.GroupCollection>Nesnede, adlandırılmamış gruplar adlandırılmış gruplardan önce gelmeli.

Gruplandırma yapıları genellikle yalnızca birden çok dil öğesine nicelik belirteçleri uygulamak için kullanılır ve yakalanan alt dizeler hiçbir ilgi değildir. Örneğin, aşağıdaki normal ifade varsa:

`\b\(?((\w+),?\s?)+[\.!?]\)?`

yalnızca bir nokta, ünlem işareti veya soru işaretiyle biten cümleleri bir belgeden ayıklamaya yöneliktir, yalnızca elde edilen cümle (nesne tarafından temsil edilir <xref:System.Text.RegularExpressions.Match> ) ilgilenir. Koleksiyondaki tek sözcükler değildir.

Normal ifade altyapısının hem hem de koleksiyon nesnelerini doldurması gerektiğinden, daha sonra kullanılmayan grupları yakalama maliyetli olabilir <xref:System.Text.RegularExpressions.GroupCollection> <xref:System.Text.RegularExpressions.CaptureCollection> . Alternatif olarak, <xref:System.Text.RegularExpressions.RegexOptions.ExplicitCapture?displayProperty=nameWithType> `n` yalnızca geçerli yakalamalar açıkça adlandırılmış veya alt `(?<` *name* `>` *ifade* yapısı tarafından atanan numaralandırılmış grupları belirtmek için seçeneğini veya satır içi seçeneğini kullanabilirsiniz `)` .

Aşağıdaki örnek, `\b\(?((\w+),?\s?)+[\.!?]\)?` <xref:System.Text.RegularExpressions.Regex.Match%2A> yöntemi ile ve seçeneği olmadan çağrıldığında, normal ifade deseninin döndürdüğü eşleşmeler hakkındaki bilgileri görüntüler <xref:System.Text.RegularExpressions.RegexOptions.ExplicitCapture?displayProperty=nameWithType> . İlk yöntem çağrısının çıktısı gösterdiği gibi, normal ifade altyapısı, <xref:System.Text.RegularExpressions.GroupCollection> ve <xref:System.Text.RegularExpressions.CaptureCollection> koleksiyon nesnelerini yakalanan alt dizeler hakkındaki bilgilerle tamamen doldurur. İkinci yöntem `options` olarak ayarlandığı ile çağrıldığı için <xref:System.Text.RegularExpressions.RegexOptions.ExplicitCapture?displayProperty=nameWithType> , gruplar üzerinde bilgi yakalamaz.

[!code-csharp[Conceptual.Regex.Language.Options#9](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.options/cs/explicit1.cs#9)]
[!code-vb[Conceptual.Regex.Language.Options#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.options/vb/explicit1.vb#9)]

Normal ifade deseninin, `\b\(?((?>\w+),?\s?)+[\.!?]\)?` Aşağıdaki tabloda gösterildiği gibi tanımlanmıştır.

|Desen|Description|
|-------------|-----------------|
|`\b`|Bir sözcük sınırında başlayın.|
|`\(?`|Açma parantezinin ("(") sıfır veya bir tekrarından birini eşleştirin.|
|`(?>\w+),?`|Bir veya daha fazla sözcük karakterini, ardından sıfır veya bir virgül ile eşleştirin. Sözcük karakterlerini eşleştirirken geri izlememeyin.|
|`\s?`|Sıfır veya bir beyaz boşluk karakterini eşleştirin.|
|`((\w+),?\s?)+`|Bir ya da daha fazla sözcük karakterinin, sıfır veya bir virgül, sıfır veya bir boşluk karakteri ile bir veya daha fazla kez birleşimini eşleştirin.|
|`[\.!?]\)?`|Üç noktalama sembolünden birini, ardından sıfır veya bir kapanış parantezleri (")") ile eşleştirin.|

Ayrıca, `(?n)` otomatik yakalamaları bastırmak için satır içi öğesini de kullanabilirsiniz. Aşağıdaki örnek, önceki normal ifade deseninin, `(?n)` seçeneği yerine satır içi öğeyi kullanmasını sağlar <xref:System.Text.RegularExpressions.RegexOptions.ExplicitCapture?displayProperty=nameWithType> .

[!code-csharp[Conceptual.Regex.Language.Options#10](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.options/cs/explicit2.cs#10)]
[!code-vb[Conceptual.Regex.Language.Options#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.options/vb/explicit2.vb#10)]

Son olarak, `(?n:)` bir grup grubuna göre otomatik yakalamaları bastırmak için satır içi grup öğesini kullanabilirsiniz. Aşağıdaki örnek, dış gruptaki adlandırılmamış yakalamaları bastırmak için önceki stili değiştirir `((?>\w+),?\s?)` . Bunun, iç gruptaki adlandırılmamış yakalamaları da bastırdığına unutmayın.

[!code-csharp[Conceptual.Regex.Language.Options#11](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.options/cs/explicit3.cs#11)]
[!code-vb[Conceptual.Regex.Language.Options#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.options/vb/explicit3.vb#11)]

## <a name="compiled-regular-expressions"></a>Derlenmiş normal Ifadeler

Varsayılan olarak, .NET 'teki normal ifadeler yorumlanır. Bir <xref:System.Text.RegularExpressions.Regex> nesne örneği oluşturulduğunda veya bir statik <xref:System.Text.RegularExpressions.Regex> Yöntem çağrıldığında, normal ifade deseninin özel bir işlem kodları kümesi olarak ayrıştırılıp bir yorumlayıcı, normal ifadeyi çalıştırmak için bu işlem kodları kullanır. Bu bir zorunluluğunu getirir içerir: normal ifade altyapısını başlatma maliyeti, çalışma zamanı performansının masrafına göre küçültülebilir.

Seçeneğini kullanarak yorumlanan normal ifadeler yerine derlenmiş ' i kullanabilirsiniz <xref:System.Text.RegularExpressions.RegexOptions.Compiled?displayProperty=nameWithType> . Bu durumda, bir model normal ifade altyapısına geçirildiğinde, bir dizi opkodlara ayrıştırılır ve ardından doğrudan ortak dil çalışma zamanına geçirilebilen Microsoft ara diline (MSIL) dönüştürülür. Derlenmiş normal ifadeler, başlatma zamanının masrafına göre çalışma zamanı performansını en üst düzeye çıkarır.

> [!NOTE]
> Normal bir ifade yalnızca <xref:System.Text.RegularExpressions.RegexOptions.Compiled?displayProperty=nameWithType> `options` bir <xref:System.Text.RegularExpressions.Regex> sınıf oluşturucusunun parametresine veya statik bir kalıp eşleme yöntemine değer sağlanarak derlenebilir. Satır içi seçeneği olarak kullanılamaz.

Statik ve örnek normal ifadelerine yapılan çağrılardan derlenmiş normal ifadeler kullanabilirsiniz. Statik normal ifadelerde, <xref:System.Text.RegularExpressions.RegexOptions.Compiled?displayProperty=nameWithType> seçeneği `options` normal ifade deseninin eşleme yönteminin parametresine geçirilir. Örnek normal ifadelerinde, `options` <xref:System.Text.RegularExpressions.Regex> sınıf oluşturucusunun parametresine geçirilir. Her iki durumda da gelişmiş performansa neden olur.

Ancak, bu performans geliştirmesi yalnızca aşağıdaki koşullarda oluşur:

- <xref:System.Text.RegularExpressions.Regex>Belirli bir normal ifadeyi temsil eden nesne, normal ifade desenli eşleştirme yöntemlerine yapılan birden çok çağrıda kullanılır.

- <xref:System.Text.RegularExpressions.Regex>Nesnenin kapsam dışına geçmesine izin verilmiyor, bu nedenle yeniden kullanılabilir.

- Statik bir normal ifade, normal ifade desenli eşleştirme yöntemlerine yapılan birden çok çağrıda kullanılır. (Statik yöntem çağrılarında kullanılan normal ifadeler normal ifade altyapısı tarafından önbelleğe alındığından, performans iyileştirmesi mümkündür.)

> [!NOTE]
> <xref:System.Text.RegularExpressions.RegexOptions.Compiled?displayProperty=nameWithType>Seçeneği, <xref:System.Text.RegularExpressions.Regex.CompileToAssembly%2A?displayProperty=nameWithType> önceden tanımlanmış derlenmiş normal ifadeler içeren bir özel amaçlı derleme oluşturan yöntemiyle ilişkili değildir.

## <a name="ignore-white-space"></a>Boşluğu yoksay

Varsayılan olarak, normal ifade düzeninde boşluk önemlidir; normal ifade altyapısını giriş dizesindeki bir boşluk karakteriyle eşleşecek şekilde zorlar. Bu nedenle, normal " `\b\w+\s` " ve " `\b\w+` " ifadesi kabaca eşdeğer normal ifadelerdir. Ayrıca, bir normal ifade düzeninde sayı işaretiyle (#) karşılaşıldığında, eşleştirilecek bir sabit karakter olarak yorumlanır.

<xref:System.Text.RegularExpressions.RegexOptions.IgnorePatternWhitespace?displayProperty=nameWithType>Seçeneği veya `x` satır içi seçeneği, bu varsayılan davranışı aşağıdaki gibi değiştirir:

- Normal ifade deseninin kaçışsız boşluk yok sayılır. Normal ifade deseninin bir parçası olmak için, boşluk karakterlerinin kaçış olması gerekir (örneğin, `\s` veya " `\` ").

- Numara işareti (#), bir açıklamanın başlangıcı olarak yorumlanır, örneğin bir sabit karakter yerine. # Karakterden dizenin sonuna kadar olan normal ifade deseninin tüm metni bir açıklama olarak yorumlanır.

Ancak, aşağıdaki durumlarda, seçeneğini kullansanız bile normal bir ifadede boşluk karakterleri yok sayılır <xref:System.Text.RegularExpressions.RegexOptions.IgnorePatternWhitespace?displayProperty=nameWithType> :

- Bir karakter sınıfı içindeki boşluk, her zaman tam olarak yorumlanır. Örneğin, normal ifade deseninin `[ .,;:]` her biri tek boşluk karakteri, nokta, virgül, noktalı virgül veya iki nokta üst üste eşleşir.

- Köşeli ayraç içinde `{` *n* `}` , `{` *n* `,}` ve `{` *n* `,` *e* `}` gibi bir nicelik süresi içinde boşluk bulunamaz. Örneğin, normal ifade deseninin bir boşluk `\d{1, 3}` karakteri içerdiği için, bir veya daha fazla basamaklı bir sayı dizisi ile üç basamağa eşleşmesi başarısız olur.

- Dil öğesi tanıtan bir karakter dizisi içinde boşluk kullanılamaz. Örneğin:

  - Language öğesi alt `(?:` *ifadesi* `)` yakalama olmayan bir grubu temsil eder ve `(?:` öğenin bölümünde gömülü boşluk bulunamaz. `(? :` *subexpression* `)` <xref:System.ArgumentException> Normal ifade altyapısı, stili ayrıştıramadığından ve alt ifadesi alt `( ?:` *subexpression* `)` *ifade*ile eşleşmediğinden, bu, bir çalışma zamanı oluşturur.

  - `\p{` *name* `}` Bir Unicode kategorisini veya adlandırılmış bloğu temsil eden dil öğesi adı, öğenin bölümüne gömülü boşluklar içeremez `\p{` . Bir boşluk eklerseniz, öğe bir <xref:System.ArgumentException> çalışma zamanı atar.

Bu seçeneğin etkinleştirilmesi, genellikle ayrıştırılması ve anlaşılması zor olan normal ifadelerin basitleştirilmesine yardımcı olur. Okunabilirliği artırır ve normal bir ifadeyi belgelemek mümkün kılar.

Aşağıdaki örnek, aşağıdaki normal ifade düzenlerini tanımlar:

`\b \(? ( (?>\w+) ,?\s? )+  [\.!?] \)? # Matches an entire sentence.`

Bu model, [yalnızca açık yakalamalar](#explicit-captures-only) bölümünde tanımlanan düzene benzer, ancak <xref:System.Text.RegularExpressions.RegexOptions.IgnorePatternWhitespace?displayProperty=nameWithType> model boşluk boşluğu yok sayma seçeneğini kullanır.

[!code-csharp[Conceptual.Regex.Language.Options#12](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.options/cs/whitespace1.cs#12)]
[!code-vb[Conceptual.Regex.Language.Options#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.options/vb/whitespace1.vb#12)]

Aşağıdaki örnek, `(?x)` kalıp boşluk alanını yoksaymak için satır içi seçeneğini kullanır.

[!code-csharp[Conceptual.Regex.Language.Options#13](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.options/cs/whitespace2.cs#13)]
[!code-vb[Conceptual.Regex.Language.Options#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.options/vb/whitespace2.vb#13)]

## <a name="right-to-left-mode"></a>Sağdan sola mod

Varsayılan olarak, normal ifade motoru soldan sağa doğru arar. Seçeneğini kullanarak arama yönünü ters çevirebilirsiniz <xref:System.Text.RegularExpressions.RegexOptions.RightToLeft?displayProperty=nameWithType> . Arama, dizenin son karakter konumunda otomatik olarak başlar. Bir başlangıç konumu parametresi içeren, örneğin <xref:System.Text.RegularExpressions.Regex.Match%28System.String%2CSystem.Int32%29?displayProperty=nameWithType> , başlangıç konumu, aramanın başlayacağı en sağdaki karakter konumunun dizinidir.

> [!NOTE]
> Sağdan sola düzendeki desenler yalnızca <xref:System.Text.RegularExpressions.RegexOptions.RightToLeft?displayProperty=nameWithType> `options` bir <xref:System.Text.RegularExpressions.Regex> sınıf oluşturucusunun veya statik kalıp eşleştirme yönteminin parametresine değer sağlanarak kullanılabilir. Satır içi seçeneği olarak kullanılamaz.

<xref:System.Text.RegularExpressions.RegexOptions.RightToLeft?displayProperty=nameWithType>Seçeneği yalnızca arama yönünü değiştirir; normal ifade modelini sağdan sola yorumlamaz. Örneğin, normal ifade `\bb\w+\s` "b" harfiyle başlayan ve ardından bir boşluk karakteri gelen sözcüklerle eşleşir. Aşağıdaki örnekte, giriş dizesi bir veya daha fazla "b" karakteri içeren üç sözcükten oluşur. İlk sözcük "b" ile başlar, ikincisi "b" ile biter ve üçüncüsü sözcüğün ortasında iki "b" karakteri içerir. Örnekteki Çıktının gösterdiği gibi, yalnızca ilk sözcük normal ifade düzeniyle eşleşir.

[!code-csharp[Conceptual.Regex.Language.Options#17](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.options/cs/righttoleft1.cs#17)]
[!code-vb[Conceptual.Regex.Language.Options#17](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.options/vb/righttoleft1.vb#17)]

Ayrıca, ileriye doğru onaylama (alt `(?=` *ifade* `)` dili öğesi) ve geriye doğru onaylama onay (alt `(?<=` *ifade* `)` dili öğesi) yönünün değişmediğini unutmayın. İleri yönlü onaylar doğru görünür; geriye doğru arama onayları sola bakar. Örneğin, normal ifade, `(?<=\d{1,2}\s)\w+,?\s\d{4}` bir ay adından önce gelen bir tarihi sınamak için geriye yönelik onaylama onayını kullanır. Normal ifade daha sonra month ve Year ile eşleşir. İleri ve geriye yönelik onaylar hakkında daha fazla bilgi için bkz. [gruplandırma yapıları](grouping-constructs-in-regular-expressions.md).

[!code-csharp[Conceptual.Regex.Language.Options#18](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.options/cs/righttoleft2.cs#18)]
[!code-vb[Conceptual.Regex.Language.Options#18](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.options/vb/righttoleft2.vb#18)]

Normal ifade deseninin, aşağıdaki tabloda gösterildiği gibi tanımlanmıştır.

|Desen|Description|
|-------------|-----------------|
|`(?<=\d{1,2}\s)`|Eşleşmenin başlangıcında bir veya iki ondalık basamak gelmeli ve ardından bir boşluk gelmelidir.|
|`\w+`|Bir veya daha fazla sözcük karakteri eşleştir.|
|`,?`|Sıfır veya bir virgül karakteri eşleştirin.|
|`\s`|Bir boşluk karakteri ile eşleştirin.|
|`\d{4}`|Dört ondalık basamağı eşleştirin.|

## <a name="ecmascript-matching-behavior"></a>ECMAScript eşleştirme davranışı

Varsayılan olarak, normal ifade altyapısı bir normal ifade örüntüsünün giriş metnine eşleştirilirken kurallı davranışı kullanır. Ancak, normal ifade altyapısından, seçeneğini belirterek ECMAScript eşleştirme davranışı kullanmasını söyleyebilirsiniz <xref:System.Text.RegularExpressions.RegexOptions.ECMAScript?displayProperty=nameWithType> .

> [!NOTE]
> ECMAScript uyumlu davranış yalnızca <xref:System.Text.RegularExpressions.RegexOptions.ECMAScript?displayProperty=nameWithType> `options` bir <xref:System.Text.RegularExpressions.Regex> sınıf oluşturucusunun veya statik kalıp eşleştirme yönteminin parametresine değeri sağlanarak kullanılabilir. Satır içi seçeneği olarak kullanılamaz.

<xref:System.Text.RegularExpressions.RegexOptions.ECMAScript?displayProperty=nameWithType>Seçeneği yalnızca <xref:System.Text.RegularExpressions.RegexOptions.IgnoreCase?displayProperty=nameWithType> ve <xref:System.Text.RegularExpressions.RegexOptions.Multiline?displayProperty=nameWithType> seçenekleriyle birleştirilebilir. Normal ifadede herhangi bir diğer seçeneğin kullanılması bir ile sonuçlanır <xref:System.ArgumentOutOfRangeException> .

ECMAScript ve kurallı normal ifadelerin davranışı üç alanda farklılık gösterir: karakter sınıfı sözdizimi, kendine başvuran yakalama grupları ve sekizlik ve geri başvuru yorumu.

- Karakter sınıfı sözdizimi. Geleneksel normal ifadeler Unicode desteklediği için ECMAScript, ECMAScript 'teki karakter sınıfları daha sınırlı sözdizimine sahiptir ve bazı karakter sınıfı dil öğeleri farklı anlamdadır. Örneğin, ECMAScript, Unicode kategorisi veya blok öğeleri ve gibi dil öğelerini desteklemez `\p` `\P` . Benzer şekilde, `\w` bir sözcük karakteriyle eşleşen öğe, `[a-zA-Z_0-9]` ECMAScript kullanılırken ve kurallı davranış kullanılırken karakter sınıfına eşdeğerdir `[\p{Ll}\p{Lu}\p{Lt}\p{Lo}\p{Nd}\p{Pc}\p{Lm}]` . Daha fazla bilgi için bkz. [karakter sınıfları](character-classes-in-regular-expressions.md).

  Aşağıdaki örnek kurallı ve ECMAScript desenli eşleştirme arasındaki farkı gösterir. Bir normal ifade tanımlar, ve `\b(\w+\s*)+` ardından boşluk karakterleri gelen kelimelerle eşleşir. Giriş, biri Latin karakter kümesini ve diğeri ise Kiril karakter kümesini kullanan iki dizeden oluşur. Çıktıda gösterildiği gibi, <xref:System.Text.RegularExpressions.Regex.IsMatch%28System.String%2CSystem.String%2CSystem.Text.RegularExpressions.RegexOptions%29?displayProperty=nameWithType> ECMAScript eşleştirmeyi kullanan yönteme yapılan çağrı, Kiril kelimeleri ile eşleşemez, ancak kurallı eşleştirme kullanan yöntem çağrısı bu sözcüklerle eşleşir.

  [!code-csharp[Conceptual.Regex.Language.Options#16](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.options/cs/ecmascript1.cs#16)]
  [!code-vb[Conceptual.Regex.Language.Options#16](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.options/vb/ecmascript1.vb#16)]

- Kendine başvuran yakalama grupları. Kendisi için geri başvuru içeren bir normal ifade yakalama sınıfı, her yakalama yinelemesi ile güncelleştirilmeleri gerekir. Aşağıdaki örnekte gösterildiği gibi, bu özellik, normal ifadenin `((a+)(\1) ?)+` ECMAScript kullanılırken "aa aaaa aaaaaa" giriş dizesiyle eşleşmesini sağlar, ancak kurallı eşleştirme kullanılırken değildir.

  [!code-csharp[Conceptual.Regex.Language.Options#21](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.options/cs/ecmascript2.cs#21)]
  [!code-vb[Conceptual.Regex.Language.Options#21](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.options/vb/ecmascript2.vb#21)]

  Normal ifade aşağıdaki tabloda gösterildiği gibi tanımlanmıştır.

  |Desen|Description|
  |-------------|-----------------|
  |(+)|"A" harfini bir veya daha fazla kez eşleştirin. Bu ikinci yakalama grubudur.|
  |(\ 1)|İlk yakalama grubu tarafından yakalanan alt dizeyle eşleştirin. Bu, üçüncü yakalama grubudur.|
  |?|Sıfır veya bir boşluk karakterini eşleştirin.|
  |((a +) (\ 1)?) +|Bir veya daha fazla "a" karakterinin örüntüsünün ardından ilk yakalama grubuyla eşleşen bir dize ve ardından sıfır veya bir boşluk karakteri bir veya daha fazla kez olacak şekilde eşleşen bir karakter. Bu ilk yakalama grubudur.|

- Sekizlik kaçış ve geri başvurular arasında belirsizlikleri çözümlemesi. Aşağıdaki tabloda, kurallı ve ECMAScript normal ifadelerine karşılık gelen sekizlik ve geribaşvuru yorumlamasının farkları özetlenmektedir.

  |Normal ifade|Kurallı davranış|ECMAScript davranışı|
  |------------------------|------------------------|-------------------------|
  |`\0`ardından 0 ile 2 sekizlik basamak|Sekizlik olarak yorumlayın. Örneğin, `\044` her zaman sekizlik bir değer olarak yorumlanır ve "$" anlamına gelir.|Aynı davranış.|
  |`\`ardından 1 ile 9 arasında bir basamak, ardından ek ondalık basamak yok,|Bir geri başvuru olarak yorumlayın. Örneğin, `\9` bir dokuzuncu yakalama grubu mevcut olmasa bile her zaman geri başvuru 9 anlamına gelir. Yakalama grubu yoksa, normal ifade ayrıştırıcısı bir oluşturur <xref:System.ArgumentException> .|Tek bir ondalık basamak yakalama grubu varsa, bu basamağa geri başvuru. Aksi takdirde, değeri değişmez değer olarak yorumlayın.|
  |`\`ardından, 1 ile 9 arasında bir rakam ve ardından ek ondalık basamaklar|Basamakları ondalık değer olarak yorumlayın. Bu yakalama grubu varsa, ifadeyi bir geri başvuru olarak yorumlayın.<br /><br /> Aksi takdirde, önde gelen sekizlik basamakları sekizlik 377 ' e kadar yorumlayın; diğer bir deyişle, yalnızca değerin düşük 8 bitini göz önünde bulundurun. Kalan basamakları değişmez değer olarak yorumlayın. Örneğin ifadesinde, `\3000` grup 300 yakalama varsa, geri başvuru 300 olarak yorumlayın; grup 300 yakalama yoksa, sekizlik 300 olarak, ardından 0 olarak yorumlayın.|Bir yakalamaya başvurabilen ondalık bir değere mümkün olduğunca çok basamak dönüştürerek bir geri başvuru olarak yorumlayın. Herhangi bir basamak dönüştürülemiyorsa, sekizlik basamağı 377 ' e kadar olan önde gelen sekizlik basamakları kullanarak sekizlik olarak yorumlayın; kalan basamakları değişmez değer olarak yorumlayın.|

## <a name="comparison-using-the-invariant-culture"></a>Sabit kültür kullanılarak karşılaştırma

Varsayılan olarak, normal ifade altyapısı büyük küçük harfe duyarsız karşılaştırmalar gerçekleştirdiğinde, eşdeğer büyük ve küçük harfli karakterleri anlamak için geçerli kültürün büyük/küçük harf kurallarını kullanır.

Ancak, özellikle Kullanıcı girişini parolalar, dosyalar veya URL 'Ler gibi sistem kaynaklarının adlarıyla karşılaştırırken, bu davranış bazı karşılaştırmalar türleri için istenmeyen bir durum değildir. Aşağıdaki örnek senaryo gibi gösterilmektedir. Kod, URL 'SI **FILE://** ile kullanıma hazır olan herhangi bir kaynağa erişimi engellemeye yöneliktir. Normal ifade, normal ifade kullanarak dizeyle büyük/küçük harfe duyarsız bir eşleştirme girişiminde bulunur `$FILE://` . Ancak, geçerli sistem kültürü tr-TR (Türkçe-Türkiye) olduğunda "I", "i" öğesinin büyük harfli eşdeğeri değildir. Sonuç olarak, yöntemine yapılan çağrı <xref:System.Text.RegularExpressions.Regex.IsMatch%2A?displayProperty=nameWithType> döner `false` ve dosyaya erişime izin verilir.

[!code-csharp[Conceptual.Regex.Language.Options#14](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.options/cs/culture1.cs#14)]
[!code-vb[Conceptual.Regex.Language.Options#14](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.options/vb/culture1.vb#14)]

> [!NOTE]
> Büyük/küçük harfe duyarlı ve sabit kültür kullanan dize karşılaştırmaları hakkında daha fazla bilgi için bkz. [dizeleri kullanmak Için En Iyi uygulamalar](best-practices-strings.md).

Geçerli kültürün büyük/küçük harf duyarsız karşılaştırmalarını kullanmak yerine, <xref:System.Text.RegularExpressions.RegexOptions.CultureInvariant?displayProperty=nameWithType> dildeki kültürel farklılıklarını yok sayma ve sabit kültürün kurallarını kullanma seçeneğini belirtebilirsiniz.

> [!NOTE]
> Sabit kültür kullanılarak karşılaştırma yalnızca <xref:System.Text.RegularExpressions.RegexOptions.CultureInvariant?displayProperty=nameWithType> `options` bir <xref:System.Text.RegularExpressions.Regex> sınıf oluşturucusunun veya statik kalıp eşleştirme yönteminin parametresine değeri sağlanarak kullanılabilir. Satır içi seçeneği olarak kullanılamaz.

Aşağıdaki örnek, bir önceki örnekle aynıdır, ancak statik <xref:System.Text.RegularExpressions.Regex.IsMatch%28System.String%2CSystem.String%2CSystem.Text.RegularExpressions.RegexOptions%29?displayProperty=nameWithType> Yöntem dahil olan seçeneklerle çağırılır <xref:System.Text.RegularExpressions.RegexOptions.CultureInvariant?displayProperty=nameWithType> . Geçerli kültür Türkçe (Türkiye) olarak ayarlandığında bile, normal ifade altyapısı "dosya" ve "dosya" ile başarılı bir şekilde eşleştirebilir ve dosya kaynağına erişimi engelleyebilir.

[!code-csharp[Conceptual.Regex.Language.Options#15](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.options/cs/culture1.cs#15)]
[!code-vb[Conceptual.Regex.Language.Options#15](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.options/vb/culture1.vb#15)]

## <a name="see-also"></a>Ayrıca bkz.

- [Normal İfade Dili - Hızlı Başvuru](regular-expression-language-quick-reference.md)
