---
title: Zaman uyumsuz derinlemesine
description: Ne zaman uyumsuz g/Ç-bağlı ve CPU bağımlı kod yazma basit .NET görev tabanlı zaman uyumsuz modelini kullanarak olduğunu öğrenin.
author: cartermp
ms.author: wiwagn
ms.date: 06/20/2016
ms.technology: dotnet-standard
ms.assetid: 1e38f9d9-8f84-46ee-a15f-199aec4f2e34
ms.openlocfilehash: fbee7e6ad0fad312e9e5524f7b3fcc7c417ad47b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33577433"
---
# <a name="async-in-depth"></a>Zaman uyumsuz derinlemesine

G/ç ve CPU sınır yazmayı zaman uyumsuz basit .NET görev tabanlı zaman uyumsuz modelini kullanarak kodudur. Model tarafından sunulan `Task` ve `Task<T>` türleri ve `async` ve `await` C# ve Visual Basic anahtar sözcükleri. (Dile özgü kaynaklar içinde bulunan [Ayrıca bkz.](#see-also) bölümüne.) Bu makalede .NET zaman uyumsuz kullanılmasını açıklar ve perde arkasında kullanılan zaman uyumsuz framework bir anlayış sağlar.

## <a name="task-and-tasklttgt"></a>Görev ve görev&lt;T&gt;

