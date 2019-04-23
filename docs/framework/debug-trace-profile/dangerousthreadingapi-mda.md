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
ms.openlocfilehash: 46b0add67fc6bc139ef02e09190670870749d4c7
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59218309"
---
# <a name="dangerousthreadingapi-mda"></a>dangerousThreadingAPI MDA
`dangerousThreadingAPI` Yönetilen hata ayıklama Yardımcısı (MDA) etkinleştirilmiş olduğunda <xref:System.Threading.Thread.Suspend%2A?displayProperty=nameWithType> geçerli iş parçacığı dışında bir iş parçacığında yöntemi çağrılır.  
  
## <a name="symptoms"></a>Belirtiler  
 Uygulama yanıt vermiyor veya süresiz olarak askıda kalır. Sistem veya uygulama verileri, geçici veya bir uygulama bile kapatıldı sonra öngörülemeyen durumda kalmayabilir. Beklendiği gibi bazı işlemler Tamamlanıyor değil.  
  
 Belirtiler yaygın olarak sorun için devralınmış rastgeleliğinin nedeniyle değişebilir.  
  
## <a name="cause"></a>Sebep  
 Bir iş parçacığı başka bir iş parçacığı kullanarak zaman uyumsuz olarak askıya <xref:System.Threading.Thread.Suspend%2A> yöntemi. Ortasında bir işlem olabilir. başka bir iş parçacığını askıya alma güvenli olduğunda belirlemek için hiçbir yolu yoktur. İş parçacığını askıya alma, veri bozulması veya okuduğunuzda sonlandırılmasını neden olabilir. Bir iş parçacığı bir askıya alınma durumuna ve hiçbir zaman sürdürüldü kullanarak yerleştirilmesi gereken <xref:System.Threading.Thread.Resume%2A> yöntemi, uygulama süresiz olarak askıda ve büyük olasılıkla uygulama verileri zarar verebilir. Bu yöntemler eski olarak işaretlendi.  
  
 Eşitleme temellerine hedef iş parçacığı tarafından tutulan, askıya alma sırasında tutulan kalırlar. Bu başka bir iş parçacığı, örneğin iş parçacığı gerçekleştirmek için kilitlenmeleri açabilir <xref:System.Threading.Thread.Suspend%2A>, temel bir kilidi edinmeye çalışın. Bu durumda, sorunu Kilitlenme ortaya çıkmaktadır.  
  
## <a name="resolution"></a>Çözüm  
 Kullanımını zorunlu tasarımları önlemek <xref:System.Threading.Thread.Suspend%2A> ve <xref:System.Threading.Thread.Resume%2A>. İş parçacıkları arasında işbirliği için eşitleme temellerine gibi kullanın <xref:System.Threading.Monitor>, <xref:System.Threading.ReaderWriterLock>, <xref:System.Threading.Mutex>, veya C# `lock` deyimi. Bu yöntemler kullanmanız gerekirse, zaman penceresi azaltın ve iş parçacığının askıya alınmış durumda olduğu sürece yürütür kod miktarını en aza indirir.  
  
## <a name="effect-on-the-runtime"></a>Çalışma zamanı üzerindeki etkisi  
 Bu mda'nın CLR üzerinde etkisi yoktur. Yalnızca veri tehlikeli iş parçacığı oluşturma işlemleri hakkında raporlar.  
  
## <a name="output"></a>Çıkış  
 MDA etkinleştirilmesi neden tehlikeli iş parçacığı yöntemi tanımlar.  
  
## <a name="configuration"></a>Yapılandırma  
  
```xml  
<mdaConfig>  
  <assistants>  
    <dangerousThreadingAPI />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneği için bir çağrı gösterir <xref:System.Threading.Thread.Suspend%2A> etkinleştirilmesinden neden yöntemi `dangerousThreadingAPI`.  
  
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
- [lock Deyimi](~/docs/csharp/language-reference/keywords/lock-statement.md)
