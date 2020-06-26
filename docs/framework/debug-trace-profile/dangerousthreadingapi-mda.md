---
title: dangerousThreadingAPI MDA
description: Geçerli iş parçacığından farklı bir iş parçacığında Thread. Suspend çağrıldığında etkinleştirilen dangerousThreadingAPI Managed hata ayıklama Yardımcısı 'nı (MDA) gözden geçirin.
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
ms.openlocfilehash: 9069ccb6f106c83db94f88bc464bc0888d28586c
ms.sourcegitcommit: a2c8b19e813a52b91facbb5d7e3c062c7188b457
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/26/2020
ms.locfileid: "85416011"
---
# <a name="dangerousthreadingapi-mda"></a>dangerousThreadingAPI MDA
`dangerousThreadingAPI`Yönetilen hata ayıklama Yardımcısı (MDA), <xref:System.Threading.Thread.Suspend%2A?displayProperty=nameWithType> yöntem geçerli iş parçacığı dışında bir iş parçacığında çağrıldığında etkinleştirilir.  
  
## <a name="symptoms"></a>Belirtiler  
 Bir uygulama süresiz olarak yanıt vermemeye başlıyor veya askıda kalıyor. Sistem veya uygulama verileri, geçici olarak veya bir uygulama kapatıldıktan sonra bile öngörülemeyen bir durumda kalabilir. Bazı işlemler beklendiği gibi tamamlanmıyor.  
  
 Belirtiler, soruna bağlı rasgelelik nedeniyle büyük ölçüde farklılık gösterebilir.  
  
## <a name="cause"></a>Nedeni  
 İş parçacığı, yöntemi kullanılarak başka bir iş parçacığı tarafından zaman uyumsuz olarak askıya alındı <xref:System.Threading.Thread.Suspend%2A> . Bir işlemin ortasında olabilecek başka bir iş parçacığını askıya almanın ne zaman güvenli olduğunu belirlemenin bir yolu yoktur. İş parçacığını askıya almak, verilerin bozulmasına veya ınvarıant 'ların bozulmasına yol açabilir. Bir iş parçacığının askıya alınma durumuna yerleştirilmesi ve yöntemi kullanılarak hiçbir şekilde sürdürülmemesi <xref:System.Threading.Thread.Resume%2A> , uygulamanın süresiz olarak askıda kalması ve muhtemelen uygulama verilerine zarar verebiliyor olması gerekir. Bu yöntemler artık kullanılmıyor olarak işaretlendi.  
  
 Eşitleme temelleri hedef iş parçacığı tarafından tutuluyorsa, askıya alma sırasında tutuluyor olarak kalırlar. Bu, kilitlenmeyle ilgili başka bir iş parçacığı olmalıdır, örneğin iş parçacığı, <xref:System.Threading.Thread.Suspend%2A> temel üzerinde bir kilit elde etmeye çalışır. Bu durumda, sorun kendi kendine bir kilitlenme olarak bildirim gösterir.  
  
## <a name="resolution"></a>Çözüm  
 Ve kullanımını gerektiren tasarımlardan kaçının <xref:System.Threading.Thread.Suspend%2A> <xref:System.Threading.Thread.Resume%2A> . İş parçacıkları arasındaki ortak işlem için,,, <xref:System.Threading.Monitor> <xref:System.Threading.ReaderWriterLock> <xref:System.Threading.Mutex> veya C# deyimleri gibi eşitleme temel öğelerini kullanın `lock` . Bu yöntemleri kullanmanız gerekiyorsa, zaman penceresini küçültün ve iş parçacığı askıya alınma durumundayken yürütülen kod miktarını en aza indirin.  
  
## <a name="effect-on-the-runtime"></a>Çalışma zamanında etki  
 Bu MDA, CLR üzerinde hiçbir etkisi yoktur. Yalnızca tehlikeli iş parçacığı oluşturma işlemleriyle ilgili verileri raporlar.  
  
## <a name="output"></a>Çıktı  
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
 Aşağıdaki kod örneği <xref:System.Threading.Thread.Suspend%2A> , etkinleştirmesine neden olan yöntemine yapılan çağrıyı gösterir `dangerousThreadingAPI` .  
  
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
- [Yönetilen Hata Ayıklama Yardımcıları ile Hataları Tanılama](diagnosing-errors-with-managed-debugging-assistants.md)
- [lock Deyimi](../../csharp/language-reference/keywords/lock-statement.md)
