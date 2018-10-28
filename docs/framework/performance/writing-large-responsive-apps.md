---
title: Büyük, Yanıt Veren .NET Framework Uygulamaları Yazma
ms.date: 03/30/2017
ms.assetid: 123457ac-4223-4273-bb58-3bc0e4957e9d
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 8c73f1a4373583530d5afde113c5c4ec049bcea4
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/27/2018
ms.locfileid: "50195898"
---
# <a name="writing-large-responsive-net-framework-apps"></a><span data-ttu-id="f4d27-102">Büyük, Yanıt Veren .NET Framework Uygulamaları Yazma</span><span class="sxs-lookup"><span data-stu-id="f4d27-102">Writing Large, Responsive .NET Framework Apps</span></span>
<span data-ttu-id="f4d27-103">Bu makalede, büyük bir .NET Framework uygulamaları veya işlem büyük miktarda verileri dosyalar veya veritabanları gibi uygulama performansını iyileştirmek için ipuçları sağlar.</span><span class="sxs-lookup"><span data-stu-id="f4d27-103">This article provides tips for improving the performance of large .NET Framework apps, or apps that process a large amount of data such as files or databases.</span></span> <span data-ttu-id="f4d27-104">C# ve Visual Basic derleyicileri, yönetilen kodda yeniden yazma bu ipuçlarını gelir ve bu makale, çeşitli gerçek örnekler C# derleyicisi içerir.</span><span class="sxs-lookup"><span data-stu-id="f4d27-104">These tips come from rewriting the C# and Visual Basic compilers in managed code, and this article includes several real examples from the C# compiler.</span></span> 
  
 <span data-ttu-id="f4d27-105">.NET Framework uygulamaları oluşturmak için son derece üretken.</span><span class="sxs-lookup"><span data-stu-id="f4d27-105">The .NET Framework is highly productive for building apps.</span></span> <span data-ttu-id="f4d27-106">Uygulama oluşturma, güçlü ve güvenli diller ve kitaplıkların zengin bir koleksiyonu yüksek oranda bankanın olun.</span><span class="sxs-lookup"><span data-stu-id="f4d27-106">Powerful and safe languages and a rich collection of libraries make app building highly fruitful.</span></span> <span data-ttu-id="f4d27-107">Ancak, sorumluluk harika üretkenlik ile birlikte gelir.</span><span class="sxs-lookup"><span data-stu-id="f4d27-107">However, with great productivity comes responsibility.</span></span> <span data-ttu-id="f4d27-108">.NET Framework'ün tüm gücünü kullanın ancak gerektiğinde kodunuzun performansını ayarlamak hazırlanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="f4d27-108">You should use all the power of the .NET Framework, but be prepared to tune your code’s performance when needed.</span></span> 
  
## <a name="why-the-new-compiler-performance-applies-to-your-app"></a><span data-ttu-id="f4d27-109">Yeni derleyici performans uygulamanıza neden geçerlidir</span><span class="sxs-lookup"><span data-stu-id="f4d27-109">Why the new compiler performance applies to your app</span></span>  
 <span data-ttu-id="f4d27-110">.NET derleyici Platformu ("Roslyn") ekibi C# yeniden yazıldı ve Visual Basic derleyicileri, yönetilen kodu modelleme ve kodunu analiz etme, derleme araçları ve çok daha zengin, kod duyarlı deneyimler Visual Studio'da etkinleştirme için yeni API'ler sağlar.</span><span class="sxs-lookup"><span data-stu-id="f4d27-110">The .NET Compiler Platform ("Roslyn") team rewrote the C# and Visual Basic compilers in managed code to provide new APIs for modeling and analyzing code, building tools, and enabling much richer, code-aware experiences in Visual Studio.</span></span> <span data-ttu-id="f4d27-111">Yeniden yazma System.codeDom ve Visual Studio oluşturma yeni derleyiciler üzerinde deneyimlerin büyük herhangi bir .NET Framework uygulama veya çok miktarda veri işleyen herhangi bir uygulama için geçerli olan yararlı performans öngörüleri göstermiştir.</span><span class="sxs-lookup"><span data-stu-id="f4d27-111">Rewriting the compilers and building Visual Studio experiences on the new compilers revealed useful performance insights that are applicable to any large .NET Framework app or any app that processes a lot of data.</span></span> <span data-ttu-id="f4d27-112">Görüş ve örnekler C# derleyicisi yararlanmak için derleyiciler hakkında bilmeniz gerekmez.</span><span class="sxs-lookup"><span data-stu-id="f4d27-112">You don't need to know about compilers to take advantage of the insights and examples from the C# compiler.</span></span> 
  
 <span data-ttu-id="f4d27-113">Visual Studio tanımlayıcıları ve anahtar sözcükler, söz dizimi tamamlanma listeleri, renklendirme dalgalı çizgiler gibi hataları, parametre ipuçları, kod sorunları ve kod eylemleri için kullanıcıların hayran, tüm IntelliSense özelliklerini oluşturmak için derleyicinin API'leri kullanır.</span><span class="sxs-lookup"><span data-stu-id="f4d27-113">Visual Studio uses the compiler APIs to build all the IntelliSense features that users love, such as colorization of identifiers and keywords, syntax completion lists, squiggles for errors, parameter tips, code issues, and code actions.</span></span> <span data-ttu-id="f4d27-114">Visual Studio, geliştiricilerin yazarak ve kodlarını değiştirme ve derleyici geliştiriciler Düzenle kod sürekli modeller sırada Visual Studio yanıt kalması gereken bu Yardım sağlar.</span><span class="sxs-lookup"><span data-stu-id="f4d27-114">Visual Studio provides this help while developers are typing and changing their code, and Visual Studio must remain responsive while the compiler continually models the code developers edit.</span></span> 
  
 <span data-ttu-id="f4d27-115">Son kullanıcılarınızın uygulamanızla etkileşim kurduğunuzda, bunlar esnek olmasını bekler.</span><span class="sxs-lookup"><span data-stu-id="f4d27-115">When your end users interact with your app, they expect it to be responsive.</span></span> <span data-ttu-id="f4d27-116">Yazarak ya da komut işleme hiçbir zaman engellenmelidir.</span><span class="sxs-lookup"><span data-stu-id="f4d27-116">Typing or command handling should never be blocked.</span></span> <span data-ttu-id="f4d27-117">Yardım hızla açılır veya kullanıcı yazmaya devam ederse vazgeçmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="f4d27-117">Help should pop up quickly or give up if the user continues typing.</span></span> <span data-ttu-id="f4d27-118">Uygulamanızı ağır düşünüyorsanız uygulamayı uzun hesaplamalar ile UI iş parçacığı engelleme kaçınmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="f4d27-118">Your app should avoid blocking the UI thread with long computations that make the app feel sluggish.</span></span> 
  
 <span data-ttu-id="f4d27-119">Roslyn derleyicileri hakkında daha fazla bilgi için bkz: [.NET derleyici Platformu SDK](../../csharp/roslyn-sdk/index.md).</span><span class="sxs-lookup"><span data-stu-id="f4d27-119">For more information about Roslyn compilers, see [The .NET Compiler Platform SDK](../../csharp/roslyn-sdk/index.md).</span></span>
  
## <a name="just-the-facts"></a><span data-ttu-id="f4d27-120">Bulguları</span><span class="sxs-lookup"><span data-stu-id="f4d27-120">Just the Facts</span></span>  
 <span data-ttu-id="f4d27-121">Performans ayarlama, bu bilgileri göz önünde bulundurun ve hızlı yanıt veren .NET Framework uygulamaları oluşturma.</span><span class="sxs-lookup"><span data-stu-id="f4d27-121">Consider these facts when tuning performance and creating responsive .NET Framework apps.</span></span> 
  
### <a name="fact-1-dont-prematurely-optimize"></a><span data-ttu-id="f4d27-122">Olgu 1: beklenenden önce iyileştirme</span><span class="sxs-lookup"><span data-stu-id="f4d27-122">Fact 1: Don’t prematurely optimize</span></span>  
 <span data-ttu-id="f4d27-123">Olmasını ihtiyaç duyduğundan daha karmaşık kod yazma, hata ayıklama ve maliyetleri polishing bakım doğurur.</span><span class="sxs-lookup"><span data-stu-id="f4d27-123">Writing code that is more complex than it needs to be incurs maintenance, debugging, and polishing costs.</span></span> <span data-ttu-id="f4d27-124">Sezgisel bir kavrayın kodlama sorunlarını çözmek ve daha verimli kod yazma, programcılar vardır.</span><span class="sxs-lookup"><span data-stu-id="f4d27-124">Experienced programmers have an intuitive grasp of how to solve coding problems and write more efficient code.</span></span> <span data-ttu-id="f4d27-125">Ancak, bunlar bazen erken kodlarını iyileştirin.</span><span class="sxs-lookup"><span data-stu-id="f4d27-125">However, they sometimes prematurely optimize their code.</span></span> <span data-ttu-id="f4d27-126">Örneğin, bir Basit dizi yeterli veya değerleri yalnızca yeniden hesaplanıyor yerine bellekte sızıntı karmaşık önbelleğe kullandığınızda bir karma tablo kullanın.</span><span class="sxs-lookup"><span data-stu-id="f4d27-126">For example, they use a hash table when a simple array would suffice, or use complicated caching that may leak memory instead of simply recomputing values.</span></span> <span data-ttu-id="f4d27-127">Bir deneyim Programcı olmasanız bile için performans testi ve sorunları bulmak, kodunuzu analiz gerekir.</span><span class="sxs-lookup"><span data-stu-id="f4d27-127">Even if you’re an experience programmer, you should test for performance and analyze your code when you find issues.</span></span> 
  
