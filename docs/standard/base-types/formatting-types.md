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
ms.openlocfilehash: e9d53e7a75463e481b667a7ad84b68cb225e7f7c
ms.sourcegitcommit: 559259da2738a7b33a46c0130e51d336091c2097
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72774317"
---
# <a name="format-types-in-net"></a>.NET 'teki biçim türleri

Biçimlendirme, bir sınıf, yapı veya numaralandırma değerinin bir örneğini dize gösterimine dönüştürme işlemidir. böylece, sonuçta elde edilen dize kullanıcılara görüntülenebilir veya orijinal veri türünü geri yüklemek için seri durumdan çıkarılmış olur. Bu dönüştürme bir dizi zorluklara neden olabilir:

- Değerlerin dahili olarak depolandığı yol, kullanıcıların bunları görüntülemek istedikleri yöntemi göstermez. Örneğin, bir telefon numarası, Kullanıcı dostu olmayan 8009999999 biçiminde depolanabilir. Bunun yerine 800-999-9999 olarak gösterilmesi gerekir. Bu şekilde bir sayıyı biçimlendiren bir örnek için [özel biçim dizeleri](#custom-format-strings) bölümüne bakın.

- Bazen bir nesnenin dize gösterimine dönüştürülmesi sezgisel değildir. Örneğin, bir sıcaklık nesnesinin veya bir kişi nesnesinin dize gösteriminin nasıl görünmesi net değildir. Bir sıcaklık nesnesini çeşitli yollarla biçimlendiren bir örnek için bkz. [standart biçim dizeleri](#standard-format-strings) bölümü.

- Değerler genellikle kültüre duyarlı biçimlendirme gerektirir. Örneğin, parasal değerleri yansıtmak için sayı kullanan bir uygulamada, sayısal dizeler geçerli kültürün para birimi simgesini, Grup ayırıcısını (çoğu kültürde, binlerce ayırıcıdır) ve ondalık sembolünü içermelidir. Bir örnek için, [biçim sağlayıcıları Ile kültüre duyarlı biçimlendirme](#culture-sensitive-formatting-with-format-providers) bölümüne bakın.

- Uygulamanın aynı değeri farklı şekillerde görüntülemesi gerekebilir. Örneğin, bir uygulama, adının bir dize gösterimini görüntüleyerek veya onun temel aldığı değerini görüntüleyerek bir numaralandırma üyesini temsil edebilir. @No__t_0 sabit listesinin bir üyesini farklı yollarla biçimlendiren bir örnek için bkz. [standart biçim dizeleri](#standard-format-strings) bölümü.

> [!NOTE]
> Biçimlendirme bir türün değerini dize temsiline dönüştürür. Ayrıştırma biçimlendirmenin tersidir. Bir ayrıştırma işlemi, dize gösteriminden bir veri türü örneği oluşturur. Dizeleri diğer veri türlerine dönüştürme hakkında daha fazla bilgi için bkz. [dizeleri ayrıştırma](../../../docs/standard/base-types/parsing-strings.md).

.NET, geliştiricilerin bu gereksinimleri ele almasını sağlayan zengin biçimlendirme desteği sağlar.

## <a name="formatting-in-net"></a>.NET 'te biçimlendirme

Biçimlendirme için temel mekanizma, bu konunun ilerleyen kısımlarında yer olarak [ToString yöntemi kullanılarak varsayılan biçimlendirme](#default-formatting-using-the-tostring-method) bölümünde açıklanan <xref:System.Object.ToString%2A?displayProperty=nameWithType> yönteminin varsayılan uygulamasıdır. Ancak .NET, varsayılan biçimlendirme desteğini değiştirmek ve genişletmek için çeşitli yollar sunar. Bunlar aşağıdakileri içerir:

- Bir nesnenin değerinin özel bir dize gösterimini tanımlamak için <xref:System.Object.ToString%2A?displayProperty=nameWithType> yöntemini geçersiz kılma. Daha fazla bilgi için bu konunun ilerleyen kısımlarındaki [ToString yöntemini geçersiz kılma](#override-the-tostring-method) bölümüne bakın.

- Bir nesnenin değerinin dize gösterimine birden çok form geçirmesine imkan tanıyan biçim belirticileri tanımlama. Örneğin, aşağıdaki deyimdeki "X" Biçim belirleyicisi bir tamsayıyı onaltılık bir değerin dize gösterimine dönüştürür.

     [!code-csharp[Conceptual.Formatting.Overview#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/specifier1.cs#3)]
     [!code-vb[Conceptual.Formatting.Overview#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/specifier1.vb#3)]

     Biçim belirticileri hakkında daha fazla bilgi için bkz. [ToString yöntemi ve biçim dizeleri](#the-tostring-method-and-format-strings) bölümü.

- Belirli bir kültürün biçimlendirme kurallarından yararlanmak için biçim sağlayıcıları kullanma. Örneğin, aşağıdaki ifade, en-US kültürün biçimlendirme kurallarını kullanarak bir para birimi değeri görüntüler.

     [!code-csharp[Conceptual.Formatting.Overview#10](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/specifier1.cs#10)]
     [!code-vb[Conceptual.Formatting.Overview#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/specifier1.vb#10)]

     Biçim sağlayıcılarıyla biçimlendirme hakkında daha fazla bilgi için, [biçim sağlayıcıları](#culture-sensitive-formatting-with-format-providers) bölümüne bakın.

- @No__t_1 sınıfı ve bileşik biçimlendirme ile her iki dize dönüştürmeyi desteklemek için <xref:System.IFormattable> arabirimini uygulama. Daha fazla bilgi için [IFormattable arabirimi](#the-iformattable-interface) bölümüne bakın.

- Daha büyük bir dizedeki bir değerin dize gösterimini katıştırmak için bileşik biçimlendirme kullanma. Daha fazla bilgi için [Bileşik biçimlendirme](#composite-formatting) bölümüne bakın.

- @No__t_0 ve <xref:System.IFormatProvider> bir bütün özel biçimlendirme çözümü sağlamak için uygulama. Daha fazla bilgi için [ıccustomformatter Ile özel biçimlendirme](#custom-formatting-with-icustomformatter) bölümüne bakın.

Aşağıdaki bölümlerde, bir nesneyi dize gösterimine dönüştürmeye yönelik bu yöntemler incelenmekte.

## <a name="default-formatting-using-the-tostring-method"></a>ToString yöntemini kullanarak varsayılan biçimlendirme

@No__t_0 türetilen her tür, varsayılan olarak türün adını döndüren parametresiz `ToString` yöntemini otomatik olarak devralır. Aşağıdaki örnekte, varsayılan `ToString` yöntemi gösterilmektedir. Uygulama içermeyen `Automobile` adlı bir sınıfı tanımlar. Sınıf örneği oluşturulduğunda ve `ToString` yöntemi çağrıldığında, onun tür adını görüntüler. @No__t_0 yönteminin örnekte açıkça çağrılmadığını unutmayın. @No__t_0 yöntemi, bir bağımsız değişken olarak kendisine geçirilen nesnenin `ToString` yöntemini dolaylı olarak çağırır.

[!code-csharp[Conceptual.Formatting.Overview#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/default1.cs#1)]
[!code-vb[Conceptual.Formatting.Overview#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/default1.vb#1)]

> [!WARNING]
> @No__t_0 başlayarak, Windows Çalışma Zamanı, varsayılan biçimlendirme desteği sağlayan [ıtringable. ToString](xref:Windows.Foundation.IStringable.ToString%2A)adlı tek bir yönteme sahip bir <xref:Windows.Foundation.IStringable> arabirimi içerir. Ancak, yönetilen türlerin `IStringable` arabirimini uygulamamalarını öneririz. Daha fazla bilgi için <xref:System.Object.ToString%2A?displayProperty=nameWithType> başvuru sayfasındaki "Windows Çalışma Zamanı ve `IStringable` arabirimi" bölümüne bakın.

Arabirimler dışındaki tüm türler <xref:System.Object> türetildiğinden, bu işlev özel sınıflarınıza veya yapılarına otomatik olarak sağlanır. Ancak, varsayılan `ToString` yöntemi tarafından sunulan işlevsellik sınırlıdır: türü tanımlasa da, türün bir örneği hakkında herhangi bir bilgi sağlamaz. Bu nesne hakkında bilgi sağlayan bir nesnenin dize gösterimini sağlamak için `ToString` yöntemini geçersiz kılmanız gerekir.

> [!NOTE]
> Yapılar <xref:System.ValueType> devralınır, bu da <xref:System.Object> türetilir. @No__t_0, <xref:System.Object.ToString%2A?displayProperty=nameWithType> geçersiz kılsa da, uygulama aynıdır.

## <a name="override-the-tostring-method"></a>ToString yöntemini geçersiz kılma

Bir türün adının görüntülenmesi genellikle sınırlı kullanıma sahiptir ve türlerinizin tüketicilerinin bir örneği diğerinden ayırt edilmesine izin vermez. Ancak, bir nesnenin değerinin daha kullanışlı bir temsilini sağlamak için `ToString` yöntemini geçersiz kılabilirsiniz. Aşağıdaki örnek, bir `Temperature` nesnesini tanımlar ve `ToString` metodunu, sıcaklığın santigrat derece cinsinden gösterilmesi için geçersiz kılar.

[!code-csharp[Conceptual.Formatting.Overview#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/overrides1.cs#2)]
[!code-vb[Conceptual.Formatting.Overview#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/overrides1.vb#2)]

.NET ' te, her ilkel değer türünün `ToString` yöntemi, nesnenin değerini adı yerine göstermek için geçersiz kılınır. Aşağıdaki tabloda her ilkel tür için geçersiz kılma gösterilmektedir. Geçersiz kılınan yöntemlerin çoğu `ToString` yönteminin başka bir aşırı yüklemesini çağırır ve bunu, türü için genel biçimi ve geçerli kültürü temsil eden bir <xref:System.IFormatProvider> nesnesini tanımlayan "G" biçim belirticisini geçirdiğini unutmayın.

|Tür|ToString geçersiz kılma|
|----------|-----------------------|
|<xref:System.Boolean>|@No__t_0 ya da <xref:System.Boolean.FalseString?displayProperty=nameWithType> döndürür.|
|<xref:System.Byte>|Geçerli kültürün <xref:System.Byte> değerini biçimlendirmek için `Byte.ToString("G", NumberFormatInfo.CurrentInfo)` çağırır.|
|<xref:System.Char>|Karakteri dize olarak döndürür.|
|<xref:System.DateTime>|Geçerli kültürün tarih ve saat değerini biçimlendirmek için `DateTime.ToString("G", DatetimeFormatInfo.CurrentInfo)` çağırır.|
|<xref:System.Decimal>|Geçerli kültürün <xref:System.Decimal> değerini biçimlendirmek için `Decimal.ToString("G", NumberFormatInfo.CurrentInfo)` çağırır.|
|<xref:System.Double>|Geçerli kültürün <xref:System.Double> değerini biçimlendirmek için `Double.ToString("G", NumberFormatInfo.CurrentInfo)` çağırır.|
|<xref:System.Int16>|Geçerli kültürün <xref:System.Int16> değerini biçimlendirmek için `Int16.ToString("G", NumberFormatInfo.CurrentInfo)` çağırır.|
|<xref:System.Int32>|Geçerli kültürün <xref:System.Int32> değerini biçimlendirmek için `Int32.ToString("G", NumberFormatInfo.CurrentInfo)` çağırır.|
|<xref:System.Int64>|Geçerli kültürün <xref:System.Int64> değerini biçimlendirmek için `Int64.ToString("G", NumberFormatInfo.CurrentInfo)` çağırır.|
|<xref:System.SByte>|Geçerli kültürün <xref:System.SByte> değerini biçimlendirmek için `SByte.ToString("G", NumberFormatInfo.CurrentInfo)` çağırır.|
|<xref:System.Single>|Geçerli kültürün <xref:System.Single> değerini biçimlendirmek için `Single.ToString("G", NumberFormatInfo.CurrentInfo)` çağırır.|
|<xref:System.UInt16>|Geçerli kültürün <xref:System.UInt16> değerini biçimlendirmek için `UInt16.ToString("G", NumberFormatInfo.CurrentInfo)` çağırır.|
|<xref:System.UInt32>|Geçerli kültürün <xref:System.UInt32> değerini biçimlendirmek için `UInt32.ToString("G", NumberFormatInfo.CurrentInfo)` çağırır.|
|<xref:System.UInt64>|Geçerli kültürün <xref:System.UInt64> değerini biçimlendirmek için `UInt64.ToString("G", NumberFormatInfo.CurrentInfo)` çağırır.|

## <a name="the-tostring-method-and-format-strings"></a>ToString yöntemi ve biçim dizeleri

Bir nesnenin tek bir dize gösterimine sahip olması durumunda, varsayılan `ToString` yöntemi veya geçersiz kılma `ToString` güvenmek uygundur. Ancak, bir nesnenin değerinde genellikle birden çok temsili vardır. Örneğin, sıcaklık Fahrenhayt, santigrat veya Kelvin derece olarak ifade edilebilir. Benzer şekilde, 10 tamsayı değeri 10, 10,0, 1.0 E01 veya $10,00 dahil olmak üzere çeşitli yollarla temsil edilebilir.

Tek bir değerin birden çok dize temsillerine sahip olmasını sağlamak için, .NET biçim dizelerini kullanır. Biçim dizesi, bir veya daha fazla önceden tanımlanmış biçim belirticilerini içeren bir dizedir; tek karakter veya `ToString` yönteminin çıktısını nasıl biçimlendirmelidir tanımlayan karakter grupları. Biçim dizesi daha sonra nesnenin `ToString` yöntemine bir parametre olarak geçirilir ve bu nesnenin değerinin dize temsilinin nasıl görüntüleneceğini belirler.

.NET 'teki tüm sayısal türler, tarih ve saat türleri ve numaralandırma türleri önceden tanımlanmış bir biçim belirteçleri kümesini destekler. Uygulama tanımlı veri türlerinizin birden fazla dize temsilini tanımlamak için biçim dizelerini de kullanabilirsiniz.

### <a name="standard-format-strings"></a>Standart biçim dizeleri

Standart bir biçim dizesi, uygulandığı nesnenin dize gösterimini tanımlayan bir alfabetik karakter olan tek bir Biçim belirleyicisi içerir ve bu, içinde kaç basamak gösterileceğini etkileyen isteğe bağlı bir duyarlık belirticisiyle birlikte sonuç dizesi. Duyarlık belirticisi atlanırsa veya desteklenmiyorsa, standart bir biçim belirticisi standart biçim dizesine eşdeğerdir.

.NET, tüm sayısal türler, tüm tarih ve saat türleri ve tüm numaralandırma türleri için standart biçim belirticileri kümesi tanımlar. Örneğin, bu kategorilerin her biri bir "G" standart biçim belirticisini destekler ve bu tür bir değerin genel dize gösterimini tanımlar.

Sabit listesi türleri için standart biçim dizeleri, bir değerin dize temsilini doğrudan denetler. Bir numaralandırma değerinin `ToString` metoduna geçirilen biçim dizeleri değerin dize adı ("G" ve "F" biçim belirticileri), temel alınan integral değeri ("D" Biçim Belirleyicisi) veya onaltılı değeri ("X") kullanılarak görüntülenip görüntülenmeyeceğini belirtir. Biçim Belirleyicisi). Aşağıdaki örnek, bir <xref:System.DayOfWeek> numaralandırma değerini biçimlendirmek için standart biçim dizelerinin kullanımını gösterir.

[!code-csharp[Conceptual.Formatting.Overview#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/standard1.cs#4)]
[!code-vb[Conceptual.Formatting.Overview#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/standard1.vb#4)]

Numaralandırma biçim dizeleri hakkında daha fazla bilgi için bkz. [numaralandırma biçim dizeleri](../../../docs/standard/base-types/enumeration-format-strings.md).

Sayısal türler için standart biçim dizeleri, genellikle kesin görünümü bir veya daha fazla özellik değeri tarafından denetlenen bir sonuç dizesi tanımlar. Örneğin, "C" biçim belirticisi bir sayıyı para birimi değeri olarak biçimlendirir. Tek parametre olarak "C" biçim belirticisiyle `ToString` yöntemini çağırdığınızda, geçerli kültürün <xref:System.Globalization.NumberFormatInfo> nesnesinden aşağıdaki özellik değerleri sayısal değerin dize gösterimini tanımlamak için kullanılır:

- Geçerli kültürün para birimi sembolünü belirten <xref:System.Globalization.NumberFormatInfo.CurrencySymbol%2A> özelliği.

- Aşağıdakileri belirleyen bir tamsayı döndüren <xref:System.Globalization.NumberFormatInfo.CurrencyNegativePattern%2A> veya <xref:System.Globalization.NumberFormatInfo.CurrencyPositivePattern%2A> özelliği:

  - Para birimi sembolünün yerleşimi.

  - Negatif değerlerin önünde eksi işareti, sondaki eksi işareti veya parantezle gösterilip gösterilmeyeceğini belirtir.

  - Sayısal değer ve para birimi simgesi arasında bir boşluk görünüp görüntülenmediğini belirtir.

- Sonuç dizesindeki kesirli basamakların sayısını tanımlayan <xref:System.Globalization.NumberFormatInfo.CurrencyDecimalDigits%2A> özelliği.

- Sonuç dizesinde ondalık ayırıcı sembolünü tanımlayan <xref:System.Globalization.NumberFormatInfo.CurrencyDecimalSeparator%2A> özelliği.

- Grup ayırıcı sembolünü tanımlayan <xref:System.Globalization.NumberFormatInfo.CurrencyGroupSeparator%2A> özelliği.

- Her bir gruptaki basamak sayısını ondalığın solunda tanımlayan <xref:System.Globalization.NumberFormatInfo.CurrencyGroupSizes%2A> özelliği.

- Parantez negatif değerleri belirtmek için kullanılmazsa, sonuç dizesinde kullanılan negatif işareti belirleyen <xref:System.Globalization.NumberFormatInfo.NegativeSign%2A> özelliği.

Ayrıca, sayısal biçim dizeleri bir duyarlık belirticisi içerebilir. Bu belirticinin anlamı, kullanıldığı biçim dizesine bağlıdır, ancak genellikle sonuç dizesinde görünmesi gereken toplam basamak sayısını veya kesirli basamak sayısını belirtir. Örneğin, aşağıdaki örnek, dört onaltılık basamağa sahip bir dize değeri oluşturmak için "x4" standart sayısal dizesini ve duyarlık belirticisini kullanır.

[!code-csharp[Conceptual.Formatting.Overview#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/precisionspecifier1.cs#6)]
[!code-vb[Conceptual.Formatting.Overview#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/precisionspecifier1.vb#6)]

Standart sayısal biçimlendirme dizeleri hakkında daha fazla bilgi için bkz. [Standart sayısal biçim dizeleri](../../../docs/standard/base-types/standard-numeric-format-strings.md).

Tarih ve saat değerleri için standart biçim dizeleri, belirli bir <xref:System.Globalization.DateTimeFormatInfo> özelliği tarafından depolanan özel biçim dizeleri için diğer adlardır. Örneğin, "D" biçim belirticisi ile tarih ve saat değerinin `ToString` yöntemini çağırmak, geçerli kültürün <xref:System.Globalization.DateTimeFormatInfo.LongDatePattern%2A?displayProperty=nameWithType> özelliğinde depolanan özel biçim dizesini kullanarak tarih ve saati gösterir. (Özel biçim dizeleri hakkında daha fazla bilgi için [sonraki bölüme](#custom-format-strings)bakın.) Aşağıdaki örnekte bu ilişki gösterilmektedir.

[!code-csharp[Conceptual.Formatting.Overview#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/alias1.cs#5)]
[!code-vb[Conceptual.Formatting.Overview#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/alias1.vb#5)]

Standart Tarih ve saat biçim dizeleri hakkında daha fazla bilgi için bkz. [Standart Tarih ve saat biçim dizeleri](../../../docs/standard/base-types/standard-date-and-time-format-strings.md).

Ayrıca, nesnenin `ToString(String)` yöntemi tarafından üretilen uygulama tanımlı bir nesnenin dize temsilini tanımlamak için standart biçim dizelerini de kullanabilirsiniz. Nesnenizin desteklediği belirli standart biçim belirticilerini tanımlayabilir ve bunların büyük/küçük harfe duyarlı olup olmadığını belirleyebilirsiniz. @No__t_0 yöntemi uygulamanız aşağıdakileri desteklemelidir:

- Nesnenin bir normal veya ortak biçimini temsil eden bir "G" biçim belirticisi. Nesnenizin `ToString` yönteminin Parametresiz aşırı yüklemesi, `ToString(String)` aşırı yüklemesini çağırmalıdır ve "G" standart biçim dizesine iletmelidir.

- Null başvuruya eşit olan bir Biçim belirleyicisi desteği (Visual Basic `Nothing`). Null başvurusuna eşit olan bir biçim belirticisi "G" biçim belirticisine eşdeğer olarak kabul edilmelidir.

Örneğin, bir `Temperature` sınıfı sıcaklığın derece derece cinsinden dahili olarak depolanmasını sağlayabilir ve `Temperature` nesnenin değerini santigrat, derece Fahrenhayt ve Kelvin cinsinden temsil eden biçim belirticilerini kullanabilir. Aşağıdaki örnek, bir gösterim sağlar.

[!code-csharp[Conceptual.Formatting.Overview#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/appstandard1.cs#7)]
[!code-vb[Conceptual.Formatting.Overview#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/appstandard1.vb#7)]

### <a name="custom-format-strings"></a>Özel biçim dizeleri

Standart biçim dizelerine ek olarak, .NET, hem sayısal değerler hem de tarih ve saat değerleri için özel biçim dizelerini tanımlar. Özel biçim dizesi, bir değerin dize gösterimini tanımlayan bir veya daha fazla özel biçim belirticisinden oluşur. Örneğin, "yyyy/AA/GG SS: DD: ss. ffff t zzz" özel tarih ve saat biçimi dizesi, en-US kültürü için bir tarihi "2008/11/15 07:45:00.0000 P-08:00" biçiminde dize gösterimine dönüştürür. Benzer şekilde, "0000" özel biçim dizesi 12 tamsayı değerini "0012" olarak dönüştürür. Özel biçim dizelerinin tüm listesi için bkz. [özel tarih ve saat biçimi dizeleri](../../../docs/standard/base-types/custom-date-and-time-format-strings.md) ve [özel sayısal biçim dizeleri](../../../docs/standard/base-types/custom-numeric-format-strings.md).

Bir biçim dizesi tek bir özel biçim belirticisinden oluşuyorsa, Biçim belirleyicisi öncesinde% (%) olmalıdır Standart biçim belirticisiyle karışıklık oluşmasını önlemek için simge. Aşağıdaki örnek, belirli bir tarihin ayın tek basamaklı veya iki basamaklı bir sayısını göstermek için "d" özel biçim belirticisini kullanır.

[!code-csharp[Conceptual.Formatting.Overview#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/singlecustom1.cs#8)]
[!code-vb[Conceptual.Formatting.Overview#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/singlecustom1.vb#8)]

Tarih ve saat değerleri için birçok standart biçim dizesi, <xref:System.Globalization.DateTimeFormatInfo> nesnesinin özellikleri tarafından tanımlanan özel biçim dizeleri için diğer adlardır. Özel biçim dizeleri, sayısal değerler veya tarih ve saat değerleri için uygulama tanımlı biçimlendirme sağlamaya yönelik önemli bir esneklik sunar. Birden çok özel biçim belirticilerini tek bir özel biçim dizesinde birleştirerek, hem sayısal değerler hem de tarih ve saat değerleri için kendi özel sonuç dizelerinizi tanımlayabilirsiniz. Aşağıdaki örnek, ay adı, gün ve yıldan sonra parantez içinde haftanın gününü gösteren bir özel biçim dizesi tanımlar.

[!code-csharp[Conceptual.Formatting.Overview#9](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/custom1.cs#9)]
[!code-vb[Conceptual.Formatting.Overview#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/custom1.vb#9)]

Aşağıdaki örnek, alan kodu ile birlikte standart, yedi basamaklı ABD telefon numarası olarak bir <xref:System.Int64> değerini görüntüleyen bir özel biçim dizesi tanımlar.

[!code-csharp[Conceptual.Formatting.Overview#21](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/telnumber1.cs#21)]
[!code-vb[Conceptual.Formatting.Overview#21](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/telnumber1.vb#21)]

Standart biçim dizeleri, uygulama tanımlı türlerinizin çoğu biçimlendirme ihtiyaçlarını genellikle işleyebilir, ancak türlerinizi biçimlendirmek için özel biçim belirticileri de tanımlayabilirsiniz.

### <a name="format-strings-and-net-types"></a>Biçimlendirme dizeleri ve .NET türleri

Tüm sayısal türler (yani, <xref:System.Byte>, <xref:System.Decimal>, <xref:System.Double>, <xref:System.Int16>, <xref:System.Int32>, <xref:System.Int64>, <xref:System.SByte>, <xref:System.Single>, <xref:System.UInt16>, <xref:System.UInt32>, 0 ve 1 türleri) ve 2 , 3, 4, 5 ve tüm numaralandırma türleri, biçim dizeleriyle biçimlendirmeyi destekler. Her tür tarafından desteklenen belirli biçim dizeleri hakkında daha fazla bilgi için aşağıdaki konulara bakın:

|Başlık|Tanım|
|-----------|----------------|
|[Standart Sayısal Biçim Dizeleri](../../../docs/standard/base-types/standard-numeric-format-strings.md)|Sayısal değerlerin yaygın olarak kullanılan dize temsillerini oluşturan standart biçim dizelerini açıklar.|
|[Özel Sayısal Biçim Dizeleri](../../../docs/standard/base-types/custom-numeric-format-strings.md)|Sayısal değerler için uygulamaya özel biçimler oluşturan özel biçim dizelerini açıklar.|
|[Standart Tarih ve Saat Biçim Dizeleri](../../../docs/standard/base-types/standard-date-and-time-format-strings.md)|@No__t_0 ve <xref:System.DateTimeOffset> değerlerinin yaygın olarak kullanılan dize temsillerini oluşturan standart biçim dizelerini açıklar.|
|[Özel Tarih ve Saat Biçim Dizeleri](../../../docs/standard/base-types/custom-date-and-time-format-strings.md)|@No__t_0 ve <xref:System.DateTimeOffset> değerleri için uygulamaya özel biçimler oluşturan özel biçim dizelerini açıklar.|
|[Standart TimeSpan Biçim Dizeleri](../../../docs/standard/base-types/standard-timespan-format-strings.md)|Zaman aralıklarının yaygın olarak kullanılan dize temsillerini oluşturan standart biçim dizelerini açıklar.|
|[Özel TimeSpan Biçim Dizeleri](../../../docs/standard/base-types/custom-timespan-format-strings.md)|Zaman aralıkları için uygulamaya özel biçimler oluşturan özel biçim dizelerini açıklar.|
|[Sabit Listesi Biçim Dizeleri](../../../docs/standard/base-types/enumeration-format-strings.md)|Numaralandırma değerlerinin dize gösterimlerini oluşturmak için kullanılan standart biçim dizelerini açıklar.|
|<xref:System.Guid.ToString%28System.String%29?displayProperty=nameWithType>|@No__t_0 değerleri için standart biçim dizelerini açıklar.|

## <a name="culture-sensitive-formatting-with-format-providers"></a>Biçim sağlayıcılarıyla kültüre duyarlı biçimlendirme

Biçim belirticileri nesnelerin biçimlendirmesini özelleştirmenizi sağlar, ancak nesnelerin anlamlı bir dize gösterimini üretmek genellikle ek biçimlendirme bilgileri gerektirir. Örneğin, "C" standart biçim dizesi veya "$ #, #. 00" gibi özel bir biçim dizesi kullanarak bir sayıyı para birimi değeri olarak biçimlendirmek, en azından doğru para birimi sembolü, Grup ayırıcısı ve ondalık ayırıcısının olması için gereken bilgileri gerektirir biçimlendirilen dizeye dahil etmek için kullanılabilir. .NET sürümünde bu ek biçimlendirme bilgileri, sayısal türlerin ve Tarih ve saat türlerinin `ToString` yönteminin bir veya daha fazla aşırı yüküne bir parametre olarak sağlanan <xref:System.IFormatProvider> arabirimi aracılığıyla kullanılabilir hale getirilir. <xref:System.IFormatProvider> uygulamalar, .NET 'te kültüre özgü biçimlendirmeyi desteklemek için kullanılır. Aşağıdaki örnek, farklı kültürleri temsil eden üç <xref:System.IFormatProvider> nesne ile biçimlendirildiğinde bir nesnenin dize temsilinin nasıl değiştiği gösterilmektedir.

[!code-csharp[Conceptual.Formatting.Overview#11](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/iformatprovider1.cs#11)]
[!code-vb[Conceptual.Formatting.Overview#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/iformatprovider1.vb#11)]

@No__t_0 arabirimi, biçimlendirme bilgileri sağlayan nesne türünü belirten tek bir parametreye sahip <xref:System.IFormatProvider.GetFormat%28System.Type%29> bir yöntemi içerir. Yöntemi bu türden bir nesne sağlayabiliyorsanız, döndürür. Aksi halde, null bir başvuru döndürür (Visual Basic `Nothing`).

<xref:System.IFormatProvider.GetFormat%2A?displayProperty=nameWithType> bir geri çağırma yöntemidir. Bir <xref:System.IFormatProvider> parametresi içeren `ToString` yöntemi aşırı yüklemesini çağırdığınızda, bu <xref:System.IFormatProvider> nesnesinin <xref:System.IFormatProvider.GetFormat%2A> yöntemini çağırır. @No__t_0 yöntemi, `formatType` parametresi tarafından belirtilen gerekli biçimlendirme bilgilerini `ToString` yöntemine döndürmekten sorumludur.

Bir dizi biçimlendirme veya dize dönüştürme yöntemi, <xref:System.IFormatProvider> türünde bir parametre içerir, ancak çoğu durumda, yöntemi çağrıldığında parametresinin değeri yok sayılır. Aşağıdaki tabloda, parametresini kullanan bazı biçimlendirme yöntemleri ve <xref:System.IFormatProvider.GetFormat%2A?displayProperty=nameWithType> yöntemine geçirdiğiniz <xref:System.Type> nesnesinin türü listelenmektedir.

|Yöntem|@No__t_0 parametresinin türü|
|------------|------------------------------------|
|sayısal türlerde `ToString` yöntemi|<xref:System.Globalization.NumberFormatInfo?displayProperty=nameWithType>|
|Tarih ve saat türlerinin `ToString` yöntemi|<xref:System.Globalization.DateTimeFormatInfo?displayProperty=nameWithType>|
|<xref:System.String.Format%2A?displayProperty=nameWithType>|<xref:System.ICustomFormatter?displayProperty=nameWithType>|
|<xref:System.Text.StringBuilder.AppendFormat%2A?displayProperty=nameWithType>|<xref:System.ICustomFormatter?displayProperty=nameWithType>|

> [!NOTE]
> Sayısal türlerin ve Tarih ve saat türlerinin `ToString` yöntemleri aşırı yüklenmiştir ve yalnızca bazı aşırı yüklemelerin bir <xref:System.IFormatProvider> parametresi vardır. Bir yöntemde <xref:System.IFormatProvider> türünde bir parametre yoksa, bunun yerine <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=nameWithType> özelliği tarafından döndürülen nesne geçirilir. Örneğin, varsayılan <xref:System.Int32.ToString?displayProperty=nameWithType> metoduna yapılan bir çağrı sonuç olarak aşağıdaki gibi bir yöntem çağrısıyla sonuçlanır: `Int32.ToString("G", System.Globalization.CultureInfo.CurrentCulture)`.

.NET <xref:System.IFormatProvider> uygulayan üç sınıf sağlar:

- belirli bir kültürün tarih ve saat değerleri için biçimlendirme bilgileri sağlayan bir sınıf <xref:System.Globalization.DateTimeFormatInfo>. @No__t_0 uygulama kendi örneğini döndürür.

- belirli bir kültür için sayısal biçimlendirme bilgileri sağlayan bir sınıf <xref:System.Globalization.NumberFormatInfo>. @No__t_0 uygulama kendi örneğini döndürür.

- <xref:System.Globalization.CultureInfo>. @No__t_0 uygulama, tarih ve saat değerleri için biçimlendirme bilgilerini sağlamak üzere sayısal biçimlendirme bilgileri veya <xref:System.Globalization.DateTimeFormatInfo> nesnesi sağlamak üzere bir <xref:System.Globalization.NumberFormatInfo> nesnesi döndürebilir.

Bu sınıfların herhangi birini değiştirmek için kendi biçim sağlayıcınızı de uygulayabilirsiniz. Ancak, uygulamanızın <xref:System.IFormatProvider.GetFormat%2A> yöntemi, `ToString` yöntemine biçimlendirme bilgileri sağlaması gerekiyorsa, önceki tabloda listelenen türde bir nesne döndürmelidir.

### <a name="culture-sensitive-formatting-of-numeric-values"></a>Sayısal değerlerin kültüre duyarlı biçimlendirmesi

Varsayılan olarak, sayısal değer biçimlendirmesi kültüre duyarlıdır. Bir biçimlendirme yöntemini çağırdığınızda bir kültür belirtmezseniz, geçerli iş parçacığı kültürünün biçimlendirme kuralları kullanılır. Bu, geçerli iş parçacığı kültürünü dört kez değiştiren ve sonra <xref:System.Decimal.ToString%28System.String%29?displayProperty=nameWithType> yöntemi çağıran aşağıdaki örnekte gösterilmiştir. Her durumda, sonuç dizesi geçerli kültürün biçimlendirme kurallarını yansıtır. Bunun nedeni `ToString` ve `ToString(String)` yöntemlerinin her bir sayısal türün `ToString(String, IFormatProvider)` yöntemine çağrıları sarması olur.

[!code-csharp[Conceptual.Formatting.Overview#19](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/culturespecific3.cs#19)]
[!code-vb[Conceptual.Formatting.Overview#19](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/culturespecific3.vb#19)]

Ayrıca, bir `provider` parametresine sahip `ToString` aşırı yüklemesini çağırarak ve bunu aşağıdakilerden birini geçirerek, belirli bir kültür için sayısal bir değer biçimlendirebilirsiniz:

- Biçimlendirme kuralları kullanılacak olan kültürü temsil eden <xref:System.Globalization.CultureInfo> nesne. @No__t_0 yöntemi, sayısal değerler için kültüre özgü biçimlendirme bilgileri sağlayan <xref:System.Globalization.NumberFormatInfo> nesnesi olan <xref:System.Globalization.CultureInfo.NumberFormat%2A?displayProperty=nameWithType> özelliğinin değerini döndürür.

- Kullanılacak kültüre özgü biçimlendirme kurallarını tanımlayan bir <xref:System.Globalization.NumberFormatInfo> nesnesi. @No__t_0 yöntemi kendi örneğini döndürür.

Aşağıdaki örnek, bir kayan noktalı sayıyı biçimlendirmek için Ingilizce (Birleşik Devletler) ve Ingilizce (Büyük Britanya) kültürlerini ve Fransızca ve Rusça bağımsız kültürlerini temsil eden <xref:System.Globalization.NumberFormatInfo> nesnelerini kullanır.

[!code-csharp[Conceptual.Formatting.Overview#20](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/culturespecific4.cs#20)]
[!code-vb[Conceptual.Formatting.Overview#20](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/culturespecific4.vb#20)]

### <a name="culture-sensitive-formatting-of-date-and-time-values"></a>Tarih ve saat değerlerini kültüre duyarlı olarak biçimlendirme

Varsayılan olarak, tarih ve saat değerlerinin biçimlendirmesi kültüre duyarlıdır. Bir biçimlendirme yöntemini çağırdığınızda bir kültür belirtmezseniz, geçerli iş parçacığı kültürünün biçimlendirme kuralları kullanılır. Bu, geçerli iş parçacığı kültürünü dört kez değiştiren ve sonra <xref:System.DateTime.ToString%28System.String%29?displayProperty=nameWithType> yöntemi çağıran aşağıdaki örnekte gösterilmiştir. Her durumda, sonuç dizesi geçerli kültürün biçimlendirme kurallarını yansıtır. Bunun nedeni, <xref:System.DateTime.ToString?displayProperty=nameWithType>, <xref:System.DateTime.ToString%28System.String%29?displayProperty=nameWithType>, <xref:System.DateTimeOffset.ToString?displayProperty=nameWithType> ve <xref:System.DateTimeOffset.ToString%28System.String%29?displayProperty=nameWithType> yöntemlerinin, <xref:System.DateTime.ToString%28System.String%2CSystem.IFormatProvider%29?displayProperty=nameWithType> ve <xref:System.DateTimeOffset.ToString%28System.String%2CSystem.IFormatProvider%29?displayProperty=nameWithType> yöntemlerine çağrıları sarması olur.

[!code-csharp[Conceptual.Formatting.Overview#17](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/culturespecific1.cs#17)]
[!code-vb[Conceptual.Formatting.Overview#17](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/culturespecific1.vb#17)]

Ayrıca, belirli bir kültür için bir tarih ve saat değerini, `provider` parametresine sahip bir <xref:System.DateTime.ToString%2A?displayProperty=nameWithType> veya <xref:System.DateTimeOffset.ToString%2A?displayProperty=nameWithType> aşırı yüklemeyi çağırarak ve aşağıdakilerden birini geçirerek biçimlendirebilirsiniz:

- Biçimlendirme kuralları kullanılacak olan kültürü temsil eden <xref:System.Globalization.CultureInfo> nesne. @No__t_0 yöntemi, tarih ve saat değerleri için kültüre özgü biçimlendirme bilgileri sağlayan <xref:System.Globalization.DateTimeFormatInfo> nesnesi olan <xref:System.Globalization.CultureInfo.DateTimeFormat%2A?displayProperty=nameWithType> özelliğinin değerini döndürür.

- Kullanılacak kültüre özgü biçimlendirme kurallarını tanımlayan bir <xref:System.Globalization.DateTimeFormatInfo> nesnesi. @No__t_0 yöntemi kendi örneğini döndürür.

Aşağıdaki örnek, bir tarihi biçimlendirmek için Ingilizce (Birleşik Devletler) ve Ingilizce (Büyük Britanya) kültürlerini ve Fransızca ve Rusça bağımsız kültürlerini temsil eden <xref:System.Globalization.DateTimeFormatInfo> nesnelerini kullanır.

[!code-csharp[Conceptual.Formatting.Overview#18](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/culturespecific2.cs#18)]
[!code-vb[Conceptual.Formatting.Overview#18](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/culturespecific2.vb#18)]

## <a name="the-iformattable-interface"></a>IFormattable arabirimi

Genellikle, `ToString` yöntemini bir biçim dizesiyle ve bir <xref:System.IFormatProvider> parametresiyle aşırı yükleyen türler <xref:System.IFormattable> arabirimini de uygular. Bu arabirimin, parametre olarak hem biçim dizesi hem de biçim sağlayıcısını içeren tek bir üyesi <xref:System.IFormattable.ToString%28System.String%2CSystem.IFormatProvider%29?displayProperty=nameWithType> vardır.

Uygulama tanımlı sınıfınız için <xref:System.IFormattable> arabirimini uygulamak iki avantaj sunar:

- @No__t_0 sınıfı tarafından dize dönüştürme desteği. @No__t_0 ve <xref:System.Convert.ToString%28System.Object%2CSystem.IFormatProvider%29?displayProperty=nameWithType> yöntemlerine yapılan çağrılar <xref:System.IFormattable> uygulamanızı otomatik olarak çağırır.

- Bileşik biçimlendirme desteği. Özel türünü biçimlendirmek için bir biçim dizesi içeren bir biçim öğesi kullanılırsa, ortak dil çalışma zamanı <xref:System.IFormattable> uygulamanızı otomatik olarak çağırır ve bunu biçim dizesine geçirir. @No__t_0 veya <xref:System.Console.WriteLine%2A?displayProperty=nameWithType> gibi yöntemlerle bileşik biçimlendirme hakkında daha fazla bilgi için [Bileşik biçimlendirme](#composite-formatting) bölümüne bakın.

Aşağıdaki örnek, <xref:System.IFormattable> arabirimini uygulayan bir `Temperature` sınıfını tanımlar. Sıcaklığın Santide gösterilmesi için "C" veya "G" biçim belirticilerini destekler, sıcaklığın Fahrenolması için "F" biçim belirticisi ve sıcaklığın Kelvin cinsinden gösterilmesi için "K" Biçim belirleyicisi.

[!code-csharp[Conceptual.Formatting.Overview#12](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/iformattable.cs#12)]
[!code-vb[Conceptual.Formatting.Overview#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/iformattable.vb#12)]

Aşağıdaki örnek bir `Temperature` nesnesi oluşturur. Daha sonra <xref:System.Convert.ToString%2A> yöntemini çağırır ve bir `Temperature` nesnesinin farklı dize gösterimlerini almak için birkaç bileşik biçim dizesi kullanır. Bu yöntem çağrılarının her biri, sırasıyla `Temperature` sınıfının <xref:System.IFormattable> uygulamasını çağırır.

[!code-csharp[Conceptual.Formatting.Overview#13](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/iformattable.cs#13)]
[!code-vb[Conceptual.Formatting.Overview#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/iformattable.vb#13)]

## <a name="composite-formatting"></a>Bileşik biçimlendirme

@No__t_0 ve <xref:System.Text.StringBuilder.AppendFormat%2A?displayProperty=nameWithType> gibi bazı yöntemler bileşik biçimlendirmeyi destekler. Bileşik biçim dizesi, sıfır, bir veya daha fazla nesnenin dize gösterimini içeren tek bir dize döndüren bir şablon türüdür. Her nesne, bileşik biçim dizesinde dizinli biçim öğesi tarafından temsil edilir. Biçim öğesinin dizini, yöntemin parametre listesinde temsil ettiği nesnenin konumuna karşılık gelir. Dizinler sıfır tabanlıdır. Örneğin, <xref:System.String.Format%2A?displayProperty=nameWithType> yönteminin aşağıdaki çağrısında, ilk biçim öğesi `{0:D}`, `thatDate` dize temsili ile değiştirilmiştir; ikinci biçim öğesi `{1}`, `item1` dize temsili ile değiştirilmiştir; ve üçüncü biçim öğesi `{2:C2}`, `item1.Value` dize temsili ile değiştirilmiştir.

[!code-csharp[Conceptual.Formatting.Overview#14](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/composite1.cs#14)]
[!code-vb[Conceptual.Formatting.Overview#14](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/composite1.vb#14)]

Bir biçim öğesini karşılık gelen nesnenin dize gösterimiyle değiştirmeye ek olarak, biçim öğeleri de şunları denetlemenize olanak tanır:

- Nesne <xref:System.IFormattable> arabirimini uygularsa ve biçim dizelerini destekliyorsa nesnenin dize olarak temsil edildiği belirli bir yoldur. Bunu, biçim öğesinin dizinini `:` (iki nokta üst üste) ve ardından geçerli bir biçim dizesi ile izleyerek yapabilirsiniz. Önceki örnekte, bir tarih değerini "d" (kısa tarih düzeniyle) biçim dizesiyle (örn. `{0:d}`) ve bir sayısal değeri "C2" biçim dizesiyle (örneğin, iki kesir ile bir para birimi değeri olarak göstermek için `{2:C2}`) biçimlendirerek ondalık basamaklar.

- Nesnenin dize gösterimini içeren alanın genişliği ve bu alandaki dize gösteriminin hizalaması. Bunu, biçim öğesinin dizinini `,` (virgül) ve alan genişliğini izleyerek yapın. Alan genişliği pozitif bir değer ise, dize alana sağa hizalanır ve alan genişliği negatif bir değer ise sola hizalanır. Aşağıdaki örnek, tarih değerlerini 20 karakterlik bir alanda sola hizalar ve ondalık değerleri, 11 karakterlik bir alanda tek bir kesirli basamakla sağa hizalar.

     [!code-csharp[Conceptual.Formatting.Overview#22](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/composite2.cs#22)]
     [!code-vb[Conceptual.Formatting.Overview#22](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/composite2.vb#22)]

     Hizalama dizesi bileşeni ve biçim dizesi bileşeni varsa, ilki ikincinin (örneğin, `{0,-20:g}`) önünde olduğunu unutmayın.

Bileşik biçimlendirme hakkında daha fazla bilgi için bkz. [Bileşik biçimlendirme](../../../docs/standard/base-types/composite-formatting.md).

## <a name="custom-formatting-with-icustomformatter"></a>ICustomFormatter ile özel biçimlendirme

İki bileşik biçimlendirme yöntemi, <xref:System.String.Format%28System.IFormatProvider%2CSystem.String%2CSystem.Object%5B%5D%29?displayProperty=nameWithType> ve <xref:System.Text.StringBuilder.AppendFormat%28System.IFormatProvider%2CSystem.String%2CSystem.Object%5B%5D%29?displayProperty=nameWithType>, özel biçimlendirmeyi destekleyen bir biçim sağlayıcısı parametresi içerir. Bu biçimlendirme yöntemlerinden herhangi biri çağrıldığında, biçim sağlayıcısının <xref:System.IFormatProvider.GetFormat%2A> yöntemine bir <xref:System.ICustomFormatter> arabirimini temsil eden bir <xref:System.Type> nesnesi geçirir. @No__t_0 yöntemi daha sonra özel biçimlendirme sağlayan <xref:System.ICustomFormatter> uygulamasının döndürülmesinden sorumludur.

@No__t_0 arabirimi bir bileşik biçimlendirme yöntemi tarafından otomatik olarak çağrılan ve bir bileşik biçim dizesindeki her biçim öğesi için bir kez olan <xref:System.ICustomFormatter.Format%28System.String%2CSystem.Object%2CSystem.IFormatProvider%29> tek bir yönteme sahiptir. @No__t_0 yöntemi üç parametreye sahiptir: bir biçim öğesinde `formatString` bağımsız değişkeni, biçimlendirilecek bir nesne ve biçimlendirme hizmetleri sağlayan bir <xref:System.IFormatProvider> nesnesi temsil eden bir biçim dizesi. Genellikle, <xref:System.ICustomFormatter> uygulayan sınıf de <xref:System.IFormatProvider> uygular, bu nedenle bu son parametre özel biçimlendirme sınıfının bir başvurusudur. Yöntemi, biçimlendirilecek nesnenin özel bir biçimli dize gösterimini döndürür. Yöntem nesneyi biçimlendiremiyor ise, null bir başvuru döndürmelidir (Visual Basic `Nothing`).

Aşağıdaki örnek, tamsayı değerlerini iki basamaklı bir onaltılık değerler sırası ve ardından bir boşluk olarak görüntüleyen `ByteByByteFormatter` adlı <xref:System.ICustomFormatter> bir uygulama sağlar.

[!code-csharp[Conceptual.Formatting.Overview#15](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/icustomformatter1.cs#15)]
[!code-vb[Conceptual.Formatting.Overview#15](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/icustomformatter1.vb#15)]

Aşağıdaki örnek, tamsayı değerlerini biçimlendirmek için `ByteByByteFormatter` sınıfını kullanır. @No__t_0 yönteminin ikinci <xref:System.String.Format%28System.IFormatProvider%2CSystem.String%2CSystem.Object%5B%5D%29?displayProperty=nameWithType> Yöntem çağrısında birden çok kez çağrıldığını ve varsayılan <xref:System.Globalization.NumberFormatInfo> sağlayıcının üçüncü yöntem çağrısında kullanıldığını unutmayın. `ByteByByteFormatter.Format` Yöntem, "N0" biçim dizesini tanımıyor ve null bir başvuru (`Nothing` Visual Basic) döndürüyor.

[!code-csharp[Conceptual.Formatting.Overview#16](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/icustomformatter1.cs#16)]
[!code-vb[Conceptual.Formatting.Overview#16](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/icustomformatter1.vb#16)]

## <a name="related-topics"></a>İlgili konular

|Başlık|Tanım|
|-----------|----------------|
|[Standart Sayısal Biçim Dizeleri](../../../docs/standard/base-types/standard-numeric-format-strings.md)|Sayısal değerlerin yaygın olarak kullanılan dize temsillerini oluşturan standart biçim dizelerini açıklar.|
|[Özel Sayısal Biçim Dizeleri](../../../docs/standard/base-types/custom-numeric-format-strings.md)|Sayısal değerler için uygulamaya özel biçimler oluşturan özel biçim dizelerini açıklar.|
|[Standart Tarih ve Saat Biçim Dizeleri](../../../docs/standard/base-types/standard-date-and-time-format-strings.md)|@No__t_0 değerlerinin yaygın olarak kullanılan dize temsillerini oluşturan standart biçim dizelerini açıklar.|
|[Özel Tarih ve Saat Biçim Dizeleri](../../../docs/standard/base-types/custom-date-and-time-format-strings.md)|@No__t_0 değerleri için uygulamaya özel biçimler oluşturan özel biçim dizelerini açıklar.|
|[Standart TimeSpan Biçim Dizeleri](../../../docs/standard/base-types/standard-timespan-format-strings.md)|Zaman aralıklarının yaygın olarak kullanılan dize temsillerini oluşturan standart biçim dizelerini açıklar.|
|[Özel TimeSpan Biçim Dizeleri](../../../docs/standard/base-types/custom-timespan-format-strings.md)|Zaman aralıkları için uygulamaya özel biçimler oluşturan özel biçim dizelerini açıklar.|
|[Sabit Listesi Biçim Dizeleri](../../../docs/standard/base-types/enumeration-format-strings.md)|Numaralandırma değerlerinin dize gösterimlerini oluşturmak için kullanılan standart biçim dizelerini açıklar.|
|[Bileşik Biçimlendirme](../../../docs/standard/base-types/composite-formatting.md)|Bir veya daha fazla biçimli değerin bir dizeye nasıl ekleneceğini açıklar. Dize daha sonra konsolda görüntülenebilir veya bir akışa yazılabilir.|
|[Biçimlendirme İşlemlerini Gerçekleştirme](../../../docs/standard/base-types/performing-formatting-operations.md)|Belirli biçimlendirme işlemlerini gerçekleştirmeye yönelik adım adım yönergeler sağlayan konuları listeler.|
|[Dizeleri Ayrıştırma](../../../docs/standard/base-types/parsing-strings.md)|Nesnelerin, bu nesnelerin dize temsilleri tarafından tanımlanan değerlere nasıl başlatılacağını açıklar. Ayrıştırma biçimlendirmenin ters işlemidir.|

## <a name="reference"></a>Başvuru

- <xref:System.IFormattable?displayProperty=nameWithType>
- <xref:System.IFormatProvider?displayProperty=nameWithType>
- <xref:System.ICustomFormatter?displayProperty=nameWithType>
