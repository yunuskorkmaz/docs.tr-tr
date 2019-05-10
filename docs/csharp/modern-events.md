---
title: Güncelleştirilmiş .NET Core olay deseni
description: Nasıl .NET Core olay deseni esneklik ile geriye dönük uyumluluk sağlar ve nasıl güvenli bir olay işleme ile zaman uyumsuz aboneleri uygulanacağını öğrenin.
ms.date: 06/20/2016
ms.assetid: 9aa627c3-3222-4094-9ca8-7e88e1071e06
ms.openlocfilehash: 158295215932f54c75afdf1e96d48453434129fe
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64751778"
---
# <a name="the-updated-net-core-event-pattern"></a><span data-ttu-id="e9a24-103">Güncelleştirilmiş .NET Core olay deseni</span><span class="sxs-lookup"><span data-stu-id="e9a24-103">The Updated .NET Core Event Pattern</span></span>

[<span data-ttu-id="e9a24-104">Önceki</span><span class="sxs-lookup"><span data-stu-id="e9a24-104">Previous</span></span>](event-pattern.md)

<span data-ttu-id="e9a24-105">Önceki makalede en yaygın olay desenleri açıklanmıştır.</span><span class="sxs-lookup"><span data-stu-id="e9a24-105">The previous article discussed the most common event patterns.</span></span> <span data-ttu-id="e9a24-106">.NET core daha gevşek bir düzeni vardır.</span><span class="sxs-lookup"><span data-stu-id="e9a24-106">.NET Core has a more relaxed pattern.</span></span> <span data-ttu-id="e9a24-107">Bu sürümde `EventHandler<TEventArgs>` tanımı artık kısıtlaması vardır, `TEventArgs` bir sınıf nesnesinden türetilmesi gerekir `System.EventArgs`.</span><span class="sxs-lookup"><span data-stu-id="e9a24-107">In this version, the `EventHandler<TEventArgs>` definition no longer has the constraint that `TEventArgs` must be a class derived from `System.EventArgs`.</span></span>

<span data-ttu-id="e9a24-108">Bu, sizin için daha fazla esneklik sunan ve geriye dönük uyumludur.</span><span class="sxs-lookup"><span data-stu-id="e9a24-108">This increases flexibility for you, and is backwards compatible.</span></span> <span data-ttu-id="e9a24-109">Esnekliği başlayalım.</span><span class="sxs-lookup"><span data-stu-id="e9a24-109">Let's start with the flexibility.</span></span> <span data-ttu-id="e9a24-110">' % S'sınıfı System.EventArgs bir yöntem sunar: `MemberwiseClone()`, nesnenin sığ bir kopya oluşturur.</span><span class="sxs-lookup"><span data-stu-id="e9a24-110">The class System.EventArgs introduces one method: `MemberwiseClone()`, which creates a shallow copy of the object.</span></span>
<span data-ttu-id="e9a24-111">Yöntemi herhangi bir sınıftan türetilen için işlevselliği uygulamak için yansıma kullanması gerektiğini `EventArgs`.</span><span class="sxs-lookup"><span data-stu-id="e9a24-111">That method must use reflection in order to implement its functionality for any class derived from `EventArgs`.</span></span> <span data-ttu-id="e9a24-112">Bu işlevsellik belirli bir türetilmiş sınıfta oluşturmak daha kolay olur.</span><span class="sxs-lookup"><span data-stu-id="e9a24-112">That functionality is easier to create in a specific derived class.</span></span> <span data-ttu-id="e9a24-113">Etkili bir şekilde System.EventArgs türetme tasarımlarınızı sınırlar, ancak herhangi bir ek yararı sağlamaz bir kısıtlaması olduğu anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="e9a24-113">That effectively means that deriving from System.EventArgs is a constraint that limits your designs, but does not provide any additional benefit.</span></span>
<span data-ttu-id="e9a24-114">Aslında, tanımlarını değiştirebilirsiniz `FileFoundArgs` ve `SearchDirectoryArgs` oldukları türetilmesi değil böylece `EventArgs`.</span><span class="sxs-lookup"><span data-stu-id="e9a24-114">In fact, you can change the definitions of `FileFoundArgs` and `SearchDirectoryArgs` so that they do not derive from `EventArgs`.</span></span>
<span data-ttu-id="e9a24-115">Program tamamen aynı çalışır.</span><span class="sxs-lookup"><span data-stu-id="e9a24-115">The program will work exactly the same.</span></span>

