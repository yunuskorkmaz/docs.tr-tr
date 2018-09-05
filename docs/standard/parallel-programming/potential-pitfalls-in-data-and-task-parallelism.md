---
title: Veri ve Görev Paralelliğinde Olası Tuzaklar
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- parallel programming, pitfalls
ms.assetid: 1e357177-e699-4b8f-9e49-56d3513ed128
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7bb66d9009e9843a67bbc198f1e30e14d43c9a5d
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43555421"
---
# <a name="potential-pitfalls-in-data-and-task-parallelism"></a>Veri ve Görev Paralelliğinde Olası Tuzaklar
Çoğu durumda, <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> ve <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> önemli performans geliştirmeleri normal sıralı döngü sağlayabilir. Ancak, döngü paralel işi, sıralı kodda olarak genel olmayan ya da hiç karşılaşılan değil sorunlara yol açabilecek daha karmaşık hâle getirir. Bu konuda, paralel döngüler yazdığınızda önlemek için bazı yöntemler listelenmiştir.  
  
## <a name="do-not-assume-that-parallel-is-always-faster"></a>Paralel her zaman daha hızlı olan varsaymayın  
 Bazı durumlarda, paralel bir döngüden sıralı karşılığını göre daha yavaş çalışabilir. Temel birkaç yineleme ve Hızlı Kullanıcı temsilcileri paralel döngüler çok hızlandırmayı için olası udur. Ancak, performansı faktörlerden söz konusu olduğundan her zaman gerçek sonuçlarını ölçün öneririz.  
  
## <a name="avoid-writing-to-shared-memory-locations"></a>Paylaşılan bellek konumlarına yazılmasını kaçının  
 Sıralı kodda, okuma veya yazma statik değişkenler veya sınıf alanlar için yaygın görülen değil. Ancak, birden çok iş parçacığı gibi değişkenleri eriştiği her seferde, büyük bir olası yarış durumlarını yoktur. Değişkene erişimi eşitlemek için kilit kullanabilirsiniz, ancak eşitleme maliyetini performansı olumsuz etkileyebilir. Bu nedenle, öneririz, kaçının, veya en az sınırlamak, paylaşılan erişimi mümkün olduğunca paralel bir döngüden durumda olmadığını. Bunu yapmanın en iyi yolu aşırı kullanmaktır <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> ve <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> kullanan bir <xref:System.Threading.ThreadLocal%601?displayProperty=nameWithType> döngü yürütme sırasında iş parçacığı-yerel durumunu depolamak için değişken. Daha fazla bilgi için [nasıl yapılır: iş parçacığı yerel değişkenleriyle bir Parallel.For döngüsü yazma](../../../docs/standard/parallel-programming/how-to-write-a-parallel-for-loop-with-thread-local-variables.md) ve [nasıl yapılır: bölüm yerel değişkenleriyle bir Parallel.ForEach döngüsü yazma](../../../docs/standard/parallel-programming/how-to-write-a-parallel-foreach-loop-with-partition-local-variables.md).  
  
## <a name="avoid-over-parallelization"></a>Aşırı Paralelleştirme kaçının  
 Paralel döngüler kullanarak kaynak koleksiyonu bölümleme ve çalışan iş parçacığı eşitleme yüksek maliyetleri doğurur. Paralelleştirme avantajlarını daha fazla bilgisayara işlemci sayısı sınırlıdır. Tek bir işlemci üzerinde birden fazla hesaplama bağlantılı iş parçacığı çalıştırarak kazanılacak hiçbir hızlandırmayı yoktur. Bu nedenle, bir döngüyü aşırı paralel hale değil dikkatli olmanız gerekir.  
  
 En yaygın senaryoda iç içe geçmiş Döngülerde olduğundan hangi aşırı paralelleştirme ortaya çıkabilir. Çoğu durumda, bir veya daha fazla aşağıdaki koşullardan biri uygulamadığınız sürece yalnızca dış döngü paralel hale getirmek idealdir:  
  
-   İç döngü çok uzun olarak bilinir.  
  
-   Her bir order pahalı bir hesaplama yapıyorsunuz. (Örnekte gösterilen işlemi pahalı değildir.)  
  
-   Hedef sistem üzerinde sorguyu paralelleştirmek tarafından üretilen iş parçacığı sayısını işlemek için yeterli işlemci sahip olduğu bilinmektedir `cust.Orders`.  
  
 Her durumda en iyi sorgu şeklini belirlemek için en iyi test ve ölçmek için yoludur.  
  
