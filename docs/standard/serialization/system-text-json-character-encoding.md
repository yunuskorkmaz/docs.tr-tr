---
title: İle karakter kodlamasını özelleştirme System.Text.Json
description: .NET 'teki JSON 'a serileştirirken ve seri durumdan çıkarılırken karakter kodlamasını özelleştirmeyi öğrenin.
ms.date: 01/22/2021
no-loc:
- System.Text.Json
- Newtonsoft.Json
helpviewer_keywords:
- JSON serialization
- serializing objects
- serialization
- objects, serializing
ms.openlocfilehash: 136a75ab73767fd79f99caa1d1387706ab655473
ms.sourcegitcommit: 68c9d9d9a97aab3b59d388914004b5474cf1dbd7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/30/2021
ms.locfileid: "99215985"
---
# <a name="how-to-customize-character-encoding-with-no-locsystemtextjson"></a><span data-ttu-id="25b93-103">İle karakter kodlamasını özelleştirme System.Text.Json</span><span class="sxs-lookup"><span data-stu-id="25b93-103">How to customize character encoding with System.Text.Json</span></span>

<span data-ttu-id="25b93-104">Varsayılan olarak, seri hale getirici ASCII olmayan tüm karakterleri çıkar.</span><span class="sxs-lookup"><span data-stu-id="25b93-104">By default, the serializer escapes all non-ASCII characters.</span></span> <span data-ttu-id="25b93-105">Diğer bir deyişle, bu, `\uxxxx` karakterin Unicode kodunun bulunduğu konum ile değiştirilir `xxxx` .</span><span class="sxs-lookup"><span data-stu-id="25b93-105">That is, it replaces them with `\uxxxx` where `xxxx` is the Unicode code of the character.</span></span> <span data-ttu-id="25b93-106">Örneğin, `Summary` AŞAĞıDAKI JSON 'daki Özellik Kiril olarak ayarlandıysa `жарко` , `WeatherForecast` nesne şu örnekte gösterildiği gibi serileştirilir:</span><span class="sxs-lookup"><span data-stu-id="25b93-106">For example, if the `Summary` property in the following JSON is set to Cyrillic `жарко`, the `WeatherForecast` object is serialized as shown in this example:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "\u0436\u0430\u0440\u043A\u043E"
}
```

## <a name="serialize-language-character-sets"></a><span data-ttu-id="25b93-107">Dil karakter kümelerini serileştirme</span><span class="sxs-lookup"><span data-stu-id="25b93-107">Serialize language character sets</span></span>

<span data-ttu-id="25b93-108">Bir veya daha fazla dilin karakter kümesini kaçış olmadan seri hale getirmek için, aşağıdaki örnekte gösterildiği gibi bir örneği oluştururken [Unicode aralığı](xref:System.Text.Unicode.UnicodeRanges) belirtin <xref:System.Text.Encodings.Web.JavaScriptEncoder?displayProperty=fullName> :</span><span class="sxs-lookup"><span data-stu-id="25b93-108">To serialize the character set(s) of one or more languages without escaping, specify [Unicode range(s)](xref:System.Text.Unicode.UnicodeRanges) when creating an instance of <xref:System.Text.Encodings.Web.JavaScriptEncoder?displayProperty=fullName>, as shown in the following example:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/SerializeCustomEncoding.cs" id="Usings":::

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/SerializeCustomEncoding.cs" id="LanguageSets":::

<span data-ttu-id="25b93-109">Bu kod, Kiril veya Yunan karakterlerinden kaçış yapmaz.</span><span class="sxs-lookup"><span data-stu-id="25b93-109">This code doesn't escape Cyrillic or Greek characters.</span></span> <span data-ttu-id="25b93-110">`Summary`Özellik Kiril olarak ayarlandıysa `жарко` , `WeatherForecast` nesne şu örnekte gösterildiği gibi serileştirilir:</span><span class="sxs-lookup"><span data-stu-id="25b93-110">If the `Summary` property is set to Cyrillic `жарко`, the `WeatherForecast` object is serialized as shown in this example:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "жарко"
}
```

<span data-ttu-id="25b93-111">Kodlayıcı, varsayılan olarak <xref:System.Text.Unicode.UnicodeRanges.BasicLatin> aralığıyla başlatılır.</span><span class="sxs-lookup"><span data-stu-id="25b93-111">By default, the encoder is initialized with the <xref:System.Text.Unicode.UnicodeRanges.BasicLatin> range.</span></span>

<span data-ttu-id="25b93-112">Tüm dil kümelerini kaçış olmadan seri hale getirmek için kullanın <xref:System.Text.Unicode.UnicodeRanges.All?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="25b93-112">To serialize all language sets without escaping, use <xref:System.Text.Unicode.UnicodeRanges.All?displayProperty=nameWithType>.</span></span>

