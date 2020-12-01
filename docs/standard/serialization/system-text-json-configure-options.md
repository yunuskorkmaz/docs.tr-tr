---
title: İle JsonSerializerOptions örneği System.Text.Json
description: Mevcut örnekleri veya Web varsayılanlarını kopyalayarak JsonSerializerOptions örneklerinin örneğini oluşturmayı öğrenin.
ms.date: 11/30/2020
no-loc:
- System.Text.Json
- Newtonsoft.Json
zone_pivot_groups: dotnet-version
helpviewer_keywords:
- JSON serialization
- serializing objects
- serialization
- objects, serializing
ms.openlocfilehash: 0febfe15f36856f10699fd327fb17c146277eb9b
ms.sourcegitcommit: 721c3e4bdbb1ea0bb420818ec944c538fe5c513a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/01/2020
ms.locfileid: "96440032"
---
# <a name="how-to-instantiate-jsonserializeroptions-instances-with-no-locsystemtextjson"></a>İle JsonSerializerOptions örneklerinin örneğini oluşturma System.Text.Json

Bu makalede, <xref:System.Text.Json.JsonSerializerOptions> mevcut örnekleri veya Web varsayılanlarını kopyalayarak örneklerin örneğini oluşturmayı öğreneceksiniz.

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
* [Büyük/küçük harfe duyarsız eşleştirmeyi etkinleştir](system-text-json-character-casing.md)
* [Özellik adlarını ve değerlerini özelleştirme](system-text-json-customize-properties.md)
* [Özellikleri yoksay](system-text-json-ignore-properties.md)
* [Geçersiz JSON 'a izin ver](system-text-json-invalid-json.md)
* [Tutamaç taşması JSON](system-text-json-handle-overflow.md)
* [Döngüsel başvuruları koru](system-text-json-preserve-references.md)
* [Değişmez türler ve genel olmayan erişimciler](system-text-json-immutability.md)
* [Polimorfik serileştirme](system-text-json-polymorphism.md)
* [System.Text.Json API başvurusu](xref:System.Text.Json)
