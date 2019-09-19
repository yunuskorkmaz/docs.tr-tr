---
title: overlappedFreeError MDA
ms.date: 03/30/2017
helpviewer_keywords:
- OverlappedFreeError MDA
- overlapped free method call error
- managed debugging assistants (MDAs), overlapped structures
- overlapped structures
- MDAs (managed debugging assistants), overlapped structures
- freeing overlapped structures
ms.assetid: b6ab2d48-6eee-4bab-97a3-046b3b0a5470
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 70d31bc187cabe49351e86a20023e2ec65e87b94
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71052396"
---
# <a name="overlappedfreeerror-mda"></a>overlappedFreeError MDA
Yönetilen hata ayıklama Yardımcısı (MDA), bir <xref:System.Threading.Overlapped.Free%28System.Threading.NativeOverlapped%2A%29?displayProperty=nameWithType> yöntemi örtüşen işlem tamamlanmadan önce çağrıldığında etkinleştirilir. `overlappedFreeError`  
  
## <a name="symptoms"></a>Belirtiler  
 Çöp toplanmış yığının erişim ihlalleri veya bozulması.  
  
## <a name="cause"></a>Sebep  
 Çakışan bir yapı, işlem tamamlanmadan önce serbest bırakıldı. Çakışan işaretçiyi kullanan işlev, daha sonra serbest olduktan sonra yapıya yazılabilir. Başka bir nesne artık bu bölgeyi kapladığı için yığın bozulmasına neden olabilir.  
  
 Çakışan işlem başarıyla başlamadıysanız Bu MDA bir hata temsil edemeyebilir.  
  
## <a name="resolution"></a>Çözüm  
 <xref:System.Threading.Overlapped.Free%28System.Threading.NativeOverlapped%2A%29> Metodu çağırmadan önce çakışan yapıyı kullanan g/ç işleminin tamamlandığından emin olun.  
  
## <a name="effect-on-the-runtime"></a>Çalışma zamanında etki  
 Bu MDA, CLR üzerinde hiçbir etkisi yoktur.  
  
## <a name="output"></a>Çıkış  
 Bu MDA için örnek çıktı aşağıda verilmiştir.  
  
 `An overlapped pointer (0x00ea3430) that was not allocated on the GC heap was passed via Pinvoke to the win32 function 'WriteFile' in module 'KERNEL32.DLL'. If the AppDomain is shut down, this can cause heap corruption when the async I/O completes. The best solution is to pass a NativeOverlappedStructure retrieved from a call to System.Threading.Overlapped.Pack(). If the AppDomain exits, the CLR will keep this structure alive and pinned until the I/O completes.`  
  
## <a name="configuration"></a>Yapılandırma  
  
```xml  
<mdaConfig>  
  <assistants>  
    <overlappedFreeError/>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [Yönetilen Hata Ayıklama Yardımcıları ile Hataları Tanılama](diagnosing-errors-with-managed-debugging-assistants.md)
- [Birlikte Çalışma için Hazırlama](../interop/interop-marshaling.md)
