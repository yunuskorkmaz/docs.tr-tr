---
title: Veri ve Görev Paralelliğinde Olası Tuzaklar
description: Paralellik, sıralı kodda karşılaşılmayan karmaşıklık eklediğinden, veri ve görev paralelliği hakkında potansiyel bir bilgi edinin.
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- parallel programming, pitfalls
ms.assetid: 1e357177-e699-4b8f-9e49-56d3513ed128
ms.openlocfilehash: 05d934b80e60a8630db5b70e16a07c014598487a
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84599769"
---
# <a name="potential-pitfalls-in-data-and-task-parallelism"></a>Veri ve Görev Paralelliğinde Olası Tuzaklar
Birçok durumda, <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> normal sıralı döngüler üzerinde önemli performans iyileştirmeleri sağlayabilir. Ancak, döngüyü paralelleştirme işi, ardışık kodda yaygın olmayan veya hiç karşılaşılmayan sorunlara yol açabilecek karmaşıklığa neden olabilir. Bu konuda, paralel döngüler yazarken kaçınılacak bazı yöntemler listelenmiştir.  
  
## <a name="do-not-assume-that-parallel-is-always-faster"></a>Parallel öğesinin her zaman daha hızlı olduğunu varsaymayın  
 Bazı durumlarda, paralel bir döngü sıralı eşinden daha yavaş çalışabilir. Thumb 'in temel kuralı, birkaç yineleme ve Hızlı Kullanıcı temsilcileri olan paralel döngülerin çok daha hızlı bir şekilde hızlandırlanmasının düşüktür. Ancak, birçok etken performansa dahil edildiğinden, gerçek sonuçları her zaman ölçmenizi öneririz.  
  
## <a name="avoid-writing-to-shared-memory-locations"></a>Paylaşılan bellek konumlarına yazmayı önleyin  
 Ardışık kodda, statik değişkenlerle veya sınıf alanlarından okumak veya yazmak yaygın olmayan bir durumdur. Ancak, birden çok iş parçacığı bu tür değişkenlere eşzamanlı olarak eriştiği zaman, yarış koşullarında büyük bir olasılık vardır. Erişimi değişkene eşitlemek için kilitleri da kullanabilirsiniz, ancak eşitleme maliyeti performansı zarar verebilir. Bu nedenle, en az bir paralel döngüde mümkün olduğunca, paylaşılan duruma erişimi önlemenize veya en azından sınırlamanızı öneririz. Bunu yapmanın en iyi yolu, <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> <xref:System.Threading.ThreadLocal%601?displayProperty=nameWithType> döngü yürütme sırasında iş parçacığı yerel durumunu depolamak için bir değişken kullanan ve öğesinin aşırı yüklerini kullanmaktır. Daha fazla bilgi için bkz. [nasıl yapılır: Iş parçacığı yerel değişkenleriyle paralel. for döngüsü yazma](how-to-write-a-parallel-for-loop-with-thread-local-variables.md) ve [nasıl yapılır: Bölüm Yerel Değişkenleriyle bir Parallel. foreach döngüsü yazma](how-to-write-a-parallel-foreach-loop-with-partition-local-variables.md).  
  
## <a name="avoid-over-parallelization"></a>Fazla paralelleştirme kullanmaktan kaçının  
 Paralel döngüleri kullanarak, kaynak koleksiyonun bölümlenmesi ve çalışan iş parçacıklarını eşitlemek için ek ücret maliyetlerine tabi olursunuz. Paralelleştirme avantajları, bilgisayardaki işlemci sayısıyla daha fazla sınırlandırılır. Yalnızca bir işlemcide birden çok işlem ile sınırlı iş parçacığı çalıştırılarak kazanılabilir. Bu nedenle, paralel hale getirmek bir döngüye atmamaya dikkat etmeniz gerekir.  
  
 Fazla paralelleştirme gerçekleşebileceği en yaygın senaryo iç içe döngüdedir. Çoğu durumda, aşağıdaki koşullardan biri veya daha fazlası geçerli değilse yalnızca dış döngüyü paralel hale getirmek en iyi seçenektir:  
  
- İç döngünün çok uzun olduğu bilinmektedir.  
  
- Her sırada pahalı bir hesaplama gerçekleştirçalışıyorsunuz. (Örnekte gösterilen işlem pahalı değildir.)  
  
- Hedef sistemde, üzerinde sorgu paralelleştirerek üretilecek iş parçacığı sayısını işlemek için yeterli işlemci olduğu bilinmektedir `cust.Orders` .  
  
 Her durumda, en uygun sorgu şeklinin belirlenmesi için en iyi yol test ve ölçüdür.  
  
