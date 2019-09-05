---
title: .NET 'teki biçimlendirme türleri
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
ms.openlocfilehash: 82dc1e36ae5a0eede7099c8e13ac9a2393bbb904
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70253976"
---
# <a name="formatting-types-in-net"></a>.NET 'teki biçimlendirme türleri

Biçimlendirme, bir sınıf, yapı veya numaralandırma değerinin bir örneğini dize gösterimine dönüştürme işlemidir. böylece, sonuçta elde edilen dize kullanıcılara görüntülenebilir veya orijinal veri türünü geri yüklemek için seri durumdan çıkarılmış olur. Bu dönüştürme bir dizi zorluklara neden olabilir:

- Değerlerin dahili olarak depolandığı yol, kullanıcıların bunları görüntülemek istedikleri yöntemi göstermez. Örneğin, bir telefon numarası, Kullanıcı dostu olmayan 8009999999 biçiminde depolanabilir. Bunun yerine 800-999-9999 olarak gösterilmesi gerekir. Bu şekilde bir sayıyı biçimlendiren bir örnek için [özel biçim dizeleri](#customStrings) bölümüne bakın.

- Bazen bir nesnenin dize gösterimine dönüştürülmesi sezgisel değildir. Örneğin, bir sıcaklık nesnesinin veya bir kişi nesnesinin dize gösteriminin nasıl görünmesi net değildir. Bir sıcaklık nesnesini çeşitli yollarla biçimlendiren bir örnek için bkz. [standart biçim dizeleri](#standardStrings) bölümü.

- Değerler genellikle kültüre duyarlı biçimlendirme gerektirir. Örneğin, parasal değerleri yansıtmak için sayı kullanan bir uygulamada, sayısal dizeler geçerli kültürün para birimi simgesini, Grup ayırıcısını (çoğu kültürde, binlerce ayırıcıdır) ve ondalık sembolünü içermelidir. Örneğin, [biçim sağlayıcıları ve IFormatProvider arabirimi Ile kültüre duyarlı biçimlendirme](#FormatProviders) bölümüne bakın.

- Uygulamanın aynı değeri farklı şekillerde görüntülemesi gerekebilir. Örneğin, bir uygulama, adının bir dize gösterimini görüntüleyerek veya onun temel aldığı değerini görüntüleyerek bir numaralandırma üyesini temsil edebilir. <xref:System.DayOfWeek> Sabit listesinin bir üyesini farklı yollarla biçimlendiren bir örnek için bkz. [standart biçim dizeleri](#standardStrings) bölümü.

> [!NOTE]
> Biçimlendirme bir türün değerini dize temsiline dönüştürür. Ayrıştırma biçimlendirmenin tersidir. Bir ayrıştırma işlemi, dize gösteriminden bir veri türü örneği oluşturur. Dizeleri diğer veri türlerine dönüştürme hakkında daha fazla bilgi için bkz. [dizeleri ayrıştırma](../../../docs/standard/base-types/parsing-strings.md).

.NET, geliştiricilerin bu gereksinimleri ele almasını sağlayan zengin biçimlendirme desteği sağlar.

Bu genel bakış aşağıdaki bölümleri içerir:

- [.NET 'te biçimlendirme](#NetFormatting)

- [ToString yöntemini kullanarak varsayılan biçimlendirme](#DefaultToString)

- [ToString yöntemini geçersiz kılma](#OverrideToString)

- [ToString yöntemi ve biçim dizeleri](#FormatStrings)

  - [Standart biçim dizeleri](#standardStrings)

  - [Özel biçim dizeleri](#customStrings)

  - [Biçim dizeleri ve .NET sınıf kitaplığı türleri](#stringRef)

- [Biçim sağlayıcıları ve IFormatProvider arabirimi ile kültüre duyarlı biçimlendirme](#FormatProviders)

  - [Sayısal değerlerin kültüre duyarlı biçimlendirmesi](#numericCulture)

  - [Tarih ve saat değerlerini kültüre duyarlı olarak biçimlendirme](#dateCulture)

- [IFormattable arabirimi](#IFormattable)

- [Bileşik Biçimlendirme](#CompositeFormatting)

- [ICustomFormatter ile özel biçimlendirme](#Custom)

- [İlgili konular](#RelatedTopics)

- [Başvuru](#Reference)

<a name="NetFormatting"></a>

## <a name="formatting-in-net"></a>.NET 'te biçimlendirme

Biçimlendirme için temel mekanizma, bu konunun ilerleyen kısımlarında yer olarak <xref:System.Object.ToString%2A?displayProperty=nameWithType> [ToString yöntemi kullanılarak varsayılan biçimlendirme ile](#DefaultToString) bahsedilen yöntemin varsayılan uygulamasıdır. Ancak .NET, varsayılan biçimlendirme desteğini değiştirmek ve genişletmek için çeşitli yollar sunar. Bunlar aşağıdakileri içerir:

- Bir nesnenin değerinin özel bir dize gösterimini tanımlamak için yönteminigeçersizkılma.<xref:System.Object.ToString%2A?displayProperty=nameWithType> Daha fazla bilgi için bu konunun devamındaki [ToString metodunu geçersiz kılma](#OverrideToString) bölümüne bakın.

- Bir nesnenin değerinin dize gösterimine birden çok form geçirmesine imkan tanıyan biçim belirticileri tanımlama. Örneğin, aşağıdaki deyimdeki "X" Biçim belirleyicisi bir tamsayıyı onaltılık bir değerin dize gösterimine dönüştürür.

     [!code-csharp[Conceptual.Formatting.Overview#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/specifier1.cs#3)]
     [!code-vb[Conceptual.Formatting.Overview#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/specifier1.vb#3)]

     Biçim belirticileri hakkında daha fazla bilgi için bkz. [ToString yöntemi ve biçim dizeleri](#FormatStrings) bölümü.

- Belirli bir kültürün biçimlendirme kurallarından yararlanmak için biçim sağlayıcıları kullanma. Örneğin, aşağıdaki ifade, en-US kültürün biçimlendirme kurallarını kullanarak bir para birimi değeri görüntüler.

     [!code-csharp[Conceptual.Formatting.Overview#10](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/specifier1.cs#10)]
     [!code-vb[Conceptual.Formatting.Overview#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/specifier1.vb#10)]

     Biçim sağlayıcılarıyla biçimlendirme hakkında daha fazla bilgi için, [biçim sağlayıcıları ve IFormatProvider arabirimi](#FormatProviders) bölümüne bakın.

- Hem sınıf hem de bileşik biçimlendirme <xref:System.IFormattable> <xref:System.Convert> ile dize dönüştürmeyi desteklemek için arabirimini uygulama. Daha fazla bilgi için [IFormattable arabirimi](#IFormattable) bölümüne bakın.

- Daha büyük bir dizedeki bir değerin dize gösterimini katıştırmak için bileşik biçimlendirme kullanma. Daha fazla bilgi için [Bileşik biçimlendirme](#CompositeFormatting) bölümüne bakın.

- Tüm <xref:System.ICustomFormatter> özel <xref:System.IFormatProvider> biçimlendirme çözümünü sağlamak ve uygulamak. Daha fazla bilgi için [ıccustomformatter Ile özel biçimlendirme](#Custom) bölümüne bakın.

Aşağıdaki bölümlerde, bir nesneyi dize gösterimine dönüştürmeye yönelik bu yöntemler incelenmekte.

<a name="DefaultToString"></a>

## <a name="default-formatting-using-the-tostring-method"></a>ToString Yöntemini Kullanarak Varsayılan Biçimlendirme

Öğesinden <xref:System.Object?displayProperty=nameWithType> türetilen her tür, varsayılan olarak türün adını döndüren `ToString` parametresiz bir yöntemi otomatik olarak devralır. Aşağıdaki örnek, varsayılan `ToString` yöntemi gösterir. Uygulama içermeyen adlı `Automobile` bir sınıfı tanımlar. Sınıf örneği oluşturulduğunda ve `ToString` yöntemi çağrıldığında, tür adını görüntüler. `ToString` Yöntemin örnekte açıkça çağrılmadığını unutmayın. Yöntemi örtük olarak kendisine bir `ToString` bağımsız değişken olarak geçirilen nesne yöntemini çağırır. <xref:System.Console.WriteLine%28System.Object%29?displayProperty=nameWithType>

[!code-csharp[Conceptual.Formatting.Overview#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/default1.cs#1)]
[!code-vb[Conceptual.Formatting.Overview#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/default1.vb#1)]

> [!WARNING]
> ' Den [!INCLUDE[win81](../../../includes/win81-md.md)]itibaren Windows çalışma zamanı, varsayılan biçimlendirme <xref:Windows.Foundation.IStringable> desteği sağlayan [ıtringable. ToString](xref:Windows.Foundation.IStringable.ToString%2A)adlı tek bir yönteme sahip bir arabirim içerir. Ancak, yönetilen türlerin `IStringable` arabirimi uygulamamalarını öneririz. Daha fazla bilgi için `IStringable` <xref:System.Object.ToString%2A?displayProperty=nameWithType> başvuru sayfasındaki "Windows çalışma zamanı ve arabirim" bölümüne bakın.

Arabirimler dışındaki tüm türler öğesinden <xref:System.Object>türetildiğinden, bu işlev özel sınıflarınıza veya yapılarına otomatik olarak sağlanır. Ancak, varsayılan `ToString` yöntem tarafından sunulan işlevsellik sınırlıdır: Türü tanımlasa da, türün bir örneği hakkında herhangi bir bilgi sağlamaz. Bu nesne hakkında bilgi sağlayan bir nesnenin dize gösterimini sağlamak için, `ToString` yöntemini geçersiz kılmanız gerekir.

> [!NOTE]
> Yapıları öğesinden <xref:System.ValueType>devralınır, bu da öğesinden <xref:System.Object>türetilir. Geçersiz <xref:System.ValueType> kılmalarına <xref:System.Object.ToString%2A?displayProperty=nameWithType>karşın uygulamasının aynı olmasına rağmen.

<a name="OverrideToString"></a>

## <a name="overriding-the-tostring-method"></a>ToString Yöntemini Geçersiz Kılma

Bir türün adının görüntülenmesi genellikle sınırlı kullanıma sahiptir ve türlerinizin tüketicilerinin bir örneği diğerinden ayırt edilmesine izin vermez. Ancak, bir nesnenin değerinin daha `ToString` kullanışlı bir temsilini sağlamak için yöntemini geçersiz kılabilirsiniz. Aşağıdaki örnek, bir `Temperature` nesnesini tanımlar ve, sıcaklığın santigrat derece cinsinden gösterilmesi için `ToString` yöntemini geçersiz kılar.

[!code-csharp[Conceptual.Formatting.Overview#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/overrides1.cs#2)]
[!code-vb[Conceptual.Formatting.Overview#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/overrides1.vb#2)]

.NET sürümünde, `ToString` her ilkel değer türünün yöntemi, nesnenin adının adı yerine bir değerini gösterecek şekilde geçersiz kılındı. Aşağıdaki tabloda her ilkel tür için geçersiz kılma gösterilmektedir. Geçersiz kılınan yöntemlerin çoğu `ToString` yöntemin başka bir aşırı yüklemesini çağırır ve bunu, türü için genel biçimi ve geçerli kültürü temsil eden bir <xref:System.IFormatProvider> nesneyi tanımlayan "G" Biçim belirleyicisi ' ne geçirdiğini unutmayın.

|Tür|ToString geçersiz kılma|
|----------|-----------------------|
|<xref:System.Boolean>|<xref:System.Boolean.TrueString?displayProperty=nameWithType> Ya<xref:System.Boolean.FalseString?displayProperty=nameWithType>da döndürür.|
|<xref:System.Byte>|Geçerli `Byte.ToString("G", NumberFormatInfo.CurrentInfo)` kültür için <xref:System.Byte> değeri biçimlendirmek için çağrılar.|
|<xref:System.Char>|Karakteri dize olarak döndürür.|
|<xref:System.DateTime>|Geçerli `DateTime.ToString("G", DatetimeFormatInfo.CurrentInfo)` kültürün tarih ve saat değerini biçimlendirmek için çağrılar.|
|<xref:System.Decimal>|Geçerli `Decimal.ToString("G", NumberFormatInfo.CurrentInfo)` kültür için <xref:System.Decimal> değeri biçimlendirmek için çağrılar.|
|<xref:System.Double>|Geçerli `Double.ToString("G", NumberFormatInfo.CurrentInfo)` kültür için <xref:System.Double> değeri biçimlendirmek için çağrılar.|
|<xref:System.Int16>|Geçerli `Int16.ToString("G", NumberFormatInfo.CurrentInfo)` kültür için <xref:System.Int16> değeri biçimlendirmek için çağrılar.|
|<xref:System.Int32>|Geçerli `Int32.ToString("G", NumberFormatInfo.CurrentInfo)` kültür için <xref:System.Int32> değeri biçimlendirmek için çağrılar.|
|<xref:System.Int64>|Geçerli `Int64.ToString("G", NumberFormatInfo.CurrentInfo)` kültür için <xref:System.Int64> değeri biçimlendirmek için çağrılar.|
|<xref:System.SByte>|Geçerli `SByte.ToString("G", NumberFormatInfo.CurrentInfo)` kültür için <xref:System.SByte> değeri biçimlendirmek için çağrılar.|
|<xref:System.Single>|Geçerli `Single.ToString("G", NumberFormatInfo.CurrentInfo)` kültür için <xref:System.Single> değeri biçimlendirmek için çağrılar.|
|<xref:System.UInt16>|Geçerli `UInt16.ToString("G", NumberFormatInfo.CurrentInfo)` kültür için <xref:System.UInt16> değeri biçimlendirmek için çağrılar.|
|<xref:System.UInt32>|Geçerli `UInt32.ToString("G", NumberFormatInfo.CurrentInfo)` kültür için <xref:System.UInt32> değeri biçimlendirmek için çağrılar.|
|<xref:System.UInt64>|Geçerli `UInt64.ToString("G", NumberFormatInfo.CurrentInfo)` kültür için <xref:System.UInt64> değeri biçimlendirmek için çağrılar.|

<a name="FormatStrings"></a>

## <a name="the-tostring-method-and-format-strings"></a>ToString Yöntemi ve Biçim Dizeleri

Varsayılan `ToString` yönteme veya geçersiz kılmaya `ToString` bağlı olarak, bir nesnenin tek bir dize gösterimine sahip olması durumunda uygundur. Ancak, bir nesnenin değerinde genellikle birden çok temsili vardır. Örneğin, sıcaklık Fahrenhayt, santigrat veya Kelvin derece olarak ifade edilebilir. Benzer şekilde, 10 tamsayı değeri 10, 10,0, 1.0 E01 veya $10,00 dahil olmak üzere çeşitli yollarla temsil edilebilir.

Tek bir değerin birden çok dize temsillerine sahip olmasını sağlamak için, .NET biçim dizelerini kullanır. Biçim dizesi, bir veya daha fazla önceden tanımlanmış biçim belirticilerini içeren bir dizedir. tek karakter ya da, `ToString` yöntemin çıktısını nasıl biçimlendirmek gerektiğini tanımlayan karakter gruplarıdır. Biçim dizesi daha sonra nesne `ToString` yöntemine bir parametre olarak geçirilir ve bu nesnenin değerinin dize temsilinin nasıl görüntüleneceğini belirler.

.NET 'teki tüm sayısal türler, tarih ve saat türleri ve numaralandırma türleri önceden tanımlanmış bir biçim belirteçleri kümesini destekler. Uygulama tanımlı veri türlerinizin birden fazla dize temsilini tanımlamak için biçim dizelerini de kullanabilirsiniz.

<a name="standardStrings"></a>

### <a name="standard-format-strings"></a>Standart Biçim Dizeleri

Standart bir biçim dizesi, uygulandığı nesnenin dize gösterimini tanımlayan bir alfabetik karakter olan tek bir Biçim belirleyicisi içerir ve bu, içinde kaç basamak gösterileceğini etkileyen isteğe bağlı bir duyarlık belirticisiyle birlikte sonuç dizesi. Duyarlık belirticisi atlanırsa veya desteklenmiyorsa, standart bir biçim belirticisi standart biçim dizesine eşdeğerdir.

.NET, tüm sayısal türler, tüm tarih ve saat türleri ve tüm numaralandırma türleri için standart biçim belirticileri kümesi tanımlar. Örneğin, bu kategorilerin her biri bir "G" standart biçim belirticisini destekler ve bu tür bir değerin genel dize gösterimini tanımlar.

Sabit listesi türleri için standart biçim dizeleri, bir değerin dize temsilini doğrudan denetler. Bir numaralandırma değerinin `ToString` yöntemine geçirilen biçim dizeleri değerin dize adı ("G" ve "F" biçim belirticileri), temel alınan integral değeri ("D" Biçim Belirleyicisi) veya onaltılı değeri ("X") kullanılarak görüntülenip görüntülenmeyeceğini belirleme. "Biçim Belirleyicisi). Aşağıdaki örnek, bir <xref:System.DayOfWeek> sabit listesi değerini biçimlendirmek için standart biçim dizelerinin kullanımını gösterir.

[!code-csharp[Conceptual.Formatting.Overview#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/standard1.cs#4)]
[!code-vb[Conceptual.Formatting.Overview#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/standard1.vb#4)]

Numaralandırma biçim dizeleri hakkında daha fazla bilgi için bkz. [numaralandırma biçim dizeleri](../../../docs/standard/base-types/enumeration-format-strings.md).

Sayısal türler için standart biçim dizeleri, genellikle kesin görünümü bir veya daha fazla özellik değeri tarafından denetlenen bir sonuç dizesi tanımlar. Örneğin, "C" biçim belirticisi bir sayıyı para birimi değeri olarak biçimlendirir. Tek parametre olarak " `ToString` C" biçim belirticisiyle yöntemi çağırdığınızda, geçerli <xref:System.Globalization.NumberFormatInfo> kültürün nesnesinden aşağıdaki özellik değerleri, sayısal değerin dize gösterimini tanımlamak için kullanılır:

- Geçerli kültürün para birimi sembolünü belirten özelliği.<xref:System.Globalization.NumberFormatInfo.CurrencySymbol%2A>

- Aşağıdakileri belirleyen <xref:System.Globalization.NumberFormatInfo.CurrencyPositivePattern%2A> bir tamsayı döndüren veyaözelliği:<xref:System.Globalization.NumberFormatInfo.CurrencyNegativePattern%2A>

  - Para birimi sembolünün yerleşimi.

  - Negatif değerlerin önünde eksi işareti, sondaki eksi işareti veya parantezle gösterilip gösterilmeyeceğini belirtir.

  - Sayısal değer ve para birimi simgesi arasında bir boşluk görünüp görüntülenmediğini belirtir.

- Sonuç dizesindeki kesirli basamakların sayısını tanımlayan özelliği.<xref:System.Globalization.NumberFormatInfo.CurrencyDecimalDigits%2A>

- Sonuç dizesinde ondalık ayırıcı sembolünü tanımlayan özelliği.<xref:System.Globalization.NumberFormatInfo.CurrencyDecimalSeparator%2A>

- Grup ayırıcı sembolünü tanımlayan özelliği.<xref:System.Globalization.NumberFormatInfo.CurrencyGroupSeparator%2A>

- Her bir gruptaki basamakların ondalık basamak sayısını tanımlayan özelliği.<xref:System.Globalization.NumberFormatInfo.CurrencyGroupSizes%2A>

- Parantez negatif değerleri belirtmek için kullanılmazsa, sonuç dizesinde kullanılan negatif işareti belirleyen özelliği.<xref:System.Globalization.NumberFormatInfo.NegativeSign%2A>

Ayrıca, sayısal biçim dizeleri bir duyarlık belirticisi içerebilir. Bu belirticinin anlamı, kullanıldığı biçim dizesine bağlıdır, ancak genellikle sonuç dizesinde görünmesi gereken toplam basamak sayısını veya kesirli basamak sayısını belirtir. Örneğin, aşağıdaki örnek, dört onaltılık basamağa sahip bir dize değeri oluşturmak için "x4" standart sayısal dizesini ve duyarlık belirticisini kullanır.

[!code-csharp[Conceptual.Formatting.Overview#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/precisionspecifier1.cs#6)]
[!code-vb[Conceptual.Formatting.Overview#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/precisionspecifier1.vb#6)]

Standart sayısal biçimlendirme dizeleri hakkında daha fazla bilgi için bkz. [Standart sayısal biçim dizeleri](../../../docs/standard/base-types/standard-numeric-format-strings.md).

Tarih ve saat değerleri için standart biçim dizeleri, belirli <xref:System.Globalization.DateTimeFormatInfo> bir özellik tarafından depolanan özel biçim dizeleri için diğer adlardır. Örneğin, "D" `ToString` biçim belirticisi ile tarih ve saat değerinin yöntemini çağırmak, geçerli <xref:System.Globalization.DateTimeFormatInfo.LongDatePattern%2A?displayProperty=nameWithType> kültürün özelliğinde depolanan özel biçim dizesini kullanarak tarih ve saati gösterir. (Özel biçim dizeleri hakkında daha fazla bilgi için [sonraki bölüme](#customStrings)bakın.) Aşağıdaki örnekte bu ilişki gösterilmektedir.

[!code-csharp[Conceptual.Formatting.Overview#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/alias1.cs#5)]
[!code-vb[Conceptual.Formatting.Overview#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/alias1.vb#5)]

Standart Tarih ve saat biçim dizeleri hakkında daha fazla bilgi için bkz. [Standart Tarih ve saat biçim dizeleri](../../../docs/standard/base-types/standard-date-and-time-format-strings.md).

Ayrıca, nesne `ToString(String)` yöntemi tarafından üretilen uygulama tanımlı bir nesnenin dize temsilini tanımlamak için standart biçim dizelerini de kullanabilirsiniz. Nesnenizin desteklediği belirli standart biçim belirticilerini tanımlayabilir ve bunların büyük/küçük harfe duyarlı olup olmadığını belirleyebilirsiniz. `ToString(String)` Yöntemi uygulamanız aşağıdakileri desteklemelidir:

- Nesnenin bir normal veya ortak biçimini temsil eden bir "G" biçim belirticisi. Nesnenizin `ToString` yönteminin Parametresiz aşırı yüklemesi, `ToString(String)` aşırı yüklemesini çağırmalıdır ve "G" standart biçim dizesine iletmelidir.

- Null başvuruya eşit olan bir Biçim belirleyicisi desteği (`Nothing` Visual Basic). Null başvurusuna eşit olan bir biçim belirticisi "G" biçim belirticisine eşdeğer olarak kabul edilmelidir.

Örneğin, bir `Temperature` sınıf, sıcaklığın derece derece cinsinden dahili olarak depolanmasını sağlayabilir ve `Temperature` nesne değerini santigrat, derece Fahrenhayt ve Kelvin cinsinden temsil etmek için biçim belirticilerini kullanabilir. Aşağıdaki örnek, bir gösterim sağlar.

[!code-csharp[Conceptual.Formatting.Overview#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/appstandard1.cs#7)]
[!code-vb[Conceptual.Formatting.Overview#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/appstandard1.vb#7)]

<a name="customStrings"></a>

### <a name="custom-format-strings"></a>Özel Biçim Dizeleri

Standart biçim dizelerine ek olarak, .NET, hem sayısal değerler hem de tarih ve saat değerleri için özel biçim dizelerini tanımlar. Özel biçim dizesi, bir değerin dize gösterimini tanımlayan bir veya daha fazla özel biçim belirticisinden oluşur. Örneğin, "yyyy/AA/GG SS: DD: ss. ffff t zzz" özel tarih ve saat biçimi dizesi, en-US kültürü için bir tarihi "2008/11/15 07:45:00.0000 P-08:00" biçiminde dize gösterimine dönüştürür. Benzer şekilde, "0000" özel biçim dizesi 12 tamsayı değerini "0012" olarak dönüştürür. Özel biçim dizelerinin tüm listesi için bkz. [özel tarih ve saat biçimi dizeleri](../../../docs/standard/base-types/custom-date-and-time-format-strings.md) ve [özel sayısal biçim dizeleri](../../../docs/standard/base-types/custom-numeric-format-strings.md).

Bir biçim dizesi tek bir özel biçim belirticisinden oluşuyorsa, Biçim belirleyicisi öncesinde% (%) olmalıdır Standart biçim belirticisiyle karışıklık oluşmasını önlemek için simge. Aşağıdaki örnek, belirli bir tarihin ayın tek basamaklı veya iki basamaklı bir sayısını göstermek için "d" özel biçim belirticisini kullanır.

[!code-csharp[Conceptual.Formatting.Overview#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/singlecustom1.cs#8)]
[!code-vb[Conceptual.Formatting.Overview#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/singlecustom1.vb#8)]

Tarih ve saat değerleri için birçok standart biçim dizesi, <xref:System.Globalization.DateTimeFormatInfo> nesnesinin özellikleri tarafından tanımlanan özel biçim dizeleri için diğer adlardır. Özel biçim dizeleri, sayısal değerler veya tarih ve saat değerleri için uygulama tanımlı biçimlendirme sağlamaya yönelik önemli bir esneklik sunar. Birden çok özel biçim belirticilerini tek bir özel biçim dizesinde birleştirerek, hem sayısal değerler hem de tarih ve saat değerleri için kendi özel sonuç dizelerinizi tanımlayabilirsiniz. Aşağıdaki örnek, ay adı, gün ve yıldan sonra parantez içinde haftanın gününü gösteren bir özel biçim dizesi tanımlar.

[!code-csharp[Conceptual.Formatting.Overview#9](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/custom1.cs#9)]
[!code-vb[Conceptual.Formatting.Overview#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/custom1.vb#9)]

Aşağıdaki örnek, alan kodu ile birlikte standart, yedi basamaklı <xref:System.Int64> ABD telefon numarası olarak bir değeri görüntüleyen bir özel biçim dizesi tanımlar.

[!code-csharp[Conceptual.Formatting.Overview#21](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/telnumber1.cs#21)]
[!code-vb[Conceptual.Formatting.Overview#21](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/telnumber1.vb#21)]

Standart biçim dizeleri, uygulama tanımlı türlerinizin çoğu biçimlendirme ihtiyaçlarını genellikle işleyebilir, ancak türlerinizi biçimlendirmek için özel biçim belirticileri de tanımlayabilirsiniz.

<a name="stringRef"></a>

### <a name="format-strings-and-net-types"></a>Biçimlendirme dizeleri ve .NET türleri

Tüm sayısal türler ( <xref:System.Byte> <xref:System.Int64> <xref:System.UInt16> Yani,<xref:System.UInt32>,,,,,, ,,<xref:System.UInt64>, ve <xref:System.Single> <xref:System.Decimal> <xref:System.Double> <xref:System.Int16> <xref:System.Int32> <xref:System.SByte> <xref:System.Numerics.BigInteger>türlerin <xref:System.DateTime>yanı sıra <xref:System.DateTimeOffset> ,<xref:System.Guid>,, ve tüm numaralandırma türleri, biçim dizeleriyle biçimlendirmeyi destekler. <xref:System.TimeSpan> Her tür tarafından desteklenen belirli biçim dizeleri hakkında daha fazla bilgi için aşağıdaki konulara bakın:

|Başlık|Tanım|
|-----------|----------------|
|[Standart Sayısal Biçim Dizeleri](../../../docs/standard/base-types/standard-numeric-format-strings.md)|Sayısal değerlerin yaygın olarak kullanılan dize temsillerini oluşturan standart biçim dizelerini açıklar.|
|[Özel Sayısal Biçim Dizeleri](../../../docs/standard/base-types/custom-numeric-format-strings.md)|Sayısal değerler için uygulamaya özel biçimler oluşturan özel biçim dizelerini açıklar.|
|[Standart Tarih ve Saat Biçim Dizeleri](../../../docs/standard/base-types/standard-date-and-time-format-strings.md)|<xref:System.DateTime> Ve<xref:System.DateTimeOffset> değerlerinin yaygın olarak kullanılan dize temsillerini oluşturan standart biçim dizelerini açıklar.|
|[Özel Tarih ve Saat Biçim Dizeleri](../../../docs/standard/base-types/custom-date-and-time-format-strings.md)|<xref:System.DateTime> Ve<xref:System.DateTimeOffset> değerleri için uygulamaya özel biçimler oluşturan özel biçim dizelerini açıklar.|
|[Standart TimeSpan Biçim Dizeleri](../../../docs/standard/base-types/standard-timespan-format-strings.md)|Zaman aralıklarının yaygın olarak kullanılan dize temsillerini oluşturan standart biçim dizelerini açıklar.|
|[Özel TimeSpan Biçim Dizeleri](../../../docs/standard/base-types/custom-timespan-format-strings.md)|Zaman aralıkları için uygulamaya özel biçimler oluşturan özel biçim dizelerini açıklar.|
|[Sabit Listesi Biçim Dizeleri](../../../docs/standard/base-types/enumeration-format-strings.md)|Numaralandırma değerlerinin dize gösterimlerini oluşturmak için kullanılan standart biçim dizelerini açıklar.|
|<xref:System.Guid.ToString%28System.String%29?displayProperty=nameWithType>|Değerler için <xref:System.Guid> standart biçim dizelerini açıklar.|

<a name="FormatProviders"></a>

## <a name="culture-sensitive-formatting-with-format-providers-and-the-iformatprovider-interface"></a>Biçim Sağlayıcıları ve IFormatProvider Arabirimi ile Kültüre Duyarlı Biçimlendirme

Biçim belirticileri nesnelerin biçimlendirmesini özelleştirmenizi sağlar, ancak nesnelerin anlamlı bir dize gösterimini üretmek genellikle ek biçimlendirme bilgileri gerektirir. Örneğin, "C" standart biçim dizesi veya "$ #, #. 00" gibi özel bir biçim dizesi kullanarak bir sayıyı para birimi değeri olarak biçimlendirmek, en azından doğru para birimi sembolü, Grup ayırıcısı ve ondalık ayırıcısının olması için gereken bilgileri gerektirir biçimlendirilen dizeye dahil etmek için kullanılabilir. .NET sürümünde bu ek biçimlendirme bilgileri, sayısal türler ve Tarih ve <xref:System.IFormatProvider> saat türleri `ToString` yönteminin bir veya daha fazla aşırı yüküne bir parametre olarak sağlanan arabirim aracılığıyla kullanılabilir hale getirilir. <xref:System.IFormatProvider>uygulamalar, .NET 'te kültüre özgü biçimlendirmeyi desteklemek için kullanılır. Aşağıdaki örnek, bir nesnenin dize temsilinin farklı kültürleri temsil eden üç <xref:System.IFormatProvider> nesneyle biçimlendirildiğinde nasıl değiştiği gösterilmektedir.

[!code-csharp[Conceptual.Formatting.Overview#11](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/iformatprovider1.cs#11)]
[!code-vb[Conceptual.Formatting.Overview#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/iformatprovider1.vb#11)]

Arabirim, biçimlendirme bilgileri sağlayan nesne <xref:System.IFormatProvider.GetFormat%28System.Type%29>türünü belirten tek bir parametreye sahip olan bir yöntemini içerir. <xref:System.IFormatProvider> Yöntemi bu türden bir nesne sağlayabiliyorsanız, döndürür. Aksi halde, null bir başvuru döndürür (`Nothing` Visual Basic).

<xref:System.IFormatProvider.GetFormat%2A?displayProperty=nameWithType>bir geri çağırma yöntemidir. Bir `ToString` <xref:System.IFormatProvider> parametreiçeren<xref:System.IFormatProvider.GetFormat%2A> bir yöntem aşırı yüklemesini çağırdığınızda, bu nesnenin yöntemini çağırır. <xref:System.IFormatProvider> Yöntemi, `formatType` parametresi`ToString` tarafından belirtilen gerekli biçimlendirme bilgilerini yöntemine döndüren bir nesne döndürmekten sorumludur. <xref:System.IFormatProvider.GetFormat%2A>

Bir dizi biçimlendirme veya dize dönüştürme yöntemi, türünde <xref:System.IFormatProvider>bir parametre içerir, ancak çoğu durumda, yöntemi çağrıldığında parametresinin değeri yok sayılır. Aşağıdaki tabloda, parametresini kullanan bazı biçimlendirme yöntemleri ve <xref:System.Type> <xref:System.IFormatProvider.GetFormat%2A?displayProperty=nameWithType> yönteme geçirdikleri nesnenin türü listelenmektedir.

|Yöntem|`formatType` Parametrenin türü|
|------------|------------------------------------|
|`ToString`sayısal türlerin yöntemi|<xref:System.Globalization.NumberFormatInfo?displayProperty=nameWithType>|
|`ToString`Tarih ve saat türleri yöntemi|<xref:System.Globalization.DateTimeFormatInfo?displayProperty=nameWithType>|
|<xref:System.String.Format%2A?displayProperty=nameWithType>|<xref:System.ICustomFormatter?displayProperty=nameWithType>|
|<xref:System.Text.StringBuilder.AppendFormat%2A?displayProperty=nameWithType>|<xref:System.ICustomFormatter?displayProperty=nameWithType>|

> [!NOTE]
> Sayısal türlerin ve Tarih ve saat türlerinin <xref:System.IFormatProvider> yöntemleriaşırıyüklenmiştirveyalnızcabazıaşırıyüklemelerinbirparametresivardır.`ToString` Bir yöntemde türünde <xref:System.IFormatProvider>parametre yoksa, bunun yerine <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=nameWithType> özelliği tarafından döndürülen nesne geçirilir. Örneğin, varsayılan <xref:System.Int32.ToString?displayProperty=nameWithType> metoda yapılan bir çağrı sonuç olarak aşağıdaki gibi bir yöntem çağrısıyla sonuçlanır: `Int32.ToString("G", System.Globalization.CultureInfo.CurrentCulture)`.

.NET aşağıdakileri uygulayan <xref:System.IFormatProvider>üç sınıf sağlar:

- <xref:System.Globalization.DateTimeFormatInfo>, belirli bir kültür için tarih ve saat değerleri için biçimlendirme bilgileri sağlayan bir sınıf. <xref:System.IFormatProvider.GetFormat%2A?displayProperty=nameWithType> Uygulamanın kendisi bir örneğini döndürür.

- <xref:System.Globalization.NumberFormatInfo>, belirli bir kültür için sayısal biçimlendirme bilgileri sağlayan bir sınıf. <xref:System.IFormatProvider.GetFormat%2A?displayProperty=nameWithType> Uygulamanın kendisi bir örneğini döndürür.

- <xref:System.Globalization.CultureInfo>. Uygulama <xref:System.IFormatProvider.GetFormat%2A?displayProperty=nameWithType> , tarih ve saat değerleri <xref:System.Globalization.NumberFormatInfo> için biçimlendirme bilgilerini sağlamak üzere <xref:System.Globalization.DateTimeFormatInfo> sayısal biçimlendirme bilgileri veya nesne sağlamak için bir nesne döndürebilir.

Bu sınıfların herhangi birini değiştirmek için kendi biçim sağlayıcınızı de uygulayabilirsiniz. Ancak, uygulamanızın <xref:System.IFormatProvider.GetFormat%2A> yöntemi, `ToString` yönteme biçimlendirme bilgileri sağlaması gerekiyorsa, önceki tabloda listelenen türde bir nesne döndürmelidir.

<a name="numericCulture"></a>

### <a name="culture-sensitive-formatting-of-numeric-values"></a>Sayısal Değerleri Kültüre Duyarlı Olarak Biçimlendirme

Varsayılan olarak, sayısal değer biçimlendirmesi kültüre duyarlıdır. Bir biçimlendirme yöntemini çağırdığınızda bir kültür belirtmezseniz, geçerli iş parçacığı kültürünün biçimlendirme kuralları kullanılır. Bu, geçerli iş parçacığı kültürünü dört kez değiştiren ve sonra <xref:System.Decimal.ToString%28System.String%29?displayProperty=nameWithType> yöntemi çağıran aşağıdaki örnekte gösterilmiştir. Her durumda, sonuç dizesi geçerli kültürün biçimlendirme kurallarını yansıtır. Bunun nedeni, `ToString` ve `ToString(String)` yöntemlerinin her sayısal tür `ToString(String, IFormatProvider)` metoduna çağrı kaydırması.

[!code-csharp[Conceptual.Formatting.Overview#19](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/culturespecific3.cs#19)]
[!code-vb[Conceptual.Formatting.Overview#19](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/culturespecific3.vb#19)]

Ayrıca, bir `ToString` `provider` parametresi olan bir aşırı yüklemeyi çağırarak ve bu parametreyi aşağıdakilerden birini geçirerek belirli bir kültür için sayısal bir değeri biçimlendirebilirsiniz:

- Biçimlendirme kuralları kullanılacak olan kültürü temsil eden nesne.<xref:System.Globalization.CultureInfo> Yöntemi, sayısal değerler için kültüre özgü <xref:System.Globalization.CultureInfo.NumberFormat%2A?displayProperty=nameWithType> biçimlendirme bilgileri sağlayan <xref:System.Globalization.NumberFormatInfo> nesnesi olan özelliğinin değerini döndürür. <xref:System.Globalization.CultureInfo.GetFormat%2A?displayProperty=nameWithType>

- Kullanılacak <xref:System.Globalization.NumberFormatInfo> kültüre özgü biçimlendirme kurallarını tanımlayan bir nesne. <xref:System.Globalization.NumberFormatInfo.GetFormat%2A> Yöntemi kendi örneğini döndürür.

Aşağıdaki örnek, bir <xref:System.Globalization.NumberFormatInfo> kayan noktalı sayıyı biçimlendirmek için İngilizce (Birleşik Devletler) ve İngilizce (Büyük Britanya) kültürlerini ve Fransızca ve Rusça bağımsız kültürlerini temsil eden nesneleri kullanır.

[!code-csharp[Conceptual.Formatting.Overview#20](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/culturespecific4.cs#20)]
[!code-vb[Conceptual.Formatting.Overview#20](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/culturespecific4.vb#20)]

<a name="dateCulture"></a>

### <a name="culture-sensitive-formatting-of-date-and-time-values"></a>Tarih ve Saat Değerlerini Kültüre Duyarlı Olarak Biçimlendirme

Varsayılan olarak, tarih ve saat değerlerinin biçimlendirmesi kültüre duyarlıdır. Bir biçimlendirme yöntemini çağırdığınızda bir kültür belirtmezseniz, geçerli iş parçacığı kültürünün biçimlendirme kuralları kullanılır. Bu, geçerli iş parçacığı kültürünü dört kez değiştiren ve sonra <xref:System.DateTime.ToString%28System.String%29?displayProperty=nameWithType> yöntemi çağıran aşağıdaki örnekte gösterilmiştir. Her durumda, sonuç dizesi geçerli kültürün biçimlendirme kurallarını yansıtır. Bunun nedeni,, <xref:System.DateTime.ToString?displayProperty=nameWithType>ve <xref:System.DateTime.ToString%28System.String%29?displayProperty=nameWithType> <xref:System.DateTime.ToString%28System.String%2CSystem.IFormatProvider%29?displayProperty=nameWithType> <xref:System.DateTimeOffset.ToString?displayProperty=nameWithType> yöntemlerinin<xref:System.DateTimeOffset.ToString%28System.String%29?displayProperty=nameWithType> ve yöntemlerineçağrıları<xref:System.DateTimeOffset.ToString%28System.String%2CSystem.IFormatProvider%29?displayProperty=nameWithType> sarması nedeniyle oluşur.

[!code-csharp[Conceptual.Formatting.Overview#17](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/culturespecific1.cs#17)]
[!code-vb[Conceptual.Formatting.Overview#17](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/culturespecific1.vb#17)]

Ayrıca, bir <xref:System.DateTime.ToString%2A?displayProperty=nameWithType> `provider` parametresi olan bir veya <xref:System.DateTimeOffset.ToString%2A?displayProperty=nameWithType> daha fazla yük çağırarak ve bu parametreyi aşağıdakilerden birini geçirerek belirli bir kültür için bir tarih ve saat değeri biçimlendirebilirsiniz:

- Biçimlendirme kuralları kullanılacak olan kültürü temsil eden nesne.<xref:System.Globalization.CultureInfo> Yöntemi, tarih ve saat değerleri için <xref:System.Globalization.CultureInfo.DateTimeFormat%2A?displayProperty=nameWithType> kültüre özgü biçimlendirme bilgileri sağlayan <xref:System.Globalization.DateTimeFormatInfo> nesnesi olan özelliğinin değerini döndürür. <xref:System.Globalization.CultureInfo.GetFormat%2A?displayProperty=nameWithType>

- Kullanılacak <xref:System.Globalization.DateTimeFormatInfo> kültüre özgü biçimlendirme kurallarını tanımlayan bir nesne. <xref:System.Globalization.DateTimeFormatInfo.GetFormat%2A> Yöntemi kendi örneğini döndürür.

Aşağıdaki örnek, bir <xref:System.Globalization.DateTimeFormatInfo> tarihi biçimlendirmek için İngilizce (Birleşik Devletler) ve İngilizce (Büyük Britanya) kültürlerini ve Fransızca ve Rusça bağımsız kültürlerini temsil eden nesneleri kullanır.

[!code-csharp[Conceptual.Formatting.Overview#18](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/culturespecific2.cs#18)]
[!code-vb[Conceptual.Formatting.Overview#18](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/culturespecific2.vb#18)]

<a name="IFormattable"></a>

## <a name="the-iformattable-interface"></a>IFormattable Arabirimi

Genellikle, `ToString` yöntemi bir biçim dizesi ve bir <xref:System.IFormatProvider> parametre ile aşırı yükleyen türler de <xref:System.IFormattable> arabirimini uygular. Bu arabirimin, parametre olarak hem biçim <xref:System.IFormattable.ToString%28System.String%2CSystem.IFormatProvider%29?displayProperty=nameWithType>dizesi hem de biçim sağlayıcısını içeren tek bir üyesi vardır.

Uygulama tanımlı sınıfınız için arabirimiuygulamakikiavantajsunar:<xref:System.IFormattable>

- <xref:System.Convert> Sınıfı tarafından dize dönüştürme desteği. Ve yöntemlerine yapılan çağrılar <xref:System.IFormattable> uygulamanızı otomatik olarak çağırır. <xref:System.Convert.ToString%28System.Object%2CSystem.IFormatProvider%29?displayProperty=nameWithType> <xref:System.Convert.ToString%28System.Object%29?displayProperty=nameWithType>

- Bileşik biçimlendirme desteği. Özel türünü biçimlendirmek için bir biçim dizesi içeren bir biçim öğesi kullanılırsa, ortak dil çalışma zamanı <xref:System.IFormattable> uygulamanızı otomatik olarak çağırır ve biçim dizesini geçirir. <xref:System.String.Format%2A?displayProperty=nameWithType> Veya<xref:System.Console.WriteLine%2A?displayProperty=nameWithType>gibi yöntemlerle bileşik biçimlendirme hakkında daha fazla bilgi için bkz. [Bileşik biçimlendirme](#CompositeFormatting) bölümü.

Aşağıdaki örnek, <xref:System.IFormattable> arabirimini uygulayan `Temperature` bir sınıfı tanımlar. Sıcaklığın Santide gösterilmesi için "C" veya "G" biçim belirticilerini destekler, sıcaklığın Fahrenolması için "F" biçim belirticisi ve sıcaklığın Kelvin cinsinden gösterilmesi için "K" Biçim belirleyicisi.

[!code-csharp[Conceptual.Formatting.Overview#12](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/iformattable.cs#12)]
[!code-vb[Conceptual.Formatting.Overview#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/iformattable.vb#12)]

Aşağıdaki örnek bir `Temperature` nesnesi başlatır. Daha sonra <xref:System.Convert.ToString%2A> yöntemi çağırır ve bir `Temperature` nesnenin farklı dize gösterimlerini almak için birkaç bileşik biçim dizesi kullanır. Bu yöntem çağrılarının her biri, sırasıyla <xref:System.IFormattable> `Temperature` sınıfının uygulamasını çağırır.

[!code-csharp[Conceptual.Formatting.Overview#13](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/iformattable.cs#13)]
[!code-vb[Conceptual.Formatting.Overview#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/iformattable.vb#13)]

<a name="CompositeFormatting"></a>

## <a name="composite-formatting"></a>Bileşik Biçimlendirme

<xref:System.String.Format%2A?displayProperty=nameWithType> Ve<xref:System.Text.StringBuilder.AppendFormat%2A?displayProperty=nameWithType>gibi bazı yöntemler bileşik biçimlendirmeyi destekler. Bileşik biçim dizesi, sıfır, bir veya daha fazla nesnenin dize gösterimini içeren tek bir dize döndüren bir şablon türüdür. Her nesne, bileşik biçim dizesinde dizinli biçim öğesi tarafından temsil edilir. Biçim öğesinin dizini, yöntemin parametre listesinde temsil ettiği nesnenin konumuna karşılık gelir. Dizinler sıfır tabanlıdır. Örneğin, <xref:System.String.Format%2A?displayProperty=nameWithType> yöntemi için aşağıdaki çağrıda, ilk biçim `{0:D}`öğesi öğesinin `thatDate`dize temsili ile değiştirilmiştir; ikinci biçim öğesi `{1}`, öğesinin `item1`dizetemsiliiledeğiştirilmiştir; ve üçüncü biçim öğesi `{2:C2}`, öğesinin `item1.Value`dize temsili ile değiştirilmiştir.

[!code-csharp[Conceptual.Formatting.Overview#14](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/composite1.cs#14)]
[!code-vb[Conceptual.Formatting.Overview#14](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/composite1.vb#14)]

Bir biçim öğesini karşılık gelen nesnenin dize gösterimiyle değiştirmeye ek olarak, biçim öğeleri de şunları denetlemenize olanak tanır:

- Nesne, <xref:System.IFormattable> arayüzü uygularsa ve biçim dizelerini destekliyorsa, nesnenin dize olarak temsil edildiği belirli bir yoldur. Bunu, `:` (iki nokta üst üste) ve ardından geçerli bir biçim dizesi olan biçim öğesinin dizinini izleyerek yapabilirsiniz. Önceki örnekte bu, bir tarih değerini "d" (kısa tarih düzeniyle) biçim dizesiyle (örn. `{0:d}`) ve sayısal bir değeri "C2" biçim dizesiyle (örn `{2:C2}` . sayıyı iki ile para birimi değeri olarak göstermek için) biçimlendirerek oldu kesirli ondalık basamaklar.

- Nesnenin dize gösterimini içeren alanın genişliği ve bu alandaki dize gösteriminin hizalaması. Bunu, biçim öğesinin dizinini `,` (virgül) ve alan genişliğini izleyerek yapın. Alan genişliği pozitif bir değer ise, dize alana sağa hizalanır ve alan genişliği negatif bir değer ise sola hizalanır. Aşağıdaki örnek, tarih değerlerini 20 karakterlik bir alanda sola hizalar ve ondalık değerleri, 11 karakterlik bir alanda tek bir kesirli basamakla sağa hizalar.

     [!code-csharp[Conceptual.Formatting.Overview#22](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/composite2.cs#22)]
     [!code-vb[Conceptual.Formatting.Overview#22](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/composite2.vb#22)]

     Hizalama dizesi bileşeni ve biçim dizesi bileşeni varsa, ilki ikincinin (örneğin, `{0,-20:g}`) önünde olduğunu unutmayın.

Bileşik biçimlendirme hakkında daha fazla bilgi için bkz. [Bileşik biçimlendirme](../../../docs/standard/base-types/composite-formatting.md).

<a name="Custom"></a>

## <a name="custom-formatting-with-icustomformatter"></a>ICustomFormatter ile Özel Biçimlendirme

İki bileşik biçimlendirme yöntemi <xref:System.String.Format%28System.IFormatProvider%2CSystem.String%2CSystem.Object%5B%5D%29?displayProperty=nameWithType> ve <xref:System.Text.StringBuilder.AppendFormat%28System.IFormatProvider%2CSystem.String%2CSystem.Object%5B%5D%29?displayProperty=nameWithType>, özel biçimlendirmeyi destekleyen bir biçim sağlayıcısı parametresi içerir. Bu biçimlendirme yöntemlerinden herhangi biri çağrıldığında, bir <xref:System.Type> <xref:System.ICustomFormatter> arabirimi temsil eden bir nesneyi biçim sağlayıcısının <xref:System.IFormatProvider.GetFormat%2A> yöntemine geçirir. Yöntemi, daha sonra özel biçimlendirme sağlayan <xref:System.ICustomFormatter> uygulamanın döndürülmesinden sorumludur. <xref:System.IFormatProvider.GetFormat%2A>

Arabirim, bileşik biçimlendirme yöntemi tarafından otomatik <xref:System.ICustomFormatter.Format%28System.String%2CSystem.Object%2CSystem.IFormatProvider%29>olarak çağrılan tek bir yönteme sahiptir ve bir bileşik biçim dizesindeki her biçim öğesi için bir kez. <xref:System.ICustomFormatter> Yöntemi üç parametreye sahiptir: bir biçim öğesinde `formatString` bağımsız değişkeni temsil eden bir biçim dizesi, biçimlendirilecek bir nesne ve <xref:System.IFormatProvider> biçimlendirme hizmetleri sağlayan bir nesne. <xref:System.ICustomFormatter.Format%28System.String%2CSystem.Object%2CSystem.IFormatProvider%29> Genellikle, uygulayan <xref:System.ICustomFormatter> sınıf de uygular <xref:System.IFormatProvider>, bu nedenle bu son parametre özel biçimlendirme sınıfının kendisi için bir başvurudur. Yöntemi, biçimlendirilecek nesnenin özel bir biçimli dize gösterimini döndürür. Yöntem nesneyi biçimlendiremiyor ise, null bir başvuru döndürmelidir (`Nothing` Visual Basic).

Aşağıdaki örnek, tam sayı <xref:System.ICustomFormatter> değerlerini bir `ByteByByteFormatter` boşluk ile izleyen iki basamaklı onaltılık değerlerin bir sırası olarak görüntüleyen adlı bir uygulama sağlar.

[!code-csharp[Conceptual.Formatting.Overview#15](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/icustomformatter1.cs#15)]
[!code-vb[Conceptual.Formatting.Overview#15](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/icustomformatter1.vb#15)]

Aşağıdaki örnek, tamsayı değerlerini `ByteByByteFormatter` biçimlendirmek için sınıfını kullanır. Yöntemin ikinci <xref:System.String.Format%28System.IFormatProvider%2CSystem.String%2CSystem.Object%5B%5D%29?displayProperty=nameWithType> Yöntem çağrısında birden çok kez çağrıldığını ve varsayılan <xref:System.Globalization.NumberFormatInfo> sağlayıcının üçüncü yöntem çağrısında kullanıldığını unutmayın, çünkü. <xref:System.ICustomFormatter.Format%2A?displayProperty=nameWithType>`ByteByByteFormatter.Format` Yöntem, "N0" biçim dizesini tanımıyor ve null bir başvuru döndürüyor (`Nothing` Visual Basic).

[!code-csharp[Conceptual.Formatting.Overview#16](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/icustomformatter1.cs#16)]
[!code-vb[Conceptual.Formatting.Overview#16](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/icustomformatter1.vb#16)]

<a name="RelatedTopics"></a>

## <a name="related-topics"></a>İlgili Konular

|Başlık|Tanım|
|-----------|----------------|
|[Standart Sayısal Biçim Dizeleri](../../../docs/standard/base-types/standard-numeric-format-strings.md)|Sayısal değerlerin yaygın olarak kullanılan dize temsillerini oluşturan standart biçim dizelerini açıklar.|
|[Özel Sayısal Biçim Dizeleri](../../../docs/standard/base-types/custom-numeric-format-strings.md)|Sayısal değerler için uygulamaya özel biçimler oluşturan özel biçim dizelerini açıklar.|
|[Standart Tarih ve Saat Biçim Dizeleri](../../../docs/standard/base-types/standard-date-and-time-format-strings.md)|<xref:System.DateTime> Değerlerin yaygın olarak kullanılan dize temsillerini oluşturan standart biçim dizelerini açıklar.|
|[Özel Tarih ve Saat Biçim Dizeleri](../../../docs/standard/base-types/custom-date-and-time-format-strings.md)|Değerler için <xref:System.DateTime> uygulamaya özel biçimler oluşturan özel biçim dizelerini açıklar.|
|[Standart TimeSpan Biçim Dizeleri](../../../docs/standard/base-types/standard-timespan-format-strings.md)|Zaman aralıklarının yaygın olarak kullanılan dize temsillerini oluşturan standart biçim dizelerini açıklar.|
|[Özel TimeSpan Biçim Dizeleri](../../../docs/standard/base-types/custom-timespan-format-strings.md)|Zaman aralıkları için uygulamaya özel biçimler oluşturan özel biçim dizelerini açıklar.|
|[Sabit Listesi Biçim Dizeleri](../../../docs/standard/base-types/enumeration-format-strings.md)|Numaralandırma değerlerinin dize gösterimlerini oluşturmak için kullanılan standart biçim dizelerini açıklar.|
|[Bileşik Biçimlendirme](../../../docs/standard/base-types/composite-formatting.md)|Bir veya daha fazla biçimli değerin bir dizeye nasıl ekleneceğini açıklar. Dize daha sonra konsolda görüntülenebilir veya bir akışa yazılabilir.|
|[Biçimlendirme İşlemlerini Gerçekleştirme](../../../docs/standard/base-types/performing-formatting-operations.md)|Belirli biçimlendirme işlemlerini gerçekleştirmeye yönelik adım adım yönergeler sağlayan konuları listeler.|
|[Dizeleri Ayrıştırma](../../../docs/standard/base-types/parsing-strings.md)|Nesnelerin, bu nesnelerin dize temsilleri tarafından tanımlanan değerlere nasıl başlatılacağını açıklar. Ayrıştırma biçimlendirmenin ters işlemidir.|

<a name="Reference"></a>

## <a name="reference"></a>Başvuru

- <xref:System.IFormattable?displayProperty=nameWithType>
- <xref:System.IFormatProvider?displayProperty=nameWithType>
- <xref:System.ICustomFormatter?displayProperty=nameWithType>
