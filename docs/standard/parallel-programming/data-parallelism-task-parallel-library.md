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
ms.openlocfilehash: 72696a41cd3b71f47fdcf43e4ece70ebeb7d34d1
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73123156"
---
# <a name="data-parallelism-task-parallel-library"></a>Veri Paralelliği (Görev Paralel Kitaplığı)
*Veri paralelliği* , kaynak koleksiyondaki veya dizideki öğelerde aynı işlemin eşzamanlı olarak (yani paralel) gerçekleştirildiği senaryolara başvurur. Veri paralel işlemlerinde, kaynak koleksiyon, birden çok iş parçacığının aynı anda farklı kesimlerde çalışabilmesi için bölümlenmiş olur.  
  
 Görev paralel kitaplığı (TPL) <xref:System.Threading.Tasks.Parallel?displayProperty=nameWithType> sınıfı aracılığıyla verileri paralellik olarak destekler. Bu sınıf, for ve [foreach](../../csharp/language-reference/keywords/foreach-in.md) döngülerine [yönelik](../../csharp/language-reference/keywords/for.md) Yöntem tabanlı paralel uygulamalar (`For` ve Visual Basic `For Each`) sağlar. Bir <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> veya <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> döngüsü için döngü mantığını yazdığınızda, sıralı bir döngü yazarsınız. İş parçacığı oluşturmak veya iş öğelerini kuyruğa almak zorunda değilsiniz. Temel Döngülerde kilit almanız gerekmez. TPL, tüm düşük düzeydeki işleri sizin için işler. <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> ve <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType>kullanımı hakkında ayrıntılı bilgi için, [paralel programlama için belge desenlerini indirin: .NET Framework 4 Ile paralel desenleri anlama ve uygulama](https://www.microsoft.com/download/details.aspx?id=19222). Aşağıdaki kod örneği, basit bir `foreach` döngüsünü ve onun paralel eşdeğerini gösterir.  
  
> [!NOTE]
> TPL'de temsilciler tanımlamak için bu belgede lambda ifadeleri kullanılır. Veya Visual Basic içindeki C# lambda ifadeleriyle ilgili bilgi sahibi değilseniz bkz. [PLıNQ ve TPL içindeki lambda ifadeleri](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md).  
  
 [!code-csharp[TPL#20](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl/cs/tpl.cs#20)]
 [!code-vb[TPL#20](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl/vb/tpl_vb.vb#20)]  
  
 Bir paralel döngü çalıştığında, çağrının birden çok parçaya eşzamanlı olarak çalışabilmesi için, TPL veri kaynağını bölümlendirir. Arka planda Görev Zamanlayıcı, görevi sistem kaynakları ve iş yüküne göre bölümler. Mümkün olduğunda Zamanlayıcı, iş yükü dengesiz hale gelirse birden çok iş parçacığı ve işlemci arasında çalışmayı yeniden dağıtır.  
  
> [!NOTE]
> Ayrıca kendi özel bölümleyici veya Scheduler 'ı da sağlayabilirsiniz. Daha fazla bilgi için bkz. [PLıNQ ve TPL Için Özel Bölümleyiciler](../../../docs/standard/parallel-programming/custom-partitioners-for-plinq-and-tpl.md) ve [görev zamanlayıcılar](xref:System.Threading.Tasks.TaskScheduler).  
  
 <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> ve <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> yöntemlerinin her ikisi de, döngü yürütmeyi durdurmanızı veya sonlandırarak, diğer iş parçacıklarında döngülerin durumunu izlemenize, iş parçacığı yerel durumunu sürdürmenize, iş parçacığı yerel nesnelerini ve bu şekilde devam etmenize olanak tanıyan birkaç aşırı yükleme vardır. Bu işlevi etkinleştiren yardımcı türler <xref:System.Threading.Tasks.ParallelLoopState>, <xref:System.Threading.Tasks.ParallelOptions>, <xref:System.Threading.Tasks.ParallelLoopResult>, <xref:System.Threading.CancellationToken>ve <xref:System.Threading.CancellationTokenSource>içerir.  
  
 Daha fazla bilgi için bkz. [paralel programlama desenleri: .NET Framework 4 Ile paralel desenleri anlama ve uygulama](https://www.microsoft.com/download/details.aspx?id=19222).  
  
 Bildirim temelli veya sorgu benzeri, sözdizimi ile veri paralelliği, PLıNQ tarafından desteklenir. Daha fazla bilgi için bkz. [Parallel LINQ (PLıNQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md).  
  
## <a name="related-topics"></a>İlgili Konular  
  
|Başlık|Açıklama|  
|-----------|-----------------|  
|[Nasıl yapılır: Basit bir Parallel.For Döngüsü Yazma](../../../docs/standard/parallel-programming/how-to-write-a-simple-parallel-for-loop.md)|Herhangi bir dizi veya dizin <xref:System.Collections.Generic.IEnumerable%601> kaynak koleksiyonu üzerinde <xref:System.Threading.Tasks.Parallel.For%2A> döngüsünün nasıl yazılacağını açıklar.|  
|[Nasıl yapılır: Basit bir Parallel.ForEach Döngüsü Yazma](../../../docs/standard/parallel-programming/how-to-write-a-simple-parallel-foreach-loop.md)|Herhangi bir <xref:System.Collections.Generic.IEnumerable%601> kaynak koleksiyonu üzerinde <xref:System.Threading.Tasks.Parallel.ForEach%2A> döngüsünün nasıl yazılacağını açıklar.|  
|[Nasıl yapılır: Parallel. for döngüsünü durdurma veya kesme](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/dd460721(v=vs.100))|Tüm iş parçacıklarının eyleme göre bilgilendirilmesi için paralel bir döngüden nasıl durulabileceğinizi veya kesilmesini açıklar.|  
|[Nasıl yapılır: İş Parçacığı Yerel Değişkenleriyle bir Parallel.For Döngüsü Yazma](../../../docs/standard/parallel-programming/how-to-write-a-parallel-for-loop-with-thread-local-variables.md)|Her bir iş parçacığının başka bir iş parçacığı tarafından görülemeyen bir özel değişken tuttuğu ve döngü tamamlandığında sonuçların tüm iş parçacıklarında eşitlenmesi için bir <xref:System.Threading.Tasks.Parallel.For%2A> döngüsünün nasıl yazılacağını açıklar.|  
|[Nasıl yapılır: Bölüm Yerel Değişkenleriyle bir Parallel.ForEach Döngüsü Yazma](../../../docs/standard/parallel-programming/how-to-write-a-parallel-foreach-loop-with-partition-local-variables.md)|Her bir iş parçacığının başka bir iş parçacığı tarafından görülemeyen bir özel değişken tuttuğu ve döngü tamamlandığında sonuçların tüm iş parçacıklarında eşitlenmesi için bir <xref:System.Threading.Tasks.Parallel.ForEach%2A> döngüsünün nasıl yazılacağını açıklar.|  
|[Nasıl yapılır: Bir Parallel.For veya ForEach Döngüsünü İptal Etme](../../../docs/standard/parallel-programming/how-to-cancel-a-parallel-for-or-foreach-loop.md)|<xref:System.Threading.CancellationToken?displayProperty=nameWithType> kullanarak paralel bir döngünün nasıl iptal edileceğini açıklar|  
|[Nasıl yapılır: Küçük Döngü Gövdelerini Hızlandırma](../../../docs/standard/parallel-programming/how-to-speed-up-small-loop-bodies.md)|Döngü gövdesi çok küçük olduğunda yürütmeyi hızlandırmanın bir yolunu açıklar.|  
|[Görev Paralel Kitaplığı (TPL)](../../../docs/standard/parallel-programming/task-parallel-library-tpl.md)|Görev paralel kitaplığı için bir genel bakış sağlar.|  
|[Paralel Programlama](../../../docs/standard/parallel-programming/index.md)|.NET Framework paralel programlama sunar.|  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Paralel Programlama](../../../docs/standard/parallel-programming/index.md)
