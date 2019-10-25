---
title: Güncelleştirilmiş .NET Core olay deseninin
description: .NET Core olay deseninin geriye dönük uyumlulukla esnekliği nasıl sağladığını ve zaman uyumsuz aboneler ile güvenli olay işlemenin nasıl uygulanacağını öğrenin.
ms.date: 06/20/2016
ms.assetid: 9aa627c3-3222-4094-9ca8-7e88e1071e06
ms.openlocfilehash: 85fa4fd111a9eab01c1d32949d9fcc5f6300e33c
ms.sourcegitcommit: 9bd1c09128e012b6e34bdcbdf3576379f58f3137
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2019
ms.locfileid: "72798886"
---
# <a name="the-updated-net-core-event-pattern"></a><span data-ttu-id="d59fe-103">Güncelleştirilmiş .NET Core olay deseninin</span><span class="sxs-lookup"><span data-stu-id="d59fe-103">The Updated .NET Core Event Pattern</span></span>

[<span data-ttu-id="d59fe-104">Öncekini</span><span class="sxs-lookup"><span data-stu-id="d59fe-104">Previous</span></span>](event-pattern.md)

<span data-ttu-id="d59fe-105">Önceki makalede en sık kullanılan olay desenleri ele alınmıştır.</span><span class="sxs-lookup"><span data-stu-id="d59fe-105">The previous article discussed the most common event patterns.</span></span> <span data-ttu-id="d59fe-106">.NET Core daha gevşek bir düzene sahiptir.</span><span class="sxs-lookup"><span data-stu-id="d59fe-106">.NET Core has a more relaxed pattern.</span></span> <span data-ttu-id="d59fe-107">Bu sürümde `EventHandler<TEventArgs>` tanımı artık `TEventArgs` `System.EventArgs`türetilmiş bir sınıf olması gereken kısıtlamaya sahip değildir.</span><span class="sxs-lookup"><span data-stu-id="d59fe-107">In this version, the `EventHandler<TEventArgs>` definition no longer has the constraint that `TEventArgs` must be a class derived from `System.EventArgs`.</span></span>

<span data-ttu-id="d59fe-108">Bu, sizin için esnekliği artırır ve geriye dönük olarak uyumludur.</span><span class="sxs-lookup"><span data-stu-id="d59fe-108">This increases flexibility for you, and is backwards compatible.</span></span> <span data-ttu-id="d59fe-109">Esneklik ile başlayalım.</span><span class="sxs-lookup"><span data-stu-id="d59fe-109">Let's start with the flexibility.</span></span> <span data-ttu-id="d59fe-110">System. EventArgs sınıfı bir yöntemi tanıtır: nesnenin basit bir kopyasını oluşturan `MemberwiseClone()`.</span><span class="sxs-lookup"><span data-stu-id="d59fe-110">The class System.EventArgs introduces one method: `MemberwiseClone()`, which creates a shallow copy of the object.</span></span>
<span data-ttu-id="d59fe-111">Bu yöntemin, `EventArgs`türetilmiş herhangi bir sınıf için işlevselliğini uygulamak üzere yansıma kullanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="d59fe-111">That method must use reflection in order to implement its functionality for any class derived from `EventArgs`.</span></span> <span data-ttu-id="d59fe-112">Bu işlevsellik, belirli bir türetilmiş sınıfta oluşturmak daha kolaydır.</span><span class="sxs-lookup"><span data-stu-id="d59fe-112">That functionality is easier to create in a specific derived class.</span></span> <span data-ttu-id="d59fe-113">Bu, System. EventArgs 'dan Türetmenin tasarımlarınızı sınırlayan bir kısıtlamadır, ancak başka bir avantaj sunmaz.</span><span class="sxs-lookup"><span data-stu-id="d59fe-113">That effectively means that deriving from System.EventArgs is a constraint that limits your designs, but does not provide any additional benefit.</span></span>
<span data-ttu-id="d59fe-114">Aslında, `EventArgs`türetmemesi için `FileFoundArgs` ve `SearchDirectoryArgs` tanımlarını değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d59fe-114">In fact, you can change the definitions of `FileFoundArgs` and `SearchDirectoryArgs` so that they do not derive from `EventArgs`.</span></span>
<span data-ttu-id="d59fe-115">Program tamamen aynı şekilde çalışır.</span><span class="sxs-lookup"><span data-stu-id="d59fe-115">The program will work exactly the same.</span></span>

