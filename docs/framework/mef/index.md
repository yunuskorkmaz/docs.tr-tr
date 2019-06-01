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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6fa91b6f2866ba2dee6963d7258fe193ce058f61
ms.sourcegitcommit: 518e7634b86d3980ec7da5f8c308cc1054daedb7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/01/2019
ms.locfileid: "66457174"
---
# <a name="managed-extensibility-framework-mef"></a><span data-ttu-id="a3d7e-102">Managed Extensibility Framework (MEF)</span><span class="sxs-lookup"><span data-stu-id="a3d7e-102">Managed Extensibility Framework (MEF)</span></span>

<span data-ttu-id="a3d7e-103">Bu konu, .NET Framework 4'te sunulan Yönetilen Genişletilebilirlik Çerçevesi'ne genel bakış sağlar.</span><span class="sxs-lookup"><span data-stu-id="a3d7e-103">This topic provides an overview of the Managed Extensibility Framework that was introduced in the .NET Framework 4.</span></span>

<a name="what_is_mef"></a>
## <a name="what-is-mef"></a><span data-ttu-id="a3d7e-104">MEF nedir?</span><span class="sxs-lookup"><span data-stu-id="a3d7e-104">What is MEF?</span></span>

<span data-ttu-id="a3d7e-105">MEF ve Yönetilen Genişletilebilirlik Çerçevesi hafif Genişletilebilir uygulamalar oluşturmaya yönelik bir kitaplıktır.</span><span class="sxs-lookup"><span data-stu-id="a3d7e-105">The Managed Extensibility Framework or MEF is a library for creating lightweight, extensible applications.</span></span> <span data-ttu-id="a3d7e-106">Bulmak ve yapılandırma gerektirmeden uzantıları kullanmak, uygulama geliştiricilerinin sağlar.</span><span class="sxs-lookup"><span data-stu-id="a3d7e-106">It allows application developers to discover and use extensions with no configuration required.</span></span> <span data-ttu-id="a3d7e-107">Ayrıca, kolayca kod şifreleyebilir ve kırılgan sabit bağımlılıkları önlemek uzantı geliştiricileri sağlar.</span><span class="sxs-lookup"><span data-stu-id="a3d7e-107">It also lets extension developers easily encapsulate code and avoid fragile hard dependencies.</span></span> <span data-ttu-id="a3d7e-108">MEF değil yalnızca uygulama içinde ancak de uygulamalar arasında yeniden kullanılabilmeleri uzantılar sağlar.</span><span class="sxs-lookup"><span data-stu-id="a3d7e-108">MEF not only allows extensions to be reused within applications, but across applications as well.</span></span>

<a name="the_problem_of_extensibility"></a>
## <a name="the-problem-of-extensibility"></a><span data-ttu-id="a3d7e-109">Genişletilebilirlik sorunu</span><span class="sxs-lookup"><span data-stu-id="a3d7e-109">The Problem of Extensibility</span></span>
 <span data-ttu-id="a3d7e-110">Genişletilebilirlik için destek sağlayan bir büyük uygulama Mimarı olduğunuzu varsayalım.</span><span class="sxs-lookup"><span data-stu-id="a3d7e-110">Imagine that you are the architect of a large application that must provide support for extensibility.</span></span> <span data-ttu-id="a3d7e-111">Uygulamanızı daha küçük bileşenlerden büyük olasılıkla çok sayıda içermek zorundadır ve oluşturma ve bunları çalıştırmak için sorumludur.</span><span class="sxs-lookup"><span data-stu-id="a3d7e-111">Your application has to include a potentially large number of smaller components, and is responsible for creating and running them.</span></span>

 <span data-ttu-id="a3d7e-112">Sorun için en kolay yaklaşım, uygulamanızın kaynak kodunda olarak bileşenleri içerir ve doğrudan kodunuzdan çağırmaya sağlamaktır.</span><span class="sxs-lookup"><span data-stu-id="a3d7e-112">The simplest approach to the problem is to include the components as source code in your application, and call them directly from your code.</span></span> <span data-ttu-id="a3d7e-113">Bu, birkaç belirgin dezavantajları vardır.</span><span class="sxs-lookup"><span data-stu-id="a3d7e-113">This has a number of obvious drawbacks.</span></span> <span data-ttu-id="a3d7e-114">En önemlisi, örneğin, bir Web uygulaması, kabul edilebilir, ancak bir istemci uygulamasında çalışmaz bir kısıtlama kaynak kodunda değişiklik yapmadan yeni bileşenler ekleyemezsiniz.</span><span class="sxs-lookup"><span data-stu-id="a3d7e-114">Most importantly, you cannot add new components without modifying the source code, a restriction that might be acceptable in, for example, a Web application, but is unworkable in a client application.</span></span> <span data-ttu-id="a3d7e-115">Bunlar sizin erişmesine izin veremez aynı nedenden yanı sıra, üçüncü tarafların geliştirdiği eşit sorunlu, bileşenler için kaynak koduna erişim sahip.</span><span class="sxs-lookup"><span data-stu-id="a3d7e-115">Equally problematic, you may not have access to the source code for the components, because they might be developed by third parties, and for the same reason you cannot allow them to access yours.</span></span>

 <span data-ttu-id="a3d7e-116">Bir uzantı noktası ya da arabirim uygulama ve bileşenlerinin bağlantıyı kesmeye izin vermek için biraz daha karmaşık bir yaklaşım olacaktır.</span><span class="sxs-lookup"><span data-stu-id="a3d7e-116">A slightly more sophisticated approach would be to provide an extension point or interface, to permit decoupling between the application and its components.</span></span> <span data-ttu-id="a3d7e-117">Bu modelde, bir bileşen uygulayan bir arabirim ve uygulamanızla etkileşim sağlamak için bir API sağlayabilir.</span><span class="sxs-lookup"><span data-stu-id="a3d7e-117">Under this model, you might provide an interface that a component can implement, and an API to enable it to interact with your application.</span></span> <span data-ttu-id="a3d7e-118">Bu kaynak koduna erişim gerektiren sorununu çözer, ancak yine de zorluklara sahiptir.</span><span class="sxs-lookup"><span data-stu-id="a3d7e-118">This solves the problem of requiring source code access, but it still has its own difficulties.</span></span>

 <span data-ttu-id="a3d7e-119">Uygulama bileşenleri kendi bulmak için herhangi bir kapasite eksik olduğundan, bunu hala açıkça hangi bileşenlerin mevcut olduğu ve yüklenmesi gerektiğini söyledik gerekir.</span><span class="sxs-lookup"><span data-stu-id="a3d7e-119">Because the application lacks any capacity for discovering components on its own, it must still be explicitly told which components are available and should be loaded.</span></span> <span data-ttu-id="a3d7e-120">Bu genellikle, bir yapılandırma dosyasında açıkça kullanılabilir bileşenleri kaydederek da gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="a3d7e-120">This is typically accomplished by explicitly registering the available components in a configuration file.</span></span> <span data-ttu-id="a3d7e-121">Özellikle son kullanıcı ve olmayan bir güncelleştirme yapmak için beklenen geliştiriciye ise kullanıcıysa doğru Bunun anlamı bir bakım sorunu haline gelir.</span><span class="sxs-lookup"><span data-stu-id="a3d7e-121">This means that assuring that the components are correct becomes a maintenance issue, particularly if it is the end user and not the developer who is expected to do the updating.</span></span>

 <span data-ttu-id="a3d7e-122">Ayrıca, birbirleriyle etkileşime dışında uygulamanın kendisinin aracılığı tanımlanan kanallar iletişim kuramadığı bileşenlerdir.</span><span class="sxs-lookup"><span data-stu-id="a3d7e-122">In addition, components are incapable of communicating with one another, except through the rigidly defined channels of the application itself.</span></span> <span data-ttu-id="a3d7e-123">Uygulama Mimarı, belirli bir iletişim için gereken beklemiyorsa, genellikle mümkün değildir.</span><span class="sxs-lookup"><span data-stu-id="a3d7e-123">If the application architect has not anticipated the need for a particular communication, it is usually impossible.</span></span>

 <span data-ttu-id="a3d7e-124">Son olarak, bileşen geliştiricileri üzerinde uyguladıkları arabirimi hangi derlemeyi içeren sabit bir bağımlılık kabul etmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="a3d7e-124">Finally, the component developers must accept a hard dependency on what assembly contains the interface they implement.</span></span> <span data-ttu-id="a3d7e-125">Birden fazla uygulamada kullanılmak üzere bir bileşen zorlaştırır ve bir test çerçevesi bileşenleri için oluşturduğunuzda sorunları da oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a3d7e-125">This makes it difficult for a component to be used in more than one application, and can also create problems when you create a test framework for components.</span></span>

