---
ms.openlocfilehash: 6f5c1ecead4e2f74e621354058aab70bfa1cccb6
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620567"
---
### <a name="eventlistener-truncates-strings-with-embedded-nulls"></a>EventListener, gömülü null değerleri olan dizeleri keser

#### <a name="details"></a>Ayrıntılar

<xref:System.Diagnostics.Tracing.EventListener?displayProperty=fullName>gömülü null değerleri olan dizeleri keser. Null karakterler sınıf tarafından desteklenmiyor <xref:System.Diagnostics.Tracing.EventSource?displayProperty=fullName> . Değişiklik yalnızca <xref:System.Diagnostics.Tracing.EventListener?displayProperty=fullName> işlemdeki verileri okumak için kullanılan uygulamaları etkiler <xref:System.Diagnostics.Tracing.EventSource?displayProperty=fullName> ve sınırlayıcı olarak null karakterler kullanır.

#### <a name="suggestion"></a>Öneri

<xref:System.Diagnostics.Tracing.EventSource?displayProperty=fullName>Mümkünse, gömülü null karakterleri kullanmamalıdır verilerin güncelleştirilmeleri gerekir.

| Name    | Değer       |
|:--------|:------------|
| Kapsam   |Edge|
|Sürüm|4.5.1|
|Tür|Çalışma Zamanı

#### <a name="affected-apis"></a>Etkilenen API’ler

-<xref:System.Diagnostics.Tracing.EventListener.%23ctor></li><li><xref:System.Diagnostics.Tracing.EventListener.EnableEvents(System.Diagnostics.Tracing.EventSource,System.Diagnostics.Tracing.EventLevel)?displayProperty=nameWithType></li><li><xref:System.Diagnostics.Tracing.EventListener.EnableEvents(System.Diagnostics.Tracing.EventSource,System.Diagnostics.Tracing.EventLevel,System.Diagnostics.Tracing.EventKeywords)?displayProperty=nameWithType></li><li><xref:System.Diagnostics.Tracing.EventListener.EnableEvents(System.Diagnostics.Tracing.EventSource,System.Diagnostics.Tracing.EventLevel,System.Diagnostics.Tracing.EventKeywords,System.Collections.Generic.IDictionary{System.String,System.String})?displayProperty=nameWithType></li></ul>|