## <a name="avoid-calls-to-non-thread-safe-methods"></a>Iş parçacığı olmayan güvenli yöntemlere yapılan çağrılardan kaçının  
 İş parçacığı açısından güvenli olmayan örnek yöntemlerine paralel bir döngüden yazmak, programınızda algılanamayan veya algılanamayan veri bozulmasına yol açabilir. Ayrıca özel durumlara da yol açabilir. Aşağıdaki örnekte, birden çok iş parçacığı <xref:System.IO.FileStream.WriteByte%2A?displayProperty=nameWithType> yöntemi aynı anda çağırmaya çalışıyor ve bu sınıf tarafından desteklenmiyor.  
  
 [!code-csharp[TPL_Pitfalls#04](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_pitfalls/cs/pitfalls.cs#04)]
 [!code-vb[TPL_Pitfalls#04](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_pitfalls/vb/pitfalls_vb.vb#04)]  
  
## <a name="limit-calls-to-thread-safe-methods"></a>Iş parçacığı güvenli yöntemleriyle yapılan çağrıları sınırlayın  
 .NET Framework çoğu statik yöntem iş parçacığı açısından güvenlidir ve aynı anda birden çok iş parçacığından çağrılabilir. Ancak, bu durumlarda bile ilgili eşitleme, sorgudaki önemli yavaşlama oluşmasına neden olabilir.  
  
> [!NOTE]
> Sorgularınıza bazı çağrılar ekleyerek bunu kendiniz test edebilirsiniz <xref:System.Console.WriteLine%2A> . Bu yöntem, Gösterim amacıyla belge örneklerinde kullanılmasına karşın, gerekli olmadığı takdirde bunu paralel Döngülerde kullanmayın.  
  
## <a name="be-aware-of-thread-affinity-issues"></a>Iş parçacığı benzeşim sorunlarından haberdar olun  
 Tek iş parçacıklı Apartment (STA) bileşenleri, Windows Forms ve Windows Presentation Foundation (WPF) için COM birlikte çalışabilirlik gibi bazı teknolojiler, kodun belirli bir iş parçacığında çalıştırılmasını gerektiren iş parçacığı benzeşim kısıtlamalarını sağlar. Örneğin, hem Windows Forms hem de WPF 'de, bir denetime yalnızca oluşturulduğu iş parçacığında erişilebilir. Bu, örneğin, iş parçacığı Zamanlayıcı 'yı yalnızca kullanıcı arabirimi iş parçacığında çalışacak şekilde yapılandırmadığınız takdirde bir liste denetimini paralel bir döngüden güncelleştiremeyeceğiniz anlamına gelir. Daha fazla bilgi için bkz. [bir eşitleme bağlamı belirtme](xref:System.Threading.Tasks.TaskScheduler#specifying-a-synchronization-context).  
  
## <a name="use-caution-when-waiting-in-delegates-that-are-called-by-parallelinvoke"></a>Parallel. Invoke tarafından çağrılan Temsilcilerde beklerken dikkatli olun  
 Bazı durumlarda, görev paralel kitaplığı bir görevi satır içine alacak ve bu, yürütülmekte olan iş parçacığında görev üzerinde çalıştığı anlamına gelir. (Daha fazla bilgi için bkz. [Task zamanlayıcılar](xref:System.Threading.Tasks.TaskScheduler).) Bu performans iyileştirmesi belirli durumlarda kilitlenmeye neden olabilir. Örneğin, iki görev aynı temsilci kodunu çalıştırabilir, bu da bir olay meydana geldiğinde bildirir ve ardından diğer görevin sinyal gelmesini bekler. İkinci görev ilk olarak aynı iş parçacığında satır içine alınır ve ilki bekleme durumuna geçtiğinde ikinci görev hiçbir şekilde olayını işaret edemeyecektir. Böyle bir oluşumu önlemek için, bekleme işleminde bir zaman aşımı belirtebilir veya bir görevin diğerini engelleyemez emin olmak için açık iş parçacığı oluşturucuları kullanabilirsiniz.  
  
## <a name="do-not-assume-that-iterations-of-foreach-for-and-forall-always-execute-in-parallel"></a>ForEach, for ve ForAll yinelemelerinin her zaman paralel olarak yürütüleceğini varsayın  
 Bir veya döngüsünde tek tek yinelemelerin <xref:System.Threading.Tasks.Parallel.For%2A> <xref:System.Threading.Tasks.Parallel.ForEach%2A> paralel olarak yürütülmesi gerektiğini göz önünde bulundurmanız önemlidir <xref:System.Linq.ParallelEnumerable.ForAll%2A> . Bu nedenle, tekrarların paralel olarak yürütülmesi veya yinelemeler üzerinde herhangi bir sıraya göre yürütülmesi açısından doğruluğu için herhangi bir kod yazmadan kaçınmalısınız. Örneğin, bu kodun kilitlenmesi olasıdır:  
  
 [!code-csharp[TPL_Pitfalls#01](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_pitfalls/cs/pitfalls.cs#01)]
 [!code-vb[TPL_Pitfalls#01](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_pitfalls/vb/pitfalls_vb.vb#01)]  
  
 Bu örnekte, bir yineleme bir olay ayarlıyor ve diğer tüm yinelemeler olayda bekler. Olay ayarı yinelemesi tamamlanana kadar bekleyen yinelemeden hiçbiri tamamlanamaz. Ancak, bekleyen yinelemeler, olay ayarı yinelemesi yürütme şansı vermeden önce paralel döngüyü yürütmek için kullanılan tüm iş parçacıklarını engelliyor olabilir. Bu, bir kilitlenme ile sonuçlanır: olay ayarı yinelemesi hiçbir şekilde yürütülmez ve bekleyen yinelemeler hiçbir şekilde çağrılmaz.  
  
 Özellikle, bir paralel döngünün bir yinelemesi, ilerleme yapmak için döngünün başka bir yinelemesinin asla beklemelidir. Paralel döngü, yinelemeleri sırayla zamanlamaya karar verirse, ters sırada bir kilitlenme meydana gelir.  
  
## <a name="avoid-executing-parallel-loops-on-the-ui-thread"></a>UI Iş parçacığında paralel döngüler yürütmeden kaçının  
 Uygulamanızın Kullanıcı arabirimi (UI) yanıt vermesini sağlamak önemlidir. Bir işlem paralelleştirme sağlamak için yeterli iş içeriyorsa, büyük olasılıkla bu işlemi UI iş parçacığında çalıştırmamalıdır.  Bunun yerine, bir arka plan iş parçacığında çalıştırılacak işlemin boşaltması gerekir. Örneğin, bir UI denetiminde işlenmesi gereken bazı verileri hesaplamak için bir paralel döngü kullanmak istiyorsanız, döngüyü doğrudan bir UI olay işleyicide değil, bir görev örneği içinde yürütmeyi düşünmelisiniz.  Yalnızca çekirdek Hesaplama tamamlandığında, UI güncelleştirmesini UI iş parçacığına geri sıralayamaz.  
  
 UI iş parçacığında paralel döngüler çalıştırırsanız, Kullanıcı arabirimi denetimlerini döngünün içinden güncelleştirmemeye özen gösterin. UI denetimlerinin Kullanıcı arabirimi iş parçacığında yürütülen paralel bir döngüden güncelleştirilmesi girişimi, Kullanıcı arabirimi güncelleştirmesinin nasıl çağrıldığına bağlı olarak durum bozulması, özel durumlar, Gecikmeli güncelleştirmeler ve hatta kilitlenmeler oluşmasına neden olabilir. Aşağıdaki örnekte, paralel döngü tüm yinelemeler tamamlanana kadar yürütüldüğü Kullanıcı arabirimi iş parçacığını engeller. Ancak, döngü yinelemesi bir arka plan iş parçacığında çalışıyorsa (gibi <xref:System.Threading.Tasks.Parallel.For%2A> ), Invoke çağrısı, Kullanıcı arabirimi iş parçacığına ve bu iletinin işlenmesini bekleyen bloklara bir ileti gönderilmesine neden olur. Kullanıcı arabirimi iş parçacığı çalıştıran bir şekilde çalıştığından, <xref:System.Threading.Tasks.Parallel.For%2A> ileti hiçbir şekilde işlenmez ve UI iş parçacığı kilitlenmeleri.  
  
 [!code-csharp[TPL_Pitfalls#02](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_pitfalls/cs/pitfalls.cs#02)]
 [!code-vb[TPL_Pitfalls#02](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_pitfalls/vb/pitfalls_vb.vb#02)]  
  
 Aşağıdaki örnek, bir görev örneği içinde döngüyü çalıştırarak kilitlenmenin nasıl önleneceğini gösterir. UI iş parçacığı döngü tarafından engellenmemiştir ve ileti işlenebilir.  
  
 [!code-csharp[TPL_Pitfalls#03](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_pitfalls/cs/pitfalls.cs#03)]
 [!code-vb[TPL_Pitfalls#03](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_pitfalls/vb/pitfalls_vb.vb#03)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Paralel programlama](index.md)
- [PLINQ'te Olası Tuzaklar](potential-pitfalls-with-plinq.md)
- [Paralel programlama için desenler: .NET Framework 4 ile paralel desenleri anlama ve uygulama](https://www.microsoft.com/download/details.aspx?id=19222)
