---
title: İle başvuruları koruma System.Text.Json
description: .NET 'teki JSON 'dan serileştirilirken ve seri durumdan çıkarılırken başvuruları nasıl koruyacağınızı ve döngüsel başvuruları nasıl işleyeceğinizi öğrenin.
ms.date: 01/12/2021
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
ms.openlocfilehash: 0dda695c7e21090f68703309da03d5158fc858f1
ms.sourcegitcommit: f0fc5db7bcbf212e46933e9cf2d555bb82666141
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/17/2021
ms.locfileid: "100584058"
---
# <a name="how-to-preserve-references-and-handle-circular-references-with-systemtextjson"></a>Başvuruları koruma ve ile döngüsel başvuruları işleme System.Text.Json

::: zone pivot="dotnet-5-0"

Başvuruları korumak ve döngüsel başvuruları işlemek için olarak ayarlayın <xref:System.Text.Json.JsonSerializerOptions.ReferenceHandler%2A> <xref:System.Text.Json.Serialization.ReferenceHandler.Preserve%2A> . Bu ayar aşağıdaki davranışa neden olur:

* Seri hale getirme:

  Karmaşık türler yazarken serileştirici Ayrıca meta veri özellikleri ( `$id` , `$values` ve `$ref` ) yazar.

* Seri durumdan çıkarma tarihi:

  Meta veriler beklenir (zorunlu olmasa da) ve seri hale getirici bunu anlamaya çalışır.

Aşağıdaki kod, ayarın kullanımını gösterir `Preserve` .

:::code language="csharp" source="snippets/system-text-json-how-to-5-0/csharp/PreserveReferences.cs" highlight="34":::
:::code language="vb" source="snippets/system-text-json-how-to-5-0/vb/PreserveReferences.vb" :::

Bu özellik değer türlerini veya sabit türleri korumak için kullanılamaz. Seri durumdan çıkarma sırasında, tüm yük okunduktan sonra sabit bir tür örneği oluşturulur. Bu nedenle, JSON yükünün içinde bir başvuru görünürse aynı örneğin serisini kaldırma imkansızdır.

