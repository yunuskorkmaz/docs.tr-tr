---
title: "ASP.NET Core ve Azure ile Mimarı modern web uygulamaları"
description: "ASP.NET Core ve Azure ile modern Web uygulamaları mimari | Giriş"
author: ardalis
ms.author: wiwagn
ms.date: 10/06/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.openlocfilehash: 93a74bb7ba537d3c7c0291f7903112dc470133a7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="architect-modern-web-applications-with-aspnet-core-and-azure"></a><span data-ttu-id="1fe00-103">ASP.NET Core ve Azure ile Mimarı Modern Web uygulamaları</span><span class="sxs-lookup"><span data-stu-id="1fe00-103">Architect Modern Web Applications with ASP.NET Core and Azure</span></span>

<span data-ttu-id="1fe00-104">.NET core ve ASP.NET Core geleneksel .NET geliştirme birkaç avantaj sunar.</span><span class="sxs-lookup"><span data-stu-id="1fe00-104">.NET Core and ASP.NET Core offer several advantages over traditional .NET development.</span></span> <span data-ttu-id="1fe00-105">Aşağıdaki tümünün veya uygulamanızın başarısı için önemli olan ise, sunucu uygulamaları için .NET Core kullanmanız gerekir:</span><span class="sxs-lookup"><span data-stu-id="1fe00-105">You should use .NET Core for your server applications if some or all of the following are important to your application's success:</span></span>

-   <span data-ttu-id="1fe00-106">Platformlar arası desteği</span><span class="sxs-lookup"><span data-stu-id="1fe00-106">Cross-platform support</span></span>

-   <span data-ttu-id="1fe00-107">Mikro kullanımı</span><span class="sxs-lookup"><span data-stu-id="1fe00-107">Use of microservices</span></span>

-   <span data-ttu-id="1fe00-108">Docker kapsayıcıları kullanma</span><span class="sxs-lookup"><span data-stu-id="1fe00-108">Use of Docker containers</span></span>

-   <span data-ttu-id="1fe00-109">Yüksek performans ve ölçeklenebilirlik gereksinimleri</span><span class="sxs-lookup"><span data-stu-id="1fe00-109">High performance and scalability requirements</span></span>

-   <span data-ttu-id="1fe00-110">Aynı sunucuda bir uygulama tarafından .NET sürümlerinin yan yana sürüm oluşturma</span><span class="sxs-lookup"><span data-stu-id="1fe00-110">Side-by-side versioning of .NET versions by application on the same server</span></span>

<span data-ttu-id="1fe00-111">Geleneksel .NET uygulamaları yapın ve bu gereksinimleri desteklemesi ancak yukarıdaki senaryoları için geliştirilmiş destek sunmak için ASP.NET Core ve .NET Core getirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="1fe00-111">Traditional .NET applications can and do support these requirements, but ASP.NET Core and .NET Core have been optimized to offer improved support for the above scenarios.</span></span>

<span data-ttu-id="1fe00-112">Microsoft Azure gibi hizmetler kullanarak bulutta web uygulamalarını barındırmak daha da fazla kuruluşlar seçim.</span><span class="sxs-lookup"><span data-stu-id="1fe00-112">More and more organizations are choosing to host their web applications in the cloud using services like Microsoft Azure.</span></span> <span data-ttu-id="1fe00-113">Aşağıdakiler, uygulama veya kuruluşunuz için önemliyse, uygulamanızda bulut barındırma dikkate almanız gerekir:</span><span class="sxs-lookup"><span data-stu-id="1fe00-113">You should consider hosting your application in the cloud if the following are important to your application or organization:</span></span>

-   <span data-ttu-id="1fe00-114">Azaltılmış yatırım veri merkezi maliyetlerini (donanım, yazılım, boşluk, yardımcı programlar, vb.)</span><span class="sxs-lookup"><span data-stu-id="1fe00-114">Reduced investment in data center costs (hardware, software, space, utilities, etc)</span></span>

-   <span data-ttu-id="1fe00-115">(Kullanım için boşta kapasite göre ödeme) fiyatlandırma esnek</span><span class="sxs-lookup"><span data-stu-id="1fe00-115">Flexible pricing (pay based on usage, not for idle capacity)</span></span>

-   <span data-ttu-id="1fe00-116">Extreme güvenilirlik</span><span class="sxs-lookup"><span data-stu-id="1fe00-116">Extreme reliability</span></span>

-   <span data-ttu-id="1fe00-117">Geliştirilmiş uygulama mobility; kolayca değiştirmek, uygulamanızın nerede ve nasıl dağıtılır</span><span class="sxs-lookup"><span data-stu-id="1fe00-117">Improved app mobility; easily change where and how your app is deployed</span></span>

