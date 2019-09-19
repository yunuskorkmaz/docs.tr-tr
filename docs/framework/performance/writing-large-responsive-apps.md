---
title: Büyük, Yanıt Veren .NET Framework Uygulamaları Yazma
ms.date: 03/30/2017
ms.assetid: 123457ac-4223-4273-bb58-3bc0e4957e9d
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 4e4b5822306fa8f4e6b4437f4a1bef92b53a86b9
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71046141"
---
# <a name="writing-large-responsive-net-framework-apps"></a><span data-ttu-id="c99e9-102">Büyük, Yanıt Veren .NET Framework Uygulamaları Yazma</span><span class="sxs-lookup"><span data-stu-id="c99e9-102">Writing Large, Responsive .NET Framework Apps</span></span>
<span data-ttu-id="c99e9-103">Bu makalede, büyük .NET Framework uygulamalarının veya dosyalar ya da veritabanları gibi büyük miktarda veriyi işleyen uygulamaların performansını iyileştirmeye yönelik ipuçları sunulmaktadır.</span><span class="sxs-lookup"><span data-stu-id="c99e9-103">This article provides tips for improving the performance of large .NET Framework apps, or apps that process a large amount of data such as files or databases.</span></span> <span data-ttu-id="c99e9-104">Bu ipuçları, Yönetilen koddaki C# ve Visual Basic derleyicilerinin yeniden yazma işleminden gelir ve bu makalede C# derleyicinin çeşitli gerçek örnekleri yer almaktadır.</span><span class="sxs-lookup"><span data-stu-id="c99e9-104">These tips come from rewriting the C# and Visual Basic compilers in managed code, and this article includes several real examples from the C# compiler.</span></span> 
  
 <span data-ttu-id="c99e9-105">.NET Framework uygulamalar oluşturmak için son derece üretken değildir.</span><span class="sxs-lookup"><span data-stu-id="c99e9-105">The .NET Framework is highly productive for building apps.</span></span> <span data-ttu-id="c99e9-106">Güçlü ve güvenli diller ve zengin kitaplıkların bir koleksiyonu, uygulamanın yüksek düzeyde meyve özelliği olmasını kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="c99e9-106">Powerful and safe languages and a rich collection of libraries make app building highly fruitful.</span></span> <span data-ttu-id="c99e9-107">Bununla birlikte, harika üretkenlik sorumluluğu gelir.</span><span class="sxs-lookup"><span data-stu-id="c99e9-107">However, with great productivity comes responsibility.</span></span> <span data-ttu-id="c99e9-108">.NET Framework tüm gücünü kullanmanız gerekir, ancak gerektiğinde kodunuzun performansını ayarlamaya hazır olursunuz.</span><span class="sxs-lookup"><span data-stu-id="c99e9-108">You should use all the power of the .NET Framework, but be prepared to tune your code’s performance when needed.</span></span> 
  
