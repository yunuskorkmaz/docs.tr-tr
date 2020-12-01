---
title: İle karakter kodlamasını özelleştirme System.Text.Json
description: .NET 'teki JSON 'a serileştirirken ve seri durumdan çıkarılırken karakter kodlamasını özelleştirmeyi öğrenin.
ms.date: 11/30/2020
no-loc:
- System.Text.Json
- Newtonsoft.Json
helpviewer_keywords:
- JSON serialization
- serializing objects
- serialization
- objects, serializing
ms.openlocfilehash: f6a50a3ca2a5e871294cf7c056cbf197a61cd668
ms.sourcegitcommit: 721c3e4bdbb1ea0bb420818ec944c538fe5c513a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/01/2020
ms.locfileid: "96440027"
---
# <a name="how-to-customize-character-encoding-with-no-locsystemtextjson"></a><span data-ttu-id="58507-103">İle karakter kodlamasını özelleştirme System.Text.Json</span><span class="sxs-lookup"><span data-stu-id="58507-103">How to customize character encoding with System.Text.Json</span></span>

<span data-ttu-id="58507-104">Varsayılan olarak, seri hale getirici ASCII olmayan tüm karakterleri çıkar.</span><span class="sxs-lookup"><span data-stu-id="58507-104">By default, the serializer escapes all non-ASCII characters.</span></span> <span data-ttu-id="58507-105">Diğer bir deyişle, bu, `\uxxxx` karakterin Unicode kodunun bulunduğu konum ile değiştirilir `xxxx` .</span><span class="sxs-lookup"><span data-stu-id="58507-105">That is, it replaces them with `\uxxxx` where `xxxx` is the Unicode code of the character.</span></span> <span data-ttu-id="58507-106">Örneğin, `Summary` AŞAĞıDAKI JSON 'daki Özellik Kiril olarak ayarlandıysa `жарко` , `WeatherForecast` nesne şu örnekte gösterildiği gibi serileştirilir:</span><span class="sxs-lookup"><span data-stu-id="58507-106">For example, if the `Summary` property in the following JSON is set to Cyrillic `жарко`, the `WeatherForecast` object is serialized as shown in this example:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "\u0436\u0430\u0440\u043A\u043E"
}
```

## <a name="serialize-language-character-sets"></a><span data-ttu-id="58507-107">Dil karakter kümelerini serileştirme</span><span class="sxs-lookup"><span data-stu-id="58507-107">Serialize language character sets</span></span>

<span data-ttu-id="58507-108">Bir veya daha fazla dilin karakter kümesini kaçış olmadan seri hale getirmek için, aşağıdaki örnekte gösterildiği gibi bir örneği oluştururken [Unicode aralığı](xref:System.Text.Unicode.UnicodeRanges) belirtin <xref:System.Text.Encodings.Web.JavaScriptEncoder?displayProperty=fullName> :</span><span class="sxs-lookup"><span data-stu-id="58507-108">To serialize the character set(s) of one or more languages without escaping, specify [Unicode range(s)](xref:System.Text.Unicode.UnicodeRanges) when creating an instance of <xref:System.Text.Encodings.Web.JavaScriptEncoder?displayProperty=fullName>, as shown in the following example:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/SerializeCustomEncoding.cs" id="Usings":::

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/SerializeCustomEncoding.cs" id="LanguageSets":::

<span data-ttu-id="58507-109">Bu kod, Kiril veya Yunan karakterlerinden kaçış yapmaz.</span><span class="sxs-lookup"><span data-stu-id="58507-109">This code doesn't escape Cyrillic or Greek characters.</span></span> <span data-ttu-id="58507-110">`Summary`Özellik Kiril olarak ayarlandıysa `жарко` , `WeatherForecast` nesne şu örnekte gösterildiği gibi serileştirilir:</span><span class="sxs-lookup"><span data-stu-id="58507-110">If the `Summary` property is set to Cyrillic `жарко`, the `WeatherForecast` object is serialized as shown in this example:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "жарко"
}
```

<span data-ttu-id="58507-111">Tüm dil kümelerini kaçış olmadan seri hale getirmek için kullanın <xref:System.Text.Unicode.UnicodeRanges.All?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="58507-111">To serialize all language sets without escaping, use <xref:System.Text.Unicode.UnicodeRanges.All?displayProperty=nameWithType>.</span></span>

## <a name="serialize-specific-characters"></a><span data-ttu-id="58507-112">Belirli karakterleri serileştirme</span><span class="sxs-lookup"><span data-stu-id="58507-112">Serialize specific characters</span></span>

<span data-ttu-id="58507-113">Diğer bir seçenek de, kaçırılmadan, izin vermek istediğiniz tek tek karakterleri belirtmektir.</span><span class="sxs-lookup"><span data-stu-id="58507-113">An alternative is to specify individual characters that you want to allow through without being escaped.</span></span> <span data-ttu-id="58507-114">Aşağıdaki örnek, öğesinin yalnızca ilk iki karakterini seri hale getirir `жарко` :</span><span class="sxs-lookup"><span data-stu-id="58507-114">The following example serializes only the first two characters of `жарко`:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/SerializeCustomEncoding.cs" id="Usings":::

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/SerializeCustomEncoding.cs" id="SelectedCharacters":::

