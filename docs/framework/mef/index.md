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
ms.openlocfilehash: 9a601ac860ac3bf81dd01980b020470d3323772f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "79181280"
---
# <a name="managed-extensibility-framework-mef"></a><span data-ttu-id="e3df4-102">Managed Extensibility Framework (MEF)</span><span class="sxs-lookup"><span data-stu-id="e3df4-102">Managed Extensibility Framework (MEF)</span></span>

<span data-ttu-id="e3df4-103">Bu konu, .NET Framework 4'te tanıtılan Yönetilen Genişletilebilirlik Çerçevesi'ne genel bir bakış sağlar.</span><span class="sxs-lookup"><span data-stu-id="e3df4-103">This topic provides an overview of the Managed Extensibility Framework that was introduced in the .NET Framework 4.</span></span>

## <a name="what-is-mef"></a><span data-ttu-id="e3df4-104">MEF nedir?</span><span class="sxs-lookup"><span data-stu-id="e3df4-104">What is MEF?</span></span>

<span data-ttu-id="e3df4-105">Yönetilen Genişletilebilirlik Çerçevesi veya MEF, hafif ve genişletilebilir uygulamalar oluşturmak için bir kitaplıktır.</span><span class="sxs-lookup"><span data-stu-id="e3df4-105">The Managed Extensibility Framework or MEF is a library for creating lightweight, and extensible applications.</span></span> <span data-ttu-id="e3df4-106">Uygulama geliştiricilerin yapılandırma gerektirmeden uzantıları keşfetmesine ve kullanmasına olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="e3df4-106">It allows application developers to discover and use extensions with no configuration required.</span></span> <span data-ttu-id="e3df4-107">Ayrıca, uzantı geliştiricilerin kodu kolayca kapsüllemelerini ve kırılgan sert bağımlılıklardan kaçınmalarını sağlar.</span><span class="sxs-lookup"><span data-stu-id="e3df4-107">It also lets extension developers easily encapsulate code and avoid fragile hard dependencies.</span></span> <span data-ttu-id="e3df4-108">MEF uzantıların yalnızca uygulamalar içinde değil, uygulamalar arasında da yeniden kullanılmasına izin verir.</span><span class="sxs-lookup"><span data-stu-id="e3df4-108">MEF not only allows extensions to be reused within applications, but across applications as well.</span></span>

## <a name="the-problem-of-extensibility"></a><span data-ttu-id="e3df4-109">Genişletilebilirlik sorunu</span><span class="sxs-lookup"><span data-stu-id="e3df4-109">The problem of extensibility</span></span>

<span data-ttu-id="e3df4-110">Genişletilebilirlik için destek sağlaması gereken büyük bir uygulamanın mimarı olduğunuzu düşünün.</span><span class="sxs-lookup"><span data-stu-id="e3df4-110">Imagine that you are the architect of a large application that must provide support for extensibility.</span></span> <span data-ttu-id="e3df4-111">Uygulamanız, potansiyel olarak çok sayıda küçük bileşen içermelidir ve bunları oluşturmak ve çalıştırmaktan sorumludur.</span><span class="sxs-lookup"><span data-stu-id="e3df4-111">Your application has to include a potentially large number of smaller components, and is responsible for creating and running them.</span></span>

<span data-ttu-id="e3df4-112">Soruna en basit yaklaşım, bileşenleri uygulamanıza kaynak kodu olarak eklemek ve bunları doğrudan kodunuzdan çağırmaktır.</span><span class="sxs-lookup"><span data-stu-id="e3df4-112">The simplest approach to the problem is to include the components as source code in your application, and call them directly from your code.</span></span> <span data-ttu-id="e3df4-113">Bunun bariz dezavantajları vardır.</span><span class="sxs-lookup"><span data-stu-id="e3df4-113">This has a number of obvious drawbacks.</span></span> <span data-ttu-id="e3df4-114">En önemlisi, kaynak kodu değiştirmeden yeni bileşenler ekleyemezsiniz, örneğin bir Web uygulamasında kabul edilebilir bir kısıtlama, ancak istemci uygulamasında kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="e3df4-114">Most importantly, you cannot add new components without modifying the source code, a restriction that might be acceptable in, for example, a Web application, but is unworkable in a client application.</span></span> <span data-ttu-id="e3df4-115">Aynı derecede sorunlu, bileşenlerin kaynak koduna erişiminiz olmayabilir, çünkü bunlar üçüncü taraflarca geliştirilebilir ve aynı nedenle sizinkine erişmelerine izin veremezsiniz.</span><span class="sxs-lookup"><span data-stu-id="e3df4-115">Equally problematic, you may not have access to the source code for the components, because they might be developed by third parties, and for the same reason you cannot allow them to access yours.</span></span>

<span data-ttu-id="e3df4-116">Biraz daha karmaşık bir yaklaşım, uygulama ve bileşenleri arasında ayrıştırma izin vermek için bir uzantı noktası veya arabirim sağlamak olacaktır.</span><span class="sxs-lookup"><span data-stu-id="e3df4-116">A slightly more sophisticated approach would be to provide an extension point or interface, to permit decoupling between the application and its components.</span></span> <span data-ttu-id="e3df4-117">Bu modelaltında, bir bileşenin uygulayabileceği bir arabirim ve uygulamanızla etkileşimkurmasını sağlamak için bir API sağlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e3df4-117">Under this model, you might provide an interface that a component can implement, and an API to enable it to interact with your application.</span></span> <span data-ttu-id="e3df4-118">Bu, kaynak kodu erişimi gerektiren sorunu çözer, ancak yine de kendi zorlukları vardır.</span><span class="sxs-lookup"><span data-stu-id="e3df4-118">This solves the problem of requiring source code access, but it still has its own difficulties.</span></span>

<span data-ttu-id="e3df4-119">Uygulama bileşenleri kendi başına keşfetmek için herhangi bir kapasiteye sahip olmadığından, yine de hangi bileşenlerin kullanılabilir olduğu ve yüklenmesi gerektiği açıkça söylenmelidir.</span><span class="sxs-lookup"><span data-stu-id="e3df4-119">Because the application lacks any capacity for discovering components on its own, it must still be explicitly told which components are available and should be loaded.</span></span> <span data-ttu-id="e3df4-120">Bu genellikle kullanılabilir bileşenleri bir yapılandırma dosyasına açıkça kaydederek gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="e3df4-120">This is typically accomplished by explicitly registering the available components in a configuration file.</span></span> <span data-ttu-id="e3df4-121">Bu, bileşenlerin doğru olduğundan güvence verilmesinin, özellikle güncelleştirmeyi yapması beklenen geliştirici değil, son kullanıcı ysa, bir bakım sorunu haline gelmesi anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="e3df4-121">This means that assuring that the components are correct becomes a maintenance issue, particularly if it is the end user and not the developer who is expected to do the updating.</span></span>

<span data-ttu-id="e3df4-122">Buna ek olarak, bileşenler, uygulamanın kendisinin katı olarak tanımlanmış kanalları dışında birbirleriyle iletişim kuramaz.</span><span class="sxs-lookup"><span data-stu-id="e3df4-122">In addition, components are incapable of communicating with one another, except through the rigidly defined channels of the application itself.</span></span> <span data-ttu-id="e3df4-123">Uygulama mimarı belirli bir iletişim gereksinimini tahmin etmemişse, bu genellikle imkansızdır.</span><span class="sxs-lookup"><span data-stu-id="e3df4-123">If the application architect has not anticipated the need for a particular communication, it is usually impossible.</span></span>

