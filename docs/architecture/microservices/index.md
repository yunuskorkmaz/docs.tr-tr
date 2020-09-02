---
title: .NET mikro hizmetleri. Kapsayıcılı .NET Uygulamaları Mimarisi
description: Kapsayıcılı .NET uygulamaları için .NET mikro hizmetleri mimarisi | Mikro hizmetler modüler ve bağımsız olarak dağıtılabilir hizmetlerdir. Docker Kapsayıcıları (Linux ve Windows için), bir hizmet ve bağımlılıklarını tek bir birim halinde paketleyerek dağıtım ve test etmeyi basitleştirir. Bu, daha sonra yalıtılmış bir ortamda çalıştırılır.
ms.date: 09/02/2020
ms.openlocfilehash: aea5012fee102f388827d146043e69592e14f22b
ms.sourcegitcommit: b78018c850590dfc0348301e1748b779c28604cc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "89379141"
---
# <a name="net-microservices-architecture-for-containerized-net-applications"></a><span data-ttu-id="f799a-105">.NET Mikro Hizmetleri: Kapsayıcılı .NET Uygulamaları Mimarisi</span><span class="sxs-lookup"><span data-stu-id="f799a-105">.NET Microservices: Architecture for Containerized .NET Applications</span></span>

![Kitap kapağı](./media/cover-small.png)

<span data-ttu-id="f799a-107">**Sürüm v 3.1.2** -ASP.NET Core 3,1 ' ye güncelleştirildi</span><span class="sxs-lookup"><span data-stu-id="f799a-107">**EDITION v3.1.2** - Updated to ASP.NET Core 3.1</span></span>

<span data-ttu-id="f799a-108">Bu kılavuz, mikro hizmet tabanlı uygulamalar geliştirmeye ve kapsayıcıları kullanarak bunları yönetmeye yönelik bir giriş niteliğindedir.</span><span class="sxs-lookup"><span data-stu-id="f799a-108">This guide is an introduction to developing microservices-based applications and managing them using containers.</span></span> <span data-ttu-id="f799a-109">.NET Core ve Docker Kapsayıcıları kullanılarak mimari tasarımı ve uygulama yaklaşımlarını ele alır.</span><span class="sxs-lookup"><span data-stu-id="f799a-109">It discusses architectural design and implementation approaches using .NET Core and Docker containers.</span></span>

