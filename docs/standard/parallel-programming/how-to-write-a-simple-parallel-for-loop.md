---
title: 'Nasıl yapılır: Basit bir Parallel.For Döngüsü Yazma'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Parallel.For, How to Write
- for loop, parallel construction in .NET
- parallel for loops, how to use
ms.assetid: 9029ba7f-a9d1-4526-8c84-c88716dba5d4
ms.openlocfilehash: 78f07a4f0118c6bce7a043f111988281ddd6add0
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73139663"
---
# <a name="how-to-write-a-simple-parallelfor-loop"></a>Nasıl yapılır: Basit bir Parallel.For Döngüsü Yazma

Bu konu, <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> yöntemini gösteren iki örnek içerir. İlki <xref:System.Threading.Tasks.Parallel.For%28System.Int64%2CSystem.Int64%2CSystem.Action%7BSystem.Int64%7D%29?displayProperty=nameWithType> yöntemi aşırı yüklemesini kullanır ve ikincisi <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> yönteminin iki en basit aşırı yüklemesi olan <xref:System.Threading.Tasks.Parallel.For%28System.Int32%2CSystem.Int32%2CSystem.Action%7BSystem.Int32%7D%29?displayProperty=nameWithType> aşırı yüklemeyi kullanır. Döngüyü iptal etmeniz, döngü yinelemelerini kesmeniz veya herhangi bir iş parçacığı yerel durumunu sürdürmenize gerek olmadığında <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> yönteminin bu iki yüklerini kullanabilirsiniz.

> [!NOTE]
> TPL'de temsilciler tanımlamak için bu belgede lambda ifadeleri kullanılır. Veya Visual Basic içindeki C# lambda ifadeleriyle ilgili bilgi sahibi değilseniz bkz. [PLıNQ ve TPL içindeki lambda ifadeleri](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md).

İlk örnek, tek bir dizindeki dosyaların boyutunu hesaplar. İkincisi iki matrisin çarpımını hesaplar.

## <a name="directory-size-example"></a>Dizin boyutu örneği

Bu örnek, bir dizindeki dosyaların toplam boyutunu hesaplayan basit bir komut satırı yardımcı programıdır. Bağımsız değişken olarak tek bir dizin yolu bekler ve bu dizindeki dosyaların sayısını ve toplam boyutunu raporlar. Dizinin mevcut olduğunu doğruladıktan sonra, dizindeki dosyaları numaralandırma ve dosya boyutlarını belirleme <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> yöntemini kullanır. Her dosya boyutu `totalSize` değişkenine eklenir. Toplama işleminin atomik bir işlem olarak gerçekleştirilmesi için <xref:System.Threading.Interlocked.Add%2A?displayProperty=nameWithType> çağırarak bunun gerçekleştirildiğinden emin olmanız gerektiğini unutmayın. Aksi takdirde, birden çok görev `totalSize` değişkenini eşzamanlı olarak güncelleştirmeyi deneyebilir.