## <a name="avoid-calls-to-non-thread-safe-methods"></a>İş parçacığı güvenli olmayan yöntemlere yapılan çağrılar kaçının  
 İş parçacığı güvenli olmayan örnek yöntemleri için paralel bir döngüden yazılırken programınızda saptanamayabilir değil veya veri bozulmasına neden olabilir. Özel durumlar da neden olabilir. Aşağıdaki örnekte, birden çok iş parçacığı çağrı çalışıyor <xref:System.IO.FileStream.WriteByte%2A?displayProperty=nameWithType> yöntemi, aynı anda sınıfı tarafından desteklenmiyor.  
  
 [!code-csharp[TPL_Pitfalls#04](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_pitfalls/cs/pitfalls.cs#04)]
 [!code-vb[TPL_Pitfalls#04](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_pitfalls/vb/pitfalls_vb.vb#04)]  
  
## <a name="limit-calls-to-thread-safe-methods"></a>İş parçacığı açısından güvenli yöntemlere yapılan çağrılar sınırı  
 .NET Framework'teki en statik yöntemler iş parçacığı bakımından güvenlidir ve aynı anda birden fazla iş parçacığından çağrılabilir. Ancak bu durumlarda bile ilgili eşitleme sorgu önemli yol açabilir.  
  
> [!NOTE]
>  Bunun için kendiniz bazı çağrıları ekleyerek test edebilirsiniz <xref:System.Console.WriteLine%2A> sorgularınızı içinde. Bu yöntem belgeleri örneklerde tanıtım amacıyla kullanılsa da, paralel Döngülerde sürece kullanmayın gerekli.  
  
## <a name="be-aware-of-thread-affinity-issues"></a>İş parçacığı benzeşimini sorunlarından haberdar olmalı  
 Örneğin, COM birlikte çalışabilirliği Single-Threaded grubu (STA) bileşenler, Windows Forms ve Windows Presentation Foundation (WPF) için bazı teknolojiler belirli bir iş parçacığı üzerinde çalıştırılacak kodu gerektiren iş parçacığı benzeşimini kısıtlamaları dayatır. Örneğin, Windows Forms ve WPF bir denetim yalnızca üzerinde oluşturulmuş iş parçacığı üzerinde erişilebilir. Bu, örneğin, yalnızca kullanıcı Arabirimi iş parçacığında iş zamanlamak için iş parçacığı Zamanlayıcısı yapılandırmadığınız sürece, paralel bir döngüden liste denetiminden güncelleştiremezsiniz anlamına gelir. Daha fazla bilgi için [nasıl yapılır: kullanıcı arabirimi (UI) iş parçacığında iş zamanlaması](https://msdn.microsoft.com/library/32a846a5-d628-4933-907b-4888ff72c663).  
  
## <a name="use-caution-when-waiting-in-delegates-that-are-called-by-parallelinvoke"></a>Varyans Parallel.Invoke tarafından çağrılan bekleyen kullanırken dikkatli olun  
 Bazı durumlarda, görev paralel kitaplığı, o anda yürütülen iş parçacığında görevin üzerinde çalıştığı anlamına gelir. bir görev satır içi olur. (Daha fazla bilgi için [görev planlayıcılar](https://msdn.microsoft.com/library/638f8ea5-21db-47a2-a934-86e1e961bf65).) Bu performans iyileştirmesi, bazı durumlarda kilitlenme neden olabilir. Örneğin, iki görevi aynı temsilci bir olay meydana geldiğinde, sinyalleri, kod ve sinyal başka bir görev bekler çalıştırabilirsiniz. Satır içine alınmış üzerinde ikinci görev ise ilk ve ilk olarak aynı iş parçacığı bir bekleme durumuna geçtiğinde, ikinci görev hiçbir zaman kendi olay sinyal mümkün olacaktır. Böyle etkinin önlemek için bir zaman aşımı bekleme işlemi belirtebilirsiniz veya kullanımı açık bir iş parçacığı oluşturucular bir görevin sağlamaya yardımcı olmak için diğer engelleyemez.  
  
## <a name="do-not-assume-that-iterations-of-foreach-for-and-forall-always-execute-in-parallel"></a>Değil varsayılır, ForEach, yinelemeleri için ve ForAll her zaman Paralel yürütme  
 Bu tek tek yinelemelerde göz önünde bulundurmanız önemlidir bir <xref:System.Threading.Tasks.Parallel.For%2A>, <xref:System.Threading.Tasks.Parallel.ForEach%2A> veya <xref:System.Linq.ParallelEnumerable.ForAll%2A> döngü Mayıs ancak paralel olarak yürütmek izniniz yok. Bu nedenle, yinelemelerin Paralel yürütme ya da yineleme herhangi bir sırayla yürütülmesi doğruluğu bağlıdır herhangi bir kod yazmadan kaçınmanız gerekir. Örneğin, bu kodu kilitlenme olasılığı bulunur:  
  
 [!code-csharp[TPL_Pitfalls#01](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_pitfalls/cs/pitfalls.cs#01)]
 [!code-vb[TPL_Pitfalls#01](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_pitfalls/vb/pitfalls_vb.vb#01)]  
  
 Bu örnekte, bir olay bir yineleme ayarlar ve diğer tüm yinelemeleri olay üzerinde bekleyin. Olay ayarı yineleme tamamlanmasını bekleme yinelemeleri hiçbiri tamamlayabilirsiniz. Ancak, bekleme yinelemeleri önce olay ayarı yineleme yürütmek için bir fırsat paralel bir döngüden yürütmek için kullanılan tüm iş parçacıklarının block mümkündür. Bu bir kilitlenmeyle sonuçlanır: olay ayarı yineleme hiçbir zaman yürütülür ve bekleme yinelemeler hiç uyandıracağına.  
  
 Özellikle, bir yineleme, paralel bir döngüden hiçbir zaman başka bir döngü ilerleme beklemeniz gerekir. Yinelemeleri ardışık olarak ancak ters sırada zamanlamak paralel bir döngüden karar verirse, karşılıklı bir kilitlenme ortaya çıkar.  
  
## <a name="avoid-executing-parallel-loops-on-the-ui-thread"></a>UI iş parçacığı üzerinde paralel döngüler yürütme kaçının  
 Uygulamanızın kullanıcı arabirimini (UI) hızlı yanıt veren tutmak önemlidir. Bir işlem paralelleştirme garanti altına almak için yeterli işim içeriyorsa, ardından bu büyük olasılıkla UI iş parçacığı üzerinde bu işlem çalıştırılmamalıdır.  Bunun yerine, bu işlem, bir arka plan iş parçacığında çalıştırılacak boşaltması. Örneğin, bir UI denetimine işleneceğini bazı verileri hesaplamak için paralel bir döngüden kullanmak istiyorsanız, döngü içinde bir görev örneği yerine doğrudan bir kullanıcı Arabirimi olay işleyicisi yürütülürken düşünmelisiniz.  Yalnızca çekirdek hesaplama tamamlandığında ardından kullanıcı arabirimini güncelleştirme kullanıcı Arabirimi iş parçacığı sıralamanız.  
  
 UI iş parçacığı üzerinde paralel döngüler çalıştırırsanız, UI denetimleri döngü içinde güncelleştirme kaçınmak dikkatli olun. UI iş parçacığı üzerinde Yürütülüyor paralel bir döngüden içinde denetimlerden UI'yi güncellemeye çalışırken durumu bozulması, özel durumlar, ertelenen güncelleştirmeler ve kullanıcı arabirimini güncelleştirme nasıl çağrılan bağlı olarak bile kilitlenmeler, açabilir. Aşağıdaki örnekte, paralel bir döngüden tüm yinelemeleri tamamlanana kadar üzerinde yürütme UI iş parçacığını engeller. Ancak, bir yinelemesini döngü arka plan iş parçacığında çalıştıran (olarak <xref:System.Threading.Tasks.Parallel.For%2A> yapabilirsiniz), çağırma çağrısı bir ileti UI iş parçacığı ve bu iletiyi işlenmeyi bekleyen blokları ayrılmak üzere gönderilmesine neden olur. UI iş parçacığı çalıştıran engellenir beri <xref:System.Threading.Tasks.Parallel.For%2A>, ileti hiçbir zaman işlenebilir ve kullanıcı Arabirimi iş parçacığı kilitlenmeleri.  
  
 [!code-csharp[TPL_Pitfalls#02](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_pitfalls/cs/pitfalls.cs#02)]
 [!code-vb[TPL_Pitfalls#02](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_pitfalls/vb/pitfalls_vb.vb#02)]  
  
 Aşağıdaki örnek, bir görev örneği döngüsünde çalıştırarak kilitlenme önlemek gösterilmektedir. UI iş parçacığı döngü tarafından engellenmediğinden ve ileti işlenebilir.  
  
 [!code-csharp[TPL_Pitfalls#03](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_pitfalls/cs/pitfalls.cs#03)]
 [!code-vb[TPL_Pitfalls#03](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_pitfalls/vb/pitfalls_vb.vb#03)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Paralel Programlama](../../../docs/standard/parallel-programming/index.md)  
 [PLINQ'te Olası Tuzaklar](../../../docs/standard/parallel-programming/potential-pitfalls-with-plinq.md)  
 [Paralel programlama için desenler: anlama ve uygulama ile paralel düzenleri .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=19222)