<span data-ttu-id="e3df4-124">Son olarak, bileşen geliştiricilerin uyguladıkları arabirimi içeren derlemeye sıkı bir bağımlılık kabul etmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="e3df4-124">Finally, the component developers must accept a hard dependency on what assembly contains the interface they implement.</span></span> <span data-ttu-id="e3df4-125">Bu, bir bileşenin birden fazla uygulamada kullanılmasını zorlaştırır ve bileşenler için bir test çerçevesi oluşturduğunuzda da sorun yaratabilir.</span><span class="sxs-lookup"><span data-stu-id="e3df4-125">This makes it difficult for a component to be used in more than one application, and can also create problems when you create a test framework for components.</span></span>

## <a name="what-mef-provides"></a><span data-ttu-id="e3df4-126">MEF'in sağladığı</span><span class="sxs-lookup"><span data-stu-id="e3df4-126">What MEF provides</span></span>

<span data-ttu-id="e3df4-127">Kullanılabilir bileşenlerin bu açık kaydı yerine, MEF *bunları kompozisyon*aracılığıyla dolaylı olarak keşfetmenin bir yolunu sağlar.</span><span class="sxs-lookup"><span data-stu-id="e3df4-127">Instead of this explicit registration of available components, MEF provides a way to discover them implicitly, via *composition*.</span></span> <span data-ttu-id="e3df4-128">Bir MEF bileşeni, bir *parçası*olarak adlandırılan, bildirimsel hem bağımlılıkları *(içeri aktarma*olarak bilinir) ve hangi yetenekleri *(dışa*aktarma olarak bilinir) o kullanılabilir hale belirtir.</span><span class="sxs-lookup"><span data-stu-id="e3df4-128">A MEF component, called a *part*, declaratively specifies both its dependencies (known as *imports*) and what capabilities (known as *exports*) it makes available.</span></span> <span data-ttu-id="e3df4-129">Bir parça oluşturulduğunda, MEF kompozisyon motoru diğer parçalardan elde edilebilecek lerle ithalatını karşılar.</span><span class="sxs-lookup"><span data-stu-id="e3df4-129">When a part is created, the MEF composition engine satisfies its imports with what is available from other parts.</span></span>

<span data-ttu-id="e3df4-130">Bu yaklaşım, önceki bölümde tartışılan sorunları çözer.</span><span class="sxs-lookup"><span data-stu-id="e3df4-130">This approach solves the problems discussed in the previous section.</span></span> <span data-ttu-id="e3df4-131">MEF parçaları yeteneklerini bildirimsel olarak belirttiğinden, çalışma zamanında bulunabilirler, bu da bir uygulamanın sabit kodlanmış başvurular veya kırılgan yapılandırma dosyaları olmadan parçaları kullanabileceği anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="e3df4-131">Because MEF parts declaratively specify their capabilities, they are discoverable at runtime, which means an application can make use of parts without either hard-coded references or fragile configuration files.</span></span> <span data-ttu-id="e3df4-132">MEF, uygulamaların parçaları meta verilerine göre, anlık olarak oluşturmadan ve hatta derlemelerini yüklemeden keşfetmelerine ve incelemelerine olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="e3df4-132">MEF allows applications to discover and examine parts by their metadata, without instantiating them or even loading their assemblies.</span></span> <span data-ttu-id="e3df4-133">Sonuç olarak, uzantıların ne zaman ve nasıl yüklenmesi gerektiğini dikkatlice belirtmenize gerek yoktur.</span><span class="sxs-lookup"><span data-stu-id="e3df4-133">As a result, there is no need to carefully specify when and how extensions should be loaded.</span></span>

<span data-ttu-id="e3df4-134">Sağlanan dışa aktarımlarına ek olarak, bir kısmı diğer parçalar tarafından doldurulacak olan ithalatını belirtebilir.</span><span class="sxs-lookup"><span data-stu-id="e3df4-134">In addition to its provided exports, a part can specify its imports, which will be filled by other parts.</span></span> <span data-ttu-id="e3df4-135">Bu, parçalar arasındaki iletişimi yalnızca mümkün değil, aynı zamanda kolay hale getirir ve kodun iyi bir şekilde faktoringine olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="e3df4-135">This makes communication among parts not only possible, but easy, and allows for good factoring of code.</span></span> <span data-ttu-id="e3df4-136">Örneğin, birçok bileşende ortak olan hizmetler ayrı bir parçaya ayrılabilir ve kolayca değiştirilebilir veya değiştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="e3df4-136">For example, services common to many components can be factored into a separate part and easily modified or replaced.</span></span>

<span data-ttu-id="e3df4-137">MEF modeli belirli bir uygulama derlemesine sabit bağımlılık gerektirmediği için, uzantıların uygulamadan uygulamaya yeniden kullanılmasına izin verir.</span><span class="sxs-lookup"><span data-stu-id="e3df4-137">Because the MEF model requires no hard dependency on a particular application assembly, it allows extensions to be reused from application to application.</span></span> <span data-ttu-id="e3df4-138">Bu, uzantı bileşenlerini test etmek için uygulamadan bağımsız bir test kayışı geliştirmeyi de kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="e3df4-138">This also makes it easy to develop a test harness, independent of the application, to test extension components.</span></span>

<span data-ttu-id="e3df4-139">MEF kullanılarak yazılmış genişletilebilir bir uygulama, uzantı bileşenleri tarafından doldurulabilen bir alma işlemi bildirir ve uygulama hizmetlerini uzantılara maruz bırakmak için dışa aktarımlar da bildirebilir.</span><span class="sxs-lookup"><span data-stu-id="e3df4-139">An extensible application written by using MEF declares an import that can be filled by extension components, and may also declare exports in order to expose application services to extensions.</span></span> <span data-ttu-id="e3df4-140">Her uzantı bileşeni bir dışa aktarım bildirir ve ayrıca içeri aktarımlar da beyan edebilir.</span><span class="sxs-lookup"><span data-stu-id="e3df4-140">Each extension component declares an export, and may also declare imports.</span></span> <span data-ttu-id="e3df4-141">Bu şekilde, uzantı bileşenlerinin kendileri otomatik olarak genişletilebilir.</span><span class="sxs-lookup"><span data-stu-id="e3df4-141">In this way, extension components themselves are automatically extensible.</span></span>

## <a name="where-mef-is-available"></a><span data-ttu-id="e3df4-142">MEF'in mevcut olduğu yerler</span><span class="sxs-lookup"><span data-stu-id="e3df4-142">Where MEF is available</span></span>

<span data-ttu-id="e3df4-143">MEF ,NET Framework 4'ün ayrılmaz bir parçasıdır ve .NET Framework'ün kullanıldığı her yerde kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="e3df4-143">MEF is an integral part of the .NET Framework 4, and is available wherever the .NET Framework is used.</span></span> <span data-ttu-id="e3df4-144">İstemci uygulamalarınızda, windows formlarını, WPF'yi veya başka bir teknolojiyi kullanıp kullanmadıklarını veya ASP.NET kullanan sunucu uygulamalarında MEF'i kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e3df4-144">You can use MEF in your client applications, whether they use Windows Forms, WPF, or any other technology, or in server applications that use ASP.NET.</span></span>

## <a name="mef-and-maf"></a><span data-ttu-id="e3df4-145">MEF ve MAF</span><span class="sxs-lookup"><span data-stu-id="e3df4-145">MEF and MAF</span></span>

