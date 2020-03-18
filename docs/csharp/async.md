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
# <a name="asynchronous-programming"></a><span data-ttu-id="602fe-103">Zaman uyumsuz programlama</span><span class="sxs-lookup"><span data-stu-id="602fe-103">Asynchronous programming</span></span>

<span data-ttu-id="602fe-104">G/Ç'ye bağlı gereksinimleriniz varsa (ağdan veri istemek veya veritabanına erişmek gibi), eşzamanlı programlamadan yararlanmak istersiniz.</span><span class="sxs-lookup"><span data-stu-id="602fe-104">If you have any I/O-bound needs (such as requesting data from a network or accessing a database), you'll want to utilize asynchronous programming.</span></span>  <span data-ttu-id="602fe-105">Ayrıca, async kodu yazmak için de iyi bir senaryo olan pahalı bir hesaplama yapmak gibi CPU'ya bağlı kodunuz da olabilir.</span><span class="sxs-lookup"><span data-stu-id="602fe-105">You could also have CPU-bound code, such as performing an expensive calculation, which is also a good scenario for writing async code.</span></span>

<span data-ttu-id="602fe-106">C#, geri aramaları hokkabazlık yapmak veya eşzamanlılığı destekleyen bir kitaplıkla uyumluluk sağlamak zorunda kalmadan asynchronous kodu kolayca yazmanızı sağlayan bir dil düzeyinde eşzamanlı programlama modeline sahiptir.</span><span class="sxs-lookup"><span data-stu-id="602fe-106">C# has a language-level asynchronous programming model which allows for easily writing asynchronous code without having to juggle callbacks or conform to a library which supports asynchrony.</span></span> <span data-ttu-id="602fe-107">[Görev tabanlı Eşzamanlı Desen (TAP)](../standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md)olarak bilinen şeyi izler.</span><span class="sxs-lookup"><span data-stu-id="602fe-107">It follows what is known as the [Task-based Asynchronous Pattern (TAP)](../standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md).</span></span>

## <a name="basic-overview-of-the-asynchronous-model"></a><span data-ttu-id="602fe-108">Eşzamanlı Modele Temel Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="602fe-108">Basic Overview of the Asynchronous Model</span></span>

<span data-ttu-id="602fe-109">Async programlamanın özü, `Task` eşzamanlı `Task<T>` işlemleri modelleyen nesnelerdir.</span><span class="sxs-lookup"><span data-stu-id="602fe-109">The core of async programming is the `Task` and `Task<T>` objects, which model asynchronous operations.</span></span>  <span data-ttu-id="602fe-110">Bunlar `async` ve `await` anahtar kelimeler tarafından desteklenir.</span><span class="sxs-lookup"><span data-stu-id="602fe-110">They are supported by the `async` and `await` keywords.</span></span>  <span data-ttu-id="602fe-111">Model çoğu durumda oldukça basittir:</span><span class="sxs-lookup"><span data-stu-id="602fe-111">The model is fairly simple in most cases:</span></span>

<span data-ttu-id="602fe-112">G/Ç bağlı kod için, bir yöntemin `Task<T>` bir `Task` `async` veya içinde döndüren bir işlem. `await`</span><span class="sxs-lookup"><span data-stu-id="602fe-112">For I/O-bound code, you `await` an operation which returns a `Task` or `Task<T>` inside of an `async` method.</span></span>

<span data-ttu-id="602fe-113">CPU'ya bağlı kod `await` için, `Task.Run` yöntemle arka plan iş parçacığı üzerinde başlatılan bir işlem.</span><span class="sxs-lookup"><span data-stu-id="602fe-113">For CPU-bound code, you `await` an operation which is started on a background thread with the `Task.Run` method.</span></span>

<span data-ttu-id="602fe-114">Anahtar `await` kelime sihrin gerçekleştiği yerdir.</span><span class="sxs-lookup"><span data-stu-id="602fe-114">The `await` keyword is where the magic happens.</span></span> <span data-ttu-id="602fe-115">Gerçekleştirilen `await`yöntemin arayana denetim verir ve sonuçta bir Kullanıcı Aracı'nın yanıt vermesini veya bir hizmetin esnek olmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="602fe-115">It yields control to the caller of the method that performed `await`, and it ultimately allows a UI to be responsive or a service to be elastic.</span></span>

<span data-ttu-id="602fe-116">Async koduna yukarıda bağlanan `async` `await` TAP makalesinde belirtilenden daha fazla yaklaşmanın başka yolları da vardır, ancak bu belge bu noktadan itibaren dil düzeyindeki yapılara odaklanacaktır.</span><span class="sxs-lookup"><span data-stu-id="602fe-116">There are other ways to approach async code than `async` and `await` outlined in the TAP article linked above, but this document will focus on the language-level constructs from this point forward.</span></span>

