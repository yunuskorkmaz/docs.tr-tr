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
ms.locfileid: "34312072"
---
# <a name="asynchronous-programming"></a><span data-ttu-id="4ab98-103">Zaman uyumsuz programlama</span><span class="sxs-lookup"><span data-stu-id="4ab98-103">Asynchronous programming</span></span>

<span data-ttu-id="4ab98-104">Tüm g/Ç-bağlı gereksinimlerini (örneğin, ağ üzerinden veri isteme veya bir veritabanına erişirken) varsa, zaman uyumsuz programlama kullanmak istersiniz.</span><span class="sxs-lookup"><span data-stu-id="4ab98-104">If you have any I/O-bound needs (such as requesting data from a network or accessing a database), you'll want to utilize asynchronous programming.</span></span>  <span data-ttu-id="4ab98-105">Zaman uyumsuz kod yazma için iyi bir senaryo aynı zamanda olan pahalı bir hesaplama gerçekleştirme gibi CPU bağımlı kod de olabilir.</span><span class="sxs-lookup"><span data-stu-id="4ab98-105">You could also have CPU-bound code, such as performing an expensive calculation, which is also a good scenario for writing async code.</span></span>

<span data-ttu-id="4ab98-106">C# kolayca geri çağırmaları juggle veya asynchrony destekleyen bir kitaplık uymak zorunda kalmadan zaman uyumsuz kod yazmak için izin veren bir dil düzeyi zaman uyumsuz programlama modeli vardır.</span><span class="sxs-lookup"><span data-stu-id="4ab98-106">C# has a language-level asynchronous programming model which allows for easily writing asynchronous code without having to juggle callbacks or conform to a library which supports asynchrony.</span></span> <span data-ttu-id="4ab98-107">Olarak bilinen izleyen [görev tabanlı zaman uyumsuz desen (TAP)](https://msdn.microsoft.com/library/hh873175.aspx).</span><span class="sxs-lookup"><span data-stu-id="4ab98-107">It follows what is known as the [Task-based Asynchronous Pattern (TAP)](https://msdn.microsoft.com/library/hh873175.aspx).</span></span>

## <a name="basic-overview-of-the-asynchronous-model"></a><span data-ttu-id="4ab98-108">Zaman uyumsuz modeline temel genel bakış</span><span class="sxs-lookup"><span data-stu-id="4ab98-108">Basic Overview of the Asynchronous Model</span></span>

<span data-ttu-id="4ab98-109">Zaman uyumsuz programlama çekirdek olan `Task` ve `Task<T>` zaman uyumsuz işlemleri model nesneleri.</span><span class="sxs-lookup"><span data-stu-id="4ab98-109">The core of async programming are the `Task` and `Task<T>` objects, which model asynchronous operations.</span></span>  <span data-ttu-id="4ab98-110">Tarafından desteklenen `async` ve `await` anahtar sözcükler.</span><span class="sxs-lookup"><span data-stu-id="4ab98-110">They are supported by the `async` and `await` keywords.</span></span>  <span data-ttu-id="4ab98-111">Model, çoğu durumda oldukça basittir:</span><span class="sxs-lookup"><span data-stu-id="4ab98-111">The model is fairly simple in most cases:</span></span> 

<span data-ttu-id="4ab98-112">G/Ç-bağlı kodu için `await` döndüren bir işlem bir `Task` veya `Task<T>` içine bir `async` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="4ab98-112">For I/O-bound code, you `await` an operation which returns a `Task` or `Task<T>` inside of an `async` method.</span></span>

<span data-ttu-id="4ab98-113">CPU bağımlı kodu için `await` arka plan iş parçacığı ile başlatılan bir işlem `Task.Run` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="4ab98-113">For CPU-bound code, you `await` an operation which is started on a background thread with the `Task.Run` method.</span></span>

<span data-ttu-id="4ab98-114">`await` Sözcüktür burada Sihirli olur.</span><span class="sxs-lookup"><span data-stu-id="4ab98-114">The `await` keyword is where the magic happens.</span></span> <span data-ttu-id="4ab98-115">Gerçekleştirilen yöntemi çağırana denetim verir `await`, ve sonuçta bir kullanıcı Arabirimi yanıt vermesi veya esnek olması için bir hizmet sağlar.</span><span class="sxs-lookup"><span data-stu-id="4ab98-115">It yields control to the caller of the method that performed `await`, and it ultimately allows a UI to be responsive or a service to be elastic.</span></span>

<span data-ttu-id="4ab98-116">Diğer yolla yaklaşım zaman uyumsuz koduna `async` ve `await` yukarıdaki bağlı DOKUNUN makalesinde özetlenen, ancak bu belgede bu noktadan dil düzeyi yapıları üzerine odaklanacaktır.</span><span class="sxs-lookup"><span data-stu-id="4ab98-116">There are other ways to approach async code than `async` and `await` outlined in the TAP article linked above, but this document will focus on the language-level constructs from this point forward.</span></span>

