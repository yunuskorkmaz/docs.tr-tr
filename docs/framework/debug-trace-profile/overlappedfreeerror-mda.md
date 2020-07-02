---
title: overlappedFreeError MDA
description: .NET 'teki overlappedFreeError Managed hata ayıklama Yardımcısı 'nı (MDA) inceleyerek, erişim ihlallerinde veya atık toplanan yığının bozulmasıyla etkinleştirilebilir.
ms.date: 03/30/2017
helpviewer_keywords:
- OverlappedFreeError MDA
- overlapped free method call error
- managed debugging assistants (MDAs), overlapped structures
- overlapped structures
- MDAs (managed debugging assistants), overlapped structures
- freeing overlapped structures
ms.assetid: b6ab2d48-6eee-4bab-97a3-046b3b0a5470
ms.openlocfilehash: 9be33c59723ecb2743f2bc610d7fb69d24ff388c
ms.sourcegitcommit: c23d9666ec75b91741da43ee3d91c317d68c7327
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85803929"
---
# <a name="overlappedfreeerror-mda"></a>overlappedFreeError MDA
`overlappedFreeError`Yönetilen hata ayıklama Yardımcısı (MDA), bir <xref:System.Threading.Overlapped.Free%28System.Threading.NativeOverlapped%2A%29?displayProperty=nameWithType> yöntemi örtüşen işlem tamamlanmadan önce çağrıldığında etkinleştirilir.  
  
## <a name="symptoms"></a>Belirtiler  
 Çöp toplanmış yığının erişim ihlalleri veya bozulması.  
  
## <a name="cause"></a>Nedeni  
 Çakışan bir yapı, işlem tamamlanmadan önce serbest bırakıldı. Çakışan işaretçiyi kullanan işlev, daha sonra serbest olduktan sonra yapıya yazılabilir. Başka bir nesne artık bu bölgeyi kapladığı için yığın bozulmasına neden olabilir.  
  
 Çakışan işlem başarıyla başlamadıysanız Bu MDA bir hata temsil edemeyebilir.  
  
## <a name="resolution"></a>Çözüm  
 Metodu çağırmadan önce çakışan yapıyı kullanan g/ç işleminin tamamlandığından emin olun <xref:System.Threading.Overlapped.Free%28System.Threading.NativeOverlapped%2A%29> .  
  
## <a name="effect-on-the-runtime"></a>Çalışma zamanında etki  
 Bu MDA, CLR üzerinde hiçbir etkisi yoktur.  
  
## <a name="output"></a>Çıktı  
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
- [Birlikte Çalışma Hazırlama](../interop/interop-marshaling.md)
