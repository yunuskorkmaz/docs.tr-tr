---
title: 'Risk azaltma: simge nesnelerinde PNG çerçeveleri'
description: .NET Framework 4,6 ve üzeri sürümlerde bulunan yeni davranış istenmeyen bir durum değilse, simge nesnelerinde PNG çerçevelerinin davranışını nasıl yapılandıracağınızı öğrenin.
ms.date: 03/30/2017
ms.assetid: ca87fefb-7144-4b4e-8832-5a939adbb4b2
ms.openlocfilehash: a8bb4fca19a09f16c89ce8c5da08ebcae9a037ec
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96276587"
---
# <a name="mitigation-png-frames-in-icon-objects"></a>Risk azaltma: simge nesnelerinde PNG çerçeveleri

Yöntem, .NET Framework 4,6 ' den başlayarak <xref:System.Drawing.Icon.ToBitmap%2A?displayProperty=nameWithType> PNG çerçevelerinden simgeleri nesnelere başarıyla dönüştürür <xref:System.Drawing.Bitmap> .  
  
 .NET Framework 4.5.2 ve önceki sürümlerini hedefleyen uygulamalarda, <xref:System.Drawing.Icon.ToBitmap%2A?displayProperty=nameWithType> <xref:System.ArgumentOutOfRangeException> <xref:System.Drawing.Icon> nesne png çerçevelerdeyse Yöntem bir özel durum oluşturur.  
  
## <a name="impact"></a>Etki  

 Bu değişiklik, .NET Framework 4,6 ' i hedefleyecek ve <xref:System.ArgumentOutOfRangeException> bir <xref:System.Drawing.Icon> nesne png çerçevelerindeyken oluşturulan için özel işleme uygulayan uygulamaları etkiler. .NET Framework 4,6 altında çalışırken, dönüştürme başarılı olur, <xref:System.ArgumentOutOfRangeException> artık oluşturulmaz ve bu nedenle özel durum işleyicisi artık çağrılmayacaktır.  
  
### <a name="mitigation"></a>Risk azaltma  

 Bu davranış istenmez ise, app.config dosyanızın bölümüne aşağıdaki öğeyi ekleyerek önceki davranışı koruyabilirsiniz [\<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) :  
  
```xml  
<AppContextSwitchOverrides
      value="Switch.System.Drawing.DontSupportPngFramesInIcons=true" />  
```  
  
 app.config dosyası öğesi zaten içeriyorsa `AppContextSwitchOverrides` , yeni değer aşağıdaki `value` gibi özniteliğiyle birleştirilmelidir:  
  
```xml  
<AppContextSwitchOverrides
      value="Switch.System.Drawing.DontSupportPngFramesInIcons=true;previous key=previous-value" />
```
  
## <a name="see-also"></a>Ayrıca bkz.

- [Uygulama uyumluluğu](application-compatibility.md)