<a name="what_mef_provides"></a>
## <a name="what-mef-provides"></a><span data-ttu-id="a3d7e-126">MEF ne sağlar?</span><span class="sxs-lookup"><span data-stu-id="a3d7e-126">What MEF Provides</span></span>
 <span data-ttu-id="a3d7e-127">Kullanılabilir bileşenleri yerine bu açık kaydı MEF örtülü olarak bulmak için bir yol sağlar. aracılığıyla *bileşim*.</span><span class="sxs-lookup"><span data-stu-id="a3d7e-127">Instead of this explicit registration of available components, MEF provides a way to discover them implicitly, via *composition*.</span></span> <span data-ttu-id="a3d7e-128">Adlı bir MEF Bileşeni bir *bölümü*, bildirimli olarak her iki bağımlılıklarını belirtir (olarak bilinen *alır*) ve hangi özellikleri (olarak bilinen *aktarır*) kullanılabilir hale getirir.</span><span class="sxs-lookup"><span data-stu-id="a3d7e-128">A MEF component, called a *part*, declaratively specifies both its dependencies (known as *imports*) and what capabilities (known as *exports*) it makes available.</span></span> <span data-ttu-id="a3d7e-129">Bir bölümü oluşturulduğunda, MEF bileştirme altyapısı diğer bölümlerden kullanılabilir olan aktarmaları karşılar.</span><span class="sxs-lookup"><span data-stu-id="a3d7e-129">When a part is created, the MEF composition engine satisfies its imports with what is available from other parts.</span></span>

 <span data-ttu-id="a3d7e-130">Bu yaklaşım önceki bölümde açıklanan sorunları çözer.</span><span class="sxs-lookup"><span data-stu-id="a3d7e-130">This approach solves the problems discussed in the previous section.</span></span> <span data-ttu-id="a3d7e-131">MEF bölümleri yeteneklerini bildirimli olarak belirttiğinden, çalışma zamanında bulunabilir olmaları sabit kodlanmış başvuruları veya kırılgan yapılandırma dosyalarını olmadan parçalar kullanımını uygulama yapabilir anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="a3d7e-131">Because MEF parts declaratively specify their capabilities, they are discoverable at runtime, which means an application can make use of parts without either hard-coded references or fragile configuration files.</span></span> <span data-ttu-id="a3d7e-132">MEF uygulamaları bulmak ve bölümleri meta verilerine göre bunları örnekleme veya hatta kendi derlemeleri yükleme incelemek sağlar.</span><span class="sxs-lookup"><span data-stu-id="a3d7e-132">MEF allows applications to discover and examine parts by their metadata, without instantiating them or even loading their assemblies.</span></span> <span data-ttu-id="a3d7e-133">Sonuç olarak, dikkatli bir şekilde ne zaman ve nasıl uzantıları yüklenmesi gerektiğini belirtmek için gerek yoktur.</span><span class="sxs-lookup"><span data-stu-id="a3d7e-133">As a result, there is no need to carefully specify when and how extensions should be loaded.</span></span>

 <span data-ttu-id="a3d7e-134">Sağlanan aktarımlarından yanı sıra bir bölümünü başka parçalar tarafından doldurulacaktır tarafından içeri aktarılanlara belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a3d7e-134">In addition to its provided exports, a part can specify its imports, which will be filled by other parts.</span></span> <span data-ttu-id="a3d7e-135">Bu yapar arasında iletişimi değil yalnızca olası ancak kolay bölümleri ve kodu iyi bir şekilde düzenlenmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="a3d7e-135">This makes communication among parts not only possible, but easy, and allows for good factoring of code.</span></span> <span data-ttu-id="a3d7e-136">Örneğin, birçok bileşen için ortak hizmetler ayrı bir bölüm içinde ve kolayca değiştirilebilir veya değiştirildi.</span><span class="sxs-lookup"><span data-stu-id="a3d7e-136">For example, services common to many components can be factored into a separate part and easily modified or replaced.</span></span>

 <span data-ttu-id="a3d7e-137">MEF modelinin belirli uygulama derlemesine sabit hiçbir bağımlılığı gerektirdiğinden, uygulamadan uygulamaya yeniden kullanılabilmeleri uzantılar sağlar.</span><span class="sxs-lookup"><span data-stu-id="a3d7e-137">Because the MEF model requires no hard dependency on a particular application assembly, it allows extensions to be reused from application to application.</span></span> <span data-ttu-id="a3d7e-138">Bu ayrıca, uygulamayı uzantı bileşenlerini test etmek, bağımsız bir test bandı geliştirmek kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="a3d7e-138">This also makes it easy to develop a test harness, independent of the application, to test extension components.</span></span>

 <span data-ttu-id="a3d7e-139">MEF kullanılarak yazılan, Genişletilebilir bir uygulama uzantıları için uygulama hizmetleri kullanıma sunmak için uzantı bileşenleri tarafından da doldurulabilir ve ayrıca bildirebileceği bir içeri aktarır bildirir.</span><span class="sxs-lookup"><span data-stu-id="a3d7e-139">An extensible application written by using MEF declares an import that can be filled by extension components, and may also declare exports in order to expose application services to extensions.</span></span> <span data-ttu-id="a3d7e-140">Her bir uzantı bileşeni bir dışarı aktarma bildirir ve içeri aktarmaları da bildirebilir.</span><span class="sxs-lookup"><span data-stu-id="a3d7e-140">Each extension component declares an export, and may also declare imports.</span></span> <span data-ttu-id="a3d7e-141">Bu şekilde, uzantı bileşenlerinin kendileri otomatik olarak genişletilebilir.</span><span class="sxs-lookup"><span data-stu-id="a3d7e-141">In this way, extension components themselves are automatically extensible.</span></span>

<a name="where_is_mef_available"></a>
## <a name="where-is-mef-available"></a><span data-ttu-id="a3d7e-142">MEF nerede kullanılabilir?</span><span class="sxs-lookup"><span data-stu-id="a3d7e-142">Where Is MEF Available?</span></span>
 <span data-ttu-id="a3d7e-143">MEF, .NET Framework 4'ün önemli bir parçasıdır ve .NET Framework kullanılan her yerde kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="a3d7e-143">MEF is an integral part of the .NET Framework 4, and is available wherever the .NET Framework is used.</span></span> <span data-ttu-id="a3d7e-144">Windows Forms, WPF veya diğer herhangi bir teknoloji kullanıp kullanmayacağınızı veya ASP.NET kullanan sunucu uygulamaları, MEF istemci uygulamalarınızda kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a3d7e-144">You can use MEF in your client applications, whether they use Windows Forms, WPF, or any other technology, or in server applications that use ASP.NET.</span></span>

