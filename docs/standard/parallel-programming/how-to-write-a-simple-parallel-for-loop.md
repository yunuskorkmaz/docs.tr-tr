---
title: "Nasıl yapılır: Basit bir Parallel.For Döngüsü Yazma"
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
helpviewer_keywords:
- Parallel.For, How to Write
- for loop, parallel construction in .NET
- parallel for loops, how to use
ms.assetid: 9029ba7f-a9d1-4526-8c84-c88716dba5d4
caps.latest.revision: "18"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 3a70dcb5e3811a18e23aeb2ebf0940d2c52f49a9
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/23/2017
---
# <a name="how-to-write-a-simple-parallelfor-loop"></a>Nasıl yapılır: Basit bir Parallel.For Döngüsü Yazma
Bu konu, gösteren iki örnek içerir <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> yöntemi. İlk kullandığı <xref:System.Threading.Tasks.Parallel.For%28System.Int64%2CSystem.Int64%2CSystem.Action%7BSystem.Int64%7D%29?displayProperty=nameWithType> yöntemi aşırı yüklemesini ve ikinci kullandığı <xref:System.Threading.Tasks.Parallel.For%28System.Int32%2CSystem.Int32%2CSystem.Action%7BSystem.Int32%7D%29?displayProperty=nameWithType> aşırı yüklemesi, iki basit aşırı <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> yöntemi. Bu iki aşırı kullanabilirsiniz <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> döngüsünü iptal etmek gerekmediğinde yöntemi bölün döngüsü yinelemeleri dışında ya da herhangi bir iş parçacığı yerel durumu korumak.  
  