### <a name="io-bound-example-downloading-data-from-a-web-service"></a><span data-ttu-id="602fe-117">G/O-Bound Örnek: Bir web hizmetinden veri indirme</span><span class="sxs-lookup"><span data-stu-id="602fe-117">I/O-Bound Example: Downloading data from a web service</span></span>

<span data-ttu-id="602fe-118">Bir düğmeye basıldığında bir web hizmetinden bazı verileri indirmeniz gerekebilir, ancak Web Bilgisi iş parçacığının engellenmesini istemezsiniz.</span><span class="sxs-lookup"><span data-stu-id="602fe-118">You may need to download some data from a web service when a button is pressed, but don’t want to block the UI thread.</span></span> <span data-ttu-id="602fe-119">Bu sadece bu şekilde gerçekleştirilebilir:</span><span class="sxs-lookup"><span data-stu-id="602fe-119">It can be accomplished simply like this:</span></span>

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

<span data-ttu-id="602fe-120">Hepsi bu!</span><span class="sxs-lookup"><span data-stu-id="602fe-120">And that’s it!</span></span> <span data-ttu-id="602fe-121">Kod, Görev nesneleri ile etkileşimde çıkmaza girmeden amacı (bazı verileri eşit olarak indirme) ifade eder.</span><span class="sxs-lookup"><span data-stu-id="602fe-121">The code expresses the intent (downloading some data asynchronously) without getting bogged down in interacting with Task objects.</span></span>

### <a name="cpu-bound-example-performing-a-calculation-for-a-game"></a><span data-ttu-id="602fe-122">CPU'ya bağlı Örnek: Oyun Için Hesaplama Yapmak</span><span class="sxs-lookup"><span data-stu-id="602fe-122">CPU-bound Example: Performing a Calculation for a Game</span></span>

<span data-ttu-id="602fe-123">Bir düğmeye basarak ekrandaki birçok düşmana zarar verebileceği bir mobil oyun yazdığınızı varsan.</span><span class="sxs-lookup"><span data-stu-id="602fe-123">Say you're writing a mobile game where pressing a button can inflict damage on many enemies on the screen.</span></span>  <span data-ttu-id="602fe-124">Hasar hesaplaması yapmak pahalı olabilir ve bunu UI iş parçacığı üzerinde yapmak, hesaplama yapıldıkça oyunun duraklatma sını durdurur!</span><span class="sxs-lookup"><span data-stu-id="602fe-124">Performing the damage calculation can be expensive, and doing it on the UI thread would make the game appear to pause as the calculation is performed!</span></span>

<span data-ttu-id="602fe-125">Bunu işlemenin en iyi yolu, `Task.Run` `await` işi ve sonucunu kullanarak yapan bir arka plan iş parçacığı başlatmaktır.</span><span class="sxs-lookup"><span data-stu-id="602fe-125">The best way to handle this is to start a background thread which does the work using `Task.Run`, and `await` its result.</span></span>  <span data-ttu-id="602fe-126">Bu, iş yapılırken UI'nin kendinizi sorunsuz hissetmesini sağlayacaktır.</span><span class="sxs-lookup"><span data-stu-id="602fe-126">This will allow the UI to feel smooth as the work is being done.</span></span>

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

<span data-ttu-id="602fe-127">Hepsi bu!</span><span class="sxs-lookup"><span data-stu-id="602fe-127">And that's it!</span></span>  <span data-ttu-id="602fe-128">Bu kod, düğmenin tıklama olayının amacını temiz bir şekilde ifade eder, bir arka plan iş parçacığının el ile yönetilmesini gerektirmez ve bunu engellemez bir şekilde yapar.</span><span class="sxs-lookup"><span data-stu-id="602fe-128">This code cleanly expresses the intent of the button's click event, it doesn't require managing a background thread manually, and it does so in a non-blocking way.</span></span>

### <a name="what-happens-under-the-covers"></a><span data-ttu-id="602fe-129">Örtülerin altında ne olur?</span><span class="sxs-lookup"><span data-stu-id="602fe-129">What happens under the covers</span></span>

