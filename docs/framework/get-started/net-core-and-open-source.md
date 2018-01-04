---
title: ".NET Core ve Açık Kaynak"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e6bd4655-ce37-4003-8462-468a6fe2c40f
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: cc41a51a9c85b84f2f5365eb1650ebec37888652
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="net-core-and-open-source"></a><span data-ttu-id="a9955-102">.NET Core ve Açık Kaynak</span><span class="sxs-lookup"><span data-stu-id="a9955-102">.NET Core and Open-Source</span></span>
<span data-ttu-id="a9955-103">Bu konuda ne .NET Core olduğu ve nasıl daha fazla bilgi bulabilirsiniz gösterir kısa bir genel bakış sağlar.</span><span class="sxs-lookup"><span data-stu-id="a9955-103">This topic provides a brief overview  of what .NET Core is and shows how you can find more information.</span></span> <span data-ttu-id="a9955-104">.NET Core konuları tam listesi için ziyaret edin [.NET Core Kılavuzu](../../core/index.md).</span><span class="sxs-lookup"><span data-stu-id="a9955-104">To find the complete list of topics for .NET Core, visit the [.NET Core Guide](../../core/index.md).</span></span>
  
<a name="BKMK_WhatisNETCore"></a>   
## <a name="what-is-net-core"></a><span data-ttu-id="a9955-105">.NET Core nedir?</span><span class="sxs-lookup"><span data-stu-id="a9955-105">What is .NET Core?</span></span>  
 <span data-ttu-id="a9955-106">.NET core genel amaçlı, modüler, platformlar arası ve açık kaynak uygulaması .NET standart olur.</span><span class="sxs-lookup"><span data-stu-id="a9955-106">.NET Core is a general purpose, modular, cross-platform and open source implementation of the .NET Standard.</span></span> <span data-ttu-id="a9955-107">.NET Framework ile aynı API'ler çoğunu içerir (ancak .NET Core kümesidir daha küçük) ve çeşitli işletim sistemlerini destekleyen ve yonga hedefleri çalışma zamanı, framework, derleyici ve araçları bileşenleri içerir.</span><span class="sxs-lookup"><span data-stu-id="a9955-107">It contains many of the same APIs as the .NET Framework (but .NET Core is a smaller set) and includes runtime, framework, compiler and tools components that support a variety of operating systems and chip targets.</span></span> <span data-ttu-id="a9955-108">.NET Core uygulama öncelikli olarak ASP.NET Core iş yükleri de gerektiğinden gereksiniminden ve daha modern uygulama işlemleriniz.</span><span class="sxs-lookup"><span data-stu-id="a9955-108">The .NET Core implementation was primarily driven by the ASP.NET Core workloads but also by the need and desire to have a more modern implementation.</span></span> <span data-ttu-id="a9955-109">Cihaz, Bulut ve katıştırılmış IOT senaryolarını kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="a9955-109">It can be used in device, cloud and embedded/IoT scenarios.</span></span>  
  
 <span data-ttu-id="a9955-110">.NET Core'u kullanmaya başlamak için lütfen ziyaret [.NET Core giriş sayfası](https://www.microsoft.com/net/core).</span><span class="sxs-lookup"><span data-stu-id="a9955-110">To get started with .NET Core, please visit the [.NET Core homepage](https://www.microsoft.com/net/core).</span></span>  
  
 <span data-ttu-id="a9955-111">.NET Core temel özellikleri aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="a9955-111">Here are the main characteristics of .NET Core:</span></span>  
  
