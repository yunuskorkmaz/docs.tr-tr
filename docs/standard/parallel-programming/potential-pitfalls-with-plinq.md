---
title: PLıNQ ile olası tehlikeli
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- PLINQ queries, pitfalls
ms.assetid: 75a38b55-4bc4-488a-87d5-89dbdbdc76a2
ms.openlocfilehash: b4d58734fba4b834d5f5819a6bf19da0b7b7e8db
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84285319"
---
# <a name="potential-pitfalls-with-plinq"></a>PLıNQ ile olası tehlikeli

Birçok durumda PLıNQ, sıralı LINQ to Objects sorguları üzerinde önemli performans geliştirmeleri sağlayabilir. Ancak, sorgu yürütmeyi paralelleştirme işi, ardışık kodda yaygın olmayan veya hiç karşılaşılmayan sorunlara yol açabilecek karmaşıklığa neden olabilir. Bu konu başlığı altında, PLıNQ sorgularını yazarken kaçınılacak bazı yöntemler listelenmiştir.

## <a name="dont-assume-that-parallel-is-always-faster"></a>Parallel öğesinin her zaman daha hızlı olduğunu varsaymayın

Paralelleştirme bazen bir PLıNQ sorgusunun LINQ to Objects eşinden daha yavaş çalışmasına neden olur. Thumb 'in temel kuralı, az sayıda kaynak öğe ve Hızlı Kullanıcı temsilcileri olan sorguların çok daha hızlı bir şekilde hızlanmasından düşüktür. Ancak, birçok etken performansa dahil edildiğinden, PLıNQ kullanmaya karar vermeden önce gerçek sonuçları ölçmenizi öneririz. Daha fazla bilgi için bkz. [PLıNQ 'Te hızlı Hızlandırlamayı anlama](understanding-speedup-in-plinq.md).

## <a name="avoid-writing-to-shared-memory-locations"></a>Paylaşılan bellek konumlarına yazmayı önleyin

Ardışık kodda, statik değişkenlerle veya sınıf alanlarından okumak veya yazmak yaygın olmayan bir durumdur. Ancak, birden çok iş parçacığı bu tür değişkenlere eşzamanlı olarak eriştiği zaman, yarış koşullarında büyük bir olasılık vardır. Erişimi değişkene eşitlemek için kilitleri da kullanabilirsiniz, ancak eşitleme maliyeti performansı zarar verebilir. Bu nedenle, bir PLıNQ sorgusunda mümkün olduğunca, paylaşılan duruma erişimi önlemenize veya en azından sınırlamanızı öneririz.

## <a name="avoid-over-parallelization"></a>Fazla paralelleştirme kullanmaktan kaçının

`AsParallel`Yöntemini kullanarak, kaynak toplamayı bölümleyerek ve çalışan iş parçacıklarını eşitlerken ek ücret maliyetlerine tabi olursunuz. Paralelleştirme avantajları, bilgisayardaki işlemci sayısıyla daha fazla sınırlandırılır. Yalnızca bir işlemcide birden çok işlem ile sınırlı iş parçacığı çalıştırılarak kazanılabilir. Bu nedenle, paralel hale getirmek bir sorgu üzerinde bulunmamaya dikkat etmeniz gerekir.

Aşağıdaki kod parçacığında gösterildiği gibi, aşırı paralel hale getirme işleminin gerçekleşebileceği en yaygın senaryo iç içe sorgularda yer alabilir.

