---
title: Managed Extensibility Framework (MEF)
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Managed Extensibility Framework, overview
- MEF, overview
ms.assetid: 6c61b4ec-c6df-4651-80f1-4854f8b14dde
caps.latest.revision: 31
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 524fa0f2d654c812189ff6863f84db81144fb48f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="managed-extensibility-framework-mef"></a><span data-ttu-id="4e166-102">Managed Extensibility Framework (MEF)</span><span class="sxs-lookup"><span data-stu-id="4e166-102">Managed Extensibility Framework (MEF)</span></span>
<span data-ttu-id="4e166-103">Bu konu, .NET Framework 4'te tanıtılan Yönetilen Genişletilebilirlik Çerçevesi genel bir bakış sağlar.</span><span class="sxs-lookup"><span data-stu-id="4e166-103">This topic provides an overview of the Managed Extensibility Framework introduced in the .NET Framework 4.</span></span>  
  
<a name="what_is_mef"></a>   
## <a name="what-is-mef"></a><span data-ttu-id="4e166-104">MEF nedir?</span><span class="sxs-lookup"><span data-stu-id="4e166-104">What is MEF?</span></span>  
 <span data-ttu-id="4e166-105">Genişletilebilirlik Çerçevesi ile yönetilen veya MEF hafif, Genişletilebilir uygulamaları oluşturmak için bir kitaplık değil.</span><span class="sxs-lookup"><span data-stu-id="4e166-105">The Managed Extensibility Framework or MEF is a library for creating lightweight, extensible applications.</span></span> <span data-ttu-id="4e166-106">Uygulama geliştiricilerinin bulmak ve yapılandırma gerektirmeden uzantıları kullanmak sağlar.</span><span class="sxs-lookup"><span data-stu-id="4e166-106">It allows application developers to discover and use extensions with no configuration required.</span></span> <span data-ttu-id="4e166-107">Ayrıca kolayca kod kapsüllemek ve kırılacak sabit bağımlılıkları kaçının Uzantı geliştiricilerine olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="4e166-107">It also lets extension developers easily encapsulate code and avoid fragile hard dependencies.</span></span> <span data-ttu-id="4e166-108">MEF değil yalnızca uygulama içinden ancak de uygulamalar arasında yeniden kullanılabilir uzantıları sağlar.</span><span class="sxs-lookup"><span data-stu-id="4e166-108">MEF not only allows extensions to be reused within applications, but across applications as well.</span></span>  
  
<a name="the_problem_of_extensibility"></a>   
## <a name="the-problem-of-extensibility"></a><span data-ttu-id="4e166-109">Genişletilebilirlik sorunu</span><span class="sxs-lookup"><span data-stu-id="4e166-109">The Problem of Extensibility</span></span>  
 <span data-ttu-id="4e166-110">Genişletilebilirlik için destek sağlayan büyük bir uygulamanın Mimarı olduğunuzu varsayalım.</span><span class="sxs-lookup"><span data-stu-id="4e166-110">Imagine that you are the architect of a large application that must provide support for extensibility.</span></span> <span data-ttu-id="4e166-111">Uygulamanız daha küçük bileşenlerden çok sayıda içermek zorundadır ve oluşturma ve bunları çalıştırmaya sorumludur.</span><span class="sxs-lookup"><span data-stu-id="4e166-111">Your application has to include a potentially large number of smaller components, and is responsible for creating and running them.</span></span>  
  
 <span data-ttu-id="4e166-112">En basit sorun için kaynak kodu, uygulamanızda bileşenleri içerir ve doğrudan kodunuzdan çağrı yaklaşımdır.</span><span class="sxs-lookup"><span data-stu-id="4e166-112">The simplest approach to the problem is to include the components as source code in your application, and call them directly from your code.</span></span>  <span data-ttu-id="4e166-113">Bunun bir belirgin bazı dezavantajları vardır.</span><span class="sxs-lookup"><span data-stu-id="4e166-113">This has a number of obvious drawbacks.</span></span>  <span data-ttu-id="4e166-114">En önemlisi, örneğin, bir Web uygulamasında, kabul edilebilir, ancak bir istemci uygulamasında çalışmaz bir kısıtlama kaynak kodunu değiştirmeden yeni bileşenler ekleyemezsiniz.</span><span class="sxs-lookup"><span data-stu-id="4e166-114">Most importantly, you cannot add new components without modifying the source code, a restriction that might be acceptable in, for example, a Web application, but is unworkable in a client application.</span></span>  <span data-ttu-id="4e166-115">Üçüncü tarafların ve bunları sizin erişmek izin veremez aynı nedenden dolayı geliştirilebilir için eşit oranda sorunlu olmasa da, bileşenler için kaynak koduna erişim olmayabilir.</span><span class="sxs-lookup"><span data-stu-id="4e166-115">Equally problematic, you may not have access to the source code for the components, because they might be developed by third parties, and for the same reason you cannot allow them to access yours.</span></span>  
  
 <span data-ttu-id="4e166-116">Bir uzantı noktası veya uygulama ve bileşenlerinin bağlantıyı kesmeye izin vermek için arabirim sağlamak için biraz daha karmaşık bir yaklaşım olacaktır.</span><span class="sxs-lookup"><span data-stu-id="4e166-116">A slightly more sophisticated approach would be to provide an extension point or interface, to permit decoupling between the application and its components.</span></span>  <span data-ttu-id="4e166-117">Bu model altında bir bileşen uygulayabileceğiniz bir arabirim ve uygulamanız ile etkileşim kurmak etkinleştirmek için bir API sağlayabilir.</span><span class="sxs-lookup"><span data-stu-id="4e166-117">Under this model, you might provide an interface that a component can implement, and an API to enable it to interact with your application.</span></span>  <span data-ttu-id="4e166-118">Bu kaynak koduna erişim gerektiren sorununu çözer, ancak hala zorluklara sahiptir.</span><span class="sxs-lookup"><span data-stu-id="4e166-118">This solves the problem of requiring source code access, but it still has its own difficulties.</span></span>  
  
 <span data-ttu-id="4e166-119">Uygulama bileşenleri kendi başına bulmak için tüm kapasite eksik olduğundan, hala açıkça hangi bileşenlerin mevcut olduğu ve yüklenmesi gerektiğini söylediyse gerekir.</span><span class="sxs-lookup"><span data-stu-id="4e166-119">Because the application lacks any capacity for discovering components on its own, it must still be explicitly told which components are available and should be loaded.</span></span>  <span data-ttu-id="4e166-120">Bu genellikle bir yapılandırma dosyasında kullanılabilir bileşenleri açıkça kaydederek gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="4e166-120">This is typically accomplished by explicitly registering the available components in a configuration file.</span></span> <span data-ttu-id="4e166-121">Özellikle son kullanıcı ile güncelleştirme yapmak için beklenen geliştirici değil, ise bileşenleri sağlayan doğru Bunun anlamı bakım sorun haline gelir.</span><span class="sxs-lookup"><span data-stu-id="4e166-121">This means that assuring that the components are correct becomes a maintenance issue, particularly if it is the end user and not the developer who is expected to do the updating.</span></span>  
  
 <span data-ttu-id="4e166-122">Ayrıca, birbirleriyle dışında uygulamanın kendisinin aracılığı tanımlanan kanallar iletişim kuramadığı bileşenleridir.</span><span class="sxs-lookup"><span data-stu-id="4e166-122">In addition, components are incapable of communicating with one another, except through the rigidly defined channels of the application itself.</span></span>  <span data-ttu-id="4e166-123">Uygulama Mimarı belirli bir iletişim için gereken beklenen değil, genellikle mümkün değildir.</span><span class="sxs-lookup"><span data-stu-id="4e166-123">If the application architect has not anticipated the need for a particular communication, it is usually impossible.</span></span>  
  
 <span data-ttu-id="4e166-124">Son olarak, bileşen geliştiricileri hangi derlemenin uyguladıkları arayüzü içeren üzerinde sıkı bir bağımlılık kabul etmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="4e166-124">Finally, the component developers must accept a hard dependency on what assembly contains the interface they implement.</span></span>  <span data-ttu-id="4e166-125">Bu durum, birden fazla uygulamada kullanılacak bir bileşen zorlaştırır ve bileşenleri için bir test çerçevesi oluşturduğunuzda sorunları da oluşturabilir.</span><span class="sxs-lookup"><span data-stu-id="4e166-125">This makes it difficult for a component to be used in more than one application, and can also create problems when you create a test framework for components.</span></span>  
  
