---
title: Normal Ifadeleri .NET Framework
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- pattern-matching with regular expressions, about pattern-matching
- substrings
- searching with regular expressions, about regular expressions
- pattern-matching with regular expressions
- searching with regular expressions
- parsing text with regular expressions
- regular expressions [.NET Framework], about regular expressions
- regular expressions [.NET Framework]
- .NET Framework regular expressions, about
- characters [.NET Framework], regular expressions
- parsing text with regular expressions, overview
- .NET Framework regular expressions
- strings [.NET Framework], regular expressions
ms.assetid: 521b3f6d-f869-42e1-93e5-158c54a6895d
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 89b527d4febb677512b3cdcf7cd47344d182ae26
ms.sourcegitcommit: 878ca7550b653114c3968ef8906da2b3e60e3c7a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/02/2019
ms.locfileid: "71736858"
---
# <a name="net-regular-expressions"></a>.NET normal Ifadeleri
Normal ifadeler, metin işlemeye yönelik güçlü, esnek ve verimli bir yöntem sağlar. Normal ifadelerin kapsamlı desen eşleştirme gösterimi, belirli karakter desenlerini bulmak için büyük miktarda metni hızlıca ayrıştırabilmenizi sağlar; daha önceden tanımlanmış bir Düzenle (örneğin, e-posta adresi) ile eşleştiğinden emin olmak için metni doğrulamak için metin alt dizelerini ayıklamak, düzenlemek, değiştirmek veya silmek için; ve ayıklanan dizeleri bir rapor oluşturmak için bir koleksiyona eklemek. Dizelerle ilgilenen veya büyük metin bloklarını ayrıştıran birçok uygulama için, normal ifadeler bir olmazdır aracıdır.  
  
## <a name="how-regular-expressions-work"></a>Normal Ifadeler nasıl çalışır?  
 Normal ifadelerle metin işlemenin Merkez parçası, .NET içindeki <xref:System.Text.RegularExpressions.Regex?displayProperty=nameWithType> nesnesi tarafından temsil edilen normal ifade altyapısıdır. En azından, normal ifadeler kullanılarak işleme metni, normal ifade altyapısının aşağıdaki iki bilgi öğesiyle sağlanması gerekir:  
  
- Metinde tanımlanabilmesi için normal ifade deseninin.  
  
     .NET ' te, normal ifade desenleri, Perl 5 normal ifadelerle uyumlu özel bir sözdizimi veya dil tarafından tanımlanır ve sağdan sola eşleme gibi bazı ek özellikler ekler. Daha fazla bilgi için bkz. [normal Ifade dili-hızlı başvuru](regular-expression-language-quick-reference.md).  
  
- Normal ifade deseninin Ayrıştırılacak metin.  
  
 @No__t-0 sınıfının yöntemleri aşağıdaki işlemleri gerçekleştirmenize olanak tanır:  
  
- @No__t-0 yöntemini çağırarak normal ifade deseninin giriş metninde oluşup oluşmadığını belirleme. Metni doğrulamak için <xref:System.Text.RegularExpressions.Regex.IsMatch%2A> yöntemini kullanan bir örnek için bkz. [nasıl yapılır: dizelerin geçerli e-posta biçiminde olduğunu doğrulama](how-to-verify-that-strings-are-in-valid-email-format.md).  
  
- @No__t-0 veya <xref:System.Text.RegularExpressions.Regex.Matches%2A?displayProperty=nameWithType> metodunu çağırarak, normal ifade düzeniyle eşleşen metnin bir veya bütün oluşumlarını alın. Önceki yöntem, eşleşen metin hakkında bilgi sağlayan bir <xref:System.Text.RegularExpressions.Match?displayProperty=nameWithType> nesnesi döndürür. İkincisi, ayrıştırılmış metinde bulunan her bir eşleşme için bir <xref:System.Text.RegularExpressions.Match?displayProperty=nameWithType> nesnesi içeren <xref:System.Text.RegularExpressions.MatchCollection> nesnesi döndürür.  
  
