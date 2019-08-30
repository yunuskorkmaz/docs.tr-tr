---
title: Zaman uyumsuz programlama-C#
description: .NET Core tarafından C# sunulan dil düzeyi zaman uyumsuz programlama modeli hakkında bilgi edinin.
author: cartermp
ms.date: 06/20/2016
ms.assetid: b878c34c-a78f-419e-a594-a2b44fa521a4
ms.custom: seodec18
ms.openlocfilehash: 246046fb5ac9b0c03df7df71ef426dc2ac6f0617
ms.sourcegitcommit: 1b020356e421a9314dd525539da12463d980ce7a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/30/2019
ms.locfileid: "70168808"
---
# <a name="asynchronous-programming"></a>Zaman uyumsuz programlama

G/ç bağlantılı bir gereksinimleriniz varsa (bir ağdan veri istemek veya bir veritabanına erişmek gibi), zaman uyumsuz programlamayı kullanmak isteyeceksiniz.  Ayrıca, zaman uyumsuz kod yazmak için iyi bir senaryo olan pahalı bir hesaplama yapma gibi CPU 'ya göre büyük bir kod de vardır.

C#, geri çağırmaları desteklemek veya bir kitaplığa uymak zorunda kalmadan, zaman uyumsuz kodların kolayca yazılmasına izin veren dil düzeyinde bir zaman uyumsuz programlama modeline sahiptir. [Görev tabanlı zaman uyumsuz model (TAP)](../standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md)olarak bilinen öğeleri izler.

## <a name="basic-overview-of-the-asynchronous-model"></a>Zaman uyumsuz modele temel genel bakış

Zaman uyumsuz programlama `Task` çekirdeği, zaman uyumsuz işlemleri `Task<T>` modelleyebilir ve nesneleridir.  `async` Ve`await` anahtar kelimeleri tarafından desteklenir.  Çoğu durumda model oldukça basittir:

G/ç ile bağlantılı kod `await` için, bir `async` yöntemin içinde `Task` veya `Task<T>` içinde döndüren bir işlem.

CPU 'ya bağlı kodda, `await` `Task.Run` yöntemi olan bir arka plan iş parçacığında başlatılan bir işlem.

`await` Anahtar sözcüğü, Magic 'in gerçekleştiği yerdir. Bu, uygulanan yöntemin `await`çağıranına denetim verir ve sonunda bir kullanıcı arabiriminin yanıt vermesini veya bir hizmetin esnek olmasını sağlar.

Zaman uyumsuz koda `async` yaklaşıma yönelik ve yukarıda bağlantı verilen `await` dokunma makalesinde özetlenen başka yollar vardır, ancak bu belge bu noktadan sonra gelen dil düzeyi yapılarına odaklanacaktır.

### <a name="io-bound-example-downloading-data-from-a-web-service"></a>G/ç bağlantılı örnek: Bir Web hizmetinden verileri indirme

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

İşte bu kadar! Kod, görev nesneleriyle etkileşimde bulunmak için sürüklenmeden azaltma olmadan amacı ifade eder (bazı verileri zaman uyumsuz olarak indirme).

### <a name="cpu-bound-example-performing-a-calculation-for-a-game"></a>CPU-bağlantılı örnek: Bir oyun için hesaplama gerçekleştirme

Bir düğmeye basmakta olduğunuz bir mobil oyun yazıyorsanız, ekranda çok sayıda enemaya zarar verebilir.  Hasar hesaplamasının gerçekleştirilmesi pahalı olabilir ve Kullanıcı arabirimi iş parçacığında yapıldığında, hesaplama gerçekleştirilirken oyun duraklatılmasını sağlar!

