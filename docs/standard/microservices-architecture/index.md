---
title: ".NET mikro. Kapsayıcılı .NET uygulamaları için mimarisi"
description: "Kapsayıcılı .NET uygulamaları için .NET mikro mimarisi | Ön konular"
keywords: "Docker, mikro, ASP.NET, kapsayıcı"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: f869656be4c211c9b028f8ac574eb3bf2de139e2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
![](./media/cover.png)

# <a name="net-microservices-architecture-for-containerized-net-applications"></a><span data-ttu-id="bd98c-105">.NET mikro.</span><span class="sxs-lookup"><span data-stu-id="bd98c-105">.NET Microservices.</span></span> <span data-ttu-id="bd98c-106">Kapsayıcılı .NET uygulamaları için mimarisi</span><span class="sxs-lookup"><span data-stu-id="bd98c-106">Architecture for Containerized .NET Applications</span></span>

<span data-ttu-id="bd98c-107">İNDİRME bulunabilir: <https://aka.ms/microservicesebook></span><span class="sxs-lookup"><span data-stu-id="bd98c-107">DOWNLOAD available at: <https://aka.ms/microservicesebook></span></span>

<span data-ttu-id="bd98c-108">TARAFINDAN YAYIMLANAN</span><span class="sxs-lookup"><span data-stu-id="bd98c-108">PUBLISHED BY</span></span>

<span data-ttu-id="bd98c-109">Microsoft Developer bölme, .NET ve Visual Studio ürün ekipleriyle</span><span class="sxs-lookup"><span data-stu-id="bd98c-109">Microsoft Developer Division, .NET and Visual Studio product teams</span></span>

<span data-ttu-id="bd98c-110">Microsoft Corporation'ın bölme</span><span class="sxs-lookup"><span data-stu-id="bd98c-110">A division of Microsoft Corporation</span></span>

<span data-ttu-id="bd98c-111">One Microsoft Way</span><span class="sxs-lookup"><span data-stu-id="bd98c-111">One Microsoft Way</span></span>

<span data-ttu-id="bd98c-112">Redmond, Washington 98052-6399</span><span class="sxs-lookup"><span data-stu-id="bd98c-112">Redmond, Washington 98052-6399</span></span>

<span data-ttu-id="bd98c-113">Telif Hakkı © Microsoft Corporation'ın 2017</span><span class="sxs-lookup"><span data-stu-id="bd98c-113">Copyright © 2017 by Microsoft Corporation</span></span>

<span data-ttu-id="bd98c-114">Tüm hakları saklıdır.</span><span class="sxs-lookup"><span data-stu-id="bd98c-114">All rights reserved.</span></span> <span data-ttu-id="bd98c-115">Bu kitap içeriğini hiçbir bölümü çoğaltılamaz veya herhangi bir biçimde veya publisher'ın yazılı izni olmadan herhangi bir yöntemle aktarılamaz.</span><span class="sxs-lookup"><span data-stu-id="bd98c-115">No part of the contents of this book may be reproduced or transmitted in any form or by any means without the written permission of the publisher.</span></span>

<span data-ttu-id="bd98c-116">Bu kitap sağlanan "olarak-olan" ve yazar görünümler ve görüşlerini ifade eder.</span><span class="sxs-lookup"><span data-stu-id="bd98c-116">This book is provided “as-is” and expresses the author’s views and opinions.</span></span> <span data-ttu-id="bd98c-117">Görünümler, görüşlerini ve URL ve diğer Internet Web sitesi başvuruları dahil olmak üzere bu Defteri'nde ifade bilgileri bildirilmeksizin değiştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="bd98c-117">The views, opinions and information expressed in this book, including URL and other Internet website references, may change without notice.</span></span>

<span data-ttu-id="bd98c-118">Burada açıklanan bazı örnekler yalnızca çizim için sağlanmıştır ve kurgusaldır.</span><span class="sxs-lookup"><span data-stu-id="bd98c-118">Some examples depicted herein are provided for illustration only and are fictitious.</span></span> <span data-ttu-id="bd98c-119">Gerçek bir ilişki veya bağlantı amaçlanmamıştır veya çıkarılmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="bd98c-119">No real association or connection is intended or should be inferred.</span></span>

