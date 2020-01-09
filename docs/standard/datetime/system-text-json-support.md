---
title: System.Text.Json üzerinde DateTime ve DateTimeOffset desteği
description: DateTime ve DateTimeOffset türlerinin System. Text. JSON kitaplığında nasıl desteklenbir genel bakış.
ms.technology: dotnet-standard
author: layomia
ms.author: laakinri
ms.date: 07/22/2019
helpviewer_keywords:
- JSON, Serializer, Utf8
- JSON DateTime, JSON DateTimeOffset
- DateTime, DateTimeOffset
- JsonSerializer, Utf8JsonReader, Utf8JsonWriter, JsonElement, JsonDocument
- JSON Serializer, JSON Reader, JSON Writer
- Converter, JSON Converter, DateTime Converter
- ISO, ISO 8601, ISO 8601-1:2019
ms.openlocfilehash: 8198359e2c54c4ed098703fbcc070f7469b3362a
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75344648"
---
# <a name="datetime-and-datetimeoffset-support-in-systemtextjson"></a>System.Text.Json üzerinde DateTime ve DateTimeOffset desteği

System. Text. JSON kitaplığı, ISO 8601:-2019 genişletilmiş profiline göre <xref:System.DateTime> ve <xref:System.DateTimeOffset> değerlerini ayrıştırır ve yazar.
[Dönüştürücüler](xref:System.Text.Json.Serialization.JsonConverter%601) , <xref:System.Text.Json.JsonSerializer>serileştirmek ve seri durumdan çıkarmak için özel destek sağlar.
Ayrıca, <xref:System.Text.Json.Utf8JsonReader> ve <xref:System.Text.Json.Utf8JsonWriter>kullanılırken özel destek de uygulanabilir.

## <a name="support-for-the-iso-8601-12019-format"></a>ISO 8601-1:2019 biçimi desteği

<xref:System.Text.Json.JsonSerializer>, <xref:System.Text.Json.Utf8JsonReader>, <xref:System.Text.Json.Utf8JsonWriter>ve <xref:System.Text.Json.JsonElement> türleri, ISO 8601-1:2019 biçiminin genişletilmiş profiline göre <xref:System.DateTime> ve <xref:System.DateTimeOffset> metin gösterimlerini ayrıştırır ve yazar; Örneğin, 2019-07-26T16:59:57-05:00.

<xref:System.DateTime> ve <xref:System.DateTimeOffset> verileri <xref:System.Text.Json.JsonSerializer>ile seri hale getirilebilir:

[!code-csharp[example-serializing-with-jsonserializer](~/samples/snippets/standard/datetime/json/csharp/serializing-with-jsonserializer/Program.cs)]

Ayrıca, <xref:System.Text.Json.JsonSerializer>seri durumdan çıkarılabilirler:

[!code-csharp[example-deserializing-with-jsonserializer-valid](~/samples/snippets/standard/datetime/json/csharp/deserializing-with-jsonserializer-valid/Program.cs)]

Varsayılan seçeneklerle, giriş <xref:System.DateTime> ve <xref:System.DateTimeOffset> metin temsilleri, genişletilmiş ISO 8601-1:2019 profiline uymalıdır.
Profille uyumlu olmayan temsiller serisini kaldırma girişimi <xref:System.Text.Json.JsonSerializer> <xref:System.Text.Json.JsonException>oluşturmasına neden olur:

[!code-csharp[example-deserializing-with-jsonserializer-error](~/samples/snippets/standard/datetime/json/csharp/deserializing-with-jsonserializer-error/Program.cs)]

<xref:System.Text.Json.JsonDocument>, <xref:System.DateTime> ve <xref:System.DateTimeOffset> temsilleri dahil olmak üzere bir JSON yükünün içeriğine yapılandırılmış erişim sağlar. Aşağıdaki örnekte, bir sıcaklığın toplanması verildiğinde, Mondays ortalama sıcaklık hesaplanabilecek nasıl hesaplanacağı gösterilmektedir:

[!code-csharp[example-computing-with-jsondocument-valid](~/samples/snippets/standard/datetime/json/csharp/computing-with-jsondocument-valid/Program.cs)]

Uyumlu olmayan <xref:System.DateTime> gösterimlerle yük verilen ortalama sıcaklığı hesaplama girişimi <xref:System.Text.Json.JsonDocument> bir <xref:System.FormatException>oluşturmasına neden olur:

[!code-csharp[example-computing-with-jsondocument-error](~/samples/snippets/standard/datetime/json/csharp/computing-with-jsondocument-error/Program.cs)]

Alt düzey <xref:System.Text.Json.Utf8JsonWriter> <xref:System.DateTime> ve <xref:System.DateTimeOffset> verileri Yazar:

[!code-csharp[example-writing-with-utf8jsonwriter](~/samples/snippets/standard/datetime/json/csharp/writing-with-utf8jsonwriter/Program.cs)]

<xref:System.DateTime> ve <xref:System.DateTimeOffset> verileri <xref:System.Text.Json.Utf8JsonReader> ayrıştırır:

[!code-csharp[example-reading-with-utf8jsonreader-valid](~/samples/snippets/standard/datetime/json/csharp/reading-with-utf8jsonreader-valid/Program.cs)]

<xref:System.Text.Json.Utf8JsonReader> uyumlu olmayan biçimleri okuma girişimi, <xref:System.FormatException>oluşturmasına neden olur:

[!code-csharp[example-reading-with-utf8jsonreader-error](~/samples/snippets/standard/datetime/json/csharp/reading-with-utf8jsonreader-error/Program.cs)]

## <a name="custom-support-for-xrefsystemdatetime-and-xrefsystemdatetimeoffset"></a><xref:System.DateTime> ve <xref:System.DateTimeOffset> için özel destek

### <a name="when-using-xrefsystemtextjsonjsonserializer"></a><xref:System.Text.Json.JsonSerializer> kullanırken

Seri hale getiricinin özel ayrıştırma veya biçimlendirme gerçekleştirmesini istiyorsanız [özel dönüştürücüler](xref:System.Text.Json.Serialization.JsonConverter%601)uygulayabilirsiniz.
İşte birkaç örnek:

#### <a name="using-datetimeoffsetparse-and-datetimeoffsettostring"></a>`DateTime(Offset).Parse` ve `DateTime(Offset).ToString` kullanma

Giriş <xref:System.DateTime> veya <xref:System.DateTimeOffset> metin temsillerinizin biçimlerini belirleyemiyoruz, dönüştürücünün okuma mantığınızdaki `DateTime(Offset).Parse` yöntemini kullanabilirsiniz. Bu, kullanmanıza olanak sağlar. ISO 8601 dizeleri ve genişletilmiş ISO 8601-1:2019 profiliyle uyumlu olmayan ISO 8601 biçimleri dahil olmak üzere çeşitli <xref:System.DateTime> ve <xref:System.DateTimeOffset> metin biçimlerini ayrıştırmak için NET kapsamlı destek. Bu yaklaşım, seri hale getiricinin yerel uygulamasını kullanmaktan önemli ölçüde daha az performansız.

Serileştirme için, dönüştürücü yazma mantığınızdaki `DateTime(Offset).ToString` yöntemini kullanabilirsiniz. Bu, herhangi bir [Standart Tarih ve saat biçiminden](../base-types/standard-date-and-time-format-strings.md)ve [özel tarih ve saat biçimlerinden](../base-types/custom-date-and-time-format-strings.md)birini kullanarak <xref:System.DateTime> ve <xref:System.DateTimeOffset> değerleri yazmanızı sağlar.
Bu, serileştiricinin yerel uygulamasını kullanmaktan çok önemli ölçüde daha düşüktür.

[!code-csharp[example-showing-datetime-parse](~/samples/snippets/standard/datetime/json/csharp/datetime-converter-examples/example1/Program.cs)]

