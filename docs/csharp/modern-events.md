---
title: "Güncelleştirilmiş .NET Core olay düzeni"
description: "Nasıl .NET Core olay deseni esnekliği geriye dönük uyumluluk sağlar ve zaman uyumsuz aboneleri ile güvenli olay işleme uygulama öğrenin."
keywords: .NET, .NET core
author: BillWagner
ms.author: wiwagn
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: 9aa627c3-3222-4094-9ca8-7e88e1071e06
ms.openlocfilehash: cf69cbe0a7adbd274d1cb9e9544dda77d9fa1740
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="the-updated-net-core-event-pattern"></a><span data-ttu-id="06233-104">Güncelleştirilmiş .NET Core olay düzeni</span><span class="sxs-lookup"><span data-stu-id="06233-104">The Updated .NET Core Event Pattern</span></span>

[<span data-ttu-id="06233-105">Önceki</span><span class="sxs-lookup"><span data-stu-id="06233-105">Previous</span></span>](event-pattern.md)

<span data-ttu-id="06233-106">Önceki makaleyi en yaygın olay desenleri açıklanmıştır.</span><span class="sxs-lookup"><span data-stu-id="06233-106">The previous article discussed the most common event patterns.</span></span> <span data-ttu-id="06233-107">.NET core daha esnek bir deseni vardır.</span><span class="sxs-lookup"><span data-stu-id="06233-107">.NET Core has a more relaxed pattern.</span></span> <span data-ttu-id="06233-108">Bu sürümde `EventHandler<TEventArgs>` tanımı artık kısıtlaması var, `TEventArgs` bir sınıfın türetildiği gerekir `System.EventArgs`.</span><span class="sxs-lookup"><span data-stu-id="06233-108">In this version, the `EventHandler<TEventArgs>` definition no longer has the constraint that `TEventArgs` must be a class derived from `System.EventArgs`.</span></span>

<span data-ttu-id="06233-109">Bu sizin için esnekliğini artırır ve geriye dönük olarak uyumludur.</span><span class="sxs-lookup"><span data-stu-id="06233-109">This increases flexibility for you, and is backwards compatible.</span></span> <span data-ttu-id="06233-110">Esnekliği başlayalım.</span><span class="sxs-lookup"><span data-stu-id="06233-110">Let's start with the flexibility.</span></span> <span data-ttu-id="06233-111">System.EventArgs sınıfı bir yöntem sunar: `MemberwiseClone()`, nesne basit bir kopyasını oluşturur.</span><span class="sxs-lookup"><span data-stu-id="06233-111">The class System.EventArgs introduces one method: `MemberwiseClone()`, which creates a shallow copy of the object.</span></span>
<span data-ttu-id="06233-112">Herhangi bir sınıfın türetildiği için işlevselliği uygulamak için yöntemi yansıma kullanmalıdır `EventArgs`.</span><span class="sxs-lookup"><span data-stu-id="06233-112">That method must use reflection in order to implement its functionality for any class derived from `EventArgs`.</span></span> <span data-ttu-id="06233-113">Bu işlevselliği, belirli bir türetilmiş sınıfta oluşturmak kolaydır.</span><span class="sxs-lookup"><span data-stu-id="06233-113">That functionality is easier to create in a specific derived class.</span></span> <span data-ttu-id="06233-114">Etkili bir şekilde System.EventArgs türetme sizin tasarımlar sınırlar, ancak ek bir avantaja sağlamaz bir kısıtlaması olduğu anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="06233-114">That effectively means that deriving from System.EventArgs is a constraint that limits your designs, but does not provide any additional benefit.</span></span>
<span data-ttu-id="06233-115">Aslında, değişiklikler tanımlarını `FileFoundArgs` ve `SearchDirectoryArgs` böylece bunlar öğesinden türetilen değil `EventArgs`.</span><span class="sxs-lookup"><span data-stu-id="06233-115">In fact, you can changes the definitions of `FileFoundArgs` and `SearchDirectoryArgs` so that they do not derive from `EventArgs`.</span></span>
<span data-ttu-id="06233-116">Program tam olarak aynı çalışır.</span><span class="sxs-lookup"><span data-stu-id="06233-116">The program will work exactly the same.</span></span>

