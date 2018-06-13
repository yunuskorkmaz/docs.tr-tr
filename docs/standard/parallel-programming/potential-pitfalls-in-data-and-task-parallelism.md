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
ms.openlocfilehash: da87531ff7f20181e1e5499acb8152d0fbadc8af
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33592398"
---
# <a name="potential-pitfalls-in-data-and-task-parallelism"></a>Veri ve Görev Paralelliğinde Olası Tuzaklar
Çoğu durumda, <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> ve <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> önemli performans geliştirmeleri normal sıralı döngüler sağlayabilir. Ancak, döngü parallelizing iş, sıralı kodda olarak ortak olmayan ya da hiç karşılaşılan değil sorunlara yol açabilir karmaşıklık getirir. Bu konuda paralel döngüler yazdığınızda önlemek için bazı yöntemler listelenmiştir.  
  
## <a name="do-not-assume-that-parallel-is-always-faster"></a>Bu paralel her zaman daha hızlı olduğunu varsayalım değil  
 Belirli durumlarda paralel bir döngüden göre sıralı karşılığını daha yavaş çalışabilir. Temel birkaç yineleme ve Hızlı Kullanıcı temsilciler paralel döngüler çok speedup için olası udur. Bununla birlikte, birçok faktöre performans oynayan olduğundan her zaman gerçek sonuçları ölçmek öneririz.  
  
## <a name="avoid-writing-to-shared-memory-locations"></a>Paylaşılan bellek konumlara yazma kaçının  
 Sıralı kodda, onu okuma veya yazma statik değişkenler veya sınıf alanları vermektir. Ancak, birden çok iş parçacığı aynı anda bu değişkenleri erişen her bir büyük olası yarış durumları yoktur. Kilitleri değişkeni erişimi eşitlemek için kullanabileceğiniz olsa da, eşitleme maliyetini performansa zarar verebilir. Bu nedenle, öneririz, kaçının, veya en azından sınırlamak, paylaşılan erişimi mümkün olduğunca paralel bir döngüden durumda olduğunu. Bunu yapmak için en iyi yolu aşırı kullanmaktır <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> ve <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> kullanan bir <xref:System.Threading.ThreadLocal%601?displayProperty=nameWithType> döngü yürütme sırasında iş parçacığı yerel durumunu depolamak için değişkeni. Daha fazla bilgi için bkz: [nasıl yapılır: iş parçacığı yerel değişkenleriyle bir Parallel.For döngüsü yazma](../../../docs/standard/parallel-programming/how-to-write-a-parallel-for-loop-with-thread-local-variables.md) ve [nasıl yapılır: iş parçacığı yerel değişkenleriyle bir Parallel.ForEach döngüsü yazma](../../../docs/standard/parallel-programming/how-to-write-a-parallel-foreach-loop-with-thread-local-variables.md).  
  
## <a name="avoid-over-parallelization"></a>Atlayarak Paralelleştirme kaçının  
 Paralel döngüler kullanarak, kaynak koleksiyonu bölümlendirme ve çalışan iş parçacıklarını eşitleme genel giderlerinden doğurur. Paralelleştirme yararları daha fazla bilgisayar işlemci sayısıyla sınırlıdır. Tek bir işlemci, birden çok işlem bağlı iş parçacığı çalıştırarak kazanılacak hiçbir speedup yoktur. Bu nedenle, bir döngü aşırı paralel hale değil dikkatli olmanız gerekir.  
  
 En yaygın senaryo olduğundan iç içe geçmiş Döngülerde hangi atlayarak paralelleştirme oluşabilir. Çoğu durumda, bir veya daha fazla aşağıdaki koşullar geçerli sürece yalnızca dış döngü paralel hale idealdir:  
  
-   İç döngü çok uzun olduğu bilinmektedir.  
  
-   Her siparişte pahalı bir hesaplama yapıyorsunuz. (Örnekte gösterilen işlemi pahalı değildir.)  
  
-   Hedef sistem üzerinde sorgu parallelizing tarafından üretilen iş parçacığı sayısını işlemek için yeterli işlemci olduğu bilinmektedir `cust.Orders`.  
  
 Her durumda, en iyi sorgu şeklini belirlemek için en iyi test ve ölçmek için yoludur.  
  
