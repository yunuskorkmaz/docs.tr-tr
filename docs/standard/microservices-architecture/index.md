---
title: .NET mikro Hizmetleri. Kapsayıcılı .NET uygulamaları mimarisi
description: Kapsayıcılı .NET uygulamaları için .NET mikro hizmet mimarisi | Mikro hizmetler, modüler ve bağımsız bir şekilde dağıtılabilen hizmetleridir. Docker kapsayıcıları (için Linux ve Windows), dağıtım ve bir hizmeti ve bağımlılıklarını ardından yalıtılmış bir ortamda çalıştırılır tek bir birim halinde paketleme tarafından test basitleştirin.
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 06/06/2018
ms.openlocfilehash: 6b57f66068409ade24eecff636b9dd3f4084fd71
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43516157"
---
![](./media/cover.png)

# <a name="net-microservices-architecture-for-containerized-net-applications"></a><span data-ttu-id="75ad7-105">.NET mikro Hizmetleri.</span><span class="sxs-lookup"><span data-stu-id="75ad7-105">.NET Microservices.</span></span> <span data-ttu-id="75ad7-106">Kapsayıcılı .NET uygulamaları mimarisi</span><span class="sxs-lookup"><span data-stu-id="75ad7-106">Architecture for Containerized .NET Applications</span></span>

<span data-ttu-id="75ad7-107">İNDİRME bulunabilir: <https://aka.ms/microservicesebook></span><span class="sxs-lookup"><span data-stu-id="75ad7-107">DOWNLOAD available at: <https://aka.ms/microservicesebook></span></span>

<span data-ttu-id="75ad7-108">TARAFINDAN YAYIMLANAN</span><span class="sxs-lookup"><span data-stu-id="75ad7-108">PUBLISHED BY</span></span>

<span data-ttu-id="75ad7-109">Microsoft Geliştirici bölme, .NET ve Visual Studio ürün takımları</span><span class="sxs-lookup"><span data-stu-id="75ad7-109">Microsoft Developer Division, .NET and Visual Studio product teams</span></span>

<span data-ttu-id="75ad7-110">Microsoft Corporation'ın bir bölme</span><span class="sxs-lookup"><span data-stu-id="75ad7-110">A division of Microsoft Corporation</span></span>

<span data-ttu-id="75ad7-111">One Microsoft Way</span><span class="sxs-lookup"><span data-stu-id="75ad7-111">One Microsoft Way</span></span>

<span data-ttu-id="75ad7-112">Redmond, Washington 98052-6399</span><span class="sxs-lookup"><span data-stu-id="75ad7-112">Redmond, Washington 98052-6399</span></span>

<span data-ttu-id="75ad7-113">Telif Hakkı © 2018 Microsoft Corporation</span><span class="sxs-lookup"><span data-stu-id="75ad7-113">Copyright © 2018 by Microsoft Corporation</span></span>

<span data-ttu-id="75ad7-114">Tüm hakları saklıdır.</span><span class="sxs-lookup"><span data-stu-id="75ad7-114">All rights reserved.</span></span> <span data-ttu-id="75ad7-115">Bu kitap içeriğini bir parçası çoğaltılamaz veya herhangi bir araçla yayımcı yazılı izni olmadan herhangi bir biçimdeki aktarılamaz.</span><span class="sxs-lookup"><span data-stu-id="75ad7-115">No part of the contents of this book may be reproduced or transmitted in any form or by any means without the written permission of the publisher.</span></span>

<span data-ttu-id="75ad7-116">Bu kitap sağlanan "olarak-olduğunu" ve yazarın görünümleri ve düşünceleri son derece ifade eder.</span><span class="sxs-lookup"><span data-stu-id="75ad7-116">This book is provided “as-is” and expresses the author’s views and opinions.</span></span> <span data-ttu-id="75ad7-117">Görünümleri ve düşünceleri son derece bilgi URL ve diğer Internet Web sitesi referansları da dahil olmak üzere bu kitap, ifade verilmeksizin değiştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="75ad7-117">The views, opinions and information expressed in this book, including URL and other Internet website references, may change without notice.</span></span>