<span data-ttu-id="e3df4-146">.NET Framework'ün önceki sürümlerinde, uygulamaların uzantıları yalıtmalarına ve yönetmelerine olanak sağlamak üzere tasarlanmış Yönetilen Eklenti Çerçevesi (MAF) sunulmuştur.</span><span class="sxs-lookup"><span data-stu-id="e3df4-146">Previous versions of the .NET Framework introduced the Managed Add-in Framework (MAF), designed to allow applications to isolate and manage extensions.</span></span> <span data-ttu-id="e3df4-147">MAF'nin odak noktası MEF'ten biraz daha yüksektir, uzatma yalıtımı ve montaj yükleme ve boşaltma üzerine yoğunlaşırken, MEF'in odak noktası keşfedilebilirlik, genişletilebilirlik ve taşınabilirliktir.</span><span class="sxs-lookup"><span data-stu-id="e3df4-147">The focus of MAF is slightly higher-level than MEF, concentrating on extension isolation and assembly loading and unloading, while MEF's focus is on discoverability, extensibility, and portability.</span></span> <span data-ttu-id="e3df4-148">İki çerçeve sorunsuz bir şekilde çalışır ve tek bir uygulama her ikiden de yararlanabilir.</span><span class="sxs-lookup"><span data-stu-id="e3df4-148">The two frameworks interoperate smoothly, and a single application can take advantage of both.</span></span>

## <a name="simplecalculator-an-example-application"></a><span data-ttu-id="e3df4-149">SimpleCalculator: Örnek bir uygulama</span><span class="sxs-lookup"><span data-stu-id="e3df4-149">SimpleCalculator: An example application</span></span>

<span data-ttu-id="e3df4-150">MEF'in neler yapabileceğini görmenin en basit yolu basit bir MEF uygulaması oluşturmaktır.</span><span class="sxs-lookup"><span data-stu-id="e3df4-150">The simplest way to see what MEF can do is to build a simple MEF application.</span></span> <span data-ttu-id="e3df4-151">Bu örnekte, SimpleCalculator adlı çok basit bir hesap makinesi oluşturursunuz.</span><span class="sxs-lookup"><span data-stu-id="e3df4-151">In this example, you build a very simple calculator named SimpleCalculator.</span></span> <span data-ttu-id="e3df4-152">SimpleCalculator'ın amacı, temel aritmetik komutları "5+3" veya "6-2" şeklinde kabul eden ve doğru yanıtları döndüren bir konsol uygulaması oluşturmaktır.</span><span class="sxs-lookup"><span data-stu-id="e3df4-152">The goal of SimpleCalculator is to create a console application that accepts basic arithmetic commands, in the form "5+3" or "6-2", and returns the correct answers.</span></span> <span data-ttu-id="e3df4-153">MEF kullanarak, uygulama kodunu değiştirmeden yeni işleçler ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e3df4-153">Using MEF, you'll be able to add new operators without changing the application code.</span></span>

