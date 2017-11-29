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
# <a name="mitigation-png-frames-in-icon-objects"></a><span data-ttu-id="267b8-102">Azaltma: PNG çerçeveleri simgesi nesneleri</span><span class="sxs-lookup"><span data-stu-id="267b8-102">Mitigation: PNG Frames in Icon Objects</span></span>
<span data-ttu-id="267b8-103">.NET Framework 4.6 ile başlayan <xref:System.Drawing.Icon.ToBitmap%2A?displayProperty=nameWithType> yöntemi başarıyla PNG çerçevelerine simgelerle dönüştürür <xref:System.Drawing.Bitmap> nesneleri.</span><span class="sxs-lookup"><span data-stu-id="267b8-103">Starting with the .NET Framework 4.6, the <xref:System.Drawing.Icon.ToBitmap%2A?displayProperty=nameWithType> method successfully converts icons with PNG frames into <xref:System.Drawing.Bitmap> objects.</span></span>  
  
 <span data-ttu-id="267b8-104">Hedef .NET Framework 4.5.2 ve önceki sürümleri, uygulamalarda <xref:System.Drawing.Icon.ToBitmap%2A?displayProperty=nameWithType> yöntemi atar bir <xref:System.ArgumentOutOfRangeException> özel durumu ise <xref:System.Drawing.Icon> nesnesi PNG çerçeveler sahiptir.</span><span class="sxs-lookup"><span data-stu-id="267b8-104">In apps that target the .NET Framework 4.5.2 and earlier versions, the <xref:System.Drawing.Icon.ToBitmap%2A?displayProperty=nameWithType> method throws an <xref:System.ArgumentOutOfRangeException> exception if the <xref:System.Drawing.Icon> object has PNG frames.</span></span>  
  
## <a name="impact"></a><span data-ttu-id="267b8-105">Etki</span><span class="sxs-lookup"><span data-stu-id="267b8-105">Impact</span></span>  
 <span data-ttu-id="267b8-106">Bu değişiklik, .NET Framework 4.6 hedeflemek için derlenir ve özel işleme için uygulamanıza uygulamaları etkiler <xref:System.ArgumentOutOfRangeException> , oluşur ne zaman bir <xref:System.Drawing.Icon> nesnesi PNG çerçeveler sahiptir.</span><span class="sxs-lookup"><span data-stu-id="267b8-106">This change affects apps that are recompiled to target the .NET Framework 4.6 and that implement special handling for the <xref:System.ArgumentOutOfRangeException> that is thrown when an <xref:System.Drawing.Icon> object has PNG frames.</span></span> <span data-ttu-id="267b8-107">.NET Framework 4.6 altında çalışırken, dönüştürme başarılı bir <xref:System.ArgumentOutOfRangeException> Hayır artık oluşturulur ve bu nedenle özel durum işleyici artık çağrılır.</span><span class="sxs-lookup"><span data-stu-id="267b8-107">When running under the .NET Framework 4.6, the conversion is successful, an <xref:System.ArgumentOutOfRangeException> is no longer thrown, and therefore the exception handler is no longer invoked.</span></span>  
  
### <a name="mitigation"></a><span data-ttu-id="267b8-108">Azaltma</span><span class="sxs-lookup"><span data-stu-id="267b8-108">Mitigation</span></span>  
 <span data-ttu-id="267b8-109">Bu davranış istenmeyen ise, aşağıdaki öğeyi ekleyerek önceki davranış tutabilirsiniz [ \<çalışma zamanı >](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) app.config dosyasının:</span><span class="sxs-lookup"><span data-stu-id="267b8-109">If this behavior is undesirable, you can retain the previous behavior by adding the following element to the [\<runtime>](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) section of your app.config file:</span></span>  
  
```xml  
<AppContextSwitchOverrides   
      value="Switch.System.Drawing.DontSupportPngFramesInIcons=true" />  
```  
  
 <span data-ttu-id="267b8-110">App.config dosyasını zaten varsa `AppContextSwitchOverrides` öğesi, yeni değer birleştirilmiş ile `value` özniteliği şuna benzer:</span><span class="sxs-lookup"><span data-stu-id="267b8-110">If the app.config file already contains the `AppContextSwitchOverrides` element, the new value should be merged with the `value` attribute like this:</span></span>  
  
```xml  
<AppContextSwitchOverrides   
      value="Switch.System.Drawing.DontSupportPngFramesInIcons=true;<previous key>=<previous value>" />  
```  
  
## <a name="see-also"></a><span data-ttu-id="267b8-111">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="267b8-111">See Also</span></span>  
 [<span data-ttu-id="267b8-112">Yeniden hedefleme değişiklikleri</span><span class="sxs-lookup"><span data-stu-id="267b8-112">Retargeting Changes</span></span>](../../../docs/framework/migration-guide/retargeting-changes-in-the-net-framework-4-6.md)