<span data-ttu-id="602fe-130">Eşzamanlı operasyonların söz konusu olduğu bir sürü hareketli parça var.</span><span class="sxs-lookup"><span data-stu-id="602fe-130">There's a lot of moving pieces where asynchronous operations are concerned.</span></span>  <span data-ttu-id="602fe-131">Kapaklarının altında neler olup bittiğini merak `Task` ediyorsanız, `Task<T>`daha fazla bilgi için [Async derinlemesine](../standard/async-in-depth.md) makaleye göz atın.</span><span class="sxs-lookup"><span data-stu-id="602fe-131">If you're curious about what's happening underneath the covers of `Task` and `Task<T>`, checkout the [Async in-depth](../standard/async-in-depth.md) article for more information.</span></span>

<span data-ttu-id="602fe-132">Nesnelerin C# tarafında, derleyici kodunuzu bir arka plan işi tamamlandığında yürütmeverim `await` ve yürütme devam gibi şeyleri izleyen bir durum makinesine dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="602fe-132">On the C# side of things, the compiler transforms your code into a state machine which keeps track of things like yielding execution when an `await` is reached and resuming execution when a background job has finished.</span></span>

<span data-ttu-id="602fe-133">Teorik olarak eğimli için, bu [asynchrony Söz Modeli](https://en.wikipedia.org/wiki/Futures_and_promises)bir uygulamadır.</span><span class="sxs-lookup"><span data-stu-id="602fe-133">For the theoretically-inclined, this is an implementation of the [Promise Model of asynchrony](https://en.wikipedia.org/wiki/Futures_and_promises).</span></span>

## <a name="key-pieces-to-understand"></a><span data-ttu-id="602fe-134">Anlaşılması Gereken Anahtar Parçalar</span><span class="sxs-lookup"><span data-stu-id="602fe-134">Key Pieces to Understand</span></span>

* <span data-ttu-id="602fe-135">Async kodu hem I/O-bound hem de CPU'ya bağlı kod için kullanılabilir, ancak her senaryo için farklı.</span><span class="sxs-lookup"><span data-stu-id="602fe-135">Async code can be used for both I/O-bound and CPU-bound code, but differently for each scenario.</span></span>
* <span data-ttu-id="602fe-136">Async kodu `Task<T>` `Task`kullanır ve , arka planda yapılan işi modellemek için kullanılan yapılardır.</span><span class="sxs-lookup"><span data-stu-id="602fe-136">Async code uses `Task<T>` and `Task`, which are constructs used to model work being done in the background.</span></span>
* <span data-ttu-id="602fe-137">Anahtar `async` kelime, bir yöntemi, anahtar sözcüğü gövdesinde `await` kullanmanıza olanak tanıyan bir eşitleme yöntemine dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="602fe-137">The `async` keyword turns a method into an async method, which allows you to use the `await` keyword in its body.</span></span>
* <span data-ttu-id="602fe-138">`await` Anahtar kelime uygulandığında, arama yöntemini askıya eder ve beklenen görev tamamlanana kadar denetimi arayana geri verir.</span><span class="sxs-lookup"><span data-stu-id="602fe-138">When the `await` keyword is applied, it suspends the calling method and yields control back to its caller until the awaited task is complete.</span></span>
* <span data-ttu-id="602fe-139">`await`yalnızca bir async yöntemi içinde kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="602fe-139">`await` can only be used inside an async method.</span></span>

## <a name="recognize-cpu-bound-and-io-bound-work"></a><span data-ttu-id="602fe-140">CPU'ya Bağlı ve G/Ç Bağlı Çalışmayı Tanıyın</span><span class="sxs-lookup"><span data-stu-id="602fe-140">Recognize CPU-Bound and I/O-Bound Work</span></span>

<span data-ttu-id="602fe-141">Bu kılavuzun ilk iki örneği, `async` Nasıl `await` kullanabileceğinizi ve I/O-bound ve CPU'ya bağlı çalışmaları gösterdi.</span><span class="sxs-lookup"><span data-stu-id="602fe-141">The first two examples of this guide showed how you can use `async` and `await` for I/O-bound and CPU-bound work.</span></span>  <span data-ttu-id="602fe-142">Yapmanız gereken bir işin I/O'ya bağlı veya CPU'ya bağlı olduğunu belirleyebileceğiniz anahtardır, çünkü kodunuzu büyük ölçüde etkileyebilir ve bazı yapıları kötüye kullanmaya neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="602fe-142">It's key that you can identify when a job you need to do is I/O-bound or CPU-bound, because it can greatly affect the performance of your code and could potentially lead to misusing certain constructs.</span></span>

<span data-ttu-id="602fe-143">Herhangi bir kod yazmadan önce sormanız gereken iki soru şunlardır:</span><span class="sxs-lookup"><span data-stu-id="602fe-143">Here are two questions you should ask before you write any code:</span></span>

1. <span data-ttu-id="602fe-144">Kodunuz veritabanından alınan veriler gibi bir şey için "bekliyor" olacak mı?</span><span class="sxs-lookup"><span data-stu-id="602fe-144">Will your code be "waiting" for something, such as data from a database?</span></span>

    <span data-ttu-id="602fe-145">Cevabınız "evet" ise, o zaman iş **I / O-bağlı**.</span><span class="sxs-lookup"><span data-stu-id="602fe-145">If your answer is "yes", then your work is **I/O-bound**.</span></span>

2. <span data-ttu-id="602fe-146">Kodunuz çok pahalı bir hesaplama gerçekleştirecek mi?</span><span class="sxs-lookup"><span data-stu-id="602fe-146">Will your code be performing a very expensive computation?</span></span>

    <span data-ttu-id="602fe-147">"Evet" yanıtını verdiyseniz, işiniz **CPU'ya bağlıdır.**</span><span class="sxs-lookup"><span data-stu-id="602fe-147">If you answered "yes", then your work is **CPU-bound**.</span></span>

<span data-ttu-id="602fe-148">Sahip olduğunuz iş **I/O-bound** `async` ise, `await` kullanın ve *olmadan* `Task.Run`.</span><span class="sxs-lookup"><span data-stu-id="602fe-148">If the work you have is **I/O-bound**, use `async` and `await` *without* `Task.Run`.</span></span>  <span data-ttu-id="602fe-149">Görev Paralel Kitaplığı'nı *kullanmamalısınız.*</span><span class="sxs-lookup"><span data-stu-id="602fe-149">You *should not* use the Task Parallel Library.</span></span>  <span data-ttu-id="602fe-150">Bunun nedeni [Async in Depth makalesinde](../standard/async-in-depth.md)özetlenmiştir.</span><span class="sxs-lookup"><span data-stu-id="602fe-150">The reason for this is outlined in the [Async in Depth article](../standard/async-in-depth.md).</span></span>

<span data-ttu-id="602fe-151">Sahip olduğunuz iş **CPU'ya bağlıysa** ve yanıt `async` verme `await` işlemini önemsiyorsanız, ancak işi başka bir iş parçacığı üzerinde '' *ile* `Task.Run`yumurtlanın.</span><span class="sxs-lookup"><span data-stu-id="602fe-151">If the work you have is **CPU-bound** and you care about responsiveness, use `async` and `await` but spawn the work off on another thread *with* `Task.Run`.</span></span>  <span data-ttu-id="602fe-152">Çalışma eşzamanlılık ve paralellik için uygunsa, [Görev Paralel Kitaplığı'nı](../standard/parallel-programming/task-parallel-library-tpl.md)da kullanmayı düşünmelisiniz.</span><span class="sxs-lookup"><span data-stu-id="602fe-152">If the work is appropriate for concurrency and parallelism, you should also consider using the [Task Parallel Library](../standard/parallel-programming/task-parallel-library-tpl.md).</span></span>

