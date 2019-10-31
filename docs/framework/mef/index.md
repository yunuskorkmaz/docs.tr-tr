---
title: Managed Extensibility Framework (MEF)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Managed Extensibility Framework, overview
- MEF, overview
ms.assetid: 6c61b4ec-c6df-4651-80f1-4854f8b14dde
ms.openlocfilehash: da73200513d451ee391fb6dd9c214a5b8ca771c6
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73126345"
---
# <a name="managed-extensibility-framework-mef"></a><span data-ttu-id="a022b-102">Managed Extensibility Framework (MEF)</span><span class="sxs-lookup"><span data-stu-id="a022b-102">Managed Extensibility Framework (MEF)</span></span>

<span data-ttu-id="a022b-103">Bu konu, .NET Framework 4 ' te tanıtılan Managed Extensibility Framework genel bir bakış sağlar.</span><span class="sxs-lookup"><span data-stu-id="a022b-103">This topic provides an overview of the Managed Extensibility Framework that was introduced in the .NET Framework 4.</span></span>

<a name="what_is_mef"></a>
## <a name="what-is-mef"></a><span data-ttu-id="a022b-104">MEF nedir?</span><span class="sxs-lookup"><span data-stu-id="a022b-104">What is MEF?</span></span>

<span data-ttu-id="a022b-105">Managed Extensibility Framework veya MEF, hafif, Genişletilebilir uygulamalar oluşturmaya yönelik bir kitaplıktır.</span><span class="sxs-lookup"><span data-stu-id="a022b-105">The Managed Extensibility Framework or MEF is a library for creating lightweight, extensible applications.</span></span> <span data-ttu-id="a022b-106">Uygulama geliştiricilerinin yapılandırma gerekmeden uzantıları bulmasına ve kullanmasına olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="a022b-106">It allows application developers to discover and use extensions with no configuration required.</span></span> <span data-ttu-id="a022b-107">Ayrıca, uzantı geliştiricilerinin kodu kolayca kapsüllemeyi ve kırarak sabit bağımlılıklara engel olmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="a022b-107">It also lets extension developers easily encapsulate code and avoid fragile hard dependencies.</span></span> <span data-ttu-id="a022b-108">MEF, uzantıların uygulamalar içinde yeniden kullanılmasına izin verir, ancak uygulamalar arasında da kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="a022b-108">MEF not only allows extensions to be reused within applications, but across applications as well.</span></span>

<a name="the_problem_of_extensibility"></a>
## <a name="the-problem-of-extensibility"></a><span data-ttu-id="a022b-109">Genişletilebilirlik sorunu</span><span class="sxs-lookup"><span data-stu-id="a022b-109">The Problem of Extensibility</span></span>
 <span data-ttu-id="a022b-110">Genişletilebilirlik için destek sağlaması gereken büyük bir uygulamanın mimarı olduğunu düşünün.</span><span class="sxs-lookup"><span data-stu-id="a022b-110">Imagine that you are the architect of a large application that must provide support for extensibility.</span></span> <span data-ttu-id="a022b-111">Uygulamanızın büyük olasılıkla çok sayıda küçük bileşen içermesi ve bunları oluşturup çalıştırmasından sorumlu olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="a022b-111">Your application has to include a potentially large number of smaller components, and is responsible for creating and running them.</span></span>

 <span data-ttu-id="a022b-112">Soruna en basit yaklaşım, bileşenleri uygulamanıza kaynak kodu olarak dahil etmek ve doğrudan kodunuzda çağırmak olur.</span><span class="sxs-lookup"><span data-stu-id="a022b-112">The simplest approach to the problem is to include the components as source code in your application, and call them directly from your code.</span></span> <span data-ttu-id="a022b-113">Bu bir dizi belirgin sakıncalar içerir.</span><span class="sxs-lookup"><span data-stu-id="a022b-113">This has a number of obvious drawbacks.</span></span> <span data-ttu-id="a022b-114">En önemlisi, kaynak kodu değiştirmeden yeni bileşenler, örneğin bir Web uygulaması gibi kabul edilebilir olabilecek bir kısıtlama, ancak bir istemci uygulamasında kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="a022b-114">Most importantly, you cannot add new components without modifying the source code, a restriction that might be acceptable in, for example, a Web application, but is unworkable in a client application.</span></span> <span data-ttu-id="a022b-115">Benzer şekilde sorunlu olarak, bileşenler için kaynak koda erişiminiz olmayabilir, çünkü bunlar üçüncü taraflar tarafından geliştirilip aynı nedenden dolayı sizinkilerle erişime izin vermezsiniz.</span><span class="sxs-lookup"><span data-stu-id="a022b-115">Equally problematic, you may not have access to the source code for the components, because they might be developed by third parties, and for the same reason you cannot allow them to access yours.</span></span>

 <span data-ttu-id="a022b-116">Daha karmaşık bir yaklaşım, uygulama ve bileşenleri arasında ayrılmasına izin vermek için bir uzantı noktası veya arabirim sağlamaktır.</span><span class="sxs-lookup"><span data-stu-id="a022b-116">A slightly more sophisticated approach would be to provide an extension point or interface, to permit decoupling between the application and its components.</span></span> <span data-ttu-id="a022b-117">Bu model altında, bir bileşenin uygulayabileceği bir arabirim ve uygulamanızla etkileşime geçmesini sağlamak için bir API sağlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a022b-117">Under this model, you might provide an interface that a component can implement, and an API to enable it to interact with your application.</span></span> <span data-ttu-id="a022b-118">Bu, kaynak kodu erişimi gerektirme sorununu çözer, ancak yine de kendi zorluklarıyla karşılaşmıştır.</span><span class="sxs-lookup"><span data-stu-id="a022b-118">This solves the problem of requiring source code access, but it still has its own difficulties.</span></span>

 <span data-ttu-id="a022b-119">Uygulamanın, bileşenleri bulmak için herhangi bir kapasitesi olmadığından, yine de hangi bileşenlerin kullanılabilir olduğunu ve yüklenmesi gerektiğini açıkça söylemelidir.</span><span class="sxs-lookup"><span data-stu-id="a022b-119">Because the application lacks any capacity for discovering components on its own, it must still be explicitly told which components are available and should be loaded.</span></span> <span data-ttu-id="a022b-120">Bu, genellikle bir yapılandırma dosyasına kullanılabilir bileşenleri açıkça kaydederek gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="a022b-120">This is typically accomplished by explicitly registering the available components in a configuration file.</span></span> <span data-ttu-id="a022b-121">Bu, bileşenlerin doğru olduğu anlamına gelir. Bu, özellikle son kullanıcı ise, güncellemeyi yapması beklenen geliştiriciden değil, bir bakım sorunu haline gelir.</span><span class="sxs-lookup"><span data-stu-id="a022b-121">This means that assuring that the components are correct becomes a maintenance issue, particularly if it is the end user and not the developer who is expected to do the updating.</span></span>

 <span data-ttu-id="a022b-122">Ayrıca, bileşenler, uygulamanın kendisinin rigidly tanımlı kanalları dışında birbiriyle iletişim kurabiliyor.</span><span class="sxs-lookup"><span data-stu-id="a022b-122">In addition, components are incapable of communicating with one another, except through the rigidly defined channels of the application itself.</span></span> <span data-ttu-id="a022b-123">Uygulama mimarı belirli bir iletişim gereksinimini tahmin etmez, genellikle olanaksızdır.</span><span class="sxs-lookup"><span data-stu-id="a022b-123">If the application architect has not anticipated the need for a particular communication, it is usually impossible.</span></span>

 <span data-ttu-id="a022b-124">Son olarak, bileşen geliştiricileri, uygulamadıkları arabirimi içeren derlemenin bir sabit bağımlılığını kabul etmelidir.</span><span class="sxs-lookup"><span data-stu-id="a022b-124">Finally, the component developers must accept a hard dependency on what assembly contains the interface they implement.</span></span> <span data-ttu-id="a022b-125">Bu, bir bileşenin birden fazla uygulamada kullanılmasını zorlaştırıyor ve bileşenler için bir test çerçevesi oluştururken da sorun oluşturabilir.</span><span class="sxs-lookup"><span data-stu-id="a022b-125">This makes it difficult for a component to be used in more than one application, and can also create problems when you create a test framework for components.</span></span>

