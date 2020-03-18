---
title: Normal İfade davranışı
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- regular expressions, behavior
- .NET Framework regular expressions, behavior
ms.assetid: 0ee1a6b8-caac-41d2-917f-d35570021b10
ms.openlocfilehash: 504e315dda4e76f56a88d97149b1515b6743668b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "77124357"
---
# <a name="details-of-regular-expression-behavior"></a>Normal ifade davranışının ayrıntıları

.NET Framework düzenli ifade altyapısı, Perl, Python, Emacs ve Tcl tarafından kullanılan geleneksel Nondeterministic Sonlu Automaton (NFA) motorunu birleştiren bir geri izleme düzenli ifade eşleştirmesidir. Bu daha hızlı, ama daha sınırlı, saf düzenli ifade Deterministic Sonlu Automaton (DFA) bu awk, egrep veya lex bulunan gibi motorları ayırır. Bu da standart, ama yavaş, POSIX NFAs onu ayırır. Aşağıdaki bölümde üç tür normal ifade altyapısı açıklanır ve .NET Framework'deki normal ifadelerin neden geleneksel bir NFA altyapısı kullanılarak uygulandığı açıklanır.

## <a name="benefits-of-the-nfa-engine"></a>NFA motorunun faydaları

 DFA motorları desen eşleştirme gerçekleştirdiğinde, işlem sıraları giriş dizesi tarafından çalıştırılır. Motor giriş dizesinin başında başlar ve bir sonraki karakterin normal ifade deseniyle eşleşip eşleşmediğini belirlemek için sırayla ilerler. Onlar mümkün olan en uzun dize maç için garanti edebilirsiniz. Aynı karakteri asla iki kez test etmedikleri için, DFA motorları geri izlemeyi desteklemez. Ancak, bir DFA altyapısı yalnızca sonlu durum içerdiğinden, bir deseni geri başvurularla eşleştiremez ve açık bir genişletme oluşturmadığından, alt ifadeleri yakalayamaz.

 DFA motorlarının aksine, geleneksel NFA motorları desen eşleştirme gerçekleştirdiğinde, işleme sırası normal ifade deseni tarafından yönlendirilir. Belirli bir dil öğesini işlerken, motor açgözlü eşleştirme kullanır; diğer bir deyişle, giriş dizesinin mümkün olduğunca çok eşleşir. Ama aynı zamanda başarıyla bir alt ifade eşleştirdikten sonra durumunu kaydeder. Bir eşleşme sonunda başarısız olursa, ek eşleşmeleri deneyebilmek için motor kaydedilmiş bir duruma dönebilir. Daha sonra normal ifadedeki dil öğelerinin de eşleşebilmesi için başarılı bir alt ifade eşleşmesini terk etme işlemi *geri izleme*olarak bilinir. NFA motorları, normal bir ifadenin olası tüm açılımlarını belirli bir sırada test etmek ve ilk eşleşmeyi kabul etmek için geri izleme kullanır. Geleneksel bir NFA altyapısı başarılı bir eşleşme için normal ifadenin belirli bir genişlemesini oluşturduğundan, alt ifade eşleşmelerini ve eşleşen geri başvuruları yakalayabilir. Ancak, geleneksel bir NFA geri adım attığı için, farklı yollar üzerinden eyalete ulaştığında aynı durumu birden çok kez ziyaret edebilir. Sonuç olarak, en kötü durumda katlanarak yavaş çalıştırabilirsiniz. Geleneksel bir NFA altyapısı bulduğu ilk eşleşmeyi kabul ettiği için, diğer (muhtemelen daha uzun) eşleşmeleri de keşfedilmemiş olarak bırakabilir.

 POSIX NFA motorları geleneksel NFA motorları gibidir, ancak mümkün olan en uzun eşleşmeyi bulduklarını garanti edene kadar geri dönmeye devam ederler. Sonuç olarak, bir POSIX NFA motoru geleneksel NFA motorundan daha yavaştır ve bir POSIX NFA motoru kullandığınızda, geri izleme aramasının sırasını değiştirerek daha kısa bir eşleşmeyi daha uzun bir eşleşmeye tercih edemezsiniz.

 Geleneksel NFA motorları programcılar tarafından tercih edilir çünkü dize eşleştirme üzerinde DFA veya POSIX NFA motorlarına göre daha fazla kontrol sağlarlar. En kötü durumda, yavaş çalışmasına rağmen, belirsizlikleri azaltan ve geri izlemeyi sınırlayan desenler kullanarak doğrusal veya polinom zamanında kibritleri bulmalarını sağlayabilirsiniz. Başka bir deyişle, NFA motorları güç ve esneklik için performans ticareti olsa da, çoğu durumda normal bir ifade iyi yazılmışsa ve geri izlemenin performansı katlanarak düşüren durumlardan kaçınırsa, kabul edilebilir performans alameti sunarlar.

