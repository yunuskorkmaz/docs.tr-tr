---
title: overlappedFreeError MDA
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- OverlappedFreeError MDA
- overlapped free method call error
- managed debugging assistants (MDAs), overlapped structures
- overlapped structures
- MDAs (managed debugging assistants), overlapped structures
- freeing overlapped structures
ms.assetid: b6ab2d48-6eee-4bab-97a3-046b3b0a5470
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 4e17e9d6a93b69d358e89109cf965b7b9856c325
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="overlappedfreeerror-mda"></a>overlappedFreeError MDA
`overlappedFreeError` Yönetilen hata ayıklama Yardımcısı (MDA) etkinleştirilmiş olduğunda <xref:System.Threading.Overlapped.Free%28System.Threading.NativeOverlapped%2A%29?displayProperty=nameWithType> yöntemi çakışan işlem tamamlanmadan önce çağrılır.  
  
## <a name="symptoms"></a>Belirtiler  
 Erişim ihlalleri veya çöpünün toplanma yığın bozulması.  
  
## <a name="cause"></a>Sebep  
 Çakışan bir yapı işlemi tamamlandı önce bırakılmış. Serbest bırakılmış sonra Çakışan işaretçi kullanarak işlev yapısına daha sonra yazabilirsiniz. Başka bir nesneye artık bu bölge belleğinde, yığın bozulması neden olabilir.  
  
 Çakışan işlem başarıyla başlamadıysa bu MDA hata temsil edemeyebilir.  
  
## <a name="resolution"></a>Çözüm  
 Çakışan yapı kullanarak g/ç işlemi çağırmadan önce tamamlandığından emin olmak <xref:System.Threading.Overlapped.Free%28System.Threading.NativeOverlapped%2A%29> yöntemi.  
  
## <a name="effect-on-the-runtime"></a>Çalışma zamanı etkisi  
 Bu MDA CLR üzerinde etkisi yoktur.  
  
## <a name="output"></a>Çıkış  
 Bu MDA için örnek çıktı verilmiştir.  
  
 `An overlapped pointer (0x00ea3430) that was not allocated on the GC heap was passed via Pinvoke to the win32 function 'WriteFile' in module 'KERNEL32.DLL'. If the AppDomain is shut down, this can cause heap corruption when the async I/O completes. The best solution is to pass a NativeOverlappedStructure retrieved from a call to System.Threading.Overlapped.Pack(). If the AppDomain exits, the CLR will keep this structure alive and pinned until the I/O completes.`  
  
## <a name="configuration"></a>Yapılandırma  
  
```xml  
<mdaConfig>  
  <assistants>  
    <overlappedFreeError/>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Runtime.InteropServices.MarshalAsAttribute>  
 [Yönetilen Hata Ayıklama Yardımcıları ile Hataları Tanılama](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)  
 [Birlikte Çalışma için Hazırlama](../../../docs/framework/interop/interop-marshaling.md)