### <a name="io-bound-example-downloading-data-from-a-web-service"></a><span data-ttu-id="4ab98-117">G/Ç-bağlı örnek: bir web hizmetinden veri indirme</span><span class="sxs-lookup"><span data-stu-id="4ab98-117">I/O-Bound Example: Downloading data from a web service</span></span>

<span data-ttu-id="4ab98-118">Bir düğmeye basıldığında bazı verileri bir web hizmetinden yüklemeniz gerekebilir, ancak kullanıcı Arabirimi iş parçacığı engellemek istediğiniz yok.</span><span class="sxs-lookup"><span data-stu-id="4ab98-118">You may need to download some data from a web service when a button is pressed, but don’t want to block the UI thread.</span></span> <span data-ttu-id="4ab98-119">Yalnızca bu gibi gerçekleştirilebilir:</span><span class="sxs-lookup"><span data-stu-id="4ab98-119">It can be accomplished simply like this:</span></span>

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

<span data-ttu-id="4ab98-120">Ve bu kadar!</span><span class="sxs-lookup"><span data-stu-id="4ab98-120">And that’s it!</span></span> <span data-ttu-id="4ab98-121">Kod görev nesnelerle etkileşim çıkmaza olmadan (bazı verileri zaman uyumsuz olarak indirme) hedefi ifade eder.</span><span class="sxs-lookup"><span data-stu-id="4ab98-121">The code expresses the intent (downloading some data asynchronously) without getting bogged down in interacting with Task objects.</span></span>

### <a name="cpu-bound-example-performing-a-calculation-for-a-game"></a><span data-ttu-id="4ab98-122">CPU bağımlı örnek: bir oyun için bir hesaplama gerçekleştirme</span><span class="sxs-lookup"><span data-stu-id="4ab98-122">CPU-bound Example: Performing a Calculation for a Game</span></span>

<span data-ttu-id="4ab98-123">Burada bir düğmesine basarak hasar ekranında birçok enemies üzerinde verebilecek mobil oyun yazıyorsanız söyleyin.</span><span class="sxs-lookup"><span data-stu-id="4ab98-123">Say you're writing a mobile game where pressing a button can inflict damage on many enemies on the screen.</span></span>  <span data-ttu-id="4ab98-124">Hasar hesaplama gerçekleştirme pahalı olabilir ve kullanıcı Arabirimi iş parçacığı üzerinde yapmakta hesaplama gerçekleştirilir gibi duraklatmak için görünür oyun yapacağı!</span><span class="sxs-lookup"><span data-stu-id="4ab98-124">Performing the damage calculation can be expensive, and doing it on the UI thread would make the game appear to pause as the calculation is performed!</span></span>

<span data-ttu-id="4ab98-125">Bu durumu çözmek için en iyi yolu kullanarak iş yapan bir arka plan iş parçacığı başlatmaktır `Task.Run`, ve `await` sonucu.</span><span class="sxs-lookup"><span data-stu-id="4ab98-125">The best way to handle this is to start a background thread which does the work using `Task.Run`, and `await` its result.</span></span>  <span data-ttu-id="4ab98-126">Bu iş gerçekleştirilir gibi kesintisiz eşitleyerek için kullanıcı Arabirimi sağlar.</span><span class="sxs-lookup"><span data-stu-id="4ab98-126">This will allow the UI to feel smooth as the work is being done.</span></span>

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

<span data-ttu-id="4ab98-127">Ve bu kadar!</span><span class="sxs-lookup"><span data-stu-id="4ab98-127">And that's it!</span></span>  <span data-ttu-id="4ab98-128">Bu kod düzgün bir şekilde amacı ifade düğmenin olay'ı tıklatın, bir arka plan iş parçacığı el ile yönetme gerektirmez ve bunu engelleyici olmayan bir biçimde yapar.</span><span class="sxs-lookup"><span data-stu-id="4ab98-128">This code cleanly expresses the intent of the button's click event, it doesn't require managing a background thread manually, and it does so in a non-blocking way.</span></span>

### <a name="what-happens-under-the-covers"></a><span data-ttu-id="4ab98-129">Perde arkasında ne olur?</span><span class="sxs-lookup"><span data-stu-id="4ab98-129">What happens under the covers</span></span>

