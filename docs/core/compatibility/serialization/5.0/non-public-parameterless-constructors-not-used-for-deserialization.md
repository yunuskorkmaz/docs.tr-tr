---
title: 'Son değişiklik: genel olmayan, parametresiz oluşturucular seri durumundan çıkarma için kullanılmaz'
description: .NET 5 ' teki, genel olmayan ve parametresiz oluşturucuların artık JsonSerializer ile serisini kaldırma için kullanılmayan Son değişiklik hakkında bilgi edinin.
ms.date: 10/18/2020
ms.openlocfilehash: 9781061fa89eb3bffb53a4f08bacbd88f3bc9265
ms.sourcegitcommit: 9c589b25b005b9a7f87327646020eb85c3b6306f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2021
ms.locfileid: "102256276"
---
# <a name="non-public-parameterless-constructors-not-used-for-deserialization"></a>Seri durumdan çıkarma için ortak olmayan, parametresiz oluşturucular kullanılmıyor

Tüm desteklenen hedef çerçeve adları (TFMs) genelinde tutarlılık için, genel olmayan ve parametresiz oluşturucular, varsayılan olarak ile seri durumdan çıkarma için artık kullanılmamaktadır <xref:System.Text.Json.JsonSerializer> .

## <a name="change-description"></a>Açıklamayı Değiştir

.NET Standard 2,0 ve üstünü destekleyen [ NuGet paketlerindeki](https://www.nuget.org/packages/System.Text.Json/) tek başınaSystem.Text.Js, yani 4.6.0-4.7.2 sürümleri, .net Core 3,0 ve 3,1 yerleşik davranışıyla tutarsız şekilde davranır. .NET Core 3. x, iç ve özel oluşturucular seri durumundan çıkarma için kullanılabilir. Tek başına paketlerde ortak olmayan oluşturuculara izin verilmez ve <xref:System.MissingMethodException> Public, parametresiz Oluşturucu tanımlanmadığında oluşturulur.

.NET 5 ve ' den itibaren, NuGet paketi 5.0.0 üzerinde System.Text.Js, bu davranış NuGet paketi ve yerleşik API 'Ler arasında tutarlıdır. Parametresiz oluşturucular da dahil olmak üzere genel olmayan oluşturucular varsayılan olarak serileştirici tarafından yok sayılır. Serileştirici, seri durumdan çıkarmak için aşağıdaki oluşturuculardan birini kullanır:

- Ortak Oluşturucu ile açıklama eklenir <xref:System.Text.Json.Serialization.JsonConstructorAttribute> .
- Ortak parametresiz Oluşturucu.
- Ortak parametreli Oluşturucu (tek ortak Oluşturucu varsa).

Bu oluşturuculardan hiçbiri kullanılabilir değilse, <xref:System.NotSupportedException> türün serisini kaldırma girişiminde bulunursa bir oluşturulur.

## <a name="version-introduced"></a>Sunulan sürüm

5.0

## <a name="reason-for-change"></a>Değişiklik nedeni

- <xref:System.Text.Json?displayProperty=fullName>(.NET Core 3,0 ve üzeri sürümleri ve .NET Standard 2,0) için derleme yapan tüm hedef çerçeve adları (TFMs) arasında tutarlı davranışı zorlamak için
- Çünkü bir <xref:System.Text.Json.JsonSerializer> türün bir Oluşturucu, özellik veya alan gibi genel olmayan yüzey alanını çağırmamalıdır.

## <a name="recommended-action"></a>Önerilen eylem

- Türü sahibiyseniz ve mümkünse, parametresiz oluşturucuyu herkese açık hale getirin.
- Aksi takdirde, <xref:System.Text.Json.Serialization.JsonConverter%601> türü için bir uygulayın ve serisini kaldırma davranışını denetleyin. <xref:System.Text.Json.Serialization.JsonConverter%601>Söz konusu senaryoya yönelik C# erişilebilirlik kuralları buna izin verirseniz, bir uygulamadan ortak olmayan bir Oluşturucu çağırabilirsiniz.

## <a name="affected-apis"></a>Etkilenen API’ler

- <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=fullName>
- <xref:System.Text.Json.JsonSerializer.DeserializeAsync%2A?displayProperty=fullName>

<!--

### Affected APIs

- `Overload:System.Text.Json.JsonSerializer.Deserialize`
- `Overload:System.Text.Json.JsonSerializer.DeserializeAsync`

### Category

Serialization

-->
