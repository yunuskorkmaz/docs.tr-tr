---
title: Zaman uyumsuz, derinlemesine
description: .NET görev tabanlı zaman uyumsuz model kullanarak g/ç 'ye bağlı ve CPU 'ya bağlı zaman uyumsuz kod yazma hakkında bilgi edinin.
author: cartermp
ms.author: wiwagn
ms.date: 06/20/2016
ms.technology: dotnet-standard
ms.assetid: 1e38f9d9-8f84-46ee-a15f-199aec4f2e34
ms.openlocfilehash: 91fd37ce329c03b43b5472e4579be7f5ef961738
ms.sourcegitcommit: 1b020356e421a9314dd525539da12463d980ce7a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/30/2019
ms.locfileid: "70169115"
---
# <a name="async-in-depth"></a>Zaman uyumsuz, derinlemesine

G/ç ve CPU 'ya bağlı zaman uyumsuz kod yazma, .NET görev tabanlı zaman uyumsuz model kullanılarak basittir. Model `Task` ve `Task<T>` türleri `async` C# ve ve anahtar`await` kelimeleri ve Visual Basic tarafından gösterilir. (Dile özgü kaynaklar [Ayrıca bkz](#see-also) . bölümünde bulunur.) Bu makalede, .NET Async 'in nasıl kullanılacağı açıklanmaktadır ve bu bilgiler, kapsamakta olan zaman uyumsuz Framework hakkında öngörüler sağlar.

## <a name="task-and-taskt"></a>Görev ve görev\<T >