-   <span data-ttu-id="1fe00-118">Esnek Kapasite; Yukarı veya aşağı göre gerçek gereksinimlerini ölçeklendirme</span><span class="sxs-lookup"><span data-stu-id="1fe00-118">Flexible capacity; scale up or down based on actual needs</span></span>

<span data-ttu-id="1fe00-119">Microsoft Azure üzerinde barındırılan ASP.NET Core ile Web uygulamaları oluşturmak, geleneksel alternatifleri çok sayıda rekabet avantaj sunar.</span><span class="sxs-lookup"><span data-stu-id="1fe00-119">Building web applications with ASP.NET Core, hosted in Microsoft Azure, offers numerous competitive advantages over traditional alternatives.</span></span> <span data-ttu-id="1fe00-120">ASP.NET Core modern web uygulaması geliştirme uygulamaları ve bulut barındırma senaryolarında için optimize edilmiştir.</span><span class="sxs-lookup"><span data-stu-id="1fe00-120">ASP.NET Core is optimized for modern web application development practices and cloud hosting scenarios.</span></span> <span data-ttu-id="1fe00-121">Bu kılavuzda, bu özellikler en iyi şekilde yararlanmak için ASP.NET Core uygulamaları mimari öğreneceksiniz.</span><span class="sxs-lookup"><span data-stu-id="1fe00-121">In this guide, you will learn how to architect your ASP.NET Core applications to best take advantage of these capabilities.</span></span>

## <a name="purpose"></a><span data-ttu-id="1fe00-122">Amaç</span><span class="sxs-lookup"><span data-stu-id="1fe00-122">Purpose</span></span>

<span data-ttu-id="1fe00-123">Bu kılavuz, ASP.NET Core ve Azure kullanarak tek yapılı web uygulamaları geliştirmek uçtan uca yönergeler sağlar.</span><span class="sxs-lookup"><span data-stu-id="1fe00-123">This guide provides end-to-end guidance on building monolithic web applications using ASP.NET Core and Azure.</span></span>

<span data-ttu-id="1fe00-124">Bu kılavuz için tamamlayıcı "*Architecting ve geliştirme kapsayıcılı ve .NET mikro hizmet tabanlı uygulamalarla*" hangi odaklanır daha fazla üzerinde Docker, mikro ve dağıtım, kapsayıcıları konak kuruluş uygulamalar.</span><span class="sxs-lookup"><span data-stu-id="1fe00-124">This guide is complementary to the "*Architecting and Developing Containerized and Microservice-based Applications with .NET*" which focuses more on Docker, Microservices, and Deployment of Containers to host enterprise applications.</span></span>

> ### <a name="architecting-and-developing-containerized-microservice-based-apps-in-net"></a><span data-ttu-id="1fe00-125">Mimariden ve kapsayıcılı mikro hizmet geliştirirken .NET uygulamalarında dayalı</span><span class="sxs-lookup"><span data-stu-id="1fe00-125">Architecting and Developing Containerized Microservice Based Apps in .NET</span></span>
> - <span data-ttu-id="1fe00-126">**e-kitap**</span><span class="sxs-lookup"><span data-stu-id="1fe00-126">**e-book**</span></span>  
> <span data-ttu-id="1fe00-127"><http://aka.MS/MicroservicesEbook></span><span class="sxs-lookup"><span data-stu-id="1fe00-127"><http://aka.ms/MicroservicesEbook></span></span>
> - <span data-ttu-id="1fe00-128">**Örnek uygulama**</span><span class="sxs-lookup"><span data-stu-id="1fe00-128">**Sample Application**</span></span>  
> <span data-ttu-id="1fe00-129"><http://aka.MS/microservicesarchitecture></span><span class="sxs-lookup"><span data-stu-id="1fe00-129"><http://aka.ms/microservicesarchitecture></span></span>

## <a name="who-should-use-this-guide"></a><span data-ttu-id="1fe00-130">Bu kılavuz kullanan</span><span class="sxs-lookup"><span data-stu-id="1fe00-130">Who should use this guide</span></span>

<span data-ttu-id="1fe00-131">Bu kılavuzda kitlesi çoğunlukla geliştiriciler, geliştirme müşteri adayları ve bulutta Microsoft teknolojileri ve hizmetleri kullanan modern web uygulamaları oluşturmaya ilgi duyan mimarlar içindir.</span><span class="sxs-lookup"><span data-stu-id="1fe00-131">The audience for this guide is mainly developers, development leads, and architects who are interested in building modern web applications using Microsoft technologies and services in the cloud.</span></span>

