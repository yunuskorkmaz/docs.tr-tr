---
title: dangerousThreadingAPI MDA
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- suspending threads
- DangerousThreadingAPI MDA
- managed debugging assistants (MDAs), dangerous threading operations
- threading [.NET Framework], suspending
- MDAs (managed debugging assistants), dangerous threading operations
- Suspend method
- threading [.NET Framework], managed debugging assistants
ms.assetid: 3e5efbc5-92e4-4229-b31f-ce368a1adb96
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 4b7c4e7f5612cb6a46f16b6e42327e8430d548e3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="dangerousthreadingapi-mda"></a>dangerousThreadingAPI MDA
`dangerousThreadingAPI` Yönetilen hata ayıklama Yardımcısı (MDA) etkinleştirilmiş olduğunda <xref:System.Threading.Thread.Suspend%2A?displayProperty=nameWithType> yöntemi, geçerli iş parçacığı dışında bir iş parçacığında çağrılır.  
  
## <a name="symptoms"></a>Belirtiler  
 Bir uygulama yanıt vermiyor veya süresiz olarak askıda kalır. Sistem veya uygulama verileri, geçici veya uygulamanın bile kapatıldı sonra öngörülemeyen durumda kalmayabilir. Beklendiği gibi bazı işlemler Tamamlanıyor değil.  
  
 Belirtiler yaygın olarak sorun için devralınan rastgele nedeniyle değişebilir.  
  
## <a name="cause"></a>Sebep  
 Bir iş parçacığı başka bir iş parçacığı kullanarak zaman uyumsuz olarak askıya <xref:System.Threading.Thread.Suspend%2A> yöntemi. Bir işlem gerçekleştiriyor olabilir. başka bir iş parçacığı askıya almak güvenli olduğunda belirlemek için bir yolu yoktur. İş parçacığı askıya alma, veri bozulması veya invariants sonu neden olabilir. Bir iş parçacığı bir askıya alınır ve hiçbir zaman sürdürüldü kullanarak yerleştirilmelidir <xref:System.Threading.Thread.Resume%2A> yöntemi, uygulama süresiz olarak askıda ve büyük olasılıkla uygulama verileri zarar verebilir. Bu yöntemleri geçersiz olarak işaretlendi.  
  
 Eşitleme temelleri hedef iş parçacığı tarafından tutuluyor bunlar sırasında askıya tutulan kalır. Bu başka bir iş parçacığı, örneğin iş parçacığı gerçekleştirme kilitlenmeye neden olabilir <xref:System.Threading.Thread.Suspend%2A>, basit bir Kilitle girişimi. Bu durumda, sorunun bir kilitlenme ortaya çıkmaktadır.  
  
## <a name="resolution"></a>Çözüm  
 Kullanılmasını tasarımları kaçının <xref:System.Threading.Thread.Suspend%2A> ve <xref:System.Threading.Thread.Resume%2A>. Eşitleme temelleri iş parçacıkları arasında işbirliği için gibi kullandığınız <xref:System.Threading.Monitor>, <xref:System.Threading.ReaderWriterLock>, <xref:System.Threading.Mutex>, veya C# `lock` deyimi. Bu yöntemleri kullanmanız gerekiyorsa olan zaman penceresini azaltmak ve iş parçacığı askıya alınmış durumdayken, yürütülen kod miktarını en aza indirir.  
  
## <a name="effect-on-the-runtime"></a>Çalışma zamanı etkisi  
 Bu MDA CLR üzerinde etkisi yoktur. Yalnızca veri tehlikeli iş parçacığı oluşturma işlemleri hakkında raporlar.  
  
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
 Aşağıdaki kod örneğinde yapılan bir çağrı gösterilmektedir <xref:System.Threading.Thread.Suspend%2A> etkinleştirmeyi neden yöntemi `dangerousThreadingAPI`.  
  
```  
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
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Threading.Thread>  
 [Yönetilen Hata Ayıklama Yardımcıları ile Hataları Tanılama](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)  
 [lock Deyimi](~/docs/csharp/language-reference/keywords/lock-statement.md)
