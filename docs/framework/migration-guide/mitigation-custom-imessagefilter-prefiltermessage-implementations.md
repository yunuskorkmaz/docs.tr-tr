---
title: 'Risk azaltma: özel IMessageFilter. PreFilterMessage uygulamaları'
description: .NET Framework 4.6.1 ve üstünü hedefleyen Windows Forms uygulamalara eklenen özel IMessageFilter. PreFilterMessage uygulaması hakkında bilgi edinin.
ms.date: 03/30/2017
ms.assetid: 9cf47c5b-0bb2-45df-9437-61cd7e7c2f4d
ms.openlocfilehash: 5fe7500d3ed6ff293514495df150a747e7946dda
ms.sourcegitcommit: cf5a800a33de64d0aad6d115ffcc935f32375164
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/20/2020
ms.locfileid: "86475261"
---
# <a name="mitigation-custom-imessagefilterprefiltermessage-implementations"></a>Risk azaltma: özel IMessageFilter. PreFilterMessage uygulamaları

.NET Framework 4.6.1 başlayarak .NET Framework sürümlerini hedefleyen Windows Forms uygulamalarda, <xref:System.Windows.Forms.IMessageFilter.PreFilterMessage%2A?displayProperty=nameWithType> uygulama şu şekilde çağrıldığında özel bir uygulama iletileri güvenli bir şekilde filtreleyebilir <xref:System.Windows.Forms.Application.FilterMessage%2A?displayProperty=nameWithType> <xref:System.Windows.Forms.IMessageFilter.PreFilterMessage%2A?displayProperty=nameWithType> :

- Aşağıdakilerden birini veya her ikisini de yapar:

  - Yöntemini çağırarak bir ileti filtresi ekler <xref:System.Windows.Forms.Application.AddMessageFilter%2A> .

  - Yöntemini çağırarak bir ileti filtresini kaldırır <xref:System.Windows.Forms.Application.RemoveMessageFilter%2A> . yöntemidir.

- **Ve** yöntemini çağırarak pompalara iletileri <xref:System.Windows.Forms.Application.DoEvents%2A?displayProperty=nameWithType> .

## <a name="impact"></a>Etki

Bu değişiklik yalnızca .NET Framework 4.6.1 başlayarak .NET Framework sürümlerini hedefleyen Windows Forms uygulamalarını etkiler.

.NET Framework önceki sürümlerini hedefleyen Windows Forms uygulamalar için, bazı durumlarda bu gibi uygulamalar <xref:System.IndexOutOfRangeException> , <xref:System.Windows.Forms.Application.FilterMessage%2A?displayProperty=nameWithType> yöntemi çağrıldığında bir özel durum oluşturur

## <a name="mitigation"></a>Risk azaltma

Bu değişiklik isten, .NET Framework 4.6.1 veya sonraki bir sürümü hedefleyen uygulamalar, [\<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) uygulamanın yapılandırma dosyasının bölümüne aşağıdaki yapılandırma ayarını ekleyerek devre dışı bırakabilirsiniz:

```xml
<runtime>
    <AppContextSwitchOverrides value="Switch.System.Windows.Forms.DontSupportReentrantFilterMessage=true" />
</runtime>
```

Ayrıca, .NET Framework önceki sürümlerini hedefleyen ancak .NET Framework 4.6.1 altında çalışan uygulamalar veya sonraki bir sürüm, [\<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) uygulamanın yapılandırma dosyasının bölümüne aşağıdaki yapılandırma ayarını ekleyerek bu davranışı kabul edebilir:

```xml
<runtime>
    <AppContextSwitchOverrides value="Switch.System.Windows.Forms.DontSupportReentrantFilterMessage=false" />
</runtime>
```

## <a name="see-also"></a>Ayrıca bkz.

- [Uygulama uyumluluğu](application-compatibility.md)
