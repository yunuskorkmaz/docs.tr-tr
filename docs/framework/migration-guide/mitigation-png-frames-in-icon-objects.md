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
# <a name="mitigation-png-frames-in-icon-objects"></a><span data-ttu-id="1a844-102">Azaltma: Simge Nesnelerde PNG Çerçeveler</span><span class="sxs-lookup"><span data-stu-id="1a844-102">Mitigation: PNG Frames in Icon Objects</span></span>
<span data-ttu-id="1a844-103">.NET Framework 4.6 ile <xref:System.Drawing.Icon.ToBitmap%2A?displayProperty=nameWithType> başlayarak, yöntem PNG çerçeveli simgeleri başarıyla nesnelere <xref:System.Drawing.Bitmap> dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="1a844-103">Starting with the .NET Framework 4.6, the <xref:System.Drawing.Icon.ToBitmap%2A?displayProperty=nameWithType> method successfully converts icons with PNG frames into <xref:System.Drawing.Bitmap> objects.</span></span>  
  
 <span data-ttu-id="1a844-104">.NET Framework 4.5.2 ve önceki sürümleri hedefleyen <xref:System.Drawing.Icon.ToBitmap%2A?displayProperty=nameWithType> uygulamalarda, <xref:System.ArgumentOutOfRangeException> nesnepng <xref:System.Drawing.Icon> çerçeveleri varsa yöntem bir özel durum atar.</span><span class="sxs-lookup"><span data-stu-id="1a844-104">In apps that target the .NET Framework 4.5.2 and earlier versions, the <xref:System.Drawing.Icon.ToBitmap%2A?displayProperty=nameWithType> method throws an <xref:System.ArgumentOutOfRangeException> exception if the <xref:System.Drawing.Icon> object has PNG frames.</span></span>  
  
## <a name="impact"></a><span data-ttu-id="1a844-105">Etki</span><span class="sxs-lookup"><span data-stu-id="1a844-105">Impact</span></span>  
 <span data-ttu-id="1a844-106">Bu değişiklik, .NET Framework 4.6'yı hedeflemek için yeniden derlenen <xref:System.ArgumentOutOfRangeException> ve bir <xref:System.Drawing.Icon> nesnePNG çerçevesi olduğunda atılanlar için özel işleme uygulayan uygulamaları etkiler.</span><span class="sxs-lookup"><span data-stu-id="1a844-106">This change affects apps that are recompiled to target the .NET Framework 4.6 and that implement special handling for the <xref:System.ArgumentOutOfRangeException> that is thrown when an <xref:System.Drawing.Icon> object has PNG frames.</span></span> <span data-ttu-id="1a844-107">.NET Framework 4.6 altında çalışırken, dönüştürme başarılı <xref:System.ArgumentOutOfRangeException> olur, artık bir atılmıştır ve bu nedenle özel durum işleyicisi artık çağrılmaz.</span><span class="sxs-lookup"><span data-stu-id="1a844-107">When running under the .NET Framework 4.6, the conversion is successful, an <xref:System.ArgumentOutOfRangeException> is no longer thrown, and therefore the exception handler is no longer invoked.</span></span>  
  
### <a name="mitigation"></a><span data-ttu-id="1a844-108">Risk azaltma</span><span class="sxs-lookup"><span data-stu-id="1a844-108">Mitigation</span></span>  
 <span data-ttu-id="1a844-109">Bu davranış istenmiyorsa, app.config dosyanızın [ \<çalışma zamanı>](../configure-apps/file-schema/runtime/runtime-element.md) bölümüne aşağıdaki öğeyi ekleyerek önceki davranışı koruyabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="1a844-109">If this behavior is undesirable, you can retain the previous behavior by adding the following element to the [\<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) section of your app.config file:</span></span>  
  
```xml  
<AppContextSwitchOverrides
      value="Switch.System.Drawing.DontSupportPngFramesInIcons=true" />  
```  
  
 <span data-ttu-id="1a844-110">app.config dosyası zaten öğeyi içeriyorsa, `AppContextSwitchOverrides` yeni değer `value` aşağıdaki gibi öznitelik ile birleştirilmelidir:</span><span class="sxs-lookup"><span data-stu-id="1a844-110">If the app.config file already contains the `AppContextSwitchOverrides` element, the new value should be merged with the `value` attribute like this:</span></span>  
  
```xml  
<AppContextSwitchOverrides
      value="Switch.System.Drawing.DontSupportPngFramesInIcons=true;previous key=previous-value" />
```
  
## <a name="see-also"></a><span data-ttu-id="1a844-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1a844-111">See also</span></span>

- [<span data-ttu-id="1a844-112">Uygulama uyumluluğu</span><span class="sxs-lookup"><span data-stu-id="1a844-112">Application compatibility</span></span>](application-compatibility.md)
