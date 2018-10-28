---
title: . NET'te biçimlendirme türleri
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data formatting [.NET Framework]
- dates [.NET Framework], formatting
- date formatting [.NET Framework]
- number formatting [.NET Framework]
- ToString method
- custom cultural settings [.NET Framework]
- numbers [.NET Framework], formatting
- formatting strings [.NET Framework]
- time [.NET Framework], formatting
- currency [.NET Framework], formatting
- types [.NET Framework], formatting
- format specifiers [.NET Framework]
- times [.NET Framework], formatting
- culture [.NET Framework], formatting
- formatting [.NET Framework], types supported
- base types [.NET Framework], formatting
- custom formatting [.NET Framework]
- strings [.NET Framework], formatting
ms.assetid: 0d1364da-5b30-4d42-8e6b-03378343343f
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b0185d79d8663d552378248f0e021a7fee8f0522
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/27/2018
ms.locfileid: "50189725"
---
# <a name="formatting-types-in-net"></a>. NET'te biçimlendirme türleri
<a name="Introduction"></a> Biçimlendirme, böylece ortaya çıkan dize kullanıcılara görüntülenebilir ya da orijinal veri türünü geri yüklemek için seri durumdan, sınıf, yapı ya da numaralandırma değerinin bir örneğinin kendi dize sunumuna dönüştürme işlemidir. Bu dönüştürme, bir dizi güçlük çıkarabilir:  
  
