---
title: Zaman uyumsuz programlama
description: .NET Core tarafından sağlanan C# dil düzeyi zaman uyumsuz programlama modeli hakkında bilgi edinin.
author: cartermp
ms.date: 06/20/2016
ms.assetid: b878c34c-a78f-419e-a594-a2b44fa521a4
ms.openlocfilehash: b753b887da6f8836e0f4363a479c12c7364ea770
ms.sourcegitcommit: 895c7602386a6dfe7ca4facce3d965b27e5c6e87
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/19/2018
---
# <a name="asynchronous-programming"></a>Zaman uyumsuz programlama

Tüm g/Ç-bağlı gereksinimlerini (örneğin, ağ üzerinden veri isteme veya bir veritabanına erişirken) varsa, zaman uyumsuz programlama kullanmak istersiniz.  Zaman uyumsuz kod yazma için iyi bir senaryo aynı zamanda olan pahalı bir hesaplama gerçekleştirme gibi CPU bağımlı kod de olabilir.

C# kolayca geri çağırmaları juggle veya asynchrony destekleyen bir kitaplık uymak zorunda kalmadan zaman uyumsuz kod yazmak için izin veren bir dil düzeyi zaman uyumsuz programlama modeli vardır. Olarak bilinen izleyen [görev tabanlı zaman uyumsuz desen (TAP)](https://msdn.microsoft.com/library/hh873175.aspx).

## <a name="basic-overview-of-the-asynchronous-model"></a>Zaman uyumsuz modeline temel genel bakış

Zaman uyumsuz programlama çekirdek olan `Task` ve `Task<T>` zaman uyumsuz işlemleri model nesneleri.  Tarafından desteklenen `async` ve `await` anahtar sözcükler.  Model, çoğu durumda oldukça basittir: 

G/Ç-bağlı kodu için `await` döndüren bir işlem bir `Task` veya `Task<T>` içine bir `async` yöntemi.

CPU bağımlı kodu için `await` arka plan iş parçacığı ile başlatılan bir işlem `Task.Run` yöntemi.

`await` Sözcüktür burada Sihirli olur. Gerçekleştirilen yöntemi çağırana denetim verir `await`, ve sonuçta bir kullanıcı Arabirimi yanıt vermesi veya esnek olması için bir hizmet sağlar.

Diğer yolla yaklaşım zaman uyumsuz koduna `async` ve `await` yukarıdaki bağlı DOKUNUN makalesinde özetlenen, ancak bu belgede bu noktadan dil düzeyi yapıları üzerine odaklanacaktır.

### <a name="io-bound-example-downloading-data-from-a-web-service"></a>G/Ç-bağlı örnek: bir web hizmetinden veri indirme

Bir düğmeye basıldığında bazı verileri bir web hizmetinden yüklemeniz gerekebilir, ancak kullanıcı Arabirimi iş parçacığı engellemek istediğiniz yok. Yalnızca bu gibi gerçekleştirilebilir:

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

Ve bu kadar! Kod görev nesnelerle etkileşim çıkmaza olmadan (bazı verileri zaman uyumsuz olarak indirme) hedefi ifade eder.

### <a name="cpu-bound-example-performing-a-calculation-for-a-game"></a>CPU bağımlı örnek: bir oyun için bir hesaplama gerçekleştirme

Burada bir düğmesine basarak hasar ekranında birçok enemies üzerinde verebilecek mobil oyun yazıyorsanız söyleyin.  Hasar hesaplama gerçekleştirme pahalı olabilir ve kullanıcı Arabirimi iş parçacığı üzerinde yapmakta hesaplama gerçekleştirilir gibi duraklatmak için görünür oyun yapacağı!

Bu durumu çözmek için en iyi yolu kullanarak iş yapan bir arka plan iş parçacığı başlatmaktır `Task.Run`, ve `await` sonucu.  Bu iş gerçekleştirilir gibi kesintisiz eşitleyerek için kullanıcı Arabirimi sağlar.

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

