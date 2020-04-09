---
title: .NET MikroHizmetler. Kapsayıcılı .NET Uygulamaları Mimarisi
description: .NET Microservices Mimari Containerized .NET Uygulamaları için | Mikro hizmetler modüler ve bağımsız olarak dağıtılabilir hizmetlerdir. Docker kapsayıcıları (Linux ve Windows için), bir hizmeti ve bağımlılıklarını tek bir birime birleştirerek dağıtım ve sınamayı basitleştirir ve bu da daha sonra yalıtılmış bir ortamda çalıştırılır.
ms.date: 01/30/2020
ms.openlocfilehash: 9cdd5556f92e1acde540b647e7b68628a3ecf67f
ms.sourcegitcommit: e3cbf26d67f7e9286c7108a2752804050762d02d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2020
ms.locfileid: "80988797"
---
# <a name="net-microservices-architecture-for-containerized-net-applications"></a><span data-ttu-id="c2736-105">.NET Mikro Hizmetleri: Kapsayıcılı .NET Uygulamaları Mimarisi</span><span class="sxs-lookup"><span data-stu-id="c2736-105">.NET Microservices: Architecture for Containerized .NET Applications</span></span>

![Kitap kapağı](./media/cover-small.png)

<span data-ttu-id="c2736-107">**EDITION v3.1** - Core 3.1 ASP.NET güncellendi</span><span class="sxs-lookup"><span data-stu-id="c2736-107">**EDITION v3.1** - Updated to ASP.NET Core 3.1</span></span>

<span data-ttu-id="c2736-108">Bu kılavuz, mikrohizmetlere dayalı uygulamalar geliştirmeye ve bunları kapsayıcılar kullanarak yönetmeye giriştir.</span><span class="sxs-lookup"><span data-stu-id="c2736-108">This guide is an introduction to developing microservices-based applications and managing them using containers.</span></span> <span data-ttu-id="c2736-109">.NET Core ve Docker kaplarını kullanarak mimari tasarım ve uygulama yaklaşımlarını tartışır.</span><span class="sxs-lookup"><span data-stu-id="c2736-109">It discusses architectural design and implementation approaches using .NET Core and Docker containers.</span></span>