<span data-ttu-id="58507-115">Yukarıdaki kod tarafından üretilen JSON örneği aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="58507-115">Here's an example of JSON produced by the preceding code:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "жа\u0440\u043A\u043E"
}
```

## <a name="serialize-all-characters"></a><span data-ttu-id="58507-116">Tüm karakterleri seri hale getirme</span><span class="sxs-lookup"><span data-stu-id="58507-116">Serialize all characters</span></span>

<span data-ttu-id="58507-117"><xref:System.Text.Encodings.Web.JavaScriptEncoder.UnsafeRelaxedJsonEscaping?displayProperty=nameWithType>Aşağıdaki örnekte gösterildiği gibi, kullanarak kaçı en aza indirin:</span><span class="sxs-lookup"><span data-stu-id="58507-117">To minimize escaping you can use <xref:System.Text.Encodings.Web.JavaScriptEncoder.UnsafeRelaxedJsonEscaping?displayProperty=nameWithType>, as shown in the following example:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/SerializeCustomEncoding.cs" id="Usings":::

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/SerializeCustomEncoding.cs" id="UnsafeRelaxed":::

> [!CAUTION]
> <span data-ttu-id="58507-118">Varsayılan kodlayıcıyla karşılaştırıldığında kodlayıcı, `UnsafeRelaxedJsonEscaping` karakterlerin kaçışsız geçmesine izin verme konusunda daha fazla izne sahiptir:</span><span class="sxs-lookup"><span data-stu-id="58507-118">Compared to the default encoder, the `UnsafeRelaxedJsonEscaping` encoder is more permissive about allowing characters to pass through unescaped:</span></span>
>
> * <span data-ttu-id="58507-119">,, Ve gibi HTML 'ye duyarlı karakterleri atmaz `<` `>` `&` `'` .</span><span class="sxs-lookup"><span data-stu-id="58507-119">It doesn't escape HTML-sensitive characters such as `<`, `>`, `&`, and `'`.</span></span>
> * <span data-ttu-id="58507-120">Bu, XSS veya bilgi açıklama saldırılarına karşı ek derinlemesine savunma korumaları sunmaz, örneğin, *karakter* kümesinde istemci ve sunucu disagreeing neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="58507-120">It doesn't offer any additional defense-in-depth protections against XSS or information disclosure attacks, such as those which might result from the client and server disagreeing on the *charset*.</span></span>
>
> <span data-ttu-id="58507-121">Güvenli olmayan kodlayıcıyı yalnızca istemcinin, elde edilen yükü UTF-8 ile kodlanmış JSON olarak yorumladığı bilindiğinde kullanın.</span><span class="sxs-lookup"><span data-stu-id="58507-121">Use the unsafe encoder only when it's known that the client will be interpreting the resulting payload as UTF-8 encoded JSON.</span></span> <span data-ttu-id="58507-122">Örneğin, sunucu yanıt üst bilgisini gönderiyorsa onu kullanabilirsiniz `Content-Type: application/json; charset=utf-8` .</span><span class="sxs-lookup"><span data-stu-id="58507-122">For example, you can use it if the server is sending the response header `Content-Type: application/json; charset=utf-8`.</span></span> <span data-ttu-id="58507-123">Ham `UnsafeRelaxedJsonEscaping` çıkışın BIR HTML sayfasına veya bir öğeye yayılmasın `<script>` .</span><span class="sxs-lookup"><span data-stu-id="58507-123">Never allow the raw `UnsafeRelaxedJsonEscaping` output to be emitted into an HTML page or a `<script>` element.</span></span>

## <a name="see-also"></a><span data-ttu-id="58507-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="58507-124">See also</span></span>

* [<span data-ttu-id="58507-125">System.Text.Json bakýþ</span><span class="sxs-lookup"><span data-stu-id="58507-125">System.Text.Json overview</span></span>](system-text-json-overview.md)
* [<span data-ttu-id="58507-126">Özel serileştiriciler ve seri hale getiriciler yazma</span><span class="sxs-lookup"><span data-stu-id="58507-126">How to write custom serializers and deserializers</span></span>](write-custom-serializer-deserializer.md)
* [<span data-ttu-id="58507-127">JSON serileştirme için özel dönüştürücüler yazma</span><span class="sxs-lookup"><span data-stu-id="58507-127">How to write custom converters for JSON serialization</span></span>](system-text-json-converters-how-to.md)
* <span data-ttu-id="58507-128">[System.Text.Json API başvurusu](xref:System.Text.Json)</span><span class="sxs-lookup"><span data-stu-id="58507-128">[System.Text.Json API reference](xref:System.Text.Json)</span></span>
