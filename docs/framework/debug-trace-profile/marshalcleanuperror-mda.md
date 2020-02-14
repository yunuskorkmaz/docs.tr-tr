---
title: marshalCleanupError MDA
ms.date: 03/30/2017
helpviewer_keywords:
- cleanup operations
- marshaling, run-time errors
- managed debugging assistants (MDAs), marshaling
- MDAs (managed debugging assistants), marshaling
- marshaling cleanup error
- MarshalCleanupError MDA
- memory, cleanup errors
ms.assetid: 2f5d9e7c-ae51-4155-a435-54347aa1f091
ms.openlocfilehash: 1a14c548ce960d53f47934595171189db28edfbb
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2020
ms.locfileid: "77216150"
---
# <a name="marshalcleanuperror-mda"></a><span data-ttu-id="4a50d-102">marshalCleanupError MDA</span><span class="sxs-lookup"><span data-stu-id="4a50d-102">marshalCleanupError MDA</span></span>
<span data-ttu-id="4a50d-103">`marshalCleanupError` yönetilen hata ayıklama Yardımcısı (MDA), ortak dil çalışma zamanı (CLR), yerel ve yönetilen kod sınırları arasında veri türlerini hazırlama için kullanılan geçici yapıları ve belleği temizlemeye çalışırken bir hatayla karşılaştığında etkinleştirilir.</span><span class="sxs-lookup"><span data-stu-id="4a50d-103">The `marshalCleanupError` managed debugging assistant (MDA) is activated when the common language runtime (CLR) encounters an error while attempting to clean up temporary structures and memory used for marshaling data types between native and managed code boundaries.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="4a50d-104">Belirtiler</span><span class="sxs-lookup"><span data-stu-id="4a50d-104">Symptoms</span></span>  
 <span data-ttu-id="4a50d-105">Yerel ve yönetilen kod geçişleri yaparken bir bellek sızıntısı oluşur, iş parçacığı kültürü gibi çalışma zamanı durumu geri yüklenmez veya <xref:System.Runtime.InteropServices.SafeHandle> Temizleme sırasında hatalar oluşur.</span><span class="sxs-lookup"><span data-stu-id="4a50d-105">A memory leak occurs when making native and managed code transitions, runtime state such as thread culture is not restored, or errors occur in <xref:System.Runtime.InteropServices.SafeHandle> cleanup.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="4a50d-106">Nedeni</span><span class="sxs-lookup"><span data-stu-id="4a50d-106">Cause</span></span>  
 <span data-ttu-id="4a50d-107">Geçici yapılar temizlenirken beklenmeyen bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="4a50d-107">An unexpected error occurred while cleaning up temporary structures.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="4a50d-108">Çözüm</span><span class="sxs-lookup"><span data-stu-id="4a50d-108">Resolution</span></span>  
 <span data-ttu-id="4a50d-109">Hata için tüm <xref:System.Runtime.InteropServices.SafeHandle> yıkıcıyı, sonlandırıcıyı ve özel sıralayıcı uygulamalarını gözden geçirin.</span><span class="sxs-lookup"><span data-stu-id="4a50d-109">Review all <xref:System.Runtime.InteropServices.SafeHandle> destructor, finalizer, and custom marshaler implementations for errors.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="4a50d-110">Çalışma zamanında etki</span><span class="sxs-lookup"><span data-stu-id="4a50d-110">Effect on the Runtime</span></span>  
 <span data-ttu-id="4a50d-111">Bu MDA, CLR üzerinde hiçbir etkisi yoktur.</span><span class="sxs-lookup"><span data-stu-id="4a50d-111">This MDA has no effect on the CLR.</span></span>  
  
## <a name="output"></a><span data-ttu-id="4a50d-112">Çıktı</span><span class="sxs-lookup"><span data-stu-id="4a50d-112">Output</span></span>  
 <span data-ttu-id="4a50d-113">Temizleme sırasında başarısız olan işlemi bildiren bir ileti.</span><span class="sxs-lookup"><span data-stu-id="4a50d-113">A message reporting the operation that failed during cleanup.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="4a50d-114">Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="4a50d-114">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <marshalCleanupError />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="4a50d-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4a50d-115">See also</span></span>

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="4a50d-116">Yönetilen Hata Ayıklama Yardımcıları ile Hataları Tanılama</span><span class="sxs-lookup"><span data-stu-id="4a50d-116">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="4a50d-117">Birlikte Çalışma için Hazırlama</span><span class="sxs-lookup"><span data-stu-id="4a50d-117">Interop Marshaling</span></span>](../interop/interop-marshaling.md)
