---
title: Zaman uyumsuz dönüş türleri (C#)
ms.date: 04/14/2020
ms.assetid: ddb2539c-c898-48c1-ad92-245e4a996df8
ms.openlocfilehash: c2584f1e285a7ab76eb43f9a211a8d2a51c2c55e
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/21/2020
ms.locfileid: "83761882"
---
# <a name="async-return-types-c"></a>Zaman uyumsuz dönüş türleri (C#)

Zaman uyumsuz metotlar aşağıdaki dönüş türlerine sahip olabilir:

- <xref:System.Threading.Tasks.Task%601>, bir değer döndüren zaman uyumsuz bir yöntem için.
- <xref:System.Threading.Tasks.Task>, bir işlem gerçekleştiren ancak değer döndüren zaman uyumsuz bir yöntem için.
- `void`, bir olay işleyicisi için.
- C# 7,0 ile başlayarak, erişilebilir bir yöntemi olan herhangi bir tür `GetAwaiter` . Yöntemi tarafından döndürülen nesne `GetAwaiter` <xref:System.Runtime.CompilerServices.ICriticalNotifyCompletion?displayProperty=nameWithType> arabirimini uygulamalıdır.
- C# 8,0 ile başlayarak, <xref:System.Collections.Generic.IAsyncEnumerable%601> *zaman uyumsuz bir akış*döndüren zaman uyumsuz bir yöntem için.

Zaman uyumsuz yöntemler hakkında daha fazla bilgi için bkz. [Async ve await Ile zaman uyumsuz programlama (C#)](./index.md).  
  
## <a name="tasktresult-return-type"></a>Görev \< tSonuç \> dönüş türü  
<xref:System.Threading.Tasks.Task%601>Dönüş türü, işleneni olan [Return](../../../language-reference/keywords/return.md) (C#) ifadesini içeren zaman uyumsuz bir yöntem için kullanılır `TResult` .  
  
Aşağıdaki örnekte, `GetLeisureHours` Async yöntemi `return` bir tamsayı döndüren bir ifade içerir. Bu nedenle, metot bildiriminin bir dönüş türü belirtmesi gerekir `Task<int>` .  <xref:System.Threading.Tasks.Task.FromResult%2A>Async yöntemi, bir dize döndüren bir işlem için yer tutucudur.
  
:::code language="csharp" source="./snippets/async-return-types/async-returns1.cs" id="SnippetFirstExample":::

`GetLeisureHours`Yöntemi içindeki bir await ifadesi içinden çağrıldığında `ShowTodaysInfo` , await ifadesi `leisureHours` yöntemi tarafından döndürülen görevde depolanan tamsayı değerini (değeri) alır `GetLeisureHours` . Await ifadeleri hakkında daha fazla bilgi için bkz. [await](../../../language-reference/operators/await.md).  
  
`await` `Task<T>` `GetLeisureHours` `await` Aşağıdaki kodun gösterdiği gibi, çağrısını uygulamasından ayırarak sonucu bir öğesinden nasıl alacağını daha iyi anlayabilirsiniz. `GetLeisureHours`Yönteminin bildiriminden bekleyebileceğiniz için hemen beklenen bir yönteme çağrı bir döndürür `Task<int>` . Görev `integerTask` örnekteki değişkenine atanır. `integerTask`Bir olduğundan <xref:System.Threading.Tasks.Task%601> , türünde bir özelliği içerir <xref:System.Threading.Tasks.Task%601.Result> `TResult` . Bu durumda, `TResult` bir tamsayı türünü temsil eder. `await`Öğesine uygulandığında `integerTask` , await ifadesi <xref:System.Threading.Tasks.Task%601.Result%2A> öğesinin özelliğinin içeriğini değerlendirir `integerTask` . Değer `ret` değişkenine atanır.  
  
> [!IMPORTANT]
> <xref:System.Threading.Tasks.Task%601.Result%2A>Özelliği engelleyici bir özelliktir. Görevi tamamlanmadan önce ona erişmeye çalışırsanız, etkin olan iş parçacığı, görev tamamlanana ve değer kullanılabilir olana kadar engellenir. Çoğu durumda, `await` özelliğine doğrudan erişmek yerine kullanarak değere erişmeniz gerekir. <br/> Önceki örnek, <xref:System.Threading.Tasks.Task%601.Result%2A> `ShowTodaysInfo` uygulamanın sonlandırılmadan önce yürütmeyi tamamlayabilmesi için ana iş parçacığını engellemek üzere özelliğinin değerini almıştır.  

:::code language="csharp" source="./snippets/async-return-types/async-returns1a.cs" id="SnippetSecondVersion":::

## <a name="task-return-type"></a>Görev dönüş türü  
Bir `return` ifade içermeyen veya bir işleneni döndürmeyen bir ifade içeren zaman uyumsuz yöntemler `return` genellikle dönüş türüne sahiptir <xref:System.Threading.Tasks.Task> . Bu tür yöntemler `void` zaman uyumlu olarak çalıştırıldıklarında döndürülür. <xref:System.Threading.Tasks.Task>Zaman uyumsuz bir yöntem için dönüş türü kullanırsanız, çağıran `await` zaman uyumsuz yöntem bitene kadar çağıranın tamamlanmasını askıya almak için bir operatör kullanabilirsiniz.  
  
Aşağıdaki örnekte, `WaitAndApologize` Async yöntemi bir `return` ifade içermez, bu nedenle Yöntem bir <xref:System.Threading.Tasks.Task> nesne döndürür. Döndürmek, `Task` `WaitAndApologize` beklemenize olanak sağlar. <xref:System.Threading.Tasks.Task>Dönüş değeri olmadığından tür bir `Result` özellik içermiyor.  

:::code language="csharp" source="./snippets/async-return-types/async-returns2.cs" id="SnippetTaskReturn":::

`WaitAndApologize`, zaman uyumlu void döndüren bir yöntem için çağırma deyimine benzer bir await ifadesi yerine await deyimi kullanılarak bekletildi. Bu durumda await işlecinin uygulaması bir değer üretmez.  
  
Önceki örnekte olduğu gibi <xref:System.Threading.Tasks.Task%601> , `WaitAndApologize` aşağıdaki kodda gösterildiği gibi, çağrısını await işlecinin uygulamasından ayırabilirsiniz. Ancak, bir `Task` özelliğine sahip olmadığını `Result` ve bir Await işleci uygulandığında hiçbir değer üretilmediğini unutmayın `Task` .  
  
Aşağıdaki kod, yöntemi çağıran `WaitAndApologize` görevin döndürdüğü görevi bekleten ayırır.  

:::code language="csharp" source="./snippets/async-return-types/async-returns2a.cs" id="SnippetAwaitTask":::

## <a name="void-return-type"></a>Void dönüş türü

Dönüş türünü `void` , dönüş türü gerektiren zaman uyumsuz olay işleyicilerde kullanırsınız `void` . Değer döndürmeyen olay işleyicileri dışındaki yöntemler için, döndüren zaman uyumsuz bir yöntem beklenmediği için bir <xref:System.Threading.Tasks.Task> yerine döndürmelidir `void` . Bu tür bir yöntemin her çağıranı, çağrılan zaman uyumsuz yöntemin bitmesini beklemeden tamamlamaya devam etmelidir. Çağıran, zaman uyumsuz yöntemin ürettiği herhangi bir değerden veya özel durumlardan bağımsız olmalıdır.  
  
Void döndüren zaman uyumsuz bir yöntemi çağıran, yöntemden oluşturulan özel durumları yakalayabilir ve bu tür işlenmemiş özel durumlar uygulamanızın başarısız olmasına neden olabilir. Veya döndüren bir yöntem <xref:System.Threading.Tasks.Task> <xref:System.Threading.Tasks.Task%601> özel durum oluşturursa, özel durum döndürülen görevde depolanır. Görev beklediğinde özel durum yeniden oluşturulur. Bu nedenle, bir özel durum üretemeyen herhangi bir zaman uyumsuz metodun, veya dönüş türüne sahip olduğundan ve metoda yapılan çağrıların beklenmediğinden emin olun <xref:System.Threading.Tasks.Task> <xref:System.Threading.Tasks.Task%601> .  
  
Zaman uyumsuz yöntemlerde özel durumları yakalama hakkında daha fazla bilgi için, [try-catch](../../../language-reference/keywords/try-catch.md) makalesinin [zaman uyumsuz metotlar bölümünde özel durumlar](../../../language-reference/keywords/try-catch.md#exceptions-in-async-methods) bölümüne bakın.  
  
Aşağıdaki örnek, zaman uyumsuz bir olay işleyicisinin davranışını gösterir. Örnek kodda, zaman uyumsuz bir olay işleyicisi ana iş parçacığının bittiğinde bunu bilmesini sağlamalıdır. Ardından, ana iş parçacığı programdan çıkmadan zaman uyumsuz bir olay işleyicisinin tamamlanmasını bekleyebilir.

:::code language="csharp" source="./snippets/async-return-types/async-returns3.cs":::

## <a name="generalized-async-return-types-and-valuetasktresult"></a>Genelleştirilmiş zaman uyumsuz dönüş türleri ve ValueTask \< TResult\>

C# 7,0 ile başlayarak, zaman uyumsuz bir yöntem erişilebilir bir yöntemi olan herhangi bir tür döndürebilir `GetAwaiter` .

<xref:System.Threading.Tasks.Task>Ve <xref:System.Threading.Tasks.Task%601> başvuru türleri olduğundan, performans açısından kritik yollarda bellek ayırma, özellikle de ayırmalar sıkı Döngülerde gerçekleşiyorsa performansı olumsuz etkileyebilir. Genelleştirilmiş dönüş türleri için destek, ek bellek ayırmalarını önlemek için bir başvuru türü yerine hafif değer türü döndürebilmeniz anlamına gelir.

.NET, <xref:System.Threading.Tasks.ValueTask%601?displayProperty=nameWithType> genelleştirilmiş bir görev döndüren değerin hafif bir uygulama olarak yapısını sağlar. Türünü kullanmak için <xref:System.Threading.Tasks.ValueTask%601?displayProperty=nameWithType> , `System.Threading.Tasks.Extensions` NuGet paketini projenize eklemeniz gerekir. Aşağıdaki örnek, <xref:System.Threading.Tasks.ValueTask%601> iki zarın değerini almak için yapısını kullanır.
  
:::code language="csharp" source="./snippets/async-return-types/async-valuetask.cs":::

## <a name="async-streams-with-iasyncenumerablet"></a>Iasyncenumerable ile zaman uyumsuz akışlar \<\>

C# 8,0 ile başlayarak, zaman uyumsuz bir yöntem tarafından temsil edilen *zaman uyumsuz bir akış*döndürebilir <xref:System.Collections.Generic.IAsyncEnumerable%601> . Zaman uyumsuz akış yinelenen zaman uyumsuz çağrılarla parçalar halinde oluşturulduğunda akıştan okunan öğeleri numaralandırmak için bir yol sağlar. Aşağıdaki örnek, zaman uyumsuz akış üreten zaman uyumsuz bir yöntemi gösterir:

:::code language="csharp" source="./snippets/async-return-types/AsyncStreams.cs" id="SnippetGenerateAsyncStream":::

Yukarıdaki örnek, zaman uyumsuz olarak bir dizeden satırları okur. Her satır okunduktan sonra kod dizedeki her bir sözcüğü numaralandırır. Çağıranlar, her bir sözcüğü, `await foreach` ifadesini kullanarak numaralandırır. Yöntemi, kaynak dizeden sonraki satırı zaman uyumsuz olarak okuması gerektiğinde bekler.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Threading.Tasks.Task.FromResult%2A>
- [İzlenecek yol: Async ve await kullanarak Web 'e erişme (C#)](./walkthrough-accessing-the-web-by-using-async-and-await.md)
- [Zaman uyumsuz programlarda denetim akışı (C#)](./control-flow-in-async-programs.md)
- [async](../../../language-reference/keywords/async.md)
- [await](../../../language-reference/operators/await.md)
