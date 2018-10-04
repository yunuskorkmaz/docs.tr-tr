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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1b2ebf679816684e68a1c13d660ef9fc54e3a175
ms.sourcegitcommit: 69229651598b427c550223d3c58aba82e47b3f82
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/04/2018
ms.locfileid: "48777350"
---
# <a name="how-to-write-a-simple-parallelfor-loop"></a>Nasıl yapılır: Basit bir Parallel.For Döngüsü Yazma

Bu konuda gösteren iki örnek içeren <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> yöntemi. İlk kullandığı <xref:System.Threading.Tasks.Parallel.For%28System.Int64%2CSystem.Int64%2CSystem.Action%7BSystem.Int64%7D%29?displayProperty=nameWithType> yöntemi aşırı yüklemesini ve ikinci kullandığı <xref:System.Threading.Tasks.Parallel.For%28System.Int32%2CSystem.Int32%2CSystem.Action%7BSystem.Int32%7D%29?displayProperty=nameWithType> aşırı yüklemesi, iki basit aşırı yüklemeleri <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> yöntemi. Bu iki aşırı yüklemesini kullanabilirsiniz <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> döngü iptal etmek gerekmediğinde yöntemi sonu dışında döngü yinelemesi veya herhangi bir iş parçacığı-yerel durumu korumak.

