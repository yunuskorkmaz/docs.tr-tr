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
# <a name="how-to-customize-character-encoding-with-no-locsystemtextjson"></a>İle karakter kodlamasını özelleştirme System.Text.Json

Varsayılan olarak, seri hale getirici ASCII olmayan tüm karakterleri çıkar. Diğer bir deyişle, bu, `\uxxxx` karakterin Unicode kodunun bulunduğu konum ile değiştirilir `xxxx` . Örneğin, `Summary` AŞAĞıDAKI JSON 'daki Özellik Kiril olarak ayarlandıysa `жарко` , `WeatherForecast` nesne şu örnekte gösterildiği gibi serileştirilir:

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "\u0436\u0430\u0440\u043A\u043E"
}
```

## <a name="serialize-language-character-sets"></a>Dil karakter kümelerini serileştirme

Bir veya daha fazla dilin karakter kümesini kaçış olmadan seri hale getirmek için, aşağıdaki örnekte gösterildiği gibi bir örneği oluştururken [Unicode aralığı](xref:System.Text.Unicode.UnicodeRanges) belirtin <xref:System.Text.Encodings.Web.JavaScriptEncoder?displayProperty=fullName> :

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/SerializeCustomEncoding.cs" id="Usings":::

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/SerializeCustomEncoding.cs" id="LanguageSets":::

Bu kod, Kiril veya Yunan karakterlerinden kaçış yapmaz. `Summary`Özellik Kiril olarak ayarlandıysa `жарко` , `WeatherForecast` nesne şu örnekte gösterildiği gibi serileştirilir:

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "жарко"
}
```

Kodlayıcı, varsayılan olarak <xref:System.Text.Unicode.UnicodeRanges.BasicLatin> aralığıyla başlatılır.

Tüm dil kümelerini kaçış olmadan seri hale getirmek için kullanın <xref:System.Text.Unicode.UnicodeRanges.All?displayProperty=nameWithType> .

## <a name="serialize-specific-characters"></a>Belirli karakterleri serileştirme

Diğer bir seçenek de, kaçırılmadan, izin vermek istediğiniz tek tek karakterleri belirtmektir. Aşağıdaki örnek, öğesinin yalnızca ilk iki karakterini seri hale getirir `жарко` :

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/SerializeCustomEncoding.cs" id="Usings":::

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/SerializeCustomEncoding.cs" id="SelectedCharacters":::

Yukarıdaki kod tarafından üretilen JSON örneği aşağıda verilmiştir:

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "жа\u0440\u043A\u043E"
}
```

## <a name="block-lists"></a>Engelleme listeleri

Yukarıdaki bölümlerde, çıkış yapmak istemediğiniz kod noktalarının veya aralıklarının izin verilenler listelerinin nasıl belirtildiği gösterilmektedir. Ancak, izin verilenler listenizde belirli kod noktalarını geçersiz kılabilen genel ve kodlayıcılara özgü blok listeleri vardır. Bir blok listesindeki kod noktaları, izin verilenler listenize dahil edilse de her zaman kaçışlar.

### <a name="global-block-list"></a>Genel engellenenler listesi

Genel engellenenler listesi, özel kullanım karakterleri, denetim karakterleri, tanımsız kod noktaları ve [Space_Separator kategorisi](https://util.unicode.org/UnicodeJsps/list-unicodeset.jsp?a=%5B:General_Category=Space_Separator:%5D)gibi bazı Unicode kategorilerini içerir `U+0020 SPACE` . Örneğin, `U+3000 IDEOGRAPHIC SPACE` izin verilenler listeniz olarak @ [sembolleri ve noktalama Işaretlerini (U +3000-U + 303f)](xref:System.Text.Unicode.UnicodeRanges.CjkSymbolsandPunctuation) belirtseniz bile kaçış olur.

Genel engelleme listesi, .NET Core ve .NET 5 ' in her sürümünde değişen bir uygulama ayrıntıdır. Genel engelleme listesinin üyesi olan (veya üyesi olmayan) bir karakter üzerinde bağımlılık yapmayın.

### <a name="encoder-specific-block-lists"></a>Kodlayıcıya özgü blok listeleri

Kodlayıcılara özgü engellenen kod noktaları örnekleri `'<'` `'&'` , [HTML Kodlayıcısı](xref:System.Text.Encodings.Web.HtmlEncoder), `'\'` [JSON Kodlayıcısı](xref:System.Text.Encodings.Web.JavaScriptEncoder)ve `'%'` [URL Kodlayıcısı](xref:System.Text.Encodings.Web.UrlEncoder)için içerir. Örneğin, HTML Kodlayıcısı her zaman `'&'` ampersan () den çıkar, ancak `BasicLatin` ve tüm kodlayıcılar `BasicLatin` Varsayılan olarak ile başlatılır.

