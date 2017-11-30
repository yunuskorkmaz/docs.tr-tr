---
title: asynchronousThreadAbort MDA
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- asynchronous thread aborts
- AsynchronousThreadAbort MDA
- managed debugging assistants (MDAs), asynchronous thread aborts
- threading [.NET Framework], managed debugging assistants
- MDAs (managed debugging assistants), asynchronous thread aborts
ms.assetid: 9ebe40b2-d703-421e-8660-984acc42bfe0
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 6f7bfee4375a14a4456493333e65a953d406c732
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="asynchronousthreadabort-mda"></a>asynchronousThreadAbort MDA
`asynchronousThreadAbort` Yönetilen hata ayıklama Yardımcısı (MDA) başka bir iş parçacığı içinde zaman uyumsuz iptal tanıtmak bir iş parçacığı çalıştığında etkinleştirilir. Zaman uyumlu iş parçacığı iptalleri değil etkinleştirme `asynchronousThreadAbort` MDA.

## <a name="symptoms"></a>Belirtiler
 Bir uygulama işlenmeyen bir çöküyor <xref:System.Threading.ThreadAbortException> ana uygulama iş parçacığı durduruldu zaman. Uygulamayı çalıştırmak devam etmek için olsaydı, sonuçları kilitlenen, büyük olasılıkla daha fazla veri bozulmasına neden olur uygulamadan daha zayıf olabilir.

 Atomik olma amacını işlemleri uygulama verilerini öngörülemeyen durumda bırakarak kısmi tamamlandıktan sonra büyük olasılıkla kesilmiş. A <xref:System.Threading.ThreadAbortException> genellikle içinden bir özel durum beklenmiyor çıkabilecek yerlerde kod yürütmeyi rasgele gibi görünen noktalarından oluşturulabilir. Kod bozuk durumda kaynaklanan böyle bir özel durum işleme yeteneği olan olmayabilir.

 Belirtiler yaygın olarak sorun için devralınan rastgele nedeniyle değişebilir.

## <a name="cause"></a>Sebep
 Adlı tek bir iş parçacığı kodda <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> bir zaman uyumsuz iş parçacığı durdurma tanıtmak için bir hedef iş parçacığı üzerinde yöntemi. Çağrı yapar kodu iş parçacığı durdurma zaman uyumsuz olduğundan <xref:System.Threading.Thread.Abort%2A> iptal etme işlemi hedefinin daha farklı bir iş parçacığı üzerinde çalışıyor. Zaman uyumlu iş parçacığı iptalleri neden olmaz bir sorun olduğundan iş parçacığı gerçekleştirme <xref:System.Threading.Thread.Abort%2A> uygulama durumu olduğu tutarlı yalnızca bir güvenli denetim noktası yapmış olmanız.

 Hedef iş parçacığının yürütme öngörülemeyen noktalarında işlendiğinden zaman uyumsuz iş parçacığı iptalleri bir sorun var. Bunu önlemek için bu şekilde iptal bir iş parçacığı üzerinde çalıştırmak için yazılan kod işlemeye gerekir bir <xref:System.Threading.ThreadAbortException> uygulama verilerinin tutarlı bir duruma geri getirir dikkat ederek kodunun neredeyse her satırı. Kod bu sorunla aklınızda yazılacak veya tüm olası durumlarda karşı korur kod yazmaya beklediğiniz gerçekçi değildir.

 Yönetilmeyen kod çağrılarını ve `finally` blokları değil durdurulacak zaman uyumsuz olarak ancak hemen Bu kategorilerden birini Çıkışta.

 Neden sorunu devralınmış rastgele nedeniyle belirlemek zor olabilir.

## <a name="resolution"></a>Çözüm
 Zaman uyumsuz iş parçacığı iptalleri kullanılmasını gerektiren kod tasarım kaçının. Çeşitli yaklaşımlar Kesinti yapılan bir çağrı gerektirmeyen hedef iş parçacığı için daha uygun <xref:System.Threading.Thread.Abort%2A>. Ortak bir özelliği gibi bir mekanizma tanıtmak için güvenli olduğundan, kesme istemek için hedef iş parçacığı işaret eder. Hedef iş parçacığı güvenli belirli kontrol noktaları, sinyal denetler. Kesme istendi belirlerse, düzgün bir şekilde kapanabilir.

## <a name="effect-on-the-runtime"></a>Çalışma zamanı etkisi
 Bu MDA CLR üzerinde etkisi yoktur. Yalnızca veri zaman uyumsuz iş parçacığı iptalleri hakkında raporlar.

## <a name="output"></a>Çıkış
 MDA durdurma ve durdurma hedefidir iş parçacığı kimliği gerçekleştiren iş parçacığı kimliği bildirir. Bu zaman uyumsuz iptalleri sınırlı olduğundan bu asla aynı olacaktır.

## <a name="configuration"></a>Yapılandırma

```xml
<mdaConfig>
  <assistants>
    <asynchronousThreadAbort />
  </assistants>
</mdaConfig>
```

## <a name="example"></a>Örnek
 Etkinleştirme `asynchronousThreadAbort` MDA gerektirir sadece bir çağrı <xref:System.Threading.Thread.Abort%2A> ayrı çalışan iş parçacığı üzerinde. İş parçacığı içeriğini durdurma tarafından herhangi rastgele bir noktada kesilebilir daha karmaşık işlemleri kümesi olan işlevi başlatırsanız sonuçları göz önünde bulundurun.

```csharp
using System.Threading;
void FireMda()
{
    Thread t = new Thread(delegate() { Thread.Sleep(1000); });
    t.Start();
    // The following line activates the MDA.
    t.Abort();
    t.Join();
}
```

## <a name="see-also"></a>Ayrıca Bkz.
 <xref:System.Threading.Thread>[Yönetilen hata ayıklama Yardımcıları ile hataları tanılama](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
