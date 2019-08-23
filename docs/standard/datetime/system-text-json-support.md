---
title: System. Text. JSON içinde DateTime ve DateTimeOffset desteği
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
ms.openlocfilehash: 182694a3d2df02d5e2c709e33a02bd9fa7d20383
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69973193"
---
# <a name="datetime-and-datetimeoffset-support-in-systemtextjson"></a><span data-ttu-id="b85b3-103">System. Text. JSON içinde DateTime ve DateTimeOffset desteği</span><span class="sxs-lookup"><span data-stu-id="b85b3-103">DateTime and DateTimeOffset support in System.Text.Json</span></span>

<span data-ttu-id="b85b3-104">System. Text. JSON kitaplığı ISO 8601:-2019 genişletilmiş profiline <xref:System.DateTime> göre <xref:System.DateTimeOffset> ayrıştırır ve yazar ve değerlerini kaydeder.</span><span class="sxs-lookup"><span data-stu-id="b85b3-104">The System.Text.Json library parses and writes <xref:System.DateTime> and <xref:System.DateTimeOffset> values according to the ISO 8601:-2019 extended profile.</span></span>
<span data-ttu-id="b85b3-105">[Dönüştürücüler](https://docs.microsoft.com/dotnet/api/system.text.json.serialization.jsonconverter-1?view=netcore-3.0) ile <xref:System.Text.Json.JsonSerializer>serileştirme ve seri durumdan çıkarma için özel destek sağlar.</span><span class="sxs-lookup"><span data-stu-id="b85b3-105">[Converters](https://docs.microsoft.com/dotnet/api/system.text.json.serialization.jsonconverter-1?view=netcore-3.0) provide custom support for serializing and deserializing with <xref:System.Text.Json.JsonSerializer>.</span></span>

## <a name="support-for-the-iso-8601-12019-format"></a><span data-ttu-id="b85b3-106">ISO 8601-1:2019 biçimi desteği</span><span class="sxs-lookup"><span data-stu-id="b85b3-106">Support for the ISO 8601-1:2019 format</span></span>

<span data-ttu-id="b85b3-107"><xref:System.Text.Json.JsonSerializer> <xref:System.DateTime> <xref:System.DateTimeOffset> , ,<xref:System.Text.Json.Utf8JsonReader>Ve türleri,ISO8601-1:2019biçiminingenişletilmişprofilinegöreayrıştırılırveyazılırvemetingösterimleridir;Örneğin,2019-07-26T16<xref:System.Text.Json.JsonElement> <xref:System.Text.Json.Utf8JsonWriter> : 59:57-05:00.</span><span class="sxs-lookup"><span data-stu-id="b85b3-107">The <xref:System.Text.Json.JsonSerializer>, <xref:System.Text.Json.Utf8JsonReader>, <xref:System.Text.Json.Utf8JsonWriter>, and <xref:System.Text.Json.JsonElement> types parse and write <xref:System.DateTime> and <xref:System.DateTimeOffset> text representations according to the extended profile of the ISO 8601-1:2019 format; for example, 2019-07-26T16:59:57-05:00.</span></span>

<span data-ttu-id="b85b3-108"><xref:System.DateTime>ve <xref:System.DateTimeOffset> veriler ile <xref:System.Text.Json.JsonSerializer>seri hale getirilebilir:</span><span class="sxs-lookup"><span data-stu-id="b85b3-108"><xref:System.DateTime> and <xref:System.DateTimeOffset> data can be serialized with <xref:System.Text.Json.JsonSerializer>:</span></span>

[!code-csharp[example-serializing-with-jsonserializer](~/samples/snippets/standard/datetime/json/serializing-with-jsonserializer.cs)]

<span data-ttu-id="b85b3-109">Ayrıca, şu şekilde <xref:System.Text.Json.JsonSerializer>seri durumdan çıkarılabilirler:</span><span class="sxs-lookup"><span data-stu-id="b85b3-109">They can also be deserialized with <xref:System.Text.Json.JsonSerializer>:</span></span>

[!code-csharp[example-deserializing-with-jsonserializer-valid](~/samples/snippets/standard/datetime/json/deserializing-with-jsonserializer-valid.cs)]

<span data-ttu-id="b85b3-110">Varsayılan seçeneklerle, giriş <xref:System.DateTime> ve <xref:System.DateTimeOffset> metin temsilleri, genişletilmiş ISO 8601-1:2019 profiline uymalıdır.</span><span class="sxs-lookup"><span data-stu-id="b85b3-110">With default options, input <xref:System.DateTime> and <xref:System.DateTimeOffset> text representations must conform to the extended ISO 8601-1:2019 profile.</span></span>
<span data-ttu-id="b85b3-111">Profille uyumlu olmayan temsiller serisini kaldırma girişimi bir <xref:System.Text.Json.JsonSerializer> <xref:System.Text.Json.JsonException>oluşturulmasına neden olur:</span><span class="sxs-lookup"><span data-stu-id="b85b3-111">Attempting to deserialize representations that don't conform to the profile will cause <xref:System.Text.Json.JsonSerializer> to throw a <xref:System.Text.Json.JsonException>:</span></span>

[!code-csharp[example-deserializing-with-jsonserializer-error](~/samples/snippets/standard/datetime/json/deserializing-with-jsonserializer-error.cs)]

<span data-ttu-id="b85b3-112">, <xref:System.Text.Json.JsonDocument> <xref:System.DateTime> Ve temsilleridahilolmaküzerebirJSONyükününiçeriğineyapılandırılmışerişimsağlar.<xref:System.DateTimeOffset></span><span class="sxs-lookup"><span data-stu-id="b85b3-112">The <xref:System.Text.Json.JsonDocument> provides structured access to the contents of a JSON payload, including <xref:System.DateTime> and <xref:System.DateTimeOffset> representations.</span></span> <span data-ttu-id="b85b3-113">Aşağıdaki örnekte, bir sıcaklığın toplanması verildiğinde, Mondays ortalama sıcaklık hesaplanabilecek nasıl hesaplanacağı gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="b85b3-113">The example below shows how, when given a collection of temperatures, the average temperature on Mondays can be calculated:</span></span>

[!code-csharp[example-computing-with-jsondocument-valid](~/samples/snippets/standard/datetime/json/computing-with-jsondocument-valid.cs)]

<span data-ttu-id="b85b3-114">Uyumsuz <xref:System.DateTime> gösterimlerle yük verilen ortalama sıcaklığın hesaplanmaya çalışılması, şunu oluşturmasına neden <xref:System.Text.Json.JsonDocument> <xref:System.FormatException>olur:</span><span class="sxs-lookup"><span data-stu-id="b85b3-114">Attempting to compute the average temperature given a payload with non-compliant <xref:System.DateTime> representations will cause <xref:System.Text.Json.JsonDocument> to throw a <xref:System.FormatException>:</span></span>

[!code-csharp[example-computing-with-jsondocument-error](~/samples/snippets/standard/datetime/json/computing-with-jsondocument-error.cs)]

<span data-ttu-id="b85b3-115">Alt düzey <xref:System.Text.Json.Utf8JsonWriter> yazmaları <xref:System.DateTime> ve <xref:System.DateTimeOffset> verileri:</span><span class="sxs-lookup"><span data-stu-id="b85b3-115">The lower level <xref:System.Text.Json.Utf8JsonWriter> writes <xref:System.DateTime> and <xref:System.DateTimeOffset> data:</span></span>

[!code-csharp[example-writing-with-utf8jsonwriter](~/samples/snippets/standard/datetime/json/writing-with-utf8jsonwriter.cs)]

<span data-ttu-id="b85b3-116"><xref:System.Text.Json.Utf8JsonReader>ayrıştırır <xref:System.DateTime> ve<xref:System.DateTimeOffset> veriler:</span><span class="sxs-lookup"><span data-stu-id="b85b3-116"><xref:System.Text.Json.Utf8JsonReader> parses <xref:System.DateTime> and <xref:System.DateTimeOffset> data:</span></span>

[!code-csharp[example-reading-with-utf8jsonreader-valid](~/samples/snippets/standard/datetime/json/reading-with-utf8jsonreader-valid.cs)]

<span data-ttu-id="b85b3-117">Uyumlu olmayan biçimleri <xref:System.Text.Json.Utf8JsonReader> okumaya çalışmak bunun <xref:System.FormatException>oluşturulmasına neden olur:</span><span class="sxs-lookup"><span data-stu-id="b85b3-117">Attempting to read non-compliant formats with <xref:System.Text.Json.Utf8JsonReader> will cause it to throw a <xref:System.FormatException>:</span></span>

[!code-csharp[example-reading-with-utf8jsonreader-error](~/samples/snippets/standard/datetime/json/reading-with-utf8jsonreader-error.cs)]

## <a name="custom-support-for-xrefsystemdatetime-and-xrefsystemdatetimeoffset-in-xrefsystemtextjsonjsonserializer"></a><span data-ttu-id="b85b3-118"><xref:System.DateTime> Ve<xref:System.DateTimeOffset> için özel destek<xref:System.Text.Json.JsonSerializer></span><span class="sxs-lookup"><span data-stu-id="b85b3-118">Custom support for <xref:System.DateTime> and <xref:System.DateTimeOffset> in <xref:System.Text.Json.JsonSerializer></span></span>

<span data-ttu-id="b85b3-119">Seri hale getiricinin özel ayrıştırma veya biçimlendirme gerçekleştirmesini istiyorsanız [özel dönüştürücüler](https://docs.microsoft.com/dotnet/api/system.text.json.serialization.jsonconverter-1?view=netcore-3.0)uygulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b85b3-119">If you want the serializer to perform custom parsing or formatting, you can implement [custom converters](https://docs.microsoft.com/dotnet/api/system.text.json.serialization.jsonconverter-1?view=netcore-3.0).</span></span>
<span data-ttu-id="b85b3-120">İşte birkaç örnek:</span><span class="sxs-lookup"><span data-stu-id="b85b3-120">Here are a few examples:</span></span>

### <a name="using-datetimeoffsetparse-and-datetimeoffsettostring"></a><span data-ttu-id="b85b3-121">Ve `DateTime(Offset).Parse` kullanma`DateTime(Offset).ToString`</span><span class="sxs-lookup"><span data-stu-id="b85b3-121">Using `DateTime(Offset).Parse` and `DateTime(Offset).ToString`</span></span>

<span data-ttu-id="b85b3-122">Giriş <xref:System.DateTime> `DateTime(Offset).Parse` veya <xref:System.DateTimeOffset> metin gösterimlerinizin biçimlerini belirleyebulamıyorsanız, dönüştürücüyü okuma mantığınızdaki yöntemi kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b85b3-122">If you can't determine the formats of your input <xref:System.DateTime> or <xref:System.DateTimeOffset> text representations, you can use the `DateTime(Offset).Parse` method in your converter read logic.</span></span> <span data-ttu-id="b85b3-123">Bu, kullanmanıza olanak sağlar. ISO olmayan 8601 dizeleri ve genişletilmiş ISO <xref:System.DateTime> 8601-1:2019 <xref:System.DateTimeOffset> profiline uymayan ISO 8601 biçimleri dahil olmak üzere çeşitli ve metin biçimlerini ayrıştırmak için net kapsamlı destek.</span><span class="sxs-lookup"><span data-stu-id="b85b3-123">This allows you to use .NET's extensive support for parsing various <xref:System.DateTime> and <xref:System.DateTimeOffset> text formats, including non-ISO 8601 strings and ISO 8601 formats that don't conform to the extended ISO 8601-1:2019 profile.</span></span> <span data-ttu-id="b85b3-124">Bu yaklaşım, seri hale getiricinin yerel uygulamasını kullanmaktan önemli ölçüde daha az performansız.</span><span class="sxs-lookup"><span data-stu-id="b85b3-124">This approach is significantly less performant than using the serializer's native implementation.</span></span>

<span data-ttu-id="b85b3-125">Serileştirme için, dönüştürücüyü dönüştürücü yazma mantığınızdaki ' de kullanabilirsiniz `DateTime(Offset).ToString` .</span><span class="sxs-lookup"><span data-stu-id="b85b3-125">For serializing, you can use the `DateTime(Offset).ToString` method in your converter write logic.</span></span> <span data-ttu-id="b85b3-126">Bu <xref:System.DateTime> , [Standart Tarih ve saat biçimlerinden](https://docs.microsoft.com/dotnet/standard/base-types/standard-date-and-time-format-strings)birini ve [özel tarih ve saat biçimlerini](https://docs.microsoft.com/dotnet/standard/base-types/custom-date-and-time-format-strings)kullanarak yazmanızı ve <xref:System.DateTimeOffset> değerleri yazmanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="b85b3-126">This allows you to write <xref:System.DateTime> and <xref:System.DateTimeOffset> values using any of the [standard date and time formats](https://docs.microsoft.com/dotnet/standard/base-types/standard-date-and-time-format-strings), and the [custom date and time formats](https://docs.microsoft.com/dotnet/standard/base-types/custom-date-and-time-format-strings).</span></span>
<span data-ttu-id="b85b3-127">Bu, serileştiricinin yerel uygulamasını kullanmaktan çok önemli ölçüde daha düşüktür.</span><span class="sxs-lookup"><span data-stu-id="b85b3-127">This is also significantly less performant than using the serializer's native implementation.</span></span>

[!code-csharp[example-showing-datetime-parse](~/samples/snippets/standard/datetime/json/datetime-converter-examples/example1/Program.cs)]

> [!NOTE]
> <span data-ttu-id="b85b3-128"><xref:System.Text.Json.Serialization.JsonConverter%601>, Ve `T` olduğunda <xref:System.DateTime>, parametresi her zaman`typeof(DateTime)`olur. `typeToConvert`</span><span class="sxs-lookup"><span data-stu-id="b85b3-128">When implementing <xref:System.Text.Json.Serialization.JsonConverter%601>, and `T` is <xref:System.DateTime>, the `typeToConvert` parameter will always be `typeof(DateTime)`.</span></span>
<span data-ttu-id="b85b3-129">Parametresi, çok biçimli durumları işlemek için ve genel türler kullanılırken performanslı bir şekilde `typeof(T)` yararlanmak için yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="b85b3-129">The parameter is useful for handling polymorphic cases and when using generics to get `typeof(T)` in a performant way.</span></span>

### <a name="using-xrefsystembufferstextutf8parser-and-xrefsystembufferstextutf8formatter"></a><span data-ttu-id="b85b3-130">Ve <xref:System.Buffers.Text.Utf8Parser> kullanma<xref:System.Buffers.Text.Utf8Formatter></span><span class="sxs-lookup"><span data-stu-id="b85b3-130">Using <xref:System.Buffers.Text.Utf8Parser> and <xref:System.Buffers.Text.Utf8Formatter></span></span>

<span data-ttu-id="b85b3-131">Giriş <xref:System.DateTime> veya<xref:System.DateTimeOffset> metin gösterimleriniz "R", "l", "O" veya "G" [Standart Tarih ve saat biçimi dizelerinden](https://docs.microsoft.com/dotnet/standard/base-types/standard-date-and-time-format-strings)biriyle uyumluysa veya isterseniz, dönüştürücü mantığınızdaki hızlı UTF-8 tabanlı ayrıştırma ve biçimlendirme yöntemlerini kullanabilirsiniz. bu biçimlerden birine göre yazın.</span><span class="sxs-lookup"><span data-stu-id="b85b3-131">You can use fast UTF-8-based parsing and formatting methods in your converter logic if your input <xref:System.DateTime> or <xref:System.DateTimeOffset> text representations are compliant with one of the "R", "l", "O", or "G" [standard date and time format Strings](https://docs.microsoft.com/dotnet/standard/base-types/standard-date-and-time-format-strings), or you want to write according to one of these formats.</span></span> <span data-ttu-id="b85b3-132">Bu, ve `DateTime(Offset).Parse` `DateTime(Offset).ToString`kullanmaktan çok daha hızlıdır.</span><span class="sxs-lookup"><span data-stu-id="b85b3-132">This is much faster than using `DateTime(Offset).Parse` and `DateTime(Offset).ToString`.</span></span>

<span data-ttu-id="b85b3-133">Bu örnekte <xref:System.DateTime> [, değerleri "R" standart biçimine](https://docs.microsoft.com/dotnet/standard/base-types/standard-date-and-time-format-strings#the-rfc1123-r-r-format-specifier)göre seri hale getirilen ve serileştiren özel bir dönüştürücü gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="b85b3-133">This example shows a custom converter that serializes and deserializes <xref:System.DateTime> values according to [the "R" standard format](https://docs.microsoft.com/dotnet/standard/base-types/standard-date-and-time-format-strings#the-rfc1123-r-r-format-specifier):</span></span>

[!code-csharp[example-showing-utf8-parser-and-formatter](~/samples/snippets/standard/datetime/json/datetime-converter-examples/example2/Program.cs)]

> [!NOTE]
> <span data-ttu-id="b85b3-134">"R" standart biçimi her zaman 29 karakter uzunluğunda olacaktır.</span><span class="sxs-lookup"><span data-stu-id="b85b3-134">The "R" standard format will always be 29 characters long.</span></span>

### <a name="using-datetimeoffsetparse-as-a-fallback-to-the-serializers-native-parsing"></a><span data-ttu-id="b85b3-135">Seri `DateTime(Offset).Parse` hale getiricinin yerel ayrıştırmaya geri dönüş olarak kullanma</span><span class="sxs-lookup"><span data-stu-id="b85b3-135">Using `DateTime(Offset).Parse` as a fallback to the serializer's native parsing</span></span>

<span data-ttu-id="b85b3-136">Genellikle giriş <xref:System.DateTime> veya <xref:System.DateTimeOffset> verilerinizi genişletilmiş ISO 8601-1:2019 profiline uyacak şekilde bekleliyorsanız, serileştiricinin yerel ayrıştırma mantığını kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b85b3-136">If you generally expect your input <xref:System.DateTime> or <xref:System.DateTimeOffset> data to conform to the extended ISO 8601-1:2019 profile, you can use the serializer's native parsing logic.</span></span> <span data-ttu-id="b85b3-137">Ayrıca, bir geri dönüş mekanizmasını tek bir durumda uygulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b85b3-137">You can also implement a fallback mechanism just in case.</span></span>
<span data-ttu-id="b85b3-138">Bu örnekte, kullanarak <xref:System.DateTime> <xref:System.Text.Json.Utf8JsonReader.TryGetDateTime(System.DateTime@)>bir metin temsilini ayrıştırmaya başarısız olduktan sonra dönüştürücünün verileri <xref:System.DateTime.Parse(System.String)>başarıyla ayrıştırır.</span><span class="sxs-lookup"><span data-stu-id="b85b3-138">This example shows that, after failing to parse a <xref:System.DateTime> text representation using <xref:System.Text.Json.Utf8JsonReader.TryGetDateTime(System.DateTime@)>, the converter successfully parses the data using <xref:System.DateTime.Parse(System.String)>.</span></span>

[!code-csharp[example-showing-datetime-parse-as-fallback](~/samples/snippets/standard/datetime/json/datetime-converter-examples/example3/Program.cs)]

## <a name="the-extended-iso-8601-12019-profile-in-systemtextjson"></a><span data-ttu-id="b85b3-139">System. Text. JSON dosyasındaki genişletilmiş ISO 8601-1:2019 profili</span><span class="sxs-lookup"><span data-stu-id="b85b3-139">The extended ISO 8601-1:2019 profile in System.Text.Json</span></span>

### <a name="date-and-time-components"></a><span data-ttu-id="b85b3-140">Tarih ve saat bileşenleri</span><span class="sxs-lookup"><span data-stu-id="b85b3-140">Date and time components</span></span>

<span data-ttu-id="b85b3-141">' De <xref:System.Text.Json> uygulanan genişletilmiş ISO 8601-1:2019 profili, tarih ve saat temsilleri için aşağıdaki bileşenleri tanımlar.</span><span class="sxs-lookup"><span data-stu-id="b85b3-141">The extended ISO 8601-1:2019 profile implemented in <xref:System.Text.Json> defines the following components for date and time representations.</span></span> <span data-ttu-id="b85b3-142">Bu bileşenler, ayrıştırma ve biçimlendirme <xref:System.DateTime> ve <xref:System.DateTimeOffset> temsiller için desteklenen çeşitli ayrıntı düzeyi düzeylerini tanımlamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="b85b3-142">These components are used to define various levels of granularity supported when parsing and formatting <xref:System.DateTime> and <xref:System.DateTimeOffset> representations.</span></span>

| <span data-ttu-id="b85b3-143">Bileşen</span><span class="sxs-lookup"><span data-stu-id="b85b3-143">Component</span></span>       | <span data-ttu-id="b85b3-144">Biçimi</span><span class="sxs-lookup"><span data-stu-id="b85b3-144">Format</span></span>                      | <span data-ttu-id="b85b3-145">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b85b3-145">Description</span></span>                                                                     |
|-----------------|-----------------------------|---------------------------------------------------------------------------------|
| <span data-ttu-id="b85b3-146">Yıl</span><span class="sxs-lookup"><span data-stu-id="b85b3-146">Year</span></span>            | <span data-ttu-id="b85b3-147">"yyyy"</span><span class="sxs-lookup"><span data-stu-id="b85b3-147">"yyyy"</span></span>                      | <span data-ttu-id="b85b3-148">0001-9999</span><span class="sxs-lookup"><span data-stu-id="b85b3-148">0001-9999</span></span>                                                                       |
| <span data-ttu-id="b85b3-149">Başından</span><span class="sxs-lookup"><span data-stu-id="b85b3-149">Month</span></span>           | <span data-ttu-id="b85b3-150">"AA"</span><span class="sxs-lookup"><span data-stu-id="b85b3-150">"MM"</span></span>                        | <span data-ttu-id="b85b3-151">01-12</span><span class="sxs-lookup"><span data-stu-id="b85b3-151">01-12</span></span>                                                                           |
| <span data-ttu-id="b85b3-152">Gün</span><span class="sxs-lookup"><span data-stu-id="b85b3-152">Day</span></span>             | <span data-ttu-id="b85b3-153">"dd"</span><span class="sxs-lookup"><span data-stu-id="b85b3-153">"dd"</span></span>                        | <span data-ttu-id="b85b3-154">01-28, 01-29, 01-30, 01-31, ay/yıl temelinde</span><span class="sxs-lookup"><span data-stu-id="b85b3-154">01-28, 01-29, 01-30, 01-31 based on month/year</span></span>                                  |
| <span data-ttu-id="b85b3-155">Saat</span><span class="sxs-lookup"><span data-stu-id="b85b3-155">Hour</span></span>            | <span data-ttu-id="b85b3-156">"HH"</span><span class="sxs-lookup"><span data-stu-id="b85b3-156">"HH"</span></span>                        | <span data-ttu-id="b85b3-157">00-23</span><span class="sxs-lookup"><span data-stu-id="b85b3-157">00-23</span></span>                                                                           |
| <span data-ttu-id="b85b3-158">Dakika</span><span class="sxs-lookup"><span data-stu-id="b85b3-158">Minute</span></span>          | <span data-ttu-id="b85b3-159">"mm"</span><span class="sxs-lookup"><span data-stu-id="b85b3-159">"mm"</span></span>                        | <span data-ttu-id="b85b3-160">00-59</span><span class="sxs-lookup"><span data-stu-id="b85b3-160">00-59</span></span>                                                                           |
| <span data-ttu-id="b85b3-161">Saniye</span><span class="sxs-lookup"><span data-stu-id="b85b3-161">Second</span></span>          | <span data-ttu-id="b85b3-162">"ss"</span><span class="sxs-lookup"><span data-stu-id="b85b3-162">"ss"</span></span>                        | <span data-ttu-id="b85b3-163">00-59</span><span class="sxs-lookup"><span data-stu-id="b85b3-163">00-59</span></span>                                                                           |
| <span data-ttu-id="b85b3-164">İkinci kesir</span><span class="sxs-lookup"><span data-stu-id="b85b3-164">Second fraction</span></span> | <span data-ttu-id="b85b3-165">"FFFFFFF"</span><span class="sxs-lookup"><span data-stu-id="b85b3-165">"FFFFFFF"</span></span>                   | <span data-ttu-id="b85b3-166">En az bir rakam, en fazla 16 basamak</span><span class="sxs-lookup"><span data-stu-id="b85b3-166">Minimum of one digit, maximum of 16 digits</span></span>                                      |
| <span data-ttu-id="b85b3-167">Zaman boşluğu</span><span class="sxs-lookup"><span data-stu-id="b85b3-167">Time offset</span></span>     | <span data-ttu-id="b85b3-168">"K"</span><span class="sxs-lookup"><span data-stu-id="b85b3-168">"K"</span></span>                         | <span data-ttu-id="b85b3-169">"Z" ya da "(' + '/'-') HH ': ' mm"</span><span class="sxs-lookup"><span data-stu-id="b85b3-169">Either "Z" or "('+'/'-')HH':'mm"</span></span>                                                |
| <span data-ttu-id="b85b3-170">Kısmi saat</span><span class="sxs-lookup"><span data-stu-id="b85b3-170">Partial time</span></span>    | <span data-ttu-id="b85b3-171">"HH": ' mm ': ' ss [FFFFFFF] "</span><span class="sxs-lookup"><span data-stu-id="b85b3-171">"HH':'mm':'ss[FFFFFFF]"</span></span>     | <span data-ttu-id="b85b3-172">UTC fark bilgisi olmayan süre</span><span class="sxs-lookup"><span data-stu-id="b85b3-172">Time without UTC offset information</span></span>                                             |
| <span data-ttu-id="b85b3-173">Tam Tarih</span><span class="sxs-lookup"><span data-stu-id="b85b3-173">Full date</span></span>       | <span data-ttu-id="b85b3-174">"yyyy'-'MM'-'dd"</span><span class="sxs-lookup"><span data-stu-id="b85b3-174">"yyyy'-'MM'-'dd"</span></span>            | <span data-ttu-id="b85b3-175">Takvim tarihi</span><span class="sxs-lookup"><span data-stu-id="b85b3-175">Calendar date</span></span>                                                                   |
| <span data-ttu-id="b85b3-176">Tam zaman</span><span class="sxs-lookup"><span data-stu-id="b85b3-176">Full time</span></span>       | <span data-ttu-id="b85b3-177">"' Kısmi time'K"</span><span class="sxs-lookup"><span data-stu-id="b85b3-177">"'Partial time'K"</span></span>           | <span data-ttu-id="b85b3-178">Yerel Saat ve UTC arasında saat farkına sahip günün UTC günü veya yerel saati</span><span class="sxs-lookup"><span data-stu-id="b85b3-178">UTC of day or Local time of day with the time offset between local time and UTC</span></span> |
| <span data-ttu-id="b85b3-179">Tarih saat</span><span class="sxs-lookup"><span data-stu-id="b85b3-179">Date time</span></span>       | <span data-ttu-id="b85b3-180">"' Tam tarih ' 'T ' ' tam zaman '"</span><span class="sxs-lookup"><span data-stu-id="b85b3-180">"'Full date''T''Full time'"</span></span> | <span data-ttu-id="b85b3-181">Takvim tarihi ve günün saati, ör. 2019-07-26T16:59:57-05:00</span><span class="sxs-lookup"><span data-stu-id="b85b3-181">Calendar date and time of day, e.g. 2019-07-26T16:59:57-05:00</span></span>                   |

### <a name="support-for-parsing"></a><span data-ttu-id="b85b3-182">Ayrıştırma desteği</span><span class="sxs-lookup"><span data-stu-id="b85b3-182">Support for parsing</span></span>

<span data-ttu-id="b85b3-183">Aşağıdaki ayrıntı düzeyi, ayrıştırma için tanımlanmıştır:</span><span class="sxs-lookup"><span data-stu-id="b85b3-183">The following levels of granularity are defined for parsing:</span></span>

1. <span data-ttu-id="b85b3-184">' Tam tarih '</span><span class="sxs-lookup"><span data-stu-id="b85b3-184">'Full date'</span></span>
    1. <span data-ttu-id="b85b3-185">"yyyy'-'MM'-'dd"</span><span class="sxs-lookup"><span data-stu-id="b85b3-185">"yyyy'-'MM'-'dd"</span></span>

2. <span data-ttu-id="b85b3-186">"' Tam tarih ' 'T ' ' saat ' ': ' ' dakika '"</span><span class="sxs-lookup"><span data-stu-id="b85b3-186">"'Full date''T''Hour'':''Minute'"</span></span>
    1. <span data-ttu-id="b85b3-187">"yyyy'-'MM'-'dd'T'HH ': ' mm"</span><span class="sxs-lookup"><span data-stu-id="b85b3-187">"yyyy'-'MM'-'dd'T'HH':'mm"</span></span>

3. <span data-ttu-id="b85b3-188">"' Tam tarih ' 'T ' ' kısmi zaman '"</span><span class="sxs-lookup"><span data-stu-id="b85b3-188">"'Full date''T''Partial time'"</span></span>
    1. <span data-ttu-id="b85b3-189">"yyyy'-'MM'-'dd'T'HH ': ' mm ': ' ss" ([sıralanabilir ("s") Biçim belirleyicisi](https://docs.microsoft.com/dotnet/standard/base-types/standard-date-and-time-format-strings#the-sortable-s-format-specifier))</span><span class="sxs-lookup"><span data-stu-id="b85b3-189">"yyyy'-'MM'-'dd'T'HH':'mm':'ss" ([The Sortable ("s") Format Specifier](https://docs.microsoft.com/dotnet/standard/base-types/standard-date-and-time-format-strings#the-sortable-s-format-specifier))</span></span>
    2. <span data-ttu-id="b85b3-190">"yyyy'-'MM'-'dd'T'HH ': ' mm ': ' ss '. ' FFFFFFF</span><span class="sxs-lookup"><span data-stu-id="b85b3-190">"yyyy'-'MM'-'dd'T'HH':'mm':'ss'.'FFFFFFF"</span></span>

4. <span data-ttu-id="b85b3-191">"' Tam tarih ' 'T ' ' saat saat ' ': ' ' dakika ' ' zaman boşluğu '"</span><span class="sxs-lookup"><span data-stu-id="b85b3-191">"'Full date''T''Time hour'':''Minute''Time offset'"</span></span>
    1. <span data-ttu-id="b85b3-192">"yyyy'-'MM'-'dd'T'HH ': ' mmZ"</span><span class="sxs-lookup"><span data-stu-id="b85b3-192">"yyyy'-'MM'-'dd'T'HH':'mmZ"</span></span>
    2. <span data-ttu-id="b85b3-193">"yyyy'-'MM'-'dd'T'HH ': ' mm (' + '/'-') HH ': ' mm"</span><span class="sxs-lookup"><span data-stu-id="b85b3-193">"yyyy'-'MM'-'dd'T'HH':'mm('+'/'-')HH':'mm"</span></span>

5. <span data-ttu-id="b85b3-194">' Tarih saat '</span><span class="sxs-lookup"><span data-stu-id="b85b3-194">'Date time'</span></span>
    1. <span data-ttu-id="b85b3-195">"yyyy'-'MM'-'dd'T'HH ': ' mm ': ' ssZ"</span><span class="sxs-lookup"><span data-stu-id="b85b3-195">"yyyy'-'MM'-'dd'T'HH':'mm':'ssZ"</span></span>
    2. <span data-ttu-id="b85b3-196">"yyyy'-'MM'-'dd'T'HH ': ' mm ': ' ss '. ' FFFFFFFZ"</span><span class="sxs-lookup"><span data-stu-id="b85b3-196">"yyyy'-'MM'-'dd'T'HH':'mm':'ss'.'FFFFFFFZ"</span></span>
    3. <span data-ttu-id="b85b3-197">"yyyy'-'MM'-'dd'T'HH ': ' mm ': ' ss (' + '/'-') HH ': ' mm"</span><span class="sxs-lookup"><span data-stu-id="b85b3-197">"yyyy'-'MM'-'dd'T'HH':'mm':'ss('+'/'-')HH':'mm"</span></span>
    4. <span data-ttu-id="b85b3-198">"yyyy'-'MM'-'dd'T'HH ': ' mm ': ' ss '. ' FFFFFFF (' + '/'-') HH ': ' mm "</span><span class="sxs-lookup"><span data-stu-id="b85b3-198">"yyyy'-'MM'-'dd'T'HH':'mm':'ss'.'FFFFFFF('+'/'-')HH':'mm"</span></span>

<span data-ttu-id="b85b3-199">Saniyeler için ondalık kesirler varsa, en az bir rakam olmalıdır; `2019-07-26T00:00:00.` izin verilmiyor.</span><span class="sxs-lookup"><span data-stu-id="b85b3-199">If there are decimal fractions for seconds, there must be at least one digit; `2019-07-26T00:00:00.` is not allowed.</span></span>
<span data-ttu-id="b85b3-200">16 ' ya kadar kesirli basamağa izin verildiğinde, yalnızca ilk yedi ayrıştırılır.</span><span class="sxs-lookup"><span data-stu-id="b85b3-200">While up to 16 fractional digits are allowed, only the first seven are parsed.</span></span> <span data-ttu-id="b85b3-201">Bundan sonraki bir şey sıfır olarak kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="b85b3-201">Anything beyond that is considered a zero.</span></span>
<span data-ttu-id="b85b3-202">Örneğin, `2019-07-26T00:00:00.1234567890` olduğu gibi `2019-07-26T00:00:00.1234567`ayrıştırılacaktır.</span><span class="sxs-lookup"><span data-stu-id="b85b3-202">For example, `2019-07-26T00:00:00.1234567890` will be parsed as if it is `2019-07-26T00:00:00.1234567`.</span></span>
<span data-ttu-id="b85b3-203">Bu, bu çözünürlükle sınırlı olan <xref:System.DateTime> uygulamayla uyumlu kalmasıdır.</span><span class="sxs-lookup"><span data-stu-id="b85b3-203">This is to stay compatible with the <xref:System.DateTime> implementation, which is limited to this resolution.</span></span>

<span data-ttu-id="b85b3-204">Artık saniyeler desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="b85b3-204">Leap seconds are not supported.</span></span>

### <a name="support-for-formatting"></a><span data-ttu-id="b85b3-205">Biçimlendirme desteği</span><span class="sxs-lookup"><span data-stu-id="b85b3-205">Support for formatting</span></span>

<span data-ttu-id="b85b3-206">Biçimlendirme için aşağıdaki ayrıntı düzeyi düzeyleri tanımlanmıştır:</span><span class="sxs-lookup"><span data-stu-id="b85b3-206">The following levels of granularity are defined for formatting:</span></span>

1. <span data-ttu-id="b85b3-207">"' Tam tarih ' 'T ' ' kısmi zaman '"</span><span class="sxs-lookup"><span data-stu-id="b85b3-207">"'Full date''T''Partial time'"</span></span>
    1. <span data-ttu-id="b85b3-208">"yyyy'-'MM'-'dd'T'HH ': ' mm ': ' ss" ([sıralanabilir ("s") Biçim belirleyicisi](https://docs.microsoft.com/dotnet/standard/base-types/standard-date-and-time-format-strings#the-sortable-s-format-specifier))</span><span class="sxs-lookup"><span data-stu-id="b85b3-208">"yyyy'-'MM'-'dd'T'HH':'mm':'ss"  ([The Sortable ("s") Format Specifier](https://docs.microsoft.com/dotnet/standard/base-types/standard-date-and-time-format-strings#the-sortable-s-format-specifier))</span></span>

        <span data-ttu-id="b85b3-209">Kesirli saniyeler <xref:System.DateTime> olmadan ve hiçbir konum bilgisi olmadan biçimlendirmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="b85b3-209">Used to format a <xref:System.DateTime> without fractional seconds and without offset information.</span></span>

    2. <span data-ttu-id="b85b3-210">"yyyy'-'MM'-'dd'T'HH ': ' mm ': ' ss '. ' FFFFFFF</span><span class="sxs-lookup"><span data-stu-id="b85b3-210">"yyyy'-'MM'-'dd'T'HH':'mm':'ss'.'FFFFFFF"</span></span>

        <span data-ttu-id="b85b3-211">Kesirli saniyeler <xref:System.DateTime> ile biçimlendirmek için kullanılır, ancak bu bilgiler, konum bilgisi olmadan.</span><span class="sxs-lookup"><span data-stu-id="b85b3-211">Used to format a <xref:System.DateTime> with fractional seconds but without offset information.</span></span>

2. <span data-ttu-id="b85b3-212">' Tarih saat '</span><span class="sxs-lookup"><span data-stu-id="b85b3-212">'Date time'</span></span>
    1. <span data-ttu-id="b85b3-213">"yyyy'-'MM'-'dd'T'HH ': ' mm ': ' ssZ"</span><span class="sxs-lookup"><span data-stu-id="b85b3-213">"yyyy'-'MM'-'dd'T'HH':'mm':'ssZ"</span></span>

        <span data-ttu-id="b85b3-214">Kesirli saniyeleri, ancak <xref:System.DateTime> UTC <xref:System.DateTimeOffset> boşluğu olmadan biçimlendirmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="b85b3-214">Used to format a <xref:System.DateTime> or <xref:System.DateTimeOffset> without fractional seconds but with a UTC offset.</span></span>

    2. <span data-ttu-id="b85b3-215">"yyyy'-'MM'-'dd'T'HH ': ' mm ': ' ss '. ' FFFFFFFZ"</span><span class="sxs-lookup"><span data-stu-id="b85b3-215">"yyyy'-'MM'-'dd'T'HH':'mm':'ss'.'FFFFFFFZ"</span></span>

        <span data-ttu-id="b85b3-216">Bir <xref:System.DateTime> veya<xref:System.DateTimeOffset> kesirli saniyeleri ve UTC bir sapmayı biçimlendirmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="b85b3-216">Used to format a <xref:System.DateTime> or <xref:System.DateTimeOffset> with fractional seconds and with a UTC offset.</span></span>

    3. <span data-ttu-id="b85b3-217">"yyyy'-'MM'-'dd'T'HH ': ' mm ': ' ss (' + '/'-') HH ': ' mm"</span><span class="sxs-lookup"><span data-stu-id="b85b3-217">"yyyy'-'MM'-'dd'T'HH':'mm':'ss('+'/'-')HH':'mm"</span></span>

        <span data-ttu-id="b85b3-218">Kesirli saniyeleri <xref:System.DateTime> veya <xref:System.DateTimeOffset> yerel bir kaydırmadan biçimlendirmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="b85b3-218">Used to format a <xref:System.DateTime> or <xref:System.DateTimeOffset> without fractional seconds but with a local offset.</span></span>

    4. <span data-ttu-id="b85b3-219">"yyyy'-'MM'-'dd'T'HH ': ' mm ': ' ss '. ' FFFFFFF (' + '/'-') HH ': ' mm "</span><span class="sxs-lookup"><span data-stu-id="b85b3-219">"yyyy'-'MM'-'dd'T'HH':'mm':'ss'.'FFFFFFF('+'/'-')HH':'mm"</span></span>

        <span data-ttu-id="b85b3-220">Bir <xref:System.DateTime> veya<xref:System.DateTimeOffset> kesirli saniye ve yerel bir uzaklığa göre biçimlendirmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="b85b3-220">Used to format a <xref:System.DateTime> or <xref:System.DateTimeOffset> with fractional seconds and with a local offset.</span></span>