<span data-ttu-id="06233-117">Aynı zamanda değişebilir `SearchDirectoryArgs` ayrıca bir daha fazla değişiklik yaparsanız, bir yapı için:</span><span class="sxs-lookup"><span data-stu-id="06233-117">You could also change the `SearchDirectoryArgs` to a struct, if you also make one more change:</span></span>

```csharp  
internal struct SearchDirectoryArgs  
{  
    internal string CurrentSearchDirectory { get; }  
    internal int TotalDirs { get; }  
    internal int CompletedDirs { get; }  
    
    internal SearchDirectoryArgs(string dir, int totalDirs, 
        int completedDirs) : this()  
    {  
        CurrentSearchDirectory = dir;  
        TotalDirs = totalDirs;  
        CompletedDirs = completedDirs;  
    }  
}  
```   

<span data-ttu-id="06233-118">Ek değişiklik varsayılan oluşturucu tüm alanları başlatır Oluşturucusu girmeden önce çağırmaktır.</span><span class="sxs-lookup"><span data-stu-id="06233-118">The additional change is to call the default constructor before entering the constructor that initializes all the fields.</span></span> <span data-ttu-id="06233-119">Bu ayrıca, C# kuralları, atanmış önce özellikleri Erişilmekte olduğunu raporlar.</span><span class="sxs-lookup"><span data-stu-id="06233-119">Without that addition, the rules of C# would report that the properties are being accessed before they have been assigned.</span></span>

<span data-ttu-id="06233-120">Değil değiştirmelisiniz `FileFoundArgs` yapısı (değer türü) için bir sınıftan (başvuru türü).</span><span class="sxs-lookup"><span data-stu-id="06233-120">You should not change the `FileFoundArgs` from a class (reference type) to a struct (value type).</span></span> <span data-ttu-id="06233-121">Olay bağımsız değişkenleri başvuruya göre geçirilir iptal işlemek için protokol gerektirir olmasıdır.</span><span class="sxs-lookup"><span data-stu-id="06233-121">That's because the protocol for handling cancel requires that the event arguments are passed by reference.</span></span> <span data-ttu-id="06233-122">Aynı değişiklik yaptıysanız, dosya arama sınıfı hiçbir zaman herhangi bir olay aboneler tarafından yapılan değişiklikler girdiğini.</span><span class="sxs-lookup"><span data-stu-id="06233-122">If you made the same change, the file search class could never observe any changes made by any of the event subscribers.</span></span> <span data-ttu-id="06233-123">Yapısının yeni bir kopya her abone için kullanılır ve bu kopyayı dosya arama nesne tarafından görülen olandan farklı bir kopyasını olacaktır.</span><span class="sxs-lookup"><span data-stu-id="06233-123">A new copy of the structure would be used for each subscriber, and that copy would be a different copy than the one seen by the file search object.</span></span>

<span data-ttu-id="06233-124">Ardından, şimdi bu değişiklik nasıl geriye dönük olarak uyumlu olabilir göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="06233-124">Next, let's consider how this change can be backwards compatible.</span></span>
<span data-ttu-id="06233-125">Kısıtlama kaldırılmasını herhangi bir varolan kod etkilemez.</span><span class="sxs-lookup"><span data-stu-id="06233-125">The removal of the constraint does not affect any existing code.</span></span> <span data-ttu-id="06233-126">Tüm mevcut olay bağımsız değişken türleri hala türetilen `System.EventArgs`.</span><span class="sxs-lookup"><span data-stu-id="06233-126">Any existing event argument types do still derive from `System.EventArgs`.</span></span>
<span data-ttu-id="06233-127">Geriye dönük uyumluluk neden bunlar devam öğesinden türetilen bir ana nedeni `System.EventArgs`.</span><span class="sxs-lookup"><span data-stu-id="06233-127">Backwards compatibility is one major reason why they will continue to derive from `System.EventArgs`.</span></span> <span data-ttu-id="06233-128">Mevcut tüm olay aboneler Klasik düzeni izlenen bir olay abonelere olacaktır.</span><span class="sxs-lookup"><span data-stu-id="06233-128">Any existing event subscribers will be subscribers to an event that followed the classic pattern.</span></span>

