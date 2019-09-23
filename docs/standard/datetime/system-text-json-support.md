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
ms.openlocfilehash: 000a6b6dc892e65b50ae413ab3cb95d2a73ef0ef
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/23/2019
ms.locfileid: "71182581"
---
# <a name="datetime-and-datetimeoffset-support-in-systemtextjson"></a>System.Text.Json üzerinde DateTime ve DateTimeOffset desteği

System. Text. JSON kitaplığı ISO 8601:-2019 genişletilmiş profiline <xref:System.DateTime> göre <xref:System.DateTimeOffset> ayrıştırır ve yazar ve değerlerini kaydeder.
[Dönüştürücüler](xref:System.Text.Json.Serialization.JsonConverter%601) ile <xref:System.Text.Json.JsonSerializer>serileştirme ve seri durumdan çıkarma için özel destek sağlar.
Ayrıca, ve <xref:System.Text.Json.Utf8JsonReader> <xref:System.Text.Json.Utf8JsonWriter>kullanılırken özel destek de uygulanabilir.

## <a name="support-for-the-iso-8601-12019-format"></a>ISO 8601-1:2019 biçimi desteği

<xref:System.Text.Json.JsonSerializer> <xref:System.DateTime> <xref:System.DateTimeOffset> , ,<xref:System.Text.Json.Utf8JsonReader>Ve türleri,ISO8601-1:2019biçiminingenişletilmişprofilinegöreayrıştırılırveyazılırvemetingösterimleridir;Örneğin,2019-07-26T16<xref:System.Text.Json.JsonElement> <xref:System.Text.Json.Utf8JsonWriter> : 59:57-05:00.

<xref:System.DateTime>ve <xref:System.DateTimeOffset> veriler ile <xref:System.Text.Json.JsonSerializer>seri hale getirilebilir:

[!code-csharp[example-serializing-with-jsonserializer](~/samples/snippets/standard/datetime/json/csharp/serializing-with-jsonserializer/Program.cs)]

Ayrıca, şu şekilde <xref:System.Text.Json.JsonSerializer>seri durumdan çıkarılabilirler:

[!code-csharp[example-deserializing-with-jsonserializer-valid](~/samples/snippets/standard/datetime/json/csharp/deserializing-with-jsonserializer-valid/Program.cs)]

Varsayılan seçeneklerle, giriş <xref:System.DateTime> ve <xref:System.DateTimeOffset> metin temsilleri, genişletilmiş ISO 8601-1:2019 profiline uymalıdır.
Profille uyumlu olmayan temsiller serisini kaldırma girişimi bir <xref:System.Text.Json.JsonSerializer> <xref:System.Text.Json.JsonException>oluşturulmasına neden olur:

[!code-csharp[example-deserializing-with-jsonserializer-error](~/samples/snippets/standard/datetime/json/csharp/deserializing-with-jsonserializer-error/Program.cs)]

, <xref:System.Text.Json.JsonDocument> <xref:System.DateTime> Ve temsilleridahilolmaküzerebirJSONyükününiçeriğineyapılandırılmışerişimsağlar.<xref:System.DateTimeOffset> Aşağıdaki örnekte, bir sıcaklığın toplanması verildiğinde, Mondays ortalama sıcaklık hesaplanabilecek nasıl hesaplanacağı gösterilmektedir:

[!code-csharp[example-computing-with-jsondocument-valid](~/samples/snippets/standard/datetime/json/csharp/computing-with-jsondocument-valid/Program.cs)]

Uyumsuz <xref:System.DateTime> gösterimlerle yük verilen ortalama sıcaklığın hesaplanmaya çalışılması, şunu oluşturmasına neden <xref:System.Text.Json.JsonDocument> <xref:System.FormatException>olur:

[!code-csharp[example-computing-with-jsondocument-error](~/samples/snippets/standard/datetime/json/csharp/computing-with-jsondocument-error/Program.cs)]

Alt düzey <xref:System.Text.Json.Utf8JsonWriter> yazmaları <xref:System.DateTime> ve <xref:System.DateTimeOffset> verileri:

[!code-csharp[example-writing-with-utf8jsonwriter](~/samples/snippets/standard/datetime/json/csharp/writing-with-utf8jsonwriter/Program.cs)]

