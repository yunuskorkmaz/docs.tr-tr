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
# <a name="mitigation-png-frames-in-icon-objects"></a><span data-ttu-id="70396-102">Mayı Simge nesnelerinde PNG çerçeveleri</span><span class="sxs-lookup"><span data-stu-id="70396-102">Mitigation: PNG Frames in Icon Objects</span></span>
<span data-ttu-id="70396-103"><xref:System.Drawing.Icon.ToBitmap%2A?displayProperty=nameWithType> Yöntem, .NET Framework 4,6 ' den başlayarak png <xref:System.Drawing.Bitmap> çerçevelerinden simgeleri nesnelere başarıyla dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="70396-103">Starting with the .NET Framework 4.6, the <xref:System.Drawing.Icon.ToBitmap%2A?displayProperty=nameWithType> method successfully converts icons with PNG frames into <xref:System.Drawing.Bitmap> objects.</span></span>  
  
 <span data-ttu-id="70396-104">.NET Framework 4.5.2 ve önceki sürümlerini hedefleyen uygulamalarda, <xref:System.Drawing.Icon.ToBitmap%2A?displayProperty=nameWithType> <xref:System.Drawing.Icon> nesne png çerçevelerdeyse Yöntem bir <xref:System.ArgumentOutOfRangeException> özel durum oluşturur.</span><span class="sxs-lookup"><span data-stu-id="70396-104">In apps that target the .NET Framework 4.5.2 and earlier versions, the <xref:System.Drawing.Icon.ToBitmap%2A?displayProperty=nameWithType> method throws an <xref:System.ArgumentOutOfRangeException> exception if the <xref:System.Drawing.Icon> object has PNG frames.</span></span>  
  
## <a name="impact"></a><span data-ttu-id="70396-105">Etki</span><span class="sxs-lookup"><span data-stu-id="70396-105">Impact</span></span>  
 <span data-ttu-id="70396-106">Bu değişiklik, .NET Framework 4,6 ' i hedefleyecek ve bir <xref:System.ArgumentOutOfRangeException> <xref:System.Drawing.Icon> nesne png çerçevelerindeyken oluşturulan için özel işleme uygulayan uygulamaları etkiler.</span><span class="sxs-lookup"><span data-stu-id="70396-106">This change affects apps that are recompiled to target the .NET Framework 4.6 and that implement special handling for the <xref:System.ArgumentOutOfRangeException> that is thrown when an <xref:System.Drawing.Icon> object has PNG frames.</span></span> <span data-ttu-id="70396-107">.NET Framework 4,6 altında çalışırken, dönüştürme başarılı olur, <xref:System.ArgumentOutOfRangeException> artık oluşturulmaz ve bu nedenle özel durum işleyicisi artık çağrılmayacaktır.</span><span class="sxs-lookup"><span data-stu-id="70396-107">When running under the .NET Framework 4.6, the conversion is successful, an <xref:System.ArgumentOutOfRangeException> is no longer thrown, and therefore the exception handler is no longer invoked.</span></span>  
  
### <a name="mitigation"></a><span data-ttu-id="70396-108">Azaltma</span><span class="sxs-lookup"><span data-stu-id="70396-108">Mitigation</span></span>  
 <span data-ttu-id="70396-109">Bu davranış istenmez ise, App. config dosyanızın [ \<Runtime >](../configure-apps/file-schema/runtime/runtime-element.md) bölümüne aşağıdaki öğeyi ekleyerek önceki davranışı koruyabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="70396-109">If this behavior is undesirable, you can retain the previous behavior by adding the following element to the [\<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) section of your app.config file:</span></span>  
  
```xml  
<AppContextSwitchOverrides   
      value="Switch.System.Drawing.DontSupportPngFramesInIcons=true" />  
```  
  
 <span data-ttu-id="70396-110">App. config dosyası zaten `AppContextSwitchOverrides` öğesini içeriyorsa, yeni değer aşağıdaki gibi `value` özniteliğiyle birleştirilmelidir:</span><span class="sxs-lookup"><span data-stu-id="70396-110">If the app.config file already contains the `AppContextSwitchOverrides` element, the new value should be merged with the `value` attribute like this:</span></span>  
  
```xml  
<AppContextSwitchOverrides   
      value="Switch.System.Drawing.DontSupportPngFramesInIcons=true;<previous key>=<previous value>" />  
```  
  
## <a name="see-also"></a><span data-ttu-id="70396-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="70396-111">See also</span></span>

- [<span data-ttu-id="70396-112">Yeniden Hedefleme Değişiklikleri</span><span class="sxs-lookup"><span data-stu-id="70396-112">Retargeting Changes</span></span>](retargeting-changes-in-the-net-framework-4-6.md)
