---
title: invalidOverlappedToPinvoke MDA
ms.date: 03/30/2017
helpviewer_keywords:
- overlapped pointers
- managed debugging assistants (MDAs), overlapped pointers
- invalid overlapped pointer to platform invoke
- InvalidOverlappedToPinvoke MDA
- MDAs (managed debugging assistants), overlapped pointers
- pointers, overlapped
ms.assetid: 28876047-58bd-4fed-9452-c7da346d67c0
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 4dc09f3e8cb926d31b21f0cc2a6442c7a6b8dec9
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54714791"
---
# <a name="invalidoverlappedtopinvoke-mda"></a>invalidOverlappedToPinvoke MDA
`invalidOverlappedToPinvoke` Yönetilen hata ayıklama Yardımcısı (MDA) çöp koleksiyonu yığınında oluşturulmamış bir çakışan işaretçi belirli Win32 işlevlerine geçirildiğinde etkinleştirilir.  
  
> [!NOTE]
>  Varsayılan olarak, bu MDA, yalnızca platform çağırma çağrısı kodunuzda tanımlanır ve hata ayıklayıcı her yöntemin JustMyCode durumunu raporlar etkinleştirilir. JustMyCode (örneğin, MDbg.exe uzantısız) anlamıyor bir hata ayıklayıcı bu mda'nın etkinleştirmez. Bu MDA etkinleştirilebilir bu hata ayıklayıcıları için bir yapılandırma dosyası ve açıkça mda.config kullanarak `justMyCode="false"` içinde. mda.config dosyasından `(<invalidOverlappedToPinvoke enable="true" justMyCode="false"/>`).  
  
## <a name="symptoms"></a>Belirtiler  
 Sistem çökmeleri ya da açıklanamaz yığın bozulmaları.  
  
## <a name="cause"></a>Sebep  
 Çöp koleksiyonu yığınında oluşturulmamış bir çakışan işaretçi belirli işletim sistemi işlevlerine geçirilir.  
  
 Aşağıdaki tablo bu mda'nın izlediği işlevleri gösterir.  
  
|Modül|İşlev|  
|------------|--------------|  
|HttpApi.dll|`HttpReceiveHttpRequest`|  
|IpHlpApi.dll|`NotifyAddrChange`|  
|kernel32.dll|`ReadFile`|  
|kernel32.dll|`ReadFileEx`|  
|kernel32.dll|`WriteFile`|  
|kernel32.dll|`WriteFileEx`|  
|kernel32.dll|`ReadDirectoryChangesW`|  
|kernel32.dll|`PostQueuedCompletionStatus`|  
|MSWSock.dll|`ConnectEx`|  
|WS2_32.dll|`WSASend`|  
|WS2_32.dll|`WSASendTo`|  
|WS2_32.dll|`WSARecv`|  
|WS2_32.dll|`WSARecvFrom`|  
|MQRT.dll|`MQReceiveMessage`|  
  
 Çünkü bu koşul için yığın bozulma olasılığı yüksektir <xref:System.AppDomain> yapılıyor çağrısını kaldırın. Varsa <xref:System.AppDomain> kaldırılırsa, uygulama kodu serbest bırakacak ya da işlem bittiğinde ya da kod bellekte sızıntı oluşturacaktır Bozulması neden, daha sonra sorunlarla neden Çakışan işaretçi için bellek.  
  
## <a name="resolution"></a>Çözüm  
 Kullanım bir <xref:System.Threading.Overlapped> çağrılırken, nesne <xref:System.Threading.Overlapped.Pack%2A> almak için yöntemi bir <xref:System.Threading.NativeOverlapped> işleve geçirilen yapısı. Varsa <xref:System.AppDomain> kaldırılırsa CLR işaretçi serbest bırakılmadan önce zaman uyumsuz işlem tamamlanana kadar bekler.  
  
## <a name="effect-on-the-runtime"></a>Çalışma zamanı üzerindeki etkisi  
 Bu mda'nın CLR üzerinde hiçbir etkisi vardı.  
  
## <a name="output"></a>Çıkış  
 Bu mda'nın bir örnek çıktı verilmiştir.  
  
 `An overlapped pointer (0x00ea3430) that was not allocated on the GC heap was passed via Pinvoke to the Win32 function 'WriteFile' in module 'KERNEL32.DLL'. If the AppDomain is shut down, this can cause heap corruption when the async I/O completes. The best solution is to pass a NativeOverlapped structure retrieved from a call to System.Threading.Overlapped.Pack(). If the AppDomain exits, the CLR will keep this structure alive and pinned until the I/O completes.`  
  
## <a name="configuration"></a>Yapılandırma  
  
```xml  
<mdaConfig>  
  <assistants>  
    <invalidOverlappedToPinvoke/>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [Yönetilen Hata Ayıklama Yardımcıları ile Hataları Tanılama](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
- [Birlikte Çalışma için Hazırlama](../../../docs/framework/interop/interop-marshaling.md)
