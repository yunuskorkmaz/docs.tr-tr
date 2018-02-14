---
title: "ASP.NET Core ve Azure ile Mimarı modern web uygulamaları"
description: "ASP.NET Core ve Azure ile modern Web uygulamaları mimari | Giriş"
author: ardalis
ms.author: wiwagn
ms.date: 10/06/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: db9f0ddd875df1f84bcc5681ee1383b0185f8b7e
ms.sourcegitcommit: e2bf8e6bc365bd9a0e86fe81eeae7d14f85f48c1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/13/2018
---
# <a name="architect-modern-web-applications-with-aspnet-core-and-azure"></a><span data-ttu-id="407a1-103">ASP.NET Core ve Azure ile Mimarı Modern Web uygulamaları</span><span class="sxs-lookup"><span data-stu-id="407a1-103">Architect Modern Web Applications with ASP.NET Core and Azure</span></span>

![kapak resmi](./media/cover.jpg)


<span data-ttu-id="407a1-105">.NET core ve ASP.NET Core geleneksel .NET geliştirme birkaç avantaj sunar.</span><span class="sxs-lookup"><span data-stu-id="407a1-105">.NET Core and ASP.NET Core offer several advantages over traditional .NET development.</span></span> <span data-ttu-id="407a1-106">Aşağıdaki tümünün veya uygulamanızın başarısı için önemli olan ise, sunucu uygulamaları için .NET Core kullanmanız gerekir:</span><span class="sxs-lookup"><span data-stu-id="407a1-106">You should use .NET Core for your server applications if some or all of the following are important to your application's success:</span></span>

-   <span data-ttu-id="407a1-107">Platformlar arası desteği</span><span class="sxs-lookup"><span data-stu-id="407a1-107">Cross-platform support</span></span>

-   <span data-ttu-id="407a1-108">Mikro kullanımı</span><span class="sxs-lookup"><span data-stu-id="407a1-108">Use of microservices</span></span>

-   <span data-ttu-id="407a1-109">Docker kapsayıcıları kullanma</span><span class="sxs-lookup"><span data-stu-id="407a1-109">Use of Docker containers</span></span>

-   <span data-ttu-id="407a1-110">Yüksek performans ve ölçeklenebilirlik gereksinimleri</span><span class="sxs-lookup"><span data-stu-id="407a1-110">High performance and scalability requirements</span></span>

-   <span data-ttu-id="407a1-111">Aynı sunucuda bir uygulama tarafından .NET sürümlerinin yan yana sürüm oluşturma</span><span class="sxs-lookup"><span data-stu-id="407a1-111">Side-by-side versioning of .NET versions by application on the same server</span></span>

<span data-ttu-id="407a1-112">Geleneksel .NET uygulamaları yapın ve bu gereksinimleri desteklemesi ancak yukarıdaki senaryoları için geliştirilmiş destek sunmak için ASP.NET Core ve .NET Core getirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="407a1-112">Traditional .NET applications can and do support these requirements, but ASP.NET Core and .NET Core have been optimized to offer improved support for the above scenarios.</span></span>

<span data-ttu-id="407a1-113">Microsoft Azure gibi hizmetler kullanarak bulutta web uygulamalarını barındırmak daha da fazla kuruluşlar seçim.</span><span class="sxs-lookup"><span data-stu-id="407a1-113">More and more organizations are choosing to host their web applications in the cloud using services like Microsoft Azure.</span></span> <span data-ttu-id="407a1-114">Aşağıdakiler, uygulama veya kuruluşunuz için önemliyse, uygulamanızda bulut barındırma dikkate almanız gerekir:</span><span class="sxs-lookup"><span data-stu-id="407a1-114">You should consider hosting your application in the cloud if the following are important to your application or organization:</span></span>

-   <span data-ttu-id="407a1-115">Azaltılmış yatırım veri merkezi maliyetlerini (donanım, yazılım, boşluk, yardımcı programlar, vb.)</span><span class="sxs-lookup"><span data-stu-id="407a1-115">Reduced investment in data center costs (hardware, software, space, utilities, etc)</span></span>

-   <span data-ttu-id="407a1-116">(Kullanım için boşta kapasite göre ödeme) fiyatlandırma esnek</span><span class="sxs-lookup"><span data-stu-id="407a1-116">Flexible pricing (pay based on usage, not for idle capacity)</span></span>

-   <span data-ttu-id="407a1-117">Extreme güvenilirlik</span><span class="sxs-lookup"><span data-stu-id="407a1-117">Extreme reliability</span></span>

