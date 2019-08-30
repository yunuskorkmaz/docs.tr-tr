---
title: Zaman uyumsuz dönüş türleriC#()
ms.date: 05/29/2017
ms.assetid: ddb2539c-c898-48c1-ad92-245e4a996df8
ms.openlocfilehash: 2c0dae6b4357ce89325ecb9b7d70ffd79f4e9417
ms.sourcegitcommit: 1b020356e421a9314dd525539da12463d980ce7a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/30/2019
ms.locfileid: "70168394"
---
# <a name="async-return-types-c"></a>Zaman uyumsuz dönüş türleriC#()
Zaman uyumsuz metotlar aşağıdaki dönüş türlerine sahip olabilir:

- <xref:System.Threading.Tasks.Task%601>, bir değer döndüren zaman uyumsuz bir yöntem için. 
 
- <xref:System.Threading.Tasks.Task>, bir işlem gerçekleştiren ancak değer döndüren zaman uyumsuz bir yöntem için.

- `void`, bir olay işleyicisi için. 

- 7,0 ile C# başlayarak, erişilebilir `GetAwaiter` bir yöntemi olan herhangi bir tür. `GetAwaiter` Yöntemi tarafından döndürülen nesne <xref:System.Runtime.CompilerServices.ICriticalNotifyCompletion?displayProperty=nameWithType> arabirimini uygulamalıdır.
  
