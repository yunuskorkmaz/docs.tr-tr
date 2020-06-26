---
title: asynchronousThreadAbort MDA
description: Bir iş parçacığı zaman uyumsuz bir iptal işlemini başka bir iş parçacığına koymaya çalıştığında, Asynchronousthreadavbort yönetilen hata ayıklama Yardımcısı 'nın (MDA) nasıl etkinleştirildiğini gözden geçirin.
ms.date: 03/30/2017
helpviewer_keywords:
- asynchronous thread aborts
- AsynchronousThreadAbort MDA
- managed debugging assistants (MDAs), asynchronous thread aborts
- threading [.NET Framework], managed debugging assistants
- MDAs (managed debugging assistants), asynchronous thread aborts
ms.assetid: 9ebe40b2-d703-421e-8660-984acc42bfe0
ms.openlocfilehash: 469372d57d9c21198353d171fec16458691eb25d
ms.sourcegitcommit: a2c8b19e813a52b91facbb5d7e3c062c7188b457
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/26/2020
ms.locfileid: "85415673"
---
# <a name="asynchronousthreadabort-mda"></a>asynchronousThreadAbort MDA
`asynchronousThreadAbort`Yönetilen hata ayıklama Yardımcısı (MDA), bir iş parçacığı başka bir iş parçacığına zaman uyumsuz bir iptal uygulamayı denediğinde etkinleştirilir. Zaman uyumlu iş parçacığı durdurulduğunda MDA 'ı etkinleştirmeyin `asynchronousThreadAbort` .

## <a name="symptoms"></a>Belirtiler
 <xref:System.Threading.ThreadAbortException>Ana uygulama iş parçacığı iptal edildiğinde, bir uygulama işlenmemiş ile çöküyor. Uygulamanın yürütülmeye devam etmesi gerekiyorsa, sonuçlar uygulama kilitlenmesinin ardından büyük olasılıkla daha fazla veri bozulmasına neden olabilir.

 Atomik olması amaçlanan işlemler kısmen tamamlandığında kesintiye uğratıldıktan sonra, uygulama verileri öngörülemeyen bir durumda bırakılır. Bir <xref:System.Threading.ThreadAbortException> özel durumun meydana gelmesi beklenmediği yerlerde, kod yürütmesindeki düzensiz rastgele noktalarda oluşturulabilir. Kod böyle bir özel durumu işleyemeyebilir, bu durum bozuk bir duruma neden olabilir.

 Belirtiler, soruna bağlı rasgelelik nedeniyle büyük ölçüde farklılık gösterebilir.

## <a name="cause"></a>Nedeni
 Bir iş parçacığındaki kod, <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> zaman uyumsuz bir iş parçacığı iptali tanıtmak için bir hedef iş parçacığında yöntemi olarak adlandırılır. Çağrıyı yapan kod, <xref:System.Threading.Thread.Abort%2A> durdurma işleminin hedefinden farklı bir iş parçacığında çalıştığından, iş parçacığı iptali zaman uyumsuzdur. İşlemi gerçekleştiren iş parçacığının <xref:System.Threading.Thread.Abort%2A> yalnızca uygulama durumunun tutarlı olduğu güvenli bir denetim noktasında yapılması gerektiğinden, zaman uyumlu iş parçacığı iptal noktaları soruna neden olmamalıdır.

 Zaman uyumsuz thread, hedef iş parçacığının yürütmesindeki öngörülemeyen noktalarda işlendiği için bir sorun oluştu. Bu durumdan kaçınmak için, bu şekilde durdurulmuş olabilecek bir iş parçacığında çalışmak üzere yazılan kodun <xref:System.Threading.ThreadAbortException> , neredeyse her bir kod satırında işlenmesi ve uygulama verilerinin tutarlı bir duruma geri alınmasına dikkat etmeniz gerekir. Kodun bu sorun ile yazılması veya tüm olası koşullara karşı koruyan bir kod yazmak için gerçekçi değildir.

 Yönetilmeyen kod ve `finally` bloklara yapılan çağrılar zaman uyumsuz olarak iptal edilmez, ancak bu kategorilerden birinden çıkış yapıldığında hemen silinir.

 Sorunun, soruna bağlı rastgele bir durum nedeniyle belirlenmesi zor olabilir.

## <a name="resolution"></a>Çözüm
 Zaman uyumsuz iş parçacığı iptal durumu kullanımını gerektiren kod tasarımını önleyin. Çağrısı gerektirmeyen bir hedef iş parçacığının kesintiye uğraması için çok sayıda yaklaşım daha uygundur <xref:System.Threading.Thread.Abort%2A> . En güvenli, bir kesme istemek için hedef iş parçacığına işaret eden ortak bir özellik gibi bir mekanizma tanıtmaktır. Hedef iş parçacığı belirli güvenli denetim noktalarında sinyali denetler. Bir kesmenin istenmiş olduğunu fark ederseniz, düzgün bir şekilde kapatılabilir.

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
 `asynchronousThreadAbort`Mda ' ın etkinleştirilmesi <xref:System.Threading.Thread.Abort%2A> ayrı çalışan bir iş parçacığında yalnızca bir çağrısı gerektirir. İş parçacığı başlatma işlevinin içerikleri, iptal tarafından herhangi bir rastgele noktada kesintiye uğramış olabilecek daha karmaşık işlemler kümesi olsaydı sonuçları göz önünde bulundurun.

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
