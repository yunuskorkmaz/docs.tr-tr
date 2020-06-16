---
title: .NET Framework Normal İfadeleri
description: Belirli karakter düzenlerini bulmak, metni doğrulamak, metin alt dizeleriyle çalışmak & ayıklanan dizeleri .NET içindeki bir koleksiyona eklemek için normal ifadeleri kullanın.
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
ms.openlocfilehash: d9505cdfb57faf586c714aa7dd537210959f50d8
ms.sourcegitcommit: 5fd4696a3e5791b2a8c449ccffda87f2cc2d4894
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/15/2020
ms.locfileid: "84768839"
---
# <a name="net-regular-expressions"></a>.NET normal ifadeleri

Normal ifadeler, metin işleme için güçlü, esnek ve verimli bir yöntem sunar. Normal ifadelerin kapsamlı kalıp eşleme gösterimi, büyük miktarlarda metni hızlıca ayrıştırabilmenizi sağlar:

- Belirli karakter düzenlerini bulun.
- Önceden tanımlanmış bir Düzenle (örneğin, e-posta adresi) ile eşleştiğinden emin olmak için metni doğrulayın.
- Metin alt dizelerini ayıklayın, düzenleyin, değiştirin veya silin.
- Bir rapor oluşturmak için bir koleksiyona ayıklanan dizeler ekleyin.

Dizeler üzerinde çalışan veya büyük metin bloklarını ayrıştıran uygulamalar için normal ifadeler vazgeçilmez bir araçtır.  
  
## <a name="how-regular-expressions-work"></a>Normal ifadeler nasıl çalışır?

 Normal ifadelerle metin işlemenin centeru parçası, .NET içindeki nesne tarafından temsil edilen normal ifade altyapısıdır <xref:System.Text.RegularExpressions.Regex?displayProperty=nameWithType> . Metinleri normal ifadeler kullanarak işlemek için, normal ifade altyapısına en azından aşağıdaki iki bilgi öğesinin sağlanması gerekir:  
  
- Metinde tanımlanacak olan normal ifade deseni.  
  
     .NET ' te, normal ifade desenleri, Perl 5 normal ifadelerle uyumlu özel bir sözdizimi veya dil tarafından tanımlanır ve sağdan sola eşleme gibi bazı ek özellikler ekler. Daha fazla bilgi için bkz. [normal Ifade dili-hızlı başvuru](regular-expression-language-quick-reference.md).  
  
- Normal ifade deseni için ayrıştırılacak olan metin.  
  
<xref:System.Text.RegularExpressions.Regex> sınıfının yöntemleri aşağıdaki işlemleri gerçekleştirmenizi sağlar:  
  
- <xref:System.Text.RegularExpressions.Regex.IsMatch%2A?displayProperty=nameWithType> metodunu çağırarak normal ifade deseninin giriş metninde oluşup oluşmayacağını belirleyin. <xref:System.Text.RegularExpressions.Regex.IsMatch%2A>Metni doğrulamak için yöntemini kullanan bir örnek için bkz. [nasıl yapılır: dizelerin geçerli e-posta biçiminde olduğunu doğrulama](how-to-verify-that-strings-are-in-valid-email-format.md).  
  
- <xref:System.Text.RegularExpressions.Regex.Match%2A?displayProperty=nameWithType> veya <xref:System.Text.RegularExpressions.Regex.Matches%2A?displayProperty=nameWithType> yöntemini çağırarak, normal ifade deseniyle eşleşen metnin bir veya tüm oluşumlarını alın. İlk yöntem, eşleşen metin hakkında bilgi sağlayan bir <xref:System.Text.RegularExpressions.Match?displayProperty=nameWithType> nesnesi döndürür. İkinci yöntem, ayrıştırılan metinde bulunan her bir eşleşme için bir <xref:System.Text.RegularExpressions.MatchCollection> nesnesi içeren bir <xref:System.Text.RegularExpressions.Match?displayProperty=nameWithType> nesnesi döndürür.  
  