Görevler, [taahhüt modelinin Promise modeli](https://en.wikipedia.org/wiki/Futures_and_promises)olarak bilinünü uygulamak için kullanılan yapılardır.  Kısa bir süre sonra, iş daha sonraki bir noktada tamamlanacak bir "Promise" sunar ve bu da bir temiz API ile Promise ile koordine etmenizi sağlar.

- `Task`değer döndürmeyen tek bir işlemi temsil eder.
- `Task<T>`türünde `T`bir değer döndüren tek bir işlemi temsil eder.

Görevler, iş parçacığı üzerinde bir soyutlama *değil* , zaman uyumsuz olarak gerçekleşen işin soyut kısımları olarak gerçekleşmekte önemlidir. Varsayılan olarak, görevler geçerli iş parçacığı üzerinde yürütülür ve uygun şekilde Işletim sisteminde iş devredebilir. İsteğe bağlı olarak, görevler `Task.Run` API aracılığıyla ayrı bir iş parçacığında çalışmak üzere açıkça istenebilir.

Görevler, izleme için bir API protokolünü açığa çıkarır, bir görevin sonuç değerine (Bu durumda `Task<T>`) ve bunlara erişmeyi bekler. `await` Anahtar sözcüğü ile dil tümleştirmesi, görevleri kullanmaya yönelik daha yüksek düzeyde bir soyutlama sağlar.

Kullanılarak `await` , görev tamamlanana kadar, bir görev çalışırken bir görev çalışırken, bir görev çalışırken, uygulama veya hizmetinizin yararlı çalışmalar gerçekleştirmesini sağlar. Görev tamamlandıktan sonra, bir yürütmeye devam etmek için kodunuzun geri çağırmaları veya olaylara dayalı olması gerekmez. Dil ve görev API 'SI tümleştirmesi sizin için bunu yapar. `Task<T>` Kullanıyorsanız`await` , anahtar sözcüğü görev tamamlandığında döndürülen değeri "sarmalama" olarak da döndürür.  Bunun nasıl çalıştığına ilişkin ayrıntılar aşağıda açıklanmaktadır.

Görevler hakkında daha fazla bilgi edinmek için [görev tabanlı zaman uyumsuz düzende (dokunarak)](./asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md) bunlarla etkileşimde bulunmak için farklı yollar bulabilirsiniz.

## <a name="deeper-dive-into-tasks-for-an-io-bound-operation"></a>G/ç ile bağlantılı bir Işlem için görevlere daha derin bakış

Aşağıdaki bölümde, tipik bir zaman uyumsuz g/ç çağrısıyla ne olacağı hakkında 10.000 Foot görünümü açıklanmaktadır. Birkaç örnek ile başlayalım.

İlk örnek, zaman uyumsuz bir yöntemi çağırır ve muhtemelen tamamlanmamış olan etkin bir görevi döndürüyor.

```csharp
public Task<string> GetHtmlAsync()
{
    // Execution is synchronous here
    var client = new HttpClient();

    return client.GetStringAsync("https://www.dotnetfoundation.org");
}
```

İkinci örnek, görev üzerinde çalışmak için `async` ve `await` anahtar sözcüklerinin kullanımını ekler.

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

Alt düzey .net `GetStringAsync()` kitaplıkları (Belki de diğer zaman uyumsuz yöntemleri çağırır) aracılığıyla çağrı yapılan çağrı, yerel bir ağ kitaplığına P/Invoke birlikte çalışabilirlik çağrısına erişene kadar. Yerel kitaplık daha sonra bir sistem API çağrısı (Linux üzerinde bir yuva gibi `write()` ) ile çağırabilir. Bir görev nesnesi, muhtemelen [TaskCompletionSource](xref:System.Threading.Tasks.TaskCompletionSource%601.SetResult(%600))kullanılarak yerel/yönetilen sınırında oluşturulur. Görev nesnesi, büyük olasılıkla üzerinde çalıştırılan veya doğrudan döndürülen, sonunda ilk çağırana döndürülen katmanlarla geçirilir.

Yukarıdaki ikinci örnekte, öğesinden `Task<T>` `GetStringAsync`bir nesne döndürülür. `await` Anahtar sözcüğünün kullanılması, yönteminin yeni oluşturulan bir görev nesnesi döndürmesini sağlar. Denetim, `GetFirstCharactersCountAsync` yöntemde bu konumdan çağırana döner. [Görev&lt;T&gt; ](xref:System.Threading.Tasks.Task%601) nesnesinin yöntemleri ve özellikleri, çağrı yapanların, getfirstkarakterscountasync içindeki geri kalan kod yürütüldüğünde tamamlanacak olan görevin ilerlemesini izlemelerine olanak tanır.

Sistem API çağrısından sonra, istek artık çekirdek alanında bulunur ve bu, işletim sisteminin ağ alt sistemine (Linux çekirdekte olduğu `/net` gibi) yol getirir.  Burada işletim sistemi ağ isteklerini *zaman uyumsuz*olarak işleyecek.  Ayrıntılar, kullanılan işletim sistemine bağlı olarak farklı olabilir (cihaz sürücüsü çağrısı çalışma zamanına geri gönderilen bir sinyal olarak zamanlanabilir veya bir cihaz sürücüsü çağrısı yapılabilir ve *sonra* bir sinyal geri gönderilir), ancak sonunda çalışma zamanı ağın istek devam ediyor.  Şu anda, cihaz sürücüsü için çalışma zamanlanmış, devam ediyor veya zaten bitmiş (istek zaten "kablo üzerinden") olur, ancak bu durum zaman uyumsuz olarak yapıldığından, cihaz sürücüsü başka bir şeyi hemen işleyebilir!

Örneğin, Windows 'da bir işletim sistemi iş parçacığı ağ aygıtı sürücüsüne bir çağrı yapar ve bunu işlemi temsil eden bir kesme Isteği paketi (IRP) aracılığıyla ağ işlemini gerçekleştirmesini ister.  Aygıt sürücüsü IRP 'yi alır, ağa çağrı yapar, IRP 'yi "bekliyor" olarak işaretler ve işletim sistemine geri döner.  İşletim sistemi iş parçacığı artık IRP 'nin "bekliyor" olduğunu bildiğinden, bu iş için daha fazla iş yapmaya sahip değildir ve diğer işleri gerçekleştirmek için kullanılabilmesi için "geri döndürür".

İstek yerine getirildiyse ve veriler cihaz sürücüsü aracılığıyla geri geldiğinde, bir kesme aracılığıyla alınan yeni verilerin CPU 'suna bildirir.  Bu kesmenin nasıl işlendiği, IŞLETIM sistemine bağlı olarak farklılık gösterir, ancak sonunda bir sistem birlikte çalışma çağrısına ulaşıncaya kadar veriler IŞLETIM sistemi üzerinden geçirilir (örneğin, Linux 'ta bir kesme işleyicisi, verileri işletim sistemi üzerinden iletmek için IRQ 'nun alt yarısını zamanlıyor  zaman uyumsuz).  Bunun *de* zaman uyumsuz olarak gerçekleştiğini unutmayın!  Sonuç, bir sonraki kullanılabilir iş parçacığı zaman uyumsuz yöntemini yürütebilene ve tamamlanmış görevin sonucunu "sarmadan" çıkana kadar sıraya alınır.

Bu işlemin tamamında, bir anahtar, **görevi çalıştırmak için hiçbir iş parçacığının ayrılmadığı**bir işlemdir.  Çalışma bazı bağlamda yürütülse de (yani işletim sisteminin bir cihaz sürücüsüne veri geçirmesi ve kesintiye yanıt vermesi gerekir), isteğin geri *dönmesi* için ayrılan iş parçacığı yok.  Bu, sistemin bazı g/ç çağrısının tamamlanmasını beklemek yerine çok daha büyük bir iş hacmi işlemesini sağlar.

Yukarıdaki çok fazla iş olması gibi görünse de, duvar saati zamanı bakımından ölçüldüğünde, bu, gerçek g/ç işinin yapılması için gereken süre ile karşılaştırıldığında minscc olur. Her türlü kesin olmasa da bu tür bir çağrının olası bir zaman çizelgesi şuna benzer:

0-1————————————————————————————————————————————————–2-3

- Zaman uyumsuz bir yöntem `0` , `1` çağıranına denetim yapana kadar her şey için noktadan geçen süre.
- `1` Noktadan`2` itibaren harcanan süre, CPU maliyeti olmadan g/ç 'de harcanan süredir.
- Son olarak, noktadan harcanan `2` `3` süre zaman uyumsuz metoda denetim geri (ve potansiyel bir değer) geçirmekte ve bu noktada yeniden yürütüyordur.

### <a name="what-does-this-mean-for-a-server-scenario"></a>Bu bir sunucu senaryosu için ne anlama geliyor?

Bu model tipik bir sunucu senaryosu iş yükü ile iyi şekilde çalışmaktadır.  Tamamlanmamış görevlerde engellemeye ayrılmış iş parçacığı olmadığından, sunucu ThreadPool çok daha yüksek bir Web istekleri hacmine hizmet edebilir.

İki sunucu düşünün: zaman uyumsuz kod çalıştıran bir ve olmayan bir.  Bu örneğin, her sunucuda yalnızca hizmet istekleri için kullanılabilir 5 iş parçacığı bulunur.  Bu sayıların imaginarily küçük olduğunu ve yalnızca bir gösterim amaçlıdır bağlamında işlev olduğunu unutmayın.

Her iki sunucunun da 6 eşzamanlı istek alacağını varsayın. Her istek bir g/ç işlemi gerçekleştirir.  Zaman uyumsuz kod *içermeyen* sunucu, 5 iş parçacığından biri g/ç ile bağlantılı çalışmayı tamamlayana ve yanıt yazana kadar 6. isteği sıraya almak zorunda değildir. 20. isteğin geldiği noktada, sıra çok uzun sürtiğinden sunucu yavaşlamaya başlayabilir.

Üzerinde çalışan zaman uyumsuz koda *sahip* sunucu yine 6. isteği sıraya alır, ancak kullandığından `async` `await`, iş parçacıklarının her biri bittiğinde değil g/ç bağlı iş başladığında serbest bırakılır.  20. isteğin geldiği zamana göre, gelen isteklerin kuyruğu çok daha küçüktür (herhangi bir şey varsa) ve sunucu yavaşmaz.

Bu bir contrived örneği olmasına rağmen gerçek dünyada çok benzer bir biçimde çalışmaktadır.  Aslında, bir sunucunun `async` , `await` aldığı her istek için bir iş parçacığını ayrılmış hale aldığına göre daha fazla istek sırasını işleyebilmesini sağlayabilirsiniz.

### <a name="what-does-this-mean-for-client-scenario"></a>Bu, istemci senaryosu için ne anlama geliyor?

İstemci uygulaması için ve `async` `await` kullanmanın en büyük kazancı, yanıt verme hızını artırır.  Bir uygulamayı iş parçacıklarını el ile oluşturarak yanıt verebilseniz de, iş parçacığı oluşturma işlemi, yalnızca `async` ve ile `await`ilgili pahalı bir işlemdir.  Özellikle bir mobil oyun gibi bir şey için, g/ç 'nin ilgili olduğu durumlarda Kullanıcı arabirimi iş parçacığını olabildiğince az etkilediğinde.

Daha da önemlisi, g/ç bağlı işi CPU üzerinde neredeyse zaman harcadığından, tüm CPU iş parçacığını çok iyi bir şekilde gerçekleştirmek için kullanılabilir olan tüm yararlı işler, kaynakların kötü bir şekilde kullanılmasını sağlar.

Ek olarak, Kullanıcı arabirimi iş parçacığına (Kullanıcı arabirimini güncelleştirme gibi) dağıtım çok basittir `async` ve ek iş gerektirmez (iş parçacığı güvenli temsilcisini çağırma gibi).

## <a name="deeper-dive-into-task-and-taskt-for-a-cpu-bound-operation"></a>CPU ile bağlantılı bir işlem için görev\<ve görev T > daha derin bakış

CPU-bağlantılı `async` kod, g/ç ile bağlantılı `async` koddan biraz farklıdır.  İş CPU üzerinde yapıldığından, bir iş parçacığını hesaplama altına almanın bir yolu yoktur.  `async` Ve`await` kullanımı, bir arka plan iş parçacığı ile etkileşime geçmek için temiz bir yol sağlar ve zaman uyumsuz yöntem çağıranı yanıt vermeye devam edecektir.  Bunun, paylaşılan veriler için herhangi bir koruma sağlamayacağını unutmayın.  Paylaşılan veriler kullanıyorsanız, yine de uygun bir eşitleme stratejisi uygulamanız gerekir.

CPU ile bağlantılı zaman uyumsuz çağrının 10.000 Foot görünümü aşağıda verilmiştir:

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

`CalculateResult()`üzerinde çağrıldığı iş parçacığı üzerinde yürütülür.  Çağırdığında `Task.Run`, iş parçacığı havuzunda pahalı CPU 'ya bağlı `DoExpensiveCalculation()`işlemi sıraya alır ve bir `Task<int>` tanıtıcı alır.  `DoExpensiveCalculation()`, büyük olasılıkla başka bir CPU çekirdeğinde, bir sonraki kullanılabilir iş parçacığında eşzamanlı olarak çalışır.  `DoExpensiveCalculation()` Çağıran`CalculateResult()` iş parçacığı çalışmaya devam ettiği için, başka bir iş parçacığında meşgul olduğu sürece eşzamanlı çalışma yapılabilir.

Bir `await` kez karşılaşılırsa, `CalculateResult()` yürütülmesi çağrı yapana geri gönderilir ve bu, bir sonucu ortaya tutarken `DoExpensiveCalculation()` geçerli iş parçacığı ile diğer çalışmanın yapılmasına izin verir.  İşlem tamamlandıktan sonra, sonuç ana iş parçacığında çalışacak şekilde sıralanır.  Sonuç olarak, ana iş parçacığı yürütmek `CalculateResult()`üzere döner ve bu noktada sonucunu elde edecektir. `DoExpensiveCalculation()`

### <a name="why-does-async-help-here"></a>Zaman uyumsuz yardım neden burada?

`async`ve `await` yanıt verme gerektiğinde CPU ile bağlantılı çalışmanın yönetilmesi için en iyi uygulamadır. CPU ile bağlantılı çalışmalarla zaman uyumsuz olarak kullanılması için birden çok desen vardır. Zaman uyumsuz kullanmanın küçük bir maliyeti olduğunu ve sıkı döngüler için önerilmediğini aklınızda bulundurmamak önemlidir.  Kodunuzu bu yeni özellik etrafında nasıl yazacağınızı belirlemektir.

## <a name="see-also"></a>Ayrıca bkz.

- [İçinde zaman uyumsuz programlamaC#](../csharp/async.md)
- [Async ve await (C#) ile zaman uyumsuz programlama](../csharp/programming-guide/concepts/async/index.md)
- [İçinde zaman uyumsuz programlamaF#](../fsharp/tutorials/asynchronous-and-concurrent-programming/async.md)
- [Async ve await ile zaman uyumsuz programlama (Visual Basic)](../visual-basic/programming-guide/concepts/async/index.md)