<span data-ttu-id="e3df4-154">Bu örnek için tam kodu indirmek için [SimpleCalculator örneğine (Visual Basic)](https://docs.microsoft.com/samples/dotnet/samples/simple-calculator-vb/)bakın.</span><span class="sxs-lookup"><span data-stu-id="e3df4-154">To download the complete code for this example, see the [SimpleCalculator sample (Visual Basic)](https://docs.microsoft.com/samples/dotnet/samples/simple-calculator-vb/).</span></span>

> [!NOTE]
> <span data-ttu-id="e3df4-155">SimpleCalculator amacı mutlaka kullanımı için gerçekçi bir senaryo sağlamak yerine, MEF kavramları ve sözdizimi göstermektir.</span><span class="sxs-lookup"><span data-stu-id="e3df4-155">The purpose of SimpleCalculator is to demonstrate the concepts and syntax of MEF, rather than to necessarily provide a realistic scenario for its use.</span></span> <span data-ttu-id="e3df4-156">MEF'in gücünden en çok yararlanacak uygulamaların çoğu SimpleCalculator'dan daha karmaşıktır.</span><span class="sxs-lookup"><span data-stu-id="e3df4-156">Many of the applications that would benefit most from the power of MEF are more complex than SimpleCalculator.</span></span> <span data-ttu-id="e3df4-157">Daha kapsamlı örnekler için GitHub'daki [Yönetilen Genişletilebilirlik Çerçevesi'ne](https://github.com/MicrosoftArchive/mef) bakın.</span><span class="sxs-lookup"><span data-stu-id="e3df4-157">For more extensive examples, see the [Managed Extensibility Framework](https://github.com/MicrosoftArchive/mef) on GitHub.</span></span>

- <span data-ttu-id="e3df4-158">Başlamak için Visual Studio'da yeni bir Konsol `SimpleCalculator`Uygulaması projesi oluşturun ve adını adlandırın.</span><span class="sxs-lookup"><span data-stu-id="e3df4-158">To start, in Visual Studio, create a new Console Application project and name it `SimpleCalculator`.</span></span>

- <span data-ttu-id="e3df4-159">MEF'in `System.ComponentModel.Composition` bulunduğu derlemeye bir başvuru ekleyin.</span><span class="sxs-lookup"><span data-stu-id="e3df4-159">Add a reference to the `System.ComponentModel.Composition` assembly, where MEF resides.</span></span>

- <span data-ttu-id="e3df4-160">*Open Module1.vb* veya *Program.cs* ve `System.ComponentModel.Composition` `System.ComponentModel.Composition.Hosting`eklemek `Imports` veya `using` ifadeler için ve .</span><span class="sxs-lookup"><span data-stu-id="e3df4-160">Open *Module1.vb* or *Program.cs* and add `Imports` or `using` statements for `System.ComponentModel.Composition` and `System.ComponentModel.Composition.Hosting`.</span></span> <span data-ttu-id="e3df4-161">Bu iki ad alanı, genişletilebilir bir uygulama geliştirmek için gereken MEF türleri içerir.</span><span class="sxs-lookup"><span data-stu-id="e3df4-161">These two namespaces contain MEF types you will need to develop an extensible application.</span></span>

- <span data-ttu-id="e3df4-162">Visual Basic kullanıyorsanız, `Public` `Module1` modülü bildiren satıra anahtar kelimeyi ekleyin.</span><span class="sxs-lookup"><span data-stu-id="e3df4-162">If you're using Visual Basic, add the `Public` keyword to the line that declares the `Module1` module.</span></span>

## <a name="composition-container-and-catalogs"></a><span data-ttu-id="e3df4-163">Kompozisyon konteyner ve kataloglar</span><span class="sxs-lookup"><span data-stu-id="e3df4-163">Composition container and catalogs</span></span>

<span data-ttu-id="e3df4-164">MEF kompozisyon modelinin çekirdeği, mevcut tüm parçaları içeren ve kompozisyon gerçekleştiren kompozisyon kapsayıcısır. *composition container*</span><span class="sxs-lookup"><span data-stu-id="e3df4-164">The core of the MEF composition model is the *composition container*, which contains all the parts available and performs composition.</span></span> <span data-ttu-id="e3df4-165">Kompozisyon, ithalatın dışa aktarımla eşleştirilmesidir.</span><span class="sxs-lookup"><span data-stu-id="e3df4-165">Composition is the matching up of imports to exports.</span></span> <span data-ttu-id="e3df4-166">Kompozisyon kapsayıcıen yaygın <xref:System.ComponentModel.Composition.Hosting.CompositionContainer>türü, ve SimpleCalculator için bu kullanacağız.</span><span class="sxs-lookup"><span data-stu-id="e3df4-166">The most common type of composition container is <xref:System.ComponentModel.Composition.Hosting.CompositionContainer>, and you'll use this for SimpleCalculator.</span></span>

<span data-ttu-id="e3df4-167">Visual Basic kullanıyorsanız, `Program` *Module1.vb'de*adlandırılmış bir genel sınıf ekleyin.</span><span class="sxs-lookup"><span data-stu-id="e3df4-167">If you're using Visual Basic, add a public class named `Program` in *Module1.vb*.</span></span>

<span data-ttu-id="e3df4-168">*Module1.vb* veya `Program` *Program.cs*sınıfa aşağıdaki satırı ekleyin:</span><span class="sxs-lookup"><span data-stu-id="e3df4-168">Add the following line to the `Program` class in *Module1.vb* or *Program.cs*:</span></span>

```vb
Dim _container As CompositionContainer
```

```csharp
private CompositionContainer _container;
```

<span data-ttu-id="e3df4-169">Kullanılabilir parçaları keşfetmek için, kompozisyon kapları bir *katalog*kullanır.</span><span class="sxs-lookup"><span data-stu-id="e3df4-169">In order to discover the parts available to it, the composition containers makes use of a *catalog*.</span></span> <span data-ttu-id="e3df4-170">Katalog, bazı kaynaktan kullanılabilir parçaları n için kullanılabilir kılan bir nesnedir.</span><span class="sxs-lookup"><span data-stu-id="e3df4-170">A catalog is an object that makes available parts discovered from some source.</span></span> <span data-ttu-id="e3df4-171">MEF, sağlanan bir tür, derleme veya dizin parçaları keşfetmek için kataloglar sağlar.</span><span class="sxs-lookup"><span data-stu-id="e3df4-171">MEF provides catalogs to discover parts from a provided type, an assembly, or a directory.</span></span> <span data-ttu-id="e3df4-172">Uygulama geliştiricileri, Web hizmeti gibi diğer kaynaklardan parçaları kolayca keşfetmek için yeni kataloglar oluşturabilir.</span><span class="sxs-lookup"><span data-stu-id="e3df4-172">Application developers can easily create new catalogs to discover parts from other sources, such as a Web service.</span></span>

<span data-ttu-id="e3df4-173">Sınıfa aşağıdaki oluşturucuekleyin: `Program`</span><span class="sxs-lookup"><span data-stu-id="e3df4-173">Add the following constructor to the `Program` class:</span></span>

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

<span data-ttu-id="e3df4-174">Çağrı, <xref:System.ComponentModel.Composition.AttributedModelServices.ComposeParts%2A> kompozisyon kapsayıcısına belirli bir parça kümesi oluşturmasını `Program`söyler, bu durumda geçerli durumda .</span><span class="sxs-lookup"><span data-stu-id="e3df4-174">The call to <xref:System.ComponentModel.Composition.AttributedModelServices.ComposeParts%2A> tells the composition container to compose a specific set of parts, in this case the current instance of `Program`.</span></span> <span data-ttu-id="e3df4-175">Ancak bu noktada, hiçbir şey `Program` olmayacak, çünkü hiçbir ithalat doldurmak zorunda.</span><span class="sxs-lookup"><span data-stu-id="e3df4-175">At this point, however, nothing will happen, since `Program` has no imports to fill.</span></span>

## <a name="imports-and-exports-with-attributes"></a><span data-ttu-id="e3df4-176">Öznitelikleri ile İthalat ve İhracat</span><span class="sxs-lookup"><span data-stu-id="e3df4-176">Imports and Exports with attributes</span></span>

<span data-ttu-id="e3df4-177">İlk olarak, `Program` bir hesap makinesi alma var.</span><span class="sxs-lookup"><span data-stu-id="e3df4-177">First, you have `Program` import a calculator.</span></span> <span data-ttu-id="e3df4-178">Bu, kullanıcı arabirimi endişelerinin ayrılmasına olanak sağlar, örneğin `Program`konsol girişi ve hesap makinesi nin mantığından girecek çıktı.</span><span class="sxs-lookup"><span data-stu-id="e3df4-178">This allows the separation of user interface concerns, such as the console input and output that will go into `Program`, from the logic of the calculator.</span></span>

<span data-ttu-id="e3df4-179">`Program` Sınıfa aşağıdaki kodu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="e3df4-179">Add the following code to the `Program` class:</span></span>

```vb
<Import(GetType(ICalculator))>
Public Property calculator As ICalculator
```

```csharp
[Import(typeof(ICalculator))]
public ICalculator calculator;
```

<span data-ttu-id="e3df4-180">`calculator` Nesnenin bildiriminin olağandışı olmadığını, ancak öznitelik ile <xref:System.ComponentModel.Composition.ImportAttribute> süslenmiş olduğuna dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="e3df4-180">Notice that the declaration of the `calculator` object is not unusual, but that it is decorated with the <xref:System.ComponentModel.Composition.ImportAttribute> attribute.</span></span> <span data-ttu-id="e3df4-181">Bu öznitelik bir şey bir alma olarak bildirir; diğer bir de, nesne oluşturulduğunda kompozisyon motoru tarafından doldurulacaktır.</span><span class="sxs-lookup"><span data-stu-id="e3df4-181">This attribute declares something to be an import; that is, it will be filled by the composition engine when the object is composed.</span></span>

<span data-ttu-id="e3df4-182">Her ithalat, hangi ihracatile eşleşeceğini belirleyen bir *sözleşmeye*sahiptir.</span><span class="sxs-lookup"><span data-stu-id="e3df4-182">Every import has a *contract*, which determines what exports it will be matched with.</span></span> <span data-ttu-id="e3df4-183">Sözleşme açıkça belirtilen bir dize olabilir veya otomatik olarak belirli bir tür MEF tarafından `ICalculator`oluşturulabilir, Bu durumda arayüzü .</span><span class="sxs-lookup"><span data-stu-id="e3df4-183">The contract can be an explicitly specified string, or it can be automatically generated by MEF from a given type, in this case the interface `ICalculator`.</span></span> <span data-ttu-id="e3df4-184">Eşleşen bir sözleşme ile beyan edilen herhangi bir ihracat bu alma yerine getirecektir.</span><span class="sxs-lookup"><span data-stu-id="e3df4-184">Any export declared with a matching contract will fulfill this import.</span></span> <span data-ttu-id="e3df4-185">`calculator` Nesnenin türü aslında `ICalculator`olsa da, bu gerekli değildir unutmayın.</span><span class="sxs-lookup"><span data-stu-id="e3df4-185">Note that while the type of the `calculator` object is in fact `ICalculator`, this is not required.</span></span> <span data-ttu-id="e3df4-186">Sözleşme, içe aktarma nesnesinin türünden bağımsızdır.</span><span class="sxs-lookup"><span data-stu-id="e3df4-186">The contract is independent from the type of the importing object.</span></span> <span data-ttu-id="e3df4-187">(Bu durumda, dışarıda bırakabilirsiniz `typeof(ICalculator)`.</span><span class="sxs-lookup"><span data-stu-id="e3df4-187">(In this case, you could leave out the `typeof(ICalculator)`.</span></span> <span data-ttu-id="e3df4-188">MEF, açıkça belirtmediğiniz sürece sözleşmenin alma türüne göre otomatik olarak kabul edilecektir.)</span><span class="sxs-lookup"><span data-stu-id="e3df4-188">MEF will automatically assume the contract to be based on the type of the import unless you specify it explicitly.)</span></span>

<span data-ttu-id="e3df4-189">Modüle veya `SimpleCalculator` ad alanına bu çok basit arabirimi ekleyin:</span><span class="sxs-lookup"><span data-stu-id="e3df4-189">Add this very simple interface to the module or `SimpleCalculator` namespace:</span></span>

```vb
Public Interface ICalculator
    Function Calculate(input As String) As String
End Interface
```

```csharp
public interface ICalculator
{
    String Calculate(String input);
}
```

<span data-ttu-id="e3df4-190">Artık tanımladığınız `ICalculator`için, bunu uygulayan bir sınıfa ihtiyacınız vardır.</span><span class="sxs-lookup"><span data-stu-id="e3df4-190">Now that you have defined `ICalculator`, you need a class that implements it.</span></span> <span data-ttu-id="e3df4-191">Modüle veya `SimpleCalculator` ad alanına aşağıdaki sınıfı ekleyin:</span><span class="sxs-lookup"><span data-stu-id="e3df4-191">Add the following class to the module or `SimpleCalculator` namespace:</span></span>

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

<span data-ttu-id="e3df4-192">İşte ithalatla eşleşecek `Program`ihracat.</span><span class="sxs-lookup"><span data-stu-id="e3df4-192">Here is the export that will match the import in `Program`.</span></span> <span data-ttu-id="e3df4-193">İhracatın içe aktarılamasıyla eşleşebilmesi için, ihracatın aynı sözleşmeye sahip olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="e3df4-193">In order for the export to match the import, the export must have the same contract.</span></span> <span data-ttu-id="e3df4-194">Dayalı bir sözleşme kapsamında `typeof(MySimpleCalculator)` ihracat bir uyumsuzluk üretecek ve ithalat doldurulmaz; sözleşmetam olarak eşleşmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="e3df4-194">Exporting under a contract based on `typeof(MySimpleCalculator)` would produce a mismatch, and the import would not be filled; the contract needs to match exactly.</span></span>

<span data-ttu-id="e3df4-195">Kompozisyon kapsayıcısı bu derlemede bulunan tüm parçalarla doldurulacağı için, `MySimpleCalculator` parça kullanılabilir olacaktır.</span><span class="sxs-lookup"><span data-stu-id="e3df4-195">Since the composition container will be populated with all the parts available in this assembly, the `MySimpleCalculator` part will be available.</span></span> <span data-ttu-id="e3df4-196">Nesne üzerinde `Program` `Program` kompozisyon gerçekleştiren oluşturucu, içe aktarma bu `MySimpleCalculator` amaç için oluşturulacak bir nesne ile doldurulur.</span><span class="sxs-lookup"><span data-stu-id="e3df4-196">When the constructor for `Program` performs composition on the `Program` object, its import will be filled with a `MySimpleCalculator` object, which will be created for that purpose.</span></span>

<span data-ttu-id="e3df4-197">Kullanıcı arabirimi`Program`katmanı ( ) başka bir şey bilmek gerekmez.</span><span class="sxs-lookup"><span data-stu-id="e3df4-197">The user interface layer (`Program`) does not need to know anything else.</span></span> <span data-ttu-id="e3df4-198">Bu nedenle `Main` yöntemde kullanıcı arabirimi mantığının geri kalanını doldurabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e3df4-198">You can therefore fill in the rest of the user interface logic in the `Main` method.</span></span>

<span data-ttu-id="e3df4-199">`Main` yöntemine aşağıdaki kodu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="e3df4-199">Add the following code to the `Main` method:</span></span>

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
    string s;
    Console.WriteLine("Enter Command:");
    while (true)
    {
        s = Console.ReadLine();
        Console.WriteLine(p.calculator.Calculate(s));
    }
}
```

 <span data-ttu-id="e3df4-200">Bu kod sadece bir giriş satırı `Calculate` okur `ICalculator` ve konsola geri yazdığı sonucun işlevini çağırır.</span><span class="sxs-lookup"><span data-stu-id="e3df4-200">This code simply reads a line of input and calls the `Calculate` function of `ICalculator` on the result, which it writes back to the console.</span></span> <span data-ttu-id="e3df4-201">İhtiyacın olan tüm kod `Program`bu.</span><span class="sxs-lookup"><span data-stu-id="e3df4-201">That is all the code you need in `Program`.</span></span> <span data-ttu-id="e3df4-202">İşin geri kalanı parçalarhalinde olacak.</span><span class="sxs-lookup"><span data-stu-id="e3df4-202">All the rest of the work will happen in the parts.</span></span>

## <a name="further-imports-and-importmany"></a><span data-ttu-id="e3df4-203">Diğer İthalat ve İthalatMany</span><span class="sxs-lookup"><span data-stu-id="e3df4-203">Further Imports and ImportMany</span></span>

<span data-ttu-id="e3df4-204">SimpleCalculator'nin genişletilebilmesi için bir işlem listesi alması gerekir.</span><span class="sxs-lookup"><span data-stu-id="e3df4-204">In order for SimpleCalculator to be extensible, it needs to import a list of operations.</span></span> <span data-ttu-id="e3df4-205">Sıradan <xref:System.ComponentModel.Composition.ImportAttribute> bir öznitelik bir ve <xref:System.ComponentModel.Composition.ExportAttribute>yalnızca bir tarafından doldurulur.</span><span class="sxs-lookup"><span data-stu-id="e3df4-205">An ordinary <xref:System.ComponentModel.Composition.ImportAttribute> attribute is filled by one and only one <xref:System.ComponentModel.Composition.ExportAttribute>.</span></span> <span data-ttu-id="e3df4-206">Birden fazla kullanılabilir varsa, kompozisyon motoru bir hata üretir.</span><span class="sxs-lookup"><span data-stu-id="e3df4-206">If more than one is available, the composition engine produces an error.</span></span> <span data-ttu-id="e3df4-207">Herhangi bir sayıda dışa aktarılabilen bir alma <xref:System.ComponentModel.Composition.ImportManyAttribute> işlemi oluşturmak için özniteliği kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e3df4-207">To create an import that can be filled by any number of exports, you can use the <xref:System.ComponentModel.Composition.ImportManyAttribute> attribute.</span></span>

<span data-ttu-id="e3df4-208">Sınıfa aşağıdaki işlemler `MySimpleCalculator` özelliğini ekleyin:</span><span class="sxs-lookup"><span data-stu-id="e3df4-208">Add the following operations property to the `MySimpleCalculator` class:</span></span>

```vb
<ImportMany()>
Public Property operations As IEnumerable(Of Lazy(Of IOperation, IOperationData))
```

```csharp
[ImportMany]
IEnumerable<Lazy<IOperation, IOperationData>> operations;
```

<span data-ttu-id="e3df4-209"><xref:System.Lazy%602>mef tarafından ihracata dolaylı referanslar tutmak için sağlanan bir türdür.</span><span class="sxs-lookup"><span data-stu-id="e3df4-209"><xref:System.Lazy%602> is a type provided by MEF to hold indirect references to exports.</span></span> <span data-ttu-id="e3df4-210">Burada, dışa aktarılan nesnenin kendisine ek olarak, *dışa aktarma meta verileri*veya dışa aktarılan nesneyi açıklayan bilgiler de alırsınız.</span><span class="sxs-lookup"><span data-stu-id="e3df4-210">Here, in addition to the exported object itself, you also get *export metadata*, or information that describes the exported object.</span></span> <span data-ttu-id="e3df4-211">Her <xref:System.Lazy%602> biri, `IOperation` gerçek bir işlemi temsil `IOperationData` eden bir nesne ve meta verilerini temsil eden bir nesne içerir.</span><span class="sxs-lookup"><span data-stu-id="e3df4-211">Each <xref:System.Lazy%602> contains an `IOperation` object, representing an actual operation, and an `IOperationData` object, representing its metadata.</span></span>

<span data-ttu-id="e3df4-212">Modüle veya `SimpleCalculator` ad alanına aşağıdaki basit arabirimleri ekleyin:</span><span class="sxs-lookup"><span data-stu-id="e3df4-212">Add the following simple interfaces to the module or `SimpleCalculator` namespace:</span></span>

```vb
Public Interface IOperation
    Function Operate(left As Integer, right As Integer) As Integer
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

 <span data-ttu-id="e3df4-213">Bu durumda, her işlem için meta veri , +, -, \*, gibi bu işlemi temsil eden simgedir.</span><span class="sxs-lookup"><span data-stu-id="e3df4-213">In this case, the metadata for each operation is the symbol that represents that operation, such as +, -, \*, and so on.</span></span> <span data-ttu-id="e3df4-214">Ekleme işlemini kullanılabilir hale getirmek için, modüle veya `SimpleCalculator` ad alanına aşağıdaki sınıfı ekleyin:</span><span class="sxs-lookup"><span data-stu-id="e3df4-214">To make the addition operation available, add the following class to the module or `SimpleCalculator` namespace:</span></span>

