---
title: 'Risk azaltma: simge nesnelerinde PNG çerçeveleri'
description: .NET Framework 4,6 ve üzeri sürümlerde bulunan yeni davranış istenmeyen bir durum değilse, simge nesnelerinde PNG çerçevelerinin davranışını nasıl yapılandıracağınızı öğrenin.
ms.date: 03/30/2017
ms.assetid: ca87fefb-7144-4b4e-8832-5a939adbb4b2
ms.openlocfilehash: b7ba2951a38ee2d1c7a9b1fc45c5a81d24986a85
ms.sourcegitcommit: cf5a800a33de64d0aad6d115ffcc935f32375164
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/20/2020
ms.locfileid: "86475443"
---
# <a name="mitigation-png-frames-in-icon-objects"></a><span data-ttu-id="b658d-103">Risk azaltma: simge nesnelerinde PNG çerçeveleri</span><span class="sxs-lookup"><span data-stu-id="b658d-103">Mitigation: PNG Frames in Icon Objects</span></span>
<span data-ttu-id="b658d-104">Yöntem, .NET Framework 4,6 ' den başlayarak <xref:System.Drawing.Icon.ToBitmap%2A?displayProperty=nameWithType> PNG çerçevelerinden simgeleri nesnelere başarıyla dönüştürür <xref:System.Drawing.Bitmap> .</span><span class="sxs-lookup"><span data-stu-id="b658d-104">Starting with the .NET Framework 4.6, the <xref:System.Drawing.Icon.ToBitmap%2A?displayProperty=nameWithType> method successfully converts icons with PNG frames into <xref:System.Drawing.Bitmap> objects.</span></span>  
  
 <span data-ttu-id="b658d-105">.NET Framework 4.5.2 ve önceki sürümlerini hedefleyen uygulamalarda, <xref:System.Drawing.Icon.ToBitmap%2A?displayProperty=nameWithType> <xref:System.ArgumentOutOfRangeException> <xref:System.Drawing.Icon> nesne png çerçevelerdeyse Yöntem bir özel durum oluşturur.</span><span class="sxs-lookup"><span data-stu-id="b658d-105">In apps that target the .NET Framework 4.5.2 and earlier versions, the <xref:System.Drawing.Icon.ToBitmap%2A?displayProperty=nameWithType> method throws an <xref:System.ArgumentOutOfRangeException> exception if the <xref:System.Drawing.Icon> object has PNG frames.</span></span>  
  
## <a name="impact"></a><span data-ttu-id="b658d-106">Etki</span><span class="sxs-lookup"><span data-stu-id="b658d-106">Impact</span></span>  
 <span data-ttu-id="b658d-107">Bu değişiklik, .NET Framework 4,6 ' i hedefleyecek ve <xref:System.ArgumentOutOfRangeException> bir <xref:System.Drawing.Icon> nesne png çerçevelerindeyken oluşturulan için özel işleme uygulayan uygulamaları etkiler.</span><span class="sxs-lookup"><span data-stu-id="b658d-107">This change affects apps that are recompiled to target the .NET Framework 4.6 and that implement special handling for the <xref:System.ArgumentOutOfRangeException> that is thrown when an <xref:System.Drawing.Icon> object has PNG frames.</span></span> <span data-ttu-id="b658d-108">.NET Framework 4,6 altında çalışırken, dönüştürme başarılı olur, <xref:System.ArgumentOutOfRangeException> artık oluşturulmaz ve bu nedenle özel durum işleyicisi artık çağrılmayacaktır.</span><span class="sxs-lookup"><span data-stu-id="b658d-108">When running under the .NET Framework 4.6, the conversion is successful, an <xref:System.ArgumentOutOfRangeException> is no longer thrown, and therefore the exception handler is no longer invoked.</span></span>  
  
### <a name="mitigation"></a><span data-ttu-id="b658d-109">Risk azaltma</span><span class="sxs-lookup"><span data-stu-id="b658d-109">Mitigation</span></span>  
 <span data-ttu-id="b658d-110">Bu davranış istenmez ise, app.config dosyanızın bölümüne aşağıdaki öğeyi ekleyerek önceki davranışı koruyabilirsiniz [\<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) :</span><span class="sxs-lookup"><span data-stu-id="b658d-110">If this behavior is undesirable, you can retain the previous behavior by adding the following element to the [\<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) section of your app.config file:</span></span>  
  
```xml  
<AppContextSwitchOverrides
      value="Switch.System.Drawing.DontSupportPngFramesInIcons=true" />  
```  
  
 <span data-ttu-id="b658d-111">app.config dosyası öğesi zaten içeriyorsa `AppContextSwitchOverrides` , yeni değer aşağıdaki `value` gibi özniteliğiyle birleştirilmelidir:</span><span class="sxs-lookup"><span data-stu-id="b658d-111">If the app.config file already contains the `AppContextSwitchOverrides` element, the new value should be merged with the `value` attribute like this:</span></span>  
  
```xml  
<AppContextSwitchOverrides
      value="Switch.System.Drawing.DontSupportPngFramesInIcons=true;previous key=previous-value" />
```
  
## <a name="see-also"></a><span data-ttu-id="b658d-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b658d-112">See also</span></span>

- [<span data-ttu-id="b658d-113">Uygulama uyumluluğu</span><span class="sxs-lookup"><span data-stu-id="b658d-113">Application compatibility</span></span>](application-compatibility.md)
