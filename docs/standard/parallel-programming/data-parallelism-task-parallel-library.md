---
title: Veri Paralelliği (Görev Paralel Kitaplığı)
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- parallelism, data
ms.assetid: 3f05f33f-f1da-4b16-81c2-9ceff1bef449
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 19e518db75fe3e45f57cbb6fab8c5281cceb4d34
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69939332"
---
# <a name="data-parallelism-task-parallel-library"></a>Veri Paralelliği (Görev Paralel Kitaplığı)
*Veri paralelliği* , kaynak koleksiyondaki veya dizideki öğelerde aynı işlemin eşzamanlı olarak (yani paralel) gerçekleştirildiği senaryolara başvurur. Veri paralel işlemlerinde, kaynak koleksiyon, birden çok iş parçacığının aynı anda farklı kesimlerde çalışabilmesi için bölümlenmiş olur.  
  
 Görev paralel kitaplığı (TPL), <xref:System.Threading.Tasks.Parallel?displayProperty=nameWithType> sınıfı aracılığıyla verileri paralellik olarak destekler. Bu sınıf for ve [foreach](../../csharp/language-reference/keywords/foreach-in.md) döngüleri (`For` ve `For Each` Visual Basic) [için](../../csharp/language-reference/keywords/for.md) Yöntem tabanlı paralel uygulamalar sağlar. Sıralı bir döngü yazdığınızda bir <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> veya <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> döngüsünün döngü mantığını yazın. İş parçacığı oluşturmak veya iş öğelerini kuyruğa almak zorunda değilsiniz. Temel Döngülerde kilit almanız gerekmez. TPL, tüm düşük düzeydeki işleri sizin için işler. <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> [Ve kullanımıhakkındaayrıntılıbilgiiçin,paralelprogramlamaiçinbelgedesenleriniindirin:<xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=19222)ile paralel desenleri anlama ve uygulama. Aşağıdaki kod örneğinde basit `foreach` bir döngü ve onun paralel eşdeğeri gösterilmektedir.  
  