<span data-ttu-id="06233-129">Benzer mantığı herhangi aşağıdaki oluşturulan türü artık sahip tüm mevcut olan tüm abonelerin olay bağımsız değişken olarak kullanılabilecek kod temeli.</span><span class="sxs-lookup"><span data-stu-id="06233-129">Following similar logic, any event argument type created now would not have any subscribers in any existing codebases.</span></span> <span data-ttu-id="06233-130">Öğesinden türetilen değil yeni olay türleri `System.EventArgs` olanlar olarak kullanılabilecek kod temeli sonu olur.</span><span class="sxs-lookup"><span data-stu-id="06233-130">New event types that do not derive from `System.EventArgs` will not break those codebases.</span></span>

## <a name="events-with-async-subscribers"></a><span data-ttu-id="06233-131">Zaman uyumsuz aboneleri olan olaylar</span><span class="sxs-lookup"><span data-stu-id="06233-131">Events with Async subscribers</span></span>

<span data-ttu-id="06233-132">Bilgi edinmek için bir son deseni vardır: zaman uyumsuz kodu çağırma olay aboneleri doğru yazma.</span><span class="sxs-lookup"><span data-stu-id="06233-132">You have one final pattern to learn: How to correctly write event subscribers that call async code.</span></span> <span data-ttu-id="06233-133">Sınama üzerinde makalesinde açıklanan [async ve await](async.md).</span><span class="sxs-lookup"><span data-stu-id="06233-133">The challenge is described in the article on [async and await](async.md).</span></span> <span data-ttu-id="06233-134">Zaman uyumsuz yöntemleri geçersiz bir dönüş türüne sahip olabilir, ancak bu kesinlikle önerilmez.</span><span class="sxs-lookup"><span data-stu-id="06233-134">Async methods can have a void return type, but that is strongly discouraged.</span></span> <span data-ttu-id="06233-135">Olay abone kodunuzu bir zaman uyumsuz yöntem çağırdığında oluşturmak için choice yok ancak sahip bir `async void` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="06233-135">When your event subscriber code calls an async method, you have no choice but to create an `async void` method.</span></span> <span data-ttu-id="06233-136">Olay işleyici imzası gerektiriyor.</span><span class="sxs-lookup"><span data-stu-id="06233-136">The event handler signature requires it.</span></span>

<span data-ttu-id="06233-137">Bu rakip kılavuz karşılaştırmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="06233-137">You need to reconcile this opposing guidance.</span></span> <span data-ttu-id="06233-138">Güvenli şekilde, oluşturmalısınız `async void` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="06233-138">Somehow, you must create a safe `async void` method.</span></span> <span data-ttu-id="06233-139">Aşağıda, uygulamanız gereken desen ile ilgili temel bilgiler verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="06233-139">The basics of the pattern you need to implement are below:</span></span>

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