<span data-ttu-id="d59fe-116">Ayrıca, daha fazla değişiklik yaparsanız `SearchDirectoryArgs` bir struct olarak değiştirebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="d59fe-116">You could also change the `SearchDirectoryArgs` to a struct, if you make one more change:</span></span>

```csharp
internal struct SearchDirectoryArgs
{
    internal string CurrentSearchDirectory { get; }
    internal int TotalDirs { get; }
    internal int CompletedDirs { get; }

    internal SearchDirectoryArgs(string dir, int totalDirs, int completedDirs) : this()
    {
        CurrentSearchDirectory = dir;
        TotalDirs = totalDirs;
        CompletedDirs = completedDirs;
    }
}
```

<span data-ttu-id="d59fe-117">Ek değişiklik, tüm alanları Başlatan oluşturucuyu girmeden önce parametresiz oluşturucuyu çağırmaktır.</span><span class="sxs-lookup"><span data-stu-id="d59fe-117">The additional change is to call the parameterless constructor before entering the constructor that initializes all the fields.</span></span> <span data-ttu-id="d59fe-118">Bu ek olmadan, kuralları C# atanmadan önce özelliklere erişilmekte olduğunu raporlayabilir.</span><span class="sxs-lookup"><span data-stu-id="d59fe-118">Without that addition, the rules of C# would report that the properties are being accessed before they have been assigned.</span></span>

<span data-ttu-id="d59fe-119">Bir sınıftan (başvuru türü) `FileFoundArgs` bir struct (değer türü) olarak değiştirmemelisiniz.</span><span class="sxs-lookup"><span data-stu-id="d59fe-119">You should not change the `FileFoundArgs` from a class (reference type) to a struct (value type).</span></span> <span data-ttu-id="d59fe-120">Bunun nedeni, Cancel işleme Protokolü olay bağımsız değişkenlerinin başvuruya göre geçirilmesini gerektirir.</span><span class="sxs-lookup"><span data-stu-id="d59fe-120">That's because the protocol for handling cancel requires that the event arguments are passed by reference.</span></span> <span data-ttu-id="d59fe-121">Aynı değişikliği yaptıysanız, dosya arama sınıfı hiçbir türlü olay abonesinin yaptığı değişiklikleri hiçbir şekilde gözlemlemez.</span><span class="sxs-lookup"><span data-stu-id="d59fe-121">If you made the same change, the file search class could never observe any changes made by any of the event subscribers.</span></span> <span data-ttu-id="d59fe-122">Her abone için yapının yeni bir kopyası kullanılır ve bu kopya dosya arama nesnesi tarafından görülenden farklı bir kopya olacaktır.</span><span class="sxs-lookup"><span data-stu-id="d59fe-122">A new copy of the structure would be used for each subscriber, and that copy would be a different copy than the one seen by the file search object.</span></span>

<span data-ttu-id="d59fe-123">Daha sonra, bu değişikliğin geriye dönük olarak nasıl uyumlu olduğunu ele alalım.</span><span class="sxs-lookup"><span data-stu-id="d59fe-123">Next, let's consider how this change can be backwards compatible.</span></span>
<span data-ttu-id="d59fe-124">Kısıtlamanın kaldırılması var olan herhangi bir kodu etkilemez.</span><span class="sxs-lookup"><span data-stu-id="d59fe-124">The removal of the constraint does not affect any existing code.</span></span> <span data-ttu-id="d59fe-125">Mevcut herhangi bir olay bağımsız değişken türü `System.EventArgs`türetmeye devam eder.</span><span class="sxs-lookup"><span data-stu-id="d59fe-125">Any existing event argument types do still derive from `System.EventArgs`.</span></span>
<span data-ttu-id="d59fe-126">Geriye dönük uyumluluk, `System.EventArgs`türetmeye devam edebilecekleri önemli bir nedendir.</span><span class="sxs-lookup"><span data-stu-id="d59fe-126">Backwards compatibility is one major reason why they will continue to derive from `System.EventArgs`.</span></span> <span data-ttu-id="d59fe-127">Var olan tüm olay aboneleri, klasik kalıbı izleyen bir olaya abone olur.</span><span class="sxs-lookup"><span data-stu-id="d59fe-127">Any existing event subscribers will be subscribers to an event that followed the classic pattern.</span></span>

