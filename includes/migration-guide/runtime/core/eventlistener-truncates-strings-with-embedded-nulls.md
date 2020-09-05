---
ms.openlocfilehash: e47a24239872e3fe86ff6902f66b38daaa106598
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89497564"
---
### <a name="eventlistener-truncates-strings-with-embedded-nulls"></a>EventListener, gömülü null değerleri olan dizeleri keser

#### <a name="details"></a>Ayrıntılar

<xref:System.Diagnostics.Tracing.EventListener?displayProperty=fullName> gömülü null değerleri olan dizeleri keser. Null karakterler sınıf tarafından desteklenmiyor <xref:System.Diagnostics.Tracing.EventSource?displayProperty=fullName> . Değişiklik yalnızca <xref:System.Diagnostics.Tracing.EventListener?displayProperty=fullName> işlemdeki verileri okumak için kullanılan uygulamaları etkiler <xref:System.Diagnostics.Tracing.EventSource?displayProperty=fullName> ve sınırlayıcı olarak null karakterler kullanır.

#### <a name="suggestion"></a>Öneri

<xref:System.Diagnostics.Tracing.EventSource?displayProperty=fullName> Mümkünse, gömülü null karakterleri kullanmamalıdır verilerin güncelleştirilmeleri gerekir.

| Name    | Değer       |
|:--------|:------------|
| Kapsam   |Edge|
|Sürüm|4.5.1|
|Tür|Çalışma Zamanı|

#### <a name="affected-apis"></a>Etkilenen API’ler

- <xref:System.Diagnostics.Tracing.EventListener.%23ctor>
- <xref:System.Diagnostics.Tracing.EventListener.EnableEvents(System.Diagnostics.Tracing.EventSource,System.Diagnostics.Tracing.EventLevel)?displayProperty=nameWithType>
- <xref:System.Diagnostics.Tracing.EventListener.EnableEvents(System.Diagnostics.Tracing.EventSource,System.Diagnostics.Tracing.EventLevel,System.Diagnostics.Tracing.EventKeywords)?displayProperty=nameWithType>
- <xref:System.Diagnostics.Tracing.EventListener.EnableEvents(System.Diagnostics.Tracing.EventSource,System.Diagnostics.Tracing.EventLevel,System.Diagnostics.Tracing.EventKeywords,System.Collections.Generic.IDictionary{System.String,System.String})?displayProperty=nameWithType>

<!--

#### Affected APIs

- `M:System.Diagnostics.Tracing.EventListener.#ctor`
- `M:System.Diagnostics.Tracing.EventListener.EnableEvents(System.Diagnostics.Tracing.EventSource,System.Diagnostics.Tracing.EventLevel)`
- `M:System.Diagnostics.Tracing.EventListener.EnableEvents(System.Diagnostics.Tracing.EventSource,System.Diagnostics.Tracing.EventLevel,System.Diagnostics.Tracing.EventKeywords)`
- `M:System.Diagnostics.Tracing.EventListener.EnableEvents(System.Diagnostics.Tracing.EventSource,System.Diagnostics.Tracing.EventLevel,System.Diagnostics.Tracing.EventKeywords,System.Collections.Generic.IDictionary{System.String,System.String})`

-->