<span data-ttu-id="602fe-153">Ayrıca, her zaman kodunuzu yürütme ölçmek gerekir.</span><span class="sxs-lookup"><span data-stu-id="602fe-153">Additionally, you should always measure the execution of your code.</span></span>  <span data-ttu-id="602fe-154">Örneğin, cpu'ya bağlı çalışmanızın, çok iş parçacığı yaparken bağlam anahtarlarının yüküyle karşılaştırıldığında yeterince maliyetli olmadığı bir durumda bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="602fe-154">For example, you may find yourself in a situation where your CPU-bound work is not costly enough compared with the overhead of context switches when multithreading.</span></span>  <span data-ttu-id="602fe-155">Her seçimin bir dengelemesi vardır ve durumunuz için doğru dengelemeyi seçmelisiniz.</span><span class="sxs-lookup"><span data-stu-id="602fe-155">Every choice has its tradeoff, and you should pick the correct tradeoff for your situation.</span></span>

## <a name="more-examples"></a><span data-ttu-id="602fe-156">Diğer Örnekler</span><span class="sxs-lookup"><span data-stu-id="602fe-156">More Examples</span></span>

<span data-ttu-id="602fe-157">Aşağıdaki örnekler, C#'a async kodu yazabileceğiniz çeşitli yolları göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="602fe-157">The following examples demonstrate various ways you can write async code in C#.</span></span>  <span data-ttu-id="602fe-158">Karşılaşabileceğiniz birkaç farklı senaryoyu kapsıyor.</span><span class="sxs-lookup"><span data-stu-id="602fe-158">They cover a few different scenarios you may come across.</span></span>