<span data-ttu-id="d59fe-128">Benzer mantığın ardından, artık oluşturulan herhangi bir olay bağımsız değişken türü herhangi bir mevcut kod tabanı içinde abone olamaz.</span><span class="sxs-lookup"><span data-stu-id="d59fe-128">Following similar logic, any event argument type created now would not have any subscribers in any existing codebases.</span></span> <span data-ttu-id="d59fe-129">`System.EventArgs` türetmeyen yeni olay türleri, bu kod temellerini bozmaz.</span><span class="sxs-lookup"><span data-stu-id="d59fe-129">New event types that do not derive from `System.EventArgs` will not break those codebases.</span></span>

## <a name="events-with-async-subscribers"></a><span data-ttu-id="d59fe-130">Zaman uyumsuz aboneler içeren olaylar</span><span class="sxs-lookup"><span data-stu-id="d59fe-130">Events with Async subscribers</span></span>

<span data-ttu-id="d59fe-131">Bilgi edinmek için bir son örüntüsünün olması gerekir: zaman uyumsuz kod çağıran olay abonelerini doğru şekilde yazma.</span><span class="sxs-lookup"><span data-stu-id="d59fe-131">You have one final pattern to learn: How to correctly write event subscribers that call async code.</span></span> <span data-ttu-id="d59fe-132">Bu zorluk, [zaman uyumsuz ve await](async.md)makalesinde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="d59fe-132">The challenge is described in the article on [async and await](async.md).</span></span> <span data-ttu-id="d59fe-133">Zaman uyumsuz metotlar void dönüş türüne sahip olabilir, ancak bu kesinlikle önerilmez.</span><span class="sxs-lookup"><span data-stu-id="d59fe-133">Async methods can have a void return type, but that is strongly discouraged.</span></span> <span data-ttu-id="d59fe-134">Olay abone kodunuz zaman uyumsuz bir yöntem çağırdığında, hiçbir seçeneğiniz yoktur ancak bir `async void` yöntemi oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d59fe-134">When your event subscriber code calls an async method, you have no choice but to create an `async void` method.</span></span> <span data-ttu-id="d59fe-135">Olay işleyicisi imzası gereklidir.</span><span class="sxs-lookup"><span data-stu-id="d59fe-135">The event handler signature requires it.</span></span>

<span data-ttu-id="d59fe-136">Bu rakip kılavuzun mutabakatını yapmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="d59fe-136">You need to reconcile this opposing guidance.</span></span> <span data-ttu-id="d59fe-137">Bir şekilde, güvenli bir `async void` yöntemi oluşturmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="d59fe-137">Somehow, you must create a safe `async void` method.</span></span> <span data-ttu-id="d59fe-138">Uygulamanız gereken düzenin temelleri aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="d59fe-138">The basics of the pattern you need to implement are below:</span></span>

```csharp
worker.StartWorking += async (sender, eventArgs) =>
{
    try 
    {
        await DoWorkAsync();
    }
    catch (Exception e)
    {
        //Some form of logging.
        Console.WriteLine($"Async task failure: {e.ToString()}");
        // Consider gracefully, and quickly exiting.
    }
};
```

