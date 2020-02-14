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
ms.openlocfilehash: d0c78e6d52ae4a5b3a24e0bb4278b2e8a1b98751
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2020
ms.locfileid: "77217587"
---
# <a name="asynchronousthreadabort-mda"></a>asynchronousThreadAbort MDA
`asynchronousThreadAbort` yönetilen hata ayıklama Yardımcısı (MDA), bir iş parçacığı başka bir iş parçacığına zaman uyumsuz bir iptal yapmayı denediğinde etkinleştirilir. Zaman uyumlu iş parçacığı durdurulduğunda `asynchronousThreadAbort` MDA ' i etkinleştirmeyin.

## <a name="symptoms"></a>Belirtiler
 Ana uygulama iş parçacığı iptal edildiğinde, bir uygulama işlenmemiş bir <xref:System.Threading.ThreadAbortException> kilitleniyor. Uygulamanın yürütülmeye devam etmesi gerekiyorsa, sonuçlar uygulama kilitlenmesinin ardından büyük olasılıkla daha fazla veri bozulmasına neden olabilir.

 Atomik olması amaçlanan işlemler kısmen tamamlandığında kesintiye uğratıldıktan sonra, uygulama verileri öngörülemeyen bir durumda bırakılır. Bir <xref:System.Threading.ThreadAbortException>, genellikle bir özel durumun meydana gelmesi beklenmediği yerlerde kodun yürütülmesindeki düzensiz rastgele noktalardan oluşturulabilir. Kod böyle bir özel durumu işleyemeyebilir, bu durum bozuk bir duruma neden olabilir.

 Belirtiler, soruna bağlı rasgelelik nedeniyle büyük ölçüde farklılık gösterebilir.

## <a name="cause"></a>Nedeni
 Bir iş parçacığında, zaman uyumsuz bir iş parçacığı iptali tanıtmak için <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> yöntemi olarak adlandırılan kod. <xref:System.Threading.Thread.Abort%2A> çağrısını yapan kod, durdurma işleminin hedefinden farklı bir iş parçacığında çalıştığından iş parçacığı iptali zaman uyumsuzdur. <xref:System.Threading.Thread.Abort%2A> gerçekleştiren iş parçacığının yalnızca uygulama durumunun tutarlı olduğu güvenli bir denetim noktasında yapılması gerektiğinden, zaman uyumlu iş parçacığı iptal etmek soruna neden olmamalıdır.

 Zaman uyumsuz thread, hedef iş parçacığının yürütmesindeki öngörülemeyen noktalarda işlendiği için bir sorun oluştu. Bunu önlemek için, bu şekilde durdurulmuş olabilecek bir iş parçacığında çalışmak üzere yazılan kodun, neredeyse her kod satırında bir <xref:System.Threading.ThreadAbortException> işlemesi ve uygulama verilerinin tutarlı bir duruma geri alınmasına dikkat etmeniz gerekir. Kodun bu sorun ile yazılması veya tüm olası koşullara karşı koruyan bir kod yazmak için gerçekçi değildir.

 Yönetilmeyen koda yapılan çağrılar ve `finally` blokları zaman uyumsuz olarak durdurulmayacak, ancak bu kategorilerden birinden çıkmadan hemen sonra olmayacaktır.

 Sorunun, soruna bağlı rastgele bir durum nedeniyle belirlenmesi zor olabilir.

## <a name="resolution"></a>Çözüm
 Zaman uyumsuz iş parçacığı iptal durumu kullanımını gerektiren kod tasarımını önleyin. <xref:System.Threading.Thread.Abort%2A>çağrısı gerektirmeyen bir hedef iş parçacığının kesintiye uğramasını sağlamak için birkaç yaklaşım daha uygundur. En güvenli, bir kesme istemek için hedef iş parçacığına işaret eden ortak bir özellik gibi bir mekanizma tanıtmaktır. Hedef iş parçacığı belirli güvenli denetim noktalarında sinyali denetler. Bir kesmenin istenmiş olduğunu fark ederseniz, düzgün bir şekilde kapatılabilir.

## <a name="effect-on-the-runtime"></a>Çalışma zamanında etki
 Bu MDA, CLR üzerinde hiçbir etkisi yoktur. Yalnızca zaman uyumsuz iş parçacığı iptal eden verileri raporlar.

## <a name="output"></a>Çıktı
 MDA, Abort işlemini gerçekleştiren iş parçacığının KIMLIĞINI ve iptal 'in hedefi olan iş parçacığının KIMLIĞINI bildirir. Bu, zaman uyumsuz iptal ile sınırlandırdığı için hiçbir zaman aynı olmayacaktır.

## <a name="configuration"></a>Yapılandırma

```xml
<mdaConfig>
  <assistants>
    <asynchronousThreadAbort />
  </assistants>
</mdaConfig>
```

## <a name="example"></a>Örnek
 `asynchronousThreadAbort` MDA ' nin etkinleştirilmesi ayrı çalışan bir iş parçacığında yalnızca bir <xref:System.Threading.Thread.Abort%2A> çağrısı gerektirir. İş parçacığı başlatma işlevinin içerikleri, iptal tarafından herhangi bir rastgele noktada kesintiye uğramış olabilecek daha karmaşık işlemler kümesi olsaydı sonuçları göz önünde bulundurun.

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
- [Yönetilen Hata Ayıklama Yardımcıları ile Hataları Tanılama](diagnosing-errors-with-managed-debugging-assistants.md)
