---
title: asynchronousThreadAbort MDA
ms.date: 03/30/2017
helpviewer_keywords:
- asynchronous thread aborts
- AsynchronousThreadAbort MDA
- managed debugging assistants (MDAs), asynchronous thread aborts
- threading [.NET Framework], managed debugging assistants
- MDAs (managed debugging assistants), asynchronous thread aborts
ms.assetid: 9ebe40b2-d703-421e-8660-984acc42bfe0
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 08f67ad363d0bd3efcc7a1eeedd1f48d3bae9407
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61875712"
---
# <a name="asynchronousthreadabort-mda"></a>asynchronousThreadAbort MDA
`asynchronousThreadAbort` Yönetilen hata ayıklama Yardımcısı (MDA), başka bir diziye bir zaman uyumsuz iptal tanıtmak bir iş parçacığı girişiminde bulunduğunda etkinleştirilir. Zaman uyumlu iş parçacığı iptalleri değil etkinleştirme `asynchronousThreadAbort` MDA.

## <a name="symptoms"></a>Belirtiler
 İşlenmemiş bir uygulama kilitlenmeleri <xref:System.Threading.ThreadAbortException> zaman ana uygulama iş parçacığı durduruldu. Yürütmeye devam etmek için uygulamayı olsaydı, sonuçları kilitlenen, büyük olasılıkla daha fazla veri bozulmasına neden olur uygulamadan daha kötü olabilir.

 İşlemler atomik olacak şekilde tasarlanmış uygulama verileri öngörülemeyen durumda bırakarak kısmi tamamlandıktan sonra büyük olasılıkla kesilmiş. A <xref:System.Threading.ThreadAbortException> genellikle içinden bir özel durum beklenmiyor çıkabilecek yerlerde kod yürütülmesi görünüşte rastgele noktalarından oluşturulabilir. Kod, bozuk bir durumda kaynaklanan böyle bir özel durum işleme kapasitesine sahip olmayabilir.

 Belirtiler yaygın olarak sorun için devralınmış rastgeleliğinin nedeniyle değişebilir.

## <a name="cause"></a>Sebep
 Kod olarak adlandırılan bir iş parçacığındaki <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> yöntemi bir iş parçacığında zaman uyumsuz iş parçacığı iptal tanıtmak için hedef. Kod, çağrı yapar çünkü iş parçacığı iptal zaman uyumsuz <xref:System.Threading.Thread.Abort%2A> durdurma işleminin hedefi değerinden farklı bir iş parçacığı üzerinde çalışıyor. Zaman uyumlu iş parçacığı iptalleri neden bir sorun nedeniyle iş parçacığı gerçekleştirme <xref:System.Threading.Thread.Abort%2A> burada uygulama durumunu tutarlı olduğundan yalnızca bir güvenli denetim noktası yapmış olmanız.

 Hedef iş parçacığının yürütme öngörülemeyen noktalarında işlendiğinden zaman uyumsuz iş parçacığı iptalleri bir sorun var. Bunu önlemek için bu şekilde iptal bir iş parçacığı üzerinde çalışacak şekilde yazılmış kod işlemeye gerekir bir <xref:System.Threading.ThreadAbortException> uygulama verilerinin tutarlı bir duruma geri put dikkat ederek kodun neredeyse her satırı. Bu sorunla aklınızda yazılacak veya tüm olası koşullar karşı koruyan kod yazmak için kod beklenir gerçekçi değildir.

 Yönetilmeyen kodu çağırıyor ve `finally` blokları değil durdurulacak zaman uyumsuz olarak ancak hemen kategorilerine birinden Çıkışta.

 Nedeni sorunu devralınan rastgeleliğinin nedeniyle saptamak zor olabilir.

## <a name="resolution"></a>Çözüm
 Zaman uyumsuz iş parçacığı iptalleri kullanılmasını gerektiren tasarım kodu özen gösterin. Çeşitli yaklaşımlar daha uygun bir çağrı gerektirmeyen hedef iş parçacığı kesintinin <xref:System.Threading.Thread.Abort%2A>. Ortak bir özellik gibi bir mekanizma tanıtmak için en güvenli olanıdır, hedef iş parçacığının isteği bir kesme sinyalini verir. Hedef iş parçacığı güvenli belirli kontrol noktaları, sinyal denetler. Bir kesme istendi karşılaşırsa, düzgün bir şekilde kapanabilir.

## <a name="effect-on-the-runtime"></a>Çalışma zamanı üzerindeki etkisi
 Bu mda'nın CLR üzerinde etkisi yoktur. Yalnızca veri zaman uyumsuz iş parçacığı iptalleri hakkında raporlar.

## <a name="output"></a>Çıkış
 MDA durdurma ve iptal işleminin hedefi olan iş parçacığının kimliği gerçekleştiren iş parçacığının kimliği bildirir. Bu zaman uyumsuz iptali için sınırlı olduğundan bunlar hiçbir zaman aynı olmaz.

## <a name="configuration"></a>Yapılandırma

```xml
<mdaConfig>
  <assistants>
    <asynchronousThreadAbort />
  </assistants>
</mdaConfig>
```

## <a name="example"></a>Örnek
 Etkinleştirme `asynchronousThreadAbort` MDA, yalnızca bir çağrı gerektirir <xref:System.Threading.Thread.Abort%2A> ayrı bir çalışan iş parçacığı üzerinde. Rastgele herhangi bir noktada iptal tarafından yarıda kesilebilir daha karmaşık işlemleri bir dizi olan işlevi iş parçacığının içeriği başlatırsanız, sonuçları göz önünde bulundurun.

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

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Threading.Thread>
- [Yönetilen Hata Ayıklama Yardımcıları ile Hataları Tanılama](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
