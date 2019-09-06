---
title: ASP.NET Core ve Azure ile modern web uygulamalarını mimarın
description: ASP.NET Core ve Azure kullanarak tek parçalı Web uygulamaları oluşturmaya yönelik uçtan uca rehberlik sağlayan bir kılavuz.
author: ardalis
ms.author: wiwagn
ms.date: 01/30/2019
ms.openlocfilehash: 739dd607aaa45f73e777a30c6495e329236fee17
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/30/2019
ms.locfileid: "70296294"
---
# <a name="architect-modern-web-applications-with-aspnet-core-and-azure"></a><span data-ttu-id="d8a6a-103">ASP.NET Core ve Azure ile modern web uygulamalarını mimarın</span><span class="sxs-lookup"><span data-stu-id="d8a6a-103">Architect Modern Web Applications with ASP.NET Core and Azure</span></span>

![Mimari modern web uygulamaları kılavuzu 'nun kapak resmi.](./media/index/web-application-guide-cover-image.png)

<span data-ttu-id="d8a6a-105">YAYIMLAYAN</span><span class="sxs-lookup"><span data-stu-id="d8a6a-105">PUBLISHED BY</span></span>

<span data-ttu-id="d8a6a-106">Microsoft Geliştirici bölümü, .NET ve Visual Studio ürün ekipleri</span><span class="sxs-lookup"><span data-stu-id="d8a6a-106">Microsoft Developer Division, .NET, and Visual Studio product teams</span></span>

<span data-ttu-id="d8a6a-107">Microsoft Corporation 'ın bir bölümü</span><span class="sxs-lookup"><span data-stu-id="d8a6a-107">A division of Microsoft Corporation</span></span>

<span data-ttu-id="d8a6a-108">One Microsoft Way</span><span class="sxs-lookup"><span data-stu-id="d8a6a-108">One Microsoft Way</span></span>

<span data-ttu-id="d8a6a-109">Redmond, Washington 98052-6399</span><span class="sxs-lookup"><span data-stu-id="d8a6a-109">Redmond, Washington 98052-6399</span></span>

<span data-ttu-id="d8a6a-110">Telif hakkı © 2019 Microsoft Corporation</span><span class="sxs-lookup"><span data-stu-id="d8a6a-110">Copyright © 2019 by Microsoft Corporation</span></span>

<span data-ttu-id="d8a6a-111">Tüm hakları saklıdır.</span><span class="sxs-lookup"><span data-stu-id="d8a6a-111">All rights reserved.</span></span> <span data-ttu-id="d8a6a-112">Bu kitabın içeriğinin herhangi bir bölümü herhangi bir biçimde veya herhangi bir şekilde veya başka bir şekilde herhangi bir şekilde çoğaltılamaz veya herhangi bir şekilde gönderilebilir.</span><span class="sxs-lookup"><span data-stu-id="d8a6a-112">No part of the contents of this book may be reproduced or transmitted in any form or by any means without the written permission of the publisher.</span></span>

<span data-ttu-id="d8a6a-113">Bu kitap, "olduğu gibi" verilmiştir ve yazarın görünümlerini ve opnons 'yi ifade eder.</span><span class="sxs-lookup"><span data-stu-id="d8a6a-113">This book is provided “as-is” and expresses the author’s views and opinions.</span></span> <span data-ttu-id="d8a6a-114">Bu kitapta ifade edilen görünümler, eklentiler ve bilgiler, URL ve diğer Internet Web sitesi başvuruları da dahil olmak üzere bildirimde bulunmaksızın değiştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="d8a6a-114">The views, opinions and information expressed in this book, including URL and other Internet website references, may change without notice.</span></span>

<span data-ttu-id="d8a6a-115">Burada gösterilen bazı örnekler yalnızca gösterim amaçlıdır ve hayal ürünüdür.</span><span class="sxs-lookup"><span data-stu-id="d8a6a-115">Some examples depicted herein are provided for illustration only and are fictitious.</span></span> <span data-ttu-id="d8a6a-116">Hiçbir gerçek ilişkilendirme veya bağlantı amaçlanmaz veya çıkarsanmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="d8a6a-116">No real association or connection is intended or should be inferred.</span></span>

<span data-ttu-id="d8a6a-117">Microsoft ve "ticari markalar" https://www.microsoft.com Web sayfasında listelenen ticari markalar, Microsoft şirketler grubunun ticari markalarıdır.</span><span class="sxs-lookup"><span data-stu-id="d8a6a-117">Microsoft and the trademarks listed at https://www.microsoft.com on the “Trademarks” webpage are trademarks of the Microsoft group of companies.</span></span>

<span data-ttu-id="d8a6a-118">Mac ve macOS, Apple Inc. ' in ticari markalarıdır.</span><span class="sxs-lookup"><span data-stu-id="d8a6a-118">Mac and macOS are trademarks of Apple Inc.</span></span>

<span data-ttu-id="d8a6a-119">Docker balina logosu, Docker, Inc 'nin tescilli ticari markasıdır. İzin tarafından kullanılır.</span><span class="sxs-lookup"><span data-stu-id="d8a6a-119">The Docker whale logo is a registered trademark of Docker, Inc. Used by permission.</span></span>

<span data-ttu-id="d8a6a-120">Diğer tüm işaretler ve amblemler kendi sahiplerinin mülkiyetindedir.</span><span class="sxs-lookup"><span data-stu-id="d8a6a-120">All other marks and logos are property of their respective owners.</span></span>

<span data-ttu-id="d8a6a-121">Geliştirici</span><span class="sxs-lookup"><span data-stu-id="d8a6a-121">Author:</span></span>

> <span data-ttu-id="d8a6a-122">**Steve "ardalış" Smith** -yazılım mimarı ve trainer- [Ardalis.com](https://ardalis.com)</span><span class="sxs-lookup"><span data-stu-id="d8a6a-122">**Steve "ardalis" Smith** - Software Architect and Trainer - [Ardalis.com](https://ardalis.com)</span></span>

<span data-ttu-id="d8a6a-123">Edit</span><span class="sxs-lookup"><span data-stu-id="d8a6a-123">Editors:</span></span>

> <span data-ttu-id="d8a6a-124">**Maira Wenzel**</span><span class="sxs-lookup"><span data-stu-id="d8a6a-124">**Maira Wenzel**</span></span>

## <a name="introduction"></a><span data-ttu-id="d8a6a-125">Giriş</span><span class="sxs-lookup"><span data-stu-id="d8a6a-125">Introduction</span></span>

<span data-ttu-id="d8a6a-126">.NET Core ve ASP.NET Core geleneksel .NET geliştirme konusunda çeşitli avantajlar sunar.</span><span class="sxs-lookup"><span data-stu-id="d8a6a-126">.NET Core and ASP.NET Core offer several advantages over traditional .NET development.</span></span> <span data-ttu-id="d8a6a-127">Aşağıdakilerden bazıları veya tümü uygulamanızın başarısı için önemliyse, sunucu uygulamalarınız için .NET Core ' u kullanmanız gerekir:</span><span class="sxs-lookup"><span data-stu-id="d8a6a-127">You should use .NET Core for your server applications if some or all of the following are important to your application's success:</span></span>

- <span data-ttu-id="d8a6a-128">Platformlar arası destek.</span><span class="sxs-lookup"><span data-stu-id="d8a6a-128">Cross-platform support.</span></span>

- <span data-ttu-id="d8a6a-129">Mikro hizmetlerin kullanımı.</span><span class="sxs-lookup"><span data-stu-id="d8a6a-129">Use of microservices.</span></span>

- <span data-ttu-id="d8a6a-130">Docker Kapsayıcıları kullanımı.</span><span class="sxs-lookup"><span data-stu-id="d8a6a-130">Use of Docker containers.</span></span>

- <span data-ttu-id="d8a6a-131">Yüksek performans ve ölçeklenebilirlik gereksinimleri.</span><span class="sxs-lookup"><span data-stu-id="d8a6a-131">High performance and scalability requirements.</span></span>

- <span data-ttu-id="d8a6a-132">Aynı sunucuda .NET sürümlerinin uygulamaya göre yan yana sürümü oluşturma.</span><span class="sxs-lookup"><span data-stu-id="d8a6a-132">Side-by-side versioning of .NET versions by application on the same server.</span></span>

<span data-ttu-id="d8a6a-133">Geleneksel .NET uygulamaları, bu gereksinimlerin birçoğunu destekler ve ASP.NET Core ve .NET Core, yukarıdaki senaryolar için geliştirilmiş destek sunacak şekilde iyileştirildi.</span><span class="sxs-lookup"><span data-stu-id="d8a6a-133">Traditional .NET applications can and do support many of these requirements, but ASP.NET Core and .NET Core have been optimized to offer improved support for the above scenarios.</span></span>

<span data-ttu-id="d8a6a-134">Daha fazla kuruluş, Microsoft Azure gibi hizmetleri kullanarak Web uygulamalarını bulutta barındırmak üzere tercih ediyor.</span><span class="sxs-lookup"><span data-stu-id="d8a6a-134">More and more organizations are choosing to host their web applications in the cloud using services like Microsoft Azure.</span></span> <span data-ttu-id="d8a6a-135">Uygulamanız veya kuruluşunuz için önemli bir öneme sahipseniz, uygulamanızı bulutta barındırmayı göz önünde bulundurmanız gerekir:</span><span class="sxs-lookup"><span data-stu-id="d8a6a-135">You should consider hosting your application in the cloud if the following are important to your application or organization:</span></span>

- <span data-ttu-id="d8a6a-136">Veri merkezi maliyetlerinde daha az yatırım (donanım, yazılım, boşluk, yardımcı programlar, sunucu yönetimi vb.)</span><span class="sxs-lookup"><span data-stu-id="d8a6a-136">Reduced investment in data center costs (hardware, software, space, utilities, server management, etc.)</span></span>

- <span data-ttu-id="d8a6a-137">Esnek fiyatlandırma (boşta kapasite için değil, kullanıma göre ödeme yapın).</span><span class="sxs-lookup"><span data-stu-id="d8a6a-137">Flexible pricing (pay based on usage, not for idle capacity).</span></span>

- <span data-ttu-id="d8a6a-138">Aşırı güvenilirlik.</span><span class="sxs-lookup"><span data-stu-id="d8a6a-138">Extreme reliability.</span></span>

- <span data-ttu-id="d8a6a-139">Geliştirilmiş uygulama Mobility; Uygulamanızın nerede ve nasıl dağıtıldığını kolayca değiştirin.</span><span class="sxs-lookup"><span data-stu-id="d8a6a-139">Improved app mobility; easily change where and how your app is deployed.</span></span>

- <span data-ttu-id="d8a6a-140">Esnek kapasite; gerçek ihtiyaçlarına göre ölçeği artırma veya azaltma.</span><span class="sxs-lookup"><span data-stu-id="d8a6a-140">Flexible capacity; scale up or down based on actual needs.</span></span>

<span data-ttu-id="d8a6a-141">Azure 'da barındırılan ASP.NET Core ile Web uygulamaları oluşturmak, geleneksel alternatifler üzerinde birçok rekabet avantajı sunar.</span><span class="sxs-lookup"><span data-stu-id="d8a6a-141">Building web applications with ASP.NET Core, hosted in Azure, offers many competitive advantages over traditional alternatives.</span></span> <span data-ttu-id="d8a6a-142">ASP.NET Core Modern Web uygulaması geliştirme uygulamaları ve bulut barındırma senaryoları için iyileştirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="d8a6a-142">ASP.NET Core is optimized for modern web application development practices and cloud hosting scenarios.</span></span> <span data-ttu-id="d8a6a-143">Bu kılavuzda, bu özelliklerden en iyi şekilde yararlanmak için ASP.NET Core uygulamalarınızı nasıl mimareceğinizi öğreneceksiniz.</span><span class="sxs-lookup"><span data-stu-id="d8a6a-143">In this guide, you'll learn how to architect your ASP.NET Core applications to best take advantage of these capabilities.</span></span>

## <a name="purpose"></a><span data-ttu-id="d8a6a-144">Amaç</span><span class="sxs-lookup"><span data-stu-id="d8a6a-144">Purpose</span></span>

<span data-ttu-id="d8a6a-145">Bu kılavuz, ASP.NET Core ve Azure kullanarak *tek parçalı* Web uygulamaları oluşturmaya yönelik uçtan uca yönergeler sağlar.</span><span class="sxs-lookup"><span data-stu-id="d8a6a-145">This guide provides end-to-end guidance on building *monolithic* web applications using ASP.NET Core and Azure.</span></span> <span data-ttu-id="d8a6a-146">Bu bağlamda, "monoparçalı", bu uygulamaların bir etkileşim Hizmetleri ve uygulamaları koleksiyonu olarak değil, tek bir birim olarak dağıtılmasının gerçeğini ifade eder.</span><span class="sxs-lookup"><span data-stu-id="d8a6a-146">In this context, "monolithic" refers to the fact that these applications are deployed as a single unit, not as a collection of interacting services and applications.</span></span>

<span data-ttu-id="d8a6a-147">Bu kılavuz, [".net mikro Hizmetleri _" için tamamlayıcı bir kılavuzdur. Docker, mikro hizmetler ve_kapsayıcı](../microservices/index.md) dağıtımında kurumsal uygulamaları barındırmak için daha fazla odaklanan kapsayıcı .NET uygulamaları için mimari.</span><span class="sxs-lookup"><span data-stu-id="d8a6a-147">This guide is complementary to the ["_.NET Microservices. Architecture for Containerized .NET Applications_"](../microservices/index.md) which focuses more on Docker, Microservices, and Deployment of Containers to host enterprise applications.</span></span>

### <a name="net-microservices-architecture-for-containerized-net-applications"></a><span data-ttu-id="d8a6a-148">.NET mikro hizmetleri.</span><span class="sxs-lookup"><span data-stu-id="d8a6a-148">.NET Microservices.</span></span> <span data-ttu-id="d8a6a-149">Kapsayıcılı .NET Uygulamaları Mimarisi</span><span class="sxs-lookup"><span data-stu-id="d8a6a-149">Architecture for Containerized .NET Applications</span></span>

- <span data-ttu-id="d8a6a-150">**e-kitap**</span><span class="sxs-lookup"><span data-stu-id="d8a6a-150">**e-book**</span></span>  
  <https://aka.ms/MicroservicesEbook>
- <span data-ttu-id="d8a6a-151">**Örnek uygulama**</span><span class="sxs-lookup"><span data-stu-id="d8a6a-151">**Sample Application**</span></span>  
  <https://aka.ms/microservicesarchitecture>

## <a name="who-should-use-this-guide"></a><span data-ttu-id="d8a6a-152">Bu kılavuzu kimler kullanmalıdır?</span><span class="sxs-lookup"><span data-stu-id="d8a6a-152">Who should use this guide</span></span>

<span data-ttu-id="d8a6a-153">Bu kılavuzun hedef kitlesi, bulutta Microsoft teknolojilerini ve hizmetlerini kullanarak modern web uygulamaları oluşturmaya ilgilenen temel geliştiriciler, geliştirme müşteri adayları ve mimarilerdir.</span><span class="sxs-lookup"><span data-stu-id="d8a6a-153">The audience for this guide is mainly developers, development leads, and architects who are interested in building modern web applications using Microsoft technologies and services in the cloud.</span></span>

<span data-ttu-id="d8a6a-154">İkincil hedef kitle, zaten ASP.NET veya Azure 'u bildiğiniz ve yeni veya mevcut projeler için ASP.NET Core yükseltme konusunda anlamlı olup olmadığı hakkında bilgi arayan teknik karar mekanizmalarıdır.</span><span class="sxs-lookup"><span data-stu-id="d8a6a-154">A secondary audience is technical decision makers who are already familiar ASP.NET or Azure and are looking for information on whether it makes sense to upgrade to ASP.NET Core for new or existing projects.</span></span>

## <a name="how-you-can-use-this-guide"></a><span data-ttu-id="d8a6a-155">Bu Kılavuzu nasıl kullanabileceğiniz</span><span class="sxs-lookup"><span data-stu-id="d8a6a-155">How you can use this guide</span></span>

<span data-ttu-id="d8a6a-156">Bu kılavuz, modern .NET teknolojileri ve Windows Azure ile Web uygulamaları oluşturmaya odaklanan görece küçük bir belgeye yoğunlaştırılmıştır.</span><span class="sxs-lookup"><span data-stu-id="d8a6a-156">This guide has been condensed into a relatively small document that focuses on building web applications with modern .NET technologies and Windows Azure.</span></span> <span data-ttu-id="d8a6a-157">Bu nedenle, bu tür uygulamaları ve teknik konuları anlama temelini sağlamak için tamamen okunabilir.</span><span class="sxs-lookup"><span data-stu-id="d8a6a-157">As such, it can be read in its entirety to provide a foundation of understanding such applications and their technical considerations.</span></span> <span data-ttu-id="d8a6a-158">Kılavuz, örnek uygulamayla birlikte bir başlangıç noktası veya başvuru işlevi de sunabilir.</span><span class="sxs-lookup"><span data-stu-id="d8a6a-158">The guide, along with its sample application, can also serve as a starting point or reference.</span></span> <span data-ttu-id="d8a6a-159">İlişkili örnek uygulamayı kendi uygulamalarınız için bir şablon olarak veya uygulamanızın bileşen parçalarını nasıl düzenleyebileceğini görmek için kullanın.</span><span class="sxs-lookup"><span data-stu-id="d8a6a-159">Use the associated sample application as a template for your own applications, or to see how you might organize your application's component parts.</span></span> <span data-ttu-id="d8a6a-160">Kendi uygulamanız için bu seçenekleri katdığınızda, kılavuzun ilkelerine ve mimari ve teknoloji seçeneklerinin kapsamına ve kararına dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="d8a6a-160">Refer back to the guide's principles and coverage of architecture and technology options and decision considerations when you're weighing these choices for your own application.</span></span>

<span data-ttu-id="d8a6a-161">Bu noktaların ve fırsatların yaygın olarak anlaşılmasına yardımcı olmak için bu kılavuzu ekibinize iletmekten çekinmeyin.</span><span class="sxs-lookup"><span data-stu-id="d8a6a-161">Feel free to forward this guide to your team to help ensure a common understanding of these considerations and opportunities.</span></span> <span data-ttu-id="d8a6a-162">Her bir gövdenin ortak bir terminoloji kümesinden ve temel ilkelerin üzerinde çalışmasını sağlamak, mimari desenlerinin ve uygulamaların tutarlı olmasını sağlamaya yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="d8a6a-162">Having everybody working from a common set of terminology and underlying principles helps ensure consistent application of architectural patterns and practices.</span></span>

## <a name="references"></a><span data-ttu-id="d8a6a-163">Referanslar</span><span class="sxs-lookup"><span data-stu-id="d8a6a-163">References</span></span>

- <span data-ttu-id="d8a6a-164">**Sunucu uygulamaları için .NET Core ile .NET Framework arasında seçim yapma**</span><span class="sxs-lookup"><span data-stu-id="d8a6a-164">**Choosing between .NET Core and .NET Framework for server apps**</span></span>  
  [https://docs.microsoft.com/dotnet/standard/choosing-core-framework-server](../../standard/choosing-core-framework-server.md)

>[!div class="step-by-step"]
>[<span data-ttu-id="d8a6a-165">Next</span><span class="sxs-lookup"><span data-stu-id="d8a6a-165">Next</span></span>](modern-web-applications-characteristics.md)
