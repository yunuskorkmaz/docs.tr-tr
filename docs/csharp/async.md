---
title: 'Zaman uyumsuz programlama-C #'
description: .NET Core tarafından sunulan C# dil düzeyi zaman uyumsuz programlama modeli hakkında bilgi edinin.
author: cartermp
ms.date: 05/20/2020
ms.technology: csharp-async
ms.assetid: b878c34c-a78f-419e-a594-a2b44fa521a4
ms.openlocfilehash: ee5edc80d9c020dbbeced3fc36d3ff273036d7b1
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/21/2020
ms.locfileid: "83761895"
---
# <a name="asynchronous-programming"></a><span data-ttu-id="55b72-103">Zaman uyumsuz programlama</span><span class="sxs-lookup"><span data-stu-id="55b72-103">Asynchronous programming</span></span>

<span data-ttu-id="55b72-104">G/ç bağlantılı bir gereksinimleriniz varsa (bir ağdan veri isteme, veritabanına erişme veya dosya sistemine okuma ve yazma gibi), zaman uyumsuz programlama kullanmak isteyeceksiniz.</span><span class="sxs-lookup"><span data-stu-id="55b72-104">If you have any I/O-bound needs (such as requesting data from a network, accessing a database, or reading and writing to a file system), you'll want to utilize asynchronous programming.</span></span> <span data-ttu-id="55b72-105">Ayrıca, zaman uyumsuz kod yazmak için iyi bir senaryo olan pahalı bir hesaplama yapma gibi CPU 'ya göre büyük bir kod de vardır.</span><span class="sxs-lookup"><span data-stu-id="55b72-105">You could also have CPU-bound code, such as performing an expensive calculation, which is also a good scenario for writing async code.</span></span>

<span data-ttu-id="55b72-106">C#, geri çağırmaları desteklemek veya asynchrony 'yi destekleyen bir kitaplığa uymak zorunda kalmadan, zaman uyumsuz kodların kolayca yazılmasına izin veren dil düzeyinde bir zaman uyumsuz programlama modeline sahiptir.</span><span class="sxs-lookup"><span data-stu-id="55b72-106">C# has a language-level asynchronous programming model, which allows for easily writing asynchronous code, without having to juggle callbacks or conform to a library that supports asynchrony.</span></span> <span data-ttu-id="55b72-107">[Görev tabanlı zaman uyumsuz model (TAP)](../standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md)olarak bilinen öğeleri izler.</span><span class="sxs-lookup"><span data-stu-id="55b72-107">It follows what is known as the [Task-based Asynchronous Pattern (TAP)](../standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md).</span></span>

## <a name="overview-of-the-asynchronous-model"></a><span data-ttu-id="55b72-108">Zaman uyumsuz modele genel bakış</span><span class="sxs-lookup"><span data-stu-id="55b72-108">Overview of the asynchronous model</span></span>

<span data-ttu-id="55b72-109">Zaman uyumsuz programlama çekirdeği, `Task` `Task<T>` zaman uyumsuz işlemleri modelleyebilir ve nesneleridir.</span><span class="sxs-lookup"><span data-stu-id="55b72-109">The core of async programming is the `Task` and `Task<T>` objects, which model asynchronous operations.</span></span> <span data-ttu-id="55b72-110">`async`Ve `await` anahtar kelimeleri tarafından desteklenir.</span><span class="sxs-lookup"><span data-stu-id="55b72-110">They are supported by the `async` and `await` keywords.</span></span> <span data-ttu-id="55b72-111">Çoğu durumda model oldukça basittir:</span><span class="sxs-lookup"><span data-stu-id="55b72-111">The model is fairly simple in most cases:</span></span>

- <span data-ttu-id="55b72-112">G/ç 'ye bağlanan kod için, bir `Task` yöntemin içine veya içine döndüren bir işlemi bekleolursunuz `Task<T>` `async` .</span><span class="sxs-lookup"><span data-stu-id="55b72-112">For I/O-bound code, you await an operation that returns a `Task` or `Task<T>` inside of an `async` method.</span></span>
- <span data-ttu-id="55b72-113">CPU 'ya bağlı kod için, yöntemi olan bir arka plan iş parçacığında başlatılan bir işlemi bekleolursunuz <xref:System.Threading.Tasks.Task.Run%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="55b72-113">For CPU-bound code, you await an operation that is started on a background thread with the <xref:System.Threading.Tasks.Task.Run%2A?displayProperty=nameWithType> method.</span></span>

<span data-ttu-id="55b72-114">`await`Anahtar sözcüğü, Magic 'in gerçekleştiği yerdir.</span><span class="sxs-lookup"><span data-stu-id="55b72-114">The `await` keyword is where the magic happens.</span></span> <span data-ttu-id="55b72-115">Bu, uygulanan yöntemin çağıranına denetim verir `await` ve sonunda bir kullanıcı arabiriminin yanıt vermesini veya bir hizmetin esnek olmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="55b72-115">It yields control to the caller of the method that performed `await`, and it ultimately allows a UI to be responsive or a service to be elastic.</span></span> <span data-ttu-id="55b72-116">Ve dışındaki zaman uyumsuz koda yaklaşıma [yolları](../standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md) olmakla kalmaz `async` `await` , bu makale dil düzeyi yapılarına odaklanır.</span><span class="sxs-lookup"><span data-stu-id="55b72-116">While [there are ways](../standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md) to approach async code other than `async` and `await`, this article focuses on the language-level constructs.</span></span>