<a name="what_mef_provides"></a>
## <a name="what-mef-provides"></a><span data-ttu-id="a022b-126">MEF 'in sağladığı</span><span class="sxs-lookup"><span data-stu-id="a022b-126">What MEF Provides</span></span>
 <span data-ttu-id="a022b-127">MEF, kullanılabilir bileşenlerin bu açık kaydı yerine, bunları *kompozisyon*aracılığıyla örtülü olarak keşfetmenin bir yolunu sağlar.</span><span class="sxs-lookup"><span data-stu-id="a022b-127">Instead of this explicit registration of available components, MEF provides a way to discover them implicitly, via *composition*.</span></span> <span data-ttu-id="a022b-128">*Bölüm*adı VERILEN bir MEF bileşeni, bildirimli olarak hem bağımlılıklarını ( *içeri aktarmalar*olarak bilinir) hem de kullanılabilir özellikleri ( *dışarı aktarma*olarak bilinir) belirler.</span><span class="sxs-lookup"><span data-stu-id="a022b-128">A MEF component, called a *part*, declaratively specifies both its dependencies (known as *imports*) and what capabilities (known as *exports*) it makes available.</span></span> <span data-ttu-id="a022b-129">Bir bölüm oluşturulduğunda, MEF bileşim altyapısı, diğer bölümlerden kullanılabilir olan içeri aktarmalarını karşılar.</span><span class="sxs-lookup"><span data-stu-id="a022b-129">When a part is created, the MEF composition engine satisfies its imports with what is available from other parts.</span></span>

 <span data-ttu-id="a022b-130">Bu yaklaşım, önceki bölümde ele alınan sorunları çözer.</span><span class="sxs-lookup"><span data-stu-id="a022b-130">This approach solves the problems discussed in the previous section.</span></span> <span data-ttu-id="a022b-131">MEF parçaları, yeteneklerini bildirimli olarak belirttiğinden, çalışma zamanında keşfedilir ve bu da bir uygulamanın sabit kodlanmış başvurular veya fragel yapılandırma dosyaları olmadan parçalar tarafından kullanılabilmesini sağlayabilir.</span><span class="sxs-lookup"><span data-stu-id="a022b-131">Because MEF parts declaratively specify their capabilities, they are discoverable at runtime, which means an application can make use of parts without either hard-coded references or fragile configuration files.</span></span> <span data-ttu-id="a022b-132">MEF, uygulamaların onları örneklemeden veya derlemeleri yüklemeden, meta verilerine göre parçalar bulmasına ve incelemesine olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="a022b-132">MEF allows applications to discover and examine parts by their metadata, without instantiating them or even loading their assemblies.</span></span> <span data-ttu-id="a022b-133">Sonuç olarak, uzantıların ne zaman ve nasıl yükleneceğini dikkatle belirtmeniz gerekmez.</span><span class="sxs-lookup"><span data-stu-id="a022b-133">As a result, there is no need to carefully specify when and how extensions should be loaded.</span></span>

 <span data-ttu-id="a022b-134">Bir bölüm, belirtilen dışarı aktarımlarının yanı sıra içeri aktarmaları belirtebilir ve diğer parçalar tarafından doldurulur.</span><span class="sxs-lookup"><span data-stu-id="a022b-134">In addition to its provided exports, a part can specify its imports, which will be filled by other parts.</span></span> <span data-ttu-id="a022b-135">Bu, parçalar arasında iletişimi yalnızca mümkün değildir ancak kolay bir kod düzenleme olanağı sağlar.</span><span class="sxs-lookup"><span data-stu-id="a022b-135">This makes communication among parts not only possible, but easy, and allows for good factoring of code.</span></span> <span data-ttu-id="a022b-136">Örneğin, birçok bileşen için ortak hizmetler ayrı bir bölüme ayrılabilir ve kolayca değiştirilebilir veya değiştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="a022b-136">For example, services common to many components can be factored into a separate part and easily modified or replaced.</span></span>

 <span data-ttu-id="a022b-137">MEF modeli belirli bir uygulama derlemesinde sabit bağımlılık gerektirmediğinden, uzantıların uygulamadan uygulamaya yeniden kullanılmasına izin verir.</span><span class="sxs-lookup"><span data-stu-id="a022b-137">Because the MEF model requires no hard dependency on a particular application assembly, it allows extensions to be reused from application to application.</span></span> <span data-ttu-id="a022b-138">Bu Ayrıca, uzantı bileşenlerini test etmek için uygulamadan bağımsız bir test bandı geliştirmeyi kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="a022b-138">This also makes it easy to develop a test harness, independent of the application, to test extension components.</span></span>

 <span data-ttu-id="a022b-139">MEF kullanılarak yazılan genişletilebilir bir uygulama, uzantı bileşenleriyle doldurulabilecek bir içeri aktarma bildirir ve uygulama hizmetlerini uzantılara sunmak için dışarı aktarmaları de bildirebilir.</span><span class="sxs-lookup"><span data-stu-id="a022b-139">An extensible application written by using MEF declares an import that can be filled by extension components, and may also declare exports in order to expose application services to extensions.</span></span> <span data-ttu-id="a022b-140">Her uzantı bileşeni bir dışarı aktarma bildirir ve içeri aktarmaları de bildirebilir.</span><span class="sxs-lookup"><span data-stu-id="a022b-140">Each extension component declares an export, and may also declare imports.</span></span> <span data-ttu-id="a022b-141">Bu şekilde, uzantı bileşenleri otomatik olarak genişletilebilir.</span><span class="sxs-lookup"><span data-stu-id="a022b-141">In this way, extension components themselves are automatically extensible.</span></span>

<a name="where_is_mef_available"></a>
## <a name="where-is-mef-available"></a><span data-ttu-id="a022b-142">MEF nerede kullanılabilir?</span><span class="sxs-lookup"><span data-stu-id="a022b-142">Where Is MEF Available?</span></span>
 <span data-ttu-id="a022b-143">MEF .NET Framework 4 ' ün ayrılmaz bir parçasıdır ve .NET Framework kullanıldığı her yerde kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="a022b-143">MEF is an integral part of the .NET Framework 4, and is available wherever the .NET Framework is used.</span></span> <span data-ttu-id="a022b-144">Windows Forms, WPF veya başka herhangi bir teknolojiyi kullanıp kullandıklarından veya ASP.NET kullanan sunucu uygulamalarında MEF 'i istemci uygulamalarınızda kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a022b-144">You can use MEF in your client applications, whether they use Windows Forms, WPF, or any other technology, or in server applications that use ASP.NET.</span></span>

<a name="mef_and_maf"></a>
## <a name="mef-and-maf"></a><span data-ttu-id="a022b-145">MEF ve MAF</span><span class="sxs-lookup"><span data-stu-id="a022b-145">MEF and MAF</span></span>
 <span data-ttu-id="a022b-146">.NET Framework önceki sürümleri, uygulamaların uzantıları yalıtmasına ve yönetmesine olanak tanımak için tasarlanan yönetilen eklenti çerçevesini (MAF) kullanıma sunmuştur.</span><span class="sxs-lookup"><span data-stu-id="a022b-146">Previous versions of the .NET Framework introduced the Managed Add-in Framework (MAF), designed to allow applications to isolate and manage extensions.</span></span> <span data-ttu-id="a022b-147">MAF 'nin odağı MEF 'ten biraz daha yüksek düzeydeyse, MEF 'in odağı keşfedilebilirlik, genişletilebilirlik ve taşınabilirlik üzerinde olduğunda, uzantı yalıtımı ve derleme yükleme ve kaldırma üzerinde yoğunlaşmaktadır.</span><span class="sxs-lookup"><span data-stu-id="a022b-147">The focus of MAF is slightly higher-level than MEF, concentrating on extension isolation and assembly loading and unloading, while MEF's focus is on discoverability, extensibility, and portability.</span></span> <span data-ttu-id="a022b-148">İki çerçeve sorunsuz bir şekilde çalışır ve tek bir uygulama her ikisinin de avantajlarından yararlanabilir.</span><span class="sxs-lookup"><span data-stu-id="a022b-148">The two frameworks interoperate smoothly, and a single application can take advantage of both.</span></span>

