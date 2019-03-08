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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9bb3120887a1a42d01b8d8ddc3351d1209294ffc
ms.sourcegitcommit: 58fc0e6564a37fa1b9b1b140a637e864c4cf696e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/08/2019
ms.locfileid: "57677571"
---
# <a name="regular-expression-options"></a>Normal İfade Seçenekleri

<a name="Top"></a> Varsayılan olarak, bir Giriş dizesinin normal ifade desenindeki herhangi bir sabit karakterin ile karşılaştırması büyük/küçük harfe duyarlıdır, normal ifade desenindeki boşluk, sabit boşluk karakterleri ve normal ifadedeki yakalama grupları olarak yorumlanır örtük ve açık olarak adlandırılır. Normal ifade seçeneklerini belirterek bunları ve varsayılan normal ifade davranışının diğer birçok yönünü değiştirebilirsiniz. Aşağıdaki tabloda listelenen Bu seçenekler, normal ifade deseni bir parçası olarak satır içi olabilir veya için sağlanabilir bir <xref:System.Text.RegularExpressions.Regex?displayProperty=nameWithType> sınıfı oluşturucusunun veya statik desen eşleştirme yöntemine olarak bir <xref:System.Text.RegularExpressions.RegexOptions?displayProperty=nameWithType> numaralandırma değeri.

