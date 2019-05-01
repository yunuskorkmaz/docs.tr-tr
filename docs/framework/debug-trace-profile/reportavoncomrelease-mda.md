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
ms.openlocfilehash: f0ecb05dba70dc9c8aba7f04928fd0ab49c900c8
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61873957"
---
# <a name="reportavoncomrelease-mda"></a><span data-ttu-id="7da4c-102">reportAvOnComRelease MDA</span><span class="sxs-lookup"><span data-stu-id="7da4c-102">reportAvOnComRelease MDA</span></span>
<span data-ttu-id="7da4c-103">`reportAvOnComRelease` Yönetilen hata ayıklama Yardımcısı (MDA) kullanıcı başvuru sayım hataları COM birlikte çalışma ve kullanarak gerçekleştirilirken nedeniyle özel durumlar oluşturulduğunda etkinleştirilir <xref:System.Runtime.InteropServices.Marshal.Release%2A> veya <xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A> yöntemi ham COM çağrıları ile birlikte.</span><span class="sxs-lookup"><span data-stu-id="7da4c-103">The `reportAvOnComRelease` managed debugging assistant (MDA) is activated when exceptions are thrown due to user reference counting errors while performing COM interop and using the <xref:System.Runtime.InteropServices.Marshal.Release%2A> or <xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A> method combined with raw COM calls.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="7da4c-104">Belirtiler</span><span class="sxs-lookup"><span data-stu-id="7da4c-104">Symptoms</span></span>  
 <span data-ttu-id="7da4c-105">Erişim ihlalleri ve Bellek Bozulması.</span><span class="sxs-lookup"><span data-stu-id="7da4c-105">Access violations and memory corruption.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="7da4c-106">Sebep</span><span class="sxs-lookup"><span data-stu-id="7da4c-106">Cause</span></span>  
 <span data-ttu-id="7da4c-107">Bazen, kullanıcı başvuru sayım hataları COM birlikte çalışma ve kullanarak gerçekleştirilirken nedeniyle bir özel durum <xref:System.Runtime.InteropServices.Marshal.Release%2A> veya <xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A> yöntemi ham COM çağrıları ile birlikte.</span><span class="sxs-lookup"><span data-stu-id="7da4c-107">Occasionally, an exception is thrown due to user reference counting errors while performing COM interop and using the <xref:System.Runtime.InteropServices.Marshal.Release%2A> or <xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A> method combined with raw COM calls.</span></span> <span data-ttu-id="7da4c-108">Normalde, bunu bir erişim ihlali CLR'de neden olacağından bu özel durum atılır yükseltilebildiği.</span><span class="sxs-lookup"><span data-stu-id="7da4c-108">Normally, this exception is discarded because not doing so would cause an access violation in the CLR, bringing it down.</span></span> <span data-ttu-id="7da4c-109">Bu yardımcı etkinleştirildiğinde, bu tür özel durumların algıladı ve yalnızca atılmadan yerine bildirdi.</span><span class="sxs-lookup"><span data-stu-id="7da4c-109">When this assistant is enabled, such exceptions can be detected and reported instead of being simply discarded.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="7da4c-110">Çözüm</span><span class="sxs-lookup"><span data-stu-id="7da4c-110">Resolution</span></span>  
 <span data-ttu-id="7da4c-111">Başvuru sayım kod ve hataları Ara hem de nesne başvuru sayım hataları için yerel istemcileri İnceleme inceleyin.</span><span class="sxs-lookup"><span data-stu-id="7da4c-111">Examine your reference counting code and search for errors as well as examining the native clients of your object for reference counting errors.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="7da4c-112">Çalışma zamanı üzerindeki etkisi</span><span class="sxs-lookup"><span data-stu-id="7da4c-112">Effect on the Runtime</span></span>  
 <span data-ttu-id="7da4c-113">İki modu kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="7da4c-113">Two modes are available.</span></span> <span data-ttu-id="7da4c-114">Varsa `allowAv` özniteliği `true`, erişim ihlali atılıyor gelen çalışma zamanı Yardımcısı engeller.</span><span class="sxs-lookup"><span data-stu-id="7da4c-114">If the `allowAv` attribute is `true`, the assistant prevents the runtime from discarding the access violation.</span></span> <span data-ttu-id="7da4c-115">Varsa `allowAv` olduğu `false`, varsayılan değer olan, çalışma zamanı erişim ihlali atar, ancak bir özel durum ve atılan gerektiğini belirtmek için kullanıcıya bir uyarı iletisi bildirilir.</span><span class="sxs-lookup"><span data-stu-id="7da4c-115">If `allowAv` is `false`, which is the default, the runtime discards the access violation, but a warning message is reported to the user to indicate that an exception was thrown and discarded.</span></span>  
  
## <a name="output"></a><span data-ttu-id="7da4c-116">Çıkış</span><span class="sxs-lookup"><span data-stu-id="7da4c-116">Output</span></span>  
 <span data-ttu-id="7da4c-117">Mümkünse, COM arabirimi işaretçisini kişinin orijinal vtable çıkış içerir.</span><span class="sxs-lookup"><span data-stu-id="7da4c-117">If possible, the output contains the COM interface pointer's original vtable.</span></span> <span data-ttu-id="7da4c-118">Aksi halde bir bilgi iletisi görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="7da4c-118">Otherwise, an informational message is displayed.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="7da4c-119">Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="7da4c-119">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <reportAvOnComRelease />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="7da4c-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7da4c-120">See also</span></span>

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="7da4c-121">Yönetilen Hata Ayıklama Yardımcıları ile Hataları Tanılama</span><span class="sxs-lookup"><span data-stu-id="7da4c-121">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="7da4c-122">Birlikte Çalışma için Hazırlama</span><span class="sxs-lookup"><span data-stu-id="7da4c-122">Interop Marshaling</span></span>](../../../docs/framework/interop/interop-marshaling.md)