<a name="simplecalculator_an_example_application"></a>

## <a name="simplecalculator-an-example-application"></a><span data-ttu-id="a022b-149">SimpleCalculator: örnek bir uygulama</span><span class="sxs-lookup"><span data-stu-id="a022b-149">SimpleCalculator: An Example Application</span></span>

<span data-ttu-id="a022b-150">MEF 'in neler yapabileceğini görmenin en basit yolu basit bir MEF uygulaması derlemenize olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="a022b-150">The simplest way to see what MEF can do is to build a simple MEF application.</span></span> <span data-ttu-id="a022b-151">Bu örnekte, SimpleCalculator adlı çok basit bir Hesaplayıcı oluşturacaksınız.</span><span class="sxs-lookup"><span data-stu-id="a022b-151">In this example, you build a very simple calculator named SimpleCalculator.</span></span> <span data-ttu-id="a022b-152">SimpleCalculator 'ın amacı, "5 + 3" veya "6-2" biçimindeki temel aritmetik komutları kabul eden bir konsol uygulaması oluşturmaktır ve doğru yanıtları döndürür.</span><span class="sxs-lookup"><span data-stu-id="a022b-152">The goal of SimpleCalculator is to create a console application that accepts basic arithmetic commands, in the form "5+3" or "6-2", and returns the correct answers.</span></span> <span data-ttu-id="a022b-153">MEF kullanarak, uygulama kodunu değiştirmeden yeni işleçler ekleyebileceksiniz.</span><span class="sxs-lookup"><span data-stu-id="a022b-153">Using MEF, you'll be able to add new operators without changing the application code.</span></span>

