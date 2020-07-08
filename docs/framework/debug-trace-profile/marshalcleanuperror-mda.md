---
title: marshalCleanupError MDA
description: Geçici yapıları temizlerken beklenmeyen bir hata oluştuğundan çağrılan Marshalcleanuıperror yönetilen hata ayıklama Yardımcısı 'nı (MDA) gözden geçirin.
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
ms.openlocfilehash: 3c7498d6f51484de3a2e84d611a2634f53724ab6
ms.sourcegitcommit: 0edbeb66d71b8df10fcb374cfca4d731b58ccdb2
ms.contentlocale: tr-TR
ms.lasthandoff: 07/07/2020
ms.locfileid: "86051628"
---
# <a name="marshalcleanuperror-mda"></a><span data-ttu-id="362ea-103">marshalCleanupError MDA</span><span class="sxs-lookup"><span data-stu-id="362ea-103">marshalCleanupError MDA</span></span>
<span data-ttu-id="362ea-104">`marshalCleanupError`Ortak dil çalışma zamanı (CLR), yerel ve yönetilen kod sınırları arasında veri türlerini sıralama için kullanılan geçici yapıları ve belleği temizlemeye çalışırken bir hatayla karşılaştığında, yönetilen hata ayıklama Yardımcısı (MDA) etkinleştirilir.</span><span class="sxs-lookup"><span data-stu-id="362ea-104">The `marshalCleanupError` managed debugging assistant (MDA) is activated when the common language runtime (CLR) encounters an error while attempting to clean up temporary structures and memory used for marshaling data types between native and managed code boundaries.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="362ea-105">Belirtiler</span><span class="sxs-lookup"><span data-stu-id="362ea-105">Symptoms</span></span>  
 <span data-ttu-id="362ea-106">Yerel ve yönetilen kod geçişleri yaparken bellek sızıntısı oluşur, iş parçacığı kültürü gibi çalışma zamanı durumu geri yüklenmez veya temizleme sırasında hatalar oluşur <xref:System.Runtime.InteropServices.SafeHandle> .</span><span class="sxs-lookup"><span data-stu-id="362ea-106">A memory leak occurs when making native and managed code transitions, runtime state such as thread culture is not restored, or errors occur in <xref:System.Runtime.InteropServices.SafeHandle> cleanup.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="362ea-107">Nedeni</span><span class="sxs-lookup"><span data-stu-id="362ea-107">Cause</span></span>  
 <span data-ttu-id="362ea-108">Geçici yapılar temizlenirken beklenmeyen bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="362ea-108">An unexpected error occurred while cleaning up temporary structures.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="362ea-109">Çözüm</span><span class="sxs-lookup"><span data-stu-id="362ea-109">Resolution</span></span>  
 <span data-ttu-id="362ea-110"><xref:System.Runtime.InteropServices.SafeHandle>Hatalar için tüm yıkıcıyı, sonlandırıcıyı ve özel sıralayıcı uygulamalarını inceleyin.</span><span class="sxs-lookup"><span data-stu-id="362ea-110">Review all <xref:System.Runtime.InteropServices.SafeHandle> destructor, finalizer, and custom marshaler implementations for errors.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="362ea-111">Çalışma zamanında etki</span><span class="sxs-lookup"><span data-stu-id="362ea-111">Effect on the Runtime</span></span>  
 <span data-ttu-id="362ea-112">Bu MDA, CLR üzerinde hiçbir etkisi yoktur.</span><span class="sxs-lookup"><span data-stu-id="362ea-112">This MDA has no effect on the CLR.</span></span>  
  
## <a name="output"></a><span data-ttu-id="362ea-113">Çıktı</span><span class="sxs-lookup"><span data-stu-id="362ea-113">Output</span></span>  
 <span data-ttu-id="362ea-114">Temizleme sırasında başarısız olan işlemi bildiren bir ileti.</span><span class="sxs-lookup"><span data-stu-id="362ea-114">A message reporting the operation that failed during cleanup.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="362ea-115">Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="362ea-115">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <marshalCleanupError />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="362ea-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="362ea-116">See also</span></span>

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="362ea-117">Yönetilen Hata Ayıklama Yardımcıları ile Hataları Tanılama</span><span class="sxs-lookup"><span data-stu-id="362ea-117">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="362ea-118">Birlikte Çalışma Hazırlama</span><span class="sxs-lookup"><span data-stu-id="362ea-118">Interop Marshaling</span></span>](../interop/interop-marshaling.md)