<a name="what_mef_provides"></a>   
## <a name="what-mef-provides"></a><span data-ttu-id="4e166-126">MEF ne sağlar</span><span class="sxs-lookup"><span data-stu-id="4e166-126">What MEF Provides</span></span>  
 <span data-ttu-id="4e166-127">Mevcut bileşenlerin açık kaydı yerine MEF dolaylı olarak bulmak için bir yol sağlar. aracılığıyla *birleşim*.</span><span class="sxs-lookup"><span data-stu-id="4e166-127">Instead of this explicit registration of available components, MEF provides a way to discover them implicitly, via *composition*.</span></span>  <span data-ttu-id="4e166-128">Adlı bir MEF Bileşeni, bir *bölümü*, bildirimli olarak hem bağımlılıklarını belirtir (olarak bilinen *alır*) ve hangi özelliklere (olarak bilinen *aktarır*) kullanılabilir hale getirir.</span><span class="sxs-lookup"><span data-stu-id="4e166-128">A MEF component, called a *part*, declaratively specifies both its dependencies (known as *imports*) and what capabilities (known as *exports*) it makes available.</span></span> <span data-ttu-id="4e166-129">Bir bölümü oluşturulduğunda, MEF bileşim motoru diğer bölümlerden kullanılabilir olan, içeri aktarmalar karşılar.</span><span class="sxs-lookup"><span data-stu-id="4e166-129">When a part is created, the MEF composition engine satisfies its imports with what is available from other parts.</span></span>  
  
 <span data-ttu-id="4e166-130">Bu yaklaşım önceki bölümde açıklanan sorunları çözer.</span><span class="sxs-lookup"><span data-stu-id="4e166-130">This approach solves the problems discussed in the previous section.</span></span>  <span data-ttu-id="4e166-131">MEF bölümleri bildirimli olarak yeteneklerini belirtmek için çalışma zamanında keşfedilebilir oldukları sabit kodlanmış başvuruları veya kırılacak yapılandırma dosyalarını olmadan parçalar kullanımını uygulama yapabilir anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="4e166-131">Because MEF parts declaratively specify their capabilities, they are discoverable at runtime, which means an application can make use of parts without either hard-coded references or fragile configuration files.</span></span>  <span data-ttu-id="4e166-132">MEF bulmak ve onları başlatmasını veya hatta kendi derlemeleri yükleme bölümleri bunların meta verilerini incelemek uygulamaları sağlar.</span><span class="sxs-lookup"><span data-stu-id="4e166-132">MEF allows applications to discover and examine parts by their metadata, without instantiating them or even loading their assemblies.</span></span> <span data-ttu-id="4e166-133">Sonuç olarak, dikkatli bir şekilde nasıl ve ne zaman uzantıları yüklenmesi gerektiğini belirtmek için gerek yoktur.</span><span class="sxs-lookup"><span data-stu-id="4e166-133">As a result, there is no need to carefully specify when and how extensions should be loaded.</span></span>  
  
 <span data-ttu-id="4e166-134">Sağlanan dışarı aktarmaları ek olarak, bir bölümü diğer bölümler tarafından doldurulacak kendi içeri aktarmalar belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4e166-134">In addition to its provided exports, a part can specify its imports, which will be filled by other parts.</span></span>  <span data-ttu-id="4e166-135">Bu yapar arasında iletişimi değil yalnızca olası ancak kolay bölümleri ve kodunu iyi bir şekilde düzenlenmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="4e166-135">This makes communication among parts not only possible, but easy, and allows for good factoring of code.</span></span> <span data-ttu-id="4e166-136">Örneğin, birçok bileşen için ortak hizmetler ayrı bir bölüm içinde ve kolayca değiştirilebilir veya değiştirildi.</span><span class="sxs-lookup"><span data-stu-id="4e166-136">For example, services common to many components can be factored into a separate part and easily modified or replaced.</span></span>  
  
 <span data-ttu-id="4e166-137">MEF modeli belirli bir uygulama derlemesi üzerinde sıkı bir bağımlılık gerektirdiğinden, uygulamadan uygulamaya yeniden kullanılabilir uzantıları sağlar.</span><span class="sxs-lookup"><span data-stu-id="4e166-137">Because the MEF model requires no hard dependency on a particular application assembly, it allows extensions to be reused from application to application.</span></span>  <span data-ttu-id="4e166-138">Bu ayrıca, uygulamayı uzantı bileşenlerini test etmek, bağımsız bir test bandı geliştirmek kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="4e166-138">This also makes it easy to develop a test harness, independent of the application, to test extension components.</span></span>  
  
 <span data-ttu-id="4e166-139">Uygulama Hizmetleri uzantılarını kullanıma sunmak için uzantı bileşenleri tarafından doldurulabilir ve da bildirebilir içe aktarır MEF kullanılarak yazılmış Genişletilebilir uygulama bildirir.</span><span class="sxs-lookup"><span data-stu-id="4e166-139">An extensible application written by using MEF declares an import that can be filled by extension components, and may also declare exports in order to expose application services to extensions.</span></span>  <span data-ttu-id="4e166-140">Her uzantı bileşeni verme bildirir ve içeri aktarımlar da bildirebilir.</span><span class="sxs-lookup"><span data-stu-id="4e166-140">Each extension component declares an export, and may also declare imports.</span></span>  <span data-ttu-id="4e166-141">Bu şekilde, uzantı bileşenlerinin kendileri otomatik olarak genişletilebilir.</span><span class="sxs-lookup"><span data-stu-id="4e166-141">In this way, extension components themselves are automatically extensible.</span></span>  
  
<a name="where_is_mef_available"></a>   
## <a name="where-is-mef-available"></a><span data-ttu-id="4e166-142">Burada MEF var mı?</span><span class="sxs-lookup"><span data-stu-id="4e166-142">Where Is MEF Available?</span></span>  
 <span data-ttu-id="4e166-143">MEF bütünleyici bir [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)]ve .NET Framework'ün yerde kullanıldığı kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="4e166-143">MEF is an integral part of the [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)], and is available wherever the .NET Framework is used.</span></span>  <span data-ttu-id="4e166-144">Windows Forms, WPF veya başka bir teknolojinin kullanıp veya ASP.NET kullanan sunucu uygulamaları, istemci uygulamalarınızda MEF kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4e166-144">You can use MEF in your client applications, whether they use Windows Forms, WPF, or any other technology, or in server applications that use ASP.NET.</span></span>  
  
