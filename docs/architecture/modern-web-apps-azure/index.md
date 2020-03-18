---
title: ASP.NET Core ve Azure ile modern web uygulamalarını mimar
description: ASP.NET Core ve Azure kullanarak yekpare web uygulamaları oluşturma konusunda uçlardan uca kılavuz sağlayan bir kılavuz.
author: ardalis
ms.author: wiwagn
ms.date: 12/4/2019
ms.openlocfilehash: c19e5e90cfb96463f744cfb064abe72ee5db2e9f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "77449340"
---
# <a name="architect-modern-web-applications-with-aspnet-core-and-azure"></a><span data-ttu-id="b3545-103">ASP.NET Core ve Microsoft Azure ile Modern Web Uygulamaları Tasarlama</span><span class="sxs-lookup"><span data-stu-id="b3545-103">Architect Modern Web Applications with ASP.NET Core and Azure</span></span>

![Mimar Modern Web Uygulamaları kılavuzunun kitap kapağı görüntüsü.](./media/index/web-application-guide-cover-image.png)

<span data-ttu-id="b3545-105">**EDITION v3.1** - Core 3.1 ASP.NET güncellendi</span><span class="sxs-lookup"><span data-stu-id="b3545-105">**EDITION v3.1** - Updated to ASP.NET Core 3.1</span></span>

<span data-ttu-id="b3545-106">YAYIMLAYAN</span><span class="sxs-lookup"><span data-stu-id="b3545-106">PUBLISHED BY</span></span>

<span data-ttu-id="b3545-107">Microsoft Developer Division, .NET ve Visual Studio ürün ekipleri</span><span class="sxs-lookup"><span data-stu-id="b3545-107">Microsoft Developer Division, .NET, and Visual Studio product teams</span></span>

<span data-ttu-id="b3545-108">Microsoft Corporation'ın bir bölümü</span><span class="sxs-lookup"><span data-stu-id="b3545-108">A division of Microsoft Corporation</span></span>

<span data-ttu-id="b3545-109">One Microsoft Way</span><span class="sxs-lookup"><span data-stu-id="b3545-109">One Microsoft Way</span></span>

<span data-ttu-id="b3545-110">Redmond, Washington 98052-6399</span><span class="sxs-lookup"><span data-stu-id="b3545-110">Redmond, Washington 98052-6399</span></span>

<span data-ttu-id="b3545-111">Telif hakkı © 2020 Microsoft Corporation tarafından</span><span class="sxs-lookup"><span data-stu-id="b3545-111">Copyright © 2020 by Microsoft Corporation</span></span>

<span data-ttu-id="b3545-112">Tüm hakları saklıdır.</span><span class="sxs-lookup"><span data-stu-id="b3545-112">All rights reserved.</span></span> <span data-ttu-id="b3545-113">Bu kitabın içeriğinin hiçbir bölümü, yayımcının yazılı izni olmadan herhangi bir biçimde veya herhangi bir şekilde çoğaltılamaz veya aktarılamaz.</span><span class="sxs-lookup"><span data-stu-id="b3545-113">No part of the contents of this book may be reproduced or transmitted in any form or by any means without the written permission of the publisher.</span></span>

<span data-ttu-id="b3545-114">Bu kitap "olduğu gibi" sağlanır ve yazarın görüş ve görüşlerini ifade eder.</span><span class="sxs-lookup"><span data-stu-id="b3545-114">This book is provided “as-is” and expresses the author’s views and opinions.</span></span> <span data-ttu-id="b3545-115">URL ve diğer Internet web sitesi referansları da dahil olmak üzere bu kitapta ifade edilen görüşler, görüşler ve bilgiler önceden haber verilmeden değişebilir.</span><span class="sxs-lookup"><span data-stu-id="b3545-115">The views, opinions and information expressed in this book, including URL and other Internet website references, may change without notice.</span></span>

