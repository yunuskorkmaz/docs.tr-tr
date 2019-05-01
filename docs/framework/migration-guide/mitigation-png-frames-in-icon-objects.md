---
title: 'Azaltma: Simge nesneleri PNG çerçeveleri'
ms.date: 03/30/2017
ms.assetid: ca87fefb-7144-4b4e-8832-5a939adbb4b2
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 575d77524e567ba55f7cd9222d690fcee25d3f20
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61871364"
---
# <a name="mitigation-png-frames-in-icon-objects"></a><span data-ttu-id="476ab-102">Azaltma: Simge nesneleri PNG çerçeveleri</span><span class="sxs-lookup"><span data-stu-id="476ab-102">Mitigation: PNG Frames in Icon Objects</span></span>
<span data-ttu-id="476ab-103">.NET Framework 4.6 ile başlayan <xref:System.Drawing.Icon.ToBitmap%2A?displayProperty=nameWithType> yöntemi başarıyla PNG çerçevelere simgelerle dönüştürür <xref:System.Drawing.Bitmap> nesneleri.</span><span class="sxs-lookup"><span data-stu-id="476ab-103">Starting with the .NET Framework 4.6, the <xref:System.Drawing.Icon.ToBitmap%2A?displayProperty=nameWithType> method successfully converts icons with PNG frames into <xref:System.Drawing.Bitmap> objects.</span></span>  
  
 <span data-ttu-id="476ab-104">.NET Framework 4.5.2 ve önceki sürümleri hedefleyen uygulamalarda <xref:System.Drawing.Icon.ToBitmap%2A?displayProperty=nameWithType> yöntem bir <xref:System.ArgumentOutOfRangeException> özel durum, <xref:System.Drawing.Icon> nesnenin PNG çerçeve vardır.</span><span class="sxs-lookup"><span data-stu-id="476ab-104">In apps that target the .NET Framework 4.5.2 and earlier versions, the <xref:System.Drawing.Icon.ToBitmap%2A?displayProperty=nameWithType> method throws an <xref:System.ArgumentOutOfRangeException> exception if the <xref:System.Drawing.Icon> object has PNG frames.</span></span>  
  
## <a name="impact"></a><span data-ttu-id="476ab-105">Etki</span><span class="sxs-lookup"><span data-stu-id="476ab-105">Impact</span></span>  
 <span data-ttu-id="476ab-106">Bu değişiklik, .NET Framework 4.6 hedefleyecek şekilde derlenir ve özel işlem uygulamak uygulamaları etkiler. <xref:System.ArgumentOutOfRangeException> , harekete ne zaman bir <xref:System.Drawing.Icon> nesnenin PNG çerçeve vardır.</span><span class="sxs-lookup"><span data-stu-id="476ab-106">This change affects apps that are recompiled to target the .NET Framework 4.6 and that implement special handling for the <xref:System.ArgumentOutOfRangeException> that is thrown when an <xref:System.Drawing.Icon> object has PNG frames.</span></span> <span data-ttu-id="476ab-107">.NET Framework 4. 6'altında çalışırken, dönüştürme başarılı bir <xref:System.ArgumentOutOfRangeException> Hayır artık oluşturulur ve bu nedenle özel durum işleyicisi artık çağrılır.</span><span class="sxs-lookup"><span data-stu-id="476ab-107">When running under the .NET Framework 4.6, the conversion is successful, an <xref:System.ArgumentOutOfRangeException> is no longer thrown, and therefore the exception handler is no longer invoked.</span></span>  
  
### <a name="mitigation"></a><span data-ttu-id="476ab-108">Azaltma</span><span class="sxs-lookup"><span data-stu-id="476ab-108">Mitigation</span></span>  
 <span data-ttu-id="476ab-109">Bu davranış, istenmeyen ise, önceki davranışı şu öğeye ekleyerek koruyabilirsiniz [ \<çalışma zamanı >](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) app.config dosyanıza bölümünü:</span><span class="sxs-lookup"><span data-stu-id="476ab-109">If this behavior is undesirable, you can retain the previous behavior by adding the following element to the [\<runtime>](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) section of your app.config file:</span></span>  
  
```xml  
<AppContextSwitchOverrides   
      value="Switch.System.Drawing.DontSupportPngFramesInIcons=true" />  
```  
  
 <span data-ttu-id="476ab-110">App.config dosyasını zaten varsa `AppContextSwitchOverrides` öğenin yeni değeri yükleneceğini ile `value` özniteliği şöyle:</span><span class="sxs-lookup"><span data-stu-id="476ab-110">If the app.config file already contains the `AppContextSwitchOverrides` element, the new value should be merged with the `value` attribute like this:</span></span>  
  
```xml  
<AppContextSwitchOverrides   
      value="Switch.System.Drawing.DontSupportPngFramesInIcons=true;<previous key>=<previous value>" />  
```  
  
## <a name="see-also"></a><span data-ttu-id="476ab-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="476ab-111">See also</span></span>

- [<span data-ttu-id="476ab-112">Yeniden Hedefleme Değişiklikleri</span><span class="sxs-lookup"><span data-stu-id="476ab-112">Retargeting Changes</span></span>](../../../docs/framework/migration-guide/retargeting-changes-in-the-net-framework-4-6.md)