### <a name="io-bound-example-download-data-from-a-web-service"></a><span data-ttu-id="55b72-117">G/ç bağlantılı örnek: bir Web hizmetinden veri Indirin</span><span class="sxs-lookup"><span data-stu-id="55b72-117">I/O-bound example: Download data from a web service</span></span>

<span data-ttu-id="55b72-118">Düğmeye basıldığında bir Web hizmetinden bazı verileri indirmeniz gerekebilir, ancak UI iş parçacığını engellemek istemezsiniz.</span><span class="sxs-lookup"><span data-stu-id="55b72-118">You may need to download some data from a web service when a button is pressed, but don't want to block the UI thread.</span></span> <span data-ttu-id="55b72-119">Bu, şöyle gerçekleştirilebilir:</span><span class="sxs-lookup"><span data-stu-id="55b72-119">It can be accomplished like this:</span></span>

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

<span data-ttu-id="55b72-120">Kod, nesneleri ile etkileşimde bulunmak için sürüklenmeden azaltma olmadan hedefi (verileri zaman uyumsuz olarak indirme) ifade eder `Task` .</span><span class="sxs-lookup"><span data-stu-id="55b72-120">The code expresses the intent (downloading data asynchronously) without getting bogged down in interacting with `Task` objects.</span></span>

### <a name="cpu-bound-example-perform-a-calculation-for-a-game"></a><span data-ttu-id="55b72-121">CPU-bağlantılı örnek: bir oyun için hesaplama gerçekleştirme</span><span class="sxs-lookup"><span data-stu-id="55b72-121">CPU-bound example: Perform a calculation for a game</span></span>

<span data-ttu-id="55b72-122">Bir düğmeye basmakta olduğunuz bir mobil oyun yazıyorsanız, ekranda çok sayıda enemaya zarar verebilir.</span><span class="sxs-lookup"><span data-stu-id="55b72-122">Say you're writing a mobile game where pressing a button can inflict damage on many enemies on the screen.</span></span> <span data-ttu-id="55b72-123">Hasar hesaplamasının gerçekleştirilmesi pahalı olabilir ve Kullanıcı arabirimi iş parçacığında yapıldığında, hesaplama gerçekleştirilirken oyun duraklatılmasını sağlar!</span><span class="sxs-lookup"><span data-stu-id="55b72-123">Performing the damage calculation can be expensive, and doing it on the UI thread would make the game appear to pause as the calculation is performed!</span></span>

<span data-ttu-id="55b72-124">Bunu işlemenin en iyi yolu, kullanarak çalışmayı ve sonucunu bekleme işini başlatan bir arka plan iş parçacığını `Task.Run` başlatmanız olur `await` .</span><span class="sxs-lookup"><span data-stu-id="55b72-124">The best way to handle this is to start a background thread, which does the work using `Task.Run`, and await its result using `await`.</span></span> <span data-ttu-id="55b72-125">Bu, iş yapıldığı için Kullanıcı arabiriminin sorunsuz bir şekilde çalışmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="55b72-125">This allows the UI to feel smooth as the work is being done.</span></span>

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

<span data-ttu-id="55b72-126">Bu kod, düğmenin tıklama olayının amacını düzgün bir şekilde ifade eder, arka plan iş parçacığını el ile yönetmeyi gerektirmez ve bunu engellenmeyen bir şekilde yapar.</span><span class="sxs-lookup"><span data-stu-id="55b72-126">This code cleanly expresses the intent of the button's click event, it doesn't require managing a background thread manually, and it does so in a non-blocking way.</span></span>

### <a name="what-happens-under-the-covers"></a><span data-ttu-id="55b72-127">Kapakların altında ne olur?</span><span class="sxs-lookup"><span data-stu-id="55b72-127">What happens under the covers</span></span>

<span data-ttu-id="55b72-128">Zaman uyumsuz işlemlere önem taşıyan çok sayıda hareketli parça vardır.</span><span class="sxs-lookup"><span data-stu-id="55b72-128">There are many moving pieces where asynchronous operations are concerned.</span></span> <span data-ttu-id="55b72-129">Ve ' nin altında neler olduğunu merak ediyorsanız `Task` `Task<T>` , daha fazla bilgi Için [zaman uyumsuz derinlemesine kapsamlı](../standard/async-in-depth.md) makaleye bakın.</span><span class="sxs-lookup"><span data-stu-id="55b72-129">If you're curious about what's happening underneath the covers of `Task` and `Task<T>`, see the [Async in-depth](../standard/async-in-depth.md) article for more information.</span></span>

<span data-ttu-id="55b72-130">Derleyici, nesnelerin C# tarafında, bir `await` , erişildiğinde ve bir arka plan işi bittiğinde yürütmeye devam edildiğinde yürütmeyi sürdüetler gibi şeyleri izleyen bir durum makinesine dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="55b72-130">On the C# side of things, the compiler transforms your code into a state machine that keeps track of things like yielding execution when an `await` is reached and resuming execution when a background job has finished.</span></span>

