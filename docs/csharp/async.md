---
title: 'Asynchronous programlama - C #'
description: .NET Core tarafından sağlanan C# dil düzeyinde ki eşzamanlı programlama modeli hakkında bilgi edinin.
author: cartermp
ms.date: 06/20/2016
ms.technology: csharp-async
ms.assetid: b878c34c-a78f-419e-a594-a2b44fa521a4
ms.openlocfilehash: 38d7c856e9a536db9ef26349175ad440a49f5fe2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75713949"
---
# <a name="asynchronous-programming"></a>Zaman uyumsuz programlama

G/Ç'ye bağlı gereksinimleriniz varsa (ağdan veri istemek veya veritabanına erişmek gibi), eşzamanlı programlamadan yararlanmak istersiniz.  Ayrıca, async kodu yazmak için de iyi bir senaryo olan pahalı bir hesaplama yapmak gibi CPU'ya bağlı kodunuz da olabilir.

C#, geri aramaları hokkabazlık yapmak veya eşzamanlılığı destekleyen bir kitaplıkla uyumluluk sağlamak zorunda kalmadan asynchronous kodu kolayca yazmanızı sağlayan bir dil düzeyinde eşzamanlı programlama modeline sahiptir. [Görev tabanlı Eşzamanlı Desen (TAP)](../standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md)olarak bilinen şeyi izler.

## <a name="basic-overview-of-the-asynchronous-model"></a>Eşzamanlı Modele Temel Genel Bakış

Async programlamanın özü, `Task` eşzamanlı `Task<T>` işlemleri modelleyen nesnelerdir.  Bunlar `async` ve `await` anahtar kelimeler tarafından desteklenir.  Model çoğu durumda oldukça basittir:

G/Ç bağlı kod için, bir yöntemin `Task<T>` bir `Task` `async` veya içinde döndüren bir işlem. `await`

CPU'ya bağlı kod `await` için, `Task.Run` yöntemle arka plan iş parçacığı üzerinde başlatılan bir işlem.

Anahtar `await` kelime sihrin gerçekleştiği yerdir. Gerçekleştirilen `await`yöntemin arayana denetim verir ve sonuçta bir Kullanıcı Aracı'nın yanıt vermesini veya bir hizmetin esnek olmasını sağlar.

Async koduna yukarıda bağlanan `async` `await` TAP makalesinde belirtilenden daha fazla yaklaşmanın başka yolları da vardır, ancak bu belge bu noktadan itibaren dil düzeyindeki yapılara odaklanacaktır.

### <a name="io-bound-example-downloading-data-from-a-web-service"></a>G/O-Bound Örnek: Bir web hizmetinden veri indirme

Bir düğmeye basıldığında bir web hizmetinden bazı verileri indirmeniz gerekebilir, ancak Web Bilgisi iş parçacığının engellenmesini istemezsiniz. Bu sadece bu şekilde gerçekleştirilebilir:

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

Hepsi bu! Kod, Görev nesneleri ile etkileşimde çıkmaza girmeden amacı (bazı verileri eşit olarak indirme) ifade eder.

### <a name="cpu-bound-example-performing-a-calculation-for-a-game"></a>CPU'ya bağlı Örnek: Oyun Için Hesaplama Yapmak

Bir düğmeye basarak ekrandaki birçok düşmana zarar verebileceği bir mobil oyun yazdığınızı varsan.  Hasar hesaplaması yapmak pahalı olabilir ve bunu UI iş parçacığı üzerinde yapmak, hesaplama yapıldıkça oyunun duraklatma sını durdurur!

Bunu işlemenin en iyi yolu, `Task.Run` `await` işi ve sonucunu kullanarak yapan bir arka plan iş parçacığı başlatmaktır.  Bu, iş yapılırken UI'nin kendinizi sorunsuz hissetmesini sağlayacaktır.

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

Hepsi bu!  Bu kod, düğmenin tıklama olayının amacını temiz bir şekilde ifade eder, bir arka plan iş parçacığının el ile yönetilmesini gerektirmez ve bunu engellemez bir şekilde yapar.

### <a name="what-happens-under-the-covers"></a>Örtülerin altında ne olur?

Eşzamanlı operasyonların söz konusu olduğu bir sürü hareketli parça var.  Kapaklarının altında neler olup bittiğini merak `Task` ediyorsanız, `Task<T>`daha fazla bilgi için [Async derinlemesine](../standard/async-in-depth.md) makaleye göz atın.

Nesnelerin C# tarafında, derleyici kodunuzu bir arka plan işi tamamlandığında yürütmeverim `await` ve yürütme devam gibi şeyleri izleyen bir durum makinesine dönüştürür.

