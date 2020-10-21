---
ms.openlocfilehash: 0dfe04ba1313480f15a8e7a7e26da613799180b2
ms.sourcegitcommit: dfcbc096ad7908cd58a5f0aeabd2256f05266bac
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/21/2020
ms.locfileid: "92332893"
---
### <a name="aspnet-core-apps-allow-deserializing-quoted-numbers"></a>ASP.NET Core uygulamalar, tırnak işaretli sayıların serisini kaldırmada izin veriyor

.NET 5,0 ' den başlayarak ASP.NET Core uygulamalar, tarafından belirtilen varsayılan seri kaldırma seçeneklerini kullanır <xref:System.Text.Json.JsonSerializerDefaults.Web?displayProperty=nameWithType> . <xref:System.Text.Json.JsonSerializerDefaults.Web>Seçenek kümesi, ayarı içerir <xref:System.Text.Json.JsonSerializerOptions.NumberHandling> <xref:System.Text.Json.Serialization.JsonNumberHandling.AllowReadingFromString?displayProperty=nameWithType> . Bu değişiklik, ASP.NET Core uygulamaların özel durum oluşturmak yerine JSON dizeleri olarak temsil edilen sayıları başarıyla seri durumdan çıkaracağı anlamına gelir.

#### <a name="change-description"></a>Açıklamayı Değiştir

.NET Core 3,0-3,1 ' de, <xref:System.Text.Json.JsonSerializer> <xref:System.Text.Json.JsonException> JSON yükünde tırnak içine alınmış bir sayıyla karşılaştığında seri kaldırma sırasında bir oluşturur. Tırnak işaretleri nesne grafiklerde sayı özellikleriyle eşleştirmek için kullanılır. .NET Core 3,0-3,1 ' de rakamlar yalnızca <xref:System.Text.Json.JsonTokenType.Number?displayProperty=nameWithType> belirteçlerden okunurdur.

.NET 5,0 ' den başlayarak, JSON yüklere ilişkin tırnak işaretli sayılar, ASP.NET Core uygulamalar için varsayılan olarak geçerli kabul edilir. Tırnak işaretli sayıların serisini kaldırma sırasında hiçbir özel durum oluşturulmaz.

> [!TIP]
>
> - Varsayılan, tek başına veya için davranış değişikliği yoktur <xref:System.Text.Json.JsonSerializer> <xref:System.Text.Json.JsonSerializerOptions> .
> - Bu, teknik olarak önemli bir değişiklik değildir, çünkü bir senaryoyu daha kısıtlayıcı hale getirir (yani, bir özel durum oluşturmak yerine bir JSON dizesinden zorlama bir sayı içinde başarılı olur). Ancak, bu pek çok ASP.NET Core uygulamayı etkileyen önemli bir davranış değişikliği olduğundan, burada belgelenmiştir.
> - <xref:System.Net.Http.Json.HttpClientJsonExtensions.GetFromJsonAsync%2A>Ve <xref:System.Net.Http.Json.HttpContentJsonExtensions.ReadFromJsonAsync%2A> genişletme yöntemleri, <xref:System.Text.Json.JsonSerializerDefaults.Web> serileştirme seçenekleri kümesini de kullanır.

#### <a name="version-introduced"></a>Sunulan sürüm

5.0

#### <a name="reason-for-change"></a>Değişiklik nedeni

Birden çok Kullanıcı, içinde daha fazla izin veren numara işleme için bir seçenek istedi <xref:System.Text.Json.JsonSerializer> . Bu geri bildirim, çok sayıda JSON üreticileri (örneğin, web genelindeki hizmetler) tırnak işaretleri halinde yaydığını gösterir. Alıntılanmış sayıların okunmasına (serisi kaldırılan) izin vererek, .NET uygulamaları varsayılan olarak bu yükleri Web bağlamlarına başarıyla ayrıştırabilirler. Yapılandırma, <xref:System.Text.Json.JsonSerializerDefaults.Web?displayProperty=nameWithType> farklı uygulama katmanlarında aynı seçenekleri (örneğin, istemci, sunucu ve paylaşılan) belirleyebilmeniz için aracılığıyla sunulur.

#### <a name="recommended-action"></a>Önerilen eylem

Bu değişiklik kesintiye uğradıysanız, örneğin, doğrulama için katı sayı işleme bağımlıysa, önceki davranışı yeniden etkinleştirebilirsiniz. <xref:System.Text.Json.JsonSerializerOptions.NumberHandling?displayProperty=nameWithType>Seçeneğini olarak ayarlayın <xref:System.Text.Json.Serialization.JsonNumberHandling.Strict?displayProperty=nameWithType> .

ASP.NET Core MVC ve Web API uygulamaları için, aşağıdaki kodu kullanarak seçeneğini ' de yapılandırabilirsiniz `Startup` :

```csharp
services.AddControllers()
   .AddJsonOptions(options.NumberHandling = JsonNumberHandling.Strict);
```

#### <a name="category"></a>Kategori

- ASP.NET Core
- Serileştirme

#### <a name="affected-apis"></a>Etkilenen API’ler

- <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=fullName>
- <xref:System.Text.Json.JsonSerializer.DeserializeAsync%2A?displayProperty=fullName>

<!--

#### Affected APIs

- `Overload:System.Text.Json.JsonSerializer.Deserialize`
- `Overload:System.Text.Json.JsonSerializer.DeserializeAsync`

-->