Görevlerdir olarak bilinen uygulamak için kullanılan yapılar [, Promise modeli eşzamanlılık](https://en.wikipedia.org/wiki/Futures_and_promises).  Kısacası, bunlar sonraki bir noktada, "iş promise" tamamlanacak promise temiz bir API ile birlikte koordine imkan sağlar.

*   `Task` bir değer döndürmüyor tek bir işlemde temsil eder.
*   `Task<T>` türünde bir değer döndüren tek bir işlemi temsil eden `T`.

Zaman uyumsuz olarak gerçekleştiği iş soyutlamalar görevler hakkında neden önemlidir ve *değil* iş parçacığı üzerinde bir Özet. Varsayılan olarak, işletim sistemine uygun şekilde geçerli iş parçacığı ve temsilci iş görevleri yürütün. İsteğe bağlı olarak, görevleri açıkça ayrı bir iş parçacığı çalıştırmayı istenebilir `Task.Run` API.

Görevleri izleme, üzerinde bekleyen ve sonuç değeri erişmek için bir API Protokolü kullanıma (durumunda `Task<T>`) bir görev. Dil Tümleştirmesi ile `await` anahtar sözcüğü, görevler kullanma için üst düzey bir Özet sağlar. 

Kullanarak `await` görev yapılana kadar denetim çağırıcısına sağlayan tarafından bir görev çalışırken yararlı işlerini yapmak için uygulama veya hizmet sağlar. Geri aramalar veya görevi tamamlandıktan sonra yürütmeye devam etmek için olayları yararlanmayı kodunuzu gerekmez. Dili ve görev API tümleştirme yapar, sizin için. Kullanıyorsanız, `Task<T>`, `await` anahtar sözcüğü ayrıca "kaydırma" Görev tamamlandığında, döndürülen değer.  Bunun nasıl çalıştığı ayrıntılarını daha aşağıda açıklanmıştır.

Görevleri ve onlarla etkileşime farklı yolları hakkında daha fazla bilgiyi [görev tabanlı zaman uyumsuz desen (TAP)](~/docs/standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md) konu.

## <a name="deeper-dive-into-tasks-for-an-io-bound-operation"></a>Bir g/Ç-bağlama işlemi için görevler halinde daha derin Dalış

Aşağıdaki bölümde tipik zaman uyumsuz g/ç çağrısı ile neler 10.000 kaplama alanı görünümü açıklanmaktadır. Birkaç örnek ile başlayalım.

İlk örnek bir zaman uyumsuz yöntemini çağırır ve, henüz tamamlamak büyük olasılıkla etkin bir görev döndürür.

```csharp
public Task<string> GetHtmlAsync()
{
    // Execution is synchronous here
    var client = new HttpClient();
    
    return client.GetStringAsync("http://www.dotnetfoundation.org");
}
```

İkinci örnek kullanımını ekler `async` ve `await` görev üzerinde çalışması için anahtar sözcükler.

```csharp
public async Task<string> GetFirstCharactersCountAsync(string url, int count)
{
    // Execution is synchronous here
    var client = new HttpClient();
    
    // Execution of GetFirstCharactersCountAsync() is yielded to the caller here
    // GetStringAsync returns a Task<string>, which is *awaited*
    var page = await client.GetStringAsync("http://www.dotnetfoundation.org");
    
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

Çağrı `GetStringAsync()` çağrıları bu kadar düşük düzeyli .NET kitaplıkları (belki de diğer zaman uyumsuz yöntemleri çağırma) üzerinden ulaştığında bir yerel ağ kitaplığındaki bir P/Invoke birlikte çalışabilirlik çağrısı. Yerel Kitaplığı daha sonra sistem API çağrısını çağırabilir (gibi `write()` Linux üzerinde bir yuva için). Yerel ve yönetilen sınırında, büyük olasılıkla kullanarak bir görev nesnesi oluşturulacak [TaskCompletionSource](xref:System.Threading.Tasks.TaskCompletionSource%601.SetResult(%600)). Görev nesnesi olması katmanları aktarılabilir, büyük olasılıkla üzerinde çalıştırılan veya doğrudan döndürülen, sonunda ilk yapana. 

İkinci yukarıdaki örnekte, bir `Task<T>` nesnesi, gelen döndürülecek `GetStringAsync`. Kullanımını `await` anahtar sözcüğü bir yeni oluşturulan görev nesnesi döndürmek yöntemin neden olur. Denetim bu konumda bulunan çağırana döndürür `GetFirstCharactersCountAsync` yöntemi. Özellikleri ve yöntemleri [görev&lt;T&gt; ](xref:System.Threading.Tasks.Task%601) etkinleştir arayanlar GetFirstCharactersCountAsync kalan kodda çalıştırıldığında tamamlayacak görev ilerlemesini izlemek için nesne.

Sistem API çağrısı sonra isteği şimdi çekirdek alanında ağ alt sisteminin yolu işletim sisteminin yapıyor (gibi `/net` Linux Çekirdeği'nde).  İşletim sistemi ağ isteği burada işleyecek *zaman uyumsuz olarak*.  Ayrıntılar kullanılan işletim sistemi bağlı olarak farklı olabilir (aygıt sürücüsü araması çalışma zamanına gönderilen sinyal olarak zamanlanmış olabilir veya bir aygıt sürücüsü çağrı yapılır ve *sonra* geri gönderilen sinyal), ancak çalışma zamanı sonunda bildirilir Ağ isteği devam ediyor.  Şu anda aygıt sürücüsü için iş ya da zamanlanan, devam eden veya zaten tamamlandı (istek çıkışı "kablo üzerinden" zaten) - ancak bu tüm gerçekleştiği zaman uyumsuz olarak olduğundan, aygıt sürücüsünü hemen başka bir şey kaldırabilir mi olur!

Örneğin, Windows işletim Sisteminin iş parçacığı ağ aygıt sürücüsü için bir çağrı yapar ve ağ üzerinden bir kesme istek Paketi'ni (IRP) işlemi gerçekleştirmek için bu işlemi temsil eden ister.  Aygıt sürücüsü IRP alır, ağa çağrı yapar, IRP "bekliyor" olarak işaretler ve işletim sistemi geri döndürür.  IRP "bekliyor" işletim sistemi iş parçacığı şimdi bildiği için bu proje için yapmak için daha fazla iş yok ve "geri diğer işlemleri gerçekleştirmesi için kullanılabilmesi için böylece döndürür".

İstek yerine getirilir ve veriler geri aygıt sürücüsü aracılığıyla gelir, bir kesme alınan yeni verileri CPU size bildirir.  Bu kesme nasıl ele, işletim sistemi bağlı olarak farklılık gösterir, ancak sistem birlikte çalışabilirlik çağrısı ulaşana kadar sonunda veri işletim sistemi geçirilecektir (örneğin, Linux bir kesme işleyicisi altındaki işletim sistemi veri iletmek için IRQ yarısı zamanlar  zaman uyumsuz olarak).  Not Bu *de* zaman uyumsuz olarak olur!  Sonuç sonraki kullanılabilir iş parçacığının mümkün olduğu kadar sıraya async yöntemi yürütebilir ve "Tamamlanan görevin sonucu kaydırma".

Tüm bu işlem boyunca, bir anahtar takeaway olan **hiçbir iş parçacığı görevi çalıştırmak için adanmış**.  İş bazı içerik içinde yürütülmesi rağmen (diğer bir deyişle, işletim sistemi bir aygıt sürücüsü veri iletmek için bir kesme yanıt mevcut ve), için adanmış iş parçacığı yok *bekleyen* geri dönmeniz istekten alınan veriler için.  Bu sistemin bazı g/ç arama tamamlanması bekleniyor yerine iş çok daha büyük bir birim işlemesini sağlar.

Yukarıdaki çok uzun duvar saati süresi cinsinden ölçülen yapılması çalışmanın gibi görünse de, bu, gerçek g/ç işlerini gerçekleştirmek için gereken süreyi karşılaştırıldığında miniscule olur. Ancak hiç kesin böyle bir çağrı için olası bir zaman çizelgesi şuna benzer:

0-1————————————————————————————————————————————————–2-3

*   Harcanan zaman noktalarından `0` için `1` bir zaman uyumsuz yöntem çağırıcısına denetim verir kadar gereken her şey vardır.
*   Harcanan zaman noktalarından `1` için `2` maliyet hiçbir CPU ile g/ç üzerinde harcanan zamanı.
*   Son olarak, noktalarından harcanan zamanı `2` için `3` Denetim Arka (ve büyük olasılıkla bir değer), bu noktada, Yürütülüyor yeniden async yöntemi için geçirme.

### <a name="what-does-this-mean-for-a-server-scenario"></a>Bunun için sunucu senaryosu anlamı nedir?

Bu model, iyi bir tipik sunucu senaryosu iş yükü ile çalışır.  Tamamlanmamış görevler üzerinde engellemek üzere adanmış iş parçacığı olduğundan sunucu threadpool'u bir çok daha yüksek hacmi web istekleri servis edebilirsiniz.

İki sunucu göz önünde bulundurun: zaman uyumsuz kodu çalıştırır ve desteklemez.  Bu örneğin amacı doğrultusunda, her sunucu yalnızca hizmet istekleri için kullanılabilir 5 iş parçacığı yok.  Bu sayı imaginarily küçük ve yalnızca demonstrative bağlamında hizmet unutmayın.

Her iki sunucuyu 6 eş zamanlı istekleri almak varsayalım. Her istek bir g/ç işlemi gerçekleştirir.  Sunucu *olmadan* zaman uyumsuz koduna sahip 5 iş parçacığı bir g/Ç-bağlı iş tamamlandı ve yanıt yazılmış kadar 6 isteğini Sıraya alınacak. Sıranın uzun elde etmektir çünkü 20 istek geldiğinde noktada, aşağı, yavaş sunucu başlayabilir.

Sunucu *ile* üzerinde çalışan zaman uyumsuz kodu hala 6 isteği sıralarını ancak kullandığından `async` ve `await`, her iş parçacıklarını serbest yukarı g/Ç-bağlı iş başlatıldığında yerine bittiğinde.  Gelen istekleri kadar küçük olacaktır zamanına göre 20 isteği sırada birlikte gelir. (Bu her şeyi hiç olup olmadığını), ve sunucu yavaşlaması olmaz.

Bu contrived örnek olsa da, gerçek dünyadaki çok benzer bir şekilde çalışır.  Aslında, büyüklük kertesinde kullanarak daha fazla isteklerini işlemek için bir sunucu bekleyebilirsiniz `async` ve `await` her istek için bir iş parçacığı ayrılması, alan daha.

### <a name="what-does-this-mean-for-client-scenario"></a>Bu ne istemci senaryo için anlama geliyor?

Kullanmak için en büyük kazanç `async` ve `await` bir istemci için uygulama yanıt hızını artış olur.  Bir uygulama yanıt iş parçacığı oluşturma tarafından el ile yapabileceğiniz bir iş parçacığını oluşturma işlemi yalnızca kullanarak göre pahalı bir işlem olsa da `async` ve `await`.  Özellikle bir şey için taşınabilir oyun gibi burada g/ç kaygı kullanıcı Arabirimi iş parçacığı mümkün olduğunca az etkileyen çok önemlidir.

G/Ç-bağlı iş neredeyse hiçbir zaman CPU üzerinde harcadığı olduğundan daha da önemlisi, neredeyse hiç herhangi bir yararlı çalışmayı gerçekleştirmek için bir tüm CPU iş parçacığı ayrılması kötü bir kaynak kullanımını olacaktır.

Ayrıca, (örneğin, bir kullanıcı Arabirimi güncelleştirme) kullanıcı Arabirimi iş parçacığı için iş gönderme ile çok basit olup `async` yöntemleri ve (örneğin, bir iş parçacığı temsilci çağırma) ek iş gerektirmez.

## <a name="deeper-dive-into-task-and-taskt-for-a-cpu-bound-operation"></a>Derin Dalış görev ve görev<T> CPU bağımlı işlemi

CPU bağımlı `async` kodu g/Ç-sınırdan biraz farklıdır `async` kodu.  İş CPU'da yapıldığından, hesaplama için bir iş parçacığı ayrılması geçici almak için yolu yoktur.  Kullanımını `async` ve `await` bir arka plan ile etkileşim kurmak için temiz bir şekilde sizinle iş parçacığı ve zaman uyumsuz yöntem arayan yanıt verebilir durumda tutun sağlar.  Bu paylaşılan veriler için herhangi bir koruma sağlamaz unutmayın.  Paylaşılan veri kullanıyorsanız, uygun eşitleme stratejisi uygulamak gerekecektir.

CPU bağımlı zaman uyumsuz çağrı 10.000 kaplama alanı görünümünü şöyledir:

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

`CalculateResult()` çağrıldı iş parçacığı üzerinde yürütür.  Bunu çağırdığında `Task.Run`, pahalı CPU bağımlı işlemi kuyruklar `DoExpensiveCalculation()`, iş parçacığı havuzu üzerinde ve alan bir `Task<int>` işlemek.  `DoExpensiveCalculation()` sonunda eşzamanlı olarak sonraki kullanılabilir iş parçacığı üzerinde başka bir CPU çekirdeği üzerinde büyük olasılıkla çalıştırılır.  Eşzamanlı iş çalışırken yapmak mümkündür `DoExpensiveCalculation()` başka bir iş parçacığı üzerinde meşgul olduğundan çağrılan iş parçacığı `CalculateResult()` yürütülmeye devam.

Bir kez `await` karşılaşılırsa, yürütülmesi `CalculateResult()` sırasında geçerli iş parçacığı ile yapılacak diğer işleri izin vererek, arayana verdiğini `DoExpensiveCalculation()` bir sonuç fakat.  Tamamlandıktan sonra sonuç ana iş parçacığında çalıştırmak için sıraya alındı.  Sonuç olarak, ana iş parçacığı yürütülen döndürülecek `CalculateResult()`, bu noktada sonucu olacaktır `DoExpensiveCalculation()`.

### <a name="why-does-async-help-here"></a>Neden zaman uyumsuz burada yardımcı olur?

`async` ve `await` en iyi uygulamadır yönetme CPU bağımlı iş yanıtlama gerektiğinde şunlardır. Zaman uyumsuz CPU bağımlı iş ile kullanmak için birden çok desenleri vardır. Async kullanma için küçük bir maliyeti yoktur ve sıkı döngüler için önerilmez dikkate almak önemlidir.  Bu size kodunuzu bu yeni özellik geçici yazma biçimini belirlemek için hazır.

## <a name="see-also"></a>Ayrıca bkz.

[C# zaman uyumsuz programlama](~/docs/csharp/async.md)   
[Zaman uyumsuz programlama ile async ve await (C#)](../csharp/programming-guide/concepts/async/index.md)  
[F # zaman uyumsuz programlama](~/docs/fsharp/tutorials/asynchronous-and-concurrent-programming/async.md)   
[Zaman uyumsuz programlama ile Async ve Await (Visual Basic)](~/docs/visual-basic/programming-guide/concepts/async/index.md)