<span data-ttu-id="bd98c-120">Microsoft ve http://www.microsoft.com "Ticari" Web sayfasında listelenen ticari Microsoft şirketler grubunun ticari markalarıdır.</span><span class="sxs-lookup"><span data-stu-id="bd98c-120">Microsoft and the trademarks listed at http://www.microsoft.com on the “Trademarks” webpage are trademarks of the Microsoft group of companies.</span></span>

<span data-ttu-id="bd98c-121">Mac ve macOS Apple Inc.'in ticari markalarıdır.</span><span class="sxs-lookup"><span data-stu-id="bd98c-121">Mac and macOS are trademarks of Apple Inc.</span></span>

<span data-ttu-id="bd98c-122">Docker whale logosu, Docker, Inc.'in kayıtlı ticari markasıdır İzni tarafından kullanılır.</span><span class="sxs-lookup"><span data-stu-id="bd98c-122">The Docker whale logo is a registered trademark of Docker, Inc. Used by permission.</span></span>

<span data-ttu-id="bd98c-123">Diğer tüm işaretler ve logo markalar, ilgili sahiplerinin mülkiyetindedir.</span><span class="sxs-lookup"><span data-stu-id="bd98c-123">All other marks and logos are property of their respective owners.</span></span>

<span data-ttu-id="bd98c-124">Ortak yazarlar:</span><span class="sxs-lookup"><span data-stu-id="bd98c-124">Co-Authors:</span></span>

> <span data-ttu-id="bd98c-125">**Cesar de la Torre**, Sr. PM .NET ürün ekibi, Microsoft Corp.</span><span class="sxs-lookup"><span data-stu-id="bd98c-125">**Cesar de la Torre**, Sr. PM, .NET product team, Microsoft Corp.</span></span>
>
> <span data-ttu-id="bd98c-126">**Fatura Wagner**, Sr. Geliştirici, C + E, Microsoft Corp. içerik</span><span class="sxs-lookup"><span data-stu-id="bd98c-126">**Bill Wagner**, Sr. Content Developer, C+E, Microsoft Corp.</span></span>
>
> <span data-ttu-id="bd98c-127">**Can Rousos**, asıl yazılım mühendisi, DevDiv CAT ekibi, Microsoft</span><span class="sxs-lookup"><span data-stu-id="bd98c-127">**Mike Rousos**, Principal Software Engineer, DevDiv CAT team, Microsoft</span></span>

<span data-ttu-id="bd98c-128">Düzenleyiciler:</span><span class="sxs-lookup"><span data-stu-id="bd98c-128">Editors:</span></span>

> <span data-ttu-id="bd98c-129">**Can Pope**</span><span class="sxs-lookup"><span data-stu-id="bd98c-129">**Mike Pope**</span></span>
>
> <span data-ttu-id="bd98c-130">**Steve Hoag**</span><span class="sxs-lookup"><span data-stu-id="bd98c-130">**Steve Hoag**</span></span>

<span data-ttu-id="bd98c-131">Katılımcıların ve gözden geçirenler:</span><span class="sxs-lookup"><span data-stu-id="bd98c-131">Participants and reviewers:</span></span>

