---
title: Zaman uyumsuz dönüş türleri (C#)
ms.date: 05/29/2017
ms.assetid: ddb2539c-c898-48c1-ad92-245e4a996df8
ms.openlocfilehash: 07aefcf3149b2210e3dc97713647fa3a0133a535
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33334190"
---
# <a name="async-return-types-c"></a>Zaman uyumsuz dönüş türleri (C#)
Zaman uyumsuz yöntemleri dönüş türleri aşağıdakilere sahip olabilir:

- <xref:System.Threading.Tasks.Task%601>, bir değer döndüren bir zaman uyumsuz yöntem için. 
 
-  <xref:System.Threading.Tasks.Task>, bir işlemi gerçekleştirir, ancak hiçbir değer döndürmeyen bir zaman uyumsuz yöntem için.

- `void`, bir olay işleyici. 

- C# 7.0, bir erişilebilir olan herhangi bir tür'ile başlayan `GetAwaiter` yöntemi. Tarafından döndürülen nesne `GetAwaiter` yöntemi uygulanmalı <xref:System.Runtime.CompilerServices.ICriticalNotifyCompletion?displayProperty=nameWithType> arabirimi.
  
Zaman uyumsuz yöntemleri hakkında daha fazla bilgi için bkz: [zaman uyumsuz programlama ile async ve await (C#)](../../../../csharp/programming-guide/concepts/async/index.md).  
  
Her bir dönüş türü aşağıdaki bölümlerde biri incelenir ve konunun sonunda üç kullanan tam bir örnek bulabilirsiniz.  
  
##  <a name="BKMK_TaskTReturnType"></a> Task(T) dönüş türü  
<xref:System.Threading.Tasks.Task%601> Dönüş türü içeren bir zaman uyumsuz yöntem için kullanılan bir [dönmek](../../../../csharp/language-reference/keywords/return.md) işlenenin türü vardır (C#) deyimi `TResult`.  
  
Aşağıdaki örnekte, `GetLeisureHours` async yöntemi içeren bir `return` deyimi bir tamsayı döndürür. Bu nedenle, yöntem bildirimi dönüş türünü belirtmeniz gerekir `Task<int>`.  <xref:System.Threading.Tasks.Task.FromResult%2A> Async yöntemi bir dize döndürür. bir işlem için bir yer tutucudur.
  
[!code-csharp[return-value](../../../../../samples/snippets/csharp/programming-guide/async/async-returns1.cs)]

Zaman `GetLeisureHours` bekleme deyimde içinde çağrılır `ShowTodaysInfo` yöntemi, bekleme ifade tamsayı değerini alır (değerini `leisureHours`) tarafından döndürülen görev depolanan `GetLeisureHours` yöntemi. Hakkında daha fazla bilgi için ifadeleri await, bkz: [await](../../../../csharp/language-reference/keywords/await.md).  
  
Bu çağrı ayırarak nasıl gerçekleştiğini daha iyi anlamak `GetLeisureHours` uygulamadan `await`, aşağıdaki kodda gösterildiği gibi. Yöntemine yapılan bir çağrı `TaskOfT_MethodAsync` hemen beklemenin döndürür değil bir `Task<int>`yöntemi bildiriminden beklediğiniz gibi. Görev atandığı `integerTask` örnekte değişken. Çünkü `integerTask` olan bir <xref:System.Threading.Tasks.Task%601>, içerdiği bir <xref:System.Threading.Tasks.Task%601.Result> türündeki özelliği `TResult`. Bu durumda, TResult bir tamsayı türünü temsil eder. Zaman `await` uygulanan `integerTask`, içeriğini bekleme ifadeyi hesaplar <xref:System.Threading.Tasks.Task%601.Result%2A> özelliği `integerTask`. Değer atandığı `result2` değişkeni.  
  
> [!IMPORTANT]
>  <xref:System.Threading.Tasks.Task%601.Result%2A> Özelliği engelleyen bir özelliğidir. Görevini bitmeden önce erişmeyi denerseniz, şu anda etkin olan iş parçacığının görevi tamamlandıktan ve değeri kullanılabilir kadar engellendi. Çoğu durumda, kullanarak değeri erişmelidir `await` özelliği doğrudan erişimini yerine. <br/> Önceki örnekte değerini alınan <xref:System.Threading.Tasks.Task%601.Result%2A> ana iş parçacığı engellemek için özellik böylece `ShowTodaysInfo` yöntemi uygulama sona ermeden önce yürütme son.  

[!code-csharp[return-value](../../../../../samples/snippets/csharp/programming-guide/async/async-returns1a.cs#1)]
  
##  <a name="BKMK_TaskReturnType"></a> Görev dönüş türü  
İçermeyen zaman uyumsuz yöntemleri bir `return` deyimi ya da içeren bir `return` işleneni genellikle döndürmez deyim dönüş türüne sahip <xref:System.Threading.Tasks.Task>. Bu tür yöntemleri döndürür `void` zaman uyumlu olarak çalıştırırsanız. Kullanırsanız, bir <xref:System.Threading.Tasks.Task> dönüş türü için bir zaman uyumsuz yöntemi, bir arama yöntemi kullanabilirsiniz bir `await` çağrılan zaman uyumsuz yöntem tamamlanana kadar arayanın tamamlama askıya almak için işleci.  
  
Aşağıdaki örnekte, `WaitAndApologize` zaman uyumsuz yöntem içermiyor bir `return` yöntemi döndürecek şekilde deyimi bir <xref:System.Threading.Tasks.Task> nesnesi. Böylece `WaitAndApologize` beklemenin için. Unutmayın <xref:System.Threading.Tasks.Task> türü içermez bir `Result` özelliği bir dönüş değerine sahip olduğundan.  

[!code-csharp[return-value](../../../../../samples/snippets/csharp/programming-guide/async/async-returns2.cs)]  
  
`WaitAndApologize` zaman uyumlu bir geçersiz kılma döndürme yöntemi için arama deyimi benzer bir bekleme deyim yerine bir bekleme deyimi kullanarak beklemenin. Bekleme operatörün uygulama bu durumda bir değeri oluşturmuyor.  
  
Önceki gibi <xref:System.Threading.Tasks.Task%601> örnek, çağrısı ayırabilirsiniz `Task_MethodAsync` aşağıdaki kod bir bekleme işleç uygulamadan gösterir. Ancak, unutmayın bir `Task` sahip olmayan bir `Result` özelliği ve bekleme operatörün uygulandığında herhangi bir değer üretilir bir `Task`.  
  
Aşağıdaki kod arama ayıran `WaitAndApologize` yöntemi döndürür görev bekleyen gelen yöntemi.  
 
[!code-csharp[return-value](../../../../../samples/snippets/csharp/programming-guide/async/async-returns2a.cs#1)]  
 
##  <a name="BKMK_VoidReturnType"></a> Dönüş türü void  
Kullandığınız `void` dönüş türü gerektiren zaman uyumsuz olay işleyicileri ile bir `void` dönüş türü. Olay dışında yöntemleri için işleyicileri olmayan bir değer, iade bir <xref:System.Threading.Tasks.Task> bunun yerine, bir zaman uyumsuz yöntem döndürdüğünden `void` beklemenin olamaz. Böyle bir yöntemin herhangi bir çağırıcı tamamlanması için çağrılan zaman uyumsuz yöntemi beklemeden tamamlanıncaya kadar devam edebilirsiniz ve çağıranın tüm değerleri veya zaman uyumsuz yöntem oluşturur özel durumlar bağımsız olması gerekir.  
  
Bir geçersiz kılma döndüren zaman uyumsuz yöntem arayan yönteminden oluşturulan özel durumları yakalamak olamaz ve böyle işlenmeyen özel durumlar, uygulamanızın başarısız olmasına yol açabilir. Bir özel durum döndüren bir zaman uyumsuz yöntem oluşursa bir <xref:System.Threading.Tasks.Task> veya <xref:System.Threading.Tasks.Task%601>, özel durum döndürülen görevde depolanır ve görev beklemenin zaman işlenemezse. Bu nedenle, bir özel durum oluşturmak üzere herhangi bir zaman uyumsuz yöntemi dönüş türüne sahip olduğundan emin olun <xref:System.Threading.Tasks.Task> veya <xref:System.Threading.Tasks.Task%601> ve yöntemine yönelik çağrılar beklemenin.  
  
Zaman uyumsuz yöntemleri özel durumlarını yakalama hakkında daha fazla bilgi için bkz: [try-catch](../../../../csharp/language-reference/keywords/try-catch.md) .  
  
Aşağıdaki eample zaman uyumsuz olay işleyicisi tanımlar.  
 
[!code-csharp[return-value](../../../../../samples/snippets/csharp/programming-guide/async/async-returns3.cs)]  
 
## <a name="generalized-async-return-types-and-valuetaskt"></a>Genelleştirilmiş zaman uyumsuz dönüş türleri ve ValueTask<T>

C# 7. 0'dan başlayarak, bir zaman uyumsuz yöntem bir erişilebilir olan herhangi bir tür döndürebilir `GetAwaiter` yöntemi.
 
Çünkü <xref:System.Threading.Tasks.Task> ve <xref:System.Threading.Tasks.Task%601> olan başvuru türleri, bellek ayırma performans açısından kritik yollarda özellikle ayırmaları sıkı Döngülerde oluştuğunda olumsuz performansı etkileyebilir. Destek için ek bellek ayırmaları önlemek için bir başvuru türü yerine basit değer türü döndürebilir genelleştirilmiş dönüş türleri anlamına gelir. 

.NET sağlar <xref:System.Threading.Tasks.ValueTask%601?displayProperty=nameWithType> yapısı genelleştirilmiş bir görev döndürme değeri hafif uyarlamasını olarak. Kullanılacak <xref:System.Threading.Tasks.ValueTask%601?displayProperty=nameWithType> türü eklemelisiniz `System.Threading.Tasks.Extensions` NuGet paketini projenize. Aşağıdaki örnek kullanır <xref:System.Threading.Tasks.ValueTask%601> iki bölmek değerini almak için yapısı yapar. 
  
[!code-csharp[return-value](../../../../../samples/snippets/csharp/programming-guide/async/async-valuetask.cs)]

## <a name="see-also"></a>Ayrıca bkz.  
<xref:System.Threading.Tasks.Task.FromResult%2A>   
[İzlenecek yol: async kullanarak Web'e erişme ve await (C#)](../../../../csharp/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)   
[Denetim akışı zaman uyumsuz programlarda (C#)](../../../../csharp/programming-guide/concepts/async/control-flow-in-async-programs.md)   
[Zaman uyumsuz](../../../../csharp/language-reference/keywords/async.md)   
[await](../../../../csharp/language-reference/keywords/await.md)