<span data-ttu-id="f799a-110">Daha kolay çalışmaya başlamak için kılavuz, keşfedebileceğiniz bir başvuru Kapsayıcılı ve mikro hizmet tabanlı uygulamaya odaklanır.</span><span class="sxs-lookup"><span data-stu-id="f799a-110">To make it easier to get started, the guide focuses on a reference containerized and microservice-based application that you can explore.</span></span> <span data-ttu-id="f799a-111">Başvuru uygulaması [Eshoponcontainers](https://github.com/dotnet-architecture/eShopOnContainers) GitHub deposunda mevcuttur.</span><span class="sxs-lookup"><span data-stu-id="f799a-111">The reference application is available at the [eShopOnContainers](https://github.com/dotnet-architecture/eShopOnContainers) GitHub repo.</span></span>

## <a name="action-links"></a><span data-ttu-id="f799a-112">Eylem bağlantıları</span><span class="sxs-lookup"><span data-stu-id="f799a-112">Action links</span></span>

- <span data-ttu-id="f799a-113">Bu e-kitap ayrıca bir PDF biçiminde (Yalnızca Ingilizce sürüm) [indirilebilir](https://aka.ms/microservicesebook)</span><span class="sxs-lookup"><span data-stu-id="f799a-113">This e-book is also available in a PDF format (English version only) [Download](https://aka.ms/microservicesebook)</span></span>

- <span data-ttu-id="f799a-114">[GitHub 'daki başvuru uygulaması Eshoponcontainers 'ı](https://github.com/dotnet-architecture/eShopOnContainers) kopyalama/çatal</span><span class="sxs-lookup"><span data-stu-id="f799a-114">Clone/Fork the reference application [eShopOnContainers on GitHub](https://github.com/dotnet-architecture/eShopOnContainers)</span></span>

- <span data-ttu-id="f799a-115">[Kanal 9 ' da tanıtım videosunu](https://aka.ms/microservices-video) izleyin</span><span class="sxs-lookup"><span data-stu-id="f799a-115">Watch the [introductory video on Channel 9](https://aka.ms/microservices-video)</span></span>

- <span data-ttu-id="f799a-116">[Mikro hizmet mimarisini](https://aka.ms/MicroservicesArchitecture) hemen öğrenin</span><span class="sxs-lookup"><span data-stu-id="f799a-116">Get to know the [Microservices Architecture](https://aka.ms/MicroservicesArchitecture) right away</span></span>

## <a name="introduction"></a><span data-ttu-id="f799a-117">Giriş</span><span class="sxs-lookup"><span data-stu-id="f799a-117">Introduction</span></span>

<span data-ttu-id="f799a-118">Kuruluşlar daha fazla maliyet tasarrufu, dağıtım sorunlarını çözme ve kapsayıcıları kullanarak DevOps ve üretim işlemlerini geliştirme.</span><span class="sxs-lookup"><span data-stu-id="f799a-118">Enterprises are increasingly realizing cost savings, solving deployment problems, and improving DevOps and production operations by using containers.</span></span> <span data-ttu-id="f799a-119">Microsoft, Azure Kubernetes hizmeti ve Azure Service Fabric gibi ürünler oluşturarak ve Docker, Mesosphere ve Kubernetes gibi sektör liderleriyle işbirliği yaparak Windows ve Linux için kapsayıcı yenilikleri yayımlamaktadır.</span><span class="sxs-lookup"><span data-stu-id="f799a-119">Microsoft has been releasing container innovations for Windows and Linux by creating products like Azure Kubernetes Service and Azure Service Fabric, and by partnering with industry leaders like Docker, Mesosphere, and Kubernetes.</span></span> <span data-ttu-id="f799a-120">Bu ürünler, şirketlerin bulut hızında ve ölçekte uygulama oluşturup dağıtmalarına yardımcı olan kapsayıcı çözümleri sunar.</span><span class="sxs-lookup"><span data-stu-id="f799a-120">These products deliver container solutions that help companies build and deploy applications at cloud speed and scale, whatever their choice of platform or tools.</span></span>

<span data-ttu-id="f799a-121">Docker, Windows ve Linux ekosistemlerindeki en önemli satıcılar tarafından desteklenen kapsayıcı sektöründe standart bir standart haline geliyor.</span><span class="sxs-lookup"><span data-stu-id="f799a-121">Docker is becoming the de facto standard in the container industry, supported by the most significant vendors in the Windows and Linux ecosystems.</span></span> <span data-ttu-id="f799a-122">(Microsoft, Docker destekleyen ana bulut satıcılarından biridir.) Gelecekte Docker, büyük olasılıkla buluttaki veya Şirket içindeki herhangi bir veri merkezinde yer alır.</span><span class="sxs-lookup"><span data-stu-id="f799a-122">(Microsoft is one of the main cloud vendors supporting Docker.) In the future, Docker will probably be ubiquitous in any datacenter in the cloud or on-premises.</span></span>

<span data-ttu-id="f799a-123">Ayrıca, [mikro hizmetler](https://martinfowler.com/articles/microservices.html) mimarisi, dağıtılmış görev açısından kritik uygulamalar için önemli bir yaklaşım olarak gelişmekte.</span><span class="sxs-lookup"><span data-stu-id="f799a-123">In addition, the [microservices](https://martinfowler.com/articles/microservices.html) architecture is emerging as an important approach for distributed mission-critical applications.</span></span> <span data-ttu-id="f799a-124">Mikro hizmet tabanlı bir mimaride, uygulama, bağımsız olarak geliştirilen, test edilmiş, dağıtılan ve sürümü tutulan bir hizmetler koleksiyonu üzerine kurulmuştur.</span><span class="sxs-lookup"><span data-stu-id="f799a-124">In a microservice-based architecture, the application is built on a collection of services that can be developed, tested, deployed, and versioned independently.</span></span>

## <a name="about-this-guide"></a><span data-ttu-id="f799a-125">Bu kılavuz hakkında</span><span class="sxs-lookup"><span data-stu-id="f799a-125">About this guide</span></span>

<span data-ttu-id="f799a-126">Bu kılavuz, mikro hizmet tabanlı uygulamalar geliştirmeye ve kapsayıcıları kullanarak bunları yönetmeye yönelik bir giriş niteliğindedir.</span><span class="sxs-lookup"><span data-stu-id="f799a-126">This guide is an introduction to developing microservices-based applications and managing them using containers.</span></span> <span data-ttu-id="f799a-127">.NET Core ve Docker Kapsayıcıları kullanılarak mimari tasarımı ve uygulama yaklaşımlarını ele alır.</span><span class="sxs-lookup"><span data-stu-id="f799a-127">It discusses architectural design and implementation approaches using .NET Core and Docker containers.</span></span> <span data-ttu-id="f799a-128">Kapsayıcılar ve mikro hizmetlerle çalışmaya başlamanızı kolaylaştırmak için, rehber, keşfedebileceğiniz bir başvuru Kapsayıcılı ve mikro hizmet tabanlı uygulamaya odaklanır.</span><span class="sxs-lookup"><span data-stu-id="f799a-128">To make it easier to get started with containers and microservices, the guide focuses on a reference containerized and microservice-based application that you can explore.</span></span> <span data-ttu-id="f799a-129">Örnek uygulama [Eshoponcontainers](https://github.com/dotnet-architecture/eShopOnContainers) GitHub deposunda mevcuttur.</span><span class="sxs-lookup"><span data-stu-id="f799a-129">The sample application is available at the [eShopOnContainers](https://github.com/dotnet-architecture/eShopOnContainers) GitHub repo.</span></span>

<span data-ttu-id="f799a-130">Bu kılavuzda, temel olarak iki teknolojiyi içeren bir geliştirme ortamı düzeyinde temel geliştirme ve mimari yönergeler sunulmaktadır: Docker ve .NET Core.</span><span class="sxs-lookup"><span data-stu-id="f799a-130">This guide provides foundational development and architectural guidance primarily at a development environment level with a focus on two technologies: Docker and .NET Core.</span></span> <span data-ttu-id="f799a-131">Amaç, üretim ortamınızın altyapısına (bulut veya şirket içi) odaklanmadan uygulama tasarımınız hakkında düşünce yaparken bu kılavuzu okuduğunuzdan emin olur.</span><span class="sxs-lookup"><span data-stu-id="f799a-131">Our intention is that you read this guide when thinking about your application design without focusing on the infrastructure (cloud or on-premises) of your production environment.</span></span> <span data-ttu-id="f799a-132">Daha sonra, üretime yönelik uygulamalar oluşturduğunuzda altyapınızla ilgili kararlar alırsınız.</span><span class="sxs-lookup"><span data-stu-id="f799a-132">You will make decisions about your infrastructure later, when you create your production-ready applications.</span></span> <span data-ttu-id="f799a-133">Bu nedenle, bu kılavuzun altyapı belirsiz ve daha fazla geliştirme ortamı merkezli olması amaçlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="f799a-133">Therefore, this guide is intended to be infrastructure agnostic and more development-environment-centric.</span></span>

<span data-ttu-id="f799a-134">Bu kılavuzu araştırdık aldıktan sonra, bir sonraki adımınız Microsoft Azure üzerinde üretime Ready mikro hizmetler hakkında bilgi almak için olacaktır.</span><span class="sxs-lookup"><span data-stu-id="f799a-134">After you have studied this guide, your next step would be to learn about production-ready microservices on Microsoft Azure.</span></span>

## <a name="version"></a><span data-ttu-id="f799a-135">Sürüm</span><span class="sxs-lookup"><span data-stu-id="f799a-135">Version</span></span>

<span data-ttu-id="f799a-136">Bu kılavuz, .NET Core 3,1 sürümüyle aynı "Wave" teknolojileri (Azure ve ek üçüncü taraf teknolojileri) ile ilgili birçok ek güncelleştirme ile birlikte **.net core 3,1** sürümünü kapsayacak şekilde değiştirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="f799a-136">This guide has been revised to cover **.NET Core 3.1** version along with many additional updates related to the same “wave” of technologies (that is, Azure and additional third-party technologies) coinciding in time with the .NET Core 3.1 release.</span></span> <span data-ttu-id="f799a-137">Kitap sürümü de **3,1**sürümüne güncelleştirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="f799a-137">That’s why the book version has also been updated to version **3.1**.</span></span>

## <a name="what-this-guide-does-not-cover"></a><span data-ttu-id="f799a-138">Bu kılavuzun kapsamayan</span><span class="sxs-lookup"><span data-stu-id="f799a-138">What this guide does not cover</span></span>

<span data-ttu-id="f799a-139">Bu kılavuz uygulama yaşam döngüsü, DevOps, CI/CD işlem hatları veya takım çalışmasına odaklanmaz.</span><span class="sxs-lookup"><span data-stu-id="f799a-139">This guide does not focus on the application lifecycle, DevOps, CI/CD pipelines, or team work.</span></span> <span data-ttu-id="f799a-140">[Microsoft platformu ve araçları ile tamamlayıcı kılavuz Kapsayıcılı Docker uygulaması yaşam döngüsü](https://aka.ms/dockerlifecycleebook) ilgili konuya odaklanır.</span><span class="sxs-lookup"><span data-stu-id="f799a-140">The complementary guide [Containerized Docker Application Lifecycle with Microsoft Platform and Tools](https://aka.ms/dockerlifecycleebook) focuses on that subject.</span></span> <span data-ttu-id="f799a-141">Geçerli kılavuz Ayrıca, belirli düzenleyiciler hakkında bilgi gibi Azure altyapısında uygulama ayrıntıları sağlamaz.</span><span class="sxs-lookup"><span data-stu-id="f799a-141">The current guide also does not provide implementation details on Azure infrastructure, such as information on specific orchestrators.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="f799a-142">Ek kaynaklar</span><span class="sxs-lookup"><span data-stu-id="f799a-142">Additional resources</span></span>

- <span data-ttu-id="f799a-143">**Microsoft platformu ve araçları Ile Kapsayıcılı Docker uygulaması yaşam döngüsü** (indirilebilir e-kitap)</span><span class="sxs-lookup"><span data-stu-id="f799a-143">**Containerized Docker Application Lifecycle with Microsoft Platform and Tools** (downloadable e-book)</span></span>  
    <https://aka.ms/dockerlifecycleebook>

## <a name="who-should-use-this-guide"></a><span data-ttu-id="f799a-144">Bu kılavuzu kimler kullanmalıdır?</span><span class="sxs-lookup"><span data-stu-id="f799a-144">Who should use this guide</span></span>

<span data-ttu-id="f799a-145">Docker tabanlı uygulama geliştirmeye ve mikro hizmet tabanlı mimariye yönelik yeni olan geliştiriciler ve çözüm mimarları için bu kılavuzu yazdık.</span><span class="sxs-lookup"><span data-stu-id="f799a-145">We wrote this guide for developers and solution architects who are new to Docker-based application development and to microservices-based architecture.</span></span> <span data-ttu-id="f799a-146">Bu kılavuz, Microsoft geliştirme teknolojileri (.NET Core 'ta özel odak ile) ve Docker kapsayıcılarıyla kavram kanıtı uygulamalarının nasıl mimarilerini, tasarlanacağını ve uygulandığını öğrenmek istiyorsanız size yöneliktir.</span><span class="sxs-lookup"><span data-stu-id="f799a-146">This guide is for you if you want to learn how to architect, design, and implement proof-of-concept applications with Microsoft development technologies (with special focus on .NET Core) and with Docker containers.</span></span>

<span data-ttu-id="f799a-147">Ayrıca, yeni ve modern dağıtılmış uygulamalar için seçilecek yaklaşıma karar vermeden önce bir mimari ve teknolojiye genel bakış isteyen bir kuruluş mimarı gibi teknik bir karar veren bu kılavuzu da bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f799a-147">You will also find this guide useful if you are a technical decision maker, such as an enterprise architect, who wants an architecture and technology overview before you decide on what approach to select for new and modern distributed applications.</span></span>

### <a name="how-to-use-this-guide"></a><span data-ttu-id="f799a-148">Bu kılavuz nasıl kullanılır?</span><span class="sxs-lookup"><span data-stu-id="f799a-148">How to use this guide</span></span>

<span data-ttu-id="f799a-149">Bu kılavuzun ilk bölümü Docker kapsayıcılarını tanıtır, .NET Core ve .NET Framework bir geliştirme çerçevesi olarak arasından nasıl seçim yapılacağını açıklar ve mikro hizmetlere genel bir bakış sağlar.</span><span class="sxs-lookup"><span data-stu-id="f799a-149">The first part of this guide introduces Docker containers, discusses how to choose between .NET Core and the .NET Framework as a development framework, and provides an overview of microservices.</span></span> <span data-ttu-id="f799a-150">Bu içerik, genel bakış isteyen, ancak kod uygulama ayrıntılarına odaklanmayı gerektirmeyen mimarlar ve teknik karar mekanizmaları içindir.</span><span class="sxs-lookup"><span data-stu-id="f799a-150">This content is for architects and technical decision makers who want an overview but don't need to focus on code implementation details.</span></span>

<span data-ttu-id="f799a-151">Kılavuzun ikinci bölümü, [Docker tabanlı uygulamalar Için geliştirme süreci](./docker-application-development-process/index.md) bölümüne başlar.</span><span class="sxs-lookup"><span data-stu-id="f799a-151">The second part of the guide starts with the [Development process for Docker based applications](./docker-application-development-process/index.md) section.</span></span> <span data-ttu-id="f799a-152">.NET Core ve Docker kullanarak uygulama uygulamaya yönelik geliştirme ve mikro hizmet düzenlerine odaklanır.</span><span class="sxs-lookup"><span data-stu-id="f799a-152">It focuses on the development and microservice patterns for implementing applications using .NET Core and Docker.</span></span> <span data-ttu-id="f799a-153">Bu bölüm, kod ve düzen ve uygulama ayrıntılarına odaklanmak isteyen geliştiricilere ve mimarlara yönelik en çok ilgi çekici olacaktır.</span><span class="sxs-lookup"><span data-stu-id="f799a-153">This section will be of most interest to developers and architects who want to focus on code and on patterns and implementation details.</span></span>

## <a name="related-microservice-and-container-based-reference-application-eshoponcontainers"></a><span data-ttu-id="f799a-154">İlgili mikro hizmet ve kapsayıcı tabanlı başvuru uygulaması: eShopOnContainers</span><span class="sxs-lookup"><span data-stu-id="f799a-154">Related microservice and container-based reference application: eShopOnContainers</span></span>

<span data-ttu-id="f799a-155">EShopOnContainers uygulaması, Docker Kapsayıcıları kullanılarak dağıtılacak şekilde tasarlanan .NET Core ve mikro hizmetlere yönelik açık kaynaklı bir başvuru uygulamasıdır.</span><span class="sxs-lookup"><span data-stu-id="f799a-155">The eShopOnContainers application is an open-source reference app for .NET Core and microservices that is designed to be deployed using Docker containers.</span></span> <span data-ttu-id="f799a-156">Uygulama, çeşitli e-mağaza Kullanıcı arabirimi ön uçları (bir Web MVC uygulaması, Web SPA ve yerel bir mobil uygulama) dahil olmak üzere birden çok alt sistemi içerir.</span><span class="sxs-lookup"><span data-stu-id="f799a-156">The application consists of multiple subsystems, including several e-store UI front-ends (a Web MVC app, a Web SPA, and a native mobile app).</span></span> <span data-ttu-id="f799a-157">Ayrıca, tüm gerekli sunucu tarafı işlemler için arka uç mikro hizmetleri ve kapsayıcıları da içerir.</span><span class="sxs-lookup"><span data-stu-id="f799a-157">It also includes the back-end microservices and containers for all required server-side operations.</span></span>

<span data-ttu-id="f799a-158">Uygulamanın amacı, mimari desenleri göstersağlamaktır.</span><span class="sxs-lookup"><span data-stu-id="f799a-158">The purpose of the application is to showcase architectural patterns.</span></span> <span data-ttu-id="f799a-159">Gerçek dünyada uygulamaları başlatmak için ÜRETIME yönelik olarak **hazırlanmayan BIR şablon değildir** .</span><span class="sxs-lookup"><span data-stu-id="f799a-159">**IT IS NOT A PRODUCTION-READY TEMPLATE** to start real-world applications.</span></span> <span data-ttu-id="f799a-160">Aslında, yeni ilginç teknolojileri göründükleri gibi test etmek için de kullanıldığından, uygulama kalıcı bir beta durumundadır.</span><span class="sxs-lookup"><span data-stu-id="f799a-160">In fact, the application is in a permanent beta state, as it's also used to test new potentially interesting technologies as they show up.</span></span>

## <a name="send-us-your-feedback"></a><span data-ttu-id="f799a-161">Bize geri bildirimlerinizi gönderin!</span><span class="sxs-lookup"><span data-stu-id="f799a-161">Send us your feedback!</span></span>

<span data-ttu-id="f799a-162">.NET 'teki Kapsayıcılı uygulamaların ve mikro hizmetlerin mimarisini anlamanıza yardımcı olması için bu kılavuzu yazdık.</span><span class="sxs-lookup"><span data-stu-id="f799a-162">We wrote this guide to help you understand the architecture of containerized applications and microservices in .NET.</span></span> <span data-ttu-id="f799a-163">Kılavuz ve ilgili başvuru uygulaması geliştireceğiz, bu nedenle geri bildirimlerinize hoş geldiniz!</span><span class="sxs-lookup"><span data-stu-id="f799a-163">The guide and related reference application will be evolving, so we welcome your feedback!</span></span> <span data-ttu-id="f799a-164">Bu kılavuzun nasıl iyileştirilen hakkında açıklamalara sahipseniz, konusunda geri bildirimde bulunun <https://aka.ms/ebookfeedback> .</span><span class="sxs-lookup"><span data-stu-id="f799a-164">If you have comments about how this guide can be improved, submit feedback at <https://aka.ms/ebookfeedback>.</span></span>

## <a name="credits"></a><span data-ttu-id="f799a-165">Krediler</span><span class="sxs-lookup"><span data-stu-id="f799a-165">Credits</span></span>

<span data-ttu-id="f799a-166">Ortak Yazarlar:</span><span class="sxs-lookup"><span data-stu-id="f799a-166">Co-Authors:</span></span>

> <span data-ttu-id="f799a-167">**Cesar de La Torre**, SR. PM, .net ürün ekibi, Microsoft Corp.</span><span class="sxs-lookup"><span data-stu-id="f799a-167">**Cesar de la Torre**, Sr. PM, .NET product team, Microsoft Corp.</span></span>
>
> <span data-ttu-id="f799a-168">**Bill Wagner**, SR. Content geliştirici, C + E, Microsoft Corp.</span><span class="sxs-lookup"><span data-stu-id="f799a-168">**Bill Wagner**, Sr. Content Developer, C+E, Microsoft Corp.</span></span>
>
> <span data-ttu-id="f799a-169">**Mike Rousos**, sorumlu yazılım mühendisi, DEVDIV Cat ekibi, Microsoft</span><span class="sxs-lookup"><span data-stu-id="f799a-169">**Mike Rousos**, Principal Software Engineer, DevDiv CAT team, Microsoft</span></span>

<span data-ttu-id="f799a-170">Edit</span><span class="sxs-lookup"><span data-stu-id="f799a-170">Editors:</span></span>

> <span data-ttu-id="f799a-171">**Mike Pope**</span><span class="sxs-lookup"><span data-stu-id="f799a-171">**Mike Pope**</span></span>
>
> <span data-ttu-id="f799a-172">**Steve Hoag**</span><span class="sxs-lookup"><span data-stu-id="f799a-172">**Steve Hoag**</span></span>

<span data-ttu-id="f799a-173">Katılımcılar ve gözden geçirenler:</span><span class="sxs-lookup"><span data-stu-id="f799a-173">Participants and reviewers:</span></span>

> <span data-ttu-id="f799a-174">**Jeffrey Richter**, Iş ortağı yazılım eng, Azure ekibi, Microsoft</span><span class="sxs-lookup"><span data-stu-id="f799a-174">**Jeffrey Richter**, Partner Software Eng, Azure team, Microsoft</span></span>
>
> <span data-ttu-id="f799a-175">**Jimmy Bogard**, yay Başkan mimarı</span><span class="sxs-lookup"><span data-stu-id="f799a-175">**Jimmy Bogard**, Chief Architect at Headspring</span></span>
>
> <span data-ttu-id="f799a-176">**UDI Dahan**, & CEO, belirli yazılımlar</span><span class="sxs-lookup"><span data-stu-id="f799a-176">**Udi Dahan**, Founder & CEO, Particular Software</span></span>
>
> <span data-ttu-id="f799a-177">**Jimmy Nilsson**, Co-foin ve CEO of Factor10</span><span class="sxs-lookup"><span data-stu-id="f799a-177">**Jimmy Nilsson**, Co-founder and CEO of Factor10</span></span>
>
> <span data-ttu-id="f799a-178">**Glenn CONDRON**, SR. program yöneticisi, ASP.NET ekibi</span><span class="sxs-lookup"><span data-stu-id="f799a-178">**Glenn Condron**, Sr. Program Manager, ASP.NET team</span></span>
>
> <span data-ttu-id="f799a-179">**Mark Fussell**, sorumlu PM lideri, Azure Service Fabric ekibi, Microsoft</span><span class="sxs-lookup"><span data-stu-id="f799a-179">**Mark Fussell**, Principal PM Lead, Azure Service Fabric team, Microsoft</span></span>
>
> <span data-ttu-id="f799a-180">**Diego Vega**, PM lideri, Entity Framework ekibi, Microsoft</span><span class="sxs-lookup"><span data-stu-id="f799a-180">**Diego Vega**, PM Lead, Entity Framework team, Microsoft</span></span>
>
> <span data-ttu-id="f799a-181">**Barry Dorrans**, SR. Security Program Yöneticisi</span><span class="sxs-lookup"><span data-stu-id="f799a-181">**Barry Dorrans**, Sr. Security Program Manager</span></span>
>
> <span data-ttu-id="f799a-182">**Rowa Miller**, SR. Program Yöneticisi, Microsoft</span><span class="sxs-lookup"><span data-stu-id="f799a-182">**Rowan Miller**, Sr. Program Manager, Microsoft</span></span>
>
> <span data-ttu-id="f799a-183">**Ankit Asthana**, ana PM Yöneticisi, .NET ekibi, Microsoft</span><span class="sxs-lookup"><span data-stu-id="f799a-183">**Ankit Asthana**, Principal PM Manager, .NET team, Microsoft</span></span>
>
> <span data-ttu-id="f799a-184">**Scott Hunter**, Iş ortağı Direktörü, .NET ekibi, Microsoft</span><span class="sxs-lookup"><span data-stu-id="f799a-184">**Scott Hunter**, Partner Director PM, .NET team, Microsoft</span></span>
>
> <span data-ttu-id="f799a-185">**Hayvan anıl**, SR. Program Yöneticisi, .NET ekibi, Microsoft</span><span class="sxs-lookup"><span data-stu-id="f799a-185">**Nish Anil**, Sr. Program Manager, .NET team, Microsoft</span></span>
>
> <span data-ttu-id="f799a-186">**Dylan Reisenberger**, mimarı ve dev lideri, Polly</span><span class="sxs-lookup"><span data-stu-id="f799a-186">**Dylan Reisenberger**, Architect and Dev Lead at Polly</span></span>
>
> <span data-ttu-id="f799a-187">**Steve "ardalış" Smith** -yazılım mimarı ve trainer- [Ardalis.com](https://ardalis.com)</span><span class="sxs-lookup"><span data-stu-id="f799a-187">**Steve "ardalis" Smith** - Software Architect and Trainer - [Ardalis.com](https://ardalis.com)</span></span>
>
> <span data-ttu-id="f799a-188">**Ian Cooper**, kod mimarı parlaktır</span><span class="sxs-lookup"><span data-stu-id="f799a-188">**Ian Cooper**, Coding Architect at Brighter</span></span>
>
> <span data-ttu-id="f799a-189">Düz kavramlarda **Unaı Zorrilla**, mimar ve dev lideri</span><span class="sxs-lookup"><span data-stu-id="f799a-189">**Unai Zorrilla**, Architect and Dev Lead at Plain Concepts</span></span>
>
> <span data-ttu-id="f799a-190">**Eğitik Tomas**, geliştirme lideri, düz kavramlar</span><span class="sxs-lookup"><span data-stu-id="f799a-190">**Eduard Tomas**, Dev Lead at Plain Concepts</span></span>
>
> <span data-ttu-id="f799a-191">**Vamon Tomas**, geliştirici basit kavramlar</span><span class="sxs-lookup"><span data-stu-id="f799a-191">**Ramon Tomas**, Developer at Plain Concepts</span></span>
>
> <span data-ttu-id="f799a-192">**David Sanz**, basit kavramlarda geliştirici</span><span class="sxs-lookup"><span data-stu-id="f799a-192">**David Sanz**, Developer at Plain Concepts</span></span>
>
> <span data-ttu-id="f799a-193">**Javier Valero**, çalışma müdürü, Grupo 'da</span><span class="sxs-lookup"><span data-stu-id="f799a-193">**Javier Valero**, Chief Operating Officer at Grupo Solutio</span></span>
>
> <span data-ttu-id="f799a-194">**Pierre millet**, SR. danışman, Microsoft</span><span class="sxs-lookup"><span data-stu-id="f799a-194">**Pierre Millet**, Sr. Consultant, Microsoft</span></span>
>
> <span data-ttu-id="f799a-195">**Michael Fri,** Ürün Yöneticisi, Docker Inc</span><span class="sxs-lookup"><span data-stu-id="f799a-195">**Michael Friis**, Product Manager, Docker Inc</span></span>
>
> <span data-ttu-id="f799a-196">**Charles Lowell**, yazılım mühendısı, vs Cat ekibi, Microsoft</span><span class="sxs-lookup"><span data-stu-id="f799a-196">**Charles Lowell**, Software Engineer, VS CAT team, Microsoft</span></span>
>
> <span data-ttu-id="f799a-197">**MIGUEL Veloso**, düz kavramlarda yazılım geliştirme mühendisi</span><span class="sxs-lookup"><span data-stu-id="f799a-197">**Miguel Veloso**, Software Development Engineer at Plain Concepts</span></span>
>
> <span data-ttu-id="f799a-198">**Sumit Ghosh**, sorumlu danışman Neudesic</span><span class="sxs-lookup"><span data-stu-id="f799a-198">**Sumit Ghosh**, Principal Consultant at Neudesic</span></span>

## <a name="copyright"></a><span data-ttu-id="f799a-199">Telif Hakkı</span><span class="sxs-lookup"><span data-stu-id="f799a-199">Copyright</span></span>

<span data-ttu-id="f799a-200">YAYIMLAYAN</span><span class="sxs-lookup"><span data-stu-id="f799a-200">PUBLISHED BY</span></span>

<span data-ttu-id="f799a-201">Microsoft Geliştirici bölümü, .NET ve Visual Studio ürün ekipleri</span><span class="sxs-lookup"><span data-stu-id="f799a-201">Microsoft Developer Division, .NET and Visual Studio product teams</span></span>

<span data-ttu-id="f799a-202">Microsoft Corporation 'ın bir bölümü</span><span class="sxs-lookup"><span data-stu-id="f799a-202">A division of Microsoft Corporation</span></span>

<span data-ttu-id="f799a-203">One Microsoft Way</span><span class="sxs-lookup"><span data-stu-id="f799a-203">One Microsoft Way</span></span>

<span data-ttu-id="f799a-204">Redmond, Washington 98052-6399</span><span class="sxs-lookup"><span data-stu-id="f799a-204">Redmond, Washington 98052-6399</span></span>

<span data-ttu-id="f799a-205">Telif hakkı © 2020 Microsoft Corporation</span><span class="sxs-lookup"><span data-stu-id="f799a-205">Copyright © 2020 by Microsoft Corporation</span></span>

<span data-ttu-id="f799a-206">All rights reserved.</span><span class="sxs-lookup"><span data-stu-id="f799a-206">All rights reserved.</span></span> <span data-ttu-id="f799a-207">Bu kitabın içeriğinin herhangi bir bölümü herhangi bir biçimde veya herhangi bir şekilde veya başka bir şekilde herhangi bir şekilde çoğaltılamaz veya herhangi bir şekilde gönderilebilir.</span><span class="sxs-lookup"><span data-stu-id="f799a-207">No part of the contents of this book may be reproduced or transmitted in any form or by any means without the written permission of the publisher.</span></span>

<span data-ttu-id="f799a-208">Bu kitap, "olduğu gibi" verilmiştir ve yazarın görünümlerini ve opnons 'yi ifade eder.</span><span class="sxs-lookup"><span data-stu-id="f799a-208">This book is provided "as-is" and expresses the author's views and opinions.</span></span> <span data-ttu-id="f799a-209">Bu kitapta ifade edilen görünümler, eklentiler ve bilgiler, URL ve diğer Internet Web sitesi başvuruları da dahil olmak üzere bildirimde bulunmaksızın değiştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="f799a-209">The views, opinions and information expressed in this book, including URL and other Internet website references, may change without notice.</span></span>

<span data-ttu-id="f799a-210">Burada tarif edilen bazı örnekler yalnızca açıklama için sağlanmıştır ve kurgusaldır.</span><span class="sxs-lookup"><span data-stu-id="f799a-210">Some examples depicted herein are provided for illustration only and are fictitious.</span></span> <span data-ttu-id="f799a-211">Gerçek bir ilişki veya bağlantı amaçlanmamıştır veya böyle bir bağlantı olduğu sonucuna varılmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="f799a-211">No real association or connection is intended or should be inferred.</span></span>

<span data-ttu-id="f799a-212">Microsoft ve <https://www.microsoft.com> "ticari markalar" Web sayfasında listelenen ticari markalar, Microsoft şirketler grubunun ticari markalarıdır.</span><span class="sxs-lookup"><span data-stu-id="f799a-212">Microsoft and the trademarks listed at <https://www.microsoft.com> on the "Trademarks" webpage are trademarks of the Microsoft group of companies.</span></span>

<span data-ttu-id="f799a-213">Mac ve macOS, Apple Inc. ' in ticari markalarıdır.</span><span class="sxs-lookup"><span data-stu-id="f799a-213">Mac and macOS are trademarks of Apple Inc.</span></span>

<span data-ttu-id="f799a-214">Docker balina logosu,, izin tarafından kullanılan Docker, Inc. ' in tescilli ticari markasıdır.</span><span class="sxs-lookup"><span data-stu-id="f799a-214">The Docker whale logo is a registered trademark of Docker, Inc. Used by permission.</span></span>

<span data-ttu-id="f799a-215">Diğer tüm işaretler ve amblemler kendi sahiplerinin mülkiyetindedir.</span><span class="sxs-lookup"><span data-stu-id="f799a-215">All other marks and logos are property of their respective owners.</span></span>

>[!div class="step-by-step"]
>[<span data-ttu-id="f799a-216">Sonraki</span><span class="sxs-lookup"><span data-stu-id="f799a-216">Next</span></span>](container-docker-introduction/index.md)
