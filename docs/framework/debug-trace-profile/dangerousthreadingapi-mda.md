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
ms.openlocfilehash: d3fe7d11657c2f9edd1fea7ff639f878f993d6b1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174777"
---
# <a name="dangerousthreadingapi-mda"></a>dangerousThreadingAPI MDA
Yönetilen `dangerousThreadingAPI` hata ayıklama yardımcısı (MDA) <xref:System.Threading.Thread.Suspend%2A?displayProperty=nameWithType> yöntem geçerli iş parçacığı dışında bir iş parçacığı çağrıldığında etkinleştirilir.  
  
## <a name="symptoms"></a>Belirtiler  
 Bir uygulama yanıt vermiyor veya süresiz olarak asılı. Sistem veya uygulama verileri geçici olarak veya bir uygulama kapatıldıktan sonra bile öngörülemeyen bir durumda bırakılabilir. Bazı işlemler beklendiği gibi tamamlanınmıyor.  
  
 Belirtiler büyük ölçüde soruna bağlı rasgelelik nedeniyle değişebilir.  
  
## <a name="cause"></a>Nedeni  
 Bir iş <xref:System.Threading.Thread.Suspend%2A> parçacığı, yöntemi kullanarak başka bir iş parçacığı tarafından eş senkronize olarak askıya alınır. Bir işlemin ortasında olabilecek başka bir iş parçacığının ne zaman askıya alınabileceğini belirlemenin bir yolu yoktur. İş parçacığının askıya alınması, verilerin bozulmasına veya değişmezlerin kırılması ile sonuçlanabilir. Bir iş parçacığı askıya alınmış bir duruma yerleştirilir <xref:System.Threading.Thread.Resume%2A> ve yöntemi kullanarak devam asla, uygulama süresiz olarak asmak ve büyük olasılıkla uygulama verilerine zarar verebilir. Bu yöntemler eski olarak işaretlenmiştir.  
  
 Senkronizasyon ilkel hedef iş parçacığı tarafından tutulursa, onlar süspansiyon sırasında tutulur. Bu kilitlenmelere yol açabilir başka bir iş <xref:System.Threading.Thread.Suspend%2A>parçacığı, örneğin iş parçacığı gerçekleştiren , ilkel bir kilit elde etmek için girişimi. Bu durumda, sorun bir kilitlenme olarak kendini gösterir.  
  
## <a name="resolution"></a>Çözüm  
 Kullanımı <xref:System.Threading.Thread.Suspend%2A> ve gerektiren tasarımlar <xref:System.Threading.Thread.Resume%2A>kaçının. İş parçacıkları arasındaki işbirliği için, " , <xref:System.Threading.Monitor> <xref:System.Threading.ReaderWriterLock>, <xref:System.Threading.Mutex>, veya `lock` C# deyimi gibi senkronizasyon ilkellerini kullanın. Bu yöntemleri kullanmanız gerekiyorsa, zaman penceresini azaltın ve iş parçacığı askıya alınmış durumdayken çalıştıran kod miktarını en aza indirin.  
  
## <a name="effect-on-the-runtime"></a>Çalışma Süresi üzerindeki etkisi  
 Bu MDA'nın CLR üzerinde hiçbir etkisi yoktur. Yalnızca tehlikeli iş parçacığı işlemleriyle ilgili verileri bildirir.  
  
## <a name="output"></a>Çıktı  
 MDA, etkinleştirilmesine neden olan tehlikeli iş parçacığı yöntemini tanımlar.  
  
## <a name="configuration"></a>Yapılandırma  
  
```xml  
<mdaConfig>  
  <assistants>  
    <dangerousThreadingAPI />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneği, <xref:System.Threading.Thread.Suspend%2A> `dangerousThreadingAPI`.'ın etkinleştirilmesine neden olan yönteme yapılan bir çağrıyı gösterir.  
  
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