<span data-ttu-id="e9a24-116">Ayrıca değişebilir `SearchDirectoryArgs` bir daha fazla değişiklik yaparsanız, bir yapı için:</span><span class="sxs-lookup"><span data-stu-id="e9a24-116">You could also change the `SearchDirectoryArgs` to a struct, if you make one more change:</span></span>

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

<span data-ttu-id="e9a24-117">Ek değişiklik parametresiz bir oluşturucu tüm alanları başlatır Oluşturucusu girmeden önce çağırmaktır.</span><span class="sxs-lookup"><span data-stu-id="e9a24-117">The additional change is to call the parameterless constructor before entering the constructor that initializes all the fields.</span></span> <span data-ttu-id="e9a24-118">Ayrıca, kurallarına olmadan C# özellikleri, atanmış önce erişildiği rapor.</span><span class="sxs-lookup"><span data-stu-id="e9a24-118">Without that addition, the rules of C# would report that the properties are being accessed before they have been assigned.</span></span>

<span data-ttu-id="e9a24-119">Değil değiştirmelisiniz `FileFoundArgs` yapı (değer türü) için sınıfından (başvuru türü).</span><span class="sxs-lookup"><span data-stu-id="e9a24-119">You should not change the `FileFoundArgs` from a class (reference type) to a struct (value type).</span></span> <span data-ttu-id="e9a24-120">Olay bağımsız değişkenleri başvuruya göre iletilir iptal işlemek için bir protokol gerektiren olmasıdır.</span><span class="sxs-lookup"><span data-stu-id="e9a24-120">That's because the protocol for handling cancel requires that the event arguments are passed by reference.</span></span> <span data-ttu-id="e9a24-121">Aynı değişikliği yaptıysanız, dosya arama sınıfı hiçbir zaman herhangi bir olay aboneler tarafından yapılan değişiklikler mümkün.</span><span class="sxs-lookup"><span data-stu-id="e9a24-121">If you made the same change, the file search class could never observe any changes made by any of the event subscribers.</span></span> <span data-ttu-id="e9a24-122">Her abone için yeni bir kopyasını yapısı kullanılacaktır ve bu kopyayı dosya arama nesne tarafından görülen olandan farklı bir kopyasını olacaktır.</span><span class="sxs-lookup"><span data-stu-id="e9a24-122">A new copy of the structure would be used for each subscriber, and that copy would be a different copy than the one seen by the file search object.</span></span>

<span data-ttu-id="e9a24-123">Ardından, bu değişiklik nasıl geriye dönük olarak uyumlu olabilir düşünelim.</span><span class="sxs-lookup"><span data-stu-id="e9a24-123">Next, let's consider how this change can be backwards compatible.</span></span>
<span data-ttu-id="e9a24-124">Kısıtlamanın kaldırılması, mevcut kodlar etkilemez.</span><span class="sxs-lookup"><span data-stu-id="e9a24-124">The removal of the constraint does not affect any existing code.</span></span> <span data-ttu-id="e9a24-125">Var olan herhangi bir olay bağımsız değişken türü hala türetilen `System.EventArgs`.</span><span class="sxs-lookup"><span data-stu-id="e9a24-125">Any existing event argument types do still derive from `System.EventArgs`.</span></span>
<span data-ttu-id="e9a24-126">Geriye dönük uyumluluk neden bunlar çalışmaya devam edecek öğesinden türetilen önemli nedenlerinden biri olan `System.EventArgs`.</span><span class="sxs-lookup"><span data-stu-id="e9a24-126">Backwards compatibility is one major reason why they will continue to derive from `System.EventArgs`.</span></span> <span data-ttu-id="e9a24-127">Var olan bir etkinlik abonelerinden Klasik desenin takip bir olaya abone olur.</span><span class="sxs-lookup"><span data-stu-id="e9a24-127">Any existing event subscribers will be subscribers to an event that followed the classic pattern.</span></span>