<a name="mef_and_maf"></a>   
## <a name="mef-and-maf"></a><span data-ttu-id="4e166-145">MEF ve MAF</span><span class="sxs-lookup"><span data-stu-id="4e166-145">MEF and MAF</span></span>  
 <span data-ttu-id="4e166-146">.NET Framework'ün önceki sürümlerini yönetilen eklenti Framework (yalıtmak ve uzantıları yönetmek uygulamalara izin vermek üzere tasarlanmış MAF) sunmuş.</span><span class="sxs-lookup"><span data-stu-id="4e166-146">Previous versions of the .NET Framework introduced the Managed Add-in Framework (MAF), designed to allow applications to isolate and manage extensions.</span></span>  <span data-ttu-id="4e166-147">MAF odak biraz daha yüksek düzeyli uzantı yalıtımına ve yüklenmesi ve kaldırılması MEF'in odak bulunabilirliği, genişletilebilirlik ve taşınabilirlik durumdayken derleme yoğunlaştırıcı MEF daha.</span><span class="sxs-lookup"><span data-stu-id="4e166-147">The focus of MAF is slightly higher-level than MEF, concentrating on extension isolation and assembly loading and unloading, while MEF's focus is on discoverability, extensibility, and portability.</span></span>  <span data-ttu-id="4e166-148">İki çerçeveleri düzgün çalışmasını ve tek bir uygulama hem de yararlanabilir.</span><span class="sxs-lookup"><span data-stu-id="4e166-148">The two frameworks interoperate smoothly, and a single application can take advantage of both.</span></span>  
  