Bunu işlemenin en iyi yolu, kullanarak `Task.Run`çalışmayı ve `await` Bunun sonucunu belirleyen bir arka plan iş parçacığı başlatmanız olur.  Bu, iş yapıldığı için Kullanıcı arabiriminin sorunsuz bir şekilde çalışmasına olanak sağlar.

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
    // performs its work.  The UI thread is free to perform other work.
    var damageResult = await Task.Run(() => CalculateDamageDone());
    DisplayDamage(damageResult);
};
```

İşte bu kadar!  Bu kod, düğmenin tıklama olayının amacını düzgün bir şekilde ifade eder, arka plan iş parçacığını el ile yönetmeyi gerektirmez ve bunu engellenmeyen bir şekilde yapar.

### <a name="what-happens-under-the-covers"></a>Kapakların altında ne olur?

Zaman uyumsuz işlemlere önem taşıyan çok sayıda hareketli parça vardır.  `Task` Ve`Task<T>`' nin kapsadığından neler olduğunu merak ediyorsanız daha fazla bilgi için, [zaman uyumsuz derinlemesine kapsamlı](../standard/async-in-depth.md) makaleyi kullanıma alın.

Nesnelerin C# yanında, derleyici kodunuzu bir durum makinesine dönüştürür ve bir `await` arka plan işi bittiğinde yürütmeye devam edildiğinde yürütmeyi sürdürür.

Teorik olarak, bu, [zaman uyumsuzluğu 'nin Promise modelinin](https://en.wikipedia.org/wiki/Futures_and_promises)bir uygulamasıdır.

## <a name="key-pieces-to-understand"></a>Anlaşılması için önemli parçalar

* Zaman uyumsuz kod hem g/ç bağlantılı hem de CPU ile bağlantılı kod için kullanılabilir, ancak her senaryo için farklı olabilir.
* Zaman uyumsuz kod `Task<T>` ve `Task`, arka planda gerçekleştirilen işleri modellemek için kullanılan yapılar olan ve kullanır.
* Anahtar sözcüğü bir yöntemi bir zaman uyumsuz metoda dönüştürür. Bu, `await` anahtar sözcüğünü gövdesinde kullanmanıza olanak sağlar. `async`
* `await` Anahtar sözcüğü uygulandığında, çağıran yöntemi askıya alır ve bekleme görevi tamamlanana kadar denetimi çağrı yapana geri verir.
* `await`yalnızca zaman uyumsuz bir yöntem içinde kullanılabilir.

## <a name="recognize-cpu-bound-and-io-bound-work"></a>CPU ile bağlantılı ve g/ç bağlantılı çalışmayı tanıma

Bu kılavuzun ilk iki örneği, g/ç ile bağlantılı ve `async` CPU `await` ile bağlantılı çalışma için nasıl kullanabileceğinizi gösterir.  Bu, kodunuzun performansını önemli ölçüde etkileyebildiğinden ve belirli yapıların yanlış kullanılmasına neden olabileceği için ne zaman bir iş yapmanız gerektiğini (g/ç) veya CPU ile bağlantılı olarak belirleyebilmeniz için bir anahtardır.

Kodu yazmadan önce sormanız gereken iki soru aşağıda verilmiştir:

1. Kodunuz, bir veritabanının verileri gibi bir şey için "bekliyor" olarak değiştirilsin mi?

    Yanıtınız "Evet" ise, çalışmanız **g/ç 'ye bağlanır**.

2. Kodunuz çok pahalı bir hesaplama gerçekleştiriyor mu?

    "Evet" yanıtını verdiyseniz, çalışmanız **CPU 'ya bağlanır**.

Sahip olduğunuz iş **g/ç bağlantılı**ise `async` , ve `await` *olmadan* `Task.Run`kullanın.  Görev paralel kitaplığı kullanmamalısınız.  Bunun nedeni, [zaman uyumsuz olarak zaman uyumsuz makalesinde](../standard/async-in-depth.md)açıklanmıştır.

Sahip olduğunuz iş, **CPU** 'ya bağlıysa ve yanıt verdiğini düşünüyorsanız, `async` ' i kullanın ve `Task.Run` `await` ile işi başka bir iş parçacığında üretme işini yapın.  İş eşzamanlılık ve paralellik için uygunsa, [görev paralel kitaplığı](../standard/parallel-programming/task-parallel-library-tpl.md)kullanmayı da göz önünde bulundurmanız gerekir.

Ayrıca, kodunuzun yürütülmesini her zaman ölçmelisiniz.  Örneğin, iş parçacığı oluşturma sırasında bağlam anahtarlarının ek yüküne kıyasla, CPU bağlantılı çalışmanızın yeterince yüksek maliyetli olmadığı bir durumda kendinizi bulabilirsiniz.  Her seçim kendi zorunluluğunu getirir sahiptir ve durumunuz için doğru zorunluluğunu getirir öğesini seçmeniz gerekir.

## <a name="more-examples"></a>Daha fazla örnek

Aşağıdaki örneklerde, içinde C#zaman uyumsuz kod yazmak için kullanabileceğiniz çeşitli yollar gösterilmektedir.  Bunlar arasında karşılaşabileceğiniz birkaç farklı senaryo ele alınmaktadır.

### <a name="extracting-data-from-a-network"></a>Bir ağdan veri ayıklama

Bu kod parçacığı, [www.dotnetfoundation.org](https://www.dotnetfoundation.org) adresindeki GIRIŞ sayfasından HTML 'i indirir ve ".net" dizesinin HTML 'de oluşma sayısını sayar.  Bu görevi gerçekleştiren bir Web denetleyicisi yöntemi tanımlamak için ASP.NET MVC kullanır, sayı döndürür.

> [!NOTE]
> Üretim kodunda HTML ayrıştırma işlemi yapmanız planlandıysanız, normal ifadeleri kullanmayın. Bunun yerine bir ayrıştırma kitaplığı kullanın.

```csharp
private readonly HttpClient _httpClient = new HttpClient();

