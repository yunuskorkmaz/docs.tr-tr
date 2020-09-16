---
title: Veri Paralelliği (Görev Paralel Kitaplığı)
description: Görev paralel kitaplığı (TPL), .NET 'teki bir kaynak koleksiyon veya dizi öğelerinde aynı işlemi eşzamanlı olarak yapmak için veri paralelliğini nasıl desteklediğini okuyun.
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- parallelism, data
ms.assetid: 3f05f33f-f1da-4b16-81c2-9ceff1bef449
ms.openlocfilehash: 617757581f6d2491098e1172072bdf0387c6852b
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90558920"
---
# <a name="data-parallelism-task-parallel-library"></a>Veri Paralelliği (Görev Paralel Kitaplığı)
*Veri paralelliği* , kaynak koleksiyondaki veya dizideki öğelerde aynı işlemin eşzamanlı olarak (yani paralel) gerçekleştirildiği senaryolara başvurur. Veri paralel işlemlerinde, kaynak koleksiyon, birden çok iş parçacığının aynı anda farklı kesimlerde çalışabilmesi için bölümlenmiş olur.  
  
 Görev paralel kitaplığı (TPL), sınıfı aracılığıyla verileri paralellik olarak destekler <xref:System.Threading.Tasks.Parallel?displayProperty=nameWithType> . Bu sınıf [for](../../csharp/language-reference/keywords/for.md) ve [foreach](../../csharp/language-reference/keywords/foreach-in.md) döngüleri ( `For` ve Visual Basic) için yöntem tabanlı paralel uygulamalar sağlar `For Each` . <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType>Sıralı bir döngü yazdığınızda bir veya döngüsünün döngü mantığını yazın <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> . İş parçacığı oluşturmak veya iş öğelerini kuyruğa almak zorunda değilsiniz. Temel Döngülerde kilit almanız gerekmez. TPL, tüm düşük düzeydeki işleri sizin için işler. Ve kullanımı hakkında ayrıntılı bilgi için <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> , [paralel programlama için belge desenlerini indirin: .NET Framework 4 Ile paralel desenleri anlama ve uygulama](https://www.microsoft.com/download/details.aspx?id=19222). Aşağıdaki kod örneğinde basit bir `foreach` döngü ve onun paralel eşdeğeri gösterilmektedir.  
  
> [!NOTE]
> TPL'de temsilciler tanımlamak için bu belgede lambda ifadeleri kullanılır. C# veya Visual Basic lambda ifadeleriyle ilgili bilgi sahibi değilseniz bkz. [PLıNQ ve TPL Içindeki lambda ifadeleri](lambda-expressions-in-plinq-and-tpl.md).  
  
 [!code-csharp[TPL#20](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl/cs/tpl.cs#20)]
 [!code-vb[TPL#20](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl/vb/tpl_vb.vb#20)]  
  
 Bir paralel döngü çalıştığında, çağrının birden çok parçaya eşzamanlı olarak çalışabilmesi için, TPL veri kaynağını bölümlendirir. Arka planda Görev Zamanlayıcı, görevi sistem kaynakları ve iş yüküne göre bölümler. Mümkün olduğunda Zamanlayıcı, iş yükü dengesiz hale gelirse birden çok iş parçacığı ve işlemci arasında çalışmayı yeniden dağıtır.  
  
> [!NOTE]
> Ayrıca kendi özel bölümleyici veya Scheduler 'ı da sağlayabilirsiniz. Daha fazla bilgi için bkz. [PLıNQ ve TPL Için Özel Bölümleyiciler](custom-partitioners-for-plinq-and-tpl.md) ve [görev zamanlayıcılar](xref:System.Threading.Tasks.TaskScheduler).  
  
 Ve yöntemlerinin her ikisi de, <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> döngü yürütmeyi durdurmanızı veya sonlandırmasını, diğer iş parçacıklarında döngünün durumunu izlemenizi, iş parçacığı yerel durumunu, iş parçacığı yerel nesnelerini, eşzamanlılık derecesini ve bu şekilde devam etmenize olanak tanıyan birkaç aşırı yükleme vardır. Bu işlevi etkinleştiren yardımcı türler,,, <xref:System.Threading.Tasks.ParallelLoopState> <xref:System.Threading.Tasks.ParallelOptions> ve içerir <xref:System.Threading.Tasks.ParallelLoopResult> <xref:System.Threading.CancellationToken> <xref:System.Threading.CancellationTokenSource> .  
  
 Daha fazla bilgi için bkz. [paralel programlama desenleri: .NET Framework 4 Ile paralel desenleri anlama ve uygulama](https://www.microsoft.com/download/details.aspx?id=19222).  
  
 Bildirim temelli veya sorgu benzeri, sözdizimi ile veri paralelliği, PLıNQ tarafından desteklenir. Daha fazla bilgi için bkz. [Parallel LINQ (PLıNQ)](introduction-to-plinq.md).  
  
## <a name="related-topics"></a>İlgili Konular  
  
|Başlık|Açıklama|  
|-----------|-----------------|  
|[Nasıl yapılır: Basit bir Parallel.For Döngüsü Yazma](how-to-write-a-simple-parallel-for-loop.md)|<xref:System.Threading.Tasks.Parallel.For%2A>Herhangi bir dizi veya dizin oluşturulabilir kaynak koleksiyonu üzerinde nasıl bir döngü yazılacağını açıklar <xref:System.Collections.Generic.IEnumerable%601> .|  
|[Nasıl yapılır: Basit bir Parallel.ForEach Döngüsü Yazma](how-to-write-a-simple-parallel-foreach-loop.md)|<xref:System.Threading.Tasks.Parallel.ForEach%2A>Herhangi bir kaynak koleksiyon üzerine bir döngü yazmayı açıklar <xref:System.Collections.Generic.IEnumerable%601> .|  
|[Nasıl yapılır: Parallel. for döngüsünü durdurma veya kesme](/previous-versions/dotnet/netframework-4.0/dd460721(v=vs.100))|Tüm iş parçacıklarının eyleme göre bilgilendirilmesi için paralel bir döngüden nasıl durulabileceğinizi veya kesilmesini açıklar.|  
|[Nasıl yapılır: İş Parçacığı Yerel Değişkenleriyle bir Parallel.For Döngüsü Yazma](how-to-write-a-parallel-for-loop-with-thread-local-variables.md)|<xref:System.Threading.Tasks.Parallel.For%2A>Her bir iş parçacığının başka bir iş parçacığı tarafından görülemeyen bir özel değişken tuttuğu ve döngü tamamlandığında sonuçların tüm iş parçacıklarında eşitlenmesi için bir döngü yazmayı açıklar.|  
|[Nasıl yapılır: Bölüm Yerel Değişkenleriyle bir Parallel.ForEach Döngüsü Yazma](how-to-write-a-parallel-foreach-loop-with-partition-local-variables.md)|<xref:System.Threading.Tasks.Parallel.ForEach%2A>Her bir iş parçacığının başka bir iş parçacığı tarafından görülemeyen bir özel değişken tuttuğu ve döngü tamamlandığında sonuçların tüm iş parçacıklarında eşitlenmesi için bir döngü yazmayı açıklar.|  
|[Nasıl yapılır: Bir Parallel.For veya ForEach Döngüsünü İptal Etme](how-to-cancel-a-parallel-for-or-foreach-loop.md)|Şunu kullanarak bir paralel döngünün nasıl iptal edileceğini açıklar <xref:System.Threading.CancellationToken?displayProperty=nameWithType>|  
|[Nasıl yapılır: Küçük Döngü Gövdelerini Hızlandırma](how-to-speed-up-small-loop-bodies.md)|Döngü gövdesi çok küçük olduğunda yürütmeyi hızlandırmanın bir yolunu açıklar.|  
|[Görev Paralel Kitaplığı (TPL)](task-parallel-library-tpl.md)|Görev paralel kitaplığı için bir genel bakış sağlar.|  
|[Paralel programlama](index.md)|.NET Framework paralel programlama sunar.|  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Paralel programlama](index.md)