<a name="simplecalculator_an_example_application"></a>   
## <a name="simplecalculator-an-example-application"></a><span data-ttu-id="4e166-149">SimpleCalculator: Örnek bir uygulama</span><span class="sxs-lookup"><span data-stu-id="4e166-149">SimpleCalculator: An Example Application</span></span>  
 <span data-ttu-id="4e166-150">En basit yolu MEF neler yapabileceğinizi görmek için basit bir MEF uygulaması oluşturmaktır.</span><span class="sxs-lookup"><span data-stu-id="4e166-150">The simplest way to see what MEF can do is to build a simple MEF application.</span></span> <span data-ttu-id="4e166-151">Bu örnekte, SimpleCalculator adlı çok basit bir hesap makinesi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="4e166-151">In this example, you build a very simple calculator named SimpleCalculator.</span></span> <span data-ttu-id="4e166-152">SimpleCalculator amacı "5 + 3" biçiminde temel aritmetik komutları kabul eden bir konsol uygulaması oluşturmaktır veya "6-2" ve doğru yanıt verir.</span><span class="sxs-lookup"><span data-stu-id="4e166-152">The goal of SimpleCalculator is to create a console application that accepts basic arithmetic commands, in the form "5+3" or "6-2", and returns the correct answers.</span></span> <span data-ttu-id="4e166-153">MEF kullanarak uygulama kodunu değiştirmeden yeni işleçler eklemeniz mümkün olacaktır.</span><span class="sxs-lookup"><span data-stu-id="4e166-153">Using MEF, you will be able to add new operators without changing the application code.</span></span>  
  
 <span data-ttu-id="4e166-154">Bu örneğin tam kodu indirmek için bkz: [SimpleCalculator örnek](http://code.msdn.microsoft.com/windowsdesktop/Simple-Calculator-MEF-1152654e).</span><span class="sxs-lookup"><span data-stu-id="4e166-154">To download the complete code for this example, see the [SimpleCalculator sample](http://code.msdn.microsoft.com/windowsdesktop/Simple-Calculator-MEF-1152654e).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4e166-155">SimpleCalculator amacı MEF sözdizimi ve kavramları göstermek için yerine mutlaka gerçekçi bir senaryo için kullanımı sağlamak için budur.</span><span class="sxs-lookup"><span data-stu-id="4e166-155">The purpose of SimpleCalculator is to demonstrate the concepts and syntax of MEF, rather than to necessarily provide a realistic scenario for its use.</span></span> <span data-ttu-id="4e166-156">MEF gücünü en yararlı uygulamaları çoğunu SimpleCalculator daha karmaşıktır.</span><span class="sxs-lookup"><span data-stu-id="4e166-156">Many of the applications that would benefit most from the power of MEF are more complex than SimpleCalculator.</span></span> <span data-ttu-id="4e166-157">Daha kapsamlı örnekler için bkz: [Genişletilebilirlik Çerçevesi ile yönetilen](https://github.com/MicrosoftArchive/mef) github'da.</span><span class="sxs-lookup"><span data-stu-id="4e166-157">For more extensive examples, see the [Managed Extensibility Framework](https://github.com/MicrosoftArchive/mef) on GitHub.</span></span>
  
 <span data-ttu-id="4e166-158">, Başlatmak için [!INCLUDE[vs_dev10_long](../../../includes/vs-dev10-long-md.md)], adlı yeni bir konsol uygulama projesi oluşturun `SimpleCalculator`.</span><span class="sxs-lookup"><span data-stu-id="4e166-158">To start, in [!INCLUDE[vs_dev10_long](../../../includes/vs-dev10-long-md.md)], create a new Console Application project named `SimpleCalculator`.</span></span> <span data-ttu-id="4e166-159">MEF bulunduğu System.ComponentModel.Composition derlemesine başvuru ekleyin.</span><span class="sxs-lookup"><span data-stu-id="4e166-159">Add a reference to the System.ComponentModel.Composition assembly, where MEF resides.</span></span> <span data-ttu-id="4e166-160">Module1.vb veya Program.cs açın ve eklemek `Imports` veya `using` System.ComponentModel.Composition ve System.ComponentModel.Composition.Hosting bildirimlerini.</span><span class="sxs-lookup"><span data-stu-id="4e166-160">Open Module1.vb or Program.cs and add `Imports` or `using` statements for System.ComponentModel.Composition and System.ComponentModel.Composition.Hosting.</span></span> <span data-ttu-id="4e166-161">Bu iki ad alanı Genişletilebilir uygulama geliştirme için ihtiyaç duyduğunuz MEF türlerini içerir.</span><span class="sxs-lookup"><span data-stu-id="4e166-161">These two namespaces contain MEF types you will need to develop an extensible application.</span></span> <span data-ttu-id="4e166-162">Visual Basic'te eklemek `Public` anahtar sözcüğü bildirir satırına `Module1` modülü.</span><span class="sxs-lookup"><span data-stu-id="4e166-162">In Visual Basic, add the `Public` keyword to the line that declares the `Module1` module.</span></span>  
  
<a name="composition_container_and_catalogs"></a>   
## <a name="composition-container-and-catalogs"></a><span data-ttu-id="4e166-163">Kapsayıcının ve kataloglarını</span><span class="sxs-lookup"><span data-stu-id="4e166-163">Composition Container and Catalogs</span></span>  
 <span data-ttu-id="4e166-164">MEF bileşim modelinin çekirdeği *kapsayıcının*, kullanılabilir tüm bölümleri içerir ve oluşturma işlemini gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="4e166-164">The core of the MEF composition model is the *composition container*, which contains all the parts available and performs composition.</span></span>  <span data-ttu-id="4e166-165">(Diğer bir deyişle, içeri aktarmalar için aktarımlarla.)  Kapsayıcının en yaygın türü <xref:System.ComponentModel.Composition.Hosting.CompositionContainer>, ve bu SimpleCalculator için kullanır.</span><span class="sxs-lookup"><span data-stu-id="4e166-165">(That is, the matching up of imports to exports.)  The most common type of composition container is <xref:System.ComponentModel.Composition.Hosting.CompositionContainer>, and you will use this for SimpleCalculator.</span></span>  
  
 <span data-ttu-id="4e166-166">Visual Basic'te Module1.vb, adlı ortak bir sınıf ekleyin `Program`.</span><span class="sxs-lookup"><span data-stu-id="4e166-166">In Visual Basic, in Module1.vb, add a public class named `Program`.</span></span> <span data-ttu-id="4e166-167">Aşağıdaki satırı ekleyin `Program` Module1.vb veya Program.cs sınıfında:</span><span class="sxs-lookup"><span data-stu-id="4e166-167">Then add the following line to the `Program` class in Module1.vb or Program.cs:</span></span>  
  
```vb  
Dim _container As CompositionContainer  
```  
  
```csharp  
private CompositionContainer _container;  
```  
  
 <span data-ttu-id="4e166-168">Bunun için birleşim kapsayıcıları kullanılabilir bölümleri bulmak için kullanır bir *katalog*.</span><span class="sxs-lookup"><span data-stu-id="4e166-168">In order to discover the parts available to it, the composition containers makes use of a *catalog*.</span></span> <span data-ttu-id="4e166-169">Bir katalog bazı kaynaklardaki bölümleri kullanılabilir hale getiren bir nesnedir.</span><span class="sxs-lookup"><span data-stu-id="4e166-169">A catalog is an object that makes available parts discovered from some source.</span></span>  <span data-ttu-id="4e166-170">MEF sağlanan türü, bir derlemeyi ya da dizin bölümlerini keşfetmenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="4e166-170">MEF provides catalogs to discover parts from a provided type, an assembly, or a directory.</span></span> <span data-ttu-id="4e166-171">Uygulama geliştiricilerinin Web hizmeti gibi diğer kaynaklardan kısımlarını keşfetmek için yeni katalog kolayca oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4e166-171">Application developers can easily create new catalogs to discover parts from other sources, such as a Web service.</span></span>  
  
 <span data-ttu-id="4e166-172">Aşağıdaki oluşturucuyu ekleyin `Program` sınıfı:</span><span class="sxs-lookup"><span data-stu-id="4e166-172">Add the following constructor to the `Program` class:</span></span>  
  
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
  
 <span data-ttu-id="4e166-173">Çağrı <xref:System.ComponentModel.Composition.AttributedModelServices.ComposeParts%2A> geçerli örneği bu durumda bölümleri belirli bir kümesini oluşturmak için kapsayıcının söyler `Program`.</span><span class="sxs-lookup"><span data-stu-id="4e166-173">The call to <xref:System.ComponentModel.Composition.AttributedModelServices.ComposeParts%2A> tells the composition container to compose a specific set of parts, in this case the current instance of `Program`.</span></span> <span data-ttu-id="4e166-174">Bu noktada, ancak hiçbir şey, beri olacağını `Program` doldurmak için aktarımlara sahip değildir.</span><span class="sxs-lookup"><span data-stu-id="4e166-174">At this point, however, nothing will happen, since `Program` has no imports to fill.</span></span>  
  
<a name="imports_and_exports_with_attributes"></a>   
## <a name="imports-and-exports-with-attributes"></a><span data-ttu-id="4e166-175">İçeri ve dışarı aktarmalar özniteliklere sahip</span><span class="sxs-lookup"><span data-stu-id="4e166-175">Imports and Exports with Attributes</span></span>  
 <span data-ttu-id="4e166-176">İlk olarak `Program` bir hesap makinesini içeri aktarır.</span><span class="sxs-lookup"><span data-stu-id="4e166-176">First, you have `Program` import a calculator.</span></span> <span data-ttu-id="4e166-177">Bu kullanıcı ayrılması, konsol giriş ve çıkış gireceğini gibi arabirimi sorunlarını sağlar `Program`, hesap makinesi mantığından.</span><span class="sxs-lookup"><span data-stu-id="4e166-177">This allows the separation of user interface concerns, such as the console input and output that will go into `Program`, from the logic of the calculator.</span></span>  
  
 <span data-ttu-id="4e166-178">Aşağıdaki kodu ekleyin `Program` sınıfı:</span><span class="sxs-lookup"><span data-stu-id="4e166-178">Add the following code to the `Program` class:</span></span>  
  
```vb  
<Import(GetType(ICalculator))>  
Public Property calculator As ICalculator  
```  
  
```csharp  
[Import(typeof(ICalculator))]  
public ICalculator calculator;  
```  
  
 <span data-ttu-id="4e166-179">Dikkat bildirimi `calculator` nesne olağan dışı bir durum değil ancak ile donatılmış <xref:System.ComponentModel.Composition.ImportAttribute> özniteliği.</span><span class="sxs-lookup"><span data-stu-id="4e166-179">Notice that the declaration of the `calculator` object is not unusual, but that it is decorated with the <xref:System.ComponentModel.Composition.ImportAttribute> attribute.</span></span>  <span data-ttu-id="4e166-180">Bu öznitelik bir alma olması için bir şeyler bildirir; diğer bir deyişle, nesne oluşturulduğunda bileşim motoru tarafından doldurulur.</span><span class="sxs-lookup"><span data-stu-id="4e166-180">This attribute declares something to be an import; that is, it will be filled by the composition engine when the object is composed.</span></span>  
  
 <span data-ttu-id="4e166-181">Her içeri aktarma sahip bir *sözleşme*, onu eşleşebilecek ile hangi dışarı belirler.</span><span class="sxs-lookup"><span data-stu-id="4e166-181">Every import has a *contract*, which determines what exports it will be matched with.</span></span> <span data-ttu-id="4e166-182">Anlaşma açıkça belirtilmiş bir dize olabilir veya bu durumda arabirimi verilen bir türden MEF tarafından otomatik olarak da oluşturulabilir `ICalculator`.</span><span class="sxs-lookup"><span data-stu-id="4e166-182">The contract can be an explicitly specified string, or it can be automatically generated by MEF from a given type, in this case the interface `ICalculator`.</span></span>  <span data-ttu-id="4e166-183">Eşleşen bir anlaşma ile bildirilen tüm dışarı bu alma karşılar.</span><span class="sxs-lookup"><span data-stu-id="4e166-183">Any export declared with a matching contract will fulfill this import.</span></span>  <span data-ttu-id="4e166-184">Türü unutmayın `calculator` nesnesidir aslında `ICalculator`, bu gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="4e166-184">Note that while the type of the `calculator` object is in fact `ICalculator`, this is not required.</span></span> <span data-ttu-id="4e166-185">Sözleşme alma nesne türünden bağımsızdır.</span><span class="sxs-lookup"><span data-stu-id="4e166-185">The contract is independent from the type of the importing object.</span></span>  <span data-ttu-id="4e166-186">(Bu durumda, dışlamayı `typeof(ICalculator)`.</span><span class="sxs-lookup"><span data-stu-id="4e166-186">(In this case, you could leave out the `typeof(ICalculator)`.</span></span>  <span data-ttu-id="4e166-187">MEF otomatik olarak açıkça belirtmediğiniz sürece alma türüne göre için sözleşme varsayar.)</span><span class="sxs-lookup"><span data-stu-id="4e166-187">MEF will automatically assume the contract to be based on the type of the import unless you specify it explicitly.)</span></span>  
  
 <span data-ttu-id="4e166-188">Bu çok basit arabirim modüle ekleyin veya `SimpleCalculator` ad alanı:</span><span class="sxs-lookup"><span data-stu-id="4e166-188">Add this very simple interface to the module or `SimpleCalculator` namespace:</span></span>  
  
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
  
 <span data-ttu-id="4e166-189">Tanımladığınız göre `ICalculator`, bunu uygulayan bir sınıf gerekir.</span><span class="sxs-lookup"><span data-stu-id="4e166-189">Now that you have defined `ICalculator`, you need a class that implements it.</span></span>  <span data-ttu-id="4e166-190">Aşağıdaki sınıf modülüne ekleyin veya `SimpleCalculator` ad alanı:</span><span class="sxs-lookup"><span data-stu-id="4e166-190">Add the following class to the module or `SimpleCalculator` namespace:</span></span>  
  
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
  
 <span data-ttu-id="4e166-191">İçeri aktarma ile eşleşir verme işte `Program`.</span><span class="sxs-lookup"><span data-stu-id="4e166-191">Here is the export that will match the import in `Program`.</span></span> <span data-ttu-id="4e166-192">Alma eşleşecek şekilde dışa aktarmak için dışa aktarma aynı sözleşme olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="4e166-192">In order for the export to match the import, the export must have the same contract.</span></span>  <span data-ttu-id="4e166-193">Bir anlaşma altında dışarı aktarım temel alarak `typeof(MySimpleCalculator)` bir uyuşmazlık oluşturur ve içeri aktarma doldurulmadı; sözleşme tam olarak eşleşmesi gerekiyor.</span><span class="sxs-lookup"><span data-stu-id="4e166-193">Exporting under a contract based on `typeof(MySimpleCalculator)` would produce a mismatch, and the import would not be filled; the contract needs to match exactly.</span></span>  
  
 <span data-ttu-id="4e166-194">Bu derlemede kullanılabilir tüm bölümleri içeren kapsayıcının doldurulur beri `MySimpleCalculator` bölümü kullanılabilir olacak.</span><span class="sxs-lookup"><span data-stu-id="4e166-194">Since the composition container will be populated with all the parts available in this assembly, the `MySimpleCalculator` part will be available.</span></span>  <span data-ttu-id="4e166-195">Zaman Oluşturucusu `Program` üzerinde bileşim gerçekleştirdiğinde `Program` nesne, kendi alma ile doldurulur bir `MySimpleCalculator` bu amaç için oluşturulacak nesne.</span><span class="sxs-lookup"><span data-stu-id="4e166-195">When the constructor for `Program` performs composition on the `Program` object, its import will be filled with a `MySimpleCalculator` object, which will be created for that purpose.</span></span>  
  
 <span data-ttu-id="4e166-196">Kullanıcı arabirim katmanı (`Program`) başka bir şey bilmek gerekmez.</span><span class="sxs-lookup"><span data-stu-id="4e166-196">The user interface layer (`Program`) does not need to know anything else.</span></span>  <span data-ttu-id="4e166-197">Bu nedenle kullanıcı arabirimi mantığı geri kalanında doldurabilirsiniz `Main` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="4e166-197">You can therefore fill in the rest of the user interface logic in the `Main` method.</span></span>  
  
 <span data-ttu-id="4e166-198">Aşağıdaki kodu ekleyin `Main` yöntemi:</span><span class="sxs-lookup"><span data-stu-id="4e166-198">Add the following code to the `Main` method:</span></span>  
  
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
  
 <span data-ttu-id="4e166-199">Bu kod yalnızca bir satır girişi ve çağrıları okur `Calculate` işlevinin `ICalculator` geri konsola yazar sonucu üzerinde.</span><span class="sxs-lookup"><span data-stu-id="4e166-199">This code simply reads a line of input and calls the `Calculate` function of `ICalculator` on the result, which it writes back to the console.</span></span> <span data-ttu-id="4e166-200">İçinde ihtiyacınız olan tüm kod `Program`.</span><span class="sxs-lookup"><span data-stu-id="4e166-200">That is all the code you need in `Program`.</span></span>  <span data-ttu-id="4e166-201">İş tüm kalan bölümlerinde gerçekleşir.</span><span class="sxs-lookup"><span data-stu-id="4e166-201">All the rest of the work will happen in the parts.</span></span>  
  
<a name="further_imports_and_importmany"></a>   
## <a name="further-imports-and-importmany"></a><span data-ttu-id="4e166-202">Daha fazla içeri aktarma ve ImportMany</span><span class="sxs-lookup"><span data-stu-id="4e166-202">Further Imports and ImportMany</span></span>  
 <span data-ttu-id="4e166-203">Genişletilebilir olmak üzere SimpleCalculator sırayla işlemlerinin bir listesini almak gerekir.</span><span class="sxs-lookup"><span data-stu-id="4e166-203">In order for SimpleCalculator to be extensible, it needs to import a list of operations.</span></span> <span data-ttu-id="4e166-204">Sıradan <xref:System.ComponentModel.Composition.ImportAttribute> özniteliği bir ve yalnızca bir tarafından doldurulur <xref:System.ComponentModel.Composition.ExportAttribute>.</span><span class="sxs-lookup"><span data-stu-id="4e166-204">An ordinary <xref:System.ComponentModel.Composition.ImportAttribute> attribute is filled by one and only one <xref:System.ComponentModel.Composition.ExportAttribute>.</span></span>  <span data-ttu-id="4e166-205">Birden fazla olup olmadığını bileşim motoru hata verir.</span><span class="sxs-lookup"><span data-stu-id="4e166-205">If more than one is available, the composition engine produces an error.</span></span>  <span data-ttu-id="4e166-206">Herhangi bir sayıda dışarı doldurulabilir bir alma oluşturmak için kullanabileceğiniz <xref:System.ComponentModel.Composition.ImportManyAttribute> özniteliği.</span><span class="sxs-lookup"><span data-stu-id="4e166-206">To create an import that can be filled by any number of exports, you can use the <xref:System.ComponentModel.Composition.ImportManyAttribute> attribute.</span></span>  
  
 <span data-ttu-id="4e166-207">Aşağıdaki işlemleri özelliği Ekle `MySimpleCalculator` sınıfı:</span><span class="sxs-lookup"><span data-stu-id="4e166-207">Add the following operations property to the `MySimpleCalculator` class:</span></span>  
  
```vb  
<ImportMany()>  
Public Property operations As IEnumerable(Of Lazy(Of IOperation, IOperationData))  
```  
  
```csharp  
[ImportMany]  
IEnumerable<Lazy<IOperation, IOperationData>> operations;  
```  
  
 <span data-ttu-id="4e166-208"><xref:System.Lazy%602>bir tür dışarı başvuruları dolaylı olarak tutmak için MEF tarafından sağlanır.</span><span class="sxs-lookup"><span data-stu-id="4e166-208"><xref:System.Lazy%602> is a type provided by MEF to hold indirect references to exports.</span></span>  <span data-ttu-id="4e166-209">Burada, dışarı aktarılan nesnenin kendisinin yanı sıra, aynı zamanda alırsınız *meta verileri dışarı aktarma*, ya da dışarı aktarılan nesnenin açıklayan bilgiler.</span><span class="sxs-lookup"><span data-stu-id="4e166-209">Here, in addition to the exported object itself, you also get *export metadata*, or information that describes the exported object.</span></span> <span data-ttu-id="4e166-210">Her <xref:System.Lazy%602> içeren bir `IOperation` gerçek bir işlemi temsil eden nesne ve bir `IOperationData` meta verilerini temsil eden nesne.</span><span class="sxs-lookup"><span data-stu-id="4e166-210">Each <xref:System.Lazy%602> contains an `IOperation` object, representing an actual operation, and an `IOperationData` object, representing its metadata.</span></span>  
  
 <span data-ttu-id="4e166-211">Aşağıdaki basit modülü arabirimler veya `SimpleCalculator` ad alanı:</span><span class="sxs-lookup"><span data-stu-id="4e166-211">Add the following simple interfaces to the module or `SimpleCalculator` namespace:</span></span>  
  
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
  
 <span data-ttu-id="4e166-212">Bu durumda, her işlem için meta veriler olduğunu gibi bu işlemi temsil eden simgeyi +, -, \* ve benzeri.</span><span class="sxs-lookup"><span data-stu-id="4e166-212">In this case, the metadata for each operation is the symbol that represents that operation, such as +, -, \*, and so on.</span></span> <span data-ttu-id="4e166-213">Ek işlemi kullanılabilir yapmak için aşağıdaki sınıfı modüle ekleyin veya `SimpleCalculator` ad alanı:</span><span class="sxs-lookup"><span data-stu-id="4e166-213">To make the addition operation available, add the following class to the module or `SimpleCalculator` namespace:</span></span>  
  
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
  
 <span data-ttu-id="4e166-214"><xref:System.ComponentModel.Composition.ExportAttribute> Önce yaptığınız gibi işlevler özniteliği.</span><span class="sxs-lookup"><span data-stu-id="4e166-214">The <xref:System.ComponentModel.Composition.ExportAttribute> attribute functions as it did before.</span></span>  <span data-ttu-id="4e166-215"><xref:System.ComponentModel.Composition.ExportMetadataAttribute> Özniteliği bu dışarı meta verileri, formun ad-değer çifti ekler.</span><span class="sxs-lookup"><span data-stu-id="4e166-215">The <xref:System.ComponentModel.Composition.ExportMetadataAttribute> attribute attaches metadata, in the form of a name-value pair, to that export.</span></span>  <span data-ttu-id="4e166-216">Sırada `Add` uygulayan sınıf `IOperation`, uygulayan bir sınıf `IOperationData` açıkça tanımlı değil.</span><span class="sxs-lookup"><span data-stu-id="4e166-216">While the `Add` class implements `IOperation`, a class that implements `IOperationData` is not explicitly defined.</span></span> <span data-ttu-id="4e166-217">Bunun yerine, bir sınıf sağlanan meta verilerin adlarına göre özellikleriyle örtük olarak MEF tarafından oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="4e166-217">Instead, a class is implicitly created by MEF with properties based on the names of the metadata provided.</span></span>  <span data-ttu-id="4e166-218">(MEF meta verilerine erişmek için çeşitli yollardan budur.)</span><span class="sxs-lookup"><span data-stu-id="4e166-218">(This is one of several ways to access metadata in MEF.)</span></span>  
  
 <span data-ttu-id="4e166-219">MEF bileşimiyse *özyinelemeli*.</span><span class="sxs-lookup"><span data-stu-id="4e166-219">Composition in MEF is *recursive*.</span></span> <span data-ttu-id="4e166-220">Açık olarak oluşturdunuz `Program` içeri aktarılan nesne bir `ICalculator` , türü dönüştü `MySimpleCalculator`.</span><span class="sxs-lookup"><span data-stu-id="4e166-220">You explicitly composed the `Program` object, which imported an `ICalculator` that turned out to be of type `MySimpleCalculator`.</span></span>  <span data-ttu-id="4e166-221">`MySimpleCalculator`, sırasıyla bir koleksiyonunu alır `IOperation` nesneleri ve Al ne zaman doldurulur `MySimpleCalculator` aktarımlarının aynı zamanda oluşturulan `Program`.</span><span class="sxs-lookup"><span data-stu-id="4e166-221">`MySimpleCalculator`, in turn, imports a collection of `IOperation` objects, and that import will be filled when `MySimpleCalculator` is created, at the same time as the imports of `Program`.</span></span> <span data-ttu-id="4e166-222">Varsa `Add` sınıf bildirilen çok doldurulması ve böyle devam etmesi gereken başka bir alma.</span><span class="sxs-lookup"><span data-stu-id="4e166-222">If the `Add` class declared a further import, that too would have to be filled, and so on.</span></span> <span data-ttu-id="4e166-223">Herhangi bir birleşim hatası sol doldurulmamış sonuçları alın.</span><span class="sxs-lookup"><span data-stu-id="4e166-223">Any import left unfilled results in a composition error.</span></span>  <span data-ttu-id="4e166-224">(Ancak, içeri aktarmalar isteğe bağlı veya varsayılan değerleri atamak için bildirmek için mümkündür.)</span><span class="sxs-lookup"><span data-stu-id="4e166-224">(It is possible, however, to declare imports to be optional or to assign them default values.)</span></span>  
  
<a name="calculator_logic"></a>   
## <a name="calculator-logic"></a><span data-ttu-id="4e166-225">Hesaplayıcı mantığı</span><span class="sxs-lookup"><span data-stu-id="4e166-225">Calculator Logic</span></span>  
 <span data-ttu-id="4e166-226">Bu bölümleri yerinde, kalan tek şey hesaplayıcı mantığı.</span><span class="sxs-lookup"><span data-stu-id="4e166-226">With these parts in place, all that remains is the calculator logic itself.</span></span> <span data-ttu-id="4e166-227">Aşağıdaki kodu ekleyin `MySimpleCalculator` uygulamak için sınıf `Calculate` yöntemi:</span><span class="sxs-lookup"><span data-stu-id="4e166-227">Add the following code in the `MySimpleCalculator` class to implement the `Calculate` method:</span></span>  
  
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
  
 <span data-ttu-id="4e166-228">Sol ve sağ işlenen giriş dizeye ve bir işleç karakter başlangıç adımları ayrıştırır.</span><span class="sxs-lookup"><span data-stu-id="4e166-228">The initial steps parse the input string into left and right operands and an operator character.</span></span>  <span data-ttu-id="4e166-229">İçinde `foreach` döngü, her üyesi `operations` koleksiyonu incelenir.</span><span class="sxs-lookup"><span data-stu-id="4e166-229">In the `foreach` loop, every member of the `operations` collection is examined.</span></span> <span data-ttu-id="4e166-230">Bu nesnelerin türündedir <xref:System.Lazy%602>, ve meta veri değerleri ve dışarı aktarılan nesne ile erişilebilir <xref:System.Lazy%602.Metadata%2A> özelliği ve <xref:System.Lazy%601.Value%2A> özelliği sırasıyla.</span><span class="sxs-lookup"><span data-stu-id="4e166-230">These objects are of type <xref:System.Lazy%602>, and their metadata values and exported object can be accessed with the <xref:System.Lazy%602.Metadata%2A> property and the <xref:System.Lazy%601.Value%2A> property respectively.</span></span> <span data-ttu-id="4e166-231">Bu durumda, `Symbol` özelliği `IOperationData` nesne bulunan hesaplayıcı çağrıları bir eşleşme olarak `Operate` yöntemi `IOperation` nesne ve sonucu döndürür.</span><span class="sxs-lookup"><span data-stu-id="4e166-231">In this case, if the `Symbol` property of the `IOperationData` object is discovered to be a match, the calculator calls the `Operate` method of the `IOperation` object and returns the result.</span></span>  
  
 <span data-ttu-id="4e166-232">Hesaplayıcı tamamlamak için ayrıca ilk karakterin rakam olmayan bir dize döndürür yardımcı yöntemi gerekir.</span><span class="sxs-lookup"><span data-stu-id="4e166-232">To complete the calculator, you also need a helper method that returns the position of the first non-digit character in a string.</span></span>  <span data-ttu-id="4e166-233">Aşağıdaki yardımcı yöntemi ekleyin `MySimpleCalculator` sınıfı:</span><span class="sxs-lookup"><span data-stu-id="4e166-233">Add the following helper method to the `MySimpleCalculator` class:</span></span>  
  
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
  
 <span data-ttu-id="4e166-234">Artık derlemek ve projeyi çalıştırmak mümkün olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="4e166-234">You should now be able to compile and run the project.</span></span> <span data-ttu-id="4e166-235">Visual Basic'te, eklediğiniz emin olun `Public` anahtar `Module1`.</span><span class="sxs-lookup"><span data-stu-id="4e166-235">In Visual Basic, make sure that you added the `Public` keyword to `Module1`.</span></span> <span data-ttu-id="4e166-236">Konsol penceresinde "5 + 3" gibi bir toplama işlemi yazın ve hesaplayıcı sonuçları döndürür.</span><span class="sxs-lookup"><span data-stu-id="4e166-236">In the console window, type an addition operation, such as "5+3", and the calculator will return the results.</span></span>  <span data-ttu-id="4e166-237">Herhangi bir işleç "işlemi bulunamadı!" neden olur</span><span class="sxs-lookup"><span data-stu-id="4e166-237">Any other operator will result in the "Operation Not Found!"</span></span> <span data-ttu-id="4e166-238">İleti.</span><span class="sxs-lookup"><span data-stu-id="4e166-238">message.</span></span>  
  
<a name="extending_simplecalculator_using_a_new_class"></a>   
## <a name="extending-simplecalculator-using-a-new-class"></a><span data-ttu-id="4e166-239">Yeni bir sınıf kullanarak SimpleCalculator'ı genişletme</span><span class="sxs-lookup"><span data-stu-id="4e166-239">Extending SimpleCalculator Using A New Class</span></span>  
 <span data-ttu-id="4e166-240">Hesaplayıcı çalışır, yeni bir işlem eklemek kolaydır.</span><span class="sxs-lookup"><span data-stu-id="4e166-240">Now that the calculator works, adding a new operation is easy.</span></span> <span data-ttu-id="4e166-241">Aşağıdaki sınıf modülüne ekleyin veya `SimpleCalculator` ad alanı:</span><span class="sxs-lookup"><span data-stu-id="4e166-241">Add the following class to the module or `SimpleCalculator` namespace:</span></span>  
  
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
  
 <span data-ttu-id="4e166-242">Derleme ve projeyi çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="4e166-242">Compile and run the project.</span></span> <span data-ttu-id="4e166-243">"5-3" gibi bir çıkarma işlemi yazın.</span><span class="sxs-lookup"><span data-stu-id="4e166-243">Type a subtraction operation, such as "5-3".</span></span> <span data-ttu-id="4e166-244">Hesaplayıcı artık çıkarma yanı sıra eklenmesini destekler.</span><span class="sxs-lookup"><span data-stu-id="4e166-244">The calculator now supports subtraction as well as addition.</span></span>  
  
<a name="extending_simplecalculator_using_a_new_assembly"></a>   
## <a name="extending-simplecalculator-using-a-new-assembly"></a><span data-ttu-id="4e166-245">Yeni bir derleme kullanarak SimpleCalculator'ı genişletme</span><span class="sxs-lookup"><span data-stu-id="4e166-245">Extending SimpleCalculator Using A New Assembly</span></span>  
 <span data-ttu-id="4e166-246">Sınıf ekleme kaynak kod yetecek kadar basittir ancak MEF bölümleri için dışında bir uygulamanın kendi kaynak konum olanağı sağlar.</span><span class="sxs-lookup"><span data-stu-id="4e166-246">Adding classes to the source code is simple enough, but MEF provides the ability to look outside an application’s own source for parts.</span></span> <span data-ttu-id="4e166-247">Bunu göstermek için SimpleCalculator ekleyerek bölümleri, kendi derlemesiyle yanı sıra, bir dizin aramak için değiştirmeniz gerekecektir bir <xref:System.ComponentModel.Composition.Hosting.DirectoryCatalog>.</span><span class="sxs-lookup"><span data-stu-id="4e166-247">To demonstrate this, you will need to modify SimpleCalculator to search a directory, as well as its own assembly, for parts, by adding a <xref:System.ComponentModel.Composition.Hosting.DirectoryCatalog>.</span></span>  
  
 <span data-ttu-id="4e166-248">Adlı yeni bir dizin ekleme `Extensions` SimpleCalculator projesine.</span><span class="sxs-lookup"><span data-stu-id="4e166-248">Add a new directory named `Extensions` to the SimpleCalculator project.</span></span>  <span data-ttu-id="4e166-249">Proje düzeyinde ve çözüm düzeyinde eklediğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="4e166-249">Make sure to add it at the project level, and not at the solution level.</span></span> <span data-ttu-id="4e166-250">Ardından yeni bir sınıf kitaplığı proje adlı çözüme ekleyin `ExtendedOperations`.</span><span class="sxs-lookup"><span data-stu-id="4e166-250">Then add a new Class Library project to the solution, named `ExtendedOperations`.</span></span> <span data-ttu-id="4e166-251">Yeni proje ayrı bir derleme derlenir.</span><span class="sxs-lookup"><span data-stu-id="4e166-251">The new project will compile into a separate assembly.</span></span>  
  
 <span data-ttu-id="4e166-252">ExtendedOperations projesi için proje özelliklerini Tasarımcısı'nı açın ve'ı tıklatın **derleme** veya **yapı** sekmesi. Değişiklik **yapı çıkış yolu** veya **çıkış yolu** SimpleCalculator proje dizininde uzantıları dizinine işaret edecek şekilde (.. \SimpleCalculator\Extensions\\).</span><span class="sxs-lookup"><span data-stu-id="4e166-252">Open the Project Properties Designer for the ExtendedOperations project and click the **Compile** or **Build** tab. Change the **Build output path** or **Output path** to point to the Extensions directory in the SimpleCalculator project directory (..\SimpleCalculator\Extensions\\).</span></span>  
  
 <span data-ttu-id="4e166-253">Module1.vb veya Program.cs içinde aşağıdaki satırı ekleyin `Program` Oluşturucusu:</span><span class="sxs-lookup"><span data-stu-id="4e166-253">In Module1.vb or Program.cs, add the following line to the `Program` constructor:</span></span>  
  
```vb  
catalog.Catalogs.Add(New DirectoryCatalog("C:\SimpleCalculator\SimpleCalculator\Extensions"))  
```  
  
```csharp  
catalog.Catalogs.Add(new DirectoryCatalog("C:\\SimpleCalculator\\SimpleCalculator\\Extensions"));  
```  
  
 <span data-ttu-id="4e166-254">Örnek yolu Extensions dizini yolu değiştirin.</span><span class="sxs-lookup"><span data-stu-id="4e166-254">Replace the example path with the path to your Extensions directory.</span></span>  <span data-ttu-id="4e166-255">(Bu mutlak hata ayıklama amacıyla yalnızca yoludur.</span><span class="sxs-lookup"><span data-stu-id="4e166-255">(This absolute path is for debugging purposes only.</span></span>  <span data-ttu-id="4e166-256">Bir üretim uygulamasında, göreli bir yol kullanırsınız.) <xref:System.ComponentModel.Composition.Hosting.DirectoryCatalog> Kapsayıcının uzantıları dizindeki tüm derlemelerde bulunan tüm bölümler şimdi ekleyeceksiniz.</span><span class="sxs-lookup"><span data-stu-id="4e166-256">In a production application, you would use a relative path.) The <xref:System.ComponentModel.Composition.Hosting.DirectoryCatalog> will now add any parts found in any assemblies in the Extensions directory to the composition container.</span></span>  
  
 <span data-ttu-id="4e166-257">ExtendedOperations projede başvuruları SimpleCalculator ve System.ComponentModel.Composition ekleyin.</span><span class="sxs-lookup"><span data-stu-id="4e166-257">In the ExtendedOperations project, add references to SimpleCalculator and System.ComponentModel.Composition.</span></span> <span data-ttu-id="4e166-258">ExtendedOperations sınıf dosyası ekleyin bir `Imports` veya `using` System.ComponentModel.Composition bildirimi.</span><span class="sxs-lookup"><span data-stu-id="4e166-258">In the ExtendedOperations class file, add an `Imports` or a `using` statement for System.ComponentModel.Composition.</span></span> <span data-ttu-id="4e166-259">Visual Basic'te de eklemeniz bir `Imports` SimpleCalculator deyimi.</span><span class="sxs-lookup"><span data-stu-id="4e166-259">In Visual Basic, also add an `Imports` statement for SimpleCalculator.</span></span> <span data-ttu-id="4e166-260">Daha sonra aşağıdaki sınıf ExtendedOperations sınıfı dosyaya ekleyin:</span><span class="sxs-lookup"><span data-stu-id="4e166-260">Then add the following class to the ExtendedOperations class file:</span></span>  
  
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
  
 <span data-ttu-id="4e166-261">Bu da sipariş eşleşecek şekilde sözleşme için Not <xref:System.ComponentModel.Composition.ExportAttribute> özniteliği, aynı türde olmalıdır <xref:System.ComponentModel.Composition.ImportAttribute>.</span><span class="sxs-lookup"><span data-stu-id="4e166-261">Note that in order for the contract to match, the <xref:System.ComponentModel.Composition.ExportAttribute> attribute must have the same type as the <xref:System.ComponentModel.Composition.ImportAttribute>.</span></span>  
  
 <span data-ttu-id="4e166-262">Derleme ve projeyi çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="4e166-262">Compile and run the project.</span></span> <span data-ttu-id="4e166-263">Yeni Mod (%) işleci sınayın.</span><span class="sxs-lookup"><span data-stu-id="4e166-263">Test the new Mod (%) operator.</span></span>  
  
<a name="conclusion"></a>   
## <a name="conclusion"></a><span data-ttu-id="4e166-264">Sonuç</span><span class="sxs-lookup"><span data-stu-id="4e166-264">Conclusion</span></span>  
 <span data-ttu-id="4e166-265">Bu konuda MEF temel kavramlarını ele.</span><span class="sxs-lookup"><span data-stu-id="4e166-265">This topic covered the basic concepts of MEF.</span></span>  
  
-   <span data-ttu-id="4e166-266">Parça, kataloglar ve kapsayıcının</span><span class="sxs-lookup"><span data-stu-id="4e166-266">Parts, catalogs, and the composition container</span></span>  
  
     <span data-ttu-id="4e166-267">Bölümleri ve kapsayıcının bir MEF uygulamasının temel yapı taşlarının var.</span><span class="sxs-lookup"><span data-stu-id="4e166-267">Parts and the composition container are the basic building blocks of a MEF application.</span></span> <span data-ttu-id="4e166-268">Alır ya da yukarı kendisi de dahil bir değer verir herhangi bir nesne bir parçasıdır.</span><span class="sxs-lookup"><span data-stu-id="4e166-268">A part is any object that imports or exports a value, up to and including itself.</span></span> <span data-ttu-id="4e166-269">Bir katalog belirli bir kaynaktan kısımlarının bir koleksiyonunu sağlar.</span><span class="sxs-lookup"><span data-stu-id="4e166-269">A catalog provides a collection of parts from a particular source.</span></span>  <span data-ttu-id="4e166-270">Kapsayıcının birleşim, içeri aktarmalar dışarı bağlama gerçekleştirmek için bir katalog tarafından sağlanan bölümleri kullanır.</span><span class="sxs-lookup"><span data-stu-id="4e166-270">The composition container uses the parts provided by a catalog to perform composition, the binding of imports to exports.</span></span>  
  
-   <span data-ttu-id="4e166-271">İçeri ve dışarı aktarmalar</span><span class="sxs-lookup"><span data-stu-id="4e166-271">Imports and exports</span></span>  
  
     <span data-ttu-id="4e166-272">İçeri ve dışarı aktarmalar olarak bileşenleri iletişim yoludur.</span><span class="sxs-lookup"><span data-stu-id="4e166-272">Imports and exports are the way by which components communicate.</span></span> <span data-ttu-id="4e166-273">Bir alma ile belirli bir değer veya nesne gereksinimini bileşeni belirtir ve isteğe bağlı olarak verme ile bir değer kullanılabilirliğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="4e166-273">With an import, the component specifies a need for a particular value or object, and with an export it specifies the availability of a value.</span></span> <span data-ttu-id="4e166-274">Her içeri aktarma, dışarı sözleşmesi yapmamanız listesiyle eşleştirilir.</span><span class="sxs-lookup"><span data-stu-id="4e166-274">Each import is matched with a list of exports by way of its contract.</span></span>  
  
<a name="where_do_i_go_now"></a>   
## <a name="where-do-i-go-now"></a><span data-ttu-id="4e166-275">I şimdi nereye?</span><span class="sxs-lookup"><span data-stu-id="4e166-275">Where Do I Go Now?</span></span>  
 <span data-ttu-id="4e166-276">Bu örneğin tam kodu indirmek için bkz: [SimpleCalculator örnek](http://code.msdn.microsoft.com/windowsdesktop/Simple-Calculator-MEF-1152654e).</span><span class="sxs-lookup"><span data-stu-id="4e166-276">To download the complete code for this example, see the [SimpleCalculator sample](http://code.msdn.microsoft.com/windowsdesktop/Simple-Calculator-MEF-1152654e).</span></span>  
  
 <span data-ttu-id="4e166-277">Daha fazla bilgi ve kod örnekleri için bkz: [Genişletilebilirlik Çerçevesi ile yönetilen](http://go.microsoft.com/fwlink/?LinkId=144282).</span><span class="sxs-lookup"><span data-stu-id="4e166-277">For more information and code examples, see [Managed Extensibility Framework](http://go.microsoft.com/fwlink/?LinkId=144282).</span></span> <span data-ttu-id="4e166-278">MEF türlerinin listesi için bkz: <xref:System.ComponentModel.Composition?displayProperty=nameWithType> ad alanı.</span><span class="sxs-lookup"><span data-stu-id="4e166-278">For a list of the MEF types, see the <xref:System.ComponentModel.Composition?displayProperty=nameWithType> namespace.</span></span>