<span data-ttu-id="e9a24-128">Benzer mantığı, tüm izleme olay bağımsız değişkeni oluşturulan türü artık değil sahip herhangi bir varolan tüm aboneler çıkabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e9a24-128">Following similar logic, any event argument type created now would not have any subscribers in any existing codebases.</span></span> <span data-ttu-id="e9a24-129">Öğesinden türetilen değil yeni olay türleri `System.EventArgs` Bu kod tabanlarında sonu olur.</span><span class="sxs-lookup"><span data-stu-id="e9a24-129">New event types that do not derive from `System.EventArgs` will not break those codebases.</span></span>

## <a name="events-with-async-subscribers"></a><span data-ttu-id="e9a24-130">Zaman uyumsuz abonelere olayları</span><span class="sxs-lookup"><span data-stu-id="e9a24-130">Events with Async subscribers</span></span>

<span data-ttu-id="e9a24-131">Bilgi edinmek için bir son deseni aşağıdakiler: Zaman uyumsuz kodu çağıran etkinlik abonelerinden doğru şekilde yazmak nasıl.</span><span class="sxs-lookup"><span data-stu-id="e9a24-131">You have one final pattern to learn: How to correctly write event subscribers that call async code.</span></span> <span data-ttu-id="e9a24-132">Sınama üzerinde makalesinde açıklanan [async ve await](async.md).</span><span class="sxs-lookup"><span data-stu-id="e9a24-132">The challenge is described in the article on [async and await](async.md).</span></span> <span data-ttu-id="e9a24-133">Zaman uyumsuz yöntemlerin dönüş türü void olabilir, ancak kesinlikle önerilmez.</span><span class="sxs-lookup"><span data-stu-id="e9a24-133">Async methods can have a void return type, but that is strongly discouraged.</span></span> <span data-ttu-id="e9a24-134">Olay abonesi kodunuz bir zaman uyumsuz yöntemini çağırdığında oluşturmak için seçim yok ancak sahip bir `async void` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="e9a24-134">When your event subscriber code calls an async method, you have no choice but to create an `async void` method.</span></span> <span data-ttu-id="e9a24-135">Olay işleyicisinin imzası gerektiriyor.</span><span class="sxs-lookup"><span data-stu-id="e9a24-135">The event handler signature requires it.</span></span>

<span data-ttu-id="e9a24-136">Kpı'lere bu kılavuz mutabakat sağlamak gerekir.</span><span class="sxs-lookup"><span data-stu-id="e9a24-136">You need to reconcile this opposing guidance.</span></span> <span data-ttu-id="e9a24-137">Güvenli bir şekilde, oluşturmalısınız `async void` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="e9a24-137">Somehow, you must create a safe `async void` method.</span></span> <span data-ttu-id="e9a24-138">Desen uygulamak için gereken temel aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="e9a24-138">The basics of the pattern you need to implement are below:</span></span>

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