<span data-ttu-id="c2736-110">Daha kolay başlamak için, kılavuz keşfedebilirsiniz bir referans konteyner ve mikrohizmet tabanlı uygulama odaklanır.</span><span class="sxs-lookup"><span data-stu-id="c2736-110">To make it easier to get started, the guide focuses on a reference containerized and microservice-based application that you can explore.</span></span> <span data-ttu-id="c2736-111">Referans uygulaması [eShopOnContainers](https://github.com/dotnet-architecture/eShopOnContainers) GitHub repo mevcuttur.</span><span class="sxs-lookup"><span data-stu-id="c2736-111">The reference application is available at the [eShopOnContainers](https://github.com/dotnet-architecture/eShopOnContainers) GitHub repo.</span></span>

## <a name="action-links"></a><span data-ttu-id="c2736-112">Eylem bağlantıları</span><span class="sxs-lookup"><span data-stu-id="c2736-112">Action links</span></span>

- <span data-ttu-id="c2736-113">Bu e-kitap pdf formatında da mevcuttur (yalnızca İngilizce sürüm) [İndirin](https://aka.ms/microservicesebook)</span><span class="sxs-lookup"><span data-stu-id="c2736-113">This e-book is also available in a PDF format (English version only) [Download](https://aka.ms/microservicesebook)</span></span>

- <span data-ttu-id="c2736-114">Clone / Fork github üzerinde referans uygulaması [eShopOnContainers](https://github.com/dotnet-architecture/eShopOnContainers)</span><span class="sxs-lookup"><span data-stu-id="c2736-114">Clone/Fork the reference application [eShopOnContainers on GitHub](https://github.com/dotnet-architecture/eShopOnContainers)</span></span>

- <span data-ttu-id="c2736-115">Kanal [9'da tanıtım videosunu](https://aka.ms/microservices-video) izleyin</span><span class="sxs-lookup"><span data-stu-id="c2736-115">Watch the [introductory video on Channel 9](https://aka.ms/microservices-video)</span></span>

- <span data-ttu-id="c2736-116">[Microservices Mimarisini](https://aka.ms/MicroservicesArchitecture) hemen tanıyın</span><span class="sxs-lookup"><span data-stu-id="c2736-116">Get to know the [Microservices Architecture](https://aka.ms/MicroservicesArchitecture) right away</span></span>

## <a name="introduction"></a><span data-ttu-id="c2736-117">Giriş</span><span class="sxs-lookup"><span data-stu-id="c2736-117">Introduction</span></span>

<span data-ttu-id="c2736-118">İşletmeler giderek maliyet tasarrufu gerçekleştirerek, dağıtım sorunlarını çözüyor ve devops ve üretim operasyonlarını kapsayıcılar kullanarak geliştiriyor.</span><span class="sxs-lookup"><span data-stu-id="c2736-118">Enterprises are increasingly realizing cost savings, solving deployment problems, and improving DevOps and production operations by using containers.</span></span> <span data-ttu-id="c2736-119">Microsoft, Azure Kubernetes Service ve Azure Service Fabric gibi ürünler oluşturarak ve Docker, Mezossphere ve Kubernetes gibi sektör liderleriyle ortaklık kurarak Windows ve Linux için kapsayıcı yenilikleri yayımlamaktadır.</span><span class="sxs-lookup"><span data-stu-id="c2736-119">Microsoft has been releasing container innovations for Windows and Linux by creating products like Azure Kubernetes Service and Azure Service Fabric, and by partnering with industry leaders like Docker, Mesosphere, and Kubernetes.</span></span> <span data-ttu-id="c2736-120">Bu ürünler, şirketlerin platform veya araç seçenekleri ne olursa olsun bulut hızında ve ölçekte uygulamalar oluşturmalarına ve dağıtmalarına yardımcı olan konteyner çözümleri sunar.</span><span class="sxs-lookup"><span data-stu-id="c2736-120">These products deliver container solutions that help companies build and deploy applications at cloud speed and scale, whatever their choice of platform or tools.</span></span>

<span data-ttu-id="c2736-121">Docker, Windows ve Linux ekosistemlerinin en önemli satıcıları tarafından desteklenen konteyner endüstrisinde fiili standart haline gelmektedir.</span><span class="sxs-lookup"><span data-stu-id="c2736-121">Docker is becoming the de facto standard in the container industry, supported by the most significant vendors in the Windows and Linux ecosystems.</span></span> <span data-ttu-id="c2736-122">(Microsoft, Docker'ı destekleyen ana bulut satıcılarından biridir.) Gelecekte, Docker muhtemelen bulut veya şirket içinde herhangi bir veri merkezinde her yerde olacak.</span><span class="sxs-lookup"><span data-stu-id="c2736-122">(Microsoft is one of the main cloud vendors supporting Docker.) In the future, Docker will probably be ubiquitous in any datacenter in the cloud or on-premises.</span></span>

<span data-ttu-id="c2736-123">Buna ek olarak, [mikro hizmetler](https://martinfowler.com/articles/microservices.html) mimarisi dağıtılmış görev kritik uygulamalar için önemli bir yaklaşım olarak ortaya çıkmaktadır.</span><span class="sxs-lookup"><span data-stu-id="c2736-123">In addition, the [microservices](https://martinfowler.com/articles/microservices.html) architecture is emerging as an important approach for distributed mission-critical applications.</span></span> <span data-ttu-id="c2736-124">Mikro hizmet tabanlı bir mimaride uygulama, geliştirilebilen, sınanabilen, dağıtılabilen ve bağımsız olarak sürülenebilen hizmetler koleksiyonu üzerine inşa edilmiştir.</span><span class="sxs-lookup"><span data-stu-id="c2736-124">In a microservice-based architecture, the application is built on a collection of services that can be developed, tested, deployed, and versioned independently.</span></span>

## <a name="about-this-guide"></a><span data-ttu-id="c2736-125">Bu kılavuz hakkında</span><span class="sxs-lookup"><span data-stu-id="c2736-125">About this guide</span></span>

<span data-ttu-id="c2736-126">Bu kılavuz, mikrohizmetlere dayalı uygulamalar geliştirmeye ve bunları kapsayıcılar kullanarak yönetmeye giriştir.</span><span class="sxs-lookup"><span data-stu-id="c2736-126">This guide is an introduction to developing microservices-based applications and managing them using containers.</span></span> <span data-ttu-id="c2736-127">.NET Core ve Docker kaplarını kullanarak mimari tasarım ve uygulama yaklaşımlarını tartışır.</span><span class="sxs-lookup"><span data-stu-id="c2736-127">It discusses architectural design and implementation approaches using .NET Core and Docker containers.</span></span> <span data-ttu-id="c2736-128">Konteynerler ve mikro hizmetlerle daha kolay başlamak için kılavuz, keşfedebileceğiniz bir referans konteynerve mikrohizmet tabanlı bir uygulamaya odaklanır.</span><span class="sxs-lookup"><span data-stu-id="c2736-128">To make it easier to get started with containers and microservices, the guide focuses on a reference containerized and microservice-based application that you can explore.</span></span> <span data-ttu-id="c2736-129">Örnek uygulama [eShopOnContainers](https://github.com/dotnet-architecture/eShopOnContainers) GitHub repo mevcuttur.</span><span class="sxs-lookup"><span data-stu-id="c2736-129">The sample application is available at the [eShopOnContainers](https://github.com/dotnet-architecture/eShopOnContainers) GitHub repo.</span></span>

<span data-ttu-id="c2736-130">Bu kılavuz, temel geliştirme ve mimari rehberlik temel iki teknoloji: Docker ve .NET Core odaklanarak bir geliştirme ortamı düzeyinde öncelikle sağlar.</span><span class="sxs-lookup"><span data-stu-id="c2736-130">This guide provides foundational development and architectural guidance primarily at a development environment level with a focus on two technologies: Docker and .NET Core.</span></span> <span data-ttu-id="c2736-131">Amacımız, üretim ortamınızın altyapısına (bulut veya şirket içi) odaklanmadan uygulama tasarımınızı düşünürken bu kılavuzu okumanızdır.</span><span class="sxs-lookup"><span data-stu-id="c2736-131">Our intention is that you read this guide when thinking about your application design without focusing on the infrastructure (cloud or on-premises) of your production environment.</span></span> <span data-ttu-id="c2736-132">Üretime hazır uygulamalarınızı oluşturduğunuzda altyapınızla ilgili kararları daha sonra vereceksiniz.</span><span class="sxs-lookup"><span data-stu-id="c2736-132">You will make decisions about your infrastructure later, when you create your production-ready applications.</span></span> <span data-ttu-id="c2736-133">Bu nedenle, bu kılavuz altyapı agnostik ve daha fazla geliştirme-çevre merkezli olması amaçlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="c2736-133">Therefore, this guide is intended to be infrastructure agnostic and more development-environment-centric.</span></span>

<span data-ttu-id="c2736-134">Bu kılavuzu inceledikten sonra, bir sonraki adımınız Microsoft Azure'da üretime hazır mikro hizmetler hakkında bilgi edinmek olacaktır.</span><span class="sxs-lookup"><span data-stu-id="c2736-134">After you have studied this guide, your next step would be to learn about production-ready microservices on Microsoft Azure.</span></span>

## <a name="version"></a><span data-ttu-id="c2736-135">Sürüm</span><span class="sxs-lookup"><span data-stu-id="c2736-135">Version</span></span>

<span data-ttu-id="c2736-136">Bu kılavuz, **.NET Core 3.1** sürümüyle birlikte aynı "teknoloji dalgası" (yani Azure ve ek üçüncü taraf teknolojileri) ile ilgili birçok ek güncelleştirmeyle birlikte .NET Core 3.1 sürümüyle aynı zamana denk gelecek şekilde revize edilmiştir.</span><span class="sxs-lookup"><span data-stu-id="c2736-136">This guide has been revised to cover **.NET Core 3.1** version along with many additional updates related to the same “wave” of technologies (that is, Azure and additional third-party technologies) coinciding in time with the .NET Core 3.1 release.</span></span> <span data-ttu-id="c2736-137">Bu nedenle kitap sürümü de sürüm **3.1**güncellendi.</span><span class="sxs-lookup"><span data-stu-id="c2736-137">That’s why the book version has also been updated to version **3.1**.</span></span>

## <a name="what-this-guide-does-not-cover"></a><span data-ttu-id="c2736-138">Bu kılavuzun kapsamadığı</span><span class="sxs-lookup"><span data-stu-id="c2736-138">What this guide does not cover</span></span>

<span data-ttu-id="c2736-139">Bu kılavuz, uygulama yaşam döngüsü, DevOps, CI/CD ardışık hatları veya takım çalışmasına odaklanmaz.</span><span class="sxs-lookup"><span data-stu-id="c2736-139">This guide does not focus on the application lifecycle, DevOps, CI/CD pipelines, or team work.</span></span> <span data-ttu-id="c2736-140">Microsoft Platform [ve Tools ile](https://aka.ms/dockerlifecycleebook) tamamlayıcı kılavuz Konteyner Docker Uygulama Yaşam Döngüsü bu konuya odaklanır.</span><span class="sxs-lookup"><span data-stu-id="c2736-140">The complementary guide [Containerized Docker Application Lifecycle with Microsoft Platform and Tools](https://aka.ms/dockerlifecycleebook) focuses on that subject.</span></span> <span data-ttu-id="c2736-141">Geçerli kılavuz, azure altyapısıyla ilgili belirli orkestratörler hakkındaki bilgiler gibi uygulama ayrıntıları da sağlamaz.</span><span class="sxs-lookup"><span data-stu-id="c2736-141">The current guide also does not provide implementation details on Azure infrastructure, such as information on specific orchestrators.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="c2736-142">Ek kaynaklar</span><span class="sxs-lookup"><span data-stu-id="c2736-142">Additional resources</span></span>

- <span data-ttu-id="c2736-143">**Microsoft Platform ve Araçları ile Containerized Docker Uygulama Yaşam Döngüsü** (indirilebilir e-kitap)</span><span class="sxs-lookup"><span data-stu-id="c2736-143">**Containerized Docker Application Lifecycle with Microsoft Platform and Tools** (downloadable e-book)</span></span>  
    <https://aka.ms/dockerlifecycleebook>

## <a name="who-should-use-this-guide"></a><span data-ttu-id="c2736-144">Bu kılavuzu kimler kullanmalı?</span><span class="sxs-lookup"><span data-stu-id="c2736-144">Who should use this guide</span></span>

<span data-ttu-id="c2736-145">Bu kılavuzu, Docker tabanlı uygulama geliştirme ve mikro hizmetler tabanlı mimaride yeni olan geliştiriciler ve çözüm mimarları için yazdık.</span><span class="sxs-lookup"><span data-stu-id="c2736-145">We wrote this guide for developers and solution architects who are new to Docker-based application development and to microservices-based architecture.</span></span> <span data-ttu-id="c2736-146">Bu kılavuz, Microsoft geliştirme teknolojileri (.NET Core'a özel olarak odaklanarak) ve Docker kapsayıcılarıyla kavram kanıtı uygulamalarını nasıl tasarlayıp tasarlaacağınızı ve uygulayacağınızı öğrenmek istiyorsanız tam size göre dir.</span><span class="sxs-lookup"><span data-stu-id="c2736-146">This guide is for you if you want to learn how to architect, design, and implement proof-of-concept applications with Microsoft development technologies (with special focus on .NET Core) and with Docker containers.</span></span>

<span data-ttu-id="c2736-147">Yeni ve modern dağıtılmış uygulamalar için hangi yaklaşımı seçeceğiniz konusunda karar vermeden önce mimari ve teknolojiye genel bakış isteyen bir kurumsal mimar gibi teknik bir karar vericiyseniz, bu kılavuzu da yararlı bulacaksınız.</span><span class="sxs-lookup"><span data-stu-id="c2736-147">You will also find this guide useful if you are a technical decision maker, such as an enterprise architect, who wants an architecture and technology overview before you decide on what approach to select for new and modern distributed applications.</span></span>

### <a name="how-to-use-this-guide"></a><span data-ttu-id="c2736-148">Bu kılavuz nasıl kullanılır?</span><span class="sxs-lookup"><span data-stu-id="c2736-148">How to use this guide</span></span>

<span data-ttu-id="c2736-149">Bu kılavuzun ilk bölümünde Docker kapsayıcıları tanıtılır, geliştirme çerçevesi olarak .NET Core ve .NET Framework arasında nasıl seçim yapılacağını tartışır ve mikro hizmetlere genel bir bakış sağlar.</span><span class="sxs-lookup"><span data-stu-id="c2736-149">The first part of this guide introduces Docker containers, discusses how to choose between .NET Core and the .NET Framework as a development framework, and provides an overview of microservices.</span></span> <span data-ttu-id="c2736-150">Bu içerik, genel bir bakış isteyen ancak kod uygulama ayrıntılarına odaklanması gerekmeyen mimarlar ve teknik karar vericiler içindir.</span><span class="sxs-lookup"><span data-stu-id="c2736-150">This content is for architects and technical decision makers who want an overview but don't need to focus on code implementation details.</span></span>

<span data-ttu-id="c2736-151">Kılavuzun ikinci bölümü Docker [tabanlı uygulamalar](./docker-application-development-process/index.md) bölümü için Geliştirme süreci ile başlar.</span><span class="sxs-lookup"><span data-stu-id="c2736-151">The second part of the guide starts with the [Development process for Docker based applications](./docker-application-development-process/index.md) section.</span></span> <span data-ttu-id="c2736-152">.NET Core ve Docker kullanarak uygulama uygulamak için geliştirme ve mikrohizmet kalıplarına odaklanır.</span><span class="sxs-lookup"><span data-stu-id="c2736-152">It focuses on development and microservice patterns for implementing applications using .NET Core and Docker.</span></span> <span data-ttu-id="c2736-153">Bu bölüm, kod ve desenler ve uygulama ayrıntıları üzerinde odaklanmak isteyen geliştiriciler ve mimarlar için en çok ilgi olacaktır.</span><span class="sxs-lookup"><span data-stu-id="c2736-153">This section will be of most interest to developers and architects who want to focus on code and on patterns and implementation details.</span></span>

## <a name="related-microservice-and-container-based-reference-application-eshoponcontainers"></a><span data-ttu-id="c2736-154">İlgili microservice ve konteyner tabanlı referans uygulaması: eShopOnContainers</span><span class="sxs-lookup"><span data-stu-id="c2736-154">Related microservice and container-based reference application: eShopOnContainers</span></span>

<span data-ttu-id="c2736-155">eShopOnContainers uygulaması ,NET Core ve Docker konteynerleri kullanılarak dağıtılmak üzere tasarlanmış mikro hizmetler için bir açık kaynak referans uygulamasıdır.</span><span class="sxs-lookup"><span data-stu-id="c2736-155">The eShopOnContainers application is an open-source reference app for .NET Core and microservices that is designed to be deployed using Docker containers.</span></span> <span data-ttu-id="c2736-156">Uygulama, birden fazla e-mağaza Kullanıcı UI ön uçları (Bir Web MVC uygulaması, bir Web SPA ve yerel bir mobil uygulama) dahil olmak üzere birden çok alt sistemden oluşur.</span><span class="sxs-lookup"><span data-stu-id="c2736-156">The application consists of multiple subsystems, including several e-store UI front ends (a Web MVC app, a Web SPA, and a native mobile app).</span></span> <span data-ttu-id="c2736-157">Ayrıca, gerekli tüm sunucu tarafı işlemleri için arka uç mikro hizmetleri ve kapsayıcıları içerir.</span><span class="sxs-lookup"><span data-stu-id="c2736-157">It also includes the back-end microservices and containers for all required server-side operations.</span></span>

<span data-ttu-id="c2736-158">Uygulamanın amacı mimari desenleri sergilemektir.</span><span class="sxs-lookup"><span data-stu-id="c2736-158">The purpose of the application is to showcase architectural patterns.</span></span> <span data-ttu-id="c2736-159">GERÇEK UYGULAMA YILI BAŞLATMAK İçİn **ÜRETİmHAZIR Bİr ŞABLON Değİl.**</span><span class="sxs-lookup"><span data-stu-id="c2736-159">**IT IS NOT A PRODUCTION-READY TEMPLATE** to start real-world applications.</span></span> <span data-ttu-id="c2736-160">Aslında, uygulama kalıcı bir beta durumundadır, aynı zamanda yeni potansiyel olarak ilginç teknolojileri test etmek için kullanılır gibi onlar göstermek gibi.</span><span class="sxs-lookup"><span data-stu-id="c2736-160">In fact, the application is in a permanent beta state, as it's also used to test new potentially interesting technologies as they show up.</span></span>

## <a name="send-us-your-feedback"></a><span data-ttu-id="c2736-161">Geri bildiriminizi bize gönderin!</span><span class="sxs-lookup"><span data-stu-id="c2736-161">Send us your feedback!</span></span>

<span data-ttu-id="c2736-162">Bu kılavuzu , .NET'te konteyner uygulamalarının ve mikro hizmetlerin mimarisini anlamanıza yardımcı olmak için yazdık.</span><span class="sxs-lookup"><span data-stu-id="c2736-162">We wrote this guide to help you understand the architecture of containerized applications and microservices in .NET.</span></span> <span data-ttu-id="c2736-163">Kılavuz ve ilgili referans uygulaması gelişmekte olacak, bu yüzden geribildirim bekliyoruz!</span><span class="sxs-lookup"><span data-stu-id="c2736-163">The guide and related reference application will be evolving, so we welcome your feedback!</span></span> <span data-ttu-id="c2736-164">Bu kılavuzun nasıl geliştirilebileceği hakkında yorumlarınız <https://aka.ms/ebookfeedback>varsa, 'den geri bildirim gönderin.</span><span class="sxs-lookup"><span data-stu-id="c2736-164">If you have comments about how this guide can be improved, submit feedback at <https://aka.ms/ebookfeedback>.</span></span>

## <a name="credits"></a><span data-ttu-id="c2736-165">Krediler</span><span class="sxs-lookup"><span data-stu-id="c2736-165">Credits</span></span>

<span data-ttu-id="c2736-166">Ortak Yazarlar:</span><span class="sxs-lookup"><span data-stu-id="c2736-166">Co-Authors:</span></span>

> <span data-ttu-id="c2736-167">**Cesar de la Torre**, Sr. PM, .NET ürün ekibi, Microsoft Corp.</span><span class="sxs-lookup"><span data-stu-id="c2736-167">**Cesar de la Torre**, Sr. PM, .NET product team, Microsoft Corp.</span></span>
>
> <span data-ttu-id="c2736-168">**Bill Wagner**, Sr. İçerik Geliştirici, C +E, Microsoft Corp.</span><span class="sxs-lookup"><span data-stu-id="c2736-168">**Bill Wagner**, Sr. Content Developer, C+E, Microsoft Corp.</span></span>
>
> <span data-ttu-id="c2736-169">**Mike Rousos**, Baş Yazılım Mühendisi, DevDiv CAT ekibi, Microsoft</span><span class="sxs-lookup"><span data-stu-id="c2736-169">**Mike Rousos**, Principal Software Engineer, DevDiv CAT team, Microsoft</span></span>

<span data-ttu-id="c2736-170">Editörler:</span><span class="sxs-lookup"><span data-stu-id="c2736-170">Editors:</span></span>

> <span data-ttu-id="c2736-171">**Mike Pope**</span><span class="sxs-lookup"><span data-stu-id="c2736-171">**Mike Pope**</span></span>
>
> <span data-ttu-id="c2736-172">**Steve Hoag**</span><span class="sxs-lookup"><span data-stu-id="c2736-172">**Steve Hoag**</span></span>

<span data-ttu-id="c2736-173">Katılımcılar ve gözden geçirenler:</span><span class="sxs-lookup"><span data-stu-id="c2736-173">Participants and reviewers:</span></span>

> <span data-ttu-id="c2736-174">**Jeffrey Richter**, İş Ortağı Yazılım Müg, Azure ekibi, Microsoft</span><span class="sxs-lookup"><span data-stu-id="c2736-174">**Jeffrey Richter**, Partner Software Eng, Azure team, Microsoft</span></span>
>
> <span data-ttu-id="c2736-175">**Jimmy Bogard**, Headspring Baş Mimarı</span><span class="sxs-lookup"><span data-stu-id="c2736-175">**Jimmy Bogard**, Chief Architect at Headspring</span></span>
>
> <span data-ttu-id="c2736-176">**Udi Dahan**, Kurucu & CEO'su, Özel Yazılım</span><span class="sxs-lookup"><span data-stu-id="c2736-176">**Udi Dahan**, Founder & CEO, Particular Software</span></span>
>
> <span data-ttu-id="c2736-177">**Jimmy Nilsson**, Factor10'un kurucu ortağı ve CEO'su</span><span class="sxs-lookup"><span data-stu-id="c2736-177">**Jimmy Nilsson**, Co-founder and CEO of Factor10</span></span>
>
> <span data-ttu-id="c2736-178">**Glenn Condron**, Sr. Program Yöneticisi, ASP.NET takım</span><span class="sxs-lookup"><span data-stu-id="c2736-178">**Glenn Condron**, Sr. Program Manager, ASP.NET team</span></span>
>
> <span data-ttu-id="c2736-179">**Mark Fussell**, Baş PM Müşteri Adayı, Azure Hizmet Kumaşı ekibi, Microsoft</span><span class="sxs-lookup"><span data-stu-id="c2736-179">**Mark Fussell**, Principal PM Lead, Azure Service Fabric team, Microsoft</span></span>
>
> <span data-ttu-id="c2736-180">**Diego Vega**, PM Kurşun, Varlık Çerçeve ekibi, Microsoft</span><span class="sxs-lookup"><span data-stu-id="c2736-180">**Diego Vega**, PM Lead, Entity Framework team, Microsoft</span></span>
>
> <span data-ttu-id="c2736-181">**Barry Dorrans**, Sr. Güvenlik Programı Yöneticisi</span><span class="sxs-lookup"><span data-stu-id="c2736-181">**Barry Dorrans**, Sr. Security Program Manager</span></span>
>
> <span data-ttu-id="c2736-182">**Rowan Miller**, Sr. Program Yöneticisi, Microsoft</span><span class="sxs-lookup"><span data-stu-id="c2736-182">**Rowan Miller**, Sr. Program Manager, Microsoft</span></span>
>
> <span data-ttu-id="c2736-183">**Ankit Asthana**, Baş PM Yöneticisi, .NET ekibi, Microsoft</span><span class="sxs-lookup"><span data-stu-id="c2736-183">**Ankit Asthana**, Principal PM Manager, .NET team, Microsoft</span></span>
>
> <span data-ttu-id="c2736-184">**Scott Hunter**, İş Ortağı Direktörü PM, .NET ekibi, Microsoft</span><span class="sxs-lookup"><span data-stu-id="c2736-184">**Scott Hunter**, Partner Director PM, .NET team, Microsoft</span></span>
>
> <span data-ttu-id="c2736-185">**Nish Anıl**, Sr. Program Yöneticisi, .NET ekibi, Microsoft</span><span class="sxs-lookup"><span data-stu-id="c2736-185">**Nish Anil**, Sr. Program Manager, .NET team, Microsoft</span></span>
>
> <span data-ttu-id="c2736-186">**Dylan Reisenberger**, Polly'de Mimar ve Dev Kurşun</span><span class="sxs-lookup"><span data-stu-id="c2736-186">**Dylan Reisenberger**, Architect and Dev Lead at Polly</span></span>
>
> <span data-ttu-id="c2736-187">**Steve "ardalis" Smith** - Yazılım Mimarı ve Eğitmen - [Ardalis.com](https://ardalis.com)</span><span class="sxs-lookup"><span data-stu-id="c2736-187">**Steve "ardalis" Smith** - Software Architect and Trainer - [Ardalis.com](https://ardalis.com)</span></span>
>
> <span data-ttu-id="c2736-188">**Ian Cooper**, Brighter'da Kodlama Mimarı</span><span class="sxs-lookup"><span data-stu-id="c2736-188">**Ian Cooper**, Coding Architect at Brighter</span></span>
>
> <span data-ttu-id="c2736-189">**Unai Zorrilla**, Mimar ve Dev Kurşun Düz Kavramlar at</span><span class="sxs-lookup"><span data-stu-id="c2736-189">**Unai Zorrilla**, Architect and Dev Lead at Plain Concepts</span></span>
>
> <span data-ttu-id="c2736-190">**Eduard Tomas**, Düz Kavramlar dev kurşun</span><span class="sxs-lookup"><span data-stu-id="c2736-190">**Eduard Tomas**, Dev Lead at Plain Concepts</span></span>
>
> <span data-ttu-id="c2736-191">**Ramon Tomas**, Düz Kavramlar Geliştirici</span><span class="sxs-lookup"><span data-stu-id="c2736-191">**Ramon Tomas**, Developer at Plain Concepts</span></span>
>
> <span data-ttu-id="c2736-192">**David Sanz**, Geliştirici Düz Kavramlar at</span><span class="sxs-lookup"><span data-stu-id="c2736-192">**David Sanz**, Developer at Plain Concepts</span></span>
>
> <span data-ttu-id="c2736-193">**Javier Valero**, Grupo Solutio'da Operasyon Müdürü</span><span class="sxs-lookup"><span data-stu-id="c2736-193">**Javier Valero**, Chief Operating Officer at Grupo Solutio</span></span>
>
> <span data-ttu-id="c2736-194">**Pierre Millet**, Sr. Danışman, Microsoft</span><span class="sxs-lookup"><span data-stu-id="c2736-194">**Pierre Millet**, Sr. Consultant, Microsoft</span></span>
>
> <span data-ttu-id="c2736-195">**Michael Friis,** Ürün Müdürü, Docker Inc</span><span class="sxs-lookup"><span data-stu-id="c2736-195">**Michael Friis**, Product Manager, Docker Inc</span></span>
>
> <span data-ttu-id="c2736-196">**Charles Lowell**, Yazılım Mühendisi, VS CAT ekibi, Microsoft</span><span class="sxs-lookup"><span data-stu-id="c2736-196">**Charles Lowell**, Software Engineer, VS CAT team, Microsoft</span></span>
>
> <span data-ttu-id="c2736-197">**Miguel Veloso**, Düz Kavramlar Yazılım Geliştirme Mühendisi</span><span class="sxs-lookup"><span data-stu-id="c2736-197">**Miguel Veloso**, Software Development Engineer at Plain Concepts</span></span>

## <a name="copyright"></a><span data-ttu-id="c2736-198">Telif Hakkı</span><span class="sxs-lookup"><span data-stu-id="c2736-198">Copyright</span></span>

<span data-ttu-id="c2736-199">YAYIMLAYAN</span><span class="sxs-lookup"><span data-stu-id="c2736-199">PUBLISHED BY</span></span>

<span data-ttu-id="c2736-200">Microsoft Developer Division, .NET ve Visual Studio ürün ekipleri</span><span class="sxs-lookup"><span data-stu-id="c2736-200">Microsoft Developer Division, .NET and Visual Studio product teams</span></span>

<span data-ttu-id="c2736-201">Microsoft Corporation'ın bir bölümü</span><span class="sxs-lookup"><span data-stu-id="c2736-201">A division of Microsoft Corporation</span></span>

<span data-ttu-id="c2736-202">One Microsoft Way</span><span class="sxs-lookup"><span data-stu-id="c2736-202">One Microsoft Way</span></span>

<span data-ttu-id="c2736-203">Redmond, Washington 98052-6399</span><span class="sxs-lookup"><span data-stu-id="c2736-203">Redmond, Washington 98052-6399</span></span>

<span data-ttu-id="c2736-204">Telif hakkı © 2020 Microsoft Corporation tarafından</span><span class="sxs-lookup"><span data-stu-id="c2736-204">Copyright © 2020 by Microsoft Corporation</span></span>

<span data-ttu-id="c2736-205">Tüm hakları saklıdır.</span><span class="sxs-lookup"><span data-stu-id="c2736-205">All rights reserved.</span></span> <span data-ttu-id="c2736-206">Bu kitabın içeriğinin hiçbir bölümü, yayımcının yazılı izni olmadan herhangi bir biçimde veya herhangi bir şekilde çoğaltılamaz veya aktarılamaz.</span><span class="sxs-lookup"><span data-stu-id="c2736-206">No part of the contents of this book may be reproduced or transmitted in any form or by any means without the written permission of the publisher.</span></span>

<span data-ttu-id="c2736-207">Bu kitap "olduğu gibi" sağlanır ve yazarın görüş ve görüşlerini ifade eder.</span><span class="sxs-lookup"><span data-stu-id="c2736-207">This book is provided "as-is" and expresses the author's views and opinions.</span></span> <span data-ttu-id="c2736-208">URL ve diğer Internet web sitesi referansları da dahil olmak üzere bu kitapta ifade edilen görüşler, görüşler ve bilgiler önceden haber verilmeden değişebilir.</span><span class="sxs-lookup"><span data-stu-id="c2736-208">The views, opinions and information expressed in this book, including URL and other Internet website references, may change without notice.</span></span>

<span data-ttu-id="c2736-209">Burada tarif edilen bazı örnekler yalnızca açıklama için sağlanmıştır ve kurgusaldır.</span><span class="sxs-lookup"><span data-stu-id="c2736-209">Some examples depicted herein are provided for illustration only and are fictitious.</span></span> <span data-ttu-id="c2736-210">Gerçek bir ilişki veya bağlantı amaçlanmamıştır veya böyle bir bağlantı olduğu sonucuna varılmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="c2736-210">No real association or connection is intended or should be inferred.</span></span>

<span data-ttu-id="c2736-211">Microsoft ve "Ticari <https://www.microsoft.com> Markalar" web sayfasında listelenen ticari markalar, Microsoft şirketler grubunun ticari markalarıdır.</span><span class="sxs-lookup"><span data-stu-id="c2736-211">Microsoft and the trademarks listed at <https://www.microsoft.com> on the "Trademarks" webpage are trademarks of the Microsoft group of companies.</span></span>

<span data-ttu-id="c2736-212">Mac ve macOS, Apple Inc. şirketinin ticari markalarıdır.</span><span class="sxs-lookup"><span data-stu-id="c2736-212">Mac and macOS are trademarks of Apple Inc.</span></span>

<span data-ttu-id="c2736-213">Docker balina logosu, Docker, Inc. şirketinin izni yle kullanılan tescilli ticari markasıdır.</span><span class="sxs-lookup"><span data-stu-id="c2736-213">The Docker whale logo is a registered trademark of Docker, Inc. Used by permission.</span></span>

<span data-ttu-id="c2736-214">Diğer tüm işaretler ve logolar ilgili sahiplerinin mülkiyetindedir.</span><span class="sxs-lookup"><span data-stu-id="c2736-214">All other marks and logos are property of their respective owners.</span></span>

>[!div class="step-by-step"]
>[<span data-ttu-id="c2736-215">Sonraki</span><span class="sxs-lookup"><span data-stu-id="c2736-215">Next</span></span>](container-docker-introduction/index.md)
