---
title: Büyük, Yanıt Veren .NET Framework Uygulamaları Yazma
ms.date: 03/30/2017
ms.assetid: 123457ac-4223-4273-bb58-3bc0e4957e9d
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 57f65feff5260cb83df5354f5d7ee1bad0babb3a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79180576"
---
# <a name="writing-large-responsive-net-framework-apps"></a><span data-ttu-id="1e79d-102">Büyük, Yanıt Veren .NET Framework Uygulamaları Yazma</span><span class="sxs-lookup"><span data-stu-id="1e79d-102">Writing Large, Responsive .NET Framework Apps</span></span>

<span data-ttu-id="1e79d-103">Bu makalede, büyük .NET Framework uygulamalarının veya dosya veya veritabanları gibi büyük miktarda veriyi işleyen uygulamaların performansını artırmak için ipuçları verilmektedir.</span><span class="sxs-lookup"><span data-stu-id="1e79d-103">This article provides tips for improving the performance of large .NET Framework apps, or apps that process a large amount of data such as files or databases.</span></span> <span data-ttu-id="1e79d-104">Bu ipuçları yönetilen kodc# ve Visual Basic derleyicilerini yeniden yazmaktan gelir ve bu makalede C# derleyicisinden birkaç gerçek örnek içerir.</span><span class="sxs-lookup"><span data-stu-id="1e79d-104">These tips come from rewriting the C# and Visual Basic compilers in managed code, and this article includes several real examples from the C# compiler.</span></span>
  
<span data-ttu-id="1e79d-105">.NET Framework, uygulama oluşturmak için son derece verimlidir.</span><span class="sxs-lookup"><span data-stu-id="1e79d-105">The .NET Framework is highly productive for building apps.</span></span> <span data-ttu-id="1e79d-106">Güçlü ve güvenli diller ve zengin bir kütüphane koleksiyonu, uygulama oluşturmayı son derece verimli hale getirsin.</span><span class="sxs-lookup"><span data-stu-id="1e79d-106">Powerful and safe languages and a rich collection of libraries make app building highly fruitful.</span></span> <span data-ttu-id="1e79d-107">Ancak, büyük verimlilik ile sorumluluk geliyor.</span><span class="sxs-lookup"><span data-stu-id="1e79d-107">However, with great productivity comes responsibility.</span></span> <span data-ttu-id="1e79d-108">.NET Framework'ün tüm gücünü kullanmalısınız, ancak gerektiğinde kodunuzu izlemeye hazır olmalısınız.</span><span class="sxs-lookup"><span data-stu-id="1e79d-108">You should use all the power of the .NET Framework, but be prepared to tune your code’s performance when needed.</span></span>
  