> [!NOTE]
> TPL'de temsilciler tanımlamak için bu belgede lambda ifadeleri kullanılır. Veya Visual Basic içindeki C# lambda ifadeleriyle ilgili bilgi sahibi değilseniz bkz. [PLıNQ ve TPL içindeki lambda ifadeleri](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md).  
  
 [!code-csharp[TPL#20](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl/cs/tpl.cs#20)]
 [!code-vb[TPL#20](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl/vb/tpl_vb.vb#20)]  
  
 Bir paralel döngü çalıştığında, çağrının birden çok parçaya eşzamanlı olarak çalışabilmesi için, TPL veri kaynağını bölümlendirir. Arka planda Görev Zamanlayıcı, görevi sistem kaynakları ve iş yüküne göre bölümler. Mümkün olduğunda Zamanlayıcı, iş yükü dengesiz hale gelirse birden çok iş parçacığı ve işlemci arasında çalışmayı yeniden dağıtır.  
  
> [!NOTE]
> Ayrıca kendi özel bölümleyici veya Scheduler 'ı da sağlayabilirsiniz. Daha fazla bilgi için bkz. [PLıNQ ve TPL Için Özel Bölümleyiciler](../../../docs/standard/parallel-programming/custom-partitioners-for-plinq-and-tpl.md) ve [görev zamanlayıcılar](xref:System.Threading.Tasks.TaskScheduler).  
  
 Hem hem <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> de yöntemlerinin her ikisinde de döngü yürütmeyi durdurmanızı veya sonlandırırsanız, diğer iş parçacıklarında döngünün durumunu izlemenize, iş parçacığı yerel durumunu sürdürmenize, iş parçacığı yerel nesnelerinin sonlandırmasına, eşzamanlılık derecesindeki bir şekilde kontrol etmenize olanak tanıyan birkaç aşırı yükleme vardır. vb. Bu işlevi etkinleştiren yardımcı türler <xref:System.Threading.Tasks.ParallelLoopState> <xref:System.Threading.Tasks.ParallelLoopResult>, <xref:System.Threading.Tasks.ParallelOptions> <xref:System.Threading.CancellationToken>,, ve <xref:System.Threading.CancellationTokenSource>içerir.  
  
 Daha fazla bilgi için bkz [. paralel programlama desenleri: .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=19222)ile paralel desenleri anlama ve uygulama.  
  
 Bildirim temelli veya sorgu benzeri, sözdizimi ile veri paralelliği, PLıNQ tarafından desteklenir. Daha fazla bilgi için bkz. [Parallel LINQ (PLıNQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md).  
  
## <a name="related-topics"></a>İlgili Konular  
  
|Başlık|Açıklama|  
|-----------|-----------------|  
|[Nasıl yapılır: Basit bir paralel. for döngüsü yazın](../../../docs/standard/parallel-programming/how-to-write-a-simple-parallel-for-loop.md)|Herhangi bir dizi veya dizin <xref:System.Threading.Tasks.Parallel.For%2A> oluşturulabilir <xref:System.Collections.Generic.IEnumerable%601> kaynak koleksiyonu üzerinde nasıl bir döngü yazılacağını açıklar.|  
|[Nasıl yapılır: Basit bir Parallel. ForEach Döngüsü yazın](../../../docs/standard/parallel-programming/how-to-write-a-simple-parallel-foreach-loop.md)|<xref:System.Threading.Tasks.Parallel.ForEach%2A> Herhangi<xref:System.Collections.Generic.IEnumerable%601> bir kaynak koleksiyon üzerine bir döngü yazmayı açıklar.|  
|[Nasıl yapılır: Bir Parallel. for döngüsünden Durdur veya Kes](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/dd460721(v=vs.100))|Tüm iş parçacıklarının eyleme göre bilgilendirilmesi için paralel bir döngüden nasıl durulabileceğinizi veya kesilmesini açıklar.|  
|[Nasıl yapılır: Iş parçacığı yerel değişkenleriyle bir Parallel. for döngüsü yazın](../../../docs/standard/parallel-programming/how-to-write-a-parallel-for-loop-with-thread-local-variables.md)|Her bir iş parçacığının başka <xref:System.Threading.Tasks.Parallel.For%2A> bir iş parçacığı tarafından görülemeyen bir özel değişken tuttuğu ve döngü tamamlandığında sonuçların tüm iş parçacıklarında eşitlenmesi için bir döngü yazmayı açıklar.|  
|[Nasıl yapılır: Bölüm Yerel Değişkenleriyle bir Parallel. ForEach Döngüsü Yazma](../../../docs/standard/parallel-programming/how-to-write-a-parallel-foreach-loop-with-partition-local-variables.md)|Her bir iş parçacığının başka <xref:System.Threading.Tasks.Parallel.ForEach%2A> bir iş parçacığı tarafından görülemeyen bir özel değişken tuttuğu ve döngü tamamlandığında sonuçların tüm iş parçacıklarında eşitlenmesi için bir döngü yazmayı açıklar.|  
|[Nasıl yapılır: Bir Parallel. for veya ForEach döngüsünü iptal etme](../../../docs/standard/parallel-programming/how-to-cancel-a-parallel-for-or-foreach-loop.md)|Şunu kullanarak bir paralel döngünün nasıl iptal edileceğini açıklar<xref:System.Threading.CancellationToken?displayProperty=nameWithType>|  
|[Nasıl yapılır: Küçük döngü gövdelerini hızlandırın](../../../docs/standard/parallel-programming/how-to-speed-up-small-loop-bodies.md)|Döngü gövdesi çok küçük olduğunda yürütmeyi hızlandırmanın bir yolunu açıklar.|  
|[Görev Paralel Kitaplığı (TPL)](../../../docs/standard/parallel-programming/task-parallel-library-tpl.md)|Görev paralel kitaplığı için bir genel bakış sağlar.|  
|[Paralel Programlama](../../../docs/standard/parallel-programming/index.md)|.NET Framework paralel programlama sunar.|  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Paralel Programlama](../../../docs/standard/parallel-programming/index.md)