<span data-ttu-id="4ab98-130">Zaman uyumsuz işlemleri burada ilgilenir taşıma parçaları çok yoktur.</span><span class="sxs-lookup"><span data-stu-id="4ab98-130">There's a lot of moving pieces where asynchronous operations are concerned.</span></span>  <span data-ttu-id="4ab98-131">İç in gerçekleştiği hakkında merak `Task` ve `Task<T>`, checkout [zaman uyumsuz ayrıntılı](../standard/async-in-depth.md) daha fazla bilgi için makalenin.</span><span class="sxs-lookup"><span data-stu-id="4ab98-131">If you're curious about what's happening underneath the covers of `Task` and `Task<T>`, checkout the [Async in-depth](../standard/async-in-depth.md) article for more information.</span></span>

<span data-ttu-id="4ab98-132">C# tarafında nesnelerin interneti derleyici kodunuzu yürütme sağlayan gibi şeyler ve bir durum makinesinin dönüştüren olduğunda bir `await` arka plan işi sona erdiğinde ulaştı ve devam ettirme yürütme ediyor.</span><span class="sxs-lookup"><span data-stu-id="4ab98-132">On the C# side of things, the compiler transforms your code into a state machine which keeps track of things like yielding execution when an `await` is reached and resuming execution when a background job has finished.</span></span>

