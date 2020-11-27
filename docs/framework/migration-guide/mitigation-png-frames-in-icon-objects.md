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
# <a name="mitigation-png-frames-in-icon-objects"></a><span data-ttu-id="ca12e-103">Risk azaltma: simge nesnelerinde PNG çerçeveleri</span><span class="sxs-lookup"><span data-stu-id="ca12e-103">Mitigation: PNG Frames in Icon Objects</span></span>

<span data-ttu-id="ca12e-104">Yöntem, .NET Framework 4,6 ' den başlayarak <xref:System.Drawing.Icon.ToBitmap%2A?displayProperty=nameWithType> PNG çerçevelerinden simgeleri nesnelere başarıyla dönüştürür <xref:System.Drawing.Bitmap> .</span><span class="sxs-lookup"><span data-stu-id="ca12e-104">Starting with the .NET Framework 4.6, the <xref:System.Drawing.Icon.ToBitmap%2A?displayProperty=nameWithType> method successfully converts icons with PNG frames into <xref:System.Drawing.Bitmap> objects.</span></span>  
  
 <span data-ttu-id="ca12e-105">.NET Framework 4.5.2 ve önceki sürümlerini hedefleyen uygulamalarda, <xref:System.Drawing.Icon.ToBitmap%2A?displayProperty=nameWithType> <xref:System.ArgumentOutOfRangeException> <xref:System.Drawing.Icon> nesne png çerçevelerdeyse Yöntem bir özel durum oluşturur.</span><span class="sxs-lookup"><span data-stu-id="ca12e-105">In apps that target the .NET Framework 4.5.2 and earlier versions, the <xref:System.Drawing.Icon.ToBitmap%2A?displayProperty=nameWithType> method throws an <xref:System.ArgumentOutOfRangeException> exception if the <xref:System.Drawing.Icon> object has PNG frames.</span></span>  
  
## <a name="impact"></a><span data-ttu-id="ca12e-106">Etki</span><span class="sxs-lookup"><span data-stu-id="ca12e-106">Impact</span></span>  

 <span data-ttu-id="ca12e-107">Bu değişiklik, .NET Framework 4,6 ' i hedefleyecek ve <xref:System.ArgumentOutOfRangeException> bir <xref:System.Drawing.Icon> nesne png çerçevelerindeyken oluşturulan için özel işleme uygulayan uygulamaları etkiler.</span><span class="sxs-lookup"><span data-stu-id="ca12e-107">This change affects apps that are recompiled to target the .NET Framework 4.6 and that implement special handling for the <xref:System.ArgumentOutOfRangeException> that is thrown when an <xref:System.Drawing.Icon> object has PNG frames.</span></span> <span data-ttu-id="ca12e-108">.NET Framework 4,6 altında çalışırken, dönüştürme başarılı olur, <xref:System.ArgumentOutOfRangeException> artık oluşturulmaz ve bu nedenle özel durum işleyicisi artık çağrılmayacaktır.</span><span class="sxs-lookup"><span data-stu-id="ca12e-108">When running under the .NET Framework 4.6, the conversion is successful, an <xref:System.ArgumentOutOfRangeException> is no longer thrown, and therefore the exception handler is no longer invoked.</span></span>  
  
### <a name="mitigation"></a><span data-ttu-id="ca12e-109">Risk azaltma</span><span class="sxs-lookup"><span data-stu-id="ca12e-109">Mitigation</span></span>  

 <span data-ttu-id="ca12e-110">Bu davranış istenmez ise, app.config dosyanızın bölümüne aşağıdaki öğeyi ekleyerek önceki davranışı koruyabilirsiniz [\<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) :</span><span class="sxs-lookup"><span data-stu-id="ca12e-110">If this behavior is undesirable, you can retain the previous behavior by adding the following element to the [\<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) section of your app.config file:</span></span>  
  
```xml  
<AppContextSwitchOverrides
      value="Switch.System.Drawing.DontSupportPngFramesInIcons=true" />  
```  
  
 <span data-ttu-id="ca12e-111">app.config dosyası öğesi zaten içeriyorsa `AppContextSwitchOverrides` , yeni değer aşağıdaki `value` gibi özniteliğiyle birleştirilmelidir:</span><span class="sxs-lookup"><span data-stu-id="ca12e-111">If the app.config file already contains the `AppContextSwitchOverrides` element, the new value should be merged with the `value` attribute like this:</span></span>  
  
```xml  
<AppContextSwitchOverrides
      value="Switch.System.Drawing.DontSupportPngFramesInIcons=true;previous key=previous-value" />
```
  
## <a name="see-also"></a><span data-ttu-id="ca12e-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ca12e-112">See also</span></span>

- [<span data-ttu-id="ca12e-113">Uygulama uyumluluğu</span><span class="sxs-lookup"><span data-stu-id="ca12e-113">Application compatibility</span></span>](application-compatibility.md)
