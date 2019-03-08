---
title: Zaman uyumsuz derinlemesine
description: Nasıl miyim/O-bağlı ve CPU bağımlı zaman uyumsuz kod yazmayı basit kullanarak .NET görev tabanlı zaman uyumsuz model olduğunu öğrenin.
author: cartermp
ms.author: wiwagn
ms.date: 06/20/2016
ms.technology: dotnet-standard
ms.assetid: 1e38f9d9-8f84-46ee-a15f-199aec4f2e34
ms.openlocfilehash: 45dc8b72bd61fc9aa04c977a2dc67c37384697fc
ms.sourcegitcommit: 58fc0e6564a37fa1b9b1b140a637e864c4cf696e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/08/2019
ms.locfileid: "57677532"
---
# <a name="async-in-depth"></a>Zaman uyumsuz derinlemesine

G/ç ve CPU sınır yazma zaman uyumsuz kod basit .NET görev tabanlı zaman uyumsuz model kullanmaktır. Model tarafından sunulan `Task` ve `Task<T>` türleri ve `async` ve `await` C# ve Visual Basic anahtar sözcükleri. (Dile özgü kaynakları bulunur [Ayrıca bkz:](#see-also) bölümüne.) Bu makalede .NET zaman uyumsuz nasıl kullanıldığını açıklar ve perde kullanılan zaman uyumsuz framework hakkında Öngörüler sağlar.

## <a name="task-and-taskt"></a>Görev ve görev\<T >