<span data-ttu-id="b3545-116">Burada tarif edilen bazı örnekler yalnızca açıklama için sağlanmıştır ve kurgusaldır.</span><span class="sxs-lookup"><span data-stu-id="b3545-116">Some examples depicted herein are provided for illustration only and are fictitious.</span></span> <span data-ttu-id="b3545-117">Gerçek bir ilişki veya bağlantı amaçlanmamıştır veya böyle bir bağlantı olduğu sonucuna varılmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="b3545-117">No real association or connection is intended or should be inferred.</span></span>

<span data-ttu-id="b3545-118">Microsoft ve "Ticari https://www.microsoft.com Markalar" web sayfasında listelenen ticari markalar, Microsoft şirketler grubunun ticari markalarıdır.</span><span class="sxs-lookup"><span data-stu-id="b3545-118">Microsoft and the trademarks listed at https://www.microsoft.com on the “Trademarks” webpage are trademarks of the Microsoft group of companies.</span></span>

<span data-ttu-id="b3545-119">Mac ve macOS, Apple Inc. şirketinin ticari markalarıdır.</span><span class="sxs-lookup"><span data-stu-id="b3545-119">Mac and macOS are trademarks of Apple Inc.</span></span>

<span data-ttu-id="b3545-120">Docker balina logosu, Docker, Inc. şirketinin izni yle kullanılan tescilli ticari markasıdır.</span><span class="sxs-lookup"><span data-stu-id="b3545-120">The Docker whale logo is a registered trademark of Docker, Inc. Used by permission.</span></span>

<span data-ttu-id="b3545-121">Diğer tüm işaretler ve logolar ilgili sahiplerinin mülkiyetindedir.</span><span class="sxs-lookup"><span data-stu-id="b3545-121">All other marks and logos are property of their respective owners.</span></span>

<span data-ttu-id="b3545-122">Yazar:</span><span class="sxs-lookup"><span data-stu-id="b3545-122">Author:</span></span>