<span data-ttu-id="a022b-154">Bu örneğe ilişkin tüm kodu indirmek için bkz. [SimpleCalculator örneği](https://code.msdn.microsoft.com/windowsdesktop/Simple-Calculator-MEF-1152654e).</span><span class="sxs-lookup"><span data-stu-id="a022b-154">To download the complete code for this example, see the [SimpleCalculator sample](https://code.msdn.microsoft.com/windowsdesktop/Simple-Calculator-MEF-1152654e).</span></span>

> [!NOTE]
> <span data-ttu-id="a022b-155">SimpleCalculator 'ın amacı, kullanımı için gerçekçi bir senaryo sağlamak yerine MEF 'in kavramlarını ve sözdizimini göstermektir.</span><span class="sxs-lookup"><span data-stu-id="a022b-155">The purpose of SimpleCalculator is to demonstrate the concepts and syntax of MEF, rather than to necessarily provide a realistic scenario for its use.</span></span> <span data-ttu-id="a022b-156">MEF 'in gücünden en fazla faydalanabilir uygulamalar SimpleCalculator 'dan daha karmaşıktır.</span><span class="sxs-lookup"><span data-stu-id="a022b-156">Many of the applications that would benefit most from the power of MEF are more complex than SimpleCalculator.</span></span> <span data-ttu-id="a022b-157">Daha kapsamlı örnekler için GitHub 'daki [Managed Extensibility Framework](https://github.com/MicrosoftArchive/mef) bakın.</span><span class="sxs-lookup"><span data-stu-id="a022b-157">For more extensive examples, see the [Managed Extensibility Framework](https://github.com/MicrosoftArchive/mef) on GitHub.</span></span>

- <span data-ttu-id="a022b-158">Başlamak için, Visual Studio 'da yeni bir konsol uygulaması projesi oluşturun ve `SimpleCalculator`adlandırın.</span><span class="sxs-lookup"><span data-stu-id="a022b-158">To start, in Visual Studio, create a new Console Application project and name it `SimpleCalculator`.</span></span>

- <span data-ttu-id="a022b-159">MEF 'in bulunduğu System. ComponentModel. Composition derlemesine bir başvuru ekleyin.</span><span class="sxs-lookup"><span data-stu-id="a022b-159">Add a reference to the System.ComponentModel.Composition assembly, where MEF resides.</span></span>

- <span data-ttu-id="a022b-160">Module1. vb veya Program.cs ' i açın ve System. ComponentModel. Composition ve System. ComponentModel. Composition. Hosting için `Imports` ya da `using` deyimlerini ekleyin.</span><span class="sxs-lookup"><span data-stu-id="a022b-160">Open Module1.vb or Program.cs and add `Imports` or `using` statements for System.ComponentModel.Composition and System.ComponentModel.Composition.Hosting.</span></span> <span data-ttu-id="a022b-161">Bu iki ad alanı, genişletilebilir bir uygulama geliştirmek için ihtiyacınız olan MEF türlerini içerir.</span><span class="sxs-lookup"><span data-stu-id="a022b-161">These two namespaces contain MEF types you will need to develop an extensible application.</span></span>

- <span data-ttu-id="a022b-162">Visual Basic kullanıyorsanız, `Module1` modülünü bildiren satıra `Public` anahtar sözcüğünü ekleyin.</span><span class="sxs-lookup"><span data-stu-id="a022b-162">If you're using Visual Basic, add the `Public` keyword to the line that declares the `Module1` module.</span></span>

<a name="composition_container_and_catalogs"></a>

## <a name="composition-container-and-catalogs"></a><span data-ttu-id="a022b-163">Birleşim kapsayıcısı ve kataloglar</span><span class="sxs-lookup"><span data-stu-id="a022b-163">Composition Container and Catalogs</span></span>

<span data-ttu-id="a022b-164">MEF bileşim modelinin çekirdeği, kullanılabilir tüm parçaları içeren ve kompozisyonu gerçekleştiren *bileşim kapsayıcısıdır*.</span><span class="sxs-lookup"><span data-stu-id="a022b-164">The core of the MEF composition model is the *composition container*, which contains all the parts available and performs composition.</span></span> <span data-ttu-id="a022b-165">Bileşim dışarı aktarmalar için içeri aktarmaların eşleştirmesinin eşleşmesine sahiptir.</span><span class="sxs-lookup"><span data-stu-id="a022b-165">Composition is the matching up of imports to exports.</span></span> <span data-ttu-id="a022b-166">Birleşim kapsayıcısının en yaygın türü <xref:System.ComponentModel.Composition.Hosting.CompositionContainer>ve bunu SimpleCalculator için kullanacaksınız.</span><span class="sxs-lookup"><span data-stu-id="a022b-166">The most common type of composition container is <xref:System.ComponentModel.Composition.Hosting.CompositionContainer>, and you'll use this for SimpleCalculator.</span></span>

<span data-ttu-id="a022b-167">Visual Basic kullanıyorsanız, Module1. vb dosyasında, `Program`adlı ortak bir sınıf ekleyin.</span><span class="sxs-lookup"><span data-stu-id="a022b-167">If you're using Visual Basic, in Module1.vb, add a public class named `Program`.</span></span>

<span data-ttu-id="a022b-168">Aşağıdaki satırı, Module1. vb veya Program.cs içindeki `Program` sınıfına ekleyin:</span><span class="sxs-lookup"><span data-stu-id="a022b-168">Add the following line to the `Program` class in Module1.vb or Program.cs:</span></span>

```vb
Dim _container As CompositionContainer
```

```csharp
private CompositionContainer _container;
```

<span data-ttu-id="a022b-169">Bu bölümde bulunan bölümleri saptamak için, bileşim kapsayıcıları bir *kataloğu*kullanır.</span><span class="sxs-lookup"><span data-stu-id="a022b-169">In order to discover the parts available to it, the composition containers makes use of a *catalog*.</span></span> <span data-ttu-id="a022b-170">Katalog, bazı kaynaklardan bulunan kullanılabilir bölümleri oluşturan bir nesnedir.</span><span class="sxs-lookup"><span data-stu-id="a022b-170">A catalog is an object that makes available parts discovered from some source.</span></span> <span data-ttu-id="a022b-171">MEF, sağlanan bir türden, bir derlemeden veya bir dizinden parçalar bulmaya yönelik kataloglar sağlar.</span><span class="sxs-lookup"><span data-stu-id="a022b-171">MEF provides catalogs to discover parts from a provided type, an assembly, or a directory.</span></span> <span data-ttu-id="a022b-172">Uygulama geliştiricileri, Web hizmeti gibi diğer kaynaklardan parçaları saptamak için kolayca yeni kataloglar oluşturabilir.</span><span class="sxs-lookup"><span data-stu-id="a022b-172">Application developers can easily create new catalogs to discover parts from other sources, such as a Web service.</span></span>

<span data-ttu-id="a022b-173">Aşağıdaki oluşturucuyu `Program` sınıfına ekleyin:</span><span class="sxs-lookup"><span data-stu-id="a022b-173">Add the following constructor to the `Program` class:</span></span>

```vb
Public Sub New()
    ' An aggregate catalog that combines multiple catalogs.
     Dim catalog = New AggregateCatalog()

    ' Adds all the parts found in the same assembly as the Program class.
    catalog.Catalogs.Add(New AssemblyCatalog(GetType(Program).Assembly))

    ' Create the CompositionContainer with the parts in the catalog.
    _container = New CompositionContainer(catalog)

    ' Fill the imports of this object.
    Try
        _container.ComposeParts(Me)
    Catch ex As CompositionException
        Console.WriteLine(ex.ToString)
    End Try
End Sub
```

```csharp
private Program()
{
    // An aggregate catalog that combines multiple catalogs.
    var catalog = new AggregateCatalog();
    // Adds all the parts found in the same assembly as the Program class.
    catalog.Catalogs.Add(new AssemblyCatalog(typeof(Program).Assembly));

    // Create the CompositionContainer with the parts in the catalog.
    _container = new CompositionContainer(catalog);

    // Fill the imports of this object.
    try
    {
        this._container.ComposeParts(this);
    }
    catch (CompositionException compositionException)
    {
        Console.WriteLine(compositionException.ToString());
   }
}
```

<span data-ttu-id="a022b-174"><xref:System.ComponentModel.Composition.AttributedModelServices.ComposeParts%2A> çağrısı, bileşim kapsayıcısına belirli bir parça kümesi oluşturmasını söyler. Bu durumda, `Program`geçerli örneğidir.</span><span class="sxs-lookup"><span data-stu-id="a022b-174">The call to <xref:System.ComponentModel.Composition.AttributedModelServices.ComposeParts%2A> tells the composition container to compose a specific set of parts, in this case the current instance of `Program`.</span></span> <span data-ttu-id="a022b-175">Ancak, `Program` doldurulacak içeri aktarmalar olmadığından hiçbir şey yapılmaz.</span><span class="sxs-lookup"><span data-stu-id="a022b-175">At this point, however, nothing will happen, since `Program` has no imports to fill.</span></span>

<a name="imports_and_exports_with_attributes"></a>
## <a name="imports-and-exports-with-attributes"></a><span data-ttu-id="a022b-176">Özniteliklerle içeri ve dışarı aktarmalar</span><span class="sxs-lookup"><span data-stu-id="a022b-176">Imports and Exports with Attributes</span></span>
 <span data-ttu-id="a022b-177">İlk olarak, bir Hesaplayıcı `Program` içeri aktarmalısınız.</span><span class="sxs-lookup"><span data-stu-id="a022b-177">First, you have `Program` import a calculator.</span></span> <span data-ttu-id="a022b-178">Bu, hesap makinesinin mantığındaki konsol giriş ve `Program`çıkış gibi kullanıcı arabirimi sorunlarının ayrılmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="a022b-178">This allows the separation of user interface concerns, such as the console input and output that will go into `Program`, from the logic of the calculator.</span></span>

 <span data-ttu-id="a022b-179">`Program` sınıfına aşağıdaki kodu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="a022b-179">Add the following code to the `Program` class:</span></span>

```vb
<Import(GetType(ICalculator))>
Public Property calculator As ICalculator
```

```csharp
[Import(typeof(ICalculator))]
public ICalculator calculator;
```

 <span data-ttu-id="a022b-180">`calculator` nesnesinin bildiriminin olağandışı olmadığına, ancak <xref:System.ComponentModel.Composition.ImportAttribute> özniteliğiyle tasarlandığına dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="a022b-180">Notice that the declaration of the `calculator` object is not unusual, but that it is decorated with the <xref:System.ComponentModel.Composition.ImportAttribute> attribute.</span></span> <span data-ttu-id="a022b-181">Bu öznitelik bir içeri aktarma işlemi olduğunu bildirir; diğer bir deyişle, nesne oluşturulduğunda bileşim motoru tarafından doldurulur.</span><span class="sxs-lookup"><span data-stu-id="a022b-181">This attribute declares something to be an import; that is, it will be filled by the composition engine when the object is composed.</span></span>

 <span data-ttu-id="a022b-182">Her içeri aktarma işlemi bir *sözleşmeye*sahiptir ve bu, ile eşleştirileceği dışarı aktarmaları belirler.</span><span class="sxs-lookup"><span data-stu-id="a022b-182">Every import has a *contract*, which determines what exports it will be matched with.</span></span> <span data-ttu-id="a022b-183">Sözleşme açıkça belirtilen bir dize olabilir veya belirli bir türden MEF tarafından otomatik olarak oluşturulabilir, bu durumda arabirim `ICalculator`.</span><span class="sxs-lookup"><span data-stu-id="a022b-183">The contract can be an explicitly specified string, or it can be automatically generated by MEF from a given type, in this case the interface `ICalculator`.</span></span> <span data-ttu-id="a022b-184">Eşleşen bir sözleşmeyle belirtilen tüm dışarı aktarma işlemi bu içeri aktarmayı karşılar.</span><span class="sxs-lookup"><span data-stu-id="a022b-184">Any export declared with a matching contract will fulfill this import.</span></span> <span data-ttu-id="a022b-185">`calculator` nesnenin türü aslında `ICalculator`olduğunda, bu gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="a022b-185">Note that while the type of the `calculator` object is in fact `ICalculator`, this is not required.</span></span> <span data-ttu-id="a022b-186">Sözleşme, içeri aktarma nesnesinin türünden bağımsızdır.</span><span class="sxs-lookup"><span data-stu-id="a022b-186">The contract is independent from the type of the importing object.</span></span> <span data-ttu-id="a022b-187">(Bu durumda, `typeof(ICalculator)`bırakabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a022b-187">(In this case, you could leave out the `typeof(ICalculator)`.</span></span> <span data-ttu-id="a022b-188">MEF, açıkça belirtmediğiniz takdirde, sözleşmenin içeri aktarma türüne göre otomatik olarak kabul edilir.)</span><span class="sxs-lookup"><span data-stu-id="a022b-188">MEF will automatically assume the contract to be based on the type of the import unless you specify it explicitly.)</span></span>

 <span data-ttu-id="a022b-189">Bu çok basit arabirimi modüle veya `SimpleCalculator` ad alanına ekleyin:</span><span class="sxs-lookup"><span data-stu-id="a022b-189">Add this very simple interface to the module or `SimpleCalculator` namespace:</span></span>

```vb
Public Interface ICalculator
    Function Calculate(ByVal input As String) As String
End Interface
```

```csharp
public interface ICalculator
{
    String Calculate(String input);
}
```

 <span data-ttu-id="a022b-190">`ICalculator`tanımladığınıza göre, bunu uygulayan bir sınıfa ihtiyacınız vardır.</span><span class="sxs-lookup"><span data-stu-id="a022b-190">Now that you have defined `ICalculator`, you need a class that implements it.</span></span> <span data-ttu-id="a022b-191">Aşağıdaki sınıfı modüle veya `SimpleCalculator` ad alanına ekleyin:</span><span class="sxs-lookup"><span data-stu-id="a022b-191">Add the following class to the module or `SimpleCalculator` namespace:</span></span>

```vb
<Export(GetType(ICalculator))>
Public Class MySimpleCalculator
   Implements ICalculator

End Class
```

```csharp
[Export(typeof(ICalculator))]
class MySimpleCalculator : ICalculator
{

}
```

 <span data-ttu-id="a022b-192">`Program`içeri aktarma ile eşleşecek dışarı aktarma aşağıda verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="a022b-192">Here is the export that will match the import in `Program`.</span></span> <span data-ttu-id="a022b-193">Dışarı aktarmanın içeri aktarma ile eşleşmesi için, dışarı aktarmanın aynı sözleşmeye sahip olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="a022b-193">In order for the export to match the import, the export must have the same contract.</span></span> <span data-ttu-id="a022b-194">`typeof(MySimpleCalculator)` dayalı bir sözleşme altında dışarı aktarmak bir uyumsuzluk üretebilir ve içeri aktarma doldurulmaz; sözleşmenin tam olarak eşleşmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="a022b-194">Exporting under a contract based on `typeof(MySimpleCalculator)` would produce a mismatch, and the import would not be filled; the contract needs to match exactly.</span></span>

 <span data-ttu-id="a022b-195">Bileşim kapsayıcısı Bu derlemede bulunan tüm bölümlerle doldurulduğundan, `MySimpleCalculator` bölümü kullanılabilir olacaktır.</span><span class="sxs-lookup"><span data-stu-id="a022b-195">Since the composition container will be populated with all the parts available in this assembly, the `MySimpleCalculator` part will be available.</span></span> <span data-ttu-id="a022b-196">`Program` için Oluşturucu `Program` nesnesi üzerinde kompozisyon gerçekleştirdiğinde, içeri aktarma işlemi bu amaçla oluşturulacak bir `MySimpleCalculator` nesnesi ile doldurulur.</span><span class="sxs-lookup"><span data-stu-id="a022b-196">When the constructor for `Program` performs composition on the `Program` object, its import will be filled with a `MySimpleCalculator` object, which will be created for that purpose.</span></span>

 <span data-ttu-id="a022b-197">Kullanıcı arabirimi katmanının (`Program`) başka herhangi bir şeyi bilmeleri gerekmez.</span><span class="sxs-lookup"><span data-stu-id="a022b-197">The user interface layer (`Program`) does not need to know anything else.</span></span> <span data-ttu-id="a022b-198">Bu nedenle, `Main` yönteminde Kullanıcı arabirimi mantığının geri kalanını doldurabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a022b-198">You can therefore fill in the rest of the user interface logic in the `Main` method.</span></span>

 <span data-ttu-id="a022b-199">`Main` yöntemine aşağıdaki kodu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="a022b-199">Add the following code to the `Main` method:</span></span>

```vb
Sub Main()
    ' Composition is performed in the constructor.
    Dim p As New Program()
    Dim s As String
    Console.WriteLine("Enter Command:")
    While (True)
        s = Console.ReadLine()
        Console.WriteLine(p.calculator.Calculate(s))
    End While
End Sub
```

```csharp
static void Main(string[] args)
{
    // Composition is performed in the constructor.
    var p = new Program();
    String s;
    Console.WriteLine("Enter Command:");
    while (true)
    {
        s = Console.ReadLine();
        Console.WriteLine(p.calculator.Calculate(s));
    }
}
```

 <span data-ttu-id="a022b-200">Bu kod, bir giriş satırını okur ve sonuç üzerinde `ICalculator` `Calculate` işlevini çağırarak konsola geri yazar.</span><span class="sxs-lookup"><span data-stu-id="a022b-200">This code simply reads a line of input and calls the `Calculate` function of `ICalculator` on the result, which it writes back to the console.</span></span> <span data-ttu-id="a022b-201">`Program`için ihtiyacınız olan tüm kod vardır.</span><span class="sxs-lookup"><span data-stu-id="a022b-201">That is all the code you need in `Program`.</span></span> <span data-ttu-id="a022b-202">Çalışmanın tüm geri kalanı parçalar halinde olur.</span><span class="sxs-lookup"><span data-stu-id="a022b-202">All the rest of the work will happen in the parts.</span></span>

<a name="further_imports_and_importmany"></a>
## <a name="further-imports-and-importmany"></a><span data-ttu-id="a022b-203">Daha fazla Içeri aktarmalar ve ImportMany</span><span class="sxs-lookup"><span data-stu-id="a022b-203">Further Imports and ImportMany</span></span>
 <span data-ttu-id="a022b-204">SimpleCalculator 'ın Genişletilebilir olması için, işlem listesini içeri aktarması gerekir.</span><span class="sxs-lookup"><span data-stu-id="a022b-204">In order for SimpleCalculator to be extensible, it needs to import a list of operations.</span></span> <span data-ttu-id="a022b-205">Sıradan bir <xref:System.ComponentModel.Composition.ImportAttribute> özniteliği bir ve yalnızca bir <xref:System.ComponentModel.Composition.ExportAttribute>doldurulur.</span><span class="sxs-lookup"><span data-stu-id="a022b-205">An ordinary <xref:System.ComponentModel.Composition.ImportAttribute> attribute is filled by one and only one <xref:System.ComponentModel.Composition.ExportAttribute>.</span></span> <span data-ttu-id="a022b-206">Birden fazla kullanılabilir varsa, bileşim altyapısı bir hata üretir.</span><span class="sxs-lookup"><span data-stu-id="a022b-206">If more than one is available, the composition engine produces an error.</span></span> <span data-ttu-id="a022b-207">Herhangi bir sayıda dışarı aktarmalar tarafından doldurulabilecek bir içeri aktarma oluşturmak için <xref:System.ComponentModel.Composition.ImportManyAttribute> özniteliğini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a022b-207">To create an import that can be filled by any number of exports, you can use the <xref:System.ComponentModel.Composition.ImportManyAttribute> attribute.</span></span>

 <span data-ttu-id="a022b-208">Aşağıdaki Operations özelliğini `MySimpleCalculator` sınıfına ekleyin:</span><span class="sxs-lookup"><span data-stu-id="a022b-208">Add the following operations property to the `MySimpleCalculator` class:</span></span>

```vb
<ImportMany()>
Public Property operations As IEnumerable(Of Lazy(Of IOperation, IOperationData))
```

```csharp
[ImportMany]
IEnumerable<Lazy<IOperation, IOperationData>> operations;
```

 <span data-ttu-id="a022b-209"><xref:System.Lazy%602>, MEF tarafından dışarı aktarmalar için dolaylı başvuruları tutmak üzere sunulan bir türdür.</span><span class="sxs-lookup"><span data-stu-id="a022b-209"><xref:System.Lazy%602> is a type provided by MEF to hold indirect references to exports.</span></span> <span data-ttu-id="a022b-210">Burada dışa aktarılmış nesnenin kendisinin yanı sıra dışarı *aktarma meta verilerini*veya dışarı aktarılmış nesneyi açıklayan bilgileri de alırsınız.</span><span class="sxs-lookup"><span data-stu-id="a022b-210">Here, in addition to the exported object itself, you also get *export metadata*, or information that describes the exported object.</span></span> <span data-ttu-id="a022b-211">Her <xref:System.Lazy%602>, gerçek bir işlemi temsil eden bir `IOperation` nesnesi ve meta verilerini temsil eden bir `IOperationData` nesnesi içerir.</span><span class="sxs-lookup"><span data-stu-id="a022b-211">Each <xref:System.Lazy%602> contains an `IOperation` object, representing an actual operation, and an `IOperationData` object, representing its metadata.</span></span>

 <span data-ttu-id="a022b-212">Aşağıdaki basit arabirimleri modüle veya `SimpleCalculator` ad alanına ekleyin:</span><span class="sxs-lookup"><span data-stu-id="a022b-212">Add the following simple interfaces to the module or `SimpleCalculator` namespace:</span></span>

```vb
Public Interface IOperation
    Function Operate(ByVal left As Integer, ByVal right As Integer) As Integer
End Interface

Public Interface IOperationData
    ReadOnly Property Symbol As Char
End Interface
```

```csharp
public interface IOperation
{
     int Operate(int left, int right);
}

public interface IOperationData
{
    Char Symbol { get; }
}
```

 <span data-ttu-id="a022b-213">Bu durumda, her bir işlemin meta verileri +,-, \* gibi bir işlemi temsil eden simgedir.</span><span class="sxs-lookup"><span data-stu-id="a022b-213">In this case, the metadata for each operation is the symbol that represents that operation, such as +, -, \*, and so on.</span></span> <span data-ttu-id="a022b-214">Toplama işlemini kullanılabilir hale getirmek için, aşağıdaki sınıfı modüle veya `SimpleCalculator` ad alanına ekleyin:</span><span class="sxs-lookup"><span data-stu-id="a022b-214">To make the addition operation available, add the following class to the module or `SimpleCalculator` namespace:</span></span>

```vb
<Export(GetType(IOperation))>
<ExportMetadata("Symbol", "+"c)>
Public Class Add
    Implements IOperation

    Public Function Operate(ByVal left As Integer, ByVal right As Integer) As Integer Implements IOperation.Operate
        Return left + right
    End Function
End Class
```

```csharp
[Export(typeof(IOperation))]
[ExportMetadata("Symbol", '+')]
class Add: IOperation
{
    public int Operate(int left, int right)
    {
        return left + right;
    }
}
```

 <span data-ttu-id="a022b-215"><xref:System.ComponentModel.Composition.ExportAttribute> özniteliği daha önce olduğu gibi çalışır.</span><span class="sxs-lookup"><span data-stu-id="a022b-215">The <xref:System.ComponentModel.Composition.ExportAttribute> attribute functions as it did before.</span></span> <span data-ttu-id="a022b-216"><xref:System.ComponentModel.Composition.ExportMetadataAttribute> özniteliği, meta verileri bir ad-değer çifti biçiminde bu dışarı aktarmaya iliştirir.</span><span class="sxs-lookup"><span data-stu-id="a022b-216">The <xref:System.ComponentModel.Composition.ExportMetadataAttribute> attribute attaches metadata, in the form of a name-value pair, to that export.</span></span> <span data-ttu-id="a022b-217">`Add` sınıfı `IOperation`uyguladığından `IOperationData` uygulayan bir sınıf açıkça tanımlanmamıştır.</span><span class="sxs-lookup"><span data-stu-id="a022b-217">While the `Add` class implements `IOperation`, a class that implements `IOperationData` is not explicitly defined.</span></span> <span data-ttu-id="a022b-218">Bunun yerine, bir sınıf, belirtilen meta verilerin adlarına göre özellikler ile MEF tarafından örtülü olarak oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="a022b-218">Instead, a class is implicitly created by MEF with properties based on the names of the metadata provided.</span></span> <span data-ttu-id="a022b-219">(Bu, MEF 'teki meta verilere erişmenin çeşitli yöntemlerinden biridir.)</span><span class="sxs-lookup"><span data-stu-id="a022b-219">(This is one of several ways to access metadata in MEF.)</span></span>

 <span data-ttu-id="a022b-220">MEF 'te birleşim *özyinelemeli*.</span><span class="sxs-lookup"><span data-stu-id="a022b-220">Composition in MEF is *recursive*.</span></span> <span data-ttu-id="a022b-221">`MySimpleCalculator`türünde olması için bir `ICalculator` içeri aktarılan `Program` nesnesini açıkça oluşturursunuz.</span><span class="sxs-lookup"><span data-stu-id="a022b-221">You explicitly composed the `Program` object, which imported an `ICalculator` that turned out to be of type `MySimpleCalculator`.</span></span> <span data-ttu-id="a022b-222">`MySimpleCalculator`, `IOperation` nesnelerinin bir koleksiyonunu içeri aktarır ve `MySimpleCalculator` oluşturulduğunda, `Program`içeri aktarmaları ile aynı anda bu içeri aktarma doldurulur.</span><span class="sxs-lookup"><span data-stu-id="a022b-222">`MySimpleCalculator`, in turn, imports a collection of `IOperation` objects, and that import will be filled when `MySimpleCalculator` is created, at the same time as the imports of `Program`.</span></span> <span data-ttu-id="a022b-223">`Add` sınıfı daha fazla içeri aktarma bildirmişse, bunun da doldurulması gerekir.</span><span class="sxs-lookup"><span data-stu-id="a022b-223">If the `Add` class declared a further import, that too would have to be filled, and so on.</span></span> <span data-ttu-id="a022b-224">Doldurulmamış herhangi bir içeri aktarma işlemi bir bileşim hatası ile sonuçlanır.</span><span class="sxs-lookup"><span data-stu-id="a022b-224">Any import left unfilled results in a composition error.</span></span> <span data-ttu-id="a022b-225">(Ancak, içeri aktarmaları isteğe bağlı olarak bildirmek veya varsayılan değerleri atamak mümkündür.)</span><span class="sxs-lookup"><span data-stu-id="a022b-225">(It is possible, however, to declare imports to be optional or to assign them default values.)</span></span>

<a name="calculator_logic"></a>
## <a name="calculator-logic"></a><span data-ttu-id="a022b-226">Hesaplayıcı mantığı</span><span class="sxs-lookup"><span data-stu-id="a022b-226">Calculator Logic</span></span>
 <span data-ttu-id="a022b-227">Bu parçalar yerinde olduğunda, her şey Hesaplayıcı mantığının kendisidir.</span><span class="sxs-lookup"><span data-stu-id="a022b-227">With these parts in place, all that remains is the calculator logic itself.</span></span> <span data-ttu-id="a022b-228">`Calculate` yöntemini uygulamak için `MySimpleCalculator` sınıfına aşağıdaki kodu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="a022b-228">Add the following code in the `MySimpleCalculator` class to implement the `Calculate` method:</span></span>

```vb
Public Function Calculate(ByVal input As String) As String Implements ICalculator.Calculate
    Dim left, right As Integer
    Dim operation As Char
    ' Finds the operator.
    Dim fn = FindFirstNonDigit(input)
    If fn < 0 Then
        Return "Could not parse command."
    End If
    operation = input(fn)
    Try
        ' Separate out the operands.
        left = Integer.Parse(input.Substring(0, fn))
        right = Integer.Parse(input.Substring(fn + 1))
    Catch ex As Exception
        Return "Could not parse command."
    End Try
    For Each i As Lazy(Of IOperation, IOperationData) In operations
        If i.Metadata.symbol = operation Then
            Return i.Value.Operate(left, right).ToString()
        End If
    Next
    Return "Operation not found!"
End Function
```

```csharp
public String Calculate(String input)
{
    int left;
    int right;
    char operation;
    // Finds the operator.
    int fn = FindFirstNonDigit(input); 
    if (fn < 0) return "Could not parse command.";

    try
    {
        // Separate out the operands.
        left = int.Parse(input.Substring(0, fn));
        right = int.Parse(input.Substring(fn + 1));
    }
    catch
    {
        return "Could not parse command.";
    }

    operation = input[fn];

    foreach (Lazy<IOperation, IOperationData> i in operations)
    {
        if (i.Metadata.Symbol.Equals(operation)) return i.Value.Operate(left, right).ToString();
    }
    return "Operation Not Found!";
}
```

 <span data-ttu-id="a022b-229">İlk adımlar, giriş dizesini sol ve sağ işlenenler ve bir işleç karakteri olarak ayrıştırır.</span><span class="sxs-lookup"><span data-stu-id="a022b-229">The initial steps parse the input string into left and right operands and an operator character.</span></span> <span data-ttu-id="a022b-230">`foreach` döngüsünde, `operations` koleksiyonun her üyesi incelenir.</span><span class="sxs-lookup"><span data-stu-id="a022b-230">In the `foreach` loop, every member of the `operations` collection is examined.</span></span> <span data-ttu-id="a022b-231">Bu nesneler <xref:System.Lazy%602>türündedir ve meta veri değerlerine ve aktarılmış nesnesine sırasıyla <xref:System.Lazy%602.Metadata%2A> özelliği ve <xref:System.Lazy%601.Value%2A> özelliği ile erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="a022b-231">These objects are of type <xref:System.Lazy%602>, and their metadata values and exported object can be accessed with the <xref:System.Lazy%602.Metadata%2A> property and the <xref:System.Lazy%601.Value%2A> property respectively.</span></span> <span data-ttu-id="a022b-232">Bu durumda, `IOperationData` nesnesinin `Symbol` özelliği bir eşleşme olarak bulunursa, hesaplayıcı `IOperation` nesnesinin `Operate` yöntemini çağırır ve sonucu döndürür.</span><span class="sxs-lookup"><span data-stu-id="a022b-232">In this case, if the `Symbol` property of the `IOperationData` object is discovered to be a match, the calculator calls the `Operate` method of the `IOperation` object and returns the result.</span></span>

 <span data-ttu-id="a022b-233">Hesaplayıcıyı tamamlayabilmeniz için bir dizedeki ilk basamak olmayan karakterin konumunu döndüren bir yardımcı yöntemi de gereklidir.</span><span class="sxs-lookup"><span data-stu-id="a022b-233">To complete the calculator, you also need a helper method that returns the position of the first non-digit character in a string.</span></span> <span data-ttu-id="a022b-234">Aşağıdaki yardımcı yöntemi `MySimpleCalculator` sınıfına ekleyin:</span><span class="sxs-lookup"><span data-stu-id="a022b-234">Add the following helper method to the `MySimpleCalculator` class:</span></span>

```vb
Private Function FindFirstNonDigit(ByVal s As String) As Integer
    For i = 0 To s.Length - 1
        If (Not (Char.IsDigit(s(i)))) Then Return i
    Next
    Return -1
End Function
```

```csharp
private int FindFirstNonDigit(string s)
{
    for (int i = 0; i < s.Length; i++)
    {
        if (!(Char.IsDigit(s[i]))) return i;
    }
    return -1;
}
```

 <span data-ttu-id="a022b-235">Artık projeyi derleyip çalıştırabilmelisiniz.</span><span class="sxs-lookup"><span data-stu-id="a022b-235">You should now be able to compile and run the project.</span></span> <span data-ttu-id="a022b-236">Visual Basic, `Module1`için `Public` anahtar sözcüğünü eklediğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="a022b-236">In Visual Basic, make sure that you added the `Public` keyword to `Module1`.</span></span> <span data-ttu-id="a022b-237">Konsol penceresinde, "5 + 3" gibi bir ek işlem yazın ve Hesaplayıcı sonuçları döndürür.</span><span class="sxs-lookup"><span data-stu-id="a022b-237">In the console window, type an addition operation, such as "5+3", and the calculator returns the results.</span></span> <span data-ttu-id="a022b-238">"Işlem bulunamadı!" ile ilgili başka bir operatör oluşur</span><span class="sxs-lookup"><span data-stu-id="a022b-238">Any other operator results in the "Operation Not Found!"</span></span> <span data-ttu-id="a022b-239">İleti.</span><span class="sxs-lookup"><span data-stu-id="a022b-239">message.</span></span>

<a name="extending_simplecalculator_using_a_new_class"></a>
## <a name="extending-simplecalculator-using-a-new-class"></a><span data-ttu-id="a022b-240">Yeni bir sınıf kullanarak SimpleCalculator 'ı genişletme</span><span class="sxs-lookup"><span data-stu-id="a022b-240">Extending SimpleCalculator Using A New Class</span></span>
 <span data-ttu-id="a022b-241">Hesap Makinası artık işe yarar, yeni bir işlem eklemek kolaydır.</span><span class="sxs-lookup"><span data-stu-id="a022b-241">Now that the calculator works, adding a new operation is easy.</span></span> <span data-ttu-id="a022b-242">Aşağıdaki sınıfı modüle veya `SimpleCalculator` ad alanına ekleyin:</span><span class="sxs-lookup"><span data-stu-id="a022b-242">Add the following class to the module or `SimpleCalculator` namespace:</span></span>

```vb
<Export(GetType(IOperation))>
<ExportMetadata("Symbol", "-"c)>
Public Class Subtract
    Implements IOperation

    Public Function Operate(ByVal left As Integer, ByVal right As Integer) As Integer Implements IOperation.Operate
        Return left - right
    End Function
End Class
```

```csharp
[Export(typeof(IOperation))]
[ExportMetadata("Symbol", '-')]
class Subtract : IOperation
{
    public int Operate(int left, int right)
    {
        return left - right;
    }
}
```

 <span data-ttu-id="a022b-243">Projeyi derleyin ve çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="a022b-243">Compile and run the project.</span></span> <span data-ttu-id="a022b-244">"5-3" gibi bir çıkarma işlemi yazın.</span><span class="sxs-lookup"><span data-stu-id="a022b-244">Type a subtraction operation, such as "5-3".</span></span> <span data-ttu-id="a022b-245">Hesaplayıcı artık çıkarma ve ekleme de desteklemektedir.</span><span class="sxs-lookup"><span data-stu-id="a022b-245">The calculator now supports subtraction as well as addition.</span></span>

<a name="extending_simplecalculator_using_a_new_assembly"></a>
## <a name="extending-simplecalculator-using-a-new-assembly"></a><span data-ttu-id="a022b-246">Yeni bir derleme kullanarak SimpleCalculator 'ı genişletme</span><span class="sxs-lookup"><span data-stu-id="a022b-246">Extending SimpleCalculator Using A New Assembly</span></span>
 <span data-ttu-id="a022b-247">Kaynak koda sınıflar eklemek yeterince basittir, ancak MEF, bir uygulamanın parçalar için kendi kaynağını göz atabilme olanağı sağlar.</span><span class="sxs-lookup"><span data-stu-id="a022b-247">Adding classes to the source code is simple enough, but MEF provides the ability to look outside an application’s own source for parts.</span></span> <span data-ttu-id="a022b-248">Bunu göstermek için, bir <xref:System.ComponentModel.Composition.Hosting.DirectoryCatalog>ekleyerek SimpleCalculator 'ı bir dizini ve kendi derlemesini aramak için de değiştirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="a022b-248">To demonstrate this, you will need to modify SimpleCalculator to search a directory, as well as its own assembly, for parts, by adding a <xref:System.ComponentModel.Composition.Hosting.DirectoryCatalog>.</span></span>

 <span data-ttu-id="a022b-249">SimpleCalculator projesine `Extensions` adlı yeni bir dizin ekleyin.</span><span class="sxs-lookup"><span data-stu-id="a022b-249">Add a new directory named `Extensions` to the SimpleCalculator project.</span></span> <span data-ttu-id="a022b-250">Çözüm düzeyinde değil, proje düzeyine eklediğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="a022b-250">Make sure to add it at the project level, and not at the solution level.</span></span> <span data-ttu-id="a022b-251">Ardından `ExtendedOperations`adlı çözüme yeni bir sınıf kitaplığı projesi ekleyin.</span><span class="sxs-lookup"><span data-stu-id="a022b-251">Then add a new Class Library project to the solution, named `ExtendedOperations`.</span></span> <span data-ttu-id="a022b-252">Yeni proje ayrı bir derlemede derlenir.</span><span class="sxs-lookup"><span data-stu-id="a022b-252">The new project will compile into a separate assembly.</span></span>

 <span data-ttu-id="a022b-253">ExtendedOperations projesi için proje özellikleri tasarımcısını açın ve **Derle** veya **Derle** sekmesine tıklayın. **derleme çıkış yolunu** veya **Çıkış yolunu** , SimpleCalculator projesindeki Extensions dizinini işaret etmek üzere değiştirin Dizin (.. \Simplehesaplator\extensions\\).</span><span class="sxs-lookup"><span data-stu-id="a022b-253">Open the Project Properties Designer for the ExtendedOperations project and click the **Compile** or **Build** tab. Change the **Build output path** or **Output path** to point to the Extensions directory in the SimpleCalculator project directory (..\SimpleCalculator\Extensions\\).</span></span>

 <span data-ttu-id="a022b-254">Module1. vb veya Program.cs içinde `Program` oluşturucusuna aşağıdaki satırı ekleyin:</span><span class="sxs-lookup"><span data-stu-id="a022b-254">In Module1.vb or Program.cs, add the following line to the `Program` constructor:</span></span>

```vb
catalog.Catalogs.Add(New DirectoryCatalog("C:\SimpleCalculator\SimpleCalculator\Extensions"))
```

```csharp
catalog.Catalogs.Add(new DirectoryCatalog("C:\\SimpleCalculator\\SimpleCalculator\\Extensions"));
```

 <span data-ttu-id="a022b-255">Örnek yolu, uzantılar dizininizin yolunu ile değiştirin.</span><span class="sxs-lookup"><span data-stu-id="a022b-255">Replace the example path with the path to your Extensions directory.</span></span> <span data-ttu-id="a022b-256">(Bu mutlak yol yalnızca hata ayıklama amaçlıdır.</span><span class="sxs-lookup"><span data-stu-id="a022b-256">(This absolute path is for debugging purposes only.</span></span> <span data-ttu-id="a022b-257">Bir üretim uygulamasında göreli bir yol kullanırsınız.) <xref:System.ComponentModel.Composition.Hosting.DirectoryCatalog> artık, uzantılar dizinindeki tüm derlemelerde bulunan herhangi bir parçayı bileşim kapsayıcısına ekleyecek.</span><span class="sxs-lookup"><span data-stu-id="a022b-257">In a production application, you would use a relative path.) The <xref:System.ComponentModel.Composition.Hosting.DirectoryCatalog> will now add any parts found in any assemblies in the Extensions directory to the composition container.</span></span>

 <span data-ttu-id="a022b-258">ExtendedOperations projesinde, SimpleCalculator ve System. ComponentModel. Composition başvurularını ekleyin.</span><span class="sxs-lookup"><span data-stu-id="a022b-258">In the ExtendedOperations project, add references to SimpleCalculator and System.ComponentModel.Composition.</span></span> <span data-ttu-id="a022b-259">ExtendedOperations sınıf dosyasında, System. ComponentModel. Composition için bir `Imports` veya `using` açıklaması ekleyin.</span><span class="sxs-lookup"><span data-stu-id="a022b-259">In the ExtendedOperations class file, add an `Imports` or a `using` statement for System.ComponentModel.Composition.</span></span> <span data-ttu-id="a022b-260">Visual Basic Ayrıca, SimpleCalculator için bir `Imports` ifadesini de ekleyin.</span><span class="sxs-lookup"><span data-stu-id="a022b-260">In Visual Basic, also add an `Imports` statement for SimpleCalculator.</span></span> <span data-ttu-id="a022b-261">Ardından, aşağıdaki sınıfı ExtendedOperations sınıf dosyasına ekleyin:</span><span class="sxs-lookup"><span data-stu-id="a022b-261">Then add the following class to the ExtendedOperations class file:</span></span>

```vb
<Export(GetType(SimpleCalculator.IOperation))>
<ExportMetadata("Symbol", "%"c)>
Public Class Modulo
    Implements IOperation

    Public Function Operate(ByVal left As Integer, ByVal right As Integer) As Integer Implements IOperation.Operate
        Return left Mod right
    End Function
End Class
```

```csharp
[Export(typeof(SimpleCalculator.IOperation))]
[ExportMetadata("Symbol", '%')]
public class Mod : SimpleCalculator.IOperation
{
    public int Operate(int left, int right)
    {
        return left % right;
    }
}
```

 <span data-ttu-id="a022b-262">Sözleşmenin eşleşmesi için <xref:System.ComponentModel.Composition.ExportAttribute> özniteliğinin <xref:System.ComponentModel.Composition.ImportAttribute>aynı türde olması gerektiğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="a022b-262">Note that in order for the contract to match, the <xref:System.ComponentModel.Composition.ExportAttribute> attribute must have the same type as the <xref:System.ComponentModel.Composition.ImportAttribute>.</span></span>

 <span data-ttu-id="a022b-263">Projeyi derleyin ve çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="a022b-263">Compile and run the project.</span></span> <span data-ttu-id="a022b-264">Yeni mod (%) sınamasını yapın işlecinde.</span><span class="sxs-lookup"><span data-stu-id="a022b-264">Test the new Mod (%) operator.</span></span>

<a name="conclusion"></a>
## <a name="conclusion"></a><span data-ttu-id="a022b-265">Sonuç</span><span class="sxs-lookup"><span data-stu-id="a022b-265">Conclusion</span></span>
 <span data-ttu-id="a022b-266">Bu konu, MEF 'in temel kavramlarını ele almaktadır.</span><span class="sxs-lookup"><span data-stu-id="a022b-266">This topic covered the basic concepts of MEF.</span></span>

- <span data-ttu-id="a022b-267">Parçalar, kataloglar ve bileşim kapsayıcısı</span><span class="sxs-lookup"><span data-stu-id="a022b-267">Parts, catalogs, and the composition container</span></span>

     <span data-ttu-id="a022b-268">Parçalar ve bileşim kapsayıcısı, MEF uygulamasının temel yapı taşlarıdır.</span><span class="sxs-lookup"><span data-stu-id="a022b-268">Parts and the composition container are the basic building blocks of a MEF application.</span></span> <span data-ttu-id="a022b-269">Bir bölüm, kendisini içeren veya dahil olmak üzere bir değeri içeri aktaran veya dışarı aktaran herhangi bir nesnedir.</span><span class="sxs-lookup"><span data-stu-id="a022b-269">A part is any object that imports or exports a value, up to and including itself.</span></span> <span data-ttu-id="a022b-270">Bir katalog, belirli bir kaynaktan bir parçalar koleksiyonu sağlar.</span><span class="sxs-lookup"><span data-stu-id="a022b-270">A catalog provides a collection of parts from a particular source.</span></span> <span data-ttu-id="a022b-271">Bileşim kapsayıcısı, bir katalog tarafından, dışarı aktarmalar için içeri aktarmalar bağlamayı bağlayan bir katalog tarafından sunulan bölümleri kullanır.</span><span class="sxs-lookup"><span data-stu-id="a022b-271">The composition container uses the parts provided by a catalog to perform composition, the binding of imports to exports.</span></span>

- <span data-ttu-id="a022b-272">İçeri aktarmalar ve dışarı aktarmalar</span><span class="sxs-lookup"><span data-stu-id="a022b-272">Imports and exports</span></span>

     <span data-ttu-id="a022b-273">İçeri ve dışarı aktarmalar, bileşenlerin iletişim kurduğu yoldur.</span><span class="sxs-lookup"><span data-stu-id="a022b-273">Imports and exports are the way by which components communicate.</span></span> <span data-ttu-id="a022b-274">İçeri aktarma ile, bileşen belirli bir değer veya nesne için ihtiyacı belirtir ve bir dışarı aktarma ile bir değerin kullanılabilirliğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="a022b-274">With an import, the component specifies a need for a particular value or object, and with an export it specifies the availability of a value.</span></span> <span data-ttu-id="a022b-275">Her içeri aktarma, sözleşmesi yoluyla dışarı aktarmalar listesi ile eşleştirilir.</span><span class="sxs-lookup"><span data-stu-id="a022b-275">Each import is matched with a list of exports by way of its contract.</span></span>

<a name="where_do_i_go_now"></a>
## <a name="where-do-i-go-now"></a><span data-ttu-id="a022b-276">Şimdi nereden gidebilirim?</span><span class="sxs-lookup"><span data-stu-id="a022b-276">Where Do I Go Now?</span></span>
 <span data-ttu-id="a022b-277">Bu örneğe ilişkin tüm kodu indirmek için bkz. [SimpleCalculator örneği](https://code.msdn.microsoft.com/windowsdesktop/Simple-Calculator-MEF-1152654e).</span><span class="sxs-lookup"><span data-stu-id="a022b-277">To download the complete code for this example, see the [SimpleCalculator sample](https://code.msdn.microsoft.com/windowsdesktop/Simple-Calculator-MEF-1152654e).</span></span>

 <span data-ttu-id="a022b-278">Daha fazla bilgi ve kod örneği için bkz. [Managed Extensibility Framework](https://github.com/MicrosoftArchive/mef).</span><span class="sxs-lookup"><span data-stu-id="a022b-278">For more information and code examples, see [Managed Extensibility Framework](https://github.com/MicrosoftArchive/mef).</span></span> <span data-ttu-id="a022b-279">MEF türlerinin bir listesi için bkz. <xref:System.ComponentModel.Composition?displayProperty=nameWithType> ad alanı.</span><span class="sxs-lookup"><span data-stu-id="a022b-279">For a list of the MEF types, see the <xref:System.ComponentModel.Composition?displayProperty=nameWithType> namespace.</span></span>