> [!NOTE]
> <xref:System.Text.Json.Serialization.JsonConverter%601>uygularken ve `T` <xref:System.DateTime>, `typeToConvert` parametresi her zaman `typeof(DateTime)`olur.
Parametresi, çok biçimli durumları işlemek için ve çok yönlü bir şekilde `typeof(T)` almak için genel türler kullanılırken kullanışlıdır.

#### <a name="using-xrefsystembufferstextutf8parser-and-xrefsystembufferstextutf8formatter"></a><xref:System.Buffers.Text.Utf8Parser> ve <xref:System.Buffers.Text.Utf8Formatter> kullanma

Giriş <xref:System.DateTime> veya <xref:System.DateTimeOffset> metin TEMSİLLERİNİZ "R", "l", "O" veya "G" [Standart Tarih ve saat biçimi dizelerinden](../base-types/standard-date-and-time-format-strings.md)biriyle uyumluysa veya bu biçimlerden birine göre yazmak istiyorsanız dönüştürücü MANTıĞıNıZDAKI hızlı UTF-8 tabanlı ayrıştırma ve biçimlendirme yöntemlerini kullanabilirsiniz. Bu, `DateTime(Offset).Parse` ve `DateTime(Offset).ToString`kullanmaktan çok daha hızlıdır.

