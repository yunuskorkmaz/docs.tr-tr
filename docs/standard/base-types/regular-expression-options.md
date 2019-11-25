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
ms.openlocfilehash: a53d7517485d2a0b02b6f11928f478a7da3f9503
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/12/2019
ms.locfileid: "73972108"
---
# <a name="regular-expression-options"></a>Normal İfade Seçenekleri

Varsayılan olarak, bir giriş dizesinin normal ifade deseninin herhangi bir sabit karakter ile karşılaştırılması büyük/küçük harfe duyarlıdır, normal ifade deseninin boşluk değeri, değişmez boşluk karakterleri olarak yorumlanır ve grupları normal bir ifadede yakalanıyor örtük olarak ve açıkça adlandırılmaktadır. Normal ifade seçeneklerini belirterek, varsayılan normal ifade davranışının bu ve diğer birçok yönlerini değiştirebilirsiniz. Aşağıdaki tabloda listelenen bu seçenekler, normal ifade deseninin bir parçası olarak satır içi olarak dahil edilebilir veya bir <xref:System.Text.RegularExpressions.Regex?displayProperty=nameWithType> sınıf oluşturucusuna veya statik kalıp eşleştirme yöntemine <xref:System.Text.RegularExpressions.RegexOptions?displayProperty=nameWithType> numaralandırma değeri olarak sağlanabilir.

