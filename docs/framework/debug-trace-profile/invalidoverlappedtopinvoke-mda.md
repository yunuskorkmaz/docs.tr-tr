---
title: invalidOverlappedToPinvoke MDA
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- overlapped pointers
- managed debugging assistants (MDAs), overlapped pointers
- invalid overlapped pointer to platform invoke
- InvalidOverlappedToPinvoke MDA
- MDAs (managed debugging assistants), overlapped pointers
- pointers, overlapped
ms.assetid: 28876047-58bd-4fed-9452-c7da346d67c0
caps.latest.revision: "14"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 395601c6aaff39bf2acb01ae36d306e57566aa4f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="invalidoverlappedtopinvoke-mda"></a>invalidOverlappedToPinvoke MDA
`invalidOverlappedToPinvoke` Yönetilen hata ayıklama Yardımcısı (MDA) atık toplama yığında oluşturulmayan Çakışan işaretçi belirli Win32 işlevleri geçirildiğinde etkinleştirilir.  
  
> [!NOTE]
>  Varsayılan olarak, bu MDA platform çağırma çağrısı kodunuzda tanımlanır ve hata ayıklayıcısı her yöntemi JustMyCode durumunu raporlar yalnızca etkinleştirilir. (Örneğin, MDbg.exe uzantısız) JustMyCode anlamıyor bir hata ayıklayıcısı bu MDA etkinleştirmemek. Bu MDA etkinleştirilebilir bu hata ayıklayıcıları için bir yapılandırma dosyası ve açıkça ayarlarını kullanarak `justMyCode="false"` içinde. mda.config dosya `(<invalidOverlappedToPinvoke enable="true" justMyCode="false"/>`).  
  
## <a name="symptoms"></a>Belirtiler  
 Kilitlenme veya unexplainable yığın bozulmaları.  
  
## <a name="cause"></a>Sebep  
 Çöp toplama yığında oluşturulmayan Çakışan işaretçi belirli işletim sistemi işlevleri geçirilir.  
  
 Aşağıdaki tabloda, bu MDA izleyen işlevleri gösterir.  
  
|Modül|İşlev|  
|------------|--------------|  
|HttpApi.dll|`HttpReceiveHttpRequest`|  
|Iphlpapi.dll|`NotifyAddrChange`|  
|Kernel32.dll|`ReadFile`|  
|Kernel32.dll|`ReadFileEx`|  
|Kernel32.dll|`WriteFile`|  
|Kernel32.dll|`WriteFileEx`|  
|Kernel32.dll|`ReadDirectoryChangesW`|  
|Kernel32.dll|`PostQueuedCompletionStatus`|  
|MSWSock.dll|`ConnectEx`|  
|WS2_32.dll|`WSASend`|  
|WS2_32.dll|`WSASendTo`|  
|WS2_32.dll|`WSARecv`|  
|WS2_32.dll|`WSARecvFrom`|  
|MQRT.dll|`MQReceiveMessage`|  
  
 Bu koşul için olduğundan olası yığın bozulması yüksek <xref:System.AppDomain> çağrı unload yapma. Varsa <xref:System.AppDomain> kaldırır, uygulama kodu ya da ücretsiz işlemi bittikten ya da kod bellek sızıntısı Bozulması neden, daha sonra sorunlarla neden Çakışan işaretçi için bellek.  
  
## <a name="resolution"></a>Çözüm  
 Kullanım bir <xref:System.Threading.Overlapped> çağrılırken, nesne <xref:System.Threading.Overlapped.Pack%2A> almak için yöntemi bir <xref:System.Threading.NativeOverlapped> işlevine geçirilen yapısı. Varsa <xref:System.AppDomain> kaldırır, CLR bekler işaretçinin boşaltma önce zaman uyumsuz işlemi tamamlanana kadar.  
  
## <a name="effect-on-the-runtime"></a>Çalışma zamanı etkisi  
 Bu MDA CLR üzerinde hiçbir etkisi vardı.  
  
## <a name="output"></a>Çıkış  
 Bu MDA çıktının bir örnek verilmiştir.  
  
 `An overlapped pointer (0x00ea3430) that was not allocated on the GC heap was passed via Pinvoke to the Win32 function 'WriteFile' in module 'KERNEL32.DLL'. If the AppDomain is shut down, this can cause heap corruption when the async I/O completes. The best solution is to pass a NativeOverlapped structure retrieved from a call to System.Threading.Overlapped.Pack(). If the AppDomain exits, the CLR will keep this structure alive and pinned until the I/O completes.`  
  
## <a name="configuration"></a>Yapılandırma  
  
```xml  
<mdaConfig>  
  <assistants>  
    <invalidOverlappedToPinvoke/>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Runtime.InteropServices.MarshalAsAttribute>  
 [Yönetilen Hata Ayıklama Yardımcıları ile Hataları Tanılama](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)  
 [Birlikte Çalışma için Hazırlama](../../../docs/framework/interop/interop-marshaling.md)
