---
title: PLINQ'te Olası Tuzaklar
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- PLINQ queries, pitfalls
ms.assetid: 75a38b55-4bc4-488a-87d5-89dbdbdc76a2
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2b996b09ed3973125d4d848d5e00c18ab02a6967
ms.sourcegitcommit: 58fc0e6564a37fa1b9b1b140a637e864c4cf696e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/08/2019
ms.locfileid: "57673749"
---
# <a name="potential-pitfalls-with-plinq"></a>PLINQ'te Olası Tuzaklar

Çoğu durumda, PLINQ, sıralı LINQ-Plınq sorgularının üzerinde önemli performans geliştirmeleri sağlayabilir. Ancak, paralel sorgu yürütme işi, sıralı kodda olarak genel olmayan ya da hiç karşılaşılan değil sorunlara yol açabilecek daha karmaşık hâle getirir. Bu konuda, PLINQ sorguları yazarken önlemek için bazı yöntemler listelenmiştir.

## <a name="do-not-assume-that-parallel-is-always-faster"></a>Paralel her zaman daha hızlı olan varsaymayın

Bazen paralelleştirme bir PLINQ sorgusu nesneleri eşdeğer kendi LINQ göre daha yavaş çalışmasına neden olur. Temel birkaç kaynak öğeleri ve Hızlı Kullanıcı temsilcileri sorguları çok hızlandırmayı için olası udur. Ancak, birçok faktöre performans katılan olduğundan, PLINQ kullanıp kullanmayacağınızı karar vermeden önce gerçek sonuçlar ölçmek öneririz. Daha fazla bilgi için [plınq'te hızlandırmayı anlama](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).

## <a name="avoid-writing-to-shared-memory-locations"></a>Paylaşılan bellek konumlarına yazılmasını kaçının

Sıralı kodda, okuma veya yazma statik değişkenler veya sınıf alanlar için yaygın görülen değil. Ancak, birden çok iş parçacığı gibi değişkenleri eriştiği her seferde, büyük bir olası yarış durumlarını yoktur. Değişkene erişimi eşitlemek için kilit kullanabilirsiniz, ancak eşitleme maliyetini performansı olumsuz etkileyebilir. Bu nedenle, öneririz, kaçının, veya en az sınırlamak, paylaşılan erişimi mümkün olduğunca bir PLINQ sorgusu durumda olmadığını.

## <a name="avoid-over-parallelization"></a>Aşırı Paralelleştirme kaçının

Kullanarak `AsParallel` işleci, kaynak koleksiyonu bölümleme ve çalışan iş parçacığı eşitleme yüksek maliyetleri doğurur. Paralelleştirme avantajlarını daha fazla bilgisayara işlemci sayısı sınırlıdır. Tek bir işlemci üzerinde birden fazla hesaplama bağlantılı iş parçacığı çalıştırarak kazanılacak hiçbir hızlandırmayı yoktur. Bu nedenle, bir sorguyu aşırı paralel olmayan dikkatli olmanız gerekir.

En yaygın senaryoda hangi aşırı paralelleştirme oluşabilir iç içe geçmiş sorgularda aşağıdaki kod parçacığında gösterildiği gibi.

[!code-csharp[PLINQ#20](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#20)]
[!code-vb[PLINQ#20](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinq2_vb.vb#20)]

Bu durumda, bir veya daha fazla aşağıdaki koşullardan biri uygulamadığınız sürece yalnızca dış veri kaynağı (müşteri) paralel hale getirmek idealdir:

- İç veri kaynağı (müşteri. Siparişler) çok uzun olarak bilinir.

- Her bir order pahalı bir hesaplama yapıyorsunuz. (Örnekte gösterilen işlemi pahalı değildir.)

- Hedef sistem üzerinde sorguyu paralelleştirmek tarafından üretilen iş parçacığı sayısını işlemek için yeterli işlemci sahip olduğu bilinmektedir `cust.Orders`.

Her durumda en iyi sorgu şeklini belirlemek için en iyi test ve ölçmek için yoludur. Daha fazla bilgi için [nasıl yapılır: PLINQ sorgu performansını ölçme](../../../docs/standard/parallel-programming/how-to-measure-plinq-query-performance.md).

## <a name="avoid-calls-to-non-thread-safe-methods"></a>İş parçacığı güvenli olmayan yöntemlere yapılan çağrılar kaçının

İş parçacığı güvenli olmayan örnek yöntemleri için bir PLINQ yazma sorgu programınızda saptanamayabilir değil veya verilerin bozulmasına neden olabilir. Özel durumlar da neden olabilir. Aşağıdaki örnekte, birden çok iş parçacığı çağrı çalışıyor `FileStream.Write` yöntemi, aynı anda sınıfı tarafından desteklenmiyor.

```vb
Dim fs As FileStream = File.OpenWrite(…)
a.AsParallel().Where(...).OrderBy(...).Select(...).ForAll(Sub(x) fs.Write(x))
```

```csharp
FileStream fs = File.OpenWrite(...);
a.AsParallel().Where(...).OrderBy(...).Select(...).ForAll(x => fs.Write(x));
```

## <a name="limit-calls-to-thread-safe-methods"></a>İş parçacığı açısından güvenli yöntemlere yapılan çağrılar sınırı

.NET Framework'teki en statik yöntemler iş parçacığı bakımından güvenlidir ve aynı anda birden fazla iş parçacığından çağrılabilir. Ancak bu durumlarda bile ilgili eşitleme sorgu önemli yol açabilir.

> [!NOTE]
> Bunun için kendiniz bazı çağrıları ekleyerek test edebilirsiniz <xref:System.Console.WriteLine%2A> sorgularınızı içinde. Bu yöntem belgeleri örneklerde tanıtım amacıyla kullanılsa da PLINQ sorguları kullanmayın.

## <a name="avoid-unnecessary-ordering-operations"></a>Gereksiz sıralama işlemlerden kaçının

PLINQ'nun bir sorguyu paralel olarak yürütüldüğünde, kaynak sırası birden çok iş parçacığı üzerinde eşzamanlı olarak üzerinde işletilebilir bölümlere böler. Varsayılan olarak, bölümleri işlenir ve sonuçlarının teslim edildiği sıra tahmin edilebilir değildir (işleçler gibi dışında `OrderBy`). PLINQ'nun kaynak dizi sıralamasını korumak için bildirebilirsiniz, ancak bu performansı üzerinde olumsuz bir etkiye sahiptir. Sıra koruması üzerinde güvenmeyin en iyi uygulama, mümkün olduğunda, yapısı sorguları, böylelikle. Daha fazla bilgi için [plınq'te sıra koruma](../../../docs/standard/parallel-programming/order-preservation-in-plinq.md).

## <a name="prefer-forall-to-foreach-when-it-is-possible"></a>ForAll ForEach olduğunda mümkündür için tercih et

Sonuçlarda kazanabilirsiniz PLINQ sorgu birden çok iş parçacığında yürütülür. ancak bir `foreach` döngü (`For Each` Visual Basic'te), sorgu sonuçlarını bir akışına birleştirilir ve seri olarak numaralandırıcı tarafından erişilebilir. Bazı durumlarda, kaçınılmaz budur; Ancak, mümkün olduğunda kullanın `ForAll` kendi sonuçları, örneğin, bir iş parçacığı güvenli koleksiyonu yazarak çıktısını almak her bir iş parçacığı etkinleştirmek için yöntemi <xref:System.Collections.Concurrent.ConcurrentBag%601?displayProperty=nameWithType>.

Aynı sorunu uygulandığı <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> başka bir deyişle, `source.AsParallel().Where().ForAll(...)` kesin tercih edilmelidir

`Parallel.ForEach(source.AsParallel().Where(), ...)`.

## <a name="be-aware-of-thread-affinity-issues"></a>İş parçacığı benzeşimini sorunlarından haberdar olmalı

Örneğin, COM birlikte çalışabilirliği Single-Threaded grubu (STA) bileşenler, Windows Forms ve Windows Presentation Foundation (WPF) için bazı teknolojiler belirli bir iş parçacığı üzerinde çalıştırılacak kodu gerektiren iş parçacığı benzeşimini kısıtlamaları dayatır. Örneğin, Windows Forms ve WPF bir denetim yalnızca üzerinde oluşturulmuş iş parçacığı üzerinde erişilebilir. Paylaşılan bir PLINQ sorgusu Windows Forms denetiminde durumunu erişmeye çalışırsanız, hata ayıklayıcıda çalıştırıyorsanız bir özel durum oluşturulur. (Bu ayar kapatılabilir.) Sorgunuzu UI iş parçacığı üzerinde kullanılır, ancak ardından denetiminden erişebilirsiniz `foreach` sorgu listesini numaralandıran bir döngüye neden olur çünkü bu kod yalnızca bir iş parçacığında yürütülür.

## <a name="do-not-assume-that-iterations-of-foreach-for-and-forall-always-execute-in-parallel"></a>Değil varsayılır, ForEach, yinelemeleri için ve ForAll her zaman Paralel yürütme

Bu tek tek yinelemelerde göz önünde bulundurmanız önemlidir bir <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType>, <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> veya <xref:System.Linq.ParallelEnumerable.ForAll%2A> döngü Mayıs ancak paralel olarak yürütmek izniniz yok. Bu nedenle, yinelemelerin Paralel yürütme ya da yineleme herhangi bir sırayla yürütülmesi doğruluğu bağlıdır herhangi bir kod yazmadan kaçınmanız gerekir.

Örneğin, bu kodu kilitlenme olasılığı bulunur:

```vb
Dim mre = New ManualResetEventSlim()
Enumerable.Range(0, Environment.ProcessorCount * 100).AsParallel().ForAll(Sub(j)
   If j = Environment.ProcessorCount Then
       Console.WriteLine("Set on {0} with value of {1}", Thread.CurrentThread.ManagedThreadId, j)
       mre.Set()
   Else
       Console.WriteLine("Waiting on {0} with value of {1}", Thread.CurrentThread.ManagedThreadId, j)
       mre.Wait()
   End If
End Sub) ' deadlocks
```

```csharp
ManualResetEventSlim mre = new ManualResetEventSlim();
Enumerable.Range(0, Environment.ProcessorCount * 100).AsParallel().ForAll((j) =>
{
    if (j == Environment.ProcessorCount)
    {
        Console.WriteLine("Set on {0} with value of {1}", Thread.CurrentThread.ManagedThreadId, j);
        mre.Set();
    }
    else
    {
        Console.WriteLine("Waiting on {0} with value of {1}", Thread.CurrentThread.ManagedThreadId, j);
        mre.Wait();
    }
}); //deadlocks
```

Bu örnekte, bir olay bir yineleme ayarlar ve diğer tüm yinelemeleri olay üzerinde bekleyin. Olay ayarı yineleme tamamlanmasını bekleme yinelemeleri hiçbiri tamamlayabilirsiniz. Ancak, bekleme yinelemeleri önce olay ayarı yineleme yürütmek için bir fırsat paralel bir döngüden yürütmek için kullanılan tüm iş parçacıklarının block mümkündür. Bu bir kilitlenmeyle sonuçlanır: olay ayarı yineleme hiçbir zaman yürütülür ve bekleme yinelemeler hiç uyandıracağına.

Özellikle, bir yineleme, paralel bir döngüden hiçbir zaman başka bir döngü ilerleme beklemeniz gerekir. Yinelemeleri ardışık olarak ancak ters sırada zamanlamak paralel bir döngüden karar verirse, karşılıklı bir kilitlenme ortaya çıkar.

## <a name="see-also"></a>Ayrıca bkz.

- [Paralel LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)
