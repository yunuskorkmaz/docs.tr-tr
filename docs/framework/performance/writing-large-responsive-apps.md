---
title: "Büyük, Yanıt Veren .NET Framework Uygulamaları Yazma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 123457ac-4223-4273-bb58-3bc0e4957e9d
caps.latest.revision: "25"
author: BillWagner
ms.author: wiwagn
manager: wpickett
ms.workload: wiwagn
ms.openlocfilehash: a33e065d9daa886c27cde31c8f16f9b9eaa45938
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/19/2018
---
# <a name="writing-large-responsive-net-framework-apps"></a><span data-ttu-id="86a46-102">Büyük, Yanıt Veren .NET Framework Uygulamaları Yazma</span><span class="sxs-lookup"><span data-stu-id="86a46-102">Writing Large, Responsive .NET Framework Apps</span></span>
<span data-ttu-id="86a46-103">Bu makalede, büyük miktarda veri dosyaları veya veritabanları gibi işlem uygulamaları büyük .NET Framework uygulamaları veya performansını iyileştirmek için ipuçları verilmektedir.</span><span class="sxs-lookup"><span data-stu-id="86a46-103">This article provides tips for improving the performance of large .NET Framework apps, or apps that process a large amount of data such as files or databases.</span></span> <span data-ttu-id="86a46-104">C# ve Visual Basic derleyicileri yönetilen kod yeniden yazma bu ipuçlarını gelir ve bu makale, C# Derleyici birkaç gerçek örneklerinden içermektedir.</span><span class="sxs-lookup"><span data-stu-id="86a46-104">These tips come from rewriting the C# and Visual Basic compilers in managed code, and this article includes several real examples from the C# compiler.</span></span>  
  
 <span data-ttu-id="86a46-105">.NET Framework uygulamaları oluşturmak için son derece verimli kümesidir.</span><span class="sxs-lookup"><span data-stu-id="86a46-105">The .NET Framework is highly productive for building apps.</span></span>  <span data-ttu-id="86a46-106">Güçlü ve güvenli diller ve zengin bir koleksiyon kitaplıkların uygulama yapı yüksek oranda fruitful olun.</span><span class="sxs-lookup"><span data-stu-id="86a46-106">Powerful and safe languages and a rich collection of libraries make app building highly fruitful.</span></span>  <span data-ttu-id="86a46-107">Ancak, harika verimliliğini sorumluluk gelir.</span><span class="sxs-lookup"><span data-stu-id="86a46-107">However, with great productivity comes responsibility.</span></span>  <span data-ttu-id="86a46-108">.NET Framework'ün tüm güç kullanır ancak gerektiğinde, kodun performansı ayarlamak hazırlanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="86a46-108">You should use all the power of the .NET Framework, but be prepared to tune your code’s performance when needed.</span></span>  
  
