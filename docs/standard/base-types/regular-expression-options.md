---
title: "Normal İfade Seçenekleri"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "27"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 7bc068cc248e1ca8e1d3c64eaa4132682721e035
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="regular-expression-options"></a>Normal İfade Seçenekleri
<a name="Top"></a>Varsayılan olarak, herhangi bir normal ifade deseni değişmez değer karakter ile giriş dizesi karşılaştırması büyük küçük harfe duyarlı olduğundan, normal ifade deseni boşluk değişmez değer boşluk karakterleri ve yakalama gruplarında normal bir ifade olarak yorumlanır açıkça örtük olarak da adlandırılır. Normal ifade seçenekleri belirterek bu ve diğer birkaç varsayılan normal ifade davranışının yönlerini değiştirebilirsiniz. Aşağıdaki tabloda listelenen, bu seçenekleri normal ifade deseni bir parçası olarak dahil edilen satır içi olabilir ya da için sağlanabilir bir <xref:System.Text.RegularExpressions.Regex?displayProperty=nameWithType> sınıfı oluşturucusu veya statik desen eşleştirme yöntemi olarak bir <xref:System.Text.RegularExpressions.RegexOptions?displayProperty=nameWithType> numaralandırma değeri.  
  
|RegexOptions üyesi|Satır içi karakter|Efekt|  
|-------------------------|----------------------|------------|  
|<xref:System.Text.RegularExpressions.RegexOptions.None>|Yok|Varsayılan davranışını kullanın. Daha fazla bilgi için bkz: [varsayılan seçenekleri](#Default).|  
|<xref:System.Text.RegularExpressions.RegexOptions.IgnoreCase>|`i`|Büyük küçük harf duyarlı eşleme kullanın. Daha fazla bilgi için bkz: [Case-Insensitive eşleşen](#Case).|  
|<xref:System.Text.RegularExpressions.RegexOptions.Multiline>|`m`|Çok satırlı moda kullanın, burada `^` ve `$` başlangıcını ve bitişini her satırın (yerine, başlangıç ve bitiş Giriş dizesinin) eşleşmesi. Daha fazla bilgi için bkz: [çok satırlı modu](#Multiline).|  
|<xref:System.Text.RegularExpressions.RegexOptions.Singleline>|`s`|Her karakter nokta (.) eşleştiği tek satırlı modu kullan (her karakteri dışındaki yerine `\n`). Daha fazla bilgi için bkz: [Singleline modu](#Singleline).|  
|<xref:System.Text.RegularExpressions.RegexOptions.ExplicitCapture>|`n`|Adsız grupları yakalamayın. Yalnızca geçerli yakalamaları açıkça adlı veya numaralı grupları formun `(?<` *adı* `>` *alt*`)`. Daha fazla bilgi için bkz: [yalnızca açık yakalar](#Explicit).|  
|<xref:System.Text.RegularExpressions.RegexOptions.Compiled>|Yok|Normal ifade bir derleme derleyin. Daha fazla bilgi için bkz: [derlenmiş normal ifadeler](#Compiled).|  
|<xref:System.Text.RegularExpressions.RegexOptions.IgnorePatternWhitespace>|`x`|Atlanmayan boşluk düzeni dışlayın ve sonra sayı işareti açıklamaları etkinleştir (`#`). Daha fazla bilgi için bkz: [yoksay boşluk](#Whitespace).|  
|<xref:System.Text.RegularExpressions.RegexOptions.RightToLeft>|Yok|Arama yönünü değiştirin. Arama sağdan sola yerine soldan sağa taşır. Daha fazla bilgi için bkz: [sağdan sola modu](#RightToLeft).|  
|<xref:System.Text.RegularExpressions.RegexOptions.ECMAScript>|Yok|İfadenin ECMAScript uyumlu davranışı etkinleştirin. Daha fazla bilgi için bkz: [ECMAScript eşleşen davranış](#ECMAScript).|  
|<xref:System.Text.RegularExpressions.RegexOptions.CultureInvariant>|Yok|Kültürel dil farklılıkları yoksay. Daha fazla bilgi için bkz: [sabit kültür kullanarak karşılaştırma](#Invariant).|  
  
## <a name="specifying-the-options"></a>Seçeneklerini belirtme  
 Normal ifadeler için seçeneklerini üç yöntemden birini belirtebilirsiniz:  
  
-   İçinde `options` parametresinin bir <xref:System.Text.RegularExpressions.Regex?displayProperty=nameWithType> sınıfı oluşturucusu veya statik (`Shared` Visual Basic'te) desen eşleştirme yöntemi gibi <xref:System.Text.RegularExpressions.Regex.%23ctor%28System.String%2CSystem.Text.RegularExpressions.RegexOptions%29?displayProperty=nameWithType> veya <xref:System.Text.RegularExpressions.Regex.Match%28System.String%2CSystem.String%2CSystem.Text.RegularExpressions.RegexOptions%29?displayProperty=nameWithType>. `options` Parametresi birleşimidir bit düzeyinde OR <xref:System.Text.RegularExpressions.RegexOptions?displayProperty=nameWithType> değerleri numaralandırılır.  
  
     Zaman seçenekleri sağlanır için bir <xref:System.Text.RegularExpressions.Regex> kullanarak örnek `options` parametresi bir sınıf oluşturucu, seçeneklerdir atanan <xref:System.Text.RegularExpressions.RegexOptions?displayProperty=nameWithType> özelliği. Ancak, <xref:System.Text.RegularExpressions.RegexOptions?displayProperty=nameWithType> özelliği, normal ifade deseni satır içi seçeneklerinde yansıtacak değil.  
  
     Aşağıdaki örnek, bir gösterim sağlar. Kullandığı `options` parametresinin <xref:System.Text.RegularExpressions.Regex.Match%28System.String%2CSystem.String%2CSystem.Text.RegularExpressions.RegexOptions%29?displayProperty=nameWithType> yöntemi büyük küçük harf duyarsız eşleşen etkinleştirmek ve "d" harfiyle başlayan sözcükleri tanımlarken düzeni boşluk yoksay.  
  
     [!code-csharp[Conceptual.Regex.Language.Options#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.options/cs/example1.cs#6)]
     [!code-vb[Conceptual.Regex.Language.Options#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.options/vb/example1.vb#6)]  
  
-   Satır içi bir normal ifade deseni sözdizimiyle seçeneklerinde uygulayarak `(?imnsx-imnsx)`. Seçenek desen seçeneği seçeneği başka bir satır içi seçenek tarafından tanımsız noktasına veya ucunu bir desen tanımlanan noktasından uygulanır. Unutmayın <xref:System.Text.RegularExpressions.RegexOptions?displayProperty=nameWithType> özelliği bir <xref:System.Text.RegularExpressions.Regex> örneği, bu satır içi seçenekleri yansıtmak değil. Daha fazla bilgi için bkz: [çeşitli yapıları](../../../docs/standard/base-types/miscellaneous-constructs-in-regular-expressions.md) konu.  
  
     Aşağıdaki örnek, bir gösterim sağlar. Büyük küçük harf duyarsız eşleşen etkinleştirmek ve "d" harfiyle başlayan sözcükleri tanımlarken düzeni boşluk yoksaymak için satır içi seçeneklerini kullanır.  
  
     [!code-csharp[Conceptual.Regex.Language.Options#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.options/cs/example1.cs#7)]
     [!code-vb[Conceptual.Regex.Language.Options#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.options/vb/example1.vb#7)]  
  
-   Normal ifade deseni sözdizimiyle içinde belirli bir gruplandırma satır içi seçeneklerinde uygulayarak oluşturmak `(?imnsx-imnsx:` *alt*`)`. Bir seçenek kümesini kümesi kapanmadan önce hiçbir oturum; eksi bir seçenek kümesini önce kümesi devre dışı bırakır. (`?` seçenekleri etkin veya devre dışı bırakılan gereklidir dil yapısı 's sözdizimi, sabit bir parçasıdır.) Seçeneği, yalnızca bu grup için geçerlidir. Daha fazla bilgi için bkz: [gruplandırma yapıları](../../../docs/standard/base-types/grouping-constructs-in-regular-expressions.md).  
  
     Aşağıdaki örnek, bir gösterim sağlar. Büyük küçük harf duyarsız eşleşen etkinleştirmek ve "d" harfiyle başlayan sözcükleri tanımlarken düzeni boşluk yoksaymak için satır içi seçenekleri bir gruplama yapısı kullanır.  
  
     [!code-csharp[Conceptual.Regex.Language.Options#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.options/cs/example1.cs#8)]
     [!code-vb[Conceptual.Regex.Language.Options#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.options/vb/example1.vb#8)]  
  
 Belirtilen satır içi, eksi işareti seçeneklerini olması durumunda (`-`) önce bir seçenek veya seçenek kümesi bu seçenekleri devre dışı bırakır. Örneğin, satır içi oluşturmak `(?ix-ms)` açar <xref:System.Text.RegularExpressions.RegexOptions.IgnoreCase?displayProperty=nameWithType> ve <xref:System.Text.RegularExpressions.RegexOptions.IgnorePatternWhitespace?displayProperty=nameWithType> seçenekleri ve kapanmadan <xref:System.Text.RegularExpressions.RegexOptions.Multiline?displayProperty=nameWithType> ve <xref:System.Text.RegularExpressions.RegexOptions.Singleline?displayProperty=nameWithType> seçenekleri. Tüm normal ifade seçenekleri varsayılan olarak kapalıdır.  
  
> [!NOTE]
>  Normal ifade seçenekleri belirtilmişse `options` seçeneklerle Oluşturucusu veya yöntem çağrısı çakışma parametresi belirtilen satır içi bir normal ifade deseni, satır içi seçenekleri kullanılır.  
  
 Aşağıdaki beş normal ifade seçenekleri hem seçenekleri parametre ve satır içi ayarlayabilirsiniz:  
  
-   <xref:System.Text.RegularExpressions.RegexOptions.IgnoreCase?displayProperty=nameWithType>  
  
-   <xref:System.Text.RegularExpressions.RegexOptions.Multiline?displayProperty=nameWithType>  
  
-   <xref:System.Text.RegularExpressions.RegexOptions.Singleline?displayProperty=nameWithType>  
  
-   <xref:System.Text.RegularExpressions.RegexOptions.ExplicitCapture?displayProperty=nameWithType>  
  
-   <xref:System.Text.RegularExpressions.RegexOptions.IgnorePatternWhitespace?displayProperty=nameWithType>  
  
 Aşağıdaki beş normal ifade seçenekleri kullanılarak ayarlanabilir `options` parametresi satır içi ayarlanamaz, ancak:  
  
-   <xref:System.Text.RegularExpressions.RegexOptions.None?displayProperty=nameWithType>  
  
-   <xref:System.Text.RegularExpressions.RegexOptions.Compiled?displayProperty=nameWithType>  
  
-   <xref:System.Text.RegularExpressions.RegexOptions.RightToLeft?displayProperty=nameWithType>  
  
-   <xref:System.Text.RegularExpressions.RegexOptions.CultureInvariant?displayProperty=nameWithType>  
  
-   <xref:System.Text.RegularExpressions.RegexOptions.ECMAScript?displayProperty=nameWithType>  
  
## <a name="determining-the-options"></a>Seçeneklerini belirleme  
 Hangi seçeneklerin için sağlanan belirleyebilirsiniz bir <xref:System.Text.RegularExpressions.Regex> nesne salt okunur değeri alarak örneğinin başlatılmasından zaman <xref:System.Text.RegularExpressions.Regex.Options%2A?displayProperty=nameWithType> özelliği. Bu özellik tarafından oluşturulan derlenmiş bir normal ifade için tanımlanan seçeneklerini belirlemek için özellikle yararlıdır <xref:System.Text.RegularExpressions.Regex.CompileToAssembly%2A?displayProperty=nameWithType> yöntemi.  
  
 Dışında herhangi bir seçenek varlığını sınamak için <xref:System.Text.RegularExpressions.RegexOptions.None?displayProperty=nameWithType>, değeriyle ve işlemi <xref:System.Text.RegularExpressions.Regex.Options%2A?displayProperty=nameWithType> özelliği ve <xref:System.Text.RegularExpressions.RegexOptions> içinde ilgi değeri. Sonuç eşittir kapanmadığını <xref:System.Text.RegularExpressions.RegexOptions> değeri. Aşağıdaki örnek testleri olup olmadığını <xref:System.Text.RegularExpressions.RegexOptions.IgnoreCase?displayProperty=nameWithType> seçeneği ayarlayın.  
  
 [!code-csharp[Conceptual.Regex.Language.Options#19](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.options/cs/determine1.cs#19)]
 [!code-vb[Conceptual.Regex.Language.Options#19](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.options/vb/determine1.vb#19)]  
  
 Sınamak için <xref:System.Text.RegularExpressions.RegexOptions.None?displayProperty=nameWithType>, belirlemek olup olmadığını değerini <xref:System.Text.RegularExpressions.Regex.Options%2A?displayProperty=nameWithType> özelliği eşittir <xref:System.Text.RegularExpressions.RegexOptions.None?displayProperty=nameWithType>aşağıdaki örnekte gösterildiği gibi.  
  
 [!code-csharp[Conceptual.Regex.Language.Options#20](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.options/cs/determine1.cs#20)]
 [!code-vb[Conceptual.Regex.Language.Options#20](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.options/vb/determine1.vb#20)]  
  
 Aşağıdaki bölümlerde .NET normal ifadede tarafından desteklenen seçenekleri listelenmiştir.  
  
<a name="Default"></a>   
## <a name="default-options"></a>Varsayılan seçenekleri  
 <xref:System.Text.RegularExpressions.RegexOptions.None?displayProperty=nameWithType> Seçeneği hiçbir seçenek belirtilen ve normal ifade altyapısı kendi varsayılan davranışı kullanacağını gösterir. Buna aşağıdakiler dahildir:  
  
-   Bir kurallı yerine olarak ECMAScript normal ifade deseni yorumlanır.  
  
-   Giriş dizisinde soldan sağa normal ifade deseni eşleşir.  
  
-   Karşılaştırma büyük/küçük harfe duyarlıdır.  
  
-   `^` Ve `$` dil öğeleri eşleşen başlangıcını ve bitişini giriş dizesi.  
  
-   `.` Language öğesi eşleşen her karakteri dışındaki `\n`.  
  
-   Normal ifade deseni herhangi bir beyaz alanı bir değişmez değer boşluk karakteri yorumlanır.  
  
-   Geçerli kültür kurallarına giriş dizesi desen karşılaştırma olduğunda kullanılır.  
  
-   Normal ifade deseni yakalama gruplarında örtük olarak açık.  
  
> [!NOTE]
>  <xref:System.Text.RegularExpressions.RegexOptions.None?displayProperty=nameWithType> Seçeneği eşdeğer bir satır vardır. Normal ifade seçenekleri uygulanan satır içi olduğunda, varsayılan davranışı belirli bir seçenek kapatma tarafından bir seçenek olarak seçeneği temelinde geri yüklendi. Örneğin, `(?i)` büyük küçük harf duyarsız karşılaştırma üzerine kapatır ve `(?-i)` varsayılan büyük küçük harfe duyarlı karşılaştırma geri yükler.  
  
 Çünkü <xref:System.Text.RegularExpressions.RegexOptions.None?displayProperty=nameWithType> seçeneği normal ifade Altyapısı'nın varsayılan davranışını temsil eder, bu nadiren açıkça bir yöntem çağrısı belirtilir. Oluşturucunun ya da statik desen eşleştirme yöntemi olmadan bir `options` parametresi yerine çağrılır.  
  
 [Başa dön](#Top)  
  
<a name="Case"></a>   
## <a name="case-insensitive-matching"></a>Büyük küçük harf duyarsız eşleştirme  
 <xref:System.Text.RegularExpressions.RegexOptions.IgnoreCase> Seçeneğini veya `i` satır içi seçenek sağlar eşleştirme büyük küçük harfe duyarsızdır. Varsayılan olarak, geçerli kültürü büyük/küçük harf kuralları kullanılır.  
  
 Aşağıdaki örnekte bir normal ifade deseni tanımlayan `\bthe\w*\b`, "" ile başlayan tüm sözcükleri eşleşir. İlk çağrı çünkü <xref:System.Text.RegularExpressions.Regex.Match%2A> yöntemi kullanan varsayılan büyük küçük harfe duyarlı karşılaştırma, "" cümlesi başlar dizeyi eşlenemiyor çıkış gösterir. Eşleşen zaman <xref:System.Text.RegularExpressions.Regex.Match%2A> kümesine seçeneklerle yöntemi çağrıldığında <xref:System.Text.RegularExpressions.RegexOptions.IgnoreCase>.  
  
 [!code-csharp[Conceptual.Regex.Language.Options#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.options/cs/case1.cs#1)]
 [!code-vb[Conceptual.Regex.Language.Options#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.options/vb/case1.vb#1)]  
  
 Aşağıdaki örnek yerine satır içi seçeneklerini kullanmayı önceki örnekten normal ifade deseni değiştirir `options` parametresi büyük küçük harf duyarsız karşılaştırma sağlayın. İlk desen dizesindeki "t" harf yalnızca uygulandığı bir gruplandırma yapısında büyük küçük harf duyarsız seçeneği tanımlar. "". Seçenek yapı düzeni başında oluştuğundan, ikinci desen büyük küçük harf duyarsız seçeneği tüm normal ifadeye uygular.  
  
 [!code-csharp[Conceptual.Regex.Language.Options#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.options/cs/case2.cs#2)]
 [!code-vb[Conceptual.Regex.Language.Options#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.options/vb/case2.vb#2)]  
  
 [Başa dön](#Top)  
  
<a name="Multiline"></a>   
## <a name="multiline-mode"></a>Çok satırlı moda  
 <xref:System.Text.RegularExpressions.RegexOptions.Multiline?displayProperty=nameWithType> Seçeneğini veya `m` satır içi seçenek, çok satırlı oluşan giriş dizesi işlemek normal ifade altyapısı sağlar. Yorumu değiştirir `^` ve `$` dil öğeleri başlangıcını ve bitişini başlangıcını ve bitişini Giriş dizesinin yerine bir çizginin eşleşmesi.  
  
 Varsayılan olarak, `$` yalnızca giriş dizesi sonu ile eşleşir. Belirtirseniz <xref:System.Text.RegularExpressions.RegexOptions.Multiline?displayProperty=nameWithType> seçeneği, yeni satır karakteri eşleşen (`\n`) veya giriş dize sonu. Bu ancak, satır başı/karakter bileşimi satır besleme eşleşmiyor. Başarıyla ayarlarla eşleşecek şekilde alt kullanmak `\r?$` yerine yalnızca `$`.  
  
 Aşağıdaki örnek bowlers adları ve puanlarını ayıklar ve eklenmektedir bir <xref:System.Collections.Generic.SortedList%602> azalan düzende sıralar koleksiyonu. <xref:System.Text.RegularExpressions.Regex.Matches%2A> Yöntemi iki kez çağrılır. İlk yöntem çağrısında normal ifade olan `^(\w+)\s(\d+)$` ve hiçbir seçeneklerini ayarlayın. Normal ifade altyapısı başlangıcını ve bitişini Giriş dizesinin birlikte giriş düzeni eşleştiğinden çıkış gösterildiği gibi herhangi bir eşleşme bulunamadı. Normal ifade değiştirilir ikinci yöntem çağrısında `^(\w+)\s(\d+)\r?$` ve seçeneklerini ayarlamak <xref:System.Text.RegularExpressions.RegexOptions.Multiline?displayProperty=nameWithType>. Çıktı gösterildiği gibi ad ve puanlarını başarıyla eşleştirilir ve notların azalan sırada görüntülenir.  
  
 [!code-csharp[Conceptual.Regex.Language.Options#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.options/cs/multiline1.cs#3)]
 [!code-vb[Conceptual.Regex.Language.Options#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.options/vb/multiline1.vb#3)]  
  
 Normal ifade deseni `^(\w+)\s(\d+)\r*$` aşağıdaki tabloda gösterildiği gibi tanımlanır.  
  
|Desen|Açıklama|  
|-------------|-----------------|  
|`^`|Satırın başlangıcına başlayın.|  
|`(\w+)`|Bir veya daha fazla sözcük karakteri eşleştir. Bu ilk yakalama grubudur.|  
|`\s`|Bir boşluk karakteri ile eşleştirin.|  
|`(\d+)`|Bir veya daha fazla ondalık basamağı eşleştirin. Bu ikinci yakalama grubudur.|  
|`\r?`|Sıfır veya bir satır başı karakteri eşleşmesi.|  
|`$`|Satırın sonuna sonlandırın.|  
  
 Satır içi seçeneğini kullanan dışında aşağıdaki örnekte önceki birine eşdeğerdir `(?m)` çok satırlı seçeneğini ayarlamak için.  
  
 [!code-csharp[Conceptual.Regex.Language.Options#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.options/cs/multiline2.cs#4)]
 [!code-vb[Conceptual.Regex.Language.Options#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.options/vb/multiline2.vb#4)]  
  
 [Başa dön](#Top)  
  
<a name="Singleline"></a>   
## <a name="single-line-mode"></a>Tek satırlı modu  
 <xref:System.Text.RegularExpressions.RegexOptions.Singleline?displayProperty=nameWithType> Seçeneğini veya `s` satır içi seçenek, normal ifade altyapısı tarafından giriş dizesini tek bir satırı oluşuyorsa gibi davran neden olur. Bunu süresi davranışını değiştirerek yapar (`.`) yerine yeni satır karakteri dışındaki her karakter eşleştirme her karakter, BT'nin eşleşecek şekilde language öğesi `\n` veya \u000A.  
  
 Aşağıdaki örnek gösterilmektedir nasıl davranışını `.` language öğesi değişiklikleri kullandığınızda <xref:System.Text.RegularExpressions.RegexOptions.Singleline?displayProperty=nameWithType> seçeneği. Normal ifade `^.+` dizenin başında başlar ve her bir karakterle eşleşir. Varsayılan olarak, ilk satırın sonuna eşleşme sonlandırır; Normal ifade deseni ile eşleşen satır başı karakteri `\r` veya \u000D, ancak eşleşmiyor `\n`. Çünkü <xref:System.Text.RegularExpressions.RegexOptions.Singleline?displayProperty=nameWithType> seçeneği yorumlar tek bir satır olarak tüm giriş dizesi, giriş dizesi içinde her karakterle eşleşir dahil olmak üzere `\n`.  
  
 [!code-csharp[Conceptual.Regex.Language.CharacterClasses#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.characterclasses/cs/any2.cs#5)]
 [!code-vb[Conceptual.Regex.Language.CharacterClasses#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.characterclasses/vb/any2.vb#5)]  
  
 Satır içi seçeneğini kullanan dışında aşağıdaki örnekte önceki birine eşdeğerdir `(?s)` tek satırlı modunu etkinleştirmek için.  
  
 [!code-csharp[Conceptual.Regex.Language.Options#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.options/cs/singleline1.cs#5)]
 [!code-vb[Conceptual.Regex.Language.Options#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.options/vb/singleline1.vb#5)]  
  
 [Başa dön](#Top)  
  
<a name="Explicit"></a>   
## <a name="explicit-captures-only"></a>Yalnızca açık yakalar  
 Varsayılan olarak, yakalama gruplarını normal ifade deseni parantezlerde kullanımını tanımlanır. Adlandırılmış gruplar tarafından sayı veya bir ad atanmış `(?<` *adı*`>`*alt* `)` dil seçeneği ise adlandırılmamış grupları dizini tarafından erişilebilir. İçinde <xref:System.Text.RegularExpressions.GroupCollection> nesnesi, adlandırılmamış grupları adlandırılmış gruplar koyun.  
  
 Gruplandırma yapıları genellikle yalnızca nicelik birden çok dil öğelerine uygulamak için kullanılır ve hiçbir ilgilendiğiniz yakalanan alt dizeler. Örneğin, aşağıdaki normal ifade:  
  
```  
\b\(?((\w+),?\s?)+[\.!?]\)?  
```  
  
 yalnızca süresi, ünlem veya soru işareti bir belgeden yalnızca elde edilen cümlesi ile biter cümleleri ayıklamak için tasarlanmıştır (tarafından gösterilen <xref:System.Text.RegularExpressions.Match> nesnesi) ilginizi çekecektir. Koleksiyon içindeki ayrı sözcükleri değildir.  
  
 Daha sonra kullanılmayan grupları yakalama olabilir pahalı, normal ifade altyapısı hem de doldurmanız gerekir çünkü <xref:System.Text.RegularExpressions.GroupCollection> ve <xref:System.Text.RegularExpressions.CaptureCollection> koleksiyon nesnesi. Alternatif olarak, ya da kullanabilirsiniz <xref:System.Text.RegularExpressions.RegexOptions.ExplicitCapture?displayProperty=nameWithType> seçeneği veya `n` yalnızca geçerli yakalamaları açıkça adlı veya numaralı tarafından atanan grupları olduğunu belirtmek için satır içi seçeneği `(?<` *adı* `>` *alt* `)` oluşturun.  
  
 Aşağıdaki örnek tarafından döndürülen eşleşme hakkında bilgi görüntüler `\b\(?((\w+),?\s?)+[\.!?]\)?` normal ifade deseni <xref:System.Text.RegularExpressions.Regex.Match%2A> olan ve olmayan yöntemi çağrıldığında <xref:System.Text.RegularExpressions.RegexOptions.ExplicitCapture?displayProperty=nameWithType> seçeneği. İlk yöntem çıktısı olarak gösterir çağrısı, normal ifade altyapısı tam doldurur <xref:System.Text.RegularExpressions.GroupCollection> ve <xref:System.Text.RegularExpressions.CaptureCollection> yakalanan alt dizeler hakkında bilgi içeren koleksiyon nesnesi. İkinci yöntem ile çağrıldığı için `options` kümesine <xref:System.Text.RegularExpressions.RegexOptions.ExplicitCapture?displayProperty=nameWithType>, grupları bilgi yakalamaz.  
  
 [!code-csharp[Conceptual.Regex.Language.Options#9](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.options/cs/explicit1.cs#9)]
 [!code-vb[Conceptual.Regex.Language.Options#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.options/vb/explicit1.vb#9)]  
  
 Normal ifade deseni`\b\(?((?>\w+),?\s?)+[\.!?]\)?` aşağıdaki tabloda gösterildiği gibi tanımlanır.  
  
|Desen|Açıklama|  
|-------------|-----------------|  
|`\b`|Word sınırında başlayın.|  
|`\(?`|Eşleşen sıfır veya bir oluşumu açma ayracı ("(").|  
|`(?>\w+),?`|Sıfır veya bir virgül koyarak ve ardından bir veya daha fazla word karakterlerle eşleşen. Sözcük karakterlerini eşleştirirken geri izlemeyi değil.|  
|`\s?`|Sıfır veya bir beyaz boşluk karakterini eşleştirin.|  
|`((\w+),?\s?)+`|Bir veya daha fazla word karakter, sıfır veya bir virgül ve sıfır birleşimi eşleşmiyor veya bir veya birden çok kez bir boşluk karakterleri.|  
|`[\.!?]\)?`|Sıfır veya bir ayraç tarafından (") ve ardından üç noktalama simge hiçbiriyle").|  
  
 Aynı zamanda `(?n)` otomatik yakalamaları gizlemek için satır içi öğenin. Aşağıdaki örnek kullanmak için önceki normal ifade deseni değiştirir `(?n)` satır içi öğenin yerine <xref:System.Text.RegularExpressions.RegexOptions.ExplicitCapture?displayProperty=nameWithType> seçeneği.  
  
 [!code-csharp[Conceptual.Regex.Language.Options#10](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.options/cs/explicit2.cs#10)]
 [!code-vb[Conceptual.Regex.Language.Options#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.options/vb/explicit2.vb#10)]  
  
 Son olarak, satır içi Grup öğesi kullanabilirsiniz `(?n:)` grubu grubu temelinde otomatik yakalamaları gizlemek için. Aşağıdaki örnek dış Grup adlandırılmamış yakalamaları gizlemek için önceki düzeni değiştirdiği `((?>\w+),?\s?)`. Bu bastırır adlandırılmamış Not iç grubunda yakalar.  
  
 [!code-csharp[Conceptual.Regex.Language.Options#11](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.options/cs/explicit3.cs#11)]
 [!code-vb[Conceptual.Regex.Language.Options#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.options/vb/explicit3.vb#11)]  
  
 [Başa dön](#Top)  
  
<a name="Compiled"></a>   
## <a name="compiled-regular-expressions"></a>Derlenmiş normal ifadeler  
 Varsayılan olarak, .NET normal ifadelerde yorumlanır. Zaman bir <xref:System.Text.RegularExpressions.Regex> nesnesidir oluşturulmuş veya statik <xref:System.Text.RegularExpressions.Regex> yöntemi çağrıldığında, normal ifade deseni özel işlem kodları kümesine ayrıştırılır ve bir yorumlayıcı normal ifade çalıştırmak için bu işlem kodları kullanır. Bu bir kolaylığını içerir: çalışma zamanı performans ödün verme pahasına normal ifade altyapısı başlatma maliyetini en aza indirilir.  
  
 Kullanabileceğiniz yerine yorumlanan normal ifadeler kullanarak derlenmiş <xref:System.Text.RegularExpressions.RegexOptions.Compiled?displayProperty=nameWithType> seçeneği. Bu durumda, bir desen normal ifade altyapısı geçirildiğinde, bu işlem kodları kümesine ayrıştırılır ve doğrudan ortak dil çalışma zamanı için geçirilebilen Microsoft Ara dile (MSIL) dönüştürülür. Derlenmiş normal ifadeler başlatma saati ödün verme pahasına çalışma zamanı performansı en üst düzeye çıkarın.  
  
> [!NOTE]
>  Normal bir ifade yalnızca sağlayarak derlenebilir <xref:System.Text.RegularExpressions.RegexOptions.Compiled?displayProperty=nameWithType> değeri `options` parametresinin bir <xref:System.Text.RegularExpressions.Regex> sınıf oluşturucu veya statik bir desen eşleştirme yöntemi. Satır içi seçenek olarak kullanılabilir değil.  
  
 Hem statik çağrılarında derlenmiş normal ifadeler ve örneği normal ifadeler kullanabilirsiniz. Statik normal ifadelerde <xref:System.Text.RegularExpressions.RegexOptions.Compiled?displayProperty=nameWithType> seçeneği geçirilen `options` desen eşleştirme normal ifade yönteminin parametresi. İçin geçirilen örneği normal ifadelerde `options` parametresinin <xref:System.Text.RegularExpressions.Regex> sınıfı oluşturucusu. Her iki durumda da, Gelişmiş performansla sonuçlanır.  
  
 Ancak, bu geliştirme performans, yalnızca aşağıdaki koşullarda oluşur:  
  
-   A <xref:System.Text.RegularExpressions.Regex> belirli olağan bir ifadeyi temsil eden nesne birden fazla çağrı normal ifade desen eşleştirme yöntemleri için kullanılır.  
  
-   <xref:System.Text.RegularExpressions.Regex> Nesnesi tekrar kullanılabilmesi için kapsam dışına gitmek için izin yok.  
  
-   Statik bir normal ifade birden fazla çağrı normal ifade desen eşleştirme yöntemleri için kullanılır. (Performans geliştirmesi statik yöntem çağrılarında kullanılan normal ifadeleri normal ifade altyapısı tarafından önbelleğe alındığı için mümkündür.)  
  
> [!NOTE]
>  <xref:System.Text.RegularExpressions.RegexOptions.Compiled?displayProperty=nameWithType> Seçeneği ilgisi olmayan <xref:System.Text.RegularExpressions.Regex.CompileToAssembly%2A?displayProperty=nameWithType> önceden tanımlanmış derlenmiş normal ifadeler içeren bir özel amaçlı derleme oluşturur yöntemi.  
  
 [Başa dön](#Top)  
  
<a name="Whitespace"></a>   
## <a name="ignore-white-space"></a>Beyaz alan yoksay  
 Varsayılan olarak, bir normal ifade deseni boşluk önemlidir; Giriş dizisinde bir boşluk karakteri eşleştirmek için normal ifade altyapısı zorlar. Bu nedenle, normal ifade "`\b\w+\s`"ve"`\b\w+` " kabaca eşdeğer normal ifadeler. Ayrıca, numara işareti (#) bir normal ifade deseni karşılaşıldığında, eşleştirilmesini harf karakter olarak yorumlanır.  
  
 <xref:System.Text.RegularExpressions.RegexOptions.IgnorePatternWhitespace?displayProperty=nameWithType> Seçeneğini veya `x` satır içi seçenek, bu varsayılan davranışı aşağıdaki gibi değişir:  
  
-   Atlanmayan boşluk normal ifade deseni göz ardı edilir. Normal ifade deseni bir parçası olması için boşluk karakterleri kaçış uygulanmalıdır (örneğin, `\s` veya "`\` ").  
  
-   Sayı işareti (#) açıklama başlangıcını yerine harf karakter olarak yorumlanır. Tüm metin dizesi sonuna # karakter normal ifade deseni olarak bir açıklama olarak yorumlanır.  
  
 Kullansanız bile ancak, aşağıdaki durumlarda boşluk karakterlerini normal bir ifade, göz ardı olmayan <xref:System.Text.RegularExpressions.RegexOptions.IgnorePatternWhitespace?displayProperty=nameWithType> seçeneği:  
  
-   Boşluk karakteri sınıfı içinde her zaman tam anlamıyla yorumlanır. Örneğin, normal ifade deseni `[ .,;:]` herhangi tek boşluk karakterini, nokta, virgül, noktalı virgül veya iki nokta üst üste ile eşleşir.  
  
-   Beyaz alan kullanılamaz köşeli parantez içindeki bir niceleyici içinde gibi `{`  *n*  `}`, `{`  *n*  `,}`ve `{`  *n*  `,` *m*`}`. Örneğin, normal ifade deseni `\d{1. 3}` bir boşluk karakteri içerdiğinden bir ile üç basamak basamaklarının herhangi bir dizisini eşleştirmek başarısız olur.  
  
-   Beyaz alan language öğesi tanıtan bir karakter dizisi içinde izin verilmiyor. Örneğin:  
  
    -   Language öğesi `(?:` *alt* `)` Yakalama yapmayan bir grubu temsil eder ve `(?:` öğesi kısmı, alanları katıştırılmış olamaz. Desen `(? :` *alt* `)` oluşturur bir <xref:System.ArgumentException> çalışma zamanında normal ifade altyapısı düzeni ve düzeni ayrıştıramadığından `( ?:` *alt*  `)` eşleşecek şekilde başarısız *alt*.  
  
    -   Language öğesi `\p{` *adı*`}`, Unicode kategorisini temsil eder veya bloğu adlı içinde katıştırılmış boşluklar içeremez `\p{` öğesi kısmı. Bir boşluk içeriyorsa öğesi oluşturduğunda bir <xref:System.ArgumentException> çalışma zamanında.  
  
 Bu seçeneğin etkinleştirilmesi, genellikle ayrıştırılamıyor ve anlaşılması zor olan normal ifadeler basitleştirmeye yardımcı olur. Okunabilirliğini artırır ve normal bir ifade belge mümkün kılar.  
  
 Aşağıdaki örnek, aşağıdaki normal ifade deseni tanımlar:  
  
 `\b \(? ( (?>\w+) ,?\s? )+  [\.!?] \)? # Matches an entire sentence.`  
  
 Bu desen tanımlanan örnekle benzer [yalnızca açık yakalar](#Explicit) kullanır ancak bu, bölüm <xref:System.Text.RegularExpressions.RegexOptions.IgnorePatternWhitespace?displayProperty=nameWithType> düzeni boşluk gözardı etme seçeneği.  
  
 [!code-csharp[Conceptual.Regex.Language.Options#12](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.options/cs/whitespace1.cs#12)]
 [!code-vb[Conceptual.Regex.Language.Options#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.options/vb/whitespace1.vb#12)]  
  
 Aşağıdaki örnek satır içi seçeneğini kullanır `(?x)` düzeni boşluk yoksaymak için.  
  
 [!code-csharp[Conceptual.Regex.Language.Options#13](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.options/cs/whitespace2.cs#13)]
 [!code-vb[Conceptual.Regex.Language.Options#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.options/vb/whitespace2.vb#13)]  
  
 [Başa dön](#Top)  
  
<a name="RightToLeft"></a>   
## <a name="right-to-left-mode"></a>Sağdan sola modu  
 Varsayılan olarak, normal ifade altyapısı soldan sağa arar. Kullanarak arama yönünü ters çevirebilirsiniz <xref:System.Text.RegularExpressions.RegexOptions.RightToLeft?displayProperty=nameWithType> seçeneği. Arama dizesi son karakter konumunda otomatik olarak başlar. Başlangıç içeren desen eşleştirme yöntemleri parametresi gibi konumlandırmak için <xref:System.Text.RegularExpressions.Regex.Match%28System.String%2CSystem.Int32%29?displayProperty=nameWithType>, konumdan başlayarak olduğunu arama olduğu başlamak için en sağdaki karakterin dizini.  
  
> [!NOTE]
>  Sağdan sola desen modu kullanılabilir yalnızca sağlayarak <xref:System.Text.RegularExpressions.RegexOptions.RightToLeft?displayProperty=nameWithType> değeri `options` parametresinin bir <xref:System.Text.RegularExpressions.Regex> sınıf oluşturucu veya statik desen eşleştirme yöntemi. Satır içi seçenek olarak kullanılabilir değil.  
  
 <xref:System.Text.RegularExpressions.RegexOptions.RightToLeft?displayProperty=nameWithType> Seçeneği yalnızca arama yönünü değiştirir; sağdan sola normal ifade deseni yorumlama değil. Örneğin, normal ifade `\bb\w+\s` , "b" harfiyle başlayan ve sonrasında bir boşluk karakteri sözcükler eşleşir. Aşağıdaki örnekte, giriş dizesi bir veya daha fazla "b" karakter içeren üç sözcük birleşiminden oluşur. İlk word "b" ile başlar, "b" ve üçüncü ikinci biter word ortasında iki "b" karakter içerir. Örneğin çıktısını gösterildiği gibi yalnızca ilk sözcük normal ifade deseni eşleştirir.  
  
 [!code-csharp[Conceptual.Regex.Language.Options#17](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.options/cs/righttoleft1.cs#17)]
 [!code-vb[Conceptual.Regex.Language.Options#17](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.options/vb/righttoleft1.vb#17)]  
  
 Ayrıca ileri yönlü onaylama ( `(?=` *alt* `)` language öğesi) ve geriye ilerleme onaylama ( `(?<=` *alt* `)`language öğesi) yönü değiştirmeyin. İleri yönlü onaylar sağa bakın; geriye ilerleme onaylar sola arayın. Örneğin, normal ifade `(?<=\d{1,2}\s)\w+,?\s\d{4}` geriye ilerleme onaylama işlemi için bir ay tıklayınca bir tarihi test etmek için kullanır. Ay ve yıl sonra normal ifadeyle eşleşir. İleri yönlü ve geriye ilerleme assertsions hakkında daha fazla bilgi için bkz: [gruplandırma yapıları](../../../docs/standard/base-types/grouping-constructs-in-regular-expressions.md).  
  
 [!code-csharp[Conceptual.Regex.Language.Options#18](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.options/cs/righttoleft2.cs#18)]
 [!code-vb[Conceptual.Regex.Language.Options#18](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.options/vb/righttoleft2.vb#18)]  
  
 Normal ifade deseni aşağıdaki tabloda gösterildiği gibi tanımlanır.  
  
|Desen|Açıklama|  
|-------------|-----------------|  
|`(?<=\d{1,2}\s)`|Eşleşme başına bir boşluk bırakarak bir veya iki ondalık basamak gelmesi gerekir.|  
|`\w+`|Bir veya daha fazla sözcük karakteri eşleştir.|  
|`,?`|Sıfır veya bir virgül karakteri eşleştirmek.|  
|`\s`|Bir boşluk karakteri ile eşleştirin.|  
|`\d{4}`|Dört ondalık basamak eşleşir.|  
  
 [Başa dön](#Top)  
  
<a name="ECMAScript"></a>   
## <a name="ecmascript-matching-behavior"></a>ECMAScript eşleşen davranışı  
 Varsayılan olarak, normal ifade altyapısı kurallı davranışı bir normal ifade ile eşleşen metin girişi için kullanır. Ancak belirterek davranışı eşleşen ECMAScript kullanılacak normal ifade altyapısı söyleyebilirsiniz <xref:System.Text.RegularExpressions.RegexOptions.ECMAScript?displayProperty=nameWithType> seçeneği.  
  
> [!NOTE]
>  ECMAScript uyumlu davranış kullanılabilir yalnızca sağlayarak <xref:System.Text.RegularExpressions.RegexOptions.ECMAScript?displayProperty=nameWithType> değeri `options` parametresinin bir <xref:System.Text.RegularExpressions.Regex> sınıf oluşturucu veya statik desen eşleştirme yöntemi. Satır içi seçenek olarak kullanılabilir değil.  
  
 <xref:System.Text.RegularExpressions.RegexOptions.ECMAScript?displayProperty=nameWithType> Seçeneği, yalnızca ile birleştirilebilir <xref:System.Text.RegularExpressions.RegexOptions.IgnoreCase?displayProperty=nameWithType> ve <xref:System.Text.RegularExpressions.RegexOptions.Multiline?displayProperty=nameWithType> seçenekleri. Diğer bir seçenek normal ifadede kullanımını sonuçlanıyor bir <xref:System.ArgumentOutOfRangeException>.  
  
 Üç alana ECMAScript ve kurallı normal ifadeler davranışını farklıdır: karakter sınıfı sözdizimi, kendine başvuran grupları yakalama ve yeniden başvuru yorumlama karşı sekizli.  
  
-   Karakter sınıfı sözdizimi. ECMAScript'in almadığı kurallı normal ifadeler Unicode desteği olduğundan daha kısıtlı bir söz dizimi ECMAScript karakter sınıfları sahip ve bazı karakter sınıfı dil öğeleri farklı bir anlama sahip. Örneğin, ECMAScript dil öğeleri Unicode kategori veya blok öğeleri gibi desteklemiyor `\p` ve `\P`. Benzer şekilde, `\w` adıyla eşleşen bir sözcük karakteriyle öğesi eşdeğerdir `[a-zA-Z_0-9]` ECMAScript kullanırken sınıfı karakter ve `[\p{Ll}\p{Lu}\p{Lt}\p{Lo}\p{Nd}\p{Pc}\p{Lm}]` kurallı davranışı kullanırken. Daha fazla bilgi için bkz: [karakter sınıfları](../../../docs/standard/base-types/character-classes-in-regular-expressions.md).  
  
     Aşağıdaki örnek, kurallı arasındaki farkı gösterir ve ECMAScript desen eşleştirme. Normal bir ifade tanımlar `\b(\w+\s*)+`, boşluk karakterleri tarafından izlenen sözcükler eşleşir. İki dizeyi, Latin karakter kümesi kullanan bir ve Kiril karakter kümesi kullanan diğer giriş oluşur. Çıktı gösterildiği çağrısı <xref:System.Text.RegularExpressions.Regex.IsMatch%28System.String%2CSystem.String%2CSystem.Text.RegularExpressions.RegexOptions%29?displayProperty=nameWithType> ECMAScript eşleşen kullandığı yöntem başarısız Kiril sözcükleri eşleştirmeye kurallı eşleşen kullandığı yöntem çağrısı bu sözcükleri eşleşmiyor ise.  
  
     [!code-csharp[Conceptual.Regex.Language.Options#16](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.options/cs/ecmascript1.cs#16)]
     [!code-vb[Conceptual.Regex.Language.Options#16](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.options/vb/ecmascript1.vb#16)]  
  
-   Yakalama kendi kendine başvuran gruplandırır. Yeniden başvuru kendisine bir normal ifade yakalama sınıfla her bir yakalama yineleme güncelleştirilmesi gerekir. Aşağıdaki örnekte gösterildiği gibi bu özellik, normal ifade sağlar. `((a+)(\1) ?)+` "aa aaaa aaaaaa" giriş dizesi ECMAScript kullanırken, ancak kurallı eşleşen kullanmadığınızda eşleşecek şekilde.  
  
     [!code-csharp[Conceptual.Regex.Language.Options#21](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.options/cs/ecmascript2.cs#21)]
     [!code-vb[Conceptual.Regex.Language.Options#21](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.options/vb/ecmascript2.vb#21)]  
  
     Normal ifade aşağıdaki tabloda gösterildiği gibi tanımlanır.  
  
    |Desen|Açıklama|  
    |-------------|-----------------|  
    |(bir +)|Harf "a" bir veya birden çok kez eşleşir. Bu ikinci yakalama grubudur.|  
    |(\1)|İlk yakalama grubu tarafından yakalanan alt dize eşleşiyor. Bu, üçüncü yakalama grubudur.|  
    |?|Sıfır veya bir boşluk karakterleri eşleşmesi.|  
    |((a+)(\1)?) +|Sıfır veya bir boşluk bırakarak ilk yakalama grubuyla eşleşen bir dize tarafından izlenen bir veya daha fazla "a" karakter desen eşleştirme bir veya birden çok kez karakter. Bu ilk yakalama grubudur.|  
  
-   Yeniden başvurular sekizli çıkışları arasındaki belirsizlikleri çözünürlüğü. Aşağıdaki tabloda farklar özetlenmektedir kurallı tarafından yeniden başvuru yorumunu ve ECMAScript normal ifadeler karşı sekizli.  
  
    |Normal ifade|Kurallı davranışı|ECMAScript davranışı|  
    |------------------------|------------------------|-------------------------|  
    |`\0`0-2 sekizli basamak ile izlenen|Bir sekizli yorumlayın. Örneğin, `\044` her zaman bir sekizli değeri olarak yorumlanır ve "$" anlamına gelir.|Aynı davranışı.|  
    |`\`bir sayı 1'den 9, hiçbir ek ondalık basamak ile izlenen ve ardından,|Yeniden başvuru yorumlayın. Örneğin, `\9` Grup yakalama dokuzuncu yok olsa bile her zaman yeniden başvuru 9, anlamına gelir. Yakalama grubu yok, normal ifade ayrıştırıcısının döndürürse bir <xref:System.ArgumentException>.|Tek bir ondalık basamak yakalama grubu varsa, bu sayı için yeniden başvuru. Aksi halde değer sabit değer olarak algılar.|  
    |`\`Ek ondalık basamak ile izlenen 9 ' 1'den bir rakam ile izlenen|Basamaklı bir ondalık değer olarak algılar. Bu yakalama Grup zaten varsa, ifade bir yeniden başvuru olarak yorumlayın.<br /><br /> Aksi takdirde, baştaki sekizli basamak sekizli 377 kadar yorumlar; diğer bir deyişle, yalnızca düşük 8 bit değeri göz önünde bulundurun. Kalan basamaklar değişmez değerler yorumlayın. Örneğin, ifadede `\3000`, Grup 300 yakalama varsa, 300 yeniden başvuru yorumlanan; Grup 300 yakalama mevcut değilse, 0 ile izlenen sekizli 300 olarak yorumlar.|Yeniden başvuru yakalamaya başvurabilir ondalık bir değer mümkün olduğunca çok basamak dönüştürerek yorumlayın. Sekizlik 377 kadar başında sekizli basamak kullanarak hiç basamak dönüştürülebilir ise bir sekizli yorumlar; kalan basamaklar değişmez değerler yorumlayın.|  
  
 [Başa dön](#Top)  
  
<a name="Invariant"></a>   
## <a name="comparison-using-the-invariant-culture"></a>Sabit kültür kullanarak karşılaştırma  
 Normal ifade altyapısı duyarlı karşılaştırmalar gerçekleştirdiğinde varsayılan olarak, bu geçerli kültürü büyük/küçük harf kuralları eşdeğeri büyük ve küçük harfleri belirlemek için kullanır.  
  
 Ancak, bu özellikle parolalar, dosyaları veya URL'leri gibi sistem kaynakların adları için kullanıcı girişi karşılaştırılırken karşılaştırmaları, bazı türleri için istenmeyen bir davranıştır. Aşağıdaki örnek gibi senaryo gösterilmektedir. Kod, URL başında ile herhangi bir kaynağa erişimi engellemek için yöneliktir **FILE://**. Normal ifade kullanarak normal ifade dizesini küçük harf olarak eşleşen çalışır `$FILE://`. Geçerli sistem kültürü tr-TR (Türkçe-Türkiye) olduğunda, ancak "Yeni" büyük denk değil "i". Sonuç olarak, çağrısı <xref:System.Text.RegularExpressions.Regex.IsMatch%2A?displayProperty=nameWithType> yöntemi döndürür `false`, ve dosyaya erişimi verilir.  
  
 [!code-csharp[Conceptual.Regex.Language.Options#14](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.options/cs/culture1.cs#14)]
 [!code-vb[Conceptual.Regex.Language.Options#14](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.options/vb/culture1.vb#14)]  
  
> [!NOTE]
>  Dize karşılaştırmaları büyük küçük harfe duyarlı olmayan ve sabit kültür kullanma hakkında daha fazla bilgi için bkz: [kullanarak dizeleri için en iyi uygulamaları](../../../docs/standard/base-types/best-practices-strings.md).  
  
 Geçerli kültür duyarlı karşılaştırmaları kullanmak yerine, belirtebilirsiniz <xref:System.Text.RegularExpressions.RegexOptions.CultureInvariant?displayProperty=nameWithType> kültürel dil farklılıkları yoksay ve sabit kültür kurallarını kullanmasını seçeneği.  
  
> [!NOTE]
>  Sabit kültür kullanarak karşılaştırma kullanılabilir yalnızca sağlayarak <xref:System.Text.RegularExpressions.RegexOptions.CultureInvariant?displayProperty=nameWithType> değeri `options` parametresinin bir <xref:System.Text.RegularExpressions.Regex> sınıf oluşturucu veya statik desen eşleştirme yöntemi. Satır içi seçenek olarak kullanılabilir değil.  
  
 Aşağıdaki örnek, önceki örnekte, hariç eşdeğerdir statik <xref:System.Text.RegularExpressions.Regex.IsMatch%28System.String%2CSystem.String%2CSystem.Text.RegularExpressions.RegexOptions%29?displayProperty=nameWithType> dahil seçeneklerle yöntemi çağrıldığında <xref:System.Text.RegularExpressions.RegexOptions.CultureInvariant?displayProperty=nameWithType>. Geçerli kültür Türkçe (Türkiye) bile ayarlandığında, normal ifade "Dosyası" ve "dosyası" ve blok erişim dosya kaynağı başarıyla eşleşen mümkün altyapısıdır.  
  
 [!code-csharp[Conceptual.Regex.Language.Options#15](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.options/cs/culture1.cs#15)]
 [!code-vb[Conceptual.Regex.Language.Options#15](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.options/vb/culture1.vb#15)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Normal ifade dili - hızlı başvuru](../../../docs/standard/base-types/regular-expression-language-quick-reference.md)