<xref:System.Text.Json.Utf8JsonReader>ayrıştırır <xref:System.DateTime> ve<xref:System.DateTimeOffset> veriler:

[!code-csharp[example-reading-with-utf8jsonreader-valid](~/samples/snippets/standard/datetime/json/csharp/reading-with-utf8jsonreader-valid/Program.cs)]

Uyumlu olmayan biçimleri <xref:System.Text.Json.Utf8JsonReader> okumaya çalışmak bunun <xref:System.FormatException>oluşturulmasına neden olur:

[!code-csharp[example-reading-with-utf8jsonreader-error](~/samples/snippets/standard/datetime/json/csharp/reading-with-utf8jsonreader-error/Program.cs)]

## <a name="custom-support-for-xrefsystemdatetime-and-xrefsystemdatetimeoffset"></a>Ve için <xref:System.DateTime> özel destek<xref:System.DateTimeOffset>

### <a name="when-using-xrefsystemtextjsonjsonserializer"></a>Kullanırken<xref:System.Text.Json.JsonSerializer>

Seri hale getiricinin özel ayrıştırma veya biçimlendirme gerçekleştirmesini istiyorsanız [özel dönüştürücüler](xref:System.Text.Json.Serialization.JsonConverter%601)uygulayabilirsiniz.
İşte birkaç örnek:

#### <a name="using-datetimeoffsetparse-and-datetimeoffsettostring"></a>Ve `DateTime(Offset).Parse` kullanma`DateTime(Offset).ToString`

Giriş <xref:System.DateTime> `DateTime(Offset).Parse` veya <xref:System.DateTimeOffset> metin gösterimlerinizin biçimlerini belirleyebulamıyorsanız, dönüştürücüyü okuma mantığınızdaki yöntemi kullanabilirsiniz. Bu, kullanmanıza olanak sağlar. ISO olmayan 8601 dizeleri ve genişletilmiş ISO <xref:System.DateTime> 8601-1:2019 <xref:System.DateTimeOffset> profiline uymayan ISO 8601 biçimleri dahil olmak üzere çeşitli ve metin biçimlerini ayrıştırmak için net kapsamlı destek. Bu yaklaşım, seri hale getiricinin yerel uygulamasını kullanmaktan önemli ölçüde daha az performansız.

Serileştirme için, dönüştürücüyü dönüştürücü yazma mantığınızdaki ' de kullanabilirsiniz `DateTime(Offset).ToString` . Bu <xref:System.DateTime> , [Standart Tarih ve saat biçimlerinden](https://docs.microsoft.com/dotnet/standard/base-types/standard-date-and-time-format-strings)birini ve [özel tarih ve saat biçimlerini](https://docs.microsoft.com/dotnet/standard/base-types/custom-date-and-time-format-strings)kullanarak yazmanızı ve <xref:System.DateTimeOffset> değerleri yazmanızı sağlar.
Bu, serileştiricinin yerel uygulamasını kullanmaktan çok önemli ölçüde daha düşüktür.

[!code-csharp[example-showing-datetime-parse](~/samples/snippets/standard/datetime/json/csharp/datetime-converter-examples/example1/Program.cs)]

> [!NOTE]
> <xref:System.Text.Json.Serialization.JsonConverter%601>, Ve `T` olduğunda <xref:System.DateTime>, parametresi her zaman`typeof(DateTime)`olur. `typeToConvert`
Parametresi, çok biçimli durumları işlemek için ve genel türler kullanılırken performanslı bir şekilde `typeof(T)` yararlanmak için yararlıdır.

#### <a name="using-xrefsystembufferstextutf8parser-and-xrefsystembufferstextutf8formatter"></a>Ve <xref:System.Buffers.Text.Utf8Parser> kullanma<xref:System.Buffers.Text.Utf8Formatter>

