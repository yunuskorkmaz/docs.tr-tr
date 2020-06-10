---
title: 'Nasıl yapılır: Basit bir Parallel.For Döngüsü Yazma'
description: Döngüyü iptal etmeniz, döngü yinelemelerini kesmeniz veya herhangi bir iş parçacığı yerel durumunu sürdürmeniz gerekmeyen .NET 'teki Parallel. for döngüleri yazmayı öğrenin.
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
ms.openlocfilehash: 8307f2205653fbd213d824acffc405ee97580166
ms.sourcegitcommit: 7137e12f54c4e83a94ae43ec320f8cf59c1772ea
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/10/2020
ms.locfileid: "84662699"
---
# <a name="how-to-write-a-simple-parallelfor-loop"></a>Nasıl yapılır: Basit bir Parallel.For Döngüsü Yazma

Bu konu, yöntemi gösteren iki örnek içerir <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> . İlki <xref:System.Threading.Tasks.Parallel.For%28System.Int64%2CSystem.Int64%2CSystem.Action%7BSystem.Int64%7D%29?displayProperty=nameWithType> yöntem aşırı yüklemesini kullanır ve ikincisi, <xref:System.Threading.Tasks.Parallel.For%28System.Int32%2CSystem.Int32%2CSystem.Action%7BSystem.Int32%7D%29?displayProperty=nameWithType> yönteminin iki en basit aşırı yüklemesi olan aşırı yüklemeyi kullanır <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> . <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType>Yöntemi iptal etmeniz, döngü yinelemelerini kesmeniz veya herhangi bir iş parçacığı yerel durumunu sürdürmenize gerek olmadığında, bu iki aşırı yüklemeyi kullanabilirsiniz.

> [!NOTE]
> TPL'de temsilciler tanımlamak için bu belgede lambda ifadeleri kullanılır. C# veya Visual Basic lambda ifadeleriyle ilgili bilgi sahibi değilseniz bkz. [PLıNQ ve TPL Içindeki lambda ifadeleri](lambda-expressions-in-plinq-and-tpl.md).

İlk örnek, tek bir dizindeki dosyaların boyutunu hesaplar. İkincisi iki matrisin çarpımını hesaplar.

## <a name="directory-size-example"></a>Dizin boyutu örneği

Bu örnek, bir dizindeki dosyaların toplam boyutunu hesaplayan basit bir komut satırı yardımcı programıdır. Bağımsız değişken olarak tek bir dizin yolu bekler ve bu dizindeki dosyaların sayısını ve toplam boyutunu raporlar. Dizinin mevcut olduğunu doğruladıktan sonra, <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> dizindeki dosyaları numaralandırma ve dosya boyutlarını belirleme yöntemini kullanır. Her dosya boyutu, `totalSize` değişkenine eklenir. Ek, <xref:System.Threading.Interlocked.Add%2A?displayProperty=nameWithType> ek bir atomik işlem olarak gerçekleştirilmeleri için çağırarak, çağrısı yaparak gerçekleştirilmiş olduğunu unutmayın. Aksi takdirde, birden çok görev değişkeni eşzamanlı olarak güncelleştirmeyi deneyebilir `totalSize` .

