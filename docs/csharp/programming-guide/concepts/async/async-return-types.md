---
title: Async İade Türleri (C#)
ms.date: 04/14/2020
ms.assetid: ddb2539c-c898-48c1-ad92-245e4a996df8
ms.openlocfilehash: 73a6e1924652c8635377547e2faddc864ac5540a
ms.sourcegitcommit: c91110ef6ee3fedb591f3d628dc17739c4a7071e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/15/2020
ms.locfileid: "81389130"
---
# <a name="async-return-types-c"></a>Async İade Türleri (C#)

Async yöntemleri aşağıdaki iade türlerine sahip olabilir:

- <xref:System.Threading.Tasks.Task%601>, bir değer döndüren bir async yöntemi için.
- <xref:System.Threading.Tasks.Task>, bir işlemi gerçekleştiren ancak değer döndüren bir async yöntemi için.
- `void`, bir olay işleyicisi için.
- C# 7.0 ile başlayarak, erişilebilir `GetAwaiter` bir yönteme sahip herhangi bir tür. `GetAwaiter` Yöntem tarafından döndürülen nesne <xref:System.Runtime.CompilerServices.ICriticalNotifyCompletion?displayProperty=nameWithType> arabirimi uygulamalıdır.
- C# 8.0 ile <xref:System.Collections.Generic.IAsyncEnumerable%601>başlayarak, bir *async akışı*döndüren bir async yöntemi için.

Async yöntemleri hakkında daha fazla bilgi için, [async ile Asynchronous Programming'e bakın ve (C#) bekleyin.](./index.md)  
  
## <a name="tasktresult-return-type"></a>Görev\<Sonuç\> İade Türü  
İade <xref:System.Threading.Tasks.Task%601> türü, operand'ın içinde bulunduğu bir [return](../../../language-reference/keywords/return.md) (C#) deyimini `TResult`içeren bir async yöntemi için kullanılır.  
  
Aşağıdaki örnekte, `GetLeisureHours` async yöntemi `return` bir tamsayı döndüren bir deyim içerir. Bu nedenle, yöntem bildirimi bir `Task<int>`dönüş türü belirtmelidir.  Async <xref:System.Threading.Tasks.Task.FromResult%2A> yöntemi, dize döndüren bir işlem için bir yer tutucudur.
  
:::code language="csharp" source="./snippets/async-returns1.cs" id="SnippetFirstExample":::

Yöntemdeki bekleyen ifadesinin içinden `GetLeisureHours` çağrıldığında, bekleyen ifade `GetLeisureHours` yöntem tarafından döndürülen `leisureHours`görevde depolanan hesaplaç değerini (değeri) alır. `ShowTodaysInfo` Bekleyen ifadeler hakkında daha fazla bilgi için, [bkz.](../../../language-reference/operators/await.md)  
  
Aşağıdaki kodun `await` gösterdiği `await`gibi, aramayı `Task<T>` `GetLeisureHours` uygulamadan ayırarak sonucu nasıl aldığını daha iyi anlayabilirsiniz. Hemen beklenmeyen `GetLeisureHours` yöntem çağrısı, yöntemin bildiriminden beklediğiniz gibi bir `Task<int>`döndürür. Görev örnekteki `integerTask` değişkene atanır. Çünkü `integerTask` bir <xref:System.Threading.Tasks.Task%601>, bu <xref:System.Threading.Tasks.Task%601.Result> tür `TResult`bir özellik içerir. Bu durumda, `TResult` bir tamsayı türünü temsil eder. Uygulandığında `await` `integerTask`, bekleme ifadesi <xref:System.Threading.Tasks.Task%601.Result%2A> özelliğinin içeriğini `integerTask`değerlendirir. Değer `ret` değişkene atanır.  
  
> [!IMPORTANT]
> Tesis, <xref:System.Threading.Tasks.Task%601.Result%2A> engelleyici bir özelliktir. Görevi tamamlanmadan önce erişmeye çalışırsanız, görev tamamlanana ve değer kullanılabilir olana kadar şu anda etkin olan iş parçacığı engellenir. Çoğu durumda, doğrudan özelliğine erişmek `await` yerine kullanarak değere erişmelisiniz. <br/> Önceki örnek, <xref:System.Threading.Tasks.Task%601.Result%2A> `ShowTodaysInfo` yöntemin uygulama sona ermeden önce yürütmeyi bitirebilmeleri için ana iş parçacığı engellemek için özelliğin değerini aldı.  

:::code language="csharp" source="./snippets/async-returns1a.cs" id="SnippetSecondVersion":::

## <a name="task-return-type"></a>Görev İade Türü  
İfade `return` içermeyen veya oper return olmayan ve `return` genellikle bir dönüş türüne sahip bir deyim <xref:System.Threading.Tasks.Task>içermeyen async yöntemleri. Bu tür `void` yöntemler eşzamanlı çalıştırılırsa geri döner. Async yöntemi <xref:System.Threading.Tasks.Task> için bir iade türü kullanıyorsanız, bir `await` arama yöntemi çağrılan async yöntemi tamamlanana kadar arayanın tamamlanmasını askıya almak için bir işleç kullanabilirsiniz.  
  
Aşağıdaki örnekte, `WaitAndApologize` async yöntemi bir `return` deyim içermez, bu nedenle <xref:System.Threading.Tasks.Task> yöntem bir nesne döndürür. Bir `Task` `WaitAndApologize` döndürülme beklenen sağlar. İade <xref:System.Threading.Tasks.Task> değeri olmadığından türü `Result` bir özellik içermez.  

:::code language="csharp" source="./snippets/async-returns2.cs" id="SnippetTaskReturn":::

`WaitAndApologize`senkron boşluk döndürme yöntemi için çağrı deyimine benzer bir bekleme ifadesi yerine bir bekleme ifadesi kullanılarak beklenen bir ifadedir. Bu durumda bekleyen bir işleç uygulaması bir değer üretmez.  
  
Önceki <xref:System.Threading.Tasks.Task%601> örnekte olduğu gibi, aşağıdaki `WaitAndApologize` kodun gösterdiği gibi, aramayı bekleyen bir işlecinin uygulamasından ayırabilirsiniz. Ancak, a'nın `Task` bir `Result` özelliği olmadığını ve bekleyen bir işleç bir `Task`.'e uygulandığında hiçbir değer inanMadığını unutmayın.  
  
Aşağıdaki kod, `WaitAndApologize` metod çağırma yöntemini yöntemin döndürdettiği görevi beklemekten ayırır.  

:::code language="csharp" source="./snippets/async-returns2a.cs" id="SnippetAwaitTask":::

## <a name="void-return-type"></a>Geçersiz dönüş türü

`void` İade türünü, iade türü gerektiren eşsenkronize olay işleyicilerinde kullanırsınız. `void` Bir değer döndürmeyen olay işleyicileri dışındaki yöntemler için, <xref:System.Threading.Tasks.Task> döndüren `void` bir async yöntemi beklenemediği için bunun yerine bir döndürmeniz gerekir. Böyle bir yöntemin herhangi bir arayan bitiş için adlandırılan async yöntemi beklemeden tamamlamaya devam etmelidir. Arayan, async yönteminin oluşturduğu değerlerden veya özel farklardan bağımsız olmalıdır.  
  
Geçersiz dönen bir async yöntemini arayan yöntemden atılan özel durumları yakalayamaz ve bu tür işlenmemiş özel durumlar uygulamanızın başarısız olması muhtemeldir. Bir <xref:System.Threading.Tasks.Task> özel durum döndüren veya <xref:System.Threading.Tasks.Task%601> özel durum atan bir yöntem varsa, özel durum döndürülen görevde depolanır. Görev beklenen zaman özel durum yeniden atılır. Bu nedenle, bir özel durum oluşturabilen herhangi bir <xref:System.Threading.Tasks.Task> async yönteminin bir dönüş türü olduğundan veya <xref:System.Threading.Tasks.Task%601> yönteme çağrı beklediğinden emin olun.  
  
Özel durumları async yöntemlerinde nasıl yakalayacağız hakkında daha fazla bilgi için, [try-catch](../../../language-reference/keywords/try-catch.md) makalesinin [Async Yöntemleri](../../../language-reference/keywords/try-catch.md#exceptions-in-async-methods) bölümündeki Özel Durumlar bölümüne bakın.  
  
Aşağıdaki örnek, bir async olay işleyicisi davranışını gösterir. Örnek kodda, bir async olay işleyicisi ana iş parçacığıne ne zaman bitacağını bildirmelidir. Daha sonra ana iş parçacığı programdan çıkmadan önce tamamlanması için bir async olay işleyicisi için bekleyebilirsiniz.

:::code language="csharp" source="./snippets/async-returns3.cs":::

## <a name="generalized-async-return-types-and-valuetasktresult"></a>Genelleştirilmiş async dönüş türleri\<ve ValueTask TResult\>

C# 7.0 ile başlayarak, bir async yöntemi `GetAwaiter` erişilebilir bir yöntem eki olan herhangi bir türü döndürebilir.

Başvuru <xref:System.Threading.Tasks.Task> <xref:System.Threading.Tasks.Task%601> türleri olduğundan ve kaynak türleri olduğundan, performans açısından kritik yollarda bellek ayırma, özellikle de ayırmalar sıkı döngülerde gerçekleştiğinde, performansı olumsuz etkileyebilir. Genelleştirilmiş iade türleri için destek, ek bellek ayırmalarını önlemek için başvuru türü yerine hafif bir değer türü döndürebileceğiniz anlamına gelir.

.NET, <xref:System.Threading.Tasks.ValueTask%601?displayProperty=nameWithType> genelleştirilmiş görev döndüren değerin hafif bir uygulaması olarak yapıyı sağlar. <xref:System.Threading.Tasks.ValueTask%601?displayProperty=nameWithType> Türü kullanmak için Projenize `System.Threading.Tasks.Extensions` NuGet paketini eklemeniz gerekir. Aşağıdaki örnek, <xref:System.Threading.Tasks.ValueTask%601> iki zar rulo değerini almak için yapıyı kullanır.
  
:::code language="csharp" source="./snippets/async-valuetask.cs":::

## <a name="async-streams-with-iasyncenumerablet"></a>IAsyncEnumerable\<T ile async akışları\>

C# 8.0 ile başlayarak, bir async yöntemi ile <xref:System.Collections.Generic.IAsyncEnumerable%601>temsil edilen bir *async akışı*döndürebilir. Async akışı, öğeler yinelenen eşzamanlı çağrılarla parçalar halinde oluşturulduğunda, akıştan okunan öğeleri sayısala aktarmak için bir yol sağlar. Aşağıdaki örnekte, async akışı oluşturan bir async yöntemi gösterilmektedir:

:::code language="csharp" source="./snippets/AsyncStreams.cs" id="SnippetGenerateAsyncStream":::

Önceki örnek, bir dizedeki satırları eşit olarak okur. Her satır okunduktan sonra, kod dizedeki her sözcüğü numaralandırır. Arayanlar ifadeyi kullanarak her sözcüğü `await foreach` sayısala erdirler. Yöntem, kaynak dizeden bir sonraki satırı eş senkronize olarak okuması gerektiğinde sizi bekler.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Threading.Tasks.Task.FromResult%2A>
- [Walkthrough: Async kullanarak Web'e erişim ve bekleme (C#)](./walkthrough-accessing-the-web-by-using-async-and-await.md)
- [Async Programlarında Kontrol Akışı (C#)](./control-flow-in-async-programs.md)
- [async](../../../language-reference/keywords/async.md)
- [await](../../../language-reference/operators/await.md)
