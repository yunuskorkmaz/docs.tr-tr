---
title: 'Zaman uyumsuz programlama-C #'
description: .NET Core tarafından sunulan C# dil düzeyi zaman uyumsuz programlama modeli hakkında bilgi edinin.
author: cartermp
ms.date: 05/20/2020
ms.technology: csharp-async
ms.assetid: b878c34c-a78f-419e-a594-a2b44fa521a4
ms.openlocfilehash: 35ba90f978b1993f80451a28a4cd08129afddd85
ms.sourcegitcommit: 3d84eac0818099c9949035feb96bbe0346358504
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/21/2020
ms.locfileid: "86864507"
---
# <a name="asynchronous-programming"></a>Zaman uyumsuz programlama

G/ç bağlantılı bir gereksinimleriniz varsa (bir ağdan veri isteme, veritabanına erişme veya dosya sistemine okuma ve yazma gibi), zaman uyumsuz programlama kullanmak isteyeceksiniz. Ayrıca, zaman uyumsuz kod yazmak için iyi bir senaryo olan pahalı bir hesaplama yapma gibi CPU 'ya göre büyük bir kod de vardır.

C#, geri çağırmaları desteklemek veya asynchrony 'yi destekleyen bir kitaplığa uymak zorunda kalmadan, zaman uyumsuz kodların kolayca yazılmasına izin veren dil düzeyinde bir zaman uyumsuz programlama modeline sahiptir. [Görev tabanlı zaman uyumsuz model (TAP)](../standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md)olarak bilinen öğeleri izler.

## <a name="overview-of-the-asynchronous-model"></a>Zaman uyumsuz modele genel bakış

Zaman uyumsuz programlama çekirdeği, `Task` `Task<T>` zaman uyumsuz işlemleri modelleyebilir ve nesneleridir. `async`Ve `await` anahtar kelimeleri tarafından desteklenir. Çoğu durumda model oldukça basittir:

- G/ç 'ye bağlanan kod için, bir `Task` yöntemin içine veya içine döndüren bir işlemi bekleolursunuz `Task<T>` `async` .
- CPU 'ya bağlı kod için, yöntemi olan bir arka plan iş parçacığında başlatılan bir işlemi bekleolursunuz <xref:System.Threading.Tasks.Task.Run%2A?displayProperty=nameWithType> .

`await`Anahtar sözcüğü, Magic 'in gerçekleştiği yerdir. Bu, uygulanan yöntemin çağıranına denetim verir `await` ve sonunda bir kullanıcı arabiriminin yanıt vermesini veya bir hizmetin esnek olmasını sağlar. Ve dışındaki zaman uyumsuz koda yaklaşıma [yolları](../standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md) olmakla kalmaz `async` `await` , bu makale dil düzeyi yapılarına odaklanır.

### <a name="io-bound-example-download-data-from-a-web-service"></a>G/ç bağlantılı örnek: bir Web hizmetinden veri Indirin

Düğmeye basıldığında bir Web hizmetinden bazı verileri indirmeniz gerekebilir, ancak UI iş parçacığını engellemek istemezsiniz. Bu, şöyle gerçekleştirilebilir:

```csharp
private readonly HttpClient _httpClient = new HttpClient();

downloadButton.Clicked += async (o, e) =>
{
    // This line will yield control to the UI as the request
    // from the web service is happening.
    //
    // The UI thread is now free to perform other work.
    var stringData = await _httpClient.GetStringAsync(URL);
    DoSomethingWithData(stringData);
};
```

Kod, nesneleri ile etkileşimde bulunmak için sürüklenmeden azaltma olmadan hedefi (verileri zaman uyumsuz olarak indirme) ifade eder `Task` .

### <a name="cpu-bound-example-perform-a-calculation-for-a-game"></a>CPU-bağlantılı örnek: bir oyun için hesaplama gerçekleştirme

Bir düğmeye basmakta olduğunuz bir mobil oyun yazıyorsanız, ekranda çok sayıda enemaya zarar verebilir. Hasar hesaplamasının gerçekleştirilmesi pahalı olabilir ve Kullanıcı arabirimi iş parçacığında yapıldığında, hesaplama gerçekleştirilirken oyun duraklatılmasını sağlar!

