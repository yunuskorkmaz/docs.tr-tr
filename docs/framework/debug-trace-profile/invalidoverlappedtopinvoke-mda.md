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
ms.openlocfilehash: 7e9c7e1038591e5e8ea6f62b37ff4d02b2b6a9c5
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71052553"
---
# <a name="invalidoverlappedtopinvoke-mda"></a>invalidOverlappedToPinvoke MDA
`invalidOverlappedToPinvoke` Yönetilen hata ayıklama Yardımcısı (MDA), çöp toplama yığınında oluşturulmamış bir çakışan işaretçi belirli Win32 işlevlerine geçirildiğinde etkinleştirilir.  
  
> [!NOTE]
> Varsayılan olarak, bu MDA yalnızca platform çağırma çağrısı kodunuzda tanımlanmışsa ve hata ayıklayıcı her yöntemin Adamcode durumunu bildirirse etkinleştirilir. Bir hata ayıklayıcı (örneğin, hiçbir uzantısı olmayan MDbg. exe) Bu MDA ' i etkinleştirmeyecektir. Bu mda, bu hata ayıklayıcılar için bir yapılandırma dosyası kullanılarak ve. mda. config dosyasında `justMyCode="false"` `(<invalidOverlappedToPinvoke enable="true" justMyCode="false"/>`açıkça bir şekilde çalıştırılarak etkinleştirilebilir.  
  
## <a name="symptoms"></a>Belirtiler  
 Kilitlenmeler veya unexplainable yığın bozulmaları.  
  
## <a name="cause"></a>Sebep  
 Çöp toplama yığınında oluşturulmamış bir çakışan işaretçi belirli işletim sistemi işlevlerine geçirilir.  
  
 Aşağıdaki tabloda bu MDA 'ın izlediği işlevler gösterilmektedir.  
  
|Modül|İşlev|  
|------------|--------------|  
|HTTPAPI. dll|`HttpReceiveHttpRequest`|  
|IpHlpApi.dll|`NotifyAddrChange`|  
|Kernel32. dll|`ReadFile`|  
|Kernel32. dll|`ReadFileEx`|  
|Kernel32. dll|`WriteFile`|  
|Kernel32. dll|`WriteFileEx`|  
|Kernel32. dll|`ReadDirectoryChangesW`|  
|Kernel32. dll|`PostQueuedCompletionStatus`|  
|MSWSock. dll|`ConnectEx`|  
|WS2_32.dll|`WSASend`|  
|WS2_32.dll|`WSASendTo`|  
|WS2_32.dll|`WSARecv`|  
|WS2_32.dll|`WSARecvFrom`|  
|MQRT. dll|`MQReceiveMessage`|  
  
 Bu durum için yığın bozulması olasılığı yüksektir çünkü <xref:System.AppDomain> çağrının kaldırılması mümkün olur. <xref:System.AppDomain> Kaldırılırsa, uygulama kodu çakışan işaretçi için belleği serbest kalacak, işlem bittiğinde bozulmaya neden olur veya kod belleği sızıntısına neden olur ve daha sonra zorluklara yol açar.  
  
## <a name="resolution"></a>Çözüm  
 İşleve geçirilebilecek <xref:System.Threading.Overlapped> bir <xref:System.Threading.Overlapped.Pack%2A> Yapıalmakiçinyönteminiçağırarak<xref:System.Threading.NativeOverlapped> bir nesnesi kullanın. <xref:System.AppDomain> Kaldırıldığında, clr, işaretçiyi boşaltmadan önce zaman uyumsuz işlem tamamlanana kadar bekler.  
  
## <a name="effect-on-the-runtime"></a>Çalışma zamanında etki  
 Bu MDA, CLR üzerinde hiçbir etkisi yoktu.  
  
## <a name="output"></a>Çıkış  
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