```vb
<Export(GetType(IOperation))>
<ExportMetadata("Symbol", "+"c)>
Public Class Add
    Implements IOperation

    Public Function Operate(left As Integer, right As Integer) As Integer Implements IOperation.Operate
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

<span data-ttu-id="e3df4-215">Öznitelik <xref:System.ComponentModel.Composition.ExportAttribute> daha önce olduğu gibi çalışır.</span><span class="sxs-lookup"><span data-stu-id="e3df4-215">The <xref:System.ComponentModel.Composition.ExportAttribute> attribute functions as it did before.</span></span> <span data-ttu-id="e3df4-216">Öznitelik, <xref:System.ComponentModel.Composition.ExportMetadataAttribute> bu dışa aktarıma ad değeri çifti biçiminde meta verileri bağlar.</span><span class="sxs-lookup"><span data-stu-id="e3df4-216">The <xref:System.ComponentModel.Composition.ExportMetadataAttribute> attribute attaches metadata, in the form of a name-value pair, to that export.</span></span> <span data-ttu-id="e3df4-217">`Add` Sınıf uygular `IOperation`ken, uygulayan `IOperationData` bir sınıf açıkça tanımlanmamıştır.</span><span class="sxs-lookup"><span data-stu-id="e3df4-217">While the `Add` class implements `IOperation`, a class that implements `IOperationData` is not explicitly defined.</span></span> <span data-ttu-id="e3df4-218">Bunun yerine, bir sınıf örtülü mef tarafından sağlanan meta veri adlarını dayalı özellikleri ile oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="e3df4-218">Instead, a class is implicitly created by MEF with properties based on the names of the metadata provided.</span></span> <span data-ttu-id="e3df4-219">(Bu, MEF'deki meta verilere erişmenin birkaç yollarından biridir.)</span><span class="sxs-lookup"><span data-stu-id="e3df4-219">(This is one of several ways to access metadata in MEF.)</span></span>

<span data-ttu-id="e3df4-220">MEF kompozisyon *özyinelemeli.*</span><span class="sxs-lookup"><span data-stu-id="e3df4-220">Composition in MEF is *recursive*.</span></span> <span data-ttu-id="e3df4-221">Açıkça bir tür `Program` `MySimpleCalculator`olduğu ortaya `ICalculator` çıktı bir içe aktarılan nesne, besteledi.</span><span class="sxs-lookup"><span data-stu-id="e3df4-221">You explicitly composed the `Program` object, which imported an `ICalculator` that turned out to be of type `MySimpleCalculator`.</span></span> <span data-ttu-id="e3df4-222">`MySimpleCalculator`, sırayla, `IOperation` nesnelerin bir koleksiyon alır ve bu `MySimpleCalculator` alma oluşturulduğunda doldurulur, aynı `Program`zamanda ithalat olarak.</span><span class="sxs-lookup"><span data-stu-id="e3df4-222">`MySimpleCalculator`, in turn, imports a collection of `IOperation` objects, and that import will be filled when `MySimpleCalculator` is created, at the same time as the imports of `Program`.</span></span> <span data-ttu-id="e3df4-223">`Add` Sınıf daha fazla alma beyan ederse, bu da doldurulması gerekir, ve benzeri.</span><span class="sxs-lookup"><span data-stu-id="e3df4-223">If the `Add` class declared a further import, that too would have to be filled, and so on.</span></span> <span data-ttu-id="e3df4-224">Doldurulmamış kalan tüm alma işlemi kompozisyon hatasına neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="e3df4-224">Any import left unfilled results in a composition error.</span></span> <span data-ttu-id="e3df4-225">(Ancak, içeri aktarımları isteğe bağlı olarak beyan etmek veya varsayılan değerler atamak mümkündür.)</span><span class="sxs-lookup"><span data-stu-id="e3df4-225">(It is possible, however, to declare imports to be optional or to assign them default values.)</span></span>

## <a name="calculator-logic"></a><span data-ttu-id="e3df4-226">Hesap Makinesi Mantığı</span><span class="sxs-lookup"><span data-stu-id="e3df4-226">Calculator Logic</span></span>

<span data-ttu-id="e3df4-227">Bu parçalar yerinde, geriye kalan tek şey hesap makinesi mantığının kendisidir.</span><span class="sxs-lookup"><span data-stu-id="e3df4-227">With these parts in place, all that remains is the calculator logic itself.</span></span> <span data-ttu-id="e3df4-228">Yöntemi uygulamak için `MySimpleCalculator` sınıfa aşağıdaki kodu ekleyin: `Calculate`</span><span class="sxs-lookup"><span data-stu-id="e3df4-228">Add the following code in the `MySimpleCalculator` class to implement the `Calculate` method:</span></span>

```vb
Public Function Calculate(input As String) As String Implements ICalculator.Calculate
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
public String Calculate(string input)
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