- @No__t-0 yöntemini çağırarak normal ifade düzeniyle eşleşen metni değiştirin. Tarih biçimlerini değiştirmek ve bir dizeden geçersiz karakterleri kaldırmak için <xref:System.Text.RegularExpressions.Regex.Replace%2A> yöntemini kullanan örnekler için bkz. [nasıl yapılır: bir dizeden geçersiz karakterleri](how-to-strip-invalid-characters-from-a-string.md) bırakma ve [örnek: tarih biçimlerini değiştirme](regular-expression-example-changing-date-formats.md).  
  
 Normal ifade nesne modeline genel bakış için bkz. [normal Ifade nesne modeli](the-regular-expression-object-model.md).  
  
 Normal ifade dili hakkında daha fazla bilgi için bkz. [normal Ifade dili-hızlı başvuru](regular-expression-language-quick-reference.md) veya indirme ve bu broşürden birini indirme ve yazdırma:  
  
 [Word (. docx) biçiminde hızlı başvuru](https://download.microsoft.com/download/D/2/4/D240EBF6-A9BA-4E4F-A63F-AEB6DA0B921C/Regular%20expressions%20quick%20reference.docx)  
 [PDF (. PDF) biçiminde hızlı başvuru](https://download.microsoft.com/download/D/2/4/D240EBF6-A9BA-4E4F-A63F-AEB6DA0B921C/Regular%20expressions%20quick%20reference.pdf)  
  
## <a name="regular-expression-examples"></a>Normal Ifade örnekleri  
 @No__t-0 sınıfı, daha büyük bir dizedeki değişmez dizeleri bulmak istediğinizde kullanabileceğiniz bir dizi dize araması ve değiştirme yöntemi içerir. Normal ifadeler çoğu zaman daha büyük bir dizedeki birkaç alt dizeden birini bulmak istediğinizde veya bir dizedeki desenleri tanımlamak istediğinizde, aşağıdaki örneklerde gösterildiği gibi yararlıdır.  
  
### <a name="example-1-replacing-substrings"></a>Örnek 1: alt dizeleri değiştirme  
 Bir posta listesinin, bazı durumlarda bir başlık (Mr., Mrs., Isabetsizlik veya MS.) içeren adları ve adı ve soyadı içerdiğini varsayın. Listeden zarf etiketleri oluştururken başlıkları dahil etmek istemiyorsanız, aşağıdaki örnekte gösterildiği gibi, başlıkları kaldırmak için normal bir ifade kullanabilirsiniz.  
  
 [!code-csharp[Conceptual.Regex#2](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex/cs/example1.cs#2)]
 [!code-vb[Conceptual.Regex#2](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex/vb/example1.vb#2)]  
  
 @No__t-0 normal ifade deseninin herhangi bir "Mr", "Mr.", "Mrs", "Mrs.", "Isabet", "MS veya" MS. "ile herhangi bir tekrarı eşleşir. @No__t-0 yöntemine yapılan çağrı, eşleşen dizeyi <xref:System.String.Empty?displayProperty=nameWithType> ile değiştirir; diğer bir deyişle, özgün dizeden kaldırır.  
  
### <a name="example-2-identifying-duplicated-words"></a>Örnek 2: yinelenen sözcükleri tanımlama  
 Yanlışlıkla yinelenen sözcükler, yazarları oluşturan yaygın bir hatadır. Aşağıdaki örnekte gösterildiği gibi, yinelenen kelimeleri belirlemek için normal bir ifade kullanılabilir.  
  
 [!code-csharp[Conceptual.Regex#3](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex/cs/example2.cs#3)]
 [!code-vb[Conceptual.Regex#3](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex/vb/example2.vb#3)]  
  
 @No__t-0 normal ifade deseninin şu şekilde yorumlanabilen:  
  
|||  
|-|-|  
|`\b`|Bir sözcük sınırında başlatın.|  
|(\w +?)|Bir veya daha fazla sözcük karakterini ve mümkün olduğunca az karakter eşleştirin. Birlikte, `\1` olarak başvurulabilen bir grup oluşturur.|  
|`\s`|Bir boşluk karakteriyle eşleştirin.|  
|`\1`|@No__t-0 adlı gruba eşit olan alt dizeyle eşleştirin.|  
|`\b`|Bir sözcük sınırını eşleştirin.|  
  
 @No__t-0 yöntemi, <xref:System.Text.RegularExpressions.RegexOptions.IgnoreCase?displayProperty=nameWithType> olarak ayarlanan normal ifade seçenekleriyle çağrılır. Bu nedenle, eşleştirme işlemi büyük/küçük harfe duyarlıdır ve örnek "This this" alt dizesini yineleme olarak tanımlar.  
  
 Giriş dizesinin "This?" alt dizesini içerdiğine unutmayın. Bu ". Ancak, aradaki noktalama işareti nedeniyle, yineleme olarak tanımlanmaz.  
  
### <a name="example-3-dynamically-building-a-culture-sensitive-regular-expression"></a>Örnek 3: dinamik olarak kültüre duyarlı normal Ifade oluşturma  
 Aşağıdaki örnek, tarafından sunulan esneklikle birlikte normal ifadelerin gücünü göstermektedir. NET 'in Genelleştirme özellikleri. Sistemin geçerli kültürünün para birimi değerlerinin biçimini belirleyebilmek için <xref:System.Globalization.NumberFormatInfo> nesnesini kullanır. Daha sonra, metinden para birimi değerlerini çıkaran bir normal ifadeyi dinamik olarak oluşturmak için bu bilgileri kullanır. Her eşleşme için, yalnızca sayısal dizeyi içeren alt grubu ayıklar, <xref:System.Decimal> değerine dönüştürür ve çalışan toplamı hesaplar.  
  
 [!code-csharp[Conceptual.Regex#1](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex/cs/example.cs#1)]
 [!code-vb[Conceptual.Regex#1](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex/vb/example.vb#1)]  
  
 Geçerli kültürü Ingilizce-Birleşik Devletler (en-US) olan bir bilgisayarda, örnek, normal ifadeyi dinamik olarak oluşturur `\$\s*[-+]?([0-9]{0,3}(,[0-9]{3})*(\.[0-9]+)?)`. Bu normal ifade deseninin aşağıdaki şekilde yorumlanabilen:  
  
|||  
|-|-|  
|`\$`|Giriş dizesinde dolar simgesinin (`$`) tek bir oluşumunu arayın. Normal ifade deseninin dizesi, dolar simgesinin bir normal ifade Bağlayıcısı yerine tam olarak yorumlanacağı belirtmek için bir ters eğik çizgi içerir. (@No__t-0 simgesi tek başına, normal ifade altyapısının bir dizenin sonunda eşleşme başlatmaya başlaması gerektiğini gösterir.) Geçerli kültürün para birimi sembolünün normal ifade simgesi olarak yanlış yorumlanmadığından emin olmak için örnek, karakteri atlamak için <xref:System.Text.RegularExpressions.Regex.Escape%2A?displayProperty=nameWithType> metodunu çağırır.|  
|`\s*`|Boşluk karakterinin sıfır veya daha fazla örneğini arayın.|  
|`[-+]?`|Sıfır veya bir pozitif işaret ya da eksi işareti ara veya bir oluşumunu arayın.|  
|`([0-9]{0,3}(,[0-9]{3})*(\.[0-9]+)?)`|Bu ifade etrafındaki dış parantezler, yakalama grubu veya alt ifade olarak tanımlar. Bir eşleşme bulunursa, eşleşen dizenin bu bölümüyle ilgili bilgiler <xref:System.Text.RegularExpressions.Match.Groups%2A?displayProperty=nameWithType> özelliği tarafından döndürülen <xref:System.Text.RegularExpressions.GroupCollection> nesnesindeki ikinci <xref:System.Text.RegularExpressions.Group> nesnesinden alınabilir. (Koleksiyondaki ilk öğe tüm eşleşmeyi temsil eder.)|  
|`[0-9]{0,3}`|0 ' dan 9 ' a kadar ondalık basamakların sıfır ila üç tekrarının olup olmadığına bakın.|  
|`(,[0-9]{3})*`|Bir grup ayırıcısının sıfır veya daha fazla tekrarının ardından üç ondalık basamak arayın.|  
|`\.`|Ondalık ayırıcısının tek bir oluşumunu arayın.|  
|`[0-9]+`|Bir veya daha fazla ondalık basamak bulun.|  
|`(\.[0-9]+)?`|Ondalık ayırıcının ardından en az bir ondalık basamağının sıfır veya bir oluşumunu arayın.|  
  
 Bu alt desenlerin her biri giriş dizesinde bulunursa, eşleşme başarılı olur ve eşleşme hakkında bilgi içeren <xref:System.Text.RegularExpressions.Match> nesnesi <xref:System.Text.RegularExpressions.MatchCollection> nesnesine eklenir.  
  
## <a name="related-topics"></a>İlgili Konular  
  
|Başlık|Açıklama|  
|-----------|-----------------|  
|[Normal Ifade dili-hızlı başvuru](regular-expression-language-quick-reference.md)|Normal ifadeleri tanımlamak için kullanabileceğiniz karakter, işleç ve yapılar kümesi hakkında bilgi sağlar.|  
|[Normal Ifade nesne modeli](the-regular-expression-object-model.md)|Normal ifade sınıflarının nasıl kullanılacağını gösteren bilgi ve kod örnekleri sağlar.|  
|[Normal Ifade davranışının ayrıntıları](details-of-regular-expression-behavior.md)|.NET normal ifadelerinin özellikleri ve davranışları hakkında bilgi sağlar.|  
|[Normal Ifade örnekleri](regular-expression-examples.md)|Normal ifadelerin tipik kullanımlarını gösteren kod örnekleri sağlar.|  
  
## <a name="reference"></a>Başvuru  
 <xref:System.Text.RegularExpressions?displayProperty=nameWithType>  
 <xref:System.Text.RegularExpressions.Regex?displayProperty=nameWithType>  
 [Normal Ifadeler-hızlı başvuru (Word biçiminde indir)](https://download.microsoft.com/download/D/2/4/D240EBF6-A9BA-4E4F-A63F-AEB6DA0B921C/Regular%20expressions%20quick%20reference.docx)  
 [Normal Ifadeler-hızlı başvuru (PDF biçiminde indir)](https://download.microsoft.com/download/D/2/4/D240EBF6-A9BA-4E4F-A63F-AEB6DA0B921C/Regular%20expressions%20quick%20reference.pdf)
