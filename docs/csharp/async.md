---
title: Zaman uyumsuz programlama-C#
description: .NET Core tarafından C# sunulan dil düzeyi zaman uyumsuz programlama modeli hakkında bilgi edinin.
author: cartermp
ms.date: 06/20/2016
ms.technology: csharp-async
ms.assetid: b878c34c-a78f-419e-a594-a2b44fa521a4
ms.custom: seodec18
ms.openlocfilehash: 86145e8971d9a59fba17368d9530f40d86bf2858
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/29/2019
ms.locfileid: "73037682"
---
# <a name="asynchronous-programming"></a><span data-ttu-id="39c95-103">Zaman uyumsuz programlama</span><span class="sxs-lookup"><span data-stu-id="39c95-103">Asynchronous programming</span></span>

<span data-ttu-id="39c95-104">G/ç bağlantılı bir gereksinimleriniz varsa (bir ağdan veri istemek veya bir veritabanına erişmek gibi), zaman uyumsuz programlamayı kullanmak isteyeceksiniz.</span><span class="sxs-lookup"><span data-stu-id="39c95-104">If you have any I/O-bound needs (such as requesting data from a network or accessing a database), you'll want to utilize asynchronous programming.</span></span>  <span data-ttu-id="39c95-105">Ayrıca, zaman uyumsuz kod yazmak için iyi bir senaryo olan pahalı bir hesaplama yapma gibi CPU 'ya göre büyük bir kod de vardır.</span><span class="sxs-lookup"><span data-stu-id="39c95-105">You could also have CPU-bound code, such as performing an expensive calculation, which is also a good scenario for writing async code.</span></span>

<span data-ttu-id="39c95-106">C#, geri çağırmaları desteklemek veya bir kitaplığa uymak zorunda kalmadan, zaman uyumsuz kodların kolayca yazılmasına izin veren dil düzeyinde bir zaman uyumsuz programlama modeline sahiptir.</span><span class="sxs-lookup"><span data-stu-id="39c95-106">C# has a language-level asynchronous programming model which allows for easily writing asynchronous code without having to juggle callbacks or conform to a library which supports asynchrony.</span></span> <span data-ttu-id="39c95-107">[Görev tabanlı zaman uyumsuz model (TAP)](../standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md)olarak bilinen öğeleri izler.</span><span class="sxs-lookup"><span data-stu-id="39c95-107">It follows what is known as the [Task-based Asynchronous Pattern (TAP)](../standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md).</span></span>

## <a name="basic-overview-of-the-asynchronous-model"></a><span data-ttu-id="39c95-108">Zaman uyumsuz modele temel genel bakış</span><span class="sxs-lookup"><span data-stu-id="39c95-108">Basic Overview of the Asynchronous Model</span></span>

<span data-ttu-id="39c95-109">Zaman uyumsuz programlama çekirdeği, zaman uyumsuz işlemleri modellerdeki `Task` ve `Task<T>` nesneleridir.</span><span class="sxs-lookup"><span data-stu-id="39c95-109">The core of async programming is the `Task` and `Task<T>` objects, which model asynchronous operations.</span></span>  <span data-ttu-id="39c95-110">`async` ve `await` anahtar sözcükleri desteklenir.</span><span class="sxs-lookup"><span data-stu-id="39c95-110">They are supported by the `async` and `await` keywords.</span></span>  <span data-ttu-id="39c95-111">Çoğu durumda model oldukça basittir:</span><span class="sxs-lookup"><span data-stu-id="39c95-111">The model is fairly simple in most cases:</span></span>

<span data-ttu-id="39c95-112">G/ç ile bağlantılı kod için, bir `async` yönteminin içinde `Task` veya `Task<T>` döndüren bir işlem `await`.</span><span class="sxs-lookup"><span data-stu-id="39c95-112">For I/O-bound code, you `await` an operation which returns a `Task` or `Task<T>` inside of an `async` method.</span></span>

<span data-ttu-id="39c95-113">CPU 'ya bağlı kod için, `Task.Run` yöntemine sahip bir arka plan iş parçacığında başlatılan bir işlem `await`.</span><span class="sxs-lookup"><span data-stu-id="39c95-113">For CPU-bound code, you `await` an operation which is started on a background thread with the `Task.Run` method.</span></span>

<span data-ttu-id="39c95-114">`await` anahtar sözcüğü, Magic 'in gerçekleştiği yerdir.</span><span class="sxs-lookup"><span data-stu-id="39c95-114">The `await` keyword is where the magic happens.</span></span> <span data-ttu-id="39c95-115">`await`gerçekleştirdiği yöntemin çağıranına denetim verir ve sonunda bir kullanıcı arabiriminin yanıt vermesini veya bir hizmetin esnek olmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="39c95-115">It yields control to the caller of the method that performed `await`, and it ultimately allows a UI to be responsive or a service to be elastic.</span></span>

