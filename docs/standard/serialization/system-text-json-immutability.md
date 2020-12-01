---
title: İle değişmez türleri ve genel olmayan erişimcileri kullanma System.Text.Json
description: .NET ' te JSON ile seri hale getirme ve serisini kaldırma sırasında değişmez türleri ve genel olmayan erişimcileri kullanmayı öğrenin.
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
ms.openlocfilehash: d3e61d44ce22b7f50838b6d3ba9cf64004bd3725
ms.sourcegitcommit: 721c3e4bdbb1ea0bb420818ec944c538fe5c513a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/01/2020
ms.locfileid: "96440014"
---
# <a name="how-to-use-immutable-types-and-non-public-accessors-with-no-locsystemtextjson"></a>İle değişmez türleri ve genel olmayan erişimcileri kullanma System.Text.Json

Bu makalede, ad alanı ile kayıtlar gibi değişmez türlerin nasıl kullanılacağını öğreneceksiniz `System.Text.Json` .

## <a name="immutable-types-and-records"></a>Sabit türler ve kayıtlar

::: zone pivot="dotnet-5-0"
`System.Text.Json` , sabit bir sınıfın veya yapının serisini kaldırma olanağı sağlayan parametreli bir Oluşturucu kullanabilir. Bir sınıf için, tek Oluşturucu parametreli bir ise, bu Oluşturucu kullanılacaktır. Bir yapı veya birden çok Oluşturucu içeren bir sınıf için, [[Jsonconstructor]](xref:System.Text.Json.Serialization.JsonConstructorAttribute.%23ctor%2A) özniteliğini uygulayarak kullanılacak olanı belirtin. Özniteliği kullanılmazsa, varsa Ortak parametresiz bir Oluşturucu her zaman kullanılır. Özniteliği yalnızca ortak oluşturucularla birlikte kullanılabilir. Aşağıdaki örnek `[JsonConstructor]` özniteliğini kullanır:

:::code language="csharp" source="snippets/system-text-json-how-to-5-0/csharp/ImmutableTypes.cs" highlight="13":::

C# 9 ' da kayıtlar aşağıdaki örnekte gösterildiği gibi desteklenir:

:::code language="csharp" source="snippets/system-text-json-how-to-5-0/csharp/Records.cs":::

Tüm özellik ayarlayıcıları ortak olmadığından, sabit olan türler için, [genel olmayan özellik erişimcileri](#non-public-property-accessors)hakkında aşağıdaki bölüme bakın.
::: zone-end

::: zone pivot="dotnet-core-3-1"
`JsonConstructorAttribute` ve C# 9 kayıt desteği .NET Core 3,1 ' de kullanılamaz.
::: zone-end

## <a name="non-public-property-accessors"></a>Ortak olmayan özellik erişimcileri

::: zone pivot="dotnet-5-0"
Ortak olmayan bir özellik erişimcisinin kullanımını etkinleştirmek için, aşağıdaki örnekte gösterildiği gibi [[Jsonınclude]](xref:System.Text.Json.Serialization.JsonIncludeAttribute) özniteliğini kullanın:

:::code language="csharp" source="snippets/system-text-json-how-to-5-0/csharp/NonPublicAccessors.cs" highlight="12,15":::
::: zone-end

::: zone pivot="dotnet-core-3-1"
Ortak olmayan özellik erişimcileri .NET Core 3,1 ' de desteklenmez. Daha fazla bilgi için, bkz. [ Newtonsoft.Json makaleden geçiş](system-text-json-migrate-from-newtonsoft-how-to.md#non-public-property-setters-and-getters).
::: zone-end

## <a name="see-also"></a>Ayrıca bkz.

* [System.Text.Json bakýþ](system-text-json-overview.md)
* [JsonSerializerOptions örneğini oluşturma](system-text-json-configure-options.md)
* [Büyük/küçük harfe duyarsız eşleştirmeyi etkinleştir](system-text-json-character-casing.md)
* [Özellik adlarını ve değerlerini özelleştirme](system-text-json-customize-properties.md)
* [Özellikleri yoksay](system-text-json-ignore-properties.md)
* [Geçersiz JSON 'a izin ver](system-text-json-invalid-json.md)
* [Tutamaç taşması JSON](system-text-json-handle-overflow.md)
* [Döngüsel başvuruları koru](system-text-json-preserve-references.md)
* [Polimorfik serileştirme](system-text-json-polymorphism.md)
* [System.Text.Json API başvurusu](xref:System.Text.Json)
