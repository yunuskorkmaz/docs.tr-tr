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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 7452ae28d63c89845b45bf500c02e771f0b8f4df
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71052607"
---
# <a name="invalidgchandlecookie-mda"></a><span data-ttu-id="89217-102">invalidGCHandleCookie MDA</span><span class="sxs-lookup"><span data-stu-id="89217-102">invalidGCHandleCookie MDA</span></span>
<span data-ttu-id="89217-103"><xref:System.Runtime.InteropServices.GCHandle> Geçersiz `invalidGCHandleCookie` bir<xref:System.IntPtr> tanımlama bilgisinden öğesine dönüştürme denendiğinde yönetilen hata ayıklama Yardımcısı (MDA) etkinleştirilir.</span><span class="sxs-lookup"><span data-stu-id="89217-103">The `invalidGCHandleCookie` managed debugging assistant (MDA) is activated when a conversion from an invalid <xref:System.IntPtr> cookie to a <xref:System.Runtime.InteropServices.GCHandle> is attempted.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="89217-104">Belirtiler</span><span class="sxs-lookup"><span data-stu-id="89217-104">Symptoms</span></span>  
 <span data-ttu-id="89217-105"><xref:System.Runtime.InteropServices.GCHandle> '<xref:System.IntPtr>Dan ' i kullanmaya veya almaya çalışırken erişim ihlalleri ve bellek bozulması gibi tanımsız davranışlar.</span><span class="sxs-lookup"><span data-stu-id="89217-105">Undefined behavior such as access violations and memory corruption while attempting to use or retrieve a <xref:System.Runtime.InteropServices.GCHandle> from an <xref:System.IntPtr>.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="89217-106">Sebep</span><span class="sxs-lookup"><span data-stu-id="89217-106">Cause</span></span>  
 <span data-ttu-id="89217-107">Tanımlama bilgisi muhtemelen bir <xref:System.Runtime.InteropServices.GCHandle>' dan oluşturulmadığından geçersiz, zaten serbest bırakılmış olan bir <xref:System.Runtime.InteropServices.GCHandle> temsil eder, farklı bir uygulama etki alanındaki bir <xref:System.Runtime.InteropServices.GCHandle> tanımlama bilgisidir, veya yerel koda şu şekilde sıralanmış <xref:System.Runtime.InteropServices.GCHandle>ancak <xref:System.IntPtr>, bir atama denendiğinde clr 'ye geri geçirilir.</span><span class="sxs-lookup"><span data-stu-id="89217-107">The cookie is probably invalid because it was not originally created from a <xref:System.Runtime.InteropServices.GCHandle>, represents a <xref:System.Runtime.InteropServices.GCHandle> that has already been freed, is a cookie to a <xref:System.Runtime.InteropServices.GCHandle> in a different application domain, or was marshaled to native code as a <xref:System.Runtime.InteropServices.GCHandle> but passed back into the CLR as an <xref:System.IntPtr>, where a cast was attempted.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="89217-108">Çözüm</span><span class="sxs-lookup"><span data-stu-id="89217-108">Resolution</span></span>  
 <span data-ttu-id="89217-109">İçin geçerli <xref:System.IntPtr> bir tanımlama bilgisi belirtin. <xref:System.Runtime.InteropServices.GCHandle></span><span class="sxs-lookup"><span data-stu-id="89217-109">Specify a valid <xref:System.IntPtr> cookie for the <xref:System.Runtime.InteropServices.GCHandle>.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="89217-110">Çalışma zamanında etki</span><span class="sxs-lookup"><span data-stu-id="89217-110">Effect on the Runtime</span></span>  
 <span data-ttu-id="89217-111">Bu MDA etkinleştirildiğinde, hata ayıklayıcı artık kök nesneleri nesnelerine geri izleyemez çünkü geri geçirilen tanımlama bilgisi değerleri, MDA etkin olmadığında döndürülmeden farklı.</span><span class="sxs-lookup"><span data-stu-id="89217-111">When this MDA is enabled, the debugger is no longer able to trace the roots back to their objects because the cookie values passed back are different from the ones returned when the MDA is not enabled.</span></span>  
  
## <a name="output"></a><span data-ttu-id="89217-112">Çıkış</span><span class="sxs-lookup"><span data-stu-id="89217-112">Output</span></span>  
 <span data-ttu-id="89217-113">Geçersiz <xref:System.IntPtr> tanımlama bilgisi değeri bildirildi.</span><span class="sxs-lookup"><span data-stu-id="89217-113">The invalid <xref:System.IntPtr> cookie value is reported.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="89217-114">Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="89217-114">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <invalidGCHandleCookie />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="89217-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="89217-115">See also</span></span>

- <xref:System.Runtime.InteropServices.GCHandle.FromIntPtr%2A>
- <xref:System.Runtime.InteropServices.GCHandle>
- [<span data-ttu-id="89217-116">Yönetilen Hata Ayıklama Yardımcıları ile Hataları Tanılama</span><span class="sxs-lookup"><span data-stu-id="89217-116">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