<span data-ttu-id="39c95-116">Zaman uyumsuz koda `async` yaklaşımı ve yukarıda bağlantı verilen dokunma makalesinde özetlenen `await` için başka yollar vardır, ancak bu belge bu noktadan sonra gelen dil düzeyi yapılarına odaklanacaktır.</span><span class="sxs-lookup"><span data-stu-id="39c95-116">There are other ways to approach async code than `async` and `await` outlined in the TAP article linked above, but this document will focus on the language-level constructs from this point forward.</span></span>

### <a name="io-bound-example-downloading-data-from-a-web-service"></a><span data-ttu-id="39c95-117">G/ç bağlantılı örnek: bir Web hizmetinden veri Indirme</span><span class="sxs-lookup"><span data-stu-id="39c95-117">I/O-Bound Example: Downloading data from a web service</span></span>

<span data-ttu-id="39c95-118">Düğmeye basıldığında bir Web hizmetinden bazı verileri indirmeniz gerekebilir, ancak UI iş parçacığını engellemek istemezsiniz.</span><span class="sxs-lookup"><span data-stu-id="39c95-118">You may need to download some data from a web service when a button is pressed, but don’t want to block the UI thread.</span></span> <span data-ttu-id="39c95-119">Bu, şöyle gerçekleştirilebilir:</span><span class="sxs-lookup"><span data-stu-id="39c95-119">It can be accomplished simply like this:</span></span>

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

<span data-ttu-id="39c95-120">İşte bu kadar!</span><span class="sxs-lookup"><span data-stu-id="39c95-120">And that’s it!</span></span> <span data-ttu-id="39c95-121">Kod, görev nesneleriyle etkileşimde bulunmak için sürüklenmeden azaltma olmadan amacı ifade eder (bazı verileri zaman uyumsuz olarak indirme).</span><span class="sxs-lookup"><span data-stu-id="39c95-121">The code expresses the intent (downloading some data asynchronously) without getting bogged down in interacting with Task objects.</span></span>

### <a name="cpu-bound-example-performing-a-calculation-for-a-game"></a><span data-ttu-id="39c95-122">CPU-bağlantılı örnek: bir oyun için hesaplama gerçekleştirme</span><span class="sxs-lookup"><span data-stu-id="39c95-122">CPU-bound Example: Performing a Calculation for a Game</span></span>

<span data-ttu-id="39c95-123">Bir düğmeye basmakta olduğunuz bir mobil oyun yazıyorsanız, ekranda çok sayıda enemaya zarar verebilir.</span><span class="sxs-lookup"><span data-stu-id="39c95-123">Say you're writing a mobile game where pressing a button can inflict damage on many enemies on the screen.</span></span>  <span data-ttu-id="39c95-124">Hasar hesaplamasının gerçekleştirilmesi pahalı olabilir ve Kullanıcı arabirimi iş parçacığında yapıldığında, hesaplama gerçekleştirilirken oyun duraklatılmasını sağlar!</span><span class="sxs-lookup"><span data-stu-id="39c95-124">Performing the damage calculation can be expensive, and doing it on the UI thread would make the game appear to pause as the calculation is performed!</span></span>

<span data-ttu-id="39c95-125">Bunu işlemenin en iyi yolu, `Task.Run`kullanarak çalışmayı başlatan bir arka plan iş parçacığını başlatmak ve onun sonucunu `await`.</span><span class="sxs-lookup"><span data-stu-id="39c95-125">The best way to handle this is to start a background thread which does the work using `Task.Run`, and `await` its result.</span></span>  <span data-ttu-id="39c95-126">Bu, iş yapıldığı için Kullanıcı arabiriminin sorunsuz bir şekilde çalışmasına olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="39c95-126">This will allow the UI to feel smooth as the work is being done.</span></span>

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

<span data-ttu-id="39c95-127">İşte bu kadar!</span><span class="sxs-lookup"><span data-stu-id="39c95-127">And that's it!</span></span>  <span data-ttu-id="39c95-128">Bu kod, düğmenin tıklama olayının amacını düzgün bir şekilde ifade eder, arka plan iş parçacığını el ile yönetmeyi gerektirmez ve bunu engellenmeyen bir şekilde yapar.</span><span class="sxs-lookup"><span data-stu-id="39c95-128">This code cleanly expresses the intent of the button's click event, it doesn't require managing a background thread manually, and it does so in a non-blocking way.</span></span>

### <a name="what-happens-under-the-covers"></a><span data-ttu-id="39c95-129">Kapakların altında ne olur?</span><span class="sxs-lookup"><span data-stu-id="39c95-129">What happens under the covers</span></span>