## <a name="why-the-new-compiler-performance-applies-to-your-app"></a><span data-ttu-id="1e79d-109">Yeni derleyici performansı uygulamanız için neden geçerlidir?</span><span class="sxs-lookup"><span data-stu-id="1e79d-109">Why the new compiler performance applies to your app</span></span>  
 <span data-ttu-id="1e79d-110">.NET Derleyici Platformu ("Roslyn") ekibi, kodu modellemek ve analiz etmek, araçlar oluşturmak ve Visual Studio'da çok daha zengin, kod bilincine duyarlı deneyimler sağlamak için yeni API'ler sağlamak için yönetilen koddaki C# ve Visual Basic derleyicilerini yeniden yazdı.</span><span class="sxs-lookup"><span data-stu-id="1e79d-110">The .NET Compiler Platform ("Roslyn") team rewrote the C# and Visual Basic compilers in managed code to provide new APIs for modeling and analyzing code, building tools, and enabling much richer, code-aware experiences in Visual Studio.</span></span> <span data-ttu-id="1e79d-111">Derleyicileri yeniden yazmak ve yeni derleyiciler üzerinde Visual Studio deneyimleri oluşturmak, herhangi bir büyük .NET Framework uygulaması veya çok fazla veriyi işleyen herhangi bir uygulama için geçerli olan yararlı performans öngörülerini ortaya çıkardı.</span><span class="sxs-lookup"><span data-stu-id="1e79d-111">Rewriting the compilers and building Visual Studio experiences on the new compilers revealed useful performance insights that are applicable to any large .NET Framework app or any app that processes a lot of data.</span></span> <span data-ttu-id="1e79d-112">C# derleyicisinden gelen kavrayışve örneklerden yararlanmak için derleyiciler hakkında bilgi edinmeniz gerekmez.</span><span class="sxs-lookup"><span data-stu-id="1e79d-112">You don't need to know about compilers to take advantage of the insights and examples from the C# compiler.</span></span>
  
 <span data-ttu-id="1e79d-113">Visual Studio, tanımlayıcıların ve anahtar kelimelerin renklendirilmesi, sözdizimi tamamlama listeleri, hatalar için dalgalandırmalar, parametre ipuçları, kod sorunları ve kod eylemleri gibi kullanıcıların sevdiği tüm IntelliSense özelliklerini oluşturmak için derleyici API'lerini kullanır.</span><span class="sxs-lookup"><span data-stu-id="1e79d-113">Visual Studio uses the compiler APIs to build all the IntelliSense features that users love, such as colorization of identifiers and keywords, syntax completion lists, squiggles for errors, parameter tips, code issues, and code actions.</span></span> <span data-ttu-id="1e79d-114">Visual Studio, geliştiriciler kodlarını yazarken ve değiştirirken bu yardımı sağlar ve derleyici kod geliştiricilerin ini sürekli olarak modellerken Visual Studio'nun yanıt layıcı olarak kalması gerekir.</span><span class="sxs-lookup"><span data-stu-id="1e79d-114">Visual Studio provides this help while developers are typing and changing their code, and Visual Studio must remain responsive while the compiler continually models the code developers edit.</span></span>
  
 <span data-ttu-id="1e79d-115">Son kullanıcılarınız uygulamanızla etkileşimde ne zaman yanıt vermesini beklerler.</span><span class="sxs-lookup"><span data-stu-id="1e79d-115">When your end users interact with your app, they expect it to be responsive.</span></span> <span data-ttu-id="1e79d-116">Yazma veya komut işleme asla engellenmemelidir.</span><span class="sxs-lookup"><span data-stu-id="1e79d-116">Typing or command handling should never be blocked.</span></span> <span data-ttu-id="1e79d-117">Kullanıcı yazmaya devam ederse yardım hızlı bir şekilde açılır veya vazgeçmelidir.</span><span class="sxs-lookup"><span data-stu-id="1e79d-117">Help should pop up quickly or give up if the user continues typing.</span></span> <span data-ttu-id="1e79d-118">Uygulamanız, uygulamanın kendini yavaş hissetmesini sağlayan uzun hesaplamalarla UI iş parçacığının engellenmesini önlemelidir.</span><span class="sxs-lookup"><span data-stu-id="1e79d-118">Your app should avoid blocking the UI thread with long computations that make the app feel sluggish.</span></span>
  
 <span data-ttu-id="1e79d-119">Roslyn derleyicileri hakkında daha fazla bilgi için [.NET Derleyici Platformu SDK'ya](../../csharp/roslyn-sdk/index.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="1e79d-119">For more information about Roslyn compilers, see [The .NET Compiler Platform SDK](../../csharp/roslyn-sdk/index.md).</span></span>
  
## <a name="just-the-facts"></a><span data-ttu-id="1e79d-120">Sadece Gerçekler</span><span class="sxs-lookup"><span data-stu-id="1e79d-120">Just the Facts</span></span>  
 <span data-ttu-id="1e79d-121">Performansı alarken ve duyarlı .NET Framework uygulamaları oluştururken bu gerçekleri göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="1e79d-121">Consider these facts when tuning performance and creating responsive .NET Framework apps.</span></span>
  
### <a name="fact-1-dont-prematurely-optimize"></a><span data-ttu-id="1e79d-122">Gerçek 1: Zamanından önce optimize etmeyin</span><span class="sxs-lookup"><span data-stu-id="1e79d-122">Fact 1: Don’t prematurely optimize</span></span>  
 <span data-ttu-id="1e79d-123">Olması gerekenden daha karmaşık kod yazma, bakım, hata ayıklama ve parlatma maliyetlerine neden olur.</span><span class="sxs-lookup"><span data-stu-id="1e79d-123">Writing code that is more complex than it needs to be incurs maintenance, debugging, and polishing costs.</span></span> <span data-ttu-id="1e79d-124">Deneyimli programcılar, kodlama sorunlarını nasıl çözeceklerine ve daha verimli kodlar yazabilmek için sezgisel bir kavrayışa sahiptir.</span><span class="sxs-lookup"><span data-stu-id="1e79d-124">Experienced programmers have an intuitive grasp of how to solve coding problems and write more efficient code.</span></span> <span data-ttu-id="1e79d-125">Ancak, bazen kodlarını zamanından önce optimize ederler.</span><span class="sxs-lookup"><span data-stu-id="1e79d-125">However, they sometimes prematurely optimize their code.</span></span> <span data-ttu-id="1e79d-126">Örneğin, basit bir dizi yeterli olduğunda karma tablo kullanırlar veya değerleri yeniden hesaplamak yerine bellek sızdırabilecek karmaşık önbelleğe alma kullanırlar.</span><span class="sxs-lookup"><span data-stu-id="1e79d-126">For example, they use a hash table when a simple array would suffice, or use complicated caching that may leak memory instead of simply recomputing values.</span></span> <span data-ttu-id="1e79d-127">Deneyim programcısı olsanız bile, performans için test etmeli ve sorunları bulduğunuzda kodunuzu çözümlemelisiniz.</span><span class="sxs-lookup"><span data-stu-id="1e79d-127">Even if you’re an experience programmer, you should test for performance and analyze your code when you find issues.</span></span>
  
### <a name="fact-2-if-youre-not-measuring-youre-guessing"></a><span data-ttu-id="1e79d-128">Gerçek 2: Eğer ölçüm değilseniz, tahmin ediyoruz</span><span class="sxs-lookup"><span data-stu-id="1e79d-128">Fact 2: If you’re not measuring, you’re guessing</span></span>  
 <span data-ttu-id="1e79d-129">Profiller ve ölçümler yalan söylemez.</span><span class="sxs-lookup"><span data-stu-id="1e79d-129">Profiles and measurements don’t lie.</span></span> <span data-ttu-id="1e79d-130">Profiller, CPU'nun tam yüklü olup olmadığını veya disk G/Ç'de engellenip engellenmediğinizi gösterir.</span><span class="sxs-lookup"><span data-stu-id="1e79d-130">Profiles show you whether the CPU is fully loaded or whether you’re blocked on disk I/O.</span></span> <span data-ttu-id="1e79d-131">Profiller, ne tür ve ne kadar bellek ayırdığınızı ve CPU'nuzun [çöp toplamada](../../standard/garbage-collection/index.md) (GC) çok zaman harcayıp harcamadığınızı söyler.</span><span class="sxs-lookup"><span data-stu-id="1e79d-131">Profiles tell you what kind and how much memory you’re allocating and whether your CPU is spending a lot of time in [garbage collection](../../standard/garbage-collection/index.md) (GC).</span></span>
  
 <span data-ttu-id="1e79d-132">Uygulamanızdaki önemli müşteri deneyimleri veya senaryolar için performans hedefleri belirlemeli ve performansı ölçmek için testler yazmalısınız.</span><span class="sxs-lookup"><span data-stu-id="1e79d-132">You should set performance goals for key customer experiences or scenarios in your app and write tests to measure performance.</span></span> <span data-ttu-id="1e79d-133">Bilimsel yöntemi uygulayarak başarısız testleri araştırın: size rehberlik etmek için profilleri kullanın, sorunun ne olabileceğini varsayılın ve hipotezinizi bir deneme veya kod değişikliğiyle test edin.</span><span class="sxs-lookup"><span data-stu-id="1e79d-133">Investigate failing tests by applying the scientific method: use profiles to guide you, hypothesize what the issue might be, and test your hypothesis with an experiment or code change.</span></span> <span data-ttu-id="1e79d-134">Düzenli sınama ile zaman içinde temel performans ölçümleri belirleyin, böylece performansta gerilemelere neden olan değişiklikleri yalıtabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1e79d-134">Establish baseline performance measurements over time with regular testing, so you can isolate changes that cause regressions in performance.</span></span> <span data-ttu-id="1e79d-135">Performans çalışmalarına titiz bir şekilde yaklaşarak, gerek duymadığınız kod güncelleştirmeleriyle zaman kaybından kurtulursunuz.</span><span class="sxs-lookup"><span data-stu-id="1e79d-135">By approaching performance work in a rigorous way, you’ll avoid wasting time with code updates you don’t need.</span></span>
  
### <a name="fact-3-good-tools-make-all-the-difference"></a><span data-ttu-id="1e79d-136">Gerçek 3: İyi araçlar tüm fark yaratmak</span><span class="sxs-lookup"><span data-stu-id="1e79d-136">Fact 3: Good tools make all the difference</span></span>  
 <span data-ttu-id="1e79d-137">İyi araçlar, en büyük performans sorunlarını (CPU, bellek veya disk) hızla çözmenize ve bu darboğazlara neden olan kodu bulmanıza yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="1e79d-137">Good tools let you drill quickly into the biggest performance issues (CPU, memory, or disk) and help you locate the code that causes those bottlenecks.</span></span> <span data-ttu-id="1e79d-138">Microsoft, [Visual Studio Profiler](/visualstudio/profiling/beginners-guide-to-performance-profiling) ve [PerfView](https://www.microsoft.com/download/details.aspx?id=28567)gibi çeşitli performans araçları ile gönderilmiştir.</span><span class="sxs-lookup"><span data-stu-id="1e79d-138">Microsoft ships a variety of performance tools such as [Visual Studio Profiler](/visualstudio/profiling/beginners-guide-to-performance-profiling) and [PerfView](https://www.microsoft.com/download/details.aspx?id=28567).</span></span>
  
 <span data-ttu-id="1e79d-139">PerfView, disk G/Ç, GC olayları ve bellek gibi derin sorunlara odaklanmanıza yardımcı olan ücretsiz ve inanılmaz derecede güçlü bir araçtır.</span><span class="sxs-lookup"><span data-stu-id="1e79d-139">PerfView is a free and amazingly powerful tool that helps you focus on deep issues such as disk I/O, GC events, and memory.</span></span> <span data-ttu-id="1e79d-140">Windows (ETW) olayları için performansla ilgili [Olay İzleme'yi](../wcf/samples/etw-tracing.md) yakalayabilir ve uygulama başına, işlem başına, yığın başına ve iş parçacığı bilgisi başına kolayca görüntüleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1e79d-140">You can capture performance-related [Event Tracing for Windows](../wcf/samples/etw-tracing.md) (ETW) events and view easily per app, per process, per stack, and per thread information.</span></span> <span data-ttu-id="1e79d-141">PerfView, uygulamanızın ne kadar ve ne tür bellek ayırdığını ve hangi işlevlerin veya çağrı yığınlarının bellek ayırmalarına ne kadar katkıda bulunur.</span><span class="sxs-lookup"><span data-stu-id="1e79d-141">PerfView shows you how much and what kind of memory your app allocates, and which functions or call stacks contribute how much to the memory allocations.</span></span> <span data-ttu-id="1e79d-142">Ayrıntılar için, araca dahil olan zengin yardım konularına, demolara ve videolara bakın (Kanal 9'daki [PerfView eğitimleri](https://channel9.msdn.com/Series/PerfView-Tutorial) gibi).</span><span class="sxs-lookup"><span data-stu-id="1e79d-142">For details, see the rich help topics, demos, and videos included with the tool (such as the [PerfView tutorials](https://channel9.msdn.com/Series/PerfView-Tutorial) on Channel 9).</span></span>
  
### <a name="fact-4-its-all-about-allocations"></a><span data-ttu-id="1e79d-143">Gerçek 4: Her şey tahsisatlarla ilgili</span><span class="sxs-lookup"><span data-stu-id="1e79d-143">Fact 4: It’s all about allocations</span></span>  
 <span data-ttu-id="1e79d-144">Duyarlı bir .NET Framework uygulaması oluşturmanın, kabarcık sıralaması yerine hızlı sıralama kullanmak gibi algoritmalarla ilgili olduğunu düşünebilirsiniz, ancak durum böyle değildir.</span><span class="sxs-lookup"><span data-stu-id="1e79d-144">You might think that building a responsive .NET Framework app is all about algorithms, such as using quick sort instead of bubble sort, but that's not the case.</span></span> <span data-ttu-id="1e79d-145">Duyarlı bir uygulama oluşturmanın en büyük nedeni, özellikle uygulamanız çok büyükse veya büyük miktarda veri işlediğinde bellek ayırmaktır.</span><span class="sxs-lookup"><span data-stu-id="1e79d-145">The biggest factor in building a responsive app is allocating memory, especially when your app is very large or processes large amounts of data.</span></span>
  
 <span data-ttu-id="1e79d-146">Yeni derleyici API'leri ile duyarlı IDE deneyimleri oluşturmak için yapılan çalışmaların neredeyse tamamı, tahsisatlardan kaçınmayı ve önbelleğe alma stratejilerini yönetmeyi içeriyordu.</span><span class="sxs-lookup"><span data-stu-id="1e79d-146">Almost all the work to build responsive IDE experiences with the new compiler APIs involved avoiding allocations and managing caching strategies.</span></span> <span data-ttu-id="1e79d-147">PerfView izleri, yeni C# ve Visual Basic derleyicilerinin performansının nadiren CPU'ya bağlı olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="1e79d-147">PerfView traces show that the performance of the new C# and Visual Basic compilers is rarely CPU bound.</span></span> <span data-ttu-id="1e79d-148">Derleyiciler yüz binlerce veya milyonlarca kod satırı okurken, meta verileri okurken veya oluşturulan kodu yayırken G/Ç'ye bağlı olabilir.</span><span class="sxs-lookup"><span data-stu-id="1e79d-148">The compilers can be I/O bound when reading hundreds of thousands or millions of lines of code, reading metadata, or emitting generated code.</span></span> <span data-ttu-id="1e79d-149">UI iş parçacığı gecikmeleri neredeyse tüm çöp toplama nedeniyle.</span><span class="sxs-lookup"><span data-stu-id="1e79d-149">The UI thread delays are nearly all due to garbage collection.</span></span> <span data-ttu-id="1e79d-150">.NET Framework GC performans için son derece ayarlanmıştır ve uygulama kodu yürütülürken çalışmalarının çoğunu aynı anda yapar.</span><span class="sxs-lookup"><span data-stu-id="1e79d-150">The .NET Framework GC is highly tuned for performance and does much of its work concurrently while app code executes.</span></span> <span data-ttu-id="1e79d-151">Ancak, tek bir ayırma tüm iş parçacığı durdurarak pahalı bir [gen2](../../standard/garbage-collection/fundamentals.md) toplama tetikleyebilir.</span><span class="sxs-lookup"><span data-stu-id="1e79d-151">However, a single allocation can trigger an expensive [gen2](../../standard/garbage-collection/fundamentals.md) collection, stopping all threads.</span></span>
  
## <a name="common-allocations-and-examples"></a><span data-ttu-id="1e79d-152">Ortak ayırmalar ve örnekler</span><span class="sxs-lookup"><span data-stu-id="1e79d-152">Common allocations and examples</span></span>  
 <span data-ttu-id="1e79d-153">Bu bölümdeki örnek ifadeler, küçük görünen gizli ayırmalara sahiptir.</span><span class="sxs-lookup"><span data-stu-id="1e79d-153">The example expressions in this section have hidden allocations that appear small.</span></span> <span data-ttu-id="1e79d-154">Ancak, büyük bir uygulama ifadeleri yeterince kez yürütürse, yüzlerce megabayt, hatta gigabayt, ayırmalara neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="1e79d-154">However, if a large app executes the expressions enough times, they can causes hundreds of megabytes, even gigabytes, of allocations.</span></span> <span data-ttu-id="1e79d-155">Örneğin, bir geliştiricinin düzenleyicideki yazısını simüle eden bir dakikalık testler gigabaytlarzaman bellek ayırmış ve performans ekibinin senaryo yazmaya odaklanmasına yol açmıştır.</span><span class="sxs-lookup"><span data-stu-id="1e79d-155">For example, one-minute tests that simulated a developer’s typing in the editor allocated gigabytes of memory and led the performance team to focus on typing scenarios.</span></span>
  
### <a name="boxing"></a><span data-ttu-id="1e79d-156">Kutulama</span><span class="sxs-lookup"><span data-stu-id="1e79d-156">Boxing</span></span>  
 <span data-ttu-id="1e79d-157">[Kutulama,](../../csharp/programming-guide/types/boxing-and-unboxing.md) normalde yığında veya veri yapılarında yaşayan değer türleri bir nesneye sarılınca oluşur.</span><span class="sxs-lookup"><span data-stu-id="1e79d-157">[Boxing](../../csharp/programming-guide/types/boxing-and-unboxing.md) occurs when value types that normally live on the stack or in data structures are wrapped in an object.</span></span> <span data-ttu-id="1e79d-158">Diğer bir tarihte, verileri tutmak için bir nesne ayırırsınız ve ardından bir işaretçiyi nesneye döndürebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1e79d-158">That is, you allocate an object to hold the data, and then return a pointer to the object.</span></span> <span data-ttu-id="1e79d-159">.NET Framework bazen bir yöntemin imzası veya depolama konumunun türü nedeniyle değerleri kutular.</span><span class="sxs-lookup"><span data-stu-id="1e79d-159">The .NET Framework sometimes boxes values due to the signature of a method or the type of a storage location.</span></span> <span data-ttu-id="1e79d-160">Bir nesnedeki değer türünü sarma, bellek ayırmaya neden olur.</span><span class="sxs-lookup"><span data-stu-id="1e79d-160">Wrapping a value type in an object causes memory allocation.</span></span> <span data-ttu-id="1e79d-161">Birçok boks işlemi, uygulamanıza megabaytlarca veya gigabaytlık tahsisatlar sağlayabilir, bu da uygulamanızın daha fazla GC'ye neden olacağı anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="1e79d-161">Many boxing operations can contribute megabytes or gigabytes of allocations to your app, which means that your app will cause more GCs.</span></span> <span data-ttu-id="1e79d-162">.NET Framework ve dil derleyicileri mümkün olduğunda kutulamaktan kaçınır, ancak bazen en az beklediğiniz anda olur.</span><span class="sxs-lookup"><span data-stu-id="1e79d-162">The .NET Framework and the language compilers avoid boxing when possible, but sometimes it happens when you least expect it.</span></span>
  
 <span data-ttu-id="1e79d-163">PerfView'da boksu görmek için bir izleme açın ve uygulamanızın işlem adı altında GC Heap Alloc Yığınları'na bakın (unutmayın, tüm süreçler hakkında PerfView raporları).</span><span class="sxs-lookup"><span data-stu-id="1e79d-163">To see boxing in PerfView, open a trace and look at GC Heap Alloc Stacks under your app’s process name (remember, PerfView reports on all processes).</span></span> <span data-ttu-id="1e79d-164">Tahsisatlar gibi <xref:System.Int32?displayProperty=nameWithType> <xref:System.Char?displayProperty=nameWithType> ve altında türleri görüyorsanız, değer türlerini kutulup alasınız.</span><span class="sxs-lookup"><span data-stu-id="1e79d-164">If you see types like <xref:System.Int32?displayProperty=nameWithType> and <xref:System.Char?displayProperty=nameWithType> under allocations, you are boxing value types.</span></span> <span data-ttu-id="1e79d-165">Bu türlerden birini seçmek, kutulu oldukları yığınları ve işlevleri gösterir.</span><span class="sxs-lookup"><span data-stu-id="1e79d-165">Choosing one of these types will show the stacks and functions in which they are boxed.</span></span>
  
 <span data-ttu-id="1e79d-166">**Örnek 1: dize yöntemleri ve değer türü bağımsız değişkenleri**</span><span class="sxs-lookup"><span data-stu-id="1e79d-166">**Example 1: string methods and value type arguments**</span></span>  
  
 <span data-ttu-id="1e79d-167">Bu örnek kod, gereksiz ve aşırı kutulama yı göstermektedir:</span><span class="sxs-lookup"><span data-stu-id="1e79d-167">This sample code illustrates potentially unnecessary and excessive boxing:</span></span>  
  
```csharp  
public class Logger  
{  
    public static void WriteLine(string s) { /*...*/ }  
}  
  
public class BoxingExample  
{  
    public void Log(int id, int size)  
    {  
        var s = string.Format("{0}:{1}", id, size);  
        Logger.WriteLine(s);  
    }  
}  
```  
  
 <span data-ttu-id="1e79d-168">Bu kod günlük işlevselliği sağlar, `Log` böylece bir uygulama işlevi sık sık, belki de milyonlarca kez arayabilir.</span><span class="sxs-lookup"><span data-stu-id="1e79d-168">This code provides logging functionality, so an app may call the `Log` function frequently, maybe millions of times.</span></span> <span data-ttu-id="1e79d-169">Sorun şu ki, `string.Format` aşırı yükleme <xref:System.String.Format%28System.String%2CSystem.Object%2CSystem.Object%29> için giderilmesi için çağrı.</span><span class="sxs-lookup"><span data-stu-id="1e79d-169">The problem is that the call to `string.Format` resolves to the <xref:System.String.Format%28System.String%2CSystem.Object%2CSystem.Object%29> overload.</span></span>
  
 <span data-ttu-id="1e79d-170">Bu aşırı yük, `int` .NET Framework'ün değerleri nesnelere kutulayarak bu yöntem çağrısına geçirmesini gerektirir.</span><span class="sxs-lookup"><span data-stu-id="1e79d-170">This overload requires the .NET Framework to box the `int` values into objects to pass them to this method call.</span></span> <span data-ttu-id="1e79d-171">Kısmi düzeltme, tüm `id.ToString()` `size.ToString()` dizeleri (nesne olan) `string.Format` aramaya çağırmak ve geçirmektir.</span><span class="sxs-lookup"><span data-stu-id="1e79d-171">A partial fix is to call `id.ToString()` and `size.ToString()` and pass all strings (which are objects) to the `string.Format` call.</span></span> <span data-ttu-id="1e79d-172">Arama `ToString()` bir dize ayırır, ancak bu `string.Format`ayırma zaten içinde olur.</span><span class="sxs-lookup"><span data-stu-id="1e79d-172">Calling `ToString()` does allocate a string, but that allocation will happen anyway inside `string.Format`.</span></span>
  
 <span data-ttu-id="1e79d-173">Bu temel çağrının `string.Format` sadece dize biraraya getirin, bu nedenle bu kodu yazabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="1e79d-173">You might consider that this basic call to `string.Format` is just string concatenation, so you might write this code instead:</span></span>  
  
```csharp  
var s = id.ToString() + ':' + size.ToString();  
```  
  
 <span data-ttu-id="1e79d-174">Ancak, bu kod satırı bir kutulama ayırma <xref:System.String.Concat%28System.Object%2CSystem.Object%2CSystem.Object%29>sı derlediği için.</span><span class="sxs-lookup"><span data-stu-id="1e79d-174">However, that line of code introduces a boxing allocation because it compiles to <xref:System.String.Concat%28System.Object%2CSystem.Object%2CSystem.Object%29>.</span></span> <span data-ttu-id="1e79d-175">.NET Framework, çağrılması için karakter in ivel kutusunu kutulamalıdır`Concat`</span><span class="sxs-lookup"><span data-stu-id="1e79d-175">The .NET Framework must box the character literal to invoke `Concat`</span></span>  
  
 <span data-ttu-id="1e79d-176">**Örneğin 1'i düzeltme**</span><span class="sxs-lookup"><span data-stu-id="1e79d-176">**Fix for example 1**</span></span>  
  
 <span data-ttu-id="1e79d-177">Tam düzeltme basittir.</span><span class="sxs-lookup"><span data-stu-id="1e79d-177">The complete fix is simple.</span></span> <span data-ttu-id="1e79d-178">Dizeleri zaten nesneler olduğundan hiçbir kutulama tahakkuk eden bir dize literal ile karakter literal değiştirin:</span><span class="sxs-lookup"><span data-stu-id="1e79d-178">Just replace the character literal with a string literal, which incurs no boxing because strings are already objects:</span></span>  
  
```csharp  
var s = id.ToString() + ":" + size.ToString();  
```  
  
 <span data-ttu-id="1e79d-179">**Örnek 2: enum boks**</span><span class="sxs-lookup"><span data-stu-id="1e79d-179">**Example 2: enum boxing**</span></span>  
  
 <span data-ttu-id="1e79d-180">Bu örnek, özellikle sözlük arama işlemlerinde numaralandırma türlerinin sık kullanımı nedeniyle yeni C# ve Visual Basic derleyicilerinde büyük miktarda ayırmadan sorumluydu.</span><span class="sxs-lookup"><span data-stu-id="1e79d-180">This example was responsible for a huge amount of allocation in the new C# and Visual Basic compilers due to frequent use of enumeration types, especially in dictionary lookup operations.</span></span>
  
```csharp  
public enum Color  
{  
    Red, Green, Blue  
}  
  
public class BoxingExample  
{  
    private string name;  
    private Color color;  
    public override int GetHashCode()  
    {  
        return name.GetHashCode() ^ color.GetHashCode();  
    }  
}  
```  
  
 <span data-ttu-id="1e79d-181">Bu sorun çok ince.</span><span class="sxs-lookup"><span data-stu-id="1e79d-181">This problem is very subtle.</span></span> <span data-ttu-id="1e79d-182">PerfView bunu kutulama olarak <xref:System.Enum.GetHashCode> bildirir, çünkü yöntem, uygulama nedenleriyle numaralandırma türünün temel temsilini kutular.</span><span class="sxs-lookup"><span data-stu-id="1e79d-182">PerfView would report this as <xref:System.Enum.GetHashCode> boxing because the method boxes the underlying representation of the enumeration type, for implementation reasons.</span></span> <span data-ttu-id="1e79d-183">PerfView'e yakından bakarsanız, her arama için iki kutulama <xref:System.Enum.GetHashCode>ayırması görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1e79d-183">If you look closely in PerfView, you may see two boxing allocations for each call to <xref:System.Enum.GetHashCode>.</span></span> <span data-ttu-id="1e79d-184">Derleyici birini ekler, .NET Framework diğerini ekler.</span><span class="sxs-lookup"><span data-stu-id="1e79d-184">The compiler inserts one, and the .NET Framework inserts the other.</span></span>
  
 <span data-ttu-id="1e79d-185">**Örneğin 2'yi düzeltme**</span><span class="sxs-lookup"><span data-stu-id="1e79d-185">**Fix for example 2**</span></span>  
  
 <span data-ttu-id="1e79d-186">Aşağıdakileri aramadan <xref:System.Enum.GetHashCode>önce altta yatan temsile döküm yaparak her iki ayırmayı da kolayca önleyebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="1e79d-186">You can easily avoid both allocations by casting to the underlying representation before calling <xref:System.Enum.GetHashCode>:</span></span>  
  
```csharp  
((int)color).GetHashCode()  
```  
  
 <span data-ttu-id="1e79d-187">Numaralandırma türlerinde bir diğer yaygın boks <xref:System.Enum.HasFlag%28System.Enum%29?displayProperty=nameWithType> kaynağı da yöntemdir.</span><span class="sxs-lookup"><span data-stu-id="1e79d-187">Another common source of boxing on enumeration types is the <xref:System.Enum.HasFlag%28System.Enum%29?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="1e79d-188">Geçirilen <xref:System.Enum.HasFlag%28System.Enum%29> argüman kutulanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="1e79d-188">The argument passed to <xref:System.Enum.HasFlag%28System.Enum%29> has to be boxed.</span></span> <span data-ttu-id="1e79d-189">Çoğu durumda, çağrıları bitwise testi <xref:System.Enum.HasFlag%28System.Enum%29?displayProperty=nameWithType> ile değiştirmek daha basit ve tahsisat gerektirmez.</span><span class="sxs-lookup"><span data-stu-id="1e79d-189">In most cases, replacing calls to <xref:System.Enum.HasFlag%28System.Enum%29?displayProperty=nameWithType> with a bitwise test is simpler and allocation-free.</span></span>
  
 <span data-ttu-id="1e79d-190">İlk performans gerçeğini aklınızda tutun (diğer bir deyişle, zamanından önce optimize etmeyin) ve tüm kodunuzu bu şekilde yeniden yazmaya başlamayın.</span><span class="sxs-lookup"><span data-stu-id="1e79d-190">Keep the first performance fact in mind (that is, don’t prematurely optimize) and don’t start rewriting all your code in this way.</span></span> <span data-ttu-id="1e79d-191">Bu boks maliyetlerine dikkat edin, ancak kodunuzu yalnızca uygulamanızın profilini çıkardıktan ve önemli noktaları bulduktan sonra değiştirin.</span><span class="sxs-lookup"><span data-stu-id="1e79d-191">Be aware of these boxing costs, but change your code only after profiling your app and finding the hot spots.</span></span>
  
### <a name="strings"></a><span data-ttu-id="1e79d-192">Dizeler</span><span class="sxs-lookup"><span data-stu-id="1e79d-192">Strings</span></span>  
 <span data-ttu-id="1e79d-193">Dize manipülasyonları tahsisatların en büyük suçlularından bazılarıdır ve genellikle perfView'da ilk beş ayırmada ortaya çıkar.</span><span class="sxs-lookup"><span data-stu-id="1e79d-193">String manipulations are some of the biggest culprits for allocations, and they often show up in PerfView in the top five allocations.</span></span> <span data-ttu-id="1e79d-194">Programlar serileştirme, JSON ve REST API'leri için dizeleri kullanır.</span><span class="sxs-lookup"><span data-stu-id="1e79d-194">Programs use strings for serialization, JSON, and REST APIs.</span></span> <span data-ttu-id="1e79d-195">Dizileri, numaralandırma türlerini kullanamadığınızda sistemlerle etkileşim için programlı sabitler olarak kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1e79d-195">You can use strings as programmatic constants for interoperating with systems when you can’t use enumeration types.</span></span> <span data-ttu-id="1e79d-196">Profil oluşturmanız dizelerin performansı son derece etkilediğini <xref:System.String> gösterdiğinde, <xref:System.String.Format%2A> <xref:System.String.Concat%2A>, <xref:System.String.Split%2A> <xref:System.String.Join%2A>, <xref:System.String.Substring%2A>, , gibi yöntemlere yapılan çağrıları arayın.</span><span class="sxs-lookup"><span data-stu-id="1e79d-196">When your profiling shows that strings are highly affecting performance, look for calls to <xref:System.String> methods such as <xref:System.String.Format%2A>, <xref:System.String.Concat%2A>, <xref:System.String.Split%2A>, <xref:System.String.Join%2A>, <xref:System.String.Substring%2A>, and so on.</span></span> <span data-ttu-id="1e79d-197">Birçok <xref:System.Text.StringBuilder> parçadan bir dize oluşturma maliyetini önlemek için kullanarak <xref:System.Text.StringBuilder> yardımcı olur, ancak nesne tahsis bile yönetmek için gereken bir darboğaz haline gelebilir.</span><span class="sxs-lookup"><span data-stu-id="1e79d-197">Using <xref:System.Text.StringBuilder> to avoid the cost of creating one string from many pieces helps, but even allocating the <xref:System.Text.StringBuilder> object might become a bottleneck that you need to manage.</span></span>
  
 <span data-ttu-id="1e79d-198">**Örnek 3: dize işlemleri**</span><span class="sxs-lookup"><span data-stu-id="1e79d-198">**Example 3: string operations**</span></span>  
  
 <span data-ttu-id="1e79d-199">C# derleyicisi biçimlendirilmiş bir XML doc yorum metnini yazan bu kodvardı:</span><span class="sxs-lookup"><span data-stu-id="1e79d-199">The C# compiler had this code that writes the text of a formatted XML doc comment:</span></span>  
  
```csharp  
public void WriteFormattedDocComment(string text)  
{  
    string[] lines = text.Split(new[] { "\r\n", "\r", "\n" },  
                                StringSplitOptions.None);  
    int numLines = lines.Length;  
    bool skipSpace = true;  
    if (lines[0].TrimStart().StartsWith("///"))  
    {  
        for (int i = 0; i < numLines; i++)  
        {  
            string trimmed = lines[i].TrimStart();  
            if (trimmed.Length < 4 || !char.IsWhiteSpace(trimmed[3]))  
            {  
                skipSpace = false;  
                break;  
            }  
        }  
        int substringStart = skipSpace ? 4 : 3;  
        for (int i = 0; i < numLines; i++)  
            WriteLine(lines[i].TrimStart().Substring(substringStart));  
    }  
    else { /* ... */ }  
```  
  
 <span data-ttu-id="1e79d-200">Bu kodun çok fazla dize manipülasyonu yaptığını görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1e79d-200">You can see that this code does a lot of string manipulation.</span></span> <span data-ttu-id="1e79d-201">Kod, satırları ayrı dizeleri bölmek, beyaz alanı kırpmak, bağımsız `text` değişkenin XML belge yorumu olup olmadığını denetlemek ve satırlardan alt dizeleri ayıklamak için kitaplık yöntemleri kullanır.</span><span class="sxs-lookup"><span data-stu-id="1e79d-201">The code uses library methods to split lines into separate strings, to trim white space, to check whether the argument `text` is an XML documentation comment, and to extract substrings from lines.</span></span>
  
 <span data-ttu-id="1e79d-202">İçerideki `WriteFormattedDocComment`ilk satırda, `text.Split` çağrı, her çağrıldığında bağımsız değişken olarak yeni bir üç öğeli dizi ayırır.</span><span class="sxs-lookup"><span data-stu-id="1e79d-202">On the first line inside `WriteFormattedDocComment`, the `text.Split` call allocates a new three-element array as the argument every time it’s called.</span></span> <span data-ttu-id="1e79d-203">Derleyici, bu diziyi her seferinde ayırmak için kod yontmak zorundadır.</span><span class="sxs-lookup"><span data-stu-id="1e79d-203">The compiler has to emit code to allocate this array each time.</span></span> <span data-ttu-id="1e79d-204">Bunun nedeni, derleyicinin diziyi <xref:System.String.Split%2A> dizinin başka bir kod tarafından değiştirilebileceği bir yerde depolayıp depolar, bu da daha sonraki çağrıları etkileyip etkilemediğini bilmiyor `WriteFormattedDocComment`olmasıdır.</span><span class="sxs-lookup"><span data-stu-id="1e79d-204">That’s because the compiler doesn’t know if <xref:System.String.Split%2A> stores the array somewhere where the array might be modified by other code, which would affect later calls to `WriteFormattedDocComment`.</span></span> <span data-ttu-id="1e79d-205">Çağrı <xref:System.String.Split%2A> da her satır için bir `text` dize ayırır ve işlemi gerçekleştirmek için diğer bellek ayırır.</span><span class="sxs-lookup"><span data-stu-id="1e79d-205">The call to <xref:System.String.Split%2A> also allocates a string for every line in `text` and allocates other memory to perform the operation.</span></span>
  
 <span data-ttu-id="1e79d-206">`WriteFormattedDocComment`<xref:System.String.TrimStart%2A> yönteme üç çağrı vardır.</span><span class="sxs-lookup"><span data-stu-id="1e79d-206">`WriteFormattedDocComment` has three calls to the <xref:System.String.TrimStart%2A> method.</span></span> <span data-ttu-id="1e79d-207">İki, çalışmayı ve ayırmaları yineleyen iç döngülerdedir.</span><span class="sxs-lookup"><span data-stu-id="1e79d-207">Two are in inner loops that duplicate work and allocations.</span></span> <span data-ttu-id="1e79d-208">Daha da kötüsü, <xref:System.String.TrimStart%2A> hiçbir bağımsız değişken ile yöntem arama `params` dize sonucu ek olarak boş bir dizi (parametre için) ayırır.</span><span class="sxs-lookup"><span data-stu-id="1e79d-208">To make matters worse, calling the <xref:System.String.TrimStart%2A> method with no arguments allocates an empty array (for the `params` parameter) in addition to the string result.</span></span>
  
 <span data-ttu-id="1e79d-209">Son olarak, genellikle yeni <xref:System.String.Substring%2A> bir dize ayıran yönteme bir çağrı vardır.</span><span class="sxs-lookup"><span data-stu-id="1e79d-209">Lastly, there is a call to the <xref:System.String.Substring%2A> method, which usually allocates a new string.</span></span>
  
 <span data-ttu-id="1e79d-210">**Örneğin 3'e göre düzeltme**</span><span class="sxs-lookup"><span data-stu-id="1e79d-210">**Fix for example 3**</span></span>  
  
 <span data-ttu-id="1e79d-211">Önceki örneklerin aksine, küçük düzeltmeler bu ayırmaları düzeltemez.</span><span class="sxs-lookup"><span data-stu-id="1e79d-211">Unlike the earlier examples, small edits cannot fix these allocations.</span></span> <span data-ttu-id="1e79d-212">Geri çekilip, soruna bakmalı ve farklı bir yaklaşım sergilemelisin.</span><span class="sxs-lookup"><span data-stu-id="1e79d-212">You need to step back, look at the problem, and approach it differently.</span></span> <span data-ttu-id="1e79d-213">Örneğin, bağımsız değişkenin yöntemin `WriteFormattedDocComment()` ihtiyaç duyduğu tüm bilgilere sahip bir dize olduğunu fark edeceksiniz, böylece kod çok sayıda kısmi dize ayırmak yerine daha fazla dizin oluşturma yapabilir.</span><span class="sxs-lookup"><span data-stu-id="1e79d-213">For example, you'll notice that the argument to `WriteFormattedDocComment()` is a string that has all the information that the method needs, so the code could do more indexing instead of allocating many partial strings.</span></span>
  
 <span data-ttu-id="1e79d-214">Derleyicinin performans ekibi tüm bu ayırmaları şu gibi kodla ele almıştır:</span><span class="sxs-lookup"><span data-stu-id="1e79d-214">The compiler’s performance team tackled all these allocations with code like this:</span></span>  
  
```csharp  
private int IndexOfFirstNonWhiteSpaceChar(string text, int start) {  
    while (start < text.Length && char.IsWhiteSpace(text[start])) start++;  
    return start;  
}  
  
private bool TrimmedStringStartsWith(string text, int start, string prefix) {  
    start = IndexOfFirstNonWhiteSpaceChar(text, start);  
    int len = text.Length - start;  
    if (len < prefix.Length) return false;  
    for (int i = 0; i < len; i++)  
    {  
        if (prefix[i] != text[start + i]) return false;  
    }  
    return true;  
}  
  
// etc...
```  
  
 <span data-ttu-id="1e79d-215">Bir dizi, `WriteFormattedDocComment()` birkaç alt dizeleri ve boş `params` bir dizi ile birlikte kesilmiş bir alt dize tahsis ilk sürümü.</span><span class="sxs-lookup"><span data-stu-id="1e79d-215">The first version of `WriteFormattedDocComment()` allocated an array, several substrings, and a trimmed substring along with an empty `params` array.</span></span> <span data-ttu-id="1e79d-216">Ayrıca "/"'' diye de kontrol edildi.</span><span class="sxs-lookup"><span data-stu-id="1e79d-216">It also checked for "///".</span></span> <span data-ttu-id="1e79d-217">Gözden geçirilen kod yalnızca dizine ayırma kullanır ve hiçbir şey ayırmaz.</span><span class="sxs-lookup"><span data-stu-id="1e79d-217">The revised code uses only indexing and allocates nothing.</span></span> <span data-ttu-id="1e79d-218">Beyaz boşluk olmayan ilk karakteri bulur ve ardından dize "//" ile başlayıp başlamadığını görmek için karakteri karaktere göre denetler.</span><span class="sxs-lookup"><span data-stu-id="1e79d-218">It finds the first character that is not white space, and then checks character by character to see if the string starts with "///".</span></span> <span data-ttu-id="1e79d-219">Yeni kod, `IndexOfFirstNonWhiteSpaceChar` beyaz <xref:System.String.TrimStart%2A> olmayan bir alanın oluştuğu ilk dizini (belirli bir başlangıç dizininden sonra) döndürmek yerine kullanır.</span><span class="sxs-lookup"><span data-stu-id="1e79d-219">The new code uses `IndexOfFirstNonWhiteSpaceChar` instead of <xref:System.String.TrimStart%2A> to return the first index (after a specified start index) where a non-white-space character occurs.</span></span> <span data-ttu-id="1e79d-220">Düzeltme tamamlanmadı, ancak tam bir çözüm için benzer düzeltmeleri nasıl uygulayacağınızı görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1e79d-220">The fix is not complete, but you can see how to apply similar fixes for a complete solution.</span></span> <span data-ttu-id="1e79d-221">Bu yaklaşımı kod boyunca uygulayarak, 'deki `WriteFormattedDocComment()`tüm ayırmaları kaldırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1e79d-221">By applying this approach throughout the code, you can remove all allocations in `WriteFormattedDocComment()`.</span></span>
  
 <span data-ttu-id="1e79d-222">**Örnek 4: StringBuilder**</span><span class="sxs-lookup"><span data-stu-id="1e79d-222">**Example 4: StringBuilder**</span></span>  
  
 <span data-ttu-id="1e79d-223">Bu örnekte <xref:System.Text.StringBuilder> bir nesne kullanır.</span><span class="sxs-lookup"><span data-stu-id="1e79d-223">This example uses a <xref:System.Text.StringBuilder> object.</span></span> <span data-ttu-id="1e79d-224">Aşağıdaki işlev genel türleri için tam bir tür adı oluşturur:</span><span class="sxs-lookup"><span data-stu-id="1e79d-224">The following function generates a full type name for generic types:</span></span>  
  
```csharp  
public class Example  
{  
    // Constructs a name like "SomeType<T1, T2, T3>"  
    public string GenerateFullTypeName(string name, int arity)  
    {  
        StringBuilder sb = new StringBuilder();  
  
        sb.Append(name);  
        if (arity != 0)  
        {  
            sb.Append("<");  
            for (int i = 1; i < arity; i++)  
            {  
                sb.Append("T"); sb.Append(i.ToString()); sb.Append(", ");  
            }  
            sb.Append("T"); sb.Append(i.ToString()); sb.Append(">");  
        }  
  
        return sb.ToString();  
    }  
}  
```  
  
 <span data-ttu-id="1e79d-225">Odak yeni bir <xref:System.Text.StringBuilder> örnek oluşturur satırüzerindedir.</span><span class="sxs-lookup"><span data-stu-id="1e79d-225">The focus is on the line that creates a new <xref:System.Text.StringBuilder> instance.</span></span> <span data-ttu-id="1e79d-226">Kod, <xref:System.Text.StringBuilder> uygulama içinde `sb.ToString()` bir ayırma ve iç ayırmalara neden olur, ancak dize sonucunu istiyorsanız bu ayırmaları denetleyemezsiniz.</span><span class="sxs-lookup"><span data-stu-id="1e79d-226">The code causes an allocation for `sb.ToString()` and internal allocations within the <xref:System.Text.StringBuilder> implementation, but you cannot control those allocations if you want the string result.</span></span>
  
 <span data-ttu-id="1e79d-227">**Örneğin 4'e göre düzeltme**</span><span class="sxs-lookup"><span data-stu-id="1e79d-227">**Fix for example 4**</span></span>  
  
 <span data-ttu-id="1e79d-228">Nesne ayırmayı `StringBuilder` düzeltmek için nesneyi önbelleğe edin.</span><span class="sxs-lookup"><span data-stu-id="1e79d-228">To fix the `StringBuilder` object allocation, cache the  object.</span></span> <span data-ttu-id="1e79d-229">Çöpe atılabilecek tek bir örneği önbelleğe almak bile performansı önemli ölçüde artırabilir.</span><span class="sxs-lookup"><span data-stu-id="1e79d-229">Even caching a single instance that might get thrown away can improve performance significantly.</span></span> <span data-ttu-id="1e79d-230">Bu, işlevin yeni ilk ve son satırlar dışında tüm kodu atlayarak yeni uygulamasıdır:</span><span class="sxs-lookup"><span data-stu-id="1e79d-230">This is the function’s new implementation, omitting all the code except for the new first and last lines:</span></span>  
  
```csharp  
// Constructs a name like "MyType<T1, T2, T3>"  
public string GenerateFullTypeName(string name, int arity)  
{  
    StringBuilder sb = AcquireBuilder();  
    /* Use sb as before */  
    return GetStringAndReleaseBuilder(sb);  
}  
```  
  
 <span data-ttu-id="1e79d-231">Önemli parçalar yeni `AcquireBuilder()` ve `GetStringAndReleaseBuilder()` fonksiyonlar şunlardır:</span><span class="sxs-lookup"><span data-stu-id="1e79d-231">The key parts are the new `AcquireBuilder()` and `GetStringAndReleaseBuilder()` functions:</span></span>  
  
```csharp  
[ThreadStatic]  
private static StringBuilder cachedStringBuilder;  
  
private static StringBuilder AcquireBuilder()  
{  
    StringBuilder result = cachedStringBuilder;  
    if (result == null)  
    {  
        return new StringBuilder();  
    }  
    result.Clear();  
    cachedStringBuilder = null;  
    return result;  
}  
  
private static string GetStringAndReleaseBuilder(StringBuilder sb)  
{  
    string result = sb.ToString();  
    cachedStringBuilder = sb;  
    return result;  
}  
```  
  
 <span data-ttu-id="1e79d-232">Yeni derleyiciler iş parçacığı kullandığından, bu uygulamalar bir<xref:System.ThreadStaticAttribute> iş parçacığı statik <xref:System.Text.StringBuilder>alanı (öznitelik) önbellek için kullanır ve büyük olasılıkla `ThreadStatic` bildirimi bırakabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1e79d-232">Because the new compilers use threading, these implementations use a thread-static field (<xref:System.ThreadStaticAttribute> attribute) to cache the <xref:System.Text.StringBuilder>, and you likely can forgo the `ThreadStatic` declaration.</span></span> <span data-ttu-id="1e79d-233">İş parçacığı statik alan, bu kodu çalıştıran her iş parçacığı için benzersiz bir değer tutar.</span><span class="sxs-lookup"><span data-stu-id="1e79d-233">The thread-static field holds a unique value for each thread that executes this code.</span></span>
  
 <span data-ttu-id="1e79d-234">`AcquireBuilder()`önbelleğe alınan <xref:System.Text.StringBuilder> örneği, temizledikten ve alanı veya önbelleği null'a ayarladıktan sonra döndürür.</span><span class="sxs-lookup"><span data-stu-id="1e79d-234">`AcquireBuilder()` returns the cached <xref:System.Text.StringBuilder> instance if there is one, after clearing it and setting the field or cache to null.</span></span> <span data-ttu-id="1e79d-235">Aksi `AcquireBuilder()` takdirde, yeni bir örnek oluşturur ve alanı veya önbelleği null olarak bırakarak döndürür.</span><span class="sxs-lookup"><span data-stu-id="1e79d-235">Otherwise, `AcquireBuilder()` creates a new instance and returns it, leaving the field or cache set to null.</span></span>
  
 <span data-ttu-id="1e79d-236">İşi <xref:System.Text.StringBuilder> bittiğinde, dize `GetStringAndReleaseBuilder()` sonucunu almak için ararsınız, <xref:System.Text.StringBuilder> örneği alana veya önbelleğe kaydedin ve sonra sonucu döndürün.</span><span class="sxs-lookup"><span data-stu-id="1e79d-236">When you’re done with <xref:System.Text.StringBuilder> , you call `GetStringAndReleaseBuilder()` to get the string result, save the <xref:System.Text.StringBuilder> instance in the field or cache, and then return the result.</span></span> <span data-ttu-id="1e79d-237">Yürütmenin bu kodu yeniden girmesi ve birden <xref:System.Text.StringBuilder> çok nesne oluşturması mümkündür (ancak bu nadiren olur).</span><span class="sxs-lookup"><span data-stu-id="1e79d-237">It is possible for execution to re-enter this code and to create multiple <xref:System.Text.StringBuilder> objects (although that rarely happens).</span></span> <span data-ttu-id="1e79d-238">Kod, daha sonra kullanılmak <xref:System.Text.StringBuilder> üzere yalnızca son yayımlanan örneği kaydeder.</span><span class="sxs-lookup"><span data-stu-id="1e79d-238">The code saves only the last released <xref:System.Text.StringBuilder> instance for later use.</span></span> <span data-ttu-id="1e79d-239">Bu basit önbelleğe alma stratejisi, yeni derleyicilerde ayırmaları önemli ölçüde azalttı.</span><span class="sxs-lookup"><span data-stu-id="1e79d-239">This simple caching strategy significantly reduced allocations in the new compilers.</span></span> <span data-ttu-id="1e79d-240">.NET Framework ve MSBuild 'in ("MSBuild") parçaları performansı artırmak için benzer bir teknik kullanır.</span><span class="sxs-lookup"><span data-stu-id="1e79d-240">Parts of the .NET Framework and MSBuild ("MSBuild") use a similar technique to improve performance.</span></span>
  
 <span data-ttu-id="1e79d-241">Bu basit önbelleğe alma stratejisi, boyut kapağına sahip olduğundan iyi önbellek tasarımına bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="1e79d-241">This simple caching strategy adheres to good cache design because it has a size cap.</span></span> <span data-ttu-id="1e79d-242">Ancak, şimdi orijinalinden daha fazla kod var, bu da daha fazla bakım maliyeti anlamına geliyor.</span><span class="sxs-lookup"><span data-stu-id="1e79d-242">However, there is more code now than in the original, which means more maintenance costs.</span></span> <span data-ttu-id="1e79d-243">Önbelleğe alma stratejisini yalnızca bir performans sorunu bulduysanız ve PerfView <xref:System.Text.StringBuilder> ayırmaların önemli bir katkıda bulunduğunu göstermiştir.</span><span class="sxs-lookup"><span data-stu-id="1e79d-243">You should adopt the caching strategy only if you’ve found a performance problem, and PerfView has shown that <xref:System.Text.StringBuilder> allocations are a significant contributor.</span></span>
  
### <a name="linq-and-lambdas"></a><span data-ttu-id="1e79d-244">LINQ ve lambdas</span><span class="sxs-lookup"><span data-stu-id="1e79d-244">LINQ and lambdas</span></span>  
<span data-ttu-id="1e79d-245">Dil-Entegre Sorgu (LINQ), lambda ifadeleri ile birlikte, bir verimlilik özelliği bir örnektir.</span><span class="sxs-lookup"><span data-stu-id="1e79d-245">Language-Integrated Query (LINQ), in conjunction with lambda expressions, is an example of a productivity feature.</span></span> <span data-ttu-id="1e79d-246">Ancak, kullanımı zaman içinde performans üzerinde önemli bir etkiye sahip olabilir ve kodunuzu yeniden yazmanız gerektiğini görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1e79d-246">However, its use may have a significant impact on performance over time, and you might find you need to rewrite your code.</span></span>
  
 <span data-ttu-id="1e79d-247">**Örnek 5: Lambdas, Liste\<T> ve\<Imumerable T>**</span><span class="sxs-lookup"><span data-stu-id="1e79d-247">**Example 5: Lambdas, List\<T>, and IEnumerable\<T>**</span></span>  
  
 <span data-ttu-id="1e79d-248">Bu örnek, derleyicinin modelinde bir ad dizesi verilen bir simge bulmak için [LINQ ve işlevsel stil kodunu](https://docs.microsoft.com/archive/blogs/charlie/anders-hejlsberg-on-linq-and-functional-programming) kullanır:</span><span class="sxs-lookup"><span data-stu-id="1e79d-248">This example uses [LINQ and functional style code](https://docs.microsoft.com/archive/blogs/charlie/anders-hejlsberg-on-linq-and-functional-programming) to find a symbol in the compiler’s model, given a name string:</span></span>  
  
```csharp  
class Symbol {  
    public string Name { get; private set; }  
    /*...*/  
}  
  
class Compiler {  
    private List<Symbol> symbols;  
    public Symbol FindMatchingSymbol(string name)  
    {  
        return symbols.FirstOrDefault(s => s.Name == name);  
    }  
}  
```  
  
 <span data-ttu-id="1e79d-249">Yeni derleyici ve üzerinde yerleşik IDE `FindMatchingSymbol()` deneyimleri çok sık çağrı ve bu işlevin tek kod satırında birkaç gizli ayırmalar vardır.</span><span class="sxs-lookup"><span data-stu-id="1e79d-249">The new compiler and the IDE experiences built on it call `FindMatchingSymbol()` very frequently, and there are several hidden allocations in this function’s single line of code.</span></span> <span data-ttu-id="1e79d-250">Bu ayırmaları incelemek için, önce işlevin tek kod satırını iki satıra bölün:</span><span class="sxs-lookup"><span data-stu-id="1e79d-250">To examine those allocations, first split the function’s single line of code into two lines:</span></span>  
  
```csharp  
Func<Symbol, bool> predicate = s => s.Name == name;  
     return symbols.FirstOrDefault(predicate);  
```  
  
 <span data-ttu-id="1e79d-251">İlk satırda [lambda ifadesi](../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md) `s => s.Name == name` yerel `name` [değişkenin üzerinde kapanır.](https://docs.microsoft.com/archive/blogs/ericlippert/what-are-closures)</span><span class="sxs-lookup"><span data-stu-id="1e79d-251">In the first line, the [lambda expression](../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md) `s => s.Name == name` [closes over](https://docs.microsoft.com/archive/blogs/ericlippert/what-are-closures) the local variable `name`.</span></span> <span data-ttu-id="1e79d-252">Bu, `predicate` bir nesneyi tutan [temsilciye](../../csharp/language-reference/builtin-types/reference-types.md#the-delegate-type) ayırmanın yanı sıra, kodun `name`değerini yakalayan ortamı tutmak için statik bir sınıf ayırdığı anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="1e79d-252">This means that in addition to allocating an object for the [delegate](../../csharp/language-reference/builtin-types/reference-types.md#the-delegate-type) that `predicate` holds, the code allocates a static class to hold the environment that captures the value of `name`.</span></span> <span data-ttu-id="1e79d-253">Derleyici aşağıdaki gibi kod oluşturur:</span><span class="sxs-lookup"><span data-stu-id="1e79d-253">The compiler generates code like the following:</span></span>  
  
```csharp  
// Compiler-generated class to hold environment state for lambda  
private class Lambda1Environment  
{  
    public string capturedName;  
    public bool Evaluate(Symbol s)  
    {  
        return s.Name == this.capturedName;  
    }  
}  
  
// Expanded Func<Symbol, bool> predicate = s => s.Name == name;  
Lambda1Environment l = new Lambda1Environment() { capturedName = name };  
var predicate = new Func<Symbol, bool>(l.Evaluate);  
```  
  
 <span data-ttu-id="1e79d-254">İki `new` ayırma (biri çevre sınıfı için, diğeri temsilci için) şimdi açık.</span><span class="sxs-lookup"><span data-stu-id="1e79d-254">The two `new` allocations (one for the environment class and one for the delegate) are explicit now.</span></span>
  
 <span data-ttu-id="1e79d-255">Şimdi çağrıya `FirstOrDefault`bak.</span><span class="sxs-lookup"><span data-stu-id="1e79d-255">Now look at the call to `FirstOrDefault`.</span></span> <span data-ttu-id="1e79d-256"><xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> Türdeki bu uzantı yöntemi de bir ayırmaya neden oluyor.</span><span class="sxs-lookup"><span data-stu-id="1e79d-256">This extension method on the <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> type incurs an allocation too.</span></span> <span data-ttu-id="1e79d-257">Bir `FirstOrDefault` nesneyi <xref:System.Collections.Generic.IEnumerable%601> ilk bağımsız değişkeni olarak aldığından, aramayı aşağıdaki koda genişletebilirsiniz (tartışma için biraz basitleştirilmiş):</span><span class="sxs-lookup"><span data-stu-id="1e79d-257">Because `FirstOrDefault` takes an <xref:System.Collections.Generic.IEnumerable%601> object as its first argument, you can expand the call to the following code (simplified a bit for discussion):</span></span>  
  
```csharp  
// Expanded return symbols.FirstOrDefault(predicate) ...
     IEnumerable<Symbol> enumerable = symbols;  
     IEnumerator<Symbol> enumerator = enumerable.GetEnumerator();  
     while(enumerator.MoveNext())  
     {  
         if (predicate(enumerator.Current))  
             return enumerator.Current;  
     }  
     return default(Symbol);  
```  
  
 <span data-ttu-id="1e79d-258">Değişkenin `symbols` türü <xref:System.Collections.Generic.List%601>vardır.</span><span class="sxs-lookup"><span data-stu-id="1e79d-258">The `symbols` variable has type <xref:System.Collections.Generic.List%601>.</span></span> <span data-ttu-id="1e79d-259">Koleksiyon <xref:System.Collections.Generic.List%601> türü uygular <xref:System.Collections.Generic.IEnumerable%601> ve akıllıca bir<xref:System.Collections.Generic.IEnumerator%601> <xref:System.Collections.Generic.List%601> `struct`ile uygulayan bir bir sayısallaştırıcı (arabirim) tanımlar .</span><span class="sxs-lookup"><span data-stu-id="1e79d-259">The <xref:System.Collections.Generic.List%601> collection type implements <xref:System.Collections.Generic.IEnumerable%601> and cleverly defines an enumerator (<xref:System.Collections.Generic.IEnumerator%601> interface) that <xref:System.Collections.Generic.List%601> implements with a `struct`.</span></span> <span data-ttu-id="1e79d-260">Sınıf yerine bir yapı kullanmak, genellikle çöp toplama performansını etkileyebilecek yığın ayırmalardan kaçınmanız anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="1e79d-260">Using a structure instead of a class means that you usually avoid any heap allocations, which, in turn, can affect garbage collection performance.</span></span> <span data-ttu-id="1e79d-261">Tümumeratörler genellikle çağrı yığınında `foreach` döndürülür gibi enumerator yapısını kullanan dilin döngü ile kullanılır.</span><span class="sxs-lookup"><span data-stu-id="1e79d-261">Enumerators are typically used with the language’s `foreach` loop, which uses the enumerator structure as it is returned on the call stack.</span></span> <span data-ttu-id="1e79d-262">Bir nesneye yer açmak için çağrı yığını işaretçisini artımlı yorum, yığın ayırmanın yaptığı gibi GC'yi etkilemez.</span><span class="sxs-lookup"><span data-stu-id="1e79d-262">Incrementing the call stack pointer to make room for an object does not affect GC the way a heap allocation does.</span></span>
  
 <span data-ttu-id="1e79d-263">Genişletilmiş `FirstOrDefault` arama söz konusu olduğunda, kodun `GetEnumerator()` bir <xref:System.Collections.Generic.IEnumerable%601>.</span><span class="sxs-lookup"><span data-stu-id="1e79d-263">In the case of the expanded `FirstOrDefault` call, the code needs to call `GetEnumerator()` on an <xref:System.Collections.Generic.IEnumerable%601>.</span></span> <span data-ttu-id="1e79d-264">Tür `IEnumerable<Symbol>` `symbols` değişkenine `enumerable` atama, gerçek nesnenin bir <xref:System.Collections.Generic.List%601>.</span><span class="sxs-lookup"><span data-stu-id="1e79d-264">Assigning `symbols` to the `enumerable` variable of type `IEnumerable<Symbol>` loses the information that the actual object is a <xref:System.Collections.Generic.List%601>.</span></span> <span data-ttu-id="1e79d-265">Bu, kod, .NET `enumerable.GetEnumerator()`Framework'ün döndürülen yapıyı `enumerator` değişkene atamak için kutuya takması gerektiği anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="1e79d-265">This means that when the code fetches the enumerator with `enumerable.GetEnumerator()`, the .NET Framework has to box the returned structure to assign it to the `enumerator` variable.</span></span>
  
 <span data-ttu-id="1e79d-266">**Örneğin 5'i düzeltme**</span><span class="sxs-lookup"><span data-stu-id="1e79d-266">**Fix for example 5**</span></span>  
  
 <span data-ttu-id="1e79d-267">Düzeltme, tek kod `FindMatchingSymbol` satırını hala kısa, okunması ve anlaşılması kolay ve bakımı kolay altı kod satırıyla değiştirerek aşağıdaki gibi yeniden yazmaktır:</span><span class="sxs-lookup"><span data-stu-id="1e79d-267">The fix is to rewrite `FindMatchingSymbol` as follows, replacing its single line of code with six lines of code that are still concise, easy to read and understand, and easy to maintain:</span></span>  
  
```csharp  
public Symbol FindMatchingSymbol(string name)  
    {  
        foreach (Symbol s in symbols)  
        {  
            if (s.Name == name)  
                return s;  
        }  
        return null;  
    }  
```  
  
 <span data-ttu-id="1e79d-268">Bu kod LINQ uzantı yöntemleri, lambdas veya numaralandırıcılar kullanmaz ve hiçbir ayırma ya da yok.</span><span class="sxs-lookup"><span data-stu-id="1e79d-268">This code doesn’t use LINQ extension methods, lambdas, or enumerators, and it incurs no allocations.</span></span> <span data-ttu-id="1e79d-269">Derleyici koleksiyonun `symbols` a <xref:System.Collections.Generic.List%601> olduğunu görebildiği ve elde edilen enumerator'u (yapı) kutulamayı önlemek için doğru türe sahip yerel bir değişkene bağlayabildiği için ayırma yoktur.</span><span class="sxs-lookup"><span data-stu-id="1e79d-269">There are no allocations because the compiler can see that the `symbols` collection is a <xref:System.Collections.Generic.List%601> and can bind the resulting enumerator (a structure) to a local variable with the right type to avoid boxing.</span></span> <span data-ttu-id="1e79d-270">Bu işlevin özgün sürümü, C#'ın ifade gücünün ve .NET Framework'ün üretkenliğinin harika bir örneğiydi.</span><span class="sxs-lookup"><span data-stu-id="1e79d-270">The original version of this function was a great example of the expressive power of C# and the productivity of the .NET Framework.</span></span> <span data-ttu-id="1e79d-271">Bu yeni ve daha verimli sürüm korumak için herhangi bir karmaşık kod eklemeden bu nitelikleri korur.</span><span class="sxs-lookup"><span data-stu-id="1e79d-271">This new and more efficient version preserves those qualities without adding any complex code to maintain.</span></span>
  
### <a name="async-method-caching"></a><span data-ttu-id="1e79d-272">Async yöntemi önbelleğe alma</span><span class="sxs-lookup"><span data-stu-id="1e79d-272">Async method caching</span></span>  

<span data-ttu-id="1e79d-273">Sonraki örnek, önbelleğe alınmış sonuçları bir [async](../../csharp/programming-guide/concepts/async/index.md) yönteminde kullanmaya çalıştığınızda sık karşılaşılan bir sorun gösterir.</span><span class="sxs-lookup"><span data-stu-id="1e79d-273">The next example shows a common problem when you try to use cached results in an [async](../../csharp/programming-guide/concepts/async/index.md) method.</span></span>
  
 <span data-ttu-id="1e79d-274">**Örnek 6: async yöntemleri önbelleğe alma**</span><span class="sxs-lookup"><span data-stu-id="1e79d-274">**Example 6: caching in async methods**</span></span>  
  
 <span data-ttu-id="1e79d-275">Visual Studio IDE özellikleri yeni C# ve Visual Basic derleyicileri sık sık sözdizimi ağaçlarını getirir ve derleyiciler Visual Studio'yu duyarlı tutmak için bunu yaparken async kullanır.</span><span class="sxs-lookup"><span data-stu-id="1e79d-275">The Visual Studio IDE features built on the new C# and Visual Basic compilers frequently fetch syntax trees, and the compilers use async when doing so to keep Visual Studio responsive.</span></span> <span data-ttu-id="1e79d-276">Sözdizimi ağacı almak için yazabileceğiniz kodun ilk sürümü aşağıda veda edebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="1e79d-276">Here’s the first version of the code you might write to get a syntax tree:</span></span>  
  
```csharp  
class SyntaxTree { /*...*/ }  
  
class Parser { /*...*/  
    public SyntaxTree Syntax { get; }  
    public Task ParseSourceCode() { /*...*/ }  
}  
  
class Compilation { /*...*/  
    public async Task<SyntaxTree> GetSyntaxTreeAsync()  
    {  
        var parser = new Parser(); // allocation  
        await parser.ParseSourceCode(); // expensive  
        return parser.Syntax;  
    }  
}  
```  
  
 <span data-ttu-id="1e79d-277">Aramanın `GetSyntaxTreeAsync()` kodu `Parser`parlataya verdiğini ve sonra bir <xref:System.Threading.Tasks.Task> nesneyi `Task<SyntaxTree>`döndürttürün,</span><span class="sxs-lookup"><span data-stu-id="1e79d-277">You can see that calling `GetSyntaxTreeAsync()` instantiates a `Parser`, parses the code, and then returns a <xref:System.Threading.Tasks.Task> object, `Task<SyntaxTree>`.</span></span> <span data-ttu-id="1e79d-278">Pahalı kısmı `Parser` örneği tahsis ve kodu ayrıştırma olduğunu.</span><span class="sxs-lookup"><span data-stu-id="1e79d-278">The expensive part is allocating the `Parser` instance and parsing the code.</span></span> <span data-ttu-id="1e79d-279">İşlev, <xref:System.Threading.Tasks.Task> arayanların ayrışma çalışmasını bekleyebileceği ve Kullanıcı İçi'nin kullanıcı girişine yanıt verebileceği kullanıcı iş parçacığının serbest bırakılabilmeleri için bir yanıt verir.</span><span class="sxs-lookup"><span data-stu-id="1e79d-279">The function returns a <xref:System.Threading.Tasks.Task> so that callers can await the parsing work and free the UI thread to be responsive to user input.</span></span>
  
 <span data-ttu-id="1e79d-280">Çeşitli Visual Studio özellikleri aynı sözdizimi ağacını almayı deneyebilir, bu nedenle zaman ve ayırmalardan tasarruf etmek için ayrışma sonucunu önbelleğe almak için aşağıdaki kodu yazabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1e79d-280">Several Visual Studio features might try to get the same syntax tree, so you might write the following code to cache the parsing result to save time and allocations.</span></span> <span data-ttu-id="1e79d-281">Ancak, bu kod bir ayırma yatiran:</span><span class="sxs-lookup"><span data-stu-id="1e79d-281">However, this code incurs an allocation:</span></span>  
  
```csharp  
class Compilation { /*...*/  
  
    private SyntaxTree cachedResult;  
  
    public async Task<SyntaxTree> GetSyntaxTreeAsync()  
    {  
        if (this.cachedResult == null)  
        {  
            var parser = new Parser(); // allocation  
            await parser.ParseSourceCode(); // expensive  
            this.cachedResult = parser.Syntax;  
        }  
        return this.cachedResult;  
    }  
}  
```  
  
 <span data-ttu-id="1e79d-282">Önbelleğe alınmış yeni kodun `SyntaxTree` bir `cachedResult`alanı olduğunu görüyorsunuz.</span><span class="sxs-lookup"><span data-stu-id="1e79d-282">You see that the new code with caching has a `SyntaxTree` field named `cachedResult`.</span></span> <span data-ttu-id="1e79d-283">Bu alan null `GetSyntaxTreeAsync()` olduğunda, işi yapar ve önbellekte sonucu kaydeder.</span><span class="sxs-lookup"><span data-stu-id="1e79d-283">When this field is null, `GetSyntaxTreeAsync()` does the work and saves the result in the cache.</span></span> <span data-ttu-id="1e79d-284">`GetSyntaxTreeAsync()`nesneyi `SyntaxTree` döndürür.</span><span class="sxs-lookup"><span data-stu-id="1e79d-284">`GetSyntaxTreeAsync()` returns the `SyntaxTree` object.</span></span> <span data-ttu-id="1e79d-285">Sorun şu ki, bir `async` tür `Task<SyntaxTree>`işleviniz olduğunda ve bir `SyntaxTree`tür değeri döndürdüğünde, derleyici sonucu tutmak için bir `Task<SyntaxTree>.FromResult()`Görev ayırmak için kod yayır (kullanarak).</span><span class="sxs-lookup"><span data-stu-id="1e79d-285">The problem is that when you have an `async` function of type `Task<SyntaxTree>`, and you return a value of type `SyntaxTree`, the compiler emits code to allocate a Task to hold the result (by using `Task<SyntaxTree>.FromResult()`).</span></span> <span data-ttu-id="1e79d-286">Görev tamamlanmış olarak işaretlenir ve sonuç hemen kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="1e79d-286">The Task is marked as completed, and the result is immediately available.</span></span> <span data-ttu-id="1e79d-287">Yeni derleyicilerin kodunda, <xref:System.Threading.Tasks.Task> zaten tamamlanmış olan nesneler o kadar sık oluştu ki, bu ayırmaları düzeltme, yanıt verme yeteneğini belirgin şekilde artırdı.</span><span class="sxs-lookup"><span data-stu-id="1e79d-287">In the code for the new compilers, <xref:System.Threading.Tasks.Task> objects that were already completed occurred so often that fixing these allocations improved responsiveness noticeably.</span></span>
  
 <span data-ttu-id="1e79d-288">**Örneğin 6'yı düzeltme**</span><span class="sxs-lookup"><span data-stu-id="1e79d-288">**Fix for example 6**</span></span>  
  
 <span data-ttu-id="1e79d-289">Tamamlanan <xref:System.Threading.Tasks.Task> ayırmayı kaldırmak için Görev nesnesini tamamlanan sonuçla önbelleğe alabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="1e79d-289">To remove the completed <xref:System.Threading.Tasks.Task> allocation, you can cache the Task object with the completed result:</span></span>  
  
```csharp  
class Compilation { /*...*/  
  
    private Task<SyntaxTree> cachedResult;  
  
    public Task<SyntaxTree> GetSyntaxTreeAsync()  
    {  
        return this.cachedResult ??
               (this.cachedResult = GetSyntaxTreeUncachedAsync());  
    }  
  
    private async Task<SyntaxTree> GetSyntaxTreeUncachedAsync()  
    {  
        var parser = new Parser(); // allocation  
        await parser.ParseSourceCode(); // expensive  
        return parser.Syntax;  
    }  
}  
```  
  
 <span data-ttu-id="1e79d-290">Bu kod, `cachedResult` 'nin `Task<SyntaxTree>` türünü değiştirir `async` ve özgün kodu ' `GetSyntaxTreeAsync()`dan tutan bir yardımcı işlev kullanır.</span><span class="sxs-lookup"><span data-stu-id="1e79d-290">This code changes the type of `cachedResult` to `Task<SyntaxTree>` and employs an `async` helper function that holds the original code from `GetSyntaxTreeAsync()`.</span></span> <span data-ttu-id="1e79d-291">`GetSyntaxTreeAsync()`null değilse dönmek `cachedResult` için null [coalescing operatör](../../csharp/language-reference/operators/null-coalescing-operator.md) kullanır.</span><span class="sxs-lookup"><span data-stu-id="1e79d-291">`GetSyntaxTreeAsync()` now uses the [null coalescing operator](../../csharp/language-reference/operators/null-coalescing-operator.md) to return `cachedResult` if it isn't null.</span></span> <span data-ttu-id="1e79d-292">Null `cachedResult` ise, `GetSyntaxTreeAsync()` o `GetSyntaxTreeUncachedAsync()` zaman aramaları ve sonucu önbelleğe alın.</span><span class="sxs-lookup"><span data-stu-id="1e79d-292">If `cachedResult` is null, then `GetSyntaxTreeAsync()` calls `GetSyntaxTreeUncachedAsync()` and caches the result.</span></span> <span data-ttu-id="1e79d-293">Kodun `GetSyntaxTreeAsync()` normalde yapacağı `GetSyntaxTreeUncachedAsync()` gibi aramayı beklemediğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="1e79d-293">Notice that `GetSyntaxTreeAsync()` doesn’t await the call to `GetSyntaxTreeUncachedAsync()` as the code would normally.</span></span> <span data-ttu-id="1e79d-294">Beklemeyi kullanmamak, `GetSyntaxTreeUncachedAsync()` <xref:System.Threading.Tasks.Task> `GetSyntaxTreeAsync()` nesnesini döndürdüğünde <xref:System.Threading.Tasks.Task>hemen 'yi döndürür.</span><span class="sxs-lookup"><span data-stu-id="1e79d-294">Not using await means that when `GetSyntaxTreeUncachedAsync()` returns its <xref:System.Threading.Tasks.Task> object, `GetSyntaxTreeAsync()` immediately returns the <xref:System.Threading.Tasks.Task>.</span></span> <span data-ttu-id="1e79d-295">Şimdi, önbelleğe alınmış <xref:System.Threading.Tasks.Task>sonuç , önbelleğe alınmış sonucu döndürmek için hiçbir ayırmalar vardır.</span><span class="sxs-lookup"><span data-stu-id="1e79d-295">Now, the cached result is a <xref:System.Threading.Tasks.Task>, so there are no allocations to return the cached result.</span></span>
  
### <a name="additional-considerations"></a><span data-ttu-id="1e79d-296">Diğer konular</span><span class="sxs-lookup"><span data-stu-id="1e79d-296">Additional considerations</span></span>  
 <span data-ttu-id="1e79d-297">Burada, çok fazla veriyi işleyen büyük uygulamalarda veya uygulamalarda olası sorunlarla ilgili birkaç nokta daha verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="1e79d-297">Here are a few more points about potential problems in large apps or apps that process a lot of data.</span></span>
  
 <span data-ttu-id="1e79d-298">**Sözlükler**</span><span class="sxs-lookup"><span data-stu-id="1e79d-298">**Dictionaries**</span></span>  
  
 <span data-ttu-id="1e79d-299">Sözlükler birçok programda her yerde kullanılır ve sözlükler çok kullanışlı ve doğal olarak verimli olmasına rağmen.</span><span class="sxs-lookup"><span data-stu-id="1e79d-299">Dictionaries are used ubiquitously in many programs, and though dictionaries are very convenient and inherently efficient.</span></span> <span data-ttu-id="1e79d-300">Ancak, genellikle uygunsuz kullanılır.</span><span class="sxs-lookup"><span data-stu-id="1e79d-300">However, they’re often used inappropriately.</span></span> <span data-ttu-id="1e79d-301">Visual Studio ve yeni derleyicilerde, analizler sözlüklerin çoğunun tek bir öğe içerdiğini veya boş olduğunu göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="1e79d-301">In Visual Studio and the new compilers, analysis shows that many of the dictionaries contained a single element or were empty.</span></span> <span data-ttu-id="1e79d-302">Bir <xref:System.Collections.Generic.Dictionary%602> boş on alanları vardır ve bir x86 makine üzerinde yığın üzerinde 48 bayt kaplar.</span><span class="sxs-lookup"><span data-stu-id="1e79d-302">An empty <xref:System.Collections.Generic.Dictionary%602> has ten fields and occupies 48 bytes on the heap on an x86 machine.</span></span> <span data-ttu-id="1e79d-303">Sözlükler, sabit zamanlı arama ile bir eşleme veya etkieltif veri yapısı gerektiğinde harikadır.</span><span class="sxs-lookup"><span data-stu-id="1e79d-303">Dictionaries are great when you need a mapping or associative data structure with constant-time lookup.</span></span> <span data-ttu-id="1e79d-304">Ancak, yalnızca birkaç öğeniz olduğunda, sözlük kullanarak çok fazla yer harcarsınız.</span><span class="sxs-lookup"><span data-stu-id="1e79d-304">However, when you have only a few elements, you waste a lot of space by using a dictionary.</span></span> <span data-ttu-id="1e79d-305">Bunun yerine, örneğin, yinelemeli bir `List<KeyValuePair\<K,V>>`üzerinden bakabilirsiniz , gibi hızlı.</span><span class="sxs-lookup"><span data-stu-id="1e79d-305">Instead, for example, you could iteratively look through a `List<KeyValuePair\<K,V>>`, just as fast.</span></span> <span data-ttu-id="1e79d-306">Bir sözlüğü yalnızca verilerle yüklemek için kullanıyorsanız ve sonra ondan (çok yaygın bir desen) okursanız, kullandığınız öğe sayısına bağlı olarak N(log(N)) araması içeren sıralanmış bir dizi kullanmak neredeyse aynı kadar hızlı olabilir.</span><span class="sxs-lookup"><span data-stu-id="1e79d-306">If you use a dictionary only to load it with data and then read from it (a very common pattern), using a sorted array with an N(log(N)) lookup might be nearly as fast, depending on the number of elements you're using.</span></span>
  
 <span data-ttu-id="1e79d-307">**Sınıflar ve yapılar**</span><span class="sxs-lookup"><span data-stu-id="1e79d-307">**Classes vs. structures**</span></span>  
  
 <span data-ttu-id="1e79d-308">Bir bakıma, sınıflar ve yapılar uygulamalarınızı aparat etmek için klasik bir alan/zaman dengelemesi sağlar.</span><span class="sxs-lookup"><span data-stu-id="1e79d-308">In a way, classes and structures provide a classic space/time tradeoff for tuning your apps.</span></span> <span data-ttu-id="1e79d-309">Sınıflar, alanları olmasa bile x86 makinesinde 12 bayt ek yükü nelerdir, ancak yalnızca bir sınıf örneğine başvurmak için bir işaretçi gerektirdiğinden, geçici olarak dolaşmak ucuzdur.</span><span class="sxs-lookup"><span data-stu-id="1e79d-309">Classes incur 12 bytes of overhead on an x86 machine even if they have no fields, but they are inexpensive to pass around because it only takes a pointer to refer to a class instance.</span></span> <span data-ttu-id="1e79d-310">Yapılar kutulu değilseniz yığın ayırması yapmaz, ancak işlev bağımsız değişkenleri veya döndürme değerleri olarak büyük yapıları geçtiğizde, yapıların tüm veri üyelerini atomik olarak kopyalamak CPU'nun zaman ını alır.</span><span class="sxs-lookup"><span data-stu-id="1e79d-310">Structures incur no heap allocations if they aren’t boxed, but when you pass large structures as function arguments or return values, it takes CPU time to atomically copy all the data members of the structures.</span></span> <span data-ttu-id="1e79d-311">Yapıları döndüren özelliklere yapılan tekrarlanan çağrılara dikkat edin ve aşırı veri kopyalamayı önlemek için özelliğin değerini yerel bir değişkende önbelleğe alın.</span><span class="sxs-lookup"><span data-stu-id="1e79d-311">Watch out for repeated calls to properties that return structures, and cache the property’s value in a local variable to avoid excessive data copying.</span></span>
  
 <span data-ttu-id="1e79d-312">**Caches**</span><span class="sxs-lookup"><span data-stu-id="1e79d-312">**Caches**</span></span>  
  
 <span data-ttu-id="1e79d-313">Yaygın bir performans hilesi sonuçları önbelleğe almaktır.</span><span class="sxs-lookup"><span data-stu-id="1e79d-313">A common performance trick is to cache results.</span></span> <span data-ttu-id="1e79d-314">Ancak, boyut sınırı veya imha ilkesi olmayan bir önbellek bellek sızıntısı olabilir.</span><span class="sxs-lookup"><span data-stu-id="1e79d-314">However, a cache without a size cap or disposal policy can be a memory leak.</span></span> <span data-ttu-id="1e79d-315">Büyük miktarda veriyi işlerken, önbelleklerde çok fazla belleğe tutunursanız, önbelleğe alınan aramalarınızın avantajlarını geçersiz kılmak için çöp toplamaişlemine neden olabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1e79d-315">When processing large amounts of data, if you hold on to a lot of memory in caches, you can cause garbage collection to override the benefits of your cached lookups.</span></span>
  
 <span data-ttu-id="1e79d-316">Bu makalede, özellikle büyük miktarda veriyi işleyen büyük sistemler veya sistemler için uygulamanızın yanıt verme yeteneğini etkileyebilecek performans darboğaz belirtilerine nasıl dikkat edilmesi gerektiğini tartıştık.</span><span class="sxs-lookup"><span data-stu-id="1e79d-316">In this article, we discussed how you should be aware of performance bottleneck symptoms that can affect your app's responsiveness, especially for large systems or systems that process a large amount of data.</span></span> <span data-ttu-id="1e79d-317">Ortak suçlular boks, dize manipülasyonları, LINQ ve lambda, async yöntemleri önbelleğe alma, bir boyut sınırı veya bertaraf politikası olmadan önbelleğe alma, sözlüklerin uygunsuz kullanımı ve yapıların etrafında niçin geçilmesidir.</span><span class="sxs-lookup"><span data-stu-id="1e79d-317">Common culprits include boxing, string manipulations, LINQ and lambda, caching in async methods, caching without a size limit or disposal policy, inappropriate use of dictionaries, and passing around structures.</span></span> <span data-ttu-id="1e79d-318">Uygulamalarınızı alaişletmeniz için dört gerçek olduğunu unutmayın:</span><span class="sxs-lookup"><span data-stu-id="1e79d-318">Keep in mind the four facts for tuning your apps:</span></span>  
  
- <span data-ttu-id="1e79d-319">Erken optimize etmeyin – üretken olun ve sorunları fark ettiğinizde uygulamanızı ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="1e79d-319">Don’t prematurely optimize – be productive and tune your app when you spot problems.</span></span>
  
- <span data-ttu-id="1e79d-320">Profiller yalan söylemez – ölçüm yapmıyorsanız tahmin edeyim.</span><span class="sxs-lookup"><span data-stu-id="1e79d-320">Profiles don’t lie – you’re guessing if you’re not measuring.</span></span>
  
- <span data-ttu-id="1e79d-321">İyi araçlar tüm fark yaratmak - PerfView indirin ve deneyin.</span><span class="sxs-lookup"><span data-stu-id="1e79d-321">Good tools make all the difference – download PerfView and try it out.</span></span>
  
- <span data-ttu-id="1e79d-322">Her şey tahsisatlarla ilgilidir – derleyici platformu ekibinin zamanlarının çoğunu yeni derleyicilerin performansını artırmak için harcadığı yerdir.</span><span class="sxs-lookup"><span data-stu-id="1e79d-322">It's all about allocations – that is where the compiler platform team spent most of their time improving the performance of the new compilers.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="1e79d-323">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1e79d-323">See also</span></span>

- [<span data-ttu-id="1e79d-324">Bu konunun sunumu video</span><span class="sxs-lookup"><span data-stu-id="1e79d-324">Video of presentation of this topic</span></span>](https://channel9.msdn.com/Events/TechEd/NorthAmerica/2013/DEV-B333)
- [<span data-ttu-id="1e79d-325">Yeni Başlayanlar Performans Profilleme Rehberi</span><span class="sxs-lookup"><span data-stu-id="1e79d-325">Beginners Guide to Performance Profiling</span></span>](/visualstudio/profiling/beginners-guide-to-performance-profiling)
- [<span data-ttu-id="1e79d-326">Performans</span><span class="sxs-lookup"><span data-stu-id="1e79d-326">Performance</span></span>](index.md)
- <span data-ttu-id="1e79d-327">[.NET Performans İpuçları](https://docs.microsoft.com/previous-versions/dotnet/articles/ms973839(v%3dmsdn.10))</span><span class="sxs-lookup"><span data-stu-id="1e79d-327">[.NET Performance Tips](https://docs.microsoft.com/previous-versions/dotnet/articles/ms973839(v%3dmsdn.10))</span></span>
- [<span data-ttu-id="1e79d-328">Kanal 9 PerfView eğitimleri</span><span class="sxs-lookup"><span data-stu-id="1e79d-328">Channel 9 PerfView tutorials</span></span>](https://channel9.msdn.com/Series/PerfView-Tutorial)
- [<span data-ttu-id="1e79d-329">.NET Derleyici Platformu SDK</span><span class="sxs-lookup"><span data-stu-id="1e79d-329">The .NET Compiler Platform SDK</span></span>](../../csharp/roslyn-sdk/index.md)
- [<span data-ttu-id="1e79d-330">GitHub üzerinde dotnet/roslyn repo</span><span class="sxs-lookup"><span data-stu-id="1e79d-330">dotnet/roslyn repo on GitHub</span></span>](https://github.com/dotnet/roslyn)
