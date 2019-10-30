---
title: .NET mikro hizmetleri. Kapsayıcılı .NET Uygulamaları Mimarisi
description: Kapsayıcılı .NET uygulamaları için .NET mikro hizmetleri mimarisi | Mikro hizmetler modüler ve bağımsız olarak dağıtılabilir hizmetlerdir. Docker Kapsayıcıları (Linux ve Windows için), bir hizmet ve bağımlılıklarını tek bir birim halinde paketleyerek dağıtım ve test etmeyi basitleştirir. Bu, daha sonra yalıtılmış bir ortamda çalıştırılır.
ms.date: 01/07/2019
ms.openlocfilehash: 7fa4935fe56ca873a5311812637964083e34170e
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73089906"
---
# <a name="net-microservices-architecture-for-containerized-net-applications"></a><span data-ttu-id="132ca-105">.NET mikro hizmetleri: Kapsayıcılı .NET uygulamaları için mimari</span><span class="sxs-lookup"><span data-stu-id="132ca-105">.NET Microservices: Architecture for Containerized .NET Applications</span></span>

![Kitap kapağı](./media/cover-small.png)

<span data-ttu-id="132ca-107">**Sürüm v 2.2** -ASP.NET Core 2,2 ' ye güncelleştirildi</span><span class="sxs-lookup"><span data-stu-id="132ca-107">**EDITION v2.2** - Updated to ASP.NET Core 2.2</span></span>

<span data-ttu-id="132ca-108">Bu kılavuz, mikro hizmet tabanlı uygulamalar geliştirmeye ve kapsayıcıları kullanarak bunları yönetmeye yönelik bir giriş niteliğindedir.</span><span class="sxs-lookup"><span data-stu-id="132ca-108">This guide is an introduction to developing microservices-based applications and managing them using containers.</span></span> <span data-ttu-id="132ca-109">.NET Core ve Docker Kapsayıcıları kullanılarak mimari tasarımı ve uygulama yaklaşımlarını ele alır.</span><span class="sxs-lookup"><span data-stu-id="132ca-109">It discusses architectural design and implementation approaches using .NET Core and Docker containers.</span></span>

