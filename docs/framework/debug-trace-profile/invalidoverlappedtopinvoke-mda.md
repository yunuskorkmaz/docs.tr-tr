---
title: invalidOverlappedToPinvoke MDA
description: .NET 'teki invalidOverlappedToPinvoke Managed hata ayıklama Yardımcısı 'nı (MDA), kilitlenme veya bir unexplainable yığın bozulması sırasında etkinleştirilebilecek şekilde gözden geçirin.
ms.date: 03/30/2017
helpviewer_keywords:
- overlapped pointers
- managed debugging assistants (MDAs), overlapped pointers
- invalid overlapped pointer to platform invoke
- InvalidOverlappedToPinvoke MDA
- MDAs (managed debugging assistants), overlapped pointers
- pointers, overlapped
ms.assetid: 28876047-58bd-4fed-9452-c7da346d67c0
ms.openlocfilehash: 162efd55bf636cf2e8698706bd011379f2f6f11f
ms.sourcegitcommit: 0edbeb66d71b8df10fcb374cfca4d731b58ccdb2
ms.contentlocale: tr-TR
ms.lasthandoff: 07/07/2020
ms.locfileid: "86051707"
---
# <a name="invalidoverlappedtopinvoke-mda"></a>invalidOverlappedToPinvoke MDA
`invalidOverlappedToPinvoke`Yönetilen hata ayıklama Yardımcısı (MDA), çöp toplama yığınında oluşturulmamış bir çakışan işaretçi belirli Win32 işlevlerine geçirildiğinde etkinleştirilir.  
  
> [!NOTE]
> Varsayılan olarak, bu MDA yalnızca platform çağırma çağrısı kodunuzda tanımlanmışsa ve hata ayıklayıcı her yöntemin Adamcode durumunu bildirirse etkinleştirilir. Bir hata ayıklayıcı (uzantısı olmayan MDbg.exe gibi), bu MDA ' i etkinleştirmez. Bu MDA, bu hata ayıklayıcılar için bir yapılandırma dosyası kullanılarak ve .mda.config dosyasında açıkça bir şekilde çalıştırılarak etkinleştirilebilir `justMyCode="false"` `(<invalidOverlappedToPinvoke enable="true" justMyCode="false"/>` .  
  
## <a name="symptoms"></a>Belirtiler  
 Kilitlenmeler veya unexplainable yığın bozulmaları.  
  
## <a name="cause"></a>Nedeni  
 Çöp toplama yığınında oluşturulmamış bir çakışan işaretçi belirli işletim sistemi işlevlerine geçirilir.  
  
 Aşağıdaki tabloda bu MDA 'ın izlediği işlevler gösterilmektedir.  
  
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
  
 Bu durum için yığın bozulması olasılığı yüksektir çünkü çağrının kaldırılması mümkün olur <xref:System.AppDomain> . Kaldırılırsa <xref:System.AppDomain> , uygulama kodu çakışan işaretçi için belleği serbest kalacak, işlem bittiğinde bozulmaya neden olur veya kod belleği sızıntısına neden olur ve daha sonra zorluklara yol açar.  
  
## <a name="resolution"></a>Çözüm  
 <xref:System.Threading.Overlapped> <xref:System.Threading.Overlapped.Pack%2A> İşleve geçirilebilecek bir yapı almak için yöntemini çağırarak bir nesnesi kullanın <xref:System.Threading.NativeOverlapped> . <xref:System.AppDomain>Kaldırıldığında, clr, işaretçiyi boşaltmadan önce zaman uyumsuz işlem tamamlanana kadar bekler.  
  
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
- [Birlikte Çalışma Hazırlama](../interop/interop-marshaling.md)
