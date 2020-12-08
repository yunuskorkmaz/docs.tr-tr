---
title: ASP.NET Core ve Azure ile modern web uygulamaları tasarlama
description: ASP.NET Core ve Azure kullanarak tek parçalı Web uygulamaları oluşturmaya yönelik uçtan uca rehberlik sağlayan bir kılavuz.
author: ardalis
ms.author: wiwagn
ms.date: 12/07/2020
ms.openlocfilehash: 90d092b2269315e5b6734430e82cc7211324479b
ms.sourcegitcommit: 45c7148f2483db2501c1aa696ab6ed2ed8cb71b2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/08/2020
ms.locfileid: "96851301"
---
# <a name="architect-modern-web-applications-with-aspnet-core-and-azure"></a><span data-ttu-id="7c8ea-103">ASP.NET Core ve Microsoft Azure ile Modern Web Uygulamaları Tasarlama</span><span class="sxs-lookup"><span data-stu-id="7c8ea-103">Architect Modern Web Applications with ASP.NET Core and Azure</span></span>

![Mimarel Modern Web uygulamaları kılavuzu 'nun kitap kapağı resmi.](./media/index/web-application-guide-cover-image.png)

<span data-ttu-id="7c8ea-105">**Sürüm v 5.0** -ASP.NET Core 5,0 ' ye güncelleştirildi</span><span class="sxs-lookup"><span data-stu-id="7c8ea-105">**EDITION v5.0** - Updated to ASP.NET Core 5.0</span></span>

<span data-ttu-id="7c8ea-106">Kitap güncelleştirmeleri ve topluluk katkılarına yönelik [changelog](https://aka.ms/aspnet-ebook-changelog) 'u inceleyin.</span><span class="sxs-lookup"><span data-stu-id="7c8ea-106">Refer [changelog](https://aka.ms/aspnet-ebook-changelog) for the book updates and community contributions.</span></span>

<span data-ttu-id="7c8ea-107">YAYIMLAYAN</span><span class="sxs-lookup"><span data-stu-id="7c8ea-107">PUBLISHED BY</span></span>

<span data-ttu-id="7c8ea-108">Microsoft Geliştirici bölümü, .NET ve Visual Studio ürün ekipleri</span><span class="sxs-lookup"><span data-stu-id="7c8ea-108">Microsoft Developer Division, .NET, and Visual Studio product teams</span></span>

<span data-ttu-id="7c8ea-109">Microsoft Corporation 'ın bir bölümü</span><span class="sxs-lookup"><span data-stu-id="7c8ea-109">A division of Microsoft Corporation</span></span>

<span data-ttu-id="7c8ea-110">One Microsoft Way</span><span class="sxs-lookup"><span data-stu-id="7c8ea-110">One Microsoft Way</span></span>

<span data-ttu-id="7c8ea-111">Redmond, Washington 98052-6399</span><span class="sxs-lookup"><span data-stu-id="7c8ea-111">Redmond, Washington 98052-6399</span></span>

<span data-ttu-id="7c8ea-112">Telif hakkı © 2020 Microsoft Corporation</span><span class="sxs-lookup"><span data-stu-id="7c8ea-112">Copyright © 2020 by Microsoft Corporation</span></span>

<span data-ttu-id="7c8ea-113">All rights reserved.</span><span class="sxs-lookup"><span data-stu-id="7c8ea-113">All rights reserved.</span></span> <span data-ttu-id="7c8ea-114">Bu kitabın içeriğinin herhangi bir bölümü herhangi bir biçimde veya herhangi bir şekilde veya başka bir şekilde herhangi bir şekilde çoğaltılamaz veya herhangi bir şekilde gönderilebilir.</span><span class="sxs-lookup"><span data-stu-id="7c8ea-114">No part of the contents of this book may be reproduced or transmitted in any form or by any means without the written permission of the publisher.</span></span>

<span data-ttu-id="7c8ea-115">Bu kitap, "olduğu gibi" verilmiştir ve yazarın görünümlerini ve opnons 'yi ifade eder.</span><span class="sxs-lookup"><span data-stu-id="7c8ea-115">This book is provided "as-is" and expresses the author's views and opinions.</span></span> <span data-ttu-id="7c8ea-116">URL ve diğer Internet Web sitesi başvuruları dahil olmak üzere bu kitapta ifade edilen görünümler, eklentiler ve bilgiler bildirimde bulunmadan değiştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="7c8ea-116">The views, opinions, and information expressed in this book, including URL and other Internet website references, may change without notice.</span></span>

<span data-ttu-id="7c8ea-117">Burada tarif edilen bazı örnekler yalnızca açıklama için sağlanmıştır ve kurgusaldır.</span><span class="sxs-lookup"><span data-stu-id="7c8ea-117">Some examples depicted herein are provided for illustration only and are fictitious.</span></span> <span data-ttu-id="7c8ea-118">Gerçek bir ilişki veya bağlantı amaçlanmamıştır veya böyle bir bağlantı olduğu sonucuna varılmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="7c8ea-118">No real association or connection is intended or should be inferred.</span></span>

<span data-ttu-id="7c8ea-119">Microsoft ve <https://www.microsoft.com> "ticari markalar" Web sayfasında listelenen ticari markalar, Microsoft şirketler grubunun ticari markalarıdır.</span><span class="sxs-lookup"><span data-stu-id="7c8ea-119">Microsoft and the trademarks listed at <https://www.microsoft.com> on the "Trademarks" webpage are trademarks of the Microsoft group of companies.</span></span>

<span data-ttu-id="7c8ea-120">Mac ve macOS, Apple Inc. ' in ticari markalarıdır.</span><span class="sxs-lookup"><span data-stu-id="7c8ea-120">Mac and macOS are trademarks of Apple Inc.</span></span>

<span data-ttu-id="7c8ea-121">Docker balina logosu,, izin tarafından kullanılan Docker, Inc. ' in tescilli ticari markasıdır.</span><span class="sxs-lookup"><span data-stu-id="7c8ea-121">The Docker whale logo is a registered trademark of Docker, Inc. Used by permission.</span></span>

<span data-ttu-id="7c8ea-122">Diğer tüm işaretler ve amblemler kendi sahiplerinin mülkiyetindedir.</span><span class="sxs-lookup"><span data-stu-id="7c8ea-122">All other marks and logos are property of their respective owners.</span></span>

<span data-ttu-id="7c8ea-123">Yazar:</span><span class="sxs-lookup"><span data-stu-id="7c8ea-123">Author:</span></span>

> <span data-ttu-id="7c8ea-124">**Steve "ardalış" Smith** -yazılım mimarı ve trainer- [Ardalis.com](https://ardalis.com)</span><span class="sxs-lookup"><span data-stu-id="7c8ea-124">**Steve "ardalis" Smith** - Software Architect and Trainer - [Ardalis.com](https://ardalis.com)</span></span>

<span data-ttu-id="7c8ea-125">Edit</span><span class="sxs-lookup"><span data-stu-id="7c8ea-125">Editors:</span></span>

> <span data-ttu-id="7c8ea-126">**Maira Wenzel**</span><span class="sxs-lookup"><span data-stu-id="7c8ea-126">**Maira Wenzel**</span></span>

## <a name="action-links"></a><span data-ttu-id="7c8ea-127">Eylem bağlantıları</span><span class="sxs-lookup"><span data-stu-id="7c8ea-127">Action links</span></span>

- <span data-ttu-id="7c8ea-128">Bu e-kitap ayrıca bir PDF biçiminde (Yalnızca Ingilizce sürüm) [indirilebilir](https://aka.ms/webappebook)</span><span class="sxs-lookup"><span data-stu-id="7c8ea-128">This e-book is also available in a PDF format (English version only) [Download](https://aka.ms/webappebook)</span></span>

- <span data-ttu-id="7c8ea-129">[GitHub 'da başvuru uygulaması Eshoponweb 'i](https://github.com/dotnet-architecture/eShopOnWeb) kopyalama/çatal</span><span class="sxs-lookup"><span data-stu-id="7c8ea-129">Clone/Fork the reference application [eShopOnWeb on GitHub](https://github.com/dotnet-architecture/eShopOnWeb)</span></span>

## <a name="introduction"></a><span data-ttu-id="7c8ea-130">Giriş</span><span class="sxs-lookup"><span data-stu-id="7c8ea-130">Introduction</span></span>

<span data-ttu-id="7c8ea-131">.NET 5 ve ASP.NET Core geleneksel .NET geliştirme konusunda çeşitli avantajlar sunar.</span><span class="sxs-lookup"><span data-stu-id="7c8ea-131">.NET 5 and ASP.NET Core offer several advantages over traditional .NET development.</span></span> <span data-ttu-id="7c8ea-132">Aşağıdakilerden bazıları veya tümü uygulamanızın başarısı için önemliyse, sunucu uygulamalarınız için .NET 5 ' i kullanmanız gerekir:</span><span class="sxs-lookup"><span data-stu-id="7c8ea-132">You should use .NET 5 for your server applications if some or all of the following are important to your application's success:</span></span>

- <span data-ttu-id="7c8ea-133">Platformlar arası destek.</span><span class="sxs-lookup"><span data-stu-id="7c8ea-133">Cross-platform support.</span></span>

- <span data-ttu-id="7c8ea-134">Mikro hizmetlerin kullanımı.</span><span class="sxs-lookup"><span data-stu-id="7c8ea-134">Use of microservices.</span></span>

- <span data-ttu-id="7c8ea-135">Docker Kapsayıcıları kullanımı.</span><span class="sxs-lookup"><span data-stu-id="7c8ea-135">Use of Docker containers.</span></span>

- <span data-ttu-id="7c8ea-136">Yüksek performans ve ölçeklenebilirlik gereksinimleri.</span><span class="sxs-lookup"><span data-stu-id="7c8ea-136">High performance and scalability requirements.</span></span>

- <span data-ttu-id="7c8ea-137">Aynı sunucuda .NET sürümlerinin uygulamaya göre yan yana sürümü oluşturma.</span><span class="sxs-lookup"><span data-stu-id="7c8ea-137">Side-by-side versioning of .NET versions by application on the same server.</span></span>

<span data-ttu-id="7c8ea-138">Geleneksel .NET uygulamaları bu gereksinimlerin birçoğunu destekler ve ASP.NET Core ve .NET 5, yukarıdaki senaryolar için geliştirilmiş destek sunacak şekilde iyileştirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="7c8ea-138">Traditional .NET applications can and do support many of these requirements, but ASP.NET Core and .NET 5 have been optimized to offer improved support for the above scenarios.</span></span>

<span data-ttu-id="7c8ea-139">Daha fazla kuruluş, Microsoft Azure gibi hizmetleri kullanarak Web uygulamalarını bulutta barındırmak üzere tercih ediyor.</span><span class="sxs-lookup"><span data-stu-id="7c8ea-139">More and more organizations are choosing to host their web applications in the cloud using services like Microsoft Azure.</span></span> <span data-ttu-id="7c8ea-140">Uygulamanız veya kuruluşunuz için önemli bir öneme sahipseniz, uygulamanızı bulutta barındırmayı göz önünde bulundurmanız gerekir:</span><span class="sxs-lookup"><span data-stu-id="7c8ea-140">You should consider hosting your application in the cloud if the following are important to your application or organization:</span></span>

- <span data-ttu-id="7c8ea-141">Veri merkezi maliyetlerinde daha az yatırım (donanım, yazılım, boşluk, yardımcı programlar, sunucu yönetimi vb.)</span><span class="sxs-lookup"><span data-stu-id="7c8ea-141">Reduced investment in data center costs (hardware, software, space, utilities, server management, etc.)</span></span>

- <span data-ttu-id="7c8ea-142">Esnek fiyatlandırma (boşta kapasite için değil, kullanıma göre ödeme yapın).</span><span class="sxs-lookup"><span data-stu-id="7c8ea-142">Flexible pricing (pay based on usage, not for idle capacity).</span></span>

- <span data-ttu-id="7c8ea-143">Aşırı güvenilirlik.</span><span class="sxs-lookup"><span data-stu-id="7c8ea-143">Extreme reliability.</span></span>

- <span data-ttu-id="7c8ea-144">Geliştirilmiş uygulama Mobility; Uygulamanızın nerede ve nasıl dağıtıldığını kolayca değiştirin.</span><span class="sxs-lookup"><span data-stu-id="7c8ea-144">Improved app mobility; easily change where and how your app is deployed.</span></span>

- <span data-ttu-id="7c8ea-145">Esnek kapasite; gerçek ihtiyaçlarına göre ölçeği artırma veya azaltma.</span><span class="sxs-lookup"><span data-stu-id="7c8ea-145">Flexible capacity; scale up or down based on actual needs.</span></span>

<span data-ttu-id="7c8ea-146">Azure 'da barındırılan ASP.NET Core ile Web uygulamaları oluşturmak, geleneksel alternatifler üzerinde birçok rekabet avantajı sunar.</span><span class="sxs-lookup"><span data-stu-id="7c8ea-146">Building web applications with ASP.NET Core, hosted in Azure, offers many competitive advantages over traditional alternatives.</span></span> <span data-ttu-id="7c8ea-147">ASP.NET Core Modern Web uygulaması geliştirme uygulamaları ve bulut barındırma senaryoları için iyileştirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="7c8ea-147">ASP.NET Core is optimized for modern web application development practices and cloud hosting scenarios.</span></span> <span data-ttu-id="7c8ea-148">Bu kılavuzda, bu özelliklerden en iyi şekilde yararlanmak için ASP.NET Core uygulamalarınızı nasıl mimareceğinizi öğreneceksiniz.</span><span class="sxs-lookup"><span data-stu-id="7c8ea-148">In this guide, you'll learn how to architect your ASP.NET Core applications to best take advantage of these capabilities.</span></span>

## <a name="version"></a><span data-ttu-id="7c8ea-149">Sürüm</span><span class="sxs-lookup"><span data-stu-id="7c8ea-149">Version</span></span>

<span data-ttu-id="7c8ea-150">Bu kılavuz, .NET 5,0 sürümüyle aynı "Wave" teknolojileri (Azure ve ek üçüncü taraf teknolojileri) coinciding ile ilgili birçok ek güncelleştirme ile birlikte **.net 5,0** sürümünü kapsayacak şekilde değiştirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="7c8ea-150">This guide has been revised to cover **.NET 5.0** version along with many additional updates related to the same "wave" of technologies (that is, Azure and additional third-party technologies) coinciding in time with the .NET 5.0 release.</span></span> <span data-ttu-id="7c8ea-151">Kitap sürümü de **5,0** sürümüne güncelleştirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="7c8ea-151">That's why the book version has also been updated to version **5.0**.</span></span>

## <a name="purpose"></a><span data-ttu-id="7c8ea-152">Amaç</span><span class="sxs-lookup"><span data-stu-id="7c8ea-152">Purpose</span></span>

<span data-ttu-id="7c8ea-153">Bu kılavuz, ASP.NET Core ve Azure kullanarak *tek parçalı* Web uygulamaları oluşturmaya yönelik uçtan uca yönergeler sağlar.</span><span class="sxs-lookup"><span data-stu-id="7c8ea-153">This guide provides end-to-end guidance on building *monolithic* web applications using ASP.NET Core and Azure.</span></span> <span data-ttu-id="7c8ea-154">Bu bağlamda, "monoparçalı", bu uygulamaların bir etkileşim Hizmetleri ve uygulamaları koleksiyonu olarak değil, tek bir birim olarak dağıtılmasının gerçeğini ifade eder.</span><span class="sxs-lookup"><span data-stu-id="7c8ea-154">In this context, "monolithic" refers to the fact that these applications are deployed as a single unit, not as a collection of interacting services and applications.</span></span>

<span data-ttu-id="7c8ea-155">Bu kılavuz, ["_.net mikro hizmetleri" için tamamlayıcı bir kılavuzdur._](../microservices/index.md)Docker, mikro hizmetler ve kapsayıcı dağıtımında kurumsal uygulamaları barındırmak için daha fazla odaklanan, Kapsayıcılı .NET uygulamaları için mimari.</span><span class="sxs-lookup"><span data-stu-id="7c8ea-155">This guide is complementary to ["_.NET Microservices. Architecture for Containerized .NET Applications_"](../microservices/index.md), which focuses more on Docker, microservices, and deployment of containers to host enterprise applications.</span></span>

### <a name="net-microservices-architecture-for-containerized-net-applications"></a><span data-ttu-id="7c8ea-156">.NET mikro hizmetleri.</span><span class="sxs-lookup"><span data-stu-id="7c8ea-156">.NET Microservices.</span></span> <span data-ttu-id="7c8ea-157">Kapsayıcılı .NET Uygulamaları Mimarisi</span><span class="sxs-lookup"><span data-stu-id="7c8ea-157">Architecture for Containerized .NET Applications</span></span>

- <span data-ttu-id="7c8ea-158">**e-kitap**</span><span class="sxs-lookup"><span data-stu-id="7c8ea-158">**e-book**</span></span>  
  <https://aka.ms/MicroservicesEbook>
- <span data-ttu-id="7c8ea-159">**Örnek uygulama**</span><span class="sxs-lookup"><span data-stu-id="7c8ea-159">**Sample Application**</span></span>  
  <https://aka.ms/microservicesarchitecture>

## <a name="who-should-use-this-guide"></a><span data-ttu-id="7c8ea-160">Bu kılavuzu kimler kullanmalıdır?</span><span class="sxs-lookup"><span data-stu-id="7c8ea-160">Who should use this guide</span></span>

<span data-ttu-id="7c8ea-161">Bu kılavuzun hedef kitlesi, bulutta Microsoft teknolojilerini ve hizmetlerini kullanarak modern web uygulamaları oluşturmaya ilgilenen temel geliştiriciler, geliştirme müşteri adayları ve mimarilerdir.</span><span class="sxs-lookup"><span data-stu-id="7c8ea-161">The audience for this guide is mainly developers, development leads, and architects who are interested in building modern web applications using Microsoft technologies and services in the cloud.</span></span>

<span data-ttu-id="7c8ea-162">İkincil hedef kitle, zaten ASP.NET veya Azure 'u bildiğiniz ve yeni veya mevcut projeler için ASP.NET Core yükseltme konusunda anlamlı olup olmadığı hakkında bilgi arayan teknik karar mekanizmalarıdır.</span><span class="sxs-lookup"><span data-stu-id="7c8ea-162">A secondary audience is technical decision makers who are already familiar ASP.NET or Azure and are looking for information on whether it makes sense to upgrade to ASP.NET Core for new or existing projects.</span></span>

## <a name="how-you-can-use-this-guide"></a><span data-ttu-id="7c8ea-163">Bu Kılavuzu nasıl kullanabileceğiniz</span><span class="sxs-lookup"><span data-stu-id="7c8ea-163">How you can use this guide</span></span>

<span data-ttu-id="7c8ea-164">Bu kılavuz, modern .NET teknolojileri ve Azure ile Web uygulamaları oluşturmaya odaklanan görece küçük bir belgeye yoğunlaştırılmıştır.</span><span class="sxs-lookup"><span data-stu-id="7c8ea-164">This guide has been condensed into a relatively small document that focuses on building web applications with modern .NET technologies and Azure.</span></span> <span data-ttu-id="7c8ea-165">Bu nedenle, bu tür uygulamaları ve teknik konuları anlama temelini sağlamak için tamamen okunabilir.</span><span class="sxs-lookup"><span data-stu-id="7c8ea-165">As such, it can be read in its entirety to provide a foundation of understanding such applications and their technical considerations.</span></span> <span data-ttu-id="7c8ea-166">Kılavuz, örnek uygulamayla birlikte bir başlangıç noktası veya başvuru işlevi de sunabilir.</span><span class="sxs-lookup"><span data-stu-id="7c8ea-166">The guide, along with its sample application, can also serve as a starting point or reference.</span></span> <span data-ttu-id="7c8ea-167">İlişkili örnek uygulamayı kendi uygulamalarınız için bir şablon olarak veya uygulamanızın bileşen parçalarını nasıl düzenleyebileceğini görmek için kullanın.</span><span class="sxs-lookup"><span data-stu-id="7c8ea-167">Use the associated sample application as a template for your own applications, or to see how you might organize your application's component parts.</span></span> <span data-ttu-id="7c8ea-168">Kendi uygulamanız için bu seçenekleri katdığınızda, kılavuzun ilkelerine ve mimari ve teknoloji seçeneklerinin kapsamına ve kararına dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="7c8ea-168">Refer back to the guide's principles and coverage of architecture and technology options and decision considerations when you're weighing these choices for your own application.</span></span>

<span data-ttu-id="7c8ea-169">Bu noktaların ve fırsatların yaygın olarak anlaşılmasına yardımcı olmak için bu kılavuzu ekibinize iletmekten çekinmeyin.</span><span class="sxs-lookup"><span data-stu-id="7c8ea-169">Feel free to forward this guide to your team to help ensure a common understanding of these considerations and opportunities.</span></span> <span data-ttu-id="7c8ea-170">Her bir gövdenin ortak bir terminoloji kümesinden ve temel ilkelerin üzerinde çalışmasını sağlamak, mimari desenlerinin ve uygulamaların tutarlı olmasını sağlamaya yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="7c8ea-170">Having everybody working from a common set of terminology and underlying principles helps ensure consistent application of architectural patterns and practices.</span></span>

## <a name="references"></a><span data-ttu-id="7c8ea-171">Başvurular</span><span class="sxs-lookup"><span data-stu-id="7c8ea-171">References</span></span>

- <span data-ttu-id="7c8ea-172">**Sunucu uygulamaları için .NET 5 ve .NET Framework arasında seçim yapma**</span><span class="sxs-lookup"><span data-stu-id="7c8ea-172">**Choosing between .NET 5 and .NET Framework for server apps**</span></span>  
  [https://docs.microsoft.com/dotnet/standard/choosing-core-framework-server](../../standard/choosing-core-framework-server.md)

>[!div class="step-by-step"]
>[<span data-ttu-id="7c8ea-173">Sonraki</span><span class="sxs-lookup"><span data-stu-id="7c8ea-173">Next</span></span>](modern-web-applications-characteristics.md)