<span data-ttu-id="132ca-110">Daha kolay çalışmaya başlamak için kılavuz, keşfedebileceğiniz bir başvuru Kapsayıcılı ve mikro hizmet tabanlı uygulamaya odaklanır.</span><span class="sxs-lookup"><span data-stu-id="132ca-110">To make it easier to get started, the guide focuses on a reference containerized and microservice-based application that you can explore.</span></span> <span data-ttu-id="132ca-111">Başvuru uygulaması [Eshoponcontainers](https://github.com/dotnet-architecture/eShopOnContainers) GitHub deposunda mevcuttur.</span><span class="sxs-lookup"><span data-stu-id="132ca-111">The reference application is available at the [eShopOnContainers](https://github.com/dotnet-architecture/eShopOnContainers) GitHub repo.</span></span>

## <a name="action-links"></a><span data-ttu-id="132ca-112">Eylem bağlantıları</span><span class="sxs-lookup"><span data-stu-id="132ca-112">Action links</span></span>

- <span data-ttu-id="132ca-113">Bu e-kitabı tercih ettiğiniz biçime indirin (Yalnızca Ingilizce sürüm): | [PDF](https://aka.ms/microservicesebook) | [mobi](https://dotnet.microsoft.com/download/thank-you/microservices-architecture-ebook-mobi) | [EPUB](https://dotnet.microsoft.com/download/thank-you/microservices-architecture-ebook-epub) |</span><span class="sxs-lookup"><span data-stu-id="132ca-113">Download this e-book in your format of choice (English version only): | [PDF](https://aka.ms/microservicesebook) | [MOBI](https://dotnet.microsoft.com/download/thank-you/microservices-architecture-ebook-mobi) | [EPUB](https://dotnet.microsoft.com/download/thank-you/microservices-architecture-ebook-epub) |</span></span>

- <span data-ttu-id="132ca-114">[GitHub 'daki başvuru uygulaması Eshoponcontainers 'ı](https://github.com/dotnet-architecture/eShopOnContainers) kopyalama/çatal</span><span class="sxs-lookup"><span data-stu-id="132ca-114">Clone/Fork the reference application [eShopOnContainers on GitHub](https://github.com/dotnet-architecture/eShopOnContainers)</span></span>

- <span data-ttu-id="132ca-115">[Kanal 9 ' da tanıtım videosunu](https://aka.ms/microservices-video) izleyin</span><span class="sxs-lookup"><span data-stu-id="132ca-115">Watch the [introductory video on Channel 9](https://aka.ms/microservices-video)</span></span>

- <span data-ttu-id="132ca-116">[Mikro hizmet mimarisini](https://aka.ms/MicroservicesArchitecture) hemen öğrenin</span><span class="sxs-lookup"><span data-stu-id="132ca-116">Get to know the [Microservices Architecture](https://aka.ms/MicroservicesArchitecture) right away</span></span>

## <a name="introduction"></a><span data-ttu-id="132ca-117">Giriş</span><span class="sxs-lookup"><span data-stu-id="132ca-117">Introduction</span></span>

<span data-ttu-id="132ca-118">Kuruluşlar daha fazla maliyet tasarrufu, dağıtım sorunlarını çözme ve kapsayıcıları kullanarak DevOps ve üretim işlemlerini geliştirme.</span><span class="sxs-lookup"><span data-stu-id="132ca-118">Enterprises are increasingly realizing cost savings, solving deployment problems, and improving DevOps and production operations by using containers.</span></span> <span data-ttu-id="132ca-119">Microsoft, Azure Kubernetes hizmeti ve Azure Service Fabric gibi ürünler oluşturarak ve Docker, Mesosphere ve Kubernetes gibi sektör liderleriyle işbirliği yaparak Windows ve Linux için kapsayıcı yenilikleri yayımlamaktadır.</span><span class="sxs-lookup"><span data-stu-id="132ca-119">Microsoft has been releasing container innovations for Windows and Linux by creating products like Azure Kubernetes Service and Azure Service Fabric, and by partnering with industry leaders like Docker, Mesosphere, and Kubernetes.</span></span> <span data-ttu-id="132ca-120">Bu ürünler, şirketlerin bulut hızında ve ölçekte uygulama oluşturup dağıtmalarına yardımcı olan kapsayıcı çözümleri sunar.</span><span class="sxs-lookup"><span data-stu-id="132ca-120">These products deliver container solutions that help companies build and deploy applications at cloud speed and scale, whatever their choice of platform or tools.</span></span>

<span data-ttu-id="132ca-121">Docker, Windows ve Linux ekosistemlerindeki en önemli satıcılar tarafından desteklenen kapsayıcı sektöründe standart bir standart haline geliyor.</span><span class="sxs-lookup"><span data-stu-id="132ca-121">Docker is becoming the de facto standard in the container industry, supported by the most significant vendors in the Windows and Linux ecosystems.</span></span> <span data-ttu-id="132ca-122">(Microsoft, Docker destekleyen ana bulut satıcılarından biridir.) Gelecekte Docker, büyük olasılıkla buluttaki veya Şirket içindeki herhangi bir veri merkezinde yer alır.</span><span class="sxs-lookup"><span data-stu-id="132ca-122">(Microsoft is one of the main cloud vendors supporting Docker.) In the future, Docker will probably be ubiquitous in any datacenter in the cloud or on-premises.</span></span>

<span data-ttu-id="132ca-123">Ayrıca, [mikro hizmetler](https://martinfowler.com/articles/microservices.html) mimarisi, dağıtılmış görev açısından kritik uygulamalar için önemli bir yaklaşım olarak gelişmekte.</span><span class="sxs-lookup"><span data-stu-id="132ca-123">In addition, the [microservices](https://martinfowler.com/articles/microservices.html) architecture is emerging as an important approach for distributed mission-critical applications.</span></span> <span data-ttu-id="132ca-124">Mikro hizmet tabanlı bir mimaride, uygulama, bağımsız olarak geliştirilen, test edilmiş, dağıtılan ve sürümü tutulan bir hizmetler koleksiyonu üzerine kurulmuştur.</span><span class="sxs-lookup"><span data-stu-id="132ca-124">In a microservice-based architecture, the application is built on a collection of services that can be developed, tested, deployed, and versioned independently.</span></span>

## <a name="about-this-guide"></a><span data-ttu-id="132ca-125">Bu kılavuz hakkında</span><span class="sxs-lookup"><span data-stu-id="132ca-125">About this guide</span></span>

<span data-ttu-id="132ca-126">Bu kılavuz, mikro hizmet tabanlı uygulamalar geliştirmeye ve kapsayıcıları kullanarak bunları yönetmeye yönelik bir giriş niteliğindedir.</span><span class="sxs-lookup"><span data-stu-id="132ca-126">This guide is an introduction to developing microservices-based applications and managing them using containers.</span></span> <span data-ttu-id="132ca-127">.NET Core ve Docker Kapsayıcıları kullanılarak mimari tasarımı ve uygulama yaklaşımlarını ele alır.</span><span class="sxs-lookup"><span data-stu-id="132ca-127">It discusses architectural design and implementation approaches using .NET Core and Docker containers.</span></span> <span data-ttu-id="132ca-128">Kapsayıcılar ve mikro hizmetlerle çalışmaya başlamanızı kolaylaştırmak için, rehber, keşfedebileceğiniz bir başvuru Kapsayıcılı ve mikro hizmet tabanlı uygulamaya odaklanır.</span><span class="sxs-lookup"><span data-stu-id="132ca-128">To make it easier to get started with containers and microservices, the guide focuses on a reference containerized and microservice-based application that you can explore.</span></span> <span data-ttu-id="132ca-129">Örnek uygulama [Eshoponcontainers](https://github.com/dotnet-architecture/eShopOnContainers) GitHub deposunda mevcuttur.</span><span class="sxs-lookup"><span data-stu-id="132ca-129">The sample application is available at the [eShopOnContainers](https://github.com/dotnet-architecture/eShopOnContainers) GitHub repo.</span></span>

<span data-ttu-id="132ca-130">Bu kılavuzda, temel olarak iki teknolojiyi içeren bir geliştirme ortamı düzeyinde temel geliştirme ve mimari yönergeler sunulmaktadır: Docker ve .NET Core.</span><span class="sxs-lookup"><span data-stu-id="132ca-130">This guide provides foundational development and architectural guidance primarily at a development environment level with a focus on two technologies: Docker and .NET Core.</span></span> <span data-ttu-id="132ca-131">Amaç, üretim ortamınızın altyapısına (bulut veya şirket içi) odaklanmadan uygulama tasarımınız hakkında düşünce yaparken bu kılavuzu okuduğunuzdan emin olur.</span><span class="sxs-lookup"><span data-stu-id="132ca-131">Our intention is that you read this guide when thinking about your application design without focusing on the infrastructure (cloud or on-premises) of your production environment.</span></span> <span data-ttu-id="132ca-132">Daha sonra, üretime yönelik uygulamalar oluşturduğunuzda altyapınızla ilgili kararlar alırsınız.</span><span class="sxs-lookup"><span data-stu-id="132ca-132">You will make decisions about your infrastructure later, when you create your production-ready applications.</span></span> <span data-ttu-id="132ca-133">Bu nedenle, bu kılavuzun altyapı belirsiz ve daha fazla geliştirme ortamı merkezli olması amaçlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="132ca-133">Therefore, this guide is intended to be infrastructure agnostic and more development-environment-centric.</span></span>

<span data-ttu-id="132ca-134">Bu kılavuzu araştırdık aldıktan sonra, bir sonraki adımınız Microsoft Azure üzerinde üretime Ready mikro hizmetler hakkında bilgi almak için olacaktır.</span><span class="sxs-lookup"><span data-stu-id="132ca-134">After you have studied this guide, your next step would be to learn about production-ready microservices on Microsoft Azure.</span></span>

## <a name="version"></a><span data-ttu-id="132ca-135">Version</span><span class="sxs-lookup"><span data-stu-id="132ca-135">Version</span></span>

<span data-ttu-id="132ca-136">Bu kılavuz, **.NET Core 2,2** sürümünün yanı sıra teknolojilerin "Wave" ile ilgili birçok ek güncelleştirmeyi (yani,) kapsayacak şekilde değiştirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="132ca-136">This guide has been revised to cover **.NET Core 2.2** version plus many additional updates related to the same “wave” of technologies (that is.</span></span> <span data-ttu-id="132ca-137">Azure ve diğer 3. taraf teknolojileri) .NET Core 2,2 ile zaman içinde coinciding.</span><span class="sxs-lookup"><span data-stu-id="132ca-137">Azure and additional 3rd party technologies) coinciding in time with .NET Core 2.2.</span></span> <span data-ttu-id="132ca-138">Kitap sürümü de **2,2**sürümüne güncelleştirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="132ca-138">That’s why the book version has also been updated to version **2.2**.</span></span>

## <a name="what-this-guide-does-not-cover"></a><span data-ttu-id="132ca-139">Bu kılavuzun kapsamayan</span><span class="sxs-lookup"><span data-stu-id="132ca-139">What this guide does not cover</span></span>

<span data-ttu-id="132ca-140">Bu kılavuz uygulama yaşam döngüsü, DevOps, CI/CD işlem hatları veya takım çalışmasına odaklanmaz.</span><span class="sxs-lookup"><span data-stu-id="132ca-140">This guide does not focus on the application lifecycle, DevOps, CI/CD pipelines, or team work.</span></span> <span data-ttu-id="132ca-141">[Microsoft platformu ve araçları ile tamamlayıcı kılavuz Kapsayıcılı Docker uygulaması yaşam döngüsü](https://aka.ms/dockerlifecycleebook) ilgili konuya odaklanır.</span><span class="sxs-lookup"><span data-stu-id="132ca-141">The complementary guide [Containerized Docker Application Lifecycle with Microsoft Platform and Tools](https://aka.ms/dockerlifecycleebook) focuses on that subject.</span></span> <span data-ttu-id="132ca-142">Geçerli kılavuz Ayrıca, belirli düzenleyiciler hakkında bilgi gibi Azure altyapısında uygulama ayrıntıları sağlamaz.</span><span class="sxs-lookup"><span data-stu-id="132ca-142">The current guide also does not provide implementation details on Azure infrastructure, such as information on specific orchestrators.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="132ca-143">Ek kaynaklar</span><span class="sxs-lookup"><span data-stu-id="132ca-143">Additional resources</span></span>

- <span data-ttu-id="132ca-144">**Microsoft platformu ve araçları Ile Kapsayıcılı Docker uygulaması yaşam döngüsü** (indirilebilir e-kitap)</span><span class="sxs-lookup"><span data-stu-id="132ca-144">**Containerized Docker Application Lifecycle with Microsoft Platform and Tools** (downloadable e-book)</span></span>  
    <https://aka.ms/dockerlifecycleebook>

## <a name="who-should-use-this-guide"></a><span data-ttu-id="132ca-145">Bu kılavuzu kimler kullanmalıdır?</span><span class="sxs-lookup"><span data-stu-id="132ca-145">Who should use this guide</span></span>

<span data-ttu-id="132ca-146">Docker tabanlı uygulama geliştirmeye ve mikro hizmet tabanlı mimariye yönelik yeni olan geliştiriciler ve çözüm mimarları için bu kılavuzu yazdık.</span><span class="sxs-lookup"><span data-stu-id="132ca-146">We wrote this guide for developers and solution architects who are new to Docker-based application development and to microservices-based architecture.</span></span> <span data-ttu-id="132ca-147">Bu kılavuz, Microsoft geliştirme teknolojileri (.NET Core 'ta özel odak ile) ve Docker kapsayıcılarıyla kavram kanıtı uygulamalarının nasıl mimarilerini, tasarlanacağını ve uygulandığını öğrenmek istiyorsanız size yöneliktir.</span><span class="sxs-lookup"><span data-stu-id="132ca-147">This guide is for you if you want to learn how to architect, design, and implement proof-of-concept applications with Microsoft development technologies (with special focus on .NET Core) and with Docker containers.</span></span>

<span data-ttu-id="132ca-148">Ayrıca, yeni ve modern dağıtılmış uygulamalar için seçilecek yaklaşıma karar vermeden önce bir mimari ve teknolojiye genel bakış isteyen bir kuruluş mimarı gibi teknik bir karar veren bu kılavuzu da bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="132ca-148">You will also find this guide useful if you are a technical decision maker, such as an enterprise architect, who wants an architecture and technology overview before you decide on what approach to select for new and modern distributed applications.</span></span>

### <a name="how-to-use-this-guide"></a><span data-ttu-id="132ca-149">Bu kılavuz nasıl kullanılır?</span><span class="sxs-lookup"><span data-stu-id="132ca-149">How to use this guide</span></span>

<span data-ttu-id="132ca-150">Bu kılavuzun ilk bölümü Docker kapsayıcılarını tanıtır, .NET Core ve .NET Framework bir geliştirme çerçevesi olarak arasından nasıl seçim yapılacağını açıklar ve mikro hizmetlere genel bir bakış sağlar.</span><span class="sxs-lookup"><span data-stu-id="132ca-150">The first part of this guide introduces Docker containers, discusses how to choose between .NET Core and the .NET Framework as a development framework, and provides an overview of microservices.</span></span> <span data-ttu-id="132ca-151">Bu içerik, genel bakış isteyen, ancak kod uygulama ayrıntılarına odaklanmayı gerektirmeyen mimarlar ve teknik karar mekanizmaları içindir.</span><span class="sxs-lookup"><span data-stu-id="132ca-151">This content is for architects and technical decision makers who want an overview but don't need to focus on code implementation details.</span></span>

<span data-ttu-id="132ca-152">Kılavuzun ikinci bölümü, [Docker tabanlı uygulamalar Için geliştirme süreci](./docker-application-development-process/index.md) bölümüne başlar.</span><span class="sxs-lookup"><span data-stu-id="132ca-152">The second part of the guide starts with the [Development process for Docker based applications](./docker-application-development-process/index.md) section.</span></span> <span data-ttu-id="132ca-153">.NET Core ve Docker kullanarak uygulama uygulamaya yönelik geliştirme ve mikro hizmet desenlerine odaklanır.</span><span class="sxs-lookup"><span data-stu-id="132ca-153">It focuses on development and microservice patterns for implementing applications using .NET Core and Docker.</span></span> <span data-ttu-id="132ca-154">Bu bölüm, kod ve düzen ve uygulama ayrıntılarına odaklanmak isteyen geliştiricilere ve mimarlara yönelik en çok ilgi çekici olacaktır.</span><span class="sxs-lookup"><span data-stu-id="132ca-154">This section will be of most interest to developers and architects who want to focus on code and on patterns and implementation details.</span></span>

## <a name="related-microservice-and-container-based-reference-application-eshoponcontainers"></a><span data-ttu-id="132ca-155">İlgili mikro hizmet ve kapsayıcı tabanlı başvuru uygulaması: eShopOnContainers</span><span class="sxs-lookup"><span data-stu-id="132ca-155">Related microservice and container-based reference application: eShopOnContainers</span></span>

<span data-ttu-id="132ca-156">EShopOnContainers uygulaması, Docker Kapsayıcıları kullanılarak dağıtılacak şekilde tasarlanan .NET Core ve mikro hizmetlere yönelik açık kaynaklı bir başvuru uygulamasıdır.</span><span class="sxs-lookup"><span data-stu-id="132ca-156">The eShopOnContainers application is an open-source reference app for .NET Core and microservices that is designed to be deployed using Docker containers.</span></span> <span data-ttu-id="132ca-157">Uygulama, birkaç e-mağaza Kullanıcı arabirimi ön uçları (bir Web MVC uygulaması, Web SPA ve yerel bir mobil uygulama) dahil olmak üzere birden çok alt sistemi içerir.</span><span class="sxs-lookup"><span data-stu-id="132ca-157">The application consists of multiple subsystems, including several e-store UI front ends (a Web MVC app, a Web SPA, and a native mobile app).</span></span> <span data-ttu-id="132ca-158">Ayrıca, tüm gerekli sunucu tarafı işlemler için arka uç mikro hizmetleri ve kapsayıcıları da içerir.</span><span class="sxs-lookup"><span data-stu-id="132ca-158">It also includes the back-end microservices and containers for all required server-side operations.</span></span>

<span data-ttu-id="132ca-159">Uygulamanın amacı, mimari desenleri göstersağlamaktır.</span><span class="sxs-lookup"><span data-stu-id="132ca-159">The purpose of the application is to showcase architectural patterns.</span></span> <span data-ttu-id="132ca-160">Gerçek dünyada uygulamaları başlatmak için ÜRETIME yönelik olarak **hazırlanmayan BIR şablon değildir** .</span><span class="sxs-lookup"><span data-stu-id="132ca-160">**IT IS NOT A PRODUCTION-READY TEMPLATE** to start real-world applications.</span></span> <span data-ttu-id="132ca-161">Aslında, yeni ilginç teknolojileri göründükleri gibi test etmek için de kullanıldığından, uygulama kalıcı bir beta durumundadır.</span><span class="sxs-lookup"><span data-stu-id="132ca-161">In fact, the application is in a permanent beta state, as it’s also used to test new potentially interesting technologies as they show up.</span></span>

## <a name="send-us-your-feedback"></a><span data-ttu-id="132ca-162">Görüşlerinizi bize gönderin!</span><span class="sxs-lookup"><span data-stu-id="132ca-162">Send us your feedback!</span></span>

<span data-ttu-id="132ca-163">.NET 'teki Kapsayıcılı uygulamaların ve mikro hizmetlerin mimarisini anlamanıza yardımcı olması için bu kılavuzu yazdık.</span><span class="sxs-lookup"><span data-stu-id="132ca-163">We wrote this guide to help you understand the architecture of containerized applications and microservices in .NET.</span></span> <span data-ttu-id="132ca-164">Kılavuz ve ilgili başvuru uygulaması geliştireceğiz, bu nedenle geri bildirimlerinize hoş geldiniz!</span><span class="sxs-lookup"><span data-stu-id="132ca-164">The guide and related reference application will be evolving, so we welcome your feedback!</span></span> <span data-ttu-id="132ca-165">Bu kılavuzun nasıl iyileştirilen hakkında açıklamalarınız varsa, lütfen şu kişilere gönderin:</span><span class="sxs-lookup"><span data-stu-id="132ca-165">If you have comments about how this guide can be improved, please send them to:</span></span>

[dotnet-architecture-ebooks-feedback@service.microsoft.com](mailto:dotnet-architecture-ebooks-feedback@service.microsoft.com)

## <a name="credits"></a><span data-ttu-id="132ca-166">iler</span><span class="sxs-lookup"><span data-stu-id="132ca-166">Credits</span></span>

<span data-ttu-id="132ca-167">Ortak Yazarlar:</span><span class="sxs-lookup"><span data-stu-id="132ca-167">Co-Authors:</span></span>

> <span data-ttu-id="132ca-168">**Cesar de La Torre**, SR. PM, .net ürün ekibi, Microsoft Corp.</span><span class="sxs-lookup"><span data-stu-id="132ca-168">**Cesar de la Torre**, Sr. PM, .NET product team, Microsoft Corp.</span></span>
>
> <span data-ttu-id="132ca-169">**Bill Wagner**, SR. Content geliştirici, C + E, Microsoft Corp.</span><span class="sxs-lookup"><span data-stu-id="132ca-169">**Bill Wagner**, Sr. Content Developer, C+E, Microsoft Corp.</span></span>
>
> <span data-ttu-id="132ca-170">**Mike Rousos**, sorumlu yazılım mühendisi, DEVDIV Cat ekibi, Microsoft</span><span class="sxs-lookup"><span data-stu-id="132ca-170">**Mike Rousos**, Principal Software Engineer, DevDiv CAT team, Microsoft</span></span>

<span data-ttu-id="132ca-171">Edit</span><span class="sxs-lookup"><span data-stu-id="132ca-171">Editors:</span></span>

> <span data-ttu-id="132ca-172">**Mike Pope**</span><span class="sxs-lookup"><span data-stu-id="132ca-172">**Mike Pope**</span></span>
>
> <span data-ttu-id="132ca-173">**Steve Hoag**</span><span class="sxs-lookup"><span data-stu-id="132ca-173">**Steve Hoag**</span></span>

<span data-ttu-id="132ca-174">Katılımcılar ve gözden geçirenler:</span><span class="sxs-lookup"><span data-stu-id="132ca-174">Participants and reviewers:</span></span>

> <span data-ttu-id="132ca-175">**Jeffrey Richter**, Iş ortağı yazılım eng, Azure ekibi, Microsoft</span><span class="sxs-lookup"><span data-stu-id="132ca-175">**Jeffrey Richter**, Partner Software Eng, Azure team, Microsoft</span></span>
>
> <span data-ttu-id="132ca-176">**Jimmy Bogard**, yay Başkan mimarı</span><span class="sxs-lookup"><span data-stu-id="132ca-176">**Jimmy Bogard**, Chief Architect at Headspring</span></span>
>
> <span data-ttu-id="132ca-177">**UDI Dahan**, & CEO, belirli yazılımlar</span><span class="sxs-lookup"><span data-stu-id="132ca-177">**Udi Dahan**, Founder & CEO, Particular Software</span></span>
>
> <span data-ttu-id="132ca-178">**Jimmy Nilsson**, Co-foin ve CEO of Factor10</span><span class="sxs-lookup"><span data-stu-id="132ca-178">**Jimmy Nilsson**, Co-founder and CEO of Factor10</span></span>
>
> <span data-ttu-id="132ca-179">**Glenn CONDRON**, SR. program yöneticisi, ASP.NET ekibi</span><span class="sxs-lookup"><span data-stu-id="132ca-179">**Glenn Condron**, Sr. Program Manager, ASP.NET team</span></span>
>
> <span data-ttu-id="132ca-180">**Mark Fussell**, sorumlu PM lideri, Azure Service Fabric ekibi, Microsoft</span><span class="sxs-lookup"><span data-stu-id="132ca-180">**Mark Fussell**, Principal PM Lead, Azure Service Fabric team, Microsoft</span></span>
>
> <span data-ttu-id="132ca-181">**Diego Vega**, PM lideri, Entity Framework ekibi, Microsoft</span><span class="sxs-lookup"><span data-stu-id="132ca-181">**Diego Vega**, PM Lead, Entity Framework team, Microsoft</span></span>
>
> <span data-ttu-id="132ca-182">**Barry Dorrans**, SR. Security Program Yöneticisi</span><span class="sxs-lookup"><span data-stu-id="132ca-182">**Barry Dorrans**, Sr. Security Program Manager</span></span>
>
> <span data-ttu-id="132ca-183">**Rowa Miller**, SR. Program Yöneticisi, Microsoft</span><span class="sxs-lookup"><span data-stu-id="132ca-183">**Rowan Miller**, Sr. Program Manager, Microsoft</span></span>
>
> <span data-ttu-id="132ca-184">**Ankit Asthana**, ana PM Yöneticisi, .NET ekibi, Microsoft</span><span class="sxs-lookup"><span data-stu-id="132ca-184">**Ankit Asthana**, Principal PM Manager, .NET team, Microsoft</span></span>
>
> <span data-ttu-id="132ca-185">**Scott Hunter**, Iş ortağı Direktörü, .NET ekibi, Microsoft</span><span class="sxs-lookup"><span data-stu-id="132ca-185">**Scott Hunter**, Partner Director PM, .NET team, Microsoft</span></span>
>
> <span data-ttu-id="132ca-186">**Hayvan anıl**, SR. Program Yöneticisi, .NET ekibi, Microsoft</span><span class="sxs-lookup"><span data-stu-id="132ca-186">**Nish Anil**, Sr. Program Manager, .NET team, Microsoft</span></span>
>
> <span data-ttu-id="132ca-187">**Dylan Reisenberger**, mimarı ve dev lideri, Polly</span><span class="sxs-lookup"><span data-stu-id="132ca-187">**Dylan Reisenberger**, Architect and Dev Lead at Polly</span></span>
>
> <span data-ttu-id="132ca-188">**Steve "ardalış" Smith** -yazılım mimarı ve trainer- [Ardalis.com](https://ardalis.com)</span><span class="sxs-lookup"><span data-stu-id="132ca-188">**Steve "ardalis" Smith** - Software Architect and Trainer - [Ardalis.com](https://ardalis.com)</span></span>
>
> <span data-ttu-id="132ca-189">**Ian Cooper**, kod mimarı parlaktır</span><span class="sxs-lookup"><span data-stu-id="132ca-189">**Ian Cooper**, Coding Architect at Brighter</span></span>
>
> <span data-ttu-id="132ca-190">Düz kavramlarda **Unaı Zorrilla**, mimar ve dev lideri</span><span class="sxs-lookup"><span data-stu-id="132ca-190">**Unai Zorrilla**, Architect and Dev Lead at Plain Concepts</span></span>
>
> <span data-ttu-id="132ca-191">**Eğitik Tomas**, geliştirme lideri, düz kavramlar</span><span class="sxs-lookup"><span data-stu-id="132ca-191">**Eduard Tomas**, Dev Lead at Plain Concepts</span></span>
>
> <span data-ttu-id="132ca-192">**Vamon Tomas**, geliştirici basit kavramlar</span><span class="sxs-lookup"><span data-stu-id="132ca-192">**Ramon Tomas**, Developer at Plain Concepts</span></span>
>
> <span data-ttu-id="132ca-193">**David Sanz**, basit kavramlarda geliştirici</span><span class="sxs-lookup"><span data-stu-id="132ca-193">**David Sanz**, Developer at Plain Concepts</span></span>
>
> <span data-ttu-id="132ca-194">**Javier Valero**, çalışma müdürü, Grupo 'da</span><span class="sxs-lookup"><span data-stu-id="132ca-194">**Javier Valero**, Chief Operating Officer at Grupo Solutio</span></span>
>
> <span data-ttu-id="132ca-195">**Pierre millet**, SR. danışman, Microsoft</span><span class="sxs-lookup"><span data-stu-id="132ca-195">**Pierre Millet**, Sr. Consultant, Microsoft</span></span>
>
> <span data-ttu-id="132ca-196">**Michael Fri,** Ürün Yöneticisi, Docker Inc</span><span class="sxs-lookup"><span data-stu-id="132ca-196">**Michael Friis**, Product Manager, Docker Inc</span></span>
>
> <span data-ttu-id="132ca-197">**Charles Lowell**, yazılım mühendısı, vs Cat ekibi, Microsoft</span><span class="sxs-lookup"><span data-stu-id="132ca-197">**Charles Lowell**, Software Engineer, VS CAT team, Microsoft</span></span>
>
> <span data-ttu-id="132ca-198">**Miguel Veloso**, SR. danışman, zorlu zorluk</span><span class="sxs-lookup"><span data-stu-id="132ca-198">**Miguel Veloso**, Sr. Consultant at Turing Challenge</span></span>

## <a name="copyright"></a><span data-ttu-id="132ca-199">yaptırımlar</span><span class="sxs-lookup"><span data-stu-id="132ca-199">Copyright</span></span>

<span data-ttu-id="132ca-200">INDIRME şu adreste bulunabilir: <https://aka.ms/microservicesebook></span><span class="sxs-lookup"><span data-stu-id="132ca-200">DOWNLOAD available at: <https://aka.ms/microservicesebook></span></span>

<span data-ttu-id="132ca-201">YAYıMLAYAN</span><span class="sxs-lookup"><span data-stu-id="132ca-201">PUBLISHED BY</span></span>

<span data-ttu-id="132ca-202">Microsoft Geliştirici bölümü, .NET ve Visual Studio ürün ekipleri</span><span class="sxs-lookup"><span data-stu-id="132ca-202">Microsoft Developer Division, .NET and Visual Studio product teams</span></span>

<span data-ttu-id="132ca-203">Microsoft Corporation 'ın bir bölümü</span><span class="sxs-lookup"><span data-stu-id="132ca-203">A division of Microsoft Corporation</span></span>

<span data-ttu-id="132ca-204">One Microsoft Way</span><span class="sxs-lookup"><span data-stu-id="132ca-204">One Microsoft Way</span></span>

<span data-ttu-id="132ca-205">Redmond, Washington 98052-6399</span><span class="sxs-lookup"><span data-stu-id="132ca-205">Redmond, Washington 98052-6399</span></span>

<span data-ttu-id="132ca-206">Telif hakkı © 2019 Microsoft Corporation</span><span class="sxs-lookup"><span data-stu-id="132ca-206">Copyright © 2019 by Microsoft Corporation</span></span>

<span data-ttu-id="132ca-207">Tüm hakları saklıdır.</span><span class="sxs-lookup"><span data-stu-id="132ca-207">All rights reserved.</span></span> <span data-ttu-id="132ca-208">Bu kitabın içeriğinin herhangi bir bölümü herhangi bir biçimde veya herhangi bir şekilde veya başka bir şekilde herhangi bir şekilde çoğaltılamaz veya herhangi bir şekilde gönderilebilir.</span><span class="sxs-lookup"><span data-stu-id="132ca-208">No part of the contents of this book may be reproduced or transmitted in any form or by any means without the written permission of the publisher.</span></span>

<span data-ttu-id="132ca-209">Bu kitap, "olduğu gibi" verilmiştir ve yazarın görünümlerini ve opnons 'yi ifade eder.</span><span class="sxs-lookup"><span data-stu-id="132ca-209">This book is provided “as-is” and expresses the author’s views and opinions.</span></span> <span data-ttu-id="132ca-210">Bu kitapta ifade edilen görünümler, eklentiler ve bilgiler, URL ve diğer Internet Web sitesi başvuruları da dahil olmak üzere bildirimde bulunmaksızın değiştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="132ca-210">The views, opinions and information expressed in this book, including URL and other Internet website references, may change without notice.</span></span>

<span data-ttu-id="132ca-211">Burada gösterilen bazı örnekler yalnızca gösterim amaçlıdır ve hayal ürünüdür.</span><span class="sxs-lookup"><span data-stu-id="132ca-211">Some examples depicted herein are provided for illustration only and are fictitious.</span></span> <span data-ttu-id="132ca-212">Hiçbir gerçek ilişkilendirme veya bağlantı amaçlanmaz veya çıkarsanmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="132ca-212">No real association or connection is intended or should be inferred.</span></span>

<span data-ttu-id="132ca-213">Microsoft ve "ticari markalar" Web sayfasındaki <https://www.microsoft.com> listelenen ticari markalar, Microsoft şirketler grubunun ticari markalarıdır.</span><span class="sxs-lookup"><span data-stu-id="132ca-213">Microsoft and the trademarks listed at <https://www.microsoft.com> on the “Trademarks” webpage are trademarks of the Microsoft group of companies.</span></span>

<span data-ttu-id="132ca-214">Mac ve macOS, Apple Inc. ' in ticari markalarıdır.</span><span class="sxs-lookup"><span data-stu-id="132ca-214">Mac and macOS are trademarks of Apple Inc.</span></span>

<span data-ttu-id="132ca-215">Docker balina logosu,, izin tarafından kullanılan Docker, Inc. ' in tescilli ticari markasıdır.</span><span class="sxs-lookup"><span data-stu-id="132ca-215">The Docker whale logo is a registered trademark of Docker, Inc. Used by permission.</span></span>

<span data-ttu-id="132ca-216">Diğer tüm işaretler ve amblemler kendi sahiplerinin mülkiyetindedir.</span><span class="sxs-lookup"><span data-stu-id="132ca-216">All other marks and logos are property of their respective owners.</span></span>

>[!div class="step-by-step"]
>[<span data-ttu-id="132ca-217">Next</span><span class="sxs-lookup"><span data-stu-id="132ca-217">Next</span></span>](container-docker-introduction/index.md)