Ve bu kadar!  Bu kod düzgün bir şekilde amacı ifade düğmenin olay'ı tıklatın, bir arka plan iş parçacığı el ile yönetme gerektirmez ve bunu engelleyici olmayan bir biçimde yapar.

### <a name="what-happens-under-the-covers"></a>Perde arkasında ne olur?

Zaman uyumsuz işlemleri burada ilgilenir taşıma parçaları çok yoktur.  İç in gerçekleştiği hakkında merak `Task` ve `Task<T>`, checkout [zaman uyumsuz ayrıntılı](../standard/async-in-depth.md) daha fazla bilgi için makalenin.

C# tarafında nesnelerin interneti derleyici kodunuzu yürütme sağlayan gibi şeyler ve bir durum makinesinin dönüştüren olduğunda bir `await` arka plan işi sona erdiğinde ulaştı ve devam ettirme yürütme ediyor.

Teorik olarak-inclined için bu bir uygulamasıdır [asynchrony Promise modelinin](https://en.wikipedia.org/wiki/Futures_and_promises).

## <a name="key-pieces-to-understand"></a>Anlamak için temel parçalar

*   Zaman uyumsuz kodu için kod g/Ç-bağlı ve CPU bağımlı, ancak farklı her senaryo için kullanılabilir.
*   Zaman uyumsuz kodu kullanan `Task<T>` ve `Task`, arka planda gerçekleştirilen modeli çalışmak için kullanılan yapılar olduğu.
* `async` Anahtar sözcüğü bir yöntem kullanmanıza olanak sağlayan bir zaman uyumsuz yöntem kapatır `await` kendi gövdesindeki anahtar sözcüğü.
*   Zaman `await` anahtar sözcüğü uygulandığında, çağrıyı yapan yöntemini askıya alır ve awaited görevi tamamlanana kadar geri çağırıcısına denetim verir.
*   `await` yalnızca bir zaman uyumsuz yöntem içinde kullanılabilir.

## <a name="recognize-cpu-bound-and-io-bound-work"></a>CPU bağımlı ve g/Ç-bağlı iş tanı

Bu kılavuzun ilk iki örnek gösterdi nasıl kullanacağınızı `async` ve `await` g/Ç-bağlı ve CPU bağımlı iş için.  Bir işi yapmak gereksinim duyduğunuzda, tanımlayabilirsiniz, g/Ç-bağlı veya CPU bağımlı anahtarıdır, kodunuzu performansını önemli ölçüde etkileyebilir ve büyük olasılıkla olabilir çünkü kötüye adayı belirli oluşturur.

Herhangi bir kod yazmadan önce istemelisiniz iki sorular şunlardır:

1. Kodunuzu "bir veritabanındaki verileri gibi şeyler bekliyor olabilir"?

    "Evet" aradığınız cevaptır sonra iş **g/Ç-bağlı**.

2. Kodunuzu çok pahalı bir hesaplama gerçekleştirecekseniz?

    "Evet" yanıtlanan sonra iş **CPU bağımlı**.
    
Sahip olduğunuz iş ise **g/Ç-bağlı**, kullanın `async` ve `await` *olmadan* `Task.Run`.  *Vermemelisiniz* görev paralel kitaplığı kullanın.  Bunun nedeni kısmında özetlenen [zaman uyumsuz derinliği makalede](../standard/async-in-depth.md).

Sahip olduğunuz iş ise **CPU bağımlı** ve yanıtlama hakkında kullanım verdiğiniz `async` ve `await` ancak başka bir iş parçacığında İş dışı oluşturma *ile* `Task.Run`.  İş eşzamanlılığı ve paralellik için uygun değilse, görev paralel kitaplığı kullanmayı da düşünmeniz gerekir.

Ayrıca, her zaman kodunuzun yürütülmesini ölçmek.  Örneğin, kendiniz CPU bağımlı iş olduğu pahalı bir durumda bulabilirsiniz İçerik Geçişi çoklu iş parçacığı kullanımı zaman yüküyle yeterince karşılaştırılan.  Her seçenek kendi kolaylığını var ve durumunuz için doğru kolaylığını seçmeniz gerekir.

## <a name="more-examples"></a>Daha fazla örnek

Aşağıdaki örnekler, zaman uyumsuz kod C# dilinde yazabilirsiniz çeşitli yolları gösterir.  Bunlar arasında gelebilir birkaç farklı senaryolar kapsar.

### <a name="extracting-data-from-a-network"></a>Ağ üzerinden veri çıkarma

Bu kod parçacığında www.dotnetfoundation.org HTML indirir ve HTML dizesi ".NET" oluşur kez sayar.  ASP.NET MVC sayısı, bu görevi gerçekleştiren bir web denetleyicisi yöntemi tanımlamak için kullanır.

> [!NOTE]
> HTML üretim kodunda ayrıştırma yapmayı planlıyorsanız, normal ifadeler kullanmayın. Bunun yerine bir ayrıştırma kitaplığını kullanın.

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

### <a name="waiting-for-multiple-tasks-to-complete"></a>Birden fazla görevin tamamlanmasını bekliyor

Kendinizi eşzamanlı olarak birden çok veri parçalarını almanıza gerek olduğu bir durumda bulabilirsiniz.  `Task` API'yi içeren iki yöntem `Task.WhenAll` ve `Task.WhenAny` birden fazla arka plan işleri engelleyici olmayan bir bekleme gerçekleştiren zaman uyumsuz kod yazmayı izin.

Bu örnek nasıl yakalayın gösterir `User` veri kümesi için `userId`s.

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

LINQ kullanarak bu biraz daha temellerini yazmak için başka bir yolu şöyledir:

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
Daha az kod olmasına rağmen zaman uyumsuz koduyla LINQ karıştırma zaman dikkatli olun.  LINQ ertelenmiş (yavaş) yürütme kullandığından, zaman uyumsuz çağrıları göründükleri hemen gerçekleşmez bir `foreach()` çağrısıyla yinelemek için oluşturulan sıra zorlama sürece döngü `.ToList()` veya `.ToArray()`.

## <a name="important-info-and-advice"></a>Önemli bilgiler ve öneriler

Zaman uyumsuz programlama görece basit olsa da, bazı ayrıntılar beklenmeyen davranışları önleyebilir göz önünde bulundurmanız vardır.

*  `async` **yöntemleri olması gerekir bir** `await` **kendi gövdesindeki anahtar sözcüğü veya hiçbir zaman sunacak!**

Bu, göz önünde bulundurmanız önemlidir.  Varsa `await` gövdesinde kullanılmayan bir `async` yöntemi, bir uyarı üretir C# Derleyici olacaktır, ancak derleme ve normal bir yöntem değilmiş gibi çalıştırma kodu olacaktır.  Async yöntemi için C# Derleyici tarafından oluşturulan Durum makinesi herhangi bir şey gerçekleştirmeye olabilir değil olarak bu de son derece verimli olacaktır.

*   **Yazdığınız her zaman uyumsuz yöntem adı son eki olarak "Zaman uyumsuz" eklemeniz gerekir.**

Bu, .NET içinde daha kolayca zaman uyumlu ve zaman uyumsuz yöntemleri ayırdetmek için kullanılan kuraldır. Kodunuzu (örneğin, olay işleyicileri veya web denetleyicisi yöntemleri) tarafından açıkça çağrılan olmayan bazı yöntemleri mutlaka uygulanmaz unutmayın. Bunlar açıkça kodunuz tarafından adlandırılır değil çünkü bunların adlandırma hakkında açık olması önemli değildir.

*   `async void` **yalnızca olay işleyicileri için kullanılmalıdır.**

`async void` olaylar, dönüş türleri olmadığı için çalışması zaman uyumsuz olay işleyicileri izin vermek için tek yolu (Bu nedenle yapılamıyor kullanımı `Task` ve `Task<T>`). Diğer bir kullanımını `async void` DOKUNUN model izlemez ve gibi kullanmak için zor olabilir:

  *   Oluşturulan özel durumları bir `async void` yöntemi bu yöntemi dışında yakalanan olamaz.
  *   `async void` test etmek oldukça zor yöntemleridir.
  *   `async void` Arayan bunları zaman uyumsuz olarak bekleniyor değil, yöntemleri hatalı yan etkileri neden olabilir.

*   **Zaman uyumsuz Lambda'lar LINQ ifadelerinde kullanırken dikkatle tread**

Ertelenmiş yürütme LINQ lambda ifadeleri kullanma, anlamı kod zaman kendisine beklediğiniz olmayan bir anda yürütülmekte end. Bu görevleri engelleme giriş kolayca bir kilitlenmeyle doğru yazılmaz neden olabilir. Ayrıca, zaman uyumsuz kod bu gibi iç içe ayrıca daha kodunun yürütülmesini hakkında nedeni zorlaştırabilir. Zaman uyumsuz ve LINQ güçlüdür ancak dikkatle ve mümkün olduğunca açıkça olarak birlikte kullanılmalıdır.

*   **Engelleyici olmayan bir biçimde görevleri bekler kod yazma**

Geçerli iş parçacığının beklemek için bir yol engelleme tamamlamak bir görev için Kilitlenmeler ve engellenen bağlam iş parçacığı neden olabilir ve önemli ölçüde daha karmaşık hata işleme gerektirebilir. Aşağıdaki tabloda engelleyici olmayan bir biçimde görevler için bekleyen ile ilgilidir hakkında yönergeler sağlar:

| Bu kullan... | Bunun yerine... | Bunu yapmak isteyen olduğunda |
| --- | --- | --- |
| `await` | `Task.Wait` Veya `Task.Result` | Bir arka plan görevi sonucunu alınıyor |
| `await Task.WhenAny` | `Task.WaitAny` | Tamamlamak herhangi bir görev için bekleniyor |
| `await Task.WhenAll` | `Task.WaitAll` | Tüm görevlerin tamamlanması bekleniyor |
| `await Task.Delay` | `Thread.Sleep` | Bir süre için bekleniyor |

*   **Durum bilgisi olan daha az kod yazma**

Genel nesne veya belirli yöntemlerini yürütülmesi durumuna bağlı yok. Bunun yerine, yalnızca yöntemleri dönüş değerlerine bağlıdır. Neden?

  *   Kod nedeni hakkında daha kolay olacaktır.
  *   Kodu test etmek daha kolay olacaktır.
  *   Zaman uyumsuz ve zaman uyumlu bir kod karıştırma kadar basittir.
  *   Yarış durumları genellikle tamamen önlenebilir.
  *   Dönüş değerleri bağlı olarak, denetleyici zaman uyumsuz kod basit hale getirir.
  *   (Prim) gerçekten de bağımlılık ekleme ile çalışır.

Tam ya da yakın tamamlamak elde etmek için önerilen bir hedefi olan [başvuru saydamlık](https://en.wikipedia.org/wiki/Referential_transparency_%28computer_science%29) kodunuzda. Bunun yapılması bir son derece tahmin edilebilir, sınanabilir ve sürdürülebilir codebase neden olur.

## <a name="other-resources"></a>Diğer Kaynaklar

* [Zaman uyumsuz ayrıntılı](../standard/async-in-depth.md) görevlerin nasıl çalıştığı hakkında daha fazla bilgi sağlar.
* [Zaman uyumsuz programlama ile async ve await (C#)](../csharp/programming-guide/concepts/async/index.md)
* Lucian Wischik'ın [zaman uyumsuz altı önemli ipuçları](https://channel9.msdn.com/Series/Three-Essential-Tips-for-Async) zaman uyumsuz programlama için harika bir kaynaktır