Değer türleri, değişmez türler ve diziler için hiçbir başvuru meta verisi serileştirilmez. Seri durumdan çıkarma sırasında, veya bulunursa bir özel durum oluşturulur `$ref` `$id` . Ancak, `$id` `$values` kullanılarak seri hale getirilen yüklerin serisini kaldırma olanağı sağlamak için değer türleri (koleksiyonlar durumunda ve ' de) yoksayar Newtonsoft.Json .  Newtonsoft.Json Bu tür türler için meta verileri serileştirmez.

Nesnelerin eşit olup olmadığını anlamak için, System.Text.Json <xref:System.Collections.Generic.ReferenceEqualityComparer.Instance%2A?displayProperty=nameWithType> <xref:System.Object.ReferenceEquals(System.Object,System.Object)?displayProperty=nameWithType> değer eşitlik yerine başvuru eşitlik () kullanır ( <xref:System.Object.Equals(System.Object)?displayProperty=nameWithType> iki nesne örneği karşılaştırılırken).

Başvuruların serileştirilme ve seri durumdan çıkarıldığı hakkında daha fazla bilgi için bkz <xref:System.Text.Json.Serialization.ReferenceHandler.Preserve%2A?displayProperty=nameWithType> ..

<xref:System.Text.Json.Serialization.ReferenceResolver>Sınıfı serileştirme ve seri durumundan çıkarma için başvuruları koruma davranışını tanımlar. Özel davranışı belirtmek için türetilmiş bir sınıf oluşturun. Bir örnek için bkz. [GuidReferenceResolver](https://github.com/dotnet/docs/blob/9d5e88edbd7f12be463775ffebbf07ac8415fe18/docs/standard/serialization/snippets/system-text-json-how-to-5-0/csharp/GuidReferenceResolverExample.cs).

## <a name="persist-reference-metadata-across-multiple-serialization-and-deserialization-calls"></a>Birden çok serileştirme ve seri durumdan çıkarma çağrılarında başvuru meta verilerini kalıcı yap

Varsayılan olarak, başvuru verileri yalnızca veya için yapılan her çağrı için önbelleğe alınır <xref:System.Text.Json.JsonSerializer.Serialize%2A> <xref:System.Text.Json.JsonSerializer.Deserialize%2A> . Bir çağrıdan diğerine yapılan başvuruları kalıcı hale getirmek için `Serialize` / `Deserialize` , ' <xref:System.Text.Json.Serialization.ReferenceResolver> ın çağrı sitesinde kökünü yapın `Serialize` / `Deserialize` . Aşağıdaki kod, bu senaryo için bir örnek gösterir:

* Bir listeniz vardır `Employee` ve her birini ayrı olarak serileştirmek zorunda olursunuz.
* çözümleyicisine kaydedilen başvuruların avantajlarından yararlanmak istiyorsunuz `ReferenceHandler` .

`Employee`Sınıf şöyledir:

:::code language="csharp" source="snippets/system-text-json-how-to-5-0/csharp/PreserveReferencesMultipleCalls.cs" id="Employee":::

Öğesinden türetilen bir sınıf <xref:System.Text.Json.Serialization.ReferenceResolver> , başvuruları bir sözlükte depolar:

:::code language="csharp" source="snippets/system-text-json-how-to-5-0/csharp/PreserveReferencesMultipleCalls.cs" id="MyReferenceResolver":::

Öğesinden türetilen bir sınıf <xref:System.Text.Json.Serialization.ReferenceHandler> , bir örneğini tutar `MyReferenceResolver` ve yalnızca gerektiğinde yeni bir örnek oluşturur (Bu örnekte adlı bir yöntemde `Reset` ):

:::code language="csharp" source="snippets/system-text-json-how-to-5-0/csharp/PreserveReferencesMultipleCalls.cs" id="MyReferenceHandler":::

Örnek kod serileştiriciyi çağırdığında, <xref:System.Text.Json.JsonSerializerOptions> <xref:System.Text.Json.JsonSerializerOptions.ReferenceHandler> özelliğinin bir örneğine ayarlandığı bir örneği kullanır `MyReferenceHandler` . Bu kalıbı izlediğinizde, `ReferenceResolver` seri hale getirmeyi tamamladıktan sonra, sonsuza kadar büyümeye devam etmek için sözlüğü sıfırladığınızdan emin olun.

:::code language="csharp" source="snippets/system-text-json-how-to-5-0/csharp/PreserveReferencesMultipleCalls.cs" id="CallSerializer" highlight = "3-4,14":::

::: zone-end

::: zone pivot="dotnet-core-3-1"
System.Text.Json .NET Core 3,1 yalnızca değere göre serileştirme destekler ve döngüsel başvurular için bir özel durum oluşturur.
::: zone-end

## <a name="see-also"></a>Ayrıca bkz.

* [System.Text.Json bakýþ](system-text-json-overview.md)
* [JSON’u seri hale getirme ve seri halden çıkarma](system-text-json-how-to.md)
* [JsonSerializerOptions örneklerinin örneğini oluşturma](system-text-json-configure-options.md)
* [Büyük/küçük harf duyarlı eşlemeyi etkinleştirme](system-text-json-character-casing.md)
* [Özellik adlarını ve değerlerini özelleştirme](system-text-json-customize-properties.md)
* [Özellikleri yoksayma](system-text-json-ignore-properties.md)
* [Geçersiz JSON’a izin verme](system-text-json-invalid-json.md)
* [Sap taşması JSON’ı](system-text-json-handle-overflow.md)
* [Sabit türler ve genel olmayan erişimciler](system-text-json-immutability.md)
* [Polimorfik serileştirme](system-text-json-polymorphism.md)
* [' Den ' a geçiş Newtonsoft.JsonSystem.Text.Json](system-text-json-migrate-from-newtonsoft-how-to.md)
* [Karakter kodlamasını özelleştirme](system-text-json-character-encoding.md)
* [Özel serileştiriciler ve seri hale getiriciler yazma](write-custom-serializer-deserializer.md)
* [JSON serileştirme için özel dönüştürücüler yazma](system-text-json-converters-how-to.md)
* [DateTime ve DateTimeOffset desteği](../datetime/system-text-json-support.md)
* [System.Text.Json API başvurusu](xref:System.Text.Json)
* [System.Text.Json. Serileştirme API başvurusu](xref:System.Text.Json.Serialization)
