---
title: İle JsonSerializerOptions örneği System.Text.Json
description: Performans sorunlarından kaçının ve JsonSerializerOptions örnekleri için kullanılabilir oluşturucuların nasıl kullanılacağını öğrenin.
ms.date: 12/02/2020
no-loc:
- System.Text.Json
- Newtonsoft.Json
zone_pivot_groups: dotnet-version
helpviewer_keywords:
- JSON serialization
- serializing objects
- serialization
- objects, serializing
ms.openlocfilehash: 257c99e117dea9a9b3ab2352c9a442d71a2cdabd
ms.sourcegitcommit: 0014aa4d5cb2da56a70e03fc68f663d64df5247a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/09/2020
ms.locfileid: "96918560"
---
# <a name="how-to-instantiate-jsonserializeroptions-instances-with-no-locsystemtextjson"></a>İle JsonSerializerOptions örneklerinin örneğini oluşturma System.Text.Json

Bu makalede, kullanırken performans sorunlarının nasıl önleneceği açıklanmaktadır <xref:System.Text.Json.JsonSerializerOptions> . Ayrıca, kullanılabilir parametreli oluşturucuların nasıl kullanılacağını gösterir.

## <a name="reuse-jsonserializeroptions-instances"></a>JsonSerializerOptions örneklerini yeniden kullanma

`JsonSerializerOptions`Aynı seçeneklerle tekrar tekrar kullanırsanız, `JsonSerializerOptions` her kullandığınızda yeni bir örnek oluşturmayın. Her çağrı için aynı örneği yeniden kullanın. Bu kılavuz, özel dönüştürücüler için yazdığınız koda ve veya ' i çağırdığınızda geçerlidir <xref:System.Text.Json.JsonSerializer.Serialize%2A?displayProperty=nameWithType> <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType> .

Aşağıdaki kod, yeni seçenek örneklerinin kullanımı için performans cezaını gösterir.

:::code language="csharp" source="snippets/system-text-json-configure-options/csharp/ReuseOptionsInstances.cs":::

Yukarıdaki kod, aynı seçenek örneğini kullanarak küçük bir nesne 100.000 kez seri hale getirir. Daha sonra aynı nesneyi aynı sayıda seri hale getirir ve her seferinde yeni bir seçenek örneği oluşturur. Tipik bir çalıştırma süresi farkı, 40.140 milisaniyeye kıyasla 190 ' dir. Yineleme sayısını arttırmanız halinde fark daha büyük olur.

Seri hale getirici, yeni bir seçenek örneği geçirildiğinde nesne grafiğindeki her bir türün ilk serileştirilmesi sırasında bir ısınma aşamasına geçer. Bu ısınma, serileştirme için gereken meta verilerin bir önbelleğinin oluşturulmasını içerir. Meta veriler, özellik Getters, ayarlayıcıları, Oluşturucu bağımsız değişkenleri, belirtilen öznitelikler ve benzeri temsilciler içerir. Bu meta veri önbelleği seçenekler örneğinde depolanır. Aynı ısınma işlemi ve önbellek seri durumundan çıkarma için geçerlidir.

Bir örnekteki meta veri önbelleğinin boyutu, `JsonSerializerOptions` seri hale getirilecek türlerin sayısına bağlıdır. Seri hale getirici için çok sayıda tür geçirirseniz — Örneğin, dinamik olarak üretilen türler —, önbellek boyutu büyümeye devam eder ve bir soruna neden olabilir `OutOfMemoryException` .

## <a name="copy-jsonserializeroptions"></a>JsonSerializerOptions 'ı Kopyala

::: zone pivot="dotnet-5-0"
[JsonSerializerOptions Oluşturucusu] (XREF:) var System.Text.Json . JsonSerializerOptions .% 23ctor ( System.Text.Json . JsonSerializerOptions)), aşağıdaki örnekte gösterildiği gibi, var olan örnekle aynı seçeneklere sahip yeni bir örnek oluşturmanıza olanak sağlar:

:::code language="csharp" source="snippets/system-text-json-how-to-5-0/csharp/CopyOptions.cs" highlight="29":::
::: zone-end

::: zone pivot="dotnet-core-3-1"
`JsonSerializerOptions`Mevcut bir örneği alan bir Oluşturucu .NET Core 3,1 ' de kullanılamaz.
::: zone-end

## <a name="web-defaults-for-jsonserializeroptions"></a>JsonSerializerOptions için Web Varsayılanları

::: zone pivot="dotnet-5-0"
Web uygulamaları için farklı varsayılan değerlere sahip olan seçenekler şunlardır:

* <xref:System.Text.Json.JsonSerializerOptions.PropertyNameCaseInsensitive%2A> = `true`
* <xref:System.Text.Json.JsonNamingPolicy> = <xref:System.Text.Json.JsonNamingPolicy.CamelCase>
* <xref:System.Text.Json.JsonSerializerOptions.NumberHandling%2A> = <xref:System.Text.Json.Serialization.JsonNumberHandling.AllowReadingFromString>

[JsonSerializerOptions Oluşturucusu] (XREF:) var System.Text.Json . JsonSerializerOptions .% 23ctor ( System.Text.Json . JsonSerializerDefaults)? View = net-5,0&Preserve-View = true), aşağıdaki örnekte gösterildiği gibi, ASP.NET Core Web Apps için kullandığı varsayılan seçeneklerle yeni bir örnek oluşturmanıza olanak sağlar:

:::code language="csharp" source="snippets/system-text-json-how-to-5-0/csharp/OptionsDefaults.cs" highlight="24":::
::: zone-end

::: zone pivot="dotnet-core-3-1"
Web uygulamaları için farklı varsayılan değerlere sahip olan seçenekler şunlardır:

* <xref:System.Text.Json.JsonSerializerOptions.PropertyNameCaseInsensitive%2A> = `true`
* <xref:System.Text.Json.JsonNamingPolicy> = <xref:System.Text.Json.JsonNamingPolicy.CamelCase>

`JsonSerializerOptions`Varsayılan kümesini belirten bir Oluşturucu .NET Core 3,1 ' de kullanılamaz.
::: zone-end

## <a name="see-also"></a>Ayrıca bkz.

* [System.Text.Json bakýþ](system-text-json-overview.md)
* [Büyük/küçük harf duyarlı eşlemeyi etkinleştirme](system-text-json-character-casing.md)
* [Özellik adlarını ve değerlerini özelleştirme](system-text-json-customize-properties.md)
* [Özellikleri yoksayma](system-text-json-ignore-properties.md)
* [Geçersiz JSON’a izin verme](system-text-json-invalid-json.md)
* [Sap taşması JSON’ı](system-text-json-handle-overflow.md)
* [Döngüsel başvuruları koru](system-text-json-preserve-references.md)
* [Sabit türler ve genel olmayan erişimciler](system-text-json-immutability.md)
* [Polimorfik serileştirme](system-text-json-polymorphism.md)
* [System.Text.Json API başvurusu](xref:System.Text.Json)
