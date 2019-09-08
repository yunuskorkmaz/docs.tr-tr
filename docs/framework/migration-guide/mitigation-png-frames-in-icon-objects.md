---
title: Mayı Simge nesnelerinde PNG çerçeveleri
ms.date: 03/30/2017
ms.assetid: ca87fefb-7144-4b4e-8832-5a939adbb4b2
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 85a76681cf6efd649fe366a68d956246334975fe
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70789980"
---
# <a name="mitigation-png-frames-in-icon-objects"></a>Mayı Simge nesnelerinde PNG çerçeveleri
<xref:System.Drawing.Icon.ToBitmap%2A?displayProperty=nameWithType> Yöntem, .NET Framework 4,6 ' den başlayarak png <xref:System.Drawing.Bitmap> çerçevelerinden simgeleri nesnelere başarıyla dönüştürür.  
  
 .NET Framework 4.5.2 ve önceki sürümlerini hedefleyen uygulamalarda, <xref:System.Drawing.Icon.ToBitmap%2A?displayProperty=nameWithType> <xref:System.Drawing.Icon> nesne png çerçevelerdeyse Yöntem bir <xref:System.ArgumentOutOfRangeException> özel durum oluşturur.  
  
## <a name="impact"></a>Etki  
 Bu değişiklik, .NET Framework 4,6 ' i hedefleyecek ve bir <xref:System.ArgumentOutOfRangeException> <xref:System.Drawing.Icon> nesne png çerçevelerindeyken oluşturulan için özel işleme uygulayan uygulamaları etkiler. .NET Framework 4,6 altında çalışırken, dönüştürme başarılı olur, <xref:System.ArgumentOutOfRangeException> artık oluşturulmaz ve bu nedenle özel durum işleyicisi artık çağrılmayacaktır.  
  
### <a name="mitigation"></a>Azaltma  
 Bu davranış istenmez ise, App. config dosyanızın [ \<Runtime >](../configure-apps/file-schema/runtime/runtime-element.md) bölümüne aşağıdaki öğeyi ekleyerek önceki davranışı koruyabilirsiniz:  
  
```xml  
<AppContextSwitchOverrides   
      value="Switch.System.Drawing.DontSupportPngFramesInIcons=true" />  
```  
  
 App. config dosyası zaten `AppContextSwitchOverrides` öğesini içeriyorsa, yeni değer aşağıdaki gibi `value` özniteliğiyle birleştirilmelidir:  
  
```xml  
<AppContextSwitchOverrides   
      value="Switch.System.Drawing.DontSupportPngFramesInIcons=true;<previous key>=<previous value>" />  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Yeniden Hedefleme Değişiklikleri](retargeting-changes-in-the-net-framework-4-6.md)