<span data-ttu-id="75ad7-118">Burada açıklanan bazı örnekler yalnızca çizim için sağlanmıştır ve bu kurgusaldır.</span><span class="sxs-lookup"><span data-stu-id="75ad7-118">Some examples depicted herein are provided for illustration only and are fictitious.</span></span> <span data-ttu-id="75ad7-119">Gerçek bir ilişki veya bağlantı amaçlanmamıştır veya çıkarılmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="75ad7-119">No real association or connection is intended or should be inferred.</span></span>

<span data-ttu-id="75ad7-120">Microsoft ve adresinde listelenmiş ticari http://www.microsoft.com "Ticari" Web sayfasında Microsoft şirketler grubunun ticari markalarıdır.</span><span class="sxs-lookup"><span data-stu-id="75ad7-120">Microsoft and the trademarks listed at http://www.microsoft.com on the “Trademarks” webpage are trademarks of the Microsoft group of companies.</span></span>

<span data-ttu-id="75ad7-121">Mac ve macOS Apple Inc.'in ticari markalarıdır.</span><span class="sxs-lookup"><span data-stu-id="75ad7-121">Mac and macOS are trademarks of Apple Inc.</span></span>

<span data-ttu-id="75ad7-122">Docker whale logosu, Docker, Inc.'in kayıtlı ticari markasıdır. İzni tarafından kullanılır.</span><span class="sxs-lookup"><span data-stu-id="75ad7-122">The Docker whale logo is a registered trademark of Docker, Inc. Used by permission.</span></span>

<span data-ttu-id="75ad7-123">Diğer tüm işaretleri ve logoları sahiplerinin özelliği var.</span><span class="sxs-lookup"><span data-stu-id="75ad7-123">All other marks and logos are property of their respective owners.</span></span>

<span data-ttu-id="75ad7-124">Ortak yazarlar:</span><span class="sxs-lookup"><span data-stu-id="75ad7-124">Co-Authors:</span></span>

> <span data-ttu-id="75ad7-125">**Cesar de la Torre**, üst düzey PM, .NET ürün ekibi, Microsoft Corp.</span><span class="sxs-lookup"><span data-stu-id="75ad7-125">**Cesar de la Torre**, Sr. PM, .NET product team, Microsoft Corp.</span></span>
>
> <span data-ttu-id="75ad7-126">**Fatura Wagner**, üst düzey İçerik geliştirici, C + E, Microsoft Corp.</span><span class="sxs-lookup"><span data-stu-id="75ad7-126">**Bill Wagner**, Sr. Content Developer, C+E, Microsoft Corp.</span></span>
>
> <span data-ttu-id="75ad7-127">**Mike Rousos**, baş yazılım mühendisi, Devdiv'e CAT ekibi, Microsoft</span><span class="sxs-lookup"><span data-stu-id="75ad7-127">**Mike Rousos**, Principal Software Engineer, DevDiv CAT team, Microsoft</span></span>

<span data-ttu-id="75ad7-128">Düzenleyiciler:</span><span class="sxs-lookup"><span data-stu-id="75ad7-128">Editors:</span></span>

> <span data-ttu-id="75ad7-129">**Mike Pope**</span><span class="sxs-lookup"><span data-stu-id="75ad7-129">**Mike Pope**</span></span>
>
> <span data-ttu-id="75ad7-130">**Steve Hoag**</span><span class="sxs-lookup"><span data-stu-id="75ad7-130">**Steve Hoag**</span></span>

<span data-ttu-id="75ad7-131">Katılımcılar ve gözden geçirenler:</span><span class="sxs-lookup"><span data-stu-id="75ad7-131">Participants and reviewers:</span></span>

