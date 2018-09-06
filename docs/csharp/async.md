---
title: Zaman uyumsuz programlama
description: .NET Core tarafından sağlanan C# dil düzeyi zaman uyumsuz programlama modeli hakkında bilgi edinin.
author: cartermp
ms.date: 06/20/2016
ms.assetid: b878c34c-a78f-419e-a594-a2b44fa521a4
ms.openlocfilehash: 971295b85e5f2763eef87bfe9109524db2630120
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2018
ms.locfileid: "43741376"
---
# <a name="asynchronous-programming"></a>Zaman uyumsuz programlama

(Örneğin, bir ağ üzerinden veri isteme veya bir veritabanına erişirken) tüm miyim/O-bağlı gereksinimleriniz varsa, zaman uyumsuz programlama kullanmak isteyebilirsiniz.  Ayrıca, zaman uyumsuz kod yazmak için iyi bir senaryodur pahalı bir hesaplama gerçekleştirmek gibi CPU bağımlı kod da olabilir.

C# kolayca geri çağırmaları juggle veya faaliyetler destekleyen bir kitaplığa uymak zorunda kalmadan zaman uyumsuz kod yazmak için izin veren bir dil düzeyinde zaman uyumsuz programlama modeli vardır. Olarak bilinen takip eden [görev tabanlı zaman uyumsuz desen (TAP)](../standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md).

## <a name="basic-overview-of-the-asynchronous-model"></a>Zaman uyumsuz Model temel genel bakış

Zaman uyumsuz programlamanın temel `Task` ve `Task<T>` zaman uyumsuz işlemler model nesneleri.  Tarafından desteklenen `async` ve `await` anahtar sözcükleri.  Çoğu durumda modeli oldukça basittir: 

Ben/O-bağlama kodunu, `await` döndüren bir işlem bir `Task` veya `Task<T>` içine bir `async` yöntemi.

CPU bağımlı kod için `await` ile arka plan iş parçacığında başlatılan bir işlem `Task.Run` yöntemi.

`await` Anahtar sözcüğü, burada sihrin. Gerçekleştirilen bir yöntemi çağıran kişi için Denetim verir `await`, ve sonuçta bir kullanıcı Arabirimi yanıt vermesi veya esnek bir şekilde bir hizmet sağlar.

Yaklaşım daha zaman uyumsuz kod için başka bir yöntemle `async` ve `await` DOKUNUN makaleyi, yukarıda bağlantı bölümünde açıklanan, ancak bu belgede, bu noktadan itibaren dil düzeyinde yapılar üzerinde odaklanır.

### <a name="io-bound-example-downloading-data-from-a-web-service"></a>Ben/O-bağlı örnek: bir web hizmetinden veri indirme

Bir düğmeye basıldığında, bazı veriler bir web hizmetinden indirmeniz gerekebilir ancak UI iş parçacığını engellemesini istemiyorsanız. Yalnızca şu şekilde gerçekleştirilebilir:

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

Ve İşte bu kadar! Kod (bazı veriler zaman uyumsuz olarak yükleme) amacı, görev nesnelerle etkileşim içinde çıkmaza olmadan ifade eder.

### <a name="cpu-bound-example-performing-a-calculation-for-a-game"></a>CPU bağımlı örnek: bir hesaplama için oyun gerçekleştirme

Burada bir düğmeye basarak zarar ekranında birçok düşman üzerinde başını ağrıtabilir mobil oyun yazdığınız varsayalım.  Zarar hesaplama gerçekleştirmek pahalı olabilir ve kullanıcı Arabirimi iş parçacığında yapılması oyun hesaplama gerçekleştirildiği duraklatmak için görünür hale getirir!

Bu durumu çözmek için en iyi yolu kullanarak iş yapan bir arka plan iş parçacığı olan `Task.Run`, ve `await` sonucu.  Bu, UI iş bitti olarak kesintisiz düşünüyorsanız olanak tanır.

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

Ve İşte bu kadar!  Bu kodun amacı düzgün bir şekilde ifade düğmenin olay'ı tıklatın, bir arka plan iş parçacığı el ile yönetme gerektirmez ve engelleyici olmayan bir yolla bunu yapar.

### <a name="what-happens-under-the-covers"></a>Bu işlem arka planda ne olur?

