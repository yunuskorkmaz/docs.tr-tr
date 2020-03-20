---
title: 'Azaltma: Özel IMessageFilter.PreFilterMessage Uygulamaları'
ms.date: 03/30/2017
ms.assetid: 9cf47c5b-0bb2-45df-9437-61cd7e7c2f4d
ms.openlocfilehash: 7757e8d1fd0258ab2d972b7321082e4afa37f710
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "79400122"
---
# <a name="mitigation-custom-imessagefilterprefiltermessage-implementations"></a>Azaltma: Özel IMessageFilter.PreFilterMessage Uygulamaları

.NET Framework 4.6.1 ile başlayan .NET Framework sürümlerini hedefleyen Windows <xref:System.Windows.Forms.IMessageFilter.PreFilterMessage%2A?displayProperty=nameWithType> Forms uygulamalarında, <xref:System.Windows.Forms.Application.FilterMessage%2A?displayProperty=nameWithType> <xref:System.Windows.Forms.IMessageFilter.PreFilterMessage%2A?displayProperty=nameWithType> uygulama çağrıldığında özel bir uygulama iletileri güvenli bir şekilde filtreleyebilir:

- Aşağıdakilerden biri veya her ikisi de:

  - <xref:System.Windows.Forms.Application.AddMessageFilter%2A> Yöntemi arayarak bir ileti filtresi ekler.

  - Yöntemi çağırarak ileti filtresini <xref:System.Windows.Forms.Application.RemoveMessageFilter%2A> kaldırır. Yöntem.

- **Ve** <xref:System.Windows.Forms.Application.DoEvents%2A?displayProperty=nameWithType> yöntemi arayarak mesajları pompalar.

## <a name="impact"></a>Etki

Bu değişiklik yalnızca .NET Framework 4.6.1 ile başlayan .NET Framework sürümlerini hedefleyen Windows Forms uygulamalarını etkiler.

.NET Framework'ün önceki sürümlerini hedefleyen Windows Forms uygulamaları için, <xref:System.IndexOutOfRangeException> yöntem <xref:System.Windows.Forms.Application.FilterMessage%2A?displayProperty=nameWithType> çağrıldığında bazı durumlarda bu tür uygulamalar bir özel durum oluşturur

## <a name="mitigation"></a>Risk azaltma

Bu değişiklik istenmiyorsa, .NET Framework 4.6.1 veya daha sonraki bir sürümü hedefleyen uygulamalar, [ \<](../configure-apps/file-schema/runtime/runtime-element.md) uygulamanın yapılandırma dosyasının çalışma zamanı>bölümüne aşağıdaki yapılandırma ayarını ekleyerek bu uygulamadan vazgeçebilir:

```xml
<runtime>
    <AppContextSwitchOverrides value="Switch.System.Windows.Forms.DontSupportReentrantFilterMessage=true" />
</runtime>
```

Buna ek olarak, .NET Framework'ün önceki sürümlerini hedefleyen ancak .NET Framework 4.6.1 veya daha sonraki bir sürüm [ \<](../configure-apps/file-schema/runtime/runtime-element.md) altında çalışan uygulamalar, uygulamanın yapılandırma dosyasının çalışma süresi>bölümüne aşağıdaki yapılandırma ayarını ekleyerek bu davranışı seçebilir:

```xml
<runtime>
    <AppContextSwitchOverrides value="Switch.System.Windows.Forms.DontSupportReentrantFilterMessage=false" />
</runtime>
```

## <a name="see-also"></a>Ayrıca bkz.

- [Uygulama uyumluluğu](application-compatibility.md)