## <a name="why-the-new-compiler-performance-applies-to-your-app"></a><span data-ttu-id="86a46-109">Yeni derleyici performans uygulamanıza neden uygular</span><span class="sxs-lookup"><span data-stu-id="86a46-109">Why the new compiler performance applies to your app</span></span>  
 <span data-ttu-id="86a46-110">.NET derleme Platformu ("Roslyn") ekibin C# yeniden yazıldı ve Visual Basic derleyicileri yönetilen kodu modelleme ve kodunu analiz etme, araçları oluşturmaya ve çok daha zengin, kod algılayan deneyimleri Visual Studio'da etkinleştirilmesi için yeni API sağlamak için.</span><span class="sxs-lookup"><span data-stu-id="86a46-110">The .NET Compiler Platform ("Roslyn") team rewrote the C# and Visual Basic compilers in managed code to provide new APIs for modeling and analyzing code, building tools, and enabling much richer, code-aware experiences in Visual Studio.</span></span>  <span data-ttu-id="86a46-111">Derleyicileri yeniden yazma işlemi ve Visual Studio derleme yeni derleyicileri deneyimler büyük herhangi bir .NET Framework uygulama ya da çok miktarda veri işleyen herhangi bir uygulama için geçerli olan yararlı performansı öngörüleri göstermiştir.</span><span class="sxs-lookup"><span data-stu-id="86a46-111">Rewriting the compilers and building Visual Studio experiences on the new compilers revealed useful performance insights that are applicable to any large .NET Framework app or any app that processes a lot of data.</span></span>  <span data-ttu-id="86a46-112">Öngörüler ve örnekler C# Derleyici yararlanmak için derleyicileri hakkında bilmeniz gerek yoktur.</span><span class="sxs-lookup"><span data-stu-id="86a46-112">You don't need to know about compilers to take advantage of the insights and examples from the C# compiler.</span></span>  
  
 <span data-ttu-id="86a46-113">Visual Studio API derleyici tanımlayıcıları ve anahtar sözcükler, sözdizimi tamamlanma listeleri, renklendirme dalgalı çizgiler gibi hatalar, parametre ipuçları, kod sorunları ve kod eylemleri için kullanıcıların hayran, tüm IntelliSense özellikleri oluşturmak için kullanır.</span><span class="sxs-lookup"><span data-stu-id="86a46-113">Visual Studio uses the compiler APIs to build all the IntelliSense features that users love, such as colorization of identifiers and keywords, syntax completion lists, squiggles for errors, parameter tips, code issues, and code actions.</span></span>  <span data-ttu-id="86a46-114">Visual Studio, geliştiricilerin yazarak ve kendi kod değiştirme ve derleyici sürekli kodu geliştiriciler Düzenle modeller sırada Visual Studio yanıt verebilir durumda kalması gereken çalışırken bu Yardım sağlar.</span><span class="sxs-lookup"><span data-stu-id="86a46-114">Visual Studio provides this help while developers are typing and changing their code, and Visual Studio must remain responsive while the compiler continually models the code developers edit.</span></span>  
  
 <span data-ttu-id="86a46-115">Son kullanıcılarınızın uygulamanızla etkileşim kurduklarında, bunlar esnek olmasını bekler.</span><span class="sxs-lookup"><span data-stu-id="86a46-115">When your end users interact with your app, they expect it to be responsive.</span></span>  <span data-ttu-id="86a46-116">Yazarak veya komut işleme hiçbir zaman engellenmelidir.</span><span class="sxs-lookup"><span data-stu-id="86a46-116">Typing or command handling should never be blocked.</span></span>  <span data-ttu-id="86a46-117">Yardım, hızlı bir şekilde pop veya kullanıcı yazmaya devam ederse işlemden vazgeçerlerdi.</span><span class="sxs-lookup"><span data-stu-id="86a46-117">Help should pop up quickly or give up if the user continues typing.</span></span>  <span data-ttu-id="86a46-118">Uygulamanızın kullanıcı Arabirimi iş parçacığı ağır eşitleyerek uygulama olun uzun hesaplamalar ile engelleme kaçınmalısınız.</span><span class="sxs-lookup"><span data-stu-id="86a46-118">Your app should avoid blocking the UI thread with long computations that make the app feel sluggish.</span></span>  
  
 <span data-ttu-id="86a46-119">Roslyn derleyicileri hakkında daha fazla bilgi için ziyaret [dotnet/roslyn](https://github.com/dotnet/roslyn) bağlantıların github'da.</span><span class="sxs-lookup"><span data-stu-id="86a46-119">For more information about Roslyn compilers, visit the [dotnet/roslyn](https://github.com/dotnet/roslyn) repo on GitHub.</span></span>
 <!-- TODO: replace with link to Roslyn conceptual docs once that's published -->
  
## <a name="just-the-facts"></a><span data-ttu-id="86a46-120">Yalnızca bulguları</span><span class="sxs-lookup"><span data-stu-id="86a46-120">Just the Facts</span></span>  
 <span data-ttu-id="86a46-121">Bu bilgiler performans ayarlama yaparken göz önünde bulundurun ve yanıt veren .NET Framework uygulamaları oluşturma.</span><span class="sxs-lookup"><span data-stu-id="86a46-121">Consider these facts when tuning performance and creating responsive .NET Framework apps.</span></span>  
  
### <a name="fact-1-dont-prematurely-optimize"></a><span data-ttu-id="86a46-122">Olgu 1: erken en iyi duruma getirme yok</span><span class="sxs-lookup"><span data-stu-id="86a46-122">Fact 1: Don’t prematurely optimize</span></span>  
 <span data-ttu-id="86a46-123">Olması gerekenden daha karmaşıktır kod yazma hata ayıklama ve maliyetleri polishing bakım doğurur.</span><span class="sxs-lookup"><span data-stu-id="86a46-123">Writing code that is more complex than it needs to be incurs maintenance, debugging, and polishing costs.</span></span>  <span data-ttu-id="86a46-124">Deneyimli programcıları sezgisel bir kavrayın kodlama sorunlarını çözmek ve daha verimli kod yazmak nasıl olması.</span><span class="sxs-lookup"><span data-stu-id="86a46-124">Experienced programmers have an intuitive grasp of how to solve coding problems and write more efficient code.</span></span>  <span data-ttu-id="86a46-125">Ancak, bunlar bazen erken kendi kodu en iyi duruma getirme.</span><span class="sxs-lookup"><span data-stu-id="86a46-125">However, they sometimes prematurely optimize their code.</span></span>  <span data-ttu-id="86a46-126">Örneğin, basit bir dizi yeterli veya yalnızca değerleri recomputing yerine bellek sızıntısı görülebilir karmaşık önbelleğe kullandığınızda bir karma tablosu kullanın.</span><span class="sxs-lookup"><span data-stu-id="86a46-126">For example, they use a hash table when a simple array would suffice, or use complicated caching that may leak memory instead of simply recomputing values.</span></span>  <span data-ttu-id="86a46-127">Bir deneyim Programcı olsa için performans testi ve sorunları bulduğunuzda, kodunuzun analiz edin.</span><span class="sxs-lookup"><span data-stu-id="86a46-127">Even if you’re an experience programmer, you should test for performance and analyze your code when you find issues.</span></span>  
  
### <a name="fact-2-if-youre-not-measuring-youre-guessing"></a><span data-ttu-id="86a46-128">Olgu 2:, ölçüm yaptığınız değil ise, tahmin</span><span class="sxs-lookup"><span data-stu-id="86a46-128">Fact 2: If you’re not measuring, you’re guessing</span></span>  
 <span data-ttu-id="86a46-129">Profilleri ve ölçümleri yer yok.</span><span class="sxs-lookup"><span data-stu-id="86a46-129">Profiles and measurements don’t lie.</span></span>  <span data-ttu-id="86a46-130">Profilleri CPU tam olarak yüklü olduğu ya da disk g/ç üzerinde engellenen göster.</span><span class="sxs-lookup"><span data-stu-id="86a46-130">Profiles show you whether the CPU is fully loaded or whether you’re blocked on disk I/O.</span></span>  <span data-ttu-id="86a46-131">Profilleri söyleyin, size, ne tür ve ne kadar bellek ayırma ve mi, CPU harcama çok zaman içinde [çöp toplama](../../../docs/standard/garbage-collection/index.md) (GC).</span><span class="sxs-lookup"><span data-stu-id="86a46-131">Profiles tell you what kind and how much memory you’re allocating and whether your CPU is spending a lot of time in [garbage collection](../../../docs/standard/garbage-collection/index.md) (GC).</span></span>  
  
 <span data-ttu-id="86a46-132">Anahtar müşteri için performans hedeflerini deneyimleri veya senaryolar uygulamanızı ayarlama ve performansını ölçmek için testleri yazmak gerekir.</span><span class="sxs-lookup"><span data-stu-id="86a46-132">You should set performance goals for key customer experiences or scenarios in your app and write tests to measure performance.</span></span>  <span data-ttu-id="86a46-133">Başarısız olan testleri bilimsel yöntemi uygulayarak araştırın: profillerini kullanmak için size yol, ne sorun olabilir, hypothesize ve varsayımınızın bir denemeyi ile test veya kod değişikliği.</span><span class="sxs-lookup"><span data-stu-id="86a46-133">Investigate failing tests by applying the scientific method: use profiles to guide you, hypothesize what the issue might be, and test your hypothesis with an experiment or code change.</span></span>  <span data-ttu-id="86a46-134">Performans gerileme neden değişiklikleri yalıtabilirsiniz şekilde normal test ile zamanla temel performans ölçümleri oluşturun.</span><span class="sxs-lookup"><span data-stu-id="86a46-134">Establish baseline performance measurements over time with regular testing, so you can isolate changes that cause regressions in performance.</span></span>  <span data-ttu-id="86a46-135">Sıkı bir şekilde performans iş yaklaşan tarafından gerekmeyen kod güncelleştirmeleriyle zaman kaçının.</span><span class="sxs-lookup"><span data-stu-id="86a46-135">By approaching performance work in a rigorous way, you’ll avoid wasting time with code updates you don’t need.</span></span>  
  
### <a name="fact-3-good-tools-make-all-the-difference"></a><span data-ttu-id="86a46-136">Olgu 3: İyi araçları tüm fark kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="86a46-136">Fact 3: Good tools make all the difference</span></span>  
 <span data-ttu-id="86a46-137">Hızlı bir şekilde büyük performans sorunlarını (CPU, bellek veya disk) ve bu performans sorunu neden kodu bulun Yardım ayrıntıya iyi araçları sağlar.</span><span class="sxs-lookup"><span data-stu-id="86a46-137">Good tools let you drill quickly into the biggest performance issues (CPU, memory, or disk) and help you locate the code that causes those bottlenecks.</span></span>  <span data-ttu-id="86a46-138">Microsoft çeşitli performans araçları gibi birlikte gelen [Visual Studio profil oluşturucu](/visualstudio/profiling/beginners-guide-to-performance-profiling), [Windows Phone çözümleme aracı](http://msdn.microsoft.com/library/e67e3199-ea43-4d14-ab7e-f7f19266253f), ve [PerfView](http://www.microsoft.com/download/details.aspx?id=28567).</span><span class="sxs-lookup"><span data-stu-id="86a46-138">Microsoft ships a variety of performance tools such as [Visual Studio Profiler](/visualstudio/profiling/beginners-guide-to-performance-profiling), [Windows Phone Analysis Tool](http://msdn.microsoft.com/library/e67e3199-ea43-4d14-ab7e-f7f19266253f), and [PerfView](http://www.microsoft.com/download/details.aspx?id=28567).</span></span>  
  
 <span data-ttu-id="86a46-139">PerfView disk g/ç gibi ayrıntılı sorunları odaklanmak, GC olayları ve bellek yardımcı olan ücretsiz ve son derece güçlü bir araçtır.</span><span class="sxs-lookup"><span data-stu-id="86a46-139">PerfView is a free and amazingly powerful tool that helps you focus on deep issues such as disk I/O, GC events, and memory.</span></span>  <span data-ttu-id="86a46-140">Performansla ilgili yakalayabilirsiniz [Windows için olay izleme](../../../docs/framework/wcf/samples/etw-tracing.md) (ETW) olayları ve görünüm kolayca uygulama başına, işlem başına, yığın başına ve başına iş parçacığı bilgileri.</span><span class="sxs-lookup"><span data-stu-id="86a46-140">You can capture performance-related [Event Tracing for Windows](../../../docs/framework/wcf/samples/etw-tracing.md) (ETW) events and view easily per app, per process, per stack, and per thread information.</span></span>  <span data-ttu-id="86a46-141">PerfView uygulamanızı ayırır, bellek ve hangi işlevleri veya çağrı yığınları ne kadar bellek ayırmaları katkıda ne kadar ve ne tür gösterir.</span><span class="sxs-lookup"><span data-stu-id="86a46-141">PerfView shows you how much and what kind of memory your app allocates, and which functions or call stacks contribute how much to the memory allocations.</span></span> <span data-ttu-id="86a46-142">Ayrıntılar için bkz: zengin Yardım konuları, gösterileri ve aracıyla dahil videoları (gibi [PerfView öğreticileri](http://channel9.msdn.com/Series/PerfView-Tutorial) Channel 9).</span><span class="sxs-lookup"><span data-stu-id="86a46-142">For details, see the rich help topics, demos, and videos included with the tool (such as the [PerfView tutorials](http://channel9.msdn.com/Series/PerfView-Tutorial) on Channel 9).</span></span>  
  
### <a name="fact-4-its-all-about-allocations"></a><span data-ttu-id="86a46-143">Olgu 4: Tüm ayırmaları hakkında olduğu</span><span class="sxs-lookup"><span data-stu-id="86a46-143">Fact 4: It’s all about allocations</span></span>  
 <span data-ttu-id="86a46-144">Bu esnek bir derleme düşünebilirsiniz .NET Framework uygulaması Kabarcık sıralama yerine Hızlı sıralama kullanarak gibi tüm algoritmalar hakkında ancak bu durumda değil.</span><span class="sxs-lookup"><span data-stu-id="86a46-144">You might think that building a responsive .NET Framework app is all about algorithms, such as using quick sort instead of bubble sort, but that's not the case.</span></span>  <span data-ttu-id="86a46-145">Özellikle uygulamanız çok büyük olduğunda veya büyük miktarlarda verinin işler esnek bir uygulaması oluşturmanın en büyük faktörü bellek ayırma olduğu.</span><span class="sxs-lookup"><span data-stu-id="86a46-145">The biggest factor in building a responsive app is allocating memory, especially when your app is very large or processes large amounts of data.</span></span>  
  
 <span data-ttu-id="86a46-146">Neredeyse tüm iş esnek IDE oluşturmak için yeni derleyici API'leri ile karşılaştığında ayırmaları önleme ve önbelleğe alma stratejilerine yönetme dahil.</span><span class="sxs-lookup"><span data-stu-id="86a46-146">Almost all the work to build responsive IDE experiences with the new compiler APIs involved avoiding allocations and managing caching strategies.</span></span>  <span data-ttu-id="86a46-147">PerfView izlemeleri yeni C# ve Visual Basic derleyicileri performansını nadiren CPU'ya olmadığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="86a46-147">PerfView traces show that the performance of the new C# and Visual Basic compilers is rarely CPU bound.</span></span>  <span data-ttu-id="86a46-148">Oluşturulan kod yayma veya derleyicileri meta verileri okuma binlerce veya kod satırı milyonlarca yüzlerce okunurken bağlı g/ç olabilir.</span><span class="sxs-lookup"><span data-stu-id="86a46-148">The compilers can be I/O bound when reading hundreds of thousands or millions of lines of code, reading metadata, or emitting generated code.</span></span>  <span data-ttu-id="86a46-149">Kullanıcı Arabirimi iş parçacığı gecikmeler neredeyse tüm atık toplama nedeniyle ' dir.</span><span class="sxs-lookup"><span data-stu-id="86a46-149">The UI thread delays are nearly all due to garbage collection.</span></span>  <span data-ttu-id="86a46-150">.NET Framework GC yüksek performans için ayarlanmış ve uygulama kodu eşzamanlı olarak çalışırken çalışmasını çoğunu yapar.</span><span class="sxs-lookup"><span data-stu-id="86a46-150">The .NET Framework GC is highly tuned for performance and does much of its work concurrently while app code executes.</span></span>  <span data-ttu-id="86a46-151">Ancak, tek bir ayırma pahalı bir tetikleyebilir [gen2](../../../docs/standard/garbage-collection/fundamentals.md) koleksiyon, tüm iş parçacıklarını durdurma.</span><span class="sxs-lookup"><span data-stu-id="86a46-151">However, a single allocation can trigger an expensive [gen2](../../../docs/standard/garbage-collection/fundamentals.md) collection, stopping all threads.</span></span>  
  
## <a name="common-allocations-and-examples"></a><span data-ttu-id="86a46-152">Ortak ayırma ve örnekler</span><span class="sxs-lookup"><span data-stu-id="86a46-152">Common allocations and examples</span></span>  
 <span data-ttu-id="86a46-153">Bu bölümdeki örnek ifadeler küçük görünür ayırmaları gizli.</span><span class="sxs-lookup"><span data-stu-id="86a46-153">The example expressions in this section have hidden allocations that appear small.</span></span>  <span data-ttu-id="86a46-154">Ancak, büyük uygulama yeterli kez ifadeleri yürütülürse, megabayt, hatta gigabayt cinsinden ayırmalarının yüzlerce nedenleri olabilir.</span><span class="sxs-lookup"><span data-stu-id="86a46-154">However, if a large app executes the expressions enough times, they can causes hundreds of megabytes, even gigabytes, of allocations.</span></span>  <span data-ttu-id="86a46-155">Bir geliştiricinin bellek tahsis düzenleyicisinde yazarak benzetimli ve senaryoları yazarak odaklanmak için performans takım öncülük Örneğin, bir dakikalık sınamaları.</span><span class="sxs-lookup"><span data-stu-id="86a46-155">For example, one-minute tests that simulated a developer’s typing in the editor allocated gigabytes of memory and led the performance team to focus on typing scenarios.</span></span>  
  
### <a name="boxing"></a><span data-ttu-id="86a46-156">Kutulama</span><span class="sxs-lookup"><span data-stu-id="86a46-156">Boxing</span></span>  
 <span data-ttu-id="86a46-157">[Kutulama](~/docs/csharp/programming-guide/types/boxing-and-unboxing.md) normalde değer türleri yığında Canlı veya nesneyi Sarmalanan veri yapılarını oluşur.</span><span class="sxs-lookup"><span data-stu-id="86a46-157">[Boxing](~/docs/csharp/programming-guide/types/boxing-and-unboxing.md) occurs when value types that normally live on the stack or in data structures are wrapped in an object.</span></span>  <span data-ttu-id="86a46-158">Diğer bir deyişle, verileri tutmak için bir nesne ayrılamadı ve ardından bir işaretçi nesnesine dönün.</span><span class="sxs-lookup"><span data-stu-id="86a46-158">That is, you allocate an object to hold the data, and then return a pointer to the object.</span></span>  <span data-ttu-id="86a46-159">.NET Framework bazen değerleri bir yöntem veya bir depolama konumu türünün imza nedeniyle kutuları.</span><span class="sxs-lookup"><span data-stu-id="86a46-159">The .NET Framework sometimes boxes values due to the signature of a method or the type of a storage location.</span></span>  <span data-ttu-id="86a46-160">Değer türü içinde bir nesne nedenler bellek ayırma kaydırma.</span><span class="sxs-lookup"><span data-stu-id="86a46-160">Wrapping a value type in an object causes memory allocation.</span></span>  <span data-ttu-id="86a46-161">Birçok kutulama işlemleri, megabayt veya gigabayt uygulamanızı daha fazla GC'ler sebep ve uygulamanızın ayırmalarının katkıda bulunabilir.</span><span class="sxs-lookup"><span data-stu-id="86a46-161">Many boxing operations can contribute megabytes or gigabytes of allocations to your app, which means that your app will cause more GCs.</span></span> <span data-ttu-id="86a46-162">.NET Framework ve dil derleyicileri kutulama mümkün olduğunda kaçının ancak bazen az beklediğiniz olur.</span><span class="sxs-lookup"><span data-stu-id="86a46-162">The .NET Framework and the language compilers avoid boxing when possible, but sometimes it happens when you least expect it.</span></span>  
  
 <span data-ttu-id="86a46-163">PerfView kutulama görmek için bir izleme açın ve uygulamanızın işlem adı altında GC yığın ayırma yığında bakın (unutmayın, PerfView raporları tüm işlemleri).</span><span class="sxs-lookup"><span data-stu-id="86a46-163">To see boxing in PerfView, open a trace and look at GC Heap Alloc Stacks under your app’s process name (remember, PerfView reports on all processes).</span></span>  <span data-ttu-id="86a46-164">Türleri gibi görürseniz <xref:System.Int32?displayProperty=nameWithType> ve <xref:System.Char?displayProperty=nameWithType> ayırmaları altında değer türleri kutulama.</span><span class="sxs-lookup"><span data-stu-id="86a46-164">If you see types like <xref:System.Int32?displayProperty=nameWithType> and <xref:System.Char?displayProperty=nameWithType> under allocations, you are boxing value types.</span></span>  <span data-ttu-id="86a46-165">Bu türlerinden birini seçerek Kutulu işlevler ve yığınları gösterir.</span><span class="sxs-lookup"><span data-stu-id="86a46-165">Choosing one of these types will show the stacks and functions in which they are boxed.</span></span>  
  
 <span data-ttu-id="86a46-166">**Örnek 1: dize yöntemlerini ve değer türü bağımsız değişkenleri**</span><span class="sxs-lookup"><span data-stu-id="86a46-166">**Example 1: string methods and value type arguments**</span></span>  
  
 <span data-ttu-id="86a46-167">Bu örnek kod, büyük olasılıkla gereksiz ve aşırı kutulama gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="86a46-167">This sample code illustrates potentially unnecessary and excessive boxing:</span></span>  
  
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
  
 <span data-ttu-id="86a46-168">Bu kod bir uygulama çağırabilir günlük işlevini sağlar `Log` sık, belki de kez milyonlarca işlev.</span><span class="sxs-lookup"><span data-stu-id="86a46-168">This code provides logging functionality, so an app may call the `Log` function frequently, maybe millions of times.</span></span>  <span data-ttu-id="86a46-169">Sorunu olan çağrısı `string.Format` çözümler <xref:System.String.Format%28System.String%2CSystem.Object%2CSystem.Object%29> aşırı yükleme.</span><span class="sxs-lookup"><span data-stu-id="86a46-169">The problem is that the call to `string.Format` resolves to the <xref:System.String.Format%28System.String%2CSystem.Object%2CSystem.Object%29> overload.</span></span>  
  
 <span data-ttu-id="86a46-170">.NET Framework kutusuna bu aşırı gerektirir `int` bu yöntem çağrısı geçirilecek nesneleri içine değerleri.</span><span class="sxs-lookup"><span data-stu-id="86a46-170">This overload requires the .NET Framework to box the `int` values into objects to pass them to this method call.</span></span>  <span data-ttu-id="86a46-171">Kısmi bir düzeltme çağırmaktır `id.ToString()` ve `size.ToString()` ve geçişi için (hangi nesnelerin olduğunu) tüm dizeleri `string.Format` çağırın.</span><span class="sxs-lookup"><span data-stu-id="86a46-171">A partial fix is to call `id.ToString()` and `size.ToString()` and pass all strings (which are objects) to the `string.Format` call.</span></span>  <span data-ttu-id="86a46-172">Çağırma `ToString()` ayırma içinde yine de gerçekleşir ancak bu bir dize tahsis `string.Format`.</span><span class="sxs-lookup"><span data-stu-id="86a46-172">Calling `ToString()` does allocate a string, but that allocation will happen anyway inside `string.Format`.</span></span>  
  
 <span data-ttu-id="86a46-173">Bu bu temel düşünebilirsiniz çağrısı `string.Format` yalnızca dize birleştirme olduğundan, bunun yerine bu kod yazabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="86a46-173">You might consider that this basic call to `string.Format` is just string concatenation, so you might write this code instead:</span></span>  
  
```csharp  
var s = id.ToString() + ':' + size.ToString();  
```  
  
 <span data-ttu-id="86a46-174">Ancak, bu kod satırı kutulama ayırma tanıtır için derler olduğundan <xref:System.String.Concat%28System.Object%2CSystem.Object%2CSystem.Object%29>.</span><span class="sxs-lookup"><span data-stu-id="86a46-174">However, that line of code introduces a boxing allocation because it compiles to <xref:System.String.Concat%28System.Object%2CSystem.Object%2CSystem.Object%29>.</span></span>  <span data-ttu-id="86a46-175">.NET Framework çağırmak için değişmez değer karakter kutusunda gerekir`Concat`</span><span class="sxs-lookup"><span data-stu-id="86a46-175">The .NET Framework must box the character literal to invoke `Concat`</span></span>  
  
 <span data-ttu-id="86a46-176">**Örneğin 1 Düzelt**</span><span class="sxs-lookup"><span data-stu-id="86a46-176">**Fix for example 1**</span></span>  
  
 <span data-ttu-id="86a46-177">Tam düzeltme basit bir işlemdir.</span><span class="sxs-lookup"><span data-stu-id="86a46-177">The complete fix is simple.</span></span>  <span data-ttu-id="86a46-178">Yalnızca karakter değişmez değeri bir dize değişmez değer dizeleri nesneler olduğundan, hiçbir kutulama doğurur değiştirin:</span><span class="sxs-lookup"><span data-stu-id="86a46-178">Just replace the character literal with a string literal, which incurs no boxing because strings are already objects:</span></span>  
  
```csharp  
var s = id.ToString() + ":" + size.ToString();  
```  
  
 <span data-ttu-id="86a46-179">**Örnek 2: enum kutulama**</span><span class="sxs-lookup"><span data-stu-id="86a46-179">**Example 2: enum boxing**</span></span>  
  
 <span data-ttu-id="86a46-180">Bu örnekte sık kullanılan nedeniyle yeni C# ve Visual Basic derleyicileri tahsisini sözlük arama işlemlerinde özellikle numaralandırma türlerinin çok büyük miktarlarda sorumlu.</span><span class="sxs-lookup"><span data-stu-id="86a46-180">This example was responsible for a huge amount of allocation in the new C# and Visual Basic compilers due to frequent use of enumeration types, especially in dictionary lookup operations.</span></span>  
  
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
  
 <span data-ttu-id="86a46-181">Bu sorun çok ince oluşur.</span><span class="sxs-lookup"><span data-stu-id="86a46-181">This problem is very subtle.</span></span>  <span data-ttu-id="86a46-182">PerfView bu olarak rapor <xref:System.Enum.GetHashCode> yöntemi uygulama nedeniyle numaralandırma türü temeldeki gösterimini kutular çünkü kutulama.</span><span class="sxs-lookup"><span data-stu-id="86a46-182">PerfView would report this as <xref:System.Enum.GetHashCode> boxing because the method boxes the underlying representation of the enumeration type, for implementation reasons.</span></span>  <span data-ttu-id="86a46-183">İçinde PerfView yakından bakarsanız, her çağrı için iki kutulama ayırmaları görebilirsiniz <xref:System.Enum.GetHashCode>.</span><span class="sxs-lookup"><span data-stu-id="86a46-183">If you look closely in PerfView, you may see two boxing allocations for each call to <xref:System.Enum.GetHashCode>.</span></span>   <span data-ttu-id="86a46-184">Derleyici bir ekler ve .NET Framework diğer ekler.</span><span class="sxs-lookup"><span data-stu-id="86a46-184">The compiler inserts one, and the .NET Framework inserts the other.</span></span>  
  
 <span data-ttu-id="86a46-185">**Örneğin 2 düzeltme**</span><span class="sxs-lookup"><span data-stu-id="86a46-185">**Fix for example 2**</span></span>  
  
 <span data-ttu-id="86a46-186">Temel alınan gösterimi çağırmadan önce atama tarafından her iki ayırma kolayca önleyebilirsiniz <xref:System.Enum.GetHashCode>:</span><span class="sxs-lookup"><span data-stu-id="86a46-186">You can easily avoid both allocations by casting to the underlying representation before calling <xref:System.Enum.GetHashCode>:</span></span>  
  
```csharp  
((int)color).GetHashCode()  
```  
  
 <span data-ttu-id="86a46-187">Kutulama Numaralandırma türleri üzerinde başka bir ortak kaynağı <xref:System.Enum.HasFlag%28System.Enum%29?displayProperty=nameWithType> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="86a46-187">Another common source of boxing on enumeration types is the <xref:System.Enum.HasFlag%28System.Enum%29?displayProperty=nameWithType> method.</span></span>  <span data-ttu-id="86a46-188">Geçirilen bağımsız değişken <xref:System.Enum.HasFlag%28System.Enum%29> Kutulu gerekir.</span><span class="sxs-lookup"><span data-stu-id="86a46-188">The argument passed to <xref:System.Enum.HasFlag%28System.Enum%29> has to be boxed.</span></span>  <span data-ttu-id="86a46-189">Çoğu durumda, çağrıları değiştirme <xref:System.Enum.HasFlag%28System.Enum%29?displayProperty=nameWithType> bit düzeyinde bir test ile daha basit ve ayırma boş olur.</span><span class="sxs-lookup"><span data-stu-id="86a46-189">In most cases, replacing calls to <xref:System.Enum.HasFlag%28System.Enum%29?displayProperty=nameWithType> with a bitwise test is simpler and allocation-free.</span></span>  
  
 <span data-ttu-id="86a46-190">İlk performans olgu unutmayın (diğer bir deyişle, erken İyileştir yok) ve bu şekilde tüm kodunuzu yeniden yazma işlemi başlatma.</span><span class="sxs-lookup"><span data-stu-id="86a46-190">Keep the first performance fact in mind (that is, don’t prematurely optimize) and don’t start rewriting all your code in this way.</span></span>    <span data-ttu-id="86a46-191">Bu kutulama maliyetinden unutmayın, ancak yalnızca uygulama profili oluşturma ve etkin noktalar bulma sonra kodunuzu değiştirmek.</span><span class="sxs-lookup"><span data-stu-id="86a46-191">Be aware of these boxing costs, but change your code only after profiling your app and finding the hot spots.</span></span>  
  
### <a name="strings"></a><span data-ttu-id="86a46-192">Dizeler</span><span class="sxs-lookup"><span data-stu-id="86a46-192">Strings</span></span>  
 <span data-ttu-id="86a46-193">Dize işlemeleri ayırmaları için büyük culprits bazıları ve bunlar genellikle PerfView içinde ilk beş ayırma gösterilir.</span><span class="sxs-lookup"><span data-stu-id="86a46-193">String manipulations are some of the biggest culprits for allocations, and they often show up in PerfView in the top five allocations.</span></span>  <span data-ttu-id="86a46-194">Programları dizeleri serileştirme, JSON ve REST API'lerini kullanır.</span><span class="sxs-lookup"><span data-stu-id="86a46-194">Programs use strings for serialization, JSON, and REST APIs.</span></span>  <span data-ttu-id="86a46-195">Numaralandırma türleri kullanamadığında sistemleriyle birlikte için programlı sabitleri dizelerini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="86a46-195">You can use strings as programmatic constants for interoperating with systems when you can’t use enumeration types.</span></span>  <span data-ttu-id="86a46-196">Çağrılar, profil dizeleri performans yüksek oranda etkileyen göstermediğinde arayın <xref:System.String> gibi yöntemler <xref:System.String.Format%2A>, <xref:System.String.Concat%2A>, <xref:System.String.Split%2A>, <xref:System.String.Join%2A>, <xref:System.String.Substring%2A>ve benzeri.</span><span class="sxs-lookup"><span data-stu-id="86a46-196">When your profiling shows that strings are highly affecting performance, look for calls to <xref:System.String> methods such as <xref:System.String.Format%2A>, <xref:System.String.Concat%2A>, <xref:System.String.Split%2A>, <xref:System.String.Join%2A>, <xref:System.String.Substring%2A>, and so on.</span></span>  <span data-ttu-id="86a46-197">Kullanarak <xref:System.Text.StringBuilder> bir dize oluşturma çok sayıda parça yardımcı olur, ancak bile ayırma maliyetini önlemek için <xref:System.Text.StringBuilder> nesne yönetmeniz gereken bir performans sorunu hale.</span><span class="sxs-lookup"><span data-stu-id="86a46-197">Using <xref:System.Text.StringBuilder> to avoid the cost of creating one string from many pieces helps, but even allocating the <xref:System.Text.StringBuilder> object might become a bottleneck that you need to manage.</span></span>  
  
 <span data-ttu-id="86a46-198">**Örnek 3: dize işlemleri**</span><span class="sxs-lookup"><span data-stu-id="86a46-198">**Example 3: string operations**</span></span>  
  
 <span data-ttu-id="86a46-199">C# Derleyici biçimlendirilmiş XML Belge açıklama metni yazar bu kodunu döndürdü:</span><span class="sxs-lookup"><span data-stu-id="86a46-199">The C# compiler had this code that writes the text of a formatted XML doc comment:</span></span>  
  
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
  
 <span data-ttu-id="86a46-200">Bu kod dize düzenlemesi çok mu görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="86a46-200">You can see that this code does a lot of string manipulation.</span></span>  <span data-ttu-id="86a46-201">Kod kitaplığı yöntemi satırları denetlemek için boşluk, kırpma için ayrı dizeleri, bölmek için kullanır. olup olmadığını bağımsız değişkeni `text` bir XML belge açıklaması ve satırlarından alt dizeler ayıklamak için.</span><span class="sxs-lookup"><span data-stu-id="86a46-201">The code uses library methods to split lines into separate strings, to trim white space, to check whether the argument `text` is an XML documentation comment, and to extract substrings from lines.</span></span>  
  
 <span data-ttu-id="86a46-202">İçinde ilk satırda `WriteFormattedDocComment`, `text.Split` çağrısı her çağrıldığında bu yeni üç öğeli bir dizi bağımsız değişken olarak ayırır.</span><span class="sxs-lookup"><span data-stu-id="86a46-202">On the first line inside `WriteFormattedDocComment`, the `text.Split` call allocates a new three-element array as the argument every time it’s called.</span></span>  <span data-ttu-id="86a46-203">Bu dizinin her zaman ayırmak için kod yaymak üzere derleyici sahiptir.</span><span class="sxs-lookup"><span data-stu-id="86a46-203">The compiler has to emit code to allocate this array each time.</span></span>  <span data-ttu-id="86a46-204">Derleyici, bilmiyor çünkü <xref:System.String.Split%2A> yere Burada dizi değiştirilmesi daha sonraki çağrıları etkileyecek diğer kodu tarafından dizi depolar `WriteFormattedDocComment`.</span><span class="sxs-lookup"><span data-stu-id="86a46-204">That’s because the compiler doesn’t know if <xref:System.String.Split%2A> stores the array somewhere where the array might be modified by other code, which would affect later calls to `WriteFormattedDocComment`.</span></span>  <span data-ttu-id="86a46-205">Çağrı <xref:System.String.Split%2A> ayrıca her satır için bir dize ayırır `text` ve işlemi gerçekleştirmek için başka bir bellek ayırır.</span><span class="sxs-lookup"><span data-stu-id="86a46-205">The call to <xref:System.String.Split%2A> also allocates a string for every line in `text` and allocates other memory to perform the operation.</span></span>  
  
 <span data-ttu-id="86a46-206">`WriteFormattedDocComment`üç çağrı sahip <xref:System.String.TrimStart%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="86a46-206">`WriteFormattedDocComment` has three calls to the <xref:System.String.TrimStart%2A> method.</span></span>  <span data-ttu-id="86a46-207">İş ve ayırmaları yinelenen iç Döngülerde ikisidir.</span><span class="sxs-lookup"><span data-stu-id="86a46-207">Two are in inner loops that duplicate work and allocations.</span></span>  <span data-ttu-id="86a46-208">Önemlidir daha da kötüsü, arama yapmak için <xref:System.String.TrimStart%2A> yöntemi bağımsız değişken içermeyen boş bir dizi ayırır (için `params` parametresi) dize sonucu yanı sıra.</span><span class="sxs-lookup"><span data-stu-id="86a46-208">To make matters worse, calling the <xref:System.String.TrimStart%2A> method with no arguments allocates an empty array (for the `params` parameter) in addition to the string result.</span></span>  
  
 <span data-ttu-id="86a46-209">Son olarak, bir arama var. <xref:System.String.Substring%2A> genellikle yeni bir dize ayırır yöntemi.</span><span class="sxs-lookup"><span data-stu-id="86a46-209">Lastly, there is a call to the <xref:System.String.Substring%2A> method, which usually allocates a new string.</span></span>  
  
 <span data-ttu-id="86a46-210">**Örneğin 3 Düzelt**</span><span class="sxs-lookup"><span data-stu-id="86a46-210">**Fix for example 3**</span></span>  
  
 <span data-ttu-id="86a46-211">Önceki örneklerin aksine bu ayırmaları küçük düzenlemeler düzeltilemiyor.</span><span class="sxs-lookup"><span data-stu-id="86a46-211">Unlike the earlier examples, small edits cannot fix these allocations.</span></span>  <span data-ttu-id="86a46-212">Geri adım, sorun ve farklı şekilde yaklaşır gerekir.</span><span class="sxs-lookup"><span data-stu-id="86a46-212">You need to step back, look at the problem, and approach it differently.</span></span>  <span data-ttu-id="86a46-213">Örneğin, olduğunu fark edeceksiniz bağımsız değişkeni `WriteFormattedDocComment()` kodu birçok kısmi dizeler ayırma yerine daha fazla dizin oluşturma yapabilirsiniz, böylece yöntemi gerektiren tüm bilgilere sahip bir dizedir.</span><span class="sxs-lookup"><span data-stu-id="86a46-213">For example, you'll notice that the argument to `WriteFormattedDocComment()` is a string that has all the information that the method needs, so the code could do more indexing instead of allocating many partial strings.</span></span>  
  
 <span data-ttu-id="86a46-214">Derleyicinin performans takım bu ayırma aşağıdakine benzer bir kod ile tackled:</span><span class="sxs-lookup"><span data-stu-id="86a46-214">The compiler’s performance team tackled all these allocations with code like this:</span></span>  
  
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
  
 <span data-ttu-id="86a46-215">İlk sürümü `WriteFormattedDocComment()` bir dizi, birkaç alt dizeler ve boş bir birlikte bölünen substring ayrılan `params` dizi.</span><span class="sxs-lookup"><span data-stu-id="86a46-215">The first version of `WriteFormattedDocComment()` allocated an array, several substrings, and a trimmed substring along with an empty `params` array.</span></span>  <span data-ttu-id="86a46-216">Bu ayrıca kontrol `"///"`.</span><span class="sxs-lookup"><span data-stu-id="86a46-216">It also checked for `"///"`.</span></span>  <span data-ttu-id="86a46-217">Düzeltilmiş kod yalnızca dizin oluşturma kullanır ve hiçbir şey ayırır.</span><span class="sxs-lookup"><span data-stu-id="86a46-217">The revised code uses only indexing and allocates nothing.</span></span>  <span data-ttu-id="86a46-218">Boşluk ve denetimleri karakter dizesi ile başlayıp başlamadığını görmek için düzeyinde değil ilk karakteri bulur `"///"`.</span><span class="sxs-lookup"><span data-stu-id="86a46-218">It finds the first character that is not white space, and then checks character by character to see if the string starts with `"///"`.</span></span>  <span data-ttu-id="86a46-219">Yeni kod kullanır `IndexOfFirstNonWhiteSpaceChar` yerine <xref:System.String.TrimStart%2A> bir boşluk olmayan karakter oluştuğu (sonra belirtilen başlangıç dizini) ilk dizin dönün.</span><span class="sxs-lookup"><span data-stu-id="86a46-219">The new code uses `IndexOfFirstNonWhiteSpaceChar` instead of <xref:System.String.TrimStart%2A> to return the first index (after a specified start index) where a non-whitespace character occurs.</span></span>  <span data-ttu-id="86a46-220">Düzeltme tam değilse, ancak eksiksiz bir çözüm için benzer düzeltmelerini uygulamak nasıl görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="86a46-220">The fix is not complete, but you can see how to apply similar fixes for a complete solution.</span></span>  <span data-ttu-id="86a46-221">Bu yaklaşım kod genelindeki uygulayarak, tüm ayırma kaldırabilirsiniz `WriteFormattedDocComment()`.</span><span class="sxs-lookup"><span data-stu-id="86a46-221">By applying this approach throughout the code, you can remove all allocations in `WriteFormattedDocComment()`.</span></span>  
  
 <span data-ttu-id="86a46-222">**Örnek 4: StringBuilder**</span><span class="sxs-lookup"><span data-stu-id="86a46-222">**Example 4: StringBuilder**</span></span>  
  
 <span data-ttu-id="86a46-223">Bu örnekte bir <xref:System.Text.StringBuilder> nesnesi.</span><span class="sxs-lookup"><span data-stu-id="86a46-223">This example uses a <xref:System.Text.StringBuilder> object.</span></span>  <span data-ttu-id="86a46-224">Genel türler için tam tür adı aşağıdaki işlevi oluşturur:</span><span class="sxs-lookup"><span data-stu-id="86a46-224">The following function generates a full type name for generic types:</span></span>  
  
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
  
 <span data-ttu-id="86a46-225">Yeni bir satıra odak noktasıdır <xref:System.Text.StringBuilder> örneği.</span><span class="sxs-lookup"><span data-stu-id="86a46-225">The focus is on the line that creates a new <xref:System.Text.StringBuilder> instance.</span></span>  <span data-ttu-id="86a46-226">Kod için bir ayırma neden `sb.ToString()` ve iç ayırmaları içinde <xref:System.Text.StringBuilder> uygulaması, ancak denetimi bu ayırmaları dize sonucu istiyorsanız.</span><span class="sxs-lookup"><span data-stu-id="86a46-226">The code causes an allocation for `sb.ToString()` and internal allocations within the <xref:System.Text.StringBuilder> implementation, but you cannot control those allocations if you want the string result.</span></span>  
  
 <span data-ttu-id="86a46-227">**Örneğin 4 Düzelt**</span><span class="sxs-lookup"><span data-stu-id="86a46-227">**Fix for example 4**</span></span>  
  
 <span data-ttu-id="86a46-228">Düzeltmek için `StringBuilder` ayırma nesne, nesne önbellek.</span><span class="sxs-lookup"><span data-stu-id="86a46-228">To fix the `StringBuilder` object allocation, cache the  object.</span></span>  <span data-ttu-id="86a46-229">Hatta atılmak tek bir örnek önbelleğe alma performansını önemli ölçüde artırabilir.</span><span class="sxs-lookup"><span data-stu-id="86a46-229">Even caching a single instance that might get thrown away can improve performance significantly.</span></span>  <span data-ttu-id="86a46-230">Bu yeni ilk ve son satır hariç tüm kod atlama işlevin yeni uygulama.</span><span class="sxs-lookup"><span data-stu-id="86a46-230">This is the function’s new implementation, omitting all the code except for the new first and last lines:</span></span>  
  
```csharp  
// Constructs a name like "MyType<T1, T2, T3>"  
public string GenerateFullTypeName(string name, int arity)  
{  
    StringBuilder sb = AcquireBuilder();  
    /* Use sb as before */  
    return GetStringAndReleaseBuilder(sb);  
}  
```  
  
 <span data-ttu-id="86a46-231">Anahtar bölümleri yenidir `AcquireBuilder()` ve `GetStringAndReleaseBuilder()` işlevleri:</span><span class="sxs-lookup"><span data-stu-id="86a46-231">The key parts are the new `AcquireBuilder()` and `GetStringAndReleaseBuilder()` functions:</span></span>  
  
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
  
 <span data-ttu-id="86a46-232">Yeni derleyicileri iş parçacığı oluşturma kullandığından, bu uygulamaların bir iş parçacığı statik alanı kullanın (<xref:System.ThreadStaticAttribute> özniteliği) önbelleğe <xref:System.Text.StringBuilder>, ve büyük olasılıkla atlayabilirsiniz `ThreadStatic` bildirimi.</span><span class="sxs-lookup"><span data-stu-id="86a46-232">Because the new compilers use threading, these implementations use a thread-static field (<xref:System.ThreadStaticAttribute> attribute) to cache the <xref:System.Text.StringBuilder>, and you likely can forgo the `ThreadStatic` declaration.</span></span>  <span data-ttu-id="86a46-233">İş parçacığı statik alan bu kodu yürütür her iş parçacığı için benzersiz bir değere sahiptir.</span><span class="sxs-lookup"><span data-stu-id="86a46-233">The thread-static field holds a unique value for each thread that executes this code.</span></span>  
  
 <span data-ttu-id="86a46-234">`AcquireBuilder()`önbelleğe alınan döndürür <xref:System.Text.StringBuilder> varsa, temizlemeden ve alan veya önbellek null değerine ayarlayarak sonra örneği.</span><span class="sxs-lookup"><span data-stu-id="86a46-234">`AcquireBuilder()` returns the cached <xref:System.Text.StringBuilder> instance if there is one, after clearing it and setting the field or cache to null.</span></span>  <span data-ttu-id="86a46-235">Aksi takdirde `AcquireBuilder()` yeni bir örnek oluşturur ve alan veya önbellek kümesi null bırakarak döndürür.</span><span class="sxs-lookup"><span data-stu-id="86a46-235">Otherwise, `AcquireBuilder()` creates a new instance and returns it, leaving the field or cache set to null.</span></span>  
  
 <span data-ttu-id="86a46-236">İle bitirdiğinizde <xref:System.Text.StringBuilder> , çağırmanız `GetStringAndReleaseBuilder()` dize sonucu elde etmek için Kaydet <xref:System.Text.StringBuilder> örnek alan veya önbellek ve sonucu döndürür.</span><span class="sxs-lookup"><span data-stu-id="86a46-236">When you’re done with <xref:System.Text.StringBuilder> , you call `GetStringAndReleaseBuilder()` to get the string result, save the <xref:System.Text.StringBuilder> instance in the field or cache, and then return the result.</span></span>  <span data-ttu-id="86a46-237">Bu kod yeniden girin ve birden çok oluşturmak için yürütme için mümkündür <xref:System.Text.StringBuilder> (, nadiren gerçekleşir rağmen) nesneleri.</span><span class="sxs-lookup"><span data-stu-id="86a46-237">It is possible for execution to re-enter this code and to create multiple <xref:System.Text.StringBuilder> objects (although that rarely happens).</span></span>  <span data-ttu-id="86a46-238">Yalnızca son yayımlanan kod kaydeder <xref:System.Text.StringBuilder> örnek daha sonra kullanmak için.</span><span class="sxs-lookup"><span data-stu-id="86a46-238">The code saves only the last released <xref:System.Text.StringBuilder> instance for later use.</span></span>  <span data-ttu-id="86a46-239">Bu basit önbelleğe alma stratejisi yeni derleyicileri ayırma önemli ölçüde azalır.</span><span class="sxs-lookup"><span data-stu-id="86a46-239">This simple caching strategy significantly reduced allocations in the new compilers.</span></span>  <span data-ttu-id="86a46-240">MSBuild ("MSBuild") ve .NET Framework bölümleri, performansı artırmak için benzer bir teknik kullanın.</span><span class="sxs-lookup"><span data-stu-id="86a46-240">Parts of the .NET Framework and MSBuild ("MSBuild") use a similar technique to improve performance.</span></span>  
  
 <span data-ttu-id="86a46-241">Bir boyut cap içerdiğinden bu basit önbelleğe alma stratejisi iyi önbellek tasarım uyar.</span><span class="sxs-lookup"><span data-stu-id="86a46-241">This simple caching strategy adheres to good cache design because it has a size cap.</span></span>  <span data-ttu-id="86a46-242">Ancak, daha fazla bakım maliyetlerinin anlamı özgün, artık daha fazla kod yoktur.</span><span class="sxs-lookup"><span data-stu-id="86a46-242">However, there is more code now than in the original, which means more maintenance costs.</span></span>  <span data-ttu-id="86a46-243">Yalnızca bir performans sorununu buldunuz ve PerfView, gösterilen önbelleğe alma stratejisi benimsemeyi <xref:System.Text.StringBuilder> ayırmaları olan önemli katılımcı.</span><span class="sxs-lookup"><span data-stu-id="86a46-243">You should adopt the caching strategy only if you’ve found a performance problem, and PerfView has shown that <xref:System.Text.StringBuilder> allocations are a significant contributor.</span></span>  
  
### <a name="linq-and-lambdas"></a><span data-ttu-id="86a46-244">LINQ ve lambdas</span><span class="sxs-lookup"><span data-stu-id="86a46-244">LINQ and lambdas</span></span>  
 <span data-ttu-id="86a46-245">Dil ile tümleşik sorgu (LINQ) ve lambda ifadeleri kullanma kodu performansı önemli bir etkisi olursa yeniden yazmak zorunda daha sonra bulabileceğiniz üretken özellikleri kullanarak, harika bir örnektir.</span><span class="sxs-lookup"><span data-stu-id="86a46-245">Using Language-Integrated Query (LINQ) and lambda expressions is a great example of using productive features that you might later find you need to rewrite if the code becomes a significant impact on performance.</span></span>  
  
 <span data-ttu-id="86a46-246">**Örnek 5: Lambda'lar, liste\<T > ve IEnumerable\<T >**</span><span class="sxs-lookup"><span data-stu-id="86a46-246">**Example 5: Lambdas, List\<T>, and IEnumerable\<T>**</span></span>  
  
 <span data-ttu-id="86a46-247">Bu örnekte [LINQ ve işlevsel stili kodu](http://blogs.msdn.com/b/charlie/archive/2007/01/26/anders-hejlsberg-on-linq-and-functional-programming.aspx) ad dizesini verilen bir sembol derleyicinin modelinde bulmak için:</span><span class="sxs-lookup"><span data-stu-id="86a46-247">This example uses [LINQ and functional style code](http://blogs.msdn.com/b/charlie/archive/2007/01/26/anders-hejlsberg-on-linq-and-functional-programming.aspx) to find a symbol in the compiler’s model, given a name string:</span></span>  
  
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
  
 <span data-ttu-id="86a46-248">Yeni derleyici ve arama üzerinde oluşturulmuş IDE deneyimleri `FindMatchingSymbol()` bu işlevin tek satırlık bir kod birkaç gizli ayırma şunlardır: çok sık ve vardır.</span><span class="sxs-lookup"><span data-stu-id="86a46-248">The new compiler and the IDE experiences built on it call `FindMatchingSymbol()` very frequently, and there are several hidden allocations in this function’s single line of code.</span></span>  <span data-ttu-id="86a46-249">Bu ayırmaları incelemek için ilk işlevin tek satırlık bir kod iki çizgiye bölün:</span><span class="sxs-lookup"><span data-stu-id="86a46-249">To examine those allocations, first split the function’s single line of code into two lines:</span></span>  
  
```csharp  
Func<Symbol, bool> predicate = s => s.Name == name;  
     return symbols.FirstOrDefault(predicate);  
```  
  
 <span data-ttu-id="86a46-250">İlk satırdaki [lambda ifadesi](~/docs/csharp/programming-guide/statements-expressions-operators/lambda-expressions.md)`s => s.Name == name`[üzerinden kapatır](http://blogs.msdn.com/b/ericlippert/archive/2003/09/17/53028.aspx) yerel değişken `name`.</span><span class="sxs-lookup"><span data-stu-id="86a46-250">In the first line, the [lambda expression](~/docs/csharp/programming-guide/statements-expressions-operators/lambda-expressions.md)`s => s.Name == name`[closes over](http://blogs.msdn.com/b/ericlippert/archive/2003/09/17/53028.aspx) the local variable `name`.</span></span>  <span data-ttu-id="86a46-251">Bu, bir nesne için ayırma yanı sıra gelir [temsilci](~/docs/csharp/language-reference/keywords/delegate.md) , `predicate` tutan kodu ayırır değerini yakalar ortamı tutmak için bir statik sınıf `name`.</span><span class="sxs-lookup"><span data-stu-id="86a46-251">This means that in addition to allocating an object for the [delegate](~/docs/csharp/language-reference/keywords/delegate.md) that `predicate` holds, the code allocates a static class to hold the environment that captures the value of `name`.</span></span>  <span data-ttu-id="86a46-252">Derleyici aşağıdaki gibi bir kod oluşturur:</span><span class="sxs-lookup"><span data-stu-id="86a46-252">The compiler generates code like the following:</span></span>  
  
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
  
 <span data-ttu-id="86a46-253">İki `new` ayırmaları (bir ortam sınıfı için) ve bir temsilci için açık şimdi.</span><span class="sxs-lookup"><span data-stu-id="86a46-253">The two `new` allocations (one for the environment class and one for the delegate) are explicit now.</span></span>  
  
 <span data-ttu-id="86a46-254">Şimdi çağrısına bakın `FirstOrDefault`.</span><span class="sxs-lookup"><span data-stu-id="86a46-254">Now look at the call to `FirstOrDefault`.</span></span> <span data-ttu-id="86a46-255">Bu uzantı metodu <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> türü bir ayırma çok doğurur.</span><span class="sxs-lookup"><span data-stu-id="86a46-255">This extension method on the <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> type incurs an allocation too.</span></span>  <span data-ttu-id="86a46-256">Çünkü `FirstOrDefault` geçen bir <xref:System.Collections.Generic.IEnumerable%601> nesnesi, ilk bağımsız değişkeni olarak (bir bit tartışma için Basitleştirilmiş) aşağıdaki kodu çağrısı genişletebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="86a46-256">Because `FirstOrDefault` takes an <xref:System.Collections.Generic.IEnumerable%601> object as its first argument, you can expand the call to the following code (simplified a bit for discussion):</span></span>  
  
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
  
 <span data-ttu-id="86a46-257">`symbols` Değişken türüne sahip <xref:System.Collections.Generic.List%601>.</span><span class="sxs-lookup"><span data-stu-id="86a46-257">The `symbols` variable has type <xref:System.Collections.Generic.List%601>.</span></span>  <span data-ttu-id="86a46-258"><xref:System.Collections.Generic.List%601> Koleksiyon türü uygulayan <xref:System.Collections.Generic.IEnumerable%601> ve zekice bir numaralandırıcı tanımlar (<xref:System.Collections.Generic.IEnumerator%601> arabirimi), <xref:System.Collections.Generic.List%601> ile uygulayan bir `struct`.</span><span class="sxs-lookup"><span data-stu-id="86a46-258">The <xref:System.Collections.Generic.List%601> collection type implements <xref:System.Collections.Generic.IEnumerable%601> and cleverly defines an enumerator (<xref:System.Collections.Generic.IEnumerator%601> interface) that <xref:System.Collections.Generic.List%601> implements with a `struct`.</span></span>  <span data-ttu-id="86a46-259">Bir sınıf yerine bir yapı kullanarak hangi sırayla, atık toplama performansını etkileyebilecek herhangi yığın ayırmaları genellikle kaçının anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="86a46-259">Using a structure instead of a class means that you usually avoid any heap allocations, which, in turn, can affect garbage collection performance.</span></span>  <span data-ttu-id="86a46-260">Numaralandırmalar genelde dil kullanılan `foreach` çağrı yığınındaki döndürülen Numaralandırıcı yapısı kullanır döngüsü.</span><span class="sxs-lookup"><span data-stu-id="86a46-260">Enumerators are typically used with the language’s `foreach` loop, which uses the enumerator structure as it is returned on the call stack.</span></span>  <span data-ttu-id="86a46-261">Bir nesne için yer açmak için çağrı yığını işaretçi artırma yaptığı gibi bir yığın ayırma GC etkilemez.</span><span class="sxs-lookup"><span data-stu-id="86a46-261">Incrementing the call stack pointer to make room for an object does not affect GC the way a heap allocation does.</span></span>  
  
 <span data-ttu-id="86a46-262">Genişletilmiş durumunda `FirstOrDefault` çağrısı kod gereken çağırmak `GetEnumerator()` üzerinde bir <xref:System.Collections.Generic.IEnumerable%601>.</span><span class="sxs-lookup"><span data-stu-id="86a46-262">In the case of the expanded `FirstOrDefault` call, the code needs to call `GetEnumerator()` on an <xref:System.Collections.Generic.IEnumerable%601>.</span></span>  <span data-ttu-id="86a46-263">Atama `symbols` için `enumerable` değişken türü `IEnumerable<Symbol>` gerçek nesne bilgileri kaybeder bir <xref:System.Collections.Generic.List%601>.</span><span class="sxs-lookup"><span data-stu-id="86a46-263">Assigning `symbols` to the `enumerable` variable of type `IEnumerable<Symbol>` loses the information that the actual object is a <xref:System.Collections.Generic.List%601>.</span></span>  <span data-ttu-id="86a46-264">Kod Numaralandırıcı ile getirir, yani `enumerable.GetEnumerator()`, .NET Framework atamak döndürülen yapısı kutusunda gereken `enumerator` değişkeni.</span><span class="sxs-lookup"><span data-stu-id="86a46-264">This means that when the code fetches the enumerator with `enumerable.GetEnumerator()`, the .NET Framework has to box the returned structure to assign it to the `enumerator` variable.</span></span>  
  
 <span data-ttu-id="86a46-265">**Örneğin 5 Düzelt**</span><span class="sxs-lookup"><span data-stu-id="86a46-265">**Fix for example 5**</span></span>  
  
 <span data-ttu-id="86a46-266">Düzeltme yeniden yazmaktır `FindMatchingSymbol` gibi kendi tek satırlık bir kod hala kısa, kolay okuduğunuzdan ve anladığınızdan ve bakımını kolay olan altı kod satırıyla değiştirme:</span><span class="sxs-lookup"><span data-stu-id="86a46-266">The fix is to rewrite `FindMatchingSymbol` as follows, replacing its single line of code with six lines of code that are still concise, easy to read and understand, and easy to maintain:</span></span>  
  
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
  
 <span data-ttu-id="86a46-267">Bu kod LINQ genişletme yöntemleri, Lambda'lar veya numaralandırıcıları kullanmayan ve hiçbir ayırmaları doğurur.</span><span class="sxs-lookup"><span data-stu-id="86a46-267">This code doesn’t use LINQ extension methods, lambdas, or enumerators, and it incurs no allocations.</span></span>  <span data-ttu-id="86a46-268">Derleyici görebilirsiniz çünkü hiçbir ayırmaları olan `symbols` koleksiyonu bir <xref:System.Collections.Generic.List%601> ve sonuçta elde edilen Numaralandırıcı (yapı) yerel bir değişkene kutulama önlemek için doğru türü ile bağlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="86a46-268">There are no allocations because the compiler can see that the `symbols` collection is a <xref:System.Collections.Generic.List%601> and can bind the resulting enumerator (a structure) to a local variable with the right type to avoid boxing.</span></span>  <span data-ttu-id="86a46-269">Bu işlev özgün sürümü gücüyle C# ve .NET Framework'ün üretkenlik harika bir örneği oluştu.</span><span class="sxs-lookup"><span data-stu-id="86a46-269">The original version of this function was a great example of the expressive power of C# and the productivity of the .NET Framework.</span></span>  <span data-ttu-id="86a46-270">Bu yeni ve daha verimli sürümü korumak için herhangi bir karmaşık kod eklemeden bu nitelikleri korur.</span><span class="sxs-lookup"><span data-stu-id="86a46-270">This new and more efficient version preserves those qualities without adding any complex code to maintain.</span></span>  
  
### <a name="async-method-caching"></a><span data-ttu-id="86a46-271">Zaman uyumsuz yöntem önbelleğe alma</span><span class="sxs-lookup"><span data-stu-id="86a46-271">Async method caching</span></span>  
 <span data-ttu-id="86a46-272">Önbelleğe alınan sonuçları kullanmaya çalıştığınızda sonraki örnek ortak bir sorunu gösterir. bir [zaman uyumsuz](http://msdn.microsoft.com/library/db854f91-ccef-4035-ae4d-0911fde808c7) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="86a46-272">The next example shows a common problem when you try to use cached results in an [async](http://msdn.microsoft.com/library/db854f91-ccef-4035-ae4d-0911fde808c7) method.</span></span>  
  
 <span data-ttu-id="86a46-273">**Örnek 6: zaman uyumsuz yöntemleri önbelleğe alma**</span><span class="sxs-lookup"><span data-stu-id="86a46-273">**Example 6: caching in async methods**</span></span>  
  
 <span data-ttu-id="86a46-274">Sözdizimi ağacı üzerinde yeni C# ve Visual Basic derleyicileri sık yerleşik olarak bulunan Visual Studio IDE özelliklerinden getirebilir ve derleyicileri Visual Studio yanıt verebilir durumda tutmak için bunu yaparken zaman uyumsuz kullanın.</span><span class="sxs-lookup"><span data-stu-id="86a46-274">The Visual Studio IDE features built on the new C# and Visual Basic compilers frequently fetch syntax trees, and the compilers use async when doing so to keep Visual Studio responsive.</span></span>  <span data-ttu-id="86a46-275">Sözdizimi ağacı almak için yazabilir kod ilk sürümü şöyledir:</span><span class="sxs-lookup"><span data-stu-id="86a46-275">Here’s the first version of the code you might write to get a syntax tree:</span></span>  
  
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
  
 <span data-ttu-id="86a46-276">Bu arama görebilirsiniz `GetSyntaxTreeAsync()` başlatır bir `Parser`kodu ayrıştırır ve ardından döndürür bir <xref:System.Threading.Tasks.Task> nesnesi `Task<SyntaxTree>`.</span><span class="sxs-lookup"><span data-stu-id="86a46-276">You can see that calling `GetSyntaxTreeAsync()` instantiates a `Parser`, parses the code, and then returns a <xref:System.Threading.Tasks.Task> object, `Task<SyntaxTree>`.</span></span>  <span data-ttu-id="86a46-277">Pahalı bölümü ayırma `Parser` örneği ve kod ayrıştırma.</span><span class="sxs-lookup"><span data-stu-id="86a46-277">The expensive part is allocating the `Parser` instance and parsing the code.</span></span>  <span data-ttu-id="86a46-278">İşlevi döndürür bir <xref:System.Threading.Tasks.Task> böylece çağıranlar ayrıştırma iş bekler ve kullanıcı girişine yanıt vermesi kullanıcı Arabirimi iş parçacığı boş.</span><span class="sxs-lookup"><span data-stu-id="86a46-278">The function returns a <xref:System.Threading.Tasks.Task> so that callers can await the parsing work and free the UI thread to be responsive to user input.</span></span>  
  
 <span data-ttu-id="86a46-279">Saat ve ayırmaları kaydetmek için ayrıştırma sonucu önbelleğe almak için aşağıdaki kodu yazabilirsiniz aynı sözdizimi ağacı almak birkaç Visual Studio özellikleri deneyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="86a46-279">Several Visual Studio features might try to get the same syntax tree, so you might write the following code to cache the parsing result to save time and allocations.</span></span>  <span data-ttu-id="86a46-280">Ancak, bu kod bir ayırma oluşturur:</span><span class="sxs-lookup"><span data-stu-id="86a46-280">However, this code incurs an allocation:</span></span>  
  
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
  
 <span data-ttu-id="86a46-281">Önbelleğe alma ile yeni koduna sahip olduğunu gördüğünüz bir `SyntaxTree` adlı alanı `cachedResult`.</span><span class="sxs-lookup"><span data-stu-id="86a46-281">You see that the new code with caching has a `SyntaxTree` field named `cachedResult`.</span></span>  <span data-ttu-id="86a46-282">Bu alan boş olduğunda `GetSyntaxTreeAsync()` işi yapar ve sonuç önbelleğine kaydeder.</span><span class="sxs-lookup"><span data-stu-id="86a46-282">When this field is null, `GetSyntaxTreeAsync()` does the work and saves the result in the cache.</span></span>  <span data-ttu-id="86a46-283">`GetSyntaxTreeAsync()`döndürür `SyntaxTree` nesnesi.</span><span class="sxs-lookup"><span data-stu-id="86a46-283">`GetSyntaxTreeAsync()` returns the `SyntaxTree` object.</span></span>  <span data-ttu-id="86a46-284">Varsa olan sorunu bir `async` türündeki işlevi `Task<SyntaxTree>`, ve türünde bir değer döndürmesi `SyntaxTree`, sonuç tutmak için bir görev ayırmak için kod derleyicisi yayar (kullanarak `Task<SyntaxTree>.FromResult()`).</span><span class="sxs-lookup"><span data-stu-id="86a46-284">The problem is that when you have an `async` function of type `Task<SyntaxTree>`, and you return a value of type `SyntaxTree`, the compiler emits code to allocate a Task to hold the result (by using `Task<SyntaxTree>.FromResult()`).</span></span>  <span data-ttu-id="86a46-285">Görev tamamlandı olarak işaretlenir ve sonucu hemen kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="86a46-285">The Task is marked as completed, and the result is immediately available.</span></span>  <span data-ttu-id="86a46-286">Yeni derleyicileri kodunda <xref:System.Threading.Tasks.Task> zaten tamamlandığından nesneleri oluştu nedenle genellikle bu düzeltmeyle Bu ayırmaları yanıtlama hızı önemli ölçüde geliştirildi.</span><span class="sxs-lookup"><span data-stu-id="86a46-286">In the code for the new compilers, <xref:System.Threading.Tasks.Task> objects that were already completed occurred so often that fixing these allocations improved responsiveness noticeably.</span></span>  
  
 <span data-ttu-id="86a46-287">**Örneğin 6 Düzelt**</span><span class="sxs-lookup"><span data-stu-id="86a46-287">**Fix for example 6**</span></span>  
  
 <span data-ttu-id="86a46-288">Tamamlanan kaldırmak için <xref:System.Threading.Tasks.Task> ayırma, tamamlanmış sonuç görev nesnesiyle önbelleğe alabilir:</span><span class="sxs-lookup"><span data-stu-id="86a46-288">To remove the completed <xref:System.Threading.Tasks.Task> allocation, you can cache the Task object with the completed result:</span></span>  
  
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
  
 <span data-ttu-id="86a46-289">Bu kod türünü değiştirir `cachedResult` için `Task<SyntaxTree>` ve kullanan bir `async` özgün kod tutan yardımcı işlevini `GetSyntaxTreeAsync()`.</span><span class="sxs-lookup"><span data-stu-id="86a46-289">This code changes the type of `cachedResult` to `Task<SyntaxTree>` and employs an `async` helper function that holds the original code from `GetSyntaxTreeAsync()`.</span></span>  <span data-ttu-id="86a46-290">`GetSyntaxTreeAsync()`Şimdi kullanan [null birleştirmesi işleci](~/docs/csharp/language-reference/operators/null-conditional-operator.md) dönmek için `cachedResult` null değilse.</span><span class="sxs-lookup"><span data-stu-id="86a46-290">`GetSyntaxTreeAsync()` now uses the [null coalescing operator](~/docs/csharp/language-reference/operators/null-conditional-operator.md) to return `cachedResult` if it isn't null.</span></span>  <span data-ttu-id="86a46-291">Varsa `cachedResult` null ise `GetSyntaxTreeAsync()` çağrıları `GetSyntaxTreeUncachedAsync()` ve sonucu önbelleğe alır.</span><span class="sxs-lookup"><span data-stu-id="86a46-291">If `cachedResult` is null, then `GetSyntaxTreeAsync()` calls `GetSyntaxTreeUncachedAsync()` and caches the result.</span></span>  <span data-ttu-id="86a46-292">Dikkat `GetSyntaxTreeAsync()` çağrısı await değil `GetSyntaxTreeUncachedAsync()` kodu normal olarak.</span><span class="sxs-lookup"><span data-stu-id="86a46-292">Notice that `GetSyntaxTreeAsync()` doesn’t await the call to `GetSyntaxTreeUncachedAsync()` as the code would normally.</span></span>  <span data-ttu-id="86a46-293">Await anlamına gelir kullanmıyor olduğunda `GetSyntaxTreeUncachedAsync()` döndürür kendi <xref:System.Threading.Tasks.Task> nesnesi, `GetSyntaxTreeAsync()` hemen döndürür <xref:System.Threading.Tasks.Task>.</span><span class="sxs-lookup"><span data-stu-id="86a46-293">Not using await means that when `GetSyntaxTreeUncachedAsync()` returns its <xref:System.Threading.Tasks.Task> object, `GetSyntaxTreeAsync()` immediately returns the <xref:System.Threading.Tasks.Task>.</span></span>  <span data-ttu-id="86a46-294">Şimdi, önbelleğe alınan sonucu olan bir <xref:System.Threading.Tasks.Task>, bu nedenle hiçbir ayırmaları önbelleğe alınmış bir sonuç yok.</span><span class="sxs-lookup"><span data-stu-id="86a46-294">Now, the cached result is a <xref:System.Threading.Tasks.Task>, so there are no allocations to return the cached result.</span></span>  
  
### <a name="additional-considerations"></a><span data-ttu-id="86a46-295">Ek hususlar</span><span class="sxs-lookup"><span data-stu-id="86a46-295">Additional considerations</span></span>  
 <span data-ttu-id="86a46-296">Büyük uygulamalar ya da çok miktarda veri işleyen uygulamalar olası sorunlar hakkında daha fazla birkaç noktalar şunlardır.</span><span class="sxs-lookup"><span data-stu-id="86a46-296">Here are a few more points about potential problems in large apps or apps that process a lot of data.</span></span>  
  
 <span data-ttu-id="86a46-297">**Sözlük**</span><span class="sxs-lookup"><span data-stu-id="86a46-297">**Dictionaries**</span></span>  
  
 <span data-ttu-id="86a46-298">Ancak çok kullanışlı ve kendiliğinden verimli sözlükler ve sözlükleri ubiquitously birçok programda kullanılır.</span><span class="sxs-lookup"><span data-stu-id="86a46-298">Dictionaries are used ubiquitously in many programs, and though dictionaries are very convenient and inherently efficient.</span></span>  <span data-ttu-id="86a46-299">Ancak, bunlar genellikle açamayacağı kullanılır.</span><span class="sxs-lookup"><span data-stu-id="86a46-299">However, they’re often used inappropriately.</span></span>  <span data-ttu-id="86a46-300">Visual Studio ve yeni derleyicileri, analiz sözlükler birçoğu tek bir öğe içeriyor veya boş gösterir.</span><span class="sxs-lookup"><span data-stu-id="86a46-300">In Visual Studio and the new compilers, analysis shows that many of the dictionaries contained a single element or were empty.</span></span>  <span data-ttu-id="86a46-301">Boş bir <xref:System.Collections.Generic.Dictionary%602> on alanları olan ve bir x86 üzerinde yığında 48 bayt kaplar makine.</span><span class="sxs-lookup"><span data-stu-id="86a46-301">An empty <xref:System.Collections.Generic.Dictionary%602> has ten fields and occupies 48 bytes on the heap on an x86 machine.</span></span>  <span data-ttu-id="86a46-302">Bir eşleme veya ilişkilendirilebilir veri yapısı sabiti zamanı arama ile gerektiğinde sözlükler mükemmeldir.</span><span class="sxs-lookup"><span data-stu-id="86a46-302">Dictionaries are great when you need a mapping or associative data structure with constant-time lookup.</span></span>  <span data-ttu-id="86a46-303">Yalnızca birkaç öğeler varsa, ancak, çok fazla alan bir sözlüğünü kullanarak boşa harcanmasına.</span><span class="sxs-lookup"><span data-stu-id="86a46-303">However, when you have only a few elements, you waste a lot of space by using a dictionary.</span></span>  <span data-ttu-id="86a46-304">Bunun yerine, örneğin, yinelemeli olarak görünebilir bir `List<KeyValuePair\<K,V>>`, yalnızca hızlı.</span><span class="sxs-lookup"><span data-stu-id="86a46-304">Instead, for example, you could iteratively look through a `List<KeyValuePair\<K,V>>`, just as fast.</span></span>  <span data-ttu-id="86a46-305">Sıralanmış bir dizi N(log(N)) arama ile kullanarak, kullanmakta olduğunuz öğeleri sayısına bağlı olarak, hızlı olarak neredeyse yalnızca ile veri yükleme ve ondan (çok yaygın bir desen) okumak için bir sözlük kullanıyorsanız olabilir.</span><span class="sxs-lookup"><span data-stu-id="86a46-305">If you use a dictionary only to load it with data and then read from it (a very common pattern), using a sorted array with an N(log(N)) lookup might be nearly as fast, depending on the number of elements you're using.</span></span>  
  
 <span data-ttu-id="86a46-306">**Sınıfları ve yapıları**</span><span class="sxs-lookup"><span data-stu-id="86a46-306">**Classes vs. structures**</span></span>  
  
 <span data-ttu-id="86a46-307">Bir biçimde sınıfları ve yapıları Klasik alanı/saat kolaylığını uygulamalarınızı ayarlamak için sağlar.</span><span class="sxs-lookup"><span data-stu-id="86a46-307">In a way, classes and structures provide a classic space/time tradeoff for tuning your apps.</span></span>  <span data-ttu-id="86a46-308">Sınıfları kullanan bir x86 ek yükü 12 bayt hiçbir alan sahip, ancak yalnızca bir sınıf örneğine başvuru yapmak için bir işaretçi aldığından geçici geçirmek uygun maliyetli olsa bile makine.</span><span class="sxs-lookup"><span data-stu-id="86a46-308">Classes incur 12 bytes of overhead on an x86 machine even if they have no fields, but they are inexpensive to pass around because it only takes a pointer to refer to a class instance.</span></span>  <span data-ttu-id="86a46-309">Yapıları hiçbir yığın ayırmaları Kutulu değil, ancak işlev bağımsız değişkenleri olarak büyük yapıları geçirmenizi ya da dönüş değerleri otomatik olarak yapıları tüm veri üyeleri kopyalamak için CPU süresi geçen doğurur.</span><span class="sxs-lookup"><span data-stu-id="86a46-309">Structures incur no heap allocations if they aren’t boxed, but when you pass large structures as function arguments or return values, it takes CPU time to atomically copy all the data members of the structures.</span></span>  <span data-ttu-id="86a46-310">Yinelenen çağrılar yapıları dönün ve özelliğin değeri, aşırı miktarda veri kopyalamayı önlemek için bir yerel değişkende önbellek özellikleri için dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="86a46-310">Watch out for repeated calls to properties that return structures, and cache the property’s value in a local variable to avoid excessive data copying.</span></span>  
  
 <span data-ttu-id="86a46-311">**Önbellekler**</span><span class="sxs-lookup"><span data-stu-id="86a46-311">**Caches**</span></span>  
  
 <span data-ttu-id="86a46-312">Ortak bir performans elde sonuçlarını önbelleğe alma ' dir.</span><span class="sxs-lookup"><span data-stu-id="86a46-312">A common performance trick is to cache results.</span></span>  <span data-ttu-id="86a46-313">Ancak, bir önbellek boyutu cap ya da elden ilkesine sahip olmayan bir bellek sızıntısı olabilir.</span><span class="sxs-lookup"><span data-stu-id="86a46-313">However, a cache without a size cap or disposal policy can be a memory leak.</span></span>  <span data-ttu-id="86a46-314">Çok sayıda önbellekleri bellekte tutun, büyük miktarlarda verilerin işlerken, önbelleğe alınan aramaları yararları geçersiz kılmak atık toplama neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="86a46-314">When processing large amounts of data, if you hold on to a lot of memory in caches, you can cause garbage collection to override the benefits of your cached lookups.</span></span>  
  
 <span data-ttu-id="86a46-315">Bu makalede, nasıl özellikle büyük sistemleri veya büyük miktarda veri işleyen sistemleri için uygulama yanıt hızını etkileyebilir performans sorununu Belirtiler bilincinde olmalısınız açıklanmıştır.</span><span class="sxs-lookup"><span data-stu-id="86a46-315">In this article, we discussed how you should be aware of performance bottleneck symptoms that can affect your app's responsiveness, especially for large systems or systems that process a large amount of data.</span></span> <span data-ttu-id="86a46-316">Ortak culprits kutulama dize işlemeleri, LINQ ve lambda, önbellek boyutu sınırı ya da elden İlkesi, sözlükler ve yapıları geçici geçirme uygunsuz kullanımını olmadan zaman uyumsuz yöntemleri önbelleğe alma yer alır.</span><span class="sxs-lookup"><span data-stu-id="86a46-316">Common culprits include boxing, string manipulations, LINQ and lambda, caching in async methods, caching without a size limit or disposal policy, inappropriate use of dictionaries, and passing around structures.</span></span>  <span data-ttu-id="86a46-317">Uygulamalarınızı ayarlama dört bulguları göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="86a46-317">Keep in mind the four facts for tuning your apps:</span></span>  
  
-   <span data-ttu-id="86a46-318">Yoksa erken en iyi duruma getirme – üretken ve sorunları nokta olduğunda, uygulamanızın ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="86a46-318">Don’t prematurely optimize – be productive and tune your app when you spot problems.</span></span>  
  
-   <span data-ttu-id="86a46-319">Profilleri kalan yok –, değil ölçümleri gerçekleştiriyoruz, tahmin.</span><span class="sxs-lookup"><span data-stu-id="86a46-319">Profiles don’t lie – you’re guessing if you’re not measuring.</span></span>  
  
-   <span data-ttu-id="86a46-320">İyi araçları tüm fark olun – PerfView indirin ve deneyin.</span><span class="sxs-lookup"><span data-stu-id="86a46-320">Good tools make all the difference – download PerfView and try it out.</span></span>  
  
-   <span data-ttu-id="86a46-321">Tüm olmasından ayırmaları hakkında – başka bir deyişle derleyici platform takım yeni derleyicileri performansını iyileştirme zamanının çoğunu burada harcanan.</span><span class="sxs-lookup"><span data-stu-id="86a46-321">It's all about allocations – that is where the compiler platform team spent most of their time improving the performance of the new compilers.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="86a46-322">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="86a46-322">See Also</span></span>  
 [<span data-ttu-id="86a46-323">Bu konuda sunumu videosu</span><span class="sxs-lookup"><span data-stu-id="86a46-323">Video of presentation of this topic</span></span>](http://channel9.msdn.com/Events/TechEd/NorthAmerica/2013/DEV-B333)  
 [<span data-ttu-id="86a46-324">Performans profili oluşturma Başlangıç Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="86a46-324">Beginners Guide to Performance Profiling</span></span>](/visualstudio/profiling/beginners-guide-to-performance-profiling)  
 [<span data-ttu-id="86a46-325">Performans</span><span class="sxs-lookup"><span data-stu-id="86a46-325">Performance</span></span>](../../../docs/framework/performance/index.md)  
 [<span data-ttu-id="86a46-326">.NET Performans İpuçları</span><span class="sxs-lookup"><span data-stu-id="86a46-326">.NET Performance Tips</span></span>](http://msdn.microsoft.com/library/ms973839.aspx)  
 [<span data-ttu-id="86a46-327">Windows Phone performans çözümleme aracı</span><span class="sxs-lookup"><span data-stu-id="86a46-327">Windows Phone Performance Analysis Tool</span></span>](http://msdn.microsoft.com/magazine/hh781024.aspx)  
 [<span data-ttu-id="86a46-328">Visual Studio Profil Oluşturucu ile uygulama engelleri bulun</span><span class="sxs-lookup"><span data-stu-id="86a46-328">Find Application Bottlenecks with Visual Studio Profiler</span></span>](http://msdn.microsoft.com/magazine/cc337887.aspx)  
 [<span data-ttu-id="86a46-329">Kanal 9 PerfView öğreticileri</span><span class="sxs-lookup"><span data-stu-id="86a46-329">Channel 9 PerfView tutorials</span></span>](http://channel9.msdn.com/Series/PerfView-Tutorial)  
 [<span data-ttu-id="86a46-330">Üst düzey performans ipuçları</span><span class="sxs-lookup"><span data-stu-id="86a46-330">High-level Performance Tips</span></span>](http://curah.microsoft.com/4604/improving-your-net-apps-startup-performance)  
 [<span data-ttu-id="86a46-331">DotNet/roslyn bağlantıların github'da</span><span class="sxs-lookup"><span data-stu-id="86a46-331">dotnet/roslyn repo on GitHub</span></span>](https://github.com/dotnet/roslyn)
