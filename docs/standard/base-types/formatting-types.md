---
title: .NET'te biçimlendirme türleri
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
ms.openlocfilehash: 124c32a09a32dd90b8b96b39aa80352094030b23
ms.sourcegitcommit: 79b0dd8bfc63f33a02137121dd23475887ecefda
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/01/2020
ms.locfileid: "80523954"
---
# <a name="format-types-in-net"></a>.NET'teki biçim türlerini biçimlendirme

Biçimlendirme, genellikle elde edilen dizekullanıcılara görüntülenebileceği veya özgün veri türünü geri yüklemek için deserialized böylece, bir sınıf, yapı veya numaralandırma değeri bir örnek dönüştürme işlemidir. Bu dönüştürme bir takım zorluklar oluşturabilir:

- Değerlerin dahili olarak depolanma şekli, kullanıcıların bunları görüntülemek isteme biçimini yansıtmaz. Örneğin, bir telefon numarası kullanıcı dostu olmayan 8009999999 formunda depolanabilir. Bunun yerine 800-999-9999 olarak görüntülenmelidir. Bir sayıyı bu şekilde biçimlendiren bir örnek için [Özel Biçim Dizeleri](#custom-format-strings) bölümüne bakın.

- Bazen bir nesnenin dize gösterimine dönüştürülmesi sezgisel değildir. Örneğin, bir Sıcaklık nesnesinin veya Bir Kişi nesnesinin dize gösteriminin nasıl görünmesi gerektiği açık değildir. Sıcaklık nesnesini çeşitli şekillerde biçimlendiren bir örnek [için, Standart Biçim Dizeleri](#standard-format-strings) bölümüne bakın.

- Değerler genellikle kültüre duyarlı biçimlendirme gerektirir. Örneğin, sayıları parasal değerleri yansıtmak için kullanan bir uygulamada, sayısal dizeler geçerli kültürün para birimi simgesini, grup ayırıcısını (çoğu kültürde binlerce ayırıcıdır) ve ondalık sembolü içermelidir. Örneğin, [biçim sağlayıcıları bölümüyle Kültüre duyarlı biçimlendirme](#culture-sensitive-formatting-with-format-providers) bölümüne bakın.

- Bir uygulamanın aynı değeri farklı şekillerde görüntülemesi gerekebilir. Örneğin, bir uygulama, adının dize temsilini görüntüleyerek veya temel değerini görüntüleyerek numaralandırma üyesini temsil edebilir. Numaralandırmanın bir üyesini <xref:System.DayOfWeek> farklı şekillerde biçimlendiren bir örnek için, Standart Biçim [Dizeleri](#standard-format-strings) bölümüne bakın.

> [!NOTE]
> Biçimlendirme, bir türün değerini dize gösterimine dönüştürür. Ayrıştırma biçimlendirme nin tersidir. Ayrıştırma işlemi, dize gösteriminden bir veri türü örneği oluşturur. Dizeleri diğer veri türlerine dönüştürme hakkında bilgi için [bkz.](../../../docs/standard/base-types/parsing-strings.md)

.NET, geliştiricilerin bu gereksinimleri karşılamasını sağlayan zengin biçimlendirme desteği sağlar.

## <a name="formatting-in-net"></a>.NET'te biçimlendirme

Biçimlendirme için temel mekanizma, daha <xref:System.Object.ToString%2A?displayProperty=nameWithType> sonra bu konudaki ToString Yöntemi ni [kullanarak Varsayılan Biçimlendirme](#default-formatting-using-the-tostring-method) bölümünde tartışılan yöntemin varsayılan uygulamasıdır. Ancak,.NET varsayılan biçimlendirme desteğini değiştirmek ve genişletmek için çeşitli yollar sağlar. Bunlar aşağıdakileri içerir:

- Nesnenin <xref:System.Object.ToString%2A?displayProperty=nameWithType> değerinin özel bir dize temsilini tanımlamak için yöntemi geçersiz kılma. Daha fazla bilgi için, bu konunun ilerleyen bölümlerinde [ToString Yöntemini Geçersiz Kılma](#override-the-tostring-method) bölümüne bakın.

- Bir nesnenin değerinin dize gösteriminin birden çok form almasını sağlayan biçim belirteçleri tanımlama. Örneğin, aşağıdaki deyimdeki "X" biçimi belirtici, bir tamsayıyı hexadecimal değerin dize gösterimine dönüştürür.

     [!code-csharp[Conceptual.Formatting.Overview#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/specifier1.cs#3)]
     [!code-vb[Conceptual.Formatting.Overview#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/specifier1.vb#3)]

     Biçim belirteçleri hakkında daha fazla bilgi için [ToString Yöntemi ve Biçim Dizeleri](#the-tostring-method-and-format-strings) bölümüne bakın.

- Belirli bir kültürün biçimlendirme kurallarından yararlanmak için biçim sağlayıcılarını kullanma. Örneğin, aşağıdaki deyim, en-ABD kültürünün biçimlendirme kurallarını kullanarak bir para birimi değeri görüntüler.

     [!code-csharp[Conceptual.Formatting.Overview#10](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/specifier1.cs#10)]
     [!code-vb[Conceptual.Formatting.Overview#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/specifier1.vb#10)]

     Biçim sağlayıcılarıyla biçimlendirme hakkında daha fazla bilgi için [Biçim Sağlayıcıları](#culture-sensitive-formatting-with-format-providers) bölümüne bakın.

- Hem dize dönüşümlerini sınıf la hem de bileşik biçimlendirmeyle desteklemek için <xref:System.IFormattable> arabirimi uygulama. <xref:System.Convert> Daha fazla bilgi için [IFormattable Interface](#the-iformattable-interface) bölümüne bakın.

- Bir değerin dize temsilini daha büyük bir dizeye gömmek için bileşik biçimlendirme kullanma. Daha fazla bilgi için [Bileşik Biçimlendirme](#composite-formatting) bölümüne bakın.

- Uygulama <xref:System.ICustomFormatter> ve <xref:System.IFormatProvider> tam bir özel biçimlendirme çözümü sağlamak. Daha fazla bilgi için [ICustomFormatter bölümüyle Özel Biçimlendirme](#custom-formatting-with-icustomformatter) bölümüne bakın.

Aşağıdaki bölümlerde bir nesneyi dize gösterimine dönüştürmek için bu yöntemler inceleyin.

## <a name="default-formatting-using-the-tostring-method"></a>ToString yöntemini kullanarak varsayılan biçimlendirme

<xref:System.Object?displayProperty=nameWithType> Otomatik olarak türetilen her tür varsayılan olarak `ToString` türün adını döndüren parametresiz bir yöntem devralır. Aşağıdaki örnekte varsayılan `ToString` yöntem gösteriş verilmiştir. Hiçbir uygulama olan `Automobile` adlı bir sınıf tanımlar. Sınıf anında ve yöntemi `ToString` çağrıldığında, onun tür adını görüntüler. Yöntemin `ToString` örnekte açıkça çağrılmadığını unutmayın. Yöntem, <xref:System.Console.WriteLine%28System.Object%29?displayProperty=nameWithType> kendisine aktarılan `ToString` nesnenin yöntemini dolaylı olarak bağımsız değişken olarak çağırır.

[!code-csharp[Conceptual.Formatting.Overview#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/default1.cs#1)]
[!code-vb[Conceptual.Formatting.Overview#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/default1.vb#1)]

> [!WARNING]
> Windows 8.1 ile başlayarak, Windows <xref:Windows.Foundation.IStringable> Runtime tek bir yöntem, [IStringable.ToString](xref:Windows.Foundation.IStringable.ToString%2A), varsayılan biçimlendirme desteği sağlayan bir arabirim içerir. Ancak, yönetilen türlerin arabirimi uygulamamalarını `IStringable` öneririz. Daha fazla bilgi için başvuru sayfasındaki `IStringable` "Windows Çalışma <xref:System.Object.ToString%2A?displayProperty=nameWithType> Zamanı ve Arabirim" bölümüne bakın.

Arabirimler dışındaki tüm türler türetildiği <xref:System.Object>için, bu işlevsellik özel sınıflarınıza veya yapılarınıza otomatik olarak sağlanır. Ancak, varsayılan `ToString` yöntem tarafından sunulan işlevsellik sınırlıdır: türü tanımlasa da, türün bir örneği hakkında herhangi bir bilgi sağlamaz. Bu nesne hakkında bilgi sağlayan bir nesnenin dize gösterimi `ToString` sağlamak için yöntemi geçersiz kılmanız gerekir.

> [!NOTE]
> Yapılar devralır <xref:System.ValueType>, sırayla <xref:System.Object>türetilir. Geçersiz <xref:System.ValueType> kılar, <xref:System.Object.ToString%2A?displayProperty=nameWithType>uygulanması aynıdır.

## <a name="override-the-tostring-method"></a>ToString yöntemini geçersiz kıl

Bir türün adını görüntülemek genellikle sınırlı kullanıma sahiptir ve türünüzün tüketicilerin bir örneği diğerinden ayırt etmesine izin vermez. Ancak, bir nesnenin `ToString` değerinin daha yararlı bir temsili sağlamak için yöntemi geçersiz kılabilirsiniz. Aşağıdaki örnek, bir `Temperature` nesneyi tanımlar `ToString` ve sıcaklığı santigrat derecede görüntülemek için yöntemini geçersiz kılar.

[!code-csharp[Conceptual.Formatting.Overview#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/overrides1.cs#2)]
[!code-vb[Conceptual.Formatting.Overview#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/overrides1.vb#2)]

.NET'te, `ToString` her ilkel değer türünün yöntemi, nesnenin adını n yerine değerini görüntülemek için geçersiz kılınmıştır. Aşağıdaki tablo, her ilkel tür için geçersiz kılmayı gösterir. Geçersiz kılınan yöntemlerin çoğunun `ToString` yöntemin başka bir aşırı yüklemesini çağırdığını ve türü için genel biçimi tanımlayan "G" biçim belirticisini ve geçerli kültürü temsil eden bir <xref:System.IFormatProvider> nesneyi geçtiğini unutmayın.

|Tür|ToString geçersiz kılma|
|----------|-----------------------|
|<xref:System.Boolean>|Ya <xref:System.Boolean.TrueString?displayProperty=nameWithType> da <xref:System.Boolean.FalseString?displayProperty=nameWithType>.|
|<xref:System.Byte>|Geçerli `Byte.ToString("G", NumberFormatInfo.CurrentInfo)` kültürün <xref:System.Byte> değerini biçimlendirmek için çağrılar.|
|<xref:System.Char>|Karakteri dize olarak döndürür.|
|<xref:System.DateTime>|Geçerli `DateTime.ToString("G", DatetimeFormatInfo.CurrentInfo)` kültürün tarih ve saat değerini biçimlendirmek için çağrılar.|
|<xref:System.Decimal>|Geçerli `Decimal.ToString("G", NumberFormatInfo.CurrentInfo)` kültürün <xref:System.Decimal> değerini biçimlendirmek için çağrılar.|
|<xref:System.Double>|Geçerli `Double.ToString("G", NumberFormatInfo.CurrentInfo)` kültürün <xref:System.Double> değerini biçimlendirmek için çağrılar.|
|<xref:System.Int16>|Geçerli `Int16.ToString("G", NumberFormatInfo.CurrentInfo)` kültürün <xref:System.Int16> değerini biçimlendirmek için çağrılar.|
|<xref:System.Int32>|Geçerli `Int32.ToString("G", NumberFormatInfo.CurrentInfo)` kültürün <xref:System.Int32> değerini biçimlendirmek için çağrılar.|
|<xref:System.Int64>|Geçerli `Int64.ToString("G", NumberFormatInfo.CurrentInfo)` kültürün <xref:System.Int64> değerini biçimlendirmek için çağrılar.|
|<xref:System.SByte>|Geçerli `SByte.ToString("G", NumberFormatInfo.CurrentInfo)` kültürün <xref:System.SByte> değerini biçimlendirmek için çağrılar.|
|<xref:System.Single>|Geçerli `Single.ToString("G", NumberFormatInfo.CurrentInfo)` kültürün <xref:System.Single> değerini biçimlendirmek için çağrılar.|
|<xref:System.UInt16>|Geçerli `UInt16.ToString("G", NumberFormatInfo.CurrentInfo)` kültürün <xref:System.UInt16> değerini biçimlendirmek için çağrılar.|
|<xref:System.UInt32>|Geçerli `UInt32.ToString("G", NumberFormatInfo.CurrentInfo)` kültürün <xref:System.UInt32> değerini biçimlendirmek için çağrılar.|
|<xref:System.UInt64>|Geçerli `UInt64.ToString("G", NumberFormatInfo.CurrentInfo)` kültürün <xref:System.UInt64> değerini biçimlendirmek için çağrılar.|

## <a name="the-tostring-method-and-format-strings"></a>ToString yöntemi ve biçim dizeleri

Varsayılan `ToString` yönteme güvenmek veya `ToString` bir nesne tek bir dize gösterimi olduğunda geçersiz kılma uygundur. Ancak, bir nesnenin değeri genellikle birden çok gösterimi vardır. Örneğin, bir sıcaklık fahrenhayt, santigrat derece veya kelvins derece cinsinden ifade edilebilir. Benzer şekilde, 10'un tümsedo değeri 10, 10,0, 1,0e01 veya 10,00 TL dahil olmak üzere çeşitli şekillerde temsil edilebilir.

.NET, tek bir değerin birden çok dize gösterimine sahip olmasını sağlamak için biçim dizeleri kullanır. Biçim dizesi, `ToString` yöntemin çıktısını nasıl biçimlendirmesi gerektiğini tanımlayan tek karakterler veya karakter grupları olan bir veya daha fazla önceden tanımlanmış biçim belirticiiçeren bir dizedir. Biçim dizesi daha sonra nesnenin `ToString` yöntemine bir parametre olarak geçirilir ve bu nesnenin değerinin dize gösteriminin nasıl görünyeceklerini belirler.

.NET'teki tüm sayısal türleri, tarih ve saat türleri ve numaralandırma türleri önceden tanımlanmış biçim belirteçleri kümesini destekler. Uygulama tanımlı veri türlerinizin birden çok dize temsilini tanımlamak için biçim dizeleri de kullanabilirsiniz.

### <a name="standard-format-strings"></a>Standart biçim dizeleri

Standart biçim dizesi, uygulandığı nesnenin dize gösterimini tanımlayan alfabetik bir karakter olan tek bir biçim belirticive sonuç dizesinde kaç basamak görüntüleneceğini etkileyen isteğe bağlı bir kesinlik belirteç içerir. Hassas belirtici atlanırsa veya desteklenmiyorsa, standart biçim belirtici standart biçim dizesine eşdeğerdir.

.NET, tüm sayısal türler, tüm tarih ve saat türleri ve tüm numaralandırma türleri için standart biçim belirteçleri kümesi tanımlar. Örneğin, bu kategorilerin her biri, bu tür bir değerin genel dize gösterimini tanımlayan bir "G" standart biçim belirtimini destekler.

Numaralandırma türleri için standart biçim dizeleri doğrudan bir değerin dize gösterimini denetler. Numaralandırma değerinin `ToString` yöntemine geçirilen biçim dizeleri, değerin dize adı ("G" ve "F" biçim belirleyicileri), temel integral değeri ("D" biçim belirtileyicisi) veya hexadecimal değeri ("X" biçim belirtileyicisi) kullanılarak görüntülenip görüntülenmediğini belirler. Aşağıdaki örnekte, numaralandırma değerini biçimlendirmek <xref:System.DayOfWeek> için standart biçim dizeleri kullanımı gösterilmektedir.

[!code-csharp[Conceptual.Formatting.Overview#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/standard1.cs#4)]
[!code-vb[Conceptual.Formatting.Overview#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/standard1.vb#4)]

Numaralandırma biçimi dizeleri hakkında daha fazla bilgi için [bkz.](../../../docs/standard/base-types/enumeration-format-strings.md)

Sayısal türler için standart biçim dizeleri genellikle kesin görünümü bir veya daha fazla özellik değerleri tarafından denetlenen bir sonuç dizesini tanımlar. Örneğin, "C" biçimi, bir sayıyı para birimi değeri olarak biçimlendiriyor. Tek parametre `ToString` olarak "C" biçimi belirtimi yapılan yöntemi çağırdığınızda, sayısal değerin dize temsilini tanımlamak için geçerli kültürün <xref:System.Globalization.NumberFormatInfo> nesnesinden aşağıdaki özellik değerleri kullanılır:

- Geçerli <xref:System.Globalization.NumberFormatInfo.CurrencySymbol%2A> kültürün para birimi simgesini belirten özellik.

- Aşağıdakileri belirleyen bir karşıcıyı döndüren <xref:System.Globalization.NumberFormatInfo.CurrencyNegativePattern%2A> özellik veya <xref:System.Globalization.NumberFormatInfo.CurrencyPositivePattern%2A> özellik:

  - Para birimi sembolünün yerleşimi.

  - Negatif değerlerin önde gelen negatif işaretle, sondaki negatif işaretle veya parantezle mi gösterilirse,

  - Sayısal değer ile para birimi simgesi arasında bir boşluk görünüp görünmediği.

- Sonuç <xref:System.Globalization.NumberFormatInfo.CurrencyDecimalDigits%2A> dizesinde kesirli basamak sayısını tanımlayan özellik.

- Sonuç <xref:System.Globalization.NumberFormatInfo.CurrencyDecimalSeparator%2A> dizesinde ondalık ayırıcı simgesini tanımlayan özellik.

- Grup <xref:System.Globalization.NumberFormatInfo.CurrencyGroupSeparator%2A> ayırıcı sembolütanımlayan özellik.

- Ondalık <xref:System.Globalization.NumberFormatInfo.CurrencyGroupSizes%2A> adedin solundaki her gruptaki basamak sayısını tanımlayan özellik.

- Parantez <xref:System.Globalization.NumberFormatInfo.NegativeSign%2A> negatif değerleri belirtmek için kullanılmazsa, sonuç dizesinde kullanılan negatif işareti belirleyen özellik.

Buna ek olarak, sayısal biçim dizeleri bir hassas belirteç içerebilir. Bu belirticinin anlamı, kullanıldığı biçim dizelerine bağlıdır, ancak genellikle toplam basamak sayısını veya sonuç dizesinde görünmesi gereken kesirli basamak sayısını gösterir. Örneğin, aşağıdaki örnekte "X4" standart sayısal dize ve dört hexadecimal basamak olan bir dize değeri oluşturmak için bir kesinlik belirteç kullanır.

[!code-csharp[Conceptual.Formatting.Overview#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/precisionspecifier1.cs#6)]
[!code-vb[Conceptual.Formatting.Overview#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/precisionspecifier1.vb#6)]

Standart sayısal biçimlendirme dizeleri hakkında daha fazla bilgi için [Standart Sayısal Biçim Dizeleri'ne](../../../docs/standard/base-types/standard-numeric-format-strings.md)bakın.

Tarih ve saat değerleri için standart biçim dizeleri, belirli <xref:System.Globalization.DateTimeFormatInfo> bir özellik tarafından depolanan özel biçim dizeleri için diğer adlardır. Örneğin, "D" biçimi belirtimi ile bir tarih ve saat değeri `ToString` yöntemini çağırmak, geçerli kültürün <xref:System.Globalization.DateTimeFormatInfo.LongDatePattern%2A?displayProperty=nameWithType> özelliğinde depolanan özel biçim dizesini kullanarak tarih ve saati görüntüler. (Özel biçim dizeleri hakkında daha fazla bilgi için [sonraki bölüme](#custom-format-strings)bakın.) Aşağıdaki örnek, bu ilişkiyi göstermektedir.

[!code-csharp[Conceptual.Formatting.Overview#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/alias1.cs#5)]
[!code-vb[Conceptual.Formatting.Overview#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/alias1.vb#5)]

Standart tarih ve saat biçimi dizeleri hakkında daha fazla bilgi için [Standart Tarih ve Saat Biçimi Dizeleri'ne](../../../docs/standard/base-types/standard-date-and-time-format-strings.md)bakın.

Nesnenin `ToString(String)` yöntemi tarafından üretilen uygulama tanımlı bir nesnenin dize temsilini tanımlamak için standart biçim dizeleri de kullanabilirsiniz. Nesnenizin desteklediği belirli standart biçim belirteçlerini tanımlayabilir ve bunların büyük/küçük harf duyarlı mı yoksa büyük/küçük harf duyarlı mı olduğunu belirleyebilirsiniz. `ToString(String)` Yöntemin uygulanması aşağıdakileri desteklemelidir:

- Nesnenin alışılmış veya ortak biçimini temsil eden bir "G" biçimi belirtimi. Nesnenizin `ToString` yönteminin parametresiz aşırı yükü `ToString(String)` aşırı yüklemesini aramalı ve "G" standart biçim dizesini geçirmelidir.

- Null reference'a eşit bir biçim belirtici`Nothing` desteği (Visual Basic'te). Null reference'a eşit bir biçim belirticisi "G" biçimi belirticisine eşdeğer olarak kabul edilmelidir.

Örneğin, bir `Temperature` sınıf sıcaklığı santigrat derece cinsinden dahili olarak depolayabilir ve `Temperature` cismin derece, Fahrenhayt ve kelvin cinsinden değerini temsil edecek biçim belirteçleri kullanabilir. Aşağıdaki örnek, bir gösterim sağlar.

[!code-csharp[Conceptual.Formatting.Overview#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/appstandard1.cs#7)]
[!code-vb[Conceptual.Formatting.Overview#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/appstandard1.vb#7)]

### <a name="custom-format-strings"></a>Özel biçim dizeleri

.NET, standart biçim dizelerine ek olarak, hem sayısal değerler hem de tarih ve saat değerleri için özel biçim dizeleri tanımlar. Özel biçim dizesi, bir değerin dize temsilini tanımlayan bir veya daha fazla özel biçim belirteçlerinden oluşur. Örneğin, özel tarih ve saat biçimi dizesi "yyyy/mm/dd hh:mm:ss.ffff t zzz" bir tarihi en-ABD kültürü için "2008/11/15 07:45:00.0000 P -08:00" şeklindeki dize gösterimine dönüştürür. Benzer şekilde, özel biçim dizesi "0000" 12'deki tümmsayı değerini "0012" olarak dönüştürür. Özel biçim dizeleri tam listesi için bkz: [Özel Tarih ve Saat Biçim Dizeleri](../../../docs/standard/base-types/custom-date-and-time-format-strings.md) ve Özel Sayısal Biçim [Dizeleri.](../../../docs/standard/base-types/custom-numeric-format-strings.md)

Biçim dizesi tek bir özel biçim belirticiden oluşuyorsa, biçim belirticiyüzdesi önce yüzde (%) standart bir biçim belirtici ile karışıklığı önlemek için sembol. Aşağıdaki örnekte, belirli bir tarihin ayının tek basamaklı veya iki basamaklı sayısını görüntülemek için "M" özel biçim belirtimi kullanır.

[!code-csharp[Conceptual.Formatting.Overview#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/singlecustom1.cs#8)]
[!code-vb[Conceptual.Formatting.Overview#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/singlecustom1.vb#8)]

Tarih ve saat değerleri için birçok standart biçim dizeleri, nesnenin <xref:System.Globalization.DateTimeFormatInfo> özellikleriyle tanımlanan özel biçim dizeleri için diğer adlardır. Özel biçim dizeleri, sayısal değerler veya tarih ve saat değerleri için uygulama tanımlı biçimlendirme sağlamada önemli esneklik de sunar. Birden çok özel biçim belirtimlerini tek bir özel biçim dizesi içinde birleştirerek hem sayısal değerler hem de tarih ve saat değerleri için kendi özel sonuç dizelerinizi tanımlayabilirsiniz. Aşağıdaki örnek, ay adı, gün ve yıl sonra parantez içinde haftanın gün görüntüleyen özel bir biçim dize tanımlar.

[!code-csharp[Conceptual.Formatting.Overview#9](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/custom1.cs#9)]
[!code-vb[Conceptual.Formatting.Overview#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/custom1.vb#9)]

Aşağıdaki örnek, bir <xref:System.Int64> değeri alan koduyla birlikte standart, yedi basamaklı ABD telefon numarası olarak görüntüleyen özel bir biçim dizesi tanımlar.

[!code-csharp[Conceptual.Formatting.Overview#21](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/telnumber1.cs#21)]
[!code-vb[Conceptual.Formatting.Overview#21](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/telnumber1.vb#21)]

Standart biçim dizeleri genellikle uygulama tanımlı türleriniz için biçimlendirme gereksinimlerinin çoğunu işleyebilir, ancak türlerinizi biçimlendirmek için özel biçim belirteçleri de tanımlayabilirsiniz.

### <a name="format-strings-and-net-types"></a>Dizeleri ve .NET türlerini biçimlendirme

Tüm sayısal <xref:System.Byte>türleri (yani, , <xref:System.Decimal> <xref:System.Double>, <xref:System.Int16> <xref:System.Int32> <xref:System.Int64> <xref:System.SByte> <xref:System.Single> <xref:System.UInt16> <xref:System.UInt32>, , , <xref:System.UInt64>, <xref:System.Numerics.BigInteger> , , , <xref:System.DateTime>, <xref:System.DateTimeOffset> <xref:System.TimeSpan>ve türleri), yanı sıra , , , <xref:System.Guid>, ve tüm numaralandırma türleri, biçim dizeleri ile biçimlendirme desteği. Her tür tarafından desteklenen belirli biçim dizeleri hakkında bilgi için aşağıdaki konulara bakın:

|Başlık|Tanım|
|-----------|----------------|
|[Standart Sayısal Biçim Dizeleri](../../../docs/standard/base-types/standard-numeric-format-strings.md)|Sayısal değerlerin yaygın olarak kullanılan dize gösterimlerini oluşturan standart biçim dizelerini açıklar.|
|[Özel Sayısal Biçim Dizeleri](../../../docs/standard/base-types/custom-numeric-format-strings.md)|Sayısal değerler için uygulamaya özgü biçimler oluşturan özel biçim dizelerini açıklar.|
|[Standart Tarih ve Saat Biçim Dizeleri](../../../docs/standard/base-types/standard-date-and-time-format-strings.md)|Sık kullanılan dize gösterimlerini <xref:System.DateTime> ve <xref:System.DateTimeOffset> değerlerini oluşturan standart biçim dizelerini açıklar.|
|[Özel Tarih ve Saat Biçim Dizeleri](../../../docs/standard/base-types/custom-date-and-time-format-strings.md)|Uygulama için <xref:System.DateTime> özel biçimler ve <xref:System.DateTimeOffset> değerler oluşturan özel biçim dizelerini açıklar.|
|[Standart TimeSpan Biçim Dizeleri](../../../docs/standard/base-types/standard-timespan-format-strings.md)|Zaman aralıklarının sık kullanılan dize gösterimlerini oluşturan standart biçim dizelerini açıklar.|
|[Özel TimeSpan Biçim Dizeleri](../../../docs/standard/base-types/custom-timespan-format-strings.md)|Zaman aralıkları için uygulamaya özgü biçimler oluşturan özel biçim dizelerini açıklar.|
|[Numaralandırma Biçimi Dizeleri](../../../docs/standard/base-types/enumeration-format-strings.md)|Numaralandırma değerlerinin dize gösterimlerini oluşturmak için kullanılan standart biçim dizeleri açıklar.|
|<xref:System.Guid.ToString%28System.String%29?displayProperty=nameWithType>|Değerler için <xref:System.Guid> standart biçim dizelerini açıklar.|

## <a name="culture-sensitive-formatting-with-format-providers"></a>Biçim sağlayıcılarla kültüre duyarlı biçimlendirme

Biçim belirteçleri nesnelerin biçimlendirmesini özelleştirmenize izin vermesine rağmen, nesnelerin anlamlı bir dize gösterimi oluşturma genellikle ek biçimlendirme bilgileri gerektirir. Örneğin, "C" standart biçim dizesi veya "$ #,#.00" gibi özel bir biçim dizesi kullanarak bir sayıyı para birimi değeri olarak biçimlendirmek, en azından doğru para birimi simgesi, grup ayırıcısı ve ondalık ayırıcı hakkında bilgi gerektirir. .NET'te, bu ek biçimlendirme bilgileri, sayısal türleri ve tarih ve saat türlerinin <xref:System.IFormatProvider> `ToString` bir veya daha fazla aşırı yüklemesi için bir veya daha fazla parametre olarak sağlanan arabirim aracılığıyla kullanılabilir hale getirilir. <xref:System.IFormatProvider>uygulamaları kültüre özgü biçimlendirmeyi desteklemek için .NET'te kullanılır. Aşağıdaki örnek, farklı kültürleri temsil eden üç <xref:System.IFormatProvider> nesneyle biçimlendirildiğinde bir nesnenin dize gösteriminin nasıl değiştiğini göstermektedir.

[!code-csharp[Conceptual.Formatting.Overview#11](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/iformatprovider1.cs#11)]
[!code-vb[Conceptual.Formatting.Overview#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/iformatprovider1.vb#11)]

<xref:System.IFormatProvider> Arabirim, <xref:System.IFormatProvider.GetFormat%28System.Type%29>biçimlendirme bilgileri sağlayan nesne türünü belirten tek bir parametreye sahip bir yöntem içerir. Yöntem bu tür bir nesne sağlayabilir, döndürür. Aksi takdirde, (Visual`Nothing` Basic'te) null bir başvuru döndürür.

<xref:System.IFormatProvider.GetFormat%2A?displayProperty=nameWithType>bir geri arama yöntemidir. Parametre içeren `ToString` bir <xref:System.IFormatProvider> yöntem aşırı çağırdığınızda, <xref:System.IFormatProvider.GetFormat%2A> bu <xref:System.IFormatProvider> nesnenin yöntemi çağırır. Yöntem, <xref:System.IFormatProvider.GetFormat%2A> `formatType` parametrede belirtildiği gibi gerekli biçimlendirme bilgilerini sağlayan bir nesneyi `ToString` yönteme döndürmekten sorumludur.

Biçimlendirme veya dize dönüştürme yöntemleri bir dizi <xref:System.IFormatProvider>türü bir parametre içerir, ancak çoğu durumda yöntem çağrıldığında parametre değeri yoksayılır. Aşağıdaki tabloda, parametreyi kullanan biçimlendirme yöntemlerinden bazıları <xref:System.Type> ve <xref:System.IFormatProvider.GetFormat%2A?displayProperty=nameWithType> yönteme geçtikleri nesnenin türü listelenmektedir.

|Yöntem|Parametre `formatType` türü|
|------------|------------------------------------|
|`ToString`sayısal tip yöntemi|<xref:System.Globalization.NumberFormatInfo?displayProperty=nameWithType>|
|`ToString`tarih ve saat türlerinin yöntemi|<xref:System.Globalization.DateTimeFormatInfo?displayProperty=nameWithType>|
|<xref:System.String.Format%2A?displayProperty=nameWithType>|<xref:System.ICustomFormatter?displayProperty=nameWithType>|
|<xref:System.Text.StringBuilder.AppendFormat%2A?displayProperty=nameWithType>|<xref:System.ICustomFormatter?displayProperty=nameWithType>|

> [!NOTE]
> Sayısal `ToString` türlerin yöntemleri ile tarih ve saat türleri aşırı yüklenir ve yalnızca bazı <xref:System.IFormatProvider> aşırı yüklemeler bir parametre içerir. Bir yöntemtürü <xref:System.IFormatProvider>bir parametre yoksa, <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=nameWithType> özellik tarafından döndürülen nesne yerine geçirilir. Örneğin, varsayılan <xref:System.Int32.ToString?displayProperty=nameWithType> yönteme yapılan bir çağrı, sonuçta aşağıdaki gibi `Int32.ToString("G", System.Globalization.CultureInfo.CurrentCulture)`bir yöntem çağrısıyla sonuçlanır: .

.NET uygulayan <xref:System.IFormatProvider>üç sınıf sağlar:

- <xref:System.Globalization.DateTimeFormatInfo>, belirli bir kültür için tarih ve saat değerleri için biçimlendirme bilgileri sağlayan bir sınıf. Uygulanması <xref:System.IFormatProvider.GetFormat%2A?displayProperty=nameWithType> kendi bir örneğini döndürür.

- <xref:System.Globalization.NumberFormatInfo>, belirli bir kültür için sayısal biçimlendirme bilgisi sağlayan bir sınıf. Uygulanması <xref:System.IFormatProvider.GetFormat%2A?displayProperty=nameWithType> kendi bir örneğini döndürür.

- <xref:System.Globalization.CultureInfo>. Uygulanması, <xref:System.IFormatProvider.GetFormat%2A?displayProperty=nameWithType> sayısal biçimlendirme bilgileri sağlamak için bir <xref:System.Globalization.NumberFormatInfo> nesne <xref:System.Globalization.DateTimeFormatInfo> veya tarih ve saat değerleri için biçimlendirme bilgileri sağlamak için bir nesne döndürebilir.

Ayrıca, bu sınıflardan herhangi birini değiştirmek için kendi biçim sağlayıcınızı da uygulayabilirsiniz. Ancak, `ToString` yönteme <xref:System.IFormatProvider.GetFormat%2A> biçimlendirme bilgileri sağlaması gerekiyorsa, uygulamanızın yönteminin önceki tabloda listelenen türdeki bir nesneyi döndürmesi gerekir.

### <a name="culture-sensitive-formatting-of-numeric-values"></a>Sayısal değerlerin kültüre duyarlı biçimlendirmesi

Varsayılan olarak, sayısal değerlerin biçimlendirmesi kültüre duyarlıdır. Biçimlendirme yöntemini çağırdığınızda bir kültür belirtmezseniz, geçerli iş parçacığı kültürünün biçimlendirme kuralları kullanılır. Bu, geçerli iş parçacığı kültürünü dört kez değiştiren ve yöntemi <xref:System.Decimal.ToString%28System.String%29?displayProperty=nameWithType> çağıran aşağıdaki örnekte gösterilmiştir. Her durumda, sonuç dizesi geçerli kültürün biçimlendirme kurallarını yansıtır. Bunun nedeni, `ToString` `ToString(String)` ve yöntemlerin her sayısal türün `ToString(String, IFormatProvider)` yöntemine çağrıları kaydırmasının.

[!code-csharp[Conceptual.Formatting.Overview#19](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/culturespecific3.cs#19)]
[!code-vb[Conceptual.Formatting.Overview#19](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/culturespecific3.vb#19)]

Ayrıca, parametresi olan bir `ToString` aşırı yüklemeyi çağırArak ve `provider` aşağıdakilerden birini geçirerek belirli bir kültür için sayısal bir değeri biçimlendirebilirsiniz:

- Biçimlendirme kuralları kullanılacak kültürü temsil eden bir <xref:System.Globalization.CultureInfo> nesne. Yöntemi, <xref:System.Globalization.CultureInfo.GetFormat%2A?displayProperty=nameWithType> sayısal değerler <xref:System.Globalization.CultureInfo.NumberFormat%2A?displayProperty=nameWithType> için kültüre <xref:System.Globalization.NumberFormatInfo> özgü biçimlendirme bilgileri sağlayan nesne olan özelliğin değerini döndürür.

- Kullanılacak <xref:System.Globalization.NumberFormatInfo> kültüre özgü biçimlendirme kurallarını tanımlayan bir nesne. Yöntemi <xref:System.Globalization.NumberFormatInfo.GetFormat%2A> kendi bir örneğini döndürür.

Aşağıdaki örnekte, kayan nokta sayısını biçimlendirmek için İngilizce (AMERIKA Birleşik Devletleri) ve İngilizce (Büyük Britanya) kültürlerini ve Fransız ve Rus tarafsız kültürlerini temsil eden nesneler kullanır. <xref:System.Globalization.NumberFormatInfo>

[!code-csharp[Conceptual.Formatting.Overview#20](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/culturespecific4.cs#20)]
[!code-vb[Conceptual.Formatting.Overview#20](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/culturespecific4.vb#20)]

### <a name="culture-sensitive-formatting-of-date-and-time-values"></a>Tarih ve saat değerlerinin kültüre duyarlı biçimlendirmesi

Varsayılan olarak, tarih ve saat değerlerinin biçimlendirmesi kültüre duyarlıdır. Biçimlendirme yöntemini çağırdığınızda bir kültür belirtmezseniz, geçerli iş parçacığı kültürünün biçimlendirme kuralları kullanılır. Bu, geçerli iş parçacığı kültürünü dört kez değiştiren ve yöntemi <xref:System.DateTime.ToString%28System.String%29?displayProperty=nameWithType> çağıran aşağıdaki örnekte gösterilmiştir. Her durumda, sonuç dizesi geçerli kültürün biçimlendirme kurallarını yansıtır. Bunun <xref:System.DateTime.ToString?displayProperty=nameWithType>nedeni, <xref:System.DateTime.ToString%28System.String%29?displayProperty=nameWithType>, <xref:System.DateTimeOffset.ToString?displayProperty=nameWithType>, <xref:System.DateTimeOffset.ToString%28System.String%29?displayProperty=nameWithType> , ve <xref:System.DateTime.ToString%28System.String%2CSystem.IFormatProvider%29?displayProperty=nameWithType> yöntemleri <xref:System.DateTimeOffset.ToString%28System.String%2CSystem.IFormatProvider%29?displayProperty=nameWithType> ve yöntemleri ve yöntemleri aramaları sarın olmasıdır.

[!code-csharp[Conceptual.Formatting.Overview#17](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/culturespecific1.cs#17)]
[!code-vb[Conceptual.Formatting.Overview#17](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/culturespecific1.vb#17)]

Ayrıca, parametresi olan bir veya <xref:System.DateTime.ToString%2A?displayProperty=nameWithType> <xref:System.DateTimeOffset.ToString%2A?displayProperty=nameWithType> aşırı yüklemeyi arayarak ve `provider` aşağıdakilerden birini geçirerek belirli bir kültür için tarih ve saat değerini biçimlendirebilirsiniz:

- Biçimlendirme kuralları kullanılacak kültürü temsil eden bir <xref:System.Globalization.CultureInfo> nesne. Yöntemi, <xref:System.Globalization.CultureInfo.GetFormat%2A?displayProperty=nameWithType> tarih ve <xref:System.Globalization.CultureInfo.DateTimeFormat%2A?displayProperty=nameWithType> saat değerleri için <xref:System.Globalization.DateTimeFormatInfo> kültüre özgü biçimlendirme bilgileri sağlayan nesne olan özelliğin değerini döndürür.

- Kullanılacak <xref:System.Globalization.DateTimeFormatInfo> kültüre özgü biçimlendirme kurallarını tanımlayan bir nesne. Yöntemi <xref:System.Globalization.DateTimeFormatInfo.GetFormat%2A> kendi bir örneğini döndürür.

Aşağıdaki örnekte, bir tarihi biçimlendirmek için İngilizce (AMERIKA Birleşik Devletleri) ve İngilizce (Büyük Britanya) kültürlerini ve Fransız ve Rus tarafsız kültürlerini temsil eden nesneler kullanır. <xref:System.Globalization.DateTimeFormatInfo>

[!code-csharp[Conceptual.Formatting.Overview#18](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/culturespecific2.cs#18)]
[!code-vb[Conceptual.Formatting.Overview#18](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/culturespecific2.vb#18)]

## <a name="the-iformattable-interface"></a>IFormattable arabirimi

Genellikle, bir biçim dizesi ve bir `ToString` <xref:System.IFormatProvider> parametre ile <xref:System.IFormattable> yöntemi aşırı yükleyin türleri de arabirimi uygular. Bu arabirim, <xref:System.IFormattable.ToString%28System.String%2CSystem.IFormatProvider%29?displayProperty=nameWithType>parametre olarak hem biçim dizesi hem de biçim sağlayıcısı içeren tek bir üyeye sahiptir.

Uygulama tanımlı sınıfınız için <xref:System.IFormattable> arabirimi uygulamak iki avantaj sunar:

- <xref:System.Convert> Sınıfa göre dize dönüştürme desteği. Aramalar <xref:System.Convert.ToString%28System.Object%29?displayProperty=nameWithType> ve <xref:System.Convert.ToString%28System.Object%2CSystem.IFormatProvider%29?displayProperty=nameWithType> yöntemler uygulamanızı <xref:System.IFormattable> otomatik olarak arayın.

- Bileşik biçimlendirme desteği. Özel türünüzü biçimlendirmek için biçim dizesi içeren bir biçim öğesi kullanılırsa, ortak dil çalışma süresi uygulamanızı <xref:System.IFormattable> otomatik olarak çağırır ve biçim dizesini geçirir. Bileşik biçimlendirme gibi yöntemlerle bileşik <xref:System.String.Format%2A?displayProperty=nameWithType> <xref:System.Console.WriteLine%2A?displayProperty=nameWithType>biçimlendirme hakkında daha fazla bilgi [için, Bileşik Biçimlendirme](#composite-formatting) bölümüne bakın.

Aşağıdaki örnek, `Temperature` <xref:System.IFormattable> arabirimi uygulayan bir sınıf tanımlar. Santigrat sıcaklığı görüntülemek için "C" veya "G" formatı belirteçleri destekler, Fahrenheit sıcaklık görüntülemek için "F" formatı belirtici, ve Kelvin sıcaklık görüntülemek için "K" biçimi belirtici.

[!code-csharp[Conceptual.Formatting.Overview#12](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/iformattable.cs#12)]
[!code-vb[Conceptual.Formatting.Overview#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/iformattable.vb#12)]

Aşağıdaki örnek bir `Temperature` nesneyi anında alalar. Daha sonra <xref:System.Convert.ToString%2A> yöntemi çağırır ve bir `Temperature` nesnenin farklı dize gösterimleri elde etmek için birkaç bileşik biçim dizeleri kullanır. Bu yöntemin her biri, sırayla, <xref:System.IFormattable> `Temperature` sınıfın uygulanmasını çağırır.

[!code-csharp[Conceptual.Formatting.Overview#13](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/iformattable.cs#13)]
[!code-vb[Conceptual.Formatting.Overview#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/iformattable.vb#13)]

## <a name="composite-formatting"></a>Bileşik biçimlendirme

Bazı yöntemler, <xref:System.String.Format%2A?displayProperty=nameWithType> gibi <xref:System.Text.StringBuilder.AppendFormat%2A?displayProperty=nameWithType>ve, bileşik biçimlendirme destekler. Bileşik biçim dizesi, sıfır, bir veya daha fazla nesnenin dize temsilini içeren tek bir dizeyi döndüren bir şablon türüdür. Her nesne bileşik biçim dizesinde dizinlenmiş biçim öğesi tarafından temsil edilir. Biçim öğesinin dizini, yöntemin parametre listesinde temsil ettiği nesnenin konumuna karşılık gelir. Dizinler sıfır tabanlıdır. Örneğin, <xref:System.String.Format%2A?displayProperty=nameWithType> yönteme aşağıdaki çağrıda, ilk biçim `{0:D}`öğesi, dize gösterimi `thatDate`ile değiştirilir; ikinci biçim öğesi, `{1}`, dize gösterimi `item1`ile değiştirilir; ve üçüncü biçim `{2:C2}`öğesi, , dize gösterimi `item1.Value`ile değiştirilir.

[!code-csharp[Conceptual.Formatting.Overview#14](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/composite1.cs#14)]
[!code-vb[Conceptual.Formatting.Overview#14](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/composite1.vb#14)]

Biçim öğesi, bir biçim öğesinin ilgili nesnesinin dize gösterimiyle değiştirilmesine ek olarak, biçim öğeleri de aşağıdakileri denetlemenize izin verir:

- Nesne <xref:System.IFormattable> arabirimi uygular ve biçim dizeleri destekler, bir nesne bir dize olarak temsil edilen belirli bir şekilde. Bunu, biçim öğesinin dizinini (iki `:` nokta üst üste) ve ardından geçerli bir biçim dizesi ile izleyerek yaparsınız. Önceki örnekte bunu, bir tarih değerini "d" (kısa tarih deseni) biçimlendirme `{0:d}`dizesi (örneğin,) ile biçimlendirerek ve sayısal bir değeri `{2:C2}` "C2" biçim dizesi ile biçimlendirerek (örneğin, sayıyı iki kesirli ondalık basamaklı para birimi değeri olarak temsil etmek) yapmıştır.

- Nesnenin dize gösterimini içeren alanın genişliği ve bu alandaki dize gösteriminin hizalanması. Bunu, biçim öğesinin dizini alan `,` genişliğini izleyen bir (virgül) ile izleyerek yaparsınız. Alan genişliği pozitif bir değerse dize alanda sağ hizalanır ve alan genişliği negatif bir değerse sol hizalanır. Aşağıdaki örnek, tarih değerlerini 20 karakterlik bir alana hizalar ve ondalık değerleri 11 karakterlik bir alanda bir kesirli basamakla sağa hizalar.

     [!code-csharp[Conceptual.Formatting.Overview#22](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/composite2.cs#22)]
     [!code-vb[Conceptual.Formatting.Overview#22](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/composite2.vb#22)]

     Hem hizalama dizesi bileşeni hem de biçim dize bileşeni varsa, eskisinin `{0,-20:g}`ikinciden önce geldiğini unutmayın (örneğin, .

Bileşik biçimlendirme hakkında daha fazla bilgi için [Bkz. Bileşik Biçimlendirme.](../../../docs/standard/base-types/composite-formatting.md)

## <a name="custom-formatting-with-icustomformatter"></a>ICustomFormatter ile özel biçimlendirme

İki bileşik biçimlendirme <xref:System.String.Format%28System.IFormatProvider%2CSystem.String%2CSystem.Object%5B%5D%29?displayProperty=nameWithType> <xref:System.Text.StringBuilder.AppendFormat%28System.IFormatProvider%2CSystem.String%2CSystem.Object%5B%5D%29?displayProperty=nameWithType>yöntemi ve özel biçimlendirmedestekleyen bir biçimlendirme sağlayıcısı parametresi içerir. Bu biçimlendirme yöntemlerinden biri çağrıldığında, bir <xref:System.ICustomFormatter> arabirimi temsil eden <xref:System.IFormatProvider.GetFormat%2A> bir <xref:System.Type> nesneyi biçim sağlayıcısının yöntemine geçirir. Yöntem <xref:System.IFormatProvider.GetFormat%2A> daha sonra özel biçimlendirme sağlayan <xref:System.ICustomFormatter> uygulamayı döndürmekten sorumludur.

<xref:System.ICustomFormatter> Arabirim, <xref:System.ICustomFormatter.Format%28System.String%2CSystem.Object%2CSystem.IFormatProvider%29>bileşik biçimlendirme dizesinde her biçim öğesi için bir kez, bileşik biçimlendirme yöntemi yle otomatik olarak çağrılan tek bir yönteme sahiptir. Yöntemin <xref:System.ICustomFormatter.Format%28System.String%2CSystem.Object%2CSystem.IFormatProvider%29> üç parametresi vardır: `formatString` biçim öğesindeki bağımsız değişkeni temsil eden <xref:System.IFormatProvider> biçim dizesi, biçimlendirme nesnesi ve biçimlendirme hizmetleri sağlayan bir nesne. Genellikle, uygulayan <xref:System.ICustomFormatter> sınıf da <xref:System.IFormatProvider>uygular, bu nedenle bu son parametre özel biçimlendirme sınıfının kendisine bir başvurudur. Yöntem, biçimlendirilecek nesnenin özel biçimlendirilmiş dize temsilini döndürür. Yöntem nesneyi biçimlendiremezse, null başvurusu`Nothing` (Visual Basic'te) döndürmelidir.

Aşağıdaki örnekte, <xref:System.ICustomFormatter> tamsayı değerlerini iki basamaklı heksadedemal değerlerin bir dizi olarak görüntüleyen ve ardından bir boşluk olarak görüntüleyen `ByteByByteFormatter` bir uygulama görüntülenir.

[!code-csharp[Conceptual.Formatting.Overview#15](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/icustomformatter1.cs#15)]
[!code-vb[Conceptual.Formatting.Overview#15](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/icustomformatter1.vb#15)]

Aşağıdaki örnek, `ByteByByteFormatter` sınıfını, üstbilgi değerlerini biçimlendirmek için kullanır. Yöntemin <xref:System.ICustomFormatter.Format%2A?displayProperty=nameWithType> ikinci <xref:System.String.Format%28System.IFormatProvider%2CSystem.String%2CSystem.Object%5B%5D%29?displayProperty=nameWithType> yöntem çağrısında birden fazla kez çağrıldığını ve <xref:System.Globalization.NumberFormatInfo> üçüncü yöntem çağrısında varsayılan sağlayıcının kullanıldığını unutmayın çünkü .`ByteByByteFormatter.Format` yöntem "N0" biçim dizesini tanımaz ve`Nothing` null bir başvuru (Visual Basic'te) döndürür.

[!code-csharp[Conceptual.Formatting.Overview#16](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/icustomformatter1.cs#16)]
[!code-vb[Conceptual.Formatting.Overview#16](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/icustomformatter1.vb#16)]

## <a name="related-topics"></a>İlgili konular

|Başlık|Tanım|
|-----------|----------------|
|[Standart Sayısal Biçim Dizeleri](../../../docs/standard/base-types/standard-numeric-format-strings.md)|Sayısal değerlerin yaygın olarak kullanılan dize gösterimlerini oluşturan standart biçim dizelerini açıklar.|
|[Özel Sayısal Biçim Dizeleri](../../../docs/standard/base-types/custom-numeric-format-strings.md)|Sayısal değerler için uygulamaya özgü biçimler oluşturan özel biçim dizelerini açıklar.|
|[Standart Tarih ve Saat Biçim Dizeleri](../../../docs/standard/base-types/standard-date-and-time-format-strings.md)|Sık kullanılan <xref:System.DateTime> dize temsillerini oluşturan standart biçim dizeleri açıklar.|
|[Özel Tarih ve Saat Biçim Dizeleri](../../../docs/standard/base-types/custom-date-and-time-format-strings.md)|Değerler için <xref:System.DateTime> uygulamaya özgü biçimler oluşturan özel biçim dizelerini açıklar.|
|[Standart TimeSpan Biçim Dizeleri](../../../docs/standard/base-types/standard-timespan-format-strings.md)|Zaman aralıklarının sık kullanılan dize gösterimlerini oluşturan standart biçim dizelerini açıklar.|
|[Özel TimeSpan Biçim Dizeleri](../../../docs/standard/base-types/custom-timespan-format-strings.md)|Zaman aralıkları için uygulamaya özgü biçimler oluşturan özel biçim dizelerini açıklar.|
|[Numaralandırma Biçimi Dizeleri](../../../docs/standard/base-types/enumeration-format-strings.md)|Numaralandırma değerlerinin dize gösterimlerini oluşturmak için kullanılan standart biçim dizeleri açıklar.|
|[Bileşik Biçimlendirme](../../../docs/standard/base-types/composite-formatting.md)|Bir dize ye bir veya daha fazla biçimlendirilmiş değerleri nasıl gömeceklerini açıklar. Dize daha sonra konsolda görüntülenebilir veya bir akışa yazılabilir.|
|[Dizeleri Ayrıştırma](../../../docs/standard/base-types/parsing-strings.md)|Nesneleri bu nesnelerin dize gösterimleri tarafından açıklanan değerlere nasıl başharflere getirin açıklar. Ayrıştırma biçimlendirmenin ters işlemidir.|

## <a name="reference"></a>Başvuru

- <xref:System.IFormattable?displayProperty=nameWithType>
- <xref:System.IFormatProvider?displayProperty=nameWithType>
- <xref:System.ICustomFormatter?displayProperty=nameWithType>
