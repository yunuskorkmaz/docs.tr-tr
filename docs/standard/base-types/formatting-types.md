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
ms.openlocfilehash: e63a0962efb689a865436df771420e92319110b5
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84290545"
---
# <a name="format-types-in-net"></a>.NET 'teki biçim türleri

Biçimlendirme, bir sınıf, yapı veya numaralandırma değerinin bir örneğini dize gösterimine dönüştürme işlemidir. böylece, sonuçta elde edilen dize kullanıcılara görüntülenebilir veya orijinal veri türünü geri yüklemek için seri durumdan çıkarılmış olur. Bu dönüştürme bir dizi zorluklara neden olabilir:

- Değerlerin dahili olarak depolandığı yol, kullanıcıların bunları görüntülemek istedikleri yöntemi göstermez. Örneğin, bir telefon numarası, Kullanıcı dostu olmayan 8009999999 biçiminde depolanabilir. Bunun yerine 800-999-9999 olarak gösterilmesi gerekir. Bu şekilde bir sayıyı biçimlendiren bir örnek için [özel biçim dizeleri](#custom-format-strings) bölümüne bakın.

- Bazen bir nesnenin dize gösterimine dönüştürülmesi sezgisel değildir. Örneğin, bir sıcaklık nesnesinin veya bir kişi nesnesinin dize gösteriminin nasıl görünmesi net değildir. Bir sıcaklık nesnesini çeşitli yollarla biçimlendiren bir örnek için bkz. [standart biçim dizeleri](#standard-format-strings) bölümü.

- Değerler genellikle kültüre duyarlı biçimlendirme gerektirir. Örneğin, parasal değerleri yansıtmak için sayı kullanan bir uygulamada, sayısal dizeler geçerli kültürün para birimi simgesini, Grup ayırıcısını (çoğu kültürde, binlerce ayırıcıdır) ve ondalık sembolünü içermelidir. Bir örnek için, [biçim sağlayıcıları Ile kültüre duyarlı biçimlendirme](#culture-sensitive-formatting-with-format-providers) bölümüne bakın.

- Uygulamanın aynı değeri farklı şekillerde görüntülemesi gerekebilir. Örneğin, bir uygulama, adının bir dize gösterimini görüntüleyerek veya onun temel aldığı değerini görüntüleyerek bir numaralandırma üyesini temsil edebilir. Sabit listesinin bir üyesini farklı yollarla biçimlendiren bir örnek için <xref:System.DayOfWeek> bkz. [standart biçim dizeleri](#standard-format-strings) bölümü.

> [!NOTE]
> Biçimlendirme bir türün değerini dize temsiline dönüştürür. Ayrıştırma biçimlendirmenin tersidir. Bir ayrıştırma işlemi, dize gösteriminden bir veri türü örneği oluşturur. Dizeleri diğer veri türlerine dönüştürme hakkında daha fazla bilgi için bkz. [dizeleri ayrıştırma](parsing-strings.md).

.NET, geliştiricilerin bu gereksinimleri ele almasını sağlayan zengin biçimlendirme desteği sağlar.

## <a name="formatting-in-net"></a>.NET 'te biçimlendirme

Biçimlendirme için temel mekanizma, <xref:System.Object.ToString%2A?displayProperty=nameWithType> Bu konunun ilerleyen kısımlarında yer olarak [ToString yöntemi kullanılarak varsayılan biçimlendirme ile](#default-formatting-using-the-tostring-method) bahsedilen yöntemin varsayılan uygulamasıdır. Ancak .NET, varsayılan biçimlendirme desteğini değiştirmek ve genişletmek için çeşitli yollar sunar. Bunlar aşağıdakileri içerir:

- <xref:System.Object.ToString%2A?displayProperty=nameWithType>Bir nesnenin değerinin özel bir dize gösterimini tanımlamak için yöntemini geçersiz kılma. Daha fazla bilgi için bu konunun ilerleyen kısımlarındaki [ToString yöntemini geçersiz kılma](#override-the-tostring-method) bölümüne bakın.

- Bir nesnenin değerinin dize gösterimine birden çok form geçirmesine imkan tanıyan biçim belirticileri tanımlama. Örneğin, aşağıdaki deyimdeki "X" Biçim belirleyicisi bir tamsayıyı onaltılık bir değerin dize gösterimine dönüştürür.

     [!code-csharp[Conceptual.Formatting.Overview#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/specifier1.cs#3)]
     [!code-vb[Conceptual.Formatting.Overview#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/specifier1.vb#3)]

     Biçim belirticileri hakkında daha fazla bilgi için bkz. [ToString yöntemi ve biçim dizeleri](#the-tostring-method-and-format-strings) bölümü.

- Belirli bir kültürün biçimlendirme kurallarından yararlanmak için biçim sağlayıcıları kullanma. Örneğin, aşağıdaki ifade, en-US kültürün biçimlendirme kurallarını kullanarak bir para birimi değeri görüntüler.

     [!code-csharp[Conceptual.Formatting.Overview#10](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/specifier1.cs#10)]
     [!code-vb[Conceptual.Formatting.Overview#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/specifier1.vb#10)]

     Biçim sağlayıcılarıyla biçimlendirme hakkında daha fazla bilgi için, [biçim sağlayıcıları](#culture-sensitive-formatting-with-format-providers) bölümüne bakın.

- <xref:System.IFormattable>Hem <xref:System.Convert> sınıf hem de bileşik biçimlendirme ile dize dönüştürmeyi desteklemek için arabirimini uygulama. Daha fazla bilgi için [IFormattable arabirimi](#the-iformattable-interface) bölümüne bakın.

- Daha büyük bir dizedeki bir değerin dize gösterimini katıştırmak için bileşik biçimlendirme kullanma. Daha fazla bilgi için [Bileşik biçimlendirme](#composite-formatting) bölümüne bakın.

- <xref:System.ICustomFormatter> <xref:System.IFormatProvider> Tüm özel biçimlendirme çözümünü sağlamak ve uygulamak. Daha fazla bilgi için [ıccustomformatter Ile özel biçimlendirme](#custom-formatting-with-icustomformatter) bölümüne bakın.

Aşağıdaki bölümlerde, bir nesneyi dize gösterimine dönüştürmeye yönelik bu yöntemler incelenmekte.

## <a name="default-formatting-using-the-tostring-method"></a>ToString yöntemini kullanarak varsayılan biçimlendirme

Öğesinden türetilen her tür, <xref:System.Object?displayProperty=nameWithType> Varsayılan olarak türün adını döndüren parametresiz bir yöntemi otomatik olarak devralır `ToString` . Aşağıdaki örnek, varsayılan yöntemi gösterir `ToString` . Uygulama içermeyen adlı bir sınıfı tanımlar `Automobile` . Sınıf örneği oluşturulduğunda ve `ToString` yöntemi çağrıldığında, tür adını görüntüler. `ToString`Yöntemin örnekte açıkça çağrılmadığını unutmayın. <xref:System.Console.WriteLine%28System.Object%29?displayProperty=nameWithType>Yöntemi örtük olarak `ToString` kendisine bir bağımsız değişken olarak geçirilen nesne yöntemini çağırır.

[!code-csharp[Conceptual.Formatting.Overview#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/default1.cs#1)]
[!code-vb[Conceptual.Formatting.Overview#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/default1.vb#1)]

> [!WARNING]
> Windows 8.1 başlayarak, Windows Çalışma Zamanı, <xref:Windows.Foundation.IStringable> varsayılan biçimlendirme desteği sağlayan [ıtringable. ToString](xref:Windows.Foundation.IStringable.ToString%2A)adlı tek bir yönteme sahip bir arabirim içerir. Ancak, yönetilen türlerin arabirimi uygulamamalarını öneririz `IStringable` . Daha fazla bilgi için başvuru sayfasındaki "Windows Çalışma Zamanı ve `IStringable` arabirim" bölümüne bakın <xref:System.Object.ToString%2A?displayProperty=nameWithType> .

Arabirimler dışındaki tüm türler öğesinden türetildiğinden <xref:System.Object> , bu işlev özel sınıflarınıza veya yapılarına otomatik olarak sağlanır. Ancak, varsayılan yöntem tarafından sunulan işlevsellik `ToString` sınırlıdır: türü tanımlasa da, türün bir örneği hakkında herhangi bir bilgi sağlamaz. Bu nesne hakkında bilgi sağlayan bir nesnenin dize gösterimini sağlamak için, yöntemini geçersiz kılmanız gerekir `ToString` .

> [!NOTE]
> Yapıları öğesinden devralınır <xref:System.ValueType> , bu da öğesinden türetilir <xref:System.Object> . <xref:System.ValueType>Geçersiz kılmalarına karşın <xref:System.Object.ToString%2A?displayProperty=nameWithType> uygulamasının aynı olmasına rağmen.

## <a name="override-the-tostring-method"></a>ToString yöntemini geçersiz kılma

Bir türün adının görüntülenmesi genellikle sınırlı kullanıma sahiptir ve türlerinizin tüketicilerinin bir örneği diğerinden ayırt edilmesine izin vermez. Ancak, `ToString` bir nesnenin değerinin daha kullanışlı bir temsilini sağlamak için yöntemini geçersiz kılabilirsiniz. Aşağıdaki örnek, bir `Temperature` nesnesini tanımlar ve, `ToString` sıcaklığın santigrat derece cinsinden gösterilmesi için yöntemini geçersiz kılar.

[!code-csharp[Conceptual.Formatting.Overview#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/overrides1.cs#2)]
[!code-vb[Conceptual.Formatting.Overview#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/overrides1.vb#2)]

.NET sürümünde, `ToString` her ilkel değer türünün yöntemi, nesnenin adının adı yerine bir değerini gösterecek şekilde geçersiz kılındı. Aşağıdaki tabloda her ilkel tür için geçersiz kılma gösterilmektedir. Geçersiz kılınan yöntemlerin çoğu yöntemin başka bir aşırı yüklemesini çağırır `ToString` ve bunu, türü için genel biçimi ve <xref:System.IFormatProvider> geçerli kültürü temsil eden bir nesneyi tanımlayan "G" Biçim belirleyicisi ' ne geçirdiğini unutmayın.

|Tür|ToString geçersiz kılma|
|----------|-----------------------|
|<xref:System.Boolean>|Ya da <xref:System.Boolean.TrueString?displayProperty=nameWithType> döndürür <xref:System.Boolean.FalseString?displayProperty=nameWithType> .|
|<xref:System.Byte>|`Byte.ToString("G", NumberFormatInfo.CurrentInfo)` <xref:System.Byte> Geçerli kültür için değeri biçimlendirmek için çağrılar.|
|<xref:System.Char>|Karakteri dize olarak döndürür.|
|<xref:System.DateTime>|`DateTime.ToString("G", DatetimeFormatInfo.CurrentInfo)`Geçerli kültürün tarih ve saat değerini biçimlendirmek için çağrılar.|
|<xref:System.Decimal>|`Decimal.ToString("G", NumberFormatInfo.CurrentInfo)` <xref:System.Decimal> Geçerli kültür için değeri biçimlendirmek için çağrılar.|
|<xref:System.Double>|`Double.ToString("G", NumberFormatInfo.CurrentInfo)` <xref:System.Double> Geçerli kültür için değeri biçimlendirmek için çağrılar.|
|<xref:System.Int16>|`Int16.ToString("G", NumberFormatInfo.CurrentInfo)` <xref:System.Int16> Geçerli kültür için değeri biçimlendirmek için çağrılar.|
|<xref:System.Int32>|`Int32.ToString("G", NumberFormatInfo.CurrentInfo)` <xref:System.Int32> Geçerli kültür için değeri biçimlendirmek için çağrılar.|
|<xref:System.Int64>|`Int64.ToString("G", NumberFormatInfo.CurrentInfo)` <xref:System.Int64> Geçerli kültür için değeri biçimlendirmek için çağrılar.|
|<xref:System.SByte>|`SByte.ToString("G", NumberFormatInfo.CurrentInfo)` <xref:System.SByte> Geçerli kültür için değeri biçimlendirmek için çağrılar.|
|<xref:System.Single>|`Single.ToString("G", NumberFormatInfo.CurrentInfo)` <xref:System.Single> Geçerli kültür için değeri biçimlendirmek için çağrılar.|
|<xref:System.UInt16>|`UInt16.ToString("G", NumberFormatInfo.CurrentInfo)` <xref:System.UInt16> Geçerli kültür için değeri biçimlendirmek için çağrılar.|
|<xref:System.UInt32>|`UInt32.ToString("G", NumberFormatInfo.CurrentInfo)` <xref:System.UInt32> Geçerli kültür için değeri biçimlendirmek için çağrılar.|
|<xref:System.UInt64>|`UInt64.ToString("G", NumberFormatInfo.CurrentInfo)` <xref:System.UInt64> Geçerli kültür için değeri biçimlendirmek için çağrılar.|

## <a name="the-tostring-method-and-format-strings"></a>ToString yöntemi ve biçim dizeleri

Varsayılan `ToString` yönteme veya geçersiz kılmaya bağlı `ToString` olarak, bir nesnenin tek bir dize gösterimine sahip olması durumunda uygundur. Ancak, bir nesnenin değerinde genellikle birden çok temsili vardır. Örneğin, sıcaklık Fahrenhayt, santigrat veya Kelvin derece olarak ifade edilebilir. Benzer şekilde, 10 tamsayı değeri 10, 10,0, 1.0 E01 veya $10,00 dahil olmak üzere çeşitli yollarla temsil edilebilir.

Tek bir değerin birden çok dize temsillerine sahip olmasını sağlamak için, .NET biçim dizelerini kullanır. Biçim dizesi, bir veya daha fazla önceden tanımlanmış biçim belirticilerini içeren bir dizedir. tek karakter ya da, `ToString` yöntemin çıktısını nasıl biçimlendirmek gerektiğini tanımlayan karakter gruplarıdır. Biçim dizesi daha sonra nesne yöntemine bir parametre olarak geçirilir `ToString` ve bu nesnenin değerinin dize temsilinin nasıl görüntüleneceğini belirler.

.NET 'teki tüm sayısal türler, tarih ve saat türleri ve numaralandırma türleri önceden tanımlanmış bir biçim belirteçleri kümesini destekler. Uygulama tanımlı veri türlerinizin birden fazla dize temsilini tanımlamak için biçim dizelerini de kullanabilirsiniz.

### <a name="standard-format-strings"></a>Standart biçim dizeleri

Standart bir biçim dizesi, uygulandığı nesnenin dize gösterimini tanımlayan bir alfabetik karakter olan tek bir Biçim belirleyicisi içerir ve sonuç dizesinde kaç basamak gösterileceğini etkileyen isteğe bağlı bir duyarlık belirticisiyle birlikte. Duyarlık belirticisi atlanırsa veya desteklenmiyorsa, standart bir biçim belirticisi standart biçim dizesine eşdeğerdir.

.NET, tüm sayısal türler, tüm tarih ve saat türleri ve tüm numaralandırma türleri için standart biçim belirticileri kümesi tanımlar. Örneğin, bu kategorilerin her biri bir "G" standart biçim belirticisini destekler ve bu tür bir değerin genel dize gösterimini tanımlar.

Sabit listesi türleri için standart biçim dizeleri, bir değerin dize temsilini doğrudan denetler. Bir numaralandırma değerinin yöntemine geçirilen biçim dizeleri `ToString` değerin dize adı ("G" ve "F" biçim belirticileri), temel alınan integral değeri ("D" Biçim Belirleyicisi) veya onaltılı değeri ("X" Biçim Belirleyicisi) kullanılarak görüntülenip görüntülenmeyeceğini belirtir. Aşağıdaki örnek, bir sabit listesi değerini biçimlendirmek için standart biçim dizelerinin kullanımını gösterir <xref:System.DayOfWeek> .

[!code-csharp[Conceptual.Formatting.Overview#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/standard1.cs#4)]
[!code-vb[Conceptual.Formatting.Overview#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/standard1.vb#4)]

Numaralandırma biçim dizeleri hakkında daha fazla bilgi için bkz. [numaralandırma biçim dizeleri](enumeration-format-strings.md).

Sayısal türler için standart biçim dizeleri, genellikle kesin görünümü bir veya daha fazla özellik değeri tarafından denetlenen bir sonuç dizesi tanımlar. Örneğin, "C" biçim belirticisi bir sayıyı para birimi değeri olarak biçimlendirir. `ToString`Tek parametre olarak "C" biçim belirticisiyle yöntemi çağırdığınızda, geçerli kültürün nesnesinden aşağıdaki özellik değerleri, <xref:System.Globalization.NumberFormatInfo> sayısal değerin dize gösterimini tanımlamak için kullanılır:

- <xref:System.Globalization.NumberFormatInfo.CurrencySymbol%2A>Geçerli kültürün para birimi sembolünü belirten özelliği.

- <xref:System.Globalization.NumberFormatInfo.CurrencyNegativePattern%2A> <xref:System.Globalization.NumberFormatInfo.CurrencyPositivePattern%2A> Aşağıdakileri belirleyen bir tamsayı döndüren veya özelliği:

  - Para birimi sembolünün yerleşimi.

  - Negatif değerlerin önünde eksi işareti, sondaki eksi işareti veya parantezle gösterilip gösterilmeyeceğini belirtir.

  - Sayısal değer ve para birimi simgesi arasında bir boşluk görünüp görüntülenmediğini belirtir.

- <xref:System.Globalization.NumberFormatInfo.CurrencyDecimalDigits%2A>Sonuç dizesindeki kesirli basamakların sayısını tanımlayan özelliği.

- <xref:System.Globalization.NumberFormatInfo.CurrencyDecimalSeparator%2A>Sonuç dizesinde ondalık ayırıcı sembolünü tanımlayan özelliği.

- <xref:System.Globalization.NumberFormatInfo.CurrencyGroupSeparator%2A>Grup ayırıcı sembolünü tanımlayan özelliği.

- <xref:System.Globalization.NumberFormatInfo.CurrencyGroupSizes%2A>Her bir gruptaki basamakların ondalık basamak sayısını tanımlayan özelliği.

- <xref:System.Globalization.NumberFormatInfo.NegativeSign%2A>Parantez negatif değerleri belirtmek için kullanılmazsa, sonuç dizesinde kullanılan negatif işareti belirleyen özelliği.

Ayrıca, sayısal biçim dizeleri bir duyarlık belirticisi içerebilir. Bu belirticinin anlamı, kullanıldığı biçim dizesine bağlıdır, ancak genellikle sonuç dizesinde görünmesi gereken toplam basamak sayısını veya kesirli basamak sayısını belirtir. Örneğin, aşağıdaki örnek, dört onaltılık basamağa sahip bir dize değeri oluşturmak için "x4" standart sayısal dizesini ve duyarlık belirticisini kullanır.

[!code-csharp[Conceptual.Formatting.Overview#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/precisionspecifier1.cs#6)]
[!code-vb[Conceptual.Formatting.Overview#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/precisionspecifier1.vb#6)]

Standart sayısal biçimlendirme dizeleri hakkında daha fazla bilgi için bkz. [Standart sayısal biçim dizeleri](standard-numeric-format-strings.md).

Tarih ve saat değerleri için standart biçim dizeleri, belirli bir özellik tarafından depolanan özel biçim dizeleri için diğer adlardır <xref:System.Globalization.DateTimeFormatInfo> . Örneğin, `ToString` "D" biçim belirticisi ile tarih ve saat değerinin yöntemini çağırmak, geçerli kültürün özelliğinde depolanan özel biçim dizesini kullanarak tarih ve saati gösterir <xref:System.Globalization.DateTimeFormatInfo.LongDatePattern%2A?displayProperty=nameWithType> . (Özel biçim dizeleri hakkında daha fazla bilgi için [sonraki bölüme](#custom-format-strings)bakın.) Aşağıdaki örnekte bu ilişki gösterilmektedir.

[!code-csharp[Conceptual.Formatting.Overview#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/alias1.cs#5)]
[!code-vb[Conceptual.Formatting.Overview#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/alias1.vb#5)]

Standart Tarih ve saat biçim dizeleri hakkında daha fazla bilgi için bkz. [Standart Tarih ve saat biçim dizeleri](standard-date-and-time-format-strings.md).

Ayrıca, nesne yöntemi tarafından üretilen uygulama tanımlı bir nesnenin dize temsilini tanımlamak için standart biçim dizelerini de kullanabilirsiniz `ToString(String)` . Nesnenizin desteklediği belirli standart biçim belirticilerini tanımlayabilir ve bunların büyük/küçük harfe duyarlı olup olmadığını belirleyebilirsiniz. `ToString(String)`Yöntemi uygulamanız aşağıdakileri desteklemelidir:

- Nesnenin bir normal veya ortak biçimini temsil eden bir "G" biçim belirticisi. Nesnenizin yönteminin Parametresiz aşırı yüklemesi, `ToString` `ToString(String)` aşırı yüklemesini çağırmalıdır ve "G" standart biçim dizesine iletmelidir.

- Null başvuruya eşit olan bir Biçim belirleyicisi desteği ( `Nothing` Visual Basic). Null başvurusuna eşit olan bir biçim belirticisi "G" biçim belirticisine eşdeğer olarak kabul edilmelidir.

Örneğin, bir `Temperature` sınıf, sıcaklığın derece derece cinsinden dahili olarak depolanmasını sağlayabilir ve `Temperature` nesne değerini santigrat, derece Fahrenhayt ve Kelvin cinsinden temsil etmek için biçim belirticilerini kullanabilir. Aşağıdaki örnek, bir gösterim sağlar.

[!code-csharp[Conceptual.Formatting.Overview#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/appstandard1.cs#7)]
[!code-vb[Conceptual.Formatting.Overview#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/appstandard1.vb#7)]

### <a name="custom-format-strings"></a>Özel biçim dizeleri

Standart biçim dizelerine ek olarak, .NET, hem sayısal değerler hem de tarih ve saat değerleri için özel biçim dizelerini tanımlar. Özel biçim dizesi, bir değerin dize gösterimini tanımlayan bir veya daha fazla özel biçim belirticisinden oluşur. Örneğin, "yyyy/AA/GG SS: DD: ss. ffff t zzz" özel tarih ve saat biçimi dizesi, en-US kültürü için bir tarihi "2008/11/15 07:45:00.0000 P-08:00" biçiminde dize gösterimine dönüştürür. Benzer şekilde, "0000" özel biçim dizesi 12 tamsayı değerini "0012" olarak dönüştürür. Özel biçim dizelerinin tüm listesi için bkz. [özel tarih ve saat biçimi dizeleri](custom-date-and-time-format-strings.md) ve [özel sayısal biçim dizeleri](custom-numeric-format-strings.md).

Bir biçim dizesi tek bir özel biçim belirticisinden oluşuyorsa, Biçim belirleyicisi öncesinde% (%) olmalıdır Standart biçim belirticisiyle karışıklık oluşmasını önlemek için simge. Aşağıdaki örnek, belirli bir tarihin ayın tek basamaklı veya iki basamaklı bir sayısını göstermek için "d" özel biçim belirticisini kullanır.

[!code-csharp[Conceptual.Formatting.Overview#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/singlecustom1.cs#8)]
[!code-vb[Conceptual.Formatting.Overview#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/singlecustom1.vb#8)]

Tarih ve saat değerleri için birçok standart biçim dizesi, nesnesinin özellikleri tarafından tanımlanan özel biçim dizeleri için diğer adlardır <xref:System.Globalization.DateTimeFormatInfo> . Özel biçim dizeleri, sayısal değerler veya tarih ve saat değerleri için uygulama tanımlı biçimlendirme sağlamaya yönelik önemli bir esneklik sunar. Birden çok özel biçim belirticilerini tek bir özel biçim dizesinde birleştirerek, hem sayısal değerler hem de tarih ve saat değerleri için kendi özel sonuç dizelerinizi tanımlayabilirsiniz. Aşağıdaki örnek, ay adı, gün ve yıldan sonra parantez içinde haftanın gününü gösteren bir özel biçim dizesi tanımlar.

[!code-csharp[Conceptual.Formatting.Overview#9](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/custom1.cs#9)]
[!code-vb[Conceptual.Formatting.Overview#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/custom1.vb#9)]

Aşağıdaki örnek, <xref:System.Int64> alan kodu ile birlikte standart, yedi basamaklı ABD telefon numarası olarak bir değeri görüntüleyen bir özel biçim dizesi tanımlar.

[!code-csharp[Conceptual.Formatting.Overview#21](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/telnumber1.cs#21)]
[!code-vb[Conceptual.Formatting.Overview#21](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/telnumber1.vb#21)]

Standart biçim dizeleri, uygulama tanımlı türlerinizin çoğu biçimlendirme ihtiyaçlarını genellikle işleyebilir, ancak türlerinizi biçimlendirmek için özel biçim belirticileri de tanımlayabilirsiniz.

### <a name="format-strings-and-net-types"></a>Biçimlendirme dizeleri ve .NET türleri

Tüm sayısal türler (yani,,,,,,,,,,, <xref:System.Byte> <xref:System.Decimal> <xref:System.Double> <xref:System.Int16> <xref:System.Int32> <xref:System.Int64> <xref:System.SByte> <xref:System.Single> <xref:System.UInt16> <xref:System.UInt32> <xref:System.UInt64> ve <xref:System.Numerics.BigInteger> türleri),,,, <xref:System.DateTime> <xref:System.DateTimeOffset> <xref:System.TimeSpan> <xref:System.Guid> ve tüm numaralandırma türleri, biçim dizeleriyle biçimlendirmeyi destekler. Her tür tarafından desteklenen belirli biçim dizeleri hakkında daha fazla bilgi için aşağıdaki konulara bakın:

|Başlık|Tanım|
|-----------|----------------|
|[Standart sayısal biçim dizeleri](standard-numeric-format-strings.md)|Sayısal değerlerin yaygın olarak kullanılan dize temsillerini oluşturan standart biçim dizelerini açıklar.|
|[Özel sayısal biçim dizeleri](custom-numeric-format-strings.md)|Sayısal değerler için uygulamaya özel biçimler oluşturan özel biçim dizelerini açıklar.|
|[Standart Tarih ve saat biçim dizeleri](standard-date-and-time-format-strings.md)|Ve değerlerinin yaygın olarak kullanılan dize temsillerini oluşturan standart biçim dizelerini açıklar <xref:System.DateTime> <xref:System.DateTimeOffset> .|
|[Özel tarih ve saat biçim dizeleri](custom-date-and-time-format-strings.md)|Ve değerleri için uygulamaya özel biçimler oluşturan özel biçim dizelerini açıklar <xref:System.DateTime> <xref:System.DateTimeOffset> .|
|[Standart TimeSpan Biçim dizeleri](standard-timespan-format-strings.md)|Zaman aralıklarının yaygın olarak kullanılan dize temsillerini oluşturan standart biçim dizelerini açıklar.|
|[Özel TimeSpan Biçim dizeleri](custom-timespan-format-strings.md)|Zaman aralıkları için uygulamaya özel biçimler oluşturan özel biçim dizelerini açıklar.|
|[Sabit listesi biçim dizeleri](enumeration-format-strings.md)|Numaralandırma değerlerinin dize gösterimlerini oluşturmak için kullanılan standart biçim dizelerini açıklar.|
|<xref:System.Guid.ToString%28System.String%29?displayProperty=nameWithType>|Değerler için standart biçim dizelerini açıklar <xref:System.Guid> .|

## <a name="culture-sensitive-formatting-with-format-providers"></a>Biçim sağlayıcılarıyla kültüre duyarlı biçimlendirme

Biçim belirticileri nesnelerin biçimlendirmesini özelleştirmenizi sağlar, ancak nesnelerin anlamlı bir dize gösterimini üretmek genellikle ek biçimlendirme bilgileri gerektirir. Örneğin, "C" standart biçim dizesi veya "$ #, #. 00" gibi özel bir biçim dizesi kullanarak bir sayıyı para birimi değeri olarak biçimlendirmek, en azından, doğru para birimi sembolü, Grup ayırıcısı ve ondalık ayırıcısının biçimlendirilmiş dizeye dahil olması için kullanılabilecek bilgiler gerektirir. .NET sürümünde bu ek biçimlendirme bilgileri, <xref:System.IFormatProvider> `ToString` sayısal türler ve Tarih ve saat türleri yönteminin bir veya daha fazla aşırı yüküne bir parametre olarak sağlanan arabirim aracılığıyla kullanılabilir hale getirilir. <xref:System.IFormatProvider>uygulamalar, .NET 'te kültüre özgü biçimlendirmeyi desteklemek için kullanılır. Aşağıdaki örnek, bir nesnenin dize temsilinin <xref:System.IFormatProvider> farklı kültürleri temsil eden üç nesneyle biçimlendirildiğinde nasıl değiştiği gösterilmektedir.

[!code-csharp[Conceptual.Formatting.Overview#11](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/iformatprovider1.cs#11)]
[!code-vb[Conceptual.Formatting.Overview#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/iformatprovider1.vb#11)]

<xref:System.IFormatProvider>Arabirim, <xref:System.IFormatProvider.GetFormat%28System.Type%29> biçimlendirme bilgileri sağlayan nesne türünü belirten tek bir parametreye sahip olan bir yöntemini içerir. Yöntemi bu türden bir nesne sağlayabiliyorsanız, döndürür. Aksi halde, null bir başvuru döndürür ( `Nothing` Visual Basic).

<xref:System.IFormatProvider.GetFormat%2A?displayProperty=nameWithType>bir geri çağırma yöntemidir. Bir parametre içeren bir `ToString` yöntem aşırı yüklemesini çağırdığınızda <xref:System.IFormatProvider> , <xref:System.IFormatProvider.GetFormat%2A> Bu nesnenin yöntemini çağırır <xref:System.IFormatProvider> . <xref:System.IFormatProvider.GetFormat%2A>Yöntemi, parametresi tarafından belirtilen gerekli biçimlendirme bilgilerini yöntemine döndüren bir nesne döndürmekten sorumludur `formatType` `ToString` .

Bir dizi biçimlendirme veya dize dönüştürme yöntemi, türünde bir parametre içerir <xref:System.IFormatProvider> , ancak çoğu durumda, yöntemi çağrıldığında parametresinin değeri yok sayılır. Aşağıdaki tabloda, parametresini kullanan bazı biçimlendirme yöntemleri ve <xref:System.Type> yönteme geçirdikleri nesnenin türü listelenmektedir <xref:System.IFormatProvider.GetFormat%2A?displayProperty=nameWithType> .

|Yöntem|Parametrenin türü `formatType`|
|------------|------------------------------------|
|`ToString`sayısal türlerin yöntemi|<xref:System.Globalization.NumberFormatInfo?displayProperty=nameWithType>|
|`ToString`Tarih ve saat türleri yöntemi|<xref:System.Globalization.DateTimeFormatInfo?displayProperty=nameWithType>|
|<xref:System.String.Format%2A?displayProperty=nameWithType>|<xref:System.ICustomFormatter?displayProperty=nameWithType>|
|<xref:System.Text.StringBuilder.AppendFormat%2A?displayProperty=nameWithType>|<xref:System.ICustomFormatter?displayProperty=nameWithType>|

> [!NOTE]
> `ToString`Sayısal türlerin ve Tarih ve saat türlerinin yöntemleri aşırı yüklenmiştir ve yalnızca bazı aşırı yüklemelerin bir <xref:System.IFormatProvider> parametresi vardır. Bir yöntemde türünde parametre yoksa <xref:System.IFormatProvider> , <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=nameWithType> bunun yerine özelliği tarafından döndürülen nesne geçirilir. Örneğin, varsayılan metoda yapılan bir çağrı sonuç <xref:System.Int32.ToString?displayProperty=nameWithType> olarak aşağıdaki gibi bir yöntem çağrısıyla sonuçlanır: `Int32.ToString("G", System.Globalization.CultureInfo.CurrentCulture)` .

.NET aşağıdakileri uygulayan üç sınıf sağlar <xref:System.IFormatProvider> :

- <xref:System.Globalization.DateTimeFormatInfo>, belirli bir kültür için tarih ve saat değerleri için biçimlendirme bilgileri sağlayan bir sınıf. <xref:System.IFormatProvider.GetFormat%2A?displayProperty=nameWithType>Uygulamanın kendisi bir örneğini döndürür.

- <xref:System.Globalization.NumberFormatInfo>, belirli bir kültür için sayısal biçimlendirme bilgileri sağlayan bir sınıf. <xref:System.IFormatProvider.GetFormat%2A?displayProperty=nameWithType>Uygulamanın kendisi bir örneğini döndürür.

- <xref:System.Globalization.CultureInfo>. <xref:System.IFormatProvider.GetFormat%2A?displayProperty=nameWithType>Uygulama, <xref:System.Globalization.NumberFormatInfo> <xref:System.Globalization.DateTimeFormatInfo> Tarih ve saat değerleri için biçimlendirme bilgilerini sağlamak üzere sayısal biçimlendirme bilgileri veya nesne sağlamak için bir nesne döndürebilir.

Bu sınıfların herhangi birini değiştirmek için kendi biçim sağlayıcınızı de uygulayabilirsiniz. Ancak, uygulamanızın <xref:System.IFormatProvider.GetFormat%2A> yöntemi, yönteme biçimlendirme bilgileri sağlaması gerekiyorsa, önceki tabloda listelenen türde bir nesne döndürmelidir `ToString` .

### <a name="culture-sensitive-formatting-of-numeric-values"></a>Sayısal değerlerin kültüre duyarlı biçimlendirmesi

Varsayılan olarak, sayısal değer biçimlendirmesi kültüre duyarlıdır. Bir biçimlendirme yöntemini çağırdığınızda bir kültür belirtmezseniz, geçerli iş parçacığı kültürünün biçimlendirme kuralları kullanılır. Bu, geçerli iş parçacığı kültürünü dört kez değiştiren ve sonra yöntemi çağıran aşağıdaki örnekte gösterilmiştir <xref:System.Decimal.ToString%28System.String%29?displayProperty=nameWithType> . Her durumda, sonuç dizesi geçerli kültürün biçimlendirme kurallarını yansıtır. Bunun nedeni, `ToString` ve `ToString(String)` yöntemlerinin her sayısal tür metoduna çağrı kaydırması `ToString(String, IFormatProvider)` .

[!code-csharp[Conceptual.Formatting.Overview#19](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/culturespecific3.cs#19)]
[!code-vb[Conceptual.Formatting.Overview#19](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/culturespecific3.vb#19)]

Ayrıca, `ToString` bir parametresi olan bir aşırı yüklemeyi çağırarak `provider` ve bu parametreyi aşağıdakilerden birini geçirerek belirli bir kültür için sayısal bir değeri biçimlendirebilirsiniz:

- <xref:System.Globalization.CultureInfo>Biçimlendirme kuralları kullanılacak olan kültürü temsil eden nesne. <xref:System.Globalization.CultureInfo.GetFormat%2A?displayProperty=nameWithType>Yöntemi <xref:System.Globalization.CultureInfo.NumberFormat%2A?displayProperty=nameWithType> , <xref:System.Globalization.NumberFormatInfo> sayısal değerler için kültüre özgü biçimlendirme bilgileri sağlayan nesnesi olan özelliğinin değerini döndürür.

- <xref:System.Globalization.NumberFormatInfo>Kullanılacak kültüre özgü biçimlendirme kurallarını tanımlayan bir nesne. <xref:System.Globalization.NumberFormatInfo.GetFormat%2A>Yöntemi kendi örneğini döndürür.

Aşağıdaki örnek, <xref:System.Globalization.NumberFormatInfo> bir kayan noktalı sayıyı biçimlendirmek Için İngilizce (Birleşik Devletler) ve İngilizce (Büyük Britanya) kültürlerini ve Fransızca ve Rusça bağımsız kültürlerini temsil eden nesneleri kullanır.

[!code-csharp[Conceptual.Formatting.Overview#20](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/culturespecific4.cs#20)]
[!code-vb[Conceptual.Formatting.Overview#20](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/culturespecific4.vb#20)]

### <a name="culture-sensitive-formatting-of-date-and-time-values"></a>Tarih ve saat değerlerini kültüre duyarlı olarak biçimlendirme

Varsayılan olarak, tarih ve saat değerlerinin biçimlendirmesi kültüre duyarlıdır. Bir biçimlendirme yöntemini çağırdığınızda bir kültür belirtmezseniz, geçerli iş parçacığı kültürünün biçimlendirme kuralları kullanılır. Bu, geçerli iş parçacığı kültürünü dört kez değiştiren ve sonra yöntemi çağıran aşağıdaki örnekte gösterilmiştir <xref:System.DateTime.ToString%28System.String%29?displayProperty=nameWithType> . Her durumda, sonuç dizesi geçerli kültürün biçimlendirme kurallarını yansıtır. Bunun nedeni,, <xref:System.DateTime.ToString?displayProperty=nameWithType> <xref:System.DateTime.ToString%28System.String%29?displayProperty=nameWithType> <xref:System.DateTimeOffset.ToString?displayProperty=nameWithType> ve <xref:System.DateTimeOffset.ToString%28System.String%29?displayProperty=nameWithType> yöntemlerinin ve yöntemlerine çağrıları sarması nedeniyle oluşur <xref:System.DateTime.ToString%28System.String%2CSystem.IFormatProvider%29?displayProperty=nameWithType> <xref:System.DateTimeOffset.ToString%28System.String%2CSystem.IFormatProvider%29?displayProperty=nameWithType> .

[!code-csharp[Conceptual.Formatting.Overview#17](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/culturespecific1.cs#17)]
[!code-vb[Conceptual.Formatting.Overview#17](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/culturespecific1.vb#17)]

Ayrıca, bir <xref:System.DateTime.ToString%2A?displayProperty=nameWithType> parametresi olan bir veya daha <xref:System.DateTimeOffset.ToString%2A?displayProperty=nameWithType> fazla yük çağırarak `provider` ve bu parametreyi aşağıdakilerden birini geçirerek belirli bir kültür için bir tarih ve saat değeri biçimlendirebilirsiniz:

- <xref:System.Globalization.CultureInfo>Biçimlendirme kuralları kullanılacak olan kültürü temsil eden nesne. <xref:System.Globalization.CultureInfo.GetFormat%2A?displayProperty=nameWithType>Yöntemi <xref:System.Globalization.CultureInfo.DateTimeFormat%2A?displayProperty=nameWithType> , <xref:System.Globalization.DateTimeFormatInfo> Tarih ve saat değerleri için kültüre özgü biçimlendirme bilgileri sağlayan nesnesi olan özelliğinin değerini döndürür.

- <xref:System.Globalization.DateTimeFormatInfo>Kullanılacak kültüre özgü biçimlendirme kurallarını tanımlayan bir nesne. <xref:System.Globalization.DateTimeFormatInfo.GetFormat%2A>Yöntemi kendi örneğini döndürür.

Aşağıdaki örnek, <xref:System.Globalization.DateTimeFormatInfo> bir tarihi biçimlendirmek Için İngilizce (Birleşik Devletler) ve İngilizce (Büyük Britanya) kültürlerini ve Fransızca ve Rusça bağımsız kültürlerini temsil eden nesneleri kullanır.

[!code-csharp[Conceptual.Formatting.Overview#18](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/culturespecific2.cs#18)]
[!code-vb[Conceptual.Formatting.Overview#18](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/culturespecific2.vb#18)]

## <a name="the-iformattable-interface"></a>IFormattable arabirimi

Genellikle, `ToString` yöntemi bir biçim dizesi ve bir parametre ile aşırı yükleyen türler <xref:System.IFormatProvider> de <xref:System.IFormattable> arabirimini uygular. Bu arabirimin, <xref:System.IFormattable.ToString%28System.String%2CSystem.IFormatProvider%29?displayProperty=nameWithType> parametre olarak hem biçim dizesi hem de biçim sağlayıcısını içeren tek bir üyesi vardır.

<xref:System.IFormattable>Uygulama tanımlı sınıfınız için arabirimi uygulamak iki avantaj sunar:

- Sınıfı tarafından dize dönüştürme desteği <xref:System.Convert> . <xref:System.Convert.ToString%28System.Object%29?displayProperty=nameWithType>Ve yöntemlerine yapılan çağrılar <xref:System.Convert.ToString%28System.Object%2CSystem.IFormatProvider%29?displayProperty=nameWithType> <xref:System.IFormattable> uygulamanızı otomatik olarak çağırır.

- Bileşik biçimlendirme desteği. Özel türünü biçimlendirmek için bir biçim dizesi içeren bir biçim öğesi kullanılırsa, ortak dil çalışma zamanı uygulamanızı otomatik olarak çağırır <xref:System.IFormattable> ve biçim dizesini geçirir. Veya gibi yöntemlerle bileşik biçimlendirme hakkında daha fazla bilgi için <xref:System.String.Format%2A?displayProperty=nameWithType> <xref:System.Console.WriteLine%2A?displayProperty=nameWithType> bkz. [Bileşik biçimlendirme](#composite-formatting) bölümü.

Aşağıdaki örnek, `Temperature` arabirimini uygulayan bir sınıfı tanımlar <xref:System.IFormattable> . Sıcaklığın Santide gösterilmesi için "C" veya "G" biçim belirticilerini destekler, sıcaklığın Fahrenolması için "F" biçim belirticisi ve sıcaklığın Kelvin cinsinden gösterilmesi için "K" Biçim belirleyicisi.

[!code-csharp[Conceptual.Formatting.Overview#12](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/iformattable.cs#12)]
[!code-vb[Conceptual.Formatting.Overview#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/iformattable.vb#12)]

Aşağıdaki örnek bir nesnesi başlatır `Temperature` . Daha sonra yöntemi çağırır <xref:System.Convert.ToString%2A> ve bir nesnenin farklı dize gösterimlerini almak için birkaç bileşik biçim dizesi kullanır `Temperature` . Bu yöntem çağrılarının her biri, sırasıyla <xref:System.IFormattable> sınıfının uygulamasını çağırır `Temperature` .

[!code-csharp[Conceptual.Formatting.Overview#13](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/iformattable.cs#13)]
[!code-vb[Conceptual.Formatting.Overview#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/iformattable.vb#13)]

## <a name="composite-formatting"></a>Bileşik biçimlendirme

Ve gibi bazı yöntemler <xref:System.String.Format%2A?displayProperty=nameWithType> <xref:System.Text.StringBuilder.AppendFormat%2A?displayProperty=nameWithType> bileşik biçimlendirmeyi destekler. Bileşik biçim dizesi, sıfır, bir veya daha fazla nesnenin dize gösterimini içeren tek bir dize döndüren bir şablon türüdür. Her nesne, bileşik biçim dizesinde dizinli biçim öğesi tarafından temsil edilir. Biçim öğesinin dizini, yöntemin parametre listesinde temsil ettiği nesnenin konumuna karşılık gelir. Dizinler sıfır tabanlıdır. Örneğin, yöntemi için aşağıdaki çağrıda, <xref:System.String.Format%2A?displayProperty=nameWithType> ilk biçim öğesi `{0:D}` öğesinin dize temsili ile değiştirilmiştir `thatDate` ; ikinci biçim öğesi, `{1}` öğesinin dize temsili ile değiştirilmiştir `item1` ; ve üçüncü biçim öğesi, `{2:C2}` öğesinin dize temsili ile değiştirilmiştir `item1.Value` .

[!code-csharp[Conceptual.Formatting.Overview#14](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/composite1.cs#14)]
[!code-vb[Conceptual.Formatting.Overview#14](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/composite1.vb#14)]

Bir biçim öğesini karşılık gelen nesnenin dize gösterimiyle değiştirmeye ek olarak, biçim öğeleri de şunları denetlemenize olanak tanır:

- Nesne, arayüzü uygularsa <xref:System.IFormattable> ve biçim dizelerini destekliyorsa, nesnenin dize olarak temsil edildiği belirli bir yoldur. Bunu, `:` (iki nokta üst üste) ve ardından geçerli bir biçim dizesi olan biçim öğesinin dizinini izleyerek yapabilirsiniz. Önceki örnekte bu, bir tarih değerini "d" (kısa tarih düzeniyle) biçim dizesiyle (örn. `{0:d}` ) ve sayısal bir değeri "C2" biçim dizesiyle (örn. `{2:C2}` sayıyı iki kesirli ondalık basamaklı bir para birimi değeri olarak göstermek için) biçimlendirerek oldu.

- Nesnenin dize gösterimini içeren alanın genişliği ve bu alandaki dize gösteriminin hizalaması. Bunu, biçim öğesinin dizinini `,` (virgül) ve alan genişliğini izleyerek yapın. Alan genişliği pozitif bir değer ise, dize alana sağa hizalanır ve alan genişliği negatif bir değer ise sola hizalanır. Aşağıdaki örnek, tarih değerlerini 20 karakterlik bir alanda sola hizalar ve ondalık değerleri, 11 karakterlik bir alanda tek bir kesirli basamakla sağa hizalar.

     [!code-csharp[Conceptual.Formatting.Overview#22](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/composite2.cs#22)]
     [!code-vb[Conceptual.Formatting.Overview#22](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/composite2.vb#22)]

     Hizalama dizesi bileşeni ve biçim dizesi bileşeni varsa, ilki ikincinin (örneğin,) önünde olduğunu unutmayın `{0,-20:g}` .

Bileşik biçimlendirme hakkında daha fazla bilgi için bkz. [Bileşik biçimlendirme](composite-formatting.md).

## <a name="custom-formatting-with-icustomformatter"></a>ICustomFormatter ile özel biçimlendirme

İki bileşik biçimlendirme yöntemi <xref:System.String.Format%28System.IFormatProvider%2CSystem.String%2CSystem.Object%5B%5D%29?displayProperty=nameWithType> ve <xref:System.Text.StringBuilder.AppendFormat%28System.IFormatProvider%2CSystem.String%2CSystem.Object%5B%5D%29?displayProperty=nameWithType> , özel biçimlendirmeyi destekleyen bir biçim sağlayıcısı parametresi içerir. Bu biçimlendirme yöntemlerinden herhangi biri çağrıldığında, <xref:System.Type> bir arabirimi temsil eden bir nesneyi <xref:System.ICustomFormatter> biçim sağlayıcısının <xref:System.IFormatProvider.GetFormat%2A> yöntemine geçirir. <xref:System.IFormatProvider.GetFormat%2A>Yöntemi, daha sonra <xref:System.ICustomFormatter> özel biçimlendirme sağlayan uygulamanın döndürülmesinden sorumludur.

Arabirim, bileşik <xref:System.ICustomFormatter> <xref:System.ICustomFormatter.Format%28System.String%2CSystem.Object%2CSystem.IFormatProvider%29> biçimlendirme yöntemi tarafından otomatik olarak çağrılan tek bir yönteme sahiptir ve bir bileşik biçim dizesindeki her biçim öğesi için bir kez. <xref:System.ICustomFormatter.Format%28System.String%2CSystem.Object%2CSystem.IFormatProvider%29>Yöntemi üç parametreye sahiptir: bir biçim öğesinde bağımsız değişkeni temsil eden bir biçim dizesi, `formatString` biçimlendirilecek bir nesne ve <xref:System.IFormatProvider> biçimlendirme hizmetleri sağlayan bir nesne. Genellikle, uygulayan sınıf <xref:System.ICustomFormatter> de uygular <xref:System.IFormatProvider> , bu nedenle bu son parametre özel biçimlendirme sınıfının kendisi için bir başvurudur. Yöntemi, biçimlendirilecek nesnenin özel bir biçimli dize gösterimini döndürür. Yöntem nesneyi biçimlendiremiyor ise, null bir başvuru döndürmelidir ( `Nothing` Visual Basic).

Aşağıdaki örnek, <xref:System.ICustomFormatter> `ByteByByteFormatter` tam sayı değerlerini bir boşluk ile izleyen iki basamaklı onaltılık değerlerin bir sırası olarak görüntüleyen adlı bir uygulama sağlar.

[!code-csharp[Conceptual.Formatting.Overview#15](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/icustomformatter1.cs#15)]
[!code-vb[Conceptual.Formatting.Overview#15](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/icustomformatter1.vb#15)]

Aşağıdaki örnek, `ByteByByteFormatter` tamsayı değerlerini biçimlendirmek için sınıfını kullanır. <xref:System.ICustomFormatter.Format%2A?displayProperty=nameWithType>Yöntemin ikinci yöntem çağrısında birden çok kez çağrıldığını <xref:System.String.Format%28System.IFormatProvider%2CSystem.String%2CSystem.Object%5B%5D%29?displayProperty=nameWithType> ve varsayılan <xref:System.Globalization.NumberFormatInfo> sağlayıcının üçüncü yöntem çağrısında kullanıldığını unutmayın, çünkü.`ByteByByteFormatter.Format` Yöntem, "N0" biçim dizesini tanımıyor ve null bir başvuru döndürüyor ( `Nothing` Visual Basic).

[!code-csharp[Conceptual.Formatting.Overview#16](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/icustomformatter1.cs#16)]
[!code-vb[Conceptual.Formatting.Overview#16](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/icustomformatter1.vb#16)]

## <a name="related-topics"></a>İlgili konular

|Başlık|Tanım|
|-----------|----------------|
|[Standart sayısal biçim dizeleri](standard-numeric-format-strings.md)|Sayısal değerlerin yaygın olarak kullanılan dize temsillerini oluşturan standart biçim dizelerini açıklar.|
|[Özel sayısal biçim dizeleri](custom-numeric-format-strings.md)|Sayısal değerler için uygulamaya özel biçimler oluşturan özel biçim dizelerini açıklar.|
|[Standart Tarih ve saat biçim dizeleri](standard-date-and-time-format-strings.md)|Değerlerin yaygın olarak kullanılan dize temsillerini oluşturan standart biçim dizelerini açıklar <xref:System.DateTime> .|
|[Özel tarih ve saat biçim dizeleri](custom-date-and-time-format-strings.md)|Değerler için uygulamaya özel biçimler oluşturan özel biçim dizelerini açıklar <xref:System.DateTime> .|
|[Standart TimeSpan Biçim dizeleri](standard-timespan-format-strings.md)|Zaman aralıklarının yaygın olarak kullanılan dize temsillerini oluşturan standart biçim dizelerini açıklar.|
|[Özel TimeSpan Biçim dizeleri](custom-timespan-format-strings.md)|Zaman aralıkları için uygulamaya özel biçimler oluşturan özel biçim dizelerini açıklar.|
|[Sabit listesi biçim dizeleri](enumeration-format-strings.md)|Numaralandırma değerlerinin dize gösterimlerini oluşturmak için kullanılan standart biçim dizelerini açıklar.|
|[Bileşik biçimlendirme](composite-formatting.md)|Bir veya daha fazla biçimli değerin bir dizeye nasıl ekleneceğini açıklar. Dize daha sonra konsolda görüntülenebilir veya bir akışa yazılabilir.|
|[Dizeleri Ayrıştırma](parsing-strings.md)|Nesnelerin, bu nesnelerin dize temsilleri tarafından tanımlanan değerlere nasıl başlatılacağını açıklar. Ayrıştırma biçimlendirmenin ters işlemidir.|

## <a name="reference"></a>Başvuru

- <xref:System.IFormattable?displayProperty=nameWithType>
- <xref:System.IFormatProvider?displayProperty=nameWithType>
- <xref:System.ICustomFormatter?displayProperty=nameWithType>
