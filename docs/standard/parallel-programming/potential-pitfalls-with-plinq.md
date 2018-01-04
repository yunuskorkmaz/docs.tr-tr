---
title: "PLINQ'te Olası Tuzaklar"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords: PLINQ queries, pitfalls
ms.assetid: 75a38b55-4bc4-488a-87d5-89dbdbdc76a2
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 972734b1275c82141c9057398268d068f5eaf3e6
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/23/2017
---
# <a name="potential-pitfalls-with-plinq"></a>PLINQ'te Olası Tuzaklar
Çoğu durumda, PLINQ nesneleri sorgulara sıralı LINQ üzerinde önemli ölçüde performans artışı sağlar. Ancak, sorgu yürütme parallelizing iş, sıralı kodda olarak ortak olmayan ya da hiç karşılaşılan değil sorunlara yol açabilir karmaşıklık getirir. Bu konuda PLINQ sorguları yazdığınızda önlemek için bazı yöntemler listelenmiştir.  
  
## <a name="do-not-assume-that-parallel-is-always-faster"></a>Bu paralel her zaman daha hızlı olduğunu varsayalım değil  
 Bazen paralelleştirme bir PLINQ sorgusu nesneleri eşdeğer kendi LINQ daha yavaş çalışmasına neden olur. Temel birkaç kaynağı öğeleri ve Hızlı Kullanıcı temsilcileri sorguları çok speedup için olası udur. Bununla birlikte, birçok faktöre performans oynayan çünkü PLINQ kullanıp kullanmayacağınızı karar vermeden önce gerçek sonuçları ölçmek öneririz. Daha fazla bilgi için bkz: [Plınq'te hızlandırmayı anlama](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).  
  
## <a name="avoid-writing-to-shared-memory-locations"></a>Paylaşılan bellek konumlara yazma kaçının  
 Sıralı kodda, onu okuma veya yazma statik değişkenler veya sınıf alanları vermektir. Ancak, birden çok iş parçacığı aynı anda bu değişkenleri erişen her bir büyük olası yarış durumları yoktur. Kilitleri değişkeni erişimi eşitlemek için kullanabileceğiniz olsa da, eşitleme maliyetini performansa zarar verebilir. Bu nedenle, öneririz, kaçının, veya en az sınırlamak, paylaşılan erişimi mümkün olduğunca bir PLINQ sorgusu durumda olduğunu.  
  
## <a name="avoid-over-parallelization"></a>Atlayarak Paralelleştirme kaçının  
 Kullanarak `AsParallel` işleci, kaynak koleksiyonu bölümlendirme ve çalışan iş parçacıklarını eşitleme genel giderlerinden doğurur. Paralelleştirme yararları daha fazla bilgisayar işlemci sayısıyla sınırlıdır. Tek bir işlemci, birden çok işlem bağlı iş parçacığı çalıştırarak kazanılacak hiçbir speedup yoktur. Bu nedenle, bir sorgu aşırı paralel hale değil dikkatli olmanız gerekir.  
  
 En yaygın senaryo hangi atlayarak paralelleştirme oluşabilir iç içe geçmiş sorgularda aşağıdaki kod parçacığında gösterildiği gibi değil.  
  
 [!code-csharp[PLINQ#20](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#20)]
 [!code-vb[PLINQ#20](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinq2_vb.vb#20)]  
  
 Bu durumda, bir veya daha fazla aşağıdaki koşullar geçerli sürece yalnızca dış veri kaynağı (Müşteriler) paralel hale idealdir:  
  
-   İç veri kaynağı (müşteri. Siparişleri) çok uzun olduğu bilinen.  
  
-   Her siparişte pahalı bir hesaplama yapıyorsunuz. (Örnekte gösterilen işlemi pahalı değildir.)  
  
-   Hedef sistem üzerinde sorgu parallelizing tarafından üretilen iş parçacığı sayısını işlemek için yeterli işlemci olduğu bilinmektedir `cust.Orders`.  
  
 Her durumda, en iyi sorgu şeklini belirlemek için en iyi test ve ölçmek için yoludur. Daha fazla bilgi için bkz: [nasıl yapılır: PLINQ sorgu performansını ölçü](../../../docs/standard/parallel-programming/how-to-measure-plinq-query-performance.md).  
  
## <a name="avoid-calls-to-non-thread-safe-methods"></a>İş parçacığı güvenli olmayan yöntem çağrıları kaçının  
 İş parçacığı güvenli olmayan örnek yöntemleri için bir PLINQ yazma programınıza saptanamayabilir değil veya veri bozulması sorgu neden olabilir. Özel durumlar da yol açabilir. Aşağıdaki örnekte, birden çok iş parçacığı çağırmak çalışıyor olabilir `Filestream.Write` yöntemi, aynı anda sınıfı tarafından desteklenmiyor.  
  
```vb  
Dim fs As FileStream = File.OpenWrite(…)  
a.Where(...).OrderBy(...).Select(...).ForAll(Sub(x) fs.Write(x))  
```  
  
```csharp  
FileStream fs = File.OpenWrite(...);  
a.Where(...).OrderBy(...).Select(...).ForAll(x => fs.Write(x));  
```  
  
## <a name="limit-calls-to-thread-safe-methods"></a>İş parçacığı yöntemleri sınırı çağrıları  
 .NET Framework'teki en statik yöntemler iş parçacığı ve birden çok iş parçacığı tarafından eşzamanlı olarak çağrılabilir. Ancak, bu durumlarda bile söz konusu eşitleme sorgusunda önemli yavaşlama neden olabilir.  
  
> [!NOTE]
>  Bunun için kendiniz bazı çağrılar ekleyerek test edebilirsiniz <xref:System.Console.WriteLine%2A> sorgularınızı içinde. Bu yöntem belgeleri örneklerde tanıtım amacıyla kullanılsa da PLINQ sorguları kullanmayın.  
  
## <a name="avoid-unnecessary-ordering-operations"></a>Gereksiz sıralama işlemlerden kaçının  
 PLINQ paralel olarak bir sorgu yürütüldüğünde, üzerinde aynı anda birden çok iş parçacığı üzerinde çalıştırılan bölümleri kaynak sıradaki böler. Varsayılan olarak, bölümler işlenir ve sonuçları vermiştir sırası tahmin edilebilir değil (gibi işleçleri hariç `OrderBy`). Tüm kaynak dizi sıralaması korumak için PLINQ söyleyebilirsiniz, ancak bu performans üzerinde olumsuz bir etkisi vardır. Sıra koruma güvenmeyin en iyi uygulama, mümkün olduğunda, yapısı sorguları, böylelikle. Daha fazla bilgi için bkz: [plınq'te sıra koruma](../../../docs/standard/parallel-programming/order-preservation-in-plinq.md).  
  
## <a name="prefer-forall-to-foreach-when-it-is-possible"></a>ForAll ForEach olduğunda mümkündür için tercih ettiğiniz  
 Sonuçlarda kullanırsa PLINQ sorgu birden çok iş parçacığı üzerinde yürütür. rağmen bir `foreach` döngü (`For Each` Visual Basic'te), sorgu sonuçları geri bir iş parçacığı birleştirilir ve seri olarak numaralandırıcı tarafından erişilebilir. Bazı durumlarda bu kaçınılmaz; Ancak, mümkün olduğunda kullanın `ForAll` gibi bir iş parçacığı koleksiyona yazarak kendi bu gibi bir durumda sonuçlarını çıkarmak her bir iş parçacığı etkinleştirmek için yöntemi <xref:System.Collections.Concurrent.ConcurrentBag%601?displayProperty=nameWithType>.  
  
 Aynı sorun uygulandığı <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> diğer bir deyişle, `source.AsParallel().Where().ForAll(...)` için kesinlikle tercih edilen olmalıdır  
  
 `Parallel.ForEach(source.AsParallel().Where(), ...)`.  
  
## <a name="be-aware-of-thread-affinity-issues"></a>İş parçacığı benzeşimini sorunlarının farkında olmanız  
 Bazı teknolojiler, örneğin, COM birlikte çalışabilirliği Single-Threaded grubu (STA) bileşenler, Windows Forms ve Windows Presentation Foundation (WPF) için belirli bir iş parçacığında çalıştırmak için kod gerektiren iş parçacığı benzeşimini kısıtlamaları zorunlu tuttukları. Örneğin, Windows Forms ve WPF içinde bir denetimi yalnızca üzerinde oluşturulduğu iş parçacığı üzerinde erişilebilir. Bir Windows Forms denetimi PLINQ sorgusunda paylaşılan durumu erişmeye çalışırsa hata ayıklayıcıda çalıştırıyorsanız, bir özel durum oluşturulur. (Bu ayar kapatılabilir.) Kullanıcı Arabirimi iş parçacığı üzerinde sorgunuzu tüketilen, ancak ardından denetimden erişebilirsiniz `foreach` sorgu numaralandırır döngü Bu kod yalnızca bir iş parçacığında yürüttüğünden sonuçlanır.  
  
## <a name="do-not-assume-that-iterations-of-foreach-for-and-forall-always-execute-in-parallel"></a>Değil varsayın ForEach, o yinelemelerini için ve ForAll her zaman Paralel yürütme  
 Bu tek tek yinelemelerini göz önünde bulundurmanız önemlidir bir <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType>, <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> veya <xref:System.Linq.ParallelEnumerable.ForAll%2A> döngü olabilir ancak Paralel yürütme gerekmez. Bu nedenle, doğruluk için tekrar Paralel yürütme ya da belirli bir sıraya yinelemelerini yürütülmesi bağlıdır herhangi bir kod yazmadan kaçınmalısınız.  
  
 Örneğin, bu kodu kilitlenme olasılığı bulunur:  
  
```vb  
Dim mre = New ManualResetEventSlim()  
    Enumerable.Range(0, ProcessorCount * 100).AsParallel().ForAll(Sub(j)   
  
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
            Enumerable.Range(0, ProcessorCount * 100).AsParallel().ForAll((j) =>  
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
  
 Bu örnekte, bir olay bir yineleme ayarlar ve diğer tüm yinelemeleri olayda bekleyin. Olay ayarı yineleme tamamlanana kadar bekleme yineleme hiçbiri tamamlayabilirsiniz. Ancak, bekleme yineleme olay ayarı yineleme yürütmek için bir fırsat dolmadığı önce paralel döngü yürütmek için kullanılan tüm iş parçacıklarının engelleme mümkündür. Bu bir kilitlenmeyle sonuçlanır – olay ayarı yineleme hiçbir zaman yürütülür ve bekleme yineleme hiçbir zaman uyandıracağına.  
  
 Özellikle, bir paralel bir döngüden yinelemesi hiçbir zaman başka bir döngü ilerleme beklemeniz gerekir. Paralel döngüsü yinelemeleri sırayla ancak ters sırada zamanlamak karar verirse, kilitlenme meydana gelir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Paralel LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)