<span data-ttu-id="06233-140">İlk olarak, işleyiciyi zaman uyumsuz işleyici olarak işaretlenmiş dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="06233-140">First, notice that the handler is marked as an async handler.</span></span> <span data-ttu-id="06233-141">Atanmış olduğu için olay işleyicisi için temsilci türüne, geçersiz bir dönüş türüne sahip olur.</span><span class="sxs-lookup"><span data-stu-id="06233-141">Because it is being assigned to an event handler delegate type, it will have a void return type.</span></span> <span data-ttu-id="06233-142">İşleyicisinde gösterilen düzeni izleyin ve zaman uyumsuz işleyici bağlamı dışında durum tüm özel durumlara izin vermeyecek anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="06233-142">That means you must follow the pattern shown in the handler, and not allow any exceptions to be thrown out of the context of the async handler.</span></span> <span data-ttu-id="06233-143">Bir görev döndürmediğinden hata hatalı durum girerek bildirebileceği görev yok.</span><span class="sxs-lookup"><span data-stu-id="06233-143">Because it does not return a task, there is no task that can report the error by entering the faulted state.</span></span> <span data-ttu-id="06233-144">Zaman uyumsuz yöntem olduğu için yöntemi yalnızca özel durumu atılamıyor.</span><span class="sxs-lookup"><span data-stu-id="06233-144">Because the method is async, the method can't simply throw the exception.</span></span> <span data-ttu-id="06233-145">(Çünkü arama yöntemi yürütme devam etti `async`.) Gerçek çalışma zamanı davranışı farklı farklı ortamlar için tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="06233-145">(The calling method has continued execution because it is `async`.) The actual runtime behavior will be defined differently for different environments.</span></span> <span data-ttu-id="06233-146">İş parçacığı sonlandırabilir, program sonlandırabilir veya program belirlenmemiş bir durumda bırakabilir.</span><span class="sxs-lookup"><span data-stu-id="06233-146">It may terminate the thread, it may terminate the program, or it may leave the program in an undetermined state.</span></span> <span data-ttu-id="06233-147">Bu iyi sonuç yok.</span><span class="sxs-lookup"><span data-stu-id="06233-147">None of those are good outcomes.</span></span>

<span data-ttu-id="06233-148">İşte bu nedenle bekleme deyim zaman uyumsuz görev için kendi try bloğunda kaydırılacağını.</span><span class="sxs-lookup"><span data-stu-id="06233-148">That's why you should wrap the await statement for the async Task in your own try block.</span></span> <span data-ttu-id="06233-149">Hatalı bir görev neden, hata oturum açabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="06233-149">If it does cause a faulted task, you can log the error.</span></span> <span data-ttu-id="06233-150">Uygulamanızı kurtarma gerçekleştiremezsiniz bir hata olması durumunda hızla ve dikkatlice program çıkabilirsiniz</span><span class="sxs-lookup"><span data-stu-id="06233-150">If it is an error from which your application cannot recover, you can exit the program quickly and gracefully</span></span>

<span data-ttu-id="06233-151">.NET olay deseni önemli güncelleştirmeler olanlardır.</span><span class="sxs-lookup"><span data-stu-id="06233-151">Those are the major updates to the .NET event pattern.</span></span> <span data-ttu-id="06233-152">İle çalışma kitaplıkları önceki sürümlerde birçok örnekleri görürsünüz.</span><span class="sxs-lookup"><span data-stu-id="06233-152">You will see many examples of the earlier versions in the libraries you work with.</span></span> <span data-ttu-id="06233-153">Ancak, en son desenleri de nelerdir anlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="06233-153">However, you should understand what the latest patterns are as well.</span></span>

<span data-ttu-id="06233-154">Bu serideki sonraki makalede kullanma arasında ayrım yardımcı olan `delegates` ve `events` sizin tasarımlar içinde.</span><span class="sxs-lookup"><span data-stu-id="06233-154">The next article in this series helps you distinguish between using `delegates` and `events` in your designs.</span></span> <span data-ttu-id="06233-155">Benzer kavram olan ve bu makalede programlarınız için en iyi karar vermenize yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="06233-155">They are similar concepts, and that article will help you make the best decision for your programs.</span></span>

[<span data-ttu-id="06233-156">Sonraki</span><span class="sxs-lookup"><span data-stu-id="06233-156">Next</span></span>](distinguish-delegates-events.md)
