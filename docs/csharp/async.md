---
title: Zaman uyumsuz programlama-C#
description: .NET Core tarafından sağlanan C# dil düzeyi zaman uyumsuz programlama modeli hakkında bilgi edinin.
author: cartermp
ms.date: 06/20/2016
ms.assetid: b878c34c-a78f-419e-a594-a2b44fa521a4
ms.custom: seodec18
ms.openlocfilehash: a36f4a6f01c4e11429fda3a3022b4092e98db6cf
ms.sourcegitcommit: 79066169e93d9d65203028b21983574ad9dcf6b4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/01/2019
ms.locfileid: "57212215"
---
# <a name="asynchronous-programming"></a><span data-ttu-id="8921d-103">Zaman uyumsuz programlama</span><span class="sxs-lookup"><span data-stu-id="8921d-103">Asynchronous programming</span></span>

<span data-ttu-id="8921d-104">(Örneğin, bir ağ üzerinden veri isteme veya bir veritabanına erişirken) tüm miyim/O-bağlı gereksinimleriniz varsa, zaman uyumsuz programlama kullanmak isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8921d-104">If you have any I/O-bound needs (such as requesting data from a network or accessing a database), you'll want to utilize asynchronous programming.</span></span>  <span data-ttu-id="8921d-105">Ayrıca, zaman uyumsuz kod yazmak için iyi bir senaryodur pahalı bir hesaplama gerçekleştirmek gibi CPU bağımlı kod da olabilir.</span><span class="sxs-lookup"><span data-stu-id="8921d-105">You could also have CPU-bound code, such as performing an expensive calculation, which is also a good scenario for writing async code.</span></span>

<span data-ttu-id="8921d-106">C# kolayca geri çağırmaları juggle veya faaliyetler destekleyen bir kitaplığa uymak zorunda kalmadan zaman uyumsuz kod yazmak için izin veren bir dil düzeyinde zaman uyumsuz programlama modeli vardır.</span><span class="sxs-lookup"><span data-stu-id="8921d-106">C# has a language-level asynchronous programming model which allows for easily writing asynchronous code without having to juggle callbacks or conform to a library which supports asynchrony.</span></span> <span data-ttu-id="8921d-107">Olarak bilinen takip eden [görev tabanlı zaman uyumsuz desen (TAP)](../standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md).</span><span class="sxs-lookup"><span data-stu-id="8921d-107">It follows what is known as the [Task-based Asynchronous Pattern (TAP)](../standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md).</span></span>

## <a name="basic-overview-of-the-asynchronous-model"></a><span data-ttu-id="8921d-108">Zaman uyumsuz Model temel genel bakış</span><span class="sxs-lookup"><span data-stu-id="8921d-108">Basic Overview of the Asynchronous Model</span></span>

<span data-ttu-id="8921d-109">Zaman uyumsuz programlamanın temel `Task` ve `Task<T>` zaman uyumsuz işlemler model nesneleri.</span><span class="sxs-lookup"><span data-stu-id="8921d-109">The core of async programming is the `Task` and `Task<T>` objects, which model asynchronous operations.</span></span>  <span data-ttu-id="8921d-110">Tarafından desteklenen `async` ve `await` anahtar sözcükleri.</span><span class="sxs-lookup"><span data-stu-id="8921d-110">They are supported by the `async` and `await` keywords.</span></span>  <span data-ttu-id="8921d-111">Çoğu durumda modeli oldukça basittir:</span><span class="sxs-lookup"><span data-stu-id="8921d-111">The model is fairly simple in most cases:</span></span>

<span data-ttu-id="8921d-112">Ben/O-bağlama kodunu, `await` döndüren bir işlem bir `Task` veya `Task<T>` içine bir `async` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="8921d-112">For I/O-bound code, you `await` an operation which returns a `Task` or `Task<T>` inside of an `async` method.</span></span>

<span data-ttu-id="8921d-113">CPU bağımlı kod için `await` ile arka plan iş parçacığında başlatılan bir işlem `Task.Run` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="8921d-113">For CPU-bound code, you `await` an operation which is started on a background thread with the `Task.Run` method.</span></span>

<span data-ttu-id="8921d-114">`await` Anahtar sözcüğü, burada sihrin.</span><span class="sxs-lookup"><span data-stu-id="8921d-114">The `await` keyword is where the magic happens.</span></span> <span data-ttu-id="8921d-115">Gerçekleştirilen bir yöntemi çağıran kişi için Denetim verir `await`, ve sonuçta bir kullanıcı Arabirimi yanıt vermesi veya esnek bir şekilde bir hizmet sağlar.</span><span class="sxs-lookup"><span data-stu-id="8921d-115">It yields control to the caller of the method that performed `await`, and it ultimately allows a UI to be responsive or a service to be elastic.</span></span>

