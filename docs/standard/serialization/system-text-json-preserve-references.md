---
title: İle başvuruları koruma System.Text.Json
description: .NET 'teki JSON 'dan serileştirilirken ve seri durumdan çıkarılırken başvuruları nasıl koruyacağınızı ve döngüsel başvuruları nasıl işleyeceğinizi öğrenin.
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
ms.openlocfilehash: 9254ca261c7d748c04c311fa56359014f752ff31
ms.sourcegitcommit: 721c3e4bdbb1ea0bb420818ec944c538fe5c513a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/01/2020
ms.locfileid: "96440016"
---
# <a name="how-to-handle-circular-references-with-no-locsystemtextjson"></a>İle döngüsel başvuruları işleme System.Text.Json

Bu makalede, ad alanıyla döngüsel başvuruları nasıl işleyeceğinizi öğreneceksiniz `System.Text.Json` .

## <a name="preserve-references-and-handle-circular-references"></a>Başvuruları koru ve döngüsel başvuruları işle

::: zone pivot="dotnet-5-0"

Başvuruları korumak ve döngüsel başvuruları işlemek için olarak ayarlayın <xref:System.Text.Json.JsonSerializerOptions.ReferenceHandler%2A> <xref:System.Text.Json.Serialization.ReferenceHandler.Preserve%2A> . Bu ayar aşağıdaki davranışa neden olur:

* Seri hale getirme:

  Karmaşık türler yazarken serileştirici Ayrıca meta veri özellikleri ( `$id` , `$values` ve `$ref` ) yazar.

* Seri durumdan çıkarma tarihi:

  Meta veriler beklenir (zorunlu olmasa da) ve seri hale getirici bunu anlamaya çalışır.

Aşağıdaki kod, ayarın kullanımını gösterir `Preserve` .

:::code language="csharp" source="snippets/system-text-json-how-to-5-0/csharp/PreserveReferences.cs" highlight="34":::

Bu özellik değer türlerini veya sabit türleri korumak için kullanılamaz. Seri durumdan çıkarma sırasında, tüm yük okunduktan sonra sabit bir tür örneği oluşturulur. Bu nedenle, JSON yükünün içinde bir başvuru görünürse aynı örneğin serisini kaldırma imkansızdır.

Değer türleri, değişmez türler ve diziler için hiçbir başvuru meta verisi serileştirilmez. Seri durumdan çıkarma sırasında, veya bulunursa bir özel durum oluşturulur `$ref` `$id` . Ancak, `$id` `$values` kullanılarak seri hale getirilen yüklerin serisini kaldırma olanağı sağlamak için değer türleri (koleksiyonlar durumunda ve ' de) yoksayar Newtonsoft.Json .  Newtonsoft.Json Bu tür türler için meta verileri serileştirmez.

Nesnelerin eşit olup olmadığını anlamak için, System.Text.Json <xref:System.Collections.Generic.ReferenceEqualityComparer.Instance%2A?displayProperty=nameWithType> <xref:System.Object.ReferenceEquals(System.Object,System.Object)?displayProperty=nameWithType> değer eşitlik yerine başvuru eşitlik () kullanır ( <xref:System.Object.Equals(System.Object)?displayProperty=nameWithType> iki nesne örneği karşılaştırılırken).

Başvuruların serileştirilme ve seri durumdan çıkarıldığı hakkında daha fazla bilgi için bkz <xref:System.Text.Json.Serialization.ReferenceHandler.Preserve%2A?displayProperty=nameWithType> ..

<xref:System.Text.Json.Serialization.ReferenceResolver>Sınıfı serileştirme ve seri durumundan çıkarma için başvuruları koruma davranışını tanımlar. Özel davranışı belirtmek için türetilmiş bir sınıf oluşturun. Bir örnek için bkz. [GuidReferenceResolver](https://github.com/dotnet/docs/blob/9d5e88edbd7f12be463775ffebbf07ac8415fe18/docs/standard/serialization/snippets/system-text-json-how-to-5-0/csharp/GuidReferenceResolverExample.cs).

::: zone-end

::: zone pivot="dotnet-core-3-1"
System.Text.Json .NET Core 3,1 yalnızca değere göre serileştirme destekler ve döngüsel başvurular için bir özel durum oluşturur.
::: zone-end

## <a name="see-also"></a>Ayrıca bkz.

* [System.Text.Json bakýþ](system-text-json-overview.md)
* [JsonSerializerOptions örneğini oluşturma](system-text-json-configure-options.md)
* [Büyük/küçük harfe duyarsız eşleştirmeyi etkinleştir](system-text-json-character-casing.md)
* [Özellik adlarını ve değerlerini özelleştirme](system-text-json-customize-properties.md)
* [Özellikleri yoksay](system-text-json-ignore-properties.md)
* [Geçersiz JSON 'a izin ver](system-text-json-invalid-json.md)
* [Tutamaç taşması JSON](system-text-json-handle-overflow.md)
* [Değişmez türler ve genel olmayan erişimciler](system-text-json-immutability.md)
* [Polimorfik serileştirme](system-text-json-polymorphism.md)
* [System.Text.Json API başvurusu](xref:System.Text.Json)
