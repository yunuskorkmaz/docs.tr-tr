---
title: Zaman uyumsuz dönüş türleri (C#)
ms.date: 05/29/2017
ms.assetid: ddb2539c-c898-48c1-ad92-245e4a996df8
ms.openlocfilehash: 3d3c7d610dd1287d2c7284a5edd9c92810a74dba
ms.sourcegitcommit: ea00c05e0995dae928d48ead99ddab6296097b4c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48036246"
---
# <a name="async-return-types-c"></a>Zaman uyumsuz dönüş türleri (C#)
Zaman uyumsuz yöntemler, aşağıdaki dönüş türlerine sahip olabilir:

- <xref:System.Threading.Tasks.Task%601>, bir değer döndüren zaman uyumsuz bir yöntem için. 
 
-  <xref:System.Threading.Tasks.Task>, bir işlemi gerçekleştirir, ancak hiçbir değer döndürmeyen bir zaman uyumsuz yöntem için.

- `void`, bir olay işleyicisi için. 

- C# 7.0, bir erişilebilir olan herhangi bir türü'ile başlayan `GetAwaiter` yöntemi. Tarafından döndürülen nesne `GetAwaiter` yöntemi uygulanmalı <xref:System.Runtime.CompilerServices.ICriticalNotifyCompletion?displayProperty=nameWithType> arabirimi.
  
Zaman uyumsuz yöntemler hakkında daha fazla bilgi için bkz. [Asynchronous Programming with async ve await (C#)](../../../../csharp/programming-guide/concepts/async/index.md).  
  
Her dönüş türü aşağıdaki bölümlerden birinde incelenir ve konunun sonunda üç türü kullanan bir tam örnek bulabilirsiniz.  
  
##  <a name="BKMK_TaskTReturnType"></a> Görev\<TResult\> dönüş türü  
<xref:System.Threading.Tasks.Task%601> Dönüş türü içeren zaman uyumsuz yöntemi için kullanılan bir [dönüş](../../../../csharp/language-reference/keywords/return.md) işlenen türü içeren (C#) ifadesi `TResult`.  
  
Aşağıdaki örnekte, `GetLeisureHours` zaman uyumsuz yönteminde bir `return` deyimi bir tamsayı döndürür. Bu nedenle, yöntem bildiriminde bir dönüş türü belirtmelisiniz `Task<int>`.  <xref:System.Threading.Tasks.Task.FromResult%2A> Zaman uyumsuz yöntem bir dize döndüren bir işlem için bir yer tutucudur.
  
[!code-csharp[return-value](../../../../../samples/snippets/csharp/programming-guide/async/async-returns1.cs)]

Zaman `GetLeisureHours` bir await ifadesine içinde çağrılır `ShowTodaysInfo` yöntemi, await ifadesi tamsayı değerini alır (değerini `leisureHours`) tarafından döndürülen görev depolanan `GetLeisureHours` yöntemi. Hakkında daha fazla bilgi için await ifadeleri, bkz: [await](../../../../csharp/language-reference/keywords/await.md).  
  
Çağrı ayırarak nasıl böyle daha iyi anlamak `GetLeisureHours` uygulamasından `await`aşağıdaki kodda gösterildiği gibi. Yöntemine yapılan bir çağrı `GetLeisureHours` hemen beklenmeyen döndürür, değilse bir `Task<int>`, yöntem bildiriminden beklediğiniz gibi. Görevin atandığı `infoTask` örnekte değişken. Çünkü `infoTask` olduğu bir <xref:System.Threading.Tasks.Task%601>, içerdiği bir <xref:System.Threading.Tasks.Task%601.Result> türünün özelliği `TResult`. Bu durumda, `TResult` bir tamsayı türünü temsil eder. Zaman `await` uygulanan `infoTask`, bekleme ifadesi içeriğine göre değerlendirilir <xref:System.Threading.Tasks.Task%601.Result%2A> özelliği `infoTask`. Değeri atanır `ret` değişkeni.  
  
> [!IMPORTANT]
>  <xref:System.Threading.Tasks.Task%601.Result%2A> Özelliği engelleyici bir özelliktir. Kendi görevi bitmeden önce buna erişmeyi denerseniz, şu anda etkin olan iş parçacığı değeri kullanılabilir ve görev tamamlanıncaya kadar engellenir. Çoğu durumda, değeri kullanarak erişmeli `await` özelliği doğrudan erişmek yerine. <br/> Değerini önceki örnekte alınan <xref:System.Threading.Tasks.Task%601.Result%2A> ana iş parçacığı engellemek için özellik böylece `ShowTodaysInfo` yöntemi uygulama sona ermeden önce yürütme son.  

[!code-csharp[return-value](../../../../../samples/snippets/csharp/programming-guide/async/async-returns1a.cs#1)]
  
##  <a name="BKMK_TaskReturnType"></a> Görev dönüş türü  
İçermeyen zaman uyumsuz yöntemler bir `return` , ya da bir deyim içeren bir `return` genellikle dönüş işleneni deyim dönüş türüne sahip <xref:System.Threading.Tasks.Task>. Bu tür yöntemler döndürür `void` zaman uyumlu olarak çalıştırırsanız. Kullanıyorsanız bir <xref:System.Threading.Tasks.Task> dönüş türü için zaman uyumsuz yöntemi çağıran bir yöntemi kullanabilirsiniz bir `await` çağrılan zaman uyumsuz yöntemi bitene kadar çağıranın tamamlanmasını bekletmek için işleci.  
  
Aşağıdaki örnekte, `WaitAndApologize` zaman uyumsuz yöntem içermiyor bir `return` yöntemi döndürecek şekilde deyimi bir <xref:System.Threading.Tasks.Task> nesne. Böylece `WaitAndApologize` beklenmesini. Unutmayın <xref:System.Threading.Tasks.Task> türü içermez bir `Result` özelliği olduğundan, dönüş değeri yok.  

[!code-csharp[return-value](../../../../../samples/snippets/csharp/programming-guide/async/async-returns2.cs)]  
  
`WaitAndApologize` void döndüren bir zaman uyumlu yöntem için çağırma deyimine benzer bir await ifadesi yerine await deyimi kullanılarak beklenir. Bir await işleci uygulaması, bu durumda değer üretemez.  
  
Önceki olduğu gibi <xref:System.Threading.Tasks.Task%601> örnek, çağrı ayırabilirsiniz `WaitAndApologize` aşağıdaki kod, bir await işlecinin uygulamasından gösterir. Ancak, unutmayın bir `Task` sahip olmayan bir `Result` özelliği ve bir await işleci uygulandığında, değer üretilmediğini bir `Task`.  
  
Aşağıdaki kod ayırır `WaitAndApologize` yöntemin döndürdüğü görevi bekleme işleminden yöntemi.  
 
[!code-csharp[return-value](../../../../../samples/snippets/csharp/programming-guide/async/async-returns2a.cs#1)]  
 
##  <a name="BKMK_VoidReturnType"></a> Void dönüş türü

Kullandığınız `void` dönüş türünü gerektiren zaman uyumsuz olay işleyicilerini içinde bir `void` dönüş türü. Döndürme zorunluluğu dışında bir değer döndürmez olay işleyicisi yöntemleri için bir <xref:System.Threading.Tasks.Task> bunun yerine, döndüren zaman uyumsuz bir yöntem olduğundan `void` beklenemez. Tüm bu yöntemi çağıran kişi çağrılan zaman uyumsuz yöntemin tamamlanmasını beklemeden tamamlanana kadar devam edebilir ve çağıran zaman uyumsuz yöntemin oluşturduğu özel durumları veya değerlerden bağımsız olmalıdır.  
  
Void döndüren zaman uyumsuz yöntemi çağıran kişi yöntemden atılan özel durumları yakalayamaz ve böyle işlenmeyen özel durumların, uygulamanızın başarısız olmasına neden olabilecek. Döndüren zaman uyumsuz yöntemde özel durum oluşursa bir <xref:System.Threading.Tasks.Task> veya <xref:System.Threading.Tasks.Task%601>, özel durum getirilen görevde depolanır ve görev beklenirken yeniden atılır. Bu nedenle, bir özel durum oluşturabilecek herhangi bir zaman uyumsuz yöntem dönüş türüne sahip olduğundan emin olun <xref:System.Threading.Tasks.Task> veya <xref:System.Threading.Tasks.Task%601> ve yöntemine yönelik çağrılar beklediğinden.  
  
Zaman uyumsuz yöntemlerde özel durumları yakalama hakkında daha fazla bilgi için bkz. [zaman uyumsuz yöntemlerde özel durumları](../../../language-reference/keywords/try-catch.md#exceptions-in-async-methods) bölümünü [try-catch](../../../language-reference/keywords/try-catch.md) konu.  
  
Aşağıdaki örnek, zaman uyumsuz olay işleyicisi davranışını gösterir. Örnek kodda unutmayın, zaman uyumsuz olay işleyicisi ana iş parçacığı bittiğinde bilmeniz bildirmeniz gerekir. Ardından ana iş parçacığı zaman uyumsuz olay işleyicisi program çıkmadan önce tamamlanmasını bekleyebilirsiniz.
 
[!code-csharp[return-value](../../../../../samples/snippets/csharp/programming-guide/async/async-returns3.cs)]  
 
## <a name="generalized-async-return-types-and-valuetasktresult"></a>Genelleştirilmiş bir zaman uyumsuz dönüş türleri ve ValueTask\<TResult\>

C# 7.0 ile başlayarak, bir zaman uyumsuz yöntem bir erişilebilir olan herhangi bir türü döndürebilir `GetAwaiter` yöntemi.
 
Çünkü <xref:System.Threading.Tasks.Task> ve <xref:System.Threading.Tasks.Task%601> olan başvuru türleri, performans açısından kritik yollarda bellek ayırma özellikle ayırmaları sıkı Döngülerde oluştuğunda olumsuz performansı etkileyebilir. Destek için ek bellek ayırmaları önlemek için bir başvuru türü yerine bir basit değer türü döndürebilir genelleştirilmiş dönüş türleri anlamına gelir. 

.NET sağlar <xref:System.Threading.Tasks.ValueTask%601?displayProperty=nameWithType> yapısı olarak genelleştirilmiş bir görev döndüren değer hafif uygulamasıdır. Kullanılacak <xref:System.Threading.Tasks.ValueTask%601?displayProperty=nameWithType> türü eklemelisiniz `System.Threading.Tasks.Extensions` NuGet paketini projenize. Aşağıdaki örnekte <xref:System.Threading.Tasks.ValueTask%601> yapısı iki dice değerini almak için yapar. 
  
[!code-csharp[return-value](../../../../../samples/snippets/csharp/programming-guide/async/async-valuetask.cs)]

## <a name="see-also"></a>Ayrıca Bkz.

- <xref:System.Threading.Tasks.Task.FromResult%2A>   
- [İzlenecek yol: async kullanarak Web'e erişme ve await (C#)](../../../../csharp/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)   
- [Denetim akışı zaman uyumsuz programlarda (C#)](../../../../csharp/programming-guide/concepts/async/control-flow-in-async-programs.md)   
- [async](../../../../csharp/language-reference/keywords/async.md)   
- [await](../../../../csharp/language-reference/keywords/await.md)
