---
title: reportAvOnComRelease MDA
ms.date: 03/30/2017
helpviewer_keywords:
- MDAs (managed debugging assistants), reference counting errors
- exceptions, reference counting errors
- ReportAvOnComRelease MDA
- COM release access violations
- user reference counting errors
- managed debugging assistants (MDAs), reference counting errors
- report access violation on Com release
- reference counting errors
ms.assetid: a2b86b63-08b2-4943-b344-3c2cf46ccd31
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 7b03b4f3f8c5b6e3e86903a240259ddf2fbf5c71
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33386372"
---
# <a name="reportavoncomrelease-mda"></a><span data-ttu-id="5a1a8-102">reportAvOnComRelease MDA</span><span class="sxs-lookup"><span data-stu-id="5a1a8-102">reportAvOnComRelease MDA</span></span>
<span data-ttu-id="5a1a8-103">`reportAvOnComRelease` Yönetilen hata ayıklama Yardımcısı (MDA) kullanıcı başvuru sayım hataları COM birlikte çalışma ve kullanarak gerçekleştirilirken nedeniyle özel durum oluştuğunda etkinleştirilirse <xref:System.Runtime.InteropServices.Marshal.Release%2A> veya <xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A> yöntemi birleştirilmiş ham COM aramaları.</span><span class="sxs-lookup"><span data-stu-id="5a1a8-103">The `reportAvOnComRelease` managed debugging assistant (MDA) is activated when exceptions are thrown due to user reference counting errors while performing COM interop and using the <xref:System.Runtime.InteropServices.Marshal.Release%2A> or <xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A> method combined with raw COM calls.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="5a1a8-104">Belirtiler</span><span class="sxs-lookup"><span data-stu-id="5a1a8-104">Symptoms</span></span>  
 <span data-ttu-id="5a1a8-105">Erişim ihlalleri ve Bellek Bozulması.</span><span class="sxs-lookup"><span data-stu-id="5a1a8-105">Access violations and memory corruption.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="5a1a8-106">Sebep</span><span class="sxs-lookup"><span data-stu-id="5a1a8-106">Cause</span></span>  
 <span data-ttu-id="5a1a8-107">Bazen, kullanıcı başvuru sayım hataları COM birlikte çalışma ve kullanarak gerçekleştirilirken nedeniyle bir özel durum <xref:System.Runtime.InteropServices.Marshal.Release%2A> veya <xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A> yöntemi birleştirilmiş ham COM aramaları.</span><span class="sxs-lookup"><span data-stu-id="5a1a8-107">Occasionally, an exception is thrown due to user reference counting errors while performing COM interop and using the <xref:System.Runtime.InteropServices.Marshal.Release%2A> or <xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A> method combined with raw COM calls.</span></span> <span data-ttu-id="5a1a8-108">Bunu yapmazsanız bir erişim ihlali CLR neden olacağından normalde, bu özel durum atılır getiren.</span><span class="sxs-lookup"><span data-stu-id="5a1a8-108">Normally, this exception is discarded because not doing so would cause an access violation in the CLR, bringing it down.</span></span> <span data-ttu-id="5a1a8-109">Bu yardımcı etkinleştirildiğinde, bu tür özel durumlar algıladı ve yalnızca atılmadan yerine bildirdi.</span><span class="sxs-lookup"><span data-stu-id="5a1a8-109">When this assistant is enabled, such exceptions can be detected and reported instead of being simply discarded.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="5a1a8-110">Çözüm</span><span class="sxs-lookup"><span data-stu-id="5a1a8-110">Resolution</span></span>  
 <span data-ttu-id="5a1a8-111">Başvuru sayım kodu ve hatalarını arayın yanı sıra nesnenizin başvuru sayım hataları için yerel istemcilerde inceleniyor inceleyin.</span><span class="sxs-lookup"><span data-stu-id="5a1a8-111">Examine your reference counting code and search for errors as well as examining the native clients of your object for reference counting errors.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="5a1a8-112">Çalışma zamanı etkisi</span><span class="sxs-lookup"><span data-stu-id="5a1a8-112">Effect on the Runtime</span></span>  
 <span data-ttu-id="5a1a8-113">İki mod kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="5a1a8-113">Two modes are available.</span></span> <span data-ttu-id="5a1a8-114">Varsa `allowAv` özniteliği `true`, erişim ihlali atılıyor çalışma zamanı Yardımcısı engeller.</span><span class="sxs-lookup"><span data-stu-id="5a1a8-114">If the `allowAv` attribute is `true`, the assistant prevents the runtime from discarding the access violation.</span></span> <span data-ttu-id="5a1a8-115">Varsa `allowAv` olan `false`, varsayılan, erişim ihlali çalışma zamanı atar, ancak bir uyarı iletisi bir özel durum oluşturulur ve atılan gerektiğini belirtmek için kullanıcıya bildirilir.</span><span class="sxs-lookup"><span data-stu-id="5a1a8-115">If `allowAv` is `false`, which is the default, the runtime discards the access violation, but a warning message is reported to the user to indicate that an exception was thrown and discarded.</span></span>  
  
## <a name="output"></a><span data-ttu-id="5a1a8-116">Çıkış</span><span class="sxs-lookup"><span data-stu-id="5a1a8-116">Output</span></span>  
 <span data-ttu-id="5a1a8-117">Mümkünse, çıktı COM arabirimi işaretçinin özgün vtable içerir.</span><span class="sxs-lookup"><span data-stu-id="5a1a8-117">If possible, the output contains the COM interface pointer's original vtable.</span></span> <span data-ttu-id="5a1a8-118">Aksi halde, bir bilgilendirme iletisi görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="5a1a8-118">Otherwise, an informational message is displayed.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="5a1a8-119">Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="5a1a8-119">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <reportAvOnComRelease />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="5a1a8-120">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="5a1a8-120">See Also</span></span>  
 <xref:System.Runtime.InteropServices.MarshalAsAttribute>  
 [<span data-ttu-id="5a1a8-121">Yönetilen Hata Ayıklama Yardımcıları ile Hataları Tanılama</span><span class="sxs-lookup"><span data-stu-id="5a1a8-121">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)  
 [<span data-ttu-id="5a1a8-122">Birlikte Çalışma için Hazırlama</span><span class="sxs-lookup"><span data-stu-id="5a1a8-122">Interop Marshaling</span></span>](../../../docs/framework/interop/interop-marshaling.md)
