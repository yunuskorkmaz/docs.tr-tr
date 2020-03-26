---
title: 'Azaltma: Simge Nesnelerde PNG Çerçeveler'
ms.date: 03/30/2017
ms.assetid: ca87fefb-7144-4b4e-8832-5a939adbb4b2
ms.openlocfilehash: 713e6a0fa615ac748134fac501e5142a65e434f1
ms.sourcegitcommit: 99b153b93bf94d0fecf7c7bcecb58ac424dfa47c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2020
ms.locfileid: "80248901"
---
# <a name="mitigation-png-frames-in-icon-objects"></a>Azaltma: Simge Nesnelerde PNG Çerçeveler
.NET Framework 4.6 ile <xref:System.Drawing.Icon.ToBitmap%2A?displayProperty=nameWithType> başlayarak, yöntem PNG çerçeveli simgeleri başarıyla nesnelere <xref:System.Drawing.Bitmap> dönüştürür.  
  
 .NET Framework 4.5.2 ve önceki sürümleri hedefleyen <xref:System.Drawing.Icon.ToBitmap%2A?displayProperty=nameWithType> uygulamalarda, <xref:System.ArgumentOutOfRangeException> nesnepng <xref:System.Drawing.Icon> çerçeveleri varsa yöntem bir özel durum atar.  
  
## <a name="impact"></a>Etki  
 Bu değişiklik, .NET Framework 4.6'yı hedeflemek için yeniden derlenen <xref:System.ArgumentOutOfRangeException> ve bir <xref:System.Drawing.Icon> nesnePNG çerçevesi olduğunda atılanlar için özel işleme uygulayan uygulamaları etkiler. .NET Framework 4.6 altında çalışırken, dönüştürme başarılı <xref:System.ArgumentOutOfRangeException> olur, artık bir atılmıştır ve bu nedenle özel durum işleyicisi artık çağrılmaz.  
  
### <a name="mitigation"></a>Risk azaltma  
 Bu davranış istenmiyorsa, app.config dosyanızın [ \<çalışma zamanı>](../configure-apps/file-schema/runtime/runtime-element.md) bölümüne aşağıdaki öğeyi ekleyerek önceki davranışı koruyabilirsiniz:  
  
```xml  
<AppContextSwitchOverrides
      value="Switch.System.Drawing.DontSupportPngFramesInIcons=true" />  
```  
  
 app.config dosyası zaten öğeyi içeriyorsa, `AppContextSwitchOverrides` yeni değer `value` aşağıdaki gibi öznitelik ile birleştirilmelidir:  
  
```xml  
<AppContextSwitchOverrides
      value="Switch.System.Drawing.DontSupportPngFramesInIcons=true;previous key=previous-value" />
```
  
## <a name="see-also"></a>Ayrıca bkz.

- [Uygulama uyumluluğu](application-compatibility.md)