> <span data-ttu-id="75ad7-132">**Jeffrey Richter**, iş ortağı yazılım Mühendisliği, Azure ekibi, Microsoft</span><span class="sxs-lookup"><span data-stu-id="75ad7-132">**Jeffrey Richter**, Partner Software Eng, Azure team, Microsoft</span></span>
>
> <span data-ttu-id="75ad7-133">**Jimmy Bogard**, Headspring, baş Mimar</span><span class="sxs-lookup"><span data-stu-id="75ad7-133">**Jimmy Bogard**, Chief Architect at Headspring</span></span>
>
> <span data-ttu-id="75ad7-134">**UDI Dahan**, kurucu ve CEO, belirli yazılım</span><span class="sxs-lookup"><span data-stu-id="75ad7-134">**Udi Dahan**, Founder & CEO, Particular Software</span></span>
>
> <span data-ttu-id="75ad7-135">**Jimmy Nilsson**, ortak kurucu ve CEO, Factor10</span><span class="sxs-lookup"><span data-stu-id="75ad7-135">**Jimmy Nilsson**, Co-founder and CEO of Factor10</span></span>
>
> <span data-ttu-id="75ad7-136">**Glenn Condron**, üst düzey Program Yöneticisi, ASP.NET takımı</span><span class="sxs-lookup"><span data-stu-id="75ad7-136">**Glenn Condron**, Sr. Program Manager, ASP.NET team</span></span>
>
> <span data-ttu-id="75ad7-137">**İşareti Fussell**, asıl PM lideri, Microsoft Azure Service Fabric ekibi</span><span class="sxs-lookup"><span data-stu-id="75ad7-137">**Mark Fussell**, Principal PM Lead, Azure Service Fabric team, Microsoft</span></span>
>
> <span data-ttu-id="75ad7-138">**Diego Vega**, PM lideri, Entity Framework takım, Microsoft</span><span class="sxs-lookup"><span data-stu-id="75ad7-138">**Diego Vega**, PM Lead, Entity Framework team, Microsoft</span></span>
>
> <span data-ttu-id="75ad7-139">**Barry Dorrans**, üst düzey Güvenlik Program Yöneticisi</span><span class="sxs-lookup"><span data-stu-id="75ad7-139">**Barry Dorrans**, Sr. Security Program Manager</span></span>
>
> <span data-ttu-id="75ad7-140">**Rowan Miller**, üst düzey Program Yöneticisi, Microsoft</span><span class="sxs-lookup"><span data-stu-id="75ad7-140">**Rowan Miller**, Sr. Program Manager, Microsoft</span></span>
>
> <span data-ttu-id="75ad7-141">**Ankit Asthana**, baş PM Yöneticisi, Microsoft .NET ekibi</span><span class="sxs-lookup"><span data-stu-id="75ad7-141">**Ankit Asthana**, Principal PM Manager, .NET team, Microsoft</span></span>
>
> <span data-ttu-id="75ad7-142">**Scott Hunter**, .NET ekibi, Microsoft iş ortağı Direktörü PM</span><span class="sxs-lookup"><span data-stu-id="75ad7-142">**Scott Hunter**, Partner Director PM, .NET team, Microsoft</span></span>
>
> <span data-ttu-id="75ad7-143">**Dylan Reisenberger**, Mimar ve Polly Bykov'un geliştirme</span><span class="sxs-lookup"><span data-stu-id="75ad7-143">**Dylan Reisenberger**, Architect and Dev Lead at Polly</span></span>
>
> <span data-ttu-id="75ad7-144">**Steve Smith**, yazılım mesleğini geliştirme & ASPSmith Ltd., eğitmen</span><span class="sxs-lookup"><span data-stu-id="75ad7-144">**Steve Smith**, Software Craftsman & Trainer at ASPSmith Ltd.</span></span>
>
> <span data-ttu-id="75ad7-145">**Ian Cooper**, kodlama mimari en parlak</span><span class="sxs-lookup"><span data-stu-id="75ad7-145">**Ian Cooper**, Coding Architect at Brighter</span></span>
>
> <span data-ttu-id="75ad7-146">**Unai Zorrilla**, mimari ve geliştirme Bykov'un düz kavramları</span><span class="sxs-lookup"><span data-stu-id="75ad7-146">**Unai Zorrilla**, Architect and Dev Lead at Plain Concepts</span></span>
>
> <span data-ttu-id="75ad7-147">**Eduard Tomas**, geliştirme Bykov'un düz kavramları</span><span class="sxs-lookup"><span data-stu-id="75ad7-147">**Eduard Tomas**, Dev Lead at Plain Concepts</span></span>
>
> <span data-ttu-id="75ad7-148">**Ramon Tomas**, düz kavramları geliştiricisi</span><span class="sxs-lookup"><span data-stu-id="75ad7-148">**Ramon Tomas**, Developer at Plain Concepts</span></span>
>
> <span data-ttu-id="75ad7-149">**David Sanz**, düz kavramları geliştiricisi</span><span class="sxs-lookup"><span data-stu-id="75ad7-149">**David Sanz**, Developer at Plain Concepts</span></span>
>
> <span data-ttu-id="75ad7-150">**Javier Valero**, Enformasyon Müdürü Grupo çözümleri işletim</span><span class="sxs-lookup"><span data-stu-id="75ad7-150">**Javier Valero**, Chief Operating Officer at Grupo Solutio</span></span>
>
> <span data-ttu-id="75ad7-151">**Pierre Millet**, üst düzey Danışman, Microsoft</span><span class="sxs-lookup"><span data-stu-id="75ad7-151">**Pierre Millet**, Sr. Consultant, Microsoft</span></span>
>
> <span data-ttu-id="75ad7-152">**Michael Friis**, ürün Yöneticisi, Docker Inc.</span><span class="sxs-lookup"><span data-stu-id="75ad7-152">**Michael Friis**, Product Manager, Docker Inc</span></span>
>
> <span data-ttu-id="75ad7-153">**Charles Lowell**, yazılım mühendisi, VS CAT ekibi, Microsoft</span><span class="sxs-lookup"><span data-stu-id="75ad7-153">**Charles Lowell**, Software Engineer, VS CAT team, Microsoft</span></span>