<span data-ttu-id="e3df4-229">İlk adımlar, giriş dizesini sol ve sağ operandlara ve bir işleç karakterine ayrışturur.</span><span class="sxs-lookup"><span data-stu-id="e3df4-229">The initial steps parse the input string into left and right operands and an operator character.</span></span> <span data-ttu-id="e3df4-230">Döngüde, `foreach` koleksiyonun `operations` her üyesi incelenir.</span><span class="sxs-lookup"><span data-stu-id="e3df4-230">In the `foreach` loop, every member of the `operations` collection is examined.</span></span> <span data-ttu-id="e3df4-231">Bu nesneler türündendir <xref:System.Lazy%602>ve meta veri değerleri ve dışa <xref:System.Lazy%602.Metadata%2A> aktarılan nesne <xref:System.Lazy%601.Value%2A> sırasıyla özellik ve özellik ile erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="e3df4-231">These objects are of type <xref:System.Lazy%602>, and their metadata values and exported object can be accessed with the <xref:System.Lazy%602.Metadata%2A> property and the <xref:System.Lazy%601.Value%2A> property respectively.</span></span> <span data-ttu-id="e3df4-232">`Symbol` Bu durumda, nesnenin `IOperationData` özelliği eşleşebilir olarak keşfedilirse, hesap `Operate` makinesi nesnenin yöntemini `IOperation` çağırır ve sonucu döndürür.</span><span class="sxs-lookup"><span data-stu-id="e3df4-232">In this case, if the `Symbol` property of the `IOperationData` object is discovered to be a match, the calculator calls the `Operate` method of the `IOperation` object and returns the result.</span></span>

<span data-ttu-id="e3df4-233">Hesap makinesini tamamlamak için, bir dizedeki ilk basamaksız karakterin konumunu döndüren bir yardımcı yöntemine de ihtiyacınız vardır.</span><span class="sxs-lookup"><span data-stu-id="e3df4-233">To complete the calculator, you also need a helper method that returns the position of the first non-digit character in a string.</span></span> <span data-ttu-id="e3df4-234">Sınıfa aşağıdaki yardımcı yöntemi `MySimpleCalculator` ekleyin:</span><span class="sxs-lookup"><span data-stu-id="e3df4-234">Add the following helper method to the `MySimpleCalculator` class:</span></span>

