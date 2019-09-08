---
title: Mayı Özel IMessageFilter. PreFilterMessage uygulamaları
ms.date: 03/30/2017
ms.assetid: 9cf47c5b-0bb2-45df-9437-61cd7e7c2f4d
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2af81468c5c4c4caf2f09725d6c7c4723084e35c
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70779437"
---
# <a name="mitigation-custom-imessagefilterprefiltermessage-implementations"></a>Mayı Özel IMessageFilter. PreFilterMessage uygulamaları

.NET Framework 4.6.1 başlayarak .NET Framework sürümlerini hedefleyen Windows Forms uygulamalarda, <xref:System.Windows.Forms.IMessageFilter.PreFilterMessage%2A?displayProperty=nameWithType> <xref:System.Windows.Forms.IMessageFilter.PreFilterMessage%2A?displayProperty=nameWithType> uygulama şu şekilde çağrıldığında özel bir uygulama iletileri <xref:System.Windows.Forms.Application.FilterMessage%2A?displayProperty=nameWithType> güvenli bir şekilde filtreleyebilir:

- Aşağıdakilerden birini veya her ikisini de yapar:

  - <xref:System.Windows.Forms.Application.AddMessageFilter%2A> Yöntemini çağırarak bir ileti filtresi ekler.

  - <xref:System.Windows.Forms.Application.RemoveMessageFilter%2A> Yöntemini çağırarak bir ileti filtresini kaldırır. yöntemidir.

- **Ve** <xref:System.Windows.Forms.Application.DoEvents%2A?displayProperty=nameWithType> yöntemini çağırarak pompalara iletileri.

## <a name="impact"></a>Etki

Bu değişiklik yalnızca .NET Framework 4.6.1 başlayarak .NET Framework sürümlerini hedefleyen Windows Forms uygulamalarını etkiler.

.NET Framework önceki sürümlerini hedefleyen Windows Forms uygulamalar için, bazı durumlarda bu gibi uygulamalar, <xref:System.IndexOutOfRangeException> <xref:System.Windows.Forms.Application.FilterMessage%2A?displayProperty=nameWithType> yöntemi çağrıldığında bir özel durum oluşturur

## <a name="mitigation"></a>Azaltma

Bu değişiklik istenmeyen ise, .NET Framework 4.6.1 veya sonraki bir sürümü hedefleyen uygulamalar, uygulamanın yapılandırma dosyasının [ \<çalışma zamanı >](../configure-apps/file-schema/runtime/runtime-element.md) bölümüne aşağıdaki yapılandırma ayarını ekleyerek devre dışı bırakabilirsiniz:

```xml
<runtime>
    <AppContextSwitchOverrides value="Switch.System.Windows.Forms.DontSupportReentrantFilterMessage=true" />
</runtime>
```

Ayrıca, .NET Framework önceki sürümlerini hedefleyen, ancak .NET Framework 4.6.1 altında çalışan uygulamalar veya sonraki bir sürüm, aşağıdaki yapılandırma ayarını [ \<çalışma zamanı >](../configure-apps/file-schema/runtime/runtime-element.md) bölümüne ekleyerek bu davranışı kabul edebilir. uygulamanın yapılandırma dosyası:

```xml
<runtime>
    <AppContextSwitchOverrides value="Switch.System.Windows.Forms.DontSupportReentrantFilterMessage=false" />
</runtime>
```

## <a name="see-also"></a>Ayrıca bkz.

- [Yeniden Hedefleme Değişiklikleri](retargeting-changes-in-the-net-framework-4-6-1.md)