### <a name="extracting-data-from-a-network"></a><span data-ttu-id="602fe-159">Ağdan Veri Çıkarma</span><span class="sxs-lookup"><span data-stu-id="602fe-159">Extracting Data from a Network</span></span>

<span data-ttu-id="602fe-160">Bu parçacık, HTML'yi ana sayfadan [www.dotnetfoundation.org](https://www.dotnetfoundation.org) indirir ve HTML'de ".NET" dizesinin kaç kez oluştuğunu sayar.</span><span class="sxs-lookup"><span data-stu-id="602fe-160">This snippet downloads the HTML from the homepage at [www.dotnetfoundation.org](https://www.dotnetfoundation.org) and counts the number of times the string ".NET" occurs in the HTML.</span></span>  <span data-ttu-id="602fe-161">Bu sayıyı döndürerek, bu görevi gerçekleştiren bir web denetleyici yöntemi tanımlamak için ASP.NET MVC kullanır.</span><span class="sxs-lookup"><span data-stu-id="602fe-161">It uses ASP.NET MVC to define a web controller method which performs this task, returning the number.</span></span>

> [!NOTE]
> <span data-ttu-id="602fe-162">Üretim kodunda HTML ayrıştması yapmayı planlıyorsanız, normal ifadeler kullanmayın.</span><span class="sxs-lookup"><span data-stu-id="602fe-162">If you plan on doing HTML parsing in production code, don't use regular expressions.</span></span> <span data-ttu-id="602fe-163">Bunun yerine ayrıştma kitaplığı kullanın.</span><span class="sxs-lookup"><span data-stu-id="602fe-163">Use a parsing library instead.</span></span>

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

<span data-ttu-id="602fe-164">Bir Düğmeye basıldığında aynı görevi gerçekleştiren Evrensel Windows Uygulaması için yazılmış aynı senaryo aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="602fe-164">Here's the same scenario written for a Universal Windows App, which performs the same task when a Button is pressed:</span></span>

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

### <a name="waiting-for-multiple-tasks-to-complete"></a><span data-ttu-id="602fe-165">Birden Çok Görevin Tamamlanmasını Bekliyor</span><span class="sxs-lookup"><span data-stu-id="602fe-165">Waiting for Multiple Tasks to Complete</span></span>

<span data-ttu-id="602fe-166">Aynı anda birden çok veri parçası almanız gereken bir durumda bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="602fe-166">You may find yourself in a situation where you need to retrieve multiple pieces of data concurrently.</span></span>  <span data-ttu-id="602fe-167">`Task` API iki `Task.WhenAll` yöntem içerir `Task.WhenAny` ve birden çok arka plan işleri üzerinde engelleyici olmayan bir bekleme gerçekleştiren eşzamanlı kod yazmak için izin verir.</span><span class="sxs-lookup"><span data-stu-id="602fe-167">The `Task` API contains two methods, `Task.WhenAll` and `Task.WhenAny` which allow you to write asynchronous code which performs a non-blocking wait on multiple background jobs.</span></span>

<span data-ttu-id="602fe-168">Bu örnek, bir `User` s kümesi için `userId`verileri nasıl kapabileceğinizi gösterir.</span><span class="sxs-lookup"><span data-stu-id="602fe-168">This example shows how you might grab `User` data for a set of `userId`s.</span></span>

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

<span data-ttu-id="602fe-169">LinQ kullanarak bunu biraz daha kısa yazmanın başka bir yolu daha var:</span><span class="sxs-lookup"><span data-stu-id="602fe-169">Here's another way to write this a bit more succinctly, using LINQ:</span></span>

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

<span data-ttu-id="602fe-170">Daha az kod olmasına rağmen, LINQ'u eşzamanlı kodla karıştırırken dikkatli olsun.</span><span class="sxs-lookup"><span data-stu-id="602fe-170">Although it's less code, take care when mixing LINQ with asynchronous code.</span></span>  <span data-ttu-id="602fe-171">LINQ ertelenmiş (tembel) yürütme kullandığından, `foreach()` oluşturulan sırayı bir çağrıyla `.ToList()` veya . `.ToArray()`</span><span class="sxs-lookup"><span data-stu-id="602fe-171">Because LINQ uses deferred (lazy) execution, async calls won't happen immediately as they do in a `foreach()` loop unless you force the generated sequence to iterate with a call to `.ToList()` or `.ToArray()`.</span></span>

## <a name="important-info-and-advice"></a><span data-ttu-id="602fe-172">Önemli Bilgi ve Öneriler</span><span class="sxs-lookup"><span data-stu-id="602fe-172">Important Info and Advice</span></span>

<span data-ttu-id="602fe-173">Async programlama nispeten basit olmasına rağmen, beklenmeyen davranışı önleyebilir akılda tutulması gereken bazı ayrıntılar vardır.</span><span class="sxs-lookup"><span data-stu-id="602fe-173">Although async programming is relatively straightforward, there are some details to keep in mind which can prevent unexpected behavior.</span></span>

* <span data-ttu-id="602fe-174">`async`**yöntemleri** `await` kendi vücudunda bir anahtar kelime olması gerekir **ya da asla verim olmaz!**</span><span class="sxs-lookup"><span data-stu-id="602fe-174">`async` **methods need to have an** `await` **keyword in their body or they will never yield!**</span></span>

<span data-ttu-id="602fe-175">Bu akılda tutulması gereken önemlidir.</span><span class="sxs-lookup"><span data-stu-id="602fe-175">This is important to keep in mind.</span></span>  <span data-ttu-id="602fe-176">Bir `await` `async` yöntemin gövdesinde kullanılmazsa, C# derleyicisi bir uyarı oluşturur, ancak kod normal bir yöntemgibi derlenir ve çalışır.</span><span class="sxs-lookup"><span data-stu-id="602fe-176">If `await` is not used in the body of an `async` method, the C# compiler will generate a warning, but the code will compile and run as if it were a normal method.</span></span>  <span data-ttu-id="602fe-177">Async yöntemi için C# derleyicisi tarafından oluşturulan durum makinesi bir şey başarmak olmaz gibi bu da inanılmaz verimsiz olacağını unutmayın.</span><span class="sxs-lookup"><span data-stu-id="602fe-177">Note that this would also be incredibly inefficient, as the state machine generated by the C# compiler for the async method would not be accomplishing anything.</span></span>

* <span data-ttu-id="602fe-178">**Yazdığınız her async yöntem adının sonek olarak "Async" eklemeniz gerekir.**</span><span class="sxs-lookup"><span data-stu-id="602fe-178">**You should add "Async" as the suffix of every async method name you write.**</span></span>

<span data-ttu-id="602fe-179">Bu, .NET'te senkron ve eşzamanlı yöntemleri daha kolay ayırt etmek için kullanılan kuraldır.</span><span class="sxs-lookup"><span data-stu-id="602fe-179">This is the convention used in .NET to more-easily differentiate synchronous and asynchronous methods.</span></span> <span data-ttu-id="602fe-180">Kodunuz tarafından açıkça çağrılmadı belirli yöntemlerin (olay işleyicileri veya web denetleyici yöntemleri gibi) mutlaka geçerli olmadığını unutmayın.</span><span class="sxs-lookup"><span data-stu-id="602fe-180">Note that certain methods which aren’t explicitly called by your code (such as event handlers or web controller methods) don’t necessarily apply.</span></span> <span data-ttu-id="602fe-181">Bunlar kodunuzun açıkça çağrılmadığından, adlandırmaları hakkında açık olmak o kadar da önemli değildir.</span><span class="sxs-lookup"><span data-stu-id="602fe-181">Because these are not explicitly called by your code, being explicit about their naming isn’t as important.</span></span>

* <span data-ttu-id="602fe-182">`async void`**yalnızca olay işleyicileri için kullanılmalıdır.**</span><span class="sxs-lookup"><span data-stu-id="602fe-182">`async void` **should only be used for event handlers.**</span></span>

<span data-ttu-id="602fe-183">`async void`olaylar dönüş türleri olmadığından (bu nedenle kullanamaz `Task` ve). `Task<T>`</span><span class="sxs-lookup"><span data-stu-id="602fe-183">`async void` is the only way to allow asynchronous event handlers to work because events do not have return types (thus cannot make use of `Task` and `Task<T>`).</span></span> <span data-ttu-id="602fe-184">Diğer kullanımlar `async void` TAP modelini izlemez ve aşağıdakiler gibi kullanımı zor olabilir:</span><span class="sxs-lookup"><span data-stu-id="602fe-184">Any other use of `async void` does not follow the TAP model and can be challenging to use, such as:</span></span>

* <span data-ttu-id="602fe-185">Bir `async void` yöntemde atılan özel durumlar bu yöntemin dışına yakalanamaz.</span><span class="sxs-lookup"><span data-stu-id="602fe-185">Exceptions thrown in an `async void` method can’t be caught outside of that method.</span></span>
* <span data-ttu-id="602fe-186">`async void`yöntemleri test etmek çok zordur.</span><span class="sxs-lookup"><span data-stu-id="602fe-186">`async void` methods are very difficult to test.</span></span>
* <span data-ttu-id="602fe-187">`async void`arayan kişinin uyumlu olmasını beklemiyorsa, yöntemler kötü yan etkilere neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="602fe-187">`async void` methods can cause bad side effects if the caller isn’t expecting them to be async.</span></span>

* <span data-ttu-id="602fe-188">**LINQ ifadelerinde async lambdas kullanırken dikkatli bir şekilde tread**</span><span class="sxs-lookup"><span data-stu-id="602fe-188">**Tread carefully when using async lambdas in LINQ expressions**</span></span>

<span data-ttu-id="602fe-189">LINQ'daki Lambda ifadeleri ertelenmiş yürütmeyi kullanır, yani kod, beklemediğiniz bir zamanda yürütülebilir.</span><span class="sxs-lookup"><span data-stu-id="602fe-189">Lambda expressions in LINQ use deferred execution, meaning code could end up executing at a time when you’re not expecting it to.</span></span> <span data-ttu-id="602fe-190">Bu içine engelleme görevleri giriş kolayca doğru yazılmamışsa bir kilitlenme neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="602fe-190">The introduction of blocking tasks into this can easily result in a deadlock if not written correctly.</span></span> <span data-ttu-id="602fe-191">Ayrıca, bu gibi eşsenkron kodun iç içe geçmede, kodun yürütülmesi hakkında neden daha zor hale getirebilir.</span><span class="sxs-lookup"><span data-stu-id="602fe-191">Additionally, the nesting of asynchronous code like this can also make it more difficult to reason about the execution of the code.</span></span> <span data-ttu-id="602fe-192">Async ve LINQ güçlüdür, ancak mümkün olduğunca dikkatli ve net bir şekilde birlikte kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="602fe-192">Async and LINQ are powerful, but should be used together as carefully and clearly as possible.</span></span>

* <span data-ttu-id="602fe-193">**Görevleri engellemeyen bir şekilde bekleyen kod yazma**</span><span class="sxs-lookup"><span data-stu-id="602fe-193">**Write code that awaits Tasks in a non-blocking manner**</span></span>

<span data-ttu-id="602fe-194">Bir Görevin tamamlanmasını beklemek için geçerli iş parçacığının engellenmesi kilitlenmelere ve engellenmiş bağlam iş parçacıklarına neden olabilir ve önemli ölçüde daha karmaşık hata işleme gerektirebilir.</span><span class="sxs-lookup"><span data-stu-id="602fe-194">Blocking the current thread as a means to wait for a Task to complete can result in deadlocks and blocked context threads, and can require significantly more complex error-handling.</span></span> <span data-ttu-id="602fe-195">Aşağıdaki tablo, Görevleri engellemeyen bir şekilde beklemeyle nasıl başa çıkılalalalalabilmek konusunda kılavuz sağlar:</span><span class="sxs-lookup"><span data-stu-id="602fe-195">The following table provides guidance on how to deal with waiting for Tasks in a non-blocking way:</span></span>

| <span data-ttu-id="602fe-196">Bunu kullanın...</span><span class="sxs-lookup"><span data-stu-id="602fe-196">Use this...</span></span> | <span data-ttu-id="602fe-197">Bunun yerine...</span><span class="sxs-lookup"><span data-stu-id="602fe-197">Instead of this...</span></span> | <span data-ttu-id="602fe-198">Bunu yapmak isteyen</span><span class="sxs-lookup"><span data-stu-id="602fe-198">When wishing to do this</span></span> |
| --- | --- | --- |
| `await` | <span data-ttu-id="602fe-199">`Task.Wait` veya `Task.Result`</span><span class="sxs-lookup"><span data-stu-id="602fe-199">`Task.Wait` or `Task.Result`</span></span> | <span data-ttu-id="602fe-200">Arka plan görevinin sonucunu alma</span><span class="sxs-lookup"><span data-stu-id="602fe-200">Retrieving the result of a background task</span></span> |
| `await Task.WhenAny` | `Task.WaitAny` | <span data-ttu-id="602fe-201">Herhangi bir görevin tamamlanmasını bekliyorum</span><span class="sxs-lookup"><span data-stu-id="602fe-201">Waiting for any task to complete</span></span> |
| `await Task.WhenAll` | `Task.WaitAll` | <span data-ttu-id="602fe-202">Tüm görevlerin tamamlanmasını bekliyorum</span><span class="sxs-lookup"><span data-stu-id="602fe-202">Waiting for all tasks to complete</span></span> |
| `await Task.Delay` | `Thread.Sleep` | <span data-ttu-id="602fe-203">Bir süre için bekleme</span><span class="sxs-lookup"><span data-stu-id="602fe-203">Waiting for a period of time</span></span> |

* <span data-ttu-id="602fe-204">**Daha az durumlu kod yazma**</span><span class="sxs-lookup"><span data-stu-id="602fe-204">**Write less stateful code**</span></span>

<span data-ttu-id="602fe-205">Küresel nesnelerin durumuna veya belirli yöntemlerin yürütülmesine bağlı değil.</span><span class="sxs-lookup"><span data-stu-id="602fe-205">Don’t depend on the state of global objects or the execution of certain methods.</span></span> <span data-ttu-id="602fe-206">Bunun yerine, yalnızca yöntemlerin dönüş değerlerine bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="602fe-206">Instead, depend only on the return values of methods.</span></span> <span data-ttu-id="602fe-207">Neden?</span><span class="sxs-lookup"><span data-stu-id="602fe-207">Why?</span></span>

* <span data-ttu-id="602fe-208">Kod hakkında neden daha kolay olacaktır.</span><span class="sxs-lookup"><span data-stu-id="602fe-208">Code will be easier to reason about.</span></span>
* <span data-ttu-id="602fe-209">Kodu test etmek daha kolay olacaktır.</span><span class="sxs-lookup"><span data-stu-id="602fe-209">Code will be easier to test.</span></span>
* <span data-ttu-id="602fe-210">Async ve senkron kodu karıştırmak çok daha kolaydır.</span><span class="sxs-lookup"><span data-stu-id="602fe-210">Mixing async and synchronous code is far simpler.</span></span>
* <span data-ttu-id="602fe-211">Yarış koşulları genellikle tamamen önlenebilir.</span><span class="sxs-lookup"><span data-stu-id="602fe-211">Race conditions can typically be avoided altogether.</span></span>
* <span data-ttu-id="602fe-212">İade değerlerine bağlı olarak async kodunukoordine etmek kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="602fe-212">Depending on return values makes coordinating async code simple.</span></span>
* <span data-ttu-id="602fe-213">(Bonus) bağımlılık enjeksiyonu ile gerçekten iyi çalışır.</span><span class="sxs-lookup"><span data-stu-id="602fe-213">(Bonus) it works really well with dependency injection.</span></span>

<span data-ttu-id="602fe-214">Önerilen hedef, kodunuzda tam veya neredeyse tamamlanmış [Başvuru Saydamlığı](https://en.wikipedia.org/wiki/Referential_transparency_%28computer_science%29) elde etmektir.</span><span class="sxs-lookup"><span data-stu-id="602fe-214">A recommended goal is to achieve complete or near-complete [Referential Transparency](https://en.wikipedia.org/wiki/Referential_transparency_%28computer_science%29) in your code.</span></span> <span data-ttu-id="602fe-215">Bunu yapmak son derece öngörülebilir, sınanabilir ve sürdürülebilir bir kod tabanıyla sonuçlanır.</span><span class="sxs-lookup"><span data-stu-id="602fe-215">Doing so will result in an extremely predictable, testable, and maintainable codebase.</span></span>

## <a name="other-resources"></a><span data-ttu-id="602fe-216">Diğer Kaynaklar</span><span class="sxs-lookup"><span data-stu-id="602fe-216">Other Resources</span></span>

* <span data-ttu-id="602fe-217">[Async in-depth](../standard/async-in-depth.md) Görevlerin nasıl çalıştığı hakkında daha fazla bilgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="602fe-217">[Async in-depth](../standard/async-in-depth.md) provides more information about how Tasks work.</span></span>
* [<span data-ttu-id="602fe-218">Async ve await ile asynchronous programlama (C#)</span><span class="sxs-lookup"><span data-stu-id="602fe-218">Asynchronous programming with async and await (C#)</span></span>](./programming-guide/concepts/async/index.md)
* <span data-ttu-id="602fe-219">Lucian Wischik's [Six Essential Tips async için](https://channel9.msdn.com/Series/Three-Essential-Tips-for-Async) async programlama için harika bir kaynak</span><span class="sxs-lookup"><span data-stu-id="602fe-219">Lucian Wischik's [Six Essential Tips for Async](https://channel9.msdn.com/Series/Three-Essential-Tips-for-Async) are a wonderful resource for async programming</span></span>