> [!NOTE]
> TPL'de temsilciler tanımlamak için bu belgede lambda ifadeleri kullanılır. C# veya Visual Basic'te lambda ifadelerine aşina değilseniz bkz [PLINQ ve TPL'deki Lambda ifadeleri](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md).

İlk örnek, tek bir dizindeki dosyaların boyutunu hesaplar. İkinci iki matrislerde çarpımını hesaplar.

## <a name="directory-size-example"></a>Dizin boyutu örneği

Bu örnek, bir dizindeki dosyaların toplam boyutu hesaplar basit bir komut satırı yardımcı programıdır. Bağımsız değişken olarak tek bir dizin yolu bekliyor ve sayısı ve bu dizindeki dosyaların toplam boyutu raporlar. Dizinin mevcut olduğunu doğruladıktan sonra bunu kullanan <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> dizindeki dosyaları numaralandırma ve kendi dosya boyutunu belirlemek için yöntem. Her bir dosya boyutu daha sonra eklenen `totalSize` değişkeni. Ayrıca çağrılarak gerçekleştirilir Not <xref:System.Threading.Interlocked.Add%2A?displayProperty=nameWithType> böylece ek bir atomik işlem olarak gerçekleştirilir. Aksi takdirde, birden çok görevi güncelleştirmek çalışabilir `totalSize` değişken aynı anda.

[!code-csharp[Conceptual.Parallel.For#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.parallel.for/cs/for1.cs#1)]
[!code-vb[Conceptual.Parallel.For#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.parallel.for/vb/for1.vb#1)]

## <a name="matrix-and-stopwatch-example"></a>Matris ve kronometre örneği

Bu örnekte <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> iki matrislerde çarpımını için yöntemi. Ayrıca nasıl kullanılacağını gösterir <xref:System.Diagnostics.Stopwatch?displayProperty=nameWithType> paralel olmayan döngü ile paralel bir döngüden performansını karşılaştırmak için sınıf. Çıkış büyük hacimli oluşturabileceğinden, örnek çıkış bir dosyaya yönlendirilmesi verdiğini unutmayın.

[!code-csharp[TPL_Parallel#01](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_parallel/cs/simpleparallelfor.cs#01)]
[!code-vb[TPL_Parallel#01](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_parallel/vb/simpleparallelfor.vb#01)]

Döngüler, dahil olmak üzere herhangi bir kod paralelleştirmek önemli amaçlarından burada herhangi bir performans avantaj paralel işleme yükü olumsuz duruma getirir noktasına paralelleştirmek üzerinden işlemci olmadan mümkün olduğunca yararlanmak için andır. Bu örnekte, iç döngü içinde gerçekleştirilen çok iş olmadığından yalnızca dış döngü paralelleştirildi. Az miktarda iş ve istenmeyen önbellek etkileri birleşimi iç içe geçmiş paralel Döngülerde performans düşüşüne neden olabilir. Bu nedenle, dış döngü paralelleştirmek yalnızca çoğu sistemde yararlarını en üst düzeye çıkarmak için en iyi yoludur.

## <a name="the-delegate"></a>Temsilci

Bu aşırı yüklemesi, üçüncü parametresinin <xref:System.Threading.Tasks.Parallel.For%2A> bir temsilci türü `Action<int>` C# veya `Action(Of Integer)` Visual Basic'te. Bir `Action` temsilcisi, sıfır, bir veya altı tür parametreleri, sahip olup olmadığını her zaman döndürür void. Visual Basic'te davranışını bir `Action` ile tanımlanmış bir `Sub`. Örnek, bir temsilci oluşturmak için bir lambda ifadesi kullanır. ancak, temsilci başka yöntemlerle de oluşturabilirsiniz. Daha fazla bilgi için [PLINQ ve TPL'deki Lambda ifadeleri](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md).

## <a name="the-iteration-value"></a>Yineleme değeri

Temsilci geçerli yineleme değeri olan tek bir giriş parametresi alır. Bu yineleme değeri çalışma zamanı tarafından sağlanan ve başlangıç değeri geçerli iş parçacığı üzerinde işlenmekte olan kaynağı segmentine (bölüm) ilk öğenin dizinidir.

Eşzamanlılık düzeyi hakkında daha fazla denetime ihtiyacınız varsa, alan aşırı kullanan bir <xref:System.Threading.Tasks.ParallelOptions?displayProperty=nameWithType> gibi giriş parametresi: <xref:System.Threading.Tasks.Parallel.For%28System.Int32%2CSystem.Int32%2CSystem.Threading.Tasks.ParallelOptions%2CSystem.Action%7BSystem.Int32%2CSystem.Threading.Tasks.ParallelLoopState%7D%29?displayProperty=nameWithType>.

## <a name="return-value-and-exception-handling"></a>Dönüş değeri ve özel durum işleme

<xref:System.Threading.Tasks.Parallel.For%2A> döndürür bir <xref:System.Threading.Tasks.ParallelLoopResult?displayProperty=nameWithType> tüm iş parçacıklarının tamamladıktan sonra nesne. Bu dönüş değeri olduğundan yararlı, durdurma veya kesme döngü yinelemesi el ile <xref:System.Threading.Tasks.ParallelLoopResult> tamamlanmak üzere çalıştığı son yineleme gibi bilgileri depolar. Bir iş parçacığı üzerinde bir veya daha fazla özel durum oluşursa bir <xref:System.AggregateException?displayProperty=nameWithType> oluşturulur.

Bu örnekte, dönüş değeri koddaki <xref:System.Threading.Tasks.Parallel.For%2A> kullanılmaz.

## <a name="analysis-and-performance"></a>Analiz ve performans

Performans Sihirbazı, bilgisayarınızda CPU kullanımı görüntülemek için kullanabilirsiniz. Bir deney sütun ve matrislerde satır sayısını artırın. Daha büyük matrisler, hesaplama paralel ve sıralı sürümleri arasında büyük performans farkı. Matris küçük olduğunda, paralel bir döngüden ayarlama yükü nedeniyle sıralı sürümü daha hızlı çalışır.

Zaman uyumlu çağrılar, konsol veya dosya sistemi gibi paylaşılan kaynaklar için önemli ölçüde paralel bir döngüden performansını bozar. Performansı ölçmek, çağrıları gibi kaçınmaya çalışın <xref:System.Console.WriteLine%2A?displayProperty=nameWithType> döngü içinde.

## <a name="compile-the-code"></a>Kod derleme

Kopyalayın ve bu kod bir Visual Studio projesine yapıştırın.

## <a name="see-also"></a>Ayrıca Bkz.

- <xref:System.Threading.Tasks.Parallel.For%2A>
- <xref:System.Threading.Tasks.Parallel.ForEach%2A>
- [Veri Paralelliği](../../../docs/standard/parallel-programming/data-parallelism-task-parallel-library.md)
- [Paralel Programlama](../../../docs/standard/parallel-programming/index.md)
