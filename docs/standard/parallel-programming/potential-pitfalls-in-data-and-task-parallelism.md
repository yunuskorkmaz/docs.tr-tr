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
ms.openlocfilehash: ff6ac9e8c41ee203ae72e1b28c088f462ddf6a54
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "73140024"
---
# <a name="potential-pitfalls-in-data-and-task-parallelism"></a>Veri ve Görev Paralelliğinde Olası Tuzaklar
Birçok durumda <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> ve <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> sıradan sıralı döngüler üzerinde önemli performans iyileştirmeleri sağlayabilir. Ancak, döngüparalelleştirme çalışması, sıralı kodolarak, yaygın olmayan veya hiç karşılaşılan sorunlara yol açabilecek karmaşıklık tanıtır. Bu konu, paralel döngüler yazarken kaçınılması gereken bazı uygulamaları listeler.  
  
## <a name="do-not-assume-that-parallel-is-always-faster"></a>Paralelin her zaman daha hızlı olduğunu düşünmeyin  
 Bazı durumlarda paralel döngü, sıralı eşdeğerinden daha yavaş çalışabilir. Başparmak temel kuralı, birkaç yineleme ve hızlı kullanıcı temsilcileri olan paralel döngüler çok hızlandırmak olası değildir. Ancak, performansta birçok etken söz konusu olduğundan, gerçek sonuçları her zaman ölçmenizi öneririz.  
  
## <a name="avoid-writing-to-shared-memory-locations"></a>Paylaşılan Bellek Konumlarına Yazmaktan Kaçının  
 Sıralı kodda, statik değişkenlerden veya sınıf alanlarına okumak veya yazmak nadir değildir. Ancak, birden çok iş parçacığı aynı anda bu tür değişkenlere erişiyorsa, yarış koşulları için büyük bir potansiyel vardır. Değişkene erişimi eşitlemek için kilitleri kullanabiliyor olsanız da, eşitleme maliyeti performansa zarar verebilir. Bu nedenle, paylaşılan duruma mümkün olduğunca paralel bir döngü içinde erişimi önlemenizi veya en azından sınırlamanızı öneririz. Bunu yapmanın en iyi yolu, döngü <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> yürütme <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> sırasında <xref:System.Threading.ThreadLocal%601?displayProperty=nameWithType> iş parçacığı yerel durumu depolamak için aşırı yükleri kullanmaktır. Daha fazla bilgi için [bkz: Thread-Local Variables ile Parallel.For Loop yazın](../../../docs/standard/parallel-programming/how-to-write-a-parallel-for-loop-with-thread-local-variables.md) ve [Nasıl: Partition-Local Variables ile Parallel.ForEach Loop yazın.](../../../docs/standard/parallel-programming/how-to-write-a-parallel-foreach-loop-with-partition-local-variables.md)  
  
## <a name="avoid-over-parallelization"></a>Aşırı Paralelleştirmeden Kaçının  
 Paralel döngüler kullanarak, kaynak koleksiyonunu bölümleme ve alt iş parçacıklarını eşitleme nin genel gider maliyetlerine maruz kalırsınız. Paralelleştirmenin yararları bilgisayardaki işlemci sayısıyla daha da sınırlıdır. Tek bir işlemcide birden çok işlemle bağlı iş parçacığı çalıştırılarak hız kazanılacak bir hız yoktur. Bu nedenle, bir döngüyü aşırı paralelleştirmemeye dikkat etmelisiniz.  
  
 Aşırı paralelleştirmeoluşabilir en yaygın senaryo iç içe döngüler içinde. Çoğu durumda, aşağıdaki koşullardan biri veya daha fazlası geçerli olmadıkça yalnızca dış döngüyü paralelleştirmek en iyisidir:  
  
- İç döngü çok uzun olduğu bilinmektedir.  
  
- Her siparişte pahalı bir hesaplama gerçekleştiresiniz. (Örnekte gösterilen işlem pahalı değildir.)  
  
- Hedef sistemde sorguyu paralelleştirerek üretilecek iş parçacığı sayısını işlemek için yeterli işlemciye sahip olduğu `cust.Orders`bilinmektedir.  
  
 Her durumda, en iyi sorgu şeklini belirlemenin en iyi yolu sınamak ve ölçmektir.  
  
