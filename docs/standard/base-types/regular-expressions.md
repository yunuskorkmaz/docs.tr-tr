---
title: ".NET Framework Normal İfadeleri"
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
caps.latest.revision: "24"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: b9922576e4ef942e896f365c44cebec717abe3b4
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/23/2017
---
# <a name="net-regular-expressions"></a>.NET normal ifadeler
Normal ifadeler, metin işleme için güçlü, esnek ve verimli bir yöntem sunar. Normal ifadelerin kapsamlı desen eşleştirme gösterimi; belirli karakter desenlerini bulmak için büyük miktarlarda metini hızlıca ayrıştırmanızı; önceden tanımlı bir desenle (örneğin bir e-posta adresi) eşleştiğinden emin olmak için metni doğrulamanızı; metin alt dizeleri ayıklamanızı, düzenlemenizi, değiştirmenizi veya silmenizi; ve bir rapor oluşturmak için ayıklanan dizeleri bir koleksiyona eklemenizi sağlar. Dizeler üzerinde çalışan veya büyük metin bloklarını ayrıştıran uygulamalar için normal ifadeler vazgeçilmez bir araçtır.  
  
## <a name="how-regular-expressions-work"></a>Normal İfadeler Nasıl Çalışır?  
 Normal ifadelerle işleme metnin bir merkez tarafından temsil edilen normal ifade altyapısı olan <xref:System.Text.RegularExpressions.Regex?displayProperty=nameWithType> .NET nesne. Metinleri normal ifadeler kullanarak işlemek için, normal ifade altyapısına en azından aşağıdaki iki bilgi öğesinin sağlanması gerekir:  
  
-   Metinde tanımlanacak olan normal ifade deseni.  
  
     .NET, normal ifade desenleri özel sözdizimi veya Perl 5 normal ifadeler ile uyumludur ve sağdan sola eşleşen gibi diğer bazı özellikler ekler, dil tarafından tanımlanır. Daha fazla bilgi için bkz: [normal ifade dili - hızlı başvuru](../../../docs/standard/base-types/regular-expression-language-quick-reference.md).  
  
-   Normal ifade deseni için ayrıştırılacak olan metin.  
  
 <xref:System.Text.RegularExpressions.Regex> sınıfının yöntemleri aşağıdaki işlemleri gerçekleştirmenizi sağlar:  
  
-   <xref:System.Text.RegularExpressions.Regex.IsMatch%2A?displayProperty=nameWithType> metodunu çağırarak normal ifade deseninin giriş metninde oluşup oluşmayacağını belirleyin. Kullanan bir örnek <xref:System.Text.RegularExpressions.Regex.IsMatch%2A> metin, doğrulama yöntemi bkz [nasıl yapılır: dizelerin geçerli e-posta biçiminde olduğunu doğrulama](../../../docs/standard/base-types/how-to-verify-that-strings-are-in-valid-email-format.md).  
  
-   <xref:System.Text.RegularExpressions.Regex.Match%2A?displayProperty=nameWithType> veya <xref:System.Text.RegularExpressions.Regex.Matches%2A?displayProperty=nameWithType> yöntemini çağırarak, normal ifade deseniyle eşleşen metnin bir veya tüm oluşumlarını alın. İlk yöntem, eşleşen metin hakkında bilgi sağlayan bir <xref:System.Text.RegularExpressions.Match?displayProperty=nameWithType> nesnesi döndürür. İkinci yöntem, ayrıştırılan metinde bulunan her bir eşleşme için bir <xref:System.Text.RegularExpressions.MatchCollection> nesnesi içeren bir <xref:System.Text.RegularExpressions.Match?displayProperty=nameWithType> nesnesi döndürür.  
  