Teorik olarak eğimli için, bu [asynchrony Söz Modeli](https://en.wikipedia.org/wiki/Futures_and_promises)bir uygulamadır.

## <a name="key-pieces-to-understand"></a>Anlaşılması Gereken Anahtar Parçalar

* Async kodu hem I/O-bound hem de CPU'ya bağlı kod için kullanılabilir, ancak her senaryo için farklı.
* Async kodu `Task<T>` `Task`kullanır ve , arka planda yapılan işi modellemek için kullanılan yapılardır.
* Anahtar `async` kelime, bir yöntemi, anahtar sözcüğü gövdesinde `await` kullanmanıza olanak tanıyan bir eşitleme yöntemine dönüştürür.
* `await` Anahtar kelime uygulandığında, arama yöntemini askıya eder ve beklenen görev tamamlanana kadar denetimi arayana geri verir.
* `await`yalnızca bir async yöntemi içinde kullanılabilir.

## <a name="recognize-cpu-bound-and-io-bound-work"></a>CPU'ya Bağlı ve G/Ç Bağlı Çalışmayı Tanıyın

Bu kılavuzun ilk iki örneği, `async` Nasıl `await` kullanabileceğinizi ve I/O-bound ve CPU'ya bağlı çalışmaları gösterdi.  Yapmanız gereken bir işin I/O'ya bağlı veya CPU'ya bağlı olduğunu belirleyebileceğiniz anahtardır, çünkü kodunuzu büyük ölçüde etkileyebilir ve bazı yapıları kötüye kullanmaya neden olabilir.

Herhangi bir kod yazmadan önce sormanız gereken iki soru şunlardır:

1. Kodunuz veritabanından alınan veriler gibi bir şey için "bekliyor" olacak mı?

    Cevabınız "evet" ise, o zaman iş **I / O-bağlı**.

2. Kodunuz çok pahalı bir hesaplama gerçekleştirecek mi?

    "Evet" yanıtını verdiyseniz, işiniz **CPU'ya bağlıdır.**

Sahip olduğunuz iş **I/O-bound** `async` ise, `await` kullanın ve *olmadan* `Task.Run`.  Görev Paralel Kitaplığı'nı *kullanmamalısınız.*  Bunun nedeni [Async in Depth makalesinde](../standard/async-in-depth.md)özetlenmiştir.

Sahip olduğunuz iş **CPU'ya bağlıysa** ve yanıt `async` verme `await` işlemini önemsiyorsanız, ancak işi başka bir iş parçacığı üzerinde '' *ile* `Task.Run`yumurtlanın.  Çalışma eşzamanlılık ve paralellik için uygunsa, [Görev Paralel Kitaplığı'nı](../standard/parallel-programming/task-parallel-library-tpl.md)da kullanmayı düşünmelisiniz.

Ayrıca, her zaman kodunuzu yürütme ölçmek gerekir.  Örneğin, cpu'ya bağlı çalışmanızın, çok iş parçacığı yaparken bağlam anahtarlarının yüküyle karşılaştırıldığında yeterince maliyetli olmadığı bir durumda bulabilirsiniz.  Her seçimin bir dengelemesi vardır ve durumunuz için doğru dengelemeyi seçmelisiniz.

## <a name="more-examples"></a>Diğer Örnekler

Aşağıdaki örnekler, C#'a async kodu yazabileceğiniz çeşitli yolları göstermektedir.  Karşılaşabileceğiniz birkaç farklı senaryoyu kapsıyor.

### <a name="extracting-data-from-a-network"></a>Ağdan Veri Çıkarma

Bu parçacık, HTML'yi ana sayfadan [www.dotnetfoundation.org](https://www.dotnetfoundation.org) indirir ve HTML'de ".NET" dizesinin kaç kez oluştuğunu sayar.  Bu sayıyı döndürerek, bu görevi gerçekleştiren bir web denetleyici yöntemi tanımlamak için ASP.NET MVC kullanır.

> [!NOTE]
> Üretim kodunda HTML ayrıştması yapmayı planlıyorsanız, normal ifadeler kullanmayın. Bunun yerine ayrıştma kitaplığı kullanın.

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

Bir Düğmeye basıldığında aynı görevi gerçekleştiren Evrensel Windows Uygulaması için yazılmış aynı senaryo aşağıda verilmiştir:

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

### <a name="waiting-for-multiple-tasks-to-complete"></a>Birden Çok Görevin Tamamlanmasını Bekliyor

Aynı anda birden çok veri parçası almanız gereken bir durumda bulabilirsiniz.  `Task` API iki `Task.WhenAll` yöntem içerir `Task.WhenAny` ve birden çok arka plan işleri üzerinde engelleyici olmayan bir bekleme gerçekleştiren eşzamanlı kod yazmak için izin verir.

Bu örnek, bir `User` s kümesi için `userId`verileri nasıl kapabileceğinizi gösterir.

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

LinQ kullanarak bunu biraz daha kısa yazmanın başka bir yolu daha var:

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

Daha az kod olmasına rağmen, LINQ'u eşzamanlı kodla karıştırırken dikkatli olsun.  LINQ ertelenmiş (tembel) yürütme kullandığından, `foreach()` oluşturulan sırayı bir çağrıyla `.ToList()` veya . `.ToArray()`

## <a name="important-info-and-advice"></a>Önemli Bilgi ve Öneriler