> <span data-ttu-id="b3545-123">**Steve "ardalis" Smith** - Yazılım Mimarı ve Eğitmen - [Ardalis.com](https://ardalis.com)</span><span class="sxs-lookup"><span data-stu-id="b3545-123">**Steve "ardalis" Smith** - Software Architect and Trainer - [Ardalis.com](https://ardalis.com)</span></span>

<span data-ttu-id="b3545-124">Editörler:</span><span class="sxs-lookup"><span data-stu-id="b3545-124">Editors:</span></span>

> <span data-ttu-id="b3545-125">**Maira Wenzel**</span><span class="sxs-lookup"><span data-stu-id="b3545-125">**Maira Wenzel**</span></span>

## <a name="introduction"></a><span data-ttu-id="b3545-126">Giriş</span><span class="sxs-lookup"><span data-stu-id="b3545-126">Introduction</span></span>

<span data-ttu-id="b3545-127">.NET Core ve ASP.NET Core, geleneksel .NET geliştirmeye göre çeşitli avantajlar sunar.</span><span class="sxs-lookup"><span data-stu-id="b3545-127">.NET Core and ASP.NET Core offer several advantages over traditional .NET development.</span></span> <span data-ttu-id="b3545-128">Aşağıdakilerden bazıları veya tümü uygulamanızın başarısı için önemliyse sunucu uygulamalarınız için .NET Core'u kullanmalısınız:</span><span class="sxs-lookup"><span data-stu-id="b3545-128">You should use .NET Core for your server applications if some or all of the following are important to your application's success:</span></span>

- <span data-ttu-id="b3545-129">Platform ötesi destek.</span><span class="sxs-lookup"><span data-stu-id="b3545-129">Cross-platform support.</span></span>

- <span data-ttu-id="b3545-130">Mikro hizmetlerin kullanımı.</span><span class="sxs-lookup"><span data-stu-id="b3545-130">Use of microservices.</span></span>

- <span data-ttu-id="b3545-131">Docker konteynerlerinin kullanımı.</span><span class="sxs-lookup"><span data-stu-id="b3545-131">Use of Docker containers.</span></span>

- <span data-ttu-id="b3545-132">Yüksek performans ve ölçeklenebilirlik gereksinimleri.</span><span class="sxs-lookup"><span data-stu-id="b3545-132">High performance and scalability requirements.</span></span>

- <span data-ttu-id="b3545-133">.NET sürümlerinin aynı sunucudaki uygulamalara göre yan yana sürüklüyor.</span><span class="sxs-lookup"><span data-stu-id="b3545-133">Side-by-side versioning of .NET versions by application on the same server.</span></span>

<span data-ttu-id="b3545-134">Geleneksel .NET uygulamaları bu gereksinimlerin çoğunu destekleyebilir ve destekleyebilir, ancak ASP.NET Core ve .NET Core yukarıdaki senaryolar için geliştirilmiş destek sunmak üzere optimize edilmiştir.</span><span class="sxs-lookup"><span data-stu-id="b3545-134">Traditional .NET applications can and do support many of these requirements, but ASP.NET Core and .NET Core have been optimized to offer improved support for the above scenarios.</span></span>

<span data-ttu-id="b3545-135">Giderek daha fazla kuruluş, Microsoft Azure gibi hizmetleri kullanarak web uygulamalarını bulutta barındırmayı tercih ediyor.</span><span class="sxs-lookup"><span data-stu-id="b3545-135">More and more organizations are choosing to host their web applications in the cloud using services like Microsoft Azure.</span></span> <span data-ttu-id="b3545-136">Aşağıdakiler uygulamanız veya kuruluşunuz için önemliyse, uygulamanızı bulutta barındırmayı düşünmelisiniz:</span><span class="sxs-lookup"><span data-stu-id="b3545-136">You should consider hosting your application in the cloud if the following are important to your application or organization:</span></span>

- <span data-ttu-id="b3545-137">Veri merkezi maliyetlerine daha az yatırım (donanım, yazılım, alan, yardımcı programlar, sunucu yönetimi, vb.)</span><span class="sxs-lookup"><span data-stu-id="b3545-137">Reduced investment in data center costs (hardware, software, space, utilities, server management, etc.)</span></span>

- <span data-ttu-id="b3545-138">Esnek fiyatlandırma (boşta kapasite için değil, kullanıma göre ödeme).</span><span class="sxs-lookup"><span data-stu-id="b3545-138">Flexible pricing (pay based on usage, not for idle capacity).</span></span>

- <span data-ttu-id="b3545-139">Aşırı güvenilirlik.</span><span class="sxs-lookup"><span data-stu-id="b3545-139">Extreme reliability.</span></span>

- <span data-ttu-id="b3545-140">Geliştirilmiş uygulama hareketliliği; uygulamanızın nerede ve nasıl dağıtılandığını kolayca değiştirin.</span><span class="sxs-lookup"><span data-stu-id="b3545-140">Improved app mobility; easily change where and how your app is deployed.</span></span>

- <span data-ttu-id="b3545-141">Esnek kapasite; gerçek ihtiyaçlar temel alınabında yukarı veya aşağı ölçeklendirin.</span><span class="sxs-lookup"><span data-stu-id="b3545-141">Flexible capacity; scale up or down based on actual needs.</span></span>

<span data-ttu-id="b3545-142">Azure'da barındırılan ASP.NET Core ile web uygulamaları oluşturmak, geleneksel alternatiflere göre birçok rekabet avantajı sunar.</span><span class="sxs-lookup"><span data-stu-id="b3545-142">Building web applications with ASP.NET Core, hosted in Azure, offers many competitive advantages over traditional alternatives.</span></span> <span data-ttu-id="b3545-143">ASP.NET Core modern web uygulama geliştirme uygulamaları ve bulut barındırma senaryoları için optimize edin.</span><span class="sxs-lookup"><span data-stu-id="b3545-143">ASP.NET Core is optimized for modern web application development practices and cloud hosting scenarios.</span></span> <span data-ttu-id="b3545-144">Bu kılavuzda, bu özelliklerden en iyi şekilde yararlanmak için ASP.NET Core uygulamalarınızı nasıl tasarlayacağımızı öğreneceksiniz.</span><span class="sxs-lookup"><span data-stu-id="b3545-144">In this guide, you'll learn how to architect your ASP.NET Core applications to best take advantage of these capabilities.</span></span>

## <a name="purpose"></a><span data-ttu-id="b3545-145">Amaç</span><span class="sxs-lookup"><span data-stu-id="b3545-145">Purpose</span></span>

<span data-ttu-id="b3545-146">Bu kılavuz, ASP.NET Core ve Azure kullanarak *yekpare* web uygulamaları oluşturma konusunda uçlardan uca kılavuz sağlar.</span><span class="sxs-lookup"><span data-stu-id="b3545-146">This guide provides end-to-end guidance on building *monolithic* web applications using ASP.NET Core and Azure.</span></span> <span data-ttu-id="b3545-147">Bu bağlamda,"yekpare", bu uygulamaların etkileşimli hizmetler ve uygulamalar topluluğu olarak değil, tek bir birim olarak dağıtılmasını ifade eder.</span><span class="sxs-lookup"><span data-stu-id="b3545-147">In this context, "monolithic" refers to the fact that these applications are deployed as a single unit, not as a collection of interacting services and applications.</span></span>

<span data-ttu-id="b3545-148">Bu kılavuz ["_.NET Microservices tamamlayıcıdır. _](../microservices/index.md) Kurumsal uygulamaları barındıracak şekilde Docker, Microservices ve Dağıtım Kapları'na odaklanan Containerized .NET Applications için Mimari.</span><span class="sxs-lookup"><span data-stu-id="b3545-148">This guide is complementary to the ["_.NET Microservices. Architecture for Containerized .NET Applications_"](../microservices/index.md) which focuses more on Docker, Microservices, and Deployment of Containers to host enterprise applications.</span></span>

### <a name="net-microservices-architecture-for-containerized-net-applications"></a><span data-ttu-id="b3545-149">.NET MikroHizmetler.</span><span class="sxs-lookup"><span data-stu-id="b3545-149">.NET Microservices.</span></span> <span data-ttu-id="b3545-150">Kapsayıcılı .NET Uygulamaları Mimarisi</span><span class="sxs-lookup"><span data-stu-id="b3545-150">Architecture for Containerized .NET Applications</span></span>

- <span data-ttu-id="b3545-151">**e-kitap**</span><span class="sxs-lookup"><span data-stu-id="b3545-151">**e-book**</span></span>  
  <https://aka.ms/MicroservicesEbook>
- <span data-ttu-id="b3545-152">**Örnek Uygulama**</span><span class="sxs-lookup"><span data-stu-id="b3545-152">**Sample Application**</span></span>  
  <https://aka.ms/microservicesarchitecture>

## <a name="who-should-use-this-guide"></a><span data-ttu-id="b3545-153">Bu kılavuzu kimler kullanmalı?</span><span class="sxs-lookup"><span data-stu-id="b3545-153">Who should use this guide</span></span>

<span data-ttu-id="b3545-154">Bu kılavuzun hedef kitlesi, bulutta Microsoft teknolojilerini ve hizmetlerini kullanarak modern web uygulamaları oluşturmak isteyen geliştiriciler, geliştirme yol gösterici ve mimarlardır.</span><span class="sxs-lookup"><span data-stu-id="b3545-154">The audience for this guide is mainly developers, development leads, and architects who are interested in building modern web applications using Microsoft technologies and services in the cloud.</span></span>

<span data-ttu-id="b3545-155">İkinci bir hedef kitle, ASP.NET veya Azure'u zaten tanıdık olan ve yeni veya varolan projeler için ASP.NET Core'a yükseltmenin mantıklı olup olmadığı hakkında bilgi arayan teknik karar vericilerdir.</span><span class="sxs-lookup"><span data-stu-id="b3545-155">A secondary audience is technical decision makers who are already familiar ASP.NET or Azure and are looking for information on whether it makes sense to upgrade to ASP.NET Core for new or existing projects.</span></span>

## <a name="how-you-can-use-this-guide"></a><span data-ttu-id="b3545-156">Bu kılavuzu nasıl kullanabilirsiniz?</span><span class="sxs-lookup"><span data-stu-id="b3545-156">How you can use this guide</span></span>

<span data-ttu-id="b3545-157">Bu kılavuz, modern .NET teknolojileri ve Windows Azure ile web uygulamaları oluşturmaya odaklanan nispeten küçük bir belgeye sıkıştırılmıştır.</span><span class="sxs-lookup"><span data-stu-id="b3545-157">This guide has been condensed into a relatively small document that focuses on building web applications with modern .NET technologies and Windows Azure.</span></span> <span data-ttu-id="b3545-158">Bu nedenle, bu tür uygulamalar ve teknik hususlar anlayış bir temel sağlamak için bütünüyle okunabilir.</span><span class="sxs-lookup"><span data-stu-id="b3545-158">As such, it can be read in its entirety to provide a foundation of understanding such applications and their technical considerations.</span></span> <span data-ttu-id="b3545-159">Kılavuz, örnek uygulamasıyla birlikte, bir başlangıç noktası veya başvuru olarak da hizmet verebilir.</span><span class="sxs-lookup"><span data-stu-id="b3545-159">The guide, along with its sample application, can also serve as a starting point or reference.</span></span> <span data-ttu-id="b3545-160">İlişkili örnek uygulamayı kendi uygulamalarınız için şablon olarak veya uygulamanızın bileşen parçalarını nasıl düzenleyebileceğini görmek için kullanın.</span><span class="sxs-lookup"><span data-stu-id="b3545-160">Use the associated sample application as a template for your own applications, or to see how you might organize your application's component parts.</span></span> <span data-ttu-id="b3545-161">Kendi uygulamanız için bu seçenekleri değerlendirirken kılavuzun ilkelerine ve mimari ve teknoloji seçeneklerinin ve karar konularının kapsamına bakın.</span><span class="sxs-lookup"><span data-stu-id="b3545-161">Refer back to the guide's principles and coverage of architecture and technology options and decision considerations when you're weighing these choices for your own application.</span></span>

<span data-ttu-id="b3545-162">Bu hususların ve fırsatların ortak bir şekilde anlaşılmasını sağlamaya yardımcı olmak için bu kılavuzu ekibinize iletmekten çekinmeyin.</span><span class="sxs-lookup"><span data-stu-id="b3545-162">Feel free to forward this guide to your team to help ensure a common understanding of these considerations and opportunities.</span></span> <span data-ttu-id="b3545-163">Herkesin ortak bir terminoloji ve temel ilkeler den çalışması mimari örüntü lerin ve uygulamaların tutarlı bir şekilde uygulanmasını sağlamaya yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="b3545-163">Having everybody working from a common set of terminology and underlying principles helps ensure consistent application of architectural patterns and practices.</span></span>

## <a name="references"></a><span data-ttu-id="b3545-164">Başvurular</span><span class="sxs-lookup"><span data-stu-id="b3545-164">References</span></span>

- <span data-ttu-id="b3545-165">**Sunucu uygulamaları için .NET Core ile .NET Framework arasında seçim yapma**</span><span class="sxs-lookup"><span data-stu-id="b3545-165">**Choosing between .NET Core and .NET Framework for server apps**</span></span>  
  [https://docs.microsoft.com/dotnet/standard/choosing-core-framework-server](../../standard/choosing-core-framework-server.md)

>[!div class="step-by-step"]
>[<span data-ttu-id="b3545-166">Sonraki</span><span class="sxs-lookup"><span data-stu-id="b3545-166">Next</span></span>](modern-web-applications-characteristics.md)