## <a name="serialize-specific-characters"></a><span data-ttu-id="25b93-113">Belirli karakterleri serileştirme</span><span class="sxs-lookup"><span data-stu-id="25b93-113">Serialize specific characters</span></span>

<span data-ttu-id="25b93-114">Diğer bir seçenek de, kaçırılmadan, izin vermek istediğiniz tek tek karakterleri belirtmektir.</span><span class="sxs-lookup"><span data-stu-id="25b93-114">An alternative is to specify individual characters that you want to allow through without being escaped.</span></span> <span data-ttu-id="25b93-115">Aşağıdaki örnek, öğesinin yalnızca ilk iki karakterini seri hale getirir `жарко` :</span><span class="sxs-lookup"><span data-stu-id="25b93-115">The following example serializes only the first two characters of `жарко`:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/SerializeCustomEncoding.cs" id="Usings":::

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/SerializeCustomEncoding.cs" id="SelectedCharacters":::

<span data-ttu-id="25b93-116">Yukarıdaki kod tarafından üretilen JSON örneği aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="25b93-116">Here's an example of JSON produced by the preceding code:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "жа\u0440\u043A\u043E"
}
```

## <a name="block-lists"></a><span data-ttu-id="25b93-117">Engelleme listeleri</span><span class="sxs-lookup"><span data-stu-id="25b93-117">Block lists</span></span>

<span data-ttu-id="25b93-118">Yukarıdaki bölümlerde, çıkış yapmak istemediğiniz kod noktalarının veya aralıklarının izin verilenler listelerinin nasıl belirtildiği gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="25b93-118">The preceding sections show how to specify allow lists of code points or ranges that you don't want to be escaped.</span></span> <span data-ttu-id="25b93-119">Ancak, izin verilenler listenizde belirli kod noktalarını geçersiz kılabilen genel ve kodlayıcılara özgü blok listeleri vardır.</span><span class="sxs-lookup"><span data-stu-id="25b93-119">However, there are global and encoder-specific block lists that can override certain code points in your allow list.</span></span> <span data-ttu-id="25b93-120">Bir blok listesindeki kod noktaları, izin verilenler listenize dahil edilse de her zaman kaçışlar.</span><span class="sxs-lookup"><span data-stu-id="25b93-120">Code points in a block list are always escaped, even if they're included in your allow list.</span></span>

### <a name="global-block-list"></a><span data-ttu-id="25b93-121">Genel engellenenler listesi</span><span class="sxs-lookup"><span data-stu-id="25b93-121">Global block list</span></span>

<span data-ttu-id="25b93-122">Genel engellenenler listesi, özel kullanım karakterleri, denetim karakterleri, tanımsız kod noktaları ve [Space_Separator kategorisi](https://util.unicode.org/UnicodeJsps/list-unicodeset.jsp?a=%5B:General_Category=Space_Separator:%5D)gibi bazı Unicode kategorilerini içerir `U+0020 SPACE` .</span><span class="sxs-lookup"><span data-stu-id="25b93-122">The global block list includes things like private-use characters, control characters, undefined code points, and certain Unicode categories, such as the [Space_Separator category](https://util.unicode.org/UnicodeJsps/list-unicodeset.jsp?a=%5B:General_Category=Space_Separator:%5D), excluding `U+0020 SPACE`.</span></span> <span data-ttu-id="25b93-123">Örneğin, `U+3000 IDEOGRAPHIC SPACE` izin verilenler listeniz olarak @ [sembolleri ve noktalama Işaretlerini (U +3000-U + 303f)](xref:System.Text.Unicode.UnicodeRanges.CjkSymbolsandPunctuation) belirtseniz bile kaçış olur.</span><span class="sxs-lookup"><span data-stu-id="25b93-123">For example, `U+3000 IDEOGRAPHIC SPACE` is escaped even if you specify Unicode range [CJK Symbols and Punctuation (U+3000-U+303F)](xref:System.Text.Unicode.UnicodeRanges.CjkSymbolsandPunctuation) as your allow list.</span></span>

<span data-ttu-id="25b93-124">Genel engelleme listesi, .NET Core ve .NET 5 ' in her sürümünde değişen bir uygulama ayrıntıdır.</span><span class="sxs-lookup"><span data-stu-id="25b93-124">The global block list is an implementation detail that has changed in every release of .NET Core and in .NET 5.</span></span> <span data-ttu-id="25b93-125">Genel engelleme listesinin üyesi olan (veya üyesi olmayan) bir karakter üzerinde bağımlılık yapmayın.</span><span class="sxs-lookup"><span data-stu-id="25b93-125">Don't take a dependency on a character being a member of (or not being a member of) the global block list.</span></span>

### <a name="encoder-specific-block-lists"></a><span data-ttu-id="25b93-126">Kodlayıcıya özgü blok listeleri</span><span class="sxs-lookup"><span data-stu-id="25b93-126">Encoder-specific block lists</span></span>

<span data-ttu-id="25b93-127">Kodlayıcılara özgü engellenen kod noktaları örnekleri `'<'` `'&'` , [HTML Kodlayıcısı](xref:System.Text.Encodings.Web.HtmlEncoder), `'\'` [JSON Kodlayıcısı](xref:System.Text.Encodings.Web.JavaScriptEncoder)ve `'%'` [URL Kodlayıcısı](xref:System.Text.Encodings.Web.UrlEncoder)için içerir.</span><span class="sxs-lookup"><span data-stu-id="25b93-127">Examples of encoder-specific blocked code points include `'<'` and `'&'` for the [HTML encoder](xref:System.Text.Encodings.Web.HtmlEncoder), `'\'` for the [JSON encoder](xref:System.Text.Encodings.Web.JavaScriptEncoder), and `'%'` for the [URL encoder](xref:System.Text.Encodings.Web.UrlEncoder).</span></span> <span data-ttu-id="25b93-128">Örneğin, HTML Kodlayıcısı her zaman `'&'` ampersan () den çıkar, ancak `BasicLatin` ve tüm kodlayıcılar `BasicLatin` Varsayılan olarak ile başlatılır.</span><span class="sxs-lookup"><span data-stu-id="25b93-128">For example, the HTML encoder always escapes ampersands (`'&'`), even though the ampersand is in the `BasicLatin` range and all the encoders are initialized with `BasicLatin` by default.</span></span>