Bu örnek [, değerleri "R" standart biçimine](../base-types/standard-date-and-time-format-strings.md#the-rfc1123-r-r-format-specifier)göre seri hale getirip <xref:System.DateTime> serileştirtiren özel bir dönüştürücüyü gösterir:

[!code-csharp[example-showing-utf8-parser-and-formatter](~/samples/snippets/standard/datetime/json/csharp/datetime-converter-examples/example2/Program.cs)]

> [!NOTE]
> "R" standart biçimi her zaman 29 karakter uzunluğunda olacaktır.

#### <a name="using-datetimeoffsetparse-as-a-fallback-to-the-serializers-native-parsing"></a>Seri hale getiricinin yerel ayrıştırmaya geri dönüş olarak `DateTime(Offset).Parse` kullanma

Genellikle giriş <xref:System.DateTime> veya <xref:System.DateTimeOffset> verilerinizi genişletilmiş ISO 8601-1:2019 profiline uyacak şekilde bekleliyorsanız, serileştiricinin yerel ayrıştırma mantığını kullanabilirsiniz. Ayrıca, bir geri dönüş mekanizmasını tek bir durumda uygulayabilirsiniz.
Bu örnek, <xref:System.Text.Json.Utf8JsonReader.TryGetDateTime(System.DateTime@)>kullanarak bir <xref:System.DateTime> metin temsilini ayrıştırmaya başarısız olduktan sonra, dönüştürücünün <xref:System.DateTime.Parse(System.String)>kullanarak verileri başarıyla ayrıştırdığı gösterilmektedir.

[!code-csharp[example-showing-datetime-parse-as-fallback](~/samples/snippets/standard/datetime/json/csharp/datetime-converter-examples/example3/Program.cs)]

### <a name="when-writing-with-xrefsystemtextjsonutf8jsonwriter"></a><xref:System.Text.Json.Utf8JsonWriter> yazma sırasında

<xref:System.Text.Json.Utf8JsonWriter>ile özel bir <xref:System.DateTime> veya <xref:System.DateTimeOffset> metin temsili yazmak isterseniz, özel gösteriminizi <xref:System.String>, `ReadOnlySpan<Byte>`, `ReadOnlySpan<Char>`veya <xref:System.Text.Json.JsonEncodedText>olarak biçimlendirebilir, ardından bunu karşılık gelen <xref:System.Text.Json.Utf8JsonWriter.WriteStringValue%2A?displayProperty=nameWithType> veya <xref:System.Text.Json.Utf8JsonWriter.WriteString%2A?displayProperty=nameWithType> yöntemine geçirebilirsiniz.

Aşağıdaki örnek, <xref:System.DateTime.ToString(System.String,System.IFormatProvider)>bir özel <xref:System.DateTime> biçiminin nasıl oluşturulabileceğini gösterir ve <xref:System.Text.Json.Utf8JsonWriter.WriteStringValue(System.String)> yöntemiyle yazılır:

[!code-csharp[example-custom-writing-with-utf8jsonwriter](~/samples/snippets/standard/datetime/json/csharp/custom-writing-with-utf8jsonwriter/Program.cs)]

### <a name="when-reading-with-xrefsystemtextjsonutf8jsonreader"></a><xref:System.Text.Json.Utf8JsonReader> ile okurken

<xref:System.Text.Json.Utf8JsonReader>ile özel bir <xref:System.DateTime> veya <xref:System.DateTimeOffset> metin gösterimini okumak istiyorsanız, geçerli JSON belirtecinin değerini <xref:System.Text.Json.Utf8JsonReader.GetString>kullanarak <xref:System.String> olarak alabilir ve ardından özel mantık kullanarak değeri ayrıştırın.

Aşağıdaki örnek, bir özel <xref:System.DateTimeOffset> metin gösteriminin <xref:System.Text.Json.Utf8JsonReader.GetString>kullanarak nasıl alınamayacağını gösterir ve ardından <xref:System.DateTimeOffset.ParseExact(System.String,System.String,System.IFormatProvider)>kullanılarak ayrıştırılır:

[!code-csharp[example-custom-reading-with-utf8jsonreader](~/samples/snippets/standard/datetime/json/csharp/custom-reading-with-utf8jsonreader/Program.cs)]

## <a name="the-extended-iso-8601-12019-profile-in-systemtextjson"></a>System. Text. JSON dosyasındaki genişletilmiş ISO 8601-1:2019 profili

### <a name="date-and-time-components"></a>Tarih ve saat bileşenleri

<xref:System.Text.Json> uygulanan genişletilmiş ISO 8601-1:2019 profili, tarih ve saat temsilleri için aşağıdaki bileşenleri tanımlar. Bu bileşenler, <xref:System.DateTime> ve <xref:System.DateTimeOffset> temsillerini ayrıştırırken ve biçimlendirirken desteklenen çeşitli ayrıntı düzeyi düzeylerini tanımlamak için kullanılır.

| Bileşen       | Biçimi                      | Açıklama                                                                     |
|-----------------|-----------------------------|---------------------------------------------------------------------------------|
| Yıl            | "yyyy"                      | 0001-9999                                                                       |
| Ay           | "AA"                        | 01-12                                                                           |
| Gün             | "dd"                        | 01-28, 01-29, 01-30, 01-31, ay/yıl temelinde                                  |
| Saat            | "HH"                        | 00-23                                                                           |
| Dakika          | "mm"                        | 00-59                                                                           |
| Saniye          | "ss"                        | 00-59                                                                           |
| İkinci kesir | "FFFFFFF"                   | En az bir rakam, en fazla 16 basamak                                      |
| Zaman boşluğu     | "K"                         | "Z" ya da "(' + '/'-') HH ': ' mm"                                                |
| Kısmi saat    | "HH": ' mm ': ' ss [FFFFFFF] "     | UTC fark bilgisi olmayan süre                                             |
| Tam Tarih       | "yyyy'-'MM'-'dd"            | Takvim tarihi                                                                   |
| Tam zaman       | "' Kısmi time'K"           | Yerel Saat ve UTC arasında saat farkına sahip günün UTC günü veya yerel saati |
| Tarih saat       | "' Tam tarih ' 'T ' ' tam zaman '" | Takvim tarihi ve günün saati, ör. 2019-07-26T16:59:57-05:00                   |

### <a name="support-for-parsing"></a>Ayrıştırma desteği

Aşağıdaki ayrıntı düzeyi, ayrıştırma için tanımlanmıştır:

1. ' Tam tarih '
    1. "yyyy'-'MM'-'dd"

2. "' Tam tarih ' 'T ' ' saat ' ': ' ' dakika '"
    1. "yyyy'-'MM'-'dd'T'HH ': ' mm"

3. "' Tam tarih ' 'T ' ' kısmi zaman '"
    1. "yyyy'-'MM'-'dd'T'HH ': ' mm ': ' ss" ([sıralanabilir ("s") Biçim belirleyicisi](../base-types/standard-date-and-time-format-strings.md#the-sortable-s-format-specifier))
    2. "yyyy'-'MM'-'dd'T'HH ': ' mm ': ' ss '. ' FFFFFFF

4. "' Tam tarih ' 'T ' ' saat saat ' ': ' ' dakika ' ' zaman boşluğu '"
    1. "yyyy'-'MM'-'dd'T'HH ': ' mmZ"
    2. "yyyy'-'MM'-'dd'T'HH ': ' mm (' + '/'-') HH ': ' mm"

5. ' Tarih saat '
    1. "yyyy'-'MM'-'dd'T'HH ': ' mm ': ' ssZ"
    2. "yyyy'-'MM'-'dd'T'HH ': ' mm ': ' ss '. ' FFFFFFFZ"
    3. "yyyy'-'MM'-'dd'T'HH ': ' mm ': ' ss (' + '/'-') HH ': ' mm"
    4. "yyyy'-'MM'-'dd'T'HH ': ' mm ': ' ss '. ' FFFFFFF (' + '/'-') HH ': ' mm "

Saniyeler için ondalık kesirler varsa, en az bir rakam olmalıdır; `2019-07-26T00:00:00.` izin verilmiyor.
16 ' ya kadar kesirli basamağa izin verildiğinde, yalnızca ilk yedi ayrıştırılır. Bundan sonraki bir şey sıfır olarak kabul edilir.
Örneğin, `2019-07-26T00:00:00.1234567890` `2019-07-26T00:00:00.1234567`gibi ayrıştırılacaktır.
Bu, bu çözümüyle sınırlı <xref:System.DateTime> uygulamasıyla uyumlu kalmasıdır.

Artık saniyeler desteklenmez.

### <a name="support-for-formatting"></a>Biçimlendirme desteği

Biçimlendirme için aşağıdaki ayrıntı düzeyi düzeyleri tanımlanmıştır:

1. "' Tam tarih ' 'T ' ' kısmi zaman '"
    1. "yyyy'-'MM'-'dd'T'HH ': ' mm ': ' ss" ([sıralanabilir ("s") Biçim belirleyicisi](../base-types/standard-date-and-time-format-strings.md#the-sortable-s-format-specifier))

        Kesirli saniye olmadan ve hiçbir konum bilgisi olmadan bir <xref:System.DateTime> biçimlendirmek için kullanılır.

    2. "yyyy'-'MM'-'dd'T'HH ': ' mm ': ' ss '. ' FFFFFFF

        Bir <xref:System.DateTime> Kesirli saniyeler ile biçimlendirmek için kullanılır, ancak bu bilgiler, konum bilgisi olmadan.

2. ' Tarih saat '
    1. "yyyy'-'MM'-'dd'T'HH ': ' mm ': ' ssZ"

        Bir <xref:System.DateTime> Kesirli saniyeler olmadan, ancak UTC bir uzaklığa göre biçimlendirmek için kullanılır.

    2. "yyyy'-'MM'-'dd'T'HH ': ' mm ': ' ss '. ' FFFFFFFZ"

        <xref:System.DateTime> Kesirli saniyeler ile ve UTC denkbir uzaklığa göre biçimlendirmek için kullanılır.

    3. "yyyy'-'MM'-'dd'T'HH ': ' mm ': ' ss (' + '/'-') HH ': ' mm"

        Bir <xref:System.DateTime> veya <xref:System.DateTimeOffset> Kesirli saniyeler olmadan, ancak yerel bir uzaklığa göre biçimlendirmek için kullanılır.

    4. "yyyy'-'MM'-'dd'T'HH ': ' mm ': ' ss '. ' FFFFFFF (' + '/'-') HH ': ' mm "

        Bir <xref:System.DateTime> veya <xref:System.DateTimeOffset> Kesirli saniyeler ile ve yerel bir uzaklığa göre biçimlendirmek için kullanılır.

Varsa, en fazla 7 kesirli basamak yazılır. Bu, bu çözümlenle sınırlı <xref:System.DateTime> uygulamayla hizalanır.