<span data-ttu-id="8921d-116">Yaklaşım daha zaman uyumsuz kod için başka bir yöntemle `async` ve `await` DOKUNUN makaleyi, yukarıda bağlantı bölümünde açıklanan, ancak bu belgede, bu noktadan itibaren dil düzeyinde yapılar üzerinde odaklanır.</span><span class="sxs-lookup"><span data-stu-id="8921d-116">There are other ways to approach async code than `async` and `await` outlined in the TAP article linked above, but this document will focus on the language-level constructs from this point forward.</span></span>

### <a name="io-bound-example-downloading-data-from-a-web-service"></a><span data-ttu-id="8921d-117">Ben/O-bağlı örnek: Bir web hizmetinden veri indirme</span><span class="sxs-lookup"><span data-stu-id="8921d-117">I/O-Bound Example: Downloading data from a web service</span></span>

<span data-ttu-id="8921d-118">Bir düğmeye basıldığında, bazı veriler bir web hizmetinden indirmeniz gerekebilir ancak UI iş parçacığını engellemesini istemiyorsanız.</span><span class="sxs-lookup"><span data-stu-id="8921d-118">You may need to download some data from a web service when a button is pressed, but don’t want to block the UI thread.</span></span> <span data-ttu-id="8921d-119">Yalnızca şu şekilde gerçekleştirilebilir:</span><span class="sxs-lookup"><span data-stu-id="8921d-119">It can be accomplished simply like this:</span></span>

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

<span data-ttu-id="8921d-120">Ve İşte bu kadar!</span><span class="sxs-lookup"><span data-stu-id="8921d-120">And that’s it!</span></span> <span data-ttu-id="8921d-121">Kod (bazı veriler zaman uyumsuz olarak yükleme) amacı, görev nesnelerle etkileşim içinde çıkmaza olmadan ifade eder.</span><span class="sxs-lookup"><span data-stu-id="8921d-121">The code expresses the intent (downloading some data asynchronously) without getting bogged down in interacting with Task objects.</span></span>

### <a name="cpu-bound-example-performing-a-calculation-for-a-game"></a><span data-ttu-id="8921d-122">CPU bağımlı örnek: Bir hesaplama gerçekleştirmek için bir oyun</span><span class="sxs-lookup"><span data-stu-id="8921d-122">CPU-bound Example: Performing a Calculation for a Game</span></span>

<span data-ttu-id="8921d-123">Burada bir düğmeye basarak zarar ekranında birçok düşman üzerinde başını ağrıtabilir mobil oyun yazdığınız varsayalım.</span><span class="sxs-lookup"><span data-stu-id="8921d-123">Say you're writing a mobile game where pressing a button can inflict damage on many enemies on the screen.</span></span>  <span data-ttu-id="8921d-124">Zarar hesaplama gerçekleştirmek pahalı olabilir ve kullanıcı Arabirimi iş parçacığında yapılması oyun hesaplama gerçekleştirildiği duraklatmak için görünür hale getirir!</span><span class="sxs-lookup"><span data-stu-id="8921d-124">Performing the damage calculation can be expensive, and doing it on the UI thread would make the game appear to pause as the calculation is performed!</span></span>

<span data-ttu-id="8921d-125">Bu durumu çözmek için en iyi yolu kullanarak iş yapan bir arka plan iş parçacığı olan `Task.Run`, ve `await` sonucu.</span><span class="sxs-lookup"><span data-stu-id="8921d-125">The best way to handle this is to start a background thread which does the work using `Task.Run`, and `await` its result.</span></span>  <span data-ttu-id="8921d-126">Bu, UI iş bitti olarak kesintisiz düşünüyorsanız olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="8921d-126">This will allow the UI to feel smooth as the work is being done.</span></span>

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

<span data-ttu-id="8921d-127">Ve İşte bu kadar!</span><span class="sxs-lookup"><span data-stu-id="8921d-127">And that's it!</span></span>  <span data-ttu-id="8921d-128">Bu kodun amacı düzgün bir şekilde ifade düğmenin olay'ı tıklatın, bir arka plan iş parçacığı el ile yönetme gerektirmez ve engelleyici olmayan bir yolla bunu yapar.</span><span class="sxs-lookup"><span data-stu-id="8921d-128">This code cleanly expresses the intent of the button's click event, it doesn't require managing a background thread manually, and it does so in a non-blocking way.</span></span>

### <a name="what-happens-under-the-covers"></a><span data-ttu-id="8921d-129">Bu işlem arka planda ne olur?</span><span class="sxs-lookup"><span data-stu-id="8921d-129">What happens under the covers</span></span>