Görevleridir olarak bilinen uygulamak için kullanılan yapıları [, Promise modeli eşzamanlılık](https://en.wikipedia.org/wiki/Futures_and_promises).  Kısacası, bunlar sonraki bir noktada, "iş promise" tamamlanacak promise temiz bir API ile birlikte olanak sağlar.

*   `Task` bir değer döndürmeyen tek bir işlemi temsil eder.
*   `Task<T>` türünde bir değer döndüren tek bir işlemi temsil eden `T`.

Zaman uyumsuz olarak gerçekleştirilecek iş özetlerini görevleri hakkında daha fazla neden önemlidir ve *değil* iş parçacığı üzerinde bir soyutlamadır. Varsayılan olarak, uygun işletim sistemi için geçerli iş parçacığı ve temsilci iş görevleri yürütün. İsteğe bağlı olarak, görevleri açıkça ayrı bir iş parçacığı üzerinde çalıştırılacak istenebilir `Task.Run` API.

Görevleri izleme, üzerinde bekleyen ve sonuç değeri erişmek için bir API Protokolü kullanıma sunma (durumunda `Task<T>`) bir görev. Dil Tümleştirmesi ile `await` anahtar sözcüğü, görevleri kullanarak için üst düzey bir Özet sağlar. 

Kullanarak `await` görev tamamlanana kadar denetim çağırana sonuçlanmıyor tarafından bir görev devam ederken yararlı işlerini yapmak için uygulama veya hizmet verir. Kodunuzun geri çağırmaları veya görev tamamlandıktan sonra yürütmeye devam etmeyi olayları dayalı gerekmez. Görev API tümleştirmesi ve dil, sizin için yapar. Kullanıyorsanız `Task<T>`, `await` anahtar sözcüğü ayrıca "sarmalamadan çıkarma" Görev tamamlandığında, döndürülen değer.  Bunun nasıl çalıştığını ayrıntıları, aşağıda daha ayrıntılı açıklanmıştır.

Görevler ve onlarla etkileşim kurmak için farklı yollar hakkında daha fazla bilgi [görev tabanlı zaman uyumsuz desen (TAP)](~/docs/standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md) konu.

## <a name="deeper-dive-into-tasks-for-an-io-bound-operation"></a>Ben/O-bağlama işlemi için görevlere daha yakından bakın

Aşağıdaki bölümde, bir normal zaman uyumsuz g/ç çağrısı ile neler sunduğu 10.000 feet görünüm tanımlar. Birkaç örnek ile başlayalım.

İlk örnek, bir zaman uyumsuz yöntemini çağırır ve, büyük olasılıkla henüz tamamlanmamış etkin bir görev döndürür.

```csharp
public Task<string> GetHtmlAsync()
{
    // Execution is synchronous here
    var client = new HttpClient();
    
    return client.GetStringAsync("https://www.dotnetfoundation.org");
}
```

İkinci örnek, kullanımını ekler `async` ve `await` görev üzerinde çalışmaya anahtar sözcükleri.

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

Çağrı `GetStringAsync()` çağrılar aracılığıyla bu kadar düşük düzeyli .NET kitaplıkları (belki başka bir zaman uyumsuz yöntem çağırmadan) ulaştığında bir P/Invoke birlikte çalışma çağrısına yerel ağ kitaplığı. Yerel Kitaplığı daha sonra sistem API çağrısını çağırabilir (gibi `write()` Linux üzerinde bir yuva için). Bir görev nesnesi, yerel ve yönetilen sınırında, büyük olasılıkla kullanarak oluşturulacak [TaskCompletionSource](xref:System.Threading.Tasks.TaskCompletionSource%601.SetResult(%600)). Görev nesnesi katmanından aktarılabilir, büyük olasılıkla üzerinde çalıştırılan veya doğrudan döndürülen, sonuçta ilk arayana döndürülür. 

Yukarıdaki ikinci örnekte bir `Task<T>` nesne öğesinden döndürüleceği `GetStringAsync`. Kullanımını `await` anahtar sözcüğü, yeni oluşturulan görev nesnesi döndürmek yöntemin neden olur. Denetim, bu konumdan çağırana döner `GetFirstCharactersCountAsync` yöntemi. Özellikleri ve yöntemleri [görev&lt;T&gt; ](xref:System.Threading.Tasks.Task%601) etkinleştir çağıranlar GetFirstCharactersCountAsync kalan kod yürütüldüğünde tamamlayacak görev, ilerleyişini izlemek için nesne.

Sistem API çağrısından sonra isteği artık çekirdek alanında ağ alt sistemini yolu işletim sisteminin yapıyor (gibi `/net` Linux Çekirdeği'nde).  Burada, işletim Sisteminin ağ isteği işleyecek *zaman uyumsuz olarak*.  Ayrıntılar kullanılan işletim sistemi bağlı olarak farklı olabilir (cihaz sürücüsü çağrı çalışma zamanı geri gönderilen sinyal olarak zamanlanmış olabilir veya bir cihaz sürücüsü arama yapılabilir ve *ardından* geri gönderilen sinyal), ancak çalışma zamanı sonunda bildirilir Ağ isteği devam ediyor.  Şu anda, aygıt sürücüsünün ya da zamanlanmış, devam eden veya zaten tamamlandı (istek zaten kullanıma "kablo üzerinden" dır) - ancak bu tüm gerçekleştiği zaman uyumsuz olarak olduğundan, aygıt sürücüsünü hemen başka bir şey işleyebildiğinden çalışır!

Örneğin, Windows işletim sistemi iş parçacığı ağ cihaz sürücüsü çağrıda ve ağ üzerinden bir kesme istek Paketi'ni (IRP) işlemi gerçekleştirmek için bu işlemi temsil eden ister.  Aygıt sürücüsü IRP alır, ağ çağrıda, IRP "bekliyor" olarak işaretler ve işletim sistemine geri döndürür.  İşletim sistemi iş parçacığı artık IRP "bekliyor" olduğunu bildiğinden, bu proje için yapmak için daha fazla bir iş içermiyorsa ve "geri bu diğer işlemleri gerçekleştirmesi için kullanılabilir, böylece döndürür".

İstek yerine veri aygıt sürücüsü geri gelir, yeni veri kesme alınan CPU bildirir.  Bu kesme nasıl ele, işletim sistemi bağlı olarak farklılık gösterir ancak sistem birlikte çalışma çağrısı ulaşana kadar sonunda veriler işletim sistemi geçirilir (örneğin, Linux'ta bir kesme işleyicisi altındaki işletim sistemi veri iletmek için IRQ yarısını zamanlar  zaman uyumsuz olarak).  Not Bu *ayrıca* zaman uyumsuz olarak olur!  Sonucu bir sonraki kullanılabilir iş parçacığı bulabildiği kadar kuyruğa alınır zaman uyumsuz yöntemin ve "Tamamlanan görevin sonucu kaydırma".

Tüm bu işlem boyunca bir güvenebileceğinizdir olan **iş parçacığının görevi çalıştırmak için adanmış**.  İş bazı bağlam içinde yürütülen rağmen (diğer bir deyişle, işletim sistemi veri iletmek için bir aygıt sürücüsü ve kesme için yanıt yok), için adanmış iş parçacığı yok *bekleyen* geri dönmeniz istek verileri.  Bu, sistemin bazı g/ç çağrısı tamamlanması bekleniyor yerine iş çok daha büyük bir birime işlemesini sağlar.

Yukarıdaki birçok iş duvar saati süresi bakımından ölçüldüğünde yapılması gibi görünse de, bu, gerçek g/ç işi yapmak için gereken süreyi için karşılaştırıldığında miniscule olur. Ancak hiç kesin olası zaman çizelgesi için böyle bir çağrı şuna benzer:

0-1————————————————————————————————————————————————–2-3

*   Harcanan süre noktalarından `0` için `1` kadar zaman uyumsuz bir yöntem denetimi onu arayan verir gereken her şey vardır.
*   Harcanan süre noktalarından `1` için `2` maliyet herhangi bir CPU ile g/ç üzerinde harcanan zamanı.
*   Son olarak, noktalarından harcanan süre `2` için `3` Denetim Arka (ve büyük olasılıkla bir değer) Bu noktada yürütme yaptığı yeniden zaman uyumsuz yönteme geçiyor.

### <a name="what-does-this-mean-for-a-server-scenario"></a>Bu sunucu senaryosu için anlamı nedir?

Bu model, iyi bir tipik sunucu senaryosu iş yükü ile çalışır.  Tamamlanmamış görevler üzerinde engelleme durumu adanmış iş parçacığı olduğundan sunucu işten web istekleri çok daha yüksek hacimde servis edebilirsiniz.

İki sunucu göz önünde bulundurun: zaman uyumsuz kodu çalıştırır ve desteklemez.  Bu örneğin amacı doğrultusunda, her sunucuyla yalnızca 5 iş parçacıkları isteklerine hizmet kullanılabilir vardır.  Bu numaraları imaginarily küçük ve yalnızca gösterim bir bağlamda hizmet unutmayın.

Her iki sunucuyu 6 eş zamanlı istekleri almak varsayılır. Her istek bir g/ç işlemi gerçekleştirir.  Sunucu *olmadan* 5 iş parçacıklarından miyim/O-bağlı iş tamamlandı ve yanıt yazılan kadar 6 isteği sıraya almak zaman uyumsuz kod vardır. Sıranın uzun alma nedeni 20 istek geldiğinde noktada aşağı yavaş sunucu başlayabilir.

Sunucu *ile* üzerinde çalıştırılan zaman uyumsuz kod hala 6 istek sıralarını ancak kullandığından `async` ve `await`, her iş parçacıklarını serbest yukarı miyim/O-işi başladığında yerine bittiğinde.  Gelen isteklerin çok daha küçük için zamanında 20 isteği, kuyrukta birlikte gelir. (hiçbir şey içinde hiç olup olmadığını), ve sunucu yavaşlamasına olmaz.

Bu contrived örnek olsa da, gerçek dünyadaki çok benzer bir biçimde çalışır.  Aslında, büyüklük kertesinde kullanarak daha fazla isteklerini işlemek bir sunucuya bekleyebileceğiniz `async` ve `await` her istek için bir iş parçacığı ayrılmış, aldığı daha.

### <a name="what-does-this-mean-for-client-scenario"></a>Bu istemci senaryo için anlamı nedir?

Kullanmak için en büyük kazanç `async` ve `await` yanıt hızını artış için bir istemci uygulamasıdır.  Uygulama yanıt iş parçacıkları tarafından el ile UNICODE yapabileceğiniz rağmen bir iş parçacığını üretme işlemi yalnızca kullanarak göre pahalı bir işlemdir `async` ve `await`.  Özellikle de benzer bir şey için bir mobil oyun, g/ç burada ilgilenmektedir UI iş parçacığı olabildiğince az etkileyerek çok önemlidir.

Ben/O-bağlı iş neredeyse hiçbir zaman CPU üzerinde harcadığı olduğundan daha da önemlisi, şekilleri faydalı bir iş gerçekleştirmek için bir tüm CPU iş parçacığı ayrılmış bir düşük kaynak kullanımını olacaktır.

Ayrıca, (örneğin, bir kullanıcı Arabirimi güncelleştirme) UI iş parçacığı için iş gönderme ile çok basit `async` yöntemleri ve ek iş (örneğin, bir iş parçacığı açısından güvenli temsilci çağırma) gerektirmez.

## <a name="deeper-dive-into-task-and-taskt-for-a-cpu-bound-operation"></a>Görev ve görev derinlemesine\<T > CPU bağımlı işlem için

CPU bağımlı `async` kodudur miyim/O-sınırdan biraz farklı `async` kod.  İş CPU üzerinde yapıldığından, hesaplama için bir iş parçacığı ayrılması etrafında erişmenin bir yolu yoktur.  Kullanımını `async` ve `await` arka plan ile etkileşim kurmak için temiz bir yol, iş parçacığı ve hızlı yanıt veren zaman uyumsuz yöntemi çağıran kişi tutmak sağlar.  Bu paylaşılan veriler için herhangi bir koruma sağlamaz unutmayın.  Paylaşılan veri kullanıyorsanız, uygun eşitleme stratejisi uygulamak gerekecektir.

CPU bağımlı zaman uyumsuz çağrı sunduğu 10.000 feet görünümü şu şekildedir:

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

`CalculateResult()` iş parçacığında çağrıldı yürütür.  Çağırdığında, `Task.Run`, pahalı CPU bağımlı işlem kuyruklar `DoExpensiveCalculation()`, iş parçacığı havuzundaki ve alan bir `Task<int>` tanıtıcı.  `DoExpensiveCalculation()` sonunda eşzamanlı olarak sonraki kullanılabilir iş parçacığı üzerinde başka bir CPU çekirdeği üzerinde büyük olasılıkla çalıştırılır.  Sırasında eş zamanlı iş gerçekleştirmek mümkündür `DoExpensiveCalculation()` başka bir iş parçacığı üzerinde meşgul olduğundan çağrılan iş parçacığı `CalculateResult()` hala yürütülüyor.

Bir kez `await` karşılaşılırsa, yürütülmesini `CalculateResult()` sırasında geçerli iş parçacığı ile yapılacak diğer işleri izin vererek arayanına üretilenleri kaydeder `DoExpensiveCalculation()` bir sonuç ayrıldığı.  Tamamlandıktan sonra sonuç ana iş parçacığı üzerinde çalıştırılacak sıraya alınır.  Sonuç olarak, ana iş parçacığı yürütülen döndüreceği `CalculateResult()`, sonucunu olması, bu noktada `DoExpensiveCalculation()`.

### <a name="why-does-async-help-here"></a>Neden zaman uyumsuz burada yardımcı oldu mu?

`async` ve `await` yanıt hızını gerektiğinde CPU bağımlı iş yönetimi için en iyi uygulamalardan biridir. Zaman uyumsuz CPU bağımlı iş ile kullanmak için birden çok desen vardır. Zaman uyumsuz kullanarak küçük bir maliyeti yoktur ve sıkı döngüler için önerilmez unutulmaması önemlidir.  Kodunuzda bu yeni özellikten nasıl yazdığınız belirlemek size aittir.

## <a name="see-also"></a>Ayrıca bkz.

- [C# zaman uyumsuz programlama](~/docs/csharp/async.md)
- [Zaman uyumsuz programlama ile async ve await (C#)](../csharp/programming-guide/concepts/async/index.md)
- [Zaman uyumsuz programlamaF#](~/docs/fsharp/tutorials/asynchronous-and-concurrent-programming/async.md)
- [Zaman uyumsuz programlama ile Async ve Await (Visual Basic)](~/docs/visual-basic/programming-guide/concepts/async/index.md)
