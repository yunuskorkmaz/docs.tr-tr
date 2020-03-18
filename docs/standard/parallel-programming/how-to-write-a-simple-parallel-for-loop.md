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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "73139663"
---
# <a name="how-to-write-a-simple-parallelfor-loop"></a>Nasıl yapılır: Basit bir Parallel.For Döngüsü Yazma

Bu konu <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> yöntemi gösteren iki örnek içerir. İlk <xref:System.Threading.Tasks.Parallel.For%28System.Int64%2CSystem.Int64%2CSystem.Action%7BSystem.Int64%7D%29?displayProperty=nameWithType> yöntem aşırı yükleme kullanır ve ikinci <xref:System.Threading.Tasks.Parallel.For%28System.Int32%2CSystem.Int32%2CSystem.Action%7BSystem.Int32%7D%29?displayProperty=nameWithType> aşırı yükleme kullanır, <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> yöntemin en basit iki aşırı yükleri. Döngüyü iptal etme, döngü <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> yinelemelerini koparmanız veya iş parçacığı yerel durumunu korumanız gerekmediğinde bu iki yöntemin aşırı yükünü kullanabilirsiniz.

> [!NOTE]
> TPL'de temsilciler tanımlamak için bu belgede lambda ifadeleri kullanılır. C# veya Visual Basic'teki lambda ifadelerine aşina değilseniz, [PLINQ ve TPL'deki Lambda İfadeleri'ne](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md)bakın.

İlk örnek, tek bir dizindeki dosyaların boyutunu hesaplar. İkinci iki matrisin ürünlerini hesaplar.

## <a name="directory-size-example"></a>Dizin boyutu örneği

Bu örnek, bir dizindeki dosyaların toplam boyutunu hesaplayan basit bir komut satırı yardımcı programıdır. Bağımsız değişken olarak tek bir dizin yolu bekler ve bu dizindeki dosyaların sayısını ve toplam boyutunu bildirir. Dizinin var olduğunu doğruladıktan sonra, <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> dizindeki dosyaları numaralandırmak ve dosya boyutlarını belirlemek için yöntemi kullanır. Her dosya boyutu daha `totalSize` sonra değişkene eklenir. Ekleme nin atomik bir işlem <xref:System.Threading.Interlocked.Add%2A?displayProperty=nameWithType> olarak gerçekleştirilebilmeleri için çağrılar ekleyerek gerçekleştirildiğini unutmayın. Aksi takdirde, birden çok `totalSize` görev değişkeni aynı anda güncelleştirmeyi deneyebilir.

