---
title: invalidGCHandleCookie MDA
ms.date: 03/30/2017
helpviewer_keywords:
- MDAs (managed debugging assistants), invalid cookies
- cookies, invalid
- managed debugging assistants (MDAs), invalid cookies
- InvalidGCHandleCookie MDA
- invalid cookies
ms.assetid: 613ad742-3c11-401d-a6b3-893ceb8de4f8
ms.openlocfilehash: c1d8fab863c34313c0cdb778136c6f69a64defeb
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2020
ms.locfileid: "77216314"
---
# <a name="invalidgchandlecookie-mda"></a><span data-ttu-id="1fef6-102">invalidGCHandleCookie MDA</span><span class="sxs-lookup"><span data-stu-id="1fef6-102">invalidGCHandleCookie MDA</span></span>
<span data-ttu-id="1fef6-103">`invalidGCHandleCookie` yönetilen hata ayıklama Yardımcısı (MDA), geçersiz bir <xref:System.IntPtr> tanımlama bilgisinden <xref:System.Runtime.InteropServices.GCHandle> dönüştürme denendiğinde etkinleştirilir.</span><span class="sxs-lookup"><span data-stu-id="1fef6-103">The `invalidGCHandleCookie` managed debugging assistant (MDA) is activated when a conversion from an invalid <xref:System.IntPtr> cookie to a <xref:System.Runtime.InteropServices.GCHandle> is attempted.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="1fef6-104">Belirtiler</span><span class="sxs-lookup"><span data-stu-id="1fef6-104">Symptoms</span></span>  
 <span data-ttu-id="1fef6-105"><xref:System.IntPtr>bir <xref:System.Runtime.InteropServices.GCHandle> kullanmaya veya almaya çalışırken erişim ihlalleri ve bellek bozulması gibi tanımsız davranışlar.</span><span class="sxs-lookup"><span data-stu-id="1fef6-105">Undefined behavior such as access violations and memory corruption while attempting to use or retrieve a <xref:System.Runtime.InteropServices.GCHandle> from an <xref:System.IntPtr>.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="1fef6-106">Nedeni</span><span class="sxs-lookup"><span data-stu-id="1fef6-106">Cause</span></span>  
 <span data-ttu-id="1fef6-107">Tanımlama bilgisi büyük olasılıkla geçersiz bir <xref:System.Runtime.InteropServices.GCHandle>, zaten serbest bırakılmış olan bir <xref:System.Runtime.InteropServices.GCHandle> temsil eder, farklı bir uygulama etki alanındaki bir <xref:System.Runtime.InteropServices.GCHandle> tanımlama bilgisidir veya yerel <xref:System.Runtime.InteropServices.GCHandle> koda bir <xref:System.IntPtr>olarak geri geçirilir, ancak bir atama denendiğinde bu şekilde CLR 'ye geçirildi.</span><span class="sxs-lookup"><span data-stu-id="1fef6-107">The cookie is probably invalid because it was not originally created from a <xref:System.Runtime.InteropServices.GCHandle>, represents a <xref:System.Runtime.InteropServices.GCHandle> that has already been freed, is a cookie to a <xref:System.Runtime.InteropServices.GCHandle> in a different application domain, or was marshaled to native code as a <xref:System.Runtime.InteropServices.GCHandle> but passed back into the CLR as an <xref:System.IntPtr>, where a cast was attempted.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="1fef6-108">Çözüm</span><span class="sxs-lookup"><span data-stu-id="1fef6-108">Resolution</span></span>  
 <span data-ttu-id="1fef6-109"><xref:System.Runtime.InteropServices.GCHandle>için geçerli bir <xref:System.IntPtr> tanımlama bilgisi belirtin.</span><span class="sxs-lookup"><span data-stu-id="1fef6-109">Specify a valid <xref:System.IntPtr> cookie for the <xref:System.Runtime.InteropServices.GCHandle>.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="1fef6-110">Çalışma zamanında etki</span><span class="sxs-lookup"><span data-stu-id="1fef6-110">Effect on the Runtime</span></span>  
 <span data-ttu-id="1fef6-111">Bu MDA etkinleştirildiğinde, hata ayıklayıcı artık kök nesneleri nesnelerine geri izleyemez çünkü geri geçirilen tanımlama bilgisi değerleri, MDA etkin olmadığında döndürülmeden farklı.</span><span class="sxs-lookup"><span data-stu-id="1fef6-111">When this MDA is enabled, the debugger is no longer able to trace the roots back to their objects because the cookie values passed back are different from the ones returned when the MDA is not enabled.</span></span>  
  
## <a name="output"></a><span data-ttu-id="1fef6-112">Çıktı</span><span class="sxs-lookup"><span data-stu-id="1fef6-112">Output</span></span>  
 <span data-ttu-id="1fef6-113">Geçersiz <xref:System.IntPtr> tanımlama bilgisi değeri bildirildi.</span><span class="sxs-lookup"><span data-stu-id="1fef6-113">The invalid <xref:System.IntPtr> cookie value is reported.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="1fef6-114">Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="1fef6-114">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <invalidGCHandleCookie />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="1fef6-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1fef6-115">See also</span></span>

- <xref:System.Runtime.InteropServices.GCHandle.FromIntPtr%2A>
- <xref:System.Runtime.InteropServices.GCHandle>
- [<span data-ttu-id="1fef6-116">Yönetilen Hata Ayıklama Yardımcıları ile Hataları Tanılama</span><span class="sxs-lookup"><span data-stu-id="1fef6-116">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
