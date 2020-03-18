---
title: Derinlemesine Async
description: .NET Görev tabanlı async modelini kullanarak I/O-bound ve CPU'ya bağlı asynchronous kodunu yazmanın nasıl basit olduğunu öğrenin.
author: cartermp
ms.author: wiwagn
ms.date: 06/20/2016
ms.technology: dotnet-standard
ms.assetid: 1e38f9d9-8f84-46ee-a15f-199aec4f2e34
ms.openlocfilehash: 91fd37ce329c03b43b5472e4579be7f5ef961738
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "70169115"
---
# <a name="async-in-depth"></a>Derinlemesine Async

.NET Görev tabanlı async modeli kullanılarak G/Ç ve CPU'ya bağlı asynchronous kodu yazmak kolaydır. Model, C# `Task` ve `Task<T>` Visual `async` Basic'teki `await` tipler ve anahtar kelimeler tarafından ortaya atılır. (Dile özel kaynaklar [Bak](#see-also) bölümünde bulunur.) Bu makalede, .NET async'in nasıl kullanılacağı açıklanmaktadır ve kapakların altında kullanılan async çerçevesihakkında bilgi sağlar.

## <a name="task-and-taskt"></a>Görev ve\<Görev T>

Görevler, Eşzamanlılık Vaadi Modeli olarak bilinen şeyi uygulamak için kullanılan [yapılardır.](https://en.wikipedia.org/wiki/Futures_and_promises)  Kısacası, size işlerin daha sonraki bir noktada tamamlanacağını ve temiz bir API ile sözle koordine olmanızı sağlayacak bir "söz" sunarlar.

- `Task`bir değer döndürmeyen tek bir işlemi temsil eder.
- `Task<T>`türünde `T`bir değer döndüren tek bir işlemi temsil eder.

İş parçacığı üzerinde bir soyutlama *değil,* eşzamanlı olarak gerçekleşen iş soyutlamaları olarak görevleri hakkında neden önemlidir. Varsayılan olarak, görevler geçerli iş parçacığı üzerinde yürütülür ve uygun olduğu şekilde İşletim Sistemi'ne yetkiveda çalışır. İsteğe bağlı olarak, görevlerin `Task.Run` API üzerinden ayrı bir iş parçacığı üzerinde çalışması açıkça istenebilir.

Görevler, bir görevin sonuç değerini izlemek, beklemek ve erişim için `Task<T>`bir API protokolünü ortaya çıkarır. Anahtar kelimeyle `await` birlikte dil tümleştirmesi, görevleri kullanmak için daha üst düzey bir soyutlama sağlar.

Bir `await` görev, görev tamamlanına kadar arayana denetim vererek çalışırken uygulamanızın veya hizmetin yararlı işler gerçekleştirmesine olanak tanır. Görev tamamlandıktan sonra yürütmeye devam etmek için kodunuzun geri aramalara veya olaylara dayanması gerekmez. Dil ve görev API tümleştirmesi bunu sizin için yapar. `Task<T>`Kullanıyorsanız, `await` anahtar kelime ayrıca Görev tamamlandığında döndürülen değeri "açar".  Bu çalışmaların ayrıntıları aşağıda daha ayrıntılı olarak açıklanmıştır.

[Görev tabanlı Eşzamanlı Desen (TAP)](./asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md) konusunda görevler ve bunlarla etkileşim kurmanın farklı yolları hakkında daha fazla bilgi edinebilirsiniz.

## <a name="deeper-dive-into-tasks-for-an-io-bound-operation"></a>G/Ç'ye Bağlı İşlem için Görevlere Daha Derin Dalış

Aşağıdaki bölümde, tipik bir async G/Ç aramasıyla ne olduğu 10.000 metrelik bir görünüm açıklanmaktadır. Birkaç örnekle başlayalım.

İlk örnek bir async yöntemi çağırır ve büyük olasılıkla henüz tamamlanması için etkin bir görev döndürür.

```csharp
public Task<string> GetHtmlAsync()
{
    // Execution is synchronous here
    var client = new HttpClient();

    return client.GetStringAsync("https://www.dotnetfoundation.org");
}
```

İkinci örnek, görevde çalışmak `async` `await` için anahtar kelimelerin ve anahtar kelimelerin kullanımını ekler.

```csharp
public async Task<string> GetFirstCharactersCountAsync(string url, int count)
{
    // Execution is synchronous here
    var client = new HttpClient();

    // Execution of GetFirstCharactersCountAsync() is yielded to the caller here
    // GetStringAsync returns a Task<string>, which is *awaited*
    var page = await client.GetStringAsync("https://www.dotnetfoundation.org");

    // Execution resumes when the client.GetStringAsync task completes,
    // becoming synchronous again.

    if (count > page.Length)
    {
        return page;
    }
    else
    {
        return page.Substring(0, count);
    }
}
```

Yerel ağ `GetStringAsync()` kitaplığına Bir P/Invoke interop çağrısına ulaşana kadar alt düzey .NET kitaplıkları (belki de diğer async yöntemlerini çağıran) aracılığıyla yapılan aramalara çağrı. Yerel kitaplık daha sonra bir Sistem API `write()` çağrısına (Linux'taki bir soket gibi) çağrıyapabilir. Görev [Tamamlama Kaynağı](xref:System.Threading.Tasks.TaskCompletionSource%601.SetResult(%600))kullanılarak yerel/yönetilen sınırda bir görev nesnesi oluşturulur. Görev nesnesi katmanlar aracılığıyla geçirilir, muhtemelen çalıştırılır veya doğrudan döndürülür, sonunda ilk arayana döndürülür.

Yukarıdaki ikinci örnekte, `Task<T>` bir nesne `GetStringAsync`.'den döndürülür. `await` Anahtar kelimenin kullanımı yöntemin yeni oluşturulan görev nesnesini döndürmesine neden olur. Denetim `GetFirstCharactersCountAsync` yöntemde bu konumdan arayana döner. [Görev&lt;T&gt; ](xref:System.Threading.Tasks.Task%601) nesnesinin yöntemleri ve özellikleri, arayanların GetFirstCharactersCountAsync'de kalan kod yürütüldüğünde tamamlanacak olan görevin ilerlemesini izlemesini sağlar.

Sistem API çağrısından sonra, istek artık çekirdek alanında dır ve işletim sisteminin ağ alt sistemine `/net` (Linux Çekirdeği'nde olduğu gibi) doğru yola çıkar.  Burada işletim sistemi ağ isteğini *eşit bir şekilde*işleyecek.  Ayrıntılar kullanılan işletim sistemi bağlı olarak farklı olabilir (aygıt sürücüsü arama sı çalıştırılmak için geri gönderilen bir sinyal olarak zamanlanabilir veya bir aygıt sürücüsü araması yapılabilir ve *daha sonra* bir sinyal geri gönderilebilir), ancak sonunda çalışma süresi ağ isteği devam ettiği bildirilir.  Şu anda, aygıt sürücüsü için çalışma ya zamanlanmış olacak, devam ediyor, ya da zaten bitmiş (istek zaten "tel üzerinde" dışarı) - ama bu tüm eşzamanlı oluyor çünkü, cihaz sürücüsü hemen başka bir şey işlemek mümkün!

Örneğin, Windows'da bir işletim sistemi iş parçacığı ağ aygıtı sürücüsüne bir çağrı yapar ve işlemi temsil eden bir Kesme İstek Paketi (IRP) aracılığıyla ağ işlemini gerçekleştirmesini ister.  Aygıt sürücüsü IRP alır, ağa arama yapar, IRP'yi "beklemede" olarak işaretler ve işletim sistemi'ne geri döner.  İşletim sistemi iş parçacığı artık IRP'nin "beklemede" olduğunu bildiğinden, bu iş için yapacak daha fazla işi yoktur ve diğer işleri gerçekleştirmek için kullanılabilmesi için "geri döner".

İstek yerine getirildiğinde ve veriler aygıt sürücüsünden geri geldiğinde, bir kesinti yle alınan yeni verilerin CPU'ya haber verirken.  Bu kesintinin nasıl işleneceğini os bağlı olarak değişir, ancak sonunda veri bir sistem interop çağrı ulaşana kadar işletim sistemi üzerinden geçirilecektir (örneğin, Linux'ta bir kesme işleyicisi işletim sistemi üzerinden veri geçmek için IRQ alt yarısını zamanlar asynchronously).  Bu *da* eşzamanlı olur unutmayın!  Bir sonraki kullanılabilir iş parçacığı async yöntemini yürütmek ve tamamlanan görevin sonucunu "açmak" mümkün olana kadar sonuç sıraya alınır.

Tüm bu işlem boyunca, önemli bir paket **hiçbir iş parçacığı görevi çalıştırmak için adamıştır.**  Çalışma bazı bağlamlarda yürütülse de (diğer bir deyişle, işletim sistemi verileri aygıt sürücüsüne aktarmak ve kesintiye yanıt vermek zorunda), istekten gelen verilerin geri gelmesini *beklemeye* adanmış bir iş parçacığı yoktur.  Bu, sistemin bazı G/Ç aramalarının tamamlanmasını beklemek yerine çok daha büyük bir iş hacmini işlemesini sağlar.

Yukarıdaki yapılacak bir çok iş gibi görünse de, duvar saati süresi açısından ölçüldüğünde, gerçek G / O iş yapmak için gereken süre ile karşılaştırıldığında küçük. Tüm kesin olmasa da, böyle bir arama için potansiyel bir zaman çizelgesi şu şekilde görünür:

0-1————————————————————————————————————————————————–2-3

- Puanlardan `0` async `1` yöntemi arayana denetim verene kadar harcanan zaman her şeydir.
- Puanlardan `1` G/Ç'ye `2` harcanan süre, CPU maliyeti olmadan I/Ç'de harcanan süredir.
- Son olarak, `2` puanlardan `3` harcanan zaman denetimi async yöntemine geri (ve potansiyel olarak bir değer) geçiriyor ve bu noktada yeniden yürütülmeye başlıyor.

### <a name="what-does-this-mean-for-a-server-scenario"></a>Bu, sunucu senaryosu için ne anlama gelir?

Bu model, tipik bir sunucu senaryosu iş yükü ile iyi çalışır.  Tamamlanmamış görevlerde engellemeye adanmış iş parçacıkları olmadığından, sunucu iş parçacığı havuzu çok daha yüksek hacimli web isteklerine hizmet verebilir.

İki sunucu düşünün: biri async kodu çalıştıran, diğeri çalıştırmayan.  Bu örnek için, her sunucunun hizmet istekleri için yalnızca 5 iş parçacığı vardır.  Bu sayıların hayali olarak küçük olduğunu ve yalnızca gösterici bir bağlamda hizmet verdiğini unutmayın.

Her iki sunucunun da 6 eşzamanlı istek aldığını varsayalım. Her istek bir G/Ç işlemi gerçekleştirir.  Async kodu *olmayan* sunucu, 5 iş parçacığından biri G/Ç'ye bağlı çalışmayı bitirip yanıt yazana kadar 6. 20. istek geldiği noktada, sıra çok uzun sürdüğü için sunucu yavaşlamaya başlayabilir.

Üzerinde async kodu *çalışan* sunucu hala 6 istek sıraya, ancak `async` kullandığı `await`için ve , her iş parçacığı, I / O-bound çalışma başladığında, yerine ne zaman bitirir serbest bırakılır.  20. istek gelene kadar, gelen istekler için kuyruk çok daha küçük olacaktır (içinde herhangi bir şey varsa) ve sunucu yavaşlamaz.

Bu contrived bir örnek olmasına rağmen, gerçek dünyada çok benzer bir şekilde çalışır.  Aslında, bir sunucunun aldığı her istek için bir iş `async` parçacığı `await` ayırıyorsa, daha fazla istek kullanarak ve daha büyük bir istek siparişi işlemek mümkün olmasını bekleyebilirsiniz.

### <a name="what-does-this-mean-for-client-scenario"></a>Bu istemci senaryosu için ne anlama geliyor?

Bir istemci uygulamasını `async` `await` kullanmak ve kullanmak için en büyük kazanç yanıt verme deki artıştır.  Bir uygulamayı iş parçacıklarını el ile yumurtlayarak yanıt vermeye zorlasanız da, bir `async` `await`iş parçacığı nın yumurtlama eylemi, sadece kullanmaya ve .  Özellikle mobil bir oyun gibi bir şey için, I / O söz konusu olduğunda mümkün olduğunca az UI iplik etkileyen çok önemlidir.

Daha da önemlisi, I / O bağlı çalışma CPU üzerinde hemen hemen hiç zaman harcamak, ancak herhangi bir yararlı iş gerçekleştirmek için tüm bir CPU iş parçacığı adamak kaynakların kötü kullanımı olacaktır.

Ayrıca, kullanıcı arabirimi iş parçacığına iş gönderme (kullanıcı arabirimi güncelleştirme `async` gibi) yöntemlerle çok basittir ve ek çalışma gerektirmez (iş parçacığı için güvenli bir temsilci çağırmak gibi).

## <a name="deeper-dive-into-task-and-taskt-for-a-cpu-bound-operation"></a>CPU'ya Bağlı Bir\<İşlem için Görev ve Görev T> Daha Derin dalış

CPU'ya `async` bağlı kod, G/Ç'ye `async` bağlı koddan biraz farklıdır.  İşlem üzerinde iş yapıldığından, bir iş parçacığının hesaplamaya ithaf edilmesinin bir yolu yoktur.  Kullanımı `async` ve `await` bir arka plan iş parçacığı ile etkileşim ve async yönteminin arayan duyarlı tutmak için temiz bir yol sağlar.  Bunun paylaşılan veriler için herhangi bir koruma sağlamadığını unutmayın.  Paylaşılan verileri kullanıyorsanız, yine de uygun bir eşitleme stratejisi uygulamanız gerekir.

Burada bir CPU bağlı async arama 10.000 ayak görünümü:

```csharp
public async Task<int> CalculateResult(InputData data)
{
    // This queues up the work on the threadpool.
    var expensiveResultTask = Task.Run(() => DoExpensiveCalculation(data));

    // Note that at this point, you can do some other work concurrently,
    // as CalculateResult() is still executing!

    // Execution of CalculateResult is yielded here!
    var result = await expensiveResultTask;

    return result;
}
```

`CalculateResult()`çağrıldığı iş parçacığı üzerinde yürütür.  `Task.Run`Aradığında, iş parçacığı havuzunda pahalı CPU'ya bağlı işlemi `DoExpensiveCalculation()`sıralar ve bir `Task<int>` tutamaç alır.  `DoExpensiveCalculation()`sonunda aynı anda bir sonraki kullanılabilir iş parçacığı, büyük olasılıkla başka bir CPU çekirdek üzerinde çalıştırılır.  Başka bir iş parçacığı üzerinde `DoExpensiveCalculation()` meşgul ken eşzamanlı iş yapmak mümkündür, çünkü adlandırılan `CalculateResult()` iş parçacığı hala yürütülmeye devam ediyor.

Bir `await` kez karşılaşılan, `CalculateResult()` yürütme arayan teslim edilir, başka bir iş bir sonuç `DoExpensiveCalculation()` çalkalama ise geçerli iş parçacığı ile yapılmasını sağlar.  Tamamlandıktan sonra, sonuç ana iş parçacığı üzerinde çalıştırmak için sıraya alınır.  Sonunda, ana iş parçacığı yürütme `CalculateResult()`dönecektir , hangi noktada sonucu `DoExpensiveCalculation()`olacaktır .

### <a name="why-does-async-help-here"></a>Async neden burada yardımcı olur?

`async`ve `await` yanıt verme gereksinimi olduğunda CPU'ya bağlı çalışmayı yönetmek için en iyi yöntemdir. CPU'ya bağlı çalışma ile async kullanmak için birden çok desen vardır. Bu async kullanarak küçük bir maliyet olduğunu ve sıkı döngüler için tavsiye edilmez dikkat etmek önemlidir.  Bu yeni özellik etrafında kodunuzu nasıl yazdığınızı belirlemek size kalmış.

## <a name="see-also"></a>Ayrıca bkz.

- [C'de asynchronous programlama #](../csharp/async.md)
- [Async ve await ile asynchronous programlama (C#)](../csharp/programming-guide/concepts/async/index.md)
- [F'de Async Programlama #](../fsharp/tutorials/asynchronous-and-concurrent-programming/async.md)
- [Async ve Await ile Asynchronous Programlama (Visual Basic)](../visual-basic/programming-guide/concepts/async/index.md)