-   <xref:System.Text.RegularExpressions.Regex.Replace%2A?displayProperty=nameWithType> yöntemini çağırarak normal ifade deseniyle eşleşen metni değiştirin. Kullanma örnekleri için <xref:System.Text.RegularExpressions.Regex.Replace%2A> yöntemi bir dizeden geçersiz karakterleri kaldırın ve tarih biçimleri değiştirmek için bkz: [nasıl yapılır: Şerit bir dizeden geçersiz karakterleri](../../../docs/standard/base-types/how-to-strip-invalid-characters-from-a-string.md) ve [örnek: tarih biçimlerini değiştirme](../../../docs/standard/base-types/regular-expression-example-changing-date-formats.md).  
  
 Normal ifade nesnesi modeli genel bakış için bkz: [normal ifade nesnesi modeli](../../../docs/standard/base-types/the-regular-expression-object-model.md).  
  
 Normal ifade dili hakkında daha fazla bilgi için bkz: [normal ifade dili - hızlı başvuru](../../../docs/standard/base-types/regular-expression-language-quick-reference.md) veya indirin ve bu broşürler biri yazdırma:  
  
 [Word (.docx) biçiminde hızlı başvuru](http://download.microsoft.com/download/D/2/4/D240EBF6-A9BA-4E4F-A63F-AEB6DA0B921C/Regular%20expressions%20quick%20reference.docx)  
 [PDF (.pdf) biçiminde hızlı başvuru](http://download.microsoft.com/download/D/2/4/D240EBF6-A9BA-4E4F-A63F-AEB6DA0B921C/Regular%20expressions%20quick%20reference.pdf)  
  
## <a name="regular-expression-examples"></a>Normal İfade Örnekleri  
 <xref:System.String> sınıfı, daha büyük bir dizede sabit değer dizelerini bulmak istediğiniz zaman kullanabileceğiniz dize arama ve yerleştirme yöntemlerini içerir. Normal ifadeler en çok, büyük bir dizedeki alt dizelerin birini konumlandırmak istediğinizde veya aşağıdaki örnekte gösterildiği gibi bir dizede desenleri tanımlamak istediğinizde kullanışlıdır.  
  
### <a name="example-1-replacing-substrings"></a>Örnek 1: Alt Dizeleri Değiştirme  
 Bir posta listesinin, ada ve soyada ek olarak bazen bir ünvan (Mr., Mrs., Miss veya Ms.) içerdiğini varsayın. Eğer listeden zarf etiketleri oluştururken ünvanları dahil etmek istemiyorsanız, aşağıdaki örnekte gösterildiği gibi ünvanları kaldırmak için bir normal ifade kullanabilirsiniz.  
  
 [!code-csharp[Conceptual.Regex#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex/cs/example1.cs#2)]
 [!code-vb[Conceptual.Regex#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex/vb/example1.vb#2)]  
  
 Normal ifade deseni`(Mr\.? |Mrs\.? |Miss |Ms\.? )` "Mr", "Bay", "Mrs", "Merve", "İsabetsizliği", "Ms ya da"Ms.". herhangi bir örneğini eşleşir <xref:System.Text.RegularExpressions.Regex.Replace%2A?displayProperty=nameWithType> yöntemine yapılan çağrı, eşleşen dizeyi <xref:System.String.Empty?displayProperty=nameWithType> ile değiştirir; yani başka bir deyişle bu dizeyi orijinal dizeden kaldırır.  
  
### <a name="example-2-identifying-duplicated-words"></a>Örnek 2: Yinelenen Sözcükleri Tanımlama  
 Kelimeleri yanlışlıkla yinelemek yazarların yaptığı yaygın bir hatadır. Bir normal ifade, aşağıdaki örnekte gösterdiği gibi yinelenen kelimeleri tanımlamak için kullanılabilir.  
  
 [!code-csharp[Conceptual.Regex#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex/cs/example2.cs#3)]
 [!code-vb[Conceptual.Regex#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex/vb/example2.vb#3)]  
  
 Normal ifade deseni `\b(\w+?)\s\1\b` şu şekilde yorumlanabilir:  
  
|||  
|-|-|  
|`\b`|Bir sözcük sınırında başla.|  
|(\w+?)|Bir veya daha fazla sözcük karakterleri, mümkün olduğunca az karakter ancak aynı. Birlikte, bunlar için olarak adlandırılabilir bir grup form `\1`.|  
|`\s`|Bir boşluk karakteri ile eşleştirin.|  
|`\1`|Adlı gruba eşittir alt dizeyi eşleştirmek `\1`.|  
|`\b`|Bir sözcük sınırıyla eşleş.|  
  
 <xref:System.Text.RegularExpressions.Regex.Matches%2A?displayProperty=nameWithType> yöntemi, normal ifade ayarları <xref:System.Text.RegularExpressions.RegexOptions.IgnoreCase?displayProperty=nameWithType> şeklinde ayarlanmış olarak çağırılır. Bu nedenle eşleştirme işlemi büyük/küçük harfe duyarsızdır, ve örnek "This this" alt dizesini bir yineleme olarak tanımlar.  
  
 Giriş dizesinin "this?this" alt dizesini içerdiğini unutmayın. Ancak, aradaki noktalama işareti nedeniyle bu, bir yineleme olarak tanımlanmaz.  
  
### <a name="example-3-dynamically-building-a-culture-sensitive-regular-expression"></a>Örnek 3: Kültüre Duyarlı Normal Bir İfadeyi Dinamik Olarak Oluşturma  
 Aşağıdaki örnek tarafından sunulan esneklik birlikte normal ifadeler gücünü gösterilmektedir. NET Genelleştirme özellikleri. Sistemin geçerli kültüründeki para birimi değerlerinin biçimini belirlemek için <xref:System.Globalization.NumberFormatInfo> nesnesini kullanır. Ardından metinden para birimi değerleri ayıklayan bir normal ifadeyi dinamik olarak oluşturmak için bu bilgiyi kullanır. Her bir eşleşme için, yalnızca sayısal dizeyi içeren alt grubu ayıklar, bir <xref:System.Decimal> değerine dönüştürür ve toplamı hesaplar.  
  
 [!code-csharp[Conceptual.Regex#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex/cs/example.cs#1)]
 [!code-vb[Conceptual.Regex#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex/vb/example.vb#1)]  
  
 Geçerli kültür İngilizce - bir bilgisayarda Amerika Birleşik Devletleri (en-US) örnek dinamik olarak normal ifade derlemeler `\$\s*[-+]?([0-9]{0,3}(,[0-9]{3})*(\.[0-9]+)?)`. Bu normal ifade deseni aşağıdaki şekilde yorumlanabilir:  
  
|||  
|-|-|  
|`\$`|Giriş dizesinde dolar simgesinin ($) tek bir oluşumunu arayın. Normal ifade deseni dizesi, dolar simgesinin bir normal ifade yer işareti yerine sabit değer olarak yorumlanmasını sağlamak için bir ters eğik çizgi içerir. (Tek başına $ simgesi, normal ifade alt yapısının eşleştirmeye bir dizenin sonunda başlamayı denemesi gerektiğini gösterir.) Geçerli kültürün para birimi simgesinin bir normal ifade simgesi olarak yanlış yorumlanmamasını sağlamak amacıyla örnek, karakteri kaçırmak için <xref:System.Text.RegularExpressions.Regex.Escape%2A> yöntemini kullanır.|  
|`\s*`|Bir boşluk karakterin sıfır veya daha fazla oluşumunu arayın.|  
|`[-+]?`|Bir artı işareti veya eksi işaretinin sıfır veya bir oluşumunu arayın.|  
|`([0-9]{0,3}(,[0-9]{3})*(\.[0-9]+)?)`|Bu ifadenin dışındaki parantezler onu bir yakalama grubu veya alt ifade olarak tanımlar. Eğer bir eşleşme bulunursa eşleşen dizenin bu bölümüyle ilgili bilgi, <xref:System.Text.RegularExpressions.Group> özelliği tarafından döndürülen <xref:System.Text.RegularExpressions.GroupCollection> nesnesindeki ikinci <xref:System.Text.RegularExpressions.Match.Groups%2A?displayProperty=nameWithType> nesnesinden alınabilir. (Koleksiyondaki ilk öğe tüm eşleşmeyi temsil eder.)|  
|`[0-9]{0,3}`|0 ile 9 arasındaki ondalık basamakların sıfırdan üç taneye kadar oluşumunu arayın.|  
|`(,[0-9]{3})*`|Ardından üç ondalık basamak gelen bir grup ayracının sıfır veya daha fazla oluşumunu arayın.|  
|`\.`|Ondalık ayracının tek bir oluşumunu arayın.|  
|`[0-9]+`|Bir veya daha fazla ondalık basamak arayın.|  
|`(\.[0-9]+)?`|Ardından en az bir ondalık basamak gelen ondalık ayracın sıfır veya bir oluşumunu arayın.|  
  
 Bu alt desenlerin her biri giriş dizesinde bulunuyorsa, eşleşme başarılı olur ve <xref:System.Text.RegularExpressions.Match> nesnesine eşleşme hakkında bilgi içeren bir <xref:System.Text.RegularExpressions.MatchCollection> nesnesi eklenir.  
  
## <a name="related-topics"></a>İlgili Konular  
  
|Başlık|Açıklama|  
|-----------|-----------------|  
|[Normal İfade Dili - Hızlı Başvuru](../../../docs/standard/base-types/regular-expression-language-quick-reference.md)|Normal ifadeler tanımlamak için kullanabileceğiniz karakterler, operatörler ve yapılar kümesi hakkında bilgi sağlar.|  
|[Normal İfade Nesne Modeli](../../../docs/standard/base-types/the-regular-expression-object-model.md)|Normal ifade sınıflarının nasıl kullanılacağını gösteren bilgileri ve kod örneklerini sağlar.|  
|[Normal İfade Davranışının Ayrıntıları](../../../docs/standard/base-types/details-of-regular-expression-behavior.md)|.NET normal ifadeler davranışını ve özellikleri hakkında bilgi sağlar.|  
|[Normal İfade Örnekleri](../../../docs/standard/base-types/regular-expression-examples.md)|Normal ifadelerin genel kullanımlarını gösteren kod örnekleri sağlar.|  
  
## <a name="reference"></a>Başvuru  
 <xref:System.Text.RegularExpressions?displayProperty=nameWithType>  
 <xref:System.Text.RegularExpressions.Regex?displayProperty=nameWithType>  
 [Normal ifadeler - hızlı başvuru (Word biçiminde de indirilebilir)](http://download.microsoft.com/download/D/2/4/D240EBF6-A9BA-4E4F-A63F-AEB6DA0B921C/Regular%20expressions%20quick%20reference.docx)  
 [Normal ifadeler - hızlı başvuru (PDF biçimli indirme)](http://download.microsoft.com/download/D/2/4/D240EBF6-A9BA-4E4F-A63F-AEB6DA0B921C/Regular%20expressions%20quick%20reference.pdf)