<span data-ttu-id="d59fe-139">İlk olarak, işleyicinin zaman uyumsuz işleyici olarak işaretlendiğinden emin olun.</span><span class="sxs-lookup"><span data-stu-id="d59fe-139">First, notice that the handler is marked as an async handler.</span></span> <span data-ttu-id="d59fe-140">Bir olay işleyicisi temsilci türüne atanmakta olduğundan, void dönüş türüne sahip olur.</span><span class="sxs-lookup"><span data-stu-id="d59fe-140">Because it is being assigned to an event handler delegate type, it will have a void return type.</span></span> <span data-ttu-id="d59fe-141">Bu, işleyicide gösterilen kalıbı izlemeniz ve tüm özel durumların zaman uyumsuz işleyicinin içeriğinden çıkmasına izin vermeniz gerektiği anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="d59fe-141">That means you must follow the pattern shown in the handler, and not allow any exceptions to be thrown out of the context of the async handler.</span></span> <span data-ttu-id="d59fe-142">Bir görev döndürmediğinden, hatayı hatalı duruma girerek bildiremeyen bir görev yoktur.</span><span class="sxs-lookup"><span data-stu-id="d59fe-142">Because it does not return a task, there is no task that can report the error by entering the faulted state.</span></span> <span data-ttu-id="d59fe-143">Yöntemi zaman uyumsuz olduğundan, yöntem özel durumu oluşturmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="d59fe-143">Because the method is async, the method can't simply throw the exception.</span></span> <span data-ttu-id="d59fe-144">(Çağırma yöntemi `async`olduğundan yürütmeye devam etti.) Gerçek çalışma zamanı davranışı farklı ortamlar için farklı şekilde tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="d59fe-144">(The calling method has continued execution because it is `async`.) The actual runtime behavior will be defined differently for different environments.</span></span> <span data-ttu-id="d59fe-145">İş parçacığını veya iş parçacığına sahip olan işlemi sonlandırabilir veya işlemi belirsiz bir durumda bırakabilir.</span><span class="sxs-lookup"><span data-stu-id="d59fe-145">It may terminate the thread or the process that owns the thread, or leave the process in an indeterminate state.</span></span> <span data-ttu-id="d59fe-146">Tüm bu olası sonuçlar yüksek oranda istenmeyen bir süreçlerdir.</span><span class="sxs-lookup"><span data-stu-id="d59fe-146">All of these potential outcomes are highly undesirable.</span></span>

<span data-ttu-id="d59fe-147">Bu nedenle, kendi TRY bloğinizdeki zaman uyumsuz görev için Await ifadesini sarmalısınız.</span><span class="sxs-lookup"><span data-stu-id="d59fe-147">That's why you should wrap the await statement for the async Task in your own try block.</span></span> <span data-ttu-id="d59fe-148">Hatalı bir göreve neden olursa, hatayı günlüğe kaydedebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d59fe-148">If it does cause a faulted task, you can log the error.</span></span> <span data-ttu-id="d59fe-149">Uygulamanızın kurtaramayacağı bir hata ise programdan hızlı ve sorunsuz bir şekilde çıkabilirsiniz</span><span class="sxs-lookup"><span data-stu-id="d59fe-149">If it is an error from which your application cannot recover, you can exit the program quickly and gracefully</span></span>

<span data-ttu-id="d59fe-150">Bunlar, .NET olay deseninin önemli güncelleştirmeleridir.</span><span class="sxs-lookup"><span data-stu-id="d59fe-150">Those are the major updates to the .NET event pattern.</span></span> <span data-ttu-id="d59fe-151">Üzerinde çalıştığınız kitaplıklarda daha önceki sürümlere ait birçok örnek görürsünüz.</span><span class="sxs-lookup"><span data-stu-id="d59fe-151">You will see many examples of the earlier versions in the libraries you work with.</span></span> <span data-ttu-id="d59fe-152">Ancak, en son desenlerin de ne olduğunu anlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="d59fe-152">However, you should understand what the latest patterns are as well.</span></span>

<span data-ttu-id="d59fe-153">Bu serinin sonraki makalesi tasarımlarınızın `delegates` ve `events` kullanımını ayırt etmenize yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="d59fe-153">The next article in this series helps you distinguish between using `delegates` and `events` in your designs.</span></span> <span data-ttu-id="d59fe-154">Bunlar benzer kavramlardır ve bu makale programlarınıza en iyi kararı vermenize yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="d59fe-154">They are similar concepts, and that article will help you make the best decision for your programs.</span></span>

[<span data-ttu-id="d59fe-155">Next</span><span class="sxs-lookup"><span data-stu-id="d59fe-155">Next</span></span>](distinguish-delegates-events.md)