[!code-csharp[PLINQ#20](~/samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#20)]
[!code-vb[PLINQ#20](~/samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinq2_vb.vb#20)]

Bu durumda, aşağıdaki koşullardan biri veya birkaçı geçerli olmadığı için yalnızca dış veri kaynağına (müşteriler) paralel hale getirmek en iyi seçenektir:

- İç veri kaynağı (Müşt. Siparişler) çok uzun olduğu bilinmektedir.

- Her sırada pahalı bir hesaplama gerçekleştirçalışıyorsunuz. (Örnekte gösterilen işlem pahalı değildir.)

- Hedef sistemde, üzerinde sorgu paralelleştirerek üretilecek iş parçacığı sayısını işlemek için yeterli işlemci olduğu bilinmektedir `cust.Orders` .

Her durumda, en uygun sorgu şeklinin belirlenmesi için en iyi yol test ve ölçüdür. Daha fazla bilgi için bkz. [nasıl yapılır: PLıNQ sorgu performansını ölçme](how-to-measure-plinq-query-performance.md).

## <a name="avoid-calls-to-non-thread-safe-methods"></a>İş parçacığı olmayan güvenli yöntemlere yapılan çağrılardan kaçının

Bir PLıNQ sorgusundan iş parçacığı açısından güvenli olmayan örnek yöntemlerine yazmak, programınızda algılanamayan veya algılanamayan veri bozulmasına yol açabilir. Ayrıca özel durumlara da yol açabilir. Aşağıdaki örnekte, birden çok iş parçacığı `FileStream.Write` yöntemi aynı anda çağırmaya çalışıyor ve bu sınıf tarafından desteklenmiyor.

```vb
Dim fs As FileStream = File.OpenWrite(…)
a.AsParallel().Where(...).OrderBy(...).Select(...).ForAll(Sub(x) fs.Write(x))
```

```csharp
FileStream fs = File.OpenWrite(...);
a.AsParallel().Where(...).OrderBy(...).Select(...).ForAll(x => fs.Write(x));
```

## <a name="limit-calls-to-thread-safe-methods"></a>İş parçacığı güvenli yöntemleriyle yapılan çağrıları sınırlayın

.NET Framework çoğu statik yöntem iş parçacığı açısından güvenlidir ve aynı anda birden çok iş parçacığından çağrılabilir. Ancak, bu durumlarda bile ilgili eşitleme, sorgudaki önemli yavaşlama oluşmasına neden olabilir.

> [!NOTE]
> Sorgularınıza bazı çağrılar ekleyerek bunu kendiniz test edebilirsiniz <xref:System.Console.WriteLine%2A> . Bu yöntem, Gösterim amacıyla belge örneklerinde kullanılmasına karşın, bunu PLıNQ sorgularında kullanmayın.

## <a name="avoid-unnecessary-ordering-operations"></a>Gereksiz sıralama işlemlerinden kaçının

PLıNQ bir sorguyu paralel olarak yürüttüğünde, kaynak diziyi birden çok iş parçacığında eşzamanlı olarak işletilebilir bölümlere böler. Varsayılan olarak, bölümlerin işlenme sırası ve sonuçlar teslim edilebilir değildir (gibi işleçler hariç `OrderBy` ). PLıNQ ile herhangi bir kaynak dizinin sıralamasını koruyabilir, ancak bu performans üzerinde olumsuz bir etkiye sahip olabilir. En iyi yöntem, mümkün olduğunda, sorgu siparişi saklama üzerine güvenmemesi için sorguları yapısal olarak kullanmaktır. Daha fazla bilgi için bkz. [PLıNQ 'Te sıra koruma](order-preservation-in-plinq.md).

## <a name="prefer-forall-to-foreach-when-it-is-possible"></a>Bu mümkün olduğunda, ForAll öğesini ForEach olarak tercih et

PLıNQ birden çok iş parçacığında bir sorgu yürütüyordu, ancak sonuçları bir `foreach` döngüde ( `For Each` Visual Basic) kullandıysanız, sorgu sonuçlarının bir iş parçacığında geri birleştirilmesi ve Numaralandırıcının seri hale getirilene erişilmesi gerekir. Bazı durumlarda bu durum kaçınılmaz; Ancak mümkün olduğunda, `ForAll` her bir iş parçacığının kendi sonuçlarını çıktısının (örneğin, gibi iş parçacığı güvenli bir koleksiyona yazarak) çıkışını sağlamak için yöntemini kullanın <xref:System.Collections.Concurrent.ConcurrentBag%601?displayProperty=nameWithType> .

Aynı sorun için geçerlidir <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> . Diğer bir deyişle, `source.AsParallel().Where().ForAll(...)` için güçlü bir tercih edilmelidir `Parallel.ForEach(source.AsParallel().Where(), ...)` .

## <a name="be-aware-of-thread-affinity-issues"></a>İş parçacığı benzeşim sorunlarından haberdar olun

Tek iş parçacıklı Apartment (STA) bileşenleri, Windows Forms ve Windows Presentation Foundation (WPF) için COM birlikte çalışabilirlik gibi bazı teknolojiler, kodun belirli bir iş parçacığında çalıştırılmasını gerektiren iş parçacığı benzeşim kısıtlamalarını sağlar. Örneğin, hem Windows Forms hem de WPF 'de, bir denetime yalnızca oluşturulduğu iş parçacığında erişilebilir. Bir PLıNQ sorgusunda Windows Forms denetiminin paylaşılan durumuna erişmeye çalışırsanız, hata ayıklayıcıda çalıştırıyorsanız bir özel durum oluşturulur. (Bu ayar kapatılabilir.) Ancak, Sorgunuz UI iş parçacığında kullanılıyorsa, `foreach` Bu kod yalnızca bir iş parçacığında yürütüldüğü için sorgu sonuçlarını belirten döngüden denetime erişebilirsiniz.

## <a name="dont-assume-that-iterations-of-foreach-for-and-forall-always-execute-in-parallel"></a>ForEach, for ve ForAll yinelemelerinin her zaman paralel olarak yürütüleceğini varsayın

Bir <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> , veya döngüsünde tek tek yinelemelerin <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> paralel olarak yürütülmesi gerektiğini göz önünde bulundurmanız önemlidir <xref:System.Linq.ParallelEnumerable.ForAll%2A> . Bu nedenle, tekrarların paralel olarak yürütülmesi veya yinelemeler üzerinde herhangi bir sıraya göre yürütülmesi açısından doğruluğu için herhangi bir kod yazmadan kaçınmalısınız.

Örneğin, bu kodun kilitlenmesi olasıdır:

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

Bu örnekte, bir yineleme bir olay ayarlıyor ve diğer tüm yinelemeler olayda bekler. Olay ayarı yinelemesi tamamlanana kadar bekleyen yinelemeden hiçbiri tamamlanamaz. Ancak, bekleyen yinelemeler, olay ayarı yinelemesi yürütme şansı vermeden önce paralel döngüyü yürütmek için kullanılan tüm iş parçacıklarını engelliyor olabilir. Bu, bir kilitlenme ile sonuçlanır: olay ayarı yinelemesi hiçbir şekilde yürütülmez ve bekleyen yinelemeler hiçbir şekilde çağrılmaz.

Özellikle, bir paralel döngünün bir yinelemesi, ilerleme yapmak için döngünün başka bir yinelemesinin asla beklemelidir. Paralel döngü, yinelemeleri sırayla zamanlamaya karar verirse, ters sırada bir kilitlenme meydana gelir.

## <a name="see-also"></a>Ayrıca bkz.

- [Paralel LINQ (PLINQ)](introduction-to-plinq.md)