-   <span data-ttu-id="407a1-118">Geliştirilmiş uygulama mobility; kolayca değiştirmek, uygulamanızın nerede ve nasıl dağıtılır</span><span class="sxs-lookup"><span data-stu-id="407a1-118">Improved app mobility; easily change where and how your app is deployed</span></span>

-   <span data-ttu-id="407a1-119">Esnek Kapasite; Yukarı veya aşağı göre gerçek gereksinimlerini ölçeklendirme</span><span class="sxs-lookup"><span data-stu-id="407a1-119">Flexible capacity; scale up or down based on actual needs</span></span>

<span data-ttu-id="407a1-120">Microsoft Azure üzerinde barındırılan ASP.NET Core ile Web uygulamaları oluşturmak, geleneksel alternatifleri çok sayıda rekabet avantaj sunar.</span><span class="sxs-lookup"><span data-stu-id="407a1-120">Building web applications with ASP.NET Core, hosted in Microsoft Azure, offers numerous competitive advantages over traditional alternatives.</span></span> <span data-ttu-id="407a1-121">ASP.NET Core modern web uygulaması geliştirme uygulamaları ve bulut barındırma senaryolarında için optimize edilmiştir.</span><span class="sxs-lookup"><span data-stu-id="407a1-121">ASP.NET Core is optimized for modern web application development practices and cloud hosting scenarios.</span></span> <span data-ttu-id="407a1-122">Bu kılavuzda, bu özellikler en iyi şekilde yararlanmak için ASP.NET Core uygulamaları mimari öğreneceksiniz.</span><span class="sxs-lookup"><span data-stu-id="407a1-122">In this guide, you will learn how to architect your ASP.NET Core applications to best take advantage of these capabilities.</span></span>

## <a name="purpose"></a><span data-ttu-id="407a1-123">Amaç</span><span class="sxs-lookup"><span data-stu-id="407a1-123">Purpose</span></span>

<span data-ttu-id="407a1-124">Bu kılavuz, ASP.NET Core ve Azure kullanarak tek yapılı web uygulamaları geliştirmek uçtan uca yönergeler sağlar.</span><span class="sxs-lookup"><span data-stu-id="407a1-124">This guide provides end-to-end guidance on building monolithic web applications using ASP.NET Core and Azure.</span></span>

<span data-ttu-id="407a1-125">Bu kılavuz için tamamlayıcı "*Architecting ve geliştirme kapsayıcılı ve .NET mikro hizmet tabanlı uygulamalarla*" hangi odaklanır daha fazla üzerinde Docker, mikro ve dağıtım, kapsayıcıları konak kuruluş uygulamalar.</span><span class="sxs-lookup"><span data-stu-id="407a1-125">This guide is complementary to the "*Architecting and Developing Containerized and Microservice-based Applications with .NET*" which focuses more on Docker, Microservices, and Deployment of Containers to host enterprise applications.</span></span>

> ### <a name="architecting-and-developing-containerized-microservice-based-apps-in-net"></a><span data-ttu-id="407a1-126">Mimariden ve kapsayıcılı mikro hizmet geliştirirken .NET uygulamalarında dayalı</span><span class="sxs-lookup"><span data-stu-id="407a1-126">Architecting and Developing Containerized Microservice Based Apps in .NET</span></span>
> - <span data-ttu-id="407a1-127">**e-kitap**</span><span class="sxs-lookup"><span data-stu-id="407a1-127">**e-book**</span></span>  
> <span data-ttu-id="407a1-128"><http://aka.ms/MicroservicesEbook></span><span class="sxs-lookup"><span data-stu-id="407a1-128"><http://aka.ms/MicroservicesEbook></span></span>
> - <span data-ttu-id="407a1-129">**Örnek uygulama**</span><span class="sxs-lookup"><span data-stu-id="407a1-129">**Sample Application**</span></span>  
> <span data-ttu-id="407a1-130"><http://aka.ms/microservicesarchitecture></span><span class="sxs-lookup"><span data-stu-id="407a1-130"><http://aka.ms/microservicesarchitecture></span></span>

## <a name="who-should-use-this-guide"></a><span data-ttu-id="407a1-131">Bu kılavuz kullanan</span><span class="sxs-lookup"><span data-stu-id="407a1-131">Who should use this guide</span></span>

<span data-ttu-id="407a1-132">Bu kılavuzda kitlesi çoğunlukla geliştiriciler, geliştirme müşteri adayları ve bulutta Microsoft teknolojileri ve hizmetleri kullanan modern web uygulamaları oluşturmaya ilgi duyan mimarlar içindir.</span><span class="sxs-lookup"><span data-stu-id="407a1-132">The audience for this guide is mainly developers, development leads, and architects who are interested in building modern web applications using Microsoft technologies and services in the cloud.</span></span>