Async programlama nispeten basit olmasına rağmen, beklenmeyen davranışı önleyebilir akılda tutulması gereken bazı ayrıntılar vardır.

* `async`**yöntemleri** `await` kendi vücudunda bir anahtar kelime olması gerekir **ya da asla verim olmaz!**

Bu akılda tutulması gereken önemlidir.  Bir `await` `async` yöntemin gövdesinde kullanılmazsa, C# derleyicisi bir uyarı oluşturur, ancak kod normal bir yöntemgibi derlenir ve çalışır.  Async yöntemi için C# derleyicisi tarafından oluşturulan durum makinesi bir şey başarmak olmaz gibi bu da inanılmaz verimsiz olacağını unutmayın.

* **Yazdığınız her async yöntem adının sonek olarak "Async" eklemeniz gerekir.**

Bu, .NET'te senkron ve eşzamanlı yöntemleri daha kolay ayırt etmek için kullanılan kuraldır. Kodunuz tarafından açıkça çağrılmadı belirli yöntemlerin (olay işleyicileri veya web denetleyici yöntemleri gibi) mutlaka geçerli olmadığını unutmayın. Bunlar kodunuzun açıkça çağrılmadığından, adlandırmaları hakkında açık olmak o kadar da önemli değildir.

* `async void`**yalnızca olay işleyicileri için kullanılmalıdır.**

`async void`olaylar dönüş türleri olmadığından (bu nedenle kullanamaz `Task` ve). `Task<T>` Diğer kullanımlar `async void` TAP modelini izlemez ve aşağıdakiler gibi kullanımı zor olabilir:

* Bir `async void` yöntemde atılan özel durumlar bu yöntemin dışına yakalanamaz.
* `async void`yöntemleri test etmek çok zordur.
* `async void`arayan kişinin uyumlu olmasını beklemiyorsa, yöntemler kötü yan etkilere neden olabilir.

* **LINQ ifadelerinde async lambdas kullanırken dikkatli bir şekilde tread**

LINQ'daki Lambda ifadeleri ertelenmiş yürütmeyi kullanır, yani kod, beklemediğiniz bir zamanda yürütülebilir. Bu içine engelleme görevleri giriş kolayca doğru yazılmamışsa bir kilitlenme neden olabilir. Ayrıca, bu gibi eşsenkron kodun iç içe geçmede, kodun yürütülmesi hakkında neden daha zor hale getirebilir. Async ve LINQ güçlüdür, ancak mümkün olduğunca dikkatli ve net bir şekilde birlikte kullanılmalıdır.

* **Görevleri engellemeyen bir şekilde bekleyen kod yazma**

Bir Görevin tamamlanmasını beklemek için geçerli iş parçacığının engellenmesi kilitlenmelere ve engellenmiş bağlam iş parçacıklarına neden olabilir ve önemli ölçüde daha karmaşık hata işleme gerektirebilir. Aşağıdaki tablo, Görevleri engellemeyen bir şekilde beklemeyle nasıl başa çıkılalalalalabilmek konusunda kılavuz sağlar:

| Bunu kullanın... | Bunun yerine... | Bunu yapmak isteyen |
| --- | --- | --- |
| `await` | `Task.Wait` veya `Task.Result` | Arka plan görevinin sonucunu alma |
| `await Task.WhenAny` | `Task.WaitAny` | Herhangi bir görevin tamamlanmasını bekliyorum |
| `await Task.WhenAll` | `Task.WaitAll` | Tüm görevlerin tamamlanmasını bekliyorum |
| `await Task.Delay` | `Thread.Sleep` | Bir süre için bekleme |

* **Daha az durumlu kod yazma**

Küresel nesnelerin durumuna veya belirli yöntemlerin yürütülmesine bağlı değil. Bunun yerine, yalnızca yöntemlerin dönüş değerlerine bağlıdır. Neden?

* Kod hakkında neden daha kolay olacaktır.
* Kodu test etmek daha kolay olacaktır.
* Async ve senkron kodu karıştırmak çok daha kolaydır.
* Yarış koşulları genellikle tamamen önlenebilir.
* İade değerlerine bağlı olarak async kodunukoordine etmek kolaylaştırır.
* (Bonus) bağımlılık enjeksiyonu ile gerçekten iyi çalışır.

Önerilen hedef, kodunuzda tam veya neredeyse tamamlanmış [Başvuru Saydamlığı](https://en.wikipedia.org/wiki/Referential_transparency_%28computer_science%29) elde etmektir. Bunu yapmak son derece öngörülebilir, sınanabilir ve sürdürülebilir bir kod tabanıyla sonuçlanır.

## <a name="other-resources"></a>Diğer Kaynaklar

* [Async in-depth](../standard/async-in-depth.md) Görevlerin nasıl çalıştığı hakkında daha fazla bilgi sağlar.
* [Async ve await ile asynchronous programlama (C#)](./programming-guide/concepts/async/index.md)
* Lucian Wischik's [Six Essential Tips async için](https://channel9.msdn.com/Series/Three-Essential-Tips-for-Async) async programlama için harika bir kaynak