Zaman uyumsuz yöntemler hakkında daha fazla bilgi için bkz. [Async ve await (C#) Ile zaman uyumsuz programlama](./index.md).  
  
Her dönüş türü aşağıdaki bölümlerden birinde incelenir ve konunun sonunda her üç türü kullanan tam bir örnek bulabilirsiniz.  
  
## <a name="BKMK_TaskTReturnType"></a>Görev\<tSonuç\> dönüş türü  
Dönüş türü, `TResult`işlenenin türü olan bir [Return](../../../language-reference/keywords/return.md) (C#) ifadesini içeren zaman uyumsuz bir yöntem için kullanılır. <xref:System.Threading.Tasks.Task%601>  
  
Aşağıdaki örnekte, `GetLeisureHours` async yöntemi bir tamsayı döndüren bir `return` ifade içerir. Bu nedenle, metot bildiriminin bir dönüş türü `Task<int>`belirtmesi gerekir.  <xref:System.Threading.Tasks.Task.FromResult%2A> Async yöntemi, bir dize döndüren bir işlem için yer tutucudur.
  
[!code-csharp[return-value](../../../../../samples/snippets/csharp/programming-guide/async/async-returns1.cs)]

Yöntemi içindeki bir `leisureHours`await ifadesi `GetLeisureHours` içinden çağrıldığında, await ifadesi yöntemi tarafından döndürülen görevde depolanan tamsayı değerini (değeri) alır. `GetLeisureHours` `ShowTodaysInfo` Await ifadeleri hakkında daha fazla bilgi için bkz. [await](../../../language-reference/operators/await.md).  
  
Aşağıdaki kodda gösterildiği gibi `GetLeisureHours` `await`, çağrısını uygulamasından ayırarak bunun nasıl gerçekleştiğini daha iyi anlayabilirsiniz. Yönteminin bildiriminden bekleyebileceğiniz `GetLeisureHours` için hemen beklenen bir yönteme çağrı bir `Task<int>`döndürür. Görev örnekteki `integerTask` değişkenine atanır. Bir olduğundan, <xref:System.Threading.Tasks.Task%601.Result> türünde bir`TResult`özelliğiiçerir. <xref:System.Threading.Tasks.Task%601> `integerTask` Bu durumda, `TResult` bir tamsayı türünü temsil eder. Öğesine uygulandığında, <xref:System.Threading.Tasks.Task%601.Result%2A> await ifadesi öğesinin `integerTask`özelliğinin içeriğini değerlendirir. `integerTask` `await` Değer `ret` değişkenine atanır.  
  
> [!IMPORTANT]
> <xref:System.Threading.Tasks.Task%601.Result%2A> Özelliği engelleyici bir özelliktir. Görevi tamamlanmadan önce ona erişmeye çalışırsanız, etkin olan iş parçacığı, görev tamamlanana ve değer kullanılabilir olana kadar engellenir. Çoğu durumda, özelliğine doğrudan erişmek yerine kullanarak `await` değere erişmeniz gerekir. <br/> Önceki örnek, uygulamanın sonlandırılmadan önce yürütmeyi tamamlayabilmesi <xref:System.Threading.Tasks.Task%601.Result%2A> `ShowTodaysInfo` için ana iş parçacığını engellemek üzere özelliğinin değerini almıştır.  

[!code-csharp[return-value](../../../../../samples/snippets/csharp/programming-guide/async/async-returns1a.cs#1)]
  
## <a name="BKMK_TaskReturnType"></a>Görev dönüş türü  
Bir `return` ifade içermeyen veya bir işleneni döndürmeyen bir `return` ifade içeren zaman uyumsuz yöntemler genellikle dönüş türüne <xref:System.Threading.Tasks.Task>sahiptir. Bu tür yöntemler `void` zaman uyumlu olarak çalıştırıldıklarında döndürülür. Zaman uyumsuz bir yöntem <xref:System.Threading.Tasks.Task> için dönüş türü kullanırsanız, çağıran zaman uyumsuz yöntem bitene kadar çağıranın tamamlanmasını `await` askıya almak için bir operatör kullanabilirsiniz.  
  
Aşağıdaki örnekte, `WaitAndApologize` async yöntemi bir `return` ifade içermez, bu nedenle Yöntem bir <xref:System.Threading.Tasks.Task> nesne döndürür. Bu, `WaitAndApologize` beklemenize olanak sağlar. Dönüş değeri olmadığından <xref:System.Threading.Tasks.Task> türün bir `Result` özellik içermediğini unutmayın.  

[!code-csharp[return-value](../../../../../samples/snippets/csharp/programming-guide/async/async-returns2.cs)]  
  
`WaitAndApologize`, zaman uyumlu void döndüren bir yöntem için çağırma deyimine benzer bir await ifadesi yerine await deyimi kullanılarak bekletildi. Bu durumda await işlecinin uygulaması bir değer üretmez.  
  
Önceki <xref:System.Threading.Tasks.Task%601> örnekte olduğu gibi, aşağıdaki kodda gösterildiği gibi, `WaitAndApologize` çağrısını await işlecinin uygulamasından ayırabilirsiniz. Ancak, bir `Task` `Result` özelliğine sahip olmadığını ve bir `Task`Await işleci uygulandığında hiçbir değer üretilmediğini unutmayın.  
  
Aşağıdaki kod, yöntemi çağıran `WaitAndApologize` görevin döndürdüğü görevi bekleten ayırır.  
 
[!code-csharp[return-value](../../../../../samples/snippets/csharp/programming-guide/async/async-returns2a.cs#1)]  
 
## <a name="BKMK_VoidReturnType"></a>Void dönüş türü

Dönüş türünü, `void` `void` dönüş türü gerektiren zaman uyumsuz olay işleyicilerde kullanırsınız. Değer döndürmeyen olay işleyicileri dışındaki yöntemler için, döndüren <xref:System.Threading.Tasks.Task> `void` zaman uyumsuz bir yöntem beklenmediği için bir yerine döndürmelidir. Bu tür bir yöntemi çağıran, çağrılan zaman uyumsuz yöntemin tamamlanmasını beklemeden tamamlamaya devam edebilmelidir ve çağıranın, zaman uyumsuz yöntemin ürettiği herhangi bir değerden veya özel durumlardan bağımsız olması gerekir.  
  
Void döndüren zaman uyumsuz bir yöntemi çağıran, yöntemden oluşturulan özel durumları yakalayabilir ve bu tür işlenmemiş özel durumlar uygulamanızın başarısız olmasına neden olabilir. Bir <xref:System.Threading.Tasks.Task> veya<xref:System.Threading.Tasks.Task%601>döndüren zaman uyumsuz bir yöntemde özel durum oluşursa, özel durum döndürülen görevde depolanır ve görev beklendiğinde yeniden oluşturulur. Bu nedenle, bir özel durum üretemeyen herhangi bir zaman uyumsuz metodun, <xref:System.Threading.Tasks.Task> veya <xref:System.Threading.Tasks.Task%601> dönüş türüne sahip olduğundan ve metoda yapılan çağrıların beklenmediğinden emin olun.  
  
Zaman uyumsuz yöntemlerde özel durumları yakalama hakkında daha fazla bilgi için, [try-catch](../../../language-reference/keywords/try-catch.md) konusunun [zaman uyumsuz metotlar bölümünde özel durumlar](../../../language-reference/keywords/try-catch.md#exceptions-in-async-methods) bölümüne bakın.  
  
Aşağıdaki örnek, zaman uyumsuz bir olay işleyicisinin davranışını gösterir. Örnek kodda, zaman uyumsuz bir olay işleyicisinin ana iş parçacığının tamamlandığında bunu bilmesini sağlamalıdır. Ardından, ana iş parçacığı programdan çıkmadan zaman uyumsuz bir olay işleyicisinin tamamlanmasını bekleyebilir.
 
[!code-csharp[return-value](../../../../../samples/snippets/csharp/programming-guide/async/async-returns3.cs)]  
 
## <a name="generalized-async-return-types-and-valuetasktresult"></a>Genelleştirilmiş zaman uyumsuz dönüş türleri ve valuetask\<TResult\>

7,0 ile C# başlayarak, zaman uyumsuz bir yöntem erişilebilir `GetAwaiter` bir yöntemi olan herhangi bir tür döndürebilir.
 
<xref:System.Threading.Tasks.Task> Ve<xref:System.Threading.Tasks.Task%601> başvuru türleri olduğundan, performans açısından kritik yollarda bellek ayırma, özellikle de ayırmalar sıkı Döngülerde gerçekleşiyorsa performansı olumsuz etkileyebilir. Genelleştirilmiş dönüş türleri için destek, ek bellek ayırmalarını önlemek için bir başvuru türü yerine hafif değer türü döndürebilmeniz anlamına gelir. 

.Net, <xref:System.Threading.Tasks.ValueTask%601?displayProperty=nameWithType> genelleştirilmiş bir görev döndüren değerin hafif bir uygulama olarak yapısını sağlar. <xref:System.Threading.Tasks.ValueTask%601?displayProperty=nameWithType> Türünü kullanmak için, `System.Threading.Tasks.Extensions` NuGet paketini projenize eklemeniz gerekir. Aşağıdaki örnek, iki zarın değerini almak için <xref:System.Threading.Tasks.ValueTask%601> yapısını kullanır. 
  
[!code-csharp[return-value](../../../../../samples/snippets/csharp/programming-guide/async/async-valuetask.cs)]

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Threading.Tasks.Task.FromResult%2A>
- [İzlenecek yol: Async ve await (C#) kullanarak Web 'e erişme](./walkthrough-accessing-the-web-by-using-async-and-await.md)
- [Zaman uyumsuz programlarda denetim akışı (C#)](./control-flow-in-async-programs.md)
- [async](../../../language-reference/keywords/async.md)
- [await](../../../language-reference/operators/await.md)
