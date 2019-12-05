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
ms.openlocfilehash: 20aa7ecd354ef1a8982ae75eda87275c80cdaaf6
ms.sourcegitcommit: 32a575bf4adccc901f00e264f92b759ced633379
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/04/2019
ms.locfileid: "74802472"
---
# <a name="format-types-in-net"></a>.NET 'teki biçim türleri

Biçimlendirme bir sınıf, yapı ya da numaralandırma değerinin bir örneğinin kendi dize sunumuna dönüştürülmesi işlemidir, bu sayede ortaya çıkan dize kullanıcılara görüntülenebilir ya da orijinal veri türünü geri yüklemek için seri durumdan çıkarılabilir. Bu dönüştürme, bir dizi güçlük çıkarabilir:

- Değerlerin dahili olarak depolanma biçimi, zorunlu olarak kullanıcıların bunları görüntülemek isteyeceği biçimi yansıtmaz. Örneğin bir telefon numarası, kullanıcı dostu olmayan 8009999999 formunda saklanabilir. Bunun yerine 800-999-9999 olarak görüntülenebilir. Bu şekilde bir sayıyı biçimlendiren bir örnek için [özel biçim dizeleri](#custom-format-strings) bölümüne bakın.

- Bazen bir nesnenin dize gösterimindeki karşılığı beklendiği gibi değildir. Örneğin bir Sıcaklık nesnesinin ya da bir Kişi nesnesinin dize temsilinin nasıl görüneceği belirgin değildir. Bir sıcaklık nesnesini çeşitli yollarla biçimlendiren bir örnek için bkz. [standart biçim dizeleri](#standard-format-strings) bölümü.

- Değerler sıklıkla kültüre duyarlı biçimlendirme gerektirir. Örneğin sayıları parasal değerleri yansıtmak için kullanan bir uygulamada, sayısal dizeler geçerli kültürün para birimi sembolünü, grup ayırıcısını (çoğu kültürde bu bir binler ayırıcısıdır) ve ondalık sembolünü içermelidir. Bir örnek için, [biçim sağlayıcıları Ile kültüre duyarlı biçimlendirme](#culture-sensitive-formatting-with-format-providers) bölümüne bakın.

- Bir uygulama aynı değeri farklı şekillerde göstermek durumunda kalabilir. Örneğin bir uygulama bir numaralandırma üyesini, kendi adının bir dize temsilini ya da bunu temel değerini görüntüleyerek temsil edebilir. <xref:System.DayOfWeek> sabit listesinin bir üyesini farklı yollarla biçimlendiren bir örnek için bkz. [standart biçim dizeleri](#standard-format-strings) bölümü.

> [!NOTE]
> Biçimlendirme, bir türün değerini bir dize temsiline dönüştürür. Ayrıştırma biçimlendirmenin tersidir. Bir ayrıştırma işlemi kendi dize temsilinde bir veri türü örneği oluşturur. Dizeleri diğer veri türlerine dönüştürme hakkında daha fazla bilgi için bkz. [dizeleri ayrıştırma](../../../docs/standard/base-types/parsing-strings.md).

.NET, geliştiricilerin bu gereksinimleri ele almasını sağlayan zengin biçimlendirme desteği sağlar.

## <a name="formatting-in-net"></a>.NET 'te biçimlendirme

Biçimlendirme için temel mekanizma, bu konunun ilerleyen kısımlarında yer olarak [ToString yöntemi kullanılarak varsayılan biçimlendirme](#default-formatting-using-the-tostring-method) bölümünde açıklanan <xref:System.Object.ToString%2A?displayProperty=nameWithType> yönteminin varsayılan uygulamasıdır. Ancak .NET, varsayılan biçimlendirme desteğini değiştirmek ve genişletmek için çeşitli yollar sunar. Bunlar aşağıdakileri içerir:

- Bir nesnenin değerinin özel bir dize temsilini tanımlamak için <xref:System.Object.ToString%2A?displayProperty=nameWithType> yöntemini geçersiz kılma. Daha fazla bilgi için bu konunun ilerleyen kısımlarındaki [ToString yöntemini geçersiz kılma](#override-the-tostring-method) bölümüne bakın.

- Bir nesne değerinin dize temsilinin birden çok biçim almasını sağlayan biçim belirleyicilerini tanımlama. Örneğin aşağıdaki deyimde yer alan "X" biçim belirleyicisi, bir tamsayıyı onaltılık bir değerin dize temsiline dönüştürür.

     [!code-csharp[Conceptual.Formatting.Overview#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/specifier1.cs#3)]
     [!code-vb[Conceptual.Formatting.Overview#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/specifier1.vb#3)]

     Biçim belirticileri hakkında daha fazla bilgi için bkz. [ToString yöntemi ve biçim dizeleri](#the-tostring-method-and-format-strings) bölümü.

- Belirli bir kültürün biçimlendirme standartlarından yararlanmak için biçim sağlayıcılar kullanma. Örneğin aşağıdaki deyim, bir para birimi değerini, en-US kültürünün biçimlendirme kurallarını kullanarak görüntüler.

     [!code-csharp[Conceptual.Formatting.Overview#10](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/specifier1.cs#10)]
     [!code-vb[Conceptual.Formatting.Overview#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/specifier1.vb#10)]

     Biçim sağlayıcılarıyla biçimlendirme hakkında daha fazla bilgi için, [biçim sağlayıcıları](#culture-sensitive-formatting-with-format-providers) bölümüne bakın.

- Hem <xref:System.IFormattable> sınıfını içeren dize dönüşümü hem de bileşik biçimlendirmeyi desteklemek için <xref:System.Convert> arabirimini uygulama. Daha fazla bilgi için [IFormattable arabirimi](#the-iformattable-interface) bölümüne bakın.

- Daha büyük bir dizedeki bir değerin dize gösterimini katıştırmak için bileşik biçimlendirme kullanma. Daha fazla bilgi için [Bileşik biçimlendirme](#composite-formatting) bölümüne bakın.

- Komple bir özel biçimlendirme çözümü sağlamak için <xref:System.ICustomFormatter> ve <xref:System.IFormatProvider> uygulama. Daha fazla bilgi için [ıccustomformatter Ile özel biçimlendirme](#custom-formatting-with-icustomformatter) bölümüne bakın.

Aşağıdaki bölümler, bir nesneyi dize gösterimine dönüştürmek için bu yöntemleri incelemektedir.

## <a name="default-formatting-using-the-tostring-method"></a>ToString yöntemini kullanarak varsayılan biçimlendirme

<xref:System.Object?displayProperty=nameWithType> 'ten türetilen her bir tür parametresiz bir `ToString` yöntemini otomatik devralır, bu da varsayılan olarak türün adını döndürür. Aşağıdaki örnek, varsayılan `ToString` yönteminin kullanımını göstermektedir. Uygulaması olmayan `Automobile` adında bir sınıf tanımlar. Sınıfın bir örneği oluşturulduğunda ve `ToString` yöntemi çağrıldığında, tür adını görüntüler. `ToString` yönteminin örnekte açık şekilde çağrılmadığına dikkat edin. <xref:System.Console.WriteLine%28System.Object%29?displayProperty=nameWithType> yöntemi, kendisine değişken olarak geçilen nesnenin `ToString` yöntemini örtük olarak çağırır.

[!code-csharp[Conceptual.Formatting.Overview#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/default1.cs#1)]
[!code-vb[Conceptual.Formatting.Overview#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/default1.vb#1)]

> [!WARNING]
> Windows 8.1 başlayarak, Windows Çalışma Zamanı, varsayılan biçimlendirme desteği sağlayan [ıtringable. ToString](xref:Windows.Foundation.IStringable.ToString%2A)adlı tek bir yönteme sahip bir <xref:Windows.Foundation.IStringable> arabirimi içerir. Ancak yönetilen türlerin `IStringable` arabirimini uygulamamasını öneririz. Daha fazla bilgi için <xref:System.Object.ToString%2A?displayProperty=nameWithType> başvuru sayfasındaki "Windows Çalışma Zamanı ve `IStringable` arabirimi" bölümüne bakın.

Arabirimler dışında tüm türler <xref:System.Object> ile türetildiğinden, bu işlev özel sınıflarınıza ya da yapılarınıza otomatik sağlanır. Ancak varsayılan `ToString` yöntemi ile sağlanan işlev sınırlıdır: Türü tanımlamasına rağmen türün bir örneği hakkında herhangi bir bilgi sunamaz. Bir nesnenin o nesne hakkında bilgi sağlayan dize halindeki bir gösterimini sağlamak için, `ToString` yöntemini yeniden tanımlamalısınız.

> [!NOTE]
> Yapılar <xref:System.ValueType> türünden devralınır; bu ise <xref:System.Object> nesnesinden türetilmiştir. <xref:System.ValueType>, <xref:System.Object.ToString%2A?displayProperty=nameWithType> öğesini geçersiz kılmasına rağmen uygulaması aynıdır.

## <a name="override-the-tostring-method"></a>ToString yöntemini geçersiz kılma

Bir türün adını görüntülemek genelde sınırlı bir kullanımdır ve türlerinizin tüketicilerinin bir örneği bir diğerinden ayırt etmesine izin vermez. Ancak daha kullanışlı bir nesne değeri temsili sağlamak için `ToString` yöntemini geçersiz kılabilirsiniz. Aşağıdaki örnek, sıcaklığı Santigrat derece olarak görüntülemek için `ToString` yöntemini geçersiz kılan bir `Temperature` nesnesi tanımlamaktadır.

[!code-csharp[Conceptual.Formatting.Overview#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/overrides1.cs#2)]
[!code-vb[Conceptual.Formatting.Overview#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/overrides1.vb#2)]

.NET ' te, her ilkel değer türünün `ToString` yöntemi, nesnenin değerini adı yerine göstermek için geçersiz kılınır. Aşağıdaki tablo her ilkel tür için geçersiz kılmayı göstermektedir. Geçersiz kılınan yöntemlerin çoğunun başka bir `ToString` yöntemi aşırı yükü çağırdığına ve bunu, kendi türü için genel biçimi ve geçerli kültürü temsil eden bir <xref:System.IFormatProvider> nesnesini tanımlayan bir "G" biçim belirleyicisine geçirdiğine dikkat edin.

|Tür|ToString'i geçersiz kılma|
|----------|-----------------------|
|<xref:System.Boolean>|<xref:System.Boolean.TrueString?displayProperty=nameWithType> ya da<xref:System.Boolean.FalseString?displayProperty=nameWithType> döndürür.|
|<xref:System.Byte>|Geçerli kültür için <xref:System.Byte> değerini biçimlendirmek üzere `Byte.ToString("G", NumberFormatInfo.CurrentInfo)` yöntemini çağırır.|
|<xref:System.Char>|Karakteri bir dize olarak döndürür.|
|<xref:System.DateTime>|Geçerli kültür için tarih ve saat değerini biçimlendirmek üzere `DateTime.ToString("G", DatetimeFormatInfo.CurrentInfo)` yöntemini çağırır.|
|<xref:System.Decimal>|Geçerli kültür için <xref:System.Decimal> değerini biçimlendirmek üzere `Decimal.ToString("G", NumberFormatInfo.CurrentInfo)` yöntemini çağırır.|
|<xref:System.Double>|Geçerli kültür için <xref:System.Double> değerini biçimlendirmek üzere `Double.ToString("G", NumberFormatInfo.CurrentInfo)` yöntemini çağırır.|
|<xref:System.Int16>|Geçerli kültür için <xref:System.Int16> değerini biçimlendirmek üzere `Int16.ToString("G", NumberFormatInfo.CurrentInfo)` yöntemini çağırır.|
|<xref:System.Int32>|Geçerli kültür için <xref:System.Int32> değerini biçimlendirmek üzere `Int32.ToString("G", NumberFormatInfo.CurrentInfo)` yöntemini çağırır.|
|<xref:System.Int64>|Geçerli kültür için <xref:System.Int64> değerini biçimlendirmek üzere `Int64.ToString("G", NumberFormatInfo.CurrentInfo)` yöntemini çağırır.|
|<xref:System.SByte>|Geçerli kültür için <xref:System.SByte> değerini biçimlendirmek üzere `SByte.ToString("G", NumberFormatInfo.CurrentInfo)` yöntemini çağırır.|
|<xref:System.Single>|Geçerli kültür için <xref:System.Single> değerini biçimlendirmek üzere `Single.ToString("G", NumberFormatInfo.CurrentInfo)` yöntemini çağırır.|
|<xref:System.UInt16>|Geçerli kültür için <xref:System.UInt16> değerini biçimlendirmek üzere `UInt16.ToString("G", NumberFormatInfo.CurrentInfo)` yöntemini çağırır.|
|<xref:System.UInt32>|Geçerli kültür için <xref:System.UInt32> değerini biçimlendirmek üzere `UInt32.ToString("G", NumberFormatInfo.CurrentInfo)` yöntemini çağırır.|
|<xref:System.UInt64>|Geçerli kültür için <xref:System.UInt64> değerini biçimlendirmek üzere `UInt64.ToString("G", NumberFormatInfo.CurrentInfo)` yöntemini çağırır.|

## <a name="the-tostring-method-and-format-strings"></a>ToString yöntemi ve biçim dizeleri

Bir nesnede tek bir dize temsili varsa varsayılan `ToString` yöntemine ya da `ToString` geçersiz kılma işlemine güvenmek uygundur. Ancak bir nesnenin değeri genelde birden çok temsile sahiptir. Örneğin bir sıcaklık Fahrenhayt derece, Santigrat derece ya da Kelvin cinsinden ifade edilebilir. Benzer şekilde tamsayı değeri 10, 10, 10.0, 1.0e01 ya da $10,00 gibi çeşitli şekillerde temsil edilebilir.

Tek bir değerin birden çok dize temsillerine sahip olmasını sağlamak için, .NET biçim dizelerini kullanır. Bir format dizesi, tek karakterler ya da karakter gruplarının `ToString` yönteminin kendi çıkışını nasıl biçimlendirmesi gerektiğini tanımlayan bir ya da daha fazla ön tanımlı biçim belirleyicisi içeren bir dizedir. Biçim dizesi daha sonra parametre olarak nesnenin `ToString` yöntemine geçilir ve nesnenin değerinin dize gösteriminin nasıl görüneceğini belirler.

.NET 'teki tüm sayısal türler, tarih ve saat türleri ve numaralandırma türleri önceden tanımlanmış bir biçim belirteçleri kümesini destekler. Biçim dizelerini, ayrıca, uygulamanızın tanımladığı veri türleri için birden fazla dize gösterimi tanımlamak üzere kullanabilirsiniz.

### <a name="standard-format-strings"></a>Standart biçim dizeleri

Standart biçimli bir dize, nesnenin uygulandığı şeye olan dize sunumunu tanımlayan ve alfabetik bir karakter olan tek bir biçim belirticisi ve yanında sonuç dizesinde kaç hane gösterileceğini etkileyen isteğe bağlı bir hassas belirtici içerir. Hassas belirleyici yok sayılırsa ya da desteklenmiyorsa, standart biçim belirleyicisi standart biçim dizesine eşdeğerdir.

.NET, tüm sayısal türler, tüm tarih ve saat türleri ve tüm numaralandırma türleri için standart biçim belirticileri kümesi tanımlar. Örneğin bu kategorilerden her biri bir "G" standart biçim belirleyicisini destekler, bu da o türün bir değeri için genel bir dize temsili tanımlar.

Sabit listesi türleri için standart biçim dizeleri, bir değerin dize olarak gösterimini doğrudan kontrol eder. Bir sabit listesi değerinin `ToString` yöntemine geçilen biçim dizeleri, değerin dize adıyla mı ("G" ve "F" biçim belirticileri), arka plandaki tamsayı değeriyle mi ("D" biçim belirticisi) yoksa onaltılık değeriyle mi ("X" biçim belirticisi) gösterileceğini belirler. Aşağıdaki örnek, bir <xref:System.DayOfWeek> sabit listesi değerini biçimlendirmek için standart biçim dizesi kullanılmasını göstermektedir.

[!code-csharp[Conceptual.Formatting.Overview#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/standard1.cs#4)]
[!code-vb[Conceptual.Formatting.Overview#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/standard1.vb#4)]

Numaralandırma biçim dizeleri hakkında daha fazla bilgi için bkz. [numaralandırma biçim dizeleri](../../../docs/standard/base-types/enumeration-format-strings.md).

Sayısal türlerin standart biçim dizeleri, genellikle, tam görünümü bir veya daha fazla özellik değeri tarafından denetlenen bir sonuç dizesini tanımlar. Örneğin "C" biçim belirleyicisi bir sayıyı bir para birimi değeri olarak biçimlendirir. `ToString` yöntemini tek parametre olarak "C" biçim belirticisiyle çağırdığınızda, sayısal değerin dize gösterimini tanımlamak için geçerli kültürün <xref:System.Globalization.NumberFormatInfo> nesnesinin aşağıdaki özellik değerleri kullanılır:

- Geçerli kültürün para birimi sembolünü belirten <xref:System.Globalization.NumberFormatInfo.CurrencySymbol%2A> özelliği.

- Aşağıdakileri belirleyen bir tamsayı döndüren <xref:System.Globalization.NumberFormatInfo.CurrencyNegativePattern%2A> veya <xref:System.Globalization.NumberFormatInfo.CurrencyPositivePattern%2A> özelliği:

  - Para birimi sembolünün yeri.

  - Negatif değerler başta bir eksi işareti, sonda bir eksi işareti veya parantezler ile gösterilir.

  - Sayısal değer ile para birimi sembolü arasında bir boşluk olup olmayacağı.

- Sonuç dizesindeki ondalık rakamların sayısını tanımlayan <xref:System.Globalization.NumberFormatInfo.CurrencyDecimalDigits%2A> özelliği.

- Sonuç dizesindeki ondalık ayırma sembolünü tanımlayan <xref:System.Globalization.NumberFormatInfo.CurrencyDecimalSeparator%2A> özelliği.

- Grup ayırma sembolünü tanımlayan <xref:System.Globalization.NumberFormatInfo.CurrencyGroupSeparator%2A> özelliği.

- Küsur işaretinin solundaki her gruptaki rakam sayısını tanımlayan <xref:System.Globalization.NumberFormatInfo.CurrencyGroupSizes%2A> özelliği.

- Negatif değerleri göstermek için parantez kullanılmıyorsa sonuç dizesinde kullanılacak negatif işaretini belirleyen <xref:System.Globalization.NumberFormatInfo.NegativeSign%2A> özelliği.

Ek olarak, sayısal biçim dizeleri bir hassas belirleyici içerebilir. Bu belirticinin anlamı, kullanıldığı biçim dizesine bağlıdır, ancak tipik olarak sonuç dizesinde görünmesi gereken toplam rakam sayısını ya da ondalık rakam sayısını gösterir. Örneğin aşağıdaki örnek "X4" standart sayısal dizesi ve bir hassas belirleyiciyi, dört onaltılık basamağı olan bir dize oluşturmak için kullanır.

[!code-csharp[Conceptual.Formatting.Overview#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/precisionspecifier1.cs#6)]
[!code-vb[Conceptual.Formatting.Overview#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/precisionspecifier1.vb#6)]

Standart sayısal biçimlendirme dizeleri hakkında daha fazla bilgi için bkz. [Standart sayısal biçim dizeleri](../../../docs/standard/base-types/standard-numeric-format-strings.md).

Tarih ve saat değerlerinin standart biçim dizeleri, belirli bir <xref:System.Globalization.DateTimeFormatInfo> özelliği tarafından depolanan özel biçim dizelerinin diğer adlarıdır. Örneğin "D" biçim belirleyicisi olan bir tarih ve saat değerinin `ToString` yöntemini çağırmak, tarihi ve saati, geçerli kültürün <xref:System.Globalization.DateTimeFormatInfo.LongDatePattern%2A?displayProperty=nameWithType> özelliğinde saklanan özel biçim dizesini kullanarak görüntüler. (Özel biçim dizeleri hakkında daha fazla bilgi için [sonraki bölüme](#custom-format-strings)bakın.) Aşağıdaki örnekte bu ilişki gösterilmektedir.

[!code-csharp[Conceptual.Formatting.Overview#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/alias1.cs#5)]
[!code-vb[Conceptual.Formatting.Overview#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/alias1.vb#5)]

Standart Tarih ve saat biçim dizeleri hakkında daha fazla bilgi için bkz. [Standart Tarih ve saat biçim dizeleri](../../../docs/standard/base-types/standard-date-and-time-format-strings.md).

Ayrıca, uygulama tarafından tanımlanan nesnelerin, `ToString(String)` yöntemi tarafından üretilen dize gösterimlerini tanımlamak için standart biçim dizeleri kullanabilirsiniz. Nesnenizin desteklediği özgül standart biçim belirticileri tanımlayabilir ve bunların büyük/küçük harfe duyarlı olup olmayacağını belirleyebilirsiniz. `ToString(String)` yöntemi uygulamanız şunları desteklemelidir:

- Nesnenin geleneksel ya da genel bir biçimini temsil eden bir "G" biçim belirleyicisi. Nesnenizin `ToString` yönteminin parametresiz aşırı yüklemesi, "G" standart biçim dizesine geçmek için `ToString(String)` aşırı yüklemesini çağırmalıdır.

- Bir null başvuruya (Visual Basic'te `Nothing`) eşit olan bir biçim belirtici için destek. Null başvuruya eşit olan bir biçim belirleyici, "G" biçimli belirleyiciye eşdeğer kabul edilmelidir.

Örneğin bir `Temperature` sınıfı dahili olarak sıcaklığı Santigrat derece cinsinden depolayabilir ve `Temperature` nesnesinin değerini Santigrat derece, Fahrenhayt derece ve Kelvin cinsinden temsil etmek için biçim belirleyicileri kullanabilir. Aşağıdaki örnek, bir gösterim sağlar.

[!code-csharp[Conceptual.Formatting.Overview#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/appstandard1.cs#7)]
[!code-vb[Conceptual.Formatting.Overview#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/appstandard1.vb#7)]

### <a name="custom-format-strings"></a>Özel biçim dizeleri

Standart biçim dizelerine ek olarak, .NET, hem sayısal değerler hem de tarih ve saat değerleri için özel biçim dizelerini tanımlar. Özel bir biçim dizesi, bir değerin dize temsilini tanımlayan bir ya da daha fazla özel biçim belirleyicisinden oluşur. Örneğin özel tarih ve zaman biçimi dizesi "yyyy/mm/dd hh:mm:ss.ffff t zzz", bir tarihi en-US kültürü için "2008/11/15 07:45:00.0000 P -08:00" formundaki kendi dize temsiline dönüştürür. Benzer şekilde, özel biçim dizesi "0000", tamsayı değeri 12'yi "0012"'ye dönüştürür. Özel biçim dizelerinin tüm listesi için bkz. [özel tarih ve saat biçimi dizeleri](../../../docs/standard/base-types/custom-date-and-time-format-strings.md) ve [özel sayısal biçim dizeleri](../../../docs/standard/base-types/custom-numeric-format-strings.md).

Bir biçim dizesi tek bir özel biçim belirleyicisinden oluşuyorsa, standart biçim belirleyicisi ile karıştırılmaması için biçim belirleyicisinden önce yüzde (%) sembolü gelmelidir. Aşağıdaki örnek, belirli bir tarihin tek rakamlı veya iki rakamlı sayısını göstermek için "M" özel biçimini kullanmaktadır.

[!code-csharp[Conceptual.Formatting.Overview#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/singlecustom1.cs#8)]
[!code-vb[Conceptual.Formatting.Overview#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/singlecustom1.vb#8)]

Tarih ve saat değerleri için birçok standart biçim dizesi, <xref:System.Globalization.DateTimeFormatInfo> nesnesinin özellikleri tarafından tanımlanan özel biçim dizeleri için takma adlardır. Özel biçim dizeleri ayrıca, sayısal değerler ya da tarih ve saat değerleri için uygulama tanımlı biçimlendirme sunarken önemli ölçüde esneklik sunar. Birden fazla özel biçim belirticiyi tek bir özel biçim dizesinde birleştirerek hem sayısal değerler, hem tarih ve saat değerleri için özel sonuç dizelerinizi tanımlayabilirsiniz. Aşağıdaki örnek, haftanın gününü ay adı, gün ve yıldan sonra parantez içinde gösteren özel biçimli bir dize tanımlamaktadır.

[!code-csharp[Conceptual.Formatting.Overview#9](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/custom1.cs#9)]
[!code-vb[Conceptual.Formatting.Overview#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/custom1.vb#9)]

Aşağıdaki örnek bir <xref:System.Int64> değerini bölge koduyla birlikte standart, yedi rakamlı bir ABD telefon numarası olarak gösteren özel bir biçim dizesi tanımlamaktadır.

[!code-csharp[Conceptual.Formatting.Overview#21](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/telnumber1.cs#21)]
[!code-vb[Conceptual.Formatting.Overview#21](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/telnumber1.vb#21)]

Standart biçim dizeleri genelde uygulamanızın tanımladığı türlerin biçimlendirme ihtiyaçlarının tümünü yönetebilmesine rağmen türlerinizi biçimlendirmek için ayrıca özel biçim belirleyicileri tanımlayabilirsiniz.

### <a name="format-strings-and-net-types"></a>Biçimlendirme dizeleri ve .NET türleri

Tüm sayısal türler (yani, <xref:System.Byte>, <xref:System.Decimal>, <xref:System.Double>, <xref:System.Int16>, <xref:System.Int32>, <xref:System.Int64>, <xref:System.SByte>, <xref:System.Single>, <xref:System.UInt16>, <xref:System.UInt32>, <xref:System.UInt64>ve <xref:System.Numerics.BigInteger> türleri), Ayrıca, <xref:System.DateTime>, <xref:System.DateTimeOffset>, <xref:System.TimeSpan>, <xref:System.Guid>ve tüm numaralandırma türleri, biçim dizeleriyle biçimlendirmeyi destekler. Her tür tarafından desteklenen belirli biçim dizeleri hakkında daha fazla bilgi için aşağıdaki konulara bakın:

|Başlık|Tanım|
|-----------|----------------|
|[Standart Sayısal Biçim Dizeleri](../../../docs/standard/base-types/standard-numeric-format-strings.md)|Sayısal değerlerin ortak kullanılan dize temsillerini oluşturan standart biçim dizelerini açıklar.|
|[Özel Sayısal Biçim Dizeleri](../../../docs/standard/base-types/custom-numeric-format-strings.md)|Sayısal değerler için uygulamaya özel biçimler oluşturan biçim dizelerini açıklar.|
|[Standart Tarih ve Saat Biçim Dizeleri](../../../docs/standard/base-types/standard-date-and-time-format-strings.md)|<xref:System.DateTime> ve <xref:System.DateTimeOffset> değerlerinin yaygın olarak kullanılan dize temsillerini oluşturan standart biçim dizelerini açıklar.|
|[Özel Tarih ve Saat Biçim Dizeleri](../../../docs/standard/base-types/custom-date-and-time-format-strings.md)|<xref:System.DateTime> ve <xref:System.DateTimeOffset> değerleri için uygulamaya özel biçimler oluşturan özel biçim dizelerini açıklar.|
|[Standart TimeSpan Biçim Dizeleri](../../../docs/standard/base-types/standard-timespan-format-strings.md)|Ortak kullanılan zaman aralığı dize temsillerini oluşturan standart biçimli dizeleri açıklar.|
|[Özel TimeSpan Biçim Dizeleri](../../../docs/standard/base-types/custom-timespan-format-strings.md)|Zaman aralıkları için uygulamaya özel biçimler oluşturan biçim dizelerini açıklar.|
|[Sabit Listesi Biçim Dizeleri](../../../docs/standard/base-types/enumeration-format-strings.md)|Numaralandırma değerlerinin dize temsillerini oluşturmak için kullanılan standart biçim dizelerini açıklar.|
|<xref:System.Guid.ToString%28System.String%29?displayProperty=nameWithType>|<xref:System.Guid> değerleri için standart biçim dizelerini açıklar.|

## <a name="culture-sensitive-formatting-with-format-providers"></a>Biçim sağlayıcılarıyla kültüre duyarlı biçimlendirme

Biçim belirleyicileri, nesneleri biçimlendirilmenize izin vermesine rağmen, nesnelerin anlamlı bir dize temsilini üretmek için genelde ek biçimlendirme bilgisi gerekir. Örneğin bir numarayı, "C" standart biçim dizesi ya da "$ #,#.00" gibi özel bir biçim dizesi kullanarak bir para birimi değeri olarak biçimlendirmek en azından geçerli para birimi sembolü, grup ayırıcı ve ondalık ayırıcı hakkındaki bilginin biçimlendirilen dize içinde varolmasını gerektirir. .NET sürümünde bu ek biçimlendirme bilgileri, sayısal türlerin ve Tarih ve saat türlerinin `ToString` yönteminin bir veya daha fazla aşırı yüküne bir parametre olarak sağlanan <xref:System.IFormatProvider> arabirimi aracılığıyla kullanılabilir hale getirilir. <xref:System.IFormatProvider> uygulamalar, .NET 'te kültüre özgü biçimlendirmeyi desteklemek için kullanılır. Aşağıdaki örnek, farklı kültürleri gösteren üç <xref:System.IFormatProvider> nesnesiyle biçimlendirildiğinde bir nesnenin dize gösteriminin nasıl değiştiğini göstermektedir.

[!code-csharp[Conceptual.Formatting.Overview#11](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/iformatprovider1.cs#11)]
[!code-vb[Conceptual.Formatting.Overview#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/iformatprovider1.vb#11)]

<xref:System.IFormatProvider> arabiriminde <xref:System.IFormatProvider.GetFormat%28System.Type%29> adlı, biçimlendirme bilgilerini sağlayan nesne türünü belirten tek bir parametresi vardır. Yöntem o türün bir nesnesini sağlayabiliyorsa, bunu döndürür. Aksi halde, null bir başvuru döndürür (Visual Basic`Nothing`).

<xref:System.IFormatProvider.GetFormat%2A?displayProperty=nameWithType> bir geri çağırma yöntemidir. `ToString` yönteminin bir <xref:System.IFormatProvider> parametresini dahil eden bir aşırı yüklemesini çağırdığınızda, yöntem, bu <xref:System.IFormatProvider.GetFormat%2A> nesnesinin <xref:System.IFormatProvider> yöntemini çağırır. <xref:System.IFormatProvider.GetFormat%2A> yöntemi, `formatType` parametresi tarafından belirtilen gerekli biçimlendirme bilgilerini `ToString` yöntemine sağlayan bir nesne döndürmekten sorumludur.

Bir dizi biçimlendirme ya da dize dönüştürme yöntemi bir <xref:System.IFormatProvider> türü parametresi içerir, ancak birçok durumda parametrenin değeri, yöntem çağrıldığında yok sayılır. Aşağıdaki tablo, <xref:System.Type> yöntemine geçtikleri <xref:System.IFormatProvider.GetFormat%2A?displayProperty=nameWithType> nesnesinin parametresini ve türünü kullanan bazı biçimlendirme yöntemlerini listelemektedir.

|Yöntem|`formatType` parametresinin türü|
|------------|------------------------------------|
|Sayısal türlerin `ToString` yöntemi|<xref:System.Globalization.NumberFormatInfo?displayProperty=nameWithType>|
|Tarih ve saat türlerinin `ToString` yöntemi|<xref:System.Globalization.DateTimeFormatInfo?displayProperty=nameWithType>|
|<xref:System.String.Format%2A?displayProperty=nameWithType>|<xref:System.ICustomFormatter?displayProperty=nameWithType>|
|<xref:System.Text.StringBuilder.AppendFormat%2A?displayProperty=nameWithType>|<xref:System.ICustomFormatter?displayProperty=nameWithType>|

> [!NOTE]
> Sayısal türlerin ve tarih ve saat türlerinin `ToString` yöntemleri aşırı yüklenmiştir ve aşırı yüklemelerin yalnızca bazılarında bir <xref:System.IFormatProvider> parametresi vardır. Bir yöntemde bir <xref:System.IFormatProvider>, türü parametresi yoksa, bunun yerine <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=nameWithType> özelliği tarafından döndürülen nesne geçirilir. Örneğin varsayılan <xref:System.Int32.ToString?displayProperty=nameWithType> yöntemine bir çağrı, sonunda aşağıdaki gibi bir yöntem çağrısına neden olabilir: `Int32.ToString("G", System.Globalization.CultureInfo.CurrentCulture)`.

.NET <xref:System.IFormatProvider>uygulayan üç sınıf sağlar:

- <xref:System.Globalization.DateTimeFormatInfo>, belirli bir kültür için tarih ve saat değerleri için biçimlendirme bilgileri sağlayan bir sınıf. <xref:System.IFormatProvider.GetFormat%2A?displayProperty=nameWithType> uygulaması kendinin bir örneğini döndürür.

- <xref:System.Globalization.NumberFormatInfo>, belirli bir kültür için sayısal biçimlendirme bilgileri sağlayan bir sınıf. <xref:System.IFormatProvider.GetFormat%2A?displayProperty=nameWithType> uygulaması kendinin bir örneğini döndürür.

- <xref:System.Globalization.CultureInfo>. <xref:System.IFormatProvider.GetFormat%2A?displayProperty=nameWithType> uygulaması, sayısal biçimlendirme bilgisini sağlamak için bir <xref:System.Globalization.NumberFormatInfo> nesnesi ya da tarih ve saat değerleri için biçimlendirme bilgisi sağlamak için bir <xref:System.Globalization.DateTimeFormatInfo> nesnesi döndürebilir.

Ayrıca, bu sınıflardan herhangi birinin yerine geçmek üzere kendi biçim sağlayıcılarınızı uygulayabilirsiniz. Ancak uygulamanızın <xref:System.IFormatProvider.GetFormat%2A> yönteminin, `ToString` yöntemine biçimlendirme bilgileri sağlaması gerekiyorsa önceli tabloda listelenen bir tür nesnesi geri döndürmesi gerekir.

### <a name="culture-sensitive-formatting-of-numeric-values"></a>Sayısal değerlerin kültüre duyarlı biçimlendirmesi

Varsayılan olarak, sayısal değerlerin biçimlendirilmesi kültüre duyarlıdır. Bir biçimlendirme yöntemi çağırdığınızda bir kültür belirtmezseniz, geçerli iş parçası kültürünün biçimlendirme kuralları kullanılır. Bu, geçerli iş parçacığı kültürünü dört kez değiştirdikten sonra <xref:System.Decimal.ToString%28System.String%29?displayProperty=nameWithType> yöntemini çağıran aşağıdaki örnekte gösterilmektedir. Her durumda sonuç dizesi, geçerli kültürün biçimlendirme dönüşümlerini yansıtır. Bunun nedeni, `ToString` ve `ToString(String)` yöntemlerinin her sayısal türün `ToString(String, IFormatProvider)` yöntemine yapılan çağrıları sarmasıdır.

[!code-csharp[Conceptual.Formatting.Overview#19](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/culturespecific3.cs#19)]
[!code-vb[Conceptual.Formatting.Overview#19](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/culturespecific3.vb#19)]

Ayrıca, bir `provider` parametresi olan aşırı yüklenmiş bir `ToString` yöntemini çağırarak ve yönteme şunlardan birini geçerek sayısal bir değeri belirli bir kültür için biçimlendirebilirsiniz:

- Biçimlendirme kuralları kullanılacak kültürü temsil eden bir <xref:System.Globalization.CultureInfo> nesnesi. <xref:System.Globalization.CultureInfo.GetFormat%2A?displayProperty=nameWithType> Yöntemi, sayısal değerler için kültüre özel biçimlendirme bilgisini sağlayan <xref:System.Globalization.CultureInfo.NumberFormat%2A?displayProperty=nameWithType> nesnesi olan <xref:System.Globalization.NumberFormatInfo> özelliğinin değerini döndürür.

- Kullanılacak kültüre özgü biçimlendirme kurallarını tanımlayan bir <xref:System.Globalization.NumberFormatInfo> nesnesi. <xref:System.Globalization.NumberFormatInfo.GetFormat%2A> yöntemi kendinin bir örneğini döndürür.

Aşağıdaki örnek, bir kayan nokta sayısını biçimlendirmek için İngilizce (ABD) ve İngilizce (İngiltere) kültürlerini ve Fransızca ve Rusça bağımsız kültürlerini temsil eden <xref:System.Globalization.NumberFormatInfo> nesneleri kullanmaktadır.

[!code-csharp[Conceptual.Formatting.Overview#20](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/culturespecific4.cs#20)]
[!code-vb[Conceptual.Formatting.Overview#20](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/culturespecific4.vb#20)]

### <a name="culture-sensitive-formatting-of-date-and-time-values"></a>Tarih ve saat değerlerini kültüre duyarlı olarak biçimlendirme

Varsayılan olarak, tarih ve saat değerlerinin biçimlendirilmesi kültüre duyarlıdır. Bir biçimlendirme yöntemi çağırdığınızda bir kültür belirtmezseniz, geçerli iş parçası kültürünün biçimlendirme kuralları kullanılır. Bu, geçerli iş parçacığı kültürünü dört kez değiştirdikten sonra <xref:System.DateTime.ToString%28System.String%29?displayProperty=nameWithType> yöntemini çağıran aşağıdaki örnekte gösterilmektedir. Her durumda sonuç dizesi, geçerli kültürün biçimlendirme dönüşümlerini yansıtır. Bunun nedeni <xref:System.DateTime.ToString?displayProperty=nameWithType>, <xref:System.DateTime.ToString%28System.String%29?displayProperty=nameWithType>, <xref:System.DateTimeOffset.ToString?displayProperty=nameWithType> ve <xref:System.DateTimeOffset.ToString%28System.String%29?displayProperty=nameWithType> yöntemlerinin <xref:System.DateTime.ToString%28System.String%2CSystem.IFormatProvider%29?displayProperty=nameWithType> ve <xref:System.DateTimeOffset.ToString%28System.String%2CSystem.IFormatProvider%29?displayProperty=nameWithType> yöntemlerine yapılan çağrıları sarmasıdır.

[!code-csharp[Conceptual.Formatting.Overview#17](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/culturespecific1.cs#17)]
[!code-vb[Conceptual.Formatting.Overview#17](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/culturespecific1.vb#17)]

Ayrıca, bir `provider` parametresi olan aşırı yüklenmiş bir <xref:System.DateTime.ToString%2A?displayProperty=nameWithType> veya <xref:System.DateTimeOffset.ToString%2A?displayProperty=nameWithType> yöntemini çağırarak ve yönteme şunlardan birini geçerek bir tarih ve saat değerini belirli bir kültür için biçimlendirebilirsiniz:

- Biçimlendirme kuralları kullanılacak kültürü temsil eden bir <xref:System.Globalization.CultureInfo> nesnesi. <xref:System.Globalization.CultureInfo.GetFormat%2A?displayProperty=nameWithType> yöntemi, tarih ve saat değerleri için kültüre özel biçimlendirme bilgisini sağlayan <xref:System.Globalization.CultureInfo.DateTimeFormat%2A?displayProperty=nameWithType> nesnesi olan <xref:System.Globalization.DateTimeFormatInfo> özelliğinin değerini döndürür.

- Kullanılacak kültüre özgü biçimlendirme kurallarını tanımlayan bir <xref:System.Globalization.DateTimeFormatInfo> nesnesi. <xref:System.Globalization.DateTimeFormatInfo.GetFormat%2A> yöntemi kendinin bir örneğini döndürür.

Aşağıdaki örnek, bir tarihi biçimlendirmek için İngilizce (ABD) ve İngilizce (İngiltere) kültürlerini ve Fransızca ve Rusça bağımsız kültürlerini temsil eden <xref:System.Globalization.DateTimeFormatInfo> nesneleri kullanmaktadır.

[!code-csharp[Conceptual.Formatting.Overview#18](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/culturespecific2.cs#18)]
[!code-vb[Conceptual.Formatting.Overview#18](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/culturespecific2.vb#18)]

## <a name="the-iformattable-interface"></a>IFormattable arabirimi

Genellikle `ToString` yöntemine bir biçimlendirme dizesi ve bir <xref:System.IFormatProvider> parametresi ile aşırı yükleyen türler, <xref:System.IFormattable> arabirimini de uygular. Bu arabirim, <xref:System.IFormattable.ToString%28System.String%2CSystem.IFormatProvider%29?displayProperty=nameWithType> adlı, parametre olarak hem bir biçim dizesi, hem de bir biçim sağlayıcısı içeren tek bir üyeye sahiptir.

Uygulama tanımlı sınıfınız için <xref:System.IFormattable> arabirimini uygulamak iki avantaj sağlar:

- <xref:System.Convert> sınıfıyla dize dönüştürme için destek. <xref:System.Convert.ToString%28System.Object%29?displayProperty=nameWithType> uygulamanızı otomatik çağıran <xref:System.Convert.ToString%28System.Object%2CSystem.IFormatProvider%29?displayProperty=nameWithType> ve <xref:System.IFormattable> yöntemlerini çağırır.

- Bileşik biçimlendirme için destek. Özel türünüzü biçimlendirmek için bir biçim dizesi içeren bir biçim öğesi kullanılırsa, ortak dil çalışma zamanı otomatik olarak <xref:System.IFormattable> uygulamanızı çağırır ve bunu biçim dizesine geçirir. <xref:System.String.Format%2A?displayProperty=nameWithType> veya <xref:System.Console.WriteLine%2A?displayProperty=nameWithType>gibi yöntemlerle bileşik biçimlendirme hakkında daha fazla bilgi için [Bileşik biçimlendirme](#composite-formatting) bölümüne bakın.

Aşağıdaki örnek, <xref:System.IFormattable> arabirimini uygulayan bir `Temperature` sınıfını tanımlar. Sıcaklığı Santigrat cinsinden görüntülemek için "C" ya da "G" biçim belirticilerini, sıcaklığı Fahrenhayt cinsinden görüntülemek için "F" belirtecini ve sıcaklığı Kelvin cinsinden görüntülemek için "K" belirtecini destekler.

[!code-csharp[Conceptual.Formatting.Overview#12](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/iformattable.cs#12)]
[!code-vb[Conceptual.Formatting.Overview#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/iformattable.vb#12)]

Aşağıdaki örnek bir `Temperature` nesnesine öndeğer atamaktadır. <xref:System.Convert.ToString%2A> yöntemini çağırır ve bir `Temperature` nesnesinin farklı dize temsillerini elde etmek için çeşitli bileşik biçimli dizeler kullanır. Bu yöntem çağrılarından her biri, karşılık olarak `Temperature` sınıfının <xref:System.IFormattable> uygulamasını çağırır.

[!code-csharp[Conceptual.Formatting.Overview#13](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/iformattable.cs#13)]
[!code-vb[Conceptual.Formatting.Overview#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/iformattable.vb#13)]

## <a name="composite-formatting"></a>Bileşik biçimlendirme

<xref:System.String.Format%2A?displayProperty=nameWithType> ve <xref:System.Text.StringBuilder.AppendFormat%2A?displayProperty=nameWithType> gibi bazı yöntemler bileşik biçimlendirmeyi destekler. Bir bileşik format dizesi, sıfır dize temsilini, bir ya da daha fazla nesneyi kullanan tek bir dize döndüren bir şablon türüdür. Her bir nesne bileşik biçim dizesinde dizini oluşturulmuş bir biçim öğesi tarafından temsil edilir. Biçimlendirme öğesinin indisi, yöntemin parametre listesinde temsil ettiği nesnenin konumuna karşılık gelir. Dizinler sıfır tabanlıdır. Örneğin aşağıdaki <xref:System.String.Format%2A?displayProperty=nameWithType> yöntemi çağrısında, birinci biçim öğesi olan `{0:D}`, `thatDate` dize temsili ile değiştirilir; ikinci biçim öğesi olan `{1}`, `item1` dize temsili ile değiştirilir; ve üçüncü biçim öğesi olan `{2:C2}`, `item1.Value` dize temsili ile değiştirilir.

[!code-csharp[Conceptual.Formatting.Overview#14](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/composite1.cs#14)]
[!code-vb[Conceptual.Formatting.Overview#14](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/composite1.vb#14)]

Bir biçim öğesini karşılık gelen nesnenin dize gösterimiyle değiştirmeye ek olarak, biçim öğeleri de şunları denetlemenize olanak tanır:

- Nesne <xref:System.IFormattable> arabirimini uygularsa ve biçim dizelerini destekliyorsa nesnenin dize olarak temsil edildiği belirli bir yoldur. Bunu, biçim öğesinin dizinini `:` (iki nokta üst üste) ve ardından geçerli bir biçim dizesi ile izleyerek yapabilirsiniz. Önceki örnekte, bir tarih değerini "d" (kısa tarih düzeniyle) biçim dizesiyle (örn. `{0:d}`) ve bir sayısal değeri "C2" biçim dizesiyle (örneğin `{2:C2}`, iki kesirli ondalık basamaklı bir para birimi değeri olarak temsil edecek şekilde) biçimlendirerek bu bir değer.

- Nesnenin dize gösterimini içeren alanın genişliği ve bu alandaki dize gösteriminin hizalaması. Bunu, biçim öğesinin dizinini `,` (virgül) ve alan genişliğini izleyerek yapın. Alan genişliği pozitif bir değer ise, dize alana sağa hizalanır ve alan genişliği negatif bir değer ise sola hizalanır. Aşağıdaki örnek, tarih değerlerini 20 karakterlik bir alanda sola hizalar ve ondalık değerleri, 11 karakterlik bir alanda tek bir kesirli basamakla sağa hizalar.

     [!code-csharp[Conceptual.Formatting.Overview#22](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/composite2.cs#22)]
     [!code-vb[Conceptual.Formatting.Overview#22](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/composite2.vb#22)]

     Hizalama dizesi bileşeni ve biçim dizesi bileşeni varsa, ilki ikincinin (örneğin, `{0,-20:g}`) önünde olduğunu unutmayın.

Bileşik biçimlendirme hakkında daha fazla bilgi için bkz. [Bileşik biçimlendirme](../../../docs/standard/base-types/composite-formatting.md).

## <a name="custom-formatting-with-icustomformatter"></a>ICustomFormatter ile özel biçimlendirme

İki bileşik biçimlendirme yöntemi, <xref:System.String.Format%28System.IFormatProvider%2CSystem.String%2CSystem.Object%5B%5D%29?displayProperty=nameWithType> ve <xref:System.Text.StringBuilder.AppendFormat%28System.IFormatProvider%2CSystem.String%2CSystem.Object%5B%5D%29?displayProperty=nameWithType>, özel biçimlendirmeyi destekleyen bir biçim sağlayıcı parametresi içerir. Bu biçimlendirme yöntemlerinden biri çağrıldığında, yöntem, biçim sağlayıcının <xref:System.Type> yöntemine bir <xref:System.ICustomFormatter> arabimini temsil eden bir <xref:System.IFormatProvider.GetFormat%2A> nesnesi geçer. <xref:System.IFormatProvider.GetFormat%2A> yöntemi, bundan sonra, özel biçimlendirme sağlayan <xref:System.ICustomFormatter> uygulamasını döndürmekten sorumludur.

<xref:System.ICustomFormatter> arabiriminin <xref:System.ICustomFormatter.Format%28System.String%2CSystem.Object%2CSystem.IFormatProvider%29> adlı, bileşik bir biçimlendirme yöntemi tarafından, bileşik bir biçimlendirme dizesindeki her biçimlendirme öğesi için bir kez olmak üzere otomatik olarak çağrılan tek bir yöntemi vardır. <xref:System.ICustomFormatter.Format%28System.String%2CSystem.Object%2CSystem.IFormatProvider%29> yönteminin üç parametresi vardır: bir biçim öğesindeki `formatString` değişkenini temsil eden bir biçim dizesi, biçimlendirilecek bir nesne ve biçimlendirme hizmetleri sağlayan bir <xref:System.IFormatProvider> nesnesi. Genellikle <xref:System.ICustomFormatter> arabirimini uygulayan sınıf <xref:System.IFormatProvider> arabirimini de uygular, bu yüzden son parametre özel biçimlendirme sınıfının kendisine bir başvurudur. Yöntem, biçimlendirilecek nesnenin özel bir biçimlendirilmiş dize gösterimini döndürür. Yöntem nesneyi biçimlendiremiyorsa, bir null başvurusu (Visual Basic'te `Nothing`) döndürür.

Aşağıdaki örnek, tamsayı değerlerini iki rakamlı onaltılık bir dizi değer ve ardından bir boşluk ile görüntüleyen `ByteByByteFormatter` adlı bir <xref:System.ICustomFormatter> uygulaması vermektedir.

[!code-csharp[Conceptual.Formatting.Overview#15](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/icustomformatter1.cs#15)]
[!code-vb[Conceptual.Formatting.Overview#15](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/icustomformatter1.vb#15)]

Aşağıdaki örnek, tamsayı değerlerini biçimlendirmek için `ByteByByteFormatter` sınıfını kullanmaktadır. <xref:System.ICustomFormatter.Format%2A?displayProperty=nameWithType> yönteminin ikinci <xref:System.String.Format%28System.IFormatProvider%2CSystem.String%2CSystem.Object%5B%5D%29?displayProperty=nameWithType> Yöntem çağrısında birden çok kez çağrıldığını ve varsayılan <xref:System.Globalization.NumberFormatInfo> sağlayıcının üçüncü yöntem çağrısında kullanıldığını unutmayın.`ByteByByteFormatter.Format` Yöntem, "N0" biçim dizesini tanımıyor ve null bir başvuru (`Nothing` Visual Basic) döndürüyor.

[!code-csharp[Conceptual.Formatting.Overview#16](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/icustomformatter1.cs#16)]
[!code-vb[Conceptual.Formatting.Overview#16](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/icustomformatter1.vb#16)]

## <a name="related-topics"></a>İlgili konular

|Başlık|Tanım|
|-----------|----------------|
|[Standart Sayısal Biçim Dizeleri](../../../docs/standard/base-types/standard-numeric-format-strings.md)|Sayısal değerlerin ortak kullanılan dize temsillerini oluşturan standart biçim dizelerini açıklar.|
|[Özel Sayısal Biçim Dizeleri](../../../docs/standard/base-types/custom-numeric-format-strings.md)|Sayısal değerler için uygulamaya özel biçimler oluşturan biçim dizelerini açıklar.|
|[Standart Tarih ve Saat Biçim Dizeleri](../../../docs/standard/base-types/standard-date-and-time-format-strings.md)|<xref:System.DateTime> değerlerinin ortak kullanılan dize temsillerini oluşturan standart biçim dizelerini açıklar.|
|[Özel Tarih ve Saat Biçim Dizeleri](../../../docs/standard/base-types/custom-date-and-time-format-strings.md)|<xref:System.DateTime>değerleri için uygulamaya özel biçimler oluşturan biçim dizelerini açıklar.|
|[Standart TimeSpan Biçim Dizeleri](../../../docs/standard/base-types/standard-timespan-format-strings.md)|Ortak kullanılan zaman aralığı dize temsillerini oluşturan standart biçimli dizeleri açıklar.|
|[Özel TimeSpan Biçim Dizeleri](../../../docs/standard/base-types/custom-timespan-format-strings.md)|Zaman aralıkları için uygulamaya özel biçimler oluşturan biçim dizelerini açıklar.|
|[Sabit Listesi Biçim Dizeleri](../../../docs/standard/base-types/enumeration-format-strings.md)|Numaralandırma değerlerinin dize temsillerini oluşturmak için kullanılan standart biçim dizelerini açıklar.|
|[Bileşik Biçimlendirme](../../../docs/standard/base-types/composite-formatting.md)|Bir ya da daha fazla biçimlendirilmiş değerin bir dizeye nasıl katıştırılacağını açıklar. Dize daha sonra konsolda gösterilebilir veya bir akışa yazılabilir.|
|[Biçimlendirme İşlemlerini Gerçekleştirme](../../../docs/standard/base-types/performing-formatting-operations.md)|Özel biçimlendirme işlemlerini gerçekleştirmek için adım adım talimatları sağlayan konuları listeler.|
|[Dizeleri Ayrıştırma](../../../docs/standard/base-types/parsing-strings.md)|Nesnelerin, bu nesnelerin dize temsilleriyle açıklanan değerlere nasıl başlatılacağını açıklar. Ayrıştırma biçimlendirmenin ters işlemidir.|

## <a name="reference"></a>Başvuru

- <xref:System.IFormattable?displayProperty=nameWithType>
- <xref:System.IFormatProvider?displayProperty=nameWithType>
- <xref:System.ICustomFormatter?displayProperty=nameWithType>
