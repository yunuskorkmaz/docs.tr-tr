---
title: PLINQ ile potansiyel tuzaklar
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- PLINQ queries, pitfalls
ms.assetid: 75a38b55-4bc4-488a-87d5-89dbdbdc76a2
ms.openlocfilehash: 3ddc0c013335e6a7b4708a5dd8be0b2247b2f60c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "74716248"
---
# <a name="potential-pitfalls-with-plinq"></a>PLINQ ile potansiyel tuzaklar

Çoğu durumda PLINQ, nesnelere sıralı LINQ üzerinden önemli performans iyileştirmeleri sağlayabilir. Ancak, sorgu yürütme paralelleştirme çalışması, sıralı kod olarak, ortak olmayan veya hiç karşılaşılan sorunlara yol açabilir karmaşıklığı tanıtır. Bu konu, PLINQ sorguları yazarken kaçınılması gereken bazı uygulamaları listeler.

## <a name="dont-assume-that-parallel-is-always-faster"></a>Paralelin her zaman daha hızlı olduğunu düşünmeyin

Paralelleştirme bazen bir PLINQ sorgusunun LINQ'dan Nesnelere eşdeğerinden daha yavaş çalışmasına neden olur. Başparmak temel kuralı, az kaynak öğeleri ve hızlı kullanıcı temsilcileri olan sorguları çok hızlandırmak olası değildir. Ancak, performansta birçok etken söz konusu olduğundan, PLINQ'u kullanıp kullanmamaya karar vermeden önce gerçek sonuçları ölçmenizi öneririz. Daha fazla bilgi için [PLINQ'da Çabuk'u Anlama'ya](understanding-speedup-in-plinq.md)bakın.

## <a name="avoid-writing-to-shared-memory-locations"></a>Paylaşılan bellek konumlarına yazmaktan kaçının

Sıralı kodda, statik değişkenlerden veya sınıf alanlarına okumak veya yazmak nadir değildir. Ancak, birden çok iş parçacığı aynı anda bu tür değişkenlere erişiyorsa, yarış koşulları için büyük bir potansiyel vardır. Değişkene erişimi eşitlemek için kilitleri kullanabiliyor olsanız da, eşitleme maliyeti performansa zarar verebilir. Bu nedenle, plinq sorgusunda paylaşılan duruma erişimi mümkün olduğunca önlemenizi veya en azından sınırlamanızı öneririz.

## <a name="avoid-over-parallelization"></a>Aşırı paralelleştirmeden kaçının

`AsParallel` Yöntemi kullanarak, kaynak koleksiyonunu bölümleme ve alt iş parçacıklarını eşitleme nin genel gider maliyetlerine maruz kalırsınız. Paralelleştirmenin yararları bilgisayardaki işlemci sayısıyla daha da sınırlıdır. Tek bir işlemcide birden çok işlemle bağlı iş parçacığı çalıştırılarak hız kazanılacak bir hız yoktur. Bu nedenle, bir sorguaşırı paralelleştirmemeye dikkat etmelisiniz.

Aşırı paralelleştirmenin gerçekleşebileceği en yaygın senaryo, aşağıdaki parçacıkta gösterildiği gibi iç içe dönük sorgularda dır.

[!code-csharp[PLINQ#20](~/samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#20)]
[!code-vb[PLINQ#20](~/samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinq2_vb.vb#20)]

Bu durumda, aşağıdaki koşullardan biri veya birkaçı geçerli olmadıkça yalnızca dış veri kaynağını (müşterileri) paralelleştirmek en iyisidir:

- İç veri kaynağı (cust. Siparişler) çok uzun olduğu bilinmektedir.

- Her siparişte pahalı bir hesaplama gerçekleştiresiniz. (Örnekte gösterilen işlem pahalı değildir.)

- Hedef sistemde sorguyu paralelleştirerek üretilecek iş parçacığı sayısını işlemek için yeterli işlemciye sahip olduğu `cust.Orders`bilinmektedir.

Her durumda, en iyi sorgu şeklini belirlemenin en iyi yolu sınamak ve ölçmektir. Daha fazla bilgi için [bkz: PLINQ Sorgu Performansını Ölçün.](../../../docs/standard/parallel-programming/how-to-measure-plinq-query-performance.md)

## <a name="avoid-calls-to-non-thread-safe-methods"></a>İş parçacığı güvenli olmayan yöntemlere yapılan çağrıları önlemek

PLINQ sorgusundan iş parçacığı güvenli olmayan örnek yöntemlerine yazma, programınızda algılanmayan veya görünmeyebilecek veri bozulmasına neden olabilir. Ayrıca özel durumlara yol açabilir. Aşağıdaki örnekte, birden çok iş parçacığı aynı `FileStream.Write` anda, hangi sınıf tarafından desteklenmeyen yöntemi çağırmak için çalışıyor olacaktır.

```vb
Dim fs As FileStream = File.OpenWrite(…)
a.AsParallel().Where(...).OrderBy(...).Select(...).ForAll(Sub(x) fs.Write(x))
```

```csharp
FileStream fs = File.OpenWrite(...);
a.AsParallel().Where(...).OrderBy(...).Select(...).ForAll(x => fs.Write(x));
```

## <a name="limit-calls-to-thread-safe-methods"></a>Aramaları iş parçacığı için güvenli yöntemlerle sınırlandırın

.NET Framework'deki statik yöntemlerin çoğu iş parçacığı açısından güvenlidir ve aynı anda birden çok iş parçacığından çağrılabilir. Ancak, bu gibi durumlarda bile, söz konusu eşitleme sorguda önemli yavaşlamaya neden olabilir.

> [!NOTE]
> Sorgularınıza bazı aramalar <xref:System.Console.WriteLine%2A> ekleyerek bunu kendiniz test edebilirsiniz. Bu yöntem belge örneklerinde gösteri amacıyla kullanılsa da, PLINQ sorgularında kullanmayın.

## <a name="avoid-unnecessary-ordering-operations"></a>Gereksiz sipariş işlemlerinden kaçının

PLINQ bir sorguyu paralel olarak yürüttüğünde, kaynak sırasını aynı anda birden çok iş parçacığı üzerinde çalıştırılabilen bölümlere böler. Varsayılan olarak, bölümlerin işlendiği ve sonuçların teslim edildiği sıra öngörülebilir değildir (örneğin, `OrderBy`işleçler hariç). PLINQ'a herhangi bir kaynak dizisinin sırasını korumasını emredebilirsiniz, ancak bunun performans üzerinde olumsuz bir etkisi vardır. Mümkün olduğunda en iyi yöntem, sorguları sipariş korumasına güvenmemek için yapılandırmaktır. Daha fazla bilgi için [PLINQ'da Sipariş Koruma'ya](order-preservation-in-plinq.md)bakın.

## <a name="prefer-forall-to-foreach-when-it-is-possible"></a>Mümkün olduğunda ForAll'ı ForEach'e tercih edin

PLINQ birden çok iş parçacığı üzerinde bir sorgu yürütür, sonuçları bir `foreach` döngüde (Visual Basic'te)`For Each` tüketirseniz, sorgu sonuçları tek bir iş parçacığında birleştirilmeli ve sayısallaştırıcı tarafından seri olarak erişilmelidir. Bazı durumlarda, bu kaçınılmazdır; ancak, mümkün olduğunda, `ForAll` her iş parçacığının kendi sonuçlarını çıkarmasını sağlamak için yöntemi kullanın, örneğin, <xref:System.Collections.Concurrent.ConcurrentBag%601?displayProperty=nameWithType>.

Aynı sorun <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType>. Başka bir `source.AsParallel().Where().ForAll(...)` deyişle, şiddetle tercih `Parallel.ForEach(source.AsParallel().Where(), ...)`edilmelidir.

## <a name="be-aware-of-thread-affinity-issues"></a>İş parçacığı afiyeti sorunlarına dikkat edin

Bazı teknolojiler, örneğin, Tek İş Parçacığı Daire (STA) bileşenleri, Windows Formları ve Windows Presentation Foundation (WPF) için COM birlikte çalışabilirliği, belirli bir iş parçacığı üzerinde çalıştırmak için kod gerektiren iş parçacığı afinite kısıtlamaları uygular. Örneğin, hem Windows Formlarında hem de WPF'de, denetime yalnızca oluşturulduğu iş parçacığında erişilebilir. PLINQ sorgusunda Windows Forms denetiminin paylaşılan durumuna erişmeye çalışırsanız, hata ayıklamada çalışıyorsanız bir özel durum yükseltilir. (Bu ayar kapatılabilir.) Ancak, sorgunuz UI iş parçacığı nda tüketiliyorsa, `foreach` bu kod tek bir iş parçacığı üzerinde yürütüldettiği için sorgu sonuçlarını sayan döngüden denetime erişebilirsiniz.

## <a name="dont-assume-that-iterations-of-foreach-for-and-forall-always-execute-in-parallel"></a>ForEach, For ve ForAll yinelemelerinin her zaman paralel olarak yürütüldettiğini düşünmeyin

Bir <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType>, veya <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> <xref:System.Linq.ParallelEnumerable.ForAll%2A> döngüdeki tek tek yinelemelerin ancak paralel olarak yürütülmesi gerekmediğini göz önünde bulundurmak önemlidir. Bu nedenle, yinelemelerin paralel yürütülmesi veya belirli bir sırada yinelemelerin yürütülmesi doğruluğa bağlı herhangi bir kod yazmaktan kaçınmalısınız.

Örneğin, bu kodun kilitlenme olasılığı yüksektir:

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

Bu örnekte, bir yineleme bir olay ayarlar ve diğer tüm yinelemeler olay üzerinde bekleyin. Olay ayar yinelemesi tamamlanana kadar bekleyen yinelemelerin hiçbiri tamamlanamaz. Ancak, olay ayar yinelemesi yürütme şansı olmadan önce, bekleyen yinelemeler paralel döngü yürütmek için kullanılan tüm iş parçacığı engellemek mümkündür. Bu bir kilitlenme yle sonuçlanır – olay ayar yinelemesi asla yürütülmeyecek ve bekleyen yinelemeler asla uyanmayacak.

Özellikle, paralel bir döngü bir yineleme ilerleme yapmak için döngü başka bir yineleme beklemek asla. Paralel döngü yinelemeleri sırayla ancak ters sırada zamanlamaya karar verirse, bir kilitlenme oluşur.

## <a name="see-also"></a>Ayrıca bkz.

- [Paralel LINQ (PLINQ)](parallel-linq-plinq.md)