> [!NOTE]
>  TPL'de temsilciler tanımlamak için bu belgede lambda ifadeleri kullanılır. C# veya Visual Basic'deki lambda ifadeleri alışık değilseniz bkz [PLINQ ve TPL'deki Lambda ifadeleri](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md).  
  
 İlk örnek tek bir dizindeki dosyaların boyutunu hesaplar. İkinci iki matrisi çarpımını hesaplar.  
  
## <a name="example"></a>Örnek  
 Bu örnek, bir dizindeki dosyaların toplam boyutu hesaplar basit bir komut satırı yardımcı programıdır. Tek dizin yolu olarak bir bağımsız değişken bekler ve raporları numarası ve dizindeki dosyaların toplam boyutu. Dizinin var olduğunu doğruladıktan sonra onu kullanır <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> dizindeki dosyaları numaralandırma ve bunların dosya boyutunu belirlemek için yöntem. Her bir dosya boyutu daha sonra eklenen `totalSize` değişkeni. Eklenmesi çağırarak gerçekleştirildiğini unutmayın <xref:System.Threading.Interlocked.Add%2A?displayProperty=nameWithType> böylece eklenmesi atomik bir işlem olarak gerçekleştirilir. Aksi takdirde, birden çok görev güncelleştirme yararlanmaya `totalSize` değişken aynı anda.  
  
 [!code-csharp[Conceptual.Parallel.For#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.parallel.for/cs/for1.cs#1)]
 [!code-vb[Conceptual.Parallel.For#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.parallel.for/vb/for1.vb#1)]  
  
## <a name="example"></a>Örnek  
 Bu örnekte <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> yöntemi iki matrisi çarpımını hesaplar. Ayrıca nasıl kullanılacağını gösterir <xref:System.Diagnostics.Stopwatch?displayProperty=nameWithType> paralel olmayan döngü ile paralel bir döngüden performansını Karşılaştırılacak sınıfı. Çıktı büyük miktarda oluşturabileceğinden, örnek bir dosyaya yeniden yönlendirilmesi çıktı verdiğini unutmayın.  
  
 [!code-csharp[TPL_Parallel#01](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_parallel/cs/simpleparallelfor.cs#01)]
 [!code-vb[TPL_Parallel#01](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_parallel/vb/simpleparallelfor.vb#01)]  
  
 Döngüler, dahil olmak üzere herhangi bir kod parallelizing zaman bir önemli olduğu tüm performans avantajı paralel işleme yükünü üzerindeki geçersiz kılar noktasına parallelizing üzerinden olmadan mümkün olduğunca işlemciler kullanmaya hedeftir. İç döngüde gerçekleştirilen çok benzer iş olmadığından bu örnekte yalnızca dış döngü paralel birkaç ölçeklendirin. İş amaçlı ve istenmeyen önbellek etkileri az miktarda birleşimi iç içe geçmiş paralel Döngülerde performans düşüşüne neden olabilir. Bu nedenle, dış döngü parallelizing yalnızca çoğu sistemlerde eşzamanlılık yararlarını en üst düzeye çıkarmak için en iyi yoludur.  
  
## <a name="the-delegate"></a>Temsilci  
 Bu aşırı yüklemesi, üçüncü parametresinin <xref:System.Threading.Tasks.Parallel.For%2A> bir temsilci türü `Action<int>` C# veya `Action(Of Integer)` Visual Basic'te. Bir `Action` temsilcisi sıfır, bir veya altı tür parametreleri olup her zaman döndürür void. Visual Basic'te davranışını bir `Action` ile tanımlanmış bir `Sub`. Temsilciyi oluşturmak için örnek bir lambda ifadesi kullanır ancak temsilci diğer yollarla oluşturabilirsiniz. Daha fazla bilgi için bkz: [PLINQ ve TPL'deki Lambda ifadeleri](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md).  
  
## <a name="the-iteration-value"></a>Yineleme değeri  
 Temsilci geçerli yineleme değeri olan tek bir giriş parametresi alır. Çalışma zamanı tarafından sağlanan bu yineleme değeri ve başlangıç değeri geçerli iş parçacığı üzerinde işlenen kaynak (bölüm) kesimindeki ilk öğe dizinidir.  
  
 Eşzamanlılık düzeyi hakkında daha fazla denetime ihtiyacınız varsa, alan aşırı birini kullanın bir <xref:System.Threading.Tasks.ParallelOptions?displayProperty=nameWithType> gibi giriş parametresi: <xref:System.Threading.Tasks.Parallel.For%28System.Int32%2CSystem.Int32%2CSystem.Threading.Tasks.ParallelOptions%2CSystem.Action%7BSystem.Int32%2CSystem.Threading.Tasks.ParallelLoopState%7D%29?displayProperty=nameWithType>.  
  
## <a name="return-value-and-exception-handling"></a>Dönüş değeri ve özel durum işleme  
 <xref:System.Threading.Tasks.Parallel.For%2A>döndüren bir <xref:System.Threading.Tasks.ParallelLoopResult?displayProperty=nameWithType> tüm iş parçacıklarının tamamlandığında nesne. Bu dönüş değeri: yararlı, durdurma veya kesme döngü yineleme el ile çünkü <xref:System.Threading.Tasks.ParallelLoopResult> tamamlanıncaya kadar çalıştırılan son yineleme gibi bilgileri depolar. Bir veya daha fazla özel durumları iş parçacıkları birinde oluşursa bir <xref:System.AggregateException?displayProperty=nameWithType> oluşturulur.  
  
 Bu örnekte, dönüş değerini kodda <xref:System.Threading.Tasks.Parallel.For%2A> kullanılmaz.  
  
## <a name="analysis-and-performance"></a>Çözümleme ve performans  
 Performans Sihirbazı, bilgisayarınızda CPU kullanımı görüntülemek için kullanabilirsiniz. Bir deney matrisleri satırları ve sütunları sayısını artırın. Büyük matrislerini, hesaplama paralel ve sıralı sürümleri arasında performans farkı daha büyük. Matris küçük olduğunda, sıralı sürüm paralel döngü ayarlama yükü nedeniyle daha hızlı çalışacaktır.  
  
 Konsol veya dosya sistemi gibi paylaşılan kaynakları için zaman uyumlu çağrıları paralel bir döngüden performansını önemli ölçüde düşer. Çağrıları gibi önlemek performans ölçüm yaparken deneyin <xref:System.Console.WriteLine%2A?displayProperty=nameWithType> döngü içinde.  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
  
-   Bu kodu kopyalayıp bir Visual Studio 2010 projeye yapıştırın.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Threading.Tasks.Parallel.For%2A>  
 <xref:System.Threading.Tasks.Parallel.ForEach%2A>  
 [Veri Paralelliği](../../../docs/standard/parallel-programming/data-parallelism-task-parallel-library.md)  
 [Paralel Programlama](../../../docs/standard/parallel-programming/index.md)