<span data-ttu-id="8921d-130">Birçok hareketli parça nerede zaman uyumsuz işlemler ilgilenir yoktur.</span><span class="sxs-lookup"><span data-stu-id="8921d-130">There's a lot of moving pieces where asynchronous operations are concerned.</span></span>  <span data-ttu-id="8921d-131">Aslında neler olduğu hakkında merak `Task` ve `Task<T>`, kullanıma alma [ayrıntılı zaman uyumsuz](../standard/async-in-depth.md) makale daha fazla bilgi için.</span><span class="sxs-lookup"><span data-stu-id="8921d-131">If you're curious about what's happening underneath the covers of `Task` and `Task<T>`, checkout the [Async in-depth](../standard/async-in-depth.md) article for more information.</span></span>

<span data-ttu-id="8921d-132">C# tarafında nesnelerin interneti, derleyici, kodunuzun yürütme sonuçlanmıyor gibi şeyler ve bir Durum makinesi dönüştüren olduğunda bir `await` ulaştı ve sürdürme yürütmesi bir arka plan işi tamamlandığında.</span><span class="sxs-lookup"><span data-stu-id="8921d-132">On the C# side of things, the compiler transforms your code into a state machine which keeps track of things like yielding execution when an `await` is reached and resuming execution when a background job has finished.</span></span>