Giriş <xref:System.DateTime> veya<xref:System.DateTimeOffset> metin gösterimleriniz "R", "l", "O" veya "G" [Standart Tarih ve saat biçimi dizelerinden](https://docs.microsoft.com/dotnet/standard/base-types/standard-date-and-time-format-strings)biriyle uyumluysa veya isterseniz, dönüştürücü mantığınızdaki hızlı UTF-8 tabanlı ayrıştırma ve biçimlendirme yöntemlerini kullanabilirsiniz. bu biçimlerden birine göre yazın. Bu, ve `DateTime(Offset).Parse` `DateTime(Offset).ToString`kullanmaktan çok daha hızlıdır.

Bu örnekte <xref:System.DateTime> [, değerleri "R" standart biçimine](https://docs.microsoft.com/dotnet/standard/base-types/standard-date-and-time-format-strings#the-rfc1123-r-r-format-specifier)göre seri hale getirilen ve serileştiren özel bir dönüştürücü gösterilmektedir:

[!code-csharp[example-showing-utf8-parser-and-formatter](~/samples/snippets/standard/datetime/json/csharp/datetime-converter-examples/example2/Program.cs)]

> [!NOTE]
> "R" standart biçimi her zaman 29 karakter uzunluğunda olacaktır.

#### <a name="using-datetimeoffsetparse-as-a-fallback-to-the-serializers-native-parsing"></a>Seri `DateTime(Offset).Parse` hale getiricinin yerel ayrıştırmaya geri dönüş olarak kullanma

Genellikle giriş <xref:System.DateTime> veya <xref:System.DateTimeOffset> verilerinizi genişletilmiş ISO 8601-1:2019 profiline uyacak şekilde bekleliyorsanız, serileştiricinin yerel ayrıştırma mantığını kullanabilirsiniz. Ayrıca, bir geri dönüş mekanizmasını tek bir durumda uygulayabilirsiniz.
Bu örnekte, kullanarak <xref:System.DateTime> <xref:System.Text.Json.Utf8JsonReader.TryGetDateTime(System.DateTime@)>bir metin temsilini ayrıştırmaya başarısız olduktan sonra dönüştürücünün verileri <xref:System.DateTime.Parse(System.String)>başarıyla ayrıştırır.

[!code-csharp[example-showing-datetime-parse-as-fallback](~/samples/snippets/standard/datetime/json/csharp/datetime-converter-examples/example3/Program.cs)]

### <a name="when-writing-with-xrefsystemtextjsonutf8jsonwriter"></a>İle yazarken<xref:System.Text.Json.Utf8JsonWriter>

<xref:System.DateTime> İle `ReadOnlySpan<Byte>` <xref:System.String> <xref:System.Text.Json.JsonEncodedText> `ReadOnlySpan<Char>`özel veya <xref:System.DateTimeOffset> metin temsili yazmak isterseniz, özel gösteriminizi bir,, veya olarak biçimlendirebilir, ardından karşılık gelen <xref:System.Text.Json.Utf8JsonWriter> [Utf8JsonWriter. WriteStringValue](https://docs.microsoft.com/dotnet/api/system.text.json.utf8jsonwriter.writestringvalue?view=netcore-3.0) veya [Utf8JsonWriter. WriteString](https://docs.microsoft.com/dotnet/api/system.text.json.utf8jsonwriter.writestring?view=netcore-3.0) yöntemi.

Aşağıdaki örnek, ile <xref:System.DateTime> <xref:System.DateTime.ToString(System.String,System.IFormatProvider)>nasıl özel bir biçimin oluşturulabileceğini gösterir <xref:System.Text.Json.Utf8JsonWriter.WriteStringValue(System.String)> ve yöntemi ile yazılır:

[!code-csharp[example-custom-writing-with-utf8jsonwriter](~/samples/snippets/standard/datetime/json/csharp/custom-writing-with-utf8jsonwriter/Program.cs)]

### <a name="when-reading-with-xrefsystemtextjsonutf8jsonreader"></a>İle okurken<xref:System.Text.Json.Utf8JsonReader>

<xref:System.DateTime> İle <xref:System.DateTimeOffset> <xref:System.Text.Json.Utf8JsonReader.GetString>özel veya metin gösterimini okumak istiyorsanız, geçerli JSON belirtecinin değerini bir <xref:System.String> using olarak alabilir ve ardından özel mantık kullanarak değeri ayrıştırın. <xref:System.Text.Json.Utf8JsonReader>

Aşağıdaki örnek <xref:System.DateTimeOffset> <xref:System.Text.Json.Utf8JsonReader.GetString>, kullanarak bir özel metin gösteriminin nasıl alınamayacağını gösterir ve kullanılarak <xref:System.DateTimeOffset.ParseExact(System.String,System.String,System.IFormatProvider)>ayrıştırılır:

[!code-csharp[example-custom-reading-with-utf8jsonreader](~/samples/snippets/standard/datetime/json/csharp/custom-reading-with-utf8jsonreader/Program.cs)]

## <a name="the-extended-iso-8601-12019-profile-in-systemtextjson"></a>System. Text. JSON dosyasındaki genişletilmiş ISO 8601-1:2019 profili

### <a name="date-and-time-components"></a>Tarih ve saat bileşenleri

' De <xref:System.Text.Json> uygulanan genişletilmiş ISO 8601-1:2019 profili, tarih ve saat temsilleri için aşağıdaki bileşenleri tanımlar. Bu bileşenler, ayrıştırma ve biçimlendirme <xref:System.DateTime> ve <xref:System.DateTimeOffset> temsiller için desteklenen çeşitli ayrıntı düzeyi düzeylerini tanımlamak için kullanılır.

| Bileşen       | Biçimi                      | Açıklama                                                                     |
|-----------------|-----------------------------|---------------------------------------------------------------------------------|
| Yıl            | "yyyy"                      | 0001-9999                                                                       |
| Başından           | "AA"                        | 01-12                                                                           |
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
    1. "yyyy'-'MM'-'dd'T'HH ': ' mm ': ' ss" ([sıralanabilir ("s") Biçim belirleyicisi](https://docs.microsoft.com/dotnet/standard/base-types/standard-date-and-time-format-strings#the-sortable-s-format-specifier))
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
Örneğin, `2019-07-26T00:00:00.1234567890` olduğu gibi `2019-07-26T00:00:00.1234567`ayrıştırılacaktır.
Bu, bu çözünürlükle sınırlı olan <xref:System.DateTime> uygulamayla uyumlu kalmasıdır.

Artık saniyeler desteklenmez.

### <a name="support-for-formatting"></a>Biçimlendirme desteği

Biçimlendirme için aşağıdaki ayrıntı düzeyi düzeyleri tanımlanmıştır:

1. "' Tam tarih ' 'T ' ' kısmi zaman '"
    1. "yyyy'-'MM'-'dd'T'HH ': ' mm ': ' ss" ([sıralanabilir ("s") Biçim belirleyicisi](https://docs.microsoft.com/dotnet/standard/base-types/standard-date-and-time-format-strings#the-sortable-s-format-specifier))

        Kesirli saniyeler <xref:System.DateTime> olmadan ve hiçbir konum bilgisi olmadan biçimlendirmek için kullanılır.

    2. "yyyy'-'MM'-'dd'T'HH ': ' mm ': ' ss '. ' FFFFFFF

        Kesirli saniyeler <xref:System.DateTime> ile biçimlendirmek için kullanılır, ancak bu bilgiler, konum bilgisi olmadan.

2. ' Tarih saat '
    1. "yyyy'-'MM'-'dd'T'HH ': ' mm ': ' ssZ"

        Kesirli saniyeleri, ancak <xref:System.DateTime> UTC <xref:System.DateTimeOffset> boşluğu olmadan biçimlendirmek için kullanılır.

    2. "yyyy'-'MM'-'dd'T'HH ': ' mm ': ' ss '. ' FFFFFFFZ"

        Bir <xref:System.DateTime> veya<xref:System.DateTimeOffset> kesirli saniyeleri ve UTC bir sapmayı biçimlendirmek için kullanılır.

    3. "yyyy'-'MM'-'dd'T'HH ': ' mm ': ' ss (' + '/'-') HH ': ' mm"

        Kesirli saniyeleri <xref:System.DateTime> veya <xref:System.DateTimeOffset> yerel bir kaydırmadan biçimlendirmek için kullanılır.

    4. "yyyy'-'MM'-'dd'T'HH ': ' mm ': ' ss '. ' FFFFFFF (' + '/'-') HH ': ' mm "

        Bir <xref:System.DateTime> veya<xref:System.DateTimeOffset> kesirli saniye ve yerel bir uzaklığa göre biçimlendirmek için kullanılır.

Varsa, en fazla 7 kesirli basamak yazılır. Bu, bu çözünürlükle <xref:System.DateTime> sınırlı olan uygulamayla hizalanır.
