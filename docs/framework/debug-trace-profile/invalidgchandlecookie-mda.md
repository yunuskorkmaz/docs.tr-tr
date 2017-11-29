---
title: invalidGCHandleCookie MDA
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- MDAs (managed debugging assistants), invalid cookies
- cookies, invalid
- managed debugging assistants (MDAs), invalid cookies
- InvalidGCHandleCookie MDA
- invalid cookies
ms.assetid: 613ad742-3c11-401d-a6b3-893ceb8de4f8
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 4757298a382085c1ffebc9a04e41eea81c31941b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="invalidgchandlecookie-mda"></a><span data-ttu-id="b78d3-102">invalidGCHandleCookie MDA</span><span class="sxs-lookup"><span data-stu-id="b78d3-102">invalidGCHandleCookie MDA</span></span>
<span data-ttu-id="b78d3-103">`invalidGCHandleCookie` Dönüştürme, geçersiz bir'ndan yönetilen hata ayıklama Yardımcısı (MDA) etkinleştirilirse <xref:System.IntPtr> tanımlama bilgisine bir <xref:System.Runtime.InteropServices.GCHandle> denenir.</span><span class="sxs-lookup"><span data-stu-id="b78d3-103">The `invalidGCHandleCookie` managed debugging assistant (MDA) is activated when a conversion from an invalid <xref:System.IntPtr> cookie to a <xref:System.Runtime.InteropServices.GCHandle> is attempted.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="b78d3-104">Belirtiler</span><span class="sxs-lookup"><span data-stu-id="b78d3-104">Symptoms</span></span>  
 <span data-ttu-id="b78d3-105">Erişim ihlalleri ve kullanın veya almaya çalışırken Bellek Bozulması gibi davranış tanımlanmamış bir <xref:System.Runtime.InteropServices.GCHandle> gelen bir <xref:System.IntPtr>.</span><span class="sxs-lookup"><span data-stu-id="b78d3-105">Undefined behavior such as access violations and memory corruption while attempting to use or retrieve a <xref:System.Runtime.InteropServices.GCHandle> from an <xref:System.IntPtr>.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="b78d3-106">Sebep</span><span class="sxs-lookup"><span data-stu-id="b78d3-106">Cause</span></span>  
 <span data-ttu-id="b78d3-107">İlk olarak gelen oluşturulmadığından tanımlama bilgisi büyük olasılıkla geçersiz bir <xref:System.Runtime.InteropServices.GCHandle>, temsil eden bir <xref:System.Runtime.InteropServices.GCHandle> zaten serbest, tanımlama bilgisi için bir <xref:System.Runtime.InteropServices.GCHandle> farklı uygulama etki alanındaki veya yerel koda bir olaraksıralanmış<xref:System.Runtime.InteropServices.GCHandle>CLR uygulamasına geri ancak geçirilen bir <xref:System.IntPtr>, burada bir cast yapılmaya çalışıldı.</span><span class="sxs-lookup"><span data-stu-id="b78d3-107">The cookie is probably invalid because it was not originally created from a <xref:System.Runtime.InteropServices.GCHandle>, represents a <xref:System.Runtime.InteropServices.GCHandle> that has already been freed, is a cookie to a <xref:System.Runtime.InteropServices.GCHandle> in a different application domain, or was marshaled to native code as a <xref:System.Runtime.InteropServices.GCHandle> but passed back into the CLR as an <xref:System.IntPtr>, where a cast was attempted.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="b78d3-108">Çözüm</span><span class="sxs-lookup"><span data-stu-id="b78d3-108">Resolution</span></span>  
 <span data-ttu-id="b78d3-109">Geçerli bir belirtin <xref:System.IntPtr> için tanımlama bilgisi <xref:System.Runtime.InteropServices.GCHandle>.</span><span class="sxs-lookup"><span data-stu-id="b78d3-109">Specify a valid <xref:System.IntPtr> cookie for the <xref:System.Runtime.InteropServices.GCHandle>.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="b78d3-110">Çalışma zamanı etkisi</span><span class="sxs-lookup"><span data-stu-id="b78d3-110">Effect on the Runtime</span></span>  
 <span data-ttu-id="b78d3-111">Bu MDA etkinleştirildiğinde, hata ayıklayıcı artık geri geçirilen tanımlama bilgisi değerleri MDA etkin değilse döndürülen olanlardan farklı olduğu için kendi nesnelere geri kökleri izleme mümkün değildir.</span><span class="sxs-lookup"><span data-stu-id="b78d3-111">When this MDA is enabled, the debugger is no longer able to trace the roots back to their objects because the cookie values passed back are different from the ones returned when the MDA is not enabled.</span></span>  
  
## <a name="output"></a><span data-ttu-id="b78d3-112">Çıkış</span><span class="sxs-lookup"><span data-stu-id="b78d3-112">Output</span></span>  
 <span data-ttu-id="b78d3-113">Geçersiz <xref:System.IntPtr> tanımlama bilgisi değerini bildirilir.</span><span class="sxs-lookup"><span data-stu-id="b78d3-113">The invalid <xref:System.IntPtr> cookie value is reported.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="b78d3-114">Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="b78d3-114">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <invalidGCHandleCookie />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="b78d3-115">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="b78d3-115">See Also</span></span>  
 <xref:System.Runtime.InteropServices.GCHandle.FromIntPtr%2A>  
 <xref:System.Runtime.InteropServices.GCHandle>  
 [<span data-ttu-id="b78d3-116">Yönetilen hata ayıklama Yardımcıları ile hataları tanılama</span><span class="sxs-lookup"><span data-stu-id="b78d3-116">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