## <a name="introduction"></a><span data-ttu-id="75ad7-154">Giriş</span><span class="sxs-lookup"><span data-stu-id="75ad7-154">Introduction</span></span>

<span data-ttu-id="75ad7-155">Kuruluşların giderek daha fazla maliyet tasarrufu taahhüdünü gerçekleştirmeye dağıtım sorunlarını giderme ve kapsayıcıları kullanarak DevOps ve üretim işlemleri iyileştirme.</span><span class="sxs-lookup"><span data-stu-id="75ad7-155">Enterprises are increasingly realizing cost savings, solving deployment problems, and improving DevOps and production operations by using containers.</span></span> <span data-ttu-id="75ad7-156">Microsoft Windows ve Linux kapsayıcı yenilikten Azure Container Service ve Azure Service Fabric gibi ürünleri oluşturarak ve Docker, Mesosphere ve Kubernetes gibi sektör öncüleri ile işbirliği yapan mıt'li serbest.</span><span class="sxs-lookup"><span data-stu-id="75ad7-156">Microsoft has been releasing container innovations for Windows and Linux by creating products like Azure Container Service and Azure Service Fabric, and by partnering with industry leaders like Docker, Mesosphere, and Kubernetes.</span></span> <span data-ttu-id="75ad7-157">Bu ürünler, bulut hızı ve ölçeği, hangi uygulamaları derlemeye ve dağıtmaya şirketlerin yardımcı kapsayıcı çözümler sunmak kendi seçtiğiniz platform veya araçları.</span><span class="sxs-lookup"><span data-stu-id="75ad7-157">These products deliver container solutions that help companies build and deploy applications at cloud speed and scale, whatever their choice of platform or tools.</span></span>