- <xref:System.Text.RegularExpressions.Regex.Replace%2A?displayProperty=nameWithType> yöntemini çağırarak normal ifade deseniyle eşleşen metni değiştirin. <xref:System.Text.RegularExpressions.Regex.Replace%2A>Tarih biçimlerini değiştirmek ve bir dizeden geçersiz karakterleri kaldırmak için yöntemini kullanan örnekler için bkz. [nasıl yapılır: bir dizeden geçersiz karakterleri](how-to-strip-invalid-characters-from-a-string.md) bırakma ve [örnek: tarih biçimlerini değiştirme](regular-expression-example-changing-date-formats.md).  
  
Normal ifade nesne modeline genel bakış için bkz. [normal Ifade nesne modeli](the-regular-expression-object-model.md).  
  
Normal ifade dili hakkında daha fazla bilgi için bkz. [normal Ifade dili-hızlı başvuru](regular-expression-language-quick-reference.md) veya indirme ve bu broşürden birini indirme ve yazdırma:  
  
- [Word (. docx) biçiminde hızlı başvuru](https://download.microsoft.com/download/D/2/4/D240EBF6-A9BA-4E4F-A63F-AEB6DA0B921C/Regular%20expressions%20quick%20reference.docx)  
- [PDF (. PDF) biçiminde hızlı başvuru](https://download.microsoft.com/download/D/2/4/D240EBF6-A9BA-4E4F-A63F-AEB6DA0B921C/Regular%20expressions%20quick%20reference.pdf)  
  
## <a name="regular-expression-examples"></a>Normal ifade örnekleri

<xref:System.String> sınıfı, daha büyük bir dizede sabit değer dizelerini bulmak istediğiniz zaman kullanabileceğiniz dize arama ve yerleştirme yöntemlerini içerir. Normal ifadeler en çok, büyük bir dizedeki alt dizelerin birini konumlandırmak istediğinizde veya aşağıdaki örnekte gösterildiği gibi bir dizede desenleri tanımlamak istediğinizde kullanışlıdır.

> [!TIP]
> <xref:System.Web.RegularExpressions>Ad alanı, HTML, XML ve ASP.net belgelerinden dizeleri ayrıştırmak için önceden tanımlanmış normal ifade desenleri uygulayan bir dizi normal ifade nesnesi içerir. Örneğin, <xref:System.Web.RegularExpressions.TagRegex> sınıfı bir dizedeki başlangıç etiketlerini tanımlar ve <xref:System.Web.RegularExpressions.CommentRegex> sınıf ASP.net açıklamalarını bir dizede tanımlar.

### <a name="example-1-replace-substrings"></a>Örnek 1: alt dizeleri değiştir  

 Bir posta listesinin, ada ve soyada ek olarak bazen bir ünvan (Mr., Mrs., Miss veya Ms.) içerdiğini varsayın. Eğer listeden zarf etiketleri oluştururken ünvanları dahil etmek istemiyorsanız, aşağıdaki örnekte gösterildiği gibi ünvanları kaldırmak için bir normal ifade kullanabilirsiniz.  
  
 [!code-csharp[Conceptual.Regex#2](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex/cs/example1.cs#2)]
 [!code-vb[Conceptual.Regex#2](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex/vb/example1.vb#2)]  
  
 Normal ifade deseninin `(Mr\.? |Mrs\.? |Miss |Ms\.? )` her türlü "Mr", "Mr.", "Mrs", "Mrs.", "Isabetsizlik", "MS veya" MS. "gibi herhangi bir oluşumu eşleşir. <xref:System.Text.RegularExpressions.Regex.Replace%2A?displayProperty=nameWithType> yöntemine yapılan çağrı, eşleşen dizeyi <xref:System.String.Empty?displayProperty=nameWithType> ile değiştirir; yani başka bir deyişle bu dizeyi orijinal dizeden kaldırır.  
  
### <a name="example-2-identify-duplicated-words"></a>Örnek 2: yinelenen sözcükleri tanımla  

 Kelimeleri yanlışlıkla yinelemek yazarların yaptığı yaygın bir hatadır. Bir normal ifade, aşağıdaki örnekte gösterdiği gibi yinelenen kelimeleri tanımlamak için kullanılabilir.  
  
 [!code-csharp[Conceptual.Regex#3](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex/cs/example2.cs#3)]
 [!code-vb[Conceptual.Regex#3](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex/vb/example2.vb#3)]  
  
 Normal ifade deseninin `\b(\w+?)\s\1\b` Şu şekilde yorumlanması için:  
  
> [!div class="mx-tdCol2BreakAll"]
> |Desen|Yorum|  
> |-|-|
> |`\b`|Bir sözcük sınırında başla.|  
> |`(\w+?)`|Bir veya daha fazla sözcük karakterini ve mümkün olduğunca az karakter eşleştirin. Birlikte, olarak başvurulabilen bir grup oluşturur `\1` .|  
> |`\s`|Bir boşluk karakteri ile eşleştirin.|  
> |`\1`|Adlı gruba eşit olan alt dizeyle eşleştirin `\1` .|  
> |`\b`|Bir sözcük sınırıyla eşleş.|  
  
 <xref:System.Text.RegularExpressions.Regex.Matches%2A?displayProperty=nameWithType> yöntemi, normal ifade ayarları <xref:System.Text.RegularExpressions.RegexOptions.IgnoreCase?displayProperty=nameWithType> şeklinde ayarlanmış olarak çağırılır. Bu nedenle eşleştirme işlemi büyük/küçük harfe duyarsızdır, ve örnek "This this" alt dizesini bir yineleme olarak tanımlar.  
  
 Giriş dizesi "This?" alt dizesini içerir. unutmayın. Ancak, aradaki noktalama işareti nedeniyle bu, bir yineleme olarak tanımlanmaz.  
  
### <a name="example-3-dynamically-build-a-culture-sensitive-regular-expression"></a>Örnek 3: dinamik olarak kültüre duyarlı normal ifade derleme  

 Aşağıdaki örnek, tarafından sunulan esneklikle birlikte normal ifadelerin gücünü göstermektedir. NET 'in Genelleştirme özellikleri. Sistemin geçerli kültüründeki para birimi değerlerinin biçimini belirlemek için <xref:System.Globalization.NumberFormatInfo> nesnesini kullanır. Ardından metinden para birimi değerleri ayıklayan bir normal ifadeyi dinamik olarak oluşturmak için bu bilgiyi kullanır. Her bir eşleşme için, yalnızca sayısal dizeyi içeren alt grubu ayıklar, bir <xref:System.Decimal> değerine dönüştürür ve toplamı hesaplar.  
  
 [!code-csharp[Conceptual.Regex#1](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex/cs/example.cs#1)]
 [!code-vb[Conceptual.Regex#1](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex/vb/example.vb#1)]  
  
 Geçerli kültürü Ingilizce-Birleşik Devletler (en-US) olan bir bilgisayarda, örnek dinamik ifadeyi dinamik olarak oluşturur `\$\s*[-+]?([0-9]{0,3}(,[0-9]{3})*(\.[0-9]+)?)` . Bu normal ifade deseni aşağıdaki şekilde yorumlanabilir:  

> [!div class="mx-tdCol2BreakAll"]
> |Desen|Yorum|  
> |-|-|  
> |`\$`|Giriş dizesinde dolar simgesinin () tek bir oluşumunu arayın `$` . Normal ifade deseni dizesi, dolar simgesinin bir normal ifade yer işareti yerine sabit değer olarak yorumlanmasını sağlamak için bir ters eğik çizgi içerir. ( `$` Tek başına simge, normal ifade altyapısının bir dizenin sonunda eşleşme başlatmaya başlaması gerektiğini gösterir.) Geçerli kültürün para birimi simgesinin bir normal ifade simgesi olarak yanlış yorumlanmadığından emin olmak için örnek, <xref:System.Text.RegularExpressions.Regex.Escape%2A?displayProperty=nameWithType> karakteri kaçış yöntemini çağırır.|  
> |`\s*`|Bir boşluk karakterin sıfır veya daha fazla oluşumunu arayın.|  
> |`[-+]?`|Bir artı işareti veya eksi işaretinin sıfır veya bir oluşumunu arayın.|  
> |`([0-9]{0,3}(,[0-9]{3})*(\.[0-9]+)?)`|Bu ifadenin dışındaki parantezler onu bir yakalama grubu veya alt ifade olarak tanımlar. Eğer bir eşleşme bulunursa eşleşen dizenin bu bölümüyle ilgili bilgi, <xref:System.Text.RegularExpressions.Group> özelliği tarafından döndürülen <xref:System.Text.RegularExpressions.GroupCollection> nesnesindeki ikinci <xref:System.Text.RegularExpressions.Match.Groups%2A?displayProperty=nameWithType> nesnesinden alınabilir. (Koleksiyondaki ilk öğe tüm eşleşmeyi temsil eder.)|  
> |`[0-9]{0,3}`|0 ile 9 arasındaki ondalık basamakların sıfırdan üç taneye kadar oluşumunu arayın.|  
> |`(,[0-9]{3})*`|Ardından üç ondalık basamak gelen bir grup ayracının sıfır veya daha fazla oluşumunu arayın.|  
> |`\.`|Ondalık ayracının tek bir oluşumunu arayın.|  
> |`[0-9]+`|Bir veya daha fazla ondalık basamak arayın.|  
> |`(\.[0-9]+)?`|Ardından en az bir ondalık basamak gelen ondalık ayracın sıfır veya bir oluşumunu arayın.|  
  
 Bu alt desenlerin her biri giriş dizesinde bulunuyorsa, eşleşme başarılı olur ve <xref:System.Text.RegularExpressions.Match> nesnesine eşleşme hakkında bilgi içeren bir <xref:System.Text.RegularExpressions.MatchCollection> nesnesi eklenir.  
  
## <a name="related-topics"></a>İlgili konular  
  
|Başlık|Açıklama|  
|-----------|-----------------|  
|[Normal İfade Dili - Hızlı Başvuru](regular-expression-language-quick-reference.md)|Normal ifadeler tanımlamak için kullanabileceğiniz karakterler, operatörler ve yapılar kümesi hakkında bilgi sağlar.|  
|[Normal İfade Nesnesi Modeli](the-regular-expression-object-model.md)|Normal ifade sınıflarının nasıl kullanılacağını gösteren bilgileri ve kod örneklerini sağlar.|  
|[Normal İfade Davranışının Ayrıntıları](details-of-regular-expression-behavior.md)|.NET normal ifadelerinin özellikleri ve davranışları hakkında bilgi sağlar.|
|[Visual Studio 'da normal ifadeler kullanma](/visualstudio/ide/using-regular-expressions-in-visual-studio)||
  
## <a name="reference"></a>Başvuru  

- <xref:System.Text.RegularExpressions?displayProperty=nameWithType>  
- <xref:System.Text.RegularExpressions.Regex?displayProperty=nameWithType>  
- [Normal Ifadeler-hızlı başvuru (Word biçiminde indir)](https://download.microsoft.com/download/D/2/4/D240EBF6-A9BA-4E4F-A63F-AEB6DA0B921C/Regular%20expressions%20quick%20reference.docx)  
- [Normal Ifadeler-hızlı başvuru (PDF biçiminde indir)](https://download.microsoft.com/download/D/2/4/D240EBF6-A9BA-4E4F-A63F-AEB6DA0B921C/Regular%20expressions%20quick%20reference.pdf)
