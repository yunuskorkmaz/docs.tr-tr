---
title: C#-.NET kullanarak JSON serileştirmek ve serisini kaldırma
description: System.Text.Json.Net 'TEKI JSON 'a seri hale getirmek ve seri durumdan çıkarmak için ad alanını nasıl kullanacağınızı öğrenin. Örnek kod içerir.
ms.date: 01/19/2021
ms.custom: contperf-fy21q2
no-loc:
- System.Text.Json
- Newtonsoft.Json
zone_pivot_groups: dotnet-version
dev_langs:
- csharp
- vb
helpviewer_keywords:
- JSON serialization
- serializing objects
- serialization
- objects, serializing
ms.openlocfilehash: fb0866dfad67bfe14a7f1388ec2f52a8dc970233
ms.sourcegitcommit: f0fc5db7bcbf212e46933e9cf2d555bb82666141
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/17/2021
ms.locfileid: "100583225"
---
# <a name="how-to-serialize-and-deserialize-marshal-and-unmarshal-json-in-net"></a><span data-ttu-id="dac08-104">.NET içinde JSON ve seri hale getirme (sıralama ve kaldırma)</span><span class="sxs-lookup"><span data-stu-id="dac08-104">How to serialize and deserialize (marshal and unmarshal) JSON in .NET</span></span>

<span data-ttu-id="dac08-105">Bu makalede, <xref:System.Text.Json?displayProperty=fullName> JavaScript nesne gösterimi (JSON) ' den seri hale getirmek ve seri durumdan çıkarmak için ad alanının nasıl kullanılacağı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="dac08-105">This article shows how to use the <xref:System.Text.Json?displayProperty=fullName> namespace to serialize to and deserialize from JavaScript Object Notation (JSON).</span></span> <span data-ttu-id="dac08-106">İçinden mevcut kodu aktarıyorsanız `Newtonsoft.Json` , bkz. [nasıl geçiş `System.Text.Json` yapılacağı ](system-text-json-migrate-from-newtonsoft-how-to.md).</span><span class="sxs-lookup"><span data-stu-id="dac08-106">If you're porting existing code from `Newtonsoft.Json`, see [How to migrate to `System.Text.Json`](system-text-json-migrate-from-newtonsoft-how-to.md).</span></span>

<span data-ttu-id="dac08-107">Yönergeler ve örnek kod, kitaplığı, [ASP.NET Core](/aspnet/core/)gibi bir çerçeve aracılığıyla değil, doğrudan kullanır.</span><span class="sxs-lookup"><span data-stu-id="dac08-107">The directions and sample code use the library directly, not through a framework such as [ASP.NET Core](/aspnet/core/).</span></span>

<span data-ttu-id="dac08-108">Serileştirme örnek kodunun çoğu, <xref:System.Text.Json.JsonSerializerOptions.WriteIndented?displayProperty=nameWithType> `true` JSON (girintileme ve insanlar okunabilirlik için boşluk) olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="dac08-108">Most of the serialization sample code sets <xref:System.Text.Json.JsonSerializerOptions.WriteIndented?displayProperty=nameWithType> to `true` to "pretty-print" the JSON (with indentation and whitespace for human readability).</span></span> <span data-ttu-id="dac08-109">Üretim kullanımı için genellikle bu ayar için varsayılan değerini kabul etmiş olursunuz `false` , çünkü gereksiz boşluklar eklemek performans ve bant genişliği kullanımı üzerinde dikkat çekici, olumsuz bir etkiye neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="dac08-109">For production use, you would typically accept the default value of `false` for this setting, since adding unnecessary whitespace may incur a noticeable, negative impact on performance and bandwidth usage.</span></span>

<span data-ttu-id="dac08-110">Kod örnekleri, aşağıdaki sınıfa ve türevlerini ifade eder:</span><span class="sxs-lookup"><span data-stu-id="dac08-110">The code examples refer to the following class and variants of it:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/WeatherForecast.cs" id="WF":::
:::code language="vb" source="snippets/system-text-json-how-to/vb/WeatherForecast.vb" id="WF":::

## <a name="visual-basic-support"></a><span data-ttu-id="dac08-111">Visual Basic desteği</span><span class="sxs-lookup"><span data-stu-id="dac08-111">Visual Basic support</span></span>