<span data-ttu-id="8921d-133">Teorik olarak-yazmaya için bu uygulamasıdır [faaliyetler Promise modelinin](https://en.wikipedia.org/wiki/Futures_and_promises).</span><span class="sxs-lookup"><span data-stu-id="8921d-133">For the theoretically-inclined, this is an implementation of the [Promise Model of asynchrony](https://en.wikipedia.org/wiki/Futures_and_promises).</span></span>

## <a name="key-pieces-to-understand"></a><span data-ttu-id="8921d-134">Temel Parçalar aşağıda anlamanın</span><span class="sxs-lookup"><span data-stu-id="8921d-134">Key Pieces to Understand</span></span>

* <span data-ttu-id="8921d-135">Zaman uyumsuz kod, ı/O-bağlı hem de CPU bağımlı kod ancak farklı her senaryo için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="8921d-135">Async code can be used for both I/O-bound and CPU-bound code, but differently for each scenario.</span></span>
* <span data-ttu-id="8921d-136">Zaman uyumsuz kod `Task<T>` ve `Task`, model çalışma arka planda yapılması için kullanılan yapıları olduğu.</span><span class="sxs-lookup"><span data-stu-id="8921d-136">Async code uses `Task<T>` and `Task`, which are constructs used to model work being done in the background.</span></span>
* <span data-ttu-id="8921d-137">`async` Anahtar sözcüğü bir yöntem kullanmanıza olanak tanıyan bir zaman uyumsuz yönteme bırakır `await` gövdesinde anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="8921d-137">The `async` keyword turns a method into an async method, which allows you to use the `await` keyword in its body.</span></span>
* <span data-ttu-id="8921d-138">Zaman `await` anahtar sözcüğü uygulanırsa, çağıran yöntem askıya alır ve beklenen görev tamamlanana kadar denetim çağırana geri verir.</span><span class="sxs-lookup"><span data-stu-id="8921d-138">When the `await` keyword is applied, it suspends the calling method and yields control back to its caller until the awaited task is complete.</span></span>
* <span data-ttu-id="8921d-139">`await` yalnızca zaman uyumsuz bir yöntem içinde kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="8921d-139">`await` can only be used inside an async method.</span></span>

## <a name="recognize-cpu-bound-and-io-bound-work"></a><span data-ttu-id="8921d-140">CPU bağımlı ve ben/O-bağlı iş tanıması</span><span class="sxs-lookup"><span data-stu-id="8921d-140">Recognize CPU-Bound and I/O-Bound Work</span></span>

<span data-ttu-id="8921d-141">Bu kılavuzun ilk iki örnek gösterdi nasıl kullanabileceğinizi `async` ve `await` miyim/O-bağlı ve CPU bağımlı iş için.</span><span class="sxs-lookup"><span data-stu-id="8921d-141">The first two examples of this guide showed how you can use `async` and `await` for I/O-bound and CPU-bound work.</span></span>  <span data-ttu-id="8921d-142">Bir işi yapmak ihtiyaç duyduğunuzda, tanımlayabilirsiniz, anahtar miyim/O-bağlı veya CPU sınırlıdır, kodunuzun performansını önemli ölçüde etkileyebilir ve potansiyel olarak olabilir çünkü kötüye adayı belirli oluşturur.</span><span class="sxs-lookup"><span data-stu-id="8921d-142">It's key that you can identify when a job you need to do is I/O-bound or CPU-bound, because it can greatly affect the performance of your code and could potentially lead to misusing certain constructs.</span></span>

<span data-ttu-id="8921d-143">Herhangi bir kod yazmadan önce istemelisiniz iki sorular şunlardır:</span><span class="sxs-lookup"><span data-stu-id="8921d-143">Here are two questions you should ask before you write any code:</span></span>

1. <span data-ttu-id="8921d-144">Kodunuzu "veritabanından veri gibi bir şey için bekleyeceği süreye"?</span><span class="sxs-lookup"><span data-stu-id="8921d-144">Will your code be "waiting" for something, such as data from a database?</span></span>

    <span data-ttu-id="8921d-145">"Evet" aradığınız cevaptır sonra iş **miyim/O-bağlı**.</span><span class="sxs-lookup"><span data-stu-id="8921d-145">If your answer is "yes", then your work is **I/O-bound**.</span></span>

2. <span data-ttu-id="8921d-146">Kodunuzu çok pahalı bir hesaplama gerçekleştiren?</span><span class="sxs-lookup"><span data-stu-id="8921d-146">Will your code be performing a very expensive computation?</span></span>

    <span data-ttu-id="8921d-147">"Evet" yanıtlanmış sonra iş **CPU bağımlı**.</span><span class="sxs-lookup"><span data-stu-id="8921d-147">If you answered "yes", then your work is **CPU-bound**.</span></span>

<span data-ttu-id="8921d-148">Sahip olduğunuz iş ise **miyim/O-bağlı**, kullanın `async` ve `await` *olmadan* `Task.Run`.</span><span class="sxs-lookup"><span data-stu-id="8921d-148">If the work you have is **I/O-bound**, use `async` and `await` *without* `Task.Run`.</span></span>  <span data-ttu-id="8921d-149">*Barındırmamalıdır* görev paralel Kitaplığı'nı kullanın.</span><span class="sxs-lookup"><span data-stu-id="8921d-149">You *should not* use the Task Parallel Library.</span></span>  <span data-ttu-id="8921d-150">Bunun nedeni açıklandığı [zaman uyumsuz derinliği makaledeki](../standard/async-in-depth.md).</span><span class="sxs-lookup"><span data-stu-id="8921d-150">The reason for this is outlined in the [Async in Depth article](../standard/async-in-depth.md).</span></span>

<span data-ttu-id="8921d-151">Sahip olduğunuz iş ise **CPU bağımlı** ve yanıtlama hakkında kullanım verdiğiniz `async` ve `await` ancak başka bir iş parçacığında iş devre dışı üretme *ile* `Task.Run`.</span><span class="sxs-lookup"><span data-stu-id="8921d-151">If the work you have is **CPU-bound** and you care about responsiveness, use `async` and `await` but spawn the work off on another thread *with* `Task.Run`.</span></span>  <span data-ttu-id="8921d-152">İş eşzamanlılığı ve paralelliği için uygun değilse, ayrıca kullanmayı düşünmeniz gerekir [görev paralel Kitaplığı](../standard/parallel-programming/task-parallel-library-tpl.md).</span><span class="sxs-lookup"><span data-stu-id="8921d-152">If the work is appropriate for concurrency and parallelism, you should also consider using the [Task Parallel Library](../standard/parallel-programming/task-parallel-library-tpl.md).</span></span>

<span data-ttu-id="8921d-153">Ayrıca, her zaman kodunuzun yürütülmesini ölçü.</span><span class="sxs-lookup"><span data-stu-id="8921d-153">Additionally, you should always measure the execution of your code.</span></span>  <span data-ttu-id="8921d-154">Örneğin, kendinizi CPU bağımlı iş olduğu pahalı bir durumda bulabilirsiniz yeterli bağlam anahtarları çoklu iş parçacığı zaman ek yükü ile karşılaştırılır.</span><span class="sxs-lookup"><span data-stu-id="8921d-154">For example, you may find yourself in a situation where your CPU-bound work is not costly enough compared with the overhead of context switches when multithreading.</span></span>  <span data-ttu-id="8921d-155">Kendi tradeoff her seçeneği vardır ve kendi durumunuza doğru artırabilen seçmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="8921d-155">Every choice has its tradeoff, and you should pick the correct tradeoff for your situation.</span></span>

## <a name="more-examples"></a><span data-ttu-id="8921d-156">Daha fazla örnek</span><span class="sxs-lookup"><span data-stu-id="8921d-156">More Examples</span></span>

<span data-ttu-id="8921d-157">Aşağıdaki örnekler, zaman uyumsuz kodu C# içinde yazabileceğiniz çeşitli şekillerde gösterir.</span><span class="sxs-lookup"><span data-stu-id="8921d-157">The following examples demonstrate various ways you can write async code in C#.</span></span>  <span data-ttu-id="8921d-158">Bunlar arasında gelebilir birkaç farklı senaryoları kapsar.</span><span class="sxs-lookup"><span data-stu-id="8921d-158">They cover a few different scenarios you may come across.</span></span>

### <a name="extracting-data-from-a-network"></a><span data-ttu-id="8921d-159">Ağ üzerinden veri ayıklama</span><span class="sxs-lookup"><span data-stu-id="8921d-159">Extracting Data from a Network</span></span>

<span data-ttu-id="8921d-160">Bu kod parçacığı giriş sayfasının HTML indirir [www.dotnetfoundation.org](https://www.dotnetfoundation.org) ve ".NET" dize gerçekleşir HTML'de sayısını sayar.</span><span class="sxs-lookup"><span data-stu-id="8921d-160">This snippet downloads the HTML from the homepage at [www.dotnetfoundation.org](https://www.dotnetfoundation.org) and counts the number of times the string ".NET" occurs in the HTML.</span></span>  <span data-ttu-id="8921d-161">ASP.NET MVC sayısı, bu görevi gerçekleştiren bir web denetleyicisi yöntemi tanımlamak için kullanır.</span><span class="sxs-lookup"><span data-stu-id="8921d-161">It uses ASP.NET MVC to define a web controller method which performs this task, returning the number.</span></span>

> [!NOTE]
> <span data-ttu-id="8921d-162">HTML Ayrıştırma üretim kodunda yapmayı planlıyorsanız, normal ifadeler kullanmayın.</span><span class="sxs-lookup"><span data-stu-id="8921d-162">If you plan on doing HTML parsing in production code, don't use regular expressions.</span></span> <span data-ttu-id="8921d-163">Bunun yerine bir ayrıştırma kitaplığını kullanın.</span><span class="sxs-lookup"><span data-stu-id="8921d-163">Use a parsing library instead.</span></span>

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

<span data-ttu-id="8921d-164">Bir evrensel Windows bir düğmeye basıldığında aynı görevi gerçekleştiren uygulama için yazılmış aynı senaryo aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="8921d-164">Here's the same scenario written for a Universal Windows App, which performs the same task when a Button is pressed:</span></span>

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
    // This is what allows the app to be responsive and not hang on the UI thread.
    var html = await getDotNetFoundationHtmlTask;
    int count = Regex.Matches(html, @"\.NET").Count;

    DotNetCountLabel.Text = $"Number of .NETs on dotnetfoundation.org: {count}";

    NetworkProgressBar.IsEnabled = false;
    NetworkProgressBar.Visibility = Visibility.Collapsed;
}
```

### <a name="waiting-for-multiple-tasks-to-complete"></a><span data-ttu-id="8921d-165">Birden çok görevin tamamlanması bekleniyor</span><span class="sxs-lookup"><span data-stu-id="8921d-165">Waiting for Multiple Tasks to Complete</span></span>

<span data-ttu-id="8921d-166">Aynı anda birden çok parça veri almak için gerek duyduğunuz bir durumda kendinizi bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8921d-166">You may find yourself in a situation where you need to retrieve multiple pieces of data concurrently.</span></span>  <span data-ttu-id="8921d-167">`Task` API içeren iki yöntem `Task.WhenAll` ve `Task.WhenAny` engelleyici olmayan bir bekleme birden fazla arka plan işleri yapan zaman uyumsuz kod yazma sağlar.</span><span class="sxs-lookup"><span data-stu-id="8921d-167">The `Task` API contains two methods, `Task.WhenAll` and `Task.WhenAny` which allow you to write asynchronous code which performs a non-blocking wait on multiple background jobs.</span></span>

<span data-ttu-id="8921d-168">Bu örnek nasıl alın gösterir `User` veri kümesi için `userId`s.</span><span class="sxs-lookup"><span data-stu-id="8921d-168">This example shows how you might grab `User` data for a set of `userId`s.</span></span>

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

<span data-ttu-id="8921d-169">LINQ kullanarak bu biraz daha temellerini yazmak için başka bir yolu şu şekildedir:</span><span class="sxs-lookup"><span data-stu-id="8921d-169">Here's another way to write this a bit more succinctly, using LINQ:</span></span>

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

<span data-ttu-id="8921d-170">Bu daha az kod olsa da, LINQ ile zaman uyumsuz kod kullanırken dikkatli olun.</span><span class="sxs-lookup"><span data-stu-id="8921d-170">Although it's less code, take care when mixing LINQ with asynchronous code.</span></span>  <span data-ttu-id="8921d-171">LINQ (lazy) ertelenmiş yürütme kullandığından, zaman uyumsuz çağrılar yapmasını hemen gerçekleşmez bir `foreach()` çağrısı ile yinelemek için oluşturulan sıralı zorla sürece döngü `.ToList()` veya `.ToArray()`.</span><span class="sxs-lookup"><span data-stu-id="8921d-171">Because LINQ uses deferred (lazy) execution, async calls won't happen immediately as they do in a `foreach()` loop unless you force the generated sequence to iterate with a call to `.ToList()` or `.ToArray()`.</span></span>

## <a name="important-info-and-advice"></a><span data-ttu-id="8921d-172">Önemli bilgiler ve öneriler</span><span class="sxs-lookup"><span data-stu-id="8921d-172">Important Info and Advice</span></span>

<span data-ttu-id="8921d-173">Zaman uyumsuz programlama oldukça basit olsa da, bazı ayrıntılar olduğu beklemeyen davranışı önlemek akılda tutulması gereken vardır.</span><span class="sxs-lookup"><span data-stu-id="8921d-173">Although async programming is relatively straightforward, there are some details to keep in mind which can prevent unexpected behavior.</span></span>

* <span data-ttu-id="8921d-174">`async` **yöntemleri olması gerekir bir** `await` **gövde anahtar sözcük veya hiçbir zaman verecek!**</span><span class="sxs-lookup"><span data-stu-id="8921d-174">`async` **methods need to have an** `await` **keyword in their body or they will never yield!**</span></span>

<span data-ttu-id="8921d-175">Bu, göz önünde bulundurmanız önemlidir.</span><span class="sxs-lookup"><span data-stu-id="8921d-175">This is important to keep in mind.</span></span>  <span data-ttu-id="8921d-176">Varsa `await` gövdesinde kullanılmayan bir `async` yöntemi, bir uyarı üretir C# Derleyici olacaktır, ancak kod olacak derleyin ve normal bir yöntemi gibi çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="8921d-176">If `await` is not used in the body of an `async` method, the C# compiler will generate a warning, but the code will compile and run as if it were a normal method.</span></span>  <span data-ttu-id="8921d-177">Zaman uyumsuz yöntemi için C# Derleyici tarafından oluşturulan Durum makinesi herhangi bir şey yerine getirmeye olabilir değil olarak bu de son derece verimli olacaktır.</span><span class="sxs-lookup"><span data-stu-id="8921d-177">Note that this would also be incredibly inefficient, as the state machine generated by the C# compiler for the async method would not be accomplishing anything.</span></span>

* <span data-ttu-id="8921d-178">**"Async" soneki yazdığınız her zaman uyumsuz yöntem adı eklemeniz gerekir.**</span><span class="sxs-lookup"><span data-stu-id="8921d-178">**You should add "Async" as the suffix of every async method name you write.**</span></span>

<span data-ttu-id="8921d-179">. NET'te zaman uyumlu ve zaman uyumsuz yöntemleri daha kolay ayırt etmek için kullanılan kuraldır.</span><span class="sxs-lookup"><span data-stu-id="8921d-179">This is the convention used in .NET to more-easily differentiate synchronous and asynchronous methods.</span></span> <span data-ttu-id="8921d-180">Açıkça (örneğin, olay işleyicileri veya web denetleyici yöntemleri) kod tarafından çağrılan olmayan bazı yöntemler mutlaka geçerli değildir unutmayın.</span><span class="sxs-lookup"><span data-stu-id="8921d-180">Note that certain methods which aren’t explicitly called by your code (such as event handlers or web controller methods) don’t necessarily apply.</span></span> <span data-ttu-id="8921d-181">Bunlar açıkça kodunuz tarafından çağrılır değil, kendi adlandırma hakkında açık olan önemli değildir.</span><span class="sxs-lookup"><span data-stu-id="8921d-181">Because these are not explicitly called by your code, being explicit about their naming isn’t as important.</span></span>

* <span data-ttu-id="8921d-182">`async void` **yalnızca olay işleyicileri için kullanılmalıdır.**</span><span class="sxs-lookup"><span data-stu-id="8921d-182">`async void` **should only be used for event handlers.**</span></span>

<span data-ttu-id="8921d-183">`async void` olaylar, dönüş türleri olmadığı için çalışması zaman uyumsuz olay işleyicileri izin vermek için tek yolu (Bu nedenle yapılamıyor kullanım `Task` ve `Task<T>`).</span><span class="sxs-lookup"><span data-stu-id="8921d-183">`async void` is the only way to allow asynchronous event handlers to work because events do not have return types (thus cannot make use of `Task` and `Task<T>`).</span></span> <span data-ttu-id="8921d-184">Başka bir kullanımını `async void` DOKUNUN model izlemez ve gibi kullanmak zor olabilir:</span><span class="sxs-lookup"><span data-stu-id="8921d-184">Any other use of `async void` does not follow the TAP model and can be challenging to use, such as:</span></span>

* <span data-ttu-id="8921d-185">Oluşturulan özel durumlar bir `async void` yöntemi bu yöntemi dışında yakalandı olamaz.</span><span class="sxs-lookup"><span data-stu-id="8921d-185">Exceptions thrown in an `async void` method can’t be caught outside of that method.</span></span>
* <span data-ttu-id="8921d-186">`async void` yöntemleri test etmek çok zordur.</span><span class="sxs-lookup"><span data-stu-id="8921d-186">`async void` methods are very difficult to test.</span></span>
* <span data-ttu-id="8921d-187">`async void` çağırana zaman uyumsuz olarak bekleniyor olmayan yöntemleri hatalı yan etkilere neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="8921d-187">`async void` methods can cause bad side effects if the caller isn’t expecting them to be async.</span></span>

* <span data-ttu-id="8921d-188">**Zaman uyumsuz lambda ifadeleri LINQ ifadelerinde kullanırken dikkatli bir şekilde tread**</span><span class="sxs-lookup"><span data-stu-id="8921d-188">**Tread carefully when using async lambdas in LINQ expressions**</span></span>

<span data-ttu-id="8921d-189">Lambda ifadeleri LINQ ertelenmiş yürütme kullanın, anlamı kod zaman kendisine beklediğiniz olmayan bir zaman yürütme bitiş.</span><span class="sxs-lookup"><span data-stu-id="8921d-189">Lambda expressions in LINQ use deferred execution, meaning code could end up executing at a time when you’re not expecting it to.</span></span> <span data-ttu-id="8921d-190">Bu görevleri engelleme giriş kolayca bir kilitlenmeyle doğru yazılmaz neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="8921d-190">The introduction of blocking tasks into this can easily result in a deadlock if not written correctly.</span></span> <span data-ttu-id="8921d-191">Ayrıca, bu gibi zaman uyumsuz kod iç içe Ayrıca, daha zor kod yürütme ile ilgili nedeni zorlaştırabilir.</span><span class="sxs-lookup"><span data-stu-id="8921d-191">Additionally, the nesting of asynchronous code like this can also make it more difficult to reason about the execution of the code.</span></span> <span data-ttu-id="8921d-192">Zaman uyumsuz ve LINQ güçlü ancak dikkatli bir şekilde ve mümkün olduğunca NET bir şekilde birlikte kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="8921d-192">Async and LINQ are powerful, but should be used together as carefully and clearly as possible.</span></span>

* <span data-ttu-id="8921d-193">**Görevleri bekler engelleyici olmayan bir şekilde kod yazın**</span><span class="sxs-lookup"><span data-stu-id="8921d-193">**Write code that awaits Tasks in a non-blocking manner**</span></span>

<span data-ttu-id="8921d-194">Geçerli iş parçacığı engelleme beklenecek bir yol bir görevin tamamlanmasını Kilitlenmeler ve bağlam engellenen iş parçacıkları neden olabilir ve önemli ölçüde daha karmaşık hata işleme gerektirebilir.</span><span class="sxs-lookup"><span data-stu-id="8921d-194">Blocking the current thread as a means to wait for a Task to complete can result in deadlocks and blocked context threads, and can require significantly more complex error-handling.</span></span> <span data-ttu-id="8921d-195">Aşağıdaki tabloda engelleyici olmayan bir yolla görevlerde bekleyen ile uğraşmak konusunda rehberlik sağlar:</span><span class="sxs-lookup"><span data-stu-id="8921d-195">The following table provides guidance on how to deal with waiting for Tasks in a non-blocking way:</span></span>

| <span data-ttu-id="8921d-196">Bunu kullanın...</span><span class="sxs-lookup"><span data-stu-id="8921d-196">Use this...</span></span> | <span data-ttu-id="8921d-197">Bunun yerine...</span><span class="sxs-lookup"><span data-stu-id="8921d-197">Instead of this...</span></span> | <span data-ttu-id="8921d-198">Bunu yapmak isteyen olduğunda</span><span class="sxs-lookup"><span data-stu-id="8921d-198">When wishing to do this</span></span> |
| --- | --- | --- |
| `await` | <span data-ttu-id="8921d-199">`Task.Wait` veya `Task.Result`</span><span class="sxs-lookup"><span data-stu-id="8921d-199">`Task.Wait` or `Task.Result`</span></span> | <span data-ttu-id="8921d-200">Arka plan görevinin sonucunu alınıyor</span><span class="sxs-lookup"><span data-stu-id="8921d-200">Retrieving the result of a background task</span></span> |
| `await Task.WhenAny` | `Task.WaitAny` | <span data-ttu-id="8921d-201">Bir görevi tamamlamak bekleniyor</span><span class="sxs-lookup"><span data-stu-id="8921d-201">Waiting for any task to complete</span></span> |
| `await Task.WhenAll` | `Task.WaitAll` | <span data-ttu-id="8921d-202">Tüm görevlerin tamamlanması bekleniyor</span><span class="sxs-lookup"><span data-stu-id="8921d-202">Waiting for all tasks to complete</span></span> |
| `await Task.Delay` | `Thread.Sleep` | <span data-ttu-id="8921d-203">Bir süre için bekleniyor</span><span class="sxs-lookup"><span data-stu-id="8921d-203">Waiting for a period of time</span></span> |

* <span data-ttu-id="8921d-204">**Durum bilgisi olan küçük kod yazma**</span><span class="sxs-lookup"><span data-stu-id="8921d-204">**Write less stateful code**</span></span>

<span data-ttu-id="8921d-205">Genel nesnelerin veya belirli yöntemleri yürütme durumunu bağlı değilsiniz.</span><span class="sxs-lookup"><span data-stu-id="8921d-205">Don’t depend on the state of global objects or the execution of certain methods.</span></span> <span data-ttu-id="8921d-206">Bunun yerine, yalnızca yöntemlerinin dönüş değerlerine bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="8921d-206">Instead, depend only on the return values of methods.</span></span> <span data-ttu-id="8921d-207">Neden?</span><span class="sxs-lookup"><span data-stu-id="8921d-207">Why?</span></span>

  * <span data-ttu-id="8921d-208">Kod nedeni hakkında daha kolay olacaktır.</span><span class="sxs-lookup"><span data-stu-id="8921d-208">Code will be easier to reason about.</span></span>
  * <span data-ttu-id="8921d-209">Kodu test etmek daha kolay olacaktır.</span><span class="sxs-lookup"><span data-stu-id="8921d-209">Code will be easier to test.</span></span>
  * <span data-ttu-id="8921d-210">Zaman uyumsuz ve eş zamanlı kod karıştırma kadar basittir.</span><span class="sxs-lookup"><span data-stu-id="8921d-210">Mixing async and synchronous code is far simpler.</span></span>
  * <span data-ttu-id="8921d-211">Yarış durumları genellikle tamamen önlenebilir.</span><span class="sxs-lookup"><span data-stu-id="8921d-211">Race conditions can typically be avoided altogether.</span></span>
  * <span data-ttu-id="8921d-212">Dönüş değerlerine bağlı olarak, denetleyici zaman uyumsuz kodu basitleştirir.</span><span class="sxs-lookup"><span data-stu-id="8921d-212">Depending on return values makes coordinating async code simple.</span></span>
  * <span data-ttu-id="8921d-213">(Ekstra) gerçekten de bağımlılık ekleme ile çalışır.</span><span class="sxs-lookup"><span data-stu-id="8921d-213">(Bonus) it works really well with dependency injection.</span></span>

<span data-ttu-id="8921d-214">Önerilen bir hedef tam veya neredeyse eksiksiz elde etmektir [başvuru saydamlık](https://en.wikipedia.org/wiki/Referential_transparency_%28computer_science%29) kodunuzda.</span><span class="sxs-lookup"><span data-stu-id="8921d-214">A recommended goal is to achieve complete or near-complete [Referential Transparency](https://en.wikipedia.org/wiki/Referential_transparency_%28computer_science%29) in your code.</span></span> <span data-ttu-id="8921d-215">Bunun yapılması, son derece tahmin edilebilir, sınanabilir ve sürdürülebilir bir kod temeli neden olur.</span><span class="sxs-lookup"><span data-stu-id="8921d-215">Doing so will result in an extremely predictable, testable, and maintainable codebase.</span></span>

## <a name="other-resources"></a><span data-ttu-id="8921d-216">Diğer Kaynaklar</span><span class="sxs-lookup"><span data-stu-id="8921d-216">Other Resources</span></span>

* <span data-ttu-id="8921d-217">[Zaman uyumsuz ayrıntılı](../standard/async-in-depth.md) görevleri nasıl çalıştığı hakkında daha fazla bilgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="8921d-217">[Async in-depth](../standard/async-in-depth.md) provides more information about how Tasks work.</span></span>
* [<span data-ttu-id="8921d-218">Zaman uyumsuz programlama ile async ve await (C#)</span><span class="sxs-lookup"><span data-stu-id="8921d-218">Asynchronous programming with async and await (C#)</span></span>](./programming-guide/concepts/async/index.md)
* <span data-ttu-id="8921d-219">Lucian Wischik'ın [zaman uyumsuz altı önemli ipuçları](https://channel9.msdn.com/Series/Three-Essential-Tips-for-Async) zaman uyumsuz programlama için harika bir kaynaktır</span><span class="sxs-lookup"><span data-stu-id="8921d-219">Lucian Wischik's [Six Essential Tips for Async](https://channel9.msdn.com/Series/Three-Essential-Tips-for-Async) are a wonderful resource for async programming</span></span>