> <span data-ttu-id="bd98c-132">**Gamze Ritcher**, iş ortağı yazılım Eng, Azure ekibi, Microsoft</span><span class="sxs-lookup"><span data-stu-id="bd98c-132">**Jeffrey Ritcher**, Partner Software Eng, Azure team, Microsoft</span></span>
>
> <span data-ttu-id="bd98c-133">**Jimmy Bogard**, Headspring adresindeki Baş Mimarı</span><span class="sxs-lookup"><span data-stu-id="bd98c-133">**Jimmy Bogard**, Chief Architect at Headspring</span></span>
>
> <span data-ttu-id="bd98c-134">**UDI Dahan**, kurucusu & CEO, belirli yazılım</span><span class="sxs-lookup"><span data-stu-id="bd98c-134">**Udi Dahan**, Founder & CEO, Particular Software</span></span>
>
> <span data-ttu-id="bd98c-135">**Jimmy Nilsson**, ortak kurucusu ve Factor10 CEO</span><span class="sxs-lookup"><span data-stu-id="bd98c-135">**Jimmy Nilsson**, Co-founder and CEO of Factor10</span></span>
>
> <span data-ttu-id="bd98c-136">**Glenn Condron**, Sr. Program Yöneticisi, ASP.NET ekibi</span><span class="sxs-lookup"><span data-stu-id="bd98c-136">**Glenn Condron**, Sr. Program Manager, ASP.NET team</span></span>
>
> <span data-ttu-id="bd98c-137">**İşareti Fussell**, asıl PM sağlama, Microsoft Azure Service Fabric ekibi</span><span class="sxs-lookup"><span data-stu-id="bd98c-137">**Mark Fussell**, Principal PM Lead, Azure Service Fabric team, Microsoft</span></span>
>
> <span data-ttu-id="bd98c-138">**Diego Vega**, PM sağlama, Entity Framework takım, Microsoft</span><span class="sxs-lookup"><span data-stu-id="bd98c-138">**Diego Vega**, PM Lead, Entity Framework team, Microsoft</span></span>
>
> <span data-ttu-id="bd98c-139">**Hakan Dorrans**, Sr. Güvenlik Program Yöneticisi</span><span class="sxs-lookup"><span data-stu-id="bd98c-139">**Barry Dorrans**, Sr. Security Program Manager</span></span>
>
> <span data-ttu-id="bd98c-140">**Rowan Mert**, Sr. Program Yöneticisi, Microsoft</span><span class="sxs-lookup"><span data-stu-id="bd98c-140">**Rowan Miller**, Sr. Program Manager, Microsoft</span></span>
>
> <span data-ttu-id="bd98c-141">**Ankit Asthana**, asıl PM Yöneticisi, .NET ekibi, Microsoft</span><span class="sxs-lookup"><span data-stu-id="bd98c-141">**Ankit Asthana**, Principal PM Manager, .NET team, Microsoft</span></span>
>
> <span data-ttu-id="bd98c-142">**Tan Hunter**, .NET ekibi, Microsoft iş ortağı Director PM</span><span class="sxs-lookup"><span data-stu-id="bd98c-142">**Scott Hunter**, Partner Director PM, .NET team, Microsoft</span></span>
>
> <span data-ttu-id="bd98c-143">**Dylan Reisenberger**, mimarı ve Polly adresindeki Geliştirici sağlama</span><span class="sxs-lookup"><span data-stu-id="bd98c-143">**Dylan Reisenberger**, Architect and Dev Lead at Polly</span></span>
>
> <span data-ttu-id="bd98c-144">**Steve Smith**, yazılım Craftsman & ASPSmith Ltd. şirketindeki Eğitmen</span><span class="sxs-lookup"><span data-stu-id="bd98c-144">**Steve Smith**, Software Craftsman & Trainer at ASPSmith Ltd.</span></span>
>
> <span data-ttu-id="bd98c-145">**Yen Cooper**, kodlama mimari adresindeki parlak</span><span class="sxs-lookup"><span data-stu-id="bd98c-145">**Ian Cooper**, Coding Architect at Brighter</span></span>
>
> <span data-ttu-id="bd98c-146">**Unai Zorrilla**, mimarı ve düz kavramları adresindeki Geliştirici sağlama</span><span class="sxs-lookup"><span data-stu-id="bd98c-146">**Unai Zorrilla**, Architect and Dev Lead at Plain Concepts</span></span>
>
> <span data-ttu-id="bd98c-147">**Eduard Tomas**, düz kavramları adresindeki Geliştirici sağlama</span><span class="sxs-lookup"><span data-stu-id="bd98c-147">**Eduard Tomas**, Dev Lead at Plain Concepts</span></span>
>
> <span data-ttu-id="bd98c-148">**Ramon Tomas**, düz kavramları adresindeki Geliştirici</span><span class="sxs-lookup"><span data-stu-id="bd98c-148">**Ramon Tomas**, Developer at Plain Concepts</span></span>
>
> <span data-ttu-id="bd98c-149">**David Sanz**, düz kavramları adresindeki Geliştirici</span><span class="sxs-lookup"><span data-stu-id="bd98c-149">**David Sanz**, Developer at Plain Concepts</span></span>
>
> <span data-ttu-id="bd98c-150">**Javier Valero**, baş Müdürü Grupo çözümleri adresindeki işletim</span><span class="sxs-lookup"><span data-stu-id="bd98c-150">**Javier Valero**, Chief Operating Officer at Grupo Solutio</span></span>
>
> <span data-ttu-id="bd98c-151">**Pierre Millet**, Sr. Danışman, Microsoft</span><span class="sxs-lookup"><span data-stu-id="bd98c-151">**Pierre Millet**, Sr. Consultant, Microsoft</span></span>
>
> <span data-ttu-id="bd98c-152">**Michael Friis**, ürün Yöneticisi, Docker Inc</span><span class="sxs-lookup"><span data-stu-id="bd98c-152">**Michael Friis**, Product Manager, Docker Inc</span></span>
>
> <span data-ttu-id="bd98c-153">**Charles Lowell**, yazılım mühendisi, VS CAT ekibi, Microsoft</span><span class="sxs-lookup"><span data-stu-id="bd98c-153">**Charles Lowell**, Software Engineer, VS CAT team, Microsoft</span></span>