Bunu işlemenin en iyi yolu, kullanarak çalışmayı ve sonucunu bekleme işini başlatan bir arka plan iş parçacığını `Task.Run` başlatmanız olur `await` . Bu, iş yapıldığı için Kullanıcı arabiriminin sorunsuz bir şekilde çalışmasını sağlar.

```csharp
private DamageResult CalculateDamageDone()
{
    // Code omitted:
    //
    // Does an expensive calculation and returns
    // the result of that calculation.
}

calculateButton.Clicked += async (o, e) =>
{
    // This line will yield control to the UI while CalculateDamageDone()
    // performs its work. The UI thread is free to perform other work.
    var damageResult = await Task.Run(() => CalculateDamageDone());
    DisplayDamage(damageResult);
};
```

Bu kod, düğmenin tıklama olayının amacını düzgün bir şekilde ifade eder, arka plan iş parçacığını el ile yönetmeyi gerektirmez ve bunu engellenmeyen bir şekilde yapar.

### <a name="what-happens-under-the-covers"></a>Kapakların altında ne olur?

Zaman uyumsuz işlemlere önem taşıyan çok sayıda hareketli parça vardır. Ve ' nin altında neler olduğunu merak ediyorsanız `Task` `Task<T>` , daha fazla bilgi Için [zaman uyumsuz derinlemesine kapsamlı](../standard/async-in-depth.md) makaleye bakın.

Derleyici, nesnelerin C# tarafında, bir `await` , erişildiğinde ve bir arka plan işi bittiğinde yürütmeye devam edildiğinde yürütmeyi sürdüetler gibi şeyleri izleyen bir durum makinesine dönüştürür.