[HttpGet]
[Route("DotNetCount")]
public async Task<int> GetDotNetCountAsync()
{
    // Suspends GetDotNetCountAsync() to allow the caller (the web server)
    // to accept another request, rather than blocking on this one.
    var html = await _httpClient.GetStringAsync("https://dotnetfoundation.org");

    return Regex.Matches(html, @"\.NET").Count;
}
```

Bir düğmeye basıldığında aynı görevi gerçekleştiren bir Evrensel Windows uygulaması için yazılan senaryo aşağıda verilmiştir:

```csharp
private readonly HttpClient _httpClient = new HttpClient();

private async void SeeTheDotNets_Click(object sender, RoutedEventArgs e)
{
    // Capture the task handle here so we can await the background task later.
    var getDotNetFoundationHtmlTask = _httpClient.GetStringAsync("https://www.dotnetfoundation.org");

    // Any other work on the UI thread can be done here, such as enabling a Progress Bar.
    // This is important to do here, before the "await" call, so that the user
    // sees the progress bar before execution of this method is yielded.
    NetworkProgressBar.IsEnabled = true;
    NetworkProgressBar.Visibility = Visibility.Visible;

    // The await operator suspends SeeTheDotNets_Click, returning control to its caller.
    // This is what allows the app to be responsive and not block the UI thread.
    var html = await getDotNetFoundationHtmlTask;
    int count = Regex.Matches(html, @"\.NET").Count;

    DotNetCountLabel.Text = $"Number of .NETs on dotnetfoundation.org: {count}";

    NetworkProgressBar.IsEnabled = false;
    NetworkProgressBar.Visibility = Visibility.Collapsed;
}
```

### <a name="waiting-for-multiple-tasks-to-complete"></a>Birden çok görevin tamamlanması bekleniyor

Kendinizi aynı anda birden çok veri parçası almanız gereken bir durumda bulabilirsiniz.  API iki yöntem içerir `Task.WhenAny` ve birden fazla arka plan iş üzerinde engellenmeyen bir bekleme gerçekleştiren zaman uyumsuz kod yazmanızı sağlar. `Task.WhenAll` `Task`

Bu örnek, bir `User` `userId`dizi s için nasıl veri elde edebileceğini gösterir.

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

Bu, LINQ kullanarak bu bit daha fazla succinctly yazmak için başka bir yoldur:

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

Daha az kod olsa da, LINQ 'i zaman uyumsuz kodla karıştırdığınızda dikkatli olmanız gerekir.  LINQ, ertelenmiş (geç) yürütmeyi kullandığından, üretilen sırayı `foreach()` `.ToList()` veya `.ToArray()`' a çağrısıyla tekrarlamaya zormadığınız sürece zaman uyumsuz çağrılar bir döngüde olduğu gibi hemen gerçekleşmeyecek.

## <a name="important-info-and-advice"></a>Önemli bilgi ve öneriler

Zaman uyumsuz programlama görece basittir, ancak beklenmeyen davranışları engelleyebilen aklınızda bulundurmanız gereken bazı ayrıntılar vardır.

* `async`**yöntemlerin bir** **anahtar sözcüğü gövdelerinde veya hiçbir şekilde hiçbir sonuç vermez!** `await`

Göz önünde bulundurmanız önemlidir.  Bir yöntemin gövdesinde kullanılmazsa, C# derleyici bir uyarı oluşturur, ancak kod normal bir yöntem gibi derleyip çalıştırılır. `async` `await`  Bu, zaman uyumsuz yöntem için C# derleyici tarafından oluşturulan durum makinesi herhangi bir şeyi gerçekleştiremeyecek olduğundan, bunun da inanılmaz verimsiz olacağını unutmayın.

* **Yazdığınız her zaman uyumsuz yöntem adının soneki olarak "Async" eklemeniz gerekir.**

Bu, zaman uyumlu ve zaman uyumsuz yöntemleri daha kolay ayırt etmek için .NET ' te kullanılan kuraldır. Kodunuz (örneğin, olay işleyicileri veya Web denetleyicisi yöntemleri) tarafından açıkça çağrılmayan bazı yöntemlerin uygulanması gerekmediğini unutmayın. Bunlar kodunuz tarafından açıkça çağrılmadığı için, adlandırmalarına yönelik açık olması önemli değildir.

* `async void`**yalnızca olay işleyicileri için kullanılmalıdır.**

`async void`, olaylar dönüş türlerine sahip olmadığından zaman uyumsuz olay işleyicilerinin çalışmasına izin vermek için tek yoldur (Bu nedenle, `Task` ve `Task<T>`kullanamaz). ' Nin `async void` diğer kullanımı, dokunma modelini uygulamaz ve şu gibi kullanımı zor olabilir:

* Bir `async void` yöntemde oluşturulan özel durumlar, bu yöntemin dışında yakalanamıyor.
* `async void`yöntemler test etmek çok zordur.
* `async void`arayan, zaman uyumsuz olmasını beklemiyorsanız, Yöntemler hatalı yan etkilere neden olabilir.

* **LINQ ifadelerinde zaman uyumsuz Lambdalar kullanırken Tread dikkatlice**

LINQ kullanım içindeki lambda ifadeleri ertelenmiş yürütme, bu kodun bir kez çalıştırılmasını beklemiyorduk. Bu görevin engellenmesi, doğru yazılmayan bir kilitlenmeye neden olabilir. Ayrıca, bu gibi zaman uyumsuz kodun iç içe geçirilmesi, kodun yürütülmesi ile ilgili nedenlerle da daha zor hale gelir. Async ve LINQ güçlü, ancak mümkün olduğunca dikkatli ve açık olarak kullanılmalıdır.

* **Görevleri engellenmeyen bir şekilde beklede bir kod yazın**

Görevin tamamlanmasını beklemek için geçerli iş parçacığını engellemek, kilitlenmeleri ve engellenen bağlam iş parçacıklarının oluşmasına neden olabilir ve önemli ölçüde daha karmaşık hata işleme gerektirebilir. Aşağıdaki tabloda, engellenmeyen bir şekilde görevlerin beklenmesiyle ilgili yönergeler sağlanmaktadır:

| Bunu kullan... | Bunun yerine... | Bunu yapmak için |
| --- | --- | --- |
| `await` | `Task.Wait` veya `Task.Result` | Arka plan görevinin sonucunu alma |
| `await Task.WhenAny` | `Task.WaitAny` | Herhangi bir görevin tamamlanması bekleniyor |
| `await Task.WhenAll` | `Task.WaitAll` | Tüm görevlerin tamamlanması bekleniyor |
| `await Task.Delay` | `Thread.Sleep` | Bir süre bekleniyor |

* **Daha az durum bilgisi olan kod yazma**

Genel nesnelerin durumuna veya belirli yöntemlerin yürütülmesine bağlı değildir. Bunun yerine, yalnızca yöntemlerin dönüş değerlerine göre değişir. Neden?

* Kodun nedeni daha kolay olacaktır.
* Kodun test etmek daha kolay olacaktır.
* Zaman uyumsuz ve zaman uyumlu kodu karıştırma çok basittir.
* Yarış koşullarından genellikle tamamen kaçınılabilir.
* Dönüş değerlerine bağlı olarak, zaman uyumsuz kod koordine etme basit hale gelir.
* (Ödül) bağımlılık ekleme ile oldukça iyi bir şekilde çalışmaktadır.

Önerilen bir amaç, kodunuzda tam veya neredeyse tam bir [bilgi saydamlığı](https://en.wikipedia.org/wiki/Referential_transparency_%28computer_science%29) elde etmek için kullanılır. Bunun yapılması, son derece öngörülebilir, test edilebilir ve sürdürülebilir kod temeli oluşmasına neden olur.

## <a name="other-resources"></a>Diğer Kaynaklar

* [Zaman uyumsuz kapsamlı,](../standard/async-in-depth.md) görevlerin nasıl çalıştığı hakkında daha fazla bilgi sağlar.
* [Async ve await (C#) ile zaman uyumsuz programlama](./programming-guide/concepts/async/index.md)
* Zaman uyumsuz programlama için Lucian Wıchık 'nin [altı temel ipucu](https://channel9.msdn.com/Series/Three-Essential-Tips-for-Async) , Async programlama için harika bir kaynaktır
