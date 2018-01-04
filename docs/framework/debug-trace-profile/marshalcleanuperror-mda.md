---
title: marshalCleanupError MDA
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- cleanup operations
- marshaling, run-time errors
- managed debugging assistants (MDAs), marshaling
- MDAs (managed debugging assistants), marshaling
- marshaling cleanup error
- MarshalCleanupError MDA
- memory, cleanup errors
ms.assetid: 2f5d9e7c-ae51-4155-a435-54347aa1f091
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 641d12131f1502ce1ef00c6cf3889c803bd9fce3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="marshalcleanuperror-mda"></a><span data-ttu-id="e4955-102">marshalCleanupError MDA</span><span class="sxs-lookup"><span data-stu-id="e4955-102">marshalCleanupError MDA</span></span>
<span data-ttu-id="e4955-103">`marshalCleanupError` Yönetilen hata ayıklama Yardımcısı (MDA), ortak dil çalışma zamanı (CLR) geçici yapılar ve yerel ve yönetilen kod sınırlar arasında veri türlerini sıralama için kullanılan bellek temizleme girişimi sırasında bir hatayla karşılaştığında etkinleştirilir.</span><span class="sxs-lookup"><span data-stu-id="e4955-103">The `marshalCleanupError` managed debugging assistant (MDA) is activated when the common language runtime (CLR) encounters an error while attempting to clean up temporary structures and memory used for marshaling data types between native and managed code boundaries.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="e4955-104">Belirtiler</span><span class="sxs-lookup"><span data-stu-id="e4955-104">Symptoms</span></span>  
 <span data-ttu-id="e4955-105">Bellek sızıntısı oluşuyor yerel ve yönetilen kod geçiş yaparken, çalışma zamanı durum iş parçacığı kültürünü geri yüklenmemiş veya hataları gerçekleştirilir gibi <xref:System.Runtime.InteropServices.SafeHandle> temizleme.</span><span class="sxs-lookup"><span data-stu-id="e4955-105">A memory leak occurs when making native and managed code transitions, runtime state such as thread culture is not restored, or errors occur in <xref:System.Runtime.InteropServices.SafeHandle> cleanup.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="e4955-106">Sebep</span><span class="sxs-lookup"><span data-stu-id="e4955-106">Cause</span></span>  
 <span data-ttu-id="e4955-107">Geçici yapılarını temizleme sırasında beklenmeyen bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="e4955-107">An unexpected error occurred while cleaning up temporary structures.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="e4955-108">Çözüm</span><span class="sxs-lookup"><span data-stu-id="e4955-108">Resolution</span></span>  
 <span data-ttu-id="e4955-109">Tüm gözden <xref:System.Runtime.InteropServices.SafeHandle> yıkıcı, Sonlandırıcı ve hataları için özel sıralayıcı uygulamaları.</span><span class="sxs-lookup"><span data-stu-id="e4955-109">Review all <xref:System.Runtime.InteropServices.SafeHandle> destructor, finalizer, and custom marshaler implementations for errors.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="e4955-110">Çalışma zamanı etkisi</span><span class="sxs-lookup"><span data-stu-id="e4955-110">Effect on the Runtime</span></span>  
 <span data-ttu-id="e4955-111">Bu MDA CLR üzerinde etkisi yoktur.</span><span class="sxs-lookup"><span data-stu-id="e4955-111">This MDA has no effect on the CLR.</span></span>  
  
## <a name="output"></a><span data-ttu-id="e4955-112">Çıkış</span><span class="sxs-lookup"><span data-stu-id="e4955-112">Output</span></span>  
 <span data-ttu-id="e4955-113">Temizleme sırasında başarısız olan işlem raporlama iletisi.</span><span class="sxs-lookup"><span data-stu-id="e4955-113">A message reporting the operation that failed during cleanup.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="e4955-114">Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="e4955-114">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <marshalCleanupError />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="e4955-115">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="e4955-115">See Also</span></span>  
 <xref:System.Runtime.InteropServices.MarshalAsAttribute>  
 [<span data-ttu-id="e4955-116">Yönetilen Hata Ayıklama Yardımcıları ile Hataları Tanılama</span><span class="sxs-lookup"><span data-stu-id="e4955-116">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)  
 [<span data-ttu-id="e4955-117">Birlikte Çalışma için Hazırlama</span><span class="sxs-lookup"><span data-stu-id="e4955-117">Interop Marshaling</span></span>](../../../docs/framework/interop/interop-marshaling.md)