<span data-ttu-id="39c95-130">Zaman uyumsuz işlemlere önem taşıyan çok sayıda hareketli parça vardır.</span><span class="sxs-lookup"><span data-stu-id="39c95-130">There's a lot of moving pieces where asynchronous operations are concerned.</span></span>  <span data-ttu-id="39c95-131">`Task` ve `Task<T>`kapakların altında neler olduğunu merak ediyorsanız, daha fazla bilgi için [zaman uyumsuz ayrıntılı](../standard/async-in-depth.md) makaleyi kullanıma alın.</span><span class="sxs-lookup"><span data-stu-id="39c95-131">If you're curious about what's happening underneath the covers of `Task` and `Task<T>`, checkout the [Async in-depth](../standard/async-in-depth.md) article for more information.</span></span>

<span data-ttu-id="39c95-132">Nesnelerin C# yanında, derleyici kodunuzu bir durum makinesine dönüştürür ve bu da bir`await`erişildiğinde ve bir arka plan işi bittiğinde yürütmeye devam eder.</span><span class="sxs-lookup"><span data-stu-id="39c95-132">On the C# side of things, the compiler transforms your code into a state machine which keeps track of things like yielding execution when an `await` is reached and resuming execution when a background job has finished.</span></span>

<span data-ttu-id="39c95-133">Teorik olarak, bu, [zaman uyumsuzluğu 'nin Promise modelinin](https://en.wikipedia.org/wiki/Futures_and_promises)bir uygulamasıdır.</span><span class="sxs-lookup"><span data-stu-id="39c95-133">For the theoretically-inclined, this is an implementation of the [Promise Model of asynchrony](https://en.wikipedia.org/wiki/Futures_and_promises).</span></span>

## <a name="key-pieces-to-understand"></a><span data-ttu-id="39c95-134">Anlaşılması için önemli parçalar</span><span class="sxs-lookup"><span data-stu-id="39c95-134">Key Pieces to Understand</span></span>

* <span data-ttu-id="39c95-135">Zaman uyumsuz kod hem g/ç bağlantılı hem de CPU ile bağlantılı kod için kullanılabilir, ancak her senaryo için farklı olabilir.</span><span class="sxs-lookup"><span data-stu-id="39c95-135">Async code can be used for both I/O-bound and CPU-bound code, but differently for each scenario.</span></span>
* <span data-ttu-id="39c95-136">Zaman uyumsuz kod, arka planda gerçekleştirilen işleri modellemek için kullanılan yapılar olan `Task<T>` ve `Task`kullanır.</span><span class="sxs-lookup"><span data-stu-id="39c95-136">Async code uses `Task<T>` and `Task`, which are constructs used to model work being done in the background.</span></span>
* <span data-ttu-id="39c95-137">`async` anahtar sözcüğü bir yöntemi bir zaman uyumsuz metoda dönüştürür. Bu, gövdesinde `await` anahtar sözcüğünü kullanmanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="39c95-137">The `async` keyword turns a method into an async method, which allows you to use the `await` keyword in its body.</span></span>
* <span data-ttu-id="39c95-138">`await` anahtar sözcüğü uygulandığında, çağıran yöntemi askıya alır ve bekleme görevi tamamlanana kadar denetimi çağrı yapana geri verir.</span><span class="sxs-lookup"><span data-stu-id="39c95-138">When the `await` keyword is applied, it suspends the calling method and yields control back to its caller until the awaited task is complete.</span></span>
* <span data-ttu-id="39c95-139">`await` yalnızca zaman uyumsuz bir yöntem içinde kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="39c95-139">`await` can only be used inside an async method.</span></span>

## <a name="recognize-cpu-bound-and-io-bound-work"></a><span data-ttu-id="39c95-140">CPU ile bağlantılı ve g/ç bağlantılı çalışmayı tanıma</span><span class="sxs-lookup"><span data-stu-id="39c95-140">Recognize CPU-Bound and I/O-Bound Work</span></span>

<span data-ttu-id="39c95-141">Bu kılavuzun ilk iki örneği g/ç ile bağlantılı ve CPU ile bağlantılı çalışma için `async` ve `await` nasıl kullanabileceğinizi gösterdi.</span><span class="sxs-lookup"><span data-stu-id="39c95-141">The first two examples of this guide showed how you can use `async` and `await` for I/O-bound and CPU-bound work.</span></span>  <span data-ttu-id="39c95-142">Bu, kodunuzun performansını önemli ölçüde etkileyebildiğinden ve belirli yapıların yanlış kullanılmasına neden olabileceği için ne zaman bir iş yapmanız gerektiğini (g/ç) veya CPU ile bağlantılı olarak belirleyebilmeniz için bir anahtardır.</span><span class="sxs-lookup"><span data-stu-id="39c95-142">It's key that you can identify when a job you need to do is I/O-bound or CPU-bound, because it can greatly affect the performance of your code and could potentially lead to misusing certain constructs.</span></span>

<span data-ttu-id="39c95-143">Kodu yazmadan önce sormanız gereken iki soru aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="39c95-143">Here are two questions you should ask before you write any code:</span></span>

1. <span data-ttu-id="39c95-144">Kodunuz, bir veritabanının verileri gibi bir şey için "bekliyor" olarak değiştirilsin mi?</span><span class="sxs-lookup"><span data-stu-id="39c95-144">Will your code be "waiting" for something, such as data from a database?</span></span>

    <span data-ttu-id="39c95-145">Yanıtınız "Evet" ise, çalışmanız **g/ç 'ye bağlanır**.</span><span class="sxs-lookup"><span data-stu-id="39c95-145">If your answer is "yes", then your work is **I/O-bound**.</span></span>

2. <span data-ttu-id="39c95-146">Kodunuz çok pahalı bir hesaplama gerçekleştiriyor mu?</span><span class="sxs-lookup"><span data-stu-id="39c95-146">Will your code be performing a very expensive computation?</span></span>

    <span data-ttu-id="39c95-147">"Evet" yanıtını verdiyseniz, çalışmanız **CPU 'ya bağlanır**.</span><span class="sxs-lookup"><span data-stu-id="39c95-147">If you answered "yes", then your work is **CPU-bound**.</span></span>

<span data-ttu-id="39c95-148">Sahip olduğunuz iş **g/ç 'ye bağlıysa**, `Task.Run`*olmadan* `async` ve `await` kullanın.</span><span class="sxs-lookup"><span data-stu-id="39c95-148">If the work you have is **I/O-bound**, use `async` and `await` *without* `Task.Run`.</span></span>  <span data-ttu-id="39c95-149">Görev paralel *kitaplığı kullanmamalısınız.*</span><span class="sxs-lookup"><span data-stu-id="39c95-149">You *should not* use the Task Parallel Library.</span></span>  <span data-ttu-id="39c95-150">Bunun nedeni, [zaman uyumsuz olarak zaman uyumsuz makalesinde](../standard/async-in-depth.md)açıklanmıştır.</span><span class="sxs-lookup"><span data-stu-id="39c95-150">The reason for this is outlined in the [Async in Depth article](../standard/async-in-depth.md).</span></span>

<span data-ttu-id="39c95-151">Sahip olduğunuz iş, **CPU** 'ya bağlıysa ve yanıt hızını düşünüyorsanız, `async` ve `await` kullanın, ancak çalışmayı `Task.Run`*ile* başka bir iş parçacığında üretme işlemini yapın.</span><span class="sxs-lookup"><span data-stu-id="39c95-151">If the work you have is **CPU-bound** and you care about responsiveness, use `async` and `await` but spawn the work off on another thread *with* `Task.Run`.</span></span>  <span data-ttu-id="39c95-152">İş eşzamanlılık ve paralellik için uygunsa, [görev paralel kitaplığı](../standard/parallel-programming/task-parallel-library-tpl.md)kullanmayı da göz önünde bulundurmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="39c95-152">If the work is appropriate for concurrency and parallelism, you should also consider using the [Task Parallel Library](../standard/parallel-programming/task-parallel-library-tpl.md).</span></span>

<span data-ttu-id="39c95-153">Ayrıca, kodunuzun yürütülmesini her zaman ölçmelisiniz.</span><span class="sxs-lookup"><span data-stu-id="39c95-153">Additionally, you should always measure the execution of your code.</span></span>  <span data-ttu-id="39c95-154">Örneğin, iş parçacığı oluşturma sırasında bağlam anahtarlarının ek yüküne kıyasla, CPU bağlantılı çalışmanızın yeterince yüksek maliyetli olmadığı bir durumda kendinizi bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="39c95-154">For example, you may find yourself in a situation where your CPU-bound work is not costly enough compared with the overhead of context switches when multithreading.</span></span>  <span data-ttu-id="39c95-155">Her seçim kendi zorunluluğunu getirir sahiptir ve durumunuz için doğru zorunluluğunu getirir öğesini seçmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="39c95-155">Every choice has its tradeoff, and you should pick the correct tradeoff for your situation.</span></span>

## <a name="more-examples"></a><span data-ttu-id="39c95-156">Daha fazla örnek</span><span class="sxs-lookup"><span data-stu-id="39c95-156">More Examples</span></span>

<span data-ttu-id="39c95-157">Aşağıdaki örneklerde, içinde C#zaman uyumsuz kod yazmak için kullanabileceğiniz çeşitli yollar gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="39c95-157">The following examples demonstrate various ways you can write async code in C#.</span></span>  <span data-ttu-id="39c95-158">Bunlar arasında karşılaşabileceğiniz birkaç farklı senaryo ele alınmaktadır.</span><span class="sxs-lookup"><span data-stu-id="39c95-158">They cover a few different scenarios you may come across.</span></span>

### <a name="extracting-data-from-a-network"></a><span data-ttu-id="39c95-159">Bir ağdan veri ayıklama</span><span class="sxs-lookup"><span data-stu-id="39c95-159">Extracting Data from a Network</span></span>

<span data-ttu-id="39c95-160">Bu kod parçacığı, [www.dotnetfoundation.org](https://www.dotnetfoundation.org) adresindeki GIRIŞ sayfasından HTML 'i indirir ve ".net" dizesinin HTML 'de oluşma sayısını sayar.</span><span class="sxs-lookup"><span data-stu-id="39c95-160">This snippet downloads the HTML from the homepage at [www.dotnetfoundation.org](https://www.dotnetfoundation.org) and counts the number of times the string ".NET" occurs in the HTML.</span></span>  <span data-ttu-id="39c95-161">Bu görevi gerçekleştiren bir Web denetleyicisi yöntemi tanımlamak için ASP.NET MVC kullanır, sayı döndürür.</span><span class="sxs-lookup"><span data-stu-id="39c95-161">It uses ASP.NET MVC to define a web controller method which performs this task, returning the number.</span></span>

> [!NOTE]
> <span data-ttu-id="39c95-162">Üretim kodunda HTML ayrıştırma işlemi yapmanız planlandıysanız, normal ifadeleri kullanmayın.</span><span class="sxs-lookup"><span data-stu-id="39c95-162">If you plan on doing HTML parsing in production code, don't use regular expressions.</span></span> <span data-ttu-id="39c95-163">Bunun yerine bir ayrıştırma kitaplığı kullanın.</span><span class="sxs-lookup"><span data-stu-id="39c95-163">Use a parsing library instead.</span></span>

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

<span data-ttu-id="39c95-164">Bir düğmeye basıldığında aynı görevi gerçekleştiren bir Evrensel Windows uygulaması için yazılan senaryo aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="39c95-164">Here's the same scenario written for a Universal Windows App, which performs the same task when a Button is pressed:</span></span>

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

### <a name="waiting-for-multiple-tasks-to-complete"></a><span data-ttu-id="39c95-165">Birden çok görevin tamamlanması bekleniyor</span><span class="sxs-lookup"><span data-stu-id="39c95-165">Waiting for Multiple Tasks to Complete</span></span>

<span data-ttu-id="39c95-166">Kendinizi aynı anda birden çok veri parçası almanız gereken bir durumda bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="39c95-166">You may find yourself in a situation where you need to retrieve multiple pieces of data concurrently.</span></span>  <span data-ttu-id="39c95-167">`Task` API 'SI, birden fazla arka plan iş üzerinde engellenmeyen bir bekleme kodu gerçekleştiren zaman uyumsuz kod yazmanızı sağlayan `Task.WhenAll` ve `Task.WhenAny` iki yöntem içerir.</span><span class="sxs-lookup"><span data-stu-id="39c95-167">The `Task` API contains two methods, `Task.WhenAll` and `Task.WhenAny` which allow you to write asynchronous code which performs a non-blocking wait on multiple background jobs.</span></span>

<span data-ttu-id="39c95-168">Bu örnek, bir `userId`s kümesi için `User` verilerini nasıl kullanabileceğinizi gösterir.</span><span class="sxs-lookup"><span data-stu-id="39c95-168">This example shows how you might grab `User` data for a set of `userId`s.</span></span>

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

<span data-ttu-id="39c95-169">Bu, LINQ kullanarak bu bit daha fazla succinctly yazmak için başka bir yoldur:</span><span class="sxs-lookup"><span data-stu-id="39c95-169">Here's another way to write this a bit more succinctly, using LINQ:</span></span>

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

<span data-ttu-id="39c95-170">Daha az kod olsa da, LINQ 'i zaman uyumsuz kodla karıştırdığınızda dikkatli olmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="39c95-170">Although it's less code, take care when mixing LINQ with asynchronous code.</span></span>  <span data-ttu-id="39c95-171">LINQ, ertelenmiş (geç) yürütmeyi kullandığından, üretilen sırayı `.ToList()` veya `.ToArray()`çağrısıyla tekrarlamaya zorlamayın, zaman uyumsuz çağrılar `foreach()` döngüsünde göründükleri şekilde hemen gerçekleşmeyecek.</span><span class="sxs-lookup"><span data-stu-id="39c95-171">Because LINQ uses deferred (lazy) execution, async calls won't happen immediately as they do in a `foreach()` loop unless you force the generated sequence to iterate with a call to `.ToList()` or `.ToArray()`.</span></span>

## <a name="important-info-and-advice"></a><span data-ttu-id="39c95-172">Önemli bilgi ve öneriler</span><span class="sxs-lookup"><span data-stu-id="39c95-172">Important Info and Advice</span></span>

<span data-ttu-id="39c95-173">Zaman uyumsuz programlama görece basittir, ancak beklenmeyen davranışları engelleyebilen aklınızda bulundurmanız gereken bazı ayrıntılar vardır.</span><span class="sxs-lookup"><span data-stu-id="39c95-173">Although async programming is relatively straightforward, there are some details to keep in mind which can prevent unexpected behavior.</span></span>

* <span data-ttu-id="39c95-174">`async` yöntemlerinin gövdesinde bir `await` anahtar sözcüğü **olması gerekir** , **Aksi durumda hiçbir şekilde sonuç vermez!**</span><span class="sxs-lookup"><span data-stu-id="39c95-174">`async` **methods need to have an** `await` **keyword in their body or they will never yield!**</span></span>

<span data-ttu-id="39c95-175">Göz önünde bulundurmanız önemlidir.</span><span class="sxs-lookup"><span data-stu-id="39c95-175">This is important to keep in mind.</span></span>  <span data-ttu-id="39c95-176">`await` bir `async` yönteminin gövdesinde kullanılmıyorsa, C# derleyici bir uyarı oluşturur, ancak kod normal bir yöntem gibi derleyip çalıştırılır.</span><span class="sxs-lookup"><span data-stu-id="39c95-176">If `await` is not used in the body of an `async` method, the C# compiler will generate a warning, but the code will compile and run as if it were a normal method.</span></span>  <span data-ttu-id="39c95-177">Bu, zaman uyumsuz yöntem için C# derleyici tarafından oluşturulan durum makinesi herhangi bir şeyi gerçekleştiremeyecek olduğundan, bunun da inanılmaz verimsiz olacağını unutmayın.</span><span class="sxs-lookup"><span data-stu-id="39c95-177">Note that this would also be incredibly inefficient, as the state machine generated by the C# compiler for the async method would not be accomplishing anything.</span></span>

* <span data-ttu-id="39c95-178">**Yazdığınız her zaman uyumsuz yöntem adının soneki olarak "Async" eklemeniz gerekir.**</span><span class="sxs-lookup"><span data-stu-id="39c95-178">**You should add "Async" as the suffix of every async method name you write.**</span></span>

<span data-ttu-id="39c95-179">Bu, zaman uyumlu ve zaman uyumsuz yöntemleri daha kolay ayırt etmek için .NET ' te kullanılan kuraldır.</span><span class="sxs-lookup"><span data-stu-id="39c95-179">This is the convention used in .NET to more-easily differentiate synchronous and asynchronous methods.</span></span> <span data-ttu-id="39c95-180">Kodunuz (örneğin, olay işleyicileri veya Web denetleyicisi yöntemleri) tarafından açıkça çağrılmayan bazı yöntemlerin uygulanması gerekmediğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="39c95-180">Note that certain methods which aren’t explicitly called by your code (such as event handlers or web controller methods) don’t necessarily apply.</span></span> <span data-ttu-id="39c95-181">Bunlar kodunuz tarafından açıkça çağrılmadığı için, adlandırmalarına yönelik açık olması önemli değildir.</span><span class="sxs-lookup"><span data-stu-id="39c95-181">Because these are not explicitly called by your code, being explicit about their naming isn’t as important.</span></span>

* <span data-ttu-id="39c95-182">`async void` **yalnızca olay işleyicileri için kullanılmalıdır.**</span><span class="sxs-lookup"><span data-stu-id="39c95-182">`async void` **should only be used for event handlers.**</span></span>

<span data-ttu-id="39c95-183">`async void`, zaman uyumsuz olay işleyicilerinin çalışmasına izin veren tek yoldur çünkü olaylar dönüş türlerine sahip değildir (Bu nedenle `Task` ve `Task<T>`kullanamaz).</span><span class="sxs-lookup"><span data-stu-id="39c95-183">`async void` is the only way to allow asynchronous event handlers to work because events do not have return types (thus cannot make use of `Task` and `Task<T>`).</span></span> <span data-ttu-id="39c95-184">`async void` diğer tüm kullanımı, dokunma modelini takip etmez ve şu gibi kullanımı zor olabilir:</span><span class="sxs-lookup"><span data-stu-id="39c95-184">Any other use of `async void` does not follow the TAP model and can be challenging to use, such as:</span></span>

* <span data-ttu-id="39c95-185">`async void` yöntemde oluşturulan özel durumlar, bu yöntemin dışında yakalanamıyor.</span><span class="sxs-lookup"><span data-stu-id="39c95-185">Exceptions thrown in an `async void` method can’t be caught outside of that method.</span></span>
* <span data-ttu-id="39c95-186">`async void` yöntemlerinin test edilmesi çok zordur.</span><span class="sxs-lookup"><span data-stu-id="39c95-186">`async void` methods are very difficult to test.</span></span>
* <span data-ttu-id="39c95-187">`async void` Yöntemler, çağıranın zaman uyumsuz olmasını beklemiyorsanız hatalı yan etkilere neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="39c95-187">`async void` methods can cause bad side effects if the caller isn’t expecting them to be async.</span></span>

* <span data-ttu-id="39c95-188">**LINQ ifadelerinde zaman uyumsuz Lambdalar kullanırken Tread dikkatlice**</span><span class="sxs-lookup"><span data-stu-id="39c95-188">**Tread carefully when using async lambdas in LINQ expressions**</span></span>

<span data-ttu-id="39c95-189">LINQ kullanım içindeki lambda ifadeleri ertelenmiş yürütme, bu kodun bir kez çalıştırılmasını beklemiyorduk.</span><span class="sxs-lookup"><span data-stu-id="39c95-189">Lambda expressions in LINQ use deferred execution, meaning code could end up executing at a time when you’re not expecting it to.</span></span> <span data-ttu-id="39c95-190">Bu görevin engellenmesi, doğru yazılmayan bir kilitlenmeye neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="39c95-190">The introduction of blocking tasks into this can easily result in a deadlock if not written correctly.</span></span> <span data-ttu-id="39c95-191">Ayrıca, bu gibi zaman uyumsuz kodun iç içe geçirilmesi, kodun yürütülmesi ile ilgili nedenlerle da daha zor hale gelir.</span><span class="sxs-lookup"><span data-stu-id="39c95-191">Additionally, the nesting of asynchronous code like this can also make it more difficult to reason about the execution of the code.</span></span> <span data-ttu-id="39c95-192">Async ve LINQ güçlü, ancak mümkün olduğunca dikkatli ve açık olarak kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="39c95-192">Async and LINQ are powerful, but should be used together as carefully and clearly as possible.</span></span>

* <span data-ttu-id="39c95-193">**Görevleri engellenmeyen bir şekilde beklede bir kod yazın**</span><span class="sxs-lookup"><span data-stu-id="39c95-193">**Write code that awaits Tasks in a non-blocking manner**</span></span>

<span data-ttu-id="39c95-194">Görevin tamamlanmasını beklemek için geçerli iş parçacığını engellemek, kilitlenmeleri ve engellenen bağlam iş parçacıklarının oluşmasına neden olabilir ve önemli ölçüde daha karmaşık hata işleme gerektirebilir.</span><span class="sxs-lookup"><span data-stu-id="39c95-194">Blocking the current thread as a means to wait for a Task to complete can result in deadlocks and blocked context threads, and can require significantly more complex error-handling.</span></span> <span data-ttu-id="39c95-195">Aşağıdaki tabloda, engellenmeyen bir şekilde görevlerin beklenmesiyle ilgili yönergeler sağlanmaktadır:</span><span class="sxs-lookup"><span data-stu-id="39c95-195">The following table provides guidance on how to deal with waiting for Tasks in a non-blocking way:</span></span>

| <span data-ttu-id="39c95-196">Bunu kullan...</span><span class="sxs-lookup"><span data-stu-id="39c95-196">Use this...</span></span> | <span data-ttu-id="39c95-197">Bunun yerine...</span><span class="sxs-lookup"><span data-stu-id="39c95-197">Instead of this...</span></span> | <span data-ttu-id="39c95-198">Bunu yapmak için</span><span class="sxs-lookup"><span data-stu-id="39c95-198">When wishing to do this</span></span> |
| --- | --- | --- |
| `await` | <span data-ttu-id="39c95-199">`Task.Wait` veya `Task.Result`</span><span class="sxs-lookup"><span data-stu-id="39c95-199">`Task.Wait` or `Task.Result`</span></span> | <span data-ttu-id="39c95-200">Arka plan görevinin sonucunu alma</span><span class="sxs-lookup"><span data-stu-id="39c95-200">Retrieving the result of a background task</span></span> |
| `await Task.WhenAny` | `Task.WaitAny` | <span data-ttu-id="39c95-201">Herhangi bir görevin tamamlanması bekleniyor</span><span class="sxs-lookup"><span data-stu-id="39c95-201">Waiting for any task to complete</span></span> |
| `await Task.WhenAll` | `Task.WaitAll` | <span data-ttu-id="39c95-202">Tüm görevlerin tamamlanması bekleniyor</span><span class="sxs-lookup"><span data-stu-id="39c95-202">Waiting for all tasks to complete</span></span> |
| `await Task.Delay` | `Thread.Sleep` | <span data-ttu-id="39c95-203">Bir süre bekleniyor</span><span class="sxs-lookup"><span data-stu-id="39c95-203">Waiting for a period of time</span></span> |

* <span data-ttu-id="39c95-204">**Daha az durum bilgisi olan kod yazma**</span><span class="sxs-lookup"><span data-stu-id="39c95-204">**Write less stateful code**</span></span>

<span data-ttu-id="39c95-205">Genel nesnelerin durumuna veya belirli yöntemlerin yürütülmesine bağlı değildir.</span><span class="sxs-lookup"><span data-stu-id="39c95-205">Don’t depend on the state of global objects or the execution of certain methods.</span></span> <span data-ttu-id="39c95-206">Bunun yerine, yalnızca yöntemlerin dönüş değerlerine göre değişir.</span><span class="sxs-lookup"><span data-stu-id="39c95-206">Instead, depend only on the return values of methods.</span></span> <span data-ttu-id="39c95-207">Neden?</span><span class="sxs-lookup"><span data-stu-id="39c95-207">Why?</span></span>

* <span data-ttu-id="39c95-208">Kodun nedeni daha kolay olacaktır.</span><span class="sxs-lookup"><span data-stu-id="39c95-208">Code will be easier to reason about.</span></span>
* <span data-ttu-id="39c95-209">Kodun test etmek daha kolay olacaktır.</span><span class="sxs-lookup"><span data-stu-id="39c95-209">Code will be easier to test.</span></span>
* <span data-ttu-id="39c95-210">Zaman uyumsuz ve zaman uyumlu kodu karıştırma çok basittir.</span><span class="sxs-lookup"><span data-stu-id="39c95-210">Mixing async and synchronous code is far simpler.</span></span>
* <span data-ttu-id="39c95-211">Yarış koşullarından genellikle tamamen kaçınılabilir.</span><span class="sxs-lookup"><span data-stu-id="39c95-211">Race conditions can typically be avoided altogether.</span></span>
* <span data-ttu-id="39c95-212">Dönüş değerlerine bağlı olarak, zaman uyumsuz kod koordine etme basit hale gelir.</span><span class="sxs-lookup"><span data-stu-id="39c95-212">Depending on return values makes coordinating async code simple.</span></span>
* <span data-ttu-id="39c95-213">(Ödül) bağımlılık ekleme ile oldukça iyi bir şekilde çalışmaktadır.</span><span class="sxs-lookup"><span data-stu-id="39c95-213">(Bonus) it works really well with dependency injection.</span></span>

<span data-ttu-id="39c95-214">Önerilen bir amaç, kodunuzda tam veya neredeyse tam bir [bilgi saydamlığı](https://en.wikipedia.org/wiki/Referential_transparency_%28computer_science%29) elde etmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="39c95-214">A recommended goal is to achieve complete or near-complete [Referential Transparency](https://en.wikipedia.org/wiki/Referential_transparency_%28computer_science%29) in your code.</span></span> <span data-ttu-id="39c95-215">Bunun yapılması, son derece öngörülebilir, test edilebilir ve sürdürülebilir kod temeli oluşmasına neden olur.</span><span class="sxs-lookup"><span data-stu-id="39c95-215">Doing so will result in an extremely predictable, testable, and maintainable codebase.</span></span>

## <a name="other-resources"></a><span data-ttu-id="39c95-216">Diğer Kaynaklar</span><span class="sxs-lookup"><span data-stu-id="39c95-216">Other Resources</span></span>

* <span data-ttu-id="39c95-217">[Zaman uyumsuz kapsamlı,](../standard/async-in-depth.md) görevlerin nasıl çalıştığı hakkında daha fazla bilgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="39c95-217">[Async in-depth](../standard/async-in-depth.md) provides more information about how Tasks work.</span></span>
* [<span data-ttu-id="39c95-218">Async ve await (C#) ile zaman uyumsuz programlama</span><span class="sxs-lookup"><span data-stu-id="39c95-218">Asynchronous programming with async and await (C#)</span></span>](./programming-guide/concepts/async/index.md)
* <span data-ttu-id="39c95-219">Zaman uyumsuz programlama için Lucian Wıchık 'nin [altı temel ipucu](https://channel9.msdn.com/Series/Three-Essential-Tips-for-Async) , Async programlama için harika bir kaynaktır</span><span class="sxs-lookup"><span data-stu-id="39c95-219">Lucian Wischik's [Six Essential Tips for Async](https://channel9.msdn.com/Series/Three-Essential-Tips-for-Async) are a wonderful resource for async programming</span></span>
