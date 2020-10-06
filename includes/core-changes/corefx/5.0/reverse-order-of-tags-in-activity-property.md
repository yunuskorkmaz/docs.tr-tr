---
ms.openlocfilehash: 24b88b3ba1b6cfe9fb9fb1f6398a6daeb57596a9
ms.sourcegitcommit: a8a205034eeffc7c3e1bdd6f506a75b0f7099ebf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/06/2020
ms.locfileid: "91756122"
---
### <a name="order-of-tags-in-activitytags-is-reversed"></a>Etkinlik içindeki etiketlerin sırası. Etiketler tersine çevrilir

<xref:System.Diagnostics.Activity.Tags?displayProperty=nameWithType> Artık öğeleri eklendiği sıraya göre listede depolar, diğer bir deyişle, eklenen ilk öğe listede ilk olarak listelenir. Bu değişiklik, [Opentelemetri öznitelikleri belirtimiyle](https://github.com/open-telemetry/opentelemetry-specification/blob/master/specification/common/common.md#attributes)eşleşecek şekilde yapılmıştır.

#### <a name="change-description"></a>Açıklamayı Değiştir

Önceki .NET sürümlerinde, <xref:System.Diagnostics.Activity.Tags?displayProperty=nameWithType> öğeleri eklendikleri ters sırada depolar. Diğer bir deyişle, eklenen ilk öğe listenin en son öğesidir. .NET 5,0 ' den başlayarak, öğelerin sırası tersine çevrilir ve eklenen ilk öğe her zaman listede ilk olarak olur.

#### <a name="version-introduced"></a>Sunulan sürüm

5.0

#### <a name="recommended-action"></a>Önerilen eylem

Uygulamanızda <xref:System.Diagnostics.Activity.Tags?displayProperty=nameWithType> liste sırası bağımlılığı varsa ve .net 5,0 veya sonraki bir sürüme yükseltiyorsanız, kodunuzun bu bölümünü değiştirmeniz gerekir.

#### <a name="category"></a>Kategori

Core .NET kitaplıkları

#### <a name="affected-apis"></a>Etkilenen API’ler

- <xref:System.Diagnostics.Activity.Tags?displayProperty=fullName>

<!--

#### Affected APIs

- `P:System.Diagnostics.Activity.Tags`

-->