<a name="mef_and_maf"></a>
## <a name="mef-and-maf"></a><span data-ttu-id="a3d7e-145">MEF ve MAF</span><span class="sxs-lookup"><span data-stu-id="a3d7e-145">MEF and MAF</span></span>
 <span data-ttu-id="a3d7e-146">.NET Framework'ün önceki sürümlerini yönetilen eklenti Framework (yalıtmak ve uzantıları yönetmek uygulamalara izin vermek üzere tasarlanmış MAF), kullanıma sunuldu.</span><span class="sxs-lookup"><span data-stu-id="a3d7e-146">Previous versions of the .NET Framework introduced the Managed Add-in Framework (MAF), designed to allow applications to isolate and manage extensions.</span></span> <span data-ttu-id="a3d7e-147">Odak noktası, MAF uzantısı yalıtım ve yükleme ve kaldırma MEF'ın odak bulunabilirliği, genişletilebilirlik ve taşınabilirlik ederken derleme odaklanarak, MEF değerinden biraz daha üst düzey.</span><span class="sxs-lookup"><span data-stu-id="a3d7e-147">The focus of MAF is slightly higher-level than MEF, concentrating on extension isolation and assembly loading and unloading, while MEF's focus is on discoverability, extensibility, and portability.</span></span> <span data-ttu-id="a3d7e-148">İki çerçeveleri sorunsuz çalışma ve tek bir uygulama hem de yararlanabilir.</span><span class="sxs-lookup"><span data-stu-id="a3d7e-148">The two frameworks interoperate smoothly, and a single application can take advantage of both.</span></span>

<a name="simplecalculator_an_example_application"></a>

## <a name="simplecalculator-an-example-application"></a><span data-ttu-id="a3d7e-149">SimpleCalculator: Örnek bir uygulama</span><span class="sxs-lookup"><span data-stu-id="a3d7e-149">SimpleCalculator: An Example Application</span></span>

<span data-ttu-id="a3d7e-150">MEF neler yapabileceğinizi görmek için en basit yolu, basit bir MEF uygulaması oluşturmaktır.</span><span class="sxs-lookup"><span data-stu-id="a3d7e-150">The simplest way to see what MEF can do is to build a simple MEF application.</span></span> <span data-ttu-id="a3d7e-151">Bu örnekte çok basit hesap makinesi SimpleCalculator adlı oluşturun.</span><span class="sxs-lookup"><span data-stu-id="a3d7e-151">In this example, you build a very simple calculator named SimpleCalculator.</span></span> <span data-ttu-id="a3d7e-152">"5 + 3" biçiminde temel aritmetik komutları kabul eden bir konsol uygulaması oluşturmak için SimpleCalculator amacı olan veya "6-2" ve doğru yanıtları döndürür.</span><span class="sxs-lookup"><span data-stu-id="a3d7e-152">The goal of SimpleCalculator is to create a console application that accepts basic arithmetic commands, in the form "5+3" or "6-2", and returns the correct answers.</span></span> <span data-ttu-id="a3d7e-153">MEF kullanarak, uygulamanın kodunu değiştirmeden yeni işleç eklemek mümkün olacaktır.</span><span class="sxs-lookup"><span data-stu-id="a3d7e-153">Using MEF, you'll be able to add new operators without changing the application code.</span></span>