[!code-csharp[Conceptual.Parallel.For#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.parallel.for/cs/for1.cs#1)]
[!code-vb[Conceptual.Parallel.For#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.parallel.for/vb/for1.vb#1)]

## <a name="matrix-and-stopwatch-example"></a>Matris ve kronometre örneği

Bu örnek, <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> iki matrisin ürünlerini hesaplamak için yöntemi kullanır. Ayrıca, paralel döngünün <xref:System.Diagnostics.Stopwatch?displayProperty=nameWithType> performansını paralel olmayan bir döngüyle karşılaştırmak için sınıfın nasıl kullanılacağını da gösterir. Büyük miktarda çıktı oluşturabildiği için, örneğin çıktının bir dosyaya yönlendirilmesine izin verdiğini unutmayın.

[!code-csharp[TPL_Parallel#01](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_parallel/cs/simpleparallelfor.cs#01)]
[!code-vb[TPL_Parallel#01](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_parallel/vb/simpleparallelfor.vb#01)]

Döngüler de dahil olmak üzere herhangi bir kodu paralelleştirirken, önemli bir amaç, paralel işleme için ek yükün herhangi bir performans avantajını yok ettiği noktaya paralelleme yapmadan işlemcileri mümkün olduğunca kullanmaktır. Bu özel örnekte, iç döngüde çok fazla çalışma yapılmadığından, yalnızca dış döngü paralelleştirilmiştir. Az miktarda çalışma ve istenmeyen önbellek efektlerinin birleşimi iç içe paralel döngülerde performans düşüşüne neden olabilir. Bu nedenle, dış döngüyü yalnızca paralelleştirmek, çoğu sistemde eşzamanlılık faydalarını en üst düzeye çıkarmanın en iyi yoludur.

## <a name="the-delegate"></a>Temsilci

Bu aşırı yükün <xref:System.Threading.Tasks.Parallel.For%2A> üçüncü parametresi C# veya `Action<int>` `Action(Of Integer)` Visual Basic'te bir tür temsilcisidir. Bir `Action` temsilci, ister sıfır, ister bir veya on altı tür parametreye sahip olsun, her zaman geçersiz olarak döndürür. Visual Basic'te, bir `Action` davranışı bir `Sub`. ile tanımlanır Örnek, temsilciyi oluşturmak için bir lambda ifadesi kullanır, ancak temsilciyi başka şekillerde de oluşturabilirsiniz. Daha fazla bilgi için [PLINQ ve TPL'deki Lambda İfadeleri'ne](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md)bakın.

## <a name="the-iteration-value"></a>Yineleme Değeri

Temsilci, değeri geçerli yineleme olan tek bir giriş parametresini alır. Bu yineleme değeri çalışma zamanı tarafından sağlanır ve başlangıç değeri, geçerli iş parçacığı üzerinde işlenen kaynağın segmentindeki (bölüm) ilk öğenin dizinidir.

Eşzamanlılık düzeyi üzerinde daha fazla denetime ihtiyaç duyuyorsanız, <xref:System.Threading.Tasks.ParallelOptions?displayProperty=nameWithType> aşağıdakiler gibi bir giriş <xref:System.Threading.Tasks.Parallel.For%28System.Int32%2CSystem.Int32%2CSystem.Threading.Tasks.ParallelOptions%2CSystem.Action%7BSystem.Int32%2CSystem.Threading.Tasks.ParallelLoopState%7D%29?displayProperty=nameWithType>parametresi alan aşırı yüklerden birini kullanın: .

## <a name="return-value-and-exception-handling"></a>İade Değeri ve Özel Durum Taşıma

<xref:System.Threading.Tasks.Parallel.For%2A>tüm <xref:System.Threading.Tasks.ParallelLoopResult?displayProperty=nameWithType> iş parçacıkları tamamlandığında bir nesne döndürür. Bu iade değeri, döngü yinelemesini el ile durdururken veya <xref:System.Threading.Tasks.ParallelLoopResult> kırarken yararlıdır, çünkü tamamlanmak üzere olan son yineleme gibi bilgileri depolar. İş iş parçacığı birinde bir veya daha fazla <xref:System.AggregateException?displayProperty=nameWithType> özel durum oluşursa, bir tane atılır.

Bu örnekteki kodda, iade <xref:System.Threading.Tasks.Parallel.For%2A> değeri kullanılmaz.

## <a name="analysis-and-performance"></a>Analiz ve Performans

BilgisayarınızdaCPU kullanımını görüntülemek için Performans Sihirbazı'nı kullanabilirsiniz. Deneme olarak, matrislerde sütun ve satır sayısını artırın. Matrisler ne kadar büyükse, hesaplamanın paralel ve sıralı sürümleri arasındaki performans farkı da o kadar büyük türler. Matris küçük olduğunda, paralel döngüyü ayarlamadaki ek yükü nedeniyle sıralı sürüm daha hızlı çalışır.

Konsol veya Dosya Sistemi gibi paylaşılan kaynaklara yapılan eşzamanlı çağrılar, paralel bir döngünün performansını önemli ölçüde düşürür. Performansı ölçerken, döngü içindeki <xref:System.Console.WriteLine%2A?displayProperty=nameWithType> gibi çağrılardan kaçınmaya çalışın.

## <a name="compile-the-code"></a>Kodu Derleme

Bu kodu Visual Studio projesine kopyalayıp yapıştırın.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Threading.Tasks.Parallel.For%2A>
- <xref:System.Threading.Tasks.Parallel.ForEach%2A>
- [Veri Paralelliği](../../../docs/standard/parallel-programming/data-parallelism-task-parallel-library.md)
- [Paralel Programlama](../../../docs/standard/parallel-programming/index.md)
