---
title: 'Nasıl yapılır: İş Parçacığı Yerel Değişkenleriyle bir Parallel.For Döngüsü Yazma'
description: Döngünün her ayrı görevde durum depolayan ve alan iş parçacığı yerel değişkenleri kullanan, .NET 'teki bir Parallel. for döngüsünün nasıl yazılacağını gösteren bir örnek görürsünüz.
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- parallel for loops, how to use local state
ms.assetid: 68384064-7ee7-41e2-90e3-71f00bde01bb
ms.openlocfilehash: 9cff507757aab2e5676df2fabb02a237a2172c17
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84599795"
---
# <a name="how-to-write-a-parallelfor-loop-with-thread-local-variables"></a>Nasıl yapılır: İş Parçacığı Yerel Değişkenleriyle bir Parallel.For Döngüsü Yazma
Bu örnek, bir döngü tarafından oluşturulan her ayrı görevde durumu depolamak ve almak için iş parçacığı yerel değişkenlerinin nasıl kullanılacağını gösterir <xref:System.Threading.Tasks.Parallel.For%2A> . İş parçacığı yerel verilerini kullanarak, paylaşılan duruma çok sayıda erişimi eşitleme yükünden kaçınabilirsiniz. Her yinelemede paylaşılan bir kaynağa yazmak yerine, görev için tüm yinelemeler tamamlanana kadar değeri hesaplar ve depolar. Ardından, son sonucu paylaşılan kaynağa yazabilir veya başka bir yönteme geçirebilirsiniz.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, <xref:System.Threading.Tasks.Parallel.For%60%601%28System.Int32%2CSystem.Int32%2CSystem.Func%7B%60%600%7D%2CSystem.Func%7BSystem.Int32%2CSystem.Threading.Tasks.ParallelLoopState%2C%60%600%2C%60%600%7D%2CSystem.Action%7B%60%600%7D%29> 1.000.000 öğelerini içeren bir dizideki değerlerin toplamını hesaplamak için yöntemini çağırır. Her öğenin değeri, dizinine eşittir.  
  
 [!code-csharp[TPL_Parallel#05](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_parallel/cs/forandforeach_simple.cs#05)]
 [!code-vb[TPL_Parallel#05](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_parallel/vb/forwiththreadlocal.vb#05)]  
  
 Her yöntemin ilk iki parametresi, <xref:System.Threading.Tasks.Parallel.For%2A> Başlangıç ve bitiş yineleme değerlerini belirtir. Yönteminin bu aşırı yüküne üçüncü parametresi, yerel eyaletinizi başlattığınız yerdir. Bu bağlamda yerel durum, ömrü son yinelemeden hemen sonra olmak üzere geçerli iş parçacığındaki döngünün ilk yinelemesinden hemen önce olan bir değişken anlamına gelir.  
  
 Üçüncü parametrenin türü, <xref:System.Func%601> `TResult` iş parçacığı yerel durumunu depolayacak değişkenin türüdür. Türü, genel yöntem çağrılırken sağlanan genel tür bağımsız değişkeni tarafından tanımlanır <xref:System.Threading.Tasks.Parallel.For%60%601%28System.Int32%2CSystem.Int32%2CSystem.Func%7B%60%600%7D%2CSystem.Func%7BSystem.Int32%2CSystem.Threading.Tasks.ParallelLoopState%2C%60%600%2C%60%600%7D%2CSystem.Action%7B%60%600%7D%29> , bu durumda <xref:System.Int64> . Tür bağımsız değişkeni derleyiciye iş parçacığı yerel durumunu depolamak için kullanılacak geçici değişkenin türünü söyler. Bu örnekte, ifadesi `() => 0` (veya `Function() 0` Visual Basic), Thread-Local değişkenini sıfır olarak başlatır. Genel tür bağımsız değişkeni bir başvuru türü veya Kullanıcı tanımlı değer türsiyse, ifade şöyle görünür:  
  
```csharp  
() => new MyClass()  
```  
  
```vb  
Function() new MyClass()  
```  
  
 Dördüncü parametre döngü mantığını tanımlar. İmzası `Func<int, ParallelLoopState, long, long>` C# veya Visual Basic içinde olan bir temsilci veya lambda ifadesi olmalıdır `Func(Of Integer, ParallelLoopState, Long, Long)` . İlk parametre, döngünün o yinelemesi için döngü sayacının değeridir. İkincisi, <xref:System.Threading.Tasks.ParallelLoopState> döngüyü bölmek için kullanılabilecek bir nesnedir; bu nesne, <xref:System.Threading.Tasks.Parallel> döngünün her geçtiği her bir sınıf tarafından sağlanır. Üçüncü parametre iş parçacığı yerel değişkenidir. Son parametre, dönüş türüdür. Bu durumda, türü <xref:System.Int64> tür bağımsız değişkeninde belirttiğimiz tür olur <xref:System.Threading.Tasks.Parallel.For%2A> . Bu değişken olarak adlandırılır `subtotal` ve lambda ifadesi tarafından döndürülür. Dönüş değeri, `subtotal` döngünün sonraki tekrarında başlatmak için kullanılır. Ayrıca, bu son parametreyi her yinelemeye geçirilen bir değer olarak düşünebilirsiniz ve ardından `localFinally` son yineleme tamamlandığında temsilciye geçirilir.  
  
 Beşinci parametre, belirli bir iş parçacığında tüm yinelemeler tamamlandıktan sonra bir kez çağrılan yöntemi tanımlar. Giriş bağımsız değişkeninin türü, metodun tür bağımsız değişkenine <xref:System.Threading.Tasks.Parallel.For%60%601%28System.Int32%2CSystem.Int32%2CSystem.Func%7B%60%600%7D%2CSystem.Func%7BSystem.Int32%2CSystem.Threading.Tasks.ParallelLoopState%2C%60%600%2C%60%600%7D%2CSystem.Action%7B%60%600%7D%29> ve gövde lambda ifadesi tarafından döndürülen türe karşılık gelir. Bu örnekte, değeri yöntemini çağırarak iş parçacığı güvenli bir şekilde sınıf kapsamındaki bir değişkene eklenir <xref:System.Threading.Interlocked.Add%2A?displayProperty=nameWithType> . İş parçacığı yerel değişkeni kullanarak döngünün her yinelemesinde Bu sınıf değişkenine yazmayı önliyoruz.  
  
 Lambda ifadelerinin nasıl kullanılacağı hakkında daha fazla bilgi için bkz. [PLıNQ ve TPL Içindeki lambda ifadeleri](lambda-expressions-in-plinq-and-tpl.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Veri paralelliği](data-parallelism-task-parallel-library.md)
- [Paralel programlama](index.md)
- [Görev Paralel Kitaplığı (TPL)](task-parallel-library-tpl.md)
- [PLıNQ ve TPL 'deki lambda Ifadeleri](lambda-expressions-in-plinq-and-tpl.md)
