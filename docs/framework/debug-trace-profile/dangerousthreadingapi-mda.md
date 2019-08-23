---
title: dangerousThreadingAPI MDA
ms.date: 03/30/2017
helpviewer_keywords:
- suspending threads
- DangerousThreadingAPI MDA
- managed debugging assistants (MDAs), dangerous threading operations
- threading [.NET Framework], suspending
- MDAs (managed debugging assistants), dangerous threading operations
- Suspend method
- threading [.NET Framework], managed debugging assistants
ms.assetid: 3e5efbc5-92e4-4229-b31f-ce368a1adb96
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 9d635100c4e8214a7a8659c2d3e4da61825cf243
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69966300"
---
# <a name="dangerousthreadingapi-mda"></a>dangerousThreadingAPI MDA
Yönetilen hata ayıklama Yardımcısı (MDA), <xref:System.Threading.Thread.Suspend%2A?displayProperty=nameWithType> yöntem geçerli iş parçacığı dışında bir iş parçacığında çağrıldığında etkinleştirilir. `dangerousThreadingAPI`  
  
## <a name="symptoms"></a>Belirtiler  
 Bir uygulama süresiz olarak yanıt vermemeye başlıyor veya askıda kalıyor. Sistem veya uygulama verileri, geçici olarak veya bir uygulama kapatıldıktan sonra bile öngörülemeyen bir durumda kalabilir. Bazı işlemler beklendiği gibi tamamlanmıyor.  
  
 Belirtiler, soruna bağlı rasgelelik nedeniyle büyük ölçüde farklılık gösterebilir.  
  
## <a name="cause"></a>Sebep  
 İş parçacığı, <xref:System.Threading.Thread.Suspend%2A> yöntemi kullanılarak başka bir iş parçacığı tarafından zaman uyumsuz olarak askıya alındı. Bir işlemin ortasında olabilecek başka bir iş parçacığını askıya almanın ne zaman güvenli olduğunu belirlemenin bir yolu yoktur. İş parçacığını askıya almak, verilerin bozulmasına veya ınvarıant 'ların bozulmasına yol açabilir. Bir iş parçacığının askıya alınma durumuna yerleştirilmesi ve <xref:System.Threading.Thread.Resume%2A> yöntemi kullanılarak hiçbir şekilde sürdürülmemesi, uygulamanın süresiz olarak askıda kalması ve muhtemelen uygulama verilerine zarar verebiliyor olması gerekir. Bu yöntemler artık kullanılmıyor olarak işaretlendi.  
  
 Eşitleme temelleri hedef iş parçacığı tarafından tutuluyorsa, askıya alma sırasında tutuluyor olarak kalırlar. Bu, kilitlenmeyle <xref:System.Threading.Thread.Suspend%2A>ilgili başka bir iş parçacığı olmalıdır, örneğin iş parçacığı, temel üzerinde bir kilit elde etmeye çalışır. Bu durumda, sorun kendi kendine bir kilitlenme olarak bildirim gösterir.  
  
## <a name="resolution"></a>Çözüm  
 <xref:System.Threading.Thread.Suspend%2A> Ve<xref:System.Threading.Thread.Resume%2A>kullanımını gerektiren tasarımlardan kaçının. İş parçacıkları arasındaki ortak işlem için,,, <xref:System.Threading.Monitor>veya C# `lock` deyimleri gibi <xref:System.Threading.ReaderWriterLock>eşitleme <xref:System.Threading.Mutex>temel öğelerini kullanın. Bu yöntemleri kullanmanız gerekiyorsa, zaman penceresini küçültün ve iş parçacığı askıya alınma durumundayken yürütülen kod miktarını en aza indirin.  
  
## <a name="effect-on-the-runtime"></a>Çalışma zamanında etki  
 Bu MDA, CLR üzerinde hiçbir etkisi yoktur. Yalnızca tehlikeli iş parçacığı oluşturma işlemleriyle ilgili verileri raporlar.  
  
## <a name="output"></a>Çıkış  
 MDA, etkinleştirilmesinin nedeni olan tehlikeli iş parçacığı yöntemini tanımlar.  
  
## <a name="configuration"></a>Yapılandırma  
  
```xml  
<mdaConfig>  
  <assistants>  
    <dangerousThreadingAPI />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneği, <xref:System.Threading.Thread.Suspend%2A> `dangerousThreadingAPI`etkinleştirmesine neden olan yöntemine yapılan çağrıyı gösterir.  
  
```csharp
using System.Threading;  
void FireMda()  
{  
Thread t = new Thread(delegate() { Thread.Sleep(1000); });  
    t.Start();  
    // The following line activates the MDA.  
    t.Suspend();   
    t.Resume();  
    t.Join();  
}  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Threading.Thread>
- [Yönetilen Hata Ayıklama Yardımcıları ile Hataları Tanılama](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
- [lock Deyimi](../../csharp/language-reference/keywords/lock-statement.md)
