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
ms.openlocfilehash: a70b8e3d1f56eafc04b97a19a1582d9c664e587d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33584676"
---
# <a name="how-to-write-a-parallelfor-loop-with-thread-local-variables"></a>Nasıl yapılır: İş Parçacığı Yerel Değişkenleriyle bir Parallel.For Döngüsü Yazma
Bu örnek tarafından oluşturulan her ayrı görev durumda depolanıp iş parçacığı yerel değişkenleri kullanmayı gösterir bir <xref:System.Threading.Tasks.Parallel.For%2A> döngü. İş parçacığı yerel verileri kullanarak, çok sayıda paylaşılan durum erişimin eşitleme yükünü önleyebilirsiniz. Paylaşılan kaynağa her yinelemesinde yazmak, yerine işlem ve görev için tüm yinelemeleri tamamlanana kadar değeri saklayın. Sonra nihai sonucu kez paylaşılan kaynağa yazma veya başka bir yönteme geçirin.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek çağrıları <xref:System.Threading.Tasks.Parallel.For%60%601%28System.Int32%2CSystem.Int32%2CSystem.Func%7B%60%600%7D%2CSystem.Func%7BSystem.Int32%2CSystem.Threading.Tasks.ParallelLoopState%2C%60%600%2C%60%600%7D%2CSystem.Action%7B%60%600%7D%29> bir milyon öğeleri içeren bir dizi değerlerin toplamını hesaplamak için yöntem. Her öğenin değerini kendi dizinine eşittir.  
  
 [!code-csharp[TPL_Parallel#05](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_parallel/cs/forandforeach_simple.cs#05)]
 [!code-vb[TPL_Parallel#05](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_parallel/vb/forwiththreadlocal.vb#05)]  
  
 İlk iki parametrelerinin her <xref:System.Threading.Tasks.Parallel.For%2A> yöntemi, başlangıç ve bitiş yineleme değerlerini belirtin. Bu yöntem aşırı içinde yerel durumunuza başlatma burada üçüncü parametresidir. Bu bağlamda yerel durumu son yinelemeden sonra yalnızca için geçerli iş parçacığı üzerinde ilk döngü hemen önce gelen, yaşam süresi genişleten bir değişken anlamına gelir.  
  
 Üçüncü parametre türü bir <xref:System.Func%601> burada `TResult` yerel iş parçacığı durumu depolayacak değişkeni türüdür. Türünü genel çağrılırken genel tür bağımsız değişkeni tarafından tanımlanan <xref:System.Threading.Tasks.Parallel.For%60%601%28System.Int32%2CSystem.Int32%2CSystem.Func%7B%60%600%7D%2CSystem.Func%7BSystem.Int32%2CSystem.Threading.Tasks.ParallelLoopState%2C%60%600%2C%60%600%7D%2CSystem.Action%7B%60%600%7D%29> bu durumda yöntemi <xref:System.Int64>. Tür bağımsız değişkeni derleyici iş parçacığı yerel durumunu depolamak için kullanılan geçici değişken türünü bildirir. Bu örnekte, ifade `() => 0` (veya `Function() 0` Visual Basic'te) iş parçacığı yerel değişkeni sıfırdan başlatır. Genel tür bağımsız değişkeni bir başvuru veya kullanıcı tanımlı bir değer türü ise, ifade şöyle olabilir:  
  
```csharp  
() => new MyClass()  
```  
  
```vb  
Function() new MyClass()  
```  
  
 Dördüncü parametrenin döngü mantığı tanımlar. İmza bir temsilci ya da lambda ifadesi olmalıdır `Func<int, ParallelLoopState, long, long>` C# veya `Func(Of Integer, ParallelLoopState, Long, Long)` Visual Basic'te. İlk parametre Bu döngü döngü sayaç değeri. İkinci bir <xref:System.Threading.Tasks.ParallelLoopState> ; bu nesne tarafından sağlanan dışında döngüsünü kesmek için kullanılabilir nesne <xref:System.Threading.Tasks.Parallel> döngünün her oluşumu sınıfı. Üçüncü parametre iş parçacığı yerel değişkenidir. Dönüş türü son parametresidir. Bu durumda, türüdür <xref:System.Int64> türü olduğu için biz belirtilen <xref:System.Threading.Tasks.Parallel.For%2A> bağımsız değişkeni yazın. Bu değişken adlı `subtotal` ve lambda ifadesi tarafından döndürülen. Dönüş değeri başlatmak için kullanılan `subtotal` sonraki her döngü tekrarında üzerinde. Bu son parametresi, her bir yineleme için geçirilen ve için geçirilen değer olarak düşünebilirsiniz `localFinally` son yineleme tamamlandığında temsilci.  
  
 Beşinci parametrenin belirli bir iş parçacığı üzerinde tüm yinelemeleri tamamladıktan sonra bir kez çağrılır yöntemi tanımlar. Giriş bağımsız değişkeni tür tür bağımsız değişkeni yeniden karşılık gelen <xref:System.Threading.Tasks.Parallel.For%60%601%28System.Int32%2CSystem.Int32%2CSystem.Func%7B%60%600%7D%2CSystem.Func%7BSystem.Int32%2CSystem.Threading.Tasks.ParallelLoopState%2C%60%600%2C%60%600%7D%2CSystem.Action%7B%60%600%7D%29> yöntemi ve gövde lambda ifadesi tarafından döndürülen tür. Bu örnekte, değeri bir değişkene sınıfı kapsamdaki iş parçacığı güvenli bir yolla çağrılarak eklenir <xref:System.Threading.Interlocked.Add%2A?displayProperty=nameWithType> yöntemi. Bir iş parçacığı yerel değişkeni kullanarak, biz Bu sınıf değişkeni her döngü tekrarında üzerine yazılmasını kaçınılması.  
  
 Lambda ifadeleri kullanma hakkında daha fazla bilgi için bkz: [PLINQ ve TPL'deki Lambda ifadeleri](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Veri Paralelliği](../../../docs/standard/parallel-programming/data-parallelism-task-parallel-library.md)  
 [Paralel Programlama](../../../docs/standard/parallel-programming/index.md)  
 [Görev Paralel Kitaplığı (TPL)](../../../docs/standard/parallel-programming/task-parallel-library-tpl.md)  
 [PLINQ ve TPL'deki Lambda İfadeleri](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md)