### <a name="fact-2-if-youre-not-measuring-youre-guessing"></a><span data-ttu-id="f4d27-128">Olgu 2:, ölçüm yaptığınız değil ise, tahmin</span><span class="sxs-lookup"><span data-stu-id="f4d27-128">Fact 2: If you’re not measuring, you’re guessing</span></span>  
 <span data-ttu-id="f4d27-129">Profilleri ve ölçümler yer yok.</span><span class="sxs-lookup"><span data-stu-id="f4d27-129">Profiles and measurements don’t lie.</span></span> <span data-ttu-id="f4d27-130">Profilleri, CPU tam yüklü olmadığı ya da disk g/ç üzerinde engellendi gösterir.</span><span class="sxs-lookup"><span data-stu-id="f4d27-130">Profiles show you whether the CPU is fully loaded or whether you’re blocked on disk I/O.</span></span> <span data-ttu-id="f4d27-131">Profilleri bahsedin, ne tür ve ne kadar bellek ayırma ve mi CPU harcama çok zaman içinde [çöp toplama](../../../docs/standard/garbage-collection/index.md) (GC).</span><span class="sxs-lookup"><span data-stu-id="f4d27-131">Profiles tell you what kind and how much memory you’re allocating and whether your CPU is spending a lot of time in [garbage collection](../../../docs/standard/garbage-collection/index.md) (GC).</span></span> 
  
 <span data-ttu-id="f4d27-132">Uygulamanızda performans hedeflerini önemli müşteri deneyimleri veya senaryoları ayarlayın ve performansını ölçmek için testleri yazmak gerekir.</span><span class="sxs-lookup"><span data-stu-id="f4d27-132">You should set performance goals for key customer experiences or scenarios in your app and write tests to measure performance.</span></span> <span data-ttu-id="f4d27-133">Başarısız olan testler bilimsel yöntemi uygulayarak araştırın: profillerini kullanmak için size rehberlik, ne sorun olabilir, hipotezler varsayımınızın deneme ile test ve kod değişikliği.</span><span class="sxs-lookup"><span data-stu-id="f4d27-133">Investigate failing tests by applying the scientific method: use profiles to guide you, hypothesize what the issue might be, and test your hypothesis with an experiment or code change.</span></span> <span data-ttu-id="f4d27-134">Performans gerilemeleri neden değişiklikleri yalıtabilirsiniz için normal test ile zaman içinde temel performans ölçümleri kurun.</span><span class="sxs-lookup"><span data-stu-id="f4d27-134">Establish baseline performance measurements over time with regular testing, so you can isolate changes that cause regressions in performance.</span></span> <span data-ttu-id="f4d27-135">Sıkı bir şekilde performans iş yaklaşan tarafından zaman ihtiyacınız olmayan kod güncelleştirmeleriyle önlenir.</span><span class="sxs-lookup"><span data-stu-id="f4d27-135">By approaching performance work in a rigorous way, you’ll avoid wasting time with code updates you don’t need.</span></span> 
  
