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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 6784848a5103dc9206267fc25fe7457257624cb7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33392037"
---
# <a name="marshalcleanuperror-mda"></a><span data-ttu-id="703de-102">marshalCleanupError MDA</span><span class="sxs-lookup"><span data-stu-id="703de-102">marshalCleanupError MDA</span></span>
<span data-ttu-id="703de-103">`marshalCleanupError` Yönetilen hata ayıklama Yardımcısı (MDA), ortak dil çalışma zamanı (CLR) geçici yapılar ve yerel ve yönetilen kod sınırlar arasında veri türlerini sıralama için kullanılan bellek temizleme girişimi sırasında bir hatayla karşılaştığında etkinleştirilir.</span><span class="sxs-lookup"><span data-stu-id="703de-103">The `marshalCleanupError` managed debugging assistant (MDA) is activated when the common language runtime (CLR) encounters an error while attempting to clean up temporary structures and memory used for marshaling data types between native and managed code boundaries.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="703de-104">Belirtiler</span><span class="sxs-lookup"><span data-stu-id="703de-104">Symptoms</span></span>  
 <span data-ttu-id="703de-105">Bellek sızıntısı oluşuyor yerel ve yönetilen kod geçiş yaparken, çalışma zamanı durum iş parçacığı kültürünü geri yüklenmemiş veya hataları gerçekleştirilir gibi <xref:System.Runtime.InteropServices.SafeHandle> temizleme.</span><span class="sxs-lookup"><span data-stu-id="703de-105">A memory leak occurs when making native and managed code transitions, runtime state such as thread culture is not restored, or errors occur in <xref:System.Runtime.InteropServices.SafeHandle> cleanup.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="703de-106">Sebep</span><span class="sxs-lookup"><span data-stu-id="703de-106">Cause</span></span>  
 <span data-ttu-id="703de-107">Geçici yapılarını temizleme sırasında beklenmeyen bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="703de-107">An unexpected error occurred while cleaning up temporary structures.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="703de-108">Çözüm</span><span class="sxs-lookup"><span data-stu-id="703de-108">Resolution</span></span>  
 <span data-ttu-id="703de-109">Tüm gözden <xref:System.Runtime.InteropServices.SafeHandle> yıkıcı, Sonlandırıcı ve hataları için özel sıralayıcı uygulamaları.</span><span class="sxs-lookup"><span data-stu-id="703de-109">Review all <xref:System.Runtime.InteropServices.SafeHandle> destructor, finalizer, and custom marshaler implementations for errors.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="703de-110">Çalışma zamanı etkisi</span><span class="sxs-lookup"><span data-stu-id="703de-110">Effect on the Runtime</span></span>  
 <span data-ttu-id="703de-111">Bu MDA CLR üzerinde etkisi yoktur.</span><span class="sxs-lookup"><span data-stu-id="703de-111">This MDA has no effect on the CLR.</span></span>  
  
## <a name="output"></a><span data-ttu-id="703de-112">Çıkış</span><span class="sxs-lookup"><span data-stu-id="703de-112">Output</span></span>  
 <span data-ttu-id="703de-113">Temizleme sırasında başarısız olan işlem raporlama iletisi.</span><span class="sxs-lookup"><span data-stu-id="703de-113">A message reporting the operation that failed during cleanup.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="703de-114">Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="703de-114">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <marshalCleanupError />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="703de-115">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="703de-115">See Also</span></span>  
 <xref:System.Runtime.InteropServices.MarshalAsAttribute>  
 [<span data-ttu-id="703de-116">Yönetilen Hata Ayıklama Yardımcıları ile Hataları Tanılama</span><span class="sxs-lookup"><span data-stu-id="703de-116">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)  
 [<span data-ttu-id="703de-117">Birlikte Çalışma için Hazırlama</span><span class="sxs-lookup"><span data-stu-id="703de-117">Interop Marshaling</span></span>](../../../docs/framework/interop/interop-marshaling.md)