<span data-ttu-id="a3d7e-154">Bu örnek için tam kod indirmek için bkz [SimpleCalculator örnek](https://code.msdn.microsoft.com/windowsdesktop/Simple-Calculator-MEF-1152654e).</span><span class="sxs-lookup"><span data-stu-id="a3d7e-154">To download the complete code for this example, see the [SimpleCalculator sample](https://code.msdn.microsoft.com/windowsdesktop/Simple-Calculator-MEF-1152654e).</span></span>

> [!NOTE]
> <span data-ttu-id="a3d7e-155">MEF sözdizimi ve kavramları göstermek için yerine mutlaka gerçekçi bir senaryo için kullanımını sağlamak için SimpleCalculator amacı budur.</span><span class="sxs-lookup"><span data-stu-id="a3d7e-155">The purpose of SimpleCalculator is to demonstrate the concepts and syntax of MEF, rather than to necessarily provide a realistic scenario for its use.</span></span> <span data-ttu-id="a3d7e-156">Birçok avantaj elde edecektir MEF gücünü en iyi uygulamaları SimpleCalculator daha karmaşıktır.</span><span class="sxs-lookup"><span data-stu-id="a3d7e-156">Many of the applications that would benefit most from the power of MEF are more complex than SimpleCalculator.</span></span> <span data-ttu-id="a3d7e-157">Daha kapsamlı örnekler için bkz: [Managed Extensibility Framework](https://github.com/MicrosoftArchive/mef) GitHub üzerinde.</span><span class="sxs-lookup"><span data-stu-id="a3d7e-157">For more extensive examples, see the [Managed Extensibility Framework](https://github.com/MicrosoftArchive/mef) on GitHub.</span></span>

- <span data-ttu-id="a3d7e-158">Başlamak için Visual Studio'da yeni bir konsol uygulaması projesi oluşturun ve adlandırın `SimpleCalculator`.</span><span class="sxs-lookup"><span data-stu-id="a3d7e-158">To start, in Visual Studio, create a new Console Application project and name it `SimpleCalculator`.</span></span>

- <span data-ttu-id="a3d7e-159">MEF bulunduğu System.ComponentModel.Composition derlemesine bir başvuru ekleyin.</span><span class="sxs-lookup"><span data-stu-id="a3d7e-159">Add a reference to the System.ComponentModel.Composition assembly, where MEF resides.</span></span>

- <span data-ttu-id="a3d7e-160">Module1.vb veya program.cs'i açın ve eklemek `Imports` veya `using` System.ComponentModel.Composition ve System.ComponentModel.Composition.Hosting deyimleri.</span><span class="sxs-lookup"><span data-stu-id="a3d7e-160">Open Module1.vb or Program.cs and add `Imports` or `using` statements for System.ComponentModel.Composition and System.ComponentModel.Composition.Hosting.</span></span> <span data-ttu-id="a3d7e-161">Bu iki ad alanlarında, Genişletilebilir bir uygulama geliştirmek için ihtiyacınız olacak MEF türler bulunur.</span><span class="sxs-lookup"><span data-stu-id="a3d7e-161">These two namespaces contain MEF types you will need to develop an extensible application.</span></span>

- <span data-ttu-id="a3d7e-162">Visual Basic kullanıyorsanız, ekleyin `Public` anahtar sözcüğü bildiren satırına `Module1` modülü.</span><span class="sxs-lookup"><span data-stu-id="a3d7e-162">If you're using Visual Basic, add the `Public` keyword to the line that declares the `Module1` module.</span></span>

<a name="composition_container_and_catalogs"></a>

## <a name="composition-container-and-catalogs"></a><span data-ttu-id="a3d7e-163">Kapsayıcının ve katalogları</span><span class="sxs-lookup"><span data-stu-id="a3d7e-163">Composition Container and Catalogs</span></span>

<span data-ttu-id="a3d7e-164">MEF bileşim modeli temel *kapsayıcının*, kullanılabilir tüm parçaları içerir ve oluşturma işlemini gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="a3d7e-164">The core of the MEF composition model is the *composition container*, which contains all the parts available and performs composition.</span></span> <span data-ttu-id="a3d7e-165">Birleşim eşleşen dışarı aktarır, çalışıyor.</span><span class="sxs-lookup"><span data-stu-id="a3d7e-165">Composition is the matching up of imports to exports.</span></span> <span data-ttu-id="a3d7e-166">Kapsayıcının en yaygın türü <xref:System.ComponentModel.Composition.Hosting.CompositionContainer>, ve bu SimpleCalculator için kullanacaksınız.</span><span class="sxs-lookup"><span data-stu-id="a3d7e-166">The most common type of composition container is <xref:System.ComponentModel.Composition.Hosting.CompositionContainer>, and you'll use this for SimpleCalculator.</span></span>

<span data-ttu-id="a3d7e-167">Visual Basic kullanıyorsanız Module1.vb adlı bir ortak Sınıf Ekle `Program`.</span><span class="sxs-lookup"><span data-stu-id="a3d7e-167">If you're using Visual Basic, in Module1.vb, add a public class named `Program`.</span></span>

<span data-ttu-id="a3d7e-168">Aşağıdaki satırı ekleyin `Program` Module1.vb veya Program.cs sınıfında:</span><span class="sxs-lookup"><span data-stu-id="a3d7e-168">Add the following line to the `Program` class in Module1.vb or Program.cs:</span></span>

```vb
Dim _container As CompositionContainer
```

```csharp
private CompositionContainer _container;
```

<span data-ttu-id="a3d7e-169">Bunun için bileşim kapsayıcılar kullanılabilir bölümleri bulmak için kullanır bir *Kataloğu*.</span><span class="sxs-lookup"><span data-stu-id="a3d7e-169">In order to discover the parts available to it, the composition containers makes use of a *catalog*.</span></span> <span data-ttu-id="a3d7e-170">Katalog bölümleri bazı kaynaklardaki kullanılabilir hale getiren bir nesnedir.</span><span class="sxs-lookup"><span data-stu-id="a3d7e-170">A catalog is an object that makes available parts discovered from some source.</span></span> <span data-ttu-id="a3d7e-171">MEF bölümleri sağlanan türü, bir derleme veya dizin keşfetmenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="a3d7e-171">MEF provides catalogs to discover parts from a provided type, an assembly, or a directory.</span></span> <span data-ttu-id="a3d7e-172">Uygulama geliştiricileri, bir Web hizmeti gibi diğer kaynaklardan kısımlarını keşfetmek için yeni katalog kolayca oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a3d7e-172">Application developers can easily create new catalogs to discover parts from other sources, such as a Web service.</span></span>

<span data-ttu-id="a3d7e-173">Aşağıdaki oluşturucuyu ekleyin `Program` sınıfı:</span><span class="sxs-lookup"><span data-stu-id="a3d7e-173">Add the following constructor to the `Program` class:</span></span>

```vb
Public Sub New()
    'An aggregate catalog that combines multiple catalogs
     Dim catalog = New AggregateCatalog()

    'Adds all the parts found in the same assembly as the Program class
    catalog.Catalogs.Add(New AssemblyCatalog(GetType(Program).Assembly))

    'Create the CompositionContainer with the parts in the catalog
    _container = New CompositionContainer(catalog)

    'Fill the imports of this object
    Try
        _container.ComposeParts(Me)
    Catch ex As Exception
        Console.WriteLine(ex.ToString)
    End Try
End Sub
```

```csharp
private Program()
{
    //An aggregate catalog that combines multiple catalogs
    var catalog = new AggregateCatalog();
    //Adds all the parts found in the same assembly as the Program class
    catalog.Catalogs.Add(new AssemblyCatalog(typeof(Program).Assembly));

    //Create the CompositionContainer with the parts in the catalog
    _container = new CompositionContainer(catalog);

    //Fill the imports of this object
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

<span data-ttu-id="a3d7e-174">Çağrı <xref:System.ComponentModel.Composition.AttributedModelServices.ComposeParts%2A> geçerli örneği bu durumda, bölümleri belirli bir dizi oluşturmak için kapsayıcının söyler `Program`.</span><span class="sxs-lookup"><span data-stu-id="a3d7e-174">The call to <xref:System.ComponentModel.Composition.AttributedModelServices.ComposeParts%2A> tells the composition container to compose a specific set of parts, in this case the current instance of `Program`.</span></span> <span data-ttu-id="a3d7e-175">Bu noktada, ancak hiçbir şey, beri olacağını `Program` aktarımlara doldurmak için sahip değildir.</span><span class="sxs-lookup"><span data-stu-id="a3d7e-175">At this point, however, nothing will happen, since `Program` has no imports to fill.</span></span>

<a name="imports_and_exports_with_attributes"></a>
## <a name="imports-and-exports-with-attributes"></a><span data-ttu-id="a3d7e-176">İçeri ve dışarı aktarmalar özniteliklerine sahip</span><span class="sxs-lookup"><span data-stu-id="a3d7e-176">Imports and Exports with Attributes</span></span>
 <span data-ttu-id="a3d7e-177">İlk olarak `Program` hesap makinesi içeri aktarın.</span><span class="sxs-lookup"><span data-stu-id="a3d7e-177">First, you have `Program` import a calculator.</span></span> <span data-ttu-id="a3d7e-178">Bu kullanıcı ayrımı gibi konsol girdi ve çıktı olacak arabirimi konuları sağlar `Program`, hesaplayıcı mantığından.</span><span class="sxs-lookup"><span data-stu-id="a3d7e-178">This allows the separation of user interface concerns, such as the console input and output that will go into `Program`, from the logic of the calculator.</span></span>

 <span data-ttu-id="a3d7e-179">Aşağıdaki kodu ekleyin `Program` sınıfı:</span><span class="sxs-lookup"><span data-stu-id="a3d7e-179">Add the following code to the `Program` class:</span></span>

```vb
<Import(GetType(ICalculator))>
Public Property calculator As ICalculator
```

```csharp
[Import(typeof(ICalculator))]
public ICalculator calculator;
```

 <span data-ttu-id="a3d7e-180">Dikkat bildirimi `calculator` nesne olağan dışı değildir ancak ile donatılmış <xref:System.ComponentModel.Composition.ImportAttribute> özniteliği.</span><span class="sxs-lookup"><span data-stu-id="a3d7e-180">Notice that the declaration of the `calculator` object is not unusual, but that it is decorated with the <xref:System.ComponentModel.Composition.ImportAttribute> attribute.</span></span> <span data-ttu-id="a3d7e-181">Bu öznitelik bir bir içe aktarım olarak bildirir; diğer bir deyişle, bir nesne oluşturulduğunda bileşim motoru tarafından doldurulur.</span><span class="sxs-lookup"><span data-stu-id="a3d7e-181">This attribute declares something to be an import; that is, it will be filled by the composition engine when the object is composed.</span></span>

 <span data-ttu-id="a3d7e-182">Her bir içe aktarması yok bir *sözleşme*, eşleştiği ile hangi dışarı belirler.</span><span class="sxs-lookup"><span data-stu-id="a3d7e-182">Every import has a *contract*, which determines what exports it will be matched with.</span></span> <span data-ttu-id="a3d7e-183">Sözleşmeyi açıkça belirtilen bir dize olabilir ve bu durumda arabirimi belirli bir türden MEF tarafından otomatik olarak da oluşturulabilir `ICalculator`.</span><span class="sxs-lookup"><span data-stu-id="a3d7e-183">The contract can be an explicitly specified string, or it can be automatically generated by MEF from a given type, in this case the interface `ICalculator`.</span></span> <span data-ttu-id="a3d7e-184">Eşleşen bir anlaşma ile bildirilen herhangi bir dışarı aktarma, bu içeri aktarma karşılar.</span><span class="sxs-lookup"><span data-stu-id="a3d7e-184">Any export declared with a matching contract will fulfill this import.</span></span> <span data-ttu-id="a3d7e-185">Türü unutmayın `calculator` nesnedir, aslında `ICalculator`, bu gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="a3d7e-185">Note that while the type of the `calculator` object is in fact `ICalculator`, this is not required.</span></span> <span data-ttu-id="a3d7e-186">Sözleşmenin alma nesnenin türünden bağımsızdır.</span><span class="sxs-lookup"><span data-stu-id="a3d7e-186">The contract is independent from the type of the importing object.</span></span> <span data-ttu-id="a3d7e-187">(Bu durumda, dışlamayı `typeof(ICalculator)`.</span><span class="sxs-lookup"><span data-stu-id="a3d7e-187">(In this case, you could leave out the `typeof(ICalculator)`.</span></span> <span data-ttu-id="a3d7e-188">MEF otomatik olarak içeri aktarma türüne açıkça belirtmediğiniz sürece alan sözleşme varsayar.)</span><span class="sxs-lookup"><span data-stu-id="a3d7e-188">MEF will automatically assume the contract to be based on the type of the import unless you specify it explicitly.)</span></span>

 <span data-ttu-id="a3d7e-189">Bu çok basit bir arabirim modüle ekleyin veya `SimpleCalculator` ad alanı:</span><span class="sxs-lookup"><span data-stu-id="a3d7e-189">Add this very simple interface to the module or `SimpleCalculator` namespace:</span></span>

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

 <span data-ttu-id="a3d7e-190">Tanımladığınız göre `ICalculator`, onu uygulayan bir sınıf gerekir.</span><span class="sxs-lookup"><span data-stu-id="a3d7e-190">Now that you have defined `ICalculator`, you need a class that implements it.</span></span> <span data-ttu-id="a3d7e-191">Aşağıdaki sınıf modüle ekleyin veya `SimpleCalculator` ad alanı:</span><span class="sxs-lookup"><span data-stu-id="a3d7e-191">Add the following class to the module or `SimpleCalculator` namespace:</span></span>

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

 <span data-ttu-id="a3d7e-192">Alma eşleşen dışarı aktarma işte `Program`.</span><span class="sxs-lookup"><span data-stu-id="a3d7e-192">Here is the export that will match the import in `Program`.</span></span> <span data-ttu-id="a3d7e-193">İçeri aktarma eşleşecek şekilde dışarı aktarma, dışarı aktarma aynı anlaşmaya olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="a3d7e-193">In order for the export to match the import, the export must have the same contract.</span></span> <span data-ttu-id="a3d7e-194">Bir sözleşme çerçevesinde verme temel alarak `typeof(MySimpleCalculator)` bir uyumsuzluk oluşturur ve içeri aktarma olmayan doldurulur; sözleşmenin tam olarak eşleşmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="a3d7e-194">Exporting under a contract based on `typeof(MySimpleCalculator)` would produce a mismatch, and the import would not be filled; the contract needs to match exactly.</span></span>

 <span data-ttu-id="a3d7e-195">Bu derlemede, kullanılabilir tüm bölümleri içeren kapsayıcının doldurulur beri `MySimpleCalculator` bölümünü, kullanıma sunulacaktır.</span><span class="sxs-lookup"><span data-stu-id="a3d7e-195">Since the composition container will be populated with all the parts available in this assembly, the `MySimpleCalculator` part will be available.</span></span> <span data-ttu-id="a3d7e-196">Zaman Oluşturucusu `Program` üzerinde birleştirme gerçekleştirir `Program` nesnesi, içeri aktarma ile doldurulur bir `MySimpleCalculator` bu amaç için oluşturulan nesne.</span><span class="sxs-lookup"><span data-stu-id="a3d7e-196">When the constructor for `Program` performs composition on the `Program` object, its import will be filled with a `MySimpleCalculator` object, which will be created for that purpose.</span></span>

 <span data-ttu-id="a3d7e-197">Kullanıcı arabirim katmanı (`Program`) başka bir şey bilmek gerekmez.</span><span class="sxs-lookup"><span data-stu-id="a3d7e-197">The user interface layer (`Program`) does not need to know anything else.</span></span> <span data-ttu-id="a3d7e-198">Bu nedenle kullanıcı arabirimi mantığı, rest doldurabilirsiniz `Main` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="a3d7e-198">You can therefore fill in the rest of the user interface logic in the `Main` method.</span></span>

 <span data-ttu-id="a3d7e-199">Aşağıdaki kodu ekleyin `Main` yöntemi:</span><span class="sxs-lookup"><span data-stu-id="a3d7e-199">Add the following code to the `Main` method:</span></span>

```vb
Sub Main()
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
    Program p = new Program(); //Composition is performed in the constructor
    String s;
    Console.WriteLine("Enter Command:");
    while (true)
    {
        s = Console.ReadLine();
        Console.WriteLine(p.calculator.Calculate(s));
    }
}
```

 <span data-ttu-id="a3d7e-200">Bu kod yalnızca bir satır girişi ve iletileriniz okur `Calculate` işlevi `ICalculator` sonucuna konsola geri yazar.</span><span class="sxs-lookup"><span data-stu-id="a3d7e-200">This code simply reads a line of input and calls the `Calculate` function of `ICalculator` on the result, which it writes back to the console.</span></span> <span data-ttu-id="a3d7e-201">İhtiyacınız olan tüm kod `Program`.</span><span class="sxs-lookup"><span data-stu-id="a3d7e-201">That is all the code you need in `Program`.</span></span> <span data-ttu-id="a3d7e-202">İşin tüm rest bölümlerinde gerçekleşir.</span><span class="sxs-lookup"><span data-stu-id="a3d7e-202">All the rest of the work will happen in the parts.</span></span>

<a name="further_imports_and_importmany"></a>
## <a name="further-imports-and-importmany"></a><span data-ttu-id="a3d7e-203">İçeri aktarmalar ve ImportMany daha iyi</span><span class="sxs-lookup"><span data-stu-id="a3d7e-203">Further Imports and ImportMany</span></span>
 <span data-ttu-id="a3d7e-204">SimpleCalculator Genişletilebilir olmak üzere, bu işlemlerin bir listesini almak gerekir.</span><span class="sxs-lookup"><span data-stu-id="a3d7e-204">In order for SimpleCalculator to be extensible, it needs to import a list of operations.</span></span> <span data-ttu-id="a3d7e-205">Sıradan <xref:System.ComponentModel.Composition.ImportAttribute> özniteliği bir ve yalnızca bir tarafından doldurulur <xref:System.ComponentModel.Composition.ExportAttribute>.</span><span class="sxs-lookup"><span data-stu-id="a3d7e-205">An ordinary <xref:System.ComponentModel.Composition.ImportAttribute> attribute is filled by one and only one <xref:System.ComponentModel.Composition.ExportAttribute>.</span></span> <span data-ttu-id="a3d7e-206">Bileşim motoru, birden fazla varsa bir hata oluşturur.</span><span class="sxs-lookup"><span data-stu-id="a3d7e-206">If more than one is available, the composition engine produces an error.</span></span> <span data-ttu-id="a3d7e-207">Herhangi bir sayıda dışarı aktarmaları doldurulmuş bir içeri aktarma oluşturmak için kullanabileceğiniz <xref:System.ComponentModel.Composition.ImportManyAttribute> özniteliği.</span><span class="sxs-lookup"><span data-stu-id="a3d7e-207">To create an import that can be filled by any number of exports, you can use the <xref:System.ComponentModel.Composition.ImportManyAttribute> attribute.</span></span>

 <span data-ttu-id="a3d7e-208">Aşağıdaki işlemleri özelliği Ekle `MySimpleCalculator` sınıfı:</span><span class="sxs-lookup"><span data-stu-id="a3d7e-208">Add the following operations property to the `MySimpleCalculator` class:</span></span>

```vb
<ImportMany()>
Public Property operations As IEnumerable(Of Lazy(Of IOperation, IOperationData))
```

```csharp
[ImportMany]
IEnumerable<Lazy<IOperation, IOperationData>> operations;
```

 <span data-ttu-id="a3d7e-209"><xref:System.Lazy%602> bir türü MEF dışarı aktarma dolaylı başvuruları tutmak için tarafından sağlanır.</span><span class="sxs-lookup"><span data-stu-id="a3d7e-209"><xref:System.Lazy%602> is a type provided by MEF to hold indirect references to exports.</span></span> <span data-ttu-id="a3d7e-210">Burada, dışarı aktarılan nesnenin kendisinin yanı sıra, ayrıca Al *meta verileri dışarı aktarma*, ya da dışarı aktarılan nesnenin açıklayan bilgiler.</span><span class="sxs-lookup"><span data-stu-id="a3d7e-210">Here, in addition to the exported object itself, you also get *export metadata*, or information that describes the exported object.</span></span> <span data-ttu-id="a3d7e-211">Her <xref:System.Lazy%602> içeren bir `IOperation` gerçek bir işlemi temsil eden bir nesne ve bir `IOperationData` meta verilerini temsil eden nesne.</span><span class="sxs-lookup"><span data-stu-id="a3d7e-211">Each <xref:System.Lazy%602> contains an `IOperation` object, representing an actual operation, and an `IOperationData` object, representing its metadata.</span></span>

 <span data-ttu-id="a3d7e-212">Aşağıdaki basit arabirimleri modüle ekleyin veya `SimpleCalculator` ad alanı:</span><span class="sxs-lookup"><span data-stu-id="a3d7e-212">Add the following simple interfaces to the module or `SimpleCalculator` namespace:</span></span>

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

 <span data-ttu-id="a3d7e-213">Bu durumda, her işlem için meta veriler gibi bu işlemi temsil eden semboldür +, -, \* ve benzeri.</span><span class="sxs-lookup"><span data-stu-id="a3d7e-213">In this case, the metadata for each operation is the symbol that represents that operation, such as +, -, \*, and so on.</span></span> <span data-ttu-id="a3d7e-214">Toplama işlemi kullanılabilir yapmak için aşağıdaki sınıf modüle ekleyin veya `SimpleCalculator` ad alanı:</span><span class="sxs-lookup"><span data-stu-id="a3d7e-214">To make the addition operation available, add the following class to the module or `SimpleCalculator` namespace:</span></span>

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

 <span data-ttu-id="a3d7e-215"><xref:System.ComponentModel.Composition.ExportAttribute> Önce yaptığınız gibi işlevleri özniteliği.</span><span class="sxs-lookup"><span data-stu-id="a3d7e-215">The <xref:System.ComponentModel.Composition.ExportAttribute> attribute functions as it did before.</span></span> <span data-ttu-id="a3d7e-216"><xref:System.ComponentModel.Composition.ExportMetadataAttribute> Özniteliği bu dışarı aktarma için bir ad-değer çiftinin biçiminde meta veriler ekler.</span><span class="sxs-lookup"><span data-stu-id="a3d7e-216">The <xref:System.ComponentModel.Composition.ExportMetadataAttribute> attribute attaches metadata, in the form of a name-value pair, to that export.</span></span> <span data-ttu-id="a3d7e-217">Sırada `Add` sınıfının Implements `IOperation`, uygulayan bir sınıf `IOperationData` açıkça tanımlı değil.</span><span class="sxs-lookup"><span data-stu-id="a3d7e-217">While the `Add` class implements `IOperation`, a class that implements `IOperationData` is not explicitly defined.</span></span> <span data-ttu-id="a3d7e-218">Bunun yerine, bir sınıf sağlanan meta verilerin adlarına göre özellikleriyle örtük olarak MEF tarafından oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="a3d7e-218">Instead, a class is implicitly created by MEF with properties based on the names of the metadata provided.</span></span> <span data-ttu-id="a3d7e-219">(Bir MEF meta verilerinde erişmenin birkaç yolu budur.)</span><span class="sxs-lookup"><span data-stu-id="a3d7e-219">(This is one of several ways to access metadata in MEF.)</span></span>

 <span data-ttu-id="a3d7e-220">MEF birleşimde olan *özyinelemeli*.</span><span class="sxs-lookup"><span data-stu-id="a3d7e-220">Composition in MEF is *recursive*.</span></span> <span data-ttu-id="a3d7e-221">Siz açıkça oluşan `Program` içe nesne, bir `ICalculator` türünde olmasını açık `MySimpleCalculator`.</span><span class="sxs-lookup"><span data-stu-id="a3d7e-221">You explicitly composed the `Program` object, which imported an `ICalculator` that turned out to be of type `MySimpleCalculator`.</span></span> <span data-ttu-id="a3d7e-222">`MySimpleCalculator`, sırasıyla bir koleksiyonunu alır `IOperation` nesneleri ve içeri aktarma ne zaman doldurulur `MySimpleCalculator` aktarımlarının aynı zamanda oluşturulan `Program`.</span><span class="sxs-lookup"><span data-stu-id="a3d7e-222">`MySimpleCalculator`, in turn, imports a collection of `IOperation` objects, and that import will be filled when `MySimpleCalculator` is created, at the same time as the imports of `Program`.</span></span> <span data-ttu-id="a3d7e-223">Varsa `Add` sınıfı bildirilen çok doldurulması ve böyle devam etmesi gereken bir başka alma.</span><span class="sxs-lookup"><span data-stu-id="a3d7e-223">If the `Add` class declared a further import, that too would have to be filled, and so on.</span></span> <span data-ttu-id="a3d7e-224">Herhangi bir birleştirme hatası sol dolgusuz sonuçları alın.</span><span class="sxs-lookup"><span data-stu-id="a3d7e-224">Any import left unfilled results in a composition error.</span></span> <span data-ttu-id="a3d7e-225">(Ancak, isteğe bağlı olacak şekilde veya bunları varsayılan değer atamak için içeri aktarmalar bildirmek için mümkündür.)</span><span class="sxs-lookup"><span data-stu-id="a3d7e-225">(It is possible, however, to declare imports to be optional or to assign them default values.)</span></span>

<a name="calculator_logic"></a>
## <a name="calculator-logic"></a><span data-ttu-id="a3d7e-226">Hesaplayıcı mantığı</span><span class="sxs-lookup"><span data-stu-id="a3d7e-226">Calculator Logic</span></span>
 <span data-ttu-id="a3d7e-227">Bu bölümleri yerinde, kalan tek şey hesaplayıcı mantığı.</span><span class="sxs-lookup"><span data-stu-id="a3d7e-227">With these parts in place, all that remains is the calculator logic itself.</span></span> <span data-ttu-id="a3d7e-228">Aşağıdaki kodu ekleyin `MySimpleCalculator` uygulamak için sınıfı `Calculate` yöntemi:</span><span class="sxs-lookup"><span data-stu-id="a3d7e-228">Add the following code in the `MySimpleCalculator` class to implement the `Calculate` method:</span></span>

```vb
Public Function Calculate(ByVal input As String) As String Implements ICalculator.Calculate
    Dim left, right As Integer
    Dim operation As Char
    Dim fn = FindFirstNonDigit(input) 'Finds the operator
    If fn < 0 Then
        Return "Could not parse command."
    End If
    operation = input(fn)
    Try
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
    Char operation;
    int fn = FindFirstNonDigit(input); //finds the operator
    if (fn < 0) return "Could not parse command.";

    try
    {
        //separate out the operands
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

 <span data-ttu-id="a3d7e-229">İlk adımlarında, sol ve sağ işlenen uygulamasına giriş dizesi ile bir işleç karakter ayrıştırılamıyor.</span><span class="sxs-lookup"><span data-stu-id="a3d7e-229">The initial steps parse the input string into left and right operands and an operator character.</span></span> <span data-ttu-id="a3d7e-230">İçinde `foreach` döngü, her üyesi `operations` koleksiyon incelenir.</span><span class="sxs-lookup"><span data-stu-id="a3d7e-230">In the `foreach` loop, every member of the `operations` collection is examined.</span></span> <span data-ttu-id="a3d7e-231">Bu nesnelerin türündedir <xref:System.Lazy%602>, meta veri değerleri ve dışarı aktarılan nesne ile erişilebilir <xref:System.Lazy%602.Metadata%2A> özelliği ve <xref:System.Lazy%601.Value%2A> özelliği sırasıyla.</span><span class="sxs-lookup"><span data-stu-id="a3d7e-231">These objects are of type <xref:System.Lazy%602>, and their metadata values and exported object can be accessed with the <xref:System.Lazy%602.Metadata%2A> property and the <xref:System.Lazy%601.Value%2A> property respectively.</span></span> <span data-ttu-id="a3d7e-232">Bu durumda, `Symbol` özelliği `IOperationData` nesne hesaplayıcı çağrıları bir eşleşme olarak bulunursa `Operate` yöntemi `IOperation` nesne ve sonucu döndürür.</span><span class="sxs-lookup"><span data-stu-id="a3d7e-232">In this case, if the `Symbol` property of the `IOperationData` object is discovered to be a match, the calculator calls the `Operate` method of the `IOperation` object and returns the result.</span></span>

 <span data-ttu-id="a3d7e-233">Hesaplayıcı tamamlamak için ayrıca bir dizede ilk basamak olmayan karakterle konumunu döndürür bir yardımcı yöntem gerekir.</span><span class="sxs-lookup"><span data-stu-id="a3d7e-233">To complete the calculator, you also need a helper method that returns the position of the first non-digit character in a string.</span></span> <span data-ttu-id="a3d7e-234">Eklemek için aşağıdaki yardımcı yöntemini `MySimpleCalculator` sınıfı:</span><span class="sxs-lookup"><span data-stu-id="a3d7e-234">Add the following helper method to the `MySimpleCalculator` class:</span></span>

```vb
Private Function FindFirstNonDigit(ByVal s As String) As Integer
    For i = 0 To s.Length
        If (Not (Char.IsDigit(s(i)))) Then Return i
    Next
    Return -1
End Function
```

```csharp
private int FindFirstNonDigit(String s)
{
    for (int i = 0; i < s.Length; i++)
    {
        if (!(Char.IsDigit(s[i]))) return i;
    }
    return -1;
}
```

 <span data-ttu-id="a3d7e-235">Şimdi projeyi derlemek ve çalıştırmak mümkün olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="a3d7e-235">You should now be able to compile and run the project.</span></span> <span data-ttu-id="a3d7e-236">Visual Basic'te, eklediğiniz emin `Public` anahtar `Module1`.</span><span class="sxs-lookup"><span data-stu-id="a3d7e-236">In Visual Basic, make sure that you added the `Public` keyword to `Module1`.</span></span> <span data-ttu-id="a3d7e-237">Konsol penceresinde türü "5 + 3" ve hesap makinesi gibi ek bir işlem sonuçlarını döndürür.</span><span class="sxs-lookup"><span data-stu-id="a3d7e-237">In the console window, type an addition operation, such as "5+3", and the calculator returns the results.</span></span> <span data-ttu-id="a3d7e-238">Herhangi bir işleç "işlemi bulunamadı!" sonuçları</span><span class="sxs-lookup"><span data-stu-id="a3d7e-238">Any other operator results in the "Operation Not Found!"</span></span> <span data-ttu-id="a3d7e-239">İleti.</span><span class="sxs-lookup"><span data-stu-id="a3d7e-239">message.</span></span>

<a name="extending_simplecalculator_using_a_new_class"></a>
## <a name="extending-simplecalculator-using-a-new-class"></a><span data-ttu-id="a3d7e-240">Yeni bir sınıf kullanarak SimpleCalculator genişletme</span><span class="sxs-lookup"><span data-stu-id="a3d7e-240">Extending SimpleCalculator Using A New Class</span></span>
 <span data-ttu-id="a3d7e-241">Hesaplayıcı çalışır, yeni bir işlem eklemek kolaydır.</span><span class="sxs-lookup"><span data-stu-id="a3d7e-241">Now that the calculator works, adding a new operation is easy.</span></span> <span data-ttu-id="a3d7e-242">Aşağıdaki sınıf modüle ekleyin veya `SimpleCalculator` ad alanı:</span><span class="sxs-lookup"><span data-stu-id="a3d7e-242">Add the following class to the module or `SimpleCalculator` namespace:</span></span>

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

 <span data-ttu-id="a3d7e-243">Projeyi derlemek ve çalıştırmak.</span><span class="sxs-lookup"><span data-stu-id="a3d7e-243">Compile and run the project.</span></span> <span data-ttu-id="a3d7e-244">"5-3" gibi bir çıkarma işlemi yazın.</span><span class="sxs-lookup"><span data-stu-id="a3d7e-244">Type a subtraction operation, such as "5-3".</span></span> <span data-ttu-id="a3d7e-245">Hesaplayıcı, ayrıca yanı sıra çıkarma artık desteklemektedir.</span><span class="sxs-lookup"><span data-stu-id="a3d7e-245">The calculator now supports subtraction as well as addition.</span></span>

<a name="extending_simplecalculator_using_a_new_assembly"></a>
## <a name="extending-simplecalculator-using-a-new-assembly"></a><span data-ttu-id="a3d7e-246">Yeni bir derleme kullanmakla SimpleCalculator genişletme</span><span class="sxs-lookup"><span data-stu-id="a3d7e-246">Extending SimpleCalculator Using A New Assembly</span></span>
 <span data-ttu-id="a3d7e-247">Sınıf ekleme kaynak kod yeterli basittir, ancak MEF bölümleri için bir uygulamanın kendi kaynak dışında görme olanağı sağlar.</span><span class="sxs-lookup"><span data-stu-id="a3d7e-247">Adding classes to the source code is simple enough, but MEF provides the ability to look outside an application’s own source for parts.</span></span> <span data-ttu-id="a3d7e-248">Bunu göstermek için ekleyerek bölümleri, kendi derleme yanı sıra, bir dizini aranacak SimpleCalculator değiştirmeniz gerekecektir bir <xref:System.ComponentModel.Composition.Hosting.DirectoryCatalog>.</span><span class="sxs-lookup"><span data-stu-id="a3d7e-248">To demonstrate this, you will need to modify SimpleCalculator to search a directory, as well as its own assembly, for parts, by adding a <xref:System.ComponentModel.Composition.Hosting.DirectoryCatalog>.</span></span>

 <span data-ttu-id="a3d7e-249">Adlı yeni bir dizin eklemek `Extensions` SimpleCalculator projeye.</span><span class="sxs-lookup"><span data-stu-id="a3d7e-249">Add a new directory named `Extensions` to the SimpleCalculator project.</span></span> <span data-ttu-id="a3d7e-250">Proje düzeyinde ve çözüm düzeyinde eklediğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="a3d7e-250">Make sure to add it at the project level, and not at the solution level.</span></span> <span data-ttu-id="a3d7e-251">Ardından yeni bir sınıf kitaplığı projesi adlı çözüme ekleyin `ExtendedOperations`.</span><span class="sxs-lookup"><span data-stu-id="a3d7e-251">Then add a new Class Library project to the solution, named `ExtendedOperations`.</span></span> <span data-ttu-id="a3d7e-252">Yeni projeyi ayrı bir derleme içine derlenir.</span><span class="sxs-lookup"><span data-stu-id="a3d7e-252">The new project will compile into a separate assembly.</span></span>

 <span data-ttu-id="a3d7e-253">ExtendedOperations projesi için proje özellikleri Tasarımcısı'nı açın ve tıklayın **derleme** veya **derleme** sekmesi. Değişiklik **yapı çıkış yolu** veya **çıkış yolu** uzantı dizini SimpleCalculator proje dizinine işaret edecek şekilde (.. \SimpleCalculator\Extensions\\).</span><span class="sxs-lookup"><span data-stu-id="a3d7e-253">Open the Project Properties Designer for the ExtendedOperations project and click the **Compile** or **Build** tab. Change the **Build output path** or **Output path** to point to the Extensions directory in the SimpleCalculator project directory (..\SimpleCalculator\Extensions\\).</span></span>

 <span data-ttu-id="a3d7e-254">Module1.vb veya Program.cs içinde aşağıdaki satırı ekleyin `Program` Oluşturucusu:</span><span class="sxs-lookup"><span data-stu-id="a3d7e-254">In Module1.vb or Program.cs, add the following line to the `Program` constructor:</span></span>

```vb
catalog.Catalogs.Add(New DirectoryCatalog("C:\SimpleCalculator\SimpleCalculator\Extensions"))
```

```csharp
catalog.Catalogs.Add(new DirectoryCatalog("C:\\SimpleCalculator\\SimpleCalculator\\Extensions"));
```

 <span data-ttu-id="a3d7e-255">Örnek yol uzantıları dizininize yoluyla değiştirin.</span><span class="sxs-lookup"><span data-stu-id="a3d7e-255">Replace the example path with the path to your Extensions directory.</span></span> <span data-ttu-id="a3d7e-256">(Yalnızca hata ayıklama için bu mutlak bir yol içindir.</span><span class="sxs-lookup"><span data-stu-id="a3d7e-256">(This absolute path is for debugging purposes only.</span></span> <span data-ttu-id="a3d7e-257">Bir üretim uygulamasında, göreli bir yol kullanabilirsiniz.) <xref:System.ComponentModel.Composition.Hosting.DirectoryCatalog> Uzantı dizini bileştirme kapsayıcısı için tüm derlemelerde bulunan tüm bölümler artık ekleyeceksiniz.</span><span class="sxs-lookup"><span data-stu-id="a3d7e-257">In a production application, you would use a relative path.) The <xref:System.ComponentModel.Composition.Hosting.DirectoryCatalog> will now add any parts found in any assemblies in the Extensions directory to the composition container.</span></span>

 <span data-ttu-id="a3d7e-258">ExtendedOperations projesinde SimpleCalculator ve System.ComponentModel.Composition başvurular ekleyin.</span><span class="sxs-lookup"><span data-stu-id="a3d7e-258">In the ExtendedOperations project, add references to SimpleCalculator and System.ComponentModel.Composition.</span></span> <span data-ttu-id="a3d7e-259">ExtendedOperations sınıf dosyasında, ekleme bir `Imports` veya `using` System.ComponentModel.Composition bildirimi.</span><span class="sxs-lookup"><span data-stu-id="a3d7e-259">In the ExtendedOperations class file, add an `Imports` or a `using` statement for System.ComponentModel.Composition.</span></span> <span data-ttu-id="a3d7e-260">Visual Basic'te de eklemeniz bir `Imports` SimpleCalculator deyimi.</span><span class="sxs-lookup"><span data-stu-id="a3d7e-260">In Visual Basic, also add an `Imports` statement for SimpleCalculator.</span></span> <span data-ttu-id="a3d7e-261">Ardından aşağıdaki sınıf ExtendedOperations sınıfı dosyaya ekleyin:</span><span class="sxs-lookup"><span data-stu-id="a3d7e-261">Then add the following class to the ExtendedOperations class file:</span></span>

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

 <span data-ttu-id="a3d7e-262">Bu da sipariş sözleşmesiyle eşleşecek şekilde unutmayın <xref:System.ComponentModel.Composition.ExportAttribute> özniteliği, aynı türde olmalıdır <xref:System.ComponentModel.Composition.ImportAttribute>.</span><span class="sxs-lookup"><span data-stu-id="a3d7e-262">Note that in order for the contract to match, the <xref:System.ComponentModel.Composition.ExportAttribute> attribute must have the same type as the <xref:System.ComponentModel.Composition.ImportAttribute>.</span></span>

 <span data-ttu-id="a3d7e-263">Projeyi derlemek ve çalıştırmak.</span><span class="sxs-lookup"><span data-stu-id="a3d7e-263">Compile and run the project.</span></span> <span data-ttu-id="a3d7e-264">Yeni Mod (%) test etme işleci.</span><span class="sxs-lookup"><span data-stu-id="a3d7e-264">Test the new Mod (%) operator.</span></span>

<a name="conclusion"></a>
## <a name="conclusion"></a><span data-ttu-id="a3d7e-265">Sonuç</span><span class="sxs-lookup"><span data-stu-id="a3d7e-265">Conclusion</span></span>
 <span data-ttu-id="a3d7e-266">Bu konuda, MEF temel kavramlarını ele.</span><span class="sxs-lookup"><span data-stu-id="a3d7e-266">This topic covered the basic concepts of MEF.</span></span>

- <span data-ttu-id="a3d7e-267">Bölümleri ve Katalog bileşim kapsayıcı</span><span class="sxs-lookup"><span data-stu-id="a3d7e-267">Parts, catalogs, and the composition container</span></span>

     <span data-ttu-id="a3d7e-268">Bölümleri ve kapsayıcının MEF uygulamasının temel yapı taşları şunlardır.</span><span class="sxs-lookup"><span data-stu-id="a3d7e-268">Parts and the composition container are the basic building blocks of a MEF application.</span></span> <span data-ttu-id="a3d7e-269">Alır ya da en fazla kendisi de dahil bir değer verir herhangi bir nesne bir parçasıdır.</span><span class="sxs-lookup"><span data-stu-id="a3d7e-269">A part is any object that imports or exports a value, up to and including itself.</span></span> <span data-ttu-id="a3d7e-270">Katalog, belirli bir kaynaktan bölümleri koleksiyonu sağlar.</span><span class="sxs-lookup"><span data-stu-id="a3d7e-270">A catalog provides a collection of parts from a particular source.</span></span> <span data-ttu-id="a3d7e-271">Kapsayıcının Kataloğu tarafından sağlanan bölümleri oluşturmak, içeri dışarı aktarmalar bağlaması için kullanır.</span><span class="sxs-lookup"><span data-stu-id="a3d7e-271">The composition container uses the parts provided by a catalog to perform composition, the binding of imports to exports.</span></span>

- <span data-ttu-id="a3d7e-272">İçeri ve dışarı aktarmalar</span><span class="sxs-lookup"><span data-stu-id="a3d7e-272">Imports and exports</span></span>

     <span data-ttu-id="a3d7e-273">İçeri ve dışarı aktarmalar bileşenleri tarafından iletişim yoludur.</span><span class="sxs-lookup"><span data-stu-id="a3d7e-273">Imports and exports are the way by which components communicate.</span></span> <span data-ttu-id="a3d7e-274">Bir içeri aktarma ile bileşenin belirli bir değer veya nesne için bir gereksinim belirtir ve isteğe bağlı olarak dışa kullanılabilirliğini bir değer belirtir.</span><span class="sxs-lookup"><span data-stu-id="a3d7e-274">With an import, the component specifies a need for a particular value or object, and with an export it specifies the availability of a value.</span></span> <span data-ttu-id="a3d7e-275">Her bir içeri aktarma, dışarı aktarmaları sözleşmesi yoluyla listesiyle eşleştirilir.</span><span class="sxs-lookup"><span data-stu-id="a3d7e-275">Each import is matched with a list of exports by way of its contract.</span></span>

<a name="where_do_i_go_now"></a>
## <a name="where-do-i-go-now"></a><span data-ttu-id="a3d7e-276">Burada artık gitmeliyim?</span><span class="sxs-lookup"><span data-stu-id="a3d7e-276">Where Do I Go Now?</span></span>
 <span data-ttu-id="a3d7e-277">Bu örnek için tam kod indirmek için bkz [SimpleCalculator örnek](https://code.msdn.microsoft.com/windowsdesktop/Simple-Calculator-MEF-1152654e).</span><span class="sxs-lookup"><span data-stu-id="a3d7e-277">To download the complete code for this example, see the [SimpleCalculator sample](https://code.msdn.microsoft.com/windowsdesktop/Simple-Calculator-MEF-1152654e).</span></span>

 <span data-ttu-id="a3d7e-278">Daha fazla bilgi ve kod örnekleri için bkz. [Managed Extensibility Framework](https://github.com/MicrosoftArchive/mef).</span><span class="sxs-lookup"><span data-stu-id="a3d7e-278">For more information and code examples, see [Managed Extensibility Framework](https://github.com/MicrosoftArchive/mef).</span></span> <span data-ttu-id="a3d7e-279">MEF türlerinin bir listesi için bkz. <xref:System.ComponentModel.Composition?displayProperty=nameWithType> ad alanı.</span><span class="sxs-lookup"><span data-stu-id="a3d7e-279">For a list of the MEF types, see the <xref:System.ComponentModel.Composition?displayProperty=nameWithType> namespace.</span></span>