-   Değerlerin dahili olarak depolanma biçimi, kullanıcıların bunları görüntülemek istediğiniz şekilde yansıtmayabilir. Örneğin, bir telefon numarası, kullanıcı dostu olmayan 8009999999 formunda saklanabilir. Bunun yerine 800-999-9999 görüntülenmelidir. Bkz: [özel biçim dizeleri](#customStrings) bir sayıyı bu şekilde biçimlendiren bir örnek için bölüm.  
  
-   Bazen bir nesnenin dize gösterimine dönüştürme sezgisel değildir. Örneğin, bunu bir sıcaklık nesnesinin ya da bir kişi nesnesinin dize gösterimini nasıl görünmelidir açık değildir. Bir sıcaklık nesnesini birçok şekilde biçimlendiren bir örnek için bkz. [standart biçim dizeleri](#standardStrings) bölümü.  
  
-   Değerleri genellikle kültüre duyarlı biçimlendirme gerektirir. Örneğin, sayıları parasal değerleri yansıtmak için kullanan bir uygulamada, sayısal dizeler geçerli kültürün para birimi sembolünü, Grup ayırıcısını içermelidir (, çoğu kültürde olduğu binlik ayırıcı) ve ondalık sembolünü. Bir örnek için bkz. [biçim sağlayıcıları ve Iformatprovider arabirimi ile kültüre duyarlı biçimlendirme](#FormatProviders) bölümü.  
  
-   Bir uygulama aynı değeri farklı şekillerde göstermek durumunda kalabilir. Örneğin, bir uygulama bir numaralandırma üyesine adını bir dize gösterimini görüntüleyerek ya da bunu temel değerini görüntüleyerek temsil edebilir. Üye biçimlendiren bir örnek için <xref:System.DayOfWeek> numaralandırması farklı şekillerde bkz [standart biçim dizeleri](#standardStrings) bölümü.  
  
> [!NOTE]
>  Biçimlendirme bir türün değerini bir dize temsiline dönüştürür. Ayrıştırma biçimlendirmenin tersidir. Bir ayrıştırma işlemi kendi dize temsilinde bir veri türü örneği oluşturur. Dizeleri diğer veri türlerine dönüştürme hakkında daha fazla bilgi için bkz: [dizeleri ayrıştırma](../../../docs/standard/base-types/parsing-strings.md).  
  
 .NET, geliştiricilerin bu gereksinimleri karşılamasını sağlayan zengin biçimlendirme desteği sağlar.  
  
 Bu genel bakış aşağıdaki bölümleri içerir:  
  
-   [. NET'te biçimlendirme](#NetFormatting)  
  
-   [Biçimlendirme ToString yöntemini kullanarak varsayılan](#DefaultToString)  
  
-   [ToString yöntemini geçersiz kılma](#OverrideToString)  
  
-   [ToString yöntemi ve biçim dizeleri](#FormatStrings)  
  
    -   [Standart biçim dizeleri](#standardStrings)  
  
    -   [Özel biçim dizeleri](#customStrings)  
  
    -   [Biçim dizeleri ve .NET sınıfı kitaplık türleri](#stringRef)  
  
-   [Biçim sağlayıcıları ve Iformatprovider arabirimi ile kültüre duyarlı biçimlendirme](#FormatProviders)  
  
    -   [Sayısal değerleri kültüre duyarlı biçimlendirme](#numericCulture)  
  
    -   [Tarih ve saat değerlerini kültüre duyarlı biçimlendirme](#dateCulture)  
  
-   [Iformattable arabirimi](#IFormattable)  
  
-   [Bileşik Biçimlendirme](#CompositeFormatting)  
  
-   [Icustomformatter ile özel biçimlendirme](#Custom)  
  
-   [İlgili Konular](#RelatedTopics)  
  
-   [Başvuru](#Reference)  
  
<a name="NetFormatting"></a>   
## <a name="formatting-in-net"></a>. NET'te biçimlendirme  
 Varsayılan uygulamasıdır biçimlendirme temel mekanizması <xref:System.Object.ToString%2A?displayProperty=nameWithType> tartışılan yöntemi [ToString yöntemini kullanarak biçimlendirme varsayılan](#DefaultToString) bu konunun ilerleyen bölümlerinde. Ancak, .NET, değiştirmek ve kendi varsayılan biçimlendirme desteğini genişletmek için birçok yol sağlar. Bunlar aşağıdakileri içerir:  
  
-   Geçersiz kılma <xref:System.Object.ToString%2A?displayProperty=nameWithType> bir nesnenin değerinin özel bir dize temsilini tanımlamak için yöntemi. Daha fazla bilgi için [ToString yöntemini geçersiz kılma](#OverrideToString) bu konunun ilerleyen bölümlerinde.  
  
-   Birden çok nesnenin değerinin dize gösterimine olanak tanıyan biçim belirticileri tanımlama. Örneğin, aşağıdaki ifade, "X" biçim belirticisi bir tamsayı bir onaltılık değerinin dize gösterimine dönüştürür.  
  
     [!code-csharp[Conceptual.Formatting.Overview#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/specifier1.cs#3)]
     [!code-vb[Conceptual.Formatting.Overview#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/specifier1.vb#3)]  
  
     Biçim tanımlayıcıları hakkında daha fazla bilgi için bkz. [ToString yöntemi ve biçim dizeleri](#FormatStrings) bölümü.  
  
-   Belirli bir kültürün biçimlendirme kurallarını yararlanmak için biçim sağlayıcılar kullanma. Örneğin, aşağıdaki deyim, en-US kültürünün biçimlendirme kurallarını kullanarak bir para birimi değeri görüntüler.  
  
     [!code-csharp[Conceptual.Formatting.Overview#10](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/specifier1.cs#10)]
     [!code-vb[Conceptual.Formatting.Overview#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/specifier1.vb#10)]  
  
     Biçim sağlayıcılarla biçimlendirme hakkında daha fazla bilgi için bkz. [biçim sağlayıcıları ve Iformatprovider arabirimi](#FormatProviders) bölümü.  
  
-   Uygulama <xref:System.IFormattable> içeren iki dize dönüşümü desteklemek için arabirimi <xref:System.Convert> sınıfı ve bileşik biçimlendirme. Daha fazla bilgi için [Iformattable arabirimi](#IFormattable) bölümü.  
  
-   Daha büyük bir dizedeki bir değerin dize gösterimini katıştırmak için bileşik biçimlendirme kullanma. Daha fazla bilgi için [bileşik biçimlendirme](#CompositeFormatting) bölümü.  
  
-   Uygulama <xref:System.ICustomFormatter> ve <xref:System.IFormatProvider> bir özel biçimlendirme çözümü sağlamak için. Daha fazla bilgi için [Icustomformatter ile özel biçimlendirme](#Custom) bölümü.  
  
 Aşağıdaki bölümlerde, bir nesneyi dize gösterimine dönüştürmek için bu yöntemleri incelemektedir.  
  
 [Başa dön](#Introduction)  
  
<a name="DefaultToString"></a>   
## <a name="default-formatting-using-the-tostring-method"></a>ToString Yöntemini Kullanarak Varsayılan Biçimlendirme  
 Türetilen her tür <xref:System.Object?displayProperty=nameWithType> otomatik olarak bir parametresiz devralan `ToString` yöntemi varsayılan olarak türün adını döndürür. Aşağıdaki örnekte varsayılan `ToString` yöntemi. Adlı bir sınıf tanımlar `Automobile` uygulaması olmayan. Sınıf oluşturulduğunda ve kendi `ToString` yöntemi çağrıldığında, tür adını görüntüler. Unutmayın `ToString` yöntemi örnekte açıkça çağrılmaz. <xref:System.Console.WriteLine%28System.Object%29?displayProperty=nameWithType> Örtük olarak çağırır `ToString` nesnesinin yöntemi için bir bağımsız değişkeni olarak geçirilir.  
  
 [!code-csharp[Conceptual.Formatting.Overview#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/default1.cs#1)]
 [!code-vb[Conceptual.Formatting.Overview#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/default1.vb#1)]  
  
> [!WARNING]
>  İle başlayan [!INCLUDE[win81](../../../includes/win81-md.md)], [!INCLUDE[wrt](../../../includes/wrt-md.md)] içeren bir <xref:Windows.Foundation.IStringable> tek bir yöntemi ile arabirim [Istringable](xref:Windows.Foundation.IStringable.ToString%2A), varsayılan biçimlendirme desteği sağlar. Ancak Yönetilen türlerin uygulamamasını öneririz `IStringable` arabirimi. Daha fazla bilgi için " [!INCLUDE[wrt](../../../includes/wrt-md.md)] ve `IStringable` arabirimi" bölümünde <xref:System.Object.ToString%2A?displayProperty=nameWithType> başvuru sayfası.  
  
 Arabirimler dışında tüm türler türetildiği <xref:System.Object>, bu işlev özel sınıflarınıza ya da yapıları için otomatik olarak sağlanır. Bununla birlikte, varsayılan olarak sağlanan işlev `ToString` yöntemi sınırlıdır: türü tanımlamasına rağmen türün bir örneğini hakkındaki tüm bilgileri sağlamak başarısız. Bu nesne hakkında bilgi sağlayan nesnenin dize gösterimini sağlamak için geçersiz kılmanız gerekir `ToString` yöntemi.  
  
> [!NOTE]
>  Yapıları devralmanız <xref:System.ValueType>, hangi sırayla türetilmiş olan <xref:System.Object>. Ancak <xref:System.ValueType> geçersiz kılmalar <xref:System.Object.ToString%2A?displayProperty=nameWithType>, uygulaması aynıdır.  
  
 [Başa dön](#Introduction)  
  
<a name="OverrideToString"></a>   
## <a name="overriding-the-tostring-method"></a>ToString Yöntemini Geçersiz Kılma  
 Bir türün adını görüntülemek, genellikle sınırlı bir kullanımdır ve bir örneği bir diğerinden ayırt etmesine Türlerinizin tüketicilerinin izin vermiyor. Ancak, kılabilirsiniz `ToString` bir daha kullanışlı bir nesne değeri temsili sağlamak için yöntemi. Aşağıdaki örnekte tanımlayan bir `Temperature` nesne ve geçersiz kılmalar, `ToString` sıcaklığı Santigrat derece olarak görüntülemek için yöntemi.  
  
 [!code-csharp[Conceptual.Formatting.Overview#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/overrides1.cs#2)]
 [!code-vb[Conceptual.Formatting.Overview#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/overrides1.vb#2)]  
  
 . NET'te, `ToString` yöntemi her temel değer türünün adı yerine nesnenin değerini görüntülemek için kılınmış. Aşağıdaki tablo her ilkel tür için geçersiz kılma gösterir. Geçersiz kılınan yöntemlerin çoğunun başka bir aşırı yüklemesini çağırmak Not `ToString` yöntemi ve kendi türünün genel biçimini tanımlar, "G" Biçim belirleyicisi geçirin ve bir <xref:System.IFormatProvider> geçerli kültürü temsil eden nesne.  
  
|Tür|ToString'i geçersiz kılma|  
|----------|-----------------------|  
|<xref:System.Boolean>|Döndürür <xref:System.Boolean.TrueString?displayProperty=nameWithType> veya <xref:System.Boolean.FalseString?displayProperty=nameWithType>.|  
|<xref:System.Byte>|Çağrıları `Byte.ToString("G", NumberFormatInfo.CurrentInfo)` biçimlendirmek için <xref:System.Byte> geçerli kültür için değer.|  
|<xref:System.Char>|Karakteri bir dize olarak döndürür.|  
|<xref:System.DateTime>|Çağrıları `DateTime.ToString("G", DatetimeFormatInfo.CurrentInfo)` geçerli kültür için tarih ve saat değerini biçimlendirmek için.|  
|<xref:System.Decimal>|Çağrıları `Decimal.ToString("G", NumberFormatInfo.CurrentInfo)` biçimlendirmek için <xref:System.Decimal> geçerli kültür için değer.|  
|<xref:System.Double>|Çağrıları `Double.ToString("G", NumberFormatInfo.CurrentInfo)` biçimlendirmek için <xref:System.Double> geçerli kültür için değer.|  
|<xref:System.Int16>|Çağrıları `Int16.ToString("G", NumberFormatInfo.CurrentInfo)` biçimlendirmek için <xref:System.Int16> geçerli kültür için değer.|  
|<xref:System.Int32>|Çağrıları `Int32.ToString("G", NumberFormatInfo.CurrentInfo)` biçimlendirmek için <xref:System.Int32> geçerli kültür için değer.|  
|<xref:System.Int64>|Çağrıları `Int64.ToString("G", NumberFormatInfo.CurrentInfo)` biçimlendirmek için <xref:System.Int64> geçerli kültür için değer.|  
|<xref:System.SByte>|Çağrıları `SByte.ToString("G", NumberFormatInfo.CurrentInfo)` biçimlendirmek için <xref:System.SByte> geçerli kültür için değer.|  
|<xref:System.Single>|Çağrıları `Single.ToString("G", NumberFormatInfo.CurrentInfo)` biçimlendirmek için <xref:System.Single> geçerli kültür için değer.|  
|<xref:System.UInt16>|Çağrıları `UInt16.ToString("G", NumberFormatInfo.CurrentInfo)` biçimlendirmek için <xref:System.UInt16> geçerli kültür için değer.|  
|<xref:System.UInt32>|Çağrıları `UInt32.ToString("G", NumberFormatInfo.CurrentInfo)` biçimlendirmek için <xref:System.UInt32> geçerli kültür için değer.|  
|<xref:System.UInt64>|Çağrıları `UInt64.ToString("G", NumberFormatInfo.CurrentInfo)` biçimlendirmek için <xref:System.UInt64> geçerli kültür için değer.|  
  
 [Başa dön](#Introduction)  
  
<a name="FormatStrings"></a>   
## <a name="the-tostring-method-and-format-strings"></a>ToString Yöntemi ve Biçim Dizeleri  
 Varsayılan bağlı olan `ToString` yöntemi veya geçersiz kılma `ToString` nesne tek bir dize temsili varsa uygundur. Ancak, bir nesnenin değerini, genellikle birden çok temsile sahiptir. Örneğin bir sıcaklık Fahrenhayt derece, Santigrat derece ve Kelvin cinsinden ifade edilebilir. Benzer şekilde, tamsayı değeri 10 10 ' da dahil olmak üzere çeşitli şekillerde temsil edilebilir 10.0, 1.0e01 ya da $10,00.  
  
 Tek bir değerin birden çok dize gösterimini etkinleştirmek için .NET biçim dizeleri kullanır. Bir biçim dizesi içeren bir dize veya tek karakterleri veya tanımladığınız karakter grubu olan daha önceden tanımlı Biçim belirleyicisi olan nasıl `ToString` yöntemi çıktısını biçimlendirme. Biçim dizesi bir parametre olarak nesnenin geçirilir `ToString` yöntemi ve nesnenin değerinin dize gösterimini nasıl görüneceğini belirler.  
  
 Önceden tanımlanmış biçim belirticileri kümesi tüm sayısal türler, tarih ve saat türleri ve. NET'te Numaralandırma türleri destekler. Biçim dizeleri Ayrıca, uygulama tanımlı veri türleri, birden çok dize gösterimini tanımlamak için de kullanabilirsiniz.  
  
<a name="standardStrings"></a>   
### <a name="standard-format-strings"></a>Standart Biçim Dizeleri  
 Standart biçim dizesi, uygulandığı, kaç hane görüntülenme şeklini etkiler bir isteğe bağlı bir hassas belirleyici ile birlikte nesnenin dize temsili tanımlar alfabetik bir karakter olan bir tek biçim belirticisi içerir Sonuç dizesi. Duyarlık belirtici atlanırsa veya desteklenmeyen ise bir standart biçim tanımlayıcısı bir standart biçim dizesine eşdeğerdir.  
  
 .NET, tüm sayısal türler, tüm tarih ve saat türleri ve tüm numaralandırma türleri için standart biçim belirticileri kümesi tanımlar. Örneğin bu kategorilerden her biri bir değer türü genel dize temsili tanımlar bir "G" Standart Biçim belirleyicisi destekler.  
  
 Numaralandırma türleri için standart biçim dizeleri bir değerin dize gösterimini doğrudan kontrol eder. Bir sabit listesi değerinin geçilen biçim dizeleri `ToString` yöntemi, değerin dize adıyla ("G" ve "F" biçim belirticileri), arka plandaki tamsayı değeriyle ("D" biçim belirticisi) yoksa onaltılık değeriyle ("X kullanarak görüntülenip görüntülenmeyeceğini belirler "biçim belirticisi). Aşağıdaki örnek biçimlendirmek için standart biçim dizeleri kullanışını bir <xref:System.DayOfWeek> numaralandırma değeri.  
  
 [!code-csharp[Conceptual.Formatting.Overview#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/standard1.cs#4)]
 [!code-vb[Conceptual.Formatting.Overview#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/standard1.vb#4)]  
  
 Sabit listesi biçim dizeleri hakkında daha fazla bilgi için bkz: [sabit listesi biçim dizeleri](../../../docs/standard/base-types/enumeration-format-strings.md).  
  
 Sayısal türlerin standart biçim dizeleri, genellikle, tam görünümü bir veya daha fazla özellik değeri tarafından denetlenen bir sonuç dizesini tanımlar. Örneğin, "C" biçim belirticisi bir sayıyı bir para birimi değeri olarak biçimlendirir. Çağırdığınızda `ToString` yöntemini tek parametre olarak "C" biçim belirticisi, aşağıdaki özellik değerleri geçerli kültürün <xref:System.Globalization.NumberFormatInfo> nesne sayısal değerin dize gösterimini tanımlamak için kullanılır:  
  
-   <xref:System.Globalization.NumberFormatInfo.CurrencySymbol%2A> Geçerli kültürün para birimi sembolünü belirten özelliği.  
  
-   <xref:System.Globalization.NumberFormatInfo.CurrencyNegativePattern%2A> Veya <xref:System.Globalization.NumberFormatInfo.CurrencyPositivePattern%2A> aşağıdakileri belirleyen bir tamsayı döndüren özelliği:  
  
    -   Para birimi sembolünün yerleşimini.  
  
    -   Olup negatif değerler başta bir eksi işareti, sonda bir eksi işareti veya parantezler ile gösterilir.  
  
    -   Olup bir alanı sayısal değer ile para birimi sembolü arasında görünür.  
  
-   <xref:System.Globalization.NumberFormatInfo.CurrencyDecimalDigits%2A> Özelliği sonuç dizesinde kesirli bir basamak sayısını tanımlar.  
  
-   <xref:System.Globalization.NumberFormatInfo.CurrencyDecimalSeparator%2A> Sonuç dizesindeki ondalık ayırma sembolünü tanımlayan özellik.  
  
-   <xref:System.Globalization.NumberFormatInfo.CurrencyGroupSeparator%2A> Grup ayırma sembolünü tanımlayan özellik.  
  
-   <xref:System.Globalization.NumberFormatInfo.CurrencyGroupSizes%2A> Küsur işaretinin solundaki her gruptaki rakam sayısını tanımlayan özellik.  
  
-   <xref:System.Globalization.NumberFormatInfo.NegativeSign%2A> Negatif değerleri göstermek için parantez kullanılmıyorsa sonuç dizesinde kullanılacak negatif işaretini belirleyen özelliği.  
  
 Ayrıca, bir sayısal biçim dizeleri bir hassas belirleyici içerebilir. Bu tanımlayıcının anlamını biçim dizesi hangi kullanılır, ancak genellikle basamakların toplam sayısı veya sonuç dizesinde görünmesi gereken kesirli bir basamak sayısını gösterir bağlıdır. Örneğin, aşağıdaki örnek "X 4" standart sayısal dizesi ve duyarlık belirtici dört onaltılık basamağı olan bir dize değeri oluşturmak için kullanır.  
  
 [!code-csharp[Conceptual.Formatting.Overview#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/precisionspecifier1.cs#6)]
 [!code-vb[Conceptual.Formatting.Overview#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/precisionspecifier1.vb#6)]  
  
 Standart sayısal biçimlendirme dizeleri hakkında daha fazla bilgi için bkz: [standart sayısal biçim dizeleri](../../../docs/standard/base-types/standard-numeric-format-strings.md).  
  
 Tarih ve saat değerleri için standart biçim dizeleri için belirli bir tarafından depolanan özel biçim dizelerinin diğer adlarıdır <xref:System.Globalization.DateTimeFormatInfo> özelliği. Örneğin, çağırma `ToString` yöntemi ile "D" biçim belirticisi bir tarih ve saat değerinin tarih ve saat geçerli kültürün içinde depolanan özel biçim dizesi kullanarak görüntüler <xref:System.Globalization.DateTimeFormatInfo.LongDatePattern%2A?displayProperty=nameWithType> özelliği. (Özel biçim dizeleri hakkında daha fazla bilgi için bkz. [sonraki bölümde](#customStrings).) Aşağıdaki örnek bu ilişkiyi göstermektedir.  
  
 [!code-csharp[Conceptual.Formatting.Overview#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/alias1.cs#5)]
 [!code-vb[Conceptual.Formatting.Overview#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/alias1.vb#5)]  
  
 Standart tarih ve saat biçim dizeleri hakkında daha fazla bilgi için bkz: [standart tarih ve saat biçim dizeleri](../../../docs/standard/base-types/standard-date-and-time-format-strings.md).  
  
 Nesne tarafından üretilen uygulama tanımlı bir nesnenin dize temsilini tanımlamak için standart biçim dizeleri kullanabilirsiniz `ToString(String)` yöntemi. Nesnenizin desteklediği özgül standart biçim belirticileri tanımlayabilir ve bunların büyük küçük harfe duyarlı veya duyarsız olup olmadığını belirleyebilirsiniz. Uygulamanıza `ToString(String)` yöntemi şunları desteklemelidir:  
  
-   Nesnenin geleneksel ya da genel bir biçimini temsil eden bir "G" Biçim belirleyicisi. Nesnenizin parametresiz aşırı yüklemesi `ToString` yöntemini çağırın, `ToString(String)` "G" standart biçim dizesine geçmek ve aşırı yükleme.  
  
-   Bir null başvuruya eşit olan bir biçim belirtici için destek (`Nothing` Visual Basic'te). Bir null başvuruya eşit olan bir biçim belirtici "G" biçimli belirleyiciye eşdeğer kabul edilmelidir.  
  
 Örneğin, bir `Temperature` sınıfı, dahili olarak sıcaklığı Santigrat derece cinsinden depolayabilir ve değerini temsil etmek için biçim Belirleyicileri kullanma `Temperature` Santigrat derece, fahrenhayt derece ve Kelvin cinsinden nesne. Aşağıdaki örnek, bir gösterim sağlar.  
  
 [!code-csharp[Conceptual.Formatting.Overview#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/appstandard1.cs#7)]
 [!code-vb[Conceptual.Formatting.Overview#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/appstandard1.vb#7)]  
  
 [Başa dön](#Introduction)  
  
<a name="customStrings"></a>   
### <a name="custom-format-strings"></a>Özel Biçim Dizeleri  
 Standart biçim dizelerine ek olarak, .NET, hem sayısal değerler hem de tarih ve saat değerleri için özel biçim dizeleri tanımlar. Bir özel biçim dizesinde bir değerin dize temsilini tanımlayan bir veya daha fazla özel biçim belirleyicisinden oluşur. Örneğin, özel tarih ve saat biçim dizesi "yyyy/mm/dd hh:mm:ss.ffff t zzz" formundaki kendi dize temsiline dönüştürür "2008/11/15 07:45:00.0000 P -08:00" en-US kültürü için. Benzer şekilde, özel biçim dizesi "0000", tamsayı değeri 12 "0012"'ye dönüştürür. Özel biçim dizeleri tam bir listesi için bkz. [özel tarih ve saat biçim dizeleri](../../../docs/standard/base-types/custom-date-and-time-format-strings.md) ve [özel sayısal biçim dizeleri](../../../docs/standard/base-types/custom-numeric-format-strings.md).  
  
 Bir biçim dizesi tek özel biçim belirleyicisinden oluşuyorsa, Biçim belirleyicisi standart biçim belirteci ile Karışıklığı önlemek için yüzde (%) sembolü gelmelidir. Aşağıdaki örnek, belirli bir tarihin ayın tek basamaklı veya iki basamaklı bir sayı görüntülemek için "M" özel Biçim belirleyicisi kullanır.  
  
 [!code-csharp[Conceptual.Formatting.Overview#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/singlecustom1.cs#8)]
 [!code-vb[Conceptual.Formatting.Overview#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/singlecustom1.vb#8)]  
  
 Tarih ve saat değerleri için birçok standart biçim dizesi özellikleri tarafından tanımlanan özel biçim dizeleri için diğer adlardır <xref:System.Globalization.DateTimeFormatInfo> nesne. Özel biçim dizeleri de sayısal değerler ya da tarih ve saat değerleri için uygulama tanımlı biçimlendirme sunarken önemli ölçüde esneklik sunar. Birden fazla özel biçim belirticileri bir tek özel biçim dizesinde birleştirerek hem sayısal değerler hem de tarih ve saat değerleri için kendi özel sonuç dizelerinizi tanımlayabilirsiniz. Aşağıdaki örnek, haftanın gününü ay adı, gün ve yıl sonra parantez içinde gösteren özel bir biçim dizesi tanımlar.  
  
 [!code-csharp[Conceptual.Formatting.Overview#9](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/custom1.cs#9)]
 [!code-vb[Conceptual.Formatting.Overview#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/custom1.vb#9)]  
  
 Aşağıdaki örnek, görüntüleyen bir özel biçim dizesi tanımlar. bir <xref:System.Int64> değerini bölge koduyla birlikte standart, yedi rakamlı ABD telefon numarası olarak.  
  
 [!code-csharp[Conceptual.Formatting.Overview#21](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/telnumber1.cs#21)]
 [!code-vb[Conceptual.Formatting.Overview#21](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/telnumber1.vb#21)]  
  
 Standart biçim dizeleri genelde uygulamanızın tanımladığı türlerin biçimlendirme ihtiyaçlarının çoğunu yönetebilmesine rağmen türlerinizi biçimlendirmek için özel biçim belirticileri da tanımlayabilir.  
  
 [Başa dön](#Introduction)  
  
<a name="stringRef"></a>   
### <a name="format-strings-and-net-types"></a>Biçim dizeleri ve .NET türleri  
 Tüm sayısal türlerin (diğer bir deyişle, <xref:System.Byte>, <xref:System.Decimal>, <xref:System.Double>, <xref:System.Int16>, <xref:System.Int32>, <xref:System.Int64>, <xref:System.SByte>, <xref:System.Single>, <xref:System.UInt16>, <xref:System.UInt32>, <xref:System.UInt64>ve <xref:System.Numerics.BigInteger>türleri), hem de <xref:System.DateTime>, <xref:System.DateTimeOffset>, <xref:System.TimeSpan>, <xref:System.Guid>, ve tüm numaralandırma türleri, biçim dizeleri ile biçimlendirme desteği. Her türü tarafından desteklenen özel biçim dizeleri hakkında daha fazla bilgi için aşağıdaki konulara bakın:  
  
|Başlık|Tanım|  
|-----------|----------------|  
|[Standart Sayısal Biçim Dizeleri](../../../docs/standard/base-types/standard-numeric-format-strings.md)|Sayısal değerlerin ortak kullanılan dize temsillerini oluşturan standart biçim dizelerini açıklar.|  
|[Özel Sayısal Biçim Dizeleri](../../../docs/standard/base-types/custom-numeric-format-strings.md)|Sayısal değerler için uygulamaya özel biçimler oluşturan biçim dizelerini açıklar.|  
|[Standart Tarih ve Saat Biçim Dizeleri](../../../docs/standard/base-types/standard-date-and-time-format-strings.md)|Ortak kullanılan dize temsillerini oluşturan standart biçim dizelerini açıklar <xref:System.DateTime> ve <xref:System.DateTimeOffset> değerleri.|  
|[Özel Tarih ve Saat Biçim Dizeleri](../../../docs/standard/base-types/custom-date-and-time-format-strings.md)|İçin uygulamaya özel biçimler oluşturan biçim dizelerini açıklar <xref:System.DateTime> ve <xref:System.DateTimeOffset> değerleri.|  
|[Standart TimeSpan Biçim Dizeleri](../../../docs/standard/base-types/standard-timespan-format-strings.md)|Zaman aralıkları ortak kullanılan dize temsillerini oluşturan standart biçim dizelerini açıklar.|  
|[Özel TimeSpan Biçim Dizeleri](../../../docs/standard/base-types/custom-timespan-format-strings.md)|Zaman aralıkları için uygulamaya özel biçimler oluşturan biçim dizelerini açıklar.|  
|[Sabit Listesi Biçim Dizeleri](../../../docs/standard/base-types/enumeration-format-strings.md)|Numaralandırma değerlerinin dize temsillerini oluşturmak için kullanılan standart biçim dizelerini açıklar.|  
|<xref:System.Guid.ToString%28System.String%29?displayProperty=nameWithType>|İçin standart biçim dizelerini açıklar <xref:System.Guid> değerleri.|  
  
<a name="FormatProviders"></a>   
## <a name="culture-sensitive-formatting-with-format-providers-and-the-iformatprovider-interface"></a>Biçim Sağlayıcıları ve IFormatProvider Arabirimi ile Kültüre Duyarlı Biçimlendirme  
 Biçim belirticileri nesnelerin biçimlendirme özelleştirmenize izin vermesine rağmen genellikle anlamlı dize gösterimi nesnelerin üretme ek biçimlendirme bilgisi gerekir. Örneğin, bir sayı gibi "C" standart biçim dizesi ya da bir özel biçim dizesi kullanarak bir para birimi değeri olarak biçimlendirme "$ #, #. 00" gerektirir, en azından geçerli para birimi sembolü, Grup ayırıcı ve ondalık ayırıcısı olarak hakkında bilgi biçimlendirilen dize içinde kullanılabilir. . NET'te, bu ek biçimlendirme bilgisi kullanılabilir hale <xref:System.IFormatProvider> bir veya daha fazla aşırı yüküne bir parametre olarak sağlanan arabirim `ToString` sayısal türlerin ve tarih ve saat türlerinin yöntemi. <xref:System.IFormatProvider> uygulamaları,. NET'te kültüre özgü biçimlendirmeyi desteklemek için kullanılır. Aşağıdaki örnek üç biçimlendirildiğinde bir nesnenin dize gösterimini nasıl değiştiğini gösterir <xref:System.IFormatProvider> farklı kültürü temsil eden nesneleri.  
  
 [!code-csharp[Conceptual.Formatting.Overview#11](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/iformatprovider1.cs#11)]
 [!code-vb[Conceptual.Formatting.Overview#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/iformatprovider1.vb#11)]  
  
 <xref:System.IFormatProvider> Arabirimi içeren bir yöntem <xref:System.IFormatProvider.GetFormat%28System.Type%29>, biçimlendirme bilgilerini sağlayan nesne türünü belirten tek bir parametre vardır. Yöntemi o türün bir nesnesini sağlayabiliyorsa, bunu döndürür. Aksi takdirde, null bir başvuru döndürür (`Nothing` Visual Basic'te).  
  
 <xref:System.IFormatProvider.GetFormat%2A?displayProperty=nameWithType> bir geri çağırma yöntemidir. Çağırdığınızda bir `ToString` içeren yöntemi aşırı yüklemesini bir <xref:System.IFormatProvider> parametresini çağırır <xref:System.IFormatProvider.GetFormat%2A> yöntem <xref:System.IFormatProvider> nesne. <xref:System.IFormatProvider.GetFormat%2A> Yöntemi tarafından belirtilen gerekli biçimlendirme bilgilerini sağlayan bir nesne döndürmekten sorumludur kendi `formatType` parametresi, `ToString` yöntemi.  
  
 Bir dizi biçimlendirme ya da dize dönüştürme yöntem türü parametresi içerir <xref:System.IFormatProvider>, ancak yöntem çağrıldığında birçok durumda parametrenin değeri yoksayılır. Aşağıdaki tablo bazı parametresini ve türünü kullanan bir biçimlendirme yöntemlerini listeler <xref:System.Type> geçtikleri nesne <xref:System.IFormatProvider.GetFormat%2A?displayProperty=nameWithType> yöntemi.  
  
|Yöntem|Tür `formatType` parametresi|  
|------------|------------------------------------|  
|`ToString` sayısal türlerin yöntemi|<xref:System.Globalization.NumberFormatInfo?displayProperty=nameWithType>|  
|`ToString` Tarih ve saat türlerinin yöntemi|<xref:System.Globalization.DateTimeFormatInfo?displayProperty=nameWithType>|  
|<xref:System.String.Format%2A?displayProperty=nameWithType>|<xref:System.ICustomFormatter?displayProperty=nameWithType>|  
|<xref:System.Text.StringBuilder.AppendFormat%2A?displayProperty=nameWithType>|<xref:System.ICustomFormatter?displayProperty=nameWithType>|  
  
> [!NOTE]
>  `ToString` Sayısal türlerin ve tarih ve saat türlerinin yöntemleri aşırı yüklenmiştir ve aşırı yüklemeleri yalnızca bazıları şunlardır bir <xref:System.IFormatProvider> parametresi. Bir yöntem türünde bir parametre yoksa <xref:System.IFormatProvider>, tarafından döndürülen nesne <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=nameWithType> özelliği bunun yerine geçirilen. Örneğin, varsayılan bir çağrı <xref:System.Int32.ToString?displayProperty=nameWithType> yöntemi sonuçta sonuçları aşağıdaki gibi bir yöntem çağrısında: `Int32.ToString("G", System.Globalization.CultureInfo.CurrentCulture)`.  
  
 .NET uygulayan üç sınıf sunar <xref:System.IFormatProvider>:  
  
-   <xref:System.Globalization.DateTimeFormatInfo>, belirli bir kültür için tarih ve saat değerleri için biçimlendirme bilgileri sağlayan bir sınıf. Kendi <xref:System.IFormatProvider.GetFormat%2A?displayProperty=nameWithType> uygulaması kendinin bir örneğini döndürür.  
  
-   <xref:System.Globalization.NumberFormatInfo>, belirli bir kültür için sayısal biçimlendirme bilgilerini sağlayan bir sınıf. Kendi <xref:System.IFormatProvider.GetFormat%2A?displayProperty=nameWithType> uygulaması kendinin bir örneğini döndürür.  
  
-   <xref:System.Globalization.CultureInfo>. Kendi <xref:System.IFormatProvider.GetFormat%2A?displayProperty=nameWithType> uygulama ya da döndürebilir bir <xref:System.Globalization.NumberFormatInfo> sayısal biçimlendirme bilgilerini sağlayan nesne veya <xref:System.Globalization.DateTimeFormatInfo> tarih ve saat değerleri için biçimlendirme bilgileri sağlayan nesne.  
  
 Ayrıca bu sınıfların herhangi birini değiştirmek için kendi biçim sağlayıcılarınızı uygulayabilirsiniz. Ancak, uygulamanızın <xref:System.IFormatProvider.GetFormat%2A> yöntemi, biçimlendirme bilgileri sağlaması gerekiyorsa önceki tabloda listelenen tür nesnesi geri döndürmesi gerekir `ToString` yöntemi.  
  
 [Başa dön](#Introduction)  
  
<a name="numericCulture"></a>   
### <a name="culture-sensitive-formatting-of-numeric-values"></a>Sayısal Değerleri Kültüre Duyarlı Olarak Biçimlendirme  
 Varsayılan olarak, sayısal değerlerin biçimlendirilmesi kültüre duyarlıdır. Bir biçimlendirme yöntemi çağırdığınızda bir kültür belirtmezseniz geçerli iş parçacığı kültürünün biçimlendirme kuralları kullanılır. Bu, geçerli iş parçacığı kültürünü dört kez değiştirdikten sonra çağıran aşağıdaki örnekte gösterilmiştir <xref:System.Decimal.ToString%28System.String%29?displayProperty=nameWithType> yöntemi. Her durumda sonuç dizesi geçerli kültürün biçimlendirme kurallarını yansıtır. Bunun nedeni, `ToString` ve `ToString(String)` yöntemleri her sayısal türün yapılan çağrıları sarmasıdır `ToString(String, IFormatProvider)` yöntemi.  
  
 [!code-csharp[Conceptual.Formatting.Overview#19](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/culturespecific3.cs#19)]
 [!code-vb[Conceptual.Formatting.Overview#19](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/culturespecific3.vb#19)]  
  
 Çağırarak bir sayısal değer belirli bir kültür için biçimlendirebilirsiniz bir `ToString` olan aşırı yüklenmiş bir `provider` parametresi ve aşağıdakilerden birini geçirme:  
  
-   A <xref:System.Globalization.CultureInfo> biçimlendirme kuralları kullanılacak kültürü temsil eden nesne. Kendi <xref:System.Globalization.CultureInfo.GetFormat%2A?displayProperty=nameWithType> yöntemi değerini döndürür <xref:System.Globalization.CultureInfo.NumberFormat%2A?displayProperty=nameWithType> özelliğinin <xref:System.Globalization.NumberFormatInfo> sayısal değerler için kültüre özgü biçimlendirme bilgileri sağlayan nesne.  
  
-   A <xref:System.Globalization.NumberFormatInfo> kullanılacak kültüre özgü biçimlendirme kurallarını tanımlayan nesne. Kendi <xref:System.Globalization.NumberFormatInfo.GetFormat%2A> yöntemi kendinin bir örneğini döndürür.  
  
 Aşağıdaki örnekte <xref:System.Globalization.NumberFormatInfo> bir kayan nokta sayısını biçimlendirmek için İngilizce (ABD) ve İngilizce (İngiltere) kültürlerini ve Fransızca ve Rusça bağımsız kültürlerini temsil eden nesneleri.  
  
 [!code-csharp[Conceptual.Formatting.Overview#20](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/culturespecific4.cs#20)]
 [!code-vb[Conceptual.Formatting.Overview#20](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/culturespecific4.vb#20)]  
  
<a name="dateCulture"></a>   
### <a name="culture-sensitive-formatting-of-date-and-time-values"></a>Tarih ve Saat Değerlerini Kültüre Duyarlı Olarak Biçimlendirme  
 Varsayılan olarak, tarih ve saat değerlerinin biçimlendirilmesi kültüre duyarlıdır. Bir biçimlendirme yöntemi çağırdığınızda bir kültür belirtmezseniz geçerli iş parçacığı kültürünün biçimlendirme kuralları kullanılır. Bu, geçerli iş parçacığı kültürünü dört kez değiştirdikten sonra çağıran aşağıdaki örnekte gösterilmiştir <xref:System.DateTime.ToString%28System.String%29?displayProperty=nameWithType> yöntemi. Her durumda sonuç dizesi geçerli kültürün biçimlendirme kurallarını yansıtır. Bunun nedeni, <xref:System.DateTime.ToString?displayProperty=nameWithType>, <xref:System.DateTime.ToString%28System.String%29?displayProperty=nameWithType>, <xref:System.DateTimeOffset.ToString?displayProperty=nameWithType>, ve <xref:System.DateTimeOffset.ToString%28System.String%29?displayProperty=nameWithType> yöntemleri yapılan çağrıları sarmasıdır <xref:System.DateTime.ToString%28System.String%2CSystem.IFormatProvider%29?displayProperty=nameWithType> ve <xref:System.DateTimeOffset.ToString%28System.String%2CSystem.IFormatProvider%29?displayProperty=nameWithType> yöntemleri.  
  
 [!code-csharp[Conceptual.Formatting.Overview#17](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/culturespecific1.cs#17)]
 [!code-vb[Conceptual.Formatting.Overview#17](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/culturespecific1.vb#17)]  
  
 Çağırarak bir tarih ve saat değerini belirli bir kültür için biçimlendirebilirsiniz bir <xref:System.DateTime.ToString%2A?displayProperty=nameWithType> veya <xref:System.DateTimeOffset.ToString%2A?displayProperty=nameWithType> olan aşırı yüklenmiş bir `provider` parametresi ve aşağıdakilerden birini geçirme:  
  
-   A <xref:System.Globalization.CultureInfo> biçimlendirme kuralları kullanılacak kültürü temsil eden nesne. Kendi <xref:System.Globalization.CultureInfo.GetFormat%2A?displayProperty=nameWithType> yöntemi değerini döndürür <xref:System.Globalization.CultureInfo.DateTimeFormat%2A?displayProperty=nameWithType> özelliğinin <xref:System.Globalization.DateTimeFormatInfo> tarih ve saat değerleri için kültüre özgü biçimlendirme bilgileri sağlayan nesne.  
  
-   A <xref:System.Globalization.DateTimeFormatInfo> kullanılacak kültüre özgü biçimlendirme kurallarını tanımlayan nesne. Kendi <xref:System.Globalization.DateTimeFormatInfo.GetFormat%2A> yöntemi kendinin bir örneğini döndürür.  
  
 Aşağıdaki örnekte <xref:System.Globalization.DateTimeFormatInfo> bir tarihi biçimlendirmek için İngilizce (ABD) ve İngilizce (İngiltere) kültürlerini ve Fransızca ve Rusça bağımsız kültürlerini temsil eden nesneleri.  
  
 [!code-csharp[Conceptual.Formatting.Overview#18](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/culturespecific2.cs#18)]
 [!code-vb[Conceptual.Formatting.Overview#18](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/culturespecific2.vb#18)]  
  
<a name="IFormattable"></a>   
## <a name="the-iformattable-interface"></a>IFormattable Arabirimi  
 Genellikle, aşırı yükleyen türler `ToString` bir biçim dizesi ile yöntemi ve bir <xref:System.IFormatProvider> parametresi de uygulamak <xref:System.IFormattable> arabirimi. Bu arabirim bir tek üyeye sahip <xref:System.IFormattable.ToString%28System.String%2CSystem.IFormatProvider%29?displayProperty=nameWithType>, parametre olarak hem bir biçim dizesi hem de bir biçim sağlayıcısı içeren.  
  
 Uygulama <xref:System.IFormattable> arabirimini uygulama tanımlı sınıfınız iki avantaj sağlar:  
  
-   Dize dönüştürme için destek <xref:System.Convert> sınıfı. Çağrılar <xref:System.Convert.ToString%28System.Object%29?displayProperty=nameWithType> ve <xref:System.Convert.ToString%28System.Object%2CSystem.IFormatProvider%29?displayProperty=nameWithType> yöntemi çağrısı, <xref:System.IFormattable> uygulama otomatik olarak.  
  
-   Bileşik biçimlendirme desteği. Bir biçim öğesi içeren bir biçim dizesi özel türünüzü biçimlendirmek için kullanılan, ortak dil çalışma zamanı otomatik olarak çağırır, <xref:System.IFormattable> uygulama ve biçim dizesine geçirir. Bileşik yöntemleriyle gibi biçimlendirme hakkında daha fazla bilgi için <xref:System.String.Format%2A?displayProperty=nameWithType> veya <xref:System.Console.WriteLine%2A?displayProperty=nameWithType>, bkz: [bileşik biçimlendirme](#CompositeFormatting) bölümü.  
  
 Aşağıdaki örnekte tanımlayan bir `Temperature` uygulayan sınıf <xref:System.IFormattable> arabirimi. Bu, "C" veya "G" biçim belirticilerini, sıcaklığı Santigrat cinsinden görüntülemek için sıcaklığı Fahrenhayt cinsinden görüntülemek için "F" biçim belirticisi ve "K" biçim belirticisi sıcaklığı Kelvin cinsinden görüntülemek için destekler.  
  
 [!code-csharp[Conceptual.Formatting.Overview#12](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/iformattable.cs#12)]
 [!code-vb[Conceptual.Formatting.Overview#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/iformattable.vb#12)]  
  
 Aşağıdaki örnek bir `Temperature` nesne. Ardından <xref:System.Convert.ToString%2A> yöntemi ve farklı elde etmek için çeşitli bileşik biçimli dizeler dize temsillerini kullanan bir `Temperature` nesne. Bu yöntem çağrılarından her sırayla çağırır <xref:System.IFormattable> uygulaması `Temperature` sınıfı.  
  
 [!code-csharp[Conceptual.Formatting.Overview#13](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/iformattable.cs#13)]
 [!code-vb[Conceptual.Formatting.Overview#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/iformattable.vb#13)]  
  
 [Başa dön](#Introduction)  
  
<a name="CompositeFormatting"></a>   
## <a name="composite-formatting"></a>Bileşik Biçimlendirme  
 Bazı yöntemler gibi <xref:System.String.Format%2A?displayProperty=nameWithType> ve <xref:System.Text.StringBuilder.AppendFormat%2A?displayProperty=nameWithType>, bileşik biçimlendirmeyi destekler. Bir bileşik biçimlendirme dizesi, sıfır, bir veya daha fazla nesne dize gösterimini içeren tek bir dize döndüren bir şablon türüdür. Her nesne bileşik Biçim dizesinde bir dizini oluşturulmuş bir biçim öğesi tarafından temsil edilir. Biçim öğesinin dizin, yöntemin parametre listesinde temsil ettiği nesnenin konumuna karşılık gelir. Dizinler sıfır tabanlıdır. Örneğin, aşağıdaki çağrı <xref:System.String.Format%2A?displayProperty=nameWithType> yöntemi, birinci biçim öğesi olan `{0:D}`, dize temsili ile değiştirilir `thatDate`; ikinci biçim öğesi olan `{1}`, dizetemsiliiledeğiştirilir`item1`; ve üçüncü biçim öğesi olan `{2:C2}`, dize temsili ile değiştirilir `item1.Value`.  
  
 [!code-csharp[Conceptual.Formatting.Overview#14](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/composite1.cs#14)]
 [!code-vb[Conceptual.Formatting.Overview#14](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/composite1.vb#14)]  
  
 Bir biçim öğesi, karşılık gelen nesnenin dize gösterimini ile değiştirerek yanı sıra, biçim öğeleri de aşağıdaki denetlemenize olanak verir:  
  
-   Nesne uyguluyorsa, bir nesne bir dize olarak temsil edilen belirli yoludur <xref:System.IFormattable> arabirim ve biçim dizeleri destekler. Öğenin dizini ile izleyerek bunu bir `:` (üste) tarafından geçerli bir biçim dizesi. Önceki örnek "d" (kısa tarih deseni) biçim dizesi içeren bir date değeri biçimlendirme tarafından bu işlem (örn, `{0:d}`) ve biçim dizesi "C2" ile bir sayısal biçimlendirme (örneğin, `{2:C2}` iki para birimi değeri olarak sayıyı temsil etmek için kesirli ondalık basamaklar.  
  
-   Nesnenin dize gösterimi ve bu alandaki dize gösteriminin hizalama içeren alan genişliği. Öğenin dizini ile izleyerek bunu bir `,` (virgül) ve ardından alan genişliği. Dize alanı alan genişliği pozitif bir değer varsa ve bunu sol alan genişliği negatif bir değer ise hizalanır sağa hizalanır. Aşağıdaki örnek sol-20 karakter alanda tarih değerleri, ve onu sağ-ondalık değerleri 11 karakterli bir alanda kesirli bir basamak ile hizalar.  
  
     [!code-csharp[Conceptual.Formatting.Overview#22](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/composite2.cs#22)]
     [!code-vb[Conceptual.Formatting.Overview#22](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/composite2.vb#22)]  
  
     Hizalama dizesi bileşeni hem biçim dizesi bileşeni mevcut olması durumunda, önceki ikinci önündeki, Not (örneğin, `{0,-20:g}`.  
  
 Bileşik biçimlendirme hakkında daha fazla bilgi için bkz. [bileşik biçimlendirme](../../../docs/standard/base-types/composite-formatting.md).  
  
 [Başa dön](#Introduction)  
  
<a name="Custom"></a>   
## <a name="custom-formatting-with-icustomformatter"></a>ICustomFormatter ile Özel Biçimlendirme  
 İki bileşik biçimlendirme yöntemi, <xref:System.String.Format%28System.IFormatProvider%2CSystem.String%2CSystem.Object%5B%5D%29?displayProperty=nameWithType> ve <xref:System.Text.StringBuilder.AppendFormat%28System.IFormatProvider%2CSystem.String%2CSystem.Object%5B%5D%29?displayProperty=nameWithType>, özel biçimlendirmeyi destekleyen bir biçim sağlayıcı parametresi içerir. Bu biçimlendirme yöntemlerinden biri çağrıldığında, arabimini bir <xref:System.Type> temsil eden bir nesne bir <xref:System.ICustomFormatter> biçim sağlayıcısının arabirimine <xref:System.IFormatProvider.GetFormat%2A> yöntemi. <xref:System.IFormatProvider.GetFormat%2A> Yöntemi döndürmekten sorumludur ardından <xref:System.ICustomFormatter> özel biçimlendirme sağlayan uygulama.  
  
 <xref:System.ICustomFormatter> Arabirimi tek bir yöntemi vardır <xref:System.ICustomFormatter.Format%28System.String%2CSystem.Object%2CSystem.IFormatProvider%29>, yani bir bileşik biçimlendirme yöntemi, bir bileşik biçimlendirme dizesi her biçimlendirme öğesi için bir kez tarafından otomatik olarak çağrılır. <xref:System.ICustomFormatter.Format%28System.String%2CSystem.Object%2CSystem.IFormatProvider%29> Yönteminin üç parametresi vardır: temsil eden bir biçim dizesi `formatString` bağımsız değişkeni bir biçim öğesindeki Biçimlendirilecek bir nesne ve bir <xref:System.IFormatProvider> Hizmetleri biçimlendirme sağlayan nesne. Genellikle, uygulayan sınıf <xref:System.ICustomFormatter> ayrıca uygulayan <xref:System.IFormatProvider>, bu son parametre özel biçimlendirme bir başvuru sınıfının kendisine olacak şekilde. Yöntem, Biçimlendirilecek nesnenin özel bir biçimlendirilmiş dize gösterimini döndürür. Yöntem nesneyi biçimlendiremiyorsa, bir null başvuru döndürmesi gerekir (`Nothing` Visual Basic'te).  
  
 Aşağıdaki örnek sağlayan bir <xref:System.ICustomFormatter> adlı uygulama `ByteByByteFormatter` , gösteren tamsayı değerlerini iki rakamlı onaltılık değerler ardından bir boşluk olarak.  
  
 [!code-csharp[Conceptual.Formatting.Overview#15](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/icustomformatter1.cs#15)]
 [!code-vb[Conceptual.Formatting.Overview#15](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/icustomformatter1.vb#15)]  
  
 Aşağıdaki örnekte `ByteByByteFormatter` tamsayı değerlerini biçimlendirmek için sınıf. Unutmayın <xref:System.ICustomFormatter.Format%2A?displayProperty=nameWithType> yöntemi ikinci birden çok kez çağrılır <xref:System.String.Format%28System.IFormatProvider%2CSystem.String%2CSystem.Object%5B%5D%29?displayProperty=nameWithType> yöntemi çağrısında varsayılan <xref:System.Globalization.NumberFormatInfo> sağlayıcısı olduğundan üçüncü yöntem çağrısında kullanılan.`ByteByByteFormatter.Format` yöntemi "N0" biçim dizesini tanımadığından ve bir null başvuru döndürür (`Nothing` Visual Basic'te).  
  
 [!code-csharp[Conceptual.Formatting.Overview#16](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/icustomformatter1.cs#16)]
 [!code-vb[Conceptual.Formatting.Overview#16](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/icustomformatter1.vb#16)]  
  
 [Başa dön](#Introduction)  
  
<a name="RelatedTopics"></a>   
## <a name="related-topics"></a>İlgili Konular  
  
|Başlık|Tanım|  
|-----------|----------------|  
|[Standart Sayısal Biçim Dizeleri](../../../docs/standard/base-types/standard-numeric-format-strings.md)|Sayısal değerlerin ortak kullanılan dize temsillerini oluşturan standart biçim dizelerini açıklar.|  
|[Özel Sayısal Biçim Dizeleri](../../../docs/standard/base-types/custom-numeric-format-strings.md)|Sayısal değerler için uygulamaya özel biçimler oluşturan biçim dizelerini açıklar.|  
|[Standart Tarih ve Saat Biçim Dizeleri](../../../docs/standard/base-types/standard-date-and-time-format-strings.md)|Ortak kullanılan dize temsillerini oluşturan standart biçim dizelerini açıklar <xref:System.DateTime> değerleri.|  
|[Özel Tarih ve Saat Biçim Dizeleri](../../../docs/standard/base-types/custom-date-and-time-format-strings.md)|İçin uygulamaya özel biçimler oluşturan biçim dizelerini açıklar <xref:System.DateTime> değerleri.|  
|[Standart TimeSpan Biçim Dizeleri](../../../docs/standard/base-types/standard-timespan-format-strings.md)|Zaman aralıkları ortak kullanılan dize temsillerini oluşturan standart biçim dizelerini açıklar.|  
|[Özel TimeSpan Biçim Dizeleri](../../../docs/standard/base-types/custom-timespan-format-strings.md)|Zaman aralıkları için uygulamaya özel biçimler oluşturan biçim dizelerini açıklar.|  
|[Sabit Listesi Biçim Dizeleri](../../../docs/standard/base-types/enumeration-format-strings.md)|Numaralandırma değerlerinin dize temsillerini oluşturmak için kullanılan standart biçim dizelerini açıklar.|  
|[Bileşik Biçimlendirme](../../../docs/standard/base-types/composite-formatting.md)|Bir veya daha fazla biçimlendirilmiş değerin bir dizeye katıştırmak açıklar. Dize daha sonra konsolda gösterilebilir veya bir akışa yazılabilir.|  
|[Biçimlendirme İşlemlerini Gerçekleştirme](../../../docs/standard/base-types/performing-formatting-operations.md)|Özel biçimlendirme işlemlerini gerçekleştirmek için adım adım talimatları sağlayan konuları listeler.|  
|[Dizeleri Ayrıştırma](../../../docs/standard/base-types/parsing-strings.md)|Nesnelerinin bu nesnelerin dize temsillerini açıklanan değerlere nasıl başlatılacağını açıklar. Ayrıştırma biçimlendirmenin ters işlemidir.|  
  
 [Başa dön](#Introduction)  
  
<a name="Reference"></a>   
## <a name="reference"></a>Başvuru  
 <xref:System.IFormattable?displayProperty=nameWithType>  
  
 <xref:System.IFormatProvider?displayProperty=nameWithType>  
  
 <xref:System.ICustomFormatter?displayProperty=nameWithType>
