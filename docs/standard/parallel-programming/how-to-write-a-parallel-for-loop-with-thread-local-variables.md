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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 18458e52c6cf38b2900036613676adea3f3b2d0b
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/08/2018
ms.locfileid: "44188130"
---
# <a name="how-to-write-a-parallelfor-loop-with-thread-local-variables"></a>Nasıl yapılır: İş Parçacığı Yerel Değişkenleriyle bir Parallel.For Döngüsü Yazma
Bu örnek tarafından oluşturulan her ayrı görev durumda depolanıp thread-local değişkenleri kullanmayı gösterir. bir <xref:System.Threading.Tasks.Parallel.For%2A> döngü. İş parçacığı-yerel verileri kullanarak, çok sayıda paylaşılan durum erişimin eşitleme ek yükü önleyebilirsiniz. Paylaşılan bir kaynağa her yinelemede yazmak, yerine işlem ve tüm yineleme için görev tamamlanana kadar değeri depolar. Paylaşılan kaynak için nihai sonucu bir defa yazın veya başka yönteme geçirin.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek çağrıları <xref:System.Threading.Tasks.Parallel.For%60%601%28System.Int32%2CSystem.Int32%2CSystem.Func%7B%60%600%7D%2CSystem.Func%7BSystem.Int32%2CSystem.Threading.Tasks.ParallelLoopState%2C%60%600%2C%60%600%7D%2CSystem.Action%7B%60%600%7D%29> bir milyon öğeleri içeren bir dizideki değerlerin toplamını hesaplamak için yöntemi. Her öğenin dizinini için eşittir.  
  
 [!code-csharp[TPL_Parallel#05](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_parallel/cs/forandforeach_simple.cs#05)]
 [!code-vb[TPL_Parallel#05](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_parallel/vb/forwiththreadlocal.vb#05)]  
  
 İlk iki parametrelerinin her <xref:System.Threading.Tasks.Parallel.For%2A> yöntemi, başlangıç ve bitiş yineleme değerlerini belirtin. Bu yöntem aşırı içinde yerel durumunuzu başlatmak burada üçüncü parametredir. Bu bağlamda yerel durumu son yinelemeden sonra yalnızca geçerli iş parçacığı üzerinde ilk döngü hemen önce gelen ömürlerinin genişleten bir değişken anlamına gelir.  
  
 Üçüncü parametre türü bir <xref:System.Func%601> burada `TResult` iş parçacığı-yerel durumunu depolayacak değişkeninin türü. Türü genel çağırırken sağlanan genel tür bağımsız değişkeni tarafından tanımlanan <xref:System.Threading.Tasks.Parallel.For%60%601%28System.Int32%2CSystem.Int32%2CSystem.Func%7B%60%600%7D%2CSystem.Func%7BSystem.Int32%2CSystem.Threading.Tasks.ParallelLoopState%2C%60%600%2C%60%600%7D%2CSystem.Action%7B%60%600%7D%29> bu durumda olan yöntemini <xref:System.Int64>. İş parçacığı-yerel durumunu depolamak için kullanılacak geçici değişken türünü derleyiciye tür bağımsız değişkeni. Bu örnekte, ifade `() => 0` (veya `Function() 0` Visual Basic'te) iş parçacığı yerel değişkeni sıfırdan başlatır. Genel tür bağımsız değişkeni bir başvuru türüyle veya kullanıcı tanımlı değer türü ise, ifade şöyle görünebilir:  
  
```csharp  
() => new MyClass()  
```  
  
```vb  
Function() new MyClass()  
```  
  
 Dördüncü parametre döngü mantığı tanımlar. İmzaya sahip, bir temsilci veya lambda ifadesi olmalıdır `Func<int, ParallelLoopState, long, long>` C# veya `Func(Of Integer, ParallelLoopState, Long, Long)` Visual Basic'te. İlk parametre, söz konusu döngü için döngü sayacı değerdir. İkinci bir <xref:System.Threading.Tasks.ParallelLoopState> nesne döngüden için kullanılabilir; bu nesne tarafından sağlanan <xref:System.Threading.Tasks.Parallel> döngünün her örneği için sınıf. Üçüncü parametre iş parçacığı-yerel bir değişkendir. Dönüş türü son parametredir. Bu durumda, türü, <xref:System.Int64> , türü olduğundan belirttiğimiz <xref:System.Threading.Tasks.Parallel.For%2A> tür bağımsız değişkeni. Bu değişken adlı `subtotal` ve lambda ifadesi tarafından döndürülür. Dönüş değeri başlatmak için kullanılan `subtotal` döngüsünün her yinelemesinde. Bu son parametresi, her yineleme için geçirilen ve ardından geçirilen değeri olarak düşünebilirsiniz `localFinally` son yinelenmesinden tamamlandığında temsilci.  
  
 Beşinci parametrenin belirli bir iş parçacığında tüm yinelemeleri tamamladıktan sonra bir kez çağıran yönteme tanımlar. Giriş bağımsız değişkeninin türü tür bağımsız değişkeni yeniden karşılık gelen <xref:System.Threading.Tasks.Parallel.For%60%601%28System.Int32%2CSystem.Int32%2CSystem.Func%7B%60%600%7D%2CSystem.Func%7BSystem.Int32%2CSystem.Threading.Tasks.ParallelLoopState%2C%60%600%2C%60%600%7D%2CSystem.Action%7B%60%600%7D%29> yöntemi ve gövdesi lambda ifadesi tarafından döndürülen tür. Bu örnekte, değeri bir değişkene sınıf kapsamda iş parçacığı güvenli bir şekilde çağrılarak eklenir <xref:System.Threading.Interlocked.Add%2A?displayProperty=nameWithType> yöntemi. Bir iş parçacığı yerel değişkeni kullanarak, biz Bu döngünün her yinelemesinden sınıfı değişkenine yazma önlenmiş.  
  
 Lambda ifadeleri kullanma hakkında daha fazla bilgi için bkz. [PLINQ ve TPL'deki Lambda ifadeleri](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Veri Paralelliği](../../../docs/standard/parallel-programming/data-parallelism-task-parallel-library.md)  
- [Paralel Programlama](../../../docs/standard/parallel-programming/index.md)  
- [Görev Paralel Kitaplığı (TPL)](../../../docs/standard/parallel-programming/task-parallel-library-tpl.md)  
- [PLINQ ve TPL'deki Lambda İfadeleri](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md)
