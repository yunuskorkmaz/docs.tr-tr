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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "73139713"
---
# <a name="how-to-write-a-parallelfor-loop-with-thread-local-variables"></a>Nasıl yapılır: İş Parçacığı Yerel Değişkenleriyle bir Parallel.For Döngüsü Yazma
Bu örnek, bir <xref:System.Threading.Tasks.Parallel.For%2A> döngü tarafından oluşturulan her ayrı görevde durumu depolamak ve almak için iş parçacığı yerel değişkenlerinin nasıl kullanılacağını gösterir. İş parçacığı yerel verileri kullanarak, paylaşılan duruma çok sayıda erişim eşitleme yükü önleyebilirsiniz. Her yinelemede paylaşılan bir kaynağa yazmak yerine, görev için tüm yinelemeler tamamlanana kadar değeri hesaplar ve depolarsınız. Daha sonra nihai sonucu paylaşılan kaynağa bir kez yazabilir veya başka bir yönteme aktarabilirsiniz.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, <xref:System.Threading.Tasks.Parallel.For%60%601%28System.Int32%2CSystem.Int32%2CSystem.Func%7B%60%600%7D%2CSystem.Func%7BSystem.Int32%2CSystem.Threading.Tasks.ParallelLoopState%2C%60%600%2C%60%600%7D%2CSystem.Action%7B%60%600%7D%29> bir milyon öğe içeren bir dizideki değerlerin toplamını hesaplama yöntemini çağırır. Her öğenin değeri kendi dizin eşittir.  
  
 [!code-csharp[TPL_Parallel#05](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_parallel/cs/forandforeach_simple.cs#05)]
 [!code-vb[TPL_Parallel#05](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_parallel/vb/forwiththreadlocal.vb#05)]  
  
 Her <xref:System.Threading.Tasks.Parallel.For%2A> yöntemin ilk iki parametresi, yinelemenin başlangıcı nı ve bitiş değerlerini belirtir. Yöntemin bu aşırı yüklenmesinde, üçüncü parametre yerel durumunuzu başlatmanızdır. Bu bağlamda, yerel durum, geçerli iş parçacığı üzerindeki döngünün ilk yinelemesinden hemen önce, son yinelemeden hemen sonrasına kadar uzanan bir değişken anlamına gelir.  
  
 Üçüncü parametrenin türü, <xref:System.Func%601> iş `TResult` parçacığı yerel durumunu depolayacak değişkenin türü olan bir yerdir. Türü, <xref:System.Threading.Tasks.Parallel.For%60%601%28System.Int32%2CSystem.Int32%2CSystem.Func%7B%60%600%7D%2CSystem.Func%7BSystem.Int32%2CSystem.Threading.Tasks.ParallelLoopState%2C%60%600%2C%60%600%7D%2CSystem.Action%7B%60%600%7D%29> bu durumda <xref:System.Int64>. Tür bağımsız değişkeni derleyiciye iş parçacığı yerel durumunu depolamak için kullanılacak geçici değişkenin türünü söyler. Bu örnekte, `() => 0` ifade `Function() 0` (veya Visual Basic' te) iş parçacığı yerel değişkenini sıfıra indirir. Genel tür bağımsız değişkeni bir başvuru türü veya kullanıcı tanımlı değer türüyse, ifade aşağıdaki gibi görünür:  
  
```csharp  
() => new MyClass()  
```  
  
```vb  
Function() new MyClass()  
```  
  
 Dördüncü parametre döngü mantığını tanımlar. İmzası C# veya Visual `Func<int, ParallelLoopState, long, long>` Basic'te olan `Func(Of Integer, ParallelLoopState, Long, Long)` bir temsilci veya lambda ifadesi olmalıdır. İlk parametre, döngünün yinelemesi için döngü sayacının değeridir. İkincisi, döngüden çıkmak için kullanılabilecek bir <xref:System.Threading.Tasks.ParallelLoopState> nesnedir; bu nesne, döngünün <xref:System.Threading.Tasks.Parallel> her oluşumuiçin sınıf tarafından sağlanır. Üçüncü parametre iş parçacığı yerel değişkendir. Son parametre dönüş türüdür. Bu durumda, tür <xref:System.Int64> türü, <xref:System.Threading.Tasks.Parallel.For%2A> tür bağımsız değişkeninde belirttiğimiz tür olmasıdır. Bu değişken `subtotal` adlandırılmış ve lambda ifadesi ile döndürülür. İade değeri, döngüyü `subtotal` sonraki her yinelemede başlatma için kullanılır. Ayrıca, bu son parametreyi her yinelemeye geçirilen ve son yineleme tamamlandığında `localFinally` temsilciye geçirilen bir değer olarak da düşünebilirsiniz.  
  
 Beşinci parametre, belirli bir iş parçacığı üzerindeki tüm yinelemeler tamamlandıktan sonra, bir kez çağrılan yöntemi tanımlar. Giriş bağımsız değişkeninin türü yine <xref:System.Threading.Tasks.Parallel.For%60%601%28System.Int32%2CSystem.Int32%2CSystem.Func%7B%60%600%7D%2CSystem.Func%7BSystem.Int32%2CSystem.Threading.Tasks.ParallelLoopState%2C%60%600%2C%60%600%7D%2CSystem.Action%7B%60%600%7D%29> yöntemin türüne ve gövde lambda ifadesitarafından döndürülen türe karşılık gelir. Bu örnekte, <xref:System.Threading.Interlocked.Add%2A?displayProperty=nameWithType> değer, yöntem çağırılarak sınıf kapsamındaki bir değişkene iş parçacığı güvenli bir şekilde eklenir. Bir iş parçacığı yerel değişkeni kullanarak, döngüher yineleme bu sınıf değişkenine yazma kaçındık.  
  
 Lambda ifadelerinin nasıl kullanılacağı hakkında daha fazla bilgi için [PLINQ ve TPL'deki Lambda İfadeleri'ne](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md)bakın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Veri Paralelliği](../../../docs/standard/parallel-programming/data-parallelism-task-parallel-library.md)
- [Paralel Programlama](../../../docs/standard/parallel-programming/index.md)
- [Görev Paralel Kitaplığı (TPL)](../../../docs/standard/parallel-programming/task-parallel-library-tpl.md)
- [PLINQ ve TPL'deki Lambda İfadeleri](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md)
