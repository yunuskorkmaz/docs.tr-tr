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
ms.openlocfilehash: 1f557cc370d5c6121b0ad9a4528bd75dcb70a93c
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2020
ms.locfileid: "77216284"
---
# <a name="invalidoverlappedtopinvoke-mda"></a>invalidOverlappedToPinvoke MDA
`invalidOverlappedToPinvoke` yönetilen hata ayıklama Yardımcısı (MDA), çöp toplama yığınında oluşturulmamış bir çakışan işaretçi belirli Win32 işlevlerine geçirildiğinde etkinleştirilir.  
  
> [!NOTE]
> Varsayılan olarak, bu MDA yalnızca platform çağırma çağrısı kodunuzda tanımlanmışsa ve hata ayıklayıcı her yöntemin Adamcode durumunu bildirirse etkinleştirilir. Bir hata ayıklayıcı (örneğin, hiçbir uzantısı olmayan MDbg. exe) Bu MDA ' i etkinleştirmeyecektir. Bu MDA, bir yapılandırma dosyası kullanılarak bu hata ayıklayıcılar için etkinleştirilebilir ve. mda. config dosyasında `(<invalidOverlappedToPinvoke enable="true" justMyCode="false"/>`) açıkça `justMyCode="false"`.  
  
## <a name="symptoms"></a>Belirtiler  
 Kilitlenmeler veya unexplainable yığın bozulmaları.  
  
## <a name="cause"></a>Nedeni  
 Çöp toplama yığınında oluşturulmamış bir çakışan işaretçi belirli işletim sistemi işlevlerine geçirilir.  
  
 Aşağıdaki tabloda bu MDA 'ın izlediği işlevler gösterilmektedir.  
  
|Modül|İşlev|  
|------------|--------------|  
|HTTPAPI. dll|`HttpReceiveHttpRequest`|  
|IpHlpApi.dll|`NotifyAddrChange`|  
|paketindeki|`ReadFile`|  
|paketindeki|`ReadFileEx`|  
|paketindeki|`WriteFile`|  
|paketindeki|`WriteFileEx`|  
|paketindeki|`ReadDirectoryChangesW`|  
|paketindeki|`PostQueuedCompletionStatus`|  
|MSWSock. dll|`ConnectEx`|  
|WS2_32.dll|`WSASend`|  
|WS2_32.dll|`WSASendTo`|  
|WS2_32.dll|`WSARecv`|  
|WS2_32.dll|`WSARecvFrom`|  
|MQRT. dll|`MQReceiveMessage`|  
  
 Çağrıyı yapan <xref:System.AppDomain>, bu durum için yığın bozulması olasılığı yüksektir. <xref:System.AppDomain> kaldırılırsa, uygulama kodu çakışan işaretçi için belleği serbest kalacak, işlem bittiğinde bozulmaya neden olur veya kod belleği sızdırdığınızda, daha sonra zorluklara neden olur.  
  
## <a name="resolution"></a>Çözüm  
 İşleve geçirilebilecek <xref:System.Threading.NativeOverlapped> yapısını almak için <xref:System.Threading.Overlapped.Pack%2A> metodunu çağırarak bir <xref:System.Threading.Overlapped> nesnesi kullanın. <xref:System.AppDomain> kaldırıldığında CLR, işaretçiyi boşaltmadan önce zaman uyumsuz işlem tamamlanana kadar bekler.  
  
## <a name="effect-on-the-runtime"></a>Çalışma zamanında etki  
 Bu MDA, CLR üzerinde hiçbir etkisi yoktu.  
  
## <a name="output"></a>Çıktı  
 Aşağıda, bu MDA 'ın çıkış örneği verilmiştir.  
  
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
- [Yönetilen Hata Ayıklama Yardımcıları ile Hataları Tanılama](diagnosing-errors-with-managed-debugging-assistants.md)
- [Birlikte Çalışma için Hazırlama](../interop/interop-marshaling.md)