## <a name="introduction"></a><span data-ttu-id="bd98c-154">Giriş</span><span class="sxs-lookup"><span data-stu-id="bd98c-154">Introduction</span></span>

<span data-ttu-id="bd98c-155">Giderek kuruluşların maliyet tasarrufu kullanıldıklarını, dağıtım sorunlarını çözmek ve kapsayıcılar kullanarak DevOps ve üretim işlemlerini artırma.</span><span class="sxs-lookup"><span data-stu-id="bd98c-155">Enterprises are increasingly realizing cost savings, solving deployment problems, and improving DevOps and production operations by using containers.</span></span> <span data-ttu-id="bd98c-156">Microsoft Windows ve Linux için kapsayıcı yenilikleri Azure kapsayıcı hizmeti ve Azure Service Fabric gibi ürün oluşturma ve Docker, Mesosphere ve Kubernetes gibi endüstri kılavuzları ile ortaklık serbest.</span><span class="sxs-lookup"><span data-stu-id="bd98c-156">Microsoft has been releasing container innovations for Windows and Linux by creating products like Azure Container Service and Azure Service Fabric, and by partnering with industry leaders like Docker, Mesosphere, and Kubernetes.</span></span> <span data-ttu-id="bd98c-157">Bu ürünler bulut hızı ve ölçek, hangi uygulamalar oluşturma ve dağıtma şirketlerin yardımcı kapsayıcı çözümleri teslim kendi seçtikleri platform veya Araçlar.</span><span class="sxs-lookup"><span data-stu-id="bd98c-157">These products deliver container solutions that help companies build and deploy applications at cloud speed and scale, whatever their choice of platform or tools.</span></span>

<span data-ttu-id="bd98c-158">Docker gerçek Windows ve Linux ekosistemlerini en önemli satıcılar tarafından desteklenen kapsayıcı endüstri standardında durumundadır.</span><span class="sxs-lookup"><span data-stu-id="bd98c-158">Docker is becoming the de facto standard in the container industry, supported by the most significant vendors in the Windows and Linux ecosystems.</span></span> <span data-ttu-id="bd98c-159">(Microsoft Docker destekleyen ana bulut satıcılar biridir.) Gelecekte, Docker büyük olasılıkla bulutta veya şirket içi herhangi bir veri merkezinde bulunabilen olacaktır.</span><span class="sxs-lookup"><span data-stu-id="bd98c-159">(Microsoft is one of the main cloud vendors supporting Docker.) In the future, Docker will probably be ubiquitous in any datacenter in the cloud or on-premises.</span></span>