<span data-ttu-id="55b72-131">Teorik olarak, bu, [zaman uyumsuzluğu 'nin Promise modelinin](https://en.wikipedia.org/wiki/Futures_and_promises)bir uygulamasıdır.</span><span class="sxs-lookup"><span data-stu-id="55b72-131">For the theoretically-inclined, this is an implementation of the [Promise Model of asynchrony](https://en.wikipedia.org/wiki/Futures_and_promises).</span></span>

## <a name="key-pieces-to-understand"></a><span data-ttu-id="55b72-132">Anlaşılması için önemli parçalar</span><span class="sxs-lookup"><span data-stu-id="55b72-132">Key pieces to understand</span></span>

* <span data-ttu-id="55b72-133">Zaman uyumsuz kod hem g/ç bağlantılı hem de CPU ile bağlantılı kod için kullanılabilir, ancak her senaryo için farklı olabilir.</span><span class="sxs-lookup"><span data-stu-id="55b72-133">Async code can be used for both I/O-bound and CPU-bound code, but differently for each scenario.</span></span>
* <span data-ttu-id="55b72-134">Zaman uyumsuz kod `Task<T>` ve `Task` , arka planda gerçekleştirilen işleri modellemek için kullanılan yapılar olan ve kullanır.</span><span class="sxs-lookup"><span data-stu-id="55b72-134">Async code uses `Task<T>` and `Task`, which are constructs used to model work being done in the background.</span></span>
* <span data-ttu-id="55b72-135">`async`Anahtar sözcüğü bir yöntemi bir zaman uyumsuz metoda dönüştürür. Bu, `await` anahtar sözcüğünü gövdesinde kullanmanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="55b72-135">The `async` keyword turns a method into an async method, which allows you to use the `await` keyword in its body.</span></span>
* <span data-ttu-id="55b72-136">`await`Anahtar sözcüğü uygulandığında, çağıran yöntemi askıya alır ve bekleme görevi tamamlanana kadar denetimi çağrı yapana geri verir.</span><span class="sxs-lookup"><span data-stu-id="55b72-136">When the `await` keyword is applied, it suspends the calling method and yields control back to its caller until the awaited task is complete.</span></span>
* <span data-ttu-id="55b72-137">`await`yalnızca zaman uyumsuz bir yöntem içinde kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="55b72-137">`await` can only be used inside an async method.</span></span>

## <a name="recognize-cpu-bound-and-io-bound-work"></a><span data-ttu-id="55b72-138">CPU ile bağlantılı ve g/ç bağlantılı çalışmayı tanıma</span><span class="sxs-lookup"><span data-stu-id="55b72-138">Recognize CPU-bound and I/O-bound work</span></span>

<span data-ttu-id="55b72-139">Bu kılavuzun ilk iki örneği, `async` `await` g/ç ile bağlantılı ve CPU ile bağlantılı çalışma için nasıl kullanabileceğinizi gösterir.</span><span class="sxs-lookup"><span data-stu-id="55b72-139">The first two examples of this guide showed how you can use `async` and `await` for I/O-bound and CPU-bound work.</span></span> <span data-ttu-id="55b72-140">Bu, kodunuzun performansını önemli ölçüde etkileyebildiğinden ve belirli yapıların yanlış kullanılmasına neden olabileceği için ne zaman bir iş yapmanız gerektiğini (g/ç) veya CPU ile bağlantılı olarak belirleyebilmeniz için bir anahtardır.</span><span class="sxs-lookup"><span data-stu-id="55b72-140">It's key that you can identify when a job you need to do is I/O-bound or CPU-bound, because it can greatly affect the performance of your code and could potentially lead to misusing certain constructs.</span></span>

<span data-ttu-id="55b72-141">Kodu yazmadan önce sormanız gereken iki soru aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="55b72-141">Here are two questions you should ask before you write any code:</span></span>

1. <span data-ttu-id="55b72-142">Kodunuz, bir veritabanının verileri gibi bir şey için "bekliyor" olarak değiştirilsin mi?</span><span class="sxs-lookup"><span data-stu-id="55b72-142">Will your code be "waiting" for something, such as data from a database?</span></span>

   <span data-ttu-id="55b72-143">Yanıtınız "Evet" ise, çalışmanız **g/ç 'ye bağlanır**.</span><span class="sxs-lookup"><span data-stu-id="55b72-143">If your answer is "yes", then your work is **I/O-bound**.</span></span>

1. <span data-ttu-id="55b72-144">Kodunuz pahalı bir hesaplama gerçekleştiriyor mu?</span><span class="sxs-lookup"><span data-stu-id="55b72-144">Will your code be performing an expensive computation?</span></span>

   <span data-ttu-id="55b72-145">"Evet" yanıtını verdiyseniz, çalışmanız **CPU 'ya bağlanır**.</span><span class="sxs-lookup"><span data-stu-id="55b72-145">If you answered "yes", then your work is **CPU-bound**.</span></span>

<span data-ttu-id="55b72-146">Sahip olduğunuz iş **g/ç bağlantılı**ise, `async` ve `await` *olmadan* kullanın `Task.Run` .</span><span class="sxs-lookup"><span data-stu-id="55b72-146">If the work you have is **I/O-bound**, use `async` and `await` *without* `Task.Run`.</span></span> <span data-ttu-id="55b72-147">Görev paralel *kitaplığı kullanmamalısınız.*</span><span class="sxs-lookup"><span data-stu-id="55b72-147">You *should not* use the Task Parallel Library.</span></span> <span data-ttu-id="55b72-148">Bunun nedeni, [zaman uyumsuz olarak zaman uyumsuz](../standard/async-in-depth.md)olarak özetlenmiştir.</span><span class="sxs-lookup"><span data-stu-id="55b72-148">The reason for this is outlined in [Async in Depth](../standard/async-in-depth.md).</span></span>

<span data-ttu-id="55b72-149">Sahip olduğunuz iş, **CPU** 'ya bağlıysa ve yanıt verdiğini düşünüyorsanız, `async` ve ' i kullanın, `await` ancak *ile* başka bir iş parçacığında çalışmayı yapın `Task.Run` .</span><span class="sxs-lookup"><span data-stu-id="55b72-149">If the work you have is **CPU-bound** and you care about responsiveness, use `async` and `await`, but spawn off the work on another thread *with* `Task.Run`.</span></span> <span data-ttu-id="55b72-150">İş eşzamanlılık ve paralellik için uygunsa, [görev paralel kitaplığı](../standard/parallel-programming/task-parallel-library-tpl.md)kullanmayı da düşünün.</span><span class="sxs-lookup"><span data-stu-id="55b72-150">If the work is appropriate for concurrency and parallelism, also consider using the [Task Parallel Library](../standard/parallel-programming/task-parallel-library-tpl.md).</span></span>

<span data-ttu-id="55b72-151">Ayrıca, kodunuzun yürütülmesini her zaman ölçmelisiniz.</span><span class="sxs-lookup"><span data-stu-id="55b72-151">Additionally, you should always measure the execution of your code.</span></span> <span data-ttu-id="55b72-152">Örneğin, iş parçacığı oluşturma sırasında bağlam anahtarlarının ek yüküne kıyasla, CPU bağlantılı çalışmanızın yeterince yüksek maliyetli olmadığı bir durumda kendinizi bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="55b72-152">For example, you may find yourself in a situation where your CPU-bound work is not costly enough compared with the overhead of context switches when multithreading.</span></span> <span data-ttu-id="55b72-153">Her seçim kendi zorunluluğunu getirir sahiptir ve durumunuz için doğru zorunluluğunu getirir öğesini seçmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="55b72-153">Every choice has its tradeoff, and you should pick the correct tradeoff for your situation.</span></span>

## <a name="more-examples"></a><span data-ttu-id="55b72-154">Daha fazla örnek</span><span class="sxs-lookup"><span data-stu-id="55b72-154">More examples</span></span>

<span data-ttu-id="55b72-155">Aşağıdaki örneklerde, C# dilinde zaman uyumsuz kod yazmak için çeşitli yollar gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="55b72-155">The following examples demonstrate various ways you can write async code in C#.</span></span> <span data-ttu-id="55b72-156">Bunlar arasında karşılaşabileceğiniz birkaç farklı senaryo ele alınmaktadır.</span><span class="sxs-lookup"><span data-stu-id="55b72-156">They cover a few different scenarios you may come across.</span></span>

### <a name="extract-data-from-a-network"></a><span data-ttu-id="55b72-157">Bir ağdan veri ayıklama</span><span class="sxs-lookup"><span data-stu-id="55b72-157">Extract data from a network</span></span>

<span data-ttu-id="55b72-158">Bu kod parçacığı, konumundaki giriş sayfasından HTML 'i indirir <https://dotnetfoundation.org> ve ".net" DIZESININ HTML 'de oluşma sayısını sayar.</span><span class="sxs-lookup"><span data-stu-id="55b72-158">This snippet downloads the HTML from the homepage at <https://dotnetfoundation.org> and counts the number of times the string ".NET" occurs in the HTML.</span></span> <span data-ttu-id="55b72-159">Bu görevi gerçekleştiren ve sayıyı döndüren bir Web API denetleyicisi yöntemi tanımlamak için ASP.NET kullanır.</span><span class="sxs-lookup"><span data-stu-id="55b72-159">It uses ASP.NET to define a Web API controller method, which performs this task and returns the number.</span></span>

> [!NOTE]
> <span data-ttu-id="55b72-160">Üretim kodunda HTML ayrıştırma işlemi yapmanız planlandıysanız, normal ifadeleri kullanmayın.</span><span class="sxs-lookup"><span data-stu-id="55b72-160">If you plan on doing HTML parsing in production code, don't use regular expressions.</span></span> <span data-ttu-id="55b72-161">Bunun yerine bir ayrıştırma kitaplığı kullanın.</span><span class="sxs-lookup"><span data-stu-id="55b72-161">Use a parsing library instead.</span></span>

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

<span data-ttu-id="55b72-162">Bir düğmeye basıldığında aynı görevi gerçekleştiren bir Evrensel Windows uygulaması için yazılan senaryo aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="55b72-162">Here's the same scenario written for a Universal Windows App, which performs the same task when a Button is pressed:</span></span>

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

    // The await operator suspends SeeTheDotNets_Click, returning control to its caller.
    // This is what allows the app to be responsive and not block the UI thread.
    var html = await getDotNetFoundationHtmlTask;
    int count = Regex.Matches(html, @"\.NET").Count;

    DotNetCountLabel.Text = $"Number of .NETs on dotnetfoundation.org: {count}";

    NetworkProgressBar.IsEnabled = false;
    NetworkProgressBar.Visibility = Visibility.Collapsed;
}
```

### <a name="wait-for-multiple-tasks-to-complete"></a><span data-ttu-id="55b72-163">Birden çok görevin tamamlanmasını bekle</span><span class="sxs-lookup"><span data-stu-id="55b72-163">Wait for multiple tasks to complete</span></span>

<span data-ttu-id="55b72-164">Kendinizi aynı anda birden çok veri parçası almanız gereken bir durumda bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="55b72-164">You may find yourself in a situation where you need to retrieve multiple pieces of data concurrently.</span></span> <span data-ttu-id="55b72-165">`Task`API iki yöntem içerir <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> ve bu, <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType> birden fazla arka plan iş üzerinde engellenmeyen bir bekleme gerçekleştiren zaman uyumsuz kod yazmanıza olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="55b72-165">The `Task` API contains two methods, <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> and <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType>, that allow you to write asynchronous code that performs a non-blocking wait on multiple background jobs.</span></span>

<span data-ttu-id="55b72-166">Bu örnek, `User` bir dizi s için nasıl veri elde edebileceğini gösterir `userId` .</span><span class="sxs-lookup"><span data-stu-id="55b72-166">This example shows how you might grab `User` data for a set of `userId`s.</span></span>

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

<span data-ttu-id="55b72-167">Bu, LINQ kullanarak daha fazla succinctly yazmak için başka bir yoldur:</span><span class="sxs-lookup"><span data-stu-id="55b72-167">Here's another way to write this more succinctly, using LINQ:</span></span>

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

<span data-ttu-id="55b72-168">Daha az kod olsa da, LINQ 'i zaman uyumsuz kodla karıştırdığınızda dikkatli olmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="55b72-168">Although it's less code, take care when mixing LINQ with asynchronous code.</span></span> <span data-ttu-id="55b72-169">LINQ, ertelenmiş (geç) yürütmeyi kullandığından, `foreach` üretilen sırayı veya ' a çağrısıyla tekrarlamaya zormadığınız sürece zaman uyumsuz çağrılar bir döngüde olduğu gibi hemen gerçekleşmeyecek `.ToList()` `.ToArray()` .</span><span class="sxs-lookup"><span data-stu-id="55b72-169">Because LINQ uses deferred (lazy) execution, async calls won't happen immediately as they do in a `foreach` loop unless you force the generated sequence to iterate with a call to `.ToList()` or `.ToArray()`.</span></span>

## <a name="important-info-and-advice"></a><span data-ttu-id="55b72-170">Önemli bilgi ve öneriler</span><span class="sxs-lookup"><span data-stu-id="55b72-170">Important info and advice</span></span>

<span data-ttu-id="55b72-171">Zaman uyumsuz programlama ile, beklenmeyen davranışlara engel olabilecek bazı ayrıntılar göz önünde bulundurularak vardır.</span><span class="sxs-lookup"><span data-stu-id="55b72-171">With async programming there are some details to keep in mind which can prevent unexpected behavior.</span></span>

* <span data-ttu-id="55b72-172">`async`**yöntemlerin bir** `await` **anahtar sözcüğü gövdelerinde veya hiçbir şekilde hiçbir sonuç vermez!**</span><span class="sxs-lookup"><span data-stu-id="55b72-172">`async` **methods need to have an** `await` **keyword in their body or they will never yield!**</span></span>

  <span data-ttu-id="55b72-173">Göz önünde bulundurmanız önemlidir.</span><span class="sxs-lookup"><span data-stu-id="55b72-173">This is important to keep in mind.</span></span> <span data-ttu-id="55b72-174">`await`Bir yöntemin gövdesinde kullanılmazsa `async` , C# derleyicisi bir uyarı oluşturur, ancak kod normal bir yöntem gibi derlenir ve çalışır.</span><span class="sxs-lookup"><span data-stu-id="55b72-174">If `await` is not used in the body of an `async` method, the C# compiler generates a warning, but the code compiles and runs as if it were a normal method.</span></span> <span data-ttu-id="55b72-175">Bu, zaman uyumsuz yöntem için C# derleyicisi tarafından oluşturulan durum makinesi herhangi bir şeyi gerçekleştirmediğinden, inanılmaz verimsiz olur.</span><span class="sxs-lookup"><span data-stu-id="55b72-175">This is incredibly inefficient, as the state machine generated by the C# compiler for the async method is not accomplishing anything.</span></span>

* <span data-ttu-id="55b72-176">**Yazdığınız her zaman uyumsuz yöntem adının soneki olarak "Async" eklemeniz gerekir.**</span><span class="sxs-lookup"><span data-stu-id="55b72-176">**You should add "Async" as the suffix of every async method name you write.**</span></span>

<span data-ttu-id="55b72-177">Bu, zaman uyumlu ve zaman uyumsuz yöntemleri daha kolay ayırt etmek için .NET ' te kullanılan kuraldır.</span><span class="sxs-lookup"><span data-stu-id="55b72-177">This is the convention used in .NET to more easily differentiate synchronous and asynchronous methods.</span></span> <span data-ttu-id="55b72-178">Kodunuz tarafından açıkça çağrılmayan bazı Yöntemler (örneğin, olay işleyicileri veya Web denetleyicisi yöntemleri) uygulanabilir değildir.</span><span class="sxs-lookup"><span data-stu-id="55b72-178">Certain methods that aren't explicitly called by your code (such as event handlers or web controller methods) don't necessarily apply.</span></span> <span data-ttu-id="55b72-179">Kodunuz tarafından açıkça çağrılmadığı için, adlandırmaları hakkında açık olması önemli değildir.</span><span class="sxs-lookup"><span data-stu-id="55b72-179">Because they are not explicitly called by your code, being explicit about their naming isn't as important.</span></span>

* <span data-ttu-id="55b72-180">`async void`**yalnızca olay işleyicileri için kullanılmalıdır.**</span><span class="sxs-lookup"><span data-stu-id="55b72-180">`async void` **should only to be used for event handlers.**</span></span>

<span data-ttu-id="55b72-181">`async void`, olaylar dönüş türlerine sahip olmadığından zaman uyumsuz olay işleyicilerinin çalışmasına izin vermek için tek yoldur (Bu nedenle, `Task` ve kullanamaz `Task<T>` ).</span><span class="sxs-lookup"><span data-stu-id="55b72-181">`async void` is the only way to allow asynchronous event handlers to work because events do not have return types (thus cannot make use of `Task` and `Task<T>`).</span></span> <span data-ttu-id="55b72-182">' Nin diğer kullanımı, `async void` dokunma modelini uygulamaz ve şu gibi kullanımı zor olabilir:</span><span class="sxs-lookup"><span data-stu-id="55b72-182">Any other use of `async void` does not follow the TAP model and can be challenging to use, such as:</span></span>

* <span data-ttu-id="55b72-183">Bir yöntemde oluşturulan özel durumlar, `async void` Bu yöntemin dışında yakalanamıyor.</span><span class="sxs-lookup"><span data-stu-id="55b72-183">Exceptions thrown in an `async void` method can't be caught outside of that method.</span></span>
* <span data-ttu-id="55b72-184">`async void`yöntemler test etmek zordur.</span><span class="sxs-lookup"><span data-stu-id="55b72-184">`async void` methods are difficult to test.</span></span>
* <span data-ttu-id="55b72-185">`async void`arayan, zaman uyumsuz olmasını beklemiyorsanız, Yöntemler hatalı yan etkilere neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="55b72-185">`async void` methods can cause bad side effects if the caller isn't expecting them to be async.</span></span>

* <span data-ttu-id="55b72-186">**LINQ ifadelerinde zaman uyumsuz Lambdalar kullanırken Tread dikkatlice**</span><span class="sxs-lookup"><span data-stu-id="55b72-186">**Tread carefully when using async lambdas in LINQ expressions**</span></span>

<span data-ttu-id="55b72-187">LINQ kullanım içindeki lambda ifadeleri ertelenmiş yürütme, bu kodun bir kez çalıştırılmasını beklemiyorduk.</span><span class="sxs-lookup"><span data-stu-id="55b72-187">Lambda expressions in LINQ use deferred execution, meaning code could end up executing at a time when you're not expecting it to.</span></span> <span data-ttu-id="55b72-188">Bu görevin engellenmesi, doğru yazılmayan bir kilitlenmeye neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="55b72-188">The introduction of blocking tasks into this can easily result in a deadlock if not written correctly.</span></span> <span data-ttu-id="55b72-189">Ayrıca, bu gibi zaman uyumsuz kodun iç içe geçirilmesi, kodun yürütülmesi ile ilgili nedenlerle da daha zor hale gelir.</span><span class="sxs-lookup"><span data-stu-id="55b72-189">Additionally, the nesting of asynchronous code like this can also make it more difficult to reason about the execution of the code.</span></span> <span data-ttu-id="55b72-190">Async ve LINQ güçlü, ancak mümkün olduğunca dikkatli ve açık olarak kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="55b72-190">Async and LINQ are powerful, but should be used together as carefully and clearly as possible.</span></span>

* <span data-ttu-id="55b72-191">**Görevleri engellenmeyen bir şekilde beklede bir kod yazın**</span><span class="sxs-lookup"><span data-stu-id="55b72-191">**Write code that awaits Tasks in a non-blocking manner**</span></span>

<span data-ttu-id="55b72-192">Bir işlemin tamamlanmasını beklemek için geçerli iş parçacığını engellemek `Task` kilitlenmeleri ve engellenen bağlam iş parçacıklarının oluşmasına neden olabilir ve daha karmaşık hata işleme gerektirebilir.</span><span class="sxs-lookup"><span data-stu-id="55b72-192">Blocking the current thread as a means to wait for a `Task` to complete can result in deadlocks and blocked context threads, and can require more complex error-handling.</span></span> <span data-ttu-id="55b72-193">Aşağıdaki tabloda, engellenmeyen bir şekilde görevlerin beklenmesiyle ilgili yönergeler sağlanmaktadır:</span><span class="sxs-lookup"><span data-stu-id="55b72-193">The following table provides guidance on how to deal with waiting for tasks in a non-blocking way:</span></span>

| <span data-ttu-id="55b72-194">Bunu kullanın...</span><span class="sxs-lookup"><span data-stu-id="55b72-194">Use this...</span></span>          | <span data-ttu-id="55b72-195">Bunun yerine...</span><span class="sxs-lookup"><span data-stu-id="55b72-195">Instead of this...</span></span>           | <span data-ttu-id="55b72-196">Bunu yaparken...</span><span class="sxs-lookup"><span data-stu-id="55b72-196">When wishing to do this...</span></span>                 |
|----------------------|------------------------------|--------------------------------------------|
| `await`              | <span data-ttu-id="55b72-197">`Task.Wait` veya `Task.Result`</span><span class="sxs-lookup"><span data-stu-id="55b72-197">`Task.Wait` or `Task.Result`</span></span> | <span data-ttu-id="55b72-198">Arka plan görevinin sonucunu alma</span><span class="sxs-lookup"><span data-stu-id="55b72-198">Retrieving the result of a background task</span></span> |
| `await Task.WhenAny` | `Task.WaitAny`               | <span data-ttu-id="55b72-199">Herhangi bir görevin tamamlanması bekleniyor</span><span class="sxs-lookup"><span data-stu-id="55b72-199">Waiting for any task to complete</span></span>           |
| `await Task.WhenAll` | `Task.WaitAll`               | <span data-ttu-id="55b72-200">Tüm görevlerin tamamlanması bekleniyor</span><span class="sxs-lookup"><span data-stu-id="55b72-200">Waiting for all tasks to complete</span></span>          |
| `await Task.Delay`   | `Thread.Sleep`               | <span data-ttu-id="55b72-201">Bir süre bekleniyor</span><span class="sxs-lookup"><span data-stu-id="55b72-201">Waiting for a period of time</span></span>               |

* <span data-ttu-id="55b72-202">**Kullanmayı düşünün** `ValueTask` **mümkün olduğunda**</span><span class="sxs-lookup"><span data-stu-id="55b72-202">**Consider using** `ValueTask` **where possible**</span></span>

<span data-ttu-id="55b72-203">`Task`Zaman uyumsuz metotlardan bir nesne döndürmek, belirli yollarda performans sorunlarını ortaya çıkarabilir.</span><span class="sxs-lookup"><span data-stu-id="55b72-203">Returning a `Task` object from async methods can introduce performance bottlenecks in certain paths.</span></span> <span data-ttu-id="55b72-204">`Task`bir başvuru türüdür, bu nedenle bu bir nesne ayırma anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="55b72-204">`Task` is a reference type, so using it means allocating an object.</span></span> <span data-ttu-id="55b72-205">Değiştirici ile belirtilen bir yöntemin `async` önbelleğe alınmış bir sonuç döndürdüğü veya zaman uyumlu olarak tamamladığı durumlarda, ek ayırmalar kodun performans açısından kritik bölümlerinde önemli bir zaman maliyeti olabilir.</span><span class="sxs-lookup"><span data-stu-id="55b72-205">In cases where a method declared with the `async` modifier returns a cached result or completes synchronously, the extra allocations can become a significant time cost in performance critical sections of code.</span></span> <span data-ttu-id="55b72-206">Bu ayırmalar sıkı Döngülerde gerçekleşirse maliyetli hale gelebilir.</span><span class="sxs-lookup"><span data-stu-id="55b72-206">It can become costly if those allocations occur in tight loops.</span></span> <span data-ttu-id="55b72-207">Daha fazla bilgi için bkz. [Genelleştirilmiş zaman uyumsuz dönüş türleri](whats-new/csharp-7.md#generalized-async-return-types).</span><span class="sxs-lookup"><span data-stu-id="55b72-207">For more information, see [generalized async return types](whats-new/csharp-7.md#generalized-async-return-types).</span></span>

* <span data-ttu-id="55b72-208">Kullanmayı **düşünün**`ConfigureAwait(false)`</span><span class="sxs-lookup"><span data-stu-id="55b72-208">**Consider using** `ConfigureAwait(false)`</span></span>

<span data-ttu-id="55b72-209">Ortak bir soru, "yöntemi ne zaman kullanmalıyım <xref:System.Threading.Tasks.Task.ConfigureAwait(System.Boolean)?displayProperty=nameWithType> ?" dir.</span><span class="sxs-lookup"><span data-stu-id="55b72-209">A common question is, "when should I use the <xref:System.Threading.Tasks.Task.ConfigureAwait(System.Boolean)?displayProperty=nameWithType> method?".</span></span> <span data-ttu-id="55b72-210">Yöntemi, bir örneğin, `Task` awaiter 'yi yapılandırmasına izin verir.</span><span class="sxs-lookup"><span data-stu-id="55b72-210">The method allows for a `Task` instance to configure its awaiter.</span></span> <span data-ttu-id="55b72-211">Bu önemli bir noktadır ve yanlış ayarlanmaması, performans etkilerine ve hatta kilitlenmeleri sağlayabilir.</span><span class="sxs-lookup"><span data-stu-id="55b72-211">This is an important consideration and setting it incorrectly could potentially have performance implications and even deadlocks.</span></span> <span data-ttu-id="55b72-212">Hakkında daha fazla bilgi için `ConfigureAwait` , bkz. [ConfigureAwait SSS](https://devblogs.microsoft.com/dotnet/configureawait-faq).</span><span class="sxs-lookup"><span data-stu-id="55b72-212">For more information on `ConfigureAwait`, see the [ConfigureAwait FAQ](https://devblogs.microsoft.com/dotnet/configureawait-faq).</span></span>

* <span data-ttu-id="55b72-213">**Daha az durum bilgisi olan kod yazma**</span><span class="sxs-lookup"><span data-stu-id="55b72-213">**Write less stateful code**</span></span>

<span data-ttu-id="55b72-214">Genel nesnelerin durumuna veya belirli yöntemlerin yürütülmesine bağlı değildir.</span><span class="sxs-lookup"><span data-stu-id="55b72-214">Don't depend on the state of global objects or the execution of certain methods.</span></span> <span data-ttu-id="55b72-215">Bunun yerine, yalnızca yöntemlerin dönüş değerlerine göre değişir.</span><span class="sxs-lookup"><span data-stu-id="55b72-215">Instead, depend only on the return values of methods.</span></span> <span data-ttu-id="55b72-216">Neden?</span><span class="sxs-lookup"><span data-stu-id="55b72-216">Why?</span></span>

* <span data-ttu-id="55b72-217">Kodun nedeni daha kolay olacaktır.</span><span class="sxs-lookup"><span data-stu-id="55b72-217">Code will be easier to reason about.</span></span>
* <span data-ttu-id="55b72-218">Kodun test etmek daha kolay olacaktır.</span><span class="sxs-lookup"><span data-stu-id="55b72-218">Code will be easier to test.</span></span>
* <span data-ttu-id="55b72-219">Zaman uyumsuz ve zaman uyumlu kodu karıştırma çok basittir.</span><span class="sxs-lookup"><span data-stu-id="55b72-219">Mixing async and synchronous code is far simpler.</span></span>
* <span data-ttu-id="55b72-220">Yarış koşullarından genellikle tamamen kaçınılabilir.</span><span class="sxs-lookup"><span data-stu-id="55b72-220">Race conditions can typically be avoided altogether.</span></span>
* <span data-ttu-id="55b72-221">Dönüş değerlerine bağlı olarak, zaman uyumsuz kod koordine etme basit hale gelir.</span><span class="sxs-lookup"><span data-stu-id="55b72-221">Depending on return values makes coordinating async code simple.</span></span>
* <span data-ttu-id="55b72-222">(Ödül) bağımlılık ekleme ile oldukça iyi bir şekilde çalışmaktadır.</span><span class="sxs-lookup"><span data-stu-id="55b72-222">(Bonus) it works really well with dependency injection.</span></span>

<span data-ttu-id="55b72-223">Önerilen bir amaç, kodunuzda tam veya neredeyse tam bir [bilgi saydamlığı](https://en.wikipedia.org/wiki/Referential_transparency_%28computer_science%29) elde etmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="55b72-223">A recommended goal is to achieve complete or near-complete [Referential Transparency](https://en.wikipedia.org/wiki/Referential_transparency_%28computer_science%29) in your code.</span></span> <span data-ttu-id="55b72-224">Bunun yapılması, son derece öngörülebilir, test edilebilir ve sürdürülebilir kod temeli oluşmasına neden olur.</span><span class="sxs-lookup"><span data-stu-id="55b72-224">Doing so will result in an extremely predictable, testable, and maintainable codebase.</span></span>

## <a name="other-resources"></a><span data-ttu-id="55b72-225">Diğer kaynaklar</span><span class="sxs-lookup"><span data-stu-id="55b72-225">Other resources</span></span>

* <span data-ttu-id="55b72-226">[Zaman uyumsuz kapsamlı,](../standard/async-in-depth.md) görevlerin nasıl çalıştığı hakkında daha fazla bilgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="55b72-226">[Async in-depth](../standard/async-in-depth.md) provides more information about how Tasks work.</span></span>
* [<span data-ttu-id="55b72-227">Async ve await ile zaman uyumsuz programlama (C#)</span><span class="sxs-lookup"><span data-stu-id="55b72-227">Asynchronous programming with async and await (C#)</span></span>](./programming-guide/concepts/async/index.md)
* <span data-ttu-id="55b72-228">Zaman uyumsuz programlama için Lucian Wıchık 'nin [altı temel ipucu](https://channel9.msdn.com/Series/Three-Essential-Tips-for-Async) , Async programlama için harika bir kaynaktır</span><span class="sxs-lookup"><span data-stu-id="55b72-228">Lucian Wischik's [Six Essential Tips for Async](https://channel9.msdn.com/Series/Three-Essential-Tips-for-Async) are a wonderful resource for async programming</span></span>