[!code-csharp[Conceptual.Parallel.For#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.parallel.for/cs/for1.cs#1)]
[!code-vb[Conceptual.Parallel.For#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.parallel.for/vb/for1.vb#1)]

## <a name="matrix-and-stopwatch-example"></a>Matris ve kronometre örneği

Bu örnek, <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> iki matrisin çarpımını hesaplamak için yöntemini kullanır. Ayrıca, paralel <xref:System.Diagnostics.Stopwatch?displayProperty=nameWithType> olmayan bir döngüyle paralel bir döngünün performansını karşılaştırmak için sınıfını nasıl kullanacağınızı gösterir. Büyük bir çıkış hacmi üretebildiğinden, örneğin çıktının bir dosyaya yeniden yönlendirilmesine izin verdiğini unutmayın.

[!code-csharp[TPL_Parallel#01](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_parallel/cs/simpleparallelfor.cs#01)]
[!code-vb[TPL_Parallel#01](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_parallel/vb/simpleparallelfor.vb#01)]

Döngüler dahil olmak üzere herhangi bir kodu paralelleştirdiğinde, önemli bir amaç, paralel işleme yükünün herhangi bir performans avantajlarından yararlanmasına neden olacak şekilde, işlemciyi paralelleştirmeden mümkün olduğunca çok daha fazla kullanır. Bu örnekte, iç döngüde çok fazla iş gerçekleştirilmediğinden yalnızca dış döngü paralelleştirildi. Az miktarda iş ve istenmeyen önbellek efektlerinin birleşimi, iç içe paralel Döngülerde performans düşüşüne neden olabilir. Bu nedenle, dış döngüyü paralelleştirme, çoğu sistemde eşzamanlılık avantajlarından en iyi şekilde yararlanmanın en iyi yoludur.

## <a name="the-delegate"></a>Temsilci

Bu aşırı yüklemesinin üçüncü parametresi, <xref:System.Threading.Tasks.Parallel.For%2A> `Action<int>` C# dilinde veya Visual Basic bir temsilcisidir `Action(Of Integer)` . `Action`Sıfır, bir veya on altı tür parametresi olup olmadığı bir temsilci, her zaman void döndürür. Visual Basic, öğesinin davranışı `Action` ile tanımlanır `Sub` . Örnek, temsilciyi oluşturmak için bir lambda ifadesi kullanır, ancak temsilciyi başka yollarla da oluşturabilirsiniz. Daha fazla bilgi için bkz. [PLıNQ ve TPL 'Deki lambda ifadeleri](lambda-expressions-in-plinq-and-tpl.md).

## <a name="the-iteration-value"></a>Yineleme değeri

Temsilci, değeri geçerli yineleme olan tek bir giriş parametresi alır. Bu yineleme değeri çalışma zamanı tarafından sağlanır ve başlangıç değeri, geçerli iş parçacığında işlenmekte olan kaynağın segmentindeki (bölüm) ilk öğenin dizinidir.

Eşzamanlılık düzeyi üzerinde daha fazla denetime ihtiyacınız varsa, şöyle bir giriş parametresi alan aşırı yüklemelerden birini kullanın <xref:System.Threading.Tasks.ParallelOptions?displayProperty=nameWithType> : <xref:System.Threading.Tasks.Parallel.For%28System.Int32%2CSystem.Int32%2CSystem.Threading.Tasks.ParallelOptions%2CSystem.Action%7BSystem.Int32%2CSystem.Threading.Tasks.ParallelLoopState%7D%29?displayProperty=nameWithType> .

## <a name="return-value-and-exception-handling"></a>Dönüş değeri ve özel durum Işleme

<xref:System.Threading.Tasks.Parallel.For%2A><xref:System.Threading.Tasks.ParallelLoopResult?displayProperty=nameWithType>tüm iş parçacıkları tamamlandığında bir nesne döndürür. Bu dönüş değeri, Döngü yinelemesini el ile durdururken veya parçaladığında faydalıdır, çünkü <xref:System.Threading.Tasks.ParallelLoopResult> tamamlanmayı çalıştıran son yineleme gibi bilgileri depolar. İş parçacıklarından birinde bir veya daha fazla özel durum oluşursa, bir <xref:System.AggregateException?displayProperty=nameWithType> oluşturulur.

Bu örnekteki kodda, öğesinin dönüş değeri <xref:System.Threading.Tasks.Parallel.For%2A> kullanılmaz.

## <a name="analysis-and-performance"></a>Analiz ve performans

Bilgisayarınızdaki CPU kullanımını görüntülemek için performans sihirbazını kullanabilirsiniz. Bir deneme olarak, matrislerde sütun ve satır sayısını artırın. Matrisler arttıkça, hesaplamanın paralel ve sıralı sürümleri arasındaki performans farkı artar. Matris küçük olduğunda, paralel döngü ayarlamadaki ek yük nedeniyle sıralı sürüm daha hızlı çalışır.

Konsol veya dosya sistemi gibi paylaşılan kaynaklara zaman uyumlu çağrılar, paralel bir döngünün performansını önemli ölçüde azaltır. Performansı ölçerek, döngü içindeki gibi çağrılardan kaçının <xref:System.Console.WriteLine%2A?displayProperty=nameWithType> .

## <a name="compile-the-code"></a>Kodu derle

Bu kodu kopyalayıp bir Visual Studio projesine yapıştırın.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Threading.Tasks.Parallel.For%2A>
- <xref:System.Threading.Tasks.Parallel.ForEach%2A>
- [Veri paralelliği](data-parallelism-task-parallel-library.md)
- [Paralel programlama](index.md)
