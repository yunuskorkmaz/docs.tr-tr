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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "73123156"
---
# <a name="data-parallelism-task-parallel-library"></a>Veri Paralelliği (Görev Paralel Kitaplığı)
*Veri paralelliği,* aynı işlemin aynı anda (yani paralel olarak) bir kaynak koleksiyonundaki veya dizideki öğeler üzerinde gerçekleştirildiği senaryoları ifade eder. Veri paralel işlemlerinde, kaynak toplama, birden çok iş parçacığının aynı anda farklı segmentlerde çalışabilmesi için bölümlenir.  
  
 Görev Paralel Kitaplığı (TPL), <xref:System.Threading.Tasks.Parallel?displayProperty=nameWithType> sınıf boyunca veri paralelcimini destekler. Bu [sınıf, for](../../csharp/language-reference/keywords/for.md) and [foreach](../../csharp/language-reference/keywords/foreach-in.md) döngülerinin (ve`For` `For Each` Visual Basic'te) yöntem tabanlı paralel uygulamalarını sağlar. Bir <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> veya <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> döngü için döngü mantığını, sıralı bir döngü yazdığın gibi yazarsınız. İş parçacıkları veya sıra çalışma öğeleri oluşturmak zorunda değilsin. Temel döngülerde kilit almak zorunda kalmamanız gerekmez. TPL sizin için tüm düşük seviyeli işleri yönetir. Paralel Programlama için belge [Desenleri: .NET Framework 4 ile Paralel Desenlerin Anlaşılması ve Uygulanması](https://www.microsoft.com/download/details.aspx?id=19222)hakkında ayrıntılı bilgi <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> için. <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> Aşağıdaki kod örneği basit `foreach` bir döngü ve paralel eşdeğeri gösterir.  
  
> [!NOTE]
> TPL'de temsilciler tanımlamak için bu belgede lambda ifadeleri kullanılır. C# veya Visual Basic'teki lambda ifadelerine aşina değilseniz, [PLINQ ve TPL'deki Lambda İfadeleri'ne](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md)bakın.  
  
 [!code-csharp[TPL#20](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl/cs/tpl.cs#20)]
 [!code-vb[TPL#20](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl/vb/tpl_vb.vb#20)]  
  
 Paralel bir döngü çalıştığında, TPL veri kaynağını bölümlere ayırır, böylece döngü aynı anda birden çok parça üzerinde çalışabilir. Arka planda, Görev Zamanlayıcısı görevi sistem kaynaklarına ve iş yüküne göre bölümlere ayırır. Mümkün olduğunda, iş yükü dengesizleşirse zamanlayıcı işi birden çok iş parçacığı ve işlemci arasında yeniden dağıtır.  
  
> [!NOTE]
> Ayrıca kendi özel bölümleyici veya zamanlayıcı sağlayabilir. Daha fazla bilgi [için PLINQ ve TPL ve](../../../docs/standard/parallel-programming/custom-partitioners-for-plinq-and-tpl.md) Görev Zamanlayıcıları için Özel [Bölümleyiciler'e](xref:System.Threading.Tasks.TaskScheduler)bakın.  
  
 Hem <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> yöntem <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> hem de döngü yürütmeyi durdurmanızı veya kesmenize, diğer iş parçacıklarındaki döngünün durumunu izlemenize, iş parçacığı yerel durumunu korumanıza, iş parçacığı yerel nesnelerini tamamlamanıza, eşzamanlılık derecesini denetlemenize ve benzeri neden olan birkaç aşırı yüklemeye sahiptir. Bu işlevselliği etkinleştiren yardımcı <xref:System.Threading.Tasks.ParallelLoopState> <xref:System.Threading.Tasks.ParallelOptions>türleri <xref:System.Threading.Tasks.ParallelLoopResult> <xref:System.Threading.CancellationToken>, <xref:System.Threading.CancellationTokenSource>, , ve .  
  
 Daha fazla bilgi [için bkz: Paralel Programlama Desenleri: .NET Framework 4 ile Paralel Desenleri Anlama ve Uygulama 4](https://www.microsoft.com/download/details.aspx?id=19222).  
  
 Bildirimsel veya sorgu benzeri sözdizimi ile veri paralelliği PLINQ tarafından desteklenir. Daha fazla bilgi için [Paralel LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)bakın.  
  
## <a name="related-topics"></a>İlgili Konular  
  
|Başlık|Açıklama|  
|-----------|-----------------|  
|[Nasıl yapılır: Basit bir Parallel.For Döngüsü Yazma](../../../docs/standard/parallel-programming/how-to-write-a-simple-parallel-for-loop.md)|Herhangi bir <xref:System.Threading.Tasks.Parallel.For%2A> dizi veya dizidüzenlenebilir <xref:System.Collections.Generic.IEnumerable%601> kaynak koleksiyonu üzerine döngü yazma nın nasıl yapılacağını açıklar.|  
|[Nasıl yapılır: Basit bir Parallel.ForEach Döngüsü Yazma](../../../docs/standard/parallel-programming/how-to-write-a-simple-parallel-foreach-loop.md)|Herhangi <xref:System.Threading.Tasks.Parallel.ForEach%2A> <xref:System.Collections.Generic.IEnumerable%601> bir kaynak koleksiyonu üzerine döngü nasıl yazılabildiğini açıklar.|  
|[Nasıl Yapilir: Parallel.For Loop'u Durdur veya Kır](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/dd460721(v=vs.100))|Tüm iş parçacıklarının eylemden haberdar olması için paralel bir döngüyü nasıl durdurup kırılabildiğini açıklar.|  
|[Nasıl yapılır: İş Parçacığı Yerel Değişkenleriyle bir Parallel.For Döngüsü Yazma](../../../docs/standard/parallel-programming/how-to-write-a-parallel-for-loop-with-thread-local-variables.md)|Her iş parçacığının diğer iş parçacıkları tarafından görülemeyen özel bir değişkeni koruduğu bir <xref:System.Threading.Tasks.Parallel.For%2A> döngünün nasıl yazılması gerektiğini ve döngü tamamlandığında tüm iş parçacıklarının sonuçlarını nasıl eşitleyeceklerini açıklar.|  
|[Nasıl yapılır: Bölüm Yerel Değişkenleriyle bir Parallel.ForEach Döngüsü Yazma](../../../docs/standard/parallel-programming/how-to-write-a-parallel-foreach-loop-with-partition-local-variables.md)|Her iş parçacığının diğer iş parçacıkları tarafından görülemeyen özel bir değişkeni koruduğu bir <xref:System.Threading.Tasks.Parallel.ForEach%2A> döngünün nasıl yazılması gerektiğini ve döngü tamamlandığında tüm iş parçacıklarının sonuçlarını nasıl eşitleyeceklerini açıklar.|  
|[Nasıl yapılır: Bir Parallel.For veya ForEach Döngüsünü İptal Etme](../../../docs/standard/parallel-programming/how-to-cancel-a-parallel-for-or-foreach-loop.md)|Bir paralel döngü kullanarak nasıl iptal edilir açıklar<xref:System.Threading.CancellationToken?displayProperty=nameWithType>|  
|[Nasıl yapılır: Küçük Döngü Gövdelerini Hızlandırma](../../../docs/standard/parallel-programming/how-to-speed-up-small-loop-bodies.md)|Döngü gövdesi çok küçükolduğunda yürütmeyi hızlandırmanın bir yolunu açıklar.|  
|[Görev Paralel Kitaplığı (TPL)](../../../docs/standard/parallel-programming/task-parallel-library-tpl.md)|Görev Paralel Kitaplığı'na genel bir bakış sağlar.|  
|[Paralel Programlama](../../../docs/standard/parallel-programming/index.md)|.NET Çerçevesinde Paralel Programlama'yı tanır.|  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Paralel Programlama](../../../docs/standard/parallel-programming/index.md)
