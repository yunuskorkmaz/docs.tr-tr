---
title: İle değişmez türleri ve genel olmayan erişimcileri kullanma System.Text.Json
description: .NET ' te JSON ile seri hale getirme ve serisini kaldırma sırasında değişmez türleri ve genel olmayan erişimcileri kullanmayı öğrenin.
ms.date: 02/08/2021
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
ms.openlocfilehash: 188ed6a5582f4677eb60963af72036963b5fe821
ms.sourcegitcommit: bdbf6472de867a0a11aaa5b9384a2506c24f27d2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102206680"
---
# <a name="how-to-use-immutable-types-and-non-public-accessors-with-systemtextjson"></a>İle değişmez türleri ve genel olmayan erişimcileri kullanma System.Text.Json

Bu makalede, ad alanıyla değişmez türlerin, genel parametreli oluşturucuların ve genel olmayan erişimcilerinin nasıl kullanılacağı gösterilmektedir `System.Text.Json` .

## <a name="immutable-types-and-records"></a>Sabit türler ve kayıtlar

::: zone pivot="dotnet-5-0"
`System.Text.Json` , sabit bir sınıfın veya yapının serisini kaldırmak mümkün kılan ortak parametreli bir Oluşturucu kullanabilir. Bir sınıf için, tek Oluşturucu parametreli bir ise, bu Oluşturucu kullanılacaktır. Bir yapı veya birden çok Oluşturucu içeren bir sınıf için, [[Jsonconstructor]](xref:System.Text.Json.Serialization.JsonConstructorAttribute) özniteliğini uygulayarak kullanılacak olanı belirtin. Özniteliği kullanılmazsa, varsa Ortak parametresiz bir Oluşturucu her zaman kullanılır. Özniteliği yalnızca ortak oluşturucularla birlikte kullanılabilir. Aşağıdaki örnek `[JsonConstructor]` özniteliğini kullanır:

:::code language="csharp" source="snippets/system-text-json-how-to-5-0/csharp/ImmutableTypes.cs" highlight="13":::
:::code language="vb" source="snippets/system-text-json-how-to-5-0/vb/ImmutableTypes.vb" :::

Parametreli bir oluşturucunun parametre adları, özellik adlarıyla eşleşmelidir. Eşleştirme büyük/küçük harfe duyarlıdır ve bir özelliği yeniden adlandırmak için [[Jsonpropertyname]](xref:System.Text.Json.Serialization.JsonPropertyNameAttribute) kullanıyor olsanız bile, Oluşturucu parametresi gerçek özellik adıyla eşleşmelidir. Aşağıdaki örnekte, `TemperatureC` özelliğinin adı `celsius` JSON içinde olarak değiştirilir, ancak Oluşturucu parametresi hala adlandırılmaktadır `temperatureC` :

:::code language="csharp" source="snippets/system-text-json-how-to-5-0/csharp/ImmutableTypesCtorParms.cs" highlight="10,14-16":::

`[JsonPropertyName]`Aşağıdaki özniteliklerin yanı sıra parametreli oluşturucularla serisini kaldırma desteği de vardır:

* [[JsonConverter]](xref:System.Text.Json.Serialization.JsonConverterAttribute)
* [[Jsonıgnore]](xref:System.Text.Json.Serialization.JsonIgnoreAttribute)
* [[Jsonınclude]](xref:System.Text.Json.Serialization.JsonIncludeAttribute)
* [[JsonNumberHandling]](xref:System.Text.Json.Serialization.JsonNumberHandlingAttribute)

C# 9 ' da kayıtlar aşağıdaki örnekte gösterildiği gibi desteklenir:

:::code language="csharp" source="snippets/system-text-json-how-to-5-0/csharp/Records.cs":::

Tüm özellik ayarlayıcıları ortak olmadığından, sabit olan türler için aşağıdaki bölüme bakın.
::: zone-end

::: zone pivot="dotnet-core-3-1"
`JsonConstructorAttribute` ve C# 9 kayıt desteği .NET Core 3,1 ' de kullanılamaz.
::: zone-end

## <a name="non-public-property-accessors"></a>Ortak olmayan özellik erişimcileri

::: zone pivot="dotnet-5-0"
Ortak olmayan bir özellik erişimcisinin kullanımını etkinleştirmek için, aşağıdaki örnekte gösterildiği gibi [[Jsonınclude]](xref:System.Text.Json.Serialization.JsonIncludeAttribute) özniteliğini kullanın:

:::code language="csharp" source="snippets/system-text-json-how-to-5-0/csharp/NonPublicAccessors.cs" highlight="12,15":::
:::code language="vb" source="snippets/system-text-json-how-to-5-0/vb/NonPublicAccessors.vb" :::
::: zone-end

::: zone pivot="dotnet-core-3-1"
Ortak olmayan özellik erişimcileri .NET Core 3,1 ' de desteklenmez. Daha fazla bilgi için, bkz. [ Newtonsoft.Json makaleden geçiş](system-text-json-migrate-from-newtonsoft-how-to.md#non-public-property-setters-and-getters).
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
* [Başvuruları koruma](system-text-json-preserve-references.md)
* [Polimorfik serileştirme](system-text-json-polymorphism.md)
* [' Den ' a geçiş Newtonsoft.JsonSystem.Text.Json](system-text-json-migrate-from-newtonsoft-how-to.md)
* [Karakter kodlamasını özelleştirme](system-text-json-character-encoding.md)
* [Özel serileştiriciler ve seri hale getiriciler yazma](write-custom-serializer-deserializer.md)
* [JSON serileştirme için özel dönüştürücüler yazma](system-text-json-converters-how-to.md)
* [DateTime ve DateTimeOffset desteği](../datetime/system-text-json-support.md)
* [System.Text.Json API başvurusu](xref:System.Text.Json)
* [System.Text.Json. Serileştirme API başvurusu](xref:System.Text.Json.Serialization)