<span data-ttu-id="4ab98-133">Teorik olarak-inclined için bu bir uygulamasıdır [asynchrony Promise modelinin](https://en.wikipedia.org/wiki/Futures_and_promises).</span><span class="sxs-lookup"><span data-stu-id="4ab98-133">For the theoretically-inclined, this is an implementation of the [Promise Model of asynchrony](https://en.wikipedia.org/wiki/Futures_and_promises).</span></span>

## <a name="key-pieces-to-understand"></a><span data-ttu-id="4ab98-134">Anlamak için temel parçalar</span><span class="sxs-lookup"><span data-stu-id="4ab98-134">Key Pieces to Understand</span></span>

*   <span data-ttu-id="4ab98-135">Zaman uyumsuz kodu için kod g/Ç-bağlı ve CPU bağımlı, ancak farklı her senaryo için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="4ab98-135">Async code can be used for both I/O-bound and CPU-bound code, but differently for each scenario.</span></span>
*   <span data-ttu-id="4ab98-136">Zaman uyumsuz kodu kullanan `Task<T>` ve `Task`, arka planda gerçekleştirilen modeli çalışmak için kullanılan yapılar olduğu.</span><span class="sxs-lookup"><span data-stu-id="4ab98-136">Async code uses `Task<T>` and `Task`, which are constructs used to model work being done in the background.</span></span>
* <span data-ttu-id="4ab98-137">`async` Anahtar sözcüğü bir yöntem kullanmanıza olanak sağlayan bir zaman uyumsuz yöntem kapatır `await` kendi gövdesindeki anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="4ab98-137">The `async` keyword turns a method into an async method, which allows you to use the `await` keyword in its body.</span></span>
*   <span data-ttu-id="4ab98-138">Zaman `await` anahtar sözcüğü uygulandığında, çağrıyı yapan yöntemini askıya alır ve awaited görevi tamamlanana kadar geri çağırıcısına denetim verir.</span><span class="sxs-lookup"><span data-stu-id="4ab98-138">When the `await` keyword is applied, it suspends the calling method and yields control back to its caller until the awaited task is complete.</span></span>
*   <span data-ttu-id="4ab98-139">`await` yalnızca bir zaman uyumsuz yöntem içinde kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="4ab98-139">`await` can only be used inside an async method.</span></span>

## <a name="recognize-cpu-bound-and-io-bound-work"></a><span data-ttu-id="4ab98-140">CPU bağımlı ve g/Ç-bağlı iş tanı</span><span class="sxs-lookup"><span data-stu-id="4ab98-140">Recognize CPU-Bound and I/O-Bound Work</span></span>

<span data-ttu-id="4ab98-141">Bu kılavuzun ilk iki örnek gösterdi nasıl kullanacağınızı `async` ve `await` g/Ç-bağlı ve CPU bağımlı iş için.</span><span class="sxs-lookup"><span data-stu-id="4ab98-141">The first two examples of this guide showed how you can use `async` and `await` for I/O-bound and CPU-bound work.</span></span>  <span data-ttu-id="4ab98-142">Bir işi yapmak gereksinim duyduğunuzda, tanımlayabilirsiniz, g/Ç-bağlı veya CPU bağımlı anahtarıdır, kodunuzu performansını önemli ölçüde etkileyebilir ve büyük olasılıkla olabilir çünkü kötüye adayı belirli oluşturur.</span><span class="sxs-lookup"><span data-stu-id="4ab98-142">It's key that you can identify when a job you need to do is I/O-bound or CPU-bound, because it can greatly affect the performance of your code and could potentially lead to misusing certain constructs.</span></span>

<span data-ttu-id="4ab98-143">Herhangi bir kod yazmadan önce istemelisiniz iki sorular şunlardır:</span><span class="sxs-lookup"><span data-stu-id="4ab98-143">Here are two questions you should ask before you write any code:</span></span>

1. <span data-ttu-id="4ab98-144">Kodunuzu "bir veritabanındaki verileri gibi şeyler bekliyor olabilir"?</span><span class="sxs-lookup"><span data-stu-id="4ab98-144">Will your code be "waiting" for something, such as data from a database?</span></span>

    <span data-ttu-id="4ab98-145">"Evet" aradığınız cevaptır sonra iş **g/Ç-bağlı**.</span><span class="sxs-lookup"><span data-stu-id="4ab98-145">If your answer is "yes", then your work is **I/O-bound**.</span></span>

2. <span data-ttu-id="4ab98-146">Kodunuzu çok pahalı bir hesaplama gerçekleştirecekseniz?</span><span class="sxs-lookup"><span data-stu-id="4ab98-146">Will your code be performing a very expensive computation?</span></span>

    <span data-ttu-id="4ab98-147">"Evet" yanıtlanan sonra iş **CPU bağımlı**.</span><span class="sxs-lookup"><span data-stu-id="4ab98-147">If you answered "yes", then your work is **CPU-bound**.</span></span>
    
<span data-ttu-id="4ab98-148">Sahip olduğunuz iş ise **g/Ç-bağlı**, kullanın `async` ve `await` *olmadan* `Task.Run`.</span><span class="sxs-lookup"><span data-stu-id="4ab98-148">If the work you have is **I/O-bound**, use `async` and `await` *without* `Task.Run`.</span></span>  <span data-ttu-id="4ab98-149">*Vermemelisiniz* görev paralel kitaplığı kullanın.</span><span class="sxs-lookup"><span data-stu-id="4ab98-149">You *should not* use the Task Parallel Library.</span></span>  <span data-ttu-id="4ab98-150">Bunun nedeni kısmında özetlenen [zaman uyumsuz derinliği makalede](../standard/async-in-depth.md).</span><span class="sxs-lookup"><span data-stu-id="4ab98-150">The reason for this is outlined in the [Async in Depth article](../standard/async-in-depth.md).</span></span>

<span data-ttu-id="4ab98-151">Sahip olduğunuz iş ise **CPU bağımlı** ve yanıtlama hakkında kullanım verdiğiniz `async` ve `await` ancak başka bir iş parçacığında İş dışı oluşturma *ile* `Task.Run`.</span><span class="sxs-lookup"><span data-stu-id="4ab98-151">If the work you have is **CPU-bound** and you care about responsiveness, use `async` and `await` but spawn the work off on another thread *with* `Task.Run`.</span></span>  <span data-ttu-id="4ab98-152">İş eşzamanlılığı ve paralellik için uygun değilse, görev paralel kitaplığı kullanmayı da düşünmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="4ab98-152">If the work is appropriate for concurrency and parallelism, you should also consider using the Task Parallel Library.</span></span>

<span data-ttu-id="4ab98-153">Ayrıca, her zaman kodunuzun yürütülmesini ölçmek.</span><span class="sxs-lookup"><span data-stu-id="4ab98-153">Additionally, you should always measure the execution of your code.</span></span>  <span data-ttu-id="4ab98-154">Örneğin, kendiniz CPU bağımlı iş olduğu pahalı bir durumda bulabilirsiniz İçerik Geçişi çoklu iş parçacığı kullanımı zaman yüküyle yeterince karşılaştırılan.</span><span class="sxs-lookup"><span data-stu-id="4ab98-154">For example, you may find yourself in a situation where your CPU-bound work is not costly enough compared with the overhead of context switches when multithreading.</span></span>  <span data-ttu-id="4ab98-155">Her seçenek kendi kolaylığını var ve durumunuz için doğru kolaylığını seçmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="4ab98-155">Every choice has its tradeoff, and you should pick the correct tradeoff for your situation.</span></span>

## <a name="more-examples"></a><span data-ttu-id="4ab98-156">Daha fazla örnek</span><span class="sxs-lookup"><span data-stu-id="4ab98-156">More Examples</span></span>

<span data-ttu-id="4ab98-157">Aşağıdaki örnekler, zaman uyumsuz kod C# dilinde yazabilirsiniz çeşitli yolları gösterir.</span><span class="sxs-lookup"><span data-stu-id="4ab98-157">The following examples demonstrate various ways you can write async code in C#.</span></span>  <span data-ttu-id="4ab98-158">Bunlar arasında gelebilir birkaç farklı senaryolar kapsar.</span><span class="sxs-lookup"><span data-stu-id="4ab98-158">They cover a few different scenarios you may come across.</span></span>

### <a name="extracting-data-from-a-network"></a><span data-ttu-id="4ab98-159">Ağ üzerinden veri çıkarma</span><span class="sxs-lookup"><span data-stu-id="4ab98-159">Extracting Data from a Network</span></span>

<span data-ttu-id="4ab98-160">Bu kod parçacığında www.dotnetfoundation.org HTML indirir ve HTML dizesi ".NET" oluşur kez sayar.</span><span class="sxs-lookup"><span data-stu-id="4ab98-160">This snippet downloads the HTML from www.dotnetfoundation.org and counts the number of times the string ".NET" occurs in the HTML.</span></span>  <span data-ttu-id="4ab98-161">ASP.NET MVC sayısı, bu görevi gerçekleştiren bir web denetleyicisi yöntemi tanımlamak için kullanır.</span><span class="sxs-lookup"><span data-stu-id="4ab98-161">It uses ASP.NET MVC to define a web controller method which performs this task, returning the number.</span></span>

> [!NOTE]
> <span data-ttu-id="4ab98-162">HTML üretim kodunda ayrıştırma yapmayı planlıyorsanız, normal ifadeler kullanmayın.</span><span class="sxs-lookup"><span data-stu-id="4ab98-162">If you plan on doing HTML parsing in production code, don't use regular expressions.</span></span> <span data-ttu-id="4ab98-163">Bunun yerine bir ayrıştırma kitaplığını kullanın.</span><span class="sxs-lookup"><span data-stu-id="4ab98-163">Use a parsing library instead.</span></span>

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

<span data-ttu-id="4ab98-164">Bir evrensel Windows bir düğmeye basıldığında aynı görevi gerçekleştiren uygulama için yazılmış aynı senaryo aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="4ab98-164">Here's the same scenario written for a Universal Windows App, which performs the same task when a Button is pressed:</span></span>

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

### <a name="waiting-for-multiple-tasks-to-complete"></a><span data-ttu-id="4ab98-165">Birden fazla görevin tamamlanmasını bekliyor</span><span class="sxs-lookup"><span data-stu-id="4ab98-165">Waiting for Multiple Tasks to Complete</span></span>

<span data-ttu-id="4ab98-166">Kendinizi eşzamanlı olarak birden çok veri parçalarını almanıza gerek olduğu bir durumda bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4ab98-166">You may find yourself in a situation where you need to retrieve multiple pieces of data concurrently.</span></span>  <span data-ttu-id="4ab98-167">`Task` API'yi içeren iki yöntem `Task.WhenAll` ve `Task.WhenAny` birden fazla arka plan işleri engelleyici olmayan bir bekleme gerçekleştiren zaman uyumsuz kod yazmayı izin.</span><span class="sxs-lookup"><span data-stu-id="4ab98-167">The `Task` API contains two methods, `Task.WhenAll` and `Task.WhenAny` which allow you to write asynchronous code which performs a non-blocking wait on multiple background jobs.</span></span>

<span data-ttu-id="4ab98-168">Bu örnek nasıl yakalayın gösterir `User` veri kümesi için `userId`s.</span><span class="sxs-lookup"><span data-stu-id="4ab98-168">This example shows how you might grab `User` data for a set of `userId`s.</span></span>

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

<span data-ttu-id="4ab98-169">LINQ kullanarak bu biraz daha temellerini yazmak için başka bir yolu şöyledir:</span><span class="sxs-lookup"><span data-stu-id="4ab98-169">Here's another way to write this a bit more succinctly, using LINQ:</span></span>

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
<span data-ttu-id="4ab98-170">Daha az kod olmasına rağmen zaman uyumsuz koduyla LINQ karıştırma zaman dikkatli olun.</span><span class="sxs-lookup"><span data-stu-id="4ab98-170">Although it's less code, take care when mixing LINQ with asynchronous code.</span></span>  <span data-ttu-id="4ab98-171">LINQ ertelenmiş (yavaş) yürütme kullandığından, zaman uyumsuz çağrıları göründükleri hemen gerçekleşmez bir `foreach()` çağrısıyla yinelemek için oluşturulan sıra zorlama sürece döngü `.ToList()` veya `.ToArray()`.</span><span class="sxs-lookup"><span data-stu-id="4ab98-171">Because LINQ uses deferred (lazy) execution, async calls won't happen immediately as they do in a `foreach()` loop unless you force the generated sequence to iterate with a call to `.ToList()` or `.ToArray()`.</span></span>

## <a name="important-info-and-advice"></a><span data-ttu-id="4ab98-172">Önemli bilgiler ve öneriler</span><span class="sxs-lookup"><span data-stu-id="4ab98-172">Important Info and Advice</span></span>

<span data-ttu-id="4ab98-173">Zaman uyumsuz programlama görece basit olsa da, bazı ayrıntılar beklenmeyen davranışları önleyebilir göz önünde bulundurmanız vardır.</span><span class="sxs-lookup"><span data-stu-id="4ab98-173">Although async programming is relatively straightforward, there are some details to keep in mind which can prevent unexpected behavior.</span></span>

*  <span data-ttu-id="4ab98-174">`async` **yöntemleri olması gerekir bir** `await` **kendi gövdesindeki anahtar sözcüğü veya hiçbir zaman sunacak!**</span><span class="sxs-lookup"><span data-stu-id="4ab98-174">`async` **methods need to have an** `await` **keyword in their body or they will never yield!**</span></span>

<span data-ttu-id="4ab98-175">Bu, göz önünde bulundurmanız önemlidir.</span><span class="sxs-lookup"><span data-stu-id="4ab98-175">This is important to keep in mind.</span></span>  <span data-ttu-id="4ab98-176">Varsa `await` gövdesinde kullanılmayan bir `async` yöntemi, bir uyarı üretir C# Derleyici olacaktır, ancak derleme ve normal bir yöntem değilmiş gibi çalıştırma kodu olacaktır.</span><span class="sxs-lookup"><span data-stu-id="4ab98-176">If `await` is not used in the body of an `async` method, the C# compiler will generate a warning, but the code will compile and run as if it were a normal method.</span></span>  <span data-ttu-id="4ab98-177">Async yöntemi için C# Derleyici tarafından oluşturulan Durum makinesi herhangi bir şey gerçekleştirmeye olabilir değil olarak bu de son derece verimli olacaktır.</span><span class="sxs-lookup"><span data-stu-id="4ab98-177">Note that this would also be incredibly inefficient, as the state machine generated by the C# compiler for the async method would not be accomplishing anything.</span></span>

*   <span data-ttu-id="4ab98-178">**Yazdığınız her zaman uyumsuz yöntem adı son eki olarak "Zaman uyumsuz" eklemeniz gerekir.**</span><span class="sxs-lookup"><span data-stu-id="4ab98-178">**You should add "Async" as the suffix of every async method name you write.**</span></span>

<span data-ttu-id="4ab98-179">Bu, .NET içinde daha kolayca zaman uyumlu ve zaman uyumsuz yöntemleri ayırdetmek için kullanılan kuraldır.</span><span class="sxs-lookup"><span data-stu-id="4ab98-179">This is the convention used in .NET to more-easily differentiate synchronous and asynchronous methods.</span></span> <span data-ttu-id="4ab98-180">Kodunuzu (örneğin, olay işleyicileri veya web denetleyicisi yöntemleri) tarafından açıkça çağrılan olmayan bazı yöntemleri mutlaka uygulanmaz unutmayın.</span><span class="sxs-lookup"><span data-stu-id="4ab98-180">Note that certain methods which aren’t explicitly called by your code (such as event handlers or web controller methods) don’t necessarily apply.</span></span> <span data-ttu-id="4ab98-181">Bunlar açıkça kodunuz tarafından adlandırılır değil çünkü bunların adlandırma hakkında açık olması önemli değildir.</span><span class="sxs-lookup"><span data-stu-id="4ab98-181">Because these are not explicitly called by your code, being explicit about their naming isn’t as important.</span></span>

*   <span data-ttu-id="4ab98-182">`async void` **yalnızca olay işleyicileri için kullanılmalıdır.**</span><span class="sxs-lookup"><span data-stu-id="4ab98-182">`async void` **should only be used for event handlers.**</span></span>

<span data-ttu-id="4ab98-183">`async void` olaylar, dönüş türleri olmadığı için çalışması zaman uyumsuz olay işleyicileri izin vermek için tek yolu (Bu nedenle yapılamıyor kullanımı `Task` ve `Task<T>`).</span><span class="sxs-lookup"><span data-stu-id="4ab98-183">`async void` is the only way to allow asynchronous event handlers to work because events do not have return types (thus cannot make use of `Task` and `Task<T>`).</span></span> <span data-ttu-id="4ab98-184">Diğer bir kullanımını `async void` DOKUNUN model izlemez ve gibi kullanmak için zor olabilir:</span><span class="sxs-lookup"><span data-stu-id="4ab98-184">Any other use of `async void` does not follow the TAP model and can be challenging to use, such as:</span></span>

  *   <span data-ttu-id="4ab98-185">Oluşturulan özel durumları bir `async void` yöntemi bu yöntemi dışında yakalanan olamaz.</span><span class="sxs-lookup"><span data-stu-id="4ab98-185">Exceptions thrown in an `async void` method can’t be caught outside of that method.</span></span>
  *   <span data-ttu-id="4ab98-186">`async void` test etmek oldukça zor yöntemleridir.</span><span class="sxs-lookup"><span data-stu-id="4ab98-186">`async void` methods are very difficult to test.</span></span>
  *   <span data-ttu-id="4ab98-187">`async void` Arayan bunları zaman uyumsuz olarak bekleniyor değil, yöntemleri hatalı yan etkileri neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="4ab98-187">`async void` methods can cause bad side effects if the caller isn’t expecting them to be async.</span></span>

*   <span data-ttu-id="4ab98-188">**Zaman uyumsuz Lambda'lar LINQ ifadelerinde kullanırken dikkatle tread**</span><span class="sxs-lookup"><span data-stu-id="4ab98-188">**Tread carefully when using async lambdas in LINQ expressions**</span></span>

<span data-ttu-id="4ab98-189">Ertelenmiş yürütme LINQ lambda ifadeleri kullanma, anlamı kod zaman kendisine beklediğiniz olmayan bir anda yürütülmekte end.</span><span class="sxs-lookup"><span data-stu-id="4ab98-189">Lambda expressions in LINQ use deferred execution, meaning code could end up executing at a time when you’re not expecting it to.</span></span> <span data-ttu-id="4ab98-190">Bu görevleri engelleme giriş kolayca bir kilitlenmeyle doğru yazılmaz neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="4ab98-190">The introduction of blocking tasks into this can easily result in a deadlock if not written correctly.</span></span> <span data-ttu-id="4ab98-191">Ayrıca, zaman uyumsuz kod bu gibi iç içe ayrıca daha kodunun yürütülmesini hakkında nedeni zorlaştırabilir.</span><span class="sxs-lookup"><span data-stu-id="4ab98-191">Additionally, the nesting of asynchronous code like this can also make it more difficult to reason about the execution of the code.</span></span> <span data-ttu-id="4ab98-192">Zaman uyumsuz ve LINQ güçlüdür ancak dikkatle ve mümkün olduğunca açıkça olarak birlikte kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="4ab98-192">Async and LINQ are powerful, but should be used together as carefully and clearly as possible.</span></span>

*   <span data-ttu-id="4ab98-193">**Engelleyici olmayan bir biçimde görevleri bekler kod yazma**</span><span class="sxs-lookup"><span data-stu-id="4ab98-193">**Write code that awaits Tasks in a non-blocking manner**</span></span>

<span data-ttu-id="4ab98-194">Geçerli iş parçacığının beklemek için bir yol engelleme tamamlamak bir görev için Kilitlenmeler ve engellenen bağlam iş parçacığı neden olabilir ve önemli ölçüde daha karmaşık hata işleme gerektirebilir.</span><span class="sxs-lookup"><span data-stu-id="4ab98-194">Blocking the current thread as a means to wait for a Task to complete can result in deadlocks and blocked context threads, and can require significantly more complex error-handling.</span></span> <span data-ttu-id="4ab98-195">Aşağıdaki tabloda engelleyici olmayan bir biçimde görevler için bekleyen ile ilgilidir hakkında yönergeler sağlar:</span><span class="sxs-lookup"><span data-stu-id="4ab98-195">The following table provides guidance on how to deal with waiting for Tasks in a non-blocking way:</span></span>

| <span data-ttu-id="4ab98-196">Bu kullan...</span><span class="sxs-lookup"><span data-stu-id="4ab98-196">Use this...</span></span> | <span data-ttu-id="4ab98-197">Bunun yerine...</span><span class="sxs-lookup"><span data-stu-id="4ab98-197">Instead of this...</span></span> | <span data-ttu-id="4ab98-198">Bunu yapmak isteyen olduğunda</span><span class="sxs-lookup"><span data-stu-id="4ab98-198">When wishing to do this</span></span> |
| --- | --- | --- |
| `await` | <span data-ttu-id="4ab98-199">`Task.Wait` Veya `Task.Result`</span><span class="sxs-lookup"><span data-stu-id="4ab98-199">`Task.Wait` or `Task.Result`</span></span> | <span data-ttu-id="4ab98-200">Bir arka plan görevi sonucunu alınıyor</span><span class="sxs-lookup"><span data-stu-id="4ab98-200">Retrieving the result of a background task</span></span> |
| `await Task.WhenAny` | `Task.WaitAny` | <span data-ttu-id="4ab98-201">Tamamlamak herhangi bir görev için bekleniyor</span><span class="sxs-lookup"><span data-stu-id="4ab98-201">Waiting for any task to complete</span></span> |
| `await Task.WhenAll` | `Task.WaitAll` | <span data-ttu-id="4ab98-202">Tüm görevlerin tamamlanması bekleniyor</span><span class="sxs-lookup"><span data-stu-id="4ab98-202">Waiting for all tasks to complete</span></span> |
| `await Task.Delay` | `Thread.Sleep` | <span data-ttu-id="4ab98-203">Bir süre için bekleniyor</span><span class="sxs-lookup"><span data-stu-id="4ab98-203">Waiting for a period of time</span></span> |

*   <span data-ttu-id="4ab98-204">**Durum bilgisi olan daha az kod yazma**</span><span class="sxs-lookup"><span data-stu-id="4ab98-204">**Write less stateful code**</span></span>

<span data-ttu-id="4ab98-205">Genel nesne veya belirli yöntemlerini yürütülmesi durumuna bağlı yok.</span><span class="sxs-lookup"><span data-stu-id="4ab98-205">Don’t depend on the state of global objects or the execution of certain methods.</span></span> <span data-ttu-id="4ab98-206">Bunun yerine, yalnızca yöntemleri dönüş değerlerine bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="4ab98-206">Instead, depend only on the return values of methods.</span></span> <span data-ttu-id="4ab98-207">Neden?</span><span class="sxs-lookup"><span data-stu-id="4ab98-207">Why?</span></span>

  *   <span data-ttu-id="4ab98-208">Kod nedeni hakkında daha kolay olacaktır.</span><span class="sxs-lookup"><span data-stu-id="4ab98-208">Code will be easier to reason about.</span></span>
  *   <span data-ttu-id="4ab98-209">Kodu test etmek daha kolay olacaktır.</span><span class="sxs-lookup"><span data-stu-id="4ab98-209">Code will be easier to test.</span></span>
  *   <span data-ttu-id="4ab98-210">Zaman uyumsuz ve zaman uyumlu bir kod karıştırma kadar basittir.</span><span class="sxs-lookup"><span data-stu-id="4ab98-210">Mixing async and synchronous code is far simpler.</span></span>
  *   <span data-ttu-id="4ab98-211">Yarış durumları genellikle tamamen önlenebilir.</span><span class="sxs-lookup"><span data-stu-id="4ab98-211">Race conditions can typically be avoided altogether.</span></span>
  *   <span data-ttu-id="4ab98-212">Dönüş değerleri bağlı olarak, denetleyici zaman uyumsuz kod basit hale getirir.</span><span class="sxs-lookup"><span data-stu-id="4ab98-212">Depending on return values makes coordinating async code simple.</span></span>
  *   <span data-ttu-id="4ab98-213">(Prim) gerçekten de bağımlılık ekleme ile çalışır.</span><span class="sxs-lookup"><span data-stu-id="4ab98-213">(Bonus) it works really well with dependency injection.</span></span>

<span data-ttu-id="4ab98-214">Tam ya da yakın tamamlamak elde etmek için önerilen bir hedefi olan [başvuru saydamlık](https://en.wikipedia.org/wiki/Referential_transparency_%28computer_science%29) kodunuzda.</span><span class="sxs-lookup"><span data-stu-id="4ab98-214">A recommended goal is to achieve complete or near-complete [Referential Transparency](https://en.wikipedia.org/wiki/Referential_transparency_%28computer_science%29) in your code.</span></span> <span data-ttu-id="4ab98-215">Bunun yapılması bir son derece tahmin edilebilir, sınanabilir ve sürdürülebilir codebase neden olur.</span><span class="sxs-lookup"><span data-stu-id="4ab98-215">Doing so will result in an extremely predictable, testable, and maintainable codebase.</span></span>

## <a name="other-resources"></a><span data-ttu-id="4ab98-216">Diğer Kaynaklar</span><span class="sxs-lookup"><span data-stu-id="4ab98-216">Other Resources</span></span>

* <span data-ttu-id="4ab98-217">[Zaman uyumsuz ayrıntılı](../standard/async-in-depth.md) görevlerin nasıl çalıştığı hakkında daha fazla bilgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="4ab98-217">[Async in-depth](../standard/async-in-depth.md) provides more information about how Tasks work.</span></span>
* [<span data-ttu-id="4ab98-218">Zaman uyumsuz programlama ile async ve await (C#)</span><span class="sxs-lookup"><span data-stu-id="4ab98-218">Asynchronous programming with async and await (C#)</span></span>](../csharp/programming-guide/concepts/async/index.md)
* <span data-ttu-id="4ab98-219">Lucian Wischik'ın [zaman uyumsuz altı önemli ipuçları](https://channel9.msdn.com/Series/Three-Essential-Tips-for-Async) zaman uyumsuz programlama için harika bir kaynaktır</span><span class="sxs-lookup"><span data-stu-id="4ab98-219">Lucian Wischik's [Six Essential Tips for Async](https://channel9.msdn.com/Series/Three-Essential-Tips-for-Async) are a wonderful resource for async programming</span></span>
