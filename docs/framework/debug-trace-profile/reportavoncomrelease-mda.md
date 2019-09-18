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
ms.openlocfilehash: 0bea73a30cb103f0e72caf73a633229a0719dc6c
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71052322"
---
# <a name="reportavoncomrelease-mda"></a><span data-ttu-id="825da-102">reportAvOnComRelease MDA</span><span class="sxs-lookup"><span data-stu-id="825da-102">reportAvOnComRelease MDA</span></span>
<span data-ttu-id="825da-103">Yönetilen `reportAvOnComRelease` hata ayıklama Yardımcısı (MDA), com birlikte çalışma gerçekleştirirken ve ham com çağrılarıyla birleştirilmiş <xref:System.Runtime.InteropServices.Marshal.Release%2A> veya <xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A> yöntemi kullanılarak kullanıcı başvurusu sayma hataları nedeniyle özel durumlar oluştuğunda etkinleştirilir.</span><span class="sxs-lookup"><span data-stu-id="825da-103">The `reportAvOnComRelease` managed debugging assistant (MDA) is activated when exceptions are thrown due to user reference counting errors while performing COM interop and using the <xref:System.Runtime.InteropServices.Marshal.Release%2A> or <xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A> method combined with raw COM calls.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="825da-104">Belirtiler</span><span class="sxs-lookup"><span data-stu-id="825da-104">Symptoms</span></span>  
 <span data-ttu-id="825da-105">Erişim ihlalleri ve bellek bozulması.</span><span class="sxs-lookup"><span data-stu-id="825da-105">Access violations and memory corruption.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="825da-106">Sebep</span><span class="sxs-lookup"><span data-stu-id="825da-106">Cause</span></span>  
 <span data-ttu-id="825da-107">Bazen, com birlikte çalışma gerçekleştirirken ve ham com çağrılarıyla birleştirilmiş <xref:System.Runtime.InteropServices.Marshal.Release%2A> veya <xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A> yöntemi kullanılarak Kullanıcı başvuruları saymasına neden olan bir özel durum oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="825da-107">Occasionally, an exception is thrown due to user reference counting errors while performing COM interop and using the <xref:System.Runtime.InteropServices.Marshal.Release%2A> or <xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A> method combined with raw COM calls.</span></span> <span data-ttu-id="825da-108">Normalde bu özel durum atılır çünkü bu durum, CLR 'de bir erişim ihlaline neden olur ve bunu aşağı doğru hale getiriyor.</span><span class="sxs-lookup"><span data-stu-id="825da-108">Normally, this exception is discarded because not doing so would cause an access violation in the CLR, bringing it down.</span></span> <span data-ttu-id="825da-109">Bu yardımcı etkin olduğunda, bu tür özel durumlar algılanmak yerine tespit edilebilir ve bildirilebilir.</span><span class="sxs-lookup"><span data-stu-id="825da-109">When this assistant is enabled, such exceptions can be detected and reported instead of being simply discarded.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="825da-110">Çözüm</span><span class="sxs-lookup"><span data-stu-id="825da-110">Resolution</span></span>  
 <span data-ttu-id="825da-111">Başvuru sayma kodunuzu inceleyin ve hata sayma hataları için nesnenizin yerel istemcilerini inceleyerek hata sayısını araştırın.</span><span class="sxs-lookup"><span data-stu-id="825da-111">Examine your reference counting code and search for errors as well as examining the native clients of your object for reference counting errors.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="825da-112">Çalışma zamanında etki</span><span class="sxs-lookup"><span data-stu-id="825da-112">Effect on the Runtime</span></span>  
 <span data-ttu-id="825da-113">İki mod kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="825da-113">Two modes are available.</span></span> <span data-ttu-id="825da-114">`allowAv` Özniteliği ise`true`, yardımcı çalışma zamanının erişim ihlaline engel olmasını önler.</span><span class="sxs-lookup"><span data-stu-id="825da-114">If the `allowAv` attribute is `true`, the assistant prevents the runtime from discarding the access violation.</span></span> <span data-ttu-id="825da-115">`allowAv` Varsayılanolanise,çalışmazamanıerişimihlaliniatar,ancakbirözeldurumunoluşturulduğunuveatıldığınıgöstermekiçinkullanıcıya`false`bir uyarı iletisi bildirilir.</span><span class="sxs-lookup"><span data-stu-id="825da-115">If `allowAv` is `false`, which is the default, the runtime discards the access violation, but a warning message is reported to the user to indicate that an exception was thrown and discarded.</span></span>  
  
## <a name="output"></a><span data-ttu-id="825da-116">Çıkış</span><span class="sxs-lookup"><span data-stu-id="825da-116">Output</span></span>  
 <span data-ttu-id="825da-117">Mümkünse, çıkış COM arabirimi işaretçisinin orijinal vtable 'sini içerir.</span><span class="sxs-lookup"><span data-stu-id="825da-117">If possible, the output contains the COM interface pointer's original vtable.</span></span> <span data-ttu-id="825da-118">Aksi takdirde, bir bilgi iletisi görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="825da-118">Otherwise, an informational message is displayed.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="825da-119">Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="825da-119">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <reportAvOnComRelease />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="825da-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="825da-120">See also</span></span>

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="825da-121">Yönetilen Hata Ayıklama Yardımcıları ile Hataları Tanılama</span><span class="sxs-lookup"><span data-stu-id="825da-121">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="825da-122">Birlikte Çalışma için Hazırlama</span><span class="sxs-lookup"><span data-stu-id="825da-122">Interop Marshaling</span></span>](../interop/interop-marshaling.md)