Teorik olarak, bu, [zaman uyumsuzluğu 'nin Promise modelinin](https://en.wikipedia.org/wiki/Futures_and_promises)bir uygulamasıdır.

## <a name="key-pieces-to-understand"></a>Anlaşılması için önemli parçalar

* Zaman uyumsuz kod hem g/ç bağlantılı hem de CPU ile bağlantılı kod için kullanılabilir, ancak her senaryo için farklı olabilir.
* Zaman uyumsuz kod `Task<T>` ve `Task` , arka planda gerçekleştirilen işleri modellemek için kullanılan yapılar olan ve kullanır.
* `async`Anahtar sözcüğü bir yöntemi bir zaman uyumsuz metoda dönüştürür. Bu, `await` anahtar sözcüğünü gövdesinde kullanmanıza olanak sağlar.
* `await`Anahtar sözcüğü uygulandığında, çağıran yöntemi askıya alır ve bekleme görevi tamamlanana kadar denetimi çağrı yapana geri verir.
* `await`yalnızca zaman uyumsuz bir yöntem içinde kullanılabilir.

## <a name="recognize-cpu-bound-and-io-bound-work"></a>CPU ile bağlantılı ve g/ç bağlantılı çalışmayı tanıma

Bu kılavuzun ilk iki örneği, `async` `await` g/ç ile bağlantılı ve CPU ile bağlantılı çalışma için nasıl kullanabileceğinizi gösterir. Bu, kodunuzun performansını önemli ölçüde etkileyebildiğinden ve belirli yapıların yanlış kullanılmasına neden olabileceği için ne zaman bir iş yapmanız gerektiğini (g/ç) veya CPU ile bağlantılı olarak belirleyebilmeniz için bir anahtardır.

Kodu yazmadan önce sormanız gereken iki soru aşağıda verilmiştir:

1. Kodunuz, bir veritabanının verileri gibi bir şey için "bekliyor" olarak değiştirilsin mi?

   Yanıtınız "Evet" ise, çalışmanız **g/ç 'ye bağlanır**.

1. Kodunuz pahalı bir hesaplama gerçekleştiriyor mu?

   "Evet" yanıtını verdiyseniz, çalışmanız **CPU 'ya bağlanır**.

Sahip olduğunuz iş **g/ç bağlantılı**ise, `async` ve `await` *olmadan* kullanın `Task.Run` . Görev paralel *kitaplığı kullanmamalısınız.* Bunun nedeni, [zaman uyumsuz olarak zaman uyumsuz](../standard/async-in-depth.md)olarak özetlenmiştir.

Sahip olduğunuz iş, **CPU** 'ya bağlıysa ve yanıt verdiğini düşünüyorsanız, `async` ve ' i kullanın, `await` ancak *ile* başka bir iş parçacığında çalışmayı yapın `Task.Run` . İş eşzamanlılık ve paralellik için uygunsa, [görev paralel kitaplığı](../standard/parallel-programming/task-parallel-library-tpl.md)kullanmayı da düşünün.

Ayrıca, kodunuzun yürütülmesini her zaman ölçmelisiniz. Örneğin, iş parçacığı oluşturma sırasında bağlam anahtarlarının ek yüküne kıyasla, CPU bağlantılı çalışmanızın yeterince yüksek maliyetli olmadığı bir durumda kendinizi bulabilirsiniz. Her seçim kendi zorunluluğunu getirir sahiptir ve durumunuz için doğru zorunluluğunu getirir öğesini seçmeniz gerekir.

## <a name="more-examples"></a>Daha fazla örnek

Aşağıdaki örneklerde, C# dilinde zaman uyumsuz kod yazmak için çeşitli yollar gösterilmektedir. Bunlar arasında karşılaşabileceğiniz birkaç farklı senaryo ele alınmaktadır.

### <a name="extract-data-from-a-network"></a>Bir ağdan veri ayıklama

Bu kod parçacığı, konumundaki giriş sayfasından HTML 'i indirir <https://dotnetfoundation.org> ve ".net" DIZESININ HTML 'de oluşma sayısını sayar. Bu görevi gerçekleştiren ve sayıyı döndüren bir Web API denetleyicisi yöntemi tanımlamak için ASP.NET kullanır.

> [!NOTE]
> Üretim kodunda HTML ayrıştırma işlemi yapmanız planlandıysanız, normal ifadeleri kullanmayın. Bunun yerine bir ayrıştırma kitaplığı kullanın.

```csharp
private readonly HttpClient _httpClient = new HttpClient();

[HttpGet, Route("DotNetCount")]
public async Task<int> GetDotNetCount()
{
    // Suspends GetDotNetCount() to allow the caller (the web server)
    // to accept another request, rather than blocking on this one.
    var html = await _httpClient.GetStringAsync("https://dotnetfoundation.org");

    return Regex.Matches(html, @"\.NET").Count;
}
```

Bir düğmeye basıldığında aynı görevi gerçekleştiren bir Evrensel Windows uygulaması için yazılan senaryo aşağıda verilmiştir:

```csharp
private readonly HttpClient _httpClient = new HttpClient();

private async void OnSeeTheDotNetsButtonClick(object sender, RoutedEventArgs e)
{
    // Capture the task handle here so we can await the background task later.
    var getDotNetFoundationHtmlTask = _httpClient.GetStringAsync("https://dotnetfoundation.org");

    // Any other work on the UI thread can be done here, such as enabling a Progress Bar.
    // This is important to do here, before the "await" call, so that the user
    // sees the progress bar before execution of this method is yielded.
    NetworkProgressBar.IsEnabled = true;
    NetworkProgressBar.Visibility = Visibility.Visible;

    // The await operator suspends OnSeeTheDotNetsButtonClick(), returning control to its caller.
    // This is what allows the app to be responsive and not block the UI thread.
    var html = await getDotNetFoundationHtmlTask;
    int count = Regex.Matches(html, @"\.NET").Count;

    DotNetCountLabel.Text = $"Number of .NETs on dotnetfoundation.org: {count}";

    NetworkProgressBar.IsEnabled = false;
    NetworkProgressBar.Visibility = Visibility.Collapsed;
}
```

### <a name="wait-for-multiple-tasks-to-complete"></a>Birden çok görevin tamamlanmasını bekle

Kendinizi aynı anda birden çok veri parçası almanız gereken bir durumda bulabilirsiniz. `Task`API iki yöntem içerir <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> ve bu, <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType> birden fazla arka plan iş üzerinde engellenmeyen bir bekleme gerçekleştiren zaman uyumsuz kod yazmanıza olanak tanır.

Bu örnek, `User` bir dizi s için nasıl veri elde edebileceğini gösterir `userId` .

```csharp
public async Task<User> GetUserAsync(int userId)
{
    // Code omitted:
    //
    // Given a user Id {userId}, retrieves a User object corresponding
    // to the entry in the database with {userId} as its Id.
}

public static async Task<IEnumerable<User>> GetUsersAsync(IEnumerable<int> userIds)
{
    var getUserTasks = new List<Task<User>>();
    foreach (int userId in userIds)
    {
        getUserTasks.Add(GetUserAsync(userId));
    }

    return await Task.WhenAll(getUserTasks);
}
```

Bu, LINQ kullanarak daha fazla succinctly yazmak için başka bir yoldur:

```csharp
public async Task<User> GetUserAsync(int userId)
{
    // Code omitted:
    //
    // Given a user Id {userId}, retrieves a User object corresponding
    // to the entry in the database with {userId} as its Id.
}

public static async Task<User[]> GetUsersAsync(IEnumerable<int> userIds)
{
    var getUserTasks = userIds.Select(id => GetUserAsync(id));
    return await Task.WhenAll(getUserTasks);
}
```

Daha az kod olsa da, LINQ 'i zaman uyumsuz kodla karıştırdığınızda dikkatli olun. LINQ, ertelenmiş (geç) yürütmeyi kullandığından, `foreach` üretilen sırayı veya ' a çağrısıyla tekrarlamaya zormadığınız sürece zaman uyumsuz çağrılar bir döngüde olduğu gibi hemen gerçekleşmeyecek `.ToList()` `.ToArray()` .

## <a name="important-info-and-advice"></a>Önemli bilgi ve öneriler

Zaman uyumsuz programlama ile, beklenmeyen davranışlara engel olabilecek bazı ayrıntılar göz önünde bulundurularak vardır.

* `async`**yöntemlerin bir** `await` **anahtar sözcüğü gövdelerinde veya hiçbir şekilde hiçbir sonuç vermez!**

  Göz önünde bulundurmanız önemlidir. `await`Bir yöntemin gövdesinde kullanılmazsa `async` , C# derleyicisi bir uyarı oluşturur, ancak kod normal bir yöntem gibi derlenir ve çalışır. Bu, zaman uyumsuz yöntem için C# derleyicisi tarafından oluşturulan durum makinesi herhangi bir şeyi gerçekleştirmediğinden, inanılmaz verimsiz olur.

* **Yazdığınız her zaman uyumsuz yöntem adının soneki olarak "Async" eklemeniz gerekir.**

Bu, zaman uyumlu ve zaman uyumsuz yöntemleri daha kolay ayırt etmek için .NET ' te kullanılan kuraldır. Kodunuz tarafından açıkça çağrılmayan bazı Yöntemler (örneğin, olay işleyicileri veya Web denetleyicisi yöntemleri) uygulanabilir değildir. Kodunuz tarafından açıkça çağrılmadığı için, adlandırmaları hakkında açık olması önemli değildir.

* `async void`**yalnızca olay işleyicileri için kullanılmalıdır.**

`async void`, olaylar dönüş türlerine sahip olmadığından zaman uyumsuz olay işleyicilerinin çalışmasına izin vermek için tek yoldur (Bu nedenle, `Task` ve kullanamaz `Task<T>` ). ' Nin diğer kullanımı, `async void` dokunma modelini uygulamaz ve şu gibi kullanımı zor olabilir:

* Bir yöntemde oluşturulan özel durumlar, `async void` Bu yöntemin dışında yakalanamıyor.
* `async void`yöntemler test etmek zordur.
* `async void`arayan, zaman uyumsuz olmasını beklemiyorsanız, Yöntemler hatalı yan etkilere neden olabilir.

* **LINQ ifadelerinde zaman uyumsuz Lambdalar kullanırken Tread dikkatlice**

LINQ kullanım içindeki lambda ifadeleri ertelenmiş yürütme, bu kodun bir kez çalıştırılmasını beklemiyorduk. Bu görevin engellenmesi, doğru yazılmayan bir kilitlenmeye neden olabilir. Ayrıca, bu gibi zaman uyumsuz kodun iç içe geçirilmesi, kodun yürütülmesi ile ilgili nedenlerle da daha zor hale gelir. Async ve LINQ güçlü, ancak mümkün olduğunca dikkatli ve açık olarak kullanılmalıdır.

* **Görevleri engellenmeyen bir şekilde beklede bir kod yazın**

Bir işlemin tamamlanmasını beklemek için geçerli iş parçacığını engellemek `Task` kilitlenmeleri ve engellenen bağlam iş parçacıklarının oluşmasına neden olabilir ve daha karmaşık hata işleme gerektirebilir. Aşağıdaki tabloda, engellenmeyen bir şekilde görevlerin beklenmesiyle ilgili yönergeler sağlanmaktadır:

| Bunu kullanın...          | Bunun yerine...           | Bunu yaparken...                 |
|----------------------|------------------------------|--------------------------------------------|
| `await`              | `Task.Wait` veya `Task.Result` | Arka plan görevinin sonucunu alma |
| `await Task.WhenAny` | `Task.WaitAny`               | Herhangi bir görevin tamamlanması bekleniyor           |
| `await Task.WhenAll` | `Task.WaitAll`               | Tüm görevlerin tamamlanması bekleniyor          |
| `await Task.Delay`   | `Thread.Sleep`               | Bir süre bekleniyor               |

* **Kullanmayı düşünün** `ValueTask` **mümkün olduğunda**

`Task`Zaman uyumsuz metotlardan bir nesne döndürmek, belirli yollarda performans sorunlarını ortaya çıkarabilir. `Task`bir başvuru türüdür, bu nedenle bu bir nesne ayırma anlamına gelir. Değiştirici ile belirtilen bir yöntemin `async` önbelleğe alınmış bir sonuç döndürdüğü veya zaman uyumlu olarak tamamladığı durumlarda, ek ayırmalar kodun performans açısından kritik bölümlerinde önemli bir zaman maliyeti olabilir. Bu ayırmalar sıkı Döngülerde gerçekleşirse maliyetli hale gelebilir. Daha fazla bilgi için bkz. [Genelleştirilmiş zaman uyumsuz dönüş türleri](whats-new/csharp-7.md#generalized-async-return-types).

* Kullanmayı **düşünün**`ConfigureAwait(false)`

Ortak bir soru, "yöntemi ne zaman kullanmalıyım <xref:System.Threading.Tasks.Task.ConfigureAwait(System.Boolean)?displayProperty=nameWithType> ?" dir. Yöntemi, bir örneğin, `Task` awaiter 'yi yapılandırmasına izin verir. Bu önemli bir noktadır ve yanlış ayarlanmaması, performans etkilerine ve hatta kilitlenmeleri sağlayabilir. Hakkında daha fazla bilgi için `ConfigureAwait` , bkz. [ConfigureAwait SSS](https://devblogs.microsoft.com/dotnet/configureawait-faq).

* **Daha az durum bilgisi olan kod yazma**

Genel nesnelerin durumuna veya belirli yöntemlerin yürütülmesine bağlı değildir. Bunun yerine, yalnızca yöntemlerin dönüş değerlerine göre değişir. Neden mi?

* Kodun nedeni daha kolay olacaktır.
* Kodun test etmek daha kolay olacaktır.
* Zaman uyumsuz ve zaman uyumlu kodu karıştırma çok basittir.
* Yarış koşullarından genellikle tamamen kaçınılabilir.
* Dönüş değerlerine bağlı olarak, zaman uyumsuz kod koordine etme basit hale gelir.
* (Ödül) bağımlılık ekleme ile oldukça iyi bir şekilde çalışmaktadır.

Önerilen bir amaç, kodunuzda tam veya neredeyse tam bir [bilgi saydamlığı](https://en.wikipedia.org/wiki/Referential_transparency_%28computer_science%29) elde etmek için kullanılır. Bunun yapılması, son derece öngörülebilir, test edilebilir ve sürdürülebilir kod temeli oluşmasına neden olur.

## <a name="other-resources"></a>Diğer kaynaklar

* [Zaman uyumsuz kapsamlı,](../standard/async-in-depth.md) görevlerin nasıl çalıştığı hakkında daha fazla bilgi sağlar.
* [Async ve await ile zaman uyumsuz programlama (C#)](./programming-guide/concepts/async/index.md)
* Zaman uyumsuz programlama için Lucian Wıchık 'nin [altı temel ipucu](https://channel9.msdn.com/Series/Three-Essential-Tips-for-Async) , Async programlama için harika bir kaynaktır
