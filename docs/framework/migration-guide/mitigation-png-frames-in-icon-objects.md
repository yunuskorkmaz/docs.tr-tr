---
title: 'Risk azaltma: simge nesnelerinde PNG çerçeveleri'
ms.date: 03/30/2017
ms.assetid: ca87fefb-7144-4b4e-8832-5a939adbb4b2
ms.openlocfilehash: 1a4ae0c069a4cd6d53bce77e64822ebf3fbb5361
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73457876"
---
# <a name="mitigation-png-frames-in-icon-objects"></a>Risk azaltma: simge nesnelerinde PNG çerçeveleri
.NET Framework 4,6 ' den başlayarak <xref:System.Drawing.Icon.ToBitmap%2A?displayProperty=nameWithType> yöntemi, simgeleri PNG çerçevelerinden <xref:System.Drawing.Bitmap> nesnelerine başarıyla dönüştürür.  
  
 .NET Framework 4.5.2 ve önceki sürümlerini hedefleyen uygulamalarda, <xref:System.Drawing.Icon> nesnesi PNG çerçevelerdeyse <xref:System.Drawing.Icon.ToBitmap%2A?displayProperty=nameWithType> yöntemi bir <xref:System.ArgumentOutOfRangeException> özel durumu oluşturur.  
  
## <a name="impact"></a>Etki  
 Bu değişiklik, .NET Framework 4,6 ' i hedefleyecek ve bir <xref:System.Drawing.Icon> nesnesi PNG çerçevelerindeyken oluşturulan <xref:System.ArgumentOutOfRangeException> için özel işleme uygulayan uygulamaları etkiler. .NET Framework 4,6 altında çalışırken, dönüştürme başarılı olur, bir <xref:System.ArgumentOutOfRangeException> artık oluşturulmaz ve bu nedenle özel durum işleyicisi artık çağrılmayacaktır.  
  
### <a name="mitigation"></a>Azaltma  
 Bu davranış istenmez ise, App. config dosyanızın [\<runtime >](../configure-apps/file-schema/runtime/runtime-element.md) bölümüne aşağıdaki öğeyi ekleyerek önceki davranışı koruyabilirsiniz:  
  
```xml  
<AppContextSwitchOverrides   
      value="Switch.System.Drawing.DontSupportPngFramesInIcons=true" />  
```  
  
 App. config dosyası `AppContextSwitchOverrides` öğesini zaten içeriyorsa, yeni değer aşağıdaki gibi `value` özniteliğiyle birleştirilmelidir:  
  
```xml  
<AppContextSwitchOverrides   
      value="Switch.System.Drawing.DontSupportPngFramesInIcons=true;<previous key>=<previous value>" />  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Uygulama uyumluluğu](application-compatibility.md)