-   <span data-ttu-id="a9955-112">**Platformlar arası:** .NET Core gerekir ve bu kod, platform hedefi bağımsız olarak yeniden uygulama özelliklerini uygulamak için anahtar işlevselliği sağlar.</span><span class="sxs-lookup"><span data-stu-id="a9955-112">**Cross-platform:** .NET Core provides key functionality to implement the app features you need and reuse this code regardless of your platform target.</span></span> <span data-ttu-id="a9955-113">Şu anda üç ana işletim sistemlerini (OS) desteklemektedir: Windows, Linux ve macOS.</span><span class="sxs-lookup"><span data-stu-id="a9955-113">It currently supports three main operating systems (OS): Windows, Linux and macOS.</span></span> <span data-ttu-id="a9955-114">Uygulamalar ve desteklenen işletim sistemleri arasında değiştirilmemiş çalıştırmak kitaplıkları yazabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a9955-114">You can write apps and libraries that run unmodified across supported operating systems.</span></span> <span data-ttu-id="a9955-115">Desteklenen işletim sistemlerinin listesini görmek için ziyaret [.NET Core yol haritası](https://github.com/dotnet/core/blob/master/roadmap.md).</span><span class="sxs-lookup"><span data-stu-id="a9955-115">To see the list of supported operating systems, visit [.NET Core roadmap](https://github.com/dotnet/core/blob/master/roadmap.md).</span></span>
  