<span data-ttu-id="75ad7-158">Docker kapsayıcı sektördeki en önemli Windows ve Linux eko satıcılar tarafından desteklenen, pratikte bir standart hale gelmektedir.</span><span class="sxs-lookup"><span data-stu-id="75ad7-158">Docker is becoming the de facto standard in the container industry, supported by the most significant vendors in the Windows and Linux ecosystems.</span></span> <span data-ttu-id="75ad7-159">(Microsoft, Docker'ı destekleyen temel bulut satıcıları biridir.) Gelecekte, Docker büyük olasılıkla bulutta veya şirket içinde herhangi bir veri merkezinde bulunabilen olacaktır.</span><span class="sxs-lookup"><span data-stu-id="75ad7-159">(Microsoft is one of the main cloud vendors supporting Docker.) In the future, Docker will probably be ubiquitous in any datacenter in the cloud or on-premises.</span></span>

<span data-ttu-id="75ad7-160">Ayrıca, [mikro Hizmetler](https://martinfowler.com/articles/microservices.html) mimarisi Gelişmekte olan dağıtılmış görev açısından kritik uygulamalar için önemli bir yaklaşım.</span><span class="sxs-lookup"><span data-stu-id="75ad7-160">In addition, the [microservices](https://martinfowler.com/articles/microservices.html) architecture is emerging as an important approach for distributed mission-critical applications.</span></span> <span data-ttu-id="75ad7-161">Mikro hizmet tabanlı bir mimaride, uygulama koleksiyonu, test edilmiş, dağıtılan ve tutulan bağımsız olarak geliştirilebilir hizmetleri üzerinde oluşturulmuştur.</span><span class="sxs-lookup"><span data-stu-id="75ad7-161">In a microservice-based architecture, the application is built on a collection of services that can be developed, tested, deployed, and versioned independently.</span></span>

## <a name="about-this-guide"></a><span data-ttu-id="75ad7-162">Bu kılavuz hakkında</span><span class="sxs-lookup"><span data-stu-id="75ad7-162">About this guide</span></span>

<span data-ttu-id="75ad7-163">Mikro hizmet tabanlı uygulamaları geliştirmek ve bunları yönetmek için giriş niteliğindeki bu kılavuzda, kapsayıcıları kullanma.</span><span class="sxs-lookup"><span data-stu-id="75ad7-163">This guide is an introduction to developing microservices-based applications and managing them using containers.</span></span> <span data-ttu-id="75ad7-164">Mimari Tasarım açıklar ve .NET Core ve Docker kapsayıcılarını kullanarak uygulama yaklaşıyor.</span><span class="sxs-lookup"><span data-stu-id="75ad7-164">It discusses architectural design and implementation approaches using .NET Core and Docker containers.</span></span> <span data-ttu-id="75ad7-165">Kapsayıcılar ve mikro hizmetler kullanmaya başlama daha kolay hale getirmek için bir kapsayıcıya alınmış başvuru ve keşfedebilirsiniz mikro hizmet tabanlı uygulama Kılavuzu odaklanır.</span><span class="sxs-lookup"><span data-stu-id="75ad7-165">To make it easier to get started with containers and microservices, the guide focuses on a reference containerized and microservice-based application that you can explore.</span></span> <span data-ttu-id="75ad7-166">Örnek uygulamayı kullanılabilir [hizmetine](https://github.com/dotnet-architecture/eShopOnContainers) GitHub deposu.</span><span class="sxs-lookup"><span data-stu-id="75ad7-166">The sample application is available at the [eShopOnContainers](https://github.com/dotnet-architecture/eShopOnContainers) GitHub repo.</span></span>

<span data-ttu-id="75ad7-167">Bu kılavuz iki teknoloji odaklanan temel geliştirme ve öncelikli olarak geliştirme ortamı düzeyde mimari rehberlik sağlar: Docker ve .NET Core.</span><span class="sxs-lookup"><span data-stu-id="75ad7-167">This guide provides foundational development and architectural guidance primarily at a development environment level with a focus on two technologies: Docker and .NET Core.</span></span> <span data-ttu-id="75ad7-168">Bizim engellemekse altyapıya üretim ortamınızın (Bulut veya şirket içi) odaklanmadan uygulama tasarımınızı düşünürken, bu kılavuzu okumadan ' dir.</span><span class="sxs-lookup"><span data-stu-id="75ad7-168">Our intention is that you read this guide when thinking about your application design without focusing on the infrastructure (cloud or on-premises) of your production environment.</span></span> <span data-ttu-id="75ad7-169">Üretime hazır uygulamalar oluşturduğunuzda, altyapı konusunda kararlar daha sonra yapar.</span><span class="sxs-lookup"><span data-stu-id="75ad7-169">You will make decisions about your infrastructure later, when you create your production-ready applications.</span></span> <span data-ttu-id="75ad7-170">Bu nedenle, bu kılavuz dilden bağımsız ve daha fazla geliştirme ortamı-merkezli altyapı olması amaçlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="75ad7-170">Therefore, this guide is intended to be infrastructure agnostic and more development-environment-centric.</span></span>

<span data-ttu-id="75ad7-171">Bu kılavuzda eğitim sonra Microsoft Azure üzerinde üretime hazır mikro hizmetler hakkında bilgi edinmek için sonraki adımınız olacaktır.</span><span class="sxs-lookup"><span data-stu-id="75ad7-171">After you have studied this guide, your next step would be to learn about production-ready microservices on Microsoft Azure.</span></span>

## <a name="what-this-guide-does-not-cover"></a><span data-ttu-id="75ad7-172">Ne bu kılavuzda ele alınmamaktadır</span><span class="sxs-lookup"><span data-stu-id="75ad7-172">What this guide does not cover</span></span>

<span data-ttu-id="75ad7-173">Bu kılavuz, uygulama yaşam döngüsü üzerinde DevOps, CI/CD işlem hatları, odaklı değildir veya takım iş.</span><span class="sxs-lookup"><span data-stu-id="75ad7-173">This guide does not focus on the application lifecycle, DevOps, CI/CD pipelines, or team work.</span></span> <span data-ttu-id="75ad7-174">Tamamlayıcı Kılavuzu [kapsayıcılı Docker uygulaması yaşam döngüsü Microsoft Platformu ve araçları ile](https://aka.ms/dockerlifecycleebook) Bu konu üzerinde odaklanır.</span><span class="sxs-lookup"><span data-stu-id="75ad7-174">The complementary guide [Containerized Docker Application Lifecycle with Microsoft Platform and Tools](https://aka.ms/dockerlifecycleebook) focuses on that subject.</span></span> <span data-ttu-id="75ad7-175">Geçerli Kılavuz ayrıca uygulama ayrıntıları gibi belirli düzenleyicileri bilgi Azure altyapı sağlamaz.</span><span class="sxs-lookup"><span data-stu-id="75ad7-175">The current guide also does not provide implementation details on Azure infrastructure, such as information on specific orchestrators.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="75ad7-176">Ek kaynaklar</span><span class="sxs-lookup"><span data-stu-id="75ad7-176">Additional resources</span></span>

-   <span data-ttu-id="75ad7-177">**Docker uygulaması yaşam döngüsü Microsoft Platformu ve araçları ile kapsayıcılı hale** (indirilebilir e-kitap) [*https://aka.ms/dockerlifecycleebook*](https://aka.ms/dockerlifecycleebook)</span><span class="sxs-lookup"><span data-stu-id="75ad7-177">**Containerized Docker Application Lifecycle with Microsoft Platform and Tools** (downloadable e-book) [*https://aka.ms/dockerlifecycleebook*](https://aka.ms/dockerlifecycleebook)</span></span>

## <a name="who-should-use-this-guide"></a><span data-ttu-id="75ad7-178">Bu kılavuzda kullanan</span><span class="sxs-lookup"><span data-stu-id="75ad7-178">Who should use this guide</span></span>

<span data-ttu-id="75ad7-179">Geliştiriciler ve Docker tabanlı uygulama geliştirmeyi ve mikro hizmet tabanlı mimari için yeni olan çözüm mimarları için bu kılavuzu yazdığımız.</span><span class="sxs-lookup"><span data-stu-id="75ad7-179">We wrote this guide for developers and solution architects who are new to Docker-based application development and to microservices-based architecture.</span></span> <span data-ttu-id="75ad7-180">Mimari hakkında bilgi edinmek isterseniz tasarlamanıza ve kavram kanıtı uygulamalarını (.NET Core odaklanmaktadır ile) Microsoft geliştirme teknolojileri ile uygulamak için bu kılavuzda sunulmaktadır ve Docker kapsayıcıları ile.</span><span class="sxs-lookup"><span data-stu-id="75ad7-180">This guide is for you if you want to learn how to architect, design, and implement proof-of-concept applications with Microsoft development technologies (with special focus on .NET Core) and with Docker containers.</span></span>

<span data-ttu-id="75ad7-181">Ayrıca bu kılavuzun yararlı bir mimari isteyen bir kuruluş Mimarı'gibi bir teknik karar mercii olan ve teknoloji genel bakış, önce karar verirseniz dağıtılmış uygulamalar yeni ve modern seçmek için hangi yaklaşımı hakkında bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="75ad7-181">You will also find this guide useful if you are a technical decision maker, such as an enterprise architect, who wants an architecture and technology overview before you decide on what approach to select for new and modern distributed applications.</span></span>

### <a name="how-to-use-this-guide"></a><span data-ttu-id="75ad7-182">Bu kılavuz nasıl kullanılır?</span><span class="sxs-lookup"><span data-stu-id="75ad7-182">How to use this guide</span></span>

<span data-ttu-id="75ad7-183">Bu kılavuzun ilk bölümü Docker kapsayıcıları sunar, .NET Core ve geliştirme framework .NET Framework arasında seçim anlatılmaktadır ve mikro hizmetler için genel bir bakış sağlar.</span><span class="sxs-lookup"><span data-stu-id="75ad7-183">The first part of this guide introduces Docker containers, discusses how to choose between .NET Core and the .NET Framework as a development framework, and provides an overview of microservices.</span></span> <span data-ttu-id="75ad7-184">Bu içerik mimarları ve kimlerin kod uygulaması ayrıntılara odaklanmak gerekmez ancak isteyen bir Genel Bakış Teknik karar verenler içindir.</span><span class="sxs-lookup"><span data-stu-id="75ad7-184">This content is for architects and technical decision makers who want an overview but who do not need to focus on code implementation details.</span></span>

<span data-ttu-id="75ad7-185">İle başlayan Kılavuzu ikinci bölümü [geliştirme süreci için Docker tabanlı uygulamalar](#ch_dev_process_for_docker_based_apps) bölümü.</span><span class="sxs-lookup"><span data-stu-id="75ad7-185">The second part of the guide starts with the [Development process for Docker based applications](#ch_dev_process_for_docker_based_apps) section.</span></span> <span data-ttu-id="75ad7-186">.NET Core ve Docker kullanan uygulamalar, uygulama geliştirme ve mikro hizmet desenleri odaklanır.</span><span class="sxs-lookup"><span data-stu-id="75ad7-186">It focuses on development and microservice patterns for implementing applications using .NET Core and Docker.</span></span> <span data-ttu-id="75ad7-187">Bu bölümde, geliştiricilere ve mimarlara desenleri ve uygulama ayrıntılarını ve kod üzerinde odaklanmak isteyen çoğu ilgi olacaktır.</span><span class="sxs-lookup"><span data-stu-id="75ad7-187">This section will be of most interest to developers and architects who want to focus on code and on patterns and implementation details.</span></span>

## <a name="related-microservice-and-container-based-reference-application-eshoponcontainers"></a><span data-ttu-id="75ad7-188">Mikro hizmet ve kapsayıcı tabanlı başvuru uygulaması ilgili: hizmetine</span><span class="sxs-lookup"><span data-stu-id="75ad7-188">Related microservice and container-based reference application: eShopOnContainers</span></span>

<span data-ttu-id="75ad7-189">.NET Core ve Docker kapsayıcılarını kullanarak dağıtılması için tasarlanmış bir mikro hizmetler için bir başvuru uygulaması hizmetine uygulamasıdır.</span><span class="sxs-lookup"><span data-stu-id="75ad7-189">The eShopOnContainers application is a reference app for .NET Core and microservices that is designed to be deployed using Docker containers.</span></span> <span data-ttu-id="75ad7-190">Uygulama birden çok e-store UI ön uçlar (bir Web uygulaması ve yerel bir mobil uygulama) dahil olmak üzere birden çok alt oluşur.</span><span class="sxs-lookup"><span data-stu-id="75ad7-190">The application consists of multiple subsystems, including several e-store UI front ends (a Web app and a native mobile app).</span></span> <span data-ttu-id="75ad7-191">Ayrıca arka uç mikro hizmetler ve kapsayıcılar için gerekli tüm sunucu tarafı işlemleri içerir.</span><span class="sxs-lookup"><span data-stu-id="75ad7-191">It also includes the back-end microservices and containers for all required server-side operations.</span></span>

<span data-ttu-id="75ad7-192">Bu mikro hizmet ve kapsayıcı tabanlı uygulama kaynak kodu, açık kaynak ve [hizmetine](https://aka.ms/MicroservicesArchitecture) GitHub deposu.</span><span class="sxs-lookup"><span data-stu-id="75ad7-192">This microservice and container-based application source code is open source and available at the [eShopOnContainers](https://aka.ms/MicroservicesArchitecture) GitHub repo.</span></span>

## <a name="send-us-your-feedback"></a><span data-ttu-id="75ad7-193">Bize geri bildirim gönderin!</span><span class="sxs-lookup"><span data-stu-id="75ad7-193">Send us your feedback!</span></span>

<span data-ttu-id="75ad7-194">Kapsayıcılı uygulamaları ve .NET içinde mikro hizmetler mimarisi anlamanıza yardımcı olması için bu kılavuzu yazdığımız.</span><span class="sxs-lookup"><span data-stu-id="75ad7-194">We wrote this guide to help you understand the architecture of containerized applications and microservices in .NET.</span></span> <span data-ttu-id="75ad7-195">Bildirimleriniz bizim için değerli şekilde Kılavuzu ve ilgili başvuru uygulaması, gelişen!</span><span class="sxs-lookup"><span data-stu-id="75ad7-195">The guide and related reference application will be evolving, so we welcome your feedback!</span></span> <span data-ttu-id="75ad7-196">Bu kılavuz nasıl geliştirilebilir hakkında açıklamalar varsa, Lütfen bunları gönderin:</span><span class="sxs-lookup"><span data-stu-id="75ad7-196">If you have comments about how this guide can be improved, please send them to:</span></span>

[dotnet-architecture-ebooks-feedback@service.microsoft.com](mailto:dotnet-architecture-ebooks-feedback@service.microsoft.com)

>[!div class="step-by-step"]
[<span data-ttu-id="75ad7-197">Next</span><span class="sxs-lookup"><span data-stu-id="75ad7-197">Next</span></span>](container-docker-introduction/index.md)