<span data-ttu-id="e9a24-139">İlk olarak, işleyiciyi zaman uyumsuz bir işleyici işaretlenmiş olduğuna dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="e9a24-139">First, notice that the handler is marked as an async handler.</span></span> <span data-ttu-id="e9a24-140">Kendine atanan temsilci türüne bir olay işleyicisi, void dönüş türüne sahip.</span><span class="sxs-lookup"><span data-stu-id="e9a24-140">Because it is being assigned to an event handler delegate type, it will have a void return type.</span></span> <span data-ttu-id="e9a24-141">Bu işleyici içinde gösterilen desenini izler ve zaman uyumsuz işleyici bağlamı dışında oluşturulması tüm özel durumlara izin vermeyecek anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="e9a24-141">That means you must follow the pattern shown in the handler, and not allow any exceptions to be thrown out of the context of the async handler.</span></span> <span data-ttu-id="e9a24-142">Bir task döndürmüyor olduğundan, hata, hatalı durumuna girerek bildirebileceği görev yok.</span><span class="sxs-lookup"><span data-stu-id="e9a24-142">Because it does not return a task, there is no task that can report the error by entering the faulted state.</span></span> <span data-ttu-id="e9a24-143">Zaman uyumsuz yöntem olduğundan, yöntemi yalnızca özel durumu atılamıyor.</span><span class="sxs-lookup"><span data-stu-id="e9a24-143">Because the method is async, the method can't simply throw the exception.</span></span> <span data-ttu-id="e9a24-144">(Yöntemi çağrılırken, olduğundan yürütme devam etti `async`.) Fiili çalışma zamanı davranışı farklı farklı ortamlar için tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="e9a24-144">(The calling method has continued execution because it is `async`.) The actual runtime behavior will be defined differently for different environments.</span></span> <span data-ttu-id="e9a24-145">İş parçacığı sonlandırabilir, program sonlandırabilir veya program belirsiz bir durumda bırakabilir.</span><span class="sxs-lookup"><span data-stu-id="e9a24-145">It may terminate the thread, it may terminate the program, or it may leave the program in an undetermined state.</span></span> <span data-ttu-id="e9a24-146">Bu iyi bir sonuç yok.</span><span class="sxs-lookup"><span data-stu-id="e9a24-146">None of those are good outcomes.</span></span>

<span data-ttu-id="e9a24-147">İşte bu nedenle kendi try bloğunda bekleme ifadesinin zaman uyumsuz görev için uzun olmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="e9a24-147">That's why you should wrap the await statement for the async Task in your own try block.</span></span> <span data-ttu-id="e9a24-148">Hatalı bir görev neden olmaz, hata oturum açabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e9a24-148">If it does cause a faulted task, you can log the error.</span></span> <span data-ttu-id="e9a24-149">Uygulamanızın içinden kurtaramazsınız bir hata olması durumunda, hızlı ve düzgün bir şekilde program çıkabilirsiniz</span><span class="sxs-lookup"><span data-stu-id="e9a24-149">If it is an error from which your application cannot recover, you can exit the program quickly and gracefully</span></span>

<span data-ttu-id="e9a24-150">Önemli güncelleştirmeler .NET olay deseni olanlardır.</span><span class="sxs-lookup"><span data-stu-id="e9a24-150">Those are the major updates to the .NET event pattern.</span></span> <span data-ttu-id="e9a24-151">Birlikte çalıştığınız kitaplıklar daha önceki sürümlerinde, birçok örneği görürsünüz.</span><span class="sxs-lookup"><span data-stu-id="e9a24-151">You will see many examples of the earlier versions in the libraries you work with.</span></span> <span data-ttu-id="e9a24-152">Ancak, en son desenleri de nelerdir anlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="e9a24-152">However, you should understand what the latest patterns are as well.</span></span>

<span data-ttu-id="e9a24-153">Bu serideki sonraki makalede kullanma arasında ayırt etmenize yardımcı olur. `delegates` ve `events` tasarımlarınızı içinde.</span><span class="sxs-lookup"><span data-stu-id="e9a24-153">The next article in this series helps you distinguish between using `delegates` and `events` in your designs.</span></span> <span data-ttu-id="e9a24-154">Benzer kavramları olduklarını ve bu makalede programlar için en iyi karar vermenize yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="e9a24-154">They are similar concepts, and that article will help you make the best decision for your programs.</span></span>

[<span data-ttu-id="e9a24-155">Next</span><span class="sxs-lookup"><span data-stu-id="e9a24-155">Next</span></span>](distinguish-delegates-events.md)
