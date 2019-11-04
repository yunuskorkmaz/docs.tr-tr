---
title: 'Risk azaltma: özel IMessageFilter. PreFilterMessage uygulamaları'
ms.date: 03/30/2017
ms.assetid: 9cf47c5b-0bb2-45df-9437-61cd7e7c2f4d
ms.openlocfilehash: 7757e8d1fd0258ab2d972b7321082e4afa37f710
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73457934"
---
# <a name="mitigation-custom-imessagefilterprefiltermessage-implementations"></a>Risk azaltma: özel IMessageFilter. PreFilterMessage uygulamaları

.NET Framework 4.6.1 ile başlayan .NET Framework sürümlerini hedefleyen Windows Forms uygulamalarda, <xref:System.Windows.Forms.Application.FilterMessage%2A?displayProperty=nameWithType> yöntemi çağrıldığında bir özel <xref:System.Windows.Forms.IMessageFilter.PreFilterMessage%2A?displayProperty=nameWithType> uygulaması iletileri güvenli bir şekilde filtreleyebilir:

- Aşağıdakilerden birini veya her ikisini de yapar:

  - <xref:System.Windows.Forms.Application.AddMessageFilter%2A> yöntemini çağırarak bir ileti filtresi ekler.

  - <xref:System.Windows.Forms.Application.RemoveMessageFilter%2A> yöntemini çağırarak bir ileti filtresini kaldırır. yöntemidir.

- **Ve** <xref:System.Windows.Forms.Application.DoEvents%2A?displayProperty=nameWithType> yöntemini çağırarak pompalara iletileri.

## <a name="impact"></a>Etki

Bu değişiklik yalnızca .NET Framework 4.6.1 başlayarak .NET Framework sürümlerini hedefleyen Windows Forms uygulamalarını etkiler.

.NET Framework önceki sürümlerini hedefleyen Windows Forms uygulamalar için, bazı durumlarda bu tür uygulamalar <xref:System.Windows.Forms.Application.FilterMessage%2A?displayProperty=nameWithType> yöntemi çağrıldığında <xref:System.IndexOutOfRangeException> özel durumu oluşturur

## <a name="mitigation"></a>Azaltma

Bu değişiklik istenmeyen ise, .NET Framework 4.6.1 veya sonraki bir sürümü hedefleyen uygulamalar, uygulamanın yapılandırma dosyasının [\<runtime >](../configure-apps/file-schema/runtime/runtime-element.md) bölümüne aşağıdaki yapılandırma ayarını ekleyerek devre dışı bırakabilirsiniz:

```xml
<runtime>
    <AppContextSwitchOverrides value="Switch.System.Windows.Forms.DontSupportReentrantFilterMessage=true" />
</runtime>
```

Ayrıca, .NET Framework önceki sürümlerini hedefleyen, ancak .NET Framework 4.6.1 altında çalışan uygulamalar veya daha sonraki bir sürüm, aşağıdaki yapılandırma ayarını [\<çalışma zamanı >](../configure-apps/file-schema/runtime/runtime-element.md) bölümüne ekleyerek bu davranışı kabul edebilir. uygulamanın yapılandırma dosyası:

```xml
<runtime>
    <AppContextSwitchOverrides value="Switch.System.Windows.Forms.DontSupportReentrantFilterMessage=false" />
</runtime>
```

## <a name="see-also"></a>Ayrıca bkz.

- [Uygulama uyumluluğu](application-compatibility.md)
