---
title: ASP.NET Core ve Azure ile modern web uygulamaları tasarlama
description: ASP.NET Core ve Azure kullanarak tek parça web uygulamaları oluşturmaya uçtan uca yönergeler sağlar. bir kılavuz.
author: ardalis
ms.author: wiwagn
ms.date: 01/30/2019
ms.openlocfilehash: 0b29a407ae18f3ce0c7499c75ee3c888296102c2
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65639305"
---
# <a name="architect-modern-web-applications-with-aspnet-core-and-azure"></a><span data-ttu-id="14aff-103">ASP.NET Core ve Azure ile modern Web uygulamaları tasarlama</span><span class="sxs-lookup"><span data-stu-id="14aff-103">Architect Modern Web Applications with ASP.NET Core and Azure</span></span>

![Görüntü mimari Modern Web uygulamaları Kılavuzu'nun kapsar.](./media/index/web-application-guide-cover-image.png)

<span data-ttu-id="14aff-105">TARAFINDAN YAYIMLANAN</span><span class="sxs-lookup"><span data-stu-id="14aff-105">PUBLISHED BY</span></span>

<span data-ttu-id="14aff-106">Microsoft Geliştirici bölme, .NET ve Visual Studio ürün takımları</span><span class="sxs-lookup"><span data-stu-id="14aff-106">Microsoft Developer Division, .NET, and Visual Studio product teams</span></span>

<span data-ttu-id="14aff-107">Microsoft Corporation'ın bir bölme</span><span class="sxs-lookup"><span data-stu-id="14aff-107">A division of Microsoft Corporation</span></span>

<span data-ttu-id="14aff-108">One Microsoft Way</span><span class="sxs-lookup"><span data-stu-id="14aff-108">One Microsoft Way</span></span>

<span data-ttu-id="14aff-109">Redmond, Washington 98052-6399</span><span class="sxs-lookup"><span data-stu-id="14aff-109">Redmond, Washington 98052-6399</span></span>

<span data-ttu-id="14aff-110">Telif Hakkı © Microsoft Corporation 2019</span><span class="sxs-lookup"><span data-stu-id="14aff-110">Copyright © 2019 by Microsoft Corporation</span></span>

<span data-ttu-id="14aff-111">Tüm hakları saklıdır.</span><span class="sxs-lookup"><span data-stu-id="14aff-111">All rights reserved.</span></span> <span data-ttu-id="14aff-112">Bu kitap içeriğini bir parçası çoğaltılamaz veya herhangi bir araçla yayımcı yazılı izni olmadan herhangi bir biçimdeki aktarılamaz.</span><span class="sxs-lookup"><span data-stu-id="14aff-112">No part of the contents of this book may be reproduced or transmitted in any form or by any means without the written permission of the publisher.</span></span>

<span data-ttu-id="14aff-113">Bu kitap sağlanan "olarak-olduğunu" ve yazarın görünümleri ve düşünceleri son derece ifade eder.</span><span class="sxs-lookup"><span data-stu-id="14aff-113">This book is provided “as-is” and expresses the author’s views and opinions.</span></span> <span data-ttu-id="14aff-114">Görünümleri ve düşünceleri son derece bilgi URL ve diğer Internet Web sitesi referansları da dahil olmak üzere bu kitap, ifade verilmeksizin değiştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="14aff-114">The views, opinions and information expressed in this book, including URL and other Internet website references, may change without notice.</span></span>

<span data-ttu-id="14aff-115">Burada açıklanan bazı örnekler yalnızca çizim için sağlanmıştır ve bu kurgusaldır.</span><span class="sxs-lookup"><span data-stu-id="14aff-115">Some examples depicted herein are provided for illustration only and are fictitious.</span></span> <span data-ttu-id="14aff-116">Gerçek bir ilişki veya bağlantı amaçlanmamıştır veya çıkarılmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="14aff-116">No real association or connection is intended or should be inferred.</span></span>

<span data-ttu-id="14aff-117">Microsoft ve adresinde listelenmiş ticari https://www.microsoft.com "Ticari" Web sayfasında Microsoft şirketler grubunun ticari markalarıdır.</span><span class="sxs-lookup"><span data-stu-id="14aff-117">Microsoft and the trademarks listed at https://www.microsoft.com on the “Trademarks” webpage are trademarks of the Microsoft group of companies.</span></span>

<span data-ttu-id="14aff-118">Mac ve macOS Apple Inc.'in ticari markalarıdır.</span><span class="sxs-lookup"><span data-stu-id="14aff-118">Mac and macOS are trademarks of Apple Inc.</span></span>

<span data-ttu-id="14aff-119">Docker whale logosu, Docker, Inc.'in kayıtlı ticari markasıdır. İzni tarafından kullanılır.</span><span class="sxs-lookup"><span data-stu-id="14aff-119">The Docker whale logo is a registered trademark of Docker, Inc. Used by permission.</span></span>

<span data-ttu-id="14aff-120">Diğer tüm işaretleri ve logoları sahiplerinin özelliği var.</span><span class="sxs-lookup"><span data-stu-id="14aff-120">All other marks and logos are property of their respective owners.</span></span>

<span data-ttu-id="14aff-121">Yazar:</span><span class="sxs-lookup"><span data-stu-id="14aff-121">Author:</span></span>

> <span data-ttu-id="14aff-122">**Steve "ardalis" Smith** - yazılım mühendisi ve Eğitmen - [Ardalis.com](https://ardalis.com)</span><span class="sxs-lookup"><span data-stu-id="14aff-122">**Steve "ardalis" Smith** - Software Architect and Trainer - [Ardalis.com](https://ardalis.com)</span></span>

<span data-ttu-id="14aff-123">Düzenleyiciler:</span><span class="sxs-lookup"><span data-stu-id="14aff-123">Editors:</span></span>

> <span data-ttu-id="14aff-124">**Maira Wenzel**</span><span class="sxs-lookup"><span data-stu-id="14aff-124">**Maira Wenzel**</span></span>

## <a name="introduction"></a><span data-ttu-id="14aff-125">Giriş</span><span class="sxs-lookup"><span data-stu-id="14aff-125">Introduction</span></span>

<span data-ttu-id="14aff-126">.NET core ve ASP.NET Core geleneksel .NET geliştirme kıyasla çeşitli avantajlar sunar.</span><span class="sxs-lookup"><span data-stu-id="14aff-126">.NET Core and ASP.NET Core offer several advantages over traditional .NET development.</span></span> <span data-ttu-id="14aff-127">Aşağıdakilerin tümü veya uygulamanızın başarısı için önemli ise, sunucu uygulamaları için .NET Core kullanmanız gerekir:</span><span class="sxs-lookup"><span data-stu-id="14aff-127">You should use .NET Core for your server applications if some or all of the following are important to your application's success:</span></span>

- <span data-ttu-id="14aff-128">Platformlar arası desteği.</span><span class="sxs-lookup"><span data-stu-id="14aff-128">Cross-platform support.</span></span>

- <span data-ttu-id="14aff-129">Mikro hizmetler kullanın.</span><span class="sxs-lookup"><span data-stu-id="14aff-129">Use of microservices.</span></span>

- <span data-ttu-id="14aff-130">Docker kapsayıcılarını kullanın.</span><span class="sxs-lookup"><span data-stu-id="14aff-130">Use of Docker containers.</span></span>

- <span data-ttu-id="14aff-131">Yüksek performans ve ölçeklenebilirlik gereksinimleri.</span><span class="sxs-lookup"><span data-stu-id="14aff-131">High performance and scalability requirements.</span></span>

- <span data-ttu-id="14aff-132">Uygulama ile aynı sunucuya .NET sürümlerinin yan yana sürüm oluşturma.</span><span class="sxs-lookup"><span data-stu-id="14aff-132">Side-by-side versioning of .NET versions by application on the same server.</span></span>

<span data-ttu-id="14aff-133">Geleneksel .NET uygulamalar yapın ve bu gereksinimlerin çoğu destekler, ancak yukarıdaki senaryoları için geliştirilmiş destek sunmak için ASP.NET Core ve .NET Core getirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="14aff-133">Traditional .NET applications can and do support many of these requirements, but ASP.NET Core and .NET Core have been optimized to offer improved support for the above scenarios.</span></span>

<span data-ttu-id="14aff-134">Microsoft Azure gibi hizmetleri kullanarak bulutta web uygulamalarını barındırmak giderek daha fazla kuruluşların seçim.</span><span class="sxs-lookup"><span data-stu-id="14aff-134">More and more organizations are choosing to host their web applications in the cloud using services like Microsoft Azure.</span></span> <span data-ttu-id="14aff-135">Aşağıda, uygulama veya kuruluşunuz için önemliyse, uygulamanızı bulutta barındırma dikkate almanız gerekir:</span><span class="sxs-lookup"><span data-stu-id="14aff-135">You should consider hosting your application in the cloud if the following are important to your application or organization:</span></span>

- <span data-ttu-id="14aff-136">Daha az yatırım veri merkezi maliyetlerini (donanım, yazılım, boşluk, yardımcı programlar, sunucu yönetimi, vb.)</span><span class="sxs-lookup"><span data-stu-id="14aff-136">Reduced investment in data center costs (hardware, software, space, utilities, server management, etc.)</span></span>

- <span data-ttu-id="14aff-137">Esnek fiyatlandırma (boş kapasite için değil, kullanıma bağlı olarak ödeme).</span><span class="sxs-lookup"><span data-stu-id="14aff-137">Flexible pricing (pay based on usage, not for idle capacity).</span></span>

- <span data-ttu-id="14aff-138">Extreme güvenilirlik.</span><span class="sxs-lookup"><span data-stu-id="14aff-138">Extreme reliability.</span></span>

- <span data-ttu-id="14aff-139">Gelişmiş uygulama taşınabilirliği; kolayca uygulamanızı nerede ve nasıl dağıtılır.</span><span class="sxs-lookup"><span data-stu-id="14aff-139">Improved app mobility; easily change where and how your app is deployed.</span></span>

- <span data-ttu-id="14aff-140">Esnek Kapasite; ölçeği artırın veya göre gerçek ihtiyaçları azaltın.</span><span class="sxs-lookup"><span data-stu-id="14aff-140">Flexible capacity; scale up or down based on actual needs.</span></span>

<span data-ttu-id="14aff-141">ASP.NET Core, Azure üzerinde barındırılan Web uygulamalarıyla geleneksel alternatifleri rekabetçi birçok avantaj sunar.</span><span class="sxs-lookup"><span data-stu-id="14aff-141">Building web applications with ASP.NET Core, hosted in Azure, offers many competitive advantages over traditional alternatives.</span></span> <span data-ttu-id="14aff-142">ASP.NET Core, modern bir web uygulaması geliştirme uygulamaları ve bulut barındırma senaryoları için optimize edilmiştir.</span><span class="sxs-lookup"><span data-stu-id="14aff-142">ASP.NET Core is optimized for modern web application development practices and cloud hosting scenarios.</span></span> <span data-ttu-id="14aff-143">Bu kılavuzda, bu özellikler en iyi şekilde yararlanmak için ASP.NET Core uygulamalarınızı tasarlama öğreneceksiniz.</span><span class="sxs-lookup"><span data-stu-id="14aff-143">In this guide, you'll learn how to architect your ASP.NET Core applications to best take advantage of these capabilities.</span></span>

## <a name="purpose"></a><span data-ttu-id="14aff-144">Amaç</span><span class="sxs-lookup"><span data-stu-id="14aff-144">Purpose</span></span>

<span data-ttu-id="14aff-145">Bu kılavuz, uygulama oluşturmaya uçtan uca yönergeler sağlar *tek parça* web uygulamaları ASP.NET Core ve Azure kullanarak.</span><span class="sxs-lookup"><span data-stu-id="14aff-145">This guide provides end-to-end guidance on building *monolithic* web applications using ASP.NET Core and Azure.</span></span> <span data-ttu-id="14aff-146">Bu bağlamda, bu uygulamaların etkileşim kuran hizmetler ve uygulamalar koleksiyonu olarak değil, tek bir birim olarak dağıtıldığını olgu "tek parça" ifade eder.</span><span class="sxs-lookup"><span data-stu-id="14aff-146">In this context, "monolithic" refers to the fact that these applications are deployed as a single unit, not as a collection of interacting services and applications.</span></span>

<span data-ttu-id="14aff-147">Bu kılavuz için tamamlayıcı ["_.NET mikro Hizmetleri. Kapsayıcılı .NET uygulamaları mimarisi_"](../microservices-architecture/index.md) hangi odaklanır daha fazla üzerinde Docker, mikro hizmetler ve kapsayıcılar dağıtımının Kurumsal uygulamalarını barındırmak için.</span><span class="sxs-lookup"><span data-stu-id="14aff-147">This guide is complementary to the ["_.NET Microservices. Architecture for Containerized .NET Applications_"](../microservices-architecture/index.md) which focuses more on Docker, Microservices, and Deployment of Containers to host enterprise applications.</span></span>

### <a name="net-microservices-architecture-for-containerized-net-applications"></a><span data-ttu-id="14aff-148">.NET mikro Hizmetleri.</span><span class="sxs-lookup"><span data-stu-id="14aff-148">.NET Microservices.</span></span> <span data-ttu-id="14aff-149">Kapsayıcılı .NET Uygulamaları Mimarisi</span><span class="sxs-lookup"><span data-stu-id="14aff-149">Architecture for Containerized .NET Applications</span></span>

- <span data-ttu-id="14aff-150">**e-kitabı**</span><span class="sxs-lookup"><span data-stu-id="14aff-150">**e-book**</span></span>  
  <https://aka.ms/MicroservicesEbook>
- <span data-ttu-id="14aff-151">**Örnek uygulama**</span><span class="sxs-lookup"><span data-stu-id="14aff-151">**Sample Application**</span></span>  
  <https://aka.ms/microservicesarchitecture>

## <a name="who-should-use-this-guide"></a><span data-ttu-id="14aff-152">Bu kılavuzda kullanan</span><span class="sxs-lookup"><span data-stu-id="14aff-152">Who should use this guide</span></span>

<span data-ttu-id="14aff-153">Bu kılavuz için İzleyici ağırlıklı olarak geliştiriciler, geliştirme Liderleri ve bulutta Microsoft teknolojileri ve Hizmetleri kullanarak modern web uygulamaları oluşturmak istiyorsanız mimarları olduğu.</span><span class="sxs-lookup"><span data-stu-id="14aff-153">The audience for this guide is mainly developers, development leads, and architects who are interested in building modern web applications using Microsoft technologies and services in the cloud.</span></span>

<span data-ttu-id="14aff-154">İkincil bir dinleyici zaten bilinen ASP.NET veya Azure ve ASP.NET Core için yeni veya mevcut projeleri için yükseltme mantıklı olup olmadığı hakkında bilgi arıyorsanız, teknik karar verenler ' dir.</span><span class="sxs-lookup"><span data-stu-id="14aff-154">A secondary audience is technical decision makers who are already familiar ASP.NET or Azure and are looking for information on whether it makes sense to upgrade to ASP.NET Core for new or existing projects.</span></span>

## <a name="how-you-can-use-this-guide"></a><span data-ttu-id="14aff-155">Nasıl bu kılavuzu kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="14aff-155">How you can use this guide</span></span>

<span data-ttu-id="14aff-156">Bu kılavuz, modern .NET teknolojileri ve Windows Azure ile web uygulamaları oluşturmaya odaklanan görece küçük bir belgenin içine sıkıştırılmış.</span><span class="sxs-lookup"><span data-stu-id="14aff-156">This guide has been condensed into a relatively small document that focuses on building web applications with modern .NET technologies and Windows Azure.</span></span> <span data-ttu-id="14aff-157">Bu nedenle, bu tür uygulamalar ve bunların teknik konuları anlamanın sağlamasıdır için tamamen okunabilir.</span><span class="sxs-lookup"><span data-stu-id="14aff-157">As such, it can be read in its entirety to provide a foundation of understanding such applications and their technical considerations.</span></span> <span data-ttu-id="14aff-158">Birlikte, örnek uygulama Kılavuzu, ayrıca bir başlangıç noktası veya başvuru hizmet verebilir.</span><span class="sxs-lookup"><span data-stu-id="14aff-158">The guide, along with its sample application, can also serve as a starting point or reference.</span></span> <span data-ttu-id="14aff-159">İlişkili örnek uygulama için kendi uygulamalarınızı ya da uygulamanızın bileşen parçalarına nasıl düzenleyebileceğini görmek için bir şablon olarak kullanın.</span><span class="sxs-lookup"><span data-stu-id="14aff-159">Use the associated sample application as a template for your own applications, or to see how you might organize your application's component parts.</span></span> <span data-ttu-id="14aff-160">Kendi uygulamanız için bu seçenekleri ağırlığıyla olduğunda geri kılavuz ilkeleri ve mimarisi ve teknolojisi seçeneklerini ve karar konuları kapsamını bakın.</span><span class="sxs-lookup"><span data-stu-id="14aff-160">Refer back to the guide's principles and coverage of architecture and technology options and decision considerations when you're weighing these choices for your own application.</span></span>

<span data-ttu-id="14aff-161">Bu noktalar ve fırsatlar genel olarak anladığından emin olmak için bu kılavuzu takımınıza iletmek çekinmeyin.</span><span class="sxs-lookup"><span data-stu-id="14aff-161">Feel free to forward this guide to your team to help ensure a common understanding of these considerations and opportunities.</span></span> <span data-ttu-id="14aff-162">Herkesin sahip ortak bir dizi terminolojisi çalışma ve ilkeler temel mimari desenleri ve uygulamaları tutarlı uygulama sağlamaya yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="14aff-162">Having everybody working from a common set of terminology and underlying principles helps ensure consistent application of architectural patterns and practices.</span></span>

## <a name="references"></a><span data-ttu-id="14aff-163">Referanslar</span><span class="sxs-lookup"><span data-stu-id="14aff-163">References</span></span>

- <span data-ttu-id="14aff-164">**Sunucu uygulamaları için .NET Core ile .NET Framework arasında seçim yapma**</span><span class="sxs-lookup"><span data-stu-id="14aff-164">**Choosing between .NET Core and .NET Framework for server apps**</span></span>  
  [https://docs.microsoft.com/dotnet/standard/choosing-core-framework-server](../choosing-core-framework-server.md)

>[!div class="step-by-step"]
>[<span data-ttu-id="14aff-165">Next</span><span class="sxs-lookup"><span data-stu-id="14aff-165">Next</span></span>](modern-web-applications-characteristics.md)