|RegexOptions üyesi|Satır içi karakter|Efekt|
|-------------------------|----------------------|------------|
|<xref:System.Text.RegularExpressions.RegexOptions.None>|Yok|Varsayılan davranışı kullanın. Daha fazla bilgi için bkz. [varsayılan seçenekler](#default-options).|
|<xref:System.Text.RegularExpressions.RegexOptions.IgnoreCase>|`i`|Büyük küçük harf duyarlı eşleme kullanın. Daha fazla bilgi için bkz. [büyük/küçük harfe duyarsız eşleşme](#case-insensitive-matching).|
|<xref:System.Text.RegularExpressions.RegexOptions.Multiline>|`m`|`^` ve `$` her satırın başlangıcını ve sonunu (giriş dizesinin başı ve sonu yerine) eşleştirmek için çok satırlı modunu kullanın. Daha fazla bilgi için bkz. [çok satırlı mod](#multiline-mode).|
|<xref:System.Text.RegularExpressions.RegexOptions.Singleline>|`s`|Nokta (.) her karakterle (`\n`hariç her karakter yerine) eşleştiğinde tek satırlık modu kullanın. Daha fazla bilgi için bkz. [tek satırlık mod](#single-line-mode).|
|<xref:System.Text.RegularExpressions.RegexOptions.ExplicitCapture>|`n`|Adsız grupları yakalamayın. Yalnızca geçerli yakalamalar, form `(?<`*adı*`>` alt *ifade*`)`açıkça adlandırılmış veya numaralandırılmış gruplarıdır. Daha fazla bilgi için [yalnızca açık yakalamalar](#explicit-captures-only)bölümüne bakın.|
|<xref:System.Text.RegularExpressions.RegexOptions.Compiled>|Yok|Normal ifadeyi bir derleme için derleyin. Daha fazla bilgi için bkz. [derlenmiş normal ifadeler](#compiled-regular-expressions).|
|<xref:System.Text.RegularExpressions.RegexOptions.IgnorePatternWhitespace>|`x`|Kaçışsız boşluğu düzeninden hariç tutun ve bir sayı işaretinden sonra açıklamaları etkinleştirin (`#`). Daha fazla bilgi için bkz. boşluğu [Yoksay](#ignore-white-space).|
|<xref:System.Text.RegularExpressions.RegexOptions.RightToLeft>|Yok|Arama yönünü değiştirin. Arama, soldan sağa yerine sağdan sola gider. Daha fazla bilgi için bkz. [sağdan sola mod](#right-to-left-mode).|
|<xref:System.Text.RegularExpressions.RegexOptions.ECMAScript>|Yok|İfade için ECMAScript uyumlu davranışı etkinleştirin. Daha fazla bilgi için bkz. [ECMAScript eşleştirme davranışı](#ecmascript-matching-behavior).|
|<xref:System.Text.RegularExpressions.RegexOptions.CultureInvariant>|Yok|Dildeki kültürel farklarını yoksayın. Daha fazla bilgi için bkz. [sabit kültür kullanılarak karşılaştırma](#comparison-using-the-invariant-culture).|

## <a name="specifying-the-options"></a>Seçenekleri belirtme

Normal ifadeler için seçenekleri üç şekilde belirtebilirsiniz:

- <xref:System.Text.RegularExpressions.Regex?displayProperty=nameWithType> sınıf oluşturucusunun `options` parametresinde veya <xref:System.Text.RegularExpressions.Regex.%23ctor%28System.String%2CSystem.Text.RegularExpressions.RegexOptions%29?displayProperty=nameWithType> veya <xref:System.Text.RegularExpressions.Regex.Match%28System.String%2CSystem.String%2CSystem.Text.RegularExpressions.RegexOptions%29?displayProperty=nameWithType>gibi bir statik (Visual Basic ' de`Shared`) desenler eşleme yöntemi. `options` parametresi, <xref:System.Text.RegularExpressions.RegexOptions?displayProperty=nameWithType> numaralandırılmış değerlerin bit seviyesinde veya birleşimidir.

  Bir sınıf oluşturucusunun `options` parametresi kullanılarak bir <xref:System.Text.RegularExpressions.Regex> örneğine seçenekler sağlandığında, Seçenekler <xref:System.Text.RegularExpressions.RegexOptions?displayProperty=nameWithType> özelliğine atanır. Ancak, <xref:System.Text.RegularExpressions.RegexOptions?displayProperty=nameWithType> özelliği normal ifade deseninin kendisinde satır içi seçenekleri yansıtmaz.

  Aşağıdaki örnek, bir gösterim sağlar. Büyük/küçük harfe duyarsız eşleştirmeyi etkinleştirmek ve "d" harfiyle başlayan sözcükleri tanımlarken kalıp uzayını yoksaymak için <xref:System.Text.RegularExpressions.Regex.Match%28System.String%2CSystem.String%2CSystem.Text.RegularExpressions.RegexOptions%29?displayProperty=nameWithType> yönteminin `options` parametresini kullanır.

  [!code-csharp[Conceptual.Regex.Language.Options#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.options/cs/example1.cs#6)]
  [!code-vb[Conceptual.Regex.Language.Options#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.options/vb/example1.vb#6)]

- Bir normal ifade deseninin satır içi seçeneklerini `(?imnsx-imnsx)`sözdizimiyle uygulayarak. Seçeneği, seçeneğinin düzenin sonuna kadar veya başka bir satır içi seçenek tarafından tanımsız olan nokta için geçerli olan nokta için geçerlidir. Bir <xref:System.Text.RegularExpressions.Regex> örneğinin <xref:System.Text.RegularExpressions.RegexOptions?displayProperty=nameWithType> özelliğinin bu satır içi seçenekleri yansıtmadığını unutmayın. Daha fazla bilgi için bkz. [çeşitli yapılar](../../../docs/standard/base-types/miscellaneous-constructs-in-regular-expressions.md) konusu.

  Aşağıdaki örnek, bir gösterim sağlar. Büyük/küçük harfe duyarsız eşleştirmeyi etkinleştirmek ve "d" harfiyle başlayan sözcükleri tanımlarken kalıp boşluk yoksaymak için satır içi seçenekleri kullanır.

  [!code-csharp[Conceptual.Regex.Language.Options#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.options/cs/example1.cs#7)]
  [!code-vb[Conceptual.Regex.Language.Options#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.options/vb/example1.vb#7)]

- Belirli bir gruplama yapısına satır içi seçenekler uygulayarak `(?imnsx-imnsx:`alt *ifade*`)`sözdizimi olan bir normal ifade düzeniyle. Bir seçenek kümesinden önce hiçbir işaret, kümeyi açmadan önce hiçbir işaret yoktur; bir seçenek kümesinden önceki bir eksi işareti, kümeyi devre dışı bırakır. (`?`, dil yapısının etkin veya devre dışı bırakılmış olması gereken sözdiziminin sabit bir parçasıdır.) Seçeneği yalnızca bu grup için geçerlidir. Daha fazla bilgi için bkz. [yapıları gruplandırma](../../../docs/standard/base-types/grouping-constructs-in-regular-expressions.md).

  Aşağıdaki örnek, bir gösterim sağlar. Büyük/küçük harfe duyarsız eşleştirmeyi etkinleştirmek ve "d" harfiyle başlayan sözcükleri tanımlarken kalıp boşluk yoksaymak için bir gruplama yapısında satır içi seçenekleri kullanır.

  [!code-csharp[Conceptual.Regex.Language.Options#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.options/cs/example1.cs#8)]
  [!code-vb[Conceptual.Regex.Language.Options#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.options/vb/example1.vb#8)]

Seçenekler satır içi belirtilirse, bir seçenek veya seçenek kümesinden önce bir eksi işareti (`-`) bu seçenekleri devre dışı bırakır. Örneğin, satır içi yapı `(?ix-ms)` <xref:System.Text.RegularExpressions.RegexOptions.IgnoreCase?displayProperty=nameWithType> ve <xref:System.Text.RegularExpressions.RegexOptions.IgnorePatternWhitespace?displayProperty=nameWithType> seçeneklerini etkinleştirir ve <xref:System.Text.RegularExpressions.RegexOptions.Multiline?displayProperty=nameWithType> ve <xref:System.Text.RegularExpressions.RegexOptions.Singleline?displayProperty=nameWithType> seçeneklerini kapatır. Tüm normal ifade seçenekleri varsayılan olarak kapalıdır.

> [!NOTE]
> Bir oluşturucunun veya yöntem çağrısının `options` parametresinde belirtilen normal ifade seçenekleri normal ifade düzeninde satır içi belirtilen seçeneklerle çakışırsa, satır içi seçenekler kullanılır.

Aşağıdaki beş normal ifade seçeneği, hem Options parametresiyle hem de satır içi olarak ayarlanabilir:

- <xref:System.Text.RegularExpressions.RegexOptions.IgnoreCase?displayProperty=nameWithType>

- <xref:System.Text.RegularExpressions.RegexOptions.Multiline?displayProperty=nameWithType>

- <xref:System.Text.RegularExpressions.RegexOptions.Singleline?displayProperty=nameWithType>

- <xref:System.Text.RegularExpressions.RegexOptions.ExplicitCapture?displayProperty=nameWithType>

- <xref:System.Text.RegularExpressions.RegexOptions.IgnorePatternWhitespace?displayProperty=nameWithType>

Aşağıdaki beş normal ifade seçeneği `options` parametresi kullanılarak ayarlanabilir, ancak satır içi ayarlanamaz:

- <xref:System.Text.RegularExpressions.RegexOptions.None?displayProperty=nameWithType>

- <xref:System.Text.RegularExpressions.RegexOptions.Compiled?displayProperty=nameWithType>

- <xref:System.Text.RegularExpressions.RegexOptions.RightToLeft?displayProperty=nameWithType>

- <xref:System.Text.RegularExpressions.RegexOptions.CultureInvariant?displayProperty=nameWithType>

- <xref:System.Text.RegularExpressions.RegexOptions.ECMAScript?displayProperty=nameWithType>

## <a name="determining-the-options"></a>Seçenekleri belirleme

Salt okunurdur <xref:System.Text.RegularExpressions.Regex.Options%2A?displayProperty=nameWithType> özelliğinin değerini alarak, örneği oluşturulduğunda <xref:System.Text.RegularExpressions.Regex> nesnesine hangi seçeneklerin sağlandığını belirleyebilirsiniz. Bu özellik, <xref:System.Text.RegularExpressions.Regex.CompileToAssembly%2A?displayProperty=nameWithType> yöntemi tarafından oluşturulan derlenmiş bir normal ifade için tanımlanan seçenekleri belirlemek için özellikle yararlıdır.

<xref:System.Text.RegularExpressions.RegexOptions.None?displayProperty=nameWithType>dışında herhangi bir seçeneğin varlığını test etmek için, <xref:System.Text.RegularExpressions.Regex.Options%2A?displayProperty=nameWithType> özelliğinin değeri ve ilgilendiğiniz <xref:System.Text.RegularExpressions.RegexOptions> değeri ile bir ve işlemi gerçekleştirin. Sonra sonucun bu <xref:System.Text.RegularExpressions.RegexOptions> değere eşit olup olmadığını test edin. Aşağıdaki örnek <xref:System.Text.RegularExpressions.RegexOptions.IgnoreCase?displayProperty=nameWithType> seçeneğinin ayarlanmış olup olmadığını sınar.

[!code-csharp[Conceptual.Regex.Language.Options#19](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.options/cs/determine1.cs#19)]
[!code-vb[Conceptual.Regex.Language.Options#19](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.options/vb/determine1.vb#19)]

<xref:System.Text.RegularExpressions.RegexOptions.None?displayProperty=nameWithType>test etmek için, aşağıdaki örnekte gösterildiği gibi, <xref:System.Text.RegularExpressions.Regex.Options%2A?displayProperty=nameWithType> özelliğinin değerinin <xref:System.Text.RegularExpressions.RegexOptions.None?displayProperty=nameWithType>'e eşit olup olmadığını saptayın.

[!code-csharp[Conceptual.Regex.Language.Options#20](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.options/cs/determine1.cs#20)]
[!code-vb[Conceptual.Regex.Language.Options#20](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.options/vb/determine1.vb#20)]

Aşağıdaki bölümlerde, .NET içindeki normal ifade tarafından desteklenen seçenekler listelenmektedir.

## <a name="default-options"></a>Varsayılan Seçenekler

<xref:System.Text.RegularExpressions.RegexOptions.None?displayProperty=nameWithType> seçeneği, hiçbir seçenek belirtilmediğini ve normal ifade altyapısının varsayılan davranışını kullandığını gösterir. Bu, aşağıdakileri içerir:

- Desenler, ECMAScript normal ifadesi yerine kurallı olarak yorumlanır.

- Normal ifade deseninin giriş dizesinde soldan sağa eşleşmesi vardır.

- Karşılaştırmalar büyük/küçük harfe duyarlıdır.

- `^` ve `$` dil öğeleri, giriş dizesinin başlangıcı ve sonu ile eşleşir.

- `.` Language öğesi `\n`hariç her karakterle eşleşir.

- Normal ifade düzenindeki herhangi bir boşluk, sabit bir boşluk karakteri olarak yorumlanır.

- Geçerli kültürün kuralları, model giriş dizesiyle karşılaştırılırken kullanılır.

- Normal ifade düzeninde yakalama grupları örtük ve açık olarak açıktır.

> [!NOTE]
> <xref:System.Text.RegularExpressions.RegexOptions.None?displayProperty=nameWithType> seçeneğinin satır içi eşdeğeri yoktur. Normal ifade seçenekleri satır içi uygulandığında, özel bir seçenek devre dışı bırakarak varsayılan davranış bir seçenek temelinde geri yüklenir. Örneğin `(?i)`, büyük/küçük harfe duyarsız karşılaştırmayı etkinleştirir ve `(?-i)`, varsayılan büyük/küçük harfe duyarlı karşılaştırmayı geri yükler.

<xref:System.Text.RegularExpressions.RegexOptions.None?displayProperty=nameWithType> seçeneği, normal ifade altyapısının varsayılan davranışını temsil ettiğinden, yöntem çağrısında nadiren açıkça belirtilir. Bunun yerine `options` parametresi olmayan bir Oluşturucu veya statik kalıp eşleştirme yöntemi çağırılır.

## <a name="case-insensitive-matching"></a>Büyük/küçük harfe duyarsız eşleşme

<xref:System.Text.RegularExpressions.RegexOptions.IgnoreCase> seçeneği veya `i` satır içi seçeneği, büyük/küçük harfe duyarsız eşleşme sağlar. Varsayılan olarak, geçerli kültürün büyük/küçük harf kuralları kullanılır.

Aşağıdaki örnek, "The" ile başlayan tüm sözcüklerle eşleşen `\bthe\w*\b`normal ifade modelini tanımlar. <xref:System.Text.RegularExpressions.Regex.Match%2A> yöntemine yapılan ilk çağrı, varsayılan büyük/küçük harfe duyarlı karşılaştırmayı kullandığından, çıkış, tümceyi Başlatan "The" dizesinin eşleştirilmediğini belirtir. <xref:System.Text.RegularExpressions.Regex.Match%2A> yöntemi <xref:System.Text.RegularExpressions.RegexOptions.IgnoreCase>olarak ayarlanan seçeneklerle çağrıldığında eşleşir.

[!code-csharp[Conceptual.Regex.Language.Options#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.options/cs/case1.cs#1)]
[!code-vb[Conceptual.Regex.Language.Options#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.options/vb/case1.vb#1)]

Aşağıdaki örnek, büyük/küçük harfe duyarsız karşılaştırma sağlamak için `options` parametresi yerine satır içi seçenekleri kullanmak için önceki örnekteki normal ifade deseninin konumunu değiştirir. İlk model, yalnızca "The" dizesinde "t" harfine uygulanan bir gruplama yapısında büyük/küçük harf duyarsız seçeneğini tanımlar. Seçenek yapısı deseninin başlangıcında gerçekleştiğinden, ikinci model büyük/küçük harf duyarsız seçeneğini normal ifadeye uygular.

[!code-csharp[Conceptual.Regex.Language.Options#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.options/cs/case2.cs#2)]
[!code-vb[Conceptual.Regex.Language.Options#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.options/vb/case2.vb#2)]

## <a name="multiline-mode"></a>Çok satırlı mod

<xref:System.Text.RegularExpressions.RegexOptions.Multiline?displayProperty=nameWithType> seçeneği veya `m` inline seçeneği, normal ifade altyapısının birden çok satırdan oluşan bir giriş dizesini işlemesini sağlar. `^` ve `$` dil öğelerinin yorumlanmasını, giriş dizesinin başı ve sonu yerine bir satırın başlangıcını ve sonuna uyacak şekilde değiştirir.

Varsayılan olarak, `$` yalnızca giriş dizesinin sonu ile eşleşir. <xref:System.Text.RegularExpressions.RegexOptions.Multiline?displayProperty=nameWithType> seçeneğini belirtirseniz, yeni satır karakteriyle (`\n`) veya giriş dizesinin sonuyla eşleşir. Ancak, satır başı/satır besleme karakteri bileşimiyle eşleşmez. Bunları başarıyla eşleştirmek için, yalnızca `$`yerine `\r?$` alt ifadeyi kullanın.

Aşağıdaki örnek Bowler adlarını ve puanlarını ayıklar ve bunları azalan sırada sıralayan bir <xref:System.Collections.Generic.SortedList%602> koleksiyonuna ekler. <xref:System.Text.RegularExpressions.Regex.Matches%2A> yöntemi iki kez çağrılır. İlk yöntem çağrısında, normal ifade `^(\w+)\s(\d+)$` ve hiçbir seçenek ayarlanmadı. Çıktının gösterdiği gibi, normal ifade altyapısı giriş deseninin yanı sıra giriş dizesinin başlangıcı ve sonuyla eşleşeceğinden, hiçbir eşleşme bulunamamıştır. İkinci yöntem çağrısında, normal ifade `^(\w+)\s(\d+)\r?$` olarak değiştirilir ve seçenekler <xref:System.Text.RegularExpressions.RegexOptions.Multiline?displayProperty=nameWithType>olarak ayarlanır. Çıktıda gösterildiği gibi, adlar ve puanlar başarıyla eşleştirilir ve puanlar azalan sırada görüntülenir.

[!code-csharp[Conceptual.Regex.Language.Options#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.options/cs/multiline1.cs#3)]
[!code-vb[Conceptual.Regex.Language.Options#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.options/vb/multiline1.vb#3)]

`^(\w+)\s(\d+)\r*$` normal ifade deseninin aşağıdaki tabloda gösterildiği gibi tanımlanmıştır.

|Desen|Açıklama|
|-------------|-----------------|
|`^`|Satırın başlangıcında başlayın.|
|`(\w+)`|Bir veya daha fazla sözcük karakteri eşleştir. Bu ilk yakalama grubudur.|
|`\s`|Bir boşluk karakteri ile eşleştirin.|
|`(\d+)`|Bir veya daha fazla ondalık basamağı eşleştirin. Bu ikinci yakalama grubudur.|
|`\r?`|Sıfır veya bir satır başı karakteri eşleştirin.|
|`$`|Satırın sonunda biter.|

Aşağıdaki örnek, tek satırlı seçeneğini ayarlamak için `(?m)` satır içi seçeneğini kullanması dışında, öncekiyle eşdeğerdir.

[!code-csharp[Conceptual.Regex.Language.Options#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.options/cs/multiline2.cs#4)]
[!code-vb[Conceptual.Regex.Language.Options#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.options/vb/multiline2.vb#4)]

## <a name="single-line-mode"></a>Tek satırlık mod

<xref:System.Text.RegularExpressions.RegexOptions.Singleline?displayProperty=nameWithType> seçeneği veya `s` inline seçeneği, normal ifade altyapısının giriş dizesini tek bir satırdan oluşan gibi işleme almasına neden olur. Bu, nokta (`.`) dil öğesinin davranışını, yeni satır karakteri için `\n` veya \U000ahariç her karakterle eşleştirmek yerine her karakterle eşleşecek şekilde değiştirerek yapar.

Aşağıdaki örnek, <xref:System.Text.RegularExpressions.RegexOptions.Singleline?displayProperty=nameWithType> seçeneğini kullandığınızda `.` Language öğesinin davranışının nasıl değiştiği gösterilmektedir. Normal ifade `^.+` dizenin başlangıcında başlar ve her karakterle eşleşir. Varsayılan olarak eşleştirme, ilk satırın sonunda biter; normal ifade deseninin satır dönüş karakteriyle `\r` veya \u000D ile eşleşmesi, ancak `\n`eşleşmez. <xref:System.Text.RegularExpressions.RegexOptions.Singleline?displayProperty=nameWithType> seçeneği giriş dizesinin tamamını tek bir satır olarak yorumladığından, `\n`dahil olmak üzere giriş dizesindeki her karakterle eşleşir.

[!code-csharp[Conceptual.Regex.Language.CharacterClasses#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.characterclasses/cs/any2.cs#5)]
[!code-vb[Conceptual.Regex.Language.CharacterClasses#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.characterclasses/vb/any2.vb#5)]

Aşağıdaki örnek, tek satır modunu etkinleştirmek için `(?s)` satır içi seçeneğini kullanması dışında, önceki bir ile eşdeğerdir.

[!code-csharp[Conceptual.Regex.Language.Options#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.options/cs/singleline1.cs#5)]
[!code-vb[Conceptual.Regex.Language.Options#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.options/vb/singleline1.vb#5)]

## <a name="explicit-captures-only"></a>Yalnızca açık yakalamalar

Varsayılan olarak, yakalama grupları, normal ifade deseninin parantez kullanılarak tanımlanır. Adlandırılmış gruplara `(?<`*ad*`>`alt *ifade*`)` dil seçeneği tarafından bir ad veya sayı atanır, ancak adlandırılmamış gruplara dizin tarafından erişilebilir. <xref:System.Text.RegularExpressions.GroupCollection> nesnesinde, adlandırılmamış gruplar adlandırılmış gruplardan önce gelmeli.

Gruplandırma yapıları genellikle yalnızca birden çok dil öğesine nicelik belirteçleri uygulamak için kullanılır ve yakalanan alt dizeler hiçbir ilgi değildir. Örneğin, aşağıdaki normal ifade varsa:

`\b\(?((\w+),?\s?)+[\.!?]\)?`

yalnızca bir nokta, ünlem işareti veya soru işaretiyle biten cümleleri bir belgeden ayıklamak için tasarlanmıştır; yalnızca elde edilen cümle (<xref:System.Text.RegularExpressions.Match> nesnesi tarafından temsil edilir) ilgilenir. Koleksiyondaki tek sözcükler değildir.

Normal ifade altyapısının hem <xref:System.Text.RegularExpressions.GroupCollection> hem de <xref:System.Text.RegularExpressions.CaptureCollection> koleksiyon nesnelerini doldurması gerektiğinden, daha sonra kullanılmayan grupları yakalama pahalı olabilir. Alternatif olarak, yalnızca geçerli yakalamalar açıkça adlandırılmış veya `(?<`*adı*`>` alt *ifade*`)` yapısı tarafından atanan numaralandırılmış grupları belirtmek için <xref:System.Text.RegularExpressions.RegexOptions.ExplicitCapture?displayProperty=nameWithType> seçeneğini veya `n` satır içi seçeneğini kullanabilirsiniz.

Aşağıdaki örnek, <xref:System.Text.RegularExpressions.Regex.Match%2A> yöntemi <xref:System.Text.RegularExpressions.RegexOptions.ExplicitCapture?displayProperty=nameWithType> seçeneği olmadan ve ile çağrıldığında `\b\(?((\w+),?\s?)+[\.!?]\)?` normal ifade deseninin döndürdüğü eşleşmeler hakkındaki bilgileri görüntüler. İlk yöntem çağrısının çıktısı gösterdiği gibi, normal ifade altyapısı <xref:System.Text.RegularExpressions.GroupCollection> ve <xref:System.Text.RegularExpressions.CaptureCollection> koleksiyon nesnelerini yakalanan alt dizeler hakkında bilgilerle tamamen doldurur. İkinci yöntem `options` <xref:System.Text.RegularExpressions.RegexOptions.ExplicitCapture?displayProperty=nameWithType>olarak ayarlandığı için, gruplar hakkındaki bilgileri yakalamaz.

[!code-csharp[Conceptual.Regex.Language.Options#9](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.options/cs/explicit1.cs#9)]
[!code-vb[Conceptual.Regex.Language.Options#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.options/vb/explicit1.vb#9)]

`\b\(?((?>\w+),?\s?)+[\.!?]\)?` normal ifade deseninin aşağıdaki tabloda gösterildiği gibi tanımlanmıştır.

|Desen|Açıklama|
|-------------|-----------------|
|`\b`|Bir sözcük sınırında başlayın.|
|`\(?`|Açma parantezinin ("(") sıfır veya bir tekrarından birini eşleştirin.|
|`(?>\w+),?`|Bir veya daha fazla sözcük karakterini, ardından sıfır veya bir virgül ile eşleştirin. Sözcük karakterlerini eşleştirirken geri izlememeyin.|
|`\s?`|Sıfır veya bir beyaz boşluk karakterini eşleştirin.|
|`((\w+),?\s?)+`|Bir ya da daha fazla sözcük karakterinin, sıfır veya bir virgül, sıfır veya bir boşluk karakteri ile bir veya daha fazla kez birleşimini eşleştirin.|
|`[\.!?]\)?`|Üç noktalama sembolünden birini, ardından sıfır veya bir kapanış parantezleri (")") ile eşleştirin.|

Otomatik yakalamaları bastırmak için `(?n)` inline öğesini de kullanabilirsiniz. Aşağıdaki örnek, önceki normal ifade deseninin <xref:System.Text.RegularExpressions.RegexOptions.ExplicitCapture?displayProperty=nameWithType> seçeneği yerine `(?n)` inline öğesini kullanmasını sağlar.

[!code-csharp[Conceptual.Regex.Language.Options#10](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.options/cs/explicit2.cs#10)]
[!code-vb[Conceptual.Regex.Language.Options#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.options/vb/explicit2.vb#10)]

Son olarak, Grup grubuna göre otomatik yakalamaları bastırmak için `(?n:)` satır içi grup öğesini kullanabilirsiniz. Aşağıdaki örnek, `((?>\w+),?\s?)`dış gruptaki adlandırılmamış yakalamaları bastırmak için önceki stili değiştirir. Bunun, iç gruptaki adlandırılmamış yakalamaları da bastırdığına unutmayın.

[!code-csharp[Conceptual.Regex.Language.Options#11](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.options/cs/explicit3.cs#11)]
[!code-vb[Conceptual.Regex.Language.Options#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.options/vb/explicit3.vb#11)]

## <a name="compiled-regular-expressions"></a>Derlenmiş normal Ifadeler

Varsayılan olarak, .NET 'teki normal ifadeler yorumlanır. Bir <xref:System.Text.RegularExpressions.Regex> nesnesi örneği oluşturulduğunda veya statik bir <xref:System.Text.RegularExpressions.Regex> yöntemi çağrıldığında, normal ifade deseninin bir dizi özel işlem kodları olarak ayrıştırılıp bir yorumlayıcı, normal ifadeyi çalıştırmak için bu işlem kodları kullanır. Bu bir zorunluluğunu getirir içerir: normal ifade altyapısını başlatma maliyeti, çalışma zamanı performansının masrafına göre küçültülebilir.

<xref:System.Text.RegularExpressions.RegexOptions.Compiled?displayProperty=nameWithType> seçeneğini kullanarak yorumlanan normal ifadeler yerine derlenmiş ' i kullanabilirsiniz. Bu durumda, bir model normal ifade altyapısına geçirildiğinde, bir dizi opkodlara ayrıştırılır ve ardından doğrudan ortak dil çalışma zamanına geçirilebilen Microsoft ara diline (MSIL) dönüştürülür. Derlenmiş normal ifadeler, başlatma zamanının masrafına göre çalışma zamanı performansını en üst düzeye çıkarır.

> [!NOTE]
> Normal bir ifade, yalnızca bir <xref:System.Text.RegularExpressions.Regex> sınıf oluşturucusunun `options` parametresine veya statik bir kalıp eşleme yöntemine <xref:System.Text.RegularExpressions.RegexOptions.Compiled?displayProperty=nameWithType> değeri sağlanarak derlenebilir. Satır içi seçeneği olarak kullanılamaz.

Statik ve örnek normal ifadelerine yapılan çağrılardan derlenmiş normal ifadeler kullanabilirsiniz. Statik normal ifadelerde <xref:System.Text.RegularExpressions.RegexOptions.Compiled?displayProperty=nameWithType> seçeneği, normal ifade deseninin eşleme yönteminin `options` parametresine geçirilir. Örnek normal ifadelerde, <xref:System.Text.RegularExpressions.Regex> sınıf oluşturucusunun `options` parametresine geçirilir. Her iki durumda da gelişmiş performansa neden olur.

Ancak, bu performans geliştirmesi yalnızca aşağıdaki koşullarda oluşur:

- Belirli bir normal ifadeyi temsil eden <xref:System.Text.RegularExpressions.Regex> nesnesi, normal ifade desenli eşleştirme yöntemlerine yapılan birden çok çağrıda kullanılır.

- <xref:System.Text.RegularExpressions.Regex> nesnenin kapsam dışına geçmesine izin verilmiyor, bu nedenle yeniden kullanılabilir.

- Statik bir normal ifade, normal ifade desenli eşleştirme yöntemlerine yapılan birden çok çağrıda kullanılır. (Statik yöntem çağrılarında kullanılan normal ifadeler normal ifade altyapısı tarafından önbelleğe alındığından, performans iyileştirmesi mümkündür.)

> [!NOTE]
> <xref:System.Text.RegularExpressions.RegexOptions.Compiled?displayProperty=nameWithType> seçeneği, önceden tanımlanmış derlenmiş normal ifadeler içeren bir özel amaçlı derleme oluşturan <xref:System.Text.RegularExpressions.Regex.CompileToAssembly%2A?displayProperty=nameWithType> yöntemiyle ilgisiz değildir.

## <a name="ignore-white-space"></a>Boşluğu yoksay

Varsayılan olarak, normal ifade düzeninde boşluk önemlidir; normal ifade altyapısını giriş dizesindeki bir boşluk karakteriyle eşleşecek şekilde zorlar. Bu nedenle, normal "`\b\w+\s`" ve "`\b\w+`" ifadesi kabaca eşdeğer normal ifadelerdir. Ayrıca, bir normal ifade düzeninde sayı işaretiyle (#) karşılaşıldığında, eşleştirilecek bir sabit karakter olarak yorumlanır.

<xref:System.Text.RegularExpressions.RegexOptions.IgnorePatternWhitespace?displayProperty=nameWithType> seçeneği veya `x` satır içi seçeneği, bu varsayılan davranışı aşağıdaki gibi değiştirir:

- Normal ifade deseninin kaçışsız boşluk yok sayılır. Normal ifade deseninin bir parçası olmak için, boşluk karakterlerinin kaçış olması gerekir (örneğin, `\s` veya "`\`" olarak).

- Numara işareti (#), bir açıklamanın başlangıcı olarak yorumlanır, örneğin bir sabit karakter yerine. # Karakterden dizenin sonuna kadar olan normal ifade deseninin tüm metni bir açıklama olarak yorumlanır.

Ancak, aşağıdaki durumlarda, <xref:System.Text.RegularExpressions.RegexOptions.IgnorePatternWhitespace?displayProperty=nameWithType> seçeneğini kullansanız bile normal ifadede boşluk karakterleri yok sayılır:

- Bir karakter sınıfı içindeki boşluk, her zaman tam olarak yorumlanır. Örneğin, normal ifade deseninin `[ .,;:]`, tek boşluk karakteri, nokta, virgül, noktalı virgül veya iki nokta üst üste eşleşir.

- `{`*n*`}`, `{`*n*`,}`ve `{`*n*`,`*d*`}`gibi, parantez içine alınmış nicelik, boşluk kullanımına izin verilmez. Örneğin, normal ifade deseninin `\d{1, 3}`, bir boşluk karakteri içerdiği için, bir veya üç basamaklı herhangi bir rakam dizisini eşleşemez.

- Dil öğesi tanıtan bir karakter dizisi içinde boşluk kullanılamaz. Örneğin:

  - Dil öğesi `(?:`alt *ifade*`)` yakalama olmayan bir grubu temsil eder ve öğenin `(?:` bölümünde gömülü boşluk bulunamaz. Normal ifade altyapısı, stili ayrıştıramadığından *ve `( ?:`alt ifadesi`)`* alt *ifade*ile eşleşmediği için,`)` `(? :`alt *ifade* , çalışma zamanında bir <xref:System.ArgumentException> oluşturur.

  - Bir Unicode kategorisini veya adlandırılmış bloğu temsil eden `\p{`*adı*`}`dil öğesi, öğenin `\p{` bölümünde gömülü boşluk içeremez. Boşluk eklerseniz, öğe çalışma zamanında bir <xref:System.ArgumentException> oluşturur.

Bu seçeneğin etkinleştirilmesi, genellikle ayrıştırılması ve anlaşılması zor olan normal ifadelerin basitleştirilmesine yardımcı olur. Okunabilirliği artırır ve normal bir ifadeyi belgelemek mümkün kılar.

Aşağıdaki örnek, aşağıdaki normal ifade düzenlerini tanımlar:

`\b \(? ( (?>\w+) ,?\s? )+  [\.!?] \)? # Matches an entire sentence.`

Bu model, [yalnızca açık yakalamalar](#explicit-captures-only) bölümünde tanımlanan düzene benzer, ancak model boşluk boşluğu yoksaymak için <xref:System.Text.RegularExpressions.RegexOptions.IgnorePatternWhitespace?displayProperty=nameWithType> seçeneğini kullanır.

[!code-csharp[Conceptual.Regex.Language.Options#12](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.options/cs/whitespace1.cs#12)]
[!code-vb[Conceptual.Regex.Language.Options#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.options/vb/whitespace1.vb#12)]

Aşağıdaki örnek, `(?x)` deseninin boşluk olduğunu yoksaymak için satır içi seçeneğini kullanır.

[!code-csharp[Conceptual.Regex.Language.Options#13](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.options/cs/whitespace2.cs#13)]
[!code-vb[Conceptual.Regex.Language.Options#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.options/vb/whitespace2.vb#13)]

## <a name="right-to-left-mode"></a>Sağdan sola mod

Varsayılan olarak, normal ifade motoru soldan sağa doğru arar. <xref:System.Text.RegularExpressions.RegexOptions.RightToLeft?displayProperty=nameWithType> seçeneğini kullanarak arama yönünü ters çevirebilirsiniz. Arama, dizenin son karakter konumunda otomatik olarak başlar. <xref:System.Text.RegularExpressions.Regex.Match%28System.String%2CSystem.Int32%29?displayProperty=nameWithType>gibi bir başlangıç konumu parametresi içeren desenli eşleşen yöntemler için başlangıç konumu, aramanın başlayacağı en sağdaki karakter konumunun dizinidir.

> [!NOTE]
> Sağdan sola desenler modu, yalnızca bir <xref:System.Text.RegularExpressions.Regex> sınıf oluşturucusunun veya statik kalıp eşleştirme yönteminin `options` parametresine <xref:System.Text.RegularExpressions.RegexOptions.RightToLeft?displayProperty=nameWithType> değeri sağlanarak kullanılabilir. Satır içi seçeneği olarak kullanılamaz.

<xref:System.Text.RegularExpressions.RegexOptions.RightToLeft?displayProperty=nameWithType> seçeneği yalnızca arama yönünü değiştirir; normal ifade modelini sağdan sola yorumlamaz. Örneğin, normal ifade `\bb\w+\s` "b" harfiyle başlayan ve ardından bir boşluk karakteri gelen sözcüklerle eşleşir. Aşağıdaki örnekte, giriş dizesi bir veya daha fazla "b" karakteri içeren üç sözcükten oluşur. İlk sözcük "b" ile başlar, ikincisi "b" ile biter ve üçüncüsü sözcüğün ortasında iki "b" karakteri içerir. Örnekteki Çıktının gösterdiği gibi, yalnızca ilk sözcük normal ifade düzeniyle eşleşir.

[!code-csharp[Conceptual.Regex.Language.Options#17](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.options/cs/righttoleft1.cs#17)]
[!code-vb[Conceptual.Regex.Language.Options#17](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.options/vb/righttoleft1.vb#17)]

Ayrıca, ileriye doğru onaylama (`(?=`alt *ifade*`)` Language öğesi) ve geriye doğru onaylama onayı (`(?<=`alt *ifade*`)` Language öğesi), yönü değiştirmediğini unutmayın. İleri yönlü onaylar doğru görünür; geriye doğru arama onayları sola bakar. Örneğin, normal ifade `(?<=\d{1,2}\s)\w+,?\s\d{4}`, bir ay adından önce gelen bir tarihi sınamak için geriye yönelik onay onayını kullanır. Normal ifade daha sonra month ve Year ile eşleşir. İleri ve geriye yönelik onaylar hakkında daha fazla bilgi için bkz. [gruplandırma yapıları](../../../docs/standard/base-types/grouping-constructs-in-regular-expressions.md).

[!code-csharp[Conceptual.Regex.Language.Options#18](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.options/cs/righttoleft2.cs#18)]
[!code-vb[Conceptual.Regex.Language.Options#18](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.options/vb/righttoleft2.vb#18)]

Normal ifade deseninin, aşağıdaki tabloda gösterildiği gibi tanımlanmıştır.

|Desen|Açıklama|
|-------------|-----------------|
|`(?<=\d{1,2}\s)`|Eşleşmenin başlangıcında bir veya iki ondalık basamak gelmeli ve ardından bir boşluk gelmelidir.|
|`\w+`|Bir veya daha fazla sözcük karakteri eşleştir.|
|`,?`|Sıfır veya bir virgül karakteri eşleştirin.|
|`\s`|Bir boşluk karakteri ile eşleştirin.|
|`\d{4}`|Dört ondalık basamağı eşleştirin.|

## <a name="ecmascript-matching-behavior"></a>ECMAScript eşleştirme davranışı

Varsayılan olarak, normal ifade altyapısı bir normal ifade örüntüsünün giriş metnine eşleştirilirken kurallı davranışı kullanır. Ancak, normal ifade altyapısından <xref:System.Text.RegularExpressions.RegexOptions.ECMAScript?displayProperty=nameWithType> seçeneğini belirterek ECMAScript eşleştirme davranışı kullanmasını söyleyebilirsiniz.

> [!NOTE]
> ECMAScript uyumlu davranış yalnızca bir <xref:System.Text.RegularExpressions.Regex> sınıf oluşturucusunun veya statik kalıp eşleştirme yönteminin `options` parametresine <xref:System.Text.RegularExpressions.RegexOptions.ECMAScript?displayProperty=nameWithType> değeri sağlanarak kullanılabilir. Satır içi seçeneği olarak kullanılamaz.

<xref:System.Text.RegularExpressions.RegexOptions.ECMAScript?displayProperty=nameWithType> seçeneği yalnızca <xref:System.Text.RegularExpressions.RegexOptions.IgnoreCase?displayProperty=nameWithType> ve <xref:System.Text.RegularExpressions.RegexOptions.Multiline?displayProperty=nameWithType> seçenekleriyle birleştirilebilir. Normal ifadede başka bir seçeneğin kullanılması <xref:System.ArgumentOutOfRangeException>sonuçlanır.

ECMAScript ve kurallı normal ifadelerin davranışı üç alanda farklılık gösterir: karakter sınıfı sözdizimi, kendine başvuran yakalama grupları ve sekizlik ve geri başvuru yorumu.

- Karakter sınıfı sözdizimi. Geleneksel normal ifadeler Unicode desteklediği için ECMAScript, ECMAScript 'teki karakter sınıfları daha sınırlı sözdizimine sahiptir ve bazı karakter sınıfı dil öğeleri farklı anlamdadır. Örneğin, ECMAScript Unicode kategorisi veya blok öğeleri `\p` ve `\P`gibi dil öğelerini desteklemez. Benzer şekilde, bir kelime karakteriyle eşleşen `\w` öğesi, `[a-zA-Z_0-9]` karakter sınıfına eşdeğerdir ve kurallı davranış kullanılırken ECMAScript ve `[\p{Ll}\p{Lu}\p{Lt}\p{Lo}\p{Nd}\p{Pc}\p{Lm}]` kullanılırken. Daha fazla bilgi için bkz. [karakter sınıfları](../../../docs/standard/base-types/character-classes-in-regular-expressions.md).

  Aşağıdaki örnek kurallı ve ECMAScript desenli eşleştirme arasındaki farkı gösterir. Bir normal ifade tanımlar, bu, sözcüklerin ardından boşluk karakterleri ile eşleşen `\b(\w+\s*)+`. Giriş, biri Latin karakter kümesini ve diğeri ise Kiril karakter kümesini kullanan iki dizeden oluşur. Çıktıda gösterildiği gibi, ECMAScript eşleştirmeyi kullanan <xref:System.Text.RegularExpressions.Regex.IsMatch%28System.String%2CSystem.String%2CSystem.Text.RegularExpressions.RegexOptions%29?displayProperty=nameWithType> yöntemine yapılan çağrı, Kiril kelimeleri ile eşleşemez, ancak kurallı eşleştirme kullanan yöntem çağrısı bu sözcüklerle eşleşir.

  [!code-csharp[Conceptual.Regex.Language.Options#16](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.options/cs/ecmascript1.cs#16)]
  [!code-vb[Conceptual.Regex.Language.Options#16](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.options/vb/ecmascript1.vb#16)]

- Kendine başvuran yakalama grupları. Kendisi için geri başvuru içeren bir normal ifade yakalama sınıfı, her yakalama yinelemesi ile güncelleştirilmeleri gerekir. Aşağıdaki örnekte gösterildiği gibi, bu özellik, normal ifade `((a+)(\1) ?)+` ECMAScript kullanılırken "aa aaaa aaaaaa" giriş dizesiyle eşleşecek, ancak kurallı eşleştirme kullanılırken değil.

  [!code-csharp[Conceptual.Regex.Language.Options#21](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.options/cs/ecmascript2.cs#21)]
  [!code-vb[Conceptual.Regex.Language.Options#21](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.options/vb/ecmascript2.vb#21)]

  Normal ifade aşağıdaki tabloda gösterildiği gibi tanımlanmıştır.

  |Desen|Açıklama|
  |-------------|-----------------|
  |(+)|"A" harfini bir veya daha fazla kez eşleştirin. Bu ikinci yakalama grubudur.|
  |(\ 1)|İlk yakalama grubu tarafından yakalanan alt dizeyle eşleştirin. Bu, üçüncü yakalama grubudur.|
  |?|Sıfır veya bir boşluk karakterini eşleştirin.|
  |((a +) (\ 1)?) +|Bir veya daha fazla "a" karakterinin örüntüsünün ardından ilk yakalama grubuyla eşleşen bir dize ve ardından sıfır veya bir boşluk karakteri bir veya daha fazla kez olacak şekilde eşleşen bir karakter. Bu ilk yakalama grubudur.|

- Sekizlik kaçış ve geri başvurular arasında belirsizlikleri çözümlemesi. Aşağıdaki tabloda, kurallı ve ECMAScript normal ifadelerine karşılık gelen sekizlik ve geribaşvuru yorumlamasının farkları özetlenmektedir.

  |Normal ifade|Kurallı davranış|ECMAScript davranışı|
  |------------------------|------------------------|-------------------------|
  |`\0` ardından 0 ile 2 sekizlik basamak|Sekizlik olarak yorumlayın. Örneğin, `\044` her zaman sekizlik bir değer olarak yorumlanır ve "$" anlamına gelir.|Aynı davranış.|
  |`\` sonra 1 ile 9 arasında bir rakam ve ardından ek ondalık basamak yok,|Bir geri başvuru olarak yorumlayın. Örneğin, bir dokuzuncu yakalama grubu mevcut olmasa bile `\9` her zaman geri başvuru 9 anlamına gelir. Yakalama grubu yoksa, normal ifade ayrıştırıcısı bir <xref:System.ArgumentException>oluşturur.|Tek bir ondalık basamak yakalama grubu varsa, bu basamağa geri başvuru. Aksi takdirde, değeri değişmez değer olarak yorumlayın.|
  |`\` sonra 1 ile 9 arasında bir rakam ve ardından ek ondalık basamaklar|Basamakları ondalık değer olarak yorumlayın. Bu yakalama grubu varsa, ifadeyi bir geri başvuru olarak yorumlayın.<br /><br /> Aksi takdirde, önde gelen sekizlik basamakları sekizlik 377 ' e kadar yorumlayın; diğer bir deyişle, yalnızca değerin düşük 8 bitini göz önünde bulundurun. Kalan basamakları değişmez değer olarak yorumlayın. Örneğin, ifadede `\3000`, Grup 300 yakalama varsa, geri başvuru 300 olarak yorumlayın; yakalama grubu 300 yoksa, sekizli 300 ve sonrasında 0 olarak yorumlanır.|Bir yakalamaya başvurabilen ondalık bir değere mümkün olduğunca çok basamak dönüştürerek bir geri başvuru olarak yorumlayın. Herhangi bir basamak dönüştürülemiyorsa, sekizlik basamağı 377 ' e kadar olan önde gelen sekizlik basamakları kullanarak sekizlik olarak yorumlayın; kalan basamakları değişmez değer olarak yorumlayın.|

## <a name="comparison-using-the-invariant-culture"></a>Sabit kültür kullanılarak karşılaştırma

Varsayılan olarak, normal ifade altyapısı büyük küçük harfe duyarsız karşılaştırmalar gerçekleştirdiğinde, eşdeğer büyük ve küçük harfli karakterleri anlamak için geçerli kültürün büyük/küçük harf kurallarını kullanır.

Ancak, özellikle Kullanıcı girişini parolalar, dosyalar veya URL 'Ler gibi sistem kaynaklarının adlarıyla karşılaştırırken, bu davranış bazı karşılaştırmalar türleri için istenmeyen bir durum değildir. Aşağıdaki örnek senaryo gibi gösterilmektedir. Kod, URL 'SI **FILE://** ile kullanıma hazır olan herhangi bir kaynağa erişimi engellemeye yöneliktir. Normal ifade, `$FILE://`normal ifade kullanarak dizeyle büyük/küçük harfe duyarsız bir eşleşme dener. Ancak, geçerli sistem kültürü tr-TR (Türkçe-Türkiye) olduğunda "I", "i" öğesinin büyük harfli eşdeğeri değildir. Sonuç olarak, <xref:System.Text.RegularExpressions.Regex.IsMatch%2A?displayProperty=nameWithType> yöntemine yapılan çağrı `false`döndürür ve dosyaya erişime izin verilir.

[!code-csharp[Conceptual.Regex.Language.Options#14](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.options/cs/culture1.cs#14)]
[!code-vb[Conceptual.Regex.Language.Options#14](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.options/vb/culture1.vb#14)]

> [!NOTE]
> Büyük/küçük harfe duyarlı ve sabit kültür kullanan dize karşılaştırmaları hakkında daha fazla bilgi için bkz. [dizeleri kullanmak Için En Iyi uygulamalar](../../../docs/standard/base-types/best-practices-strings.md).

Geçerli kültürün büyük/küçük harf duyarsız karşılaştırmalarını kullanmak yerine, dildeki kültürel farklarını yoksaymak ve sabit kültürün kurallarını kullanmak için <xref:System.Text.RegularExpressions.RegexOptions.CultureInvariant?displayProperty=nameWithType> seçeneğini belirtebilirsiniz.

> [!NOTE]
> Sabit kültür kullanılarak karşılaştırma yalnızca bir <xref:System.Text.RegularExpressions.Regex> sınıf oluşturucusunun veya statik kalıp eşleştirme yönteminin `options` parametresine <xref:System.Text.RegularExpressions.RegexOptions.CultureInvariant?displayProperty=nameWithType> değeri sağlanarak kullanılabilir. Satır içi seçeneği olarak kullanılamaz.

Aşağıdaki örnek, bir önceki örnekle aynıdır, ancak statik <xref:System.Text.RegularExpressions.Regex.IsMatch%28System.String%2CSystem.String%2CSystem.Text.RegularExpressions.RegexOptions%29?displayProperty=nameWithType> yöntemi <xref:System.Text.RegularExpressions.RegexOptions.CultureInvariant?displayProperty=nameWithType>içeren seçeneklerle çağırılır. Geçerli kültür Türkçe (Türkiye) olarak ayarlandığında bile, normal ifade altyapısı "dosya" ve "dosya" ile başarılı bir şekilde eşleştirebilir ve dosya kaynağına erişimi engelleyebilir.

[!code-csharp[Conceptual.Regex.Language.Options#15](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.options/cs/culture1.cs#15)]
[!code-vb[Conceptual.Regex.Language.Options#15](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.options/vb/culture1.vb#15)]

## <a name="see-also"></a>Ayrıca bkz.

- [Normal İfade Dili - Hızlı Başvuru](../../../docs/standard/base-types/regular-expression-language-quick-reference.md)
