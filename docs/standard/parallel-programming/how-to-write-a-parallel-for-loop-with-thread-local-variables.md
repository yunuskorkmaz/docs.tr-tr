---
title: 'Nasıl yapılır: İş Parçacığı Yerel Değişkenleriyle bir Parallel.For Döngüsü Yazma'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- parallel for loops, how to use local state
ms.assetid: 68384064-7ee7-41e2-90e3-71f00bde01bb
ms.openlocfilehash: 14f4f1402f564d38bb508e893521a3951c1509f4
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73139713"
---
# <a name="how-to-write-a-parallelfor-loop-with-thread-local-variables"></a>Nasıl yapılır: İş Parçacığı Yerel Değişkenleriyle bir Parallel.For Döngüsü Yazma
Bu örnek, <xref:System.Threading.Tasks.Parallel.For%2A> döngüsü tarafından oluşturulan her ayrı görevde durumu depolamak ve almak için iş parçacığı yerel değişkenlerinin nasıl kullanılacağını gösterir. İş parçacığı yerel verilerini kullanarak, paylaşılan duruma çok sayıda erişimi eşitleme yükünden kaçınabilirsiniz. Her yinelemede paylaşılan bir kaynağa yazmak yerine, görev için tüm yinelemeler tamamlanana kadar değeri hesaplar ve depolar. Ardından, son sonucu paylaşılan kaynağa yazabilir veya başka bir yönteme geçirebilirsiniz.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, 1.000.000 öğelerini içeren bir dizideki değerlerin toplamını hesaplamak için <xref:System.Threading.Tasks.Parallel.For%60%601%28System.Int32%2CSystem.Int32%2CSystem.Func%7B%60%600%7D%2CSystem.Func%7BSystem.Int32%2CSystem.Threading.Tasks.ParallelLoopState%2C%60%600%2C%60%600%7D%2CSystem.Action%7B%60%600%7D%29> yöntemini çağırır. Her öğenin değeri, dizinine eşittir.  
  
 [!code-csharp[TPL_Parallel#05](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_parallel/cs/forandforeach_simple.cs#05)]
 [!code-vb[TPL_Parallel#05](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_parallel/vb/forwiththreadlocal.vb#05)]  
  
 Her <xref:System.Threading.Tasks.Parallel.For%2A> yönteminin ilk iki parametresi, başlangıç ve bitiş yineleme değerlerini belirtir. Yönteminin bu aşırı yüküne üçüncü parametresi, yerel eyaletinizi başlattığınız yerdir. Bu bağlamda yerel durum, ömrü son yinelemeden hemen sonra olmak üzere geçerli iş parçacığındaki döngünün ilk yinelemesinden hemen önce olan bir değişken anlamına gelir.  
  
 Üçüncü parametrenin türü, `TResult` iş parçacığı yerel durumunu depolayacak değişkenin türü olan bir <xref:System.Func%601>. Türü, genel <xref:System.Threading.Tasks.Parallel.For%60%601%28System.Int32%2CSystem.Int32%2CSystem.Func%7B%60%600%7D%2CSystem.Func%7BSystem.Int32%2CSystem.Threading.Tasks.ParallelLoopState%2C%60%600%2C%60%600%7D%2CSystem.Action%7B%60%600%7D%29> yöntemi çağrılırken sağlanan genel tür bağımsız değişkeni tarafından tanımlanır, bu durumda <xref:System.Int64>. Tür bağımsız değişkeni derleyiciye iş parçacığı yerel durumunu depolamak için kullanılacak geçici değişkenin türünü söyler. Bu örnekte, `() => 0` (`Function() 0` veya Visual Basic) ifadesi, Thread-Local değişkenini sıfır olarak başlatır. Genel tür bağımsız değişkeni bir başvuru türü veya Kullanıcı tanımlı değer türsiyse, ifade şöyle görünür:  
  
```csharp  
() => new MyClass()  
```  
  
```vb  
Function() new MyClass()  
```  
  
 Dördüncü parametre döngü mantığını tanımlar. İmzası Visual Basic içinde C# veya `Func(Of Integer, ParallelLoopState, Long, Long)` `Func<int, ParallelLoopState, long, long>` bir temsilci veya lambda ifadesi olmalıdır. İlk parametre, döngünün o yinelemesi için döngü sayacının değeridir. İkincisi, döngüden ayırmak için kullanılabilecek bir <xref:System.Threading.Tasks.ParallelLoopState> nesnesidir; Bu nesne, döngünün her geçtiği <xref:System.Threading.Tasks.Parallel> sınıfı tarafından sağlanır. Üçüncü parametre iş parçacığı yerel değişkenidir. Son parametre, dönüş türüdür. Bu durumda, <xref:System.Int64> türü <xref:System.Threading.Tasks.Parallel.For%2A> türü bağımsız değişkeninde belirttiğimiz tür olduğundan tür. Bu değişken `subtotal` olarak adlandırılır ve lambda ifadesi tarafından döndürülür. Dönüş değeri, döngünün sonraki tekrarında `subtotal` başlatmak için kullanılır. Ayrıca, bu son parametreyi her yinelemeye geçirilen bir değer olarak düşünebilirsiniz ve sonra son yineleme tamamlandığında `localFinally` temsilcisine geçirilir.  
  
 Beşinci parametre, belirli bir iş parçacığında tüm yinelemeler tamamlandıktan sonra bir kez çağrılan yöntemi tanımlar. Giriş bağımsız değişkeninin türü, <xref:System.Threading.Tasks.Parallel.For%60%601%28System.Int32%2CSystem.Int32%2CSystem.Func%7B%60%600%7D%2CSystem.Func%7BSystem.Int32%2CSystem.Threading.Tasks.ParallelLoopState%2C%60%600%2C%60%600%7D%2CSystem.Action%7B%60%600%7D%29> yönteminin tür bağımsız değişkenine ve gövde lambda ifadesi tarafından döndürülen türe karşılık gelir. Bu örnekte, değer, <xref:System.Threading.Interlocked.Add%2A?displayProperty=nameWithType> yöntemini çağırarak iş parçacığı güvenli bir şekilde sınıf kapsamındaki bir değişkene eklenir. İş parçacığı yerel değişkeni kullanarak döngünün her yinelemesinde Bu sınıf değişkenine yazmayı önliyoruz.  
  
 Lambda ifadelerinin nasıl kullanılacağı hakkında daha fazla bilgi için bkz. [PLıNQ ve TPL Içindeki lambda ifadeleri](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Veri Paralelliği](../../../docs/standard/parallel-programming/data-parallelism-task-parallel-library.md)
- [Paralel Programlama](../../../docs/standard/parallel-programming/index.md)
- [Görev Paralel Kitaplığı (TPL)](../../../docs/standard/parallel-programming/task-parallel-library-tpl.md)
- [PLINQ ve TPL'deki Lambda İfadeleri](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md)