```vb
Private Function FindFirstNonDigit(s As String) As Integer
    For i = 0 To s.Length - 1
        If Not Char.IsDigit(s(i)) Then Return i
    Next
    Return -1
End Function
```

```csharp
private int FindFirstNonDigit(string s)
{
    for (int i = 0; i < s.Length; i++)
    {
        if (!Char.IsDigit(s[i])) return i;
    }
    return -1;
}
```

<span data-ttu-id="e3df4-235">Artık projeyi derleyip çalıştırabilmelisin.</span><span class="sxs-lookup"><span data-stu-id="e3df4-235">You should now be able to compile and run the project.</span></span> <span data-ttu-id="e3df4-236">Visual Basic'te, anahtar kelimeyi `Public` ' `Module1`ye eklediğinizden emin olun</span><span class="sxs-lookup"><span data-stu-id="e3df4-236">In Visual Basic, make sure that you added the `Public` keyword to `Module1`.</span></span> <span data-ttu-id="e3df4-237">Konsol penceresinde, "5+3" gibi bir ekleme işlemi yazın ve hesap makinesi sonuçları döndürür.</span><span class="sxs-lookup"><span data-stu-id="e3df4-237">In the console window, type an addition operation, such as "5+3", and the calculator returns the results.</span></span> <span data-ttu-id="e3df4-238">Başka bir operatör "İşlem Bulunamadı!"</span><span class="sxs-lookup"><span data-stu-id="e3df4-238">Any other operator results in the "Operation Not Found!"</span></span> <span data-ttu-id="e3df4-239">iletisi döndürmektedir.</span><span class="sxs-lookup"><span data-stu-id="e3df4-239">message.</span></span>

## <a name="extending-simplecalculator-using-a-new-class"></a><span data-ttu-id="e3df4-240">Yeni bir sınıf kullanarak SimpleCalculator'ı genişletme</span><span class="sxs-lookup"><span data-stu-id="e3df4-240">Extending SimpleCalculator using a new class</span></span>

<span data-ttu-id="e3df4-241">Artık hesap makinesi çalıştığıiçin, yeni bir işlem eklemek kolaydır.</span><span class="sxs-lookup"><span data-stu-id="e3df4-241">Now that the calculator works, adding a new operation is easy.</span></span> <span data-ttu-id="e3df4-242">Modüle veya `SimpleCalculator` ad alanına aşağıdaki sınıfı ekleyin:</span><span class="sxs-lookup"><span data-stu-id="e3df4-242">Add the following class to the module or `SimpleCalculator` namespace:</span></span>

```vb
<Export(GetType(IOperation))>
<ExportMetadata("Symbol", "-"c)>
Public Class Subtract
    Implements IOperation

    Public Function Operate(left As Integer, right As Integer) As Integer Implements IOperation.Operate
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

<span data-ttu-id="e3df4-243">Projeyi derle ve çalıştır.</span><span class="sxs-lookup"><span data-stu-id="e3df4-243">Compile and run the project.</span></span> <span data-ttu-id="e3df4-244">"5-3" gibi bir çıkarma işlemi yazın.</span><span class="sxs-lookup"><span data-stu-id="e3df4-244">Type a subtraction operation, such as "5-3".</span></span> <span data-ttu-id="e3df4-245">Hesap makinesi artık çıkarmanın yanı sıra eklemeyi de destekler.</span><span class="sxs-lookup"><span data-stu-id="e3df4-245">The calculator now supports subtraction as well as addition.</span></span>

## <a name="extending-simplecalculator-using-a-new-assembly"></a><span data-ttu-id="e3df4-246">Yeni bir derleme kullanarak SimpleCalculator'ı genişletme</span><span class="sxs-lookup"><span data-stu-id="e3df4-246">Extending SimpleCalculator using a new assembly</span></span>

<span data-ttu-id="e3df4-247">Kaynak koduna sınıf eklemek yeterince basittir, ancak MEF, bir uygulamanın kendi kaynağının dışına parçalar için bakma olanağı sağlar.</span><span class="sxs-lookup"><span data-stu-id="e3df4-247">Adding classes to the source code is simple enough, but MEF provides the ability to look outside an application’s own source for parts.</span></span> <span data-ttu-id="e3df4-248">Bunu göstermek için, bir dizin aramak için SimpleCalculator değiştirmek gerekir, yanı sıra kendi <xref:System.ComponentModel.Composition.Hosting.DirectoryCatalog>derleme, parçalar için, ekleyerek .</span><span class="sxs-lookup"><span data-stu-id="e3df4-248">To demonstrate this, you will need to modify SimpleCalculator to search a directory, as well as its own assembly, for parts, by adding a <xref:System.ComponentModel.Composition.Hosting.DirectoryCatalog>.</span></span>

<span data-ttu-id="e3df4-249">SimpleCalculator projesine `Extensions` yeni bir dizin ekleyin.</span><span class="sxs-lookup"><span data-stu-id="e3df4-249">Add a new directory named `Extensions` to the SimpleCalculator project.</span></span> <span data-ttu-id="e3df4-250">Çözüm düzeyinde değil, proje düzeyinde eklediğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="e3df4-250">Make sure to add it at the project level, and not at the solution level.</span></span> <span data-ttu-id="e3df4-251">Ardından çözüme yeni bir Sınıf Kitaplığı projesi ekleyin. `ExtendedOperations`</span><span class="sxs-lookup"><span data-stu-id="e3df4-251">Then add a new Class Library project to the solution, named `ExtendedOperations`.</span></span> <span data-ttu-id="e3df4-252">Yeni proje ayrı bir derleme halinde derlenecek.</span><span class="sxs-lookup"><span data-stu-id="e3df4-252">The new project will compile into a separate assembly.</span></span>

<span data-ttu-id="e3df4-253">Genişletilmiş İşlemler projesi için Proje Özellikleri Tasarımcısı'nı açın ve **Derleme** veya **Oluştur** sekmesini tıklatın. SimpleCalculator proje dizinindeki Uzantılar dizinine işaret etmek için **Çıktı Veya** Çıktı **yolunu** değiştirin (*... \SimpleCalculator\Uzantılar).\\*</span><span class="sxs-lookup"><span data-stu-id="e3df4-253">Open the Project Properties Designer for the ExtendedOperations project and click the **Compile** or **Build** tab. Change the **Build output path** or **Output path** to point to the Extensions directory in the SimpleCalculator project directory (*..\SimpleCalculator\Extensions\\*).</span></span>

 <span data-ttu-id="e3df4-254">*Module1.vb* veya *Program.cs'* de, `Program` oluşturucuya aşağıdaki satırı ekleyin:</span><span class="sxs-lookup"><span data-stu-id="e3df4-254">In *Module1.vb* or *Program.cs*, add the following line to the `Program` constructor:</span></span>

```vb
catalog.Catalogs.Add(New DirectoryCatalog("C:\SimpleCalculator\SimpleCalculator\Extensions"))
```

```csharp
catalog.Catalogs.Add(new DirectoryCatalog("C:\\SimpleCalculator\\SimpleCalculator\\Extensions"));
```

<span data-ttu-id="e3df4-255">Örnek yolu Uzantılar dizininize giden yolile değiştirin.</span><span class="sxs-lookup"><span data-stu-id="e3df4-255">Replace the example path with the path to your Extensions directory.</span></span> <span data-ttu-id="e3df4-256">(Bu mutlak yol sadece hata ayıklama amacıyladır.</span><span class="sxs-lookup"><span data-stu-id="e3df4-256">(This absolute path is for debugging purposes only.</span></span> <span data-ttu-id="e3df4-257">Bir üretim uygulamasında, göreli bir yol kullanırsınız.) Şimdi <xref:System.ComponentModel.Composition.Hosting.DirectoryCatalog> kompozisyon kapsayıcısına Uzantılar dizininde bulunan herhangi bir parça eklenecektir.</span><span class="sxs-lookup"><span data-stu-id="e3df4-257">In a production application, you would use a relative path.) The <xref:System.ComponentModel.Composition.Hosting.DirectoryCatalog> will now add any parts found in any assemblies in the Extensions directory to the composition container.</span></span>

<span data-ttu-id="e3df4-258">Genişletilmiş Operasyonlar projesinde, SimpleCalculator ve System.ComponentModel.Composition'a göndermeler ekleyin.</span><span class="sxs-lookup"><span data-stu-id="e3df4-258">In the ExtendedOperations project, add references to SimpleCalculator and System.ComponentModel.Composition.</span></span> <span data-ttu-id="e3df4-259">ExtendedOperations sınıf dosyasında System.ComponentModel.Composition için bir `Imports` açıklama veya deyim `using` ekleyin.</span><span class="sxs-lookup"><span data-stu-id="e3df4-259">In the ExtendedOperations class file, add an `Imports` or a `using` statement for System.ComponentModel.Composition.</span></span> <span data-ttu-id="e3df4-260">Visual Basic'te SimpleCalculator için bir `Imports` deyim de ekleyin.</span><span class="sxs-lookup"><span data-stu-id="e3df4-260">In Visual Basic, also add an `Imports` statement for SimpleCalculator.</span></span> <span data-ttu-id="e3df4-261">Ardından ExtendedOperations sınıf dosyasına aşağıdaki sınıfı ekleyin:</span><span class="sxs-lookup"><span data-stu-id="e3df4-261">Then add the following class to the ExtendedOperations class file:</span></span>

```vb
<Export(GetType(SimpleCalculator.IOperation))>
<ExportMetadata("Symbol", "%"c)>
Public Class Modulo
    Implements IOperation

    Public Function Operate(left As Integer, right As Integer) As Integer Implements IOperation.Operate
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