## <a name="avoid-calls-to-non-thread-safe-methods"></a>İş parçacığı güvenli olmayan yöntem çağrıları kaçının  
 İş parçacığı güvenli olmayan örnek yöntemleri için paralel bir döngüden yazılırken olabilir veya programınıza saptanamayabilir değil veri bozulmasına neden olabilir. Özel durumlar da yol açabilir. Aşağıdaki örnekte, birden çok iş parçacığı çağırmak çalışıyor olabilir <xref:System.IO.FileStream.WriteByte%2A?displayProperty=nameWithType> yöntemi, aynı anda sınıfı tarafından desteklenmiyor.  
  
 [!code-csharp[TPL_Pitfalls#04](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_pitfalls/cs/pitfalls.cs#04)]
 [!code-vb[TPL_Pitfalls#04](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_pitfalls/vb/pitfalls_vb.vb#04)]  
  
## <a name="limit-calls-to-thread-safe-methods"></a>İş parçacığı yöntemleri sınırı çağrıları  
 .NET Framework'teki en statik yöntemler iş parçacığı ve birden çok iş parçacığı tarafından eşzamanlı olarak çağrılabilir. Ancak, bu durumlarda bile söz konusu eşitleme sorgusunda önemli yavaşlama neden olabilir.  
  
> [!NOTE]
>  Bunun için kendiniz bazı çağrılar ekleyerek test edebilirsiniz <xref:System.Console.WriteLine%2A> sorgularınızı içinde. Bu yöntem belgeleri örneklerde tanıtım amacıyla kullanılsa da, paralel Döngülerde sürece kullanmayın gerekli.  
  
## <a name="be-aware-of-thread-affinity-issues"></a>İş parçacığı benzeşimini sorunlarının farkında olmanız  
 Bazı teknolojiler, örneğin, COM birlikte çalışabilirliği Single-Threaded grubu (STA) bileşenler, Windows Forms ve Windows Presentation Foundation (WPF) için belirli bir iş parçacığında çalıştırmak için kod gerektiren iş parçacığı benzeşimini kısıtlamaları zorunlu tuttukları. Örneğin, Windows Forms ve WPF içinde bir denetimi yalnızca üzerinde oluşturulduğu iş parçacığı üzerinde erişilebilir. Bu, örneğin, yalnızca kullanıcı Arabirimi iş parçacığı üzerinde çalışması zamanlamak için iş parçacığı Zamanlayıcı yapılandırmadığınız sürece paralel bir döngüden listesi denetiminden güncelleştirilemiyor anlamına gelir. Daha fazla bilgi için bkz: [nasıl yapılır: kullanıcı arabirimi (UI) iş parçacığı üzerinde zamanlama iş](http://msdn.microsoft.com/library/32a846a5-d628-4933-907b-4888ff72c663).  
  
## <a name="use-caution-when-waiting-in-delegates-that-are-called-by-parallelinvoke"></a>Parallel.Invoke tarafından çağrılan temsilciler bekleyen değiştirirken dikkatli olun  
 Bazı durumlarda, görev paralel kitaplığı, bir görev, görevi şu anda yürütülen iş parçacığı üzerinde çalıştığı anlamına gelir satır içi olur. (Daha fazla bilgi için bkz: [görev zamanlayıcılar](http://msdn.microsoft.com/library/638f8ea5-21db-47a2-a934-86e1e961bf65).) Bu performans iyileştirme belirli durumlarda kilitlenmeye neden olabilir. Örneğin, iki görevi bir olay gerçekleştiğinde sinyalleri, kod, ardından sinyal başka bir görev bekler aynı temsilci çalıştırabilirsiniz. İkinci görev çubuğunda içermesinden ise ilk ve ilk olarak iş parçacığı bir bekleme durumuna geçtiğinde, ikinci görev hiçbir zaman kendi olay sinyal mümkün olmaz. Bu tür bir oluşumunu önlemek için bir zaman aşımı bekleme işlemi belirtebilir veya görev sağlamaya yardımcı olmak için kullanım açık iş parçacığı oluşturucular diğer durduramazsınız.  
  
## <a name="do-not-assume-that-iterations-of-foreach-for-and-forall-always-execute-in-parallel"></a>Değil varsayın ForEach, o yinelemelerini için ve ForAll her zaman Paralel yürütme  
 Bu tek tek yinelemelerini göz önünde bulundurmanız önemlidir bir <xref:System.Threading.Tasks.Parallel.For%2A>, <xref:System.Threading.Tasks.Parallel.ForEach%2A> veya <xref:System.Linq.ParallelEnumerable.ForAll%2A> döngü olabilir ancak Paralel yürütme gerekmez. Bu nedenle, doğruluk için tekrar Paralel yürütme ya da belirli bir sıraya yinelemelerini yürütülmesi bağlıdır herhangi bir kod yazmadan kaçınmalısınız. Örneğin, bu kodu kilitlenme olasılığı bulunur:  
  
 [!code-csharp[TPL_Pitfalls#01](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_pitfalls/cs/pitfalls.cs#01)]
 [!code-vb[TPL_Pitfalls#01](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_pitfalls/vb/pitfalls_vb.vb#01)]  
  
 Bu örnekte, bir olay bir yineleme ayarlar ve diğer tüm yinelemeleri olayda bekleyin. Olay ayarı yineleme tamamlanana kadar bekleme yineleme hiçbiri tamamlayabilirsiniz. Ancak, bekleme yineleme olay ayarı yineleme yürütmek için bir fırsat dolmadığı önce paralel döngü yürütmek için kullanılan tüm iş parçacıklarının engelleme mümkündür. Bu bir kilitlenmeyle sonuçlanır – olay ayarı yineleme hiçbir zaman yürütülür ve bekleme yineleme hiçbir zaman uyandıracağına.  
  
 Özellikle, bir paralel bir döngüden yinelemesi hiçbir zaman başka bir döngü ilerleme beklemeniz gerekir. Paralel döngüsü yinelemeleri sırayla ancak ters sırada zamanlamak karar verirse, kilitlenme meydana gelir.  
  
## <a name="avoid-executing-parallel-loops-on-the-ui-thread"></a>Paralel döngüler kullanıcı Arabirimi iş parçacığı üzerinde yürütme kaçının  
 Uygulamanızın kullanıcı arabirimi (UI) yanıt verebilir durumda tutmak önemlidir. Bir işlem paralelleştirme garanti etmeye yeterli iş içeriyorsa, daha sonra bu büyük olasılıkla kullanıcı Arabirimi iş parçacığı üzerinde bu işlem çalıştırılmamalıdır.  Bunun yerine, arka plan iş parçacığında çalıştırmak için bu işlem boşaltması. Örneğin, bir kullanıcı Arabirimi denetime işleneceğini bazı verileri hesaplamak için paralel bir döngüden kullanmak istiyorsanız, bir görev örneği içinde yerine doğrudan bir UI olay işleyicisi döngü yürütme düşünmelisiniz.  Yalnızca çekirdek hesaplama tamamlandığında UI güncelleştirme kullanıcı Arabirimi iş parçacığı sonra sıralama.  
  
 Paralel döngüler kullanıcı Arabirimi iş parçacığı üzerinde çalıştırıyorsanız, kullanıcı Arabirimi denetimlerini döngü içinde güncelleştirme kaçınmak için dikkatli olun. UI güncelleştirme girişimi kullanıcı Arabirimi iş parçacığı üzerinde yürütme paralel bir döngüden içinde denetimlerden durumu bozulması, özel durumlar, Gecikmeli güncelleştirmeleri ve UI güncelleştirme nasıl çağrıldığını bağlı olarak bile kilitlenmeleri neden olabilir. Aşağıdaki örnekte, tüm yinelemeleri tamamlanana kadar üzerinde yürütülmekte olduğu kullanıcı Arabirimi iş parçacığı paralel döngü engeller. Ancak, bir yinelemesi döngü arka plan iş parçacığında çalıştıran (olarak <xref:System.Threading.Tasks.Parallel.For%2A> yapabilirsiniz), bu iletiyi işlenmeyi bekleyen blokları ve kullanıcı Arabirimi iş parçacığı için gönderilecek bir ileti çağırma çağrısı neden olur. Kullanıcı Arabirimi iş parçacığı çalıştıran engellendi beri <xref:System.Threading.Tasks.Parallel.For%2A>, ileti hiçbir zaman işlenebilir ve kullanıcı Arabirimi iş parçacığı kilitlenmeleri.  
  
 [!code-csharp[TPL_Pitfalls#02](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_pitfalls/cs/pitfalls.cs#02)]
 [!code-vb[TPL_Pitfalls#02](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_pitfalls/vb/pitfalls_vb.vb#02)]  
  
 Aşağıdaki örnek, bir görev örneği içinde döngü çalıştırarak kilitlenme önlemek gösterilmiştir. Kullanıcı Arabirimi iş parçacığı tarafından döngü engellenmeyen ve ileti işlenebilir.  
  
 [!code-csharp[TPL_Pitfalls#03](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_pitfalls/cs/pitfalls.cs#03)]
 [!code-vb[TPL_Pitfalls#03](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_pitfalls/vb/pitfalls_vb.vb#03)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Paralel Programlama](../../../docs/standard/parallel-programming/index.md)  
 [PLINQ'te Olası Tuzaklar](../../../docs/standard/parallel-programming/potential-pitfalls-with-plinq.md)  
 [Paralel programlama için desenleri: anlama ve uygulama paralel .NET Framework 4 desenler](https://www.microsoft.com/download/details.aspx?id=19222)
