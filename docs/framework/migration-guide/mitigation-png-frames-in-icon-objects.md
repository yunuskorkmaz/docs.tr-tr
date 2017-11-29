---
title: "Azaltma: PNG çerçeveleri simgesi nesneleri"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ca87fefb-7144-4b4e-8832-5a939adbb4b2
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: dbc81484f55cabbdc86e7ba57e68f9e1c96a567f
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="mitigation-png-frames-in-icon-objects"></a>Azaltma: PNG çerçeveleri simgesi nesneleri
.NET Framework 4.6 ile başlayan <xref:System.Drawing.Icon.ToBitmap%2A?displayProperty=nameWithType> yöntemi başarıyla PNG çerçevelerine simgelerle dönüştürür <xref:System.Drawing.Bitmap> nesneleri.  
  
 Hedef .NET Framework 4.5.2 ve önceki sürümleri, uygulamalarda <xref:System.Drawing.Icon.ToBitmap%2A?displayProperty=nameWithType> yöntemi atar bir <xref:System.ArgumentOutOfRangeException> özel durumu ise <xref:System.Drawing.Icon> nesnesi PNG çerçeveler sahiptir.  
  
## <a name="impact"></a>Etki  
 Bu değişiklik, .NET Framework 4.6 hedeflemek için derlenir ve özel işleme için uygulamanıza uygulamaları etkiler <xref:System.ArgumentOutOfRangeException> , oluşur ne zaman bir <xref:System.Drawing.Icon> nesnesi PNG çerçeveler sahiptir. .NET Framework 4.6 altında çalışırken, dönüştürme başarılı bir <xref:System.ArgumentOutOfRangeException> Hayır artık oluşturulur ve bu nedenle özel durum işleyici artık çağrılır.  
  
### <a name="mitigation"></a>Azaltma  
 Bu davranış istenmeyen ise, aşağıdaki öğeyi ekleyerek önceki davranış tutabilirsiniz [ \<çalışma zamanı >](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) app.config dosyasının:  
  
```xml  
<AppContextSwitchOverrides   
      value="Switch.System.Drawing.DontSupportPngFramesInIcons=true" />  
```  
  
 App.config dosyasını zaten varsa `AppContextSwitchOverrides` öğesi, yeni değer birleştirilmiş ile `value` özniteliği şuna benzer:  
  
```xml  
<AppContextSwitchOverrides   
      value="Switch.System.Drawing.DontSupportPngFramesInIcons=true;<previous key>=<previous value>" />  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Yeniden hedefleme değişiklikleri](../../../docs/framework/migration-guide/retargeting-changes-in-the-net-framework-4-6.md)