<span data-ttu-id="dac08-112">System.Text.JsonVisual Basic tarafından desteklenmeyen [ref yapıları](../../csharp/language-reference/builtin-types/struct.md#ref-struct)kullanma bölümleri.</span><span class="sxs-lookup"><span data-stu-id="dac08-112">Parts of System.Text.Json use [ref structs](../../csharp/language-reference/builtin-types/struct.md#ref-struct), which are not supported by Visual Basic.</span></span> <span data-ttu-id="dac08-113">System.Text.JsonVisual Basic ile ref struct API 'leri kullanmayı denerseniz, BC40000 derleyici hataları alırsınız.</span><span class="sxs-lookup"><span data-stu-id="dac08-113">If you try to use System.Text.Json ref struct APIs with Visual Basic you get BC40000 compiler errors.</span></span> <span data-ttu-id="dac08-114">Hata iletisi, sorunun eski bir API olduğunu gösterir ancak gerçek sorun, derleyicide başvuru yapısı desteğinin olmamasından kaynaklanır.</span><span class="sxs-lookup"><span data-stu-id="dac08-114">The error message indicates that the problem is an obsolete API, but the actual issue is lack of ref struct support in the compiler.</span></span> <span data-ttu-id="dac08-115">Aşağıdaki bölümleri System.Text.Json Visual Basic kullanılamaz:</span><span class="sxs-lookup"><span data-stu-id="dac08-115">The following parts of System.Text.Json aren't usable from Visual Basic:</span></span>

* <span data-ttu-id="dac08-116"><xref:System.Text.Json.Utf8JsonReader>Sınıfı.</span><span class="sxs-lookup"><span data-stu-id="dac08-116">The <xref:System.Text.Json.Utf8JsonReader> class.</span></span> <span data-ttu-id="dac08-117"><xref:System.Text.Json.Serialization.JsonConverter%601.Read%2A?displayProperty=nameWithType>Yöntem bir `Utf8JsonReader` parametre kullandığından, bu sınırlama özel dönüştürücüler yazmak için Visual Basic kullanma ' yı yazamıyoruz.</span><span class="sxs-lookup"><span data-stu-id="dac08-117">Since the <xref:System.Text.Json.Serialization.JsonConverter%601.Read%2A?displayProperty=nameWithType> method takes a `Utf8JsonReader` parameter, this limitation means you can't write use Visual Basic to write custom converters.</span></span> <span data-ttu-id="dac08-118">Bunun için geçici bir çözüm olarak, bir C# Kitaplığı derlemesinde özel dönüştürücüler uygulamanız ve bu derlemeye VB projenizden başvurulamıyor.</span><span class="sxs-lookup"><span data-stu-id="dac08-118">A workaround for this is to implement custom converters in a C# library assembly, and reference that assembly from your VB project.</span></span> <span data-ttu-id="dac08-119">Bu, Visual Basic ' de her şey, dönüştürücülerin serileştiriciye kaydettirilmekte olduğunu varsayar.</span><span class="sxs-lookup"><span data-stu-id="dac08-119">This assumes that all you do in Visual Basic is register the converters into the serializer.</span></span> <span data-ttu-id="dac08-120">`Read`Visual Basic koddan dönüştürücülerin yöntemlerini çağırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="dac08-120">You can't call the `Read` methods of the converters from Visual Basic code.</span></span>
* <span data-ttu-id="dac08-121">Bir tür içeren diğer API 'lerin aşırı yüklemeleri <xref:System.ReadOnlySpan%601> .</span><span class="sxs-lookup"><span data-stu-id="dac08-121">Overloads of other APIs that include a <xref:System.ReadOnlySpan%601> type.</span></span> <span data-ttu-id="dac08-122">Çoğu yöntem yerine kullanan aşırı yüklemeleri içerir `String` `ReadOnlySpan` .</span><span class="sxs-lookup"><span data-stu-id="dac08-122">Most methods include overloads that use `String` instead of `ReadOnlySpan`.</span></span>

<span data-ttu-id="dac08-123">Başvuru yapıları, yalnızca "verileri üzerinden geçirme" sırasında bile dil desteği olmadan güvenli şekilde kullanılamadığından bu kısıtlamalar uygulanır.</span><span class="sxs-lookup"><span data-stu-id="dac08-123">These restrictions are in place because ref structs cannot be used safely without language support, even when just "passing data through."</span></span> <span data-ttu-id="dac08-124">Bu hatanın gerçekleştirilmesi, belleği bozmaya ve yapılmamalıdır Visual Basic koda neden olur.</span><span class="sxs-lookup"><span data-stu-id="dac08-124">Subverting this error will result in Visual Basic code that can corrupt memory and should not be done.</span></span>

## <a name="namespaces"></a><span data-ttu-id="dac08-125">Ad alanları</span><span class="sxs-lookup"><span data-stu-id="dac08-125">Namespaces</span></span>

<span data-ttu-id="dac08-126"><xref:System.Text.Json>Ad alanı tüm giriş noktalarını ve ana türleri içerir.</span><span class="sxs-lookup"><span data-stu-id="dac08-126">The <xref:System.Text.Json> namespace contains all the entry points and the main types.</span></span> <span data-ttu-id="dac08-127"><xref:System.Text.Json.Serialization>Ad alanı, serileştirme ve seri durumdan çıkarma ile ilgili gelişmiş senaryolar ve özelleştirme için öznitelikler ve API 'leri içerir.</span><span class="sxs-lookup"><span data-stu-id="dac08-127">The <xref:System.Text.Json.Serialization> namespace contains attributes and APIs for advanced scenarios and customization specific to serialization and deserialization.</span></span> <span data-ttu-id="dac08-128">Bu makalede gösterilen kod örnekleri, `using` Bu ad alanlarından biri veya her ikisi için yönergeler gerektirir:</span><span class="sxs-lookup"><span data-stu-id="dac08-128">The code examples shown in this article require `using` directives for one or both of these namespaces:</span></span>

```csharp
using System.Text.Json;
using System.Text.Json.Serialization;
```

```vb
Imports System.Text.Json
Imports System.Text.Json.Serialization
```

> [!IMPORTANT]
> <span data-ttu-id="dac08-129"><xref:System.Runtime.Serialization>Ad alanındaki öznitelikler ' de desteklenmez `System.Text.Json` .</span><span class="sxs-lookup"><span data-stu-id="dac08-129">Attributes from the <xref:System.Runtime.Serialization> namespace aren't supported in `System.Text.Json`.</span></span>

## <a name="how-to-write-net-objects-as-json-serialize"></a><span data-ttu-id="dac08-130">.NET nesnelerini JSON (serileştirme) olarak yazma</span><span class="sxs-lookup"><span data-stu-id="dac08-130">How to write .NET objects as JSON (serialize)</span></span>

<span data-ttu-id="dac08-131">JSON 'yi bir dizeye veya bir dosyaya yazmak için <xref:System.Text.Json.JsonSerializer.Serialize%2A?displayProperty=nameWithType> yöntemini çağırın.</span><span class="sxs-lookup"><span data-stu-id="dac08-131">To write JSON to a string or to a file, call the <xref:System.Text.Json.JsonSerializer.Serialize%2A?displayProperty=nameWithType> method.</span></span>

<span data-ttu-id="dac08-132">Aşağıdaki örnek bir dize olarak JSON oluşturur:</span><span class="sxs-lookup"><span data-stu-id="dac08-132">The following example creates JSON as a string:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/RoundtripToString.cs" id="Serialize":::
:::code language="vb" source="snippets/system-text-json-how-to/vb/RoundtripToString.vb" id="Serialize":::

<span data-ttu-id="dac08-133">Aşağıdaki örnek, bir JSON dosyası oluşturmak için zaman uyumlu kod kullanır:</span><span class="sxs-lookup"><span data-stu-id="dac08-133">The following example uses synchronous code to create a JSON file:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/RoundtripToFile.cs" id="Serialize":::
:::code language="vb" source="snippets/system-text-json-how-to/vb/RoundtripToFile.vb" id="Serialize":::

<span data-ttu-id="dac08-134">Aşağıdaki örnek, bir JSON dosyası oluşturmak için zaman uyumsuz kod kullanır:</span><span class="sxs-lookup"><span data-stu-id="dac08-134">The following example uses asynchronous code to create a JSON file:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/RoundtripToFileAsync.cs" id="Serialize":::
:::code language="vb" source="snippets/system-text-json-how-to/vb/RoundtripToFileAsync.vb" id="Serialize":::

<span data-ttu-id="dac08-135">Önceki örneklerde, serileştirilmekte olan türün tür çıkarımı kullanılır.</span><span class="sxs-lookup"><span data-stu-id="dac08-135">The preceding examples use type inference for the type being serialized.</span></span> <span data-ttu-id="dac08-136">Öğesinin aşırı yüklemesi `Serialize()` genel bir tür parametresi alır:</span><span class="sxs-lookup"><span data-stu-id="dac08-136">An overload of `Serialize()` takes a generic type parameter:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/RoundtripToString.cs" id="SerializeWithGenericParameter":::
:::code language="vb" source="snippets/system-text-json-how-to/vb/RoundtripToString.vb" id="SerializeWithGenericParameter":::

### <a name="serialization-example"></a><span data-ttu-id="dac08-137">Serileştirme örneği</span><span class="sxs-lookup"><span data-stu-id="dac08-137">Serialization example</span></span>

<span data-ttu-id="dac08-138">Aşağıda, koleksiyon türü özellikleri ve Kullanıcı tanımlı bir tür içeren örnek bir sınıf verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="dac08-138">Here's an example class that contains collection-type properties and a user-defined type:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/WeatherForecast.cs" id="WFWithPOCOs":::
:::code language="vb" source="snippets/system-text-json-how-to/vb/WeatherForecast.vb" id="WFWithPOCOs":::

> [!TIP]
> <span data-ttu-id="dac08-139">"POCO", [düz eskı clr nesnesini](https://en.wikipedia.org/wiki/Plain_old_CLR_object)temsil eder.</span><span class="sxs-lookup"><span data-stu-id="dac08-139">"POCO" stands for [plain old CLR object](https://en.wikipedia.org/wiki/Plain_old_CLR_object).</span></span> <span data-ttu-id="dac08-140">POCO, örneğin devralma veya öznitelikler aracılığıyla herhangi bir çerçeveye özgü türe bağımlı olmayan bir .NET türüdür.</span><span class="sxs-lookup"><span data-stu-id="dac08-140">A POCO is a .NET type that doesn't depend on any framework-specific types, for example, through inheritance or attributes.</span></span>

<span data-ttu-id="dac08-141">Önceki türün bir örneğinin serileştirilmesi için JSON çıktısı aşağıdaki örnekteki gibi görünür.</span><span class="sxs-lookup"><span data-stu-id="dac08-141">The JSON output from serializing an instance of the preceding type looks like the following example.</span></span> <span data-ttu-id="dac08-142">JSON çıktısı küçültülmüş (boşluk, girintileme ve yeni satır karakterleri kaldırılır) varsayılan olarak:</span><span class="sxs-lookup"><span data-stu-id="dac08-142">The JSON output is minified (whitespace, indentation, and new-line characters are removed) by default:</span></span>

```json
{"Date":"2019-08-01T00:00:00-07:00","TemperatureCelsius":25,"Summary":"Hot","DatesAvailable":["2019-08-01T00:00:00-07:00","2019-08-02T00:00:00-07:00"],"TemperatureRanges":{"Cold":{"High":20,"Low":-10},"Hot":{"High":60,"Low":20}},"SummaryWords":["Cool","Windy","Humid"]}
```

<span data-ttu-id="dac08-143">Aşağıdaki örnek aynı JSON 'ı gösterir, ancak biçimlendirilir (yani, boşluk ve girintileme ile düzgün şekilde yazdırılır):</span><span class="sxs-lookup"><span data-stu-id="dac08-143">The following example shows the same JSON, but formatted (that is, pretty-printed with whitespace and indentation):</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "Hot",
  "DatesAvailable": [
    "2019-08-01T00:00:00-07:00",
    "2019-08-02T00:00:00-07:00"
  ],
  "TemperatureRanges": {
    "Cold": {
      "High": 20,
      "Low": -10
    },
    "Hot": {
      "High": 60,
      "Low": 20
    }
  },
  "SummaryWords": [
    "Cool",
    "Windy",
    "Humid"
  ]
}
```

## <a name="serialize-to-utf-8"></a><span data-ttu-id="dac08-144">UTF-8 ' e serileştirme</span><span class="sxs-lookup"><span data-stu-id="dac08-144">Serialize to UTF-8</span></span>

<span data-ttu-id="dac08-145">UTF-8 ' e seri hale getirmek için <xref:System.Text.Json.JsonSerializer.SerializeToUtf8Bytes%2A?displayProperty=nameWithType> yöntemini çağırın:</span><span class="sxs-lookup"><span data-stu-id="dac08-145">To serialize to UTF-8, call the <xref:System.Text.Json.JsonSerializer.SerializeToUtf8Bytes%2A?displayProperty=nameWithType> method:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/RoundtripToUtf8.cs" id="Serialize":::
:::code language="vb" source="snippets/system-text-json-how-to/vb/RoundtripToUtf8.vb" id="Serialize":::

<span data-ttu-id="dac08-146">' İ <xref:System.Text.Json.JsonSerializer.Serialize%2A> alan bir aşırı yükleme <xref:System.Text.Json.Utf8JsonWriter> de mevcuttur.</span><span class="sxs-lookup"><span data-stu-id="dac08-146">A <xref:System.Text.Json.JsonSerializer.Serialize%2A> overload that takes a <xref:System.Text.Json.Utf8JsonWriter> is also available.</span></span>

<span data-ttu-id="dac08-147">UTF-8 ' i seri hale getirmek, dize tabanlı yöntemler kullanmaktan daha hızlı% 5-10 daha hızlıdır.</span><span class="sxs-lookup"><span data-stu-id="dac08-147">Serializing to UTF-8 is about 5-10% faster than using the string-based methods.</span></span> <span data-ttu-id="dac08-148">Aradaki fark, baytların (UTF-8 olarak) dizelere dönüştürülmesi gerekmez (UTF-16).</span><span class="sxs-lookup"><span data-stu-id="dac08-148">The difference is because the bytes (as UTF-8) don't need to be converted to strings (UTF-16).</span></span>

## <a name="serialization-behavior"></a><span data-ttu-id="dac08-149">Serileştirme davranışı</span><span class="sxs-lookup"><span data-stu-id="dac08-149">Serialization behavior</span></span>

::: zone pivot="dotnet-5-0"

* <span data-ttu-id="dac08-150">Varsayılan olarak, tüm ortak özellikler serileştirilir.</span><span class="sxs-lookup"><span data-stu-id="dac08-150">By default, all public properties are serialized.</span></span> <span data-ttu-id="dac08-151">[Yoksayılacak özellikleri belirtebilirsiniz](system-text-json-ignore-properties.md).</span><span class="sxs-lookup"><span data-stu-id="dac08-151">You can [specify properties to ignore](system-text-json-ignore-properties.md).</span></span>
* <span data-ttu-id="dac08-152">[Varsayılan KODLAYıCı](xref:System.Text.Encodings.Web.JavaScriptEncoder.Default) ASCII olmayan KARAKTERLERI, ASCII ARALıĞı içindeki HTML duyarlı KARAKTERLERI ve [RFC 8259 JSON](https://tools.ietf.org/html/rfc8259#section-7)belirtimine göre kaçılması gereken karakterleri çıkar.</span><span class="sxs-lookup"><span data-stu-id="dac08-152">The [default encoder](xref:System.Text.Encodings.Web.JavaScriptEncoder.Default) escapes non-ASCII characters, HTML-sensitive characters within the ASCII-range, and characters that must be escaped according to [the RFC 8259 JSON spec](https://tools.ietf.org/html/rfc8259#section-7).</span></span>
* <span data-ttu-id="dac08-153">Varsayılan olarak JSON, Mini olarak belirlenir.</span><span class="sxs-lookup"><span data-stu-id="dac08-153">By default, JSON is minified.</span></span> <span data-ttu-id="dac08-154">JSON 'ı [düzgün](#serialize-to-formatted-json)bir şekilde yazdırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="dac08-154">You can [pretty-print the JSON](#serialize-to-formatted-json).</span></span>
* <span data-ttu-id="dac08-155">Varsayılan olarak, JSON adlarının büyük küçük harfleri .NET adlarıyla eşleşir.</span><span class="sxs-lookup"><span data-stu-id="dac08-155">By default, casing of JSON names matches the .NET names.</span></span> <span data-ttu-id="dac08-156">[JSON adının büyük küçük harflerini özelleştirebilirsiniz](system-text-json-customize-properties.md).</span><span class="sxs-lookup"><span data-stu-id="dac08-156">You can [customize JSON name casing](system-text-json-customize-properties.md).</span></span>
* <span data-ttu-id="dac08-157">Varsayılan olarak, döngüsel başvurular algılanır ve özel durumlar oluşur.</span><span class="sxs-lookup"><span data-stu-id="dac08-157">By default, circular references are detected and exceptions thrown.</span></span> <span data-ttu-id="dac08-158">[Başvuruları koruyabilir ve döngüsel başvuruları işleyebilirsiniz](system-text-json-preserve-references.md).</span><span class="sxs-lookup"><span data-stu-id="dac08-158">You can [preserve references and handle circular references](system-text-json-preserve-references.md).</span></span>
* <span data-ttu-id="dac08-159">Varsayılan olarak, [alanlar](../../csharp/programming-guide/classes-and-structs/fields.md) yok sayılır.</span><span class="sxs-lookup"><span data-stu-id="dac08-159">By default, [fields](../../csharp/programming-guide/classes-and-structs/fields.md) are ignored.</span></span> <span data-ttu-id="dac08-160">[Alanları dahil](#include-fields)edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="dac08-160">You can [include fields](#include-fields).</span></span>

<span data-ttu-id="dac08-161">System.Text.JsonASP.NET Core uygulamasında dolaylı olarak kullandığınızda, bazı varsayılan davranışlar farklıdır.</span><span class="sxs-lookup"><span data-stu-id="dac08-161">When you use System.Text.Json indirectly in an ASP.NET Core app, some default behaviors are different.</span></span> <span data-ttu-id="dac08-162">Daha fazla bilgi için bkz. [JsonSerializerOptions Için Web Varsayılanları](system-text-json-configure-options.md#web-defaults-for-jsonserializeroptions).</span><span class="sxs-lookup"><span data-stu-id="dac08-162">For more information, see [Web defaults for JsonSerializerOptions](system-text-json-configure-options.md#web-defaults-for-jsonserializeroptions).</span></span>
::: zone-end

::: zone pivot="dotnet-core-3-1"

* <span data-ttu-id="dac08-163">Varsayılan olarak, tüm ortak özellikler serileştirilir.</span><span class="sxs-lookup"><span data-stu-id="dac08-163">By default, all public properties are serialized.</span></span> <span data-ttu-id="dac08-164">[Yoksayılacak özellikleri belirtebilirsiniz](system-text-json-ignore-properties.md).</span><span class="sxs-lookup"><span data-stu-id="dac08-164">You can [specify properties to ignore](system-text-json-ignore-properties.md).</span></span>
* <span data-ttu-id="dac08-165">[Varsayılan KODLAYıCı](xref:System.Text.Encodings.Web.JavaScriptEncoder.Default) ASCII olmayan KARAKTERLERI, ASCII ARALıĞı içindeki HTML duyarlı KARAKTERLERI ve [RFC 8259 JSON](https://tools.ietf.org/html/rfc8259#section-7)belirtimine göre kaçılması gereken karakterleri çıkar.</span><span class="sxs-lookup"><span data-stu-id="dac08-165">The [default encoder](xref:System.Text.Encodings.Web.JavaScriptEncoder.Default) escapes non-ASCII characters, HTML-sensitive characters within the ASCII-range, and characters that must be escaped according to [the RFC 8259 JSON spec](https://tools.ietf.org/html/rfc8259#section-7).</span></span>
* <span data-ttu-id="dac08-166">Varsayılan olarak JSON, Mini olarak belirlenir.</span><span class="sxs-lookup"><span data-stu-id="dac08-166">By default, JSON is minified.</span></span> <span data-ttu-id="dac08-167">JSON 'ı [düzgün](#serialize-to-formatted-json)bir şekilde yazdırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="dac08-167">You can [pretty-print the JSON](#serialize-to-formatted-json).</span></span>
* <span data-ttu-id="dac08-168">Varsayılan olarak, JSON adlarının büyük küçük harfleri .NET adlarıyla eşleşir.</span><span class="sxs-lookup"><span data-stu-id="dac08-168">By default, casing of JSON names matches the .NET names.</span></span> <span data-ttu-id="dac08-169">[JSON adının büyük küçük harflerini özelleştirebilirsiniz](system-text-json-customize-properties.md).</span><span class="sxs-lookup"><span data-stu-id="dac08-169">You can [customize JSON name casing](system-text-json-customize-properties.md).</span></span>
* <span data-ttu-id="dac08-170">Döngüsel başvurular algılandı ve özel durumlar oluşturuldu.</span><span class="sxs-lookup"><span data-stu-id="dac08-170">Circular references are detected and exceptions thrown.</span></span>
* <span data-ttu-id="dac08-171">[Alanlar](../../csharp/programming-guide/classes-and-structs/fields.md) yok sayılır.</span><span class="sxs-lookup"><span data-stu-id="dac08-171">[Fields](../../csharp/programming-guide/classes-and-structs/fields.md) are ignored.</span></span>
::: zone-end

<span data-ttu-id="dac08-172">Desteklenen türler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="dac08-172">Supported types include:</span></span>
::: zone pivot="dotnet-5-0"

* <span data-ttu-id="dac08-173">Sayısal türler, dizeler ve Boole gibi JavaScript temel elemanlarına eşleyen .NET temel türleri.</span><span class="sxs-lookup"><span data-stu-id="dac08-173">.NET primitives that map to JavaScript primitives, such as numeric types, strings, and Boolean.</span></span>
* <span data-ttu-id="dac08-174">Kullanıcı tanımlı [düz eskı clr nesneleri (POCOs)](https://en.wikipedia.org/wiki/Plain_old_CLR_object).</span><span class="sxs-lookup"><span data-stu-id="dac08-174">User-defined [plain old CLR objects (POCOs)](https://en.wikipedia.org/wiki/Plain_old_CLR_object).</span></span>
* <span data-ttu-id="dac08-175">Tek boyutlu ve pürüzlü Diziler ( `T[][]` ).</span><span class="sxs-lookup"><span data-stu-id="dac08-175">One-dimensional and jagged arrays (`T[][]`).</span></span>
* <span data-ttu-id="dac08-176">Aşağıdaki ad alanlarından gelen koleksiyonlar ve sözlükler.</span><span class="sxs-lookup"><span data-stu-id="dac08-176">Collections and dictionaries from the following namespaces.</span></span>
  * <xref:System.Collections>
  * <xref:System.Collections.Generic>
  * <xref:System.Collections.Immutable>
  * <xref:System.Collections.Concurrent>
  * <xref:System.Collections.Specialized>
  * <xref:System.Collections.ObjectModel>
::: zone-end

::: zone pivot="dotnet-core-3-1"

* <span data-ttu-id="dac08-177">Sayısal türler, dizeler ve Boole gibi JavaScript temel elemanlarına eşleyen .NET temel türleri.</span><span class="sxs-lookup"><span data-stu-id="dac08-177">.NET primitives that map to JavaScript primitives, such as numeric types, strings, and Boolean.</span></span>
* <span data-ttu-id="dac08-178">Kullanıcı tanımlı [düz eskı clr nesneleri (POCOs)](https://en.wikipedia.org/wiki/Plain_old_CLR_object).</span><span class="sxs-lookup"><span data-stu-id="dac08-178">User-defined [plain old CLR objects (POCOs)](https://en.wikipedia.org/wiki/Plain_old_CLR_object).</span></span>
* <span data-ttu-id="dac08-179">Tek boyutlu ve pürüzlü Diziler ( `ArrayName[][]` ).</span><span class="sxs-lookup"><span data-stu-id="dac08-179">One-dimensional and jagged arrays (`ArrayName[][]`).</span></span>
* <span data-ttu-id="dac08-180">`Dictionary<string,TValue>` Burada `TValue` , `object` `JsonElement` veya bir poco.</span><span class="sxs-lookup"><span data-stu-id="dac08-180">`Dictionary<string,TValue>` where `TValue` is `object`, `JsonElement`, or a POCO.</span></span>
* <span data-ttu-id="dac08-181">Aşağıdaki ad alanlarından Koleksiyonlar.</span><span class="sxs-lookup"><span data-stu-id="dac08-181">Collections from the following namespaces.</span></span>
  * <xref:System.Collections>
  * <xref:System.Collections.Generic>
  * <xref:System.Collections.Immutable>
  * <xref:System.Collections.Concurrent>
  * <xref:System.Collections.Specialized>
  * <xref:System.Collections.ObjectModel>
::: zone-end

<span data-ttu-id="dac08-182">Ek türleri işlemek veya yerleşik dönüştürücüler tarafından desteklenmeyen işlevler sağlamak için [özel dönüştürücüler uygulayabilirsiniz](system-text-json-converters-how-to.md) .</span><span class="sxs-lookup"><span data-stu-id="dac08-182">You can [implement custom converters](system-text-json-converters-how-to.md) to handle additional types or to provide functionality that isn't supported by the built-in converters.</span></span>

## <a name="how-to-read-json-as-net-objects-deserialize"></a><span data-ttu-id="dac08-183">.NET nesneleri olarak JSON okuma (serisini kaldırma)</span><span class="sxs-lookup"><span data-stu-id="dac08-183">How to read JSON as .NET objects (deserialize)</span></span>

<span data-ttu-id="dac08-184">Bir dizeden veya dosyadan seri durumdan çıkarmak için <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType> yöntemini çağırın.</span><span class="sxs-lookup"><span data-stu-id="dac08-184">To deserialize from a string or a file, call the <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType> method.</span></span>

<span data-ttu-id="dac08-185">Aşağıdaki örnek, bir dizeden JSON okur ve `WeatherForecastWithPOCOs` daha önce [serileştirme örneği](#serialization-example)için gösterilen sınıfının bir örneğini oluşturur:</span><span class="sxs-lookup"><span data-stu-id="dac08-185">The following example reads JSON from a string and creates an instance of the `WeatherForecastWithPOCOs` class shown earlier for the [serialization example](#serialization-example):</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/RoundtripToString.cs" id="Deserialize":::
:::code language="vb" source="snippets/system-text-json-how-to/vb/RoundtripToString.vb" id="Deserialize":::

<span data-ttu-id="dac08-186">Zaman uyumlu kod kullanarak bir dosyadan seri durumdan çıkarmak için, aşağıdaki örnekte gösterildiği gibi dosyayı bir dizeye okuyun:</span><span class="sxs-lookup"><span data-stu-id="dac08-186">To deserialize from a file by using synchronous code, read the file into a string, as shown in the following example:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/RoundtripToFile.cs" id="Deserialize":::
:::code language="vb" source="snippets/system-text-json-how-to/vb/RoundtripToFile.vb" id="Deserialize":::

<span data-ttu-id="dac08-187">Zaman uyumsuz kod kullanarak bir dosyadan seri durumdan çıkarmak için yöntemini çağırın <xref:System.Text.Json.JsonSerializer.DeserializeAsync%2A> :</span><span class="sxs-lookup"><span data-stu-id="dac08-187">To deserialize from a file by using asynchronous code, call the <xref:System.Text.Json.JsonSerializer.DeserializeAsync%2A> method:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/RoundtripToFileAsync.cs" id="Deserialize":::
:::code language="vb" source="snippets/system-text-json-how-to/vb/RoundtripToFileAsync.vb" id="Deserialize":::

> [!TIP]
> <span data-ttu-id="dac08-188">Seri durumdan çıkarmak istediğiniz JSON varsa ve bunun serisini kaldırmak için sınıfınız yoksa, Visual Studio 2019, ihtiyacınız olan sınıfı otomatik olarak oluşturabilir:</span><span class="sxs-lookup"><span data-stu-id="dac08-188">If you have JSON that you want to deserialize, and you don't have the class to deserialize it into, Visual Studio 2019 can automatically generate the class you need:</span></span>
>
> 1. <span data-ttu-id="dac08-189">Seri durumdan çıkarmak için gereken JSON 'ı kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="dac08-189">Copy the JSON that you need to deserialize.</span></span>
> 1. <span data-ttu-id="dac08-190">Bir sınıf dosyası oluşturun ve şablon kodunu silin.</span><span class="sxs-lookup"><span data-stu-id="dac08-190">Create a class file and delete the template code.</span></span>
> 1. <span data-ttu-id="dac08-191">**Düzenleme**  >  **Yapıştır Özel**  >  **JSON 'ı sınıflar olarak Yapıştır**' ı seçin.</span><span class="sxs-lookup"><span data-stu-id="dac08-191">Choose **Edit** > **Paste Special** > **Paste JSON as Classes**.</span></span>
>
> <span data-ttu-id="dac08-192">Sonuç, seri durumdan çıkarma hedefi için kullanabileceğiniz bir sınıftır.</span><span class="sxs-lookup"><span data-stu-id="dac08-192">The result is a class that you can use for your deserialization target.</span></span>

## <a name="deserialize-from-utf-8"></a><span data-ttu-id="dac08-193">UTF-8 ' den serisini kaldırma</span><span class="sxs-lookup"><span data-stu-id="dac08-193">Deserialize from UTF-8</span></span>

<span data-ttu-id="dac08-194">UTF-8 ' den seri durumdan çıkarmak için, <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType> `ReadOnlySpan<byte>` `Utf8JsonReader` Aşağıdaki örneklerde gösterildiği gibi bir veya içeren bir aşırı yükleme çağırın.</span><span class="sxs-lookup"><span data-stu-id="dac08-194">To deserialize from UTF-8, call a <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType> overload that takes a `ReadOnlySpan<byte>` or a `Utf8JsonReader`, as shown in the following examples.</span></span> <span data-ttu-id="dac08-195">Örnekler, JSON 'ın jsonUtf8Bytes adlı bir bayt dizisinde olduğunu varsayar.</span><span class="sxs-lookup"><span data-stu-id="dac08-195">The examples assume the JSON is in a byte array named jsonUtf8Bytes.</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/RoundtripToUtf8.cs" id="Deserialize1":::
:::code language="vb" source="snippets/system-text-json-how-to/vb/RoundtripToUtf8.vb" id="Deserialize1":::

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/RoundtripToUtf8.cs" id="Deserialize2":::
:::code language="vb" source="snippets/system-text-json-how-to/vb/RoundtripToUtf8.vb" id="Deserialize2":::

## <a name="deserialization-behavior"></a><span data-ttu-id="dac08-196">Seri durumdan çıkarma davranışı</span><span class="sxs-lookup"><span data-stu-id="dac08-196">Deserialization behavior</span></span>

<span data-ttu-id="dac08-197">JSON serisi kaldırılırken aşağıdaki davranışlar geçerlidir:</span><span class="sxs-lookup"><span data-stu-id="dac08-197">The following behaviors apply when deserializing JSON:</span></span>

::: zone pivot="dotnet-5-0"

* <span data-ttu-id="dac08-198">Özellik adı eşleştirme, varsayılan olarak büyük/küçük harfe duyarlıdır.</span><span class="sxs-lookup"><span data-stu-id="dac08-198">By default, property name matching is case-sensitive.</span></span> <span data-ttu-id="dac08-199">[Büyük/küçük harf duyarlı belirtebilirsiniz](system-text-json-character-casing.md).</span><span class="sxs-lookup"><span data-stu-id="dac08-199">You can [specify case-insensitivity](system-text-json-character-casing.md).</span></span>
* <span data-ttu-id="dac08-200">JSON salt okunurdur özelliği için bir değer içeriyorsa, değer yok sayılır ve hiçbir özel durum oluşturulmaz.</span><span class="sxs-lookup"><span data-stu-id="dac08-200">If the JSON contains a value for a read-only property, the value is ignored and no exception is thrown.</span></span>
* <span data-ttu-id="dac08-201">Ortak olmayan oluşturucular seri hale getirici tarafından yok sayılır.</span><span class="sxs-lookup"><span data-stu-id="dac08-201">Non-public constructors are ignored by the serializer.</span></span>
* <span data-ttu-id="dac08-202">Sabit nesneler veya salt okunurdur özellikleri seri durumundan çıkarma desteklenir.</span><span class="sxs-lookup"><span data-stu-id="dac08-202">Deserialization to immutable objects or read-only properties is supported.</span></span> <span data-ttu-id="dac08-203">Bkz. [değişmez türler ve kayıtlar](system-text-json-immutability.md).</span><span class="sxs-lookup"><span data-stu-id="dac08-203">See [Immutable types and Records](system-text-json-immutability.md).</span></span>
* <span data-ttu-id="dac08-204">Varsayılan olarak, numaralandırmalar sayı olarak desteklenir.</span><span class="sxs-lookup"><span data-stu-id="dac08-204">By default, enums are supported as numbers.</span></span> <span data-ttu-id="dac08-205">[Enum adlarını dizeler olarak seri hale](system-text-json-customize-properties.md#enums-as-strings)getirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="dac08-205">You can [serialize enum names as strings](system-text-json-customize-properties.md#enums-as-strings).</span></span>
* <span data-ttu-id="dac08-206">Varsayılan olarak, alanlar yok sayılır.</span><span class="sxs-lookup"><span data-stu-id="dac08-206">By default, fields are ignored.</span></span> <span data-ttu-id="dac08-207">[Alanları dahil](#include-fields)edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="dac08-207">You can [include fields](#include-fields).</span></span>
* <span data-ttu-id="dac08-208">Varsayılan olarak, JSON 'daki açıklama veya sondaki virgüller özel durum oluşturur.</span><span class="sxs-lookup"><span data-stu-id="dac08-208">By default, comments or trailing commas in the JSON throw exceptions.</span></span> <span data-ttu-id="dac08-209">[Yorumlara ve sondaki virgüllerin bulunmasına izin](system-text-json-invalid-json.md)verebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="dac08-209">You can [allow comments and trailing commas](system-text-json-invalid-json.md).</span></span>
* <span data-ttu-id="dac08-210">[Varsayılan en yüksek derinlik](xref:System.Text.Json.JsonReaderOptions.MaxDepth) 64 ' dir.</span><span class="sxs-lookup"><span data-stu-id="dac08-210">The [default maximum depth](xref:System.Text.Json.JsonReaderOptions.MaxDepth) is 64.</span></span>

<span data-ttu-id="dac08-211">System.Text.JsonASP.NET Core uygulamasında dolaylı olarak kullandığınızda, bazı varsayılan davranışlar farklıdır.</span><span class="sxs-lookup"><span data-stu-id="dac08-211">When you use System.Text.Json indirectly in an ASP.NET Core app, some default behaviors are different.</span></span> <span data-ttu-id="dac08-212">Daha fazla bilgi için bkz. [JsonSerializerOptions Için Web Varsayılanları](system-text-json-configure-options.md#web-defaults-for-jsonserializeroptions).</span><span class="sxs-lookup"><span data-stu-id="dac08-212">For more information, see [Web defaults for JsonSerializerOptions](system-text-json-configure-options.md#web-defaults-for-jsonserializeroptions).</span></span>
::: zone-end

::: zone pivot="dotnet-core-3-1"

* <span data-ttu-id="dac08-213">Özellik adı eşleştirme, varsayılan olarak büyük/küçük harfe duyarlıdır.</span><span class="sxs-lookup"><span data-stu-id="dac08-213">By default, property name matching is case-sensitive.</span></span> <span data-ttu-id="dac08-214">[Büyük/küçük harf duyarlı belirtebilirsiniz](system-text-json-character-casing.md).</span><span class="sxs-lookup"><span data-stu-id="dac08-214">You can [specify case-insensitivity](system-text-json-character-casing.md).</span></span> <span data-ttu-id="dac08-215">ASP.NET Core uygulamalar [Varsayılan olarak büyük/küçük harf duyarlı belirtir](system-text-json-configure-options.md#web-defaults-for-jsonserializeroptions).</span><span class="sxs-lookup"><span data-stu-id="dac08-215">ASP.NET Core apps [specify case-insensitivity by default](system-text-json-configure-options.md#web-defaults-for-jsonserializeroptions).</span></span>
* <span data-ttu-id="dac08-216">JSON salt okunurdur özelliği için bir değer içeriyorsa, değer yok sayılır ve hiçbir özel durum oluşturulmaz.</span><span class="sxs-lookup"><span data-stu-id="dac08-216">If the JSON contains a value for a read-only property, the value is ignored and no exception is thrown.</span></span>
* <span data-ttu-id="dac08-217">Seri durumdan çıkarma için genel, iç veya özel olabilen parametresiz bir Oluşturucu kullanılır.</span><span class="sxs-lookup"><span data-stu-id="dac08-217">A parameterless constructor, which can be public, internal, or private, is used for deserialization.</span></span>
* <span data-ttu-id="dac08-218">Sabit nesneler veya salt okunurdur özellikleri seri durumundan çıkarma desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="dac08-218">Deserialization to immutable objects or read-only properties isn't supported.</span></span>
* <span data-ttu-id="dac08-219">Varsayılan olarak, numaralandırmalar sayı olarak desteklenir.</span><span class="sxs-lookup"><span data-stu-id="dac08-219">By default, enums are supported as numbers.</span></span> <span data-ttu-id="dac08-220">[Enum adlarını dizeler olarak seri hale](system-text-json-customize-properties.md#enums-as-strings)getirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="dac08-220">You can [serialize enum names as strings](system-text-json-customize-properties.md#enums-as-strings).</span></span>
* <span data-ttu-id="dac08-221">Alanlar desteklenmiyor.</span><span class="sxs-lookup"><span data-stu-id="dac08-221">Fields aren't supported.</span></span>
* <span data-ttu-id="dac08-222">Varsayılan olarak, JSON 'daki açıklama veya sondaki virgüller özel durum oluşturur.</span><span class="sxs-lookup"><span data-stu-id="dac08-222">By default, comments or trailing commas in the JSON throw exceptions.</span></span> <span data-ttu-id="dac08-223">[Yorumlara ve sondaki virgüllerin bulunmasına izin](system-text-json-invalid-json.md)verebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="dac08-223">You can [allow comments and trailing commas](system-text-json-invalid-json.md).</span></span>
* <span data-ttu-id="dac08-224">[Varsayılan en yüksek derinlik](xref:System.Text.Json.JsonReaderOptions.MaxDepth) 64 ' dir.</span><span class="sxs-lookup"><span data-stu-id="dac08-224">The [default maximum depth](xref:System.Text.Json.JsonReaderOptions.MaxDepth) is 64.</span></span>

<span data-ttu-id="dac08-225">System.Text.JsonASP.NET Core uygulamasında dolaylı olarak kullandığınızda, bazı varsayılan davranışlar farklıdır.</span><span class="sxs-lookup"><span data-stu-id="dac08-225">When you use System.Text.Json indirectly in an ASP.NET Core app, some default behaviors are different.</span></span> <span data-ttu-id="dac08-226">Daha fazla bilgi için bkz. [JsonSerializerOptions Için Web Varsayılanları](system-text-json-configure-options.md#web-defaults-for-jsonserializeroptions).</span><span class="sxs-lookup"><span data-stu-id="dac08-226">For more information, see [Web defaults for JsonSerializerOptions](system-text-json-configure-options.md#web-defaults-for-jsonserializeroptions).</span></span>
::: zone-end

<span data-ttu-id="dac08-227">Yerleşik dönüştürücüler tarafından desteklenmeyen işlevselliği sağlamak için [özel dönüştürücüler uygulayabilirsiniz](system-text-json-converters-how-to.md) .</span><span class="sxs-lookup"><span data-stu-id="dac08-227">You can [implement custom converters](system-text-json-converters-how-to.md) to provide functionality that isn't supported by the built-in converters.</span></span>

## <a name="serialize-to-formatted-json"></a><span data-ttu-id="dac08-228">Biçimlendirilen JSON 'a serileştirme</span><span class="sxs-lookup"><span data-stu-id="dac08-228">Serialize to formatted JSON</span></span>

<span data-ttu-id="dac08-229">JSON çıkışını gerçekten yazdırmak için şu <xref:System.Text.Json.JsonSerializerOptions.WriteIndented?displayProperty=nameWithType> şekilde ayarlayın `true` :</span><span class="sxs-lookup"><span data-stu-id="dac08-229">To pretty-print the JSON output, set <xref:System.Text.Json.JsonSerializerOptions.WriteIndented?displayProperty=nameWithType> to `true`:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/RoundtripToString.cs" id="SerializePrettyPrint":::
:::code language="vb" source="snippets/system-text-json-how-to/vb/RoundtripToString.vb" id="SerializePrettyPrint":::

<span data-ttu-id="dac08-230">Aşağıda, seri hale getirilebilir ve düzgün şekilde yazdırılan JSON çıkışının örnek bir türü verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="dac08-230">Here's an example type to be serialized and pretty-printed JSON output:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/WeatherForecast.cs" id="WF":::
:::code language="vb" source="snippets/system-text-json-how-to/vb/WeatherForecast.vb" id="WF":::

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "Hot"
}
```

<span data-ttu-id="dac08-231">`JsonSerializerOptions`Aynı seçeneklerle tekrar tekrar kullanırsanız, `JsonSerializerOptions` her kullandığınızda yeni bir örnek oluşturmayın.</span><span class="sxs-lookup"><span data-stu-id="dac08-231">If you use `JsonSerializerOptions` repeatedly with the same options, don't create a new `JsonSerializerOptions` instance each time you use it.</span></span> <span data-ttu-id="dac08-232">Her çağrı için aynı örneği yeniden kullanın.</span><span class="sxs-lookup"><span data-stu-id="dac08-232">Reuse the same instance for every call.</span></span> <span data-ttu-id="dac08-233">Daha fazla bilgi için bkz. [JsonSerializerOptions örneklerini yeniden kullanma](system-text-json-configure-options.md#reuse-jsonserializeroptions-instances).</span><span class="sxs-lookup"><span data-stu-id="dac08-233">For more information, see [Reuse JsonSerializerOptions instances](system-text-json-configure-options.md#reuse-jsonserializeroptions-instances).</span></span>

## <a name="include-fields"></a><span data-ttu-id="dac08-234">Dahil etme alanları</span><span class="sxs-lookup"><span data-stu-id="dac08-234">Include fields</span></span>

::: zone pivot="dotnet-5-0"
<span data-ttu-id="dac08-235"><xref:System.Text.Json.JsonSerializerOptions.IncludeFields?displayProperty=nameWithType>Aşağıdaki örnekte gösterildiği gibi, seri hale getirilirken veya seri durumdan çıkarılırken alanları dahil etmek için genel ayarını veya [[jsonınclude]](xref:System.Text.Json.Serialization.JsonIncludeAttribute) özniteliğini kullanın:</span><span class="sxs-lookup"><span data-stu-id="dac08-235">Use the <xref:System.Text.Json.JsonSerializerOptions.IncludeFields?displayProperty=nameWithType> global setting or the [[JsonInclude]](xref:System.Text.Json.Serialization.JsonIncludeAttribute) attribute to include fields when serializing or deserializing, as shown in the following example:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to-5-0/csharp/Fields.cs" highlight="16,18,20,32-35":::
:::code language="vb" source="snippets/system-text-json-how-to-5-0/vb/Fields.vb" :::

<span data-ttu-id="dac08-236">Salt okuma alanlarını yok saymak için <xref:System.Text.Json.JsonSerializerOptions.IgnoreReadOnlyFields%2A?displayProperty=nameWithType> genel ayarını kullanın.</span><span class="sxs-lookup"><span data-stu-id="dac08-236">To ignore read-only fields, use the <xref:System.Text.Json.JsonSerializerOptions.IgnoreReadOnlyFields%2A?displayProperty=nameWithType> global setting.</span></span>
::: zone-end

::: zone pivot="dotnet-core-3-1"
<span data-ttu-id="dac08-237">Alanlar System.Text.Json .NET Core 3,1 ' de desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="dac08-237">Fields are not supported in System.Text.Json in .NET Core 3.1.</span></span> <span data-ttu-id="dac08-238">[Özel dönüştürücüler](system-text-json-converters-how-to.md) , bu işlevselliği sağlayabilir.</span><span class="sxs-lookup"><span data-stu-id="dac08-238">[Custom converters](system-text-json-converters-how-to.md) can provide this functionality.</span></span>
::: zone-end

## <a name="httpclient-and-httpcontent-extension-methods"></a><span data-ttu-id="dac08-239">HttpClient ve HttpContent genişletme yöntemleri</span><span class="sxs-lookup"><span data-stu-id="dac08-239">HttpClient and HttpContent extension methods</span></span>

::: zone pivot="dotnet-5-0"

<span data-ttu-id="dac08-240">JSON yüklerini ağdan serileştirmek ve serisini kaldırma yaygın işlemlerdir.</span><span class="sxs-lookup"><span data-stu-id="dac08-240">Serializing and deserializing JSON payloads from the network are common operations.</span></span> <span data-ttu-id="dac08-241">[HttpClient](xref:System.Net.Http.Json.HttpClientJsonExtensions) ve [HttpContent](xref:System.Net.Http.Json.HttpContentJsonExtensions) üzerindeki genişletme yöntemleri, bu işlemleri tek bir kod satırında yapmanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="dac08-241">Extension methods on [HttpClient](xref:System.Net.Http.Json.HttpClientJsonExtensions) and [HttpContent](xref:System.Net.Http.Json.HttpContentJsonExtensions) let you do these operations in a single line of code.</span></span> <span data-ttu-id="dac08-242">Bu uzantı yöntemleri, [JsonSerializerOptions için Web varsayılanlarını](system-text-json-configure-options.md#web-defaults-for-jsonserializeroptions)kullanır.</span><span class="sxs-lookup"><span data-stu-id="dac08-242">These extension methods use [web defaults for JsonSerializerOptions](system-text-json-configure-options.md#web-defaults-for-jsonserializeroptions).</span></span>

<span data-ttu-id="dac08-243">Aşağıdaki örnek, ve kullanımını göstermektedir <xref:System.Net.Http.Json.HttpClientJsonExtensions.GetFromJsonAsync%2A?displayProperty=nameWithType> <xref:System.Net.Http.Json.HttpClientJsonExtensions.PostAsJsonAsync%2A?displayProperty=nameWithType> :</span><span class="sxs-lookup"><span data-stu-id="dac08-243">The following example illustrates use of <xref:System.Net.Http.Json.HttpClientJsonExtensions.GetFromJsonAsync%2A?displayProperty=nameWithType> and <xref:System.Net.Http.Json.HttpClientJsonExtensions.PostAsJsonAsync%2A?displayProperty=nameWithType>:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to-5-0/csharp/HttpClientExtensionMethods.cs" highlight="26,33":::
:::code language="vb" source="snippets/system-text-json-how-to-5-0/vb/HttpClientExtensionMethods.vb" :::

<span data-ttu-id="dac08-244">Ayrıca, HttpContent için uzantı yöntemleri de vardır System.Text.Json . [](xref:System.Net.Http.Json.HttpContentJsonExtensions)</span><span class="sxs-lookup"><span data-stu-id="dac08-244">There are also extension methods for System.Text.Json on [HttpContent](xref:System.Net.Http.Json.HttpContentJsonExtensions).</span></span>
::: zone-end

::: zone pivot="dotnet-core-3-1"
<span data-ttu-id="dac08-245">Ve ' de uzantı yöntemleri `HttpClient` `HttpContent` System.Text.Json .NET Core 3,1 ' de kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="dac08-245">Extension methods on `HttpClient` and `HttpContent` are not available in System.Text.Json in .NET Core 3.1.</span></span>
::: zone-end

## <a name="see-also"></a><span data-ttu-id="dac08-246">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="dac08-246">See also</span></span>

* [<span data-ttu-id="dac08-247">System.Text.Json bakýþ</span><span class="sxs-lookup"><span data-stu-id="dac08-247">System.Text.Json overview</span></span>](system-text-json-overview.md)
* [<span data-ttu-id="dac08-248">JsonSerializerOptions örneklerinin örneğini oluşturma</span><span class="sxs-lookup"><span data-stu-id="dac08-248">Instantiate JsonSerializerOptions instances</span></span>](system-text-json-configure-options.md)
* [<span data-ttu-id="dac08-249">Büyük/küçük harf duyarlı eşlemeyi etkinleştirme</span><span class="sxs-lookup"><span data-stu-id="dac08-249">Enable case-insensitive matching</span></span>](system-text-json-character-casing.md)
* [<span data-ttu-id="dac08-250">Özellik adlarını ve değerlerini özelleştirme</span><span class="sxs-lookup"><span data-stu-id="dac08-250">Customize property names and values</span></span>](system-text-json-customize-properties.md)
* [<span data-ttu-id="dac08-251">Özellikleri yoksayma</span><span class="sxs-lookup"><span data-stu-id="dac08-251">Ignore properties</span></span>](system-text-json-ignore-properties.md)
* [<span data-ttu-id="dac08-252">Geçersiz JSON’a izin verme</span><span class="sxs-lookup"><span data-stu-id="dac08-252">Allow invalid JSON</span></span>](system-text-json-invalid-json.md)
* [<span data-ttu-id="dac08-253">Sap taşması JSON’ı</span><span class="sxs-lookup"><span data-stu-id="dac08-253">Handle overflow JSON</span></span>](system-text-json-handle-overflow.md)
* [<span data-ttu-id="dac08-254">Başvuruları koruma</span><span class="sxs-lookup"><span data-stu-id="dac08-254">Preserve references</span></span>](system-text-json-preserve-references.md)
* [<span data-ttu-id="dac08-255">Sabit türler ve genel olmayan erişimciler</span><span class="sxs-lookup"><span data-stu-id="dac08-255">Immutable types and non-public accessors</span></span>](system-text-json-immutability.md)
* [<span data-ttu-id="dac08-256">Polimorfik serileştirme</span><span class="sxs-lookup"><span data-stu-id="dac08-256">Polymorphic serialization</span></span>](system-text-json-polymorphism.md)
* [<span data-ttu-id="dac08-257">' Den ' a geçiş Newtonsoft.JsonSystem.Text.Json</span><span class="sxs-lookup"><span data-stu-id="dac08-257">Migrate from Newtonsoft.Json to System.Text.Json</span></span>](system-text-json-migrate-from-newtonsoft-how-to.md)
* [<span data-ttu-id="dac08-258">Karakter kodlamasını özelleştirme</span><span class="sxs-lookup"><span data-stu-id="dac08-258">Customize character encoding</span></span>](system-text-json-character-encoding.md)
* [<span data-ttu-id="dac08-259">Özel serileştiriciler ve seri hale getiriciler yazma</span><span class="sxs-lookup"><span data-stu-id="dac08-259">Write custom serializers and deserializers</span></span>](write-custom-serializer-deserializer.md)
* [<span data-ttu-id="dac08-260">JSON serileştirme için özel dönüştürücüler yazma</span><span class="sxs-lookup"><span data-stu-id="dac08-260">Write custom converters for JSON serialization</span></span>](system-text-json-converters-how-to.md)
* [<span data-ttu-id="dac08-261">DateTime ve DateTimeOffset desteği</span><span class="sxs-lookup"><span data-stu-id="dac08-261">DateTime and DateTimeOffset support</span></span>](../datetime/system-text-json-support.md)
* [<span data-ttu-id="dac08-262">İçinde desteklenen koleksiyon türleri System.Text.Json</span><span class="sxs-lookup"><span data-stu-id="dac08-262">Supported collection types in System.Text.Json</span></span>](system-text-json-supported-collection-types.md)
* <span data-ttu-id="dac08-263">[System.Text.Json API başvurusu](xref:System.Text.Json)</span><span class="sxs-lookup"><span data-stu-id="dac08-263">[System.Text.Json API reference](xref:System.Text.Json)</span></span>
* <span data-ttu-id="dac08-264">[System.Text.Json. Serileştirme API başvurusu](xref:System.Text.Json.Serialization)</span><span class="sxs-lookup"><span data-stu-id="dac08-264">[System.Text.Json.Serialization API reference](xref:System.Text.Json.Serialization)</span></span>