## <a name="serialize-all-characters"></a><span data-ttu-id="25b93-129">Tüm karakterleri seri hale getirme</span><span class="sxs-lookup"><span data-stu-id="25b93-129">Serialize all characters</span></span>

<span data-ttu-id="25b93-130"><xref:System.Text.Encodings.Web.JavaScriptEncoder.UnsafeRelaxedJsonEscaping?displayProperty=nameWithType>Aşağıdaki örnekte gösterildiği gibi, kullanarak kaçı en aza indirin:</span><span class="sxs-lookup"><span data-stu-id="25b93-130">To minimize escaping you can use <xref:System.Text.Encodings.Web.JavaScriptEncoder.UnsafeRelaxedJsonEscaping?displayProperty=nameWithType>, as shown in the following example:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/SerializeCustomEncoding.cs" id="Usings":::

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/SerializeCustomEncoding.cs" id="UnsafeRelaxed":::

> [!CAUTION]
> <span data-ttu-id="25b93-131">Varsayılan kodlayıcıyla karşılaştırıldığında kodlayıcı, `UnsafeRelaxedJsonEscaping` karakterlerin kaçışsız geçmesine izin verme konusunda daha fazla izne sahiptir:</span><span class="sxs-lookup"><span data-stu-id="25b93-131">Compared to the default encoder, the `UnsafeRelaxedJsonEscaping` encoder is more permissive about allowing characters to pass through unescaped:</span></span>
>
> * <span data-ttu-id="25b93-132">,, Ve gibi HTML 'ye duyarlı karakterleri atmaz `<` `>` `&` `'` .</span><span class="sxs-lookup"><span data-stu-id="25b93-132">It doesn't escape HTML-sensitive characters such as `<`, `>`, `&`, and `'`.</span></span>
> * <span data-ttu-id="25b93-133">Bu, XSS veya bilgi açıklama saldırılarına karşı ek derinlemesine savunma korumaları sunmaz, örneğin, *karakter* kümesinde istemci ve sunucu disagreeing neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="25b93-133">It doesn't offer any additional defense-in-depth protections against XSS or information disclosure attacks, such as those which might result from the client and server disagreeing on the *charset*.</span></span>
>
> <span data-ttu-id="25b93-134">Güvenli olmayan kodlayıcıyı yalnızca istemcinin, elde edilen yükü UTF-8 ile kodlanmış JSON olarak yorumladığı bilindiğinde kullanın.</span><span class="sxs-lookup"><span data-stu-id="25b93-134">Use the unsafe encoder only when it's known that the client will be interpreting the resulting payload as UTF-8 encoded JSON.</span></span> <span data-ttu-id="25b93-135">Örneğin, sunucu yanıt üst bilgisini gönderiyorsa onu kullanabilirsiniz `Content-Type: application/json; charset=utf-8` .</span><span class="sxs-lookup"><span data-stu-id="25b93-135">For example, you can use it if the server is sending the response header `Content-Type: application/json; charset=utf-8`.</span></span> <span data-ttu-id="25b93-136">Ham `UnsafeRelaxedJsonEscaping` çıkışın BIR HTML sayfasına veya bir öğeye yayılmasın `<script>` .</span><span class="sxs-lookup"><span data-stu-id="25b93-136">Never allow the raw `UnsafeRelaxedJsonEscaping` output to be emitted into an HTML page or a `<script>` element.</span></span>