> [!NOTE]
> Aşırı geri izlemenin neden olduğu performans cezası ve bunların etrafında çalışmak için düzenli bir ifade oluşturma yolları hakkında bilgi [için](../../../docs/standard/base-types/backtracking-in-regular-expressions.md)Bkz.

## <a name="net-framework-engine-capabilities"></a>.NET Framework motor yetenekleri

 Geleneksel bir NFA altyapısının avantajlarından yararlanmak için ,NET Framework normal ifade altyapısı, programcıların geri izleme motorını yönlendirmesini sağlamak için eksiksiz bir yapı kümesi içerir. Bu yapılar daha hızlı eşleşmeleri bulmak veya diğerleri ne göre belirli açılımları lehine kullanılabilir.

 .NET Framework normal ifade altyapısının diğer özellikleri şunlardır:

- Tembel ölçütler: `??` `*?`, `+?` `{`, , *n*`,`*m*`}?`. Bu yapılar, geri izleme motoruna önce en az tekrar sayısını aramasını söyler. Buna karşılık, sıradan açgözlü niceleyiciler ilk tekrarları maksimum sayıda maç deneyin. Aşağıdaki örnek, ikisi arasındaki farkı göstermektedir. Normal bir ifade, bir sayıyla biten bir cümleyle eşleşir ve yakalama grubu bu sayıyı ayıklamak için tasarlanmıştır. Normal ifade, `.+(\d+)\.` normal ifade altyapısının `.+`sayının yalnızca son basamağı yakalamasına neden olan açgözlü niceleyiciyi içerir. Buna karşılık, normal `.+?(\d+)\.` ifade tembel niceleyici `.+?`içerir , hangi tüm sayı yakalamak için düzenli ifade altyapısı neden olur.

     [!code-csharp[Conceptual.RegularExpressions.Design#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.design/cs/lazy1.cs#1)]
     [!code-vb[Conceptual.RegularExpressions.Design#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.design/vb/lazy1.vb#1)]

     Bu normal ifadenin açgözlü ve tembel sürümleri aşağıdaki tabloda gösterildiği gibi tanımlanır:

    |Desen|Açıklama|
    |-------------|-----------------|
    |`.+`(açgözlü niceleyici)|Herhangi bir karakterin en az bir oluşumunu eşleştirin. Bu, normal ifade altyapısının tüm dizeyle eşleşmesine ve ardından desenin geri kalanını eşleştirmek için gerektiği gibi geri izlemesine neden olur.|
    |`.+?`(tembel niceleyici)|Herhangi bir karakterin en az bir oluşumunu eşleştirin, ancak mümkün olduğunca az eşleşme.|
    |`(\d+)`|En az bir sayısal karakteri eşleştirin ve ilk yakalama grubuna atayın.|
    |`\.`|Bir periyodu eşleştirin.|

     Tembel niceleyiciler hakkında daha fazla bilgi için, [Niceleyiciler](../../../docs/standard/base-types/quantifiers-in-regular-expressions.md)bakın.

- Pozitif lookahead: `(?=` *alt ifade*`)`. Bu özellik, geri izleme altyapısının bir alt ifadeyi eşleştirdikten sonra metindeki aynı noktaya dönmesini sağlar. Aynı konumdan başlayan birden çok delemi doğrulayarak metin boyunca arama yapmak yararlıdır. Ayrıca, motorun eşleşen metne substring dahil etmeden maçın sonunda bir alt dize olduğunu doğrulamak için izin verir. Aşağıdaki örnek, noktalama işaretleri tarafından takip edilmeyen bir cümledeki sözcükleri ayıklamak için pozitif bakış kullanır.

     [!code-csharp[Conceptual.RegularExpressions.Design#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.design/cs/lookahead1.cs#2)]
     [!code-vb[Conceptual.RegularExpressions.Design#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.design/vb/lookahead1.vb#2)]

     Normal ifade `\b[A-Z]+\b(?=\P{P})` aşağıdaki tabloda gösterildiği gibi tanımlanır.

    |Desen|Açıklama|
    |-------------|-----------------|
    |`\b`|Bir sözcük sınırında eşleşmeye başla.|
    |`[A-Z]+`|Herhangi bir alfabetik karakteri bir veya daha fazla kez eşleştirin. <xref:System.Text.RegularExpressions.Regex.Matches%2A?displayProperty=nameWithType> Yöntem <xref:System.Text.RegularExpressions.RegexOptions.IgnoreCase?displayProperty=nameWithType> seçeneği ile çağrıldığından, karşılaştırma büyük/küçük harf duyarsız.|
    |`\b`|Eşlemeyi bir sözcük sınırında sonlandır.|
    |`(?=\P{P})`|Bir sonraki karakterin noktalama işareti simgesi olup olmadığını belirlemek için ileriye bakın. Değilse, eşleşme başarılı olur.|

     Olumlu ileriye dönük iddialar hakkında daha fazla bilgi için, [Gruplandırma Yapıları'na](../../../docs/standard/base-types/grouping-constructs-in-regular-expressions.md)bakın.

- Negatif lookahead: `(?!` *alt ifade*`)`. Bu özellik, yalnızca bir alt ifade eşleşmezse bir ifadeyi eşleştirme özelliği ekler. Bu, özellikle bir aramayı budama için güçlüdür, çünkü eklenmesi gereken durumlar için bir ifadeden daha ortadan kaldırılması gereken bir servis talebi için ifade sağlamak genellikle daha kolaydır. Örneğin, "non" ile başlamayan sözcükler için bir ifade yazmak zordur. Aşağıdaki örnek, bunları dışlamak için negatif gözcü kullanır.

     [!code-csharp[Conceptual.RegularExpressions.Design#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.design/cs/lookahead2.cs#3)]
     [!code-vb[Conceptual.RegularExpressions.Design#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.design/vb/lookahead2.vb#3)]

     Normal ifade `\b(?!non)\w+\b` deseni aşağıdaki tabloda gösterildiği gibi tanımlanır.

    |Desen|Açıklama|
    |-------------|-----------------|
    |`\b`|Bir sözcük sınırında eşleşmeye başla.|
    |`(?!non)`|Geçerli dize "non" ile başlamadığından emin olmak için ileriye bakın. Olursa, eşleşme başarısız olur.|
    |`(\w+)`|Bir veya daha fazla sözcük karakteri eşleştir.|
    |`\b`|Eşlemeyi bir sözcük sınırında sonlandır.|

     Negatif ileriye dönük iddialar hakkında daha fazla bilgi için, [Gruplandırma Yapıları'na](../../../docs/standard/base-types/grouping-constructs-in-regular-expressions.md)bakın.

- Koşullu değerlendirme: `(?(` *ifade*`)` `(?(`*evet*`|`*hayır* `)` ve *isim*`)`*evet*`|`*hayır*`)`, *ifade* eşleşecek bir alt ifade olduğu yerde, *ad* yakalama grubunun adıdır, *evet* *ifade* eşleşirse eşleşen dizedir veya *ad* geçerli, boş olmayan yakalanan grup, ve *hayır* *ifade varsa eşleşecek alt ifadedir *eşleşmez veya *ad* geçerli, boş olmayan yakalanan bir grup değildir. Bu özellik, önceki bir alt ifade eşleşmesinin veya sıfır genişlikli bir iddianın sonucuna bağlı olarak, motorun birden fazla alternatif desen kullanarak arama yapmasına olanak tanır. Bu, örneğin, önceki bir alt ifadenin eşleşip eşleşmediğine bağlı bir alt ifadeyi eşleştirmeye izin veren daha güçlü bir geri gönderme biçimine izin verir. Aşağıdaki örnekteki normal ifade, hem genel hem de dahili kullanım için tasarlanmış paragraflarla eşleşir. Yalnızca dahili kullanım için tasarlanan `<PRIVATE>` paragraflar bir etiketle başlar. Normal ifade `^(?<Pvt>\<PRIVATE\>\s)?(?(Pvt)((\w+\p{P}?\s)+)|((\w+\p{P}?\s)+))\r?$` deseni, genel ve yakalama gruplarını ayırmak için dahili kullanıma yönelik paragrafların içeriğini atamak için koşullu değerlendirme kullanır. Bu paragraflar daha sonra farklı işlenebilir.

     [!code-csharp[Conceptual.RegularExpressions.Design#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.design/cs/conditional1.cs#4)]
     [!code-vb[Conceptual.RegularExpressions.Design#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.design/vb/conditional1.vb#4)]

     Normal ifade deseni aşağıdaki tabloda gösterildiği gibi tanımlanır.

    |Desen|Açıklama|
    |-------------|-----------------|
    |`^`|Maça bir çizginin başında başlayın.|
    |`(?<Pvt>\<PRIVATE\>\s)?`|Bir beyaz boşluk karakteri `<PRIVATE>` ardından dize sıfır veya bir olay maç. Eşleşmeyi bir yakalama grubuna `Pvt`ata.|
    |`(?(Pvt)((\w+\p{P}?\s)+)`|`Pvt` Yakalama grubu varsa, bir veya daha fazla sözcük karakterinin bir veya daha fazla oluşumunu eşleştirin ve ardından sıfır veya bir noktalama ayırıcısı ve ardından beyaz boşluk karakteri eşleştirin. Substring'i ilk yakalama grubuna atayın.|
    |<code>&#124;((\w+\p{P}?\s)+))</code>|`Pvt` Yakalama grubu yoksa, bir veya daha fazla sözcük karakterinin bir veya daha fazla oluşumunu eşleştirin ve ardından sıfır veya bir noktalama işaretçisi ve ardından beyaz boşluk karakteri yle eşleştirin. Alt dizeyi üçüncü yakalama grubuna atayın.|
    |`\r?$`|Bir çizginin sonu veya dize sonu maç.|

     Koşullu değerlendirme hakkında daha fazla bilgi için [alternation Constructs'a](../../../docs/standard/base-types/alternation-constructs-in-regular-expressions.md)bakın.

- Grup tanımlarını `(?<`dengeleme: *name1*`-`*name2* `>` alt *ifadesi*`)`. Bu özellik, normal ifade altyapısının parantez veya açma ve kapama ayraçları gibi iç içe yapıları izlemesini sağlar. Örneğin, [yapıoluşturma yı](../../../docs/standard/base-types/grouping-constructs-in-regular-expressions.md)bünyelerine bakın.

- Atomik gruplar: `(?>` *alt ifade*`)`. Bu özellik, geri izleme altyapısının, bir alt ifadenin, ifadenin içerdiği ifadeden bağımsız olarak çalışıyormuş gibi, bu alt ifade için bulunan yalnızca ilk eşleşmeyle eşleştiğini garanti etmesini sağlar. Bu yapıyı kullanmazsanız, aramaları daha büyük ifadeden geri izleme bir alt ifadenin davranışını değiştirebilir. Örneğin, normal ifade `(a+)\w` bir veya daha fazla "a" karakteriyle eşleşir ve "a" karakterleri dizisini izleyen bir sözcük karakteriyle eşleşir ve ilk yakalama grubuna "a" karakter dizisini atar. Ancak, giriş dizesinin son karakteri de "a" ise, `\w` dil öğesiyle eşleşir ve yakalanan gruba dahil edilmez.

     [!code-csharp[Conceptual.RegularExpressions.Design#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.design/cs/nonbacktracking2.cs#7)]
     [!code-vb[Conceptual.RegularExpressions.Design#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.design/vb/nonbacktracking2.vb#7)]

     Normal ifade `((?>a+))\w` bu davranışı engeller. Ardışık tüm "a" karakterleri geri izleme olmadan eşleştirildiklerinden, ilk yakalama grubu tüm ardışık "a" karakterlerini içerir. "A" karakterleri "a" dışında en az bir karakter daha takip edilmezse, eşleşme başarısız olur.

     [!code-csharp[Conceptual.RegularExpressions.Design#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.design/cs/nonbacktracking1.cs#8)]
     [!code-vb[Conceptual.RegularExpressions.Design#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.design/vb/nonbacktracking1.vb#8)]

     Atomik gruplar hakkında daha fazla bilgi için [bkz.](../../../docs/standard/base-types/grouping-constructs-in-regular-expressions.md)

- Bir <xref:System.Text.RegularExpressions.Regex> sınıf oluşturucu veya statik örnek eşleştirme <xref:System.Text.RegularExpressions.RegexOptions.RightToLeft?displayProperty=nameWithType> yöntemi seçeneği sağlayarak belirtilen sağdan sola eşleştirme. Bu özellik, soldan sağa yerine sağdan sola arama yaparken veya desenin sol yerine sağ kısmında eşleşmebaşlatmanın daha verimli olduğu durumlarda yararlıdır. Aşağıdaki örnekte de gösterildiği gibi, sağdan sola eşleştirme kullanarak açgözlü niceleyicilerin davranışını değiştirebilirsiniz. Örnek, bir sayıyla biten bir cümle için iki arama yapar. Açgözlü nicel'i kullanan soldan sağa arama, `+` cümledeki altı basamaktan biriyle eşleşirken, sağdan sola arama altı basamakla eşleşir. Normal ifade deseninin açıklaması için, bu bölümde daha önce tembel niceleyicileri gösteren örneğe bakın.

     [!code-csharp[Conceptual.RegularExpressions.Design#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.design/cs/rtl1.cs#6)]
     [!code-vb[Conceptual.RegularExpressions.Design#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.design/vb/rtl1.vb#6)]

     Sağdan sola eşleştirme hakkında daha fazla bilgi için [Normal İfade Seçenekleri'ne](../../../docs/standard/base-types/regular-expression-options.md)bakın.

- Olumlu ve negatif `(?<=`bakış: pozitif bakış için `(?<!`alt *ifade* `)` ve negatif bakış için alt *ifade.* `)` Bu özellik, bu konuda daha önce tartışılan ileriye benzer. Normal ifade altyapısı tam sağdan sola eşleştirmeye izin verdiğinden, normal ifadeler sınırsız bakışlara izin verir. İç içe geçen alt ifade bir dış ifadenin bir üst kümesi olduğunda, iç içe geçme ölçütlerini önlemek için pozitif ve negatif görünüm de kullanılabilir. Bu tür iç içe niceleyiciler ile düzenli ifadeler genellikle kötü performans sunuyoruz. Örneğin, aşağıdaki örnek, bir dize nin alfasayısal bir karakterle başlayıp bittiğini ve dizedeki diğer herhangi bir karakterin daha büyük bir alt kümeden biri olduğunu doğrular. E-posta adreslerini doğrulamak için kullanılan normal ifadenin bir bölümünü oluşturur; daha fazla bilgi için [bkz: Dizeleri Geçerli E-posta Biçiminde olduğunu doğrulayın.](../../../docs/standard/base-types/how-to-verify-that-strings-are-in-valid-email-format.md)

     [!code-csharp[Conceptual.RegularExpressions.Design#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.design/cs/lookbehind1.cs#5)]
     [!code-vb[Conceptual.RegularExpressions.Design#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.design/vb/lookbehind1.vb#5)]

     Normal ifade ``^[A-Z0-9]([-!#$%&'.*+/=?^`{}|~\w])*(?<=[A-Z0-9])$`` aşağıdaki tabloda gösterildiği gibi tanımlanır.

    |Desen|Açıklama|
    |-------------|-----------------|
    |`^`|Dize başında maç başlayın.|
    |`[A-Z0-9]`|Herhangi bir sayısal veya alfanümerik karakteri eşleştirin. (Karşılaştırma büyük/küçük harf duyarsızdır.)|
    |<code>([-!#$%&'.*+/=?^\`{}&#124;~\w])\*</code>|Herhangi bir sözcük karakterinin veya aşağıdaki karakterlerden herhangi birinin sıfır veya daha fazla oluşumlarını \*eşleştirin: -, !, #, $, %, &, ', ., +, /, =, ?, ^, &#96;, {, }, &#124; veya ~.|
    |`(?<=[A-Z0-9])`|Sayısal veya alfanümerik olmalıdır önceki karakter, arkasına bakın. (Karşılaştırma büyük/küçük harf duyarsızdır.)|
    |`$`|Dize sonunda maç sona erdirin.|

     Olumlu ve olumsuz bakışlar hakkında daha fazla bilgi için, [Gruplandırma Yapıları'na](../../../docs/standard/base-types/grouping-constructs-in-regular-expressions.md)bakın.

## <a name="related-articles"></a>İlgili makaleler:

|Başlık|Açıklama|
|-----------|-----------------|
|[Geri Dönüş](../../../docs/standard/base-types/backtracking-in-regular-expressions.md)|Alternatif eşleşmeleri bulmak için düzenli ifade geri izleme dalları hakkında bilgi sağlar.|
|[Derleme ve Yeniden Kullanma](../../../docs/standard/base-types/compilation-and-reuse-in-regular-expressions.md)|Performansı artırmak için düzenli ifadeleri derleme ve yeniden kullanma hakkında bilgi sağlar.|
|[İş Parçacığı Güvenliği](../../../docs/standard/base-types/thread-safety-in-regular-expressions.md)|Normal ifade iş parçacığı güvenliği hakkında bilgi sağlar ve normal ifade nesnelerine erişimi ne zaman eşitlemeniz gerektiğini açıklar.|
|[.NET Framework Normal İfadeleri](../../../docs/standard/base-types/regular-expressions.md)|Normal ifadelerin programlama dili boyutuna genel bir bakış sağlar.|
|[Normal İfade Nesne Modeli](../../../docs/standard/base-types/the-regular-expression-object-model.md)|Normal ifade sınıflarının nasıl kullanılacağını gösteren bilgi ve kod örnekleri sağlar.|
|[Normal İfade Örnekleri](../../../docs/standard/base-types/regular-expression-examples.md)|Ortak uygulamalarda normal ifadelerin kullanımını gösteren kod örnekleri içerir.|
|[Normal İfade Dili - Hızlı Başvuru](../../../docs/standard/base-types/regular-expression-language-quick-reference.md)|Normal ifadeleri tanımlamak için kullanabileceğiniz karakter kümesi, işleçler ve yapılar hakkında bilgi sağlar.|

## <a name="reference"></a>Başvuru

- <xref:System.Text.RegularExpressions?displayProperty=nameWithType>