### <a name="fact-3-good-tools-make-all-the-difference"></a><span data-ttu-id="f4d27-136">Olgu 3: İyi Araçlar fark olun.</span><span class="sxs-lookup"><span data-stu-id="f4d27-136">Fact 3: Good tools make all the difference</span></span>  
 <span data-ttu-id="f4d27-137">Hızlı bir şekilde büyük performans sorunları (CPU, bellek veya disk) ve bu sorunları neden kodu bulun Yardım ayrıntılarına girmek iyi araçları sağlar.</span><span class="sxs-lookup"><span data-stu-id="f4d27-137">Good tools let you drill quickly into the biggest performance issues (CPU, memory, or disk) and help you locate the code that causes those bottlenecks.</span></span> <span data-ttu-id="f4d27-138">Microsoft gelen çeşitli performans araçları gibi [Visual Studio Profiler](/visualstudio/profiling/beginners-guide-to-performance-profiling), [Windows Phone analiz aracı](https://msdn.microsoft.com/library/e67e3199-ea43-4d14-ab7e-f7f19266253f), ve [PerfView](https://www.microsoft.com/download/details.aspx?id=28567).</span><span class="sxs-lookup"><span data-stu-id="f4d27-138">Microsoft ships a variety of performance tools such as [Visual Studio Profiler](/visualstudio/profiling/beginners-guide-to-performance-profiling), [Windows Phone Analysis Tool](https://msdn.microsoft.com/library/e67e3199-ea43-4d14-ab7e-f7f19266253f), and [PerfView](https://www.microsoft.com/download/details.aspx?id=28567).</span></span> 
  
 <span data-ttu-id="f4d27-139">PerfView disk g/ç gibi ayrıntılı sorunlara odaklanmak, GC olayları ve bellek yardımcı olan ücretsiz ve şaşırtıcı derecede güçlü bir araçtır.</span><span class="sxs-lookup"><span data-stu-id="f4d27-139">PerfView is a free and amazingly powerful tool that helps you focus on deep issues such as disk I/O, GC events, and memory.</span></span> <span data-ttu-id="f4d27-140">Performansla ilgili yakalayabilirsiniz [olay izleme için Windows](../../../docs/framework/wcf/samples/etw-tracing.md) (ETW) olayları ve görünümü, uygulama başına bir kolayca, her işlem, yığın başına ve başına iş parçacığı bilgileri.</span><span class="sxs-lookup"><span data-stu-id="f4d27-140">You can capture performance-related [Event Tracing for Windows](../../../docs/framework/wcf/samples/etw-tracing.md) (ETW) events and view easily per app, per process, per stack, and per thread information.</span></span> <span data-ttu-id="f4d27-141">PerfView uygulamanızı ayırır, bellek ve hangi işlevleri veya çağrı yığınlarını ne kadar bellek ayırmaları için katkıda bulunan ne kadar ve ne tür gösterir.</span><span class="sxs-lookup"><span data-stu-id="f4d27-141">PerfView shows you how much and what kind of memory your app allocates, and which functions or call stacks contribute how much to the memory allocations.</span></span> <span data-ttu-id="f4d27-142">Zengin Yardım konuları, tanıtımlar ve videolar aracıyla dahil Ayrıntılar için bkz. (gibi [PerfView öğreticiler](https://channel9.msdn.com/Series/PerfView-Tutorial) Channel 9).</span><span class="sxs-lookup"><span data-stu-id="f4d27-142">For details, see the rich help topics, demos, and videos included with the tool (such as the [PerfView tutorials](https://channel9.msdn.com/Series/PerfView-Tutorial) on Channel 9).</span></span> 
  
### <a name="fact-4-its-all-about-allocations"></a><span data-ttu-id="f4d27-143">Olgu 4: Tüm ayırmaları hakkında olduğu</span><span class="sxs-lookup"><span data-stu-id="f4d27-143">Fact 4: It’s all about allocations</span></span>  
 <span data-ttu-id="f4d27-144">Bu bir yanıt oluşturmak düşündüğünüzden .NET Framework uygulaması Kabarcık sıralama yerine Hızlı sıralama kullanma gibi tüm algoritmalar hakkında ancak bu durum geçerli değildir.</span><span class="sxs-lookup"><span data-stu-id="f4d27-144">You might think that building a responsive .NET Framework app is all about algorithms, such as using quick sort instead of bubble sort, but that's not the case.</span></span> <span data-ttu-id="f4d27-145">Özellikle uygulama çok büyükse veya büyük miktarlarda veri işler hızlı yanıt veren bir uygulama oluşturmanın en büyük faktör, bellek ayırma olduğu.</span><span class="sxs-lookup"><span data-stu-id="f4d27-145">The biggest factor in building a responsive app is allocating memory, especially when your app is very large or processes large amounts of data.</span></span> 
  
 <span data-ttu-id="f4d27-146">Neredeyse tüm esnek IDE oluşturmak için iş API'leri yeni derleyici ile deneyimleri ayırmaları önleme ve önbelleğe alma stratejilerine yönetme dahil.</span><span class="sxs-lookup"><span data-stu-id="f4d27-146">Almost all the work to build responsive IDE experiences with the new compiler APIs involved avoiding allocations and managing caching strategies.</span></span> <span data-ttu-id="f4d27-147">İzleme PerfView yeni C# ve Visual Basic derleyicileri performansını nadiren CPU bağımlı olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="f4d27-147">PerfView traces show that the performance of the new C# and Visual Basic compilers is rarely CPU bound.</span></span> <span data-ttu-id="f4d27-148">Oluşturulan kod yayan veya derleyiciler meta verileri okuma binlerce veya milyonlarca satır kod, yüzlerce okurken g/ç olabilir.</span><span class="sxs-lookup"><span data-stu-id="f4d27-148">The compilers can be I/O bound when reading hundreds of thousands or millions of lines of code, reading metadata, or emitting generated code.</span></span> <span data-ttu-id="f4d27-149">UI iş parçacığı gecikmeleri neredeyse tüm çöp toplama nedeniyle ' dir.</span><span class="sxs-lookup"><span data-stu-id="f4d27-149">The UI thread delays are nearly all due to garbage collection.</span></span> <span data-ttu-id="f4d27-150">.NET Framework GC yüksek performans için ayarlanmış ve aynı anda uygulama kodu yürütürken işini çoğunu yapar.</span><span class="sxs-lookup"><span data-stu-id="f4d27-150">The .NET Framework GC is highly tuned for performance and does much of its work concurrently while app code executes.</span></span> <span data-ttu-id="f4d27-151">Ancak, tek bir ayırma pahalı bir tetikleyebilirsiniz [gen2](../../../docs/standard/garbage-collection/fundamentals.md) tüm iş parçacıklarını durdurma koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="f4d27-151">However, a single allocation can trigger an expensive [gen2](../../../docs/standard/garbage-collection/fundamentals.md) collection, stopping all threads.</span></span> 
  
## <a name="common-allocations-and-examples"></a><span data-ttu-id="f4d27-152">Ortak ayırmaları ve örnekler</span><span class="sxs-lookup"><span data-stu-id="f4d27-152">Common allocations and examples</span></span>  
 <span data-ttu-id="f4d27-153">Bu bölümdeki örnek ifadeler küçük görünen ayırmaları gizli.</span><span class="sxs-lookup"><span data-stu-id="f4d27-153">The example expressions in this section have hidden allocations that appear small.</span></span> <span data-ttu-id="f4d27-154">Ancak, çok sayıda uygulama, yeterli sayıda deyimleri yürütür, megabayt, hatta gigabayt ayırmaların yüzlerce nedenlerini olabilir.</span><span class="sxs-lookup"><span data-stu-id="f4d27-154">However, if a large app executes the expressions enough times, they can causes hundreds of megabytes, even gigabytes, of allocations.</span></span> <span data-ttu-id="f4d27-155">Gigabayt cinsinden bellek tahsis düzenleyicide Geliştirici yazarak simulated ve performans takım senaryoları yazarken odaklanmak için yönetilen Örneğin, bir dakikalık sınar.</span><span class="sxs-lookup"><span data-stu-id="f4d27-155">For example, one-minute tests that simulated a developer’s typing in the editor allocated gigabytes of memory and led the performance team to focus on typing scenarios.</span></span> 
  
### <a name="boxing"></a><span data-ttu-id="f4d27-156">Kutulama</span><span class="sxs-lookup"><span data-stu-id="f4d27-156">Boxing</span></span>  
 <span data-ttu-id="f4d27-157">[Kutulama](~/docs/csharp/programming-guide/types/boxing-and-unboxing.md) normal olarak değer türleri yığında live veya veri yapılarını nesneyi sarmalanır gerçekleşir.</span><span class="sxs-lookup"><span data-stu-id="f4d27-157">[Boxing](~/docs/csharp/programming-guide/types/boxing-and-unboxing.md) occurs when value types that normally live on the stack or in data structures are wrapped in an object.</span></span> <span data-ttu-id="f4d27-158">Diğer bir deyişle, verileri tutmak için bir nesne ayrılamadı ve ardından nesneye bir işaretçi döndürür.</span><span class="sxs-lookup"><span data-stu-id="f4d27-158">That is, you allocate an object to hold the data, and then return a pointer to the object.</span></span> <span data-ttu-id="f4d27-159">.NET Framework, bazen bir yöntem veya bir depolama konumu türünün imza nedeniyle değerleri kutular.</span><span class="sxs-lookup"><span data-stu-id="f4d27-159">The .NET Framework sometimes boxes values due to the signature of a method or the type of a storage location.</span></span> <span data-ttu-id="f4d27-160">Bir değer türü bir nesne nedenleri bellek ayırmayı kaydırma.</span><span class="sxs-lookup"><span data-stu-id="f4d27-160">Wrapping a value type in an object causes memory allocation.</span></span> <span data-ttu-id="f4d27-161">Birçok kutulama işlemleri, megabayt veya gigabayt uygulamanızı daha fazla GC'ler sebep uygulamanıza ayırmaların katkıda bulunabilir.</span><span class="sxs-lookup"><span data-stu-id="f4d27-161">Many boxing operations can contribute megabytes or gigabytes of allocations to your app, which means that your app will cause more GCs.</span></span> <span data-ttu-id="f4d27-162">.NET Framework ve dil derleyicileri kutulama mümkün olduğunda kaçının, ancak bazen az beklediğiniz olur.</span><span class="sxs-lookup"><span data-stu-id="f4d27-162">The .NET Framework and the language compilers avoid boxing when possible, but sometimes it happens when you least expect it.</span></span> 
  
 <span data-ttu-id="f4d27-163">Perfview'de Aç kutulama görmek için bir izleme açın ve uygulamanızın işlem adı altında GC yığın ayırma yığında bakın (unutmayın, PerfView tüm işlemlerde raporları).</span><span class="sxs-lookup"><span data-stu-id="f4d27-163">To see boxing in PerfView, open a trace and look at GC Heap Alloc Stacks under your app’s process name (remember, PerfView reports on all processes).</span></span> <span data-ttu-id="f4d27-164">Türleri gibi görürseniz <xref:System.Int32?displayProperty=nameWithType> ve <xref:System.Char?displayProperty=nameWithType> ayırmaları altında değer türleri kutulama.</span><span class="sxs-lookup"><span data-stu-id="f4d27-164">If you see types like <xref:System.Int32?displayProperty=nameWithType> and <xref:System.Char?displayProperty=nameWithType> under allocations, you are boxing value types.</span></span> <span data-ttu-id="f4d27-165">Bu türlerinden birini seçerek Kutulu işlevler ve yığınlarını gösterir.</span><span class="sxs-lookup"><span data-stu-id="f4d27-165">Choosing one of these types will show the stacks and functions in which they are boxed.</span></span> 
  
 <span data-ttu-id="f4d27-166">**Örnek 1: dize yöntemlerini ve değer tür bağımsız değişkenleri**</span><span class="sxs-lookup"><span data-stu-id="f4d27-166">**Example 1: string methods and value type arguments**</span></span>  
  
 <span data-ttu-id="f4d27-167">Bu örnek kod, büyük olasılıkla gereksiz ve aşırı kutulama gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="f4d27-167">This sample code illustrates potentially unnecessary and excessive boxing:</span></span>  
  
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
  
 <span data-ttu-id="f4d27-168">Bu kod günlüğü işlevini sağlar. böylece, bir uygulamayı çağırabilir `Log` sık, milyonlarca kez belki de işlev.</span><span class="sxs-lookup"><span data-stu-id="f4d27-168">This code provides logging functionality, so an app may call the `Log` function frequently, maybe millions of times.</span></span> <span data-ttu-id="f4d27-169">Sorunu olan çağrı `string.Format` çözümler <xref:System.String.Format%28System.String%2CSystem.Object%2CSystem.Object%29> aşırı yükleme.</span><span class="sxs-lookup"><span data-stu-id="f4d27-169">The problem is that the call to `string.Format` resolves to the <xref:System.String.Format%28System.String%2CSystem.Object%2CSystem.Object%29> overload.</span></span> 
  
 <span data-ttu-id="f4d27-170">Bu aşırı yükü .NET Framework kutusuna gerektirir `int` bu yöntem çağrısına geçirilecek nesnelere değerleri.</span><span class="sxs-lookup"><span data-stu-id="f4d27-170">This overload requires the .NET Framework to box the `int` values into objects to pass them to this method call.</span></span> <span data-ttu-id="f4d27-171">Kısmi bir düzeltme çağırmaktır `id.ToString()` ve `size.ToString()` ve (hangi nesneleri) tüm dizeleri geçirmek `string.Format` çağırın.</span><span class="sxs-lookup"><span data-stu-id="f4d27-171">A partial fix is to call `id.ToString()` and `size.ToString()` and pass all strings (which are objects) to the `string.Format` call.</span></span> <span data-ttu-id="f4d27-172">Çağırma `ToString()` ayırma içinde yine de gerçekleşir ancak bu bir dize tahsis `string.Format`.</span><span class="sxs-lookup"><span data-stu-id="f4d27-172">Calling `ToString()` does allocate a string, but that allocation will happen anyway inside `string.Format`.</span></span> 
  
 <span data-ttu-id="f4d27-173">Bu temel düşünebilirsiniz çağrısı `string.Format` yalnızca dize birleştirme olduğundan, bunun yerine bu kodu yazabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="f4d27-173">You might consider that this basic call to `string.Format` is just string concatenation, so you might write this code instead:</span></span>  
  
```csharp  
var s = id.ToString() + ':' + size.ToString();  
```  
  
 <span data-ttu-id="f4d27-174">Ancak, kodun o satırına için derleme nedeni kutulama ayırma tanıtır <xref:System.String.Concat%28System.Object%2CSystem.Object%2CSystem.Object%29>.</span><span class="sxs-lookup"><span data-stu-id="f4d27-174">However, that line of code introduces a boxing allocation because it compiles to <xref:System.String.Concat%28System.Object%2CSystem.Object%2CSystem.Object%29>.</span></span> <span data-ttu-id="f4d27-175">.NET Framework karakter çağrılacak sabiti kutusunda gerekir `Concat`</span><span class="sxs-lookup"><span data-stu-id="f4d27-175">The .NET Framework must box the character literal to invoke `Concat`</span></span>  
  
 <span data-ttu-id="f4d27-176">**Örneğin 1 Düzelt**</span><span class="sxs-lookup"><span data-stu-id="f4d27-176">**Fix for example 1**</span></span>  
  
 <span data-ttu-id="f4d27-177">Tüm düzeltme, basit bir işlemdir.</span><span class="sxs-lookup"><span data-stu-id="f4d27-177">The complete fix is simple.</span></span> <span data-ttu-id="f4d27-178">Yalnızca karakteri bir dize sabit değeri, değişmez değer dizeleri nesneler olduğundan, hiçbir kutulama doğurur değiştirin:</span><span class="sxs-lookup"><span data-stu-id="f4d27-178">Just replace the character literal with a string literal, which incurs no boxing because strings are already objects:</span></span>  
  
```csharp  
var s = id.ToString() + ":" + size.ToString();  
```  
  
 <span data-ttu-id="f4d27-179">**Örnek 2: sabit listesi kutulama**</span><span class="sxs-lookup"><span data-stu-id="f4d27-179">**Example 2: enum boxing**</span></span>  
  
 <span data-ttu-id="f4d27-180">Bu örnekte, sık kullanılması nedeniyle yeni C# ve Visual Basic derleyicileri, bir ayırma Numaralandırma türleri, özellikle sözlük arama işlemleri sektörünüz sorumluydu.</span><span class="sxs-lookup"><span data-stu-id="f4d27-180">This example was responsible for a huge amount of allocation in the new C# and Visual Basic compilers due to frequent use of enumeration types, especially in dictionary lookup operations.</span></span> 
  
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
  
 <span data-ttu-id="f4d27-181">Bu sorun, çok hafif olmasıdır.</span><span class="sxs-lookup"><span data-stu-id="f4d27-181">This problem is very subtle.</span></span> <span data-ttu-id="f4d27-182">PerfView olarak rapor <xref:System.Enum.GetHashCode> yöntemi temel alınan numaralandırma türü, Uygulama nedenlerinden gösterimini kutular çünkü kutulama.</span><span class="sxs-lookup"><span data-stu-id="f4d27-182">PerfView would report this as <xref:System.Enum.GetHashCode> boxing because the method boxes the underlying representation of the enumeration type, for implementation reasons.</span></span> <span data-ttu-id="f4d27-183">PerfView içinde yakından bakarsanız, her çağrı için iki kutulama ayırmaları görebilirsiniz <xref:System.Enum.GetHashCode>.</span><span class="sxs-lookup"><span data-stu-id="f4d27-183">If you look closely in PerfView, you may see two boxing allocations for each call to <xref:System.Enum.GetHashCode>.</span></span> <span data-ttu-id="f4d27-184">Derleyici bir ekler ve diğer .NET Framework ekler.</span><span class="sxs-lookup"><span data-stu-id="f4d27-184">The compiler inserts one, and the .NET Framework inserts the other.</span></span> 
  
 <span data-ttu-id="f4d27-185">**Örnek 2 düzeltme**</span><span class="sxs-lookup"><span data-stu-id="f4d27-185">**Fix for example 2**</span></span>  
  
 <span data-ttu-id="f4d27-186">Atama temel alınan gösterimi çağırmadan önce tarafından her iki ayırma kolayca kaçınabilirsiniz <xref:System.Enum.GetHashCode>:</span><span class="sxs-lookup"><span data-stu-id="f4d27-186">You can easily avoid both allocations by casting to the underlying representation before calling <xref:System.Enum.GetHashCode>:</span></span>  
  
```csharp  
((int)color).GetHashCode()  
```  
  
 <span data-ttu-id="f4d27-187">Numaralandırma türleri kutulama, başka bir ortak kaynak <xref:System.Enum.HasFlag%28System.Enum%29?displayProperty=nameWithType> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="f4d27-187">Another common source of boxing on enumeration types is the <xref:System.Enum.HasFlag%28System.Enum%29?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="f4d27-188">Geçirilen bağımsız değişken <xref:System.Enum.HasFlag%28System.Enum%29> Kutulu gerekir.</span><span class="sxs-lookup"><span data-stu-id="f4d27-188">The argument passed to <xref:System.Enum.HasFlag%28System.Enum%29> has to be boxed.</span></span> <span data-ttu-id="f4d27-189">Çoğu durumda, çağrıları değiştirerek <xref:System.Enum.HasFlag%28System.Enum%29?displayProperty=nameWithType> bir bit düzeyinde ile daha basit ve ayırma testtir.</span><span class="sxs-lookup"><span data-stu-id="f4d27-189">In most cases, replacing calls to <xref:System.Enum.HasFlag%28System.Enum%29?displayProperty=nameWithType> with a bitwise test is simpler and allocation-free.</span></span> 
  
 <span data-ttu-id="f4d27-190">İlk performans gerçeği göz önünde bulundurun (diğer bir deyişle, erken iyileştirme) ve bu şekilde tüm kodunuzu yeniden başlatma.</span><span class="sxs-lookup"><span data-stu-id="f4d27-190">Keep the first performance fact in mind (that is, don’t prematurely optimize) and don’t start rewriting all your code in this way.</span></span> <span data-ttu-id="f4d27-191">Bu kutulama maliyetlerini unutmayın, ancak yalnızca uygulama profili oluşturma ve etkin noktaları bulma sonra kodunuzu değiştirin.</span><span class="sxs-lookup"><span data-stu-id="f4d27-191">Be aware of these boxing costs, but change your code only after profiling your app and finding the hot spots.</span></span> 
  
### <a name="strings"></a><span data-ttu-id="f4d27-192">Dizeler</span><span class="sxs-lookup"><span data-stu-id="f4d27-192">Strings</span></span>  
 <span data-ttu-id="f4d27-193">Dize işlemeleri ayırmalar için büyük culprits bazıları, ve bunlar genellikle PerfView ilk beş ayırmalar şeklinde gösterilir.</span><span class="sxs-lookup"><span data-stu-id="f4d27-193">String manipulations are some of the biggest culprits for allocations, and they often show up in PerfView in the top five allocations.</span></span> <span data-ttu-id="f4d27-194">Program serileştirme, JSON ve REST API'leri için dizeleri kullanın.</span><span class="sxs-lookup"><span data-stu-id="f4d27-194">Programs use strings for serialization, JSON, and REST APIs.</span></span> <span data-ttu-id="f4d27-195">Numaralandırma türleri kullanamadığınızda sistemleriyle birlikte çalışma için dizeleri programlı sabitleri kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f4d27-195">You can use strings as programmatic constants for interoperating with systems when you can’t use enumeration types.</span></span> <span data-ttu-id="f4d27-196">Dizeleri yüksek oranda performansı etkilediğinden, profil oluşturma gösterilmektedir, çağrılar için konum <xref:System.String> gibi yöntemler <xref:System.String.Format%2A>, <xref:System.String.Concat%2A>, <xref:System.String.Split%2A>, <xref:System.String.Join%2A>, <xref:System.String.Substring%2A>ve benzeri.</span><span class="sxs-lookup"><span data-stu-id="f4d27-196">When your profiling shows that strings are highly affecting performance, look for calls to <xref:System.String> methods such as <xref:System.String.Format%2A>, <xref:System.String.Concat%2A>, <xref:System.String.Split%2A>, <xref:System.String.Join%2A>, <xref:System.String.Substring%2A>, and so on.</span></span> <span data-ttu-id="f4d27-197">Kullanarak <xref:System.Text.StringBuilder> bir dize oluşturma çok sayıda parça yardımcı olur, ancak bile ayırma maliyetini önlemek için <xref:System.Text.StringBuilder> nesne yönetmeniz gereken bir performans sorunu haline.</span><span class="sxs-lookup"><span data-stu-id="f4d27-197">Using <xref:System.Text.StringBuilder> to avoid the cost of creating one string from many pieces helps, but even allocating the <xref:System.Text.StringBuilder> object might become a bottleneck that you need to manage.</span></span> 
  
 <span data-ttu-id="f4d27-198">**Örnek 3: dize işlemleri**</span><span class="sxs-lookup"><span data-stu-id="f4d27-198">**Example 3: string operations**</span></span>  
  
 <span data-ttu-id="f4d27-199">C# derleyicisi, metnin bir biçimlendirilmiş XML belge açıklamasının yazar bu kodu sahipti:</span><span class="sxs-lookup"><span data-stu-id="f4d27-199">The C# compiler had this code that writes the text of a formatted XML doc comment:</span></span>  
  
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
  
 <span data-ttu-id="f4d27-200">Bu kod dize düzenlemesi çok mu olduğunu görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f4d27-200">You can see that this code does a lot of string manipulation.</span></span> <span data-ttu-id="f4d27-201">Kod satırları ayrı dizelere içerecek şekilde kırpmanıza denetlemek için beyaz boşluk, bölme için kitaplık yöntemleri kullanır. olmadığını bağımsız değişken `text` bir XML belge açıklaması ve satırlarından alt dizeleri ayıklama.</span><span class="sxs-lookup"><span data-stu-id="f4d27-201">The code uses library methods to split lines into separate strings, to trim white space, to check whether the argument `text` is an XML documentation comment, and to extract substrings from lines.</span></span> 
  
 <span data-ttu-id="f4d27-202">İçinde ilk satırda `WriteFormattedDocComment`, `text.Split` çağrı her çağrıldığında bu yeni üç öğeli bir dizi bağımsız değişken olarak ayırır.</span><span class="sxs-lookup"><span data-stu-id="f4d27-202">On the first line inside `WriteFormattedDocComment`, the `text.Split` call allocates a new three-element array as the argument every time it’s called.</span></span> <span data-ttu-id="f4d27-203">Derleyici, her zaman bu dizi ayırmak için kod yaymak vardır.</span><span class="sxs-lookup"><span data-stu-id="f4d27-203">The compiler has to emit code to allocate this array each time.</span></span> <span data-ttu-id="f4d27-204">Derleyici, bilmez çünkü <xref:System.String.Split%2A> yere burada dizisi değiştirilmesine sonraki çağrılar etkileyecek diğer kod tarafından dizi depolar `WriteFormattedDocComment`.</span><span class="sxs-lookup"><span data-stu-id="f4d27-204">That’s because the compiler doesn’t know if <xref:System.String.Split%2A> stores the array somewhere where the array might be modified by other code, which would affect later calls to `WriteFormattedDocComment`.</span></span> <span data-ttu-id="f4d27-205">Çağrı <xref:System.String.Split%2A> ayrıca her satır için bir dize ayırır `text` ve bu işlemi gerçekleştirmek için diğer bellek ayırır.</span><span class="sxs-lookup"><span data-stu-id="f4d27-205">The call to <xref:System.String.Split%2A> also allocates a string for every line in `text` and allocates other memory to perform the operation.</span></span> 
  
 <span data-ttu-id="f4d27-206">`WriteFormattedDocComment` üç çağrı sahip <xref:System.String.TrimStart%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="f4d27-206">`WriteFormattedDocComment` has three calls to the <xref:System.String.TrimStart%2A> method.</span></span> <span data-ttu-id="f4d27-207">İş ve ayırmaları yinelenen iç Döngülerde ikisidir.</span><span class="sxs-lookup"><span data-stu-id="f4d27-207">Two are in inner loops that duplicate work and allocations.</span></span> <span data-ttu-id="f4d27-208">Önemli olan konuya daha da kötüsü, arama yapmak için <xref:System.String.TrimStart%2A> yöntemi bağımsız değişken içermeyen boş bir dizi ayırır (için `params` parametresi) dize sonucu yanı sıra.</span><span class="sxs-lookup"><span data-stu-id="f4d27-208">To make matters worse, calling the <xref:System.String.TrimStart%2A> method with no arguments allocates an empty array (for the `params` parameter) in addition to the string result.</span></span> 
  
 <span data-ttu-id="f4d27-209">Son olarak, bir çağrı yoktur <xref:System.String.Substring%2A> yöntemi genellikle yeni bir dize ayırır.</span><span class="sxs-lookup"><span data-stu-id="f4d27-209">Lastly, there is a call to the <xref:System.String.Substring%2A> method, which usually allocates a new string.</span></span> 
  
 <span data-ttu-id="f4d27-210">**Örneğin 3 düzeltme**</span><span class="sxs-lookup"><span data-stu-id="f4d27-210">**Fix for example 3**</span></span>  
  
 <span data-ttu-id="f4d27-211">Önceki örneklerde, bu ayırma küçük düzenlemelerle düzeltemiyor.</span><span class="sxs-lookup"><span data-stu-id="f4d27-211">Unlike the earlier examples, small edits cannot fix these allocations.</span></span> <span data-ttu-id="f4d27-212">Geri adım, sorun ve farklı yaklaşım gerekir.</span><span class="sxs-lookup"><span data-stu-id="f4d27-212">You need to step back, look at the problem, and approach it differently.</span></span> <span data-ttu-id="f4d27-213">Örneğin, olduğunu fark edeceksiniz bağımsız değişkeni `WriteFormattedDocComment()` kod birçok kısmi dizeler ayırma yerine daha fazla dizin oluşturma yapabilir, yöntemi gerektiren tüm bilgilere sahip bir dizedir.</span><span class="sxs-lookup"><span data-stu-id="f4d27-213">For example, you'll notice that the argument to `WriteFormattedDocComment()` is a string that has all the information that the method needs, so the code could do more indexing instead of allocating many partial strings.</span></span> 
  
 <span data-ttu-id="f4d27-214">Derleyicinin performans takım bu ayırmaları aşağıdakine benzer bir kod ile tackled:</span><span class="sxs-lookup"><span data-stu-id="f4d27-214">The compiler’s performance team tackled all these allocations with code like this:</span></span>  
  
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
  
 <span data-ttu-id="f4d27-215">Ürününün ilk sürümünü `WriteFormattedDocComment()` dizisi ve alt dizelerin kırpılmış bir alt dizesi boş birlikte ayrılan `params` dizisi.</span><span class="sxs-lookup"><span data-stu-id="f4d27-215">The first version of `WriteFormattedDocComment()` allocated an array, several substrings, and a trimmed substring along with an empty `params` array.</span></span> <span data-ttu-id="f4d27-216">Ayrıca kullanıma "/ / / için".</span><span class="sxs-lookup"><span data-stu-id="f4d27-216">It also checked for "///".</span></span> <span data-ttu-id="f4d27-217">Düzeltilen kod yalnızca dizin kullanır ve hiçbir şey ayırır.</span><span class="sxs-lookup"><span data-stu-id="f4d27-217">The revised code uses only indexing and allocates nothing.</span></span> <span data-ttu-id="f4d27-218">Bu dize başlayıp başlamadığını "/ / /" ile görmek için boşluk değildir ve ardından karakter denetler ilk karakteri bulur.</span><span class="sxs-lookup"><span data-stu-id="f4d27-218">It finds the first character that is not white space, and then checks character by character to see if the string starts with "///".</span></span> <span data-ttu-id="f4d27-219">Yeni kod `IndexOfFirstNonWhiteSpaceChar` yerine <xref:System.String.TrimStart%2A> boşluk olmayan karakter oluştuğu (sonra belirtilen başlangıç dizini) ilk dizin dönün.</span><span class="sxs-lookup"><span data-stu-id="f4d27-219">The new code uses `IndexOfFirstNonWhiteSpaceChar` instead of <xref:System.String.TrimStart%2A> to return the first index (after a specified start index) where a non-white-space character occurs.</span></span> <span data-ttu-id="f4d27-220">Düzeltmenin tam değil, ancak benzer düzeltmeleri için eksiksiz bir çözüm uygulamak nasıl görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f4d27-220">The fix is not complete, but you can see how to apply similar fixes for a complete solution.</span></span> <span data-ttu-id="f4d27-221">Bu yaklaşım kod genelindeki uygulayarak, tüm ayırmaları kaldırabilirsiniz `WriteFormattedDocComment()`.</span><span class="sxs-lookup"><span data-stu-id="f4d27-221">By applying this approach throughout the code, you can remove all allocations in `WriteFormattedDocComment()`.</span></span> 
  
 <span data-ttu-id="f4d27-222">**Örnek 4: StringBuilder**</span><span class="sxs-lookup"><span data-stu-id="f4d27-222">**Example 4: StringBuilder**</span></span>  
  
 <span data-ttu-id="f4d27-223">Bu örnekte bir <xref:System.Text.StringBuilder> nesne.</span><span class="sxs-lookup"><span data-stu-id="f4d27-223">This example uses a <xref:System.Text.StringBuilder> object.</span></span> <span data-ttu-id="f4d27-224">Tam tür adı genel türler için aşağıdaki işlevi oluşturur:</span><span class="sxs-lookup"><span data-stu-id="f4d27-224">The following function generates a full type name for generic types:</span></span>  
  
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
  
 <span data-ttu-id="f4d27-225">Odağı oluşturan yeni bir satırda olduğu <xref:System.Text.StringBuilder> örneği.</span><span class="sxs-lookup"><span data-stu-id="f4d27-225">The focus is on the line that creates a new <xref:System.Text.StringBuilder> instance.</span></span> <span data-ttu-id="f4d27-226">Kod için bir ayırma neden `sb.ToString()` ve içinde iç Tahsisatları <xref:System.Text.StringBuilder> uygulaması, ancak denetimi bu ayırmaları dize sonucu istiyorsanız.</span><span class="sxs-lookup"><span data-stu-id="f4d27-226">The code causes an allocation for `sb.ToString()` and internal allocations within the <xref:System.Text.StringBuilder> implementation, but you cannot control those allocations if you want the string result.</span></span> 
  
 <span data-ttu-id="f4d27-227">**Örneğin, 4 Düzelt**</span><span class="sxs-lookup"><span data-stu-id="f4d27-227">**Fix for example 4**</span></span>  
  
 <span data-ttu-id="f4d27-228">Düzeltmek için `StringBuilder` nesne ayırma, nesne önbelleğe alma.</span><span class="sxs-lookup"><span data-stu-id="f4d27-228">To fix the `StringBuilder` object allocation, cache the  object.</span></span> <span data-ttu-id="f4d27-229">Atılan tek bir örnek bile önbelleğe alma performansını önemli ölçüde artırabilir.</span><span class="sxs-lookup"><span data-stu-id="f4d27-229">Even caching a single instance that might get thrown away can improve performance significantly.</span></span> <span data-ttu-id="f4d27-230">Bu işlevin yeni uygulama, yeni ilk ve son satırlar dışında tüm kod atlama.</span><span class="sxs-lookup"><span data-stu-id="f4d27-230">This is the function’s new implementation, omitting all the code except for the new first and last lines:</span></span>  
  
```csharp  
// Constructs a name like "MyType<T1, T2, T3>"  
public string GenerateFullTypeName(string name, int arity)  
{  
    StringBuilder sb = AcquireBuilder();  
    /* Use sb as before */  
    return GetStringAndReleaseBuilder(sb);  
}  
```  
  
 <span data-ttu-id="f4d27-231">Yeni bazı önemli bölümleri `AcquireBuilder()` ve `GetStringAndReleaseBuilder()` İşlevler:</span><span class="sxs-lookup"><span data-stu-id="f4d27-231">The key parts are the new `AcquireBuilder()` and `GetStringAndReleaseBuilder()` functions:</span></span>  
  
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
  
 <span data-ttu-id="f4d27-232">Yeni derleyiciler iş parçacığı kullandığından, bu uygulamaları bir iş parçacığı statik alan kullanır (<xref:System.ThreadStaticAttribute> özniteliği) önbelleğe <xref:System.Text.StringBuilder>, ve büyük olasılıkla bırakmayı `ThreadStatic` bildirimi.</span><span class="sxs-lookup"><span data-stu-id="f4d27-232">Because the new compilers use threading, these implementations use a thread-static field (<xref:System.ThreadStaticAttribute> attribute) to cache the <xref:System.Text.StringBuilder>, and you likely can forgo the `ThreadStatic` declaration.</span></span> <span data-ttu-id="f4d27-233">İş parçacığı statik alanı bu kodu yürüten her bir iş parçacığı için benzersiz bir değer tutar.</span><span class="sxs-lookup"><span data-stu-id="f4d27-233">The thread-static field holds a unique value for each thread that executes this code.</span></span> 
  
 <span data-ttu-id="f4d27-234">`AcquireBuilder()` önbelleğe alınan döndürür <xref:System.Text.StringBuilder> varsa, alan veya önbellek null olarak ayarlamak ve temizlemeden sonra örnek.</span><span class="sxs-lookup"><span data-stu-id="f4d27-234">`AcquireBuilder()` returns the cached <xref:System.Text.StringBuilder> instance if there is one, after clearing it and setting the field or cache to null.</span></span> <span data-ttu-id="f4d27-235">Aksi takdirde, `AcquireBuilder()` yeni bir örneğini oluşturur ve alan veya önbellek kümesi null olarak bırakarak döndürür.</span><span class="sxs-lookup"><span data-stu-id="f4d27-235">Otherwise, `AcquireBuilder()` creates a new instance and returns it, leaving the field or cache set to null.</span></span> 
  
 <span data-ttu-id="f4d27-236">Bitirdiğinizde ile <xref:System.Text.StringBuilder> , çağırmanızı `GetStringAndReleaseBuilder()` dize sonucu elde etmek için Kaydet <xref:System.Text.StringBuilder> örnek alanı veya önbellek ve sonucu döndürür.</span><span class="sxs-lookup"><span data-stu-id="f4d27-236">When you’re done with <xref:System.Text.StringBuilder> , you call `GetStringAndReleaseBuilder()` to get the string result, save the <xref:System.Text.StringBuilder> instance in the field or cache, and then return the result.</span></span> <span data-ttu-id="f4d27-237">Bu kodu tekrar girin ve birden çok oluşturmak için yürütme için mümkündür <xref:System.Text.StringBuilder> (, nadiren gerçekleşir ancak) nesneleri.</span><span class="sxs-lookup"><span data-stu-id="f4d27-237">It is possible for execution to re-enter this code and to create multiple <xref:System.Text.StringBuilder> objects (although that rarely happens).</span></span> <span data-ttu-id="f4d27-238">Yalnızca en son yayımlanan kod kaydeder <xref:System.Text.StringBuilder> daha sonra kullanmak için örneği.</span><span class="sxs-lookup"><span data-stu-id="f4d27-238">The code saves only the last released <xref:System.Text.StringBuilder> instance for later use.</span></span> <span data-ttu-id="f4d27-239">Bu basit bir önbelleğe alma stratejisi, yeni derleyiciler ayırmalarda önemli ölçüde azaldığından.</span><span class="sxs-lookup"><span data-stu-id="f4d27-239">This simple caching strategy significantly reduced allocations in the new compilers.</span></span> <span data-ttu-id="f4d27-240">.NET Framework ve MSBuild ("MSBuild") bölümleri, performansı artırmak için benzer bir teknik kullanın.</span><span class="sxs-lookup"><span data-stu-id="f4d27-240">Parts of the .NET Framework and MSBuild ("MSBuild") use a similar technique to improve performance.</span></span> 
  
 <span data-ttu-id="f4d27-241">Bir boyut sınırına sahip olduğundan bu basit bir önbelleğe alma stratejisi iyi önbellek tasarım uyar.</span><span class="sxs-lookup"><span data-stu-id="f4d27-241">This simple caching strategy adheres to good cache design because it has a size cap.</span></span> <span data-ttu-id="f4d27-242">Ancak, daha fazla bakım maliyetlerini diğer bir deyişle orijinal, artık daha fazla kod yoktur.</span><span class="sxs-lookup"><span data-stu-id="f4d27-242">However, there is more code now than in the original, which means more maintenance costs.</span></span> <span data-ttu-id="f4d27-243">Yalnızca bir performans sorunu buldunuz ve PerfView, gösterilen önbelleğe alma stratejisi benimseyin <xref:System.Text.StringBuilder> ayırmaları olan önemli bir katkıda bulunan.</span><span class="sxs-lookup"><span data-stu-id="f4d27-243">You should adopt the caching strategy only if you’ve found a performance problem, and PerfView has shown that <xref:System.Text.StringBuilder> allocations are a significant contributor.</span></span> 
  
### <a name="linq-and-lambdas"></a><span data-ttu-id="f4d27-244">LINQ ve lambda ifadeleri</span><span class="sxs-lookup"><span data-stu-id="f4d27-244">LINQ and lambdas</span></span>  
<span data-ttu-id="f4d27-245">Dil ile tümleşik sorgu (LINQ), lambda ifadeleri ile birlikte bir üretkenlik özellik örneğidir.</span><span class="sxs-lookup"><span data-stu-id="f4d27-245">Language-Integrated Query (LINQ), in conjunction with lambda expressions, is an example of a productivity feature.</span></span> <span data-ttu-id="f4d27-246">Ancak, kullanımı zaman içerisinde performansı üzerinde önemli bir etkisi olabilir ve kodunuzu yeniden yazmak zorunda bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f4d27-246">However, its use may have a significant impact on performance over time, and you might find you need to rewrite your code.</span></span>
  
 <span data-ttu-id="f4d27-247">**5. örnek: Lambda ifadeleri, liste\<T > ve IEnumerable\<T >**</span><span class="sxs-lookup"><span data-stu-id="f4d27-247">**Example 5: Lambdas, List\<T>, and IEnumerable\<T>**</span></span>  
  
 <span data-ttu-id="f4d27-248">Bu örnekte [LINQ ve işlev stili kod](https://blogs.msdn.com/b/charlie/archive/2007/01/26/anders-hejlsberg-on-linq-and-functional-programming.aspx) adı dizesi verilmiş bir sembol derleyicinin modelinde bulmak için:</span><span class="sxs-lookup"><span data-stu-id="f4d27-248">This example uses [LINQ and functional style code](https://blogs.msdn.com/b/charlie/archive/2007/01/26/anders-hejlsberg-on-linq-and-functional-programming.aspx) to find a symbol in the compiler’s model, given a name string:</span></span>  
  
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
  
 <span data-ttu-id="f4d27-249">Yeni derleyici ve çağrı bunu temel IDE deneyimleri `FindMatchingSymbol()` tek satır kod bu işlevin, birkaç gizli ayırmaları çok sık ve var olan.</span><span class="sxs-lookup"><span data-stu-id="f4d27-249">The new compiler and the IDE experiences built on it call `FindMatchingSymbol()` very frequently, and there are several hidden allocations in this function’s single line of code.</span></span> <span data-ttu-id="f4d27-250">Bu ayırmalar incelemek için ilk işlevin tek satır kod iki çizgiye bölün:</span><span class="sxs-lookup"><span data-stu-id="f4d27-250">To examine those allocations, first split the function’s single line of code into two lines:</span></span>  
  
```csharp  
Func<Symbol, bool> predicate = s => s.Name == name;  
     return symbols.FirstOrDefault(predicate);  
```  
  
 <span data-ttu-id="f4d27-251">İlk satırda [lambda ifadesi](~/docs/csharp/programming-guide/statements-expressions-operators/lambda-expressions.md) `s => s.Name == name` [üzerinden kapatır](https://blogs.msdn.com/b/ericlippert/archive/2003/09/17/53028.aspx) yerel değişken `name`.</span><span class="sxs-lookup"><span data-stu-id="f4d27-251">In the first line, the [lambda expression](~/docs/csharp/programming-guide/statements-expressions-operators/lambda-expressions.md) `s => s.Name == name` [closes over](https://blogs.msdn.com/b/ericlippert/archive/2003/09/17/53028.aspx) the local variable `name`.</span></span> <span data-ttu-id="f4d27-252">Bunun için bir nesne ayırma ek olarak anlamı [temsilci](~/docs/csharp/language-reference/keywords/delegate.md) , `predicate` tutar, kodu değerini yakalayan bir ortam için bir statik sınıf ayırır `name`.</span><span class="sxs-lookup"><span data-stu-id="f4d27-252">This means that in addition to allocating an object for the [delegate](~/docs/csharp/language-reference/keywords/delegate.md) that `predicate` holds, the code allocates a static class to hold the environment that captures the value of `name`.</span></span> <span data-ttu-id="f4d27-253">Derleyici, aşağıdaki gibi bir kod oluşturur:</span><span class="sxs-lookup"><span data-stu-id="f4d27-253">The compiler generates code like the following:</span></span>  
  
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
  
 <span data-ttu-id="f4d27-254">İki `new` ayırmalar (bir ortam sınıfı için) ve bir temsilci için açık şimdi.</span><span class="sxs-lookup"><span data-stu-id="f4d27-254">The two `new` allocations (one for the environment class and one for the delegate) are explicit now.</span></span> 
  
 <span data-ttu-id="f4d27-255">Artık çağrısına bakın `FirstOrDefault`.</span><span class="sxs-lookup"><span data-stu-id="f4d27-255">Now look at the call to `FirstOrDefault`.</span></span> <span data-ttu-id="f4d27-256">Bu genişletme yöntemini <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> türü bir ayırma çok doğurur.</span><span class="sxs-lookup"><span data-stu-id="f4d27-256">This extension method on the <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> type incurs an allocation too.</span></span> <span data-ttu-id="f4d27-257">Çünkü `FirstOrDefault` götüren bir <xref:System.Collections.Generic.IEnumerable%601> nesne, ilk bağımsız değişkeni olarak (hakkında ayrıntılı bilgi için biraz Basitleştirilmiş) aşağıdaki koda çağrı genişletebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="f4d27-257">Because `FirstOrDefault` takes an <xref:System.Collections.Generic.IEnumerable%601> object as its first argument, you can expand the call to the following code (simplified a bit for discussion):</span></span>  
  
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
  
 <span data-ttu-id="f4d27-258">`symbols` Değişken türüne sahip <xref:System.Collections.Generic.List%601>.</span><span class="sxs-lookup"><span data-stu-id="f4d27-258">The `symbols` variable has type <xref:System.Collections.Generic.List%601>.</span></span> <span data-ttu-id="f4d27-259"><xref:System.Collections.Generic.List%601> Koleksiyon türü uygulayan <xref:System.Collections.Generic.IEnumerable%601> ve zekice bir numaralandırıcı tanımlar (<xref:System.Collections.Generic.IEnumerator%601> arabirimi), <xref:System.Collections.Generic.List%601> ile uygulayan bir `struct`.</span><span class="sxs-lookup"><span data-stu-id="f4d27-259">The <xref:System.Collections.Generic.List%601> collection type implements <xref:System.Collections.Generic.IEnumerable%601> and cleverly defines an enumerator (<xref:System.Collections.Generic.IEnumerator%601> interface) that <xref:System.Collections.Generic.List%601> implements with a `struct`.</span></span> <span data-ttu-id="f4d27-260">Bir sınıf yerine bir yapı kullanarak hangi sırayla, çöp toplama performansı etkileyebilir herhangi bir yığın ayırma genellikle kaçının anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="f4d27-260">Using a structure instead of a class means that you usually avoid any heap allocations, which, in turn, can affect garbage collection performance.</span></span> <span data-ttu-id="f4d27-261">Numaralandırıcılar genellikle dil kullanılan `foreach` döngü çağrı yığınındaki döndürülür, numaralandırıcı yapısını kullanır.</span><span class="sxs-lookup"><span data-stu-id="f4d27-261">Enumerators are typically used with the language’s `foreach` loop, which uses the enumerator structure as it is returned on the call stack.</span></span> <span data-ttu-id="f4d27-262">Bir nesne için yer açmak için çağrı yığın işaretçisi artan yaptığı gibi bir yığın ayırma GC etkilemez.</span><span class="sxs-lookup"><span data-stu-id="f4d27-262">Incrementing the call stack pointer to make room for an object does not affect GC the way a heap allocation does.</span></span> 
  
 <span data-ttu-id="f4d27-263">Genişletilmiş durumunda `FirstOrDefault` çağrı, kod çağırmak gereken `GetEnumerator()` üzerinde bir <xref:System.Collections.Generic.IEnumerable%601>.</span><span class="sxs-lookup"><span data-stu-id="f4d27-263">In the case of the expanded `FirstOrDefault` call, the code needs to call `GetEnumerator()` on an <xref:System.Collections.Generic.IEnumerable%601>.</span></span> <span data-ttu-id="f4d27-264">Atama `symbols` için `enumerable` türündeki değişken `IEnumerable<Symbol>` gerçek nesneye bilgileri kaybeder bir <xref:System.Collections.Generic.List%601>.</span><span class="sxs-lookup"><span data-stu-id="f4d27-264">Assigning `symbols` to the `enumerable` variable of type `IEnumerable<Symbol>` loses the information that the actual object is a <xref:System.Collections.Generic.List%601>.</span></span> <span data-ttu-id="f4d27-265">Kod ile Numaralandırıcı getirir olduğunda bunun anlamı `enumerable.GetEnumerator()`, geri döndürülen yapı atamak kutu içine almak .NET Framework sahip `enumerator` değişkeni.</span><span class="sxs-lookup"><span data-stu-id="f4d27-265">This means that when the code fetches the enumerator with `enumerable.GetEnumerator()`, the .NET Framework has to box the returned structure to assign it to the `enumerator` variable.</span></span> 
  
 <span data-ttu-id="f4d27-266">**Örneğin 5 Düzelt**</span><span class="sxs-lookup"><span data-stu-id="f4d27-266">**Fix for example 5**</span></span>  
  
 <span data-ttu-id="f4d27-267">Düzeltme yeniden yazmaktır `FindMatchingSymbol` gibi yine de kısa, okumanız ve anlamanız kolay ve sürdürmek daha kolay olan altı kod satırıyla, tek satırlık bir kod değiştirme:</span><span class="sxs-lookup"><span data-stu-id="f4d27-267">The fix is to rewrite `FindMatchingSymbol` as follows, replacing its single line of code with six lines of code that are still concise, easy to read and understand, and easy to maintain:</span></span>  
  
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
  
 <span data-ttu-id="f4d27-268">Bu kod, LINQ genişletme yöntemleri, lambdalar veya numaralandırıcılar kullanmaz ve edilmedi doğurur.</span><span class="sxs-lookup"><span data-stu-id="f4d27-268">This code doesn’t use LINQ extension methods, lambdas, or enumerators, and it incurs no allocations.</span></span> <span data-ttu-id="f4d27-269">Derleyici, görebilirsiniz çünkü edilmedi olan `symbols` koleksiyonu bir <xref:System.Collections.Generic.List%601> ve sonuçta elde edilen Numaralandırıcı (yapı) yerel bir değişkene kutulama önlemek için doğru tür ile bağlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f4d27-269">There are no allocations because the compiler can see that the `symbols` collection is a <xref:System.Collections.Generic.List%601> and can bind the resulting enumerator (a structure) to a local variable with the right type to avoid boxing.</span></span> <span data-ttu-id="f4d27-270">Bu işlevin özgün sürümle etkileyici gücüyle C# ve .NET Framework'ün üretkenlik harika bir örneği oluştu.</span><span class="sxs-lookup"><span data-stu-id="f4d27-270">The original version of this function was a great example of the expressive power of C# and the productivity of the .NET Framework.</span></span> <span data-ttu-id="f4d27-271">Bu yeni ve daha verimli sürümü bu kalitelerini korumak için karmaşık kodlar eklemeden korur.</span><span class="sxs-lookup"><span data-stu-id="f4d27-271">This new and more efficient version preserves those qualities without adding any complex code to maintain.</span></span> 
  
### <a name="async-method-caching"></a><span data-ttu-id="f4d27-272">Zaman uyumsuz yöntem önbelleğe alma</span><span class="sxs-lookup"><span data-stu-id="f4d27-272">Async method caching</span></span>  
 <span data-ttu-id="f4d27-273">Sonraki örnek, ortak bir sorunu gösterir, önbelleğe alınan sonuçları kullanmaya çalıştığınızda bir [zaman uyumsuz](https://msdn.microsoft.com/library/db854f91-ccef-4035-ae4d-0911fde808c7) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="f4d27-273">The next example shows a common problem when you try to use cached results in an [async](https://msdn.microsoft.com/library/db854f91-ccef-4035-ae4d-0911fde808c7) method.</span></span> 
  
 <span data-ttu-id="f4d27-274">**Örnek 6: zaman uyumsuz yöntemlerde önbelleğe alma**</span><span class="sxs-lookup"><span data-stu-id="f4d27-274">**Example 6: caching in async methods**</span></span>  
  
 <span data-ttu-id="f4d27-275">Söz dizimi ağacı sık yeni C# ve Visual Basic derleyicileri üzerinde oluşturulmuş Visual Studio IDE özelliklerini getirmek ve derleyiciler Visual Studio yanıt saklamak için Bunun yapılması, zaman uyumsuz kullanın.</span><span class="sxs-lookup"><span data-stu-id="f4d27-275">The Visual Studio IDE features built on the new C# and Visual Basic compilers frequently fetch syntax trees, and the compilers use async when doing so to keep Visual Studio responsive.</span></span> <span data-ttu-id="f4d27-276">Sözdizimi ağacı almak için yazabilirsiniz kod ilk hali aşağıdadır:</span><span class="sxs-lookup"><span data-stu-id="f4d27-276">Here’s the first version of the code you might write to get a syntax tree:</span></span>  
  
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
  
 <span data-ttu-id="f4d27-277">Çağırmanın gördüğünüz `GetSyntaxTreeAsync()` örnekleyen bir `Parser`kodunu ayrıştırır ve ardından döndürür bir <xref:System.Threading.Tasks.Task> nesnesi `Task<SyntaxTree>`.</span><span class="sxs-lookup"><span data-stu-id="f4d27-277">You can see that calling `GetSyntaxTreeAsync()` instantiates a `Parser`, parses the code, and then returns a <xref:System.Threading.Tasks.Task> object, `Task<SyntaxTree>`.</span></span> <span data-ttu-id="f4d27-278">Pahalı bölümü ayırma `Parser` örneği ve kod ayrıştırma.</span><span class="sxs-lookup"><span data-stu-id="f4d27-278">The expensive part is allocating the `Parser` instance and parsing the code.</span></span> <span data-ttu-id="f4d27-279">İşlev döndürür bir <xref:System.Threading.Tasks.Task> çağıranlar ayrıştırma işi await ve kullanıcı girişine yanıt olarak UI iş parçacığı ücretsiz.</span><span class="sxs-lookup"><span data-stu-id="f4d27-279">The function returns a <xref:System.Threading.Tasks.Task> so that callers can await the parsing work and free the UI thread to be responsive to user input.</span></span> 
  
 <span data-ttu-id="f4d27-280">Birçok Visual Studio özellikleri zaman ve ayırmaların Kaydet ayrıştırma sonucunu önbelleğe almak için aşağıdaki kodu yazabilirsiniz aynı söz dizimi ağacı almak deneyebilir.</span><span class="sxs-lookup"><span data-stu-id="f4d27-280">Several Visual Studio features might try to get the same syntax tree, so you might write the following code to cache the parsing result to save time and allocations.</span></span> <span data-ttu-id="f4d27-281">Ancak, bu kod, bir ayırma doğurur:</span><span class="sxs-lookup"><span data-stu-id="f4d27-281">However, this code incurs an allocation:</span></span>  
  
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
  
 <span data-ttu-id="f4d27-282">Önbelleğe alma ile yeni kod olduğunu gördüğünüz bir `SyntaxTree` adlı alan `cachedResult`.</span><span class="sxs-lookup"><span data-stu-id="f4d27-282">You see that the new code with caching has a `SyntaxTree` field named `cachedResult`.</span></span> <span data-ttu-id="f4d27-283">Bu alan boş olduğunda `GetSyntaxTreeAsync()` çalışır ve sonuçları önbelleğe kaydeder.</span><span class="sxs-lookup"><span data-stu-id="f4d27-283">When this field is null, `GetSyntaxTreeAsync()` does the work and saves the result in the cache.</span></span> <span data-ttu-id="f4d27-284">`GetSyntaxTreeAsync()` döndürür `SyntaxTree` nesne.</span><span class="sxs-lookup"><span data-stu-id="f4d27-284">`GetSyntaxTreeAsync()` returns the `SyntaxTree` object.</span></span> <span data-ttu-id="f4d27-285">Varsa, sorunu olan bir `async` türünde işlevi `Task<SyntaxTree>`, ve türünde bir değer döndürür `SyntaxTree`, derleyici sonucu tutmak için bir görev ayırmak için kodu yayan (kullanarak `Task<SyntaxTree>.FromResult()`).</span><span class="sxs-lookup"><span data-stu-id="f4d27-285">The problem is that when you have an `async` function of type `Task<SyntaxTree>`, and you return a value of type `SyntaxTree`, the compiler emits code to allocate a Task to hold the result (by using `Task<SyntaxTree>.FromResult()`).</span></span> <span data-ttu-id="f4d27-286">Görevin tamamlandı olarak işaretlenir ve sonuç hemen kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="f4d27-286">The Task is marked as completed, and the result is immediately available.</span></span> <span data-ttu-id="f4d27-287">Yeni derleyicileri için kodunda <xref:System.Threading.Tasks.Task> zaten tamamlanmış nesneler, böylece genellikle bu düzeltmeyle Bu ayırmaları yanıt hızını önemli ölçüde geliştirilmiş oluştu.</span><span class="sxs-lookup"><span data-stu-id="f4d27-287">In the code for the new compilers, <xref:System.Threading.Tasks.Task> objects that were already completed occurred so often that fixing these allocations improved responsiveness noticeably.</span></span> 
  
 <span data-ttu-id="f4d27-288">**Örneğin 6 Düzelt**</span><span class="sxs-lookup"><span data-stu-id="f4d27-288">**Fix for example 6**</span></span>  
  
 <span data-ttu-id="f4d27-289">Tamamlanan kaldırmak için <xref:System.Threading.Tasks.Task> ayırma, görev nesnesi tamamlanmış sonucuyla önbelleğe alabilir:</span><span class="sxs-lookup"><span data-stu-id="f4d27-289">To remove the completed <xref:System.Threading.Tasks.Task> allocation, you can cache the Task object with the completed result:</span></span>  
  
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
  
 <span data-ttu-id="f4d27-290">Bu kod değişiklikleri türde `cachedResult` için `Task<SyntaxTree>` ve kullandığı bir `async` özgün koda göre tutan yardımcı işlevini `GetSyntaxTreeAsync()`.</span><span class="sxs-lookup"><span data-stu-id="f4d27-290">This code changes the type of `cachedResult` to `Task<SyntaxTree>` and employs an `async` helper function that holds the original code from `GetSyntaxTreeAsync()`.</span></span> <span data-ttu-id="f4d27-291">`GetSyntaxTreeAsync()` artık kullanan [null birleşim işleci](../../csharp/language-reference/operators/null-coalescing-operator.md) döndürülecek `cachedResult` null değilse.</span><span class="sxs-lookup"><span data-stu-id="f4d27-291">`GetSyntaxTreeAsync()` now uses the [null coalescing operator](../../csharp/language-reference/operators/null-coalescing-operator.md) to return `cachedResult` if it isn't null.</span></span> <span data-ttu-id="f4d27-292">Varsa `cachedResult` null ise `GetSyntaxTreeAsync()` çağrıları `GetSyntaxTreeUncachedAsync()` ve sonucu önbelleğe alır.</span><span class="sxs-lookup"><span data-stu-id="f4d27-292">If `cachedResult` is null, then `GetSyntaxTreeAsync()` calls `GetSyntaxTreeUncachedAsync()` and caches the result.</span></span> <span data-ttu-id="f4d27-293">Dikkat `GetSyntaxTreeAsync()` çağrısı await değil `GetSyntaxTreeUncachedAsync()` kod normalde yaptığınız gibi.</span><span class="sxs-lookup"><span data-stu-id="f4d27-293">Notice that `GetSyntaxTreeAsync()` doesn’t await the call to `GetSyntaxTreeUncachedAsync()` as the code would normally.</span></span> <span data-ttu-id="f4d27-294">Kullanmayan await anlamına gelir olduğunda `GetSyntaxTreeUncachedAsync()` döndürür, <xref:System.Threading.Tasks.Task> nesnesi `GetSyntaxTreeAsync()` hemen döndürür <xref:System.Threading.Tasks.Task>.</span><span class="sxs-lookup"><span data-stu-id="f4d27-294">Not using await means that when `GetSyntaxTreeUncachedAsync()` returns its <xref:System.Threading.Tasks.Task> object, `GetSyntaxTreeAsync()` immediately returns the <xref:System.Threading.Tasks.Task>.</span></span> <span data-ttu-id="f4d27-295">Artık, önbelleğe alınan sonucu olan bir <xref:System.Threading.Tasks.Task>var. Bu nedenle önbelleğe alınan sonuçları döndürmek için edilmedi.</span><span class="sxs-lookup"><span data-stu-id="f4d27-295">Now, the cached result is a <xref:System.Threading.Tasks.Task>, so there are no allocations to return the cached result.</span></span> 
  
### <a name="additional-considerations"></a><span data-ttu-id="f4d27-296">Ek hususlar</span><span class="sxs-lookup"><span data-stu-id="f4d27-296">Additional considerations</span></span>  
 <span data-ttu-id="f4d27-297">Büyük uygulamalar veya çok miktarda veri işleyen uygulamalar olası sorunlar hakkında birkaç daha fazla noktalar şunlardır.</span><span class="sxs-lookup"><span data-stu-id="f4d27-297">Here are a few more points about potential problems in large apps or apps that process a lot of data.</span></span> 
  
 <span data-ttu-id="f4d27-298">**sözlükler**</span><span class="sxs-lookup"><span data-stu-id="f4d27-298">**Dictionaries**</span></span>  
  
 <span data-ttu-id="f4d27-299">Ancak çok kullanışlı ve verimli kendiliğinden sözlükleri ve sözlükleri ubiquitously birçok programlarda kullanılır.</span><span class="sxs-lookup"><span data-stu-id="f4d27-299">Dictionaries are used ubiquitously in many programs, and though dictionaries are very convenient and inherently efficient.</span></span> <span data-ttu-id="f4d27-300">Ancak, bunlar genellikle uygunsuz bir şekilde kullanılır.</span><span class="sxs-lookup"><span data-stu-id="f4d27-300">However, they’re often used inappropriately.</span></span> <span data-ttu-id="f4d27-301">Visual Studio ve yeni derleyicileri, analiz sözlükleri birçoğu bulunan tek bir öğe veya boş gösterir.</span><span class="sxs-lookup"><span data-stu-id="f4d27-301">In Visual Studio and the new compilers, analysis shows that many of the dictionaries contained a single element or were empty.</span></span> <span data-ttu-id="f4d27-302">Boş bir <xref:System.Collections.Generic.Dictionary%602> on alanları olan ve 48 bayt x x86 yığın üzerinde kapladığı makine.</span><span class="sxs-lookup"><span data-stu-id="f4d27-302">An empty <xref:System.Collections.Generic.Dictionary%602> has ten fields and occupies 48 bytes on the heap on an x86 machine.</span></span> <span data-ttu-id="f4d27-303">Sabit zamanlı arama ile eşleştirme veya ilişkili bir veri yapısı gerektiğinde sözlükleri mükemmel özellikler.</span><span class="sxs-lookup"><span data-stu-id="f4d27-303">Dictionaries are great when you need a mapping or associative data structure with constant-time lookup.</span></span> <span data-ttu-id="f4d27-304">Ancak, yalnızca birkaç öğeleri varsa, bir sözlük kullanarak alanı çok fazla vakit.</span><span class="sxs-lookup"><span data-stu-id="f4d27-304">However, when you have only a few elements, you waste a lot of space by using a dictionary.</span></span> <span data-ttu-id="f4d27-305">Bunun yerine, örneğin, tekrarlayarak bakarak bir `List<KeyValuePair\<K,V>>`, yalnızca hızlı.</span><span class="sxs-lookup"><span data-stu-id="f4d27-305">Instead, for example, you could iteratively look through a `List<KeyValuePair\<K,V>>`, just as fast.</span></span> <span data-ttu-id="f4d27-306">Yalnızca ile veri yükleme ve ardından, (çok yaygın bir düzen) okumak için Sözlük kullanma, bir N(log(N)) arama ile sıralanmış bir diziyi kullanılarak yaklaşık olarak kullandığınız öğeleri sayısına bağlı olarak daha hızlı olabilir.</span><span class="sxs-lookup"><span data-stu-id="f4d27-306">If you use a dictionary only to load it with data and then read from it (a very common pattern), using a sorted array with an N(log(N)) lookup might be nearly as fast, depending on the number of elements you're using.</span></span> 
  
 <span data-ttu-id="f4d27-307">**Yapılar ve sınıflar**</span><span class="sxs-lookup"><span data-stu-id="f4d27-307">**Classes vs. structures**</span></span>  
  
 <span data-ttu-id="f4d27-308">Bir yolla, sınıfları ve yapıları Klasik alanı/saat tradeoff uygulamalarınızı ayarlama için sağlar.</span><span class="sxs-lookup"><span data-stu-id="f4d27-308">In a way, classes and structures provide a classic space/time tradeoff for tuning your apps.</span></span> <span data-ttu-id="f4d27-309">Sınıfları ücret 12 x x86 yükü baytını bile hiçbir alan sahiptirler, ancak bunlar etrafında yalnızca bir sınıf örneğine başvurmak için bir işaretçi aldığından geçirilecek ucuzdur makine.</span><span class="sxs-lookup"><span data-stu-id="f4d27-309">Classes incur 12 bytes of overhead on an x86 machine even if they have no fields, but they are inexpensive to pass around because it only takes a pointer to refer to a class instance.</span></span> <span data-ttu-id="f4d27-310">Yapıları Kutulu değildir, ancak büyük yapılar işlevi bağımsız değişken olarak geçirin veya dönüş değerleri, tüm veri üyelerini yapıları atomik olarak kopyalamak için CPU zaman alır, hiçbir yığın ayırmaları yansıtılmaz.</span><span class="sxs-lookup"><span data-stu-id="f4d27-310">Structures incur no heap allocations if they aren’t boxed, but when you pass large structures as function arguments or return values, it takes CPU time to atomically copy all the data members of the structures.</span></span> <span data-ttu-id="f4d27-311">Yinelenen çağrılar için iade yapıları ve özelliğin değerini aşırı miktarda veri kopyalamayı önlemek için yerel bir değişkende önbellek özellikleri dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="f4d27-311">Watch out for repeated calls to properties that return structures, and cache the property’s value in a local variable to avoid excessive data copying.</span></span> 
  
 <span data-ttu-id="f4d27-312">**Önbellekler**</span><span class="sxs-lookup"><span data-stu-id="f4d27-312">**Caches**</span></span>  
  
 <span data-ttu-id="f4d27-313">Genel bir performans elde sonuçlarını önbelleğe alma ' dir.</span><span class="sxs-lookup"><span data-stu-id="f4d27-313">A common performance trick is to cache results.</span></span> <span data-ttu-id="f4d27-314">Ancak, bir önbellek boyutu büyük harf ya da elden çıkarma İlkesi olmadan bir bellek sızıntısı olabilir.</span><span class="sxs-lookup"><span data-stu-id="f4d27-314">However, a cache without a size cap or disposal policy can be a memory leak.</span></span> <span data-ttu-id="f4d27-315">Çok miktarda bellek önbelleğinde tutun büyük miktarda veri işleme, çöp toplama, önbelleğe alınan aramaları avantajlarını geçersiz kılmak neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="f4d27-315">When processing large amounts of data, if you hold on to a lot of memory in caches, you can cause garbage collection to override the benefits of your cached lookups.</span></span> 
  
 <span data-ttu-id="f4d27-316">Bu makalede, nasıl özellikle büyük sistemleri veya büyük miktarda veri işleyen sistemleri için uygulamanızın yanıt hızını etkileyebilir performans sorununun belirtileri bilincinde olmalısınız almıştık.</span><span class="sxs-lookup"><span data-stu-id="f4d27-316">In this article, we discussed how you should be aware of performance bottleneck symptoms that can affect your app's responsiveness, especially for large systems or systems that process a large amount of data.</span></span> <span data-ttu-id="f4d27-317">Ortak culprits kutulama, dize işlemeleri, LINQ ve lambda, önbellek boyutu sınırı veya çıkarma ilkesini, uygunsuz kullanımdan sözlükleri ve yapıları etrafında geçirme olmadan zaman uyumsuz yöntemlerde önbelleğe almayı içerir.</span><span class="sxs-lookup"><span data-stu-id="f4d27-317">Common culprits include boxing, string manipulations, LINQ and lambda, caching in async methods, caching without a size limit or disposal policy, inappropriate use of dictionaries, and passing around structures.</span></span> <span data-ttu-id="f4d27-318">Uygulamalarınızı ayarlama dört bilgiler göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="f4d27-318">Keep in mind the four facts for tuning your apps:</span></span>  
  
-   <span data-ttu-id="f4d27-319">Yoksa beklenenden önce en iyi duruma getirme – üretken ve problemleri fark, uygulamanızı ayarlama.</span><span class="sxs-lookup"><span data-stu-id="f4d27-319">Don’t prematurely optimize – be productive and tune your app when you spot problems.</span></span> 
  
-   <span data-ttu-id="f4d27-320">Profilleri şekilde yok –, olmayan ölçüm yaptığınız, tahmin.</span><span class="sxs-lookup"><span data-stu-id="f4d27-320">Profiles don’t lie – you’re guessing if you’re not measuring.</span></span> 
  
-   <span data-ttu-id="f4d27-321">İyi Araçlar fark olun – PerfView indirin ve deneyin.</span><span class="sxs-lookup"><span data-stu-id="f4d27-321">Good tools make all the difference – download PerfView and try it out.</span></span> 
  
-   <span data-ttu-id="f4d27-322">Tüm olduğu ayırmaları hakkında – diğer bir deyişle derleyici platformu ekibinden yeni derleyiciler performansını iyileştirme zamanlarının çoğunu burada harcanan.</span><span class="sxs-lookup"><span data-stu-id="f4d27-322">It's all about allocations – that is where the compiler platform team spent most of their time improving the performance of the new compilers.</span></span> 
  
## <a name="see-also"></a><span data-ttu-id="f4d27-323">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f4d27-323">See also</span></span>

- [<span data-ttu-id="f4d27-324">Sunu bu konunun videosu</span><span class="sxs-lookup"><span data-stu-id="f4d27-324">Video of presentation of this topic</span></span>](https://channel9.msdn.com/Events/TechEd/NorthAmerica/2013/DEV-B333)  
- [<span data-ttu-id="f4d27-325">Performans Profili Oluşturma Başlangıç Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="f4d27-325">Beginners Guide to Performance Profiling</span></span>](/visualstudio/profiling/beginners-guide-to-performance-profiling)  
- [<span data-ttu-id="f4d27-326">Performans</span><span class="sxs-lookup"><span data-stu-id="f4d27-326">Performance</span></span>](../../../docs/framework/performance/index.md)  
- [<span data-ttu-id="f4d27-327">.NET Performans İpuçları</span><span class="sxs-lookup"><span data-stu-id="f4d27-327">.NET Performance Tips</span></span>](https://msdn.microsoft.com/library/ms973839.aspx)  
- [<span data-ttu-id="f4d27-328">Windows Phone Performans analiz aracı</span><span class="sxs-lookup"><span data-stu-id="f4d27-328">Windows Phone Performance Analysis Tool</span></span>](https://msdn.microsoft.com/magazine/hh781024.aspx)  
- [<span data-ttu-id="f4d27-329">Visual Studio Profiler uygulama performans sorunlarını bulun</span><span class="sxs-lookup"><span data-stu-id="f4d27-329">Find Application Bottlenecks with Visual Studio Profiler</span></span>](https://msdn.microsoft.com/magazine/cc337887.aspx)  
- [<span data-ttu-id="f4d27-330">Channel 9 PerfView öğreticiler</span><span class="sxs-lookup"><span data-stu-id="f4d27-330">Channel 9 PerfView tutorials</span></span>](https://channel9.msdn.com/Series/PerfView-Tutorial)  
- [<span data-ttu-id="f4d27-331">.NET derleyici Platformu SDK'sı</span><span class="sxs-lookup"><span data-stu-id="f4d27-331">The .NET Compiler Platform SDK</span></span>](../../csharp/roslyn-sdk/index.md)
- [<span data-ttu-id="f4d27-332">github'da dotnet/roslyn depo</span><span class="sxs-lookup"><span data-stu-id="f4d27-332">dotnet/roslyn repo on GitHub</span></span>](https://github.com/dotnet/roslyn)