## <a name="why-the-new-compiler-performance-applies-to-your-app"></a><span data-ttu-id="c99e9-109">Yeni derleyici performansının neden uygulamanız için geçerli olduğu</span><span class="sxs-lookup"><span data-stu-id="c99e9-109">Why the new compiler performance applies to your app</span></span>  
 <span data-ttu-id="c99e9-110">.NET Compiler Platform ("Roslyn") ekibi, Visual Studio 'da C# kod modellemesi ve analiz etmek, araçları oluşturmak ve çok daha zengin, kod duyarlı deneyimler sağlamak Için yeni API 'ler sağlamak üzere Yönetilen koddaki ve Visual Basic derleyicilerini yeniden yazdı.</span><span class="sxs-lookup"><span data-stu-id="c99e9-110">The .NET Compiler Platform ("Roslyn") team rewrote the C# and Visual Basic compilers in managed code to provide new APIs for modeling and analyzing code, building tools, and enabling much richer, code-aware experiences in Visual Studio.</span></span> <span data-ttu-id="c99e9-111">Derleyicilerin yeniden oluşturulması ve yeni derleyicilerde Visual Studio deneyimleri oluşturmak, büyük .NET Framework uygulamaları veya çok sayıda veriyi işleyen herhangi bir uygulama için geçerli olan yararlı performans öngörülerini ortaya çıkarmaktadır.</span><span class="sxs-lookup"><span data-stu-id="c99e9-111">Rewriting the compilers and building Visual Studio experiences on the new compilers revealed useful performance insights that are applicable to any large .NET Framework app or any app that processes a lot of data.</span></span> <span data-ttu-id="c99e9-112">Derleyicilerin sunduğu öngörülerden C# ve örneklerden yararlanmak için derleyiciler hakkında bilmeniz gerekmez.</span><span class="sxs-lookup"><span data-stu-id="c99e9-112">You don't need to know about compilers to take advantage of the insights and examples from the C# compiler.</span></span> 
  
 <span data-ttu-id="c99e9-113">Visual Studio, tanımlayıcıların ve anahtar sözcüklerin, sözdizimi tamamlanma listelerinin, dalgalı çizgiler hataları, parametre ipuçları, kod sorunları ve kod eylemleri gibi çok sevdiği tüm IntelliSense özelliklerini oluşturmak için derleyici API 'Lerini kullanır.</span><span class="sxs-lookup"><span data-stu-id="c99e9-113">Visual Studio uses the compiler APIs to build all the IntelliSense features that users love, such as colorization of identifiers and keywords, syntax completion lists, squiggles for errors, parameter tips, code issues, and code actions.</span></span> <span data-ttu-id="c99e9-114">Visual Studio, geliştiriciler kodu yazarken ve değiştirirken bu yardım 'ı sağlar ve derleyici sürekli olarak kod geliştiricilerin düzenlemesini düzenleyecağından Visual Studio yanıt vermeye devam etmelidir.</span><span class="sxs-lookup"><span data-stu-id="c99e9-114">Visual Studio provides this help while developers are typing and changing their code, and Visual Studio must remain responsive while the compiler continually models the code developers edit.</span></span> 
  
 <span data-ttu-id="c99e9-115">Son kullanıcılarınız uygulamanızla etkileşdiğinde, yanıt vermesini bekler.</span><span class="sxs-lookup"><span data-stu-id="c99e9-115">When your end users interact with your app, they expect it to be responsive.</span></span> <span data-ttu-id="c99e9-116">Yazma veya komut işleme hiçbir şekilde engellenmemelidir.</span><span class="sxs-lookup"><span data-stu-id="c99e9-116">Typing or command handling should never be blocked.</span></span> <span data-ttu-id="c99e9-117">Yardım hızlı bir şekilde açılır veya Kullanıcı yazmaya devam ederse bunu vermelidir.</span><span class="sxs-lookup"><span data-stu-id="c99e9-117">Help should pop up quickly or give up if the user continues typing.</span></span> <span data-ttu-id="c99e9-118">Uygulamanız, uygulamayı ağır hale getirmek için uzun hesaplamalar ile UI iş parçacığını engellemeyi engellememelidir.</span><span class="sxs-lookup"><span data-stu-id="c99e9-118">Your app should avoid blocking the UI thread with long computations that make the app feel sluggish.</span></span> 
  
 <span data-ttu-id="c99e9-119">Roslyn derleyicileri hakkında daha fazla bilgi için [.net Compiler Platform SDK 'sına](../../csharp/roslyn-sdk/index.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="c99e9-119">For more information about Roslyn compilers, see [The .NET Compiler Platform SDK](../../csharp/roslyn-sdk/index.md).</span></span>
  
## <a name="just-the-facts"></a><span data-ttu-id="c99e9-120">Yalnızca olgu</span><span class="sxs-lookup"><span data-stu-id="c99e9-120">Just the Facts</span></span>  
 <span data-ttu-id="c99e9-121">Performansı ayarlama ve yanıt veren .NET Framework uygulamalar oluşturma konusunda bu olguları göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="c99e9-121">Consider these facts when tuning performance and creating responsive .NET Framework apps.</span></span> 
  
### <a name="fact-1-dont-prematurely-optimize"></a><span data-ttu-id="c99e9-122">Olgu 1: Zamanından önce iyileştirmeyin</span><span class="sxs-lookup"><span data-stu-id="c99e9-122">Fact 1: Don’t prematurely optimize</span></span>  
 <span data-ttu-id="c99e9-123">Bu değerden daha karmaşık olan ve bakım, hata ayıklama ve polishing maliyetleri için gereken bir kod yazma.</span><span class="sxs-lookup"><span data-stu-id="c99e9-123">Writing code that is more complex than it needs to be incurs maintenance, debugging, and polishing costs.</span></span> <span data-ttu-id="c99e9-124">Deneyimli programcıların kodlama sorunlarını çözme ve daha verimli kod yazma hakkında sezgisel bir attık vardır.</span><span class="sxs-lookup"><span data-stu-id="c99e9-124">Experienced programmers have an intuitive grasp of how to solve coding problems and write more efficient code.</span></span> <span data-ttu-id="c99e9-125">Ancak, bazen kodlarını daha önce iyileştirirler.</span><span class="sxs-lookup"><span data-stu-id="c99e9-125">However, they sometimes prematurely optimize their code.</span></span> <span data-ttu-id="c99e9-126">Örneğin, basit bir dizi yeterli olduğunda bir karma tablo kullanır ya da yalnızca yeniden hesaplama değerleri yerine bellek sızıntısına neden olabilecek karmaşık önbellek kullanır.</span><span class="sxs-lookup"><span data-stu-id="c99e9-126">For example, they use a hash table when a simple array would suffice, or use complicated caching that may leak memory instead of simply recomputing values.</span></span> <span data-ttu-id="c99e9-127">Deneyim programlayıcı olsanız bile, sorunları bulduğunuzda performansı test etmeniz ve kodunuzu çözümlemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="c99e9-127">Even if you’re an experience programmer, you should test for performance and analyze your code when you find issues.</span></span> 
  
### <a name="fact-2-if-youre-not-measuring-youre-guessing"></a><span data-ttu-id="c99e9-128">Olgu 2: Ölçmeye başladıysanız tahmin edersiniz</span><span class="sxs-lookup"><span data-stu-id="c99e9-128">Fact 2: If you’re not measuring, you’re guessing</span></span>  
 <span data-ttu-id="c99e9-129">Profiller ve ölçümler yer almıyor.</span><span class="sxs-lookup"><span data-stu-id="c99e9-129">Profiles and measurements don’t lie.</span></span> <span data-ttu-id="c99e9-130">Profiller, CPU 'nun tam olarak yüklenip yüklenmediğini veya disk g/ç üzerinde engellenip engellenmeyeceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="c99e9-130">Profiles show you whether the CPU is fully loaded or whether you’re blocked on disk I/O.</span></span> <span data-ttu-id="c99e9-131">Profiller size ne tür ve ne kadar bellek ayrılacağını ve CPU 'nun [çöp toplamada](../../standard/garbage-collection/index.md) (GC) çok fazla zaman harcamadığını söyler.</span><span class="sxs-lookup"><span data-stu-id="c99e9-131">Profiles tell you what kind and how much memory you’re allocating and whether your CPU is spending a lot of time in [garbage collection](../../standard/garbage-collection/index.md) (GC).</span></span> 
  
 <span data-ttu-id="c99e9-132">Uygulamanızda önemli müşteri deneyimleri veya senaryolar için performans hedefleri ayarlamanız ve ölçü performansına yönelik testler yazmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="c99e9-132">You should set performance goals for key customer experiences or scenarios in your app and write tests to measure performance.</span></span> <span data-ttu-id="c99e9-133">Bilimsel yöntemi uygulayarak başarısız testleri araştırın: size rehberlik etmek için profilleri kullanın, sorunun ne olabileceğini hypothesize ve bir deneme veya kod değişikliği ile varsayımını test edin.</span><span class="sxs-lookup"><span data-stu-id="c99e9-133">Investigate failing tests by applying the scientific method: use profiles to guide you, hypothesize what the issue might be, and test your hypothesis with an experiment or code change.</span></span> <span data-ttu-id="c99e9-134">Düzenli test ile zaman içinde temel performans ölçümleri oluşturun, böylece performans üzerinde gerilemeyi ortaya tutmaya yönelik değişiklikleri ayırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c99e9-134">Establish baseline performance measurements over time with regular testing, so you can isolate changes that cause regressions in performance.</span></span> <span data-ttu-id="c99e9-135">Performans çalışmasına ciddi bir şekilde yaklaşarak, ihtiyacınız olmayan kod güncelleştirmeleriyle zaman harcamaktan kaçınabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c99e9-135">By approaching performance work in a rigorous way, you’ll avoid wasting time with code updates you don’t need.</span></span> 
  
### <a name="fact-3-good-tools-make-all-the-difference"></a><span data-ttu-id="c99e9-136">Olgu 3: İyi araçlar tüm farkları yapar</span><span class="sxs-lookup"><span data-stu-id="c99e9-136">Fact 3: Good tools make all the difference</span></span>  
 <span data-ttu-id="c99e9-137">İyi araçlar, en büyük performans sorunlarına (CPU, bellek veya disk) hızla göz atalım ve bu performans sorunlarına neden olan kodu bulmanıza yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="c99e9-137">Good tools let you drill quickly into the biggest performance issues (CPU, memory, or disk) and help you locate the code that causes those bottlenecks.</span></span> <span data-ttu-id="c99e9-138">Microsoft, [Visual Studio Profiler](/visualstudio/profiling/beginners-guide-to-performance-profiling) ve [PerfView](https://www.microsoft.com/download/details.aspx?id=28567)gibi çeşitli performans araçları ile birlikte sunulur.</span><span class="sxs-lookup"><span data-stu-id="c99e9-138">Microsoft ships a variety of performance tools such as [Visual Studio Profiler](/visualstudio/profiling/beginners-guide-to-performance-profiling) and [PerfView](https://www.microsoft.com/download/details.aspx?id=28567).</span></span> 
  
 <span data-ttu-id="c99e9-139">PerfView, disk g/ç, GC olayları ve bellek gibi derin sorunlara odaklanmanıza yardımcı olan ücretsiz ve başaramayabiliriz güçlü bir araçtır.</span><span class="sxs-lookup"><span data-stu-id="c99e9-139">PerfView is a free and amazingly powerful tool that helps you focus on deep issues such as disk I/O, GC events, and memory.</span></span> <span data-ttu-id="c99e9-140">Windows için performans ile ilgili [olay izleme](../wcf/samples/etw-tracing.md) (ETW) olaylarını yakalayabilir ve uygulama başına, işlem başına, yığın başına ve iş parçacığı bilgileri başına kolayca görüntüleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c99e9-140">You can capture performance-related [Event Tracing for Windows](../wcf/samples/etw-tracing.md) (ETW) events and view easily per app, per process, per stack, and per thread information.</span></span> <span data-ttu-id="c99e9-141">PerfView, uygulamanızın ne kadar ve ne tür bellek ayırdığını ve hangi işlevlerin veya çağrı yığınlarının bellek ayırmalarının ne kadar katkıda bulunduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="c99e9-141">PerfView shows you how much and what kind of memory your app allocates, and which functions or call stacks contribute how much to the memory allocations.</span></span> <span data-ttu-id="c99e9-142">Ayrıntılar için bkz. araçla birlikte sunulan zengin yardım konuları, tanıtımlar ve videolar (örneğin, Channel 9 ' da [PerfView öğreticileri](https://channel9.msdn.com/Series/PerfView-Tutorial) ).</span><span class="sxs-lookup"><span data-stu-id="c99e9-142">For details, see the rich help topics, demos, and videos included with the tool (such as the [PerfView tutorials](https://channel9.msdn.com/Series/PerfView-Tutorial) on Channel 9).</span></span> 
  
### <a name="fact-4-its-all-about-allocations"></a><span data-ttu-id="c99e9-143">Olgu 4: Ayırmaların hepsi hakkında</span><span class="sxs-lookup"><span data-stu-id="c99e9-143">Fact 4: It’s all about allocations</span></span>  
 <span data-ttu-id="c99e9-144">Bir yanıt veren .NET Framework uygulamasının, kabarcık sıralaması yerine hızlı sıralama kullanma gibi algoritmaların hepsi olduğunu düşünebilirsiniz, ancak bu durum böyle değildir.</span><span class="sxs-lookup"><span data-stu-id="c99e9-144">You might think that building a responsive .NET Framework app is all about algorithms, such as using quick sort instead of bubble sort, but that's not the case.</span></span> <span data-ttu-id="c99e9-145">Yanıt veren bir uygulama oluşturmanın en büyük faktörü, özellikle uygulamanız çok büyükse veya büyük miktarlarda veriyi işliyorsa bellek ayırmaktır.</span><span class="sxs-lookup"><span data-stu-id="c99e9-145">The biggest factor in building a responsive app is allocating memory, especially when your app is very large or processes large amounts of data.</span></span> 
  
 <span data-ttu-id="c99e9-146">Ayırmaktan ve önbelleğe alma stratejilerinin yönetilmesine neden olan yeni derleyici API 'Leri ile yanıt veren IDE deneyimleri oluşturmaya yönelik neredeyse tüm çalışmalar.</span><span class="sxs-lookup"><span data-stu-id="c99e9-146">Almost all the work to build responsive IDE experiences with the new compiler APIs involved avoiding allocations and managing caching strategies.</span></span> <span data-ttu-id="c99e9-147">PerfView izlemeleri, yeni C# ve Visual Basic derleyicilerinin PERFORMANSıNıN nadiren CPU ile bağlantılı olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="c99e9-147">PerfView traces show that the performance of the new C# and Visual Basic compilers is rarely CPU bound.</span></span> <span data-ttu-id="c99e9-148">Derleyiciler yüzlerce binlerce veya milyonlarca satırı okurken, meta verileri okurken veya üretilen kod yayırken g/ç bağlantılı olabilir.</span><span class="sxs-lookup"><span data-stu-id="c99e9-148">The compilers can be I/O bound when reading hundreds of thousands or millions of lines of code, reading metadata, or emitting generated code.</span></span> <span data-ttu-id="c99e9-149">Kullanıcı arabirimi iş parçacığı gecikmeleri çöp toplama nedeniyle neredeyse hepsi olur.</span><span class="sxs-lookup"><span data-stu-id="c99e9-149">The UI thread delays are nearly all due to garbage collection.</span></span> <span data-ttu-id="c99e9-150">.NET Framework GC, performans için yüksek düzeyde ayarlanmıştır ve uygulama kodu yürütüldüğü sırada işinin çoğunu eşzamanlı olarak yapar.</span><span class="sxs-lookup"><span data-stu-id="c99e9-150">The .NET Framework GC is highly tuned for performance and does much of its work concurrently while app code executes.</span></span> <span data-ttu-id="c99e9-151">Ancak, tek bir ayırma pahalı bir [Gen2](../../standard/garbage-collection/fundamentals.md) koleksiyonunu tetikleyip tüm iş parçacıklarını durdurabilir.</span><span class="sxs-lookup"><span data-stu-id="c99e9-151">However, a single allocation can trigger an expensive [gen2](../../standard/garbage-collection/fundamentals.md) collection, stopping all threads.</span></span> 
  
## <a name="common-allocations-and-examples"></a><span data-ttu-id="c99e9-152">Ortak ayırmalar ve örnekler</span><span class="sxs-lookup"><span data-stu-id="c99e9-152">Common allocations and examples</span></span>  
 <span data-ttu-id="c99e9-153">Bu bölümdeki örnek ifadelerde küçük görünen gizli ayırmalar vardır.</span><span class="sxs-lookup"><span data-stu-id="c99e9-153">The example expressions in this section have hidden allocations that appear small.</span></span> <span data-ttu-id="c99e9-154">Ancak, büyük bir uygulama ifadeleri yeterince uzun bir şekilde yürütülüyorsa, yüzlerce megabayt, hatta gigabayt, hatta ayırmaya neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="c99e9-154">However, if a large app executes the expressions enough times, they can causes hundreds of megabytes, even gigabytes, of allocations.</span></span> <span data-ttu-id="c99e9-155">Örneğin, düzenleyicide bir geliştiricinin yazı tipini uygulayan tek dakikalık testler, gigabayt bellek ayırmıştır ve performans ekibinin yazma senaryolarına odaklanmaya yol açmaktadır.</span><span class="sxs-lookup"><span data-stu-id="c99e9-155">For example, one-minute tests that simulated a developer’s typing in the editor allocated gigabytes of memory and led the performance team to focus on typing scenarios.</span></span> 
  
### <a name="boxing"></a><span data-ttu-id="c99e9-156">Kutulama</span><span class="sxs-lookup"><span data-stu-id="c99e9-156">Boxing</span></span>  
 <span data-ttu-id="c99e9-157">[Kutulama](../../csharp/programming-guide/types/boxing-and-unboxing.md) , normalde yığında veya veri yapılarında bulunan değer türleri bir nesneye sarmalandıktan sonra gerçekleşir.</span><span class="sxs-lookup"><span data-stu-id="c99e9-157">[Boxing](../../csharp/programming-guide/types/boxing-and-unboxing.md) occurs when value types that normally live on the stack or in data structures are wrapped in an object.</span></span> <span data-ttu-id="c99e9-158">Yani, verileri tutacak bir nesne ayırırsınız ve sonra nesneye bir işaretçi döndürülür.</span><span class="sxs-lookup"><span data-stu-id="c99e9-158">That is, you allocate an object to hold the data, and then return a pointer to the object.</span></span> <span data-ttu-id="c99e9-159">.NET Framework bazen bir yöntemin imzası veya bir depolama konumu türü nedeniyle değerlere izin vermez.</span><span class="sxs-lookup"><span data-stu-id="c99e9-159">The .NET Framework sometimes boxes values due to the signature of a method or the type of a storage location.</span></span> <span data-ttu-id="c99e9-160">Bir nesne içindeki bir değer türünü sarmalama, bellek ayırmaya neden olur.</span><span class="sxs-lookup"><span data-stu-id="c99e9-160">Wrapping a value type in an object causes memory allocation.</span></span> <span data-ttu-id="c99e9-161">Birçok paketleme işlemi uygulamanıza megabayt veya gigabayt 'lik ayırmaları katkıda bulunabilir, bu da uygulamanızın daha fazla GB 'a neden olacağı anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="c99e9-161">Many boxing operations can contribute megabytes or gigabytes of allocations to your app, which means that your app will cause more GCs.</span></span> <span data-ttu-id="c99e9-162">.NET Framework ve dil derleyicileri, mümkün olduğunda kutulamayı önler, ancak bazen en azından beklediğinde meydana gelir.</span><span class="sxs-lookup"><span data-stu-id="c99e9-162">The .NET Framework and the language compilers avoid boxing when possible, but sometimes it happens when you least expect it.</span></span> 
  
 <span data-ttu-id="c99e9-163">PerfView içinde kutulamayı görmek için bir izleme açın ve uygulamanızın işlem adı altında GC yığın ayırma yığınlarına bakın (tüm süreçlerdeki PerfView raporlarını unutmayın).</span><span class="sxs-lookup"><span data-stu-id="c99e9-163">To see boxing in PerfView, open a trace and look at GC Heap Alloc Stacks under your app’s process name (remember, PerfView reports on all processes).</span></span> <span data-ttu-id="c99e9-164"><xref:System.Int32?displayProperty=nameWithType> Ve<xref:System.Char?displayProperty=nameWithType> ayırma altında, gibi türler görürseniz, değer türlerini kutulanıyorsanız.</span><span class="sxs-lookup"><span data-stu-id="c99e9-164">If you see types like <xref:System.Int32?displayProperty=nameWithType> and <xref:System.Char?displayProperty=nameWithType> under allocations, you are boxing value types.</span></span> <span data-ttu-id="c99e9-165">Bu türlerden birini seçmek, paketlenmiş yığınları ve işlevleri gösterir.</span><span class="sxs-lookup"><span data-stu-id="c99e9-165">Choosing one of these types will show the stacks and functions in which they are boxed.</span></span> 
  
 <span data-ttu-id="c99e9-166">**Örnek 1: dize yöntemleri ve değer türü bağımsız değişkenleri**</span><span class="sxs-lookup"><span data-stu-id="c99e9-166">**Example 1: string methods and value type arguments**</span></span>  
  
 <span data-ttu-id="c99e9-167">Bu örnek kod, potansiyel olarak gereksiz ve aşırı kutulamayı göstermektedir:</span><span class="sxs-lookup"><span data-stu-id="c99e9-167">This sample code illustrates potentially unnecessary and excessive boxing:</span></span>  
  
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
  
 <span data-ttu-id="c99e9-168">Bu kod günlüğe kaydetme işlevselliği sağlar; bu nedenle, bir uygulama `Log` çoğunlukla milyonlarca kez işlev çağırabilir.</span><span class="sxs-lookup"><span data-stu-id="c99e9-168">This code provides logging functionality, so an app may call the `Log` function frequently, maybe millions of times.</span></span> <span data-ttu-id="c99e9-169">Sorun, `string.Format` <xref:System.String.Format%28System.String%2CSystem.Object%2CSystem.Object%29> aşırı yüklemeye çözümlenme çağrısının.</span><span class="sxs-lookup"><span data-stu-id="c99e9-169">The problem is that the call to `string.Format` resolves to the <xref:System.String.Format%28System.String%2CSystem.Object%2CSystem.Object%29> overload.</span></span> 
  
 <span data-ttu-id="c99e9-170">Bu aşırı yükleme, .NET Framework `int` bu yöntem çağrısına iletmek için değerleri nesnelere eklemesini gerektirir.</span><span class="sxs-lookup"><span data-stu-id="c99e9-170">This overload requires the .NET Framework to box the `int` values into objects to pass them to this method call.</span></span> <span data-ttu-id="c99e9-171">Kısmi bir çözüm `id.ToString()` , çağrı yapmak `string.Format` ve `size.ToString()` tüm dizeleri (nesneler) çağırmak ve geçirmek.</span><span class="sxs-lookup"><span data-stu-id="c99e9-171">A partial fix is to call `id.ToString()` and `size.ToString()` and pass all strings (which are objects) to the `string.Format` call.</span></span> <span data-ttu-id="c99e9-172">Çağırma `ToString()` bir dize ayırır, ancak bu ayırma içinde `string.Format`de olur.</span><span class="sxs-lookup"><span data-stu-id="c99e9-172">Calling `ToString()` does allocate a string, but that allocation will happen anyway inside `string.Format`.</span></span> 
  
 <span data-ttu-id="c99e9-173">Bu temel çağrının `string.Format` yalnızca dize birleştirmesi olduğunu düşünebilirsiniz, bu nedenle bunun yerine bu kodu yazabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="c99e9-173">You might consider that this basic call to `string.Format` is just string concatenation, so you might write this code instead:</span></span>  
  
```csharp  
var s = id.ToString() + ':' + size.ToString();  
```  
  
 <span data-ttu-id="c99e9-174">Ancak, bu kod satırı, ' a derlendiğinden <xref:System.String.Concat%28System.Object%2CSystem.Object%2CSystem.Object%29>bir kutulama ayırmayı tanıtır.</span><span class="sxs-lookup"><span data-stu-id="c99e9-174">However, that line of code introduces a boxing allocation because it compiles to <xref:System.String.Concat%28System.Object%2CSystem.Object%2CSystem.Object%29>.</span></span> <span data-ttu-id="c99e9-175">.NET Framework çağrılacak karakter sabit değerini Box olmalıdır`Concat`</span><span class="sxs-lookup"><span data-stu-id="c99e9-175">The .NET Framework must box the character literal to invoke `Concat`</span></span>  
  
 <span data-ttu-id="c99e9-176">**Örnek 1 için çözüm**</span><span class="sxs-lookup"><span data-stu-id="c99e9-176">**Fix for example 1**</span></span>  
  
 <span data-ttu-id="c99e9-177">Tüm düzeltmeler basittir.</span><span class="sxs-lookup"><span data-stu-id="c99e9-177">The complete fix is simple.</span></span> <span data-ttu-id="c99e9-178">Yalnızca karakter sabit değerini bir dize sabit değeri ile değiştirin, ancak dizeler zaten nesneler olduğundan kutulama yok:</span><span class="sxs-lookup"><span data-stu-id="c99e9-178">Just replace the character literal with a string literal, which incurs no boxing because strings are already objects:</span></span>  
  
```csharp  
var s = id.ToString() + ":" + size.ToString();  
```  
  
 <span data-ttu-id="c99e9-179">**Örnek 2: sabit listesi paketleme**</span><span class="sxs-lookup"><span data-stu-id="c99e9-179">**Example 2: enum boxing**</span></span>  
  
 <span data-ttu-id="c99e9-180">Bu örnek, özellikle sözlük arama işlemlerinde listeleme türlerinin sık sık kullanılması nedeniyle C# yeni ve Visual Basic derleyicilerde çok büyük miktarda ayrılmasından sorumludur.</span><span class="sxs-lookup"><span data-stu-id="c99e9-180">This example was responsible for a huge amount of allocation in the new C# and Visual Basic compilers due to frequent use of enumeration types, especially in dictionary lookup operations.</span></span> 
  
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
  
 <span data-ttu-id="c99e9-181">Bu sorun çok daha hafif.</span><span class="sxs-lookup"><span data-stu-id="c99e9-181">This problem is very subtle.</span></span> <span data-ttu-id="c99e9-182">Yöntem, uygulama nedenleriyle numaralandırma türünün <xref:System.Enum.GetHashCode> temel gösterimine bir kutu olduğundan PerfView bunu kutulama olarak raporlayabilir.</span><span class="sxs-lookup"><span data-stu-id="c99e9-182">PerfView would report this as <xref:System.Enum.GetHashCode> boxing because the method boxes the underlying representation of the enumeration type, for implementation reasons.</span></span> <span data-ttu-id="c99e9-183">PerfView 'a <xref:System.Enum.GetHashCode>yakından bakarsanız, her bir çağrı için iki paketleme ayırması görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c99e9-183">If you look closely in PerfView, you may see two boxing allocations for each call to <xref:System.Enum.GetHashCode>.</span></span> <span data-ttu-id="c99e9-184">Derleyici bir tane ekler ve .NET Framework diğerini ekler.</span><span class="sxs-lookup"><span data-stu-id="c99e9-184">The compiler inserts one, and the .NET Framework inserts the other.</span></span> 
  
 <span data-ttu-id="c99e9-185">**Örneğin 2**</span><span class="sxs-lookup"><span data-stu-id="c99e9-185">**Fix for example 2**</span></span>  
  
 <span data-ttu-id="c99e9-186">' İ çağırmadan <xref:System.Enum.GetHashCode>önce temeldeki temsilde kaldırarak her iki ayırmadan kolayca kaçınabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="c99e9-186">You can easily avoid both allocations by casting to the underlying representation before calling <xref:System.Enum.GetHashCode>:</span></span>  
  
```csharp  
((int)color).GetHashCode()  
```  
  
 <span data-ttu-id="c99e9-187">Numaralandırma türlerinde <xref:System.Enum.HasFlag%28System.Enum%29?displayProperty=nameWithType> başka bir ortak paketleme kaynağı yöntemidir.</span><span class="sxs-lookup"><span data-stu-id="c99e9-187">Another common source of boxing on enumeration types is the <xref:System.Enum.HasFlag%28System.Enum%29?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="c99e9-188">Öğesine <xref:System.Enum.HasFlag%28System.Enum%29> geçirilen bağımsız değişken kutulanmış olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="c99e9-188">The argument passed to <xref:System.Enum.HasFlag%28System.Enum%29> has to be boxed.</span></span> <span data-ttu-id="c99e9-189">Çoğu durumda, çağrıları <xref:System.Enum.HasFlag%28System.Enum%29?displayProperty=nameWithType> bit düzeyinde bir test ile değiştirmek daha basit ve ayırma ücretsizdir.</span><span class="sxs-lookup"><span data-stu-id="c99e9-189">In most cases, replacing calls to <xref:System.Enum.HasFlag%28System.Enum%29?displayProperty=nameWithType> with a bitwise test is simpler and allocation-free.</span></span> 
  
 <span data-ttu-id="c99e9-190">İlk performans olgusunu göz önünde bulundurun (yani, zamanından önce iyileştirmeyin) ve tüm kodunuzu bu şekilde yeniden yazmayı başlamayamazsınız.</span><span class="sxs-lookup"><span data-stu-id="c99e9-190">Keep the first performance fact in mind (that is, don’t prematurely optimize) and don’t start rewriting all your code in this way.</span></span> <span data-ttu-id="c99e9-191">Bu paketleme maliyetlerinden haberdar olun, ancak yalnızca uygulamanızın profilini oluşturup etkin noktaları bulduktan sonra kodunuzu değiştirin.</span><span class="sxs-lookup"><span data-stu-id="c99e9-191">Be aware of these boxing costs, but change your code only after profiling your app and finding the hot spots.</span></span> 
  
### <a name="strings"></a><span data-ttu-id="c99e9-192">Dizeler</span><span class="sxs-lookup"><span data-stu-id="c99e9-192">Strings</span></span>  
 <span data-ttu-id="c99e9-193">Dize işlemeleri, ayırmaların en büyük küllerinin bazılarıdır ve genellikle ilk beş tahsisde PerfView ' de görünür.</span><span class="sxs-lookup"><span data-stu-id="c99e9-193">String manipulations are some of the biggest culprits for allocations, and they often show up in PerfView in the top five allocations.</span></span> <span data-ttu-id="c99e9-194">Programlar serileştirme, JSON ve REST API 'Leri için dizeler kullanır.</span><span class="sxs-lookup"><span data-stu-id="c99e9-194">Programs use strings for serialization, JSON, and REST APIs.</span></span> <span data-ttu-id="c99e9-195">Sabit Listesi türlerini kullanamıyoruz, sistemlerle birlikte çalışmak için, dizeleri programlama sabitleri olarak kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c99e9-195">You can use strings as programmatic constants for interoperating with systems when you can’t use enumeration types.</span></span> <span data-ttu-id="c99e9-196">Profil oluşturma, dizelerin performansı yüksek oranda etkilediğini gösteriyorsa,,,, vb. <xref:System.String> gibi yöntemlere <xref:System.String.Substring%2A> <xref:System.String.Format%2A> <xref:System.String.Concat%2A> <xref:System.String.Split%2A> <xref:System.String.Join%2A>yönelik çağrılar olup olmadığına bakın.</span><span class="sxs-lookup"><span data-stu-id="c99e9-196">When your profiling shows that strings are highly affecting performance, look for calls to <xref:System.String> methods such as <xref:System.String.Format%2A>, <xref:System.String.Concat%2A>, <xref:System.String.Split%2A>, <xref:System.String.Join%2A>, <xref:System.String.Substring%2A>, and so on.</span></span> <span data-ttu-id="c99e9-197">Birçok <xref:System.Text.StringBuilder> parçadan bir dize oluşturma maliyetini önlemek için kullanmak yardımcı olur, ancak <xref:System.Text.StringBuilder> nesnenin tahsisi bile yönetmeniz gereken bir performans sorunu olabilir.</span><span class="sxs-lookup"><span data-stu-id="c99e9-197">Using <xref:System.Text.StringBuilder> to avoid the cost of creating one string from many pieces helps, but even allocating the <xref:System.Text.StringBuilder> object might become a bottleneck that you need to manage.</span></span> 
  
 <span data-ttu-id="c99e9-198">**Örnek 3: dize işlemleri**</span><span class="sxs-lookup"><span data-stu-id="c99e9-198">**Example 3: string operations**</span></span>  
  
 <span data-ttu-id="c99e9-199">Derleyici C# , BIÇIMLI bir XML belgesi açıklamasının metnini yazan bu koda sahipti:</span><span class="sxs-lookup"><span data-stu-id="c99e9-199">The C# compiler had this code that writes the text of a formatted XML doc comment:</span></span>  
  
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
  
 <span data-ttu-id="c99e9-200">Bu kodun çok sayıda dize düzenlemesi olduğunu görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c99e9-200">You can see that this code does a lot of string manipulation.</span></span> <span data-ttu-id="c99e9-201">Kod, satırları ayrı dizelere bölmek, boşluk kırpmak, bağımsız değişkenin `text` bir XML belgesi yorumu olup olmadığını denetlemek ve satırlardan alt dizeleri ayıklamak için kitaplık yöntemlerini kullanır.</span><span class="sxs-lookup"><span data-stu-id="c99e9-201">The code uses library methods to split lines into separate strings, to trim white space, to check whether the argument `text` is an XML documentation comment, and to extract substrings from lines.</span></span> 
  
 <span data-ttu-id="c99e9-202">İçindeki `WriteFormattedDocComment`ilk satırda `text.Split` , çağrı her çağrıldığında bağımsız değişken olarak yeni bir üç öğeli dizi ayırır.</span><span class="sxs-lookup"><span data-stu-id="c99e9-202">On the first line inside `WriteFormattedDocComment`, the `text.Split` call allocates a new three-element array as the argument every time it’s called.</span></span> <span data-ttu-id="c99e9-203">Derleyicinin her seferinde bu diziyi ayırmak için kod yaymalıdır.</span><span class="sxs-lookup"><span data-stu-id="c99e9-203">The compiler has to emit code to allocate this array each time.</span></span> <span data-ttu-id="c99e9-204">Bunun nedeni, derleyicinin diziyi dizinin bir yere <xref:System.String.Split%2A> depoladığını, daha sonra öğesine yapılan çağrıları etkileyecek şekilde `WriteFormattedDocComment`depolayabileceğini bilmez.</span><span class="sxs-lookup"><span data-stu-id="c99e9-204">That’s because the compiler doesn’t know if <xref:System.String.Split%2A> stores the array somewhere where the array might be modified by other code, which would affect later calls to `WriteFormattedDocComment`.</span></span> <span data-ttu-id="c99e9-205"><xref:System.String.Split%2A> Ayrıca çağrısı, içindeki `text` her satır için bir dize ayırır ve işlemi gerçekleştirmek için diğer belleği ayırır.</span><span class="sxs-lookup"><span data-stu-id="c99e9-205">The call to <xref:System.String.Split%2A> also allocates a string for every line in `text` and allocates other memory to perform the operation.</span></span> 
  
 <span data-ttu-id="c99e9-206">`WriteFormattedDocComment`<xref:System.String.TrimStart%2A> yöntemine üç çağrı içerir.</span><span class="sxs-lookup"><span data-stu-id="c99e9-206">`WriteFormattedDocComment` has three calls to the <xref:System.String.TrimStart%2A> method.</span></span> <span data-ttu-id="c99e9-207">İkisi de yinelenen iş ve ayırmaları yineleyen iç Döngülerde bulunur.</span><span class="sxs-lookup"><span data-stu-id="c99e9-207">Two are in inner loops that duplicate work and allocations.</span></span> <span data-ttu-id="c99e9-208">Önemli hale getirmek için bir bağımsız değişken <xref:System.String.TrimStart%2A> olmadan yöntemi çağırmak, dize sonucuna ek olarak boş bir dizi `params` (parametresi için) ayırır.</span><span class="sxs-lookup"><span data-stu-id="c99e9-208">To make matters worse, calling the <xref:System.String.TrimStart%2A> method with no arguments allocates an empty array (for the `params` parameter) in addition to the string result.</span></span> 
  
 <span data-ttu-id="c99e9-209">Son olarak, genellikle yeni bir dize ayıran <xref:System.String.Substring%2A> yöntemine bir çağrı vardır.</span><span class="sxs-lookup"><span data-stu-id="c99e9-209">Lastly, there is a call to the <xref:System.String.Substring%2A> method, which usually allocates a new string.</span></span> 
  
 <span data-ttu-id="c99e9-210">**3. örnekte çözüm**</span><span class="sxs-lookup"><span data-stu-id="c99e9-210">**Fix for example 3**</span></span>  
  
 <span data-ttu-id="c99e9-211">Önceki örneklerden farklı olarak, küçük düzenlemeler bu ayırmaları düzeltemedi.</span><span class="sxs-lookup"><span data-stu-id="c99e9-211">Unlike the earlier examples, small edits cannot fix these allocations.</span></span> <span data-ttu-id="c99e9-212">Geri dönüp soruna bakmanız ve farklı bir yaklaşım yapmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="c99e9-212">You need to step back, look at the problem, and approach it differently.</span></span> <span data-ttu-id="c99e9-213">Örneğin, bağımsız değişkeninin `WriteFormattedDocComment()` yöntemin ihtiyacı olan tüm bilgilere sahip bir dize olduğunu ve bu nedenle kodun çok sayıda kısmi dize ayırmak yerine daha fazla dizin oluşturulmasını sağlayabileceğini fark edersiniz.</span><span class="sxs-lookup"><span data-stu-id="c99e9-213">For example, you'll notice that the argument to `WriteFormattedDocComment()` is a string that has all the information that the method needs, so the code could do more indexing instead of allocating many partial strings.</span></span> 
  
 <span data-ttu-id="c99e9-214">Derleyicinin performans ekibi, tüm bu ayırmaların şu şekilde kodla aynı şekilde olduğunu.</span><span class="sxs-lookup"><span data-stu-id="c99e9-214">The compiler’s performance team tackled all these allocations with code like this:</span></span>  
  
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
  
 <span data-ttu-id="c99e9-215">`WriteFormattedDocComment()` Boş`params` bir dizi ile birlikte bir diziyi, birkaç alt dizeyi ve kırpılmış alt dizeyi ayırmış ilk sürümü.</span><span class="sxs-lookup"><span data-stu-id="c99e9-215">The first version of `WriteFormattedDocComment()` allocated an array, several substrings, and a trimmed substring along with an empty `params` array.</span></span> <span data-ttu-id="c99e9-216">Ayrıca "///" için kontrol edilir.</span><span class="sxs-lookup"><span data-stu-id="c99e9-216">It also checked for "///".</span></span> <span data-ttu-id="c99e9-217">Düzeltilen kod yalnızca dizin oluşturmayı kullanır ve hiçbir şey ayırır.</span><span class="sxs-lookup"><span data-stu-id="c99e9-217">The revised code uses only indexing and allocates nothing.</span></span> <span data-ttu-id="c99e9-218">Boşluk olmayan ilk karakteri bulur ve sonra dizenin "///" ile başlatılıp başlatılmadığını görmek için karaktere göre karakteri denetler.</span><span class="sxs-lookup"><span data-stu-id="c99e9-218">It finds the first character that is not white space, and then checks character by character to see if the string starts with "///".</span></span> <span data-ttu-id="c99e9-219">Yeni kod, boşluk `IndexOfFirstNonWhiteSpaceChar` olmayan bir <xref:System.String.TrimStart%2A> karakterin gerçekleştiği ilk dizini (belirtilen başlangıç dizininden sonra) döndürmek için yerine kullanır.</span><span class="sxs-lookup"><span data-stu-id="c99e9-219">The new code uses `IndexOfFirstNonWhiteSpaceChar` instead of <xref:System.String.TrimStart%2A> to return the first index (after a specified start index) where a non-white-space character occurs.</span></span> <span data-ttu-id="c99e9-220">Düzeltme tamamlanmaz, ancak tüm çözümler için benzer düzeltmelerin nasıl uygulanacağını görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c99e9-220">The fix is not complete, but you can see how to apply similar fixes for a complete solution.</span></span> <span data-ttu-id="c99e9-221">Bu yaklaşımı kodun tamamında uygulayarak içindeki `WriteFormattedDocComment()`tüm ayırmaları kaldırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c99e9-221">By applying this approach throughout the code, you can remove all allocations in `WriteFormattedDocComment()`.</span></span> 
  
 <span data-ttu-id="c99e9-222">**Örnek 4: Öncesinde**</span><span class="sxs-lookup"><span data-stu-id="c99e9-222">**Example 4: StringBuilder**</span></span>  
  
 <span data-ttu-id="c99e9-223">Bu örnek bir <xref:System.Text.StringBuilder> nesnesi kullanır.</span><span class="sxs-lookup"><span data-stu-id="c99e9-223">This example uses a <xref:System.Text.StringBuilder> object.</span></span> <span data-ttu-id="c99e9-224">Aşağıdaki işlev genel türler için tam bir tür adı üretir:</span><span class="sxs-lookup"><span data-stu-id="c99e9-224">The following function generates a full type name for generic types:</span></span>  
  
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
  
 <span data-ttu-id="c99e9-225">Odak, yeni <xref:System.Text.StringBuilder> bir örnek oluşturan satırdır.</span><span class="sxs-lookup"><span data-stu-id="c99e9-225">The focus is on the line that creates a new <xref:System.Text.StringBuilder> instance.</span></span> <span data-ttu-id="c99e9-226">Kod, <xref:System.Text.StringBuilder> uygulama içinde ve iç `sb.ToString()` ayırmalar için bir ayırmaya neden olur, ancak dize sonucunu istiyorsanız bu ayırmaları kontrol edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c99e9-226">The code causes an allocation for `sb.ToString()` and internal allocations within the <xref:System.Text.StringBuilder> implementation, but you cannot control those allocations if you want the string result.</span></span> 
  
 <span data-ttu-id="c99e9-227">**Örneğin 4 için çözüm**</span><span class="sxs-lookup"><span data-stu-id="c99e9-227">**Fix for example 4**</span></span>  
  
 <span data-ttu-id="c99e9-228">`StringBuilder` Nesne ayırmayı onarmak için nesneyi önbelleğe alma.</span><span class="sxs-lookup"><span data-stu-id="c99e9-228">To fix the `StringBuilder` object allocation, cache the  object.</span></span> <span data-ttu-id="c99e9-229">Oluşan tek bir örneği önbelleğe almak bile, performansı önemli ölçüde iyileştirebilir.</span><span class="sxs-lookup"><span data-stu-id="c99e9-229">Even caching a single instance that might get thrown away can improve performance significantly.</span></span> <span data-ttu-id="c99e9-230">Bu, yeni ilk ve son satırlar hariç tüm kodu atlayarak işlevin yeni uygulamasıdır:</span><span class="sxs-lookup"><span data-stu-id="c99e9-230">This is the function’s new implementation, omitting all the code except for the new first and last lines:</span></span>  
  
```csharp  
// Constructs a name like "MyType<T1, T2, T3>"  
public string GenerateFullTypeName(string name, int arity)  
{  
    StringBuilder sb = AcquireBuilder();  
    /* Use sb as before */  
    return GetStringAndReleaseBuilder(sb);  
}  
```  
  
 <span data-ttu-id="c99e9-231">Anahtar parçalar yeni `AcquireBuilder()` ve `GetStringAndReleaseBuilder()` işlevlerdir:</span><span class="sxs-lookup"><span data-stu-id="c99e9-231">The key parts are the new `AcquireBuilder()` and `GetStringAndReleaseBuilder()` functions:</span></span>  
  
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
  
 <span data-ttu-id="c99e9-232">Yeni derleyiciler iş parçacığı kullandığından bu uygulamalar,<xref:System.ThreadStaticAttribute> <xref:System.Text.StringBuilder>önbelleğe almak için bir iş parçacığı statik alanı (özniteliği) kullanır ve `ThreadStatic` büyük olasılıkla bildirime geçebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c99e9-232">Because the new compilers use threading, these implementations use a thread-static field (<xref:System.ThreadStaticAttribute> attribute) to cache the <xref:System.Text.StringBuilder>, and you likely can forgo the `ThreadStatic` declaration.</span></span> <span data-ttu-id="c99e9-233">Thread-static alanı, bu kodu yürüten her iş parçacığı için benzersiz bir değer tutar.</span><span class="sxs-lookup"><span data-stu-id="c99e9-233">The thread-static field holds a unique value for each thread that executes this code.</span></span> 
  
 <span data-ttu-id="c99e9-234">`AcquireBuilder()`bir tane varsa <xref:System.Text.StringBuilder> , onu temizleyip, alanı veya önbelleği null olarak ayarlayarak önbelleğe alınmış örneği döndürür.</span><span class="sxs-lookup"><span data-stu-id="c99e9-234">`AcquireBuilder()` returns the cached <xref:System.Text.StringBuilder> instance if there is one, after clearing it and setting the field or cache to null.</span></span> <span data-ttu-id="c99e9-235">Aksi takdirde `AcquireBuilder()` , yeni bir örnek oluşturur ve alan ya da önbelleğin null olarak ayarlanması için onu döndürür.</span><span class="sxs-lookup"><span data-stu-id="c99e9-235">Otherwise, `AcquireBuilder()` creates a new instance and returns it, leaving the field or cache set to null.</span></span> 
  
 <span data-ttu-id="c99e9-236">İle <xref:System.Text.StringBuilder> işiniz bittiğinde `GetStringAndReleaseBuilder()` ,<xref:System.Text.StringBuilder> dize sonucunu elde etmek için çağırın, örneği alan veya önbellekte kaydedin ve sonra sonucu geri döndürün.</span><span class="sxs-lookup"><span data-stu-id="c99e9-236">When you’re done with <xref:System.Text.StringBuilder> , you call `GetStringAndReleaseBuilder()` to get the string result, save the <xref:System.Text.StringBuilder> instance in the field or cache, and then return the result.</span></span> <span data-ttu-id="c99e9-237">Yürütmenin bu kodu yeniden girmesi ve birden çok <xref:System.Text.StringBuilder> nesne oluşturmak (nadiren gerçekleşse de) mümkündür.</span><span class="sxs-lookup"><span data-stu-id="c99e9-237">It is possible for execution to re-enter this code and to create multiple <xref:System.Text.StringBuilder> objects (although that rarely happens).</span></span> <span data-ttu-id="c99e9-238">Kod, daha sonra kullanılmak üzere yalnızca <xref:System.Text.StringBuilder> son yayınlanan örneği kaydeder.</span><span class="sxs-lookup"><span data-stu-id="c99e9-238">The code saves only the last released <xref:System.Text.StringBuilder> instance for later use.</span></span> <span data-ttu-id="c99e9-239">Bu basit önbelleğe alma stratejisi, yeni derleyicilerde ayırmaları önemli ölçüde düşürür.</span><span class="sxs-lookup"><span data-stu-id="c99e9-239">This simple caching strategy significantly reduced allocations in the new compilers.</span></span> <span data-ttu-id="c99e9-240">.NET Framework ve MSBuild 'in ("MSBuild") bölümleri, performansı artırmak için benzer bir teknik kullanır.</span><span class="sxs-lookup"><span data-stu-id="c99e9-240">Parts of the .NET Framework and MSBuild ("MSBuild") use a similar technique to improve performance.</span></span> 
  
 <span data-ttu-id="c99e9-241">Bu basit önbelleğe alma stratejisi, boyut üst sınırı içerdiğinden iyi önbellek tasarımına uyar.</span><span class="sxs-lookup"><span data-stu-id="c99e9-241">This simple caching strategy adheres to good cache design because it has a size cap.</span></span> <span data-ttu-id="c99e9-242">Ancak, artık orijinalden daha fazla kod vardır. Bu, daha fazla bakım maliyeti anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="c99e9-242">However, there is more code now than in the original, which means more maintenance costs.</span></span> <span data-ttu-id="c99e9-243">Önbelleğe alma stratejisini yalnızca bir performans sorunu bullediyseniz benimsemelisiniz ve PerfView, ayırmaların önemli bir katkı olduğunu <xref:System.Text.StringBuilder> göstermiştir.</span><span class="sxs-lookup"><span data-stu-id="c99e9-243">You should adopt the caching strategy only if you’ve found a performance problem, and PerfView has shown that <xref:System.Text.StringBuilder> allocations are a significant contributor.</span></span> 
  
### <a name="linq-and-lambdas"></a><span data-ttu-id="c99e9-244">LINQ ve Lambdalar</span><span class="sxs-lookup"><span data-stu-id="c99e9-244">LINQ and lambdas</span></span>  
<span data-ttu-id="c99e9-245">Lambda ifadeleriyle birlikte, dil ile tümleşik sorgu (LINQ), üretkenlik özelliğine bir örnektir.</span><span class="sxs-lookup"><span data-stu-id="c99e9-245">Language-Integrated Query (LINQ), in conjunction with lambda expressions, is an example of a productivity feature.</span></span> <span data-ttu-id="c99e9-246">Ancak, kullanımı zaman içinde performans üzerinde önemli bir etkiye sahip olabilir ve kodunuzu yeniden yazmanız gerektiğini fark edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c99e9-246">However, its use may have a significant impact on performance over time, and you might find you need to rewrite your code.</span></span>
  
 <span data-ttu-id="c99e9-247">**Örnek 5: Lambdalar,\<liste T > ve IEnumerable\<T >**</span><span class="sxs-lookup"><span data-stu-id="c99e9-247">**Example 5: Lambdas, List\<T>, and IEnumerable\<T>**</span></span>  
  
 <span data-ttu-id="c99e9-248">Bu örnek, bir ad dizesi verildiğinde derleyicinin modelinde bir sembol bulmak için [LINQ ve işlevsel stil kodu](https://blogs.msdn.microsoft.com/charlie/2007/01/27/anders-hejlsberg-on-linq-and-functional-programming/) kullanır:</span><span class="sxs-lookup"><span data-stu-id="c99e9-248">This example uses [LINQ and functional style code](https://blogs.msdn.microsoft.com/charlie/2007/01/27/anders-hejlsberg-on-linq-and-functional-programming/) to find a symbol in the compiler’s model, given a name string:</span></span>  
  
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
  
 <span data-ttu-id="c99e9-249">Yeni derleyici ve IDE deneyimleri, çok sık çağrı `FindMatchingSymbol()` üzerine oluşturulmuştur ve bu işlevin tek satırlık kod satırında birkaç gizli ayırma vardır.</span><span class="sxs-lookup"><span data-stu-id="c99e9-249">The new compiler and the IDE experiences built on it call `FindMatchingSymbol()` very frequently, and there are several hidden allocations in this function’s single line of code.</span></span> <span data-ttu-id="c99e9-250">Bu ayırmaları incelemek için, önce işlevin tek satırlık kod satırını iki satıra ayırın:</span><span class="sxs-lookup"><span data-stu-id="c99e9-250">To examine those allocations, first split the function’s single line of code into two lines:</span></span>  
  
```csharp  
Func<Symbol, bool> predicate = s => s.Name == name;  
     return symbols.FirstOrDefault(predicate);  
```  
  
 <span data-ttu-id="c99e9-251">İlk satırda, [lambda ifadesi](../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md) `s => s.Name == name` yerel değişken `name` [üzerinde kapanır](https://blogs.msdn.microsoft.com/ericlippert/2003/09/17/what-are-closures/) .</span><span class="sxs-lookup"><span data-stu-id="c99e9-251">In the first line, the [lambda expression](../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md) `s => s.Name == name` [closes over](https://blogs.msdn.microsoft.com/ericlippert/2003/09/17/what-are-closures/) the local variable `name`.</span></span> <span data-ttu-id="c99e9-252">Diğer bir deyişle, `predicate` tutan [temsilci](../../csharp/language-reference/keywords/delegate.md) için bir nesne ayırmanın yanı sıra, kod, değerini `name`yakalayan ortamı tutmak için bir statik sınıf ayırır.</span><span class="sxs-lookup"><span data-stu-id="c99e9-252">This means that in addition to allocating an object for the [delegate](../../csharp/language-reference/keywords/delegate.md) that `predicate` holds, the code allocates a static class to hold the environment that captures the value of `name`.</span></span> <span data-ttu-id="c99e9-253">Derleyici, aşağıdaki gibi bir kod üretir:</span><span class="sxs-lookup"><span data-stu-id="c99e9-253">The compiler generates code like the following:</span></span>  
  
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
  
 <span data-ttu-id="c99e9-254">İki `new` ayırma (ortam sınıfı için bir diğeri temsilci için bir tane) artık açıktır.</span><span class="sxs-lookup"><span data-stu-id="c99e9-254">The two `new` allocations (one for the environment class and one for the delegate) are explicit now.</span></span> 
  
 <span data-ttu-id="c99e9-255">Şimdi çağrısına `FirstOrDefault`bakın.</span><span class="sxs-lookup"><span data-stu-id="c99e9-255">Now look at the call to `FirstOrDefault`.</span></span> <span data-ttu-id="c99e9-256">Bu <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> tür genişletme yöntemi çok fazla bir ayırma doğurur.</span><span class="sxs-lookup"><span data-stu-id="c99e9-256">This extension method on the <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> type incurs an allocation too.</span></span> <span data-ttu-id="c99e9-257">, `FirstOrDefault` İlk bağımsız <xref:System.Collections.Generic.IEnumerable%601> değişkeni olarak bir nesne kullandığından, aşağıdaki koda yapılan çağrıyı genişletebilirsiniz (bir tartışmaya yönelik bir bit Basitleştirilmiş):</span><span class="sxs-lookup"><span data-stu-id="c99e9-257">Because `FirstOrDefault` takes an <xref:System.Collections.Generic.IEnumerable%601> object as its first argument, you can expand the call to the following code (simplified a bit for discussion):</span></span>  
  
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
  
 <span data-ttu-id="c99e9-258">`symbols` Değişkenin türü<xref:System.Collections.Generic.List%601>.</span><span class="sxs-lookup"><span data-stu-id="c99e9-258">The `symbols` variable has type <xref:System.Collections.Generic.List%601>.</span></span> <span data-ttu-id="c99e9-259">Koleksiyon <xref:System.Collections.Generic.List%601> türü uygular <xref:System.Collections.Generic.IEnumerable%601> ve Cleverly, ile <xref:System.Collections.Generic.List%601> uygulayan bir `struct`Numaralandırıcı<xref:System.Collections.Generic.IEnumerator%601> (arabirim) tanımlar.</span><span class="sxs-lookup"><span data-stu-id="c99e9-259">The <xref:System.Collections.Generic.List%601> collection type implements <xref:System.Collections.Generic.IEnumerable%601> and cleverly defines an enumerator (<xref:System.Collections.Generic.IEnumerator%601> interface) that <xref:System.Collections.Generic.List%601> implements with a `struct`.</span></span> <span data-ttu-id="c99e9-260">Sınıf yerine bir yapı kullanılması, genellikle atık toplama performansını etkileyebilecek yığın ayırmalarının önüne geçmek anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="c99e9-260">Using a structure instead of a class means that you usually avoid any heap allocations, which, in turn, can affect garbage collection performance.</span></span> <span data-ttu-id="c99e9-261">Numaralandırıcılar genellikle, çağrı yığınında döndürüldüğünden `foreach` Numaralandırıcı yapısını kullanan dilin döngüsü ile kullanılır.</span><span class="sxs-lookup"><span data-stu-id="c99e9-261">Enumerators are typically used with the language’s `foreach` loop, which uses the enumerator structure as it is returned on the call stack.</span></span> <span data-ttu-id="c99e9-262">Bir nesne için yer açmak üzere çağrı yığını işaretçisinin arttırılmasının, yığın ayırma yöntemi GC 'yi etkilemez.</span><span class="sxs-lookup"><span data-stu-id="c99e9-262">Incrementing the call stack pointer to make room for an object does not affect GC the way a heap allocation does.</span></span> 
  
 <span data-ttu-id="c99e9-263">Genişletilmiş `FirstOrDefault` çağrı durumunda kodun bir <xref:System.Collections.Generic.IEnumerable%601>üzerinde çağrı `GetEnumerator()` yapması gerekir.</span><span class="sxs-lookup"><span data-stu-id="c99e9-263">In the case of the expanded `FirstOrDefault` call, the code needs to call `GetEnumerator()` on an <xref:System.Collections.Generic.IEnumerable%601>.</span></span> <span data-ttu-id="c99e9-264">`symbols` <xref:System.Collections.Generic.List%601>Türü değişkenineatama`IEnumerable<Symbol>` , gerçek nesnenin bir olduğu bilgileri kaybeder. `enumerable`</span><span class="sxs-lookup"><span data-stu-id="c99e9-264">Assigning `symbols` to the `enumerable` variable of type `IEnumerable<Symbol>` loses the information that the actual object is a <xref:System.Collections.Generic.List%601>.</span></span> <span data-ttu-id="c99e9-265">Bu, kod numaralandırıcıyı ile `enumerable.GetEnumerator()`aldığında, .NET Framework `enumerator` değişkene atamak için döndürülen yapıyı Box ' a sahip olduğu anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="c99e9-265">This means that when the code fetches the enumerator with `enumerable.GetEnumerator()`, the .NET Framework has to box the returned structure to assign it to the `enumerator` variable.</span></span> 
  
 <span data-ttu-id="c99e9-266">**5. örnek için çözüm**</span><span class="sxs-lookup"><span data-stu-id="c99e9-266">**Fix for example 5**</span></span>  
  
 <span data-ttu-id="c99e9-267">Bu çözüm aşağıdaki şekilde yeniden `FindMatchingSymbol` yazmak için, tek bir kod satırını, hala net, okunması ve anlaşılması kolay ve bakımı kolay olan altı satırlık kod ile değiştirir:</span><span class="sxs-lookup"><span data-stu-id="c99e9-267">The fix is to rewrite `FindMatchingSymbol` as follows, replacing its single line of code with six lines of code that are still concise, easy to read and understand, and easy to maintain:</span></span>  
  
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
  
 <span data-ttu-id="c99e9-268">Bu kod LINQ uzantı yöntemleri, Lambdalar veya Numaralandırıcılar kullanmaz ve hiçbir ayırma yapmaz.</span><span class="sxs-lookup"><span data-stu-id="c99e9-268">This code doesn’t use LINQ extension methods, lambdas, or enumerators, and it incurs no allocations.</span></span> <span data-ttu-id="c99e9-269">Derleyici `symbols` koleksiyonun bir <xref:System.Collections.Generic.List%601> olduğunu görebildiğinden ve ortaya çıkan Numaralandırıcı (bir yapı), kutulamayı önlemek için doğru türe sahip yerel bir değişkene bağlayabildiğinden, hiçbir ayırma yoktur.</span><span class="sxs-lookup"><span data-stu-id="c99e9-269">There are no allocations because the compiler can see that the `symbols` collection is a <xref:System.Collections.Generic.List%601> and can bind the resulting enumerator (a structure) to a local variable with the right type to avoid boxing.</span></span> <span data-ttu-id="c99e9-270">Bu işlevin orijinal sürümü C# ve .NET Framework verimliliği hakkında harika bir örnektir.</span><span class="sxs-lookup"><span data-stu-id="c99e9-270">The original version of this function was a great example of the expressive power of C# and the productivity of the .NET Framework.</span></span> <span data-ttu-id="c99e9-271">Bu yeni ve daha verimli sürüm, sürdürmek için herhangi bir karmaşık kod eklemeden bu nitelikleri korur.</span><span class="sxs-lookup"><span data-stu-id="c99e9-271">This new and more efficient version preserves those qualities without adding any complex code to maintain.</span></span> 
  
### <a name="async-method-caching"></a><span data-ttu-id="c99e9-272">Zaman uyumsuz metot önbelleğe alma</span><span class="sxs-lookup"><span data-stu-id="c99e9-272">Async method caching</span></span>  

<span data-ttu-id="c99e9-273">Sonraki örnek, önbelleğe alınmış sonuçları [zaman uyumsuz](../../csharp/programming-guide/concepts/async/index.md) bir yöntemde kullanmaya çalıştığınızda yaygın bir sorunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="c99e9-273">The next example shows a common problem when you try to use cached results in an [async](../../csharp/programming-guide/concepts/async/index.md) method.</span></span>
  
 <span data-ttu-id="c99e9-274">**Örnek 6: zaman uyumsuz metotlarda önbelleğe alma**</span><span class="sxs-lookup"><span data-stu-id="c99e9-274">**Example 6: caching in async methods**</span></span>  
  
 <span data-ttu-id="c99e9-275">New C# ve Visual Basic derleyicileri üzerinde oluşturulan VISUAL Studio IDE özellikleri genellikle sözdizimi ağaçlarını getirir ve derleyiciler, Visual Studio 'yu yanıt vermeye devam etmek için zaman uyumsuz olarak kullanır.</span><span class="sxs-lookup"><span data-stu-id="c99e9-275">The Visual Studio IDE features built on the new C# and Visual Basic compilers frequently fetch syntax trees, and the compilers use async when doing so to keep Visual Studio responsive.</span></span> <span data-ttu-id="c99e9-276">Bir sözdizimi ağacı almak için, yazmanız gerekebilecek kodun ilk sürümü aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="c99e9-276">Here’s the first version of the code you might write to get a syntax tree:</span></span>  
  
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
  
 <span data-ttu-id="c99e9-277">Çağıran `GetSyntaxTreeAsync()` bir `Parser`örneği başlatır, kodu ayrıştırır ve `Task<SyntaxTree>`sonra bir <xref:System.Threading.Tasks.Task> nesnesi döndürür.</span><span class="sxs-lookup"><span data-stu-id="c99e9-277">You can see that calling `GetSyntaxTreeAsync()` instantiates a `Parser`, parses the code, and then returns a <xref:System.Threading.Tasks.Task> object, `Task<SyntaxTree>`.</span></span> <span data-ttu-id="c99e9-278">Pahalı parça `Parser` örneği ayırarak ve kodu ayrıştırır.</span><span class="sxs-lookup"><span data-stu-id="c99e9-278">The expensive part is allocating the `Parser` instance and parsing the code.</span></span> <span data-ttu-id="c99e9-279">Bu işlev, çağıranların ayrıştırma işini bekleme ve kullanıcı girişine yanıt vermek için UI iş parçacığını serbest verebilmeleri için bir <xref:System.Threading.Tasks.Task> döndürür.</span><span class="sxs-lookup"><span data-stu-id="c99e9-279">The function returns a <xref:System.Threading.Tasks.Task> so that callers can await the parsing work and free the UI thread to be responsive to user input.</span></span> 
  
 <span data-ttu-id="c99e9-280">Birçok Visual Studio özelliği aynı sözdizimi ağacını almayı deneyebilir, bu nedenle zaman ve ayırmaları kaydetmek için ayrıştırma sonucunu önbelleğe almak üzere aşağıdaki kodu yazabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c99e9-280">Several Visual Studio features might try to get the same syntax tree, so you might write the following code to cache the parsing result to save time and allocations.</span></span> <span data-ttu-id="c99e9-281">Ancak, bu kod bir ayırma doğurur:</span><span class="sxs-lookup"><span data-stu-id="c99e9-281">However, this code incurs an allocation:</span></span>  
  
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
  
 <span data-ttu-id="c99e9-282">Önbelleğe alma ile yeni kodun adlı `SyntaxTree` `cachedResult`bir alan olduğunu görürsünüz.</span><span class="sxs-lookup"><span data-stu-id="c99e9-282">You see that the new code with caching has a `SyntaxTree` field named `cachedResult`.</span></span> <span data-ttu-id="c99e9-283">Bu alan null olduğunda, `GetSyntaxTreeAsync()` işi yapar ve sonucu önbelleğe kaydeder.</span><span class="sxs-lookup"><span data-stu-id="c99e9-283">When this field is null, `GetSyntaxTreeAsync()` does the work and saves the result in the cache.</span></span> <span data-ttu-id="c99e9-284">`GetSyntaxTreeAsync()``SyntaxTree` nesneyi döndürür.</span><span class="sxs-lookup"><span data-stu-id="c99e9-284">`GetSyntaxTreeAsync()` returns the `SyntaxTree` object.</span></span> <span data-ttu-id="c99e9-285">`async` Bu sorun, türünde `Task<SyntaxTree>`bir işleviniz olduğunda ve türünde `SyntaxTree`bir değer döndürdüğünüzde, derleyicinin sonucu tutmak için bir görev ayırmak üzere kod yayar (kullanarak `Task<SyntaxTree>.FromResult()`).</span><span class="sxs-lookup"><span data-stu-id="c99e9-285">The problem is that when you have an `async` function of type `Task<SyntaxTree>`, and you return a value of type `SyntaxTree`, the compiler emits code to allocate a Task to hold the result (by using `Task<SyntaxTree>.FromResult()`).</span></span> <span data-ttu-id="c99e9-286">Görev tamamlandı olarak işaretlenir ve sonuç hemen kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="c99e9-286">The Task is marked as completed, and the result is immediately available.</span></span> <span data-ttu-id="c99e9-287">Yeni derleyicilerin kodunda, zaten tamamlanmış olan <xref:System.Threading.Tasks.Task> nesneler, bu ayırmaları düzeltme hızını önemli ölçüde düzeltmeye yönelik olarak oluşmuştur.</span><span class="sxs-lookup"><span data-stu-id="c99e9-287">In the code for the new compilers, <xref:System.Threading.Tasks.Task> objects that were already completed occurred so often that fixing these allocations improved responsiveness noticeably.</span></span> 
  
 <span data-ttu-id="c99e9-288">**Örnek 6**</span><span class="sxs-lookup"><span data-stu-id="c99e9-288">**Fix for example 6**</span></span>  
  
 <span data-ttu-id="c99e9-289">Tamamlanan <xref:System.Threading.Tasks.Task> ayırmayı kaldırmak için, görev nesnesini tamamlanan sonuçla önbelleğe alabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="c99e9-289">To remove the completed <xref:System.Threading.Tasks.Task> allocation, you can cache the Task object with the completed result:</span></span>  
  
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
  
 <span data-ttu-id="c99e9-290">Bu kod `cachedResult` , ' nin türünü olarak `Task<SyntaxTree>` değiştirir ve özgün kodu ' den `GetSyntaxTreeAsync()`tutan bir `async` yardımcı işlevi kullanır.</span><span class="sxs-lookup"><span data-stu-id="c99e9-290">This code changes the type of `cachedResult` to `Task<SyntaxTree>` and employs an `async` helper function that holds the original code from `GetSyntaxTreeAsync()`.</span></span> <span data-ttu-id="c99e9-291">`GetSyntaxTreeAsync()`Şimdi null [birleştirme işlecini](../../csharp/language-reference/operators/null-coalescing-operator.md) kullanarak null değilse döndürün `cachedResult` .</span><span class="sxs-lookup"><span data-stu-id="c99e9-291">`GetSyntaxTreeAsync()` now uses the [null coalescing operator](../../csharp/language-reference/operators/null-coalescing-operator.md) to return `cachedResult` if it isn't null.</span></span> <span data-ttu-id="c99e9-292">Null ise, sonuçları `GetSyntaxTreeUncachedAsync()`çağırırveönbelleğealır. `GetSyntaxTreeAsync()` `cachedResult`</span><span class="sxs-lookup"><span data-stu-id="c99e9-292">If `cachedResult` is null, then `GetSyntaxTreeAsync()` calls `GetSyntaxTreeUncachedAsync()` and caches the result.</span></span> <span data-ttu-id="c99e9-293">Genellikle kod olarak yapılan `GetSyntaxTreeUncachedAsync()` çağrıyı beklemez.`GetSyntaxTreeAsync()`</span><span class="sxs-lookup"><span data-stu-id="c99e9-293">Notice that `GetSyntaxTreeAsync()` doesn’t await the call to `GetSyntaxTreeUncachedAsync()` as the code would normally.</span></span> <span data-ttu-id="c99e9-294">Await `GetSyntaxTreeUncachedAsync()` kullanılması, <xref:System.Threading.Tasks.Task> nesnesinidöndürdüğünde`GetSyntaxTreeAsync()` , hemen öğesini döndüren anlamına gelir. <xref:System.Threading.Tasks.Task></span><span class="sxs-lookup"><span data-stu-id="c99e9-294">Not using await means that when `GetSyntaxTreeUncachedAsync()` returns its <xref:System.Threading.Tasks.Task> object, `GetSyntaxTreeAsync()` immediately returns the <xref:System.Threading.Tasks.Task>.</span></span> <span data-ttu-id="c99e9-295">Şimdi önbelleğe alınmış sonuç bir olduğundan, <xref:System.Threading.Tasks.Task>önbelleğe alınmış sonucu döndürecek bir ayırma yoktur.</span><span class="sxs-lookup"><span data-stu-id="c99e9-295">Now, the cached result is a <xref:System.Threading.Tasks.Task>, so there are no allocations to return the cached result.</span></span> 
  
### <a name="additional-considerations"></a><span data-ttu-id="c99e9-296">Ek hususlar</span><span class="sxs-lookup"><span data-stu-id="c99e9-296">Additional considerations</span></span>  
 <span data-ttu-id="c99e9-297">Büyük uygulamalarda veya çok sayıda veriyi işleyen uygulamalarda olası sorunlar hakkında daha fazla noktaya yer verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="c99e9-297">Here are a few more points about potential problems in large apps or apps that process a lot of data.</span></span> 
  
 <span data-ttu-id="c99e9-298">**Sözlüğü**</span><span class="sxs-lookup"><span data-stu-id="c99e9-298">**Dictionaries**</span></span>  
  
 <span data-ttu-id="c99e9-299">Sözlüklerde çok sayıda programda her ikisi de kullanılır, ancak sözlüklerde çok kullanışlı ve doğal olarak etkilidir.</span><span class="sxs-lookup"><span data-stu-id="c99e9-299">Dictionaries are used ubiquitously in many programs, and though dictionaries are very convenient and inherently efficient.</span></span> <span data-ttu-id="c99e9-300">Ancak, bunlar genellikle uygun şekilde kullanılır.</span><span class="sxs-lookup"><span data-stu-id="c99e9-300">However, they’re often used inappropriately.</span></span> <span data-ttu-id="c99e9-301">Visual Studio ve yeni derleyiciler ' de analiz, sözlüklerin çoğunun tek bir öğe içerdiğini veya boş olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="c99e9-301">In Visual Studio and the new compilers, analysis shows that many of the dictionaries contained a single element or were empty.</span></span> <span data-ttu-id="c99e9-302">Boş <xref:System.Collections.Generic.Dictionary%602> , on alana sahiptir ve bir x86 makinesindeki yığında 48 bayt kaplar.</span><span class="sxs-lookup"><span data-stu-id="c99e9-302">An empty <xref:System.Collections.Generic.Dictionary%602> has ten fields and occupies 48 bytes on the heap on an x86 machine.</span></span> <span data-ttu-id="c99e9-303">Sözlük, sabit zamanlı arama ile bir eşleme veya ilişkilendirilebilir veri yapısına ihtiyacınız olduğunda harika.</span><span class="sxs-lookup"><span data-stu-id="c99e9-303">Dictionaries are great when you need a mapping or associative data structure with constant-time lookup.</span></span> <span data-ttu-id="c99e9-304">Ancak yalnızca birkaç öğe varsa, bir sözlük kullanarak çok fazla alan duydum.</span><span class="sxs-lookup"><span data-stu-id="c99e9-304">However, when you have only a few elements, you waste a lot of space by using a dictionary.</span></span> <span data-ttu-id="c99e9-305">Bunun yerine, örneğin, hızlı bir şekilde ' a `List<KeyValuePair\<K,V>>`kadar hızla göz atabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c99e9-305">Instead, for example, you could iteratively look through a `List<KeyValuePair\<K,V>>`, just as fast.</span></span> <span data-ttu-id="c99e9-306">Bir sözlüğü yalnızca verileri kullanarak yüklemek ve bundan sonra (çok yaygın bir düzende) okumak için kullanırsanız, bir N (günlük (N)) arama ile sıralanmış bir diziyi kullanmak, kullanmakta olduğunuz öğelerin sayısına bağlı olarak neredeyse hızlı olabilir.</span><span class="sxs-lookup"><span data-stu-id="c99e9-306">If you use a dictionary only to load it with data and then read from it (a very common pattern), using a sorted array with an N(log(N)) lookup might be nearly as fast, depending on the number of elements you're using.</span></span> 
  
 <span data-ttu-id="c99e9-307">**Sınıflar ve yapılar**</span><span class="sxs-lookup"><span data-stu-id="c99e9-307">**Classes vs. structures**</span></span>  
  
 <span data-ttu-id="c99e9-308">Bir şekilde, sınıflar ve yapılar, uygulamalarınızı ayarlamak için klasik bir alan/saat zorunluluğunu getirir sağlar.</span><span class="sxs-lookup"><span data-stu-id="c99e9-308">In a way, classes and structures provide a classic space/time tradeoff for tuning your apps.</span></span> <span data-ttu-id="c99e9-309">Sınıflar bir x86 makinesinde alan olmasa bile 12 baytlık ek yük sağlar, ancak yalnızca bir sınıf örneğine başvurmak için bir işaretçi kullandığından, bunlara geçiş yapmak pahalı değildir.</span><span class="sxs-lookup"><span data-stu-id="c99e9-309">Classes incur 12 bytes of overhead on an x86 machine even if they have no fields, but they are inexpensive to pass around because it only takes a pointer to refer to a class instance.</span></span> <span data-ttu-id="c99e9-310">Yapılar, kutulamadıklarında yığın ayırmaları oluşturmaz, ancak büyük yapıları işlev bağımsız değişkenleri veya dönüş değerleri olarak geçirdiğinizde, yapıların tüm veri üyelerini otomatik olarak kopyalamak için CPU süresi sürer.</span><span class="sxs-lookup"><span data-stu-id="c99e9-310">Structures incur no heap allocations if they aren’t boxed, but when you pass large structures as function arguments or return values, it takes CPU time to atomically copy all the data members of the structures.</span></span> <span data-ttu-id="c99e9-311">Yapıları döndüren özelliklere yapılan yinelenen çağrılar için izleyin ve aşırı veri kopyalamayı önlemek için özelliğin değerini yerel bir değişkende önbelleğe koyun.</span><span class="sxs-lookup"><span data-stu-id="c99e9-311">Watch out for repeated calls to properties that return structures, and cache the property’s value in a local variable to avoid excessive data copying.</span></span> 
  
 <span data-ttu-id="c99e9-312">**Önbelleklerinde**</span><span class="sxs-lookup"><span data-stu-id="c99e9-312">**Caches**</span></span>  
  
 <span data-ttu-id="c99e9-313">Yaygın bir performans eli, sonuçları önbelleğe almak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="c99e9-313">A common performance trick is to cache results.</span></span> <span data-ttu-id="c99e9-314">Ancak, boyut Cap veya çıkarma ilkesi olmayan bir önbellek bellek sızıntısı olabilir.</span><span class="sxs-lookup"><span data-stu-id="c99e9-314">However, a cache without a size cap or disposal policy can be a memory leak.</span></span> <span data-ttu-id="c99e9-315">Büyük miktarlarda verileri işlerken önbellekler üzerinde çok fazla bellek tutarsanız, çöp toplamanın önbelleğe alınmış aramalarınızın avantajlarını geçersiz kılmasına neden olabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c99e9-315">When processing large amounts of data, if you hold on to a lot of memory in caches, you can cause garbage collection to override the benefits of your cached lookups.</span></span> 
  
 <span data-ttu-id="c99e9-316">Bu makalede, özellikle büyük miktarda veri işleyen büyük sistemler veya sistemler için uygulamanızın yanıt hızını etkileyebilecek performans sorunu belirtilerini nasıl anlamış olursunuz.</span><span class="sxs-lookup"><span data-stu-id="c99e9-316">In this article, we discussed how you should be aware of performance bottleneck symptoms that can affect your app's responsiveness, especially for large systems or systems that process a large amount of data.</span></span> <span data-ttu-id="c99e9-317">Ortak külekler kutulama, dize işlemeleri, LINQ ve lambda, zaman uyumsuz metotlarda önbelleğe alma, boyut sınırı veya aktiften çıkarma ilkesi olmadan önbelleğe alma, uygunsuz sözlüklerin kullanımı ve yapıların etrafında geçiş içerir.</span><span class="sxs-lookup"><span data-stu-id="c99e9-317">Common culprits include boxing, string manipulations, LINQ and lambda, caching in async methods, caching without a size limit or disposal policy, inappropriate use of dictionaries, and passing around structures.</span></span> <span data-ttu-id="c99e9-318">Uygulamalarınızı ayarlamaya yönelik dört olgu göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="c99e9-318">Keep in mind the four facts for tuning your apps:</span></span>  
  
- <span data-ttu-id="c99e9-319">, Sorunsuz bir şekilde iyileştirmeyin; sorunları belirlediğinizde uygulamanızı üretken yapın ve ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="c99e9-319">Don’t prematurely optimize – be productive and tune your app when you spot problems.</span></span> 
  
- <span data-ttu-id="c99e9-320">Profiller yok – ölçmeniz durumunda tahmin edersiniz.</span><span class="sxs-lookup"><span data-stu-id="c99e9-320">Profiles don’t lie – you’re guessing if you’re not measuring.</span></span> 
  
- <span data-ttu-id="c99e9-321">İyi araçlar, tüm farkları yapar – PerfView 'ı indirin ve deneyin.</span><span class="sxs-lookup"><span data-stu-id="c99e9-321">Good tools make all the difference – download PerfView and try it out.</span></span> 
  
- <span data-ttu-id="c99e9-322">Bu, her zaman, derleyici platformu ekibinin yeni derleyicilerin performansını en iyi şekilde harcadığı bir ayırdır.</span><span class="sxs-lookup"><span data-stu-id="c99e9-322">It's all about allocations – that is where the compiler platform team spent most of their time improving the performance of the new compilers.</span></span> 
  
## <a name="see-also"></a><span data-ttu-id="c99e9-323">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c99e9-323">See also</span></span>

- [<span data-ttu-id="c99e9-324">Bu konunun sunumunun videosu</span><span class="sxs-lookup"><span data-stu-id="c99e9-324">Video of presentation of this topic</span></span>](https://channel9.msdn.com/Events/TechEd/NorthAmerica/2013/DEV-B333)
- [<span data-ttu-id="c99e9-325">Performans Profili Oluşturma Başlangıç Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="c99e9-325">Beginners Guide to Performance Profiling</span></span>](/visualstudio/profiling/beginners-guide-to-performance-profiling)
- [<span data-ttu-id="c99e9-326">Performans</span><span class="sxs-lookup"><span data-stu-id="c99e9-326">Performance</span></span>](index.md)
- <span data-ttu-id="c99e9-327">[.NET performans Ipuçları](https://docs.microsoft.com/previous-versions/dotnet/articles/ms973839(v%3dmsdn.10))</span><span class="sxs-lookup"><span data-stu-id="c99e9-327">[.NET Performance Tips](https://docs.microsoft.com/previous-versions/dotnet/articles/ms973839(v%3dmsdn.10))</span></span>
- [<span data-ttu-id="c99e9-328">Channel 9 PerfView öğreticileri</span><span class="sxs-lookup"><span data-stu-id="c99e9-328">Channel 9 PerfView tutorials</span></span>](https://channel9.msdn.com/Series/PerfView-Tutorial)
- [<span data-ttu-id="c99e9-329">.NET Compiler Platform SDK 'Sı</span><span class="sxs-lookup"><span data-stu-id="c99e9-329">The .NET Compiler Platform SDK</span></span>](../../csharp/roslyn-sdk/index.md)
- [<span data-ttu-id="c99e9-330">GitHub 'da DotNet/Roslyn deposu</span><span class="sxs-lookup"><span data-stu-id="c99e9-330">dotnet/roslyn repo on GitHub</span></span>](https://github.com/dotnet/roslyn)