<span data-ttu-id="e3df4-262">Sözleşmenin eşleşebilmesi için özniteliğin <xref:System.ComponentModel.Composition.ExportAttribute> . <xref:System.ComponentModel.Composition.ImportAttribute></span><span class="sxs-lookup"><span data-stu-id="e3df4-262">Note that in order for the contract to match, the <xref:System.ComponentModel.Composition.ExportAttribute> attribute must have the same type as the <xref:System.ComponentModel.Composition.ImportAttribute>.</span></span>

<span data-ttu-id="e3df4-263">Projeyi derle ve çalıştır.</span><span class="sxs-lookup"><span data-stu-id="e3df4-263">Compile and run the project.</span></span> <span data-ttu-id="e3df4-264">Yeni Mod test edin (%) Işleç.</span><span class="sxs-lookup"><span data-stu-id="e3df4-264">Test the new Mod (%) operator.</span></span>

## <a name="conclusion"></a><span data-ttu-id="e3df4-265">Sonuç</span><span class="sxs-lookup"><span data-stu-id="e3df4-265">Conclusion</span></span>

<span data-ttu-id="e3df4-266">Bu konu MEF'in temel kavramlarını kapsamaktadır.</span><span class="sxs-lookup"><span data-stu-id="e3df4-266">This topic covered the basic concepts of MEF.</span></span>

- <span data-ttu-id="e3df4-267">Parçalar, kataloglar ve kompozisyon konteyneri</span><span class="sxs-lookup"><span data-stu-id="e3df4-267">Parts, catalogs, and the composition container</span></span>

     <span data-ttu-id="e3df4-268">Parçalar ve bileşim konteyneri bir MEF uygulamasının temel yapı taşlarıdır.</span><span class="sxs-lookup"><span data-stu-id="e3df4-268">Parts and the composition container are the basic building blocks of a MEF application.</span></span> <span data-ttu-id="e3df4-269">Bir parça, kendisine kadar ve kendisi de dahil olmak üzere bir değer içe aktaran veya dışa aktaran herhangi bir nesnedir.</span><span class="sxs-lookup"><span data-stu-id="e3df4-269">A part is any object that imports or exports a value, up to and including itself.</span></span> <span data-ttu-id="e3df4-270">Katalog, belirli bir kaynaktan parçalar koleksiyonu sağlar.</span><span class="sxs-lookup"><span data-stu-id="e3df4-270">A catalog provides a collection of parts from a particular source.</span></span> <span data-ttu-id="e3df4-271">Kompozisyon kapsayıcıkompozisyon gerçekleştirmek için bir katalog tarafından sağlanan parçaları kullanır, dışa aktarımbağlama.</span><span class="sxs-lookup"><span data-stu-id="e3df4-271">The composition container uses the parts provided by a catalog to perform composition, the binding of imports to exports.</span></span>

- <span data-ttu-id="e3df4-272">İthalat ve ihracat</span><span class="sxs-lookup"><span data-stu-id="e3df4-272">Imports and exports</span></span>

     <span data-ttu-id="e3df4-273">İthalat ve dışaaklar, bileşenlerin iletişim kurma yoludur.</span><span class="sxs-lookup"><span data-stu-id="e3df4-273">Imports and exports are the way by which components communicate.</span></span> <span data-ttu-id="e3df4-274">Bir alma ile bileşen, belirli bir değer veya nesne için bir ihtiyaç belirtir ve bir dışa aktarma ile bir değerin kullanılabilirliğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="e3df4-274">With an import, the component specifies a need for a particular value or object, and with an export it specifies the availability of a value.</span></span> <span data-ttu-id="e3df4-275">Her içe aktarım, sözleşmesi nin bir dışa aktarım listesiyle eşleşir.</span><span class="sxs-lookup"><span data-stu-id="e3df4-275">Each import is matched with a list of exports by way of its contract.</span></span>

## <a name="next-steps"></a><span data-ttu-id="e3df4-276">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="e3df4-276">Next steps</span></span>

<span data-ttu-id="e3df4-277">Bu örnek için tam kodu indirmek için [SimpleCalculator örneğine (Visual Basic)](https://docs.microsoft.com/samples/dotnet/samples/simple-calculator-vb/)bakın.</span><span class="sxs-lookup"><span data-stu-id="e3df4-277">To download the complete code for this example, see the [SimpleCalculator sample (Visual Basic)](https://docs.microsoft.com/samples/dotnet/samples/simple-calculator-vb/).</span></span>

 <span data-ttu-id="e3df4-278">Daha fazla bilgi ve kod örnekleri için [Yönetilen Genişletilebilirlik Çerçevesi'ne](https://github.com/MicrosoftArchive/mef)bakın.</span><span class="sxs-lookup"><span data-stu-id="e3df4-278">For more information and code examples, see [Managed Extensibility Framework](https://github.com/MicrosoftArchive/mef).</span></span> <span data-ttu-id="e3df4-279">MEF türlerinin listesi için <xref:System.ComponentModel.Composition?displayProperty=nameWithType> ad alanına bakın.</span><span class="sxs-lookup"><span data-stu-id="e3df4-279">For a list of the MEF types, see the <xref:System.ComponentModel.Composition?displayProperty=nameWithType> namespace.</span></span>