|RegexOptions üyesi|Satır içi karakter|Efekt|
|-------------------------|----------------------|------------|
|<xref:System.Text.RegularExpressions.RegexOptions.None>|Yok|Varsayılan davranışı kullanın. Daha fazla bilgi için [varsayılan seçenekleri](#Default).|
|<xref:System.Text.RegularExpressions.RegexOptions.IgnoreCase>|`i`|Büyük küçük harf duyarlı eşleme kullanın. Daha fazla bilgi için [Case-Insensitive eşleşen](#Case).|
|<xref:System.Text.RegularExpressions.RegexOptions.Multiline>|`m`|Çok satırlı modunu kullanın, burada `^` ve `$` (yerine başlangıcını ve bitişini girdi dizesinin) her bir satırın sonuna eşleşir. Daha fazla bilgi için [çok satırlı modu](#Multiline).|
|<xref:System.Text.RegularExpressions.RegexOptions.Singleline>|`s`|Nokta (.), her karakterle eşleştiği tek satır modunu kullanın (dışında her karakter yerine `\n`). Daha fazla bilgi için [tek satırlı mod](#Singleline).|
|<xref:System.Text.RegularExpressions.RegexOptions.ExplicitCapture>|`n`|Adsız grupları yakalamayın. Tek geçerli yakalamalar açıkça adlandırılmış veya numaralandırılmış grupların biçiminde `(?<` *adı* `>` *subexpression*`)`. Daha fazla bilgi için [yalnızca belirtik yakalama](#Explicit).|
|<xref:System.Text.RegularExpressions.RegexOptions.Compiled>|Yok|Normal ifadeyi bir derleme için derleyin. Daha fazla bilgi için [derlenmiş normal ifadeler](#Compiled).|
|<xref:System.Text.RegularExpressions.RegexOptions.IgnorePatternWhitespace>|`x`|Çıkmamış boşluğu desenden hariç tutun ve sayı işaretinden sonra açıklamaları etkinleştirin (`#`). Daha fazla bilgi için [beyaz boşluğu yok saymak](#Whitespace).|
|<xref:System.Text.RegularExpressions.RegexOptions.RightToLeft>|Yok|Arama yönünü değiştirin. Arama sağdan sola yerine soldan sağa taşır. Daha fazla bilgi için [sağdan sola modu](#RightToLeft).|
|<xref:System.Text.RegularExpressions.RegexOptions.ECMAScript>|Yok|İfade için ECMAScript uyumlu davranışı etkinleştirin. Daha fazla bilgi için [ECMAScript eşleştirme davranışı](#ECMAScript).|
|<xref:System.Text.RegularExpressions.RegexOptions.CultureInvariant>|Yok|Dildeki kültürel farklılıkları yoksayın. Daha fazla bilgi için [sabit kültür kullanılarak karşılaştırma](#Invariant).|

## <a name="specifying-the-options"></a>Seçenekleri belirtme

Normal ifadeler için seçenekleri üç yoldan biriyle belirleyebilirsiniz:

- İçinde `options` parametresinin bir <xref:System.Text.RegularExpressions.Regex?displayProperty=nameWithType> sınıfı oluşturucusunun veya statik (`Shared` Visual Basic'te) desen eşleşmeli yöntemde gibi <xref:System.Text.RegularExpressions.Regex.%23ctor%28System.String%2CSystem.Text.RegularExpressions.RegexOptions%29?displayProperty=nameWithType> veya <xref:System.Text.RegularExpressions.Regex.Match%28System.String%2CSystem.String%2CSystem.Text.RegularExpressions.RegexOptions%29?displayProperty=nameWithType>. `options` Parametredir bir bit düzeyindeki OR kombinasyonudur <xref:System.Text.RegularExpressions.RegexOptions?displayProperty=nameWithType> numaralandırılmış değerlerinin.

    Ne zaman seçenekleri sağlanır için bir <xref:System.Text.RegularExpressions.Regex> kullanarak örneği `options` parametre sınıfı yapıcısının seçenekleri atanmış <xref:System.Text.RegularExpressions.RegexOptions?displayProperty=nameWithType> özelliği. Ancak, <xref:System.Text.RegularExpressions.RegexOptions?displayProperty=nameWithType> özelliği, normal ifade deseni satır içi seçenekler yansıtmıyor.

    Aşağıdaki örnek, bir gösterim sağlar. Kullandığı `options` parametresinin <xref:System.Text.RegularExpressions.Regex.Match%28System.String%2CSystem.String%2CSystem.Text.RegularExpressions.RegexOptions%29?displayProperty=nameWithType> büyük küçük harf duyarsız eşleşmeyi etkinleştirmek ve "d" harfi ile başlayan sözcükleri tanımlamak için kullanıldığında desen beyaz boşluğu yok saymak için yöntemi.

    [!code-csharp[Conceptual.Regex.Language.Options#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.options/cs/example1.cs#6)]
    [!code-vb[Conceptual.Regex.Language.Options#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.options/vb/example1.vb#6)]

- Sözdizimini içeren bir normal ifade deseninde satır içi seçenekler uygulayarak `(?imnsx-imnsx)`. Seçenek desen seçeneği seçeneği ile başka bir satır içi seçeneği tanımsız noktasına veya her iki desenin sonuna kadar tanımlanan noktasından uygulanır. Unutmayın <xref:System.Text.RegularExpressions.RegexOptions?displayProperty=nameWithType> özelliği bir <xref:System.Text.RegularExpressions.Regex> örneği, bu satır içi seçenekler yansıtmıyor. Daha fazla bilgi için [çeşitli yapıları](../../../docs/standard/base-types/miscellaneous-constructs-in-regular-expressions.md) konu.

    Aşağıdaki örnek, bir gösterim sağlar. Büyük küçük harf duyarsız eşleşmeyi etkinleştirmek ve "d" harfi ile başlayan sözcükleri tanımlamak için kullanıldığında desen beyaz boşluğu yok saymak için satıriçi seçeneklerini kullanır.

    [!code-csharp[Conceptual.Regex.Language.Options#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.options/cs/example1.cs#7)]
    [!code-vb[Conceptual.Regex.Language.Options#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.options/vb/example1.vb#7)]

- Söz dizimi ile normal ifade desenindeki belirli bir gruplandırma satır içi seçenekler uygulayarak oluşturmak `(?imnsx-imnsx:` *subexpression*`)`. Bir dizi seçenek kümesi kapanmadan önce hiçbir oturum; bir seçenek kümesi önce bir eksi işareti kümeyi kapatır. (`?` seçenekleri etkin veya devre dışı bırakılan, gerekli dil yapısı sözdiziminin sabit bir parçasıdır.) Seçeneği, yalnızca bu grup için geçerlidir. Daha fazla bilgi için bkz. [Gruplandırma Yapıları](../../../docs/standard/base-types/grouping-constructs-in-regular-expressions.md).

    Aşağıdaki örnek, bir gösterim sağlar. Büyük küçük harf duyarsız eşleşmeyi etkinleştirmek ve "d" harfi ile başlayan sözcükleri tanımlamak için kullanıldığında desen beyaz boşluğu yok saymak için satıriçi seçeneklerini Gruplandırma yapısında kullanır.

    [!code-csharp[Conceptual.Regex.Language.Options#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.options/cs/example1.cs#8)]
    [!code-vb[Conceptual.Regex.Language.Options#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.options/vb/example1.vb#8)]

Seçenekler satır için belirtilirse, eksi işareti varsa (`-`) önce bir seçenek veya seçenek kümesi bu seçenekleri kapatır. Örneğin, satır içi yapısı `(?ix-ms)` açar <xref:System.Text.RegularExpressions.RegexOptions.IgnoreCase?displayProperty=nameWithType> ve <xref:System.Text.RegularExpressions.RegexOptions.IgnorePatternWhitespace?displayProperty=nameWithType> seçenekleri ve kapanmadan <xref:System.Text.RegularExpressions.RegexOptions.Multiline?displayProperty=nameWithType> ve <xref:System.Text.RegularExpressions.RegexOptions.Singleline?displayProperty=nameWithType> seçenekleri. Tüm normal ifade seçenekleri varsayılan olarak kapalıdır.

> [!NOTE]
> Normal ifade seçeneği belirtilmişse `options` seçenekleri ile bir oluşturucu veya yöntem çağrısı çakışma parametresinin bir normal ifade deseninde satır içi belirtilen, satır içi seçenekler kullanılır.

Aşağıdaki beş normal ifade seçeneği hem seçenekler parametresi hem satır içi ile ayarlanabilir:

- <xref:System.Text.RegularExpressions.RegexOptions.IgnoreCase?displayProperty=nameWithType>

- <xref:System.Text.RegularExpressions.RegexOptions.Multiline?displayProperty=nameWithType>

- <xref:System.Text.RegularExpressions.RegexOptions.Singleline?displayProperty=nameWithType>

- <xref:System.Text.RegularExpressions.RegexOptions.ExplicitCapture?displayProperty=nameWithType>

- <xref:System.Text.RegularExpressions.RegexOptions.IgnorePatternWhitespace?displayProperty=nameWithType>

Aşağıdaki beş normal ifade seçeneği kullanılarak ayarlanabilir `options` parametre satır içi ayarlanamaz:

- <xref:System.Text.RegularExpressions.RegexOptions.None?displayProperty=nameWithType>

- <xref:System.Text.RegularExpressions.RegexOptions.Compiled?displayProperty=nameWithType>

- <xref:System.Text.RegularExpressions.RegexOptions.RightToLeft?displayProperty=nameWithType>

- <xref:System.Text.RegularExpressions.RegexOptions.CultureInvariant?displayProperty=nameWithType>

- <xref:System.Text.RegularExpressions.RegexOptions.ECMAScript?displayProperty=nameWithType>

## <a name="determining-the-options"></a>Seçenekleri belirleme

Hangi seçeneklerin sağlandığını belirleyebilirsiniz bir <xref:System.Text.RegularExpressions.Regex> nesne, salt okunur değerini alarak oluşturulduğunda <xref:System.Text.RegularExpressions.Regex.Options%2A?displayProperty=nameWithType> özelliği. Bu özellik tarafından oluşturulan derlenmiş bir normal ifade için tanımlanmış olan seçenekleri belirlemek için özellikle yararlıdır <xref:System.Text.RegularExpressions.Regex.CompileToAssembly%2A?displayProperty=nameWithType> yöntemi.

Dışında herhangi bir seçeneğin varlığını test etmek için <xref:System.Text.RegularExpressions.RegexOptions.None?displayProperty=nameWithType>, değeriyle bir AND işlemi gerçekleştirin <xref:System.Text.RegularExpressions.Regex.Options%2A?displayProperty=nameWithType> özelliği ve <xref:System.Text.RegularExpressions.RegexOptions> , olduğu ilgilenen değeri. Ardından sonuç eşit olup olmadığını test <xref:System.Text.RegularExpressions.RegexOptions> değeri. Aşağıdaki örnek testleri olmadığını <xref:System.Text.RegularExpressions.RegexOptions.IgnoreCase?displayProperty=nameWithType> seçeneğini ayarlayın.

[!code-csharp[Conceptual.Regex.Language.Options#19](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.options/cs/determine1.cs#19)]
[!code-vb[Conceptual.Regex.Language.Options#19](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.options/vb/determine1.vb#19)]

Sınanacak <xref:System.Text.RegularExpressions.RegexOptions.None?displayProperty=nameWithType>, belirlemek olmadığını değerini <xref:System.Text.RegularExpressions.Regex.Options%2A?displayProperty=nameWithType> özelliğini eşittir <xref:System.Text.RegularExpressions.RegexOptions.None?displayProperty=nameWithType>, aşağıdaki örnekte gösterildiği gibi.

[!code-csharp[Conceptual.Regex.Language.Options#20](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.options/cs/determine1.cs#20)]
[!code-vb[Conceptual.Regex.Language.Options#20](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.options/vb/determine1.vb#20)]

Aşağıdaki bölümler .NET normal ifade tarafından desteklenen seçenekleri listelemektedir.

<a name="Default"></a>

## <a name="default-options"></a>Varsayılan seçenekleri

<xref:System.Text.RegularExpressions.RegexOptions.None?displayProperty=nameWithType> Seçeneği, hiçbir seçenek belirtilmedi ve normal ifade motorunun varsayılan davranışını kullandığını gösterir. Bu, aşağıdakileri içerir:

- Desen, kurallı yerine ECMAScript normal ifade olarak yorumlanır.

- Normal ifade deseni, giriş dizesi soldan sağa eşleştirilir.

- Karşılaştırmalar büyük/küçük harfe duyarlıdır.

- `^` Ve `$` dil öğelerini eşleşen başlangıcını ve bitişini girdi dizesinin.

- `.` Dil öğesi dışında her karakterle eşleşir `\n`.

- Normal ifade desenindeki herhangi bir boşluk bir hazır bilgi boşluk karakteri yorumlanır.

- Geçerli kültürün kuralları giriş dizesi deseni karşılaştırılırken kullanılır.

- Normal ifade desenindeki yakalama grupları örtük olarak açıktır.

> [!NOTE]
> <xref:System.Text.RegularExpressions.RegexOptions.None?displayProperty=nameWithType> Seçeneği olan satır içi eşdeğeri yoktur. Normal ifade seçenekleri satır içi uygulandığında olduğunda, belirli bir seçenek kapatıp varsayılan davranışı bir seçeneği tarafından seçeneği temelinde geri yüklenir. Örneğin, `(?i)` büyük küçük harf duyarsız karşılaştırmayı açar ve `(?-i)` varsayılan büyük küçük harfe duyarlı karşılaştırmayı geri yükler.

Çünkü <xref:System.Text.RegularExpressions.RegexOptions.None?displayProperty=nameWithType> seçeneği normal ifade motorunun varsayılan davranışını temsil eder, bu nadiren açıkça bir yöntem çağrısında belirtilir. Bir oluşturucu veya statik desen eşleştirme yönteminin olmadan bir `options` parametresi yerine çağrılır.

[Başa dön](#Top)

<a name="Case"></a>

## <a name="case-insensitive-matching"></a>Büyük küçük harf duyarsız eşleştirme

<xref:System.Text.RegularExpressions.RegexOptions.IgnoreCase> Seçeneği veya `i` satır içi seçeneği büyük küçük harf duyarlı eşleştirme sağlar. Varsayılan olarak, geçerli kültürün büyük/küçük harf kuralları kullanılır.

Aşağıdaki örnek, bir normal ifade desenini tanımlar `\bthe\w*\b`, "" ile başlayan tüm sözcüklerle eşleşir. Yapılan ilk çağrı <xref:System.Text.RegularExpressions.Regex.Match%2A> varsayılan büyük/küçük harfe karşılaştırma yöntemini kullanan, çıktı "" cümlenin dizeyi eşleşmediğini gösterir. Eşleştirilir olduğunda <xref:System.Text.RegularExpressions.Regex.Match%2A> kümesine seçeneklerle yöntemi çağrıldığında <xref:System.Text.RegularExpressions.RegexOptions.IgnoreCase>.

[!code-csharp[Conceptual.Regex.Language.Options#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.options/cs/case1.cs#1)]
[!code-vb[Conceptual.Regex.Language.Options#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.options/vb/case1.vb#1)]

Aşağıdaki örnek, normal ifade deseni yerine satır içi seçeneklerini kullanmak için önceki örnekte değiştirir `options` büyük küçük harf duyarsız karşılaştırma sağlamak için parametre. İlk desen yalnızca dizesinde "t" harfi için geçerli olan bir gruplama yapısında büyük küçük harf duyarsız seçeneğini tanımlar "". Seçenek yapısı desenin başında oluştuğundan, ikinci desen, normal ifadenin tamamına büyük küçük harf duyarsız seçeneği uygular.

[!code-csharp[Conceptual.Regex.Language.Options#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.options/cs/case2.cs#2)]
[!code-vb[Conceptual.Regex.Language.Options#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.options/vb/case2.vb#2)]

[Başa dön](#Top)

<a name="Multiline"></a>

## <a name="multiline-mode"></a>Çok satırlı modu

<xref:System.Text.RegularExpressions.RegexOptions.Multiline?displayProperty=nameWithType> Seçeneği veya `m` satır içi seçeneği, birden çok satır içeren bir giriş dizesini işlemek normal ifade altyapısı sağlar. Yorumu değişiklikleri `^` ve `$` dil öğelerini böylece bunlar bir satırın başlangıcını ve bitişini girdi dizesinin yerine eşleşir.

Varsayılan olarak, `$` yalnızca Giriş dizesinin sonuyla eşleşir. Belirtirseniz <xref:System.Text.RegularExpressions.RegexOptions.Multiline?displayProperty=nameWithType> seçeneği, yeni satır karakteri eşleşir (`\n`) veya Giriş dizesinin sonu. Bu ancak, satır başı/satır besleme karakter birleşimi eşleşmiyor. Başarılı bir şekilde eşleştirmek için alt ifadesini kullanın. `\r?$` yerine yalnızca `$`.

Aşağıdaki örnek bovling oyuncularının adları ve puanlarını ayıklar ve eklenmeye bir <xref:System.Collections.Generic.SortedList%602> azalan düzende sıralayan koleksiyonu. <xref:System.Text.RegularExpressions.Regex.Matches%2A> Yöntemi iki kez çağrılır. İlk yöntem çağrısında düzenli ifadedir `^(\w+)\s(\d+)$` seçenekleri ayarlayın. Normal ifade altyapısı giriş desenini başlangıcını ve bitişini girdi dizesinin birlikte eşleştiğinden çıktının gösterdiği gibi bir eşleşme bulunamadı. Normal ifadeyle değiştirilir ikinci yöntem çağrısında `^(\w+)\s(\d+)\r?$` ve seçenekleri ayarlamak <xref:System.Text.RegularExpressions.RegexOptions.Multiline?displayProperty=nameWithType>. Çıktıda gösterildiği gibi ad ve puanlar başarıyla eşleştirilir ve puanlar azalan düzende görüntülenir.

[!code-csharp[Conceptual.Regex.Language.Options#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.options/cs/multiline1.cs#3)]
[!code-vb[Conceptual.Regex.Language.Options#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.options/vb/multiline1.vb#3)]

Normal ifade deseni `^(\w+)\s(\d+)\r*$` aşağıdaki tabloda gösterildiği gibi tanımlanmaktadır.

|Desen|Açıklama|
|-------------|-----------------|
|`^`|Satırın başlangıcında başlayın.|
|`(\w+)`|Bir veya daha fazla sözcük karakteri eşleştir. Bu ilk yakalama grubudur.|
|`\s`|Bir boşluk karakteri ile eşleştirin.|
|`(\d+)`|Bir veya daha fazla ondalık basamağı eşleştirin. Bu ikinci yakalama grubudur.|
|`\r?`|Sıfır veya bir satır başı karakteri eşleştirin.|
|`$`|Satır sonunda Bitir.|

Satır içi seçeneğini kullanması hariç, aşağıdaki örnek Öncekine, eşdeğerdir `(?m)` çok satırlı seçeneği ayarlamak için.

[!code-csharp[Conceptual.Regex.Language.Options#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.options/cs/multiline2.cs#4)]
[!code-vb[Conceptual.Regex.Language.Options#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.options/vb/multiline2.vb#4)]

[Başa dön](#Top)

<a name="Singleline"></a>

## <a name="single-line-mode"></a>Tek satır modu

<xref:System.Text.RegularExpressions.RegexOptions.Singleline?displayProperty=nameWithType> Seçeneği veya `s` satır içi seçeneği, normal ifade motoru, Giriş dizesinin tek satırlık oluşuyorsa olarak değerlendirilecek neden olur. Bunu nokta davranışını değiştirerek yapar (`.`) dil öğesinin onun yerine yeni satır karakteri dışında her karakterle eşleşen bağlı olarak, her karakter ile eşleşir `\n` veya \u000A.

Aşağıdaki örnekte nasıl davranışını `.` dil öğesinde değişiklikler kullandığınızda <xref:System.Text.RegularExpressions.RegexOptions.Singleline?displayProperty=nameWithType> seçeneği. Normal ifade `^.+` dize başlangıcında başlar ve her karakter ile eşleşir. Varsayılan olarak eşleştirme, ilk satırın sonunda biter; satır başı karakteri normal ifade deseniyle eşleşen `\r` veya \u000D, ancak eşleşmiyor `\n`. Çünkü <xref:System.Text.RegularExpressions.RegexOptions.Singleline?displayProperty=nameWithType> seçeneği Giriş dizesinin tamamının tek bir satır olarak yorumladığından, giriş dizesindeki her karakterle eşleşir dahil olmak üzere `\n`.

[!code-csharp[Conceptual.Regex.Language.CharacterClasses#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.characterclasses/cs/any2.cs#5)]
[!code-vb[Conceptual.Regex.Language.CharacterClasses#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.characterclasses/vb/any2.vb#5)]

Satır içi seçeneğini kullanması hariç, aşağıdaki örnek Öncekine, eşdeğerdir `(?s)` tek satır modunu etkinleştirmek için.

[!code-csharp[Conceptual.Regex.Language.Options#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.options/cs/singleline1.cs#5)]
[!code-vb[Conceptual.Regex.Language.Options#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.options/vb/singleline1.vb#5)]

[Başa dön](#Top)

<a name="Explicit"></a>

## <a name="explicit-captures-only"></a>Yalnızca açık yakalamalar

Varsayılan olarak, yakalama grupları, normal ifade deseninde ayraç kullanılarak tanımlanır. Adlandırılmış gruplara bir ad atanan veya göre sayı `(?<` *adı*`>`*subexpression* `)` dil seçeneği, oysa adsız gruplara dizinden erişilebilir. İçinde <xref:System.Text.RegularExpressions.GroupCollection> nesnesi, adlandırılmamış gruplar adlandırılmış grupların önünde.

Yapıları gruplandırma genellikle yalnızca birden çok dil öğesine miktar Belirleyicileri uygulamak için kullanılır ve yakalanan alt dizeler ilgili değildir. Örneğin, aşağıdaki normal ifade:

```
\b\(?((\w+),?\s?)+[\.!?]\)?
```

yalnızca nokta, ünlem işareti veya bir belgeden oluşturulan soru işareti ile biten cümleler ayıklamak için tasarlanmıştır (ile temsil edilir <xref:System.Text.RegularExpressions.Match> nesnesi) ilgi çekecektir. Koleksiyondaki sözcükler değildir.

Yakalama sonradan kullanılmayan grupları pahalı olabilir, normal ifade motorunun hem doldurması gerektiğinden <xref:System.Text.RegularExpressions.GroupCollection> ve <xref:System.Text.RegularExpressions.CaptureCollection> nesneleri koleksiyonu. Alternatif olarak, ya da kullanabilirsiniz <xref:System.Text.RegularExpressions.RegexOptions.ExplicitCapture?displayProperty=nameWithType> seçeneği veya `n` tek geçerli yakalamalar açıkça adlandırılmış veya numaralandırılmış tarafından atanan gruplar emin belirtmek için satır içi seçeneği `(?<` *adı* `>` *subexpression* `)` oluşturun.

Aşağıdaki örnek tarafından döndürülen eşleşme hakkında bilgi görüntüler `\b\(?((\w+),?\s?)+[\.!?]\)?` normal ifade deseni <xref:System.Text.RegularExpressions.Regex.Match%2A> olmadan yöntemi çağrıldığında <xref:System.Text.RegularExpressions.RegexOptions.ExplicitCapture?displayProperty=nameWithType> seçeneği. İlk yöntem çıktısı olarak gösterir çağrısı, normal ifade altyapısı tamamen doldurur <xref:System.Text.RegularExpressions.GroupCollection> ve <xref:System.Text.RegularExpressions.CaptureCollection> yakalanan alt dizelerle ilgili bilgilerle nesneleri koleksiyonu. İkinci yöntem ile çağrıldığından `options` kümesine <xref:System.Text.RegularExpressions.RegexOptions.ExplicitCapture?displayProperty=nameWithType>, gruplarıyla ilgili bilgi yakalamaz.

[!code-csharp[Conceptual.Regex.Language.Options#9](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.options/cs/explicit1.cs#9)]
[!code-vb[Conceptual.Regex.Language.Options#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.options/vb/explicit1.vb#9)]

Normal ifade deseni`\b\(?((?>\w+),?\s?)+[\.!?]\)?` aşağıdaki tabloda gösterildiği gibi tanımlanmaktadır.

|Desen|Açıklama|
|-------------|-----------------|
|`\b`|Bir sözcük sınırında başlayın.|
|`\(?`|Eşleşen sıfır veya bir oluşumunu parantez açmayı mı ("(").|
|`(?>\w+),?`|Sıfır veya bir virgülü izleyen bir veya daha fazla sözcük karakterini eşleştirin. Sözcük karakterlerini eşleştirirken gerçekleştirmeyin.|
|`\s?`|Sıfır veya bir beyaz boşluk karakterini eşleştirin.|
|`((\w+),?\s?)+`|Bir veya daha fazla sözcük karakterini, sıfır veya bir virgül ve sıfır bileşimi ile eşleştirmek veya bir beyaz alan karakteri bir veya daha fazla kez.|
|`[\.!?]\)?`|Sıfır veya bir kapanış parantezi ('') izleyen üç Noktalama işaretinden hiçbiriyle ").|

Ayrıca `(?n)` otomatik yakalamaları bastırmak için satır içi öğesi. Aşağıdaki örnek kullanmak için önceki normal ifade desenini değiştirmektedir `(?n)` yerine satır içi öğesini <xref:System.Text.RegularExpressions.RegexOptions.ExplicitCapture?displayProperty=nameWithType> seçeneği.

[!code-csharp[Conceptual.Regex.Language.Options#10](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.options/cs/explicit2.cs#10)]
[!code-vb[Conceptual.Regex.Language.Options#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.options/vb/explicit2.vb#10)]

Son olarak, satır içi Grup öğesini kullanabilirsiniz `(?n:)` grubu tarafından temelinde otomatik yakalamaları bastırmak için. Aşağıdaki örnek, dış gruptaki adlandırılmamış yakalamaları bastırmak için önceki desenle değiştirir `((?>\w+),?\s?)`. De iç gruptaki adlandırılmamış yakalamaları bastırdığına dikkat edin.

[!code-csharp[Conceptual.Regex.Language.Options#11](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.options/cs/explicit3.cs#11)]
[!code-vb[Conceptual.Regex.Language.Options#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.options/vb/explicit3.vb#11)]

[Başa dön](#Top)

<a name="Compiled"></a>

## <a name="compiled-regular-expressions"></a>Derlenmiş normal ifadeler

Varsayılan olarak, .NET içinde normal ifadeler yorumlanır. Olduğunda bir <xref:System.Text.RegularExpressions.Regex> nesnesi başlatılırsa veya bir statik <xref:System.Text.RegularExpressions.Regex> yöntemi çağrıldığında, normal ifade deseni bir özel işlem kodları kümesine ayrıştırılır ve bir yorumlayıcı normal ifadeyi çalıştırmak için bu işlem kodlarını kullanır. Bu bir tradeoff içerir: Normal ifade motor başlatılırken maliyetini çalıştırma performans küçültülür en aza indirilir.

Kullanabileceğiniz yorumlanan normal ifadeler yerine derlenmiş <xref:System.Text.RegularExpressions.RegexOptions.Compiled?displayProperty=nameWithType> seçeneği. Bu durumda, bir desen normal ifade altyapısına geçirildiğinde, bu işlem kodları kümesine ayrıştırılır ve sonra doğrudan ortak dil çalışma zamanına geçirilebilen Microsoft Ara dilini (MSIL) dönüştürülür. Derlenmiş normal ifadeler başlatma zamanından taviz vererek çalışma zamanı performansını en üst düzeye çıkarın.

> [!NOTE]
> Normal bir ifade yalnızca sağlanarak derlenebilir <xref:System.Text.RegularExpressions.RegexOptions.Compiled?displayProperty=nameWithType> değerini `options` parametresinin bir <xref:System.Text.RegularExpressions.Regex> sınıfı oluşturucusunun veya statik desen eşleştirme yönteminin. Bir satır içi seçenek olarak kullanılamaz.

Hem statik çağrılarda derlenmiş normal ifadeler ve örnek normal ifadeler kullanabilirsiniz. Statik normal ifadelerde, <xref:System.Text.RegularExpressions.RegexOptions.Compiled?displayProperty=nameWithType> seçeneği geçirildiğinde `options` normal ifade desen eşleşmeli yönteminin parametresi. İçin geçirilen örnek normal ifadelerde `options` parametresinin <xref:System.Text.RegularExpressions.Regex> sınıf oluşturucusu. Her iki durumda da Gelişmiş performansla sonuçlanır.

Ancak, bu performans artışı yalnızca aşağıdaki koşullarda oluşur:

- A <xref:System.Text.RegularExpressions.Regex> normal ifade deseni eşleştirme yöntemlerine yapılan birden çok çağrıda kullanılan belirli bir normal ifadeyi temsil eden nesne.

- <xref:System.Text.RegularExpressions.Regex> Nesnesinin tekrar kullanılabilmesi için kapsam dışına çıkmasına izin verilmiyor.

- Normal ifade deseni eşleştirme yöntemlerine yapılan birden çok çağrıda statik bir normal ifade kullanılır. (Performans iyileştirmesi statik yöntem çağrılarında kullanılan normal ifadeler normal ifade motoru tarafından önbelleğe alındığından mümkündür.)

> [!NOTE]
> <xref:System.Text.RegularExpressions.RegexOptions.Compiled?displayProperty=nameWithType> Seçeneği ilgisi olmayan <xref:System.Text.RegularExpressions.Regex.CompileToAssembly%2A?displayProperty=nameWithType> yöntemi öntanımlı derlenmiş normal ifadeler içeren özel amaçlı bir derleme oluşturur.

[Başa dön](#Top)

<a name="Whitespace"></a>

## <a name="ignore-white-space"></a>Boşluğu yoksay

Varsayılan olarak, bir normal ifade deseninde boşluk önemlidir; Giriş dizesindeki bir boşluk karakteri eşleştirmek için normal ifade altyapısı zorlar. Bu nedenle, normal ifade "`\b\w+\s`"ve"`\b\w+` " kabaca eşdeğeridir. Ayrıca, bir normal ifade deseninde sayı işaretiyle (#) karşılaşıldığında, eşleştirilecek değişmez değer olarak yorumlanır.

<xref:System.Text.RegularExpressions.RegexOptions.IgnorePatternWhitespace?displayProperty=nameWithType> Seçeneği veya `x` satır içi seçeneği bu varsayılan davranışı aşağıdaki gibi değişir:

- Normal ifade deseninde kaçışsız boşluk yoksayıldı. Bir normal ifade deseninin parçası olması için boşluk karakterlerinden kaçınılmalıdır (örneğin, `\s` veya "`\` ").

- Sayı işaretiyle (#) değişmez bir karakter olarak değil, bir açıklama başlangıcı olarak yorumlanır. Normal ifade deseninde # karakterinden dizenin sonuna tüm metin açıklama olarak yorumlanır.

Kullansanız bile ancak aşağıdaki durumlarda, boşluk karakterlerinin normal bir ifadede, göz ardı olmayan <xref:System.Text.RegularExpressions.RegexOptions.IgnorePatternWhitespace?displayProperty=nameWithType> seçeneği:

- Bir karakter sınıfı içindeki boşluk her zaman tam anlamıyla yorumlanır. Örneğin, normal ifade deseni `[ .,;:]` herhangi tek bir boşluk karakteri, nokta, virgül, noktalı virgül veya iki nokta üst üste ile eşleşir.

- Boşluk kullanılamaz köşeli parantez içindeki miktar belirleyici içinde gibi `{` *n*`}`, `{` *n*`,}`, ve `{` *n* `,` *m*`}`. Örneğin, normal ifade deseni `\d{1, 3}` bir boşluk karakteri içerdiği için herhangi bir ila üç basamak basamak dizisi eşleştirilecek başarısız olur.

- Boşluk bir dil öğesi tanıtan bir karakter dizisi içinde izin verilmiyor. Örneğin:

    - Language öğesi `(?:` *subexpression* `)` Yakalama yapmayan grubu temsil eder ve `(?:` öğesi bir kısmı, alanları katıştırılmış olamaz. Desen `(? :` *subexpression* `)` oluşturur bir <xref:System.ArgumentException> çalışma zamanında normal ifade altyapısı, desen ve deseni ayrıştıramadığından `( ?:` *alt ifade*  `)` eşleştirilecek başarısız *subexpression*.

    - Language öğesi `\p{` *adı*`}`, bir Unicode kategorisinin temsil eder veya adlandırılmış blok, içinde gömülü boşluklar içeremez `\p{` öğe kısmı. Öğenin bir boşluk içeriyorsa, oluşturur bir <xref:System.ArgumentException> çalışma zamanında.

Bu seçeneğin etkinleştirilmesi, genellikle ayrıştırılması ve anlaşılması zor olan normal ifadelerin basitleştirilmesine yardımcı olur. Okunabilirliğini artırır ve normal ifadeyi belgeleyebilir.

Aşağıdaki örnek, aşağıdaki normal ifade desenini tanımlar:

`\b \(? ( (?>\w+) ,?\s? )+  [\.!?] \)? # Matches an entire sentence.`

Bu Düzen bölümünde tanımlanan örnekle benzer [yalnızca belirtik yakalama](#Explicit) da kullanması hariç, bölüm <xref:System.Text.RegularExpressions.RegexOptions.IgnorePatternWhitespace?displayProperty=nameWithType> desen beyaz boşluğu yok saymak için seçeneği.

[!code-csharp[Conceptual.Regex.Language.Options#12](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.options/cs/whitespace1.cs#12)]
[!code-vb[Conceptual.Regex.Language.Options#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.options/vb/whitespace1.vb#12)]

Aşağıdaki örnek, satır içi seçeneğini kullanır. `(?x)` desen beyaz boşluğu yok saymak için.

[!code-csharp[Conceptual.Regex.Language.Options#13](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.options/cs/whitespace2.cs#13)]
[!code-vb[Conceptual.Regex.Language.Options#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.options/vb/whitespace2.vb#13)]

[Başa dön](#Top)

<a name="RightToLeft"></a>

## <a name="right-to-left-mode"></a>Sağdan sola modu

Varsayılan olarak, normal ifade motoru soldan sağa arar. Kullanarak arama yönünü ters çevirebilirsiniz <xref:System.Text.RegularExpressions.RegexOptions.RightToLeft?displayProperty=nameWithType> seçeneği. Arama dizenin son karakter konumunda otomatik olarak başlar. Bir başlangıç ekleyin, deseni eşleştirme yöntemlerine parametresi gibi konumu <xref:System.Text.RegularExpressions.Regex.Match%28System.String%2CSystem.Int32%29?displayProperty=nameWithType>, arama olduğu başlamak için en sağdaki karakter konumunun dizinini olduğu başlangıç konumu.

> [!NOTE]
> Sağdan sola desen modu yalnızca sağlanarak kullanılabilir <xref:System.Text.RegularExpressions.RegexOptions.RightToLeft?displayProperty=nameWithType> değerini `options` parametresinin bir <xref:System.Text.RegularExpressions.Regex> sınıfı oluşturucusunun veya statik desen eşleştirme yönteminin. Bir satır içi seçenek olarak kullanılamaz.

<xref:System.Text.RegularExpressions.RegexOptions.RightToLeft?displayProperty=nameWithType> Seçeneği yalnızca arama yönünü değiştirir; normal ifade desenini sağdan sola yorumlayamaz. Örneğin, normal ifade `\bb\w+\s` sözcük "b" harfiyle başlayan ve sonrasında bir boşluk karakteri ile eşleşir. Aşağıdaki örnekte, giriş dizesindeki bir veya daha fazla "b" karakteri içeren üç sözcükten oluşuyor. İlk sözcük "b" ile başlar, ikinci biter "b" ve üçüncüsü sözcük ortasında iki "b" karakteri içerir. Örneğin çıktısında gösterildiği gibi yalnızca ilk sözcük normal ifade deseni ile eşleşir.

[!code-csharp[Conceptual.Regex.Language.Options#17](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.options/cs/righttoleft1.cs#17)]
[!code-vb[Conceptual.Regex.Language.Options#17](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.options/vb/righttoleft1.vb#17)]

Ayrıca ileriye yönelik onay ( `(?=` *subexpression* `)` dil öğesi) ve geriye yönelik onayın ( `(?<=` *subexpression* `)`dil öğesi) yön değiştirmediğini. İleriye yönelik onaylar sağa arar; Geriye dönük onaylar ise sola dönüktür. Örneğin, normal ifade `(?<=\d{1,2}\s)\w+,?\s\d{4}` ay adını önünde bir tarih için test etmek için geriye yönelik onay kullanır. Normal ifade daha sonra ay ve yılı eşleştirir. İleriye ve geriye yönelik onaylar hakkında daha fazla bilgi için bkz: [Grouping Constructs](../../../docs/standard/base-types/grouping-constructs-in-regular-expressions.md).

[!code-csharp[Conceptual.Regex.Language.Options#18](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.options/cs/righttoleft2.cs#18)]
[!code-vb[Conceptual.Regex.Language.Options#18](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.options/vb/righttoleft2.vb#18)]

Normal ifade deseni aşağıdaki tabloda gösterildiği gibi tanımlanır.

|Desen|Açıklama|
|-------------|-----------------|
|`(?<=\d{1,2}\s)`|Eşleşmenin başına bir veya iki ondalık basamak ardından bir boşluk tarafından gelmelidir.|
|`\w+`|Bir veya daha fazla sözcük karakteri eşleştir.|
|`,?`|Sıfır veya bir virgül karakterini eşleştirin.|
|`\s`|Bir boşluk karakteri ile eşleştirin.|
|`\d{4}`|Dört ondalık basamağı eşleştirin.|

[Başa dön](#Top)

<a name="ECMAScript"></a>

## <a name="ecmascript-matching-behavior"></a>ECMAScript eşleştirme davranışı

Varsayılan olarak, normal ifade altyapısı kurallı davranışı bir normal ifade deseni eşleştirme yapılırken metin girişi için kullanır. Ancak, ECMAScript davranışı belirterek eşleşen kullanılacak normal ifade altyapısı bildirebilirsiniz <xref:System.Text.RegularExpressions.RegexOptions.ECMAScript?displayProperty=nameWithType> seçeneği.

> [!NOTE]
> ECMAScript uyumlu davranış yalnızca sağlanarak kullanılabilir <xref:System.Text.RegularExpressions.RegexOptions.ECMAScript?displayProperty=nameWithType> değerini `options` parametresinin bir <xref:System.Text.RegularExpressions.Regex> sınıfı oluşturucusunun veya statik desen eşleştirme yönteminin. Bir satır içi seçenek olarak kullanılamaz.

<xref:System.Text.RegularExpressions.RegexOptions.ECMAScript?displayProperty=nameWithType> Seçeneği, yalnızca ile birleştirilebilir <xref:System.Text.RegularExpressions.RegexOptions.IgnoreCase?displayProperty=nameWithType> ve <xref:System.Text.RegularExpressions.RegexOptions.Multiline?displayProperty=nameWithType> seçenekleri. Normal ifadede herhangi bir seçeneğin kullanımı sonuçlanıyor bir <xref:System.ArgumentOutOfRangeException>.

ECMAScript ve kurallı normal ifadelerin davranışı üç alanda farklılık gösterir: karakter sınıfı sözdizimi, kendi kendine başvuruda bulunan yakalama grupları ve sekizliye karşı geribaşvuru yorumu.

- Karakter sınıfı sözdizimi. ECMAScript nin almadığı kurallı normal ifadeler Unicode'u desteklediğinden, ECMAScript karakter sınıfları daha sınırlı sözdizimine sahiptir ve bazı karakter sınıfı dil öğeleri farklı bir anlama sahip. Örneğin, ECMAScript Unicode kategorisi veya blok öğeler gibi Dil öğelerini desteklemez `\p` ve `\P`. Benzer şekilde, `\w` bir sözcük karakteri ile eşleşir, öğesi, eşdeğer `[a-zA-Z_0-9]` ECMAScript kullanılırken karakter sınıfını ve `[\p{Ll}\p{Lu}\p{Lt}\p{Lo}\p{Nd}\p{Pc}\p{Lm}]` kurallı davranışı kullanırken. Daha fazla bilgi için bkz.[Karakter Sınıfları](../../../docs/standard/base-types/character-classes-in-regular-expressions.md).

    Aşağıdaki örnek, kurallı arasındaki farkı gösterir ve ECMAScript desen eşleştirme. Bir normal ifade tanımlar `\b(\w+\s*)+`, boşluk karakterlerinin izlediği sözcükleri eşleştirir. Giriş, iki dizeyi, Latin karakter kümesi kullanan bir ve diğeri Kiril karakter kümesi kullanan oluşur. Çıktıda gösterildiği çağrısı olarak <xref:System.Text.RegularExpressions.Regex.IsMatch%28System.String%2CSystem.String%2CSystem.Text.RegularExpressions.RegexOptions%29?displayProperty=nameWithType> ECMAScript eşleştirme kullanan yöntem başarısız Kiril sözcüklerle eşleştirilecek ancak kurallı eşleştirme kullanan yöntem çağrısı Bu sözcüklerle eşleşir.

    [!code-csharp[Conceptual.Regex.Language.Options#16](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.options/cs/ecmascript1.cs#16)]
    [!code-vb[Conceptual.Regex.Language.Options#16](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.options/vb/ecmascript1.vb#16)]

- Kendi kendine başvurma yakalama grupları. Kendisine geri başvuru içeren bir normal ifade yakalama sınıfı, her yakalama yinelemesi ile güncelleştirilmelidir. Aşağıdaki örnekte gösterildiği gibi bu özellik, normal ifade sağlar. `((a+)(\1) ?)+` ECMAScript kullanılırken, ancak kurallı eşleştirme kullanılırken değil "aa aaaa aaaaaa" giriş dizesiyle eşleştirmek için.

    [!code-csharp[Conceptual.Regex.Language.Options#21](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.options/cs/ecmascript2.cs#21)]
    [!code-vb[Conceptual.Regex.Language.Options#21](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.options/vb/ecmascript2.vb#21)]

    Normal ifade aşağıdaki tabloda gösterildiği gibi tanımlanır.

    |Desen|Açıklama|
    |-------------|-----------------|
    |(a+)|Harf "a" bir veya daha fazla kez eşleştirin. Bu ikinci yakalama grubudur.|
    |(\1)|İlk yakalama grubu tarafından yakalanan alt dizeyi eşleştirin. Bu, üçüncü yakalama grubudur.|
    |?|Sıfır veya bir boşluk karakterini eşleştirin.|
    |((a+)(\1)?) +|Eşleşen "ilk yakalama grubuyla eşleşen bir dize tarafından izlenen bir veya daha fazla a" karakteri desenini ardından sıfır veya bir boşluk karakteri bir veya daha fazla kez. Bu ilk yakalama grubudur.|

- Sekizlik Kaçışlar ve geribaşvurular arasındaki belirsizliklerin çözümü. Aşağıdaki tabloda farklılıklar özetlenmektedir sekizliye karşı geribaşvuru yorumu tarafından kurallı ve ECMAScript normal ifadeler.

    |Normal ifade|Kurallı davranışı|ECMAScript davranışı|
    |------------------------|------------------------|-------------------------|
    |`\0` ardından 0 ila 2 sekizli basamak|Sekizli olarak yorumlayın. Örneğin, `\044` her zaman sekiz bir değer olarak yorumlanır ve "$" anlamına gelir.|Aynı davranış.|
    |`\` 1 ila 9, hiçbir ek ondalık basamak gelen ardından bir rakam,|Bir yeniden başvuru yorumlar. Örneğin, `\9` bir yakalama grubu dokuzuncu mevcut olsa bile her zaman geri başvuru 9 anlamına gelir. Yakalama grubu yoksa, normal ifade ayrıştırıcısı oluşturur bir <xref:System.ArgumentException>.|Bir tek bir ondalık basamak yakalama grubu varsa, o sayı için geri başvuru. Aksi takdirde, değeri değişmez değer olarak yorumlayın.|
    |`\` ardından 1 ila 9, ek ondalık basamak gelen bir rakam|Rakamları ondalık değer olarak yorumlayın. Bu yakalama grubu varsa, ifadeyi bir geri başvuru olarak yorumlayın.<br /><br /> Aksi halde, önde gelen sekizlik sayıyı sekizlik 377 yorumlayın; diğer bir deyişle, yalnızca düşük 8 bitlik değerini göz önünde bulundurun. Kalan rakamları değişmez değer olarak yorumlayın. Örneğin, ifadede `\3000`, yakalama grubu 300 varsa, geri başvuru 300 yorumlayın; yakalama grubu 300 yoksa, ardından 0 gelen sekizlik 300 olarak yorumlayın.|Yakalamaya başvurabilirsiniz bir ondalık değer için mümkün olduğunca çok basamak dönüştürerek bir geribaşvuru yorumlar. Önde gelen sekizlik sayıyı sekizlik 377'ni kullanarak herhangi bir basamak dönüştürülemezse sekizli olarak yorumlayın; Kalan rakamları değişmez değer olarak yorumlayın.|

[Başa dön](#Top)

<a name="Invariant"></a>

## <a name="comparison-using-the-invariant-culture"></a>Sabit kültür kullanılarak karşılaştırma

Normal ifade motoru büyük küçük harf duyarsız karşılaştırmalar gerçekleştirdiğinde, varsayılan olarak, geçerli kültürün büyük/küçük harf kuralları eşdeğer büyük ve küçük harf karakterleri belirlemek için kullanır.

Ancak, bu özellikle, parolalar, dosyalar veya URL'ler gibi sistem kaynaklarının adları için kullanıcı girişi karşılaştırılırken bazı karşılaştırma türleri için istenmeyen bir davranıştır. Aşağıdaki örnek senaryoları gösterir. Kod URL'si ile giriş yapılmış herhangi bir kaynağa erişimi engelleyecek biçimde tasarlanmıştır **FILE://**. Normal ifade dizesini harf olarak eşleşen normal ifade kullanarak çalışır `$FILE://`. Geçerli sistem kültürü tr-TR (Türkçe-Türkiye) olduğunda, ancak "I" büyük harf eşdeğeri değildir "i". Sonuç olarak, çağrı <xref:System.Text.RegularExpressions.Regex.IsMatch%2A?displayProperty=nameWithType> yöntemi döndürür `false`, ve dosyaya erişime izin verilir.

[!code-csharp[Conceptual.Regex.Language.Options#14](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.options/cs/culture1.cs#14)]
[!code-vb[Conceptual.Regex.Language.Options#14](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.options/vb/culture1.vb#14)]

> [!NOTE]
> Büyük küçük harfe duyarlı olan ve sabit kültür kullanan dize karşılaştırmaları hakkında daha fazla bilgi için bkz: [kullanarak dizeleri için en iyi](../../../docs/standard/base-types/best-practices-strings.md).

Belirtebileceğiniz geçerli kültürün büyük küçük harf duyarsız karşılaştırmalarını kullanmak yerine, <xref:System.Text.RegularExpressions.RegexOptions.CultureInvariant?displayProperty=nameWithType> seçeneği dildeki kültürel farklılıkları yoksay ve sabit kültür kurallarını kullanmak için.

> [!NOTE]
> Sabit kültür kullanılarak karşılaştırma yalnızca sağlanarak kullanılabilir <xref:System.Text.RegularExpressions.RegexOptions.CultureInvariant?displayProperty=nameWithType> değerini `options` parametresinin bir <xref:System.Text.RegularExpressions.Regex> sınıfı oluşturucusunun veya statik desen eşleştirme yönteminin. Bir satır içi seçenek olarak kullanılamaz.

Aşağıdaki örnek dışında önceki örnekle aynıdır statik <xref:System.Text.RegularExpressions.Regex.IsMatch%28System.String%2CSystem.String%2CSystem.Text.RegularExpressions.RegexOptions%29?displayProperty=nameWithType> içeren seçeneklerle çağrılmasıdır yöntemi çağrıldığında <xref:System.Text.RegularExpressions.RegexOptions.CultureInvariant?displayProperty=nameWithType>. Geçerli kültür Türkçe (Türkiye) bile ayarlandığında, normal ifade altyapısı "FILE" ve "FILE" erişimi engelleyebilir ve dosya kaynağına başarılı bir şekilde eşleşecek şekilde kuramıyor.

[!code-csharp[Conceptual.Regex.Language.Options#15](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.options/cs/culture1.cs#15)]
[!code-vb[Conceptual.Regex.Language.Options#15](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.options/vb/culture1.vb#15)]

## <a name="see-also"></a>Ayrıca bkz.

- [Normal İfade Dili - Hızlı Başvuru](../../../docs/standard/base-types/regular-expression-language-quick-reference.md)