## <a name="serialize-all-characters"></a>Tüm karakterleri seri hale getirme

<xref:System.Text.Encodings.Web.JavaScriptEncoder.UnsafeRelaxedJsonEscaping?displayProperty=nameWithType>Aşağıdaki örnekte gösterildiği gibi, kullanarak kaçı en aza indirin:

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/SerializeCustomEncoding.cs" id="Usings":::

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/SerializeCustomEncoding.cs" id="UnsafeRelaxed":::

> [!CAUTION]
> Varsayılan kodlayıcıyla karşılaştırıldığında kodlayıcı, `UnsafeRelaxedJsonEscaping` karakterlerin kaçışsız geçmesine izin verme konusunda daha fazla izne sahiptir:
>
> * ,, Ve gibi HTML 'ye duyarlı karakterleri atmaz `<` `>` `&` `'` .
> * Bu, XSS veya bilgi açıklama saldırılarına karşı ek derinlemesine savunma korumaları sunmaz, örneğin, *karakter* kümesinde istemci ve sunucu disagreeing neden olabilir.
>
> Güvenli olmayan kodlayıcıyı yalnızca istemcinin, elde edilen yükü UTF-8 ile kodlanmış JSON olarak yorumladığı bilindiğinde kullanın. Örneğin, sunucu yanıt üst bilgisini gönderiyorsa onu kullanabilirsiniz `Content-Type: application/json; charset=utf-8` . Ham `UnsafeRelaxedJsonEscaping` çıkışın BIR HTML sayfasına veya bir öğeye yayılmasın `<script>` .

## <a name="see-also"></a>Ayrıca bkz.

* [System.Text.Json bakýþ](system-text-json-overview.md)
* [JSON’u seri hale getirme ve seri halden çıkarma](system-text-json-how-to.md)
* [JsonSerializerOptions örneklerinin örneğini oluşturma](system-text-json-configure-options.md)
* [Büyük/küçük harf duyarlı eşlemeyi etkinleştirme](system-text-json-character-casing.md)
* [Özellik adlarını ve değerlerini özelleştirme](system-text-json-customize-properties.md)
* [Özellikleri yoksayma](system-text-json-ignore-properties.md)
* [Geçersiz JSON’a izin verme](system-text-json-invalid-json.md)
* [Sap taşması JSON’ı](system-text-json-handle-overflow.md)
* [Başvuruları koruma](system-text-json-preserve-references.md)
* [Sabit türler ve genel olmayan erişimciler](system-text-json-immutability.md)
* [Polimorfik serileştirme](system-text-json-polymorphism.md)
* [' Den ' a geçiş Newtonsoft.JsonSystem.Text.Json](system-text-json-migrate-from-newtonsoft-how-to.md)
* [Özel serileştiriciler ve seri hale getiriciler yazma](write-custom-serializer-deserializer.md)
* [JSON serileştirme için özel dönüştürücüler yazma](system-text-json-converters-how-to.md)
* [DateTime ve DateTimeOffset desteği](../datetime/system-text-json-support.md)
* [System.Text.Json API başvurusu](xref:System.Text.Json)
* [System.Text.Json. Serileştirme API başvurusu](xref:System.Text.Json.Serialization)