-   <span data-ttu-id="a9955-116">**Açık kaynak:** .NET Core Hizmetleri altında çok sayıda proje biridir [.NET Foundation](http://www.dotnetfoundation.org/) ve kullanılabilir [GitHub](https://github.com/).</span><span class="sxs-lookup"><span data-stu-id="a9955-116">**Open source:** .NET Core is one of the many projects under the stewardship of the [.NET Foundation](http://www.dotnetfoundation.org/) and is available on [GitHub](https://github.com/).</span></span>  <span data-ttu-id="a9955-117">.NET Core açık kaynaklı proje olarak daha saydam bir geliştirme sürecinin yükseltir ve etkin ve bağlı bir topluluk yükseltir.</span><span class="sxs-lookup"><span data-stu-id="a9955-117">Having .NET Core as an open source project promotes a more transparent development process and promotes an active and engaged community.</span></span>  
  
-   <span data-ttu-id="a9955-118">**Esnek dağıtım:** uygulamanızı dağıtmak için başlıca iki yolu vardır: framework bağımlı dağıtımı veya kendi içinde bulunan dağıtımı.</span><span class="sxs-lookup"><span data-stu-id="a9955-118">**Flexible deployment:** there are two main ways to deploy your app: framework-dependent deployment or self-contained deployment.</span></span> <span data-ttu-id="a9955-119">Framework bağımlı dağıtım, yalnızca, uygulama ve üçüncü taraf bağımlılıkları yüklenir ve uygulamanızı .NET bulunması için çekirdek sistem genelinde sürümüne bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="a9955-119">With framework-dependent deployment, only your app and third-party dependencies are installed and your app depends on a system-wide version of .NET Core to be present.</span></span>  <span data-ttu-id="a9955-120">Kendi içinde bulunan dağıtım ile uygulamanızı oluşturmak için kullanılan .NET Core sürümü de uygulama ve üçüncü taraf bağımlılıkları ile birlikte dağıtılır ve yan yana çalıştırabilirsiniz diğer sürümleri ile.</span><span class="sxs-lookup"><span data-stu-id="a9955-120">With self-contained deployment, the .NET Core version used to build your application is also deployed along with your app and third-party dependencies and can run side-by-side with other versions.</span></span>    <span data-ttu-id="a9955-121">Daha fazla bilgi için bkz: [.NET Core uygulama dağıtımı](../../core/deploying/index.md).</span><span class="sxs-lookup"><span data-stu-id="a9955-121">For more information, see [.NET Core Application Deployment](../../core/deploying/index.md).</span></span>

-   <span data-ttu-id="a9955-122">**Modüler:** .NET Core olduğundan modüler küçük derleme paketlerinde NuGet yayımlanır.</span><span class="sxs-lookup"><span data-stu-id="a9955-122">**Modular:** .NET Core is modular because it's released through NuGet in smaller assembly packages.</span></span> <span data-ttu-id="a9955-123">Çekirdek işlevselliğini çoğunu içeren bir büyük derleme yerine, .NET Core küçük özelliği merkezli paketleri olarak kullanılabilir hale getirilir.</span><span class="sxs-lookup"><span data-stu-id="a9955-123">Rather than one large assembly that contains most of the core functionality, .NET Core is made available as smaller feature-centric packages.</span></span> <span data-ttu-id="a9955-124">Bu daha Çevik Geliştirme modeli bize sağlar ve yalnızca gereksinim duyduğunuz NuGet paketleri dahil etmek için uygulamanızı en iyi duruma olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="a9955-124">This enables a more agile development model for us and allows you to optimize your app to include just the NuGet packages you need.</span></span> <span data-ttu-id="a9955-125">Hizmet, performans geliştirildi ve ödeme için-what-size-kullanım modeli maliyetlerini azaltılabilir azaltılmış daha sıkı güvenlik, daha küçük bir uygulama yüzey alanını yararları içerir.</span><span class="sxs-lookup"><span data-stu-id="a9955-125">The benefits of a smaller app surface area include tighter security, reduced servicing, improved performance, and decreased costs in a pay-for-what-you-use model.</span></span>  
  
## <a name="the-net-core-platform"></a><span data-ttu-id="a9955-126">.NET Core platformu</span><span class="sxs-lookup"><span data-stu-id="a9955-126">The .NET Core Platform</span></span>  
 <span data-ttu-id="a9955-127">.NET Core platform yönetilen derleyicileri, çalışma zamanı, temel sınıf kitaplıkları ve ASP.NET Core gibi çok sayıda uygulama modelleri içeren çeşitli bileşenlerinin yapılır.</span><span class="sxs-lookup"><span data-stu-id="a9955-127">The .NET Core platform is made of several components, which includes the managed compilers, the runtime, the base class libraries, and numerous application models, such as ASP.NET Core.</span></span> <span data-ttu-id="a9955-128">Farklı bileşenleri hakkında daha fazla bilgi ve, aşağıdaki ziyaret ederek bağlı [GitHub](https://github.com/) depoları:</span><span class="sxs-lookup"><span data-stu-id="a9955-128">You can learn more about the different components and get engaged, by visiting the following [GitHub](https://github.com/) repos:</span></span>  
  
-   [<span data-ttu-id="a9955-129">.NET Core</span><span class="sxs-lookup"><span data-stu-id="a9955-129">.NET Core</span></span>](https://github.com/dotnet/core)  
  
-   [<span data-ttu-id="a9955-130">CoreFX - .NET Core temel kitaplıkları</span><span class="sxs-lookup"><span data-stu-id="a9955-130">CoreFX - .NET Core foundational libraries</span></span>](https://github.com/dotnet/corefx)  
  
-   [<span data-ttu-id="a9955-131">CoreCLR - .NET çekirdeği çalışma zamanı</span><span class="sxs-lookup"><span data-stu-id="a9955-131">CoreCLR - .NET Core runtime</span></span>](https://github.com/dotnet/coreclr)  
  
-   [<span data-ttu-id="a9955-132">CLI - .NET Core komut satırı araçları</span><span class="sxs-lookup"><span data-stu-id="a9955-132">CLI - .NET Core command-line tools</span></span>](https://github.com/dotnet/cli)  
  
-   [<span data-ttu-id="a9955-133">Roslyn - .NET derleyici platformu</span><span class="sxs-lookup"><span data-stu-id="a9955-133">Roslyn - .NET Compiler Platform</span></span>](https://github.com/dotnet/roslyn)  
  
-   [<span data-ttu-id="a9955-134">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="a9955-134">ASP.NET Core</span></span>](https://github.com/aspnet/home)  
  
## <a name="see-also"></a><span data-ttu-id="a9955-135">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="a9955-135">See Also</span></span>  
 [<span data-ttu-id="a9955-136">.NET core giriş sayfası</span><span class="sxs-lookup"><span data-stu-id="a9955-136">.NET Core homepage</span></span>](https://www.microsoft.com/net/core)  
 [<span data-ttu-id="a9955-137">.NET Core Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="a9955-137">.NET Core Guide</span></span>](../../core/index.md)  
 [<span data-ttu-id="a9955-138">ASP.NET Core belgeleri</span><span class="sxs-lookup"><span data-stu-id="a9955-138">ASP.NET Core Documentation</span></span>](/aspnet/core/)
