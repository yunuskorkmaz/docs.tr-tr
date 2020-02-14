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
ms.openlocfilehash: fca6b209e6432678a264f10762adb3871e3596ce
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2020
ms.locfileid: "77217217"
---
# <a name="reportavoncomrelease-mda"></a><span data-ttu-id="eff93-102">reportAvOnComRelease MDA</span><span class="sxs-lookup"><span data-stu-id="eff93-102">reportAvOnComRelease MDA</span></span>
<span data-ttu-id="eff93-103">`reportAvOnComRelease` yönetilen hata ayıklama Yardımcısı (MDA), COM birlikte çalışma gerçekleştirirken ve ham COM çağrılarıyla birleştirilmiş <xref:System.Runtime.InteropServices.Marshal.Release%2A> veya <xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A> yöntemi kullanılarak kullanıcı başvurusu sayma hataları nedeniyle özel durumlar oluştuğunda etkinleştirilir.</span><span class="sxs-lookup"><span data-stu-id="eff93-103">The `reportAvOnComRelease` managed debugging assistant (MDA) is activated when exceptions are thrown due to user reference counting errors while performing COM interop and using the <xref:System.Runtime.InteropServices.Marshal.Release%2A> or <xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A> method combined with raw COM calls.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="eff93-104">Belirtiler</span><span class="sxs-lookup"><span data-stu-id="eff93-104">Symptoms</span></span>  
 <span data-ttu-id="eff93-105">Erişim ihlalleri ve bellek bozulması.</span><span class="sxs-lookup"><span data-stu-id="eff93-105">Access violations and memory corruption.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="eff93-106">Nedeni</span><span class="sxs-lookup"><span data-stu-id="eff93-106">Cause</span></span>  
 <span data-ttu-id="eff93-107">Bazen, COM birlikte çalışma gerçekleştirirken ve ham COM çağrılarıyla birleştirilmiş <xref:System.Runtime.InteropServices.Marshal.Release%2A> ya da <xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A> yöntemi kullanılarak kullanıcı başvurusu sayma hataları nedeniyle bir özel durum oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="eff93-107">Occasionally, an exception is thrown due to user reference counting errors while performing COM interop and using the <xref:System.Runtime.InteropServices.Marshal.Release%2A> or <xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A> method combined with raw COM calls.</span></span> <span data-ttu-id="eff93-108">Normalde bu özel durum atılır çünkü bu durum, CLR 'de bir erişim ihlaline neden olur ve bunu aşağı doğru hale getiriyor.</span><span class="sxs-lookup"><span data-stu-id="eff93-108">Normally, this exception is discarded because not doing so would cause an access violation in the CLR, bringing it down.</span></span> <span data-ttu-id="eff93-109">Bu yardımcı etkin olduğunda, bu tür özel durumlar algılanmak yerine tespit edilebilir ve bildirilebilir.</span><span class="sxs-lookup"><span data-stu-id="eff93-109">When this assistant is enabled, such exceptions can be detected and reported instead of being simply discarded.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="eff93-110">Çözüm</span><span class="sxs-lookup"><span data-stu-id="eff93-110">Resolution</span></span>  
 <span data-ttu-id="eff93-111">Başvuru sayma kodunuzu inceleyin ve hata sayma hataları için nesnenizin yerel istemcilerini inceleyerek hata sayısını araştırın.</span><span class="sxs-lookup"><span data-stu-id="eff93-111">Examine your reference counting code and search for errors as well as examining the native clients of your object for reference counting errors.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="eff93-112">Çalışma zamanında etki</span><span class="sxs-lookup"><span data-stu-id="eff93-112">Effect on the Runtime</span></span>  
 <span data-ttu-id="eff93-113">İki mod kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="eff93-113">Two modes are available.</span></span> <span data-ttu-id="eff93-114">`allowAv` özniteliği `true`, yardımcı çalışma zamanının erişim ihlalini almasını engeller.</span><span class="sxs-lookup"><span data-stu-id="eff93-114">If the `allowAv` attribute is `true`, the assistant prevents the runtime from discarding the access violation.</span></span> <span data-ttu-id="eff93-115">Varsayılan değer olan `allowAv` `false`, çalışma zamanı erişim ihlalini atar, ancak bir özel durumun oluşturulduğunu ve atıldığını göstermek için kullanıcıya bir uyarı iletisi bildirilir.</span><span class="sxs-lookup"><span data-stu-id="eff93-115">If `allowAv` is `false`, which is the default, the runtime discards the access violation, but a warning message is reported to the user to indicate that an exception was thrown and discarded.</span></span>  
  
## <a name="output"></a><span data-ttu-id="eff93-116">Çıktı</span><span class="sxs-lookup"><span data-stu-id="eff93-116">Output</span></span>  
 <span data-ttu-id="eff93-117">Mümkünse, çıkış COM arabirimi işaretçisinin orijinal vtable 'sini içerir.</span><span class="sxs-lookup"><span data-stu-id="eff93-117">If possible, the output contains the COM interface pointer's original vtable.</span></span> <span data-ttu-id="eff93-118">Aksi takdirde, bir bilgi iletisi görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="eff93-118">Otherwise, an informational message is displayed.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="eff93-119">Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="eff93-119">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <reportAvOnComRelease />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="eff93-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="eff93-120">See also</span></span>

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="eff93-121">Yönetilen Hata Ayıklama Yardımcıları ile Hataları Tanılama</span><span class="sxs-lookup"><span data-stu-id="eff93-121">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="eff93-122">Birlikte Çalışma için Hazırlama</span><span class="sxs-lookup"><span data-stu-id="eff93-122">Interop Marshaling</span></span>](../interop/interop-marshaling.md)
