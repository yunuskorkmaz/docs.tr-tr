---
title: reportAvOnComRelease MDA
description: .NET 'teki erişim ihlalleri ve bellek bozulması nedeniyle etkinleştirilebilecek reportAvOnComRelease Managed hata ayıklama Yardımcısı 'nı (MDA) gözden geçirin.
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
ms.openlocfilehash: f9ba343060cb4d16de5909a5b619353546aca8ca
ms.sourcegitcommit: c23d9666ec75b91741da43ee3d91c317d68c7327
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85803616"
---
# <a name="reportavoncomrelease-mda"></a><span data-ttu-id="d6cc5-103">reportAvOnComRelease MDA</span><span class="sxs-lookup"><span data-stu-id="d6cc5-103">reportAvOnComRelease MDA</span></span>
<span data-ttu-id="d6cc5-104">`reportAvOnComRelease`Yönetilen hata ayıklama Yardımcısı (MDA), com birlikte çalışma gerçekleştirirken ve <xref:System.Runtime.InteropServices.Marshal.Release%2A> <xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A> ham com çağrılarıyla birleştirilmiş veya yöntemi kullanılarak kullanıcı başvurusu sayma hataları nedeniyle özel durumlar oluştuğunda etkinleştirilir.</span><span class="sxs-lookup"><span data-stu-id="d6cc5-104">The `reportAvOnComRelease` managed debugging assistant (MDA) is activated when exceptions are thrown due to user reference counting errors while performing COM interop and using the <xref:System.Runtime.InteropServices.Marshal.Release%2A> or <xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A> method combined with raw COM calls.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="d6cc5-105">Belirtiler</span><span class="sxs-lookup"><span data-stu-id="d6cc5-105">Symptoms</span></span>  
 <span data-ttu-id="d6cc5-106">Erişim ihlalleri ve bellek bozulması.</span><span class="sxs-lookup"><span data-stu-id="d6cc5-106">Access violations and memory corruption.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="d6cc5-107">Nedeni</span><span class="sxs-lookup"><span data-stu-id="d6cc5-107">Cause</span></span>  
 <span data-ttu-id="d6cc5-108">Bazen, COM birlikte çalışma gerçekleştirirken ve <xref:System.Runtime.InteropServices.Marshal.Release%2A> <xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A> ham com çağrılarıyla birleştirilmiş veya yöntemi kullanılarak Kullanıcı başvuruları saymasına neden olan bir özel durum oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="d6cc5-108">Occasionally, an exception is thrown due to user reference counting errors while performing COM interop and using the <xref:System.Runtime.InteropServices.Marshal.Release%2A> or <xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A> method combined with raw COM calls.</span></span> <span data-ttu-id="d6cc5-109">Normalde bu özel durum atılır çünkü bu durum, CLR 'de bir erişim ihlaline neden olur ve bunu aşağı doğru hale getiriyor.</span><span class="sxs-lookup"><span data-stu-id="d6cc5-109">Normally, this exception is discarded because not doing so would cause an access violation in the CLR, bringing it down.</span></span> <span data-ttu-id="d6cc5-110">Bu yardımcı etkin olduğunda, bu tür özel durumlar algılanmak yerine tespit edilebilir ve bildirilebilir.</span><span class="sxs-lookup"><span data-stu-id="d6cc5-110">When this assistant is enabled, such exceptions can be detected and reported instead of being simply discarded.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="d6cc5-111">Çözüm</span><span class="sxs-lookup"><span data-stu-id="d6cc5-111">Resolution</span></span>  
 <span data-ttu-id="d6cc5-112">Başvuru sayma kodunuzu inceleyin ve hata sayma hataları için nesnenizin yerel istemcilerini inceleyerek hata sayısını araştırın.</span><span class="sxs-lookup"><span data-stu-id="d6cc5-112">Examine your reference counting code and search for errors as well as examining the native clients of your object for reference counting errors.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="d6cc5-113">Çalışma zamanında etki</span><span class="sxs-lookup"><span data-stu-id="d6cc5-113">Effect on the Runtime</span></span>  
 <span data-ttu-id="d6cc5-114">İki mod kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="d6cc5-114">Two modes are available.</span></span> <span data-ttu-id="d6cc5-115">`allowAv`Özniteliği ise `true` , yardımcı çalışma zamanının erişim ihlaline engel olmasını önler.</span><span class="sxs-lookup"><span data-stu-id="d6cc5-115">If the `allowAv` attribute is `true`, the assistant prevents the runtime from discarding the access violation.</span></span> <span data-ttu-id="d6cc5-116">Varsayılan olan ise, `allowAv` `false` çalışma zamanı erişim ihlalini atar, ancak bir özel durumun oluşturulduğunu ve atıldığını göstermek için kullanıcıya bir uyarı iletisi bildirilir.</span><span class="sxs-lookup"><span data-stu-id="d6cc5-116">If `allowAv` is `false`, which is the default, the runtime discards the access violation, but a warning message is reported to the user to indicate that an exception was thrown and discarded.</span></span>  
  
## <a name="output"></a><span data-ttu-id="d6cc5-117">Çıktı</span><span class="sxs-lookup"><span data-stu-id="d6cc5-117">Output</span></span>  
 <span data-ttu-id="d6cc5-118">Mümkünse, çıkış COM arabirimi işaretçisinin orijinal vtable 'sini içerir.</span><span class="sxs-lookup"><span data-stu-id="d6cc5-118">If possible, the output contains the COM interface pointer's original vtable.</span></span> <span data-ttu-id="d6cc5-119">Aksi takdirde, bir bilgi iletisi görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="d6cc5-119">Otherwise, an informational message is displayed.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="d6cc5-120">Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="d6cc5-120">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <reportAvOnComRelease />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="d6cc5-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d6cc5-121">See also</span></span>

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="d6cc5-122">Yönetilen Hata Ayıklama Yardımcıları ile Hataları Tanılama</span><span class="sxs-lookup"><span data-stu-id="d6cc5-122">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="d6cc5-123">Birlikte Çalışma Hazırlama</span><span class="sxs-lookup"><span data-stu-id="d6cc5-123">Interop Marshaling</span></span>](../interop/interop-marshaling.md)