<span data-ttu-id="bd98c-160">Ayrıca, [mikro](https://martinfowler.com/articles/microservices.html) mimarisi gelişen dağıtılmış görev açısından kritik uygulamalar için önemli bir yaklaşım olarak.</span><span class="sxs-lookup"><span data-stu-id="bd98c-160">In addition, the [microservices](https://martinfowler.com/articles/microservices.html) architecture is emerging as an important approach for distributed mission-critical applications.</span></span> <span data-ttu-id="bd98c-161">Mikro hizmet tabanlı bir mimari, uygulama, test edilmiş, dağıtılan ve sürümü tutulan bağımsız olarak geliştirilebilir hizmetler koleksiyonu üzerinde oluşturulmuştur.</span><span class="sxs-lookup"><span data-stu-id="bd98c-161">In a microservice-based architecture, the application is built on a collection of services that can be developed, tested, deployed, and versioned independently.</span></span>

## <a name="about-this-guide"></a><span data-ttu-id="bd98c-162">Bu kılavuz hakkında</span><span class="sxs-lookup"><span data-stu-id="bd98c-162">About this guide</span></span>

<span data-ttu-id="bd98c-163">Bu kılavuz mikro tabanlı uygulamaları geliştirmek ve bunları yönetmek için bir giriş olduğunu kapsayıcıları kullanma.</span><span class="sxs-lookup"><span data-stu-id="bd98c-163">This guide is an introduction to developing microservices-based applications and managing them using containers.</span></span> <span data-ttu-id="bd98c-164">Mimari Tasarım açıklanır ve .NET Core ve Docker kapsayıcıları kullanma uygulaması yaklaşıyor.</span><span class="sxs-lookup"><span data-stu-id="bd98c-164">It discusses architectural design and implementation approaches using .NET Core and Docker containers.</span></span> <span data-ttu-id="bd98c-165">Kapsayıcılar ve mikro kullanmaya başlama kolaylaştırmak için bir kapsayıcılı başvurusu ve keşfedebilirsiniz mikro hizmet tabanlı bir Uygulama Kılavuzu odaklanır.</span><span class="sxs-lookup"><span data-stu-id="bd98c-165">To make it easier to get started with containers and microservices, the guide focuses on a reference containerized and microservice-based application that you can explore.</span></span> <span data-ttu-id="bd98c-166">Örnek uygulama kullanılabilir [eShopOnContainers](https://github.com/dotnet-architecture/eShopOnContainers) GitHub depo.</span><span class="sxs-lookup"><span data-stu-id="bd98c-166">The sample application is available at the [eShopOnContainers](https://github.com/dotnet-architecture/eShopOnContainers) GitHub repo.</span></span>

<span data-ttu-id="bd98c-167">Bu kılavuz temel geliştirme ve Mimari Kılavuzu birincil olarak geliştirme ortamı düzeyde iki teknolojiyi odaklanmak sağlar: Docker ve .NET Core.</span><span class="sxs-lookup"><span data-stu-id="bd98c-167">This guide provides foundational development and architectural guidance primarily at a development environment level with a focus on two technologies: Docker and .NET Core.</span></span> <span data-ttu-id="bd98c-168">Bizim amaç, yapı üretim ortamınızın (Bulut veya şirket içi) odaklanan olmadan uygulama tasarımı hakkında düşünürken, bu kılavuzu okumadan ' dir.</span><span class="sxs-lookup"><span data-stu-id="bd98c-168">Our intention is that you read this guide when thinking about your application design without focusing on the infrastructure (cloud or on-premises) of your production environment.</span></span> <span data-ttu-id="bd98c-169">Üretime hazır uygulamalarınızı oluşturduğunuzda altyapınızı hakkında kararlar daha sonra hale getirir.</span><span class="sxs-lookup"><span data-stu-id="bd98c-169">You will make decisions about your infrastructure later, when you create your production-ready applications.</span></span> <span data-ttu-id="bd98c-170">Bu nedenle, bu kılavuz, altyapı belirsiz ve daha fazla geliştirme ortamı-merkezli olması amaçlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="bd98c-170">Therefore, this guide is intended to be infrastructure agnostic and more development-environment-centric.</span></span>

<span data-ttu-id="bd98c-171">Bu kılavuz eğitim sonra sonraki adımınız üretime hazır mikro Microsoft Azure üzerinde hakkında bilgi edinmek için olacaktır.</span><span class="sxs-lookup"><span data-stu-id="bd98c-171">After you have studied this guide, your next step would be to learn about production-ready microservices on Microsoft Azure.</span></span>

## <a name="what-this-guide-does-not-cover"></a><span data-ttu-id="bd98c-172">Ne bu kılavuzda ele alınmamaktadır</span><span class="sxs-lookup"><span data-stu-id="bd98c-172">What this guide does not cover</span></span>

<span data-ttu-id="bd98c-173">Bu kılavuz uygulama yaşam döngüsü DevOps, CI/CD ardışık odaklanan değil veya ekibi çalışın.</span><span class="sxs-lookup"><span data-stu-id="bd98c-173">This guide does not focus on the application lifecycle, DevOps, CI/CD pipelines, or team work.</span></span> <span data-ttu-id="bd98c-174">Tamamlayıcı Kılavuzu [Microsoft Platformu ve araçları ile kapsayıcılı Docker uygulama yaşam döngüsü](https://aka.ms/dockerlifecycleebook) bu konuda odaklanır.</span><span class="sxs-lookup"><span data-stu-id="bd98c-174">The complementary guide [Containerized Docker Application Lifecycle with Microsoft Platform and Tools](https://aka.ms/dockerlifecycleebook) focuses on that subject.</span></span> <span data-ttu-id="bd98c-175">Geçerli Kılavuz ayrıca uygulama ayrıntılarını belirli orchestrators hakkında bilgi gibi Azure altyapı sağlamaz.</span><span class="sxs-lookup"><span data-stu-id="bd98c-175">The current guide also does not provide implementation details on Azure infrastructure, such as information on specific orchestrators.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="bd98c-176">Ek kaynaklar</span><span class="sxs-lookup"><span data-stu-id="bd98c-176">Additional resources</span></span>

-   <span data-ttu-id="bd98c-177">**Microsoft Platformu ve araçları ile Docker uygulama yaşam döngüsü kapsayıcılı** (indirilebilir e-kitap) [ *https://aka.ms/dockerlifecycleebook*](https://aka.ms/dockerlifecycleebook)</span><span class="sxs-lookup"><span data-stu-id="bd98c-177">**Containerized Docker Application Lifecycle with Microsoft Platform and Tools** (downloadable e-book) [*https://aka.ms/dockerlifecycleebook*](https://aka.ms/dockerlifecycleebook)</span></span>

## <a name="who-should-use-this-guide"></a><span data-ttu-id="bd98c-178">Bu kılavuz kullanan</span><span class="sxs-lookup"><span data-stu-id="bd98c-178">Who should use this guide</span></span>

<span data-ttu-id="bd98c-179">Geliştiriciler ve Docker tabanlı uygulama geliştirme ve mikro tabanlı mimari yeni çözüm mimarları için bu kılavuzu yazıldı.</span><span class="sxs-lookup"><span data-stu-id="bd98c-179">We wrote this guide for developers and solution architects who are new to Docker-based application development and to microservices-based architecture.</span></span> <span data-ttu-id="bd98c-180">Bu kılavuz, mimari, öğrenmek istiyorsanız, tasarlayıp (odaklanılan özel .NET Core üzerinde) Microsoft geliştirme teknolojileriyle kavram kanıtı uygulamaları için olan ve Docker kapsayıcılarla.</span><span class="sxs-lookup"><span data-stu-id="bd98c-180">This guide is for you if you want to learn how to architect, design, and implement proof-of-concept applications with Microsoft development technologies (with special focus on .NET Core) and with Docker containers.</span></span>

<span data-ttu-id="bd98c-181">Da bu kılavuzda yararlı bir mimari isteyen bir kuruluş Mimarı gibi bir teknik karar veren olan ve teknoloji genel bakış, önce karar verirseniz dağıtılmış uygulamalar yeni ve modern seçmek için hangi yaklaşımın üzerinde bulacaksınız.</span><span class="sxs-lookup"><span data-stu-id="bd98c-181">You will also find this guide useful if you are a technical decision maker, such as an enterprise architect, who wants an architecture and technology overview before you decide on what approach to select for new and modern distributed applications.</span></span>

### <a name="how-to-use-this-guide"></a><span data-ttu-id="bd98c-182">Bu kılavuz kullanma</span><span class="sxs-lookup"><span data-stu-id="bd98c-182">How to use this guide</span></span>

<span data-ttu-id="bd98c-183">Bu kılavuzun ilk bölümü Docker kapsayıcıları tanıtır, .NET Core ve .NET Framework geliştirme framework olarak arasında seçim yapma açıklanır ve mikro genel bir bakış sağlar.</span><span class="sxs-lookup"><span data-stu-id="bd98c-183">The first part of this guide introduces Docker containers, discusses how to choose between .NET Core and the .NET Framework as a development framework, and provides an overview of microservices.</span></span> <span data-ttu-id="bd98c-184">Bu içerik mimarları ve genel bir bakış isteyen ancak kimin kod uygulama ayrıntılara odaklanmak gerekmez teknik karar alıcılar içindir.</span><span class="sxs-lookup"><span data-stu-id="bd98c-184">This content is for architects and technical decision makers who want an overview but who do not need to focus on code implementation details.</span></span>

<span data-ttu-id="bd98c-185">Kılavuzu ikinci bölümü ile başlayan [geliştirme işlemi için Docker tabanlı uygulamalar](#ch_dev_process_for_docker_based_apps) bölümü.</span><span class="sxs-lookup"><span data-stu-id="bd98c-185">The second part of the guide starts with the [Development process for Docker based applications](#ch_dev_process_for_docker_based_apps) section.</span></span> <span data-ttu-id="bd98c-186">.NET Core ve Docker kullanan uygulamalar uygulama geliştirme ve mikro hizmet desenleri odaklanır.</span><span class="sxs-lookup"><span data-stu-id="bd98c-186">It focuses on development and microservice patterns for implementing applications using .NET Core and Docker.</span></span> <span data-ttu-id="bd98c-187">Bu bölümde, geliştiriciler ve odak kodu ve modelleri ve uygulama ayrıntılarını istediğiniz mimarları için en ilgi olacaktır.</span><span class="sxs-lookup"><span data-stu-id="bd98c-187">This section will be of most interest to developers and architects who want to focus on code and on patterns and implementation details.</span></span>

## <a name="related-microservice-and-container-based-reference-application-eshoponcontainers"></a><span data-ttu-id="bd98c-188">İlgili mikro hizmet ve kapsayıcı tabanlı başvuru uygulaması: eShopOnContainers</span><span class="sxs-lookup"><span data-stu-id="bd98c-188">Related microservice and container-based reference application: eShopOnContainers</span></span>

<span data-ttu-id="bd98c-189">.NET Core ve Docker kapsayıcıları kullanma dağıtılması için tasarlanmış mikro hizmetler için bir başvuru uygulaması eShopOnContainers uygulamasıdır.</span><span class="sxs-lookup"><span data-stu-id="bd98c-189">The eShopOnContainers application is a reference app for .NET Core and microservices that is designed to be deployed using Docker containers.</span></span> <span data-ttu-id="bd98c-190">Uygulama birkaç e deposu UI ön uçlar (bir Web uygulaması ve yerel bir mobil uygulama) dahil olmak üzere birden çok alt oluşur.</span><span class="sxs-lookup"><span data-stu-id="bd98c-190">The application consists of multiple subsystems, including several e-store UI front ends (a Web app and a native mobile app).</span></span> <span data-ttu-id="bd98c-191">Arka uç mikro ve gerekli tüm sunucu tarafı işlemleri için kapsayıcı de içerir.</span><span class="sxs-lookup"><span data-stu-id="bd98c-191">It also includes the back-end microservices and containers for all required server-side operations.</span></span>

<span data-ttu-id="bd98c-192">Bu mikro hizmet ve kapsayıcı tabanlı uygulama kaynak kodudur açık kaynaklı ve adresinde [eShopOnContainers](http://aka.ms/MicroservicesArchitecture) GitHub depo.</span><span class="sxs-lookup"><span data-stu-id="bd98c-192">This microservice and container-based application source code is open source and available at the [eShopOnContainers](http://aka.ms/MicroservicesArchitecture) GitHub repo.</span></span>

## <a name="send-us-your-feedback"></a><span data-ttu-id="bd98c-193">Bize Geri bildiriminizi gönderin!</span><span class="sxs-lookup"><span data-stu-id="bd98c-193">Send us your feedback!</span></span>

<span data-ttu-id="bd98c-194">Kapsayıcılı uygulamaları ve .NET mikro mimarisini anlamanıza yardımcı olması için bu kılavuzu yazdığımız.</span><span class="sxs-lookup"><span data-stu-id="bd98c-194">We wrote this guide to help you understand the architecture of containerized applications and microservices in .NET.</span></span> <span data-ttu-id="bd98c-195">Bildiriminiz bizim için kılavuz ve ilgili başvuru uygulaması, Gelişmekte olan!</span><span class="sxs-lookup"><span data-stu-id="bd98c-195">The guide and related reference application will be evolving, so we welcome your feedback!</span></span> <span data-ttu-id="bd98c-196">Bu kılavuz nasıl geliştirilebilir hakkında yorumlar varsa, lütfen gönderebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="bd98c-196">If you have comments about how this guide can be improved, please send them to:</span></span>

[dotnet-architecture-ebooks-feedback@service.microsoft.com](mailto:dotnet-architecture-ebooks-feedback@service.microsoft.com)

>[!div class="step-by-step"]
<span data-ttu-id="bd98c-197">[Sonraki] (kapsayıcı-docker-giriş/index.md)</span><span class="sxs-lookup"><span data-stu-id="bd98c-197">[Next] (container-docker-introduction/index.md)</span></span>