[!code-csharp[Conceptual.Parallel.For#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.parallel.for/cs/for1.cs#1)]
[!code-vb[Conceptual.Parallel.For#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.parallel.for/vb/for1.vb#1)]

## <a name="matrix-and-stopwatch-example"></a>Matris ve kronometre örneği

Bu örnek, iki matrisinin çarpımını hesaplamak için <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> yöntemini kullanır. Ayrıca, paralel olmayan bir döngüyle paralel bir döngünün performansını karşılaştırmak için <xref:System.Diagnostics.Stopwatch?displayProperty=nameWithType> sınıfını nasıl kullanacağınızı gösterir. Büyük bir çıkış hacmi üretebildiğinden, örneğin çıktının bir dosyaya yeniden yönlendirilmesine izin verdiğini unutmayın.

[!code-csharp[TPL_Parallel#01](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_parallel/cs/simpleparallelfor.cs#01)]
[!code-vb[TPL_Parallel#01](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_parallel/vb/simpleparallelfor.vb#01)]

Döngüler dahil olmak üzere herhangi bir kodu paralelleştirdiğinde, önemli bir amaç, paralel işleme yükünün herhangi bir performans avantajlarından yararlanmasına neden olacak şekilde, işlemciyi paralelleştirmeden mümkün olduğunca çok daha fazla kullanır. Bu örnekte, iç döngüde çok fazla iş gerçekleştirilmediğinden yalnızca dış döngü paralelleştirildi. Az miktarda iş ve istenmeyen önbellek efektlerinin birleşimi, iç içe paralel Döngülerde performans düşüşüne neden olabilir. Bu nedenle, dış döngüyü paralelleştirme, çoğu sistemde eşzamanlılık avantajlarından en iyi şekilde yararlanmanın en iyi yoludur.

## <a name="the-delegate"></a>Temsilci

Bu <xref:System.Threading.Tasks.Parallel.For%2A> aşırı yüklemesinin üçüncü parametresi, Visual Basic içinde `Action<int>` C# veya `Action(Of Integer)` türünde bir temsilcisidir. Sıfır, bir veya on altı tür parametresi olup olmadığı, her zaman void döndüren bir `Action` temsilcisi. Visual Basic, bir `Action` davranışı bir `Sub`ile tanımlanır. Örnek, temsilciyi oluşturmak için bir lambda ifadesi kullanır, ancak temsilciyi başka yollarla da oluşturabilirsiniz. Daha fazla bilgi için bkz. [PLıNQ ve TPL 'Deki lambda ifadeleri](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md).

## <a name="the-iteration-value"></a>Yineleme değeri

Temsilci, değeri geçerli yineleme olan tek bir giriş parametresi alır. Bu yineleme değeri çalışma zamanı tarafından sağlanır ve başlangıç değeri, geçerli iş parçacığında işlenmekte olan kaynağın segmentindeki (bölüm) ilk öğenin dizinidir.

Eşzamanlılık düzeyi üzerinde daha fazla denetime ihtiyacınız varsa, <xref:System.Threading.Tasks.ParallelOptions?displayProperty=nameWithType> giriş parametresi alan aşırı yüklerden birini kullanın, örneğin: <xref:System.Threading.Tasks.Parallel.For%28System.Int32%2CSystem.Int32%2CSystem.Threading.Tasks.ParallelOptions%2CSystem.Action%7BSystem.Int32%2CSystem.Threading.Tasks.ParallelLoopState%7D%29?displayProperty=nameWithType>.

## <a name="return-value-and-exception-handling"></a>Dönüş değeri ve özel durum Işleme

<xref:System.Threading.Tasks.Parallel.For%2A>, tüm iş parçacıkları tamamlandığında bir <xref:System.Threading.Tasks.ParallelLoopResult?displayProperty=nameWithType> nesnesi döndürür. Bu dönüş değeri, <xref:System.Threading.Tasks.ParallelLoopResult> tamamlama için çalıştırılan son yineleme gibi bilgileri depoladığı için döngü yinelemesini el ile durdururken veya parçaladığında faydalıdır. İş parçacıklarından birinde bir veya daha fazla özel durum oluşursa, bir <xref:System.AggregateException?displayProperty=nameWithType> oluşturulur.

Bu örnekteki kodda, <xref:System.Threading.Tasks.Parallel.For%2A> dönüş değeri kullanılmaz.

## <a name="analysis-and-performance"></a>Analiz ve performans

Bilgisayarınızdaki CPU kullanımını görüntülemek için performans sihirbazını kullanabilirsiniz. Bir deneme olarak, matrislerde sütun ve satır sayısını artırın. Matrisler arttıkça, hesaplamanın paralel ve sıralı sürümleri arasındaki performans farkı artar. Matris küçük olduğunda, paralel döngü ayarlamadaki ek yük nedeniyle sıralı sürüm daha hızlı çalışır.

Konsol veya dosya sistemi gibi paylaşılan kaynaklara zaman uyumlu çağrılar, paralel bir döngünün performansını önemli ölçüde azaltır. Performansı ölçerek, döngü içinde <xref:System.Console.WriteLine%2A?displayProperty=nameWithType> gibi çağrılardan kaçınmaya çalışın.

## <a name="compile-the-code"></a>Kodu derle

Bu kodu kopyalayıp bir Visual Studio projesine yapıştırın.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Threading.Tasks.Parallel.For%2A>
- <xref:System.Threading.Tasks.Parallel.ForEach%2A>
- [Veri Paralelliği](../../../docs/standard/parallel-programming/data-parallelism-task-parallel-library.md)
- [Paralel Programlama](../../../docs/standard/parallel-programming/index.md)