<span data-ttu-id="407a1-133">İkincil bir dinleyici zaten bilinen ASP.NET ve/veya Azure ve yeni veya mevcut projeleri için ASP.NET Core yükseltmek için anlam olup olmadığı hakkında bilgi mi arıyorsunuz teknik karar alıcılar ' dir.</span><span class="sxs-lookup"><span data-stu-id="407a1-133">A secondary audience is technical decision makers who are already familiar ASP.NET and/or Azure and are looking for information on whether it makes sense to upgrade to ASP.NET Core for new or existing projects.</span></span>

## <a name="how-you-can-use-this-guide"></a><span data-ttu-id="407a1-134">Bu kılavuz nasıl kullanabileceğiniz</span><span class="sxs-lookup"><span data-stu-id="407a1-134">How you can use this guide</span></span>

<span data-ttu-id="407a1-135">Bu kılavuz, modern .NET teknolojileri ve Windows Azure ile web uygulamaları oluşturmaya odaklanan görece küçük bir belgeye sıkıştırılmış.</span><span class="sxs-lookup"><span data-stu-id="407a1-135">This guide has been condensed into a relatively small document that focuses on building web applications with modern .NET technologies and Windows Azure.</span></span> <span data-ttu-id="407a1-136">Bu nedenle, bu tür uygulamalar ve bunların teknik konular anlamanın bir temel tamamının okunabilir.</span><span class="sxs-lookup"><span data-stu-id="407a1-136">As such, it can be read in its entirety to provide a foundation of understanding such applications and their technical considerations.</span></span> <span data-ttu-id="407a1-137">Kendi örnek uygulama ile birlikte kılavuzu ayrıca bir başlangıç noktası veya başvuru hizmet verebilir.</span><span class="sxs-lookup"><span data-stu-id="407a1-137">The guide, along with its sample application, can also serve as a starting point or reference.</span></span> <span data-ttu-id="407a1-138">İlişkili örnek uygulaması, kendi uygulamalar için veya uygulamanızın bileşen parçalarını nasıl düzenleyebileceğini görmek için bir şablon olarak kullanın.</span><span class="sxs-lookup"><span data-stu-id="407a1-138">Use the associated sample application as a template for your own applications, or to see how you might organize your application's component parts.</span></span> <span data-ttu-id="407a1-139">Geri kılavuz ilkeleri ve kapsamı mimarisi ve teknoloji seçenekleri ve karar dikkat edilecek noktalar, kendi uygulama için bu seçeneklerin başvuracaklarını zaman bakın.</span><span class="sxs-lookup"><span data-stu-id="407a1-139">Refer back to the guide's principles and coverage of architecture and technology options and decision considerations when weighing these choices for your own application.</span></span>

<span data-ttu-id="407a1-140">Bu konuları ve fırsatlar genel olarak anlaşılmasını sağlamak için bu kılavuzu ekibinize iletmek çekinmeyin.</span><span class="sxs-lookup"><span data-stu-id="407a1-140">Feel free to forward this guide to your team to help ensure a common understanding of these considerations and opportunities.</span></span> <span data-ttu-id="407a1-141">Herkes ortak bir dizi terminolojisi çalışma ve ilkeleri temelindeki sahip mimari desenleri ve uygulamalar tutarlı uygulama sağlamaya yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="407a1-141">Having everybody working from a common set of terminology and underlying principles will help ensure consistent application of architectural patterns and practices.</span></span>

## <a name="references"></a><span data-ttu-id="407a1-142">Referanslar</span><span class="sxs-lookup"><span data-stu-id="407a1-142">References</span></span>
- <span data-ttu-id="407a1-143">**Sunucu uygulamaları için .NET Core ile .NET Framework arasında seçim yapma**</span><span class="sxs-lookup"><span data-stu-id="407a1-143">**Choosing between .NET Core and .NET Framework for server apps**</span></span>  
<span data-ttu-id="407a1-144"><https://docs.microsoft.com/dotnet/articles/standard/choosing-core-framework-server></span><span class="sxs-lookup"><span data-stu-id="407a1-144"><https://docs.microsoft.com/dotnet/articles/standard/choosing-core-framework-server></span></span>

>[!div class="step-by-step"]
<span data-ttu-id="407a1-145">[Sonraki] (modern-web-uygulamalar-characteristics.md)</span><span class="sxs-lookup"><span data-stu-id="407a1-145">[Next] (modern-web-applications-characteristics.md)</span></span>
