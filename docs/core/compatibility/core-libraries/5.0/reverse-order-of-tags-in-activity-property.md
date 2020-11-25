---
title: 'Son değişiklik: etkinlik içindeki etiketlerin sırası. Etiketler tersine çevrilir'
description: .NET 5,0 önemli .NET kitaplıklarında etkinlik. Etiketler eklendiği sıraya göre öğeleri artık depolar.
ms.date: 11/01/2020
ms.openlocfilehash: 1ff14dc1a4f7a0bf8cf9e79f3750b819f4d4a5ca
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95761497"
---
# <a name="order-of-tags-in-activitytags-is-reversed"></a>Etkinlik içindeki etiketlerin sırası. Etiketler tersine çevrilir

<xref:System.Diagnostics.Activity.Tags?displayProperty=nameWithType> Artık öğeleri eklendiği sıraya göre listede depolar, diğer bir deyişle, eklenen ilk öğe listede ilk olarak listelenir. Bu değişiklik, [Opentelemetri öznitelikleri belirtimiyle](https://github.com/open-telemetry/opentelemetry-specification/blob/master/specification/common/common.md#attributes)eşleşecek şekilde yapılmıştır.

## <a name="change-description"></a>Açıklamayı Değiştir

Önceki .NET sürümlerinde, <xref:System.Diagnostics.Activity.Tags?displayProperty=nameWithType> öğeleri eklendikleri ters sırada depolar. Diğer bir deyişle, eklenen ilk öğe listenin en son öğesidir. .NET 5,0 ' den başlayarak, öğelerin sırası tersine çevrilir ve eklenen ilk öğe her zaman listede ilk olarak olur.

## <a name="version-introduced"></a>Sunulan sürüm

5.0

## <a name="recommended-action"></a>Önerilen eylem

Uygulamanızda <xref:System.Diagnostics.Activity.Tags?displayProperty=nameWithType> liste sırası bağımlılığı varsa ve .net 5,0 veya sonraki bir sürüme yükseltiyorsanız, kodunuzun bu bölümünü değiştirmeniz gerekir.

## <a name="affected-apis"></a>Etkilenen API’ler

- <xref:System.Diagnostics.Activity.Tags?displayProperty=fullName>

<!--

#### Category

Core .NET libraries

### Affected APIs

- `P:System.Diagnostics.Activity.Tags`

-->