## <a name="see-also"></a><span data-ttu-id="25b93-137">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="25b93-137">See also</span></span>

* [<span data-ttu-id="25b93-138">System.Text.Json bakýþ</span><span class="sxs-lookup"><span data-stu-id="25b93-138">System.Text.Json overview</span></span>](system-text-json-overview.md)
* [<span data-ttu-id="25b93-139">JSON’u seri hale getirme ve seri halden çıkarma</span><span class="sxs-lookup"><span data-stu-id="25b93-139">How to serialize and deserialize JSON</span></span>](system-text-json-how-to.md)
* [<span data-ttu-id="25b93-140">JsonSerializerOptions örneklerinin örneğini oluşturma</span><span class="sxs-lookup"><span data-stu-id="25b93-140">Instantiate JsonSerializerOptions instances</span></span>](system-text-json-configure-options.md)
* [<span data-ttu-id="25b93-141">Büyük/küçük harf duyarlı eşlemeyi etkinleştirme</span><span class="sxs-lookup"><span data-stu-id="25b93-141">Enable case-insensitive matching</span></span>](system-text-json-character-casing.md)
* [<span data-ttu-id="25b93-142">Özellik adlarını ve değerlerini özelleştirme</span><span class="sxs-lookup"><span data-stu-id="25b93-142">Customize property names and values</span></span>](system-text-json-customize-properties.md)
* [<span data-ttu-id="25b93-143">Özellikleri yoksayma</span><span class="sxs-lookup"><span data-stu-id="25b93-143">Ignore properties</span></span>](system-text-json-ignore-properties.md)
* [<span data-ttu-id="25b93-144">Geçersiz JSON’a izin verme</span><span class="sxs-lookup"><span data-stu-id="25b93-144">Allow invalid JSON</span></span>](system-text-json-invalid-json.md)
* [<span data-ttu-id="25b93-145">Sap taşması JSON’ı</span><span class="sxs-lookup"><span data-stu-id="25b93-145">Handle overflow JSON</span></span>](system-text-json-handle-overflow.md)
* [<span data-ttu-id="25b93-146">Başvuruları koruma</span><span class="sxs-lookup"><span data-stu-id="25b93-146">Preserve references</span></span>](system-text-json-preserve-references.md)
* [<span data-ttu-id="25b93-147">Sabit türler ve genel olmayan erişimciler</span><span class="sxs-lookup"><span data-stu-id="25b93-147">Immutable types and non-public accessors</span></span>](system-text-json-immutability.md)
* [<span data-ttu-id="25b93-148">Polimorfik serileştirme</span><span class="sxs-lookup"><span data-stu-id="25b93-148">Polymorphic serialization</span></span>](system-text-json-polymorphism.md)
* [<span data-ttu-id="25b93-149">' Den ' a geçiş Newtonsoft.JsonSystem.Text.Json</span><span class="sxs-lookup"><span data-stu-id="25b93-149">Migrate from Newtonsoft.Json to System.Text.Json</span></span>](system-text-json-migrate-from-newtonsoft-how-to.md)
* [<span data-ttu-id="25b93-150">Özel serileştiriciler ve seri hale getiriciler yazma</span><span class="sxs-lookup"><span data-stu-id="25b93-150">Write custom serializers and deserializers</span></span>](write-custom-serializer-deserializer.md)
* [<span data-ttu-id="25b93-151">JSON serileştirme için özel dönüştürücüler yazma</span><span class="sxs-lookup"><span data-stu-id="25b93-151">Write custom converters for JSON serialization</span></span>](system-text-json-converters-how-to.md)
* [<span data-ttu-id="25b93-152">DateTime ve DateTimeOffset desteği</span><span class="sxs-lookup"><span data-stu-id="25b93-152">DateTime and DateTimeOffset support</span></span>](../datetime/system-text-json-support.md)
* <span data-ttu-id="25b93-153">[System.Text.Json API başvurusu](xref:System.Text.Json)</span><span class="sxs-lookup"><span data-stu-id="25b93-153">[System.Text.Json API reference](xref:System.Text.Json)</span></span>
* <span data-ttu-id="25b93-154">[System.Text.Json. Serileştirme API başvurusu](xref:System.Text.Json.Serialization)</span><span class="sxs-lookup"><span data-stu-id="25b93-154">[System.Text.Json.Serialization API reference](xref:System.Text.Json.Serialization)</span></span>