<span data-ttu-id="1fe00-132">İkincil bir dinleyici zaten bilinen ASP.NET ve/veya Azure ve yeni veya mevcut projeleri için ASP.NET Core yükseltmek için anlam olup olmadığı hakkında bilgi mi arıyorsunuz teknik karar alıcılar ' dir.</span><span class="sxs-lookup"><span data-stu-id="1fe00-132">A secondary audience is technical decision makers who are already familiar ASP.NET and/or Azure and are looking for information on whether it makes sense to upgrade to ASP.NET Core for new or existing projects.</span></span>

## <a name="how-you-can-use-this-guide"></a><span data-ttu-id="1fe00-133">Bu kılavuz nasıl kullanabileceğiniz</span><span class="sxs-lookup"><span data-stu-id="1fe00-133">How you can use this guide</span></span>

<span data-ttu-id="1fe00-134">Bu kılavuz, modern .NET teknolojileri ve Windows Azure ile web uygulamaları oluşturmaya odaklanan görece küçük bir belgeye sıkıştırılmış.</span><span class="sxs-lookup"><span data-stu-id="1fe00-134">This guide has been condensed into a relatively small document that focuses on building web applications with modern .NET technologies and Windows Azure.</span></span> <span data-ttu-id="1fe00-135">Bu nedenle, bu tür uygulamalar ve bunların teknik konular anlamanın bir temel tamamının okunabilir.</span><span class="sxs-lookup"><span data-stu-id="1fe00-135">As such, it can be read in its entirety to provide a foundation of understanding such applications and their technical considerations.</span></span> <span data-ttu-id="1fe00-136">Kendi örnek uygulama ile birlikte kılavuzu ayrıca bir başlangıç noktası veya başvuru hizmet verebilir.</span><span class="sxs-lookup"><span data-stu-id="1fe00-136">The guide, along with its sample application, can also serve as a starting point or reference.</span></span> <span data-ttu-id="1fe00-137">İlişkili örnek uygulaması, kendi uygulamalar için veya uygulamanızın bileşen parçalarını nasıl düzenleyebileceğini görmek için bir şablon olarak kullanın.</span><span class="sxs-lookup"><span data-stu-id="1fe00-137">Use the associated sample application as a template for your own applications, or to see how you might organize your application's component parts.</span></span> <span data-ttu-id="1fe00-138">Geri kılavuz ilkeleri ve kapsamı mimarisi ve teknoloji seçenekleri ve karar dikkat edilecek noktalar, kendi uygulama için bu seçeneklerin başvuracaklarını zaman bakın.</span><span class="sxs-lookup"><span data-stu-id="1fe00-138">Refer back to the guide's principles and coverage of architecture and technology options and decision considerations when weighing these choices for your own application.</span></span>

<span data-ttu-id="1fe00-139">Bu konuları ve fırsatlar genel olarak anlaşılmasını sağlamak için bu kılavuzu ekibinize iletmek çekinmeyin.</span><span class="sxs-lookup"><span data-stu-id="1fe00-139">Feel free to forward this guide to your team to help ensure a common understanding of these considerations and opportunities.</span></span> <span data-ttu-id="1fe00-140">Herkes ortak bir dizi terminolojisi çalışma ve ilkeleri temelindeki sahip mimari desenleri ve uygulamalar tutarlı uygulama sağlamaya yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="1fe00-140">Having everybody working from a common set of terminology and underlying principles will help ensure consistent application of architectural patterns and practices.</span></span>

## <a name="references"></a><span data-ttu-id="1fe00-141">Referanslar</span><span class="sxs-lookup"><span data-stu-id="1fe00-141">References</span></span>
- <span data-ttu-id="1fe00-142">**Sunucu uygulamaları için .NET Core ve .NET Framework arasında seçim yapma**</span><span class="sxs-lookup"><span data-stu-id="1fe00-142">**Choosing between .NET Core and .NET Framework for server apps**</span></span>  
<span data-ttu-id="1fe00-143"><https://docs.microsoft.com/dotnet/articles/Standard/choosing-Core-Framework-Server></span><span class="sxs-lookup"><span data-stu-id="1fe00-143"><https://docs.microsoft.com/dotnet/articles/standard/choosing-core-framework-server></span></span>

>[!div class="step-by-step"]
<span data-ttu-id="1fe00-144">[Sonraki] (modern-web-uygulamalar-characteristics.md)</span><span class="sxs-lookup"><span data-stu-id="1fe00-144">[Next] (modern-web-applications-characteristics.md)</span></span>
