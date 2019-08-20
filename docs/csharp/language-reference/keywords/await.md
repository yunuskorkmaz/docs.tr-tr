---
title: await- C# başvuru
ms.custom: seodec18
ms.date: 05/22/2017
f1_keywords:
- await_CSharpKeyword
helpviewer_keywords:
- await keyword [C#]
- await [C#]
ms.assetid: 50725c24-ac76-4ca7-bca1-dd57642ffedb
ms.openlocfilehash: 2f6fb9fb8c29013165298c186ec072aa1e750ab9
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69602293"
---
# <a name="await-c-reference"></a>await (C# Başvurusu)
`await` İşleci, beklenen görev tamamlanana kadar yöntemin yürütülmesine bir askıya alma noktası eklemek için zaman uyumsuz bir yöntemde bir göreve uygulanır. Görev, devam eden işi temsil eder.  
  
`await`yalnızca [Async](./async.md) anahtar sözcüğü tarafından değiştirilen zaman uyumsuz bir yöntemde kullanılabilir. Bu tür bir yöntem, `async` değiştirici kullanılarak tanımlanır ve genellikle bir veya daha fazla `await` ifade içeren bir *zaman uyumsuz yöntem*olarak adlandırılır.  
  
> [!NOTE]
> Ve anahtar sözcükleri 5 ' te C# tanıtılmıştı. `await` `async` Zaman uyumsuz programlamaya giriş için bkz. [Async ve await Ile zaman uyumsuz programlama](../../programming-guide/concepts/async/index.md).  
  
`await` İşlecin uygulandığı görev, genellikle [görev tabanlı zaman uyumsuz model](../../../standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md)uygulayan bir yönteme yapılan bir çağrı tarafından döndürülür. Bunlar,,, ve <xref:System.Threading.Tasks.Task> <xref:System.Threading.Tasks.Task%601>nesneleridöndüren <xref:System.Threading.Tasks.ValueTask>yöntemleri içerir<xref:System.Threading.Tasks.ValueTask%601> .  

Aşağıdaki örnekte, <xref:System.Net.Http.HttpClient.GetByteArrayAsync%2A?displayProperty=nameWithType> yöntemi bir `Task<byte[]>`döndürür. Görev tamamlandığında gerçek bayt dizisini üretmek için bir taahhüddir. İşleci, <xref:System.Net.Http.HttpClient.GetByteArrayAsync%2A> yöntemin çalışması tamamlanana kadar yürütmeyi askıya alır. `await` Bu sırada denetim, çağıran `GetPageSizeAsync`öğesine döndürülür. Görev yürütmeyi bitirdiğinde, `await` ifade bir bayt dizisi olarak değerlendirilir.  

[!code-csharp[await-example](../../../../samples/snippets/csharp/language-reference/keywords/await/await1.cs)]  

> [!IMPORTANT]
> Tüm örnek için bkz [. İzlenecek yol: Async ve await](../../programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)kullanarak Web 'e erişme. Örneği, Microsoft Web sitesindeki [Geliştirici kodu örneklerinden](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f) indirebilirsiniz. Örnek, AsyncWalkthrough_HttpClient projem.  
  
Önceki örnekte `await` gösterildiği gibi, döndüren bir `Task<TResult>`yöntem çağrısının sonucuna uygulanırsa, `await` ifadesinin türü olur `TResult`. , Döndüren bir `Task`yöntem çağrısının sonucuna uygulanırsa, `await` ifadesinin türü olur `void`. `await` Aşağıdaki örnek, farkı göstermektedir.  
  
```csharp  
// await keyword used with a method that returns a Task<TResult>.  
TResult result = await AsyncMethodThatReturnsTaskTResult();  
  
// await keyword used with a method that returns a Task.  
await AsyncMethodThatReturnsTask();  

// await keyword used with a method that returns a ValueTask<TResult>.
TResult result = await AsyncMethodThatReturnsValueTaskTResult();
```  
  
Bir `await` ifade, üzerinde yürütüldüğü iş parçacığını engellemez. Bunun yerine, derleyicinin zaman uyumsuz yöntemin geri kalanını beklenen görevde devamlılık olarak kaydetmesine neden olur. Sonra Denetim zaman uyumsuz yöntemi çağırana döner. Görev tamamlandığında, devamlılığını çağırır ve zaman uyumsuz yöntemin yürütülmesi kaldığınız yerden devam eder.  
  
Bir `await` ifade yalnızca kapsayan metodun, lambda ifadesinin veya anonim yöntemin gövdesinde gerçekleşebilir, bu da bir `async` değiştiriciyle işaretlenmelidir. *Await* terimi yalnızca söz konusu bağlamda anahtar sözcük olarak işlev görür. Başka bir yerde, tanımlayıcı olarak yorumlanır. Yöntem, lambda ifadesi veya anonim yöntem içinde bir `await` ifade, zaman uyumlu bir işlevin gövdesinde, bir sorgu ifadesinde, bir [kilit deyiminin](./lock-statement.md)bloğunda veya [güvenli olmayan](./unsafe.md) bir bağlamda gerçekleşemez.  
  
## <a name="exceptions"></a>Özel Durumlar  
En zaman uyumsuz yöntemler bir <xref:System.Threading.Tasks.Task> veya <xref:System.Threading.Tasks.Task%601>döndürür. Döndürülen görevin özellikleri, görevin tamamlanıp tamamlanmayacağı, zaman uyumsuz yöntemin bir özel durum mi olduğunu, yoksa iptal edildiğini mi olduğunu ve nihai sonucun ne olduğunu belirtir gibi durum ve geçmişi hakkındaki bilgileri taşır. İşleci, `GetAwaiter` yöntemi tarafından döndürülen nesnedeki yöntemleri çağırarak bu özelliklere erişir. `await`  
  
Bir özel duruma neden olan bir görev döndüren zaman uyumsuz yöntemi beklelerseniz, `await` işleç özel durumu yeniden oluşturur.  
  
İptal edilen bir görev döndüren zaman uyumsuz yöntemi beklelerseniz, `await` işleç yeniden <xref:System.OperationCanceledException>atar.  
  
Hatalı durumda olan tek bir görev birden çok özel durumu yansıtabilir. Örneğin, görev bir çağrısının <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType>sonucu olabilir. Böyle bir görevi beklelerseniz, await işlemi özel durumların yalnızca birini yeniden oluşturur. Ancak, özel durumların hangisinin yeniden oluşturulduğu tahmin edebilirsiniz.  
  
Zaman uyumsuz yöntemlerde hata işleme örnekleri için bkz. [try-catch](./try-catch.md).  
  
## <a name="example"></a>Örnek  
Aşağıdaki örnek, içindeki URL 'Leri komut satırı bağımsız değişkenleri olarak geçirilen sayfalardaki toplam karakter sayısını döndürür. Örnek, `async` anahtar sözcüğüyle `GetPageLengthsAsync` işaretlenen yöntemini çağırır. İçindeki yöntemi, <xref:System.Net.Http.HttpClient.GetStringAsync%2A?displayProperty=nameWithType> yöntemine yapılan çağrıları `await` beklemek için anahtar sözcüğünü kullanır. `GetPageLengthsAsync`  

[!code-csharp[await-example](../../../../samples/snippets/csharp/language-reference/keywords/await/await2.cs)]  

Yukarıdaki örnek, C# [ `async` `Main` yöntemini](../../programming-guide/main-and-command-args/index.md)destekleyen 7,1 kullanır. C# Önceki sürümler veya <xref:System.Threading.Tasks.Task> `async` `Main` `GetPageLengthsAsync` döndüren uygulama giriş noktalarını desteklemediğinden, değiştiricisini yönteme uygulayamaz ve yöntem çağrısını beklemezsiniz. <xref:System.Threading.Tasks.Task%601> Bu durumda, `Main` <xref:System.Threading.Tasks.Task%601.Result?displayProperty=nameWithType> özelliğinin değerini alarak yönteminin zaman uyumsuz işlemin tamamlanmasını beklediğini sağlayabilirsiniz. Değer döndürmeyen görevler için <xref:System.Threading.Tasks.Task.Wait%2A?displayProperty=nameWithType> yöntemini çağırabilirsiniz. Dil sürümünü seçme hakkında daha fazla bilgi için bkz. [ C# dil sürümünü seçme](../configure-language-version.md).

## <a name="see-also"></a>Ayrıca bkz.

- [Async ve Await ile Zaman Uyumsuz Programlama](../../programming-guide/concepts/async/index.md)
- [İzlenecek yol: Async ve await kullanarak Web 'e erişme](../../programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)
- [async](./async.md)