## <a name="avoid-calls-to-non-thread-safe-methods"></a>İş Parçacığı Güvenli Olmayan Yöntemlere Yapılan Çağrılardan Kaçının  
 Paralel bir döngüden iş parçacığı güvenli olmayan örnek yöntemlerine yazma, programınızda algılanmayan veya görünmeyen veri bozulmasına neden olabilir. Ayrıca özel durumlara yol açabilir. Aşağıdaki örnekte, birden çok iş parçacığı aynı <xref:System.IO.FileStream.WriteByte%2A?displayProperty=nameWithType> anda, hangi sınıf tarafından desteklenmeyen yöntemi çağırmak için çalışıyor olacaktır.  
  
 [!code-csharp[TPL_Pitfalls#04](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_pitfalls/cs/pitfalls.cs#04)]
 [!code-vb[TPL_Pitfalls#04](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_pitfalls/vb/pitfalls_vb.vb#04)]  
  
## <a name="limit-calls-to-thread-safe-methods"></a>Aramaları İş Parçacığı Güvenli Yöntemlerle Sınırlandırın  
 .NET Framework'deki statik yöntemlerin çoğu iş parçacığı açısından güvenlidir ve aynı anda birden çok iş parçacığından çağrılabilir. Ancak, bu gibi durumlarda bile, söz konusu eşitleme sorguda önemli yavaşlamaya neden olabilir.  
  
> [!NOTE]
> Sorgularınıza bazı aramalar <xref:System.Console.WriteLine%2A> ekleyerek bunu kendiniz test edebilirsiniz. Bu yöntem belge örneklerinde gösterim amacıyla kullanılsa da, gerekmedikçe paralel döngülerde kullanmayın.  
  
## <a name="be-aware-of-thread-affinity-issues"></a>Konu Afiyeti Sorunlarının Farkında Olun  
 Bazı teknolojiler, örneğin, Tek İş Parçacığı Daire (STA) bileşenleri, Windows Formları ve Windows Presentation Foundation (WPF) için COM birlikte çalışabilirliği, belirli bir iş parçacığı üzerinde çalıştırmak için kod gerektiren iş parçacığı afinite kısıtlamaları uygular. Örneğin, hem Windows Formlarında hem de WPF'de, denetime yalnızca oluşturulduğu iş parçacığında erişilebilir. Bu, örneğin, iş parçacığı zamanlayıcısını yalnızca Kullanıcı Arabirimi iş parçacığı üzerinde çalışacak şekilde yapılandırmadığınız sürece, bir liste denetimini paralel döngüden güncelleştiremeyeceğiniz anlamına gelir. Daha fazla bilgi için [bkz.](xref:System.Threading.Tasks.TaskScheduler#specifying-a-synchronization-context)  
  
## <a name="use-caution-when-waiting-in-delegates-that-are-called-by-parallelinvoke"></a>Paralel Olarak Çağrılan Temsilcilerde Beklerken Dikkatli Olun.Çağrıl  
 Belirli durumlarda, Görev Paralel Kitaplığı bir görev satır, hangi şu anda yürütülen iş parçacığı üzerinde görevde çalışır anlamına gelir. (Daha fazla bilgi için [Görev Zamanlayıcıları'na](xref:System.Threading.Tasks.TaskScheduler)bakın.) Bu performans optimizasyonu bazı durumlarda kilitlenmelere neden olabilir. Örneğin, iki görev, bir olay oluştuğunda sinyal veren ve sonra diğer görevin sinyal gelmesini bekleyen aynı temsilci kodunu çalıştırabilir. İkinci görev ilki yle aynı iş parçacığıüzerinde sıralanmışsa ve ilki Bekle durumuna geçerse, ikinci görev hiçbir zaman olay sinyalini veremeyecektir. Böyle bir oluşumu önlemek için, Bekleme işlemi nde bir zaman sonu belirtebilir veya bir görevin diğerini engelleyememesini sağlamaya yardımcı olmak için açık iş parçacığı oluşturucuları kullanabilirsiniz.  
  
## <a name="do-not-assume-that-iterations-of-foreach-for-and-forall-always-execute-in-parallel"></a>ForEach, For ve ForAll Yinelemelerinin Her Zaman Paralel Yürütüldettiğini Düşünmeyin  
 Bir <xref:System.Threading.Tasks.Parallel.For%2A>döngüdeki <xref:System.Threading.Tasks.Parallel.ForEach%2A> <xref:System.Linq.ParallelEnumerable.ForAll%2A> tek tek yinelemelerin, ancak paralel olarak yürütülmesi gerekmediğini göz önünde bulundurmak önemlidir. Bu nedenle, yinelemelerin paralel yürütülmesi veya belirli bir sırada yinelemelerin yürütülmesi doğruluğa bağlı herhangi bir kod yazmaktan kaçınmalısınız. Örneğin, bu kodun kilitlenme olasılığı yüksektir:  
  
 [!code-csharp[TPL_Pitfalls#01](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_pitfalls/cs/pitfalls.cs#01)]
 [!code-vb[TPL_Pitfalls#01](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_pitfalls/vb/pitfalls_vb.vb#01)]  
  
 Bu örnekte, bir yineleme bir olay ayarlar ve diğer tüm yinelemeler olay üzerinde bekleyin. Olay ayar yinelemesi tamamlanana kadar bekleyen yinelemelerin hiçbiri tamamlanamaz. Ancak, olay ayar yinelemesi yürütme şansı olmadan önce, bekleyen yinelemeler paralel döngü yürütmek için kullanılan tüm iş parçacığı engellemek mümkündür. Bu bir kilitlenme yle sonuçlanır – olay ayar yinelemesi asla yürütülmeyecek ve bekleyen yinelemeler asla uyanmayacak.  
  
 Özellikle, paralel bir döngü bir yineleme ilerleme yapmak için döngü başka bir yineleme beklemek asla. Paralel döngü yinelemeleri sırayla ancak ters sırada zamanlamaya karar verirse, bir kilitlenme oluşur.  
  
## <a name="avoid-executing-parallel-loops-on-the-ui-thread"></a>UI İş parçacığı üzerinde Paralel Döngüler Yürütme kaçının  
 Uygulamanızın kullanıcı arabirimini (UI) duyarlı tutmak önemlidir. Bir işlem paralelleştirmeyi gerektirecek kadar çalışma içeriyorsa, büyük olasılıkla bu işlemi UI iş parçacığı üzerinde çalıştırılmamalıdır.  Bunun yerine, bir arka plan iş parçacığı üzerinde çalıştırılmak üzere bu işlemi boşaltmak gerekir. Örneğin, daha sonra bir UI denetimine işlenmesi gereken bazı verileri hesaplamak için paralel bir döngü kullanmak istiyorsanız, doğrudan bir UI olay işleyicisi yerine bir görev örneği içinde döngü yürütme yi düşünmelisiniz.  Yalnızca çekirdek hesaplama tamamlandığında, kullanıcı arası bilgi alan güncelleştirmeyi kullanıcı arası birimi iş parçacığına geri döndürmelisiniz.  
  
 UI iş parçacığı üzerinde paralel döngüler çalıştırırsanız, döngü içinden UI denetimleri güncelleştirmeyi önlemek için dikkatli olun. Kullanıcı Arabirimi iş parçacığı üzerinde çalışan paralel bir döngü içinde UI denetimleri güncelleştirmeye çalışırken, Kullanıcı Arabirimi güncelleştirmesinin nasıl çağrıldığine bağlı olarak durum bozulmasına, özel durumlara, gecikmeli güncelleştirmelere ve hatta kilitlenmelere neden olabilir. Aşağıdaki örnekte, paralel döngü tüm yinelemeler tamamlanana kadar yürütüldettiği UI iş parçacığı engeller. Ancak, döngü bir yineleme bir arka plan iş parçacığı <xref:System.Threading.Tasks.Parallel.For%2A> üzerinde çalışıyorsa (olabilir gibi), Çağrı çağrısı kullanıcı arabirimi iş parçacığına gönderilmesine neden olur ve bu iletinin işlenmesini bekleyen engeller. UI iş parçacığı çalışırken engellenir <xref:System.Threading.Tasks.Parallel.For%2A>yana, ileti asla işlenebilir ve UI iş parçacığı kilitlenir.  
  
 [!code-csharp[TPL_Pitfalls#02](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_pitfalls/cs/pitfalls.cs#02)]
 [!code-vb[TPL_Pitfalls#02](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_pitfalls/vb/pitfalls_vb.vb#02)]  
  
 Aşağıdaki örnek, döngüyü bir görev örneğinin içinde çalıştırarak kilitlenmeyi nasıl önleyileceğimi gösterir. UI iş parçacığı döngü tarafından engellenmez ve ileti işlenebilir.  
  
 [!code-csharp[TPL_Pitfalls#03](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_pitfalls/cs/pitfalls.cs#03)]
 [!code-vb[TPL_Pitfalls#03](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_pitfalls/vb/pitfalls_vb.vb#03)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Paralel Programlama](../../../docs/standard/parallel-programming/index.md)
- [PLINQ'te Olası Tuzaklar](../../../docs/standard/parallel-programming/potential-pitfalls-with-plinq.md)
- [Paralel Programlama Kalıpları: .NET Framework 4 ile Paralel Desenlerin Anlaşılması ve Uygulanması](https://www.microsoft.com/download/details.aspx?id=19222)
