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
ms.openlocfilehash: 3908663a12f0e4edd8024c7f53f21b2e82bb8dbd
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54665402"
---
# <a name="invalidgchandlecookie-mda"></a><span data-ttu-id="c5d46-102">invalidGCHandleCookie MDA</span><span class="sxs-lookup"><span data-stu-id="c5d46-102">invalidGCHandleCookie MDA</span></span>
<span data-ttu-id="c5d46-103">`invalidGCHandleCookie` Yönetilen hata ayıklama Yardımcısı (MDA) etkin olduğu bir dönüştürme, geçersiz bir'den <xref:System.IntPtr> tanımlama bilgisi için bir <xref:System.Runtime.InteropServices.GCHandle> denenir.</span><span class="sxs-lookup"><span data-stu-id="c5d46-103">The `invalidGCHandleCookie` managed debugging assistant (MDA) is activated when a conversion from an invalid <xref:System.IntPtr> cookie to a <xref:System.Runtime.InteropServices.GCHandle> is attempted.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="c5d46-104">Belirtiler</span><span class="sxs-lookup"><span data-stu-id="c5d46-104">Symptoms</span></span>  
 <span data-ttu-id="c5d46-105">Tanımsız davranış erişim ihlalleri ve kullanın veya almaya çalışırken Bellek Bozulması gibi bir <xref:System.Runtime.InteropServices.GCHandle> gelen bir <xref:System.IntPtr>.</span><span class="sxs-lookup"><span data-stu-id="c5d46-105">Undefined behavior such as access violations and memory corruption while attempting to use or retrieve a <xref:System.Runtime.InteropServices.GCHandle> from an <xref:System.IntPtr>.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="c5d46-106">Sebep</span><span class="sxs-lookup"><span data-stu-id="c5d46-106">Cause</span></span>  
 <span data-ttu-id="c5d46-107">Bu ilk olarak oluşturulduğu değil çünkü tanımlama bilgisinin büyük olasılıkla geçersiz bir <xref:System.Runtime.InteropServices.GCHandle>, temsil eder bir <xref:System.Runtime.InteropServices.GCHandle> önce serbest bırakılmış, bir tanımlama bilgisi için bir <xref:System.Runtime.InteropServices.GCHandle> farklı uygulama etki alanında veya bir olarakyerelkodiçinsıralanmış<xref:System.Runtime.InteropServices.GCHandle>CLR yeniden içine geçirilen ancak bir <xref:System.IntPtr>, burada bir tür dönüştürme yapılmaya çalışıldı.</span><span class="sxs-lookup"><span data-stu-id="c5d46-107">The cookie is probably invalid because it was not originally created from a <xref:System.Runtime.InteropServices.GCHandle>, represents a <xref:System.Runtime.InteropServices.GCHandle> that has already been freed, is a cookie to a <xref:System.Runtime.InteropServices.GCHandle> in a different application domain, or was marshaled to native code as a <xref:System.Runtime.InteropServices.GCHandle> but passed back into the CLR as an <xref:System.IntPtr>, where a cast was attempted.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="c5d46-108">Çözüm</span><span class="sxs-lookup"><span data-stu-id="c5d46-108">Resolution</span></span>  
 <span data-ttu-id="c5d46-109">Geçerli <xref:System.IntPtr> için tanımlama bilgisi <xref:System.Runtime.InteropServices.GCHandle>.</span><span class="sxs-lookup"><span data-stu-id="c5d46-109">Specify a valid <xref:System.IntPtr> cookie for the <xref:System.Runtime.InteropServices.GCHandle>.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="c5d46-110">Çalışma zamanı üzerindeki etkisi</span><span class="sxs-lookup"><span data-stu-id="c5d46-110">Effect on the Runtime</span></span>  
 <span data-ttu-id="c5d46-111">Bu MDA etkinleştirildiğinde, hata ayıklayıcı artık köklerine nesnelerine geri geçirilen tanımlama bilgisi değerleri MDA etkinleştirilmediğinde döndürülen olanlardan farklı olduğundan izleme mümkün değildir.</span><span class="sxs-lookup"><span data-stu-id="c5d46-111">When this MDA is enabled, the debugger is no longer able to trace the roots back to their objects because the cookie values passed back are different from the ones returned when the MDA is not enabled.</span></span>  
  
## <a name="output"></a><span data-ttu-id="c5d46-112">Çıkış</span><span class="sxs-lookup"><span data-stu-id="c5d46-112">Output</span></span>  
 <span data-ttu-id="c5d46-113">Geçersiz <xref:System.IntPtr> tanımlama bilgisi değeri raporlanır.</span><span class="sxs-lookup"><span data-stu-id="c5d46-113">The invalid <xref:System.IntPtr> cookie value is reported.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="c5d46-114">Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="c5d46-114">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <invalidGCHandleCookie />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="c5d46-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c5d46-115">See also</span></span>
- <xref:System.Runtime.InteropServices.GCHandle.FromIntPtr%2A>
- <xref:System.Runtime.InteropServices.GCHandle>
- [<span data-ttu-id="c5d46-116">Yönetilen Hata Ayıklama Yardımcıları ile Hataları Tanılama</span><span class="sxs-lookup"><span data-stu-id="c5d46-116">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