Birçok hareketli parça nerede zaman uyumsuz işlemler ilgilenir yoktur.  Aslında neler olduğu hakkında merak `Task` ve `Task<T>`, kullanıma alma [ayrıntılı zaman uyumsuz](../standard/async-in-depth.md) makale daha fazla bilgi için.

C# tarafında nesnelerin interneti, derleyici, kodunuzun yürütme sonuçlanmıyor gibi şeyler ve bir Durum makinesi dönüştüren olduğunda bir `await` ulaştı ve sürdürme yürütmesi bir arka plan işi tamamlandığında.

Teorik olarak-yazmaya için bu uygulamasıdır [faaliyetler Promise modelinin](https://en.wikipedia.org/wiki/Futures_and_promises).

## <a name="key-pieces-to-understand"></a>Temel Parçalar aşağıda anlamanın

*   Zaman uyumsuz kod, ı/O-bağlı hem de CPU bağımlı kod ancak farklı her senaryo için kullanılabilir.
*   Zaman uyumsuz kod `Task<T>` ve `Task`, model çalışma arka planda yapılması için kullanılan yapıları olduğu.
* `async` Anahtar sözcüğü bir yöntem kullanmanıza olanak tanıyan bir zaman uyumsuz yönteme bırakır `await` gövdesinde anahtar sözcüğü.
*   Zaman `await` anahtar sözcüğü uygulanırsa, çağıran yöntem askıya alır ve beklenen görev tamamlanana kadar denetim çağırana geri verir.
*   `await` yalnızca zaman uyumsuz bir yöntem içinde kullanılabilir.

## <a name="recognize-cpu-bound-and-io-bound-work"></a>CPU bağımlı ve ben/O-bağlı iş tanıması

Bu kılavuzun ilk iki örnek gösterdi nasıl kullanabileceğinizi `async` ve `await` miyim/O-bağlı ve CPU bağımlı iş için.  Bir işi yapmak ihtiyaç duyduğunuzda, tanımlayabilirsiniz, anahtar miyim/O-bağlı veya CPU sınırlıdır, kodunuzun performansını önemli ölçüde etkileyebilir ve potansiyel olarak olabilir çünkü kötüye adayı belirli oluşturur.

Herhangi bir kod yazmadan önce istemelisiniz iki sorular şunlardır:

1. Kodunuzu "veritabanından veri gibi bir şey için bekleyeceği süreye"?

    "Evet" aradığınız cevaptır sonra iş **miyim/O-bağlı**.

2. Kodunuzu çok pahalı bir hesaplama gerçekleştiren?

    "Evet" yanıtlanmış sonra iş **CPU bağımlı**.
    
Sahip olduğunuz iş ise **miyim/O-bağlı**, kullanın `async` ve `await` *olmadan* `Task.Run`.  *Barındırmamalıdır* görev paralel Kitaplığı'nı kullanın.  Bunun nedeni açıklandığı [zaman uyumsuz derinliği makaledeki](../standard/async-in-depth.md).

Sahip olduğunuz iş ise **CPU bağımlı** ve yanıtlama hakkında kullanım verdiğiniz `async` ve `await` ancak başka bir iş parçacığında iş devre dışı üretme *ile* `Task.Run`.  İş eşzamanlılığı ve paralelliği için uygun değilse, görev paralel kitaplığı kullanarak da düşünmelisiniz.

Ayrıca, her zaman kodunuzun yürütülmesini ölçü.  Örneğin, kendinizi CPU bağımlı iş olduğu pahalı bir durumda bulabilirsiniz yeterli bağlam anahtarları çoklu iş parçacığı zaman ek yükü ile karşılaştırılır.  Kendi tradeoff her seçeneği vardır ve kendi durumunuza doğru artırabilen seçmeniz gerekir.

## <a name="more-examples"></a>Daha fazla örnek

Aşağıdaki örnekler, zaman uyumsuz kodu C# içinde yazabileceğiniz çeşitli şekillerde gösterir.  Bunlar arasında gelebilir birkaç farklı senaryoları kapsar.

### <a name="extracting-data-from-a-network"></a>Ağ üzerinden veri ayıklama

Bu kod parçacığı giriş sayfasının HTML indirir [www.dotnetfoundation.org](https://www.dotnetfoundation.org) ve ".NET" dize gerçekleşir HTML'de sayısını sayar.  ASP.NET MVC sayısı, bu görevi gerçekleştiren bir web denetleyicisi yöntemi tanımlamak için kullanır.

> [!NOTE]
> HTML Ayrıştırma üretim kodunda yapmayı planlıyorsanız, normal ifadeler kullanmayın. Bunun yerine bir ayrıştırma kitaplığını kullanın.

```csharp
private readonly HttpClient _httpClient = new HttpClient();

[HttpGet]
[Route("DotNetCount")]
public async Task<int> GetDotNetCountAsync()
{
    // Suspends GetDotNetCountAsync() to allow the caller (the web server)
    // to accept another request, rather than blocking on this one.
    var html = await _httpClient.GetStringAsync("http://dotnetfoundation.org");

    return Regex.Matches(html, @"\.NET").Count;
}
```

Bir evrensel Windows bir düğmeye basıldığında aynı görevi gerçekleştiren uygulama için yazılmış aynı senaryo aşağıda verilmiştir:

```csharp
private readonly HttpClient _httpClient = new HttpClient();

private async void SeeTheDotNets_Click(object sender, RoutedEventArgs e)
{
    // Capture the task handle here so we can await the background task later.
    var getDotNetFoundationHtmlTask = _httpClient.GetStringAsync("http://www.dotnetfoundation.org");

    // Any other work on the UI thread can be done here, such as enabling a Progress Bar.
    // This is important to do here, before the "await" call, so that the user
    // sees the progress bar before execution of this method is yielded.
    NetworkProgressBar.IsEnabled = true;
    NetworkProgressBar.Visibility = Visibility.Visible;

    // The await operator suspends SeeTheDotNets_Click, returning control to its caller.
    // This is what allows the app to be responsive and not hang on the UI thread.
    var html = await getDotNetFoundationHtmlTask;
    int count = Regex.Matches(html, @"\.NET").Count;

    DotNetCountLabel.Text = $"Number of .NETs on dotnetfoundation.org: {count}";

    NetworkProgressBar.IsEnabled = false;
    NetworkProgressBar.Visibility = Visibility.Collapsed;
}
```

### <a name="waiting-for-multiple-tasks-to-complete"></a>Birden çok görevin tamamlanması bekleniyor

Aynı anda birden çok parça veri almak için gerek duyduğunuz bir durumda kendinizi bulabilirsiniz.  `Task` API içeren iki yöntem `Task.WhenAll` ve `Task.WhenAny` engelleyici olmayan bir bekleme birden fazla arka plan işleri yapan zaman uyumsuz kod yazma sağlar.

Bu örnek nasıl alın gösterir `User` veri kümesi için `userId`s.

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

LINQ kullanarak bu biraz daha temellerini yazmak için başka bir yolu şu şekildedir:

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
Bu daha az kod olsa da, LINQ ile zaman uyumsuz kod kullanırken dikkatli olun.  LINQ (lazy) ertelenmiş yürütme kullandığından, zaman uyumsuz çağrılar yapmasını hemen gerçekleşmez bir `foreach()` çağrısı ile yinelemek için oluşturulan sıralı zorla sürece döngü `.ToList()` veya `.ToArray()`.

## <a name="important-info-and-advice"></a>Önemli bilgiler ve öneriler

Zaman uyumsuz programlama oldukça basit olsa da, bazı ayrıntılar olduğu beklemeyen davranışı önlemek akılda tutulması gereken vardır.

*  `async` **yöntemleri olması gerekir bir** `await` **gövde anahtar sözcük veya hiçbir zaman verecek!**

Bu, göz önünde bulundurmanız önemlidir.  Varsa `await` gövdesinde kullanılmayan bir `async` yöntemi, bir uyarı üretir C# Derleyici olacaktır, ancak kod olacak derleyin ve normal bir yöntemi gibi çalıştırın.  Zaman uyumsuz yöntemi için C# Derleyici tarafından oluşturulan Durum makinesi herhangi bir şey yerine getirmeye olabilir değil olarak bu de son derece verimli olacaktır.

*   **"Async" soneki yazdığınız her zaman uyumsuz yöntem adı eklemeniz gerekir.**

. NET'te zaman uyumlu ve zaman uyumsuz yöntemleri daha kolay ayırt etmek için kullanılan kuraldır. Açıkça (örneğin, olay işleyicileri veya web denetleyici yöntemleri) kod tarafından çağrılan olmayan bazı yöntemler mutlaka geçerli değildir unutmayın. Bunlar açıkça kodunuz tarafından çağrılır değil, kendi adlandırma hakkında açık olan önemli değildir.

*   `async void` **yalnızca olay işleyicileri için kullanılmalıdır.**

`async void` olaylar, dönüş türleri olmadığı için çalışması zaman uyumsuz olay işleyicileri izin vermek için tek yolu (Bu nedenle yapılamıyor kullanım `Task` ve `Task<T>`). Başka bir kullanımını `async void` DOKUNUN model izlemez ve gibi kullanmak zor olabilir:

  *   Oluşturulan özel durumlar bir `async void` yöntemi bu yöntemi dışında yakalandı olamaz.
  *   `async void` yöntemleri test etmek çok zordur.
  *   `async void` çağırana zaman uyumsuz olarak bekleniyor olmayan yöntemleri hatalı yan etkilere neden olabilir.

*   **Zaman uyumsuz lambda ifadeleri LINQ ifadelerinde kullanırken dikkatli bir şekilde tread**

Lambda ifadeleri LINQ ertelenmiş yürütme kullanın, anlamı kod zaman kendisine beklediğiniz olmayan bir zaman yürütme bitiş. Bu görevleri engelleme giriş kolayca bir kilitlenmeyle doğru yazılmaz neden olabilir. Ayrıca, bu gibi zaman uyumsuz kod iç içe Ayrıca, daha zor kod yürütme ile ilgili nedeni zorlaştırabilir. Zaman uyumsuz ve LINQ güçlü ancak dikkatli bir şekilde ve mümkün olduğunca NET bir şekilde birlikte kullanılmalıdır.

*   **Görevleri bekler engelleyici olmayan bir şekilde kod yazın**

Geçerli iş parçacığı engelleme beklenecek bir yol bir görevin tamamlanmasını Kilitlenmeler ve bağlam engellenen iş parçacıkları neden olabilir ve önemli ölçüde daha karmaşık hata işleme gerektirebilir. Aşağıdaki tabloda engelleyici olmayan bir yolla görevlerde bekleyen ile uğraşmak konusunda rehberlik sağlar:

| Bunu kullanın... | Bunun yerine... | Bunu yapmak isteyen olduğunda |
| --- | --- | --- |
| `await` | `Task.Wait` veya `Task.Result` | Arka plan görevinin sonucunu alınıyor |
| `await Task.WhenAny` | `Task.WaitAny` | Bir görevi tamamlamak bekleniyor |
| `await Task.WhenAll` | `Task.WaitAll` | Tüm görevlerin tamamlanması bekleniyor |
| `await Task.Delay` | `Thread.Sleep` | Bir süre için bekleniyor |

*   **Durum bilgisi olan küçük kod yazma**

Genel nesnelerin veya belirli yöntemleri yürütme durumunu bağlı değilsiniz. Bunun yerine, yalnızca yöntemlerinin dönüş değerlerine bağlıdır. Neden?

  *   Kod nedeni hakkında daha kolay olacaktır.
  *   Kodu test etmek daha kolay olacaktır.
  *   Zaman uyumsuz ve eş zamanlı kod karıştırma kadar basittir.
  *   Yarış durumları genellikle tamamen önlenebilir.
  *   Dönüş değerlerine bağlı olarak, denetleyici zaman uyumsuz kodu basitleştirir.
  *   (Ekstra) gerçekten de bağımlılık ekleme ile çalışır.

Önerilen bir hedef tam veya neredeyse eksiksiz elde etmektir [başvuru saydamlık](https://en.wikipedia.org/wiki/Referential_transparency_%28computer_science%29) kodunuzda. Bunun yapılması, son derece tahmin edilebilir, sınanabilir ve sürdürülebilir bir kod temeli neden olur.

## <a name="other-resources"></a>Diğer Kaynaklar

* [Zaman uyumsuz ayrıntılı](../standard/async-in-depth.md) görevleri nasıl çalıştığı hakkında daha fazla bilgi sağlar.
* [Zaman uyumsuz programlama ile async ve await (C#)](../csharp/programming-guide/concepts/async/index.md)
* Lucian Wischik'ın [zaman uyumsuz altı önemli ipuçları](https://channel9.msdn.com/Series/Three-Essential-Tips-for-Async) zaman uyumsuz programlama için harika bir kaynaktır
